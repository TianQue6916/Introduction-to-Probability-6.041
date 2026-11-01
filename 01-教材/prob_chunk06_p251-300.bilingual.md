<!-- ===== PDF p251 ===== -->

<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）**</span> — §4.5（续）

<span style="color:#c0392b;">**§4.5　随机个数的独立随机变量之和（Sum of a Random Number of Independent Random Variables）**</span> <span style="color:#7f8c8d;">（Sec. 4.5，PDF 页码 241；本页续接上一页 §4.5 正文的期望与方差推导。）</span>

> <span style="color:#7f8c8d;">承接上一页：设 $N$ 为取非负整数值的随机变量，$X_1, X_2, \ldots$ 为一列独立同分布的随机变量，且它们与 $N$ 相互独立，记 $Y = X_1 + \cdots + X_N$。上一页已证对固定的 $n$ 有 $E[Y \mid N = n] = n\,E[X]$（其中 $X$ 表示与诸 $X_i$ 同分布的随机变量，令 $X = X_1$）。本页继续推导方差与生成函数。</span>

由于上式对每个非负整数 $n$ 都成立，因此有

```math
E[Y \mid N] = N\,E[X].
```

利用迭代期望律（law of iterated expectations），可得

```math
E[Y] = E\big[E[Y \mid N]\big] = E\big[N\,E[X]\big] = E[N]\;E[X].
```

类似地，

```math
\operatorname{var}(Y \mid N = n)
= \operatorname{var}(X_1 + \cdots + X_N \mid N = n)
= \operatorname{var}(X_1 + \cdots + X_n)
= n\,\operatorname{var}(X).
```

由于上式对每个非负整数 $n$ 都成立，随机变量 $\operatorname{var}(Y \mid N)$ 等于 $N\,\operatorname{var}(X)$。现在我们利用全方差律（law of total variance）来求

```math
\begin{aligned}
\operatorname{var}(Y)
&= E\big[\operatorname{var}(Y \mid N)\big] + \operatorname{var}\big(E[Y \mid N]\big)\\
&= E\big[N\,\operatorname{var}(X)\big] + \operatorname{var}\big(N\,E[X]\big)\\
&= E[N]\;\operatorname{var}(X) + \big(E[X]\big)^2 \operatorname{var}(N).
\end{aligned}
```

生成函数（transform）的计算沿类似的思路进行。在给定 $N = n$ 的条件下与 $Y$ 关联的生成函数为 $E\left[e^{sY} \mid N = n\right]$。然而，在给定 $N = n$ 的条件下，$Y$ 是相互独立的随机变量 $X_1, \ldots, X_n$ 之和，于是

```math
E\left[e^{sY} \mid N = n\right]
= E\left[e^{sX_1} \cdots e^{sX_n}\right]
= E\left[e^{sX_1}\right] \cdots E\left[e^{sX_n}\right]
= \big(M_X(s)\big)^n,
```

其中 $M_X(s)$ 是与 $X_i$（每个 $i$）关联的生成函数。利用迭代期望律，与 $Y$ 关联的（无条件）生成函数为

```math
M_Y(s) = E\left[e^{sY}\right] = E\left[E\left[e^{sY} \mid N\right]\right] = E\left[\big(M_X(s)\big)^N\right].
```

利用下面的观测结论，我们得到

```math
M_Y(s) = \sum_{n = 0}^{\infty} \big(M_X(s)\big)^n p_N(n).
```

> <span style="color:#7f8c8d;">本页 §4.5 正文推导自 $E[Y\mid N] = NE[X]$ 起续接上一页，连续呈现的条件期望均值、条件方差与生成函数三组推导即为本节标准推导流程；原书此处分页衔接处（「利用观测结论」一句）未指明该观测的显式式样，语义上即 $E\left[\big(M_X(s)\big)^N\right] = \sum_{n} \big(M_X(s)\big)^n p_N(n)$，此处按上文自然补全，不作臆造。</span>
<!-- ===== PDF p252 ===== -->

<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）**</span>

<span style="color:#c0392b;">**§4.5　随机个数的独立随机变量之和（Sum of a Random Number of Independent Random Variables）** —— 正文子节（续）</span>

> <span style="color:#7f8c8d;">承接上一页：页首原文先与前面导出的 $M_Y(s)$ 公式式相互对照，随后给出如下「性质」总结框，并以 **Example 4.34** 作演示（该例自本页开始，延续到下一页）。</span>

将上式与公式式（comparing）相互对照：

```math
M_N(s) = E\!\left[ e^{sN} \right] = \sum_{n=0}^{\infty} e^{s n}\, p_N(n) ,
```

我们看出（we see that）$M_Y(s) = M_N\!\left( \log M_X(s) \right)$。即，$M_Y(s)$ 可这样从关于 $M_N(s)$ 的公式式得到：把其中的 $s$ 换成 $\log M_X(s)$；等价地，把 $e^s$ 换成 $M_X(s)$。

让我们把目前已导出的性质总结如下（Let us summarize the properties derived so far）。

<span style="color:#c0392b;">**随机个数的独立随机变量之和的性质（Properties of the Sum of a Random Number of Independent Random Variables）**</span>

设 $X_1, X_2, \ldots$ 为同分布（identically distributed）的随机变量，均值为 $E[X]$、方差为 $\operatorname{var}(X)$。设 $N$ 为取非负整数值（nonnegative integer values）的随机变量。我们假定所有这些随机变量均相互独立（independent），并考虑和式

```math
Y = X_1 + \cdots + X_N .
```

那么有下列结论：

- $E[Y] = E[N]\, E[X]$。
- $\operatorname{var}(Y) = E[N]\, \operatorname{var}(X) + \left( E[X] \right)^{2} \operatorname{var}(N)$。
- 我们有变换关系 $M_Y(s) = M_N\!\left( \log M_X(s) \right)$。
- 等价地，变换 $M_Y(s)$ 的求法是：以变换 $M_N(s)$ 为出发点，把其中每一次出现的 $e^{s}$ 都替换为 $M_X(s)$。

<span style="color:#2471a3;">**[example]**</span>  <span style="color:#00838f;">**Example 4.34（偏远村庄的三座加油站）**</span>

一个偏远村庄（remote village）有三座加油站。每座加油站在任意给定的一天开放的概率为 $1/2$，且互不相关（independent of the others）。每座加油站中可用的汽油量未知，在 $0$ 到 $1000$ 加仑（gallons）之间均匀分布（uniformly distributed）。我们希望刻画那些正开放的加油站中可用的总汽油量这一概率规律（probability law）。

开放加油站的数量（number）$N$ 是参数 $p = 1/2$ 的二项随机变量（binomial random variable），其相应的变换为

```math
M_N(s) = \left( \frac{1 + e^{s}}{2} \right)^{3} .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本例中 $M_N(s)$ 的具体算式在 OCR 中被吞（行间仅余「...the corresponding transform is」即跳到下一公式），上面按二项随机变量（$n=3$, $p=1/2$）的标准变换式重建为 $M_N(s)=\left(\frac{1+e^{s}}{2}\right)^{3}$；若需最严格原文请回查原书页 242。</span>

与一座开放加油站内可用汽油量相对应的变换 $M_X(s)$ 为

```math
M_X(s) = \frac{e^{1000 s} - 1}{1000 s} .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 末行分子 `e^{1000 s} - 1` 与分母 `1000 s` 在 OCR 中碎裂（读作 `elOOOs _ 1` 与 `l 0O0 s`），此式系按 $0$ 到 $1000$ 加仑均匀分布的变换式重建；本例延续到下一页继续讨论。</span>
<!-- ===== PDF p253 ===== -->
<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）—— §4.5（续）随机个数的独立随机变量之和（Sum of a Random Number of Independent Random Variables）**</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 4.34（续）—— 三家油站的汽油总量（three gas stations）**</span>

> <span style="color:#7f8c8d;">续上一页：某边远村庄有三家油站，每家任一给定日子营业的概率为 $1/2$，彼此独立；每家油站可用的汽油量未知，在 $0$ 到 $1000$ 加仑之间均匀分布。本页承接其解法的末尾，算出总可用量的变换 $M_Y(s)$。</span>

与总可用量 $Y$ 相关联的变换与 $M_N(s)$ 相同，只是须把其中每一次出现的 $e^s$ 替换为 $M_X(s)$，即

```math
M_Y(s) = \frac{1}{8}\left( 1 + \frac{e^{1000s} - 1}{1000s} \right)^{3}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式为按二项变换 $M_N(s) = \big((1+e^s)/2\big)^{3} = (1+e^s)^{3}/8$ 并把每一处 $e^s$ 替换为 $M_X(s) = (e^{1000s}-1)/(1000s)$ 而重建的 $M_Y(s)$；原图把系数 `1/8`、括号与指数 `3` 拆散在数行，数值一律未改动。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 4.35　服从几何分布的独立指数随机变量个数之和（Sum of a Geometric Number of Independent Exponential Random Variables）**</span>

Jane 连续走访若干家书店，寻找小说《远大前程》（*Great Expectations*）。任一给定的书店以概率 $p$ 存有此书，且各书店之间相互独立。在被走访的一家典型书店中，Jane 会花费一段随机的时间，服从参数为 $\lambda$ 的指数分布，直到她要么找到这本书、要么判定该书店并无此书为止。我们假定 Jane 会一直走访下去、直到买到书为止，并且她在每家书店所花的时间与其他一切都相互独立。我们希望求出她在书店里花费的总时间的均值、方差与 PDF。

走访的书店总数 $N$ 服从参数为 $p$ 的几何分布（geometrically distributed）。因此，在书店里花费的总时间 $Y$ 是数量服从几何分布的 $N$ 个相互独立的指数随机变量 $X_1, X_2, \ldots$ 之和。我们有

```math
E[Y] = E[N]\,E[X] = \frac{1}{p}\cdot\frac{1}{\lambda}.
```

利用几何随机变量与指数随机变量的方差公式，我们还得到

```math
\operatorname{var}(Y)
= E[N]\operatorname{var}(X) + (E[X])^2 \operatorname{var}(N)
= \frac{1}{p}\cdot\frac{1}{\lambda^2} + \frac{1}{\lambda^2}\cdot \frac{1-p}{p^{2}}
= \frac{1}{\lambda^{2} p^{2}}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 方差式为 $E[N]=1/p$、$\operatorname{var}(N)=(1-p)/p^2$、$E[X]=1/\lambda$、$\operatorname{var}(X)=1/\lambda^2$；OCR 把 `p1`、`λ1`、`A12`、`λ2p2` 等碎块拆行，最终式 $1/(\lambda^2 p^2)$ 由化简 $[p + (1-p)]/(\lambda^2 p^2)$ 得到，数值一律未改动。</span>

为求变换 $M_Y(s)$，先回忆

```math
M_X(s) = \frac{\lambda}{\lambda - s}.
```

于是，从 $M_N(s)$ 出发并把其中每一处出现的 $e^{s}$ 替换为 $M_X(s)$，即可得到 $M_Y(s)$。由此得

```math
M_Y(s) = \frac{p\,M_X(s)}{1 - (1-p)M_X(s)}
= \frac{p\,\dfrac{\lambda}{\lambda - s}}{1 - (1-p)\,\dfrac{\lambda}{\lambda - s}},
```

化简为

```math
M_Y(s) = \frac{p\lambda}{p\lambda - s}.
```

我们认出这正是参数为 $p\lambda$ 的指数分布随机变量所对应的变换，因此

```math
f_Y(y) = p\lambda\, e^{-p\lambda\, y}, \qquad y \ge 0.
```
<!-- ===== PDF p254 ===== -->
> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）—— 正文 §4.5（随机个数的独立随机变量之和），页印 244。本页含三部分：上一例尾部结论、Example 4.36 全例、§4.6 小结与讨论的开场。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 4.35（续）——几何个数的独立指数随机变量之和（Sum of a Geometric Number of Independent Exponential Random Variables）的结论讨论**</span>

> <span style="color:#7f8c8d;">承接上一页：本段为上一例（随机个数 $N$ 的独立指数随机变量之和）的收尾讨论，其结论指出该几何个数指数和并不服从中途展示的简单形式。</span>

这个结果可能会令人惊讶，因为固定个数 $n$ 个独立指数随机变量之和并不服从指数分布。例如，当 $n = 2$ 时，该和所对应的变换（transform）为 $(\lambda/(\lambda - s))^2$，它并不对应于一个指数分布。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 4.36（几何个数的独立几何随机变量之和，Sum of a Geometric Number of Independent Geometric Random Variables）**</span>

本例子是上一例的离散对应情形（discrete counterpart）。设 $N$ 服从参数为 $p$ 的几何分布，并设每个随机变量 $X_i$ 服从参数为 $q$ 的几何分布。我们假设所有这些随机变量相互独立。令 $Y = X_1 + \cdots + X_N$。我们有

```math
M_X(s) = \frac{q\,e^s}{1 - (1 - q)\,e^s}.
```

为确定 $M_Y(s)$，我们从 $M_N(s)$ 的公式出发，并把每一次出现的 $e^s$ 替换为 $M_X(s)$。由此得到

```math
M_Y(s) = \frac{p\,M_X(s)}{1 - (1 - p)\,M_X(s)},
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上述中间式在原页 OCR 中被打散（分子分母碎片交错：`pMx(s)` 与 `(1−p)Mx(s)` 及其余片段错位），此处按 $M_N(s)$ 对合替换 $e^s\to M_X(s)$ 的推导语义重建为等价标准式；公式的真实朝向以结果式 $M_Y(s) = pq\,e^s\big/\big(1-(1-pq)e^s\big)$ 为准。</span>

再经若干代数运算（after some algebra），

```math
M_Y(s) = \frac{pq\,e^s}{1 - (1 - pq)\,e^s}.
```

我们得出结论：$Y$ 服从参数为 $pq$ 的几何分布。

---

<span style="color:#c0392b;">**4.6　小结与讨论（Summary and Discussion）**</span>

在本章中，我们研究了许多进阶专题。这里我们讨论其中若干重点。

在 §4.1 中，我们处理了计算一个连续随机变量 $X$ 的某函数 $g(X)$ 的概率密度函数（probability density function, PDF）这一问题。累积分布函数（cumulative distribution function, CDF）的概念在此非常有用。特别地，$g(X)$ 的 PDF 通常通过对相应的 CDF 进行计算与求导而得到。在某些情形下，例如当函数 $g$ 严格单调时，借助特殊公式可使该计算得到简化。我们还考察了一些涉及两个连续随机变量的函数 $g(X, Y)$ 的示例，其中特别地推导了两个独立随机变量之和的概率分布所满足的卷积公式（convolution formula）。

在 §4.2 中，我们引入了协方差（covariance）与相关（correlation），二者都是刻画两个随机变量之间关系的重要定性指标。协方差及其缩放版本——相关系数（correlation coefficient）——在确定相关随机变量之和的方差时都会用到。它们在 §8.4 的线性最小均方估计（linear least mean squares estimation）方法中也起着重要作用。
<!-- ===== PDF p255 ===== -->
<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）　小结与讨论（Summary and Discussion）**</span>

<span style="color:#7f8c8d;">**Sec. 4.6**（页眉小节号，印页号 245）。本章收尾的回顾性小结页，正序回顾第 4 章各节的要点。</span>

在第 4.3 节（Section 4.3）中，我们重新审视了条件（conditioning）这一主题，目的是为计算期望值和方差（expected values and variances）开发工具。我们更仔细地考察了条件期望（conditional expectation），并指出它可以被视为一个随机变量（random variable），其本身具有自己的期望和方差。我们还推导出若干相关性质，包括迭代期望定律（law of iterated expectations）和全方差定律（law of total variance）。

在第 4.4 节（Section 4.4）中，我们引入了与随机变量相关联的变换（transform），并看到这样的变换是可以计算的。反过来，我们指出：已知一个变换，与之相关联的随机变量的分布就被唯一确定。它可以通过查找常用变换的表（tables of commonly occurring transforms）等方法得到。我们发现变换可用于多种多样的目的，例如以下几项。

(a) 与某随机变量相关联的变换的知识，为计算该随机变量的矩（moments）提供了一条捷径。

(b) 与两个独立随机变量（independent random variables）之和相关联的变换，等于与它们各自相关联的变换的乘积。这一性质被用来证明确实两个独立的、正态（respectively, Poisson）随机变量之和是正态（respectively, Poisson）的。

(c) 变换可用来刻画随机个随机变量（random number of random variables）之和的分布（第 4.5 节），而这往往是用其他方法无法做到的。

最后，在第 4.5 节（Section 4.5）中，我们通过把第 4.3 节和第 4.4 节的方法结合起来，推导出随机个随机变量之和的均值、方差以及变换的公式。

> <span style="color:#7f8c8d;">[尾注] 本页为第 4 章小结页正文（无公式、无具体数值），OCR 仅有个别连排的断词（如 random vari&#x00ad;able 的连字符断行被合并不影响语义），实质无损坏。正文到本页结尾翻页，续接后续页面内容。</span>
<!-- ===== PDF p256 ===== -->
<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）**</span>

<span style="color:#c0392b;">**Problems（习题）**</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">SECTION 4.1　派生分布（Derived Distributions）</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 1（$\lvert X\rvert$ 与 $\ln \lvert X\rvert$ 的 PDF）</span>

If $X$ is a random variable that is uniformly distributed between $-1$ and $1$, find the PDF of $\lvert X\rvert$ and the PDF of $\ln \lvert X\rvert$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 2（$e^X$ 的 PDF）</span>

Find the PDF of $e^X$ in terms of the PDF of $X$. Specialize the answer to the case where $X$ is uniformly distributed between $0$ and $1$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 3（$\lvert X\rvert^{1/3}$ 与 $\lvert X\rvert^{1/4}$ 的 PDF）</span>

Find the PDFs of $\lvert X\rvert^{1/3}$ and $\lvert X\rvert^{1/4}$ in terms of the PDF of $X$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 4（地铁到站时刻与候车等待时间的 CDF/PDF）</span>

The metro train arrives at the station near your home every quarter hour starting at 6:00 a.m. You walk into the station every morning between 7:10 and 7:30 a.m., with the time in this interval being a random variable with given PDF (cf. Example 3.14, in Chapter 3). Let $X$ be the elapsed time, in minutes, between 7:10 and the time of your arrival. Let $Y$ be the time that you have to wait until you board a train. Calculate the CDF of $Y$ in terms of the CDF of $X$ and differentiate to obtain a formula for the PDF of $Y$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 5（$\lvert X - Y\rvert$ 的 CDF 与 PDF，$X,Y\sim\text{Uniform}[0,1]$）</span>

Let $X$ and $Y$ be independent random variables, uniformly distributed in the interval $[0, 1]$. Find the CDF and the PDF of $\lvert X - Y\rvert$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 6（三角形上均匀点的 $\lvert XY\rvert$ 的 CDF 与 PDF）</span>

Let $X$ and $Y$ be the Cartesian coordinates of a randomly chosen point (according to a uniform PDF) in the triangle with vertices at $(0, 1)$, $(0, -1)$, and $(1, 0)$. Find the CDF and the PDF of $\lvert XY\rvert$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 7（区间 $[0,1]$ 上两点期望距离为 $1/3$）</span>

Two points are chosen randomly and independently from the interval $[0, 1]$ according to a uniform distribution. Show that the expected distance between the two points is $1/3$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 8（$Z = X + Y$ 的 PDF，两个同参数指数随机变量之和）</span>

Find the PDF of $Z = X + Y$, when $X$ and $Y$ are independent exponential random variables with common parameter $\lambda$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 9（$X - Y$ 的 PDF，两个不同参数指数随机变量之差）</span>

Consider the same problem as in Example 4.9, but assume that the random variables $X$ and $Y$ are independent and exponentially distributed with different parameters $\lambda$ and $\mu$, respectively. Find the PDF of $X - Y$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 10（用卷积公式求 $Z = X + Y$ 的 PMF）</span>

Let $X$ and $Y$ be independent random variables with PMFs

```math
p_X(x) = \begin{cases}
\frac{1}{3}, & \text{if } x = 1,\, 2,\, 3,\\
0, & \text{otherwise},
\end{cases}
\qquad
p_Y(y) = \begin{cases}
\frac{1}{2}, & \text{if } y = 0,\\
\frac{1}{3}, & \text{if } y = 1,\\
\frac{1}{6}, & \text{if } y = -2,\\
0, & \text{otherwise}.
\end{cases}
```

Find the PMF of $Z = X + Y$, using the convolution formula.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 10 的两个 PMF 定义在 OCR 中被纵向打散、列位置错乱（`px x` 与 `py y` 的括号/条款混排，$\frac{1}{2}$、$\frac{1}{3}$、$\frac{1}{6}$ 等取值与 $x,y$ 取值错配、`=` 与 `{` 被拆行）。上面按教科书标准形式重建为 $p_X(x)=\tfrac13$（$x=1,2,3$）与 $p_Y(y)$（$y=0,1,-2$ 对应 $\tfrac12,\tfrac13,\tfrac16$）。若需严格原文请回查原书页 246。</span>
<!-- ===== PDF p257 ===== -->
<span style="color:#7f8c8d;">**第 4 章 Further Topics on Random Variables（随机变量的进一步专题）—— 习题区（Problems）延续，打印页码 247，承接上一页 p256（Problem 1–10），本页覆盖 Problem 11–15。**</span>

<span style="color:#2471a3;">**[##]**</span> <span style="color:#c0392b;">**Problems（习题）**</span>

> <span style="color:#7f8c8d;">跨页定位：p257 是第 4 章习题区中段，承接上一页 Problem 1–10，本题页为 Problem 11–15。Problem 15 为带 `*` 题（Cauchy random variable），其英文 Solution 只写到 (b) 的 CDF 计算中断，续接到下一页 p258。</span>

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 11（利用卷积公式证明两个独立 Poisson 随机变量之和仍为 Poisson）</span>

Use the convolution formula to establish that the sum of two independent Poisson random variables with parameters $\lambda$ and $\mu$, respectively, is Poisson with parameter $\lambda + \mu$.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 12（$X$、$Y$、$Z$ 在 $[0,1]$ 上独立均匀分布，求 $X+Y+Z$ 的 PDF）</span>

The random variables $X$, $Y$, and $Z$ are independent and uniformly distributed between zero and one. Find the PDF of $X + Y + Z$.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 13（对称 PDF 的独立随机变量之差如何由和之 PDF 简便求得）</span>

Consider a PDF that is positive only within an interval $[a, b]$ and is symmetric around the mean $(a+b)/2$. Let $X$ and $Y$ be independent random variables that both have this PDF. Suppose that you have calculated the PDF of $X + Y$. How can you easily obtain the PDF of $X - Y$?

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 14（竞争指数分布：灯泡寿命的两因子取最小）</span>

Competing exponentials. The lifetimes of two light bulbs are modeled as independent and exponential random variables $X$ and $Y$, with parameters $\lambda$ and $\mu$, respectively. The time at which a light bulb first burns out is

```math
Z = \min\{X, Y\}.
```

Show that $Z$ is an exponential random variable with parameter $\lambda + \mu$.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 15 $^{*}$  Cauchy random variable（柯西随机变量）</span>

**(a)** Let $X$ be a random variable that is uniformly distributed between $-1/2$ and $1/2$. Show that the PDF of $Y = \tan(\pi X)$ is

```math
f_Y(y) = \frac{1}{\pi(1 + y^2)}, \qquad -\infty < y < \infty.
```

($Y$ is called a Cauchy random variable.)

**(b)** Let $Y$ be a Cauchy random variable. Find the PDF of the random variable $X$, which is equal to the angle between $-\pi/2$ and $\pi/2$ whose tangent is $Y$.

<span style="color:#2471a3;">**[solution]**</span> **Solution.** **(a)** We first note that $Y$ is a continuous, strictly monotonically increasing function of $X$, which takes values between $-\infty$ and $\infty$, as $X$ ranges over the interval $[-1/2, 1/2]$. Therefore, we have for all scalars $y$,

```math
F_Y(y) = P(Y \le y) = P(\tan(\pi X) \le y) = P\left(\pi X \le \tan^{-1} y\right) = \frac{1}{\pi} \tan^{-1} y + \frac{1}{2},
```

where the last equality follows using the CDF of $X$, which is uniformly distributed in the interval $[-1/2, 1/2]$. Therefore, by differentiation, using the formula $\dfrac{d}{dy}(\tan^{-1} y) = \dfrac{1}{1 + y^2}$, we have for all $y$,

```math
f_Y(y) = \frac{1}{\pi(1 + y^2)}.
```

**(b)** We first compute the CDF of $X$ and then differentiate to obtain its PDF. We have for $-\pi/2 \le x \le \pi/2$,

```math
P(X \le x) = P(\tan^{-1} Y \le x) = P(Y \le \tan x) = \ \cdots
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏 / 翻页续接] 本题 (b) 的 CDF 计算式在页末中断（OCR 只给出 `P(X ≤ x) = P(tan^{-1} Y ≤ x)`、`P(Y ≤ tan x)` 与一个随后的 `=`，该处应续以 $F_Y(\tan x)$ 代入并微分得 $f_X(x)$），Solution 续接到下一页 p258。本题多处 OCR 碎裂均已按常规符号修复：电离参数名 `A`→$\lambda$、`J.L`→$\mu$、`71'`→$\pi$、`ex::`→$\infty$、`::;`→$\le$、`- 1 /2`→$-1/2$、`tan - l y`→$\tan^{-1} y$。</span>
<!-- ===== PDF p258 ===== -->
<span style="color:#7f8c8d;">**第 4 章 Further Topics on Random Variables（随机变量的进一步专题）—— 习题区（Problems）延续，打印页码 248，承接上一页 p257（Problem 11–15），本页续接 Problem 15*(b) Solution，然后是 Problem 16*。**</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（续）。** **(b)** We first compute the CDF of $X$ and then differentiate to obtain its PDF. We have for $-\pi/2 \le x \le \pi/2$,

