---
title: "Repositories"
description: "An overview of the repositories maintained under the dexidp GitHub organization."
date: 2026-04-17
draft: false
toc: true
weight: 1000
---

The Dex project is split across three repositories under the [dexidp](https://github.com/dexidp) GitHub organization. Each one targets a different layer of the project, and most contributions land in just one of them.

## dex

Repository: [github.com/dexidp/dex](https://github.com/dexidp/dex)

The core of the project — an OpenID Connect (OIDC) identity and OAuth 2.0 provider written in Go. This is where the federation logic, the gRPC API, the storage backends (Postgres, MySQL, etcd, Kubernetes CRDs, SQLite, in-memory), and all upstream connectors (LDAP, SAML, GitHub, GitLab, OIDC, OAuth2, and others) live.

Typical contributions:

- New connectors or fixes to existing ones (under `connector/`).
- Storage backend changes (under `storage/`).
- Server, token, and protocol behavior (under `server/`).
- Updates to the gRPC API definitions (under `api/`).

Container images are published to [`ghcr.io/dexidp/dex`](https://github.com/dexidp/dex/pkgs/container/dex) and Docker Hub for every tagged release.

## helm-charts

Repository: [github.com/dexidp/helm-charts](https://github.com/dexidp/helm-charts)

The official Helm chart for deploying Dex on Kubernetes. The chart is published to the `https://charts.dexidp.io` repository and indexed on [Artifact Hub](https://artifacthub.io/packages/search?repo=dex).

```bash
helm repo add dex https://charts.dexidp.io
helm search repo dex
```

Typical contributions:

- New chart values exposing additional Dex configuration knobs.
- Upgrades to bundled Kubernetes manifests (Deployment, Service, Ingress, ServiceMonitor, etc.).
- Compatibility fixes for newer Kubernetes or Helm versions.

Note that the chart is versioned independently of Dex itself — a chart release does not imply a new Dex release, and vice versa.

## website

Repository: [github.com/dexidp/website](https://github.com/dexidp/website)

The source of [dexidp.io](https://dexidp.io) — this very site. It is a [Hugo](https://gohugo.io/) site built on top of the [Docsy](https://www.docsy.dev/) theme and deployed via Netlify.

Typical contributions:

- New or improved documentation pages under `content/docs/`.
- Connector and configuration reference updates as features land in `dex`.
- Landing page, navigation, and theme tweaks (see `STYLES.md` in the repo for the design-system guide before touching SCSS).

Documentation changes that describe new behavior in `dex` should generally be opened against this repository in a separate PR, referencing the corresponding `dex` PR.
