[English](./qwen_code.md) | [简体中文](./qwen_code.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Qwen Code

Qwen Code 是由阿里巴巴 Qwen 团队开发的开源终端 AI Agent。

- **GitHub：** <https://github.com/QwenLM/qwen-code>
- **文档：** <https://qwenlm.github.io/qwen-code-docs/en/users/overview/>

## 前置条件

Qwen Code 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Qwen Code

- 安装 [Node.js](https://nodejs.org/zh-cn/download/) 20 或更高版本。
- 安装 Qwen Code：

```bash
npm install -g @qwen-code/qwen-code@latest
```

或通过快速安装脚本：

```bash
curl -fsSL https://qwen-code-assets.oss-cn-hangzhou.aliyuncs.com/installation/install-qwen-standalone.sh | bash
```

或 Homebrew：

```bash
brew install qwen-code
```

- 验证安装：

```bash
qwen --version
```

## 2. 通过 /auth 配置 MiMo

启动 Qwen Code：

```bash
qwen
```

在交互式会话中执行 `/auth`：

```
/auth
```

选择 **Custom Provider**，按 6 步向导填写：

| 步骤 | 字段 | 填写内容 |
|---|---|---|
| 1 | Protocol | OpenAI Compatible |
| 2 | Base URL | `https://api.xiaomimimo.com/v1`（按量付费）或 `https://token-plan-{region}.xiaomimimo.com/v1`（Token Plan） |
| 3 | API Key | 你的 MiMo API Key |
| 4 | Model ID | `mimo-v2.5-pro` |
| 5 | Advanced Config | Enable thinking: **开启**；Enable modality: 关闭；上下文窗口: `1048576` |
| 6 | Provider Name | `MiMo`（或你喜欢的名称） |

## 3. 切换到 MiMo 模型

执行 `/model` 命令并选择 `mimo-v2.5-pro`：

```
/model
```

配置完成，Qwen Code 将使用 MiMo 进行编码。

> **提示：** 随时使用 `/model` 切换模型。需要重新配置时使用 `/auth`。

## 相关资源

- [Qwen Code](https://github.com/QwenLM/qwen-code) — 开源终端 AI 编程 Agent。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