```math
P(X \le x) = P(\tan^{-1} Y \le x) = P(Y \le \tan x) = F_Y(\tan x),
```

and by differentiating, we obtain

```math
f_X(x) = f_Y(\tan x) \frac{d}{dx} \tan x = \frac{1}{\pi(1 + \tan^2 x)} \cdot \sec^2 x = \frac{1}{\pi},
```

where the last equality follows from the identity $1 + \tan^2 x = \sec^2 x$.

For $x < -\pi/2$, we have $P(X \le x) = 0$, and for $\pi/2 < x$, we have $P(X \le x) = 1$. Taking the derivative of the CDF $P(X \le x)$, we find that $X$ is uniformly distributed on the interval $[-\pi/2, \pi/2]$.

> **Note :** An interesting property of the Cauchy random variable is that it satisfies

```math
E[|Y|] = \infty,
```

>(此处变量记号 $Y$ 承接上一页 Problem 15 的柯西随机变量。) as can be easily verified. As a result, the Cauchy random variable does not have a well-defined expected value, despite the symmetry of its PDF around 0; see the footnote in Section 3.1 on the definition of the expected value of a continuous random variable.

> <span style="color:#7f8c8d;">[note] Note（译者注，置于 Solution 之后）:</span> 上述原文 Note（柯西随机变量期望绝对值等于无穷大、虽 PDF 关于 0 对称却仍无良定义期望）为 Problem 15* 英文 Solution 的原生结尾，保留英文原文。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 16 $^{*}$  两个独立正态随机变量的极坐标（The polar coordinates of two independent normal random variables）</span>

Problem 16. * The polar coordinates of two independent normal random
variables. Let $X$ and $Y$ be independent standard normal random variables. The pair $(X, Y)$ can be described in polar coordinates in terms of random variables $R \ge 0$ and $\Theta \in [0, 2\pi]$, so that

```math
\begin{aligned}
X &= R \cos \Theta, \\
Y &= R \sin \Theta.
\end{aligned}
```

(a) Show that $\Theta$ is uniformly distributed in $[0, 2\pi]$, that $R$ has the PDF

```math
f_R(r) = r e^{-r^2/2}, \qquad r \ge 0,
```

and that $R$ and $\Theta$ are independent. (The random variable $R$ is said to have a Rayleigh distribution.)

(b) Show that $R^2$ has an exponential distribution with parameter $1/2$.

> <span style="color:#7f8c8d;">Note:</span> Using the results in this problem, we see that samples of a normal random variable can be generated using samples of independent uniform and exponential random variables.

<span style="color:#2471a3;">**[solution]**</span> **Solution.** (a) The joint PDF of $X$ and $Y$ is

```math
f_{X,Y}(x, y) = \frac{1}{2\pi} e^{-(x^2 + y^2)/2}.
```

We first find the joint CDF（cumulative distribution function） of $R$ and $\Theta$. Fix some $r > 0$ and some $\theta \in [0, 2\pi]$, and let $A$ be the set of points $(x, y)$ whose polar coordinates $(\rho, \phi)$ satisfy $0 \le \rho \le r$ and $0 \le \phi \le \theta$; note that the set $A$ is a sector of a circle of radius $r$, with angle $\theta$. We have

```math
F_{R,\Theta}(r, \theta) = P(R \le r, \Theta \le \theta) = p\left((X, Y) \in A\right).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 页尾截断]：joint CDF 计算式到 $p\!\left((X, Y) \in A\right)$ 结束后即到翻页处，内容续接下一页。</span>
<!-- ===== PDF p259 ===== -->
<span style="color:#7f8c8d;">**第 4 章 Further Topics on Random Variables（随机变量的进一步专题）—— 习题区（Problems）延续，打印页码 249，承接上一页 p258（Problem 16\* 题干与 Solution 开头），此页续完 Problem 16\* 的英文 Solution，随后进入 §4.2 的 Problem 17–19。**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 16$\ ^{*}$（续）——两个独立正态随机变量的极坐标（The polar coordinates of two independent normal random variables）**</span>

> <span style="color:#7f8c8d;">承接上一页 p258：Problem 16\* 的题干与 Solution（a）前段已在前页给出（设 $X,Y$ 为相互独立的标准正态随机变量，极坐标 $X = R\cos\Theta$、$Y = R\sin\Theta$，其中 $R \ge 0$、$\Theta \in [0, 2\pi]$）。本页续接其 Solution 的极坐标联合 CDF 求导及其后推导。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（续）。** ...where the last equality is obtained by transforming to polar coordinates. We then differentiate, to find that

```math
f_{R,\Theta}(r, \theta) = \frac{\partial^2}{\partial r\, \partial\theta}\, F_{R,\Theta}(r, \theta) = \frac{1}{2\pi}\, r\, e^{-r^2/2}, \qquad r \ge 0,\ \theta \in [0, 2\pi].
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏]：上方极坐标联合 PDF $f_{R,\Theta}(r,\theta)$ 的式子被 OCR 打碎，仅残余「!R.e (r. 8) _ a2 FR .e / ara8 」等碎片，此处按 Fubini 对上一页 joint CDF $F_{R,\Theta}(r,\theta)$ 混合求偏导还原为等价规范形式；分量的真实朝向（系数、指数）以上式为准。</span>

Thus,

```math
f_R(r) = \int_0^{2\pi} f_{R,\Theta}(r, \theta)\, d\theta = r\, e^{-r^2/2}, \qquad r \ge 0.
```

Furthermore,

```math
f_{\Theta \mid R}(\theta \mid r) = \frac{f_{R,\Theta}(r, \theta)}{f_R(r)} = \frac{1}{2\pi}, \qquad \theta \in [0, 2\pi].
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏]：后一行 $f_{\Theta \mid R}(\theta \mid r)$ 的条件 PDF 式子在 OCR 中断行被打散（残片形如「!el R (8 I r ) = 2 7f / fR (r)」），此处按 $f_{R,\Theta}$ 与 $f_R$ 的商合并且归一化为 $1/(2\pi)$；以如上方为准。</span>

Since the conditional PDF $f_{\Theta \mid R}$ of $\Theta$ is unaffected by the value of the conditioning variable $R$, it follows that it is also equal to the unconditional PDF $f_{\Theta}$. In particular, $f_{R,\Theta}(r, \theta) = f_R(r)\, f_{\Theta}(\theta)$, so that $R$ and $\Theta$ are independent.

**(b)** Let $t \ge 0$. We have

```math
P(R^2 \ge t) = P(R \ge \sqrt{t}) = \int_{\sqrt{t}}^{\infty} r\, e^{-r^2/2}\, dr = \int_{t/2}^{\infty} e^{-u}\, du = e^{-t/2},
```

where we have used the change of variables $u = r^2 / 2$. By differentiating, we obtain

```math
f_{R^2}(t) = \frac{1}{2}\, e^{-t/2}, \qquad t \ge 0.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏]：末尾一行「$f_{R^2}(t) = \tfrac{1}{2}e^{-t/2}$」在 OCR 中被断行（残片为「!R2 (t) - !2 e - t/2 , t 2: 0.」，$\,1/2\,$ 的分数被吞、等号被误读为减号），此处还原为标准指数 PDF 形式。</span>

> <span style="color:#7f8c8d;">说明：Problem 16\* 为带星号题，按其英文原件 Solution 保留英文原文（仅「Solution（解答）」标签给出中文）。其结尾落款「Problem 16\* 解答完毕」，翻页进入下一节习题。</span>

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**Section 4.2　协方差与相关（Covariance and Correlation）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 17.**</span> Suppose that $X$ and $Y$ are random variables with the same variance. Show that $XY$ and $X+Y$ are uncorrelated.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 18.**</span> Consider four random variables $W$, $X$, $Y$, $Z$, with

```math
E[W] = E[X] = E[Y] = E[Z] = 0,
```

```math
\operatorname{var}(W) = \operatorname{var}(X) = \operatorname{var}(Y) = \operatorname{var}(Z) = 1,
```

and assume that $W$, $X$, $Y$, $Z$ are pairwise uncorrelated. Find the correlation coefficients $\rho(R, S)$ and $\rho(R, T)$, where $R = W + X$, $S = X + Y$, and $T = Y + Z$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏]：第一行「$W$, $X$, $Y$, $Z$」中 $W$ 被 OCR 误读为「\IF」（斜杠 I 与 F），按原书还原为 $W$；下方 $E[W] = E[X] = E[Y] = E[Z] = 0$ 各恒等关系在 OCR 中被打成竖排碎片，已按连续等号合并。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 19.**</span> Suppose that a random variable $X$ satisfies

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏/跨行丢失]：原文在「satisfies（满足）」与「and let $Y = a + bX + cX^2$」之间应有一段对 $X$ 的数个矩条件的定义，该条件行在换页/扫描时丢失（OCR 中「satisfies」后直接跳到「and let」」，此处不臆造具体数值，需回查原书以补全）。</span>

and let

```math
Y = a + bX + cX^2.
```

Find the correlation coefficient $\rho(X, Y)$.
<!-- ===== PDF p260 ===== -->
<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）**</span> — 习题区续接（Problems，续）；印页号 250，承接前页习题编号序列。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 20\*.（Schwarz inequality，施瓦茨不等式）**</span>

Show that for any random variables $X$ and $Y$, we have

```math
\left( E[XY] \right)^2 \le E\left[ X^2 \right]\, E\left[ Y^2 \right].
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 习题题干的待证不等式在 OCR 中被切断（页文在 "we have" 后即跳转 Solution），上式 $ \left( E[XY] \right)^2 \le E[ X^2 ]\, E[ Y^2 ] $ 由本页尾部 Solution 的推导结论还原，为标准施瓦茨不等式（Schwarz inequality）的陈述。若需最严格原文请回查原书页 250。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution.（解答）**

We may assume that $E[Y^2] \ne 0$; otherwise, we have $Y = 0$ with probability $1$, and hence $E[XY] = 0$, so the inequality holds. We have

```math
0
\le E\left[ \left( X - \frac{E[XY]}{E[Y^2]}\, Y \right)^2 \right]
= E\left[ X^2 - 2\,\frac{E[XY]}{E[Y^2]}\, XY + \left( \frac{E[XY]}{E[Y^2]} \right)^2 Y^2 \right]
```

```math
= E[ X^2 ] - 2\,\frac{E[XY]}{E[Y^2]}\, E[XY] + \left( \frac{E[XY]}{E[Y^2]} \right)^2 E[ Y^2 ]
= E[ X^2 ] - \frac{\left( E[XY] \right)^2}{E[Y^2]},
```

```math
\left( E[XY] \right)^2 \le E[ X^2 ]\, E[ Y^2 ].
```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 21\*.（Correlation coefficient，相关系数）**</span>

Consider the correlation coefficient

```math
\rho(X, Y) = \frac{\operatorname{cov}(X, Y)}{\sqrt{\operatorname{var}(X)\,\operatorname{var}(Y)}}
```

of two random variables $X$ and $Y$ that have positive variances. Show that:

**(a)** $|\rho(X, Y)| \le 1$. Hint: Use the Schwarz inequality from the preceding problem.

**(b)** If $Y - E[Y]$ is a positive (or negative) multiple of $X - E[X]$, then $\rho(X, Y) = 1$ [or $\rho(X, Y) = -1$, respectively].

**(c)** If $\rho(X, Y) = 1$ [or $\rho(X, Y) = -1$], then, with probability $1$, $Y - E[Y]$ is a positive (or negative, respectively) multiple of $X - E[X]$.

<span style="color:#2471a3;">**[solution]**</span> **Solution.（解答）**

**(a)** Let $\tilde X = X - E[X]$ and $\tilde Y = Y - E[Y]$. Using the Schwarz inequality, we get

```math
\left( \rho(X, Y) \right)^2
= \frac{\left( E[ \tilde X \tilde Y ] \right)^2}{E[ \tilde X^2 ]\, E[ \tilde Y^2 ]}
\le 1,
```

and hence $|\rho(X, Y)| \le 1$.

**(b)** If $\tilde Y = a \tilde X$, then

```math
\rho(X, Y)
= \frac{E[ \tilde X \, a \tilde X ]}{\sqrt{ E[ \tilde X^2 ]\, E[ (a \tilde X)^2 ] }}
= \frac{a\, E[ \tilde X^2 ]}{|a|\, E[ \tilde X^2 ]}
= \frac{a}{|a|},
```

> <span style="color:#7f8c8d;">[跨页续接] 本页止于 Problem 21 (b) 的中间推导（OCR 在本页结尾显示 $\frac{a}{|a|}$ 与残缺的 `.5:..`），(b) 的结论（$\rho(X,Y) = a/|a|$，即取 $a$ 的符号）及 (c) 小节翻页续接，见下一页。</span>
<!-- ===== PDF p261 ===== -->

<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）——习题区（Problems，续）**</span>

<span style="color:#7f8c8d;">承接上一页：本页开头为某道习题解答（solution）的尾部，即其小问 **(c)** 的收束部分。该题号起于上一页，本页不再标出题号；推导中引用了 **Problem 20** 的解答结果，涉及随机变量 $X$、$Y$ 与其相关系数 $\rho(X,Y)$。</span>

**(c)** 若 $(\rho(X,Y))^2 = 1$，则沿用 Problem 20 解答中的计算方法可得

```math
E\!\left[\left(X - \frac{E[XY]}{E[Y^2]}\,Y\right)^2\right]
= E[X^2] - \frac{\bigl(E[XY]\bigr)^2}{E[Y^2]}
= E[X^2]\Bigl(1 - \bigl(\rho(X,Y)\bigr)^2\Bigr)
= 0.
```

因此，以概率 $1$，随机变量 $X - \frac{E[XY]}{E[Y^2]}\,Y$ 等于零。由此可知，以概率 $1$ 有

```math
X = \frac{E[XY]}{E[Y^2]}\,Y,
```

即 $X$ 与 $Y$ 的常数比值（constant ratio）的符号由 $\rho(X,Y)$ 的符号决定。

---

<span style="color:#c0392b;">**SECTION 4.3　条件期望与方差的再访（Conditional Expectation and Variance Revisited）**</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 22（凯利策略 Kelly strategy——n 次赌博后的期望财富）**</span>

Consider a gambler who at each gamble either wins or loses his bet with probabilities $p$ and $1 - p$, independent of earlier gambles. When $p > 1/2$, a popular gambling system, known as the Kelly strategy, is to always bet the fraction $2p - 1$ of the current fortune. Compute the expected fortune after $n$ gambles, starting with $x$ units and employing the Kelly strategy.

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 题干中「probabilities $p$ and $1-p$」「When $p > 1/2$」「the fraction $2p-1$」在 OCR 中被拆分到多个碎行（如出示 "probabilities p and p"、"the fraction 2p" 与孤立 "-1"），此处按原文语义与后续推导还原为上述规范形式；请以原书为准。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 23（Pat 与 Nat 约会）**</span>

Pat and Nat are dating, and all of their dates are scheduled to start at 9 p.m. Nat always arrives promptly at 9 p.m. Pat is highly disorganized and arrives at a time that is uniformly distributed between 8 p.m. and 10 p.m. Let $X$ be the time in hours between 8 p.m. and the time when Pat arrives. If Pat arrives before 9 p.m., their date will last exactly 3 hours. If Pat arrives after 9 p.m., their date will last for a time that is uniformly distributed between 0 and $3 - X$ hours. The date starts at the time they meet. Nat gets irritated when Pat is late and will end the relationship after the second date on which Pat is late by more than 45 minutes. All dates are independent of any other dates.

(a) What is the expected number of hours Nat waits for Pat to arrive?

(b) What is the expected duration of any particular date?

(c) What is the expected number of dates they will have before breaking up?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 24（退休教授在办公室逗留的时间）**</span>

A retired professor comes to the office at a time which is uniformly distributed between 9 a.m. and 1 p.m., performs a single task, and leaves when the task is completed. The duration of the task is exponentially distributed with parameter $\lambda(y) = \dfrac{1}{5 - y}$, where $y$ is the length of the time interval between 9 a.m. and the time of his arrival.

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 参数 $\lambda(y) = 1/(5 - y)$ 在 OCR 中被拆成孤立分行的 "\$,X(y) = ( 5 - y)" 与 "1/"；本式已按语义还原为 $\lambda(y) = \dfrac{1}{5 - y}$，最终式请以原书为准。</span>
<!-- ===== PDF p262 ===== -->
> <span style="color:#7f8c8d;">第 4 章 Further Topics on Random Variables（随机变量的进一步专题）——习题区（Problems）中段，承接 p261。本页先续接 Problem 24 的 (a)(b)(c) 小问，随后是带 * 的 Problem 25 与 Problem 26 及其英文 Solution（Solutions 按规范保持英文原文）。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 24（续）**——退休教授处理单一任务：条件期望、完成时刻与全期望定理</span>

> <span style="color:#7f8c8d;">承接上一页（p261）的题干：一位退休教授在上午 9 点到下午 1 点之间均匀随机地到办公室，做单一任务，任务完成后离开。任务持续时间服从参数 $\lambda(y) = 1/(5 - y)$ 的指数分布，其中 $y$ 是上午 9 点到其到达时刻之间的时间区间长度。本页续接下列小问。</span>

(a) What is the expected amount of time that the professor devotes to the task?

(b) What is the expected time at which the task is completed?

(c) The professor has a Ph.D. student who on a given day comes to see him at a time that is uniformly distributed between 9 a.m. and 5 p.m. If the student does not find the professor, he leaves and does not return. If he finds the professor, he spends an amount of time that is uniformly distributed between 0 and 1 hour. The professor will spend the same total amount of time on his task regardless of whether he is interrupted by the student. What is the expected amount of time that the professor will spend with the student and what is the expected time at which he will leave his office?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 25\*——**条件期望算子可将给定另一随机变量 $Y$ 时的函数 $g(Y)$ 提出期望符号之外</span>

**Problem 25.\*** Show that for a discrete or continuous random variable $X$, and any function $g(Y)$ of another random variable $Y$, we have $E[Xg(Y) \mid Y] = g(Y)\,E[X \mid Y]$.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

Assume that $X$ is continuous. From a version of the expected value rule for conditional expectations given in Chapter 3, we have

```math
E[Xg(Y) \mid Y = y] = \int_{-\infty}^{\infty} x\, g(y)\, f_{X \mid Y}(x \mid y)\, dx
= g(y) \int_{-\infty}^{\infty} x\, f_{X \mid Y}(x \mid y)\, dx
= g(y)\, E[X \mid Y = y].
```

因为当给定 $Y = y$ 时，$g(y)$ 在关于 $x$ 的积分中是常数，故可提到积分号与条件期望符号之外。This shows that the realized values $E[Xg(Y) \mid Y = y]$ and $g(y)E[X \mid Y = y]$ of the random variables $E[Xg(Y) \mid Y]$ and $g(Y)E[X \mid Y]$ are always equal. Hence these two random variables are equal. The proof is similar if $X$ is discrete.

> <span style="color:#7f8c8d;">[原页此处 OCR 轻微碎裂] 上式中的积分出自 $-\infty$ 到 $+\infty$，OCR 将该积分上下限与 $xg(y) f_{X\mid Y}(x \mid y)$ 的行首碎行（如将 $\int_{-\infty}^{\infty}$ 误读为 `1:` 加碎片），此处按标准版本期望规则重构为统一 LaTeX；等式的实质内容与推导顺序与原文一致。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 26\*——**用全方差定理（law of total variance）推 independence 乘积的方差公式</span>

**Problem 26.\*** Let $X$ and $Y$ be independent random variables. Use the law of total variance to show that

```math
\operatorname{var}(XY) = \left(E[X]\right)^2 \operatorname{var}(Y) + \left(E[Y]\right)^2 \operatorname{var}(X) + \operatorname{var}(X)\operatorname{var}(Y).
```

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

Let $Z = XY$. The law of total variance yields

```math
\operatorname{var}(Z)
= \operatorname{var}\!\left(E[Z \mid X]\right) + E\!\left[\operatorname{var}(Z \mid X)\right].
```

We have

```math
E[Z \mid X] = E[XY \mid X] = X\, E[Y],
```

so that

```math
\operatorname{var}\!\left(E[Z \mid X]\right)
= \operatorname{var}\!\left(X E[Y]\right)
= \left(E[Y]\right)^2 \operatorname{var}(X).
```

Furthermore,

```math
\operatorname{var}(Z \mid X)
= \operatorname{var}(XY \mid X)
= X^2 \operatorname{var}(Y \mid X)
= X^2 \operatorname{var}(Y),
```

so that

```math
E\!\left[\operatorname{var}(Z \mid X)\right]
= E\!\left[X^2\right] \operatorname{var}(Y)
= \left(E[X]\right)^2 \operatorname{var}(Y) + \operatorname{var}(X)\operatorname{var}(Y).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 等式中的平方号 ``^2`` 在 OCR 中被打散成独立的行（如 `( E[XJ )` 与 `2` 分行，`]` 被误读为 `J`），此处按本领域标准符号归一化为 $(\cdot)^2$ 与 $\operatorname{var}(\cdot)$；各分量的朝向与原文一致，末尾公式为本题最终结论。</span>
<!-- ===== PDF p263 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problems（习题）**</span> — <span style="color:#7f8c8d;">PDF 印页号 253；第 4 章习题区（Problems）续接，承接 p262 的 Problem 26，继续 Problem 27。</span>

> <span style="color:#7f8c8d;">承接上一页 Problem 26 的 Solution 末尾：对独立随机变量的积 $XY$ 应用全期望与方差分解，综合前述关系可得其方差公式「Combining the preceding relations, we obtain …」，故本页首页为该题的英文解答收尾（续）。</span>

Combining the preceding relations, we obtain

```math
\operatorname{var}(XY) = \left(E[X]\right)^2\operatorname{var}(Y) + \left(E[Y]\right)^2\operatorname{var}(X) + \operatorname{var}(X)\operatorname{var}(Y).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 首行公式各因子的上标（如 $(E[X])^2$）在 OCR 中被拆散为独立行（源文特地把 $^2$ 幂次与符号分行），此处按标准方差恒等式合并还原为该行。该行属承接上一页 Problem 26 解答的收尾，故标题沿用「续」。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 27\*（抛掷 $n$ 次偏置硬币，头部概率随机的随机变量 $Q$ 决定）**</span>

We toss $n$ times a biased coin whose probability of heads, denoted by $q$, is the value of a random variable $Q$ with given mean $\mu$ and positive variance $\sigma^2$. Let $X_i$ be a Bernoulli random variable that models the outcome of the $i$th toss (i.e., $X_i = 1$ if the $i$th toss is a head). We assume that $X_1, \ldots, X_n$ are conditionally independent, given $Q = q$. Let $X$ be the number of heads obtained in the $n$ tosses.

(a) Use the law of iterated expectations to find $E[X_1]$ and $E[X]$.

(b) Find $\operatorname{cov}(X_i, X_j)$. Are $X_1, \ldots, X_n$ independent?

(c) Use the law of total variance to find $\operatorname{var}(X)$. Verify your answer using the covariance result of part (b).

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

**(a)** We have, from the law of iterated expectations and the fact $E[X_i \mid Q] = Q$,

```math
E[X_i] = E\!\left[E[X_i \mid Q]\right] = E[Q] = \mu .
```

Since $X = X_1 + \cdots + X_n$, it follows that

```math
E[X] = E[X_1] + \cdots + E[X_n] = n\mu .
```

**(b)** We have, for $i \neq j$, using the conditional independence assumption,

```math
E[X_i X_j \mid Q] = E[X_i \mid Q]\,E[X_j \mid Q] = Q^2 ,
```

and

```math
\operatorname{cov}(X_i, X_j) = E[X_i X_j] - E[X_i]\,E[X_j] = E[Q^2] - \mu^2 = \sigma^2 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (b) 中「We have, for $i\neq j$ …」「and」「Thus,」三处之间夹着的若干中间公式在 OCR 中被清空（源文这几处留白），此处按条件独立的前提还原为 $E[X_i X_j \mid Q] = Q^2$ 与协方差分解的上述两式；最终 $\operatorname{cov}(X_i, X_j) = \sigma^2 > 0$ 与下文「not independent」的判定一致。</span>

