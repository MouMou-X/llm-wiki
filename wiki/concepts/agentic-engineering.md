---
title: 代理式工程（Agentic Engineering）
type: concept
tags: [ai-agents, engineering-methodology, karpathy]
sources: ["raw/articles/A Guide to Andrej Karpathy's AutoResearch Automating ML with AI Agents.md"]
created: 2026-04-12
updated: 2026-04-12
---

# 代理式工程（Agentic Engineering）

## 定义

[[andrej-karpathy|Andrej Karpathy]] 于 2026 年 2 月提出的术语，用以描述工程师与 AI 代理协作的新工作范式：

> "你 99% 的时间不再亲自写代码。你在编排代理去做事、并充当监督者。"

## 详细说明

Karpathy 将人机协作分为三个递进阶段：

1. **Vibe coding（氛围编码）**：人类给出提示，AI 写代码，人类审查。代理是助手。
2. **Agentic engineering（代理式工程）**：人类**实时编排**多个代理，自己不再直接写代码。代理是执行者。
3. **独立研究（Independent research）**：人类只在 markdown 中描述研究方向，代理自己运行数小时乃至数日。代理是研究者。

每一阶段都减少了人类在"执行"上的存在感——从作家（writer），到导演（director），再到 [[wiki/entities/autoresearch|AutoResearch]] 中所说的"研究顾问（research advisor）"。

## 关键特征

- 人类角色从"编写代码"转变为"设定方向与约束"
- 代理自主完成大量工作（实时编排或离线运行）
- 需要明确的契约界面（如 [[wiki/concepts/three-file-architecture|三文件架构]]）来约束代理行为
- 依赖评估机制（测试、指标、棘轮）来替代人类审查

## 相关概念

- [[wiki/concepts/ratchet-loop|棘轮循环]] — 独立研究阶段的核心机制
- [[wiki/concepts/three-file-architecture|三文件架构]] — 代理式工程的一种契约形式
- [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]] — 同一思想在知识管理领域的映射：LLM 做执行，人类做筛选

## 相关实体

- [[andrej-karpathy|Andrej Karpathy]] — 术语提出者
- [[wiki/entities/autoresearch|AutoResearch]] — 代理式工程"独立研究"阶段的典型实现

## 来源

- [[wiki/summaries/autoresearch-guide|AutoResearch 使用指南（摘要）]]
