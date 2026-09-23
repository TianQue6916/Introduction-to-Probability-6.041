<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 5 解答（Problem Set 5: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）· 电气工程与计算机科学系（Department of Electrical Engineering &amp; Computer Science）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 由于任何联合概率密度函数（joint PDF）都必须满足归一化性质（normalization property），
>
> ```math
> 1 = \int_{x=1}^{2}\int_{y=x}^{2} ax\,\mathrm{d}y\,\mathrm{d}x = \int_{x=1}^{2} ax(2-x)\,\mathrm{d}x = a\left(2^2 - 1^2 - \frac{2^3}{3} + \frac{1^3}{3}\right) = \frac{2a}{3},
> ```
>
> 故 $a = 3/2$。
>
> **(b)** 当 $1 \le y \le 2$ 时，
>
> ```math
> f_Y(y) = \int_1^y ax\,\mathrm{d}x = \frac{a}{2}\,(y^2 - 1) = \frac{3}{4}\,(y^2 - 1),
> ```
>
> 其余情形下 $f_Y(y) = 0$。
>
> **(c)** 首先注意到，当 $1 \le x \le 3/2$ 时，
>
> ```math
> f_{X|Y}(x \mid 3/2) = \frac{f_{X,Y}(x,\,3/2)}{f_Y(3/2)} = \frac{(3/2)\,x}{\frac{3}{4}\left[\left(\frac{3}{2}\right)^2 - 1^2\right]} = \frac{8x}{5}.
> ```
>
> 因此，
>
> ```math
> E\!\left[\frac{1}{X} \,\middle|\, Y = 3/2\right] = \int_1^{3/2} \frac{1}{x}\cdot\frac{8x}{5}\,\mathrm{d}x = \frac{4}{5}.
> ```

---

