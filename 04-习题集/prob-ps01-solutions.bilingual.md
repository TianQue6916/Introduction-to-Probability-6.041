<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 1 解答（Problem Set 1: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；Due: September 15, 2010，截止日期：2010 年 9 月 15 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 · 电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

<span style="color:#7f8c8d;">（原解答未重述题干：由答案与配图可知，本题要求用集合运算表示各 Venn 图中的阴影区域，下列 (a)–(g) 即为对应答案。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) $A \cup B \cup C$
>
> (b) $(A \cap B^c \cap C^c) \cup (A^c \cap B \cap C^c) \cup (A^c \cap B^c \cap C) \cup (A^c \cap B^c \cap C^c)$
>
> (c) $(A \cup B \cup C)^c = A^c \cap B^c \cap C^c$
>
> (d) $A \cap B \cap C$
>
> (e) $(A \cap B^c \cap C^c) \cup (A^c \cap B \cap C^c) \cup (A^c \cap B^c \cap C)$
>
> (f) $A \cap B \cap C^c$
>
> (g) $A \cup (A^c \cap B^c)$

<span style="color:#7f8c8d;">【图】原页此处为 7 幅 Venn 图，分别对应 (a)–(g) 各小问的阴影区域（全集为 $\Omega$，涉及集合 $A$、$B$、$C$）。原图由后处理统一插入。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

<span style="color:#7f8c8d;">（原解答未重述题干：由解答可知，本题考察将一枚硬币抛掷 3 次的古典概型，样本点为 H/T 序列。）</span>

> <span style="color:#2471a3;">[solution]</span> 由于所有结果都是等可能的，我们应用离散均匀概率律（discrete uniform probability law）来求解：对任一事件，只需数出该事件中元素的个数，再除以样本空间（sample space）中元素的总数。
>
> 每次抛掷有 2 种可能结果，共抛 3 次，因此样本空间中共有 $2^3 = 8$ 个元素（即序列）。
>
> (a) 每个序列的概率都是 $1/8$，因此 $P(\{H, H, H\}) = 1/8$。
>
> (b) 这仍是单个序列，故 $P(\{H, T, H\}) = 1/8$。
>
> (c) 所考察的事件包含 3 个不同的序列，故 $P(\{HHT, HTH, THH\}) = 3/8$。
>
> (d) 正面多于反面的序列构成 $A : \{HHH, HHT, HTH, THH\}$；由 4 个不同序列得 $P(A) = 1/2$。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答表格可知：两枚 4 面骰各掷一次，表中每一组合对应的概率值为其点数之和乘以常数 $p$。）</span>

<!-- ===== PDF p2 ===== -->

