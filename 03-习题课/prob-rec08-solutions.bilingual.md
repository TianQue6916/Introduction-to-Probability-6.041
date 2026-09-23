<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 8 解答（Recitation 8: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期，2010 年 10 月 5 日）</span>

<span style="color:#1e8449;">**[note]** 本解答 PDF 原文不含题面（各题直接给出解答或教材引用）。为便于阅读，以下各题题面均译自 MIT OCW 同课程配套的《Recitation 8》题目 PDF（官方原文，逐题对应）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

设 $Z$ 为连续随机变量（continuous random variable），其 probability density function（概率密度函数，PDF）为

```math
f_Z(z) = \begin{cases} \gamma\,(1+z^2), & -2 < z < 1, \\ 0, & \text{其余情形（otherwise）}. \end{cases}
```

- **(a)** $\gamma$ 取何值时这才可能成立？
- **(b)** 求 $Z$ 的 cumulative distribution function（累积分布函数，CDF）。

**（a）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 我们知道 PDF 必须积分为 1。因此
>
> ```math
> \int_{-\infty}^{\infty} f_Z(z)\,dz = \int_{-2}^{1} \gamma\,(1+z^2)\,dz = \gamma\left(z + \frac{z^3}{3}\right)\Bigg|_{-2}^{1} = 6\gamma.
> ```
>
> 由此我们得出 $\gamma = 1/6$。

