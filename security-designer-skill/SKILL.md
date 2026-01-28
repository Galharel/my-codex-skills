---
name: security-designer-skill
description: Design security controls (auth, authorization, threat model, audit, secrets, data protection) based on architecture/backend/data artifacts. Use when defining security posture and mapping controls to system components.
---

# Security Designer Skill

## Purpose
Produce security design artifacts that define threat model, auth strategy, data protection, and operational controls aligned with architecture, backend, and data designs.

## Inputs (authoritative order)
1. `docs/architecture.packet.json`
2. `docs/backend.design.packet.json` (if available)
3. `docs/data.schema.packet.json` (if available)
4. `docs/story-map.json` and `docs/prd.packet.json` (fallback)

If required inputs are missing, ask targeted questions and proceed with clearly labeled TBDs.

## Output Files (write under `docs/`)
- `docs/security.design.packet.json` (authoritative)
- `docs/security.design.md` (derived summary)

## Required Decisions
- **Threat model**: attack surfaces, risks, mitigations.
- **Authn/Authz**: mechanisms, role model, session/token design.
- **Data protection**: encryption at rest/in transit, key management.
- **Operational controls**: audit logging, rate limits, abuse prevention, secrets handling.

## Security Clarity Gate (Always Use)
Ask probing questions whenever security requirements, compliance constraints, or threat surfaces could alter controls. Do not assume. Provide up to 3 options with pros/cons and ask the user to choose. Continue until the security plan is explicit and testable.
Example format:
1) **Question**: (precise decision)
2) **Options**:
   - Option A: pros/cons
   - Option B: pros/cons
3) **Ask**: "Which option should I proceed with?"

## Sync Rules
- Ensure security controls map to backend and data designs.
- Record security-related conflicts for the Design Synchronizer.
- Preserve traceability to story IDs and FR/NFR IDs.
