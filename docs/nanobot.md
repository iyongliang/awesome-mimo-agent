[English](./nanobot.md) | [简体中文](./nanobot.zh-CN.md) · [← Back](../README.md)

# Integrate with nanobot

nanobot is a lightweight AI agent that supports integration with popular chat tools. MiMo integrates with nanobot via the OpenAI-compatible protocol.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with nanobot. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install nanobot

- Install [uv](https://github.com/astral-sh/uv).
- Run the following command to install nanobot:

```bash
uv tool install nanobot-ai
```

- Note: On Windows, add the `.local/bin` directory under your user home directory to the environment variables:

```powershell
$env:PATH = "$env:USERPROFILE\.local\bin;$env:PATH"
```

- Or update the terminal via `uv`:

```powershell
uv tool update-shell
```

- After installation, run the following command. If a version number is displayed, the installation was successful:

```bash
nanobot --version
```

## 2. Configure nanobot

Run the following command to initialize the nanobot configuration file:

```bash
nanobot onboard
```

The configuration file path varies by operating system:

- **Windows**: `$env:USERPROFILE\.nanobot\config.json`
- **Linux / macOS**: `~/.nanobot/config.json`

Edit the `config.json` file:

> nanobot has a built-in `xiaomi_mimo` provider that is auto-detected when the model name contains `mimo`. The default API base is `https://api.xiaomimimo.com/v1`, so there is no need to set it manually for pay-as-you-go.

### Pay-as-you-go

Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key (format: `sk-xxxxx`).

```json
{
    "providers": {
        "xiaomi_mimo": {
            "apiKey": "${XIAOMIMIMO_API_KEY}"
        }
    },
    "modelPresets": {
        "mimo": {
            "provider": "xiaomi_mimo",
            "model": "xiaomi/mimo-v2.5-pro"
        }
    },
    "agents": {
        "defaults": {
            "modelPreset": "mimo"
        }
    }
}
```

### Token Plan

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe). With Token Plan, override `apiBase` with the dedicated endpoint.

```json
{
    "providers": {
        "xiaomi_mimo": {
            "apiKey": "${XIAOMIMIMO_API_KEY}",
            "apiBase": "https://token-plan-{region}.xiaomimimo.com/v1"
        }
    },
    "modelPresets": {
        "mimo": {
            "provider": "xiaomi_mimo",
            "model": "xiaomi/mimo-v2.5-pro"
        }
    },
    "agents": {
        "defaults": {
            "modelPreset": "mimo"
        }
    }
}
```

## 3. Set the Environment Variable

The `${XIAOMIMIMO_API_KEY}` in the config file is read from an environment variable. Set it before running:

Linux / macOS:

```bash
export XIAOMIMIMO_API_KEY="<your MiMo API Key>"
```

Windows:

```powershell
$env:XIAOMIMIMO_API_KEY="<your MiMo API Key>"
```

## 4. Get Started

Run in the terminal:

```bash
nanobot agent
```

## Resources

- [nanobot](https://github.com/nanobot-ai/nanobot) — Lightweight AI agent.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
