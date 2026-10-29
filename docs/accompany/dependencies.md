# Dependencies (Accompany Health notes)

## Upstream (this repo's own dependency)

This repo mirrors [`openfga/openfga`](https://github.com/openfga/openfga).

```bash
git remote -v
# origin    git@github.com:Accompany-Health/openfga.git
# upstream  git@github.com:openfga/openfga.git
```

As of this audit, `HEAD` has zero commits ahead of `upstream/main` — this is
a clean mirror with no Accompany-specific code changes. To pull in new
upstream releases:

```bash
git fetch upstream
git merge upstream/main   # or rebase, per team preference
```

TODO(human): document the actual process/cadence for syncing this fork if one
exists (e.g. Dependabot, a scheduled job, manual) — none was found in
`.github/workflows/` beyond upstream's own CI/release workflows.

## Datastores

OpenFGA supports Postgres, MySQL, and SQLite (beta) — see `pkg/storage/`.
Which backend the deployed Accompany instance uses is not determined from
this repo alone; see [`docs/accompany/architecture.md`](architecture.md).

## Consumers

Services in this environment talk to a running OpenFGA instance via the
[`openfga/go-sdk`](https://github.com/openfga/go-sdk) Go client (a separate
repo/module), not by importing this repo. Observed consumers (`go.mod`
grep): `ah-scheduling`, `aquila`, `ah-messaging`, `hydra`, `ophiuchus`,
`pulsar`, `vela`.
