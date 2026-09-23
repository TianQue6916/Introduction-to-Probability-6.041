# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 2 — Conditioning and Bayes' Rule（条件作用与贝叶斯规则）</span>

<span style="color:#7f8c8d;">Instructor: John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Review of probability models（概率模型回顾）</span>

**阅读**：教材 Sections 1.3–1.4。

**Lecture outline（本讲大纲）**：
- Review（回顾）。
- Conditional probability（条件概率）。
- 三个重要工具：
  - **Multiplication rule（乘法规则）**。
  - **Total probability theorem（全概率定理）**。
  - **Bayes' rule（贝叶斯规则）**。

**Review（回顾）**：
- 样本空间 $\Omega$：互斥、穷尽、正确粒度。
- 事件：样本空间的子集。
- 概率分配给事件：
  1. $P(A) \ge 0$。
  2. $P(\Omega) = 1$。
  3. 若 $A \cap B = \emptyset$，则 $P(A \cup B) = P(A) + P(B)$。
  3'. 若 $A_1, A_2, \ldots$ 是两两不相交的事件，则 $P(A_1 \cup A_2 \cup \cdots) = P(A_1) + P(A_2) + \cdots$（可数可加）。
- **Problem solving（解题步骤）**：明确样本空间 → 定义概率律 → 确定感兴趣的事件 → 计算……

> <span style="color:#7f8c8d;">Bertsekas §1.1–1.2</span>

> <span style="color:#1e8449;">**[note] Note（译者注，回顾）:**</span> 这一页把上一讲（Lec 01）的公理与解题流程压缩成回顾：样本空间（互斥+穷尽+正确粒度）、事件（子集）、概率律（三条公理 + 可数可加）。特别注意"3'"——可数可加性是本讲计算"无穷事件并的概率"（如后续 $P(\text{偶数})$）的前提。解题四步（样本空间 → 概率律 → 事件 → 计算）是本课程反复使用的**问题求解模板**：先建模，再计算。本讲的条件概率把"事件"的概念升级——给定 $B$ 发生后，整个世界（样本空间）都变了。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditional probability（条件概率）</span>

- $P(A \mid B)$ = 在已知 $B$ 发生的条件下，$A$ 的概率。
  - $B$ 是我们的 **new universe（新宇宙）**。
- **Definition（定义）**：假设 $P(B) \neq 0$，
```math
P(A \mid B) = \frac{P(A \cap B)}{P(B)} .
```
若 $P(B) = 0$，则 $P(A \mid B)$ 未定义。

> <span style="color:#7f8c8d;">Bertsekas §1.3, p.18</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 条件概率是"**在缩小了的世界上重新分配概率**"：已知 $B$ 发生，样本空间从 $\Omega$ 收缩为 $B$（"$B$ 是新的宇宙"），原来在 $\Omega$ 上的概率律被"重新归一化"——$\frac{P(A \cap B)}{P(B)}$ 就是把"$A$ 与 $B$ 的交"在 $B$ 上归一化（除以 $P(B)$ 使 $P(B\mid B)=1$）。卡点诊断：**$P(A\mid B)$ 不是 $P(A)$ 的"一部分"，而是把 $A$ 限制在 $B$ 内再看比例**。直观例子：全班中"戴眼镜"概率 $P(A)$，已知"男生"$B$ 后，"戴眼镜且男生"占"男生"的比例就是 $P(A\mid B)$。要求 $P(B) \neq 0$（$B$ 必须"可能发生"），否则条件概率无意义。这与你在 100B 学的"测度论条件"呼应：条件概率本质是"在子集 $B$ 上重新归一化的测度"。

**Die roll example（骰子例子）**：
设 $B$ 是事件"$\min(X, Y) = 2$"，$M = \max(X, Y)$。求：
- $P(M = 1 \mid B)$
- $P(M = 2 \mid B)$

