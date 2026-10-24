# Project configuration — specification

[Requirements](project-configuration.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Current project context

- [ ] **R13** Instruction responses shall include the project context configured at invocation time.

### S02 — Artifact rules

- [ ] **R14** Artifact instruction responses shall include the rules configured for that artifact.

### S03 — Apply guidance

- [ ] **R15** Apply instruction responses shall include `operations.apply.guidance` when configured.

### S04 — Archive guidance

- [ ] **R16** Archive instruction responses shall include `operations.archive.guidance` when configured.

### S05 — Partial configuration recovery

- [ ] **R72** Project configuration loading shall warn when malformed input or an invalid field is discarded.
- [ ] **R73** Project configuration loading shall retain valid fields when another field is invalid.

## Pending work

Enumerate malformed and partially valid live configuration cases. Strict termination remains held as R12.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
