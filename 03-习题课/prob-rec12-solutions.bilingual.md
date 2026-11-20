<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 12 解答（Recitation 12: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；October 19, 2010，2010 年 10 月 19 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1（第 1 题）**</span>

<span style="color:#7f8c8d;">[note] 本解答 PDF 未附原题面。由解答可知题设为：设 $X$、$Y$ 为随机变量，$a$、$b$ 为常数（$a\neq 0$），证明相关系数在平移与缩放变换下不变：$\rho(aX+b,\,Y)=\rho(X,\,Y)$。</span>

> <span style="color:#2471a3;">[solution]</span>
>
> ```math
> \rho(aX+b,\,Y)=\frac{\mathrm{cov}(aX+b,\,Y)}{\sqrt{\mathrm{var}(aX+b)\,\mathrm{var}(Y)}}
> =\frac{E[(aX+b-E[aX+b])(Y-E[Y])]}{\sqrt{a^2\,\mathrm{var}(X)\,\mathrm{var}(Y)}}
> =\frac{E[(aX+b-aE[X]-b)(Y-E[Y])]}{\sqrt{a^2\,\mathrm{var}(X)\,\mathrm{var}(Y)}}
> ```
>
> ```math
> =\frac{aE[(X-E[X])(Y-E[Y])]}{a\sqrt{\mathrm{var}(X)\,\mathrm{var}(Y)}}
> =\frac{\mathrm{cov}(X,\,Y)}{\sqrt{\mathrm{var}(X)\,\mathrm{var}(Y)}}
> =\rho(X,\,Y).
> ```
>
> <span style="color:#1e8449;">[mathtip]</span> 严格地说 $\sqrt{a^2}=|a|$：当 $a>0$ 时 $\rho(aX+b,Y)=\rho(X,Y)$；当 $a<0$ 时相关系数会变号。这里相关系数 $\rho(X,Y)$ 定义为 $\rho(X,Y)=\dfrac{\mathrm{cov}(X,Y)}{\sqrt{\mathrm{var}(X)\,\mathrm{var}(Y)}}$，即协方差除以两者标准差之积。
>
> 作为相关系数（correlation coefficient）这一性质的一个应用实例，考虑一个班级里学生的作业（homework）成绩与考试（exam）成绩。我们预期两者正相关（positively correlated），因而相关系数为正。注意，在此例中，上述性质意味着：无论考试以 105 分、10 分还是任何其他分数为满分，相关系数都不会改变。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#7f8c8d;">**Problem 2（第 2 题）**</span>

<span style="color:#7f8c8d;">[note] 本解答 PDF 未附原题面。由解答可知题设为：$X$ 与 $Y$ 相互独立，均服从参数为 $\lambda$ 的指数分布（exponential distribution）；令 $Z=X-Y$，求 $Z$ 的 CDF 与 PDF。</span>

> <span style="color:#2471a3;">[solution]</span> **(a)** 当 $z\ge 0$ 时：
>
> ```math
> F_Z(z)=P(X-Y\le z)=P(X\le Y+z)
> =\int_0^\infty\int_0^{y+z}f_{X,Y}(x,\,y)\,dx\,dy
> =\int_0^\infty\int_0^{y+z}\lambda e^{-\lambda x}\,\lambda e^{-\lambda y}\,dx\,dy
> ```
>
> 这里利用了 $X$ 与 $Y$ 相互独立，故联合密度 $f_{X,Y}(x,y)=f_X(x)\,f_Y(y)=\lambda e^{-\lambda x}\cdot\lambda e^{-\lambda y}$（$x\ge 0,\ y\ge 0$）。由于 $z\ge 0$，内层积分上限 $y+z\ge y\ge 0$，积分区域没有问题。
>
> ```math
> =\int_0^\infty\lambda e^{-\lambda y}\big(1-e^{-\lambda(y+z)}\big)\,dy
> =\Big[-e^{-\lambda y}+\frac{e^{-\lambda z}}{2}\,e^{-2\lambda y}\Big]_{y=0}^{y=\infty}
> =1-\frac{1}{2}e^{-\lambda z},\qquad z\ge 0.
> ```

<!-- ===== PDF p2 ===== -->

**（续）**

