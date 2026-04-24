# ICJIA Public Website 2026 — Documentation

Planning and design documentation for the rebuild of [icjia.illinois.gov](https://icjia.illinois.gov).

## Status

**Planning phase.** This repository currently holds the planning set — executive summary, master design plan, Strapi migration plan, per-phase deliverables, design system, accessibility strategy, security requirements, open questions, and an operational migration runbook. Implementation code will land in separate repositories when the planning set is accepted.

## What this is

ICJIA (the Illinois Criminal Justice Information Authority) is rebuilding its public website. The current site, built in 2021, has reached its limits — slow on phones, content-management system past end-of-life, accessibility held together with runtime workarounds. The new site is a complete rebuild on Nuxt 4 and Strapi 5, targeting **6–8 weeks** of focused work (8–11 weeks with buffer).

Full detail, written for non-technical leadership, is in [`docs/01-EXECUTIVE-SUMMARY.md`](./docs/01-EXECUTIVE-SUMMARY.md).

## Where to start

| If you are… | Start here |
|---|---|
| A non-technical manager or sponsor | [`docs/01-EXECUTIVE-SUMMARY.md`](./docs/01-EXECUTIVE-SUMMARY.md) — self-contained; has its own glossary |
| A project sponsor or program manager | [`docs/00-README.md`](./docs/00-README.md) — for reading paths by role |
| An engineer, designer, or security reviewer | [`docs/00-README.md`](./docs/00-README.md) — it routes you to the right file |

## Repository scope

This repository is **planning documents only.** When implementation begins:

- The Nuxt 4 frontend will live in its own repository.
- The Strapi 5 instance will live in its own repository.
- The data-migration scripts fork from [`ICJIA/hub-migration-tools`](https://github.com/ICJIA/hub-migration-tools) and will live in a new repository.

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
