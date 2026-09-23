<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 11 解答（Recitation 11: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；October 14, 2010，2010 年 10 月 14 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1（第 1 题）**</span>

<span style="color:#7f8c8d;">[note] 本解答 PDF 未附原题面。由解答过程可还原题设：$X$ 是取值于 $\{0,1\}$ 的离散随机变量，$P(X=1)=p$；观测 $Z=X+Y$，其中噪声 $Y$ 服从参数为 $\lambda$ 的对称双侧指数分布（拉普拉斯分布，Laplace distribution），即在 $X=x$ 的条件下 $Z$ 的条件 PDF 为 $f_{Z|X}(z\mid x)=\frac{\lambda}{2}e^{-\lambda|z-x|}$。</span>

> <span style="color:#2471a3;">[solution]</span> 我们需要使用“离散随机变量以连续随机变量为条件”版本的贝叶斯法则（Bayes' rule）：
>
> ```math
> p_{X|Z}(x\mid z)=\frac{p_X(x)\,f_{Z|X}(z\mid x)}{f_Z(z)}
> =\frac{p_X(x)\,f_{Z|X}(z\mid x)}{\sum_{k=0}^{1}p_X(k)\,f_{Z|X}(z\mid k)}.
> ```
>
> 具体地，
>
> ```math
> p_{X|Z}(1\mid z)=P(X=1\mid Z=z)
> =\frac{p_X(1)\,f_{Z|X}(z\mid 1)}{\sum_{k=0}^{1}p_X(k)\,f_{Z|X}(z\mid k)}
> =\frac{p\cdot\frac{1}{2}\lambda e^{-\lambda|z-1|}}{(1-p)\cdot\frac{1}{2}\lambda e^{-\lambda|z+1|}+p\cdot\frac{1}{2}\lambda e^{-\lambda|z-1|}}
> =\frac{pe^{-\lambda|z-1|}}{(1-p)e^{-\lambda|z+1|}+pe^{-\lambda|z-1|}}
> =\frac{p}{(1-p)e^{-\lambda(|z+1|-|z-1|)}+p}.
> ```
>
> 上述最后的变形是为了便于解读 $p\to 0^+$、$p\to 1^-$、$\lambda\to 0^+$ 与 $\lambda\to\infty$ 各种极限下的含义。容易得到
>
> ```math
> \lim_{p\to 0^+}P(X=1\mid Z=z)=0
> \qquad\text{and}\qquad
> \lim_{p\to 1^-}P(X=1\mid Z=z)=1;
> ```
>
> 这很合理：当不借助观测就能确定 $X$ 的取值时，观测值 $z$ 就变得无关紧要了。接下来，
>
> ```math
> \lim_{\lambda\to 0^+}P(X=1\mid Z=z)=p,
> ```
>
> 这也合理：当 $\lambda\to 0^+$ 时 $Y$ 的分布变得非常平坦，观测不再提供信息（uninformative）。最后，
>
> ```math
> \lim_{\lambda\to\infty}P(X=1\mid Z=z)=
> \begin{cases}
> 1, & \text{if } |z+1|>|z-1|,\\
> 0, & \text{if } |z+1|<|z-1|,
> \end{cases}
> \;=\;
> \begin{cases}
> 1, & \text{if } z>0,\\
> 0, & \text{if } z<0;
> \end{cases}
> ```
>
> 这很合理：$\lambda\to\infty$ 使 $Y$ 变得可忽略。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2（第 2 题）**</span>

<span style="color:#7f8c8d;">[note] 本解答 PDF 未附原题面。由解答过程可还原题设：$Q$ 是 $[0,1]$ 上的连续随机变量，先验 PDF 为 $f_Q(q)=6q(1-q)$；给定 $Q=q$ 时，$X$ 为伯努利随机变量（Bernoulli random variable），$P(X=1\mid Q=q)=q$，即 $p_{X|Q}(1\mid q)=q$、$p_{X|Q}(0\mid q)=1-q$。</span>

> <span style="color:#2471a3;">[solution]</span> 我们需要使用“连续随机变量以离散随机变量为条件”版本的贝叶斯法则（Bayes' rule）：
>
> ```math
> f_{Q|X}(q\mid x)=\frac{f_Q(q)\,p_{X|Q}(x\mid q)}{p_X(x)},\qquad
> p_X(x)=\int_0^1 f_Q(q)\,p_{X|Q}(x\mid q)\,dq.
> ```
>
> 对于 $x=0$ 与 $q\in[0,1]$，
>
> ```math
> f_{Q|X}(q\mid 0)=\frac{f_Q(q)\,p_{X|Q}(0\mid q)}{\int_0^1 f_Q(q)\,p_{X|Q}(0\mid q)\,dq}
> =\frac{6q(1-q)\cdot(1-q)}{\int_0^1 6q(1-q)\cdot(1-q)\,dq}
> =\frac{6q(1-q)\cdot(1-q)}{1/2}=12q(1-q)^2.
> ```

<!-- ===== PDF p2 ===== -->

**（续）**

> <span style="color:#2471a3;">[solution]</span>（续）对于 $x=1$ 与 $q\in[0,1]$，
>
> ```math
> f_{Q|X}(q\mid 1)=\frac{f_Q(q)\,p_{X|Q}(1\mid q)}{\int_0^1 f_Q(q)\,p_{X|Q}(1\mid q)\,dq}
> =\frac{6q(1-q)\cdot q}{\int_0^1 6q(1-q)\cdot q\,dq}
> =\frac{6q(1-q)\cdot q}{1/2}=12q^2(1-q).
> ```
>
> $f_Q(q)$、$f_{Q|X}(q\mid 0)$ 与 $f_{Q|X}(q\mid 1)$ 都属于贝塔分布（beta distribution）家族，该分布族在教材第 8 章中还会再次出现。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3（第 3 题）**</span>

<span style="color:#7f8c8d;">[note] 本解答 PDF 未附原题面。由解答过程可还原题设：$X$ 服从标准正态分布（standard normal distribution），$f_X(x)=\frac{1}{\sqrt{2\pi}}e^{-x^2/2}$；$Y=g(X)$，其中 $g$ 的定义使 $Y$ 只取非负值（由推导过程可知：当 $X\le 0$ 时 $Y=-X$，当 $X>0$ 时 $Y=\sqrt{X}$）。任务是求 $Y$ 的 PDF $f_Y(y)$。</span>

> <span style="color:#2471a3;">[solution]</span> 由 $g$ 的定义，随机变量 $Y$ 只取非负值。因此对任意负的 $y$ 都有 $f_Y(y)=0$。当 $y>0$ 时，
>
> ```math
> F_Y(y)=P(Y\le y)=P\big(X\in[-y,\,0]\big)+P\big(X\in(0,\,y^2]\big)
> =\big(F_X(0)-F_X(-y)\big)+\big(F_X(y^2)-F_X(0)\big)
> =F_X(y^2)-F_X(-y).
> ```
>
> 对 $F_Y(y)$ 求导（并使用链式法则，chain rule），得
>
> ```math
> f_Y(y)=2y\,f_X(y^2)+f_X(-y)
> =2y\cdot\frac{1}{\sqrt{2\pi}}e^{-y^4/2}+\frac{1}{\sqrt{2\pi}}e^{-y^2/2}.
> ```

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课件）　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
