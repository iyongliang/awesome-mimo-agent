[English](./crush.md) | [简体中文](./crush.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Crush

Crush 是由 Charm 开发的开源 AI 编程 Agent，运行在终端中。支持多模型切换、LSP 集成、MCP 服务器和代理式编码工作流。MiMo 通过 OpenAI 兼容协议接入 Crush。

## 前置条件

Crush 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Crush

- 安装 [Node.js](https://nodejs.org/zh-cn/download/)。
- 在命令行界面，执行以下命令安装 Crush：

```bash
npm install -g @charmland/crush
```

- 安装结束后，执行以下命令，若显示版本号则安装成功：

```bash
crush --version
```

> **注意：** macOS 用户也可以通过 Homebrew 安装：`brew install charmbracelet/tap/crush`。

## 2. 配置 MiMo 供应商

Crush 支持通过 OpenAI 兼容 API 添加自定义供应商。在配置文件中添加 MiMo：

- **Linux / macOS**：`~/.config/crush/crush.json`
- **Windows**：`%USERPROFILE%\.config\crush\crush.json`

### 按量付费

前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key（格式：`sk-xxxxx`）。

```json
{
  "$schema": "https://charm.land/crush.json",
  "providers": {
    "mimo": {
      "type": "openai-compat",
      "base_url": "https://api.xiaomimimo.com/v1",
      "api_key": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        }
      ]
    }
  }
}
```

### Token Plan

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。

```json
{
  "$schema": "https://charm.land/crush.json",
  "providers": {
    "mimo": {
      "type": "openai-compat",
      "base_url": "https://token-plan-{region}.xiaomimimo.com/v1",
      "api_key": "$MIMO_API_KEY",
      "models": [
        {
          "id": "mimo-v2.5-pro",
          "name": "MiMo-V2.5-Pro",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        },
        {
          "id": "mimo-v2.5",
          "name": "MiMo-V2.5",
          "context_window": 1048576,
          "default_max_tokens": 131072,
          "can_reason": true
        }
      ]
    }
  }
}
```

设置环境变量：

Linux / Mac：

```bash
export MIMO_API_KEY="<你的 MiMo API Key>"
```

Windows：

```powershell
$env:MIMO_API_KEY="<你的 MiMo API Key>"
```

## 3. 运行并选择模型

进入项目目录并执行 `crush` 命令：

```bash
cd /path/to/my-project
crush
```

- 按 `Ctrl+L`（或输入 `/model`）打开模型切换器。
- 选择 **mimo** 供应商，然后选择 `MiMo-V2.5-Pro` 或 `MiMo-V2.5`。

## 相关资源

- [Crush](https://github.com/charmbracelet/crush) — 开源终端 AI 编程 Agent。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
