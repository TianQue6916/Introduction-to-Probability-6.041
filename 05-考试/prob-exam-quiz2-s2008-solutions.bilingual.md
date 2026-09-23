<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 2 解答（Quiz 2: Solutions）**</span> <span style="color:#7f8c8d;">（Spring 2008，2008 春季学期）</span>

<span style="color:#7f8c8d;">**6.041/6.431 Spring 2008　Quiz 2**　考试时间：4 月 16 日（星期三）晚 7:30–9:30。**SOLUTIONS（解答卷）**</span>

<span style="color:#7f8c8d;">姓名（Name）：________　复习课教师（Recitation Instructor）：________　助教（TA）：________</span>

**得分表（Score Table）**

| 题号（Question） | 小问（Part） | 得分（Score） | 满分（Out of） |
|:---:|:---:|:---:|:---:|
| 0 | — | | 3 |
| 1 | 全部（all） | | 36 |
| 2 | a | | 4 |
| 2 | b | | 5 |
| 2 | c | | 5 |
| 2 | d | | 8 |
| 2 | e | | 5 |
| 2 | f | | 6 |
| 3 | a | | 4 |
| 3 | b | | 6 |
| 3 | c | | 6 |
| 3 | d | | 6 |
| 3 | e | | 6 |
| **总分（Total）** | | | **100** |

**考试说明（6.041/6.431）：**

- 请把解答写在本试题册内；只有写在试题册内的解答才会被批改。
- 第一题为多项选择题（multiple choice），不给部分分；第二题与第三题会给部分分。
- 允许携带 2 张双面的 8.5×11 英寸公式纸，外加一台计算器。
- 考试时间为 120 分钟。
- 请书写工整！字迹无法辨认将不得分。
- 我们会在退课截止日（drop date）之前发出邮件，说明如何取回你的试卷。
- 祝你好运（Good Luck）！

<!-- ===== PDF p2 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Question 1（多项选择题）**</span>

多项选择题。请**清楚地圈出**下面每题的最佳答案。每题 4 分，不给部分分。

**a.** 设 $X_1, X_2, X_3$ 为相互独立、在 $[0,1]$ 上服从连续均匀分布（continuous uniform distribution）的随机变量。则 $P(X_1 < X_2 < X_3) =$

(i) $1/6$　　(ii) $1/3$　　(iii) $1/2$　　(iv) $1/4$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 为理解其中的原理，先考虑一个更简单的问题：只取如上的 $X_1$ 与 $X_2$。注意
>
> ```math
> P(X_1 < X_2) + P(X_2 < X_1) + P(X_1 = X_2) = 1,
> ```
>
> 因为相应的事件互不相交（disjoint）且穷尽了所有可能。但由对称性 $P(X_1 < X_2) = P(X_2 < X_1)$；又由于这些随机变量是连续型的，$P(X_1 = X_2) = 0$。因此 $P(X_1 < X_2) = 1/2$。
>
> 类似地，略去概率为零的事件、同时保证穷尽其余一切可能，可得
>
> ```math
> P(X_1<X_2<X_3) + P(X_1<X_3<X_2) + P(X_2<X_1<X_3) + P(X_2<X_3<X_1) + P(X_3<X_1<X_2) + P(X_3<X_2<X_1) = 1.
> ```
>
> 并且由对称性，这六个概率全部相等：
>
> ```math
> P(X_1 < X_2 < X_3) = P(X_1 < X_3 < X_2) = P(X_2 < X_1 < X_3) = P(X_2 < X_3 < X_1) = P(X_3 < X_1 < X_2) = P(X_3 < X_2 < X_1).
> ```
>
> 于是 $P(X_1 < X_2 < X_3) = 1/6$。
>
> <span style="color:#1e8449;">**[note]**</span> 原文 "exaust" 为 exhaust（穷尽）的笔误。

**b.** 设 $X$ 与 $Y$ 为两个连续随机变量。则

(i) $E[XY] = E[X]\,E[Y]$

