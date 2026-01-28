---
name: backend-designer-skill
description: Design backend architecture, API contracts, core business logic boundaries, and language/framework choices based on architecture/story artifacts. Use when selecting backend stack, auth strategy, and service design.
---

# Backend Designer Skill

## Purpose
Produce backend design artifacts that define the API surface, core logic boundaries, and platform choices (language, framework, runtime). Provide recommended defaults and alternatives with pros/cons.

## Inputs (authoritative order)
1. `docs/architecture.packet.json`
2. `docs/architecture.handoff.backend.md`
3. `docs/story-map.json` and `docs/prd.packet.json` (fallback)

If required inputs are missing, ask targeted questions and proceed with clearly labeled TBDs.

## Output Files (write under `docs/`)
- `docs/backend.design.packet.json` (authoritative)
- `docs/backend.design.md` (derived summary)

## Required Decisions
- **Language + framework**: recommend and justify (e.g., Python + FastAPI vs Django; Node + NestJS; Go).
- **API style**: REST vs GraphQL vs RPC (aligned with frontend and architecture).
- **Core logic boundaries**: domain services/modules and responsibilities.
- **Authn/Authz**: JWT/session/OAuth/SSO; role/permission model.
- **Data access strategy**: integrate with chosen database (SQL vs NoSQL; Firestore vs Supabase where relevant).
- **Error handling, retries, observability**: define expected behaviors.

## Questions & Options (Required When Uncertain)
Ask targeted questions with 2–3 options and pros/cons whenever a choice cannot be derived from inputs.
Example format:
1) **Question**: (precise decision)
2) **Options**:
   - Option A: pros/cons
   - Option B: pros/cons
3) **Ask**: “Which option should I proceed with?”

## Sync Rules
- Backend defines the **canonical API contract** unless explicitly delegated.
- Record any API mismatches or unclear data dependencies for the Design Synchronizer.
- Preserve traceability to story IDs and FR/NFR IDs.
