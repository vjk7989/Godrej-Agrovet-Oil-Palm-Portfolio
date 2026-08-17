# Architecture Record

## Provenance and scope

- Standalone Godrej Agrovet Oil Palm portfolio derived from `G:\oil-palm-1.5-gui-work` at commit `f6a821e`.
- The build is intentionally isolated to the `gavl` company profile and its workbook-derived demo data. It enters that dashboard directly; the multi-company landing page and company switcher are excluded.
- The persistent header pairs the approved Godrej Agrovet logo with the PalmWatch product name.
- All farm, location, operational, and ownership content remains explicitly identified as demo data or Godrej Agrovet-supported/linked plantation areas; it must not imply company ownership unless source data establishes that fact.

## Decisions and interfaces

- The site is a static, repository-subpath-safe application: document, asset, and navigation references use relative paths so both local preview and GitHub Pages work.
- The production build emits the deployable site to `dist/`; the GitHub Actions Pages workflow tests and builds before publishing that directory.
- Accessibility repairs are part of the accepted implementation: active navigation exposes `aria-current`, grouped toggles expose pressed state, menus support keyboard operation, decorative icons are hidden from assistive technology, text uses contrast-safe tokens, and the document supplies a favicon.

## Current codebase map

- `index.html` — standalone application shell, Godrej-only data and behavior, direct dashboard entry, branding, and accessibility semantics.
- `assets/company-logos/godrej-agrovet.png` — approved company logo used by the persistent brand area.
- `tests/` — static isolation/build assertions and browser coverage for responsive, keyboard, accessibility, and runtime behavior.
- `scripts/build.mjs` — minimal static packager that creates the Pages-ready `dist/` output.
- `.github/workflows/deploy-pages.yml` — CI test/build and GitHub Pages deployment workflow for `main`.

## Verification status

Independent verification passed for this increment:

- Static checks, production build, and diff checks: passed.
- Forbidden cross-company strings: `0` matches.
- Production artifact: `9` files, `3,371,769` bytes.
- Browser suite: `46/46` checks passed.
- Axe accessibility scan: `0` violations.
- Browser console errors, page errors, failed requests, and HTTP failures: `0` each.
- Public GitHub Pages URL verified `200` with Godrej title, logo alternative text, PalmWatch branding, no company switcher, and no foreign-company strings: `https://vjk7989.github.io/Godrej-Agrovet-Oil-Palm-Portfolio/`.

## Pending and next safe task

- No Godrej implementation work remains.
- Next safe task: keep monitoring GitHub Pages if a green Actions history entry is required; the live public page is already verified.
