# ICJIA Public Website Redesign — Documentation

**Last updated:** 2026-05-03

This folder contains the planning set for the rebuild of icjia.illinois.gov. The site will be faster, easier for staff to update, and meet stricter accessibility standards.

**Backend migration status:** the underlying content system (Strapi) has already been upgraded from the legacy version (Strapi 3, end-of-life) to the current version (Strapi 5). The migration tool is at [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools); the procedure is recorded in `08-STRAPI-MIGRATION-RUNBOOK.md`. The remaining work — and the active subject of this planning set — is the front-end rebuild on top of that newer backend.

## Reading paths by role

Read in the order listed. Files are numbered; skip what isn't in your path.

| Role | Reading order |
|---|---|
| Non-technical manager, funder, or sponsor | **01** |
| Project sponsor or program manager | 01 → 02 → 04 → 09 |
| Backend / CMS engineer | 01 → 02 → 03 → 04 → 08 → 09 → 07 |
| Frontend engineer | 01 → 02 → 05 → 06 → 04 → `docs/phases/*` → 09 → 07 |
| Security reviewer | 09 → 02 §4.5 → 03 §9 → 06 |

## Document status

| # | Document | Status | Audience |
|---|---|---|---|
| 00 | `00-README.md` | — | everyone (this file) |
| 01 | `01-EXECUTIVE-SUMMARY.md` | v2.3 | non-technical leadership (self-contained; has its own glossary) |
| 02 | `02-MASTER-DESIGN-PLAN.md` | DRAFT v0.5 | technical team |
| 03 | `03-STRAPI-UPGRADE-PLAN.md` | COMPLETED | backend / CMS engineers — historical record of the upgrade strategy that was followed |
| 04 | `04-PHASED-DELIVERABLE-PLAN.md` | DRAFT v0.3 (Strapi track complete) | project management |
| 05 | `05-DESIGN-SYSTEM.md` | DRAFT v0.1 | frontend engineers, design |
| 06 | `06-ACCESSIBILITY-STRATEGY.md` | DRAFT v0.1 | frontend, QA, project lead (a11y is owned in-house — no external reviewer) |
| 07 | `07-OPEN-QUESTIONS.md` | LIVING | everyone — appended as decisions close |
| 08 | `08-STRAPI-MIGRATION-RUNBOOK.md` | COMPLETED | backend / CMS engineers — operational record of the executed migration |
| 09 | `09-SECURITY-REQUIREMENTS.md` | DRAFT v0.1 | project lead + security reviewer — must-fix items before/during implementation |

### Subfolders

- [`docs/phases/`](./phases/) — per-phase deep-dive docs for the Nuxt rebuild (P0–P8). Companion to `04-PHASED-DELIVERABLE-PLAN.md`. Currently scaffolds; design-driven content fills in a second planning round once the HTML designs are shared.

## Contributing to these documents

- **07-OPEN-QUESTIONS.md** is append-only. When a question is decided, update its status and add the resolution as a new paragraph underneath — do not delete the original question. Decided items remain as a record and are referenced later.
- **Other documents** are revised in place, with a version bump in the frontmatter and an entry in the "Last updated" line noting what changed.
- **Changes to any planning document are recorded in [`../CHANGELOG.md`](../CHANGELOG.md).** The changelog package version follows the master design plan's version (`02-MASTER-DESIGN-PLAN.md`).
- Cross-references between documents use the numbered filename (e.g. `02-MASTER-DESIGN-PLAN.md §4.5`). If you rename or add a document, sweep for stale references.
- Forthcoming documents: `TEST-PLAN.md` (test strategy, coverage, procedures) — not yet written.
