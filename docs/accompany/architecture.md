# Architecture (Accompany Health notes)

This repo is a vendored fork of the upstream [OpenFGA](https://github.com/openfga/openfga) server
with, as of this writing, zero Accompany-specific commits (see the README's
"Accompany Health Fork" section). For how OpenFGA itself works internally —
resolver chain, storage interface, type system — read the upstream-authored
[`AGENTS.md`](../../AGENTS.md) and [`docs/architecture/architecture.md`](../architecture/architecture.md)
first; this file only covers how Accompany Health runs it.

## How Accompany Health runs this

- Deployed in the `orion` Kubernetes namespace (observed as
  `openfga.orion-<env>.svc.cluster.local:8080` in `poseidon` Helm values, e.g.
  `poseidon/helm/orion/ophiuchus/values-dev.yaml`).
- Consumed by other Go services over HTTP/gRPC via the
  [`openfga/go-sdk`](https://github.com/openfga/go-sdk) client library — not
  imported as a Go module. Known consumers (via `go.mod` grep across
  `~/git/*`): `ah-scheduling`, `aquila`, `ah-messaging`, `hydra`, `ophiuchus`,
  `pulsar`, `vela`.
- TODO(human): confirm which repo/pipeline actually deploys and configures
  this instance (datastore backend, Helm chart source, env config) — it was
  not found in `accomp-infrastructure` or `poseidon/helm` as of this audit.
  The deployed instance may be running the stock upstream Helm chart rather
  than anything versioned in this repo.

## Fork maintenance

This fork tracks `upstream` (`openfga/openfga`) with no divergence at the time
these standards were adopted. See [`docs/accompany/dependencies.md`](dependencies.md)
for the remote setup and how to pull in upstream changes.