> **（续）**<span style="color:#2471a3;">[solution]</span> 求解本题最简单的方法，是列出类似下面的一个表格。
>
> | Die 1（骰 1） | Die 2（骰 2） | Sum（和） | P(Sum) |
> |:---:|:---:|:---:|:---:|
> | 1 | 1 | 2 | $2p$ |
> | 1 | 2 | 3 | $3p$ |
> | 1 | 3 | 4 | $4p$ |
> | 1 | 4 | 5 | $5p$ |
> | 2 | 1 | 3 | $3p$ |
> | 2 | 2 | 4 | $4p$ |
> | 2 | 3 | 5 | $5p$ |
> | 2 | 4 | 6 | $6p$ |
> | 3 | 1 | 4 | $4p$ |
> | 3 | 2 | 5 | $5p$ |
> | 3 | 3 | 6 | $6p$ |
> | 3 | 4 | 7 | $7p$ |
> | 4 | 1 | 5 | $5p$ |
> | 4 | 2 | 6 | $6p$ |
> | 4 | 3 | 7 | $7p$ |
> | 4 | 4 | 8 | $8p$ |
> | **Total（总计）** | | | $80p$ |
>
> 所有结果的概率 $P(\text{All outcomes}) = 80p$（即表中的 Total 项），因此
>
> ```math
> p = \frac{1}{80}
> ```
>
> (a) 掷出偶数和（Even sum）的概率：
>
> ```math
> P(\text{Even sum}) = 2p + 4p + 4p + 6p + 4p + 6p + 6p + 8p = 40p = 1/2
> ```
>
> (b) 掷出一个 2 和一个 3（Rolling a 2 and a 3）的概率：
>
> ```math
> P(\text{Rolling a 2 and a 3}) = P(2, 3) + P(3, 2) = 5p + 5p = 10p = 1/8
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答与图形可知：Alice 与 Bob 各在 $[0,2]$ 内取一个数，样本空间为 $[0,2]\times[0,2]$，总面积为 4；事件 $A$、$B$、$C$、$D$ 的定义见原习题。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **求 $P(B)$**：下图的阴影区域是「Alice 取的数大于 $1/3$」与「Bob 取的数大于 $1/3$」这两个事件的并（union）。
>
> <span style="color:#7f8c8d;">【图】原页此处为示意图：以 Alice 为横轴、Bob 为纵轴的 $[0,2]\times[0,2]$ 正方形，在 $1/3$、$1$、$2$ 处标有刻度，阴影为事件 $B$ 的区域。原图由后处理统一插入。</span>

<!-- ===== PDF p3 ===== -->

> **（续）** 由 1 减去「两个数都小于 $1/3$」（both numbers are smaller than 1/3）的概率，后者即小正方形面积（area of small square）与总样本面积（total sample area）之比：
>
> ```math
> P(B) = 1 - P(\text{both numbers are smaller than } 1/3) = 1 - \frac{\text{area of small square}}{\text{total sample area}} = 1 - \frac{(1/3)(1/3)}{4} = 1 - \frac{1}{36} = \frac{35}{36}
> ```
>
> **求 $P(C)$**：在下图中，对角线表示「两个所选数相等」的点集。
>
> <span style="color:#7f8c8d;">【图】原页此处为示意图：同一正方形，其中对角线表示两数相等（事件 $C$）。原图由后处理统一插入。</span>
>
> 该直线的面积为 0，因此「直线面积（area of line）除以总样本面积（total sample area）」得
>
> ```math
> P(C) = \frac{\text{area of line}}{\text{total sample area}} = \frac{0}{4} = 0
> ```
>
> **求 $P(A \cap D)$**：把 $P(A)$ 与 $P(D)$ 各自对应的图形叠在一起，
>
> <span style="color:#7f8c8d;">【图】原页此处为示意图：两事件区域重叠后的图形，双重阴影部分即 $A \cap D$。原图由后处理统一插入。</span>

<!-- ===== PDF p4 ===== -->

> **（续）** 双重阴影面积（double shaded area）与总样本面积（total sample area）之比为
>
> ```math
> P(A \cap D) = \frac{\text{double shaded area}}{\text{total sample area}} = \frac{(5/3)(5/3)(1/2) + (4/3)(4/3)(1/2)}{4} = \frac{25/18 + 16/18}{4} = \frac{41}{72}
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：Mike 掷飞镖于半径 10 英寸的圆盘，距原点 1 英寸以内得 50 分、1–3 英寸的环带得 30 分；(c) 小问考察另一名选手 John。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) Mike 得 50 分的概率与内圆盘（inner disk）的面积成正比，因此它等于 $\alpha\pi R^2 = \alpha\pi$，其中 $\alpha$ 为待定常数。由于飞镖落在盘上的概率等于 1，即 $\alpha\pi 10^2 = 1$，从而 $\alpha = 1/(100\pi)$。因此，Mike 得 50 分的概率为
>
> ```math
> \frac{\pi}{100\pi} = 0.01
> ```
>
> (b) 要想恰好得 30 分，Mike 需要把飞镖掷在距原点 1 到 3 英寸之间。一个简便的算法是先看「得分超过 30 分」的概率，它等于 $\alpha\pi 3^2 = 0.09$。接着，由于 30 分的环带与 50 分的圆盘互不相交（disjoint），「超过 30 分」的概率等于「得 50 分」的概率加上「恰好得 30 分」的概率。因此，Mike 恰好得 30 分的概率等于 $0.09 - 0.01 = 0.08$。
>
> (c) 对应 (a) 小问：John 得 50 分的概率，等于「掷在盘的右半边且得 50 分」的概率加上「掷在左半边且得 50 分」的概率。和式中的第一项与内圆盘右半部分的面积成正比，等于 $\alpha\pi R^2/2 = \alpha\pi/2$，其中 $\alpha$ 为待定常数；类似地，他掷在盘的左半边且得 50 分的概率等于 $\beta\pi/2$，其中 $\beta$ 是常数（不一定等于 $\alpha$）。为确定 $\alpha$ 与 $\beta$，我们先计算飞镖掷在盘右半边的概率，它等于
>
> ```math
> \alpha\pi R^2/2 = \alpha\pi 10^2/2 = 50\alpha\pi
> ```
>
> 由于该概率等于 $2/3$，故 $\alpha = 1/(75\pi)$；用同样的方法可确定 $\beta = 1/(150\pi)$。于是总概率为
>
> ```math
> \frac{1}{150} + \frac{1}{300} = 0.01
> ```
>
> 对应 (b) 小问：恰好得 30 分的概率，等于「超过 30 分」的概率减去「恰好 50 分」的概率。套用上面 (b) 中同类型的分析，可得该概率等于 $0.08$。
>
> 这些数字表明 John 与 Mike 的水平相当，两人赢得比赛的可能性相同。Mike 对投掷方向的控制更好（或者更差，取决于你怎么看），却并不能提高他获胜的概率；其原因在于：两名选手对「距原点距离」的控制是完全相同的。

