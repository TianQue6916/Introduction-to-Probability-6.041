<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 10 解答（Tutorial 10: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 11 月 18/19 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering &amp; Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

<span style="color:#7f8c8d;">原解答 PDF 未附题面；以下题面译自 MIT OCW 同课程 Tutorial 10 习题版（同一辅导课，2010 年 11 月 18/19 日）。</span>

设 $X$ 为随机选出的一名加拿大人的身高（单位：米），每位加拿大人被选中的概率相同，并记 $E[X] = h$。Bo 想估计 $h$。由于他确信没有加拿大人身高超过 3 米，Bo 决定采用 1.5 米作为 $X$ 的 standard deviation（标准差）的保守（偏大）取值。为估计 $h$，Bo 对随机选出的 $n$ 名加拿大人的身高取平均，并将该量记为 $H$。

**(a)** 用 $h$ 与 Bo 对 $X$ 标准差的 1.5 米界，求出 $H$ 的期望与标准差。

**(b)** 请帮 Bo 求出 $n$ 的最小值（$n > 0$），使得 Bo 的估计量 $H$ 的标准差小于 0.01 米。

**(c)** Bo 希望"99% 地确信"他的估计与加拿大人真实平均身高相差不超过 5 厘米。使用 Chebyshev inequality（切比雪夫不等式），求出让 Bo 满意的 $n$ 的最小值。

**(d)** 如果我们认同"没有加拿大人身高超过三米"，为什么把 1.5 米用作随机选出的加拿大人身高 $X$ 的标准差上界是正确的？

<span style="color:#2471a3;">**[solution]**</span>

> 注意 $n$ 是 deterministic（确定性的），而 $H$ 是 random variable（随机变量）。
>
> **(a)** 用 $X_1, X_2, \ldots$ 表示各次（随机）测得的身高：
>
> ```math
> H = \frac{X_1 + X_2 + \cdots + X_n}{n}
> ```
>
> ```math
> E[H] = \frac{E[X_1 + X_2 + \cdots + X_n]}{n} = \frac{nE[X]}{n} = h
> ```
>
> ```math
> \begin{aligned}
> \sigma_H &= \sqrt{\mathrm{var}(H)} = \sqrt{\frac{n\,\mathrm{var}(X)}{n^2}} \\
> &= \frac{1.5}{\sqrt{n}}
> \end{aligned}
> ```
>
> （独立随机变量（independent r.v.s）之和的方差等于各方差之和。）
>
> <span style="color:#1e8449;">**[mathtip]**　末步取 $\sigma_X = 1.5$（Bo 的保守界）；一般地 $\sigma_H = \sigma_X/\sqrt{n}$。</span>
>
> **(b)** 解 $\dfrac{1.5}{\sqrt{n}} < 0.01$，得 $n > 22500$。
>
> **(c)** 对 $H$ 应用 Chebyshev inequality（切比雪夫不等式），并代入 (a) 中的 $E[H]$ 与 $\mathrm{var}(H)$：
>
> ```math
> P(|H - h| \geq t) \leq \left(\frac{\sigma_H}{t}\right)^2
> ```
>
> ```math
> P(|H - h| < t) \geq 1 - \left(\frac{\sigma_H}{t}\right)^2
> ```
>
> 要做到"99% 地确信"，需后一个概率至少为 0.99。于是解
>
> ```math
> 1 - \left(\frac{\sigma_H}{t}\right)^2 \geq 0.99
> ```
>
> 代入 $t = 0.05$ 与 $\sigma_H = \dfrac{1.5}{\sqrt{n}}$，得
>
> ```math
> n \geq \left(\frac{1.5}{0.05}\right)^2 \cdot \frac{1}{0.01} = 90000\,.
> ```
>
> **(d)** 直观上，取值于范围 $[0, b]$ 的随机变量 $X$，其方差在 $X$ 以概率 0.5 取 0、以概率 0.5 取 $b$ 时最大；此时 $X$ 的方差为 $b^2/4$，标准差为 $b/2$。更正式地，由于 $E[(X - c)^2]$ 在 $c = E[X]$ 处取最小值，故对任何取值于 $[0, b]$ 的随机变量 $X$，有
>
> ```math
> \begin{aligned}
> \mathrm{var}(X) &\leq E\left[\left(X - \frac{b}{2}\right)^2\right] \\
> &= E[X^2] - bE[X] + \frac{b^2}{4} \\
> &= E[X(X - b)] + \frac{b^2}{4} \\
> &\leq 0 + \frac{b^2}{4},
> \end{aligned}
> ```
>
> 因为 $0 \leq X \leq b\ \Rightarrow\ X(X - b) \leq 0$。于是 $\sigma_X \leq b/2$。在本例中 $b = 3$，故 $\sigma_X \leq 3/2$。

<!-- ===== PDF p2 ===== -->

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

<span style="color:#7f8c8d;">原解答 PDF 未附题面；以下题面译自 MIT OCW 同课程 Tutorial 10 习题版。</span>

