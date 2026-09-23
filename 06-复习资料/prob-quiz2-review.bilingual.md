<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 2 复习幻灯（Review Slides）**</span> <span style="color:#7f8c8d;">（Quiz II Review，Fall 2010，2010 秋季学期）</span>

> <span style="color:#7f8c8d;">说明：源文件为考前复习幻灯，原 PDF 共 7 页、每页并排多张幻灯片；译文按原 PDF 页码 p1–p7 连续整理，每张幻灯片的标题作为一节。首页幻灯片带有课程页眉：6.041/6.431 Probabilistic Systems Analysis · Quiz II Review · Fall 2010。</span>

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Probability Density Functions（概率密度函数，PDF）**</span>

设 $X$ 为 continuous RV（连续随机变量），其 PDF（概率密度函数）为 $f_X(x)$：

```math
P(a \le X \le b) = \int_a^b f_X(x)\,dx, \qquad P(X \in A) = \int_A f_X(x)\,dx
```

Properties（性质）：

- Nonnegativity（非负性）：$f_X(x) \ge 0 \;\;\forall x$；
- Normalization（归一化）：

```math
\int_{-\infty}^{\infty} f_X(x)\,dx = 1
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**PDF Interpretation（PDF 的解读）**</span>

- Caution（注意）：$f_X(x) \neq P(X = x)$。
- 若 $X$ 是连续随机变量，则 $P(X = x) = 0$，对一切 $x$ 都成立！！
- $f_X(x)$ 的取值可以 $\ge 1$。
- Interpretation（解读）：$f_X(x)$ 度量的是 $x$ 附近"小"区间上的"单位长度的概率"（probability per unit length）：

```math
P(x \le X \le x + \delta) \approx f_X(x)\,\delta
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Mean and Variance of a Continuous RV（连续随机变量的均值与方差）**</span>

```math
E[X] = \int_{-\infty}^{\infty} x\, f_X(x)\,dx
```

```math
\mathrm{Var}(X) = E\!\left[(X - E[X])^2\right] = \int_{-\infty}^{\infty} (x - E[X])^2 f_X(x)\,dx = E[X^2] - (E[X])^2 \;(\ge 0)
```

```math
E[g(X)] = \int_{-\infty}^{\infty} g(x)\, f_X(x)\,dx
```

```math
E[aX + b] = a\,E[X] + b, \qquad \mathrm{Var}(aX + b) = a^2\,\mathrm{Var}(X)
```

<!-- ===== PDF p2 ===== -->

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Cumulative Distribution Functions（累积分布函数，CDF）**</span>

Definition（定义）：$F_X(x) = P(X \le x)$，它从 $-\infty$ 处的 $0$ 单调递增（monotonically increasing）到 $+\infty$ 处的 $1$。

- Continuous RV（连续随机变量）（CDF 关于 $x$ 连续）：

```math
F_X(x) = P(X \le x) = \int_{-\infty}^{x} f_X(t)\,dt, \qquad f_X(x) = \frac{dF_X(x)}{dx}
```

- Discrete RV（离散随机变量）（CDF 为分段常数，piecewise constant）：

```math
F_X(x) = P(X \le x) = \sum_{k \le x} p_X(k), \qquad p_X(k) = F_X(k) - F_X(k-1)
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Uniform Random Variable（均匀随机变量）**</span>

设 $X$ 是区间 $[a, b]$ 上的 uniform random variable（均匀随机变量）：

```math
f_X(x) = \begin{cases} \dfrac{1}{b-a}, & \text{if } a \le x \le b \\[4pt] 0, & \text{otherwise} \end{cases}
```

```math
F_X(x) = \begin{cases} 0, & \text{if } x \le a \\[4pt] \dfrac{x-a}{b-a}, & \text{if } a \le x \le b \\[4pt] 1, & \text{otherwise } (x > b) \end{cases}
```

```math
E[X] = \frac{a+b}{2}, \qquad \mathrm{Var}(X) = \frac{(b-a)^2}{12}
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Exponential Random Variable（指数随机变量）**</span>

设 $X$ 是参数为 $\lambda$ 的 exponential random variable（指数随机变量）：

```math
f_X(x) = \begin{cases} \lambda e^{-\lambda x}, & \text{if } x \ge 0 \\[2pt] 0, & \text{otherwise} \end{cases} \qquad\quad F_X(x) = \begin{cases} 1 - e^{-\lambda x}, & \text{if } x \ge 0 \\[2pt] 0, & \text{otherwise} \end{cases}
```

