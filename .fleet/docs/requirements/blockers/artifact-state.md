# Artifact state and readiness

Scope: Upstream parity.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R17** Artifact status results shall list each prerequisite before its dependants.
- [ ] **R19** Artifact instruction responses shall identify every existing file matching the artifact output pattern.
- [ ] **R20** Artifact output resolution shall reject paths that escape the change directory.
- [ ] **R32** Status `isPlanningComplete` shall be true exactly when every non-skipped artifact exists.
- [ ] **R78** Status `isComplete` shall equal `isPlanningComplete`.

## Scope notes

Planning completion is an artifact-existence result. These requirements do not introduce an implementation-verification engine.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R17 | — |
| R19 | — |
| R20 | — |
| R32 | — |
| R78 | [R32](artifact-state.md) |

## Upstream basis

- [src/core/artifact-graph/types.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/artifact-graph/types.ts)
- [src/commands/workflow/instructions.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/commands/workflow/instructions.ts)
- [docs/agent-contract.md](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/docs/agent-contract.md)