<!-- ===== PDF p2 ===== -->

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 按定义 $f_{X,Y}(x,y) = f_X(x)\,f_{Y|X}(y \mid x)$。如图所示，$f_X(x) = ax$。于是
>
> ```math
> 1 = \int_0^{40} ax\,\mathrm{d}x = 800a,
> ```
>
> 所以 $f_X(x) = x/800$。由题意，$f_{Y|X}(y \mid x) = \dfrac{1}{2x}$，其中 $y \in [0,\,2x]$。因此
>
> ```math
> f_{X,Y}(x,y) =
> \begin{cases}
> 1/1600, & \text{若 } 0 \le x \le 4 \text{ 且 } 0 < y < 2x, \\[1mm]
> 0, & \text{其余情形}.
> \end{cases}
> ```
>
> **(b)** 当 $Y > X$ 时，Paul 获得正利润（positive profit）。这发生的概率为
>
> ```math
> P(Y > X) = \iint_{y>x} f_{X,Y}(x,y)\,\mathrm{d}y\,\mathrm{d}x = \int_0^{40}\int_x^{2x} \frac{1}{1600}\,\mathrm{d}y\,\mathrm{d}x = \frac{1}{2}.
> ```
>
> 我们本来也可以这样得到同一答案：意识到对 $X$ 的每一个可能取值，都有 $1/2$ 的概率使 $Y > X$。
>
> **(c)** 联合密度函数满足 $f_{X,Z}(x,z) = f_X(x)\,f_{Z|X}(z \mid x)$。由于 $Z$ 在给定 $X$ 时条件均匀分布（conditionally uniformly distributed），故当 $-x \le z \le x$ 时 $f_{Z|X}(z \mid x) = \dfrac{1}{2x}$。因此，当 $0 \le x \le 40$ 且 $-x \le z \le x$ 时，$f_{X,Z}(x,z) = 1/1600$。边缘密度（marginal density）$f_Z(z)$ 计算如下：
>
> ```math
> f_Z(z) = \int_{x=|z|}^{40} f_{X,Z}(x,z)\,\mathrm{d}x = \int_{x=|z|}^{40} \frac{1}{1600}\,\mathrm{d}x =
> \begin{cases}
> \dfrac{40 - |z|}{1600}, & \text{若 } |z| < 40, \\[2mm]
> 0, & \text{其余情形}.
> \end{cases}
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 要使 $X$ 与 $Y$ 相互独立（independent），对 $X$ 的任何观测都不应提供关于 $Y$ 的任何信息。若观测到 $X = 0$，则必有 $Y = 0$。换言之，$f_{Y|\{X=0\}}(y \mid 0) \ne f_Y(y)$。因此 $X$ 与 $Y$ 不独立。
>
> **(b)**
>
> ```math
> f_X(x) =
> \begin{cases}
> x/2, & \text{若 } 0 \le x \le 1, \\[1mm]
> -3x/2 + 3, & \text{若 } 1 < x \le 2, \\[1mm]
> 0, & \text{其余情形};
> \end{cases}
> ```
>
> ```math
> f_{Y|X}(y \mid 0.5) =
> \begin{cases}
> 2, & \text{若 } 0 \le y \le 1/2, \\[1mm]
> 0, & \text{其余情形};
> \end{cases}
> ```
>
> ```math
> f_{X|Y}(x \mid 0.5) =
> \begin{cases}
> 1/2, & \text{若 } 1/2 \le x \le 1, \\[1mm]
> 3/2, & \text{若 } 1 < x \le 3/2, \\[1mm]
> 0, & \text{其余情形}.
> \end{cases}
> ```
>
> <span style="color:#7f8c8d;">【图】原页此处为三幅密度曲线图：$f_X(x)$、$f_{Y|X}(y\,|\,0.5)$ 与 $f_{X|Y}(x\,|\,0.5)$ 的图形。原图由后处理统一插入。</span>
>
> **(c)** 事件 $A$ 使我们剩下的区域是一个高度恒定的直角三角形，于是条件 PDF 为 $1/\text{面积} = 8$。条件期望（conditional expectation）为：
>
> ```math
> E[R \mid A] = E[XY \mid A] = \int_0^{0.5}\int_y^{0.5} 8xy\,\mathrm{d}x\,\mathrm{d}y = 1/16.
> ```
>
> **(d)** $W$ 的累积分布函数（CDF）为 $F_W(w) = P(W \le w) = P(Y - X \le w) = P(Y \le X + w)$。$P(Y \le X + w)$ 可以这样计算：对一切可能的 $w$，积分直线 $Y = X + w$ 之下的面积。下图画出了 $w = 0$、$w = -1/2$、$w = -1$ 与 $w = -3/2$ 时的直线 $Y = X + w$。利用两个三角形上均匀 PDF 的性质即可求出我们关注的概率——别忘了把面积乘以相应的联合密度 $f_{X,Y}(x,y)$！注意有 4 个值得关注的区域：$w < -2$、$-2 \le w \le -1$、$-1 < w \le 0$ 与 $w > 0$。

<!-- ===== PDF p3 ===== -->

<span style="color:#c0392b;">**Problem 3（续）**</span>

> <span style="color:#7f8c8d;">【图】原页此处为支撑区域示意图：三角形两条边界 $y = x$ 与 $y = 2 - x$，并画出 $w = 0$、$w = -1$ 时的直线 $Y = X + w$，标注区域 $w \in (-1,\,0)$ 与 $w \in (-2,\,-1)$，以及截距 $1 + w$、$2 + w$ 等。原图由后处理统一插入。</span>
>
> $W$ 的 CDF 为
>
> ```math
> F_W(w) =
> \begin{cases}
> 0, & \text{若 } w < -2, \\[2mm]
> \dfrac{3}{2}\cdot\dfrac{1}{2}\cdot\dfrac{(2+w)^2}{2}, & \text{若 } -2 \le w \le -1, \\[3mm]
> \dfrac{1}{2}\cdot\dfrac{(1+w)^2}{2} + \dfrac{3}{2}\left(\dfrac{1}{2}\cdot 1\cdot 1 - \dfrac{1}{2}\left(-\dfrac{w}{2}\right)(-w)\right), & \text{若 } -1 < w \le 0, \\[3mm]
> 1, & \text{若 } w > 0,
> \end{cases}
> ```
>
> 即
>
> ```math
> F_W(w) =
> \begin{cases}
> 0, & \text{若 } w < -2, \\[2mm]
> \dfrac{3}{8}\,(2+w)^2, & \text{若 } -2 \le w \le -1, \\[2mm]
> \dfrac{1}{8}\,(-w^2 + 4w + 8), & \text{若 } -1 < w \le 0, \\[2mm]
> 1, & \text{若 } w > 0.
> \end{cases}
> ```
>
> 作为合理性检验（sanity check）：$F_W(-\infty) = 0$，$F_W(+\infty) = 1$；且 $F_W(w)$ 在 $w = -2$ 与 $w = -1$ 处连续。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 若发射机（transmitter）发送符号 0，则接收信号是一个均值为 $-2$、方差为 $4$ 的正态随机变量（normal random variable）。换言之，$f_{Y|X}(y \mid -2) = \mathrm{N}(-2,\,4)$；同样地，$f_{Y|X}(y \mid 2) = \mathrm{N}(2,\,4)$。这些条件 PDF 如下图所示。

<!-- ===== PDF p4 ===== -->

<span style="color:#c0392b;">**Problem 4（续）**</span>

> <span style="color:#7f8c8d;">【图】原页此处为两条条件正态密度曲线 $f_{Y|X}(y\,|\,2)$ 与 $f_{Y|X}(y\,|\,-2)$（横轴范围约 $-8$ 到 $8$），并以阴影标出错误区域 $P(\mathrm{error} \mid X = 2)$ 与 $P(\mathrm{error} \mid X = -2)$。原图由后处理统一插入。</span>
>
> 错误概率（probability of error）可利用全概率定理（total probability theorem）求得：
>
> ```math
> P(\mathrm{error}) = P(\mathrm{error} \mid X = -2)\,P(X = -2) + P(\mathrm{error} \mid X = 2)\,P(X = 2)
> ```
>
> ```math
> = \frac{1}{2}\left(P(Y \ge 0 \mid X = -2) + P(Y < 0 \mid X = 2)\right)
> = \frac{1}{2}\left(P(N \ge 2 \mid X = -2) + P(N < -2 \mid X = 2)\right)
> ```
>
> ```math
> = \frac{1}{2}\left(P(N \ge 2) + P(N < -2)\right)
> = \frac{1}{2}\left(P\!\left(\frac{N-0}{2} \ge \frac{2-0}{2}\right) + P\!\left(\frac{N-0}{2} < \frac{-2-0}{2}\right)\right)
> ```
>
> ```math
> = \frac{1}{2}\left((1 - \Phi(1)) + (1 - \Phi(1))\right) = 0.1587.
> ```
>
> **(b)** 使用 3 个分量（component）时，在观测到 $X$ 的条件下，错误概率就是 3 个分量中有 2 个或 3 个被错误解码的概率。每个分量的错误概率为 $0.1587$。因此
>
> ```math
> P(\mathrm{error} \mid \mathrm{sent}\ 0) = \binom{3}{2}(0.1587)^2 (1 - 0.1587) + (0.1587)^3 = 0.0676.
> ```
>
> 由对称性，$P(\mathrm{error} \mid \mathrm{sent}\ 1) = P(\mathrm{error} \mid \mathrm{sent}\ 0)$。因此
>
> ```math
> P(\mathrm{error}) = P(\mathrm{error} \mid \mathrm{sent}\ 0)\,P(\mathrm{sent}\ 0) + P(\mathrm{error} \mid \mathrm{sent}\ 1)\,P(\mathrm{sent}\ 1) = 0.0676.
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 有很多方法可以证明 $X$ 与 $Y$ 不独立。最直观的论证之一是：知道 $X$ 的取值会限制 $Y$ 的取值范围，反之亦然。例如，若已知某次试验中 $X \ge 1/2$，那么该次试验中 $Y$ 的取值就不可能小于 $1/2$。

