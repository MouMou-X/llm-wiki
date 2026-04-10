---
title: Obsidian
type: entity
tags: [tool, knowledge-management, markdown]
sources: [LLM Wiki.md]
created: 2026-04-10
updated: 2026-04-10
---

# Obsidian

## 概述

基于本地 Markdown 文件的知识管理工具。在 [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]]中担任"IDE"角色——用户通过 Obsidian 浏览 Wiki，而 LLM 在后台编写和维护内容。

## 关键信息

| 属性 | 值 |
| --- | --- |
| 类别 | 工具 |
| 类型 | 本地优先的 Markdown 知识库 |
| 核心特性 | 双链、图谱视图、插件生态 |

## 与本 Wiki 的关联

本知识库运行在 Obsidian 之上。Obsidian 提供了浏览、搜索和可视化 Wiki 结构的界面，而 LLM 通过文件系统操作来生成和维护页面内容。

## 关键功能（在 Wiki 模式中）

- **图谱视图**：可视化页面间的链接结构，发现孤立页面和枢纽页面
- **Web Clipper**：浏览器扩展，将网页文章转为 Markdown 并放入 `raw/`
- **Dataview 插件**：对 YAML frontmatter 做查询，生成动态表格
- **Marp 插件**：将 Markdown 渲染为幻灯片

## 相关页面

- [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]] — Obsidian 在该模式中的角色定位
- [[andrej-karpathy|Andrej Karpathy]] — 推荐使用 Obsidian 的人

## 来源

- [[wiki/summaries/llm-wiki-pattern|LLM Wiki 模式（摘要）]]
