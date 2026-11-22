<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 1 复习幻灯（Quiz I Review）**</span> <span style="color:#7f8c8d;">（Massachusetts Institute of Technology（麻省理工学院），2010 年 10 月 7 日；Fall 2010，2010 秋季学期）</span>

- Quiz I Review（测验 I 复习）
- Probabilistic Systems Analysis（概率系统分析）
- 6.041 / 6.431
- Massachusetts Institute of Technology（麻省理工学院）
- October 7, 2010（2010 年 10 月 7 日）

<span style="color:#7f8c8d;">【说明】原幻灯页脚编号为 N / 26（共 26 页正文，另含 1 页 MIT OCW 封底）；以下页标记 PDF p1–p27 与之一一对应。</span>

---

<!-- ===== PDF p2 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**考试信息（Quiz Information）**</span>

- 闭卷考试（closed-book），但允许携带一张双面的 8.5 × 11 英寸公式纸（formula sheet）。
- 考试内容：教材第 1–2 章（Chapters 1–2），Lecture 1–7（讲授课 1–7），Recitation 1–7（复习课 1–7），Problem Sets 1–4（习题集 1–4），Tutorials 1–3（辅导课 1–3）。
- 只要可能，请展示你的推理过程（Show your reasoning when possible）！

---

<!-- ===== PDF p3 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**一个概率模型（A Probabilistic Model）**</span>

- **Sample space（样本空间）**：一次 experiment（实验）的所有可能 outcome（结果）组成的集合。
- **Probability law（概率律）**：给每个 event（事件）$E$ 指派一个非负数 $P(E)$。

<span style="color:#7f8c8d;">【图】原页此处为示意图：实验（Experiment）→ 样本空间（Sample Space，其中含事件 A 与事件 B 两个子区域）→ 概率律（Probability Law）把事件分别映射为 P(A)、P(B)。原图由后处理统一插入。</span>

---

<!-- ===== PDF p4 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**概率公理（Probability Axioms）**</span>

给定样本空间 $\Omega$：

1. **Nonnegativity（非负性）**：对每个事件 $A$，$P(A) \geq 0$。
2. **Additivity（可加性）**：若 $A$ 与 $B$ 是互斥（disjoint）事件，则 $P(A \cup B) = P(A) + P(B)$。若 $A_1, A_2, \ldots$ 是一列互斥事件，则 $P(A_1 \cup A_2 \cup \cdots) = P(A_1) + P(A_2) + \cdots$。
3. **Normalization（归一性）**：$P(\Omega) = 1$。

---

<!-- ===== PDF p5 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**概率律的性质（Properties of Probability Laws）**</span>

给定事件 $A$、$B$ 与 $C$：

1. 若 $A \subset B$，则 $P(A) \leq P(B)$。
2. $P(A \cup B) = P(A) + P(B) - P(A \cap B)$。
3. $P(A \cup B) \leq P(A) + P(B)$。
4. $P(A \cup B \cup C) = P(A) + P(A^c \cap B) + P(A^c \cap B^c \cap C)$。

---

<!-- ===== PDF p6 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**离散模型（Discrete Models）**</span>

- **Discrete probability law（离散概率律）**：若 $\Omega$ 是有限的（finite），则每个事件 $A \subseteq \Omega$ 都可以表示为

```math
A = \{s_1, s_2, \ldots, s_n\}, \qquad s_i \in \Omega
```

  因此事件 $A$ 的概率为

```math
P(A) = P(s_1) + P(s_2) + \cdots + P(s_n)
```

- **Discrete uniform probability law（离散均匀概率律）**：若所有 outcome（结果）等可能（equally likely），则

```math
P(A) = \frac{|A|}{|\Omega|}
```

---

<!-- ===== PDF p7 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**条件概率（Conditional Probability）**</span>

- 给定满足 $P(B) > 0$ 的事件 $B$，事件 $A \subseteq \Omega$ 的 conditional probability（条件概率）定义为

```math
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
```

- $P(A \mid B)$ 是 $\Omega$ 上的一个合法（valid）概率律，满足：
  1. $P(A \mid B) \geq 0$；
  2. $P(\Omega \mid B) = 1$；
  3. $P(A_1 \cup A_2 \cup \cdots \mid B) = P(A_1 \mid B) + P(A_2 \mid B) + \cdots$，其中 $\{A_i\}_i$ 是一族互斥事件。
