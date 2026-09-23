<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Final Exam 解答（Fall 2009）**</span> <span style="color:#7f8c8d;">（Final Solutions，解答日期：2009 年 12 月 15 日）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）</span>

<span style="color:#7f8c8d;">**[note]** 译者注：本解答册正文共 7 页，从 Problem 2 开始（试卷中的 Problem 1 仅为在答题册封面填写姓名与评阅信息，不设解答内容）。原文件只含解答、不含题干，题干请参见同课程发布的 Fall 2009 期末试卷原件；各题标题下的灰色说明为译者依据试卷原文补注，非解答原文。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2（20 points，20 分）**</span>

<span style="color:#7f8c8d;">题干背景（见试卷原件）：一对联合连续的随机变量 $X$ 与 $Y$，其联合概率密度函数（joint PDF）在图 1 的阴影区域上为常数 $c$、其余处为 $0$。解答用到：阴影区域面积为 $1/2$，且该联合 PDF 关于区域对称。</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)（5 points，5 分）**
>
> 由题设，联合 PDF 在阴影区域内为常数；由于 PDF 必须积分为 $1$，该常数必等于区域面积的倒数。因此
>
> ```math
> c=\frac{1}{1/2}=2.
> ```

> **(b)（5 points，5 分）**
>
> $X$ 与 $Y$ 的边缘 PDF（marginal PDF）可分别通过对联合 PDF 沿所有可能的 $y$ 值、$x$ 值积分得到。求 $X$ 的边缘 PDF 时，取定某个 $x$，并在 $X=x$ 处的竖直"切片"上对所有可能的 $y$ 值积分。由于联合 PDF 是常数，该积分简化为联合 PDF 乘以"切片"的宽度。因为对任意 $x\in[0,1]$，切片宽度恒为 $1/2$，所以 $X$ 的边缘 PDF 在该区间上均匀分布（uniform）：
>
> ```math
> f_X(x)=\begin{cases}1,&0\le x\le 1,\\[2pt]0,&\text{其他。}\end{cases}
> ```
>
> 由于联合 PDF 对称，$Y$ 的边缘 PDF 也是均匀的：
>
> ```math
> f_Y(y)=\begin{cases}1,&0\le y\le 1,\\[2pt]0,&\text{其他。}\end{cases}
> ```

> **(c)（5 points，5 分）**
>
> 为求条件期望（conditional expectation）与条件方差（conditional variance），先要确定在 $Y=1/4$ 条件下的条件分布。在 $Y=1/4$ 处对这个均匀的联合 PDF 作水平切片，得到 $x\in[1/4,\,3/4]$ 上的均匀分布。于是
>
> ```math
> \begin{aligned}
> E[X\mid Y=1/4]&=\frac{1}{2},\\
> \mathrm{var}(X\mid Y=1/4)&=\frac{(1/2)^{2}}{12}=\frac{1}{48}.
> \end{aligned}
> ```

> **(d)（5 points，5 分）**
>
> 在 $Y=3/4$ 处对联合 PDF 作水平切片，切片在 $x\in[0,\,1/4]\cup[3/4,\,1]$ 上非零。由于联合 PDF 是均匀的，该切片在其非零范围（即 $(x,y)$ 落在阴影区域内的范围）内也均匀。因此 $X$ 的条件 PDF（conditional PDF）为
>
> ```math
> f_{X|Y}(x\mid 3/4)=\begin{cases}2,&x\in[0,\,1/4]\cup[3/4,\,1],\\[2pt]0,&\text{其他。}\end{cases}
> ```

---

<!-- ===== PDF p2 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3（25 points，25 分）**</span>

<span style="color:#7f8c8d;">题干背景（见试卷原件）：四状态马尔可夫链（Markov chain）$X_n$，一步转移概率由状态转移图给出——自状态 1 依次以 $1/4,\,1/4,\,1/3,\,1/6$ 转到状态 $1,2,3,4$；自状态 2 以 $1/3,\,1/3,\,1/3$ 转到状态 $1,3,4$（留在状态 2 的概率为 $0$）；状态 3、4 均为吸收态（absorbing states）。</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)（5 points，5 分）**
>
> 常返态（recurrent states）为 $\{3,4\}$。

