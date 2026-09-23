<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 11 解答（Tutorial 11: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering &amp; Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

<span style="color:#7f8c8d;">原解答 PDF 未附题面；以下题面译自 MIT OCW 同课程 Tutorial 11 习题版。</span>

连续随机变量（continuous random variables）$X$ 与 $Y$ 的 joint PDF（联合概率密度函数）为

```math
f_{X,Y}(x,y) = \begin{cases} 2/3, & (x,y)\ \text{属于闭阴影区域（the closed shaded region）}, \\[2mm] 0, & \text{否则}. \end{cases}
```

<span style="color:#7f8c8d;">【图】习题版原页此处为阴影区域示意图：$x$–$y$ 平面上由 $y = x$、$y = x - 1$、$y = 0$ 与 $x = 2$ 围成的闭四边形区域（顶点 $(0,0)$、$(1,0)$、$(2,1)$、$(2,2)$，据解答中的积分限推知），两坐标轴上标有 1 与 2。原图由后处理统一插入。</span>

我们要基于 $X$ 来估计 $Y$。

**(a)** 求 $Y$ 的 LMS estimator（LMS 估计量）$g(X)$。

**(b)** 计算 conditional mean squared error（条件均方误差）$E[(Y - g(X))^2 \mid X = x]$。

**(c)** 计算 mean squared error（均方误差）$E[(Y - g(X))^2]$。它与 $E[\mathrm{var}(Y \mid X)]$ 相同吗？

**(d)** 推导基于 $X$ 的 linear LMS estimator（线性 LMS 估计量）$L(X)$。

**(e)** 你预期 $L(X)$ 的均方误差与 $g(X)$ 的均方误差相比会如何？

**(f)** 若试图基于 $X$ 的观测求 $Y$ 的 MAP estimator（MAP 估计量），你预期会遇到什么问题（若有）？

<span style="color:#2471a3;">**[solution]**</span>

