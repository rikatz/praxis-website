+++
title = "Old homepage"
type = "guides"
body_class = "historical-archive-page"
version_archive = true
exclude_search = true
url = "/archive/old-site/homepage/"
archive_title_in_content = true
weight = 10
+++

# The proxy built for AI infrastructure

> **Historical homepage copy.** This text is preserved from the old website at commit <code>43fb08a65bdf4341d78adb829ffcd6cc5e4d8131</code> (2026-10-21). Product claims reflect that unversioned page and may not describe a selected release. See the [current Praxis homepage](/) and the [exact React source](/archive/old-site/source/src/pages/index.tsx).

One proxy between your apps and every AI provider. Route traffic, manage keys, enforce guardrails — all from a single config file. Built in Rust for performance and safety.

[Get started](/praxis/) · [GitHub](https://github.com/praxis-proxy/praxis)

## Why teams choose Praxis

### Route to Any AI Provider

Send requests to OpenAI, Anthropic, or your own models. Praxis reads the model name, injects the right API key, and routes to the right upstream — your app never touches a credential.

### Built for Claude Code & Codex

Native MCP gateway — aggregate tools from multiple servers behind one endpoint. Praxis handles session management, credential injection, and tool-call routing so your AI coding agents work securely at scale.

### Build Pipelines, Not Middleware

Stack rate limiting, auth, guardrails, and routing in any order using a simple YAML config. 50+ built-in filters ship ready to use, and you can write your own in Rust.

### Security Without the Setup

TLS everywhere, zero unsafe code, CORS and rate limiting out of the box. Praxis ships locked down so you don\

### Ship Changes Without Downtime

HTTP/1.1, HTTP/2, gRPC, WebSocket, TCP — all supported. Hot-reload your config at runtime without dropping a single connection.

## Understand the architecture

Interactive visual guides that walk through how Praxis works with animated diagrams.

### Praxis Core

How requests flow through filter pipelines, how chains compose, and how config reloads without dropping a connection.

[Read the Praxis Core guide](/praxis-core-booklet.html)

### Praxis AI

How the AI gateway classifies requests, routes to providers, injects credentials, and speaks MCP and A2A.

[Read the Praxis AI guide](/praxis-ai-booklet.html)

### Praxis Grid

How the distributed control plane converges state with CRDTs, discovers sites with SWIM, and scores routes by locality.

[Read the Praxis Grid guide](/praxis-grid-booklet.html)

## Deploy in minutes, not weeks

Apache 2.0 licensed. One binary, one config file, production-ready.

[Quick Start](/guides/first-proxy/) · [Examples](/examples/) · [GitHub](https://github.com/praxis-proxy/praxis)
