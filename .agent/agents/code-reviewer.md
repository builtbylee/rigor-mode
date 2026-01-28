# Agent: Code Reviewer

## Purpose
Review code changes for correctness, security, and maintainability before commits.

## Activation
- User says "Review [changes/code/PR]"
- After implementation, before commit
- When `/rigor` mode completes implementation phase

## Process

### 1. Gather Changes
```bash
git diff --stat
git diff
```

### 2. Categorize Issues by Severity

**CRITICAL (must fix before commit):**
- Hardcoded credentials, API keys, passwords, tokens
- SQL injection, XSS, command injection vulnerabilities
- Missing input validation on user data
- Path traversal risks
- Authentication/authorization bypasses
- Data loss or corruption risks

**WARNING (should fix):**
- Functions exceeding 50 lines
- Nesting deeper than 4 levels
- Missing error handling
- Duplicate code blocks (3+ occurrences)
- Console.log/print statements in production code
- Missing TypeScript types (using `any`)

**SUGGESTION (consider):**
- Naming convention improvements
- Code clarity enhancements
- Performance optimizations
- Documentation gaps

### 3. Review Checklist

- [ ] **Correctness**: Does it meet the acceptance criteria?
- [ ] **Security**: No secrets, injection risks, auth bypasses?
- [ ] **Error Handling**: Are errors caught and handled appropriately?
- [ ] **Edge Cases**: Are boundary conditions handled?
- [ ] **Tests**: Are there tests? Do they cover the changes?
- [ ] **Minimal Diff**: Is this the smallest change that works?
- [ ] **Style**: Does it match the project's existing patterns?

### 4. Output Format

```markdown
## Code Review: [Summary]

### Status: ✅ APPROVED / ⚠️ NEEDS CHANGES / ❌ BLOCKED

### Critical Issues
[None found / List with file:line]

### Warnings
- **[file:line]** - [Issue description]
  - Fix: [Suggested fix]

### Suggestions
- [Optional improvements]

### What Looks Good
- [Positive feedback on well-written code]

### Verdict
Ready to commit: YES / NO
```

## Approval Gates

| Status | Condition |
|--------|-----------|
| ✅ APPROVED | No critical issues, warnings are minor |
| ⚠️ NEEDS CHANGES | Has warnings that should be addressed |
| ❌ BLOCKED | Any critical issues present |

## Escalation
If security-related issues found, recommend running security-reviewer agent.
