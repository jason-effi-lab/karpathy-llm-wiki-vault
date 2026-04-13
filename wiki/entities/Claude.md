---
title: "Claude"
type: entity
tags: [模型, Anthropic, LLM, 实体]
sources: 
  - raw/01-articles/Prompting best practices-Anthropic.md
  - raw/01-articles/The Complete Guide to AI Prompt Engineering in 2025-2026.md
last_updated: 2026-04-12
---

## 定义

Claude 是由 **Anthropic** 开发的大型语言模型家族，以其强大的长上下文处理能力和细致推理而闻名。Claude 系列模型强调有用性、无害性和诚实性（Helpful, Harmless, Honest - HHH 原则）。

## 主要版本

### Claude 4.6 系列（当前最新）
- **Claude Opus 4.6**：最强大的模型，擅长深度分析、研究和复杂编码
- **Claude Sonnet 4.6**：平衡性能和速度，默认 effort=high
- **Claude Haiku 4.6**：轻量级，适合简单任务

**关键特性**：
- **Adaptive Thinking（自适应思考）**：动态决定何时以及思考多少
- **Extended Context**：200K+ tokens
- **Native Subagent Orchestration**：原生子代理编排能力

### Claude 4.5 系列
- **Claude Opus 4.5**：前一版本旗舰模型
- **Claude Sonnet 4.5**：前一版本平衡模型

### 早期版本
- Claude 3.x 系列（Sonnet, Opus, Haiku）

## 核心特点

### 1. 视角："聪明但缺乏上下文的新员工"
Anthropic 对 Claude 的定位：
- 极其聪明但缺乏你团队的规范和流程知识
- **越精确地解释你想要什么，结果越好**
- 不会主动推断模糊的"超越预期"行为

### 2. 指令遵循：字面理解
Claude 4.x 模型**按字面理解指令**：
- 早期版本会推断意图并扩展模糊请求
- 现在必须**明确表达**期望的行为
- 不会有过度假设

### 3. 思考模式演进

| 版本 | 思考模式 | 配置方式 |
|------|----------|----------|
| Claude 4.5 | Extended Thinking | `budget_tokens` |
| Claude 4.6 | Adaptive Thinking | `effort` 参数 |

**Adaptive Thinking**：
```python
# 老方式（4.5 及之前）
thinking={"type": "enabled", "budget_tokens": 32000}

# 新方式（4.6）
thinking={"type": "adaptive"}
output_config={"effort": "high"}  # low/medium/high
```

- Claude 根据任务复杂度自动决定思考深度
- 简单查询直接响应，复杂任务深度思考
- 比固定预算的 Extended Thinking 更高效

### 4. 上下文窗口
- **标准上下文**：200K+ tokens
- **Context Awareness**：模型能跟踪剩余 token 预算

**Context Awareness 的实践意义**：
```
你的上下文窗口在接近限制时会自动压缩，允许你无限期继续工作。
因此，不要因为 token 预算担忧而提前停止任务。
在接近 token 预算时，将进度和状态保存到内存。
```

### 5. Agentic Capabilities（智能体能力）

Claude 4.6 在长期推理和状态跟踪方面表现卓越：

**多上下文窗口工作流**：
- 第一个窗口：设置框架（测试、脚本）
- 后续窗口：在待办事项列表上迭代
- 能在新窗口中从文件系统恢复状态

**子代理编排**：
- 识别何时需要将任务委托给子代理
- 无需显式指令即可主动编排
- 可能过度使用（Opus 4.6 对子代理有强烈偏好）

### 6. 过度热诚倾向
Claude 4.5 和 4.6 存在过度工程化倾向：
- 创建额外文件
- 添加不必要的抽象
- 为假设的未来需求构建灵活性

**缓解措施**：
```
避免过度工程。只进行直接请求或明显必要的更改。
- 范围：不添加功能或重构
- 文档：只在你更改的代码上添加注释
- 防御性编码：只在系统边界验证
```

## 提示工程最佳实践

### 核心原则
1. **Clear and Direct**：清晰明确的指令
2. **Use Examples**：3-5 个示例是最可靠的控制方式
3. **XML Structuring**：使用 XML 标签分隔不同组件
4. **Role Assignment**：通过系统提示设置角色

### 长上下文策略
```
提示结构：
[长文档放在顶部]
[查询、指令和示例放在底部]

益处：查询放在末尾可提升高达 30% 的性能，
尤其在复杂多文档场景中。
```

### 避免对 Claude 4.6 过度提示
与早期模型不同，Claude 4.6：
- **不要太激进**：之前需要 "CRITICAL: You MUST..." 现在只需 "Use this tool when..."
- **移除"过度提示"**：早期模型的"如果在犹豫，使用工具"会导致 4.6 过度触发工具

### 词敏感性问题
**Claude Opus 4.5 对"think"及其变体特别敏感**（当 extended thinking 禁用时）：
- 避免："think", "thinking", "thought"
- 改用："consider", "evaluate", "reason through", "analyze"

### 工具使用
Claude 4.6 对工具使用更积极：
```
# 增加主动性
<default_to_action>
默认实施更改而非仅提供建议。如果用户意图不明确，
推断最有用的可能行动并使用工具发现缺失信息。
</default_to_action>

# 减少主动性
<do_not_act_before_instructions>
除非明确指示进行更改，否则不跳入实施。
当用户意图模糊时，默认提供信息和推荐。
</do_not_act_before_instructions>
```

## 安全设计

### Constitutional AI
Claude 使用 Constitutional AI 技术进行训练：
- 从人类反馈强化学习（RLHF）的改良版本
- 通过原则（Constitution）而非仅人类标签指导行为
- 目标是更有帮助、更无害、更诚实

### 自主性与安全的平衡
```
考虑你行为的可逆性和潜在影响。
鼓励采取本地、可逆的行动（如编辑文件、运行测试），
但对于难以逆转、影响共享系统或具有破坏性的行动，先询问用户。
```

## 关联连接
- [[Prompt_Engineering]] — 提示工程总览
- [[Anthropic]] — Anthropic 公司
- [[Adaptive_Thinking]] — 自适应思考机制
- [[Agentic_Systems]] — 智能体系统
- [[摘要-anthropic-prompting-best-practices]] — Anthropic 最佳实践
- [[摘要-ai-prompt-engineering-2025-2026-espo]] — 2025-2026 指南
