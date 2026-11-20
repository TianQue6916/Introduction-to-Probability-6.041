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
> 由于 $E[Z \mid X, Y]$ 是随机变量 $X$ 与 $Y$ 的函数，并且在 $X = x$、$Y = y$ 发生时（该情况以概率 $p_{X,Y}(x, y)$ 发生）等于 $E[Z \mid X = x, Y = y]$，于是由 expected value rule（期望值法则，即：若 $W = g(X, Y)$ 是 $X, Y$ 的函数，则 $E[W] = \sum_x \sum_y g(x, y)\, p_{X,Y}(x, y)$），
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
> 〔上面第三行用到乘法法则（multiplication rule）$p_{Z\mid X,Y}(z\mid x,y)\,p_{X,Y}(x,y) = p_{X,Y,Z}(x,y,z)$；第四行用到边际化（marginalization）$\sum_x\sum_y p_{X,Y,Z}(x,y,z) = p_Z(z)$，故 $\sum_z z\, p_Z(z) = E[Z]$。〕
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
> 〔第三行用到条件形式的乘法法则 $p_{Z\mid X,Y}(z\mid x,y)\,p_{Y\mid X}(y\mid x) = p_{Y,Z\mid X}(y,z\mid x)$；第四行用到边际化 $\sum_y p_{Y,Z\mid X}(y,z\mid x) = p_{Z\mid X}(z\mid x)$。〕
>
> 由于上式对 $x$ 的一切可能取值都成立，故有 $E\big[E[Z \mid Y, X] \mid X\big] = E[Z \mid X]$。（$E[Z \mid Y, X]$ 与 $E[Z \mid X, Y]$ 是同一个随机变量，只是书写次序不同。）
>
> **(c)** 对 (b) 中公式的两边取期望，得
>
> > ```math
> > E\big[E[Z \mid X]\big] = E\big[E\big[E[Z \mid X, Y] \,\big|\, X\big]\big].
> > ```
>
> 由 law of iterated expectations（期望迭代法则，又称 tower property（塔性质），即 $E[Z] = E\big[E[Z \mid X]\big]$），上式左边即为 $E[Z]$，从而证得所要的结果。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $Y$ 为第一次折断后所得一段的长度，$X$ 为第二次折断后所得一段的长度。
>
> 〔模型补充：这里考虑的是一根长度为 $\ell$ 的木棍。先在 $[0, \ell]$ 上均匀随机取一点折断，取其中一段，其长度记为 $Y$，故 $Y$ 在 $[0, \ell]$ 上均匀分布；再对这段长为 $Y$ 的木棍在 $[0, Y]$ 上均匀随机取一点折断，取其中一段，其长度记为 $X$，故给定 $Y$ 时 $X$ 在 $[0, Y]$ 上均匀分布。下文 $E[X \mid Y] = Y/2$、$E[Y] = \ell/2$ 均由此模型而来。〕

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> **(a)** law of iterated expectations（期望迭代法则）指出：
>
> > ```math
> > E[X] = E\big[E[X \mid Y]\big]
> > ```
>
> 我们有 $E[X \mid Y] = Y/2$（因为给定 $Y$，$X$ 在 $[0, Y]$ 上均匀分布，均值为 $Y/2$），以及 $E[Y] = \ell/2$（因为 $Y$ 在 $[0, \ell]$ 上均匀分布，均值为 $\ell/2$）。于是：
>
> > ```math
> > E[X] = E\big[E[X \mid Y]\big] = E[Y/2] = \frac{1}{2}\, E[Y] = \frac{1}{2}\cdot\frac{\ell}{2} = \frac{\ell}{4}.
> > ```
>
> **(b)** 我们用 law of total variance（全方差定律：$\mathrm{var}(X) = E\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(E[X \mid Y]\big)$）来求 $\mathrm{var}(X)$：
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
> 〔上式中 $f_Y(y) = 1/\ell$（$0 \le y \le \ell$）是 $Y$ 在 $[0, \ell]$ 上均匀分布的密度。〕
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
> 〔模型补充：这里 $N$ 是箱子的总数（一个随机变量），每个箱子里小部件的数目 $X_i$ 是独立同分布（i.i.d.，independently and identically distributed）的随机变量，且都独立于 $N$。记共同分布为 $E[X_i] = E[X]$、$\mathrm{var}(X_i) = \mathrm{var}(X)$。题目给定 $E[X] = 10$、$\mathrm{var}(X) = 16$、$E[N] = 10$、$\mathrm{var}(N) = 16$（这四个数值可由最终结果 $E[T] = 100$、$\mathrm{var}(T) = 1760$ 唯一反推得出）。〕
>
> > ```math
> > \begin{aligned}
> > E[T] &= E\!\left[E\!\left[\sum_{i=1}^{N} X_i \,\middle|\, N\right]\right] \\
> > &= E\!\left[\sum_{i=1}^{N} E[X_i \mid N]\right] \\
> > &= E\!\left[\sum_{i=1}^{N} E[X]\right] \\
> > &= E[X] \cdot E[N] = 100.
> > \end{aligned}
> > ```
>
> 〔第二、三行用到 $X_i$ 与 $N$ 独立，故 $E[X_i \mid N] = E[X_i] = E[X]$；第四行 $E\big[\sum_{i=1}^{N} E[X]\big] = E[X]\, E[N]$，因为 $E[X]$ 是常数。〕

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
>
> 〔第三行用到 $X_i$ 独立同分布且独立于 $N$：$\mathrm{var}\big(\sum_{i=1}^{N} X_i \mid N\big) = N\,\mathrm{var}(X)$，$E\big[\sum_{i=1}^{N} X_i \mid N\big] = N\,E[X]$；第四行用到 $E[N\,\mathrm{var}(X)] = \mathrm{var}(X)\,E[N]$（$\mathrm{var}(X)$ 是常数）以及 $\mathrm{var}(N\,E[X]) = (E[X])^2\,\mathrm{var}(N)$（$\mathrm{var}(aN) = a^2\,\mathrm{var}(N)$）。〕

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">【尾页】本页为 MIT OpenCourseWare（麻省理工学院开放式课程）封底版权页：注明课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）、Fall 2010 学期，以及引用条款网址 http://ocw.mit.edu/terms，无实质教学内容，不译。</span>
