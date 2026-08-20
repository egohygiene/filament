---
schema: aether.architecture-document/v1
id: filament-ontology
title: Filament Ontology
kind: architecture-document
version: 0.1.0
status: provisional
owners: [egohygiene]
created: 2026-08-19
updated: 2026-08-19
governed_by: [architecture-ontology]
depends_on: [filament-purpose, filament-vision, filament-principles, filament-epistemology]
related: [filament-system, filament-architecture]
supersedes: []
---

# Filament Ontology

- **Capability** — a reusable infrastructure outcome such as storage, DNS, networking, compute, secrets integration, or observability wiring.
- **Module** — the smallest independently versioned implementation of a capability for an IaC engine/provider combination.
- **Stack** — an intentional composition of modules for a repeatable topology.
- **Provider adapter** — provider-specific implementation and constraints behind an explicit capability contract.
- **Consumer** — a repository or deployment that selects Filament capabilities and owns environment-specific intent.
- **Configuration** — non-secret consumer inputs that parameterize a module or stack.
- **Secret reference** — a reference to externally managed secret material; never the secret value itself.
- **Plan** — a reviewable representation of proposed infrastructure change before mutation.
- **State** — engine/provider knowledge of deployed resources. Production state belongs to the consumer's approved backend, not to Filament as a service.
- **Policy** — reusable validation constraints supplied by Hygiene or Filament-specific safety requirements.
- **Release** — an immutable version of modules, schemas, documentation, and migration guidance.
- **Evidence** — validation, test, plan, or runtime information that supports a claim about a module.
