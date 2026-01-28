# Workflow: Verify

## Purpose
Close the loop: prove the change works with evidence.

## When to Use
- After any implementation
- Before declaring a task complete
- When user requests verification
- Always in `/rigor` mode before completion

## Process

### 1. Load Acceptance Criteria
- Reference the approved plan (if exists)
- Or state the acceptance criteria now
- Criteria must be testable and specific

### 2. Execute Verification

For each criterion:
```
#### Check: [Name]
- **Method**: [Command / Manual step]
- **Expected**: [Expected output]
- **Actual**: [Actual output]
- **Status**: ✅ PASS / ❌ FAIL
```

### 3. Evidence Collection

| Evidence Type | Location |
|---------------|----------|
| Build log | `.agent/evidence/[task]/build.log` |
| Test output | `.agent/evidence/[task]/test.log` |
| Screenshots | `.agent/evidence/[task]/` |
| Command output | `.agent/evidence/[task]/output.log` |

### 4. Security Check (if applicable)
If changes touched sensitive areas:
- [ ] Run security-reviewer agent
- [ ] Document security review outcome
- [ ] Address any security findings

### 5. Regression Check
- [ ] Existing tests still pass
- [ ] No new warnings introduced
- [ ] Build size/performance not degraded significantly

## Output Format

```markdown
## Verification Report: [Task Name]

### Status: ✅ VERIFIED / ❌ FAILED / ⚠️ PARTIAL

### Acceptance Criteria
- [x] [Criterion 1] - PASSED
- [ ] [Criterion 2] - FAILED: [reason]

### Checks Performed

| Check | Method | Expected | Actual | Status |
|-------|--------|----------|--------|--------|
| Build | `npm run build` | Exit 0 | Exit 0 | ✅ |
| Tests | `npm test` | All pass | 2 failed | ❌ |
| Feature | Manual test | [expected] | [actual] | ✅ |

### Evidence
- Build log: `.agent/evidence/[task]/build.log`
- Test log: `.agent/evidence/[task]/test.log`

### Issues Found
- [None / List with file:line and description]

### Recommendation
- [x] Ready to commit
- [ ] Needs fixes before commit
- [ ] Recommend rollback
```

## Failure Handling

When verification fails:

### 1. Do NOT mark task complete
The task remains open until all criteria pass.

### 2. Diagnose the failure
- Identify which specific check failed
- Determine if it's a code issue or test issue
- Check if the failure is related to the changes

### 3. Report clearly
```markdown
## Verification FAILED

### Failed Checks
- [Check name]: [What failed and why]

### Root Cause
[Analysis of why it failed]

### Recommended Action
- [ ] Fix: [Specific fix to apply]
- [ ] Investigate: [What needs more analysis]
- [ ] Rollback: [If changes should be reverted]

### Questions for User
- [Any decisions needed]
```

### 4. Offer options
- Propose a fix and re-verify
- Ask for guidance
- Offer to rollback changes

## Evidence Directory Structure
```
.agent/evidence/
└── [task-slug]-[YYYYMMDD]/
    ├── build.log
    ├── test.log
    ├── output.log
    └── screenshots/
```

## Completion
Only after ALL criteria pass:
1. Summarize what was verified
2. Link to evidence
3. Mark task complete
4. Recommend next steps (commit, deploy, etc.)
