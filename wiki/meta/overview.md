---
title: 知识库概览
type: meta
tags: [overview, meta]
sources: [LLM Wiki.md]
created: 2026-04-10
updated: 2026-04-10
---

# 知识库概览

## 综述

本知识库是一个基于 [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]]构建的个人知识管理系统，灵感来自 [[andrej-karpathy|Andrej Karpathy]] 的公开 gist。

核心理念：LLM 负责编写和维护所有 Wiki 页面，人类负责筛选来源、提出问题和指导分析。知识不是在查询时临时检索（如 [[wiki/concepts/rag|RAG]]），而是被预先[[wiki/concepts/knowledge-compilation|编译]]为结构化、互链的 Markdown 页面，持续积累和更新。

## 当前状态

| 指标 | 数值 |
| --- | --- |
| 来源总数 | 1 |
| 摘要页 | 1 |
| 实体页 | 2 |
| 概念页 | 4 |
| 对比页 | 1 |
| 元分析页 | 1（本页） |

## 核心主题

目前本 Wiki 围绕一个核心主题展开：

1. **知识管理方法论**：如何用 LLM 构建和维护个人知识库，以及这种方式与传统 RAG 的本质区别

随着更多来源的录入，预计将涌现出更多主题。

## 当前理解

基于已有的单一来源，核心判断是：

- LLM Wiki 模式代表了从"被动检索"到"主动编译"的范式转变
- 该模式的可行性依赖于 LLM 近乎零成本的维护能力
- 历史上类似的愿景（[[wiki/concepts/memex|Memex]]）因缺乏自动化维护能力而未能实现

## 开放问题

- [ ] 大规模（1000+ 页面）下的导航与检索策略？
- [ ] 多领域知识库如何组织？按主题分库还是统一管理？
- [ ] 如何评估 Wiki 质量——什么指标说明知识库是健康的？
- [ ] 与 Zettelkasten、PARA 等个人知识管理方法的对比？

## 知识空白

- 尚无实际使用案例或经验数据
- 缺少对大规模 Wiki 运作的讨论
- 缺少与其他知识管理方法论的系统对比
- 缺少对 LLM 生成内容质量控制的讨论

## 相关页面

- [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]]
- [[wiki/summaries/llm-wiki-pattern|LLM Wiki 模式（摘要）]]
