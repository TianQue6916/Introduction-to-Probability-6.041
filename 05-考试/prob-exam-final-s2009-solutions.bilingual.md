<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Final Exam 解答（Final Exam: Solutions）**</span> <span style="color:#7f8c8d;">（Spring 2009，2009 春季学期）</span>

<span style="color:#7f8c8d;">原文：MIT OCW「6.041SC Spring 2009 final exam solutions」（期末考试解答，本文翻译第 1–9 页）。</span>

---

**6.041/6.431　2009 春季学期期末考试（Spring 2009 Final Exam）**

考试时间：5 月 21 日（星期四），下午 1:30 – 4:30。

名字（Name）：＿＿＿＿＿＿　　习题课教师（Recitation Instructor）：＿＿＿＿＿＿

| Question（题号） | Part（部分） | Score（得分） | Out of（满分） |
|:---:|:---:|:---:|:---:|
| 0 | — | | 2 |
| 1 | all（全部） | | 18 |
| 2 | all（全部） | | 24 |
| 3 | a | | 4 |
| 3 | b | | 4 |
| 3 | c | | 4 |
| 4 | a | | 6 |
| 4 | b | | 6 |
| 4 | c | | 6 |
| 5 | a | | 6 |
| 5 | b | | 6 |
| 6 | a | | 4 |
| 6 | b | | 4 |
| 6 | c | | 4 |
| 6 | d | | 5 |
| 6 | e | | 5 |
| 7 | a | | 6 |
| 7 | b | | 6 |
| **Total（总分）** | | | **120** |

- 请把解答写在本试题册（quiz packet）内；只有写在本试题册内的解答才会被评分。
- 允许携带三张双面的 8.5×11 英寸公式纸（formula sheet），外加一台计算器。
- 考试时间为 180 分钟。
- 请书写工整！若我们无法辨认，将不给分。

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">（原文自本页起每页页眉为 "Massachusetts Institute of Technology / Department of Electrical Engineering & Computer Science / 6.041/6.431: Probabilistic Systems Analysis (Spring 2009)"，页脚为 "Page N of 18"，下文不再逐页重复。）</span>

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1. 判断题（True or False）（每小题 2 分，共 18 分）**</span>

本部分中的各小题均不设部分分（no partial credit）。

**a.** 设 $\{X_n\}$ 为取值于区间 $[0,\,0.5]$ 的独立同分布（i.i.d.）随机变量序列。考察以下论断：

- **(A)** 若 $E[X_n^2]$ 当 $n\to\infty$ 时收敛于 0，则 $X_n$ 依概率（in probability）收敛于 0。
- **(B)** 若所有 $X_n$ 都满足 $E[X_n]=0.2$，且 $\mathrm{var}(X_n)$ 当 $n\to\infty$ 时收敛于 0，则 $X_n$ 依概率收敛于 0.2。
- **(C)** 由 $Z_n = X_1\cdot X_2\cdot\ldots\cdot X_n$ 定义的随机变量序列 $Z_n$，当 $n\to\infty$ 时依概率收敛于 0。

上述论断中哪些总是成立？请在下方各框内填写 True（真）或 False（假）。

**A：True　　B：True　　C：True** <span style="color:#7f8c8d;">（解答版中框内已填入答案）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(A) True（正确）。** $\lim_{n\to\infty}E[X_n^2]=0$ 这一事实蕴含 $\lim_{n\to\infty}E[X_n]=0$ 与 $\lim_{n\to\infty}\mathrm{var}(X_n)=0$。于是有
>
> ```math
> \begin{aligned}
> P\left(|X_n-0|\geq\epsilon\right)
> &\leq P\left(|X_n-E[X_n]|\geq\epsilon/2\right)+P\left(|E[X_n]-0|\geq\epsilon/2\right)\\
> &\leq \frac{\mathrm{var}(X_n)}{(\epsilon/2)^2}+P\left(|E[X_n]-0|\geq\epsilon/2\right)\;\to\;0,
> \end{aligned}
> ```
>
> 其中我们用到了切比雪夫不等式（Chebyshev inequality）。
>
> **(B) True。** 应用切比雪夫不等式得
>
> ```math
> P\left(|X_n-E[X_n]|\geq\epsilon\right)\leq\frac{\mathrm{var}(X_n)}{\epsilon^2}\;\to\;0.
> ```
>
> 因此 $X_n$ 依概率收敛于 $E[X_n]=0.2$。
>
> **(C) True。** 对任意 $\epsilon>0$，由于 $Z_n\leq(1/2)^n$，故当 $n>-\log\epsilon/\log 2$ 时 $P\left(|Z_n-0|\geq\epsilon\right)=0$。
>
> <span style="color:#1e8449;">[mathtip] 因为每个 $X_i\in[0,0.5]$，故 $0\le Z_n\le(1/2)^n$；一旦 $(1/2)^n<\epsilon$（即 $n>-\log\epsilon/\log 2$），事件 $\{|Z_n-0|\ge\epsilon\}$ 便是不可能事件。</span>

<!-- ===== PDF p3 ===== -->

**Problem 1-b（续）**

上述论断中哪些总是成立？请在下方各框内填写 True（真）或 False（假）。

**A：True　　B：True　　C：True**

