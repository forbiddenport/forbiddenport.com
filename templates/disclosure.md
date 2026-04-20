<!--
  Reference template for a CVE / security disclosure.
  Copy this into content/disclosures/<slug>.md and edit.
  URL will be /disclosures/<slug>/
  The fields cve/vendor/product/severity render automatically as a
  spec block under the title (see themes/minimal/layouts/_default/single.html).
-->

---
title: "CVE-YYYY-NNNNN — vendor/product"   # required — keep the CVE ID + target in the title
date: 2026-04-20                           # required — public disclosure date
draft: true                                # set false when ready
tags: ["cve", "web"]                       # optional — "cve" is a useful tag; add category tags
summary: >                                 # required — one-line description of the bug
  What the bug is in one sentence. Will show up in the RSS feed and on
  the home page when the section index is populated.

# Spec block fields — all optional, all rendered together if any are set.
cve: "CVE-YYYY-NNNNN"                      # assigned CVE ID, if any
vendor: "Vendor Name"                      # company / maintainer
product: "product-name"                    # affected product / package
severity: "High (CVSS 8.2)"                # free-form; include CVSS if assigned
---

## Summary

One short paragraph. What the bug is, where it lives in the codebase,
how it's reachable, and what impact looks like. Readers who only read
this far should understand the shape of the issue.

## Timeline

- **YYYY-MM-DD** — Bug found (context: engagement, research, fuzz run, etc.)
- **YYYY-MM-DD** — Reported to security@vendor.example via [channel]
- **YYYY-MM-DD** — Vendor acknowledged, assigned internal tracker
- **YYYY-MM-DD** — Patch released in version X.Y.Z
- **YYYY-MM-DD** — Public disclosure (reason: 90-day window / coordinated / etc.)

## Details

Full technical write-up. Show the vulnerable code or path, explain why
it's broken, and how the fix addresses it. Inline code samples welcome.

```c
// minimized vulnerable excerpt — rename variables for readability,
// but keep semantics faithful to the original.
int verify(...) {
    ...
}
```

If a PoC is appropriate to publish (post-patch, no live exploitation
concern), include a minimized one:

```
0000  ff fe 01 2a 2a 2a                  ......
```

## Impact

Short, factual. Who's affected, under what preconditions, what the
worst-case outcome is. Avoid hype; avoid minimizing.

## Mitigations

For admins running the affected product before the patch: what stops
the attack. Keep it concrete — "apply patch X.Y.Z" is fine if nothing
else exists.

## References

- [NVD record](https://nvd.nist.gov/vuln/detail/CVE-YYYY-NNNNN)
- [Vendor advisory](https://vendor.example.com/security/...)
- [Patch commit](https://github.com/.../commit/...)
- [Related write-up]({{< ref "some-related-post" >}})
