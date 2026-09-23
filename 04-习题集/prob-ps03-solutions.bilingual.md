<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 3 解答（Problem Set 3: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；Due September 29, 2010，截止日期：2010 年 9 月 29 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 · 电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

$n$ 个人的帽子被扔进一个箱子里。然后这些人随机地取回帽子（即帽子在人们之间的每一种分配（assignment）都是等可能的）。求下列事件的概率：

(a) 每个人都取回自己的帽子？

(b) 最先取帽子的 $m$ 个人取回的都是自己的帽子？

(c) 最先取帽子的 $m$ 个人中的每一个人，取回的帽子都属于最后取帽子的 $m$ 个人之一？

> <span style="color:#2471a3;">[solution]</span>
>
> (a) **答案（Answer）**：$\dfrac{1}{n!}$。
>
> **解答（Solution）**：考虑所有可能的帽子分配构成的样本空间（sample space）。它有 $n!$ 个元素（第一个人有 $n$ 种选帽方式，之后第二个人有 $n-1$ 种，依此类推），且每个单元素事件都等可能（因此概率为 $1/n!$）。题目要计算的是一个单元素事件的概率，故答案为 $1/n!$。
>
> (b) **答案**：$\dfrac{(n-m)!}{n!}$。
>
> **解答**：考虑与 (a) 解答中相同的样本空间和概率。具有 $(n-m)!$ 个元素的事件（即前 $m$ 顶帽子分配给其主人之后，余下 $n-m$ 顶帽子的分配方式数）的概率为 $(n-m)!/n!$。
>
> (c) **答案**：$\dfrac{m!(n-m)!}{n!} = \dfrac{1}{\binom{n}{m}} = \dfrac{1}{\binom{n}{n-m}}$。
>
> **解答**：把这 $m$ 顶帽子分给最先取帽子的 $m$ 个人共有 $m!$ 种方式，把其余 $n-m$ 顶帽子分掉共有 $(n-m)!$ 种方式。具有 $m!(n-m)!$ 个元素的事件的概率为 $m!(n-m)!/n!$。

现在再假设：此外，每顶被扔进箱子的帽子都有概率 $p$ 变脏（与其他帽子的遭遇、以及是谁扔下或捡起它均无关）。求下列事件的概率：

(d) 最先取帽子的 $m$ 个人都取到干净帽子？

(e) 恰好 $m$ 个人取到干净帽子？

> <span style="color:#2471a3;">[solution]</span>
>
> (d) **答案**：$(1-p)^m$。
>
> **解答**：给定的人取到干净帽子的概率是 $1-p$。由独立性假设（independence），被选中的 $m$ 个人都取到干净帽子的概率为 $(1-p)^m$。
>
> (e) **答案**：$(1-p)^m p^{\,n-m} \dbinom{n}{m}$。
>
> **解答**：任取一个由 $m$ 个人组成的组 $G$，它定义了事件「$G$ 中的每个人都取到干净帽子，不在 $G$ 中的每个人都取到脏帽子」。这些事件互不相交（disjoint），每个的概率为 $(1-p)^m p^{\,n-m}$。这样的事件共有 $\binom{n}{m}$ 个，故得答案。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：Alice 已确定 4 张牌，Bob 从 52 张牌中选 8 张，求 Bob 的 8 张牌包含 Alice 这 4 张牌的概率。）</span>

