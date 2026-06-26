[English](./hermes.md) | [简体中文](./hermes.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Hermes Agent

Hermes 是由 Nous Research 构建的自我改进 AI Agent。它内置学习循环：从经验中创建技能、在使用中改进、持久化知识，并跨会话构建用户偏好模型。

## 前置条件

Hermes 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Hermes

### 快速安装

Linux / macOS / WSL2：

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

唯一的前置依赖是 Git，安装脚本会自动处理其他所有依赖。

更多安装方式请参阅 [Hermes 安装页面](https://hermes-agent.nousresearch.com/docs/getting-started/installation)。

## 2. 运行并配置

重新加载终端后开始 Hermes 配置：

```bash
hermes setup
```

1. 选择 **Full setup** — configure every provider, tool & option yourself
2. 在 **Select provider** 列表中选择 **Xiaomi MiMo**（MiMo-V2.5 and V2 models: pro, omni, flash）
3. 按提示输入你的 MiMo API Key
4. 选择模型（如 `mimo-v2.5-pro`）
5. 继续完成剩余选项（工具、偏好等）

## 3. 使用 Hermes

进入项目目录并运行：

```bash
cd /path/to/my-project
hermes
```

## 相关资源

- [Hermes Agent](https://github.com/NousResearch/hermes-agent) — Nous Research 的自我改进 AI Agent。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
