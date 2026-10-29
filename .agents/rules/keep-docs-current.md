---
name: keep-docs-current
description: Documentation and agentic material must be updated in the same change that invalidates it
target: both
---

# Keep documentation current

Stale documentation is worse than missing documentation: an agent reads it
with the same confidence as correct documentation and acts on it.

**Update the docs in the same PR as the change that invalidates them.** Not a
follow-up ticket. A reviewer should be able to reject a PR for leaving a doc
wrong, the same way they would for a missing test.

Org-level requirements are in `ah-agents/docs/repository-standards.md` →
**Documentation Maintenance**. This rule is the local enforcement.

This repo is a vendored fork of upstream OpenFGA (see `README.md` →
"Accompany Health Fork"). Most dev-workflow and architecture documentation
lives in upstream-authored [`AGENTS.md`](../../AGENTS.md) and
[`docs/architecture/architecture.md`](../../docs/architecture/architecture.md)
— **do not edit those for Accompany-specific reasons**; they should track
upstream. Accompany-specific facts belong in `docs/accompany/` and
`context.yaml` instead.

## What to update, and when

| If you change… | Update |
|---|---|
| How/where the Accompany instance is deployed or configured | [`docs/accompany/architecture.md`](../../docs/accompany/architecture.md) |
| Setup, env vars, or how to run it locally (Accompany-specific) | [`docs/accompany/local-development.md`](../../docs/accompany/local-development.md) |
| A dependent service, consumer, or datastore | [`docs/accompany/dependencies.md`](../../docs/accompany/dependencies.md) |
| A new failure mode, or the fix for one | [`docs/accompany/troubleshooting.md`](../../docs/accompany/troubleshooting.md) |
| Ownership, team, Slack, on-call, tier | [`context.yaml`](../../context.yaml), the README's Ownership section, and `.github/CODEOWNERS` |
| A new convention, pattern, or anti-pattern (Accompany-specific code is added) | [`coding-guidelines.md`](../../coding-guidelines.md) |
| A procedure encoded in a script or workflow | the matching file under [`.agents/`](../README.md) |
| Upstream is merged/synced and it changes a fact asserted above | all of the above, as needed — re-verify the "vendored fork" claims in `README.md` and `coding-guidelines.md` still hold |

## Files the context manifest promises exist

[`context.yaml`](../../context.yaml) declares these under `docs:` and
`important_paths:`. If you move or delete one, update the manifest in the
same change:

`README.md` · `docs/accompany/architecture.md` · `docs/accompany/local-development.md`

## Don't hardcode values that drift

Reference the file that holds a value instead of copying the value into
prose — versions, ports, team names, and consumer lists all go stale.

## Agentic material is documentation too

Everything under `.agents/` is subject to this rule. There is no automated
sync checker in this repo yet (unlike `mercury`'s `scripts/check_agents_sync.sh`)
because there are no stubs to drift — add one if `.claude/`/`.windsurf/` stubs
are ever introduced here.
