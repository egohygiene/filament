---
schema: aether.architecture-document/v1
id: filament-meta
title: Filament Meta
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-meta]
depends_on: [filament-epistemology, filament-ai-constitution]
related: [filament-purpose, filament-vision, filament-principles, filament-pillars]
supersedes: []
---

# Filament Meta Architecture

Filament's architecture is an 18-document graph following the organization Aether architecture-document convention.

## Document inventory

| Artifact | Path | Concern |
| --- | --- | --- |
| filament-purpose | [PURPOSE.md](PURPOSE.md) | Why Filament exists |
| filament-vision | [VISION.md](VISION.md) | Desired future |
| filament-principles | [PRINCIPLES.md](PRINCIPLES.md) | Decision heuristics |
| filament-pillars | [PILLARS.md](PILLARS.md) | Strategic capabilities |
| filament-manifesto | [MANIFESTO.md](MANIFESTO.md) | Public commitments |
| filament-epistemology | [EPISTEMOLOGY.md](EPISTEMOLOGY.md) | Evidence and uncertainty |
| filament-ai-constitution | [AI_CONSTITUTION.md](AI_CONSTITUTION.md) | AI authority and limits |
| filament-ontology | [ONTOLOGY.md](ONTOLOGY.md) | Domain language |
| filament-personal-model | [PERSONAL_MODEL.md](PERSONAL_MODEL.md) | Human/operator assumptions |
| filament-foundations | [FOUNDATIONS.md](FOUNDATIONS.md) | Invariants |
| filament-system | [SYSTEM.md](SYSTEM.md) | Logical system |
| filament-architecture | [ARCHITECTURE.md](ARCHITECTURE.md) | Boundaries and relationships |
| filament-methodology | [METHODOLOGY.md](METHODOLOGY.md) | Working method |
| filament-design | [DESIGN.md](DESIGN.md) | Developer/operator experience |
| filament-design-system | [DESIGN_SYSTEM.md](DESIGN_SYSTEM.md) | Shared semantic language |
| filament-decisions | [DECISIONS.md](DECISIONS.md) | Durable decisions |
| filament-roadmap | [ROADMAP.md](ROADMAP.md) | Evolution and v1 gates |
| filament-meta | [META.md](META.md) | Architecture graph/index |

## Relationship graph

```mermaid
flowchart TD
  PURPOSE --> VISION --> PRINCIPLES --> PILLARS --> MANIFESTO
  PURPOSE --> EPISTEMOLOGY --> AI[AI Constitution]
  EPISTEMOLOGY --> ONTOLOGY --> PERSONAL[Personal Model]
  PRINCIPLES --> FOUNDATIONS
  EPISTEMOLOGY --> FOUNDATIONS
  FOUNDATIONS --> SYSTEM --> ARCHITECTURE --> METHODOLOGY
  PERSONAL --> DESIGN --> DS[Design System]
  ARCHITECTURE --> DECISIONS --> ROADMAP
  PILLARS --> ROADMAP
  AI --> META
  EPISTEMOLOGY --> META
```

## Lifecycle

All documents are provisional until reviewed. Implementation evidence should progressively move specific contracts from proposed architecture into active, versioned behavior. Changes to Filament's durable ownership boundary require synchronized review with Hygiene because they affect cross-repository dependency direction.

## Current uncertainty

The ownership boundary is now sufficiently defined to begin research and a first vertical slice, but the IaC engine, provider set, module packaging format, state-backend support, and first capability remain intentionally undecided.