**（b）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 为求 CDF，我们积分：
>
> ```math
> F_Z(z) = \int_{-\infty}^{z} f_Z(t)\,dt =
> \begin{cases}
> 0, & z < -2, \\
> \dfrac{1}{6}\left(t + \dfrac{t^3}{3}\right)\Bigg|_{-2}^{z}, & -2 \le z \le 1, \\
> 1, & z > 1,
> \end{cases}
> ```
>
> ```math
> = \begin{cases}
> 0, & z < -2, \\
> \dfrac{1}{6}\left(z + \dfrac{z^3}{3} + \dfrac{14}{3}\right), & -2 \le z \le 1, \\
> 1, & z > 1.
> \end{cases}
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

教材（text）第 186–187 页习题 3.9（Problem 3.9）。Al 家附近的出租车站与公交站在同一处。Al 在某一给定时刻到达该处：若已有出租车在等候（以概率 $2/3$ 发生），他就上车；否则他等待出租车或公交车中先到者。下一辆出租车到达所需的时间均匀分布于 0 到 10 分钟之间，而下一辆公交车恰好在 5 分钟后到达。求 Al 等待时间的 CDF 与期望值。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 见教材（textbook）习题 3.9（Problem 3.9），第 187 页。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

设 $\lambda$ 为正数。当连续随机变量 $X$ 的概率密度函数为

```math
f_X(x) = \begin{cases} \lambda e^{-\lambda x}, & x \ge 0, \\ 0, & \text{其余情形（otherwise）} \end{cases}
```

时，称 $X$ 为参数（parameter）为 $\lambda$ 的 exponential random variable（指数随机变量）。

- **(a)** 求 $X$ 的累积分布函数（CDF）。
- **(b)** 求 $X$ 的均值（mean）。
- **(c)** 求 $X$ 的方差（variance）。
- **(d)** 设 $X_1$、$X_2$、$X_3$ 为相互独立的、参数均为 $\lambda$ 的指数随机变量。求 $Z = \max\{X_1, X_2, X_3\}$ 的 PDF。
- **(e)** 求 $W = \min\{X_1, X_2\}$ 的 PDF。

**（a）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 对 $x \ge 0$：
>
> ```math
> F_X(x) = \int_{-\infty}^{x} f_X(t)\,dt = \int_{0}^{x} \lambda e^{-\lambda t}\,dt = \Bigl[-e^{-\lambda t}\Bigr]_{0}^{x} = 1 - e^{-\lambda x}.
> ```
>
> 对 $x < 0$，有 $F_X(x) = \int_{-\infty}^{x} f_X(t)\,dt = 0$。于是我们得到
>
> ```math
> F_X(x) = \begin{cases} 0, & x < 0, \\ 1 - e^{-\lambda x}, & x \ge 0. \end{cases}
> ```

**（b）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 下列计算的关键步骤用到分部积分（integration by parts），即以 $u = x$、$v = -e^{-\lambda x}$ 应用公式
>
> ```math
> \int_{0}^{\infty} u\,dv = \Bigl.uv\Bigr|_{0}^{\infty} - \int_{0}^{\infty} v\,du
> ```
>
> 如此有
>
> ```math
> E[X] = \int_{-\infty}^{\infty} x f_X(x)\,dx = \int_{0}^{\infty} x\lambda e^{-\lambda x}\,dx = \Bigl[-x e^{-\lambda x}\Bigr]_{0}^{\infty} + \int_{0}^{\infty} e^{-\lambda x}\,dx = \frac{1}{\lambda}.
> ```

**（c）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 在下式第二行中以 $u = x^2$、$v = -e^{-\lambda x}$ 作分部积分，得
>
> ```math
> E[X^2] = \int_{-\infty}^{\infty} x^2 f_X(x)\,dx = \int_{0}^{\infty} x^2 \lambda e^{-\lambda x}\,dx = \Bigl[-x^2 e^{-\lambda x}\Bigr]_{0}^{\infty} + 2\int_{0}^{\infty} x e^{-\lambda x}\,dx = \frac{2}{\lambda}E[X] = \frac{2}{\lambda^2}.
> ```
>
> 结合前一小问的计算，我们得到
>
> ```math
> \mathrm{var}(X) = E[X^2] - \bigl(E[X]\bigr)^2 = \frac{2}{\lambda^2} - \left(\frac{1}{\lambda}\right)^{2} = \frac{1}{\lambda^2}.
> ```

<!-- ===== PDF p2 ===== -->

**（续）**

**（d）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 当集合中每个元素都以 $z$ 为上界（upper bounded by $z$）时，该集合的最大值（maximum）也就以 $z$ 为上界。于是对任意正数 $z$：
>
> ```math
> P(Z \le z) = P(\max\{X_1, X_2, X_3\} \le z) = P(X_1 \le z,\, X_2 \le z,\, X_3 \le z) = P(X_1 \le z)\,P(X_2 \le z)\,P(X_3 \le z) = \bigl(1 - e^{-\lambda z}\bigr)^3,
> ```
>
> 其中第三个等号利用了 $X_1$、$X_2$、$X_3$ 的独立性（independence）。于是
>
> ```math
> F_Z(z) = \begin{cases} 0, & z < 0, \\ \bigl(1 - e^{-\lambda z}\bigr)^3, & z \ge 0. \end{cases}
> ```
>
> 对 CDF 求导，即得所求的 PDF：
>
> ```math
> f_Z(z) = \begin{cases} 0, & z < 0, \\ 3\lambda e^{-\lambda z}\bigl(1 - e^{-\lambda z}\bigr)^2, & z \ge 0. \end{cases}
> ```

**（e）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 当集合中每个元素都以 $w$ 为下界（lower bounded by $w$）时，该集合的最小值（minimum）也就以 $w$ 为下界。于是对任意正数 $w$：
>
> ```math
> P(W \ge w) = P(\min\{X_1, X_2\} \ge w) = P(X_1 \ge w,\, X_2 \ge w) = P(X_1 \ge w)\,P(X_2 \ge w) = \bigl(e^{-\lambda w}\bigr)^2 = e^{-2\lambda w},
> ```
>
> 其中第三个等号利用了 $X_1$ 与 $X_2$ 的独立性。于是
>
> ```math
> F_W(w) = \begin{cases} 0, & w < 0, \\ 1 - e^{-2\lambda w}, & w \ge 0. \end{cases}
> ```
>
> 我们可以认出这就是参数为 $2\lambda$ 的指数随机变量的 CDF。其 PDF 为
>
> ```math
> f_W(w) = \begin{cases} 0, & w < 0, \\ 2\lambda e^{-2\lambda w}, & w \ge 0. \end{cases}
> ```

<span style="color:#1e8449;">**[mathtip]** 独立指数随机变量的最小值仍服从指数分布，其参数为各参数之和（此处即 $2\lambda$）；而最大值（(d) 中的 $Z$）不服从指数分布——其 CDF 为各 CDF 之积 $\bigl(1-e^{-\lambda z}\bigr)^3$，相应 PDF 为 $3\lambda e^{-\lambda z}\bigl(1-e^{-\lambda z}\bigr)^2$。</span>

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 标准版权尾页：MIT OpenCourseWare, http://ocw.mit.edu, 6.041/6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010；课程内容至此结束。）</span>