<!-- ===== PDF p5 ===== -->

<span style="color:#c0392b;">**Problem 5（续）**</span>

> 另一种证明两者不独立的方法是：计算它们各自期望的乘积，并说明该乘积不等于 $E[XY]$。
>
> **(b)** 应用边缘 PDF 的定义：当 $0 \le x \le 1$ 时，
>
> ```math
> f_X(x) = \int f_{X,Y}(x,y)\,\mathrm{d}y = \int_x^{x+1} 1\,\mathrm{d}y = 1;
> ```
>
> 当 $0 \le y \le 1$ 时，
>
> ```math
> f_Y(y) = \int f_{X,Y}(x,y)\,\mathrm{d}x = \int_0^y 1\,\mathrm{d}x = y;
> ```
>
> 当 $1 \le y \le 2$ 时，
>
> ```math
> f_Y(y) = \int f_{X,Y}(x,y)\,\mathrm{d}x = \int_{y-1}^{1} 1\,\mathrm{d}x = 2 - y.
> ```
>
> <span style="color:#7f8c8d;">【图】原页此处为两幅密度曲线图：$f_X(x)$（区间 $[0,1]$ 上高度为 1 的均匀密度）与 $f_Y(y)$（在 $y = 1$ 处达到峰值 1 的三角形密度）。原图由后处理统一插入。</span>
>
> **(c)** 由期望的线性性（linearity of expectation），和的期望等于期望的和。直接观察可得 $E[X] = 1/2$、$E[Y] = 1$。于是 $E[X + Y] = E[X] + E[Y] = 3/2$。

