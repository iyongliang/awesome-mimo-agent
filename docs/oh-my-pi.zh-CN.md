[English](./oh-my-pi.md) | [简体中文](./oh-my-pi.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Oh My Pi

[Oh My Pi](https://github.com/can1357/oh-my-pi) 是一个终端 AI 编程 Agent。MiMo 可通过自定义 `models.yml` 文件使用 OpenAI 兼容端点接入。

## 前置条件

支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Oh My Pi

按照以下链接安装：<https://github.com/can1357/oh-my-pi#installation>

## 2. 配置 MiMo 供应商

设置 API Key 环境变量：

```sh
export MIMO_API_KEY=<你的 MiMo API Key>
```

创建 `~/.omp/agent/models.yml`：

### 按量付费

```yaml
providers:
  mimo:
    baseUrl: https://api.xiaomimimo.com/v1
    api: openai-completions
    apiKey: MIMO_API_KEY
    authHeader: true
    models:
      - id: mimo-v2.5-pro
        name: MiMo-V2.5-Pro
        reasoning: true
        input: [text]
        contextWindow: 1048576
        maxTokens: 131072
        compat:
          supportsDeveloperRole: false
          supportsReasoningEffort: true
          maxTokensField: max_tokens
          supportsToolChoice: false
          requiresReasoningContentForToolCalls: true
          requiresAssistantContentForToolCalls: true
          extraBody:
            thinking:
              type: enabled
      - id: mimo-v2.5
        name: MiMo-V2.5
        reasoning: true
        input: [text, image]
        contextWindow: 1048576
        maxTokens: 131072
        compat:
          supportsDeveloperRole: false
          supportsReasoningEffort: true
          maxTokensField: max_tokens
          supportsToolChoice: false
          requiresReasoningContentForToolCalls: true
          requiresAssistantContentForToolCalls: true
          extraBody:
            thinking:
              type: enabled
```

### Token Plan

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

```yaml
providers:
  mimo:
    baseUrl: https://token-plan-{region}.xiaomimimo.com/v1
    api: openai-completions
    apiKey: MIMO_API_KEY
    authHeader: true
    models:
      - id: mimo-v2.5-pro
        name: MiMo-V2.5-Pro
        reasoning: true
        input: [text]
        contextWindow: 1048576
        maxTokens: 131072
        compat:
          supportsDeveloperRole: false
          supportsReasoningEffort: true
          maxTokensField: max_tokens
          supportsToolChoice: false
          requiresReasoningContentForToolCalls: true
          requiresAssistantContentForToolCalls: true
          extraBody:
            thinking:
              type: enabled
      - id: mimo-v2.5
        name: MiMo-V2.5
        reasoning: true
        input: [text, image]
        contextWindow: 1048576
        maxTokens: 131072
        compat:
          supportsDeveloperRole: false
          supportsReasoningEffort: true
          maxTokensField: max_tokens
          supportsToolChoice: false
          requiresReasoningContentForToolCalls: true
          requiresAssistantContentForToolCalls: true
          extraBody:
            thinking:
              type: enabled
```

## 3. 使用

```sh
cd /path/to/your-project
omp --model mimo/mimo-v2.5-pro
```

多模态支持：

```sh
omp --model mimo/mimo-v2.5
```

在 Oh My Pi 内可通过 `/model` 或 `Ctrl+L` 切换模型。

## 相关资源

- [Oh My Pi](https://github.com/can1357/oh-my-pi) — 终端 AI 编程 Agent。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
