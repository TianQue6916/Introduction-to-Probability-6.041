<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 6 解答（Problem Set 6: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）· 电气工程与计算机科学系（Department of Electrical Engineering &amp; Computer Science）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> 我们画出 $f_{X,Y}(x,y)$ 非零的区域：
>
> <span style="color:#7f8c8d;">【图】原页此处为区域 $R$ 的示意图：由直线 $y = x$、$x = 2$ 与 $x$ 轴围成的三角形区域（$1 \le x \le 2$，$0 \le y \le x$），图中还画出了直线 $y - x = z$。原图由后处理统一插入。</span>
>
> **(a)** 联合 PDF 必须积分为 1。由
>
> ```math
> \int_{x=1}^{2}\int_{y=0}^{x} ax\,\mathrm{d}y\,\mathrm{d}x = \frac{7}{3}\,a = 1,
> ```
>
> 得 $a = \dfrac{3}{7}$。
>
> **(b)**
>
> ```math
> f_Y(y) = \int f_{X,Y}(x,y)\,\mathrm{d}x =
> \begin{cases}
> \displaystyle\int_1^2 \frac{3}{7}\,x\,\mathrm{d}x, & \text{若 } 0 \le y \le 1, \\[3mm]
> \displaystyle\int_y^2 \frac{3}{7}\,x\,\mathrm{d}x, & \text{若 } 1 < y \le 2, \\[3mm]
> 0, & \text{其余情形},
> \end{cases}
> =
> \begin{cases}
> \dfrac{9}{14}, & \text{若 } 0 \le y \le 1, \\[2mm]
> \dfrac{3}{14}\,(4 - y^2), & \text{若 } 1 < y \le 2, \\[2mm]
> 0, & \text{其余情形}.
> \end{cases}
> ```
>
> **(c)**
>
> ```math
> f_{X|Y}(x \mid 3/2) = \frac{f_{X,Y}(x,\,3/2)}{f_Y(3/2)} = \frac{8}{7}\,x, \qquad \frac{3}{2} \le x \le 2, \text{（其余为 } 0\text{）}.
> ```
>
> 于是，
>
> ```math
> E\!\left[\frac{1}{X} \,\middle|\, Y = 3/2\right] = \int_{3/2}^{2} \frac{1}{x}\cdot\frac{8}{7}\,x\,\mathrm{d}x = \frac{4}{7}.
> ```
>
> **(d)** 我们采用“先求 CDF、再对其求导得到 PDF”的技巧。
>
> ```math
> F_Z(z) = P(Z \le z) = P(Y - X \le z)
> ```
>
> ```math
> = \begin{cases}
> 0, & \text{若 } z < -2, \\[2mm]
> \displaystyle\int_{x=-z}^{2}\int_{y=0}^{x+z} \frac{3}{7}\,x\,\mathrm{d}y\,\mathrm{d}x = \frac{8}{7} + \frac{6}{7}\,z - \frac{1}{14}\,z^3, & \text{若 } -2 \le z \le -1, \\[4mm]
> \displaystyle\int_{x=1}^{2}\int_{y=0}^{x+z} \frac{3}{7}\,x\,\mathrm{d}y\,\mathrm{d}x = 1 + \frac{9}{14}\,z, & \text{若 } -1 < z \le 0, \\[4mm]
> 1, & \text{若 } 0 < z.
> \end{cases}
> ```
>
> ```math
> f_Z(z) = \frac{\mathrm{d}}{\mathrm{d}z}F_Z(z) =
> \begin{cases}
> \dfrac{6}{7} - \dfrac{3}{14}\,z^2, & \text{若 } -2 \le z \le -1, \\[2mm]
> \dfrac{9}{14}, & \text{若 } -1 < z \le 0, \\[2mm]
> 0, & \text{其余情形}.
> \end{cases}
> ```

---