```math
E[X] = \frac{1}{\lambda}, \qquad \mathrm{Var}(X) = \frac{1}{\lambda^2}
```

- Memoryless Property（无记忆性）：在给定 $X > t$ 的条件下，$X - t$ 仍是参数为 $\lambda$ 的指数随机变量（exponential RV）。

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Normal/Gaussian Random Variables（正态/高斯随机变量）**</span>

General normal RV（一般正态随机变量）$N(\mu, \sigma^2)$：

```math
f_X(x) = \frac{1}{\sigma\sqrt{2\pi}}\; e^{-(x-\mu)^2/2\sigma^2}, \qquad E[X] = \mu, \quad \mathrm{Var}(X) = \sigma^2
```

Property（性质）：若 $X \sim N(\mu, \sigma^2)$ 且 $Y = aX + b$，则

```math
Y \sim N(a\mu + b,\; a^2\sigma^2)
```

<!-- ===== PDF p3 ===== -->

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Normal CDF（正态分布的 CDF）**</span>

Standard Normal RV（标准正态随机变量）：$N(0, 1)$。

标准正态随机变量 $Y$ 在 $y$ 处的 CDF 记作 $\Phi(y)$：

- $y \ge 0$ 的取值已制成表格（given in tables）可供查用；
- $y < 0$ 时利用结果：$\Phi(y) = 1 - \Phi(-y)$。

要计算一般正态随机变量的 CDF，把它表示成标准正态随机变量的函数：

```math
X \sim N(\mu, \sigma^2) \;\Longleftrightarrow\; \frac{X - \mu}{\sigma} \sim N(0, 1)
```

```math
P(X \le x) = P\!\left(\frac{X - \mu}{\sigma} \le \frac{x - \mu}{\sigma}\right) = \Phi\!\left(\frac{x - \mu}{\sigma}\right)
```

> <span style="color:#1e8449;">**[note]**　源片此句写作 "To evaluate CDF of a general standard normal"（"一般标准正态"），措辞自相矛盾；按上下文应指一般（非标准）正态随机变量，译文已据此译出。</span>

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Joint PDF（联合 PDF）**</span>

两个连续随机变量（continuous RV）$X$ 与 $Y$ 的 joint PDF（联合 PDF）：$f_{X,Y}(x, y)$。

```math
P(A) = \iint_A f_{X,Y}(x, y)\,dx\,dy
```

Marginal PDF（边缘 PDF）：

```math
f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x, y)\,dy
```

```math
E[g(X, Y)] = \int_{-\infty}^{\infty}\!\!\int_{-\infty}^{\infty} g(x, y)\, f_{X,Y}(x, y)\,dx\,dy
```

Joint CDF（联合 CDF）：$F_{X,Y}(x, y) = P(X \le x,\, Y \le y)$。

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Independence（独立性）**</span>

By definition（按定义）：$X$ 与 $Y$ 相互独立（independent）$\iff f_{X,Y}(x, y) = f_X(x)\, f_Y(y)$，对一切 $(x, y)$ 成立。

若 $X$ 与 $Y$ 相互独立：

- $E[XY] = E[X]\, E[Y]$；
- $g(X)$ 与 $h(Y)$ 相互独立；
- $E[g(X)h(Y)] = E[g(X)]\, E[h(Y)]$。

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Conditioning on an Event（以事件为条件）**</span>

设 $X$ 为连续随机变量，$A$ 为满足 $P(A) > 0$ 的 event（事件）：

```math
f_{X|A}(x) = \begin{cases} \dfrac{f_X(x)}{P(X \in A)}, & \text{if } x \in A \\[4pt] 0, & \text{otherwise} \end{cases}
```

```math
P(X \in B \mid X \in A) = \int_B f_{X|A}(x)\,dx
```

```math
E[X \mid A] = \int_{-\infty}^{\infty} x\, f_{X|A}(x)\,dx, \qquad E[g(X) \mid A] = \int_{-\infty}^{\infty} g(x)\, f_{X|A}(x)\,dx
```

<!-- ===== PDF p4 ===== -->

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Conditioning on a RV（以随机变量为条件）**</span>

$X, Y$ 为连续随机变量（continuous RV）：

```math
f_{X|Y}(x \mid y) = \frac{f_{X,Y}(x, y)}{f_Y(y)}
```

