---
title: "摘要-Anthropic Claude 提示最佳实践"
type: source
tags: [来源, Claude, Anthropic, 提示工程, 最佳实践]
sources: [raw/01-articles/Prompting best practices-Anthropic.md]
last_updated: 2026-04-12
---

## 核心摘要

Anthropic 官方 Claude 4.6 系列模型的提示工程指南，涵盖基础技巧到智能体系统设计。核心原则：**清晰直接** — 像对待聪明但缺乏上下文的新员工一样对待 Claude。

**关键要点：**
- **Claude 4.6 特性**：更简洁自然的沟通风格，更少冗长总结，并行工具调用能力
- **XML 结构化**：使用 `<instructions>`, `<context>`, `<input>` 等标签减少误解
- **长上下文策略**：将长文档放在提示顶部，查询放最后（可提升 30% 性能）

**思考模式：**
- Claude Opus 4.6 默认使用**自适应思考**（adaptive thinking），而非固定预算
- 通过 `effort` 参数控制思考深度：low/medium/high
- 复杂任务不需要显式"逐步思考"提示，模型会自动推理

**智能体系统：**
- Claude 4.6 擅长长期推理和状态跟踪
- 支持多上下文窗口工作流，可保存/恢复进度
- 原生支持子代理编排（subagent orchestration）

**工具使用：**
- 4.6 模型对工具使用更积极，可能需要调低激进提示
- 支持并行工具调用优化效率
- 可通过系统提示调整行动倾向（主动实施 vs 仅提供建议）

**最佳实践：**
- 3-5 个示例效果最佳，用 `<example>` 标签包裹
- 始终指定输出格式而非"不要使用某种格式"
- Claude Opus 4.5 对"think"这个词特别敏感，可改用"consider"或"evaluate"

## 关联连接
- [[Prompt_Engineering]] — 提示工程总览
- [[Claude]] — Anthropic Claude 模型
- [[Agentic_Systems]] — 智能体系统设计
- [[Adaptive_Thinking]] — 自适应思考
