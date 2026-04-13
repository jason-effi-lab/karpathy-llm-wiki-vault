---
title: "Anthropic"
type: entity
tags: [公司, AI, 实体, Anthropic]
sources: [raw/01-articles/Prompting best practices-Anthropic.md]
last_updated: 2026-04-12
---

## 定义

Anthropic 是一家专注于 AI 安全研究的美国人工智能公司，成立于 2021 年，由前 OpenAI 研究副总裁 Dario Amodei 及其妹妹 Daniela Amodei 等人创立。公司使命是开发可靠、可解释和可操控的 AI 系统。

## 核心产品与产品

### Claude 系列模型
Anthropic 的旗舰大型语言模型家族：
- **Claude 3/4 系列**：Haiku, Sonnet, Opus
- 以强大的长上下文处理和细致推理能力著称
- 强调 HHH 原则（Helpful, Harmless, Honest）

### Claude API 与平台
- **Claude API**：面向开发者的模型访问接口
- **Claude Code**：智能编程助手
- **Claude Enterprise**：企业级解决方案

## 核心理念

### Constitutional AI
Anthropic 开发的 AI 训练方法：
- 不仅依赖人类反馈，还使用一套原则（Constitution）指导模型行为
- 目标是使 AI 更安全、更可控
- 减少对人类标注者的依赖

### AI Safety Research
Anthropic 将 AI 安全作为核心研究方向：
- **Mechanistic Interpretability**：理解神经网络内部工作机制
- **Scaling Laws**：研究模型能力随规模变化的规律
- **Alignment**：确保 AI 系统按照人类意图行动

## 关键技术创新

### Adaptive Thinking
Claude 4.6 引入的自适应思考机制：
- 模型动态决定何时以及思考多少
- 基于任务复杂度和 `effort` 参数
- 比固定预算的 Extended Thinking 更高效

### Context Awareness
Claude Sonnet 4.6 和 4.5 支持上下文感知：
- 模型能跟踪剩余上下文窗口
- 优化长任务执行
- 支持多上下文窗口工作流

## 关联连接
- [[Claude]] — Anthropic 的 LLM 产品
- [[Prompt_Engineering]] — 提示工程（Anthropic 是重要贡献者）
- [[Constitutional_AI]] — 宪法 AI 训练方法
- [[摘要-anthropic-prompting-best-practices]] — 官方最佳实践指南
