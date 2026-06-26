[English](./zoo_code.md) | [简体中文](./zoo_code.zh-CN.md) · [← Back](../README.md)

# Integrate with Zoo Code

Zoo Code is an AI coding assistant that runs as a VS Code extension, supporting multiple API providers and models. It is a community-maintained fork that continues the discontinued Roo Code project. MiMo integrates with Zoo Code via the OpenAI-compatible protocol.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Zoo Code. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Zoo Code Extension

- Open VS Code.
- Click the **Extensions** icon in the activity bar (or press `Ctrl+Shift+X` / `Cmd+Shift+X`).
- Search for `Zoo Code`.
- Find the **Zoo Code** extension (published by **Zoo Code Organization**) in the results and click **Install**.
- After installation, open Zoo Code from the icon in the activity bar.

> For VS Code-compatible editors without the Marketplace (such as VSCodium or Windsurf), install Zoo Code from the [Open VSX Registry](https://open-vsx.org/) using the same steps.

## 2. Configure API Provider

In the Zoo Code settings, configure the provider as follows:

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

(Optional) Expand **Model Configuration** to adjust context window size, max output tokens, pricing, and other limits. MiMo V2.5 Pro supports up to **1 million tokens** of context.

## 3. Use Zoo Code

After configuration, you can start using Zoo Code with MiMo in VS Code. Open Zoo Code from the activity bar and begin chatting. Switch between **Code**, **Architect**, **Ask**, and **Debug** modes depending on your task.

## Resources

- [Zoo Code](https://github.com/Zoo-Code-Org/Zoo-Code) — AI coding assistant VS Code extension.
- [Zoo Code Documentation](https://docs.zoocode.dev/)
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
