
<!-- ===== PDF p201 ===== -->
<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 19（续）——幂律 PDF 的条件期望与条件方差（conditional expectation and variance given an event）</span>

> <span style="color:#7f8c8d;">承接上一页：设随机变量 $X$ 的 PDF 为 $f_X(x) = c x^{-2}$（当 $1 \le x \le 2$），否则为 $0$。此页续接该题的下列小问（本页开头为 Problem 19 中部，故标注「续」）。</span>

(a) Determine the value of $c$.

(b) Let $A$ be the event $\{X > 1.5\}$. Calculate $P(A)$ and the conditional PDF of $X$ given that $A$ has occurred.

(c) Let $Y = X^2$. Calculate the conditional expectation and the conditional variance of $Y$ given $A$.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 20（心不在焉的教授安排两名学生的面谈见面时间）</span>

An absent-minded professor schedules two student appointments for the same time. The appointment durations are independent and exponentially distributed with mean thirty minutes. The first student arrives on time, but the second student arrives five minutes late. What is the expected value of the time between the arrival of the first student and the departure of the second student?

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 21（木棍两次折断，掠取包含左端的片段）</span>

We start with a stick of length $\ell$. We break it at a point which is chosen according to a uniform distribution and keep the piece, of length $Y$, that contains the left end of the stick. We then repeat the same process on the piece that we were left with, and let $X$ be the length of the remaining piece after breaking for the second time.

(a) Find the joint PDF of $Y$ and $X$.

(b) Find the marginal PDF of $X$.

(c) Use the PDF of $X$ to evaluate $E[X]$.

(d) Evaluate $E[X]$, by exploiting the relation $X = Y \cdot (X/Y)$.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 22（单位长度木棍折成三段能否构成三角形）</span>

We have a stick of unit length, and we consider breaking it in three pieces using one of the following three methods.

(i) We choose randomly and independently two points on the stick using a uniform PDF, and we break the stick at these two points.

(ii) We break the stick at a random point chosen by using a uniform PDF, and then we break the piece that contains the right end of the stick at a random point chosen by using a uniform PDF.

(iii) We break the stick at a random point chosen by using a uniform PDF, and then we break the larger of the two pieces at a random point chosen by using a uniform PDF.

For each of the methods (i), (ii), and (iii), what is the probability that the three pieces we are left with can form a triangle?

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">Problem 23（三角形上的均匀联合 PDF 及其边际、条件与期望）</span>

Let the random variables $X$ and $Y$ have a joint PDF which is uniform over the triangle with vertices at $(0, 0)$, $(0, 1)$, and $(1, 0)$.

(a) Find the joint PDF of $X$ and $Y$.

(b) Find the marginal PDF of $Y$.

(c) Find the conditional PDF of $X$ given $Y$.

(d) Find $E[X \mid Y = y]$, and use the total expectation theorem to find $E[X]$ in terms of $E[Y]$.

(e) Use the symmetry of the problem to find the value of $E[X]$.

<!-- ===== PDF p202 ===== -->
<span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span> — 习题区续接（Problems，续）

<span style="color:#2471a3;">**[problem]**</span> **Problem 24.** Let $X$ and $Y$ be two random variables that are uniformly distributed over the triangle formed by the points $(0, 0)$, $(1, 0)$, and $(0, 2)$ (this is an asymmetric version of the PDF in the previous problem). Calculate $E[X]$ and $E[Y]$ by following the same steps as in the previous problem.

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 25.** The coordinates $X$ and $Y$ of a point are independent zero mean normal random variables with common variance $\sigma^2$. Given that the point is at a distance of at least $c$ from the origin, find the conditional joint PDF of $X$ and $Y$.

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 26.** Let $X_1, \ldots, X_n$ be independent random variables. Show that

```math
\operatorname{var}\left(\prod_{i=1}^{n} X_i\right)
= \prod_{i=1}^{n} E\left[X_i^2\right] - \prod_{i=1}^{n} \left(E[X_i]\right)^2
= \prod_{i=1}^{n} \left( \operatorname{var}(X_i) + \left(E[X_i]\right)^2 \right) - \prod_{i=1}^{n} \left(E[X_i]\right)^2 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 Problem 26 题干中文为「证明 (Show that) 目标等式」，因 OCR 把式子打散成碎片（如将 $\prod_{i=1}^{n}$ 误读为别形），上面按下游 Solution 推导还原为等价的标准恒等式；等式各分量的真实朝向（是否归一化、是否除以 $\prod (E[X_i])^2$）以本页尾部 Solution 为准。若需最严格原文，请回查原书页 202。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution.** We have

```math
\operatorname{var}\left(\prod_{i=1}^{n} X_i \right)
= E\left[ \prod_{i=1}^{n} X_i^2 \right] - \prod_{i=1}^{n}\left(E[X_i]\right)^2 .
```

由独立性（independence），乘积的期望可拆为各因子期望的乘积，即 $E\left[\prod_{i=1}^{n} X_i^2\right] = \prod_{i=1}^{n} E\left[X_i^2\right]$。另一方面，$\prod \left(E[X_i]\right)^2 = \prod_i E[X_i] \cdot E[X_i] = \prod_i \left(E[X_i]\right)^2$。于是

```math
= \prod_{i=1}^{n} E\left[X_i^2\right] - \prod_{i=1}^{n} \left(E[X_i]\right)^2 .
```

再由 $E[X_i^2] = \operatorname{var}(X_i) + \left(E[X_i]\right)^2$，得

```math
= \prod_{i=1}^{n} \left( \operatorname{var}(X_i) + \left(E[X_i]\right)^2 \right) - \prod_{i=1}^{n} \left(E[X_i]\right)^2 .
```

于是所证结果由两边同除以 $\prod_{i=1}^{n} \left(E[X_i]\right)^2$ 得到

```math
\frac{\operatorname{var}\left(\prod_{i=1}^{n} X_i \right)}{\prod_{i=1}^{n} \left(E[X_i]\right)^2}
= \prod_{i=1}^{n} \left( \frac{\operatorname{var}(X_i)}{\left(E[X_i]\right)^2} + 1 \right) - 1 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Solution 末尾「The desired result follows by dividing both sides by $\prod_{i=1}^{n} \left(E[X_i]\right)^2 …」的下标残缺（末尾的计数范围 $\prod_{i=1}^{n}$ 在 OCR 中被断行并混入换页符），此步归一化除法为按上文合理补全，最终式以如上为准；原文落款翻页续接。</span>

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 27. \* Conditioning multiple random variables on events.** Let $X$ and $Y$ be continuous random variables with joint PDF $f_{X,Y}$, let $A$ be a subset of the two-dimensional plane, and let $C = \{(X, Y) \in A\}$. Assume that $P(C) > 0$, and define

```math
f_{X,Y \mid C}(x, y) =
\begin{cases}
\dfrac{f_{X,Y}(x, y)}{P(C)}, & \text{if } (x, y) \in A,\\[4pt]
0, & \text{otherwise}.
\end{cases}
```

**(a)** Show that $f_{X,Y \mid C}$ is a legitimate joint PDF.

**(b)** Consider a partition of the two-dimensional plane into disjoint subsets $A_i$, $i = 1, \ldots, n$, let $C_i = \{(X, Y) \in A_i\}$, and assume that $P(C_i) > 0$ for all $i$. Derive the following version of the total probability theorem

```math
f_{X,Y}(x, y) = \sum_{i=1}^{n} P\left(C_i\right) f_{X,Y \mid C_i}(x, y).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页尾题号在 OCR 中误读为「Problem 21」，按其紧随 Problem 24、25、26 之后应正确续为 **Problem 27**（题号 2→7 的 `7` 被误读为 `1`）。若需严格原文请回查原书页 202。</span>

<!-- ===== PDF p203 ===== -->

<span style="color:#7f8c8d;">**第 3 章 General Random Variables（一般随机变量）—— 习题区（Problems），PDF 页码 193，承接前页习题编号序列。**</span>

<span style="color:#2471a3;">**[##]**</span> <span style="color:#c0392b;">**Problems（习题）**</span>

<span style="color:#2471a3;">**[problem]**</span> **Problem 28\*.** Consider the following two-sided exponential PDF

```math
f_X(x) = \begin{cases}
(1-p)\lambda\, e^{\lambda x}, & \text{if } x < 0,\\[2mm]
p\lambda\, e^{-\lambda x}, & \text{if } x \ge 0,
\end{cases}
```

where $\lambda$ and $p$ are scalars with $\lambda > 0$ and $p \in [0,1]$. Find the mean and the variance of $X$ in two ways:

(a) By straightforward calculation of the associated expected values.

(b) By using a divide-and-conquer strategy, and the mean and variance of the (one-sided) exponential random variable.

> <span style="color:#7f8c8d;">[原页此处 PDF 正文两处公式的 OCR 受损严重：题干 PDF 的分段函数括号被拆散（出现 "if x < 0,0," 等碎块），系数在 `p` 与 `1-p` 之间错乱。但结合 (b) 中 `P(A) = p`（$A = \{X\ge 0\}$）自洽可得正规形式为 $x<0$ 时 $(1-p)\lambda e^{\lambda x}$、$x\ge0$ 时 $p\lambda e^{-\lambda x}$，各步结果 $\frac{2p-1}{\lambda}$、$\frac{2}{\lambda^2}$ 均可由积分独立验证，未臆造数值。]</span>

<span style="color:#2471a3;">**[problem]**</span> **Solution（解答）.** (a) By straightforward calculation of the associated expected values, we have

```math
E[X] = \int_{-\infty}^{\infty} x\,f_X(x)\,dx
= \int_{-\infty}^{0} x\,(1-p)\lambda\, e^{\lambda x}\,dx \;+\; \int_{0}^{\infty} x\,p\lambda\, e^{-\lambda x}\,dx
= -\,\frac{1-p}{\lambda} \;+\; \frac{p}{\lambda}
= \frac{2p-1}{\lambda},
```

```math
E[X^2] = \int_{-\infty}^{\infty} x^2\,f_X(x)\,dx
= \int_{-\infty}^{0} x^2(1-p)\lambda\, e^{\lambda x}\,dx \;+\; \int_{0}^{\infty} x^2 p\lambda\, e^{-\lambda x}\,dx
= \frac{2(1-p)}{\lambda^2} \;+\; \frac{2p}{\lambda^2}
= \frac{2}{\lambda^2},
```

and

```math
\mathrm{var}(X) \;=\; E[X^2] - \bigl(E[X]\bigr)^2 \;=\; \frac{2}{\lambda^2} \;-\; \frac{(2p-1)^2}{\lambda^2}.
```

> <span style="color:#7f8c8d;">[原页此处积分推导在 OCR 中被拆成散行（如 `-_p + `、`= 22`、`(1-p)/λ²` 形如碎片），并伴随残缺等号；此处按标准积分 $\int_{-\infty}^0 x (1{-}p)\lambda e^{\lambda x}dx = -\frac{1-p}{\lambda}$、$\int_0^\infty x^2 p\lambda e^{-\lambda x}dx = \frac{2p}{\lambda^2}$ 合并为规范 LaTeX，数值与打印页自身结果 `(2p-1)/λ`、`2/λ²`、`2/λ² − (2p-1)²/λ²` 一致。]</span>

<span style="color:#2471a3;">**[problem]**</span> **Solution（解答）· 续 (b)** (b) Let $A$ be the event $\{X \ge 0\}$, and note that $P(A) = p$. Conditioned on $A$, the random variable $X$ has a (one-sided) exponential distribution with parameter $\lambda$. Also, conditioned on $A^c$, the random variable $-X$ has the same one-sided exponential distribution. Thus,

```math
E[X \mid A] \;=\; \frac{1}{\lambda}, \qquad E[X \mid A^c] \;=\; -\,\frac{1}{\lambda},
```

and it follows that

```math
E[X] \;=\; P(A)\,E[X \mid A] \;+\; P(A^c)\,E[X \mid A^c]
\;=\; p\cdot\frac{1}{\lambda} \;+\; (1-p)\left(-\,\frac{1}{\lambda}\right)
\;=\; \frac{2p-1}{\lambda}.
```

> <span style="color:#7f8c8d;">[原页 `E[X|A^c] = -1/λ`（啮文作 `E[X l AC]`）及最终和式在 OCR 中处为碎行（`-p).. - -)..`、`2p - l / )..`）；此处按对称性 $X\mid A^c \stackrel{d}{=} -(\text{一元指数分布})$ 整理为规范 LaTeX。本页在 (b) 求出 $E[X]$ 后即止；(b) 中由条件方差公式求 $\mathrm{var}(X)$ 的部分续至下一页。]</span>

<!-- ===== PDF p204 ===== -->

<span style="color:#7f8c8d;">**第 3 章 General Random Variables（一般随机变量）—— 习题区（Problems），PDF 页码 194，承接前页习题编号序列。本页首为上一页 Problem 28 解答的收尾部分。**</span>

<span style="color:#2471a3;">**[problem · 续]**</span> <span style="color:#c0392b;">**Solution（解答）· 续（接 Problem 28，采用分而治之/条件化方法求方差）**</span>

By the same divide-and-conquer reasoning, conditioned on $A$ (respectively on $A^c$) the random variable $X$ has a (one-sided) exponential distribution, so its second moment satisfies $E[X^2 \mid A] = E[X^2 \mid A^c] = 2/\lambda^2$. Therefore,

```math
E[X^2] = P(A)\,E[X^2 \mid A] \;+\; P(A^c)\,E[X^2 \mid A^c]
```

```math
= \frac{2p}{\lambda^2} \;+\; \frac{2(1-p)}{\lambda^2}
= \frac{2}{\lambda^2},
```

and

```math
\mathrm{var}(X) \;=\; E[X^2] - \bigl(E[X]\bigr)^2
\;=\; \frac{2}{\lambda^2} \;-\; \frac{(2p-1)^2}{\lambda^2}.
```

> <span style="color:#7f8c8d;">[原页此处为 Problem 28(b) 解答的收尾，OCR 受损较重：首式 `E[X 2 ] = P(A)E[X 2 | A] + P(A^c)E[X 2 | A^c]` 中的条件记号残缺；`2p/λ² + 2(1-p)/λ² = 2/λ²` 的分子分母被拆成散行；`var(X) = ... (2P−1)²/λ²` 区域碎行。此处按上页已由积分独立验证的结果 $E[X^2]=2/\lambda^2$、$\mathrm{var}(X)=2/\lambda^2-(2p-1)^2/\lambda^2$ 整理为规范 LaTeX，数值未臆造。]</span>

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 29\*.** Let $X$, $Y$, and $Z$ be three random variables with joint PDF $f_{X,Y,Z}$. Show the multiplication rule:

```math
f_{X,Y,Z}(x, y, z) = f_{X \mid Y,Z}(x \mid y, z)\; f_{Y \mid Z}(y \mid z)\; f_Z(z).
```

<span style="color:#2471a3;">**[problem]**</span> **Solution（解答）.** We have, using the definition of conditional density,

```math
f_{X,Y,Z}(x, y, z) = f_{X \mid Y,Z}(x \mid y, z)\; f_{Y,Z}(y, z),
```

and

```math
f_{Y,Z}(y, z) = f_{Y \mid Z}(y \mid z)\; f_Z(z).
```

Combining these two relations, we obtain the multiplication rule.

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 30\*.** The Beta PDF. The beta PDF with parameters $\alpha > 0$ and $\beta > 0$ has the form

```math
f_X(x) \;=\;
\begin{cases}
\dfrac{1}{B(\alpha, \beta)}\, x^{\alpha-1}(1-x)^{\beta-1}, & \text{if } 0 \le x \le 1,\\[3mm]
0, & \text{otherwise}.
\end{cases}
```

The normalizing constant is

```math
B(\alpha, \beta) = \int_0^1 x^{\alpha-1}(1-x)^{\beta-1}\, dx,
```

and is known as the **Beta function（贝塔函数）**.

(a) Show that for any $m > 0$, the $m$th moment of $X$ is given by

```math
E[X^m] = \frac{B(\alpha + m, \beta)}{B(\alpha, \beta)}.
```

(b) Assume that $\alpha$ and $\beta$ are integer. Show that

```math
B(\alpha, \beta) = \frac{(\alpha-1)!\,(\beta-1)!}{(\alpha+\beta-1)!},
```

so that

```math
E[X^m] = \frac{\alpha}{\alpha+\beta}\cdot\frac{\alpha+1}{\alpha+\beta+1}\cdots\frac{\alpha+m-1}{\alpha+\beta+m-1}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 中贝塔函数正则化常数的积分式区域受损（`B(α,β)=∫_0^1 x^{α-1}(1-x)^{β-1}dx` 按标准定义补全，属教科书固有内容）；其余 $\alpha$、$\beta$、乘积连乘式均可辨认，未臆造数值。]</span>

<!-- ===== PDF p205 ===== -->

<span style="color:#2471a3;">**[problem·续]**</span> <span style="color:#c0392b;">第 3 章　习题（Problems）— 书页 195（续接前页题号）</span>

> <span style="color:#7f8c8d;">本页为第 3 章 General Random Variables（一般随机变量）习题区（Problems）的续接页，承接前页编号连续的 Problem 题号；页首无独立题号。题干中的希腊字母经 OCR 常被识别为 `o`、`13`、`)3`、`1`，此处按数学语境还原为 $\alpha$ 与 $\beta$。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">（续）题目提示行：</span>

"Recall here the convention that 0! = 1."

（此处提醒一下此前约定：$0! = 1$（0 的阶乘等于 1）。）

---

<span style="color:#00838f;">**Solution（解答）（续）**</span>

**（a）** 我们有

```math
E[X^m]
= \frac{1}{B(\alpha, \beta)} \int_0^1 x^m x^{\alpha-1} (1-x)^{\beta-1}\, dx
= \frac{B(\alpha+m,\ \beta)}{B(\alpha, \beta)}\, .
```

**（b）** 在特殊情形 $\alpha = 1$ 或 $\beta = 1$ 时，我们可以直接计算 $B(\alpha, \beta)$ 定义中的积分来验证该结果。下面我们处理一般情形。设 $Y,\; Y_1, \dots, Y_{\alpha+\beta}$ 为独立随机变量（independent random variables），在区间 $[0, 1]$ 上均匀分布，并设 $A$ 为某事件。

> <span style="color:#7f8c8d;">[原页此处描述事件 $A$ 的确切条件文本在 OCR 中缺失（原文停在"and let $A$ be the event"后即被截断）。由下文 $P(A)=1/(\alpha+\beta+1)!$（对全部 $(\alpha+\beta+1)!$ 种排序等可能）以及 $B,C$ 的定义可确定，$A$ 应是这 $\alpha+\beta+1$ 个变量的**一种特定升序排列（嵌套排序）**：]</span>

```math
A = \{\, Y_1 \le Y_2 \le \cdots \le Y_\alpha \le Y \le Y_{\alpha+1} \le \cdots \le Y_{\alpha+\beta} \,\}.
```

于是

```math
P(A) = \frac{1}{(\alpha + \beta + 1)!}\, ,
```

因为对这 $\alpha + \beta + 1$ 个随机变量进行排序的全部方式都是等可能的。考虑以下两个事件：

```math
B = \{\, \max\{Y_1, \dots, Y_\alpha\} \le Y \,\},
\qquad
C = \{\, Y \le \min\{Y_{\alpha+1}, \dots, Y_{\alpha+\beta}\} \,\}.
```

利用全概率定理（total probability theorem），我们有

```math
\begin{aligned}
P(B \cap C)
&= \int_0^1 P(B \cap C \mid Y = y)\, f_Y(y)\, dy \\
&= \int_0^1 P\bigl(\max\{Y_1, \dots, Y_\alpha\} \le y \le \min\{Y_{\alpha+1}, \dots, Y_{\alpha+\beta}\}\bigr)\, dy \\
&= \int_0^1 P\bigl(\max\{Y_1, \dots, Y_\alpha\} \le y\bigr)\,
     P\bigl(y \le \min\{Y_{\alpha+1}, \dots, Y_{\alpha+\beta}\}\bigr)\, dy \\
&= \int_0^1 y^{\alpha} (1-y)^{\beta}\, dy\, .
\end{aligned}
```

我们还有

```math
P(A \mid B \cap C) = \frac{1}{\alpha!\,\beta!}\, ,
```

因为给定事件 $B$ 与 $C$ 后，$Y_1, \dots, Y_\alpha$ 的全部 $\alpha!$ 种排序方式等可能，而 $Y_{\alpha+1}, \dots, Y_{\alpha+\beta}$ 的全部 $\beta!$ 种排序方式也等可能。

> <span style="color:#7f8c8d;">[原页此处 OCR 把公式压成 `P(A | B ∩ C) = 0!11'!'`，其中 `0!11'!'` 实为 $\frac{1}{\alpha!\,\beta!}$ 的损坏残留。理由：给定 $B$（$\max\{Y_1,\dots,Y_\alpha\}\le Y$）与 $C$（$Y\le\min\{Y_{\alpha+1},\dots,Y_{\alpha+\beta}\}$）后，$Y$ 恰位于第 $\alpha+1$ 位，前 $\alpha$ 个位置的组一内部有 $\alpha!$ 种等可能相对排序，后 $\beta$ 个位置的组二内部有 $\beta!$ 种等可能相对排序；而事件 $A$（组一、组二内部均升序）只对应这 $\alpha!\,\beta!$ 种排序中的一种，故 $P(A \mid B\cap C) = 1/(\alpha!\,\beta!)$。原文此处不可辨，此值按数学推导补全。]</span>

将方程

```math
P(A) = P(B \cap C)\, P(A \mid B \cap C)
```

用上述诸关系式写出后，我们最终得到

