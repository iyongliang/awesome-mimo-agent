[English](./cherry_studio.md) | [简体中文](./cherry_studio.zh-CN.md) · [← Back](../README.md)

# Integrate with Cherry Studio

Cherry Studio is an open-source desktop AI client for Windows, macOS, and Linux that unifies access to multiple LLM providers. It ships with 300+ pre-configured chat assistants, agents, AI translation, knowledge bases, and MCP servers.

- **GitHub:** <https://github.com/CherryHQ/cherry-studio>
- **Website:** <https://cherry-ai.com>

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Cherry Studio. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Cherry Studio

Download the installer for your platform from the [Cherry Studio releases page](https://github.com/CherryHQ/cherry-studio/releases) or the [official website](https://cherry-ai.com).

Available builds:

- Windows (`.exe`)
- macOS (`.dmg` — Intel and Apple Silicon)
- Linux (`.AppImage` / `.deb` / `.rpm`)

## 2. Configure the MiMo Provider

Open Cherry Studio and click the gear icon in the lower-left corner to open **Settings**.

1. Open **Model Provider** in the left navigation.
2. Search `mimo` and select **Xiaomi MiMo** from the list.
3. Paste your MiMo API Key into the **API 密钥** (API Key) field (click "检测" to verify connectivity).
4. The API address is pre-filled as `https://api.xiaomimimo.com` — no changes needed.
5. Models are pre-populated (Mimo V2.5, Mimo V2.5 Pro, Mimo V2 Flash) — no manual addition needed.
6. Toggle the switch in the top-right of the provider page to enable it.

## 3. Start Chatting

Open the **Agents** tab from the top navigation, click **+ Agents**, give your agent a name, set **Model** to `mimo-v2.5-pro`, and click **Add**.

Open the new agent and start sending messages.

## Resources

- [Cherry Studio](https://github.com/CherryHQ/cherry-studio) — Open-source desktop AI client.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
