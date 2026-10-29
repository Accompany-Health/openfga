# `.agents/` — agentic material for this repo

This directory is the **single source of truth** for every repo-local rule,
skill, workflow, and sub-agent in this repo. It is tool-neutral: Claude Code,
Windsurf, and Devin all consume it.

## This repo is a vendored fork

This is a vendored fork of upstream [OpenFGA](https://github.com/openfga/openfga)
with no Accompany-specific commits as of this writing — see `README.md` →
"Accompany Health Fork". Upstream already ships its own excellent AI agent
guidance in [`AGENTS.md`](../AGENTS.md) (dev commands, architecture, code
conventions, testing) — **do not duplicate it here.** This `.agents/` tree
only holds material specific to running this fork at Accompany Health.

## Edit here, never in `.claude/` or `.windsurf/`

Agent tools only discover content from fixed paths — Claude Code from
`.claude/{skills,agents,commands}`, Windsurf and Devin from
`.windsurf/{rules,skills,workflows}`. A prose pointer cannot create a slash
command or a dispatchable sub-agent, so those directories hold **stubs**:
real frontmatter plus a single line pointing back here.

```markdown
---
name: example-skill
description: <copied verbatim from the .agents/ source>
---

Canonical definition: `.agents/skills/example-skill/SKILL.md`. Read that file and follow it.
```

A stub never contains content. If you find yourself editing prose inside
`.claude/` or `.windsurf/`, you are editing the wrong file.

## Layout

| Path | What goes here |
|---|---|
| `rules/` | Always-on conventions and guardrails. Short, imperative, non-negotiable. |
| `skills/<name>/SKILL.md` | On-demand procedural knowledge — "how do I do X in this repo". |
| `workflows/<name>.md` | Multi-step procedures, surfaced as slash commands. |
| `agents/<name>/AGENT.md` | Sub-agent personas. |

As of this writing only `rules/keep-docs-current.md` exists — there is no
Accompany-specific procedural knowledge in this fork yet beyond what upstream
`AGENTS.md` already covers.

## What does *not* belong here

Anything reusable across Accompany Health repos. Shared skills and agents
(`ah-sdlc:*`, `ah-dev:*`, `ah-data:*`) are installed with `/plugin install`
from [ah-agents](https://github.com/Accompany-Health/ah-agents) and must
never be vendored into this repo.

**The test:** could another Go service use this unchanged? If yes, it
belongs in `ah-agents`, not here.

Prose documentation belongs in `docs/` (upstream's own `docs/`, plus
`docs/accompany/` for Accompany-specific notes); rules and skills link to it
rather than restating it.

## Standard

This layout implements the **Repo-Local Agentic Material** section of
`ah-agents/docs/repository-standards.md`, and keeps instruction files thin
per `ah-agents/docs/agentic-sdlc-standards.md` first principle #4. `mercury`
is the reference implementation for a non-vendored repo.
