# Workflow: debug

## Purpose
Find root cause without thrashing.

## Steps
1. Reproduce: describe the minimal repro.
2. Observe: collect logs/output; note what you expected vs got.
3. Hypothesize: list 2–4 plausible root causes.
4. Test hypotheses one-by-one (cheapest/highest-signal first).
5. Confirm root cause.
6. Fix minimally.
7. Add regression test or durable check.

## Output
- Repro
- Observations
- Root cause
- Fix
- Verification
