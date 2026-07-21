# DAVe — Installation on Kubernetes

This document describes how to deploy DAVe (Datenbank und Auswertung von Verkehrszählungen) on Kubernetes,
based on the project's documentation and architecture. The recommended way to install DAVe is via the project's Helm chart.
This guide provides an end-to-end Kubernetes installation walkthrough, configuration notes and examples for common components.

Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Quickstart (Helm)](#quickstart-helm)
- [Dependencies (PostgreSQL, Elasticsearch, Keycloak, S3/MinIO)](#dependencies-and-recommended-helm-charts)
- [Example values.yaml](#example-valuesyaml-important-snippets)
- [Ingress / TLS](#ingress--tls-example)
- [Map and tenant configuration (map center, layers, stadtbezirk mapping)](#key-configuration-options)
- [Resource requests & limits (recommended)](#resource-recommendations)
- [Development / Local testing notes](#development--local-testing)

---

## Overview

DAVe is a set of services (backend & frontends) and optional EAI components:
- Backend: Java Spring Boot (business logic, DB access).
- Frontends: Vue 3 (data portal, admin portal, selfservice portal).
- Supporting components: Elasticsearch (search index), PostgreSQL (relational storage of count data), Keycloak (Identity Provider), Document storage (S3), EAI services.

Recommended installation: use the published Helm chart:
- Chart (ArtifactHub / helm repository): it-at-m/dave

The architecture expects:
- Elasticsearch 8.x as search index (storing searchable metadata)
- PostgreSQL (recommended 16) for traffic/count data
- Keycloak (or other OAuth2 provider) for authentication & authorization
- S3-compatible object storage for document storage (presigned URL flow)
- ConfigMaps/Secrets for configuration such as stadtbezirke.properties and map layers

---

## Prerequisites

- Kubernetes cluster (v1.24+ recommended)
- kubectl and Helm 3 installed and configured for your cluster
- Sufficient resources for services (see Resource section)
- Persistent Volume support in cluster (for PostgreSQL, Elasticsearch storage)
- TLS termination (IngressController) or external load balancer for production
- (Optional) MinIO for S3-compatible object storage in dev/test

---

## Quickstart (Helm)

1. Add the Helm repo and update:

```bash docs/install/kubernetes.md
helm repo add it-at-m https://it-at-m.github.io/helm-charts
helm repo update
```

2. Create a namespace:

```bash docs/install/kubernetes.md
kubectl create namespace dave
```

3. Prepare your `values.yaml` (see example further down). Then install:

```bash docs/install/kubernetes.md
helm install dave it-at-m/dave \
  --namespace dave \
  -f my-values.yaml
```

4. Monitor install:

```bash docs/install/kubernetes.md
kubectl -n dave get pods
kubectl -n dave describe pod <pod-name>
kubectl -n dave logs -f deployment/dave-backend
```

Notes:
- The chart will typically deploy the backend and optionally the frontends, or rely on external frontends and API gateways depending on chart options.
- For production, provide external Postgres, Elasticsearch and Keycloak (or configure the chart to use existing services).

---

## Dependencies and recommended Helm charts

You can install the following charts in the same cluster or point DAVe to external instances:

- PostgreSQL (example chart: bitnami/postgresql)
  - Use a production-ready configuration (replication, backups).
- Elasticsearch 8.x (example chart: elastic/elasticsearch)
  - Ensure it matches DAVe's Elasticsearch index format (8.x).
  - Persistent volumes are required.
- Keycloak (example chart: bitnami/keycloak or the upstream Keycloak Operator)
  - Configure realms/clients according to DAVe's SSO configuration (see sso-client.json example in backend repo).
- MinIO (for dev S3) or your S3 object storage
  - Used for document storage and presigned URL generation used by the backend.

Install examples (brief):

```bash docs/install/kubernetes.md
# Example: install a Postgres for DAVe
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install dave-postgres bitnami/postgresql --namespace dave -f postgres-values.yaml

# Example: install MinIO (dev)
helm repo add minio https://charts.min.io/
helm install dave-minio minio/minio --namespace dave -f minio-values.yaml
```

---

## Key configuration options

The backend exposes a set of environment variables and application.yml settings. Important items:

- DAVE_STADTBEZIRKMAPPINGCONFIGURL
  - URL (or classpath resource) to the stadtbezirke.properties mapping file (used by the backend to map city districts).
  - For Kubernetes, provide this as a ConfigMap and mount in the backend container or host it via an accessible HTTP endpoint.

- Map center and map layers
  - DAVE_TENANT_MAP_CENTER_LAT
  - DAVE_TENANT_MAP_CENTER_LNG
  - DAVE_TENANT_MAP_BASELAYERS_<n>   (list entries)
  - DAVE_TENANT_MAP_OVERLAYLAYERS_<n>
  - These values are used to configure the default map center (Munich by default) and available map layers.

- Database and Elasticsearch connection variables
  - spring.datasource.url, username, password
  - spring.elasticsearch.uris, credentials (or via chart settings)

- Identity Provider (Keycloak) settings
  - Keycloak URL, realm, client-id and client-secret

- Object storage (S3) settings
  - S3 endpoint, bucket, credentials — used by the document storage flow for presigned URLs

- Security profile
  - For development you can run with security disabled (as in the docker-compose sample). For production, always enable Keycloak integration.

---

## Example values.yaml (important snippets)

Below is a compact example `my-values.yaml`. Adjust for your environment and the actual chart keys in the published chart.

```yaml docs/install/kubernetes.md
# Example values for Helm installation (adjust keys to the chart)
replicaCount: 1

image:
  repository: it-at-m/dave-backend
  tag: sprint

postgresql:
  enabled: false
  host: dave-postgres.dave.svc.cluster.local
  port: 5432
  username: dave
  password: supersecret
  database: davedb

elasticsearch:
  enabled: false
  url: https://elasticsearch.dave.svc.cluster.local:9200
  username: elastic
  password: elasticpassword

keycloak:
  enabled: false
  url: https://keycloak.example.com/auth
  realm: dave
  clientId: dave
  clientSecret: <secret>

s3:
  endpoint: https://minio.dave.svc.cluster.local:9000
  bucket: dave-docs
  accessKey: minio
  secretKey: minio123
  pathStyle: true

env:
  DAVE_TENANT_MAP_CENTER_LAT: 48.137154
  DAVE_TENANT_MAP_CENTER_LNG: 11.576124
  DAVE_STADTBEZIRKMAPPINGCONFIGURL: /config/stadtbezirke.properties

resources:
  backend:
    requests:
      cpu: "500m"
      memory: "2.25Gi"
    limits:
      cpu: "1"
      memory: "3Gi"
```

Notes:
- The exact keys depend on the published chart. Use this snippet as a template and adapt.
- We recommend using external managed PostgreSQL and Elasticsearch in production. Set `enabled: false` and point to externally managed clusters.

---

## ConfigMaps and Secrets

- stadtbezirke.properties
  - Create a ConfigMap with the mapping file and mount into the backend container or provide a URL:

```bash docs/install/kubernetes.md
kubectl -n dave create configmap dave-stadtbezirke --from-file=stadtbezirke.properties
```

- Secrets
  - Store DB credentials, Keycloak client secret and S3 credentials as Kubernetes secrets and reference them in the Helm values.

---

## Ingress / TLS example

Example Ingress manifest (annotated for cert-manager / nginx ingress). Adapt annotations for your Ingress controller.

```yaml docs/install/kubernetes.md
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: dave-ingress
  namespace: dave
  annotations:
    kubernetes.io/ingress.class: nginx
    cert-manager.io/cluster-issuer: letsencrypt-prod
spec:
  tls:
    - hosts:
        - dave.example.com
      secretName: dave-tls
  rules:
    - host: dave.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: dave-frontend
                port:
                  number: 80
```

---

## Resource recommendations

Per SysSpec-arc42 recommended resource sizing (example):

- Backend: CPU 0.5 — 1 core, Memory 2.25 GB (requests), limits higher for burst
- API Gateways (frontend): CPU 0.25, Memory 1 GB
- EAI: CPU 0.25, Memory 0.5 GB
- Document-Storage: CPU 0.5, Memory 512 MB
- Geodata-EAI: CPU 0.5, Memory 3.5 GB

Adjust according to your load and cluster size.

---

## Development / Local testing

If you only want a quick peek or local development environment, the project provides a docker-compose stack with security disabled and a sample dataset (see docs/docker-compose.md):

Steps (in repo):
```bash docs/install/kubernetes.md
git clone https://github.com/it-at-m/dave-frontend
git checkout sprint
cd stack
docker compose build
docker compose up
# access: http://localhost:8082