> **(a)** LMS estimator（LMS 估计量）为
>
> ```math
> g(x) = E[Y \mid X] = \begin{cases} \dfrac{X}{2}, & 0 \leq X < 1, \\[3mm] X - \dfrac{1}{2}, & 1 \leq X \leq 2, \\[3mm] \text{未定义（Undefined）}, & \text{其他}. \end{cases}
> ```
>
> **(b)** 若 $x \in [0, 1]$，则 $Y$ 的 conditional PDF（条件概率密度函数）在区间 $[0, x]$ 上 uniform（均匀）分布，且
>
> ```math
> E\left[(Y - g(X))^2 \mid X = x\right] = \frac{x^2}{12}\,.
> ```
>
> 类似地，若 $x \in [1, 2]$，则 $Y$ 的条件 PDF 在 $[1 - x,\, x]$ 上均匀分布，且
>
> ```math
> E\left[(Y - g(X))^2 \mid X = x\right] = 1/12\,.
> ```
>
> <span style="color:#1e8449;">**[note]**　原文如此（$[1 - x,\, x]$）。由联合 PDF 的支撑集及 (d) 中 $E[Y]$ 的积分限 $\int_{x-1}^{x}$ 可知，此区间应为 $[x - 1,\, x]$：其长度为 1，方差为 $1/12$、均值为 $x - \frac{1}{2}$，恰与 $g(x) = X - \frac{1}{2}$ 一致；若为 $[1 - x,\, x]$，则方差为 $(2x-1)^2/12 \neq 1/12$。</span>
>
> **(c)** 期望 $E[(Y - g(X))^2]$ 与 $E[\mathrm{var}(Y \mid X)]$ 相等，因为由 law of iterated expectations（重期望定律），
>
> ```math
> E\left[(Y - g(X))^2\right] = E\left[E\left[(Y - g(X))^2 \mid X\right]\right] = E\left[\mathrm{var}(Y \mid X)\right].
> ```
>
> 回忆 (b) 的结果：
>
> ```math
> \mathrm{var}(Y \mid X = x) = \begin{cases} \dfrac{x^2}{12}, & 0 \leq x < 1, \\[3mm] \dfrac{1}{12}, & 1 \leq x \leq 2. \end{cases}
> ```
>
> 于是
>
> ```math
> E[\mathrm{var}(Y \mid X)] = \int_x \mathrm{var}(Y \mid X = x)\, f_X(x)\, dx = \int_0^1 \frac{x^2}{12} \cdot \frac{2}{3}x\, dx + \int_1^2 \frac{1}{12} \cdot \frac{2}{3}\, dx = \frac{5}{72}\,.
> ```
>
> 注意
>
> ```math
> f_X(x) = \begin{cases} 2x/3, & 0 \leq x < 1, \\[2mm] 2/3, & 1 \leq x \leq 2. \end{cases}
> ```
>
> **(d)** 线性 LMS 估计量为
>
> ```math
> L(X) = E[Y] + \frac{\mathrm{cov}(X, Y)}{\mathrm{var}(X)}\left[X - E[X]\right].
> ```
>
> 为计算 $\mathrm{var}(X)$，先计算 $E[X^2]$ 与 $E[X]^2$：
>
> ```math
> \begin{aligned}
> E[X^2] &= \int_0^1 x^2 \cdot \frac{2}{3}x\, dx + \int_1^2 x^2 \cdot \frac{2}{3}\, dx\,, \\
> &= \frac{31}{18}\,,
> \end{aligned}
> ```
>
> ```math
> \begin{aligned}
> E[X] &= \int_0^1 x \cdot \frac{2}{3}x\, dx + \int_1^2 x \cdot \frac{2}{3}\, dx\,, \\
> &= \frac{11}{9}
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[note]**　原文此两处第一个积分的上限均印作 $2$（$\int_0^2$）。由 $f_X(x) = 2x/3$ 仅在 $[0,1)$ 上成立、且结果为 $E[X^2] = 31/18$、$E[X] = 11/9$ 可验证，正确上限应为 $1$；若上限为 $2$，则分别得 $38/9$ 与 $25/9$，均与原文结果矛盾。译文已按正确积分限还原。</span>

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> ```math
> \mathrm{var}(X) = E[X^2] - E[X]^2 = \frac{37}{162}\,.
> ```
>
> ```math
> E[Y] = \int_0^1 \int_0^x \frac{2}{3}\, y\, dy\, dx + \int_1^2 \int_{x-1}^{x} \frac{2}{3}\, y\, dy\, dx = \frac{1}{9} + \frac{2}{3} = \frac{7}{9}\,.
> ```
>
> 为确定 $\mathrm{cov}(X, Y)$，需要计算 $E[XY]$：
>
> ```math
> \begin{aligned}
> E[XY] &= \int_x \int_y xy\, f_{X,Y}(x, y)\, dy\, dx \\
> &= \int_0^1 \int_0^x yx \cdot \frac{2}{3}\, dy\, dx + \int_1^2 \int_{x-1}^{x} yx \cdot \frac{2}{3}\, dy\, dx \\
> &= \frac{41}{36}
> \end{aligned}
> ```
>
> 于是 $\mathrm{cov}(X, Y) = E[XY] - E[X]E[Y] = \dfrac{61}{324}$。因此
>
> ```math
> L(X) = \frac{7}{9} + \frac{61}{74}\left[X - \frac{11}{9}\right].
> ```
>
> **(e)** LMS 估计量是（在所有基于 $X$ 的 $Y$ 的估计量中）使均方误差最小的那个。因此，线性 LMS 估计量不可能表现得比 LMS 估计量更好，即我们预期 $E[(Y - L(X))^2] \geq E[(Y - g(X))^2]$。事实上，
>
> ```math
> \begin{aligned}
> E[(Y - L(X))^2] &= \sigma_Y^2\left(1 - \rho^2\right), \\
> &= \sigma_Y^2\left(1 - \frac{\mathrm{cov}(X, Y)^2}{\sigma_X^2\, \sigma_Y^2}\right), \\
> &= \frac{37}{162}\left(1 - \left(\frac{61}{74}\right)^2\right), \\
> &= 0.073 \geq \frac{5}{72}
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[mathtip]**　其中 $\sigma_X^2 = \mathrm{var}(X) = \frac{37}{162}$；又 $E[Y^2] = \frac{5}{6}$，故 $\sigma_Y^2 = E[Y^2] - (E[Y])^2 = \frac{5}{6} - \frac{49}{81} = \frac{37}{162}$，从而 $\rho = \frac{\mathrm{cov}(X,Y)}{\sigma_X \sigma_Y} = \frac{61/324}{37/162} = \frac{61}{74}$。</span>
>
> **(f)** 对 $X$ 的单个观测值 $x$，MAP 估计不唯一，因为对该 $x$ 而言 $Y$ 的所有可能取值是等可能的。因此，MAP 估计量给不出有意义的结果。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

