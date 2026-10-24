# Archive integrity

Scope: Upstream parity.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R41** An archive-destination collision shall leave main specs and the active change unchanged.
- [ ] **R42** Archive shall claim its destination before writing main specs.
- [ ] **R43** After a pre-completion failure, archive rollback shall restore each affected spec’s prior state when it still matches the archive operation’s own change and recovery I/O succeeds.
- [ ] **R44** Archive rollback shall refuse to overwrite a concurrent edit.
- [ ] **R45** An archive recovery error shall identify the retained paths requiring operator action.
- [ ] **R46** Archive shall warn about unfinished tasks in custom tracking files.
- [ ] **R47** Archive shall require `retire_capabilities: true` before deleting a main spec whose final requirement was removed.
- [ ] **R48** `instructions archive` shall return runtime guidance without modifying project files.
- [ ] **R49** Generated archive workflows shall stop when spec synchronization fails.
- [ ] **R79** Archive shall leave capability spec files undeleted when `--no-validate` is set.

## Scope notes

Prior state in R43 includes restoring a deleted spec and removing a newly created spec. A recovery failure cannot guarantee restoration; R45 covers reporting that outcome. Completion means the archive has been secured, before any optional cleanup.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R41 | — |
| R42 | — |
| R43 | — |
| R44 | [R43](archive-integrity.md) |
| R45 | [R43](archive-integrity.md) |
| R46 | [R74](task-tracking.md), [R75](task-tracking.md), [R76](task-tracking.md) |
| R47 | — |
| R48 | — |
| R49 | — |
| R79 | — |

## Upstream basis

- [src/core/archive.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/archive.ts)
