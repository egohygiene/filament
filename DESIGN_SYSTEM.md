---
schema: aether.architecture-document/v1
id: filament-design-system
title: Filament Design System
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-design-system]
depends_on: [filament-personal-model, filament-design]
related: [filament-ontology]
supersedes: []
---

# Filament Design System

Filament should use a stable semantic vocabulary across documentation, schemas, CLI output, reports, and automation:

- capability
- module
- stack
- provider
- engine
- consumer
- configuration
- secret reference
- plan
- apply
- state
- evidence
- policy
- release
- migration

Status language should distinguish `proposed`, `validated`, `planned`, `applied`, `verified`, `drifted`, `deprecated`, and `retired` rather than using ambiguous success labels.

Risk-sensitive output should clearly identify destructive actions, public exposure, identity/permission changes, state migrations, data-retention changes, and cost-impacting configuration. Machine-readable output should remain available wherever human summaries are produced.