<span style="color:#7f8c8d;">原解答 PDF 未附题面；以下题面译自 MIT OCW 同课程 Tutorial 11 习题版。</span>

考虑一个 noisy channel（有噪信道），你通过它向朋友发送由 0 和 1 组成的消息。已知该信道以某个固定概率 $p$ 独立地 flip（翻转）所发送的每一个 bit（比特），但 $p$ 的值未知。你决定做一些实验来估计 $p$，于是请这位朋友帮忙。而这位朋友颇为淘气，坚持要你每次发送由三个比特组成的消息（双方事先约定好）；对每条消息，她只告诉你该消息中被翻转的比特总数。设 $X$ 为某条三比特消息中被翻转的比特数。

**(a)** 求 $X$ 的 PMF（概率质量函数）。

**(b)** 基于 $X_1, \ldots, X_n$（前 $n$ 条三比特消息中被翻转的比特数），推导 $p$ 的 ML estimator（ML 估计量，最大似然估计量）。

**(c)** 该 ML 估计量是 unbiased（无偏的）吗？

**(d)** 该 ML 估计量是 consistent（一致的）吗？

**(e)** 你发送了 $n = 100$ 条三比特消息，发现被翻转的比特总数为 20。构造 $p$ 的 95% confidence interval（置信区间）。如有必要，可对被翻转比特数的方差使用一个保守界。

**(f)** 还有哪些估计方差的方法？你预期置信区间会随方差估计的不同而如何变化？

<span style="color:#2471a3;">**[solution]**</span>

> **(a)** $X$ 是参数 $n = 3$、且给定"单个比特在通过有噪信道的一次传输中被翻转"的概率 $p$ 的 binomial random variable（二项随机变量）：
>
> ```math
> p_X(k;\, p) = \begin{cases} \dbinom{3}{k}\, p^k (1 - p)^{3-k}, & k = 0, 1, 2, 3, \\[3mm] 0, & \text{其他（o.w.）}. \end{cases}
> ```
>
> **(b)** 为基于 $X_1, \ldots, X_n$（前 $n$ 条三比特消息中被翻转的比特数）推导 $p$ 的 ML 估计量，需要找到使 likelihood function（似然函数）最大的 $p$ 值：
>
> ```math
> \hat{p}_n = \arg\max_p\ p_{X_1, \ldots, X_n}(k_1, k_2, \ldots, k_n;\, p)
> ```
>
> 由于各 $X_i$ 相互独立，似然函数简化为：

<!-- ===== PDF p3 ===== -->

