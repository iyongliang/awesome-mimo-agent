[English](./trae.md) | [简体中文](./trae.zh-CN.md) · [← Back](../README.md)

# Integrate with TRAE

[TRAE](https://www.trae.cn/) (The Real AI Engineer) is an AI-native IDE developed by ByteDance. MiMo is recommended to integrate with TRAE IDE via the OpenAI-compatible protocol.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with TRAE. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install TRAE IDE

Download and install TRAE IDE from the [official website](https://www.trae.cn/).

For detailed installation instructions, see the [TRAE documentation](https://docs.trae.cn/ide/get-started-with-trae).

## 2. Add Custom Model

### Supported Models

TRAE supports both chat and code completion models. The following example uses `mimo-v2.5-pro`. See the [Model List](https://platform.xiaomimimo.com/docs/en-US/quick-start/model) for all available models.

### Configuration Steps

1. Open the TRAE panel and click **Settings** in the upper right corner.

2. In the left menu bar, under **Models**, click **Add Custom model here**.

3. Select **Custom Config**, then choose **OpenAI Chat Completions** as the **API Format**.

4. Fill in the configuration (see [Pay-as-you-go](#pay-as-you-go) or [Token Plan](#token-plan) below).

5. Click **Add Model** to save the model.

<img src="./assets/trae_ide_add_model.png" width="500"/>

### Pay-as-you-go

Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key (format: `sk-xxxxx`).

| Field | Value |
|-------|-------|
| Custom Request URL | `https://api.xiaomimimo.com/v1` |
| Model ID | `mimo-v2.5-pro` |
| API Key | Your API key (`sk-xxxxx`) |

> If the Full URL option is enabled, Custom Request URL should be the complete endpoint path `https://api.xiaomimimo.com/v1/chat/completions`.

> For multimodal models (e.g., `mimo-v2.5`), enable the **MultiModal** option next to the Model ID.

### Token Plan

After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key (format: `tp-xxxxx`).

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe).

| Field | Value |
|-------|-------|
| Custom Request URL | `https://token-plan-{region}.xiaomimimo.com/v1` |
| Model ID | `mimo-v2.5-pro` |
| API Key | Your API key (`tp-xxxxx`) |

> If the Full URL option is enabled, Custom Request URL should be the complete endpoint path `https://token-plan-{region}.xiaomimimo.com/v1/chat/completions`.

> For multimodal models (e.g., `mimo-v2.5`), enable the **MultiModal** option next to the Model ID.

## 3. Use MiMo in TRAE

1. Disable **Auto Mode**.
2. In the conversation panel, select your added custom model from the model dropdown list.
3. You are now ready to start using MiMo with TRAE.

## Resources

- [TRAE Official Website](https://www.trae.cn/) — download and product information.
- [TRAE Documentation](https://docs.trae.cn/) — official guides and references.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