> **(b)（5 points，5 分）**
>
> 从状态 2 到状态 4 的两步转移概率（2-step transition probability）可以通过枚举所有可能的路径序列求得。它们是 $\{2\to 1\to 4\}$ 与 $\{2\to 4\to 4\}$。于是
>
> ```math
> P(X_2=4\mid X_0=2)=\frac{1}{3\cdot 6}+\frac{1}{3\cdot 1}=\frac{7}{18}.
> ```

> **(c)（5 points，5 分）**
>
> 一般地，
>
> ```math
> r_{11}(n+1)=\sum_{j=1}^{4}p_{1j}\,r_{j1}(n).
> ```
>
> 由于状态 3 与状态 4 是吸收态，该表达式简化为
>
> ```math
> r_{11}(n+1)=\frac{1}{4}\,r_{11}(n)+\frac{1}{4}\,r_{21}(n).
> ```
>
> 或者，等价地，
>
> ```math
> r_{11}(n+1)=\sum_{k=1}^{4}r_{1k}(n)\,p_{k1}=r_{11}(n)\cdot\frac{1}{4}+r_{12}(n)\cdot\frac{1}{3}.
> ```

> **(d)（5 points，5 分）**
>
> 平稳概率（steady-state probabilities）不存在，因为常返类不止一个。长期状态概率将依赖于初始状态。

> **(e)（5 points，5 分）**
>
> 为求最终被状态 4 吸收的概率，我们建立吸收概率（absorption probabilities）方程。注意 $a_4=1$、$a_3=0$。
>
> ```math
> a_1=\frac{1}{4}a_1+\frac{1}{4}a_2+\frac{1}{3}a_3+\frac{1}{6}a_4=\frac{1}{4}a_1+\frac{1}{4}a_2+\frac{1}{6},
> ```
>
> ```math
> a_2=\frac{1}{3}a_1+\frac{1}{3}a_3+\frac{1}{3}a_4=\frac{1}{3}a_1+\frac{1}{3}.
> ```
>
> 解此方程组得 $a_1=3/8$。
>
> <span style="color:#1e8449;">**[note]** 译者注：该分数在原始提取文本中被竖排拆行误读作"8/3"；经原 PDF 坐标核对（分子 3 在上、分母 8 在下），并按方程组验算（$a_1=3/8<1$ 方能为概率），应为 $a_1=3/8$。</span>

---

<!-- ===== PDF p3 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4（30 points，30 分）**</span>

<span style="color:#7f8c8d;">题干背景（见试卷原件）：Al、Bonnie、Clyde 三人绕跑道跑圈，每人每圈时长（小时）分别服从参数 $\lambda_A=21$、$\lambda_B=23$、$\lambda_C=24$ 的指数分布，各圈时长相互独立；每圈结束后各以概率 $1/3$、$2/3$ 喝 1 杯或 2 杯水，与其他一切独立（包括此前各圈喝了多少水），喝水耗时忽略不计。</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)（5 points，5 分）**
>
> 根据题意，可以把 Al、Bonnie、Clyde 三人的跑步看作 3 个相互独立的泊松过程（Poisson processes），其中"到达"（arrival）对应各圈的完成，到达率（arrival rate）即每小时完成的圈数。由于三个过程相互独立，可以把它们合并（merge）成一个刻画三人全部完圈情况的新过程。该合并过程的到达率为 $\lambda_M=\lambda_A+\lambda_B+\lambda_C=68$。于是第一小时内完成的总圈数 $L$ 服从 $\lambda_M=68$、$\tau=1$ 的泊松 PMF（probability mass function，概率质量函数）：
>
> ```math
> p_L(\ell)=\begin{cases}\dfrac{e^{-68}\,68^{\ell}}{\ell!},&\ell=0,\,1,\,2,\,\ldots,\\[6pt]0,&\text{其他。}\end{cases}
> ```

