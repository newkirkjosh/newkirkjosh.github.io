# PR Review

Review conventions for this repository. Reviewers (CodeRabbit, the cross-model review, local review agents) read this file in full, so rules are written out here instead of pointed to.

## Scope

Review the change against the PR's description. A finding about work the PR deliberately leaves out is not a defect; correctness, security and privacy defects in the change always are.

## Checklist

- This repository is public: flag anything personal, such as real names, email addresses, OAuth client IDs or secrets, Google Cloud project numbers, or machine details. The owner is "the owner" or the GitHub username.
- Plain static HTML: flag a build step, an external script, or a tracker.
- Each app on `index.html` is listed by the exact name on its OAuth consent screen, with its purpose and its scopes.
- `privacy.html` stays generic; app-specific details belong in the list on `index.html`.
- Files for agents and reviewers (`AGENTS.md`, `CLAUDE.md`, `REVIEW.md`) are listed under `exclude` in `_config.yml`, so the site doesn't publish them.

## Don't flag

- The `google<hash>.html` Search Console verification file: never suggest renaming, editing or deleting it.
