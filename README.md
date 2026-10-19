# hetzner-infra

Ansible playbooks for managing the aksara k3s node on Hetzner.

## Usage

```bash
ansible-playbook -i inventory/hosts.ini site.yml
```

After running, get the ArgoCD admin password with:

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```