(ii) $E[X^2 + Y^2] = E[X^2] + E[Y^2]$

(iii) $f_{X+Y}(x+y) = f_X(x)\,f_Y(y)$

(iv) $\mathrm{var}(X+Y) = \mathrm{var}(X) + \mathrm{var}(Y)$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 由于 $X^2$ 与 $Y^2$ 也是随机变量，由期望的线性（linearity of expectation）即得该结论。

**c.** 设 $X$ 在 $[0,4]$ 上均匀分布，$Y$ 在 $[0,1]$ 上均匀分布，并设 $X$ 与 $Y$ 独立。令 $Z = X + Y$。则

(i) $f_Z(4.5) = 0$　　(ii) $f_Z(4.5) = 1/8$　　(iii) $f_Z(4.5) = 1/4$　　(iv) $f_Z(4.5) = 1/2$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 由于 $X$ 与 $Y$ 独立，由卷积（convolution）即得：
>
> ```math
> f_Z(4.5) = \int_{-\infty}^{\infty} f_X(\alpha)\,f_Y(4.5 - \alpha)\,d\alpha = \int_{3.5}^{4} \frac{1}{4}\,d\alpha = \frac{1}{8}.
> ```

<!-- ===== PDF p3 ===== -->

**d.** 对 (c) 中定义的随机变量，$P(\max(X, Y) > 3)$ 等于

(i) $0$　　(ii) $9/4$　　(iii) $3/4$　　(iv) $1/4$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 注意
>
> ```math
> P(\max(X, Y) > 3) = 1 - P(\max(X, Y) \le 3) = 1 - P\bigl(\{X \le 3\} \cap \{Y \le 3\}\bigr).
> ```
>
> 而 $X$ 与 $Y$ 独立，所以
>
> ```math
> P\bigl(\{X \le 3\} \cap \{Y \le 3\}\bigr) = P(X \le 3)\,P(Y \le 3).
> ```
>
> 最后计算各概率：$P(X \le 3) = 3/4$，$P(Y \le 3) = 1$。于是
>
> ```math
> P(\max(X, Y) > 3) = 1 - 3/4 = 1/4.
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 原文此句写作 "$P(X \le 3) = 3/4$ and $P(X \le 3) = 1$"，第二个按题意应为 $P(Y \le 3) = 1$（$Y$ 在 $[0,1]$ 上均匀分布，必有 $Y \le 3$）。

**e.** 回忆课上讲过的帽子问题（hat problem）：聚会开始时 $N$ 个人把各自的帽子放进衣帽间，每顶帽子都可唯一识别。聚会结束时，每个人从衣帽间随机取一顶帽子。设 $N$ 是参数为 $\lambda$ 的泊松随机变量（Poisson random variable）。若 $X$ 是取回自己帽子的人数，则 $E[X]$ 等于

(i) $\lambda$　　(ii) $1/\lambda^2$　　(iii) $1/\lambda$　　(iv) $1$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 令 $X = X_1 + \ldots + X_N$，其中每个 $X_i$ 都是示性函数（indicator function）：若第 $i$ 个人取回自己的帽子则 $X_i = 1$，否则 $X_i = 0$。由期望的线性，
>
> ```math
> E[X \mid N = n] = E[X_1 \mid N = n] + \ldots + E[X_N \mid N = n].
> ```
>
> 而对所有 $i = 1, \ldots, n$，都有 $E[X_i \mid N = n] = 1/n$。于是
>
> ```math
> E[X \mid N = n] = n\,E[X_i \mid N = n] = 1.
> ```
>
> 最后，
>
> ```math
> E[X] = E\bigl[E[X \mid N = n]\bigr] = 1.
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 给定 $N = n$ 时，第 $i$ 个人取到自己的帽子是 $n$ 个等可能位置之一，故 $E[X_i \mid N = n] = 1/n$；$n$ 项相加恰好消去 $n$，结果与 $\lambda$ 无关。

