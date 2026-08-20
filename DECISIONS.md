---
schema: aether.architecture-document/v1
id: filament-decisions
title: Filament Decisions
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-decisions]
depends_on: [filament-principles, filament-epistemology, filament-foundations, filament-system, filament-architecture]
related: [filament-roadmap]
supersedes: []
---

# Filament Decisions

## ADR-0001 — Filament owns reusable infrastructure-as-code building blocks

**Status:** accepted for initialization.

Filament is the intended Ego Hygiene boundary for reusable IaC modules, stacks, schemas, provider adapters, tests, examples, and related validation that can serve multiple repositories.

## ADR-0002 — Consumers own deployment intent, credentials, and production state

**Status:** accepted for initialization.

Filament publishes reusable artifacts. Product/platform repositories retain environment-specific topology, budgets, secret bindings, approvals, and production state backends.

## ADR-0003 — Do not select a universal IaC engine yet

**Status:** accepted for initialization.

Terraform/OpenTofu, Pulumi, Crossplane, native provider systems, and other tools remain candidates. The first real capability should select the smallest appropriate path and record the evidence.

## ADR-0004 — Reconcile the earlier Firmament concept instead of creating a competing IaC repository

**Status:** proposed organization follow-up.

Earlier Hygiene architecture reserved `firmament` for a future infrastructure-as-code/cloud-infrastructure boundary. The clarified Filament purpose now overlaps that scope. Hygiene should update the repository catalog/decision record so Firmament is retired, renamed, or assigned a genuinely distinct future concern before any separate repository is created.

## ADR-0005 — No hosted infrastructure control plane in v1

**Status:** accepted for initialization.

A hosted orchestrator would introduce secret custody, tenancy, state, billing, and operational concerns that are not necessary to prove reusable IaC modules.
