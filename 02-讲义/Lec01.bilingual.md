# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 1 — Probability Models and Axioms（概率模型与公理）</span>

<span style="color:#7f8c8d;">Instructor: John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008（本课教材，可在 MIT OCW 查阅）</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Course information（课程信息）</span>

- **Staff（教师）**：Lecturer（主讲）John Tsitsiklis。
- 领取并阅读课程信息手册（course information handout）。
- 上交习题课与辅导课时间安排表（课程信息手册最后一页）。
- 领取幻灯片讲义。

**Coursework（评分）**：
- Quiz 1（10 月 12 日，12:05–12:55pm）17%
- Quiz 2（11 月 2 日，7:30–9:30pm）30%
- Final exam（期末考试，由教务安排）40%
- Weekly homework（每周作业，10 次中取分数最高的 9 次计入成绩）10%
- Attendance/participation/enthusiasm in recitations/tutorials（习题课/辅导课的出勤、参与与热情）3%

- 合作政策（collaboration policy）在课程信息手册中说明。
- **教材**：*Introduction to Probability*（《概率导论》），第 2 版，D. P. Bertsekas 与 J. N. Tsitsiklis，Athena Scientific, 2008。**要读书！**

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这门课（6.041/6.431）是 MIT 的"概率系统分析"，与你大二上的概率论计划（Bertsekas《概率导论》）完全对应。评分权重透露重点：Quiz 1 + Quiz 2 + Final 合计 87%，说明**概念理解与计算能力是主线**，作业只有 10%（且取最好 9 次）。这门课与你在 100B 实分析学到的"严谨语言"互为补充：概率论用集合论与测度论的直觉（样本空间、事件 = 子集），但更强调"建模"（把现实问题翻译成概率模型）与"计算"（算概率）。Tsitsiklis 在第一页就明确"Read the text!"——教材是 Bertsekas，你手头应该已有。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline（本讲大纲）</span>

**阅读**：教材 Sections 1.1、1.2。

**Lecture outline（本讲大纲）**：
- Probability as a mathematical framework for reasoning about uncertainty（概率作为对不确定性进行推理的数学框架）。
- Probabilistic models（概率模型）——sample space（样本空间）、probability law（概率律）。
- Axioms of probability（概率公理）。
- Simple examples（简单例子）。

> <span style="color:#7f8c8d;">Bertsekas §1.1–1.2</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 本讲的"设计问题"是：**如何给"不确定性"一个严格的数学框架？** 概率论的回答是两步走——先定**样本空间**（所有可能结果的集合），再定**概率律**（给每个事件分配一个数）。这与你熟悉的分析学类似：先定义对象（集合/函数），再定义"度量/极限"等结构。Tsitsiklis 强调概率是"对不确定性推理的**数学框架**"——它不回答"世界是否确定"，而是提供一套从"已知概率"推出"未知概率"的规则。第一性原理：**概率论的三条公理（非负、归一、可加）是整个学科的"地基"，本讲就是把它们讲清楚并演示如何用它们计算**。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Sample space（样本空间）</span>

- **Sample space（样本空间）$\Omega$**：可能结果的"清单"（集合）。
- 清单必须满足：
  - **Mutually exclusive（互斥）**：任意两个结果不能同时发生。
  - **Collectively exhaustive（穷尽）**：所有可能结果都被列出。
- 艺术在于：**粒度要"正确"**（Art: to be at the "right" granularity）。

> <span style="color:#7f8c8d;">Bertsekas §1.2, p.6–7</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 跨课程连接）:**</span> 样本空间是"结果的集合"，两条要求"互斥 + 穷尽"本质上是说"样本空间是一个**划分**（partition）"——每个可能的实验结局恰好落在其中一个结果里，不重不漏。卡点诊断："**正确的粒度**"是建模的艺术：同一个实验可以有不同的样本空间。抛两枚硬币，可以取 $\Omega = \{HH, HT, TH, TT\}$（4 个有序结果），也可以取"正面个数" $\Omega = \{0,1,2\}$（3 个结果，但损失了"哪枚硬币"的信息）；选哪个取决于你关心什么。这与你 6.042J 学的集合划分、以及 100B 的"事件 = 样本空间的子集"一脉相承——**概率论的第一步永远是"选好样本空间"**，选错粒度会导致后续计算无意义或信息丢失。约定：概率论中 $P$ 作用在 event（事件，$\Omega$ 的子集）上，正如你在 100B 把"可测集"作为概率的载体。

**Sample space: Discrete example（样本空间：离散例子）**：
- 抛两次 tetrahedral die（四面骰）。
- 样本空间 vs 序列描述（Sample space vs. sequential description）。

> <span style="color:#7f8c8d;">图：四面骰抛两次的样本空间格点图——横轴为第一次结果 $X$（1 到 4），纵轴为第二次结果 $Y$（1 到 4），16 个格点构成 $\Omega = \{(x,y) \mid x, y \in \{1,2,3,4\}\}$。旁边以"序列树"表示同一样本空间的另一种（序列）描述。</span>

