# Task tracking — specification

[Requirements](task-tracking.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Schema-selected task aggregation

- [ ] **R26** Apply instructions shall resolve task files from the selected schema’s `apply.tracks` value.
- [ ] **R27** Apply task-progress calculations shall aggregate every file matched by an `apply.tracks` glob.
- [ ] **R28** Each task returned by apply instructions shall identify its source file.

### S02 — Checkbox recognition and completion

- [ ] **R30** Task parsing shall recognize checkbox list items using `-`, `*`, `+`, or one-to-nine-digit ordered markers ending in `.` or `)`.
- [ ] **R74** Task accounting shall mark a recognized checkbox complete if and only if its marker is `x` or `X`.

### S03 — List and archive task discovery

- [ ] **R75** List and archive task accounting shall use the schema artifact whose output pattern equals `apply.tracks`, or the `tasks` artifact when `apply.tracks` is absent.
- [ ] **R76** List and archive task accounting shall fall back to the change’s top-level `tasks.md` when schema resolution yields no tracking files.

### S04 — Apply without declared tracking

- [ ] **R77** Apply instructions shall report no tracked tasks when the schema omits `apply.tracks`.

## Pending work

Enumerate real tracking layouts, marker variants and per-command fallbacks. Coordinate artifact readiness and archive warnings without equating task checkboxes with accepted implementation.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
