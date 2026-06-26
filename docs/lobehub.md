[English](./lobehub.md) | [简体中文](./lobehub.zh-CN.md) · [← Back](../README.md)

# Integrate with LobeHub

LobeHub is your Chief Agent Operator. It organizes your agents into 7x24 operation. It hires, schedules, reports on your entire AI team.

- **GitHub:** <https://github.com/lobehub/lobehub>
- **Website:** <https://lobehub.com>
- **Web app:** <https://app.lobehub.com>

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with LobeHub. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Prepare LobeHub

Use the hosted web app, the desktop app, or a self-hosted LobeHub instance:

- Web: open [app.lobehub.com](https://app.lobehub.com).
- Desktop: download the macOS app from the [LobeHub download page](https://lobehub.com/downloads/mac).

## 2. Configure the MiMo Provider

Open LobeHub and go to **Settings → AI Provider**.

1. Search `xiaomi` and select **Xiaomi MiMo** from the list.
2. Toggle the switch in the upper-right corner to enable it.
3. Paste your MiMo API Key into the **API Key** field.
4. The API proxy address is pre-filled as `https://api.xiaomimimo.com/v1` — no changes needed.
5. Models are pre-populated (MiMo-V2.5 Pro, MiMo-V2.5, etc.) — no manual addition needed.
6. In **Connectivity Check**, select a model and click to verify — it should show "Check Passed".

## 3. Select MiMo Model and Start Chatting

Return to **Home** or open any agent chat.

1. Click the current model chip in the chat input toolbar.
2. Search for `mimo`.
3. Choose `mimo-v2.5-pro` for coding and complex tasks, or `mimo-v2.5` for multimodal use.
4. Send a message to start the conversation.

## 4. Optional: Self-Hosting Environment Variables

If you self-host LobeHub and want the server to provide MiMo credentials globally, refer to the [LobeHub self-hosting documentation](https://lobehub.com/docs/self-hosting/environment-variables/model-provider) for the correct environment variable configuration.

## Resources

- [LobeHub](https://lobehub.com) — AI agent operations platform.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
