---
title: "The Complete Prompt Engineering Guide (2025)"
source: "https://rsx.ch/blog/prompt-engineering-guide"
author:
  - "[[BrilliantPrompts]]"
published: 2025-01-15
created: 2026-04-12
description: "Master prompt engineering with this comprehensive guide. Learn techniques for ChatGPT, Claude, and Gemini that deliver 10x better results. From basics to advanced strategies."
tags:
  - "clippings"
---
The difference between a mediocre AI response and a brilliant one isn't the AI — it's the prompt. This guide teaches you the principles, patterns, and techniques that consistently produce exceptional results from ChatGPT, Claude, and Gemini.

## What Is Prompt Engineering?

Prompt engineering is the skill of crafting inputs to AI models that produce the best possible outputs. Think of it as learning to communicate with a brilliant but literal assistant — the clearer your instructions, the better the results.

It's not about tricks or hacks. It's about understanding how AI models process language and structuring your requests to align with their strengths.

### Why It Matters

Most people use AI at about 10% of its capability. They type vague questions and get vague answers. With proper prompt engineering, you can:

- **Get specific, actionable outputs** instead of generic fluff
- **Save hours of back-and-forth** by getting it right the first time
- **Unlock capabilities** you didn't know the AI had
- **Produce professional-quality work** that requires minimal editing

## The 5 Core Principles

### 1\. Be Specific, Not Vague

The #1 mistake is being too vague. Every word in your prompt should add information that helps the AI understand exactly what you want.

**❌ Vague:** "Write a blog post about marketing."

**✅ Specific:** "Write a 1,200-word blog post about email marketing strategies for SaaS startups with less than 1,000 subscribers. Include 5 actionable tactics with examples. Tone: professional but approachable."

### 2\. Assign a Role

Telling the AI who it should be dramatically changes the quality and perspective of responses. Roles activate relevant knowledge and set the expertise level.

**✅ Example:** "You are a senior software engineer at Google specializing in distributed systems. Review this code..."

Effective roles include: job titles, experience levels, famous experts, or specialized professionals. The more specific the role, the more focused the output.

### 3\. Provide Context

AI can't read your mind. The context you provide — your situation, constraints, audience, and goals — shapes the response more than any other factor.

Key context to include:

- **Who is the audience?** (beginners, executives, developers, students)
- **What's the purpose?** (blog post, email, report, code review)
- **What are the constraints?** (word count, format, tone, deadline)
- **What do you already have?** (existing data, previous work, references)

### 4\. Structure the Output

Don't leave the format to chance. Tell the AI exactly how you want the output structured. Use numbered lists, headers, tables, or specific sections.

**✅ Example:** "Provide your analysis in this format: 1) Executive Summary (2 sentences), 2) Key Findings (bullet points), 3) Recommendations (numbered, with priority level), 4) Risk Assessment (table with likelihood and impact)."

### 5\. Iterate and Refine

Great prompts are rarely written on the first try. Treat prompt engineering as a conversation — refine based on what you get back.

The iteration cycle:

1. Write your initial prompt
2. Review the output critically
3. Identify what's missing or wrong
4. Add or modify instructions
5. Repeat until satisfied

## The CRAFT Framework

We developed the CRAFT framework to make prompt engineering systematic and repeatable:

**C** — **Context**: Set the scene. Who are you? What's the situation?

**R** — **Role**: Who should the AI be? What expertise should it channel?

**A** — **Action**: What specific task should it perform?

**F** — **Format**: How should the output be structured?

**T** — **Tone**: What style and voice should it use?

Apply CRAFT to any prompt request and you'll consistently get better results than 90% of AI users.

## Advanced Techniques

### Chain of Thought Prompting

Ask the AI to think step-by-step before giving its final answer. This dramatically improves reasoning accuracy, especially for complex problems.

**✅ Add:** "Think through this step-by-step before giving your final answer. Show your reasoning."

### Few-Shot Examples

Show the AI 2-3 examples of what you want before asking for the actual output. This is especially powerful for consistent formatting and style matching.

### Constraints and Boundaries

Tell the AI what NOT to do. Constraints often improve quality more than additional instructions.

**✅ Example:** "Do NOT use jargon. Do NOT exceed 500 words. Do NOT include a generic introduction — start directly with the first actionable tip."

### Temperature and Creativity Control

For factual tasks, ask for conservative, well-sourced responses. For creative work, explicitly ask for bold, unconventional ideas. The framing of your request acts as a "temperature" control.

## Common Mistakes to Avoid

1. **Being too short** — A 10-word prompt gets a generic response. Invest 60 seconds in a detailed prompt to save 30 minutes of revisions.
2. **Asking multiple unrelated questions** — One prompt, one task. Split complex requests into sequential prompts.
3. **Not providing examples** — If you have a specific style or format in mind, show it.
4. **Ignoring the output format** — Always specify whether you want bullets, paragraphs, tables, code, etc.
5. **Not iterating** — The first response is a draft. Build on it with follow-up instructions.

## Tips by AI Model

### ChatGPT (GPT-4)

- Excels at creative tasks and general knowledge
- Responds well to detailed system instructions
- Strong at code generation across many languages
- Can browse the web and process images with plugins

### Claude (Anthropic)

- Excellent at long-form analysis and nuanced reasoning
- Handles very long documents and contexts well
- More cautious and thoughtful by default
- Strong at following detailed, multi-step instructions

### Gemini (Google)

- Strong at factual queries and data analysis
- Integrates well with Google services
- Good at multimodal tasks (text + images)
- Solid for summarization and research

## Before & After Examples

### Example 1: Code Review

**❌ Before:** "Review my code"

**✅ After:** "You are a senior Python developer. Review this Flask API endpoint for: 1) Security vulnerabilities (SQL injection, XSS), 2) Performance bottlenecks, 3) Error handling gaps, 4) Code style (PEP 8). For each issue, explain the risk and provide a fixed code snippet."

### Example 2: Marketing Copy

**❌ Before:** "Write an ad for my product"

**✅ After:** "You are a direct-response copywriter. Write 3 Facebook ad variations for a $49/month project management tool targeting freelance designers. Each ad: headline (under 40 chars), body (under 125 chars), CTA. Tone: confident but not salesy. Focus on the pain of missed deadlines."

### Example 3: Data Analysis

**❌ Before:** "Analyze this data"

**✅ After:** "You are a data analyst at a SaaS company. I'll share our monthly metrics for the past 12 months. Identify: 1) The 3 most important trends, 2) Any anomalies that need investigation, 3) Correlations between metrics. Present findings as an executive summary (3 bullet points) and a detailed analysis (500 words max)."