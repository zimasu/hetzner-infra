# hetzner-infra

Ansible setup for my Hetzner VPS. Provisions a k3s cluster and bootstraps
ArgoCD, which then takes over deployments from [hetzner-gitops](link).
Covers OS hardening, k3s install and ArgoCD bootstrap.

![CI](https://github.com/zimasu/hetzner-infra/actions/workflows/ansible.yml/badge.svg)

## Usage

```bash
cp inventory/hosts.yml.example inventory/hosts.yml
ansible-playbook site.yml

# or by role
ansible-playbook site.yml --tags base|k3s|argocd
```

## Structure

```
roles/base      # OS hardening
roles/k3s       # k3s install
roles/argocd    # ArgoCD bootstrap
charts/         # Helm charts
inventory/      # hosts.yml (gitignored), hosts.yml.example
```