```math
f_X(x) = \int_{-\infty}^{\infty} f_Y(y)\, f_{X|Y}(x \mid y)\,dy
```

（相当于全概率定理，$\approx$ total probability theorem）

Conditional Expectation（条件期望）：

```math
E[X \mid Y = y] = \int_{-\infty}^{\infty} x\, f_{X|Y}(x \mid y)\,dx
```

```math
E[g(X) \mid Y = y] = \int_{-\infty}^{\infty} g(x)\, f_{X|Y}(x \mid y)\,dx
```

```math
E[g(X, Y) \mid Y = y] = \int_{-\infty}^{\infty} g(x, y)\, f_{X|Y}(x \mid y)\,dx
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Continuous Bayes' Rule（连续版贝叶斯法则）**</span>

$X, Y$ 为连续随机变量，$N$ 为 discrete RV（离散随机变量），$A$ 为一个事件。

```math
f_{X|Y}(x \mid y) = \frac{f_{Y|X}(y \mid x)\, f_X(x)}{f_Y(y)} = \frac{f_{Y|X}(y \mid x)\, f_X(x)}{\displaystyle\int_{-\infty}^{\infty} f_{Y|X}(y \mid t)\, f_X(t)\,dt}
```

```math
P(A \mid Y = y) = \frac{f_{Y|A}(y)\, P(A)}{f_Y(y)} = \frac{f_{Y|A}(y)\, P(A)}{f_{Y|A}(y)\, P(A) + f_{Y|A^c}(y)\, P(A^c)}
```

```math
P(N = n \mid Y = y) = \frac{p_N(n)\, f_{Y|N}(y \mid n)}{f_Y(y)} = \frac{p_N(n)\, f_{Y|N}(y \mid n)}{\displaystyle\sum_i p_N(i)\, f_{Y|N}(y \mid i)}
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Total Expectation Theorem（全期望定理）**</span>

若 $A_1, \ldots, A_n$ 是构成样本空间（sample space）的一个划分（partition）的两两不相交事件（disjoint events）：

```math
f_X(x) = \sum_{i=1}^{n} P(A_i)\, f_{X|A_i}(x)
```

（相当于全概率定理，$\approx$ total probability theorem）

```math
E[X] = \sum_{i=1}^{n} P(A_i)\, E[X \mid A_i], \qquad E[g(X)] = \sum_{i=1}^{n} P(A_i)\, E[g(X) \mid A_i]
```

（全期望定理，total expectation theorem）

若改以连续随机变量 $Y$ 为条件，则为：

```math
E[X] = \int_{-\infty}^{\infty} E[X \mid Y = y]\, f_Y(y)\,dy
```

```math
E[g(X)] = \int_{-\infty}^{\infty} E[g(X) \mid Y = y]\, f_Y(y)\,dy, \qquad E[g(X, Y)] = \int_{-\infty}^{\infty} E[g(X, Y) \mid Y = y]\, f_Y(y)\,dy
```

<!-- ===== PDF p5 ===== -->

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Derived Distributions（派生分布）**</span>

Definition（定义）：已知随机变量 $X$ 的 PDF，求其函数 $Y = g(X)$ 的 PDF。

Method（方法）：

- 先求 CDF：

```math
F_Y(y) = P(Y \le y) = P(g(X) \le y) = \int_{\{x:\, g(x) \le y\}} f_X(x)\,dx
```

- 再求导（differentiate）：$f_Y(y) = \dfrac{dF_Y(y)}{dy}$。

Special case（特例）：若 $Y = g(X) = aX + b$，则

```math
f_Y(y) = \frac{1}{|a|}\; f_X\!\left(\frac{y - b}{a}\right)
```

> <span style="color:#1e8449;">**[note]**　源片特例公式中的分式印作 $\frac{x-b}{a}$；按线性变换公式自变量应为 $y$（由 $F_Y(y) = P\!\big(X \le \frac{y-b}{a}\big)$ 求导即得 $f_Y(y) = \frac{1}{|a|}f_X\big(\frac{y-b}{a}\big)$），译文已按正确形式还原。</span>

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Convolution（卷积）**</span>

设 $W = X + Y$，其中 $X$ 与 $Y$ 相互独立（independent）。

- Discrete case（离散情形）：

```math
p_W(w) = \sum_{x} p_X(x)\, p_Y(w - x)
```

