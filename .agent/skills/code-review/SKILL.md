# Skill: code-review

## Goal
Catch correctness, security, and maintainability issues before shipping.

## Process
- Use the `review` workflow.
- Produce:
  - Summary verdict
  - High priority findings (must-fix)
  - Medium/low findings
  - Suggested next steps

## Review focus
- Correctness vs acceptance criteria
- Evidence quality (is the fix actually addressing root cause?)
- Security basics (secrets, injection, auth)
- Edge cases and error handling
- Tests and regressions
