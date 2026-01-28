# Antigravity Rigor Pack: User Guide

This guide explains how to use your global configuration effectively across all projects.

---

## 1. Core Concept

Your **Rigor Pack** forces the AI to follow a strict engineering process:
1. **Truthfulness**: No guessing. Mark assumptions. Verify before claiming.
2. **Plan-First**: No coding without a plan for non-trivial work.
3. **Verification**: No "done" without evidence it works.

It achieves this through:
- **Global User Rules**: (Configured in Settings) Persistent behavioral guardrails.
- **Rigor Levels**: Adjustable discipline from light to maximum.
- **Workflows**: (In `.agent/workflows`) Structured processes for common tasks.
- **Agents**: (In `.agent/agents`) Specialized personas for specific work types.
- **Rules**: (In `.agent/rules`) Modular behavioral constraints.
- **Templates**: (In `.agent/templates`) Reusable document structures.

---

## 2. Rigor Levels

Choose the right level of process overhead for your task:

| Command | When to Use |
|---------|-------------|
| `/rigor light` | Quick fixes, simple edits, exploration |
| `/rigor` | **Default** - Feature work, bug fixes |
| `/rigor full` | Important features, production changes |
| `/rigor max` | Security-sensitive, architectural changes |

### What Each Level Does

```
Light     Standard    Full        Max
  │          │          │          │
  ▼          ▼          ▼          ▼
Verify    + Plan     + Evidence  + Security Review
only       (2+ files)  capture     + Arch Review
                                   + Rollback Plan
```

---

## 3. Quick Start

### Starting a New Chat

**Option A: The Magic Word (Recommended)**
```
/rigor
```

**Option B: With a specific level**
```
/rigor full
```

**Option C: Full Bootstrap (Fallback)**
```markdown
Enable my Rigor Pack at [level].

- Follow my global User Rules.
- Use `.agent/workflows` when a task matches.
- For non-trivial work: start with the `plan` workflow.
- Before making changes: confirm assumptions and risks.
- After changes: run the `verify` workflow.

Task:
<YOUR TASK HERE>
```

---

## 4. Workflows

Workflows are structured processes the AI follows. They live in `.agent/workflows/`.

| Workflow | Trigger Keywords | Purpose |
|----------|------------------|---------|
| **plan** | "Plan...", "Design..." | Create implementation plan with risks, steps, verification |
| **implement** | "Implement...", "Build..." | Execute an approved plan |
| **verify** | "Verify...", "Check..." | Confirm changes work with evidence |
| **review** | "Review..." | Code quality and correctness check |
| **debug** | "Debug...", "Why is..." | Root cause analysis |
| **research** | "Research...", "Explore..." | Learn before planning |
| **checkpoint** | "Checkpoint" | Save progress, create commit message |

**Example usages:**
```
"Plan a user authentication system"
"Debug why the API is returning 500 errors"
"Verify the checkout flow changes"
"Review the payment processing module"
```

---

## 5. Specialized Agents

Agents are specialized personas for specific types of work. They live in `.agent/agents/`.

| Agent | Auto-Triggers On | Purpose |
|-------|------------------|---------|
| **planner** | Complex features, 3+ files | Structured planning with risks and verification |
| **code-reviewer** | "Review...", PR analysis | Quality assessment with severity levels |
| **security-reviewer** | Auth, payments, data, APIs | OWASP-aware vulnerability scanning |
| **architect** | New patterns, technology choices | Trade-off analysis and system design |
| **debugger** | "debug", "error", "not working", "why" | Scientific root cause analysis |

### Auto-Trigger Examples

The **security-reviewer** automatically activates when changes touch:
- `**/auth/**`, `**/security/**`
- `**/api/**`, `**/payments/**`
- Files with `password`, `token`, `secret` in the name

### Manually Invoking an Agent
```
"Use the security-reviewer agent to check the login flow"
"Switch to architect mode for this database redesign"
```

---

## 6. Evidence Capture

In `/rigor full` and `/rigor max` modes, evidence is captured automatically.

### Evidence Directory Structure
```
.agent/evidence/
└── [task-slug]-[YYYYMMDD]/
    ├── build.log      # Build output
    ├── test.log       # Test results
    ├── output.log     # Command outputs
    └── screenshots/   # Visual evidence
```

### What Gets Captured
- Build logs (pass/fail, warnings)
- Test output (pass/fail, coverage)
- Command output from verification steps
- Before/after screenshots for UI changes

