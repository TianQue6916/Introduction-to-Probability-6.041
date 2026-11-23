<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 2 解答（Tutorial 2: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 9 月 23/24 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

一名玩家从一副标准 52 张牌的 deck（一副扑克牌）中被随机发到 13 张牌。

**(a)** 第 13 张发出的牌是 K（king）的概率是多少？

**(b)** 第 13 张发出的牌是所发出的第一张 K 的概率是多少？

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** **答（Answer）：** $\dfrac{4}{52}$。
>
> **解（Solution）：** 由于关于先发出的 12 张牌我们未被告知任何信息，「第 13 张发出的牌是 K」的概率就与「第一张发出的牌——实际上任何特定一张发出的牌——是 K」的概率相同，而这个概率等于 $\dfrac{4}{52}$。
>
> **(b)** **答（Answer）：** $\dfrac{1}{13}\cdot 4\,\dbinom{48}{12}\Big/\dbinom{52}{13}$。
>
> **解（Solution）：** 「第 13 张牌是所发出的第一张 K」的概率，等于「前 13 张发出的牌中恰好有一张 K，而且这张 K 恰好最后发出」的概率。现在，给定前 13 张中恰好发出了一张 K，这张 K 恰好排在最后的概率就是 $1/13$，因为每个「位置」都是 equally likely（等可能）的。于是剩下要计算的，是「前 13 张发出的牌中恰好有一张 K」的概率。为计算这一概率，我们数出 favorable（有利）结果数，再除以可能结果总数。先数有利结果，即前 13 张中恰好含一张 K 的那些结果：选定是哪一张 K 有 $4$ 种方式，其余 12 张牌可从剩下的 48 张牌中选取，有 $\dbinom{48}{12}$ 种方式，因此有利结果共有 $4\cdot\dbinom{48}{12}$ 个。总结果共有 $\dbinom{52}{13}$ 个，故所求概率为
>
> ```math
> \frac{1}{13}\cdot\frac{4\binom{48}{12}}{\binom{52}{13}}.
> ```
>
> 另一种解法：我们如例 1.10（Example 1.10）中那样论证。第一张牌不是 K 的概率为 $48/52$；在此条件下，第二张牌不是 K 的概率为 $47/51$；类似地继续下去直到第 12 张牌：给定前 11 张都不是 K，第 12 张牌不是 K 的概率为 $37/41$（此时还剩 $52-11=41$ 张牌，其中 $48-11=37$ 张不是 K）。最后，第 13 张牌是 K 的条件概率为 $4/40$。故所求概率为
>
> ```math
> \frac{48\cdot 47\cdot\ldots\cdot 37\cdot 4}{52\cdot 51\cdot\ldots\cdot 41\cdot 40}.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

考虑一个 random variable（随机变量）$X$：当 $x\in\{-3,-2,-1,1,2,3\}$ 时 $p_X(x)=\dfrac{x^2}{a}$；当 $x\notin\{-3,-2,-1,1,2,3\}$ 时 $P(X=x)=0$。其中 $a>0$ 为 real parameter（实参数）。

**(a)** 求 $a$。

<!-- ===== PDF p2 ===== -->

**（续）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** **解（Solution）：** 随机变量的 PMF（probability mass function，概率质量函数）在其所有以正概率取得的取值上的总和必等于 $1$。因此
>
> ```math
> 1=\sum_{x=-3}^{3}p_X(x)=\frac{9}{a}+\frac{4}{a}+\frac{1}{a}+\frac{1}{a}+\frac{4}{a}+\frac{9}{a}=\frac{28}{a},
> ```
>
> 由此得 $a=28$。
>
> **(b)** 随机变量 $Z=X^2$ 的 PMF 是什么？
>
> **解（Solution）：** 下表给出了 $Z$ 在 $X$ 的每个取值下所取的值，以及相应事件的概率：
>
> | $x$ | $-3$ | $-2$ | $-1$ | $1$ | $2$ | $3$ |
> |---|---|---|---|---|---|---|
> | $p_X(x)$ | $9/28$ | $1/7$ | $1/28$ | $1/28$ | $1/7$ | $9/28$ |
> | $Z\mid X=x$ | $9$ | $4$ | $1$ | $1$ | $4$ | $9$ |
>
> 我们看到，$Z$ 只能以非零概率取三个可能的值：$1$、$4$ 和 $9$；此外，每个值都对应 $X$ 的两个取值。于是，例如有 $p_Z(9)=P(Z=9)=P(X=-3)+P(X=3)=p_X(-3)+p_X(3)$。故 $Z$ 的 PMF 为
>
> ```math
> p_Z(z)=\begin{cases}1/14, & z=1,\\[2pt] 2/7, & z=4,\\[2pt] 9/14, & z=9.\end{cases}
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设我们给三个 class（班）标号为 A、B、C。Joe 和 Jane 两人都分到 A 班的概率是：「同时包含 Joe 和 Jane 的 A 班组成方式数」除以「A 班的组成方式总数」。因此，我们所求的概率为
>
> ```math
> \frac{\dbinom{88}{28}}{\dbinom{90}{30}}.
> ```
>
> 由于共有三个 classroom（教室），Joe 和 Jane 最终分到同一教室的概率就是上面所得答案的三倍：
>
> ```math
> 3\cdot\frac{\dbinom{88}{28}}{\dbinom{90}{30}}.
> ```
>
> 本题还可以这样看：设其中一人先选，比如说 Joe。他可以从 90 个可用位置中任选一个。接着轮到 Jane 选，她选中与 Joe 同班的位置的概率为 $\dfrac{29}{89}$。因此，总概率为 $\dfrac{29}{89}$，它与 $3\cdot\dfrac{\binom{88}{28}}{\binom{90}{30}}$ 相同。
>
> <span style="color:#1e8449;">**[note]**</span> 上一句中 $\tfrac{29}{89}$ 的来历：Joe 选定一个位置后还剩 $89$ 个位置，其中属于 Joe 所在班级（每班 $30$ 个位置）的还剩 $30-1=29$ 个。
>
> <span style="color:#1e8449;">**[mathtip]**</span> 两种算法的一致性可由 $\dbinom{90}{30}=\dfrac{90}{30}\cdot\dfrac{89}{29}\dbinom{88}{28}$ 直接验证：$3\cdot\dfrac{\binom{88}{28}}{\binom{90}{30}}=\dfrac{29}{89}$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $A$ = 「这 7 张牌中恰好包含 3 张 ace（A 牌）」这一事件。
>
> ```math
> P(A)=\frac{(\text{选 3 张 A 的方式数})\cdot(\text{选其余 4 张牌的方式数})}{\text{选 7 张牌的方式数}}=\frac{\dbinom{4}{3}\,\dbinom{48}{4}}{\dbinom{52}{7}}.
> ```

---

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课件）　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关这些材料的引用方式或使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>
