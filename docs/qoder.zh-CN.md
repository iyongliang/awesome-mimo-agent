[English](./qoder.md) | [简体中文](./qoder.zh-CN.md) · [← 返回](../README.zh-CN.md)

# 接入 Qoder

[Qoder](https://qoder.com.cn/) ，原灵码Lingma，是阿里云推出的 AI 智能体产品系列，覆盖软件开发与日常办公多元场景，包含面向编码场景的 Qoder CN（含 IDE、JetBrains 插件）、面向日常工作的 QoderWork CN（桌面应用）、Qoder CN CLI（终端原生形态）、QoderWake CN（数字员工）、Qoder Cloud Agents（云端 Agent 平台）等子产品。系列基于国内主流大模型与国内部署，满足金融、政务等行业对数据安全与合规的高要求。

## 前置条件

Qoder 支持 **按量付费 API** 和 **Token Plan** 两种使用方式，配置前需先获取对应凭证。

| 使用方式 | 说明 | 获取凭证 |
|---|---|---|
| **按量付费** | 按实际使用量计费，适合轻度使用 | 前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key |
| **Token Plan** | 固定订阅，按套餐限量调用 | 订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key |

## 1. 安装 Qoder Desktop

从[官网](https://qoder.com.cn/desktop)下载并安装 Qoder Desktop。

详细安装说明请参阅 [Qoder 文档](https://help.aliyun.com/zh/lingma/product-overview/introduction-of-lingma)。

## 2. 添加自定义模型

### 2.1. 支持的模型

Qoder Desktop 支持对话模型和代码补全模型。以下示例以 `mimo-v2.5-pro` 为例，完整模型列表请参阅 [模型列表](https://platform.xiaomimimo.com/docs/zh-CN/quick-start/model)。

### 2.2. 配置步骤

1. 打开 文件 -> 首选项 -> **Qoder 设置**。

2. 在左侧菜单栏 **模型** 下，点击 **添加**。

3. 提供商选择 **Xiaomi MIMO**。

4. 填写配置信息（参考后续[按量付费](#按量付费)或 [Token Plan](#token-plan) 章节）。

5. 点击 **模型选择**，默认支持 Mimo-2.5-Pro 和 Mimo-2.5。

<img src="./assets/qoder_add_model.png" width="500"/>

### 按量付费

添加模型时，类型（Type）要选 “按量付费（Pay As You Go）”，填入对应的按量付费的 API_KEY。

前往 [API Keys](https://platform.xiaomimimo.com/console/api-keys) 创建 API Key（格式：`sk-xxxxx`）。

### Token Plan

订阅成功后，前往 [订阅管理](https://platform.xiaomimimo.com/console/plan-manage) 获取专属 Base URL 和 API Key（格式：`tp-xxxxx`）。

添加模型时，类型要选 “Token Plan”，填入对应的 Token Plan 的 API_KEY。

## 3. 在 Qoder Desktop 中使用 MiMo

1. 打开AI侧边栏。
2. 在对话面板中，从模型下拉列表选择已添加的自定义模型，点击确认。
3. 即可开始使用 MiMo。

## 相关资源

- [Qoder 官网](https://qoder.com.cn/) — 下载与产品信息。
- [Qoder 文档](https://help.aliyun.com/zh/lingma/product-overview/introduction-of-lingma) — 官方指南与参考文档。
- [MiMo 官网](https://mimo.xiaomi.com/)
- [MiMo 开放平台](https://platform.xiaomimimo.com/) — API Key 管理与用量查看。
