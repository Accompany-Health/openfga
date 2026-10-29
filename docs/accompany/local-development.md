# Local Development (Accompany Health notes)

This is a vendored fork of upstream OpenFGA. For day-to-day dev commands
(build, test, lint, hot-reload), use the upstream-authored
[`AGENTS.md`](../../AGENTS.md) → "Development Commands" section and the
[`Makefile`](../../Makefile) — they are accurate and already repo-local; this
file does not duplicate them.

Quick reference:

```bash
make build                        # Build binary to ./dist/openfga
make test                         # Generate mocks + run all tests with race/coverage
make lint                         # golangci-lint v2 with auto-fix
make dev-run                      # Hot-reload dev server (in-memory datastore)
DATASTORE="postgres" make dev-run # Hot-reload with postgres (requires Docker, see docker-compose.yaml)
```

## Environment variables

No Accompany-specific environment variables or `.env` files exist in this
fork. Configuration is via CLI flags / env vars documented upstream in
`cmd/run/run.go` and the [upstream docs](https://openfga.dev/docs/getting-started/setup-openfga).
TODO(human): if the deployed instance (see
[`docs/accompany/architecture.md`](architecture.md)) uses Accompany-specific
config (secrets, datastore DSN, OIDC settings), document it here or link to
where it's configured (likely in a Helm `values-*.yaml` outside this repo).

## Running against Docker Compose

`docker-compose.yaml` and `docker-compose.override.yaml` at the repo root are
upstream's own local dev compose files (Postgres/MySQL + OpenFGA). No
Accompany-specific overrides exist.