<!-- ===== PDF p2 ===== -->

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#1e8449;">[note] 译者注：原题设定（由解答中的卷积式与各段积分限反推，并已完整验算）：$X$ 与 $Y$ 相互独立，其中一个随机变量的 PDF 为 $f(x) = \frac{3}{4}(1 - x^2)$（$-1 \le x \le 1$，其余为 0），另一个为分段均匀密度：$f(y) = \frac{1}{3}$（$0 \le y \le 1$）、$f(y) = \frac{2}{3}$（$2 \le y \le 3$），其余为 0；$Z = X + Y$。</span>
>
> <span style="color:#2471a3;">[solution]</span>
>
> 利用卷积积分（convolution integral）可以直接算出 $Z$ 的 PDF $f_Z(z)$：
>
> ```math
> f_Z(z) = \int_{-\infty}^{\infty} f_X(t)\,f_Y(z - t)\,\mathrm{d}t.
> ```
>
> 当 $z \in [-1,\,0]$ 时，
>
> ```math
> f_Z(z) = \int_{-1}^{z} \frac{1}{3}\cdot\frac{3}{4}\,(1 - t^2)\,\mathrm{d}t = \frac{1}{4}\left(z - \frac{z^3}{3} + \frac{2}{3}\right).
> ```
>
> 当 $z \in [0,\,1]$ 时，
>
> ```math
> f_Z(z) = \int_{z-1}^{z} \frac{1}{3}\cdot\frac{3}{4}\,(1 - t^2)\,\mathrm{d}t = \frac{1}{4}\left(1 - \frac{z^3}{3} + \frac{(z-1)^3}{3}\right).
> ```
>
> 当 $z \in [1,\,2]$ 时，
>
> ```math
> f_Z(z) = \int_{z-1}^{1} \frac{1}{3}\cdot\frac{3}{4}\,(1 - t^2)\,\mathrm{d}t + \int_{-1}^{z-2} \frac{2}{3}\cdot\frac{3}{4}\,(1 - t^2)\,\mathrm{d}t = \frac{1}{3}\left[\frac{3(z-1)}{4} + \frac{(z-1)^3}{4} - \frac{(z-2)^3}{2}\right].
> ```
>
> 当 $z \in [2,\,3]$ 时，
>
> ```math
> f_Z(z) = \int_{z-3}^{z-2} \frac{2}{3}\cdot\frac{3}{4}\,(1 - t^2)\,\mathrm{d}t = \frac{1}{6}\left(3 + (z-3)^3 - (z-2)^3\right).
> ```
>
> 当 $z \in [3,\,4]$ 时，
>
> ```math
> f_Z(z) = \int_{z-3}^{1} \frac{2}{3}\cdot\frac{3}{4}\,(1 - t^2)\,\mathrm{d}t = \frac{1}{6}\left(11 - 3z + (z-3)^3\right).
> ```
>
> $f_Z(z)$ 的草图如下。
>
> <span style="color:#7f8c8d;">【图】原页此处为 $f_Z(z)$ 的草图：横轴 $z$ 从 $-1$ 到 $4$，纵轴标出 $0.5$ 与 $1$，曲线在 $z \in [2,3]$ 内达到约 $0.46$ 的最大值。原图由后处理统一插入。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#1e8449;">[note] 译者注：原题设定（由解答反推）：共进行 $n$ 次独立投掷，每次投掷以概率 $1/k$ 等可能地得到 $1, \dots, k$ 之一；$X_1$、$X_2$ 分别为结果等于 1 和等于 2 的次数。</span>
>
> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** $X_1$ 与 $X_2$ 负相关（negatively correlated）。直观上说，结果为 1 的投掷次数较多，就意味着结果为 2 的投掷次数较少。
>
> **(b)** 设 $A_t$（相应地，$B_t$）为伯努利（Bernoulli）随机变量，当且仅当第 $t$ 次投掷结果为 1（相应地，为 2）时取值 1。我们有 $E[A_t B_t] = 0$（因为 $A_t \ne 0$ 就意味着 $B_t = 0$），并且当 $s \ne t$ 时
>
> ```math
> E[A_t B_s] = E[A_t]\,E[B_s] = \frac{1}{k}\cdot\frac{1}{k}.
> ```
>
> 于是，
>
> ```math
> E[X_1 X_2] = E\left[(A_1 + \cdots + A_n)(B_1 + \cdots + B_n)\right] = n\,E\left[A_1 (B_1 + \cdots + B_n)\right] = n(n-1)\cdot\frac{1}{k}\cdot\frac{1}{k}.
> ```