> <span style="color:#2471a3;">[solution]</span>（续）当 $z<0$ 时：
>
> ```math
> P(X\le Y+z)=\int_0^\infty\int_0^{y+z}f_{X,Y}(x,\,y)\,dx\,dy
> =\int_0^\infty\int_{x-z}^{\infty}\lambda e^{-\lambda x}\,\lambda e^{-\lambda y}\,dy\,dx
> ```
>
> 注意此时 $z<0$，若仍按"先对 $x$、后对 $y$"积分，内层上限 $y+z$ 在 $0\le y<-z$ 时会小于 $0$，导致积分区间越界。因此这里先交换积分次序（interchange the order of integration）：原积分区域是 $\{(x,y):x\ge 0,\ y\ge 0,\ x\le y+z\}$，固定 $x$ 后 $y$ 的范围是 $y\ge x-z$（且 $x-z\ge 0$ 自动满足，$y\ge 0$ 的约束已被覆盖），于是得到上式。
>
> ```math
> =\int_0^\infty\lambda e^{-\lambda x}\,e^{-\lambda(x-z)}\,dx
> =e^{\lambda z}\int_0^\infty\lambda e^{-2\lambda x}\,dx
> =\frac{1}{2}e^{\lambda z},\qquad z\le 0.
> ```
>
> 因此，
>
> ```math
> F_Z(z)=\begin{cases}1-\dfrac{1}{2}e^{-\lambda z}, & z\ge 0,\\[2mm] \dfrac{1}{2}e^{\lambda z}, & z<0,\end{cases}
> \qquad
> f_Z(z)=\frac{d}{dz}F_Z(z)=\begin{cases}\dfrac{\lambda}{2}e^{-\lambda z}, & z\ge 0,\\[2mm] \dfrac{\lambda}{2}e^{\lambda z}, & z<0.\end{cases}
> ```
>
> 从而
>
> ```math
> f_Z(z)=\frac{\lambda}{2}e^{-\lambda|z|}.
> ```
>
> 这个分布就是著名的 Laplace 分布（Laplace distribution，亦称 double exponential distribution，双指数分布）在中心（均值为 $0$）情形下的形式。
>
> **(b)** 用全概率定理（total probability theorem）求解，有：
>
> ```math
> f_Z(z)=\int_{-\infty}^{\infty}f_X(x)\,f_{Z|X}(z\mid x)\,dx
> =\int_{-\infty}^{\infty}f_X(x)\,f_{Y|X}(x-z\mid x)\,dx
> =\int_{-\infty}^{\infty}f_X(x)\,f_Y(x-z)\,dx.
> ```
>
> 这里第二、三步用到：在给定 $X=x$ 的条件下，$Z=X-Y=x-Y$，故 $f_{Z|X}(z\mid x)=f_Y(x-z)$（把 $Z$ 的密度在 $z$ 处的取值换算成 $Y$ 的密度在 $x-z$ 处的取值）；又因 $X$、$Y$ 独立，$f_{Y|X}=f_Y$。
>
> 先看 $z<0$ 的情形：
>
> ```math
> \int_{-\infty}^{\infty}f_X(x)\,f_Y(x-z)\,dx
> =\int_0^{\infty}\lambda e^{-\lambda x}\,\lambda e^{-\lambda(x-z)}\,dx
> =\lambda e^{\lambda z}\int_0^{\infty}\lambda e^{-2\lambda x}\,dx
> =\frac{\lambda}{2}e^{\lambda z}.
> ```

<!-- ===== PDF p3 ===== -->

**（续）**

