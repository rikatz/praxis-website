+++
title = "Overview"
type = "guides"
body_class = "historical-archive-page"
version_archive = true
exclude_search = true
url = "/archive/old-site/docs/grid/overview/"
archive_title_in_content = true
+++

# Grid


> **Historical archive.** This unversioned page is preserved from the old website at commit <code>43fb08a65bdf4341d78adb829ffcd6cc5e4d8131</code> (2026-10-21). Its instructions may not match current releases. Read the [current guidance](/docs/grid/overview), [exact Markdown source](/archive/old-site/source/docs/grid/overview.md), and [original site license](/archive/old-site/source/LICENSE).

Grid is the distributed Kubernetes control plane for
multi-site AI inference routing. It discovers providers
across every site, scores them, and writes a
pre-computed `grid-config.json` ConfigMap that Praxis
reads at request time - so the data-plane hot path
never calls a cluster.

**Grid decides what should be routable. Praxis routes.**

Grid never proxies traffic, terminates data-plane TLS,
or touches a request. It operates entirely in the
control plane.

## Why Grid Exists

Without Grid, every gateway needs static knowledge of
every backend, every remote cluster, every credential
rule, and every health signal. That does not scale
across sites and providers.

Grid turns that moving control-plane state into a local
file the gateway reads cheaply. A live request never
calls Kubernetes, SWIM, the CRDT layer, or the
operator.

## Architecture

```text
                CONTROL PLANE - Grid Operator
  ┌───────────────────────────────────────────────┐
  │  GridNetwork    InferenceProvider    SWIM/CRDT │
  │                       │                       │
  │               grid-config.json                │
  └───────────────────────┼───────────────────────┘
  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┼ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
                DATA PLANE - Praxis AI
  ┌───────────────────────────────────────────────┐
  │         grid_route  ->  proxy -> backend      │
  └───────────────────────────────────────────────┘
```

| Layer | Role |
|---|---|
| **Grid Operator** | Watch CRDs, exchange peer state via SWIM/CRDT, score candidates, render ConfigMaps, manage mTLS trust |
| **Praxis AI** | AI-aware gateway: request parsing, `grid_route` filter, credential injection, provider routing |
| **Praxis Core** | Generic proxy runtime: listeners, filter pipelines, load balancing, TLS |

## How It Works

1. **Watch** - The operator watches three CRDs:
   [GridNetwork](/archive/old-site/docs/grid/concepts/#gridnetwork),
   [GridSite](/archive/old-site/docs/grid/concepts/#gridsite), and
   [InferenceProvider](/archive/old-site/docs/grid/concepts/#inferenceprovider).

2. **Discover** - Sites find each other through
   [SWIM](/archive/old-site/docs/grid/concepts/#swim-membership), a gossip-based
   membership protocol over AES-256-GCM encrypted UDP.

3. **Converge** - Provider state replicates across
   sites using [CRDTs](/archive/old-site/docs/grid/concepts/#crdts) piggybacked on
   SWIM probe messages. No central coordinator needed.

4. **Score** - Six normalized
   [signals](/archive/old-site/docs/grid/concepts/#scoring) - locality, queue
   depth, KV-cache utilization, prefix-cache hit ratio,
   P99 latency, and cost per token - produce a weighted
   score per candidate.

5. **Render** - The operator writes `grid-config.json`
   with pre-sorted candidates, admission state, and
   credential references. Praxis picks from the top.

## Workspace Crates

| Crate | Purpose |
|---|---|
| `operator` | K8s controllers, CRDs, operator binary |
| `swim` | foca wrapper, SWIM runtime, AES-256-GCM encryption |
| `crdt` | Delta CRDTs (LWW registers, OR-Sets, G-Counters) |
| `scoring` | Six-signal scoring engine and backend types |
| `certs` | Certificate generation and provider trait for mTLS |

## Visual Guide

For an interactive walkthrough with live diagrams
covering architecture, CRDs, scoring, SWIM, and CRDT
convergence, see the
[Grid Booklet](/praxis-grid-booklet.html).
