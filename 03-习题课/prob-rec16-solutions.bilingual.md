<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 16 解答（Recitation 16: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；November 2, 2010，2010 年 11 月 2 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）。本件即 6.041/6.431 Spring 2007 Quiz 2 Solutions（2007 春季学期测验 2 解答）。原 PDF 共 7 页，其中 p7 为 MIT OpenCourseWare 版权页；原文只含解答、不含题面。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）（i）** $X$ 的 PDF 图形见图 1。PDF 必须积分为 1，所以 $f_X(x)$ 之下的面积 $2c+c$ 必须等于 1，因此 $c=1/3$。
>
> PDF 的积分（integration of the PDF）：
>
> ```math
> \int_2^4 f_X(x)\,dx = 1
> ```
>
> 拆开写为
>
> ```math
> \int_2^3 2c\,dx + \int_3^4 c\,dx = 2c + c = 1
> ```
>
> 故 $c = 1/3$。
>
> <span style="color:#7f8c8d;">【图】原页此处为 Figure 1：$X$ 的 PDF（PDF of $X$）——分段均匀密度，在 $2\le x\le 3$ 上高度为 $2c$、在 $3\le x\le 4$ 上高度为 $c$，横轴为 $x$。原图由后处理统一插入。</span>
>
> **（ii）**
>
> ```math
> E[X] = \int_2^4 x f_X(x)\,dx = \int_2^3 x\cdot 2/3\,dx + \int_3^4 x\cdot 1/3\,dx
> ```
>
> ```math
> = 1/3\cdot\left(3^2 - 2^2\right) + 1/6\cdot\left(4^2 - 3^2\right) = 5/3 + 17/6 = 17/6.
> ```
>
> <span style="color:#1e8449;">**[note]** 原文如此：中间一步应为 "$5/3 + 7/6$"（因为 $\frac{1}{6}\left(4^2-3^2\right)=\frac{7}{6}$），最终结果 $E[X]=17/6$ 正确。</span>
>
> **（iii）**
>
> ```math
> E[X^2] = \int_2^4 x^2 f_X(x)\,dx = \int_2^3 x^2\cdot 2/3\,dx + \int_3^4 x^2\cdot 1/3\,dx
> ```
>
> ```math
> = 2/9\cdot\left(3^3 - 2^3\right) + 1/9\cdot\left(4^3 - 3^3\right) = 38/9 + 37/9 = 25/3.
> ```

<!-- ===== PDF p2 ===== -->

**（续 Problem 1）**

> **（iv）** 令 $Y = 2X+1$。$Y$ 的取值范围不再是 2 到 4，而是 $5\le y\le 9$。$Y$ 的 PDF 形状应与 $X$ 的 PDF 相同，但要按某一比例缩放使其归一化（normalize）到 1。$Y$ 的范围是 $X$ 的两倍，所以密度减半。图形见下方图 2。
>
> 由于 $Y=g(X)$ 是 $X$ 的线性函数（linear function），可以使用线性函数的导出分布（derived distribution）公式：$Y = 2X+1$，故当 $5\le y\le 9$ 时 $f_Y(y) = \frac{1}{2}f_X\!\left(\frac{y-1}{2}\right)$。图 2 与该分布吻合。
>
> <span style="color:#7f8c8d;">【图】原页此处为 Figure 2：$Y=2X+1$ 的 PDF（PDF of $Y=2X+1$）——分段均匀密度，在 $5\le y\le 7$ 上高度为 $c$、在 $7\le y\le 9$ 上高度为 $c/2$，横轴为 $y$。原图由后处理统一插入。</span>
>
> **（b）** 首先计算联合 PDF（joint PDF）。它应在区域 $2\le x\le 4$、$2\le w\le 4$ 上有非零的联合密度；但它并不在整个正方形上都均匀——这种情况课上已多次见到。由于 $X$ 的密度分段均匀，该正方形被划分成两个各自具有均匀联合密度的矩形。$X$ 与 $W$ 相互独立（independent），所以联合密度就是两个边缘密度（marginal）的乘积：
>
> ```math
> f_{X,W}(x,w) = f_X(x)\,f_W(w) = f_X(x)\cdot 1/2 =
> \begin{cases}
> c_1 = 2/3\cdot 1/2 = 1/3, & 2\le x\le 3,\ 2\le w\le 4,\\[4pt]
> c_2 = 1/3\cdot 1/2 = 1/6, & 3\le x\le 4,\ 2\le w\le 4.
> \end{cases}
> ```
>
> 变量 $c_1$、$c_2$ 用来表示这两块不同的联合密度，并标注在联合分布图中。作为检验，联合 PDF 应归一化为 1——事实正是如此。
>
> $X$ 与 $W$ 的联合 PDF 如图 3 所示。观察联合 PDF 的图形可知，$P(X\le W)$ 对应直线 $x=w$ 上方的区域，见图 4。用 $c_1$、$c_2$ 分别对阴影区域两部分的面积加权，即得所求概率：
>
> ```math
> P(X\le W) = 1/2\cdot 1/6 + 3/2\cdot 1/3 = 1/12 + 1/2 = 7/12.
> ```
>
> 图解法是简便的做法。当然，也可以直接积分：