Thus,

```math
\operatorname{cov}(X_i, X_j) = \sigma^2 > 0 .
```

Since $\operatorname{cov}(X_i, X_j) > 0$, $X_1, \ldots, X_n$ are **not** independent.

Also, for $i = j$, using the observation that $X_i^2 = X_i$,

```math
\operatorname{var}(X_i) = E[X_i^2] - \left(E[X_i]\right)^2
= E[X_i] - \left(E[X_i]\right)^2
= \mu - \mu^2 .
```

<span style="color:#7f8c8d;">**本页止于此（第 263 页末尾），Problem 27 的解答到 $\operatorname{var}(X_i) = \mu - \mu^2$ 为止；部分 (c) 及其余内容是否存在需视下一页继续。</span>
<!-- ===== PDF p264 ===== -->
<span style="color:#7f8c8d;">**第 4 章 Further Topics on Random Variables（随机变量的进一步专题）—— 习题区（Problems）续接**（PDF 页 254，承接前一页 Problem 编号序列）。</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#c0392b;">**Solution（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：设 $Q$ 是取值于 $[0,1]$ 的随机变量（均值为 $\mu$、方差为 $\sigma^2$），给定 $Q$ 时 $X_1, \ldots, X_n$ 条件独立，且每项 $X_i$ 的条件均值 $E[X_i \mid Q] = Q$、条件方差 $\operatorname{var}(X_i \mid Q) = Q(1-Q)$，$X = X_1 + \cdots + X_n$。此页开头续接该解法的部分 (c)。</span>

**(c)** Using the law of total variance, and the conditional independence of $X_1, \ldots, X_n$, we have

```math
\operatorname{var}(X) = E\big[\operatorname{var}(X \mid Q)\big] + \operatorname{var}\big(E[X \mid Q]\big)
```

```math
= E\big[\operatorname{var}(X_1 + \cdots + X_n \mid Q)\big] + \operatorname{var}\big(E[X_1 + \cdots + X_n \mid Q]\big)
```

```math
= E[nQ(1-Q)] + \operatorname{var}(nQ)
```

```math
= n E[Q - Q^2] + n^2 \operatorname{var}(Q)
```

```math
= n(\mu - \mu^2 - \sigma^2) + n^2 \sigma^2
```

```math
= n(\mu - \mu^2) + n(n-1)\sigma^2 .
```

To verify the result using the covariance formulas of part (b), we write

```math
\operatorname{var}(X) = \operatorname{var}(X_1 + \cdots + X_n)
```

```math
= \sum_{i=1}^{n} \operatorname{var}(X_i) + \sum_{\{(i,j) \mid i \neq j\}} \operatorname{cov}(X_i, X_j)
```

```math
= n\operatorname{var}(X_1) + n(n-1)\operatorname{cov}(X_1, X_2)
```

```math
= n(\mu - \mu^2) + n(n-1)\sigma^2 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页顶部为前一页起题的解答尾部：部分与式（如 $\sum_{\{(i,j) \mid i\neq j\}}$ 的下标集、若干幂次角标）被 OCR 打散断行（如 "$n(\mu-\mu^2-\sigma^2)$" 被拆成 "n( J-L - J-L / 2 - 0'2 )"），此处按上下文将 $Q$ 的均值为 $\mu$、方差为 $\sigma^2$ 还原为标准推导，最终结果 $n(\mu-\mu^2)+n(n-1)\sigma^2$ 为两种方法一致收敛。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 28.\* The Bivariate Normal PDF（二元正态概率密度函数）**</span>

The (zero mean) bivariate normal PDF is of the form

```math
f_{X,Y}(x, y) = c\, e^{-q(x,y)},
```

where the exponent term $q(x,y)$ is a quadratic function of $x$ and $y$,

```math
q(x,y) = \frac{1}{2(1-\rho^2)}\left( \frac{x^2}{\sigma_x^2} - 2\rho \frac{xy}{\sigma_x \sigma_y} + \frac{y^2}{\sigma_y^2} \right),
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原页中 $q(x,y)$ 的具体式子因版心 OCR 破裂而未捕获文字（仅见左侧函数名 "q(x, y) =" ，其后直接跳到衔接句 "… and c is a normalizing constant"）。为使前文参数 $\sigma_x,\ \sigma_y,\ \rho,\ c$ 与后续 (a)–(g) 小问自洽，此处按该书标准的（零均值）二元正态指数形式还原；如需严格原文请回查原书 PDF 页 254。</span>

$\sigma_x$ and $\sigma_y$ are positive constants, $\rho$ is a constant that satisfies $-1 < \rho < 1$, and $c$ is a normalizing constant.

**(a)** By completing the square, rewrite $q(x,y)$ in the form $(\alpha x - \beta y)^2 + \gamma y^2$ for some constants $\alpha$, $\beta$, and $\gamma$.

**(b)** Show that $X$ and $Y$ are zero mean normal random variables with variance $\sigma_x^2$ and $\sigma_y^2$, respectively.

**(c)** Find the normalizing constant $c$.

**(d)** Show that the conditional PDF of $X$ given that $Y = y$ is normal, and identify its conditional mean and variance.

**(e)** Show that the correlation coefficient of $X$ and $Y$ is equal to $\rho$.

**(f)** Show that $X$ and $Y$ are independent if and only if they are uncorrelated.

**(g)** Show that the estimation error $E[X \mid Y] - X$ is normal with mean zero and variance $(1 - \rho^2)\sigma_x^2$, and is independent from $Y$.

> <span style="color:#7f8c8d;">[题号与角标说明] 原页小问 (b) 中方差书写 "$0';$ 与 $O'_{\Delta}$"、(e) 相关系数 "$p$"、(g) 方差 "$(1 - /)0';$" 均为 OCR 对 $\sigma_x^2,\ \sigma_y^2,\ \rho,\ \sigma_x^2$ 的误读/丢失，此处统一恢复为标准记号 $(1-\rho^2)\sigma_x^2$ 等；本页题号 Problem 28 为原文编号。</span>
<!-- ===== PDF p265 ===== -->

> <span style="color:#7f8c8d;">第 4 章 Further Topics on Random Variables（随机变量的进一步专题）—— 习题区（Problems），印页号 255。本页为 **Problem 28\*（The Bivariate Normal PDF，二元正态 PDF）** 的英文 Solution，承接前页 p264 的问题陈述（(a)–(g) 已在 p264 给出）。本页覆盖 Solution 的 (a)、(b)、(c) 与 (d) 之开头（给出了条件密度表达式，其均值/方差的识别及 (e)–(g) 续接下一页）。带 `*` 题的 Solution 保持英文，仅标签标注中文。</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#c0392b;">**Problem 28\* —— The Bivariate Normal PDF 的 Solution（续）**</span>

**Solution.**

**(a)** We can rewrite $q(x, y)$ in the form

```math
q(x, y) = q_1(x, y) + q_2(y),
```

where

```math
q_1(x, y) = \frac{\left(x - \rho\,\sigma_x\,y/\sigma_y\right)^2}{2\left(1 - \rho^2\right)\sigma_x^2},
\qquad
q_2(y) = \frac{y^2}{2\,\sigma_y^2}.
```

> <span style="color:#7f8c8d;">[OCR 校正] 原文此处的 $q_1(x,y)$ 分式被 OCR 打散成碎片（残存 `d`、`2(1-p²)`、`(x - pY)²`、`σx`、`σy` 等孤立字符），此处按二元正态二次型的标准配方法补全为上述规范式；真实朝向以 p266（Solution (a) 之末）为准，若需严格原文请回查原书页 255。</span>

**(b)** We have

```math
f_Y(y) \;=\; c\, e^{-q_2(y)} \int_{-\infty}^{\infty} e^{-q_1(x, y)}\, dx,
```

and, using the change of variables

```math
z = \frac{x - \rho\,\sigma_x\,y/\sigma_y}{\sigma_x\sqrt{1 - \rho^2}},
```

we obtain

```math
\int_{-\infty}^{\infty} e^{-q_1(x, y)}\, dx \;=\; \sqrt{2\pi\left(1 - \rho^2\right)}\,\sigma_x.
```

Thus,

```math
f_Y(y) \;=\; c\,\sigma_x\,\sqrt{2\pi\left(1 - \rho^2\right)}\, e^{-y^2/(2\,\sigma_y^2)}.
```

We recognize this as a normal PDF with mean zero and variance $\sigma_y^2$. The result for the random variable $X$ follows by symmetry.

> <span style="color:#7f8c8d;">[OCR 校正] 原文这一行的常数因子与指数被 OCR 截断为 `fy(y) = cax Jl-p2 ... e^{-y/2(...)}`，上值按偏边际积分为 $\sqrt{2\pi(1-\rho^2)}\,\sigma_x$ 补全；真实因子以原书页 255 为准。</span>

**(c)** The normalizing constant for the PDF of $Y$ must be equal to $1/(\sqrt{2\pi}\,\sigma_y)$. It follows that

```math
c\,\sigma_x\,\sqrt{2\pi\left(1 - \rho^2\right)} \;=\; \frac{1}{\sqrt{2\pi}\,\sigma_y},
```

which implies that

```math
c \;=\; \frac{1}{2\pi\,\sigma_x\,\sigma_y\,\sqrt{1 - \rho^2}}.
```

**(d)** Since

```math
f_{X,Y}(x, y) = \frac{1}{2\pi\,\sigma_x\,\sigma_y\,\sqrt{1 - \rho^2}}\; e^{-q_1(x, y)}\, e^{-q_2(y)},
```

and $f_Y(y)$ is as in part (b), we obtain

```math
f_{X \mid Y}(x \mid y)
= \frac{f_{X,Y}(x, y)}{f_Y(y)}
= \frac{1}{\sqrt{2\pi}\,\sigma_x\,\sqrt{1 - \rho^2}}
\; \exp\!\left\{ -\frac{\left(x - \rho\,\sigma_x\,y/\sigma_y\right)^2}{2\,\sigma_x^2\left(1 - \rho^2\right)} \right\}.
```

> <span style="color:#7f8c8d;">本页结束于此条件密度表达式；由该正态形式立即可识别其条件均值为 $\rho\,\sigma_x\,y/\sigma_y$、条件方差为 $\sigma_x^2(1-\rho^2)$，(d) 的显式识别陈述及 (e)(f)(g) 续接下一页 p266。</span>
<!-- ===== PDF p266 ===== -->

> <span style="color:#7f8c8d;">承接上一页：本页顶部为上一页某带 \* 习题英文解答（Solution）的末段——涵盖 (d) 小问收尾与 (e)(f)(g) 小问（二元正态 $\rho(\rho,\sigma_x,\sigma_y)$ 的条件期望、协方差/相关系数与估计误差）。题号未在本页给出，依同页其后 Problem 29 为 §4.4 首题推断，此解答应承自前一节末题（推断为 Problem 28\*），故标注「续」；若需最严格题号，请回查原书上一页。</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（续）**</span>

For any fixed $y$, we recognize this as a normal PDF with mean $(\rho\sigma_x/\sigma_y)\,y$ and variance $\sigma_x^2(1-\rho^2)$. In particular, $E[X \mid Y = y] = (\rho\sigma_x/\sigma_y)\,y$ and $E[X \mid Y] = (\rho\sigma_x/\sigma_y)\,Y$.

**(e)** Using the expected value rule and the law of iterated expectations, we have

```math
E[XY] = E\!\left[\, E[XY \mid Y] \,\right] .
```

Since, conditioned on $Y$, the conditional mean of $X$ is $(\rho\sigma_x/\sigma_y)\,Y$, we have $E[XY \mid Y] = Y \cdot (\rho\sigma_x/\sigma_y)\,Y$, so

```math
E[XY] = E\!\left[ Y \cdot \frac{\rho\sigma_x}{\sigma_y} Y \right]
= \frac{\rho\sigma_x}{\sigma_y}\, E[Y^2]
= \frac{\rho\sigma_x}{\sigma_y}\, \sigma_y^2
= \rho\,\sigma_x\sigma_y ,
```

where we used $E[Y^2] = \sigma_y^2$ (because $Y$ has mean zero).

Thus, the correlation coefficient $\rho(X, Y)$ is equal to

```math
\rho(X, Y) = \frac{\operatorname{cov}(X, Y)}{\sigma_x \sigma_y}
= \frac{E[XY]}{\sigma_x \sigma_y}
= \rho .
```

**(f)** If $X$ and $Y$ are uncorrelated, then $\rho = 0$, and the joint PDF satisfies $f_{X,Y}(x, y) = f_X(x)\, f_Y(y)$, so that $X$ and $Y$ are independent. Conversely, if $X$ and $Y$ are independent, then they are automatically uncorrelated.

**(g)** From part (d), conditioned on $Y = y$, $X$ is normal with mean $E[X \mid Y = y]$ and variance $(1-\rho^2)\sigma_x^2$. Therefore, conditioned on $Y = y$, the estimation error $\tilde{X} = X - E[X \mid Y = y]$ is normal with mean zero and variance $(1-\rho^2)\sigma_x^2$, i.e.,

```math
f_{\tilde{X} \mid Y}(\tilde{x} \mid y)
= \frac{1}{\sqrt{2\pi\,(1-\rho^2)}\,\sigma_x}\,
\exp\!\left( -\frac{\tilde{x}^2}{2(1-\rho^2)\sigma_x^2} \right) .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述给 $\tilde{X}$ 的「条件正态 PDF 公式」在原页 OCR 中残缺丢失（源页在第 42 行「normal with mean zero and variance $(1-\rho^2)\sigma_x^2$，i.e.」后公式即断裂、随后直接接「Since the conditional PDF of X does not depend…」），此式为按均值 0、方差 $(1-\rho^2)\sigma_x^2$ 补全的标准正态密度；若需最严格原文请回查原书页 256。</span>

Since the conditional PDF of $\tilde{X}$ does not depend on the value $y$ of $Y$, it follows that $\tilde{X}$ is independent of $Y$, and the above conditional PDF is also the unconditional PDF of $\tilde{X}$.

---

<span style="color:#c0392b;">**§4.4　变换（Transforms）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 29（给定取值与概率的随机变量，求其变换并用之计算前三阶矩）</span>

Let $X$ be a random variable that takes the values $1$, $2$, and $3$, with the following probabilities:

```math
P(X = 1) = \frac12, \qquad P(X = 2) = \frac14, \qquad P(X = 3) = \frac14 .
```

Find the transform associated with $X$ and use it to obtain the first three moments, $E[X]$, $E[X^2]$, $E[X^3]$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 30（求标准正态随机变量的 $E[X^3]$ 与 $E[X^4]$）</span>

Calculate $E[X^3]$ and $E[X^4]$ for a standard normal random variable $X$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 31（求参数为 $\lambda$ 的指数随机变量的第三、四、五阶矩）</span>

Find the third, fourth, and fifth moments of an exponential random variable with parameter $\lambda$.
<!-- ===== PDF p267 ===== -->
<span style="color:#7f8c8d;">**第 4 章　Further Topics on Random Variables（随机变量的进一步专题）—— 习题区（Problems），承接前页 Problem 31，本页从 Problem 32 继续，编号连续。**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 32（非负整值随机变量，两个候选变换表达式，判别何者不可能为变换）</span>

A nonnegative integer-valued random variable $X$ has one of the following two expressions as its transform:

1. $M_X(s) = e^{2(e^{s} - 1)}$.

2. $M_X(s) = e^{2(e^{e^s} - 1)}$.

(a) Explain why one of the two cannot possibly be the transform.

(b) Use the true transform to find $P(X = 0)$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 两个候选变换的记号在 OCR 中被打散：`!vf(8)` / `M(8)` 实为 $M_X(s)$，表达式 1 的 `e 2 ( ee - l _ l )` 与表达式 2 的 `e 2 ( e e s - 1)` 按第 4 章变换常规写法还原为上方两类形式即 Poisson 型 $e^{2(e^s-1)}$ 与含指数套叠的 $e^{2(e^{e^s}-1)}$。若需最严格原文，请回查原书页 257。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 33（由给定变换求连续随机变量的 PDF）</span>

Find the PDF of the continuous random variable $X$ associated with the transform

```math
M(s) = \frac{1}{3}\cdot\frac{2}{2-s} + \frac{2}{3}\cdot\frac{3}{3-s}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 变换式的系数与分母在 OCR 中被打散为竖排碎片（`1/3`、`2/(2-s)`、`2/3`、`3/(3-s)` 分列多行），此处按常见指数分布变换的线性组合形态还原为上方表达式。若需最严格原文，请回查原书页 257。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 34（足球队员罚点球，用卷积计算 PMF 并对照变换印证）</span>

A soccer team has three designated players who take turns striking penalty shots. The $i$th player has probability of success $p_i$, independent of the successes of the other players. Let $X$ be the number of successful penalty shots after each player has had one turn. Use convolution to calculate the PMF of $X$. Confirm your answer by first calculating the transform associated with $X$ and then obtaining the PMF from the transform.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中「probability of success $p_i$」的概率记号被 OCR 误读为 `PI`，按上下文还原为 $p_i$。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 35（由分式变换求 $E[X]$、$p_X(1)$ 与 $E[X \mid X \ne 0]$）</span>

Let $X$ be a random variable that takes nonnegative integer values, and is associated with a transform of the form

```math
M_X(s) = c\,\frac{3 + 4e^{2s} + 2e^{3s}}{3 - e^s},
```

where $c$ is some scalar. Find $E[X]$, $p_X(1)$, and $E[X \mid X \ne 0]$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 变换记号被 OCR 误读为 `A1x`，实为 $M_X(s)$；末小问 `E[X I X 1= 0]` 按上下文还原为 $E[X \mid X \ne 0]$（条件为 $X \neq 0$）。若需最严格原文，请回查原书页 257。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 36（独立随机变量组合的变换）</span>

Let $X$, $Y$, and $Z$ be independent random variables, where $X$ is Bernoulli with parameter $1/3$, $Y$ is exponential with parameter $2$, and $Z$ is Poisson with parameter $3$.

(a) Consider the new random variable $U = XY + (1 - X)Z$. Find the transform associated with $U$.

(b) Find the transform associated with $2Z + 3$.

(c) Find the transform associated with $Y + Z$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 37（披萨店：以变换刻画期望的披萨种类数）</span>

A pizza parlor serves $n$ different types of pizza, and is visited by a number $K$ of customers in a given period of time, where $K$ is a nonnegative integer random variable with a known associated transform $M_K(s) = E[e^{sK}]$. Each customer orders a single pizza, with all types of pizza being equally likely, independent of the number of other customers and the types of pizza they order. Give a formula, in terms of $M_K(\cdot)$, for the expected number of different types of pizzas ordered.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 末句「in terms of $M_K(\cdot)$」被 OCR 误读为 `l\1K (')`，按上下文还原为「in terms of $M_K(\cdot)$」。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 38（带星题，非负整值随机变量：$P(X=0)=\lim_{s\to-\infty}M(s)$）</span>

$\ast$ Let $X$ be a discrete random variable taking nonnegative integer values. Let $M(s)$ be the transform associated with $X$.

(a) Show that

```math
P(X = 0) = \lim_{s \to -\infty} M(s).
```

> <span style="color:#7f8c8d;">[跨页截断] 本题 (a) 之后的小问（如 (b)）应续接至下一页，此处仅止于 (a)。（本页 Problem 38 题头标有星号 $\ast$，其英文 Solution 若出现将保持英文，仅标签可中文。）</span>
<!-- ===== PDF p268 ===== -->

<span style="color:#7f8c8d;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）—— 习题区（Problems）续页，印页号 258，承接 p267 的习题编号序列。**</span>

> <span style="color:#7f8c8d;">[本页结构] 页首是上一页 Problem 38 的尾部：取题为「利用变换（transform）求 $P(X=0)$ 与 $P(X=k)$」，本页含其第 (b)、(c) 小问及完整 Solution；Problem 38 的题干第 (a) 小问、题号与是否带 `*` 均位于上一页（p267），本页无法确认。其后开始 Problem 39\*。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 38（续）—— 利用变换（transform）求 $P(X=0)$ 与 $P(X=k)$**</span>

> <span style="color:#7f8c8d;">承接上一页（Prob 38 第 (a) 小问所述内容在 p267，本页从第 (b) 小问续起）。</span>

**(b)** Use part (a) to verify that if $X$ is a binomial random variable with parameters $n$ and $p$, we have $P(X = 0) = (1-p)^{n}$. Furthermore, if $X$ is a Poisson random variable with parameter $\lambda$, we have $P(X = 0) = e^{-\lambda}$.

**(c)** Suppose that $X$ is instead known to take only integer values that are greater than or equal to a given integer $k$. How can we calculate $P(X = k)$ using the transform associated with $X$?

<span style="color:#2471a3;">**[solution]**</span> **Solution.**

**(a)** We have

```math
M(s) = \sum_{k=0}^{\infty} P(X = k)\, e^{k s}.
```

As $s \to -\infty$, all the terms $e^{k s}$ with $k > 0$ tend to $0$, so we obtain $\lim_{s\to -\infty} M(s) = P(X = 0)$.

**(b)** In the case of the binomial, we have from the transform tables
$M(s) = \left(1 - p + p e^{s}\right)^{n}$,
so that $\lim_{s\to -\infty} M(s) = (1-p)^{n}$. In the case of the Poisson, we have
$M(s) = e^{\lambda (e^{s} - 1)}$,
so that $\lim_{s\to -\infty} M(s) = e^{-\lambda}$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 Solution (b) 中二项与泊松变换的显式（$M(s)=(1-p+pe^{s})^{n}$ 与 $M(s)=e^{\lambda(e^{s}-1)}$）被 OCR 丢失，仅残留「…we have from the transform tables」与「so that lim…」字样；上面两项按「from the transform tables」并结合全书变换表补全，数值方向以原书变换表为准。若需最严格原文，请回查原书页 258。</span>

**(c)** The random variable $Y = X - k$ takes only nonnegative integer values and the associated transform is $M_Y(s) = e^{-k s}\, M_X(s)$ (cf. Example 4.25). Since $P(Y = 0) = P(X = k)$, we have from part (a),

```math
P(X = k) = \lim_{s \to -\infty} e^{-k s}\, M_X(s).
```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 39. &#42; 均匀分布随机变量的变换（Transforms associated with uniform random variables）**</span>

**(a)** Find the transform associated with an integer-valued random variable $X$ that is uniformly distributed in the range $\{a,\, a+1,\, \ldots,\, b\}$.

**(b)** Find the transform associated with a continuous random variable $X$ that is uniformly distributed in the range $[a,\, b]$.

<span style="color:#2471a3;">**[solution]**</span> **Solution.**

**(a)** The PMF of $X$ is

```math
p_X(k) =
\begin{cases}
\dfrac{1}{b - a + 1}, & \text{if } k = a,\, a+1,\, \ldots,\, b,\\[4pt]
0, & \text{otherwise}.
\end{cases}
```

The transform is

```math
M(s) = \sum_{k=-\infty}^{\infty} e^{s k}\, p_X(k),
```

> <span style="color:#7f8c8d;">[跨页续接] Problem 39\* 的 Solution (a) 在上式求和之后于本页截断，变换的闭合化简式及第 (b) 小问（连续均匀情形）续接至下一页（p269）。此外，本页上方 (a) 的 PMF 取值 $\tfrac{1}{b-a+1}$（均匀概率质量函数）在 OCR 中被整块丢失，仅残留「if $k = a,a+1,\ldots,b$ / otherwise」；此处按均匀分布定义补全。请回查原书核对。</span>
<!-- ===== PDF p269 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problems（习题）—— 第 4 章 随机变量的进一步专题（Further Topics on Random Variables），习题区续接</span>

> <span style="color:#7f8c8d;">本页承接上一页：页首是某道题 **Solution（解答）** 的收尾段（无新 Problem 标题，其题号在本页 OCR 中不可见，不臆造）。页中起为 **Problem 40**（带 \* 题）。印页号约 259。</span>