---

## 7. Plans Directory

Plans are saved for reference and approval tracking.

### Plan Location
```
.agent/plans/
└── [task-slug]-[YYYYMMDD].md
```

### Plan Template
Plans follow the structure in `.agent/templates/plan-template.md`:
- Goal
- Assumptions (marked with [ASSUMED])
- Files to modify/create
- Implementation steps with verification
- Risks and mitigations
- Rollback plan

---

## 8. Rules

Modular behavioral rules live in `.agent/rules/`. They're always active.

| Rule | Enforces |
|------|----------|
| **truthfulness** | No guessing, mark assumptions, verify before claiming |
| **safety** | Confirm destructive actions, protect secrets |
| **verification** | Capture evidence, handle failures properly |
| **minimal-diff** | Smallest change, match existing style |

---

## 9. Templates

Reusable document structures in `.agent/templates/`:

| Template | Use For |
|----------|---------|
| `context.md` | Project setup - copy to `.agent/context.md` in new projects |
| `plan-template.md` | Reference structure for implementation plans |

### Setting Up a New Project

1. **Clone rigor-mode** (if you haven't already):
   ```bash
   git clone https://github.com/builtbylee/rigor-mode.git ~/rigor-mode
   ```

2. **Symlink to your project**:
   ```bash
   cd /path/to/your/project
   ln -s ~/rigor-mode/.agent .agent
   ```

3. **Create project context**:
   ```bash
   cp .agent/templates/context.md .agent/context.md
   # Edit with your project's details
   ```

---

## 10. Skills

Skills are background capabilities. They live in `.agent/skills/`.

| Skill | Purpose |
|-------|---------|
| `rigor-core` | Foundation for plan/execute/verify loop |
| `model-routing` | Opus (thinking) vs Gemini (coding) decisions |
| `code-review` | Code quality analysis |
| `security-review` | Vulnerability identification |

---

## 11. Directory Structure

```
.agent/
├── agents/           # Specialized personas
│   ├── planner.md
│   ├── code-reviewer.md
│   ├── security-reviewer.md
│   ├── architect.md
│   └── debugger.md
├── rules/            # Behavioral constraints
│   ├── truthfulness.md
│   ├── safety.md
│   ├── verification.md
│   └── minimal-diff.md
├── workflows/        # Process definitions
│   ├── plan.md
│   ├── implement.md
│   ├── verify.md
│   ├── review.md
│   ├── debug.md
│   ├── research.md
│   └── checkpoint.md
├── skills/           # Background capabilities
│   ├── rigor-core.md
│   ├── model-routing.md
│   ├── code-review.md
│   └── security-review.md
├── templates/        # Reusable structures
│   ├── context.md
│   └── plan-template.md
├── plans/            # Saved implementation plans
├── evidence/         # Captured verification evidence
└── context.md        # Project-specific context (you create this)
```

---

## 12. Troubleshooting

### "The agent is ignoring my workflows"
- Did you say `/rigor` at the start of the chat?
- Is the `.agent` symlink intact? Check with `ls -la .agent`

### "I want different rules for this project"
1. Delete the symlink: `rm .agent`
2. Copy the folder: `cp -r ~/rigor-mode/.agent .agent`
3. Edit locally (note: you lose automatic global updates)

### "Evidence isn't being captured"
- Are you in `/rigor full` or `/rigor max` mode?
- Check that `.agent/evidence/` directory exists

### "Security review didn't trigger"
- Security review auto-triggers in `/rigor max` mode
- Or when changes touch auth/security/payment files
- Manually invoke: "Use security-reviewer agent to check this"

### "Plans aren't being saved"
- Ensure `.agent/plans/` directory exists
- Plans are saved in `/rigor` and higher modes

---

## 13. Quick Reference

```
RIGOR LEVELS
/rigor light    → Verify only
/rigor          → Standard (plan + verify)
/rigor full     → Full (+ evidence capture)
/rigor max      → Maximum (+ security + architecture)
/rigor off      → Disable
/rigor status   → Show current level

AGENTS
planner           → Complex features, 3+ files
code-reviewer     → PR reviews, quality checks
security-reviewer → Auth, payments, APIs
architect         → New patterns, technology choices
debugger          → Root cause analysis, troubleshooting

KEY DIRECTORIES
.agent/plans/     → Saved implementation plans
.agent/evidence/  → Captured verification evidence
.agent/context.md → Your project context (create this)
```
