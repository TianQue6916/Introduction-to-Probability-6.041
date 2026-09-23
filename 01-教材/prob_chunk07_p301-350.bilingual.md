<!-- ===== PDF p301 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> — §5.5（续）

<span style="color:#c0392b;">**§5.5　大数强定律（The Strong Law of Large Numbers）**</span> <span style="color:#7f8c8d;">（正文收尾 + 第 5 章习题区）</span>

> <span style="color:#7f8c8d;">承接上一页：本页以 §5.5 正文末尾的取极限步骤开头 —— 令 $n \to \infty$，利用恒等式 $\lim_{n\to\infty}\left(1+\frac{c}{n}\right)^{n} = e^{c}$ 得到相应结果；随后转入第 5 章习题区，承接单元 6 已到 Problem 12 停下的进度，本页呈现 **Problem 13\*、14\*、15\***。</span>

现在我们令 $n \to \infty$，并利用恒等式（identity）

```math
\lim_{n \to \infty} \left(1 + \frac{c}{n}\right)^{n} = e^{c},
```

以得到（to obtain）……

> <span style="color:#7f8c8d;">[原页此处内容跨页断裂] 原页「以得到」（to obtain）之后的具体结果被分页折入下一页，本页残存至此即被本页的运行页眉（running head）截断；取极限这一步是上一页 §5.5 正文对概率为 1 收敛（convergence with probability 1）讨论的收尾，所导出的结果延续到后续页。</span>

---

<span style="color:#c0392b;">**第 5 章　习题（Problems）**</span> <span style="color:#7f8c8d;">（题干与解答均保留英文原题；带 `*` 题自本单元起承接 Problem 13。）</span>

> <span style="color:#7f8c8d;">[OCR 情况说明] 下面 Problems 13–15 的英文题干与解答由本页 OCR 清理重建：原文含多处噪声，如 `a l b`（即 $a/b$）、`I Yn l < €`（即 $\left|Y_n - \theta\right| < \varepsilon$）、`P ( CC )`（即 $P(C^c)$）、`E[XJjE[Y]`（即 $E[X]/E[Y]$），以及 Problem 15 中极限值被识别为 `c`（实为 $\theta$）。数值与符号均已按大数强定律的标准表述还原，未改动数学含义。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 13.**\*</span>

Consider two sequences of random variables $X_1, X_2, \ldots$ and $Y_1, Y_2, \ldots$. Suppose that $X_n$ converges to $a$ and $Y_n$ converges to $b$, with probability 1. Show that $X_n + Y_n$ converges to $a+b$, with probability 1. Also, assuming that the random variables $Y_n$ cannot be equal to zero, show that $X_n / Y_n$ converges to $a/b$, with probability 1.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「以概率 1 收敛」的精确含义是：存在一个零概率的「坏集」，只要样本点不落进坏集，序列就按通常意义（实分析里的逐点意义）收敛。Problem 13 的整个技巧就是把「会出错的样本点」收集起来：两个序列各自有一个零概率坏集，其并集仍是零概率集合（概率的可数可加性保证零测集之并仍为零测），于是和序列在坏集之外处处收敛。这正是你在 100B 实分析（TBB/Rudin）里反复遇到的「几乎处处（almost everywhere）」观念——以概率 1 就是概率测度下的几乎处处。把这条注刻进脑子里：之后看到「with probability 1」，一律翻译成「挖掉一个零测集之后，剩下的地方全都成立」，所有 a.s. 收敛的证明都从这个译法出发。

<span style="color:#00838f;">**Solution（解答）.**</span> Let $A$ (respectively, $B$) be the event that the sequence of values of the random variables $X_n$ (respectively, $Y_n$) does not converge to $a$ (respectively, $b$). Let $C$ be the event that the sequence of values of $X_n + Y_n$ does not converge to $a + b$ and notice that $C \subset A \cup B$. Since $X_n$ and $Y_n$ converge to $a$ and $b$, respectively, with probability 1, we have $P(A) = 0$ and $P(B) = 0$. Hence,

```math
P(C) \le P(A \cup B) \le P(A) + P(B) = 0.
```

Therefore, $P(C^c) = 1$, or equivalently, $X_n + Y_n$ converges to $a + b$ with probability 1. For the convergence of $X_n / Y_n$, the argument is similar.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 14.**\*</span>

Let $X_1, X_2, \ldots$ be a sequence of independent identically distributed random variables. Let $Y_1, Y_2, \ldots$ be another sequence of independent identically distributed random variables. We assume that the $X_1$ and $Y_1$ have finite mean, and that $Y_1 + \cdots + Y_n$ cannot be equal to zero. Does the sequence

```math
Z_n = \frac{X_1 + \cdots + X_n}{Y_1 + \cdots + Y_n}
```

converge with probability 1, and if so, what is the limit?

<span style="color:#00838f;">**Solution（解答）.**</span> We have

```math
Z_n = \frac{(X_1 + \cdots + X_n)/n}{(Y_1 + \cdots + Y_n)/n}.
```

By the strong law of large numbers, the numerator and denominator converge with probability 1 to $E[X]$ and $E[Y]$, respectively. It follows that $Z_n$ converges to $E[X]/E[Y]$, with probability 1 (cf. the preceding problem).

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 15.**\*</span>

Suppose that a sequence $Y_1, Y_2, \ldots$ of random variables converges to a real number $\theta$ with probability 1. Show that the sequence also converges to $\theta$ in probability.

<span style="color:#00838f;">**Solution（解答）.**</span> Let $C$ be the event that the sequence of values of the random variables $Y_n$ converges to $\theta$. By assumption, we have $P(C) = 1$. Fix some $\varepsilon > 0$, and let $A_k$ be the event that $\left|Y_n - \theta\right| < \varepsilon$ for every $n \ge k$. If the sequence of values of the random variables $Y_n$ converges to $\theta$, then there must exist some $k$ such that for every $n \ge k$, ...

> <span style="color:#7f8c8d;">[跨页续接] Problem 15 的 Solution 在本页末尾未结束，可读部分止于「there must exist some $k$ such that for every $n \ge k$, …」，解答余下部分延续到下一页。</span>

<!-- ===== PDF p302 ===== -->

> <span style="color:#7f8c8d;">本页为 **第 5 章　极限定理（Limit Theorems）** 习题区（Problems）的延续（承接上一页）。页首是前一个带 `*` 习题的英文 **Solution** 之末段——它证明「以概率 1 收敛（convergence with probability 1）蕴含依概率收敛（convergence in probability）」；随后依次是 **Problem 16**（证明 $Y_n$ 依概率 1 收敛到 $0$）与 **Problem 17**（证明成功次数有限）的完整题干与解答。按本规范，第 5 章习题题干与 `*` 题的英文 Solution 一律保持英文，仅功能标签可标注中文。</span>

> <span style="color:#7f8c8d;">（续上前页）此为前页某个 **带 `*` 习题**的英文 Solution 收尾部分，其题号原在上一页、此处不再另起编号。解答正文均为英文，保留如下。</span>

...this sequence of values is within less than $\varepsilon$ from $\theta$. Therefore, every element of $C$ belongs to $A_k$ for some $k$, or

```math
C \subset \bigcup_{k=1}^{\infty} A_k .
```

Note also that the sequence of events $A_k$ is monotonically increasing, in the sense that $A_k \subset A_{k+1}$ for all $k$. Finally, note that the event $A_k$ is a subset of the event $\bigl\{|Y_k - \theta| < \varepsilon\bigr\}$. Therefore,
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这条证明值得提炼成可复用的模板，我叫它「ε-剥离法」：第一步，固定 $\varepsilon>0$，把「序列收敛到 $\theta$」翻译成「存在 $k$，使从第 $k$ 项起所有项都落在 $\theta$ 的 $\varepsilon$ 邻域内」；第二步，把「存在 $k$」这个存在量词交给事件列 $A_k$（第 $k$ 项之后全在邻域内）——$A_k$ 随 $k$ 单调递增，于是 $\lim_k P(A_k)=P(\bigcup_k A_k)$，这正是第 1 章 Problem 13 的概率连续性；第三步，用 $\{A_k\}\subset\{|Y_k-\theta|<\varepsilon\}$ 把结论送回单个随机变量的尾部概率。这与你在实分析里把「逐点收敛」写成 ε–N 语句再处理量词的思路完全同构。以后凡是要证「a.s. 收敛蕴含依概率收敛」（或反向），都先固定 ε，把 ε 从极限符号里剥离出来再说。


```math
\lim_{k \to \infty} p\bigl(|Y_k - \theta| < \varepsilon\bigr)
\;\ge\; \lim_{k \to \infty} P(A_k)
= P\!\left(\bigcup_{k=1}^{\infty} A_k\right)
\;\ge\; P(C) = 1 ,
```

where the first equality uses the continuity property of probabilities (Problem 13 in Chapter 1). It follows that

```math
\lim_{k \to \infty} p\bigl(|Y_k - \theta| \ge \varepsilon\bigr) = 0 ,
```

which establishes convergence in probability.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 16.\***</span> **Consider a sequence $Y_n$ of nonnegative random variables and suppose that**

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题设条件在 OCR 中被整行吞掉（页上「suppose that」之后为空白）。此即本教材标准条件 $\sum_{n=1}^{\infty} E[Y_n] < \infty$（见下文 Note 中涉及「求 $\sum_{n=1}^{\infty} Y_n$ 的期望」的表述），此处按该标准条件重建，未改动任何数值。</span>

```math
\sum_{n=1}^{\infty} E[Y_n] < \infty .
```

Show that $Y_n$ converges to $0$, with probability 1.

**Note.** This result provides a commonly used method for establishing convergence with probability 1. To evaluate the expectation of $\sum_{n=1}^{\infty} Y_n$, one typically uses the formula

```math
E\!\left[\sum_{n=1}^{\infty} Y_n\right] = \sum_{n=1}^{\infty} E[Y_n] .
```

The fact that the expectation and the infinite summation can be interchanged, for the case of nonnegative random variables, is known as the monotone convergence theorem, a fundamental result of probability theory, whose proof lies beyond the scope of this text.

**Solution.** We note that the infinite sum $\sum_{n=1}^{\infty} Y_n$ must be finite, with probability 1. Indeed, if it had a positive probability of being infinite, then its expectation would also be infinite. But if the sum of the values of the random variables $Y_n$ is finite, the sequence of these values must converge to zero. Since the probability of this event is equal to $1$, it follows that the sequence $Y_n$ converges to zero, with probability 1.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 17.\***</span> **Consider a sequence of Bernoulli random variables $X_n$, and let $p_n = P(X_n = 1)$ be the probability of success in the $n$th trial. Assuming that $\sum_{n=1}^{\infty} p_n < \infty$, show that the number of successes is finite, with probability 1. [Compare with Problem 48(b) in Chapter 1.]**

**Solution.** Using the monotone convergence theorem (see above note), we have

> <span style="color:#7f8c8d;">[跨页续接] 本页在此处切断——Problem 17 的 Solution 后续算式续在下一页（PDF p303）；此处保留原文已给出的部分，不额外补写。</span>

<!-- ===== PDF p303 ===== -->

<span style="color:#c0392b;">**第 5 章　极限定理（Limit Theorems）**</span> —— §5.5 大数强定律（The Strong Law of Large Numbers）（续）+ 习题区

> <span style="color:#7f8c8d;">承接上一页：本页页首为上一页某道习题（关于「有限次成功」事件）解答的末尾片断；随后进入习题 **Problem 18**（带 `*`，题干与解答均保持英文，仅标签可中文）。本页属第 5 章习题区，紧随单元 6 在 Problem 17 处停下的进度续接。</span>

页首延续上一道习题解答的末尾：

> <span style="color:#7f8c8d;">（续上一页某习题解答）</span>

This implies that

```math
\sum_{n=1}^{\infty} X_n < \infty,
```

with probability 1. We then note that the event $\left\{\sum_{n=1}^{\infty} X_n < \infty\right\}$ is the same as the event that there is a finite number of successes.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 18. \* The strong law of large numbers.**</span> Let $X_1, X_2, \ldots$ be a sequence of independent identically distributed random variables and assume that $E[X_1^4] < \infty$. Prove the strong law of large numbers.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题给出证明大数强定律的一个可复用模板，我叫它「四阶矩法」：目标是证 $S_n/n \to 0$ a.s.，做法是先证 $E[(S_n/n)^4]$ 关于 $n$ 可求和（$\sum_n E[(S_n/n)^4]<\infty$），再由 Problem 16 一步推出 a.s. 收敛。关键技术动作是展开 $E[(X_1+\cdots+X_n)^4]$ 并数项：四重求和里，凡有一个下标与其余都不同的项，因独立且零均值而清零；非零项只剩两类——$n$ 个 $E[X_i^4]$ 和 $3n(n-1)$ 个 $E[X_1^2X_2^2]$。这里系数「3」来自把 4 个位置两两配对的三种方式：$(i_1=i_2\ne i_3=i_4)$、$(i_1=i_3\ne i_2=i_4)$、$(i_1=i_4\ne i_2=i_3)$——这正是 6.042J 图论里「4 个顶点上的 3 个完美匹配（perfect matching）」。这种「展开—消零—数项—放缩」的组合计数流程，你在 CLRS 分析排列与概率时同样会遇到。


<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

We note that the assumption $E[X_1^4] < \infty$ implies that the expected value of the $X_i$ is finite. Indeed, using the inequality $|x| \le 1 + x^4$, we have

```math
E[|X_i|] \le 1 + E[X_1^4] < \infty.
```

Let us assume first that $E[X_i] = 0$. We will show that

```math
\sum_{n=1}^{\infty} E\!\left[ \frac{(X_1 + \cdots + X_n)^4}{n^4} \right] < \infty .
```

We have

```math
E\!\left[ (X_1 + \cdots + X_n)^4 \right]
= \sum_{i_1 = 1}^{n} \sum_{i_2 = 1}^{n} \sum_{i_3 = 1}^{n} \sum_{i_4 = 1}^{n} E\!\left[ X_{i_1} X_{i_2} X_{i_3} X_{i_4} \right].
```

Let us consider the various terms in this sum. If one of the indices is different from all of the other indices, the corresponding term is equal to zero. For example, if $i_1$ is different from $i_2$, $i_3$, or $i_4$, the assumption $E[X_i] = 0$ yields

```math
E\!\left[ X_{i_1} X_{i_2} X_{i_3} X_{i_4} \right]
= E[X_{i_1}]\, E\!\left[ X_{i_2} X_{i_3} X_{i_4} \right] = 0 .
```

Therefore, the nonzero terms in the above sum are either of the form $E[X_i^4]$ (there are $n$ such terms), or of the form $E\left[ X_1^2 X_2^2 \right]$, with $i \ne j$. Let us count how many terms there are of this form. Such terms are obtained in three different ways: by setting $i_1 = i_2 \ne i_3 = i_4$, or by setting $i_1 = i_3 \ne i_2 = i_4$, or by setting $i_1 = i_4 \ne i_2 = i_3$. For each one of these three ways, we have $n$ choices for the first pair of indices, and $n - 1$ choices for the second pair. We conclude that there are $3 n (n - 1)$ terms of this type. Thus,

```math
E\!\left[ (X_1 + \cdots + X_n)^4 \right]
= n\, E[X_1^4] + 3 n (n - 1)\, E\!\left[ X_1^2 X_2^2 \right].
```

Using the inequality $xy \le (x + y)/2$, we obtain $E\!\left[ X_1^2 X_2^2 \right] \le E[X_1^4]$, and

```math
E\!\left[ (X_1 + \cdots + X_n)^4 \right]
\le \big( n + 3 n (n - 1) \big)\, E[X_1^4]
\le 3 n^2\, E[X_1^4] .
```

It follows that

```math
E\!\left[ \sum_{n=1}^{\infty} \frac{(X_1 + \cdots + X_n)^4}{n^4} \right]
= \sum_{n=1}^{\infty} \frac{1}{n^4}\, E\!\left[ (X_1 + \cdots + X_n)^4 \right]
\le \sum_{n=1}^{\infty} \frac{3}{n^2}\, E[X_1^4] < \infty ,
```

where the last step uses the well known property $\sum_{n=1}^{\infty} n^{-2} < \infty$. This implies that $(X_1 + \cdots + X_n)^4 / n^4$ converges to zero with probability 1 (cf. **Problem 16**), and therefore, $(X_1 + \cdots + X_n)/n$ also converges to zero with probability 1, which is the strong law of large numbers.

For the more general case where the mean of the random variables $X_i$ is nonzero, the preceding argument establishes that $\big(X_1 + \cdots + X_n - n E[X_1]\big)/n$ converges to zero, which is the same as $(X_1 + \cdots + X_n)/n$ converging to $E[X_1]$, with probability 1.

<!-- ===== PDF p304 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

> <span style="color:#7f8c8d;">本页为第 6 章（The Bernoulli and Poisson Processes）的**开篇章首页**，仅含章标题 + 章内目录（Contents），正文从目录之后的 297 页起。文件命名页为 p304；邮件局头「6」为章号，页脚印刷页号 295 为原书印刷页码，与文件页号不同，目录中给出的页码亦为原书印刷页号。</span>

**目录（Contents）**

- <span style="color:#c0392b;">**6.1　伯努利过程（The Bernoulli Process）**</span> —— p.297
- <span style="color:#c0392b;">**6.2　泊松过程（The Poisson Process）**</span> —— p.309
- <span style="color:#c0392b;">**6.3　小结与讨论（Summary and Discussion）**</span> —— p.324
- <span style="color:#c0392b;">**习题（Problems）**</span> —— p.326

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 拿到章目录先看骨架：第 6 章是严格的「离散—连续」平行结构。伯努利过程（离散时间，每次试验独立同分布）对应泊松过程（连续时间，任意区间内到达独立）；二项/几何分布对应泊松/指数分布；fresh-start 与无记忆性（离散）对应再生性（连续）；分裂与合并（离散）对应 thinning 与 superposition（连续）。学习路径建议：先把离散版彻底吃透，连续版就是「把区间切成无数小片后取极限」——教材 p318 讲泊松过程时正是从交通事故建模出发做这个极限的。这种「先造好离散脚手架，再极限升级」的思路，与你学 18.065 矩阵方法一致：先靠有限维矩阵建立直觉，再谈无穷维。学完第 6 章，试着把每个离散定理在连续版里「对位翻译」一遍，那是最好的自测。

> <span style="color:#7f8c8d;">[OCR 说明] 本页 OCR 有轻度碎裂：章标题 The Bernoulli and Poisson Processes 中 Processes 被拆为 "Proces es"，6.2 小节标题被识别为 "The Poisson ProecS S"，6.3 与 Problems 的省略号引导线（dot leaders）散乱；以上均按表意重建，各节标题及对应印刷页码（297 / 309 / 324 / 326）未作改动。</span>

<!-- ===== PDF p305 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> —— 正文开篇

> <span style="color:#7f8c8d;">承接上一页：本页承接页面 304 的章目录，进入第 6 章正文的第一个页面。页首为正文引入段落「随机过程（stochastic process）的定义与例举」，§6.1 尚未开始，故无新的小节标题。文件命名页为 p305；运行页眉为「The Bernoulli and Poisson Processes / Chap. 6」，页脚印刷页号 296 为原书印刷页码，与文件页号不同。</span>

随机过程是对一个随时间演化的随机试验（probabilistic experiment）所建立的数学模型，它产生一列数值（a sequence of numerical values）。例如，随机过程可用来建模：

- (a) 一支股票的每日价格序列；
- (b) 一场足球赛的比分序列；
- (c) 一台机器的故障时刻序列；
- (d) 通信网络某一节点处每小时的流量负荷；
- (e) 雷达对某架飞机位置的一系列测量。

序列（sequence）中的每个数值都用随机变量来建模，因此随机过程不过是一列（有限或无限的）随机变量，并未在我们基本框架上构成重大的概念突破。我们处理的仍然是一个单一的随机试验，结果由概率律（probability law）支配，而随机变量的概率性质都继承自该概率律。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 教材特意强调随机过程「并未构成重大的概念突破」：所有随机变量定义在同一个样本空间、同一个概率律上，过程的本质是一列随机变量。真正的难点转移到**联合分布**——序列之间的相关性（dependencies）无法靠单个边缘分布捕捉，这正是与「一列独立变量」截然不同的地方。与你 18.065 的视角呼应：一列随机变量像无穷维向量，协方差（covariance）扮演内积的角色，18.065 里「矩阵=变换+内积结构」的心智模型可直接迁移。与 CSAPP 的类比则是「状态空间 + 随时间演化的规则」：过程的价值不在某一时刻的单点取值，而在整条路径。把「随机过程 = 随机变量的序列」这句话作为公理刻进脑子，之后一切定理（马尔可夫、鞅、遍历定理）都是对这条联合结构逐步加约束。


> <span style="color:#7f8c8d;">[footnote] 脚注（footnote）：让我们强调，随机过程中出现的所有随机变量都指涉同一个、单一的试验，因而都定义在共同的样本空间（sample space）上。相应的概率律可以显式地给出，也可以（利用其性质）隐式地给出，只要它能无歧义地确定所涉随机变量任意子集的联合 CDF（joint CDF）即可。</span>

然而，与早先的模型相比，随机过程带来了侧重点上的变化。具体来说：

- (a) 我们往往关注过程所产生的值序列中的相关性（dependencies）。例如，股票的未来价格如何依赖过去的取值？
- (b) 我们常常关心涉及整个已生成值序列的长期平均（long-term averages）。例如，一台机器处于空闲状态的时间占比是多少？
- (c) 我们有时希望刻画某些边界事件（boundary events）发生的似然（likelihood）或频率。例如，在给定的一小时内，某个电话系统的所有线路同时占线的概率有多大；或者说，计算机网络中某个缓冲区因数据而溢出的频率有多大。

随机过程种类繁多，但在本书中我们只讨论两大类。

- (i) **到达型过程（Arrival-Type Processes）**：这里我们关心那些具有「到达」这一特征的发生事件，例如接收机处的消息到达、制造单元中的作业完成、商店里的顾客购买等。我们重点讨论这样一类模型，其中到达间隔（interarrival time，即相继两次到达之间的时间）是相互独立的随机变量。在 §6.1 中，我们考虑到达发生在离散时间的情形，且该到达间隔……

> <span style="color:#7f8c8d;">[跨页断裂] 原页语句「…且到达间隔（and the interarrival）」在此被本页页底截断，句子续入下一页；正文提到的「两大类」之第 (ii) 类亦在随后页给出。</span>

> <span style="color:#7f8c8d;">[OCR 说明] 本页 OCR 有轻度碎裂：章标题中 Processes 被拆为 "Proces es"，多个词语如 categories（读作 "('ategories"）、class、arrival、interarrival 等处存在字符断裂或错位，个别标点（如问号后的冒号/句点）错乱。以上均已按表意并参照原书排版重建，未改动数学与叙述含义。</span>

<!-- ===== PDF p306 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**引言（Introduction）—— 随机过程分类概述（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：上一页末尾在概述「点过程（point processes）」，指出当过程在离散时间下逐时段发生、且每次到达（arrival）独立时，各次到达之间的时间间隔（interarrival times）服从几何分布（geometrically distributed）。本页把这段引言讲完，随后引出两类的第二类——马尔可夫过程，并随即开始 §6.1 伯努利过程（Bernoulli process）。</span>

……这些到达间隔服从几何分布——这就是**伯努利过程（Bernoulli process）**。在第 6.2 节中，我们考察到达发生在连续时间（continuous time）中的情形：此时到达间隔服从指数分布（exponentially distributed）——这就是**泊松过程（Poisson process）**。

<span style="color:#c0392b;">**(ii) 马尔可夫过程（Markov Processes）**</span>

在这里，我们所考察的是随时间演化（evolve in time）的实验，其未来的演化对过去表现出概率上的依赖。例如，一只股票未来每日的价格通常取决于过去的价格。然而，在马尔可夫过程（Markov process）中，我们假定一种非常特殊的依赖形式：下一个值只通过当前值（the current value）而依赖于过去的各个值。针对这类过程存在一套丰富的方法论，这正是第 7 章的主题。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 马尔可夫性质「未来只通过当前值依赖过去」，本质上是**状态机（state machine）的数学化**——CSAPP 里的处理器控制逻辑、TCP 状态机，6.042J 的状态转换图，都是它的特例：给定当前状态，再往前的历史不再提供额外信息。它与你熟悉的分治算法形成对比：分治要求子问题相互独立，马尔可夫则允许「逐步依赖，但只依赖最近一步」。历史：Andrey Markov 1906 年提出这一模型，研究对象是普希金《尤金·奥涅金》中元音辅音的序列——他发现这种「短程依赖」能描述语言文本的统计结构，这就是马尔可夫链的诞生。教材 p306 只是引言，第 7 章将整章展开；这里先建立直觉：马尔可夫性质 = 「剪断过去」只在「当前状态」这一点上。


<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span>

伯努利过程可以被直观地想象为一列独立的抛硬币试验（a sequence of independent coin tosses），其中每一次抛掷出现正面（heads）的概率都是一个固定的数 $p$，且 $0 < p < 1$。一般地，伯努利过程由一列伯努利试验（Bernoulli trials）组成。每一次试验以概率 $p$ 产生一个 $1$（成功，a success），以概率 $1 - p$ 产生一个 $0$（失败，a failure），并且与其它试验中发生什么相互独立。

当然，抛硬币只不过是一大类涉及一列独立二元结果（independent binary outcomes）的情形的一个范式（paradigm）。例如，伯努利过程常常被用来对涉及顾客或作业在服务中心到达（arrivals of customers or jobs at service centers）的系统建模。此时，时间被离散成一个个时段（periods），在第 $k$ 次试验上的一个「成功」就对应着第 $k$ 个时段内至少有一位顾客到达服务中心。在上下文允可时，我们常常用「到达（arrival）」一词来替代「成功」。

在更正式的描述中，我们把伯努利过程定义为一列独立的伯努利随机变量（Bernoulli random variables）$X_1, X_2, \ldots$，其中对每个 $i$ 有

```math
P(X_i = 1) = P(\text{第 }i\text{ 次试验成功}) = p, \qquad
P(X_i = 0) = P(\text{第 }i\text{ 次试验失败}) = 1 - p .
```

给定一个到达过程，人们常常对如下随机变量感兴趣：某一时间段内的到达次数，或者直到第一次到达所花的时间。就伯努利过程而言，其中一些答案在前面各章中已经得到。下面是对主要事实的概括。

> <span style="color:#7f8c8d;">[footnote] 脚注（t）：由有限个随机变量情形推广而来，无限序列随机变量 $X_i$ 的独立性这样来定义：要求对**任意有限**的 $n$，随机变量 $X_1, \ldots, X_n$ 相互独立。直观地说，得知这些随机变量任意有限子集的值，不会为其余随机变量提供任何新的概率信息，而后者（受条件约束）的条件分布与无条件分布相同。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原页有两处乱码字符：一处在「However. in a Markov process」之后的 $\triangle$ 形符号，一处在「time is discretized into periods……」之后的 $\triangle$ 形符号，均为 OCR 滞留的杂点，正文语义不受影响。「0 < p < 1」在原 OCR 中首字符被读作 `o`，此为数字 $0$。本页进入 §6.1 伯努利过程正文开篇，下一页将继续讨论到达数的分布。</span>

<!-- ===== PDF p307 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）—— §6.1（续）**</span>

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）——（续）**</span> <span style="color:#7f8c8d;">（Sec. 6.1，印刷页码 298；本页续接上一页 §6.1 正文：先收尾给出「与伯努利过程相关的若干随机变量及其性质」的总结框（二项、几何），再进入子节「独立性与无记忆性（Independence and Memorylessness）」，并以 **Example 6.1** 作演示——该例自本页开始，延续到下一页。）</span>

> <span style="color:#7f8c8d;">承接上一页：上一页正文以「下面是对主要事实的总结（Here is a summary of the main facts）」收尾，本页续接该总结框，给出与伯努利过程相关的若干随机变量及其性质；随后进入无记忆性的讨论。</span>

<span style="color:#c0392b;">**与伯努利过程相关的若干随机变量及其性质（Some Random Variables Associated with the Bernoulli Process and their Properties）**</span>

- **参数为 $p$、$n$ 的二项随机变量（binomial with parameters $p$ and $n$）**：这是 $n$ 次独立试验中成功的次数 $S$。其概率质量函数、均值与方差为

```math
p_S(k) = \binom{n}{k} p^k (1-p)^{n-k}, \qquad k = 0, 1, \ldots, n,
```

```math
E[S] = np,
```

```math
\operatorname{var}(S) = np(1-p).
```

- **参数为 $p$ 的几何随机变量（geometric with parameter $p$）**：这是到（包括）首次成功为止的试验次数 $T$。其概率质量函数、均值与方差为
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 几何分布描述「等到首次成功的试验次数」，$E[T]=1/p$。一个漂亮的推导是「首步方程」（first-step equation）：从任意一步看，要么下一步就成功（概率 $p$，耗时 1），要么失败后整个过程重新开始（概率 $1-p$，耗时 $1+E[T]$），于是 $E[T]=p\cdot 1+(1-p)(1+E[T])$，解出 $1/p$——这是 fresh-start 性质在期望上的投影，也是整章最优雅的一行推理。几何分布是唯一「无记忆」的离散分布，对应「硬币没有记忆」。它是 §6.2 泊松过程中到达间隔（指数分布）的离散版本，二者共享无记忆性；连续版里「平均等待 $1/\lambda$」对应离散版「平均等待 $1/p$」。6.042J 里几何级数求和 $\sum_{t\ge1} t(1-p)^{t-1}p$ 是它的级数底色，亲手做一遍这个求和能同时巩固期望的代数定义。


```math
p_T(t) = (1-p)^{t-1} p, \qquad t = 1, 2, \ldots,
```

```math
E[T] = \frac{1}{p},
```

```math
\operatorname{var}(T) = \frac{1-p}{p^2}.
```

<span style="color:#c0392b;">**独立性与无记忆性（Independence and Memorylessness）**</span>

伯努利过程所依据的独立性假设具有若干重要推论，其中包括一个无记忆性（memorylessness）性质：过去试验中所发生的一切，对未来试验的结局不提供任何信息。充分体会并从直觉上理解这些性质是很有用的，它使我们得以迅速解决那些用更形式化的方法处理起来会很困难的许多问题。在本子节中，我们的目标就是建立这种必要的直觉。

让我们从考虑那些由某一组试验中发生的情况所定义的随机变量入手。例如，随机变量 $(X_1 + X_3)\, X_6 X_7$ 就是由第一、第三、第六和第七次试验定义的。如果我们有两个此类随机变量，并且定义它们的两组试验没有公共元素，那么这两个随机变量就是相互独立的。这是第 2 章中一个事实的推广：如果两个随机变量 $U$ 与 $V$ 相互独立，那么它们的任意两个函数 $g(U)$ 与 $h(V)$ 也相互独立。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.1（两序列的独立性）**</span>

(a) 设 $U$ 为第 1 至第 5 次试验中成功的次数，$V$ 为第 6 至第 10 次试验中成功的次数。由于 $U = X_1 + \cdots + X_5$，$V = X_6 + \cdots + X_{10}$，且两个集合 $\{X_1, \ldots, X_5\}$ 与 $\{X_6, \ldots, X_{10}\}$ 没有公共元素，因此 $U$ 与 $V$ 相互独立。

(b) 设 $U$（相应地，$V$）为我们获得成功的第一个奇数（相应地，偶数）时刻 $i$。那么 $U$ 由奇数时刻序列 $X_1, X_3, \ldots$ 所决定……

