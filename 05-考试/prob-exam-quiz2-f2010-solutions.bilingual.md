<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 2 解答（Quiz 2: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）· 电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）· 6.041/6.431：概率系统分析（Probabilistic Systems Analysis），Fall 2010。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1（80 分）**</span>

本题中：

(i) $X$ 是 $[0,4]$ 上的（连续）均匀随机变量（uniform random variable）。

(ii) $Y$ 是与 $X$ 独立的指数随机变量（exponential random variable），参数 $\lambda = 2$。

**1.（10 分）求 $X - 3Y$ 的均值与方差（mean and variance）。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> E[X - 3Y] = E[X] - 3\,E[Y] = 2 - 3\cdot\frac{1}{2} = \frac{1}{2},
> ```
>
> ```math
> \mathrm{var}(X - 3Y) = \mathrm{var}(X) + 9\,\mathrm{var}(Y) = \frac{(4-0)^2}{12} + 9\cdot\frac{1}{2^2} = \frac{43}{12}.
> ```

**2.（10 分）求 $Y \ge X$ 的概率。**（记本题答案为常数 $c$。）

> <span style="color:#2471a3;">**[solution]**</span>
>
> $X$ 与 $Y$ 的 PDF 分别为：
>
> ```math
> f_X(x) = \begin{cases} 1/4, & \text{若 } 0 \le x \le 4, \\[4pt] 0, & \text{其他情形}, \end{cases} \qquad\qquad f_Y(y) = \begin{cases} 2e^{-2y}, & \text{若 } y \ge 0, \\[4pt] 0, & \text{其他情形}. \end{cases}
> ```
>
> 利用全概率定理（total probability theorem），
>
> ```math
> P(Y \ge X) = \int f_X(x)\,P(Y \ge X \mid X = x)\,dx = \int_0^4 \frac{1}{4}\bigl(1 - F_Y(x)\bigr)\,dx = \int_0^4 \frac{1}{4}\,e^{-2x}\,dx = \frac{1}{8}\int_0^4 2e^{-2x}\,dx = \frac{1}{8}\bigl(1 - e^{-8}\bigr).
> ```

<!-- ===== PDF p2 ===== -->

**3.（10 分）求在事件 $Y \ge X$ 已经发生的条件下，$X$ 与 $Y$ 的条件联合 PDF（conditional joint PDF）。**（答案可以用上一小问中的常数 $c$ 来表示。）

> <span style="color:#2471a3;">**[solution]**</span>
>
> 设 $A$ 为事件 $Y \ge X$。由于 $X$ 与 $Y$ 独立，
>
> ```math
> f_{X,Y\mid A}(x,y) = \frac{f_X(x)\,f_Y(y)}{P(A)} = \frac{f_X(x)\,f_Y(y)}{c} = \begin{cases} \dfrac{4e^{-2y}}{1 - e^{-8}}, & \text{若 } (x,y)\in A \text{，即 } 0 \le x \le 4,\ y \ge x, \\[8pt] 0, & \text{其他情形}. \end{cases}
> ```

**4.（10 分）求 $Z = X + Y$ 的 PDF。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 由于 $X$ 与 $Y$ 独立，可以用卷积积分（convolution integral）来求 $f_Z(z)$：
>
> ```math
> f_Z(z) = \int_{\max(0,\,z-4)}^{z} \frac{1}{4}\cdot 2e^{-2t}\,dt = \begin{cases} \dfrac{1}{4}\left(1 - e^{-2z}\right), & \text{若 } 0 \le z \le 4, \\[8pt] \dfrac{1}{4}\left(e^{8} - 1\right)e^{-2z}, & \text{若 } z > 4, \\[8pt] 0, & \text{其他情形}. \end{cases}
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 当 $z>4$ 时积分下限为 $z-4$，此时 $e^{-2(z-4)} = e^{8}\,e^{-2z}$，故结果中出现因子 $(e^8-1)$。

**5.（10 分）画出在给定 $Y = 3$ 的条件下 $Z$ 的条件 PDF 的完整标注草图（fully labeled sketch）。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 给定 $Y = 3$ 时，$Z = X + 3$，因此 $Z$ 的条件 PDF 就是 $X$ 的 PDF 平移后的版本。$Z$ 的条件 PDF 及其草图为：
>
> ```math
> f_{Z\mid\{Y=3\}}(z) = \begin{cases} \dfrac{1}{4}, & \text{若 } 3 \le z \le 7, \\[8pt] 0, & \text{其他情形}. \end{cases}
> ```
>
> <span style="color:#7f8c8d;">【图】原页此处为该条件 PDF 的草图：在区间 $[3,7]$ 上高度为 $1/4$ 的矩形（均匀分布），横轴标 $z$，并标注端点 3 与 7。原图由后处理统一插入。</span>

**6.（10 分）求 $E[Z \mid Y = y]$ 与 $E[Z \mid Y]$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 条件 PDF $f_{Z\mid Y=y}(z)$ 是 $y$ 与 $y+4$ 之间的均匀分布。因此
>
> ```math
> E[Z \mid Y = y] = y + 2.
> ```
>
> 上式对所有可能的 $y$ 值都成立，所以
>
> ```math
> E[Z \mid Y] = Y + 2.
> ```

