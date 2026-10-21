+++
title = "Architecture Overview"
type = "guides"
body_class = "historical-archive-page"
version_archive = true
exclude_search = true
url = "/archive/old-site/docs/architecture/overview/"
archive_title_in_content = true
+++

# Architecture Overview


> **Historical archive.** This unversioned page is preserved from the old website at commit <code>43fb08a65bdf4341d78adb829ffcd6cc5e4d8131</code> (2026-10-21). Its instructions may not match current releases. Read the [current guidance](/docs/architecture/overview), [exact Markdown source](/archive/old-site/source/docs/architecture/overview.md), and [original site license](/archive/old-site/source/LICENSE).

## Design Principles

**Fast.** Performance is a primary design goal.

**Secure by default.** Security is a primary design goal.

**Composable.** Everything is a filter. Routing, load
balancing, rate limiting, AI model selection: all filters,
all using the same traits, all assembled through chains.

**Extensible.** Your filters implement the same [`HttpFilter`]
and [`TcpFilter`] traits as built-in filters. Register with
one macro.

**Adaptive.** Praxis is a framework for building proxies,
not just a proxy. Use a provided build out of the box, or
compose a bespoke proxy server from the same primitives.

[`HttpFilter`]:/archive/old-site/docs/filters/
[`TcpFilter`]:/archive/old-site/docs/filters/

## Primary Use-Cases

- **Ingress**: Reverse proxy, API gateway, edge proxy
- **Egress**: Outbound proxy, service-to-service
- **East/West**: Sidecar or converged proxy for service mesh
- **AI Inference**: Proxy for AI inference workloads
- **AI Agents**: Proxy for AI agents
- **Security Gateway**: Guardrails, Network Policy

> **Tip: Interactive Diagram**
>
> See the [interactive architecture diagram](/architecture/diagram.html)
> for a visual overview of crate dependencies, filter
> categories, and request flow.
>

## System Architecture

### Protocol Adapters

Adapters translate upstream library callbacks into pipeline
invocations. When feasible Praxis owns no protocol logic,
instead handing it off to well-maintained and battle-tested
upstream solutions.

```text
HTTP  --> praxis-protocol/http  --> Pingora
TCP   --> praxis-protocol/tcp   --> Pingora
QUIC  --> praxis-protocol/http3 --> Quiche  (planned, not yet implemented)
```

These adapters are modular, it's intended to enable adding new protocols by
writing new adapters, and even having multiple implementations of a single
protocol that can be swapped via build features or runtime configuration.

### Filter-First Design

Every behavior is a filter. Built-in filters use the same
traits as user-provided filters.

```mermaid
sequenceDiagram
    participant C  as Client
    participant F1 as RequestIdFilter
    participant F2 as RouterFilter
    participant F3 as HeaderFilter
    participant F4 as LoadBalancerFilter
    participant U  as Upstream

    C  ->>  F1: request
    F1 ->>  F2: on_request
    F2 ->>  F3: on_request  (sets ctx.cluster)
    F3 ->>  F4: on_request
    F4 ->>  U:  on_request  (sets ctx.upstream)

    U  -->> F4: response
    F4 -->> F3: on_response
    F3 -->> F2: on_response
    F2 -->> F1: on_response
    F1 -->> C:  response
```

Request filters run in declared order, response filters in
reverse. Any filter can short-circuit, and multiple payload
processing options are available to do filtering, routing,
caching and load-balancing based on request or response bodies.

See the [filter system documentation] for more extensive
documentation, and the [extensions guide] for how to write
your own.

[filter system documentation]:/archive/old-site/docs/filters/
[extensions guide]:/archive/old-site/docs/filters/extensions/

### Listeners

```mermaid
flowchart LR
    Client -->|TCP| L1["Listener (named)"]
    L1 -->|rustls| TLS
    TLS --> Resolve["Chain Resolution"]
    Resolve --> Pipeline["Filter Pipeline"]
    Pipeline --> Pool["Upstream Pool"]
    Pool --> Backend

    Config["Config (YAML)"] -. startup .-> Chains
    Chains["filter_chains:"] -. per listener .-> Resolve
```

Each listener has a `name` and a list of `filter_chains`.
At startup, the referenced chains are resolved and
concatenated into a single pipeline per listener. Different
listeners can compose different subsets of chains.

### Filters

Filter chains are named, reusable groups of filters defined
at the top level of the config. A listener references one or
more chains by name; the filters are concatenated in order
to form that listener's pipeline.

```mermaid
flowchart LR
    subgraph "Listener: public"
        direction LR
        S["security chain"] --> O["observability chain"]
        O --> R["routing chain"]
    end

    subgraph "Listener: internal"
        direction LR
        O2["observability chain"] --> R2["routing chain"]
    end
```

This enables reuse without duplication. A "security" chain
can be shared across public listeners while internal
listeners skip it entirely.

#### Protocol-Aware Filters

Filters are protocol-aware. HTTP filters implement the
`HttpFilter` trait (`on_request`, `on_response`, body hooks).
TCP filters implement the `TcpFilter` trait (`on_connect`,
`on_disconnect`). The `AnyFilter` enum wraps both variants
for storage in a unified pipeline.

Protocol compatibility is enforced via `ProtocolKind::stack()`
and `supports()`. An HTTP listener supports both HTTP and TCP
filters. A TCP listener supports only TCP filters.

```mermaid
flowchart TD
    AnyFilter --> HttpFilter
    AnyFilter --> TcpFilter

    HttpListener["HTTP Listener"] -->|supports| HttpFilter
    HttpListener -->|supports| TcpFilter
    TcpListener["TCP Listener"] -->|supports| TcpFilter
```

### What Stays Outside Filters

- TCP/TLS, HTTP framing, connection pooling: adapters
- Config loading and validation: `praxis-core`
- Pipeline executor and `HttpFilterContext`: `praxis-filter`

## Dynamic Configuration Reload

Praxis swaps filter pipelines at runtime without
restarting the server or disrupting in-flight requests.

Each handler holds an `Arc<ArcSwap<FilterPipeline>>`
instead of a plain `Arc<FilterPipeline>`. On every
request, the handler calls `pipeline.load()` to get a
snapshot pinned for that request's lifetime. A reload
stores a new pipeline into the `ArcSwap`; the next
request loads the new pointer while in-flight requests
drain on the old one.

A file watcher (`notify` crate, 500ms debounce) monitors
the config file. On change it validates the new config,
rebuilds all pipelines, and swaps them atomically. If
validation fails, nothing changes. Health check tasks
are cancelled and respawned with a fresh registry on
each successful reload.

Changes that cannot be applied dynamically (listener
topology, protocol type, compression module, TLS toggle)
are detected by diffing old and new configs and logged
as warnings.

## Related

- [Connection Lifecycle](/archive/old-site/docs/architecture/connection-lifecycle/)
- [Payload Processing](/archive/old-site/docs/architecture/payload-processing/)
- [Crate Layout](/archive/old-site/docs/architecture/crate-layout/)
- [HTTP Correctness](/archive/old-site/docs/architecture/http-correctness/)