<span style="color:#1e8449;">[note]</span> 原文 "or worst" 疑为 "or worse"（更差）之笔误。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 6**</span>

> <span style="color:#2471a3;">[solution]</span> 见教材（textbook）习题 1.11（Problem 1.11），第 55 页，该题证明了一般形式的 Bonferroni 不等式（Bonferroni's inequality）。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**G1†**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；本题考察区间序列 $A_n = [a_n, b_n]$ 与概率连续性（continuity property）的关系。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 若对每个 $n$ 都定义 $A_n = [a_n, b_n]$，则容易看出序列 $A_1, A_2, \ldots$ 是「单调递减的（monotonically decreasing）」，即对所有 $n$ 都有 $A_{n+1} \subset A_n$：

<!-- ===== PDF p5 ===== -->

> **（续）**
>
> <span style="color:#7f8c8d;">【图】原页此处为示意图：$\Omega$ 内一列嵌套的区间 $A_1 \supset A_2 \supset A_3 \supset \cdots \supset A_n$。原图由后处理统一插入。</span>
>
> 此外，$\bigcap_{n=1}^{\infty} A_n = [a, b]$。由概率的连续性（continuity property of probabilities）（见教材习题 1.13，第 56 页），
>
> ```math
> \lim_{n\to\infty} P([a_n, b_n]) = P([a, b])
> ```
>
> (b) 不成立（No）。考虑如下例子：令 $a_n = a + \dfrac{1}{n}$，$b_n = b - \dfrac{1}{n}$。则 $\{a_n\}$ 是收敛到 $a$ 的递减数列，$\{b_n\}$ 是收敛到 $b$ 的递增数列。如果定义一个只在点 $a$ 与 $b$ 上具有非零概率的概率律（probability law），那么 $\lim_{n\to\infty} P([a_n, b_n]) = 0$，但 $P([a, b]) = 1$。
>
> 这个例子与概率的连续性密切相关。此时若定义 $A_n = [a_n, b_n]$，则序列 $A_1, A_2, \ldots$ 是「单调递增的（monotonically increasing）」，即 $A_n \subset A_{n+1}$，但 $A = \Bigl(\bigcup_{n=1}^{\infty} A_n\Bigr) = (a, b)$ 是一个开区间，在上述概率律下其概率为 0。

<!-- ===== PDF p6 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 尾页：6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010，http://ocw.mit.edu/terms —— 无实质题目内容。）</span>
