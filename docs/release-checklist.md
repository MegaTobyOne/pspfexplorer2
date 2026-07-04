# Release checklist

Run these checks before publishing or merging to `main`:

1. `npm run lint`
2. `npm run typecheck`
3. `npm run test:run`
4. `npm run build`
5. `npm run perf:budget`
6. `npm run test:e2e:prod`
7. `npm run sbom`

Manual smoke pass:

- Open the app shell and verify grouped navigation, global search, and the command palette.
- Check Directions response tracking, evidence, filtering, and copy-summary feedback.
- Check the relationship map with data that includes a compliance gap, work log, risk, action, and Direction.
- Check a narrow viewport for header wrapping, search, Directions, and map inspector layout.

Notes:

- Current CI validation should keep the focused E2E specs for the navigation/compliance/work-log/relationship-map flows alongside the full `npm run test:e2e:prod` run. That combination matches the current open-first UI pattern and catches both targeted regressions and base-path/accessibility drift.
- `npm run test:e2e:prod` uses the production root base path (`PSPF_BASE=/`) and catches lazy-route/base-path regressions.
- `npm run sbom` generates from `package-lock.json` so CI avoids package metadata parsing issues in installed `node_modules`.
- Re-run `npm run build` before `npm run perf:budget` if source files changed.
