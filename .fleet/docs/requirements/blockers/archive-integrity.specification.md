# Archive integrity — specification

[Requirements](archive-integrity.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Collision-safe destination reservation

- [ ] **R41** An archive-destination collision shall leave main specs and the active change unchanged.
- [ ] **R42** Archive shall claim its destination before writing main specs.

### S02 — Restoration after pre-completion failure

- [ ] **R43** After a pre-completion failure, archive rollback shall restore each affected spec’s prior state when it still matches the archive operation’s own change and recovery I/O succeeds.

### S03 — Concurrent-edit preservation during recovery

- [ ] **R44** Archive rollback shall refuse to overwrite a concurrent edit.

### S04 — Actionable recovery failure

- [ ] **R45** An archive recovery error shall identify the retained paths requiring operator action.

### S05 — Custom tracking warnings

- [ ] **R46** Archive shall warn about unfinished tasks in custom tracking files.

### S06 — Explicit and validated capability retirement

- [ ] **R47** Archive shall require `retire_capabilities: true` before deleting a main spec whose final requirement was removed.
- [ ] **R79** Archive shall leave capability spec files undeleted when `--no-validate` is set.

### S07 — Read-only archive instructions

- [ ] **R48** `instructions archive` shall return runtime guidance without modifying project files.

### S08 — Workflow stops on synchronization failure

- [ ] **R49** Generated archive workflows shall stop when spec synchronization fails.

## Pending work

Start with S01–S04 as the archive-safety cluster. Enumerate collision, failure and concurrent-edit cases on isolated copies of live data. Coordinate S05 with task tracking. Clarify whether withdrawing the metadata declaration also covers the separate archive --skip-specs flag.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