> **（续）**
>
> ```math
> p_{X_1, \ldots, X_n}(k_1, \ldots, k_n;\, p) = \prod_{i=1}^{n} p_{X_i}(k_i;\, p) = \prod_{i=1}^{n} \binom{3}{k_i}\, p^{k_i} (1 - p)^{3 - k_i}
> ```
>
> log-likelihood function（对数似然函数）为
>
> ```math
> \log\left(p_{X_1, \ldots, X_n}(k_1, \ldots, k_n;\, p)\right) = \sum_{i=1}^{n}\left( k_i \log(p) + (3 - k_i)\log(1 - p) + \log \binom{3}{k_i} \right)
> ```
>
> 然后对 $p$ 最大化该对数似然函数：
>
> ```math
> \frac{1}{p}\left(\sum_{i=1}^{n} k_i\right) - \frac{1}{1 - p}\left(\sum_{i=1}^{n} (3 - k_i)\right) = 0
> ```
>
> ```math
> \left(3n - \sum_{i=1}^{n} k_i\right) p = \left(\sum_{i=1}^{n} k_i\right)(1 - p)
> ```
>
> ```math
> \hat{p}_n = \frac{1}{3n} \sum_{i=1}^{n} k_i
> ```
>
> 这就得到 ML 估计量：
>
> ```math
> \hat{P}_n = \frac{1}{3n} \sum_{i=1}^{n} X_i
> ```
>
> **(c)** 该估计量是无偏的（unbiased），因为：
>
> ```math
> E_p[\hat{P}_n] = \frac{1}{3n} \sum_{i=1}^{n} E_p[X_i] = \frac{1}{3n} \sum_{i=1}^{n} 3p = p
> ```
>
> **(d)** 由 weak law of large numbers（弱大数定律），$\frac{1}{n}\sum_{i=1}^{n} X_i$ converges in probability（依概率收敛）到 $E_p[X_i] = 3p$，因此 $\hat{P}_n = \frac{1}{3} \cdot \frac{1}{n}\sum_{i=1}^{n} X_i$ 依概率收敛到 $p$。故 $\hat{P}_n$ 是一致的（consistent）。
>
> **(e)** 发送三比特消息而不是一比特消息，并不影响 $p$ 的 ML 估计。为看清这一点，设 $Y_i$ 为 Bernoulli RV（伯努利随机变量），当第 $i$ 个比特被翻转（概率 $p$）时取值 1；并设 $m = 3n$ 为通过信道发送的比特总数。则 $p$ 的 ML 估计为
>
> ```math
> \hat{P}_n = \frac{1}{3n} \sum_{i=1}^{n} X_i = \frac{1}{m} \sum_{i=1}^{m} Y_i\,.
> ```
>
> 利用 central limit theorem（中心极限定理），对大的 $n$，$\hat{P}_n$ 近似为 normal（正态）随机变量。于是 $p$ 的近似 95% 置信区间为
>
> ```math
> \left[\hat{P}_n - 1.96\sqrt{\frac{v}{m}},\ \hat{P}_n + 1.96\sqrt{\frac{v}{m}}\right],
> ```

<!-- ===== PDF p4 ===== -->

> **（续）**
>
> 其中 $v$ 为 $Y_i$ 的方差。
>
> 按题目提示，我们用保守上界 $1/4$ 来估计未知方差 $v$。又已知 $n = 100$ 且被翻转的比特数为 20，得 $\hat{P}_n = \dfrac{2}{30}$。于是，近似 95% 置信区间为 $[0.01,\ 0.123]$。
>
> <span style="color:#1e8449;">**[mathtip]**　$m = 300$，$\hat{P}_n = 20/300 = 2/30 \approx 0.0667$；区间为 $0.0667 \pm 1.96\sqrt{0.25/300} \approx 0.0667 \pm 0.0566$，即 $[0.010,\ 0.123]$。</span>
>
> **(f)** 方差的其他估计量有 sample variance（样本方差）以及估计量 $\hat{P}_n(1 - \hat{P}_n)$。与 (e) 中使用的保守方差估计相比，它们可能给出更窄的置信区间。

<!-- ===== PDF p5 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability）· Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms</span>
