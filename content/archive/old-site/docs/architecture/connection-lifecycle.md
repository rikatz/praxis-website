+++
title = "Connection Lifecycle"
type = "guides"
body_class = "historical-archive-page"
version_archive = true
exclude_search = true
url = "/archive/old-site/docs/architecture/connection-lifecycle/"
archive_title_in_content = true
+++

# Connection Lifecycle


> **Historical archive.** This unversioned page is preserved from the old website at commit <code>43fb08a65bdf4341d78adb829ffcd6cc5e4d8131</code> (2026-10-21). Its instructions may not match current releases. Read the [current guidance](/docs/architecture/connection-lifecycle), [exact Markdown source](/archive/old-site/source/docs/architecture/connection-lifecycle.md), and [original site license](/archive/old-site/source/LICENSE).

## HTTP Connection Lifecycle

```mermaid
sequenceDiagram
    participant C as Client
    participant P as Pingora
    participant RF as request_filter
    participant BF as request_body_filter
    participant UP as upstream_peer
    participant B as Backend
    participant RSF as response_filter
    participant RBF as response_body_filter

    C->>P: TCP + TLS + HTTP decode
    P->>RF: request_filter(session, ctx)
    RF->>RF: pipeline.execute_http_request()
    Note over RF: router sets ctx.cluster<br/>load_balancer sets ctx.upstream

    opt body present
        P->>BF: request_body_filter(body, eos)
        BF->>BF: buffer or stream through pipeline
    end

    P->>UP: upstream_peer(ctx)
    UP->>UP: build HttpPeer from ctx.upstream

    opt upstream connect failure
        P->>P: fail_to_connect (retry if idempotent)
    end

    P->>P: upstream_request_filter (strip hop-by-hop)
    P->>B: forward request
    B-->>P: response headers

    P->>RSF: response_filter(upstream_response, ctx)
    RSF->>RSF: pipeline.execute_http_response()

    loop each body chunk
        B-->>P: response body chunk
        P->>RBF: response_body_filter(body, eos)
    end

    P-->>C: response
    P->>P: logging (response-filter cleanup)
```

1. TCP accept, TLS handshake, HTTP decode (Pingora)
2. `request_filter`: pipeline runs filters in order; router
   sets `ctx.cluster`, load balancer sets `ctx.upstream`
3. `request_body_filter`: buffer or stream body chunks
   through filters (if any filter declares body access)
4. `upstream_peer`: converts `ctx.upstream` to `HttpPeer`
5. Connect to upstream; `fail_to_connect` retries
   idempotent requests on failure
6. `upstream_request_filter`: strips hop-by-hop headers
7. Request forwarded, response headers received
8. `response_filter`: pipeline runs filters in reverse
9. `response_body_filter`: stream response body through
   filters (synchronous; Pingora constraint)
10. `logging`: re-runs response filters if response
    phase was skipped (upstream error, filter rejection)
11. Connection returned to pool

## TCP Connection Lifecycle

1. TCP accept, optional TLS handshake
2. `on_connect` : TCP filters run in order
3. Bidirectional byte forwarding to upstream
4. `on_disconnect` : TCP filters run on close

## Related

- [Architecture Overview](/archive/old-site/docs/architecture/overview/)
- [Payload Processing](/archive/old-site/docs/architecture/payload-processing/)
- [HTTP Correctness](/archive/old-site/docs/architecture/http-correctness/)
