# Antigravity Rigor Pack

This is a portable, cross-project rigor setup for Antigravity.

It is designed to give you “everything-claude-code”-level discipline using:

- Global **User Rules** (always-on)
- Reusable **Skills** (domain playbooks)
- Reusable **Workflows** (repeatable task sequences)
- Optional **Agent role cards** (planner/reviewer/etc.)

This pack is meant to be copied to any machine.

## Install (Global)

### 1) User Rules (Global)

1. Open Antigravity settings
2. Find **User Rules** (global, applies to every request)
3. Paste the contents of `USER_RULES.md`

### 2) Skills + Workflows

Antigravity commonly looks for:

- `.agent/skills/**/SKILL.md`
- `.agent/workflows/*.md`

Because Antigravity installations vary, choose one of these options:

#### Option A (Recommended): One global pack + per-project symlink

1. Place this folder somewhere stable, e.g.
   - macOS/Linux: `~/antigravity-rigor-pack/`
   - Windows: `%USERPROFILE%\\antigravity-rigor-pack\\`

2. For each project you work on, create a `.agent` link that points to the pack’s `.agent` directory.

- macOS/Linux (symlink):
  - From the project root: create `.agent -> /absolute/path/to/antigravity-rigor-pack/.agent`

If you don’t want symlinks, use Option B.

#### Option B: Copy into each project

Copy the contents of this pack’s `.agent/` folder into each project root.

## Usage

### Minimal bootstrap prompt

Start any new Antigravity chat with:

- “Enable Rigor Pack. Follow my User Rules. Use workflows when helpful. Start with the `plan` workflow unless the task is trivial.”

### Common workflows

- `plan.md`: planning + risks + acceptance criteria
- `implement.md`: careful implementation protocol
- `debug.md`: hypothesis-driven debugging
- `review.md`: code review checklist
- `verify.md`: verification loop
- `checkpoint.md`: save state / summarize

## Notes

- This pack intentionally avoids tool hooks that execute commands automatically, because Antigravity’s automation model varies.
- If Antigravity supports workflow hooks like `// turbo`, you can add them later (after you trust the workflow).
