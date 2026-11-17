# YachtOps

YachtOps is a local-first operational workspace for captains and crews of 40–60 m private/charter yachts. Its MVP combines Maintenance Desk, Charter Ready 48h and Captain's AI Office through shared tasks, suppliers, crew references and activity history.

## Where to find things

- `docs/intent.md` — product intent, MVP scope, domain rules and acceptance criteria
- `docs/TECH_STACK.md` — architecture, dependencies, commands and testing
- `docs/STATUS.md` — verified implementation status, development commands and outstanding work

## Working rules

- Read the three documents and the `brand` skill before making substantive product or architectural changes. In conflicts, follow explicit user requests first, then `docs/intent.md` for product scope, `docs/TECH_STACK.md` for technology and the `brand` skill for UI.
- Preserve the **three integrated modules**. Do not turn the application into a generic CRM or build a full yacht management ERP.
- Prioritize usable vertical slices and realistic data-backed workflows, not decorative mock screens. Maintain one canonical task record shared across modules.
- Never automatically approve charter readiness, supplier quotations, expenses, maintenance completion or other safety/financial decisions. Human confirmation and traceability are required.
- Captain's AI Office does not imply that an LLM exists in the MVP. No simulated model responses, unsolicited outbound communication, or third-party data transfer.
- Treat yacht and crew information as confidential. Seed data must be fictional. Do not add external integrations or credentials without explicit authorization.
- Keep cross-platform local commands and SQLite persistence working. Tests must use their own data and never reset the operator's database.
- Run relevant tests and browser checks before reporting completion. Distinguish implemented, tested and planned work accurately.
- Update `docs/STATUS.md` after every completed milestone, including commands actually run, results, unresolved issues and the next step.