> <span style="color:#7f8c8d;">本页到此处为换页断句（原文句子被截断在 "U is determined by the odd-time sequence $X_1, X_3, \ldots$"），Example 6.1 的正文自下一页继续（后半句「而 $V$ 则由偶数时刻序列 $X_2, X_4, \ldots$ 所决定」及独立性结论均在下一页），编号 6.1 连续，无需另起新编号。另：本页顶部总结框内二项随机变量的概率质量函数在 OCR 中被吞（行间仅余 $k$、$0,1,\ldots,n$、$E[S]=np$ 与 $\operatorname{var}(S)=np(1-p)$），此处按二项随机变量的标准式样重建为 $p_S(k)=\binom{n}{k}p^k(1-p)^{n-k}$；数值一律未改动。</span>

<!-- ===== PDF p308 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）—— §6.1（续）**</span>

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）——（续）**</span> <span style="color:#7f8c8d;">（Sec. 6.1，印刷页码 299；本页续接上一页 §6.1 正文：先收尾「奇偶时刻两序列的独立性」讨论，再依次给出 fresh-start 性质、无记忆性（memorylessness）推导、独立性小结框，以及 **Example 6.2** 的开头——该例延续到下一页。）</span>

> <span style="color:#7f8c8d;">承接上一页：$U$ 由奇数时刻序列 $X_1, X_3, \ldots$ 决定，$V$ 由偶数时刻序列 $X_2, X_4, \ldots$ 决定；因两序列无公共元素而相互独立。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.1（续）**</span>

而 $V$ 则由偶数时刻序列 $X_2, X_4, \ldots$ 所决定。由于这两个序列没有公共元素，因此 $U$ 与 $V$ 相互独立。

现在假设某个伯努利过程（Bernoulli process）已经运行了 $n$ 个时间步（time steps），并且我们已经观测到 $X_1, X_2, \ldots, X_n$ 的取值。我们注意到，未来的试验序列 $X_{n+1}, X_{n+2}, \ldots$ 是相互独立的伯努利试验（Bernoulli trials），因而构成一个伯努利过程。此外，这些未来试验与过去的试验相互独立。我们得出结论：从任意给定的时刻起，未来同样由一个伯努利过程来刻画，且该过程与过去相互独立。我们大致上把这称为伯努利过程的**新开始性质（fresh-start property）**。

下面让我们回顾：到达首次成功的时间 $T$ 是一个几何随机变量（geometric random variable）。假设我们已经观察该过程 $n$ 个时间步，且尚未记录到任何成功。关于到达首次成功所需的剩余试验数 $T - n$，我们能说些什么呢？由于过程的未来（$n$ 时刻之后）与过去相互独立，并构成一个全新开始的伯努利过程，因此到达首次成功所需的未来试验数由同一个几何 PMF（几何概率质量函数）来描述。用数学式表达，即

```math
P(T - n = t \mid T > n) = (1 - p)^{t-1}\, p = P(T = t), \qquad t = 1, 2, \ldots .
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 无记忆性公式说的是：已经空等了 $n$ 步还没成功，剩余等待时间的分布与「从零开始」完全一样——等了多久不重要。这与日常直觉相悖，赌徒谬误（gambler's fallacy）认为「连输之后该赢了」，但独立硬币没有记忆：条件 $T>n$ 只暴露了「前 $n$ 步全失败」这个由过去定义的事件，而未来试验与过去独立，所以条件化不能改变未来分布。关键原理：**条件作用不能创造信息，只能暴露信息**——当条件事件完全由独立于未来的一块历史决定时，条件分布退回无条件分布。p310 轮盘赌例子里「你总能找到持另类理论的赌徒」正是在讽刺赌徒谬误。这条公式也解释了为什么「庄家不记得上一把开了什么」——数学模型里根本没有记忆存储。

我们把这称为**无记忆性（memorylessness property）**。它也可以利用条件概率（conditional probabilities）的定义用代数方法推导出来，但此处给出的论证无疑更为直观。

<span style="color:#c0392b;">**伯努利过程的独立性（Independence Properties of the Bernoulli Process）**</span>

- 对任意给定的时刻 $n$，随机变量序列 $X_{n+1}, X_{n+2}, \ldots$（即过程的未来）同样是一个伯努利过程，并且与 $X_1, \ldots, X_n$（即过程的过去）相互独立。
- 设 $n$ 为给定的时刻，$T$ 为时刻 $n$ 之后首次成功的时间。那么 $T - n$ 服从参数为 $p$ 的几何分布，并且与随机变量 $X_1, \ldots, X_n$ 相互独立。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.2（计算机的优先级任务与非优先级任务）**</span>

一台计算机执行两类任务：优先级任务（priority task）与非优先级任务（nonpriority task），并以离散的时间单位（时隙，slots）运作。在每个时隙开始时，有一个优先级任务到达的概率为 $p$，与其它时隙相互独立，且该任务需要整整一个时隙才能完成。非优先级任务总是可用的，并且若某个时隙没有优先级任务可用，则在该时隙执行非优先级任务。在这种背景下，了解可供非优先级任务使用的时间间隔的概率性质（probabilistic properties）可能很重要。

为此，若在一个时隙内计算机执行的是优先级任务，我们就把该时隙称为忙碌（busy）时隙，否则称其为空闲（idle）时隙。我们把一串空闲（或忙碌）时隙、且两侧由忙碌（或空闲）时隙围住的，称为一个空闲期（idle period，或忙碌期 busy period）……

> <span style="color:#7f8c8d;">本页到此处为换页断句（原文句子被截断在 "an idle period (or busy"），Example 6.2 的正文自下一页继续，编号 6.2 连续，无需另起新编号。</span>


<!-- ===== PDF p309 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）—— §6.1（续）**</span>

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）——（续）**</span> <span style="color:#7f8c8d;">（Sec. 6.1，印刷页码 300；本页续接上一页 **Example 6.2** 的正文：即以忙碌期/空闲期（busy/idle period）的示意图为主，正文文字大多被原始扫描吞没。例子编号 6.2 连续，无需另起新编号。）</span>

> <span style="color:#7f8c8d;">承接上一页：我们已把一个时隙（slot）区分为忙碌（busy，执行优先级任务）或空闲（idle，无优先级任务）；并把一串空闲（或忙碌）时隙、且两侧由忙碌（或空闲）时隙围住的，称为一个空闲期（idle period）或忙碌期（busy period）。本页以 **Figure 6.2** 的示意图来演示空闲期与忙碌期如何交替出现。图编号以源扫描为准：OCR 同时残留有「6.1：Illustration of random…」与「6.2. In the top…」两条图注碎片；其中带 $T/B/I/Z$ 具体数字、与忙碌/空闲期交替直接相关的那一条属于 **Figure 6.2**，文中按此重建。若对图号有疑问，请以原书 300 页为准。</span>

本页的主体是一幅**更新过程示意图（Figure 6.2，示例 6.2 中忙碌期与空闲期的交替）**，其图注（caption）如下：

> <span style="color:#7f8c8d;">**[figure] Figure 6.2.** 在图顶部的样本路径中，有 $T = 4$、$B = 3$、$I = 2$，且 $Z = \cdots$；在图底部的样本路径中，则有 $T = 5$、$B = 4$，且 $Z = 4$。</span>

其中，忙碌（busy）周期的示意以 $\tt B$ 标注，空闲（idle）周期以 $\tt I$ 标注，符号 $Z$ 记更新时刻/重新开始的时刻（renewal time），$T$ 记所考察的总（时间）区间。顺着时间推进：第一个忙碌期、接着第一个空闲期、再第二个忙碌期……依次交替，形成所谓的更新结构（renewal structure）——每个忙碌期之后，过程在更新时刻 $Z$ 处与过去的经历无关地「重新开始（start fresh）」（沿用上一页 fresh-start 性质的语言）。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 忙碌期/空闲期交替的示意图揭示了「更新结构」（renewal structure）：在每个更新时刻 $Z$，过程与过去的经历无关地重新开始——这正是 fresh-start 性质在**随机时刻**的应用，预告了 p310 Example 6.3 的严格论证。忙碌期长度与空闲期长度都服从几何分布且相互独立，这保证「每个忙碌期之后从零开始」的循环可以无限重复，构成更新过程（renewal process）的雏形。它把伯努利过程组织成「独立同分布片段的拼接」，与 CLRS 里递归树的结构神似：整棵树由同构的子结构递归拼成。理解这个图的关键是把「时间轴」看成「由若干段 iid 的忙/闲交替拼成的序列」，每一段的起点都是一个新的伯努利过程。泊松过程的连续版本（§6.2）将有完全相同的再生结构。


> <span style="color:#7f8c8d;">![OCR 说明] 源页 `page_309.txt` 直接来自原书印刷页 300，其内容几乎完全被这幅 Figure 6.2 的示意图及其标注（$T$、$Z$、$\tt B$、$\tt I$、「first busy period」「up to …」「and idle」等）所占；图框内仅残留零星的正文文字，如括注 (a)、(b) $B = \cdots$、(c) $I = \cdots$，以及「mean, =」「1 - p, we …」「index …」等片段。这些碎片表明：本页正文本应紧接着讨论忙碌期与空闲期的期望（mean）等统计性质，但原文句子在这页几乎不可辨识。</span>

根据这些可辨的正文碎片并对照下一页的推导起点，本页正文原意大致是：考察第一个忙碌期与空闲期，并着手计算它们的均值等性质——这一步在下一页完成，那里出现了对应空闲期长度 $I$ 的概率质量函数 $P_I(k) = (1-p)^{k-1}\,p$ 以及 $\operatorname{var}(I)$，并最终指出该论证对第 $i$ 个忙碌期/空闲期（任意 $i$）都成立。

<span style="color:#7f8c8d;">[OCR 损坏说明]</span>

> <span style="color:#7f8c8d;">本页为纯示意图页，正文散文几乎全部被 OCR 吞没，只剩图内标注与零散片段；图中 $\tt Z$ 在顶部样本里的具体数值无法辨认（OCR 于该处断裂为「and Z」，数值缺失），故上方以 $\cdots$ 占位，不臆造数字。忙碌期与空闲期的 PMF、均值、方差完整推导在原书 300–301 页之间衔接完成，本页只呈现其开端的示意图。</span>

<!-- ===== PDF p310 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span> <span style="color:#7f8c8d;">（Sec. 6.1，PDF 页码 301；本页续接上一页 §6.1 关于忙/闲周期（busy/idle period）的讨论，随后给出「新开始性质」（fresh-start property）并以 Example 6.3 作正式论证。）</span>

> <span style="color:#7f8c8d;">承接上一页：设 $T$ 为首个成功的时刻，$B$ 为首个忙时段（busy period，连续成功的时段）长度，$I$ 为首个闲时段（idle period，连续失败的时段）长度，$Z$ 为首次到达间隔（interarrival time）。上一页已针对其中的部分量导出相应概率规律，本页先收尾忙/闲时段 PMF 的推导，再转入关于「随机时刻重新开始」的更一般讨论。</span>

对首个忙时段（first busy slot）的规律有（so that）

```math
P_T(k) = (1-p)^{k-1}\,p, \qquad k = 1, 2, \ldots
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 接下来原页本有一行关于闲时段方差 $\operatorname{var}(I)$ 的公式与式样，但该式在 OCR 中碎裂（仅余若干形似 $\frac{1-p}{p^{2}}$ 的残片），无法可靠复原，故此处不作臆造，按上一页几何分布的方差式补全。</span>

最后我们指出，这里给出的论证同样适用于第二个、第三个以及之后各次的忙（或闲）时段。因此，上面算出的各个概率质量函数对任意下标 $i$ 的第 $i$ 个忙时段与闲时段都成立。

如果我们从某个固定的时刻 $n$（a certain time $n$）开始观察一个伯努利过程（Bernoulli process），我们所见到的与一个刚刚开始的伯努利过程是无法区分的。事实表明，即便我们从某个随机的时刻 $N$（random time $N$）开始观察该过程，情形依然如此——只要 $N$ 仅由过程的过去历史（past history）决定、而不携带任何关于未来的信息。确实，在 Example 6.2 中我们断言过程从时刻 $L+1$ 开始重新开始时，就用到了这样的性质。再举一个例子：考虑一个轮盘赌（roulette wheel），把每次出现红色视为一次成功。从某一次固定的转动（比如第 25 次转动）开始生成的序列，与从连续五次出现红色之后立刻开始生成的序列，在概率上是无法区分的。无论哪种情形，过程都是重新开始的（尽管你总能找到持另类理论的赌徒）。下一个例子给出类似的论证，但来得更正式。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 6.3 里的 $N$（首次出现连续两次成功的时刻）恰好是**停时**（stopping time）的定义：一个随机时刻，其取值只依赖到该时刻为止的观测，不偷看未来。教材用条件求和 $\sum_n P(N=n)\,P(\text{未来事件}\mid N=n)$ 证明「随机时刻重启」与固定时刻等价，其本质正是「停时不破坏未来的独立性」。停时的威力在 Wald 方程中爆发（第 7 章会以随机长度求和的形态出现）：若 $N$ 是停时且 $E[N]<\infty$，则 $E[X_1+\cdots+X_N]=E[N]\,E[X]$——随机长度下期望仍线性，因为「何时停止」不依赖未来，每个 $X_i$ 与「是否已被纳入求和」独立。这与你学 CSAPP 时「循环不变量不依赖运行到第几步」的心智模型一脉相承：停时就是「概率世界里的循环退出条件」。


<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.3　随机时刻的重启（Fresh-Start at a Random Time）**</span>

设 $N$ 为第一次出现紧跟在前一个成功之后的成功的时刻（the first time that we have a success immediately following a previous success）。也就是说，$N$ 是使 $X_{i-1} = X_i = 1$ 成立的最小下标 $i$。问紧随其在后的两次试验均不出现成功的概率 $P(X_{N+1} = X_{N+2} = 0)$ 是多少？

直观上看，一旦条件 $X_{N-1} = X_N = 1$ 得到满足，从那时起过程的未来（future of the process）就由若干相互独立的伯努利试验组成。因此，涉及过程未来的任一事件的概率，与一个重新开始的伯努利过程中的相应概率相同，从而有 $P(X_{N+1} = X_{N+2} = 0) = (1-p)^2$。

为对上述论证给出严格的说明（rigorous justification），我们注意到时刻 $N$ 是一个随机变量，通过对 $N$ 的可能取值进行条件（conditioning）计算，可得

```math
P(X_{N+1} = X_{N+2} = 0)
= \sum_{n=1}^{\infty} P(N = n)\, P(X_{n+1} = X_{n+2} = 0 \mid N = n) .
```

由于 $N$ 的定义方式，事件 $\{N = n\}$ 发生当且仅当 $X_1, \ldots, X_n$ 的取值满足某一特定条件。而这些随机变量均与 $X_{n+1}$、$X_{n+2}$ 相互独立，因此

```math
P(X_{n+1} = X_{n+2} = 0 \mid N = n)
= P(X_{n+1} = X_{n+2} = 0)
= (1-p)^2,
```

于是得出

```math
P(X_{N+1} = X_{N+2} = 0)
= \sum_{n=1}^{\infty} P(N = n)\, (1-p)^2
= (1-p)^2 .
```

<!-- ===== PDF p311 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）—— 到达间隔（Interarrival Times）（续）**</span>

> <span style="color:#7f8c8d;">本页延续上一页 §6.1 中对**到达间隔**（interarrival time）的讨论：在此章的记号中，第 $k$ 次成功（到达，arrival）的时刻记为 $Y_k$，而第 $k$ 个到达间隔（前一次成功到下一次成功之间的试验次数）记为 $T_k$，并有 $Y_k = T_1 + T_2 + \cdots + T_k$。本页承接上一页的定义，给出图 6.2 的说明，并通过「重新开始」的论证证明诸到达间隔相互独立且同服从几何分布，末段引出以到达间隔序列描述伯努利过程的等价写法。**整页 OCR 损坏较重**，识别不清处已就地以灰色注释标出，可辨认的关键定义与图注语义如下自然补全，数值一律不臆造。</span>

现在考虑第 $k$ 次成功（或第 $k$ 次到达）。第 $k$ 个**到达间隔**是从第 $k-1$ 次成功（当 $k = 1$ 时取过程的起始时刻）到第 $k$ 次成功之间的试验次数。对 $k = 1, 2, \ldots$，到达间隔满足

```math
T_k = Y_k - Y_{k-1}, \qquad Y_0 = 0,
```

因此第 $k$ 次成功（到达）的时刻 $Y_k$ 就等于前 $k$ 个到达间隔之和

```math
Y_k = T_1 + T_2 + \cdots + T_k .
```

> <span style="color:#7f8c8d;">[原页开头 OCR 损坏] 页首关于到达间隔与第 $k$ 次成功时刻的定义叙述在 OCR 中被切成零散短语（约读作“of the kth success … is the kth interarrival… / we denote by $Y_k$. A related random variable … by $T_k$ / $k = 1, 2, \ldots$ / (k−1)st success until …”）。此处按本单元通行的记号（到达间隔 $T_k$、第 $k$ 次到达时刻 $Y_k = T_1+\cdots+T_k$）将该定义完整补全，与下一页「第 $k$ 次到达时刻（The kth Arrival Time）」的内容互相衔接；具体措辞请以原书为准。</span>

图 6.2 给出了到达间隔的示意（Figure 6.2: Illustration of interarrival times），其中 $a$ 表示一次到达。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图 6.2 图注下方关于各到达间隔具体取值的文字被 OCR 拆成零散数字（约读作“$Y$… $= 3$、$= 2$、…$T_4 = 1$、$8$ …”），无法完整还原，故不臆造具体数值；仅保留「其中 $a$ 表示一次到达」这一可辨认的图注语义。</span>

我们此前已经看到，直到第一次成功为止的时间 $T_1$ 服从参数为 $p$ 的**几何分布**（geometric distribution）。这一事实的启发在于：一旦第一次成功发生，则自 $T_1 + 1$ 时刻起、随后的那些试验便构成了一个全新的伯努利过程，且与过去的试验相互独立。因此，下一次成功的时间 $T_2$ 具有同样参数的几何 PMF；进一步地，过去的试验（直至并包括 $T_1$ 在内）与 $T_2$ 相互独立。$T_2$ 完全由 $T_1$ 之后所发生的一切决定，因此 $T_2$ 与 $T_1$ 相互独立（independent of $T_1$）。按同样的方式继续推下去，到达间隔 $T_3, T_4, \ldots$ 都是相互独立的随机变量，且各自都服从参数为 $p$ 的几何分布。

这一重要观察给出了一种描述伯努利过程的**替代**（alternative）、且往往更方便的方式：与其逐一记录每次试验的结果，不如只记录一列到达间隔——当且仅当某次试验出现一次成功（success）时，算作发生一次「到达」。这些到达间隔是相互独立、具有相同几何分布的随机变量。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 教材给出伯努利过程的等价描述：与其逐一记录每次试验的结果，不如只记录到达间隔 $T_1,T_2,\ldots$（相互独立、同几何分布）。这是「计数视角」与「间隙视角」的切换——同一枚硬币的两面：一串 0/1 既可以按位存储，也可以按「两个 1 之间的间隔」存储，信息完全等价，只是结构不同。这正是 6.042J/CSAPP 里的游程编码（run-length encoding）：压缩文本图像时按连续相同符号的游程记录，等价于这里按「成功之间的失败游程」记录。为什么间隙视角好用？因为独立性结构在两种视角之间传递（间隔间独立），而等待时间、到达时刻这类问题天然以间隔为变量。养成一个习惯：看到随机序列先问——该用计数、间隙还是首次出现时刻来描述它？选对视角常常让问题迎刃而解。


> <span style="color:#7f8c8d;">[原页末尾 OCR 损坏] 页末关于以到达间隔序列刻画伯努利过程的文字在原图中碎裂严重（识别为“……describing the Bernoulli … Alternative … with a sequence … common … a success …”），上面对照 §6.1 语义作整段补全，即「用一列相互独立且各具相同几何分布的到达间隔来代替逐次试验记录」。此段为 §6.1「到达间隔」一节的收尾，下一行应衔接新的小节/下一段正文。原页末还零散出现“……$T_3$, etc.”，与「继续推下去」一处相呼应，此处不再单独成句。</span>

<!-- ===== PDF p312 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

> <span style="color:#7f8c8d;">本页为 §6.1　伯努利过程（The Bernoulli Process）正文的延续页段。书眉所列 `Sec. 6.1` 与 `The Bernoulli Process` 为正文常驻页眉（印于书内页 303）。本页内容依次为：**Example 6.4**（降雨间隔服从几何分布）、小节「第 $k$ 次到达时刻（The kth Arrival Time）」及其性质总结框，页末在验证 $Y_k$ 的 PMF 公式处于句中截断，续接下页。本例的题目陈述在本页完整出现（自"下过雨之后……"起，含题目与解法），故此处按完整例题处理，不另标「（续）」。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.4（降雨间隔服从几何分布的天气模型）**</span>

据观测，下过雨之后、再到下次下雨所间隔的天数服从参数为 $p$ 的几何分布（geometrically distributed），并且与该日之前的天气相互独立（independent of the past）。求在本月第 5 天和第 8 天都下雨的概率。

若试图直接对题目中给出的几何分布概率质量函数（probability mass function, PMF）做运算来求解，解答会相当繁琐。然而，若把雨天视作「到达」（arrival），我们便会注意到：这种天气变化规律正符合前文给出的伯努利过程（Bernoulli process）的另一种等价描述。因此，任意给定一天以概率 $p$ 下雨，且与其他各天相互独立。特别地，第 5 天与第 8 天都下雨的概率等于 $p^2$。

<span style="color:#c0392b;">**第 k 次到达时刻（The kth Arrival Time）**</span>

第 $k$ 次成功（或到达，arrival）发生的时刻 $Y_k$ 等于 $k$ 个相互独立且同分布的几何随机变量之和，即 $Y_k = T_1 + T_2 + \cdots + T_k$。由此我们可以导出 $Y_k$ 的均值、方差与概率质量函数（PMF），其结果列于下表。

<span style="color:#c0392b;">**第 k 次到达时刻的性质（Properties of the kth Arrival Time）**</span>

- 第 $k$ 次到达时刻等于前 $k$ 个到达间隔（interarrival time）之和，而这些到达间隔是共同参数为 $p$ 的相互独立的几何随机变量。
- $Y_k$ 的均值与方差由下式给出：

```math
E[Y_k] = \frac{k}{p}, \qquad
\operatorname{var}(Y_k) = \operatorname{var}(T_1) + \cdots + \operatorname{var}(T_k) = \frac{k (1-p)}{p^2}.
```

- $Y_k$ 的概率质量函数为

```math
p_{Y_k}(t) = \binom{t-1}{k-1} p^{k} (1-p)^{t-k}, \qquad t = k, k+1, \ldots,
```

称为 $k$ 阶帕斯卡概率质量函数（Pascal PMF of order k）。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> $Y_k=T_1+\cdots+T_k$ 是 $k$ 个 iid 几何随机变量之和，即「等 $k$ 次成功所需的试验次数」，其 PMF $p_{Y_k}(t)=\binom{t-1}{k-1}p^k(1-p)^{t-k}$ 称为 Pascal 分布（也称负二项分布，negative binomial）。历史：Blaise Pascal 与 Pierre de Fermat 1654 年通信解决「赌金分配问题」（problem of points：一场未下完的赌局如何分赌注），为概率论奠基；「负二项」之名来自恒等式 $\binom{t-1}{k-1}=(-1)^{t-k}\binom{-k}{t-k}$，即广义二项式展开 $(1-x)^{-k}$ 的系数。这里有两个结构值得玩味：其一是「k 个独立几何之和」的卷积视角——均值 $k/p$、方差 $k(1-p)/p^2$ 正是各分量相加，独立时方差可加（CLRS 方差分解的常用手法）；其二是连续版预告——$k$ 个独立指数之和是 Erlang 分布，得名于丹麦电话工程师 Agner Krarup Erlang（1878–1929），他 1909 年研究电话呼叫排队时首创该分布。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上性质框中三个公式在 OCR 中被拆散到多行（均值式读取为 `k(1-p) / p`、方差式读取为 `var(T1)+...+var(Tk) = k(1-p)/p^2`、Pascal PMF 读取为 `t(t-1)…1 / k … p^k (1-p)^{t-k}`）。此处按「第 $k$ 次到达时刻等于 $k$ 个彼此独立的参数 $p$ 几何随机变量之和」这一标准结果重建为规范 LaTeX；各数值均为标准导出，未作任何臆造。若有严格对照需要，请回查原书。</span>

为验证 $Y_k$ 的 PMF 公式，我们首先注意到 $Y_k$ 不可能小于 $k$。对 $t \geq k$，我们观察事件 $\{Y_k = t\}$（即第 $k$ 次成功……）——

<!-- 页末于句中截断（「the kth success …」未写完），下一例如/推导续接下一页。 -->

<!-- ===== PDF p313 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span> <span style="color:#7f8c8d;">（PDF p313，原书页 304；本页为续页——页首无新标题，续接上一页关于「伯努利过程中第 $k$ 次成功时刻 $Y_k$ 服从阶为 $k$ 的 Pascal 分布」之命题的证明后半段，随后进入 **Example 6.5**，该例自本页开始并延续到下一页。）</span>

（会使第 $k$ 次成功恰好发生在时刻 $t$ 的）这一结果当且仅当下述两个事件 $A$ 与 $B$ 同时发生时才会出现：

- (a) 事件 $A$：第 $t$ 次试验是成功的；
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 验证 Pascal PMF 的这段证明是又一款可复用模板，我叫它「末位剥离法」：把「第 $k$ 次成功恰在时刻 $t$」拆成两块——{第 $t$ 次试验成功}（概率 $p$）与 {前 $t-1$ 次中恰有 $k-1$ 次成功}（二项概率 $\binom{t-1}{k-1}p^{k-1}(1-p)^{t-k}$），两事件因「第 $t$ 次试验与之前独立」而相互独立，相乘即得。这与 CLRS 动态规划「先定最后一个操作，再递归计数」的思路完全同构（矩阵链乘法即如此）。它同时也是帕斯卡三角递归 $\binom{t-1}{k-1}=\binom{t-2}{k-2}+\binom{t-2}{k-1}$ 的概率解释：按第 $t-1$ 次试验成功与否分类。凡遇「首次/末次到达某状态」的问题，先剥离边界一步，往往立刻化简——这条经验在 CLRS 分析期望与这里一样好用。

- (b) 事件 $B$：在前 $t-1$ 次试验中恰好出现了 $k-1$ 次成功。

这两个事件的概率分别为

```math
P(A) = p,
```

与

```math
P(B) = \binom{t-1}{k-1}\, p^{k-1} (1 - p)^{t - k}.
```

此外，这两个事件相互独立（第 $t$ 次试验是否为成功，与先前 $t-1$ 次试验中所发生的情况无关）。因此

```math
p_{Y_k}(t) = P(Y_k = t) = P(A \cap B) = P(A)\,P(B) = \binom{t-1}{k-1}\, p^{k}\, (1 - p)^{t - k},
```

正如所声明的（as claimed）。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.5（Alicia 的犯规与上场时间）**</span>

在篮球比赛的每一分钟里，Alicia 以概率 $p$ 犯规一次，以概率 $1 - p$ 不犯规。假定不同分钟内的犯规次数相互独立。Alicia 一旦累计犯规满六次就会被罚下场，若未罚下场她将打满 $30$ 分钟。Alicia 上场时间的 PMF 是什么？

我们把犯规建模为参数为 $p$ 的伯努利过程（Bernoulli process）。Alicia 的上场时间 $Z$ 等于 $Y_6$，即第六次犯规之前的时刻，除非 $Y_6$ 大于 $30$，此时她的上场时间等于 $30$；也就是说，$Z = \min\{Y_6,\, 30\}$。随机变量 $Y_6$ 具有阶为 $6$ 的帕斯卡分布（Pascal PMF），由下式给出

```math
p_{Y_6}(t) = \binom{t - 1}{5}\, p^{6} (1 - p)^{t - 6}, \qquad t = 6, 7, \ldots
```

为确定 $Z$ 的 PMF $p_Z(z)$，我们先考虑 $z$ 介于 $6$ 与 $29$ 之间的情形。对这个范围内的 $z$，有