- $P(A \mid B)$ 也可以看作是限制在"新宇宙"（restricted universe）$B$ 上的概率律。

---

<!-- ===== PDF p8 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**乘法法则（Multiplication Rule）**</span>

- 设 $A_1, \ldots, A_n$ 是一族事件，且 $P\left(\bigcap_{i=1}^{n-1} A_i\right) > 0$。则全部事件的 joint probability（联合概率）为

```math
P\left(\bigcap_{i=1}^{n} A_i\right) = P(A_1)\, P(A_2 \mid A_1)\, P(A_3 \mid A_1 \cap A_2) \cdots P\left(A_n \,\Big|\, \bigcap_{i=1}^{n-1} A_i\right)
```

<span style="color:#7f8c8d;">【图】原页此处为嵌套区域示意图：大区域 $A_1$ 内嵌套 $A_1 \cap A_2$，其内再嵌套 $A_1 \cap A_2 \cap A_3$，并依次标注 $P(A_1)$、$P(A_2 \mid A_1)$、$P(A_3 \mid A_1 \cap A_2)$。原图由后处理统一插入。</span>

---

<!-- ===== PDF p9 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**全概率定理（Total Probability Theorem）**</span>

设 $A_1, \ldots, A_n$ 是划分（partition）$\Omega$ 的互斥事件。若对每个 $i$ 都有 $P(A_i) > 0$，则对任意事件 $B$：

```math
P(B) = \sum_{i=1}^{n} P(B \cap A_i) = \sum_{i=1}^{n} P(B \mid A_i)\, P(A_i)
```

<span style="color:#7f8c8d;">【图】原页此处为维恩图：$A_1, A_2, A_3$ 构成对样本空间 $\Omega$ 的划分，事件 $B$ 横跨其中（含 $B^c$ 部分）；右图把 $B$ 分解为 $B \cap A_1$、$B \cap A_2$、$B \cap A_3$ 三块。原图由后处理统一插入。</span>

---

<!-- ===== PDF p10 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**贝叶斯法则（Bayes Rule）**</span>

给定 $\Omega$ 的一个有限划分 $A_1, \ldots, A_n$（满足 $P(A_i) > 0$），则对每个满足 $P(B) > 0$ 的事件 $B$：

```math
P(A_i \mid B) = \frac{P(B \mid A_i)\, P(A_i)}{P(B)} = \frac{P(B \mid A_i)\, P(A_i)}{\sum_{j=1}^{n} P(B \mid A_j)\, P(A_j)}
```

<span style="color:#7f8c8d;">【图】原页此处为维恩图：$A_1, A_2, A_3$ 构成对样本空间 $\Omega$ 的划分，事件 $B$ 横跨其中（含 $B^c$ 部分）；右图把 $B$ 分解为 $B \cap A_1$、$B \cap A_2$、$B \cap A_3$ 三块。原图由后处理统一插入。</span>

---

<!-- ===== PDF p11 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**事件的独立性（Independence of Events）**</span>

- 事件 $A$ 与 $B$ independent（独立），当且仅当

```math
P(A \cap B) = P(A)\, P(B)
```

  或者（当 $P(B) > 0$ 时）$P(A \mid B) = P(A)$。
- 事件 $A$ 与 $B$ 在给定事件 $C$ 下 conditionally independent（条件独立），当且仅当

```math
P(A \cap B \mid C) = P(A \mid C)\, P(B \mid C)
```

  或者（当 $P(B \cap C) > 0$ 时）$P(A \mid B \cap C) = P(A \mid C)$。
- Independence（独立）$\not\Rightarrow$ Conditional Independence（条件独立）。

<span style="color:#1e8449;">**[note]** 末条原文提取为 "Independence < Conditional Independence"，其中 "<" 是原 PDF 中否定蕴含符号 $\not\Rightarrow$ 的提取伪影；其含义是"独立不能推出条件独立"。结合教材（Lecture 5）可知反向同样不成立：条件独立也不蕴含独立。</span>

