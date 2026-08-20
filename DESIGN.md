---
schema: aether.architecture-document/v1
id: filament-design
title: Filament Design
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-design]
depends_on: [filament-purpose, filament-vision, filament-principles, filament-personal-model]
related: [filament-design-system]
supersedes: []
---

# Filament Design

Filament's primary experience is developer/operator comprehension rather than visual UI.

A good consumer experience should answer quickly:

- What capability am I adding?
- Which provider/engine/version does it require?
- What will it create or change?
- What will it cost or expose materially?
- Which values are required and which are sensitive?
- Where will state live?
- How do I validate without applying?
- How do I upgrade, import, rollback, or remove it?

Commands, examples, generated plans, and CI annotations should use the same domain language. Errors should point to the owning layer instead of collapsing provider, module, consumer, and policy failures into generic messages.
