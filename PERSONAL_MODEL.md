---
schema: aether.architecture-document/v1
id: filament-personal-model
title: Filament Personal Model
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-personal-model]
depends_on: [filament-purpose, filament-vision, filament-principles, filament-epistemology, filament-ontology]
related: [filament-design]
supersedes: []
---

# Filament Personal Model

Filament assumes infrastructure is often operated by people who are context-switching, learning providers, responding to failures, or returning to a project months later.

The system should therefore reduce memory burden rather than reward hidden expertise. Plans should explain consequences, errors should identify the owning layer, examples should be runnable without production credentials, and recovery paths should be documented beside happy paths.

Defaults should minimize accidental cost and exposure. Destructive operations, public-network changes, privileged identities, state migrations, and irreversible provider features require stronger friction and clearer review than ordinary local validation.
