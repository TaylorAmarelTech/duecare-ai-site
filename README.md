# DueCare AI continuity site

This repository publishes the backend-free, read-only continuity copy of
[duecare-ai.com](https://duecare-ai.com/) at
[tayloramareltech.github.io/duecare-ai-site/](https://tayloramareltech.github.io/duecare-ai-site/).
The production domain and Render service remain active and unchanged.

The website source, exporter, tests, and public data registries live in
[`TaylorAmarelTech/gemma4_comp`](https://github.com/TaylorAmarelTech/gemma4_comp/tree/master/apps/duecare-ai.com).
This small repository owns only the independent GitHub Pages deployment.

## Continuity boundary

The Pages build:

- renders all 51 public routes from the maintained FastAPI templates;
- includes five dated, checksum-bound public snapshots;
- records the exact source commit in the snapshot manifest;
- blocks every API mutation and cross-origin API request;
- disables forms, accounts, automation, admin functions, and local-KB actions;
- excludes private submissions, admin state, raw logs, credentials, and model calls; and
- intentionally omits `CNAME`, so it cannot take over `duecare-ai.com` DNS.

The deployed banner states these limitations. The machine-readable build
receipt is at
[`static/snapshots/manifest.json`](https://tayloramareltech.github.io/duecare-ai-site/static/snapshots/manifest.json).

## Deployment

[`pages.yml`](.github/workflows/pages.yml) builds from public `master` daily,
on changes to this repository, or on a manual run. A manual run can pin any
public source commit through the `source_ref` input. The source exporter and
offline validator must both pass before GitHub Pages deploys the artifact.

Do not add a custom domain or retire Render from this repository. A future DNS
cutover requires the separate approval, root-domain build, live crawl,
rollback, and HTTPS gates documented in the
[static deployment runbook](https://github.com/TaylorAmarelTech/gemma4_comp/blob/master/apps/duecare-ai.com/DEPLOY_STATIC.md).

## Ownership and reports

Source issues belong in the
[main repository](https://github.com/TaylorAmarelTech/gemma4_comp/issues).
Deployment-only failures belong in this repository. Security-sensitive reports
should use the main repository's private security-reporting path rather than a
public issue.
