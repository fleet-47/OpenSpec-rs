# Spec validation and merging — specification

[Requirements](spec-validation.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Consistent delta interpretation

- [ ] **R34** Show, validate and archive shall interpret ADDED, MODIFIED, REMOVED and RENAMED delta operations consistently.

### S02 — Paired rename validation

- [ ] **R35** Validation shall reject unpaired FROM/TO entries in RENAMED sections.

### S03 — Canonical-name uniqueness

- [ ] **R36** Archive shall reject duplicate canonical requirement names in a capability.

### S04 — Stale scenario protection

- [ ] **R37** Archive shall reject a stale MODIFIED block that omits scenarios present in the current requirement.

### S05 — Fenced-code preservation

- [ ] **R38** Spec merging shall preserve the contents of fenced code blocks.

### S06 — Discarded-content diagnostics

- [ ] **R40** Validation shall report authored delta content that archive would discard.

## Pending work

Enumerate real delta/target pairs for each operation and preservation check. Assess Sem for source impact analysis separately from Markdown merge correctness.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
