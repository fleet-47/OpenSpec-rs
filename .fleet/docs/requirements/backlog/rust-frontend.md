# Rust frontend integration

Scope: Held architecture choice.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Held for review — excluded from implementation

- **R63 — held:** Each operation used by the unified frontend shall be callable through the Rust library.
- **R64 — held:** Library operations shall accept an explicit project context.
- **R65 — held:** Library operations shall return typed results or errors.
- **R66 — held:** Library operations shall leave the process working directory unchanged.
- **R67 — held:** Library operations shall leave stdout and stderr rendering to the caller.
- **R68 — held:** Library operations shall return control to the caller instead of terminating the process.

## Scope notes

A single Rust frontend can invoke backend CLIs or embed backend libraries. The thin-router goal does not choose between those interfaces. R63–R68 apply only if embedded OpenSpec library access is selected; CLI parity does not depend on them.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R63 | — |
| R64 | [R63](rust-frontend.md) |
| R65 | [R63](rust-frontend.md) |
| R66 | [R64](rust-frontend.md) |
| R67 | [R65](rust-frontend.md) |
| R68 | [R65](rust-frontend.md) |