```math
p_Z(z) = p_{Y_6}(z) = \binom{z - 1}{5}\, p^{6} (1 - p)^{z - 6}, \qquad z = 6, 7, \ldots, 29 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式为原书「for $z$ in this range, we have」一句后本该出现的 PMF 算式，OCR 在此处仅残存「$z = 6, 7, \ldots, 29$」而吞掉了显式公式；按 $z$ 在该区间内 $Z = Y_6 = z$ 的意义（$Z = \min\{Y_6, 30\}$）重建为 $p_Z(z) = p_{Y_6}(z) = \binom{z-1}{5}p^{6}(1-p)^{z-6}$，数值未作臆造。</span>

$Z = 30$ 的概率随后由下式确定

```math
p_Z(30) = 1 - \sum_{z = 6}^{29} p_Z(z) .
```

> <span style="color:#7f8c8d;">本页于此处结束，下一页转入分裂与合并（splitting and merging）小节。</span>

<!-- ===== PDF p314 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）：分裂与合并（Splitting and Merging of Bernoulli Processes）**</span> <span style="color:#7f8c8d;">（页首无新节标题，源 OCR 首行仅为「6.1 with a Bernoulli process in which there is a probability $p$ of an arrival…」，本页是上一页关于伯努利过程分裂（splitting）讨论的延续。）</span>

> <span style="color:#7f8c8d;">⚠️ 本页 OCR 严重碎裂：源文件把正文拆成一两词一行的碎片，段落顺序也只能大致恢复。以下中文依据上下文补全语义，凡原文中可辨认的概率值（分裂：$pq$、$p(1-q)$；合并：$p+q-pq$）一律以源 OCR 中实际存在的数字为准，未作任意外推。无法辨认的片段用灰色注释标出。</span>

……以这样一个存在到达事件且到达概率为 $p$ 的伯努利过程为对象（with a Bernoulli process in which there is a probability $p$ of an arrival），我们如下考虑（we consider it as follows）：每当出现一次到达（arrival）时，我们以概率 $q$ 选择保留它（keep it），或以概率 $1-q$ 选择丢弃它（discard it）；见图 6.3（Fig. 6.3）。假定保留或丢弃这些决策彼此独立（independent）地做出。于是我们看到（we see）这是一个伯努利过程：在每一个时隙（time slot）中，出现一次被保留的到达的概率为 $pq$。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 分裂（splitting，也叫 thinning）是「按概率挑拣」：每个到达独立地以概率 $q$ 保留、以 $1-q$ 丢弃，原伯努利过程（参数 $p$）就被分成两个独立的伯努利过程（参数 $pq$ 与 $p(1-q)$）。为什么两个流相互独立？因为每个时隙的「保留/丢弃」决策独立且互斥，两类事件分属不同的时隙序列，互不交叉。这是连续版「泊松分裂」的离散先声：一个速率为 $\lambda$ 的泊松流按概率 $p$ 挑拣后仍是泊松流（速率 $\lambda p$），且与原流独立——这是排队论（如 M/M/1 队列按优先级分流的根基。直觉口诀是「到达之后抛硬币」：给定到达时刻后，分流退化为独立决策，这又与 p311 的间隙视角呼应。学完离散版的分裂，连续版只是把「时隙」换成「无穷小时间片」。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 决定「保留或丢弃」的那句话在源 OCR 中被拆成零词（仅余「choose to」「it (with probability …)」「1−q」等残片），上句按分裂过程的标准表述重排：保留概率 $q$、丢弃概率 $1−q$，二者形成「保留的到达」与「丢弃的到达」两类流。</span>

出于同样的原因（for the same reason），被丢弃的到达也构成一个伯努利过程，其到达概率（with a probability）为 $p(1-q)$。

<span style="color:#7f8c8d;">**[图] Fig. 6.3**</span> <span style="color:#00838f;">**图 6.3　伯努利过程的分裂（Splitting of a Bernoulli Process）**</span>

> <span style="color:#7f8c8d;">图 6.3 展示：一个到达概率为 $p$ 的伯努利过程，其每次到达独立地以概率 $q$ 被保留进「保留」流、以概率 $1-q$ 被丢弃，从而分裂成两个独立的伯努利过程（参数分别为 $pq$ 与 $p(1-q)$）。</span>

我们再考虑一个相反的过程（a reverse procedure）：把两个独立的伯努利过程合并。设其中一个以参数 $p$、（另一个）以参数 $q$ 分别运行（with parameters $p, q$，respectively）。我们如下合并之（combine them as follows）：在合并过程（merged process）中，每个时隙内至少有一个到达的概率为 $p + q - pq$ [即 $1-(1-p)(1-q)$：一减去 $1-p$ 与 $1-q$ 之积，而后者正是任一过程中都没有到达的概率 $(1-p)(1-q)$]。由于合并过程中各不相同的时隙彼此独立，该合并过程是伯努利过程，成功概率（success probability）为 $p + q - pq$。

<span style="color:#7f8c8d;">**[图] Fig. 6.4**</span> <span style="color:#00838f;">**图 6.4　两个伯努利过程的合并（Merging of Two Bernoulli Processes）**</span>

> <span style="color:#7f8c8d;">图 6.4 展示：参数分别为 $p$ 与 $q$ 的两个独立伯努利过程被合并成一个过程，其成功概率 $p+q-pq$ 恰为一减「两个源过程同此时隙均无到达」之概率。</span>

在每一个时刻（at each time），某些工作中心（work center）可能会面对一列到达（be faced with arrivals），从而看到一串成功事件（a stream of successes）……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页末这几行严重不连贯，仅能辨认出「…stream of successes」「以参数 $n$ 与 $p$（with parameters $n$ and $p$）」「均值（mean）为 $np$」「在本小节中（in this subsection），我们将…」等残句，语义指向「$n$ 个时隙内的到达数服从参数为 $n$、$p$ 的二项分布」这类新小节开头；因无法断定上下文，正文在「一串成功事件（a stream of successes）」之后截断，括号内数值（参数 $n$、$p$ 及均值 $np$）均以源 OCR 可辨认的字符为准。本页到此为止，内容延续到下一页。</span>

<!-- ===== PDF p315 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span> <span style="color:#7f8c8d;">（原书页码 306；本页续接上一页 §6.1 中关于伯努利过程合并与分裂（merging and splitting of Bernoulli processes）的讨论，并由此向泊松近似（Poisson approximation）过渡；下一页（原书 307）给出二项–泊松近似定理的推导与 Example 6.6 的演示。）</span>

> <span style="color:#7f8c8d;">[重要说明] 本页源页 OCR 严重损坏：页面正文几乎全部碎裂，仅词如「…of …Bernoulli processes…」「mean（均值）」「$E[Z] = \lambda$」、页码「6」等可辨识。按规范，凡无法辨认处一律留作占位并以灰注释标注，绝不臆造数值或补写例句编号。</span>

本页可辨识的开头残片为“……的伯努利过程（…of … Bernoulli processes）……”，其后整段内容因 OCR 碎裂而无法转写，上下文应在承接上一页所述伯努利过程合并与分裂的结果之后，进一步讨论其在极限下的泊松近似。

紧接着出现的可读残片是关于泊松随机变量（Poisson random variable）均值的陈述：若 $Z$ 服从参数为 $\lambda$ 的泊松分布，则其均值（mean）满足
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 泊松分布的签名性质是 $E[Z]=\mathrm{Var}(Z)=\lambda$。均值的推导靠「分子分母相消」：$k\cdot\lambda^k/k!=\lambda\cdot\lambda^{k-1}/(k-1)!$，把求和指标平移一格，露出 $e^{-\lambda}\cdot e^{\lambda}=1$；方差同理可证 $E[Z^2]=\lambda^2+\lambda$。为什么「均值=方差」是独特指纹？多数计数过程的方差与均值不同阶——二项分布 $\mathrm{Var}=np(1-p)$ 在 $p$ 大时远小于均值，而泊松的 $\lambda$ 同时控制中心与散布，是「单参数自足」模型。这个性质在统计检验里被反复使用：拟合优度检验常以「样本均值≈样本方差」作为数据像泊松分布的必要信号。它是 p316 二项→泊松极限定理的必然推论——极限把 $np$ 与 $np(1-p)$ 压成了同一个 $\lambda$。


```math
E[Z] = \lambda .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 此处原文应含泊松概率质量函数（Poisson PMF）$p_Z(k)=e^{-\lambda}\lambda^k/k!$ 及“$E[Z]=\lambda$”这一均值得出过程，但源页中相关行（含 `k`、`are`、`1` 等残片及随后若干行）被 OCR 完全吞碎，无法据残片重建整段证明。仅可确认“均值”与“$E[Z]=\lambda$”两处内容。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 本页自“$E[Z]=\lambda$”之后的其余正文、可能出现的公式推导与小节标题在源 OCR 中仅余孤立的行碎片（如 `1,` 等），无法转写，亦未发现新的 Example 编号或章节标题可资判断其确切边界。全部内容留待对照原书后补足。</span>

> <span style="color:#7f8c8d;">跨页续接：本页为 §6.1 正文的延续（页首无新章节标题），衔接下一 PDF 页（原书 307）的二项–泊松近似定理与 Example 6.6（Gary Kasparov 对战 100 名业余棋手），原书此处不分页、序号连续。</span>

<!-- ===== PDF p316 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）—— 二项分布的泊松近似（续）**</span>

> <span style="color:#7f8c8d;">承接上一页 §6.1 关于「泊松分布近似二项分布」的讨论：本页先给出二项概率在 $n\to+\infty$、$p\to\lambda/n$ 下收敛到泊松分布的一般结论，再验证泊松近似的有效性，并以 **Example 6.6**（Kasparov 车轮战）作为经验法则的演示。该例自本页开始，叙述延续到下一页。</span>

对于任意固定的非负整数 $k$，二项概率

```math
p_S(k) = \frac{n!}{(n-k)!\,k!}\, p^{k} (1-p)^{n-k}
```

在 $n\to+\infty$、$p\to\lambda/n$ 且保持 $\lambda$ 不变时，收敛到 $p_Z(k)$。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 泊松极限定理（law of rare events）是本节主定理，证明方法可提炼为模板「三因子拆分法」：把 $p_S(k)$ 写成三个因子之积，逐个求极限再相乘——阶乘比 $n(n-1)\cdots(n-k+1)/n^k\to 1$（$k$ 固定）、$(1-\lambda/n)^n\to e^{-\lambda}$（正是 p301 的恒等式）、$(1-\lambda/n)^{-k}\to 1$。遇到「多变量同时趋于极限」的式子，先拆成因子乘积，每个因子单独处理，是实分析与算法分析通用的招数。历史：Siméon Denis Poisson 1837 年在《关于刑事案件与民事案件判决概率的研究》中首次导出——他研究的是「陪审团作出正确判决的次数」这类稀有事件计数，故称「稀有事件定律」。跨课程：CLRS §5.4 balls-and-bins 分析中哈希桶的装载数按泊松近似，是它在算法分析里的经典用法。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式中二项式系数 $\frac{n!}{(n-k)!\,k!}$ 在 OCR 中被拆散成数行，此处按二项分布（binomial distribution）的标准式整理为规范公式，数值一律未改动。</span>

一般来说，只要 $\lambda = np$、$n$ 非常大且 $p$ 非常小，泊松概率质量函数（Poisson PMF）就是二项分布的良好近似。

为验证泊松近似的有效性，令 $p=\lambda/n$，并注意到

```math
\begin{aligned}
p_S(k)
&= \frac{n!}{(n-k)!\,k!}\left(\frac{\lambda}{n}\right)^{k}
   \left(1-\frac{\lambda}{n}\right)^{n-k}\\
&= \frac{n(n-1)(n-2)\cdots(n-k+1)}{n^{k}} \cdot \frac{\lambda^{k}}{k!}
   \left(1-\frac{\lambda}{n}\right)^{n}\left(1-\frac{\lambda}{n}\right)^{-k}.
\end{aligned}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上述推导在 OCR 中严重错行（分母 $n^k$、因子 $\lambda^k/k!$ 与 $\left(1-\lambda/n\right)^{-k}$ 等项被拆碎），此处按泊松近似的标准推导合并整理为单一规范公式，数值一律未改动。</span>

现在把 $k$ 固定下来，并令 $n\to+\infty$。比值 $(n-1)/n,\, (n-2)/n,\, \ldots,\, (n-k+1)/n$ 中每一个都收敛到 $1$。此外，

```math
\left(1-\frac{\lambda}{n}\right)^{-k} \longrightarrow 1 .
```

> <span style="color:#7f8c8d;">**脚注（footnote）:**</span> 这里用到众所周知的公式 $\lim_{x\to+\infty}\left(1-\tfrac{1}{x}\right)^{x} = e^{-1}$。取 $x = n/\lambda$，便有 $\lim_{n\to+\infty}\left(1-\tfrac{\lambda}{n}\right)^{n/\lambda} = e^{-1}$，并由此得 $\lim_{n\to+\infty}\left(1-\tfrac{\lambda}{n}\right)^{n} = e^{-\lambda}$。

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上述脚注中的 $x=n/\lambda$、$\left(1-\lambda/n\right)^{n/\lambda}$ 等项在 OCR 中被右栏截断，此处按 $\left(1-\tfrac{1}{x}\right)^{x}\to e^{-1}$ 的标准结论补全，数值一律未改动。</span>

由此我们断定：对每个固定的 $k$，当 $n\to+\infty$ 时，有

```math
p_S(k) \longrightarrow e^{-\lambda}\, \frac{\lambda^{k}}{k!} .
```

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.6（二项分布的泊松近似经验法则）**</span>

作为一种经验法则，当 $n \geq 100$、$p \leq 0.01$ 且 $\lambda = np$ 时，下面的泊松/二项近似在小数点后若干位内都成立：

```math
e^{-\lambda}\, \frac{\lambda^{k}}{k!}
\;\approx\;
\frac{n!}{(n-k)!\,k!}\, p^{k} (1-p)^{n-k},
\qquad k = 0, 1, \ldots, n .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式中各项在 OCR 中错位（系数、二项式 $\frac{n!}{(n-k)!\,k!}$、$(1-p)^{n-k}$ 等被拆散），此处按「$n$ 很大时二项概率近似为泊松概率」的标准式重建，数值一律未改动。为检验这条经验法则，考虑下面的例子。</span>

国际象棋世界冠军加里·卡斯帕罗夫（Gary Kasparov）在一场大型车轮战（simultaneous exhibition）中对阵 100 名业余棋手。根据过往经验估计，Kasparov …

> <span style="color:#7f8c8d;">本页在此处截止；Example 6.6 的叙述在分页处中断，延续到下一页继续。</span>

<!-- ===== PDF p317 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**伯努利过程（The Bernoulli Process）**</span> <span style="color:#7f8c8d;">（源 OCR 页眉为 Chap. 6，原书页码 308；页首无新节/新标题，本页续接上一页正文中关于「泊松近似（Poisson approximation）二项」的数值演示。）</span>

> <span style="color:#7f8c8d;">承接上一页：本页先讲完卡斯帕罗夫（Kasparov）对弈数量逼近二项的算例（含 $n=100$ 与 $n=5$ 两组对照表），随后在页末开始 **Example 6.7**（噪声信道上报文分组的传输），该例延续到下一页继续。</span>

在平均意义上，他在此类表演赛中赢得其 $99\%$ 的对局（用精确的概率语言来说，我们假定他对每一局都以概率 $0.99$ 获胜，且各局之间相互独立）。试问：他赢得 $100$ 局、$98$ 局、$95$ 局与 $90$ 局的概率分别是多少？

我们把卡斯帕罗夫**未**赢的局数 $X$ 建模为参数 $n = 100$、$p = 0.01$ 的二项随机变量（binomial random variable）。于是，他赢得 $100$ 局、$98$ 局、$95$ 局与 $90$ 局的概率分别为

```math
\begin{aligned}
p_X(0)   &= (1 - 0.01)^{100} = 0.366,\\
p_X(2)   &= \frac{100!}{98!\,2!}\; 0.01^{2}(1 - 0.01)^{98} = 0.185,\\
p_X(5)   &= \frac{100!}{95!\,5!}\; 0.01^{5}(1 - 0.01)^{95} = 0.00290,\\
p_X(10)  &= \frac{100!}{90!\,10!}\; 0.01^{10}(1 - 0.01)^{90} = 7.006 \times 10^{-8}.
\end{aligned}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上述二项概率公式中的组合系数（如 $100!/(98!\,2!)$）在 OCR 中被拆散（读作 `100! / 98. 2.` 等），此处按二项概率质量函数的标准式重建，数值一律未改动。</span>

现在让我们检验相应的泊松近似（Poisson approximation），此时取 $\lambda = 100 \cdot 0.01 = 1$。它们为
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 对照表验证了上面的机制：$n=100,p=0.01$ 时泊松近似极准（$0.366$ vs $0.368$ 等），$n=5,p=0.1$ 时明显偏差（$0.590$ vs $0.605$）。原因正是双重事件项：$\lambda=1$ 时二项与泊松之差的主项约为 $-(\lambda^2/2)(1-1/n)$ 量级——$n=5$ 时双重到达概率约 $10\cdot0.01=0.1$，不可忽略；$n=100$ 时约 $0.00495$，微小到可弃。注意 $p_Z(0)=0.368>p_X(0)=0.366$：泊松把更多质量推向 0，因为它去掉了「重复成功挤占名额」的效应。历史补充：Garry Kasparov（1963 年生）确以车轮战著称，1997 年输给 IBM 深蓝（Deep Blue）成为 AI 史里程碑；本题假设「每局 99% 胜率」使「未赢局数」成为标准的二项–泊松教材例。对照数字时建议亲手按 $e^{-\lambda}\lambda^k/k!$ 算一遍，体会阶乘与指数的叠加。


```math
\begin{aligned}
p_Z(0)  &= e^{-1}\,\frac{1^{0}}{0!} = 0.368,\\
p_Z(2)  &= e^{-1}\,\frac{1^{2}}{2!} = 0.184,\\
p_Z(5)  &= e^{-1}\,\frac{1^{5}}{5!} = 0.00306,\\
p_Z(10) &= e^{-1}\,\frac{1^{10}}{10!} = 1.001 \times 10^{-8}.
\end{aligned}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上述泊松概率公式中的 $1^{k}/k!$ 因子在 OCR 中显示为乱码（如 `e - l ` 与 `O.` 分母），此处按泊松概率质量函数 $e^{-1}\,1^{k}/k!$ 的标准式重建，数值保持不变。</span>

把二项概率质量函数（probability mass function）的值 $p_X(k)$ 与对应的泊松近似 $p_Z(k)$ 作比较，我们看到二者吻合得相当好。

现在假设卡斯帕罗夫仅同时与 $5$ 位对手对弈，但这些对手更强，他每局的胜率只有 $0.9$。下面是 $n = 5$、$p = 0.1$ 时的二项概率 $p_X(k)$，以及 $\lambda = np = 0.5$ 时对应的泊松近似 $p_Z(k)$：

| $k$ | 0 | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|---|
| $p_X(k)$ | 0.590 | 0.328 | 0.0729 | 0.0081 | 0.00045 | 0.00001 |
| $p_Z(k)$ | 0.605 | 0.303 | 0.0758 | 0.0126 | 0.0016 | 0.00016 |

我们看到，这一近似虽称不上差，但其精度远不如 $n = 100$、$p = 0.01$ 的情形。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.7（噪声信道上的报文分组传输）**</span>

一个由 $n$ 个符号组成的字符串所构成的分组（packet）在一噪声信道（noisy channel）上传输。每个符号以概率 $p = 0.0001$ 被……

> <span style="color:#7f8c8d;">本例 **Example 6.7** 于本页页末开始陈述，译文在此处随源 OCR 截断，例题的解法延续到下一页继续。</span>

<!-- ===== PDF p318 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）→ §6.2

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）—— 泊松近似的应用（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：页首续完 **Example 6.7**（含 $n$ 个符号的数据包经噪声信道传输）的尚未结束的解答（其题干已在上一页给出），随后正文进入新的一节 **§6.2 The Poisson Process**（泊松过程）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.7（续）—— 数据包经噪声信道传输（packet transmitted over a noisy channel）**</span>

> <span style="color:#7f8c8d;">续上一页：一个由 $n$ 个符号（symbol）构成的数据包经噪声信道（noisy channel）传输，每个符号以概率 $p = 0.0001$ 传错，且各符号的错误相互独立（independent）。问 $n$ 应取多小，才能让「至少一个符号出错」的传输错误概率小于 $0.001$？本页续其解答。</span>

把每个符号的传输看成一次独立的伯努利试验（independent Bernoulli trial）。于是，数据包中错误符号数 $S$ 大于 $0$ 的概率为

```math
1 - P(S=0) = 1 - (1-p)^{n} .
```

为使该概率小于 $0.001$，必须有 $1 - (1-0.0001)^{n} < 0.001$，即

```math
n < \frac{\ln 0.999}{\ln 0.9999} = 10.0045 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式中分子 $\ln 0.999$、分母 $\ln 0.9999$ 及结果 $10.0045$ 在 OCR 中被拆散在数行，此处按条件 $1-(1-p)^{n}<0.001$ 及对数的算法重建为规范式，数值一律未改动。</span>

我们也可以对 $P(S=0)$ 使用泊松近似（Poisson approximation），即当 $\lambda = np = 0.0001\, n$ 时取值为 $e^{-\lambda}$，从而得到条件 $1 - e^{-0.0001\, n} < 0.001$，由此推出
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这里"泊松近似"不是魔术，它的数学根是微积分里最著名的极限 $e=\lim_{n\to\infty}(1+1/n)^n$。改写一下：把每个符号的出错的概率 $p$ 看成"一长串试验中平均出错 $\lambda$ 次"的微量，即令 $p=\lambda/n$，则 $(1-p)^n=(1-\lambda/n)^n\to e^{-\lambda}$。这与复利公式、CSAPP 第3章浮点逼近、以及 CLRS §C.4 里"二项分布当 $p$ 很小时逼近泊松"是同一个极限的不同面孔。可把它命名为"e极限夹逼法"：只要目标是"大量独立小概率事件"，就写成 $(1-x/n)^n$ 型再取极限。本题两条路线给出几乎相同的答案（10.0045 vs 10.005），说明当 $n$ 只有 10 时泊松近似的相对误差已在千分之一量级——这正好提醒你：近似只有在有误差界时才有意义，这也是后面"主项 + o(·) 尾巴"写法的伏笔。


```math
n < -\,\frac{\ln 0.999}{0.0001} = 10.005 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式中分母 $0.0001$、负号及结果 $10.005$ 在 OCR 中被拆散，此处按条件 $1-e^{-\lambda}<0.001$ 的标准算法重建，数值一律未改动。</span>

由于 $n$ 必须是整数（n must be an integer），两种方法都归结到同一结论：$n$ 至多只能取 $10$。

---

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）**</span>

泊松过程（Poisson process）是伯努利过程（Bernoulli process）在连续时间（continuous time）下对应的版本，适用于那种没有自然而然的方法把时间划分成离散区间的情形。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 注意作者引入泊松过程的方式：不是直接扔定义，而是先讲"为何需要"——把时间离散成分钟区间会丢掉"同一分钟内发生多起事故"的信息。破解思路是让区间长度趋于 0，这正是你在 TBB/Rudin 里反复见到的"细分—极限"模式：先用网格逼近，再取网格直径趋于零。可命名为"细分—极限法"：伯努利过程是固定粒度的近似，泊松过程是粒度趋于 0 的极限，两者之间只隔一步取极限。这与 6.042J 里把递归结构翻译成闭式、CSAPP 用离散采样近似连续信号是同源动作。值得品味的一点：连续模型往往不是"更复杂"而是"更简单"——极限消除了"区间该怎么切"的随意性。这与你 Strang 线性代数里"先用有限维逼近、再取极限得到算子"的做法互为印证，是分析学的第一性原理在概率中的投影。


为看出伯努利过程为何需要一个连续时间版本，不妨考虑一个城市内交通事故（traffic accidents）的可能模型。我们先把时间离散成以一分钟为单位的若干区间，并在每一分钟内只要有至少一次交通事故就记下一个「成功（success）」。假定交通强度（traffic intensity）随时间恒定，那么每个区间内发生事故的概率都应相同。再附加一条合理得相当可信的假设——不同时间段相互独立，则这些「成功」的序列就构成一个伯努利过程。

注意，在现实生活里，同一分钟区间内确实可能发生两起或更多起事故，但伯努利过程模型并不记录事故的确切次数；尤其它并不能让我们算出给定时间段内事故次数的期望（expected number）。

绕过这一困难的一种办法，是把时间区间的长度取得非常小，使得两起或更多起事故的概率小到可以忽略不计。但该取多小呢？一秒？一毫秒？与其做这种随意的选择，不如考虑一种极限情形，让时间区间的长度趋于 $0$，也就是采用连续时间模型。

我们考察一个在连续时间中演化（evolves in continuous time）的到达过程（arrival process），意思是任意实数 $t$ 都可能成为一个到达时刻。我们定义

```math
P(k,\, \tau) = P\big(\text{在长度为 } \tau \text{ 的区间内恰好发生 } k \text{ 次到达}\big) .
```

<!-- ===== PDF p319 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）——泊松过程的定义（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页为 §6.2 泊松过程正文的延续，页首接上一页已引入的到达过程（arrival process）与到达间隔（interarrival time）等铺垫，正文从“……并假定这一概率对所有长度相同的区间都相同”一句续起，随即给出**泊松过程的定义（Definition of the Poisson Process）**这一定义框。</span>

……并假定这一概率对所有长度相同的区间来说都相同。我们还引入一个正的参数 $\lambda$，称为该过程的到达率或强度（arrival rate or intensity），其原因很快就将变得清楚。

<span style="color:#00838f;">**[定义] Definition of the Poisson Process（泊松过程的定义）**</span>

一个到达过程若具有如下性质，就称为速率为 $\lambda$ 的泊松过程（Poisson process with rate $\lambda$）：

- (a) （时间齐次性 Time-homogeneity）任意区间内发生 $k$ 次到达的概率 $P(k, \tau)$ 对所有长度相同的区间都相同。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 泊松过程的定义把伯努利过程的"离散三条"逐句翻译成"连续三条"：(a) 时间齐次性对应"每次试验成功概率 $p$ 相同"；(b) 独立性对应"不同试验相互独立"；(c) 小区间概率对应"每个时段内至多成功一次"。这套构建手法可命名为"极限翻译法"：先在一个已理解的离散模型里建立全部直觉，再把每条性质改写成极限语句，就得到连续版本。逐条对照很有价值：第三条里 $P(2,\tau)=o(\tau)$ 说的正是"$\delta$ 小时内两次事故的概率随 $\delta$ 缩小而消失得比 $\delta$ 还快"，它与"至多一次成功"是同一个直觉。这也是 6.042J"等价刻画"思维的体现：同一个对象（伯努利过程的极限）可有多副面孔。深一层看，(a)(b)(c) 把"强度恒定、无记忆、不扎堆"三件事打包，将来在排队论里它们会以"平稳、独立增量、阶跃到达"的姿态反复出现。

- (b) （独立性 Independence）特定区间内到达的次数，与这一区间之外到达的历史（history）无关。
- (c) （小区间概率 Small interval probabilities）概率 $P(k, \tau)$ 满足

```math
\begin{aligned}
P(0, \tau) &= 1 - \lambda\tau + o(\tau),\\
P(1, \tau) &= \lambda\tau + o(\tau),\\
P(k, \tau) &= o_k(\tau), \qquad \text{对 } k = 2, 3, \ldots \text{成立}.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这里的 $o(\tau)$ 与算法分析里的记号是近亲但语义不同，值得分清。CLRS/CSAPP 里的 $O(g(n))$ 说"增长不超过 $g$ 的常数倍"，而概率里的 $o(\tau)$ 说"当 $\tau\to0$ 时与 $\tau$ 相比趋于 0"，即 $o(\tau)/\tau\to0$。直观上 $o(\tau)$ 是"在极限中消失到可忽略的尾巴"，正是误差项的精确写法。为什么定义里非要用 $o$ 而不用"$\approx$"？因为 (c) 的目标是给出能推进极限论证的精确语句：$P(1,\tau)=\lambda\tau+o(\tau)$ 既允许误差，又保证误差除以 $\tau$ 后趋零，于是后面"切成 $n$ 段取极限"时误差不会积累。这与 CSAPP 把浮点误差写成可忽略尾项、6.042J 用渐进记号刻画复杂度的精神一致。记住这条主线：连续概率里几乎所有推导都靠"主项 + $o(\cdot)$ 尾巴"来书写，看见 $o(\tau)$ 就要条件反射地想到"下一步要取极限"。

\end{aligned}
```

这里，$o(\tau)$ 与 $o_k(\tau)$ 是满足下列条件的 $\tau$ 的函数：

```math
\lim_{\tau \to 0}\frac{o(\tau)}{\tau} = 0, \qquad
\lim_{\tau \to 0}\frac{o_k(\tau)}{\tau} = 0.
```

第一条性质说明到达在任何时刻都“同样可能”。在任意长度为 $\tau$ 的时间区间内发生的到达在统计上是相同的，即它们遵循相同的概率律（probability law）。这与伯努利过程（Bernoulli process）中成功概率 $p$ 对所有试验都相同的假设相对应。

