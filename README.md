# Grafana Sync Ansible

This codebase creates Grafana dashboards in an app-wise folder structure and validates them locally using Ansible before pushing to GitHub.

## Folder structure

```text
.github/workflows/deploy-dashboard.yml
ansible/create_dashboard.yml
dashboards/apps/<app_name>/_folder.json
dashboards/apps/<app_name>/<app_name>.json
dashboards/templates/standard-dashboard.json
docs/workflow.md
scripts/create_dashboard.sh
```

## Prerequisites

```bash
python3 --version
git --version
ansible-playbook --version
```

If Ansible is missing:

```bash
pip install ansible
```

## Create dashboard

```bash
chmod +x scripts/create_dashboard.sh
./scripts/create_dashboard.sh Binocs
```

## Create dashboard without push

```bash
AUTO_PUSH=false ./scripts/create_dashboard.sh Binocs
```

## Responsibility split

- Shell script: creates folder, dashboard JSON, folder metadata, and handles git push.
- Ansible: validates dashboard files locally before push.
- GitHub: stores version-controlled dashboard files.
- Grafana Git Sync: imports dashboards from GitHub.
