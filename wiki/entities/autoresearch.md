---
title: AutoResearch
type: entity
tags: [tool, open-source, ml-research, ai-agents]
sources: ["raw/articles/A Guide to Andrej Karpathy's AutoResearch Automating ML with AI Agents.md"]
created: 2026-04-12
updated: 2026-04-12
---

# AutoResearch

## 概述

由 [[andrej-karpathy|Andrej Karpathy]] 开源的 Python 工具，让 AI 编码代理在单 GPU 上不间断地运行 ML 实验循环，只保留能改善验证指标的改动。其核心机制是 [[wiki/concepts/ratchet-loop|棘轮循环]]，其设计哲学体现在 [[wiki/concepts/three-file-architecture|三文件架构]]中。

## 关键信息

| 属性 | 值 |
| --- | --- |
| 类别 | 工具（开源软件） |
| 作者 | [[andrej-karpathy\|Andrej Karpathy]] |
| 发布日期 | 2026-03-07 |
| 许可证 | MIT |
| 仓库 | <https://github.com/karpathy/autoresearch> |
| 相关领域 | 机器学习、AI 代理、自动化研究 |
| 默认任务 | 在 FineWeb-Edu 上训练 GPT 模型 |
| 评估指标 | `val_bpb`（验证位每字节） |
| 实验预算 | 每次 5 分钟挂钟时间 |
| 最低硬件 | NVIDIA GPU 20+ GB 显存，Python 3.10+，`uv` |

## 与本 Wiki 的关联

AutoResearch 和 [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]]代表了 Karpathy 在"人机分工"问题上的两种具体回答：前者把 ML 实验的执行交给代理，后者把知识维护交给 LLM；两者都让人类专注于**方向性与判断性**工作。

## 三文件契约

- `prepare.py` — 数据与评估，**不可变**
- `train.py` — 代理的沙盒（约 630 行），可任意修改
- `program.md` — 人类书写的研究议程

## 关键结果

- 首次过夜运行：83 个实验，15 个保留，`val_bpb` 1.000 → 0.975
- 社区复现：126 个实验，`val_bpb` 0.9979 → 0.9697
- 生产效果：time-to-GPT-2 基准由 2.02h 缩短至 1.80h（快 11%）
- Shopify CEO Tobi Lutke 适配后取得 19% 验证得分提升

## 已知局限

- **创造力天花板**：棘轮只接受立即改善的改动，代理困于局部搜索
- 受 RLHF 训练影响，代理在开放问题上偏保守
- 5 分钟固定预算对慢见效的改动不友好
- 对同一验证集大量实验带来过拟合风险

## 相关页面

- [[wiki/concepts/ratchet-loop|棘轮循环]] — 核心实验机制
- [[wiki/concepts/three-file-architecture|三文件架构]] — 设计契约
- [[wiki/concepts/agentic-engineering|代理式工程]] — 所属的工作范式
- [[andrej-karpathy|Andrej Karpathy]] — 作者

## 来源

- [[wiki/summaries/autoresearch-guide|AutoResearch 使用指南（摘要）]]
