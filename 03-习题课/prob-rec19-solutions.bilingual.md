<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 19 解答（Recitation 19: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 11 月 16 日）</span>

<span style="color:#7f8c8d;">麻省理工学院电气工程与计算机科学系（Massachusetts Institute of Technology, Department of Electrical Engineering & Computer Science）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)** 马尔可夫链（Markov chain）如下图所示。
>
> <span style="color:#7f8c8d;">【图】原页此处为马尔可夫链示意图（状态 $6\text{-}1$、$6\text{-}2$、$6\text{-}3$ 为瞬时状态，$9$ 与 $15$ 为吸收态：$6\text{-}1$ 有自环 $1/2$，并以 $1/8$ 分别转向 $6\text{-}2$、$6\text{-}3$、$9$、$15$；$6\text{-}2$ 以 $1/2$ 转向 $15$、以 $3/8$ 转向 $6\text{-}1$、以 $1/8$ 转向 $6\text{-}3$；$6\text{-}3$ 以 $1/4$ 转向 $9$、以 $3/8$ 转向 $6\text{-}1$、以 $3/8$ 转向 $6\text{-}2$；$9$、$15$ 的自环概率均为 $1$）。原图由后处理统一插入。</span>
>
> 由观察（by inspection）可知，状态 $6\text{-}1$、$6\text{-}2$、$6\text{-}3$ 都是 transient（瞬时的），因为从其中每一个状态出发都有路径到达状态 $9$ 或状态 $15$，而到达之后便无法返回。因此她最终以概率 $1$ 离开 course 6（课程 6）。
>
> **(b)** 这就是由状态「课程 15」（course-15）单独构成的 recurrent class（常返类）所对应的 absorption probability（吸收概率）。设 $a_i$ 为在处于状态 $i$ 的条件下最终被状态 $15$ 吸收的概率。则
>
> ```math
> \begin{aligned}
> a_{15}&=1,\qquad a_9=0\\
> a_{6\text{-}1}&=\frac{1}{8}(1)+\frac{1}{8}(0)+\frac{1}{2}\,a_{6\text{-}1}+\frac{1}{8}\,a_{6\text{-}2}+\frac{1}{8}\,a_{6\text{-}3}\\
> a_{6\text{-}2}&=\frac{1}{2}(1)+\frac{3}{8}\,a_{6\text{-}1}+\frac{1}{8}\,a_{6\text{-}3}\\
> a_{6\text{-}3}&=\frac{1}{4}(0)+\frac{3}{8}\,a_{6\text{-}1}+\frac{3}{8}\,a_{6\text{-}2}
> \end{aligned}
> ```
>
> 解此方程组（system of equations）得
>
> ```math
> a_{6\text{-}1}=\frac{105}{184}\approx 0.571
> ```
>
> 其余各 $a_i$ 我们也先保留着——后面还会用到：$a_{6\text{-}2}=0.77717$，$a_{6\text{-}3}=0.50543$。

<!-- ===== PDF p2 ===== -->