<!-- ===== PDF p6 ===== -->

<span style="color:#c0392b;">**Problem 5（续）**</span>

> **(d)** $X + Y$ 的方差为
>
> ```math
> E[(X+Y)^2] - (E[X+Y])^2 = E[X^2] + 2E[XY] + E[Y^2] - (E[X+Y])^2. \qquad (1)
> ```
>
> (c) 中已经算出 $E[X+Y]$，因此只需再计算其余三个量。首先是 $X^2$ 的期望：
>
> ```math
> E[X^2] = \int_0^1 x^2 \int_x^{x+1} 1\,\mathrm{d}y\,\mathrm{d}x = \int_0^1 x^2\,\mathrm{d}x = 1/3.
> ```
>
> 同样，$Y^2$ 的期望为
>
> ```math
> E[Y^2] = \int_0^1 \int_x^{x+1} y^2\,\mathrm{d}y\,\mathrm{d}x = \int_0^1 (3x^2 + 3x + 1)/3\,\mathrm{d}x = 7/6.
> ```
>
> 最后，$XY$ 的期望为
>
> ```math
> E[XY] = \int_0^1 \int_x^{x+1} xy\,\mathrm{d}y\,\mathrm{d}x = \int_0^1 (2x^2 + x)/2\,\mathrm{d}x = 7/12.
> ```
>
> 将它们代入 (1) 式，得 $\mathrm{var}(X + Y) = 1/3 + 7/6 + 7/6 - 9/4 = 5/12$。
>
> **(c)、(d) 两问的另一种（快捷）解法**
>
> 给定 $X$ 的任意取值（在 $[0,1]$ 内），可以观察到 $Y - X$ 的取值介于 $0$ 与 $1$ 之间，且服从均匀分布。由于 $Y - X$ 的条件分布对 $[0,1]$ 中每一个 $X$ 值都相同，可见 $Y - X$ 与 $X$ 独立。于是：(a) $X$ 是均匀分布的；(b) $Y = X + U$，其中 $U$ 也服从均匀分布且与 $X$ 独立。由此可得
>
> ```math
> E[X+Y] = E[2X + U] = 3/2.
> ```
>
> 进而 $\mathrm{var}(X + Y) = 4\,\mathrm{var}(X) + \mathrm{var}(U) = 5/12$。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 6**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 设 $A$ 为“第一次抛掷结果为正面”这一事件。为计算概率 $P(A)$，我们使用全概率定理的连续版本（continuous version of the total probability theorem）：
>
> ```math
> P(A) = \int_0^1 P(A \mid P = p)\,f_P(p)\,\mathrm{d}p = \int_0^1 p\,(1 + \sin(2\pi p))\,\mathrm{d}p,
> ```
>
> 经过一些计算得
>
> ```math
> P(A) = \frac{\pi - 1}{2\pi}.
> ```
>
> **(b)** 利用贝叶斯法则（Bayes' rule），
>
> ```math
> f_{P|A}(p) = \frac{P(A \mid P = p)\,f_P(p)}{P(A)}
> = \begin{cases}
> \dfrac{2\pi p\,(1 + \sin(2\pi p))}{\pi - 1}, & \text{若 } 0 \le p \le 1, \\[3mm]
> 0, & \text{其余情形}.
> \end{cases}
> ```

