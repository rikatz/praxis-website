+++
title = "Original examples"
type = "guides"
body_class = "historical-archive-page"
version_archive = true
exclude_search = true
url = "/archive/old-site/examples/"
archive_title_in_content = true
weight = 30
+++

# Original examples

> **Historical example catalog.** The old page fetched YAML from mutable GitHub main. The local copies linked below come from selected Praxis v0.7.2 and Praxis AI v0.7.0 commits. Their checksums preserve those snapshot bytes; they cannot establish the exact bytes returned by the old downloads.

The new [versioned example catalog](/examples/) is current discovery. The exact [old example-data source](/archive/old-site/source/src/data/examples.ts) and [old page source](/archive/old-site/source/src/pages/examples/index.tsx) are preserved too.

## Traffic Management

- **Basic Reverse Proxy** — Minimal single-listener, single-cluster proxy <code>examples/configs/traffic-management/basic-reverse-proxy.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/basic-reverse-proxy.yaml)
- **Path-Based Routing** — Route by URL path prefix to separate clusters <code>examples/configs/traffic-management/path-based-routing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/path-based-routing.yaml)
- **Host-Based Routing** — Route by Host header; one listener, multiple domains <code>examples/configs/traffic-management/hosts.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/hosts.yaml)
- **Canary Routing** — Weighted traffic split for canary deployments <code>examples/configs/traffic-management/canary-routing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/canary-routing.yaml)
- **Circuit Breaker** — Per-cluster circuit breaker with closed/open/half-open states <code>examples/configs/traffic-management/circuit-breaker.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/circuit-breaker.yaml)
- **Round Robin** — Default strategy: even distribution across backends <code>examples/configs/traffic-management/round-robin.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/round-robin.yaml)
- **Weighted Load Balancing** — Proportional traffic split via per-endpoint weights <code>examples/configs/traffic-management/weighted-load-balancing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/weighted-load-balancing.yaml)
- **Endpoint Selector** — Header-based upstream endpoint selection for deterministic routing <code>examples/configs/traffic-management/endpoint-selector.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/endpoint-selector.yaml)
- **gRPC Detection** — Automatic gRPC and gRPC-Web content-type detection <code>examples/configs/traffic-management/grpc-detection.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/grpc-detection.yaml)
- **Iterative Request Router Failover** — Iterative sub-request execution with failover across upstreams <code>examples/configs/traffic-management/iterative-request-router-failover.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/iterative-request-router-failover.yaml)
- **Iterative Request Router Origin Failover** — Origin-based failover with iterative request routing <code>examples/configs/traffic-management/iterative-request-router-origin-failover.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/iterative-request-router-origin-failover.yaml)
- **Least Connections** — Route to backend with fewest in-flight requests <code>examples/configs/traffic-management/least-connections.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/least-connections.yaml)
- **Session Affinity** — consistent_hash to pin a user to one backend <code>examples/configs/traffic-management/session-affinity.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/session-affinity.yaml)
- **Health Checks** — Active HTTP and TCP health check probes per cluster <code>examples/configs/traffic-management/health-checks.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/health-checks.yaml)
- **Timeout** — 504 when upstream exceeds a latency SLA <code>examples/configs/traffic-management/timeout.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/timeout.yaml)
- **Rate Limiting** — Token bucket rate limiter with per-IP and global modes <code>examples/configs/traffic-management/rate-limiting.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/rate-limiting.yaml)
- **Static Response** — Fixed response without upstream <code>examples/configs/traffic-management/static-response.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/static-response.yaml)
- **Redirect** — 3xx redirects with path/query template substitution <code>examples/configs/traffic-management/redirect.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/redirect.yaml)
- **Hostname Upstream** — Resolve hostname upstream endpoints such as localhost:9000 <code>examples/configs/traffic-management/hostname-upstream.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/traffic-management/hostname-upstream.yaml)

## AI / Inference

