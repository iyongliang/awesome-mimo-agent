[English](./astrbot.md) | [简体中文](./astrbot.zh-CN.md) · [← Back](../README.md)

# Integrate with AstrBot

[AstrBot](https://github.com/AstrBotDevs/AstrBot) is an open-source all-in-one agent assistant that integrates with mainstream messaging platforms such as QQ, WeChat, Feishu, and Telegram, and can be extended with skills, plugins, and MCPs.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with AstrBot. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install AstrBot

### Install via uv

For macOS and Linux users:

```bash
curl -LsSf https://docs.astrbot.app/install.sh | bash
```

For Windows users:

```bash
iwr -useb https://docs.astrbot.app/install.ps1 | iex
```

Then initialize and start AstrBot:

```bash
astrbot init
astrbot run
```

### Install via Docker

```bash
git clone https://github.com/AstrBotDevs/AstrBot --depth 1
cd AstrBot
sudo docker compose up -d
```

## 2. Configure the Default Model

After initialization, open the Web UI:

```
http://localhost:6185
```

In the left sidebar, open the **模型提供商** (Providers) page, click **+ 新增** (Add).

In the provider dropdown, select **Xiaomi** (Pay-as-you-go) or **Xiaomi Token Plan** depending on your usage mode. The API Base URL is pre-filled automatically.

Fill in:

- **API Key**: your MiMo API Key

Click **保存配置** (Save Configuration).

## 3. Get Started

Click **Chat** in the top-right corner to switch to the AstrBot Chat UI. You can now start chatting with MiMo.

You can also configure messaging platforms to use AstrBot directly from your preferred chat app. See the [AstrBot Docs](https://docs.astrbot.app/) for details.

## Resources

- [AstrBot](https://github.com/AstrBotDevs/AstrBot) — Open-source all-in-one agent assistant.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