> <span style="color:#2471a3;">[solution]</span>
>
> **(A) True。** 注意 $E\!\left[\dfrac{X_1+\cdots+X_n}{n}\right]=0$，且 $\mathrm{var}\!\left(\dfrac{X_1+\cdots+X_n}{n}\right)=\dfrac{n\cdot 2}{n^2}=\dfrac{2}{n}$。由此可见 $\dfrac{X_1+\cdots+X_n}{n}$ 依概率收敛于 0。
>
> **(B) True。** 令 $Z_i=X_i^2$，则 $E[Z_i]=2$。注意由于 $X_i$ 是 i.i.d. 的，$Z_i$ 也是 i.i.d. 的，于是由弱大数定律（WLLN），$\dfrac{Z_1+\cdots+Z_n}{n}$ 依概率收敛于 $E[Z_i]=2$。
>
> <span style="color:#1e8449;">[mathtip] 这里用到 $E[X_i^2]=\mathrm{var}(X_i)+\left(E[X_i]\right)^2=2+0=2$。</span>
>
> **(C) True。** 令 $W_i=X_iY_i$，则 $E[W_i]=E[X_i]E[Y_i]=0$。注意由于 $X_i$ 与 $Y_i$ 分别是 i.i.d. 的，$W_i$ 也是 i.i.d. 的，于是由 WLLN，$\dfrac{W_1+\cdots+W_n}{n}$ 依概率收敛于 $E[W_i]=0$。

**c.** 我们有 i.i.d. 随机变量 $X_1\,\ldots\,X_n$，其分布未知，且 $\mu=E[X_i]$。定义 $M_n=(X_1+\ldots+X_n)/n$。考察以下论断：

- **(A)** 无论 $X_i$ 的分布如何，$M_n$ 都是 $\mu$ 的极大似然估计量（maximum-likelihood estimator）。
- **(B)** 无论 $X_i$ 的分布如何，$M_n$ 都是 $\mu$ 的相合估计量（consistent estimator）。
- **(C)** 无论 $X_i$ 的分布如何，$M_n$ 都是 $\mu$ 的渐近无偏估计量（asymptotically unbiased estimator）。

上述论断中哪些总是成立？请在下方各框内填写 True（真）或 False（假）。

**A：False　　B：True　　C：True**

> <span style="color:#2471a3;">[solution]</span>
>
> **(A) False（错误）。** 考虑 $X_i$ 服从均匀分布（uniform distribution）$U\!\left[\mu-\dfrac{1}{2},\ \mu+\dfrac{1}{2}\right]$ 的情形。此时 $\mu$ 的 ML 估计量是介于 $\max(X_1,\ldots,X_n)-\dfrac{1}{2}$ 与 $\min(X_1,\ldots,X_n)+\dfrac{1}{2}$ 之间的任意值，而不是 $M_n$。
>
> **(B) True。** 由弱大数定律（WLLN），$M_n$ 依概率收敛于 $\mu$，因此它是相合估计量。
>
> **(C) True。** 由于 $E[M_n]=E[X_i]=\mu$，$M_n$ 是 $\mu$ 的无偏估计量（unbiased estimator），因而也是渐近无偏的。

---

<!-- ===== PDF p4 ===== -->

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2. 选择题（Multiple Choice）（每小题 4 分，共 24 分）**</span>

请清晰地圈出相应选项。本部分中的各小题均不设部分分。

**a.** 苏门答腊（Sumatra）的地震按强度 $\lambda=2/$年的泊松过程（Poisson process）发生。在"一年内恰好发生两次地震"的条件下，两次地震都发生在该年头三个月内的概率是多少？（为简单起见，假设每个月都有 30 天、每年有 12 个月，即一年 360 天。）

（i）$1/12$　　（ii）$1/16$　　（iii）$64/225$　　（iv）$4e^{-4}$

（v）没有足够的信息来确定所求概率。　　（vi）以上都不对。

> <span style="color:#2471a3;">[solution]</span> 把一年的区间视为 $[0,1]$。
>
> ```math
> P\bigl(2 \text{ in } [0,\tfrac{1}{4}) \,\big|\, 2 \text{ in } [0,1]\bigr)
> =\frac{P\bigl(2 \text{ in } [0,\tfrac{1}{4}),\ 0 \text{ in } [\tfrac{1}{4},1]\bigr)}{P\bigl(2 \text{ in } [0,1]\bigr)}
> =\frac{\dfrac{(\lambda\cdot 1/4)^2}{2!}\,e^{-\lambda\cdot 1/4}\cdot\dfrac{(\lambda\cdot 3/4)^0}{0!}\,e^{-\lambda\cdot 3/4}}{\dfrac{\lambda^2 e^{-\lambda}}{2!}}
> =\frac{1}{16}.
> ```
>
> （另一种解释）已知 12 个月内恰好发生了两次地震，则每次地震等可能地发生在 12 个月中的任何一个月，它发生在头 3 个月内的概率为 $3/12=1/4$。两次都发生在头 3 个月内的概率即为 $(1/4)^2$。

**b.** 考虑一个具有三个状态 $i\in\{1,2,3\}$ 的连续时间马尔可夫链（continuous-time Markov chain），每次访问状态 $i$ 时的停留时间（dwelling time）是参数为 $\nu_i=i$ 的指数随机变量，转移概率 $p_{ij}$ 由下图定义：

<span style="color:#7f8c8d;">【图】原页此处为该连续时间马尔可夫链的状态转移图（生灭链结构：状态 $1\leftrightarrow 2\leftrightarrow 3$ 相邻互连）。原图由后处理统一插入。</span>

问：长期来看，停留在状态 2 的时间的期望比例（expected fraction of time）是多少？

（i）$1/2$　　（ii）$1/4$　　（iii）$2/5$

<!-- ===== PDF p5 ===== -->

**Problem 2-b（续）**

（iv）$3/7$　　（v）以上都不对。

