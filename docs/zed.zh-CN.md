[English](./zed.md) | [简体中文](./zed.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Zed

Zed 是一款高性能代码编辑器，内置 AI 助手功能。MiMo 通过 OpenAI 兼容协议接入 Zed。

## 前置条件

Zed 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Zed

从 [官网](https://zed.dev/download) 下载并安装 Zed。

## 2. 通过 Agent 面板配置（推荐）

### 支持的模型

Zed 仅支持文本生成模型。完整模型列表请参阅 [模型列表](https://platform.xiaomimimo.com/docs/zh-CN/quick-start/model)。

### 2.1 打开 Agent 面板并添加供应商

点击 **Select a model**，然后点击 **Configure** 进入 LLM Providers 页面。点击右上角 **+ Add Provider**，选择 **OpenAI**（Compatible APIs）。

<img src="./assets/zed_llm_providers.png" width="500"/>

### 2.2 填写配置信息（以 `mimo-v2.5-pro` 为例）

#### API URL 和 API Key

根据使用方式选择对应的值：

**按量付费**

| 字段 | 值 |
|---|---|
| **API URL** | `https://api.xiaomimimo.com/v1` |
| **API Key** | 你的 API Key（格式：`sk-xxxxx`），前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 |

**Token Plan**

| 字段 | 值 |
|---|---|
| **API URL** | `https://token-plan-{region}.xiaomimimo.com/v1` |
| **API Key** | 你的 API Key（格式：`tp-xxxxx`），前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取 |

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

#### 其他字段

| 字段 | 值 |
|---|---|
| **Provider Name** | `MiMo` |
| **Model Name** | `mimo-v2.5-pro` |
| **Max Tokens** | `1048576` |
| **Max Completion Tokens** | `131072` |
| **Max Output Tokens** | `131072` |
| **Supports tools** | 勾选 |
| **Supports images** | 模型支持多模态输入时勾选（如 `mimo-v2.5`） |

### 2.3 保存配置

点击 **Save Provider** 保存，LLM Providers 列表中将出现刚添加的供应商。

### 2.4 选择模型开始使用

在 Agent 面板底部的模型选择器中选择 `mimo-v2.5-pro`，点击 **Start New Thread** 即可开始对话。

## 3. 通过 settings.json 配置（可选）

也可以直接在设置文件中配置供应商，无需通过 Agent 面板 GUI。同时也适合设置默认模型等精细化配置。

点击 **Settings**，然后点击 **Edit in settings.json** 打开 `settings.json` 文件。

> 保存正确的 `settings.json` 配置后，自定义供应商会出现在 Agent 面板的 LLM Providers 列表中，API Key 可在该列表中填写。

### 配置 LLM 提供者

#### 按量付费

```json
{
  "language_models": {
    "openai_compatible": {
      "MiMo": {
        "api_url": "https://api.xiaomimimo.com/v1",
        "available_models": [
          {
            "name": "mimo-v2.5-pro",
            "max_tokens": 1048576,
            "max_output_tokens": 131072,
            "max_completion_tokens": 131072,
            "capabilities": {
              "tools": true,
              "images": false,
              "parallel_tool_calls": false,
              "prompt_cache_key": false,
              "chat_completions": true,
              "interleaved_reasoning": false
            }
          },
          {
            "name": "mimo-v2.5",
            "max_tokens": 1048576,
            "max_output_tokens": 131072,
            "max_completion_tokens": 131072,
            "capabilities": {
              "tools": true,
              "images": true,
              "parallel_tool_calls": false,
              "prompt_cache_key": false,
              "chat_completions": true,
              "interleaved_reasoning": false
            }
          }
        ]
      }
    }
  }
}
```

#### Token Plan

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

```json
{
  "language_models": {
    "openai_compatible": {
      "MiMo-TokenPlan": {
        "api_url": "https://token-plan-{region}.xiaomimimo.com/v1",
        "available_models": [
          {
            "name": "mimo-v2.5-pro",
            "max_tokens": 1048576,
            "max_output_tokens": 131072,
            "max_completion_tokens": 131072,
            "capabilities": {
              "tools": true,
              "images": false,
              "parallel_tool_calls": false,
              "prompt_cache_key": false,
              "chat_completions": true,
              "interleaved_reasoning": false
            }
          },
          {
            "name": "mimo-v2.5",
            "max_tokens": 1048576,
            "max_output_tokens": 131072,
            "max_completion_tokens": 131072,
            "capabilities": {
              "tools": true,
              "images": true,
              "parallel_tool_calls": false,
              "prompt_cache_key": false,
              "chat_completions": true,
              "interleaved_reasoning": false
            }
          }
        ]
      }
    }
  }
}
```

## 4. 使用 Zed AI 功能

### Agent 面板

点击状态栏右下角的图标打开 Agent 面板。

<img src="./assets/zed_open_agent_panel.png" width="500"/>

### 内联助手

在编辑器中选中代码，按 `Ctrl+Enter` 获取内联 AI 辅助。

## 相关资源

- [Zed](https://zed.dev/) — 高性能代码编辑器。
- [Zed AI 文档](https://zed.dev/docs/ai/llm-providers) — LLM 提供者配置指南。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
