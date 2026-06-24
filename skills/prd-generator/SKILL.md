---
name: prd-generator
description: >
  Turns a rough feature or product idea into a structured, review-ready PRD.
  Trigger when the user asks to "write a PRD", "spec this out", "draft requirements",
  "turn this idea into a doc", or describes a feature and wants it formalized.
triggers:
  - write a prd
  - draft a prd
  - spec this out
  - product requirements
  - turn this into a doc
  - formalize this feature
version: 1.0
---

# PRD Generator

## Purpose
Convert a loosely described idea into a crisp PRD a team could actually build from.
A good PRD removes ambiguity: what we're building, for whom, why now, and how we'll
know it worked. It is NOT a wishlist — every requirement must trace to a user problem.

## When to use
- User hands you a feature idea, a problem statement, or a half-formed concept.
- User explicitly asks for a PRD, spec, or requirements doc.

## When NOT to use
- User wants a competitive teardown (use product-teardown).
- User wants to spec an LLM/AI feature specifically (use ai-feature-spec).

## Procedure
1. **Restate the problem in one sentence.** If you can't, ask the user one clarifying
   question. Never invent the problem.
2. **Identify the target user and their job-to-be-done.** Who hurts today, and what
   are they trying to accomplish?
3. **State the "why now"** — what changed (market, tech, user behavior) that makes
   this worth doing.
4. **Define the solution at a high level** before details. One paragraph.
5. **Write functional requirements** as testable statements ("The system shall…").
   Each must map to the problem. Flag any that don't.
6. **Write non-functional requirements** (performance, privacy, accessibility, cost).
7. **Define success metrics** — one primary metric, two guardrail metrics.
8. **List explicit out-of-scope items** to prevent scope creep.
9. **Surface open questions and risks** honestly. A PRD that hides risk is worse
   than useless.
10. **Fill the output template** exactly. Keep it tight — length is not quality.

## Output template
```
# PRD: [Feature Name]

## 1. Problem
[One-sentence problem statement.]
[2–3 sentences of context: who has it, how often, what it costs them.]

## 2. Target User & JTBD
- User: [persona]
- Job-to-be-done: "When [situation], I want to [motivation], so I can [outcome]."

## 3. Why Now
[What changed that makes this the right time.]

## 4. Solution Overview
[One paragraph. The shape of the solution, not the details.]

## 5. Functional Requirements
- FR1: The system shall [testable behavior]. → solves [problem element]
- FR2: …

## 6. Non-Functional Requirements
- Performance: …
- Privacy/Security: …
- Cost/Constraints: …

## 7. Success Metrics
- Primary: [metric + target]
- Guardrail 1: [must-not-regress metric]
- Guardrail 2: …

## 8. Out of Scope
- [Explicitly not doing X in v1]

## 9. Open Questions & Risks
- Risk: [risk] → Mitigation: [plan]
- Open question: [unresolved decision + who decides]
```

## Pitfalls
- Don't pad with buzzwords. Every line earns its place.
- Don't write requirements you can't test.
- If the idea is too vague to spec, ask ONE question, then proceed on stated assumptions.
- Always include out-of-scope and risks — these signal PM maturity.