<!-- ===== PDF p3 ===== -->

**（续 Problem 1）**

> <span style="color:#7f8c8d;">【图】原页顶部为 Figure 3 与 Figure 4：Figure 3 是 $X$ 与 $W$ 的联合 PDF（Joint PDF of $X$ and $W$）——正方形 $[2,4]\times[2,4]$ 分成两块矩形，$2\le x\le 3$ 一块高度为 $c_1$、$3\le x\le 4$ 一块高度为 $c_2$；Figure 4 是 $P(X\le W)$ 的图解——直线 $x=w$ 上方的阴影区，分属 $c_1$、$c_2$ 两块。原图由后处理统一插入。</span>
>
> ```math
> P(X\le W) = \int_2^3\!\!\int_x^4 1/3\,dw\,dx + \int_3^4\!\!\int_x^4 1/6\,dw\,dx
> = \frac{1}{3}\int_2^3(4-x)\,dx + \frac{1}{6}\int_3^4(4-x)\,dx = 7/12
> ```
>
> **（c）** 这里要小心：$T$ 是秒表测得的比赛时间，而不只是被高估的那段（多计的）时间；还要记住 $T$ 与 $W$ 相互独立。
>
> ```math
> f_{W|T}(w\mid 3) = \frac{f_{W,T}(w,3)}{f_T(3)}
> ```
>
> 其中 $f_{W,T}(w,3) = f_W(w)\,f_T(3) = 10\cdot 1/2 = 5$（对 $2\le w\le 4$）；且
>
> ```math
> f_T(3) = \int_{3-1/10}^{3} f_{W,T}(w,3)\,dw = 5\cdot(1/10) = 1/2.
> ```
>
> 因此
>
> ```math
> f_{W|T}(w\mid 3) =
> \begin{cases}
> 10, & \text{若 } (3-1/10)\le w\le 3 \text{ 且 } t=3,\\[2pt]
> 0, & \text{其他情形.}
> \end{cases}
> ```
>
> <span style="color:#1e8449;">**[note]** 原文如此，有两处存疑：其一，$f_W(w)=10$ 不可能在 $2\le w\le 4$ 上成立（积分不为 1），结合结论中 $3-\frac{1}{10}\le w\le 3$ 的支撑范围，"for $2\le w\le 4$" 应为笔误；其二，先写 $f_{W,T}(w,3)=f_W(w)f_T(3)$、再由它积分求 $f_T(3)$ 属循环论证，按上下文原意应为 $f_{W,T}(w,3)=f_W(w)f_N(3-w)=10\cdot\frac{1}{2}=5$（$N$ 为秒表多计的时间，与 $W$ 独立）。此读法下 $f_T(3)=5\cdot\frac{1}{10}=\frac{1}{2}$ 与最终答案 $f_{W|T}(w\mid 3)=10$ 均吻合。</span>

