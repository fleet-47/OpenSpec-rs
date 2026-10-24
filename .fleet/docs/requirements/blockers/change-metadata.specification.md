# Change metadata — specification

[Requirements](change-metadata.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Extension preservation on rewrite

- [ ] **R24** Metadata rewrites shall preserve top-level extension fields matching `^x-\S+$`.

### S02 — Unsupported-key diagnostics

- [ ] **R25** Validation shall report unrecognized metadata keys outside the supported extension namespace.

## Pending work

Define acceptance cases after withdrawal of R23. Removing the explicit skip declaration does not silently select migration behaviour for existing metadata.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
