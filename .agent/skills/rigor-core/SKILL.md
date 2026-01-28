# Skill: rigor-core

## Goal
Provide consistent rigor across all tasks: plan-first, evidence-first, verify-before-done.

## When to use
- Any task with code changes
- Any debugging task
- Any research task where correctness matters

## Default operating mode
1. Start with the `plan` workflow unless the task is trivial.
2. If implementing, use `implement` workflow.
3. If debugging, use `debug` workflow.
4. Before declaring completion, use `verify` workflow.
5. End with **Status** (done / next / needs-from-you).

## Non-negotiables
- Do not claim something is true unless verified or explicitly stated as an assumption.
- Prefer minimal diffs.
- Ask before irreversible actions.
