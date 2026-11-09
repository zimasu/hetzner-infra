# hetzner-infra

Provisions a k3s cluster on Hetzner Cloud and bootstraps ArgoCD via Ansible.
Part of a two-repo GitOps setup. Deployments live in [hetzner-gitops](https://github.com/zimasu/hetzner-gitops).

**What gets provisioned:**
- OS hardening (UFW, SSH hardening, fail2ban)
- k3s single-node cluster
- ArgoCD bootstrapped and pointed at hetzner-gitops

![CI](https://github.com/zimasu/hetzner-infra/actions/workflows/ansible.yml/badge.svg)

## Requirements

- Ansible + `community.general` (`ansible-galaxy collection install -r requirements.yml`)
- Hetzner VPS running Ubuntu with an `ansible` user and SSH key access

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

## Status
Production. Evolves with the homelab.

## License
MIT
