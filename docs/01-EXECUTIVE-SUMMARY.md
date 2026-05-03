# ICJIA Public Website Redesign — Executive Summary

**Audience:** Agency directors, program managers, and anyone in leadership who does not work with websites day-to-day.
**Status:** v2.3
**Last updated:** 2026-05-03 (reframed for completed backend migration: §1 short version, §3 reasons, §6 "what the work actually is," §7 timelines, §8 decisions, §9 risks updated to reflect that the Strapi 3→5 backend move is done — see [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools) — and the remaining work is the public front end; new §1.1 added covering Research Hub separation and SEO continuity; §3 expanded to cover Strapi 5 benefits, accessibility bonuses, and why both main site and Hub had to migrate; first-draft homepage render removed from §2; "residents" → "users" throughout)

This is a self-contained summary. You do not need to read any other document to understand this project. Technical terms are defined in the glossary at the end (§11). If something here is not clear, ask a team member directly — that is faster than tracking down supporting documentation.

---

## 1. The short version

We are building a new version of the agency's public website. The new site will **look better and work faster**. That is the point, in plain language. The current site looks dated and is slow on phones; the new one will look contemporary and be nearly instant.

Behind the scenes, the publishing tool that staff use to edit pages — Strapi — **has already been moved** from a version that no longer receives security updates to the current version. The migration tool that did this work is at [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools); every news item, event, grant, research record, biography, unit page, policy document, image, and uploaded file is now in the new system. The remaining work — and the subject of this document — is the rebuild of the public front end on top of that already-migrated content. Staff will see a cleaner, simpler editing screen when the new site goes live; otherwise the workflow is the same.

The remaining front-end work is expected to take **6 to 8 weeks** of active work, start to finish.

Users see no disruption. The existing site stays online the whole time; when the new one is ready, we switch the public address in a pre-announced window. Bookmarks and existing links continue to work.

### 1.1 What's in scope, what's separated out: the Research Hub

The site that exists today at `icjia.illinois.gov` bundles two things together: the agency's public-facing site (news, events, grants, biographies, policies, about pages — what most managers think of as "the website") and the **Research Hub** (`icjia.illinois.gov/researchhub/...` — articles, datasets, applications). The Hub is the larger of the two by a long way. It currently accounts for **roughly 65–80% of all traffic to the public-facing domain.** When stakeholders cite the agency's web traffic numbers, most of those numbers are Hub traffic.

The Hub is being separated into its own project, on its own infrastructure, with its own publishing setup. **That work is already in progress and is expected to complete within months** — before the public-site rebuild this document covers needs anything from it. The two projects are independent.

**SEO continuity is preserved.** This matters because the Hub URLs (`/researchhub/...`) carry years of accumulated search-engine authority — every external citation, every academic reference, every link from a partner agency points at those URLs. We do not give that up. The hub URLs continue to resolve to the same content, just on the dedicated hub infrastructure rather than bundled with the public site. To a search engine, to a user with a bookmark, and to a partner agency, **nothing changes about how `/researchhub/...` is found or accessed.** The plumbing behind those URLs changes; the URLs do not.

**What this means for this project's scope.** Because the Hub leaves the public-site rebuild and brings the majority of the traffic with it, the public-site rebuild this document covers is **considerably lighter** than a like-for-like rebuild of today's bundled site would be. It is the news/events/grants/biographies/policies/about portion only — what most managers actually think of as the "agency site" — without Hub article rendering, Hub dataset display, or Hub application surfaces. Those become the Hub project's responsibility.

This is a structural change with a few moving pieces. The phrasing here — "in flux now, but there is a plan" — is an honest summary of the state. The direction is clear and the SEO outcome is settled.

## 2. What the new site will look and feel like

**Visual.** The new design will be deliberately contemporary — cleaner typography, more readable layouts, a consistent look across every section. Both a light and a dark mode are part of the design system, so users can pick the mode that suits them and the site honors the device's preference by default. Compared to the current site, it will feel like a fresh page on a modern state government site rather than a page from 2021.

