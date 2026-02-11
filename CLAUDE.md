# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an educational course repository about **GitOps, Continuous Delivery, and ArgoCD**. It contains structured learning modules with theory, quizzes, diagrams, and practical labs. There is no buildable application code — the repo is purely documentation and sample Kubernetes/Helm/ArgoCD manifests.

Content is provided in three languages: **English** (`EN/`), **Ukrainian** (`UA/`), and a legacy/draft folder (`other/`).

## Repository Structure

- `0-Introduction-CD/` — Continuous Delivery fundamentals
- `1-Intrduction-GitOps/` — GitOps concepts (note: directory name has a typo)
- `2-Introduction-to-ArgoCD/` — ArgoCD architecture and overview
- `3-CRD-ArgoCD/` — ArgoCD Application CRDs
- `4-Practice/` — Hands-on lab with sample files and prerequisites guide
- `5-Conclusion/` — Course summary and final quiz

Each module directory contains `EN/`, `UA/`, and `other/` subdirectories with markdown content and a quiz file.

## Sample Files (4-Practice/sample-files/)

Contains ArgoCD and Helm manifests for a sample app called "cogitator":
- `app-of-apps.yaml` — ArgoCD App-of-Apps pattern root application
- `apps/` — Per-environment ArgoCD Application manifests (dev, qa, prod)
- `charts/cogitator/` — Helm chart with environment-specific values files (`values-dev.yaml`, `values-qa.yaml`, `values-prod.yaml`)

## Key Conventions

- When adding or editing content, maintain all three language versions (EN, UA, other)
- Each module includes a quiz file (`quiz.md` / `перевірка-знань.md`) — keep quiz format consistent
- Sample YAML files use ArgoCD `argoproj.io/v1alpha1` API version
- The Helm chart targets Kubernetes deployments and services
