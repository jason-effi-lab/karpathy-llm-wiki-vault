---
title: "摘要-Gemini API 提示设计策略"
type: source
tags: [来源, Gemini, Google, 提示工程]
sources: [raw/01-articles/提示设计策略  _  Gemini API.md]
last_updated: 2026-04-12
---

## 核心摘要

Google Gemini API 官方中文文档，系统介绍了提示工程的核心策略和最佳实践。文档强调**简洁直接的指令**最有效，建议使用 XML 标签或 Markdown 标题作为分隔符，并提供了从基础到高级的完整提示设计指南。

**关键要点：**
- **输入类型**：问题输入、任务输入、实体输入、补全输入
- **少样本提示**：始终包含 3-5 个示例，确保格式一致性
- **Gemini 3 策略**：用词精确直接、使用一致结构、定义参数、控制输出详细程度
- **智能体工作流**：逻辑分解、问题诊断、风险评估、执行与恢复

**最佳实践**：
1. 长上下文结构：先提供所有上下文，具体说明放在最后
2. 使用 XML 风格标签（`<context>`, `<task>`）分隔内容
3. 温度设为 1.0，降低会导致推理任务性能下降和循环
4. 现代推理模型自动生成"思考"文本，无需强制 Chain-of-Thought

## 关联连接
- [[Prompt_Engineering]] — 提示工程总览
- [[Gemini]] — Google 大语言模型家族
- [[Few_Shot_Prompting]] — 少样本提示技术
- [[Zero_Shot_Prompting]] — 零样本提示技术