> <span style="color:#2471a3;">[solution]</span> 首先，我们计算 $q_{ij}=\nu_i p_{ij}$，即 $q_{12}=q_{21}=q_{23}=1$ 与 $q_{32}=3$。这条生灭马尔可夫链（birth-death Markov chain）的平衡（balance）方程与归一化（normalization）方程可写为：$\pi_1=\pi_2$，$\pi_2=3\pi_3$，以及 $\pi_1+\pi_2+\pi_3=1$，由此解得 $\pi_2=3/7$。
>
> <span style="color:#1e8449;">[mathtip] 生灭链的平衡方程形如 $\pi_i q_{i,i+1}=\pi_{i+1}\,q_{i+1,i}$（相邻状态间的转移概率流守恒）：由 $\pi_1 q_{12}=\pi_2 q_{21}$ 得 $\pi_1=\pi_2$，由 $\pi_2 q_{23}=\pi_3 q_{32}$ 得 $\pi_2=3\pi_3$。</span>

<!-- ===== PDF p6 ===== -->

**c.** 考虑如下马尔可夫链：

<span style="color:#7f8c8d;">【图】原页此处为（离散时间）马尔可夫链的状态转移图（含状态与转移概率标注；由下述解答可知状态 1 为瞬态）。原图由后处理统一插入。</span>

从状态 3 出发，处于状态 1 的稳态概率（steady-state probability）是多少？

（i）$1/3$　　（ii）$1/4$　　（iii）$1$　　（iv）$0$　　（v）以上都不对。

> <span style="color:#2471a3;">[solution]</span> 状态 1 是瞬态的（transient）。
>
> <span style="color:#1e8449;">[mathtip] 瞬态状态在稳态中的概率必为 0：链以概率 1 最终永久离开瞬态状态、不再返回。</span>

**d.** 随机变量 $X$ 与 $Y$ 满足：数对 $(X,Y)$ 在图 1 所示的梯形 $A$（顶点为 $(0,0)$、$(1,2)$、$(3,2)$、$(4,0)$）上均匀分布：

<span style="color:#7f8c8d;">【图】原页此处为梯形 $A$ 的示意图（顶点 $(0,0)$、$(1,2)$、$(3,2)$、$(4,0)$，坐标轴标注 $X$、$Y$）。原图由后处理统一插入。</span>

图 1（Figure 1）：$f_{X,Y}(x,y)$ 在阴影区域上为常数，其余处为 0。

即

```math
f_{X,Y}(x,y)=\begin{cases}c, & (x,y)\in A,\\[2pt] 0, & \text{else}.\end{cases}
```

我们观测 $Y$，并用它来估计 $X$。设 $\hat{X}$ 为给定 $Y$ 时 $X$ 的最小均方误差估计量（least mean squared error estimator）。问 $\mathrm{var}(\hat{X}-X\mid Y=1)$ 的值是多少？

（i）$1/6$　　（ii）$3/2$　　（iii）$1/3$　　（iv）信息不足以计算该值。

<!-- ===== PDF p7 ===== -->

**Problem 2-d（续）**

（v）以上都不对。

> <span style="color:#2471a3;">[solution]</span> $f_{X|Y=1}(x)$ 在 $[0,2]$ 上均匀分布，因此 $\hat{X}=E[X\mid Y=1]=1$，且
>
> ```math
> \mathrm{var}(\hat{X}-X\mid Y=1)=\mathrm{var}(X\mid Y=1)=\frac{(2-0)^2}{12}=\frac{1}{3}.
> ```
>
> <span style="color:#1e8449;">[note] 译者注：按题给梯形（顶点 $(0,0)$、$(1,2)$、$(3,2)$、$(4,0)$）的几何，$Y=1$ 处的水平截面应为 $[1/2,\,7/2]$（宽 3），相应地 $\mathrm{var}(X\mid Y=1)=(7/2-1/2)^2/12=3/4$。原解答所用的 $[0,2]$（宽 2、均值 1、方差 $1/3$）恰好对应 $x=1$ 处对 $Y$ 的竖直截面，疑将 $X$ 与 $Y$ 的角色互换。此处照原文译出。</span>

**e.** $X_1\,\ldots\,X_n$ 为 i.i.d. 的正态（normal）随机变量，均值为 $\mu$、方差为 $v$，且 $\mu$ 与 $v$ 均未知。定义 $M_n=(X_1+\ldots+X_n)/n$ 与

```math
V_n=\frac{1}{n-1}\sum_{i=1}^{n}(X_i-M_n)^2.
```

再定义 $\Phi(x)$ 为标准正态分布的 CDF（累积分布函数），$\Psi_{n-1}(x)$ 为自由度 $n-1$ 的 $t$ 分布（t-distribution）的 CDF。下列哪个选项对所有 $n>1$ 都给出 $\mu$ 的精确（exact）99% 置信区间（confidence interval）？

（i）$[M_n-\delta\sqrt{V_n/n},\ M_n+\delta\sqrt{V_n/n}]$，其中 $\delta$ 的选取使 $\Phi(\delta)=0.99$。

（ii）$[M_n-\delta\sqrt{V_n/n},\ M_n+\delta\sqrt{V_n/n}]$，其中 $\delta$ 的选取使 $\Phi(\delta)=0.995$。

（iii）$[M_n-\delta\sqrt{V_n/n},\ M_n+\delta\sqrt{V_n/n}]$，其中 $\delta$ 的选取使 $\Psi_{n-1}(\delta)=0.99$。

（iv）$[M_n-\delta\sqrt{V_n/n},\ M_n+\delta\sqrt{V_n/n}]$，其中 $\delta$ 的选取使 $\Psi_{n-1}(\delta)=0.995$。