---

<!-- ===== PDF p12 ===== -->

<span style="color:#7f8c8d;">【图】原页顶部此处有一处插图（提取文本层仅残留 "6"、"!"、"\"、"Y" 等无法辨识的图形噪声，内容不可恢复）。原图由后处理统一插入。</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**一组事件的独立性（Independence of a Set of Events）**</span>

- 事件 $A_1, \ldots, A_n$ 是 pairwise independent（两两独立）的，若对每个 $i \neq j$ 都有

```math
P(A_i \cap A_j) = P(A_i)\, P(A_j)
```

- 事件 $A_1, \ldots, A_n$ 是 independent（相互独立）的，若对每个 $S \subseteq \{1, 2, \ldots, n\}$ 都有

```math
P\left(\bigcap_{i \in S} A_i\right) = \prod_{i \in S} P(A_i)
```

- 两两独立 $\not\Rightarrow$ 相互独立，但相互独立 $\Rightarrow$ 两两独立。

---

<!-- ===== PDF p13 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**计数方法（Counting Techniques）**</span>

- **Basic counting principle（基本计数原理）**：对一个 $m$ 阶段（$m$-stage）过程，若第 $i$ 阶段有 $n_i$ 种选择，则

```math
\#\text{ Choices} = n_1 n_2 \cdots n_m
```

- **Permutations（排列）**：从 $n$ 个不同元素中不放回地抽取长度为 $k$ 的序列（sequence，顺序重要）：

```math
\#\text{ Sequences} = n(n-1) \cdots (n-k+1) = \frac{n!}{(n-k)!}
```

- **Combinations（组合）**：从 $n$ 个不同元素中取出 $k$ 个元素组成的集合（set，集合内部顺序不重要）：

```math
\#\text{ Sets} = \binom{n}{k} = \frac{n!}{k!\,(n-k)!}
```

---

<!-- ===== PDF p14 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**计数方法（续）（Counting Techniques — cont'd）**</span>

- **Partitions（分割）**：把一个 $n$ 元素集合分割成 $r$ 个互不相交的子集、且第 $k$ 个子集含 $n_k$ 个元素的方式数为

```math
\binom{n}{n_1, n_2, \ldots, n_r} = \binom{n}{n_1}\binom{n - n_1}{n_2}\cdots\binom{n - n_1 - \cdots - n_{r-1}}{n_r} = \frac{n!}{n_1!\, n_2! \cdots n_r!}
```

  其中

```math
\binom{n}{k} = \frac{n!}{k!\,(n-k)!}, \qquad \sum_{i=1}^{r} n_i = n
```

---

<!-- ===== PDF p15 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**离散随机变量（Discrete Random Variables）**</span>

- random variable（随机变量）是定义在 sample space（样本空间）上的实值函数：

```math
X : \Omega \to \mathbb{R}
```

- 记号 $\{X = x\}$ 表示一个 event（事件）：

```math
\{X = x\} = \{\omega \in \Omega \mid X(\omega) = x\} \subseteq \Omega
```

- 随机变量 $X$ 的 probability mass function（PMF，概率质量函数）给每个事件 $\{X = x\}$ 指派一个概率：

```math
p_X(x) = P(\{X = x\}) = P\left(\{\omega \in \Omega \mid X(\omega) = x\}\right)
```

---

<!-- ===== PDF p16 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**PMF 的性质（PMF Properties）**</span>

- 设 $X$ 是一个随机变量，$S$ 是实直线（real line）的一个可数（countable）子集。
- 概率公理成立：
  1. $p_X(x) \geq 0$；
  2. $P(X \in S) = \sum_{x \in S} p_X(x)$；
  3. $\sum_{x} p_X(x) = 1$。
- 若 $g$ 是一个实值函数，则 $Y = g(X)$ 也是一个随机变量：$\omega \xrightarrow{\;X\;} X(\omega) \xrightarrow{\;g\;} g(X(\omega)) = Y(\omega)$，其 PMF 为

```math
p_Y(y) = \sum_{\{x \mid g(x) = y\}} p_X(x)
```

