<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 3 解答（Tutorial 3: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

<span style="color:#1e8449;">**[note]**</span> 本文件为 OCW「Tutorial 3: Solutions」解答版：题面见对应 Tutorial 题单，本文件仅含解答。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> 一般地，我们有 $E[aX+bY+c]=aE[X]+bE[Y]+c$。因此
>
> ```math
> E[Z]=2\cdot E[X]-3\cdot E[Y].
> ```
>
> 对于两随机变量 independent（独立）的情形：若 $Z=a\cdot X+b\cdot Y$，则 $\mathrm{var}(Z)=a^2\cdot \mathrm{var}(X)+b^2\cdot \mathrm{var}(Y)$。因此
>
> ```math
> \mathrm{var}(Z)=4\cdot \mathrm{var}(X)+9\cdot \mathrm{var}(Y).
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 参见 online solutions（在线解答）。
>
> <span style="color:#7f8c8d;">原文件此题仅注明 "See online solutions"，未附详细步骤；完整解答见 OCW 在线材料。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#1e8449;">**[note]**</span> 本题题面未附于本文件；由解答可知题面给出离散随机向量 $(X,Y)$ 的 joint PMF（联合概率质量函数）$p_{X,Y}(x,y)$，$x,y\in\{1,2,3\}$，各非零取值均为 $c$ 的整数倍。

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 知道整个 sample space（样本空间）的概率必等于 $1$，即可求出 $c$：
>
> ```math
> 1=\sum_{x=1}^{3}\sum_{y=1}^{3}p_{X,Y}(x,y)=c+c+2c+2c+4c+3c+c+6c=20c,
> ```
>
> 因此 $c=\dfrac{1}{20}$。
>
> <span style="color:#1e8449;">**[note]**</span> 上式只列出 8 项，因为 $p_{X,Y}(2,2)=0$（见下文 (e)）。
>
> **(b)**
>
> ```math
> p_Y(2)=\sum_{x=1}^{3}p_{X,Y}(x,2)=2c+0+4c=6c=\frac{3}{10}.
> ```
>
> **(c)** $Z=Y X^2$。在给定 $Y=2$ 的条件下，
>
> ```math
> E[Z\mid Y=2]=E[Y X^2\mid Y=2]=E[2X^2\mid Y=2]=2E[X^2\mid Y=2],
> ```
>
> 其中 $p_{X\mid Y}(x\mid 2)=\dfrac{p_{X,Y}(x,2)}{p_Y(2)}$。因此
>
> ```math
> p_{X\mid Y}(x\mid 2)=\begin{cases}\dfrac{1/10}{3/10}=\dfrac{1}{3}, & x=1,\\[6pt] \dfrac{1/5}{3/10}=\dfrac{2}{3}, & x=3,\\[4pt] 0, & \text{otherwise}.\end{cases}
> ```
>
> 于是
>
> ```math
> E[Z\mid Y=2]=2\sum_{x=1}^{3}x^2\,p_{X\mid Y}(x\mid 2)=2\Bigl[(1^2)\cdot\frac{1}{3}+(3^2)\cdot\frac{2}{3}\Bigr]=\frac{38}{3}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 一旦以 $Y=2$ 为条件，$E[Y X^2\mid Y=2]$ 中的 $Y$ 便可用常数 $2$ 代入，从而化为 $E[2X^2\mid Y=2]$。

---

<!-- ===== PDF p2 ===== -->

**（续）**

> **(d)** **是（Yes）。** 给定 $X\neq 2$ 后，无论 $Y=y$ 取何值，$X$ 的分布都相同：
>
> ```math
> P(X=x\mid Y=y,\ X\neq 2)=P(X=x\mid X\neq 2).
> ```
>
> 例如
>
> ```math
> P(X=1\mid Y=1,\ X\neq 2)=P(X=1\mid Y=3,\ X\neq 2)=P(X=1\mid X\neq 2)=\frac{1}{3}.
> ```
>
> **(e)** 由 $p_{Y\mid X}(y\mid 2)=\dfrac{p_{X,Y}(2,y)}{p_X(2)}$，而
>
> ```math
> p_X(2)=\sum_{y=1}^{3}p_{X,Y}(2,y)=c+0+c=2c=\frac{1}{10}.
> ```
>
> 因此
>
> ```math
> p_{Y\mid X}(y\mid 2)=\begin{cases}\dfrac{1/20}{1/10}=\dfrac{1}{2}, & y=1,\\[6pt] \dfrac{1/20}{1/10}=\dfrac{1}{2}, & y=3,\\[4pt] 0, & \text{otherwise}.\end{cases}
> ```
>
> ```math
> \begin{aligned}
> E[Y^2\mid X=2]&=\sum_{y=1}^{3}y^2\,p_{Y\mid X}(y\mid 2)=(1^2)\cdot\frac{1}{2}+(3^2)\cdot\frac{1}{2}=5,\\
> E[Y\mid X=2]&=\sum_{y=1}^{3}y\,p_{Y\mid X}(y\mid 2)=1\cdot\frac{1}{2}+3\cdot\frac{1}{2}=2,\\
> \mathrm{var}(Y\mid X=2)&=E[Y^2\mid X=2]-E[Y\mid X=2]^2=5-2^2=1.
> \end{aligned}
> ```

---

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课件）　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关这些材料的引用方式或使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>
