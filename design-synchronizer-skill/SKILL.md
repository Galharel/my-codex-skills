---
name: design-synchronizer-skill
description: Synchronize designer outputs (frontend, backend, data, agentic, security) against architecture artifacts, detect conflicts, and require a zero-conflicts pass before design is marked ready.
---

# Design Synchronizer Skill

## Purpose
Validate and synchronize all designer outputs, identify conflicts, and enforce a final zero-conflicts pass before design is declared ready for implementation. Proactively ask clarifying questions whenever a resolution choice affects scope, interfaces, or risk; provide up to 3 options with pros/cons so the user can choose.

## Inputs (authoritative order)
1. `docs/architecture.packet.json`
2. `docs/frontend.design.packet.json`
3. `docs/backend.design.packet.json`
4. `docs/data.schema.packet.json`
5. `docs/agentic.design.packet.json`
6. `docs/security.design.packet.json`

If any inputs are missing, ask targeted questions and identify which designer must re-run.

## Output Files (write under `docs/`)
- `docs/design.sync.packet.json` (authoritative)
- `docs/design.sync.report.md` (derived summary)

## Required Checks
- API contract consistency (frontend ↔ backend).
- Data model alignment (backend ↔ database).
- Agentic tools/permissions alignment (agentic ↔ backend/security).
- Security controls coverage for all critical components.
- Traceability coverage (stories/FR/NFR mapped to designs).

## Conflict Handling
- List each conflict with impacted artifacts and severity.
- For each conflict, provide up to 3 resolution options with pros/cons.
- Identify which designer(s) must re-run to resolve the conflict.

## Exit Criteria
- Only mark design as ready when a **zero-conflicts** pass is achieved.