> **(c)** 这是瞬时状态 $6\text{-}1$ 的 expected time until absorption（直至吸收的期望时间）。设 $\mu_i$ 为在处于状态 $i$ 的条件下直至吸收的期望时间。则
>
> ```math
> \begin{aligned}
> \mu_{15}&=0,\qquad \mu_9=0\\
> \mu_{6\text{-}1}&=1+\frac{1}{8}(0)+\frac{1}{8}(0)+\frac{1}{2}\,\mu_{6\text{-}1}+\frac{1}{8}\,\mu_{6\text{-}2}+\frac{1}{8}\,\mu_{6\text{-}3}\\
> \mu_{6\text{-}2}&=1+\frac{1}{2}(0)+\frac{3}{8}\,\mu_{6\text{-}1}+\frac{1}{8}\,\mu_{6\text{-}3}\\
> \mu_{6\text{-}3}&=1+\frac{1}{4}(0)+\frac{3}{8}\,\mu_{6\text{-}1}+\frac{3}{8}\,\mu_{6\text{-}2}
> \end{aligned}
> ```
>
> 解此方程组得
>
> ```math
> \mu_{6\text{-}1}=\frac{162}{46}=\frac{81}{23}\approx 3.522
> ```
>
> **(d)** 这名学生每次从 $6\text{-}2$ 转到 $6\text{-}1$ 或从 $6\text{-}3$ 转到 $6\text{-}1$ 时都会买一支 ice cream cone（冰淇淋甜筒），且买的不超过 $2$ 支。设 $v_i(j)$ 为「给定她处于状态 $i$，此后再发生 $j$ 次从 $6\text{-}2$ 到 $6\text{-}1$ 或从 $6\text{-}3$ 到 $6\text{-}1$ 的转移」的条件概率。我们关心随机变量 $N$ 的期望值：$N$ 表示她在离开课程 6 之前买下的冰淇淋支数，取值为 $0$、$1$ 或 $2$。于是
>
> ```math
> E[N]=(0)\,v_{6\text{-}1}(0)+(1)\,v_{6\text{-}1}(1)+(2)\bigl(1-v_{6\text{-}1}(0)-v_{6\text{-}1}(1)\bigr)
> ```
>
> 利用 total probability theorem（全概率定理），对下一天的情况取条件，得到如下方程组：
>
> ```math
> \begin{aligned}
> v_{15}(0)&=1,\qquad v_9(0)=1\\
> v_{6\text{-}1}(0)&=\frac{1}{2}\,v_{6\text{-}1}(0)+\frac{1}{8}\,v_{6\text{-}2}(0)+\frac{1}{8}\,v_{6\text{-}3}(0)+\frac{1}{8}(1)+\frac{1}{8}(1)\\
> v_{6\text{-}2}(0)&=\frac{3}{8}(0)+\frac{1}{8}\,v_{6\text{-}3}(0)+\frac{1}{2}(1)\\
> v_{6\text{-}3}(0)&=\frac{3}{8}(0)+\frac{3}{8}\,v_{6\text{-}2}(0)+\frac{1}{4}(1)
> \end{aligned}
> ```
>
> 解此方程组得：
>
> ```math
> v_{6\text{-}1}(0)=\frac{46}{61}\approx 0.754
> ```
>
> 我们还要求出 $v_{6\text{-}1}(1)$：为此再次对下一天取条件，并求解如下方程组：
>
> ```math
> \begin{aligned}
> v_{6\text{-}1}(1)&=\frac{1}{2}\,v_{6\text{-}1}(1)+\frac{1}{8}\,v_{6\text{-}2}(1)+\frac{1}{8}\,v_{6\text{-}3}(1)+\frac{1}{8}(0)+\frac{1}{8}(0)\\
> v_{6\text{-}2}(1)&=\frac{3}{8}\,v_{6\text{-}1}(0)+\frac{1}{8}\,v_{6\text{-}3}(1)+\frac{1}{2}(0)\\
> v_{6\text{-}3}(1)&=\frac{3}{8}\,v_{6\text{-}1}(0)+\frac{3}{8}\,v_{6\text{-}2}(1)+\frac{1}{4}(0)
> \end{aligned}
> ```

<!-- ===== PDF p3 ===== -->