**Speed.** On a typical phone, most pages will feel instant. On an older phone or a slow connection, they will still be noticeably faster than today. We have measured the current site and know specifically where it underperforms; the new architecture solves that directly.

**Accessibility.** The site meets Illinois state-government accessibility standards by design — not with workaround code patched on top. Screen-reader users, keyboard-only users, users who need large text, and users who prefer reduced motion will all have a seamless experience.

**What's the same.** The same information is there — news, events, grants, research, about pages, policies, and the services users look for. Menus are organized similarly. Existing web addresses continue to work; anything that moves is automatically redirected.

## 3. Why we are rebuilding rather than continuing to patch

The current site was built in 2021 and reached its limits. Three specific problems motivated this project; none of them were reparable without rebuilding.

**It is slow on phones.** Most people who reach us are on a phone. On a typical mid-range phone, the current site takes several seconds to become usable — long enough that measurable numbers of visitors give up and leave before the page finishes loading. The delay is not caused by slow servers or a bad connection; it is built into how the site is structured. No amount of tuning fixes it.

**The publishing tool was past end-of-life — and has now been replaced.** The software staff use to edit news items, events, grants, and research — called a "content management system" in the trade, and specifically called Strapi at our agency — was running a version (Strapi 3) that the vendor no longer supports, with no security updates. Every month a state-government agency runs end-of-life CMS is a compounding security and compliance risk. **This has been addressed:** the agency's content has been migrated from Strapi 3 to Strapi 5 — **for both the main public site and the Research Hub**, which had been running its own Strapi 3 instance on the same end-of-life footing. The migration tool is at [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools). Migrating both was necessary, not a nice-to-have: end-of-life applied to both, and operating on two CMS versions afterward (one supported, one not) would have forked the agency's CMS operations and left a substantial share of agency traffic — see §1.1 for the Hub's traffic weight — on unsupported software.

*What Strapi 5 brings that Strapi 3 did not:* continued vendor security updates and a maintained upgrade path forward; **native author preview** (every content type has a Preview button that shows the page exactly as it will render on the public site, before publishing — replacing the old "publish first, check after" pattern); a modern, less cluttered admin interface that works correctly on a laptop or tablet and is substantially more accessible to staff who use screen readers or keyboard navigation; an explicit draft / published state per record (cleaner to reason about than v3's nullable-published-date model); and per-role, per-content-type, per-operation permissions (so an author who edits news doesn't automatically have the same access to grant or biography records).

*Accessibility benefits, specifically.* The Strapi 5 admin is meaningfully more accessible to **staff editors with disabilities** than v3's admin was — the modern primitives Strapi 5 is built on are upstream-audited for screen-reader and keyboard support. For **content as it reaches the public**, the native preview lets authors catch how a page reads — including how a screen reader encounters it — *before* publishing rather than after; the public site's build-time content validators (heading order, alt text, malformed tables) then act as a second gate. And from a **compliance standpoint**, running a supported rather than end-of-life CMS is itself a posture improvement: state-government IT reviews flag EOL software as an audit finding, and moving to Strapi 5 closes that finding for both the public site and the Hub.

**Accessibility is held together with workarounds on the public-facing site.** The current site has two dozen small scripts that run on every page to fix accessibility problems that the underlying software generates. When one of these scripts breaks, a screen-reader user can be locked out of a page. This is a fragile situation to be in as a state-government agency whose users include many people who depend on assistive technology. The front-end rebuild this document covers replaces the runtime-fix pattern with components that emit correct markup to begin with, plus build-time validators that block broken content from shipping.

Fixing any one of these would have justified some work. All three together justified the project. The first two — phone performance won't be addressed until the new front end ships, and the CMS EOL — have a clear path: the CMS is already on Strapi 5, and the front-end rebuild handles the other two.

What remains — the subject of the rest of this document — is the public-facing front end on top of the newer backend.

## 4. What changes for users visiting the site

Almost everything that matters to a user stays the same. The changes they will notice:

