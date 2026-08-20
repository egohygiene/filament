---
schema: aether.architecture-document/v1
id: filament-roadmap
title: Filament Roadmap
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-roadmap]
depends_on: [filament-vision, filament-pillars, filament-architecture, filament-decisions]
related: [filament-purpose, filament-methodology]
supersedes: []
---

# Filament Roadmap

## Phase 0 — Establish the boundary

- Reconcile Filament with Hygiene's current repository catalog and the deferred Firmament concept.
- Inventory likely IaC consumers and repeated infrastructure needs across the organization.
- Decide the minimum v1 capability and explicit non-goals.
- Define repository layout, module metadata, compatibility, and release conventions.

**Exit:** one architecture-approved vertical slice is selected with a real or disposable consumer.

## Phase 1 — Define the module contract

- Version schemas for module metadata, inputs, outputs, provider/engine compatibility, lifecycle, security assumptions, and evidence.
- Define secret-reference, state-backend, plan-report, and migration boundaries.
- Define static validation and policy interfaces.

**Exit:** invalid modules and incompatible consumers fail clearly before provider execution.

## Phase 2 — Implement one vertical slice

- Select one IaC engine/provider combination from current evidence.
- Implement one useful reusable capability.
- Add formatting, static analysis, unit/contract tests, disposable integration tests, and plan validation.
- Create a consumer fixture proving pinned adoption without copied source.

**Exit:** the capability is independently useful, testable, and reviewable without production credentials.

## Phase 3 — Release and adoption

- Publish immutable/versioned module artifacts with checksums/provenance where supported.
- Add Relay workflows for validation/release mechanics without moving IaC semantics into Relay.
- Add upgrade, rollback, import, teardown, and compatibility documentation.
- Adopt the release in at least one non-Filament repository.

**Exit:** a consumer can upgrade between releases through a documented plan.

## Phase 4 — Composition

- Add stack composition only after multiple modules demonstrate stable boundaries.
- Define dependency ordering, outputs, cross-module references, failure semantics, and cost/risk summaries.
- Integrate evidence with Observatory and version convergence with Pace when those contracts are ready.

## Phase 5 — Broaden deliberately

Evaluate additional providers, engines, policy systems, local/cloud development flows, and advanced orchestration only from demonstrated consumer needs.

## v1 definition of done

Filament v1 is not "supports every cloud." It is complete when one reusable infrastructure capability has a stable public contract, safe validation/plan path, tests, release lifecycle, consumer adoption, explicit state/secret ownership, and documented upgrade/recovery behavior.
