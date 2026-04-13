---
name: ingest
description: 将 raw/ 目录下的原始资料编译到 wiki/ 中。处理完成后，将源文件自动移动到 raw/09-archive/ 归档。支持 `/ingest` (扫描 raw/ 下所有未归档文件) 或 `/ingest <path>` (处理指定文件)。当用户提到"摄取"、"导入"、"收入"资料，或要求将文件加入知识库时，也应该触发此技能。绝对忽略 raw/09-archive/ 目录。
user-invocable: true
---

# ingest 技能

## 核心工作流：Inbox & Archive

你正在维护一个 **LLM Wiki**（Obsidian 知识库）。`raw/` 目录是"待处理收件箱"，`wiki/` 是"编译输出层"。

**目录结构约定：**
- `raw/01-articles/` — 网页剪藏的 Markdown 文章
- `raw/02-papers/` — 论文和 PDF 文献
- `raw/03-transcripts/` — 视频转录文案
- `raw/09-archive/` — **已处理文件的归档目录，禁止读取**
- `wiki/sources/` — 资料摘要
- `wiki/entities/` — 实体（人物、公司、工具、产品）
- `wiki/concepts/` — 概念（框架、方法论、理论）

## 触发逻辑

1. **用户执行 `/ingest`**：扫描 `raw/` 所有子目录（排除 `09-archive/`），找出待处理文件。
2. **用户执行 `/ingest <path>`**：仅处理指定文件。
3. **隐式触发**：用户说"把这个资料摄入知识库"、"导入这篇文章"时，自动执行 ingest。

## 编译流水线

对每个待处理源文件，严格按以下步骤执行：

### 步骤 1：读取源文件

- **如果是 `.md` 文件**：使用读取工具完整读取内容。
- **如果是 `.pdf` 文件**：使用读取工具尝试提取文本。如果无法提取或内容为空，改为记录文件元信息（文件名、页数）在 sources 页面中。

### 步骤 2：提炼核心并翻译

从源文件中提取：
- **核心主旨**：这段资料讲什么（1-2句话）
- **实体**：人物、公司、工具、产品等具体名词
- **概念**：框架、方法论、理论等抽象名词

如果是非中文内容，则翻译成中文。

### 步骤 3：创建来源摘要

在 `wiki/sources/` 创建 Markdown 文件：

```markdown
---
title: "摘要-文件slug"
type: source
tags: [来源, 原始文件]
sources: [raw/01-articles/xxx.md]
last_updated: YYYY-MM-DD
---

## 核心摘要
[3-5句话的核心总结]

## 关联连接
- [[EntityName]] — 关联实体
- [[ConceptName]] — 关联概念
```

文件名使用 kebab-case：`摘要-{文件slug}.md`

### 步骤 4：知识网络化（实体/概念页面）

对于步骤 2 提取的每个实体和概念：

**目标目录：**
- 实体 → `wiki/entities/`
- 概念 → `wiki/concepts/`

**处理逻辑：**
1. 页面不存在 → 按照 CLAUDE.md 的 Frontmatter 规范创建新页面
2. 页面已存在 → 读取现有内容，**增量合并**新信息
3. **发现冲突** → **立即暂停**，向用户报告冲突内容，询问处理方式后再继续

**页面模板：**

```markdown
---
title: "页面名称"
type: entity | concept
tags: [标签]
sources: [关联的源文件]
last_updated: YYYY-MM-DD
---

## 定义
[对该实体/概念的定义]

## 关键信息
[从源文件中提取的详细信息]

## 关联连接
- [[摘要-source-slug]] — 来源
- [[RelatedEntity]] — 相关实体
```

### 步骤 5：更新全局注册表

**更新 `wiki/index.md`：**
按照 CLAUDE.md 规定的格式，将新增页面添加到对应分类下：
- Sources: `[[摘要-source-slug]] — 该资料的核心主旨`
- Entities: `[[EntityName]] — 该实体的身份定义`
- Concepts: `[[ConceptName]] — 该概念的核心定义`

**更新 `wiki/log.md`：**
追加操作日志（Append-only）：
```markdown
## [YYYY-MM-DD] ingest | 操作简述
- **变更**: 新增 [[PageName]]; 更新 [[index.md]]
- **冲突**: 无 (或: 冲突 [[ConflictingPage]], 已暂停等待决策)
```

### 步骤 6：归档源文件

在确认以下全部完成后，将源文件移动到 `raw/09-archive/`目录：
- sources 页面已创建
- 实体/概念页面已创建或更新
- index.md 已更新
- log.md 已更新

**绝对禁止修改源文件内部的文字。**

## 冲突处理流程

当发现新旧知识冲突时：

1. **暂停**：停止当前 ingest 流程
2. **报告**：向用户说明冲突内容（哪个页面、冲突点是什么）
3. **询问**：请用户选择处理方式：
   - A) 保留新旧两者，标注为"知识冲突"
   - B) 用新知识覆盖旧知识
   - C) 放弃本次 ingest
4. **继续**：根据用户选择继续或终止

## 注意事项

- 绝对不读取 `raw/09-archive/` 下的任何文件
- 所有 wiki 页面必须包含 `## 关联连接` 区域，不能产生孤岛页面
- 使用简体中文编写所有内容
- 实体命名使用 TitleCase，概念和来源使用 kebab-case