---
title: pandas 文本数据处理
type: summary
tags: [pandas, text-processing, python, str-accessor]
sources: [raw/articles/如何操作文本数据 — pandas 3.0.2 文档.md]
created: 2026-04-11
updated: 2026-04-11
---

# pandas 文本数据处理

> 来源：`raw/articles/如何操作文本数据 — pandas 3.0.2 文档.md`

## 核心论点

pandas 通过 `str` 访问器提供了一套逐元素的字符串操作方法，可以像处理单个字符串一样对整列文本数据进行批量操作，无需手动遍历。

## 关键要点

- **`str` 访问器**：通过 `Series.str` 访问字符串方法，所有操作逐元素应用于列中的每个值
- **大小写转换**：`str.lower()` 将整列字符串转为小写
- **字符串拆分**：`str.split(",")` 按分隔符拆分，可链式调用 `str.get(0)` 提取特定部分
- **模式匹配**：`str.contains("pattern")` 返回布尔 Series，可用作条件索引筛选数据
- **长度计算**：`str.len()` 计算每个字符串的长度，配合 `idxmax()` 找到最长值
- **值替换**：`replace({"old": "new"})` 通过字典映射批量替换值，比 `str.replace()` 更适合多值映射

## 重要细节

- 教程以泰坦尼克号数据集为例，演示了从 Name 列提取姓氏、查找特定乘客等实际操作
- `str.contains()` 和 `str.extract()` 支持正则表达式
- 使用 `str.replace()` 做多值替换时要注意顺序陷阱：先替换 `"female"→"F"` 再替换 `"male"→"M"` 会出错，因为 `"female"` 包含 `"male"`

> [!warning] 注意
> 多值替换时应使用 `replace(dict)` 而非链式 `str.replace()`，以避免顺序依赖导致的错误。

## 提及的实体

- [[wiki/entities/pandas|pandas]] — 提供 `str` 访问器的数据分析库

## 涉及的概念

- [[wiki/concepts/dataframe|DataFrame]] — `str` 访问器作用于 DataFrame 的列（Series）

## 与现有知识的关系

与 [[wiki/summaries/pandas-getting-started|pandas 入门指南]] 互补，本文深入展开了入门指南中"文本处理"板块的具体用法。

## 待探索的问题

- [ ] pandas `str` 方法与 Python 原生字符串方法的性能对比
- [ ] 正则表达式在 `str.contains()` 和 `str.extract()` 中的高级用法