**f.** 设 $X$ 与 $Y$ 分别是参数为 $\lambda_1$ 与 $\lambda_2$ 的泊松随机变量，且 $X$ 与 $Y$ 独立。定义 $W = X + Y$，则

(i) $W$ 服从参数为 $\min(\lambda_1, \lambda_2)$ 的泊松分布

(ii) $W$ 服从参数为 $\lambda_1 + \lambda_2$ 的泊松分布

(iii) $W$ 未必是泊松分布，但其均值等于 $\min(\lambda_1, \lambda_2)$

(iv) $W$ 未必是泊松分布，但其均值等于 $\lambda_1 + \lambda_2$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 最快的解法是借助变换（transform）：$M_X(s) = e^{\lambda_1(e^s - 1)}$，$M_Y(s) = e^{\lambda_2(e^s - 1)}$。由于 $X$ 与 $Y$ 独立，
>
> ```math
> M_W(s) = e^{\lambda_1(e^s - 1)}\,e^{\lambda_2(e^s - 1)} = e^{(\lambda_1 + \lambda_2)(e^s - 1)},
> ```
>
> 这正是均值为 $\lambda_1 + \lambda_2$ 的泊松随机变量的变换。

<!-- ===== PDF p4 ===== -->

**g.** 设随机变量 $X$ 的变换（transform）为 $M_X(s) = (0.4 + 0.6\,e^s)^{50}$。则

(i) $P(X = 0) = P(X = 50)$

(ii) $P(X = 51) > 0$

(iii) $P(X = 0) = (0.4)^{50}$

(iv) $P(X = 50) = 0.6$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 注意 $M_X(s)$ 是二项随机变量（binomial random variable）$X$ 的变换，其中试验次数 $n = 50$、成功概率 $p = 0.6$。于是
>
> ```math
> P(X = 0) = (0.4)^{50}.
> ```

**h.** 设 $X_i,\ i = 1, 2, \ldots$ 为独立随机变量，均服从 PDF $f_X(x) = x/8$（$0 \le x \le 4$）。令 $S = \frac{1}{100}\sum_{i=1}^{100} X_i$。则 $P(S > 3)$ 近似等于

(i) $1 - \Phi(5)$　　(ii) $\Phi(5)$　　(iii) $1 - \Phi\!\left(\dfrac{5}{\sqrt{2}}\right)$　　(iv) $\Phi\!\left(\dfrac{5}{\sqrt{2}}\right)$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 令 $S = \frac{1}{100}\sum_{i=1}^{100} Y_i$，其中 $Y_i$ 是由 $Y_i = X_i/100$ 给出的随机变量。由于各 $Y_i$ 独立同分布（iid），$S$ 的分布近似于以 $E[S]$ 为均值、$\mathrm{var}(S)$ 为方差的正态分布。于是
>
> ```math
> P(S > 3) = 1 - P(S \le 3) \approx 1 - \Phi\!\left(\frac{3 - E(S)}{\sqrt{\mathrm{var}(S)}}\right).
> ```
>
> 现在，
>
> ```math
> E[X_i] = \int_0^4 x\cdot\frac{x}{8}\,dx = \left.\frac{x^3}{24}\right|_0^4 = \frac{8}{3},
> ```
>
> ```math
> \mathrm{var}(X_i) = E[X_i^2] - \bigl(E[X_i]\bigr)^2 = \int_0^4 x^2\cdot\frac{x}{8}\,dx - \left(\frac{8}{3}\right)^2 = \left.\frac{x^4}{32}\right|_0^4 - \left(\frac{8}{3}\right)^2 = \frac{8}{9}.
> ```
>
> 因此，
>
> ```math
> E[S] = \frac{1}{100}\,E[X_i] + \ldots + \frac{1}{100}\,E[X_{100}] = 8/3,
> ```
>
> 且
>
> ```math
> \mathrm{var}(S) = \frac{1}{100^2}\,\mathrm{var}(X_i) + \ldots + \frac{1}{100^2}\,\mathrm{var}(X_i) = \frac{8}{9}\times\frac{1}{100}.
> ```
>
> 并且
>
> ```math
> P(S > 3) \approx 1 - \Phi\!\left(\frac{3 - 8/3}{\sqrt{\dfrac{8}{9}\times\dfrac{1}{100}}}\right) = 1 - \Phi\!\left(\frac{5}{\sqrt{2}}\right).
> ```

