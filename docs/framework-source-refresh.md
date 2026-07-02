# Framework Source Refresh (One-Off)

This project normally uses static in-repo PSPF data. For the 2026 uplift, we run a one-off source refresh from authoritative PSPF and ISM publications.

## Purpose

- Capture authoritative source artefacts used for this refresh.
- Record immutable checksums and validation evidence.
- Improve dataset usefulness by linking Technology requirements to current ISM source material.

## Authoritative sources

- PSPF Release 2026 - List of Requirements (PDF)
- PSPF Release 2026 - Summary of Changes (PDF)
- Information security manual (June 2026) (PDF)
- ISM June 2026 changes (PDF)

The one-off script stores these under:

- `source-data/framework-refresh/2026-07/`

## Run

From repo root:

```bash
npm run refresh:framework-data
```

This will:

- download the source files,
- validate expected marker text in each PDF,
- compute SHA-256 digests,
- write `source-data/framework-refresh/2026-07/source-manifest.json`.

## Validation checks

The script currently checks for expected source markers:

- PSPF list: `PSPF Release 2026`, `List of Requirements`, `Req Number`
- PSPF changes: `PSPF Release 2026`, `Summary of Changes`
- ISM manual: `Information security manual`, `June 2026`
- ISM changes: `ISM`, `June 2026`

## Display impact

- Technology requirements are enriched with ISM references in `src/pspf/index.ts`.
- Requirement detail now renders URL references as clickable links.
- Global search indexes requirement references, so ISM-linked requirements are searchable.

## Notes

- This is intentionally not a frequent workflow.
- Re-running in future should be done only for an explicit release refresh and should update the dated folder and manifest.