- **Pages appear much faster.** On a phone, most pages will be ready by the time the screen has finished loading. There is no visible loading spinner on content pages.
- **The site is easier to read.** Larger, clearer typography; better color contrast; more space between sections.
- **It works on more kinds of devices.** The current site is optimized for modern phones and desktops; the new site also works properly on older phones, tablets, and systems with high-contrast or large-text settings turned on.
- **Assistive technology works correctly.** Users of screen readers, keyboard navigation, or browser zoom get a seamless experience without the gaps in the current site.
- **Bookmarks still work.** Anywhere a user or an external site has linked to `icjia.illinois.gov/...`, that link continues to resolve — either to the same content on the new site, or automatically redirected to the new location.

What they will **not** notice: any change in what the site does. All services, forms, downloads, and information are available in the same places, or easily findable through the same search.

## 5. What changes for staff who publish content

The editing process stays familiar. The improvements are:

**Preview before publishing.** Every content type — news, events, grants, research, biographies, unit pages, policy documents — will have a Preview button in the editor. Clicking it shows exactly what the page will look like on the public site, with real images and real layout, before anything is published. Today, staff typically publish first and check afterward; that becomes optional.

**A cleaner editing screen.** The new editor is a current-version upgrade of the same tool staff already use. Workflows are the same — create draft, preview, publish, unpublish, edit published, republish — but the screens are more responsive, less cluttered, and easier to use on a laptop or tablet.

**The same accounts and permissions.** Every staff account carries over with the same role. Whoever can publish news today can publish news after the switch. Whoever has admin access today keeps it. Nothing about who can do what changes.

**Author support during the transition:**

- A short orientation session (about one hour) before the switch, covering what is different.
- Written step-by-step guides tailored to each content type.
- A named support contact — Chris Schweda (IDS) is the single point of contact for staff questions for the first month.
- A standing weekly check-in during the first month for any issues that surface.

## 6. What the work actually is

This section answers the adversarial question a careful manager has a right to ask: *what, exactly, are you going to do?*

Everything below happens on new infrastructure, separate from the running site. Users see no change until the final cutover window.

**Two pieces of what would have been the project's work are already accounted for.**

- *The publishing tool migration is done.* The database that stores our content has already been moved to the current Strapi version. Every news item, event, grant, research record, biography, unit page, policy document, image, and uploaded file is in the new system. The migration tool is at [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools).
- *The Research Hub is leaving the bundle.* Per §1.1, the Hub portion of today's site is being separated into its own project on its own infrastructure, with hub URLs preserved exactly so search-engine equity carries over. That project is on its own track and is not part of the scope below. Roughly two-thirds to four-fifths of today's traffic flows through Hub URLs; that traffic continues to land on the same URLs, just served by the dedicated Hub project.

**What remains is the public-facing website on top of the newer backend** — the visible pages users see, the design, the speed improvements, the accessibility work, for the news / events / grants / biographies / policies / about portion of the site. That is what the rest of this section walks through.

### 6.1 The current site keeps running throughout the front-end rebuild

The existing `icjia.illinois.gov` continues to serve users for the entire project. Nothing on it is deleted, edited, or taken offline until the 2-hour cutover window at the very end. Staff continue publishing as normal — and because the new publishing tool is already in place, staff publish into the same backend the new site will read from. Only when the new front end is reviewed, tested, and approved does the public address switch.

### 6.2 The publishing-tool upgrade was completed first (already done)

This is what `ICJIA/icjia-migration-tools` accomplished. A new, current-version publishing tool was installed on new infrastructure, starting from empty. The old tool was never edited in place — that approach carries a high risk of leaving it unusable mid-project if anything goes wrong. A purpose-built migration script then read every piece of content out of the old tool and wrote it into the new one: news, events, grants, research, unit pages, biographies, policy documents, images, and uploaded files. The script runs end-to-end in minutes; nothing was typed by hand.

*Parity* — the gate the migration had to pass — means every piece of content that exists in the old tool exists in the new one, with the same text, same images, same metadata, and the same relationships between items, nothing lost or distorted. The migration script and audit reports in `ICJIA/icjia-migration-tools` are the record of that check.

The old publishing tool is kept available, read-only, as a reference until the public cutover and for 30 days after. Authors continue to write into the old tool day-to-day during the front-end rebuild; their changes carry forward into the new tool through the same migration script.

