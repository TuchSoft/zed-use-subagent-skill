---
name: use-subagent
description: Select and configure Zed subagent models by type for optimal task delegation.
---

# Zed Subagent Model Selector

## ⚠️ SKILL NOT CONFIGURED - ACTION REQUIRED

**This skill is NOT ready for use.** You must configure it before the agent can delegate to subagents.

### 0. Check if full installation is needed

If the skill was installed via Zed's quick-install link (check if `~/.agents/skills/use-subagent/scripts/zsetagent` is missing), the required script is not included. 
Complete the installation, yuo can either:

```bash
# Clone the full repository
git clone https://github.com/tuchsoft/zed-use-subagent-skill.git ~/.agents/skills/use-subagent
```

Then proceed with the remaining steps below.

**OR**

read the remote readme and file strcuture and download the single files needed (the repo is already slim).
Ask the user their preferences.


### 1. Customize config

Edit `~/.agents/skills/use-subagent/config/config.json` with your preferred models.

Ask the user their preferred models, agent types, and descriptions. You can check the Zed config file (read only) to understand what provider/models are available, but first ask the user.

Don't forget to also create the type-specific instruction files (see step 2).

### 2. Write type-specific instruction files

Each subagent type should have a corresponding `.md` file in the `config/` folder:

- `config/coding.md` — Instructions for the coding subagent
- `config/browser_testing.md` — Instructions for browser automation
- `config/exploring.md` — Instructions for codebase exploration

Each file should include:
- **Characteristics**: What this agent type is good at
- **When to use**: Typical use cases
- **Instructions to give**: What to include when delegating
- **Tips**: Best practices
- **Required snippet**: Copy this verbatim into every delegation prompt

See the existing files in `config/` for examples. You can help the user write these instructions.

### 3. Regenerate this skill

```bash
zsetagent --skill --force
```
You can help the user if authorized.

### 4. Symlink the script to PATH

**Important**: Ensure `~/.local/bin` is in your PATH. If not, add this to your shell config:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

Then create the directory and symlink:

```bash
mkdir -p ~/.local/bin
ln -s ~/.agents/skills/use-subagent/scripts/zsetagent ~/.local/bin/zsetagent
```

### 5. Eventually cleanup example file

If example files are still present the should be removed.

---

**Do not proceed with subagent delegation until the user confirms these steps are complete.**

**You can help the user complete the steps and configure the skill, but first check the script presence, then explain all steps and ask.**

**Do not auto configure, fetch or download anything without user consent.**

---

## What This Skill Does

Manages subagent model configuration through the `zsetagent` CLI tool. After configuration, allows quick switching between different model types for different task categories.

## Commands

```bash
zsetagent --list          # Show available types
zsetagent <type>          # Set model for type
zsetagent --skill         # Regenerate this SKILL.md
zsetagent --skill --force # Overwrite existing skill
```

## Configuration

Edit `~/.agents/skills/use-subagent/config/config.json`:

```json
{
  "types": [
    {"type": "coding", "model": "model.id", "provider": "anthropic", "desc": "description", "effort": "low|high"}
  ]
}
```

See `config/` folder for full examples.