<!-- ===== PDF p4 ===== -->

**（续 Problem 1）**

> **（d）** $N$ 服从 Normal($1/60$, $4/3600$)（正态分布）。我们把 $N$ 标准化（standardize）成均值 1、标准差 1，以便利用正态表（Normal table）。
>
> <span style="color:#1e8449;">**[note]** 原文如此：标准化后的分布均值应为 0、标准差为 1，此处不影响本小问的计算。</span>
>
> ```math
> P\!\left(N>\frac{5}{60}\right) = 1 - P\!\left(N<\frac{5}{60}\right) = 1 - P\!\left(\frac{N-1/60}{2/60} < \frac{5/60-1/60}{2/60}\right) = 1 - \Phi(2).
> ```
>
> 查表得 $\Phi(2) = 0.9772$。所以 $P\!\left(N>\frac{5}{60}\right) = 1 - 0.9772 = 0.0028$。
>
> **（e）** 用导出分布（derived distributions）求出 $S$ 的 CDF，再对 $s$ 求导，得到 $S$ 的 PDF。$S$ 的范围由 $W$ 的范围决定：由于 $W$ 的 PDF 仅在 $2\le w\le 4$ 上非零，故 $S$ 的 PDF 仅在 $24/4\le s\le 24/2$ 上非零。
>
> ```math
> P(S\le s) = P(24/W\le s) = P(W\ge 24/s) = 1 - F_W(24/s) = 1 - \int_2^{24/s} f_W(w)\,dw = 1 - (12/s - 1) = 2 - 12/s
> ```
>
> 对 $s$ 求导：
>
> ```math
> f_S(s) = \frac{d}{ds}\left(2 - \frac{12}{s}\right) =
> \begin{cases}
> 12/s^2, & \text{若 } 6\le s\le 12,\\[2pt]
> 0, & \text{其他情形.}
> \end{cases}
> ```

