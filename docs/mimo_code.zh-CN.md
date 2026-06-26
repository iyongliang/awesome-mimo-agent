[English](./mimo_code.md) | [简体中文](./mimo_code.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 MiMo-Code

MiMo-Code 是小米推出的终端原生 AI 编程助手。它可以读写代码、执行命令、管理 Git，并通过持久化记忆系统在会话间保持对项目的理解。基于 OpenCode 构建，增加了持久化记忆、子 Agent 编排和自我改进等特性。

- **GitHub：** <https://github.com/XiaomiMiMo/MiMo-Code>

## 1. 安装 MiMo-Code

### 快速安装（推荐）

```bash
curl -fsSL https://mimo.xiaomi.com/install | bash
```

### 通过 npm 安装

```bash
npm install -g @mimo-ai/cli
```

验证安装：

```bash
mimo --version
```

## 2. 启动并配置

在项目目录中运行 `mimo`：

```bash
cd /path/to/my-project
mimo
```

首次启动时会引导你完成供应商配置，可选项：

| 配置方式 | 说明 |
|---|---|
| **MiMo Auto** | 免费限时匿名通道，零配置 |
| **Xiaomi MiMo Platform** | OAuth 登录 MiMo 开放平台 |
| **Import from Claude Code** | 迁移已有认证信息 |
| **Custom Provider** | 接入任意 OpenAI 兼容 API |

大多数用户选择 **Xiaomi MiMo Platform**，按提示完成 OAuth 登录即可。

## 3. 基本使用

| 按键 / 命令 | 功能 |
|---|---|
| `Tab` | 切换 Agent：**build**（完整开发权限）、**plan**（只读分析）、**compose**（编排模式） |
| `/goal` | 设置停止条件，由独立裁判评估 |
| `/voice` | 开启流式语音输入（需安装 `sox`） |
| `/dream` | 从历史会话中提取知识写入项目记忆 |
| `/distill` | 将重复工作流转化为可复用技能 |
| `/connect` | 登录额外供应商 |

## 4. 配置文件

配置文件位置：

- **项目级：** `.mimocode/mimocode.json`
- **全局：** `~/.config/mimocode/mimocode.json`

## 相关资源

- [MiMo-Code](https://github.com/XiaomiMiMo/MiMo-Code) — 小米推出的终端原生 AI 编程助手。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
