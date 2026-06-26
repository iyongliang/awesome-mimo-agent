[English](./openclaw.md) | [简体中文](./openclaw.zh-CN.md) · [← Back](../README.md)

# Integrate with OpenClaw

OpenClaw is an open-source personal AI assistant that can connect to popular chat tools like Feishu and WeChat, and can be extended through Skills.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with OpenClaw. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install OpenClaw

Linux / Mac:

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

Windows:

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

## 2. Configure the Default Model

After the initial installation, you will automatically enter the setup phase. Users who have already installed OpenClaw can enter the configuration phase via `openclaw onboard --install-daemon`.

Follow the onboard wizard:

1. **Model/auth provider** → select **Xiaomi**
2. **Xiaomi auth method** → select **Xiaomi API key (Pay-as-you-go)**
3. **Enter Xiaomi MiMo API key** → paste your API Key (starts with `sk-`)
4. The wizard sets the default model to `xiaomi/mimo-v2-flash`. Select **手动输入模型** (manually input model) and enter `xiaomi/mimo-v2.5-pro`
5. For the remaining configuration (message channels, Skills, etc.), configure as needed

## 3. Get Started

Open the Web UI:

```bash
openclaw dashboard
```

Open the TUI in the terminal:

```bash
openclaw tui
```

Chat in the terminal:

```bash
openclaw terminal
```

## Resources

- [OpenClaw](https://github.com/openclaw/openclaw) — Open-source personal AI assistant.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
