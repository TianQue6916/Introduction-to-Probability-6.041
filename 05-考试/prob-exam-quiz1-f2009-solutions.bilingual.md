<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 1 解答（Quiz 1 Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2009，2009 秋季学期，2009 年 10 月 13 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#c0392b;">**Problem 1（10 分）**</span>

> <span style="color:#2471a3;">**[solution]**</span> 我们首先列出以下概率：事件 gala（选到嘎啦品种苹果）、事件 honey crisp（选到蜜脆品种苹果）、事件 ripe（苹果成熟）满足
>
>
> ```math
> P(\text{gala})=p,\quad P(\text{honey crisp})=1-p,\quad P(\text{ripe}\mid\text{gala})=g,\quad P(\text{ripe}\mid\text{honey crisp})=h.
> ```
>
> 则 Bob 吃到一只成熟嘎啦苹果的概率为：
>
> ```math
> P(\text{ripe, gala})=P(\text{gala})\,P(\text{ripe}\mid\text{gala})=pg.
> ```

---

<span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）**（10 分）若 $K$ 是从这 $n$ 只苹果中选出的嘎啦苹果数量，则 $K$ 是一个 binomial random variable（二项随机变量）。$K=k$ 的概率为：
>
> ```math
> p_K(k)=
> \begin{cases}
> \dbinom{n}{k}p^{k}(1-p)^{\,n-k}, & 0\le k\le n,\\[6pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> **（b）(i)**（12 分）在这 $n+1$ 只苹果中，Bob 的"收获"包括：来自 Caleb 的 1 只成熟嘎啦苹果、$k$ 只嘎啦苹果、$n-k$ 只蜜脆苹果。我们可以针对上面列出的三种互斥情形，分别计算"吃到一只成熟苹果"的条件概率，再利用 total probability theorem（全概率定律）求出 Bob 吃到成熟苹果的概率：
>
> ```math
> \begin{aligned}
> P(\text{ripe apple})
> &=P(\text{ripe apple}\mid\text{Caleb's ripe gala})\,P(\text{Caleb's ripe gala})\\
> &\quad+P(\text{ripe apple}\mid k\ \text{gala})\,P(k\ \text{gala})
> +P(\text{ripe apple}\mid(n-k)\ \text{honey crisp})\,P((n-k)\ \text{honey crisp})\\[4pt]
> &=1\cdot\frac{1}{n+1}+g\cdot\frac{k}{n+1}+h\cdot\frac{n-k}{n+1}\\[4pt]
> &=\frac{1+gk+h(n-k)}{n+1}.
> \end{aligned}
> ```
>
> **（b）(ii)**（12 分）利用 Bayes' rule（贝叶斯法则）：
>
> ```math
> P(\text{gala}\mid\text{ripe apple})=\frac{P(\text{ripe}\cap\text{gala})}{P(\text{ripe apple})}.
> ```
>
> 其中 $P(\text{ripe}\cap\text{gala})$ 可如下计算：

<!-- ===== PDF p2 ===== -->

> **（b）(ii)（续）**
>
> ```math
> \begin{aligned}
> P(\text{ripe}\cap\text{gala})
> &=P(\text{ripe}\cap\text{gala}\mid\text{Caleb's ripe gala})\,P(\text{Caleb's ripe gala})\\
> &\quad+P(\text{ripe}\cap\text{gala}\mid k\ \text{gala})\,P(k\ \text{gala})
> +P(\text{ripe}\cap\text{gala}\mid(n-k)\ \text{honey crisp})\,P((n-k)\ \text{honey crisp})\\[4pt]
> &=1\cdot\frac{1}{n+1}+g\cdot\frac{k}{n+1}+0\cdot\frac{n-k}{n+1}\\[4pt]
> &=\frac{1+gk}{n+1}.
> \end{aligned}
> ```
>
> 把这个结果与 (i) 的结果相结合：
>
> ```math
> P(\text{gala}\mid\text{ripe apple})
> =\frac{\dfrac{1+gk}{n+1}}{\dfrac{1+gk+h(n-k)}{n+1}}
> =\frac{1+gk}{1+gk+h(n-k)}.
> ```
>
> **（c）**（10 分）设 $A$ 为事件「先摘出的 10 只苹果全是嘎啦」，$B$ 为事件「从 20 只苹果中恰好摘出 10 只嘎啦」。由
>
> ```math
> P(A\mid B)=\frac{P(A\cap B)}{P(B)}.
> ```
>
> 事件 $B$ 的概率可利用 (a) 的结果计算：取 $n=20$、$k=10$，得 $P(B)=\dbinom{20}{10}p^{10}(1-p)^{10}$。而 $P(A\cap B)$ 可通过把事件 $A$ 与 $B$ 的交分解为互斥事件来计算：事件 $\{A\cap B\}=\{$前 10 只摘到的都是嘎啦，且后 10 只都是蜜脆$\}$，故 $P(A\cap B)=p^{10}(1-p)^{10}$。因此
>
> ```math
> P(A\mid B)=\frac{p^{10}(1-p)^{10}}{\dbinom{20}{10}p^{10}(1-p)^{10}}=\frac{1}{\dbinom{20}{10}}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 直观理解：在"恰好 10 只嘎啦"的条件下，20 个采摘位置中哪 10 个位置是嘎啦共有 $\binom{20}{10}$ 种等可能的情形，而"前 10 个位置恰好全是嘎啦"只是其中一种。

