[English](./codex.md) | [简体中文](./codex.zh-CN.md) · [← 返回](../README.zh-CN.md)

# Codex 配置指南

**按量付费 MiMo API** 和 **Token Plan** 均支持 Codex。请参阅本指南完成配置与使用。

> MiMo 现已支持 Responses API。正在使用 Chat Completions API 的用户可参照本文档进行更新。

## 前置条件

### 获取凭证

支持两种使用方式，凭证获取方式有所不同：

| 使用方式 | 说明 | 获取方式 |
|---|---|---|
| 按量付费 API | 按实际使用量计费，适合轻度使用 | BASE_URL：`https://api.xiaomimimo.com/v1` / API Key 格式：`sk-xxxxx` — 前往 [API Keys](https://platform.xiaomimimo.com/#/console/api-keys) 创建 API Key |
| Token Plan | 固定订阅费用，按套餐限量调用 | BASE_URL：`https://token-plan-cn.xiaomimimo.com/v1` / API Key 格式：`tp-xxxxx` — 订阅成功后，前往 [Token Plan](https://platform.xiaomimimo.com/#/console/plan-manage) 获取专属 Base URL 和 API Key |

## 安装 Codex

**前置条件：** 需先安装 Node.js 18 或更高版本。

**安装命令：**

```bash
npm install -g @openai/codex
```

**验证安装（输出版本号即表示成功）：**

```bash
codex --version
```

## 编辑配置文件

> **注意**
> - 配置基本信息时，请先检查 `MIMO_API_KEY` 环境变量是否已存在。如已存在，请清除或替换为通过对应使用方式获取的 API Key。
> - 如需通过 `/model` 命令直接切换模型，请参阅"延伸阅读 - 自定义 MiMo 模型配置"章节，配置 `model-catalogs.json` 文件。

配置文件路径：

- macOS/Linux：`~/.codex/config.toml`
- Windows：`用户目录\.codex\config.toml`

以下为完整配置示例。`model` 字段可按需更改为其他支持的模型（如 `mimo-v2.5`）。

### 按量付费

**1. 编辑或创建配置文件** `config.toml`

```toml
model = "mimo-v2.5-pro"
model_provider = "mimo"
model_reasoning_effort = "high"

# 启用模型推理摘要；设为 false 时，即使配置了 model_reasoning_effort 也不会生效
model_supports_reasoning_summaries = true
model_reasoning_summary = "none"
model_context_window = 1048576

web_search = "disabled"

[model_providers.mimo]
name = "mimo"
base_url = "https://api.xiaomimimo.com/v1"
env_key = "MIMO_API_KEY"
wire_api = "responses"
```

**2. 配置环境变量** `MIMO_API_KEY`

按量付费使用以 `sk-` 开头的 API Key。

- macOS/Linux

   ```bash
   echo 'export MIMO_API_KEY="sk-your-api-key-here"' >> ~/.bashrc
   source ~/.bashrc
   ```

- Windows (CMD)

   ```bash
   # 在 CMD 中执行以下命令
   setx MIMO_API_KEY "sk-your-api-key-here"

   # 成功后，打开新的命令提示符并执行以下命令验证变量已设置
   echo %MIMO_API_KEY%
   ```

### Token Plan

**1. 编辑或创建配置文件** `config.toml`

```toml
model = "mimo-v2.5-pro"
model_provider = "mimo"
model_reasoning_effort = "high"

# 启用模型推理摘要；设为 false 时，即使配置了 model_reasoning_effort 也不会生效
model_supports_reasoning_summaries = true
model_reasoning_summary = "none"
model_context_window = 1048576

web_search = "disabled"

[model_providers.mimo]
name = "mimo"
base_url = "https://token-plan-cn.xiaomimimo.com/v1"
env_key = "MIMO_API_KEY"
wire_api = "responses"
```

**2. 配置环境变量** `MIMO_API_KEY`

Token Plan 使用以 `tp-` 开头的 API Key。

- macOS/Linux

   ```bash
   echo 'export MIMO_API_KEY="tp-your-api-key-here"' >> ~/.bashrc
   source ~/.bashrc
   ```

- Windows (CMD)

   ```bash
   # 在 CMD 中执行以下命令
   setx MIMO_API_KEY "tp-your-api-key-here"

   # 成功后，打开新的命令提示符并执行以下命令验证变量已设置
   echo %MIMO_API_KEY%
   ```

## 使用 Codex CLI

完成以上配置后，打开新终端并运行以下命令启动 Codex。

```bash
codex
```

## 使用 Codex IDE 插件

Codex 提供 VS Code 插件。在 VS Code 扩展市场搜索 "Codex" 即可安装。该插件会自动复用本地已有的 Codex 配置。如果您从未使用过 Codex 命令行工具，请按照"编辑配置文件"章节的规范完成配置。

## 延伸阅读

### 自定义 MiMo 模型配置

Codex 支持自定义模型参数配置，可对 MiMo 模型进行精细化和个性化适配。配置完成后，在 Codex CLI 中输入 `/model` 即可在模型列表中看到 MiMo 模型及其对应推理级别，并随时切换。

#### 关键字段说明

| 字段 | 说明 |
|---|---|
| `slug` | 模型唯一内部标识符；必须与后端 API 模型名完全匹配 |
| `display_name` | 前端 UI 显示的模型名称；可与 slug 相同或自定义显示名 |
| `description` | 模型描述文本，用于模型列表悬停提示和模型详情视图 |
| `default_reasoning_level` | 新会话默认推理强度级别。对于 MiMo 模型，`none` 关闭思考；其他值启用思考 |
| `supported_reasoning_levels` | 用户可切换的推理强度配置列表，包含 effort 标识符和描述文本。示例提供 `none` 和 `high` |
| `shell_type` | 工具执行环境类型。示例使用 `"shell_command"`，表示支持 Shell 命令工具 |
| `visibility` | 客户端 UI 中的模型可见性策略；`list` 表示正常显示 |
| `supported_in_api` | 模型是否对标准 API 调用开放；`true` 表示外部程序可通过 API 调用 |
| `priority` | UI 排序权重；数字越小排位越靠前，`1` 表示高优先级置顶 |
| `base_instructions` | 系统提示词 |
| `supports_reasoning_summaries` | 模型是否支持推理摘要输出。为 `true` 时请求携带推理参数；为 `false` 时清除所有推理字段，推理级别（`reasoning_level`）配置也将失效 |
| `default_reasoning_summary` | 默认推理摘要输出模式；`none` 表示不单独输出推理摘要 |
| `support_verbosity` | 是否支持输出详细度控制；`false` 表示暂不支持文本详细度级别切换 |
| `truncation_policy` | 上下文截断策略；mode 为截断单位，limit 为每次上下文的最大字节限制 |
| `supports_parallel_tool_calls` | 是否支持并行多工具调用；`false` 表示仅支持顺序调用 |
| `supports_image_detail_original` | 图像输入时是否支持原始高分辨率解析；`true` 表示使用完整原始分辨率 |
| `context_window` | 模型标称总上下文窗口大小；`1048576` = 1M 上下文窗口 |
| `max_context_window` | 支持的最大上下文窗口限制 |
| `effective_context_window_percent` | 实际可用上下文百分比；`95` 表示保留 5% 安全缓冲以防超限 |
| `experimental_supported_tools` | 实验性功能工具白名单；空数组 `[]` 表示当前无额外 beta 工具可用 |
| `input_modalities` | 支持的输入模态类型；`["text", "image"]` 表示支持文本 + 图像输入 |
| `supports_search_tool` | 是否支持内置网页搜索工具能力；`false` 表示不支持网页搜索 |

#### 配置步骤

1. 编辑或创建 `~/.codex/model-catalogs/model-catalogs.json` 文件进行 MiMo 模型详细配置（以 `mimo-v2.5-pro` 和 `mimo-v2.5` 为例）

   ```json
   {
     "models": [
       {
         "slug": "mimo-v2.5-pro",
         "display_name": "mimo-v2.5-pro",
         "description": "MiMo-v2.5-Pro: Trillion-parameter Flagship Agent Foundation",
         "default_reasoning_level": "high",
         "supported_reasoning_levels": [
           {
             "effort": "none",
             "description": "Disable Thinking"
           },
           {
             "effort": "high",
             "description": "Enabled Thinking"
           }
         ],
         "shell_type": "shell_command",
         "visibility": "list",
         "supported_in_api": true,
         "priority": 0,
         "base_instructions": "You are MiMo, an AI assistant developed by Xiaomi. Today's date: {date} {week}. Your knowledge cutoff date is December 2024.",
         "supports_reasoning_summaries": true,
         "default_reasoning_summary": "none",
         "support_verbosity": false,
         "truncation_policy": {
           "mode": "bytes",
           "limit": 10000
         },
         "supports_parallel_tool_calls": false,
         "supports_image_detail_original": false,
         "context_window": 1048576,
         "max_context_window": 1048576,
         "effective_context_window_percent": 95,
         "experimental_supported_tools": [],
         "input_modalities": ["text"],
         "supports_search_tool": false
       },
       {
         "slug": "mimo-v2.5",
         "display_name": "mimo-v2.5",
         "description": "MiMo-V2.5: Native Omni-modal Perception Model",
         "default_reasoning_level": "high",
         "supported_reasoning_levels": [
           {
             "effort": "none",
             "description": "Disable Thinking"
           },
           {
             "effort": "high",
             "description": "Enabled Thinking"
           }
         ],
         "shell_type": "shell_command",
         "visibility": "list",
         "supported_in_api": true,
         "priority": 1,
         "base_instructions": "You are MiMo, an AI assistant developed by Xiaomi. Today's date: {date} {week}. Your knowledge cutoff date is December 2024.",
         "supports_reasoning_summaries": true,
         "default_reasoning_summary": "none",
         "support_verbosity": false,
         "truncation_policy": {
           "mode": "bytes",
           "limit": 10000
         },
         "supports_parallel_tool_calls": false,
         "supports_image_detail_original": true,
         "context_window": 1048576,
         "max_context_window": 1048576,
         "effective_context_window_percent": 95,
         "experimental_supported_tools": [],
         "input_modalities": ["text", "image"],
         "supports_search_tool": false
       }
     ]
   }
   ```

2. 在 `config.toml` 文件根级别添加以下配置

   - macOS/Linux

     ```toml
     model_catalog_json = "~/.codex/model-catalogs/model-catalogs.json"
     ```

   - Windows

     ```toml
     model_catalog_json = "用户目录/.codex/model-catalogs/model-catalogs.json"
     ```

## 相关资源

- [MiMo Codex 配置指南](https://mimo.mi.com/docs/en-US/tokenplan/integration/codex-configuration)
- [Codex CLI](https://github.com/openai/codex) — OpenAI 的编程 Agent。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