### 6.3 The visible website is built section by section against the already-migrated content

This is the active work. The new front end gets populated with real content from the new publishing tool — no placeholders. It happens in a deliberate order:

1. **Homepage.** The front door of the site.
2. **News.** Ongoing and archived news items.
3. **Events.** Upcoming and past events.
4. **Grants.** Active opportunities and awarded grants.
5. **Research.** Reports, publications, and datasets.
6. **About pages.** Staff biographies, unit pages, policy documents.

Each section is completed — design reviewed, accessibility reviewed, any content oddities flagged back to authors — before the next section starts. This keeps review tractable and prevents problems in an early section from compounding through later ones.

### 6.4 Testing happens with real people before anything goes live

Before the new site takes over the public address, two rounds of testing happen on the staging copy (the private working version at `next.icjia.illinois.gov`):

- **Accessibility review.** A person trained in screen-reader use and keyboard-only navigation walks through every template and files any issues. We fix them. They walk through again.
- **Author testing.** Staff authors try drafting, previewing, and publishing real content into the new publishing tool and watching it appear correctly on the new site. They file any issues. We fix them. They try again.

Neither test is skipped, and neither is replaced by an automated check. The purpose is to surface the kinds of problems that only a real person using the site can find.

### 6.5 Cutover is a 2-hour event; the old site stays on standby for 30 days

On a pre-announced low-traffic day (typically a weekend morning), we change the public address to point to the new infrastructure. This takes minutes. Visitors arriving during the window see a brief "maintenance" page.

After the switch, the old website remains running, untouched, on its existing address — invisible to users but reachable by the project team. For 30 days after cutover, if any problem surfaces that cannot be fixed quickly on the new site, we point the public address back to the old site in minutes and resume normal operation there. No data is lost; the old site was never modified.

After 30 days of stable operation on the new site, the old website is retired. The old publishing tool follows the same retention schedule and is decommissioned at the same point.

## 7. How long the remaining work takes

**Approximately 6 to 8 weeks of active work for the front-end rebuild, start to finish.**

This is substantially faster than a traditional website rebuild (typically 9–12 months for a project of this scope) because we are combining three things that compress the work:

- **Developer familiarity with the stack.** The developer has built the current ICJIA website and 15+ other sites on the same underlying technology (Vue, JavaScript, TypeScript). Work that would take a new developer weeks of ramp-up takes days when the same patterns have been built, refined, and shipped before. Much of this project's scaffolding code already exists, proven, on prior ICJIA work.
- **Prior planning is already done.** The design direction is approved. The technical choices are made. The content inventory exists. The publishing-tool migration is already complete (see §1, §6.2). The project starts on day one with known requirements, not a discovery phase.
- **Focused scope.** We are not adding new features or changing what the site does. We are rebuilding what exists, better. A fixed scope lets the work progress in a predictable sequence.

The remaining work is a single track — the visible website. Numbers are working days relative to project start, not calendar dates; calendar dates depend on when we begin.

**Front-end rebuild timeline**

| Activity | Working days | Duration |
|---|---|---|
| Setup | 1–2 | 2 days |
| Visual design system | 3–9 | 7 days |
| Site structure | 10–13 | 4 days |
| Homepage | 14–17 | 4 days |
| Page templates | 18–22 | 5 days |
| Content rollout | 23–27 | 5 days |
| Search and admin | 28–30 | 3 days |
| Accessibility polish | 31–34 | 4 days |
| Switch to new site | 35–36 | 2 days |

**Already accounted for, out of scope for this timeline:**

- *The publishing-tool upgrade* — Strapi 3 to Strapi 5, including the data migration of every content type, media file, and relation. See [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools) for the tool and audit record.
- *The Research Hub* (per §1.1) — being delivered on its own track, on its own infrastructure, with hub URLs preserved for SEO continuity. Expected to complete within months — before the public-site rebuild needs anything from it. The 6–8 week estimate above is for the public site only and is meaningfully lighter than a like-for-like rebuild of today's bundled site would have been.

