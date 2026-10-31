# AGENTS.md

GitHub Pages site (`https://newkirkjosh.github.io/`) that supplies the home page and privacy policy Google requires before a personal OAuth app can be published (moved from Testing to In production). One site covers every such app.

## Files
- `index.html`: home page. Lists each app by the exact name on its OAuth consent screen, with one line on what it does and the scopes it requests.
- `privacy.html`: one privacy policy for all listed apps. Keep it generic; app-specific details belong in the list on `index.html`.
- `google<hash>.html`: Google Search Console ownership file for the URL-prefix property `https://newkirkjosh.github.io/`. Never rename, edit or delete it, or the domain stops counting as verified and branding checks fail.
- `_config.yml`: tells GitHub Pages' Jekyll build not to publish the agent and review files.
- `.github/workflows/secrets.yml`: scans the full history for secrets with gitleaks on every PR (any base) and every push to `main`.

## Adding an app
1. Add one `<li>` to the Apps list in `index.html`: the consent-screen app name, its purpose, its scopes.
2. Only if the new app handles data in a way the privacy policy doesn't already cover, update `privacy.html`.
3. In Google Cloud, on the app's Branding page, use home page `https://newkirkjosh.github.io/`, privacy policy `https://newkirkjosh.github.io/privacy.html`, authorized domain `newkirkjosh.github.io`.
4. Request the narrowest scopes that work. Sensitive or restricted scopes need Google verification; non-sensitive ones (such as `drive.file`) do not.

## Tracker
GitHub issues on this repository.

## Layers
None: a static site with no layered `dev` runs.

## Pull requests
Conventional-commit titles. Labels: one of `enhancement`, `bug` or `documentation`. No project board. Squash merge only.

## Merge policy
An agent may squash-merge its own PR when every gate holds on the PR's head commit, re-checked right before merging: CI green, the Codex cross-review converged, every CodeRabbit comment fixed or answered, and no unresolved review thread. Hand the merge back to the user instead when the PR touches `privacy.html` (the policy Google reviews), the `google<hash>.html` verification file, `.github/workflows/`, the review rules and what applies them (`REVIEW.md`, `.coderabbit.yaml`), or this Merge policy or the Code Review Rules section of this file.

## Code Review Rules
Read `REVIEW.md` at the repository root and apply it in full as the review rules for this repo. This section exists for Codex, which reads `AGENTS.md` but not `REVIEW.md`.

## Rules
- This repo is public. Commit nothing personal: no real names, email addresses, client IDs, client secrets, project numbers or machine details. Refer to the owner as "the owner" or by the GitHub username.
- Plain static HTML, no build step, no external scripts or trackers.
- Pages must stay publicly reachable without login; Google fetches them during review.
