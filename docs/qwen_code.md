[English](./qwen_code.md) | [简体中文](./qwen_code.zh-CN.md) · [← Back](../README.md)

# Integrate with Qwen Code

Qwen Code is an open-source AI agent that lives in your terminal, built by the Qwen team at Alibaba Group.

- **GitHub:** <https://github.com/QwenLM/qwen-code>
- **Docs:** <https://qwenlm.github.io/qwen-code-docs/en/users/overview/>

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Qwen Code. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Qwen Code

- Install [Node.js](https://nodejs.org/en/download/) 20 or later.
- Install Qwen Code:

```bash
npm install -g @qwen-code/qwen-code@latest
```

Or via the quick-install script:

```bash
curl -fsSL https://qwen-code-assets.oss-cn-hangzhou.aliyuncs.com/installation/install-qwen-standalone.sh | bash
```

Or Homebrew:

```bash
brew install qwen-code
```

- Verify:

```bash
qwen --version
```

## 2. Configure MiMo via /auth

Launch Qwen Code:

```bash
qwen
```

Inside the interactive session, run `/auth`:

```
/auth
```

Select **Custom Provider** and follow the 6-step wizard:

| Step | Field | Value |
|---|---|---|
| 1 | Protocol | OpenAI Compatible |
| 2 | Base URL | `https://api.xiaomimimo.com/v1` (Pay-as-you-go) or `https://token-plan-{region}.xiaomimimo.com/v1` (Token Plan) |
| 3 | API Key | Your MiMo API Key |
| 4 | Model ID | `mimo-v2.5-pro` |
| 5 | Advanced Config | Enable thinking: **on**; Enable modality: off; Context window: `1048576` |
| 6 | Provider Name | `MiMo` (or any name you prefer) |

## 3. Switch to MiMo Model

Run the `/model` command and select `mimo-v2.5-pro`:

```
/model
```

You're ready to go. Qwen Code will now use MiMo for coding.

> **Tip:** Use `/model` to switch between models at any time. Use `/auth` again if you need to reconfigure.

## Resources

- [Qwen Code](https://github.com/QwenLM/qwen-code) — Open-source terminal AI coding agent.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
