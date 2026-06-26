[English](./oh-my-pi.md) | [简体中文](./oh-my-pi.zh-CN.md) · [← Back](../README.md)

# Integrate with Oh My Pi

[Oh My Pi](https://github.com/can1357/oh-my-pi) is a terminal AI coding agent. MiMo can be configured via a custom `models.yml` file using the OpenAI-compatible endpoint.

## Prerequisites

Both **Pay-as-you-go API** and **Token Plan** are supported. You need to obtain the corresponding credentials before configuration.

| Usage Mode | Description | How to Get Credentials |
|---|---|---|
| **Pay-as-you-go** | Billed by actual usage, suitable for light use | Go to [API Keys](https://platform.xiaomimimo.com/console/api-keys) and create an API Key |
| **Token Plan** | Fixed subscription with quota-based access | After subscribing, go to [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) to get your dedicated Base URL and API Key |

## 1. Install Oh My Pi

Install Oh My Pi following the instructions at: <https://github.com/can1357/oh-my-pi#installation>

## 2. Configure MiMo Provider

Set the API Key environment variable:

```sh
export MIMO_API_KEY=<your MiMo API Key>
```

Create `~/.omp/agent/models.yml`:

### Pay-as-you-go

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

> Replace `{region}` with the cluster shown in your [Subscription Management](https://platform.xiaomimimo.com/console/plan-manage) page (`cn` for China, `sgp` for Singapore, `ams` for Europe).

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

## 3. Usage

```sh
cd /path/to/your-project
omp --model mimo/mimo-v2.5-pro
```

For multimodal support:

```sh
omp --model mimo/mimo-v2.5
```

Switch models inside Oh My Pi with `/model` or `Ctrl+L`.

## Resources

- [Oh My Pi](https://github.com/can1357/oh-my-pi) — Terminal AI coding agent.
- [MiMo Official Website](https://mimo.xiaomi.com/)
- [MiMo Platform](https://platform.xiaomimimo.com/) — API key management and usage.