> <span style="color:#2471a3;">[solution]</span>（续）再看 $z\ge 0$ 的情形：
>
> ```math
> \int_{-\infty}^{\infty}f_X(x)\,f_Y(x-z)\,dx
> =\int_z^{\infty}\lambda e^{-\lambda x}\,\lambda e^{-\lambda(x-z)}\,dx
> =\lambda e^{\lambda z}\int_z^{\infty}\lambda e^{-2\lambda x}\,dx
> =\frac{\lambda}{2}e^{\lambda z}e^{-2\lambda z}
> =\frac{\lambda}{2}e^{-\lambda z}.
> ```
>
> 这里积分下限从 $-\infty$ 换成 $z$，是因为 $f_Y(x-z)=\lambda e^{-\lambda(x-z)}$ 只有在 $x-z\ge 0$（即 $x\ge z$）时非零，而 $f_X(x)$ 在 $x\ge 0$ 时非零；二者取交集，当 $z\ge 0$ 时即为 $x\ge z$。
>
> ```math
> f_Z(z)=\frac{\lambda}{2}e^{-\lambda|z|}\qquad\forall z.
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3（第 3 题）**</span>

<span style="color:#7f8c8d;">[note] 本解答 PDF 未附原题面。由解答可知题设为：$X$、$Y$ 相互独立且均服从标准正态分布；改用极坐标表示 $X=R\cos\Theta$、$Y=R\sin\Theta$（$R\ge 0$，$\Theta\in[0,2\pi)$），求 $R$ 与 $\Theta$ 的（联合）分布。</span>

> <span style="color:#2471a3;">[solution]</span> **(a)** 我们有 $X=R\cos(\Theta)$、$Y=R\sin(\Theta)$。回顾极坐标（polar coordinates）中微分面积元为 $dA=dx\,dy=r\,dr\,d\theta$。于是
>
> ```math
> F_R(r)=P(R\le r)=\int_0^r\int_0^{2\pi}f_X(r'\cos\theta)\,f_Y(r'\sin\theta)\,d\theta\;r'\,dr'
> =\int_0^r\int_0^{2\pi}\frac{1}{2\pi}\,e^{-(r')^2/2}\,d\theta\;r'\,dr'
> ```
>
> 第一行到第二行的关键：因为 $X$、$Y$ 相互独立且均服从标准正态分布，联合密度 $f_{X,Y}(x,y)=f_X(x)f_Y(y)=\dfrac{1}{\sqrt{2\pi}}e^{-x^2/2}\cdot\dfrac{1}{\sqrt{2\pi}}e^{-y^2/2}=\dfrac{1}{2\pi}e^{-(x^2+y^2)/2}$。代入 $x=r'\cos\theta,\ y=r'\sin\theta$ 后，$x^2+y^2=(r')^2$，故被积函数为 $\dfrac{1}{2\pi}e^{-(r')^2/2}$。而 $dx\,dy=r'\,dr'\,d\theta$ 中的因子 $r'$ 正是极坐标变换的雅可比行列式（Jacobian determinant）。
>
> ```math
> =\frac{1}{2\pi}\int_0^{2\pi}d\theta\int_0^r r'e^{-(r')^2/2}\,dr'
> =\int_0^{r^2/2}e^{-u}\,du\qquad\big(u=(r')^2/2\big)
> ```
>
> 换元 $u=(r')^2/2$，则 $du=r'\,dr'$；当 $r'$ 从 $0$ 变到 $r$ 时，$u$ 从 $0$ 变到 $r^2/2$，且 $\dfrac{1}{2\pi}\int_0^{2\pi}d\theta=\dfrac{1}{2\pi}\cdot 2\pi=1$，故上式成立。
>
> ```math
> F_R(r)=\begin{cases}1-e^{-r^2/2}, & r\ge 0,\\ 0, & r<0,\end{cases}
> \qquad
> f_R(r)=\frac{d}{dr}F_R(r)=\big(-1/2\big)(2r)\big(-e^{-r^2/2}\big)=r\,e^{-r^2/2},\quad r\ge 0.
> ```

<!-- ===== PDF p4 ===== -->

**（续）**

> <span style="color:#2471a3;">[solution]</span>（续）**(b)**
>
> ```math
> F_\Theta(\theta)=P(\Theta\le\theta)=\int_0^\theta\int_0^\infty f_X(r\cos\theta')\,f_Y(r\sin\theta')\,r\,dr\,d\theta'
> =\int_0^\theta\int_0^\infty\frac{1}{2\pi}\,e^{-r^2/2}\,r\,dr\,d\theta'
> ```
>
> ```math
> =\frac{\theta}{2\pi}\int_0^\infty r\,e^{-r^2/2}\,dr
> =\frac{\theta}{2\pi}\int_0^\infty e^{-u}\,du\qquad\big(u=r^2/2\big)
> =\frac{\theta}{2\pi}\Big[-e^{-u}\Big]_0^\infty=\frac{\theta}{2\pi},\qquad 0\le\theta\le 2\pi.
> ```
>
> 换元 $u=r^2/2$，则 $du=r\,dr$；当 $r$ 从 $0$ 变到 $\infty$ 时，$u$ 从 $0$ 变到 $\infty$。
>
> ```math
> F_\Theta(\theta)=\begin{cases}0, & \theta<0,\\[1mm] \dfrac{\theta}{2\pi}, & 0\le\theta\le 2\pi,\\[2mm] 1, & \theta\ge 2\pi,\end{cases}
> \qquad
> f_\Theta(\theta)=\frac{d}{d\theta}F_\Theta(\theta)=\frac{1}{2\pi},\qquad 0\le\theta\le 2\pi.
> ```
>
> 即 $\Theta$ 服从 $[0,2\pi]$ 上的均匀分布（uniform distribution）。
>
> **(c)**
>
> ```math
> F_{R,\Theta}(r,\theta)=P(R\le r,\,\Theta\le\theta)
> =\int_0^\theta\int_0^r\frac{1}{2\pi}\,r'\,e^{-(r')^2/2}\,dr'\,d\theta'
> =\int_0^\theta\int_0^{r^2/2}\frac{1}{2\pi}\,e^{-u}\,du\,d\theta'\qquad\big(u=(r')^2/2\big)
> ```
>
> ```math
> =\int_0^\theta\frac{1}{2\pi}\big(1-e^{-r^2/2}\big)\,d\theta'
> =\frac{\theta}{2\pi}\big(1-e^{-r^2/2}\big),\qquad r\ge 0,\;\;0\le\theta\le 2\pi.
> ```
>
> ```math
> F_{R,\Theta}(r,\theta)=\begin{cases}\dfrac{\theta}{2\pi}\big(1-e^{-r^2/2}\big), & r\ge 0,\;\;0\le\theta\le 2\pi,\\[2mm] 1-e^{-r^2/2}, & r\ge 0,\;\;\theta>2\pi,\\[1mm] 0, & \text{otherwise},\end{cases}
> ```
>
> ```math
> f_{R,\Theta}(r,\theta)=\frac{\partial^2}{\partial r\,\partial\theta}\,F_{R,\Theta}(r,\theta)=\frac{1}{2\pi}\,r\,e^{-r^2/2},\qquad r\ge 0,\;\;0\le\theta\le 2\pi.
> ```
>
> 注意 $f_{R,\Theta}(r,\theta)=f_R(r)\,f_\Theta(\theta)=\big(r\,e^{-r^2/2}\big)\cdot\dfrac{1}{2\pi}$，这说明 $R$ 与 $\Theta$ 相互独立。
>
> 注意：$R^2$ 服从参数 $\lambda=1/2$ 的指数分布。这是一种由相互独立的均匀（uniform）随机变量与指数随机变量生成正态（normal）随机变量的非常便利的方法（这一方法的标准名称为 Box–Muller 变换，Box–Muller transform）。要生成具有任意 CDF $F_X$ 的随机变量 $X$，可以先生成均匀随机变量，再把均匀分布的样本通过函数 $F_X^{-1}$（这就是逆变换法，inverse transform method）。但由于正态随机变量的 CDF 没有闭式（closed-form）表达式，这一方法行不通。不过，我们确实有指数分布的闭式表达式。因此，可以生成参数为 $1/2$ 的指数分布以及 $[0,2\pi]$ 上的均匀分布，用这两个分布便能生成标准正态分布。

<!-- ===== PDF p5 ===== -->

**（续）**

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4（第 4 题）**</span>

> <span style="color:#2471a3;">[solution]</span> 对应教材（textbook）第 250 页的习题 4.20（Problem 4.20），证明见教材。下面给出另一种证法：
>
> 考虑选取参数 $\alpha$，使两个随机变量 $X$ 与 $Y$ 之间的期望平方差最小。考虑
>
> ```math
> J(\alpha)=E\big[(X-\alpha Y)^2\big],\qquad Y\neq 0,
> ```
>
> 我们先做一个关于参数 $\alpha$ 的一元函数求极值计算来寻找最小化 $J(\alpha)$ 的 $\alpha$。由于当 $Y\neq 0$ 时 $\dfrac{d^2J(\alpha)}{d\alpha^2}=2E[Y^2]>0$，最小化 $J(\alpha)$ 的 $\alpha$ 可通过令 $J(\alpha)$ 的一阶导数为零求得：
>
> ```math
> \frac{dJ(\alpha)}{d\alpha}=\frac{d}{d\alpha}\Big(E[X^2]-2\alpha\,E[XY]+\alpha^2E[Y^2]\Big)=0
> \qquad\Longrightarrow\qquad
> \alpha=\frac{E[XY]}{E[Y^2]}
> ```
>
> 即 $\alpha=\dfrac{E[XY]}{E[Y^2]}$ 最小化 $J(\alpha)$。

<!-- ===== PDF p6 ===== -->

**（续）**

> <span style="color:#2471a3;">[solution]</span>（续）于是
>
> ```math
> J\left(\frac{E[XY]}{E[Y^2]}\right)
> =E\left[\left(X-\frac{E[XY]}{E[Y^2]}\,Y\right)^2\right]\ge 0
> =E[X^2]-2\,\frac{(E[XY])^2}{E[Y^2]}+\frac{(E[XY])^2\,E[Y^2]}{(E[Y^2])^2}
> =E[X^2]-\frac{(E[XY])^2}{E[Y^2]}\ge 0.
> ```
>
> 整理该式即得期望形式的施瓦茨不等式（Schwarz inequality）：
>
> ```math
> E[X^2]\,E[Y^2]\ \ge\ \big(E[XY]\big)^2.
> ```
>
> 把 $X$、$Y$ 换成中心化后的 $X-E[X]$、$Y-E[Y]$，上式即化为 $\big(E[(X-E[X])(Y-E[Y])]\big)^2\le \mathrm{var}(X)\,\mathrm{var}(Y)$，这正是相关系数满足 $|\rho(X,Y)|\le 1$ 的来源。
>
> 注意，在上述推导中我们假设了 $Y\neq 0$，从而 $E[Y^2]>0$。若假设 $Y=0$（即 $Y$ 恒为零），则 $E[XY]=0$ 且 $E[Y^2]=0$，施瓦茨不等式将以等式成立。

<!-- ===== PDF p7 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课件）　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
