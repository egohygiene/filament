---
schema: aether.architecture-document/v1
id: filament-epistemology
title: Filament Epistemology
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-epistemology]
depends_on: [filament-purpose, filament-principles]
related: [filament-ai-constitution, filament-decisions]
supersedes: []
---

# Filament Epistemology

Infrastructure claims require stronger evidence than plausible configuration text.

## Evidence hierarchy

1. Provider and IaC-engine specifications or official documentation.
2. Executable schema validation and static checks.
3. Unit/contract tests against fixtures.
4. Disposable integration environments and plan evidence.
5. Verified consumer adoption.
6. Production observations, when safely available.

Architecture documents distinguish **observed**, **decided**, **proposed**, and **unknown** statements. Generated IaC is not considered correct merely because it parses.

Cost, quota, region, security, lifecycle, and provider behavior are time-sensitive and must be revalidated when relied upon. Filament should preserve source versions and test evidence so later maintainers can understand why a module was considered safe.
