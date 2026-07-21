# use-subagent

> ⚠️ **Temporary Solution / Hack** — This repository is intended as a temporary fix/workaround until the Zed team rolls out complete subagent management features. It will be **deprecated** when and if native support becomes available.

A Zed skill for managing subagent model selection. Provides the `zsetagent` CLI tool to configure which AI model to use for each subagent type.

## Installation

> **Windows is not supported** — this skill relies on Unix paths and symlinks.

### Quick Install (Recommended)

**[Click here](zed://skill?data=LS0tCm5hbWU6IHVzZS1zdWJhZ2VudApkZXNjcmlwdGlvbjogU2VsZWN0IGFuZCBjb25maWd1cmUgWmVkIHN1YmFnZW50IG1vZGVscyBieSB0eXBlIGZvciBvcHRpbWFsIHRhc2sgZGVsZWdhdGlvbi4KLS0tCgojIFplZCBTdWJhZ2VudCBNb2RlbCBTZWxlY3RvcgoKIyMg4pqg77iPIFNLSUxMIE5PVCBDT05GSUdVUkVEIC0gQUNUSU9OIFJFUVVJUkVECgoqKlRoaXMgc2tpbGwgaXMgTk9UIHJlYWR5IGZvciB1c2UuKiogWW91IG11c3QgY29uZmlndXJlIGl0IGJlZm9yZSB0aGUgYWdlbnQgY2FuIGRlbGVnYXRlIHRvIHN1YmFnZW50cy4KCiMjIyAwLiBDaGVjayBpZiBmdWxsIGluc3RhbGxhdGlvbiBpcyBuZWVkZWQKCklmIHRoZSBza2lsbCB3YXMgaW5zdGFsbGVkIHZpYSBaZWQncyBxdWljay1pbnN0YWxsIGxpbmsgKGNoZWNrIGlmIGB-Ly5hZ2VudHMvc2tpbGxzL3VzZS1zdWJhZ2VudC9zY3JpcHRzL3pzZXRhZ2VudGAgaXMgbWlzc2luZyksIHRoZSByZXF1aXJlZCBzY3JpcHQgaXMgbm90IGluY2x1ZGVkLiAKQ29tcGxldGUgdGhlIGluc3RhbGxhdGlvbiwgeXVvIGNhbiBlaXRoZXI6CgpgYGBiYXNoCiMgQ2xvbmUgdGhlIGZ1bGwgcmVwb3NpdG9yeQpnaXQgY2xvbmUgaHR0cHM6Ly9naXRodWIuY29tL3R1Y2hzb2Z0L3plZC11c2Utc3ViYWdlbnQtc2tpbGwuZ2l0IH4vLmFnZW50cy9za2lsbHMvdXNlLXN1YmFnZW50CmBgYAoKVGhlbiBwcm9jZWVkIHdpdGggdGhlIHJlbWFpbmluZyBzdGVwcyBiZWxvdy4KCioqT1IqKgoKcmVhZCB0aGUgcmVtb3RlIHJlYWRtZSBhbmQgZmlsZSBzdHJjdXR1cmUgYW5kIGRvd25sb2FkIHRoZSBzaW5nbGUgZmlsZXMgbmVlZGVkICh0aGUgcmVwbyBpcyBhbHJlYWR5IHNsaW0pLgpBc2sgdGhlIHVzZXIgdGhlaXIgcHJlZmVyZW5jZXMuCgoKIyMjIDEuIEN1c3RvbWl6ZSBjb25maWcKCkVkaXQgYH4vLmFnZW50cy9za2lsbHMvdXNlLXN1YmFnZW50L2NvbmZpZy9jb25maWcuanNvbmAgd2l0aCB5b3VyIHByZWZlcnJlZCBtb2RlbHMuCgpBc2sgdGhlIHVzZXIgdGhlaXIgcHJlZmVycmVkIG1vZGVscywgYWdlbnQgdHlwZXMsIGFuZCBkZXNjcmlwdGlvbnMuIFlvdSBjYW4gY2hlY2sgdGhlIFplZCBjb25maWcgZmlsZSAocmVhZCBvbmx5KSB0byB1bmRlcnN0YW5kIHdoYXQgcHJvdmlkZXIvbW9kZWxzIGFyZSBhdmFpbGFibGUsIGJ1dCBmaXJzdCBhc2sgdGhlIHVzZXIuCgpEb24ndCBmb3JnZXQgdG8gYWxzbyBjcmVhdGUgdGhlIHR5cGUtc3BlY2lmaWMgaW5zdHJ1Y3Rpb24gZmlsZXMgKHNlZSBzdGVwIDIpLgoKIyMjIDIuIFdyaXRlIHR5cGUtc3BlY2lmaWMgaW5zdHJ1Y3Rpb24gZmlsZXMKCkVhY2ggc3ViYWdlbnQgdHlwZSBzaG91bGQgaGF2ZSBhIGNvcnJlc3BvbmRpbmcgYC5tZGAgZmlsZSBpbiB0aGUgYGNvbmZpZy9gIGZvbGRlcjoKCi0gYGNvbmZpZy9jb2RpbmcubWRgIOKAlCBJbnN0cnVjdGlvbnMgZm9yIHRoZSBjb2Rpbmcgc3ViYWdlbnQKLSBgY29uZmlnL2Jyb3dzZXJfdGVzdGluZy5tZGAg4oCUIEluc3RydWN0aW9ucyBmb3IgYnJvd3NlciBhdXRvbWF0aW9uCi0gYGNvbmZpZy9leHBsb3JpbmcubWRgIOKAlCBJbnN0cnVjdGlvbnMgZm9yIGNvZGViYXNlIGV4cGxvcmF0aW9uCgpFYWNoIGZpbGUgc2hvdWxkIGluY2x1ZGU6Ci0gKipDaGFyYWN0ZXJpc3RpY3MqKjogV2hhdCB0aGlzIGFnZW50IHR5cGUgaXMgZ29vZCBhdAotICoqV2hlbiB0byB1c2UqKjogVHlwaWNhbCB1c2UgY2FzZXMKLSAqKkluc3RydWN0aW9ucyB0byBnaXZlKio6IFdoYXQgdG8gaW5jbHVkZSB3aGVuIGRlbGVnYXRpbmcKLSAqKlRpcHMqKjogQmVzdCBwcmFjdGljZXMKLSAqKlJlcXVpcmVkIHNuaXBwZXQqKjogQ29weSB0aGlzIHZlcmJhdGltIGludG8gZXZlcnkgZGVsZWdhdGlvbiBwcm9tcHQKClNlZSB0aGUgZXhpc3RpbmcgZmlsZXMgaW4gYGNvbmZpZy9gIGZvciBleGFtcGxlcy4gWW91IGNhbiBoZWxwIHRoZSB1c2VyIHdyaXRlIHRoZXNlIGluc3RydWN0aW9ucy4KCiMjIyAzLiBSZWdlbmVyYXRlIHRoaXMgc2tpbGwKCmBgYGJhc2gKenNldGFnZW50IC0tc2tpbGwgLS1mb3JjZQpgYGAKWW91IGNhbiBoZWxwIHRoZSB1c2VyIGlmIGF1dGhvcml6ZWQuCgojIyMgNC4gU3ltbGluayB0aGUgc2NyaXB0IHRvIFBBVEgKClRoaXMgbXVzdCBiZSBkb25lIGJ5IHRoZSB1c2VyIGR1ZSB0byBzdWRlIHJlcXVpcmVtbnRzLCB5dW8gY2FuIHByaW50IHRoZSBwYXRoIHRvIHRoZSB1c2VyIChhZGpzdXQgdG8gdGhlIHN5c3RlbSBpZiBuZWVkZWQpLgoKYGBgYmFzaApzdWRvIGxuIC1zIH4vLmFnZW50cy9za2lsbHMvdXNlLXN1YmFnZW50L3NjcmlwdHMvenNldGFnZW50IC91c3IvbG9jYWwvYmluL3pzZXRhZ2VudApgYGAKCiMjIyA1LiBFdmVudHVhbGx5IGNsZWFudXAgZXhhbXBsZSBmaWxlCgpJZiBleGFtcGxlIGZpbGVzIGFyZSBzdGlsbCBwcmVzZW50IHRoZSBzaG91bGQgYmUgcmVtb3ZlZC4KCi0tLQoKKipEbyBub3QgcHJvY2VlZCB3aXRoIHN1YmFnZW50IGRlbGVnYXRpb24gdW50aWwgdGhlIHVzZXIgY29uZmlybXMgdGhlc2Ugc3RlcHMgYXJlIGNvbXBsZXRlLioqCgoqKllvdSBjYW4gaGVscCB0aGUgdXNlciBjb21wbGV0ZSB0aGUgc3RlcHMgYW5kIGNvbmZpZ3VyZSB0aGUgc2tpbGwsIGJ1dCBmaXJzdCBjaGVjayB0aGUgc2NyaXB0IHByZXNlbmNlLCB0aGVuIGV4cGxhaW4gYWxsIHN0ZXBzIGFuZCBhc2suKioKCioqRG8gbm90IGF1dG8gY29uZmlndXJlLCBmZXRjaCBvciBkb3dubG9hZCBhbnl0aGluZyB3aXRob3V0IHVzZXIgY29uc2VudC4qKgoKLS0tCgojIyBXaGF0IFRoaXMgU2tpbGwgRG9lcwoKTWFuYWdlcyBzdWJhZ2VudCBtb2RlbCBjb25maWd1cmF0aW9uIHRocm91Z2ggdGhlIGB6c2V0YWdlbnRgIENMSSB0b29sLiBBZnRlciBjb25maWd1cmF0aW9uLCBhbGxvd3MgcXVpY2sgc3dpdGNoaW5nIGJldHdlZW4gZGlmZmVyZW50IG1vZGVsIHR5cGVzIGZvciBkaWZmZXJlbnQgdGFzayBjYXRlZ29yaWVzLgoKIyMgQ29tbWFuZHMKCmBgYGJhc2gKenNldGFnZW50IC0tbGlzdCAgICAgICAgICAjIFNob3cgYXZhaWxhYmxlIHR5cGVzCnpzZXRhZ2VudCA8dHlwZT4gICAgICAgICAgIyBTZXQgbW9kZWwgZm9yIHR5cGUKenNldGFnZW50IC0tc2tpbGwgICAgICAgICAjIFJlZ2VuZXJhdGUgdGhpcyBTS0lMTC5tZAp6c2V0YWdlbnQgLS1za2lsbCAtLWZvcmNlICMgT3ZlcndyaXRlIGV4aXN0aW5nIHNraWxsCmBgYAoKIyMgQ29uZmlndXJhdGlvbgoKRWRpdCBgfi8uYWdlbnRzL3NraWxscy91c2Utc3ViYWdlbnQvY29uZmlnL2NvbmZpZy5qc29uYDoKCmBgYGpzb24KewogICJ0eXBlcyI6IFsKICAgIHsidHlwZSI6ICJjb2RpbmciLCAibW9kZWwiOiAibW9kZWwuaWQiLCAicHJvdmlkZXIiOiAiYW50aHJvcGljIiwgImRlc2MiOiAiZGVzY3JpcHRpb24iLCAiZWZmb3J0IjogImxvd3xoaWdoIn0KICBdCn0KYGBgCgpTZWUgYGNvbmZpZy9gIGZvbGRlciBmb3IgZnVsbCBleGFtcGxlcy4K)** to install directly in Zed, then just run the skill once - your agent will guide you through the configuration.

### Full Install (Manual)

Clone directly to the skill directory and symlink the script to your PATH:

```bash
# Clone to skill directory
git clone https://github.com/tuchsoft/zed-use-subagent-skill.git \
  ~/.agents/skills/use-subagent

# Symlink script to PATH (ensure ~/.local/bin exists and is in your PATH)
mkdir -p ~/.local/bin
ln -s ~/.agents/skills/use-subagent/scripts/zsetagent ~/.local/bin/zsetagent

# Customize config (edit with your preferred models)
# Edit ~/.agents/skills/use-subagent/config/config.json

# Regenerate the skill with your config
zsetagent --skill --force
```

**Benefits:**
- Easy updates: `cd ~/.agents/skills/use-subagent && git pull`
- Skill stays in sync with repo

## Usage

```bash
zsetagent --list              # Show available types
zsetagent coding              # Set coding model
zsetagent exploring           # Set exploring model
zsetagent --skill --force     # Regenerate skill file
```

## Structure

```
~/.agents/skills/use-subagent/
├── SKILL.md                     # Zed skill documentation
├── README.md
├── scripts/
scripts/
│   └── zsetagent                # CLI tool (symlinked to ~/.local/bin/)
└── config/
    ├── config.json              # Your config
    ├── coding.md                # Type-specific instructions (optional)
    └── exploring.md             # Type-specific instructions (optional)

~/.local/bin/
└── zsetagent -> ~/.agents/skills/use-subagent/scripts/zsetagent  # Symlink
```

## Customization

### 1. Configure Model Types

Edit `~/.agents/skills/use-subagent/config/config.json` to add your own models:

```json
{
  "types": [
    {
      "type": "coding",
      "model": "your.model.here",
      "provider": "anthropic",
      "effort": "high",
      "enable_thinking": true,
      "desc": "Your description"
    }
  ]
}
```

### 2. Create Type-Specific Instruction Files

Each type in your config should have a corresponding `.md` file in the `config/` folder. These files contain **essential instructions** that get assembled into the final `SKILL.md` when you run `zsetagent --skill --force`.

For example:
- `config/coding.md` — Instructions for the coding subagent
- `config/browser_testing.md` — Instructions for browser automation
- `config/exploring.md` — Instructions for codebase exploration

#### What to include in each file:

```markdown
**Characteristics**: What this agent type is good at

**When to use**: Typical use cases

**Instructions to give**: What to include when delegating

**Tips**: Best practices for this type

**Required snippet**: Always include this verbatim in delegation prompts
```

> **Important**: The instruction files are essential. Without them, the agent won't know how to properly delegate to each subagent type.

### 3. Regenerate the Skill

After editing both config and instruction files, regenerate the skill:

```bash
zsetagent --skill --force
```

This assembles your configuration and type-specific instructions into the final `SKILL.md`.

## How It Works

1. **Config** (`~/.agents/skills/use-subagent/config/config.json`) defines types with models
2. **Script** (`zsetagent`) updates `~/.config/zed/settings.json` with selected model
3. **Skill** (`SKILL.md`) provides documentation and instruction templates

## Updating

If you used the full install:

```bash
cd ~/.agents/skills/use-subagent
git pull
```

## License

MIT
