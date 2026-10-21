+++
title = "Old website archive"
type = "guides"
body_class = "historical-archive-page"
version_archive = true
exclude_search = true
weight = 5
+++

This archive preserves useful explanations and context from the original Praxis website. The source snapshot is the old site repository at commit <code>43fb08a65bdf4341d78adb829ffcd6cc5e4d8131</code>, reviewed on 2026-10-21.

> **Historical material.** These pages are unversioned and may describe old behavior, setup, feature counts, or security defaults. Use current release documentation for operating instructions. Archive pages are excluded from search and marked noindex.

The pages below are readable Hugo views. Exact original Markdown, source files, and static assets are kept separately under [the source archive](/archive/old-site/source/). Verify copied bytes with its [SHA-256 manifest](/archive/old-site/source/SHA256SUMS). The original site repository is licensed under [Apache-2.0](/archive/old-site/source/LICENSE).

The four original standalone HTML resources remain byte-for-byte at their historical URLs and load only when opened. They are historical visual guides, not current operating guidance; the Grid booklet is unversioned and the architecture diagram describes v0.3.1:

- [Praxis Core booklet](/praxis-core-booklet.html)
- [Praxis AI booklet](/praxis-ai-booklet.html)
- [Praxis Grid booklet](/praxis-grid-booklet.html)
- [Architecture diagram](/architecture/diagram.html)

The original HTML keeps root-relative `/img/...` references unchanged. Those images load when the site is served from the hostname root; a deployment under a URL subpath may not resolve them.

See the [source provenance note](/archive/old-site/source/PROVENANCE.md) for details.