<!-- ===== PDF p5 ===== -->

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）（i）** 这是一个随机和（random sums）问题，所以 $A$ 的均值与方差要用重期望定律（law of iterated expectations）与全方差定律（law of total variance）来求。
>
> ```math
> \mu_a = E[A] = E\big[E[A\mid N]\big] = E\big[N\,E[A_i]\big] = E[A_i]\,E[N] = 1/p.
> ```
>
> ```math
> \sigma_a^2 = \mathrm{var}(A) = E\big[\mathrm{var}(A\mid N)\big] + \mathrm{var}\big(E[A\mid N]\big) = E\big[N\,\mathrm{var}(A_i)\big] + \mathrm{var}\big(N\,E[A_i]\big)
> ```
>
> ```math
> = \mathrm{var}(A_i)\,E[N] + E[A_i]^2\,\mathrm{var}(N) = 1/p + p/(1-p) = 1/p^2.
> ```
>
> <span style="color:#1e8449;">**[note]** 原文如此：中间一步 "$1/p + p/(1-p)$" 应为 "$1/p + (1-p)/p^2$"——由下面 (ii) 可知 $\mathrm{var}(N)=(1-p)/p^2$，且 $1/p + (1-p)/p^2 = 1/p^2$；最终结果 $\sigma_a^2 = 1/p^2$ 正确。</span>
>
> **（ii）**
>
> ```math
> c_{ab} = E[AB] = E\big[(A_1+A_2+A_3+\ldots+A_N)(B_1+B_2+B_3+\ldots+B_N)\big]
> ```
>
> ```math
> = E\Big[E\big[(A_1+A_2+A_3+\ldots+A_N)(B_1+B_2+B_3+\ldots+B_N)\,\big|\,N\big]\Big] = E\big[N\,E[A_i]\cdot N\,E[B_i]\big] = E\big[N^2\,E[A_i]\,E[B_i]\big] = E[A_i]\,E[B_i]\,E[N^2]
> ```
>
> ```math
> = 1\cdot 1\cdot\big(\mathrm{var}(N) + E[N]^2\big) = (1-p)/p^2 + 1/p^2 = (2-p)/p^2.
> ```
>
> **（b）（i）** 若 $N=1$，则 $A=A_1$，它服从均值为 1、方差为 1 的正态（Normal）分布。若 $N=2$，则 $A=A_1+A_2$，是两个正态随机变量之和。因此 $A$ 的分布为 $\mathrm{Normal}(1+1,\,1+1)$，即 $\mathrm{Normal}(2,\,2)$。
>
> 利用全概率定理（total probability theorem），得到：
>
> ```math
> f_A(a) = f_{A|N=1}(a)\,P_N(1) + f_{A|N=2}(a)\,P_N(2) = \mathrm{Normal}(1,1)\cdot 1/3 + \mathrm{Normal}(2,2)\cdot 2/3
> ```
>
> ```math
> = \frac{1}{3\sqrt{2\pi}}\,e^{-(a-1)^2/2} + \frac{2}{3\sqrt{4\pi}}\,e^{-(a-2)^2/4}.
> ```
>
> **（ii）**
>
> ```math
> P(N=1\mid A=a) = \frac{P(A=a,\,N=1)\,\delta}{P(A=a)\,\delta},
> ```
>
> 其中 $P(A=a)\,\delta = f_A(a)$ 已在 (a) 部分求出，而联合项为 $P(A=a)\,P(N=1)\,\delta = f_A(a)\,P_N(1)$。
>
> 于是
>
> ```math
> P(N=1\mid A=a) = \frac{\dfrac{1}{3\sqrt{2\pi}}\,e^{-(a-1)^2/2}}{\dfrac{1}{3\sqrt{2\pi}}\,e^{-(a-1)^2/2} + \dfrac{2}{3\sqrt{4\pi}}\,e^{-(a-2)^2/4}}.
> ```
>
> **（c）** 相等。首先可以验证：它们都是随机变量。$A$ 与 $B$ 彼此并不独立，因为二者的随机和都依赖于随机变量 $N$；但若以 $N$ 为条件，则 $A$ 与 $B$ 独立（也就是说，它们条件独立（conditionally independent））。这正是等式右边所陈述的含义吗？只要 $A\mid N$ 与 $A\mid(B,N)$ 的 PDF 相等，这两个期望就相等。一旦 $N$ 已知，

<!-- ===== PDF p6 ===== -->

**（续 Problem 2）**

> 再知道 $B$ 并不会改变关于 $A$ 的已知信息；因此这不仅表明给定 $N$ 时 $A$ 与 $B$ 条件独立，也表明 $A\mid N$ 与 $A\mid B,N$ 携带相同的信息。
>
> 事件 $X$、$Y$ 关于 $Z$ 的条件独立（conditional independence）定义为：
>
> ```math
> P(X\cap Y\mid Z) = P(X\mid Z)\,P(Y\mid Z)
> ```
>
> 或者等价地，
>
> ```math
> P(X\mid Y\cap Z) = P(X\mid Z).
> ```
>
> 下面证明等式在此处成立：
>
> ```math
> E[A\mid N] = E[A\mid B,N]
> ```
>
> ```math
> \int a\,f_{A|N}(a\mid n)\,da = \int a\,f_{A|B,N}(a\mid b,n)\,da
> ```
>
> 只要两个 PDF 相等，上式即成立：
>
> ```math
> f_{A|N}(a\mid n) = f_{A|B,N}(a\mid b,n) = \frac{f_{A,B,N}(a,b,n)}{f_{B,N}(b,n)}
> = \frac{f_{A,B|N}(a,b\mid n)\,P_N(n)}{f_{B|N}(b\mid n)\,P_N(n)} = \frac{f_{A|N}(a\mid n)\,f_{B|N}(b\mid n)}{f_{B|N}(b\mid n)} = f_{A|N}(a\mid n).
> ```
>
> 所以 $E[A\mid N] = E[A\mid B,N]$ 成立。

<!-- ===== PDF p7 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（http://ocw.mit.edu）· 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010。有关引用这些材料或使用条款的信息，请访问 http://ocw.mit.edu/terms。（此页为 OCW 版权页。）</span>
