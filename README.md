# Rigor Mode

A structured framework for AI-assisted development that enforces engineering discipline: no guessing, no coding without a plan, no "done" without verification.

---

## What is Rigor Mode?

Rigor Mode transforms how AI assists with your code. Instead of jumping straight to implementation, it follows a disciplined process:

```
┌─────────────────────────────────────────────────────────┐
│                    RIGOR MODE FLOW                      │
├─────────────────────────────────────────────────────────┤
│                                                         │
│   📋 PLAN          →    🔨 IMPLEMENT    →    ✅ VERIFY   │
│                                                         │
│   • List files        • Minimal changes     • Tests pass │
│   • Identify risks    • Match style         • Build works│
│   • Define success    • One step at time    • Evidence   │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

**Without Rigor Mode:**
> "Sure, I'll add that feature" → *writes 500 lines* → "Done!"
> *(May or may not work. May have broken other things. Who knows?)*

**With Rigor Mode:**
> "I'll plan this first" → *identifies 3 files, 2 risks* → *implements step by step* → *runs tests* → "Verified working. Here's the evidence."

---

## Quick Start

### 1. Activate Rigor Mode

At the start of any chat, type:

```
/rigor
```

That's it. The AI now follows the rigor framework.

### 2. Choose Your Level

| Command | Level | Best For |
|---------|-------|----------|
| `/rigor light` | Minimal | Quick fixes, exploration |
| `/rigor` | Standard | Regular feature work |
| `/rigor full` | Comprehensive | Important features, production |
| `/rigor max` | Maximum | Security-sensitive, architectural |

### 3. Give Your Task

```
/rigor full

