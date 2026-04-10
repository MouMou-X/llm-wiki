---
title: 知识编译
type: concept
tags: [methodology, knowledge-management, core-idea]
sources: [LLM Wiki.md]
created: 2026-04-10
updated: 2026-04-10
---

# 知识编译

## 定义

将原始、非结构化的来源材料（文章、论文、笔记）转化为结构化、互链、可导航的知识页面的过程。类比软件工程中的"编译"——源代码被编译一次，产出可执行产物，而非每次运行时重新解释。

## 详细说明

在 [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]]中，知识编译是核心机制。当一个新来源被录入时，LLM 不只是索引它以供日后检索，而是：

1. **阅读**全文
2. **提取**关键信息
3. **整合**进现有 Wiki——更新实体页面、修订主题摘要、标注新数据与旧声明的矛盾、强化或挑战正在演进的综合分析

知识被编译一次，然后**保持更新**，而非每次查询时重新推导。这与 [[wiki/concepts/rag|RAG]] 的"每次查询重新发现"形成根本对比。

## 关键特征

- **一次编译，持续更新**：不是缓存，是真正的转化
- **增量式**：每个新来源增强已有结构
- **跨来源综合**：自动发现来源间的关联与矛盾
- **产出持久化产物**：Wiki 页面即编译产物

## 相关概念

- [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]] — 知识编译在其中是核心操作
- [[wiki/concepts/rag|RAG]] — 缺乏编译步骤的替代方案

## 来源

- [[wiki/summaries/llm-wiki-pattern|LLM Wiki 模式（摘要）]]
