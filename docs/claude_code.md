[English](./claude_code.md) | [简体中文](./claude_code.zh-CN.md) · [← Back](../README.md)

# Integrate with Claude Code

Claude Code is a terminal-level AI coding assistant launched by Anthropic, which also supports VS Code extensions. MiMo integrates with Claude Code via the Anthropic-compatible protocol only.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Claude Code. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Claude Code CLI

### Option 1: Native Install (Recommended)

Native install automatically updates in the background to keep you on the latest version.

macOS / Linux / WSL:

```shell
curl -fsSL https://claude.ai/install.sh | bash
```

Windows PowerShell:

```powershell
irm https://claude.ai/install.ps1 | iex
```

Windows CMD:

```batch
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

> [Git for Windows](https://git-scm.com/download/win) is recommended on native Windows so Claude Code can use the Bash tool.

### Option 2: npm

- Requires [Node.js](https://nodejs.org/en/download/) 18+.
- Windows users need to install [Git for Windows](https://git-scm.com/download/win).

```shell
npm install -g @anthropic-ai/claude-code
```

---

Verify the installation:

```shell
claude --version
```

For more installation methods (Homebrew, WinGet, etc.), see the [official setup guide](https://code.claude.com/docs/en/setup).

## 2. Configure Claude Code

### Skip Login Prompt

Create or edit `~/.claude.json` (Windows: `C:\Users\<your username>\.claude.json`) to skip the Anthropic login screen:

```json
{
  "hasCompletedOnboarding": true
}
```

### Configure API Credentials

Claude Code can be configured via a configuration file or environment variables. In most cases, prefer the configuration file approach, as settings in the configuration file can be read by both Claude Code CLI and VS Code Extension.

Configuration file location:
- Linux / Mac: `~/.claude/settings.json`
- Windows: `C:\Users\<your username>\.claude\settings.json`
- **If the file does not exist, create it.**

#### Supported Models

Claude Code only supports text generation models. See the [Model List](https://platform.xiaomimimo.com/docs/en-US/quick-start/model) for all available models.

#### Pay-as-you-go

Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key (format: `sk-xxxxx`).

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.xiaomimimo.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "MIMO_API_KEY",
    "ANTHROPIC_MODEL": "mimo-v2.5-pro[1m]",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "mimo-v2.5-pro[1m]",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "mimo-v2.5-pro[1m]",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "mimo-v2.5-pro[1m]",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
  }
}
```

#### Token Plan

After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key (format: `tp-xxxxx`).

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe).

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://token-plan-{region}.xiaomimimo.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "MIMO_API_KEY",
    "ANTHROPIC_MODEL": "mimo-v2.5-pro[1m]",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "mimo-v2.5-pro[1m]",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "mimo-v2.5-pro[1m]",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "mimo-v2.5-pro[1m]",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
  }
}
```

#### Notes

- Replace the `ANTHROPIC_AUTH_TOKEN` value with your actual API key.
- `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` prevents Claude Code from sending telemetry or update checks to Anthropic servers.
- The `[1m]` suffix extends the context window to **1M** tokens for supported MiMo models. After launching Claude Code, run the `/context` command to verify it is in effect.

## 3. VS Code Extension (Optional)

Install [Claude Code VS Code Extension](https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code).

<img src="./assets/claude_code_vs_code_extension.png" width="500"/>

The VS Code extension automatically reuses the Claude Code CLI configuration (`~/.claude/settings.json` and `~/.claude.json`), so no additional setup is needed if you have already configured the CLI.

## 4. Use Claude Code

### Using Claude Code CLI

Enter the project directory and run `claude`:

```shell
cd /path/to/my-project
claude
```

### Using Claude Code VS Code Extension

Open your project directory in VS Code, click the Claude Code icon in the sidebar, and click **New session** to get started.

## Resources

- [Claude Code](https://code.claude.com/docs/en/overview) — Anthropic's AI coding assistant.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
