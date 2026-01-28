# Workflow: implement

## Purpose
Implement changes safely with minimal diff and high correctness.

## Steps
1. Confirm current behavior / baseline.
2. Identify the smallest change that can satisfy acceptance criteria.
3. Make changes.
4. Add/adjust tests or verification steps.
5. Re-run verification.

## Guardrails
- Prefer minimal diffs.
- Avoid broad refactors unless required.
- If a change is risky/irreversible, ask before proceeding.

## Output
- What changed (high-level)
- Why it changed
- Verification performed
- Remaining risks / TODOs