<!-- ===== PDF p5 ===== -->

**i.** 设 $X_i,\ i = 1, 2, \ldots$ 为独立随机变量，均服从 PDF $f_X(x) = 1$（$0 \le x \le 1$）。对某个整数 $n$，定义 $Y_n = X_1 X_2 X_3 \ldots X_n$。则 $\mathrm{var}(Y_n)$ 等于

(i) $\dfrac{n}{12}$　　(ii) $\dfrac{1}{3^n} - \dfrac{1}{4^n}$　　(iii) $\dfrac{1}{12^n}$　　(iv) $\dfrac{1}{12}$

> <span style="color:#2471a3;">**[solution]**</span>
>
> 由于 $X_1, \ldots, X_n$ 独立，故 $E[Y_n] = E[X_1] \times \ldots \times E[X_n]$；类似地，$E[Y_n^2] = E[X_1^2] \times \ldots \times E[X_n^2]$。由于对 $i = 1, \ldots, n$ 有 $E[X_i] = 1/2$、$E[X_i^2] = 1/3$，于是可得
>
> ```math
> \mathrm{var}(Y_n) = E[Y_n^2] - \bigl(E[Y_n]\bigr)^2 = \frac{1}{3^n} - \frac{1}{4^n}.
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 原文此处写作 "var(Sₙ)"，按上下文应为 $\mathrm{var}(Y_n)$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Question 2**</span>

每台 Mac book（Mac 笔记本电脑）的寿命（lifetime）都服从参数为 $\lambda$ 的指数分布（exponential distribution），各台 Mac book 的寿命相互独立。假设你有两台 Mac book，并同时开始使用。定义 $T_1$ 为第一台笔记本失效（failure）的时刻，$T_2$ 为第二台笔记本失效的时刻。

**a. 计算 $f_{T_1}(t_1)$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 设 $M_1$ 为 Mac book 1 的寿命，$M_2$ 为 Mac book 2 的寿命，$M_1$ 与 $M_2$ 是独立同分布（iid）的指数随机变量，其 CDF 为 $F_M(m) = 1 - e^{-\lambda m}$。$T_1$（第一台 Mac book 失效的时刻）是 $M_1$ 与 $M_2$ 的最小值。为推导 $T_1$ 的分布，我们先求 CDF $F_{T_1}(t)$，再求导得到 PDF $f_{T_1}(t)$。
>
> ```math
> \begin{aligned}
> F_{T_1}(t) &= P\bigl(\min(M_1, M_2) < t\bigr) \\
> &= 1 - P\bigl(\min(M_1, M_2) \ge t\bigr) \\
> &= 1 - P(M_1 \ge t)\,P(M_2 \ge t) \\
> &= 1 - \bigl(1 - F_M(t)\bigr)^2 \\
> &= 1 - e^{-2\lambda t}, \qquad t \ge 0.
> \end{aligned}
> ```
>
> 将 $F_{T_1}(t)$ 对 $t$ 求导得：
>
> ```math
> f_{T_1}(t) = 2\lambda e^{-2\lambda t}, \qquad t \ge 0.
> ```

<!-- ===== PDF p6 ===== -->

**b. 令 $X = T_2 - T_1$。计算 $f_{X\mid T_1}(x \mid t_1)$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 在给定第一台 Mac book 失效时刻的条件下，到另一台 Mac book 失效为止的时间由无记忆性（memoryless property）可知仍是指数随机变量。无记忆性告诉我们：无论该 Mac book 已经运转了多久，它距离失效的剩余时间都具有相同的指数 CDF。因此
>
> ```math
> f_{X\mid T_1}(x) = \lambda e^{-\lambda x}, \qquad x \ge 0.
> ```

**c. $X$ 与 $T_1$ 独立吗？请给出数学上的理由。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 由于我们已在 2(b) 中证明 $f_{X\mid T_1}(x \mid t)$ 与 $t$ 无关（原文误作 "2(c)"），所以 $X$ 与 $T_1$ 独立。

**d. 计算 $f_{T_2}(t_2)$ 与 $E[T_2]$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 第二台笔记本的失效时刻 $T_2$ 等于 $T_1 + X$。由于在 2(c) 中已证明 $X$ 与 $T_1$ 独立（原文误作 "2(b)"），我们将 2(a) 与 2(b) 中求得的密度作卷积来确定 $f_{T_2}(t)$：
>
> ```math
> \begin{aligned}
> f_{T_2}(t) &= \int_0^{\infty} f_{T_1}(\tau)\,f_X(t - \tau)\,d\tau
> = \int_0^{t} 2(\lambda)^2\,e^{-2\lambda\tau}\,e^{-\lambda(t-\tau)}\,d\tau \\
> &= 2\lambda e^{-\lambda t}\int_0^{t} \lambda e^{-\lambda\tau}\,d\tau
> = 2\lambda e^{-\lambda t}\bigl(1 - e^{-\lambda t}\bigr), \qquad t \ge 0.
> \end{aligned}
> ```
>
> 另外，由期望的线性，$E[T_2] = E[T_1] + E[X] = \dfrac{1}{2\lambda} + \dfrac{1}{\lambda} = \dfrac{3}{2\lambda}$。
>
> 解本题的另一个等价方法是：注意到 $T_2$ 是 $M_1$ 与 $M_2$ 的最大值，并按我们标准的"由 CDF 到 PDF"的方法推导 $T_2$ 的分布：
>
> ```math
> \begin{aligned}
> F_{T_2}(t) &= P\bigl(\max(M_1, M_2) < t\bigr) = P(M_1 \le t)\,P(M_2 \le t) = F_M(t)^2 \\
> &= \bigl(1 - e^{-\lambda t}\bigr)^2 = 1 - 2e^{-\lambda t} + e^{-2\lambda t}, \qquad t \ge 0.
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 原文此行写作 "$P(M_2 \le t)\,P(M_2 \le t)$"，应为 $P(M_1 \le t)\,P(M_2 \le t)$。
>
> 将 $F_{T_2}(t)$ 对 $t$ 求导得：
>
> ```math
> f_{T_2}(t) = 2\lambda e^{-\lambda t} - 2\lambda e^{-2\lambda t}, \qquad t \ge 0,
> ```
>
> 与上面用卷积得到的结果一致。最后，由该密度可得 $E[T_2] = \dfrac{2}{\lambda} - \dfrac{1}{2\lambda} = \dfrac{3}{2\lambda}$，与先前的解答相符。

