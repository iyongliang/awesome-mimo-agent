[English](./copilot_cli.md) | [简体中文](./copilot_cli.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 GitHub Copilot CLI

通过 BYOK（Bring Your Own Key）模式将 GitHub Copilot CLI 配置为使用 MiMo 模型，走 OpenAI 兼容端点。

## 前置条件

GitHub Copilot CLI 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 GitHub Copilot CLI

```shell
npm install -g @github/copilot
```

需要 Node.js 22 或更高版本。详见[官方入门指南](https://docs.github.com/en/copilot/how-tos/copilot-cli/cli-getting-started)。

## 2. 配置环境变量

### 按量付费

前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key（格式：`sk-xxxxx`）。

Linux / Mac：

```shell
export COPILOT_PROVIDER_TYPE=openai
export COPILOT_PROVIDER_BASE_URL=https://api.xiaomimimo.com/v1
export COPILOT_PROVIDER_API_KEY=sk-your-mimo-api-key
export COPILOT_MODEL=mimo-v2.5-pro
```

Windows (PowerShell)：

```powershell
$env:COPILOT_PROVIDER_TYPE="openai"
$env:COPILOT_PROVIDER_BASE_URL="https://api.xiaomimimo.com/v1"
$env:COPILOT_PROVIDER_API_KEY="sk-your-mimo-api-key"
$env:COPILOT_MODEL="mimo-v2.5-pro"
```

### Token Plan

订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key（格式：`tp-xxxxx`）。

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

Linux / Mac：

```shell
export COPILOT_PROVIDER_TYPE=openai
export COPILOT_PROVIDER_BASE_URL=https://token-plan-{region}.xiaomimimo.com/v1
export COPILOT_PROVIDER_API_KEY=tp-your-token-plan-key
export COPILOT_MODEL=mimo-v2.5-pro
```

Windows (PowerShell)：

```powershell
$env:COPILOT_PROVIDER_TYPE="openai"
$env:COPILOT_PROVIDER_BASE_URL="https://token-plan-{region}.xiaomimimo.com/v1"
$env:COPILOT_PROVIDER_API_KEY="tp-your-token-plan-key"
$env:COPILOT_MODEL="mimo-v2.5-pro"
```

可用模型：`mimo-v2.5-pro`、`mimo-v2.5`。修改 `COPILOT_MODEL` 即可切换。

## 3. 启动 Copilot CLI

```shell
copilot
```

完整的 Agent 模式、工具调用和 MCP 支持——全部由 MiMo 驱动。

## 相关资源

- [GitHub Copilot CLI BYOK 文档](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/use-byok-models)
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
