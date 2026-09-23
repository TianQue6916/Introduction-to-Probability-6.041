<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Final Exam 解答（Final Exam Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）｜考试时间：2010 年 12 月 15 日（星期三）上午 9:00 – 中午 12:00。</span>

---

### <span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b">**Problem 1（32 分）**</span>

考虑马尔可夫链（Markov chain）$\{X_n;\ n = 0, 1, \ldots\}$，由下面的状态转移图（transition diagram）确定。

<span style="color:#7f8c8d;">【图】原页此处为马尔可夫链状态转移图：状态 $1,2,3$；自环 $p_{11}=0.6$、$p_{22}=0.5$、$p_{33}=0.9$；$1\to 2$ 标 $0.4$，$2\to 1$ 标 $0.2$，$2\to 3$ 标 $0.3$，$3\to 2$ 标 $0.1$；不存在 $1\leftrightarrow 3$ 之间的转移。上述转移概率由本题各小问的解答反推，并与 $\pi=(1/9,\,2/9,\,6/9)$、$r_{12}(2)=0.44$、$t_1^\ast=9$ 逐一验证一致。原图由后处理统一插入。</span>

**1.（4 分）** 已知链从 $X_0 = 1$ 出发，求 $X_2 = 2$ 的概率。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 两步转移概率（two-step transition probability）为
>
> ```math
> r_{12}(2) = p_{11}\cdot p_{12} + p_{12}\cdot p_{22} = 0.6 \cdot 0.4 + 0.4 \cdot 0.5 = 0.44.
> ```

**2.（4 分）** 求各状态的稳态概率（steady-state probabilities）$\pi_1, \pi_2, \pi_3$。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 按如下方式列出生灭过程（birth-death process）的平衡方程（balance equations）与归一化方程（normalization equation）：
>
> ```math
> \pi_1 p_{12} = \pi_2 p_{21}, \qquad \pi_2 p_{23} = \pi_3 p_{32}, \qquad \pi_1 + \pi_2 + \pi_3 = 1.
> ```
>
> 解此方程组，得到如下稳态概率：
>
> ```math
> \pi_1 = \frac{1}{9}, \qquad \pi_2 = \frac{2}{9}, \qquad \pi_3 = \frac{6}{9}.
> ```
>
> 即使第 2 小问没有做对，本题后续所有小问也都可以只使用符号 $\pi_i$ 作答，不必代入具体数值。
>
> > <span style="color:#1e8449;">**[mathtip]**</span> <span style="color:#1e8449;">**Tip（提示）：** 对生灭过程（birth-death process），稳态分布满足局部平衡方程（local balance equations）$\pi_i p_{ij} = \pi_j p_{ji}$（只在相邻状态之间成立）。把它们与归一化条件 $\sum_i \pi_i = 1$ 联立即可逐个解出 $\pi_i$，无须求解完整的全局方程 $\pi = \pi P$。本题中 $\pi_2/\pi_1 = p_{12}/p_{21} = 0.4/0.2 = 2$，$\pi_3/\pi_2 = p_{23}/p_{32} = 0.3/0.1 = 3$，故比例为 $1:2:6$，再由归一化立即得 $(1/9,\,2/9,\,6/9)$。</span>

**3.（4 分）** 令 $Y_n = X_n - X_{n-1}$：$Y_n = 1$ 表示第 $n$ 次转移是向右转移，$Y_n = 0$ 表示自转移（self-transition，即停留在原状态），$Y_n = -1$ 表示向左转移。求 $\lim_{n\to\infty} P(Y_n = 1)$。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 利用全概率定理（total probability theorem）与稳态概率，
>
> ```math
> \lim_{n\to\infty} P(Y_n = 1) = \sum_{i=1}^{3} \pi_i \cdot P(Y_n = 1 \mid X_{n-1} = i) = \pi_1 p_{12} + \pi_2 p_{23} = \frac{1}{9}.
> ```

<!-- ===== PDF p2 ===== -->