<span style="color:#7f8c8d;">【图】原页此处以一个小流程示意图呈现该映射：$\omega$ 经 $X$ 映射到 $X(\omega)$，再经 $g$ 映射到 $g(X(\omega)) = Y(\omega)$；上式已将其还原为公式。原图由后处理统一插入。</span>

---

<!-- ===== PDF p17 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**期望（Expectation）**</span>

给定 PMF 为 $p_X(x)$ 的随机变量 $X$：

```math
E[X] = \sum_{x} x\, p_X(x)
```

- 对派生随机变量（derived random variable）$Y = g(X)$：

```math
E[g(X)] = \sum_{x} g(x)\, p_X(x) = \sum_{y} y\, p_Y(y) = E[Y]
```

- $n$ 阶矩：$E[X^n] = \sum_{x} x^n\, p_X(x)$。
- **Linearity of expectation（期望的线性性）**：$E[aX + b] = a\, E[X] + b$。

---

<!-- ===== PDF p18 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**方差（Variance）**</span>

派生随机变量 $g(X)$ 的期望为

```math
E[g(X)] = \sum_{x} g(x)\, p_X(x)
```

$X$ 的 variance（方差）计算为

```math
\mathrm{var}(X) = E\left[(X - E[X])^2\right] = \sum_{x} (x - E[X])^2\, p_X(x)
```

- $\mathrm{var}(X) = E[X^2] - (E[X])^2$。
- $\mathrm{var}(aX + b) = a^2\, \mathrm{var}(X)$。
- 注意 $\mathrm{var}(X) \geq 0$。

<span style="color:#1e8449;">**[note]** 原页末行写作 "$\mathrm{var}(x) \ge 0$"，按上下文应为随机变量 $X$ 的方差非负，即 $\mathrm{var}(X) \geq 0$。</span>

---

<!-- ===== PDF p19 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**多个随机变量（Multiple Random Variables）**</span>

设 $X$ 与 $Y$ 是定义在同一 sample space（样本空间）$\Omega$ 上的随机变量。

- $X$ 与 $Y$ 的 joint PMF（联合概率质量函数）记为

```math
p_{X,Y}(x, y) = P\left(\{X = x\} \cap \{Y = y\}\right)
```

- $X$ 与 $Y$ 的 marginal PMFs（边缘概率质量函数）分别为

```math
p_X(x) = \sum_{y} p_{X,Y}(x, y), \qquad p_Y(y) = \sum_{x} p_{X,Y}(x, y)
```

---

<!-- ===== PDF p20 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**多个随机变量的函数（Functions of Multiple Random Variables）**</span>

设 $Z = g(X, Y)$ 是两个随机变量的函数。

- PMF：

```math
p_Z(z) = \sum_{\{(x,y) \mid g(x,y) = z\}} p_{X,Y}(x, y)
```

- Expectation（期望）：

```math
E[Z] = \sum_{x,y} g(x, y)\, p_{X,Y}(x, y)
```

- Linearity（线性性）：设 $g(X, Y) = aX + bY + c$，则

```math
E[g(X, Y)] = a\, E[X] + b\, E[Y] + c
```

---

<!-- ===== PDF p21 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**条件化的随机变量（Conditioned Random Variables）**</span>

- 把 $X$ 条件化（conditioning）于满足 $P(A) > 0$ 的事件 $A$，得到条件 PMF：

```math
p_{X \mid A}(x) = P\left(\{X = x\} \mid A\right) = \frac{P\left(\{X = x\} \cap A\right)}{P(A)}
```

- 把 $X$ 条件化于事件 $\{Y = y\}$（满足 $p_Y(y) > 0$），得到条件 PMF：

```math
p_{X \mid Y}(x \mid y) = \frac{P\left(\{X = x\} \cap \{Y = y\}\right)}{P(\{Y = y\})} = \frac{p_{X,Y}(x, y)}{p_Y(y)}
```

---

<!-- ===== PDF p22 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**条件化的随机变量（续）（Conditioned RV — cont'd）**</span>

- **Multiplication rule（乘法法则）**：

```math
p_{X,Y}(x, y) = p_{X \mid Y}(x \mid y)\, p_Y(y)
```

- **Total probability theorem（全概率定理）**：

