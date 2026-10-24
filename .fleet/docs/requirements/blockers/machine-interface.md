# Machine-readable interfaces

Scope: Upstream parity; full contract adoption held.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R51** Each supported JSON-mode operation shall emit exactly one JSON document on stdout after command-line parsing succeeds.
- [ ] **R52** JSON-mode operational failures shall include a diagnostic code.
- [ ] **R53** Failed operations shall return a nonzero exit status.
- [ ] **R54** JSON-mode human-readable messages shall be written to stderr.

## Scope notes

R50 remains held because its blanket scope imports fields tied to the undecided store/context model. It is not an atomic requirement. It needs a chosen command-and-field compatibility boundary before decomposition. R51 covers successful execution and operational errors, excluding help, version output, argument errors and interactive cancellation. These active requirements alone do not establish full TypeScript JSON compatibility.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R51 | — |
| R52 | — |
| R53 | — |
| R54 | — |

## Upstream basis

- [docs/agent-contract.md](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/docs/agent-contract.md)