- **AI Inference Body-Based Routing** — Route LLM requests by model field in JSON body <code>examples/configs/ai-inference-body-based-routing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/ai/examples/configs/ai-inference-body-based-routing.yaml)
- **JSON-RPC Routing** — Route JSON-RPC 2.0 requests by method for MCP and A2A protocols <code>examples/configs/json-rpc-routing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/ai/examples/configs/json-rpc-routing.yaml)
- **MCP Classifier Routing** — Route MCP requests by body-derived method and tool name <code>examples/configs/mcp-classifier-routing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/ai/examples/configs/mcp-classifier-routing.yaml)
- **Model-to-Header Routing** — Route by model field in JSON body via X-Model header <code>examples/configs/model-to-header-routing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/ai/examples/configs/model-to-header-routing.yaml)
- **Prompt Enrichment** — Inject system messages into chat completion requests <code>examples/configs/prompt-enrichment.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/ai/examples/configs/prompt-enrichment.yaml)

## Payload Processing

- **JSON-RPC** — Parse JSON-RPC 2.0 envelopes and extract method/id/kind <code>examples/configs/payload-processing/json-rpc.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/json-rpc.yaml)
- **Stream Buffer** — Stream-buffered body inspection before forwarding <code>examples/configs/payload-processing/stream-buffer.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/stream-buffer.yaml)
- **Compression** — Gzip, brotli, and zstd response compression <code>examples/configs/payload-processing/compression.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/compression.yaml)
- **Multi-Field Extraction** — Extract multiple JSON fields into headers in one pass <code>examples/configs/payload-processing/multi-field-extraction.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/multi-field-extraction.yaml)
- **Conditional Field Extraction** — Apply json_body_field only on matching request paths <code>examples/configs/payload-processing/conditional-field-extraction.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/conditional-field-extraction.yaml)
- **Field Extraction Access Control** — Extract tenant_id from body for header-based routing <code>examples/configs/payload-processing/field-extraction-access-control.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/field-extraction-access-control.yaml)
- **Body Size Limit with Extraction** — Global body size ceiling with json_body_field extraction <code>examples/configs/payload-processing/body-size-limit-with-extraction.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/body-size-limit-with-extraction.yaml)
- **Multi-Listener Body Pipeline** — Three listeners with different body processing strategies <code>examples/configs/payload-processing/multi-listener-body-pipeline.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/payload-processing/multi-listener-body-pipeline.yaml)

## Security

- **CSRF Protection** — CSRF protection via origin validation <code>examples/configs/security/csrf.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/csrf.yaml)
- **Forwarded Headers** — X-Forwarded-For/Proto/Host with trusted proxies <code>examples/configs/security/forwarded-headers.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/forwarded-headers.yaml)
- **Guardrails** — Reject requests matching header or body string/regex rules <code>examples/configs/security/guardrails.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/guardrails.yaml)
- **IP ACL** — Allow or deny by source IP/CIDR <code>examples/configs/security/ip-acl.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/ip-acl.yaml)
- **Downstream Read Timeout** — Protect against slow client attacks with read timeouts <code>examples/configs/security/downstream-read-timeout.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/downstream-read-timeout.yaml)
- **CORS** — CORS preflight handling with origin validation <code>examples/configs/security/cors.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/cors.yaml)
- **Basic Auth** — HTTP Basic Authentication (RFC 7617) with credential validation <code>examples/configs/security/basic-auth.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/basic-auth.yaml)
- **Peer Identity Trust** — mTLS peer identity validation for workload authentication <code>examples/configs/security/peer-identity-trust.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/peer-identity-trust.yaml)
- **Policy** — CPEX policy engine with JWT, APL route policy, and PII scanning <code>examples/configs/security/policy.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/policy.yaml)
- **Policy HTTP** — HTTP-specific policy configuration with route-level enforcement <code>examples/configs/security/policy-http.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/policy-http.yaml)
- **Credential Injection** — Inject per-cluster API credentials and strip client tokens <code>examples/configs/security/credential-injection.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/security/credential-injection.yaml)

## Observability

