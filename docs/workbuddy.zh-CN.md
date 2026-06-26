[English](./workbuddy.md) | [简体中文](./workbuddy.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 WorkBuddy/CodeBuddy

WorkBuddy/CodeBuddy 是一款 AI Agent 编程助手，支持通过本地模型配置文件接入自定义模型。MiMo 可通过 OpenAI 兼容的 Chat Completions API 接入。

## 前置条件

支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 WorkBuddy/CodeBuddy

- 安装并登录 WorkBuddy/CodeBuddy。
- 先打开一个项目文件夹，让应用创建本地配置目录。

## 2. 配置本地模型

创建或编辑用户级配置文件：

- **macOS / Linux**：`~/.workbuddy/models.json`
- **Windows**：`C:\Users\<用户名>\.codebuddy\models.json`

如果只想对单个项目生效，可改为创建项目级配置文件：

```
<项目目录>\.codebuddy\models.json
```

先设置 MiMo API Key 环境变量：

```powershell
setx MIMO_API_KEY "<你的 MiMo API Key>"
```

### 按量付费

```json
{
  "models": [
    {
      "id": "mimo-v2.5-pro",
      "name": "MiMo V2.5 Pro",
      "vendor": "Xiaomi",
      "url": "https://api.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": false,
      "relatedModels": {
        "lite": "mimo-v2.5",
        "reasoning": "mimo-v2.5-pro"
      }
    },
    {
      "id": "mimo-v2.5",
      "name": "MiMo V2.5",
      "vendor": "Xiaomi",
      "url": "https://api.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": true
    }
  ],
  "availableModels": [
    "mimo-v2.5-pro",
    "mimo-v2.5"
  ]
}
```

### Token Plan

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

```json
{
  "models": [
    {
      "id": "mimo-v2.5-pro",
      "name": "MiMo V2.5 Pro",
      "vendor": "Xiaomi",
      "url": "https://token-plan-{region}.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": false,
      "relatedModels": {
        "lite": "mimo-v2.5",
        "reasoning": "mimo-v2.5-pro"
      }
    },
    {
      "id": "mimo-v2.5",
      "name": "MiMo V2.5",
      "vendor": "Xiaomi",
      "url": "https://token-plan-{region}.xiaomimimo.com/v1/chat/completions",
      "apiKey": "${MIMO_API_KEY}",
      "maxInputTokens": 1048576,
      "maxOutputTokens": 131072,
      "supportsToolCall": true,
      "supportsImages": true
    }
  ],
  "availableModels": [
    "mimo-v2.5-pro",
    "mimo-v2.5"
  ]
}
```

保存 `models.json` 时使用 UTF-8 编码（不带 BOM）。

## 3. 重启并选择模型

完全退出 WorkBuddy/CodeBuddy 后重新打开，在模型选择器中选择 **MiMo V2.5 Pro** 或 **MiMo V2.5**。

## 常见问题

- `Authentication Fails` 或 `401`：检查 `apiKey` 是否为你的真实 MiMo API Key。
- `Model Not Found` 或 `404`：检查模型 ID 是否为 `mimo-v2.5-pro` 或 `mimo-v2.5`。
- `Failed to read local model configuration`：检查 `models.json` 是否为合法 JSON，且以 UTF-8 无 BOM 格式保存。
- 模型未出现在选择器中：完全重启 WorkBuddy/CodeBuddy，确认文件放在 `.codebuddy\models.json` 下。

## 相关资源

- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
