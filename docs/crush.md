[English](./crush.md) | [简体中文](./crush.zh-CN.md) · [← Back](../README.md)

# Integrate with Crush

Crush is an open-source AI coding agent that runs in your terminal, built by Charm. It supports multi-model switching, LSP integration, MCP servers, and agentic coding workflows. MiMo integrates with Crush via the OpenAI-compatible protocol.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Crush. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Crush

- Install [Node.js](https://nodejs.org/en/download/).
- Run the following command in your terminal to install Crush:

```bash
npm install -g @charmland/crush
```

- After installation, run the following command. If the version number is displayed, the installation is successful:

```bash
crush --version
```

> **Note:** macOS users can also install via Homebrew: `brew install charmbracelet/tap/crush`.

## 2. Configure MiMo Provider

Crush supports custom providers via OpenAI-compatible APIs. Add MiMo to your configuration file:

- **Linux / macOS**: `~/.config/crush/crush.json`
- **Windows**: `%USERPROFILE%\.config\crush\crush.json`

### Pay-as-you-go

Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key (format: `sk-xxxxx`).

```json
{
  "$schema": "https://charm.land/crush.json",
  "providers": {
    "mimo": {
      "type": "openai-compat",
      "base_url": "https://api.xiaomimimo.com/v1",
      "api_key": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        }
      ]
    }
  }
}
```

### Token Plan

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe).

```json
{
  "$schema": "https://charm.land/crush.json",
  "providers": {
    "mimo": {
      "type": "openai-compat",
      "base_url": "https://token-plan-{region}.xiaomimimo.com/v1",
      "api_key": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        }
      ]
    }
  }
}
```

Set the environment variable:

Linux / Mac:

```bash
export MIMO_API_KEY="<your MiMo API Key>"
```

Windows:

```powershell
$env:MIMO_API_KEY="<your MiMo API Key>"
```

## 3. Run and Select Model

Enter the project directory and execute the `crush` command:

```bash
cd /path/to/my-project
crush
```

- Press `Ctrl+L` (or type `/model`) to open the model switcher.
- Select the **mimo** provider and choose `MiMo-V2.5-Pro` or `MiMo-V2.5`.

## Resources

- [Crush](https://github.com/charmbracelet/crush) — Open-source terminal AI coding agent.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
