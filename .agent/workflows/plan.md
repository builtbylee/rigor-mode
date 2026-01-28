# Workflow: Plan

## Purpose
Turn an ambiguous request into an executable plan with clear acceptance criteria, risk assessment, and verification strategy.

## When to Use
- Any task affecting 2+ files
- Non-trivial features or changes
- Architectural decisions
- When explicitly requested
- Always in `/rigor full` or `/rigor max` mode

## Inputs
- **Goal**: What success looks like
- **Constraints**: Time, risk tolerance, must-not-do
- **Environment**: Repo, language, runtime, existing patterns

## Process

### 1. Requirements Analysis
- Restate the goal in one sentence
- List explicit requirements from user
- List inferred requirements (mark as **[ASSUMED]**)
- Ask clarifying questions if ambiguous — do NOT guess

### 2. Codebase Review
- Identify affected files (list exact paths)
- Check for existing patterns to follow
- Identify dependencies between changes
- Flag potential conflicts

### 3. Risk Assessment

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk 1] | Low/Med/High | Low/Med/High | [Prevention] |
| [Risk 2] | Low/Med/High | Low/Med/High | [Prevention] |

### 4. Implementation Steps

For each step:
```
#### Step N: [Title]
- **File**: `path/to/file.ext`
- **Change**: [Specific modification]
- **Depends on**: Step X (or "None")
- **Verify**: [Command or check to confirm]
```

### 5. Verification Strategy

| Check | Command | Expected Output |
|-------|---------|-----------------|
| Build passes | `[build command]` | Exit code 0 |
| Tests pass | `[test command]` | All green |
| [Feature] | `[command/manual]` | [Expected result] |

### 6. Rollback Plan
If verification fails:
- [ ] Files to revert: [list]
- [ ] Database rollback: [migration or N/A]
- [ ] Cleanup: [any other steps]

## Output Format

```markdown
## Implementation Plan: [Task Name]

### Goal
[One sentence]

### Assumptions
- [ASSUMED] [Assumption 1]
- [ASSUMED] [Assumption 2]

### Files to Modify
- `path/to/file.ts` - [what changes]

### Files to Create
- `path/to/new.ts` - [purpose]

### Steps
[Use step format above]

### Risks
[Use risk table above]

### Verification
[Use verification table above]

### Rollback
[Rollback steps]

### Questions (if any)
- [Question needing answer before proceeding]
```

## Output Location
Save plan to: `.agent/plans/[task-slug]-[YYYYMMDD].md`

## Approval Gates
Before proceeding:
- [ ] User approved plan
- [ ] No CRITICAL risks without mitigation
- [ ] All [ASSUMED] items confirmed or acknowledged
- [ ] Verification strategy is testable

## Handoff
After approval:
1. Reference the plan file in subsequent work
2. Proceed to `implement` workflow
3. Complete with `verify` workflow