**4.（4 分）** 序列 $Y_n$ 是马尔可夫链吗？请说明理由。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 不是。设马尔可夫过程已处于稳态。要满足马尔可夫性质（Markov property），应成立
>
> ```math
> P(Y_n = 1 \mid Y_{n-1} = 1,\, Y_{n-2} = 1) = P(Y_n = 1 \mid Y_{n-1} = 1).
> ```
>
> 当 $n$ 较大时，
>
> ```math
> P(Y_n = 1 \mid Y_{n-1} = 1,\, Y_{n-2} = 1) = 0,
> ```
>
> 因为不可能连续向右移动 3 次。然而在稳态下，
>
> ```math
> P(Y_n = 1 \mid Y_{n-1} = 1) = \frac{P(\{Y_n = 1\} \cap \{Y_{n-1} = 1\})}{P(Y_{n-1} = 1)} = \frac{\pi_1 p_{12} p_{23}}{\pi_1 p_{12} + \pi_2 p_{23}} = 0.12 \neq 0.
> ```
>
> 因此，序列 $Y_n$ 不是马尔可夫链。
>
> > <span style="color:#1e8449;">**[note]**</span> <span style="color:#1e8449;">**Note（提取校验）：** 原文提取文本中此行只显示"＝ 0"。代入 $\pi_1 = 1/9$、$p_{12} = 0.4$、$p_{23} = 0.3$、$\pi_2 = 2/9$ 验证：$\pi_1 p_{12} p_{23} = 1/75$，$\pi_1 p_{12} + \pi_2 p_{23} = 1/9$，比值恰为 $9/75 = 0.12$。该比值非零正是"因此 $Y_n$ 不是马尔可夫链"这一结论成立的前提，故按 $0.12 \neq 0$ 还原。</span>

**5.（4 分）** 已知第 $n$ 次转移是向右转移（$Y_n = 1$），求前一个状态为状态 1 的概率。（可以设 $n$ 很大。）

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 由贝叶斯法则（Bayes' rule），
>
> ```math
> P(X_{n-1} = 1 \mid Y_n = 1) = \frac{P(X_{n-1} = 1)\,P(Y_n = 1 \mid X_{n-1} = 1)}{\displaystyle\sum_{i=1}^{3} P(X_{n-1} = i)\,P(Y_n = 1 \mid X_{n-1} = i)} = \frac{\pi_1 p_{12}}{\pi_1 p_{12} + \pi_2 p_{23}} = \frac{2}{5}.
> ```

**6.（4 分）** 设 $X_0 = 1$。令 $T$ 为状态重新等于 1 的首个正时刻。说明如何求 $E[T]$。（只需写出需要求解的方程即可；无须实际求解，也不必给出数值答案。）

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 为求状态 1 的平均重返时间（mean recurrence time），先通过求解下列方程组算出到达状态 1 的平均首达时间（mean first passage times）：
>
> ```math
> t_2 = 1 + p_{22} t_2 + p_{23} t_3, \qquad t_3 = 1 + p_{32} t_2 + p_{33} t_3.
> ```
>
> 状态 1 的平均重返时间即为 $t_1^\ast = 1 + p_{12} t_2$。解方程组得 $t_2 = 20$、$t_3 = 30$，从而 $t_1^\ast = 9$。
>
> > <span style="color:#1e8449;">**[mathtip]**</span> <span style="color:#1e8449;">**Tip（提示）：** 对正常返（positive recurrent）的马尔可夫链，状态 $i$ 的平均重返时间满足 $t_i^\ast = 1/\pi_i$。此处 $1/\pi_1 = 9$，与解得的 $t_1^\ast = 1 + p_{12} t_2 = 1 + 0.4 \times 20 = 9$ 完全一致，可作为快速校验。直观原因：稳态下链长期停在状态 1 的时间占比是 $\pi_1$，故平均每 $1/\pi_1$ 步回到 1 一次。</span>

**7.（4 分）** 序列 $X_1, X_2, X_3, \ldots$ 依概率收敛（converge in probability）吗？若收敛，收敛到什么？若不收敛，只需回答"否"，无须解释。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 否。

<!-- ===== PDF p3 ===== -->

**8.（4 分）** 令 $Z_n = \max\{X_1, \ldots, X_n\}$。序列 $Z_1, Z_2, Z_3, \ldots$ 依概率收敛吗？若收敛，收敛到什么？若不收敛，只需回答"否"，无须解释。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 是。该序列依概率收敛到 3。
>
> 对原马尔可夫链而言，状态 $\{1, 2, 3\}$ 构成单一的常返类（recurrent class）。因此，该马尔可夫过程最终必以概率 1 访问每个状态。此时，一旦 $X_n$ 首次访问状态 3，序列 $Z_n$ 便会以概率 1 收敛到 3。

---

### <span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b">**Problem 2（68 分）**</span>

Alice 在时刻零来到一间 Athena 机房（Athena cluster），此后把全部时间用于打字写邮件。她发出各封邮件的时刻构成一个速率为每小时 $\lambda_A$ 的泊松过程（Poisson process）。

