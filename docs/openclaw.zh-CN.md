[English](./openclaw.md) | [简体中文](./openclaw.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 OpenClaw

OpenClaw 是一个开源的个人 AI 助手，可接入飞书、微信等主流聊天工具，并通过 Skills 扩展功能。

## 前置条件

OpenClaw 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 OpenClaw

Linux / Mac：

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

Windows：

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

## 2. 配置默认模型

首次安装后会自动进入配置阶段。已安装的用户可通过 `openclaw onboard --install-daemon` 重新进入配置。

按 onboard 向导操作：

1. **Model/auth provider** → 选择 **Xiaomi**
2. **Xiaomi auth method** → 选择 **Xiaomi API key (Pay-as-you-go)**
3. **Enter Xiaomi MiMo API key** → 粘贴你的 API Key（以 `sk-` 开头）
4. 向导默认设置模型为 `xiaomi/mimo-v2-flash`。选择 **手动输入模型** 并输入 `xiaomi/mimo-v2.5-pro`
5. 其余配置（消息通道、Skills 等）按需设置

## 3. 开始使用

打开 Web UI：

```bash
openclaw dashboard
```

在终端打开 TUI：

```bash
openclaw tui
```

在终端中聊天：

```bash
openclaw terminal
```

## 相关资源

- [OpenClaw](https://github.com/openclaw/openclaw) — 开源个人 AI 助手。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
