@AGENTS.md

## Accompany Health repo-local material

This repo is a vendored fork of upstream OpenFGA — see `README.md` →
"Accompany Health Fork". `AGENTS.md` above is upstream-authored and covers
dev commands, architecture, and conventions; it is not duplicated here.
Accompany-specific material lives in `.agents/` and `docs/accompany/`:

| Read this | For |
|---|---|
| [`.agents/README.md`](.agents/README.md) | How repo-local agentic material is organized |
| [`.agents/rules/keep-docs-current.md`](.agents/rules/keep-docs-current.md) | Which doc to update for which kind of change |
| [`context.yaml`](context.yaml) | Ownership, tier, runtime commands, dependencies |
| [`docs/accompany/architecture.md`](docs/accompany/architecture.md) | How Accompany Health runs this fork |
| [`docs/accompany/local-development.md`](docs/accompany/local-development.md) | Accompany-specific local dev notes |
| [`docs/accompany/dependencies.md`](docs/accompany/dependencies.md) | Fork/upstream relationship, consumers |
| [`coding-guidelines.md`](coding-guidelines.md) | The one Accompany-specific rule: don't patch upstream code locally |

Shared ticket/PR/planning skills come from the
[ah-agents](https://github.com/Accompany-Health/ah-agents) plugin
marketplace (`ah-sdlc:*`, `ah-dev:*`, `ah-data:*`) and are installed
per-developer with `/plugin install`. Do not vendor them into this repo.