（v）以上都不对。

> <span style="color:#2471a3;">[solution]</span> 见第 23 讲（Lecture 23）幻灯片第 10–12 页（slides 10-12）。
>
> <span style="color:#1e8449;">[mathtip] 双侧 99% 置信区间的每侧尾概率为 0.5%，故分位点须取 0.995；又因方差 $v$ 未知、以其估计量 $V_n$ 代替，精确区间须用自由度 $n-1$ 的 $t$ 分布。即选项 (iv)。</span>

**f.** 我们有 i.i.d. 随机变量 $X_1,\,X_2$，服从参数 $\theta$ 未知的指数分布（exponential distribution）。在假设（hypothesis）$H_0$ 下 $\theta=1$；在假设 $H_1$ 下 $\theta=2$。在似然比检验（likelihood-ratio test）下，拒绝域（rejection region）取下列哪种形式？

（i）$R=\{(x_1,x_2):\ x_1+x_2>\xi\}$，$\xi$ 为某个值。

（ii）$R=\{(x_1,x_2):\ x_1+x_2<\xi\}$，$\xi$ 为某个值。

（iii）$R=\{(x_1,x_2):\ e^{x_1}+e^{x_2}>\xi\}$，$\xi$ 为某个值。

（iv）$R=\{(x_1,x_2):\ e^{x_1}+e^{x_2}<\xi\}$，$\xi$ 为某个值。

（v）以上都不对。

> <span style="color:#2471a3;">[solution]</span> 我们定义 $R=\{x=(x_1,x_2)\mid L(x)>c\}$，其中
>
> ```math
> L(x)=\frac{f_X(x;H_1)}{f_X(x;H_0)}
> =\frac{\theta_1 e^{-\theta_1 x_1}\,\theta_1 e^{-\theta_1 x_2}}{\theta_0 e^{-\theta_0 x_1}\,\theta_0 e^{-\theta_0 x_2}}
> =\left(\frac{\theta_1}{\theta_0}\right)^{2}e^{(\theta_0-\theta_1)(x_1+x_2)}
> =4e^{-(x_1+x_2)}.
> ```
>
> 故 $R=\{(x_1,x_2)\mid x_1+x_2<-\log(c/4)\}$。
>
> <span style="color:#1e8449;">[mathtip] $L(x)=4e^{-(x_1+x_2)}$ 是 $x_1+x_2$ 的严格减函数，故 $L(x)>c$ 等价于 $x_1+x_2<-\log(c/4)$，即选项 (ii)。</span>

---

<!-- ===== PDF p8 ===== -->

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3（共 12 分）**</span>

两种族（蓝色与绿色）的外星人正按参数分别为 $\lambda_b$ 与 $\lambda_g$ 的泊松过程（Poisson process）相互独立地抵达地球。外星人到达登记服务局（Alien Arrival Registration Service Authority, AARSA）即将开始登记外星人的到达。

设 $T_1$ 为 AARSA 运作到登记其第一只外星人为止的时间。设 $G$ 为"第一个被登记的外星人是绿色"这一事件。设 $T_2$ 为 AARSA 运作到"两种族的外星人各至少有一只被登记"为止的时间。

**（a）**（4 分。）用 $\lambda_g$ 与 $\lambda_b$ 表示 $\mu_1=E[T_1]$。请写出求解过程。

答案（Answer）：$\displaystyle\mu_1=E[T_1]=\frac{1}{\lambda_g+\lambda_b}$

> <span style="color:#2471a3;">[solution]</span> 我们考虑两类外星人到达的过程。这是一个到达率为 $\lambda_g+\lambda_b$ 的合并泊松过程（merged Poisson process）。$T_1$ 是直到首次到达为止的时间，因此服从参数为 $\lambda_g+\lambda_b$ 的指数分布。故 $\mu_1=E[T_1]=\dfrac{1}{\lambda_g+\lambda_b}$。
>
> 也可以用导出分布（derived distributions）的方法来做：由于 $T_1=\min(T_1^g,\,T_1^b)$，其中 $T_1^g$ 与 $T_1^b$ 分别是绿色与蓝色外星人的首次到达时间（即 $T_1^g$、$T_1^b$ 分别服从参数为 $\lambda_g$、$\lambda_b$ 的指数分布）。

**（b）**（4 分。）用 $\lambda_g$ 与 $\lambda_b$ 表示 $p=P(G)$。请写出求解过程。

答案（Answer）：$\displaystyle P(G)=\frac{\lambda_g}{\lambda_g+\lambda_b}$

> <span style="color:#2471a3;">[solution]</span> 考虑与前文相同的合并泊松过程，其到达率为 $\lambda_g+\lambda_b$。合并过程的任一特定到达，对应绿色外星人的概率为 $\dfrac{\lambda_g}{\lambda_g+\lambda_b}$，对应蓝色外星人的概率为 $\dfrac{\lambda_b}{\lambda_g+\lambda_b}$。题目所求即 $P(G)=\dfrac{\lambda_g}{\lambda_g+\lambda_b}$。

<!-- ===== PDF p9 ===== -->

**（c）**（4 分。）用 $\lambda_g$ 与 $\lambda_b$ 表示 $\mu_2=E[T_2]$。请写出求解过程。

答案（Answer）：

```math
\frac{1}{\lambda_g+\lambda_b}
+\frac{\lambda_g}{\lambda_g+\lambda_b}\cdot\frac{1}{\lambda_b}
+\frac{\lambda_b}{\lambda_g+\lambda_b}\cdot\frac{1}{\lambda_g}
```

