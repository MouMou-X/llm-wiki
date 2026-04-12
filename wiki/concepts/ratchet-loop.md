---
title: 棘轮循环（Ratchet Loop）
type: concept
tags: [ml-research, automation, algorithm-pattern]
sources: ["raw/articles/A Guide to Andrej Karpathy's AutoResearch Automating ML with AI Agents.md"]
created: 2026-04-12
updated: 2026-04-12
---

# 棘轮循环（Ratchet Loop）

## 定义

[[wiki/entities/autoresearch|AutoResearch]] 的核心机制：代理在"提出—训练—评估—保留/回退"的循环中不断尝试改动，**只保留能改善评估指标的改动**，从而让代码库像棘轮一样只进不退。

## 详细说明

一次迭代的 9 个步骤（由 `program.md` 定义）：

1. 读取 `program.md`，理解当前研究方向与约束。
2. 查看当前 `train.py` 和 `results.tsv` 中的历史。
3. 提出假设（架构变化、优化器调整、训练修改）。
4. 修改 `train.py`。
5. 提交到一个 git 分支。
6. 训练**固定 5 分钟挂钟时间**（硬预算）。
7. 若训练崩溃，记录失败并回退重试。
8. 用 `val_bpb` 评估，记入 `results.tsv`。
9. 若指标改善 → 保留提交；否则 `git reset HEAD~1` 回退。

"棘轮"之名来自 git 历史本身：每次成功产生一个提交，失败则被回退；代码库只会前进，不会后退。

## 关键特征

- **固定预算**：每次实验 5 分钟，使结果可直接比较（快收敛与低收敛在同等立足点上被评估）
- **只进不退**：git 历史就是研究记忆，代理读取自身历史决定下一步
- **单一血统（single lineage）**：不同于进化算法的种群/交叉/变异，棘轮只维护一条主线；LLM 同时扮演"变异算子"和"选择压力"
- **运行速率**：每小时约 12 次实验

## 与进化算法的对比

| 维度 | 棘轮循环 | 进化算法 |
| --- | --- | --- |
| 候选数量 | 1（单线） | 多（种群） |
| 变异来源 | LLM 基于历史生成 | 显式的变异/交叉算子 |
| 选择压力 | 严格单调改善 | 适应度分布 |
| 能否暂时变差 | 不能 | 能（种群内保留） |

## 局限：创造力天花板

[GitHub Issue #22](https://github.com/karpathy/autoresearch/issues/22) 指出，由于棘轮只接受立即改善的改动，代理无法执行"先变坏再变好"的策略，容易陷入局部最优。人类研究者惯常的"大胆一试"对棘轮是被禁止的。

社区提出的缓解方案：

- meta-prompt 优化（用第二个代理重写 `program.md`）
- 奖励多样性的指令
- 周期性从早期 checkpoint 重启

## 相关概念

- [[wiki/concepts/three-file-architecture|三文件架构]] — 棘轮循环依赖的文件契约
- [[wiki/concepts/agentic-engineering|代理式工程]] — 棘轮是"独立研究"阶段的核心执行机制

## 相关实体

- [[wiki/entities/autoresearch|AutoResearch]] — 棘轮循环的典型实现

## 来源

- [[wiki/summaries/autoresearch-guide|AutoResearch 使用指南（摘要）]]
