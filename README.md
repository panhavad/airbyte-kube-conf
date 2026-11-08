# Airbyte Kubernetes Config

![Last commit](https://img.shields.io/github/last-commit/panhavad/airbyte-kube-conf) [![Release](https://img.shields.io/github/v/release/panhavad/airbyte-kube-conf?include_prereleases)](https://github.com/panhavad/airbyte-kube-conf/releases/latest)

**Kustomize manifests to run [Airbyte](https://airbyte.com) on Kubernetes** - the open-source ELT / data-integration platform - including database, Temporal, scheduler, server, web app, persistent volumes and a LoadBalancer service.

![System snapshot](docs/snapshot.svg)

## Features

- Single `kubectl apply -k` deploy
- Postgres DB, Temporal, scheduler, server and webapp
- Persistent volumes for configs, DB and workspace
- LoadBalancer on ports 8000 (web) / 8001 (API)

## How it works

```mermaid
flowchart LR
    U["User"] -->|":8000"| LB["LoadBalancer"]
    LB --> W["Airbyte webapp"]
    W --> S["Airbyte server"]
    S --> DB[("Postgres")]
    S --> T["Temporal"]
    T --> SC["Scheduler / workers"]
    SC --> PV[("Workspace volume")]
```

## Getting started

```bash
kubectl apply -k resources/
kubectl get svc airbyte-webapp-loadbalancer
```

## Download

Grab the packaged source from the [latest release](https://github.com/panhavad/airbyte-kube-conf/releases/latest).

## Tech stack

- Kubernetes
- Kustomize
- Airbyte

## Project structure

```text
airbyte-kube-conf/
├── docs/
├── resources/
└── README.md
```
