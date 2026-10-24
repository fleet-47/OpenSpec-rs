# Spec validation and merging

Scope: Upstream parity.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R34** Show, validate and archive shall interpret ADDED, MODIFIED, REMOVED and RENAMED delta operations consistently.
- [ ] **R35** Validation shall reject unpaired FROM/TO entries in RENAMED sections.
- [ ] **R36** Archive shall reject duplicate canonical requirement names in a capability.
- [ ] **R37** Archive shall reject a stale MODIFIED block that omits scenarios present in the current requirement.
- [ ] **R38** Spec merging shall preserve the contents of fenced code blocks.
- [ ] **R40** Validation shall report authored delta content that archive would discard.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R34 | — |
| R35 | — |
| R36 | — |
| R37 | — |
| R38 | — |
| R40 | — |

## Upstream basis

- [src/core/specs-apply.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/specs-apply.ts)