**1.（3 分）** Alice 在时间区间 $[1, 2]$ 内恰好发出三封邮件的概率是多少？

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** Alice 在区间 $[1, 2]$ 内发出的邮件数是参数为 $\lambda_A$ 的泊松随机变量（Poisson random variable）。于是（记号 $P(3,1)$ 表示长度为 1 的区间内恰有 3 个到达的泊松概率）：
>
> ```math
> P(3, 1) = \frac{\lambda_A^3 e^{-\lambda_A}}{3!}.
> ```

**2.** 令 $Y_1$ 与 $Y_2$ 为 Alice 第一封与第二封邮件发出的时刻。

**（a）（3 分）** 求 $E[Y_2 \mid Y_1]$。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 记 $T_2$ 为 Alice 泊松过程的第二个到达间隔（inter-arrival time）。则
>
> ```math
> Y_2 = Y_1 + T_2, \qquad E[Y_2 \mid Y_1] = E[Y_1 + T_2 \mid Y_1] = Y_1 + E[T_2] = Y_1 + \frac{1}{\lambda_A}.
> ```

**（b）（3 分）** 求 $Y_1^2$ 的 PDF（概率密度函数）。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 令 $Z = Y_1^2$。先求 $Z$ 的 CDF（累积分布函数），再求导得到 $Z$ 的 PDF：
>
> ```math
> F_Z(z) = P(Y_1^2 \le z) = P(-\sqrt{z} \le Y_1 \le \sqrt{z}) =
> \begin{cases}
> 1 - e^{-\lambda_A \sqrt{z}}, & z \ge 0, \\
> 0, & z < 0.
> \end{cases}
> ```
>
> ```math
> f_Z(z) = \frac{dF_Z(z)}{dz} = \lambda_A e^{-\lambda_A \sqrt{z}} \cdot \frac{1}{2}\, z^{-1/2} \quad (z \ge 0),
> \qquad
> f_Z(z) =
> \begin{cases}
> \dfrac{\lambda_A}{2}\, z^{-1/2} e^{-\lambda_A \sqrt{z}}, & z \ge 0, \\
> 0, & z < 0.
> \end{cases}
> ```

**（c）（3 分）** 求 $Y_1$ 与 $Y_2$ 的联合 PDF（joint PDF）。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：**
>
> ```math
> f_{Y_1, Y_2}(y_1, y_2) = f_{Y_1}(y_1)\, f_{Y_2 \mid Y_1}(y_2 \mid y_1) = f_{Y_1}(y_1)\, f_{T_2}(y_2 - y_1) = \lambda_A e^{-\lambda_A y_1}\, \lambda_A e^{-\lambda_A (y_2 - y_1)},
> ```
>
> 即（otherwise 指其他情形，取值为 0）：
>
> ```math
> f_{Y_1, Y_2}(y_1, y_2) =
> \begin{cases}
> \lambda_A^2 e^{-\lambda_A y_2}, & y_2 \ge y_1 \ge 0, \\
> 0, & \text{otherwise}.
> \end{cases}
> ```

<span style="color:#7f8c8d;">（页脚注）\* Athena 是 MIT 基于 UNIX 的计算环境，OCW 不提供对其的访问权限。</span>

<!-- ===== PDF p4 ===== -->

**3.** 你在时刻 1 到达，并被告知 Alice 迄今恰好发出了一封邮件。（本小问只需给出答案，无须论证。）

**（a）（3 分）** 在此信息下，$Y_2$ 的条件期望（conditional expectation）是多少？

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 设 $A$ 为事件"$[0,1]$ 内恰有一个到达"。从时刻 $t = 1$ 向后看，距下一次到达的时间就是一个指数随机变量（exponential random variable）$T$。于是
>
> ```math
> E[Y_2 \mid A] = 1 + E[T] = 1 + \frac{1}{\lambda_A}.
> ```

**（b）（3 分）** 在此信息下，$Y_1$ 的条件期望是多少？

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 给定 $A$，这次到达的时刻 $Y_1$ 在区间 $[0,1]$ 内取各个值是等可能的（均匀分布）。因此
>
> ```math
> E[Y_1 \mid A] = \frac{1}{2}.
> ```

**4.** Bob 刚结束锻炼（期间无法使用电子邮件），在时刻 1 坐到 Alice 旁边。他从时刻 1 开始打字写邮件，并按一个独立的、速率为 $\lambda_B$ 的泊松过程把邮件发出。

