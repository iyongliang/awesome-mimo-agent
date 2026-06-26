[English](./pi_mono.md) | [简体中文](./pi_mono.zh-CN.md) · [← Back](../README.md)

# Integrate with Pi

Pi (pi-mono) is a minimal, aggressively extensible terminal coding harness. It adapts to your workflows through TypeScript extensions, skills, prompt templates, and themes — with tree-structured sessions and 15+ built-in providers.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Pi. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Pi

- Install [Node.js](https://nodejs.org/en/download/).
- Run the following command in your terminal to install Pi:

```bash
npm install -g @earendil-works/pi-coding-agent
```

- After installation, run the following command. If the version number is displayed, the installation is successful:

```bash
pi --version
```

> **Note:** Linux / macOS users can also install via the official script:
> ```bash
> curl -fsSL https://pi.dev/install.sh | sh
> ```

## 2. Configure MiMo Provider

Pi supports custom providers via `models.json`. Add MiMo as an OpenAI-compatible provider:

- **Linux / macOS**: `~/.pi/agent/models.json`
- **Windows**: `%USERPROFILE%\.pi\agent\models.json`

### Pay-as-you-go

Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key (format: `sk-xxxxx`).

```json
{
  "providers": {
    "xiaomi": {
      "baseUrl": "https://api.xiaomimimo.com/v1",
      "api": "openai-completions",
      "apiKey": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 1,
            "output": 3,
            "cacheRead": 0.2,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text", "image"],
          "reasoning": true,
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
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
  "providers": {
    "xiaomi": {
      "baseUrl": "https://token-plan-{region}.xiaomimimo.com/v1",
      "api": "openai-completions",
      "apiKey": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 1,
            "output": 3,
            "cacheRead": 0.2,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text", "image"],
          "reasoning": true,
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
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

Enter the project directory and execute the `pi` command:

```bash
cd /path/to/my-project
pi
```

- Type `/model` to open the model switcher.
- Select **xiaomi** and choose `MiMo-V2.5-Pro` or `MiMo-V2.5`.

## Resources

- [Pi](https://github.com/badlogic/pi-mono) — Minimal terminal coding harness.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
