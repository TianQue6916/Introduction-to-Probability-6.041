<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 13 解答（Recitation 13: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 10 月 21 日）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 我们先写出 $E[Z \mid X, Y]$ 的定义：
>
> > ```math
> > E[Z \mid X = x, Y = y] = \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)
> > ```
>
> 由于 $E[Z \mid X, Y]$ 是随机变量 $X$ 与 $Y$ 的函数，并且在 $X = x$、$Y = y$ 发生时（该情况以概率 $p_{X,Y}(x, y)$ 发生）等于 $E[Z \mid X = x, Y = y]$，于是由 expected value rule（期望值法则），
>
> > ```math
> > \begin{aligned}
> > E\big[E[Z \mid X, Y]\big]
> > &= \sum_x \sum_y E[Z \mid X = x, Y = y]\, p_{X,Y}(x, y) \\
> > &= \sum_x \sum_y \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)\, p_{X,Y}(x, y) \\
> > &= \sum_x \sum_y \sum_z z\, p_{X,Y,Z}(x, y, z) \\
> > &= E[Z].
> > \end{aligned}
> > ```
>
> **(b)** 我们从 $E[Z \mid X, Y]$ 的定义出发——它是随机变量 $X$ 与 $Y$ 的函数，并且在 $X = x$、$Y = y$ 时等于 $E[Z \mid X = x, Y = y]$，因此
>
> > ```math
> > E[Z \mid X = x, Y = y] = \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)
> > ```
>
> 仿照上面的步骤推进，但改为在事件 $X = x$ 上取条件，得
>
> > ```math
> > \begin{aligned}
> > E\big[E[Z \mid X, Y = y] \,\big|\, X = x\big]
> > &= \sum_y E[Z \mid X = x, Y = y]\, p_{Y\mid X}(y \mid x) \\
> > &= \sum_y \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)\, p_{Y\mid X}(y \mid x) \\
> > &= \sum_y \sum_z z\, p_{Y,Z\mid X}(y, z \mid x) \\
> > &= E[Z \mid X = x].
> > \end{aligned}
> > ```
>
> 由于上式对 $x$ 的一切可能取值都成立，故有 $E\big[E[Z \mid Y, X] \mid X\big] = E[Z \mid X]$。
>
> **(c)** 对 (b) 中公式的两边取期望，得
>
> > ```math
> > E\big[E[Z \mid X]\big] = E\big[E\big[E[Z \mid X, Y] \,\big|\, X\big]\big].
> > ```
>
> 由 law of iterated expectations（期望迭代法则），上式左边即为 $E[Z]$，从而证得所要的结果。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $Y$ 为第一次折断后所得一段的长度，$X$ 为第二次折断后所得一段的长度。

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> **(a)** law of iterated expectations（期望迭代法则）指出：
>
> > ```math
> > E[X] = E\big[E[X \mid Y]\big]
> > ```
>
> 我们有 $E[X \mid Y] = Y/2$，以及 $E[Y] = \ell/2$。于是：
>
> > ```math
> > E[X] = E\big[E[X \mid Y]\big] = E[Y/2] = \frac{1}{2}\, E[Y] = \frac{1}{2}\cdot\frac{\ell}{2} = \frac{\ell}{4}.
> > ```
>
> **(b)** 我们用 law of total variance（全方差定律）来求 $\mathrm{var}(X)$：
>
> > ```math
> > \mathrm{var}(X) = E\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(E[X \mid Y]\big).
> > ```
>
> 回顾：在区间 $[a, b]$ 上均匀分布（uniform）的随机变量，其方差为 $(b-a)^2/12$。由于 $Y$ 在 $[0, \ell]$ 上均匀分布，我们有
>
> > ```math
> > \mathrm{var}(Y) = \frac{\ell^2}{12}, \qquad \mathrm{var}(X \mid Y) = \frac{Y^2}{12}.
> > ```
>
> 已知 $E[X \mid Y] = Y/2$，于是
>
> > ```math
> > \mathrm{var}\big(E[X \mid Y]\big) = \mathrm{var}(Y/2) = \frac{1}{4}\,\mathrm{var}(Y) = \frac{\ell^2}{48}.
> > ```
>
> 另外，
>
> > ```math
> > \begin{aligned}
> > E\big[\mathrm{var}(X \mid Y)\big]
> > &= E\!\left[\frac{Y^2}{12}\right] \\
> > &= \int_0^{\ell} \frac{y^2}{12}\, f_Y(y)\, dy \\
> > &= \frac{1}{12} \cdot \frac{1}{\ell} \int_0^{\ell} y^2\, dy \\
> > &= \frac{\ell^2}{36}.
> > \end{aligned}
> > ```
>
> 综合以上结果，得
>
> > ```math
> > \mathrm{var}(X) = E\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(E[X \mid Y]\big) = \frac{\ell^2}{36} + \frac{\ell^2}{48} = \frac{7\ell^2}{144}.
> > ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $X_i$ 表示第 $i$ 个箱子中 widgets（小部件）的数目，则 $T = \sum_{i=1}^{N} X_i$。
>
> > ```math
> > \begin{aligned}
> > E[T] &= E\!\left[E\!\left[\sum_{i=1}^{N} X_i \,\middle|\, N\right]\right] \\
> > &= E\!\left[\sum_{i=1}^{N} E[X_i \mid N]\right] \\
> > &= E\!\left[\sum_{i=1}^{N} E[X]\right] \\
> > &= E[X] \cdot E[N] = 100.
> > \end{aligned}
> > ```

<!-- ===== PDF p3 ===== -->

> **（续）** 以及，
>
> > ```math
> > \begin{aligned}
> > \mathrm{var}(T) &= E\big[\mathrm{var}(T \mid N)\big] + \mathrm{var}\big(E[T \mid N]\big) \\
> > &= E\!\left[\mathrm{var}\!\left(\sum_{i=1}^{N} X_i \,\middle|\, N\right)\right] + \mathrm{var}\!\left(E\!\left[\sum_{i=1}^{N} X_i \,\middle|\, N\right]\right) \\
> > &= E\big[N\, \mathrm{var}(X)\big] + \mathrm{var}\big(N\, E[X]\big) \\
> > &= \big(\mathrm{var}(X)\big)\, E[N] + \big(E[X]\big)^2\, \mathrm{var}(N) \\
> > &= 16 \cdot 10 + 100 \cdot 16 = 1760.
> > \end{aligned}
> > ```

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">【尾页】本页为 MIT OpenCourseWare（麻省理工学院开放式课程）封底版权页：注明课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）、Fall 2010 学期，以及引用条款网址 http://ocw.mit.edu/terms，无实质教学内容，不译。</span>
