<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 9 解答（Recitation 9: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期，2010 年 10 月 7 日）</span>

<span style="color:#1e8449;">**[note]** 本解答 PDF 原文不含题面（各题直接给出解答或教材引用）。为便于阅读，以下各题题面均译自 MIT OCW 同课程配套的《Recitation 9》题目 PDF（官方原文，逐题对应）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

设 $X$ 为参数 $\lambda > 0$ 的 exponential random variable（指数随机变量）。计算 $X$ 属于诸区间 $[n,\, n+1]$（其中 $n$ 为奇数）中某一个的概率。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 我们先对任意非负整数 $n$ 计算 $X$ 落入区间 $[n, n+1]$ 的概率；随后再把所有奇的正整数值 $n$ 对应的概率相加。
>
> 我们本可以在给定区间上对 $X$ 的 PDF（probability density function，概率密度函数）积分，但这里改用 CDF（cumulative distribution function，累积分布函数）。利用指数随机变量的 CDF：
>
> ```math
> P(n \le X \le n+1) = F_X(n+1) - F_X(n) = \bigl(1 - e^{-\lambda(n+1)}\bigr) - \bigl(1 - e^{-\lambda n}\bigr) = e^{-\lambda n}\bigl(1 - e^{-\lambda}\bigr).
> ```
>
> 其中 $F_X$ 是 $X$ 的 CDF，即 $F_X(x) = P(X \le x) = 1 - e^{-\lambda x}$（$x \ge 0$）。由于这些区间互不相交（disjoint），我们可以对所有奇整数 $n$ 将该概率求和，得到所求概率：
>
> ```math
> P(\{X \in [n, n+1] \text{ 对某个奇数 } n\}) = \sum_{n\,\text{为奇数}} e^{-\lambda n}\bigl(1 - e^{-\lambda}\bigr) = \bigl(1 - e^{-\lambda}\bigr)\sum_{k=0}^{\infty} e^{-\lambda(2k+1)}
> ```
>
> 这里把奇数 $n$ 写成 $n = 2k+1$（$k = 0, 1, 2, \dots$），从而把所有奇数对应的项化为对 $k$ 的求和。接着：
>
> ```math
> = \bigl(1 - e^{-\lambda}\bigr)\sum_{k=0}^{\infty} e^{-\lambda}\bigl(e^{-2\lambda}\bigr)^{k} = \bigl(1 - e^{-\lambda}\bigr)\,\frac{e^{-\lambda}}{1 - e^{-2\lambda}}
> ```
>
> 上一步用了几何级数（geometric series）求和公式 $\sum_{k=0}^{\infty} r^{k} = \frac{1}{1-r}$（$|r| < 1$），这里 $r = e^{-2\lambda} < 1$。最后约去公因子：
>
> ```math
> = \bigl(1 - e^{-\lambda}\bigr)\,\frac{e^{-\lambda}}{\bigl(1 - e^{-\lambda}\bigr)\bigl(1 + e^{-\lambda}\bigr)} = \frac{e^{-\lambda}}{1 + e^{-\lambda}}.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

（教材例 3.13（Example 3.13），第 165 页）指数随机变量是无记忆的（memoryless）。一只新灯泡烧坏前的工作时间 $T$ 是参数为 $\lambda$ 的指数随机变量。Ariadne 打开灯后离开房间，$t$ 个时间单位后回到房间，发现灯泡仍亮着——这对应事件 $A=\{T>t\}$。设 $X$ 为直到灯泡烧坏的额外等待时间。求在给定事件 $A$ 的条件下 $X$ 的 conditional CDF（条件分布函数）。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 教材（textbook）例 3.13（Example 3.13，第 165 页）的核心结论如下，此处补全以便直接阅读。
>
> 额外等待时间 $X$ 满足 $X = T - t$，其中已给定 $T > t$。指数分布的无记忆性（memoryless property）断言：无论灯泡已经亮了多久（即 $t$ 有多大），剩下的等待时间都与一枚新灯泡的寿命同分布。具体地，对任意 $x \ge 0$，
>
> ```math
> P(X \le x \mid T > t) = P(T - t \le x \mid T > t) = P(T \le t + x \mid T > t).
> ```
>
> 由条件概率定义 $P(B \mid A) = \frac{P(A \cap B)}{P(A)}$，并利用事件 $\{T > t\}$ 与 $\{T \le t + x\}$ 的交为 $\{t < T \le t + x\}$，得
>
> ```math
> P(T \le t + x \mid T > t) = \frac{P(t < T \le t + x)}{P(T > t)} = \frac{F_T(t+x) - F_T(t)}{1 - F_T(t)}.
> ```
>
> 代入指数分布的 CDF $F_T(u) = 1 - e^{-\lambda u}$（$u \ge 0$）：
>
> ```math
> \frac{\bigl(1 - e^{-\lambda(t+x)}\bigr) - \bigl(1 - e^{-\lambda t}\bigr)}{e^{-\lambda t}} = \frac{e^{-\lambda t} - e^{-\lambda(t+x)}}{e^{-\lambda t}} = 1 - e^{-\lambda x}.
> ```
>
> 因此，$X$ 在事件 $A$ 下的条件 CDF 为
>
> ```math
> P(X \le x \mid T > t) = 1 - e^{-\lambda x}, \qquad x \ge 0,
> ```
>
> 它与 $t$ 无关，且正是参数 $\lambda$ 的指数分布的 CDF——即"剩余寿命仍是指数分布"。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

教材（text）第 191 页习题 3.23（Problem 3.23）。设随机变量 $X$ 与 $Y$ 的 joint PDF（联合概率密度函数）在以 $(0, 0)$、$(0, 1)$、$(1, 0)$ 为顶点的三角形上均匀分布（uniform）。

- **(a)** 求 $X$ 与 $Y$ 的联合 PDF。
- **(b)** 求 $Y$ 的 marginal PDF（边缘概率密度函数）。
- **(c)** 求在给定 $Y$ 条件下 $X$ 的 conditional PDF（条件概率密度函数）。
- **(d)** 求 $E[X \mid Y=y]$，并利用全期望定理（total expectation theorem）以 $E[Y]$ 表示 $E[X]$。
- **(e)** 利用问题的对称性求 $E[X]$ 的值。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 教材第 191 页习题 3.23（Problem 3.23, page 191 in text）。以下补全解答，便于直接阅读。
>
> 三角形区域记为 $D = \{(x, y) \mid x \ge 0,\ y \ge 0,\ x + y \le 1\}$，其面积为 $\frac12$。
>
> **(a)** 均匀分布在区域 $D$ 上，故 joint PDF 是面积倒数（区域内）或 $0$（区域外）：
>
> ```math
> f_{X,Y}(x,y) = \begin{cases} 2, & (x,y) \in D,\\[2pt] 0, & \text{否则}. \end{cases}
> ```
>
> **(b)** 对 $x$ 积分求 marginal PDF。固定 $y \in [0,1]$，$x$ 的范围是 $0 \le x \le 1 - y$：
>
> ```math
> f_Y(y) = \int_{0}^{1-y} 2\,dx = 2(1 - y), \qquad 0 \le y \le 1.
> ```
>
> **(c)** 条件 PDF 由 $f_{X\mid Y}(x \mid y) = \frac{f_{X,Y}(x,y)}{f_Y(y)}$ 给出（在 $f_Y(y) > 0$ 处，即 $0 < y < 1$）。当 $0 < y < 1$ 且 $0 \le x \le 1-y$ 时：
>
> ```math
> f_{X\mid Y}(x \mid y) = \frac{2}{2(1-y)} = \frac{1}{1-y}, \qquad 0 \le x \le 1-y.
> ```
>
> 即在给定 $Y=y$ 时，$X$ 在区间 $[0,\,1-y]$ 上均匀分布。
>
> **(d)** 由 (c)，均匀分布在 $[0,\,1-y]$ 上的均值为区间中点，故
>
> ```math
> E[X \mid Y=y] = \frac{1-y}{2}.
> ```
>
> 于是 $E[X \mid Y] = \frac{1-Y}{2}$。由全期望定理（total expectation theorem）$E[X] = E\bigl[E[X \mid Y]\bigr]$：
>
> ```math
> E[X] = E\!\left[\frac{1-Y}{2}\right] = \frac{1 - E[Y]}{2}.
> ```
>
> **(e)** 区域 $D$ 关于直线 $x = y$ 对称，故 $X$ 与 $Y$ 的分布完全相同，特别地 $E[X] = E[Y]$。代入 (d) 的结果 $E[X] = \frac{1 - E[Y]}{2}$ 得
>
> ```math
> E[X] = \frac{1 - E[X]}{2} \;\Longrightarrow\; 2E[X] = 1 - E[X] \;\Longrightarrow\; E[X] = \frac{1}{3}.
> ```
>
> （也可直接算 $E[Y] = \int_0^1 y \cdot 2(1-y)\,dy = \frac13$，与 $E[X] = \frac13$ 一致。）

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

<span style="color:#1e8449;">**[note]** 解答 PDF 将本题标注为教材第 191 页习题 3.22 第 (i) 小问；配套题目 PDF 中该题的题面如下。</span>

我们有一根单位长度的木棒，要把它折成三段：用均匀 PDF（uniform PDF）随机且独立地在木棒上选取两个点，并在这两点处折断。剩下三段恰好能构成一个三角形的概率是多少？

> <span style="color:#2471a3;">**[solution]**</span>
>
> 教材（text）第 191 页习题 3.22（Problem 3.22）第 (i) 小问（part (i)）。以下补全解答，便于直接阅读。
>
> 设两个折断点到木棒一端的距离分别为 $X$、$Y$，二者独立且在 $[0,1]$ 上均匀分布。不妨令 $a = \min(X,Y)$、$b = \max(X,Y)$，则三段长度依次为 $a$、$b-a$、$1-b$。
>
> 三段能构成三角形的充要条件是**任意一段都小于另外两段之和**（等价于最长的一段小于总长的一半 $\frac12$）。对三角形条件而言，只需三段长度都小于 $\frac12$。
>
> 考察 $(X, Y)$ 在单位正方形 $[0,1]^2$ 上的均匀分布。三段构成三角形当且仅当
>
> ```math
> a < \frac12, \qquad b - a < \frac12, \qquad 1 - b < \frac12 .
> ```
>
> 其中 $a = \min(X,Y)$、$b = \max(X,Y)$。第三个条件等价于 $b > \frac12$。这三个不等式在单位正方形中划出的区域由对称性分为两块（$X < Y$ 与 $X > Y$），每块面积相同。
>
> 取 $X < Y$ 的情形（此时 $a = X$、$b = Y$），条件化为 $X < \frac12$、$Y - X < \frac12$、$Y > \frac12$。该子区域是三角形，三个顶点为 $(0,\frac12)$、$(\frac12,1)$、$(\frac12,\frac12)$，其面积为 $\frac12 \cdot \frac12 \cdot \frac12 = \frac18$；$X > Y$ 的情形由对称性也贡献 $\frac18$。故总概率为
>
> ```math
> P(\text{能构成三角形}) = \frac{1}{8} + \frac{1}{8} = \frac{1}{4}.
> ```

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 标准版权尾页：MIT OpenCourseWare, http://ocw.mit.edu, 6.041/6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010；课程内容至此结束。）</span>