**What stays on a human timeline.** Accessibility reviews by real people, author testing on the new editing tool, and final stakeholder approval. These are deliberately not compressed; they are where we catch problems that no amount of automation would surface.

**Milestones visible to leadership:**

- **End of week 2.** A working version of the new site is visible at a staging address (`next.icjia.illinois.gov`) — not the public address yet. Leadership can click through it.
- **End of week 4.** Real content from the (already-migrated) publishing tool flows into the new site. Staff can try drafting, previewing, and publishing and see the result on the new front end.
- **End of week 6.** The new site has all content types rendered and is ready for accessibility and visual polish.
- **End of week 7 or 8.** Final review; cutover to the public address.

## 8. What we need from leadership

Three decisions, none of them large:

1. **Approval to begin the front-end rebuild.** The publishing-tool migration is already done; the front-end rebuild is the remaining work and is the subject of this document. Leadership confirms the start.
2. **An accessibility reviewer.** Either someone internal or an external consultant, available during weeks 6–8. Engaging a reviewer early — rather than at the end — catches problems while there is still time to fix them.
3. **A cutover window.** A pre-announced, pre-scheduled window of about two hours on a low-traffic day (weekend morning, late evening) when we switch the public address. Two weeks of advance notice is typical. Leadership picks the day.

Everything else — the development, the testing, the setup — happens without leadership intervention.

## 9. Risks worth naming at the leadership level

Two. None are unusual; both are manageable.

**Running two sites in parallel takes a small amount of author attention.** For about two weeks before the cutover, the old and new sites are both online — old at the public address, new at a staging address. Staff continue publishing as normal into the new publishing tool (which is already in place); the old front end keeps reading from a frozen copy of the content, and the new front end reads from the live one. Authors verify that what they published appears correctly on the new site. This is light work — probably ten to fifteen minutes per author per week — but it is work.

**Every change needs a settling-in period.** Even with a simpler editor and a faster site, the first two to three weeks after the switch will generate questions. "Why is this button in a different place?" "How do I do the thing I used to do?" The written guides and named support contact handle most of these; a few will require a brief team response. We have budgeted for this.

These risks are ordinary for a project of this size. They are managed through planning and communication, not by attempting to eliminate them.

The largest risk that *was* on this list — the publishing-tool upgrade landing on the critical path — is no longer a risk. That migration is done; see §1, §6.2, and [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools).

## 10. How progress is tracked

**Weekly written update,** delivered every Friday to a defined stakeholder list. One page. Three sections: what was completed this week, what is coming next week, any blockers. No meeting required; the update is read at leadership's convenience.

**Each phase has a single completion question** that decides whether it is done. Not a long checklist — one question. For example: "Does the homepage display live content from the editing tool on the staging site?" The answer is yes or no; "mostly" does not count as yes. This discipline keeps phases from dragging.

**Decisions are recorded in writing** the moment they are made — the date, the decision, and who made it. Nothing relies on anyone's memory of a hallway conversation.

## 11. Glossary

Plain-language definitions for every technical term that appears in this document. Ordered alphabetically.

