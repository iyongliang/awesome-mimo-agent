[English](./cline.md) | [简体中文](./cline.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Cline

Cline 是一款运行在 VS Code 中的 AI 编程助手扩展，支持多种 API 供应商和模型。MiMo 通过 OpenAI 兼容协议接入 Cline。

## 前置条件

Cline 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Cline 扩展

- 打开 VS Code。
- 点击活动栏中的 **扩展** 图标（或按 `Ctrl+Shift+X`）。
- 搜索 `cline`。
- 在搜索结果中找到 **Cline** 扩展，点击 **Install** 安装。
- 安装完成后，根据提示选择信任开发者。

## 2. 配置 API 供应商

在 Cline 设置中选择 **Bring my own API Key**，然后按如下方式配置：

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

（选做）点击 **Model Configuration**，调整上下文窗口大小、温度、价格和限量等参数。

## 3. 使用 Cline

配置完成后即可在 VS Code 中使用 Cline + MiMo。从侧边栏打开 Cline，开始对话。

## 相关资源

- [Cline](https://github.com/cline/cline) — AI 编程助手 VS Code 扩展。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