<!-- ===== PDF p7 ===== -->

<span style="color:#c0392b;">**Problem 6（续）**</span>

> **(c)** 设 $B$ 为“第二次抛掷结果为正面”这一事件。我们有
>
> ```math
> P(B \mid A) = \int_0^1 P(B \mid P = p,\,A)\,f_{P|A}(p)\,\mathrm{d}p
> = \int_0^1 P(B \mid P = p)\,f_{P|A}(p)\,\mathrm{d}p
> = \frac{2\pi}{\pi - 1}\int_0^1 p^2\,(1 + \sin(2\pi p))\,\mathrm{d}p.
> ```
>
> 经过一些计算，得
>
> ```math
> P(B \mid A) = \frac{2\pi}{\pi - 1}\cdot\frac{2\pi - 3}{6\pi} = \frac{2\pi - 3}{3\pi - 3} \approx 0.5110.
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**G1†**</span> <span style="color:#7f8c8d;">（† 6.431 必做；6.041 选做）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> 设 $\mathbf{a} = (\cos\theta,\,\sin\theta)$，$\mathbf{b} = (b_x,\,b_y)$。我们将证明：$R$ 的点都不落在 $C$ 之外，当且仅当
>
> ```math
> |b_y| \le |\sin\theta| \quad\text{且}\quad |b_x| \le |\cos\theta|. \qquad (2)
> ```
>
> $R$ 的另外两个顶点是 $(\cos\theta,\,b_y)$ 与 $(b_x,\,\sin\theta)$。若 $|b_x| \le |\cos\theta|$ 且 $|b_y| \le |\sin\theta|$，则 $R$ 的每个顶点 $(x, y)$ 都满足 $x^2 + y^2 \le \cos^2\theta + \sin^2\theta = 1$，因而 $R$ 的点不可能落在 $C$ 之外。反之，若 $R$ 的点都不落在 $C$ 之外，把这一条件用于除 $\mathbf{a}$、$\mathbf{b}$ 之外的另两个顶点，便得到
>
> ```math
> \cos^2\theta + b_y^2 \le 1, \qquad b_x^2 + \sin^2\theta \le 1,
> ```
>
> 这等价于 (2) 式。这些条件意味着 $(b_x, b_y)$ 位于 $C$ 之内或之上，因此对任意给定的 $\theta$，随机点 $\mathbf{b} = (b_x, b_y)$ 满足 (2) 式的概率为
>
> ```math
> \frac{2|\cos\theta|\cdot 2|\sin\theta|}{\pi} = \frac{2}{\pi}\,|\sin(2\theta)|,
> ```
>
> 故总概率为
>
> ```math
> \frac{1}{2\pi}\int_0^{2\pi} \frac{2}{\pi}\,|\sin(2\theta)|\,\mathrm{d}\theta = \frac{4}{\pi^2}\int_0^{\pi/2} \sin(2\theta)\,\mathrm{d}\theta = \frac{4}{\pi^2}.
> ```

<span style="color:#7f8c8d;">† 6.431 必做；6.041 选做（Required for 6.431; optional for 6.041）。</span>

<!-- ===== PDF p8 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu —— 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010。有关引用这些材料或使用条款的信息，请访问：http://ocw.mit.edu/terms。</span>