- **Access Logging** — Access log with sampling <code>examples/configs/observability/access-logging.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/observability/access-logging.yaml)
- **Request ID and Logging** — request_id + access_log: correlation IDs and structured logs <code>examples/configs/observability/logging.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/observability/logging.yaml)
- **TCP Access Log** — Structured JSON TCP connection logging <code>examples/configs/observability/tcp-access-log.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/observability/tcp-access-log.yaml)

## Transformation

- **Header Manipulation** — Add, overwrite, and remove request/response headers <code>examples/configs/transformation/header-manipulation.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/transformation/header-manipulation.yaml)
- **Path Rewriting** — Strip prefix, add prefix, or regex replace on request paths <code>examples/configs/transformation/path-rewriting.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/transformation/path-rewriting.yaml)
- **URL Rewriting** — Regex path transformation and query string manipulation <code>examples/configs/transformation/url-rewriting.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/transformation/url-rewriting.yaml)

## Protocols

- **TCP Proxy** — L4 bidirectional TCP forwarding <code>examples/configs/protocols/tcp-proxy.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tcp-proxy.yaml)
- **TCP Timeouts** — TCP proxy with idle and max duration timeouts <code>examples/configs/protocols/tcp-timeouts.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tcp-timeouts.yaml)
- **TCP Consistent Hash** — TCP load balancing with consistent-hash client IP affinity <code>examples/configs/protocols/tcp-consistent-hash.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tcp-consistent-hash.yaml)
- **TCP Least Connections** — TCP load balancing via least-connections strategy <code>examples/configs/protocols/tcp-least-connections.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tcp-least-connections.yaml)
- **TCP Round Robin** — TCP round-robin load balancing across replicas <code>examples/configs/protocols/tcp-round-robin.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tcp-round-robin.yaml)
- **Mixed Protocol** — HTTP + TCP listeners on one server <code>examples/configs/protocols/mixed-protocol.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/mixed-protocol.yaml)
- **TLS Termination** — HTTPS listener; plain HTTP to backends <code>examples/configs/protocols/tls-termination.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-termination.yaml)
- **TLS Cipher Suites** — Restrict accepted TLS cipher suites per listener <code>examples/configs/protocols/tls-cipher-suites.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-cipher-suites.yaml)
- **TLS SNI Routing** — Route TLS connections by SNI hostname without termination <code>examples/configs/protocols/tls-sni-routing.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-sni-routing.yaml)
- **TCP TLS mTLS** — TCP proxy with mutual TLS <code>examples/configs/protocols/tcp-tls-mtls.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tcp-tls-mtls.yaml)
- **TCP TLS Termination** — TCP proxy with TLS termination <code>examples/configs/protocols/tcp-tls-termination.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tcp-tls-termination.yaml)
- **TLS HTTP Re-encrypt** — TLS termination with re-encryption to upstream <code>examples/configs/protocols/tls-http-reencrypt.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-http-reencrypt.yaml)
- **TLS mTLS Both** — mTLS on both listener and upstream <code>examples/configs/protocols/tls-mtls-both.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-mtls-both.yaml)
- **TLS mTLS Listener** — mTLS on listener (require client cert) <code>examples/configs/protocols/tls-mtls-listener.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-mtls-listener.yaml)
- **TLS mTLS Listener Request** — mTLS on listener (request client cert) <code>examples/configs/protocols/tls-mtls-listener-request.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-mtls-listener-request.yaml)
- **TLS mTLS Upstream** — mTLS to upstream (client cert) <code>examples/configs/protocols/tls-mtls-upstream.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-mtls-upstream.yaml)
- **TLS Multi-Certificate** — SNI-based multi-certificate selection <code>examples/configs/protocols/tls-multi-cert.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-multi-cert.yaml)
- **TLS Verify Disabled** — Upstream TLS with verification disabled <code>examples/configs/protocols/tls-verify-disabled.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-verify-disabled.yaml)
- **TLS Version Constraint** — Minimum TLS version constraint <code>examples/configs/protocols/tls-version-constraint.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/tls-version-constraint.yaml)
- **Upstream CA File** — Global upstream CA file reference <code>examples/configs/protocols/upstream-ca-file.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/upstream-ca-file.yaml)
- **Upstream TLS** — Plain HTTP listener; TLS to upstream with SNI <code>examples/configs/protocols/upstream-tls.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/upstream-tls.yaml)
- **WebSocket** — Transparent WebSocket upgrade proxying over HTTP <code>examples/configs/protocols/websocket.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/protocols/websocket.yaml)

