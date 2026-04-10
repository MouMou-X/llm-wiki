---
title: LLM Wiki 模式
type: summary
tags: [knowledge-management, llm, personal-wiki, methodology]
sources: [LLM Wiki.md]
created: 2026-04-10
updated: 2026-04-10
---

# LLM Wiki 模式

> 来源：`LLM Wiki.md`（Andrej Karpathy gist）

## 核心论点

大多数人使用 LLM 处理文档的方式是 [[wiki/concepts/rag|RAG]]：上传文件，查询时检索相关片段，生成答案。这种方式没有积累——每次提问都从零开始重建知识。Karpathy 提出了一种截然不同的模式：让 LLM **增量构建并维护一个持久化的 Wiki**，将原始来源编译为结构化、互链的 Markdown 文件集合。Wiki 是一个**持续复利的知识产物**。

## 关键要点

- **Wiki 不是缓存，是编译产物**：交叉引用已经建立，矛盾已经标注，综合分析已经反映了所有已读来源。知识被编译一次，然后持续更新，而非每次查询重新推导。
- **三层架构**：原始来源（不可变）→ Wiki 层（LLM 生成维护）→ 模式文件（定义结构与规范）。
- **三种核心操作**：录入（Ingest）将来源编译进 Wiki；查询（Query）从 Wiki 综合答案；巡检（Lint）维护 Wiki 健康。
- **人机分工明确**：人类负责策展来源、提问、思考意义；LLM 负责摘要、交叉引用、归档、记账——一切维护工作。
- **Obsidian 是 IDE，LLM 是程序员，Wiki 是代码库**——这个类比精确地描述了三者的关系。

## 重要细节

- 单次录入可能触及 10-15 个 Wiki 页面
- `index.md`（按内容组织的目录）和 `log.md`（按时间的操作记录）是两个关键导航文件
- 在中等规模（约 100 个来源、数百个页面）下，基于索引的检索效果出奇地好，无需嵌入式 RAG 基础设施
- 好的查询答案可以归档为新的 Wiki 页面，使探索本身也能复利
- 灵感追溯至 [[wiki/concepts/memex|Vannevar Bush 的 Memex]]（1945）——个人策展的知识库，文档间的关联与文档本身同样有价值

## 适用场景

- **个人成长**：追踪目标、健康、心理、自我提升
- **学术研究**：跨数周/数月深入一个课题
- **阅读伴侣**：为一本书构建角色、主题、情节的 Wiki
- **团队知识库**：由 LLM 维护，以 Slack/会议/文档为来源
- **竞品分析、尽职调查、旅行规划、课程笔记**等

## 推荐工具

- [[wiki/entities/obsidian|Obsidian]]：浏览端，图谱视图可视化 Wiki 结构
- Obsidian Web Clipper：将网页文章转为 Markdown
- [qmd](https://github.com/tobi/qmd)：本地 Markdown 搜索引擎（BM25 + 向量混合搜索）
- Marp：基于 Markdown 的幻灯片
- Dataview：Obsidian 插件，对 frontmatter 做查询

## 提及的实体

- [[andrej-karpathy|Andrej Karpathy]] — 该模式的提出者
- [[wiki/entities/obsidian|Obsidian]] — 推荐的 Wiki 浏览工具

## 涉及的概念

- [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]] — 本来源的核心主题
- [[wiki/concepts/rag|RAG]] — 作为对比基准
- [[wiki/concepts/knowledge-compilation|知识编译]] — Wiki 模式的本质
- [[wiki/concepts/memex|Memex]] — 历史渊源

## 与现有知识的关系

这是本 Wiki 的奠基来源，定义了整个知识库的运作方式。

## 待探索的问题

- [ ] Wiki 在大规模（1000+ 页面）下如何有效导航？
- [ ] 如何处理来源之间的深层矛盾？
- [ ] 多人协作场景下的冲突解决机制？
- [ ] 与传统 Zettelkasten 方法的异同？