---

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#c0392b;">Solution（解答，续）</span>

接着上页的推导，这里给出上下两个小问的变换（transform）$M(s)$ 计算结果。

**(a)** 由定义，对离散型情形先按几何级数求和：

```math
M(s) = E[e^{sX}] = \sum_{k=0}^{b-a} \frac{1}{b-a+1}\, e^{s(a+k)}
= \frac{e^{sa}\left(e^{s(b-a+1)} - 1\right)}{(b-a+1)\left(e^{s} - 1\right)} .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页顶端几行严重碎裂（累加变量/上下限、因子 $1/(b-a+1)$、$e^{sa}$ 等零散字符），上式按可辨认的几何级数求和结构还原；具体上下限与首项请以原书页 259 为准。</span>

**(b)** 我们有

```math
M(s) = E[e^{sX}] = \int_{a}^{b} \frac{e^{sx}}{b-a}\, dx = \frac{e^{sb} - e^{sa}}{s(b-a)} .
```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 40. \*** （变换的有理分式分解与离散型 PMF 反演）</span>

**Problem 40. \*** Suppose that the transform associated with a discrete random variable $X$ has the form

```math
M(s) = \frac{A(e^{s})}{B(e^{s})},
```

where $A(t)$ and $B(t)$ are polynomials of the generic variable $t$. Assume that $A(t)$ and $B(t)$ have no common roots and that the degree of $A(t)$ is smaller than the degree of $B(t)$. Assume also that $B(t)$ has distinct, real, and nonzero roots that have absolute value greater than $1$. Then it can be seen that $M(s)$ can be written in the form

```math
M(s) = \sum_{i=1}^{m} \frac{a_i}{1 - T_i e^{s}},
```

where $1/T_1, \ldots, 1/T_m$ are the roots of $B(t)$ and the $a_i$ are constants that are equal to

```math
a_i = \lim_{s \to \ln(1/T_i)} \bigl(1 - T_i e^{s}\bigr)\, M(s), \qquad i = 1, \ldots, m .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 「can be written in the form」后的待显示公式在原页为空白断行，未 OCR 成形；上面按有理分式部分分式（partial fraction）的标准形式补全（即关于 $e^{s}$ 的 $A/B = \sum a_i/(1-T_i e^{s})$，$a_i$ 为对应留数）。请回查原书页 259 核对。</span>

**(a)** Show that the PMF of $X$ has the form

```math
P(X = k) =
\begin{cases}
\sum_{i=1}^{m} a_i\, T_i^{\,k}, & \text{if } k = 0, 1, \ldots,\\[4pt]
0, & \text{otherwise}.
\end{cases}
```

Note: For large $k$, the PMF of $X$ can be approximated by $a_j T_j^{k}$, where $j$ is the index corresponding to the largest $|T_i|$ (assuming $j$ is unique).

**(b)** Extend the result of part (a) to the case where $M(s) = e^{bs} A(e^{s}) / B(e^{s})$ and $b$ is an integer.

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#c0392b;">Solution（解答）</span>

**Solution.** (a) We have for all $s$ such that $|T_i| e^{s} < 1$

Therefore,

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 带 \* 题 Answer/Solution 自 `for all s such that |T_i| e^{s} < 1` 之后转为零散碎片，本页在其后「Therefore,」处翻页截断，后续内容留待下一页续接。具体推导按（$|T_i|e^s<1$ 时展开 $1/(1-T_i e^s)$ 为几何级数）的思路，以原书页 259–260 为准。</span>
<!-- ===== PDF p270 ===== -->
<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 40*（续）—— 变换为 $A(e^s)/B(e^s)$ 之离散随机变量的 PMF 形式（续）</span>

> <span style="color:#7f8c8d;">承接上一页（PDF p269）：设与一离散随机变量 $X$ 相关联的变换（transform）形如 $M(s) = A(e^s)/B(e^s)$，其中 $A(t)$ 与 $B(t)$ 为通式变量 $t$ 的多项式，$1/r_1,\ldots,1/r_m$ 为 $B(t)$ 的根，$M(s)$ 可写为若干几何变换的线性组合。本页续接该题的 Solution，先收尾 part (a)，再给出 part (b)。</span>

**Solution（续）。** (a) … 及由
的尾部，经反演（inverting）此变换，我们得

```math
P(X = k) = \sum_{i=1}^{m} a_i r_i^{\,k}, \qquad \text{for } k \ge 0,
```

而当 $k < 0$ 时 $P(X=k) = 0$。注意：若系数 $a_i$ 非负，则此 PMF 是若干几何 PMF（geometric PMFs）的混合（mixture）。

(b) 在此情形下，$M(s)$ 对应一个变换为 $A(e^s)/B(e^s)$ 的随机变量平移 $b$ 之后所得（cf. Example 4.25），从而有

