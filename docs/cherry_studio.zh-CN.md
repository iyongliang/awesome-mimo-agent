[English](./cherry_studio.md) | [简体中文](./cherry_studio.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Cherry Studio

Cherry Studio 是一个开源的桌面 AI 客户端，支持 Windows、macOS 和 Linux，统一接入多个 LLM 供应商。内置 300+ 预配置聊天助手、Agent、AI 翻译、知识库和 MCP 服务器。

- **GitHub：** <https://github.com/CherryHQ/cherry-studio>
- **官网：** <https://cherry-ai.com>

## 前置条件

Cherry Studio 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Cherry Studio

从 [Cherry Studio 发布页面](https://github.com/CherryHQ/cherry-studio/releases) 或 [官网](https://cherry-ai.com) 下载对应平台的安装包。

可用版本：

- Windows（`.exe`）
- macOS（`.dmg` — Intel 和 Apple Silicon）
- Linux（`.AppImage` / `.deb` / `.rpm`）

## 2. 配置 MiMo 供应商

打开 Cherry Studio，点击左下角齿轮图标进入 **设置**。

1. 在左侧导航栏打开 **模型供应商**。
2. 搜索 `mimo`，在列表中选择 **Xiaomi MiMo**。
3. 将你的 MiMo API Key 粘贴到 **API 密钥** 字段中（可点击"检测"验证连通性）。
4. API 地址已预填为 `https://api.xiaomimimo.com`，无需修改。
5. 模型列表已预置（Mimo V2.5、Mimo V2.5 Pro、Mimo V2 Flash），无需手动添加。
6. 打开右上角的供应商开关以启用。

## 3. 开始对话

从顶部导航栏打开 **Agents** 标签，点击 **+ Agents**，为 Agent 命名，将 **Model** 设为 `mimo-v2.5-pro`，点击 **Add**。

打开新 Agent，开始发送消息。

## 相关资源

- [Cherry Studio](https://github.com/CherryHQ/cherry-studio) — 开源桌面 AI 客户端。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