**（a）（5 分）** 两人在区间 $[0, 2]$ 内共同发出的邮件总数之 PMF（概率质量函数）是什么？

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 设 $K$ 为 $[0, 2]$ 内发出的邮件总数，$K_1$ 为 $[0, 1)$ 内发出的邮件数，$K_2$ 为 $[1, 2]$ 内发出的邮件数，则 $K = K_1 + K_2$，其中 $K_1$ 是参数为 $\lambda_A$ 的泊松随机变量，$K_2$ 是参数为 $\lambda_A + \lambda_B$ 的泊松随机变量（因为 $t = 1$ 之后 Alice 与 Bob 发出的邮件，按两者的泊松过程合并而成的合并泊松过程（merged Poisson process）到达）。由于 $K$ 是独立泊松随机变量之和，故 $K$ 是参数为 $2\lambda_A + \lambda_B$ 的泊松随机变量，即 $K$ 服从如下分布：
>
> ```math
> p_K(k) = \frac{(2\lambda_A + \lambda_B)^k e^{-(2\lambda_A + \lambda_B)}}{k!}, \qquad k = 0, 1, \ldots
> ```

**（b）（5 分）** Bob 出现的时刻，Alice 正在打的那封邮件与之相关的"总打字时间"期望值是多少？（这里"总打字时间"包含 Alice 在 Bob 到达之前与之后花在这封邮件上的时间。）

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** Bob 出现时刻 Alice 正在打的那封邮件所对应的总打字时间 $Q$，等于 $S_0$（从 Alice 的上一封邮件或时刻 0——取较晚者——到时刻 1 之间的时长）与 $T_1$（从时刻 1 到 Alice 发出当前这封邮件之时之间的时长）之和。$T_1$ 服从参数为 $\lambda_A$ 的指数分布，而 $S_0 = \min\{T_0, 1\}$，其中 $T_0$ 服从参数为 $\lambda_A$ 的指数分布。
>
> 于是
>
> ```math
> Q = S_0 + T_1 = \min\{T_0, 1\} + T_1
> ```
>
> 且
>
> ```math
> E[Q] = E[S_0] + E[T_1].
> ```
>
> 我们有：$E[T_1] = 1/\lambda_A$。

<!-- ===== PDF p5 ===== -->

**（续）**

> 利用全期望定律（law of total expectations）可求 $E[S_0]$：
>
> ```math
> \begin{aligned}
> E[S_0] &= E[\min\{T_0, 1\}] \\
> &= P(T_0 \le 1)\, E[T_0 \mid T_0 \le 1] + P(T_0 > 1)\, E[1 \mid T_0 > 1] \\
> &= (1 - e^{-\lambda_A}) \int_0^1 t\, f_{T_0 \mid T_0 \le 1}(t)\, dt + e^{-\lambda_A} \\
> &= (1 - e^{-\lambda_A}) \int_0^1 t\, \frac{\lambda_A e^{-\lambda_A t}}{1 - e^{-\lambda_A}}\, dt + e^{-\lambda_A} \\
> &= \int_0^1 t\, \lambda_A e^{-\lambda_A t}\, dt + e^{-\lambda_A} \\
> &= \frac{1}{\lambda_A} \int_0^1 t\, \lambda_A^2 e^{-\lambda_A t}\, dt + e^{-\lambda_A} \\
> &= \frac{1}{\lambda_A}\left(1 - e^{-\lambda_A} - \lambda_A e^{-\lambda_A}\right) + e^{-\lambda_A} \\
> &= \frac{1}{\lambda_A}\left(1 - e^{-\lambda_A}\right).
> \end{aligned}
> ```
>
> 其中上述积分是这样求出的：把被积函数凑成一个二阶 Erlang PDF（Erlang order-2 PDF，即两个独立同指数到达间隔之和的密度），并把该 PDF 从 0 到 1 的积分等同于"第一小时内有两个或更多到达"的概率（即 $P(Y_2 < 1) = 1 - P(0, 1) - P(1, 1)$，其中 $P(0,1)$、$P(1,1)$ 分别是长度为 1 的区间内恰有 0 个、1 个到达的泊松概率）。另外，用分部积分（integration by parts）也能得到同样的结果。
>
> 合并上面的期望：
>
> ```math
> E[Q] = E[S_0] + E[T_1] = \frac{1}{\lambda_A}\left(1 - e^{-\lambda_A}\right) + \frac{1}{\lambda_A} = \frac{1}{\lambda_A}\left(2 - e^{-\lambda_A}\right).
> ```
>
> > <span style="color:#1e8449;">**[mathtip]**</span> <span style="color:#1e8449;">**Tip（提示）：** $S_0 = \min\{T_0, 1\}$（$T_0 \sim \mathrm{Exp}(\lambda_A)$）这一步的合法性：时刻 1 处这封邮件"已经打了的时长"（age）$S_0$ 满足 $P(S_0 \ge s) = P([1-s, 1]$ 内无到达$) = e^{-\lambda_A s}$（$0 \le s \le 1$），而 $\min\{T_0, 1\} \ge s$（$s \le 1$）的概率恰为 $P(T_0 \ge s) = e^{-\lambda_A s}$，二者分布相同，故期望相等。这其实是泊松过程"无记忆性"在回看方向上的体现。</span>