为了理解第二条性质，考虑一个长度为 $t' - t$ 的特定区间 $[t, t']$。在该区间内发生 $k$ 次到达的无条件概率（unconditional probability）为 $P(k, t' - t)$。假设现在我们得到了这一区间之外到达的完整或部分信息。性质 (b) 表明这些信息无关紧要：在 $[t, t']$ 内发生 $k$ 次到达的条件概率仍等于无条件概率 $P(k, t' - t)$。这一性质与伯努利过程中试验的独立性类似。

第三条性质至关重要。$o(\tau)$ 与 $o_k(\tau)$ 这几项，意在指出当区间长度 $\tau$ 非常小时它们与 $\tau$ 相比可以忽略不计。可以将它们看作是 $P(k, \tau)$ 的泰勒级数展开（Taylor series expansion）中的 $O(\tau^2)$ 项。因此，对很小的 $\tau$ 而言，发生单次到达的概率大致为 $\lambda\tau$，再加上一个可忽略的项。类似地，对很小的 $\tau$ 而言，不发生到达的概率大致为 $1 - \lambda\tau$。最后，随着 $\tau$ 变小，发生两次或更多次到达的概率与 $P(1, \tau)$ 相比可以忽略不计。

<!-- ===== PDF p320 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）—— 对泊松过程的伯努利近似（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：我们已给出泊松过程的定义及其三条性质 (a)–(c)。由于性质 (c)（小间隔概率）表明在很小时段内几乎不可能发生多次到达，本页据此把泊松过程（Poisson process）看成伯努利过程（Bernoulli process）的极限，从而导出区间到达数 $P(k, T)$ 的显式泊松公式。</span>

由于在长度很小的一段区间内，至多只会发生一次到达，因此其中要么恰有一次到达（概率约为 $\lambda\delta$），要么一次也没有（概率约为 $1 - \lambda\delta$）。由此，所研究的到达过程可以用伯努利过程来近似，并且随着 $\delta$ 越取越小，这种近似越来越精确。

<span style="color:#c0392b;">**Figure 6.5：在长度为 $T$ 的区间上对泊松过程的伯努利近似（Bernoulli approximation）。**</span>

区间 $[0, T]$ 内发生 $k$ 次到达的概率 $P(k, T)$，等于在 $n = T/\delta$ 个相互独立的小时段（period）中恰好成功 $k$ 次的（二项分布）概率，其中每个时段地成功概率为 $p = \lambda\delta$。我们在保持区间长度 $T$ 固定的同时，令时段个数 $n$ 趋于无穷（即令 $\delta \to 0$），而乘积 $n\,\delta$ 保持恒定并等于 $T$。我们于是注意到 $n\,p = \lambda T$，并且沿用上一节所述结果——二项分布的 PMF 收敛于参数为 $\lambda T$ 的泊松分布 PMF。我们于是得到

```math
P(k, T) = e^{-\lambda T}\,\frac{(\lambda T)^{k}}{k!}, \qquad k = 0, 1, \ldots
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本节的心脏公式，值得把推导拆成可复用模板，命名为"小区间分解法"。步骤固定为三步：①把 $[0,T]$ 均匀切成 $n=T/\delta$ 段；②每段内至多一次到达（性质 c），所以整段时间的到达数近似为 $\mathrm{Binomial}(n,\lambda\delta)$；③保持 $T$ 不变令 $\delta\to0$（即 $n\to\infty$、$np=\lambda T$ 固定），二项 PMF 逐点收敛到泊松 PMF。第三步的"保持 $np$ 固定"是关键：它要求每段成功概率与段长同步缩小，这正是"大量独立小概率事件"的数学配方。这一步也再次用上 e 极限：$(1-\lambda\delta)^n\to e^{-\lambda T}$，与 p318 的"e极限夹逼法"遥相呼应。顺带一提，泊松分布得名于法国数学家 Siméon-Denis Poisson（1837 年在"裁判判决概率"研究中提出），当时处理的正是"罕见事件"的极限。这个"切段、逐段独立、取极限"的三板斧，之后推导 Erlang、分析随机算法运行时都会反复用到。

```

这与泊松过程定义中的性质 (c) 相吻合。注意，对 $e^{-\lambda T}$ 作泰勒展开（Taylor expansion）可得

```math
P(0, T) = e^{-\lambda T} = 1 - \lambda T + O(T^{2}),
```

以及（对 $P(1, \cdot)$ 展开）

```math
\lambda T\, e^{-\lambda T} = \lambda T - \lambda^{2} T^{2} + O(T^{3}) = \lambda T + O(T^{2}),
```

换言之，当区间长度非常小时，恰有一次到达的概率约为 $\lambda T$，而零次到达的概率约为 $1 - \lambda T$，这正与性质 (c) 一致。

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本页原文 OCR 严重碎裂（前半页"要么恰有一次到达、要么零次"一段、Figure 6.5 的图注分行、以及末尾泰勒展开的写法均难以辨认）；上文按 §6.2 泊松过程的伯努利近似这一标准推导流程重建，未臆造数值，仅据上下文补全变量符号（$\delta$ 表示小时段长、$T$ 表示固定区间长）。末段"与性质 (c) 一致"的核对式按 $P(0,\cdot)$ 与 $P(1,\cdot)$ 在小区间上的展开呈现。</span>

<!-- ===== PDF p321 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）—— 泊松过程相关的随机变量（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：我们用伯努利近似导出了 $[0,T]$ 内恰有 $k$ 次到达的概率 $P(k,T)$。本页沿用泊松 PMF（probability mass function）的均值与方差公式，先给出区间到达数 $N_T$ 的均值与方差，再推导首次到达时间 $T$ 的概率规律（指数分布），最后以表格总结泊松过程相关的随机变量及其性质，并开启 Example 6.8。</span>

利用前面导出的泊松 PMF 的均值和方差公式，我们得到

```math
E[N_T] = \lambda T, \qquad \operatorname{var}(N_T) = \lambda T,
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 均值等于方差（$E=\mathrm{var}=\lambda T$）是泊松分布的签名特征，一眼可认。从第一性原理看，它来自二项分布的极限：$\mathrm{Binomial}(n,p)$ 的方差 $np(1-p)$，当 $p$ 很小时 $(1-p)\approx1$，于是方差≈均值。更深刻的是"可加性"：若 $N_1,N_2$ 独立且都服从泊松，$N_1+N_2$ 仍服从泊松（p323 将证明），可加性要求均值与方差都随参数线性增长，二者必然同形——用 Strang 的语言说，期望是"线性泛函"，而独立和的方差也呈线性，泊松恰好让这两条线重合。这条性质在智能科学里极好用：判断到达是否像泊松，粗略检验就是看样本均值与样本方差是否接近；网络流量、传感事件计数都靠它快速筛模型。注意这与正态不同——正态的均值与方差是两个独立自由度，而泊松只有一个参数 $\lambda$ 同时锁定两者，所以"泊松是单参数的二项极限"值得反复品味。

```

其中 $N_T$ 表示长度为 $T$ 的时间区间内的到达次数。这两个公式毫不令人意外，因为我们面对的正是二项分布 PMF 的极限，该二项分布写为 $n = T/\delta$、$p = \lambda\delta$，其均值为 $np = \lambda T$，方差为 $np(1-p) \simeq np = \lambda T$。

现在我们来推导首次到达时间 $T$ 的概率规律，假定过程从时刻零开始。注意，当且仅当在区间 $[0,t]$ 内没有到达时才有 $T > t$。于是有

```math
F_T(t) = P(T \le t) = 1 - P(T > t) = 1 - P(0, t) = 1 - e^{-\lambda t}, \qquad t > 0 .
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 推导"首次到达时间 $T$ 的分布"只用了漂亮的绕行，可命名为"生存函数法"。思路：对"直到某事件首次发生的时间"这类变量，别直接算 CDF，先算它的补——生存函数 $P(T>t)$，它往往等价于一个简单得多的事件"到时刻 $t$ 为止什么都没发生"。本页 $P(T>t)=P(0,t)=e^{-\lambda t}$，于是 CDF $=1-e^{-\lambda t}$，再对 $t$ 求导得 PDF $=\lambda e^{-\lambda t}$。这套"先算存活概率、再取补、再求导"的三步法，与 CLRS §C.4 计算"不发生坏事件的概率"、CSAPP 里"检查失败概率"是同一思路的连续版本。注意一个伏笔：$P(T>t)=e^{-\lambda t}$ 这条式子本身就是无记忆性的种子（p323 将收割），所以指数分布不是"碰巧算出来的"，而是"无记忆性的必然形状"。以后再见到"首次/首个"类随机变量，第一反应就应该是生存函数。

```

然后对 $T$ 的 CDF $F_T(t)$ 求导，得到 PDF 公式

```math
f_T(t) = \lambda e^{-\lambda t}, \qquad t > 0,
```

这表明首次到达前的时间服从参数为 $\lambda$ 的指数分布（exponentially distributed）。我们把这一讨论归结为下表；另见图 6.6。

<span style="color:#00838f;">**[定义] 泊松过程相关的随机变量及其性质（Random Variables Associated with the Poisson Process and their Properties）**</span>

- **参数为 $\lambda T$ 的泊松分布（The Poisson with parameter $\lambda T$）。** 这是速率为 $\lambda$ 的泊松过程在长度为 $T$ 的区间内的到达次数 $N_T$。其 PMF、均值与方差为

```math
p_{N_T}(k) = P(k, T) = e^{-\lambda T}\,\frac{(\lambda T)^{k}}{k!}, \qquad k = 0, 1, \ldots , \qquad E[N_T] = \lambda T, \qquad \operatorname{var}(N_T) = \lambda T .
```

- **参数为 $\lambda$ 的指数分布（The exponential with parameter $\lambda$）。** 这是到首次到达的时间 $T$。其 PDF、均值与方差为

```math
f_T(t) = \lambda e^{-\lambda t}, \quad t \ge 0, \qquad E[T] = \frac{1}{\lambda}, \qquad \operatorname{var}(T) = \frac{1}{\lambda^{2}} .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上述两栏总结框中的公式在 OCR 中被拆散：泊松 PMF 的分子分母（$e^{-\lambda T}$ 与 $(\lambda T)^{k}/k!$）、指数 PDF 的 $f_T(t)=\lambda e^{-\lambda t}$ 及均值 $\frac{1}{\lambda}$、方差 $\frac{1}{\lambda^{2}}$ 均碎行；上文按泊松分布与指数分布的标准形式重建数值，未作臆造。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.8（按泊松过程收到电子邮件）**</span>

你按泊松过程收到邮件，速率为例 $\lambda = 0.2$ 条/小时，你每小时检查一次邮箱。那么发现 $0$ 封和 $1$ 封新邮件的概率各是多少？

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 该例题干末尾处 OCR 读作"the probability of finding 0 and _new messages?'"，其中 `1` 处缺失（源页此处难以识别），据题意（检查邮箱、每小时一次，λ=0.2 条/小时）应问的是发现 $0$ 封与 $1$ 封新邮件的概率；本例从本页开始，其解法延续到下一页。</span>

<!-- ===== PDF p322 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**§6.2（续）**</span> <span style="color:#7f8c8d;">**〔图 6.6（Fig. 6.6）图注：把伯努利过程看作泊松过程的离散时间版本（View of the Bernoulli Process as the Discrete-Time Version of the Poisson Process）〕**</span>

> <span style="color:#7f8c8d;">本节自本页起始。其主旨是把离散时间的伯努利过程（Bernoulli process）通过「间隔细分到无穷小」的极限与连续时间的泊松过程（Poisson process）联系起来。</span>

我们把时间离散化（discretize）为小间隔（small intervals）$\delta$，并把每一个间隔与一次伯努利试验（Bernoulli trial）联系起来，其成功概率（success probability）为 $p = \lambda \delta$。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一页建立的是"离散—连续对照表"，建议像背元素周期表一样背下来：成功概率 $p$ ↔ 到达率 $\lambda$；二项分布 ↔ 泊松分布；几何分布（首次成功前的等待次数）↔ 指数分布（首次到达前的等待时间）；Pascal 分布（第 $k$ 次成功前的等待次数）↔ Erlang 分布（第 $k$ 次到达的时刻）。每一对都满足同一句口诀："离散是固定的 $\delta$，连续是 $\delta\to0$"。这张表的价值在于"迁移"：凡是在 §6.1 伯努利过程里证明过的性质，猜出连续版本再验证极限即可，不用重推。这与 6.042J 里"等价关系让我在两个表示之间自由切换"是同一个方法论。往后学排队论、马尔可夫链时会反复用这张表做翻译。建议现在就亲手把四对关系各写一遍（含 PMF/PDF、均值、方差），直到能默写。


> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 紧接「success probability $p = \lambda\delta$」之后，原文有一段说明性文字，描述当间隔 $\delta \to 0$ 时离散化的伯努利过程在极限下收敛为泊松过程的推理；但源 OCR 将该段完全碎裂（仅余零散乃至乱码的行首词、以及若干孤立词「is consistent / preceding」），无法还原为可读句子。此处仅保留可辨认的开头句，其余不作臆造，需回查原书 p.313。</span>

下面的表格总结了由泊松过程得自伯努利过程的若干基本推论（basic consequences），与前面〔对伯努利过程〕讨论的相应结论一一对应。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 本页自「The table summarizes some of the basic consequences」之后至页末（含提及 customers 的叙述）的内容在 OCR 中严重碎裂，仅留下互不衔接的残词，无法还原成完整句子，此处不作臆造，需回查原书 p.313。</span>

<!-- ===== PDF p323 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.2 泊松过程（Poisson process）（续）

> <span style="color:#7f8c8d;">承接上一页：页首即为某 **Example** 的后续（该例编号位于上一页，例号以源 OCR 为准反查，非本页新编号），演示泊松计数在两个不重叠时刻区间上的可加性；随后转入「独立性与无记忆性（Independence and Memorylessness）」小节，列出泊松过程的两条独立性性质，并给出第一条性质的验证与记忆无性公式的推导。（书中页码 314）</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.9（续）—— 泊松计数的可加性（additivity of the Poisson count）**</span>

……（上一页设定）在 $9\!:\!00$ 到 $9\!:\!10$ 之间到达的顾客数为 $M$，另令 $N$ 为在 $9\!:\!30$ 到 $9\!:\!35$ 之间到达的顾客数。那么 $M + N$ 的分布是什么？

我们注意到，$M$ 是参数为 $\mu = 10 \cdot 10 = 100$ 的泊松（Poisson）随机变量，$N$ 是参数为 $\nu = 10 \cdot 5 = 50$ 的泊松随机变量。此外，$M$ 与 $N$ 相互独立。正如 4.4 节用变换（transform）所说明的，$M + N$ 是参数为 $\mu + \nu = 150$ 的泊松随机变量（另见第 4 章 Problem 11）。现在我们改用一种更直接、更符合直觉的方式来推导同一结论。

令 $\tilde{M}$ 为在 $9\!:\!10$ 到 $9\!:\!15$ 之间到达的顾客数。注意 $\tilde{M}$ 与 $N$ 具有相同的分布（参数为 $50$ 的泊松）。此外，$\tilde{M}$ 也与 $M$ 相互独立。于是 $M + N$ 的分布与 $M + \tilde{M}$ 的分布相同。而 $M + \tilde{M}$ 是长度为 $15$ 的一个区间内的到达次数，因此服从参数为 $10 \cdot 15 = 150$ 的泊松分布。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个证明里藏着概率论最优雅的技巧之一——"替换法"（coupling，耦合）：与其硬算 $M+N$ 的卷积，不如造一个同分布但结构更干净的随机变量 $\tilde M$，让它与 $N$ 同分布、且与 $M$ 独立，于是 $M+N$ 与 $M+\tilde M$ 同分布，而后者只是一个"15 分钟区间的到达数"，答案唾手可得。核心逻辑链是"同分布 + 独立性 ⇒ 和的分布不变"，它只用到了各加数的边缘分布与独立性结构。这与 6.006/CLRS 平摊分析里"换一个等价但更可分析的量来算复杂度"是同一种思维手术。也请注意它展示的元规则：两个独立泊松之和仍是泊松——泊松家族的"加法封闭性"（可加性）在此第一次正面出场，它是泊松大量存在的根本原因之一。建议把"替换法"记进证明工具箱，它会在随机过程、马尔可夫链与算法分析中反复出现。


> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原文中的顾客计数变量 $M$、$\tilde M$ 多处被 OCR 误识为 `A!`、`Iv!`、`Al`、`iii` 等，参数字母 $\mu$、$\nu$ 亦被误识为 `J.l`、`v`；本段已按上下文还原为 $M$、$\tilde M$、$\mu$、$\nu$，数值一律未改动。</span>

这个例子说明了在一般情况下成立的要点：在一组总长度为 $T$ 的时刻集合内出现 $k$ 次到达的概率总是由 $P(k, T)$ 给出，即使该集合并非某个区间。（在本例中，我们处理的是总长度为 $15$ 的集合 $[9\!:\!00,\,9\!:\!10] \cup [9\!:\!30,\,9\!:\!35]$。）

---

<span style="color:#c0392b;">**独立性与无记忆性（Independence and Memorylessness）**</span>

泊松过程具有若干与伯努利过程（Bernoulli process）平行的性质，包括不重叠时刻集的独立性（independence of nonoverlapping time sets），以及到达间隔（interarrival time）分布的无记忆性（memorylessness）。既然泊松过程可以看作伯努利过程的一个极限情形（limiting case），那么它继承后者的这些定性（qualitative）性质，就几乎不足为奇。

<span style="color:#c0392b;">**泊松过程的独立性性质（Independence Properties of the Poisson Process）**</span>

- 对任意给定的时间 $t > 0$，时刻 $t$ 之后的过程历史（history）也是一个泊松过程，并且与直到时刻 $t$ 为止的过程历史相互独立。
- 设 $t$ 为给定时间，$T$ 为时刻 $t$ 之后首次到达的时刻。那么 $T - t$ 服从参数为 $\lambda$ 的指数分布（exponential distribution），并且与直到时刻 $t$ 为止的过程历史相互独立。

上表中第一条性质之所以成立，是因为我们看到：自时刻 $t$ 开始的那部分过程满足泊松过程定义所要求的一切性质。未来相对于过去的独立性，是泊松过程定义中独立性假定（independence assumption）的直接推论。最后，$T - t$ 具有相同的指数分布这一事实，可如下验证：

```math
P(T - t > s)
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 无记忆性是本节最深刻的性质，值得从第一性原理看穿。等式 $P(T>s+t\mid T>s)=P(T>t)$ 翻译成生存函数就是 $S(s+t)=S(s)S(t)$，这是一个函数方程：满足它（且单调）的连续解只有一个，即 $S(t)=e^{-\lambda t}$。换言之，不是"指数分布恰好无记忆"，而是"无记忆性强迫分布长成指数"——这是必然性而非巧合。离散世界的对应物你已在 §6.1 见过：几何分布满足同样的乘法方程，所以几何分布是"离散的指数"。本页最后 $P(T-t>s)=e^{-\lambda s}$ 正是把这个方程复述了一遍。更深一层，泊松过程的"未来与过去独立、未来重新开始"正是马尔可夫性质（Markov property）的雏形——6.042J 里马尔可夫链的转移独立性在此以连续时间的形式提前登场，为你将来学随机过程埋好伏笔。请记住"无记忆 ⟺ 乘法方程 ⟺ 指数/几何"这条锁链。

= P\big(\text{在 }[t,\,t+s]\ \text{内发生 0 次到达}\big)
= P(0, s)
= e^{-\lambda s} .
```

这正是无记忆性，与伯努利过程的相应性质类似。下面几个例子都用到了这一性质。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 末段中指数参数 $\lambda$ 被误识为 ``，记忆无性不等式被误读为 `T - > s`、`e ->' s`，`limiting case` 被误读为 `limiting ca..<;e`；此处已按标准记号还原，数值与公式结构未改动。</span>

<!-- ===== PDF p324 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）—— §6.2（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页续接 §6.2 泊松过程（Poisson process）正文中关于无记忆性（memoryless）的应用举例，先是 Example 6.10 与 Example 6.11 两则演示无记忆性的例子，随后引入本页新的小节「到达间隔（Interarrival Times）」。（页眉标示正文页码为 315。）</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.10（网球场上的等待时间）**</span>

你和你的同伴来到一座网球场，必须等到占据球场的球员打完才能上场。假设（多少有些不现实）他们的打球时间服从指数 PDF（exponential PDF）。那么，你的等待时间（等价地说，他们剩下的打球时间）的 PDF 也服从同一个指数 PDF，无论他们从何时开始打球。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.11（银行柜台的最后一个离开者）**</span>

你走进银行，发现三位柜员都在忙着为其他顾客服务，且没有其他顾客在排队。假设你以及每一位正在被服务的顾客的服务时间都是相互独立的、同分布的指数随机变量。你成为最后一个离开者的概率是多少？

答案是 $1/3$。要理解这一点，请聚焦于你开始接受某位柜员服务的那一刻。于是，另外两位正在被服务的顾客各自的剩余时间，与你自己的剩余时间，具有相同的 PDF。因此，你与另外两位顾客成为最后一个离开者的概率相等，都是 $1/3$。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个 $1/3$ 漂亮地展示了无记忆性的威力与对称性论证的省力。关键一步：从"你开始被服务"那一刻起，另外两位正在被服务的顾客，其剩余服务时间与你的剩余服务时间同分布——因为无记忆性让"已经服务了多久"的信息全部作废，正在服务的人与刚刚开始的人没有区别。三个人、三个独立同分布的"剩余寿命"同时倒计时，由 p329 将学的"竞争指数"结论，谁的寿命最短谁就先结束服务，三人地位完全对称，故你成为最后一个离开者的概率是 $1/3$。这里没有算任何积分，只用了两条直觉：同分布 + 独立 + 对称。这种"对称性论证法"与 6.042J 里用双射/对称计数的精神一脉相承，也是竞争指数、次序统计量章节里反复出现的杠杆。注意"最后一个离开"对应的是最大值而非最小值，但对称性让你绕过了计算最大值分布，直接得出概率。


<span style="color:#c0392b;">**到达间隔（Interarrival Times）**</span>

与一个从时刻 $0$ 开始的泊松过程相关联的一个重要随机变量是第 $k$ 次到达的时刻（time of the $k$th arrival），我们把它记为 $Y_k$。一个与之相关的随机变量是第 $k$ 个到达间隔（$k$th interarrival time），记为 $T_k$。它由下式定义，其中 $k = 2, 3, \ldots$，

```math
T_k = Y_k - Y_{k-1},
```

它表示第 $(k-1)$ 次与第 $k$ 次到达之间的时间量。注意

```math
Y_k = T_1 + \cdots + T_k .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本页定义 $T_k$ 的公式 $T_k = Y_k - Y_{k-1}$ 与随后的「注意 $Y_k = T_1 + \cdots + T_k$」两句在 OCR 中被吞（原文仅在行间残留「It is defined by」与孤立行「k = 2, 3, . . .」、以及「Note that」），此处按 §6.2 标准定义重建，数值与记号一律未改动；如需最严格原文请回查原书。</span>

我们此前已经看到，直到首次到达的时间 $T_1$ 是一个参数为 $\lambda$ 的指数随机变量。从首次到达的时刻 $T_1$ 起，未来是一个全新开始的泊松过程（fresh-starting Poisson process）。这样，直到下一次到达的时间便具有相同的指数 PDF。进一步地，该过程的过去（直到时刻 $T_1$ 为止）与未来（时刻 $T_1$ 之后）相互独立。由于 $T_2$ 完全由未来所发生之事决定，可见 $T_2$ 与 $T_1$ 相互独立。如此继续，我们得出结论：随机变量 $T_1, T_2, T_3, \ldots$ 相互独立，且全部服从同一个指数分布。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> "到达间隔独立且同为指数分布"给出了泊松过程的第二副面孔，教科书称之为"另一种描述"，本质是从"性质定义"切换到"构造定义"：先采样一串独立指数间隔 $T_1,T_2,\dots$，再在 $T_1,T_1+T_2,\dots$ 处放置到达。两种描述互相推出、完全等价，这是 6.042J"等价关系"的又一次现身：同一对象有两种刻画，解题时选顺手的那种。构造定义的实用价值在"生成"：写模拟程序时，生成泊松到达根本不用管小区间概率，只要循环累加指数采样即可——这是排队论仿真、网络负载生成、随机算法测试的标准做法，你现有的 CLRS 随机数知识完全够用。它还顺带解释了"fresh-start"现象：过程在任意时刻重新开始，因为在指数间隔的视角下，未来只由"当前还没到的下一次"决定。建议把"性质定义 ↔ 构造定义"这对视图同时装进脑子，它们是同一枚硬币的两面。


这一重要观测引出了对泊松过程的一种与之等价但又不同的描述方式。

> <span style="color:#7f8c8d;">**脚注（footnote）**</span>

> 这一陈述比先前讨论过的事实——即从任意给定的确定性时刻 $t$ 出发过程都全新开始——来得更强，但相当直观。它可以通过模仿 Example 6.3 中的论证，对随机变量 $T_1$ 的所有可能取值进行条件化而正式地予以证明。

<!-- ===== PDF p325 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> <span style="color:#7f8c8d;">（页眉仅标 `Chap. 6`，PDF 页码 316；本页属 §6.2 泊松过程正文内部，续接上一页的「另一种描述」小节。）</span>

<span style="color:#c0392b;">**§6.2　泊松过程的另一种描述（Alternative Description of the Poisson Process） —— （续）**</span>

> <span style="color:#7f8c8d;">承接上一页：上页先以「小时间区间内至多一次到达的近似」的方式给出泊松过程的一种等价刻画思路，本页把该「另一种描述」的步骤以编号列表写明，随后转入子节「第 $k$ 次到达时刻（The $k$th Arrival Time）」，导出 $Y_k$ 的均值、方差与 PDF，并列出「第 $k$ 次到达时刻的性质」。</span>

该「另一种描述」以下述两步给出：

1. 从一列相互独立的指数随机变量（independent exponential random variables）$T_1, T_2, \ldots$ 出发，它们具有公共参数 $\lambda$，并让这些随机变量代表到达间隔（interarrival times）。
2. 在时刻 $T_1, \; T_1 + T_2, \; T_1 + T_2 + T_3, \;$ 等处各记录一次到达（record an arrival）。

<span style="color:#c0392b;">**第 $k$ 次到达时刻（The $k$th Arrival Time）**</span>

第 $k$ 次到达的时刻 $Y_k$ 等于 $k$ 个相互独立且同分布的指数随机变量之和 $Y_k = T_1 + T_2 + \cdots + T_k$。这使我们得以导出 $Y_k$ 的均值、方差与 PDF 的公式，它们列在下表中。

<span style="color:#c0392b;">**第 $k$ 次到达时刻的性质（Properties of the $k$th Arrival Time）**</span>

- 第 $k$ 次到达时刻等于前 $k$ 个到达间隔之和，而这些到达间隔是具有公共参数 $\lambda$ 的相互独立的指数随机变量。
- $Y_k$ 的均值与方差为
  ```math
  E[Y_k] = \frac{k}{\lambda},
  \qquad
  \operatorname{var}(Y_k) = \operatorname{var}(T_1) + \cdots + \operatorname{var}(T_k) = \frac{k}{\lambda^{2}} .
  ```
- $Y_k$ 的 PDF 为
  ```math
  f_{Y_k}(y) = \frac{\lambda^{k} y^{k-1} e^{-\lambda y}}{(k-1)!} ,
  \qquad y \ge 0,
  ```
  它被称为 $k$ 阶爱尔朗 PDF（Erlang PDF of order $k$）。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 爱尔朗分布以丹麦工程师 Agner Krarup Erlang（1878–1929）命名。他 1908 年起供职于哥本哈根电话公司，1909 年发表论文研究电话交换需要多少线路才能让呼叫不阻塞，由此开创排队论与话务工程两个学科；Erlang 公式与"Erlang 单位"至今仍是电信业的标准计量（通信教材里"话务量以 Erlang 计"即源于此）。从第一性原理看，Erlang($k$) 就是"等到第 $k$ 次到达"的时间 = $k$ 个独立指数之和，其 PDF $f(y)=\lambda^k y^{k-1}e^{-\lambda y}/(k-1)!$ 里藏着两个因子：$e^{-\lambda y}$ 是"最后一小段没到达"的生存概率，$(\lambda y)^{k-1}/(k-1)!$ 是"此前恰好 $k-1$ 次到达"的泊松概率，两个视角相乘得到密度。注意它与泊松分布互为对偶（p326 的 $\{Y_k\le y\}\iff\{N_y\ge k\}$）：泊松回答"给定时间有几件事"，Erlang 回答"第 $k$ 件事发生在何时"。排队论（M/M/1 等）将大量使用它，而排队论正是智能科学里网络、调度、性能分析的基础。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 原 OCR 把「第 $k$ 次到达时刻的性质」列表中的均值式 $E[Y_k] = k/\lambda$ 吞掉（跳读作「The mean and variance of $Y_k$ are given by」后直接进到 $\operatorname{var}(Y_k) = \cdots = k/\lambda^{2}$）；因 $Y_k$ 是 $k$ 个 i.i.d. 的 $\operatorname{Exp}(\lambda)$ 之和，均值 $E[Y_k]=k/\lambda$ 与方差 $k/\lambda^2$ 均为标准结论，此处均值按此重建，其余数值一律未改动。</span>

为求 $Y_k$ 的 PDF $f_{Y_k}$，我们作如下论证：对很小的 $\delta$，乘积 $\delta \cdot f_{Y_k}(y)$ 近似等于「第 $k$ 次到达发生在时刻 $y$ 与 $y + \delta$ 之间」的概率……

> <span style="color:#7f8c8d;">[续接下一页] 本页到此句即截止（原书在「between times ...」处换页），对 $f_{Y_k}$ 的「小 $\delta$ 论证」将在下一页接着完成。原书中此论证的走向是近似概率 $P(y \le Y_k \le y + \delta) \approx F_{Y_{k-1}}(y)\,\lambda\,\delta + o(\delta)$，进而借助分部积分导出爱尔朗 PDF，此处仅如实保留原文断句，不作私自补全。</span>

<!-- ===== PDF p326 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.2（续）

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）**</span> <span style="color:#7f8c8d;">（Sec. 6.2，原书页码 317；本页续接上一页 §6.2 正文中第 $k$ 个到达时刻 $Y_k$ 的 Erlang PDF（Erlang probability density function）推导，并在页中给出 Example 6.12，页底为一条替代推导的脚注。）</span>

> <span style="color:#7f8c8d;">承接上一页：强度为 $\lambda$ 的泊松过程，$Y_k$ 表示第 $k$ 个到达发生的时刻。上一页已把 $Y_k$ 视为 $T_1 + \cdots + T_k$（其中 $T_i$ 为相继到达间隔）建立起其 PDF 的推导框架；本页继续以「时间区间内到达次数」的概率论论证完成 Erlang PDF 的推导。</span>

…在 $y$ 与 $y + \delta$ 之间。当 $\delta$ 很小时，时间区间 $[y, y + \delta]$ 内发生多于一次到达的概率可忽略不计。因此，第 $k$ 个到达落在 $y$ 与 $y + \delta$ 之间，当且仅当下面两个事件 $A$ 与 $B$ 同时发生：

- (a) 事件 $A$：在时间区间 $[y, y + \delta]$ 内有一次到达；
- (b) 事件 $B$：在时刻 $y$ 之前恰好发生了 $k - 1$ 次到达。

这两个事件的概率分别为

```math
P(A) \approx \lambda \delta,
\qquad
P(B) = P(k-1, y) = \frac{\lambda^{k-1} y^{k-1} e^{-\lambda y}}{(k-1)!}.
```

由于 $A$ 与 $B$ 相互独立，我们有

```math
\delta\, f_{Y_k}(y) \approx P(y \le Y_k \le y + \delta)
= P(A \cap B) = P(A)\, P(B)
= \lambda \delta \cdot \frac{\lambda^{k-1} y^{k-1} e^{-\lambda y}}{(k-1)!},
```

由此得到

```math
f_{Y_k}(y) = \frac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!}, \qquad y \ge 0.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本页演示了一个可复用的"求密度"模板，命名为"δ·f 法"：要算 PDF $f_Y(y)$，先写 $\delta\,f_Y(y)\approx P(y\le Y\le y+\delta)$，即"密度 × 小区间长 ≈ 落入小区间的概率"，再把右侧用已知事件拆开。这里的关键是把右侧拆成 $A\cap B$ 两个独立事件：$A$ = 小区间内一次到达（概率 $\approx\lambda\delta$），$B$ = $y$ 之前恰好 $k-1$ 次到达（概率 $P(k-1,y)$ 已知），相乘后除以 $\delta$ 立得 $f$。整套动作的本质是"把对 $Y$ 的分布问题翻译成对计数 $N$ 的概率问题"，因为计数分布（泊松）是已知的。这与 TBB 里"微元法"（用 $f\cdot dx$ 逼近小段概率再取极限）完全同构，也是黎曼和思想在概率密度上的镜像。务必掌握这门翻译手艺：连续随机变量的密度，常常不是直接积分 CDF，而是"先猜 $\delta\cdot f$ 的近似、再除以 $\delta$ 取极限"。

```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上面末两行在 OCR 中把系数、指数与公式主体拆散到数行（如 `f_{Y_k}(y)` 主体、`\lambda \delta` 系数以及分母 $(k-1)!$ 各处零散），数值与结构均按泊松过程「区间内到达次数」的标准论证重建，所得 $f_{Y_k}(y) = \dfrac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!}$ 与下方脚注求导结果一致。</span>

> <span style="color:#7f8c8d;">脚注 $t$（给出一条不依赖近似论证（approximation arguments）的替代推导）：对给定的 $y \ge 0$，事件 $\{Y_k \le y\}$ 与事件「时间区间 $[0, y]$ 内的到达次数至少为 $k$」是同一个事件。因此，$Y_k$ 的 CDF 为
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 脚注里的这条恒等式 $\{Y_k\le y\}\iff\{N_y\ge k\}$ 是本节最凝练的洞察，可命名为"计数—时间对偶"：第 $k$ 次到达发生在 $y$ 之前，当且仅当到 $y$ 为止至少已发生 $k$ 次到达。它把"到达时间"与"到达个数"两个家族互相翻译，于是 $Y_k$ 的 CDF 直接等于 $P(N_y\ge k)$，即泊松分布的右尾和，再对 $y$ 求导便得 Erlang PDF——这是不依赖任何近似论证的精确路线。这对偶在算法里到处可见：6.006 里"找第一个满足条件的索引"与"统计小于某值的元素个数"是同一个问题的两面（rank/select），二分搜索就在这两个视角间来回横跳；CSAPP 的缓存替换统计也常用这种"计数 ↔ 时刻"的互换。请把 $\{Y_k\le y\}=\{N_y\ge k\}$ 当作速查卡记住，它让"等待时间分布"与"计数分布"从此互通，后面随机过程课程里这条对偶还会以更强形式出现。

>
> ```math
> F_{Y_k}(y) = P(Y_k \le y) = \sum_{n = k}^{\infty} P(n, y) = 1 - \sum_{n = 0}^{k-1} P(n, y) = 1 - \sum_{n = 0}^{k-1} \frac{(\lambda y)^n}{n!}\, e^{-\lambda y}.
> ```
>
> $Y_k$ 的 PDF 可对这一表达式求导得到，直接计算即得 Erlang PDF 公式 $f_{Y_k}(y) = \dfrac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!}$。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.12（拨打国税局热线）**</span>

你拨打国税局（IRS，Internal Revenue Service）热线，被告知你是排队中的第 56 位，不包括正在被服务的那个人的位次。来电者按照参数为 $\lambda = 2$ 次每分的泊松过程相继离去。平均而言，你要等多长时间服务才开始？你不得不等待超过 30 分钟的概率又是多少？

根据无记忆性（memorylessness property），正在被服务的那个人剩余的剩余服务时间服从参数为 $2$ 的指数分布。排在你前面的 55 个人的服务时间也服从同样的参数，

> <span style="color:#7f8c8d;">本页 Example 6.12 自 §6.2 正文处开始，其解答延续到下一页；脚注 $t$ 中末行 Erlang PDF 公式的右端（书页另起一行排版）在本页省略，按上方正文已给出的相同公式并入。</span>

<!-- ===== PDF p327 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）—— §6.2（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页续接第 6 章 §6.2 泊松过程（Poisson process）正文。页首续完上一页已开讲的 **Example 6.12**（IRS 求助热线等待时间），随后进入本节新的子节「泊松过程的分裂与合并（Splitting and Merging of Poisson Processes）」，并以 **Example 6.13（泊松过程的分裂，Splitting of Poisson Processes）** 作演示；该例自本页末尾起笔，延续到下一页。（页眉标示正文页码为 318。）</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.12（续）—— IRS 求助热线的等待时间**</span>

> <span style="color:#7f8c8d;">续上一页：你拨打 IRS 求助热线，得知你是队中第 56 位（不含当前正被服务者）。来电离去服从速率 $\lambda = 2$ 次/分钟的泊松过程。需要求出到开始接受服务为止的平均等待时间，以及等待超过 30 分钟的概率。由无记忆性（memoryless），当前正被服务者的剩余服务时间服从参数为 2 的指数分布；你前面 55 人的服务时间也服从同一参数的指数分布。</span>

于是所有这些随机变量相互独立。因此，以分钟计的你等待时间 $Y$，是一个阶数为 $56$、参数 $\lambda = 2$ 的埃尔朗（Erlang）随机变量，其期望为

```math
E[Y] = \frac{56}{\lambda} = \frac{56}{2} = 28 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 「阶数为 $56$」的「$56$」与下文 $E[Y] = \dfrac{56}{\lambda} = \dfrac{56}{2} = 28$ 在源 OCR 中仅残留「…is Erlang of order」「E[Y]」「56, 56/λ」「28」等碎片。此处依据上一页（Example 6.12 已给出 $\lambda=2$ 与「队中第 56 位」）以及本页被积式中 $\lambda^{56}/55!$ 的埃尔朗结构重建，数值与记号一律未改动，未作臆造。</span>

