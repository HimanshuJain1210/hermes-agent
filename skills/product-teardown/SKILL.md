---
name: product-teardown
description: >
  Analyzes any product through a structured multi-lens framework and outputs a
  sharp teardown with concrete findings and opportunities. Trigger when the user
  says "tear down", "analyze this product", "do a product review of", "break down
  how X works", or gives a product name/URL and wants critique.
triggers:
  - tear down
  - teardown
  - analyze this product
  - product review
  - break down this app
  - how does this product work
version: 1.0
---

# Product Teardown

## Purpose
Produce a rigorous, opinionated teardown of a product — not a feature list, but an
analysis of *why* it's built the way it is, where it wins, and where it's exposed.
A good teardown gives a reader insight they couldn't get by just using the product.

## When to use
- User names a product or pastes a URL and wants analysis.
- User asks how a product acquires, activates, retains, or monetizes users.

## When NOT to use
- User wants to write a spec for their own product (use prd-generator).
- User wants competitor positioning across a market (that's a competitive scan, broader).

## The six lenses
Analyze the product through each lens in order. If you lack data for a lens, say so
rather than guessing.

1. **Problem & Audience** — What real problem does it solve, and for whom? Is the
   problem frequent and painful, or nice-to-have?
2. **Core Loop** — The main action users repeat. What's the shortest path to value?
   Map: trigger → action → reward → reinvestment.
3. **Onboarding & Activation** — How fast does a new user reach the "aha" moment?
   Where do people drop off?
4. **Retention & Engagement** — What brings users back? Habit, network, content,
   utility? Is retention earned or coerced (e.g. dark patterns)?
5. **Monetization** — How does it make money, and does the model align with user value?
   Where's the tension between growth and revenue?
6. **Moat & Risk** — What's defensible (network effects, data, switching cost, brand)?
   What could kill it (platform risk, commoditization, a faster competitor)?

## Procedure
1. Confirm the product. If a URL is given and the browser tool is available, look at
   the actual product before analyzing.
2. Work through all six lenses. Be concrete — cite specific UI choices, flows, pricing.
3. For each lens, state a finding AND its implication.
4. End with the 3 sharpest opportunities or risks — the things a PM there should act on.
5. Keep opinions defensible. Distinguish observation ("the signup needs a credit card")
   from inference ("this likely filters for high-intent users").

## Output template
```
# Teardown: [Product]

## Snapshot
[1–2 sentences: what it is, who it's for.]

## 1. Problem & Audience
Finding: …
Implication: …

## 2. Core Loop
[trigger → action → reward → reinvestment]
Finding: …
Implication: …

## 3. Onboarding & Activation
Finding: …
Implication: …

## 4. Retention & Engagement
Finding: …
Implication: …

## 5. Monetization
Finding: …
Implication: …

## 6. Moat & Risk
Moat: …
Risk: …

## Top 3 Opportunities / Risks
1. …
2. …
3. …
```

## Pitfalls
- Don't just describe the product — analyze the *choices* behind it.
- Separate fact from inference clearly.
- If you haven't seen the actual product and can't, flag that your analysis is from
  general knowledge and may be dated.
- Avoid generic advice ("improve UX"). Every recommendation must be specific enough
  to action.
