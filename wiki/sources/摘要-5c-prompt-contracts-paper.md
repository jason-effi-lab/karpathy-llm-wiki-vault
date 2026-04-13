---
title: "摘要-5C Prompt Contracts 研究论文"
type: source
tags: [来源, 论文, 5C框架, 提示设计, 效率优化]
sources: [raw/02-papers/5C Prompt Contracts .pdf]
last_updated: 2026-04-12
---

## 核心摘要

由 AI 研究策略师 Ugur Ari 提出的 5C Prompt Contract 框架，是一种**极简、创意友好、token 高效**的提示设计方法，特别适合个人和中小企业使用。

**5C 组件：**
1. **Character（角色）**：定义 AI 的身份、专业知识、语气风格
2. **Cause（原因/目标）**：明确任务目的和预期成果
3. **Constraint（约束）**：设定边界条件、资源限制、执行规则
4. **Contingency（应变）**：定义备用方案和错误处理机制
5. **Calibration（校准）**：输出优化和质量控制指令

**核心发现：**
- **Token 效率**：5C 框架平均仅需 54.75 tokens 输入，远低于 DSL (348.75) 和非结构化 (346.25)
- **输出质量**：在保持创意丰富度的同时，输出一致性优于非结构化提示
- **跨模型表现**：在 OpenAI、Anthropic、DeepSeek、Gemini 上均表现优异
- **Gemini 特别优势**：5C 提示仅需 54 tokens 输入，而 DSL 需要 1212 tokens

**与 DSL 对比：**
| 维度 | 5C | DSL |
|------|-----|-----|
| 输入 Token | 极低 (~55) | 高 (~350) |
| 认知负载 | 低 | 高 |
| 创意自由度 | 高 | 受限 |
| 学习曲线 | 平缓 | 陡峭 |

**实践建议：**
- 用于token敏感场景（如 API 调用频繁的应用）
- 需要平衡结构与创意的任务
- AI 工程资源有限的个人/中小企业

## 关联连接
- [[Prompt_Engineering]] — 提示工程总览
- [[5C_Framework]] — 5C 提示契约框架详解
- [[Prompt_Design]] — 提示设计方法论
- [[Token_Efficiency]] — Token 效率优化
