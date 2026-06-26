[English](./cline.md) | [简体中文](./cline.zh-CN.md) · [← Back](../README.md)

# Integrate with Cline

Cline is an AI coding assistant that runs as a VS Code extension, supporting multiple API providers and models. MiMo integrates with Cline via the OpenAI-compatible protocol.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Cline. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Cline Extension

- Open VS Code.
- Click the **Extensions** icon in the activity bar (or press `Ctrl+Shift+X`).
- Search for `cline`.
- Find the **Cline** extension in the results and click **Install**.
- After installation completes, choose to trust the developer when prompted.

## 2. Configure API Provider

In the Cline settings, select **Bring my own API Key**, then configure as follows:

- Select **API Provider** as **OpenAI Compatible**.
- Enter your MiMo API credentials:

#### Pay-as-you-go

Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key (format: `sk-xxxxx`).

- **Base URL**: `https://api.xiaomimimo.com/v1`
- **API Key**: your MiMo API Key
- **Model ID**: `mimo-v2.5-pro`

#### Token Plan

After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key (format: `tp-xxxxx`).

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe).

- **Base URL**: `https://token-plan-{region}.xiaomimimo.com/v1`
- **API Key**: your Token Plan API Key
- **Model ID**: `mimo-v2.5-pro`

#### Supported Models

| Model ID | Description |
|---|---|
| `mimo-v2.5-pro` | Text generation, strongest reasoning |
| `mimo-v2.5` | Multimodal (text + image input) |

See the [Model List](https://platform.xiaomimimo.com/docs/en-US/quick-start/model) for all available models.

(Optional) Click **Model Configuration** to adjust context window size, temperature, pricing, and limits.

## 3. Use Cline

After configuration, you can start using Cline with MiMo in VS Code. Open Cline from the sidebar and begin chatting.

## Resources

- [Cline](https://github.com/cline/cline) — AI coding assistant VS Code extension.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
