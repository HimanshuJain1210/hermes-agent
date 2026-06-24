# PM Agent — A Product Manager AI Agent

A customized fork of [Hermes Agent](https://github.com/NousResearch/hermes-agent)
turned into an autonomous **Product Manager AI Agent**. It thinks like an experienced
PM — problem-first, user-obsessed, scope-disciplined — and ships real PM artifacts on
demand.

Built by **Himanshu Jain** ([@HimanshuJain1210](https://github.com/HimanshuJain1210)) as part of the HelloPM AI PM build challenge.

---

## What this is

Hermes is an open-source agent with persistent memory and a self-writing skill system.
This fork keeps that engine and adds a PM brain on top of it:

- A **PM identity** (`AGENT.md`) that gives the agent product judgment and operating
  principles.
- Three **PM skills** that turn it from a generic agent into a working PM teammate.

The result: ask it to spec a feature, tear down a product, or design an AI feature, and
it produces structured, review-ready output.

---

## What it can do

| Skill | Trigger it with | Output |
|---|---|---|
| **PRD Generator** | "write a PRD for…", "spec this out" | A structured, testable PRD with problem, JTBD, requirements, metrics, scope, and risks |
| **Product Teardown** | "tear down…", "analyze this product" | A six-lens teardown: Problem & Audience, Core Loop, Onboarding, Retention, Monetization, Moat & Risk + top opportunities |
| **AI Feature Spec** | "spec an AI feature…", "add AI to…" | An LLM-feature spec with output contract, failure modes, evals, and guardrails |

---

## What's customized in this fork

```
AGENT.md                          ← PM identity & operating principles
skills/
  prd-generator/SKILL.md          ← idea → PRD
  product-teardown/SKILL.md       ← product → six-lens analysis
  ai-feature-spec/SKILL.md        ← AI feature → rigorous spec
```

Everything else is the upstream Hermes engine.

---

## How to run it

1. Fork or clone this repo.
2. Follow the upstream [Hermes setup](https://github.com/NousResearch/hermes-agent)
   to install and configure the agent.
3. Connect a model provider. This build was tested with **Groq**
   (`llama-3.3-70b-versatile`) via the OpenAI-compatible endpoint
   `https://api.groq.com/openai/v1`.
4. Make sure the `AGENT.md` and `skills/` files in this repo are picked up by the agent.
5. Talk to it and try a prompt like:
   - `Write a PRD for a study-timer app for students`
   - `Tear down Duolingo`
   - `Spec an AI feature that summarizes student doubts`

> Note: model and channel setup follow the upstream Hermes docs. This fork only adds
> the PM identity and skills.

---

## Design notes

- **Problem-first by default.** The agent restates the goal before solving and asks
  one sharp question when the problem is unclear.
- **AI-PM rigor.** The AI Feature Spec skill forces evals, failure-mode planning, and
  guardrails — the things AI features actually need and most specs skip.
- **Safe by design.** The agent treats instructions inside untrusted content (web
  pages, uploads) as data, not commands, and confirms before any consequential action.

---

## Credits

- Engine: [Hermes Agent](https://github.com/NousResearch/hermes-agent) by Nous Research (MIT).
- PM customization (identity + skills): **Himanshu Jain**.