- Continuous case（连续情形）：

```math
f_W(w) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(w - x)\,dx
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Graphical Method（图解法）**</span>

（计算卷积的图解步骤）

- 把两个 PMF（或 PDF）上下叠放在一起（put the PMFs or PDFs on top of each other）；
- 翻转（flip）$Y$ 的 PMF（或 PDF）；
- 把翻转后的 $Y$ 的 PMF（或 PDF）平移（shift）$w$；
- 逐点相乘再相加（cross-multiply and add），或等价地计算积分（evaluate the integral）。

特别地（in particular）：若 $X$ 与 $Y$ 相互独立且均服从正态分布（normal），则 $W = X + Y$ 服从正态分布。

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Law of Iterated Expectations（迭代期望定律）**</span>

- $E[X \mid Y = y] = f(y)$ 是一个 number（数）；
- $E[X \mid Y] = f(Y)$ 是一个 random variable（随机变量）（期望是对 $X$ 取的，the expectation is taken with respect to $X$）。

要计算 $E[X \mid Y]$，先把 $E[X \mid Y = y]$ 表示成 $y$ 的函数。

Law of iterated expectations（迭代期望定律）：

```math
E[X] = E\big[E[X \mid Y]\big]
```

（这是两个实数之间的等式，equality between two real numbers）

<!-- ===== PDF p6 ===== -->

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Law of Total Variance（全方差定律）**</span>

$\mathrm{Var}(X \mid Y)$ 是一个随机变量，它是 $Y$ 的函数（方差是对 $X$ 取的）。

要计算 $\mathrm{Var}(X \mid Y)$，先把

```math
\mathrm{Var}(X \mid Y = y) = E\!\left[(X - E[X \mid Y = y])^2 \,\Big|\, Y = y\right]
```

表示成 $y$ 的函数。

Law of conditional variances（条件方差定律）：

```math
\mathrm{Var}(X) = E\big[\mathrm{Var}(X \mid Y)\big] + \mathrm{Var}\big(E[X \mid Y]\big)
```

（这是两个实数之间的等式，equality between two real numbers）

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Sum of a Random Number of i.i.d. RVs（数量随机的独立同分布随机变量之和）**</span>

设 $N$ 为离散随机变量（discrete RV），$X_i$ 为 i.i.d.（独立同分布）随机变量且与 $N$ 相互独立。令 $Y = X_1 + \cdots + X_N$，则：

```math
E[Y] = E[X]\, E[N]
```

```math
\mathrm{Var}(Y) = E[N]\, \mathrm{Var}(X) + (E[X])^2\, \mathrm{Var}(N)
```

---

<span style="color:#2471a3;">**[section]**</span>　<span style="color:#c0392b;">**Covariance and Correlation（协方差与相关）**</span>

```math
\mathrm{Cov}(X, Y) = E\big[(X - E[X])(Y - E[Y])\big] = E[XY] - E[X]\, E[Y]
```

- By definition（按定义）：$X$ 与 $Y$ 不相关（uncorrelated）$\iff \mathrm{Cov}(X, Y) = 0$。
- 若 $X$ 与 $Y$ 相互独立 $\Rightarrow$ $X$ 与 $Y$ 不相关（反之不成立，the converse is not true）。
- In general（一般地）：

```math
\mathrm{Var}(X + Y) = \mathrm{Var}(X) + \mathrm{Var}(Y) + 2\,\mathrm{Cov}(X, Y)
```

- 若 $X$ 与 $Y$ 不相关，则 $\mathrm{Cov}(X, Y) = 0$ 且 $\mathrm{Var}(X + Y) = \mathrm{Var}(X) + \mathrm{Var}(Y)$。

Correlation Coefficient（相关系数）（dimensionless，无量纲）：

```math
\rho = \frac{\mathrm{Cov}(X, Y)}{\sigma_X\, \sigma_Y} \in [-1,\, 1]
```

- $\rho = 0 \iff X$ 与 $Y$ 不相关；
- $|\rho| = 1 \iff X - E[X] = c\,[\,Y - E[Y]\,]$（$X$ 与 $Y$ 线性相关，linearly related）。

<!-- ===== PDF p7 ===== -->

---

> <span style="color:#7f8c8d;">MIT OpenCourseWare　·　http://ocw.mit.edu　·　6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）　·　Fall 2010（2010 秋季学期）　·　有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
