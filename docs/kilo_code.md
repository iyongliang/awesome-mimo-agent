[English](./kilo_code.md) | [简体中文](./kilo_code.zh-CN.md) · [← Back](../README.md)

# Integrate with Kilo Code

Kilo Code is an AI coding assistant available as a CLI and editor extension.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported with Kilo Code. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Kilo Code CLI

- Install [Node.js](https://nodejs.org/en/download/).
- Run the following command in your terminal to install Kilo Code CLI:

```bash
npm install -g @kilocode/cli
```

- After installation, run the following command. If the version number is displayed, the installation is successful:

```bash
kilo --version
```

## 2. Run Kilo Code

Enter the project directory and run `kilo`:

```bash
cd /path/to/my-project
kilo
```

## 3. Connect the MiMo Provider

Type `/connect` in the command bar to open the **Connect Provider** panel. Search for `xiaomi` to filter the provider list:

| Provider | Usage Mode |
|---|---|
| **Xiaomi** | Pay-as-you-go |
| **Xiaomi Token Plan (China)** | Token Plan — China cluster |
| **Xiaomi Token Plan (Europe)** | Token Plan — Europe cluster |
| **Xiaomi Token Plan (Singapore)** | Token Plan — Singapore cluster |

Select the provider matching your usage mode and enter your MiMo API Key when prompted.

## 4. Select the Model

Type `/models` to open the model selector and choose `mimo-v2.5-pro` or `mimo-v2.5`.

## Resources

- [Kilo Code](https://kilocode.ai/) — AI coding assistant CLI and extension.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
