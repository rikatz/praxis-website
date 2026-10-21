# Original route mapping

The mapping below is the build input for the 40 historical page and standalone-resource URLs. The broader [`original-site-inventory.json`](original-site-inventory.json) records documentation pages and headings, homepage and example copy, feed endpoints, and all original static files. It is a coverage ledger only; `tools/prepare-routes.py` continues to use this mapping as the sole redirect configuration.

Canonical source pages use the selected product release; root aliases should preserve incoming fragments and accept both the crawled path and its slash variant. Paths that already exist on the new site stay in place. The old standalone HTML resources are retained byte-for-byte at their original paths, so those paths are kept instead of redirected to adapted guides.

All 44 original `/img/` files are also retained byte-for-byte at those public paths because the standalone resources reference them. Their archive-source copies and hashes are listed in the coverage ledger; the old `CNAME` is preserved only as source because it names the retired host.

The exact HTML retains root-relative image references. Those references work for a root-hosted deployment; a subpath deployment may not resolve them, since changing them would break the byte-for-byte requirement.

The current Grid route is external discovery, not an imported release catalog. The original Grid pages are preserved under `/archive/old-site/docs/grid/`; their legacy routes still lead to `/grid/` until the dedicated historical-route pass. The blog contains the one retained announcement, so its index and post routes stay in place; archive and tag paths lead back to the blog. Current examples and search pages remain at their existing routes.

| Original path | Destination | Treatment |
| --- | --- | --- |
| `/` | `/` | Keep the ecosystem homepage. |
| `/blog` | `/blog/` | Keep the blog index. |
| `/blog/archive` | `/blog/` | Alias to the one-post blog. |
| `/blog/tags` | `/blog/` | Alias to the one-post blog. |
| `/blog/tags/announcement` | `/blog/welcome/` | Alias to the retained announcement. |
| `/blog/welcome` | `/blog/welcome/` | Keep the retained announcement. |
| `/docs/architecture/connection-lifecycle` | `/praxis/v0.7.2/architecture/connection-lifecycle/` (`docs/architecture/connection-lifecycle.md`) | Release-resolved page. |
| `/docs/architecture/crate-layout` | `/praxis/v0.7.2/architecture/crate-layout/` (`docs/architecture/crate-layout.md`) | Release-resolved page. |
| `/docs/architecture/filter-pipeline` | `/praxis/v0.7.2/architecture/pipeline-concepts/` (`docs/architecture/pipeline-concepts.md`) | Release-resolved pipeline explanation; branch-chain reference remains linked. |
| `/docs/architecture/http-correctness` | `/praxis/v0.7.2/architecture/http-correctness/` (`docs/architecture/http-correctness.md`) | Release-resolved page. |
| `/docs/architecture/interactive-diagram` | `/visual-guides/praxis/` | Alias to the current Core guide. |
| `/docs/architecture/overview` | `/praxis/v0.7.2/architecture/overview/` (`docs/architecture/overview.md`) | Release-resolved page. |
| `/docs/architecture/payload-processing` | `/praxis/v0.7.2/architecture/payload-processing/` (`docs/architecture/payload-processing.md`) | Release-resolved page. |
| `/docs/architecture/pingora-integration` | `/praxis/v0.7.2/architecture/connection-lifecycle/` (`docs/architecture/connection-lifecycle.md`) | Closest current runtime-lifecycle explanation; the v0.7.2 overview identifies Pingora ownership. |
| `/docs/architecture/system-design` | `/praxis/v0.7.2/architecture/overview/` (`docs/architecture/overview.md`) | Current overview replaces the old combined design page. |
| `/docs/configuration/overview` | `/praxis/v0.7.2/operating/configuration/` (`docs/operating/configuration.md`) | Release-resolved reference. |
| `/docs/development/benchmarks` | `/praxis/v0.7.2/benchmarks/` (`docs/benchmarks.md`) | Release-resolved methodology; no unmeasured results are added. |
| `/docs/development/contributing` | `/guides/extend/` | Developer setup and contribution entry points. |
| `/docs/development/proposals` | `https://github.com/praxis-proxy/enhancements` | External canonical proposal project. |
| `/docs/development/release` | `/praxis/v0.7.2/release/` (`docs/release.md`) | Release-resolved process. |
| `/docs/development/testing` | `/guides/extend/` (`docs/developing/getting-started.md`) | Developer setup includes test commands; source path is linked there. |
| `/docs/filters/` | `/praxis/v0.7.2/filters/` (`docs/filters/README.md`) | Release-resolved filter index. |
| `/docs/filters/custom-filters` | `/praxis/v0.7.2/filters/http-filter-tutorial/` (`docs/filters/http-filter-tutorial.md`) | Release-resolved Rust tutorial. |
| `/docs/filters/extensions` | `/praxis/v0.7.2/filters/extensions/` (`docs/filters/extensions.md`) | Release-resolved extension guide. |
| `/docs/filters/filter-model` | `/praxis/v0.7.2/filters/#filter-model` (`docs/filters/README.md`) | Release-resolved page and matching heading anchor. |
| `/docs/getting-started/features` | `/praxis/capabilities/` | Website-owned v0.7.2 capability/build/support matrix. |
| `/docs/getting-started/installation` | `/guides/install/` | Website-owned verified installation choices. |
| `/docs/getting-started/introduction` | `/praxis/` | Updated runnable-proxy overview. |
| `/docs/getting-started/quickstart` | `/guides/first-proxy/` | Website-owned end-to-end reverse-proxy tutorial. |
| `/docs/grid/concepts` | `/grid/` | Current Grid discovery; original unversioned concepts page is preserved in the historical archive. |
| `/docs/grid/getting-started` | `/grid/` | Current Grid discovery; original unversioned setup page is preserved in the historical archive. |
| `/docs/grid/overview` | `/grid/` | Current Grid discovery; original unversioned overview is preserved in the historical archive. |
| `/docs/protocols/tls` | `/praxis/v0.7.2/operating/tls/` (`docs/operating/tls.md`) | Release-resolved TLS/mTLS guide. |
| `/docs/security/hardening` | `/praxis/v0.7.2/operating/security-hardening/` (`docs/operating/security-hardening.md`) | Release-resolved hardening guide. |
| `/examples/` | `/examples/` | Keep the new versioned example discovery hub. |
| `/praxis-ai-booklet.html` | `/praxis-ai-booklet.html` | Keep the original standalone HTML resource byte-for-byte. |
| `/praxis-core-booklet.html` | `/praxis-core-booklet.html` | Keep the original standalone HTML resource byte-for-byte. |
| `/praxis-grid-booklet.html` | `/praxis-grid-booklet.html` | Keep the original standalone HTML resource byte-for-byte. |
| `/search` | `/search/` | Keep the current local search page. |
| `/architecture/diagram.html` | `/architecture/diagram.html` | Keep the original standalone HTML resource byte-for-byte. |

## Alias notes

- The inventory stores a mix of slash and non-slash routes. Test both forms at the actual configured base path.
- Redirects from old source pages to versioned docs should preserve fragments. Keep historical heading IDs where a current heading differs; `/docs/filters/filter-model` specifically maps to `#filter-model` on the current filter index.
- If a later catalog update changes the default Praxis tag, review the versioned destinations before regenerating aliases. The current map intentionally uses v0.7.2.
- `docs/original-route-mapping.json` is the machine-readable counterpart for the root alias work.
