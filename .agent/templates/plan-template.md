# Implementation Plan: [Task Name]

**Date**: [YYYY-MM-DD]
**Status**: DRAFT / APPROVED / IN PROGRESS / COMPLETE

---

## Goal
[One sentence describing what success looks like]

## Assumptions
- [ASSUMED] [Assumption 1 - will proceed unless corrected]
- [ASSUMED] [Assumption 2]

## Files to Modify
- `path/to/file.ts` - [what changes and why]
- `path/to/another.ts` - [what changes and why]

## Files to Create
- `path/to/new/file.ts` - [purpose of this file]

## Implementation Steps

### Step 1: [Title]
- **File**: `path/to/file.ts`
- **Change**: [Specific modification to make]
- **Depends on**: None
- **Verify**: [How to confirm this step worked]

### Step 2: [Title]
- **File**: `path/to/file.ts`
- **Change**: [Specific modification to make]
- **Depends on**: Step 1
- **Verify**: [How to confirm this step worked]

### Step 3: [Title]
- **File**: `path/to/file.ts`
- **Change**: [Specific modification to make]
- **Depends on**: Step 2
- **Verify**: [How to confirm this step worked]

## Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [What could go wrong] | Low/Med/High | Low/Med/High | [How to prevent/handle] |
| [Another risk] | Low/Med/High | Low/Med/High | [How to prevent/handle] |

## Verification Strategy

| Check | Command | Expected Output |
|-------|---------|-----------------|
| Build passes | `npm run build` | Exit code 0 |
| Tests pass | `npm test` | All tests green |
| [Feature works] | `[manual step]` | [Expected behavior] |

## Rollback Plan
If verification fails:
1. Revert files: [list files]
2. Database: [rollback migration / N/A]
3. Cleanup: [any other cleanup needed]

## Questions for User
- [Any clarifications needed before proceeding?]

---

## Approval
- [ ] User approved this plan
- [ ] No critical risks without mitigation
- [ ] All assumptions confirmed or acknowledged