> <span style="color:#2471a3;">[solution]</span> 由于 4 张牌是固定的，Bob 只能从余下的 48 张牌中再选 4 张，因此「Bob 的手牌包含 Alice 这些牌」的总方式数为 $\dbinom{4}{4}\dbinom{48}{4}$。Bob 任选 8 张牌的总方式数为 $\dbinom{52}{8}$。所以概率为
>
> ```math
> \frac{\binom{4}{4}\binom{48}{4}}{\binom{52}{8}}
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；(a) 即证明：对非负整值随机变量 $X$，有 $E[X] = \sum_{k=1}^{\infty} P(X \ge k)$；(b) 对取值于 $\{a, a+1, \ldots, b\}$ 的均匀随机变量 $Y$，利用 (a) 的结论求 $E[Y]$。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 下图给出了证明本题陈述所需的双重求和（double sum）的示意：

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> <span style="color:#7f8c8d;">【图】原页此处为双重求和示意图：平面格点上以「X」标出求和区域，横轴为 $i$（延伸至 infinity），纵轴为 $k$（$k=1$ 至 $i=k$），即区域 $\{(i,k):\ 1 \le k \le i\}$。原图由后处理统一插入。</span>
>
> 我们首先注意到
>
> ```math
> P(X \ge k) = \sum_{i=k}^{\infty} p_X(i)
> ```
>
> 然后如下进行：
>
> ```math
> \sum_{k=1}^{\infty} P(X \ge k) = \sum_{k=1}^{\infty} \sum_{i=k}^{\infty} p_X(i) = \sum_{i=1}^{\infty} \sum_{k=1}^{i} p_X(i) = \sum_{i=1}^{\infty} i\, p_X(i) = E[X]
> ```
>
> (b) 我们先计算
>
> ```math
> P(Y \ge k) = \begin{cases} 1, & k \le a \\[4pt] \dfrac{b-k+1}{b-a+1}, & a+1 \le k \le b \\[6pt] 0, & k \ge b+1 \end{cases}
> ```
>
> 于是
>
> ```math
> \sum_{k=1}^{\infty} P(Y \ge k) = \sum_{k=1}^{a} 1 + \sum_{k=a+1}^{b} \frac{b-k+1}{b-a+1} = a + \frac{1}{b-a+1}\sum_{k=1}^{b-a} k = a + \frac{(b-a+1)(b-a)}{2(b-a+1)} = a + \frac{b-a}{2} = \frac{b+a}{2}
> ```
>
> 因此 $E[Y] = \dfrac{a+b}{2}$。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由 PMF 形状可知：$X$ 为两次等可能试验（各 3 种结果，如两枚 3 点骰子）取值之差，取值 $\{-2,-1,0,1,2\}$；(a) 求 $E[X]$ 与 $\mathrm{var}(X)$，(b) 令 $Z = X^2$，求 $Z$ 的 PMF。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 对 $X$ 的每个取值，我们数出差等于该值的结果个数：
>
> ```math
> p_X(x) = \begin{cases} 1/9, & x = -2,\ 2 \\ 2/9, & x = -1,\ 1 \\ 3/9, & x = 0 \\ 0, & \text{otherwise} \end{cases}
> ```

<!-- ===== PDF p3 ===== -->

> **（续）**
>
> ```math
> E[X] = \sum_{x=-2}^{2} x\, p_X(x) = -2\cdot\frac{1}{9} + (-1)\cdot\frac{2}{9} + 0\cdot\frac{3}{9} + 1\cdot\frac{2}{9} + 2\cdot\frac{1}{9} = 0
> ```
>
> 我们也可以直接看出 $E[X] = 0$，因为 PMF（概率质量函数）关于 0 对称。
>
> 为求 $X$ 的方差（variance），我们先计算
>
> ```math
> E[X^2] = \sum_{x=-2}^{2} x^2\, p_X(x) = 4\cdot\frac{1}{9} + 1\cdot\frac{2}{9} + 0\cdot\frac{3}{9} + 1\cdot\frac{2}{9} + 4\cdot\frac{1}{9} = \frac{4}{3}
> ```
>
> 以及
>
> ```math
> \mathrm{var}(X) = E[X^2] - (E[X])^2 = \frac{4}{3}
> ```
>
> (b) 令 $Z = X^2$。把 $X$ 的可能取值及其概率与 $Z$ 的可能取值相匹配，得到
>
> ```math
> p_Z(z) = \begin{cases} 2/9, & z = 4 \\ 4/9, & z = 1 \\ 3/9, & z = 0 \\ 0, & \text{otherwise} \end{cases}
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；本题以两种方式计数「从 $n$ 人中选出俱乐部（club）：$k$ 名成员，其中一人任会长（leader）、另一人任司库（treasurer）」的方式数，从而证明 $\sum_{k=2}^{n} k(k-1)\binom{n}{k} = n(n-1)2^{n-2}$。）</span>

