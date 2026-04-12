---
title: AutoResearch 使用指南（Karpathy）
type: summary
tags: [ml-research, ai-agents, automation, karpathy]
sources: ["raw/articles/A Guide to Andrej Karpathy's AutoResearch Automating ML with AI Agents.md"]
created: 2026-04-12
updated: 2026-04-12
---

# AutoResearch 使用指南（Karpathy）

> 来源：`raw/articles/A Guide to Andrej Karpathy's AutoResearch Automating ML with AI Agents.md`
> 原文链接：<https://www.datacamp.com/tutorial/guide-to-autoresearch>
> 作者：Bex Tuychiev，发表于 2026-03-23

## 核心论点

[[wiki/entities/autoresearch|AutoResearch]] 是 [[andrej-karpathy|Andrej Karpathy]] 于 2026 年 3 月 7 日开源的 ML 实验自动化工具。它让 AI 编码代理在单 GPU 上连夜运行上百个机器学习实验，只保留能超越当前最优结果的改动。人类不再直接编码或实时编排代理，而是通过一个 markdown 文件描述研究方向，扮演"研究顾问"的角色。

## 关键要点

- **定位**：不是超参数搜索（如 Optuna、Ray Tune），也不是 AutoML/NAS，而是给代理**任意修改代码**的自由，搜索空间为 LLM 所能想到的一切改动。
- **三文件契约**：
  - `prepare.py`（数据准备+评估，不可变，保证公平标尺）
  - `train.py`（代理的沙盒，模型和训练循环都在这里）
  - `program.md`（人类唯一接触的文件，定义研究方向与约束）
- **棘轮循环（ratchet loop）**：9 步循环——读 program.md → 分析历史 → 提出假设 → 修改 train.py → 提交 → 训练 5 分钟 → 评估 → 改善则保留提交，否则 `git reset HEAD~1`。
- **进度**：发布数日内 GitHub 获 21,000+ star；Karpathy 推文浏览量 860 万。
- **代理式工程的延伸**：从 vibe coding（人类审代码）→ agentic engineering（人类实时编排）→ 独立研究（人类只设方向）。

## 重要细节

### 架构与约束

- BPE 分词器词汇量为 **8,192**；评估指标为 `val_bpb`（验证位每字节）。
- `train.py` 默认约 **630 行**，包含 GPT 模型、Muon+AdamW 优化器和训练循环。
- `program.md` 中硬编码的基线：`val_bpb: 0.997900`，峰值显存 **45 GB**。
- 每次实验固定 **5 分钟挂钟时间预算**，约每小时 12 个实验。
- 设计约束："在其他条件相同的情况下，越简单越好"——防止丑陋的复杂化。
- 关键指令："NEVER STOP"——循环开始后代理不得停下来征求人类意见。

### 实验结果

| 运行 | 实验数 | 保留的改进 | 结果 |
| --- | --- | --- | --- |
| 首次过夜（单 GPU） | 83 | 15 | val_bpb: 1.000 → 0.975 |
| 2 天扩展（depth-12） | ~700 | ~20 | 全部可叠加，可迁移到 depth-24 |
| 生产影响 | — | — | time-to-GPT-2 基准：2.02h → 1.80h（快 11%） |
| 社区复现 | 126 | — | val_bpb: 0.9979 → 0.9697 |

- 代理发现了诸如 QKnorm 缺失注意力锐化的缩放乘子、Value Embeddings 受益于正则化、AdamW beta 与权重衰减调度等结构性改动。
- Shopify CEO Tobi Lutke 在 0.8B 参数的查询扩展模型上，37 个实验就取得 **19% 验证得分提升**。

### 创造力天花板

- [GitHub Issue #22](https://github.com/karpathy/autoresearch/issues/22) 指出：棘轮只接受立即改善 `val_bpb` 的改动，代理无法"先退一步再前进两步"。
- Karpathy 在 Hacker News 上承认代理在开放性问题上显得"胆怯害怕"，归因于 [[wiki/concepts/rag|RLHF]] 训练偏好保守输出。
- 5 分钟固定预算让慢见效的改动不可见；对同一验证集运行上百实验还有过拟合风险。
- 社区提案：meta-prompt 优化（用第二个代理重写 `program.md`）、多样性指令、周期性"重置"实验。

### 适用场景

- 任何能定义**自动评分函数**的小模型任务：搜索排名、商品分类、临床命名实体识别、欺诈打分、意图分类。
- 要求：训练快、评分清晰、改进能在放大规模时迁移。
- 当实验速度比人工快 100 倍时，**评估管道本身会成为瓶颈**——静态基准很快饱和。

## 提及的实体

- [[andrej-karpathy|Andrej Karpathy]] — 工具作者，提出"代理式工程"与"研究顾问"的定位
- [[wiki/entities/autoresearch|AutoResearch]] — 本文主角，开源 ML 自动化工具
- **Bex Tuychiev** — DataCamp 本文作者
- **Tobi Lutke（Shopify CEO）** — 早期适用者，查询扩展模型提升 19%

## 涉及的概念

- [[wiki/concepts/agentic-engineering|代理式工程（Agentic Engineering）]] — Karpathy 2026-02 提出，描述人类编排代理、而非亲自写代码的工作方式
- [[wiki/concepts/ratchet-loop|棘轮循环]] — AutoResearch 的核心机制：只进不退的 git 历史
- [[wiki/concepts/three-file-architecture|三文件架构]] — 不可变评估器 + 代理沙盒 + 人类指令的契约
- [[wiki/concepts/rag|RLHF]] — 被 Karpathy 认为是代理"胆怯"行为的根源之一

## 与现有知识的关系

- 本来源扩展了对 [[andrej-karpathy|Karpathy]] 的实体页：除了 [[wiki/concepts/llm-wiki-pattern|LLM Wiki 模式]]，他在 AI 自动化研究工具方面也有重要贡献。
- 本文提出的"人类是研究顾问"的定位，与 LLM Wiki 模式中"LLM 维护 Wiki、人类筛选来源"的分工异曲同工——都是将人类推向**方向性判断**而把执行工作交给 AI。

## 待探索的问题

- [ ] 棘轮循环能否在 LLM Wiki 的录入/巡检工作流中借鉴？（例如每次变更必须通过一个"验证指标"才保留）
- [ ] AlphaEvolve 的进化式方法与棘轮的单一血统有哪些具体差异？
- [ ] meta-prompt 优化方案是否已有公开的实现尝试？
- [ ] "评估管道成为瓶颈"是否预示了下一个值得关注的工具方向？
