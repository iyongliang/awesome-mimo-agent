[English](./nanobot.md) | [简体中文](./nanobot.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 nanobot

nanobot 是一个轻量级 AI Agent，支持与主流聊天工具集成。MiMo 通过 OpenAI 兼容协议接入 nanobot。

## 前置条件

nanobot 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 nanobot

- 安装 [uv](https://github.com/astral-sh/uv)。
- 执行以下命令安装 nanobot：

```bash
uv tool install nanobot-ai
```

- 注意：Windows 用户需将用户主目录下的 `.local/bin` 添加到环境变量：

```powershell
$env:PATH = "$env:USERPROFILE\.local\bin;$env:PATH"
```

- 或通过 `uv` 更新终端：

```powershell
uv tool update-shell
```

- 安装结束后，执行以下命令，若显示版本号则安装成功：

```bash
nanobot --version
```

## 2. 配置 nanobot

执行以下命令初始化 nanobot 配置文件：

```bash
nanobot onboard
```

配置文件路径因操作系统而异：

- **Windows**：`$env:USERPROFILE\.nanobot\config.json`
- **Linux / macOS**：`~/.nanobot/config.json`

编辑 `config.json` 文件：

> nanobot 内置 `xiaomi_mimo` 供应商，当模型名包含 `mimo` 时会自动识别。默认 API Base 为 `https://api.xiaomimimo.com/v1`，按量付费方式无需手动指定。

### 按量付费

前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key（格式：`sk-xxxxx`）。

```json
{
    "providers": {
        "xiaomi_mimo": {
            "apiKey": "${XIAOMIMIMO_API_KEY}"
        }
    },
    "modelPresets": {
        "mimo": {
            "provider": "xiaomi_mimo",
            "model": "xiaomi/mimo-v2.5-pro"
        }
    },
    "agents": {
        "defaults": {
            "modelPreset": "mimo"
        }
    }
}
```

### Token Plan

> 将 `{region}` 替换为 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 页面中显示的集群标识（`cn` 中国集群、`sgp` 新加坡集群、`ams` 欧洲集群）。使用 Token Plan 时需用专属端点覆盖 `apiBase`。

```json
{
    "providers": {
        "xiaomi_mimo": {
            "apiKey": "${XIAOMIMIMO_API_KEY}",
            "apiBase": "https://token-plan-{region}.xiaomimimo.com/v1"
        }
    },
    "modelPresets": {
        "mimo": {
            "provider": "xiaomi_mimo",
            "model": "xiaomi/mimo-v2.5-pro"
        }
    },
    "agents": {
        "defaults": {
            "modelPreset": "mimo"
        }
    }
}
```

## 3. 设置环境变量

配置文件中的 `${XIAOMIMIMO_API_KEY}` 会从环境变量读取，运行前先设置：

Linux / macOS：

```bash
export XIAOMIMIMO_API_KEY="<你的 MiMo API Key>"
```

Windows：

```powershell
$env:XIAOMIMIMO_API_KEY="<你的 MiMo API Key>"
```

## 4. 开始使用

在终端中运行：

```bash
nanobot agent
```

## 相关资源

- [nanobot](https://github.com/nanobot-ai/nanobot) — 轻量级 AI Agent。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
