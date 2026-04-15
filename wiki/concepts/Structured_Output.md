---
title: "Structured_Output"
type: concept
tags: [提示技术, 输出格式, JSON, 结构化]
sources: [raw/03-transcripts/Prompt Engineering Full Course.md]
last_updated: 2026-04-15
---

## 定义

**结构化输出（Structured Output）**是一种提示技术，要求模型以特定格式（JSON、Markdown 表格、XML 等）返回结果，并通过在提示中给出格式示例来约束输出形状，使输出可被程序直接解析和使用。

## 关键信息

### 核心做法

1. **声明输出格式**：在提示中明确指定格式类型（如"仅输出有效 JSON"）
2. **给出结构示例**：提供一个目标格式的模板或示例对象
3. **禁止多余文本**：加入"不要输出其他内容"的约束

### 典型示例

```
比较 Trello、Monday.com 和 ClickUp 的功能与定价。
仅输出有效 JSON，格式如下：
{"tools": [{"name": "...", "features": [...], "price": "..."}]}
不要输出任何其他文字。
```

### 适用场景

- 将模型输出存入数据库
- 在 API 中返回结构化数据
- 前端页面直接渲染模型输出
- 多步骤流水线中传递数据

### 与少样本提示的关系

结构化输出是少样本提示的一个特殊形式：给出输出格式示例，相当于告诉模型"输出对"中的期望输出形状。

## 关联连接

- [[Prompt_Engineering]] — 结构化输出是其核心技术之一
- [[Few_Shot_Prompting]] — 结构化输出常结合少样本示例使用
- [[摘要-prompt-engineering-full-course-techwithtim]] — 来源