> <span style="color:#7f8c8d;">图：四面骰两次的 16 格点图，标出事件 $B = \{\min(X,Y) = 2\}$（格点 $(2,2),(2,3),(2,4),(3,2),(4,2)$ 共 5 个）。</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 验算这个条件概率例子（四面骰两次，16 个等可能结果）：
> - $B = \{\min(X,Y)=2\}$ 含 5 个格点：$(2,2),(2,3),(2,4),(3,2),(4,2)$，故 $P(B) = \frac{5}{16}$。
> - $P(M=1 \mid B)$：$M=1$ 意味着 $\max = 1$，即 $(1,1)$——但 $\min(1,1)=1 \neq 2$，不在 $B$ 内，所以 $P(M=1 \cap B) = 0$，$P(M=1\mid B) = 0$ ✓（直觉：$\min = 2$ 时最大至少是 2）。
> - $P(M=2 \mid B)$：$M=2$ 且 $\min=2$ 意味着两骰都 $\le 2$ 且至少一个为 2，即 $(2,2)$ 唯一，$P(M=2 \cap B) = \frac{1}{16}$，故 $P(M=2\mid B) = \frac{1/16}{5/16} = \frac{1}{5}$ ✓。
> 这个例子演示条件概率的"重新归一化"：在 $B$ 这个 5 点集合上，$M=2$ 占其中 1 点，比例 $\frac{1}{5}$。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Models based on conditional probabilities（基于条件概率的模型）</span>

> <span style="color:#7f8c8d;">Bertsekas §1.3, p.23（基于条件概率建模，Example 1.9 雷达例）</span>

**Example（例）**：事件 $A$：飞机正在上方飞行；事件 $B$：雷达屏幕上有显示。
- $P(B \mid A) = 0.99$，$P(B^c \mid A) = 0.01$。
- $P(A) = 0.05$，$P(A^c) = 0.95$。
- $P(B \mid A^c) = 0.10$，$P(B^c \mid A^c) = 0.90$。

求：$P(A \cap B) = ?$，$P(B) = ?$，$P(A \mid B) = ?$

> <span style="color:#7f8c8d;">图：雷达例子的概率树——根节点 $A$（概率 0.05）/$A^c$（0.95），$A$ 下分 $B\mid A$（0.99）/$B^c\mid A$（0.01），$A^c$ 下分 $B\mid A^c$（0.10）/$B^c\mid A^c$（0.90），树叶标注交事件 $A \cap B$ 等。</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 验算这个雷达例子（这是条件概率的标准入门题）：
> - $P(A \cap B) = P(A)P(B\mid A) = 0.05 \times 0.99 = 0.0495$ ✓。
> - $P(B) = P(A)P(B\mid A) + P(A^c)P(B\mid A^c) = 0.0495 + 0.95 \times 0.10 = 0.0495 + 0.095 = 0.1445$（全概率定理的雏形）。
> - $P(A\mid B) = \frac{P(A \cap B)}{P(B)} = \frac{0.0495}{0.1445} \approx 0.343$——**只有约 34%**！
> 卡点诊断（反直觉）：$P(B\mid A) = 0.99$ 很高（飞机在时雷达 99% 显示），但 $P(A\mid B) \approx 0.34$ 很低（雷达显示时飞机真的在的概率只有 1/3）——因为"虚警"（$A^c$ 时也 10% 显示）太多，且飞机本身很少（$P(A)=0.05$）。这正是"**先验概率**"的威力：已知 $B$ 后，$P(A\mid B)$ 从先验 $0.05$ 提升到约 $0.34$，但远未到"确认"。跨课程连接：这个例子是"**贝叶斯推断**"的最小模型——你用新的观测（雷达）更新对"飞机在"的信念（后验），与 Lec 21 的贝叶斯统计推断一脉相承；"虚警率高时后验低"的教训，也像你 6.042J 学的"条件概率反直觉"（如蒙提霍尔问题）——观测证据不足时不能草率下结论。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Multiplication rule（乘法规则）</span>

**Multiplication rule（乘法规则）**：
```math
P(A \cap B \cap C) = P(A) \cdot P(B \mid A) \cdot P(C \mid A \cap B) .
```
一般地，
```math
P(A_1 \cap A_2 \cap \cdots \cap A_n) = P(A_1) P(A_2 \mid A_1) P(A_3 \mid A_1 \cap A_2) \cdots P(A_n \mid A_1 \cap \cdots \cap A_{n-1}) .
```

> <span style="color:#7f8c8d;">Bertsekas §1.3, p.24</span>

