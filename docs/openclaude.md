[English](./openclaude.md) | [简体中文](./openclaude.zh-CN.md) · [← Back](../README.md)

# Integrate with OpenClaude

[OpenClaude](https://github.com/Gitlawb/openclaude) is an open-source AI coding assistant CLI that supports multiple providers (OpenAI, Gemini, Ollama, Xiaomi MiMo, etc.) via interactive configuration.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with OpenClaude. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install OpenClaude

Requires **Node.js >= 22.0.0**.

```bash
npm install -g @gitlawb/openclaude@latest
```

Verify the installation:

```bash
openclaude --version
```

> **Note:** If you see `ripgrep not found` after launching, install ripgrep separately (`brew install ripgrep` on macOS or the equivalent for your package manager).

## 2. Configure the MiMo Provider

Launch OpenClaude and run the `/provider` command:

```bash
openclaude
```

```
/provider
```

1. In the **Choose provider preset** list, select **Xiaomi MiMo**.
2. The endpoint and advanced details are already configured by the preset (OpenAI-compatible API).
3. **Step 1 of 2 — Default model**: enter `mimo-v2.5-pro`
4. **Step 2 of 2 — API Key**: enter your MiMo API Key

## 3. Start Coding

After configuration, OpenClaude is ready to use with MiMo. Start a new session:

```bash
openclaude
```

## Resources

- [OpenClaude](https://github.com/Gitlawb/openclaude) — Open-source AI coding assistant CLI.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