## Pipeline

- **Default Config** — Built-in default config (static JSON on /) <code>core/src/config/default.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/crates/core/src/config/default.yaml)
- **Composed Chains** — Multiple named chains composed per listener <code>examples/configs/pipeline/composed-chains.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/pipeline/composed-chains.yaml)
- **Conditional Filters** — when/unless conditions on request and response phase <code>examples/configs/pipeline/conditional-filters.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/pipeline/conditional-filters.yaml)
- **Branch Chains** — All branch chain scenarios in one config (six patterns) <code>examples/configs/pipeline/branch-chains.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/pipeline/branch-chains.yaml)
- **Failure Mode** — Failure mode behavior (open continues, closed rejects on error) <code>examples/configs/pipeline/failure-mode.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/pipeline/failure-mode.yaml)
- **Iterative Request Router Sequence** — Sequential sub-request execution through an iterative pipeline <code>examples/configs/pipeline/iterative-request-router-sequence.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/pipeline/iterative-request-router-sequence.yaml)
- **Iterative Request Router Circuit Breaker** — Iterative request routing with circuit breaker integration <code>examples/configs/pipeline/iterative-request-router-circuit-breaker.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/pipeline/iterative-request-router-circuit-breaker.yaml)

## Branching

- **Unconditional Branch** — Always-fire branch for injecting side-effect chains <code>examples/configs/branching/unconditional-branch.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/unconditional-branch.yaml)
- **Conditional Terminal** — Short-circuit the pipeline with a static response on result match <code>examples/configs/branching/conditional-terminal.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/conditional-terminal.yaml)
- **Conditional Skip-To** — Skip filters by jumping to a named rejoin point on result match <code>examples/configs/branching/conditional-skip-to.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/conditional-skip-to.yaml)
- **Multiple Branches** — Multiple branches on one filter with first-match-wins evaluation <code>examples/configs/branching/multiple-branches.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/multiple-branches.yaml)
- **Named Chain Ref** — Reference a top-level chain by name instead of inline definition <code>examples/configs/branching/named-chain-ref.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/named-chain-ref.yaml)
- **Nested Branches** — Multi-level decision tree with branches inside branches <code>examples/configs/branching/nested-branches.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/nested-branches.yaml)
- **Reentrance** — Loop back to a named filter with max_iterations cap <code>examples/configs/branching/reentrance.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/reentrance.yaml)
- **Cross-Chain Flat** — Branch across concatenated chains via flat pipeline name index <code>examples/configs/branching/cross-chain-flat.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/branching/cross-chain-flat.yaml)

## Operations

- **Production Gateway** — Full production setup with composed chains <code>examples/configs/operations/production-gateway.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/operations/production-gateway.yaml)
- **Multi-Listener** — Multiple listeners sharing a filter chain <code>examples/configs/operations/multi-listener.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/operations/multi-listener.yaml)
- **Hot Reload** — Dynamic config reload without restart <code>examples/configs/operations/hot-reload.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/operations/hot-reload.yaml)
- **Admin Interface** — Admin interface with health endpoints <code>examples/configs/operations/admin-interface.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/operations/admin-interface.yaml)
- **Container Default** — Default containerized deployment with public binding <code>examples/configs/operations/container-default.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/operations/container-default.yaml)
- **Max Connections** — Per-listener connection limit with 503 rejection <code>examples/configs/operations/max-connections.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/operations/max-connections.yaml)
- **Log Overrides** — Per-module log level tuning via runtime config <code>examples/configs/operations/log-overrides.yaml</code> · [selected snapshot bytes](/archive/old-site/source/examples/praxis/examples/configs/operations/log-overrides.yaml)
