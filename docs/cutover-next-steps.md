# Cutover Next Steps (Remote)

This file captures only the remaining remote/provider actions after local hard-cut setup.

## Current Local Status

Completed locally:

- New clean repository baseline prepared in `pspf-explorer-2.0`.
- Root-domain build defaults set (`PSPF_BASE=/`).
- GitHub Pages deployment removed.
- Ventra deployment workflow added.
- Lint, typecheck, unit tests, perf budget, and production-path smoke E2E checks all passing locally.

## Remaining Remote Steps

1. Create GitHub repository for PSPF Explorer 2.0.
2. Add `origin` remote and push `main`.
3. Configure repository secrets:
   - `VENTRA_HOST`
   - `VENTRA_PORT`
   - `VENTRA_USER`
   - `VENTRA_PATH`
   - `VENTRA_SSH_KEY`
4. Verify Ventra host path permissions and SSH key.
5. Run `Deploy to Ventra` workflow.
6. Validate staging URL smoke checks.
7. Update DNS for `pspfexplorer.au` and enable HTTPS enforcement.
8. Re-run production smoke checks on `https://pspfexplorer.au`.
9. Archive legacy repository and point to new canonical repository/domain.

## Suggested First Push Commands

```bash
cd "/Users/toby/Dev/PSPF Explorer v2.0/pspf-explorer-2.0"
git add .
git commit -m "chore: bootstrap PSPF Explorer 2.0 hard-cut baseline"
git remote add origin <new-repo-url>
git push -u origin main
```
