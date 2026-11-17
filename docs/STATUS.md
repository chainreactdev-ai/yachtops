# YachtOps — Project status

**State:** Not started. Product intent and project guidance prepared; implementation has not been verified or claimed.

## Defined scope

- One local desktop MVP for one operator and one 40–60 m mixed-use yacht.
- Three connected modules: Maintenance Desk, Charter Ready 48h, Captain's AI Office.
- Shared Dashboard and Tasks & Calendar, suppliers, crew references and activity history.
- Structured Office workflows in MVP; generative AI, cloud hosting, multi-user accounts and external integrations deferred.

## Planned implementation milestones

- [ ] Initialize root npm workspace, React/Vite frontend, FastAPI/uv backend and SQLite schema.
- [ ] Implement fictional seed data, `npm run dev`, `npm run seed` and isolated tests.
- [ ] Build design system and Dashboard with data-backed indicators.
- [ ] Implement Maintenance Desk CRUD, statuses, Kanban and timelines.
- [ ] Implement Charter Ready plans, department checklists, blockers and explicit captain readiness approval.
- [ ] Implement Captain's AI Office records, quotation tracking, drafts and deterministic reviewable reports.
- [ ] Build shared Tasks & Calendar and cross-module linking.
- [ ] Complete backend/frontend tests and real-browser E2E validation.
- [ ] Conduct captain/crew interviews and validate willingness to pay before committing to hosted SaaS or LLM integrations.

## Development commands (target contract, not yet implemented)

- `npm run dev` — local frontend and backend.
- `npm test` — isolated unit and E2E tests.
- `npm run seed` — destructive reset to fictional demo data.

The commands above are **requirements**, not evidence of existing working scripts. Record actual installation prerequisites, URLs, verified commands and test results here after implementation.

## Validation log

No implementation, automated tests, browser checks or market interviews have been completed as part of this document adaptation.

## Next action

Initialize the repository according to `docs/TECH_STACK.md`, implement the database and seed scenario, then validate the first end-to-end path: maintenance issue → charter blocker → Office action → resolution → captain approval.