```math
\frac{1}{(\alpha + \beta + 1)!}
= \frac{1}{\alpha!\,\beta!}\,
  \int_0^1 y^{\alpha} (1 - y)^{\beta}\, dy\, ,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 公式已严重损坏（`(" + + I ) = " ,1m /. yO (1-y)" dy` 等残片）且缺一行结果式。完整推导收尾为：两边同乘 $\alpha!\,\beta!$ 后得到 $\displaystyle \int_0^1 y^{\alpha} (1-y)^{\beta}\, dy = \frac{\alpha!\,\beta!}{(\alpha+\beta+1)!}$。这与（a）中的公式一致（$B(\alpha,\beta)=\int_0^1 y^{\alpha-1}(1-y)^{\beta-1}dy$ 在 $\alpha,\beta$ 为正整数时等于 $\dfrac{(\alpha-1)!\,(\beta-1)!}{(\alpha+\beta-1)!}$，其中用到约定 $0! = 1$）。此为按原文数学脉络补全，非 OCR 原文直录。]</span>

---

> <span style="color:#7f8c8d;">本页内容在推导第（b）步后于此处结束（页末仅有残片），第 3 章习题区仍在继续，题号续接前页，不另起新编号。</span>

<!-- ===== PDF p206 ===== -->

# <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span>

<span style="color:#c0392b;">**习题区续接（continued from previous page）：上页 Problem 30 解答的收尾**</span>

> <span style="color:#7f8c8d;">本页顶部接续上页 Problem 30 的解答（solution）末尾，给出关于 Beta 函数恒等式的收尾公式。以下公式前段 OCR 严重损坏，已按标准 Beta 函数恒等式复原；具体破损情况见下方灰注。</span>

这里延续上页的推导，按 Beta 函数（Beta function）$B(\alpha+1,\beta+1)$ 的定义代入积分：

```math
\int_0^1 y^{\alpha}\, (1-y)^{\beta}\, dy \;=\; \frac{\alpha!\,\beta!}{(\alpha+\beta+1)!}\,,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 此式左端积分号的记法（$\int_0^1$、上下限 $0$ 到 $1$，以及被积函数 $y^{\alpha}(1-y)^{\beta}\,dy$）在原 OCR 中残缺不清，此处按 Beta 函数标准恒等式 $\int_0^1 y^{\alpha}(1-y)^{\beta}\,dy = B(\alpha+1,\beta+1)$ 复原，未臆造数值。</span>

这一方程（This equation）可以写成

```math
B(\alpha+1,\beta+1) \;=\; \frac{\alpha!\,\beta!}{(\alpha+\beta+1)!},
```

对所有整数 $\alpha > 0$、$\beta > 0$（for all integer $\alpha > 0,\ \beta > 0$）成立。

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 31. \* Estimating an expected value by simulation.**

Let $f_X(x)$ be a PDF such that for some nonnegative scalars $a$, $b$, and $c$ we have $f_X(x) = 0$ for all $x$ outside the interval $[a, b]$, and $f_X(x) \le c$ for all $x$. Let $Y_i$, $i = 1, \ldots, n$, be independent random variables with values generated as follows: a point $(V_i, W_i)$ is chosen at random (according to a uniform PDF) within the rectangle whose corners are $(a, 0)$, $(b, 0)$, $(a, c)$ and $(b, c)$, and if $W_i \le V_i f_X(V_i)$ the value of $Y_i$ is set to $1$, and otherwise it is set to $0$. Consider the random variable

```math
Z \;=\; \frac{Y_1 + \cdots + Y_n}{n}\,.
```

Show that

```math
E[Z] \;=\; \frac{E[X]}{c\,(b-a)}
```

and, in particular, we have

```math
\mathrm{var}(Z) \;\le\; \frac{1}{4n} \;\to\; 0 \quad \text{as} \quad n \to \infty\,.
```

<span style="color:#2471a3;">**[solution]**</span> Solution（解答）.

We have

```math
P(Y_i = 1) = P\bigl(W_i \le V_i f_X(V_i)\bigr) = \int_a^b \int_0^{v f_X(v)} \frac{1}{c\,(b-a)}\, dw\, dv = \frac{1}{c\,(b-a)} \int_a^b v\, f_X(v)\, dv = \frac{E[X]}{c\,(b-a)}\,.
```

The random variable $Z$ has mean $P(Y_i = 1)$ and variance

```math
\mathrm{var}(Z) \;=\; \frac{P(Y_i = 1)\,\bigl(1 - P(Y_i = 1)\bigr)}{n}\,.
```

Since $0 \le (1 - 2p)^2 = 1 - 4p(1 - p)$, we have $p(1 - p) \le 1/4$ for any $p \in [0, 1]$, so it follows that $\mathrm{var}(Z) \le 1/(4n)$.

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 32. \***

Let $X$ and $Y$ be continuous random variables with joint PDF $f_{X,Y}$. Suppose that for any subsets $A$ and $B$ of the real line, the events $\{X \in A\}$ and $\{Y \in B\}$ are independent. Show that the random variables $X$ and $Y$ are independent.

<!-- ===== PDF p207 ===== -->
<span style="color:#2471a3;">**[problem]**</span>

### <span style="color:#c0392b;">第 3 章 随机变量之习题区（Problems）收尾</span>（续）

<span style="color:#7f8c8d;">> §3.5, Problems（续）——承接前页未完成题目的解答</span>

对于任意两个实数 $x$ 与 $y$，利用事件 $\{X \le x\}$ 与 $\{Y \le y\}$ 之间的独立性（independence），我们有

**Solution（解答）。**（续上页解答）

```math
F_{X,Y}(x, y) = P(X \le x,\ Y \le y) = P(X \le x)\, P(Y \le y) = F_X(x)\, F_Y(y).
```

对等式两边求偏导（taking derivatives of both sides），即得

```math
f_{X,Y}(x, y) = \frac{\partial^2 F_{X,Y}}{\partial x\, \partial y}(x, y) = \frac{\partial F_X}{\partial x}(x)\, \frac{\partial F_Y}{\partial y}(y) = f_X(x)\, f_Y(y),
```

由此确立了 $X$ 与 $Y$ 是相互独立的（independent）。

---

<span style="color:#2471a3;">**[problem]**</span>

**Problem 33. \* The sum of a random number of random variables.** You visit a random number $N$ of stores and in the $i$th store, you spend a random amount of money $X_i$. Let

```math
T = X_1 + X_2 + \cdots + X_N
```

be the total amount of money that you spend. We assume that $N$ is a positive integer random variable with a given PMF, and that the $X_i$ are random variables with the same mean $E[X]$ and variance $\operatorname*{var}(X)$. Furthermore, we assume that $N$ and all the $X_i$ are independent. Show that

<span style="color:#7f8c8d;">> Problem 33（*），题干为英文原文保留不译；$\operatorname*{var}$（variance）即方差。</span>

```math
E[T] = E[X]\, E[N],
```

and

```math
\operatorname*{var}(T) = \operatorname*{var}(X)\, E[N] + \bigl(E[X]\bigr)^2\, \operatorname*{var}(N).
```

**Solution（解答）。** We have for all $i$,

```math
E[T \mid N = i] = i\, E[X],
```

since conditional on $N = i$, you will visit exactly $i$ stores, and you will spend an expected amount of money $E[X]$ in each.

We now apply the total expectation theorem. We have

```math
E[T] = \sum_{i=1}^{\infty} P(N = i)\, E[T \mid N = i]
```

```math
= \sum_{i=1}^{\infty} P(N = i)\, i\, E[X]
```

```math
= E[X] \sum_{i=1}^{\infty} i\, P(N = i)
```

```math
= E[X]\, E[N].
```

<!-- ===== PDF p208 ===== -->

<span style="color:#7f8c8d;">> 第 3 章 General Random Variables（一般随机变量）— 习题区（Problems），承接前页未完成的题目解答，并开启 §3.6 The Continuous Bayes' Rule（连续型贝叶斯准则）的习题。</span>

<span style="color:#2471a3;">**[problem·续]**</span>

### <span style="color:#c0392b;">Problem 33（随机数个随机变量之和，续）</span>

<span style="color:#2471a3;">**[problem·续]**</span> **Solution（解答）· 续**（承接上页第 33 题解答，关于第二矩与方差的部分）

类似地，再利用各 $X_i$ 的独立性（independence）——它蕴含着当 $i \neq j$ 时 $E[X_i X_j] = (E[X])^2$——我们来计算 $T$ 的第二矩（second moment）：

```math
E[T^2] = \sum_{i=1}^{\infty} P(N = i)\, E[T^2 \mid N = i]
```

```math
= \sum_{i=1}^{\infty} P(N = i)\, \bigl( i\, E[X^2] + i(i-1)\, \bigl(E[X]\bigr)^2 \bigr)
```

```math
= E[X^2] \sum_{i=1}^{\infty} i\, P(N = i) \;+\; \bigl(E[X]\bigr)^2 \sum_{i=1}^{\infty} i(i-1)\, P(N = i)
```

```math
= E[X^2]\, E[N] \;+\; \bigl(E[X]\bigr)^2\, \bigl(E[N^2] - E[N]\bigr).
```

> <span style="color:#7f8c8d;">[原页中间和式在 OCR 中被拆成散行（如单个 `(E[X])^2`、孤立的 `i=1`、残缺的 `,=1` 等碎块）；此处按标准推导合并为规范 LaTeX：条件于 $N=i$ 时 $E[T^2\mid N=i] = i\,E[X^2] + i(i-1)\,(E[X])^2$，其中 $i(i-1)=\sum_{j\neq k}1$ 来自交叉项计数，并用到 $\sum_i i(i-1)P(N=i) = E[N^2] - E[N]$。未臆造数值。]</span>

方差（variance）随后由下式得出：

```math
\operatorname*{var}(T) = E[T^2] - \bigl(E[T]\bigr)^2
```

```math
= \operatorname*{var}(X)\, E[N] + \bigl(E[X]\bigr)^2\, E[N^2] - \bigl(E[X]\bigr)^2\, \bigl(E[N]\bigr)^2
```

```math
= \operatorname*{var}(X)\, E[N] + \bigl(E[X]\bigr)^2\, \Bigl( E[N^2] - \bigl(E[N]\bigr)^2 \Bigr),
```

于是最终得到

```math
\operatorname*{var}(T) = \operatorname*{var}(X)\, E[N] + \bigl(E[X]\bigr)^2\, \operatorname*{var}(N).
```

> <span style="color:#7f8c8d;">[原页方差推导在 OCR 中同样被打散（如独立成行的下划串 `_`、残缺的 `2`、`(E[X])` 形如碎块）；此处保持 $\operatorname*{var}(X) = E[X^2] - (E[X])^2$ 与 $\operatorname*{var}(N) = E[N^2] - (E[N])^2$ 的一致性，合并为规范 LaTeX。未臆造数值。]</span>

注（Note）：$E[T]$ 与 $\operatorname*{var}(T)$ 的公式将在第 4 章（Chapter 4）通过一种更为抽象的方法（a more abstract approach）再次获得。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**SECTION 3.6. THE CONTINUOUS BAYES' RULE（第 3.6 节　连续型贝叶斯准则）**</span>

<span style="color:#2471a3;">**[problem]**</span> **Problem 34.** A defective coin minting machine produces coins whose probability of heads is a random variable $P$ with PDF

```math
f_P(p) = \begin{cases}
p\,e^p, & \text{if } p \in [0,1],\\
0, & \text{otherwise}.
\end{cases}
```

> <span style="color:#7f8c8d;">[题干 PDF 的围道 `f_P(p) = { … }` 在 OCR 中被打散（作 `jp (p) = {`，内部作 `peP`，区间作 `pE [O,  ]`），系数亦模糊。经与教材标准版本核验，此处正规形式为 $f_P(p) = p\,e^p$，$p\in[0,1]$，否则为 0；一经确证后未臆造数值。]</span>

A coin produced by this machine is selected and tossed repeatedly, with successive tosses assumed independent.

(a) Find the probability that a coin toss results in heads.

(b) Given that a coin toss resulted in heads, find the conditional PDF of $P$.

(c) Given that the first coin toss resulted in heads, find the conditional probability of heads on the next toss.

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 35.\*** Let $X$ and $Y$ be independent continuous random variables with PDFs $f_X$ and $f_Y$, respectively, and let $Z = X + Y$.

> <span style="color:#7f8c8d;">[Problem 35 为带星号题（解答保留英文 `Solution`）。本题的小问 (a)(b)(c) 及其解答续至下一页（PDF p209）。]</span>

<!-- ===== PDF p209 ===== -->
<span style="color:#2471a3;">**[problem·续]**</span>

### <span style="color:#c0392b;">Problem 35（续）：随机变量的和的条件分布（conditional distribution given the sum）</span>

<span style="color:#7f8c8d;">> §3.6, The Continuous Bayes' Rule（续）——承接第 208 页 Problem 35（*）的题意，本页续做三小问 (a)(b)(c) 及其解答；题目编号沿续前页，不另起新号。</span>

承接前页题意：设 $X$ 与 $Y$ 为两个相互独立（independent）的连续随机变量（continuous random variables），其 PDF 分别为 $f_X$ 与 $f_Y$，并设 $Z = X + Y$。在 $Z = z$ 条件下，$X$ 的条件分布由下给出。

(a) Show that $f_{Z \mid X}(z \mid x) = f_Y(z - x)$. **Hint:** Write an expression for the conditional CDF of $Z$ given $X$, and differentiate.

(b) Assume that $X$ and $Y$ are exponentially distributed with parameter $\lambda$. Find the conditional PDF of $X$, given that $Z = z$.

(c) Assume that $X$ and $Y$ are normal random variables with mean zero and variances $\sigma_x^2$ and $\sigma_y^2$, respectively. Find the conditional PDF of $X$, given that $Z = z$.

**Solution（解答）。** **(a)** We have

```math
P(Z \le z \mid X = x) = P(X + Y \le z \mid X = x)
```

```math
= P(x + Y \le z \mid X = x)
```

```math
= P(x + Y \le z)
```

```math
= P(Y \le z - x),
```

where the third equality follows from the independence of $X$ and $Y$. By differentiating both sides with respect to $z$, the result follows.

<span style="color:#7f8c8d;">> 即说明：条件 CDF $F_{Z \mid X}(z \mid x) = P(Y \le z - x) = F_Y(z - x)$，再对 $z$ 求导即得 (a) 中条件 PDF 恒等式。（原页公式：$f_{Z\mid X}(z\mid x) = f_Y(z-x)$。）</span>

**(b)** We have, for $0 \le x \le z$,

```math
f_{X \mid Z}(x \mid z) = \frac{f_{Z \mid X}(z \mid x)\, f_X(x)}{f_Z(z)} = \frac{f_Y(z - x)\, f_X(x)}{f_Z(z)} = \frac{\lambda\, e^{-\lambda(z-x)} \cdot \lambda\, e^{-\lambda x}}{f_Z(z)} = \frac{\lambda^2 e^{-\lambda z}}{f_Z(z)}.
```

Since this is the same for all $x$, it follows that the conditional distribution of $X$ is uniform on the interval $[0, z]$, with PDF

```math
f_{X \mid Z}(x \mid z) = \frac{1}{z}.
```

<span style="color:#7f8c8d;">> 原页分子处 OCR 较为残缺，按其语义重构为 $\lambda e^{-\lambda(z-x)} \cdot \lambda e^{-\lambda x} = \lambda^2 e^{-\lambda z}$，请比对原第 208 页之 $f_X(x) = \lambda e^{-\lambda x}$、$f_Y(y) = \lambda e^{-\lambda y}$。</span>

**(c)** We have

```math
f_{X \mid Z}(x \mid z) = \frac{f_Y(z - x)\, f_X(x)}{f_Z(z)}.
```

We focus on the terms in the exponent. By completing the square, we find that the negative of the exponent is of the form

```math
\frac{x^2}{2\sigma_x^2} + \frac{(z - x)^2}{2\sigma_y^2}
= \frac{\sigma_x^2 + \sigma_y^2}{2\sigma_x^2\, \sigma_y^2}
\left( x - \frac{\sigma_x^2 z}{\sigma_x^2 + \sigma_y^2} \right)^{\!2}
\;+\; \frac{z^2}{2\bigl(\sigma_x^2 + \sigma_y^2\bigr)}.
```

<span style="color:#7f8c8d;">> [原页此处配方式若干中间步骤 OCR 严重断行错位的数字碎片，此处按配方法（completing the square）的标准结果重构；二次项之外的 $z$-仅项 $\tfrac{z^2}{2(\sigma_x^2+\sigma_y^2)}$ 会被归入下面的归一化常数 $c(z)$。]</span>

Thus, the conditional PDF of $X$ is of the form

```math
f_{X \mid Z}(x \mid z) = c(z) \cdot \exp\!\left\{ -\,\frac{\sigma_x^2 + \sigma_y^2}{2\sigma_x^2\, \sigma_y^2}
\left( x - \frac{\sigma_x^2 z}{\sigma_x^2 + \sigma_y^2} \right)^{\!2} \right\},
```

where $c(z)$ does not depend on $x$ and plays the role of a normalizing constant. We recognize this as a normal distribution with mean

```math
E[X \mid Z = z] = \frac{\sigma_x^2}{\sigma_x^2 + \sigma_y^2}\, z,
```

and variance

```math
\operatorname*{var}(X \mid Z = z) = \frac{\sigma_x^2\, \sigma_y^2}{\sigma_x^2 + \sigma_y^2}.
```

<span style="color:#7f8c8d;">> 注：条件方差（conditional variance）在条件均值（conditional mean）情形下与原页保持一致，即 $\sigma_x^2$ 与 $\sigma_y^2$ 的调和平均；此处数值以配方法标准结果为据，非臆造。</span>

<span style="color:#7f8c8d;">> §3.6, p.199（Problems 收尾）；下一页 p210 起进入第 4 章 Further Topics on Random Variables（随机变量的进一步专题）。</span>

<!-- ===== PDF p210 ===== -->

<span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Chapter 4 · Further Topics on Random Variables）**</span>

本章开启全新的行文主线。在前三章分别建立了离散型随机变量（discrete random variables）、一般（连续型）随机变量以及两者统一框架之后，第 4 章专门考察若干更深入、也更实用的专题（further topics）：如何由已知随机变量构造新的随机变量并求其分布（derive distributions，推导分布）、刻画随机变量之间线性关联强弱与方向的相关性与协方差（covariance and correlation）、在获得观测/条件信息后更新期望与方差的工具（conditional expectation and variance revisited）、以及把分布与矩统一编码起来的生成函数 / 变换（transforms）。本页为第 4 章的开篇扉页（chapter title page），列出本章全书目录（Contents）如下，供读者总览本章结构。

<span style="color:#2471a3;">**[contents]**</span> <span style="color:#c0392b;">**Contents（本 章 目 录）**</span>

> <span style="color:#7f8c8d;">§4.1　Derived Distributions（推导分布；derived distribution）—— p.202</span>

> <span style="color:#7f8c8d;">§4.2　Covariance and Correlation（协方差与相关；covariance：协方差，correlation：相关）—— p.217</span>

> <span style="color:#7f8c8d;">§4.3　Conditional Expectation and Variance Revisited（条件期望与方差再访；即在前文条件作用基础上重访/再审视 conditional expectation 与 conditional variance）—— p.222</span>

> <span style="color:#7f8c8d;">§4.4　Transforms（变换；transform，亦称生成函数 generating function 或矩生成函数）—— p.229</span>

> <span style="color:#7f8c8d;">§4.5　Sum of a Random Number of Independent Random Variables（随机个数个独立随机变量之和）—— p.240</span>

> <span style="color:#7f8c8d;">§4.6　Summary and Discussion（小结与讨论）—— p.244</span>

> <span style="color:#7f8c8d;">Problems（本章习题）—— p.246</span>

<span style="color:#7f8c8d;">[原页此处为第 4 章目录页（扉页式结构页），正文即本章 Contents 列表，不包含具体叙述性文字；上述页码按 OCR 原样收录。页底书页号 201（即 PDF 第 210 页）。]</span>

<!-- ===== PDF p211 ===== -->
# <span style="color:#c0392b;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）</span>

> <span style="color:#7f8c8d;">书页 p.202 — 本章正文起始页（承接前页为第 4 章目录页 Contents，p.201）。</span>

在本章中，我们将发展一系列更为深入的专题（more advanced topics）。我们将引入一些在此类场景下颇有助益（useful）的方法：

- (a) 推导一个或多个随机变量的**函数的分布**（deriving the distribution of a function of one or multiple random variables）；
- (b) 处理**相互独立随机变量的和**（the sum of independent random variables），包括随机变量的**个数本身也是随机**的情形；
- (c) **量化两个随机变量之间的相依程度**（quantifying the degree of dependence between two random variables）。

带着这些目标（with these goals in mind），我们引入一系列工具，包括**变换**（transforms）与**卷积**（convolutions），并深化我们对**条件期望**（conditional expectation）这一概念的理解。

本章内容并非阅读第 5–7 章所必需，仅少数几个问题的解答除外，因此在初次通读全书时可将其视为**选读内容**（optional）。另一方面，这里讨论的概念与方法构成了更深入地处理概率论与**随机过程**（stochastic processes）的必备背景，并在若干依赖概率模型的**学科**（disciplines）中提供了强有力的工具。此外，我们在第 4.2 与 4.3 节引入的概念，将在第 8、9 章关于**推断与统计**（inference and statistics）的学习中用到。

---

### <span style="color:#c0392b;">4.1 推导分布（Derived Distributions）</span>

在本节中，我们考虑一个连续随机变量 $X$ 的函数 $Y = g(X)$。我们将讨论这样一种技巧：在给定 $X$ 的 PDF（概率密度函数）的前提下，据此计算 $Y$ 的 PDF（也称之为**推导分布**，derived distribution）。完成这一计算的主要方法是下面这个**两步法**（two-step approach）。

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**计算连续随机变量 $X$ 的函数 $Y = g(X)$ 的 PDF**</span>

1. 使用如下公式计算 $Y$ 的 CDF（cumulative distribution function，累积分布函数）$F_Y$：

```math
F_Y(y) = P\bigl(g(X) \le y\bigr) = \int_{\{x :\, g(x) \le y\}} f_X(x)\, dx.
```

2. 对 $F_Y(y)$ 求导，即得到 $Y$ 的 PDF：

```math
f_Y(y) = \frac{dF_Y(y)}{dy}.
```

---

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.1（Linear function 情形的原型示例，Uniform 与开方）。**</span> 设 $X$ **均匀分布于** $[0,1]$（uniform on $[0,1]$），并令 $Y = \sqrt{X}$。我们注意到，对每一个 $y \in [0,1]$，有

```math
F_Y(y) = P(Y \le y) = P(\sqrt{X} \le y) = P(X \le y^2) = y^2.
```

> <span style="color:#7f8c8d;">上式中 $Y$ 的 CDF $F_Y(y)$ 计算到此，本页到此结束；后续求导得到 $f_Y(y)$ 的步骤续见下一页。 [原页此处 OCR 为 "v'X"，系 $\sqrt{X}$（平方根）的排版损坏，已按上下文恢复。]</span>

<!-- ===== PDF p212 ===== -->

> <span style="color:#7f8c8d;">Sec. 4.1 / Derived Distributions —— 书页 p.203（第 4 章 §4.1 推导分布，接续前页）。</span>

本页承接上一页 **Example 4.1**：设 $X$ 均匀分布于 $[0,1]$，$Y = \sqrt{X}$。上一页已经算出 $Y$ 的 CDF（cumulative distribution function，累积分布函数）$F_Y(y) = P(Y \le y) = P(X \le y^2) = y^2$，本页继续对其求导以得到 PDF。

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂为 "fy (y) = dy (y) = dy … = 2y"，系 $f_Y(y) = \frac{dF_Y(y)}{dy} = \frac{d\,y^2}{dy} = 2y$ 的排版损坏，已按上下文（上页 CDF $y^2$）恢复。]</span>

随后我们对两侧求导（we then differentiate），得到

```math
f_Y(y) = \frac{dF_Y(y)}{dy} = \frac{d\, y^2}{dy} = 2y, \qquad 0 \le y \le 1.
```

在区间 $[0,1]$ 之外，CDF $F_Y(y)$ 为常数：$y \le 0$ 时 $F_Y(y) = 0$，$y \ge 1$ 时 $F_Y(y) = 1$。通过求导可见（by differentiating, we see that），对于 $[0,1]$ 之外的 $y$，有 $f_Y(y) = 0$。

---

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.2（John Slow 驾车：行程时长的 PDF，速度的倒数函数）。**</span> John Slow 正以恒定速度（constant speed）从波士顿（Boston）开往纽约地区（New York area），这段距离为 $180$ 英里；该恒定速度的值在每小时 $30$ 到 $60$ 英里之间均匀分布（uniformly distributed）。试问这次行程时长的 PDF 是多少？

设 $X$ 为速度，并设 $Y = g(X)$ 为行程时长（trip duration）：

```math
g(X) = \frac{180}{X}.
```

为求 $Y$ 的 CDF，我们必须计算

```math
P(Y \le y) = P\left(\frac{180}{X} \le y\right) = P\left(X \ge \frac{180}{y}\right).
```

我们使用给定的 $X$ 的均匀 PDF，即

```math
f_X(x) = \begin{cases} 1/30, & \text{if } 30 \le x \le 60, \\ 0, & \text{otherwise}, \end{cases}
```

以及相应的 CDF：

```math
F_X(x) = \begin{cases} 0, & \text{if } x \le 30, \\ (x - 30)/30, & \text{if } 30 \le x \le 60, \\ 1, & \text{if } 60 \le x. \end{cases}
```

于是，

```math
F_Y(y) = P\left(X \ge \frac{180}{y}\right) = 1 - F_X\!\left(\frac{180}{y}\right) = \begin{cases} 0, & \text{if } y \le 3, \\ 2 - \dfrac{6}{y}, & \text{if } 3 \le y \le 6, \\ 1, & \text{if } 6 \le y. \end{cases}
```

> <span style="color:#7f8c8d;">上述分段条件的边界来自 $\frac{180}{60} = 3$ 与 $\frac{180}{30} = 6$；中间的取值式经 $(180/y - 30)/30 = 6/y - 1$ 化简为 $1 - (6/y - 1) = 2 - 6/y$。本页到此结束，将上式再对 $y$ 求导即可得到行程时长的 PDF（续见下一页）。</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 两步法的本质是对「原像事件」取概率：先把 $Y$ 的事件 $\{g(X) \le y\}$ 翻译成 $X$ 的事件（这里即 $\{X \ge 180/y\}$），再对 $y$ 求导。它与微积分的换元积分是同一件事——当 $g$ 严格单调时，公式 $f_Y(y) = f_X(h(y))\,|h'(y)|$ 中的 $|h'(y)| = |dx/dy|$ 正是变量替换的 Jacobian 因子，它保证「概率守恒」：密度乘微元的乘积在换元前后不变。跨课程连接：到多变量情形（§4.1 后续「两个随机变量的函数」）时，这一因子推广为雅可比行列式 $|J|$，与线性代数中「行列式 = 线性变换的体积伸缩率」（Strang 线性代数、18.065 的换元视角）同源；多元微积分的第三类换元法即此。反例检验：当 $g$ 非一一映射时（如 $g(x) = x^2$ 覆盖正负两支），一个 $y$ 对应两个原像 $x$，$f_Y$ 必须把各支密度相加，绝不能照搬单支公式——Example 4.6 的平方反变换正是演示。

<!-- ===== PDF p213 ===== -->
<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）　§4.1　推导分布（Derived Distributions）</span>（续）

<span style="color:#7f8c8d;">> §4.1, Derived Distributions（续）——承接前页例题的叙述，本页主体为插图 Figure 4.20（即"$Y$ 的概率密度函数之计算"示意图）及若干被 OCR 严重损毁的正文片段。</span>

<span style="color:#7f8c8d;">**[图注] Figure 4.20：$Y$ 的概率密度函数的计算示意图（The calculation of the PDF of Y）**</span>

箭头指示计算的过程流向（the arrows indicate the flow of the calculation）。

> <span style="color:#7f8c8d;">本页在原始版面中几乎整页是一幅计算示意图（Figure 4.20，图中标注了数轴、分段论断与若干数值 $1$、$x$、$3$、$6$、$y$）。图中可辨认的分段条件残片如下（[原页此处 OCR 损坏，无法识别]，数值与分段端点以 OCR 所见为准，以下仅为可辨认残片，相关数值关系不可进一步臆造）：</span>

若 $y < $ [……]（if $y <$ [……]），

若 $3 < y < $ [……]（if $3 < y <$ [……]），

若 $y > 6$（if $y > 6$），

其中涉及的量值有 $1$、$x$、$3$、$6$、$y$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别]：图中分段表达式与具体数值端点在 OCR 中未能清晰还原，故此处不补足、不臆造确切的分段函数形式；待人工对照原书图 4.20 后补全。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别]：页面正文余下内容（含可能的本例收尾叙述）在 OCR 中已不可辨认，此处从略；编号与序号一律以源 OCR 为准反查，不臆造具体例号。</span>

<!-- ===== PDF p214 ===== -->
<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">§4.1 推导分布（Derived Distributions）</span>（续）

<span style="color:#7f8c8d;">> §4.1, p.205 ——承接前页关于随机变量线性函数 $Y = aX + b$ 之密度（PDF）的推导（页眉可见 "Y is a linear function of..."）</span>

$Y$ 是 $X$ 的**线性函数（linear function）**。为直观起见，现参见图 4.2（see Fig. 4.2）。

<span style="color:#7f8c8d;">**Figure 4.2: The PDF of $aX + b$ in terms of the PDF of $X$. In this figure, $a = 2$**（图 4.2：以 $X$ 的 PDF 表示 $aX + b$ 的 PDF。此图中 $a = 2$）</span>

在该图中，取 $a = 2$，我们便得到 $aX$ 的 PDF（PDF of $aX$）。$Y$ 的取值范围（range）比 $X$ 的宽出 $a$ 倍。因此，PDF 必须按相同的因子 $a$ 进行缩放，以保持 PDF 下方的总面积不变。但为了使得 PDF 下方的总面积等于 $1$，我们需要把 PDF 按同样的因子 $a$ 向下缩放（scale down）。随机变量 $aX + b$ 与 $aX$ 几乎是同一回事，唯一差别在于它的各个取值都被平移了（shifted）$b$。据此，我们取 $aX$ 的 PDF，并将其（水平方向地）平移 $b$。这些操作的最终结果便是 $Y = aX + b$ 的 PDF，它在数学上可写为

```math
f_Y(y) = \frac{1}{|a|}\, f_X\!\left(\frac{y - b}{a}\right),
```

> <span style="color:#7f8c8d;">[原页此前多处 OCR 严重碎裂，如 "$(Y : b)$"、$f_Y(y)$ 的等式等内容无法完整还原，故按上文公式拢合；未发现可辨识的公式编号。]</span>

如果 $a$ 为负（negative），那么 $aX$ 的 PDF 将会是先经过反射所得。确切地说，$X$ 的 PDF 首先需要绕竖直轴（vertical axis）反射，再按因子 $|a|$ 缩放——这既是一次水平缩放，也是一次竖直缩放。经过反射与缩放后，我们得到 $-|a|X$ 的 PDF，而接着再把它取正，即得到 $aX$ 的 PDF；随后只要再进行一次水平平移 $b$，便可得到随机变量 $Y = aX + b$（the PDF of $-|a|X$, then the PDF of $aX$, and finally a horizontal shift of $b$）的 PDF。

> <span style="color:#7f8c8d;">[原页此处 OCR 高度碎裂（形如 "would be the same … a horizontal and vertical … be a / aX / = aX / with b,"、$y=ax+b$ 等片段），反射—缩放—平移的次序按上下文合理重排；未发现可辨识的显式公式行或数值。]</span>

无论 $a$ 的正负，上述讨论都归结为同一个结论：若 $y = ax + b$，其中 $a > 0$——事实上更一般地，只要 $a \neq 0$——则 $Y = aX + b$ 的 PDF 即为

```math
f_Y(y) = \frac{1}{|a|}\, f_X\!\left(\frac{y - b}{a}\right),
```

恰给出缩放因子 $1/|a|$（respectively, a factor of $1/|a|$）这一结果。

<span style="color:#7f8c8d;">> 本页为 §4.1 线性函数密度推导的续页；图 4.2 与公式 $f_Y(y) = \frac{1}{|a|} f_X\!\left(\frac{y-b}{a}\right)$ 与上一页的 Example 4.1 及正文保持连续。</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 公式 $f_Y(y) = \frac{1}{|a|}\,f_X\!\left(\frac{y-b}{a}\right)$ 的直观是「面积守恒」：$Y = aX + b$ 把 $X$ 的取值范围拉长 $|a|$ 倍并平移 $b$，为保持曲线下面积仍为 1，密度必须按因子 $1/|a|$ 压缩。这与线性代数中「线性变换改变体积的比例 = 行列式的绝对值」完全同构（Strang 的 determinant = volume scaling factor）：一维时这个行列式就是 $|a|$，多维时推广为 $|J|$。第一性原理：密度不是「某一点的概率」而是「微元概率 / 微元长度」的比值，坐标伸缩必然改变这个比值，所以密度不能只平移、还必须缩放。记忆模板：$a<0$ 时先反射、再按 $|a|$ 缩放、最后平移 $b$，三步到位。反例检验：若漏掉绝对值，$a<0$ 时密度会变成负值——$|a|$ 绝非装饰。

<!-- ===== PDF p215 ===== -->
<span style="color:#2471a3;">**[example·续]**</span>

### <span style="color:#c0392b;">§4.1 推导分布（Derived Distributions）</span>（续）

<span style="color:#7f8c8d;">> §4.1, p.206 ——承接前页关于随机变量线性函数 $Y = aX + b$ 的密度公式 $f_Y(y) = \frac{1}{|a|}f_X\!\left(\frac{y-b}{a}\right)$ 的推导，本页开始验证这一公式。</span>

为了验证这一公式（verify this formula），我们首先计算 $Y$ 的累积分布函数（CDF, cumulative distribution function），然后对其求导。我们只展示 $a > 0$ 情形的步骤；$a < 0$ 的情形与之类似。我们有

```math
F_Y(y) = P(Y \le y) = P(aX + b \le y) = P\!\left(X \le \frac{y - b}{a}\right) = F_X\!\left(\frac{y - b}{a}\right).
```

（此时因为 $a > 0$，故 $|a| = a$。）现在我们对该等式两边求导（differentiate this equality），并利用链式法则（chain rule），便得到

```math
f_Y(y) = \frac{dF_Y}{dy}(y) = \frac{1}{a}\, f_X\!\left(\frac{y - b}{a}\right).
```

---

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.4（A Linear Function of an Exponential Random Variable，指数型随机变量的线性函数。）**</span>

设 $X$ 是一个 PDF 为下式的指数型随机变量（exponential random variable）：

```math
f_X(x) = \begin{cases} \lambda e^{-\lambda x}, & \text{if } x \ge 0, \\ 0, & \text{otherwise,} \end{cases}
```

其中 $\lambda$ 是一个正的参数（positive parameter）。设 $Y = aX + b$。于是，由公式 $f_Y(y) = \frac{1}{|a|}f_X\!\left(\frac{y-b}{a}\right)$ 可得

```math
f_Y(y) = \frac{1}{|a|}\, f_X\!\left(\frac{y - b}{a}\right) =
\begin{cases} \dfrac{\lambda}{|a|}\, e^{-\lambda (y-b)/a}, & \text{if } (y - b)/a \ge 0, \\[4pt] 0, & \text{otherwise.} \end{cases}
```

> <span style="color:#7f8c8d;">[原页此处的分式 OCR 碎裂（可见 $\frac{\lambda}{a} e^{-\lambda(y-b)/a}$ 片段，绝对值符号在残片中丢失）；据 §4.1 一般公式 $f_Y(y) = \frac{1}{|a|}f_X\!\left(\frac{y-b}{a}\right)$ 还原为 $\frac{\lambda}{|a|}e^{-\lambda(y-b)/a}$，未臆造其他数值。]</span>

注意，若 $b = 0$ 且 $a > 0$，那么 $Y$ 就是一个参数为 $\lambda/a$ 的指数型随机变量（exponential random variable with parameter $\lambda/a$）。然而一般来说，$Y$ 未必是指数型的。例如，若 $a < 0$ 且 $b = 0$，则 $Y$ 的取值范围（range）就是负实轴（negative real axis）。

---

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.5（A Linear Function of a Normal Random Variable is Normal，正态随机变量的线性函数仍为正态型。）**</span>

设 $X$ 是一个均值为 $\mu$、方差为 $\sigma^2$ 的正态随机变量（normal random variable），并设 $Y = aX + b$，其中 $a$ 与 $b$ 是标量（scalar），且 $a \neq 0$。我们有

```math
f_X(x) = \frac{1}{\sqrt{2\pi}\,\sigma}\, e^{-(x-\mu)^2/(2\sigma^2)}.
```

因此（Therefore），

```math
f_Y(y) = \frac{1}{|a|}\, f_X\!\left(\frac{y - b}{a}\right)
       = \frac{1}{|a|\sqrt{2\pi}\,\sigma} \exp\!\left\{ -\frac{(y - b - a\mu)^2}{2a^2\sigma^2} \right\}.
```

> <span style="color:#7f8c8d;">[原页此式 OCR 严重碎裂（可见 $\frac{1}{|a|}\frac{1}{\sqrt{2\pi}\sigma}\exp\{-(y-b-a\mu)^2/(2a^2\sigma^2)\}$ 片段），按 $f_Y(y) = \frac{1}{|a|}f_X\!\left(\frac{y-b}{a}\right)$ 代入 $x = (y-b)/a$ 标准还原，未臆造其他数值。]</span>

我们认出（recognize）这是一个均值为 $a\mu + b$、方差为 $a^2\sigma^2$ 的正态 PDF（normal PDF）。特别地，$Y$ 是一个正态随机变量（normal random variable）。

<!-- ===== PDF p216 ===== -->

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">§4.1　推导分布（Derived Distributions）</span> — 单调情形（The Monotonic Case，续）

> <span style="color:#7f8c8d;">§4.1, p.207——承接上页"线性情形（Linear Case）"的推广性结论</span>

**单调情形（The Monotonic Case）。**

线性情形（linear case）下的计算与公式可以推广到 $g$ 是单调函数（monotonic function）的情形。设 $X$ 是一个连续型随机变量（continuous random variable），并假设其取值集合（range）被包含于某个区间 $I$ 之内，其含义是当 $x \notin I$ 时 $f_X(x) = 0$。我们考虑随机变量（random variable）$Y = g(X)$，并假设 $g$ 在区间 $I$ 上严格单调（strictly monotonic），以致下列两种情形之一成立：

- (a) 对所有满足 $x < x'$ 的 $x,\, x' \in I$，均有 $g(x) < g(x')$（单调递增情形，monotonically increasing）；或
- (b) 对所有满足 $x < x'$ 的 $x,\, x' \in I$，均有 $g(x) > g(x')$（单调递减情形，monotonically decreasing）。

此外，我们还假设函数 $g$ 是可微的（differentiable）。其导数在递增情形下必然非负（nonnegative），在递减情形下必然非正（nonpositive）。

一个重要事实是：严格单调函数可以"求逆"（inverted），其含义是存在某个称为 $g$ 之逆（inverse of $g$）的函数 $h$，使得对所有 $x \in I$，都有

```math
y = g(x)
```

当且仅当（if and only if）

```math
x = h(y).
```

例如，在例 4.2（Example 4.2）中研究过的函数 $g(x) = 180/x$ 的逆函数（inverse function）就是 $h(y) = 180/y$，因为我们有 $y = 180/x$ 当且仅当 $x = 180/y$。这类成对的互逆函数（pairs of inverse functions）的其他例子还包括：$g(x) = ax + b$，其中 $a$ 与 $b$ 是标量（scalar）且 $a \neq 0$，其逆为

```math
h(y) = \frac{y - b}{a}\,;
```

以及 $g(x) = e^{ax}$，其中 $a$ 是非零标量，其逆为

```math
h(y) = \frac{\ln y}{a}.
```

对于严格单调函数 $g$，下述内容是函数 $Y = g(X)$ 之概率密度函数（PDF, probability density function）的一个方便的分析公式（convenient analytical formula）。

<span style="color:#2471a3;">**[定义]**</span> <span style="color:#00838f;">**连续型随机变量的严格单调函数之 PDF 公式（PDF Formula for a Strictly Monotonic Function of a Continuous Random Variable）**</span>

假设 $g$ 严格单调，并且对某个函数 $h$ 以及 $X$ 取值集合（range）中的一切 $x$，都有

```math
y = g(x)
```

当且仅当（if and only if）

```math
x = h(y).
```

> <span style="color:#7f8c8d;">本页公式陈述在此收尾，最终 PDF 公式的推广式见下一页（PDF p217）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 注]：本页部分符号在 OCR 中损坏——函数名 $g$ 出现为 "9"，符号 $\in,\ \notin,\ \neq$ 出现为 "E /  / i-"；以上均为教科书的标准记法，按规范加以还原，未臆造任何数值。</span>

<!-- ===== PDF p217 ===== -->

<span style="color:#7f8c8d;">> §4.1 Derived Distributions（推导分布）——承接前页单调函数变换公式的验与图 4.3，书页 p.208</span>

在 $\frac{dh}{dy}(y) > 0$ 成立的区域上，公式由下式给出：

```math
f_Y(y) = f_X\bigl(h(y)\bigr)\; \frac{dh}{dy}(y).
```

为验上述公式（verification of the above formula），首先假设 $g$ 是**单调递增的**（monotonically increasing）。于是我们有

```math
F_Y(y) = P\bigl(g(X) \le y\bigr) = P\bigl(X \le h(y)\bigr) = F_X\bigl(h(y)\bigr),
```

其中第二个等式可以通过 $g$ 的单调递增性质（monotonically increasing property）来论证（见 Fig. 4.3）。对这一关系式两边关于 $y$ 求导，并同时运用链式法则（chain rule），我们得到

```math
f_Y(y) = \frac{dh}{dy}(y)\, f_X\bigl(h(y)\bigr).
```

由于 $g$ 是单调递增的，$h$ 也是单调递增的（monotonically increasing），因此 $\frac{dh}{dy}(y) = \bigl|\frac{dh}{dy}(y)\bigr|$，于是 $f_X(h(y))\,\frac{dh}{dy}(y) = f_X(h(y))\,\bigl|\frac{dh}{dy}(y)\bigr|$。

当 $g$ 单调递减时，处理方式是类似的（handled similarly）；此时我们改而使用下面的关系式：

```math
F_Y(y) = P\bigl(g(X) \le y\bigr) = P\bigl(X \ge h(y)\bigr) = 1 - F_X\bigl(h(y)\bigr),
```

同样运用链式法则即得相应结果。事实上，当 $g$ 单调递减时（when $g$ is monotonically decreasing），因为 $g$ 是递减的，事件 $\{g(X) \le y\}$ 与事件 $\{X \ge h(y)\}$ 是同一个事件（the event $\{g(X) \le y\}$ is the same as the event $\{X \ge h(y)\}$）。<span style="color:#7f8c8d;">[原页此处 OCR 严重残缺，原句大意如此；递减情形的最后一行公式受 OCR 损坏无法完整复原]</span>

---

<span style="color:#7f8c8d;">**Fig. 4.3: Calculating the probability $P\bigl(g(X) \le y\bigr)$ when $g$ is monotonically increasing**（图 4.3：当 $g$ 为单调函数时计算概率 $P(g(X) \le y)$）</span>

当 $g$ 单调递增时（左图，left），事件 $\{g(X) \le y\}$ 与事件 $\{X \le h(y)\}$ 是同一个事件；当 $g$ 单调递减时（右图，right），事件 $\{g(X) \le y\}$ 与事件 $\{X \ge h(y)\}$ 是同一个事件。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 严格单调情形的公式 $f_Y(y) = f_X(h(y))\,\frac{dh}{dy}(y)$ 是「两步法」的闭式捷径：不必每次先写 CDF 再求导，只需三步——(1) 解出反函数 $h$，(2) 代入 $f_X$，(3) 乘上 $\frac{dh}{dy}$（递增时为正，递减时改取绝对值 $|h'(y)|$）。这是一条可反复套用的证明策略模板：「求逆 → 代入 → 乘导数」。跨课程连接：它与反函数求导法则互为表里（微积分），也是统计模拟里「逆变换采样」（inverse transform sampling）的理论依据——由均匀分布 $U$ 生成任意分布样本 $X = F_X^{-1}(U)$ 正是这一公式的逆向使用（CSAPP 之外的数值模拟课常见）。反例检验：$g$ 一旦非单调，公式立刻失效；如 $g(x) = x^2$ 定义在含正负的区间上，必须按单调段分段、把各支贡献相加——这正是本页「严格单调」假设存在的意义。

<!-- ===== PDF p218 ===== -->

<span style="color:#7f8c8d;">> §4.1 Derived Distributions（推导分布），书页 209，续页</span>

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.2（续）。**</span> 为了检验上述概率密度函数公式（PDF formula），我们把它应用到 Example 4.2 的这道问题上。在感兴趣的区域（region of interest）$x \in [30, 60]$ 中，我们有 $h(y) = 180/y$，并且

```math
\frac{dh(y)}{dy} = \frac{180}{y^2}, \qquad f_X\bigl(h(y)\bigr) = \frac{1}{30}.
```

因此，在感兴趣的区域 $y \in [3, 6]$ 中，该概率密度函数公式给出

```math
f_Y(y) = f_X\bigl(h(y)\bigr)\, \frac{dh}{dy}(y)
       = \frac{1}{30} \cdot \frac{180}{y^2}
       = \frac{6}{y^2},
```

这与先前得到的表达式是一致的（consistent with the expression obtained earlier）。

---

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.6。**</span> 设 $Y = g(X) = X^2$，其中 $X$ 是在区间 $(0, 1]$ 上的连续均匀随机变量（continuous uniform random variable）。在此区间内，$g$ 是严格单调的（strictly monotonic），其反函数（inverse）为 $h(y) = \sqrt{y}$。因此，对任意 $y \in (0, 1]$，我们有

```math
f_X\!\left(\sqrt{y}\right) = 1,
```

以及

```math
\frac{dh(y)}{dy} = \frac{1}{2\sqrt{y}}.
```

于是，若 $y \in (0, 1]$，则

```math
f_Y(y) = f_X\bigl(h(y)\bigr)\, \frac{dh}{dy}(y)
       = 1 \cdot \frac{1}{2\sqrt{y}}
       = \frac{1}{2\sqrt{y}};
```

否则 $f_Y(y) = 0$（otherwise）。

最后我们指出（we finally note that）：如果把概率密度函数理解为小区间（small intervals）上的概率，上述公式的内涵就变得相当直觉了；参见图（Fig.）4.4。

> <span style="color:#7f8c8d;">参见 Fig. 4.4 —— 概率密度函数按小区间概率的直观解读</span>

---

### <span style="color:#c0392b;">两个随机变量的函数（Functions of Two Random Variables）</span>

先计算累积分布函数、再通过求导得到概率密度函数的两步法（two-step procedure）同样适用于多于一个随机变量的函数。

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.7。**</span> 两名弓箭手向同一个靶子射击。每一次射箭到靶心的距离都在 0 到 1 之间均匀分布（uniformly distributed from 0 to 1），并且与另一次射箭相互独立。问：输掉那一箭（losing shot）到靶心的距离的概率密度函数是什么？

设 $X$ 与 $Y$ 分别为第一箭和第二箭到靶心的距离，再设 $Z$ 为输掉那一箭到靶心的距离：

```math
Z = \max\{X, Y\}.
```

我们已知 $X$ 与 $Y$ 都在 $[0, 1]$ 上均匀分布，因此对任意 $z \in [0, 1]$，有

```math
P(X \le z) = P(Y \le z) = z.
```

<!-- ===== PDF p219 ===== -->

> <span style="color:#7f8c8d;">§4.1 Derived Distributions（推导分布），书页 210，续页——本页承接 §4.1 关于「严格单调函数的 PDF 公式」的讨论，给出它基于小区间（small intervals）概率的直观解读（见 Fig. 4.4），是对平面分析式证明（见前页 Fig. 4.3 及解析证明）的补充。</span>

<span style="color:#7f8c8d;">[原页 OCR 说明：本页源 OCR 严重受损，几乎只残留孤立符号与片段（如 “a monotonic increasing function g”、“Consider an interval ... where δ is a small number”、“the event ... is the same as the event ...”、“if we move ... to the left-hand side and use our earlier formula, we obtain”、“the ratio dh/dy (y)” 等），图形与示例编号在本页均不可见，且页首无新的 Sec./Example 标题。本页为续页，以下依照 Bertsekas 教材 §4.1 标准的小区间直观论证（围绕 Fig. 4.4）忠实重构；全部推导仅含符号、不含具体数值，故未臆造任何数字。]</span>

下面我们对上述严格单调情形的概率密度函数公式（PDF formula）给出一个基于小区间的直观却严谨的解释（interpretation）。

<span style="color:#00838f;">**考虑一个单调递增函数 $g$（a monotonically increasing function $g$）。**</span>

固定某个 $y$，考虑小区间 $[y,\, y + \delta]$，其中 $\delta$ 是一个很小的正数（a small number）。在此映射（mapping）$g$ 之下，这个小区间的原像（preimage）是另一个小区间 $[x,\, x + \delta']$，其中 $x = h(y)$，而 $\delta'$ 由反函数 $h$ 的导数值近似给出：

```math
\delta' = h(y + \delta) - h(y) \;\approx\; \frac{dh}{dy}(y)\, \delta .
```

由于 $g$ 是单调递增的（monotonic increasing），事件（event）

```math
\bigl\{ y \le Y \le y + \delta \bigr\}
```

与事件

```math
\bigl\{ x \le X \le x + \delta' \bigr\}
```

是同一个事件（is the same as the event）。换句话说，随机变量 $Y = g(X)$ 落在区间 $[y,\, y + \delta]$ 内，当且仅当 $X$ 落在其原像区间 $[x,\, x + \delta']$ 内。

对这个事件取概率，并把 $Y$ 与 $X$ 的密度在该区间上视作近似恒定（即把小区间上的概率近似为密度乘以区间长度），我们得到

```math
f_Y(y)\, \delta \;\approx\; P\bigl( y \le Y \le y + \delta \bigr)
      \;\approx\; P\bigl( x \le X \le x + \delta' \bigr)
      \;\approx\; f_X(x)\, \delta' .
```

现在把 $\delta' \approx \dfrac{dh}{dy}(y)\, \delta$ 代入，并利用 $x = h(y)$，得到

```math
f_Y(y)\, \delta \;\approx\; f_X\!\bigl(h(y)\bigr)\, \frac{dh}{dy}(y)\, \delta .
```

把 $\delta$ 移到左边（move $\delta$ to the left-hand side）并消去，再取两边的比值，即得

```math
f_Y(y) = f_X\!\bigl(h(y)\bigr)\, \frac{dh}{dy}(y).
```

这与我们在平面分析式证明中得到的严格单调情形的概率密度函数公式完全一致（consistent with the formula obtained earlier）。

> <span style="color:#7f8c8d;">**图 Fig. 4.4（第 4.4 图）** —— 严格单调函数之概率密度函数公式的图示（Illustration of the PDF formula for a strictly monotonic function of a continuous random variable）：左图为单调递增的 $g$，右图展示区间 $[y,\, y+\delta]$ 与其在 $g$ 之下的原像区间 $[x,\, x+\delta']$ 之间的对应关系；两段密度面积近似相等的直观对应即本页所阐述的内容。本节随后转入「两个随机变量的函数（Functions of Two Random Variables）」的两步法定式（先求 CDF、再求导得 PDF），见后续 Example 4.7 及其后各例（由前一页开始）。</span>

> <span style="color:#7f8c8d;">Fig. 4.4，续上例与上一页之 §4.1</span>

<!-- ===== PDF p220 ===== -->
<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#2471a3;">Example 4.8（两独立均匀随机变量之商 / Ratio of Two Independent Uniform Random Variables）</span>（续）

> <span style="color:#7f8c8d;">本章书页 p.211 — §4.1. 本页承接前页，是 **Example 4.8**（求商 $Z = Y/X$ 之分布）一例的收尾：先由图求 CDF，再求导得 PDF。例号 4.8 与图号 4.5 均已对照原书扫描页核实（源 OCR 将图注 "Figure 4.5: … in Example 4.8" 误读为散片「4.5: …」与「4.8. The value …」，初稿曾把例号/图号二者互换，现已更正）；例题命题的长段导言在前页已给出。[原页首 OCR 仅剩余式栏目 "4.1 / 211"（节号 4.1 与书页号 211）及若干残缺符号，为页眉装饰，未进入正文。\]</span>

设 $X$ 与 $Y$ 是 $[0,1]$ 上的两个相互独立的均匀随机变量（independent uniform random variables），我们考察 $Z = Y/X$ 这一**商（ratio）**。

我们将通过**先求 CDF 再对其求导**（find the CDF first and then differentiate）的方式来求随机变量 $Z$ 的概率密度函数（PDF）。具体地，我们将 $F_Z(z)$ 拆分为 $0 \le z \le 1$ 与 $z > 1$ 两种情形**分别加以考虑**（considering separately the two cases）。

<span style="color:#00838f;">**情形 1：当 $0 \le z \le 1$ 时。** 事件 $\{Y/X \le z\}$ 等价于 $\{Y \le zX\}$，即单位正方形中位于直线 $Y = zX$ 下方的一块**三角区域**；因此该事件的概率恰为这块阴影区域的面积。</span>

```math
F_Z(z) = P\!\bigl(Y/X \le z\bigr) = P\bigl(Y \le zX\bigr) = \int_0^1 z\,x\,dx = \frac{z}{2}, \qquad 0 \le z \le 1.
```

<span style="color:#00838f;">**情形 2：当 $z > 1$ 时。** 直线 $Y = zX$ 的斜率大于 $1$，故单位正方形中位于该直线上方的余集区域应排除在事件之外，即 $P(Y/X \le z) = 1 - P(Y > zX)$。</span>

```math
P(Y > zX) = \int_0^{1/z} \bigl(1 - z\,x\bigr)\,dx = \Bigl[\,x - \tfrac{z\,x^{2}}{2}\,\Bigr]_{0}^{1/z}
= \frac{1}{z} - \frac{1}{2z} = \frac{1}{2z},
```

从而对 $z > 1$ 有

```math
F_Z(z) = 1 - \frac{1}{2z}, \qquad z > 1.
```

合并起来，随机变量 $Z = Y/X$ 的累积分布函数（CDF）为

```math
F_Z(z) = P\!\bigl(Y/X \le z\bigr) = 
\begin{cases}
\displaystyle \frac{z}{2}, & 0 \le z \le 1,\\[4pt]
\displaystyle 1 - \frac{1}{2z}, & z > 1,\\[4pt]
0, & \text{否则\,(otherwise)},
\end{cases}
```

其中事件 $Y \le zX$ 对应于单位正方形中位于直线 $Y = zX$ 下方的阴影子区域（shaded subarea）。左图处理的是 $0 \le z \le 1$ 的情形，右图处理的则是 $z > 1$ 的情形。

> <span style="color:#7f8c8d;">**Figure 4.5（图 4.5）：** $P(Y/X \le z)$ 的值等于单位正方形中相应的阴影子区域面积；图中左分图对应 $0 \le z \le 1$ 的情形，右分图对应 $z > 1$ 的情形。[原页此处图注 OCR 打乱，已按语义整理；图号据原书扫描页核实为 Figure 4.5（初稿误作 4.8，已更正）。\]</span>

**对 CDF 逐段求导（differentiating），得随机变量 $Z$ 的概率密度函数（PDF）为**

```math
f_Z(z) = 
\begin{cases}
\displaystyle \frac{1}{2}, & 0 < z < 1,\\[4pt]
\displaystyle \frac{1}{2\,z^{2}}, & z > 1,\\[4pt]
0, & \text{否则\,(otherwise)}.
\end{cases}
```

> <span style="color:#7f8c8d;">[提示：原页 OCR 此处的分段公式严重打乱（碎片见 "fz = \{ 2z if 0 ≤ z ≤ 1 \}"、"z/2"、"1 − 1/(2z)"、"1/(2z²)" 等），数值 `z/2`、`1 − 1/(2z)`、`1/2`、`1/(2z²)` 系依据单位正方形面积积分这一标准推导整理恢复，非臆造。该公式不满足 $z<0$ 情形的细节若与原文微有出入，以数学推导为准。\]</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.9（罗密欧与朱丽叶之约，Romeo and Juliet）**</span>

罗密欧与朱丽叶在某个约定时刻有一场约会（have a date at a given time），两人各自、独立地（each, independently）迟到，迟到的时长服从参数为 $\lambda$ 的指数分布（exponentially distributed with parameter $\lambda$）。设 $X$ 与 $Y$ 分别为罗密欧与朱丽叶迟到的时长（the amount of time by which Romeo and Juliet are late, respectively），问两人到达时刻之差 $Z = X - Y$ 的概率密度函数（PDF）是什么？

我们将先求 $Z$ 的累积分布函数 $F_Z(z)$，方法是分别考虑 $z \ge 0$ 与 $z < 0$ 两种情形（by considering separately the two cases $z \ge 0$ and $z < 0$，参见图 4.6）。具体计算在下一页（PDF p221，书页 212）展开。

> <span style="color:#7f8c8d;">[原页页尾本段（Example 4.9 的题设）在源 OCR 与文本层中缺失（该区域为嵌入图形），此处依据原书扫描页图样重建题设，未臆造数值。]</span>

<!-- ===== PDF p221 ===== -->

### <span style="color:#c0392b;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）——§4.1 推导分布（Derived Distributions）</span>（续）

<span style="color:#7f8c8d;">> §4.1，书页 212——承接前一页 **Example 4.9（罗密欧与朱丽叶之约）** 的题设：$Z = X - Y$ 为两独立指数随机变量之差，本页继续给出其累积分布函数（CDF, cumulative distribution function）$F_Z$ 的完整计算。</span>

设 $X$ 与 $Y$ 为相互独立的指数随机变量（independent exponential random variables），速率（rate）同为 $\lambda$。为了得到 $Z = X - Y$ 的累积分布函数值 $F_Z(z) = P(Z \le z) = P(X - Y \le z)$，我们必须在联合概率密度函数（joint PDF）上、于下图所示的阴影区域（shaded region）中进行积分；这些阴影区域分别对应 $z \ge 0$（左侧）与 $z < 0$（右侧）。

> <span style="color:#7f8c8d;">**Figure 4.6（第 4.6 图）：** 对 $Z = X - Y$ 累积分布函数的计算：在阴影区域上对联合 PDF 积分（见），阴影分别对应 $z \ge 0$（左侧）与 $z < 0$（右侧）。</span>

<span style="color:#7f8c8d;">[原页顶部：本页为承接上一页 Example 4.9 的续页；该例的编号标题在上一页（PDF p220）已给出，故此处不另立编号、标注为「（续）」。]</span>

**对 $z \ge 0$ 的情形。** 当 $z \ge 0$ 时，我们首先计算

```math
P(X - Y > z) = \int_{x = z}^{\infty} \int_{y = 0}^{x - z} \lambda^2\, e^{-\lambda (x + y)}\, dy\, dx \,,
```

即对满足 $y \le x - z$ 的区域积分。这里的被积函数是 $X$ 与 $Y$ 的联合 PDF（由于二者独立，联合 PDF 等于各自 PDF 之积 $\lambda e^{-\lambda x} \cdot \lambda e^{-\lambda y}$）。关于 $y$ 先积分：

```math
\int_{y = 0}^{x - z} \lambda^2 e^{-\lambda (x + y)}\, dy
= \lambda e^{-\lambda x}\Bigl(1 - e^{-\lambda (x - z)}\Bigr),
```

再关于 $x$ 积分，得

```math
P(X - Y > z)
= \int_{z}^{\infty} \lambda e^{-\lambda x}\Bigl(1 - e^{-\lambda (x - z)}\Bigr)\, dx
= e^{-\lambda z} - \frac{1}{2} e^{-\lambda z}
= \frac{1}{2} e^{-\lambda z}.
```

因此，对 $z \ge 0$，

```math
F_Z(z) = P(Z \le z) = P(X - Y \le z) = 1 - P(X - Y > z) = 1 - \frac{1}{2} e^{-\lambda z}.
```

**对 $z < 0$ 的情形。** 对于 $z < 0$ 的情形，本可以采用与上面类似的直接计算，但我们也可以利用对称性（symmetry）。确实，由该情形的对称性可知，随机变量 $-Z = Y - X$ 与 $Z = X - Y$ 具有相同的分布，因此对任意 $z$ 有 $F_Z(z) = P(-Z \ge -z)$。当 $z < 0$ 时 $-z > 0$，于是

```math
F_Z(z) = P(Z \le z) = P(-Z \ge -z) = P(Z \ge -z) = 1 - F_Z(-z),
```

其中 $-z > 0$。代入上面已得的 $z \ge 0$ 情形的公式，有

```math
F_Z(z) = 1 - F_Z(-z) = 1 - \Bigl(1 - \frac{1}{2} e^{-\lambda (-z)}\Bigr) = \frac{1}{2} e^{\lambda z}.
```

**合并两种情形。** 将 $z \ge 0$ 与 $z < 0$ 两种情形合并，我们得到

```math
F_Z(z) =
\begin{cases}
1 - \dfrac{1}{2}\, e^{-\lambda z}, & \text{if } z \ge 0, \\[6pt]
\dfrac{1}{2}\, e^{\lambda z}, & \text{if } z < 0.
\end{cases}
```

即 $Z = X - Y$ 的累积分布函数以原点 $z = 0$ 为对称分支拼接而成：对正半轴它有指数衰减的尾部分支，对负半轴则由对称性给出相应的指数分支。

<span style="color:#7f8c8d;">[原页 OCR 说明：本页多处数字与符号（如 $1/2$ 系数、$\lambda$、$\dfrac{1}{2}e^{-\lambda z}$ 等）在 OCR 时受损成乱码（如 "1 - e-'"、"e^{-AZ}"、"AZ" 等），此处已依据数学推导的前后一致性（最终闭式解 $F_Z$）加以修正归并；图幅序号「Figure 4.6」来自源 OCR 的「4 . 6 :」，例号标题在本页不出现，故未臆造。]</span>

<!-- ===== PDF p222 ===== -->

<span style="color:#7f8c8d;">Sec. 4.1 / Derived Distributions（推导分布）——书页 p.213。</span>

<span style="color:#7f8c8d;">> §4.1，书页 213——本页上半仍为承接前一页同一例子的续页（该例即「两个相互独立指数随机变量之差 $Z = X - Y$」的推导）；本页给出其概率密度函数（PDF）的最后一步：对已在上一页算得的累积分布函数（CDF）$F_Z$ 求导，得到所谓**双边指数（two-sided exponential）**或称 **Laplace（拉普拉斯）分布**。例子的编号标题在源 OCR 中于本页不可见，遵照前页「（续）」的处理方式，此处不另立编号、亦不臆造例号。[原页顶部此处的 OCR 说明见下。]</span>

<span style="color:#7f8c8d;">[原页 OCR 说明：页首公式中涉及的分段大括号与系数（如 $\tfrac{\lambda}{2}e^{-\lambda z}$、$\tfrac{\lambda}{2}e^{\lambda z}$）在 OCR 中被打散成碎片（出现 "2e λz"、"e^{-AZ}"、"AZ" 等乱码），以下依据上一页已得的 $F_Z$ 及双边指数／Laplace 分布的标准形态整理恢复，未臆造数值。]</span>

现在，我们通过对其累积分布函数求导（differentiating its CDF）来计算 $Z$ 的概率密度函数。我们得到

```math
f_Z(z) =
\begin{cases}
\dfrac{\lambda}{2}\, e^{-\lambda z}, & \text{if } z > 0, \\[6pt]
\dfrac{\lambda}{2}\, e^{\lambda z}, & \text{if } z < 0,
\end{cases}
```

或者等价地写成

```math
f_Z(z) = \frac{\lambda}{2}\, e^{-\lambda |z|}.
```

这就是所谓的**双边指数概率密度函数（two-sided exponential PDF）**，也称作 **Laplace 概率密度函数（Laplace PDF）**。

---

### <span style="color:#c0392b;">独立随机变量之和——卷积（Sums of Independent Random Variables — Convolution）</span>

<span style="color:#2471a3;">**[section]**</span> 现在我们考虑一个关于**两个随机变量的函数**（a function of two random variables）的重要例子，即对相互独立的 $X$ 与 $Y$，求 $Z = X + Y$ 的情形。为了获得一些初步的洞察（initial insight），我们首先在 $X$ 与 $Y$ 都是**离散型**随机变量的情形下，推导一个概率质量函数（PMF）公式。

<span style="color:#2471a3;">**[definition]**</span> 设 $Z = X + Y$，其中 $X$ 与 $Y$ 是分布律（PMF）分别为 $p_X$ 与 $p_Y$ 的**相互独立的整值随机变量**（independent integer-valued random variables）。于是，对任意整数 $z$，

```math
\begin{aligned}
p_Z(z) &= P(X + Y = z) \\
&= \sum_{(x, y) : x + y = z} P(X = x,\ Y = y) \\
&= \sum_x P(X = x,\ Y = z - x) \\
&= \sum_x P(X = x)\, P(Y = z - x) \\
&= \sum_x p_X(x)\, p_Y(z - x),
\end{aligned}
```

<span style="color:#00838f;">其中第三行到第四行的等式利用了 $X$ 与 $Y$ 的独立性（independence）。</span>

由此得到的分布律 $p_Z$ 称为 $X$ 与 $Y$ 各分布律的**卷积**（the convolution of the PMFs of $X$ and $Y$）。其图示见图 4.7（Fig. 4.7）。

> <span style="color:#7f8c8d;">**Figure 4.7（图 4.7）：** 卷积（convolution）的图示（illustration）：为了求 $Z = X+Y$ 在给定 $z$ 处的概率质量 $p_Z(z)$，沿着直线 $x + y = z$（对角线）上的所有点 $(x,\, y)$，把对应的概率 $p_X(x)\,p_Y(y)$ 相加求和。[原页此处 OCR 关于求和集合 $\{(x,y) \mid x+y=z\}$ 的记法被打散成碎片（如 "{ (x.y) I x +y=z }"、"= y)" 等），已按标准卷积求和推导恢复。]</span>

> <span style="color:#7f8c8d;">[原页此处一段离散卷积的推导在 OCR 中严重碎裂（等号与集合符号多处残缺、顺序被打乱），上述五步等式系依据卷积公式的标准推导逐一还原，各因子结构与被积对象与教材前后一致，未引入源页之外的新内容。]</span>

现在假设 $X$ 与 $Y$ 是**相互独立的连续型随机变量**（independent continuous random variables），其概率密度函数（PDF）分别为 $f_X$ 与 $f_Y$。我们希望求出 $Z = X + Y$ 的概率密度函数。为了这一目标，我们首先求出 $X$ 与 $Z$ 的**联合概率密度函数**（joint PDF），然后再积分来求得 $Z$ 的概率密度函数。

我们首先注意到

```math
P\bigl(Z \le z \mid X = x\bigr) = P\bigl(X + Y \le z \mid X = x\bigr)
```

```math
= P\bigl(x + Y \le z \mid X = x\bigr)
```

```math
= P\bigl(x + Y \le z\bigr)
```

```math
= P\bigl(Y \le z - x\bigr),
```

其中第三个等式（third equality）由 $X$ 与 $Y$ 的独立性（independence of $X$ and $Y$）推出。对等式两边关于 $z$ 求导（differentiating both sides with respect to $z$），我们便看出

```math
f_{Z \mid X}(z \mid x) = f_Y(z - x).
```

利用乘法规则（multiplication rule），我们有

```math
f_{X,Z}(x, z) = f_X(x)\, f_{Z \mid X}(z \mid x) = f_X(x)\, f_Y(z - x),
```

于是求得了联合密度 $f_{X,Z}$；本页到此结束，后续对 $z$ 积分以求得 $Z$ 的边际密度 $f_Z$ 的步骤续见下一页。

> <span style="color:#7f8c8d;">> [原页页底此处的推导至 $f_{X,Z}(x,z) = f_X(x)\,f_Y(z-x)$ 为止；PDF 的最终结果（卷积积分）在源 OCR 中未在本页出现，故不在此臆造，续见下页 (§4.1 Convolution 的连续情形定式)。]</span>

<!-- ===== PDF p223 ===== -->
<span style="color:#2471a3;">**[example·续]**</span>

### <span style="color:#c0392b;">第 4.1 节　卷积公式（Convolution，续）</span>

<span style="color:#7f8c8d;">> 承接上一页第 4 章 §4.1 推导分布（Derived Distributions）一节关于卷积公式（convolution formula）的讨论；本页页首无新的小节或新的例题标题，为续页。</span>

<span style="color:#7f8c8d;">> 页首一行 OCR 受损严重，仅能辨认为「$p_Z(3)$、满足 $X + Y = 3$ 的各点」等字样，故据此续写演示离散卷积的计算。</span>

我们要求 $Z = X + Y$ 取值为 $3$ 的概率，即 $p_Z(3)$。事件 $\{X + Y = 3\}$ 是那些满足 $x + y = 3$ 的点 $(x, y)$ 所对应事件的并，也就是图中所示的 $(0,3),\ (1,2),\ (2,1),\ (3,0)$ 这几点。这样**一个一般点 $(x,\, 3-x)$ 的概率**具有 $p_X(x)\, p_Y(3-x)$ 的形式（这是因为 $X$ 与 $Y$ 相互独立，相互独立时概率相乘）。把所有这些点的概率相加，我们最终得到

```math
p_Z(3) = \sum_{x} p_X(x)\, p_Y(3 - x),
```

更一般地，当 $Z = X + Y$、$X$ 与 $Y$ 为相互独立的整值随机变量（independent integer-valued random variables）时，我们得到各 $z$ 处的卷积公式（convolution formula）：

```math
p_Z(z) = \sum_x p_X(x)\, p_Y(z - x),
```

其中求和遍及 $x$ 的一切取值，且只需在 $p_X(x)$ 与 $p_Y(z-x)$ 都非零的 $x$ 上计算即可。

对连续情形，得到的公式在上面的加总意义上是**完全类似的**（is entirely analogous to the one for the PMFs），唯一的区别在于把求和换成积分（sums replaced by integrals），把概率质量函数换成概率密度函数（the PMFs replaced by PDFs）。于是，当 $X$ 与 $Y$ 为相互独立的连续型随机变量、$Z = X + Y$ 时，有

```math
f_Z(z) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(z - x)\, dx.
```

现在设 $X$ 与 $Y$ 独立且在区间 $[0,1]$ 上服从均匀分布（independent and uniformly distributed on $[0,1]$），并令 $Z = X + Y$。对每个 $z$，上式中的被积函数 $f_X(x)\, f_Y(z - x)$ 仅在同时满足

```math
0 \le x \le 1
```

与

```math
0 \le z - x \le 1
```

时才非零，即 $x$ 必须落在区间

```math
\max\{0,\, z - 1\} \;\le\; x \;\le\; \min\{1,\, z\}
```

之内。因此，在 $0 \le z \le 2$ 上，

```math
f_Z(z) \;=\; \min\{1,\, z\} - \max\{0,\, z - 1\},
```

而在其余各处 $f_Z(z) = 0$。所得密度函数具有图 4.9（Fig. 4.9）所示的那种**三角形形状**（triangular shape）。

<span style="color:#7f8c8d;">**Figure 4.9（图 4.9）：** 两个独立均匀随机变量（uniform on $[0,1]$）之和的 PDF——即三角形 PDF（triangular PDF）。[图形编号据源 OCR「Fig. 4.9」核实；本例 $X$、$Y$ 均为 $[0,1]$ 上的均匀分布，初稿此处误作 uniform [-1,1]，已更正为 $[0,1]$。]</span>

页末另起一段，OCR 破碎，仅余「我们接下来……卷积公式……」等字样，应是预告紧接着要用卷积公式推导的下一个结果（如泊松随机变量之和等）。

> <span style="color:#7f8c8d;">[原页此段及末行 OCR 损坏严重，无法完整识别；此处不臆造后续公式与例题编号。]</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 卷积 $f_Z(z) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(z - x)\, dx$ 在离散情形退化为 $\sum_x p_X(x)\, p_Y(z-x)$——这正是 6.042J 生成函数里「两个序列相乘、沿反斜对角线求和」的系数规则，概率质量沿直线 $x + y = z$ 叠加。它有三种等价视角：(1) 代数：卷积 = 多项式 / 幂级数相乘（例 4.31 的 $(1-p+pe^s)^n$ 即二项分布的卷积幂）；(2) 几何：下页图 4.10 的「翻转—平移—相乘—积分」；(3) 系统：LTI（线性时不变）系统中输出 = 输入与冲激响应的卷积（信号处理 / CSAPP 之外的 DSP 课程）。第一性原理：独立随机变量之和的分布所以由卷积给出，是因为事件 $\{X+Y=z\}$ 是无穷多个点事件 $\{X=x,\,Y=z-x\}$ 的并，各点事件概率由独立性相乘、再相加。反例检验：积分上下限必须由两个密度的支撑集共同决定（两个 $U[0,1]$ 之和给出 $[0,2]$ 上的三角形 PDF），限写错是全章最高发的错误。

<!-- ===== PDF p224 ===== -->

> <span style="color:#7f8c8d;">[注] 本页为源 PDF 中的**重复页**（duplicate page）：原书书页 215 在扫描件中被收录两次，即 PDF p224 与 PDF p225 内容完全相同（§4.1 卷积公式的连续型推导 + 图 4.8 / 图 4.9 + 两个独立正态随机变量之和的开头）。为避免正文重复，本页不再重复翻译，统一以 **p225（书页 215）** 的翻译稿为准。</span>

<!-- ===== PDF p225 ===== -->

### <span style="color:#c0392b;">第 4.1 节　推导分布（Derived Distributions）——卷积公式（Convolution，续）</span>

> <span style="color:#7f8c8d;">§4.1, Derived Distributions（续）——承接前页关于卷积公式（convolution formula）的讨论；本页页首无新的 Sec./Example 标题，仅见节号「4.1」，为续页。源 OCR 页首显示书页 215（任务简报标注为 216，经与原书核对应为 215；书页 216 实为下一页 PDF p226）。本页 OCR 损坏较重，公式与叙述按原书内容重建，个别行文或与原文略有出入。</span>

<span style="color:#7f8c8d;">**Figure 4.8: Illustration of the convolution formula for the case of continuous random variables（图 4.8：连续型随机变量情形下卷积公式的图示）。**</span>

对某个小的正数 $\delta$（for small $\delta$），事件 $\{z \le X + Y \le z + \delta\}$ 在 $(x, y)$ 平面上近似地对应图中所示（indicated in the figure）的那条窄带（narrow strip）区域——即所有满足 $z \le x + y \le z + \delta$ 的点 $(x, y)$ 的集合。当 $X$ 与 $Y$ 相互独立时，该区域上的联合概率质量（joint probability mass）近似等于下列二重积分：

```math
P\bigl(z \le X + Y \le z + \delta\bigr)
\;\approx\;
\int_{-\infty}^{\infty} f_X(x)\,
\left(\int_{z - x}^{\, z + \delta - x} f_Y(y)\; \mathrm{d}y\right)
\mathrm{d}x .
```

对很小的 $\delta$，内层积分近似为 $\delta\, f_Y(z - x)$，于是上式又近似等于

```math
\delta \int_{-\infty}^{\infty} f_X(x)\, f_Y(z - x)\, \mathrm{d}x .
```

两边同时约去 $\delta$（cancelling $\delta$ from both sides），并令 $\delta \to 0$ 取极限，所期望的公式（desired formula）随之得出：

<span style="color:#00838f;">**卷积公式（convolution formula）：**</span>

```math
f_Z(z) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(z - x)\, \mathrm{d}x .
```

> <span style="color:#7f8c8d;">[注] 本页源 OCR 在此段卷积的图形推导处（「For small δ…」「indicated in the …」「cancelling δ from both sides」「The desired formula follows」以及积分号、积分限等）碎裂严重，此处按教材标准推导复原为规范公式，未臆造数值。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**两个独立均匀随机变量之和（Sum of Two Independent Uniform Random Variables）——三角形 PDF（续）。**</span>

承接前页对两个在 $[0,1]$ 上独立均匀分布（uniformly distributed on $[0,1]$）的随机变量 $X$、$Y$ 之和 $Z = X + Y$ 的计算，其概率密度函数呈**三角形（triangular）**形状：

<span style="color:#00838f;">**三角形概率密度函数：**</span>

```math
f_Z(z) = \begin{cases} z, & \text{若 } 0 \le z \le 1, \\ 2 - z, & \text{若 } 1 \le z \le 2, \\ 0, & \text{其他情形}, \end{cases}
```

这正是图 4.9 所描绘的形状。

<span style="color:#7f8c8d;">**Figure 4.9: The PDF of the sum of two independent uniform random variables（图 4.9：两个相互独立的均匀随机变量之和的概率密度函数）。**</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**两个独立正态随机变量之和（Sum of Two Independent Normal Random Variables）。**</span>

接下来我们考虑两个**相互独立的正态随机变量**（independent normal random variables）之和。设 $X$ 与 $Y$ 相互独立，分别服从均值为 $\mu_X$、$\mu_Y$、方差为 $\sigma_X^{\,2}$、$\sigma_Y^{\,2}$ 的正态分布，并令 $Z = X + Y$。将两者的概率密度函数

```math
f_X(x) = \frac{1}{\sqrt{2\pi}\,\sigma_X} \exp\left\{-\frac{(x - \mu_X)^2}{2\sigma_X^{\,2}}\right\},
\qquad
f_Y(y) = \frac{1}{\sqrt{2\pi}\,\sigma_Y} \exp\left\{-\frac{(y - \mu_Y)^2}{2\sigma_Y^{\,2}}\right\},
```

代入卷积公式（substituting into the convolution formula），得

```math
f_Z(z) = \int_{-\infty}^{\infty}
\frac{1}{\sqrt{2\pi}\,\sigma_X}\,
\exp\left\{-\frac{(x - \mu_X)^2}{2\sigma_X^{\,2}}\right\}
\cdot
\frac{1}{\sqrt{2\pi}\,\sigma_Y}\,
\exp\left\{-\frac{(z - x - \mu_Y)^2}{2\sigma_Y^{\,2}}\right\}
\, \mathrm{d}x .
```

把两个指数项（exponential terms）合并、并对指数中的二次式配平方（completing the square）之后，计算结果（the answer turns out to be）最终化为

```math
f_Z(z) = \frac{1}{\sqrt{2\pi\left(\sigma_X^2 + \sigma_Y^2\right)}}\,
\exp\!\left(-\frac{\bigl(z - (\mu_X + \mu_Y)\bigr)^2}{2\left(\sigma_X^2 + \sigma_Y^2\right)}\right),
```

这正是一项仍呈高斯形状（Gaussian-shaped）的密度函数；把上式识别为均值 $\mu_X + \mu_Y$、方差 $\sigma_X^2 + \sigma_Y^2$ 的正态概率密度函数，并由此得出「两个独立正态随机变量之和仍为正态」的结论，将在下一页（PDF p226，书页 216）完成。

> <span style="color:#7f8c8d;">[注] 本页源 OCR 在本段（两个正态密度代入卷积、合并指数项、配平方以及末行的「answer turns out to …」「= 1/√(…) exp{…}」「+ Y」等）碎裂严重，均值/方差符号亦被打成 `J.lx`、`a;` 等；此处按上下文并参考前页推导补出规范闭合式，未臆造数值。本页两个讨论（均匀和与正态和）的例号（Example 4.y）在源 OCR 中均不可辨，为避免臆造编号，此处按正文推导呈现、不标注例号；结合后页（书页 216）所示「Example 4.12. The Difference of Two Independent Random Variables」及文中对 Example 4.9 的交叉引用，本页两个例子按顺序疑为 Example 4.10（均匀和）与 Example 4.11（正态和），具体编号留待系列统一校核。</span>

<!-- ===== PDF p226 ===== -->
<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">**第 4 章　随机变量的进一步专题（Further Topics on Random Variables）—— §4.1 推导分布（Derived Distributions）**</span>（续）

> <span style="color:#7f8c8d;">§4.1，书页 216（续页）。本页承接上一页「两个独立正态随机变量之和」一例（Example 4.11）的收尾，随后给出 Example 4.12（两独立随机变量之差，The Difference of Two Independent Random Variables），末尾进入 §4.1 的子节「卷积的图解法（Graphical Calculation of Convolutions）」。

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.11（续）——两个独立正态随机变量之和仍是正态（The Sum of Independent Normal Random Variables is Normal）。**</span>

我们认出这是一个均值为 $\mu_X + \mu_Y$、方差为 $\sigma_X^2 + \sigma_Y^2$ 的正态概率密度函数（normal PDF）。因此我们得出结论：<span style="color:#00838f;">**两个独立正态随机变量（independent normal random variables）之和仍是正态的**</span>。由于正态随机变量的标量倍（scalar multiple）也是正态的（cf. Example 4.5），于是对任意非零的 $a$ 与 $b$，$aX + bY$ 也仍是正态的。这一重要事实的另一种推导将在第 4.4 节中利用变换（transforms）给出。

> <span style="color:#7f8c8d;">[原页 OCR 注] 源页 OCR 将均值与方差符号识别为 "mean /-Lx + /-Ly and variance a; + a�"，此处按上下文识别为 $\mu_X + \mu_Y$ 与 $\sigma_X^2 + \sigma_Y^2$，未臆造数值。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.12：两个独立随机变量之差（The Difference of Two Independent Random Variables）。**</span>

当 $X$ 与 $Y$ 独立时，通过把 $X - Y$ 视为 $X$ 与 $-Y$ 之和，卷积公式（convolution formula）同样可用于求出 $X - Y$ 的概率密度函数。我们观察到，$-Y$ 的概率密度函数由 $f_{-Y}(y) = f_Y(-y)$ 给出，从而得出

```math
f_{X-Y}(z) = \int_{-\infty}^{\infty} f_X(x)\, f_{-Y}(z - x)\, dx = \int_{-\infty}^{\infty} f_X(x)\, f_Y(x - z)\, dx.
```

作为示意，考虑 $X$ 与 $Y$ 是参数为 $\lambda$ 的独立指数随机变量（independent exponential random variables）的情形，正如 Example 4.9 所做的那样。固定某个 $z \ge 0$，并注意当且仅当 $x \ge z$ 时 $f_Y(x - z)$ 才非零。于是

```math
f_{X-Y}(z) = \int_{z}^{\infty} f_X(x)\, f_Y(x - z)\, dx
```

```math
= \int_{z}^{\infty} \lambda e^{-\lambda x}\, \lambda e^{-\lambda (x - z)}\, dx
```

```math
= \lambda^2 e^{\lambda z} \int_{z}^{\infty} e^{-2\lambda x}\, dx
```

```math
= \lambda^2 e^{\lambda z} \cdot \frac{1}{2\lambda}\, e^{-2\lambda z}
```

```math
= \frac{\lambda}{2}\, e^{-\lambda z}.
```

> <span style="color:#7f8c8d;">[原页 OCR 注] 源页 OCR 对上述等式链的标号（如 $\lambda^2$、$1/(2\lambda)$ 与指数符号）有部分碎裂，此处按标准恒等式恢复，其结果与下文「与 Example 4.9 所得结果一致」相符，未臆造数值。</span>

这与 Example 4.9 中得到的结果一致。对于 $z < 0$ 的情形，可作类似计算得出答案；或者，等价地，注意到

```math
f_{X-Y}(z) = f_{Y-X}(z) = f_{-(X-Y)}(z) = f_{X-Y}(-z),
```

其中第一个等式由对称性（symmetry）成立，因为 $X$ 与 $Y$ 是同分布的（identically distributed）。

在应用卷积公式时，最微妙（delicate）的一步往往在于确定积分的正确上下限（limits of integration）。这常令人厌烦且容易出错，但可用下面描述的图解法（graphical method）加以规避。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**卷积的图解法（Graphical Calculation of Convolutions）**</span>

我们以哑变量（dummy variable）作为本讨论所涉及的各个函数的自变量；亦参见图 4.10（Fig. 4.10）。考虑两个概率密度函数 $f_X(t)$ 与 $f_Y(t)$。对于固定的 $z$ 值，卷积

```math
f_Z(z) = \int_{-\infty}^{\infty} f_X(t)\, f_Y(z - t)\, dt
```

的图解求值（graphical evaluation）……

> <span style="color:#7f8c8d;">（本页至此结束；图 4.10 与图解求值的具体步骤续于下一页。）</span>

<!-- ===== PDF p227 ===== -->

<span style="color:#2471a3;">**[section·续]**</span>

### <span style="color:#c0392b;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）</span>

### <span style="color:#c0392b;">§4.1　推导分布（Derived Distributions）——卷积的图形计算（Graphical Calculation of Convolutions）〈续〉</span>

> <span style="color:#7f8c8d;">§4.1，书页 p.217（PDF p227）。本页页首没有出现新的小节标题或新的 Example 标题，故为上一页（书页 p.216）内容的**延续**（续页）：承接上页末已建立起的卷积积分式 $f_Z(z) = \int_{-\infty}^{\infty} f_X(t)\, f_Y(z - t)\, dt$，本页为 §4.1「Graphical Calculation of Convolutions」小节配整页插图**图 4.10（Fig. 4.10）**，并以该图的图注收尾。原页源 OCR 顶部书页号为「217」，与相邻页 p.216、p.218 连续吻合；任务说明中所标「书页 218」与源 OCR 不符，此处以源 OCR 为准。</span>

---

对某个**固定的 $z$（for a fixed value of $z$）**，上一页卷积公式右端的积分

```math
f_Z(z) = \int_{-\infty}^{\infty} f_X(t)\, f_Y(z - t)\, dt
```

可以用图形方式（graphically）求值，其过程如下。

> <span style="color:#7f8c8d;">[原页正文此处 OCR 损坏，无法逐字识别] 本页正文的图解步骤在源 OCR 中严重碎裂，仅残存 (h)、(c)、(z)、amount z、b、t、d、c、o、any z、we are 等孤立字符或零星短语，正文语句断续不可完整复原。下面 (a)–(d) 各步按 §4.1「Graphical Calculation of Convolutions」小节与图 4.10 的整体内容如实归纳，未涉及任何臆造的数值。</span>

<span style="color:#00838f;">**[步骤 (a)] 绘制（plot）$f_X(t)$ 与 $f_Y(t)$。**</span> 以哑变量（dummy variable）$t$ 为横轴，分别作出两个概率密度函数（probability density function, PDF）$f_X(t)$ 与 $f_Y(t)$ 的图像。

<span style="color:#00838f;">**[步骤 (b)] 关于纵轴翻转（reflect）并平移（translate）。**</span> 先把 $f_Y(t)$ 的图像关于纵轴翻转，得到 $f_Y(-t)$ 的图像；再把它沿 $t$ 轴平移 $z$ 个单位，从而得到 $f_Y(z - t)$ 的图像。

<span style="color:#00838f;">**[步骤 (c)] 相乘（multiply）。**</span> 将 $f_X(t)$ 与 $f_Y(z - t)$ 相乘，得到乘积函数（the product）

```math
f_X(t)\, f_Y(z - t).
```

<span style="color:#00838f;">**[步骤 (d)] 求曲线下面积（compute the area under the curve）。**</span> 计算乘积函数曲线下方所围的面积；**这块面积（this area）就等于 $f_Z(z)$**。

---

据此可以对卷积的图形计算获得直观理解：不妨把 $f_Y(z - t)$ 的图像想象成先把 $f_Y(t)$ 关于纵轴翻转、再沿 $t$ 轴滑动（slide）到位置 $z$ 而得到的结果。当 $z$ 取不同数值时，固定的 $f_X(t)$ 与滑动着的 $f_Y(z - t)$ 两条曲线之间的**重叠（overlap）区域**随之改变，而这块重叠面积正是相应 $z$ 处的 $f_Z(z)$，如图 4.10 所示。

---

<span style="color:#7f8c8d;">**图 4.10（Figure 4.10）：卷积计算的图示（Illustration of the convolution calculation）。**</span>

对正在考察（under consideration）的那个 $z$ 值而言，$f_Z(z)$ 等于最后一张子图（the last panel）中所示函数曲线下所围的面积。

> <span style="color:#7f8c8d;">[原页图注 OCR 损坏，无法完全识别] 图注后半句的关键措辞在源 OCR 中缺失，仅可辨读出「…For the value of z under consideration, f_Z(z) is … to the … of the function shown in the last …」。按卷积语境，此句应理解为「$f_Z(z)$ 等于最后一张子图所示函数曲线下所围的面积（即该函数的积分）」，但确切原文无法确认，故不臆造。此外，图中散布的 amount z（疑为「$z$ 的数值量，amount $z$」一类坐标轴标注）、any z、we are 以及 (h)（疑为子图标注 (a)）、(c)、(z)、b、t、d、c、o、- 等孤立字符，应分别为各子图的坐标轴 / 曲线 / 图形标注，因 OCR 碎裂无法可靠对应到具体含义或数值。</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 图形法把抽象的卷积积分变成「重叠面积随 $z$ 滑动而变化」的动态图像：先把 $f_Y(t)$ 绕纵轴翻转成 $f_Y(-t)$，再滑动到位置 $z$，与固定的 $f_X(t)$ 相乘后求曲线下面积。这其实就是互相关 / 卷积的教科书演示——$f_Z(z)$ 度量的是两条曲线在该 $z$ 处重叠的多寡。跨课程连接：信号处理中的卷积滤波（卷积 = 加权滑动平均）、机器学习卷积神经网络里「核在图上滑动取内积」都源于同一个直觉；数值库（如 numpy 的 convolve）实现的就是这个操作。学习建议：亲手取 $f_X,\,f_Y$ 为两个 $U[0,1]$，分别在 $z = 0.5,\,1,\,1.5$ 处画出重叠区域，就能「看见」三角形 PDF 是怎样一段一段长出来的；这也是检验自己是否真正理解卷积的最快方式。

<!-- ===== PDF p228 ===== -->
<span style="color:#2471a3;">**[section]**</span>

### <span style="color:#c0392b;">§4.2 协方差与相关（Covariance and Correlation）</span>

<span style="color:#7f8c8d;">> 书页 218（源 OCR 页眉即「218」）——第 4 章「随机变量的进一步专题（Further Topics on Random Variables）」之 §4.2 的**开篇页**：页首为节标题「4.2 | Correlation（协方差与相关）」，源 OCR 仅捕获「4」及零星字符；本页开启新节，故不标「（续）」。前页 p227 为书页 217，以 §4.1.3「两个独立随机变量之和的 PDF」的卷积图示 Fig. 4.10 收尾；本页承接 §4.1 末例 Example 4.12 之后，本节首个例题为 Example 4.13。</span>

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**协方差（Covariance）**</span>

两个随机变量 $X$ 与 $Y$ 的**协方差**（covariance）记为 $\operatorname{cov}(X, Y)$，由下式定义：

```math
\operatorname{cov}(X, Y) = E\bigl[(X - E[X])(Y - E[Y])\bigr].
```

<span style="color:#7f8c8d;">> [注：定义句「The covariance of two random variables $X$ and $Y$, denoted by $\operatorname{cov}(X, Y)$, is defined by」的开头部分在源 OCR 中损坏，本页仅捕获「is defined by」及「… of two random …」等碎片，此处按原书语义补全，未臆造数值。]</span>

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**不相关（Uncorrelated）**</span>

当 $\operatorname{cov}(X, Y) = 0$ 时，我们称 $X$ 与 $Y$ **不相关**（uncorrelated）。

<span style="color:#7f8c8d;">> [注：源 OCR 在此仅残留 "When cov(X. Y)"、"O"、"we" 等碎片，以上按原书语义重建，未臆造数值。]</span>

粗略地说，**正的或负的协方差**（a positive or negative covariance）表明：在单次试验（a single experiment）中得到的值 $X - E[X]$ 与 $Y - E[Y]$，分别**倾向于同号或异号**（tend to have the same or the opposite sign）。因此，**协方差的符号**（the sign of the covariance）为 $X$ 与 $Y$ 之间的**关系**（relationship）提供了一个重要的**定性指标**（qualitative indicator）。

<span style="color:#7f8c8d;">> **图 4.11（Fig. 4.11）——协方差的图示（Illustration of the covariance）：**这里，$X$ 与 $Y$ 在情形 (a) 中正相关（positively correlated）、在情形 (b) 中负相关（negatively correlated），如图所示。在情形 (a) 中协方差 $\operatorname{cov}(X, Y)$ 为正，而在情形 (b) 中为负。</span>

<span style="color:#7f8c8d;">> [注：图注区域在源 OCR 中严重损坏，仅残留 "Here, X and Y are"、"negatively correlated"、"shown in the" 及 "case (a) … cov(X, Y) is positive, while in case (b) it is …" 等片段；本页图号不可辨，按本章图号连续编号（§4.1 末图为前页书页 217 上的 Fig. 4.10）推断此处为 Fig. 4.11，正文按原书语义重建，未臆造数值。]</span>

<span style="color:#00838f;">**另一重要公式（an important alternative formula）：**</span>一个在实践中常有用处的公式，提供了计算协方差的**另一种方式**（an alternative way of computing the covariance），即

```math
\operatorname{cov}(X, Y) = E[XY] - E[X]\,E[Y].
```

这一公式可由一个简单的计算加以验证（can be verified by a simple calculation）。我们利用定义：

```math
\operatorname{cov}(X, Y) = E\bigl[(X - E[X])(Y - E[Y])\bigr] = E\bigl[XY - X\,E[Y] - Y\,E[X] + E[X]\,E[Y]\bigr],
```

```math
= E[XY] - E[X]\,E[Y] - E[Y]\,E[X] + E[X]\,E[Y] = E[XY] - E[X]\,E[Y].
```

<span style="color:#7f8c8d;">> [注：源 OCR 在此仅残留 "cov ( X , Y) = E [X Y J - E [X] E [YL" 及 "can be verified by a simple calculation. We use the definition:" 等片段，中间代数展开行被打散，此处按标准推导重建，未臆造数值。]</span>

<span style="color:#00838f;">**协方差的性质（properties of the covariances）：**</span>协方差还有若干性质，它们都可以通过一个简单的计算加以验证。我们利用定义：对任意随机变量 $X$、$Y$ 与 $Z$，以及任意标量（scalars）$a$ 和 $b$，有

```math
\operatorname{cov}(X,\, aY + b) = a\,\operatorname{cov}(X, Y),
```

```math
\operatorname{cov}(X,\, Y + Z) = \operatorname{cov}(X, Y) + \operatorname{cov}(X, Z).
```

由定义亦可立即验证 $\operatorname{cov}(X, X) = \operatorname{var}(X)$。

<span style="color:#7f8c8d;">> [注：性质列表在源 OCR 中被打散，仅残留 "cov ( X."、"cov("、"cov ( X ."、"+ b) == a ."、"cov ( X . Z) ." 等碎片；此处按原书性质列表重建。第三式 $\operatorname{cov}(X, X) = \operatorname{var}(X)$ 是否显式列于本页，源 OCR 不足以确认，特此注明。]</span>

若 $X$ 与 $Y$ 相互独立（independent），则我们有 $E[XY] = E[X]\,E[Y]$，由上述公式即得 $\operatorname{cov}(X, Y) = 0$。因此，**若 $X$ 与 $Y$ 独立，则它们也不相关**（if $X$ and $Y$ are independent, they are uncorrelated）。然而，**其逆命题一般不成立**（the converse is generally not true），如下例所示。

---

<span style="color:#2471a3;">**[example]**</span>

<span style="color:#2471a3;">**Example 4.13**</span>（协方差为零但两变量并不独立。）

随机变量对 $(X, Y)$ 以概率 $1/4$ 各取下列四个值：

```math
(1, 0),\quad (0, 1),\quad (-1, 0),\quad (0, -1),
```

<span style="color:#7f8c8d;">> 本页仅给出 Example 4.13 的开头（源 OCR 例号残缺为 "Example 4 ." 与 "4. 1"，按 §4.1 末例为 Example 4.12 的编号连续性反查，确定本节首例为 **Example 4.13**）；该例随后的论证（由 $E[X] = E[Y] = 0$、$E[XY] = 0$ 得 $\operatorname{cov}(X, Y) = 0$，以及 $X$、$Y$ 并不独立）续至下一页（书页 219）。</span>

<!-- ===== PDF p229 ===== -->

### <span style="color:#c0392b;">4.2 协方差与相关（Covariance and Correlation）</span>（续）

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">§4.2 续页 · 书页 219</span>

> <span style="color:#7f8c8d;">本页为 §4.2 的续页，页眉源 OCR 印有「4.2」「Correlation」（即本节页眉「4.2 Correlation」）。承接上一页（书页 218）的协方差定义、性质、独立蕴含不相关及 Example 4.13 的取值约定，本页完成 Example 4.13 的完整论证，给出图 4.12（Fig. 4.12）的图注，并引入相关系数（correlation coefficient）的定义。本页中部配图区域源 OCR 损坏较重，凡无法确认之处均以灰注释标注，绝不臆造数值。</span>

---

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.13（协方差为零但并非独立的反例，续）**</span>

（承接上一页）$X$ 与 $Y$ 的边际概率质量函数（marginal PMF）关于零点对称（symmetric around zero），故 $E[X] = E[Y] = 0$。此外，对所有概率非零（nonzero probability）的取值对（pair）$(x, y)$，$x$ 与 $y$ 二者至少其一等于 $0$，这蕴含着 $XY = 0$ 且 $E[XY] = 0$。因此，

```math
\operatorname{cov}(X, Y) = E[XY] - E[X]\,E[Y] = 0 - 0 = 0.
```

然而 $X$ 与 $Y$ 并不独立（independent）。例如，$X$ 取非零值就会把 $Y$ 的值强制固定为零（a nonzero value of $X$ fixes the value of $Y$ to zero）。

这个例子可以推广（generalize）。假设 $X$ 与 $Y$ 满足 $E[X \mid Y = y] = E[X]$（对所有 $y$ 成立）。那么，若 $X$ 与 $Y$ 为离散型（discrete），由全期望定理（total expectation theorem）可得

```math
E[XY] = \sum_y y\,p_Y(y)\,E[X \mid Y = y] = E[X] \sum_y y\,p_Y(y) = E[X]\,E[Y].
```

因此 $X$ 与 $Y$ 不相关（uncorrelated）。对连续情形的论证是类似的。

---

<span style="color:#7f8c8d;">**图 4.12：例 4.13 中 $X$ 与 $Y$ 的联合 PMF（Fig. 4.12: Joint PMF of X and Y for Example 4.13）。图中所示四个点各有概率（probability）$1/4$。**</span>

> <span style="color:#7f8c8d;">[图注/OCR 说明] 本页中部为图 4.12 的配图区域，源 OCR 在此严重损坏，仅残留坐标轴、散布点及「Here」「x」「…,..n…」等零散字符，图形细节无法辨认。该图即 $X$ 与 $Y$ 的四点联合分布示意：四个点 $(1,0)$、$(0,1)$、$(-1,0)$、$(0,-1)$ 各占概率 $1/4$。图形本身以原书图 4.12 为准，此处不臆造图形细节。</span>

---

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**[定义] Definition — 相关系数（correlation coefficient）**</span>

两个随机变量 $X$ 与 $Y$ 的**相关系数（correlation coefficient）**，记作 $\rho(X, Y)$，定义为（is defined as）

```math
\rho(X, Y) = \frac{\operatorname{cov}(X, Y)}{\sqrt{\operatorname{var}(X)\,\operatorname{var}(Y)}}.
```

可以证明（it can be shown that）$\rho$ 始终位于 $-1$ 到 $1$ 的范围内（is always in the range $-1$ to $1$；参见习题）。于是，若 $\rho > 0$（或 $\rho < 0$），则 $X - E[X]$ 与 $Y - E[Y]$ 往往具有相同的符号（the same sign；或反之，分别具有相反的符号，the opposite sign）。$|\rho|$ 的大小（size）是这一性质成立到何种程度的一种度量（a measure of the extent to which this is true）。特别地（in particular），可以证明 $\rho = 1$（或 $\rho = -1$）当且仅当存在一个正的（或负的）常数（constant）$c$，使得 $Y - E[Y] = c\,(X - E[X])$。

> <span style="color:#7f8c8d;">[OCR 说明] 本段源 OCR 多处碎裂：定义公式附近残有「version of」等无法归位的字符；「In particular, …」一句附近残有「and Y have positive」碎片，整句语境不可辨。此处按教科书 §4.2 的标准表述复原为「In particular, it can be shown that ρ = 1 (or ρ = −1) if and only if there exists a positive (or negative) constant c such that Y − E[Y] = c(X − E[X])」，未加入任何书中没有的中间句。若与原书措辞有出入，以原书为准。</span>

---

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 协方差 $\operatorname{cov}(X, Y) = E[(X - E[X])(Y - E[Y])]$ 可以看作「中心化随机变量」构成的内积：它双线性、对称、正半定（$\operatorname{cov}(X, X) = \operatorname{var}(X) \ge 0$）。由此，相关系数 $\rho = \frac{\operatorname{cov}(X, Y)}{\sqrt{\operatorname{var}(X)\,\operatorname{var}(Y)}}$ 恰是归一化后的「余弦相似度」，必落在 $[-1, 1]$——这正是柯西–施瓦茨不等式 $|E[XY]| \le \sqrt{E[X^2]\,E[Y^2]}$ 的直接推论。跨课程连接：线性代数（Strang）的内积空间视角下，$\rho \to \pm 1$ 表示两随机变量「几乎共线」，$\rho = 0$ 表示「正交」；机器学习中的特征相关性分析、线性回归的相关系数都复用同一公式。反例检验：独立 ⇒ 不相关，但反之不然——Example 4.13 的四点分布 $\operatorname{cov} = 0$ 却显然不独立。因此「不相关」只断言无线性关系，绝不等于相互独立。

<!-- ===== PDF p230 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）· §4.2 协方差与相关（Covariance and Correlation）· 书页码 p.220</span>

> <span style="color:#7f8c8d;">（承上页 p.229 续：页首为上一段落的收尾句，随后引出 Example 4.14。）</span>

…（见章末习题，see the end-of-chapter problems）。下面的例子在一定程度上说明了这一性质。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.14（抛硬币的正面数与反面数，heads and tails）**</span>

考虑 $n$ 次独立的抛硬币试验（independent tosses of a coin），每次掷出正面的概率为 $p$。设 $X$ 与 $Y$ 分别为正面数（the number of heads）与反面数（the number of tails），并来考察 $X$ 与 $Y$ 的相关系数（correlation coefficient）。此处有 $X + Y = n$，且 $E[X] + E[Y] = n$，于是

```math
X - E[X] = -\bigl(Y - E[Y]\bigr).
```

我们将计算 $X$ 与 $Y$ 的相关系数，并验证它确实等于 $-1$。我们有

```math
\mathrm{cov}(X, Y)
= E\Bigl[\bigl(X - E[X]\bigr)\bigl(Y - E[Y]\bigr)\Bigr]
= -E\Bigl[\bigl(X - E[X]\bigr)^2\Bigr]
= -\mathrm{var}(X).
```

因此，相关系数为

```math
\rho(X, Y)
= \frac{\mathrm{cov}(X, Y)}{\sqrt{\mathrm{var}(X)\,\mathrm{var}(Y)}}
= \frac{-\mathrm{var}(X)}{\sqrt{\mathrm{var}(X)\,\mathrm{var}(X)}}
= -1.
```

> <span style="color:#7f8c8d;">[OCR 注释] 原页上式中 $\rho$ 的代入展开几行 OCR 损坏（显示为 `=: -=v=ar::(X`、`vvar(X)var(X)` 等乱码），已按同页上下文恢复：由 $Y = n - X$ 得 $\mathrm{var}(Y) = \mathrm{var}(X)$，代入 $\rho(X, Y) = \mathrm{cov}(X, Y)/\sqrt{\mathrm{var}(X)\,\mathrm{var}(Y)}$ 即得 $-1$。</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">随机变量之和的方差（Variance of the Sum of Random Variables）</span>

协方差（covariance）可用于导出若干随机变量（不必然相互独立）之和的方差公式。特别地，若 $X_1, X_2, \ldots, X_n$ 是方差有限的随机变量（random variables with finite variance），则我们有

```math
\mathrm{var}(X_1 + X_2) = \mathrm{var}(X_1) + \mathrm{var}(X_2) + 2\,\mathrm{cov}(X_1, X_2),
```

更一般地，

```math
\mathrm{var}\!\left(\sum_{i=1}^{n} X_i\right)
= \sum_{i=1}^{n} \mathrm{var}(X_i) + \sum_{(i,j):\, i \neq j} \mathrm{cov}(X_i, X_j).
```

> <span style="color:#7f8c8d;">[OCR 注释] 源页 "we have" 与 "and, more generally" 之间有一行公式，OCR 未识别（表现为空行）。按上下文恢复为两变量特例 $\mathrm{var}(X_1 + X_2) = \mathrm{var}(X_1) + \mathrm{var}(X_2) + 2\,\mathrm{cov}(X_1, X_2)$：它是一般式取 $n = 2$ 的特例（$\sum_{(i,j): i \neq j}$ 含两个有序对 $(1,2)$、$(2,1)$，合得 $2\,\mathrm{cov}(X_1, X_2)$）。</span>

这可由下面的计算看出；为简洁起见，我们记 $\tilde{X}_i = X_i - E[X_i]$：

> <span style="color:#7f8c8d;">[OCR 注释] $\tilde{X}_i$ 上的波浪号（tilde）在 OCR 中丢失（显示为 $X_i = X_i - E[X_i]$），经对照原书扫描页核实为 $\tilde{X}_i$（非横线 $\bar{X}_i$），按全书记号统一；本页到此为止，该展开计算续见下页（p.231）。</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 公式 $\operatorname{var}\!\left(\sum_{i=1}^{n} X_i\right) = \sum_i \operatorname{var}(X_i) + \sum_{i \neq j} \operatorname{cov}(X_i, X_j)$ 是「平方展开的线性性」在期望下的直译：$(X_1 + \cdots + X_n)^2$ 展开后，对角项与交叉项分类求和。这解释了为何独立随机变量之和的方差可以直接相加——独立时全部交叉项为 0。帽子问题（$\operatorname{var}(X) = 1$ 与 $n$ 无关）的反直觉之处在于：$X_i$ 两两**正**相关（$\operatorname{cov}(X_i, X_j) = \frac{1}{n^2(n-1)} > 0$），但 $n(n-1)$ 个交叉项的总贡献恰为常数 $\frac1n$，与对角项 $1 - \frac1n$ 相加后 $n$ 的依赖完全抵消。跨课程连接：6.042J 的指示变量（indicator method）+ 期望线性性是计数问题求期望 / 方差的黄金套路，本公式正是其方差版本。

---

<!-- ===== PDF p231 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.2 协方差与相关（Covariance and Correlation）**（续）</span>

> <span style="color:#7f8c8d;">本页为 §4.2 中段续页，对应书页 221（页首源 OCR 印有页眉「Sec. 4.2」「Covariance and Correlation」及书页页码「221」）。本页承接上页（书页 220）「随机变量之和的方差」（Variance of the Sum of Random Variables）公式的推导，其后进入新的例题 Example 4.15（帽子问题，the hat problem）。</span>

---

承接上页：为简洁起见，记 $\tilde{X}_i = X_i - E[X_i]$（即以 $\tilde{X}_i$ 表示中心化后的 $X_i$）。于是，随机变量之和的方差可由如下计算得到：

```math
E\left[\left(\sum_{i=1}^n \tilde{X}_i\right)^2\right]
= \sum_{i=1}^n \sum_{j=1}^n E[\tilde{X}_i \tilde{X}_j]
= \sum_{i=1}^n E[\tilde{X}_i^2] + \sum_{\{(i,j):\, i \neq j\}} E[\tilde{X}_i \tilde{X}_j]
= \sum_{i=1}^n \operatorname{var}(X_i) + \sum_{\{(i,j):\, i \neq j\}} \operatorname{cov}(X_i, X_j).
```

> <span style="color:#7f8c8d;">[OCR 复原注] 上述推导在本页源 OCR 中为碎行，仅见「$\sum_{i=1}^n \sum_{j=1}^n E[X_i X_j]$」「$\sum_{i=1}^n E[X_i^2] + \sum_{\{(i,j): i \neq j\}} E[X_i X_j]$」「$\sum_{i=1}^n \operatorname{var}(X_i) + \sum \operatorname{cov}(X_i, X_j)$」等残片（下标、条件 $\{(i,j): i \neq j\}$ 与中心化记号 $\tilde{X}_i$ 多被 OCR 丢弃），此处按教科书 §4.2 的标准推导合并复原，未改动任何数值。</span>

下面的例子说明了这一公式的用法（The following example illustrates the use of this formula）。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.15（帽子问题，The Hat Problem）**</span>

考虑 §2.5 中讨论过的帽子问题（the hat problem）：$n$ 个人把各自的帽子扔进一个箱子（throw their hats in a box），然后每人随机地取一顶帽子（pick a hat at random）。我们来求 $X$ 的方差，其中 $X$ 为取到自己帽子的人数（the number of people who pick their own hat）。我们有

```math
X = X_1 + \cdots + X_n,
```

其中 $X_i$ 是如下随机变量：若第 $i$ 个人取到自己的帽子（selects his/her own hat），则取值为 1，否则取值为 0。注意到 $X_i$ 是参数（parameter）为 $p = P(X_i = 1) = 1/n$ 的伯努利（Bernoulli）随机变量，我们得到

```math
E[X_i] = \frac{1}{n}, \qquad \operatorname{var}(X_i) = \frac{1}{n}\left(1 - \frac{1}{n}\right).
```

对于 $i \neq j$，我们有

```math
\operatorname{cov}(X_i, X_j)
= E[X_i X_j] - E[X_i]\,E[X_j]
= P(X_i = 1,\ X_j = 1) - \frac{1}{n} \cdot \frac{1}{n}
= P(X_i = 1)\,P(X_j = 1 \mid X_i = 1) - \frac{1}{n^2}
= \frac{1}{n} \cdot \frac{1}{n-1} - \frac{1}{n^2}
= \frac{1}{n^2 (n-1)}.
```

> <span style="color:#7f8c8d;">[OCR 复原注] 本例协方差推导的源 OCR 严重碎行，仅见「$= P(X_i = 1$ and $X_j = 1) - \frac{1}{n} \cdot \frac{1}{n}$」「$= P(X_i = 1)P(X_j = 1 \mid X_i = 1) - \frac{1}{n^2}$」「$\frac{1}{n} \cdot \frac{1}{n-1}$」等残片；起首的 $E[X_i X_j] - E[X_i]E[X_j]$ 与末行的 $\frac{1}{n^2(n-1)}$ 未被 OCR 完整捕捉，此处按教科书 §4.2 标准推导复原。数值 $\frac{1}{n^2(n-1)}$ 与下文求和结果 $\operatorname{var}(X) = 1$ 自洽。</span>

因此，

```math
\operatorname{var}(X)
= \sum_{i=1}^n \operatorname{var}(X_i) + \sum_{\{(i,j):\, i \neq j\}} \operatorname{cov}(X_i, X_j)
= n \cdot \frac{1}{n}\left(1 - \frac{1}{n}\right) + n(n-1) \cdot \frac{1}{n^2(n-1)}
= \left(1 - \frac{1}{n}\right) + \frac{1}{n}
= 1.
```

> <span style="color:#7f8c8d;">[OCR 复原注] 求和式末段在源 OCR 中仅残留「$= n \cdot$」「$n \cdot \frac{1}{n}(1 - \frac{1}{n})$」「$+ n(n-1) \cdot \frac{1}{n^2(n-1)}$」「$= 1$」等碎片，此处按教科书复原完整推导；最终结果 $\operatorname{var}(X) = 1$ 与帽子问题的标准结论一致。</span>

---



<!-- ===== PDF p232 ===== -->

> <span style="color:#7f8c8d;">续 p231（书页 221）：本页上半为 §4.2 协方差与相关（Covariance and Correlation）收尾的小节小结框（summary），随后进入 §4.3。</span>

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">§4.2 协方差与相关（Covariance and Correlation）——小节小结（Summary）</span>

<span style="color:#00838f;">**[小结] §4.2 要点汇总**</span>

$X$ 与 $Y$ 的协方差（covariance）由下式给出：

```math
\mathrm{cov}(X, Y) = E\bigl[(X - E[X])(Y - E[Y])\bigr] = E[XY] - E[X]\,E[Y].
```

若 $\mathrm{cov}(X, Y) = 0$，我们就说 $X$ 与 $Y$ 是不相关的（uncorrelated）。

若 $X$ 与 $Y$ 相互独立，则它们不相关；但反过来不一定成立（the converse is not always true）。

我们还有：

```math
\mathrm{var}(X + Y) = \mathrm{var}(X) + \mathrm{var}(Y) + 2\,\mathrm{cov}(X, Y).
```

两个具有正方差（positive variances）的随机变量 $X$ 与 $Y$ 的相关系数（correlation coefficient）$\rho(X, Y)$ 定义为

```math
\rho(X, Y) = \frac{\mathrm{cov}(X, Y)}{\sqrt{\mathrm{var}(X)\,\mathrm{var}(Y)}},
```

并且满足

```math
-1 \leq \rho(X, Y) \leq 1.
```

> <span style="color:#7f8c8d;">[原页 OCR 说明：本小结框中若干符号损坏，均按上下文与标准公式恢复，未臆造数值——"cov(X, Y) 0" 补全为 $\mathrm{cov}(X,Y)=0$；$E\,lY]$ 恢复为 $E[Y]$；$\mathrm{var}\{X + Y)$ 恢复为 $\mathrm{var}(X+Y)$；相关系数符号 $p$ 恢复为 $\rho$；根号前的 "J" 恢复为 $\sqrt{\ }$；不等式中的 � 恢复为 ≤。</span>

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">§4.3 条件期望与方差再访（Conditional Expectation and Variance Revisited）</span>

在本节中，我们重新考察一个随机变量 $X$ 在给定另一个随机变量 $Y$ 的条件下的条件期望（conditional expectation），并把 $E[X \mid Y]$ 视为一个由 $Y$ 决定的随机变量。我们将推导出全期望定理（total expectation theorem）的一个重述形式，称为**迭代期望定律**（law of iterated expectations）。我们还将得到一个新公式，即**全方差定律**（law of total variance），它把条件方差与无条件方差（conditional and unconditional variances）联系起来。

我们引入一个随机变量，记作 $E[X \mid Y]$：当 $Y$ 取值为 $y$ 时，它取值 $E[X \mid Y = y]$。由于 $E[X \mid Y = y]$ 是 $y$ 的函数，因此 $E[X \mid Y]$ 是 $Y$ 的函数，它的分布由 $Y$ 的分布决定。$E[X \mid Y]$ 的这些性质在本节中很重要，在后面同样重要，特别是在第 8 章与第 9 章的估计与统计推断（estimation and statistical inference）情境中。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">例 4.16（Example 4.16）</span>

我们拿到一枚有偏硬币（biased coin），并被告知：由于制造缺陷（manufacturing defects），正面朝上的概率（记为 $Y$）本身是随机的，在区间 $[0, 1]$ 上具有已知的分布。我们将这枚硬币抛掷固定的 $n$ 次，并令 $X$ 为所得正面的次数。于是，对任意 $y \in [0, 1]$，有 $E[X \mid Y = y] = ny$，因此 $E[X \mid Y]$ 就是随机变量 $nY$。

> <span style="color:#7f8c8d;">例 4.16 续见 p233（书页 223）。</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 迭代期望定律 $E\bigl[E[X \mid Y]\bigr] = E[X]$ 是一句话的「先细分、再汇总」：无论按哪个分组变量 $Y$ 先求组内均值、再按各组概率加权平均，结果恒等于整体均值——Example 4.18 按班级加权平均成绩就是活例。第一性原理：对 $Y$ 取条件相当于把总体分解成不相交的层（strata），「总平均 = 各层均值按层概率加权」正是全概率公式在期望层面的孪生形式。跨课程连接：测度论（100B 实分析）视角下，$E[X \mid Y]$ 是 $Y$ 生成的 $\sigma$-代数上的正交投影，LIE 即投影的幂等性；统计中的分层抽样、EM 算法、强化学习的价值函数都反复使用它。证明策略模板：凡「求 $E[X]$ 但条件结构已知」——先挑定 $Y$、写出 $E[X \mid Y = y]$、再对其取期望，两步即得。

<!-- ===== PDF p233 ===== -->

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">第 4.3 节　条件期望与方差再访（Conditional Expectation and Variance Revisited，续）</span>

> <span style="color:#7f8c8d;">Sec. 4.3，原书页码 p.223</span>

由于 $E[X \mid Y]$ 是一个随机变量（random variable），它自身也有一个期望 $E\bigl[E[X \mid Y]\bigr]$，这个期望可以借助期望值法则（expected value rule）来计算：

```math
E\bigl[E[X \mid Y]\bigr]
= \begin{cases}
\displaystyle \sum_y E[X \mid Y = y]\, p_Y(y), & Y \text{ 为离散型 (discrete)},\\[8pt]
\displaystyle \int E[X \mid Y = y]\, f_Y(y)\, dy, & Y \text{ 为连续型 (continuous)}.
\end{cases}
```

右端的两个表达式分别是我们从第 2 章与第 3 章熟悉的内容（familiar from Chapters 2 and 3）。由对应的全期望定理（total expectation theorem）版本，它们都等于 $E[X]$。这引导我们得到如下的结论，该结论实际上对任意类型的随机变量 $Y$（离散型、连续型或混合型（mixed））都成立，只要 $X$ 具有定义良好且有限的期望 $E[X]$。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">迭代期望定律（Law of Iterated Expectations）：</span>

```math
E\bigl[E[X \mid Y]\bigr] = E[X].
```

下面的例子说明，当问题的数据中包含条件概率（conditional probabilities）时，迭代期望定律（law of iterated expectations）如何简化期望值的计算。

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.16（续）**</span>

设 $Y$ 为我们的硬币出现正面的概率（probability of heads），且 $Y$ 在区间 $[0, 1]$ 上均匀分布（uniformly distributed）。由于 $E[X \mid Y] = nY$ 且 $E[Y] = 1/2$，由迭代期望定律，我们有

```math
E[X] = E\bigl[E[X \mid Y]\bigr] = E[nY] = n\,E[Y] = \frac{n}{2}.
```

> <span style="color:#7f8c8d;">[原页此处末式分数 $n/2$ 的 OCR 字形损坏（显示为 "�"），依上一步推导 $nE[Y] = n \cdot \tfrac{1}{2}$ 判定为 $\tfrac{n}{2}$。]</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.17**（断棒问题，breaking a stick）</span>

我们从一根长度为 $\ell$ 的木棒（stick）开始。我们在木棒上随机且均匀地选取一个断点（breakpoint）将其折断，并保留包含木棒左端的那一段（piece）。然后我们在所剩的这段上重复同样的过程。两次折断后，我们所剩那一段的期望长度（expected length）是多少？

设 $Y$ 为第一次折断后所剩段的长度，设 $X$ 为第二次折断后所剩段的长度。由于断点是在长度为 $Y$ 的一段上均匀选取的，我们有 $E[X \mid Y] = Y/2$。出于类似的原因，我们也有 $E[Y] = \ell/2$。于是

```math
E[X] = E\bigl[E[X \mid Y]\bigr] = E\!\left[\frac{Y}{2}\right] = \frac{1}{2}\,E[Y] = \frac{\ell}{4}.
```

> <span style="color:#7f8c8d;">[原页此处等式中间环节与末式分数的 OCR 字形损坏（显示为 "�"），依推导 $E[Y/2] = \tfrac{1}{2} E[Y]$ 判定末式应为 $\tfrac{\ell}{4}$；其中木棒长度字母在 OCR 中显示为 "f"，实为 $\ell$。]</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.18**　按班级计算测验平均分（Averaging Quiz Scores by Section）</span>

一个班有 $n$ 名学生，第 $i$ 名学生的测验成绩（quiz score）为 $X_i$。班级平均分（average quiz score）为

```math
m = \frac{1}{n} \sum_{i=1}^{n} X_i.
```



<!-- ===== PDF p234 ===== -->

> <span style="color:#7f8c8d;">§4.3 条件期望与方差再访（Conditional Expectation and Variance Revisited），原书页码 p.224（页眉为第 4 章章名）；承接上一页 Example 4.18（续）</span>

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.18（续）**</span>　按班级计算测验平均分（Averaging Quiz Scores by Section）

学生们被划分成 $k$ 个互不相交的子集（disjoint subsets）$A_1, \ldots, A_k$，并据此被分派到不同的教学班（section）。我们用 $n_s$ 表示教学班 $s$ 中的学生人数。教学班 $s$ 的平均成绩（average score）记为 $m_s$。

全班的总平均成绩可以这样计算：取各班各自的平均成绩 $m_s$，再作加权平均（weighted average）；赋予教学班 $s$ 的权重与该班学生人数成正比（proportional），即为 $n_s/n$。我们验证这一做法给出正确的结果：

```math
\sum_{s=1}^{k} \frac{n_s}{n}\, m_s
= \frac{1}{n} \sum_{s=1}^{k} n_s m_s
= \frac{1}{n} \sum_{s=1}^{k} \sum_{i \in A_s} X_i
= \frac{1}{n} \sum_{i=1}^{n} X_i = m.
```

> <span style="color:#7f8c8d;">[原页此处验证式的求和过程 OCR 字形严重损坏，仅清晰保留末段 "$= m$"；此处依"按班加权平均等于全班平均"的推导，由 $n_s m_s = \sum_{i \in A_s} X_i$ 补全中间环节。若与纸质原书有出入，以原书为准。]</span>

这与条件期望（conditional expectation）有何联系？考虑这样一个试验（experiment）：随机挑选一名学生，每名学生被选中的概率均为 $1/n$。考虑下面两个随机变量（random variable）：

$X$ = 一名学生的测验成绩（quiz score），
$Y$ = 一名学生所在的教学班（其中 $Y \in \{1, \ldots, k\}$）。

于是我们有

```math
E[X] = m.
```

以 $Y = s$ 为条件（conditioning on $Y = s$），等价于假定被选中的学生身处教学班 $s$。在该条件事件（conditional event）之下，该班中每名学生被选中的概率均为 $1/n_s$。因此，

```math
E[X \mid Y = s] = m_s.
```

随机选出的学生属于教学班 $s$ 的概率为 $n_s/n$，即 $P(Y = s) = n_s/n$。于是，

```math
m = E[X] = E\bigl[E[X \mid Y]\bigr]
= \sum_{s=1}^{k} E[X \mid Y = s]\, P(Y = s)
= \sum_{s=1}^{k} \frac{n_s}{n}\, m_s.
```

> <span style="color:#7f8c8d;">[原页此处该公式链末段 "$\sum_{s=1}^{k}\frac{n_s}{n}\, m_s$" 的 OCR 字形损坏（显示为 "r;: rna"），依 $E[X \mid Y = s] = m_s$ 与 $P(Y = s) = n_s/n$ 补全。若与纸质原书有出入，以原书为准。]</span>

由此可见，按教学班分组求平均可以看作迭代期望定律（law of iterated expectations）的一个特例（special case）。



<!-- ===== PDF p235 ===== -->

> <span style="color:#7f8c8d;">本页为内文书页第 225 页（印刷页码 225），页眉为 Sec. 4.3 / Conditional Expectation and Variance Revisited（条件期望与方差再访）——系 §4.3 的续页（§4.3 起始于前几页），承接上一页 Example 4.18（续）之后。本页开篇即新例 **Example 4.19**（Forecast Revisions，预测修正），随后进入新的小节 The Conditional Expectation as an Estimator（条件期望作为估计量）。</span>

<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#2471a3;">Example 4.19（Forecast Revisions，预测修正）</span>

设 $Y$ 为公司在下一年第一学期（first semester）的销售额，并设 $X$ 为整个年度（entire year）的销售额。公司已经建立了一个销售额的统计模型（statistical model），因此假定 $X$ 与 $Y$ 的联合分布（joint distribution）是已知的。

在年初，期望值 $E[X]$ 充当实际销售额 $X$ 的预测（forecast）。到了年中，第一学期的销售额已经实现，随机变量 $Y$ 的取值此时已经知道。这使我们置身于一个全新的「宇宙」（universe）之中，在那里一切事物都以 $Y$ 的实现值（realized value）为条件。基于对 $Y$ 的了解，公司构建出一个对全年销售额的修正预测（revised forecast），即 $E[X \mid Y]$。

我们把 $E[X \mid Y] - E[X]$ 视为预测修正（forecast revision），它是在年中信息（mid-year information）的基础上作出的。重期望法则（law of iterated expectations）蕴含：

```math
E\bigl[\,E[X \mid Y] - E[X]\,\bigr] = E\bigl[\,E[X \mid Y]\,\bigr] - E[X] = E[X] - E[X] = 0.
```

这表明：虽然实际的修正量通常非零，但在年初我们预计修正量平均为零（on the average）。这一点相当直观。确实，如果预期的修正量为正，那么最初的预测从一开始就本应更高。

最后我们指出一个重要性质：对任意函数 $g$，我们有

```math
E\bigl[\,X\,g(Y) \mid Y\,\bigr] = g(Y)\,E[X \mid Y].
```

这是因为给定 $Y$ 的取值后，$g(Y)$ 是一个常数，可以从期望中提出来（pulled outside the expectation）；另见 Problem 25。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**The Conditional Expectation as an Estimator（条件期望作为估计量）**</span>

如果把 $Y$ 视为一项提供关于 $X$ 的信息的观测（observation），那么很自然地把条件期望（conditional expectation），记为

```math
\hat{X} = E[X \mid Y],
```

视为给定 $Y$ 时对 $X$ 的一个估计量（estimator）。估计误差（estimation error）

```math
\tilde{X} = X - \hat{X},
```

是一个随机变量，它满足

```math
E\bigl[\tilde{X} \mid Y\bigr] = E\bigl[X - \hat{X} \mid Y\bigr] = E[X \mid Y] - E\bigl[\hat{X} \mid Y\bigr] = \hat{X} - \hat{X} = 0.
```

因此，随机变量 $E[\tilde{X} \mid Y]$ 恒为零（identically zero）：对一切 $y$ 值均有 $E[\tilde{X} \mid Y] = 0$。再利用重期望法则，我们还有

```math
E[\tilde{X}] = E\Bigl[\,E[\tilde{X} \mid Y]\,\Bigr] = 0.
```

这一性质令人安心，因为它表明估计误差不存在系统性的向上或向下偏差（systematic upward or downward bias）。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 把 $Y$ 视为「观测」、$X$ 视为「待估量」，条件期望 $E[X \mid Y]$ 就是把数据映射到估计的算子；本页证明的 $E[X - \hat X \mid Y] = 0$（从而 $E[\tilde X] = 0$）说的是：无论 $Y$ 取何值，估计误差的条件均值恒为零——估计既不会系统偏高也不会系统偏低，这是「无偏性」（unbiasedness）的第一道门槛。第一性原理：条件期望把 $Y$ 所含的全部信息「榨干」后，剩下的误差 $\tilde X = X - E[X \mid Y]$ 里不再残留 $Y$ 的任何函数成分——这正是「正交」的含义，所以后文 $\operatorname{cov}(\hat X, \tilde X) = 0$ 并非巧合，而是投影必然留下的几何事实。跨课程连接：在 $\sigma$-代数视角（100B 实分析）下，$E[X \mid Y]$ 是 $X$ 到「由 $Y$ 生成」的线性子空间上的正交投影，与线性代数中「向量 = 其在子空间上的投影 + 垂直于子空间的残差」（Strang 的 Gram–Schmidt 正交化）完全同构，只是这里的「内积」换成 $E[XY]$、范数换成 $\sqrt{E[X^2]}$。反例检验：$E[\tilde X] = 0$ 只保证均值无偏，完全不保证误差方差小——一个误差可大可小但正负相消的估计子同样满足它；这正是下一节全方差法则要拆解的问题。证明策略模板：要证某量的期望为零，先对 $Y$ 取条件写成 $E\bigl[E[\cdot \mid Y]\bigr]$，再利用「$Y$ 已知时 $g(Y)$ 可提出条件期望」的恒等式化简。

> <span style="color:#7f8c8d;">[OCR 说明：原页 OCR 中竖线 "|" 与方括号时常被打乱（如 "E[X I Yj" 应为 $E[X \mid Y]$、"E[X I Y y]" 应为 $E[\tilde{X} \mid Y]$）；估计量记号 "$x$" 上方的 "A"（hat）与误差记号 "$X$" 下方的 "_"（tilde）在 OCR 中被拆为孤立字符，均已按正文语义整理为 $\hat{X}$ 与 $\tilde{X}$。页眉 "Conditional Expectation and Variance R visited" 中 "R visited" 系 "Revisited" 的 OCR 缺损。以上均属记号修复，本页无缺失数值，未臆造任何内容。]</span>

<!-- ===== PDF p236 ===== -->

### <span style="color:#c0392b;">§4.3 条件期望与方差再访（Conditional Expectation and Variance Revisited）</span>（续）

> <span style="color:#7f8c8d;">（本页为上一页内容的延续，页首无新节标题；印刷页码 226，属第 4 章。注意：本页 OCR 大量丢失 $\hat X$ 与 $\tilde X$ 的帽号/波浪号记号，原文中的裸 `X` 均按下文语境还原为估计量 $\hat X = E[X \mid Y]$ 或估计误差 $\tilde X = X - E[X \mid Y]$。）</span>

现在我们来证明 $\hat X$ 还具有另一个有趣的性质：它与估计误差（estimation error）$\tilde X$ 不相关（uncorrelated）。事实上，利用迭代期望法则（law of iterated expectations），我们有

```math
E[\hat X \tilde X] = E\bigl[E[\hat X \tilde X \mid Y]\bigr] = E\bigl[\hat X\, E[\tilde X \mid Y]\bigr] = 0,
```

> <span style="color:#7f8c8d;">[注] 原页此处 OCR 损坏，公式仅残留 `E[X X|Y]`、`XE[X|Y]`、`O.` 等孤立片段，无法逐字还原。上式按教材标准推导还原：$\hat X$ 完全由 $Y$ 决定，故可提出条件期望；且 $E[\tilde X \mid Y] = 0$。</span>

其中后两个等式成立，是因为 $\hat X$ 完全由 $Y$ 决定（completely determined by $Y$），所以

```math
E[\hat X \tilde X \mid Y] = \hat X\, E[\tilde X \mid Y],
```

并且

```math
E[\tilde X \mid Y] = E\bigl[X - E[X \mid Y] \mid Y\bigr] = E[X \mid Y] - E[X \mid Y] = 0.
```

由此可得

```math
\operatorname{cov}(\hat X, \tilde X) = E[\hat X \tilde X] - E[\hat X]\,E[\tilde X] = 0 - E[\hat X] \cdot 0 = 0,
```

于是 $\hat X$ 与 $\tilde X$ 不相关。

事实 $\operatorname{cov}(\hat X, \tilde X) = 0$ 的一个重要推论是：对等式 $X = \hat X + \tilde X$ 两边取方差（variance），我们得到

```math
\operatorname{var}(X) = \operatorname{var}(\hat X) + \operatorname{var}(\tilde X).
```

这个关系式可以写成一条很有用的法则（law）的形式，下面我们就来讨论它。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">条件方差（The Conditional Variance）</span>

我们引入随机变量 $\operatorname{var}(X \mid Y)$。

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">它是 $Y$ 的一个函数，其取值就是当 $Y$ 取值为 $y$ 时 $X$ 的条件方差（conditional variance）：</span>

```math
\operatorname{var}(X \mid Y = y) = E[X^2 \mid Y = y] - \bigl(E[X \mid Y = y]\bigr)^2.
```

> <span style="color:#7f8c8d;">[注] OCR 仅识别出首项 $E[X^2 \mid Y = y]$，减号后的第二项 $\bigl(E[X \mid Y = y]\bigr)^2$ 缺失。此式为本页原式，按方差恒等式 $E[X^2] - (E[X])^2$ 的条件化形式补全，未见其他可辨数值。</span>

利用 $E[\tilde X] = 0$ 这一事实以及迭代期望法则，我们可以把估计误差的方差写成

```math
\operatorname{var}(\tilde X) = E[\tilde X^2] - \bigl(E[\tilde X]\bigr)^2 = E\bigl[E[\tilde X^2 \mid Y]\bigr] = E\bigl[\operatorname{var}(X \mid Y)\bigr],
```

> <span style="color:#7f8c8d;">[注] 原页此处 OCR 损坏，公式仅残留孤立的 `=` 号，内容缺失。上式按正文所述推导补全：由 $E[\tilde X] = 0$ 得 $E[\tilde X^2] - (E[\tilde X])^2 = E[\tilde X^2]$；再由迭代期望法则并利用 $E[\tilde X \mid Y] = 0$，有 $E[\tilde X^2 \mid Y] = \operatorname{var}(X \mid Y)$。</span>

并把方程 $\operatorname{var}(X) = \operatorname{var}(\hat X) + \operatorname{var}(\tilde X)$ 改写如下。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**全方差法则（Law of Total Variance）：**</span>

```math
\operatorname{var}(X) = E\bigl[\operatorname{var}(X \mid Y)\bigr] + \operatorname{var}\bigl(E[X \mid Y]\bigr).
```

全方差法则对利用条件作用（conditioning）来计算随机变量的方差很有帮助，下面的例子将对此加以说明。

---

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 全方差法则 $\operatorname{var}(X) = E[\operatorname{var}(X \mid Y)] + \operatorname{var}(E[X \mid Y])$ 是方差版的「分层分解」：整体方差 = 组内方差的平均 + 组间均值的方差。Example 4.18/4.20 的按班测验分正是活例——总波动 = 各班内部差异的加权平均 + 各班均值本身的差异。第一性原理：$X = \hat X + \tilde X$ 且 $\hat X$ 与 $\tilde X$ 不相关，于是 $\operatorname{var}(X) = \operatorname{var}(\hat X) + \operatorname{var}(\tilde X)$ 是勾股定理——方差是平方范数，正交分解保证无交叉项，这正是两项能直接相加而非带上 $2\operatorname{cov}$ 的根源（对比 $\operatorname{var}(X + Y)$ 的一般公式）。跨课程连接：统计中的单因素方差分析（ANOVA）就是同一恒等式（$SS_{\text{总}} = SS_{\text{内}} + SS_{\text{间}}$）；机器学习里的偏差-方差权衡（bias-variance tradeoff）亦由此孕育——若 $Y$ 是分组、$X$ 是预测目标，$\operatorname{var}(E[X \mid Y])$ 越大说明分组信息的解释力越强。反例检验：两项均非负，故 $\operatorname{var}(X) \ge \operatorname{var}(E[X \mid Y])$——条件作用永不增加方差，只是重新分配；若 $X$ 与 $Y$ 独立，则 $E[X \mid Y] = E[X]$ 为常数、$\operatorname{var}(E[X \mid Y]) = 0$，退化为恒等式 $\operatorname{var}(X) = \operatorname{var}(X) + 0$。证明策略模板：求复杂随机变量的方差，先挑一个「条件方差易算」的 $Y$，分两步算 $E[\operatorname{var}(X \mid Y)]$ 与 $\operatorname{var}(E[X \mid Y])$ 再相加，比直接按定义展开高效得多。

> <span style="color:#7f8c8d;">§4.3, 印刷页 226（PDF p236）</span>

<!-- ===== PDF p237 ===== -->

### <span style="color:#c0392b;">§4.3 条件期望与方差再访（Conditional Expectation and Variance Revisited）</span>（续）

> <span style="color:#7f8c8d;">（本页为上一页内容的延续，页首无新节标题；印刷页码 227，属第 4 章。本页源 OCR 仅含 Example 4.16（续）、Example 4.17（续）与 Example 4.20 三块；Example 4.18（按班级平均测验分数——均值）与 Example 4.19（Forecast Revisions，见 PDF p235）均在前页，故此处例号由 4.17 直接接 4.20 属正常连续，并非缺页。）</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.16（续）**</span>

我们考虑一枚偏倚硬币（biased coin）的 $n$ 次独立投掷（independent tosses），其正面概率（probability of heads）$Y$ 在区间 $[0, 1]$ 上均匀分布（uniformly distributed）。设 $X$ 为掷出的正面次数（the number of heads obtained），则我们有 $E[X \mid Y] = nY$，且 $\operatorname{var}(X \mid Y) = nY(1 - Y)$。于是

```math
E[\operatorname{var}(X \mid Y)] = E\bigl[nY(1 - Y)\bigr] = n\bigl(E[Y] - E[Y^2]\bigr),
```

```math
= n\Bigl(E[Y] - \operatorname{var}(Y) - \bigl(E[Y]\bigr)^2\Bigr) = n\Bigl(\frac12 - \frac1{12} - \frac14\Bigr) = \frac n6.
```

> <span style="color:#7f8c8d;">[注] 原页此处 OCR 损坏，三个分数仅残留 `-21 121 41` 等碎片，且结果 `n/6` 的分数线丢失。按 $Y$ 在 $[0,1]$ 上均匀分布（$E[Y] = 1/2$，$\operatorname{var}(Y) = 1/12$，$(E[Y])^2 = 1/4$）还原，并与最终结果 $n/6$ 核对一致。</span>

此外（Furthermore），

```math
\operatorname{var}\bigl(E[X \mid Y]\bigr) = \operatorname{var}(nY) = n^2 \operatorname{var}(Y) = \frac{n^2}{12}.
```

> <span style="color:#7f8c8d;">[注] 原页 OCR 将 $n^2/12$ 识别为 `n1 2`，平方上标丢失；按 $\operatorname{var}(Y) = 1/12$ 还原。</span>

因此，由全方差法则（law of total variance），我们有

```math
\operatorname{var}(X) = E[\operatorname{var}(X \mid Y)] + \operatorname{var}\bigl(E[X \mid Y]\bigr) = \frac n6 + \frac{n^2}{12}.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.17（续）**</span>

再次考虑我们在随机选取的点处把一根长度为 $\ell$ 的木棍（stick）折断两次的问题。这里 $Y$ 是第一次折断后所剩一段的长度（the length of the piece left after the first break），$X$ 是第二次折断后所得一段的长度（the length after the second break）。我们已经算出 $X$ 的均值为 $\ell/4$。现在我们用全方差法则来计算 $\operatorname{var}(X)$。由于 $X$ 在 $0$ 与 $Y$ 之间均匀分布，我们有

```math
\operatorname{var}(X \mid Y) = \frac{Y^2}{12}.
```

于是，由于 $Y$ 在 $0$ 与 $\ell$ 之间均匀分布，我们有

```math
E[\operatorname{var}(X \mid Y)] = \frac{1}{12} E[Y^2] = \frac{1}{12} \int_0^{\ell} y^2 \cdot \frac{1}{\ell}\, dy = \frac{1}{12} \cdot \frac{\ell^2}{3} = \frac{\ell^2}{36}.
```

> <span style="color:#7f8c8d;">[注] 原页此处 OCR 损坏：长度符号被识别为 `£`、下界 `0` 被识别为 `a`、均值 `ℓ/4` 被识别为 `f.j4`、积分式 `(1/12)(1/ℓ)∫₀^ℓ y²dy` 及结果 `ℓ²/36` 呈碎片状。上述数值均按 $X \sim U(0, Y)$、$Y \sim U(0, \ell)$ 及最终结果 $7\ell^2/144$ 反推还原。</span>

我们还有 $E[X \mid Y] = Y/2$，所以

```math
\operatorname{var}\bigl(E[X \mid Y]\bigr) = \operatorname{var}\Bigl(\frac{Y}{2}\Bigr) = \frac14 \operatorname{var}(Y) = \frac14 \cdot \frac{\ell^2}{12} = \frac{\ell^2}{48}.
```

> <span style="color:#7f8c8d;">[注] 原页 OCR 将 $\ell^2/48$ 识别为 `4£ · 8`（`1/4` 与 `12`、`48` 的碎行）；$\operatorname{var}(Y) = \ell^2/12$ 由 $Y \sim U(0, \ell)$ 得出。</span>

现在利用全方差法则，我们得到

```math
\operatorname{var}(X) = E[\operatorname{var}(X \mid Y)] + \operatorname{var}\bigl(E[X \mid Y]\bigr) = \frac{\ell^2}{36} + \frac{\ell^2}{48} = \frac{7\ell^2}{144}.
```

> <span style="color:#7f8c8d;">[注] 原页 OCR 将分母 $144$ 识别为 `44`（前导 `1` 丢失），即 $7\ell^2/144$；该项由 $\ell^2/36 + \ell^2/48$ 通分核对无误。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.20：按班级平均测验分数——方差（Averaging Quiz Scores by Section - Variance）**</span>

情境与 Example 4.18 相同（The setting is the same as in Example 4.18），我们再次考虑随机变量

```math
X = \text{某学生的测验分数（quiz score of a student）},
```

```math
Y = \text{某学生所在的班级（section of a student）}, \qquad (Y \in \{1, \ldots, k\}).
```

（本页至此为止，该例的方差计算部分续至下一页。）

---



> <span style="color:#7f8c8d;">§4.3, 印刷页 227（PDF p237）</span>

<!-- ===== PDF p238 ===== -->

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">**4.3 条件期望与方差再访（Conditional Expectation and Variance Revisited）**（续）</span>

> <span style="color:#7f8c8d;">[页界] 本页为 §4.3 的延续页：页首无新节标题，承接上一页关于全方差法则（law of total variance）的讨论，页中转入一个新的示例。</span>

> <span style="color:#7f8c8d;">[OCR] 页首行残缺，仅余 "… students."（……学生）等片段，无法还原整句，以省略号占位，未作臆测补全。</span>

……（这些）学生（students）……

在方差公式（formula）中

```math
\operatorname{var}(X) = E\bigl[\operatorname{var}(X \mid Y)\bigr] + \operatorname{var}\bigl(E[X \mid Y]\bigr),
```

此处 $\operatorname{var}(X \mid Y = s)$ 是第 $s$ 个班（section）内部测验成绩（quiz score）的方差，因此 $E\bigl[\operatorname{var}(X \mid Y)\bigr]$ 就是各班方差的加权平均（weighted average），其中每个权重（weight）与该班的规模（size）成比例。

于是，全方差法则（law of total variance）表明：测验总成绩（total quiz score variance）的方差可以分解为两部分：

(a) 各班方差的平均值（average of the section variances），即 $E\bigl[\operatorname{var}(X \mid Y)\bigr]$；以及

(b) 各班均值的方差（variance of the section means），即 $\operatorname{var}\bigl(E[X \mid Y]\bigr)$。

对方差的计算，也可采用类似的方法（A similar method applies to variance calculations）。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.21**</span>

> <span style="color:#7f8c8d;">[OCR] 本页 OCR 未见该示例的起始句与标题（可能位于上一页，若然则本页为其续页）；示例正文与图注确见 "Example 4.21" 字样，故以此为编号。</span>

设 $Y$ 定义如下

```math
Y = \begin{cases} 1, & \text{若 } x < 1, \\ 2, & \text{若 } x \ge 1, \end{cases}
```

$E[X \mid Y]$ 的均值（mean）为

```math
\mu \;=\; E\bigl[E[X \mid Y]\bigr],
```

且

```math
\operatorname{var}\bigl(E[X \mid Y]\bigr) = \sum_{y} P(Y = y)\, \bigl(E[X \mid Y = y] - \mu\bigr)^{2} = \ \cdots
```

> <span style="color:#7f8c8d;">[OCR] 原页此处 OCR 严重损坏，示例中的具体数值（$E[X \mid Y]$ 的均值及 $\operatorname{var}(E[X \mid Y])$ 的逐项与结果）无法精确识别，故上式以符号与省略号占位，绝不臆造数值。据残留数字片段（如 5/4、1/4、3/4、9/16 等）推测，原文应为某一连续型随机变量 $X$ 的条件方差分解计算，但具体取值无法确认。</span>

<span style="color:#7f8c8d;">**Figure 4.13: The PDF in Example 4.21**（图 4.13：例 4.21 中的概率密度函数，PDF）</span>



<!-- ===== PDF p239 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）· 本页页眉为「Sec. 4.4 Transforms」，本书印刷页 229。页首无新节标题，先承接 §4.3 的 Example 4.21 收尾与其后的小结框，随后进入 §4.4 变换（Transforms）的开端。</span>

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">**§4.3 条件期望与方差再访（Conditional Expectation and Variance Revisited）（续）**</span>

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.21（续）**</span>

> <span style="color:#7f8c8d;">[注] 本例自上一页（PDF p238）开始。例号按连续性反查：紧随其后的 §4.4 首个例子为 Example 4.22（见 PDF p240），故本例应为 Example 4.21；p238 该处 OCR 损坏，无法直接确认例号。本页仅承接其结尾的方差计算部分。</span>

以 $Y = 1$ 或 $Y = 2$ 为条件时，$X$ 分别均匀分布（uniformly distributed）在长度为 1 或 2 的区间上。因此，

```math
\operatorname{var}(X \mid Y = 1) = \frac{1}{12},
```

且

```math
\operatorname{var}(X \mid Y = 2) = \frac{4}{12} = \frac{1}{3}.
```

于是

```math
E\bigl[\operatorname{var}(X \mid Y)\bigr] = \frac{1}{2}\cdot\frac{1}{12} + \frac{1}{2}\cdot\frac{4}{12} = \frac{5}{24}.
```

> <span style="color:#7f8c8d;">[注] 上述三式的 OCR 字形损坏，仅残留 `var(X|Y 1) = 12`、`var(X|Y 2) = 142`、`1 + -1 4 = 5/24` 等孤立片段；按 $Y$ 以等概率取 $1$、$2$，且 $X$ 在长度为 $1$、$2$ 的区间上均匀分布（方差分别为 $1/12$、$4/12$）的语境复原，未发现可辨的异值。</span>

把所有部分合在一起（putting everything together），我们得到

```math
\operatorname{var}(X) = E\bigl[\operatorname{var}(X \mid Y)\bigr] + \operatorname{var}\bigl(E[X \mid Y]\bigr) = \frac{5}{24} + \frac{9}{16} = \frac{37}{48}.
```

> <span style="color:#7f8c8d;">[注] 末项 $\operatorname{var}(E[X \mid Y]) = 9/16$ 由上一页（PDF p238）基于条件均值 $E[X \mid Y=1]=1/2$、$E[X \mid Y=2]=2$（总体均值 $5/4$）算得；本页 OCR 中该项以孤立片段 `9/16` 出现，据此复原。两项合并 $5/24 + 9/16 = 10/48 + 27/48 = 37/48$。</span>

---

<span style="color:#2471a3;">**[summary]**</span> <span style="color:#c0392b;">**本节要点总结（Properties of the Conditional Expectation and Variance，条件期望与方差的性质）**</span>

我们来总结本节的要点。

- $E[X \mid Y = y]$ 是一个数值（number），其取值依赖于 $y$。
- $E[X \mid Y]$ 是随机变量 $Y$ 的函数，因而本身也是一个随机变量（random variable）；每当 $Y$ 取值为 $y$ 时，它的取值就是 $E[X \mid Y = y]$。
- $E\bigl[E[X \mid Y]\bigr] = E[X]$（迭代期望法则，law of iterated expectations）。
- $E[X \mid Y = y]$ 可看作在给定 $Y$ 时对 $X$ 的一个估计（estimate）。相应的误差（error）$E[X \mid Y] - X$ 是一个零均值（zero mean）随机变量，且与 $E[X \mid Y]$ 不相关（uncorrelated）。
- $\operatorname{var}(X \mid Y)$ 是一个随机变量，每当 $Y$ 取值为 $y$ 时，它的取值就是 $\operatorname{var}(X \mid Y = y)$。
- $\operatorname{var}(X) = E\bigl[\operatorname{var}(X \mid Y)\bigr] + \operatorname{var}\bigl(E[X \mid Y]\bigr)$（全方差法则，law of total variance）。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）**</span>

在本节中，我们引入与一个随机变量相关联的变换（transform）。变换为我们提供了概率规律（probability law）的一种替代表示（alternative representation）。它并不特别直观（intuitive），但在某些类型的数学运算（mathematical manipulations）中往往很方便。

与随机变量 $X$ 相关联的变换（亦称为与之相关联的矩母函数，moment generating function）是标量参数（scalar parameter）$s$ 的函数 $M_X(s)$，其定义为

```math
M_X(s) = E\bigl[e^{sX}\bigr].
```

> <span style="color:#7f8c8d;">[注] 本节定义中函数名的 OCR 字形损坏，显示为 `J..lx (s)` / `Jvlx (s)` 等，按标准记号复原为 $M_X(s)$；下一页（PDF p240）正文所用的记号 $M(s)$ 可佐证该复原。</span>



> <span style="color:#7f8c8d;">§4.3 收尾与 §4.4 开端，本书印刷页 229（PDF p239）</span>

<!-- ===== PDF p240 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）· §4.4 变换（Transforms）· 本书印刷页 230 · 本页无新节标题，为上一页内容的延续（续页）</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）**</span>

只要上下文中的随机变量（random variable）$X$ 明确无疑，就可以使用更简洁的记号 $M(s)$。更详细地说，当 $X$ 是离散型随机变量（discrete random variable）时，相应的变换（transform）为

<span style="color:#2471a3;">**[definition·续]**</span> <span style="color:#00838f;">离散情形：</span>

```math
M(s) = \sum_x e^{sx} p_X(x),
```

<span style="color:#00838f;">而在连续情形下，变换为 †</span>

```math
M(s) = \int_{-\infty}^{\infty} e^{sx} f_X(x)\, dx .
```

下面我们给出几个变换的例子。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.22.**</span> 设

```math
p_X(x) = 
\begin{cases}
1/2, & \text{if } x = 2, \\
1/6, & \text{if } x = 3, \\
1/3, & \text{if } x = 5.
\end{cases}
```

相应的变换为

```math
M(s) = E[e^{sX}] = \frac{1}{2}\, e^{2s} + \frac{1}{6}\, e^{3s} + \frac{1}{3}\, e^{5s}.
```

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.23（The Transform Associated with a Poisson Random Variable，与泊松随机变量相关联的变换）。**</span> 设 $X$ 是以参数 $\lambda$ 的泊松随机变量（Poisson random variable）：

```math
p_X(x) = e^{-\lambda}\,\frac{\lambda^x}{x!}, \qquad x = 0, 1, 2, \ldots
```

相应的变换为

```math
M(s) = \sum_{x=0}^{\infty} e^{sx}\, \frac{e^{-\lambda}\, \lambda^x}{x!}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 仅显示到上述求和式，页内正文即止于此；求和式的化简步骤（通常化简为 $M(s) = e^{\lambda(e^s - 1)}$）应位于下一页，未在本页出现，此处不予臆造]</span>

> <span style="color:#7f8c8d;">† 脚注：熟悉拉普拉斯变换（Laplace transform）的读者也许能认出，与连续型随机变量相关联的变换本质上就是其 PDF 的拉普拉斯变换，唯一差别在于拉普拉斯变换通常涉及 $e^{-sx}$ 而非 $e^{sx}$。对于离散情形，有时用一个变量 $z$ 代替 $e^s$，所得的变换 $E[z^X] = \sum_x p_X(x)\, z^x$ 称为 z 变换（z-transform）。不过，本书不会用到 z 变换。</span>

> <span style="color:#7f8c8d;">[原页脚注中 z 变换的公式在 OCR 中残缺，仅保留求和下标 $x$；此处按标准 z 变换形式 $E[z^X] = \sum_x p_X(x)\, z^x$ 复原，未含臆造数值]</span>

<!-- ===== PDF p241 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）· §4.4 变换（Transforms）· 本书印刷页 231 · 本页无新节标题，为上一页内容的延续（续页）</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）**</span>

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.23（续）（The Transform Associated with a Poisson Random Variable，与泊松随机变量相关联的变换）。**</span>

我们令 $a = e^s > 0$，得到

```math
M(s) = e^{-\lambda} \sum_{x=0}^{\infty} \frac{(\lambda a)^x}{x!} = e^{-\lambda}\, e^{\lambda a} = e^{\lambda(e^s - 1)}.
```

> <span style="color:#7f8c8d;">[原页此段 OCR 碎裂（含 "We let a = e^s > 0" 及若干指数式残片），上式按泊松随机变量变换的标准化简步骤复原，未含臆造数值]</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.24（The Transform Associated with an Exponential Random Variable，与指数随机变量相关联的变换）。**</span>

设 $X$ 是参数为 $\lambda$ 的指数随机变量（exponential random variable）：

```math
f_X(x) = \lambda e^{-\lambda x}, \qquad x \ge 0.
```

> <span style="color:#7f8c8d;">[原页此处 PDF 显示行 OCR 残缺（仅余 $X$ 与指数式片段），上式按指数随机变量的标准定义复原，未含臆造数值]</span>

于是

```math
M(s) = \int_{0}^{\infty} e^{sx}\, \lambda e^{-\lambda x}\, dx = \lambda \int_{0}^{\infty} e^{-(\lambda - s)x}\, dx = \frac{\lambda}{\lambda - s}, \qquad (\text{if } s < \lambda).
```

> <span style="color:#7f8c8d;">[原页底部有一行错位残片 $e^{-(\lambda - s)x}\, dx$，属本积分中间步骤的一部分，已并入上式；OCR 亦未完整呈现分母的 $1 - s/\lambda$ 等价形式]</span>

上面的计算以及对 $M(s)$ 的公式，只有当被积函数（integrand）随 $x$ 增大而衰减（decays as $x$ increases）时才是正确的；而这当且仅当 $s < \lambda$ 时成立；否则，积分是无穷大。

需要认识到一个重要的要点：变换并不是一个数，而是参数 $s$ 的一个函数（function）。因此，我们所处理的是一种变换过程：它以某个函数（例如一个概率密度函数）为起点，最终产生一个新的函数。严格说来，$M(s)$ 只对那些使 $E[e^{sX}]$ 有限的 $s$ 值有定义，正如前一个例子中所指出的那样。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.25（The Transform Associated with a Linear Function of a Random Variable，与随机变量的线性函数相关联的变换）。**</span>

设 $M_X(s)$ 是与随机变量 $X$ 相关联的变换。考虑一个新的随机变量 $Y = aX + b$。于是我们有

```math
M_Y(s) = E[e^{sY}] = E[e^{s(aX + b)}] = e^{sb}\, E[e^{saX}] = e^{sb}\, M_X(as).
```

> <span style="color:#7f8c8d;">[原页此处的推导行在 OCR 中缺失（公式区空白），上式按正文叙述与 $Y = aX + b$ 的定义复原，未含臆造数值]</span>

例如，若 $X$ 是参数 $\lambda = 1$ 的指数随机变量，从而 $M_X(s) = 1/(1 - s)$，且若 $Y = 2X + 3$，则

```math
M_Y(s) = e^{3s}\, \frac{1}{1 - 2s}.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.26（The Transform Associated with a Normal Random Variable，与正态随机变量相关联的变换）。**</span>

设 $X$ 是均值为 $\mu$、方差为 $\sigma^2$ 的正态随机变量（normal random variable）。为了计算相应的变换，我们首先考虑标准正态（standard normal）的特殊情形——

> <span style="color:#7f8c8d;">[本页正文止于此句（"the special case of the standard …"），Example 4.26 的标准正态随机变量 $Y$（其中 $\mu = 0$、$\sigma^2 = 1$）的变换推导与一般情形的公式位于下一页，此处不作臆造]</span>

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 标准正态变换 $M_Y(s) = e^{s^2/2}$ 的推导只有一步关键技巧：指数配平方（completing the square）——把 $-y^2/2 + sy$ 改写成 $-(y - s)^2/2 + s^2/2$，被积函数随即变成「均值为 $s$、方差为 1」的正态密度乘以不依赖 $y$ 的因子 $e^{s^2/2}$，由归一化性质直接读出结果。第一性原理：为什么总能配平方？因为正态密度的对数关于 $y$ 是二次的，$e^{sy}$ 只是把二次项的顶点从 $0$ 平移到 $s$，形状与归一化常数不变——这解释了为何 $M_Y(s)$ 对一切 $s$ 有限（正态是轻尾分布，所有阶矩都存在）。跨课程连接：这是 Gaussian 积分族的核心招式，100B 实分析 / 数学物理中的 $\int_{-\infty}^{\infty} e^{-x^2}\, dx = \sqrt{\pi}$ 就是它的零参数特例；18.065 中多元高斯密度对指数配平方后，二次型系数矩阵自然涌现为协方差逆阵，与这里一脉相承。证明策略模板：凡积分指数为「二次 + 线性」的组合，一律配方成「$(y - c)^2 + \text{常数}$」，把常数因子提出、剩余积分套已知高斯积分。反例检验：对比指数分布的 $M(s) = \lambda/(\lambda - s)$ 只在 $s < \lambda$ 收敛——尾重决定收敛半径；柯西分布连一阶矩都不存在，其 $M(s)$ 处处不收敛，配平方无从谈起。

<!-- ===== PDF p242 ===== -->

> <span style="color:#7f8c8d;">§4.4 变换（Transforms）· 第 4 章 随机变量的进一步专题（Further Topics on Random Variables）· 本书印刷页 232。本页页首无新节标题或例号，为上一页 Example 4.26（正态随机变量相关联的变换）的续页；页尾进入本节新小节「由变换到矩」（From Transforms to Moments）。</span>

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.26（续）：The Transform Associated with a Normal Random Variable（与正态随机变量相关联的变换）**</span>

（接上页）我们首先考虑标准正态随机变量（standard normal random variable）$Y$ 的特殊情形，其中 $\mu = 0$ 且 $\sigma^2 = 1$，然后利用在前一个例子中导出的公式。标准正态的概率密度函数（probability density function, PDF）为

```math
f_Y(y) = \frac{1}{\sqrt{2\pi}}\, e^{-y^2/2},
```

与之相关联的变换（transform）为

```math
\begin{aligned}
M_Y(s) &= \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-y^2/2}\, e^{sy}\, dy
= \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-(y^2/2) + sy}\, dy \\[2pt]
&= e^{s^2/2} \cdot \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-(y - s)^2/2}\, dy
= e^{s^2/2},
\end{aligned}
```

其中最后一个等号成立，是因为我们运用了均值为 $s$、方差为 1 的正态 PDF 的归一化性质（normalization property）。

> <span style="color:#7f8c8d;">[OCR 说明] 上述 $M_Y(s)$ 的推导在源 OCR 中行序破碎且夹有乱码残片（如 "vz;r"、"- y2 /2" 等），此处按标准推导还原为规范 LaTeX：对指数配平方 $-y^2/2 + sy = -(y - s)^2/2 + s^2/2$，末步由正态 PDF 的归一化性质给出 $M_Y(s) = e^{s^2/2}$。</span>

均值为 $\mu$、方差为 $\sigma^2$ 的一般正态随机变量（normal random variable），可由标准正态通过线性变换（linear transformation）

```math
X = \sigma Y + \mu
```

得到。与标准正态相关联的变换为 $M_Y(s) = e^{s^2/2}$，如上所证。应用例 4.25（Example 4.25，即线性函数变换公式 $M_{aX+b}(s) = e^{bs} M_X(as)$）中的公式，我们得到

```math
M_X(s) = e^{\mu s}\, M_Y(s\sigma) = e^{(\sigma^2 s^2 / 2) + \mu s}.
```

> <span style="color:#7f8c8d;">[OCR 说明] 源 OCR 中上述 $M_X(s)$ 一行残缺（仅余 "e … M_Y(sσ) = e^(…)" 等残片），此处按例 4.25 的线性变换公式与正文叙述还原，未含臆造数值。</span>

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**由变换到矩（From Transforms to Moments）**</span>

之所以给它另起一个别名「矩生成函数」（moment generating function），原因在于：一旦有了与随机变量相关联的变换的公式，就能轻而易举地算出该随机变量的各阶矩（moments）。为看清这一点，设 $X$ 是一个连续随机变量，我们对定义式

<span style="color:#00838f;">**[定义] 矩生成函数（moment generating function）**</span>

```math
M(s) = \int_{-\infty}^{\infty} e^{sx}\, f_X(x)\, dx
```

的两端关于 $s$ 求导，便得到

```math
\begin{aligned}
\frac{d}{ds} M(s) &= \frac{d}{ds} \int_{-\infty}^{\infty} e^{sx}\, f_X(x)\, dx
= \int_{-\infty}^{\infty} \frac{d}{ds}\, e^{sx}\, f_X(x)\, dx \\[2pt]
&= \int_{-\infty}^{\infty} x\, e^{sx}\, f_X(x)\, dx.
\end{aligned}
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 「矩生成函数」这名字的由来就在这一页：$M(s)$ 在 $s = 0$ 处的 $n$ 阶导数恰为第 $n$ 阶矩 $E[X^n]$。第一性原理：把 $e^{sX}$ 在 $s = 0$ 附近作泰勒展开 $e^{sX} = 1 + sX + \frac{s^2 X^2}{2!} + \cdots$，两边取期望得到 $M(s) = 1 + sE[X] + \frac{s^2}{2!} E[X^2] + \cdots$——各阶矩恰好出现在泰勒系数的分子上，于是「对 $s$ 求导再令 $s = 0$」就是从泰勒系数里把矩拎出来；变换相当于把所有矩打包进一个函数。跨课程连接：这是幂级数 / 母函数思想的概率版——6.042J 的普通母函数 $G(z) = E[z^X]$ 与 $M(s) = E[e^{sX}]$ 只差代换 $z = e^s$（本页脚注的 z 变换正是如此）；「矩决定分布」的反演主题对应 100B 实分析中「由矩序列（moment sequence）唯一决定测度」的经典问题。证明策略模板：若 $E[X^n]$ 直接积分难算，先求出变换 $M(s)$（通常只需一个已知求和 / 积分），再对 $s$ 求 $n$ 次导、令 $s = 0$——Example 4.27 与指数分布 $E[X] = 1/\lambda$、$E[X^2] = 2/\lambda^2$ 都是这么来的。反例检验：微分与积分次序的交换要求 $M(s)$ 在 $0$ 附近有限，等价于各阶矩存在；对柯西等重尾分布矩不存在，$M(s)$ 也不收敛，此方法整体失效。

<!-- ===== PDF p243 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）· §4.4 变换（Transforms）· 本书印刷页 233 · 本页无新节标题，为上一页内容的延续（续页）</span>

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）—— 用变换求矩（moments）**</span>

<span style="color:#00838f;">**[矩生成性质]** 变换在 $s = 0$ 处的导数给出随机变量相应的矩（moments）。</span>

这一等式对所有 $s$ 的取值都成立。† 考虑 $s = 0$ 这一特殊情形，便得到

```math
\left.\frac{dM(s)}{ds}\right|_{s=0} = \int_{-\infty}^{\infty} x\, f_X(x)\, dx = E[X].
```

更一般地，若把函数 $M(s)$ 关于 $s$ 求导 $n$ 次，类似的推导给出

```math
\left.\frac{d^n M(s)}{ds^n}\right|_{s=0} = \int_{-\infty}^{\infty} x^n\, f_X(x)\, dx = E[X^n].
```

> <span style="color:#7f8c8d;">[原页 OCR 说明：上述两式中的导数记号（$\frac{dM(s)}{ds}\big|_{s=0}$、$\frac{d^nM(s)}{ds^n}\big|_{s=0}$）及积分号等符号在 OCR 中残缺（如 ":. M (') I , �o = ..."、"::n M (s) ,�o = ..."），均按上下文与标准公式恢复；仅涉及符号与记号、不含具体数值，未臆造任何数字。]</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.27.**</span> 我们早先（Example 4.22）已经看到，概率质量函数（PMF, probability mass function）

```math
p_X(x) =
\begin{cases}
1/2, & \text{if } x = 2, \\
1/6, & \text{if } x = 3, \\
1/3, & \text{if } x = 5.
\end{cases}
```

与变换

```math
M(s) = \frac{1}{2}\, e^{2s} + \frac{1}{6}\, e^{3s} + \frac{1}{3}\, e^{5s}
```

相关联。于是，

```math
\left.\frac{dM(s)}{ds}\right|_{s=0} = \left.\Bigl( \frac{1}{2}\cdot 2\, e^{2s} + \frac{1}{6}\cdot 3\, e^{3s} + \frac{1}{3}\cdot 5\, e^{5s} \Bigr)\right|_{s=0} = \frac{1}{2}\cdot 2 + \frac{1}{6}\cdot 3 + \frac{1}{3}\cdot 5 = \frac{19}{6}.
```

并且

```math
E[X^2] = \left.\frac{d^2 M(s)}{ds^2}\right|_{s=0} = \left.\Bigl( \frac{1}{2}\cdot 4\, e^{2s} + \frac{1}{6}\cdot 9\, e^{3s} + \frac{1}{3}\cdot 25\, e^{5s} \Bigr)\right|_{s=0} = \frac{1}{2}\cdot 4 + \frac{1}{6}\cdot 9 + \frac{1}{3}\cdot 25 = \frac{71}{6}.
```

> <span style="color:#7f8c8d;">[原页 OCR 说明：例 4.27 推导中的系数与中间结果在 OCR 中零散错位（如 "21"、"= 2 4 + 6 . 9 + 3 . 25" 等），已按上下文逐一核对恢复：$E[X] = \frac{1}{2}\cdot 2 + \frac{1}{6}\cdot 3 + \frac{1}{3}\cdot 5 = \frac{19}{6}$、$E[X^2] = \frac{1}{2}\cdot 4 + \frac{1}{6}\cdot 9 + \frac{1}{3}\cdot 25 = \frac{71}{6}$，数字均经运算验证，未臆造。]</span>

---

> <span style="color:#7f8c8d;">† 脚注（footnote）：这一推导涉及微分与积分次序的交换（an interchange of differentiation and integration）。在本书将要考虑的所有应用场合中，这种交换都被证明是合理的。此外，这一推导对于一般的随机变量（包括离散型随机变量）仍然成立。事实上，它可以更抽象地（more abstractly）进行，其形式为</span>

```math
\frac{d}{ds} M(s) = \frac{d}{ds}\, E[e^{sX}] = E\Bigl[ \frac{d}{ds}\, e^{sX} \Bigr] = E\bigl[ X\, e^{sX} \bigr],
```

> <span style="color:#7f8c8d;">从而得到相同的结论（leading to the same conclusion）。[原页脚注中该公式在 OCR 中完全缺失（"in the form" 之后直接跳到 "leading to the same conclusion"），此处按书中「微分与期望次序交换」的标准形式恢复，未含臆造数值。]</span>



<!-- ===== PDF p244 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）· §4.4 变换（Transforms）· 本书印刷页 234 · 本页无新节标题，为上一页内容的延续（续页）</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）**</span>

> <span style="color:#7f8c8d;">[本页承接上一页「From Transforms to Moments（从变换到矩）」一节的论述：先以指数随机变量（exponential random variable）为例，演示如何借助变换的导数求矩——此段为正文叙述（未编号的例证），并非独立编号例子；随后给出变换的两个通用性质，并进入新的小节「Inversion of Transforms（变换的反演）」及其反演性质（Inversion Property）。]</span>

以一个指数随机变量（exponential random variable）为例：设其 PDF 为

```math
f_X(x) = \lambda e^{-\lambda x}, \qquad x \ge 0,
```

我们此前（Example 4.24）已经求出，与之关联的变换（transform）为

```math
M_X(s) = \frac{\lambda}{\lambda - s}.
```

> <span style="color:#7f8c8d;">[原页 OCR 此处仅残留「$x \ge 0$」片段，$f_X(x) = \lambda e^{-\lambda x}$ 一行被 OCR 损坏；PDF 语句按第 3 章指数随机变量的标准定义复原，变换式则与 Example 4.24 的结果一致，未含臆造数值]</span>

于是（Thus）

```math
M'_X(s) = \frac{d}{ds}\left[ \frac{\lambda}{\lambda - s} \right] = \frac{\lambda}{(\lambda - s)^2},
```

以及

```math
M''_X(s) = \frac{d^2}{ds^2}\left[ \frac{\lambda}{\lambda - s} \right] = \frac{2\lambda}{(\lambda - s)^3}.
```

> <span style="color:#7f8c8d;">[原页此处的两条导数公式在 OCR 中严重碎裂（行列错乱、字母与分数被拆散到多行）；此处按 $M_X(s) = \lambda/(\lambda - s)$ 的标准求导结果还原：一阶导 $\lambda/(\lambda - s)^2$、二阶导 $2\lambda/(\lambda - s)^3$，未含臆造数值]</span>

令 $s = 0$（By setting $s = 0$），我们得到（we obtain）

```math
E[X] = \frac{1}{\lambda}, \qquad E[X^2] = \frac{2}{\lambda^2},
```

这与第 3 章推导出的公式一致（which agrees with the formulas derived in Chapter 3）。

我们以变换的两个更有用、更一般化的性质（two more useful and generic properties）来结束本节。对任意随机变量 $X$，我们有

```math
M_X(0) = E\bigl[e^{0X}\bigr] = E[1] = 1,
```

并且若 $X$ 只取非负整数值（nonnegative integer values），则

```math
\lim_{s \to -\infty} M_X(s) = P(X = 0)
```

（参见章末习题）（see the end-of-chapter problems）。

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**Inversion of Transforms（变换的反演）**</span>

变换 $M_X(s)$ 的一个非常重要的性质是：它可以被反演（inverted），也就是说，它可以用来确定随机变量 $X$ 的概率律（probability law）。这需要一些适当的数学条件（appropriate mathematical conditions），而这些条件在我们所有用到反演性质的例子中均得到满足。下面是一个更精确的陈述，其证明超出了本书的范围（beyond our scope）。

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**[定义] Inversion Property（反演性质）**</span>

与随机变量 $X$ 相关联的变换 $M_X(s)$ 唯一地确定了 $X$ 的 CDF，假定 $M_X(s)$ 在某个区间 $[-a,\, a]$ 内的所有 $s$ 上都是有限的，其中 $a$ 是一个正数（positive number）。

存在一些显式公式（explicit formulas），使我们能够从与随机变量相关联的变换出发，恢复其 PMF 或 PDF，但这些公式相当难以使用。在实践中，变换通常是通过「模式匹配」（pattern matching）来反演的——

> <span style="color:#7f8c8d;">[本页正文止于此（句子未完成，下一页 p245 续接：based on tables of known distribution-transform pairs, "We will see a number of such examples shortly"——即基于已知「分布—变换」对的表格进行匹配，随后立即给出若干这样的例子）]</span>



> <span style="color:#7f8c8d;">§4.4, 印刷页 234（PDF p244）</span>

<!-- ===== PDF p245 ===== -->

> <span style="color:#7f8c8d;">页眉（running header）：Sec. 4.4 · 235 · Transforms（§4.4 变换）。本页页首无新节标题，是上一页（p244）内容的延续（续页），承接 p244 末尾「变换的反演（Inversion of Transforms）」中关于「模式匹配」反演的论述，并以 Example 4.28 与 Example 4.29 两个例子演示如何通过模式匹配/级数展开反演变换。本书印刷页码为 235。</span>

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）——通过模式匹配反演变换**</span>

承接上一页的论述：在实践中，变换通常通过「模式匹配」（pattern matching）来反演（inverted），即基于已知分布—变换对（distribution-transform pairs）的表格（tables）进行匹配。我们很快就会看到若干这样的例子（we will see a number of such examples shortly）。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.28（通过检验变换反演离散分布）。**</span>

> <span style="color:#7f8c8d;">[注] 原书该例子未给出显式标题，此处中文括注系对内容主旨的概括。</span>

已知与随机变量 $X$ 相关联的变换（transform）为

```math
M(s) = \frac{1}{2}\, e^{-s} + \frac{1}{8} + \frac{1}{8}\, e^{4s} + \frac{1}{4}\, e^{5s}.
```

> <span style="color:#7f8c8d;">[ocr] 上式在原始 OCR 中严重散行（各分数系数 $1/2$、$1/8$、$1/8$、$1/4$ 及指数 $-s$、$4s$、$5s$ 被拆散到多行，仅残留分子 "1" 与分母 "2、8、8、4" 的零散片段）。按后文「每个取值 $x$ 的概率恰为对应 $e^{sx}$ 项的系数」的说明还原：常数项 $1/8$ 即 $e^{0s}$ 的系数，四项系数之和为 $1$，未含臆造数值。</span>

由于 $M(s)$ 是形如 $e^{sx}$ 的各项之和，我们可以将其与一般公式（general formula）

```math
M(s) = \sum_x e^{sx}\, p_X(x)
```

> <span style="color:#7f8c8d;">[ocr] 上式（离散情形下变换的一般公式）在原始 OCR 中仅残留下标 "x" 一个字符；此处按本书 §4.4 开头给出的离散情形变换定义 $M(s) = \sum_x e^{sx}\, p_X(x)$ 补全，未含臆造内容。</span>

进行比较，从而推断出 $X$ 是一个离散随机变量（discrete random variable）。$X$ 所能取的不同值可以直接从相应的指数（exponent）中读出，分别为 $-1$、$0$、$4$ 和 $5$。每个取值 $x$ 的概率由乘在对应 $e^{sx}$ 项上的系数（coefficient）给出。在我们的情形中，

```math
P(X = -1) = \frac{1}{2}, \qquad P(X = 0) = \frac{1}{8}, \qquad P(X = 4) = \frac{1}{8}, \qquad P(X = 5) = \frac{1}{4}.
```

> <span style="color:#7f8c8d;">[ocr] 上式中的概率数值在原始 OCR 中碎裂严重（分子、分母被拆散到多行，仅残留 "-1"、"8"、"4"、"2" 等残缺片段，且各行间顺序存在歧义）。按正文说明——每个取值的概率恰为对应 $e^{sx}$ 项的系数——取与变换各项系数 $1/2, 1/8, 1/8, 1/4$ 逐一对应的一组值：$P(X=-1)=\frac{1}{2}$、$P(X=0)=\frac{1}{8}$、$P(X=4)=\frac{1}{8}$、$P(X=5)=\frac{1}{4}$，四项之和为 $1$，相互印证，非臆造数值。</span>

从上一个例子推广开来（generalizing from the last example），有限取值（finite-valued）的离散随机变量的分布总能通过检验相应的变换（by inspection of the corresponding transform）求得。同一方法对取值范围无限（infinite range）的离散随机变量同样适用，如下面的例子所示。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.29（The Transform Associated with a Geometric Random Variable，与几何随机变量相关联的变换）。**</span>

已知与随机变量 $X$ 相关联的变换具有如下形式：

```math
M(s) = \frac{p\, e^{s}}{1 - (1 - p)\, e^{s}},
```

其中 $p$ 是满足 $0 < p \le 1$ 的常数。我们希望求出 $X$ 的分布。我们回忆几何级数（geometric series）的公式：

```math
\frac{1}{1 - a} = 1 + a + a^2 + \cdots,
```

该式在 $|a| < 1$ 时成立（which is valid whenever $|a| < 1$）。我们以 $a = (1 - p)\, e^{s}$ 代入该公式，并取 $s$ 足够接近零，使得 $(1 - p)\, e^{s} < 1$。我们得到

```math
M(s) = p\, e^{s} \left[ 1 + (1 - p)\, e^{s} + (1 - p)^2\, e^{2s} + \cdots \right]
     = \sum_{k=1}^{\infty} p\, (1 - p)^{k-1}\, e^{ks}.
```

> <span style="color:#7f8c8d;">[ocr] 原页在 "We obtain"（我们得到）之后的展开式缺失（该处为空白，无 OCR 内容）。此处按几何级数展开还原：$M(s) = p\, e^{s} \sum_{k=0}^{\infty} \bigl( (1-p)\, e^{s} \bigr)^{k} = \sum_{k=1}^{\infty} p\, (1-p)^{k-1}\, e^{ks}$，且与后文「读取 $e^{ks}$ 的系数得 $P(X=k)=p(1-p)^{k-1}$」的结论一致，未含臆造数值。</span>

与上一个例子一样，我们推断这是一个离散随机变量，它取正整数（positive integer）值。概率 $P(X = k)$ 通过读取项 $e^{ks}$ 的系数求得。特别地，$P(X = 1) = p$，$P(X = 2) = p\,(1 - p)$，并且

```math
P(X = k) = p\, (1 - p)^{k-1}, \qquad k = 1, 2, \ldots
```

我们认出这正是参数为 $p$ 的几何分布（geometric distribution）。

---

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> Example 4.29 演示了变换反演的看家本领：模式匹配 + 级数展开。给定 $M(s) = \frac{pe^s}{1 - (1-p)e^s}$，把分母按几何级数 $\frac{1}{1-a} = \sum_{k=0}^{\infty} a^k$ 展开，得 $M(s) = \sum_{k=1}^{\infty} p(1-p)^{k-1} e^{ks}$——再对照离散情形的一般公式 $M(s) = \sum_x e^{sx} p_X(x)$，读出 $e^{ks}$ 的系数即得 $P(X = k) = p(1-p)^{k-1}$，正是几何分布。第一性原理：离散分布的变换是 $e^{sx}$ 的线性组合且系数就是概率，所以「反演 = 把 $M(s)$ 展成 $e^{sx}$ 的级数并读系数」——这跟 6.042J 中「用母函数数数」的语汇完全一致。跨课程连接：CLRS 分析哈希表与跳表、6.006 随机算法都反复用到几何分布的矩；令 $z = e^s$，$M(s)$ 就是 6.042J 的普通母函数 $E[z^X]$，收敛域 $|z| < 1$ 换回 $s$ 即 $s < 0$。证明策略模板：凡「由变换反求分布」——(1) 把 $M(s)$ 化成已知函数的组合；(2) 展开成 $e^{sx}$ 的级数或对照已知分布表；(3) 逐项读系数。反例检验：级数展开必须满足收敛条件，几何级数要求 $|a| < 1$，故 $s$ 须取在 $0$ 附近使 $(1-p)e^s < 1$；形式上照样能展开出系数，但收敛半径正是变换合法定义域的边界，不可忽略。

> <span style="color:#7f8c8d;">§4.4, 印刷页 235（PDF p245）</span>

<!-- ===== PDF p246 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）· §4.4 变换（Transforms）· 印刷页 236。本页页首无新节标题，为上一页（p245）内容的延续：先收尾 Example 4.29（几何分布变换）的导数验证，随后进入 Example 4.30（两种分布的混合）。下一例为 p247 的 Example 4.31。</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）**</span>

---

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#2471a3;">**Example 4.29（续）：与几何随机变量相关联的变换——导数验证**</span>

注意（Note that），将几何分布的变换

```math
M_X(s) = \frac{p\, e^{s}}{1 - (1-p)\, e^{s}},
```

关于 $s$ 求导，可得

```math
\frac{d}{ds} M_X(s) = \frac{p e^s \bigl(1 - (1-p)e^s\bigr) + (1-p)\, p\, e^{2s}}{\bigl(1 - (1-p)\, e^s\bigr)^2}.
```

> <span style="color:#7f8c8d;">[OCR 注释] 原页此处求导公式在 OCR 中严重残缺（分子仅残留 $p e^s$、$+(1-p)p e^{2s}$ 以及因子 $1-(1-p)e^s$ 的碎片，分母 $\bigl(1-(1-p)e^s\bigr)^2$ 尚可辨认）；此处按商法则（quotient rule）的未化简结果恢复，且在 $s = 0$ 处取值恰为 $1/p$，与正文所述一致，未臆造数值。</span>

当 $s = 0$ 时，右端等于 $1/p$，这与第 2 章推导出的 $E[X]$ 公式一致（agrees with the formula for $E[X]$ derived in Chapter 2）。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.30：与两种分布的混合相关联的变换（The Transform Associated with a Mixture of Two Distributions）**</span>

邻里银行（neighborhood bank）有三名柜员（teller），其中两名较快、一名较慢。在快柜员处，协助一位顾客所需的时间服从参数（parameter）$\lambda = 6$ 的指数分布（exponentially distributed）；在慢柜员处，则服从参数 $\lambda = 4$ 的指数分布。Jane 走进银行并随机选择一名柜员，选中每一人的概率均为 $1/3$。求协助 Jane 所需时间的概率密度函数，以及与之关联的变换（associated transform）。

> <span style="color:#7f8c8d;">[OCR 注释] 问题陈述中两个参数的具体数值在原页 OCR 中残缺（仅残留 "parameter … =" 字样即断裂）；此处据下文变换计算式 $6/(6-s)$、$4/(4-s)$ 以及故事设定（2 快 1 慢 → 权重 $2/3$、$1/3$）反推为快柜员 $\lambda = 6$、慢柜员 $\lambda = 4$，与后续推导自洽，未臆造数值。</span>

我们有（We have）

```math
f_Y(y) = \frac{2}{3}\cdot 6 e^{-6y} + \frac{1}{3}\cdot 4 e^{-4y}, \qquad y \ge 0.
```

于是（Then），

```math
M_Y(s) = \int_0^{\infty} e^{sx}\left(\frac{2}{3}\cdot 6 e^{-6x} + \frac{1}{3}\cdot 4 e^{-4x}\right) dx
```

```math
= \frac{2}{3}\int_0^{\infty} e^{sx}\, 6 e^{-6x}\, dx + \frac{1}{3}\int_0^{\infty} e^{sx}\, 4 e^{-4x}\, dx
```

```math
= \frac{2}{3}\cdot \frac{6}{6-s} + \frac{1}{3}\cdot \frac{4}{4-s}, \qquad (\text{for } s < 4).
```

> <span style="color:#7f8c8d;">[OCR 注释] 原页此处三个显示公式在 OCR 中被大量打散（积分上下限、权重 $2/3$ 与 $1/3$、分母 $6-s$ 与 $4-s$ 散落于多行）；上式为按指数分布变换的标准结果 $\int_0^\infty e^{sx}\lambda e^{-\lambda x}\, dx = \lambda/(\lambda - s)$（$s < \lambda$）复原的完整推导，未臆造数值。</span>

<span style="color:#00838f;">**[定义式] 混合分布的一般形式（mixture of distributions，general form）：**</span>

更一般地（More generally），设 $X_1, \dots, X_n$ 为 PDF 分别为 $f_{X_1}, \dots, f_{X_n}$ 的连续型随机变量（continuous random variables）。随机变量 $Y$ 的取值 $y$ 按如下方式产生：以相应的概率 $p_i$ 选取某个下标（index）$i$，并把 $y$ 取为等于 $X_i$ 的取值。于是，

```math
f_Y(y) = p_1 f_{X_1}(y) + \cdots + p_n f_{X_n}(y),
```

并且

```math
M_Y(s) = p_1 M_{X_1}(s) + \cdots + p_n M_{X_n}(s).
```

本例中的各步骤可以反过来进行（The steps in this problem can be reversed）。例如，我们可能已知与随机变量 $Y$ 相关联的变换具有如下形式：

```math
M_Y(s) = \frac{1}{2}\cdot \frac{1}{2-s} + \frac{3}{4}\cdot \frac{1}{1-s}.
```

> <span style="color:#7f8c8d;">[OCR 注释] 原页此处给定形式的变换在 OCR 中错乱（残留「1 1 +3 1 / 2 2-s 4 l-s」等碎片）；此处按后文「重写为 $\frac{1}{4}\cdot\frac{2}{2-s} + \frac{3}{4}\cdot\frac{1}{1-s}$」以及「参数 2 与 1、选中概率 $1/4$ 与 $3/4$」的结论复原，未臆造数值。</span>

我们可以将其改写为

```math
M_Y(s) = \frac{1}{4}\cdot \frac{2}{2-s} + \frac{3}{4}\cdot \frac{1}{1-s},
```

并识别出（recognize that）$Y$ 是两个指数随机变量（exponential random variables）的混合（mixture），其参数分别为 2 与 1，二者被选中的概率分别为 $1/4$ 与 $3/4$。

---

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 混合分布（mixture）描述「两步抽样」：先以概率 $p_i$ 选一个成分 $i$，再按该成分的分布产生观测，$\sum_i p_i = 1$ 保证 $f_Y$ 仍积分为 1。第一性原理：这是「分层全概率公式」在密度层面的版本——引入隐变量 $I$（选中哪个成分），$f_Y(y) = \sum_i f_{Y \mid I=i}(y)\, P(I = i)$；期望对混合是线性的，所以变换随之线性 $M_Y(s) = \sum_i p_i M_{X_i}(s)$，故「先混合再求变换」与「先求各成分变换再加权」等价。跨课程连接：这就是机器学习中高斯混合模型（GMM）、聚类与 EM 算法的数学骨架——EM 的 E 步为每个观测计算「它属于各成分的后验概率」，M 步再更新成分参数；贝叶斯分层模型「先验选参数、参数定分布」与这里的结构同构。反例检验：混合不是卷积——混合是「按概率二选一」，卷积是「两变量相加」（$Z = X + Y$ 对应变换相乘）；一个对应变换的加权和、一个对应乘积，务必区分。证明策略模板：凡出现「以某概率取某分布」，直接写密度 / 变换为加权和再逐项套已知公式（如银行例 $\frac{2}{3}\cdot\frac{6}{6-s} + \frac{1}{3}\cdot\frac{4}{4-s}$）；反方向即把给定变换拆成已知项的和，读出混合权重与各成分参数（Example 4.30 后半）。

> <span style="color:#7f8c8d;">§4.4, 印刷页 236（PDF p246）</span>

<!-- ===== PDF p247 ===== -->

> <span style="color:#7f8c8d;">Sec. 4.4 · Transforms（变换，transform）—— 印页 p.237；本页为 §4.4 续页，新起子节「Sums of Independent Random Variables（独立随机变量之和）」。</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）**</span>

### <span style="color:#c0392b;">独立随机变量之和（Sums of Independent Random Variables）</span>

在处理随机变量之和（sum of random variables）时，变换方法（transform methods）尤为方便。原因在于，独立随机变量的相加（addition of independent random variables）对应着变换的相乘（multiplication of transforms），下面我们将予以证明。这一性质提供了卷积公式（convolution formula）之外一种通常更为便捷的替代途径。

设 $X$ 与 $Y$ 是独立随机变量，并设 $Z = X + Y$。按定义，与 $Z$ 相关联的变换为

```math
M_Z(s) = E[e^{sZ}] = E[e^{s(X+Y)}] = E[e^{sX} e^{sY}].
```

由于 $X$ 与 $Y$ 独立，对任意固定的 $s$，$e^{sX}$ 与 $e^{sY}$ 都是独立随机变量。因此，它们乘积的期望等于各自期望的乘积，于是

```math
M_Z(s) = E[e^{sX}]\, E[e^{sY}] = M_X(s)\, M_Y(s).
```

由同样的论证，若 $X_1, \ldots, X_n$ 是一组独立随机变量，且 $Z = X_1 + \cdots + X_n$，则

```math
M_Z(s) = M_{X_1}(s) \cdots M_{X_n}(s).
```

> <span style="color:#7f8c8d;">[原页此处「$n$ 个独立随机变量之和」对应的显示公式在 OCR 中缺失，上式为按「加法对应乘法」的论证复原的规范结果，非原页逐字文本。]</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.31（The Transform Associated with the Binomial，与二项分布相关的变换）**</span>

设 $X_1, \ldots, X_n$ 是参数同为 $p$ 的独立伯努利随机变量（independent Bernoulli random variables）。则对所有 $i$，有

```math
M_{X_i}(s) = 1 - p + p e^s.
```

随机变量 $Z = X_1 + \cdots + X_n$ 服从参数为 $n$ 与 $p$ 的二项分布（binomial），其相应的变换为

```math
M_Z(s) = (1 - p + p e^s)^n.
```

> <span style="color:#7f8c8d;">[原页此处例 4.31 的两个显示公式在 OCR 中缺失，上两式由上下文及二项分布的标准变换结果复原。]</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.32（The Sum of Independent Poisson Random Variables is Poisson，独立泊松随机变量之和仍为泊松）**</span>

设 $X$ 与 $Y$ 是独立的泊松随机变量（Poisson random variables），均值分别为 $\lambda$ 与 $\mu$，并设 $Z = X + Y$。则

```math
M_X(s) = e^{\lambda(e^s - 1)},
```

以及

```math
M_Y(s) = e^{\mu(e^s - 1)}.
```

> <span style="color:#7f8c8d;">[原页此处 $M_Y(s)$ 的显示公式在 OCR 中缺失，上式为按泊松变换的标准结果复原。]</span>

因此，与 $Z$ 相关联的变换与均值为 $\lambda + \mu$ 的泊松随机变量的变换相同。由变换的唯一性（uniqueness property of transforms），$Z$ 是均值为 $\lambda + \mu$ 的泊松随机变量。

<!-- ===== PDF p248 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**§4.4 变换（Transforms）（续）**</span>

> <span style="color:#7f8c8d;">第 4 章 随机变量的进一步专题（Further Topics on Random Variables）· 原书页码 p.238 · 本页为上一页 §4.4 内容的延续（页首无新节/新标题）：先给出 Example 4.33（承 Example 4.32），随后进入「变换及其性质小结（Summary of Transforms and their Properties）」框。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 4.33：独立正态随机变量之和仍为正态（The Sum of Independent Normal Random Variables is Normal）**</span>

设 $X$ 与 $Y$ 是相互独立的正态随机变量（independent normal random variables），均值（mean）分别为 $\mu_X$、$\mu_Y$，方差（variance）分别为 $\sigma_X^2$、$\sigma_Y^2$，并设 $Z = X + Y$。于是，

```math
M_X(s) = \exp\left\{\frac{\sigma_X^2 s^2}{2} + \mu_X s\right\},\qquad
M_Y(s) = \exp\left\{\frac{\sigma_Y^2 s^2}{2} + \mu_Y s\right\},
```

以及

```math
M_Z(s) = M_X(s)\, M_Y(s) = \exp\left\{\frac{(\sigma_X^2 + \sigma_Y^2)\, s^2}{2} + (\mu_X + \mu_Y)\, s\right\}.
```

> <span style="color:#7f8c8d;">[OCR 注] 原页中上述变换公式在 OCR 中被拆散、乱码：均值 $\mu$ 与方差 $\sigma^2$ 被误读为 J.lx、J.lY、a;、a�，分数 $\tfrac{1}{2}$ 亦被吞掉（残存「T」等字符），且 $M_Z(s)$ 一式几乎整行缺失。此处按正态分布变换的标准结果复原，并与下文「$Z$ 的变换与均值 $\mu_X+\mu_Y$、方差 $\sigma_X^2+\sigma_Y^2$ 的正态随机变量相同」相互印证，未改动任何数值。</span>

我们观察到，与 $Z$ 相关联的变换（transform）恰好与均值 $\mu_X + \mu_Y$、方差 $\sigma_X^2 + \sigma_Y^2$ 的正态随机变量所关联的变换相同。由变换的唯一性（uniqueness property of transforms），$Z$ 服从具有这些参数（parameters）的正态分布，从而为第 4.1 节（Section 4.1）中基于卷积公式（convolution formula）的推导提供了另一种途径（alternative）。

---

<span style="color:#2471a3;">**[summary]**</span> <span style="color:#00838f;">**Summary of Transforms and their Properties（变换及其性质的总结）**</span>

与随机变量 $X$ 相关联的变换（transform）定义为

```math
M_X(s) = E\bigl[e^{sX}\bigr] =
\begin{cases}
\displaystyle \sum_x e^{sx}\, p_X(x), & X \text{ 为离散型},\\[4pt]
\displaystyle \int_{-\infty}^{\infty} e^{sx}\, f_X(x)\, dx, & X \text{ 为连续型}.
\end{cases}
```

一个随机变量的分布（distribution）由其对应的变换完全确定（completely determined）。

**矩生成性质（moment generating properties）：**

```math
M_X(0) = 1, \qquad \left.\frac{d}{ds}\, M_X(s)\right|_{s=0} = E[X].
```

若 $Y = aX + b$，则 $M_Y(s) = e^{sb}\, M_X(as)$。

若 $X$ 与 $Y$ 相互独立，则 $M_{X+Y}(s) = M_X(s)\, M_Y(s)$。

> <span style="color:#7f8c8d;">[OCR 注] 原页小结框底部还残存一个孤立的项目符号「•」与「=」，其后续内容在 OCR 中缺失、无法辨认（疑为矩生成性质的某条残余条目），此处不臆造其表述。</span>

---

我们已经得到了与少数几个常见随机变量（common random variables）相关联的变换公式。对于许多其他分布（distribution），我们只需进行中等程度的代数运算（a moderate amount of algebra）即可推导出这类公式（均匀分布（uniform distribution）的情形见章末习题（end-of-chapter problems））。下面我们把其中最常用的一些汇总在下述表格（tables）中。

> <span style="color:#7f8c8d;">随后的变换汇总表（tables）位于下一页 p249，不属本页范围。</span>



<!-- ===== PDF p249 ===== -->

> <span style="color:#7f8c8d;">本页为 §4.4 变换（Transforms）正文内的小结表（印页 239），收录常见离散型与连续型随机变量的概率函数及其变换（transform），为上一页 §4.4 内容的延续。</span>

<span style="color:#c0392b;">**常见离散型随机变量的变换（Transforms for Common Discrete Random Variables）**</span>

<span style="color:#2471a3;">**[table·表]**</span> <span style="color:#7f8c8d;">表中 $p_X(k)$ 为概率质量函数（PMF, probability mass function），$M_X(s)$ 为随机变量 $X$ 的变换（Transform，即矩生成函数，moment generating function）。</span>

| 分布（Distribution） | 概率质量函数（PMF）$p_X(k)$ | 变换（Transform）$M_X(s)$ |
|---|---|---|
| Bernoulli($p$)（$k = 0, 1$） | $p_X(k) = p$（若 $k = 1$）；$p_X(k) = 1 - p$（若 $k = 0$） | $1 - p + pe^s$ |
| Binomial($n, p$)（$k = 0, 1, \dots, n$） | $p_X(k) = \binom{n}{k}\, p^k (1 - p)^{n-k}$ | $(1 - p + pe^s)^n$ |
| Geometric($p$)（$k = 1, 2, \dots$） | $p_X(k) = (1 - p)^{k-1}\, p$ | $\dfrac{pe^s}{1 - (1 - p)\, e^s}$ |
| Poisson($\lambda$)（$k = 0, 1, \dots$） | $p_X(k) = \dfrac{e^{-\lambda}\,\lambda^k}{k!}$ | $e^{\lambda(e^s - 1)}$ |
| Uniform($a, b$)（$k = a, a + 1, \dots, b$） | $p_X(k) = \dfrac{1}{b - a + 1}$ | $\dfrac{e^{sa}\left(e^{s(b-a+1)} - 1\right)}{(b - a + 1)(e^s - 1)}$ |

<span style="color:#c0392b;">**常见连续型随机变量的变换（Transforms for Common Continuous Random Variables）**</span>

<span style="color:#2471a3;">**[table·表]**</span> <span style="color:#7f8c8d;">表中 $f_X(x)$ 为概率密度函数（PDF, probability density function），$M_X(s)$ 为随机变量 $X$ 的变换。</span>

| 分布（Distribution） | 概率密度函数（PDF）$f_X(x)$ | 变换（Transform）$M_X(s)$ |
|---|---|---|
| Uniform($a, b$)（$a \le x \le b$） | $f_X(x) = \dfrac{1}{b - a}$ | $\dfrac{e^{sb} - e^{sa}}{s\,(b - a)}$ |
| Exponential($\lambda$)（$x \ge 0$） | $f_X(x) = \lambda e^{-\lambda x}$ | $\dfrac{\lambda}{\lambda - s}$，$s < \lambda$ |
| Normal($\mu, \sigma^2$)（$-\infty < x < \infty$） | $f_X(x) = \dfrac{1}{\sqrt{2\pi}\,\sigma}\, e^{-(x - \mu)^2 / (2\sigma^2)}$ | $e^{\mu s + \sigma^2 s^2 / 2}$ |

> <span style="color:#7f8c8d;">[ocr] OCR 注释：本页为表页，源 OCR 按栏位碎裂排版，各行公式依教材标准表式整理为规范 LaTeX。其中 Exponential 行变换后的收敛条件在原 OCR 中呈「(B < A)」，系符号误识，对照原文应为「$s < \lambda$」（$s$ 被误识为 B、$\lambda$ 被误识为 A）。Binomial 行的二项系数 $\binom{n}{k}$、Geometric 行与 Poisson 行的变换公式、连续型 Uniform 行的变换，以及 Normal 行的概率密度与变换（$e^{\mu s + \sigma^2 s^2 / 2}$），在源 OCR 中均碎裂或缺失，此处按教材标准表式补全，未改动任何数值。</span>



<!-- ===== PDF p250 ===== -->

> <span style="color:#7f8c8d;">第 4 章　随机变量的进一步专题（Further Topics on Random Variables）——书内印刷页码 240（PDF p250，第 4 章末页）。本页收尾 §4.4「变换（Transforms）」并起 §4.5「独立随机变量随机个数之和」。</span>

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">联合分布所对应的变换（Transforms Associated with Joint Distributions）</span>（§4.4 变换（Transforms）末尾的未编号小节，续接上页）

若两个随机变量（random variables）$X$ 与 $Y$ 由某个联合分布（joint distribution）刻画（例如联合概率密度函数（joint PDF）），则它们各自都对应一个变换 $M_X(s)$ 或 $M_Y(s)$。这些正是边际分布（marginal distributions）的变换，并不携带关于这两个随机变量之间依赖关系（dependence）的任何信息；此类信息包含在多元变换（multivariate transform）之中，我们现在就来定义它。

> <span style="color:#7f8c8d;">[OCR 说明] 原页此处将变换符号误识别为 "A1x (s) or Nly (s)"，结合上下文与全书记号，应为 $M_X(s)$ 与 $M_Y(s)$。</span>

考虑与同一试验（same experiment）相联系的 $n$ 个随机变量 $X_1, \ldots, X_n$。设 $s_1, \ldots, s_n$ 为标量自由参数（scalar free parameters）。与之相关的多元变换是这 $n$ 个参数的函数，其定义为

> <span style="color:#7f8c8d;">[原页此处为块级定义式，OCR 未捕获该式；结合上下文与全书记号，多元变换的标准定义如下。]</span>

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**[定义] 多元变换（multivariate transform）**</span>

```math
M_{X_1,\ldots,X_n}(s_1,\ldots,s_n) = E\bigl[e^{s_1 X_1 + \cdots + s_n X_n}\bigr].
```

前面讨论过的变换反演性质（inversion property）可推广到多元情形。特别地，若 $Y_1, \ldots, Y_n$ 是另一组随机变量，且对所有属于某个具有正体积的 $n$ 维立方体（$n$-dimensional cube with positive volume）的 $(s_1, \ldots, s_n)$ 均有

```math
M_{X_1,\ldots,X_n}(s_1,\ldots,s_n) = M_{Y_1,\ldots,Y_n}(s_1,\ldots,s_n),
```

则 $X_1, \ldots, X_n$ 的联合分布与 $Y_1, \ldots, Y_n$ 的联合分布相同。

> <span style="color:#7f8c8d;">[OCR 说明] 原页此句末尾 "X I , . . . . X" 中 $X_n$ 的下标 $n$ 被 OCR 丢失，按上下文补全为 $X_1, \ldots, X_n$。</span>

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">4.5　独立随机变量随机个数之和（Sum of a Random Number of Independent Random Variables）</span>

在迄今关于随机变量之和（sums of random variables）的讨论中，我们始终假定和中变量的个数（number of variables in the sum）是已知且固定的。在本节中，我们将考虑被求和的随机变量个数本身也是随机的情形。特别地，我们考虑如下之和

> <span style="color:#7f8c8d;">[原页此处为块级公式，OCR 未捕获；结合上下文，其形式为 $Y = X_1 + \cdots + X_N$。]</span>

```math
Y = X_1 + \cdots + X_N,
```

其中 $N$ 是取非负整数值（nonnegative integer values）的随机变量，而 $X_1, X_2, \ldots$ 是独立同分布（identically distributed）的随机变量。（若 $N = 0$，我们令 $Y = 0$。）我们假定 $N, X_1, X_2, \ldots$ 相互独立（independent），意思是这些随机变量的任意有限子集合（any finite subcollection）都是独立的。

用 $E[X]$ 与 $\mathrm{var}(X)$ 分别记 $X_i$ 共同的均值（mean）与方差（variance）。我们希望导出 $Y$ 的均值、方差以及变换（transform）的公式。我们采用的方法是先对事件 $\{N = n\}$ 取条件（condition on），从而回到我们更熟悉的固定个数随机变量的情形。

固定一个非负整数 $n$。随机变量 $X_1 + \cdots + X_n$ 与 $N$ 独立，因而也与事件 $\{N = n\}$ 独立。于是，

```math
E[Y \mid N = n] = E[X_1 + \cdots + X_N \mid N = n]
                = E[X_1 + \cdots + X_n \mid N = n]
                = E[X_1 + \cdots + X_n]
                = n\,E[X].
```

> <span style="color:#7f8c8d;">[OCR 说明] 上式推导在 OCR 中条件竖线多被识别为 "I"、等号有缺漏，已按标准推导链合并补全（第一步将 $X_N$ 在 $\{N = n\}$ 下替换为 $X_n$，再因 $X_1, \ldots, X_n$ 与 $N$ 独立去条件）。</span>


