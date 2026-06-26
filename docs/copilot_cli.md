[English](./copilot_cli.md) | [简体中文](./copilot_cli.zh-CN.md) · [← Back](../README.md)

# Integrate with GitHub Copilot CLI

Configure GitHub Copilot CLI to use MiMo models via BYOK (Bring Your Own Key) with the OpenAI-compatible endpoint.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with GitHub Copilot CLI. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install GitHub Copilot CLI

```shell
npm install -g @github/copilot
```

Requires Node.js 22 or later. See the [official getting-started guide](https://docs.github.com/en/copilot/how-tos/copilot-cli/cli-getting-started) for details.

## 2. Configure Environment Variables

### Pay-as-you-go

Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key (format: `sk-xxxxx`).

Linux / Mac:

```shell
export COPILOT_PROVIDER_TYPE=openai
export COPILOT_PROVIDER_BASE_URL=https://api.xiaomimimo.com/v1
export COPILOT_PROVIDER_API_KEY=sk-your-mimo-api-key
export COPILOT_MODEL=mimo-v2.5-pro
```

Windows (PowerShell):

```powershell
$env:COPILOT_PROVIDER_TYPE="openai"
$env:COPILOT_PROVIDER_BASE_URL="https://api.xiaomimimo.com/v1"
$env:COPILOT_PROVIDER_API_KEY="sk-your-mimo-api-key"
$env:COPILOT_MODEL="mimo-v2.5-pro"
```

### Token Plan

After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key (format: `tp-xxxxx`).

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe).

Linux / Mac:

```shell
export COPILOT_PROVIDER_TYPE=openai
export COPILOT_PROVIDER_BASE_URL=https://token-plan-{region}.xiaomimimo.com/v1
export COPILOT_PROVIDER_API_KEY=tp-your-token-plan-key
export COPILOT_MODEL=mimo-v2.5-pro
```

Windows (PowerShell):

```powershell
$env:COPILOT_PROVIDER_TYPE="openai"
$env:COPILOT_PROVIDER_BASE_URL="https://token-plan-{region}.xiaomimimo.com/v1"
$env:COPILOT_PROVIDER_API_KEY="tp-your-token-plan-key"
$env:COPILOT_MODEL="mimo-v2.5-pro"
```

Available models: `mimo-v2.5-pro`, `mimo-v2.5`. Switch by changing `COPILOT_MODEL`.

## 3. Start Copilot CLI

```shell
copilot
```

Full agent mode, tool calling, and MCP support — all powered by MiMo.

## Resources

- [GitHub Copilot CLI BYOK docs](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/use-byok-models)
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