**Sample space: Continuous example（样本空间：连续例子）**：
```math
\Omega = \{(x, y) \mid 0 \le x, y \le 1\}.
```

> <span style="color:#7f8c8d;">图：单位正方形 $\Omega = [0,1] \times [0,1]$（阴影区域）——连续样本空间的示意图，用于"两个随机数在 $[0,1]$ 内"的实验。</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 离散例子（四面骰两次，16 个点）与连续例子（$[0,1]^2$，不可数无穷）并排，预告本课程的两大分支：**离散概率**（样本空间可数，用"计数"算概率）与**连续概率**（样本空间连续，用"面积/密度"算概率）。注意连续例子的样本空间 $\Omega = \{(x,y): 0\le x,y \le 1\}$ 是单位正方形——"两个随机数"实验的天然模型。你在 100B 学的"面积可测性"直觉在这里直接有用：连续概率 = 面积。这为后续（Lec 08 连续随机变量）埋下伏笔。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Probability axioms（概率公理）</span>

- **Event（事件）**：样本空间的一个子集。
- 概率被分配给事件。

**Axioms（公理）**：
1. **Nonnegativity（非负性）**：$P(A) \ge 0$。
2. **Normalization（归一化）**：$P(\Omega) = 1$。
3. **Additivity（可加性）**：若 $A \cap B = \emptyset$，则 $P(A \cup B) = P(A) + P(B)$。

- $P(\{s_1, s_2, \ldots, s_k\}) = P(\{s_1\}) + \cdots + P(\{s_k\}) = P(s_1) + \cdots + P(s_k)$。
- **公理 3 需要强化**（Axiom 3 needs strengthening）。
- 怪异的集合有概率吗？（Do weird sets have probabilities?）

> <span style="color:#7f8c8d;">Bertsekas §1.2, p.9</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 战略预告）:**</span> 三条公理用最少的假设捕捉"概率"的本质：**非负**（概率不小于 0）、**归一**（必然事件概率 1）、**可加**（互斥事件并的概率 = 概率之和）。它们为什么长这样？因为概率的直觉是"频率"：在大量重复实验中，$P(A)$ 是"$A$ 发生的比例"，比例自然非负、总数归一、互斥事件的比例相加。卡点诊断："公理 3 需要强化"指的是：对**有限个**互斥事件，公理 3 直接推广；但对**可数无限个**互斥事件（如 $A_1, A_2, \ldots$），需要更强的"**可数可加性**"（本讲末尾会用到，算 $P(\text{偶数}) = 1/3$ 时就靠它）。"怪异的集合有概率吗"预告了**可测性**问题（与 100B 的测度论同源）——在连续样本空间，不是所有子集都有良定义的概率，这引出 Lebesgue 可测性（后续深入）。

**Probability law: Example with finite sample space（概率律：有限样本空间的例子）**：
- 设每个可能结果都有概率 $\frac{1}{16}$。
- $P\left((X, Y) \text{ 是 } (1,1) \text{ 或 } (1,2)\right) = \frac{2}{16}$。
- $P(\{X = 1\}) = \frac{4}{16} = \frac{1}{4}$。
- $P(X + Y \text{ 是奇数}) = \frac{8}{16} = \frac{1}{2}$。
- $P(\min(X, Y) = 2) = ?$

> <span style="color:#7f8c8d;">图：16 个格点（$X$ 横轴、$Y$ 纵轴）上标出各事件对应的格点，演示用"数格点"算概率。</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 验算（四面骰两次，共 16 个等可能结果）：$P((1,1)\text{ 或 }(1,2)) = \frac{2}{16} = \frac{1}{8}$ ✓（两个格点）；$P(X=1) = \frac{4}{16} = \frac{1}{4}$ ✓（第一列为 1 的 4 个点）；$P(X+Y \text{ 奇}) = \frac{8}{16} = \frac{1}{2}$ ✓（$X,Y$ 奇偶性不同，8 个点）；$P(\min(X,Y)=2)$：留作思考——$\min = 2$ 意味着两个骰子都 $\ge 2$ 且至少一个等于 2，即格点 $(2,2),(2,3),(2,4),(3,2),(4,2)$ 共 5 个，概率 $\frac{5}{16}$。这个例子演示了"**等可能模型 + 数格点**"的离散均匀律（下一节），而"$X+Y$ 奇偶"这类事件需要你**会数**，而非套公式。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Discrete uniform law（离散均匀律）</span>

- 设所有结果 equally likely（等可能）。
- 则
```math
P(A) = \frac{\text{number of elements of } A}{\text{total number of sample points}} .
```
- **计算概率 $\equiv$ 计数**（Computing probabilities ≡ counting）。
- 定义了公平硬币、公平骰子、洗好的牌（fair coins, fair dice, well-shuffled decks）。

