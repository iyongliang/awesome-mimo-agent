[English](./astrbot.md) | [简体中文](./astrbot.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 AstrBot

[AstrBot](https://github.com/AstrBotDevs/AstrBot) 是一个开源全能 Agent 助手，可接入 QQ、微信、飞书、Telegram 等主流消息平台，支持技能、插件和 MCP 扩展。

## 前置条件

AstrBot 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 AstrBot

### 通过 uv 安装

macOS 和 Linux 用户：

```bash
curl -LsSf https://docs.astrbot.app/install.sh | bash
```

Windows 用户：

```bash
iwr -useb https://docs.astrbot.app/install.ps1 | iex
```

然后初始化并启动 AstrBot：

```bash
astrbot init
astrbot run
```

### 通过 Docker 安装

```bash
git clone https://github.com/AstrBotDevs/AstrBot --depth 1
cd AstrBot
sudo docker compose up -d
```

## 2. 配置默认模型

初始化后打开 Web UI：

```
http://localhost:6185
```

在左侧边栏打开 **模型提供商** 页面，点击 **+ 新增**。

在提供商下拉列表中选择 **Xiaomi**（按量付费）或 **Xiaomi Token Plan**（Token Plan），API Base URL 会自动填充。

填写：

- **API Key**：你的 MiMo API Key

点击 **保存配置**。

## 3. 开始使用

点击右上角 **Chat** 切换到 AstrBot 聊天界面，即可开始与 MiMo 对话。

你也可以配置消息平台，从常用聊天应用中直接使用 AstrBot。详见 [AstrBot 文档](https://docs.astrbot.app/)。

## 相关资源

- [AstrBot](https://github.com/AstrBotDevs/AstrBot) — 开源全能 Agent 助手。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
