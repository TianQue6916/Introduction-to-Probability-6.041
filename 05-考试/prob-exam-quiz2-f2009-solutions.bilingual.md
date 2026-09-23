<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 2 解答（Quiz 2 Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2009，2009 秋季学期，2009 年 11 月 3 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

<span style="color:#7f8c8d;">（本解答文件自 Problem 2 起；Problem 1 未包含在该解答 PDF 中。）</span>

---

<span style="color:#c0392b;">**Problem 2（49 分）**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）**（7 分）我们首先注意到：当 $x\ge 0$ 时 $f_X(x)=e^{-x}$；当 $y\ge 0$ 时 $f_{Y\mid X}(y\mid x)=xe^{-xy}$。此外，$f_{X,Y}(x,y)=f_X(x)\cdot f_{Y\mid X}(y\mid x)$。代入 $f_X(x)$ 与 $f_{Y\mid X}(y\mid x)$ 得
>
> ```math
> f_{X,Y}(x,y)=
> \begin{cases}
> xe^{-(1+y)x}, & x\ge 0,\ y\ge 0,\\[2pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> **（b）**（7 分）$Y$ 的 marginal PDF（边缘概率密度函数）可以通过对 $X$ 与 $Y$ 的联合 PDF 积分求得：
>
> ```math
> f_Y(y)=\int_{X}f_{X,Y}(x,y)\,dx=\int_{0}^{\infty}xe^{-(1+y)x}\,dx=\frac{1}{(1+y)^{2}}
> ```
>
> ```math
> f_Y(y)=
> \begin{cases}
> \dfrac{1}{(1+y)^{2}}, & y\ge 0,\\[6pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> **（c）**（7 分）本题要求在以另一个随机变量 $Y$ 为条件的情况下，计算随机变量 $X$ 的 PDF。给定 $Y=2$ 时 $X$ 的 conditional PDF（条件概率密度函数）为
>
> ```math
> f_{X\mid Y}(x\mid 2)=\frac{f_{X,Y}(x,2)}{f_Y(2)}
> =\frac{xe^{-3x}}{1/9}=9xe^{-3x}
> ```
>
> ```math
> f_{X\mid Y}(x\mid 2)=
> \begin{cases}
> 9xe^{-3x}, & x\ge 0,\\[2pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> **（d）**（7 分）
>
> ```math
> E[X\mid Y=2]=\int_{X}x\cdot f_{X\mid Y}(x\mid 2)\,dx
> =9\int_{0}^{\infty}x^{2}e^{-3x}\,dx
> =9\cdot\frac{2}{3^{3}}=\frac{2}{3}.
> ```

<!-- ===== PDF p2 ===== -->

> **Problem 2（续）**
>
> **（e）**（7 分）在 $X=2$ 的这个新"世界"（universe）中，题目要求计算给定事件 $Y\ge 3$ 时 $Y$ 的条件 PDF：
>
> ```math
> f_{Y\mid X,\,Y\ge 3}(y\mid 2)=\frac{f_{Y\mid X}(y\mid 2)}{P(Y\ge 3\mid X=2)}.
> ```
>
> 我们先计算 $P(Y\ge 3\mid X=2)$：
>
> ```math
> P(Y\ge 3\mid X=2)=\int_{3}^{\infty}f_{Y\mid X}(y\mid 2)\,dy
> =\int_{3}^{\infty}2e^{-2y}\,dy
> =1-F_{Y\mid X}(3\mid 2)
> =1-\bigl(1-e^{-2\cdot 3}\bigr)
> =e^{-6},
> ```
>
> 其中 $F_{Y\mid X}(3\mid 2)$ 是参数 $\lambda=2$ 的 exponential random variable（指数随机变量）在 $y=3$ 处的 CDF（累积分布函数）。把 $f_{Y\mid X}(y\mid 2)$ 与 $P(Y\ge 3\mid X=2)$ 的值代入，得
>
> ```math
> f_{Y\mid X,\,Y\ge 3}(y\mid 2)=
> \begin{cases}
> 2e^{6}e^{-2y}, & y\ge 3,\\[2pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> 另一种做法：$f_{Y\mid X}(y\mid 2)$ 是参数 $\lambda=2$ 的指数随机变量。为计算条件 PMF $f_{Y\mid X,\,Y\ge 3}(y\mid 2)$，我们可以利用指数变量的 memorylessness property（无记忆性）。因此，这个条件 PMF 同样是参数 $\lambda=2$ 的指数随机变量，只是向右平移了 3。
>
> <span style="color:#1e8449;">**[note]**</span> 原文此两处写作 "PMF"（概率质量函数）；就连续随机变量而言应为 "PDF"（概率密度函数）。
>
> **（f）**（7 分）定义 $Z=e^{2X}$。由于 $X$ 是只取非负值的指数随机变量（$X\ge 0$），故 $Z\ge 1$。我们先计算 $Z$ 的 CDF，再求其 PDF：
>
> ```math
> \begin{aligned}
> F_Z(z)=P(Z\le z)
> &=P\bigl(e^{2X}\le z\bigr)\\
> &=P(2X\le \ln z)\\
> &=P\!\left(X\le \frac{\ln z}{2}\right)\\
> &=1-e^{-\ln z/2}\\
> &=1-e^{\ln z^{-1/2}}
> \end{aligned}
> ```
>
> $Z$ 的 CDF 为：
>
> ```math
> F_Z(z)=
> \begin{cases}
> 1-z^{-1/2}, & z\ge 1,\\[2pt]
> 0, & z<1.
> \end{cases}
> ```

<!-- ===== PDF p3 ===== -->

> **Problem 2（续）**
>
> **（f）（续）** 对 $Z$ 的 CDF 求导，得 PDF
>
> ```math
> f_Z(z)=
> \begin{cases}
> \dfrac{1}{2}z^{-3/2}, & z\ge 1,\\[6pt]
> 0, & z<1.
> \end{cases}
> ```
>
> 另一种做法：对连续随机变量的严格单调函数，可直接套用其 PDF 公式。回顾：若 $z=g(x)$ 且 $x=h(z)$，则
>
> ```math
> f_Z(z)=f_X\bigl(h(z)\bigr)\,\left|\frac{dh}{dz}(z)\right|.
> ```
>
> 在本题中，$z=e^{2x}$，$x=\dfrac{1}{2}\ln z$。注意 $h(z)$ 在 $z>1$ 时非零。由于 $X$ 是参数 $\lambda=1$ 的指数随机变量，$f_X(x)=e^{-x}$。于是
>
> ```math
> f_Z(z)=e^{-\frac{1}{2}\ln z}\,\left|\frac{1}{2z}\right|
> =e^{\ln z^{-1/2}}\cdot\frac{1}{2z}
> =\frac{1}{2}z^{-\frac{3}{2}},\qquad z\ge 1,
> ```
>
> 其中第二个等号成立，是因为当 $z\ge 1$ 时绝对值内的表达式恒为正。

---

<span style="color:#c0392b;">**Problem 3（10 分）**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）**（5 分）量 $E[X\mid Y]$ 总是：
>
> - (i) 一个数。
> - (ii) 一个 discrete random variable（离散随机变量）。
> - (iii) 一个 continuous random variable（连续随机变量）。
> - (iv) 信息不足，无法在 (i)–(iii) 之间作出选择。
>
> 若 $X$ 与 $Y$ 不独立，则 $E[X\mid Y]$ 是 $Y$ 的函数，因此是一个连续随机变量；然而若 $X$ 与 $Y$ 独立，则 $E[X\mid Y]=E[X]$，是一个数。 <span style="color:#7f8c8d;">（故应选 (iv)。）</span>
>
> **（b）**（5 分）量 $E\bigl[E[X\mid Y,N]\mid N\bigr]$ 总是：
>
> - (i) 一个数。
> - (ii) 一个离散随机变量。
> - (iii) 一个连续随机变量。
> - (iv) 信息不足，无法在 (i)–(iii) 之间作出选择。
>
> 若 $X$、$Y$、$N$ 不独立，则内层期望 $G(Y,N)=E[X\mid Y,N]$ 是 $Y$ 与 $N$ 的函数；进而 $E[G(Y,N)\mid N]$ 是 $N$ 的函数，而 $N$ 是一个离散随机变量。若 $X$、$Y$、$N$ 相互独立，则内层期望 $E[X\mid Y,N]=E[X]$，是一个数；而"给定 $N$ 时一个数的期望"仍然是一个数，它是离散随机变量的特殊情形。 <span style="color:#7f8c8d;">（故恒为离散随机变量，应选 (ii)。）</span>

<!-- ===== PDF p4 ===== -->

---

<span style="color:#c0392b;">**Problem 4（25 分）**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）**
>
> **(i)**（5 分）利用 law of iterated expectations（迭代期望定律），我们有
>
> ```math
> E[X]=E\bigl[E[X\mid Q]\bigr]=E[Q]=\frac{1}{2}.
> ```
>
> **(ii)**（5 分）$X$ 是均值为 $p=\dfrac{1}{2}$ 的 Bernoulli random variable（伯努利随机变量），其方差为 $\mathrm{var}(X)=p(1-p)=1/4$。
>
> **（b）**（7 分）我们知道 $\mathrm{cov}(X,Q)=E[XQ]-E[X]E[Q]$，所以先计算 $E[XQ]$：
>
> ```math
> E[XQ]=E\bigl[E[XQ\mid Q]\bigr]=E\bigl[Q\,E[X\mid Q]\bigr]=E[Q^{2}]=\frac{1}{3}.
> ```
>
> 因此
>
> ```math
> \mathrm{cov}(X,Q)=\frac{1}{3}-\frac{1}{2}\cdot\frac{1}{2}=\frac{1}{12}.
> ```
>
> **（c）**（8 分）利用 Bayes' rule（贝叶斯法则），我们有
>
> ```math
> f_{Q\mid X}(q\mid 1)=\frac{f_Q(q)\,p_{X\mid Q}(1\mid q)}{p_X(1)}
> =\frac{f_Q(q)\,P(X=1\mid Q=q)}{P(X=1)},\qquad 0\le q\le 1.
> ```
>
> 此外，我们知道 $P(X=1\mid Q=q)=q$，并且对伯努利随机变量有 $P(X=1)=E[X]=\dfrac{1}{2}$。于是，给定 $X=1$ 时 $Q$ 的条件 PDF 为
>
> ```math
> f_{Q\mid X}(q\mid 1)=\frac{1}{1/2}\cdot q=
> \begin{cases}
> 2q, & 0\le q\le 1,\\[2pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```

---

<span style="color:#c0392b;">**Problem 5（21 分）**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）**（7 分）
>
> ```math
> \begin{aligned}
> P(S\ge 1)&=P(\min\{X,Y\}\ge 1)=P(X\ge 1\ \text{且}\ Y\ge 1)=P(X\ge 1)\,P(Y\ge 1)\\
> &=\bigl(1-F_X(1)\bigr)\bigl(1-F_Y(1)\bigr)=\bigl(1-\Phi(1)\bigr)^{2}\approx(1-0.8413)^{2}\\
> &\approx 0.0252.
> \end{aligned}
> ```

<!-- ===== PDF p5 ===== -->

> **Problem 5（续）**
>
> **（b）**（7 分）回顾习题集 6（Problem Set 6）的第 2 题，我们有
>
> ```math
> \begin{aligned}
> P(s\le S\ \text{且}\ L\le \ell)&=P\bigl(s\le\min\{X,Y\}\ \text{且}\ \max\{X,Y\}\le\ell\bigr)\\
> &=P(s\le X\ \text{且}\ s\le Y\ \text{且}\ X\le\ell\ \text{且}\ Y\le\ell)\\
> &=P(s\le X\le\ell)\,P(s\le Y\le\ell)\\
> &=\bigl(F_X(\ell)-F_X(s)\bigr)\bigl(F_Y(\ell)-F_Y(s)\bigr).
> \end{aligned}
> ```
>
> <span style="color:#7f8c8d;">（原文末行提取为 $(F_Y(\ell)\,F_Y(s))$，疑似脱漏减号；按与 $X$ 一项的对称性，应为 $F_Y(\ell)-F_Y(s)$。）</span>
>
> **（c）**（7 分）给定 $s\le s+\delta\le\ell$，事件 $\{s\le S\le s+\delta,\ \ell\le L\le\ell+\delta\}$ 由两个互斥的可能事件之并构成：
>
> ```math
> \{s\le X\le s+\delta,\ \ell\le Y\le\ell+\delta\}\ \cup\ \{s\le Y\le s+\delta,\ \ell\le X\le\ell+\delta\}.
> ```
>
> 换言之，要么 $S=X$ 且 $L=Y$，要么 $S=Y$ 且 $L=X$。由于这两个事件互斥，其并的概率等于各自概率之和。再利用 $X$ 与 $Y$ 的独立性，我们有
>
> ```math
> \begin{aligned}
> &P(s\le S\le s+\delta,\ \ell\le L\le\ell+\delta)\\
> &=P(s\le X\le s+\delta,\ \ell\le Y\le\ell+\delta)+P(s\le Y\le s+\delta,\ \ell\le X\le\ell+\delta)\\
> &=P(s\le X\le s+\delta)\,P(\ell\le Y\le\ell+\delta)+P(s\le Y\le s+\delta)\,P(\ell\le X\le\ell+\delta)\\
> &=\int_{s}^{s+\delta}f_X(x)\,dx\int_{\ell}^{\ell+\delta}f_Y(y)\,dy
> +\int_{s}^{s+\delta}f_Y(y)\,dy\int_{\ell}^{\ell+\delta}f_X(x)\,dx
> \end{aligned}
> ```

<!-- ===== PDF p6 ===== -->

<span style="color:#7f8c8d;">【图】本页为 MIT OpenCourseWare 封面页：MIT OpenCourseWare（http://ocw.mit.edu），课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010（OCW 发布学期标注）；并含引用信息与使用条款（Terms of Use）链接 http://ocw.mit.edu/terms。无正文内容。</span>
