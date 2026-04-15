---
title: "Iterative_Refinement"
type: concept
tags: [提示技术, 多轮对话, 迭代]
sources: [raw/03-transcripts/Prompt Engineering Full Course.md]
last_updated: 2026-04-15
---

## 定义

**迭代细化（Iterative Refinement）**是一种提示策略，通过多轮对话逐步修正和完善模型输出，而不是试图在单个提示中一步到位。每一轮对话都基于上一轮的输出继续调整方向、格式或细节。

## 关键信息

### 核心思路

- 将复杂任务拆解为多轮交互
- 利用对话历史作为上下文（模型会自动注入前序对话）
- 在已建立的"规则上下文"中继续追加新的输入

### 典型工作流

```
第 1 轮：给出格式要求 + 第一个示例 → 获得初始输出
第 2 轮：直接提交新输入（无需重复规则）→ 模型沿用前轮格式
第 N 轮：继续提交，或要求调整某个细节
```

### 与面试式提示的关系

**面试式提示（Interview Style Prompting）**是迭代细化的变体：先让模型以"面试官"角色提问，收集缺失的上下文信息，再基于完整信息生成最终输出。适合任务需求不明确的场景。

### 注意事项

- 在同一会话中迭代时，历史对话会累积进入上下文窗口，注意 token 消耗
- 需要"干净"的新任务时，开启新会话以避免历史对话干扰

## 关联连接

- [[Prompt_Engineering]] — 迭代细化是核心工作方式之一
- [[Context_Engineering]] — 多轮对话中的上下文管理
- [[Few_Shot_Prompting]] — 迭代中可逐步添加更多示例
- [[摘要-prompt-engineering-full-course-techwithtim]] — 来源