```math
p_X(x) = \sum_{i=1}^{n} P(A_i)\, p_{X \mid A_i}(x), \qquad p_X(x) = \sum_{y} p_{X \mid Y}(x \mid y)\, p_Y(y)
```

---

<!-- ===== PDF p23 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**条件期望（Conditional Expectation）**</span>

设 $X$ 与 $Y$ 是样本空间 $\Omega$ 上的随机变量。

- 给定满足 $P(A) > 0$ 的事件 $A$：

```math
E[X \mid A] = \sum_{x} x\, p_{X \mid A}(x)
```

- 若 $p_Y(y) > 0$，则

```math
E[X \mid \{Y = y\}] = \sum_{x} x\, p_{X \mid Y}(x \mid y)
```

- **Total expectation theorem（全期望定理）**：设 $A_1, \ldots, A_n$ 是 $\Omega$ 的一个划分（partition）。若对每个 $i$ 都有 $P(A_i) > 0$，则

```math
E[X] = \sum_{i=1}^{n} P(A_i)\, E[X \mid A_i]
```

---

<!-- ===== PDF p24 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**独立性（Independence）**</span>

设 $X$ 与 $Y$ 是定义在 $\Omega$ 上的随机变量，$A$ 是满足 $P(A) > 0$ 的事件。

- $X$ 与事件 $A$ independent（独立），若下列条件之一成立：
  - $p_{X \mid A}(x) = p_X(x)$，对所有 $x$；
  - $p_{X,A}(x) = p_X(x)\, P(A)$，对所有 $x$（其中 $p_{X,A}(x) = P(\{X = x\} \cap A)$，即事件 $\{X = x\}$ 与 $A$ 的联合概率）。
- $X$ 与 $Y$ independent（独立），若下列条件之一成立：
  - $p_{X \mid Y}(x \mid y) = p_X(x)$，对所有 $x, y$；
  - $p_{X,Y}(x, y) = p_X(x)\, p_Y(y)$，对所有 $x, y$。

---

<!-- ===== PDF p25 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**独立性（Independence）**</span>

若 $X$ 与 $Y$ independent（独立），则下列结论成立：

- 若 $g$ 与 $h$ 是实值函数，则 $g(X)$ 与 $h(Y)$ 也相互独立。
- $E[XY] = E[X]\, E[Y]$（其逆命题不成立，inverse is not true）。
- $\mathrm{var}(X + Y) = \mathrm{var}(X) + \mathrm{var}(Y)$。

给定相互独立的随机变量 $X_1, \ldots, X_n$：

```math
\mathrm{var}(X_1 + X_2 + \cdots + X_n) = \mathrm{var}(X_1) + \mathrm{var}(X_2) + \cdots + \mathrm{var}(X_n)
```

---

<!-- ===== PDF p26 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**若干离散分布（Some Discrete Distributions）**</span>

| 分布（Distribution） | 直观含义 | $p_X(k)$ | $E[X]$ | $\mathrm{var}(X)$ |
|---|---|---|---|---|
| **Bernoulli（伯努利）** | $1$ 表示成功（success），$0$ 表示失败（failure） | $p$（当 $k = 1$）；$1 - p$（当 $k = 0$） | $p$ | $p(1 - p)$ |
| **Binomial（二项）** | $n$ 重 Bernoulli（伯努利）试验中成功的次数 | $\dbinom{n}{k} p^k (1 - p)^{n-k}$，$k = 0, 1, \ldots, n$ | $np$ | $np(1 - p)$ |
| **Geometric（几何）** | 直到首次成功（first success）所需的试验次数 | $(1 - p)^{k-1} p$，$k = 1, 2, \ldots$ | $1/p$ | $\dfrac{1 - p}{p^2}$ |
| **Uniform（均匀）** | 区间 $[a, b]$ 内的一个整数 | $\dfrac{1}{b - a + 1}$（当 $k = a, \ldots, b$）；$0$（其他情况） | $\dfrac{a + b}{2}$ | $\dfrac{(b - a)(b - a + 2)}{12}$ |

---

<!-- ===== PDF p27 ===== -->

<span style="color:#7f8c8d;">**MIT OpenCourseWare（MIT 开放课件）**：http://ocw.mit.edu —— 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms 。</span>