```math
P(X = k) =
\begin{cases}
\displaystyle\sum_{i=1}^{m} a_i r_i^{\,k - b}, & \text{if } k = b,\, b+1,\, \ldots, \\[4pt]
0, & \text{otherwise.}
\end{cases}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] part (a) 尾部求和式与 part (b) 的分段式被 OCR 打成碎片（如将 $k \ge 0$ 误读为 ``;::: 0``、把求和下标 $i$ 误读为字母噪声「I: t=l」、把 $r_i^{\,k-b}$ 的打散为「a, rj '- b)」）。上式为按 Problem 40* 题干陈述还原的等价标准式，方向与各分量朝向以本页所述为准；若需严格原文请回查原书页 260。</span>

---

<span style="color:#c0392b;">**SECTION 4.5. Sum of a Random Number of Independent Random Variables（随机个数的独立随机变量之和）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 习题分组小节标题在 OCR 中被误读为「SECTION **4.4**.」，按其下各题（Problem 41–44）均围绕「随机个数的独立随机变量之和」且该主题对应正文 §4.5，故正确应为 **SECTION 4.5**。若需严格原文请回查原书页 260。</span>

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 41（电梯内人数为 Poisson 变量时等待/重量和的变换与期望）</span>

At a certain time, the number of people that enter an elevator is a Poisson random variable with parameter $\lambda$. The weight of each person is independent of every other person's weight, and is uniformly distributed between 100 and 200 lbs. Let $X_i$ be the fraction of 100 by which the $i$th person exceeds 100 lbs, e.g., if the $7$th person weighs 175 lbs., then $X_7 = 0.75$. Let $Y$ be the sum of the $X_i$.

(a) Find the transform associated with $Y$.

(b) Use the transform to compute the expected value of $Y$.

(c) Verify your answer to part (b) by using the law of iterated expectations.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 42（随机个数的独立正态随机变量之和并非正态的反例）</span>

Construct an example to show that the sum of a random number of independent normal random variables is not normal (even though a fixed sum is).

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 43（过 4 盏红灯总等待时间的 PDF 与变换）</span>

A motorist goes through 4 lights, each of which is found to be red with probability $1/2$. The waiting times at each light are modeled as independent normal random variables with mean 1 minute and standard deviation $1/2$ minute. Let $X$ be the total waiting time at the red lights.

(a) Use the total probability theorem to find the PDF and the transform associated with $X$, and the probability that $X$ exceeds 4 minutes. Is $X$ normal?

(b) Find the transform associated with $X$ by viewing $X$ as a sum of a random number of random variables.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 44（嵌套和：$Y = X_1 + \cdots + X_N$ 的均值与方差，续至下页）</span>

Consider the calculation of the mean and variance of a sum

```math
Y = X_1 + \cdots + X_N,
```

where $N$ is itself a sum of integer-valued random variables, i.e.,

> <span style="color:#7f8c8d;">Problem 44 题干于本页 (p270) 起始，其「$N$ 本身是若干整数值随机变量之和」的具体设定（$M, K_1, K_2, \ldots, X_1, X_2, \ldots$ 定义及 (a)(b)(c) 各小问）续接至下一页（PDF p271）。</span>
<!-- ===== PDF p271 ===== -->

<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）**</span> — 习题区结尾（Problems，末页，PDF 页码 261）

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 44（续）——随机数个独立随机变量之和的均值与方差（mean and variance of a sum of a random number of independent random variables）**</span>

> <span style="color:#7f8c8d;">承接上一页（p270）：本题研究求和 $Y = X_1 + \cdots + X_N$ 的均值与方差计算，其中 $N$ 本身是整值随机变量之和，即 $N = K_1 + \cdots + K_M$（上一页末尾「i.e.,」之后的等式在此页因分页截断，据 (a) 问所求的 $E[N], \operatorname{var}(N)$ 依赖 $E[M], \operatorname{var}(M)$ 可断定 $N$ 是 $M$ 个 $K_i$ 之和）。</span>

Here $N$, $M$, $K_1$, $K_2$, ..., $X_1$, $X_2$, ... are independent random variables; $N$, $M$, $K_1$, $K_2$, ... are integer-valued and nonnegative, $K_1$, $K_2$, ... are identically distributed with common mean and variance denoted $E[K]$ and $\operatorname{var}(K)$, and $X_1$, $X_2$, ... are identically distributed with common mean and variance denoted $E[X]$ and $\operatorname{var}(X)$.

(a) Derive formulas for $E[N]$ and $\operatorname{var}(N)$ in terms of $E[M]$, $\operatorname{var}(M)$, $E[K]$, $\operatorname{var}(K)$.

(b) Derive formulas for $E[Y]$ and $\operatorname{var}(Y)$ in terms of $E[M]$, $\operatorname{var}(M)$, $E[K]$, $\operatorname{var}(K)$, $E[X]$, $\operatorname{var}(X)$.

(c) A crate contains $M$ cartons, where $M$ is geometrically distributed with parameter $p$. The $i$th carton contains $K_i$ widgets, where $K_i$ is Poisson-distributed with parameter $\mu$. The weight of each widget is exponentially distributed with parameter $\lambda$. All these random variables are independent. Find the expected value and variance of the total weight of a crate.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上面 (a)(b) 问句式中的「$E[M]$, $\operatorname{var}(M)$」在 OCR 中被误读为「E[1H], var(Af)」（字母 $M$ 被打散成 `1H`/`Af`），据相邻相同的 $E[K], \operatorname{var}(K)$ 表达式及页码语义按 $M$ 还原；(c) 问中的两个分布参数原为一处「JL」（应为 $\mu$ 之 OCR 残形）与「>..」（应为 $\lambda$），一并按 $\mu$ 与 $\lambda$ 还原。若需严格原文请回查原书页 261。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 45\*——泊松分布的随机个数之和仍为泊松（用变换证明）**</span>

Use transforms to show that the sum of a Poisson-distributed number of independent identically distributed Bernoulli random variables is Poisson.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）。**（带 * 题的英文 Solution 按规范保持英文，仅标签作中文标注。）

Let $N$ be a Poisson-distributed random variable with parameter $\lambda$. Let $X_i$, $i = 1, \ldots, N$, be independent Bernoulli random variables with parameter $p$, and let $L$ be the corresponding sum. The transform associated with $L$ is found by starting with the transform associated with $N$, which is

```math
M_N(s) = e^{\lambda(e^s - 1)},
```

and replacing each occurrence of $e^s$ by the transform associated with $X_i$, which is

```math
M_X(s) = 1 - p + p e^s.
```

We obtain

```math
\begin{aligned}
M_L(s)
&= e^{\lambda(1 - p + p e^s - 1)} \\
&= e^{\lambda p (e^s - 1)} .
\end{aligned}
```

This is the transform associated with a Poisson random variable with parameter $\lambda p$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Solution 中首个变换原文为「e ^ λ(e^s−1)」（即泊松变换 $M_N(s)=e^{\lambda(e^s-1)}$），其被 $N$ 所对应的变换字样在第 42–44 行被 OCR 打散；下面推导按题意及终式 $M_L(s)=e^{\lambda p(e^s-1)}$ 还原。本页带 * 题的解答按规范保留英文。第 4 章至此结束。</span>
<!-- ===== PDF p272 ===== -->
<span style="color:#2471a3;">**[chapter]**</span> <span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span>

以本质性定理将概率论的研究推向高潮：本章通过**大数定律（law of large numbers）** 与**中心极限定理（central limit theorem）** 揭示，当实验次数足够多时，随机现象中所蕴含的确定性规律。全章目录（Contents）如下：

<span style="color:#2471a3;">**[section]**</span> **目次（Contents）**

- 5.1　Markov and Chebyshev Inequalities（马尔可夫与切比雪夫不等式）……p. 265
- 5.2　The Weak Law of Large Numbers（大数弱定律）……p. 269
- 5.3　Convergence in Probability（依概率收敛）……p. 271
- 5.4　The Central Limit Theorem（中心极限定理）……p. 273
- 5.5　The Strong Law of Large Numbers（大数强定律）……p. 280
- 5.6　Summary and Discussion（小结与讨论）……p. 282
- Problems（习题）……p. 284

> <span style="color:#1e8449;">[章首导言] 本节为第 5 章的章首页与目次页。全章从马尔可夫与切比雪夫不等式出发，进而建立大数弱定律并定义依概率收敛，再引出本章的核心结论——中心极限定理，随后以更强的强大数定律收束，最后给出小结与习题。</span>

> <span style="color:#7f8c8d;">印页号 263</span>
<!-- ===== PDF p273 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span>

在本章中，我们讨论与随机变量序列的渐近行为（asymptotic behavior）有关的一些基本问题。我们的主要背景涉及一个独立同分布随机变量（independent identically distributed random variables）序列 $X_1, X_2, \ldots$，其均值为 $\mu$、方差为 $\sigma^2$。设

```math
S_n = X_1 + \ldots + X_n
```

为其前 $n$ 个之和。极限定理（limit theorems）主要关心当 $n$ 变得很大时 $S_n$ 及相关随机变量的性质。

由于独立性（independence），我们有

```math
\text{var}(S_n) = \text{var}(X_1) + \ldots + \text{var}(X_n) = n\sigma^2 .
```

因此，$S_n$ 的分布随 $n$ 增大而展宽，因而不能有有意义的极限。情况则不同，如果我们转而考虑样本均值（sample mean）

```math
M_n = \frac{X_1 + \ldots + X_n}{n} = \frac{S_n}{n},
```

快速计算可得

```math
E[M_n] = \mu, \qquad \text{var}(M_n) = \frac{\sigma^2}{n} .
```

特别地，$M_n$ 的方差随 $n$ 增大而趋于 $0$，于是 $M_n$ 分布的主体必然非常接近均值 $\mu$。这种现像正是某些大数定律（laws of large numbers）的主题，它们一般断言样本均值 $M_n$（一个随机变量）在精确的意义上收敛到真实均值 $\mu$（一个数）。这些定律为把期望 $E[X_1] = \mu$ 松散地解释为从 $X$ 的分布中随机抽取的 $x$ 的大量独立样本的平均值，提供了数学基础。

我们还将考虑一个介于 $S_n$ 与 $M_n$ 之间的量。我们先把 $S_n$ 减去 $n\mu$，得到零均值随机变量 $S_n - n\mu$，再除以 $\sigma\sqrt{n}$，从而构成随机变量

```math
Z_n = \frac{S_n - n\mu}{\sigma\sqrt{n}} .
```

可以看出

```math
E[Z_n] = 0, \qquad \text{var}(Z_n) = 1 .
```

由于 $Z_n$ 的均值与方差随 $n$ 增大保持不变，它的分布既不展宽、也不收缩为一点。中心极限定理（central limit theorem）关心的是 $Z_n$ 分布的渐近形状，并断言它趋于标准正态分布（standard normal distribution）。
<!-- ===== PDF p274 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — §5.1 马尔可夫与切比雪夫不等式（Markov and Chebyshev Inequalities），正文续页

> <span style="color:#7f8c8d;">承接上一页（本次作业 PDF p273）：本页先续完第 5 章开篇引言「极限定理的用途」的三点说明（a）（b）（c），随后进入 §5.1 正文，故标注「§5.1（续）」。</span>

**极限定理（limit theorems）之所以有用，有以下几个方面的原因：**

(a) 从概念上讲，它们为期望（以及概率）提供了一种基于长序列同分布独立实验的解释。

(b) 它们允许我们对诸如 $S_n$ 之类随机变量的性质进行近似分析。这与精确分析（exact analysis）形成了对比——后者需要 $S_n$ 的 PMF 或 PDF 的公式，而当 $n$ 很大时，这是一项复杂而繁琐的（complicated and tedious）工作。

(c) 在面对大型数据集时，它们在推断（inference）和统计学（statistics）中发挥着重要作用。

---

<span style="color:#c0392b;">**§5.1　马尔可夫与切比雪夫不等式（Markov and Chebyshev Inequalities）**</span>

在本节中，我们推导若干重要的不等式（inequality）。这些不等式利用随机变量的均值（mean）以及可能要用的方差（variance），来得出关于某些事件概率的结论。它们主要适用于这样的情形：随机变量 $X$ 的均值和方差的精确值或上下界易于计算，但 $X$ 的分布要么无法获得，要么很难计算。

我们首先给出**马尔可夫不等式（Markov inequality）**。粗略地说，它断言：如果一个非负随机变量具有很小的均值，那么它取值很大的概率也必然很小。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**马尔可夫不等式（Markov Inequality）**</span>

如果一个随机变量 $X$ 只能取非负值，那么对一切 $a > 0$ 有

```math
P(X \ge a) \le \frac{E[X]}{a} .
```

> <span style="color:#7f8c8d;">[原页 OCR 碎裂处] 原书陈述处的式子被 OCR 打碎为「P(X  a)  E a[X]，for all a > 0」，其中「≥」被识别为不可打印字符、「≤」碎行、「E[X]/a」被断成「E a[X]」。上面按马尔可夫不等式标准形式重建为 $P(X \ge a) \le E[X]/a$，与下文证明一致。</span>

**证明（justification）。** 为论证马尔可夫不等式，让我们固定一个正数 $a$，考虑按如下方式定义的随机变量 $Y_a$：

```math
Y_a = \begin{cases} 0, & \text{if } X < a,\\ a, & \text{if } X \ge a. \end{cases}
```

可以看到，关系式 $Y_a \le X$ 恒成立，因而

```math
E[Y_a] \le E[X] .
```

> <span style="color:#7f8c8d;">沿页后续接：本页止于 $E[Y_a] \le E[X]$。下一自然步骤（利用 $E[Y_a] = a\, P(X \ge a)$ 推出 $P(X \ge a) \le E[X]/a$）在下一页（本次作业 PDF p275）继续。</span>

<!-- ===== 页末：§5.1 马尔可夫不等式的证明在本页收于 E[Y_a] ≤ E[X]，下一页续证 ===== -->
<!-- ===== PDF p275 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span>

<span style="color:#c0392b;">**§5.1　马尔可夫与切比雪夫不等式（Markov and Chebyshev Inequalities）（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页为 §5.1 正文（马尔可夫不等式证明）的续页，页首无新小节标题，故标「（续）」。内容为图 5.1（Figure 5.1，马尔可夫不等式推导示意）的图注续文、马尔可夫不等式证明的收尾，以及例 5.1（Example 5.1）。</span>

**图 5.1　马尔可夫不等式的推导示意（Illustration of the derivation of the Markov inequality）**

子图 (a) 展示了非负随机变量（nonnegative random variable）$X$ 的概率密度函数 PDF；子图 (b) 展示了与之相关的随机变量 $Y_a$ 的概率质量函数 PMF，$Y_a$ 的构造如下：把 $X$ 的 PDF 中位于 0 与 $a$ 之间的所有质量全部移到 0，把位于 $a$ 以上的所有质量全部移到 $a$。与子图 (a) 相比，期望只会减小，因此

```math
E[X] \ge E[Y_a].
```

另一方面，由 $Y_a$ 的 PMF 可得

```math
E[Y_a] = a\,P(Y_a = a) = a\,P(X \ge a).
```

于是 $E[X] \ge a\,P(X \ge a)$，即马尔可夫不等式（Markov inequality）

```math
P(X \ge a) \le \frac{E[X]}{a} .
```

参看图 5.1（Figure 5.1）的示意。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 马尔可夫不等式的整套论证可凝练为一个处处可复用的「尾部界」模板：构造一个非负、只在目标事件发生时取正值的随机变量 $Y_a$（此处把 $X$ 位于 $a$ 以下的质量全移到 $0$、$a$ 以上的质量全移到 $a$），由恒成立的 $Y_a \le X$ 得 $E[Y_a] \le E[X]$，而 $E[Y_a] = a\,P(X \ge a)$ 恰把「取大值」这一尾部事件的概率与期望挂钩。这个证明几乎不依赖 $X$ 的分布细节，只要 $X \ge 0$；这种「构造逐步逼近的指示量 + 用期望压住尾部概率」的手法是切比雪夫不等式、切诺夫界（Chernoff bound，见第 5 章习题 2）以及各种集中不等式（concentration inequality）的共同基石——例如 Cheng–Spielman 谱聚类对割宽、对与随机图上的扩散参数的界，都先求期望再对尾部作马尔可夫/切比雪夫式控制。第一性原理在于它翻译了「期望=概率质量中心」：若质量大量堆在很大处，期望必然很大，于是均值很小就逼出「取大值的概率必小」。它不要求方差、不要求独立性，近乎「免费」，代价是界往往宽松（例 5.1 给出 $P(X\ge 3)\le 2/3$，真实值仅 $0.25$）。因此在「只知均值、未知分布」的尾部估计里，它总是第一选择。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.1（马尔可夫不等式界住均匀分布概率。）**</span>

设 $X$ 均匀分布于区间 $[0,4]$ 上（uniformly distributed in $[0,4]$），并注意 $E[X] = 2$。于是马尔可夫不等式断言

```math
P(X \ge 2) \le \frac{E[X]}{2} = 1,\qquad
P(X \ge 3) \le \frac{E[X]}{3} = \frac{2}{3},\qquad
P(X \ge 4) \le \frac{E[X]}{4} = \frac{1}{2}.
```

与精确概率（exact probabilities）比较：

```math
P(X \ge 2) = 0.5,\qquad
P(X \ge 3) = 0.25,\qquad
P(X \ge 4) = 0,
```

我们看到，马尔可夫不等式给出的界可能相当宽松（quite loose）。
<!-- ===== PDF p276 ===== -->

<span style="color:#c0392b;">**§5.1　马尔可夫与切比雪夫不等式（Markov and Chebyshev Inequalities）（续）**</span>

我们继续讨论切比雪夫不等式（Chebyshev inequality）。粗略地说，它断言：若一个随机变量（random variable）的方差（variance）很小，那么它取到远离其均值（mean）的值的概率也很小。注意，切比雪夫不等式并不要求随机变量非负。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**[定理] 切比雪夫不等式（Chebyshev Inequality）**</span>

若 $X$ 是均值为 $\mu$、方差为 $\sigma^2$ 的随机变量，则对所有 $c > 0$，

```math
P\left( \left| X - \mu \right| \ge c \right) \le \frac{\sigma^2}{c^2}.
```

<span style="color:#2471a3;">**[proof]**</span> **证明（Justification）。** 为证明切比雪夫不等式，我们考察非负随机变量 $(X - \mu)^2$，并对它以 $a = c^2$ 应用马尔可夫不等式（Markov inequality）。我们得到

```math
P\left( (X - \mu)^2 \ge c^2 \right) \le \frac{E\left[ (X - \mu)^2 \right]}{c^2} = \frac{\sigma^2}{c^2}.
```

我们通过观察事件 $(X - \mu)^2 \ge c^2$ 与事件 $|X - \mu| \ge c$ 完全相同来完成证明，于是

```math
P\left( \left| X - \mu \right| \ge c \right)
= P\left( (X - \mu)^2 \ge c^2 \right) \le \frac{\sigma^2}{c^2}.
```

作为一条绕过马尔可夫不等式的类似推导，为简单起见假设 $X$ 是连续型随机变量，引入函数

```math
g(x) =
\begin{cases}
0, & \text{if } |x - \mu| < c,\\
c^2, & \text{if } |x - \mu| \ge c,
\end{cases}
```

注意对所有 $x$ 都有 $(x - \mu)^2 \ge g(x)$，并写出

```math
\sigma^2
= \int_{-\infty}^{\infty} (x - \mu)^2\, f_X(x)\, dx
\ge \int_{-\infty}^{\infty} g(x)\, f_X(x)\, dx
= c^2\, P\left( \left| X - \mu \right| \ge c \right),
```

这正是切比雪夫不等式。

切比雪夫不等式的另一等价形式可通过令 $c = k\sigma$（其中 $k > 0$）得到，从而有

```math
P\left( \left| X - \mu \right| \ge k\sigma \right)
\le \frac{\sigma^2}{k^2 \sigma^2}
= \frac{1}{k^2}.
```

因此，随机变量取值距其均值超过 $k$ 个标准差（standard deviations）的概率至多为 $1/k^2$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 切比雪夫不等式的证明是一套堪称模板的「降维」操作：把「离均值多远」这个看似分布依赖的问题，先取平方变成非负随机变量 $(X-\mu)^2$，再对 $a=c^2$ 直接套用马尔可夫不等式，尾部概率就被 $E[(X-\mu)^2]=\sigma^2$ 除以 $c^2$ 所界住。第一性原理是：方差本身就是「到均值的平均距离平方」，而事件 $|X-\mu|\ge c$ 恰好与 $(X-\mu)^2\ge c^2$ 等价，故方差小意味着质量集中在均值附近。相比马尔可夫，它不再要求 $X$ 非负（关键进步），且同样不依赖分布的具体形状。另一形态 $P(|X-\mu|\ge k\sigma)\le 1/k^2$ 是一个纯数值、与分布无关的通用法则，可用于反向推算样本量（例 5.5 由此得 $n\ge 50000$）。在实分析里，这本质上是「$L^2$ 范数控制 $L^1$-型尾部质量」这一分层不等式的概率翻版，与刻板类估计（Chebyshev-type bounds）同源；它是 §5.3 依概率收敛定义以及此后所有「大样本集中」直觉的出发点。界限通常保守，但胜在普适，是定位概率界的第一把钥匙。

> <span style="color:#7f8c8d;">[原页 OCR 说明] 本节页眉英文为“Sec. 5.1  Markov and Chebyshev Inequalities”，印刷页码 267，承接上一页同节内容，故标题标注「（续）」。OCR 多处将希腊字母损坏，均已按数学语义重建：均值 $\mu$ 被误读为「JL」「I1」「l1」、方差 $\sigma$ 被误读为「0'」「a」、$|X - \mu|$ 被误读为「I X - 111」/「I x - l1l」、$g(x)$ 被误读为分段「g (X)」、以及 $E[(X-\mu)^2]$/$\sigma^2$ 等被断行打散，均已按标准记号还原。</span>
<!-- ===== PDF p277 ===== -->
<span style="color:#c0392b;">第 5 章　极限定理（Limit Theorems）</span> — <span style="color:#c0392b;">§5.1 马尔可夫与切比雪夫不等式（Markov and Chebyshev Inequalities，续）</span>

> <span style="color:#7f8c8d;">承接上一页 §5.1 正文：本页页眉为「Sec. 5.1」，整页仍属 §5.1（尚未进入 §5.2 大数弱定律）。页首为切比雪夫与马尔可夫不等式对比的收尾讨论，随后给出 Example 5.2 与 Example 5.3（正文，非习题）。印页号 268。</span>

切比雪夫不等式（Chebyshev inequality）往往比马尔可夫不等式（Markov inequality）更强（它给出的界更精确），因为它还利用了关于 $X$ 的方差（variance）的信息。尽管如此，随机变量的均值（mean）与方差也只不过是其性质的粗略概括，我们不能指望这些界与实际概率（exact probabilities）的精确值十分接近。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.2（用切比雪夫不等式界定均匀分布与指数分布超出均值的概率）。**</span>

与例子 5.1（Example 5.1）相同，设 $X$ 在 $[0, 4]$ 上服从均匀分布（uniform distribution）。我们使用切比雪夫不等式来界定 $|X - 2| \ge 1$ 的概率。有 $\mu = 2$，$\sigma^2 = 16/12 = 4/3$，于是

```math
P\!\left(\left|X - 2\right| \ge 1\right) \le \frac{\sigma^2}{1} = \frac{4}{3},
```

这个结果没有信息量（uninformative）。

再举一例，设 $X$ 服从参数 $\lambda = 1$ 的指数分布（exponential distribution），于是 $E[X] = \operatorname{var}(X) = 1$。对任一 $c > 1$，利用切比雪夫不等式，我们得到

```math
P(X \ge c) = P(X - 1 \ge c - 1) \le P\!\left(\left|X - 1\right| \ge c - 1\right) \le \frac{1}{(c-1)^2}.
```

与精确答案 $P(X \ge c) = e^{-c}$ 相比，这个结果同样是保守的（conservative）。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.3（切比雪夫不等式中的上界，Upper Bounds in the Chebyshev Inequality）。**</span>

当已知 $X$ 的取值范围为 $[a, b]$ 时，我们断言 $\sigma^2 \le (b-a)^2/4$。于是，若 $\sigma^2$ 未知，我们可以用 $(b-a)^2/4$ 代替切比雪夫不等式中的 $\sigma^2$，从而对一切 $c > 0$ 得到

```math
P\!\left(\left|X - \mu\right| \ge c\right) \le \frac{(b-a)^2}{4c^2}.
```

为验证我们的断言，注意到对任意常数 $\gamma$ 都有

```math
E\!\left[(X - \gamma)^2\right] = E[X^2] - 2\gamma E[X] + \gamma^2,
```

而上述这个二次式（quadratic）在 $\gamma = E[X]$ 时取得最小值。由此推出

```math
E\!\left[\left(X - E[X]\right)^2\right] \le E\!\left[(X - \gamma)^2\right], \quad \text{对一切 } \gamma.
```

令 $\gamma = (a+b)/2$，我们得到

```math
\sigma^2 \le E\!\left[\left(X - \frac{a+b}{2}\right)^{\!2}\,\right] = E\!\left[(X-a)(X-b)\right] + \frac{(b-a)^2}{4} \le \frac{(b-a)^2}{4},
```

其中上式中的等式可由简单计算验证，而最后那个不等式则来自如下事实

```math
(x-a)(x-b) \le 0, \quad \text{对所有 } x \in [a, b].
```

界 $\sigma^2 \le (b-a)^2/4$ 可能相当保守，但在缺乏关于 $X$ 的进一步信息时，它无法被改进。当 $X$ 是以相等概率 $1/2$ 取两个极端值 $a$ 与 $b$ 的随机变量时，该界取等号。
<!-- ===== PDF p278 ===== -->

<span style="color:#c0392b;">**§5.2　大数弱定律（The Weak Law of Large Numbers）**</span>

<span style="color:#c0392b;">**5.2　大数弱定律（The Weak Law of Large Numbers）**</span>

大数弱定律（weak law of large numbers）断言，大量独立同分布（independent, identically distributed）随机变量的样本均值（sample mean），会以高概率非常接近真正的均值（true mean）。

正如本章引言所述，我们考虑一个独立同分布随机变量的序列 $X_1, X_2, \ldots$，其均值为 $\mu$、方差为 $\sigma^2$，并定义样本均值为

```math
M_n = \frac{X_1 + \ldots + X_n}{n}.
```

于是我们有

```math
E[M_n] = \frac{E[X_1] + \ldots + E[X_n]}{n}
= \frac{n\mu}{n}
= \mu,
```

再利用独立性（independence），有

```math
\operatorname{var}(M_n) = \frac{\operatorname{var}(X_1 + \ldots + X_n)}{n^2}
= \frac{\operatorname{var}(X_1) + \ldots + \operatorname{var}(X_n)}{n^2}
= \frac{n\sigma^2}{n^2}
= \frac{\sigma^2}{n}.
```

我们应用切比雪夫不等式（Chebyshev inequality），得到

```math
P\bigl(|M_n - \mu| \ge \varepsilon\bigr) \le \frac{\sigma^2}{n \varepsilon^2},
```

对任意 $\varepsilon > 0$ 成立。

我们注意到，对任意固定的 $\varepsilon > 0$，这个不等式的右端会随着 $n$ 的增大而趋于零。作为推论，我们便得到大数弱定律，它陈述如下。事实上，即便 $X_i$ 的方差为无穷大，这一定律仍然成立，但那时需要一个远为精巧的论证，此处略去。所需的唯一假设是 $E[X_i]$ 良定义（well-defined）。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**大数弱定律（The Weak Law of Large Numbers）**</span>

设 $X_1, X_2, \ldots$ 为独立同分布的随机变量，其均值为 $\mu$。则对每一个 $\varepsilon > 0$，我们有

```math
P\bigl(|M_n - \mu| \ge \varepsilon\bigr) \to 0,
\qquad \text{当 } n \to \infty .
```

大数弱定律表明，当 $n$ 很大时，$M_n$ 分布的绝大部分质量集中在 $\mu$ 附近。也就是说，如果我们在 $\mu$ 周围考虑一个长度为正的区间 $[\mu - \varepsilon, \mu + \varepsilon]$，那么 $M_n$ 落入该区间的概率很高；当 $n \to \infty$ 时，这一概率收敛到 $1$。当然，倘若 $\varepsilon$ 非常小，我们可能不得不等待更久（即需要更大的 $n$ 值），才能断言 $M_n$ 极有可能落入该区间。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 大数弱定律的证明几乎是对现有工具的「水到渠成」：对样本均值 $M_n$ 直接套切比雪夫不等式，得 $P(|M_n-\mu|\ge\epsilon)\le \sigma^2/(n\epsilon^2)$，而 $n\to\infty$ 时右端趋于 $0$。依赖链一目了然——切比雪夫依赖马尔可夫，马尔可夫只依赖期望。这也暴露了弱定律的三个软肋：它只断言「对每个固定的 $\epsilon$，越出 $\epsilon$-邻域的概率趋零」，却不说这种偏离发生多少次、幅度多大；它依赖方差不发散（定理虽只在均值良定义时仍成立，但证明须精巧得多，正文略去）；它更不保证每条样本路径真的收敛。第一性原理：$E[M_n]=\mu$ 且 $\operatorname{var}(M_n)=\sigma^2/n$ 随 $n$ 缩到 $0$，故分布质量必然「收缩到 $\mu$ 附近」——这是**分布坍缩**而非**路径收敛**意义上的陈述，正是它与 §5.5 强定律的分野。跨课程上，这一范式支撑蒙特卡洛估计（$\tfrac1n\sum h(X_i)\approx Eh(X)$）、经验频率逼近概率（例 5.4），也是随机增量式算法与随机投影（如 Johnson–Lindenstrauss 引理）中「大量独立样本均值以高概率贴近期望」这一通用手法的概率依据。
<!-- ===== PDF p279 ===== -->
<span style="color:#c0392b;">第 5 章　极限定理（Limit Theorems）</span> —— §5.2 The Weak Law of Large Numbers（大数弱定律）（正文续页，印页号 270）

> <span style="color:#7f8c8d;">承接上一页：本页是 §5.2 确立大数弱定律（weak law of large numbers）之后的应用示例，页首无新节标题，故标注「（续）」。本页给出两个关于经验频率（empirical frequency）与民意调查（polling）的示例，编号 Example 5.4、Example 5.5。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.4（概率与频率，Probabilities and Frequencies。）**</span>

考虑在某个随机实验中定义的事件 $A$。设 $p = P(A)$ 为该事件的概率。我们考虑该实验的 $n$ 次独立重复，令 $M_n$ 为事件 $A$ 出现的次数所占的比例；在此语境下，$M_n$ 常被称为 $A$ 的**经验频率（empirical frequency）**。注意

```math
M_n = \frac{X_1 + \cdots + X_n}{n},
```

其中 $X_i$ 在 $A$ 出现时取 $1$，否则取 $0$；特别地，$E[X_i] = p$。大数弱定律适用，并表明当 $n$ 很大时，经验频率最有可能落在 $p$ 的 $\epsilon$ 邻域之内。粗略地说，这使我们得以断定：经验频率是 $p$ 的无偏（faithful）估计。另一方面，这也是向把概率 $p$ 理解为 $A$ 出现频率（frequency of occurrence）这一方向迈出的一步。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.5（民意调查，Polling。）**</span>

设 $p$ 为支持某位参加竞选的候选人的选民所占的比例。我们采访 $n$ 名"随机选取"的选民，并记录下其中支持该候选人的比例 $M_n$。我们把 $M_n$ 视为对 $p$ 的估计，并希望考察它的性质。

我们将"随机选取"理解为：这 $n$ 名选民是从给定总体中独立且均匀地选取的。因此，被采访的每个人给出的回答可视为一个独立的 Bernoulli（伯努利）随机变量 $X_i$，其成功概率为 $p$，方差为 $\sigma^2 = p(1 - p)$。切比雪夫不等式（Chebyshev inequality）给出

```math
P\bigl(|M_n - p| \ge \epsilon\bigr) \le \frac{p(1 - p)}{n\,\epsilon^2}.
```

参数 $p$ 的真实值假定为未知。另一方面，可以验证 $p(1 - p) \le 1/4$（参见 Example 5.3），由此得到

```math
P\bigl(|M_n - p| \ge \epsilon\bigr) \le \frac{1}{4n\,\epsilon^2}.
```

例如，若 $\epsilon = 0.1$ 且 $n = 100$，我们得到

```math
P\bigl(|M_{100} - p| \ge 0.1\bigr) \le \frac{1}{4 \cdot 100 \cdot (0.1)^2} = 0.25.
```

用文字表述：当样本容量为 $n = 100$ 时，我们的估计之误差超过 $0.1$ 的概率不超过 $0.25$。

现在设想我们对民意调查提出一些较严格的规格要求。我们希望对自己的估计抱有很高的置信度（概率至少为 $95\%$），且要求估计非常精确（在 $p$ 的 $0.01$ 以内）。应当抽样多少名选民？

我们在此刻唯一能保证的是不等式

```math
P\bigl(|M_n - p| \ge 0.01\bigr) \le \frac{1}{4n\,(0.01)^2}.
```

只要我们选取足够大的 $n$，使得

```math
\frac{1}{4n\,(0.01)^2} \le 1 - 0.95 = 0.05,
```

就一定能满足上述规格要求，由此得到 $n \ge 50{,}000$。这样的 $n$ 满足我们的规格要求，但结果相当保守（conservative），因为它建立在相当宽松的切比雪夫不等式之上。对这一结果的改进将在第 5.4 节中考虑。
<!-- ===== PDF p280 ===== -->

<span style="color:#c0392b;">**5.3　依概率收敛（CONVERGENCE IN PROBABILITY）**</span>

> <span style="color:#7f8c8d;">本节为本页页眉（Sec. 5.3 / Convergence in Probability，印页号 271），属正文新节。页首承接上一节 §5.2 大数弱定律的结论展开。本页为 §5.3 开头，非续页。</span>

我们可以把大数弱定律（weak law of large numbers）解释为：样本均值（sample mean）$\bar X_n$ 收敛到真实均值 $\mu$。然而，由于 $\bar X_1, \bar X_2, \ldots$ 是一列**随机变量**（random variables），而不是一列**数**，所以「收敛」的确切含义必须加以精确定义。下面给出一个专门的定义。为了方便与通常的收敛概念进行比较，我们也一并给出后者的定义。

<span style="color:#2471a3;">**[定义]**</span> <span style="color:#00838f;">**确定性序列的收敛（Convergence of a Deterministic Sequence）**</span>

设 $a_1, a_2, \ldots$ 为一列实数，且 $a$ 为另一个实数。我们说序列 $a_n$ 收敛（converge）到 $a$，记作 $\lim_{n\to\infty} a_n = a$，是指对每个 $\epsilon > 0$，都存在某个 $n_0$，使得对所有 $n > n_0$ 都有

```math
|a_n - a| < \epsilon .
```

直观地说，若 $\lim_{n\to\infty} a_n = a$，则对任意给定的精度水平（accuracy level）$\epsilon$，当 $n$ 足够大时，$a_n$ 必落在距 $a$ 的 $\epsilon$ 范围之内。

<span style="color:#2471a3;">**[定义]**</span> <span style="color:#00838f;">**依概率收敛（Convergence in Probability）**</span>

设 $Y_1, Y_2, \ldots$ 为一列随机变量（未必相互独立），且 $a$ 为一个实数。我们说序列 $Y_n$ 依概率收敛（converge in probability）到 $a$，是指对每个 $\epsilon > 0$，有

```math
\lim_{n\to\infty} P\bigl(|Y_n - a| \ge \epsilon\bigr) = 0 .
```

依照这一定义，大数弱定律所说的正是样本均值依概率收敛到真实均值 $\mu$。更一般地，切比雪夫不等式（Chebyshev inequality）表明：若所有 $Y_n$ 都具有相同的均值 $\mu$，且 $\operatorname{var}(Y_n)$ 收敛到 $0$，则 $Y_n$ 依概率收敛到 $\mu$。

若随机变量 $Y_1, Y_2, \ldots$ 具有概率质量函数（PMF, probability mass function）或概率密度函数（PDF, probability density function），并依概率收敛到 $a$，那么根据上述定义，对充分大的 $n$，$Y_n$ 的 PMF 或 PDF 的「几乎全部」质量都集中到距 $a$ 的 $\epsilon$ 范围之内。将上面的定义改述成如下形式也是有启发意义的：对每个 $\epsilon > 0$，并对每个 $\delta > 0$，都存在某个 $n_0$，使得对所有 $n \ge n_0$ 都有

```math
P\bigl(|Y_n - a| > \epsilon\bigr) < \delta .
```

若我们把 $\epsilon$ 称为精度水平，把 $\delta$ 称为置信水平（confidence level），那么这个定义便具有如下的直观形式：对任何给定的精度与置信水平，……（未完，接下页）

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 依概率收敛之所以需要专门定义，是因为收敛对象是随机变量而非实数数列：$Y_n$ 每次实验都给出不同路径，无法像普通数列那样「逐项趋近」。定义把它折算为「对任意精度 $\epsilon$，偏离超过 $\epsilon$ 的概率趋于 $0$」——一个以**高概率接近**的统一语言，把「随机对象收敛到常数」翻译成一串普通极限 $\lim_n P(|Y_n-a|\ge\epsilon)=0$。极限次序极其关键：是对**每个固定的 $\epsilon$** 先取 $n\to\infty$ 的概率极限，绝不意味着在某个固定 $n$ 处偏差概率为零，更不保证路径上「偶尔偏离」的次数受控（例 5.8 中 $Y_n$ 依概率收敛到 $0$，$E[Y_n]=n$ 却发散）。这正是它与 §5.5「以概率 1 收敛」的根本分野。在实分析中，它对应「依测度收敛」（measure convergence），是弱于几乎处处收敛的一种收敛模式；这一概念是概率论通往分析工具箱的第一个「收敛接口」，把样本均值（§5.2）、CLT 等极限定理与 $L^p$、测度框架接起来。常见误区是想当然认为「依概率收敛蕴含矩收敛」「期望随下标趋极限」，例 5.8 已给出反例，务必警惕。

<!-- ===== PDF p281 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span>

<span style="color:#c0392b;">**§5.3　依概率收敛（Convergence in Probability）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页 §5.3 的正文（页首无新标题、无新节号），继续依概率收敛定义的讨论，并给出三个编号例子 **Example 5.6、5.7、5.8**。本章小节编号为 §5.1–§5.6，本页无公式编号（公式均未在原文中被单独编号）。</span>

（续起上页的讨论段）……只要 $n$ 足够大，$Y_n$ 就将在这些准确度与置信度水平内等于 $a$（convergence in probability：依概率收敛）。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.6（$Y_n = \min\{X_1, \ldots, X_n\}$ 依概率收敛于零）**</span>

设 $X_n$ 是一列在区间 $[0, 1]$ 上均匀分布（uniformly distributed）的独立随机变量，并令

```math
Y_n = \min\{X_1, \ldots, X_n\}.
```

$Y_n$ 的取值不会随 $n$ 的增大而增大，并且偶尔还会减小（每当得到某个 $X_n$ 的值小于前面各值时）。因此我们直观地预期 $Y_n$ 收敛于零。事实上，对 $\varepsilon > 0$，利用 $X_n$ 的独立性，我们有

```math
P\big(|Y_n - 0| \ge \varepsilon\big)
= P(X_1 \ge \varepsilon, \ldots, X_n \ge \varepsilon)
= P(X_1 \ge \varepsilon) \cdots P(X_n \ge \varepsilon)
= (1 - \varepsilon)^n .
```

特别地，

```math
\lim_{n \to \infty} P\big(|Y_n - 0| \ge \varepsilon\big)
= \lim_{n \to \infty} (1 - \varepsilon)^n = 0 .
```

由于这对每个 $\varepsilon > 0$ 都成立，我们得出结论：$Y_n$ 依概率收敛于零。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.7（$Y_n = Y/n$ 依概率收敛于零，其中 $Y$ 为指数随机变量）**</span>

设 $Y$ 是参数（parameter）$\lambda = 1$ 的指数分布（exponentially distributed）随机变量。对任意正整数 $n$，令 $Y_n = Y / n$。（注意这些随机变量是彼此依赖的。）我们希望考察序列 $Y_n$ 是否收敛于零。

对 $\varepsilon > 0$，我们有

```math
P\big(|Y_n - 0| \ge \varepsilon\big) = P(Y \ge \varepsilon n) = e^{-\varepsilon n} .
```

特别地，

```math
\lim_{n \to \infty} P\big(|Y_n - 0| \ge \varepsilon\big)
= \lim_{n \to \infty} e^{-\varepsilon n} = 0 .
```

由于这对每个 $\varepsilon > 0$ 都成立，$Y_n$ 依概率收敛于零。

人们或许会想当然地认为：若序列 $Y_n$ 收敛到某个数 $a$，那么期望 $E[Y_n]$ 也必然收敛到 $a$。下面的例子说明事实未必如此，同时也揭示了依概率收敛这一概念的一些局限性。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.8（$E[Y_n]$ 不收敛而 $Y_n$ 依概率收敛的例子）**</span>

设 $Y_n$ 是一列具有如下分布的离散随机变量：

```math
P(Y_n = y) =
\begin{cases}
1 - \dfrac{1}{n}, & \text{若 } y = 0,\\[4pt]
\dfrac{1}{n}, & \text{若 } y = n^2,\\[4pt]
0, & \text{其他情形 (elsewhere)}.
\end{cases}
```

> <span style="color:#7f8c8d;">[注] 本页末尾的分布刻画中，$y = n^2$ 处的取值 $\frac{1}{n}$ 在本页 OCR 中被误读为「$\frac{1}{n}$ 与 $n^2$ 颠倒/碎裂」（原文行「For $y = n^2$ … $\frac{1}{n}$」），此处按 §5.3 该例的标准表述重建为 $P(Y_n = n^2) = 1/n$；Example 5.8 的渐近结论（$Y_n \to 0$ 依概率收敛，但 $E[Y_n] = n$ 发散）将在下一页续接。</span>
<!-- ===== PDF p282 ===== -->
<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.8（续）——$E[Y_n]$（期望）不收敛而 $Y_n$ 依概率收敛**</span>

> <span style="color:#7f8c8d;">承接上一页：$Y_n$ 的分布为 $P(Y_n = n^2) = \frac{1}{n}$、$P(Y_n = 0) = 1 - \frac{1}{n}$。本页续完该例的渐近结论，随后进入 **§5.4（中心极限定理）**。</span>

由于对 $\varepsilon > 0$ 有 $P\big(|Y_n| \ge \varepsilon\big) = \frac{1}{n} \to 0$（当 $n \to \infty$），故 $Y_n$ 依概率收敛到零。另一方面，$E[Y_n] = n^2 \cdot \frac{1}{n} = n$，且 $\operatorname{var}(Y_n) = \frac{n^4}{n} - n^2 = n^3 - n^2$，两者当 $n$ 增大时都无界增长。因此，尽管 $Y_n$ 依概率收敛到零，它的期望与方差却并不收敛。换言之，**依概率收敛并不蕴含矩收敛**（convergence of moments）；依概率收敛这一概念既有用，也不应被理解为序列的矩或更高阶统计量必然随之稳定。

---

<span style="color:#c0392b;">**§5.4　中心极限定理（The Central Limit Theorem）**</span>

回顾：若独立随机变量 $X_1, \ldots, X_n$ 均服从正态分布（normal），则它们的和

```math
S_n = X_1 + \cdots + X_n
```

也服从正态分布，其真实均值（true mean）为 $n\mu$、方差为 $n\sigma^2$。若 $X_i$ 并非正态，这一结论一般不再成立；事实上，当 $n$ 趋于无穷时，$S_n$ 的方差随之趋于无穷，于是 $S_n$ 的分布也不能说趋于任何有意义的东西。

一个中间结果（an intermediate result）通过如下方式获得：考察 $S_n$ 偏离其均值 $n\mu$ 的偏差，并将其乘以一个与 $1/\sqrt{n}$ 成正比的因子（缩放）。这种特定缩放的特殊之处在于：它使（缩放后随机变量的）方差在 $n$ 增长时保持为常数，并且得到的极限断言了这些缩放后随机变量的分布趋近于一个正态分布（normal distribution）。更精确地说，[单一的中心极限定理]宣称：若 $X_1, \ldots, X_n$ 是均值为 $\mu$、方差为 $\sigma^2$ 的独立随机变量，则规范化后的随机变量 $\dfrac{S_n - n\mu}{\sigma \sqrt{n}}$ 随 $n \to \infty$ 的分布趋近于标准正态分布（standard normal distribution）。直接计算可得

```math
E\left[ \frac{S_n - n\mu}{\sigma \sqrt{n}} \right] = 0,
```

且其方差为常数 $1$（即 $\operatorname{var}\!\left( \frac{S_n - n\mu}{\sigma\sqrt{n}} \right) = 1$），这正是上面所说的「方差保持为常数」的含义。

> <span style="color:#7f8c8d;">[注] 本页所述为中心极限定理（§5.4）的引入段与规范化变量 $Z_n = (S_n - n\mu)/(\sigma\sqrt{n})$ 的均值、方差计算；定理的完整量化陈述（$P\!\left( \frac{S_n - n\mu}{\sigma\sqrt{n}} \le z \right) \to \Phi(z)$，其中 $\Phi$ 为标准正态 CDF）随本页末尾续接到下一页。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页正文被 OCR 打散为大量碎片（如「n2 In」「== n.」「- nM」「nJ1」「I1. - X」「f >」等），数值与换行均已碎裂。上面按该例与 §5.4 引入段的标准数学语义重建：Example 5.8 的 $E[Y_n] = n$ 与方差 $\operatorname{var}(Y_n) = n^3 - n^2$ 依前页分布 $P(Y_n = n^2) = 1/n$ 推出；§5.4 部分则按文本式（recall…normal…true mean, scaling by $1/\sqrt{n}$, normal distribution, the calculation yields $E[\cdot]=0$）整合。任一数值的严格原文请回查原书页 273。</span>
<!-- ===== PDF p283 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）—— §5.4　中心极限定理（The Central Limit Theorem）（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：上页引入了归一化随机变量 $Z_n = \dfrac{X_1 + \cdots + X_n - n\mu}{\sigma\sqrt{n}}$，并已在 §5.2（见 Example 5.8，关于样本均值 PMF 的那一段）中说明其分布随 $n$ 增大而向一种极限分布收敛。上页还验证了其均值（期望）为 $0$；本页开头继续计算其方差（variance）。</span>

且（沿用上页记号）$Z_n$ 的方差计算如下——由独立性（independence），

```math
\operatorname{var}(Z_n)
= \operatorname{var}\!\left( \frac{X_1 + \cdots + X_n - n\mu}{\sigma\sqrt{n}} \right)
= \frac{\operatorname{var}\!\left( X_1 + \cdots + X_n \right)}{\sigma^2 n}
= \frac{\operatorname{var}(X_1) + \cdots + \operatorname{var}(X_n)}{\sigma^2 n}
= \frac{n\sigma^2}{\sigma^2 n}
= 1 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上方方差推导占了本页前大半，OCR 将其打散为若干碎片（形如「$\operatorname{var}(X_1+\cdots+X_n) = \operatorname{var}(X_1)+\cdots+\operatorname{var}(X_n) = n\sigma^2$」除以「$\sigma^2 n$」等）。此处按数学语义与「等于 $1$」的残缺尾部重建为等价的标准推导；若需最严格原文请回查原书页 274。</span>

