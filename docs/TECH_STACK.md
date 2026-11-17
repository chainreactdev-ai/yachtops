# YachtOps — Technical stack

This project uses the following high-level stack, preserving the template's local-first architecture:

1. **Frontend:** Node.js 24+ (use the currently supported LTS), TypeScript, React and Vite in `frontend/`.
2. **Backend:** Python 3.12, `uv` and FastAPI in `backend/`, with `pyproject.toml` and `uv.lock` at the repository root.
3. **API:** JSON over HTTP between React and FastAPI; explicit request/response schemas and input validation.
4. **Persistence:** a local SQLite file managed by SQLAlchemy Core (no handwritten raw SQL). Initialize the schema and populate fictional sample data when the database is new. Keep relational links between yachts, crew, suppliers, maintenance issues, visit preparations, shared tasks, quotations, Office items and activities.

Use established libraries for accessible UI primitives, tables, charts, calendar/timelines and Kanban drag-and-drop instead of inventing custom infrastructure. Choose dependencies only when needed. All data modifications go through the API; the frontend must not use a separate mock source after initial development.

## Scope and architecture

- The **MVP runs locally**, for one operator and one active yacht, without authentication or mandatory internet access.
- Organize FastAPI code by clear domain boundaries: `maintenance`, `charter`, `office`, `tasks`, `suppliers` and shared records. Shared tasks are canonical; modules link to task IDs rather than copying tasks.
- Derive dashboard KPIs and readiness from persisted records. Readiness approval and quotation decisions are explicit human actions.
- Timestamps are stored in UTC and rendered using a configured yacht/local time zone. Monetary amounts use decimal-safe representations and include an ISO currency code.
- Keep the local database outside disposable build directories. Use an independent database for tests and fixture resets.
- Avoid storing private guest details, passwords, email tokens or sensitive yacht information in sample data.
- **No LLM is required for MVP operation.** Captain's AI Office initially provides structured administration, editable drafts and deterministic reports. Later AI providers, RAG, mail integrations and document processing should be isolated behind opt-in interfaces with authorization, redaction, cost controls and auditability; do not fabricate AI output.
- **Later, not part of MVP:** Supabase for sign-in and hosted database, and Render (or a deployment platform selected after validation) for hosted operation. Multi-tenant isolation, roles and security review are required before production deployment.

## Commands

The repository root has a `package.json` and `frontend/` is an npm workspace. Cross-platform npm scripts provide:

- `npm run dev` — starts backend and frontend together.
- `npm test` — runs all unit and E2E tests; fails if any test fails; E2E launches the application itself.
- `npm run seed` — **destructively resets** the local development database to fictional sample records. Never point this command at production data.

`docs/STATUS.md` describes actual setup, commands and project state. Add or update the root `README.md` only if the repository owns it; if it contains unrelated external course material, do not silently overwrite it.

## Testing

1. **Frontend:** Vitest for components, state-driven UI, validation and readiness indicators.
2. **Backend:** pytest for API/domain behavior, persistence, links, approvals, date logic and invalid input.
3. **End-to-end:** Playwright Test (`@playwright/test`) in `e2e/`, using the installed Chrome/browser setup. Tests start their own local instance and use an isolated database; they must never reset or modify the operator's regular data.
4. **Cross-module invariant tests:** one issue linked to a charter blocker; one canonical shared task across views; readiness cannot be implicitly approved; reopening a blocker triggers re-review; Office item → task → related maintenance/charter record; accurate dashboard aggregates.

Do not claim a command works or a test passes until it has actually been executed in the target environment.
