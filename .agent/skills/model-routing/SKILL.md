# Skill: model-routing (Opus + Gemini)

## Goal
Use Opus 4.5 and Gemini 3 Pro deliberately to increase correctness and reduce thrash.

## Routing
- Use Opus 4.5 for:
  - planning with constraints
  - debugging / root-cause analysis
  - security reasoning
  - final review / decision making

- Use Gemini 3 Pro for:
  - generating alternatives
  - summarizing long inputs
  - checklist generation
  - “second opinion” sanity checks

## Disagreement protocol
When the models disagree:
1. State the disagreement explicitly.
2. Identify which claims are factual vs judgment.
3. Propose verification steps for factual disagreements.
4. Choose a path with reasons.
