---
title: LLM Wiki 模式
type: concept
tags: [methodology, knowledge-management, llm, core-pattern]
sources: [LLM Wiki.md]
created: 2026-04-10
updated: 2026-04-10
---

# LLM Wiki 模式

## 定义

一种用大语言模型（LLM）增量构建和维护持久化个人 Wiki 的方法论。LLM 不是在查询时临时检索文档片段（如 [[wiki/concepts/rag|RAG]]），而是将每个新来源**编译**进一个结构化的、互链的 Markdown 知识库中。知识被编译一次，持续更新，而非每次重新推导。

## 详细说明

### 三层架构

1. **原始来源层**（`raw/`）：用户策展的源文档集合——文章、论文、图片、数据文件。不可变，LLM 只读不写。这是事实的来源。
2. **Wiki 层**（`wiki/`）：LLM 生成的 Markdown 文件目录——摘要、实体页、概念页、对比分析、综述。LLM 完全掌管这一层：创建页面、更新内容、维护交叉引用、保持一致性。
3. **模式层**（`CLAUDE.md`）：告诉 LLM Wiki 如何结构化、遵循什么规范、执行什么工作流的配置文件。用户与 LLM 共同演进此文件。

### 三种核心操作

- **录入（Ingest）**：新来源进入系统时，LLM 阅读全文、创建摘要、更新实体/概念页面、维护索引和日志。单次录入可触及 10-15 个页面。
- **查询（Query）**：用户提问时，LLM 先读索引定位相关页面，再综合答案。好的答案可归档为新的 Wiki 页面，使探索本身也能复利。
- **巡检（Lint）**：定期健康检查——查找矛盾、陈旧声明、孤立页面、缺失交叉引用、知识空白。

### 核心洞见

> Wiki 是一个**持续复利的知识产物**。交叉引用已经建立，矛盾已经标注，综合分析已经反映了所有已读来源。

人类放弃维护 Wiki 是因为维护负担增长速度超过了价值。LLM 不会厌倦，不会忘记更新交叉引用，可以在一次操作中触及 15 个文件。维护成本接近零，所以 Wiki 得以持续维护。

## 关键特征

- **持久化**：知识编译一次，持续更新，不随对话消失
- **增量式**：每个新来源增强而非替代已有知识
- **结构化**：互链的 Markdown 文件，而非扁平的文档集合
- **人机协作**：人类策展与思考，LLM 执行与维护

## 历史渊源

精神上与 [[wiki/concepts/memex|Vannevar Bush 的 Memex]]（1945）相关——私人的、主动策展的知识库，文档间的关联与文档本身同样有价值。Bush 无法解决的"谁来做维护"的问题，由 LLM 解决了。

## 相关概念

- [[wiki/concepts/rag|RAG]] — Wiki 模式试图超越的传统范式
- [[wiki/concepts/knowledge-compilation|知识编译]] — Wiki 模式的本质机制
- [[wiki/concepts/memex|Memex]] — 历史先驱

## 相关实体

- [[andrej-karpathy|Andrej Karpathy]] — 提出者
- [[wiki/entities/obsidian|Obsidian]] — 推荐的浏览工具

## 来源

- [[wiki/summaries/llm-wiki-pattern|LLM Wiki 模式（摘要）]]