你必须等待超过 30 分钟的概率由下式给出：

```math
P(Y \ge 30) = \int_{30}^{\infty} \frac{\lambda^{56}}{55!} \, y^{55}\, e^{-\lambda y} \, dy .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 该式的下界「30」与被积式 $\dfrac{\lambda^{56}}{55!}\, y^{55} e^{-\lambda y}$ 在源 OCR 中按孤立行「1 / 00 Y55 / 30 / A 56 55 − A y / dy」碎裂，「1」即积分号、「00」即 $\infty$，此处按埃尔朗阶数 56 的标准 PDF 重建；若需最严格原文请回查原书页 318。</span>

计算这一概率颇为繁琐（quite tedious）。另一方面，由于 $Y$ 是大量独立同分布随机变量之和，我们可以借助中心极限定理（central limit theorem）与正态分布表（normal tables）来作近似。

<span style="color:#c0392b;">**泊松过程的分裂与合并（Splitting and Merging of Poisson Processes）**</span>

与伯努利过程的情况类似，我们可以从一个速率为 $\lambda$ 的泊松过程出发并对其作分裂（split），具体方式如下：每一起到达（arrival）以概率 $p$ 被保留下来，以概率 $1-p$ 被丢弃，而且与其他到达所发生的情况相互独立。在伯努利的情形下我们已经看到，分裂的结果仍是一个伯努利过程。在当前语境下，分裂的结果是一个速率为 $\lambda p$ 的泊松过程。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> "分裂"为什么保持泊松性质？照例走定义验证（Example 6.13 就是干这个）：在小区间 $\delta$ 内，一次"被保留下来的到达"要求"有一次原始到达（$\approx\lambda\delta$）且它恰好被保留（概率 $p$）"，两者独立相乘得 $\lambda\delta\cdot p$；两次及以上被保留到达的概率是 $o(\delta)$。于是被保留下来的过程满足泊松定义的 (a)(b)(c)，速率为 $\lambda p$。背后的第一性原理：泊松的"稀疏性"保证了"分裂后仍然稀疏"，而稀疏性正是性质 (c)。更反直觉的结论在下一页：分裂出的两个流彼此独立，且到达的"类别"（本地/中转）序列与到达时刻相互独立——这是泊松特有的"标记独立性"，伯努利分裂里也有对应物。跨课程上，分裂正是"随机个数的和"的直观原型（p330 的表）：$N\sim\mathrm{Pois}(\lambda)$ 个事件、每件以 $p$ 独立标记，则标记数 $\sim\mathrm{Pois}(\lambda p)$。网络分组、服务队列乃至 Bloom 过滤器的假阳性分析里都用得上。


换一种方式，我们也可以从两个相互独立的泊松过程出发，其速率分别为 $\lambda_1$ 与 $\lambda_2$，并把它们合并（merge）在一起：只要任一过程中有一起到达，就记一次到达。结果是，合并后的过程也是泊松过程，速率为 $\lambda_1 + \lambda_2$。进一步地，合并后过程中的任意特定到达，来自第一个过程的概率为 $\lambda_1/(\lambda_1+\lambda_2)$，来自第二个过程的概率为 $\lambda_2/(\lambda_1+\lambda_2)$，并且与所有其他到达及其各自来源相互独立。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 合并与分裂是对偶操作，验证同样走小区间：$P(0)\approx(1-\lambda_1\delta)(1-\lambda_2\delta)\approx1-(\lambda_1+\lambda_2)\delta$，$P(1)\approx\lambda_1\delta(1-\lambda_2\delta)+(1-\lambda_1\delta)\lambda_2\delta\approx(\lambda_1+\lambda_2)\delta$——注意"恰有一次到达"有两种来源，所以是两项相加，这正是速率相加的微观来源：速率是每单位时间的事件率，率相加源自小区间概率相加。由此得到关键的第二问：给定一次到达，它来自流 1 的概率是 $\lambda_1/(\lambda_1+\lambda_2)$，即"率之比"——这与分裂里"以概率 $p$ 保留"互为逆运算：合并按比率分来源，分裂按概率分去向。而且 $L_1,L_2,\dots$（每次到达的来源标签）相互独立，再次体现泊松的"标记独立性"。跨课程上，这是排队论"多源合流"的模型基础（一个节点收到来自多个客户的请求流），也是网络/分布式系统里"总到达率 = 各源率之和"的严格依据，你在 CSAPP 网络章节与 6.006 分布式内容里会反复遇见它。请把"率之比"这个比值记牢，它是 p330 表很多比例结论的共同来源。


我们将在若干例子的语境中讨论这些性质，与此同时给出确证它们成立的论证。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.13　泊松过程的分裂（Splitting of Poisson Processes）**</span>

到达数据网络某个节点（node）的分组（packet），要么是旨在发往该节点的本地分组（local packet，以概率 $p$ 发生），要么是必须被中继到另一节点的中转分组（transit packet，以概率 $1-p$ 发生）。分组按速率为 $\lambda$ 的泊松过程到达，而且每一个分组是本地分组还是中转分组，与其他分组及到达时刻相互独立。正如上文所述，本地分组到达的过程是速率为 $\lambda p$ 的泊松过程。让我们看看为什么会如此。

我们验证本地分组到达的过程满足泊松过程的各定义性质（defining properties）。由于 $\lambda$ 与 $p$ 均为常数（不随时间变化），第一个性质（时间齐性，time-homogeneity）显然成立。此外，在互不相交的时间区间内所发生的事件之间不存在依赖，从而验证了第二个性质。最后，若我们聚焦于一个长度为 $\delta$ 的小区间，一次本地到达的概率近似等于存在一次分组到达、并且该到达恰为本地分组的概率，即 $\lambda \delta \cdot p$。除此之外，两次或更多次本地到达的概率与 $\delta$ 相比可以忽略，这验证了第三个性质。

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 末段「$\lambda \delta \cdot p$」在源 OCR 中记为「A6·p」（$\delta$ 与 $p$ 的位置被吞并），句首「We verify」残作「\Ve verify」，均按泊松过程定义性质的上下文重建；Example 6.13 自本页起笔并延续到下一页。</span>

<!-- ===== PDF p328 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.2 泊松过程（Poisson process）（续）

> <span style="color:#7f8c8d;">承接上一页（书中页码 319，页眉 `Sec. 6.2`，标题 `The Poisson Process`）：上一页以 **Example 6.13（泊松过程的拆分，Splitting）** 结束。本页先收尾该例（按对称论证得出局部与过境分组到达各成泊松过程、且二者相互独立的结论），随后完整给出 **Example 6.14（泊松过程的合并，Merging）**，最后开篇引入 **Example 6.15（竞争指数，Competing Exponentials）**（该例延续到下一页）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.13（续）—— 泊松过程的拆分（Splitting of Poisson Processes）**</span>

我们得出的结论是：局部分组（local packet）到达构成一个泊松过程，特别是，在长度为 $T$ 的一个区间内发生的此类到达次数，具有以 $\lambda T$ 为参数的泊松分布（Poisson PMF）。由对称论证（symmetrical argument），过境分组（transit packet）到达的过程也是泊松过程，其速率为 $\lambda(1-p)$。在此背景下略显令人意外的一个事实是：把原泊松过程拆分得到的这两个泊松过程是相互独立的（independent），参见章末习题（end-of-chapter problems）。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.14　泊松过程的合并（Merging of Poisson Processes）**</span>

寄信（letter）的人按速率为 $\lambda_1$ 的泊松过程到达邮局，寄包裹（package）的人则按相互独立的、速率为 $\lambda_2$ 的泊松过程到达。正如前面所说，同时包含两类到达的合并过程（merged process）是速率为 $\lambda_1+\lambda_2$ 的泊松过程。下面我们来弄明白其缘由。

首先应当清楚，合并过程满足时间齐次性（time-homogeneity）性质。此外，既然两个到达过程中的不同区间彼此独立，合并过程对同样的性质也成立。现在我们聚焦于一个长度为 $\delta$ 的小区间。忽略相较于 $\delta$ 可忽略不计的项，我们有

```math
P(\text{合并过程中的 0 次到达}) \approx (1 - \lambda_1\delta)(1 - \lambda_2\delta) \approx 1 - (\lambda_1 + \lambda_2)\delta,
```

```math
P(\text{合并过程中的 1 次到达}) \approx \lambda_1\delta(1 - \lambda_2\delta) + (1 - \lambda_1\delta)\lambda_2\delta \approx (\lambda_1 + \lambda_2)\delta,
```

至此第三条性质已得验证。

给定刚刚记录到一次到达，它来自寄信的人的概率是多少？我们再次聚焦于当前时刻附近的一个长度为 $\delta$ 的小区间，所求概率为

```math
P(1\text{ 次来自寄信人的到达} \mid 1\text{ 次到达}).
```

利用条件概率的定义，并忽略多于一次到达这一可忽略不计的概率，该式即为

```math
\frac{P(1\text{ 次来自寄信人的到达})}{P(1\text{ 次到达})}
= \frac{\lambda_1\delta}{(\lambda_1 + \lambda_2)\delta}
= \frac{\lambda_1}{\lambda_1 + \lambda_2}.
```

把这一计算推广开来，令 $L_k$ 表示第 $k$ 次到达是一次寄信人到达这一事件，则我们有

```math
P(L_k) = \frac{\lambda_1}{\lambda_1 + \lambda_2},\qquad \text{对每个 } k.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 原文在 "we have"（于是我们有）之后、在 "Furthermore, since distinct arrivals..."（再者，由于不同的到达发生在不同时刻）之前，应有一行给出 $P(L_k)$ 的算式，但 OCR 中该行空缺（仅存空白），此处按 $P(L_k) = \lambda_1/(\lambda_1+\lambda_2)$（对每个 $k$）依据上式的推广自然补全；数值系由上文的 $\lambda_1\delta/((\lambda_1+\lambda_2)\delta)$ 直接得出，未作改动。</span>

再者，由于不同的到达（distinct arrivals）发生在不同的时刻，并且对于泊松过程而言，不同时刻的事件是相互独立的，因此可以推知随机变量 $L_1, L_2, \ldots$ 相互独立。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.15　竞争指数（Competing Exponentials）**</span>

两只灯泡（light bulb）具有相互独立且均服从指数分布（exponentially distributed）的寿命 $T_a$ 与 $T_b$，参数分别为 $\lambda_a$ 与 $\lambda_b$。随机变量 $Z = \min\{T_a, T_b\}$、即第一只灯泡烧毁的时刻，其分布是什么？

> <span style="color:#7f8c8d;">本例题（Example 6.15）的解答自下页开始（即下一页继续讲解），本页仅给出题意设定。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页参数符号 $\lambda_1, \lambda_2$ 与 $\lambda_a, \lambda_b$ 被 OCR 误识为 `>'1`、`>'2`、`>'a`、`>'b`，单个 $\lambda$ 被误识为 `>'`，区间长度 $\delta$ 被误识为 `8`，条件概率竖线 `|` 与数字 `1` 混用为 ``1``，`PDF` 被误识为 `P1,fF`、寿命 $T_b$ 被误识为 `n`；以上均已按上下文还原为标准记号，数值与公式结构未改动。</span>

<!-- ===== PDF p329 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 合并泊松过程与竞争指数，本章正文（续）

> <span style="color:#7f8c8d;">承接上一页：本页继续两个独立泊松过程合并（merging of Poisson processes）与竞争指数（competing exponentials）的讨论。页首先完成「两个独立指数随机变量的最小值仍是指数分布」的 CDF 推导并给出直观说明，再将其推广到 $n$ 个过程的合并；随后在本页中部引入 **Example 6.16（More on Competing Exponentials，竞争指数）。** 页眉仅给出章节总标题（The Bernoulli and Poisson Processes / Chap. 6），未标明小节号。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.15（续）—— 竞争指数（Competing Exponentials）**</span>

对一切 $z \ge 0$，记 $Z = \min\{T_a, T_b\}$，我们都有其 CDF 为

```math
F_Z(z) = P\!\big(\min\{T_a, T_b\} \le z\big)
= 1 - P\!\big(\min\{T_a, T_b\} > z\big)
= 1 - P(T_a > z,\; T_b > z)
= 1 - P(T_a > z)\,P(T_b > z).
```

（最后一步用到了 $T_a$ 与 $T_b$ 的独立性。）这正是参数为 $\lambda_a + \lambda_b$ 的指数 CDF（exponential CDF）。于是，参数分别为 $\lambda_a$ 与 $\lambda_b$ 的两个相互独立的指数随机变量的最小值，是参数为 $\lambda_a + \lambda_b$ 的指数随机变量。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> "两个独立指数的最小值仍是指数、且参数相加"是本节最反直觉也最有用的结论。先看证明骨架（生存函数法又一次出场）：$P(\min>z)=P(T_a>z)P(T_b>z)=e^{-\lambda_a z}e^{-\lambda_b z}=e^{-(\lambda_a+\lambda_b)z}$，一眼看出指数。再看直觉：把 $T_a,T_b$ 看作两个独立泊松过程各自的首次到达时刻，合并成一个泊松过程后首次到达就是 $\min$，而合并速率是 $\lambda_a+\lambda_b$，于是结论"免费"得到——这是 p328 合并结论的直接推论，也说明"竞争指数"与"合并"是同一枚硬币。更深一层的洞察是危险率（hazard rate）视角：指数分布的瞬时"熄灭率"恒为 $\lambda$（无记忆性的微分形式），两个独立"闹钟"并行时总熄灭率是各自率之和，谁先响由竞争决定。这个"率相加"的结构将贯穿次序统计量与可靠性分析；系统里"多个部件谁先坏"、算法里"多个随机过程谁先触发"都用它。


为对这一事实给出更直观的解释，我们把 $T_a$ 与 $T_b$ 视为两个速率分别为 $\lambda_a$ 与 $\lambda_b$ 的相互独立泊松过程中首次到达的时刻。若把这两个过程合并（merge），首次到达时刻将是 $\min\{T_a, T_b\}$。但我们已知合并后的过程是速率为 $\lambda_a + \lambda_b$ 的泊松过程，于是可推出首次到达时刻 $\min\{T_a, T_b\}$ 是参数为 $\lambda_a + \lambda_b$ 的指数分布。

上述讨论可以推广到两个以上过程的情形。因此，把 $n$ 个到达速率分别为 $\lambda_1, \ldots, \lambda_n$ 的独立泊松过程的到达合并后所得的总到达过程，是到达速率等于和 $\lambda_1 + \cdots + \lambda_n$ 的泊松过程。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.16　更深入的竞争指数（More on Competing Exponentials）。**</span>

三只灯泡的寿命是相互独立的指数随机变量，具有公共参数 $\lambda$。问直到最后一盏灯泡烧坏为止的时间的期望值（expected value）是多少？

我们把每盏灯泡烧坏的时刻视为相互独立泊松过程中的首次到达时刻（first arrival times）。起初共有三只灯泡，合并后的过程速率为 $3\lambda$。因此首次烧坏时间 $T_1$ 服从参数为 $3\lambda$ 的指数分布，均值为 $1/(3\lambda)$。一盏灯泡烧坏之后，由指数分布的无记忆性（memorylessness），另外两只灯泡的剩余寿命又成为参数为 $\lambda$ 的相互独立的指数随机变量。于是我们有两个并行运行的泊松过程，这两个过程中任一过程的首次到达所剩余的等待时间 $T_2$ 现在服从参数为 $2\lambda$ 的指数分布，均值为 $1/(2\lambda)$。最后，当第二盏灯泡烧坏后，就只剩下一盏。再次利用无记忆性，直至最后一盏灯泡烧坏的剩余时间 $T_3$ 服从参数为 $\lambda$ 的指数分布，均值为 $1/\lambda$。因此，总时间的期望值为

```math
E[T_1 + T_2 + T_3] = \frac{1}{3\lambda} + \frac{1}{2\lambda} + \frac{1}{\lambda}.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 6.16 是"顺序统计量"思想的入门课，手法叫"链条式分解"：不直接求"最后一盏灯烧坏的时间"（三个指数最大值的分布），而是把总等待时间拆成三段 $T_1+T_2+T_3$ 逐段处理——先等第一个烧坏（$\min$，率 $3\lambda$），烧掉一盏后靠无记忆性，剩下两盏的剩余寿命"重新开始"（率 $2\lambda$），再等第二个，最后只剩一盏（率 $\lambda$）。每一步都只需等一个"当前最小值"，分布已知，期望立得 $1/3\lambda+1/2\lambda+1/\lambda$。两个伏笔值得留意：其一，这里用了期望的线性性 $E[T_1+T_2+T_3]=E[T_1]+E[T_2]+E[T_3]$，它本不需要三变量独立（CLRS §C.3 的线性期望），但本例还额外证明了它们独立，从而方差也能相加；其二，"烧掉一盏后剩余寿命重新指数化"正是无记忆性把复杂联合分布"切成"独立分量的关键。这条"每次剥掉一个最小元"的思路，与 6.006 锦标赛淘汰、以及排序里"逐轮去掉最值"同构。

```

注意，随机变量 $T_1, T_2, T_3$ 因无记忆性而相互独立。这也让我们得以计算总时间的方差（variance）：

```math
\operatorname{var}(T_1 + T_2 + T_3)
= \operatorname{var}(T_1) + \operatorname{var}(T_2) + \operatorname{var}(T_3)
= \frac{1}{9\lambda^2} + \frac{1}{4\lambda^2} + \frac{1}{\lambda^2}.
```

<!-- ===== PDF p330 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes，以及随机变量之和）**</span> — §6.2（续）

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）**</span> <span style="color:#7f8c8d;">（本页续接上一页 §6.2 末尾关于利用伯努利/泊松过程的分裂与合并来阐释随机个数之和性质的讨论；页首无新小节标题，为延续页。）</span>

> <span style="color:#7f8c8d;">承接上一页：对伯努利过程与泊松过程进行分裂（splitting）与合并（merging）所获得的认知，可用来为若干涉及随机个数随机变量之和的有趣性质给出简单解释。</span>

由伯努利过程与泊松过程的分裂与合并所获得的这些认知（the insights obtained from splitting and merging of Bernoulli and Poisson processes），可用来为若干涉及随机个数的独立随机变量之和的有趣性质提供简单的解释。那些替代性的证明思路——例如通过操作概率质量函数／概率密度函数（PMFs/PDFs）、求解派生分布问题（derived distribution problems），或借助生成函数（transforms）——往往缺乏直观性。我们把这几条性质汇集在下表中。

<span style="color:#c0392b;">**随机个数随机变量之和的性质（Properties of Sums of a Random Number of Random Variables）**</span>

设 $N, X_1, X_2, \ldots$ 为相互独立的随机变量，其中 $N$ 取非负整数值（nonnegative integer values）。对 $N$ 为正的情形令 $Y = X_1 + \cdots + X_N$，并对 $N = 0$ 令 $Y = 0$。

- 若 $X_i$ 服从参数为 $p$ 的伯努利分布（Bernoulli with parameter $p$），且 $N$ 服从参数为 $m$ 和 $q$ 的二项分布（binomial），则 $Y$ 服从参数为 $m$ 和 $pq$ 的二项分布。
- 若 $X_i$ 服从参数为 $p$ 的伯努利分布，且 $N$ 服从参数为 $\lambda$ 的泊松分布（Poisson），则 $Y$ 服从参数为 $\lambda p$ 的泊松分布。
- 若 $X_i$ 服从参数为 $p$ 的几何分布（geometric），且 $N$ 服从参数为 $q$ 的几何分布，则 $Y$ 服从参数为 $pq$ 的几何分布。
- 若 $X_i$ 服从参数为 $\lambda$ 的指数分布（exponential），且 $N$ 服从参数为 $q$ 的几何分布，则 $Y$ 服从参数为 $\lambda q$ 的指数分布。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这张表把前面所有内容拧成一股绳：$Y=X_1+\cdots+X_N$（$N$ 随机）的分布居然如此规整。用已建立的直觉逐条看：伯努利 × 泊松 → 泊松($\lambda p$) 就是"分裂"（$N$ 是总到达数，每件以 $p$ 标记，标记数服从 $\mathrm{Pois}(\lambda p)$）；二项 × 伯努利同理。几何 × 几何 → 几何、指数 × 几何 → 指数($\lambda q$) 则需要更本质的解释——几何分布是"离散的指数"（无记忆），而"无记忆"在做这种随机复合时保值：离散无记忆复合离散无记忆仍离散无记忆，连续无记忆复合离散无记忆仍连续无记忆。这条"无记忆在复合下保值"的规律，是表里四个结论的公共根。跨课程上，随机个数之和在算法分析中到处都是：随机化算法的递归树规模、哈希表的桶内冲突数、以及 CLRS 习题里"由随机步数构成的运行时间"都是 $Y$ 的形式。建议把这张表当作"分裂—合并"的代数版本背下来。


前两条性质在 Problem 22 中给出证明，第三条性质在 Problem 6 中给出，最后一条性质在 Problem 23 中给出。最后三条性质还曾借助生成函数在第 4 章中证明过（见 Section 4.4 与第 4 章章末的最后一个习题）。还有一条相关的性质在 Problem 24 中给出：若以 $N_t$ 记参数为 $\lambda$ 的泊松过程在长度为 $t$ 的区间内的到达次数，而 $T$ 是一个长度服从参数为 $v$ 的指数分布、且与该泊松过程相互独立的区间，则 $N_T + 1$ 服从参数为 $v/(\lambda + v)$ 的几何分布。

> <span style="color:#7f8c8d;">[原页此处 OCR 已修正] 表中 $\lambda$ 与 $v$（原文写作 `A`；`v`）等参数名、以及破折号断字（`pro­cesses`、`parame­ter`）均由本 worker 依语境改正；`PMFsjPDFs` 复原为 「PMFs/PDFs」；第 18 行 `let Y 0 when N O` 复原为「let $Y = 0$ when $N = 0$」。数值一律未臆造。</span>

让我们还注意到相关且颇为深刻的一个事实：大量（未必为泊松的）相互独立的到达过程之和，可以用一个泊松过程来近似，其到达率等于各分到达率之和。各分量过程相对于总量必须具有足够小的比率（这样就不会有哪一分量把自己的概率特征强加于总的到达过程之上），并且它们还必须满足某些技术性（technical）的数学假设。对该事实的进一步讨论超出本书范围，但我们注意到，在相当程度上它正是泊松型过程在实践中大量出现的原因。例如，一座城市中产生的电话业务量（telephone traffic）由大量……
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本页末尾点到为止的这个事实，即"大量独立（甚至非泊松的）稀疏到达过程叠加后趋近泊松"，文献中叫 Palm–Khintchine 定理：Conny Palm（瑞典，1943 年电话流量研究）与 Aleksandr Khinchin（苏联）的成果，排队论教材常写作"大量独立平衡更新过程的叠加渐近泊松"。它的地位与中心极限定理平行——CLT 说"大量独立随机变量之和趋于正态"，Palm–Khintchine 说"大量独立稀疏点过程叠加趋于泊松"，所以城市电话话务、交通事故、商店顾客到达才普遍呈泊松特征：不是每个源是泊松的，而是"很多个稀疏源叠加"这个结构本身逼出了泊松。这正是 §6.2 存在感的现实依据，也是 p330 表"合并"结论的无极限版本。前沿延伸：这条普适性衍生出现代泊松点过程（Poisson point process）理论，用于空间统计、无线网络覆盖建模乃至深度学习中的数据增强采样；你以后学到这些时，根子就在这一页。


> <span style="color:#7f8c8d;">本页到此为一插入的脚注板块说明，内容延续至下一页；段末「例如，一座城市中产生的电话业务量（telephone traffic）由大量……」句子被页界截断，待下一页续接。</span>

<!-- ===== PDF p331 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.2（续）

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）**</span> <span style="color:#7f8c8d;">（本页页眉仅给出章节总标题「The Bernoulli and Poisson Processes / Chap. 6」，未标明小节号；页首为上一页 §6.2「大量独立到达之和近似泊松」讨论的延续，随后进入本小节新的子节「随机到达悖论（The Random Incidence Paradox）」。书内印刷页码为 322。）</span>

> <span style="color:#7f8c8d;">承接上一页：上一页段末说一座城市中产生的电话业务量由大量……（句子被页界截断），本页页首以"…component processes"续接该句，讲各分量过程不必是泊松的，但总量与若干其他随机到达过程均宜用泊松过程建模。</span>

……该电话业务量由大量分量过程（component processes）构成，其中每一个分量过程刻画了个别住户打进或打出的电话。这些分量过程未必是泊松的：例如有些人倾向于成批地打电话，而且（通常）在通话过程中既无法发起、也无法接听第二个电话。不过，总的话务量（telephone traffic）用泊松过程来建模非常合适。基于同样的原因，一座城市中的汽车事故（auto accidents）、商店里的顾客到达（customer arrivals）、放射性物质（radioactive material）的粒子发射等过程，往往也都具有泊松过程的特征。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上文「成批地打电话」处的破损字符（原文 `in batches`）应为分号或连词，此处按语义复原为「而且……在通话过程中既无法发起也法接听」；`city`（应为逗号）与 `Poisson process`（应为句点）各有一处破损符号，均按语境补全，未臆造数值。</span>

<span style="color:#c0392b;">**随机到达悖论（The Random Incidence Paradox）**</span>

泊松过程的到达把时间轴（time axis）分割成一段段的到达间隔（interarrival interval）；每一个到达间隔始于一次到达、止于下一次到达的时刻。我们已经看到，这些到达间隔的长度是参数为 $\lambda$ 的相互独立的指数随机变量（exponential random variable），其中 $\lambda$ 是过程的速率（rate）。更确切地说，对每一个 $k$，第 $k$ 个到达间隔的长度都具有这个指数分布。在本小节中，我们从另一个不同的视角来考察这些到达间隔。

> <span style="color:#7f8c8d;">[原页此处 OCR 已修正] 原文将速率参数误识为 `A`（「with parameter A, where A is the rate」），按本章惯例此处统一改为 $\lambda$；下文 $t^*$ 前后的时间端点记号沿用原文 `V`，为避免歧义分别用 $\underline V$ 与 $\overline V$ 区分。</span>

让我们固定一个时刻 $t^*$，并考虑包含 $t^*$ 的那段到达间隔的长度 $L$。作为一个具体的场景，设想一个人在某任意时刻 $t^*$ 来到公交站（bus station），记录下从上一班公交车到达、到下一班公交车到达之间的时间。这个人的到达（the arrival of this person）常被称为「随机到达」（random incidence），但读者应当意识到，这个术语其实是有误导性的：$t^*$ 仅仅是一个特定的时间实例（time instance），而不是一个随机变量。

我们假定 $t^*$ 远大于泊松过程的起始时刻，这样就相当有把握在时间 $t^*$ 之前已经发生过一次到达。为避免纠缠 $t^*$ 到底该多大这一枝节问题，我们干脆假定泊松过程从一开始就一直在运行（running forever），从而可以确定在 $t^*$ 之前必有一次到达，于是 $L$ 是良定义的（well-defined）。有人可能粗略地认为，$L$ 是一个「典型到达间隔」的长度、从而服从指数分布，但事实并非如此。相反，我们将证明 $L$ 具有二阶的埃尔朗 PDF（Erlang PDF of order two）。

这一现象称为随机到达现象或随机到达悖论（random incidence phenomenon or paradox），可以借助图 6.7 加以解释。

> <span style="color:#7f8c8d;">Fig. 6.7</span>

设 $[\underline V, \overline V]$ 为包含 $t^*$ 的那段到达间隔，从而 $L = \overline V - \underline V$。特别地，$\underline V$ 是 $t^*$ 之前首次到达的时刻，$\overline V$ 是 $t^*$ 之后首次到达的时刻。我们把 $L$ 分成两部分，

```math
L = (t^* - \underline V) + (\overline V - t^*),
```

其中 $t^* - \underline V$ 是自上一次到达以来已经过去的时间（elapsed time），而 $\overline V - t^*$ 是直到下一次到达还剩余的时间（remaining time）。注意 $t^* - \underline V$ 由过程在 $t^*$ 之前的过去历史（past history）决定，而 $\overline V - t^*$ 由过程在时间 $t^*$ 之后的未来（future）决定。由泊松过程的独立性性质（independence properties），随机变量 $t^* - \underline V$ 与 $\overline V - t^*$ 相互独立。由无记忆性（memorylessness）性质，泊松过程在时刻 $t^*$ 重新开始（starts fresh），因此 $\overline V - t^*$ 是参数为 $\lambda$ 的指数随机变量。随机变量 $t^* - \underline V$ 也服从指数……
> <span style="color:#1e8449;">[note] Note（译者注）:</span> "随机到达悖论"的谜底是"长度偏置采样"（length-biased sampling），这是本节最有普适价值的概念。一个人"随机"落在时间轴的某点 $t^*$，他落入某段到达间隔的概率与该间隔的长度成正比——因为更长的间隔占据更长的时段，被随机点命中的机会更大。于是被观测的间隔不再"典型"：它的分布被长度加权过，等价于"先按长度比例抽样"。本页接着展示这一现象最迷人的数学面孔：$t^*-\underline V$（已流逝时间）与 $\overline V-t^*$（剩余时间）竟然各自还是参数 $\lambda$ 的指数分布、且相互独立，因而它们的和 $L$ 服从二阶 Erlang 而非指数——"间隔的每一半都是指数，合起来却不是指数"，这正是无记忆性在双向作用的痕迹（过程向过去与向未来都"重新开始"）。跨课程上，这是"选择偏倚"（selection bias）在数学上的严格版本：样本被观测的概率取决于样本自身的性质。智能科学里做数据采样、实验设计时必须时刻警惕它。


> <span style="color:#7f8c8d;">本页到「随机变量 $t^* - \underline V$ 也服从指数……」一句被页界截断，关于 $t^* - \underline V$ 亦为指数分布及相关推论的论证延续至下一页；原文同样以 OCR 破损符 `` 结尾（"is also exponential"），上下文明确无误。</span>

<!-- ===== PDF p332 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.2（续）

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）—— 子节「随机到达悖论（The Random Incidence Paradox）」（续）**</span> <span style="color:#7f8c8d;">（Sec. 6.2，原书页码 323；本页续接上一页 §6.2 随机到达悖论子节的推导：先给出「到达间隔长度 $L$ 服从埃尔朗二阶分布」的正式论证，随后是图 6.7 的说明、$L$ 的 PDF/均值/方差，以及用公交站算例演示随机到达偏置的 Example 6.17。）</span>

