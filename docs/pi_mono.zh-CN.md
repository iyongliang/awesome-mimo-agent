[English](./pi_mono.md) | [简体中文](./pi_mono.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Pi

Pi (pi-mono) 是一个极简、高度可扩展的终端编程工具。通过 TypeScript 扩展、技能、提示词模板和主题适配你的工作流——支持树形结构会话和 15+ 内置供应商。

## 前置条件

Pi 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Pi

- 安装 [Node.js](https://nodejs.org/zh-cn/download/)。
- 在命令行界面，执行以下命令安装 Pi：

```bash
npm install -g @earendil-works/pi-coding-agent
```

- 安装结束后，执行以下命令，若显示版本号则安装成功：

```bash
pi --version
```

> **注意：** Linux / macOS 用户也可通过官方脚本安装：
> ```bash
> curl -fsSL https://pi.dev/install.sh | sh
> ```

## 2. 配置 MiMo 供应商

Pi 通过 `models.json` 支持自定义供应商。将 MiMo 添加为 OpenAI 兼容供应商：

- **Linux / macOS**：`~/.pi/agent/models.json`
- **Windows**：`%USERPROFILE%\.pi\agent\models.json`

### 按量付费

前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key（格式：`sk-xxxxx`）。

```json
{
  "providers": {
    "xiaomi": {
      "baseUrl": "https://api.xiaomimimo.com/v1",
      "api": "openai-completions",
      "apiKey": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 1,
            "output": 3,
            "cacheRead": 0.2,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text", "image"],
          "reasoning": true,
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
        }
      ]
    }
  }
}
```

### Token Plan

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

```json
{
  "providers": {
    "xiaomi": {
      "baseUrl": "https://token-plan-{region}.xiaomimimo.com/v1",
      "api": "openai-completions",
      "apiKey": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 1,
            "output": 3,
            "cacheRead": 0.2,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "contextWindow": 1048576,
          "maxTokens": 131072,
          "input": ["text", "image"],
          "reasoning": true,
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek"
          }
        }
      ]
    }
  }
}
```

设置环境变量：

Linux / Mac：

```bash
export MIMO_API_KEY="<你的 MiMo API Key>"
```

Windows：

```powershell
$env:MIMO_API_KEY="<你的 MiMo API Key>"
```

## 3. 运行并选择模型

进入项目目录并执行 `pi` 命令：

```bash
cd /path/to/my-project
pi
```

- 输入 `/model` 打开模型切换器。
- 选择 **xiaomi**，然后选择 `MiMo-V2.5-Pro` 或 `MiMo-V2.5`。

## 相关资源

- [Pi](https://github.com/badlogic/pi-mono) — 极简终端编程工具。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
