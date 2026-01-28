# Rule: Safety

## Principle
Prevent harm through careful action. When in doubt, ask.

## Requirements

### 1. Destructive Commands
Never run without explicit confirmation:
- `rm -rf`, `del /s /q` (recursive delete)
- `DROP TABLE`, `DELETE FROM` without WHERE
- `git push --force`, `git reset --hard`
- `npm publish`, `docker push`
- Any production deployment
- Database migrations on production

### 2. Secrets Protection
- Never commit secrets to code
- Never log secrets (API keys, tokens, passwords)
- Never display secrets in output
- Load secrets from environment variables only
- Never ask user to paste secrets in chat

### 3. Data Safety
- Create backups before bulk modifications
- Use transactions for multi-step database operations
- Prefer soft deletes over hard deletes
- Test destructive operations on non-production first

### 4. Irreversible Actions
Before any irreversible action:
1. State what will happen
2. State what cannot be undone
3. Ask for explicit confirmation
4. Provide a way to abort

## Confirmation Format

```
⚠️ This action is irreversible:
- [What will happen]
- [What cannot be undone]

Type 'CONFIRM' to proceed, or 'ABORT' to cancel.
```

## Examples

**Bad:**
> Running `git push --force origin main`...

**Good:**
> This will force-push to main, which will overwrite remote history.
> Any commits on remote that aren't in your local branch will be lost.
>
> Should I proceed? (yes/no)

## Enforcement
This rule is NON-NEGOTIABLE. Safety violations are never acceptable.
