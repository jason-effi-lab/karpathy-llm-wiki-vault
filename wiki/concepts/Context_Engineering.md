---
title: "Context Engineering（上下文工程）"
type: concept
tags: [提示工程, 上下文工程, 高级概念, 范式转变]
sources: [raw/01-articles/The Complete Guide to AI Prompt Engineering in 2025-2026.md]
last_updated: 2026-04-12
---

## 定义

Context Engineering（上下文工程）是 Prompt Engineering 的演进形态，由 Anthropic 于 2024-2025 年提出。它不再局限于优化单个提示，而是将提示视为更大系统中的上下文组成部分，包括系统提示、工具定义、外部数据和对话历史的综合策划。

核心原则：
> "找到能够最大化期望结果概率的最小高信号 token 集合。"

## 从 Prompt 到 Context 的转变

### Prompt Engineering（旧范式）
- 关注单个提示的词句优化
- 重点是"如何问问题"
- 相对孤立的提示设计

### Context Engineering（新范式）
- 关注整个上下文环境的策划
- 重点是"提供什么信息和工具"
- 系统化的上下文管理
- 版本控制和测试如代码一般

## 核心组件

Context Engineering 包含以下上下文的综合策划：

### 1. 系统提示 (System Prompt)
定义模型的整体行为和身份。

```
你是 Claude，一个由 Anthropic 创建的 AI 助手。
你擅长长文档分析和细致推理。
默认提供事实性的进展报告，而非自我庆祝式更新。
```

### 2. 工具定义 (Tool Definitions)
描述可用工具及其用途。

```
可用工具:
- search: 搜索互联网获取最新信息
- calculator: 执行数学计算
- code_interpreter: 执行 Python 代码
```

### 3. 外部数据 (External Data)
从 RAG、数据库或 API 获取的数据。

```
以下是关于你查询主题的相关文档片段：
[文档内容...]

基于上述信息，回答用户的问题。
```

### 4. 对话历史 (Conversation History)
之前交互的摘要或完整记录。

```
之前的对话摘要：
- 用户询问产品定价
- 你提供了标准定价表
- 用户表示是教育机构，询问折扣
```

### 5. 当前用户输入 (Current User Input)
用户的即时请求。

## 最佳实践

### 1. 高信号密度
优先选择最相关信息，而非包含所有可用信息。

> "一个结构良好的 16K token RAG 提示优于 128K token 的完整上下文。" —— 研究报告

### 2. 战略性放置
- **关键指令**：放在提示末尾（利用 recency bias）
- **长文档**：放在提示开头
- **锚定短语**："基于上述所有信息..." 重新聚焦注意力

### 3. 结构化分隔
使用清晰的结构标记不同上下文组件：

```
<system>
[系统提示]
</system>

<tools>
[工具定义]
</tools>

<context>
[外部数据]
</context>

<conversation>
[对话历史]
</conversation>

<user_input>
[用户输入]
</user_input>
```

### 4. 版本控制与测试
将上下文配置视为代码：
- 使用 git 进行版本控制
- 维护测试集（20-50 个真实输入）
- 回归测试防止性能退化
- 监控 token 成本和延迟

## 上下文窗口优化

### 挑战
- **Recency Bias**：Transformer 对最近的 token 加权更高
- **信号稀释**：无关信息会干扰关键信号
- **幻觉增加**：长上下文中幻觉率上升
- **延迟**：每 500 tokens 增加约 25ms 响应时间

### 优化策略

| 策略 | 说明 |
|------|------|
| **优先级排序** | 最关键信息放在开头和结尾 |
| **摘要压缩** | 长文档预摘要处理 |
| **分块检索** | 只检索最相关的片段 |
| **渐进加载** | 复杂任务分解为多个上下文窗口 |

## 应用场景

### 适用于 Context Engineering
- AI 代理（Agents）和自动化工作流
- 长文档分析和问答
- 多轮对话系统
- 工具使用型应用
- 需要持续学习的应用

### 示例工作流

```
Context Engineering 工作流示例：

1. 系统设置（一次）
   - 定义系统角色
   - 配置可用工具
   - 设置环境变量

2. 对话初始化
   - 加载相关知识库摘要
   - 设置会话状态

3. 每轮交互
   - 更新对话历史
   - 如有需要，执行 RAG 检索
   - 构建完整上下文
   - 发送给模型
   - 处理响应，更新状态

4. 持续优化
   - 基于评估结果调整上下文组件
   - A/B 测试不同配置
```

## 与 Prompt Engineering 的关系

Context Engineering **包含并超越** Prompt Engineering：

- **底层技术**：提示编写技巧仍然重要
- **上层架构**：增加了系统性视角
- **工程实践**：加入了版本控制、测试、监控

## 未来趋势

1. **自适应上下文**：模型自动决定需要加载哪些上下文
2. **上下文缓存**：重用稳定的上下文部分
3. **多模态上下文**：整合文本、图像、音频、视频
4. **个性化上下文**：基于用户历史和行为定制

## 关联连接
- [[Prompt_Engineering]] — 提示工程基础
- [[RAG]] — 检索增强生成（Context Engineering 的关键组件）
- [[摘要-ai-prompt-engineering-2025-2026-espo]] — 来源文档
- [[Agentic_Systems]] — 智能体系统（重度依赖 Context Engineering）
