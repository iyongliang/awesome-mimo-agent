[English](./cursor.md) | [简体中文](./cursor.zh-CN.md) · [← Back](../README.md)

# Integrate with Cursor

[Cursor](https://www.cursor.com/) is an AI-native code editor built on VS Code. It supports custom model providers via the OpenAI protocol, allowing you to connect MiMo as the backend model.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Cursor. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Cursor

Download and install Cursor from [cursor.com](https://www.cursor.com/).

## 2. Add MiMo as a Custom Model

1. Open Cursor **Settings → Models**.
2. Scroll down to the model list and click **+ Add Custom Model**, enter `mimo-v2.5-pro`.
3. Expand the **API Keys** section below, enable **OpenAI API Key** and fill in your MiMo API Key.
4. Enable **Override OpenAI Base URL** and set it to:
   - Pay-as-you-go: `https://api.xiaomimimo.com/v1`
   - Token Plan: `https://token-plan-{region}.xiaomimimo.com/v1`

![Cursor Add Custom Model](./assets/cursor_add_custom_model.png)

> **Important:** The model name must be all lowercase (`mimo-v2.5-pro`). Using incorrect casing like `Mimo-v2.5-pro` will result in a "Not supported model" error.

5. Click **Save**.

## 3. Select MiMo and Start Coding

Return to the Cursor homepage, switch to the MiMo provider you just configured, and start coding.

Available models:

| Model ID | Description |
|---|---|
| `mimo-v2.5-pro` | Text generation, strongest reasoning |
| `mimo-v2.5` | Multimodal (text + image input) |

## Resources

- [Cursor](https://www.cursor.com/) — AI-native code editor.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