---

<span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）**（10 分）Bob 在每棵树上摘苹果，直到摘到一只不成熟的为止。若把事件「摘到一只不成熟苹果」视为一次"成功"（success），那么 $X_i$ 就是直到首次成功为止所摘取的苹果数（即试验次数）。因此 $X_i$ 服从 geometric distribution（几何分布），其 success probability（成功概率）为 $1-g$。
>
> 由于每棵树上的苹果都是随机组合，Bob 从第一棵树摘到的苹果与从第二棵树摘到的苹果相互独立，所以 $X_1$ 与 $X_2$ 是独立同分布（independent and identically distributed）随机变量。
>
> $X_i$ 的 PMF（概率质量函数）为
>
> ```math
> p_{X_1}(k)=p_{X_2}(k)=
> \begin{cases}
> \bigl(1-(1-g)\bigr)^{k-1}(1-g)=g^{k-1}(1-g), & k=1,2,3,\ldots,\\[4pt]
> 0, & \text{otherwise（其他情形）},
> \end{cases}
> ```
>
> $X_i$ 的期望为
>
> ```math
> E[X_1]=E[X_2]=\frac{1}{1-g},
> ```
>
> $X_i$ 的方差为
>
> ```math
> \mathrm{var}(X_1)=\mathrm{var}(X_2)=\frac{1-(1-g)}{(1-g)^2}=\frac{g}{(1-g)^2}.
> ```

<!-- ===== PDF p3 ===== -->

> **Problem 3（续）**
>
> **（b）**（12 分）由 $Y_2=(X_1-1)+(X_2-1)$，可利用 expectations 的 linearity property（期望的线性性质）求 $Y_2$ 的期望：
>
> ```math
> \begin{aligned}
> E[Y_2]&=E[(X_1-1)+(X_2-1)]\\
> &=E[X_1]+E[X_2]-2\\
> &=\frac{2}{1-g}-2\\
> &=\frac{2g}{1-g}.
> \end{aligned}
> ```
>
> 由于给随机变量加上或减去一个常数不影响其方差，且 $X_1$ 与 $X_2$ 相互独立，故
>
> ```math
> \begin{aligned}
> \mathrm{var}(Y_2)&=\mathrm{var}\bigl((X_1-1)+(X_2-1)\bigr)\\
> &=\mathrm{var}(X_1+X_2)\\
> &=\mathrm{var}(X_1)+\mathrm{var}(X_2)\\
> &=\frac{2g}{(1-g)^2}.
> \end{aligned}
> ```
>
> **（c）**（12 分）设 $k\ge 0$ 且 $\ell\ge k$。事件「$Y_1=k$ 且 $Y_2=\ell$」等价于事件「$X_1=k+1$ 且 $X_2=\ell-k+1$」。由于 $X_1$ 与 $X_2$ 独立，所求概率为 $(1-g)g^{k+1-1}(1-g)g^{\ell-k+1-1}=(1-g)^{2}g^{\ell}$（当 $0\le k\le\ell$ 时），否则为零：
>
> ```math
> p_{Y_1,Y_2}(k,\ell)=
> \begin{cases}
> g^{\ell}(1-g)^{2}, & k=0,1,\ldots,\ell,\ \ \ell=k,k+1,\ldots,\\[4pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> 注意，可以把这个结果解读为：$\ell$ 次"失败"（即摘到 $\ell$ 只成熟苹果）加上两次"成功"（即令 Bob 在每棵树停止的那两只不成熟苹果）的概率。还要注意，尽管联合 PMF 的表达式不含 $k$，样本空间却依赖于 $k$（因为 $\ell\ge k$）：Bob 在第一棵树摘到的成熟苹果数，不可能多于他在前两棵树合起来摘到的成熟苹果数。
>
> **（d）**
>
> **(i)**（5 分）不是。$X_1$ 与 $Y_2$ 不独立，因为 $Y_2\ge X_1-1$，所以知道 $X_1$ 的取值就能得到关于 $Y_2$ 的信息。具体来说，若已知 Bob 从第一棵树总共摘了 10 只苹果（即 $X_1=10$），那么我们也知道 Bob 从前两棵树合起来至少摘到了 9 只成熟苹果（即 $Y_2\ge 9$）。
>
> **(ii)**（5 分）是。$X_2$ 只与第二棵树有关，$Y_1$ 只与第一棵树有关，而摘苹果这一过程在不同树之间相互独立，所以这两个随机变量相互独立。

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">【图】本页为 MIT OpenCourseWare 封面页：MIT OpenCourseWare（http://ocw.mit.edu），课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010；并含引用信息与使用条款（Terms of Use）链接 http://ocw.mit.edu/terms。无正文内容。</span>
