[English](./kilo_code.md) | [简体中文](./kilo_code.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Kilo Code

Kilo Code 是一款 AI 编程助手，提供 CLI 和编辑器扩展。

## 前置条件

Kilo Code 支持**按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Kilo Code CLI

- 安装 [Node.js](https://nodejs.org/zh-cn/download/)。
- 在命令行界面，执行以下命令安装 Kilo Code CLI：

```bash
npm install -g @kilocode/cli
```

- 安装结束后，执行以下命令，若显示版本号则安装成功：

```bash
kilo --version
```

## 2. 运行 Kilo Code

进入项目目录并运行 `kilo`：

```bash
cd /path/to/my-project
kilo
```

## 3. 连接 MiMo 供应商

在命令栏输入 `/connect` 打开 **Connect Provider** 面板。搜索 `xiaomi` 筛选供应商列表：

| 供应商 | 使用方式 |
|---|---|
| **Xiaomi** | 按量付费 |
| **Xiaomi Token Plan (China)** | Token Plan — 中国集群 |
| **Xiaomi Token Plan (Europe)** | Token Plan — 欧洲集群 |
| **Xiaomi Token Plan (Singapore)** | Token Plan — 新加坡集群 |

选择与你使用方式对应的供应商，按提示输入 MiMo API Key 即可。

## 4. 选择模型

输入 `/models` 打开模型选择器，选择 `mimo-v2.5-pro` 或 `mimo-v2.5`。

## 相关资源

- [Kilo Code](https://kilocode.ai/) — AI 编程助手 CLI 和扩展。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