**（c）（5 分）** 直到两人各至少发出一封邮件为止所需时间的期望值是多少？（注意时间从时刻 0 起算，并且要把 Alice 在区间 $[0, 1]$ 内可能已发出的邮件计入。）

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 定义 $U$ 为从 $t = 0$ 起直到两人各自都至少发出一封邮件为止的时间。定义 $V$ 为从 Bob 到达（时刻 1）起直到两人各自都至少发出一封邮件为止的剩余时间（故 $V = U - 1$）。
>
> 定义 $S$ 为时刻 1 之后 Bob 发出第一封邮件所需的时间。
>
> 定义事件 $A = \{$Alice 在区间 $[0, 1]$ 内发出一封或多封邮件$\} = \{Y_1 \le 1\}$，其中 $Y_1$ 是 Alice 发出第一封邮件的时刻。
>
> 定义事件 $B = \{$时刻 1 之后，Bob 的下一封邮件先于 Alice 发出$\}$，这等价于：从时刻 1 起，由 Alice 与 Bob 各自原始过程合并而成的合并泊松过程中，下一个到达来自 Bob 的过程。
>
> 我们有：
>
> ```math
> P(A) = P(Y_1 \le 1) = 1 - e^{-\lambda_A}, \qquad P(B) = \frac{\lambda_B}{\lambda_A + \lambda_B}.
> ```

<!-- ===== PDF p6 ===== -->

**（续）**

> 于是
>
> ```math
> \begin{aligned}
> E[U] &= P(A)\, E[U \mid A] + P(A^c)\, E[U \mid A^c] \\
> &= (1 - e^{-\lambda_A})(1 + E[V \mid A]) + e^{-\lambda_A}(1 + E[V \mid A^c]) \\
> &= (1 - e^{-\lambda_A})(1 + E[V \mid A]) + e^{-\lambda_A}\big(1 + P(B \mid A^c)\, E[V \mid B \cap A^c] + P(B^c \mid A^c)\, E[V \mid B^c \cap A^c]\big) \\
> &= (1 - e^{-\lambda_A})(1 + E[V \mid A]) + e^{-\lambda_A}\big(1 + P(B)\, E[V \mid B \cap A^c] + P(B^c)\, E[V \mid B^c \cap A^c]\big) \\
> &= (1 - e^{-\lambda_A})(1 + E[V \mid A]) + e^{-\lambda_A}\Big(1 + \frac{\lambda_B}{\lambda_A + \lambda_B}\, E[V \mid B \cap A^c] + \frac{\lambda_A}{\lambda_A + \lambda_B}\, E[V \mid B^c \cap A^c]\Big).
> \end{aligned}
> ```
>
> 注意：$E[V \mid B^c \cap A^c]$ 是"时刻 1 之后直到两人各发出一封邮件"的期望时间（因为给定 $A^c$，Alice 在 $[0, 1]$ 内一封也未发出），且此时是 Alice 的邮件先于 Bob 发出。于是它等于：合并过程中出现一次到达的期望时间，加上随后 Bob 过程中出现一次到达的期望时间。所以
>
> ```math
> E[V \mid B^c \cap A^c] = \frac{1}{\lambda_A + \lambda_B} + \frac{1}{\lambda_B}.
> ```
>
> 类似地，$E[V \mid B \cap A^c]$ 是给定 Bob 先于 Alice 发出邮件时，时刻 1 之后直到两人各发出一封邮件的时间。所以
>
> ```math
> E[V \mid B \cap A^c] = \frac{1}{\lambda_A + \lambda_B} + \frac{1}{\lambda_A}.
> ```
>
> 另外，$E[V \mid A]$ 是时刻 1 之后 Bob 发出第一封邮件所需的期望时间（因为给定 $A$，Alice 已在 $[0, 1]$ 内发出过邮件）。所以 $E[V \mid A] = E[S] = 1/\lambda_B$。
>
> 把以上结果全部代入前式，得：
>
> ```math
> E[U] = (1 - e^{-\lambda_A})\left(1 + \frac{1}{\lambda_B}\right) + e^{-\lambda_A}\left[1 + \frac{\lambda_B}{\lambda_A + \lambda_B}\left(\frac{1}{\lambda_A + \lambda_B} + \frac{1}{\lambda_A}\right) + \frac{\lambda_A}{\lambda_A + \lambda_B}\left(\frac{1}{\lambda_A + \lambda_B} + \frac{1}{\lambda_B}\right)\right].
> ```