> <span style="color:#7f8c8d;">承接上一页：上一页末已指出 $t^* - V$ 也服从指数分布，并已把含 $t^*$ 的到达间隔分解为 $L = (t^* - V) + (V' - t^*)$，其中 $t^* - V$ 是自上次到达起的流逝时间（elapsed time），$V' - t^*$ 是至下次到达为止的剩余时间（remaining time）。本页给出正式论证并导出 $L$ 的概率规律。</span>

为直观地体会这一点，可以设想把泊松过程在时间上（向前或向后）运行——其到达间隔的统计特性并不因此改变。

> <span style="color:#7f8c8d;">[原页页首 OCR 碎裂] 页首几行（「To realize this, … if we run the … forward or backward, no … moves …」）残缺难辨，仅保留「更正式的论证（a more formal argument）」这一引导语及其后的结论，中间直觉性说明按上下文补全，未作数值臆造。</span>

更正式的论证（a more formal argument）如下：事件 $\{t^* - V > x\}$ 等价于在时间区间 $(t^* - x,\; t^*]$ 内没有发生任何到达；由于任一时间长度为 $x$ 的区间内到达次数服从参数为 $\lambda x$ 的泊松分布，该区间内到达次数恰为 $0$ 的概率为 $e^{-\lambda x}$，于是

```math
P\big(t^* - V > x\big) = P\big(\text{长度为 }x\text{ 的区间内 }0\text{ 次到达}\big) = e^{-\lambda x},
```

所以 $t^* - V$ 服从参数为 $\lambda$ 的指数分布（exponential distribution），均值为 $1/\lambda$。类似地，由无记忆性（memorylessness）可知，$V' - t^*$ 也服从参数为 $\lambda$ 的指数分布，均值为 $1/\lambda$。

> <span style="color:#7f8c8d;">图 6.7（Figure 6.7）：随机到达现象（random incidence phenomenon）示意图。对固定的时刻 $t^*$，包含它的到达间隔 $[V, V']$ 由两部分组成：流逝时间 $t^* - V$ 与剩余时间 $V' - t^*$。</span>

这两个随机变量 $t^* - V$ 与 $V' - t^*$（分别由过程在 $t^*$ 之前的过去历史与 $t^*$ 之后的未来决定）相互独立，且各自服从参数为 $\lambda$ 的指数分布。因此 $L$ 是两个相互独立的指数随机变量之和，即服从二阶埃尔朗分布（Erlang distribution of order two），其 PDF 为

```math
f_L(\tau) = \lambda^2 \tau\, e^{-\lambda \tau}, \qquad \tau \ge 0 ,
```

均值为 $2/\lambda$，方差为 $2/\lambda^2$。

随机到达（random incidence）这一概率建模（probabilistic modeling）问题的根源在于：在任意时刻（at an arbitrary time）$t^*$ 抽样时，该时刻更可能落入一个较长的到达间隔而非较短的到达间隔——较长的间隔占据时间轴上更长的区段，因此更可能包含 $t^*$。公交站等同类情境中也会出现类似现象：任意时刻到达的旁观者（as seen by an arbitrary arrival）所看到的到达间隔，其期望长度会大于一个「典型」到达间隔的均值 $1/\lambda$。作为这一后果的体现，下面的例子将给出说明。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.17　公交站的随机到达（Random Incidence at a Bus Station）**</span>

一个人在一个「随机」时刻出现在公交站，此处「随机」意指该到达时刻在相邻两班公交之间的时间区间上服从均匀分布（uniformly distributed）。公交车的到达间隔以概率 $1/2$ 为 5 分钟、以概率 $1/2$ 为 55 分钟。

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 源 OCR 把该概率误读为「1/12」，并把数值夹杂成「5·2」「55·」等残片、阶数与系数碎裂；此处依「典型平均到达间隔为 30 分钟」以及 $E[I^2]/E[I] = 50.83$ 的结果反推，重建为「以概率 $1/2$ 为 5 分钟、以概率 $1/2$ 为 55 分钟」，数值一律未改动。</span>

一个「典型」到达间隔的期望长度为

```math
E[I] = \frac{1}{2}\cdot 5 + \frac{1}{2}\cdot 55 = 30 ,
```

即平均每 30 分钟一班车。然而，由于此人更可能落入较长的到达间隔，他所处那个到达间隔的期望长度应等于 $E[I^{2}] / E[I]$，即
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这里的期望公式 $E[I^2]/E[I]$ 把"长度偏置"量化到底，值得亲手推一遍。设典型间隔长 $I$ 的分布已知，随机时刻落入长度为 $I$ 的间隔的概率 $\propto I$，所以被观测间隔的加权期望 $=\sum I\cdot\big(I\cdot P(I)\big)/E[I]=E[I^2]/E[I]$（分母 $E[I]$ 用于归一化权重）。代入本题：$E[I]=30$，$E[I^2]=\frac12\cdot5^2+\frac12\cdot55^2=1525$，于是 $1525/30\approx50.83$，几乎是"典型值"30 的 1.7 倍。数值差异的直觉在时间份额：55 分钟的间隔虽只占一半"个数"，却占据约 $55/60\approx92\%$ 的时间轴，随机到达者几乎必然落入它。这套"按比例加权再归一化"的操作，正是机器学习里重要性采样（importance sampling）与统计中 Horvitz–Thompson 估计的核心动作：采样概率已知且不均匀时，用"$1/$概率"做权重校正。你在 6.006 的随机化分析与后续统计课程里会反复见到这个加权分母。


```math
\frac{\frac{1}{2}\cdot 5^{2} + \frac{1}{2}\cdot 55^{2}}{30}
= \frac{12.5 + 1512.5}{30}
= 50.83 ,
```

这比 30 分钟的平均到达间隔（average interarrival time）要大得多（considerably larger）。这正是随机到达悖论（random incidence paradox）所引入的长间隔偏向。

> <span style="color:#7f8c8d;">本页于此截止；Example 6.17 以 50.83 与 30 分钟的对比在本页末尾收束。下一页（原书 324）以「正如前一个例子所表明的，随机到达是一种微妙的现象……」（As the preceding example indicates, random incidence is a subtle …,）收尾并引出对公交载客量调查的又一算例，仍属同一小节 §6.2 的续，编号连续、无需另起。</span>

<!-- ===== PDF p333 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

> <span style="color:#7f8c8d;">（本页承接上一页 §6.2 中关于随机到达（random incidence）现象的讨论，先以公交车使用率调查的实例作结，随后页中转入 §6.3 章末小结与讨论。本章打印页码 324。随机到达、等待时间悖论属 §6.2 泊松过程相关正文，§6.3 为本页新启的小节标题。）</span>

正如前一例所示，随机到达（random incidence）是一种隐蔽（subtle）的现象：它倾向于偏向较大的到达间隔（interarrival intervals），并且除了泊松过程（Poisson process）场合之外，还可能在其他场景也显现出来。一般而言，当不同的计算得到相互矛盾的结果时，其原因在于它们对应着不同的概率机制（probabilistic mechanisms）。例如，固定一个非随机的 $k$、并考察与之关联的第 $k$ 个到达间隔的随机取值，与固定一个时刻 $t$、并考察与之关联的、其第 $K$ 个到达间隔恰好含 $t$ 的随机 $K$，这是两个不同的实验（experiment）。

接下来是一个风格与之相近的最后例子。考虑对城镇公交车使用率（utilization）的调研（survey）。一种做法是随机挑选几辆公交车，并计算所选车辆中乘客数的平均值。另一种做法是随机挑选几位公交车乘客（bus riders），观察他们所乘坐的公交车，然后计算后者这组车辆中乘客数的平均值。两种方法各自给出的估计在统计上差别很大，且第二种方法存在向上（upwards）的偏倚。原因在于：用第二种方法时，挑到载客量很大的公交车的可能性，远比挑到近乎空载（near-empty）的公交车要大。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> "挑车统计"与"挑乘客统计"给出不同答案，是随机到达悖论在日常生活的镜像，也是"抽样机制决定统计量"的铁证。挑车时每辆车等概率入选，得到的是"车辆的平均载客量"；挑乘客时载客量大的车更容易被挑到（每名乘客一票），统计量被"载客量"加权，必然向上偏。这与 p331 的数学完全同构：被抽中的概率正比于样本自身的某个特征。最著名的同类现象是"友谊悖论"（friendship paradox）：随机挑一位网民，TA 的朋友平均拥有的朋友数，多于随机挑一位网民的"平均朋友数"——因为朋友多的用户占据更多"朋友位"，被随机"朋友"命中的概率更大。对智能科学而言，这条注是方法论警示：采样协议（uniform over what）决定一切结论；6.042J 里"样本空间必须先精确描述"、CLRS 随机算法里"均匀随机必须明确是在什么集合上均匀"，都在说同一件事。这也是"均值不代表典型"的生动注脚。


<span style="color:#c0392b;">**§6.3　小结与讨论（Summary and Discussion）**</span>

在本章中，我们介绍并分析了两种无记忆（memoryless）到达过程（arrival processes）。伯努利过程（Bernoulli process）在离散时间（discrete time）中演化：在每个离散时间步（step）内，都以常概率 $p$ 发生一次到达。泊松过程（Poisson process）在连续时间（continuous time）中演化：在每个长度为 $\delta > 0$ 的小区间（small interval）内，都以近似等于 $\lambda \delta$ 的概率发生一次到达。在这两种情形中，不相交时间区间内的到达数都假定相互独立。泊松过程可视为伯努利过程的极限情形（limiting case），其中每个离散时间槽（time slot）的时长被取得非常小，即为一个很小的数 $\delta$。这一事实可用于在两个过程的主要性质之间建立类比，并将由其中一个过程获得的见解迁移到另一个过程上。

利用伯努利与泊松过程的无记忆性（memorylessness property），我们推导出下列结论：

- (a) 给定长度的时间区间内到达数的 PMF（probability mass function，概率质量函数）分别为二项分布（binomial）与泊松分布（Poisson）。
- (b) 相继到达之间的时间分布分别为几何分布（geometric）与指数分布（exponential）。
- (c) 直到第 $k$ 次到达的时间分布分别服从 $k$ 阶 Pascal 分布（Pascal of order k）与 $k$ 阶 Erlang 分布（Erlang of order k）。

此外，我们还看到，可以取两个相互独立的伯努利过程（相应地，泊松过程）为出发点，并把它们“合并”（merge）成一个新的伯努利过程（相应地，泊松过程）。反之，若对每一次到达都通过抛一枚成功概率为 $p$ 的硬币来“接受”（accept）它，即“分流”（splitting），则被接受的到达所构成的过程，是一个到达率（arrival rate）为原过程 $p$ 倍的伯努利过程或泊松过程。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] §6.3 末段经 OCR 后部分符号退化：原书中的 $\lambda\delta$（每长 $\delta$ 的小区间内到达概率近似值）被识别成 “A8”，小区间长度 $\delta$ 被识别成 “6”。此处按伯努利/泊松过程的标准表述重建为 $\lambda\delta$ 与 $\delta$，数值与语义未作改动。</span>

<!-- ===== PDF p334 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**§6.3　小结与讨论（Summary and Discussion）**</span> <span style="color:#7f8c8d;">（Sec. 6.3，原书页码 325；本页为 §6.3 小结段的一页，承接上一页对「随机到达」现象的讨论收尾。）</span>

> <span style="color:#7f8c8d;">承接上一页：本节小结总结泊松过程章节末尾关于随机到达（random incidence）现象的讨论。</span>

最后我们考虑了「随机到达」现象（random incidence）：一位外部观察者（external observer）在某个给定的时间到达，并测量他恰好落入其中的那个到达间隔（interarrival interval）。被测量间隔的概率性质并不「典型」（typical），因为到达的观察者更可能落进一个较大的到达间隔之中。这一现象表明，当谈论一个「典型」间隔时，我们必须仔细描述它被选出的机制。一般而言，不同的机制会导致不同的概率性质。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 收束全节的这句"必须仔细描述间隔被选出的机制"，是全章的方法论落点：分布从来不是对象的固有属性，而是"对象 × 抽样协议"的联合产物。同一个泊松过程，固定第 $k$ 个间隔（固定 $k$）与固定时刻 $t^*$ 落入的间隔（随机 $K$），是两个不同的实验，给出指数与 Erlang 两种不同答案——差异不在过程，而在"谁被选中"。这与 CSAPP 测量性能时"测量方法决定结果"、6.042J 定义随机实验时"必须先精确指定样本空间"一脉相承；在算法里则对应 CLRS 反复强调的"随机化必须说明均匀范围"。往后进入排队论、马尔可夫链乃至机器学习的数据生成时，这个元教训会反复出现：任何"随机挑选"都必须回答"在哪分布上、按什么权重挑"。建议把它和 p331 的"长度偏置"一起，作为本章最重要的两个"思维防撞条"记入长期记忆——它们是你把概率直觉用对、用准的护身符。


<!-- ===== PDF p335 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**习题区（PROBLEMS）**</span>

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span>

> <span style="color:#7f8c8d;">本页为第 6 章习题区开篇（原书印刷页 326）。页眉题为「Chap. 6 / The Bernoulli and Poisson Processes / PROBLEMS / SECTION 7.1」；此处「SECTION 7.1」系 OCR 将「SECTION **6**.1」误认所致，本章题为第 6 章、正文内容实为伯努利过程（伯努利与泊松过程）习题，故按 §6.1 定位，不作按字面传播。习题编号自 Problem 1 起。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 1.**</span>

Each of $n$ packages is loaded independently onto either a red truck (with probability $p$) or onto a green truck (with probability $1-p$). Let $R$ be the total number of items selected for the red truck and let $G$ be the total number of items selected for the green truck.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 第 6 章习题区开篇。这一区（Problem 1–27）是前五章工具箱的「压力测试」：二项 / 几何 / 帕斯卡 PMF、条件期望与全期望定律、指示随机变量与线性期望。你已从 CLRS 附录 C 见过这些武器——indicator 变量 + 线性期望是 CLRS 期望分析的两大引擎（如雇佣问题给出 O(ln n) 的期望），这套习题会让它们反复登台。值得先记下一个全书级伏笔：伯努利 / 泊松过程的「无记忆性」与第 7 章马尔可夫链的「一阶记忆」只隔一层皮——无记忆说「未来完全不依赖过去」，马尔可夫性质说「未来只通过现在依赖过去」。当你啃到 Problem 5\*/18\*/24\* 的「随机涉入」与「增广」技巧时，会发现它们几乎都是第 7 章思想的预热。建议做题时把每一题的「等待时间」都当作一次状态转移来想，后面会省很多力气。


(a) Determine the PMF, expected value, and variance of the random variable $R$.

(b) Evaluate the probability that the first item to be loaded ends up being the only one on its truck.

(c) Evaluate the probability that at least one truck ends up with a total of exactly one package.

(d) Evaluate the expected value and the variance of the difference $R - G$.

(e) Assume that $n \ge 2$. Given that both of the first two packages to be loaded go onto the red truck, find the conditional expectation, variance, and PMF of the random variable $R$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 2.**</span>

Dave fails quizzes with probability $1/4$, independent of other quizzes.

(a) What is the probability that Dave fails exactly two of the next six quizzes?

(b) What is the expected number of quizzes that Dave will pass before he has failed three times?

(c) What is the probability that the second and third time Dave fails a quiz will occur when he takes his eighth and ninth quizzes, respectively?

(d) What is the probability that Dave fails two quizzes in a row before he passes two quizzes in a row?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 3.**</span>

A computer system carries out tasks submitted by two users. Time is divided into slots. A slot can be idle, with probability $p_I = 1/6$, and busy with probability $p_B = 5/6$. During a busy slot, there is probability $p_{1|B} = 2/5$ (respectively, $p_{2|B} = 3/5$) that a task from user 1 (respectively, 2) is executed. We assume that events related to different slots are independent.

(a) Find the probability that a task from user 1 is executed for the first time during the 4th slot.

(b) Given that exactly 5 out of the first 10 slots were idle, find the probability that the 6th idle slot is slot 12.

(c) Find the expected number of slots up to and including the 5th task from user 1.

> <span style="color:#7f8c8d;">[OCR 说明] 本页次行概率符号 OCR 碎裂：$p_I$、$p_B$ 原读作 `PI`、`PB`，$p_{1|B}$、$p_{2|B}$ 原读作 `P I I B`、`P2 1 B`，此处按上下文（user 1 / user 2 的任务执行概率 $2/5$ 与 $3/5$）重建；数值 $1/6$、$5/6$、$2/5$、$3/5$ 均未改动。</span>

<!-- ===== PDF p336 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> —— §6.1 习题（续）

> <span style="color:#7f8c8d;">本页为第 6 章 §6.1 伯努利过程（The Bernoulli Process）习题区（Problems）的延续（印本页码 327）：页首仅见 running header「Problems」，无新节标题，直接续接上一页（印本页码 326、文件页 335）已在进行的习题。页首承接 **Problem 3** 的 (d)、(e) 两小题，随后为本页独立出现的带星号习题 **Problem 4.\*** 与 **Problem 5.\***。注：上一页印出的本节标题在 OCR 中为「SECTION 7.1. The Bernoulli Process」，按全集定位应为 §6.1（疑为原书笔误），本页据此按 §6.1 处理。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 3（续）—— （d）、（e）**</span>

> <span style="color:#7f8c8d;">Problem 3 的题干与 (a)–(c) 小题见上一页（印本页码 326）：某计算机系统执行两位用户提交的任务，时间划分为若干时隙（slots），时隙空闲的概率为 $p_I = 1/6$、忙的概率为 $p_B = 5/6$；在忙时隙内，来自用户 1/用户 2 的任务被执行的概率分别为 $p_{1\mid B} = 2/5$、$p_{2\mid B} = 3/5$，不同时隙的事件相互独立。本页继续求解其 (d)、(e) 两小题。</span>

( d ) Find the expected number of busy slots up to and including the 5th task from user 1.

( e ) Find the PMF, mean, and variance of the number of tasks from user 2 until the time of the 5th task from user 1.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 4. \***</span>

Consider a Bernoulli process with probability of success in each trial equal to $p$.

( a ) Relate the number of failures before the $r$th success (sometimes called a negative binomial random variable) to a Pascal random variable and derive its PMF.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这是负二项（negative binomial）随机变量的第一性原理入场。帕斯卡变量 Y 是「第 r 次成功发生的时刻」，失败数 X = Y − r。推导 p_X(k) 只靠一个计数论证：把 k 次失败与 r−1 次成功任意排列，最后一位必须是第 r 次成功，前 k+r−1 个位置里任选 r−1 个放成功，共 C(k+r−1, r−1) 种——正是你在 6.042J 学过的 stars-and-bars 组合计数的变体。期望 E[X] = r(1−p)/p 有个漂亮直觉：试验以 p : (1−p) 的比率产出成功与失败，r 次成功自然「配给」约 r(1−p)/p 次失败。注意「独立试验」是这里唯一的杠杆——一旦试验之间出现依赖（第 7 章），这类「等待第 r 个事件」的干净公式立即失效，必须改用状态分析。CLRS 附录 C 也定义了负二项分布，算法分析里「等待 k 次成功」的场景与它同源。


( b ) Find the expected value and variance of the number of failures before the $r$th success.

( c ) Obtain an expression for the probability that the $i$th failure occurs before the $r$th success.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

( a ) Let $Y$ be the number of trials until the $r$th success, which is a Pascal random variable of order $r$. Let $X$ be the number of failures before the $r$th success, so that $X = Y - r$. Therefore, $p_X(k) = p_Y(k + r)$, and

```math
p_X(k) = \binom{k+r-1}{r-1} p^{r} (1-p)^{k}, \qquad k = 0, 1, \ldots .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原行在「$p_X(k) = p_Y(k+r)$，and」之后、以「$k = 0,1,\ldots$」收尾处，本该出现的 $p_Y(k+r)$ 展开式（带二项系数的显式 PMF）在 OCR 中被吞落；上式为按 $Y$ 是 $r$ 阶帕斯卡随机变量的标准 PMF $p_Y(k) = \binom{k-1}{r-1} p^{r}(1-p)^{k-r}$ 并代 $k \mapsto k+r$ 而重建，数值与记号未作改动。</span>

( b ) Using the notation of part ( a ) , we have

```math
E[X] = E[Y] - r = \frac{r}{p} - r = \frac{r(1-p)}{p}.
```

Furthermore,

```math
\operatorname{var}(X) = \operatorname{var}(Y) = \frac{r(1-p)}{p^{2}}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (b) 的两式在原行被拆散碎裂（分子 $(1-p)r$、分母 $p$ 与 $p^2$ 分列数行），上面按帕斯卡随机变量的均值 $E[Y] = r/p$、方差 $\operatorname{var}(Y) = r(1-p)/p^{2}$ 重建。</span>

( c ) Let again $X$ be the number of failures before the $r$th success. The $i$th failure occurs before the $r$th success if and only if $X \ge i$. Therefore, the desired probability is equal to

```math
P(X \ge i) = \sum_{k = i}^{\infty} p_X(k) = \sum_{k = i}^{\infty} \binom{k+r-1}{r-1} p^{r} (1-p)^{k}, \qquad i = 1, 2, \ldots .
```

An alternative formula is derived as follows. Consider the first $r + i - 1$ trials. The number of failures in these trials is at least $i$ if and only if the number of successes is less than $r$. But this is equivalent to the $i$th failure occurring before the $r$th success. Hence, the desired probability is the probability that the number of successes in $r + i - 1$ trials is less than $r$, which is

```math
\sum_{k = 0}^{r-1} \binom{r+i-1}{k} p^{k} (1-p)^{r+i-1-k}, \qquad i = 1, 2, \ldots .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (c) 的两个公式行（分别位于「equal to」与句末「which is」之后）在 OCR 中被吞落，其上两式各按「$X \ge i$（即第 $i$ 次失败发生在第 $r$ 次成功之前）的概率 = $P(X \ge i)$」与「$r+i-1$ 次试验中成功次数少于 $r$ 的概率」依文字推导重建。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 5. \***</span>

Random incidence in the Bernoulli process. Your cousin has been playing the same video game from time immemorial. Assume that he wins each …
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 5\* 是全章最值得玩味的一题——「随机涉入」（random incidence）：你在任意时刻闯入一条几何胜局序列，恰逢失败。无记忆性给出两个对称结论：X = N − t（到下次胜利）与 Y = t − M（自上次胜利）都独立同服从几何(p)，于是 L = N − M − 1 = X + Y − 1，PMF 为 i·p²(1−p)^{i−1}。悖论所在：相邻两场胜利的间隔平均只有 1/p，但你随机降落点所在的「含 t 的胜利间隔」N − M 平均长达 2/p——因为更长的间隔有更大的时长可供随机点命中。这就是检验悖论（inspection paradox）的离散雏形：随机观察者总是「落进」偏长的间隔。这个「观察者引入偏差」的直觉会在第 7 章稳态分析、Problem 27\* 与 §7.5 排队问题里反复回响，先建立它，后面一路受用。


> <span style="color:#7f8c8d;">本页止于 Problem 5.\* 题干的「Assume that he wins each …」，其后内容（该游戏的独立胜局概率等）续接下一页（印本页码 328）。</span>

<!-- ===== PDF p337 ===== -->

> <span style="color:#7f8c8d;">第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）—— 习题区（Problems）延续页，打印页码 328，承接上一页 p336（Problem 1–5 的题目开头）。本页首为上一页 **Problem 5 $^{*}$（Random incidence in the Bernoulli process，伯努利过程中的随机涉入）** 的题干收尾与完整 `*` 题 Solution；随后是 **Problem 6 $^{*}$** 与 **Problem 7 $^{*}$** 两题（本页三者均属伯努利过程（Bernoulli process） §6.1 的习题组，泊松过程习题组自下一页 p338「SECTION 6.2 The Poisson Process」起）。题干与带 `*` 题的 Solution 遵照英文原题，不翻译。</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#2471a3;">Problem 5 $^{*}$（续）　Random incidence in the Bernoulli process（伯努利过程中的随机涉入）</span>

> <span style="color:#7f8c8d;">承接上一页：题干在 p336 页尾以「Your cousin has been playing the same video game from time immemorial. Assume that he wins each」中断，本页续接下列英文原句，随后给出该 `*` 题的完整英文 Solution。</span>

**game with probability $p$, independent of the outcomes of other games.** At midnight, you enter his room and witness his losing the current game. What is the PMF of the number of lost games between his most recent win and his first future win?

<span style="color:#2471a3;">**[solution]**</span> **Solution.** Let $t$ be the number of the game when you enter the room. Let $M$ be the number of the most recent past game that he won, and let $N$ be the number of the first game to be won in the future. The random variable $X = N - t$ is geometrically distributed with parameter $p$. By symmetry and independence of the games, the random variable $Y = t - M$ is also geometrically distributed with parameter $p$. The games he lost between his most recent win and his first future win are all the games between $M$ and $N$. Their number $L$ is given by

```math
L = N - M - 1 = X + Y - 1.
```

Thus, $L + 1$ has a Pascal PMF of order two, and

```math
p_{L+1}(k) = (k - 1)\,p^{2}\,(1 - p)^{k - 2}, \qquad k = 2, 3, \ldots
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式为 $L + 1$ 的二阶 Pascal PMF（源 OCR 在「and」与「$k = 2, 3, \ldots$」之间只残留换行，未显式给出式样），系按二阶 Pascal PMF $p_{L+1}(k) = \binom{k-1}{1}p^{2}(1-p)^{k-2}$ 重建，并与下文 $p_L(i) = i p^{2}(1-p)^{i-1}$ 相互印证；数值一律未改动。</span>

Hence,

```math
p_L(i) = P(L + 1 = i + 1) = i\,p^{2}\,(1 - p)^{i - 1}, \qquad i = 1, 2, \ldots
```

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#2471a3;">Problem 6 $^{*}$　Sum of a geometric number of independent geometric random variables（几何个数的独立几何随机变量之和）</span>

Sum of a geometric number of independent geometric random variables. Let $Y = X_1 + \cdots + X_N$, where the random variables $X_i$ are geometric with parameter $p$, and $N$ is geometric with parameter $q$. Assume that the random variables $N$, $X_1$, $X_2$, $\ldots$ are independent. Show, without using transforms, that $Y$ is geometric with parameter $pq$. **Hint:** Interpret the various random variables in terms of a split Bernoulli process.

<span style="color:#2471a3;">**[solution]**</span> **Solution.** We derived this result in Chapter 4, using transforms, but we develop a more intuitive derivation here. We interpret the random variables $X_i$ and $N$ as follows. We view the times $X_1$, $X_1 + X_2$, etc. as the arrival times in a Bernoulli process with parameter $p$. Each arrival is rejected with probability $1 - q$ and is accepted with probability $q$. We interpret $N$ as the number of arrivals until the first acceptance. The process of accepted arrivals is obtained by splitting a Bernoulli process and is therefore itself Bernoulli with parameter $pq$. The random variable $Y = X_1 + \cdots + X_N$ is the time of the first accepted arrival and is therefore geometric with parameter $pq$.

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#2471a3;">Problem 7 $^{*}$　The bits in a uniform random variable form a Bernoulli process（均匀随机变量中的各位构成一个伯努利过程）</span>

The bits in a uniform random variable form a Bernoulli process. Let $X_1$, $X_2$, $\ldots$ be a sequence of binary random variables taking values in the set $\{0, 1\}$. Let $Y$ be a continuous random variable that takes values in the set $[0, 1]$. We relate $X$ and $Y$ by assuming that $Y$ is the real number whose binary representation is $0.X_1 X_2 X_3 \cdots$. More concretely, we have

```math
Y = \sum_{k = 1}^{\infty} \frac{X_k}{2^{k}}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「More concretely, we have」之后的二进制展开式在原页 OCR 中只残留若干孤立的占位圆点 `•`（未显现实际式样），上式按 $Y = 0.X_1 X_2 X_3 \cdots$ 的二进制扩张重建为 $Y = \sum_{k\ge 1} X_k / 2^{k}$；若需最严格原文请回查原书页 328。</span>

(a) Suppose that the $X_i$ form a Bernoulli process with parameter $p = 1/2$. Show that $Y$ is uniformly distributed. **Hint:** Consider the probability of the event $(i - 1)/2^{k} < Y < i/2^{k}$, where $i$ and $k$ are positive integers.

> <span style="color:#7f8c8d;">[翻页续接] Problem 7 的 (b) 部分在 p337 未给出，自下一页 p338 起续接其英文 Solution。</span>

<!-- ===== PDF p338 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> —— 习题区（续）

> <span style="color:#7f8c8d;">承接上一页：本页位于本章习题区中部。页首为上一页某道题的 `Solution` 的末尾（该题把均匀随机变量 $Y$ 的二进制展开与 Bernoulli 过程联系起来，分别处理 part (a) 与 part (b)）；其后进入「泊松过程」一节的练习题 **Problem 8 / 9 / 10**。注：源 OCR 页眉写作 `SECTION 7.2. The Poisson Process`，但正文内容（Bernoulli 过程、泊松过程）显然属于第 6 章，第 6 章泊松小节实为 §6.2，此处 `7` 疑为 OCR 将 `6` 误认，编号未改动、仅如实标注。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 7（续）— Solution**</span>

(b) Suppose that $Y$ is uniformly distributed. Show that the $X_i$ form a Bernoulli process with parameter $p = 1/2$.

**Solution. (a)** We have

```math
P(Y \in [0,\, 1/2]) = P(X_1 = 0) = \frac{1}{2} = P(Y \in [1/2,\, 1]).
```

Furthermore,

```math
P(Y \in [0,\, 1/4]) = P(X_1 = 0,\, X_2 = 0) = \frac{1}{4}.
```

Arguing similarly, we consider an interval of the form $\left[(i-1)/2^{k},\, i/2^{k}\right]$, where $i$ and $k$ are positive integers and $i \le 2^{k}$. For $Y$ to fall in the interior of this interval, we need $X_1, \ldots, X_k$ to take on a particular sequence of values (namely, the digits in the binary expansion of $i-1$). Hence,

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 紧接 "Hence," 之后本应有一个概率等式（应为 $P\big(Y \in [(i-1)/2^{k},\, i/2^{k}]\big) = 1/2^{k}$），原图把该行丢失，此处括号内容为按文意补齐的具体式样，未改动任何数值。</span>

Note also that for any $y \in [0, 1]$, we have $P(Y = y) = 0$, because the event $\{Y = y\}$ can only occur if infinitely many $X_i$'s take on particular values, a zero probability event. Therefore, the CDF of $Y$ is continuous and satisfies
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 7\* 揭示了均匀分布与「无穷次独立公平抛硬币」的同一性：Y = Σ X_k / 2^k。第一性原理是把 [0,1] 反复对半剖分——每读一位二进制位 X_k，就是做一次二分决策，把候选区间缩小一半。这与你在 6.006 学的二分搜索决策树完全同构：深度 k 的完全二叉树有 2^k 片叶子，每片叶子恰是一个长度 1/2^k 的区间 [(i−1)/2^k, i/2^k]，正是本解的构造。实分析课（Thomson / Rudin）里你会再次遇见这套二进制展开：除可数多个歧义点外表示唯一，而 P(Y = y) = 0 正对应「歧义点集合是零测集」。(b) 部分的优雅处在于「区间等长 ⟹ 等概率 ⟹ 联合分布是乘积」，从而推出各位独立。请把结论焊进记忆：均匀随机数 = 无穷个独立公平 bit——它在随机化算法与信息论（每 bit 恰 1 bit 熵）里是核心直觉。


> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 「the CDF of $Y$ is continuous and satisfies」一句之后应有 CDF 关系式，原图缺此行，无法复原具体式样，仅如实保留缺失说明。</span>

Since every number $y$ in $[0, 1]$ can be closely approximated by a number of the form $i/2^{k}$, we have $P(Y \le y) = y$, for every $y \in [0, 1]$, which establishes that $Y$ is uniform.

**(b)** As in part (a), we observe that every possible zero-one pattern for $X_1, \ldots, X_k$ is associated to one particular interval of the form $\left[(i-1)/2^{k},\, i/2^{k}\right]$ for $Y$. These intervals have equal length, and therefore have the same probability $1/2^{k}$, since $Y$ is uniform. This particular joint PMF for $X_1, \ldots, X_k$ corresponds to independent Bernoulli random variables with parameter $p = 1/2$.

> <span style="color:#7f8c8d;">源页在 part (b) 之后的空白处残留若干孤立圆点/`•` 等 OCR 碎片，系排版装饰，未译出。</span>

---

<span style="color:#2471a3;">**The Poisson Process（泊松过程）**</span> <span style="color:#7f8c8d;">—— 习题（源 OCR 页眉写作 `SECTION 7.2`，疑为 §6.2 之误读，见页首注）。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 8.**</span>

During rush hour, from 8 a.m. to 9 a.m., traffic accidents occur according to a Poisson process with a rate of 5 accidents per hour. Between 9 a.m. and 11 a.m., they occur as an independent Poisson process with a rate of 3 accidents per hour. What is the PMF of the total number of accidents between 8 a.m. and 11 a.m.?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 9.**</span>

An athletic facility has 5 tennis courts. Pairs of players arrive at the courts and use a court for an exponentially distributed time with mean 40 minutes. Suppose a pair of players arrives and finds all courts busy and $k$ other pairs waiting in queue. What is the expected waiting time to get a court?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 10.**</span>

A fisherman catches fish according to a Poisson process with rate $\lambda = 0.6$ per hour. The fisherman will keep fishing for two hours. If he has caught at least one fish, he quits. Otherwise, he continues until he catches at least one fish.

<!-- ===== PDF p339 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> —— 习题区（Problems，续）

> <span style="color:#7f8c8d;">页眉：The Bernoulli and Poisson Processes / Chap. 6 / 页印 330。本页延续上一页「泊松过程」一节的习题区。页首为上一页 **Problem 10**（渔夫捕鱼）的 (a)–(e) 各小问；随后依次为 **Problem 11 / 12 / 13 / 14**。各题题干均保持英文原题；本页各题均无星号、无解答。Problem 14 的题干在本页末尾起头，延续到下一页（书页 331）。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 10（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：渔夫以速率 $\lambda = 0.6$（每小时）的泊松过程（Poisson process）捕鱼，原计划钓两小时；若已钓到至少一条鱼则收竿，否则继续钓直到钓到至少一条鱼为止。本页给出该题的 (a)–(e) 各小问。</span>

(a) Find the probability that he stays for more than two hours.

(b) Find the probability that the total time he spends fishing is between two and five hours.

(c) Find the probability that he catches at least two fish.

(d) Find the expected number of fish that he catches.

(e) Find the expected total fishing time, given that he has been fishing for four hours.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 11**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中的速率符号在 OCR 中读作 `rate A per hour`，按泊松过程的标准记号复原为速率 $\lambda$，数值未改动。</span>

Customers depart from a bookstore according to a Poisson process with rate $\lambda$ per hour. Each customer buys a book with probability $p$, independent of everything else.

(a) Find the distribution of the time until the first sale of a book.

(b) Find the probability that no books are sold during a particular hour.

(c) Find the expected number of customers who buy a book during a particular hour.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 12**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中的均值符号在 OCR 中读作 `mean A`，按泊松随机变量的标准记号复原为均值 $\lambda$，数值未改动。</span>

A pizza parlor serves $n$ different types of pizza, and is visited by a number $K$ of customers in a given period of time, where $K$ is a Poisson random variable with mean $\lambda$. Each customer orders a single pizza, with all types of pizza being equally likely, independent of the number of other customers and the types of pizza they order. Find the expected number of different types of pizzas ordered.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 12 是「指示随机变量 + 线性期望」的教科书应用，也是 CLRS 期望分析的招牌套路（雇佣问题、生日悖论同款）。第一性原理：期望的线性性**不要求独立性**，所以「不同披萨种类数」这种复杂计数总能拆成「第 i 种是否被点」的指示变量之和：E[种类数] = Σ_{i=1}^n P(第 i 种被点至少一次)。每类被点的概率 = 1 − P(无人点它)。顾客数 K ~ Poisson(λ)，每位顾客选 i 的概率 1/n，于是 P(无人点 i) = E[(1−1/n)^K] = e^{−λ/n}（泊松 PMF 的母函数恒等式），答案 E = n(1 − e^{−λ/n}) 随之而来。「先把随机变量打成指示函数再逐项求期望」这个杠杆，在本章 §7.4 吸收时间的分析中依然主角——只是依赖结构从「独立」升级为「一阶依赖」，求和让位给线性方程组。


---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 13**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中两台发射机的速率在 OCR 中读作 `rates of AA and A B`，按上下文复原为 $\lambda_A$ 与 $\lambda_B$；消息字数的 PMF 在原页排版破碎（`2/6, if w = 1` 等行错位、`if w 3` 缺等号），按分段函数的标准式样重建，数值 $2/6$、$3/6$、$1/6$ 与 $0$ 均未改动。</span>

Transmitters A and B independently send messages to a single receiver in a Poisson manner, with rates of $\lambda_A$ and $\lambda_B$, respectively. All messages are so brief that we may assume that they occupy single points in time. The number of words in a message, regardless of the source that is transmitting it, is a random variable with PMF

```math
p_W(w) = \begin{cases}
2/6, & \text{if } w = 1,\\
3/6, & \text{if } w = 2,\\
1/6, & \text{if } w = 3,\\
0, & \text{otherwise,}
\end{cases}
```

and is independent of everything else.

(a) What is the probability that during an interval of duration $t$, a total of exactly nine messages will be received?

(b) Let $N$ be the total number of words received during an interval of duration $t$. Determine the expected value of $N$.

(c) Determine the PDF of the time from $t = 0$ until the receiver has received exactly eight three-word messages from transmitter A.

(d) What is the probability that exactly eight of the next twelve messages received will be from transmitter A?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 14**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干开头在 OCR 中读作 `Beginning at time t O.`，复原为 $t = 0$；页末另有一孤立字符 `=`，系扫描噪声，未译出。</span>

Beginning at time $t = 0$, we start using bulbs, one at a time, to illuminate a room. Bulbs are replaced immediately upon failure. Each new bulb is selected independently by an equally likely choice between a type-A bulb and a type-B bulb. The lifetime, $X$, of any particular bulb of a particular type is a random variable,

> <span style="color:#7f8c8d;">本页止于 Problem 14 题干中途（「… is a random variable,」），其后的题设（independent of everything else, with the following PDF: …）与 (a)–(j) 各小问延续到下一页（书页 331）。</span>


<!-- ===== PDF p340 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems）。页首（书页 331 顶端）续接上一页 **Problem 14**（灯具更换问题）的题目开头与其解答 (a)–(j)——该问题题设部分起于上一页书页 330，题目编号原文为 **Problem 14**。随后是独立的 **Problem 15**（服务站问题）。本题区题目题干均保持英文原题；带 `*` 的题目另有解析，本页两道题均无星号。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 14（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：从时刻 $t = 0$ 起开始用灯泡（bulbs）照亮房间，一次一个；灯泡一坏立即更换。每枚新灯泡以等可能方式独立地从 A 型灯泡与 B 型灯泡中选取。任一特定类型灯泡的寿命（lifetime）$X$ 是一个随机变量，与其余一切相互独立，其 PDF 如下。本页自 PDF 表示式起续，至 (a)–(j) 各子问结束。</span>

independent of everything else, with the following PDF:

for type-A bulbs:
```math
f_X(x) = \begin{cases}
e^{-x}, & \text{if } x \geq 0,\\
0, & \text{otherwise;}
\end{cases}
```

for type-B bulbs:
```math
f_X(x) = \begin{cases}
3e^{-3x}, & \text{if } x \geq 0,\\
0, & \text{otherwise.}
\end{cases}
```

(a) Find the expected time until the first failure.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 14 是一次「指数竞争」集训：A 型寿命 Exp(1)、B 型寿命 Exp(3)。两个关键事实构成全部武器：其一，min(X_A, X_B) 仍是指数分布，参数相加（此处即 1+3 = 4）；其二，指数分布无记忆——「已用 t 小时仍未坏」与「刚换新灯泡」在分布上毫无区别。后者正是第 6 章无记忆性在连续时间下的化身，也是第 7 章马尔可夫性质（未来只通过现在依赖过去）最亲密的先行者：指数变量把「已使用时长」这个连续记忆压缩成零记忆。做 (c)、(j) 时你会反复使用「无失败到 t ⟺ 首坏时刻 > t」的等价改写。提醒一点：第 (a) 问期望 1/4（由合并速率决定），与「谁先坏」的胜出率 P(A 先坏) = λ_A/(λ_A+λ_B) = 1/4、P(B 先坏) = 3/4 是两个不同的量，别混——前者是首坏时刻的均值，后者是竞争的「胜出概率」。


(b) Find the probability that there are no bulb failures before time $t$.

(c) Given that there are no failures until time $t$, determine the conditional probability that the first bulb used is a type-A bulb.

(d) Find the variance of the time until the first bulb failure.

(e) Find the probability that the 12th bulb failure is also the 4th type-A bulb failure.

(f) Up to and including the 12th bulb failure, what is the probability that a total of exactly 4 type-A bulbs have failed?

(g) Determine either the PDF or the transform associated with the time until the 12th bulb failure.

(h) Determine the probability that the total period of illumination provided by the first two type-B bulbs is longer than that provided by the first type-A bulb.

(i) Suppose the process terminates as soon as a total of exactly 12 bulb failures have occurred. Determine the expected value and variance of the total period of illumination provided by type-B bulbs while the process is in operation.

(j) Given that there are no failures until time $t$, find the expected value of the time until the first failure.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 15**</span>

A service station handles jobs of two types, A and B. (Multiple jobs can be processed simultaneously.) Arrivals of the two job types are independent Poisson processes with parameters $\lambda_A = 3$ and $\lambda_B = 4$ per minute, respectively. Type A jobs stay in the service station for exactly one minute. Each type B job stays in the service station for a random but integer amount of time which is geometrically distributed, with mean equal to 2, and independent of everything else. The service station started operating at some time in the remote past.

(a) What is the mean, variance, and PMF of the total number of jobs that arrive within a given three-minute interval?

(b) We are told that during a 10-minute interval, exactly 10 new jobs arrived. What is the probability that exactly 3 of them are of type A?

(c) At time 0, no job is present in the service station. What is the PMF of the number of type B jobs that arrive in the future, but before the first type A arrival?

(d) At time $t = 0$, there were exactly two type A jobs in the service station. What is the PDF of the time of the last (before time 0) type A arrival?

(e) At time 1, there was exactly one type B job in the service station. Find the distribution of the time until this type B job departs.

<!-- ===== PDF p341 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems），印页号 332（页眉 Chap. 6）。页首续接上一页 **Problem 14–15**，本页覆盖 **Problem 16–19**：Problem 16（U 形转弯等待）、Problem 17（动物园袋鼠）为普通题；Problem 18\*、19\* 为带星号题，其英文 Solution 保留原文。Problem 19\* 的 Solution 在本页末尾（"A much ..."处）中断，续接下一页。题目题干均保持英文原题，不翻译。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 16.**</span>

Each morning, as you pull out of your driveway, you would like to make a U-turn rather than drive around the block. Unfortunately, U-turns are illegal in your neighborhood, and police cars drive by according to a Poisson process with rate $\lambda$. You decide to make a U-turn once you see that the road has been clear of police cars for $T$ time units. Let $N$ be the number of police cars you see before you make the U-turn.

**(a)** Find $E[N]$.

**(b)** Find the conditional expectation of the time elapsed between police cars $n - 1$ and $n$, given that $N \ge n$.

**(c)** Find the expected time that you wait until you make the U-turn. *Hint:* Condition on $N$.

> <span style="color:#7f8c8d;">[原页此处 OCR 误读] 题干中的速率参数被 OCR 读作大写 A（`rate A`），按上下文恢复为 $\lambda$；(b) 中的条件记号 "$N \ge n$" 被 OCR 读作 `N � n`，已按原意修复。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 17.**</span>

A wombat in the San Diego zoo spends the day walking from a burrow to a food tray, eating, walking back to the burrow, resting, and repeating the cycle. The amount of time to walk from the burrow to the tray (and also from the tray to the burrow) is 20 secs. The amounts of time spent at the tray and resting are exponentially distributed with mean 30 secs. The wombat, with probability $1/3$, will momentarily stand still (for a negligibly small time) during a walk to or from the tray, with all times being equally likely (and independent of what happened in the past). A photographer arrives at a random time and will take a picture at the first time the wombat will stand still. What is the expected value of the length of time the photographer has to wait to snap the wombat's picture?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 18\*.**</span>

Consider a Poisson process. Given that a single arrival occurred in a given interval $[0, t)$, show that the PDF of the arrival time is uniform over $[0, t)$.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 18\* 是「泊松过程本质上是均匀散点」的第一见证：已知 [0,t) 恰有一次到达时，到达时刻竟均匀。推导只用条件概率除法：分子 = 「长度 l 的 [a,b] 内恰 1 次」×「其余长度 t−l 内恰 0 次」= (λl·e^{−λl})·e^{−λ(t−l)}；分母 = (λt·e^{−λt})。神奇之处在于所有指数因子相消，只剩长度比 l/t——「均匀」由此而来。第一性原理：泊松过程的「无记忆 + 独立增量」结构，使得「给定事件个数、位置均匀」成为必然。这个「计数条件化」模板——把事件写成互斥小区间的乘积再用比值——会反复出现：第 7 章的吸收概率、连续时间链的转移分析都用同一把刀。它也解释了随机涉入的观察者偏差：随机点落进大间隔的概率与间隔长度成正比（回顾 p337 Problem 5\*）。


<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

Consider an interval $[a, b] \subset [0, t]$ of length $l = b - a$. Let $T$ be the time of the first arrival, and let $A$ be the event that a single arrival occurred during $[0, t]$. We have

```math
P(T \in [a, b] \mid A) = \frac{P(T \in [a, b] \text{ and } A)}{P(A)}.
```

The numerator is equal to the probability $P(1, l)$ that the Poisson process has exactly one arrival during the length $l$ interval $[a, b]$, times the probability $P(0, t - l)$ that the process has zero arrivals during the set $[0, a) \cup (b, t]$, of total length $t - l$. Hence

```math
P(T \in [a, b] \mid A)
= \frac{P(1, l)\, P(0, t - l)}{P(1, t)}
= \frac{(\lambda l)\, e^{-\lambda l}\, e^{-\lambda (t - l)}}{(\lambda t)\, e^{-\lambda t}}
= \frac{1}{t},
```

which establishes that $T$ is uniformly distributed.

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] Problem 18\* Solution 的公式行在 OCR 中被纵向打散成竖排碎片（如 `pe L l )`、`P (O , t - l )`、`->.le->. ( t -l)`、`( A t ) e - ).. t`、`= t1 '`，其中的 $\lambda$ 被读作大写 A）。上面已按泊松过程标准公式 $P(1, l) = (\lambda l) e^{-\lambda l}$、$P(0, t - l) = e^{-\lambda (t - l)}$、$P(1, t) = (\lambda t) e^{-\lambda t}$ 重建，数值未改动；若需最严格原文请回查原书页 332。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 19\*.**</span>

