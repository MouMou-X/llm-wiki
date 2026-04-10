---
title: RAG（检索增强生成）
type: concept
tags: [llm, information-retrieval, methodology]
sources: [LLM Wiki.md]
created: 2026-04-10
updated: 2026-04-10
---

# RAG（检索增强生成）

## 定义

Retrieval-Augmented Generation，一种让 LLM 在回答问题时先从文档集合中检索相关片段、再基于检索结果生成答案的方法。这是当前大多数人使用 LLM 处理文档的主流方式。

## 详细说明

RAG 的工作流程：上传文档集合 → 将文档切分为片段并建立索引（通常基于向量嵌入）→ 查询时检索最相关的片段 → LLM 基于检索到的片段生成答案。

代表性产品包括 NotebookLM、ChatGPT 文件上传、以及大多数企业 RAG 系统。

### 核心局限（据 Karpathy 分析）

RAG 的根本问题在于**没有积累**。LLM 在每次提问时都从零开始重新发现知识。如果一个问题需要综合五个文档的信息，LLM 必须每次都重新找到并拼接相关片段。没有任何东西被建立起来。

这使得 RAG 适合简单的事实查询，但在需要深层综合分析时表现欠佳。

## 关键特征

- 无状态：每次查询独立，不积累知识
- 被动检索：在查询时才接触文档
- 依赖切分质量：片段切分方式直接影响检索效果
- 适合简单事实查询，不适合深层综合

## 相关概念

- [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]] — 试图超越 RAG 的替代范式
- [[wiki/concepts/knowledge-compilation|知识编译]] — RAG 缺乏的能力

## 来源

- [[wiki/summaries/llm-wiki-pattern|LLM Wiki 模式（摘要）]]