由此，$Z_n$ 具有零均值和单位方差，这与其分布向标准正态（standard normal，即均值为 $0$、方差为 $1$ 的正态分布）收敛的性质一致。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**The Central Limit Theorem（中心极限定理）。**</span>

设 $X_1, X_2, \ldots$ 是一列独立同分布（independent identically distributed）的随机变量，具有公共均值 $\mu$ 和方差 $\sigma^2$，并定义

```math
Z_n = \frac{X_1 + \cdots + X_n - n\mu}{\sigma\sqrt{n}} .
```

则 $Z_n$ 的 CDF（累积分布函数，cumulative distribution function）收敛到标准正态分布的 CDF $\Phi$，即对每一个 $z$，都有

```math
\lim_{n \to \infty} P(Z_n \le z) = \Phi(z) .
```

中心极限定理惊人地具有普遍性。除了独立性，以及均值与方差有限这一隐含假设之外，它对 $X_i$ 的分布别无其他要求——$X_i$ 可以是离散的、连续的或混合的；其证明的大致思路见章末习题。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 中心极限定理的第一性原理谜底就藏在外层那个 $\sqrt{n}$ 归一化里。对独立同分布 $X_i$，和 $S_n$ 的方差 $n\sigma^2$ 随 $n$ **线性**增长，故标准差 $\sqrt{n}\sigma$ 也线性增长——$S_n$ 本身越铺越宽。不去中心化时，$S_n-n\mu$ 的分布宽度量为 $\Theta(\sqrt n)$，随 $n$ 摊开、趋于无意义；于是既要平移回零均值、又要缩到同一尺度，就必须除以 $\sqrt{n}$，得出 $Z_n=(S_n-n\mu)/(\sigma\sqrt n)$，均值恒 $0$、方差恒 $1$——既不弥散也不坍缩，分布才可能点对点收敛到某个固定极限形（标准正态）。证明思路（见第 5 章习题 12\*）：先把 $M_X(s)$ 在 $s=0$ 处展到二阶 $M_X(s)=1+\tfrac{\sigma^2 s^2}{2}+o(s^2)$，代入 $M_{Z_n}(s)=\left(M_X\!\left(\frac{s}{\sigma\sqrt n}\right)\right)^n$，得到 $\left(1+\frac{s^2}{2n}+o(s^2/n)\right)^n\to e^{s^2/2}$；再借「变换逐点收敛且极限分布 CDF 连续 ⇒ CDF 收敛」这条连续性定理，把矩生成层面的收敛提升为分布层面（CDF）的收敛。这个「特征函数/矩生成 + 连续对应定理」的框架，正是 Fourier 式（特征函数）证明在概率中的表现，与调和分析里「核函数逐点收敛 ⇒ 分布弱收敛」同构。实务意义：大量微小独立误差之和趋于正态，解释了测量学与工程噪声为何处处服从正态。

该定理无论从概念上还是从实践上都极其重要。从概念角度看，它表明大量独立随机变量（independent random variables）之和近似服从正态分布（normal distribution）。正因如此，它适用于许多把某个随机效应视为大量微小但彼此独立的随机因子之和的情形。自然界或工程系统中的许多噪声（noise）都具有这一性质。在多种不同场合，人们通过经验发现，噪声的统计特征总能由正态分布很好地刻画，而中心极限定理为这一现象提供了令人信服的解释。

从实践角度看，中心极限定理消除了对精细概率模型的依赖，也免去了对 PMF（概率质量函数，probability mass function）和 PDF（概率密度函数，probability density function）的繁琐处理。更确切地说，它使我们能够仅通过查正态 CDF（累积分布函数）表就算出某些概率。此外，这些计算只需用到均值和方差。

<span style="color:#c0392b;">**Approximations Based on the Central Limit Theorem（基于中心极限定理的近似）**</span>

中心极限定理使我们能够像 $Z_n$ 是正态变量那样，去计算与 $Z_n$ 有关的概率。由于正态性在线性变换（linear transformations）下保持不变——

> <span style="color:#7f8c8d;">本页到此结束；上述“Approximations Based on the Central Limit Theorem”一节的正文（含“Normal Approximation Based on the Central Limit Theorem”与具体计算步骤、Example 5.9、Example 5.10）自下一页开始续接。</span>
<!-- ===== PDF p284 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — <span style="color:#c0392b;">**§5.4　中心极限定理（The Central Limit Theorem）**</span>（续）

<span style="color:#7f8c8d;">承接上一页：本节继续讨论中心极限定理的若干等价表述。页首承续上页末句，把 $S_n$ 视为均值为 $n\mu$、方差为 $n\sigma^2$ 的正态随机变量。印页号约 275。</span>

这等价于将 $S_n$ 视为均值为 $n\mu$、方差为 $n\sigma^2$ 的正态随机变量（normal random variable）。

---

<span style="color:#00838f;">**基于中心极限定理的正态逼近（Normal Approximation Based on the Central Limit Theorem）**</span>

设 $S_n = X_1 + \dots + X_n$，其中各 $X_i$ 是均值（mean）为 $\mu$、方差（variance）为 $\sigma^2$ 的独立同分布（independent identically distributed）随机变量。当 $n$ 很大时，概率 $P(S_n \le c)$ 可按下述步骤把 $S_n$ 当作正态随机变量来近似。

1. 计算 $S_n$ 的均值 $n\mu$ 与方差 $n\sigma^2$。

2. 计算归一化值（normalized value）$z = \dfrac{c - n\mu}{\sigma\sqrt{n}}$。

3. 使用近似
```math
P(S_n \le c) \;\approx\; \Phi(z),
```
其中 $\Phi(z)$ 由标准正态累积分布函数（standard normal CDF）表格给出。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.9（飞机装载包裹的总重量超过阈值之概率。）**</span>

我们在飞机上装载 100 个包裹，其重量是相互独立的随机变量，在 5 磅与 50 磅之间均匀分布（uniformly distributed）。问：总重量超过 3000 磅的概率是多少？要精确计算总重量的累积分布函数（CDF）以及所求概率并不容易，但利用中心极限定理（central limit theorem）可以很快得到一个近似答案。

我们想计算 $P(S_{100} > 3000)$，其中 $S_{100}$ 是这 100 个包裹重量之和。单个包裹重量的均值与方差分别为
```math
\mu = \frac{5 + 50}{2} = 27.5, \qquad
\sigma^2 = \frac{(50 - 5)^2}{12} = 168.75,
```
这是基于均匀累积概率密度函数（PDF）的均值与方差公式得到的。我们计算归一化值
```math
z = \frac{3000 - 100 \cdot 27.5}{\sqrt{168.75 \cdot 100}} = \frac{250}{129.9} = 1.92,
```
并利用标准正态表格得到近似
```math
P(S_{100} \le 3000) \approx \Phi(1.92) = 0.9726.
```
于是，所求概率为
```math
P(S_{100} > 3000) = 1 - P(S_{100} \le 3000) \approx 1 - 0.9726 = 0.0274.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.10（机器逐个加工零件，加工时间的正态近似。）**</span>

一台机器逐个（one at a time）加工零件。不同零件的加工时间（processing times）是相互独立的随机变量，在区间 $[1, 5]$ 上均匀分布。

<span style="color:#7f8c8d;">（本页止于此，Example 5.10 的其余内容在下一页续接。）</span>
<!-- ===== PDF p285 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — <span style="color:#7f8c8d;">§5.4 中心极限定理（Central Limit Theorem）正文续页，印页约 276</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.10（续）——零件加工时间示例（尾段，承接上一页 §5.4 该例）**</span>

> <span style="color:#7f8c8d;">承接上一页：设零件加工时间服从均值为 3、方差为 16/12 的分布，考察「320 时间单位内加工零件数 $N_{320}$ 至少为 100」这一事件。例号按其后出现 Example 5.11 反推为 Example 5.10（此题在本页无例头，故标注「续」）。</span>

我们想要近似计算在 320 个时间单位内被处理的零件数（记为 $N_{320}$）至少为 100 的概率。

并没有直接了当的办法把随机变量 $N_{320}$ 表示为一组独立随机变量之和，但我们可以换一种方式推进。设 $X_i$ 为第 $i$ 个零件的加工时间，令 $S_{100} = X_1 + \cdots + X_{100}$ 为前 100 个零件的总加工时间。事件 $\{N_{320} \ge 100\}$ 与事件 $\{S_{100} \le 320\}$ 是同一个事件，于是我们现在可以利用正态近似（normal approximation）来处理 $S_{100}$ 的分布。注意 $\mu = E[X_1] = 3$，$\sigma^2 = \mathrm{var}(X_1) = 16/12 = 4/3$。我们计算标准化值（normalized value）

```math
z = \frac{320 - n\mu}{\sigma \sqrt{n}} = \frac{320 - 300}{\sqrt{100 \cdot 4/3}} = 1.73,
```

并采用近似

```math
P(S_{100} \le 320) \approx \Phi(1.73) = 0.9582 .
```

如果 $X_i$ 的方差未知，但已知某个上界，那么就可以利用正态近似来获得所关注概率的界。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.11（Polling，民意调查）—— 重访 Example 5.5 中的民意调查问题**</span>

我们访问 $n$ 名投票者，并记录受访者中支持某特定候选人的比例 $M_n$。若 $p$ 是全体投票者中支持该候选人的比例，则

```math
M_n = \frac{X_1 + \cdots + X_n}{n},
```

其中 $X_i$ 是参数为 $p$ 的独立 Bernoulli 随机变量。特别地，$M_n$ 的均值为 $p$，方差为 $p(1-p)/n$。由正态近似，$X_1 + \cdots + X_n$ 近似于正态，因此 $M_n$ 也近似于正态。

我们关心的是民意调查误差大于某一期望精度 $\epsilon$ 的概率 $P\bigl(|M_n - p| \ge \epsilon\bigr)$。由于正态 PDF 关于均值对称，我们有

```math
P\bigl(|M_n - p| \ge \epsilon\bigr) \approx 2\,P\bigl(M_n - p \ge \epsilon\bigr).
```

$M_n - p$ 的方差 $p(1-p)/n$ 依赖于 $p$，因而未知。我们注意到，偏离均值的较大概率会随方差增大而增大。因此，通过假定 $M_n - p$ 具有最大可能的方差，即 $1/(4n)$（这对应 $p = 1/2$），可以得到 $P(M_n - p \ge \epsilon)$ 的一个上界。为了计算这个上界，我们求标准化值

```math
z = \frac{\epsilon}{1/(2\sqrt{n})},
```

并按正态近似使用（续下页）

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本例中标准化值的式子被 OCR 打散，仅识别出分母「$1/(2\sqrt{n})$」，分子处的 $\epsilon$ 已丢失；按句意「To calculate this upper bound, we evaluate the standardized value … and use the normal approximation」补为 $z = \epsilon\Big/\big(1/(2\sqrt{n})\big)$。若需严格原文请回查原书页 276。本页在「and use the normal approximation」处终止，例 5.11 的后续计算续接下一页。</span>
<!-- ===== PDF p286 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）—— §5.4 中心极限定理（The Central Limit Theorem）（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页位于 §5.4 正文中部，印页号为 277，页眉 "Sec. 5.4 / The Central Limit Theorem" 为该书运行页眉。正文先续讲利用最坏情形方差把 $M_n$ 视作正态的算例，再讨论反向的样本量问题，结尾引入二项分布的棣莫弗–拉普拉斯逼近。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.11（续）—— 用最坏情形方差把 $M_n$ 作正态近似**</span>

例如，考虑 $n = 100$ 且 $\epsilon = 0.1$ 的情形。假设取最坏情形的方差（worst-case variance），并把 $M_n$ 当作正态来处理，我们得到

```math
P\!\left(|M_{100} - p| \ge 0.1\right)
\;\approx\; 2\,P\!\left(M_{100} - p \ge 0.1\right)
\;\le\; 2 - 2\Phi\!\left(2 \cdot 0.1 \cdot \sqrt{100}\right)
= 2 - 2\Phi(2)
= 2 - 2 \cdot 0.977
= 0.046.
```

这远小于（也更精确于）在 Example 5.5 中利用切比雪夫不等式（Chebyshev inequality）所得出的 0.25 的估计。

现在我们考虑一个反向的问题。若我们希望估计 $M_n$ 以至少 0.95 的概率落在 $p$ 的 0.01 之内，需要多大的样本量 $n$？再次假设最坏情况下的方差，我们便得到条件

```math
2 - 2\Phi\!\left(2 \cdot 0.01 \cdot \sqrt{n}\right) \le 0.05,
```
即
```math
\Phi\!\left(2 \cdot 0.01 \cdot \sqrt{n}\right) \ge 0.975.
```

由正态分布表（normal tables）可见 $\Phi(1.96) = 0.975$，从而得到

```math
2 \cdot 0.01 \cdot \sqrt{n} \ge 1.96,
```
即
```math
n \;\ge\; \frac{(1.96)^2}{4 \cdot (0.01)^2} = 9604.
```

这比我们先前用切比雪夫不等式（Chebyshev's inequality）所得出的 50,000 的样本量要好得多。

随着 $n$ 趋于无穷，正态近似（normal approximation）变得越来越精确；但在实际中我们通常面对的是具体而有限的 $n$。若能事先知道 $n$ 应大到何种程度逼近才可被信赖，将十分有用，但对此并没有简单而普适的准则。这在很大程度上取决于 $X_i$ 的分布是否接近正态，尤其是它是否对称。例如，若 $X_i$ 服从均匀分布，则 $S_8$ 就已非常接近正态；但若 $X_i$ 比如说服从指数分布，则需显著更大的 $n$，$S_n$ 的分布才会接近正态。此外，当 $c$ 位于 $S_n$ 的均值附近时，对 $P(S_n < c)$ 的正态近似往往更为精确。

<span style="color:#c0392b;">**二项分布的棣莫弗–拉普拉斯逼近（De Moivre-Laplace Approximation to the Binomial）**</span>

参数为 $n$ 和 $p$ 的二项随机变量 $S_n$ 可以看成 $n$ 个相互独立、公共参数为 $p$ 的伯努利随机变量 $X_1, \ldots, X_n$ 之和：

```math
S_n = \sum_{i=1}^{n} X_i.
```

回忆
```math
\sigma = \sqrt{\operatorname{var}(X_i)} = \sqrt{p(1-p)},
```

> <span style="color:#7f8c8d;">本页在 $\sigma = \sqrt{p(1-p)}$ 处结束，随后的二项逼近推导与数值例继续于下一页。</span>
<!-- ===== PDF p287 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — §5.4 The Central Limit Theorem（中心极限定理）正文续页（续）

> <span style="color:#7f8c8d;">承接上一页：本页为 §5.4 关于**二项随机变量的正态逼近**（即棣莫弗–拉普拉斯逼近）讨论的正文延续。页首无新节标题，由「将二项随机变量当作正态来处理」起，逐句续讲，故标题标注「（续）」。印页号约 278。</span>

中心极限定理把二项随机变量（binomial random variable）$S_n$ 视为如同均值为 $np$、方差为 $\text{var}(S_n) = np(1-p)$ 的正态变量一般来近似处理（treats a binomial random variable as if it were normal with mean $np$ and variance $np(1-p)$）。于是，一条形如 $P(k \le S_n \le l)$ 的二项概率，便可由对应正态曲线在从 $k$ 到 $l$ 之间的区间下所覆盖的面积来近似——即图中标注的阴影面积（the shaded area in the figure）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 此段涉及一张插图（阴影面积、正态曲线下的区域）及其图号，OCR 把图中指注与正文打散（如「from $k$ to $l$ which is the shaded area ...」「Sec. 5.3 provides an illustration ...」），图号及个别指注词无法辨认。上文按下文语义续接为「正态曲线在区间上的面积近似二项概率」。</span>

然而，由于 $S_n$ 是整值（integer-valued）随机变量、而正态分布是连续的，当区间取得很小（例如当 $k = l$，即只取单个整点的概率时），这一近似就会产生不小的误差（if we have $k = l$, the error will be ...）。为此可考虑两点：

(a) 直接的正态面积近似在此情形下并不精确，误差可能较大。

(b) 一种可能的补救办法（a possible remedy）是把积分区间略微放宽：用正态概率（normal probability）在区间 $\left[k - \tfrac{1}{2},\; l + \tfrac{1}{2}\right]$ 上的值来近似，用这一加宽的连续区间去覆盖整值区域 $\{k \le S_n \le l\}$，从而使近似更准确。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上文 (a)(b) 两点为对「误差/补救」讨论的重建：OCR 仅留下括号编号「(a) A ...」「(b) A possible remedy is to use the normal probability ...」及碎片词（如「if we have k = 1, the ... will be」「by zero」），具体指注表述按标准叙述补全。末尾的「连续性修正（continuity correction）」术语及其区间指注（$k - \tfrac{1}{2}$ 到 $l + \tfrac{1}{2}$）于页尾出现，表明此讨论延续至下一页。</span>

现在我们用中心极限定理所提示的近似来求事件 $\{k \le S_n \le l\}$ 的概率。因为 $S_n$ 是均值为 $np$、方差为 $np(1-p)$ 的二项随机变量，故其标准化（standardized）版本 $\frac{S_n - np}{\sqrt{np(1-p)}}$ 近似服从标准正态分布（a standard normal distribution），于是我们得到

```math
P(k \le S_n \le l) \;\approx\; P\!\left( \frac{k - np}{\sqrt{np(1-p)}} \;\le\; \frac{S_n - np}{\sqrt{np(1-p)}} \;\le\; \frac{l - np}{\sqrt{np(1-p)}} \right)
= \Phi\!\left( \frac{l - np}{\sqrt{np(1-p)}} \right) - \Phi\!\left( \frac{k - np}{\sqrt{np(1-p)}} \right),
```

其中 $\Phi$ 记标准正态分布函数（累积分布函数，CDF）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式为标准化逼近的核心结果，OCR 将三个标准化分式（$\frac{k-np}{\sqrt{np(1-p)}}$、$\frac{S_n-np}{\sqrt{np(1-p)}}$、$\frac{l-np}{\sqrt{np(1-p)}}$）拆散成多行碎片（如「k - np」「l - np」「√(np(1-p))」），此处按标准语义重建并合并为规范 LaTeX；$\Phi$ 之定义符及等式右侧为按上下文补全。若需严格原文请回查原书页 278。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 上述对整值二项随机变量的逼近可用「连续性修正（continuity correction）」改善，即用放宽的区间 $\left(k - \tfrac{1}{2},\; l + \tfrac{1}{2}\right)$ 代入上式标准化端点，从而显著减小误差；此点正文随后续讲（延续至下一页）。
<!-- ===== PDF p288 ===== -->
<span style="color:#c0392b;">**§5.4　中心极限定理（The Central Limit Theorem）**（续）</span>

> <span style="color:#7f8c8d;">承接上一页：本节宿引入的标准正态累积分布函数记作 $\Phi$，中心极限定理（central limit theorem）在上一页已作完整陈述。此页为正文续页，先给出二项分布的棣莫弗–拉普拉斯逼近（De Moivre–Laplace approximation）之盒装结果，随后转入 Example 5.12 及单点概率（single value）逼近的算例。印页号约 279。</span>

---

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**Definition　二项分布的棣莫弗–拉普拉斯逼近（De Moivre–Laplace Approximation to the Binomial）**</span>

若 $S_n$ 是参数为 $n$ 与 $p$ 的二项随机变量（binomial random variable），$n$ 很大，且 $k, l$ 为非负整数，则

```math
P(k \le S_n \le l) \approx \Phi\!\left(\frac{l - np}{\sqrt{np(1-p)}}\right) - \Phi\!\left(\frac{k - np}{\sqrt{np(1-p)}}\right).
```

当 $p$ 接近 $1/2$（此时各 $X_i$ 的概率质量函数（probability mass function，PMF）对称）时，上式即使对 $n$ 小到 40 或 50 也能给出很好的近似。当 $p$ 接近 1 或接近 0 时，近似的精度下降，为了维持同样的精度就需要更大的 $n$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 棣莫弗–拉普拉斯公式是中心极限定理最早的应用（源自梳妆赌局时代的二项近似），它把二项概率化约为标准正态 CDF 之差 $\Phi(\tfrac{l-np}{\sqrt{np(1-p)}})-\Phi(\tfrac{k-np}{\sqrt{np(1-p)}})$。第一性原理：$S_n$ 是独立同分布 Bernoulli 之和，均值 $np$、方差 $np(1-p)$，直接代入 CLT 的归一化 $Z=(S_n-np)/\sqrt{np(1-p)}$ 即得上述端点标准化。由于二项是整值、正态是连续分布，当区间很窄（如单点 $k=l$）时直接逼近误差可观，正文于是把区间放宽半格到 $\left[k-\tfrac12,\;l+\tfrac12\right]$——这就是连续性修正（continuity correction）；其本质是每个整数点集中的原子概率其实「占据」了整整一个单位宽度，把 CDF 的阶梯跳变摊平成单位宽的连续刻度，近似才不失真。这与数值积分中用归中矩形覆盖分段质量是同一思想。跨课程上，这套做法在「离散高斯/亚高斯尾界」、误差分组与直方图逼近里反复出现。实用经验法则：$n$ 越大、$p$ 越接近 $1/2$（PMF 越对称）逼近越准；$p\to 0$ 或 $1$ 时 PMF 强偏斜，需更大 $n$ 才能保持精度。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.12（二项随机变量的正态逼近算例。）**</span>

设 $S_n$ 是参数为 $n$ 与 $p = 0.5$ 的二项随机变量。精确计算给出

```math
P(S_n \le 21) = \sum_{k=0}^{21} \binom{36}{k}(0.5)^{36} = 0.8785.
```

不使用上述改进（refinement）的中心极限定理近似给出

```math
P(S_n \le 21) \approx \Phi\!\left(\frac{21 - np}{\sqrt{np(1-p)}}\right)
      = \Phi\!\left(\frac{21 - 18}{3}\right)
      = \Phi(1) = 0.8413.
