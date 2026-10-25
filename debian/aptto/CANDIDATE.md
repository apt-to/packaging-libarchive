# Candidate decision

The initial CVE-2025-5914 candidate requires over four billion RAR nodes. A type-size assertion would not reproduce the vulnerability in the installed package, and a full resource-heavy reproduction is unsuitable for this pilot.

Evaluate CVE-2026-4111 instead. Ubuntu marks focal affected and fixes it in `3.4.0-2ubuntu1.5+esm1`. Upstream commit `ec19fcbd20b18bd3b0fdcf2b3fb97789cd1bf575` supplies a small RAR5 fixture and a filter-window bound check. The real focal installed-package check passed: run [40189661421](https://github.com/apt-to/platform/actions/runs/40189661421) timed out on baseline `3.4.0-2ubuntu1.5`, then promptly rejected the fixture on `3.4.0-2ubuntu1.5+aptto1`; consumer and version-order checks passed. The candidate is regression-verified and awaits compatible scanner integration.

The source package remains libarchive, focal amd64, with immediate public binary access. This change does not alter the libxml2 seven-day policy.

References: https://ubuntu.com/security/CVE-2026-4111 and https://github.com/libarchive/libarchive/commit/ec19fcbd20b18bd3b0fdcf2b3fb97789cd1bf575
