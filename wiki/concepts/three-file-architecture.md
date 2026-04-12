---
title: 三文件架构（Three-File Architecture）
type: concept
tags: [ml-research, design-pattern, ai-agents]
sources: ["raw/articles/A Guide to Andrej Karpathy's AutoResearch Automating ML with AI Agents.md"]
created: 2026-04-12
updated: 2026-04-12
---

# 三文件架构（Three-File Architecture）

## 定义

[[wiki/entities/autoresearch|AutoResearch]] 采用的一种"契约式"设计：将代理研究环境拆分成三个职责分明的文件，并对每个文件规定明确的**所有权与可变性**，让人类、代理、评估机制三方各司其职。

## 详细说明

| 文件 | 所有者 | 可变性 | 职责 |
| --- | --- | --- | --- |
| `prepare.py` | 无人修改 | 不可变 | 数据准备与评估函数，保证公平标尺 |
| `train.py` | 代理 | 可任意修改 | 模型架构、优化器、训练循环 |
| `program.md` | 人类 | 仅人类修改 | 研究议程、约束、基线、失败处理规则 |

### prepare.py — 不可变的评估器

构建 BPE 分词器（8,192 词汇量），处理训练语料，定义 `val_bpb`（验证位每字节）指标。**任何一方都不应修改**——这是所有实验的共同标尺，保证了不同实验之间的可比性。

### train.py — 代理的沙盒

默认约 630 行，包含 GPT 模型、Muon+AdamW 优化器、完整训练循环。代理可以自由替换激活函数、重构注意力头、改动学习率调度、修改权重初始化——**只要代码仍能训练并产出 `val_bpb`**。

### program.md — 人类的议程

人类唯一接触的文件。典型内容：

- 基线指标（如 `val_bpb: 0.997900`，峰值显存 45 GB）
- 实验与结果提取的精确命令
- 失败处理规则（typo 就修后重跑；根本性错误就放弃；超过 10 分钟就杀掉）
- 关键指令"NEVER STOP"
- 设计约束：越简单越好

## 关键特征

- **职责分离**：评估、执行、方向三者解耦
- **不可变的标尺**：`prepare.py` 的不可动摇保证了实验之间可比
- **单一入口**：人类只需编辑一个 markdown 文件即可引导整个实验流程
- **可迁移**：任何能定义自动评分函数的领域都可借鉴——搜索排名、欺诈打分、命名实体识别等

## 权衡与盲点

`prepare.py` 的不可变性是"公平"的来源，也是"盲点"的来源——针对同一评估运行上百次实验有**过拟合验证集**的风险。这意味着评估集本身需要随生产数据与边界用例演化，否则瓶颈将从训练转移到评估管道。

## 相关概念

- [[wiki/concepts/ratchet-loop|棘轮循环]] — 这一架构之上运行的执行循环
- [[wiki/concepts/agentic-engineering|代理式工程]] — 这一架构是"代理式工程"的契约实现

## 相关实体

- [[wiki/entities/autoresearch|AutoResearch]] — 该架构的首个公开实现

## 来源

- [[wiki/summaries/autoresearch-guide|AutoResearch 使用指南（摘要）]]
