# Hetzner k3s Infrastructure & GitOps Portfolio

This repository contains the Infrastructure as Code and GitOps automation for a highly available web infrastructure. It fulfills the requirements of a modern DevOps lifecycle from provisioning to application orchestration.

## Architecture Overview
* **Server:** Hetzner VPS running Ubuntu.
* **Orchestration:** k3s lightweight Kubernetes cluster.
* **Traffic Management:** Nginx Ingress Controller with automatic TLS via Cert-Manager.
* **CI/CD:** GitHub Actions and ArgoCD for declarative GitOps delivery.

## Infrastructure as Code (Ansible)
The cluster foundation is provisioned using Ansible. 
* Uses modular Ansible roles (`base`, `k3s`, `argocd`) for idempotency and clean code organization.
* Manages SSH keys and security configurations.
* Automated via GitHub Actions to apply changes continuously when the inventory or roles are updated.

## GitOps & Application Delivery (ArgoCD)
All workloads are managed declaratively using ArgoCD following the App of Apps pattern.
* **Raw Manifests:** Deploys BookStack and Gitea using native Kubernetes YAML manifests to demonstrate core primitive management.
* **Helm Charts:** Deploys NocoDB and a PostgreSQL database dependency using a custom Helm chart to demonstrate advanced package management and template logic.
* **Secrets Management:** Sensitive data is isolated from the public repository using Kubernetes Secrets natively provisioned on the cluster.