在修 6.041 的每一周里，学生要么"跟上进度"（up-to-date），要么"落了后"（behind）。若她在给定的一周里跟上了进度，则她下一周"跟上"（或"落后"）的概率为 0.8（或 0.2）；若她在该周落后了，则她下一周"跟上"（或"落后"）的概率为 0.6（或 0.4）。假设这些概率与她此前各周的状态无关，因此该情形可建模为一个 2 状态的 Markov chain（马尔可夫链）：状态 1 表示学生"跟上"，状态 2 表示学生"落后"。

**(a)** 计算从状态 2 出发到达状态 1 的 mean first passage time（平均首达时间）。

**(b)** 计算到达状态 1 的 mean recurrence time（平均回归时间）。

<span style="color:#2471a3;">**[solution]**</span>

> **(a)** 取 $s = 1$，得 $t_1 = 0$，且
>
> ```math
> t_2 = 1 + \sum_{j=1}^{m} p_{ij}\, t_j \quad \forall\, i \neq s,
> ```
>
> ```math
> = 1 + p_{22}\, t_2 \quad \Rightarrow \quad t_2 = 5/3\,.
> ```
>
> **(b)**
>
> ```math
> t_s^* = 1 + \sum_{j=1}^{m} p_{sj}\, t_j
> ```
>
> ```math
> t_1^* = 1 + p_{12}\, t_2 = 4/3\,.
> ```
>
> <span style="color:#1e8449;">**[mathtip]**　按题面，$p_{22} = 0.4$（落后 $\to$ 落后），$p_{12} = 0.2$（跟上 $\to$ 落后）。故 $t_2 = 1 + 0.4\,t_2 \Rightarrow t_2 = 1/0.6 = 5/3$；$t_1^* = 1 + 0.2 \times \frac{5}{3} = \frac{4}{3}$。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#7f8c8d;">原解答 PDF 未附题面；以下题面译自 MIT OCW 同课程 Tutorial 10 习题版。</span>

考虑如下 Markov chain（马尔可夫链）：

<span style="color:#7f8c8d;">【图】习题版原页此处为 4 状态马尔可夫链的状态转移图（状态 1–4，含自环与状态间转移箭头）。原图由后处理统一插入。</span>

该过程的 steady-state probabilities（平稳概率）为

```math
\pi_1 = \frac{6}{31}, \qquad \pi_2 = \frac{9}{31}, \qquad \pi_3 = \frac{6}{31}, \qquad \pi_4 = \frac{10}{31}\,.
```

假设在第一次转移之前，过程处于状态 1。

**(a)** 求 $K$ 的期望与方差，其中 $K$ 为直至并包含"过程下一次返回状态 1 的那一次转移"在内的转移次数。

**(b)** "第 1000 次转移所得的状态，既不同于第 999 次转移所得的状态、也不同于第 1001 次转移所得状态"的概率是多少？

<span style="color:#2471a3;">**[solution]**</span>

> **(a)** $K = 2 + X_1 + X_2$，其中 $X_1$ 与 $X_2$ 为参数分别是 $2/3$ 与 $3/5$、相互独立的 exponential random variables（指数随机变量）。
>
> <span style="color:#1e8449;">**[note]**　原文如此（exponential）。但由下文所用公式 $E[X_i] = 1/p_i$、$\mathrm{var}(X_i) = (1-p_i)/p_i^2$ 可验证：$X_1, X_2$ 实为参数 $p_1 = 2/3$、$p_2 = 3/5$ 的 geometric random variables（几何随机变量）——按此算得 $\mathrm{var}(K) = \frac{1-2/3}{(2/3)^2} + \frac{1-3/5}{(3/5)^2} = \frac{3}{4} + \frac{10}{9} = \frac{67}{36}$，与原解结果一致；若为指数分布，方差应为 $1/p_i^2$，不吻合。故"exponential"应为"geometric"之笔误。</span>
>
> ```math
> \begin{aligned}
> E[K] &= 2 + 1/p_1 + 1/p_2 \\
> &= 31/6\,.
> \end{aligned}
> ```
>
> ```math
> \begin{aligned}
> \mathrm{var}(K) &= \frac{1 - p_1}{p_1^2} + \frac{1 - p_2}{p_2^2} \\
> &= 67/36\,.
> \end{aligned}
> ```
>
> **(b)**
>
> ```math
> \begin{aligned}
> P(A) &= P(X_{999} \neq X_{1000} \neq X_{1001}) \\
> &= \sum_{i=1}^{4} P(A \mid X_{999} = i)\,\pi_i \\
> &= \tfrac{2}{3}\pi_1 + \tfrac{2}{3}\pi_2 + \tfrac{3}{5}\pi_3 + \tfrac{3}{5}\pi_4 \\
> &= 30/93 + 48/155 \approx 0.6323\,.
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[mathtip]**　代入题给平稳概率：$\frac{2}{3}(\pi_1 + \pi_2) = \frac{2}{3}\cdot\frac{15}{31} = \frac{30}{93}$，$\frac{3}{5}(\pi_3 + \pi_4) = \frac{3}{5}\cdot\frac{16}{31} = \frac{48}{155}$，合计 $\frac{98}{155} \approx 0.6323$。</span>

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability）· Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms</span>
