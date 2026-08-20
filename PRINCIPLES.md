---
schema: aether.architecture-document/v1
id: filament-principles
title: Filament Principles
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-principles]
depends_on: [filament-purpose, filament-vision]
related: [filament-pillars, filament-foundations]
supersedes: []
---

# Filament Principles

1. **Reuse beats copying.** Shared infrastructure behavior belongs in versioned modules when at least two consumers need the same capability.
2. **Intent and implementation stay separate.** Consumers own product-specific intent; Filament owns reusable implementation contracts.
3. **Plan before apply.** Infrastructure changes must be inspectable before mutation.
4. **Consumers retain state ownership.** Filament must not become the hidden canonical holder of production state or credentials.
5. **Provider choices are explicit.** Portability is preferred, but false abstraction across materially different providers is avoided.
6. **Immutable inputs and provenance matter.** Modules, providers, dependencies, and generated plans should be attributable to versions or digests.
7. **Secrets never become template data.** Contracts refer to secret inputs without embedding values.
8. **Testing precedes production.** Static validation, policy checks, unit/contract tests, and disposable integration environments should precede live infrastructure changes.
9. **Small modules compose; giant platforms do not.** Prefer bounded capabilities over a universal mega-stack.
10. **Recovery is part of design.** Upgrade, migration, import, rollback, and teardown semantics are first-class.