> **(b)（5 points，5 分）**
>
> 设 $L$ 为第一小时内完成的总圈数，$C_i$ 为第 $i$ 圈结束时饮用的水杯数。则总饮水杯数为
>
> ```math
> C=\sum_{i=1}^{L}C_i,
> ```
>
> 这是"随机个"独立同分布（i.i.d.）随机变量之和。于是可以运用重复期望定律（law of iterated expectations）求得
>
> ```math
> E[C]=E\big[E[C\mid L]\big]=E[L\,C_i]=E[L]\,E[C_i]=(\lambda_M\tau)\cdot\Big(1\cdot\frac{1}{3}+2\cdot\frac{2}{3}\Big)=68\cdot\frac{5}{3}=\frac{340}{3}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 给定 $L$ 时，$E[C\mid L]=L\,E[C_i]$（$L$ 个 i.i.d. 杯数的公共期望），故 $E[C]=E\big[L\,E[C_i]\big]=E[L]\,E[C_i]$；原文把中间一步简写作 $E[L\,C_i]$。</span>

> **(c)（5 points，5 分）**
>
> 设 $X$ 为 72 圈中"喝 2 杯水"的那些圈的数目（即 72 圈中喝 2 杯的圈数）。要使他至少喝 130 杯，必须有
>
> ```math
> 1\cdot(72-X)+2\cdot X\ge 130,
> ```
>
> 由此可知需要 $X\ge 58$。
>
> 现设 $X_i$ 为独立同分布的伯努利（Bernoulli）随机变量：若 Al 第 $i$ 圈后喝 2 杯水则取 $1$，若喝 1 杯则取 $0$。则
>
> ```math
> X=X_1+X_2+\cdots+X_{72}.
> ```
>
> 显然 $X$ 是 $n=72$、$p=2/3$ 的二项（binomial）随机变量，所求概率为
>
> ```math
> P(X\ge 58)=\sum_{k=58}^{72}\binom{72}{k}\left(\frac{2}{3}\right)^{k}\left(\frac{1}{3}\right)^{72-k}.
> ```
>
> 该表达式难以直接计算；但由于这里处理的是较多个 i.i.d. 随机变量之和，可以借助中心极限定理（Central Limit Theorem）用正态分布来近似这一概率。特别地，可以把 $X$ 近似为

<!-- ===== PDF p4 ===== -->

> **（续）** 均值为 $np=72\cdot(2/3)=48$、方差为 $np(1-p)=16$ 的正态随机变量，并把所求概率近似为
>
> ```math
> P(X\ge 58)=1-P(X<58)\approx 1-\Phi\!\left(\frac{58-48}{\sqrt{16}}\right)=1-\Phi(2.5)\approx 0.0062.
> ```

> **(d)（5 points，5 分）**
>
> "Al 最先完成一圈"这一事件，等价于"合并过程的第一个到达来自 Al 的过程"这一事件。该概率为
>
> ```math
> \frac{\lambda_A}{\lambda_A+\lambda_B+\lambda_C}=\frac{21}{68}.
> ```

> **(e)（5 points，5 分）**
>
> 这是随机入射悖论（random incidence paradox）的一个实例：Al 当前这一圈的时长由两部分之和构成——从你到达时刻起，到 Al 下一次完成一圈为止的时长，加上从 Al 上一次完成一圈时刻起，到你到达时刻为止的时长。这是 2 个参数为 $\lambda_A=21$ 的独立指数（exponential）随机变量之和（即一个二阶 Erlang 随机变量，second-order Erlang random variable）：
>
> ```math
> f_T(t)=\begin{cases}21^{2}\,t\,e^{-21t},&t\ge 0,\\[2pt]0,&\text{其他。}\end{cases}
> ```

> **(f)（5 points，5 分）**
>
> 与上一小问类似，Al 第二圈的时长由两部分组成：从 $t=1/4$ 起到他完成第二圈为止的剩余时间，以及从他开始第二圈到 $t=1/4$ 为止已经过去的时间。设 $X$ 为已经过去的时间，$Y$ 为剩余时间。剩余时间 $Y$ 仍可建模为指数随机变量；但已经过去的时间 $X$ 不能再这样建模，因为我们知道 $X$ 不会超过 $1/4$，而指数随机变量可以取任意大的值。
>
> <span style="color:#1e8449;">**[mathtip]** 由指数分布的无记忆性（memorylessness），给定"时刻 $1/4$ 时正在跑第二圈"，到下一次完圈为止的剩余时长 $Y$ 仍服从同参数 $\text{Exponential}(21)$。</span>
>
> 为求 $X$ 的 PDF，先考虑其 CDF（cumulative distribution function，累积分布函数）：
>
> ```math
> P(X\le x)=P(\text{第 1 次到达发生在距时刻 }1/4\text{ 不足 }x\text{ 小时之前})
> ```
>
> ```math
> =\frac{P(\text{区间 }[1/4-x,\,1/4]\text{ 内恰有 1 次到达，且区间 }[0,\,1/4-x]\text{ 内无到达})}{P(\text{区间 }[0,\,1/4]\text{ 内恰有 1 次到达})}=\frac{P(1,\,x)\,P(0,\,1/4-x)}{P(1,\,1/4)}
> ```
>
> ```math
> =\frac{e^{-21x}(21x)\,e^{-21(1/4-x)}}{e^{-21/4}\,(21/4)}=\begin{cases}0,&x<0,\\[2pt]4x,&x\in[0,\,1/4],\\[2pt]1,&x>1/4.\end{cases}
> ```
>
> 因此 $X$ 在区间 $[0,\,1/4]$ 上均匀分布，其 PDF 为
>
> ```math
> f_X(x)=\begin{cases}4,&x\in[0,\,1/4],\\[2pt]0,&\text{其他。}\end{cases}
> ```

<!-- ===== PDF p5 ===== -->

> **（续）** 于是，Al 花在第二圈上的总时间为 $T=X+Y$。由于 $X$ 与 $Y$ 对应泊松过程中互不相交的时间区间，二者相互独立，因此可用卷积（convolution）求 $T$ 的 PDF：
>
> ```math
> \begin{aligned}
> f_T(t)&=\int_{-\infty}^{\infty}f_X(x)\,f_Y(t-x)\,dx=\int_{0}^{\min(1/4,\;t)}4\cdot 21\,e^{-21(t-x)}\,dx\\[2pt]
> &=\begin{cases}4e^{-21t}\left(e^{21\min(1/4,\;t)}-1\right),&t\ge 0,\\[2pt]0,&\text{其他。}\end{cases}
> \end{aligned}
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 5（25 points，25 分）**</span>

