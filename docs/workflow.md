# Local Ansible Validation Workflow

## Flow

```text
Developer
  -> scripts/create_dashboard.sh <app_name>
  -> creates dashboards/apps/<app_name>/<app_name>.json
  -> creates dashboards/apps/<app_name>/_folder.json
  -> runs ansible/create_dashboard.yml locally
  -> validation passes
  -> git commit and push
  -> Grafana Git Sync pulls from GitHub
```

## Why Ansible runs locally

Ansible is used as the pre-push validation layer. If JSON syntax, dashboard structure, or folder metadata is wrong, the script fails before the changes reach GitHub.

## Run command

```bash
chmod +x scripts/create_dashboard.sh
./scripts/create_dashboard.sh Binocs
```

## Local-only test without push

```bash
AUTO_PUSH=false ./scripts/create_dashboard.sh TestApp
```
