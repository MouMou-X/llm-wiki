---
title: pandas 入门指南
type: summary
tags: [pandas, data-science, python]
sources: [raw/articles/入门指南 — pandas 3.0.2 文档.md]
created: 2026-04-11
updated: 2026-04-11
---

# pandas 入门指南

> 来源：`raw/articles/入门指南 — pandas 3.0.2 文档.md`

## 核心论点

pandas 是 Python 中处理表格数据（电子表格、数据库）的核心工具。其核心数据结构 [[wiki/concepts/dataframe|DataFrame]] 提供了从数据读写、子集选择、计算统计到可视化的一站式解决方案。

## 关键要点

- **安装**：通过 `conda install -c conda-forge pandas` 或 `pip install pandas` 安装
- **数据读写**：支持 csv、excel、sql、json、parquet 等多种格式，使用 `read_*` 导入、`to_*` 导出
- **子集选择**：提供灵活的行列切片、条件筛选方法
- **数据可视化**：集成 Matplotlib，内置散点图、柱状图、箱线图等图表类型
- **列运算**：支持逐元素运算，可基于已有列轻松创建新列
- **统计计算**：内置均值、中位数等基本统计量，支持 groupby 分组聚合（拆分-应用-合并）
- **表结构变换**：`melt()` 宽转长、`pivot()` 长转宽、透视表
- **表合并**：数据库式的 join/merge，支持按列或按行连接
- **时间序列**：丰富的日期时间处理工具
- **文本处理**：提供专用的字符串清洗与提取函数

## 重要细节

本文为 pandas 3.0.2 版本的官方入门指南，是功能概览性质的导航页，每个主题都指向更详细的入门教程和用户指南。

## 提及的实体

- [[wiki/entities/pandas|pandas]] — 本文档的主角，Python 数据分析库
- Matplotlib — pandas 绑定的绘图库

## 涉及的概念

- [[wiki/concepts/dataframe|DataFrame]] — pandas 的核心数据结构
- [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]] — 本 Wiki 可作为 pandas 学习笔记的结构化载体

## 与现有知识的关系

这是知识库中首批技术文档类来源，从之前的"知识管理方法论"扩展到了具体的"数据科学工具"领域。

## 待探索的问题

- [ ] pandas 与 Polars 等新一代 DataFrame 库的对比
- [ ] pandas 在大数据场景下的性能瓶颈与替代方案