<span style="color:#7f8c8d;">题干背景（见试卷原件）：光脉冲能量 $X$ 为参数 $\lambda$ 的二阶 Erlang 随机变量，PDF 为 $f_X(x)=\lambda^{2}xe^{-\lambda x}$（$x\ge 0$）；理想光子计数器的输出 $N$ 在 $X=x$ 条件下服从均值为 $x$ 的泊松分布，即 $p_{N|X}(n\mid x)=x^{n}e^{-x}/n!$。第 (e) 小问改用离散先验 $P(X=2)=3^{3}/35$、$P(X=3)=2^{3}/35$。</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)（5 points，5 分）**
>
> 运用重复期望定律与全方差定律（law of total variance）：
>
> ```math
> E[N]=E\big[E[N\mid X]\big]=E[X]=\frac{2}{\lambda},
> ```
>
> ```math
> \mathrm{var}(N)=E\big[\mathrm{var}(N\mid X)\big]+\mathrm{var}\big(E[N\mid X]\big)=E[X]+\mathrm{var}(X)=\frac{2}{\lambda}+\frac{2}{\lambda^{2}},
> ```
>
> 其中 $\mathrm{var}(N\mid X)=E[N\mid X]=X$。

> **(b)（5 points，5 分）**
>
> ```math
> p_N(n)=\int f_X(x)\,p_{N|X}(n\mid x)\,dx=\int_{x=0}^{\infty}\frac{\lambda^{2}}{n!}\,x^{n+1}e^{-(1+\lambda)x}\,dx=\frac{\lambda^{2}}{n!}\cdot\frac{(n+1)!}{(1+\lambda)^{n+2}}
> ```
>
> ```math
> =\begin{cases}\dfrac{\lambda^{2}(n+1)}{(1+\lambda)^{n+2}},&n=0,\,1,\,2,\,\ldots,\\[6pt]0,&\text{其他。}\end{cases}
> ```

> **(c)（5 points，5 分）**
>
> 基于对 $N$ 的观测所得 $X$ 的线性最小二乘估计量（linear least-squares estimator）$\hat{X}_{lin}(N)$ 的公式为
>
> ```math
> \hat{X}_{lin}(N)=E[X]+\frac{\mathrm{cov}(X,N)}{\mathrm{var}(N)}\big(N-E(N)\big).
> ```

<!-- ===== PDF p6 ===== -->

