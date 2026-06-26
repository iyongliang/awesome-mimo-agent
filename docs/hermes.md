[English](./hermes.md) | [简体中文](./hermes.zh-CN.md) · [← Back](../README.md)

# Integrate with Hermes Agent

Hermes is a self-improving AI agent built by Nous Research. It includes a built-in learning loop: it creates skills from experience, improves them during use, persists knowledge, and builds an evolving model of your preferences across sessions.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Hermes. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Hermes

### Quick Install

Linux / macOS / WSL2:

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

The only prerequisite is Git. The installer automatically handles everything else.

For more installation instructions, please refer to the [Hermes installation page](https://hermes-agent.nousresearch.com/docs/getting-started/installation).

## 2. Run and Configure

Reload your shell and start Hermes configuration:

```bash
hermes setup
```

1. Choose **Full setup** — configure every provider, tool & option yourself
2. In the **Select provider** list, choose **Xiaomi MiMo** (MiMo-V2.5 and V2 models: pro, omni, flash)
3. Enter your MiMo API Key when prompted
4. Select the model (e.g. `mimo-v2.5-pro`)
5. Continue with the remaining options (tools, preferences, etc.)

## 3. Use Hermes

Enter the project directory and run:

```bash
cd /path/to/my-project
hermes
```

## Resources

- [Hermes Agent](https://github.com/NousResearch/hermes-agent) — Self-improving AI agent by Nous Research.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
