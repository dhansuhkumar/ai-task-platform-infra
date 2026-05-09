# AI Task Platform — Infrastructure Repository

This repository contains Kubernetes manifests for the AI Task Processing Platform, managed via Argo CD GitOps.

## Contents

| File | Description |
|------|-------------|
| `k3s/namespace.yaml` | Project namespace |
| `k3s/configmap.yaml` | Non-sensitive configuration |
| `k3s/secrets.yaml` | JWT secret and sensitive values |
| `k3s/mongodb.yaml` | MongoDB StatefulSet + Service |
| `k3s/redis.yaml` | Redis Deployment + Service |
| `k3s/backend.yaml` | Backend API Deployment + Service |
| `k3s/frontend.yaml` | Frontend Deployment + Service |
| `k3s/worker.yaml` | Worker Deployment + HPA |
| `k3s/ingress.yaml` | Ingress configuration |
| `k3s/kustomization.yaml` | Kustomize resource list |
| `k3s/argo-application.yaml` | Argo CD Application definition |

## Setup

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl apply -f k3s/argo-application.yaml
```

## Auto-Sync

Argo CD is configured with `auto-sync` enabled. Any push to this repository's `main` branch will trigger Argo CD to sync the cluster state to match the manifests.