**（d）（5 分）** 已知区间 $[0, 2]$ 内共发出 10 封邮件，问其中恰有 4 封由 Alice 发出的概率是多少？

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：**
>
> ```math
> \begin{aligned}
> &P(\text{Alice sent 4 in } [0,2] \mid \text{total 10 sent in } [0,2]) \\
> &= \frac{P(\text{Alice sent 4 in } [0,2] \cap \text{total 10 sent in } [0,2])}{P(\text{total 10 sent in } [0,2])}
> = \frac{P(\text{Alice sent 4 in } [0,2] \cap \text{Bob sent 6 in } [0,2])}{P(\text{total 10 sent in } [0,2])} \\
> &= \frac{\dfrac{(2\lambda_A)^4 e^{-2\lambda_A}}{4!} \cdot \dfrac{(\lambda_B)^6 e^{-\lambda_B}}{6!}}{\dfrac{(2\lambda_A + \lambda_B)^{10} e^{-(2\lambda_A + \lambda_B)}}{10!}}
> = \binom{10}{4}\left(\frac{2\lambda_A}{2\lambda_A + \lambda_B}\right)^{4}\left(\frac{\lambda_B}{2\lambda_A + \lambda_B}\right)^{6}.
> \end{aligned}
> ```
>
> 正如答案的形状所提示的，本题也可以换一种解法：先计算"已知某封邮件是在 $[0, 2]$ 内发出的，它由 Alice 发出"的概率。做法是：把 Alice 在 $[0, 2]$ 内发出的邮件数，看成"速率为两倍（$2\lambda_A$）的泊松过程在时长减半的区间（具体取区间 $[1, 2]$）内的到达数"，再把该过程与 Bob 的过程合并。于是，"$[0, 2]$ 内发出的某封邮件来自 Alice"的概率，就是这个新合并过程中的到达来自新构造的 $2\lambda_A$ 速率过程的概率：

<!-- ===== PDF p7 ===== -->

**（续）**

> ```math
> p = \frac{2\lambda_A}{2\lambda_A + \lambda_B}.
> ```
>
> 然后，10 封邮件中恰有 4 封来自 Alice 的概率，就是"10 次试验中成功 4 次"的二项概率（binomial probability），与上面的解法结果一致。

**5.（5 分）** 设 $\lambda_A = 4$。用切比雪夫不等式（Chebyshev's inequality）求"Alice 在区间 $[0, 1]$ 内发出至少 5 封邮件"的概率的上界。马尔可夫不等式（Markov inequality）会给出更好的界吗？

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：**
>
> 设 $N$ 为 Alice 在 $[0, 1]$ 内发出的邮件数。由于 $N$ 是参数为 $\lambda_A$ 的泊松随机变量，
>
> ```math
> E[N] = \mathrm{var}(N) = \lambda_A = 4.
> ```
>
> 为应用切比雪夫不等式，注意到：
>
> ```math
> P(N \ge 5) = P(N - 4 \ge 1) \le P(|N - 4| \ge 1) \le \frac{\mathrm{var}(N)}{1^2} = 4.
> ```
>
> 此时，由切比雪夫不等式得到的上界 4 没有信息量，因为我们本来就知道 $P(N \ge 5) \le 1$。
>
> 要得到该概率更好的界，改用马尔可夫不等式，它给出：
>
> ```math
> P(N \ge 5) \le \frac{E[N]}{5} = \frac{4}{5}.
> ```
>
> > <span style="color:#1e8449;">**[mathtip]**</span> <span style="color:#1e8449;">**Tip（提示）：** 本例精确值为 $P(N \ge 5) = 1 - e^{-4}\sum_{k=0}^{4} 4^k / k! \approx 0.371$。可见两个不等式给出的界都相当宽松，但 Markov 界 $4/5$ 至少小于 1，优于 Chebyshev 的无信息界 4。直觉：Chebyshev 界的是"偏离均值 $\ge 1$"的双侧概率，而泊松分布的方差与均值同为 4，距离 1 太近，自然松得离谱；Markov 只用非负性与均值，反而更贴题。</span>