> <span style="color:#7f8c8d;">图：乘法规则的序列树——根节点 $A$，下分 $B\mid A$ 与 $B^c\mid A$；$B\mid A$ 下再分 $C\mid(A\cap B)$ 与 $C^c\mid(A\cap B)$，树叶为交事件 $A\cap B\cap C$ 等。沿路径相乘各条件概率即得 $P(A\cap B\cap C)$。</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板）:**</span> 乘法规则是条件概率定义的**链式展开**，证明只需反复用定义：$P(A \cap B \cap C) = P(A \cap B) \cdot P(C \mid A \cap B) = P(A) \cdot P(B \mid A) \cdot P(C \mid A \cap B)$。直觉：**要同时发生 $A, B, C$，先看 $A$ 的概率，再在 $A$ 已发生的条件下看 $B$，再在 $A, B$ 都已发生的条件下看 $C$**——每一步都"追加一个条件"。这个"**链式条件化**"是概率论最常用的工具之一：它把"同时发生"分解成"依次发生"，正符合你在 100B 学的"逐步构造"思想（如区间逐步细分）。在概率树（如雷达例子的树）上，乘法规则就是"沿路径乘各边概率"——树模型的天然计算法则。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Total probability theorem（全概率定理）</span>

- **Divide and conquer（分而治之）**。
- 把样本空间划分为 $A_1, A_2, A_3$。
- 已知对每个 $i$ 有 $P(B \mid A_i)$。
- **计算 $P(B)$ 的一种方法**：
```math
P(B) = P(A_1)P(B \mid A_1) + P(A_2)P(B \mid A_2) + P(A_3)P(B \mid A_3) .
```
一般地，若 $A_1, A_2, \ldots, A_n$ 是样本空间的划分（互斥且并集为 $\Omega$），则
```math
P(B) = \sum_{i=1}^{n} P(A_i) P(B \mid A_i) .
```

> <span style="color:#7f8c8d;">Bertsekas §1.4, p.28</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 证明策略模板）:**</span> 全概率定理是"**分而治之**"：要算 $P(B)$ 但直接算很难，就把样本空间按 $A_1, A_2, \ldots$ 切块（划分），在每块上分别算 $P(B \mid A_i)$（通常容易），再用 $P(A_i)$ 加权求和。证明只需可加性：$B = (B \cap A_1) \cup (B \cap A_2) \cup \cdots$（$B$ 被划分切碎，互斥），故 $P(B) = \sum P(B \cap A_i) = \sum P(A_i) P(B\mid A_i)$（乘法规则）。关键洞察：**"以条件为代价换取可分性"**——每个 $A_i$ 上的条件概率好算，就赚了。这与你在 CLRS 学的"分治"思想同构：把问题切成子问题，各子问题独立求解再合并。注意划分要求：$A_i$ 互斥且 $\cup A_i = \Omega$（不重不漏）——正如样本空间本身的要求。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Bayes' rule（贝叶斯规则）</span>

- **Prior probabilities（先验概率）$P(A_i)$**：初始的"信念"（initial beliefs）。
- 已知对每个 $i$ 有 $P(B \mid A_i)$。
- 希望在给定 $B$ 发生之后计算 $P(A_i \mid B)$——**修正"信念"**（revise "beliefs"）。

<span style="color:#2471a3;">**[theorem]**</span> **Bayes' rule（贝叶斯规则）**：
```math
P(A_i \mid B) = \frac{P(A_i \cap B)}{P(B)} = \frac{P(A_i) P(B \mid A_i)}{P(B)} = \frac{P(A_i) P(B \mid A_i)}{\sum_j P(A_j) P(B \mid A_j)} .
```

> <span style="color:#7f8c8d;">Bertsekas §1.4, p.31</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 战略定位）:**</span> 贝叶斯规则回答概率论最深刻的问题：**已知"原因"产生"结果"的概率（$P(B\mid A_i)$），如何反过来由"结果"推断"原因"（$P(A_i\mid B)$）**。它把"先验信念 $P(A_i)$"更新为"后验信念 $P(A_i\mid B)$"，分母 $\sum_j P(A_j)P(B\mid A_j) = P(B)$（全概率定理）起"归一化"作用。推导就三步：条件概率定义 $P(A_i\mid B)=\frac{P(A_i \cap B)}{P(B)}$、分子用乘法规则 $P(A_i)P(B\mid A_i)$、分母用全概率定理。雷达例子正是贝叶斯规则的实例：先验 $P(A)=0.05$，观测到 $B$（雷达显示）后后验 $P(A\mid B) \approx 0.34$——**信念被证据更新**。战略定位：这是本课程最重要的概念之一，Lec 21-22（贝叶斯统计推断）将把它从"事件"推广到"随机变量/分布"层面。跨课程连接：这是机器学习（朴素贝叶斯分类器）的核心公式——用观测特征 $B$ 更新对类别 $A_i$ 的信念；而"后验 = 先验 $\times$ 似然 / 证据"的结构，与你在 6.042J 学的条件概率规则完全一致。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