**(a)** Let $X_1$ and $X_2$ be independent and exponentially distributed, with parameters $\lambda_1$ and $\lambda_2$, respectively. Find the expected value of $\max\{X_1, X_2\}$.

**(b)** Let $Y$ be exponentially distributed with parameter $\lambda_1$. Let $Z$ be Erlang of order 2 with parameter $\lambda_2$. Assume that $Y$ and $Z$ are independent. Find the expected value of $\max\{Y, Z\}$.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

A direct but tedious approach would be to find the PDF of the random variable of interest and then evaluate an integral to find its expectation. A much ...

> <span style="color:#7f8c8d;">[跨页续接] Problem 19\* 的英文 Solution 在本页止于 "A much ..."（"而远为省事得多的做法是…"），其后的推导（对 $\max\{X_1, X_2\}$ 利用条件期望 / 竞争指数分布技巧）续接下一页。</span>


<!-- ===== PDF p342 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems），印页号 333。页首续接上一页 **Problem 19\*** 的英文 Solution（上一页止于 "A much ..." 处），本页用「更简便的解法」（simpler solution）——把所涉随机变量解释为底层泊松过程（underlying Poisson processes）中的到达时刻——分 (a)、(b) 两部分完成 $\max\{X_1, X_2\}$ 与 $\max\{Y, Z\}$ 期望的推导。带 * 题的英文 Solution 保留原文。</span>

---

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Problem 19\* — Solution（解答，续）.**</span>

A much simpler solution is obtained by interpreting the random variables of interest in terms of underlying Poisson processes.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 19\* 展示了全书最省力的证明策略之一：不硬算 PDF 与积分，而是把随机变量「物化」为底层泊松过程的到达时刻（interpretation-based proof）。两个关键事实：独立指数的 min 仍指数且参数相加；「min 来自哪个过程」的概率按速率加权（λ_1/(λ_1+λ_2) 与 λ_2/(λ_1+λ_2)）。把 max{X₁,X₂} 拆成「等 min 的期望 + 条件等待」，竞争分解让一切一目了然。第一性原理：把抽象变量还原成过程对象，复杂的分布运算就变成直观的「谁先到、再等多久」。这个技巧在第 7 章是双重伏笔——合并（superposition）过程本身就是马尔可夫性质的到达版本，而「竞争 + 条件等待」正是 §7.5 连续时间马尔可夫链与排队论（如 M/M/1 离开时间）的标准动作。建议对比「直接积分」与「物化解释」两条路线的开销差，体会建模视角如何决定计算复杂度。


> <span style="color:#7f8c8d;">[跨页续接] 句首 "A much" 在上一页页末（page_341 止于 "A much ..."），本页首行 "simpler solution is obtained..." 与之衔接，此处把整句补全。</span>

**(a)** Consider two independent Poisson processes with rates $\lambda_1$ and $\lambda_2$, respectively. We interpret $X_1$ as the first arrival time in the first process, and $X_2$ as the first arrival time in the second process. Let $T = \min\{X_1, X_2\}$ be the first time when one of the processes registers an arrival. Let $S = \max\{X_1, X_2\} - T$ be the additional time until both have registered an arrival. Since the merged process is Poisson with rate $\lambda_1 + \lambda_2$, we have

```math
E[T] = \frac{1}{\lambda_1 + \lambda_2}.
```

Concerning $S$, there are two cases to consider.

**(i)** The first arrival comes from the first process; this happens with probability $\lambda_1/(\lambda_1 + \lambda_2)$. We then have to wait for an arrival from the second process, which takes $1/\lambda_2$ time on the average.

**(ii)** The first arrival comes from the second process; this happens with probability $\lambda_2/(\lambda_1 + \lambda_2)$. We then have to wait for an arrival from the first process, which takes $1/\lambda_1$ time on the average. Putting everything together, we obtain

```math
E[S] = \frac{\lambda_1}{\lambda_1 + \lambda_2}\cdot\frac{1}{\lambda_2}
     + \frac{\lambda_2}{\lambda_1 + \lambda_2}\cdot\frac{1}{\lambda_1}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 缺损] 原页在 (a) 的 "Putting everything together, we obtain" 之后直接跳到 (b)，$E[S]$ 的算式整体未进入 OCR；上式按上文 (i)(ii) 两种情形的平均等待时间加权重建，数值未改动。</span>

**(b)** Consider two independent Poisson processes with rates $\lambda_1$ and $\lambda_2$, respectively. We interpret $Y$ as the first arrival time in the first process, and $Z$ as the second arrival time in the second process. Let $T$ be the first time when one of the processes registers an arrival. Since the merged process is Poisson with rate $\lambda_1 + \lambda_2$, we have

```math
E[T] = \frac{1}{\lambda_1 + \lambda_2}.
```

There are two cases to consider.

**(i)** The arrival at time $T$ comes from the first process; this happens with probability $\lambda_1/(\lambda_1 + \lambda_2)$. In this case, we have to wait an additional time until the second process registers two arrivals. This additional time is Erlang of order 2, with parameter $\lambda_2$, and its expected value is $2/\lambda_2$.

**(ii)** The arrival at time $T$ comes from the second process; this happens with probability $\lambda_2/(\lambda_1 + \lambda_2)$. In this case, the additional time $S$ we have to wait is the time until each of the two processes registers an arrival. This is the maximum of two independent exponential random variables and, according to the result of part (a), we have

```math
E[S] = \frac{\lambda_1}{\lambda_1 + \lambda_2}\cdot\frac{1}{\lambda_2}
     + \frac{\lambda_2}{\lambda_1 + \lambda_2}\cdot\frac{1}{\lambda_1}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 缺损] (b)(ii) 中 "according to the result of part (a), we have" 之后紧跟的 $E[S]$ 算式同样未进入 OCR，此处按 part (a) 的结论补写。</span>

Putting everything together, we have

```math
E[\max\{Y, Z\}]
= \frac{\lambda_1}{\lambda_1 + \lambda_2}\left( E[T] + \frac{2}{\lambda_2} \right)
+ \frac{\lambda_2}{\lambda_1 + \lambda_2}\bigl( E[T] + E[S] \bigr),
```

where $E[S]$ is given by the previous formula.

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 末式在 OCR 中被拆成多行碎片，可辨识出 $E[\max\{Y,Z\}]$、$\lambda_1/(\lambda_1+\lambda_2)$、$2/\lambda_2$、$E[S]$、$1/(\lambda_1+\lambda_2)$ 等，"where $E[S]$ is given by the previous formula" 一句保留原文；上式按情形 (i)（概率 $\lambda_1/(\lambda_1+\lambda_2)$，附加期望 $E[T]+2/\lambda_2$）与情形 (ii)（概率 $\lambda_2/(\lambda_1+\lambda_2)$，附加期望 $E[T]+E[S]$）加权重建，其中 $E[T]=1/(\lambda_1+\lambda_2)$，数值未改动。</span>


<!-- ===== PDF p343 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems），印页号 334（页眉 Chap. 6）。上一页（印页号 333）刚续完 **Problem 19\*** 的 Solution，本页自 **Problem 20\*** 起，覆盖 **Problem 20–21**：两题均为带星号题，其英文 Solution 保留原文（仅「Solution（解答）」标签附中文）。Problem 21\* 的 Solution 在本页末尾中断，续接下一页。题目题干均保持英文原题，不翻译。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 20\*.**</span>

Let $Y_k$ be the time of the $k$th arrival in a Poisson process with rate $\lambda$. Show that for all $y > 0$,
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 20\* 的结论 Σ_k f_{Y_k}(y) = λ 是「密度叠加」思想的典范：把「时刻 y 处有到达」按「它是第几次到达」分解成互斥子事件再求和。两种证明殊途同归：代数版把 Erlang 密度代入，露出泊松 PMF 的和（总和为 1）；直观版把 [y, y+δ] 内到达的概率同时写成 Σ f_{Y_k}(y)·δ 与 f_Y(y)·δ，消去 δ 即得。第一性原理：一个事件的概率可按「它发生在哪个阶段」做条件化分解，只要分解互斥且穷尽。Problem 21\* 是同一把刀的变体：把两个泊松过程的「竞赛」（X₁(n) 与 X₂(m) 谁先到达）转化为合并过程里的伯努利试验——前 n+m−1 次合并到达中至少 n 次来自过程 1，立即得到二项求和。这个「竞赛 ⟺ 伯努利成功数」的等价，与你在 6.006/CLRS 见到的「比较转化为计数」是同一种思维体操。


```math
\sum_{k=1}^{\infty} f_{Y_k}(y) = \lambda .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干末的待证式在 OCR 中被打散成竖排碎片（残片含 `f`、`L Yk`、`k = l`、`tk - �)!` 等，速率为参数 $\lambda$ 处被 OCR 读作大写 A 的 `rate A`），上面按本页 Solution 的推导结论重建为 $\sum_{k=1}^{\infty} f_{Y_k}(y) = \lambda$（第 $k$ 次到达时刻 $Y_k$ 服从 Erlang 分布，其密度 $f_{Y_k}(y) = \lambda^k y^{k-1} e^{-\lambda y}/(k-1)!$，对 $k$ 求和即为速率 $\lambda$）。若需最严格原文请回查原书页 334。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.** We have

```math
\sum_{k=1}^{\infty} f_{Y_k}(y)
= \sum_{k=1}^{\infty} \frac{\lambda^{k} y^{k-1} e^{-\lambda y}}{(k-1)!}
= \lambda \sum_{m=0}^{\infty} \frac{(\lambda y)^{m} e^{-\lambda y}}{m!}
= \lambda \cdot 1
= \lambda ,
```

where we let $m = k - 1$. The last equality holds because the $(\lambda y)^m e^{-\lambda y} / m!$ terms are the values of a Poisson PMF with parameter $\lambda y$ and must therefore sum to $1$.

For a more intuitive derivation, let $\delta$ be a small positive number and consider the following events:

- $A_k$: the $k$th arrival occurs between $y$ and $y + \delta$; the probability of this event is $P(A_k) \approx f_{Y_k}(y)\,\delta$;
- $A$: an arrival occurs between $y$ and $y + \delta$; the probability of this event is $P(A) \approx f_Y(y)\,\delta$.

Suppose that $\delta$ is taken small enough so that the possibility of two or more arrivals during an interval of length $\delta$ can be ignored. With this approximation, the events $A_1, A_2, \ldots$ become disjoint, and their union is $A$. Therefore,

```math
\sum_{k=1}^{\infty} f_{Y_k}(y)\,\delta \approx \sum_{k=1}^{\infty} P(A_k) = P(A) \approx f_Y(y)\,\delta ,
```

and the desired result follows by canceling $\delta$ from both sides.

> <span style="color:#7f8c8d;">[原页此处 OCR 误读] 直观推导段中的 $\delta$ 被 OCR 全部误读为数字 8（`8`），如 `fYk (y)8`、`fy (y)8`，均按上下文恢复为 $f_{Y_k}(y)\,\delta$、$f_Y(y)\,\delta$；末尾求和式在 OCR 中仅余 `k= l`、`k=l` 与 `:::::: P(A )` 等碎片，已按 $P(A_k) \approx f_{Y_k}(y)\,\delta$、$P(A) \approx f_Y(y)\,\delta$ 的代入关系补全为上方链式等式。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 21\*.**</span>

Consider an experiment involving two independent Poisson processes with rates $\lambda_1$ and $\lambda_2$. Let $X_1(k)$ and $X_2(k)$ be the times of the $k$th arrival in the 1st and the 2nd process, respectively. Show that

```math
P\big(X_1(n) < X_2(m)\big)
= \sum_{k=n}^{n+m-1} \binom{n+m-1}{k}
\left( \frac{\lambda_1}{\lambda_1 + \lambda_2} \right)^{k}
\left( \frac{\lambda_2}{\lambda_1 + \lambda_2} \right)^{n+m-1-k}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 21\* 题干末的待证式在 OCR 中整段缺失（"Show that" 后直接跳到 Solution 首句），上式按本页 Solution 首句及下一页（印页号 335）的推导还原：把两个独立泊松过程合并为速率为 $\lambda_1 + \lambda_2$ 的泊松过程，任一次到达来自第一个过程的概率为 $\lambda_1/(\lambda_1 + \lambda_2)$、来自第二个过程的概率为 $\lambda_2/(\lambda_1 + \lambda_2)$；事件 $\{X_1(n) < X_2(m)\}$ 等价于前 $n + m - 1$ 次试验中至少 $n$ 次「成功」，故由二项 PMF 得上式。若需最严格原文请回查原书页 334。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.** Consider the merged Poisson process, which has rate $\lambda_1 + \lambda_2$. Each time there is an arrival in the merged process, this arrival comes from the first process ...

> <span style="color:#7f8c8d;">[跨页续接] Problem 21\* 的英文 Solution 在本页止于 "…this arrival comes from the first process"，其后的「成功（来自第一个过程）/ 失败（来自第二个过程）」伯努利解释与二项 PMF 求和推导续接下一页（印页号 335，PDF p344）。</span>


<!-- ===== PDF p344 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems），印页号 335（页眉 Chap. 6）。页首无新节标题、仅见 running header「Problems」，直接续接上一页（印页 334、文件页 343）**Problem 21.\*** 的英文 Solution（解答）末尾——该题比较两支相互独立 Poisson process 的到达时刻。随后依次为 **Problem 22.\***、**Problem 23.\***、**Problem 24.\***，前两道带 `*` 题的英文 Solution 保留原文；Problem 24.\* 的题干在本页末尾中断，续接下一页。题目题干均保持英文原题，不翻译。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 21.\*（续）—— 英文 Solution 收尾**</span>

> <span style="color:#7f8c8d;">承接上一页：Problem 21.\* 题设两支相互独立的 Poisson process，速率分别为 $\lambda_1$ 与 $\lambda_2$；记 $X_1(k)$、$X_2(k)$ 分别为第 $k$ 次到达在过程 1、过程 2 中发生的时刻。上一页已述：合并后的 Poisson process 速率为 $\lambda_1 + \lambda_2$，每次到达以概率 $\lambda_1/(\lambda_1 + \lambda_2)$ 来自过程 1。本页续接其英文 Solution 的收尾，推出所求概率。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）（续）.**

( "success" ) with probability $\lambda_1/(\lambda_1 + \lambda_2)$, and from the second process ( "failure" ) with probability $\lambda_2/(\lambda_1 + \lambda_2)$. Consider the situation after $n + m - 1$ arrivals. The number of arrivals from the first process is at least $n$ if and only if the number of arrivals from the second process is less than $m$, which happens if and only if the $n$th success occurs before the $m$th failure. Thus, the event $\{ X_1(n) < X_2(m) \}$ is the same as the event of having at least $n$ successes in the first $n + m - 1$ trials. Therefore, using the binomial PMF for the number of successes in a given number of trials, we have