> <span style="color:#7f8c8d;">Bertsekas §1.2, p.11</span>

> <span style="color:#1e8449;">**[note] Note（译者注，跨课程连接）:**</span> 离散均匀律是最简单的概率模型：所有结果等可能，概率 = "有利结果数 / 总结果数"。它的威力在于把"概率计算"化为"**计数**"——这正是你在 6.042J 学的组合数学（排列、组合、二项式系数）派上用场的地方：Lec 04（Counting）会系统化"数格点"的技巧。卡点诊断：均匀律只在"等可能"假设下成立——如果骰子不均匀，$P(A)$ 就不再是"数格点"，而要看各结果的实际概率。所以"公平硬币/骰子/洗牌"是均匀律的模型化前提。跨课程连接：$\frac{|A|}{|\Omega|}$ 正是"有利事件占全空间的**比例**"，与你在 6.042J 学的"比例/占比"思维一致，也是后续"计数问题"（如生日问题、彩票）的基石。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Continuous uniform law（连续均匀律）</span>

- 两个"随机"数在 $[0, 1]$ 内。
- **Uniform law（均匀律）**：Probability = Area（概率 = 面积）。
  - $P(X + Y \le \frac{1}{2}) = ?$
  - $P((X, Y) = (0.5, 0.3)) = ?$

> <span style="color:#7f8c8d;">图：单位正方形中阴影区域 $x + y \le \frac{1}{2}$（左下三角形）——概率 = 该三角形的面积。</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 连续均匀律把"数格点"换成"**量面积**"：在 $[0,1]^2$ 上随机取一点，$P(\text{点落在区域 } A) = A$ 的面积（因为全空间面积 = 1，归一化）。关键对比：
> - $P(X+Y \le \frac{1}{2})$：落在左下三角形 $\{(x,y): x+y\le\frac12\}$，面积 $= \frac{1}{2}\cdot\frac{1}{2}\cdot\frac{1}{2} = \frac{1}{8}$（底 $\frac12$、高 $\frac12$ 的直角三角形）。
> - $P((X,Y) = (0.5, 0.3))$：单点面积 $= 0$！——**连续分布下，取到"恰好某点"的概率为 0**，但这不意味着"不可能发生"（事件非空）。
> 卡点诊断：这是连续概率最反直觉的一点——**"概率为 0"$\neq$"不可能"**。一个点在连续空间中概率为 0 却可能发生；这与你 100B 学的测度论直觉一致：单点 Lebesgue 测度为 0。这也是为什么连续分布用"密度/面积"而非"单点概率"描述（Lec 08 起）。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Probability law: Countably infinite sample space（概率律：可数无限样本空间）</span>

- 样本空间：$\{1, 2, \ldots\}$。
- 已知 $P(n) = 2^{-n}$，$n = 1, 2, \ldots$。
- 求 $P(\text{outcome is even})$（结果为偶数的概率）。

> <span style="color:#7f8c8d;">图：几何级数概率质量图——$n$ 轴上的概率 $P(n) = 2^{-n}$（$1/2, 1/4, 1/8, 1/16, \ldots$ 逐项减半的阶梯）。</span>

```math
P(\{2, 4, 6, \ldots\}) = P(2) + P(4) + \cdots = \frac{1}{2^2} + \frac{1}{2^4} + \frac{1}{2^6} + \cdots = \frac{1}{3} .
```

- **可数可加性公理**（Countable additivity axiom，此计算需要它）：若 $A_1, A_2, \ldots$ 是两两不相交的事件，则
```math
P(A_1 \cup A_2 \cup \cdots) = P(A_1) + P(A_2) + \cdots .
```

> <span style="color:#7f8c8d;">Bertsekas §1.2, p.9（公理 2 的可数推广）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 战略预告）:**</span> 验算：$P(\text{偶数}) = \sum_{n=1}^{\infty} 2^{-2n} = \sum_{n=1}^{\infty} \left(\frac{1}{4}\right)^n = \frac{1/4}{1-1/4} = \frac{1}{3}$ ✓（等比级数求和，你在 L08/100B 学过：首项 $\frac14$、公比 $\frac14$）。这个例子展示了**为什么需要"可数可加性"公理**：$P(2)+P(4)+P(6)+\cdots$ 是**可数无限项**的和，公理 3（有限可加）只能处理有限并；要算"所有偶数的概率"，必须把可数可加性作为公理接受——这正是公理 3 的"强化"。战略预告：可数可加性 + 非负 + 归一，构成**测度论意义下的概率公理**（Kolmogorov 公理，1933），它让你在 100B 的测度论（Lebesgue 测度）与概率论之间看到同一数学结构；而 $2^{-n}$ 这个几何分布是后续"无记忆性"（Lec 13 伯努利过程）的种子。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · https://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
