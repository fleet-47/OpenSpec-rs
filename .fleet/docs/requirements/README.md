# Dogfooding requirements

## Aligned scope

Priorities follow the agreed Fleet planning-to-archive dogfood cycle. Requirements are rearranged without changing their wording; link targets follow their destinations.

- [Blockers](blockers/README.md): Correct, safe planning, task tracking, validation and archive for a real Fleet change.
- [Fast followers](fast-followers/README.md): Compatibility, diagnostics, navigation and workflow delivery improvements after the first complete cycle.
- [Backlog](backlog/README.md): Held architecture and policy proposals; withdrawn spec-skipping requirements remain preserved separately as historical text.

## Recorded decisions — 2026-10-25

- Preserve the agreed priorities and exceptions from the dogfood classification.
- Remove the explicit `skip_specs` option from the target workflow. Preserve R22 and R23 as withdrawn source text; do not implement them.
- Verification reporting uses one passing-test count, enumerated failures and remedy pathways. This governs reporting, not archive runtime behaviour.
- Each blocker document has a `.specification.md` sidecar for boolean acceptance slices and pending work. Slice enumeration does not establish implementation status.
- Index descriptions contain at most 25 words.

The original source inventory contains 70 active requirements and nine held proposals. With R22 and R23 withdrawn, 68 remain active; nine remain held. Existing source wording and review history are preserved.

## Source inventory

[Original inventory and scope](../PATCH-REQUIREMENTS.md): Preserved source counts and scope; this priority index governs placement and withdrawal.

R32’s “non-skipped” wording and R33’s dependency on R22 are retained source text requiring reconciliation before their implementation.
