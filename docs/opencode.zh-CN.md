[English](./opencode.md) | [简体中文](./opencode.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 OpenCode

OpenCode 是一个开源的 AI 编程 Agent，支持终端、桌面应用和 IDE 扩展使用。MiMo 推荐通过 OpenAI 兼容协议接入 OpenCode。

## 前置条件

OpenCode 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 OpenCode CLI

需要 [Node.js](https://nodejs.org/en/download/) 18+。

```shell
npm install -g opencode-ai
```

验证安装：

```shell
opencode -v
```

更多安装方式（官方脚本、Homebrew、Chocolatey、Scoop 等）请参阅 [OpenCode 官方文档](https://opencode.ai/docs)。

## 2. 配置 OpenCode

### 通过 `/connect` 快速配置（推荐）

启动 OpenCode 后输入 `/connect`，搜索 `Xiaomi`，选择与你凭证类型匹配的 Provider，填入 API Key 即可。

<img src="./assets/open_code_cli_provider.png" width="600" />

> **Token Plan** 用户需选择与集群区域匹配的 Provider：
> - `https://token-plan-cn.xiaomimimo.com/*` → Xiaomi Token Plan（中国集群）
> - `https://token-plan-sgp.xiaomimimo.com/*` → Xiaomi Token Plan（新加坡集群）
> - `https://token-plan-ams.xiaomimimo.com/*` → Xiaomi Token Plan（欧洲集群）

### 手动配置

也可以直接编辑或创建配置文件：
- macOS / Linux：`~/.config/opencode/opencode.json`
- Windows：`C:\Users\<用户名>\.config\opencode\opencode.json`

#### 支持的模型

完整模型列表请参阅 [模型列表](https://platform.xiaomimimo.com/docs/zh-CN/quick-start/model)。

#### 按量付费

前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key（格式：`sk-xxxxx`）。

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "mimo": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "MiMo",
      "options": {
        "baseURL": "https://api.xiaomimimo.com/v1",
        "apiKey": "MIMO_API_KEY"
      },
      "models": {
        "mimo-v2.5-pro": {
          "name": "mimo-v2.5-pro",
          "limit": {
            "context": 1048576,
            "output": 131072
          }
        },
        "mimo-v2.5": {
          "name": "mimo-v2.5",
          "limit": {
            "context": 1048576,
            "output": 131072
          },
          "modalities": {
            "input": ["text", "image"],
            "output": ["text"]
          }
        }
      }
    }
  },
  "model": "mimo/mimo-v2.5-pro"
}
```

#### Token Plan

订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key（格式：`tp-xxxxx`）。

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "mimo": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "MiMo-TokenPlan",
      "options": {
        "baseURL": "https://token-plan-{region}.xiaomimimo.com/v1",
        "apiKey": "MIMO_API_KEY"
      },
      "models": {
        "mimo-v2.5-pro": {
          "name": "mimo-v2.5-pro",
          "limit": {
            "context": 1048576,
            "output": 131072
          }
        },
        "mimo-v2.5": {
          "name": "mimo-v2.5",
          "limit": {
            "context": 1048576,
            "output": 131072
          },
          "modalities": {
            "input": ["text", "image"],
            "output": ["text"]
          }
        }
      }
    }
  },
  "model": "mimo/mimo-v2.5-pro"
}
```

#### 开启思考模式

MiMo 模型支持深度思考。在模型配置中添加 `thinking` 选项即可开启：

```json
"mimo-v2.5-pro": {
  "name": "mimo-v2.5-pro",
  "limit": {
    "context": 1048576,
    "output": 131072
  },
  "options": {
    "thinking": {
      "type": "enabled"
    }
  }
}
```

> 设置 `"type": "disabled"` 可关闭思考模式。

#### 说明

- 将 `MIMO_API_KEY` 替换为你的实际 API Key。
- `"model": "mimo/mimo-v2.5-pro"` 设置默认模型，格式为 `provider-id/model-id`。
- 启动 OpenCode 后，可通过 `/models` 命令查看和切换可用模型。

## 3. 桌面端（可选）

OpenCode Desktop 目前为 Beta 版，支持 macOS、Windows 和 Linux。从[官方下载页面](https://opencode.ai/download)下载。

桌面端与 CLI 共用同一份配置文件（`~/.config/opencode/opencode.json`）。

## 4. VS Code 扩展（可选）

在 [VS Code 扩展市场](https://marketplace.visualstudio.com/) 搜索 **OpenCode** 并安装。

扩展与 CLI 共用同一份配置文件（`~/.config/opencode/opencode.json`）。

也可以在扩展中使用 `/connect` 命令直接配置 MiMo：
1. 输入 `/connect`，搜索 `Xiaomi`
2. 选择对应的 Provider，填入 API Key

> **Token Plan** 用户需选择与集群区域匹配的 Provider：
> - `https://token-plan-cn.xiaomimimo.com/*` → Xiaomi Token Plan（中国集群）
> - `https://token-plan-sgp.xiaomimimo.com/*` → Xiaomi Token Plan（新加坡集群）
> - `https://token-plan-ams.xiaomimimo.com/*` → Xiaomi Token Plan（欧洲集群）

## 5. 使用 OpenCode

### 使用 OpenCode CLI

进入项目目录，执行：

```shell
cd /path/to/my-project
opencode
```

首次启动时，执行 `/init` 命令可生成 `AGENTS.md` 文件，帮助 OpenCode 理解你的项目结构。

### 使用 OpenCode VS Code 扩展

在 VS Code 中打开项目目录，点击 OpenCode 图标，即可开始对话。

## 相关资源

- [OpenCode](https://opencode.ai/docs) — 开源 AI 编程 Agent。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