> **（续）** 注意第二个与第三个方程：当她转入状态 $6\text{-}1$ 时，要使此类转移总共恰好发生一次，第二天之后就不应再发生任何从 $6\text{-}2$ 到 $6\text{-}1$ 或从 $6\text{-}3$ 到 $6\text{-}1$ 的转移。解此方程组得：
>
> ```math
> v_{6\text{-}1}(1)=\frac{690}{3721}\approx 0.185
> ```
>
> 最后，解出冰淇淋支数的期望：
>
> ```math
> \begin{aligned}
> E[N]&=(0)\,v_{6\text{-}1}(0)+(1)\,v_{6\text{-}1}(0)+(2)\bigl(1-v_{6\text{-}1}(0)-v_{6\text{-}1}(1)\bigr)\\
> &=\frac{690}{3721}+2\Bigl(\frac{225}{3721}\Bigr)\\
> &=\frac{1140}{3721}\approx 0.306
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[note]** 原文上式第一行第二项印作 $v_{6\text{-}1}(0)$，系笔误，应为 $v_{6\text{-}1}(1)$：由第二行代入的数值 $690/3721=v_{6\text{-}1}(1)$ 以及 $225/3721=1-v_{6\text{-}1}(0)-v_{6\text{-}1}(1)$ 可以验证。</span>
>
> **(e)** 我们想求的是：在「学生最终到达状态 15」这一事件（记为 $A$）的条件下，直至吸收的期望时间。于是
>
> ```math
> \begin{aligned}
> P_{i,j|A}&=P(X_{n+1}=j\mid X_n=i,\;A)\\
> &=\frac{P(A\mid X_{n+1}=j,\;X_n=i)\,P(X_{n+1}=j\mid X_n=i)}{P(A\mid X_n=i)}\\
> &=\frac{P(A\mid X_{n+1}=j)\,P(X_{n+1}=j\mid X_n=i)}{P(A\mid X_n=i)}\\
> &=\frac{a_j}{a_i}\,P_{i,j}
> \end{aligned}
> ```
>
> 其中 $a_k$ 即 (b) 中求出的「处于状态 $k$ 的条件下最终到达状态 15」的吸收概率。于是我们可以用这组新的条件概率修改原链，并在新链上计算期望吸收时间。注意，状态 9 此时消失了。
>
> <span style="color:#1e8449;">**[mathtip]** 这是因为条件化后转移到 9 的概率变为 $(a_9/a_i)\,P_{i,j}=0$；而转移到 15（吸收态）的项对剩余时间贡献为 $0$。</span>
>
> 另外，注意当 $i\neq j$ 时 $P_{i,j|A}\neq P_{i,j}$，但 $P_{i,i|A}=P_{i,i}$；这意味着我们不能在条件化之后以一致的方式（in a uniform fashion）简单地 renormalize（重新归一化）转移概率。记条件化后（以处于状态 $i$ 为条件）新的期望吸收时间为 $\tilde{\mu}_i$。则方程组变为
>
> ```math
> \begin{aligned}
> \tilde{\mu}_{15}&=0\\
> \tilde{\mu}_{6\text{-}1}&=1+\frac{a_{6\text{-}1}}{a_{6\text{-}1}}\cdot\frac{1}{2}\,\tilde{\mu}_{6\text{-}1}+0+\frac{a_{6\text{-}2}}{a_{6\text{-}1}}\cdot\frac{1}{8}\,\tilde{\mu}_{6\text{-}2}+0+\frac{a_{6\text{-}3}}{a_{6\text{-}1}}\cdot\frac{1}{8}\,\tilde{\mu}_{6\text{-}3}\\
> \tilde{\mu}_{6\text{-}2}&=1+0+\frac{a_{6\text{-}1}}{a_{6\text{-}2}}\cdot\frac{3}{8}\,\tilde{\mu}_{6\text{-}1}+\frac{a_{6\text{-}3}}{a_{6\text{-}2}}\cdot\frac{1}{8}\,\tilde{\mu}_{6\text{-}3}\\
> \tilde{\mu}_{6\text{-}3}&=1+0+\frac{a_{6\text{-}1}}{a_{6\text{-}3}}\cdot\frac{3}{8}\,\tilde{\mu}_{6\text{-}1}+\frac{a_{6\text{-}2}}{a_{6\text{-}3}}\cdot\frac{3}{8}\,\tilde{\mu}_{6\text{-}2}
> \end{aligned}
> ```
>
> 解此方程组得
>
> ```math
> \tilde{\mu}_{6\text{-}1}=\frac{1763}{483}\approx 3.65
> ```
>
> **(f)** 新的马尔可夫链如下图所示。

<!-- ===== PDF p4 ===== -->

> **（续）**
>
> <span style="color:#7f8c8d;">【图】原页此处为 (f) 的新马尔可夫链示意图（状态 $6\text{-}1$、$6\text{-}2$、$6\text{-}3$、$9$、$15$：$6\text{-}1$ 有自环 $1/2$，并以 $1/6$ 分别转向 $6\text{-}2$、$6\text{-}3$、$9$；$6\text{-}2$ 以 $3/4$ 转向 $6\text{-}1$、以 $1/4$ 转向 $6\text{-}3$；$6\text{-}3$ 以 $3/8$ 转向 $6\text{-}1$、以 $3/8$ 转向 $6\text{-}2$、以 $1/4$ 转向 $9$；$9$ 与 $15$ 之间以概率 $1$ 相互转移，二者构成常返类）。原图由后处理统一插入。</span>
>
> 这是在新链上的另一道 expected time to absorption（期望吸收时间）题。设 $\mu_k$ 为：在这条新马尔可夫链中，学生从状态 $k$ 出发到达状态 9 所需天数的期望。则
>
> ```math
> \begin{aligned}
> \mu_{6\text{-}1}&=1+\frac{1}{2}\,\mu_{6\text{-}1}+\frac{1}{6}\,\mu_{6\text{-}2}+\frac{1}{6}\,\mu_{6\text{-}3}+\frac{1}{6}(0)\\
> \mu_{6\text{-}2}&=1+\frac{3}{4}\,\mu_{6\text{-}1}+\frac{1}{4}\,\mu_{6\text{-}3}\\
> \mu_{6\text{-}3}&=1+\frac{3}{8}\,\mu_{6\text{-}1}+\frac{3}{8}\,\mu_{6\text{-}2}+\frac{1}{4}(0)
> \end{aligned}
> ```
>
> 解此方程组得：
>
> ```math
> \mu_{6\text{-}1}=\frac{86}{13}\approx 6.615
> ```
>
> **(g)** 状态 $6\text{-}1$、$6\text{-}2$、$6\text{-}3$ 现在都是 transient（瞬时的）；状态 $9$ 与 $15$ 构成一个 recurrent class（常返类）。由 symmetry（对称性），$9$ 与 $15$ 的 steady-state probability（平稳概率）相同，各为 $1/2$。

<!-- ===== PDF p5 ===== -->

> **(h)** 相应的马尔可夫链与 (a) 中的链相同，只是把 $p_{9,9}=1$、$p_{15,15}=1$ 换成了 $p_{9,6\text{-}1}=1/8$、$p_{9,9}=7/8$、$p_{15,6\text{-}1}=1/8$、$p_{15,15}=7/8$。
>
> 此时可以把状态 $6\text{-}1$ 视为 absorbing state（吸收态）。设 $\mu_k$ 为从状态 $k$ 出发直至被吸收的期望转移步数：
>
> ```math
> \mu_9=\frac{1}{8}+\frac{7}{8}(1+\mu_9)\;\Rightarrow\;\mu_9=8
> ```
>
> ```math
> \mu_{15}=\frac{1}{8}+\frac{7}{8}(1+\mu_{15})\;\Rightarrow\;\mu_{15}=8
> ```
>
> ```math
> \mu_{6\text{-}3}=\frac{3}{8}+\frac{3}{8}(1+\mu_{6\text{-}2})+\frac{1}{4}(1+\mu_9)
> ```
>
> ```math
> \mu_{6\text{-}2}=\frac{3}{8}+\frac{1}{8}(1+\mu_{6\text{-}3})+\frac{1}{2}(1+\mu_{15})
> ```
>
> ```math
> \Rightarrow\quad \mu_{6\text{-}2}=\frac{344}{61},\qquad \mu_{6\text{-}3}=\frac{312}{61}
> ```
>
> 设 $R$ 为她再次处于 $6\text{-}1$ 之前所经过的天数。对第一次转移发生的情况取条件，用 total expectation theorem（全期望定理）求 $E[R]$：
>
> ```math
> \begin{aligned}
> E[R]&=E\bigl[E[R\mid X_2]\bigr]\\
> &=\frac{1}{2}(1)+\frac{1}{8}(1+\mu_9)+\frac{1}{8}(1+\mu_{15})+\frac{1}{8}(1+\mu_{6\text{-}2})+\frac{1}{8}(1+\mu_{6\text{-}3})\\
> &=\frac{265}{61}
> \end{aligned}
> ```
>
> 注意，这条链由单个 recurrent aperiodic class（非周期常返类）构成。解本题的另一种方法是利用这条链的 steady-state probabilities（平稳概率）：
>
> ```math
> \pi_{6\text{-}1}=\frac{61}{265},\quad \pi_{6\text{-}2}=\frac{11}{265},\quad \pi_{6\text{-}3}=\frac{9}{265},\quad \pi_9=\frac{79}{265},\quad \pi_{15}=\frac{105}{265}
> ```
>
> 访问 $6\text{-}1$ 的 expected frequency of visits（期望访问频率）为 $\pi_{6\text{-}1}$，因此两次访问 $6\text{-}1$ 之间相隔的期望天数为 $1/\pi_{6\text{-}1}$。¹ 由于她当前正处于 $6\text{-}1$，直到她再次处于 $6\text{-}1$ 的期望天数即为 $1/\pi_{6\text{-}1}=265/61$。
>
> <span style="color:#7f8c8d;">¹ 关于平均重返时间（mean recurrence times）与平稳概率之间这一对应关系的更详细解释，见教材（textbook）第 399 页的 Problem 7.34（习题 7.34）。</span>

<!-- ===== PDF p6 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（http://ocw.mit.edu）　6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010。如需了解这些材料的引用方式或我们的使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>
