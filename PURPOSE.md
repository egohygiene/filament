---
schema: aether.architecture-document/v1
id: filament-purpose
title: Filament Purpose
kind: architecture-document
version: 0.1.0
status: provisional
owners:
  - egohygiene
created: 2026-08-19
updated: 2026-08-19
governed_by:
  - architecture-purpose
depends_on: []
related:
  - filament-vision
  - filament-principles
supersedes: []
---

# Filament Purpose

Filament is the Ego Hygiene repository for reusable infrastructure-as-code building blocks that product and platform repositories can compose without copying cloud or deployment implementation into each codebase.

Its purpose is to make infrastructure definitions versioned, reviewable, portable, testable, and reusable while preserving explicit ownership boundaries.

Filament should own reusable infrastructure modules, stacks, interfaces, examples, validation, and provider adapters when those artifacts are independently useful across repositories.

Filament does not own developer-container environments, shell behavior, GitHub Actions orchestration, organization policy, application deployment intent, or product-specific infrastructure state. Realm, Mantle, Relay, Hygiene, and consuming repositories retain those responsibilities.

The exact provider/tooling surface is intentionally provisional. Terraform/OpenTofu, Pulumi, Crossplane, cloud-native templates, and other approaches should be evaluated from consumer needs rather than selected as ideology.
