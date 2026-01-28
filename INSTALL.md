# Rigor Mode Installation

A structured framework for AI-assisted development. Works with Claude Code, Cursor, Windsurf, and other AI coding assistants.

## Quick Install

### Step 1: Clone the repo

```bash
git clone https://github.com/builtbylee/rigor-mode.git ~/rigor-mode
```

### Step 2: Link to your project

```bash
cd /path/to/your/project
ln -s ~/rigor-mode/.agent .agent
```

### Step 3: Configure User Rules (Optional but Recommended)

Copy the contents of `USER_RULES.md` into your AI assistant's global settings:

| Assistant | Where to paste |
|-----------|----------------|
| Claude Code | Settings → User Rules |
| Cursor | Settings → Rules for AI |
| Windsurf | Settings → AI Rules |
| Other | Look for "system prompt" or "custom instructions" |

### Step 4: Activate

Start any chat with:

```
/rigor
```

---

## Installation Options

### Option A: Symlink (Recommended)

Best for: Using the same rigor config across multiple projects, with automatic updates.

```bash
# Clone once
git clone https://github.com/builtbylee/rigor-mode.git ~/rigor-mode

# Link in each project
cd /path/to/project
ln -s ~/rigor-mode/.agent .agent
```

**To update:** `cd ~/rigor-mode && git pull`

### Option B: Copy

Best for: Project-specific customization.

```bash
# Clone
git clone https://github.com/builtbylee/rigor-mode.git ~/rigor-mode

# Copy to project
cp -r ~/rigor-mode/.agent /path/to/project/.agent
```

**Note:** You won't get automatic updates, but you can customize freely.

### Option C: Direct clone into project

Best for: One-off use.

```bash
cd /path/to/project
git clone https://github.com/builtbylee/rigor-mode.git .rigor-mode
ln -s .rigor-mode/.agent .agent
```

---

## Directory Structure After Install

Your project should look like:

```
your-project/
├── .agent/              # ← Symlink or copy
│   ├── agents/
│   ├── rules/
│   ├── workflows/
│   ├── skills/
│   └── templates/
├── src/
├── package.json
└── ...
```

---

## Setting Up Project Context

For best results, create a project context file:

```bash
cp .agent/templates/context.md .agent/context.md
```

Then edit `.agent/context.md` with your project's details:
- Tech stack
- Key directories
- Common commands
- Coding conventions

---

## Verify Installation

1. Start a new chat with your AI assistant
2. Type `/rigor status`
3. The AI should acknowledge rigor mode

If it doesn't recognize the command, paste this bootstrap prompt:

```
Enable Rigor Mode.

- Follow the rules in .agent/rules/
- Use workflows from .agent/workflows/ when tasks match
- Use agents from .agent/agents/ for specialized work
- For non-trivial tasks: start with the plan workflow
- After changes: run the verify workflow

Task: [your task here]
```

---

## Updating

If you used Option A (symlink):

```bash
cd ~/rigor-mode
git pull
```

All linked projects will automatically use the updated version.

---

## Uninstalling

```bash
# Remove from a project
rm /path/to/project/.agent

# Remove completely
rm -rf ~/rigor-mode
```

---

## Troubleshooting

**"The AI doesn't follow the workflows"**
- Check the symlink exists: `ls -la .agent`
- Try the bootstrap prompt above
- Ensure User Rules are configured

**"Symlink isn't working"**
- Use absolute path: `ln -s /Users/you/rigor-mode/.agent .agent`
- On Windows, use mklink or copy instead

**"I want to customize just one workflow"**
- Use Option B (copy) for that project
- Or keep symlink but add project-specific overrides

---

## What's Included

| Component | Count | Purpose |
|-----------|-------|---------|
| Agents | 5 | Specialized personas (planner, debugger, etc.) |
| Rules | 4 | Behavioral guardrails |
| Workflows | 7 | Step-by-step processes |
| Skills | 6 | Background capabilities |
| Templates | 2 | Reusable document structures |

See [README.md](README.md) for full documentation.
