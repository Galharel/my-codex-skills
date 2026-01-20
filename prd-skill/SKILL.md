---
name: prd-scheme
description: Normalize and refine an existing PRD (PDF/GDoc/MD text) into a structured PRD packet and a clean handoff for the User Story Mapper.
metadata:
  version: "1.0"
  category: "product"
  inputs: ["raw_prd_text", "optional_context"]
  outputs: ["normalized_prd_markdown", "prd_packet_json"]
---

# PRD Scheme Skill (PRD Refiner + Handoff Generator)

## Purpose
Given an existing PRD (often messy, incomplete, or unstructured), produce:
1) A **Normalized PRD** in consistent Markdown sections
2) A **PRD Packet (JSON)** that conforms to `assets/prd_packet.schema.json`
3) A **User Story Mapper Handoff** embedded in the PRD Packet (and optionally as a Markdown section)

This skill must work in two modes:
- **Flow mode:** expects upstream artifacts may exist (e.g., prior PRD outputs), uses them if present.
- **Standalone mode:** if upstream artifacts are missing, derive what’s needed from the PRD and clearly mark TBDs + generate questions.

## When to Use
Use when the user provides (or references) a PRD and asks to:
- refine it / make it clearer
- make it “agent-ready”
- prepare a handoff for user stories
- convert a PRD into a structured schema / markdown

## Inputs
- `raw_prd_text` (required): pasted text extracted from PDF/GDoc/MD or a summarized PRD.
- `optional_context` (optional): product constraints, team conventions, target platforms, deadlines, etc.
- Optional upstream artifacts (if available): prior normalized PRD, architecture notes, existing user stories.

## Outputs
### A) Normalized PRD Markdown
A Markdown document with these top-level headings (always output, even if some sections are TBD):
1. Overview
2. Problem
3. Users & Personas
4. Goals & Success Metrics
5. Scope (In / Out)
6. Assumptions & Constraints
7. User Journeys / Key Flows
8. Requirements
   - Functional Requirements (FR-###)
   - Non-Functional Requirements (NFR-###)
9. Edge Cases & Error States
10. Dependencies
11. Risks
12. Open Questions (TBDs)
13. User Story Mapper Handoff (summary)

### B) PRD Packet JSON
Emit JSON that validates against `assets/prd_packet.schema.json`.

## Procedure
1. **Ingest & Triage**
   - Identify: product, users, goals, scope, key flows, requirements, constraints.
   - Detect missing/contradictory info.

2. **Normalize Structure**
   - Rebuild the PRD into the standard Markdown section set.
   - Keep phrasing crisp and testable where possible.

3. **Requirements Extraction**
   - Convert vague statements into explicit requirements.
   - Assign IDs:
     - FR-001, FR-002… for functional
     - NFR-001… for non-functional
   - Add acceptance criteria when possible.
   - If acceptance criteria cannot be derived, mark as TBD and add a precise question.

4. **Quality Checks**
   - Requirements should be: unambiguous, testable/verifiable where possible.
   - Flag anything that is:
     - ambiguous (“fast”, “easy”, “secure” with no measure)
     - missing actors/roles
     - missing success metrics
     - missing error-handling expectations

5. **Generate User Story Mapper Handoff**
   - Provide:
     - personas/actors
     - epics (grouped by journey/goal)
     - candidate user stories (as a starting point)
     - acceptance criteria link-back to FR/NFR IDs
     - release slices (MVP vs later), if inferable

6. **Standalone Fallback Rules**
   If the PRD lacks critical info, do not stall. Instead:
   - Create a minimal best-effort draft with clearly labeled:
     - `tbd` fields
     - `assumptions_made`
     - `open_questions`
   - Prefer asking **targeted** questions (not generic ones).
   - Keep the handoff usable even if incomplete.

## Failure Modes & What To Do
- **PRD is too high-level:** produce a normalized PRD + a list of “precision questions” needed to make it implementable.
- **PRD conflicts with itself:** list conflicts explicitly and propose 1–2 plausible resolutions as options.
- **Missing user personas:** infer minimal actors (e.g., Admin/User/Guest) and mark as assumptions.

## Output Formatting Rules
- Always output:
  1) Normalized PRD Markdown
  2) PRD Packet JSON (separate fenced block)
- In the JSON, include `confidence` per section (0–1) if uncertain.
- Keep IDs stable and consistent across outputs.

## Example Prompt That Should Trigger This Skill
“Here’s my PRD from Google Docs. Please refine it and generate the best handoff for the user story mapper.”

