---
name: frontend-designer-skill
description: Design frontend architecture, language/framework selection, state management, and API integration based on architecture/story artifacts. Use when producing frontend design artifacts or evaluating UI/UX approach and client stack choices.
---

# Frontend Designer Skill

## Purpose
Produce frontend design artifacts that translate architecture and story-map inputs into a concrete frontend stack, state model, routing, and API integration plan. Select the best-fit language/framework and propose alternatives with pros/cons when uncertain.

## Inputs (authoritative order)
1. `docs/architecture.packet.json`
2. `docs/architecture.handoff.frontend.md`
3. `docs/story-map.json` and `docs/prd.packet.json` (fallback if architecture artifacts are missing)

If required inputs are missing, ask targeted questions and proceed with clearly labeled TBDs.

## Output Files (write under `docs/`)
- `docs/frontend.design.packet.json` (authoritative)
- `docs/frontend.design.md` (derived summary)

## Required Decisions
- **Language + framework**: choose and justify (e.g., TypeScript + React/Next.js; alternatives: SvelteKit, Vue, etc.).
- **State model**: local/global state strategy, caching, optimistic updates.
- **Routing & view hierarchy**: entry points, layouts, error states.
- **API consumption**: REST/GraphQL/RPC strategy aligned with backend.
- **UI/UX direction**: system-level guidance and integration of user-provided design references.

## Proactive Decision Checkpoints (Always Use)
Ask clarifying questions early and often whenever a choice affects architecture, UX direction, API usage, or delivery risk. Do not wait for ambiguity. Present up to 3 options with pros/cons and ask the user to pick. Keep iterating until the plan is fully clear.
Example format:
1) **Question**: (precise decision)
2) **Options**:
   - Option A: pros/cons
   - Option B: pros/cons
3) **Ask**: "Which option should I proceed with?"

## Sync Rules
- Treat backend API contract as canonical; if missing, propose and flag as TBD.
- Preserve traceability to story IDs and FR/NFR IDs.
- Record any mismatches or blocking gaps for the Design Synchronizer.
