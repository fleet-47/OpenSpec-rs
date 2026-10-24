# Machine-readable interfaces — specification

[Requirements](machine-interface.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Single JSON document and stderr separation

- [ ] **R51** Each supported JSON-mode operation shall emit exactly one JSON document on stdout after command-line parsing succeeds.
- [ ] **R54** JSON-mode human-readable messages shall be written to stderr.

### S02 — Observable operational failure

- [ ] **R52** JSON-mode operational failures shall include a diagnostic code.
- [ ] **R53** Failed operations shall return a nonzero exit status.

## Pending work

Enumerate the supported repo-local operations and failure cases for these checks. Full upstream contract adoption remains held as R50.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
