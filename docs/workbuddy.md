[English](./workbuddy.md) | [简体中文](./workbuddy.zh-CN.md) · [← Back](../README.md)

# Integrate with WorkBuddy/CodeBuddy

WorkBuddy/CodeBuddy is an AI agent and coding assistant. It supports custom models through local model configuration files, and MiMo can be connected through the OpenAI-compatible Chat Completions API.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install WorkBuddy/CodeBuddy

- Install and sign in to WorkBuddy/CodeBuddy.
- Open a project folder once, so the application can create its local configuration directories.

## 2. Configure Local Models

Create or edit the user-level configuration file:

- **macOS / Linux**: `~/.workbuddy/models.json`
- **Windows**: `C:\Users\<your-username>\.codebuddy\models.json`

To apply the configuration only to one project, create the project-level configuration file instead:

```
<your-project>\.codebuddy\models.json
```

Set your MiMo API Key as an environment variable first:

```powershell
setx MIMO_API_KEY "<your MiMo API Key>"
```

### Pay-as-you-go

```json
{
  "models": [
    {
      "id": "mimo-v2.5-pro",
      "name": "MiMo V2.5 Pro",
      "vendor": "Xiaomi",
      "url": "https://api.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": false,
      "relatedModels": {
        "lite": "mimo-v2.5",
        "reasoning": "mimo-v2.5-pro"
      }
    },
    {
      "id": "mimo-v2.5",
      "name": "MiMo V2.5",
      "vendor": "Xiaomi",
      "url": "https://api.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": true
    }
  ],
  "availableModels": [
    "mimo-v2.5-pro",
    "mimo-v2.5"
  ]
}
```

### Token Plan

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe).

```json
{
  "models": [
    {
      "id": "mimo-v2.5-pro",
      "name": "MiMo V2.5 Pro",
      "vendor": "Xiaomi",
      "url": "https://token-plan-{region}.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": false,
      "relatedModels": {
        "lite": "mimo-v2.5",
        "reasoning": "mimo-v2.5-pro"
      }
    },
    {
      "id": "mimo-v2.5",
      "name": "MiMo V2.5",
      "vendor": "Xiaomi",
      "url": "https://token-plan-{region}.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": true
    }
  ],
  "availableModels": [
    "mimo-v2.5-pro",
    "mimo-v2.5"
  ]
}
```

Save `models.json` as UTF-8 without BOM.

## 3. Restart and Select the Model

Fully quit WorkBuddy/CodeBuddy, then open it again. In the model selector, choose **MiMo V2.5 Pro** or **MiMo V2.5**.

## Troubleshooting

- `Authentication Fails` or `401`: Check whether `apiKey` is your real MiMo API Key.
- `Model Not Found` or `404`: Check whether the model id is exactly `mimo-v2.5-pro` or `mimo-v2.5`.
- `Failed to read local model configuration`: Check whether `models.json` is valid JSON and saved as UTF-8 without BOM.
- The model does not appear in the selector: Fully restart WorkBuddy/CodeBuddy and confirm the file is placed under `.codebuddy\models.json`.

## Resources

- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
