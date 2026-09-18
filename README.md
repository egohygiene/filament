# Filament

🧵 Reusable infrastructure-as-code building blocks for the Ego Hygiene ecosystem.

> **Status:** architecture-first and provisional. Filament now has a defined target boundary, but its provider/tooling implementation should be proven through real consumers before becoming stable.

## What Filament is for

Filament is intended to own reusable infrastructure-as-code modules, stacks, interfaces, validation, examples, and provider adapters that multiple Ego Hygiene repositories can consume without copying infrastructure implementation into each product.

The core idea is:

```text
product/platform intent
        ↓
versioned Filament module or stack
        ↓
reviewable infrastructure plan
        ↓
consumer-controlled deployment/state
```

Filament should make infrastructure reusable without becoming the owner of every deployed environment.

## Boundaries

Filament does **not** replace:

- **Hygiene** — organization architecture, policy, and repository ownership.
- **Realm** — developer environments, Dev Containers, workstation/runtime profiles.
- **Mantle** — portable shell and workstation behavior.
- **Relay** — GitHub Actions and CI/CD orchestration.
- **Holon** — repository/template materialization.
- **Pace** — fleet reconciliation and upgrades.
- **Observatory** — organization visibility and evidence.
- **Product repositories** — product-specific infrastructure intent, credentials, budgets, and deployed state.

The earlier deferred **Firmament** concept overlaps this newly clarified boundary and should be reconciled at the organization level before any separate Firmament repository is created.

## Architecture corpus

Start with [PURPOSE.md](PURPOSE.md), [ARCHITECTURE.md](ARCHITECTURE.md), [DECISIONS.md](DECISIONS.md), and [ROADMAP.md](ROADMAP.md). [META.md](META.md) indexes the complete architecture graph.

## Current objective

Prove Filament's boundary with one small, reusable, independently testable infrastructure vertical slice before selecting a broad provider strategy.

## Repository file pilot

The [`.gitignore` adoption record](docs/foundation/gitignore/README.md) captures the pinned Empathy baseline, Filament's selection, verification, and update process for the [organization file-contract epic](https://github.com/egohygiene/.github/issues/32).