```

利用所提出的改进，我们有

```math
P(S_n \le 21) \approx \Phi\!\left(\frac{21.5 - np}{\sqrt{np(1-p)}}\right)
      = \Phi\!\left(\frac{21.5 - 18}{3}\right)
      = \Phi(1.17) = 0.879,
```

这比之前的结果更接近精确值。

> <span style="color:#7f8c8d;">[原页此处 OCR 略损] 本例精确和的求和上下限在 OCR 中被拆散（原文当为 $\sum_{k=0}^{21}\binom{36}{k}(0.5)^{36}$），已按数值 0.8785 还原；事件记为 $P(S_n \le 21)$（$\le$ 在 OCR 中被识成一般符号）。</span>

棣莫弗–拉普拉斯公式还允许我们近似单个取值的概率。例如，

```math
P(S_n = 19) \approx \Phi\!\left(\frac{19.5 - 18}{3}\right) - \Phi\!\left(\frac{18.5 - 18}{3}\right)
      = \Phi(0.5) - \Phi(1/6) = 0.6915 - 0.5675 = 0.124.
```

这与精确值非常接近，精确值为

```math
\binom{36}{19}(0.5)^{36} = 0.1251.
```

> <span style="color:#7f8c8d;">[跨页提示] 本页在给出 $P(S_n = 19)$ 逼近后即结束；若后续为新的单点概率算例并按本手册惯例续编为 Example 5.13，则它应始于下一页，本页不做编号臆造。</span>
<!-- ===== PDF p289 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span>

<span style="color:#c0392b;">**§5.5　大数强定律（The Strong Law of Large Numbers）**</span>

大数强定律与弱定律（weak law）相似之处在于，它也处理样本均值（sample mean）对真实均值的收敛问题；但它又有所不同，因为它指的是另一种类型的收敛。

下面是关于大数强定律的一个一般性陈述（general statement）。在随机变量 $X_i$ 具有有限四阶矩（finite fourth moments）这一略显限制性的假定下，大数强定律的证明在章末习题中给出。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**大数强定律（The Strong Law of Large Numbers）**</span>

设 $X_1, X_2, \ldots$ 是一列独立同分布（independent identically distributed）的随机变量，其均值为 $\mu$。那么，样本均值序列 $M_n = (X_1 + \cdots + X_n)/n$ 依概率 1（with probability 1）收敛于 $\mu$，其含义为

```math
\Pr\left(\lim_{n \to \infty} \frac{X_1 + \cdots + X_n}{n} = \mu\right) = 1.
```

为了理解大数强定律，我们需回到基于样本空间（sample space）对概率模型最初的描述。设想中的试验是无限长的，它生成一列值，每个值对应于序列 $X_1, X_2, \ldots$ 中的某一个随机变量。因此，最好把样本空间看作实数无穷序列 $(X_1, X_2, \ldots)$ 构成的集合：任何这样的序列都是该试验的一个可能结果。现在考虑由那些长期平均值（long-term average）为 $\mu$ 的序列 $(x_1, x_2, \ldots)$ 所组成的集合 $A$，即

```math
\lim_{n \to \infty} \frac{x_1 + \cdots + x_n}{n} = \mu.
```

大数强定律断言，全部概率都集中分布在样本空间的这一特定子集上。等价地说，那些不属于 $A$ 的结果（即长期平均值不为 $\mu$ 的无穷序列）所构成的集合，其概率为零。

弱定律与强定律之间的差别十分微妙，值得仔细审视。弱定律断言，$M_n$ 显著偏离 $\mu$ 的概率 $P\big(\lvert M_n - \mu\rvert \ge \varepsilon\big)$ 在 $n \to \infty$ 时趋于零。尽管如此，对任意有限的 $n$，这一概率仍可能为正，并且可以设想会有那么偶尔的几次（即便很少发生）$M_n$ 显著偏离 $\mu$。弱定律对这类偏离的次数不提供任何确定的信息，但强定律却提供了。根据强定律，且以概率 1，$M_n$ 收敛于 $\mu$。这意味着对任意给定的 $\varepsilon > 0$，差值 $\lvert M_n - \mu\rvert$ 会无限多次超过 $\varepsilon$ 的概率等于零。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 强弱定律的分野不在结论强弱本身，而在**收敛模式**：弱定律（§5.2）用依概率收敛，只要求 $M_n$ 越出 $\epsilon$-邻域的概率逐 $n$ 趋零，对「偶发大偏离的次数与幅度」不提供任何信息；强定律则断言 $\Pr(\lim_n M_n=\mu)=1$，即几乎所有样本路径上序列本身确实收敛到 $\mu$，还蕴含「对任意 $\epsilon$，无限多次越界的概率为 $0$」。直觉上，弱定律是「空间层面—大多数时刻接近」的陈述，强定律是「路径层面—几乎每条路径最终贴近」的陈述；后者蕴含前者，反之不然。为什么证明难度陡增？弱定律只要一阶（切比雪夫）尾部界；强定律要保证「无限多次越界这个事件的概率为 $0$」，需要更精细的控制——本书在章末习题中假定**有限四阶矩**（由此可证越界事件的概率和可加、收敛），再借 Borel–Cantelli 引理论证「几乎对每条路径只有有限多次大偏离」。第一性原理：若各次大偏差的概率可求和（$\sum_n 1/n^2$ 之类收敛），则「无限多次越界」这一事件概率为 $0$。这一「弱收敛在路径层加强」的思路与实分析中「几乎处处收敛 vs 依测度收敛」、随机过程理论里「几乎必然 vs 依概率」层层递进完全同构；在信息论/通信中，强定律正是「典型序列（typical sequences）」存在性这一编码定理支柱的基石。
<!-- ===== PDF p290 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）—— §5.5　大数强定律（The Strong Law of Large Numbers，续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页为 §5.5 的正文续页（印页号 281），无新节标题，直接续讲强定律的内容；页首为 Example 5.13。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.13（概率与频率，Probabilities and Frequencies）。**</span>

如 Example 5.4 所述，考虑某个随机试验（probabilistic experiment）意义上所定义的事件 $A$。我们考察同一试验的独立重复（independent repetitions）的序列，并令 $A_n$ 为前 $n$ 次重复中事件 $A$ 发生的比例（fraction）。大数强定律（strong law of large numbers）断言，$A_n$ 以概率 1（with probability 1）收敛到 $P(A)$。相比之下，大数弱定律（weak law of large numbers）断言 $M_n$ 依概率收敛（converges in probability）到 $P(A)$（参见 Example 5.4）。

我们常常直观地把事件 $A$ 的概率说成它在无限长的一系列独立试验中发生的频率（frequency）。强定律支撑了这一直觉，并确立 $A$ 发生的长期频率确实等于 $P(A)$，且实质上确定（essential certainty）地成立（即这一事件发生的概率为 1）。

<span style="color:#2471a3;">**[定义]**</span> <span style="color:#00838f;">**Definition: Convergence with Probability 1（以概率 1 收敛 / 几乎必然收敛）**</span>

设 $Y_1, Y_2, \ldots$ 是一列随机变量（random variables）（它们不必相互独立，not necessarily independent）。设 $c$ 为一个实数。我们说 $Y_n$ 以概率 1 收敛到 $c$（或几乎必然收敛，almost surely），若

```math
P\left( \lim_{n\to\infty} Y_n = c \right) = 1.
```

与我们早先的讨论类似，对这种收敛方式的一种恰当理解需要设想一个由无限序列构成的样本空间（sample space）：所有的概率都集中在那些收敛到 $c$ 的序列上。这并不意味着其他序列不可能发生，只表示它们极其不可能（extremely unlikely）——在它们各自的总概率为零这一意义之下。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.14（最小值序列几乎必然收敛到零）。**</span>设 $X_1, X_2, \ldots$ 是一列独立随机变量，服从 $[0, 1]$ 上的均匀分布，并令 $Y_n = \min\{X_1, \ldots, X_n\}$。我们希望证明 $Y_n$ 以概率 1 收敛到 $0$。

在试验的任何一次执行中，序列 $Y_n$ 是非增的（nonincreasing），即对所有 $n$ 有 $Y_{n+1} \le Y_n$。由于该序列被零从下方界定（bounded below by zero），它必存在极限，记为 $Y$。设取定某个 $\epsilon > 0$。$Y \ge \epsilon$ 当且仅当对所有 $i$ 有 $X_i \ge \epsilon$，这意味着

> <span style="color:#7f8c8d;">[原页此处为换页截断] Example 5.14 的证明在本页末尾随换页被截断：原文写到「这意味着（which implies that）」即止，其后的概率计算（由独立性得到 $P\left(X_i \ge \epsilon,\; \text{对所有 } i\right) = (1-\epsilon)^n$，并据此对任意 $n$ 与两侧取极限得出 $P\left(Y \ge \epsilon\right) = 0$）延续至下一页。本页 OCR 恰在此处上下文读作一串无序圆点，实为续接的推理式。续页当以「（续）」承接本 Example。</span>
<!-- ===== PDF p291 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — §5.5 大数强定律（The Strong Law of Large Numbers）正文续页（承上页 Example 5.14 的收尾论证）

> <span style="color:#7f8c8d;">承上页：本页页首承接上一页 Example 5.14 的收尾论证（页首无新节/新标题，故整段 §5.5 部分标注「续」）；页正文见 Example 5.15，随后进入 §5.6。</span>

（Example 5.14，续）由于这对所有 $n$ 成立，我们必有

```math
P(Y \ge \varepsilon) \le \lim_{n\to\infty} (1-\varepsilon)^n = 0 .
```

这表明对任意正的 $\varepsilon$ 都有 $P(Y \ge \varepsilon) = 0$。由此我们推得 $P(Y > 0) = 0$，从而 $P(Y = 0) = 1$。由于 $Y$ 是 $Y_n$ 的极限，我们看到 $Y_n$ 依概率 1 收敛到 0（converge to zero with probability 1）。

依概率 1 收敛蕴含依概率收敛（convergence in probability）（见章末习题），但其逆命题不一定成立。我们最后一个例子正是说明依概率收敛与依概率 1 收敛之间的差别。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 5.15（离散时间到达过程：依概率收敛但不依概率 1 收敛）**</span>

考虑一个离散时间到达过程（discrete-time arrival process）。时间的集合被划分成连续区间（consecutive interval），形如 $I_k = \{2^k, 2^k+1, \ldots, 2^{k+1}-1\}$。注意 $I_k$ 的长度为 $2^k$，它随 $k$ 增大而增大。在每个区间 $I_k$ 内恰好有一次到达（arrival），并且区间内的各个时刻等可能。假定不同区间内的到达时刻相互独立。我们定义：若在时刻 $n$ 有一次到达，则 $Y_n = 1$；若没有到达，则 $Y_n = 0$。

若 $n \in I_k$，我们有 $P(Y_n \ne 0) = 1/2^k$。注意当 $n$ 增大时，它属于下标 $k$ 越来越大的区间 $I_k$。于是

```math
\lim_{n\to\infty} P(Y_n \ne 0) = \lim_{k\to\infty} \frac{1}{2^k} = 0 ,
```

故我们推得 $Y_n$ 依概率收敛到 $0$。然而，当我们实际做这个实验时，到达的总数是无穷的（每个区间 $I_k$ 内有一次到达）。因此，$Y_n$ 对无穷多个 $n$ 取值都为 1，事件 $\{\lim_{n\to\infty} Y_n = 0\}$ 的概率为零，于是我们并不具有依概率 1 的收敛。

直观上，发生的是以下情形：在任何给定的时刻，对 0 产生显著偏离的概率都很小，并且随 $n$ 递减，这导致了依概率收敛。另一方面，只要时间足够长，一次对 0 的显著偏离就必然会发生，正因如此，我们并不具有依概率 1 的收敛。

<span style="color:#c0392b;">**5.6 小结与讨论（Summary and Discussion）**</span>

在本章中，我们探讨了概率论中某些具有重大概念与实践意义的基本方面。在概念层面，它们为「概率（probability）是大量独立试验中的相对频率」这一解释奠定了坚实基础。在实践层面，它们使我们能够在涉及独立随机变量之和、且用其他手段计算起来会过于困难的模型中，近似地计算概率。我们将在统计推断（statistical inference）那一章看到大量的应用。
<!-- ===== PDF p292 ===== -->
<span style="color:#c0392b;">**§5.6　小结与讨论（Summary and Discussion）**</span>

> <span style="color:#7f8c8d;">第 5 章小结，回顾本节的极限定理（limit theorems）与收敛概念（convergence concepts）。印页号 283。</span>

本章讨论了三种以极限定理（limit theorems）形式出现的重要定律。

<span style="color:#2471a3;">**(a)**</span> 其一是大数弱定律（weak law of large numbers），它指出当样本量增大时，样本均值（sample mean）极可能接近真实均值。该定律建立在切比雪夫不等式（Chebyshev inequality）之上，而切比雪夫不等式本身也值得单独研究，它是贯穿概率论（probability theory）的一大类有用不等式的代表。

<span style="color:#2471a3;">**(b)**</span> 其二是中心极限定理（central limit theorem），它是概率论最引人注目的成果之一，断言大量独立随机变量之和近似服从正态分布（normal）。中心极限定理有着众多应用：它是统计分析（statistical analysis）的主要工具之一，也为主张在广泛多样情形的建模中使用正态随机变量提供了依据。

<span style="color:#2471a3;">**(c)**</span> 其三是大数强定律（strong law of large numbers），它在概率与相对频率（relative frequencies）之间建立了更强的联系，并且往往是理论研究中的重要工具。

在推导上述各种极限定理的过程中，我们引入了若干收敛概念，即依概率收敛（convergence in probability）与以概率 1 收敛（convergence with probability 1），这些概念为讨论概率模型（probabilistic models）中的收敛提供了一个精确的语言。本章讨论的极限定理与收敛概念，是研究概率模型与随机过程（stochastic processes）的若干更深入专题的基础。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 整个第 5 章的脉络可压缩成一条「工具 → 结论」的依赖链：§5.1 的马尔可夫→切比雪夫（尾部界的「构造指示量 + 期望压界」模板）是地基；§5.2 用切比雪夫随手推出大数弱定律（样本均值依概率趋向 $\mu$）；§5.3 顺势为「收敛」建立精确语言——依概率收敛；§5.4 的中心极限定理是技术巅峰，给出「大量独立和近似正态」这一普适结论；§5.5 再以更细的四阶矩工具把弱收敛升级为几乎必然收敛的强定律。三枚定理回答三个不同层次的问题：弱定律≈「均值以大概率接近真值」（估计的可靠性），中心极限定理≈「误差的具体形状是钟形」（分布的结构），强定律≈「几乎每条路径都收敛」（路径的必然性）。它们把「概率=相对频率」「大样本集中」的直觉严格化，构成后续统计推断、蒙特卡洛、以及随机过程（鞅、遍历论）的理论入口。若想融会贯通，建议把握三个抓手：①尾部界四步模板——构造指示/台阶变量→期望控制→事件等价→取极限；②为何用 $\sqrt n$ 归一化才能让 CLT 成立；③弱/强定律的收敛模式差异（依概率 vs 几乎必然）。掌握了这三点，第 5 章便可视为一座自洽的、可迁移到任何大样本分析的微型方法论。

<!-- ===== PDF p293 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — 习题区（Problems）起，印刷页码 284，承接上页 §5.6 小结后进入第 5 章习题。

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**SECTION 5.1　Some Useful Inequalities（若干有用不等式）**</span>

<hr>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1.（统计学家估计总体平均身高 height）**</span>

A statistician wants to estimate the mean height $h$ (in meters) of a population, based on $n$ independent samples $X_1, \ldots, X_n$ chosen uniformly from the entire population. He uses the sample mean $M_n = (X_1 + \cdots + X_n)/n$ as the estimate of $h$, and a rough guess of $1.0$ meters for the standard deviation of the samples $X_i$.

**(a)** How large should $n$ be so that the standard deviation of $M_n$ is at most $1$ centimeter?

**(b)** How large should $n$ be so that Chebyshev's inequality guarantees that the estimate is within $5$ centimeters from $h$, with probability at least $0.99$?

**(c)** The statistician realizes that all persons in the population have heights between $1.4$ and $2.0$ meters, and revises the standard deviation figure that he uses based on the bound of Example 5.3. How should the values of $n$ obtained in parts (a) and (b) be revised?

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 1 原文中的下标与字号在 OCR 中被碾压：样本 $X_1, \ldots, X_n$ 被误读为「Xl , . . . , X」，样本均值 $M_n = (X_1 + \cdots + X_n)/n$ 被误读为「$M_n = (X_l + \cdots + X)/n$」，抽样标准差的脚标 $X_i$ 被误读为「X$_t$」。上述按原文语义（sample mean、standard deviation of the samples）合理还原为标准记号，若需最严格原文请回查原书页 284。</span>

<hr>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2.\*（Chernoff 界 Chernoff bound）**</span>

**The Chernoff bound. The Chernoff bound is a powerful tool that relies on the transform associated with a random variable, and provides bounds on the probabilities of certain tail events.**

**(a)** Show that the inequality

```math
P(X \ge a) \le e^{-sa} M(s)
```

holds for every $a$ and every $s \ge 0$, where $M(s) = E\!\left[e^{sX}\right]$ is the transform associated with the random variable $X$, assumed to be finite in a small open interval containing $s = 0$.

**(b)** Show that the inequality

```math
P(X \le a) \le e^{-sa} M(s)
```

holds for every $a$ and every $s \le 0$.

**(c)** Show that the inequality

```math
P(X \ge a) \le e^{-\phi(a)}
```

holds for every $a$, where

```math
\phi(a) = \max_{s \ge 0} \left( sa - \ln M(s) \right).
```

**(d)** Show that if $a > E[X]$, then $\phi(a) > 0$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 2 各小问的公式在 OCR 中被打散：命题式 (a) 被误读为「P ( X ≥ a) ≤ e −sa M (s)」、式 (c) 的正文不等式整行缺失（第 42 行为空白），仅保留「holds for every a, where」；$\phi(a) = \max_{s\ge 0}(sa - \ln M(s))$ 中的 $\ln M(s)$ 被误读为「In 1.1(s)」。以上按标准 Chernoff 界（bound on tail probabilities）语义还原为规范 LaTeX，若需最严格原文请回查原书页 284。</span>

> <span style="color:#7f8c8d;">题号复核：本页为第 5 章习题区起始页，Problem 编号自第 5 章重新从 **Problem 1** 起（Problem 2 为带 * 级题），不与第 4 章 Problems（Problem 1–45）混号。本页末尾 Problem 2 的第 (d) 问结束，后续习题续接下页。</span>
<!-- ===== PDF p294 ===== -->

<span style="color:#c0392b;">第 5 章　极限定理（Limit Theorems）—— 习题区（Problems，续）</span>

> <span style="color:#7f8c8d;">承接上一页（PDF p293，印页号 285 正文）：本页为 **Problem 2﹡（Chernoff 界）** 之「英文 Solution（解答）」续页。Problem 题干与带 * 题的英文 Solution 一律保持英文原文，仅标签可中文。此处页首无新 Sec./新题号，故标注「（续）」。Problem 2﹡（上部小问 (e)(f) 陈述 + Solution (a)(b) 解答）之首部在上一页，本页为其中间部分。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2﹡（续）**</span> — (e) Apply the result of part (c) to obtain a bound for $P(X \ge a)$, for the case where $X$ is a standard normal random variable and $a > 0$.

(f) Let $X_1, X_2, \ldots$ be independent random variables with the same distribution as $X$. Show that for any $a > E[X]$, we have

```math
P\left(X_1 + \cdots + X_n \ge n a\right) \;\le\; e^{- \,n\, h(a)} \qquad \text{（指数速率上界，速率 } h(a)>0 \text{，具体形态由上文小问定出）}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上方 (f) 的目标不等式在源页 OCR 中缺失（第 10 行公式位置为空白碎片，无法辨认其上界的确切速率函数），上式为按题意「样本均值超过均值一定量的概率随 n 指数衰减」合理补全的示意式，非逐字原文。如需严格原文请回查原书页 285。</span>

so that the probability that the sample mean exceeds the mean by a certain amount decreases exponentially with $n$.

---

<span style="color:#2471a3;">**[solution]**</span> **Solution (解答，续).** (a) Given some $a$ and $s \ge 0$, consider the random variable $Y_a$ defined by