**6.（5 分）** 你不知道 $\lambda_A$，但观察了 Alice 一个小时，看到她恰好发出了 5 封邮件。据此信息推导 $\lambda_A$ 的最大似然估计（maximum likelihood estimate）。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：**
>
> ```math
> \hat{\lambda}_A = \underset{\lambda}{\arg\max}\ \log\big(p_N(5; \lambda)\big) = \underset{\lambda}{\arg\max}\ \log\frac{\lambda^5 e^{-\lambda}}{5!} = \underset{\lambda}{\arg\max}\ \big({-\log(5!) + 5\log(\lambda) - \lambda}\big).
> ```
>
> 令一阶导数为零：
>
> ```math
> \frac{5}{\lambda} - 1 = 0 \quad\Longrightarrow\quad \hat{\lambda}_A = 5.
> ```

<!-- ===== PDF p8 ===== -->

**7.（5 分）** 我们有理由相信 $\lambda_A$ 是一个很大的数。令 $N$ 为区间 $[0, 1]$ 内发出的邮件数。请论证为何可以对 $N$ 应用中心极限定理（CLT），并给出此时 CLT 的精确陈述。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 当 $\lambda_A$ 很大时，设 $\lambda_A \gg 1$。为简单起见，先设 $\lambda_A$ 为整数。我们可以把区间 $[0, 1]$ 分成 $\lambda_A$ 个互不相交、时长各为 $1/\lambda_A$ 的小区间，使它们恰好铺满整个区间 $[0, 1]$。令 $N_i$ 为第 $i$ 个这样的小区间内的到达数，则各 $N_i$ 是独立同分布、参数为 1 的泊松随机变量。由于 $N$ 定义为区间 $[0, 1]$ 内的到达数，故 $N = N_1 + \cdots + N_{\lambda_A}$。因为 $\lambda_A \gg 1$，$N$ 就是大量独立同分布随机变量之和，且 $N_i$ 的分布不随求和项数的增加而改变。因此，$N$ 近似服从均值为 $\lambda_A$、方差为 $\lambda_A$ 的正态分布。
>
> 若 $\lambda_A$ 不是整数，同样的论证仍然成立，只是小区间个数不再是 $\lambda_A$ 个，而是等于 $\lambda_A$ 的整数部分的整数个（$\bar{\lambda}_A = \lfloor \lambda_A \rfloor$，floor 即向下取整）、每个时长为 $1/\lambda_A$，另加一个时长更短（$(\lambda_A - \bar{\lambda}_A)/\lambda_A$）的额外区间。
>
> 此时，$N$ 等于 $\bar{\lambda}_A$ 个独立同分布、参数为 1 的泊松随机变量之和，再加上另一个参数为 $(\lambda_A - \bar{\lambda}_A)$ 的泊松随机变量（它与其余所有泊松随机变量也独立）。这种情况下，要套用我们熟悉形式的中心极限定理需作一点小的修正；但事实证明，即使不作此修正，加入这个额外的泊松随机变量也不会妨碍 $N$ 的分布在 $\lambda_A$ 很大时近似正态，中心极限定理依然适用。
>
> 要得到 CLT 的精确陈述，必须对 $N$ 作"标准化"（standardize）：先减去其均值，再除以其标准差。如此处理后，当求和项数趋于无穷（即 $\lambda_A \to \infty$）时，标准化后的 $N$ 的 CDF 应收敛到标准正态 CDF。
>
> 因此，CLT 应用于 $N$ 时的精确陈述为：
>
> ```math
> \lim_{\lambda_A \to \infty} P\left(\frac{N - \lambda_A}{\sqrt{\lambda_A}} \le z\right) = \Phi(z),
> ```
>
> 其中 $\Phi(z)$ 为标准正态分布的 CDF。

**8.（5 分）** 在与上一小问相同的假设（$\lambda_A$ 很大）下，现在可以把 $N$ 当作正态随机变量。设你观测到了 $N$ 的取值。给出 $\lambda_A$ 的（近似）95% 置信区间（confidence interval），并准确说明你用了哪些近似。

