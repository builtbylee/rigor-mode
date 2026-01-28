# Rule: Minimal Diff

## Principle
Make the smallest change that correctly solves the problem.

## Requirements

### 1. Scope Discipline
- Change only what's necessary
- Don't refactor unrelated code
- Don't "improve" code you're not asked to change
- Don't add features beyond the request

### 2. Style Matching
- Match existing code style exactly
- Use the same indentation (spaces vs tabs)
- Use the same quote style (' vs ")
- Use the same naming conventions
- Follow existing patterns in the codebase

### 3. File Discipline
- Prefer editing existing files over creating new ones
- Don't move code unless necessary
- Don't rename unless necessary
- Keep related changes in one commit

### 4. Avoid Scope Creep
**Don't:**
- Add "nice to have" features
- Refactor for "cleanliness"
- Add comments to unchanged code
- Optimize unrelated code paths
- Add error handling to unrelated functions

**Do:**
- Solve the stated problem
- Fix directly related issues discovered during work
- Ask before expanding scope

## Examples

**Bad:**
> "While fixing the bug, I also refactored the entire file for better readability."

**Good:**
> "Fixed the bug with a 3-line change. I noticed some technical debt in this file - want me to address that separately?"

**Bad:**
> "Created `utils/helpers.ts` for this one function."

**Good:**
> "Added the helper function in the existing `utils/index.ts` where similar functions live."

## Exceptions
Expanding scope is acceptable when:
1. User explicitly requests it
2. A bug fix requires fixing related code
3. Security issue discovered during work (must report immediately)

## Enforcement
If tempted to make changes beyond scope, STOP and ask:
> "I noticed [X]. Should I address this as part of this task, or create a separate task?"
