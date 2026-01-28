# Rule: Verification

## Principle
Every change must be proven to work. "It should work" is not acceptable.

## Requirements

### 1. Acceptance Criteria
Before implementation:
- Define what "done" looks like
- Make criteria testable and specific
- Get agreement on criteria before starting

### 2. Verification Methods
In order of preference:
1. **Automated tests** - Unit, integration, or E2E
2. **Command execution** - Run and capture output
3. **Manual verification** - Step-by-step check with evidence
4. **Reasoned proof** - Only when execution is impossible

### 3. Evidence Capture
For non-trivial changes, capture:
- Command output (success and relevant logs)
- Test results
- Screenshots (for UI changes)
- Before/after comparisons

Store evidence in: `.agent/evidence/[task-slug]-[YYYYMMDD]/`

### 4. Failure Handling
When verification fails:
1. Do NOT mark task as complete
2. Report specific failures with file:line
3. Propose fix or ask for guidance
4. Offer rollback if appropriate

## Verification Checklist

For code changes:
- [ ] Build passes
- [ ] Tests pass (existing + new)
- [ ] Acceptance criteria met
- [ ] No regressions introduced

For bug fixes:
- [ ] Bug is reproducible before fix
- [ ] Bug is not reproducible after fix
- [ ] Regression test added

For features:
- [ ] Feature works as specified
- [ ] Edge cases handled
- [ ] Error cases handled
- [ ] Documentation updated (if needed)

## Output Format

```markdown
## Verification Report

### Acceptance Criteria
- [x] [Criterion 1] - PASSED
- [ ] [Criterion 2] - FAILED: [reason]

### Evidence
| Check | Result | Evidence |
|-------|--------|----------|
| Build | ✅ PASS | `.agent/evidence/build.log` |
| Tests | ✅ PASS | `.agent/evidence/test.log` |
| Manual | ❌ FAIL | [Description of failure] |

### Status
- [ ] All criteria met
- [x] Has failures requiring attention

### Next Steps
[What needs to happen to resolve failures]
```

## Enforcement
No task is complete until verification passes. This rule is NON-NEGOTIABLE.