Add user authentication with OAuth
```

The AI will now:
1. Create a plan before coding
2. Identify files to change and risks
3. Ask for approval before implementing
4. Verify everything works when done
5. Capture evidence of success

---

## What's Included

### 📁 Directory Structure

```
.agent/
├── agents/           # Specialized AI personas
│   ├── planner.md        # Plans complex features
│   ├── code-reviewer.md  # Reviews code quality
│   ├── security-reviewer.md  # Checks for vulnerabilities
│   ├── architect.md      # Designs system architecture
│   └── debugger.md       # Scientific troubleshooting
│
├── rules/            # Behavioral guardrails
│   ├── truthfulness.md   # No guessing, verify facts
│   ├── safety.md         # Confirm destructive actions
│   ├── verification.md   # Prove changes work
│   └── minimal-diff.md   # Smallest correct change
│
├── workflows/        # Step-by-step processes
│   ├── plan.md           # Create implementation plans
│   ├── implement.md      # Execute plans
│   ├── verify.md         # Confirm success
│   ├── review.md         # Code review process
│   ├── debug.md          # Bug investigation
│   ├── research.md       # Learn before building
│   └── checkpoint.md     # Save progress
│
├── templates/        # Reusable structures
│   ├── context.md        # Project context template
│   └── plan-template.md  # Plan document structure
│
├── plans/            # Saved implementation plans
└── evidence/         # Verification logs & screenshots
```

---

## Agents

Agents are specialized personas that activate for specific types of work.

### 🗺️ Planner
**Activates:** Complex features, 3+ files, architectural decisions

Creates structured implementation plans with:
- Files to modify/create
- Step-by-step changes
- Risk assessment
- Verification strategy
- Rollback plan

### 👀 Code Reviewer
**Activates:** "Review this", PR analysis, code quality checks

Provides structured reviews with severity levels:
- 🔴 **CRITICAL** — Must fix before merge
- 🟡 **WARNING** — Should fix, potential issues
- 🔵 **SUGGESTION** — Nice to have improvements

### 🔒 Security Reviewer
**Activates:** Auth, payments, APIs, data handling, or files matching `**/auth/**`, `**/api/**`

Checks for:
- OWASP Top 10 vulnerabilities
- Injection risks (SQL, XSS, command)
- Authentication/authorization flaws
- Sensitive data exposure
- Security misconfigurations

### 🏗️ Architect
**Activates:** New patterns, technology choices, cross-cutting concerns

Provides:
- Trade-off analysis
- Architectural options with pros/cons
- Scalability considerations
- Integration patterns
- Decision documentation

### 🔍 Debugger
**Activates:** "debug", "error", "not working", "why is", "broken", "bug"

Follows scientific method:
1. **Observe** — Gather all evidence
2. **Hypothesize** — Form ranked theories
3. **Test** — Prove/disprove systematically
4. **Isolate** — Binary search to root cause
5. **Fix** — Minimal change at root cause
6. **Verify** — Prove fix works
7. **Document** — Prevent recurrence

---

## Commands Reference

### Rigor Levels

```
/rigor              Standard mode (default)
/rigor light        Minimal overhead
/rigor full         Full documentation + evidence
/rigor max          Full + security + architecture review
/rigor off          Disable rigor mode
/rigor status       Show current level
```

### What Each Level Enforces

```
                    light    standard    full    max
                    ─────    ────────    ────    ───
Plan before code      ○         ●         ●       ●
Verify after code     ●         ●         ●       ●
Evidence capture      ○         ○         ●       ●
Security review       ○         ○         ○       ●
Arch review           ○         ○         ○       ●
Rollback plan         ○         ○         ●       ●

● = Required   ○ = Optional
```

### Workflow Triggers

These keywords activate specific workflows:

| Say... | Activates |
|--------|-----------|
| "Plan a user dashboard" | `plan` workflow |
| "Implement the auth system" | `implement` workflow |
| "Verify the checkout flow" | `verify` workflow |
| "Review this PR" | `review` workflow + code-reviewer agent |
| "Debug why tests are failing" | `debug` workflow + debugger agent |
| "Research how GraphQL works" | `research` workflow |
| "Checkpoint" | `checkpoint` workflow |

---

## Example Session

```
User: /rigor full

      Add a password reset feature

AI:   ## Approach
      I'll plan the password reset feature before implementing.

      ## Implementation Plan: Password Reset

      ### Goal
      Users can reset forgotten passwords via email link.

      ### Assumptions
      - [ASSUMED] Using existing email service
      - [ASSUMED] Tokens expire after 1 hour

      ### Files to Modify
      - `src/api/auth/reset.ts` - New endpoint
      - `src/services/email.ts` - Add reset email template
      - `src/db/schema.ts` - Add reset_tokens table

      ### Files to Create
      - `src/api/auth/reset-confirm.ts` - Token verification endpoint

      ### Risks
      | Risk | Likelihood | Mitigation |
      |------|------------|------------|
      | Token enumeration | Medium | Rate limiting + generic responses |
      | Email timing attack | Low | Constant-time token comparison |

      ### Verification
      - [ ] Can request reset for existing user
      - [ ] Token expires after 1 hour
      - [ ] Invalid tokens rejected
      - [ ] Password actually changes

      ---

      Should I proceed with this plan?

User: Yes, implement it

AI:   [Implements step by step, running verifications]

      ## Verification Report

      ### Status: ✅ VERIFIED

      | Check | Result |
      |-------|--------|
      | Reset email sends | ✅ PASS |
      | Token expires | ✅ PASS |
      | Invalid token rejected | ✅ PASS |
      | Password changes | ✅ PASS |
      | Build passes | ✅ PASS |
      | Tests pass | ✅ PASS |

      ### Evidence
      - Test output: `.agent/evidence/password-reset-20240115/test.log`
      - Build log: `.agent/evidence/password-reset-20240115/build.log`

      Ready to commit.
```

---

## Installation

### Option 1: Symlink (Recommended)

Keeps your projects in sync with the latest rigor pack:

```bash
cd /path/to/your/project
ln -s "/Users/lee/Downloads/antigravity-rigor-pack/.agent" .agent
```

### Option 2: Copy

For project-specific customization:

```bash
cd /path/to/your/project
cp -r "/Users/lee/Downloads/antigravity-rigor-pack/.agent" .agent
```

### Setup Project Context

After installation, create your project context:

```bash
cp .agent/templates/context.md .agent/context.md
# Edit with your project's details
```

---

## Core Principles

### 1. Truthfulness
- Never present guesses as facts
- Mark assumptions with `[ASSUMED]`
- Verify before claiming something works
- Say "I don't know" when uncertain

### 2. Plan First
- No coding without understanding scope
- Identify files, risks, and success criteria
- Get approval before major changes
- Save plans for reference

### 3. Verify Always
- Define acceptance criteria upfront
- Test after implementing
- Capture evidence in full/max modes
- Don't mark done until proven

### 4. Minimal Diff
- Smallest change that solves the problem
- Match existing code style
- Don't refactor unrequested code
- Prefer editing over creating files

### 5. Safety
- Confirm destructive actions explicitly
- Never expose secrets in code/logs
- Check for security issues automatically
- Create rollback plans for risky changes

---

## When to Use Each Level

| Scenario | Recommended Level |
|----------|-------------------|
| Quick typo fix | `/rigor light` |
| Bug fix | `/rigor` |
| New feature | `/rigor` |
| Production hotfix | `/rigor full` |
| Payment integration | `/rigor max` |
| Auth system changes | `/rigor max` |
| Database migrations | `/rigor full` |
| Refactoring | `/rigor` |
| Security-sensitive work | `/rigor max` |
| Learning/exploring | `/rigor light` |

---

## Troubleshooting

**"The AI isn't following the process"**
- Did you say `/rigor` at the start?
- Is `.agent` folder present? Check with `ls -la .agent`

**"I want to customize for one project"**
- Use Option 2 (copy) instead of symlink
- Edit files in the local `.agent` folder

**"Evidence isn't being captured"**
- Check you're in `/rigor full` or `/rigor max`
- Ensure `.agent/evidence/` directory exists

**"Agent didn't activate"**
- Agents auto-trigger on keywords
- Manually invoke: "Use the debugger agent to investigate this"

---

## Files Reference

| File | Purpose |
|------|---------|
| `README.md` | This guide |
| `USER_RULES.md` | Rules to paste into AI settings |
| `HOW_TO_GUIDE.md` | Detailed usage documentation |
| `INSTALL.md` | Installation instructions |
| `BOOTSTRAP_PROMPT.md` | Fallback activation prompt |

---

## Philosophy

Rigor Mode is built on one insight: **AI coding assistants are eager to help, but eagerness without discipline leads to bugs, rework, and frustration.**

By adding structure—plan, implement, verify—we get:
- **Fewer bugs**: Problems caught before code is written
- **Less rework**: Scope agreed upfront
- **Better quality**: Verification proves it works
- **More trust**: Evidence over promises

The goal isn't to slow down. It's to go fast *correctly*.

---

*Built for [Antigravity](https://antigravity.dev) projects.*
