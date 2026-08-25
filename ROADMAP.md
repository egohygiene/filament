---
schema: aether.architecture-document/v1
id: filament-roadmap
title: Filament Roadmap
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-24
governed_by: [architecture-roadmap]
depends_on: [filament-vision, filament-pillars, filament-architecture, filament-decisions]
related: [filament-purpose, filament-methodology]
supersedes: []
---

# Filament Roadmap

<!-- BEGIN ROADMAP EXECUTION SNAPSHOT -->
<!-- roadmap-manifest
schema: hygiene.roadmap/v1alpha1
repository: egohygiene/filament
visibility: public
publication: central
route: /roadmap/filament/
updated: 2026-08-24
-->
## 2026-08-24 execution snapshot

> This evidence-reconciled snapshot is the issue-generation and visual-roadmap handoff. The longer-horizon strategy below remains canonical context; generated HTML, JSON, progress, issue plans, and commit lists are projections.

**Lifecycle:** provisional architecture-only  
**Current gate:** Resolve the Filament/Firmament boundary and add a license, issue backlog, and CI foundation.  
**North-star outcome:** Reusable infrastructure-as-code modules with consumer-owned state and explicit engine and provider boundaries.

### Visual roadmap publication

**Mode:** `central`  
**Route:** `/roadmap/filament/`  
**Current publication evidence:** Architecture source only; no CI, issues, Pages, package, or release observed.

Publish the public-safe projection through egohygiene.io at /roadmap/filament/. This repository owns intent and acceptance evidence; it does not add a second site deployment.

### Quest line

<!-- roadmap-step
id: FIL-Q01
status: complete
depends_on: []
issues: []
-->
#### FIL-Q01 — Record the provisional architecture

**State:** `complete`  
**Depends on:** None

**Outcome:** The intended infrastructure-module direction is documented.

**Exit criteria:**

- [x] Architecture describes module and state ownership goals.
- [x] Provisional status is explicit.

**Current evidence:**

- The repository was observed as architecture-only.

<!-- roadmap-step
id: FIL-Q02
status: blocked
depends_on: [FIL-Q01]
issues: []
-->
#### FIL-Q02 — Resolve identity and governance

**State:** `blocked`  
**Depends on:** `FIL-Q01`

**Outcome:** Filament has an unambiguous name, relationship to Firmament, license, owners, and backlog.

**Exit criteria:**

- [ ] The Filament/Firmament decision is documented.
- [ ] A license and initial issues are present.

**Current evidence:**

- The Firmament boundary is unresolved.
- No license or issues were observed.

<!-- roadmap-step
id: FIL-Q03
status: planned
depends_on: [FIL-Q02]
issues: []
-->
#### FIL-Q03 — Select one engine, provider, and consumer

**State:** `planned`  
**Depends on:** `FIL-Q02`

**Outcome:** The first vertical slice has a bounded toolchain and real consumer.

**Exit criteria:**

- [ ] Selection rationale and non-goals are recorded.
- [ ] Credentials and state ownership remain consumer-controlled.

**Current evidence:**

- No engine, provider, or consumer implementation was observed.

<!-- roadmap-step
id: FIL-Q04
status: planned
depends_on: [FIL-Q03]
issues: []
-->
#### FIL-Q04 — Implement and test one module contract

**State:** `planned`  
**Depends on:** `FIL-Q03`

**Outcome:** One module plans, applies in an isolated fixture, and produces reviewable evidence.

**Exit criteria:**

- [ ] CI validates formatting, static analysis, and a safe integration fixture.
- [ ] State and secret handling match the documented ownership boundary.

**Current evidence:**

- No implementation or CI was observed.

<!-- roadmap-step
id: FIL-Q05
status: planned
depends_on: [FIL-Q04]
issues: []
-->
#### FIL-Q05 — Release and adopt the first module

**State:** `planned`  
**Depends on:** `FIL-Q04`

**Outcome:** A pinned module release is used by the named consumer with rollback evidence.

**Exit criteria:**

- [ ] A tagged release has immutable source and provenance.
- [ ] The consumer proves upgrade and rollback without transferring state ownership.

**Current evidence:**

- No release or adoption evidence was observed.

### Roadmap-to-issue handoff

- A step is complete only when its exit criteria and required evidence are satisfied; commit count never determines progress.
- Ready steps without an issue are candidates for the private, duplicate-aware roadmap.issue-plan.json dry run. Planned steps remain preview-only unless a reviewer explicitly opts them in with issue_policy: propose.
- Issue creation or reconciliation requires human approval or an explicitly authorized Pace operation and returns issue references through a reviewable roadmap pull request.
- Pull requests and commits should include Roadmap-Step: <ID>; historical evidence may be linked through existing issue and pull-request relationships.
- Public rendering uses only allowlisted build-time evidence and never places a GitHub token or private issue plan in the browser artifact.

<!-- END ROADMAP EXECUTION SNAPSHOT -->

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
