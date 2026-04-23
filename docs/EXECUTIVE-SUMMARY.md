# ICJIA Public Website Redesign — Executive Summary

**Project:** Complete rebuild of icjia.illinois.gov
**Target stack:** Nuxt 4 + Nuxt UI 4 + Strapi 5
**Hosting:** Netlify (static generation)
**Current status:** Planning complete (v0.4); implementation pending
**Last updated:** 2026-04-23

---

## What we're doing

Complete rebuild of the Illinois Criminal Justice Information Authority's public website, replacing a Vue 2 / Vuetify / Apollo codebase that has reached its architectural ceiling. The new site is statically generated with Nuxt 4, backed by Strapi 5 for editor-driven content, with a dark-first editorial design grounded in an approved HTML mockup.

## Why now

The current site has spent months tuning toward a Lighthouse mobile score and stalled at 67. The problem is not performance work — it is architectural: a content publication should not boot a JavaScript framework to render a page. Accessibility compliance is also maintained by 24 runtime DOM-patch functions that paper over markup issues from aging dependencies. Vue 2 itself is past end-of-life. This is the right moment to reset on a simpler, faster, more accessible foundation.

## Key decisions

- **Framework:** Nuxt 4.4.x with Nuxt UI 4.x on Tailwind v4; TypeScript strict
- **Rendering:** Static site generation by default; dynamic routes only for search, admin, and author preview
- **CMS:** Strapi 5 (upgrade from Strapi 3 is a precondition) via GraphQL primary, REST reserved for uploads and auth; some static content moves to `@nuxt/content` in git
- **Live preview:** Agency authors click "Preview" in Strapi and see their unpublished drafts rendered by the Nuxt app within seconds
- **Accessibility:** WCAG 2.1 AA as the floor everywhere; AAA for core reading paths; zero axe-core violations required in CI
- **Design direction:** Dark-first with light toggle, angular (zero border-radius on primary surfaces), Inter + JetBrains Mono, three-accent palette
- **Rollout:** New site deploys to `next.icjia.illinois.gov` from week one; parallel operation with CMS authors validating against live data; two-week minimum parallel before DNS cutover

## Phase outline

Nine phases: decisions and scaffold, design system, shell and navigation, homepage, core content archetypes, content rollout, search and admin, accessibility polish, cutover. Phases 3–5 (homepage through content rollout) will overlap in practice. Critical dependency: the Strapi 3 → 5 upgrade must complete before Phase 4.

## Success criteria

- Lighthouse mobile ≥95 across sampled pages
- Real-user LCP p75 under 1.5 seconds
- Zero axe-core violations in CI
- CMS publish → visible on production in under 3 minutes
- Content authors complete their full publish workflow without developer help
- JavaScript bundle for the homepage under 100 KB gzipped

## Where to find detail

| Document | Purpose |
|---|---|
| `MASTER-DESIGN-PLAN.md` | Locked decisions, information architecture, rendering and data architecture, migration and rollout, phase outline |
| `DESIGN-SYSTEM.md` | Color tokens, typography, geometry, elevation, motion, component mapping |
| `ACCESSIBILITY-STRATEGY.md` | Compliance targets, architectural approach, CI and manual test gates, start-of-project checklist |
| `OPEN-QUESTIONS.md` | Living list of decisions still pending, with target phase and owner |
| `PHASED-DELIVERABLE-PLAN.md` | Per-phase task lists with entry and exit criteria (forthcoming) |
| `TEST-PLAN.md` | Test strategy, coverage targets, automation approach (forthcoming) |

## Status at a glance

Planning documents complete through v0.4. Ready for stakeholder review. Implementation cannot begin on content work until the Strapi 3 → 5 upgrade is scheduled. Design system, shell, and scaffold work (Phases 0–2) can proceed independently of the Strapi upgrade timeline.