- **Accessibility.** Features of a website that let people use it regardless of disability. Common examples: compatibility with software that reads pages aloud (for blind users), full functionality when navigating by keyboard alone (for users who cannot use a mouse), and readability at large text sizes. Illinois state-government sites are required by law to meet a specific accessibility standard.
- **Agency IT.** The Illinois Criminal Justice Information Authority's internal information-technology staff — the people who administer the agency's servers, accounts, and internal systems.
- **Archetype (page archetype).** A template pattern for a kind of page. For example, every news article has the same general structure — headline, date, body, related items — so we build one "news article template" and every actual article uses it. The site has about six archetypes, covering every page on the site.
- **Build / rebuild (the technical kind).** In web development, a "build" is the automated process of preparing a website's files so it can be served to visitors. Each time content is published, a rebuild runs automatically. This takes a few minutes and is invisible to visitors.
- **Content management system (CMS).** The software that staff use to write and publish content. In this project, specifically the tool called Strapi. Users never see it; only staff do.
- **Content type.** A kind of page or record that exists in the publishing tool. Examples: a news item, an event, a grant, a research paper, a staff biography. Each content type has its own set of fields (title, date, body, authors, etc.) that staff fill in.
- **Critical path.** The sequence of steps in a project where each one must finish before the next can start. If any step on the critical path slips, the whole project slips by the same amount. Steps that are not on the critical path can slip without affecting the end date.
- **Cutover.** The moment when the public web address is switched from the old site to the new one. It takes a few minutes to execute and is the final step of the project.
- **Dev / staging / production.** Three copies of the website. *Dev* is where developers try things. *Staging* is a private working copy that looks like the public site; staff test here. *Production* is the public site — what users actually see.
- **Draft, preview, published.** The three states of a piece of content in the editing tool. *Draft*: being worked on; not visible to the public. *Preview*: draft rendered exactly as it will appear once published. *Published*: visible on the public site.
- **Editor, author, publisher.** Words used interchangeably for staff who create and publish content on the agency's behalf.
- **Migration script.** A small program, written specifically for this project, that automatically reads every piece of content out of the old publishing tool and writes it into the new one. It ran in a few minutes, covered every kind of content, and typed nothing by hand. The migration is complete; the script and audit reports are at [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools).
- **Milestone.** A specific, visible moment in the project that demonstrates progress — for example, "the homepage is live on staging." Milestones are the points where leadership can check in.
- **Parallel (running in parallel).** Two lines of work happening at the same time rather than one after the other. In this project, the visible-website rebuild and the publishing-tool upgrade are parallel.
- **Parity (content parity).** A check that the content in the new publishing tool matches the content in the old one exactly — same text, same images, same metadata, same relationships between items. Parity was achieved during the backend migration and is recorded in the audit reports at [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools).
- **Phase.** A self-contained piece of the project with a clear start, a clear end, and a single completion question. This project has nine phases on the website side and ten on the publishing-tool side. Each phase takes days, not weeks.
- **Production.** The public site — what users actually see at `icjia.illinois.gov`. The opposite of "staging."
- **Redirect.** A rule that automatically forwards visitors from an old web address to a new one. If a user has bookmarked a page that has since moved, a redirect quietly sends them to the new location.
- **Responsive.** A website that rearranges itself for the device viewing it. A phone sees a single-column layout; a desktop sees more content side by side. All modern sites are responsive; the new one is designed for phones first.
- **Rollback.** The plan for undoing a change if something goes wrong. In this project, rollback is fast: switch the public address back to the old site, which remains running for several weeks after the cutover specifically for this purpose.
- **Screen reader.** Software that reads a web page aloud for users who are blind or have low vision. The two most common are VoiceOver (on Apple devices) and NVDA (on Windows). We test the new site against both.
- **Staging.** A private working copy of the website, running at a different web address (`next.icjia.illinois.gov`), used for internal review and author testing before anything reaches the public site.
- **Static site.** A website where every page is prepared in advance rather than being assembled on the fly when a visitor arrives. This is what makes the new site fast: the work is already done by the time a visitor clicks.
- **Strapi.** The specific publishing tool that agency staff use. Version 3 was the legacy one (end-of-life); the agency's content has been migrated to version 5 (the current release) — see [`ICJIA/icjia-migration-tools`](https://github.com/ICJIA/icjia-migration-tools).
- **URL / web address.** The address of a specific page, such as `icjia.illinois.gov/news/some-story`. "URL" and "web address" mean the same thing.

## 12. Questions

Questions about this project go to **Chris Schweda**, project lead and developer (IDS — Innovation and Digital Services, ICJIA). Chris has been with the agency for 25+ years, has built or managed 15+ websites across Vue 2/3, JavaScript, and TypeScript, and built the current ICJIA website (April–August 2020), which has been in continuous production since. Chris is the sole implementer of this project and the person accountable for fixes after launch — as has been the case for the current site for the past five years. You do not need to read any supporting document to understand the shape of this work. If something in this summary is not clear or you want deeper detail on a specific aspect — visual design, accessibility, the editing tool, the timeline — email Chris directly.
