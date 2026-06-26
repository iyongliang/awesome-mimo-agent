[English](./openclaude.md) | [简体中文](./openclaude.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 OpenClaude

[OpenClaude](https://github.com/Gitlawb/openclaude) 是一个开源 AI 编程助手 CLI，支持多种供应商（OpenAI、Gemini、Ollama、Xiaomi MiMo 等），通过交互式命令配置。

## 前置条件

OpenClaude 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 OpenClaude

需要 **Node.js >= 22.0.0**。

```bash
npm install -g @gitlawb/openclaude@latest
```

验证安装：

```bash
openclaude --version
```

> **注意：** 如果启动后提示 `ripgrep not found`，需额外安装 ripgrep（macOS 下 `brew install ripgrep`，或使用对应包管理器）。

## 2. 配置 MiMo 供应商

启动 OpenClaude 并执行 `/provider` 命令：

```bash
openclaude
```

```
/provider
```

1. 在 **Choose provider preset** 列表中选择 **Xiaomi MiMo**。
2. 端点和高级参数已由预设自动配置（OpenAI-compatible API）。
3. **Step 1 of 2 — Default model**：输入 `mimo-v2.5-pro`
4. **Step 2 of 2 — API Key**：输入你的 MiMo API Key

## 3. 开始使用

配置完成后即可使用 MiMo 编程。启动新会话：

```bash
openclaude
```

## 相关资源

- [OpenClaude](https://github.com/Gitlawb/openclaude) — 开源 AI 编程助手 CLI。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
