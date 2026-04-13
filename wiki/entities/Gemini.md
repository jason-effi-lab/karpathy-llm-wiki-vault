---
title: "Gemini"
type: entity
tags: [模型, Google, LLM, 实体]
sources: 
  - raw/01-articles/提示设计策略  _  Gemini API.md
  - raw/02-papers/Goolge-Prompt-Engineering-whitepaper.pdf
last_updated: 2026-04-12
---

## 定义

Gemini 是 Google 开发的大型语言模型家族，专为高级推理和多模态任务设计。作为 Google DeepMind 的旗舰模型系列，Gemini 代表了 Google 在生成式 AI 领域的核心产品。

## 主要版本

### Gemini 3（当前主要版本）
- **Gemini 3 Pro**: 最强大的版本，适合复杂推理任务
- **Gemini 3 Flash**: 轻量级版本，平衡性能与效率
- **特点**：
  - 专为高级推理和指令遵循设计
  - 自动生成内部"思考"文本
  - **不再需要复杂的提示工程**（如强制 CoT）
  - 支持 `thinking_level` 参数控制推理深度

### Gemini 2.5
- 前代主要版本
- 部分复杂提示工程技术（如详细 CoT）对其仍然有效

## 核心特点

### 1. 提示简化趋势
与其他模型不同，Gemini 3 展现出"反提示工程"的特性：
- 复杂的提示工程技术（如 elaborate CoT）可能**降低**性能
- 建议使用简化提示配合 `thinking_level: "high"`
- 如果之前为 Gemini 2.5 设计的复杂提示表现不佳，尝试简化

### 2. 分隔符偏好
- **XML 风格标签**：`<context>`, `<task>`, `<role>`
- **Markdown 标题**：# Identity, # Constraints
- **结构一致性**：同一提示中保持统一格式

### 3. 温度设置

**关键发现**：
- **推荐温度：1.0**
- 降低温度可能导致推理任务中**出现循环**和性能下降
- 这与传统认知（高确定性任务用低温）相反

### 4. 上下文窗口
- **标准上下文**：128K tokens
- **扩展上下文**：最高可达 2M tokens（适用于视频和深度文档）

### 5. 多模态能力
- 文本、图像、音频、视频原生支持
- 代码执行内置
- Google 搜索接地（Grounding）

## 提示工程建议

### Gemini 3 核心原则

```
1. 用词精确、直接
2. 使用一致的 XML 或 Markdown 结构
3. 明确说明任何模糊术语
4. 控制输出详细程度（默认高效简洁）
5. 连贯处理多模态输入
6. 将关键指令放在系统提示或提示开头
7. 长上下文：先提供所有上下文，具体说明放在最后
8. 使用锚定短语连接上下文和查询
```

### 推荐模板结构

**XML 示例**：
```xml
<role>
你是一个有帮助的助手。
</role>

<constraints>
1. 客观陈述
2. 引用来源
</constraints>

<context>
[用户输入 - 模型知道这是数据，不是指令]
</context>

<task>
[具体用户请求]
</task>
```

### 智能体工作流支持

Gemini 3 提供精细的智能体行为配置：

**推理与策略**：
- 逻辑分解详尽程度
- 问题诊断深度
- 信息详尽程度

**执行与可靠性**：
- 适应性：对新数据的反应方式
- 持久性和恢复性：错误纠正程度
- 风险评估：区分低风险探索与高风险状态变更

**互动和输出**：
- 模糊性处理：何时进行假设，何时寻求澄清
- 详细程度：文本输出量
- 精确度和完整性：输出保真度

## Code Execution（代码执行）

Gemini 默认启用 Python 代码执行：
- 自动检测需要计算、计数或算术的场景
- 执行生成的 Python 代码
- 将执行结果整合到回答中

## 接地（Grounding）

**Google 搜索接地**：
- 将 Gemini 与实时网络内容关联
- 适用于冷门或最新事实查询
- 减少幻觉

## 关联连接
- [[Prompt_Engineering]] — 提示工程总览
- [[Google]] — Google 公司
- [[摘要-gemini-api-prompting-strategies]] — Gemini API 策略来源
- [[摘要-google-prompt-engineering-whitepaper]] — Google 白皮书