> **（续）** 唯一未知的量是 $\mathrm{cov}(X,N)=E[XN]-E[X]E[N]=E[XN]-(E[X])^{2}$。再次运用重复期望定律：
>
> ```math
> E[XN]=E\big[E[XN\mid X]\big]=E\big[X\,E[N\mid X]\big]=E[X^{2}]=\mathrm{var}(X)+(E[X])^{2}=\frac{6}{\lambda^{2}}.
> ```
>
> 因此 $\mathrm{cov}(X,N)=6/\lambda^{2}-4/\lambda^{2}=2/\lambda^{2}$。将此结果与 (a) 中的结果结合：
>
> ```math
> \hat{X}_{lin}(N)=\frac{2}{\lambda}+\frac{2/\lambda^{2}}{2/\lambda+2/\lambda^{2}}\left(N-\frac{2}{\lambda}\right)=\frac{2+N}{1+\lambda}.
> ```

> **(d)（5 points，5 分）**
>
> 基于对 $N$ 的观测所得 $X$ 的最大后验（MAP）估计量（MAP estimator）$\hat{X}_{MAP}(N)$ 的表达式为
>
> ```math
> \begin{aligned}
> \hat{X}_{MAP}(N)&=\arg\max_{x}\ f_{X|N}(x\mid n)=\arg\max_{x}\ \frac{f_X(x)\,p_{N|X}(n\mid x)}{p_N(n)}\\[2pt]
> &=\arg\max_{x}\ f_X(x)\,p_{N|X}(n\mid x)=\arg\max_{x}\ \frac{\lambda^{2}}{n!}\,x^{n+1}e^{-(1+\lambda)x}=\arg\max_{x}\ x^{n+1}e^{-(1+\lambda)x},
> \end{aligned}
> ```
>
> 其中第三个等号成立是因为 $p_N(n)$ 不依赖于 $x$，最后一个等号成立是因为删去了所有不依赖于 $x$ 的量。最大值点可通过求导求得，结果为：
>
> ```math
> \hat{X}_{MAP}(N)=\frac{1+N}{1+\lambda}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 求导：$\dfrac{d}{dx}\big[x^{n+1}e^{-(1+\lambda)x}\big]=x^{n}e^{-(1+\lambda)x}\big[(n+1)-(1+\lambda)x\big]$，驻点为 $x=\dfrac{n+1}{1+\lambda}$。</span>
>
> 这是 $x\in[0,\infty)$ 范围内唯一的局部极值点。此外，$f_{X|N}(x\mid n)$ 在 $x=0$ 处等于 $0$，当 $x\to\infty$ 时趋于 $0$，且在其余处恒大于 $0$。因此可以断定 $\hat{X}_{MAP}(N)$ 确实是最大值点。

> **(e)（5 points，5 分）**
>
> 为使出错概率最小，我们选择后验概率（posterior probability）较大的那个假设。

<!-- ===== PDF p7 ===== -->

> **（续）** 我们将选择假设 $X=2$，如果
>
> ```math
> \begin{aligned}
> &P(X=2\mid N=3)>P(X=3\mid N=3)\\[2pt]
> &\frac{P(X=2)\,P(N=3\mid X=2)}{P(N=3)}>\frac{P(X=3)\,P(N=3\mid X=3)}{P(N=3)}\\[2pt]
> &P(X=2)\,P(N=3\mid X=2)>P(X=3)\,P(N=3\mid X=3)\\[2pt]
> &\frac{3^{3}}{35}\cdot\frac{2^{3}e^{-2}}{3!}>\frac{2^{3}}{35}\cdot\frac{3^{3}e^{-3}}{3!}\\[2pt]
> &e^{-2}>e^{-3}.
> \end{aligned}
> ```
>
> 该不等式成立，因此我们选择 $X=2$ 这一假设，以使出错概率最小。
>
> <span style="color:#1e8449;">**[note]** 译者注：原始 PDF 文本提取会把上标拉平，两先验在提取文本中形如"33/35、23/35"；经与原考题（(e) 小问明确给出先验）及字号坐标核对，应为 $P(X=2)=3^{3}/35=27/35$、$P(X=3)=2^{3}/35=8/35$（$27/35+8/35=1$）。又因不等式两边的公共因子 $\dfrac{3^{3}\cdot 2^{3}}{35\cdot 3!}=\dfrac{36}{35}$ 恰好相消，最后一步才归约为 $e^{-2}>e^{-3}$。</span>

<!-- ===== PDF p8 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability）　Fall 2010</span>

<span style="color:#7f8c8d;">如需了解这些材料的引用方式或使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>

<span style="color:#7f8c8d;">**[note]** 译者注：本页为 MIT OpenCourseWare 标准尾页（OCW 发布课程版本标注为 Fall 2010），非试卷内容。</span>
