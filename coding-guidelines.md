# Coding Guidelines

This repo is a vendored fork of upstream [OpenFGA](https://github.com/openfga/openfga)
with no Accompany-specific commits as of this writing (see README.md →
"Accompany Health Fork"). **Upstream's own conventions apply** — they're
already documented in [`AGENTS.md`](AGENTS.md) → "Code Conventions" and
enforced by `.golangci.yaml`. This file does not restate them; it only adds
the rule specific to maintaining a fork.

## Vendoring rule

- **BAD**: Patching application logic (e.g. `internal/graph/`, `pkg/server/`)
  directly in this fork to work around an Accompany-specific need.
- **GOOD**: Upstream the fix to [`openfga/openfga`](https://github.com/openfga/openfga)
  first, then pull it in via `git fetch upstream && git merge upstream/main`.
  If something is genuinely Accompany-only (deployment config, this
  `.agents/`/`docs/accompany/` material, `context.yaml`), keep it isolated
  from upstream-owned directories so future merges from `upstream/main` stay
  conflict-free.

If Accompany-specific application code is ever added to this fork, a human
should expand this file with the real BAD/GOOD conventions found at that
point — do not invent them pre-emptively.
