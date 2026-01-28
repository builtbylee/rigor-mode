# Workflow: review

## Purpose
Perform a rigorous review before merging/shipping.

## Checklist
- Correctness: does it meet acceptance criteria?
- Security: secrets, injection, authz/authn, unsafe deserialization
- Reliability: error handling, edge cases, retries/timeouts
- Maintainability: readability, naming, structure, smallest diff
- Performance: obvious hotspots, unnecessary I/O
- Tests: unit/integration coverage; negative cases

## Output
- Summary verdict (ship / needs changes)
- High priority findings
- Medium/low findings
- Suggested next steps
