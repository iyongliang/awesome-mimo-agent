[English](./mimo_code.md) | [简体中文](./mimo_code.zh-CN.md) · [← Back](../README.md)

# Integrate with MiMo-Code

MiMo-Code is a terminal-native AI coding assistant built by Xiaomi. It can read and write code, run commands, manage Git, and use a persistent memory system to maintain project understanding across sessions. Built on OpenCode with added persistent memory, subagent orchestration, and self-improvement features.

- **GitHub:** <https://github.com/XiaomiMiMo/MiMo-Code>

## 1. Install MiMo-Code

### Quick Install (Recommended)

```bash
curl -fsSL https://mimo.xiaomi.com/install | bash
```

### Via npm

```bash
npm install -g @mimo-ai/cli
```

Verify the installation:

```bash
mimo --version
```

## 2. Launch and Configure

Run `mimo` in your project directory:

```bash
cd /path/to/my-project
mimo
```

On first launch, you will be guided through provider setup. Available options:

| Setup Option | Description |
|---|---|
| **MiMo Auto** | Free limited-time anonymous channel, zero config needed |
| **Xiaomi MiMo Platform** | OAuth login to MiMo Platform |
| **Import from Claude Code** | Migrate existing authentication |
| **Custom Provider** | Any OpenAI-compatible API |

For most users, select **Xiaomi MiMo Platform** and follow the OAuth flow to log in.

## 3. Basic Usage

| Key / Command | Function |
|---|---|
| `Tab` | Switch agents: **build** (full dev), **plan** (read-only analysis), **compose** (orchestration) |
| `/goal` | Set a stopping condition with independent judge evaluation |
| `/voice` | Activate streaming voice input (requires `sox`) |
| `/dream` | Extract knowledge from sessions into project memory |
| `/distill` | Convert repeated workflows into reusable skills |
| `/connect` | Sign in to additional providers |

## 4. Configuration

Configuration file locations:

- **Project-level:** `.mimocode/mimocode.json`
- **Global:** `~/.config/mimocode/mimocode.json`

## Resources

- [MiMo-Code](https://github.com/XiaomiMiMo/MiMo-Code) — Terminal-native AI coding assistant by Xiaomi.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
