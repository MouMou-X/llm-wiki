---
title: DataFrame
type: concept
tags: [pandas, data-structure, tabular-data]
sources: [raw/articles/入门指南 — pandas 3.0.2 文档.md]
created: 2026-04-11
updated: 2026-04-11
---

# DataFrame

## 定义

DataFrame 是 [[wiki/entities/pandas|pandas]] 中的核心二维数据结构，用于表示带有行索引和列标签的表格数据，类似于电子表格或 SQL 表。

## 详细说明

DataFrame 是 pandas 围绕其构建整个 API 的中心抽象。每一列是一个 Series（一维数组），可以拥有不同的数据类型（数值、字符串、日期时间等）。行和列都有标签（索引），支持通过标签或位置进行灵活的数据访问。

DataFrame 的设计理念是让用户像操作电子表格一样编程式地处理数据：选择行列、按条件筛选、添加计算列、分组聚合——全部通过方法链式调用完成，无需手动循环。

## 关键特征

- **二维表结构**：行（index）× 列（columns），每列可以是不同数据类型
- **丰富的 IO**：可从 CSV、Excel、SQL、JSON、Parquet 等格式直接创建
- **向量化运算**：列操作逐元素执行，避免 Python 层面的 for 循环
- **灵活索引**：支持 `loc`（标签索引）、`iloc`（位置索引）、布尔索引
- **分组聚合**：`groupby()` 实现拆分-应用-合并模式
- **结构变换**：`melt()`/`pivot()` 在宽格式与长格式之间转换

## 相关概念

- [[wiki/concepts/rag|RAG]] — DataFrame 可作为 RAG 系统中结构化数据的载体
- [[wiki/concepts/knowledge-compilation|知识编译]] — DataFrame 的表结构本身就是一种知识的结构化编译

## 相关实体

- [[wiki/entities/pandas|pandas]] — DataFrame 的实现库

## 来源

- [[wiki/summaries/pandas-getting-started|pandas 入门指南]]
- [[wiki/summaries/pandas-text-data|pandas 文本数据处理]]
