---
title: "摘要-Google Prompt Engineering 白皮书"
type: source
tags: [来源, Google, Gemini, 白皮书, 提示工程]
sources: [raw/02-papers/Goolge-Prompt-Engineering-whitepaper.pdf]
last_updated: 2026-04-12
---

## 核心摘要

Google 官方于 2024 年 9 月发布的 Prompt Engineering 白皮书，作者 Lee Boonstra。系统介绍了提示工程的技术原理、配置参数和高级技巧。

**核心内容：**

**1. LLM 输出配置**
- **Temperature**：控制随机性，0 为确定性，高值产生多样结果
- **Top-K**：选择概率最高的 K 个 token
- **Top-P (Nucleus Sampling)**：选择累积概率不超过 P 的 token
- 推荐起点：Temperature=0.2, Top-P=0.95, Top-K=30

**2. 提示技术**
- **Zero-shot**：无示例直接提问，适用于简单明确定义的任务
- **Few-shot**：3-5 个示例引导模型学习模式
- **System Prompting**：设置整体上下文和目的
- **Role Prompting**：分配特定角色（旅行向导、编辑等）
- **Contextual Prompting**：提供具体背景信息

**3. 高级技术**
- **Step-back Prompting**：先问一般性问题再解决具体任务，激活背景知识
- **Chain of Thought (CoT)**：生成中间推理步骤，显著提升数学和逻辑任务
- **Self-consistency**：多次采样取最一致答案
- **Tree of Thoughts (ToT)**：同时探索多条推理路径
- **ReAct (Reason & Act)**：结合推理与外部工具调用的代理范式
- **Automatic Prompt Engineering (APE)**：自动化提示生成和优化

**4. 代码提示**
- 代码生成：明确编程语言和版本
- 代码解释：要求模型逐行解释
- 代码翻译：跨语言代码转换
- 代码调试：识别并修复错误

**最佳实践：**
- 提供高质量、多样化的示例
- 简洁设计优于复杂模板
- 明确指定输出格式
- 使用指令而非约束（"做 X"而非"不要做 Y"）
- 控制最大 token 长度以管理成本

## 关联连接
- [[Prompt_Engineering]] — 提示工程总览
- [[Gemini]] — Google Gemini 模型
- [[Chain_of_Thought]] — 思维链
- [[Tree_of_Thoughts]] — 思维树
- [[ReAct]] — 推理与行动