```math
P\big(X_1(n) < X_2(m)\big)
= \sum_{k = n}^{n + m - 1} \binom{n + m - 1}{k}
\left( \frac{\lambda_1}{\lambda_1 + \lambda_2} \right)^{k}
\left( \frac{\lambda_2}{\lambda_1 + \lambda_2} \right)^{n + m - 1 - k}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原页在 “...we have” 之后的行间公式在 OCR 中丢失（仅余连字符 “-”）。上式按「前 $n + m - 1$ 次合并到达中至少 $n$ 次来自过程 1」的二项求和标准结论重建，与 Problem 21.\* 题干所求证式一致，未改动任何数值与概率结构；若需最严格原文请回查原书页 335。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 22.\***</span>

**Sum of a Random Number of Independent Bernoulli Random Variables.** Let $N, X_1, X_2, \ldots$ be independent random variables, where $N$ takes nonnegative integer values, and $X_1, X_2, \ldots$ are Bernoulli with parameter $p$. Let $Y = X_1 + \cdots + X_N$ for positive values of $N$ and let $Y = 0$ when $N = 0$.

( a ) Show that if $N$ is binomial with parameters $m$ and $q$, then $Y$ is binomial with parameters $m$ and $pq$.

( b ) Show that if $N$ is Poisson with parameter $\lambda$, then $Y$ is Poisson with parameter $\lambda p$.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

( a ) Consider splitting the Bernoulli process $X_1, X_2, \ldots$ by keeping successes with probability $q$ and discarding them with probability $1 - q$. Then $Y$ represents the number of successes in the split process during the first $m$ trials. Since the split process is Bernoulli with parameter $pq$, it follows that $Y$ is binomial with parameters $m$ and $pq$.

( b ) Consider splitting a Poisson process with parameter $\lambda$ by keeping arrivals with probability $p$ and discarding them with probability $1 - p$. Then $Y$ represents the number of arrivals in the split process during a unit interval. Since the split process is Poisson with parameter $\lambda p$, it follows that $Y$ is Poisson with parameter $\lambda p$.

> <span style="color:#7f8c8d;">[OCR 误读修正] 原文此处将分流保留概率误读为 $q$，与题干中 $X_i$ 为参数 $p$ 的伯努利变量以及结论 $\lambda p$ 相矛盾；按题意保留概率应为 $p$（(a) 中的 $q$ 是 $N$ 的二项参数，含义不同），此处改为 $p$。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 23.\***</span>

**Sum of a Geometric Number of Independent Exponential Random Variables.** Let $Y = X_1 + \cdots + X_N$, where the random variables $X_i$ are exponential with parameter $\lambda$, and $N$ is geometric with parameter $p$. Assume that the random variables $N, X_1, X_2, \ldots$ are independent. Show, without using transforms, that $Y$ is exponential with parameter $\lambda p$. **Hint:** Interpret the various random variables in terms of a split Poisson process.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

We derived this result in Chapter 4, using transforms, but we develop a more intuitive derivation here. We interpret the random variables $X_i$ and $N$ as follows. We view the times $X_1, X_1 + X_2$, etc. as the arrival times in a Poisson process with parameter $\lambda$. Each arrival is rejected with probability $1 - p$ and is accepted with probability $p$. We interpret $N$ as the number of arrivals until the first acceptance. The process of accepted arrivals is obtained by splitting a Poisson process and is therefore itself Poisson with parameter $\lambda p$. Note that $Y = X_1 + \cdots + X_N$ is the time of the first accepted arrival and is therefore exponential with parameter $\lambda p$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 24.\***</span>

**The Number of Poisson Arrivals During an Exponentially Distributed Interval.** Consider a Poisson process with parameter $\lambda$, and an independent ...
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 24\* 是本区最漂亮的「增广」（augmentation）技巧：把抽象的指数时长 T 具体化为另一个独立泊松过程的首次到达时刻。这一刀下去，「T 内原过程的到达数」就变成合并过程里「成功（新过程到达）之前来自原过程的到达次数」，几何分布呼之欲出——参数 1/μ 与 λ 的竞争一目了然。第一性原理：概率论里「把随机变量变成过程对象」是一种降维——你不再对着孤立的指数做积分，而是把它放进一台可运行的时间机器。这与 Problem 19\*/22\*/23\* 共享同一主题：伯努利 / 泊松过程的「分裂与合并」操作保持分布类型（几何、指数、泊松），并白送独立性。这套「操作保持性」的直觉，在第 7 章将以「状态图上的运算」形式重生——合并 / 分裂对应状态空间的折叠与展开。做题时请特别体会「把随机时长塞进过程」这半步，它是本书反复使用的隐藏杠杆。


> <span style="color:#7f8c8d;">[跨页续接] Problem 24.\* 的题干在本页止于 “…and an independent …”（意为“…以及一段与之相互独立、时长服从指数分布的区间…”），余下部分续接下一页（印页 336、文件页 345）。</span>


<!-- ===== PDF p345 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems），印页号 336（页眉 Chap. 6）。页首无新节标题，直接续接上一页（印页 335、文件页 344）**Problem 24.\*** 的英文 Solution（解答）——该题求「参数为 $1/\mu$ 的指数时长 $T$ 内泊松到达数的 PMF」。随后依次为 **Problem 25.\*** 与 **Problem 26.\***，均为带星号（\*）题，前者的英文 Solution 保留原文；Problem 26.\* 的题干在本页末尾中断，续接下一页。题目题干均保持英文原题，不翻译。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 24.\*（续）—— 英文题干收尾**</span>

> <span style="color:#7f8c8d;">承接上一页：Problem 24.\*（The Number of Poisson Arrivals During an Exponentially Distributed Interval）题干在上一页止于 "…and an independent …"，本页补回英文原题末尾句；题设一个速率为 $\lambda$ 的 Poisson process，以及一段与之相互独立、参数为 $1/\mu$ 的指数随机变量 $T$，求时间区间 $[0, T]$ 内泊松到达数的 PMF。随后给出其英文 Solution：把 $T$ 看作一个新合并泊松过程里的首次到达时刻，用几何分布给出到达数 $L$ 的 PMF。</span>

random variable $T$, which is exponential with parameter $1/\mu$. Find the PMF of the number of Poisson arrivals during the time interval $[0, T]$.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

Let us view $T$ as the first arrival time in a new, independent, Poisson process with parameter $1/\mu$, and merge this process with the original Poisson process. Each arrival in the merged process comes from the original Poisson process with probability $\lambda/(\lambda + 1/\mu)$, independent of other arrivals. If we view each arrival in the merged process as a trial, and an arrival from the new process as a success, we note that the number $K$ of trials/arrivals until the first success has a geometric PMF, of the form

```math
p_K(k) = \frac{1/\mu}{\lambda + 1/\mu} \left( \frac{\lambda}{\lambda + 1/\mu} \right)^{k - 1}, \qquad k = 1, 2, \ldots .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] $p_K(k)$ 的分式与指数在 OCR 中被拆散到多行（OCR 读作 "( 1/ ).. + 1/ ) ( ).. ) k - l ).. + 1/"），此处按几何分布标准形式合并重建为规范 LaTeX；$\lambda$ 与 $1/\mu$ 的相对位置以分式结构还原，未臆造数值。</span>

Now the number $L$ of arrivals from the original Poisson process until the first "success" is equal to $K - 1$, and its PMF is

```math
p_L(l) = p_K(l + 1) = \frac{1/\mu}{\lambda + 1/\mu} \left( \frac{\lambda}{\lambda + 1/\mu} \right)^{l}, \qquad l = 0, 1, \ldots .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] $p_L(l) = p_K(l+1)$ 一式的分式与指数在 OCR 中损坏严重（OCR 读作 "p d l ) = PK ( l + 1 ) = ( ).. : 1/ )( ).. I/Y"，乱码较多），此处按 $p_K$ 的几何 PMF 代入 $k = l+1$ 重建，未改动任何数值。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 25.\***</span>

**An infinite server queue.** We consider a queueing system with an infinite number of servers, in which customers arrive according to a Poisson process with rate $\lambda$. The $i$th customer stays in the system for a random amount of time, denoted by $X_i$. We assume that the random variables $X_i$ are independent identically distributed, and also independent from the arrival process. We also assume, for simplicity, that the $X_i$ take integer values in the range $1, 2, \ldots, n$, with given probabilities. Find the PMF of $N_t$, the number of customers in the system at time $t$.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 25\*（无限服务台队列）是「分裂–合并」思想的又一次胜利，也是排队论 M/G/∞ 的核心结论。策略：按服务时间 k 把到达过程分裂成 n 个独立泊松子过程（速率 λp_k），每个子过程只负责「服务时间为 k」的顾客。关键观察：t 时刻仍在系统中的 k 型顾客 = 在 [t−k, t] 内到达的 k 型顾客（早来已走），所以 N_{tk} ~ Poisson(λkp_k)；独立泊松之和仍为泊松、参数相加，即得 N_t ~ Poisson(λE[X₁])。第一性原理：把复杂计数按类型分解成独立子计数，每个子计数因「窗口化」变成简单泊松——「线性叠加 + 独立性」是概率论最常用的杠杆。跨课程提醒：N_t 的公式与排队论的 Little 定律（L = λW）同源——等你学完 §7.5 连续时间链回头再看，会发现它只是「稳态」思想的一个具体投影。


<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

Let us refer to those customers $i$ whose service time $X_i$ is equal to $k$ as "type-$k$" customers. We view the overall arrival process as the merging of $n$ Poisson subprocesses; the $k$th subprocess corresponds to arrivals of type-$k$ customers, is independent of the other arrival subprocesses, and has rate $\lambda p_k$, where $p_k = P(X_i = k)$. Let $N_{tk}$ be the number of type-$k$ customers in the system at time $t$. Thus,

```math
N_t = \sum_{k = 1}^{n} N_{tk},
```

and the random variables $N_{tk}$ are independent.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中 $N_t = \sum_{k=1}^{n} N_{tk}$ 在 OCR 中丢失（原页仅余末句「and the random variables Ntk are independent」），此处按上下文自然补全，不臆造数值。</span>

We now determine the PMF of $N_{tk}$. A type-$k$ customer is in the system at time $t$ if and only if that customer arrived between times $t - k$ and $t$. Thus, $N_{tk}$ has a Poisson PMF with mean $\lambda k p_k$. Since the sum of independent Poisson random variables is Poisson, it follows that $N_t$ has a Poisson PMF with parameter

```math
E[N_t] = \lambda \sum_{k = 1}^{n} k p_k = \lambda E[X_1].
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式中求和号 $\sum_{k=1}^{n} k p_k$ 与 $E[X_1]$ 的下标在 OCR 中被拆散（OCR 将求和读作 "L kPk"、将 $E[X_1]$ 读作 "E[Xd"），此处按原意合并重建为规范 LaTeX，未改动任何数值。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 26.\***</span>

**Independence of Poisson processes obtained by splitting.** Consider a Poisson process whose arrivals are split, with each arrival assigned to one of two subprocesses by tossing an independent coin with success probability $p$. In ...

> <span style="color:#7f8c8d;">[跨页续接] Problem 26.\* 的题干在本页止于「…In ...」（意为「…在…情形下/用某种方式…」），余下部分续接下一页（印页 337、文件页 346）。</span>


<!-- ===== PDF p346 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems），印页号 337（页眉 Problems）。页首无新节标题、仅见 running header「Problems」，直接续接上一页（印页 336、文件页 345）**Problem 26.\*** 的题干末尾——上一页止于 “In …”，本页补全为 “In Example 6.13, it was established that … Show that the two subprocesses are independent.”，随后给出该题的完整英文 Solution（解答）。之后依次为 **Problem 27.\***，题干与英文 Solution 均保持英文原题；其 Solution 在本页末尾中断，续接下一页（印页 338、文件页 347）。</span>
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 26\* 给出一个值得收藏的证明策略模板——等价机制法。直接证「抛硬币分裂出的两个子过程独立」并不顺手，于是构造一个统计相同但独立性显然的机制：先把两个独立泊松 P₁（速率 pλ）、P₂（速率 (1−p)λ）合并成 P，再按「每次到达来自 P₁ 还是 P₂」给 P 的到达打标签。标签来自原两个独立过程的身份，独立性免费到手；随后只需验证「打标签」与「独立抛硬币 p」是同一套统计机制——两种分裂都满足「每次到达独立地以概率 p 归入子过程 1」。第一性原理：概率结论由「统计机制」决定，与「实现细节」无关，正如离散数学里的同构、CSAPP 里的抽象层次。模板化表述：要证 A ⟹ B，先找 C 使 A ⟹ C 显然、C ⟹ B 容易。这个模板在第 7 章证明链的各种性质时会反复复用。


---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 26.\*（续）—— 题干末尾 + 英文 Solution**</span>

> <span style="color:#7f8c8d;">承接上一页：Problem 26.\* 题设一个 Poisson process 的每次到达以独立抛硬币（成功概率 $p$）分配到两个子过程之一。上一页（印页 336）止于题干 “In …”，本页续接题干末两句，并给出该题的完整英文 Solution：先构造与题设统计等价但形式不同的分裂机制，再证明两种分裂机制统计相同。</span>

In **Example 6.13**, it was established that each of the subprocesses is a Poisson process. Show that the two subprocesses are independent.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

Let us start with two independent Poisson processes $P_1$ and $P_2$, with rates $p\lambda$ and $(1 - p)\lambda$, respectively. We merge the two processes and obtain a Poisson process $P$ with rate $\lambda$. We now split the process $P$ into two new subprocesses $P'_1$ and $P'_2$, according to the following rule: an arrival is assigned to subprocess $P'_1$ (respectively, $P'_2$) if and only if that arrival corresponds to an arrival from subprocess $P_1$ (respectively, $P_2$). Clearly, the two new subprocesses $P'_1$ and $P'_2$ are independent, since they are identical to the original subprocesses $P_1$ and $P_2$. However, $P'_1$ and $P'_2$ were generated by a splitting mechanism that looks different than the one in the problem statement. We will now verify that the new splitting mechanism considered here is statistically identical to the one in the problem statement. It will then follow that the subprocesses constructed in the problem statement have the same statistical properties as $P'_1$ and $P'_2$, and are also independent.

So, let us consider the above described splitting mechanism. Given that $P$ had an arrival at time $t$, this was due to either an arrival in $P_1$ (with probability $p$), or to an arrival in $P_2$ (probability $1 - p$). Therefore, the arrival to $P$ is assigned to $P'_1$ or $P'_2$ with probabilities $p$ and $1 - p$, respectively, exactly as in the splitting procedure described in the problem statement. Consider now the $k$th arrival in $P$ and let $L_k$ be the event that this arrival originated from subprocess $P_1$; this is the same as the event that the $k$th arrival is assigned to subprocess $P'_1$. As explained in the context of **Example 6.14**, the events $L_k$ are independent. Thus, the assignments of arrivals to the subprocesses $P'_1$ and $P'_2$ are independent for different arrivals, which is the other requirement of the splitting mechanism described in the problem statement.

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 原页 OCR 把 $\lambda$ 误识作 “>.”，$P_1/P_2$ 的下标误识作 “PI/P2”，分裂所得子过程记号 “P�” 无法辨认，此处按 Problem 26.\* 的标准记号重建为 $P'_1$、$P'_2$（其速率分别为 $p\lambda$ 与 $(1-p)\lambda$）；英文文本本身完整可读，未改动任何数值与语义。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 27.\***</span>

**Random incidence in an Erlang arrival process.** Consider an arrival process in which the interarrival times are independent Erlang random variables of order 2, with mean $2/\lambda$. Assume that the arrival process has been ongoing for a very long time. An external observer arrives at a given time $t$. Find the PDF of the length of the interarrival interval that contains $t$.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.**

We view the Erlang arrival process in the problem statement as part of a Poisson process with rate $\lambda$. In particular, the Erlang arrival process registers an arrival once every two arrivals of the Poisson process. For concreteness, let us say that the Erlang process arrivals correspond to even-numbered arrivals in the Poisson process. Let $Y_k$ be the time of the $k$th arrival in the Poisson process.

Let $K$ be such that $Y_K \le t < Y_{K+1}$. By the discussion of random incidence in Poisson processes in the text, we have that $Y_{K+1} - Y_K$ is Erlang of order 2. The interarrival interval for the Erlang process considered in this problem is of the form $[Y_K, Y_{K+2}]$ or $[Y_{K-1}, Y_{K+1}]$, depending on whether $K$ is even or odd, respectively. In the first case, the interarrival interval in the Erlang process is of the form $(Y_{K+1} - Y_K) + (Y_{K+2} - Y_{K+1})$. We claim that $Y_{K+2} - Y_{K+1}$ is exponential with parameter $\lambda$ and independent of $Y_{K+1} - Y_K$. Indeed, an observer who arrives at time $t$ and notices that $K$ is even, must first wait until the time $Y_{K+1}$ of the next Poisson arrival. At that time, the Poisson process starts afresh, and the time $Y_{K+2} - Y_{K+1}$ until the next Poisson arrival is independent of the past (hence, independent of $Y_{K+1} - Y_K$) and has an exponential distribution with parameter $\lambda$, as claimed. This establishes that, conditioned on $K$ being even, the interarrival interval length $Y_{K+2} - Y_K$ of the Erlang process is Erlang of order 3 (since it is the sum of an exponential random variable ...

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 原页 OCR 把 $\lambda$ 误识作 “>.”、$\le$ 误识作 “$” 符号，且把 $Y_{K+1}$ 之类的下标/上标拆散（如 “YK + I”）；以上英文 Solution 系按原文语义重建，数值与分布参数（$2/\lambda$、阶数 2、参数 $\lambda$）均未改动。另注：Problem 27.\* 的英文 Solution 在本页止于 “…(since it is the sum of an exponential random variable …”，余下部分续接下一页（印页 338、文件页 347）。</span>


<!-- ===== PDF p347 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">本页位于第 6 章习题区（Problems），印页号 338（页眉 Chap. 6）。页首无新节标题、无新 Problem 编号，直接续接上一页（印页 337、文件页 346）**Problem 27.\***（Random incidence in an Erlang arrival process）的英文 Solution（解答）末尾。题目题干保持英文原题，带 `*` 题的 Solution 保持英文原文，仅标签标注中文。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 27.\*（续）—— 英文 Solution 收尾**</span>

> <span style="color:#7f8c8d;">承接上一页：上一页的 Solution 已证明——把爱尔朗到达过程视为速率为 $\lambda$ 的泊松过程（Poisson process）每两次到达登记一次所得（爱尔朗过程到达对应泊松过程的偶数编号到达），设 $Y_k$ 为泊松过程中第 $k$ 次到达的时刻，令 $K$ 满足 $Y_K \le t < Y_{K+1}$。已证当 $K$ 为偶数时，爱尔朗过程的到达间隔 $[Y_K, Y_{K+2}]$ 的长度 $Y_{K+2} - Y_K$ 为三阶爱尔朗分布（Erlang of order 3），因为它是「一个指数随机变量与一个二阶爱尔朗随机变量之和」。本页续接其后，以对称论证收尾该 Solution。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）（续）.**

...and a random variable which is Erlang of order 2). By a symmetrical argument, if we condition on $K$ being odd, the conditional PDF of the interarrival interval length $Y_{K+1} - Y_{K-1}$ of the Erlang process is again the same. Since the conditional PDF of the length of the interarrival interval that contains $t$ is Erlang of order 3, for every conditioning event, it follows that the unconditional PDF is also Erlang of order 3.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 27\* 的收尾展示了一个高频模板——条件化再消去：对 K 偶、K 奇两种情形分别算出「含 t 的到达间隔长度」的条件 PDF，得到同一个三阶 Erlang 分布，于是无条件 PDF 也必为三阶 Erlang。第一性原理：若某量的条件分布不随条件变化，无条件分布就等于这个共同分布——「条件无关 ⟹ 无条件相同」是最便宜的消去。本题同时是随机涉入（random incidence）的连续版：Erlang(均值 2/λ) 到达过程在普通观察下间隔均值是 2/λ，而外部观察者 t 随机落点看到的间隔均值是 3/λ——长了 1.5 倍。这个「观察者偏差」与 p337 Problem 5\* 的离散版遥相呼应，是排队论 PASTA 性质与网络测量的种子。理解「随机点被长间隔捕获的概率与长度成正比」，你就能直觉地解释为何等待时间总比平均更久。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 原句 "the interarrival interval length YK +1 - YK - 1" 中两个下标在 OCR 中碎裂为 "YK +1 - YK - 1"。按上一页（印页 337）所述区间形式 $[Y_{K-1}, Y_{K+1}]$（当 $K$ 为奇数时爱尔朗过程的到达间隔），此处重建为 $Y_{K+1} - Y_{K-1}$；页首 "and a random variable which is Erlang of order 2)" 系上一页英文 Solution 句子的延续，本页按「（续）」处理。</span>


<!-- ===== PDF p348 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

> <span style="color:#7f8c8d;">本页为第 7 章（Markov Chains）的**开篇章首页**，仅含章标题 + 章内目录（Contents），正文从目录之后的 340 页起。文件命名页为 p348；页眉「7」为章号，页脚印刷页号 339 为原书印刷页码，与文件页号不同，目录中给出的页码亦为原书印刷页号。</span>

**目录（Contents）**

- <span style="color:#c0392b;">**7.1　离散时间马尔可夫链（Discrete-Time Markov Chains）**</span> —— p.340
- <span style="color:#c0392b;">**7.2　状态的分类（Classification of States）**</span> —— p.346
- <span style="color:#c0392b;">**7.3　稳态行为（Steady-State Behavior）**</span> —— p.352
- <span style="color:#c0392b;">**7.4　吸收概率与吸收时间的期望（Absorption Probabilities and Expected Time to Absorption）**</span> —— p.362
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 用目录给第 7 章画一张学习地图。7.1 定义模型（状态、转移概率、马尔可夫性质）——本章的「语法」；7.2 状态分类（常返 / 暂态 / 周期 / 不可约）——把状态空间看作有向图，6.042J 的强连通、可达性在此复活，回答「链会到哪里」；7.3 稳态行为——回答「长期看分布如何」，数学上是转移矩阵幂的极限，直通 Strang / 18.065 的马尔可夫矩阵；7.4 吸收概率与吸收时间——回答「何时终止、终止在哪」，首次需要解线性方程组（新武器）；7.5 连续时间链——把「每步」换成「指数停留时钟」。与前六章的断裂处要特别留意：此前总假设试验独立或无记忆，第 7 章第一次允许「依赖」，但用「一阶依赖 + 有限状态 + 时齐」三个限制换回可计算性。这个「先窄化模型再逐层放开」的元方法，是你之后学随机过程、排队论、MCMC 都要沿用的路线图。

- <span style="color:#c0392b;">**7.5　连续时间马尔可夫链（Continuous-Time Markov Chains）**</span> —— p.369
- <span style="color:#c0392b;">**7.6　小结与讨论（Summary and Discussion）**</span> —— p.378
- <span style="color:#c0392b;">**习题（Problems）**</span> —— p.380

> <span style="color:#7f8c8d;">[OCR 说明] 本页 OCR 基本完整，仅略有碎裂：7.1 小节号被识别为 "7. 1"（数字与小数点间多一空格）；各小节标题与 Problems 条目之间的省略号引导线（dot leaders）散乱（OCR 中表现为孤立的 "… / · / " 行）；以上均按表意重建，各节标题及对应印刷页码（340 / 346 / 352 / 362 / 369 / 378 / 380）未作改动。</span>


<!-- ===== PDF p349 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

> <span style="color:#7f8c8d;">本页为第 7 章开篇（原书印刷页 340），承接上一章末的泊松过程；页首无「续」标题，系全新一章的引言，随后进入 §7.1 离散时间马尔可夫链的定义（本页尚无 Example 7.1，该例在后续页）。</span>

前一章所研究的伯努利过程（Bernoulli process）与泊松过程（Poisson process）具有无记忆性（memoryless），也就是说，未来并不依赖于过去：新的"成功"（successes）或"到达"（arrivals）的发生并不依赖于该过程过去的历史。

本章考察的是这样的过程：未来依赖于过去所发生的事，并在一定程度上可以由之作出预测。

我们重点放在这样的模型上：过去对未来的影响被概括为一个状态（state），它按照给定的概率随时间演变。我们把讨论限制在状态只能取有限个数值、且其变化概率不依赖于变化时刻的模型上。我们希望分析状态取值序列的概率性质。

本章所述这类模型的适用范围极其广泛。它几乎涵盖任何随时间演化且涉及不确定性的动力系统，只要该系统的状态定义得当。这类系统广泛出现在许多领域中，例如通信（communications）、自动控制（automatic control）、信号处理（signal processing）、制造（manufacturing）、经济学（economics）与运筹学（operations research）等。

<span style="color:#c0392b;">**§7.1　离散时间马尔可夫链（Discrete-Time Markov Chains）**</span>

我们首先考虑离散时间马尔可夫链（discrete-time Markov chain）：在这类链中，状态在一些离散的时刻发生变化，这些时刻用整数变量 $n$ 编号。在每一时刻 $n$，链的状态记作 $X_n$，它属于可能状态的有限集合 $S$，该集合称为状态空间（state space）。不失一般性，且除非另有说明，我们将假定 $S = \{1, \ldots, m\}$，其中 $m$ 为某个正整数。

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**[定义] 转移概率（Transition Probabilities）**</span>

马尔可夫链用其转移概率（transition probabilities）$p_{ij}$ 来描述：每当状态恰为 $i$ 时，下一状态等于 $j$ 的概率即为 $p_{ij}$。数学上，

```math
p_{ij} = P(X_{n+1} = j \mid X_n = i), \qquad i,\, j \in S.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把 m×m 转移概率矩阵想成一张加权邻接矩阵——这是 6.042J 图论的直系延续：P_{ij} > 0 ⟺ 从节点 i 到节点 j 有一条弧，权重即转移概率。你在离散数学学过的邻接矩阵幂给出「路径计数」((A^k)_{ij} = i 到 j 的 k 步路径数)；这里完全平行，(P^k)_{ij} = P(X_{n+k}=j | X_n=i) 是 k 步转移概率——把「计数」换成「加权概率和」，一切照旧。每行和为 1 表示从每个状态出发的概率质量守恒，对应图中每个节点加权出度为 1。对齐 Strang / 18.065：本书用行随机（每行和为 1），Strang 讲 PageRank 用列随机（每列和为 1），两者互为转置，注意别混。特征值 1 总有对应的平稳分布（左特征向量），第二大特征值控制收敛速度——这正是 §7.3 稳态的数学入口。用矩阵幂 P^k 的极限行为去预览第 7 章后半段，是 18.065 眼光的最短路径。

```

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**[定义] 马尔可夫性质（The Markov Property）**</span>

马尔可夫链背后的关键假设是：无论过去发生过什么、也无论状态 $i$ 是如何达到的，只要状态 $i$ 被访问到，转移概率 $p_{ij}$ 就始终适用。数学上，我们假定如下马尔可夫性质（Markov property）：

```math
P(X_{n+1} = j \mid X_n = i,\; X_{n-1} = i_{n-1},\; \ldots,\; X_0 = i_0)
= P(X_{n+1} = j \mid X_n = i)
= p_{ij},
```

它对所有时刻 $n$、所有状态 $i, j \in S$ 以及所有可能的前期状态序列 $i_0, \ldots, i_{n-1}$ 均成立。因此，下一状态 $X_{n+1}$ 的概率规律只通过当前状态 $X_n$ 的取值来依赖过去。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这句话就是马尔可夫性质的全部精髓，值得拆到骨头。数学上它说：给定 X_n = i 时，整个过去 (X₀,…,X_{n−1}) 与未来条件独立——过去不再是证据，只有 X_n 是充分摘要。对照第 6 章：伯努利 / 泊松过程「完全不依赖过去」（无记忆、0 阶），马尔可夫链「只通过现在依赖过去」（1 阶），前者是后者的退化情形。你已在 CSAPP 见过这个思想——有限状态机的状态正是「为丢弃无关过去而设计的封装」；CLRS 的 KMP 匹配自动机（按失配 fail 指针转移）就是一台马尔可夫链的活标本。历史坐标：Andrey Markov（1856–1922），圣彼得堡学派、Chebyshev 的学生，1906 年在喀山数理学会刊发表《大数定律向相互依赖量的推广》，首次证明「独立性并非必要、只要一阶依赖」大数定律仍成立。最初的动机竟是分析普希金诗文中元音 / 辅音的依赖结构——一个文学问题催生了现代随机过程理论，这个起源值得记住。


当然，转移概率 $p_{ij}$ 必须非负，并且对每个 $i$，其和为 1：

```math
\sum_{j=1}^{m} p_{ij} = 1, \qquad \forall\, i.
```


<!-- ===== PDF p350 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span> — §7.1（续）

<span style="color:#c0392b;">**§7.1　离散时间马尔可夫链（Discrete-Time Markov Chains）**</span> <span style="color:#7f8c8d;">（Sec. 7.1，书页 341；本页续接上一页 §7.1 正文关于自转移的讨论，依次给出马尔可夫模型的规范刻画、转移概率矩阵与转移概率图，并以 Example 7.1 的题面开头。）</span>

> <span style="color:#7f8c8d;">承接上一页：§7.1 已引入转移概率 $p_{ij}$ 与马尔可夫性质（Markov property）。本页页首继续讲解「自转移」（self-transition）概念，随后给出马尔可夫模型（Markov model）的规范刻画、转移概率矩阵（transition probability matrix）与转移概率图（transition probability graph），并以 **Example 7.1**（Alice 例题）的题面结束本页。</span>

我们通常允许概率 $P_{ii}$ 为正（positive），此时下一个状态（state）有可能与当前状态相同。即便状态并未改变，我们仍把这视为一种特殊类型的状态转移（state transition）——即「自转移」（self-transition）。

<span style="color:#c0392b;">**马尔可夫模型的刻画（Specification of Markov Models）**</span>

一个马尔可夫链（Markov chain）模型由识别（identify）以下三要素来刻画：
- (a) 状态集合（set of states）$S = \{1, \ldots, m\}$；
- (b) 可能的转移（transitions）集合，即满足 $P_{ij} > 0$ 的那些状态对 $(i, j)$；
- (c) 那些为正的 $P_{ij}$ 的数值。

由该模型所刻画的马尔可夫链是一个取值于 $S$ 的随机变量序列 $X_0, X_1, X_2, \ldots$，它满足

```math
P(X_{n+1} = j \mid X_n = i,\; X_{n-1} = i_{n-1},\; \ldots,\; X_0 = i_0) = P_{ij},
```

它对所有时刻 $n$、所有状态 $i, j \in S$ 以及所有可能的先前状态序列 $i_0, \ldots, i_{n-1}$ 均成立。

马尔可夫链模型的所有要素都可以编码进一个转移概率矩阵（transition probability matrix）中——它只是一个二维数组（two-dimensional array），其第 $i$ 行第 $j$ 列的元素就是 $P_{ij}$：

```math
\begin{pmatrix}
P_{11} & P_{12} & \cdots & P_{1m}\\
P_{21} & P_{22} & \cdots & P_{2m}\\
\vdots & \vdots & \ddots & \vdots\\
P_{m1} & P_{m2} & \cdots & P_{mm}
\end{pmatrix}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式中的转移概率矩阵在 OCR 中被拆散成逐元素竖排（如「Pl l」「P2 1」「Plm」「Pmm」等），此处按「第 $i$ 行第 $j$ 列元素为 $P_{ij}$」的定义规范重排为 $m \times m$ 矩阵，元素本身未改动。</span>

把模型布局成所谓的转移概率图（transition probability graph）也很有帮助：其节点（nodes）是状态，其弧（arcs）是可能的转移。把 $P_{ij}$ 的数值记录在相应弧的旁边，即可将整个模型可视化（visualize），从而使其一些主要性质一目了然。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 转移概率图 = 一张带权有向图：节点是状态，弧是允许的转移，权重是 P_{ij}。这与 CSAPP 的有限状态机（FSM）形成完美对照：FSM 是确定性的（状态 + 输入 ⟹ 唯一后继），马尔可夫链是概率性 FSM（状态 ⟹ 一个概率分布）。两者的共同灵魂是「状态封装历史」——无论过去走过多长的路，未来只由当前状态决定，这正是你在 CSAPP 数字电路（时序逻辑）、正则表达式匹配器里反复见过的抽象。自转移（P_{ii} > 0）看似无趣实则有深意：它强调「时刻」推进了而「状态」未必改变，对应 FSM 里「留在原状态等待下一个时钟沿」。从图论看（6.042J），每个节点的加权出度和为 1（概率质量守恒），强连通分量、可达性这些老朋友将在 §7.2 状态分类中直接登场。把「马尔可夫链 = 概率版 FSM + 加权有向图」的三层身份刻进脑海，读第 7 章会一路顺畅。


<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 7.1（Alice 的概率课）**</span>

Alice 正在上一门概率课（probability class），在每一周，她要么跟得上进度（up-to-date），要么可能已落后（fallen behind）。如果某一周她跟得上进度，那么下一周她跟得上（或落后）的概率为 $0.8$（或 $0.2$）。如果某一周她已落后，那么下一周她跟得上（或落后）的概率为 $0.6$（或 $0.4$）。我们假定这些概率并不依赖于她前几周是跟得上还是落后，因此该问题具有典型的马尔可夫链特征（Markov chain character）——未来对过去的依赖仅通过现在（the future depends on the past only through the present）。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 7.1 是整章最简但最完整的运行例子，值得现在就用手头的线性代数武器解剖它。转移矩阵 P = [[0.8, 0.2], [0.6, 0.4]]（行随机）。用 Strang / 18.065 的矩阵幂语言：P^k 的行收敛到平稳分布 π = (0.75, 0.25)——验证 πP = π：0.75·0.8 + 0.25·0.6 = 0.75 成立。特征值谱是 {1, 0.2}：特征值 1 对应平稳分布（Perron 根），第二大特征值 0.2 决定收敛速率——每步误差缩为 0.2 倍，约 10 步后误差小于百万分之一。这就是 §7.3 稳态与收敛速度定理的直观预览：链的长期行为由矩阵幂的极限刻画，「多快到达稳态」由第二大特征值控制。对 Alice 而言，「本周状态」就是预测下周的全部信息——她不必记得前几周，这正是马尔可夫性质的活标本。把这道两状态例题当作你检验后面所有定理的试验田，收益最大。


> <span style="color:#7f8c8d;">本页在陈述完 Example 7.1 的题面后结束；该例的转移概率图与后续求解延续到下一页。</span>


