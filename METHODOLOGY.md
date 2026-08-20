---
schema: aether.architecture-document/v1
id: filament-methodology
title: Filament Methodology
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-methodology]
depends_on: [filament-principles, filament-epistemology, filament-ai-constitution, filament-foundations, filament-architecture]
related: [filament-roadmap]
supersedes: []
---

# Filament Methodology

New infrastructure capabilities follow:

1. **Problem** — identify at least one real consumer and the repeated infrastructure outcome.
2. **Boundary** — decide what belongs in Filament versus the consumer/provider.
3. **Spec** — define inputs, outputs, security assumptions, lifecycle, compatibility, and cost-sensitive choices.
4. **Engine/provider decision** — evaluate the smallest implementation path using current primary documentation.
5. **Implement** — create the module/adapter without embedding consumer-specific state.
6. **Validate** — schema, formatting, static analysis, policy, unit/contract tests, and disposable integration tests.
7. **Plan** — prove a reviewable non-destructive path.
8. **Release** — version artifacts and migration guidance.
9. **Adopt** — consume from a pinned real/disposable repository.
10. **Observe** — capture defects, drift, costs, ergonomics, and missing abstractions before broadening the platform.

A second provider or engine should be added because a consumer needs it, not merely to make a matrix look complete.
