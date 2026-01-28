---
name: agentic-designer-skill
description: Design agentic systems end-to-end (orchestration, memory/RAG, tools/MCP, prompt strategy) based on architecture artifacts. Use when defining agents, sequencing, tool contracts, and context management.
---

# Agentic System Designer Skill

## Purpose
Produce agentic design artifacts covering orchestration, memory/context/RAG, tool definitions (including MCP when needed), and prompt strategy in a single, unified design.

## Inputs (authoritative order)
1. `docs/architecture.packet.json`
2. `docs/architecture.handoff.agentic.md` (if available)
3. `docs/story-map.json` and `docs/prd.packet.json` (fallback)

If required inputs are missing, ask targeted questions and proceed with clearly labeled TBDs.

## Output Files (write under `docs/`)
- `docs/agentic.design.packet.json` (authoritative)
- `docs/agentic.design.md` (derived summary)

## References
- Read `references/langchain-capabilities.md` for a checklist of LangChain capability areas and doc sections to review when proposing agentic enhancements.

## Required Decisions
- **Orchestration**: agents, sequencing, parallelism, retries, escalation paths.
- **Memory/Context/RAG**: memory layers, retrieval strategy, storage boundaries.
- **Tools/MCP**: tool contracts, capability definitions, MCP server outline when needed.
- **Prompt strategy**: system prompts, role separation, guardrails.

## Questions & Options (Required When Uncertain)
Ask targeted questions with 2–3 options and pros/cons when agent scope or constraints are unclear.
Example format:
1) **Question**: (precise decision)
2) **Options**:
   - Option A: pros/cons
   - Option B: pros/cons
3) **Ask**: “Which option should I proceed with?”

## Sync Rules
- Align with backend interfaces and data constraints.
- Record tool/API mismatches or missing permissions for the Design Synchronizer.
- Preserve traceability to story IDs and FR/NFR IDs.
