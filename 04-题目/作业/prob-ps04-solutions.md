<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 4 解答（Problem Set 4: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 · 电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：$X$、$Y$ 的联合 PMF（joint PMF）仅在六个点 $(1,1),\ (1,3),\ (2,1),\ (2,3),\ (4,1),\ (4,3)$ 处非零，且每一对的概率正比于其坐标平方和 $x^2+y^2$；(i) 中事件 $A=\{Y \le X\}$（由其所含样本点可知）。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 由联合 PMF，共有六个概率非零的 $(x, y)$ 坐标对。它们是 $(1, 1)$、$(1, 3)$、$(2, 1)$、$(2, 3)$、$(4, 1)$ 和 $(4, 3)$。每一对的概率正比于该对坐标的平方和 $x^2 + y^2$。由于整个样本空间（sample space）的概率必须等于 1，我们有
>
> ```math
> (1+1)c + (1+9)c + (4+1)c + (4+9)c + (16+1)c + (16+9)c = 1
> ```
>
> 解出 $c$，得 $c = \dfrac{1}{72}$。
>
> (b) 满足 $y < x$ 的样本点有三个：
>
> ```math
> P(Y < X) = P(\{(2, 1)\}) + P(\{(4, 1)\}) + P(\{(4, 3)\}) = \frac{5}{72} + \frac{17}{72} + \frac{25}{72} = \frac{47}{72}
> ```
>
> (c) 满足 $y > x$ 的样本点有两个：
>
> ```math
> P(Y > X) = P(\{(1, 3)\}) + P(\{(2, 3)\}) = \frac{10}{72} + \frac{13}{72} = \frac{23}{72}
> ```
>
> (d) 满足 $y = x$ 的样本点只有一个：
>
> ```math
> P(Y = X) = P(\{(1, 1)\}) = \frac{2}{72}
> ```
>
> 注意，利用上面两小问的结果，
>
> ```math
> P(Y < X) + P(Y > X) + P(Y = X) = \frac{47}{72} + \frac{23}{72} + \frac{2}{72} = 1
> ```
>
> 与预期一致。
>
> (e) 满足 $y = 3$ 的样本点有三个：
>
> ```math
> P(Y = 3) = P(\{(1, 3)\}) + P(\{(2, 3)\}) + P(\{(4, 3)\}) = \frac{10}{72} + \frac{13}{72} + \frac{25}{72} = \frac{48}{72}
> ```
>
> (f) 一般地，对定义了联合 PMF 的两个离散随机变量（random variable）$X$ 与 $Y$，我们有
>
> ```math
> p_X(x) = \sum_{y=-\infty}^{\infty} p_{X,Y}(x, y) \qquad\text{and}\qquad p_Y(y) = \sum_{x=-\infty}^{\infty} p_{X,Y}(x, y)
> ```
>
> 本题中 $X$ 与 $Y$ 的取值范围相当受限，因此可以通过枚举确定边际 PMF（marginal PMF）。例如
>
> ```math
> p_X(2) = P(\{(2, 1)\}) + P(\{(2, 3)\}) = \frac{18}{72}
> ```
>
> 总体结果为
>
> ```math
> p_X(x) = \begin{cases} 12/72, & \text{if } x = 1 \\ 18/72, & \text{if } x = 2 \\ 42/72, & \text{if } x = 4 \\ 0, & \text{otherwise} \end{cases} \qquad\qquad p_Y(y) = \begin{cases} 24/72, & \text{if } y = 1 \\ 48/72, & \text{if } y = 3 \\ 0, & \text{otherwise} \end{cases}
> ```

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> (g) 一般地，任何离散随机变量 $X$ 的期望（expected value）为
>
> ```math
> E[X] = \sum_{x=-\infty}^{\infty} x\, p_X(x)
> ```
>
> 对本题，
>
> ```math
> E[X] = 1\cdot\frac{12}{72} + 2\cdot\frac{18}{72} + 4\cdot\frac{42}{72} = 3
> ```
>
> 以及
>
> ```math
> E[Y] = 1\cdot\frac{24}{72} + 3\cdot\frac{48}{72} = \frac{7}{3}
> ```
>
> 为计算 $E[XY]$，注意 $p_{X,Y}(x, y) \ne p_X(x)\,p_Y(y)$。因此 $X$ 与 $Y$ 不独立（independent），我们不能假设 $E[XY] = E[X]E[Y]$。于是
>
> ```math
> E[XY] = \sum_{x}\sum_{y} x\,y\, p_{X,Y}(x, y) = 1\cdot\frac{2}{72} + 2\cdot\frac{5}{72} + 4\cdot\frac{17}{72} + 3\cdot\frac{10}{72} + 6\cdot\frac{13}{72} + 12\cdot\frac{25}{72} = \frac{61}{9}
> ```
>
> (h) 随机变量 $X$ 的方差（variance）既可以用 $E[X^2] - E[X]^2$ 计算，也可以用 $E[(X - E[X])^2]$ 计算。由于 $X$ 与 $Y$ 的取值范围很有限，这里我们使用第二种方法。我们有
>
> ```math
> \mathrm{var}(X) = (1-3)^2\,\frac{12}{72} + (2-3)^2\,\frac{18}{72} + (4-3)^2\,\frac{42}{72} = \frac{3}{2}
> ```
>
> 以及
>
> ```math
> \mathrm{var}(Y) = \Bigl(1-\frac{7}{3}\Bigr)^2\frac{24}{72} + \Bigl(3-\frac{7}{3}\Bigr)^2\frac{48}{72} = \frac{8}{9}
> ```
>
> $X$ 与 $Y$ 不独立，所以不能假设 $\mathrm{var}(X + Y) = \mathrm{var}(X) + \mathrm{var}(Y)$。$X+Y$ 的方差将用 $\mathrm{var}(X + Y) = E[(X + Y)^2] - (E[X + Y])^2$ 来计算。因此
>
> ```math
> E[(X + Y)^2] = 4\cdot\frac{2}{72} + 9\cdot\frac{5}{72} + 25\cdot\frac{17}{72} + 16\cdot\frac{10}{72} + 25\cdot\frac{13}{72} + 49\cdot\frac{25}{72} = \frac{547}{18}
> ```
>
> ```math
> (E[X + Y])^2 = (E[X] + E[Y])^2 = \Bigl(3 + \frac{7}{3}\Bigr)^2 = \frac{256}{9}
> ```
>
> 所以
>
> ```math
> \mathrm{var}(X + Y) = \frac{547}{18} - \frac{256}{9} = \frac{35}{18}
> ```
>
> (i) $A$ 中有四个 $(x, y)$ 坐标对：$(1,1)$、$(2,1)$、$(4,1)$ 和 $(4,3)$。因此
>
> ```math
> P(A) = \frac{1}{72}\,(2 + 5 + 17 + 25) = \frac{49}{72}
> ```
>
> 为求 $E[X \mid A]$ 与 $\mathrm{var}(X \mid A)$，必须先计算 $p_{X \mid A}(x)$。我们有
>
> ```math
> p_{X \mid A}(x) = \begin{cases} 2/49, & \text{if } x = 1 \\ 5/49, & \text{if } x = 2 \\ 42/49, & \text{if } x = 4 \\ 0, & \text{otherwise} \end{cases}
> ```

