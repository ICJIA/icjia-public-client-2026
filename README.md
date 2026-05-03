# ICJIA Public Website 2026 — Documentation

Planning and design documentation for the rebuild of [icjia.illinois.gov](https://icjia.illinois.gov).

## Status

**Planning phase for the front-end rebuild.** The backend Strapi 3 → Strapi 5 migration is **complete** — see [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools) for the tool that moved every content type, media file, and relation from the legacy backend into the new one. This repository currently holds the planning set for the remaining front-end work: executive summary, master design plan, per-phase deliverables, design system, accessibility strategy, security requirements, open questions, and the migration runbook (retained for historical record). Front-end implementation code will land in a separate repository when the planning set is accepted.

## What this is

ICJIA (the Illinois Criminal Justice Information Authority) is rebuilding its public website. The current site, built in 2021, has reached its limits — slow on phones, accessibility held together with runtime workarounds. The CMS has already been moved off Strapi 3 (end-of-life) onto Strapi 5; the remaining work is a complete front-end rebuild on Nuxt 4 against the new backend, targeting **6–8 weeks** of focused work (8–11 weeks with buffer).

Full detail, written for non-technical leadership, is in [`docs/01-EXECUTIVE-SUMMARY.md`](./docs/01-EXECUTIVE-SUMMARY.md).

## Where to start

| If you are… | Start here |
|---|---|
| A non-technical manager or sponsor | [`docs/01-EXECUTIVE-SUMMARY.md`](./docs/01-EXECUTIVE-SUMMARY.md) — self-contained; has its own glossary |
| A project sponsor or program manager | [`docs/00-README.md`](./docs/00-README.md) — for reading paths by role |
| An engineer, designer, or security reviewer | [`docs/00-README.md`](./docs/00-README.md) — it routes you to the right file |

## Repository scope

This repository holds **planning documents for the front-end rebuild.** The other repositories in the project:

- **Backend migration (complete):** [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools) — the API-to-API tool that migrated every content type, media file, and relation from the Strapi 3 instance into Strapi 5. Forked from `icjia-hub-migration-tools` and adapted for the public-site content types.
- **Strapi 5 instance:** lives in its own repository.
- **Nuxt 4 frontend (forthcoming):** will live in its own repository when implementation begins.

This repository remains the authoritative planning record throughout the project and after launch.

## Author and project lead

**Chris Schweda** — IDS (Innovation and Digital Services), Illinois Criminal Justice Information Authority. 25+ years at the agency; built the current ICJIA website (April–August 2020) and 15+ other sites in Vue 2/3, JavaScript, and TypeScript. Sole implementer and post-launch maintainer for this project.

See [`docs/01-EXECUTIVE-SUMMARY.md`](./docs/01-EXECUTIVE-SUMMARY.md) §2 for full context on accountability and track record.

## Contributing conventions

- [`docs/07-OPEN-QUESTIONS.md`](./docs/07-OPEN-QUESTIONS.md) and [`docs/09-SECURITY-REQUIREMENTS.md`](./docs/09-SECURITY-REQUIREMENTS.md) are **append-only** — resolved items keep their original text with a resolution paragraph appended underneath.
- All other planning documents are revised in place with a version bump in frontmatter.
- Every substantive change is recorded in [`CHANGELOG.md`](./CHANGELOG.md) using [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format and [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
- Cross-references between planning documents use the numbered filename (e.g. `02-MASTER-DESIGN-PLAN.md §4.5`).

## License

[MIT](./LICENSE) — Copyright (c) 2026 Illinois Criminal Justice Information Authority (ICJIA).
