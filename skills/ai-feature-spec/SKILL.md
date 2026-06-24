---
name: ai-feature-spec
description: >
  Specs an AI/LLM-powered feature with the rigor that AI products specifically need —
  model behavior, prompts, evals, failure modes, and guardrails. Trigger when the user
  wants to spec something that uses an LLM, "add AI to", "build a copilot/agent/chatbot",
  or asks how to design an AI feature responsibly.
triggers:
  - ai feature
  - llm feature
  - spec an ai
  - add ai to
  - build a copilot
  - design an agent
  - ai guardrails
  - prompt spec
version: 1.0
---

# AI Feature Spec

## Purpose
Spec an AI-powered feature the way AI features actually break in production. A normal
PRD assumes deterministic behavior; LLM features are probabilistic, can fail silently,
and can be misused. This skill forces you to define the model's job, its boundaries,
how you'll measure quality, and what happens when it's wrong.

## When to use
- The feature's core depends on an LLM, ML model, or agent.
- User asks to "add AI", build a copilot/assistant/agent, or design prompting/evals.

## When NOT to use
- A standard non-AI feature (use prd-generator).
- Pure competitive analysis (use product-teardown).

## Procedure
1. **Define the AI's job in one sentence.** What does the model actually do? If the
   answer is "everything," narrow it.
2. **Decide: does this even need an LLM?** State why a model is the right tool vs.
   rules/search/heuristics. AI-PMs earn trust by NOT over-using AI.
3. **Specify inputs and outputs.** What goes in (user input, context, retrieved data),
   what comes out (format, structure, length). Define the output contract.
4. **Draft the system prompt intent** — not the final prompt, but what it must enforce:
   role, constraints, tone, refusal conditions.
5. **Map failure modes.** For LLM features these are specific: hallucination, wrong
   format, prompt injection, latency spikes, cost spikes, refusal of valid requests,
   and confidently-wrong answers. For each, define detection + handling.
6. **Define evals.** How do you know it's good? Specify: a small golden test set,
   the quality dimensions (accuracy, format adherence, safety), and pass thresholds.
7. **Set guardrails.** Input validation, output filtering, human-in-the-loop for
   high-stakes actions, rate/cost limits, and a fallback when the model fails.
8. **Choose model + cost posture.** Which model tier, why, and the cost ceiling per
   action. Note when a cheaper model suffices.
9. **Fill the output template.**

## Output template
```
# AI Feature Spec: [Feature Name]

## 1. The AI's Job
[One sentence: exactly what the model does.]

## 2. Why AI (vs. rules/search)
[Justify using a model. If a non-AI approach is viable, say so.]

## 3. Input / Output Contract
- Inputs: [user input, context, retrieved data]
- Output: [format, structure, max length]
- Output must always: [hard constraints]

## 4. System Prompt Intent
- Role: …
- Must enforce: …
- Must refuse when: …

## 5. Failure Modes & Handling
| Failure | Detection | Handling |
|---|---|---|
| Hallucination | … | … |
| Wrong format | … | … |
| Prompt injection | … | … |
| Latency/cost spike | … | … |
| Confidently wrong | … | … |

## 6. Evals
- Golden set: [N representative cases]
- Dimensions: accuracy / format / safety
- Pass threshold: [e.g. 95% format adherence, 0 safety violations]

## 7. Guardrails
- Input validation: …
- Output filtering: …
- Human-in-the-loop: [where, for what actions]
- Cost/rate limit: …
- Fallback when model fails: …

## 8. Model & Cost
- Model: [tier + why]
- Cost ceiling: [per action]
- Cheaper-model note: [where a smaller model suffices]
```

## Pitfalls
- The #1 AI-PM mistake is shipping with no evals. Never skip section 6.
- "Confidently wrong" is the most dangerous failure — always plan for it.
- Don't use the biggest model by default; justify the tier against cost.
- For any action with real-world consequences (sending, deleting, paying), require
  human confirmation. State this explicitly.
- Treat prompt injection as a guaranteed attempt, not an edge case, whenever the
  model reads untrusted text (web pages, user uploads, emails).