<!-- ===== PDF p3 ===== -->

> **（续）**
>
> ```math
> E[X \mid A] = 1\cdot\frac{2}{49} + 2\cdot\frac{5}{49} + 4\cdot\frac{42}{49} = \frac{180}{49}
> ```
>
> ```math
> E[X^2 \mid A] = 1^2\cdot\frac{2}{49} + 2^2\cdot\frac{5}{49} + 4^2\cdot\frac{42}{49} = \frac{694}{49}
> ```
>
> ```math
> \mathrm{var}(X \mid A) = E[X^2 \mid A] - (E[X \mid A])^2 = \frac{694}{49} - \Bigl(\frac{180}{49}\Bigr)^2 = \frac{1606}{2401}
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

<span style="color:#7f8c8d;">（“这枚骰子（this die）”即习题集原题中的骰子；由解答可知：掷出 1 的概率为 $1/2$，掷出 2、3 的概率各为 $1/4$。）</span>

考虑这枚骰子的六次独立抛掷组成的序列，令 $X_i$ 为对应第 $i$ 次抛掷的随机变量。

(a) 恰好有三次抛掷结果等于 3 的概率是多少？

(b) 已知六次抛掷中恰好两次结果为 1，求第一次抛掷为 1 的概率？

(c) 现已知恰好三次抛掷结果为 1、三次结果为 2，求序列 121212 的概率？

(d) 以「至少一次抛掷结果为 3」为条件，求 3 的个数的条件 PMF。

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 每次抛掷 $X_i$ 以概率 $1/4$ 得到 3，以概率 $3/4$ 得到的不是 3。把 3 放入六次抛掷的序列共有 $\binom{6}{3}$ 种放法。在要求这些位置各放一个 3（概率为 $(1/4)^3$）之后，剩下的唯一条件是其余三个位置放 1 或 2（概率为 $(3/4)^3$）。因此，六次独立抛掷中恰好出现三次 3 的概率为
>
> ```math
> \binom{6}{3}\Bigl(\frac{1}{4}\Bigr)^3\Bigl(\frac{3}{4}\Bigr)^3
> ```
>
> (b) 单次抛掷得到 1 的概率为 $1/2$，得到 2 或 3 的概率也是 $1/2$。为求解本题，我们把「得到 2 或 3」视为同一等价结果。已知恰好掷出两个 1 共有 $\binom{6}{2}$ 种方式；其中恰好有 $\binom{5}{1} = 5$ 种方式使第一次抛掷为 1，因为其余的那个 1 可以放在剩下五次抛掷中的任意一次。其余各次抛掷必须是 2 或 3。因此，「已知恰好两次掷出 1 时第一次为 1」的概率为
>
> ```math
> \frac{5}{\binom{6}{2}}
> ```
>
> (c) 我们要求
>
> ```math
> P(121212 \mid \text{exactly three 1's and three 2's}) = \frac{P(121212)}{P(\text{exactly 3 ones and 3 twos})}
> ```
>
> 任何由三个 1 和三个 2 组成的特定序列都具有相同的概率 $(1/2)^3(1/4)^3$。恰好三个 1 和三个 2 的抛掷序列共有 $\binom{6}{3}$ 种。因此
>
> ```math
> P(121212 \mid \text{exactly three 1's and three 2's}) = \Bigl(\frac{1}{\binom{6}{3}}\Bigr)
> ```
>
> (d) 设 $A$ 为事件「至少一次抛掷结果为 3」。则
>
> ```math
> P(A) = 1 - P(\text{no rolls resulted in 3}) = 1 - \Bigl(\frac{3}{4}\Bigr)^6
> ```
>
> 现在令 $K$ 为表示 6 次抛掷中 3 的个数的随机变量。$K$ 的（无条件）PMF 为
>
> ```math
> p_K(k) = \binom{6}{k}\Bigl(\frac{1}{4}\Bigr)^k\Bigl(\frac{3}{4}\Bigr)^{6-k}
> ```

<!-- ===== PDF p4 ===== -->

> **（续）** 我们利用条件概率的定义求条件 PMF（conditional PMF）$p_{K \mid A}(k \mid A)$：
>
> ```math
> p_{K \mid A}(k \mid A) = \frac{P(\{K = k\} \cap A)}{P(A)}
> ```
>
> 于是得到
>
> ```math
> p_{K \mid A}(k \mid A) = \begin{cases} \dfrac{1}{1-(3/4)^6}\,\dbinom{6}{k}\Bigl(\dfrac{1}{4}\Bigr)^k\Bigl(\dfrac{3}{4}\Bigr)^{6-k}, & \text{if } k = 1, 2, \ldots, 6 \\[8pt] 0, & \text{otherwise} \end{cases}
> ```
>
> 注意 $p_{K \mid A}(0 \mid A) = 0$，因为事件 $\{K = 0\}$ 与事件 $A$ 互斥（mutually exclusive）。因此在条件 PMF 的定义中出现在分子的「交集概率」为零。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；本题即：$X$ 与 $Y$ 为独立的几何随机变量（geometric random variables，参数 $p$），证明 $P(X = i \mid X + Y = n) = \dfrac{1}{n-1}$，$i = 1, \ldots, n-1$。）</span>

> <span style="color:#2471a3;">[solution]</span> 由条件概率的定义，
>
> ```math
> P(X = i \mid X + Y = n) = \frac{P(\{X = i\} \cap \{X + Y = n\})}{P(X + Y = n)}
> ```
>
> 分子中的事件 $\{X = i\} \cap \{X + Y = n\}$ 等价于 $\{X = i\} \cap \{Y = n - i\}$。结合 $X$ 与 $Y$ 的独立性（independence），
>
> ```math
> P(\{X = i\} \cap \{X + Y = n\}) = P(\{X = i\} \cap \{Y = n - i\}) = P(X = i)\,P(Y = n - i)
> ```
>
> 在分母中，利用全概率定理（total probability theorem）与 $X$、$Y$ 的独立性展开 $P(X + Y = n)$：
>
> ```math
> P(X + Y = n) = \sum_{i=1}^{n-1} P(X = i)\,P(X + Y = n \mid X = i) = \sum_{i=1}^{n-1} P(X = i)\,P(i + Y = n \mid X = i)
> ```
>
> ```math
> = \sum_{i=1}^{n-1} P(X = i)\,P(Y = n - i \mid X = i) = \sum_{i=1}^{n-1} P(X = i)\,P(Y = n - i)
> ```
>
> 注意，由于 $X$ 与 $Y$ 是几何随机变量，只有当 $i = 1, \ldots, n - 1$ 时才得到非零概率。

<!-- ===== PDF p5 ===== -->

> **（续）** 结合上面的计算，并显式地代入几何 PMF，即得所求结果：
>
> ```math
> P(X = i \mid X + Y = n) = \frac{P(X = i)\,P(Y = n - i)}{\sum_{i=1}^{n-1} P(X = i)\,P(Y = n - i)} = \frac{(1-p)^{i-1}p\,(1-p)^{n-i-1}p}{\sum_{i=1}^{n-1} (1-p)^{i-1}p\,(1-p)^{n-i-1}p}
> ```
>
> ```math
> = \frac{(1-p)^{n-2}p^2}{\sum_{i=1}^{n-1} (1-p)^{n-2}p^2} = \frac{(1-p)^{n-2}p^2}{(n-1)\,(1-p)^{n-2}p^2} = \frac{1}{n-1},\qquad i = 1, \ldots, n - 1
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：抛掷一枚正面概率为 $p$ 的硬币多次。(a) 中 $A$ 为「8 次抛掷中恰出现 6 次正面」、$B$ 为一次与之不重叠的抛掷出现正面（由 $P(B \cap A) = P(A)\cdot p$ 可知）；(b) $C$=前 4 次中 3 次正面、$D$=后 3 次中 2 次正面；(c) $E$=前 7 次中 4 次正面、$F$=第 2 次正面出现在第 4 次；(d) $G$=前 8 次中 5 次正面、$H$=后 5 次中 3 次正面（两组抛掷在第 6–8 次重叠）。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 由于 $P(A) > 0$，我们可以通过验证 $P(B) = P(B \mid A)$ 来证明独立性：
>
> ```math
> P(B \mid A) = \frac{P(B \cap A)}{P(A)} = \frac{\dbinom{8}{6}\,p^6(1-p)^2\,p}{\dbinom{8}{6}\,p^6(1-p)^2} = p = P(B)
> ```
>
> 因此 $A$ 与 $B$ 独立。
>
> (b) 令 $C$ 为事件「前 4 次抛掷中 3 次正面」，$D$ 为事件「后 3 次抛掷中 2 次正面」。由于 $C$ 与 $D$ 涉及的抛掷没有重叠（overlap），二者独立：
>
> ```math
> P(C \cap D) = P(C)\,P(D) = \binom{4}{3}\,p^3(1-p)\cdot\binom{3}{2}\,p^2(1-p) = 12\,p^5(1-p)^2
> ```
>
> (c) 令 $E$ 为事件「前 7 次抛掷中 4 次正面」，$F$ 为事件「第 2 次正面出现在第 4 次试验」。题目要求 $P(F \mid E) = P(F \cap E)/P(E)$。事件 $F \cap E$ 发生，当且仅当：前 3 次试验中恰有 1 次正面、第 4 次试验为正面、且后 3 次试验中恰有 2 次正面。于是
>
> ```math
> P(F \mid E) = \frac{P(F \cap E)}{P(E)} = \frac{\dbinom{3}{1}\,p(1-p)^2\cdot p \cdot \dbinom{3}{2}\,p^2(1-p)}{\dbinom{7}{4}\,p^4(1-p)^3} = \frac{3\cdot 1 \cdot 3}{35} = \frac{9}{35}
> ```
>
> 或者，我们也可以用计数法求解。已知前 7 次抛掷中出现了 4 次正面。

