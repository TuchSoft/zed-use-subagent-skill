# use-subagent

> ⚠️ **Temporary Solution / Hack** — This repository is intended as a temporary fix/workaround until the Zed team rolls out complete subagent management features. It will be **deprecated** when and if native support becomes available.

A Zed skill for managing subagent model selection. Provides the `zsetagent` CLI tool to configure which AI model to use for each subagent type.

## Installation

> **Windows is not supported** — this skill relies on Unix paths and symlinks.

### Quick Install (Recommended)

**[Click here](zed://skill?data=LS0tCm5hbWU6IHVzZS1zdWJhZ2VudApkZXNjcmlwdGlvbjogU2VsZWN0IGFuZCBjb25maWd1cmUgWmVkIHN1YmFnZW50IG1vZGVscyBieSB0eXBlIGZvciBvcHRpbWFsIHRhc2sgZGVsZWdhdGlvbi4KLS0tCgojIFplZCBTdWJhZ2VudCBNb2RlbCBTZWxlY3RvcgoKIyMg4pqg77iPIFNLSUxMIE5PVCBDT05GSUdVUkVEIC0gQUNUSU9OIFJFUVVJUkVECgoqKlRoaXMgc2tpbGwgaXMgTk9UIHJlYWR5IGZvciB1c2UuKiogWW91IG11c3QgY29uZmlndXJlIGl0IGJlZm9yZSB0aGUgYWdlbnQgY2FuIGRlbGVnYXRlIHRvIHN1YmFnZW50cy4KCiMjIyAwLiBDaGVjayBpZiBmdWxsIGluc3RhbGxhdGlvbiBpcyBuZWVkZWQKCklmIHRoZSBza2lsbCB3YXMgaW5zdGFsbGVkIHZpYSBaZWQncyBxdWljay1pbnN0YWxsIGxpbmsgKGNoZWNrIGlmIGB-Ly5hZ2VudHMvc2tpbGxzL3VzZS1zdWJhZ2VudC9zY3JpcHRzL3pzZXRhZ2VudGAgaXMgbWlzc2luZyksIHRoZSByZXF1aXJlZCBzY3JpcHQgaXMgbm90IGluY2x1ZGVkLiAKQ29tcGxldGUgdGhlIGluc3RhbGxhdGlvbiwgeXVvIGNhbiBlaXRoZXI6CgpgYGBiYXNoCiMgQ2xvbmUgdGhlIGZ1bGwgcmVwb3NpdG9yeQpnaXQgY2xvbmUgaHR0cHM6Ly9naXRodWIuY29tL3R1Y2hzb2Z0L3plZC11c2Utc3ViYWdlbnQtc2tpbGwuZ2l0IH4vLmFnZW50cy9za2lsbHMvdXNlLXN1YmFnZW50CmBgYAoKVGhlbiBwcm9jZWVkIHdpdGggdGhlIHJlbWFpbmluZyBzdGVwcyBiZWxvdy4KCioqT1IqKgoKcmVhZCB0aGUgcmVtb3RlIHJlYWRtZSBhbmQgZmlsZSBzdHJjdXR1cmUgYW5kIGRvd25sb2FkIHRoZSBzaW5nbGUgZmlsZXMgbmVlZGVkICh0aGUgcmVwbyBpcyBhbHJlYWR5IHNsaW0pLgpBc2sgdGhlIHVzZXIgdGhlaXIgcHJlZmVyZW5jZXMuCgoKIyMjIDEuIEN1c3RvbWl6ZSBjb25maWcKCkVkaXQgYH4vLmFnZW50cy9za2lsbHMvdXNlLXN1YmFnZW50L2NvbmZpZy9jb25maWcuanNvbmAgd2l0aCB5b3VyIHByZWZlcnJlZCBtb2RlbHMuCgpBc2sgdGhlIHVzZXIgdGhlaXIgcHJlZmVycmVkIG1vZGVscywgYWdlbnQgdHlwZXMsIGFuZCBkZXNjcmlwdGlvbnMuIFlvdSBjYW4gY2hlY2sgdGhlIFplZCBjb25maWcgZmlsZSAocmVhZCBvbmx5KSB0byB1bmRlcnN0YW5kIHdoYXQgcHJvdmlkZXIvbW9kZWxzIGFyZSBhdmFpbGFibGUsIGJ1dCBmaXJzdCBhc2sgdGhlIHVzZXIuCgpEb24ndCBmb3JnZXQgdG8gYWxzbyBjcmVhdGUgdGhlIHR5cGUtc3BlY2lmaWMgaW5zdHJ1Y3Rpb24gZmlsZXMgKHNlZSBzdGVwIDIpLgoKIyMjIDIuIFdyaXRlIHR5cGUtc3BlY2lmaWMgaW5zdHJ1Y3Rpb24gZmlsZXMKCkVhY2ggc3ViYWdlbnQgdHlwZSBzaG91bGQgaGF2ZSBhIGNvcnJlc3BvbmRpbmcgYC5tZGAgZmlsZSBpbiB0aGUgYGNvbmZpZy9gIGZvbGRlcjoKCi0gYGNvbmZpZy9jb2RpbmcubWRgIOKAlCBJbnN0cnVjdGlvbnMgZm9yIHRoZSBjb2Rpbmcgc3ViYWdlbnQKLSBgY29uZmlnL2Jyb3dzZXJfdGVzdGluZy5tZGAg4oCUIEluc3RydWN0aW9ucyBmb3IgYnJvd3NlciBhdXRvbWF0aW9uCi0gYGNvbmZpZy9leHBsb3JpbmcubWRgIOKAlCBJbnN0cnVjdGlvbnMgZm9yIGNvZGViYXNlIGV4cGxvcmF0aW9uCgpFYWNoIGZpbGUgc2hvdWxkIGluY2x1ZGU6Ci0gKipDaGFyYWN0ZXJpc3RpY3MqKjogV2hhdCB0aGlzIGFnZW50IHR5cGUgaXMgZ29vZCBhdAotICoqV2hlbiB0byB1c2UqKjogVHlwaWNhbCB1c2UgY2FzZXMKLSAqKkluc3RydWN0aW9ucyB0byBnaXZlKio6IFdoYXQgdG8gaW5jbHVkZSB3aGVuIGRlbGVnYXRpbmcKLSAqKlRpcHMqKjogQmVzdCBwcmFjdGljZXMKLSAqKlJlcXVpcmVkIHNuaXBwZXQqKjogQ29weSB0aGlzIHZlcmJhdGltIGludG8gZXZlcnkgZGVsZWdhdGlvbiBwcm9tcHQKClNlZSB0aGUgZXhpc3RpbmcgZmlsZXMgaW4gYGNvbmZpZy9gIGZvciBleGFtcGxlcy4gWW91IGNhbiBoZWxwIHRoZSB1c2VyIHdyaXRlIHRoZXNlIGluc3RydWN0aW9ucy4KCiMjIyAzLiBSZWdlbmVyYXRlIHRoaXMgc2tpbGwKCmBgYGJhc2gKenNldGFnZW50IC0tc2tpbGwgLS1mb3JjZQpgYGAKWW91IGNhbiBoZWxwIHRoZSB1c2VyIGlmIGF1dGhvcml6ZWQuCgojIyMgNC4gU3ltbGluayB0aGUgc2NyaXB0IHRvIFBBVEgKCioqSW1wb3J0YW50Kio6IEVuc3VyZSBgfi8ubG9jYWwvYmluYCBpcyBpbiB5b3VyIFBBVEguIElmIG5vdCwgYWRkIHRoaXMgdG8geW91ciBzaGVsbCBjb25maWc6CgpgYGBiYXNoCmV4cG9ydCBQQVRIPSIkSE9NRS8ubG9jYWwvYmluOiRQQVRIIgpgYGAKClRoZW4gY3JlYXRlIHRoZSBkaXJlY3RvcnkgYW5kIHN5bWxpbms6CgpgYGBiYXNoCm1rZGlyIC1wIH4vLmxvY2FsL2JpbgpsbiAtcyB-Ly5hZ2VudHMvc2tpbGxzL3VzZS1zdWJhZ2VudC9zY3JpcHRzL3pzZXRhZ2VudCB-Ly5sb2NhbC9iaW4venNldGFnZW50CmBgYAoKIyMjIDUuIEV2ZW50dWFsbHkgY2xlYW51cCBleGFtcGxlIGZpbGUKCklmIGV4YW1wbGUgZmlsZXMgYXJlIHN0aWxsIHByZXNlbnQgdGhlIHNob3VsZCBiZSByZW1vdmVkLgoKLS0tCgoqKkRvIG5vdCBwcm9jZWVkIHdpdGggc3ViYWdlbnQgZGVsZWdhdGlvbiB1bnRpbCB0aGUgdXNlciBjb25maXJtcyB0aGVzZSBzdGVwcyBhcmUgY29tcGxldGUuKioKCioqWW91IGNhbiBoZWxwIHRoZSB1c2VyIGNvbXBsZXRlIHRoZSBzdGVwcyBhbmQgY29uZmlndXJlIHRoZSBza2lsbCwgYnV0IGZpcnN0IGNoZWNrIHRoZSBzY3JpcHQgcHJlc2VuY2UsIHRoZW4gZXhwbGFpbiBhbGwgc3RlcHMgYW5kIGFzay4qKgoKKipEbyBub3QgYXV0byBjb25maWd1cmUsIGZldGNoIG9yIGRvd25sb2FkIGFueXRoaW5nIHdpdGhvdXQgdXNlciBjb25zZW50LioqCgotLS0KCiMjIFdoYXQgVGhpcyBTa2lsbCBEb2VzCgpNYW5hZ2VzIHN1YmFnZW50IG1vZGVsIGNvbmZpZ3VyYXRpb24gdGhyb3VnaCB0aGUgYHpzZXRhZ2VudGAgQ0xJIHRvb2wuIEFmdGVyIGNvbmZpZ3VyYXRpb24sIGFsbG93cyBxdWljayBzd2l0Y2hpbmcgYmV0d2VlbiBkaWZmZXJlbnQgbW9kZWwgdHlwZXMgZm9yIGRpZmZlcmVudCB0YXNrIGNhdGVnb3JpZXMuCgojIyBDb21tYW5kcwoKYGBgYmFzaAp6c2V0YWdlbnQgLS1saXN0ICAgICAgICAgICMgU2hvdyBhdmFpbGFibGUgdHlwZXMKenNldGFnZW50IDx0eXBlPiAgICAgICAgICAjIFNldCBtb2RlbCBmb3IgdHlwZQp6c2V0YWdlbnQgLS1za2lsbCAgICAgICAgICMgUmVnZW5lcmF0ZSB0aGlzIFNLSUxMLm1kCnpzZXRhZ2VudCAtLXNraWxsIC0tZm9yY2UgIyBPdmVyd3JpdGUgZXhpc3Rpbmcgc2tpbGwKYGBgCgojIyBDb25maWd1cmF0aW9uCgpFZGl0IGB-Ly5hZ2VudHMvc2tpbGxzL3VzZS1zdWJhZ2VudC9jb25maWcvY29uZmlnLmpzb25gOgoKYGBganNvbgp7CiAgInR5cGVzIjogWwogICAgeyJ0eXBlIjogImNvZGluZyIsICJtb2RlbCI6ICJtb2RlbC5pZCIsICJwcm92aWRlciI6ICJhbnRocm9waWMiLCAiZGVzYyI6ICJkZXNjcmlwdGlvbiIsICJlZmZvcnQiOiAibG93fGhpZ2gifQogIF0KfQpgYGAKClNlZSBgY29uZmlnL2AgZm9sZGVyIGZvciBmdWxsIGV4YW1wbGVzLgo)** to install directly in Zed, then just run the skill once - your agent will guide you through the configuration.

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