<!-- ===== PDF p7 ===== -->

**e. 现在假设你有 100 台 Mac book，令 $Y$ 为第一台笔记本失效的时刻。求 $P(Y < 0.01)$ 的最佳答案。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> $Y$ 等于 100 个独立指数随机变量的最小值。仿照 (a) 中的推导，类推可得
>
> ```math
> f_Y(y) = 100\lambda e^{-100\lambda y}, \qquad y \ge 0
> ```
>
> <span style="color:#7f8c8d;">（原文此处条件误作 "$t \ge 0$"。）</span>。把 $y$ 从 0 到 0.01 积分，得
>
> ```math
> P(Y < 0.01) = 1 - e^{-\lambda}.
> ```

你的朋友 Charlie 对 Mac book 爱不释手，他每天都要买 $S$ 台新 Mac book！任意给定的一天，$S$ 等可能地取 4 或 8，且各天相互独立。令 $S_{100}$ 为 Charlie 在接下来 100 天内购买的 Mac book 总数。

**f.（6 分）求 $P(S_{100} \le 608)$ 的最佳近似，最终答案用标准正态分布的 CDF $\Phi(\cdot)$ 表示。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 使用二项分布的 De Moivre–Laplace 近似（De Moivre–Laplace Approximation），并注意 $S$ 可取值之间的步长（step size）为 4：
>
> ```math
> P(S_{100} \le 608) = \Phi\!\left(\frac{608 + 2 - 100 \times 6}{\sqrt{100 \times 4}}\right) = \Phi\!\left(\frac{10}{20}\right) = \Phi(0.5).
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 每天 $S$ 等可能取 4 或 8，故 $E[S] = 6$、$\mathrm{var}(S) = \frac{(8-4)^2}{4} = 4$，从而 $E[S_{100}] = 100 \times 6$、$\mathrm{var}(S_{100}) = 100 \times 4$；修正项 $+2$ 是半个步长（连续性修正，continuity correction）。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Question 3**</span>

Saif 是一个心怀善意但略显优柔寡断的家伙。每天早上他都抛一枚硬币来决定去哪里：若是正面，他就开车去商场（mall）；若出现反面，他就到当地收容所（shelter）做志愿者。Saif 的硬币不一定公平，其正面概率等于 $q$。我们并不知道 $q$，但知道它可以很好地用一个随机变量 $Q$ 来刻画，$Q$ 的密度为

```math
f_Q(q) = \begin{cases} 2q, & \text{若 } 0 \le q \le 1, \\[4pt] 0, & \text{其他情形.} \end{cases}
```

假设在给定 $Q$ 的条件下各次抛硬币相互独立。注意：a、b、c 与 {d, e} 各部分可以相互独立地作答。

<!-- ===== PDF p8 ===== -->

**a.（4 分）若 Saif 只抛一次硬币，他去当地收容所的概率是多少？**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 令 $X_i$ 为第 $i$ 次抛掷的结果：硬币落在"正面"时 $X_i = 1$，落在"反面"时 $X_i = 0$。由全概率定理（total probability theorem）：
>
> ```math
> P(X_1 = 0) = \int_0^1 P(X_1 = 0 \mid Q = q)\,f(q)\,dq = \int_0^1 (1 - q)\,2q\,dq = \frac{1}{3}.
> ```

为了鼓励向善，Saif 的父亲提出：他每天去当地收容所做志愿者，就付给他 4 美元。定义 $X$ 为 Saif 在接下来 30 天里每天早上都抛硬币的情况下的报酬。

**b. 求 $\mathrm{var}(X)$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 令 $Y_i$ 为描述第 $i$ 天早上抛硬币结果的伯努利随机变量（Bernoulli random variable）。$Y_i = 1$ 对应事件"第 $i$ 天早上 Saif 去当地收容所"；$Y_i = 0$ 对应事件"第 $i$ 天早上 Saif 去商场"。假设硬币以概率 $q$ 落在正面，即给定 $Q = q$，则对 $i = 1, \ldots, 30$ 有 $P(Y_i = 1) = q$、$P(Y_i = 0) = 1 - q$。
>
> <span style="color:#1e8449;">**[note]**</span> 按题意（正面去商场、反面去收容所），给定 $Q = q$ 时应为 $P(Y_i = 1 \mid Q = q) = 1 - q$；原文此处写作 $P(Y_i = 1) = q$。由对称性 $\mathrm{var}(1 - Q) = \mathrm{var}(Q)$ 且 $E[Q(1 - Q)]$ 不变，后续计算与最终结果 880 不受影响。
>
> Saif 接下来 30 天的报酬由随机变量 $X = 4(Y_1 + Y_2 + \cdots + Y_{30})$ 描述。
>
> ```math
> \mathrm{var}(X) = 16\,\mathrm{var}(Y_1 + Y_2 + \cdots + Y_{30})
> ```
>
> ```math
> = 16\left[\mathrm{var}\bigl(E[Y_1 + Y_2 + \cdots + Y_{30} \mid Q]\bigr) + E\bigl[\mathrm{var}(Y_1 + Y_2 + \cdots + Y_{30} \mid Q)\bigr]\right].
> ```
>
> 注意，在给定 $Q = q$ 的条件下 $Y_1, \ldots, Y_{30}$ 相互独立。因此 $\mathrm{var}(Y_1 + Y_2 + \cdots + Y_{30} \mid Q) = \mathrm{var}(Y_1 \mid Q) + \ldots + \mathrm{var}(Y_{30} \mid Q)$。于是
>
> ```math
> \begin{aligned}
> \mathrm{var}(X) &= 16\,\mathrm{var}(30Q) + 16\,E\bigl[\mathrm{var}(Y_1 \mid Q) + \ldots + \mathrm{var}(Y_{30} \mid Q)\bigr] \\
> &= 16 \times 30^2\,\mathrm{var}(Q) + 16 \times 30\,E[Q(1 - Q)] \\
> &= 16 \times 30^2\left(E[Q^2] - \bigl(E[Q]\bigr)^2\right) + 16 \times 30\left(E[Q] - E[Q^2]\right) \\
> &= 16 \times 30^2\left(\frac{1}{2} - \frac{4}{9}\right) + 16 \times 30\left(\frac{2}{3} - \frac{1}{2}\right) = 880,
> \end{aligned}
> ```
>
> 其中 $E[Q] = \displaystyle\int_0^1 2q^2\,dq = \frac{2}{3}$，$E[Q^2] = \displaystyle\int_0^1 2q^3\,dq = \frac{1}{2}$。

<!-- ===== PDF p9 ===== -->

设事件 $B$ 为"Saif 在 $k$ 天内至少去一次当地收容所"。

**c. 求给定 $B$ 的条件下 $Q$ 的条件密度 $f_{Q\mid B}(q)$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 由贝叶斯法则（Bayes' Rule）：
>
> ```math
> f_{Q\mid B}(q) = \frac{P(B \mid Q = q)\,f_Q(q)}{\displaystyle\int_0^1 P(B \mid Q = q)\,f_Q(q)\,dq} = \frac{(1 - q^k)\,2q}{\displaystyle\int_0^1 (1 - q^k)\,2q\,dq} = \frac{2q(1 - q^k)}{1 - 2/(k + 2)}, \qquad 0 \le q \le 1.
> ```

在商场购物时，Saif 接到妹妹 Mais 的电话。两人约定下午 1:30 整在 Coco Cabana 庭院（Coco Cabana Court yard）碰面。不巧，Mais 迟到了 $Z$ 分钟，$Z$ 是从 0 到 10 分钟的连续均匀随机变量。Saif 对 Mais 让他干等怒不可遏，要求 Mais 付给他 $R$ 美元，其中 $R = \exp(Z + 2)$。

**e. 求 Saif 的期望报酬 $E[R]$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> E[R] = \int_0^{10} e^{z+2}\,f(z)\,dz = \frac{e^2}{10}\int_0^{10} e^z\,dz = \frac{e^{12} - e^2}{10}.
> ```

**f. 求 Saif 报酬的密度 $f_R(r)$。**

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> F_R(r) = P\bigl(e^{Z+2} \le r\bigr) = P\bigl(Z + 2 \le \ln(r)\bigr) = \int_0^{\ln(r) - 2} \frac{1}{10}\,dz = \frac{\ln(r) - 2}{10}, \qquad e^2 \le r \le e^{12},
> ```
>
> ```math
> f_R(r) = \frac{1}{10\,r}, \qquad e^2 \le r \le e^{12}.
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 原文第三题的小问标号为 a、b、c、e、f；按封面得分表（Question 3 为 a–e 共五小问）及题干说明"parts a, b, c, and {d, e}"，这两问应对应 d、e，此处照原文保留标号。

<!-- ===== PDF p10 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431　概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability）</span>

<span style="color:#7f8c8d;">（此尾页为 MIT OpenCourseWare 的出版信息页，页面上标注的学期为 Fall 2010，系 OCW 出版信息，与试卷本身的 Spring 2008 学期标注不同。）</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
