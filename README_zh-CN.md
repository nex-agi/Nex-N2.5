<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./figures/NEX_logo-dark.svg">
    <img src="./figures/NEX_logo.svg" width="180" alt="Nex-AGI">
  </picture>

# Nex-N2.5

**为能浏览网页、编写代码、操作电脑的智能体而生。**

多模态 mini / Pro · 1.6 万亿参数纯文本 Max · 面向长程智能体任务

[![体验 Pro](https://img.shields.io/badge/Try_Pro-OpenRouter-2563EB?style=for-the-badge)](https://openrouter.ai/nex-agi/nex-n2.5-pro:free) [![体验 mini](https://img.shields.io/badge/Try_mini-OpenRouter-2563EB?style=for-the-badge)](https://openrouter.ai/nex-agi/nex-n2.5-mini:free)

[模型下载](#模型选择与下载) · [快速开始](#快速开始) · [完整评测](./README.md#performance) · [本地部署](./README.md#usage) · [官网](https://nex-agi.com/)

[English](./README.md) | **简体中文**

⭐ **正在开发智能体？[点个 Star](https://github.com/nex-agi/Nex-N2.5)，收藏模型、评测与部署指南。**

</div>

Nex-N2.5 是 Nex-AGI 面向多步骤任务的模型系列，覆盖网页检索、软件操作、代码编写与测试、工具调用等场景。**mini 和 Pro** 能通过视觉反馈理解界面、检查操作结果；**Max** 基于 1.6 万亿参数的混合专家（MoE）纯文本模型，面向编程、研究和工具使用。

## 核心表现

| 网页研究 | GUI 定位 | 电脑操作 |
| :---: | :---: | :---: |
| **92.6** · BrowseComp | **87.4** · OSWorld-G | **82.2** · OSWorld-Verified |
| Nex-N2.5-Max | Nex-N2.5-Pro | Nex-N2.5-Pro |

以上为本仓库报告的部分评测成绩。在评测表列出的模型中，Max 的 BrowseComp 成绩和 Pro 的 OSWorld-G 成绩最高。完整对比、分数来源、评测框架及采样设置见[英文 README 的评测部分](./README.md#performance)。

- **开发电脑与浏览器智能体。** mini 和 Pro 结合视觉理解、动作与反馈，支持需要观察界面并调整下一步操作的任务。
- **连接编程与研究工具。** 系列模型支持函数调用，编程评测使用开源的 [NexAU 智能体框架](https://github.com/nex-agi/NexAU)。
- **从在线体验到自行部署。** Pro 和 mini 可通过 OpenRouter 体验；mini 和 Max 已提供权重，Pro 的权重发布状态见下表。

## 快速开始

### 在线体验

打开 **[Nex-N2.5-Pro](https://openrouter.ai/nex-agi/nex-n2.5-pro:free)** 或 **[Nex-N2.5-mini](https://openrouter.ai/nex-agi/nex-n2.5-mini:free)** 的 OpenRouter 页面即可开始体验，无需自行部署 GPU。当前路线标注为免费，需要 OpenRouter 账号，并受其使用额度限制。

可以从这个任务开始：*“检查下面的函数有哪些边界情况，给出修复，并写出能发现这些问题的测试。”* 在提示词后粘贴你的函数。

### 发起第一条 API 请求

创建 [OpenRouter API Key](https://openrouter.ai/settings/keys)，设置 `OPENROUTER_API_KEY`，在 Bash 中运行：

```bash
export OPENROUTER_API_KEY="your-api-key"

curl --fail-with-body https://openrouter.ai/api/v1/chat/completions \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "nex-agi/nex-n2.5-pro:free",
    "messages": [
      {
        "role": "user",
        "content": "写一个合并重叠区间的 Python 函数，并为输入为空、区间首尾相接、区间嵌套的情况编写测试。"
      }
    ],
    "temperature": 0.7,
    "top_p": 0.95,
    "top_k": 40,
    "reasoning": {"effort": "medium"}
  }'
```

将 `model` 改为 `nex-agi/nex-n2.5-mini:free` 即可调用 mini。模型 ID 和服务可用性可能变化，请以 [OpenRouter 模型目录](https://openrouter.ai/api/v1/models)为准。其他语言和流式调用方式见 [API 指南](https://openrouter.ai/docs/quickstart)。

如果希望智能体实际浏览网页、点击界面或执行代码，还需接入智能体运行框架和相应工具；单次聊天请求本身不会执行这些操作。编程评测使用 [NexAU](https://github.com/nex-agi/NexAU)，电脑操作评测框架 NexCUA 计划开源。

## 模型选择与下载

| 模型 | 适用方向 | 原生输入 | 在线体验 |
| --- | --- | --- | --- |
| **Nex-N2.5-mini** | 部署规模较小的电脑与浏览器智能体 | 文本 + 图像 | [OpenRouter](https://openrouter.ai/nex-agi/nex-n2.5-mini:free) |
| **Nex-N2.5-Pro** | 视觉智能体、GUI 定位与电脑操作 | 文本 + 图像 | [OpenRouter](https://openrouter.ai/nex-agi/nex-n2.5-pro:free) |
| **Nex-N2.5-Max** | 1.6 万亿参数规模的文本研究、编程与工具使用 | 仅文本 | 自行部署 |

托管服务开放的输入类型可能少于模型原生支持的类型。截至 **2026-09-09**，OpenRouter 将 Pro 标注为支持文本与图像输入，mini 标注为仅支持文本输入。

下表的发布状态于 **2026-09-09** 根据 Hugging Face 文件列表核对。各模型卡标注的许可证为 **Apache-2.0**，使用权重时请查阅相应模型卡及许可证。

| 模型 | Hugging Face 发布状态 | 下载 / 模型卡 | 参考部署配置 |
| --- | --- | --- | --- |
| **mini** | 权重已发布 | [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-mini) · [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-mini) | 单节点 · 2 × H100 |
| **Pro** | 已有模型卡，权重待发布 | [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Pro) · [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-Pro) | 单节点 · 8 × H100 |
| **Max** | 权重已发布 | [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Max) · [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-Max) | 双节点 · 共 16 × H200 |

以上为参考配置，并非最低硬件要求。全部模型卡见 [Hugging Face 合集](https://huggingface.co/collections/nex-agi/nex-n25)。

## 评测与部署指南

完整技术细节统一维护在英文 README 中：

- [完整评测](./README.md#performance)：文本与多模态对比表、评测口径及来源说明。
- [Docker 部署](./README.md#docker-deployment)：mini、Pro 和 Max 的启动配置。
- [请求本地服务](./README.md#send-a-request-to-your-server)：端口和模型 ID 查询。
- [采样参数](./README.md#recommended-sampling-parameters)：`temperature=0.7`、`top_p=0.95`、`top_k=40`。
- [思考模式](./README.md#thinking-modes)：OpenRouter、mini 和 Max 模板的参数差异。
- [函数调用](./README.md#function-calling)：工具调用解析与执行流程。

## 一起使用和改进

欢迎[分享使用案例或提交问题](https://github.com/nex-agi/Nex-N2.5/issues)。请附上模型版本、运行框架和复现步骤，让其他开发者也能尝试。

如果项目对你有用，欢迎 **[点个 Star](https://github.com/nex-agi/Nex-N2.5)**，也可以把仓库分享给正在开发智能体的朋友。需要接收仓库动态通知时，可通过 GitHub 的 **Watch** 菜单设置。