> <span style="color:#2471a3;">[solution]</span> 考虑从 $n$ 个人中选出 $k$ 个人组成一个俱乐部，其中一人被指定为会长，另一人为司库。我们可以先选会长（$n$ 种选法），再选司库（$n-1$ 种选法），然后从其余 $n-2$ 个人中选出一个子集。这样，共有 $n(n-1)2^{n-2}$ 个可能的俱乐部。另一方面，对任意给定的 $k$，俱乐部成员有 $\dbinom{n}{k}$ 种选法，会长与司库有 $k(k-1)$ 种选法，因此 $k$ 人俱乐部共有 $k(k-1)\dbinom{n}{k}$ 个。对所有 $k$ 求和，我们看到可能的俱乐部总数为
>
> ```math
> \sum_{k=2}^{n} k(k-1)\binom{n}{k}
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**G1†**</span>

一家糖果厂有无限供应的红、橙、黄、绿、蓝、黑、白、紫八色软糖豆（jelly beans）。工厂把软糖豆装罐，使得每罐有 200 颗豆，其中红豆与橙豆数量相等，黄豆与绿豆数量相等，黑豆比蓝豆多一颗，紫豆比白豆多三颗。

<!-- ===== PDF p4 ===== -->

**（续）** 举例来说，一种可能的颜色分布是一罐 50 颗黄、50 颗绿、1 颗黑、48 颗白和 51 颗紫的软糖豆。作为一种营销噱头，工厂保证没有两罐的颜色分布相同。工厂最多能生产多少罐？

> <span style="color:#2471a3;">[solution]</span> **答案（Answer）**：$\dbinom{101}{3} = 166650$。
>
> **解答（Solution）**：令 $N_1, N_2, N_3, N_4, N_5, N_6, N_7, N_8$ 分别表示一罐中红、橙、黄、绿、蓝、黑、白、紫软糖豆的数量。在方程
>
> ```math
> x_1 + x_2 + x_3 + x_4 = 98
> ```
>
> 的非负整数解 $x = (x_1, x_2, x_3, x_4)$ 与满足条件
>
> ```math
> N_2 = N_1,\quad N_4 = N_3,\quad N_6 = N_5 + 1,\quad N_8 = N_7 + 3,\quad \sum_{i=1}^{8} N_i = 200
> ```
>
> 的非负整数序列 $N = (N_1, N_2, \ldots, N_8)$（即可能的颜色安排）之间，存在一一对应（one-to-one correspondence）
>
> ```math
> x = (x_1, x_2, x_3, x_4) \;\mapsto\; N = (x_1, x_1, x_2, x_2, x_3, x_3 + 1, x_4, x_4 + 3)
> ```
>
> 可能的解 $x$ 的个数，按照下面给出的更一般问题的解答，为 $\dbinom{101}{3}$：
>
> 给定一个非负整数 $n$ 和一个正整数 $k$，考虑方程
>
> ```math
> x_1 + x_2 + \ldots + x_k = n
> ```
>
> 以非负整数变量 $x_1, x_2, \ldots, x_k$ 求解。求解的总数（方程 $x_1 + x_2 = 1$ 的解 $x_1 = 1, x_2 = 0$ 与 $x_1 = 0, x_2 = 1$ 视为不同的解）。
>
> **答案**：$\dbinom{n+k-1}{k-1} = \dbinom{n+k-1}{n}$。
>
> **解答**：方程 $x_1 + \ldots + x_k = n$ 的非负整数解与由 $n+k-1$ 个符号（$n$ 个「o」和 $k-1$ 个「|」）组成的序列之间存在一一对应：解 $x = (x_1, \ldots, x_k)$ 映射到这样一个序列，其中第 $i$ 个「|」（$i \in \{1, 2, \ldots, k-1\}$）位于第 $x_1 + \ldots + x_i + i$ 个位置。在这个双射（bijection）中，相邻「|」之间「o」的个数对应 $x_i$ 的值。因此，解的总数等于在长度为 $n+k-1$ 的序列中为「|」符号选出 $k-1$ 个位置的选法数。

<span style="color:#7f8c8d;">† 对 6.431 为必做（Required）；对 6.041 为选做（optional）。</span>

<!-- ===== PDF p5 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 尾页：6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010，http://ocw.mit.edu/terms —— 无实质题目内容。）</span>