> <span style="color:#2471a3;">[solution]</span> 直到"至少一只绿色与一只红色（red）外星人到达"的时间 $T_2$ 可以表示为 $T_2=\max(T_1^g,\,T_1^b)$，其中 $T_1^g$ 与 $T_1^b$ 分别是绿色与蓝色外星人的首次到达时间（即 $T_1^g$、$T_1^b$ 分别服从参数为 $\lambda_g$、$\lambda_b$ 的指数分布）。
>
> 第 1 只外星人到达之前的期望时间已在 (a) 中算得：$\mu_1=E[T_1]=\dfrac{1}{\lambda_g+\lambda_b}$。为计算其余的时间，只需按"第 1 只外星人是绿色（即事件 $G$）还是蓝色（事件 $G^c$）"进行条件化，并利用泊松过程的无记忆性（memoryless property），即
>
> ```math
> \begin{aligned}
> E[T_2]
> &=E[T_1]+P(G)\,E[\text{Time until first Blue arrives}\mid G]+P(G^c)\,E[\text{Time until first Green arrives}\mid G^c]\\
> &=E[T_1]+P(G)\,E[T_2^b]+(1-P(G))\,E[T_2^g]\\
> &=\frac{1}{\lambda_g+\lambda_b}
> +\frac{\lambda_g}{\lambda_g+\lambda_b}\cdot\frac{1}{\lambda_b}
> +\frac{\lambda_b}{\lambda_g+\lambda_b}\cdot\frac{1}{\lambda_g}.
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">[note] 译者注：上一行中间等式原文排印为 $E[T_2^b]$ 与 $E[T_2^g]$（下标为 2，经字形坐标核实）。按 (a) 中的记号体系（下标为到达序号、上标为种族），$T_1^b$、$T_1^g$ 才表示蓝/绿外星人的首次到达时间；且末行代入的数值 $1/\lambda_b$、$1/\lambda_g$ 正是首次到达时间的均值（若为第二次到达则应为 $2/\lambda_b$、$2/\lambda_g$）。故该处应为 $T_1^b$、$T_1^g$，疑为下标笔误；此处照原文排印译出。</span>
>
> <span style="color:#1e8449;">[note] 译者注：本段首句原文作 "one green and one red Aliens"（一绿一红外星人）；题目只定义了蓝（blue）、绿（green）两种族，"red"（红色）应为 "blue"（蓝色）之笔误，此处照原文译出。</span>

<!-- ===== PDF p10 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**（续）Problem 4–7**</span>

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4（共 18 分）**</span>

研究者 Jill 有意研究 "Dilicon Valley"（原文如此，应为 Silicon Valley，即硅谷）科技公司（technology firm）的就业状况。她以 $X_i$ 表示第 $i$ 家科技公司的雇员人数，并假设诸 $X_i$ 独立同分布（i.i.d.），均值为 $p$。为估计 $p$，Jill 随机走访 $n$ 家科技公司，观察这些公司的雇员人数。

<span style="color:#1e8449;">[note] 原文确实印作 "Dilicon Valley"，系 "Silicon Valley"（硅谷）的排印笔误，译文照实保留。</span>

**（a）（6 分。）** Jill 采用

```math
M_n = \frac{X_1 + \cdots + X_n}{n}
```

作为 $p$ 的估计量（estimator）。求 $x < p$ 时 $\mathbf{P}(M_n \le x)$ 在 $n \to \infty$ 下的极限；再求 $x > p$ 时 $\mathbf{P}(M_n \le x)$ 在 $n \to \infty$ 下的极限。请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 由于诸 $X_i$ 独立同分布，$M_n$ 依概率收敛（convergence in probability）到 $p$，即 $\lim_{n\to\infty}\mathbf{P}(|M_n - p| > \epsilon) = 0$，这意味着对一切 $\epsilon > 0$，有 $\lim_{n\to\infty}\mathbf{P}(M_n < p - \epsilon) = 0$ 与 $\lim_{n\to\infty}\mathbf{P}(M_n > p + \epsilon) = 0$。因此
>
> ```math
> \lim_{n\to\infty}\mathbf{P}(M_n \le x) =
> \begin{cases}
> 0, & x < p, \\
> 1, & x > p.
> \end{cases}
> ```

<span style="color:#1e8449;">[mathtip] "由于 $X_i$ 独立同分布，$M_n$ 依概率收敛到 $p$" 这一步用的正是弱大数定律（WLLN）。</span>

**（b）（6 分。）** 求 Jill 必须抽样的公司数 $n$ 的最小值，使得切比雪夫不等式（Chebyshev inequality）能给出保证 $\mathbf{P}(|M_n - p| \ge 0.5) \le 0.05$。假设 $\mathrm{var}(X_i) = v$，$v$ 为某常数。请把答案表示为 $v$ 的函数。请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 由于 $M_n$ 依概率收敛到 $p$，且 $\mathrm{var}(M_n) = \dfrac{n}{n^2}\cdot\mathrm{var}(X_i) = v/n$，由切比雪夫不等式得
>
> ```math
> \mathbf{P}(|M_n - p| \ge 0.5) \le \frac{\mathrm{var}(M_n)}{0.5^2} = \frac{v}{n\cdot 0.5^2} = 0.05
> ```
>
> $\Rightarrow\ n = 80v$。

<span style="color:#1e8449;">[mathtip] 末尾的 "$= 0.05$" 是令上界 $\frac{v}{n\cdot 0.5^2}$ 等于 $0.05$，解出最小的 $n = \frac{v}{0.5^2\cdot 0.05} = 80v$。</span>

<!-- ===== PDF p11 ===== -->

**（c）（6 分。）** 现在假设该研究者抽取 $n = 5000$ 家公司。试用中心极限定理（Central Limit Theorem, CLT）求概率

```math
\mathbf{P}(|M_{5000} - p| \ge 0.5)
```

的近似值。再次假设 $\mathrm{var}(X_i) = v$，$v$ 为某常数。答案需用 $v$ 与标准正态 CDF $\Phi$ 表示。请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 由 CLT，当 $n$ 充分大时，可用标准正态分布近似
>
> ```math
> \frac{\sum_{i=1}^{n} X_i - np}{\sqrt{nv}}
> ```
>
> 因而
>
> ```math
> \mathbf{P}(|M_{5000} - p| \ge 0.5)
> = P\left(\left|\frac{\sum_{i=1}^{n} X_i - np}{\sqrt{nv}}\right| \ge \frac{0.5\sqrt{n}}{\sqrt{v}}\right)
> = 2 - 2\Phi\left(\frac{0.5\sqrt{n}}{\sqrt{v}}\right),
> ```
>
> 其中 $n = 5000$。

<!-- ===== PDF p12 ===== -->

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5（共 12 分）**</span>

RandomView 窗户工厂生产窗玻璃（window pane）。产品制造完成后，1000 块窗玻璃被装上一辆卡车。车上第 $i$ 块窗玻璃的重量 $W_i$（单位：磅）被建模为随机变量，并假设诸 $W_i$ 相互独立且同分布。

**（a）（6 分。）** 假设测得车上货载总重为 2340 磅，且 $\mathrm{var}(W_i) \le 4$。试用中心极限定理求 $\mu = E[W_i]$ 的近似 95% 置信区间（confidence interval）（可使用随试卷发放的标准正态分布表）。请写出计算过程。

**答案（Answer）：** $[2.216,\ 2.464]$

> <span style="color:#2471a3;">[solution]</span> **解：** 样本均值估计量 $\hat{\Theta}_n = \dfrac{W_1 + \cdots + W_n}{n}$ 在本例中为
>
> ```math
> \hat{\Theta}_{1000} = \frac{2340}{1000} = 2.34
> ```
>
> 利用正态分布表中的标准正态 CDF $\Phi(z)$，有 $\Phi(1.96) = 0.975$，于是得到
>
> ```math
> \mathbf{P}\left(\frac{|\hat{\Theta}_{1000} - \mu|}{\sqrt{\mathrm{var}(W_i)/1000}} \le 1.96\right) \approx 0.95.
> ```
>
> 由于方差小于 4，我们有
>
> ```math
> \mathbf{P}\left(|\hat{\Theta}_{1000} - \mu| \le 1.96\sqrt{\mathrm{var}(W_i)/1000}\right)
> \le
> \mathbf{P}\left(|\hat{\Theta}_{1000} - \mu| \le 1.96\sqrt{4/1000}\right),
> ```
>
> 令上式右端 $\approx 0.95$，即得到 95% 的置信度，也就是
>
> ```math
> \left[\hat{\Theta}_{1000} - 1.96\sqrt{\frac{4}{1000}},\ \hat{\Theta}_{1000} + 1.96\sqrt{\frac{4}{1000}}\right]
> = \left[\hat{\Theta}_{1000} - 0.124,\ \hat{\Theta}_{1000} + 0.124\right].
> ```

<span style="color:#1e8449;">[mathtip] 代入 $\hat{\Theta}_{1000} = 2.34$，得区间 $[2.34 - 0.124,\ 2.34 + 0.124] = [2.216,\ 2.464]$，与方框答案一致。</span>

<!-- ===== PDF p13 ===== -->

**（b）（6 分。）** 现在改设随机变量 $W_i$ 独立同分布，服从参数 $\theta > 0$ 的指数分布（exponential distribution），即其 PDF 为

```math
f_W(w;\theta) = \theta e^{-\theta w}
```

已知整卡车货物重 2340 磅，求 $\theta$ 的极大似然估计（maximum likelihood estimate）。请写出计算过程。

**答案（Answer）：** $\hat{\Theta}^{mle}_{1000} = \dfrac{1000}{2340} = 0.4274$

> <span style="color:#2471a3;">[solution]</span> **解：** 似然函数（likelihood function）为
>
> ```math
> f_W(w;\theta) = \prod_{i=1}^{n} f_{W_i}(w_i;\theta) = \prod_{i=1}^{n} \theta e^{-\theta w_i},
> ```
>
> 而对数似然函数（log-likelihood function）为
>
> ```math
> \log f_W(w;\theta) = n\log\theta - \theta\sum_{i=1}^{n} w_i.
> ```
>
> 它对 $\theta$ 的导数为 $\dfrac{n}{\theta} - \displaystyle\sum_{i=1}^{n} w_i$；令其为零，可见 $\log f_W(w;\theta)$ 在 $\theta \ge 0$ 上的最大值在 $\hat{\theta}_n = \dfrac{n}{\sum_{i=1}^{n} w_i}$ 处取得。由此得到的估计量为
>
> ```math
> \hat{\Theta}^{mle}_n = \frac{n}{\sum_{i=1}^{n} W_i}.
> ```
>
> 在本例中，
>
> ```math
> \hat{\Theta}^{mle}_{1000} = \frac{1000}{2340} = 0.4274
> ```

<!-- ===== PDF p14 ===== -->

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 6（共 21 分）**</span>

在爱丽丝的仙境（Alice's Wonderland）里，有六种不同的季节：秋天（Fall，F）、冬天（Winter，W）、春天（Spring，Sp）、夏天（Summer，Su）、苦寒（Bitter Cold，B）与金色阳光（Golden Sunshine，G）。这些季节并不按任何固定顺序更替；毋宁说，每天伊始，首席魔法师（Head Wizard）都会按照下面这个马尔可夫链（Markov chain）模型来指派当天的季节：

<span style="color:#7f8c8d;">【图】原页此处为马尔可夫链状态转移图（六个状态 F、W、Sp、Su、B、G；转移：F 自环 $2/3$，F→W $1/6$，F→G $1/6$；W 自环 $1/2$，W→F $1/5$，W→Sp $1/5$，W→G $1/10$；Sp→Su $1$；Su 自环 $1/4$，Su→Sp $1/2$，Su→B $1/4$；B 自环 $3/4$，B→Su $1/4$；G 自环 $1$）。原图由后处理统一插入。</span>

因此举例来说，若某天是秋天（F），则次日为冬天（W）的概率是 $1/6$（注意：次日也可能仍是同一季节）。

**（a）（4 分。）** 对上链中的每个状态，判断它是常返（recurrent）还是非常返（transient）。请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** $F$ 与 $W$ 是非常返状态；$Sp$、$Su$、$B$ 与 $G$ 是常返状态。

**（b）（4 分。）** 若周一为秋天（F），则同一周的周四是夏天（Su）的概率是多少？请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 三天之内从 $F$ 到 $Su$ 的路径只有一条。
>
> ```math
> \mathbf{P}(S_4 = \mathrm{Su} \mid S_1 = \mathrm{F})
> = \mathbf{P}(S_2 = \mathrm{W} \mid S_1 = \mathrm{F})\cdot\mathbf{P}(S_3 = \mathrm{Sp} \mid S_2 = \mathrm{W})\cdot\mathbf{P}(S_4 = \mathrm{Su} \mid S_3 = \mathrm{Sp})
> = \frac{1}{6}\cdot\frac{1}{5}\cdot 1 = \frac{1}{30}.
> ```

<!-- ===== PDF p15 ===== -->

**（c）（4 分。）** 若今天是春天（Sp），该链会收敛到平稳概率（steady-state probabilities）吗？若会，试计算每个状态的平稳概率；若不会，请解释这些概率为何不存在。请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 该马尔可夫链将留在常返类 $\{\mathrm{Sp}, \mathrm{Su}, \mathrm{B}\}$ 之中，并且
>
> ```math
> \begin{cases}
> \pi_{\mathrm{Sp}}\cdot 1 = \pi_{\mathrm{Su}}\cdot \dfrac{1}{2} \\[4pt]
> \pi_{\mathrm{B}}\cdot \dfrac{1}{4} = \pi_{\mathrm{Su}}\cdot \dfrac{1}{4} \\[4pt]
> \pi_{\mathrm{F}} = 0 \\
> \pi_{\mathrm{W}} = 0 \\
> \pi_{\mathrm{G}} = 0 \\
> \pi_{\mathrm{F}} + \pi_{\mathrm{W}} + \pi_{\mathrm{G}} + \pi_{\mathrm{Sp}} + \pi_{\mathrm{Su}} + \pi_{\mathrm{B}} = 1
> \end{cases}
> ```
>
> $\Rightarrow\ \pi_{\mathrm{F}} = 0,\ \pi_{\mathrm{W}} = 0,\ \pi_{\mathrm{G}} = 0,\ \pi_{\mathrm{Sp}} = 1/5,\ \pi_{\mathrm{Su}} = 2/5,\ \pi_{\mathrm{B}} = 2/5$。

<span style="color:#1e8449;">[mathtip] 前两行即常返类内的平衡方程（balance equations）：$\pi_{\mathrm{Sp}} = \pi_{\mathrm{Su}}\cdot\frac{1}{2} + \pi_{\mathrm{B}}\cdot 0$（$Su\to Sp$ 的概率为 $\frac{1}{2}$，而 $B$ 不直接回到 $Sp$）；由 $\pi_{\mathrm{B}} = \pi_{\mathrm{Su}}\cdot\frac{1}{4} + \pi_{\mathrm{B}}\cdot\frac{3}{4}$ 移项即得 $\pi_{\mathrm{B}}\cdot\frac{1}{4} = \pi_{\mathrm{Su}}\cdot\frac{1}{4}$。</span>

**（d）（5 分。）** 若今天是秋天（F），"苦寒"（B）在未来永不到来的概率是多少？请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 设 $a_{\mathrm{F}}$ 与 $a_{\mathrm{W}}$ 分别为自秋天（F）、冬天（W）出发"苦寒永不到来"的概率。该事件等价于马尔可夫链最终进入 $G$。
>
> ```math
> \begin{cases}
> a_{\mathrm{F}} = \dfrac{2}{3}\cdot a_{\mathrm{F}} + \dfrac{1}{6}\cdot a_{\mathrm{W}} + \dfrac{1}{6}\cdot 1 \\[6pt]
> a_{\mathrm{W}} = \dfrac{1}{5}\cdot a_{\mathrm{F}} + \dfrac{1}{2}\cdot a_{\mathrm{W}} + \dfrac{1}{10}\cdot 1
> \end{cases}
> ```
>
> $\Rightarrow\ a_{\mathrm{F}} = 3/4$。

<span style="color:#1e8449;">[mathtip] 两式中省略了进入 $\{\mathrm{Sp}, \mathrm{Su}, \mathrm{B}\}$ 的转移项：该类是有限闭常返类，从其中任一状态出发苦寒 $B$ 终将被访问（相应概率项取 $0$）；而一旦进入吸收态 $G$，苦寒永不到来（相应项取 $1$）。</span>

<!-- ===== PDF p16 ===== -->

**（e）（5 分。）** 若今天是秋天（F），直到夏天（Su）或金色阳光（G）首次到来所需的期望天数是多少？请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 设 $\mu_{\mathrm{F}}$ 与 $\mu_{\mathrm{W}}$ 分别为自秋天（F）、冬天（W）出发，直到夏天（Su）或金色阳光（G）首次到来所需的期望天数。
>
> ```math
> \begin{cases}
> \mu_{\mathrm{F}} = 1 + \dfrac{2}{3}\cdot\mu_{\mathrm{F}} + \dfrac{1}{6}\cdot\mu_{\mathrm{W}} + \dfrac{1}{6}\cdot 0 \\[6pt]
> \mu_{\mathrm{W}} = 1 + \dfrac{1}{5}\cdot\mu_{\mathrm{F}} + \dfrac{1}{2}\cdot\mu_{\mathrm{W}} + \dfrac{1}{5}\cdot 1
> \end{cases}
> ```
>
> $\Rightarrow\ \mu_{\mathrm{F}} = 5.25$。

<span style="color:#1e8449;">[mathtip] 第二式末项 $\frac{1}{5}\cdot 1$ 对应转移 $W \to Sp$：由图知 $Sp \to Su$ 的概率为 $1$，故从 $Sp$ 出发恰好再过 1 天到达夏天，即 $\mu_{\mathrm{Sp}} = 1$；而 $W \to G$（概率 $\frac{1}{10}$）一项因目标已达而取 $0$，故省略。</span>

<!-- ===== PDF p17 ===== -->

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 7（共 12 分）**</span>

一则报道 Sed Rox 与 Y Nakee 棒球决赛的新闻广播，恰在向听众播报 Y Nakee 是否赢得比赛的关键时刻变得嘈杂失真。

<span style="color:#1e8449;">[note] "Sed Rox" 与 "Y Nakee" 是影射棒球队 Red Sox（红袜）与 Yankees（洋基）的谐趣写法，照原文保留。</span>

设参数 $a$ 表示真实赛果：若 Y Nakee 获胜则 $a = 1$，否则 $a = -1$。共有 $n$ 位听众收听这档广播。设 $Y_i$ 为第 $i$ 位听众（$1 \le i \le n$）接收到的信息。在嘈杂广播下，$Y_i = a$ 的概率为 $p$，$Y_i = -a$ 的概率为 $1 - p$。假设诸随机变量 $Y_i$ 相互独立。

听众们作为一个群体，给出了一个联合估计量（joint estimator）：

```math
Z_n =
\begin{cases}
1, & \text{若 } \sum_{i=1}^{n} Y_i \ge 0, \\
-1, & \text{否则}.
\end{cases}
```

**（a）（6 分。）** 设 $p > 0.5$ 且 $a = 1$，求 $\lim_{n\to\infty}\mathbf{P}(Z_n = a)$。请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 注意到
>
> ```math
> \lim_{n\to\infty}\mathbf{P}(Z_n = 1)
> = \lim_{n\to\infty}\mathbf{P}\left(\sum_{i=1}^{n} Y_i \ge 0\right)
> = \lim_{n\to\infty}\mathbf{P}\left(\frac{\sum_{i=1}^{n} Y_i}{n} \ge 0\right).
> ```
>
> 由于诸 $Y_i$ 独立同分布，均值 $\mathbf{E}[Y_i] = 2p - 1$，方差 $\mathrm{var}(Y_i) = 1 - (2p-1)^2$ 有限，故由切比雪夫不等式，对一切 $\epsilon > 0$ 有
>
> ```math
> \lim_{n\to\infty}\mathbf{P}\left(\left|\frac{\sum_{i=1}^{n} Y_i}{n} - (2p-1)\right| \ge \epsilon\right) = 0.
> ```
>
> 取 $\epsilon = p - \dfrac{1}{2}$，上式即意味着 $\lim_{n\to\infty}\mathbf{P}\left(\dfrac{\sum_{i=1}^{n} Y_i}{n} \le (2p-1)/2\right) = 0$。因此，
>
> ```math
> \lim_{n\to\infty}\mathbf{P}(Z_n = 1) = 1.
> ```

**（b）（6 分。）** 设 $p = 0.5$ 且 $a = 1$，求 $\lim_{n\to\infty}\mathbf{P}(Z_n = a)$。请写出计算过程。

> <span style="color:#2471a3;">[solution]</span> **解：** 注意到
>
> ```math
> \lim_{n\to\infty}\mathbf{P}(Z_n = 1)
> = \lim_{n\to\infty}\mathbf{P}\left(\sum_{i=1}^{n} Y_i \ge 0\right)
> = \lim_{n\to\infty}\mathbf{P}\left(\frac{\sum_{i=1}^{n} Y_i}{\sqrt{n}} \ge 0\right).
> ```
>
> 由于诸 $Y_i$ 独立同分布，$\mathbf{E}[Y_i] = 0$、$\mathrm{var}(Y_i) = 1$，当 $n \to \infty$ 时可将 $\dfrac{\sum_{i=1}^{n} Y_i}{\sqrt{n}}$ 近似视为标准正态（standard normal）随机变量。因此，$\lim_{n\to\infty}\mathbf{P}(Z_n = 1) = 1/2$。

<!-- ===== PDF p18 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431　概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability）　Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关引用这些材料的信息或使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms</span>
