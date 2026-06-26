[English](./lobehub.md) | [简体中文](./lobehub.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 LobeHub

LobeHub 是你的首席 Agent 运营官。它将你的 Agent 组织为 7x24 运营，负责招募、调度和汇报你的整个 AI 团队。

- **GitHub：** <https://github.com/lobehub/lobehub>
- **官网：** <https://lobehub.com>
- **Web 应用：** <https://app.lobehub.com>

## 前置条件

LobeHub 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 准备 LobeHub

使用托管的 Web 应用、桌面应用或自部署的 LobeHub 实例：

- Web：打开 [app.lobehub.com](https://app.lobehub.com)。
- 桌面：从 [LobeHub 下载页面](https://lobehub.com/downloads/mac) 下载 macOS 应用。

## 2. 配置 MiMo 供应商

打开 LobeHub，进入 **设置 → AI 服务商**。

1. 搜索 `xiaomi`，在列表中选择 **Xiaomi MiMo**。
2. 打开右上角的开关以启用。
3. 将你的 MiMo API Key 粘贴到 **API Key** 字段中。
4. API 代理地址已预填为 `https://api.xiaomimimo.com/v1`，无需修改。
5. 模型列表已预置（MiMo-V2.5 Pro、MiMo-V2.5 等），无需手动添加。
6. 在 **连通性检查** 中选择一个模型并点击检查，确认显示"检查通过"。

## 3. 选择 MiMo 模型并开始对话

返回 **首页** 或打开任意 Agent 对话。

1. 点击聊天输入工具栏中的当前模型标签。
2. 搜索 `mimo`。
3. 选择 `mimo-v2.5-pro` 用于编码和复杂任务，或选择 `mimo-v2.5` 用于多模态。
4. 发送消息开始对话。

## 4. 可选：自部署环境变量

如果你自部署 LobeHub 并希望服务器全局提供 MiMo 凭证，请参阅 [LobeHub 自部署文档](https://lobehub.com/docs/self-hosting/environment-variables/model-provider) 了解正确的环境变量配置方式。

## 相关资源

- [LobeHub](https://lobehub.com) — AI Agent 运营平台。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