<!-- ===== PDF p3 ===== -->

<span style="color:#c0392b;">**Problem 3（续）**</span>

> 且
>
> ```math
> \mathrm{cov}(X_1, X_2) = E[X_1 X_2] - E[X_1]\,E[X_2] = \frac{n(n-1)}{k^2} - \frac{n^2}{k^2} = -\frac{n}{k^2}.
> ```
>
> $X_1$ 与 $X_2$ 的协方差（covariance）为负，与预期一致。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 若 $X$ 取 $-1$ 与 $1$ 之间的值 $x$，则 $Y$ 的条件 PDF 在 $-2$ 与 $2$ 之间均匀分布；若 $X$ 取 $1$ 与 $2$ 之间的值 $x$，则 $Y$ 的条件 PDF 在 $-1$ 与 $1$ 之间均匀分布。
>
> 类似地，若 $Y$ 取 $-1$ 与 $1$ 之间的值 $y$，则 $X$ 的条件 PDF 在 $-1$ 与 $2$ 之间均匀分布；若 $Y$ 取 $1$ 与 $2$ 之间的值 $y$，或取 $-2$ 与 $-1$ 之间的值 $y$，则 $X$ 的条件 PDF 在 $-1$ 与 $1$ 之间均匀分布。
>
> **(b)** 我们有
>
> ```math
> E[X \mid Y = y] =
> \begin{cases}
> 0, & \text{若 } -2 \le y \le -1, \\[1mm]
> 1/2, & \text{若 } -1 < y \le 1, \\[1mm]
> 0, & \text{若 } 1 \le y \le 2,
> \end{cases}
> ```
>
> 以及
>
> ```math
> \mathrm{var}(X \mid Y = y) =
> \begin{cases}
> 1/3, & \text{若 } -2 \le y \le -1, \\[1mm]
> 3/4, & \text{若 } -1 < y \le 1, \\[1mm]
> 1/3, & \text{若 } 1 \le y \le 2.
> \end{cases}
> ```
>
> 由此可得 $E[X] = 3/10$，$\mathrm{var}(X) = 193/300$。
>
> **(c)** 由对称性，$E[Y \mid X] = 0$，$E[Y] = 0$。此外，$\mathrm{var}(Y \mid X = x)$ 是某个均匀 PDF（其取值范围依赖于 $x$）的方差，且
>
> ```math
> \mathrm{var}(Y \mid X = x) =
> \begin{cases}
> 4/3, & \text{若 } -1 \le x \le 1, \\[1mm]
> 1/3, & \text{若 } 1 < x \le 2.
> \end{cases}
> ```
>
> 利用全方差公式（law of total variance），我们得到
>
> ```math
> \mathrm{var}(Y) = E[\mathrm{var}(Y \mid X)] = \frac{4}{5}\cdot\frac{4}{3} + \frac{1}{5}\cdot\frac{1}{3} = 17/15.
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> 首先写出我们所有随机变量的性质。同时定义 $K$ 为出席会议的会员人数，$B$ 为描述某位会员是否出席会议的伯努利（Bernoulli）随机变量。
>
> ```math
> E[N] = \frac{1}{1-p}, \qquad \mathrm{var}(N) = \frac{p}{(1-p)^2},
> ```
>
> ```math
> E[M] = \frac{1}{\lambda}, \qquad \mathrm{var}(M) = \frac{1}{\lambda^2},
> ```
>
> ```math
> E[B] = q, \qquad \mathrm{var}(B) = q(1 - q).
> ```
>
> **(a)** 由于 $K = B_1 + B_2 + \cdots + B_N$，
>
> ```math
> E[K] = E[N]\cdot E[B] = \frac{q}{1-p},
> ```
>
> ```math
> \mathrm{var}(K) = E[N]\cdot\mathrm{var}(B) + (E[B])^2\cdot\mathrm{var}(N) = \frac{q(1-q)}{1-p} + \frac{pq^2}{(1-p)^2}.
> ```

<!-- ===== PDF p4 ===== -->

<span style="color:#c0392b;">**Problem 5（续）**</span>

> **(b)** 设 $G$ 为带到会议的总金额。则 $G = M_1 + M_2 + \cdots + M_K$。
>
> ```math
> E[G] = E[M]\cdot E[K] = \frac{q}{\lambda(1-p)},
> ```
>
> ```math
> \mathrm{var}(G) = \mathrm{var}(M)\cdot E[K] + (E[M])^2\,\mathrm{var}(K) = \frac{q}{\lambda^2(1-p)} + \frac{1}{\lambda^2}\left(\frac{q(1-q)}{1-p} + \frac{pq^2}{(1-p)^2}\right).
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**G1†**</span> <span style="color:#7f8c8d;">（† 6.431 必做；6.041 选做）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 设 $X_1, X_2, \ldots, X_n$ 为独立同分布（IID, independent identically distributed）随机变量。我们注意到
>
> ```math
> E[X_1 + \cdots + X_n \mid X_1 + \cdots + X_n = x_0] = x_0.
> ```
>
> 由期望的线性性（linearity of expectations）可得
>
> ```math
> x_0 = E[X_1 + \cdots + X_n \mid X_1 + \cdots + X_n = x_0] = E[X_1 \mid X_1 + \cdots + X_n = x_0] + \cdots + E[X_n \mid X_1 + \cdots + X_n = x_0].
> ```
>
> 由于诸 $X_i$ 同分布，我们有如下关系式：对任意 $1 \le i \le n$、$1 \le j \le n$，
>
> ```math
> E[X_i \mid X_1 + \cdots + X_n = x_0] = E[X_j \mid X_1 + \cdots + X_n = x_0].
> ```
>
> 因此，
>
> ```math
> n\,E[X_1 \mid X_1 + \cdots + X_n = x_0] = x_0
> \quad\Longrightarrow\quad
> E[X_1 \mid X_1 + \cdots + X_n = x_0] = \frac{x_0}{n}.
> ```
>
> **(b)** 注意到我们可以把 $E[X_1 \mid S_n = s_n,\, S_{n+1} = s_{n+1},\, \ldots,\, S_{2n} = s_{2n}]$ 改写如下：
>
> ```math
> E[X_1 \mid S_n = s_n,\, S_{n+1} = s_{n+1},\, \ldots,\, S_{2n} = s_{2n}]
> ```
>
> ```math
> = E[X_1 \mid S_n = s_n,\, X_{n+1} = s_{n+1} - s_n,\, X_{n+2} = s_{n+2} - s_{n+1},\, \ldots,\, X_{2n} = s_{2n} - s_{2n-1}]
> = E[X_1 \mid S_n = s_n],
> ```
>
> 其中最后一个等号成立是由于诸 $X_i$ 相互独立。我们还注意到
>
> ```math
> E[X_1 + \cdots + X_n \mid S_n = s_n] = E[S_n \mid S_n = s_n] = s_n.
> ```
>
> 由期望的线性性可得
>
> ```math
> E[X_1 + \cdots + X_n \mid S_n = s_n] = E[X_1 \mid S_n = s_n] + \cdots + E[X_n \mid S_n = s_n].
> ```
>
> 由于诸 $X_i$ 同分布，我们有如下关系式：对任意 $1 \le i \le n$、$1 \le j \le n$，
>
> ```math
> E[X_i \mid S_n = s_n] = E[X_j \mid S_n = s_n].
> ```
>
> 因此，
>
> ```math
> E[X_1 + \cdots + X_n \mid S_n = s_n] = n\,E[X_1 \mid S_n = s_n] = s_n
> \quad\Longrightarrow\quad
> E[X_1 \mid S_n = s_n] = \frac{s_n}{n}.
> ```

<span style="color:#7f8c8d;">† 6.431 必做；6.041 选做（Required for 6.431; optional for 6.041）。</span>

<!-- ===== PDF p5 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu —— 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010。有关引用这些材料或使用条款的信息，请访问：http://ocw.mit.edu/terms。</span>