可能有用的常识：标准正态累积分布满足 $\Phi(1.645) = 0.95$ 与 $\Phi(1.96) = 0.975$。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** 我们先用最大似然（ML）估计量 $\hat{\lambda}_A = N$ 来估计 $\lambda_A$（其中 $E[N] = \lambda_A$）。当 $\lambda_A$ 很大时 CLT 适用，可以设 $N$ 近似服从正态分布。由于 $\mathrm{var}(N) = \lambda_A$，还可以用 $\lambda_A$ 的 ML 估计量来近似 $N$ 的方差，即 $\mathrm{var}(N) \approx N$，从而 $\sigma_N \approx \sqrt{N}$。

<!-- ===== PDF p9 ===== -->

**（续）**

> 为求 95% 置信区间，寻找 $\beta$ 使得：
>
> ```math
> 0.95 = P(|N - \lambda_A| \le \beta) = P\left(\frac{|N - \lambda_A|}{\sqrt{N}} \le \frac{\beta}{\sqrt{N}}\right) \approx 2\Phi\left(\frac{\beta}{\sqrt{N}}\right) - 1.
> ```
>
> 于是求得：
>
> ```math
> \beta \approx \sqrt{N}\, \Phi^{-1}(0.975) = 1.96\sqrt{N}.
> ```
>
> 从而可以写出：
>
> ```math
> P(N - 1.96\sqrt{N} \le \lambda_A \le N + 1.96\sqrt{N}) \approx 0.95.
> ```
>
> 所以，近似的 95% 置信区间为：$[\,N - 1.96\sqrt{N},\ N + 1.96\sqrt{N}\,]$。
>
> > <span style="color:#1e8449;">**[note]**</span> <span style="color:#1e8449;">**Note（提取校验）：** 原文提取文本中该行显示为"$\approx 2\Phi(\beta/\sqrt{N})$"，缺少"− 1"。由 $P(|Z| \le c) = 2\Phi(c) - 1$ 以及下一步 $\beta = \sqrt{N}\,\Phi^{-1}(0.975)$（即 $2\Phi(\beta/\sqrt{N}) - 1 = 0.95 \Rightarrow \Phi(\beta/\sqrt{N}) = 0.975$）反推，此处应为 $2\Phi(\beta/\sqrt{N}) - 1$，已据计算还原。</span>

**9.** 现在告诉你：$\lambda_A$ 其实是参数为 2 的指数随机变量（exponential random variable）$\Lambda$ 的实现值：

```math
f_\Lambda(\lambda) = 2e^{-2\lambda}, \qquad \lambda \ge 0.
```

**（a）（5 分）** 求 $E[N^2]$。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：**
>
> ```math
> \begin{aligned}
> E[N^2] &= E\big[E[N^2 \mid \Lambda]\big] = E\big[\mathrm{var}(N \mid \Lambda) + (E[N \mid \Lambda])^2\big] \\
> &= E[\Lambda + \Lambda^2] = E[\Lambda] + \mathrm{var}(\Lambda) + (E[\Lambda])^2 = \frac{1}{2} + \frac{2}{2^2} = 1.
> \end{aligned}
> ```

**（b）（5 分）** 求给定 $N$ 时 $\Lambda$ 的线性最小二乘估计（linear least squares estimator, LLMS）。

> <span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：**
>
> ```math
> \hat{\Lambda}_{LLMS} = E[\Lambda] + \frac{\mathrm{cov}(N, \Lambda)}{\mathrm{var}(N)}\,(N - E[N]).
> ```
>
> 解出上式中的各个量：
>
> ```math
> E[\Lambda] = \frac{1}{2}; \qquad
> E[N] = E\big[E[N \mid \Lambda]\big] = E[\Lambda] = \frac{1}{2};
> ```
>
> ```math
> \mathrm{var}(N) = E[N^2] - (E[N])^2 = 1 - \frac{1}{4} = \frac{3}{4};
> ```
>
> ```math
> \mathrm{cov}(N, \Lambda) = E[N\Lambda] - E[N]E[\Lambda] = E\big[E[N\Lambda \mid \Lambda]\big] - (E[\Lambda])^2 = E[\Lambda^2] - (E[\Lambda])^2 = \mathrm{var}(\Lambda) = \frac{1}{4}.
> ```

<!-- ===== PDF p10 ===== -->

**（续）**

> 将上述各量代入前式：
>
> ```math
> \hat{\Lambda}_{LLMS} = E[\Lambda] + \frac{\mathrm{cov}(N, \Lambda)}{\mathrm{var}(N)}\,(N - E[N]) = \frac{1}{2} + \frac{1/4}{3/4}\left(N - \frac{1}{2}\right) = \frac{1}{3}(N + 1).
> ```

<!-- ===== PDF p11 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu　6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability）　Fall 2010（2010 秋季学期）。有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
