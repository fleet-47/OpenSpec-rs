# Project configuration

Scope: Upstream parity; one held policy.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R13** Instruction responses shall include the project context configured at invocation time.
- [ ] **R14** Artifact instruction responses shall include the rules configured for that artifact.
- [ ] **R15** Apply instruction responses shall include `operations.apply.guidance` when configured.
- [ ] **R16** Archive instruction responses shall include `operations.archive.guidance` when configured.
- [ ] **R72** Project configuration loading shall warn when malformed input or an invalid field is discarded.
- [ ] **R73** Project configuration loading shall retain valid fields when another field is invalid.

## Scope notes

R12 leaves “error” ambiguous between a diagnostic and terminating the operation. Upstream warns and uses valid fields or defaults; R72–R73 specify that behaviour. Terminating the operation remains a held policy choice, not a prerequisite for context or rules.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R13 | — |
| R14 | — |
| R15 | — |
| R16 | — |
| R72 | — |
| R73 | — |

## Upstream basis

- [src/core/project-config.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/project-config.ts)
