<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 14 解答（Recitation 14: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 10 月 26 日）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 设 $X = $（相邻两次蚊子叮咬之间的时间）$= $（直到下一次蚊子叮咬的时间）。蚊子叮咬按照参数 $p = 0.5 \cdot 0.2 = 0.1$ 的 Bernoulli process（伯努利过程）发生。$X$ 是 geometric random variable（几何随机变量），因此
>
> > ```math
> > E[X] = \frac{1}{p} = \frac{1}{0.1} = 10, \qquad \mathrm{var}(X) = \frac{1-p}{p^2} = \frac{1-0.1}{0.1^2} = 90.
> > ```
>
> **(b)** 蚊子叮咬按照参数 $p = 0.1$ 的伯努利过程发生；蜱虫（tick）叮咬按照另一个独立的、参数 $q = 0.1 \cdot 0.7 = 0.07$ 的伯努利过程发生。虫咬（蚊子或蜱虫）则按照由蚊子过程与蜱虫过程合并（merged）而成的伯努利过程发生。因此，合并伯努利过程在任一时刻"成功"的概率为 $r = p + q - pq = 0.1 + 0.07 - 0.1 \cdot 0.07 = 0.163$。设 $Y$ 为相邻两次虫咬之间的时间。如前所述，$Y$ 是几何随机变量，因此
>
> > ```math
> > E[Y] = \frac{1}{r} = \frac{1}{0.163} \approx 6.135, \qquad \mathrm{var}(Y) = \frac{1-r}{r^2} = \frac{1-0.163}{0.163^2} \approx 31.503.
> > ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 在这种情形下，由于各次试验相互独立，所给的信息是无关的。
>
> > ```math
> > P(\text{接下来 2 次试验均得到 3 个反面}) = \left(\frac{1}{8}\right)^2 = \frac{1}{64}.
> > ```
>
> **(b)**
>
> **i.** 如教材中所定义，随机变量 $N$ 的 second order Pascal PMF（二阶帕斯卡 PMF）是"第二次成功恰在第 $n$ 次试验发生"的概率。于是，随机变量 $K$ 是该二阶帕斯卡 PMF 的平移版本，即 $K = N - 1$。因此，"前 $k$ 次试验中恰出现 1 次成功、且下一次试验产生第二次成功"的概率可以表示为：
>
> > ```math
> > p_K(k) = \binom{k}{1}\left(\frac{1}{4}\right)^2\left(\frac{3}{4}\right)^{k-1}, \qquad k \geq 1.
> > ```
>
> **ii.** 第一次成功之前的反面数 $M$ 可以写成一个随机和（random sum）：
>
> > ```math
> > M = X_1 + X_2 + \cdots + X_N,
> > ```
>
> 其中 $X_i$ 是第 $i$ 次（失败的）试验中出现的反面数，$N$ 是失败试验的次数（即第一次成功之前的试验次数）。我们注意到 $X$ 等可能地取 $1$ 或 $2$，而 $N$ 是一个平移几何（shifted geometric）随机变量：$N = R - 1$，其中 $R$ 是参数为 $1/4$ 的几何随机变量。于是我们可以应用随机和公式（random sum formulae）：
>
> > ```math
> > E[M] = E[X]\, E[N] = \left(\frac{3}{2}\right)(4 - 1) = \frac{9}{2},
> > ```
>
> > ```math
> > \mathrm{var}(M) = E[N]\,\mathrm{var}(X) + \big(E[X]\big)^2\,\mathrm{var}(N) = (4 - 1)\left(\frac{1}{4}\right) + \left(\frac{3}{2}\right)^2 (12) = \frac{111}{4}.
> > ```

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> **(c)** Bob 实验中的试验次数 $N$ 可以表示为 3 个独立随机变量 $X$、$Y$、$Z$ 之和：$X$ 是直到 Bob 取出第一枚硬币的试验次数，$Y$ 是再直到他取出第二枚硬币所需的额外试验次数，$Z$ 是再直到他取出第三枚硬币所需的额外次数。我们看到 $X$ 是参数为 $1/8$ 的几何随机变量，$Y$ 是参数为 $1/4$ 的几何随机变量，$Z$ 是参数为 $1/2$ 的几何随机变量。因此，
>
> > ```math
> > E[N] = E[X] + E[Y] + E[Z] = 8 + 4 + 2 = 14.
> > ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $M$ 为你签完所有 $n$ 份文件所需的总抽取次数，并设 $T_i$ 为已签 $i$ 份文件后、直到抽出下一份未签文件所需的抽取次数。则 $M = T_0 + \cdots + T_{n-1}$。
>
> 我们可以把"已签 $i$ 份后选取下一份未签文件"的过程看作一列独立的 Bernoulli trials（伯努利试验），其成功概率为 $p_i = \dfrac{n-i}{n}$，因为 $n$ 份文件中共有 $n-i$ 份未签，而在一次抽取中抽到任何一份文件都是等可能的。在已签 $i$ 份后，"直到成功抽出下一份未签文件所需的尝试次数"服从 geometric PMF（几何 PMF）。更具体地说，已签 $i$ 份后需要 $k$ 次尝试才抽到下一份未签文件的概率为
>
> > ```math
> > P(T_i = k) = (1 - p_i)^{k-1}\, p_i.
> > ```
>
> 在此模型下，$M$（签完所有 $n$ 份文件所需的抽取次数）的期望为：
>
> > ```math
> > E[M] = E\!\left[\sum_{i=0}^{n-1} T_i\right] = \sum_{i=0}^{n-1} E[T_i] = \sum_{i=0}^{n-1} \frac{1}{p_i} = \sum_{i=0}^{n-1} \frac{n}{n-i} = n \sum_{k=1}^{n} \frac{1}{k}.
> > ```
>
> 对于大的 $n$，其量级为：$n \displaystyle\int_1^n \frac{1}{x}\, dx = n \log n$。

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">【尾页】本页为 MIT OpenCourseWare（麻省理工学院开放式课程）封底版权页：注明课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）、Fall 2010 学期，以及引用条款网址 http://ocw.mit.edu/terms，无实质教学内容，不译。</span>
