# Intent: YachtOps MVP

## Problem

Captains and department heads on 40–60 metre private and charter yachts coordinate maintenance, charter turnaround, suppliers and administrative work across messages, spreadsheets, checklists and disconnected software. They cannot always see which interventions are blocked, whether the next guest arrival is on track, which decisions await approval or who owns the next action. Re-entering the same information into multiple workflows wastes time and creates avoidable uncertainty.

## Proposed outcome

**YachtOps** is a premium, operational workspace for yacht captains and crew. The MVP combines **YachtOps Maintenance Desk**, **Charter Ready 48h** and **Captain's AI Office** around shared tasks, suppliers, documents and activity history. It is designed first for a single 40–60 m yacht with both private and charter use, and can later expand to a secure multi-user, multi-yacht SaaS.

The first release is a realistic, fully usable **local desktop MVP for one operator**, with persistent sample and user-entered data. It demonstrates the complete cross-module workflow rather than attempting to replace certified planned maintenance, onboard safety, yacht management, accounting or charter booking systems.

### Five sections

- **Dashboard** — The landing page answers *What requires attention today?* Show open and critical maintenance issues, next guest arrival and countdown, charter preparation progress, overdue tasks, pending approvals, recent activity and an upcoming-work timeline. Include clear charts for maintenance by status and readiness by department. Values must derive from actual stored records, not decorative placeholders.
- **Maintenance Desk** — Searchable and sortable list plus Kanban view of reported technical issues and interventions. Create, view, edit and delete issues; set equipment/area, priority, owner, supplier, due date and status (`Reported`, `Under Review`, `Awaiting Quotation`, `Scheduled`, `In Progress`, `Completed`). View a detail page with description, notes, linked tasks and activity history. Overdue and critical items stand out. Moving a card changes its status and persists its position.
- **Charter Ready 48h** — Create a preparation plan for a guest arrival (private visit or charter). Show arrival date/time, countdown, department progress and blockers. Reusable task checklists cover `Deck`, `Interior`, `Galley` and `Engineering`, with owner, due date, status, priority and notes. Preparations can be viewed by department or timeline. A linked unresolved critical maintenance issue can be flagged as a blocker; completion percentage is calculated from checklist items. Final `Ready — Captain Approved` status requires an explicit manual approval action; it is never inferred from task completion alone. The 48-hour milestones are configurable guidance, not a readiness guarantee.
- **Captain's AI Office** — A focused administrative workspace for operational messages, supplier quotations, action items, documents and reports. In the local MVP, the operator can manually enter or paste communications, categorize them, create linked tasks or quotations, write and edit reply drafts, and assemble a reviewable weekly operations summary from stored records. Clearly label manual/template-generated output. **Actual LLM summarization, conversational document search and automatic drafting are later enhancements**, only enabled when an explicit AI provider is configured and appropriate authorization/privacy controls exist; the MVP must not simulate AI responses as real AI.
- **Tasks & Calendar** — One shared searchable task list and calendar/timeline across all three modules. Each task has one canonical record with title, description, owner, priority, due date, status and source link. Users can add, update, complete and filter tasks without making duplicate copies in different modules. Overdue tasks and upcoming follow-ups surface on the dashboard.

### Shared experience

- A persistent left navigation, top bar with current yacht, search and `+ Create`, and context-aware links between modules.
- Suppliers and contacts are shared reference records. An intervention can link to a supplier and quotation; an Office action item can create a task; a charter checklist can link to an existing maintenance issue.
- Lists have search, sorting, useful filters, creation and edit actions. Destructive actions require confirmation explaining how linked records are handled. Preserve historical references when appropriate rather than silently cascading deletes.
- Every status change and significant edit is recorded in a readable activity timeline. The dashboard and linked screens update after changes.
- Captains should never have to enter the same task twice. If a maintenance issue blocks a charter, the charter links to that issue instead of duplicating it.

### Core records

- **Yacht**: name, length in metres, operational mode (`Private`, `Charter`, `Both`), optional photo/notes. Only one active yacht is required for the MVP; model ownership by yacht to support future multi-yacht isolation.
- **Crew member**: name, role (`Captain`, `Chief Engineer`, `Chief Stewardess`, `Chef`, `Deck Crew`, `Other`), department and contact details. Crew entries are assignable people, **not login accounts** in the MVP.
- **Supplier**: name, service category, contact details and notes.
- **Maintenance issue**: title, description, equipment/area, priority, status, reported date, due date, assigned crew member, optional supplier and quotation, plus an activity timeline.
- **Guest visit / charter preparation**: name or reference, visit type (`Private`, `Charter`), arrival/departure times, preparation status, optional captain-approved timestamp and department checklists. Avoid storing identifiable guest preferences in the MVP.
- **Task**: canonical shared action with source type and source ID, owner, due date, priority, status, notes and activity history.
- **Quotation**: supplier, reference, amount and explicit currency, status (`Requested`, `Received`, `Under Review`, `Approved`, `Rejected`) and optional linked issue; approvals are recorded as operator actions, not executed purchases.
- **Office item**: manually entered message/document reference with category, sender/source label, date, summary/notes and optional linked tasks; reply drafts are editable text.
- **Activity**: timestamped event associated with a record, with event type and description. MVP records actions by the single local operator, without pretending to identify multiple authenticated users.