```math
Y_a =
\begin{cases}
0, & \text{if } X < a,\\
e^{sa}, & \text{if } X \ge a.
\end{cases}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上方 $Y_a$ 的分段定义在源页中两分支取值（顶部应为 $0$ 或 $e^{sa}$）乱序碎裂，此处按压降思想与下文 $E[Y_a] = e^{sa} P(X \ge a)$ 推得的关系补全。原文第 15–16 行仅残留「if $X < a$,」「if $X \ge a$.」两个条件分支。</span>

It is seen that the relation $Y_a \le e^{sX}$ always holds and therefore,

```math
E[Y_a] \;\le\; E\!\left[e^{sX}\right] = M(s).
```

On the other hand,

```math
E[Y_a] = e^{sa}\, P(X \ge a),
```

from which we obtain

```math
P(X \ge a) \;\le\; e^{-sa} M(s).
```

(b) The argument is similar to the one for part (a). We define $Y_a$ by

```math
Y_a =
\begin{cases}
e^{sa}, & \text{if } X \ge a,\\
0, & \text{if } X < a .
\end{cases}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源页第 25–27 行该分段碎裂为「$\{ e^{sa}$, if X  a, / $Y_a = 0$, / if X > a.」，其中条件「if X < a」中的 $<$ 被 OCR 误读为 $>$。此处按与 (a) 对称的构造补正为「$e^{sa}$（若 $X \ge a$）、$0$（若 $X < a$）」。</span>

Since $s \ge 0$, the relation

```math
I_{\{X \ge a\}}\, e^{sa} \;\le\; e^{sX}
```

always holds and therefore,

```math
E[Y_a] \;\le\; M(s).
```

On the other hand,

```math
E[Y_a] = e^{sa}\, P(X \ge a),
```

from which we obtain

```math
P(X \ge a) \;\le\; e^{-sa} M(s).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (b) 中的中间关系式「$Y_a \le e^{sX}$」与中间期望等式在源页 OCR 中为空白碎片（第 29–34 行公式位置缺失），上式为按 (a) 平行对称地补全；若需严格原文请回查原书页 285。</span>
<!-- ===== PDF p295 ===== -->

<span style="color:#2471a3;">**[solution]**</span>  <span style="color:#c0392b;">**Problem 2\*（续）—— The Chernoff bound（切诺夫界）的英文解答**</span>

> <span style="color:#7f8c8d;">承接上一页（p294）：本页为 Problem 2\*（The Chernoff bound）的英文 Solution 之续，对应小问 (c)、(d)、(e)、(f)。页首为运行页眉（Limit Theorems / 286 / Chap. 5），无新 Sec. 亦无新题号，故标注「续」并保持英文原文。</span>

**(c)** Since the inequality from part (a) is valid for every $s \ge 0$, we obtain

```math
P(X \ge a) \le \min_{s \ge 0}\left( e^{-sa} M(s) \right)
= \min_{s \ge 0} e^{-(sa - \ln M(s))}
= e^{ - \max_{s \ge 0} (sa - \ln M(s))}
= e^{-\phi(a)} .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 变换 $M(s)$ 在源文中被打散成碎片（出现「j\,f (s)」等乱序残缺），已按该问题语境还原为 $M(s)$ 及标准切诺夫界改写；末行 $e^{-\phi(a)}$ 处 OCR 断行错位（出现负号游离），已规范合并。</span>

**(d)** For $s = 0$, we have

```math
sa - \ln M(s) = 0 - \ln 1 = 0,
```

where we have used the generic property $M(0) = 1$ of transforms. Furthermore,

```math
\left.\frac{d}{ds}\bigl( sa - \ln M(s) \bigr)\right|_{s=0}
= a - \left.\frac{M'(s)}{M(s)}\right|_{s=0}
= a - 1\cdot E[X] > 0 .
```

Since the function $sa - \ln M(s)$ is zero and has a positive derivative at $s = 0$, it must be positive when $s$ is positive and small. It follows that the maximum $\phi(a)$ of the function $sa - \ln M(s)$ over all $s \ge 0$ is also positive.

**(e)** For a standard normal random variable $X$, we have $M(s) = e^{s^2/2}$. Therefore, $sa - \ln M(s) = sa - s^2/2$. To maximize this expression over all $s \ge 0$, we form the derivative, which is $a - s$, and set it to zero, resulting in $s = a$. Thus, $\phi(a) = a^2/2$, which leads to the bound

```math
P(X \ge a) \le e^{-a^2/2}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上句「which leads to the bound」之后紧跟的显示不等式在 OCR 中缺失（空行），按上下文还原为 $P(X \ge a) \le e^{-a^2/2}$。若需最严格原文请回查原书页 286。</span>

Note: In the case where $a \le E[X]$, the maximizing value of $s$ turns out to be $s = 0$, resulting in $\phi(a) = 0$ and in the uninteresting bound

```math
P(X \ge a) \le 1 .
```

**(f)** Let $Y = X_1 + \cdots + X_n$. Using the result of part (c), we have

```math
P\!\left(\frac{Y}{n} \ge a\right) = P(Y \ge na) \le e^{-\phi_Y(na)},
```

where

```math
\phi_Y(na) = \max_{s \ge 0}\bigl( nsa - \ln M_Y(s) \bigr) ,
```

and

```math
M_Y(s) = E[e^{sY}]
```

> <span style="color:#7f8c8d;">注意：上式为源文行内补充「$M_Y(s) = E[e^{sY}]$ 是与 $Y$ 相关联的变换（the transform associated with $Y$）」，即英文原句「and $M_Y(s) = E[e^{sY}]$ is the transform associated with $Y$.」</span>

is the transform associated with $Y$. We have $\ln M_Y(s) = n \ln M(s)$, from which we obtain

```math
\phi_Y(na) = \max_{s \ge 0}\bigl( nsa - n\ln M(s) \bigr) = n \max_{s \ge 0}\bigl( sa - \ln M(s) \bigr) = n\phi(a),
```

> <span style="color:#7f8c8d;">[跨页续接] 本页以 $\phi_Y(na) = n\phi(a)$ 收尾；其后结论「$P(Y/n \ge a) \le e^{-n\phi(a)}$，即样本均值超过均值某量的概率随 $n$ 指数衰减」将在下一页（p296）续写。</span>
<!-- ===== PDF p296 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）—— 习题区（Problems，续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页页首为前一道习题（涉及 $E[X]$、函数 $\phi(\cdot)$ 与「第 (d) 问」的带 $*$ 题）英文 Solution 的收尾，故标「（续）」。页顶印页号在 OCR 中读作 `281`（本单元按版心页码定位约在 p287，此处 OCR 页码可能有误读，以正文内容为准）。</span>

承接上文（前一题英文 Solution 的末尾一段，带 $*$ 题故 Solution 保留英文）：

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏] 页首一段约三行公式碎片无法辨认（残字形如 `and`、`p`、`(;;t)`、`Xi:::a`、`:;, -n.(a)`），应为上一题 Solution 推导的尾部，无法还原完整，故以灰注释标注，不臆造。</span>

Note that when $a > E[X]$, part (d) asserts that $\phi(a) > 0$, so the probability of interest decreases exponentially with $n$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3\*（Jensen 不等式，Jensen inequality）**</span>

A twice differentiable real-valued function $J$ of a single variable is called convex if its second derivative $\dfrac{d^2 J}{dx^2}(x)$ is nonnegative for all $x$ in its domain of definition.

**(a)**
Show that the functions
$J(x) = e^{\,\theta x}$,
$J(x) = -\ln x$,
and
$J(x) = x^4$
are all convex.

**(b)**
Show that if $J$ is twice differentiable and convex, then the first order Taylor approximation of $J$ is an underestimate of the function, that is,

```math
J(a) + (x - a)\,\frac{d}{dx}J(a) \,\le\, J(x),
```

for every $a$ and $x$.

**(c)**
Show that if $J$ has the property in part (b), and if $X$ is a random variable, then

```math
J\bigl(E[X]\bigr) \,\le\, E\bigl[J(X)\bigr].
```

<span style="color:#2471a3;">**[solution]**</span> **Solution.**（解答）

**(a)**
We have

```math
\frac{d^2}{dx^2}\, e^{\,\theta x} = \theta^2 e^{\,\theta x} > 0,
```

```math
\frac{d^2}{dx^2}\, x^4 = 4 \cdot 3 \cdot x^2 \,\ge\, 0,
```

```math
\frac{d^2}{dx^2}\left(- \ln x\right) = \frac{1}{x^2} > 0.
```

**(b)**
Since the second derivative of $J$ is nonnegative, its first derivative must be nondecreasing. Using the fundamental theorem of calculus, we obtain

```math
J(x) = J(a) + \int_{a}^{x} J'(t)\, dt
\;\ge\; J(a) + \int_{a}^{x} J'(a)\, dt
= J(a) + (x - a)\, J'(a).
```

**(c)**
Since the inequality from part (b) is assumed valid for every possible value $x$ of the random variable $X$, we obtain

```math
J(a) + (X - a)\, J'(a) \,\le\, J(X).
```

We now choose $a = E[X]$ and take expectations, to obtain

```math
J\bigl(E[X]\bigr) + \bigl(E[X] - E[X]\bigr) J'\bigl(E[X]\bigr) \,\le\, E\bigl[J(X)\bigr],
```

or

```math
J\bigl(E[X]\bigr) \,\le\, E\bigl[J(X)\bigr].
```
<!-- ===== PDF p297 ===== -->

<span style="color:#c0392b;">**[section]** 第 5 章　极限定理（Limit Theorems）—— 习题区（Problems）续接</span>

> <span style="color:#7f8c8d;">页眉 Running Header：Limit Theorems（极限定理）　288　Chap. 5（第 5 章）。本页处于第 5 章习题区中部，承接第 296 页的问题编号（自 Problem 4 起），并按小节分组：页首为 §5.2（The Weak Law of Large Numbers，大数弱定律）的习题段，随后进入 §5.3（Convergence in Probability，依概率收敛）的习题段。</span>

<span style="color:#c0392b;">**[section]** SECTION 5.2. The Weak Law of Large Numbers（大数弱定律）</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4.**</span> In order to estimate $f$, the true fraction of smokers in a large population, Alvin selects $n$ people at random. His estimator is obtained by dividing $S_n$, the number of smokers in his sample, by $n$, i.e., $\hat{M}_n = S_n / n$. Alvin chooses the sample size $n$ to be the smallest possible number for which the Chebyshev inequality yields a guarantee that

```math
P\left(\left|\hat{M}_n - f\right| \ge \epsilon\right) \le \delta,
```

where $\epsilon$ and $\delta$ are some prespecified tolerances. Determine how the value of $n$ recommended by the Chebyshev inequality changes in the following cases.

(a) The value of $f$ is reduced to half its original value.

(b) The probability $\delta$ is reduced to half its original value.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 4 题干的保证式本身在 OCR 中未被识别（原句为「…yields a guarantee that … where $\epsilon$ and $\delta$ are some prespecified tolerances.」，其中 $\epsilon$ 与 $\delta$ 被误读为「€」与「6」）；上文按切比雪夫不等式的标准唤起式补为 $P(|\hat{M}_n - f| \ge \epsilon) \le \delta$，未臆造数值。</span>

---

<span style="color:#c0392b;">**[section]** SECTION 5.3. Convergence in Probability（依概率收敛）</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 5.**</span> Let $X_1, X_2, \ldots$ be independent random variables that are uniformly distributed over $[-1, 1]$. Show that the sequence $Y_1, Y_2, \ldots$ converges in probability to some limit, and identify the limit, for each of the following cases:

(a) $Y_n = X_n / n$.

(b) $Y_n = (X_n)^n$.

(c) $Y_n = X_1 \cdot X_2 \cdots X_n$.

(d) $Y_n = \max\{X_1, \ldots, X_n\}$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 6.\***</span> Consider two sequences of random variables $X_1, X_2, \ldots$ and $Y_1, Y_2, \ldots$, which converge in probability to some constants. Let $c$ be another constant. Show that $cX_n$, $X_n + Y_n$, $\max\{0, X_n\}$, $|X_n|$, and $X_n Y_n$ all converge in probability to corresponding limits.

<span style="color:#2471a3;">**[solution]**</span> **Solution.**（解答　属 Problem 6\*，英文原文保留）

Let $x$ and $y$ be the limits of $X_n$ and $Y_n$, respectively. Fix some $\epsilon > 0$ and a constant $c$. If $c = 0$, then $cX_n$ equals zero for all $n$, and convergence trivially holds. If $c \ne 0$, we observe that $P\left(|cX_n - cx| \ge \epsilon\right) = P\left(|X_n - x| \ge \epsilon/|c|\right)$, which converges to zero, thus establishing convergence in probability of $cX_n$.

We will now show that $P\left(|X_n + Y_n - x - y| \ge \epsilon\right)$ converges to zero, for any $\epsilon > 0$. To bound this probability, we note that for $|X_n + Y_n - x - y|$ to be as large as $\epsilon$, we need either $|X_n - x|$ or $|Y_n - y|$ (or both) to be at least $\epsilon/2$. Therefore, in terms of events, we have

```math
\{|X_n + Y_n - x - y| \ge \epsilon\}
\;\subseteq\;
\{|X_n - x| \ge \epsilon/2\} \cup \{|Y_n - y| \ge \epsilon/2\},
```

and hence

```math
P\left(|X_n + Y_n - x - y| \ge \epsilon\right)
\le P\left(|X_n - x| \ge \epsilon/2\right) + P\left(|Y_n - y| \ge \epsilon/2\right).
```

This implies that

```math
\lim_{n\to\infty} P\left(|X_n + Y_n - x - y| \ge \epsilon\right)
\le \lim_{n\to\infty} P\left(|X_n - x| \ge \epsilon/2\right)
+ \lim_{n\to\infty} P\left(|Y_n - y| \ge \epsilon/2\right)
= 0,
```

since the two sequences on the right-hand side both converge to zero.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页尾部的几处显示公式（事件包含关系及最终两条极限式，P 内下标 $X_n$、$Y_n$、$\epsilon/2$ 等字符）在 OCR 中被打成碎点与散乱字符，无法逐字还原；上文按标准推理链（事件包含关系 + union bound 夹逼 + 两边同取极限）补全为规范 LaTeX，未臆造含义。Problem 6 的 Solution 到此仍停留在「This implies that … = 0」的极限式，尚未收尾，Answer 翻页续至下一页。</span>
<!-- ===== PDF p298 ===== -->

<span style="color:#7f8c8d;">第 5 章　Limit Theorems（极限定理）—— 习题区（Problems），印页 289，为 p297 的习题编号序列续接（续）。</span>

> <span style="color:#7f8c8d;">[跨页续接] 本页顶部为上一页（p297）一枚带 `*` 题的英文 Solution 的续段——该证明展示 $\max\{0, X_n\}$、$|X_n|$ 与 $X_n Y_n$ 的依概率收敛，承接上一页同一证明的前段。本题为带 `*` 的习题，其英文 Solution 按规范保留英文原文。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（承接上一页，续）**

where the last equality follows since $X_n$ and $Y_n$ converge, in probability, to $x$ and $y$, respectively.

By a similar argument, it is seen that the event $\{ |\max\{0, X_n\} - \max\{0, x\}| \ge \epsilon \}$ is contained in the event $\{ |X_n - x| \ge \epsilon \}$. Since $\lim_{n\to\infty} P(|X_n - x| \ge \epsilon) = 0$, this implies that

> <span style="color:#7f8c8d;">[OCR 修复] 原行 "limoo P ( l max{O. Xn } - max{O, x}I 2: E ) = 0. n Hence ..." 中 `2:` 为 `≥`、`l...I` 为绝对值、`E` 为 $\epsilon$，且 "nHence" 系换行粘连，应按上述合并为 $\lim_{n\to\infty} P(|\max\{0,X_n\} - \max\{0,x\}| \ge \epsilon) = 0$。</span>

```math
\lim_{n\to\infty} P\!\left( |\max\{0, X_n\} - \max\{0, x\}| \ge \epsilon \right) = 0 .
```

Hence $\max\{0, X_n\}$ converges to $\max\{0, x\}$ in probability.

We have $|X_n| = \max\{0, X_n\} + \max\{0, -X_n\}$. Since $\max\{0, X_n\}$ and $\max\{0, -X_n\}$ converge, as shown earlier, it follows that their sum, $|X_n|$, converges to $\max\{0, x\} + \max\{0, -x\} = |x|$ in probability.

Finally, we have

```math
P\!\left( |X_n Y_n - xy| \ge \epsilon \right)
= P\!\left( |(X_n - x)(Y_n - y) + xY_n + yX_n - 2xy| \ge \epsilon \right)
```

```math
\le P\!\left( |(X_n - x)(Y_n - y)| \ge \epsilon/2 \right)
+ P\!\left( |xY_n + yX_n - 2xy| \ge \epsilon/2 \right).
```

Since $xY_n$ and $yX_n$ both converge to $xy$ in probability, the last probability in the above expression converges to $0$. It will thus suffice to show that

```math
\lim_{n\to\infty} P\!\left( |(X_n - x)(Y_n - y)| \ge \epsilon/2 \right) = 0 .
```

To bound this probability, we note that for $|(X_n - x)(Y_n - y)|$ to be as large as $\epsilon/2$, we need either $|X_n - x|$ or $|Y_n - y|$ (or both) to be at least $\sqrt{\epsilon/2}$. The rest of the proof is similar to the earlier proof that $X_n + Y_n$ converges in probability.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 7.***</span> A sequence $X_n$ of random variables is said to converge to a number $c$ **in the mean square**, if

```math
\lim_{n\to\infty} E\!\left[ (X_n - c)^2 \right] = 0 .
```

**(a)** Show that convergence in the mean square implies convergence in probability.

**(b)** Give an example that shows that convergence in probability does not imply convergence in the mean square.

<span style="color:#2471a3;">**[solution]**</span> **Solution.** **(a)** Suppose that $X_n$ converges to $c$ in the mean square. Using the Markov inequality, we have

```math
P\!\left( |X_n - c| \ge \epsilon \right) \le \frac{E\!\left[ (X_n - c)^2 \right]}{\epsilon^2} .
```

Taking the limit as $n \to \infty$, we obtain

```math
\lim_{n\to\infty} P\!\left( |X_n - c| \ge \epsilon \right) = 0 ,
```

which establishes convergence in probability.

**(b)** In Example 5.8, we have convergence in probability to $0$ but $E[Y_n^2] = n^3$, which diverges to infinity.
<!-- ===== PDF p299 ===== -->
<span style="color:#7f8c8d;">Limit Theorems（极限定理），Chap. 5，印页号 290。</span>

<span style="color:#c0392b;">**[section]** **SECTION 5.4　The Central Limit Theorem（中心极限定理）—— 第 5 章习题（Problems）区 · §5.4 习题段**</span>

> <span style="color:#7f8c8d;">页眉为「290 / Limit Theorems / Chap. 5」，本章 Problems 习题区内按小节分组，「SECTION 5.4. The Central Limit Theorem」为 §5.4 习题段的段首小节标题。习题编号承接 p298 的 Problem 7，本页自 Problem 8 续起。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 8（赌场轮盘的公平性检验）**</span>

Before starting to play the roulette in a casino, you want to look for biases that you can exploit. You therefore watch 100 rounds that result in a number between 1 and 36, and count the number of rounds for which the result is odd. If the count exceeds 55, you decide that the roulette is not fair. Assuming that the roulette is fair, find an approximation for the probability that you will make the wrong decision.

> <span style="color:#7f8c8d;">[原页此段 OCR 碎裂] "Problem 8." 的题号在本页 OCR 中被拆散并移位到本页中部（在 Problem 10 的 (b) 式与 (c) 之间游离出现一行「Problem 8.」），其正文即页首这段轮盘问题；此处按页序还原归位。原文以「rounds. and」出现，应为逗号「rounds, and」。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 9（操作系统每日崩溃概率）**</span>

During each day, the probability that your computer's operating system crashes at least once is 5%, independent of every other day. You are interested in the probability of at least 45 crash-free days out of the next 50 days.

(a) Find the probability of interest by using the normal approximation to the binomial.

(b) Repeat part (a), this time using the Poisson approximation to the binomial.

> <span style="color:#7f8c8d;">[原页此段 OCR 碎裂] OCR 将 (b) 中 "using" 误读为 "nsing"。题干「at least 45 crash-free days out of the next 50 days」意为「未来 50 天中至少有 45 天无崩溃」。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 10（工厂日产量与中心极限近似）**</span>

A factory produces $X_n$ gadgets on day $n$, where the $X_n$ are independent and identically distributed random variables, with mean 5 and variance 9.

(a) Find an approximation to the probability that the total number of gadgets produced in 100 days is less than 440.

(b) Find (approximately) the largest value of $n$ such that

```math
P(X_1 + \cdots + X_n \ge 200 + 5n) \le 0.05 .
```

(c) Let $N$ be the first day on which the total number of gadgets produced exceeds 1000. Calculate an approximation to the probability that $N \ge 220$.

> <span style="color:#7f8c8d;">[原页此段 OCR 碎裂] (b) 的待求不等式在 OCR 中被切成碎片，化为「P (X I + … + Xn 2: 200 + 5n) ::; 0.05」，即 $P(X_1 + \cdots + X_n \ge 200 + 5n) \le 0.05$；不等式朝向以语义还原（所求为「n 的最大值使其概率不超过 0.05」）。本页 OCR 在 (b) 式与 (c) 之间混入游离的「Problem 8.」行，已按 Problem 8 归位。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 11（单位区间均匀随机变量的 16 项和）**</span>

Let $X_1, X_2, \ldots, Y_1, Y_2, \ldots$ be independent random variables, uniformly distributed in the unit interval $[0,1]$, and let

```math
W = \frac{(X_1 + \cdots + X_{16}) - (Y_1 + \cdots + Y_{16})}{16} .
```

Find a numerical approximation to the quantity

```math
P\left( |W - E[W]| < 0.001 \right) .
```

> <span style="color:#7f8c8d;">[原页此段 OCR 碎裂] Problem 11 的 OCR 损坏严重：序列「Let $X_1, X_2, \ldots, Y_1, Y_2, \ldots$」被打散（OCR 作「X YI , X2 . Y2 .…」），$W$ 定义中的下标/分母「16」位置存疑，目标量被 OCR 成「p(I"" - E[ltV1 1 < 0.001)」，即 $P(|W - E[W]| < 0.001)$。此处 $W$ 的「$\frac{\ldots}{16}$」为按文意合理补全；若需最严格原文，请回查原书页 290。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 12\*　Proof of the central limit theorem（中心极限定理的证明）**</span>

**Proof of the central limit theorem.** Let $X_1, X_2, \ldots$ be a sequence of independent identically distributed zero-mean random variables with common variance $\sigma^2$, and associated transform $M_X(s)$. We assume that $M_X(s)$ is finite when $-d < s < d$, where $d$ is some positive number. Let $Z_n$ be the normalized sum $Z_n = (X_1 + \cdots + X_n)/(\sigma\sqrt{n})$.

(a) Show that the transform associated with $Z_n$ satisfies

```math
M_{Z_n}(s) = \left( M_X\left( \frac{s}{\sigma\sqrt{n}} \right) \right)^{\!n}.
```

> <span style="color:#7f8c8d;">[原页此段 OCR 碎裂] Problem 12\*（带 * 题，属于带英文 Solution 的选做/证明题）的陈述在整个页尾 OCR 中被切碎，碎片含「be a sequence」「of independent identically distributed zero-mean random variables with common variance $\sigma^2$」「associated transform」「is finite when」「$-d < s < d$，where $d$ is some positive number」「(a) Show that the transform associated with $Z_n$ satisfies」「$M_X(s)$」「$M_{Z_n}(s) =$」等。归一化和的定义 $Z_n = (X_1 + \cdots + X_n)/(\sigma\sqrt{n})$ 与 (a) 的变换关系 $M_{Z_n}(s) = \left(M_X\!\left(\frac{s}{\sigma\sqrt{n}}\right)\right)^{\!n}$ 为按中心极限定理的标准证明补全，签名/下标的精确朝向以本页未能完整呈现为据存疑。本页止于 (a) 的开头部分，以下续接至下一页。</span>

> <span style="color:#7f8c8d;">本页在 Problem 12\*(a) 处翻页截断，下一小问（及可能的英文 Solution）续至 p300。</span>

<!-- ===== PDF p299 / 印页号 290 END ===== -->
<!-- ===== PDF p300 ===== -->
<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — 习题区续接（Problems，续）

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 12\*（续）——中心极限定理的证明（Proof of the central limit theorem）**</span>

> <span style="color:#7f8c8d;">承接上一页：设 $X_1, X_2, \ldots$ 为独立同分布、均值为零、公共方差为 $\sigma^2$ 的随机变量序列，关联变换为 $M_X(s)$；令 $Z_n$ 为标准化样本和。此页续接该题的下列小问 (b)、(c)、Note，及其行内英文 Solution（本页为 Problem 12\* 中部，故标注「续」）。</span>

**(b)** Suppose that the transform $M_X(s)$ has a second order Taylor series expansion
around $s = 0$, of the form

```math
M_X(s) = a + bs + cs^2 + o(s^2),
```

where $o(s^2)$ is a function that satisfies $\lim_{s \to 0} o(s^2) / s^2 = 0$. Find $b$ and $c$ in terms of $\sigma^2$.

**(c)** Combine the results of parts (a) and (b) to show that the transform $M_{Z_n}(s)$
converges to the transform associated with a standard normal random variable,
that is,

```math
\lim_{n \to \infty} M_{Z_n}(s) = e^{s^2 / 2}, \qquad \text{for all } s.
```

**Note:** The central limit theorem follows from the result of part (c), together with the
fact (whose proof lies beyond the scope of this text) that if the transforms $M_{Z_n}(s)$
converge to the transform $M_Z(s)$ of a random variable $Z$ whose CDF is continuous,
then the CDFs $F_{Z_n}$ converge to the CDF of $Z$. In our case, this implies that the CDF
of $Z_n$ converges to the CDF of a standard normal.

<span style="color:#2471a3;">**[solution]**</span> **Solution.**

**(a)** We have, using the independence of the $X_i$,

```math
M_{Z_n}(s) = E\left[ e^{s Z_n} \right]
= E\left[ \exp\!\left( \frac{1}{\sigma\sqrt{n}} \sum_{i=1}^{n} s X_i \right) \right]
= \left( M_X\!\left( \frac{s}{\sigma\sqrt{n}} \right) \right)^n .
```

**(b)** Using the moment generating properties of the transform, we have

```math
a = M_X(0) = 1,
```

```math
b = \left. \frac{d}{ds} M_X(s) \right|_{s=0} = E[X] = 0,
```

```math
c = \frac{1}{2} \left. \frac{d^2}{ds^2} M_X(s) \right|_{s=0}
= \frac{E[X^2]}{2} = \frac{\sigma^2}{2}.
```

**(c)** We combine the results of parts (a) and (b). We have

```math
M_{Z_n}(s) = \left( M_X\!\left( \frac{s}{\sigma\sqrt{n}} \right) \right)^n
= \left( a + b\frac{s}{\sigma\sqrt{n}} + c\left( \frac{s}{\sigma\sqrt{n}} \right)^2
+ o\!\left( \frac{s^2}{\sigma^2 n} \right) \right)^n ,
```

and using the formulas for $a$, $b$, and $c$ from part (b), it follows that

```math
M_{Z_n}(s)
= \left( 1 + \frac{0\cdot s}{\sigma\sqrt{n}} + \frac{\sigma^2}{2}\cdot\frac{s^2}{\sigma^2 n}
+ o\!\left( \frac{s^2}{n} \right) \right)^n
= \left( 1 + \frac{s^2}{2n} + o\!\left( \frac{s^2}{n} \right) \right)^n ,
```

so that, letting $n \to \infty$,

```math
\lim_{n \to \infty} M_{Z_n}(s) = e^{s^2 / 2}, \qquad \text{for all } s.
```

> <span style="color:#7f8c8d;">[原页 OCR 说明] 本页（印页约 291）公式被 OCR 重排打散成碎片（如 $(M_X(s/(\sigma\sqrt{n})))^n$ 与 (c) 中代入 $a=1$, $b=0$, $c=\sigma^2/2$ 后的展开式残缺），上面按数学推导还原为规范 LaTeX，并据 p299 已给内容及题目标题确认为 **Problem 12\*** 的续页。中文与编号均以原书第 5 章 Problems 为准。</span>

> <span style="color:#7f8c8d;">§5.4 The Central Limit Theorem, p.290–291</span>
