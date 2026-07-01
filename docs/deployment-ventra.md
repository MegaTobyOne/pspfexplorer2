# Ventra Deployment Setup

This project deploys static `dist/` output to Ventra using GitHub Actions.

## Workflow

- File: `.github/workflows/deploy-ventra.yml`
- Trigger: push to `main` or manual run
- Build base: `PSPF_BASE=/` for root-domain hosting

## Required GitHub Secrets

Add these repository secrets before first deployment:

- `VENTRA_HOST`: Ventra SSH host (for example `s123.example.ventraip.net.au`)
- `VENTRA_PORT`: SSH port (usually `22`)
- `VENTRA_USER`: SSH user
- `VENTRA_PATH`: Destination directory for website files
- `VENTRA_SSH_KEY`: Private key for the deployment user

## Host Preparation

- Ensure destination path exists and is writable by `VENTRA_USER`.
- Ensure the public key pair for `VENTRA_SSH_KEY` is installed in `~/.ssh/authorized_keys` for that user.
- Ensure web server points document root to `VENTRA_PATH`.

## DNS and TLS

- Point `pspfexplorer.au` DNS records to the Ventra host.
- Enable TLS certificate for `pspfexplorer.au`.
- Force HTTPS redirects once certificate issuance is confirmed.

## Post-Deploy Smoke Checks

- Open home and navigate core routes.
- Confirm requirement search and filtering work.
- Confirm compliance updates persist.
- Confirm relationship map or board loads and interactions work.
- Confirm import/export and restore flows work.
- Confirm no runtime external calls after initial load.
