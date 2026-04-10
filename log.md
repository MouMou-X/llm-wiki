---
title: 操作日志
type: log
---

# 操作日志

> 按时间倒序记录所有 Wiki 操作。每条以 `## [日期] 操作类型 | 标题` 开头。
> 可用 `grep "^## \[" log.md | tail -5` 查看最近 5 条记录。

---

## [2026-04-10] ingest | LLM Wiki 模式 - Andrej Karpathy

首次来源录入：Andrej Karpathy 的 LLM Wiki gist。

来源位置：`LLM Wiki.md`（根目录，参考文档）

新建页面：
- [[wiki/summaries/llm-wiki-pattern]] — 来源摘要
- [[andrej-karpathy]] — 实体页
- [[wiki/entities/obsidian]] — 实体页
- [[wiki/concepts/llm-wiki-pattern]] — 概念页
- [[wiki/concepts/rag]] — 概念页
- [[wiki/concepts/knowledge-compilation]] — 概念页
- [[wiki/concepts/memex]] — 概念页
- [[wiki/comparisons/wiki-vs-rag]] — 对比页
- [[wiki/meta/overview]] — 概览页

## [2026-04-10] ingest | Wiki 初始化

初始化知识库结构，基于 Andrej Karpathy 的 LLM Wiki 模式。

操作内容：
- 创建完整目录结构（raw/、wiki/、templates/）
- 编写 CLAUDE.md 架构规范文件
- 创建 index.md 索引
- 创建 log.md 操作日志
- 编写所有模板文件
