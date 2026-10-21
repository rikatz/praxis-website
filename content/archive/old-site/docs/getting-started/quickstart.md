+++
title = "Quickstart"
type = "guides"
body_class = "historical-archive-page"
version_archive = true
exclude_search = true
url = "/archive/old-site/docs/getting-started/quickstart/"
archive_title_in_content = true
+++

# Quickstart


> **Historical archive.** This unversioned page is preserved from the old website at commit <code>43fb08a65bdf4341d78adb829ffcd6cc5e4d8131</code> (2026-10-21). Its instructions may not match current releases. Read the [current guidance](/docs/getting-started/quickstart), [exact Markdown source](/archive/old-site/source/docs/getting-started/quickstart.md), and [original site license](/archive/old-site/source/LICENSE).

Build the release binary:

```console
make release
```

Start Praxis:

```console
./target/release/praxis
```

The server starts on `127.0.0.1:8080` with a built-in
default configuration. Verify it:

```console
curl http://127.0.0.1:8080/
```

```json
{"status": "ok", "server": "praxis"}
```

## Proxy to a backend

Create `praxis.yaml`:

```yaml
listeners:
  - name: web
    address: "127.0.0.1:8080"
    filter_chains: [main]

filter_chains:
  - name: main
    filters:
      - filter: router
        routes:
          - path_prefix: "/"
            cluster: backend
      - filter: load_balancer
        clusters:
          - name: backend
            endpoints:
              - "127.0.0.1:3000"
```

Start Praxis with your config:

```console
./target/release/praxis -c praxis.yaml
```

Requests to port 8080 are now forwarded to your backend
on port 3000:

```console
curl http://127.0.0.1:8080/
```

## Next steps

- [Configuration](/archive/old-site/docs/configuration/overview/): filter chains,
  routing, load balancing, TLS, and all options.
- [Example configs](https://github.com/praxis-proxy/praxis/tree/main/examples/configs): working YAML
  for every feature.
- [Filters](/archive/old-site/docs/filters/filter-model/): built-in filters and how to
  write your own.
