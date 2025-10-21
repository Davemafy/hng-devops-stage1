# DevOps Stage 1 — Automated Deployment Script

This repository contains `deploy.sh` — a single Bash script to automate provisioning and deploying a Dockerized application to a remote Linux host.

## Features
- Interactive prompts for Git repo, PAT, branch, SSH details, and app port
- Clones/pulls the repo and checks for `Dockerfile` / `docker-compose.yml`
- SSH remote provisioning: installs Docker, Docker Compose, Nginx
- Transfers project files with `rsync`
- Builds and runs containers (supports docker-compose)
- Dynamically creates Nginx reverse proxy config and reloads Nginx
- Validation steps (local and remote curl checks)
- Logging to `deploy_YYYYMMDD_HHMMSS.log`
- Idempotent: safe to re-run; stops previous containers before redeploy
- `--cleanup` flag to remove deployed resources (partial cleanup)
- Basic error handling and traps, meaningful exit codes

## Quick usage
1. Make it executable:
   ```bash
   chmod +x deploy.sh
