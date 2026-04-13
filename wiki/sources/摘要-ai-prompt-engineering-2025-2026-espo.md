---
title: "摘要-AI 提示工程完整指南 2025-2026"
type: source
tags: [来源, 提示工程, 上下文工程, 框架]
sources: [raw/01-articles/The Complete Guide to AI Prompt Engineering in 2025-2026.md]
last_updated: 2026-04-12
---

## 核心摘要

本文深入探讨了从"提示工程"到"上下文工程"的范式转变。核心发现：**150-300 词是提示的最佳长度**，超过 3,000 tokens 会导致性能显著下降。现代推理模型（GPT-5, Claude 4, Gemini 3）内部自动思考，传统的"逐步思考"提示反而可能损害性能。

**七大核心要素：**
1. Role/Persona：激活领域知识
2. Task Context：背景和受众信息
3. Clear Instructions：核心请求
4. Sequential Steps：确保执行顺序
5. Few-shot Examples：3-5 个多样化示例
6. Output Format：响应结构
7. Constraints：缩小输出空间

**三大实验室的收敛趋势：**
- Claude 4.x：字面理解指令，CoT 有益但非必须
- GPT-4.1/5：冲突指令有害，避免对 o 系列使用 CoT
- Gemini 3：无需复杂提示工程，简化提示即可

**三大框架：**
- **APE**（简单任务）：Action + Purpose + Expectation
- **CO-STAR**（内容创作）：Context, Objective, Style, Tone, Audience, Response
- **RISEN**（复杂任务）：Role, Instructions, Steps, End Goal, Narrowing

**关键洞察：**
- 16K token 的 RAG 提示优于 128K token 的完整上下文
- 提示工程可提升 20-40% 基准性能
- 示例的选择比数量更重要，多样性是关键
- 现代模型默认思考，显式请求"直接答案"反而有害

## 关联连接
- [[Prompt_Engineering]] — 提示工程总览
- [[Context_Engineering]] — 上下文工程
- [[APE_Framework]] — APE 框架
- [[CO-STAR_Framework]] — CO-STAR 框架
- [[RISEN_Framework]] — RISEN 框架