### Sample data

On first start, YachtOps contains realistic **fictional** yacht and operational data: a 50 m mixed-use yacht, department heads and suppliers, maintenance issues at every stage including overdue/critical items, an upcoming arrival with unfinished department checklists, an issue blocking readiness, quotations awaiting review, Office items and tasks due soon. Sample records must not contain real guest details, credentials or commercially sensitive information. Seed data must make all three modules and their shared relationships immediately explorable.

### Look and feel

Follow `docs/BRAND.md`, which takes precedence over general design preferences. The MVP is light mode and optimized for laptops/desktops. The aesthetic is a restrained, high-end maritime operations product: clear priorities, legible data, generous spacing, helpful status labels and purposeful charts. Avoid ornamental yachting motifs and decorative metrics. Tablet/mobile layouts and dark mode follow later.

## Affected users and systems

- **MVP operator:** one captain or delegated yacht coordinator running the application locally to manage one yacht.
- **Represented stakeholders:** chief engineer, chief stewardess, chef, deck crew, suppliers and yacht manager exist as assignable/contact records but do not log in during the MVP.
- **External systems:** none are required. The local MVP does not connect to email accounts, messengers, accounting systems, maintenance control systems or yacht navigation/safety systems.

## Constraints

- Follow `docs/TECH_STACK.md` and `docs/BRAND.md`.
- One documented cross-platform command starts frontend and backend locally. Normal MVP use requires no internet connection; assets needed offline should be bundled or have local fallbacks.
- Store all operational data persistently in local SQLite. Changes survive browser refreshes and app restarts. Use a separate isolated database for automated tests.
- One documented reset command restores fictional sample data. Reset is destructive and clearly documented.
- Represent dates/times unambiguously, store timestamps in UTC and display the configured yacht/local time zone; show amounts with currency (default EUR for seed data).
- Do not claim regulatory compliance, safety certification, equipment health, guest readiness or completed repairs without human review. `Ready — Captain Approved` and quotation approvals must have explicit manual actions.
- Never send messages, place orders, spend money or authorize suppliers automatically.
- **Not in this MVP:** authentication and multi-user collaboration; multi-tenant cloud hosting; real email/WhatsApp/calendar connections; generative AI integrations; automatic PDF ingestion or RAG; file upload/storage; financial transactions; guest profiles; certified preventive-maintenance scheduling; offline mobile sync; push notifications; export/import; dark mode. These are candidates for later, separately scoped work.

## Success criteria

1. A non-technical reviewer can follow `docs/STATUS.md`, run `npm run dev`, open YachtOps in a browser and explore all five sections with meaningful fictional data.
2. Maintenance issues can be created, searched, filtered, sorted, edited and deleted with confirmation. Status changes, including Kanban moves, persist after refresh/restart and show in the record timeline; critical and overdue issues are visible on the dashboard.
3. A preparation plan can be created for either a private visit or charter. Department tasks can be assigned and completed; their progress and readiness indicators are computed from stored tasks. An unresolved linked maintenance issue appears as a blocker.
4. The application never automatically labels a preparation `Ready — Captain Approved`. A user must confirm readiness explicitly; reopening a blocker after approval visibly invalidates or flags the prior approval for re-review.
5. Office items, quotations and editable drafts can be created, searched, linked to tasks and changed; a weekly operational summary can be assembled deterministically from stored records, with review/edit before use and without falsely claiming LLM generation.
6. Shared tasks appear consistently in their source module, Tasks & Calendar and the Dashboard. Completing a task changes all views without creating a second copy.
7. Supplier references, activity histories, recent activity and the dashboard's counts/charts agree with the database. Records and relationships remain intact after restart. `npm run seed` reliably restores the sample scenario.
8. The UI follows `docs/BRAND.md`, includes appropriate empty/loading/error states, and supports keyboard interaction and non-color-only status indicators.
9. `npm test` runs frontend, backend and real-browser E2E tests against isolated data. End-to-end browser checks cover at least one cross-module workflow: report a maintenance issue → link it as a charter blocker → record a supplier quotation and action item → complete the intervention → review charter readiness → explicitly approve it. Inspect all main screens visually and confirm no browser console errors.

## Open questions

- Who is the paying customer: captain, owner, yacht management company or service provider? Validate with real interviews before cloud/SaaS investment.
- Which systems are already in use onboard, and what integration would remove more friction than it introduces?
- What collaboration and audit requirements apply when introducing real crew accounts and role-based permissions?
- Which AI workflows have measurable value and what data may lawfully be sent to a third-party model?
- Which mobile/offline needs are essential for actual deck, interior and engineering workflows?