**7.（10 分）求 $Z$ 与 $Y$ 的联合 PDF $f_{Z,Y}$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> $Z$ 与 $Y$ 的联合 PDF 可表示为：
>
> ```math
> f_{Z,Y}(z,y) = f_Y(y)\,f_{Z\mid Y}(z \mid y) = \begin{cases} \dfrac{1}{2}\cdot e^{-2y}, & \text{若 } y \ge 0,\ y \le z \le y + 4, \\[8pt] 0, & \text{其他情形}. \end{cases}
> ```

<!-- ===== PDF p3 ===== -->

**8.（10 分）** 随机变量 $W$ 定义如下：抛一枚均匀硬币（与 $Y$ 独立）。若结果为"正面"（heads），令 $W = Y$；若为反面，令 $W = 2 + Y$。求在给定 $W = 3$ 的条件下出现"正面"的概率。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 设 $X$ 为描述均匀硬币结果的伯努利随机变量（Bernoulli random variable），硬币落在"正面"时 $X = 1$。由于硬币均匀，$P(X = 1) = P(X = 0) = 1/2$。此外，在给定 $X$ 取值的条件下，$W$ 的条件 PDF 为：
>
> ```math
> f_{W\mid X=1}(w) = f_Y(w), \qquad\qquad f_{W\mid X=0}(w) = f_Y(w - 2).
> ```
>
> 利用贝叶斯法则（Bayes' Rule）的相应变形：
>
> ```math
> P(X = 1 \mid W = 3) = \frac{P(X = 1)\,f_{W\mid X=1}(3)}{P(X = 1)\,f_{W\mid X=1}(3) + P(X = 0)\,f_{W\mid X=0}(3)} = \frac{P(X = 1)\,f_Y(3)}{P(X = 1)\,f_Y(3) + P(X = 0)\,f_Y(1)} = \frac{e^{-6}}{e^{-6} + e^{-2}}.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2（30 分）**</span>

设 $X, X_1, X_2, \ldots$ 为独立的正态随机变量（normal random variables），均值为 0、方差为 9。设 $N$ 为取正整数值的随机变量，满足 $E[N] = 2$、$E[N^2] = 5$。假设随机变量 $N, X, X_1, X_2, \ldots$ 相互独立。令 $S = \sum_{i=1}^{N} X_i$。

**1.（10 分）** 若 $\delta$ 是一个小的正数，则有 $P(1 \le |X| \le 1 + \delta) \approx \alpha\,\delta$，其中 $\alpha$ 为某常数。求 $\alpha$ 的值。

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> P(1 \le |X| \le 1 + \delta) = 2\,P(1 \le X \le 1 + \delta) \approx 2\,f_X(1)\,\delta.
> ```
>
> 因此，
>
> ```math
> \alpha = 2\,f_X(1) = 2\cdot\frac{1}{\sqrt{9\cdot 2\pi}}\;e^{-\frac{(1-0)^2}{2\cdot 9}} = \frac{2}{3\sqrt{2\pi}}\;e^{-\frac{1}{18}}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 这里用到：$\delta$ 很小时 $P(x \le X \le x + \delta) \approx f_X(x)\,\delta$；再由 $X$ 的密度关于 0 对称，区间 $[1, 1+\delta]$ 与 $[-1-\delta, -1]$ 贡献相同，故多出因子 2。

**2.（10 分）求 $S$ 的方差。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 利用全方差定律（Law of Total Variance），
>
> ```math
> \mathrm{var}(S) = E[\mathrm{var}(S \mid N)] + \mathrm{var}(E[S \mid N]) = E[9N] + \mathrm{var}(0\cdot N) = 9\,E[N] = 18.
> ```

<!-- ===== PDF p4 ===== -->

**3.（5 分）$N$ 与 $S$ 不相关吗？请给出理由。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> $S$ 与 $N$ 的协方差（covariance）为
>
> ```math
> \mathrm{cov}(S, N) = E[SN] - E[S]\,E[N] = E\bigl[E[SN \mid N]\bigr] - E\bigl[E[S \mid N]\bigr]\,E[N]
> ```
>
> ```math
> = E\Bigl[E\Bigl[\textstyle\sum_{i=1}^{N} X_i\,N \,\Big|\, N\Bigr]\Bigr] - E\Bigl[E\Bigl[\textstyle\sum_{i=1}^{N} X_i \,\Big|\, N\Bigr]\Bigr]E[N] = E[X_1]\,E[N^2] - E[X_1]\,\bigl(E[N]\bigr)^2 = 0,
> ```
>
> 因为 $E[X_1] = 0$。所以 $S$ 与 $N$ 不相关（uncorrelated）。

**4.（5 分）$N$ 与 $S$ 独立吗？请给出理由。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> $S$ 与 $N$ 不独立。
>
> **证明（Proof）：** 我们有 $\mathrm{var}(S \mid N) = 9N$ 与 $\mathrm{var}(S) = 18$；更一般地，由于独立正态随机变量之和仍是正态随机变量，故 $f_{S\mid N}(s \mid n) = N(0,\,9n)$，而 $f_S(s) = N(0,\,18)$。此外，由于 $E[N^2] = 5 \neq \bigl(E[N]\bigr)^2 = 4$，$N$ 必定能取多于一个的值，并不是恒等于 2 的退化随机变量。此时，$N$ 至少能以非零概率取到某个使 $\mathrm{var}(S \mid N) = 9N \neq \mathrm{var}(S) = 18$ 成立的值，从而 $f_{S\mid N}(s \mid n) \neq f_S(s)$。因此 $S$ 与 $N$ 不独立。

<!-- ===== PDF p5 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431　概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