<!-- ===== PDF p6 ===== -->

> **（续）** 每个含 4 次正面的 7 次试验序列都是等可能的，此处可以使用离散均匀概率律（discrete uniform probability law）。$E$ 中共有 $\dbinom{7}{4}$ 个结果。对于事件 $E \cap F$：在前 3 次试验中安排 1 个正面有 $\dbinom{3}{1}$ 种方式，把第 2 个正面安排在第 4 次试验有 1 种方式，在后 3 次试验中安排 2 个正面有 $\dbinom{3}{2}$ 种方式。因此
>
> ```math
> P(F \mid E) = \frac{\dbinom{3}{1}\cdot 1 \cdot \dbinom{3}{2}}{\dbinom{7}{4}} = \frac{9}{35}
> ```
>
> <span style="color:#1e8449;">[note]</span> 原文此处误写为 "ways to arrange 2 heads in the **first** 3 trials"，应为 the **last** 3 trials（后 3 次试验）。
>
> (d) 令 $G$ 为事件「前 8 次抛掷中 5 次正面」，$H$ 为事件「后 5 次抛掷中 3 次正面」。这两个事件不独立，因为所涉及的抛掷有重叠（第 6、7、8 次）。为计算所求概率，我们以第 6、7、8 次抛掷中正面出现的次数为条件，仔细清点集合 $G \cap H$ 中所有互不相交的可能结果：
>
> ```math
> P(G \cap H) = P(G \cap H \mid \text{1 head in tosses 6--8})\,P(\text{1 head in tosses 6--8})
> ```
>
> ```math
> +\; P(G \cap H \mid \text{2 heads in tosses 6--8})\,P(\text{2 heads in tosses 6--8}) + P(G \cap H \mid \text{3 heads in tosses 6--8})\,P(\text{3 heads in tosses 6--8})
> ```
>
> ```math
> = \binom{5}{4}\,p^4(1-p)\cdot p^2 \cdot \binom{3}{1}\,p(1-p)^2 + \binom{5}{3}\,p^3(1-p)^2 \cdot \binom{2}{1}\,p(1-p) \cdot \binom{3}{2}\,p^2(1-p)
> ```
>
> ```math
> +\; \binom{5}{2}\,p^2(1-p)^3 \cdot (1-p)^2 \cdot \binom{3}{3}\,p^3
> ```
>
> ```math
> = 15\,p^7(1-p)^3 + 60\,p^6(1-p)^4 + 10\,p^5(1-p)^5
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：逐次抛掷一枚正面概率为 $p$ 的硬币，若第 $k-1$ 次为正面（H）且第 $k$ 次为反面（T），则在时刻 $k$ 支付报酬 $I_k = 1$，否则 $I_k = 0$；$R = \sum_{k=1}^{n} I_k$，求 $E[R]$ 与 $\mathrm{var}(R)$。）</span>

> <span style="color:#2471a3;">[solution]</span> 设 $I_k$ 为时刻 $k$ 支付的报酬（reward）。我们有
>
> ```math
> E[I_k] = P(I_k = 1) = P(\text{T at time k and H at time k-1}) = p(1-p)
> ```
>
> 计算 $E[R]$ 很直接，因为
>
> ```math
> E[R] = E\Bigl[\sum_{k=1}^{n} I_k\Bigr] = \sum_{k=1}^{n} E[I_k] = np(1-p)
> ```
>
> 方差的计算则没有那么容易，因为各 $I_k$ 并不全部相互独立：
>
> $E[I_k^2] = p(1-p)$；$E[I_k I_{k+1}] = 0$，因为时刻 $k$ 与 $k+1$ 的报酬是互不相容的（inconsistent）；$E[I_k I_{k+\ell}] = E[I_k]\,E[I_{k+\ell}] = p^2(1-p)^2$，对 $\ell \ge 2$。

<!-- ===== PDF p7 ===== -->

> **（续）**
>
> ```math
> E[R^2] = E\Bigl[\Bigl(\sum_{k=1}^{n} I_k\Bigr)\Bigl(\sum_{m=1}^{n} I_m\Bigr)\Bigr] = \sum_{k=1}^{n}\sum_{m=1}^{n} E[I_k I_m]
> ```
>
> ```math
> = \underbrace{np(1-p)}_{\text{$n$ terms with $k=m$}} + \underbrace{0}_{\text{$2(n-1)$ terms with $|k-m|=1$}} + \underbrace{(n^2 - 3n + 2)\,p^2(1-p)^2}_{\text{$n^2-3n+2$ terms with $|k-m|>1$}}
> ```
>
> （即：$k = m$ 的 $n$ 项；$|k-m| = 1$ 的 $2(n-1)$ 项；$|k-m| > 1$ 的 $n^2 - 3n + 2$ 项。）
>
> ```math
> \mathrm{var}(R) = E[R^2] - (E[R])^2 = np(1-p) + (n^2 - 3n + 2)\,p^2(1-p)^2 - n^2\,p^2(1-p)^2 = np(1-p) - (3n-2)\,p^2(1-p)^2
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**G1†**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；本题考察事件 $A$、$B$ 的指示随机变量（indicator random variables）$I_A$、$I_B$ 与 $A$、$B$ 独立性之间的关系，以及 $E[I_A]$ 的计算（(b) 至此为止）。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 我们知道，$I_A$ 是这样一个随机变量：若 $\omega$ 落在事件 $A$ 之内，则把它映射到实数线上的 1；若 $\omega$ 落在事件 $A$ 之外，则映射为 0。对事件 $B$ 也有类似的论证。于是我们有
>
> ```math
> I_A(\omega) = \begin{cases} 1, & \text{with probability } P(A) \\ 0, & \text{with probability } 1 - P(A) \end{cases} \qquad\qquad I_B(\omega) = \begin{cases} 1, & \text{with probability } P(B) \\ 0, & \text{with probability } 1 - P(B) \end{cases}
> ```
>
> 若随机变量 $A$ 与 $B$ 独立，则有 $P(A \cap B) = P(A)P(B)$。指示随机变量 $I_A$ 与 $I_B$ 独立的条件是：$p_{I_A, I_B}(x, y) = p_{I_A}(x)\,p_{I_B}(y)$。
>
> 我们知道，$A$ 与 $B$ 的交集给出
>
> ```math
> p_{I_A, I_B}(1, 1) = p_{I_A}(1)\,p_{I_B}(1) = P(A)P(B) = P(A \cap B)
> ```
>
> 我们还有
>
> ```math
> p_{I_A, I_B}(1, 1) = P(A \cap B) = P(A)P(B) = p_{I_A}(1)\,p_{I_B}(1)
> ```
>
> ```math
> p_{I_A, I_B}(0, 1) = P(A^c \cap B) = P(A^c)P(B) = p_{I_A}(0)\,p_{I_B}(1)
> ```
>
> ```math
> p_{I_A, I_B}(1, 0) = P(A \cap B^c) = P(A)P(B^c) = p_{I_A}(1)\,p_{I_B}(0)
> ```
>
> ```math
> p_{I_A, I_B}(0, 0) = P(A^c \cap B^c) = P(A^c)P(B^c) = p_{I_A}(0)\,p_{I_B}(0)
> ```
>
> (b) 若 $X = I_A$，我们知道
>
> ```math
> E[X] = E[I_A] = 1\cdot P(A) + 0\cdot(1 - P(A)) = P(A)
> ```

<span style="color:#7f8c8d;">† 对 6.431 为必做（Required）；对 6.041 为选做（optional）。</span>

<!-- ===== PDF p8 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 尾页：6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010，http://ocw.mit.edu/terms —— 无实质题目内容。）</span>
