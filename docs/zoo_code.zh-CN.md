[English](./zoo_code.md) | [简体中文](./zoo_code.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Zoo Code

Zoo Code 是一款运行在 VS Code 中的 AI 编程助手扩展，支持多种 API 供应商和模型。它由社区维护，是已停止维护的 Roo Code 项目的延续分支。MiMo 通过 OpenAI 兼容协议接入 Zoo Code。

## 前置条件

Zoo Code 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Zoo Code 扩展

- 打开 VS Code。
- 点击活动栏中的 **扩展** 图标（或按 `Ctrl+Shift+X` / `Cmd+Shift+X`）。
- 搜索 `Zoo Code`。
- 在搜索结果中找到 **Zoo Code** 扩展（发布者为 **Zoo Code Organization**），点击 **Install** 安装。
- 安装完成后，从活动栏的图标打开 Zoo Code。

> 对于无法访问 Marketplace 的 VS Code 兼容编辑器（如 VSCodium、Windsurf），可从 [Open VSX Registry](https://open-vsx.org/) 以相同步骤安装 Zoo Code。

## 2. 配置 API 供应商

在 Zoo Code 设置中，按如下方式配置供应商：

- 选择 **API Provider** 为 **OpenAI Compatible**。
- 填入 MiMo API 凭证：

#### 按量付费

前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key（格式：`sk-xxxxx`）。

- **Base URL**：`https://api.xiaomimimo.com/v1`
- **API Key**：你的 MiMo API Key
- **Model ID**：`mimo-v2.5-pro`

#### Token Plan

订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key（格式：`tp-xxxxx`）。

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

- **Base URL**：`https://token-plan-{region}.xiaomimimo.com/v1`
- **API Key**：你的 Token Plan API Key
- **Model ID**：`mimo-v2.5-pro`

#### 支持的模型

| 模型 ID | 说明 |
|---|---|
| `mimo-v2.5-pro` | 文本生成，推理能力最强 |
| `mimo-v2.5` | 多模态（文本 + 图片输入） |

完整模型列表请参阅 [模型列表](https://platform.xiaomimimo.com/docs/zh-CN/quick-start/model)。

（选做）展开 **Model Configuration**，调整上下文窗口大小、最大输出 token、价格等参数。MiMo V2.5 Pro 支持最高 **100 万 tokens** 上下文。

## 3. 使用 Zoo Code

配置完成后即可在 VS Code 中使用 Zoo Code + MiMo。从活动栏打开 Zoo Code，开始对话。可根据任务在 **Code**、**Architect**、**Ask**、**Debug** 等模式之间切换。

## 相关资源

- [Zoo Code](https://github.com/Zoo-Code-Org/Zoo-Code) — AI 编程助手 VS Code 扩展。
- [Zoo Code 文档](https://docs.zoocode.dev/)
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
