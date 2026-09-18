# Filament gitignore pilot

This is the first consumer pilot for the
[repository-file contract process](https://github.com/egohygiene/.github/issues/32),
tracked in [Filament #5](https://github.com/egohygiene/filament/issues/5).
It adopts an immutable Empathy baseline through a reviewed manual change.
The epic records review/merge status and the next authorized step.

## Contract and selection

| Field               | Filament selection                                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Purpose/path        | Root `.gitignore` keeps disposable local state out of Git while retaining source and reviewed artifacts.                        |
| Applicability       | Universal baseline; one declared root scope (`.`).                                                                              |
| Content ownership   | Empathy owns baseline/profile rules; Filament owns its selection and local additions.                                           |
| Foundation          | `empathy/repository-foundation@1.1.0`; plan format `empathy.gitignore/v1`.                                                      |
| Source commit       | `b44f798bb49259f9f48416b4ffebde1103e135c0`, the accepted merge of [Empathy #90](https://github.com/egohygiene/empathy/pull/90). |
| Baseline            | `foundation/ignore/universal.gitignore` in that Empathy commit; 27 active rules.                                                |
| Overlays/local text | None. Filament has no implemented language project or generated-output path.                                                    |
| Update behavior     | Review source/selection changes, regenerate the plan, inspect the diff, and explicitly adopt the proposed file.                 |
| Verification        | Pinned planner drift check, active-file byte equality, and isolated real-Git behavior checks.                                   |
| Adoption stage      | Manual pilot; Holon materialization, EgoLint/Relay enforcement, and Pace fleet adoption remain pending.                         |

The [selection manifest](../../../foundation/gitignore.manifest.json) and
[generated plan](../../../foundation/contracts/filament.gitignore-plan.json) support
only this file pilot. They do not assert that Filament implements the other
artifacts in the foundation catalog or introduce new organization-wide required
files. Required repository metadata follows the existing architecture;
`license_expression: NOASSERTION` records that no license is selected and grants
no license. License/governance completion remains a separate roadmap concern.

The baseline's raw UTF-8 SHA-256 is:

```text
79280ac4f3147ead97a0b21b01f40241238f08fa5d63abe3f81c8b64e7f179f0
```

Use the pinned [source contract](https://github.com/egohygiene/empathy/blob/b44f798bb49259f9f48416b4ffebde1103e135c0/docs/foundation/gitignore/README.md)
for rule rationale, ordering, hashing, and scope semantics. The plan includes
catalog/resolved-manifest, source-layer, local-text, and output hashes. Its
`plan-only` status describes the upstream planner: it does not inspect or modify
the consumer. The separate equality check below proves actual adoption.

## What this selection means

Local environments, `.secrets/`, named caches/dependencies, OS debris, and narrow
editor state are ignored. Explicit environment-template suffixes, shared editor
configuration, lockfiles, public certificates, fixtures, and reviewed artifacts
remain visible. Templates must contain placeholders. `.env.example.local` is
local state; `.env.production.example` is a trackable template.

Filament's architecture leaves the IaC engine/provider undecided. No Terraform,
Pulumi, Rust, or other engine-specific exclusion is selected merely because
Filament intends to own reusable IaC. Before introducing an engine or local
state, review its actual project roots, private state/plan/variable paths,
generated output, and intentionally visible lockfiles/examples. Add narrow
rules and behavior evidence with that implementation. Private local material
uses `.secrets/`; production credentials and state remain consumer-controlled.

Unknown local rules must be reviewed and preserved in the manifest, not silently
overwritten. Composition puts selected overlays first, local text second, and
the universal baseline last in every declared scope. A deeper `.gitignore` can
still override its ancestors. Ignore files do not untrack files, prevent forced
adds, or perform secret scanning. The inherited behavior suite demonstrates
these limits in disposable fixtures; it does not install nested exceptions here.

## Reproduce verification

Requirements: Git and Python 3.10 or newer. Run from Filament's root in one shell.
Obtain a separate clean Empathy checkout at the source commit above; for example,
clone `https://github.com/egohygiene/empathy.git` outside Filament and use
`git switch --detach b44f798bb49259f9f48416b4ffebde1103e135c0` there.
Set its path below. Do not update the pin to a moving branch during verification.

```bash
empathy_source="../empathy-gitignore-source"
test "$(git -C "$empathy_source" rev-parse HEAD)" = \
  "b44f798bb49259f9f48416b4ffebde1103e135c0" &&
test -z "$(git -C "$empathy_source" status --porcelain --untracked-files=all)" &&
python3 -B "$empathy_source/tools/foundation.py" \
  --catalog "$empathy_source/foundation/catalog.json" \
  check-gitignore-plan \
  --manifest "foundation/gitignore.manifest.json" \
  --source-root "$empathy_source" \
  --output "foundation/contracts/filament.gitignore-plan.json"
```

Continue only if that command succeeds. Then compare exact bytes and run the
pinned upstream suite against Filament's file, plus two consumer visibility
checks. This reuses Empathy's isolated Git harness without copying a validator
into Filament or choosing its future IaC toolchain.

```bash
python3 -B - "$empathy_source" <<'PY'
import hashlib
import json
from pathlib import Path
import sys
import unittest

source = Path(sys.argv[1]).resolve()
consumer = Path.cwd()
plan = json.loads(Path("foundation/contracts/filament.gitignore-plan.json").read_text())
entry, = plan["files"]
actual = Path(".gitignore").read_bytes()
if entry["path"] != ".gitignore" or actual != entry["content"].encode("utf-8"):
    raise SystemExit("Filament .gitignore differs from the reviewed plan")
if hashlib.sha256(actual).hexdigest() != entry["content_sha256"]:
    raise SystemExit("Filament .gitignore hash differs from the reviewed plan")

sys.path.insert(0, str(source / "tests"))
import test_gitignore_baseline as upstream

upstream.BASELINE = consumer / ".gitignore"

class FilamentVisibility(upstream.GitignoreFixture):
    def test_repository_paths_remain_visible(self):
        result = self.git("-C", str(consumer), "ls-files", "--cached",
                          "--others", "--exclude-standard", "-z")
        paths = tuple(path for path in result.stdout.split("\0")
                      if path and path != ".gitignore")
        self.assert_paths(paths, ignored=False)
        result = self.git("check-ignore", "--quiet", "--no-index", "--",
                          ".gitignore", check=False)
        self.assertEqual(1, result.returncode)

    def test_candidate_iac_sources_remain_visible(self):
        self.assert_paths(("modules/example/main.tf", "examples/main.tf",
                           "examples/example.tfvars", ".terraform.lock.hcl",
                           "Pulumi.yaml", "schemas/module.schema.json",
                           "docs/plan-example.json"), ignored=False)

loader = unittest.defaultTestLoader
suite = unittest.TestSuite((
    loader.loadTestsFromTestCase(upstream.GitignoreBaselineTests),
    loader.loadTestsFromTestCase(FilamentVisibility),
))
result = unittest.TextTestRunner(verbosity=2).run(suite)
raise SystemExit(0 if result.wasSuccessful() else 1)
PY
```

The upstream harness creates real untracked files in temporary repositories,
disables inherited system/global Git configuration and excludes, and checks
exit codes with winning-rule diagnostics. Candidate IaC paths are visibility
fixtures only; they do not create an engine selection or real infrastructure.

## Update, rollback, and resume

1. Open the master epic and verify live issues, review decisions, branches, and
   source acceptance. Inspect Filament's current files and any new nested ignore
   files before selecting another scope or overlay.
2. For an upstream update, review a new immutable Empathy commit, its matching
   catalog/resolver/fragments, and behavior changes. Update this pin explicitly.
   Keep Filament-owned local additions unless their change is reviewed.
3. Run the pinned planner with `plan-gitignore` and the same arguments above to
   update the proposal. Review the plan and current file diff before copying
   `files[0].content` to `.gitignore`. Never replace unknown edits automatically.
4. Run both verification blocks. Inspect ignored/untracked path changes without
   opening or staging private payloads; an ignored path is not safe to delete.
   Review the full diff and any completed PR checks.
5. Submit one bounded PR with source identity, behavior results, roadmap/ADR
   impact, and remaining integration. Update the epic, then stop for maintainer
   review and merge. Verify the live merge before recording pilot acceptance or
   starting the next maintainer-selected file.

Rollback is a reviewed restoration of the prior pin, selection, plan, and active
file together, preserving intervening local edits. Reverting the plan alone does
not revert Git behavior. For this initial adoption, the previous Filament commit
had no ignore file; reverting it also removes these exclusions and needs review
of any local state created since adoption.

## Initial evidence and boundaries

Inspection on 2026-09-18 started at Filament
`95cb3ef04b1664bc51ccc666524dd7f5eb04127b`: 19 documentation files, no ignore
files, implemented language roots, or CI workflows, and no competing PRs. The
clean pilot checkout had no ignored/untracked local files to migrate.

Exact validation results and review status belong in the linked issue/PR and
the master epic. The intended local gate is a matching plan/active file and
14 passing behavior tests (12 upstream and two consumer checks). There is no
Filament CI enforcement yet. Existing Empathy CI debt stays tracked upstream;
the maintainer deferred direct MegaLinter repairs to EgoLint/Relay adoption.
[Relay #5](https://github.com/egohygiene/relay/issues/5) and
[Relay #49](https://github.com/egohygiene/relay/issues/49) retain shared execution
scope. Holon owns materialization, EgoLint content conformance, and Pace fleet
adoption. None is claimed complete by this pilot.

ADR not required: this consumes the accepted baseline without changing
Filament's architecture or selecting an IaC engine. It supports `FIL-Q02`
repository-foundation work without completing its identity/license gate or
advancing roadmap status. The separately queued
[IaC slice](https://github.com/egohygiene/filament/issues/3) and
[ADR backfill](https://github.com/egohygiene/filament/issues/4) keep their existing
scope and gates. This record captures the first file's process; the master epic
remains the authoritative cross-repository continuation point.
