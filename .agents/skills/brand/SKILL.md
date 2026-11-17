---
name: brand
description: Use this skill for any UI work in YachtOps — designing or building screens, components, layouts, navigation, colors, typography, interaction patterns, charts, or any frontend/visual work. Provides the brand identity, information architecture, and interaction guidelines that all UI must follow.
---

# YachtOps — Brand and UI guidelines

## Product character

A premium yet practical operations workspace for captains and crews of 40–60 m luxury yachts. Calm, precise, trustworthy and easy to use under time pressure. The primary experience is an operational command center, not a travel brochure or luxury retail website.

## Fonts

From Google Fonts when available, with bundled/local fallbacks for offline MVP use:

- **Headings and body:** Instrument Sans
- **Occasional editorial accent only:** Instrument Serif
- **Code, figures and identifiers:** JetBrains Mono

Prefer tabular numerals for countdowns, amounts and KPI columns.

## Colors

Use this maritime palette, adapted to YachtOps:

- **Primary / Navy:** `#0B1F33` — sidebar, navigation, major headings
- **Action / Ocean Blue:** `#1677A8` — buttons, links, active selections
- **Success / Emerald:** `#159A75` — completed and captain-approved states
- **Warning / Amber:** `#E8A23A` — approaching deadlines and at-risk status
- **Critical / Coral Red:** `#D9534F` — blockers, critical and overdue issues
- **Main text / Ink:** `#162A3A`
- **Secondary text / Slate:** `#64748B`
- **Light background / Off White:** `#F7F9FB`
- **Panel background:** `#FFFFFF`

Never rely on color alone: pair status colors with clear labels, icons and text. Check accessible contrast, especially on amber and light backgrounds. Do not use red for routine destructive buttons without confirmation.

## Surfaces and layout

- **MVP light mode:** page background `#F7F9FB`; white cards and panels; dark navy sidebar.
- Clean cards with subtle shadows or low-contrast full outlines, rounded corners and consistent spacing.
- Desktop-first layout: collapsible left sidebar, slim top bar, responsive content grid and contextual detail drawers.
- Dashboard hierarchy: yacht context → urgent priorities → maintenance and charter KPIs → upcoming work → recent activity.
- Charts should communicate actual operations (issue statuses, overdue work, readiness by department), not decorative marketing statistics.
- Distinguish critical blockers from ordinary work. Use calm overall styling so critical states remain prominent.
- Keep key actions near the content they affect; avoid deep navigation for routine task completion.
- Future tablet/mobile flows prioritize large touch targets, short forms, camera attachments and obvious sync state; these are not required in the initial desktop MVP.

## Navigation labels

Use these consistent product labels:

- Dashboard
- Maintenance Desk
- Charter Ready 48h
- Captain's AI Office
- Tasks & Calendar

Suppliers and crew can be accessed through context or secondary navigation. Do not add empty navigation items for future features.

## Interaction patterns

- Show who/what owns a task, the deadline, and the next action.
- Keep statuses consistent between tables, boards, detail pages and dashboards.
- Use explicit `Captain Approved` controls; completion percentages and AI suggestions must never masquerade as official approval.
- Provide clear empty, loading, validation and error states.
- Confirm destructive actions and state what linked information will be affected.
- Show reviewable source records for summaries and reports; distinguish data-derived text from user-authored content and future AI-generated text.
- Use subtle motion only where it clarifies an interaction; respect reduced-motion preferences.

## Avoid

- Nautical clichés, anchors and wave illustrations throughout the UI.
- Heavy gradients, glassmorphism, excessive animation and decorative dashboards.
- Border-only-on-one-side panels, redundant status badges or charts with no operational purpose.
- Hidden approval actions, misleading readiness claims or synthetic AI activity.

## Tone

Plain, concise professional English, suitable for international yacht crews. Short labels, specific action verbs and meaningful statuses. Avoid jargon, hype and exclamation marks. Show money with currency, e.g. `€1,250.00` or `1 250,00 €` according to locale. Use absolute deadlines plus a clear relative indicator when helpful.
