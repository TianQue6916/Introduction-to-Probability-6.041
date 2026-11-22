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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把定义拆成三段：说「$X_n \to a$ with probability 1」，指的是存在一个 event（事件）$N$，$P(N)=0$，且对每个 $\omega \notin N$ 都有数列 $X_n(\omega) \to a$。量词顺序是「存在 $N$、对所有 $\omega \notin N$」，一旦固定就必须一次性对所有不落在其中的样本点负责；若写成「对每个 $\omega$ 存在各自的 $N$」，那就退化成逐点收敛的废话，而逐点收敛恰恰推不出 almost surely（几乎必然）。判定标准仍然是实分析里那套 $\varepsilon$–$N$：对每个 $\varepsilon>0$ 存在 $k$，使所有 $n \ge k$ 满足 $|X_n(\omega)-a|<\varepsilon$。
>
> 为什么这是合法 event（事件）而不是口语。把 $\varepsilon$ 只取 $1/m$（可数多个），就有 $\{X_n \to a\} = \bigcap_{m \ge 1} \bigcup_{k \ge 1} \bigcap_{n \ge k} \{|X_n-a|<1/m\}$。可数个 measurable set（可测集）做交与并仍然 measurable（可测），所以右边落在 σ-field（σ 代数）里；若直接对实数 $\varepsilon>0$ 取不可数并，可测性没有任何保证。这条恒等式是把 almost surely（几乎必然）从直觉变成 measure theory（测度论）对象的第一步，值得亲手写一遍，也只有写一遍才知道可数的位置在哪一层。
>
> Problem 13 关于和的机制只有一句话：坏集可以并起来。设 $A$ 是 $X_n$ 不收敛到 $a$ 的 event（事件），$B$ 是 $Y_n$ 不收敛到 $b$ 的 event（事件），题设给出 $P(A)=P(B)=0$。关键观察是：若 $\omega \notin A \cup B$，则两个极限都存在，由实分析里的极限运算法则，$X_n(\omega)+Y_n(\omega) \to a+b$。于是「和序列发散」这个坏集 $C$ 被包含在 $A \cup B$ 里——是包含，不是相等，因为 $A \cup B$ 中可能还有些点，和序列照样收敛。
>
> 于是 $P(C) \le P(A \cup B) \le P(A)+P(B) = 0$，即 $P(C^c)=1$。第二个不等号是 subadditivity（次可加性）。对可数无穷多个 event（事件）而言，同样的结论由 countable additivity（可数可加性）给出：可数个 null set（零测集）之并仍是 null set（零测集）。这两件事在实分析里是同一条公理的两面，不要当成两个定理分开记。
>
> 与实分析的接口：almost everywhere（几乎处处）永远是相对于某个 measure（测度）而言的。Lebesgue null set（勒贝格零测集）在 Dirac measure（狄拉克测度）下可以是满测度，所以「几乎处处成立」这句话脱离测度就没有意义。概率论里 measure（测度）固定为 $P$，a.s. 与 a.e. 是同一条语义，只是载体换成了 probability measure（概率测度）。这也解释了为什么 a.s. 的证明总以「挖掉一个零测集」为骨架：所有几乎必然结论都是逐点结论加一张零测集的豁免证。
>
> 方向必须刻死。a.s. 收敛蕴含 convergence in probability（依概率收敛），Problem 15 证明的正是这条蕴含；反过来不成立。反例是 typewriter sequence（打字机序列）：$[0,1]$ 上按 $1/2, 1/4, 1/4, 1/8, \ldots$ 逐层滑动的区间指示函数，它依概率收敛到 $0$，却没有任何一个点收敛。所以任何「由依概率收敛推出几乎必然收敛」的推理都必须额外付出条件，典型的两条是单调性与可求和性——Problem 16 提供的正是后者。
>
> 顺带把 Problem 14 的结构看清：$\frac{X_1+\cdots+X_n}{Y_1+\cdots+Y_n}$ 的收敛被拆成分子、分母各自的 a.s. 收敛，再用 Problem 13 的结论合起来。但封闭性有边界，必须分开说：加法与乘法在整条实轴上连续，所以 a.s. 收敛对加、乘封闭；除法不行，因为映射 $x/y$ 在 $y=0$ 处根本不连续。题面只假设 $Y_n \ne 0$，并没有要求极限 $b \ne 0$，于是取 $X_n \equiv 1$、$Y_n = 1/n$（此时 $b=0$），$X_n/Y_n = n \to \infty$，a.s. 收敛的和被除成了一个发散的商——数值上 $1/(1/10)=10$、$1/(1/1000)=1000$，看得一清二楚。正确的陈述是：在 $b \ne 0$，或更强地 $\{|Y_n|\}$ 一致远离 $0$ 时，除法才保持 a.s. 收敛。题面里 $a/b$ 这个写法本身就已经默认了 $b \ne 0$。
>
> 工程视角补一句。数值模拟里你只能抽有限条 path（路径），a.s. 是对整个样本空间成立的断言，它不保证你手上这条 path（路径）收敛，只保证坏路径所占的 probability（概率）为 $0$，所以随机抽一条几乎必然落在好集里——统计上安全，单次试验上不安全。常见的失误是把「以概率 1」读成「对所有情况」：浮点实现里的伪随机序列有周期，严格说它是确定性序列，a.s. 的说法在那里整体失效，需要重新论证才能借用。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把这条证明抽成模板，叫它「ε-剥离法」，三步：① 剥离——把「序列收敛到 $\theta$」这个含 $\forall \varepsilon>0$ 的断言先固定到一个具体的 $\varepsilon>0$ 上，得到只依赖 $\varepsilon$ 的尾部语句；② 单调化——把语句里的「存在 $k$」换成 event（事件）的并，令 $A_k$ 为「对每个 $n \ge k$ 都有 $|Y_n-\theta|<\varepsilon$」的 event（事件），则 $\bigcup_k A_k$ 就是「存在这样的 $k$」，而 $A_k$ 随 $k$ 递增；③ 取极限——用 probability（概率）的 continuity from below（从下方连续）性质把 $\lim_k P(A_k)$ 换成 $P(\bigcup_k A_k)$，再与 $P(C)=1$ 比较。
>
> 为什么 $A_k$ 一定递增，不是巧合而是结构。$A_k$ 要求「从第 $k$ 项起全部合格」，$A_{k+1}$ 比它少了一条约束（第 $k$ 项），于是 $A_k \subset A_{k+1}$。递增的 event（事件）列才能用从下方连续取极限，而这条技术条件被「尾部」这个词自动满足——这正是 tail event（尾部事件）在概率论里好用的原因。顺带纠一个容易发生的联想：Borel–Cantelli 第一引理走的是次可加性，即 $P(\limsup_n A_n) \le \sum_n P(A_n)$，完全不需要这里的递增结构；递增性在本文里只负责让 continuity from below 可用，两件事没有因果关系。
>
> 唯一真正需要动脑的地方是包含方向。$A_k \subset \{|Y_k-\theta|<\varepsilon\}$，因为 $A_k$ 要求从 $k$ 起全部合格，特别包含 $n=k$ 这一条。若方向写反，会得到 $P(|Y_k-\theta|<\varepsilon) \le P(A_k)$，取极限后只剩 $\le 1$ 这个空结论，证明整个塌掉。方法上的教益：这类论证里除了一处包含关系，其余全是机械的单调性搬运。
>
> 机械地走完：由「每个收敛点必在某个 $k$ 之后全部落在 $\varepsilon$ 邻域内」，得 $C \subset \bigcup_k A_k$，于是 $1 = P(C) \le P(\bigcup_k A_k) = \lim_k P(A_k) \le \liminf_k P(|Y_k-\theta|<\varepsilon)$。左端给的是 $\liminf$（下极限），而依概率收敛要的是极限；两者在此等价，但需要两半合起来。下界那一半就是上面那串不等式的末项：$1 \le \liminf_k P(|Y_k-\theta|<\varepsilon)$。上界那一半来自「每项都不超过 $1$」：对每个 $k$ 有 $P(|Y_k-\theta|<\varepsilon) \le 1$，故 $\limsup_k P(|Y_k-\theta|<\varepsilon) \le 1$。两半一夹，$1 \le \liminf \le \limsup \le 1$，上下极限相等且都等于 $1$，极限存在。注意方向：单靠「每项不超过 $1$」只能压住上极限，压不出 $\liminf \ge 1$——少了由 $P(C)=1$ 给出的那一半，论证就是空转。
>
> 为什么只需处理一个 $\varepsilon$。逐点收敛的定义量化在所有 $\varepsilon>0$ 上，但要证出「对每个固定 $\varepsilon$，尾部 probability（概率）趋于 $1$」，就足以覆盖全部 $\varepsilon$，无需在证明里显式搬运 $\varepsilon$ 的量词。反过来，要造「依概率收敛而不 a.s. 收敛」的反例，就必须让收敛速度随 $\varepsilon$ 退化——typewriter sequence（打字机序列）正是这样：对每个 $\varepsilon$ 尾部概率趋于 $1$，但区间宽度趋零、位置无限漂移，于是没有任何点收敛。
>
> 实分析视角。a.s. 收敛是「对 measure（测度）而言几乎所有的点，量词 $\forall \varepsilon \exists k$ 成立」，依概率收敛是「对每个 $\varepsilon$，坏集的 measure（测度）趋于零」。前者控制点集，后者控制测度，从前者到后者是丢掉一层逐点信息。够精细的版本是 Egorov theorem（叶戈罗夫定理）：几乎必然收敛在一个测度任意接近全空间的集合上是 uniform（一致）的；也就是说，逐点信息只在丢掉一块任意小的集合之后才降级成一致收敛，这一步正对应这里「丢掉坏集」的动作。
>
> 数值检查。想验证一条实现是否依概率收敛，固定 $\varepsilon$ 画 $P(|Y_k-\theta| \ge \varepsilon)$ 随 $k$ 的曲线，看它是否压向零——这是可计算、可观测的量。a.s. 收敛对应的是「对几乎所有 seed，path（路径）最终进入并留在 $\varepsilon$ 带内」，它需要看整条 path（路径），而且「最终」这个时刻没有可计算的界。把这两层分清，是 Monte Carlo 实验设计与纯数学证明之间的接口所在。
>
> 一条推广：同一套剥离动作在 SLLN 的证明里反复出现。凡是要从「a.s. 类型的强度」退到某种更弱模式，都先固定 $\varepsilon$、把事件列单调化、再取极限；模板固定下来以后，剩下的只是算每一层 event（事件）的 probability（概率）。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把整条证明的骨架摆出来。目标是 $S_n/n → 0$ a.s.，其中 $S_n = X_1+\cdots+X_n$，各 $X_i$ 是 i.i.d.（independent identically distributed，独立同分布）且均值为零。想法是把「a.s. 收敛」降解成「某个非负随机变量的级数可求和」，这一步由 Problem 16 完成：若 $Y_n≥0$ 且 $\sum_n E[Y_n]<∞$，则 $\sum_n Y_n<∞$ a.s.，从而 $Y_n → 0$ a.s.。于是问题变成：取什么 $Y_n$，它的期望级数才收敛？
>
> 选阶数的判据是幂次而非美感。取 $Y_n = |S_n/n|^2$ 时 $E[Y_n] = n\sigma^2/n^2$，级数 $\sum_n \sigma^2/n$ 发散，Problem 16 的门槛过不去；取四阶时 $E[S_n^4]$ 只长到 $n^2$ 量级，而分母是 $n^4$，剩下 $\sum_n 1/n^2$ 这条收敛的 p-series（p 级数），它在 $p=2$ 时收敛，这正是 Euler 1735 年算出 $π^2/6$ 的那一条。所以「为什么恰好四阶」的答案是：阶数决定幂次，幂次决定可求和性，二阶差一个幂次，四阶刚好够。
>
> 数项时按指标的重合模式分类。四重和里，若某个指标只出现一次，则因各 $X_i$ 相互独立且均值为零，这一项可以拆出一个 $E[X_i]=0$ 的因子而整项清零。幸存的模式只剩两种：四个指标全同，共 $n$ 项、每项取值 $E[X^4]$；恰有两个不同指标各出现两次，共 $3n(n-1)$ 项、每项取值 $E[X_1^2X_2^2]$。系数 $3$ 是把四个位置分成两块的方式数——与 6.042J 里 4 个顶点上 perfect matching（完美匹配）的个数是同一个计数。
>
> 保留非零均值时还要多出 $(3,1)$、$(2,1,1)$、$(1,1,1,1)$ 几类项，只写三类在 $n≥3$ 就错。按指标的重数把四重和分组，完整的展开是 $E[S_n^4] = nE[X^4] + 4n(n-1)E[X^3]E[X] + 3n(n-1)(E[X^2])^2 + 6n(n-1)(n-2)E[X^2](E[X])^2 + n(n-1)(n-2)(n-3)(E[X])^4$，其中 $(2,1,1)$ 类有 $6n(n-1)(n-2)$ 项、$(1,1,1,1)$ 类有 $n(n-1)(n-2)(n-3)$ 项。陷阱在 $n=2$：后两类的系数都含因子 $(n-2)$，自动归零，三项式恰好吃对，所以只拿 $n=2$ 验算抓不到错。用 $X∈\{0,2\}$、$P(2)=3/5$ 复算：$n=3$ 的真值是 $395.136$，三项式只给 $270.72$；$n=4$ 的真值是 $1069.6704$，三项式只给 $522.24$。凡引用这条公式就得写全。教材先假设零均值，最后一段用 centering（中心化）把一般情形归约：$X_i-E[X_1]$ 零均值，套用结论得 $(S_n-nE[X_1])/n → 0$，等价于 $S_n/n → E[X_1]$ a.s.。这是「先规范化、再把结论搬回」的标准手法，与构造 t 统计量的思路同源。
>
> 放缩只差常数。由二元均值不等式 $x^2y^2 ≤ (x^4+y^4)/2$ 得 $E[X_1^2X_2^2] ≤ E[X_1^4]$，于是 $E[S_n^4] ≤ (n+3n(n-1))E[X_1^4] ≤ 3n^2E[X_1^4]$。对可求和性而言常数无关紧要，这正是 a.s. 收敛比逐项收敛「宽容」的地方：它只对 tail（尾部）敏感，早期有限项多大都不影响，所以任何多项式级放缩都够用。
>
> 收尾三步：$\sum_n E[(S_n/n)^4] ≤ 3E[X_1^4]\sum_n n^{-2}<∞$；由 Problem 16 得 $\sum_n (S_n/n)^4<∞$ a.s.；级数收敛蕴含通项趋于零，故 $S_n^4/n^4 → 0$，再由 $x^4 → 0$ 当且仅当 $x → 0$ 得 $S_n/n → 0$ a.s.。最后一步不涉及任何概率论证，纯粹是实数的单调性事实。
>
> 代价要说清。四阶矩条件是充分的、不是必要的：Kolmogorov 在 1933 年的 Grundbegriffe 里给出的条件是独立且 $E|X_1|<∞$，四阶矩远强于它；Etemadi 在 1981 年给出的初等证明甚至只要求 pairwise independent（两两独立）。四阶矩法的价值在教学——它把 SLLN 的全部困难压缩成组合计数，绕开了 truncation（截断）与 Kolmogorov 三级数定理。代价是它不给速率：真实速率由 central limit theorem（中心极限定理）给出，$S_n/n$ 的量级是 $n^{-1/2}$，而这条证明对速率一无所知。
>
> 换个视角看同一条证明：$S_n^4/n^4$ 就是 $|S_n/n|$ 的四次幂，而把「收敛」翻译成「一串非负随机变量组成的级数有限」是概率论特有的技巧，其合法性来自 Problem 16 背后那条 monotone convergence theorem（单调收敛定理，Beppo Levi 1906）：非负随机量可以无条件交换期望与无穷求和。所以这条证明有三根支柱——组合计数、p 级数、单调收敛定理，缺一根都走不通。另外 $E[X_1^4]<∞$ 还顺带经 $|x| ≤ 1+x^4$ 保证了均值有限，这行不等式是截断论证里最常用的一步。
>
> 方向警告，也是最容易犯的错：由 $E[(S_n/n)^4] → 0$ 直接宣布 a.s. 收敛是错的。期望逐项趋于零只给依概率收敛（用 Markov 不等式），a.s. 需要的是期望的级数 summability（可求和）——一个比「逐项趋于零」强得多的条件。Problem 16 的全部价值就在这个从逐项到可求和的升级上。


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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 拿到目录先看骨架：第 6 章是严格的「离散—连续」平行结构，整章就是一张表被逐项证明。Bernoulli process（伯努利过程）对应 Poisson process（泊松过程）；binomial distribution（二项分布）对应 Poisson distribution（泊松分布）；geometric distribution（几何分布）对应 exponential distribution（指数分布）；第 $k$ 次到达时刻的 Pascal distribution（帕斯卡分布）对应 Erlang distribution（爱尔朗分布，即形状参数为正整数的伽马分布）；splitting（分裂）对应 thinning（稀疏化）；merging（合并）对应 superposition（叠加）；fresh-start（新开始）对应 independent increments（独立增量）加 memorylessness（无记忆性）。先把这张表抄在本子上，学一节勾一节。
>
> 过渡的机制只有一个：时间单位取极限。伯努利过程里 $p$ 是无量纲的 probability（概率），泊松过程里 $\lambda$ 是带量纲的 rate（强度，单位 $1/$时间）。连接方式是令时隙长度 $\delta → 0$、$p = \lambda\delta + o(\delta)$，并保持 $np = \lambda t$ 不变——也就是「单位时间内期望到达数」不变。$p$ 与 $\lambda$ 差一个量纲，凡是把 $np$ 与 $\lambda t$ 混用的推导，代回单位就能立刻发现错误。
>
> 代数版本就是二项分布的 Poisson limit theorem（泊松极限，1837 年由 Poisson 给出）：当 $n → ∞$、$p → 0$、$np → \lambda$ 时，$p_S(k) = C(n,k)p^k(1-p)^{n-k} → e^{-\lambda}\lambda^k/k!$。推导的核心是 $(1-\lambda/n)^n → e^{-\lambda}$——恰好是 PDF p301 页首、§5.5 正文收尾处被分页切断的那条 identity（恒等式），本章把它用作全章的技术支点，值得记住它在这里的用处而不是只在微积分里见过它。
>
> 为什么必须先离散。离散版每个量都能手算：二项系数、几何级数、Pascal 组合、期望的首步递推，全是 6.042J 练过的有限计数。连续版需要指数与伽马函数的积分，但结构完全不变。顺序反了会有严重后果：先学连续版，会把「指数分布的无记忆性」当成一条孤立的怪现象，而它其实只是几何级数的尾在缩放极限下的像。先有离散的脚手架，连续版就只是把符号换掉。
>
> 两条线的平行不是逐项对应，这一点必须说清。连续时间允许「两个到达在同一时刻」的概率为零（对泊松过程，一个小区间内到达两次的 probability（概率）是 $o(\delta)$），而离散时间里两次到达可以落在同一时隙。这条差别不是细节：它让泊松过程在任意时刻都可切分，也让许多「同时发生」的边界情况在连续版里自动消失。凡是要把离散结论照搬过去，先问一句「同时性在那边是不是可测的零集」。
>
> 与 18.06 和 18.065 的接口。有限步转移写成矩阵幂，离散时间的长期行为由 stochastic matrix（随机矩阵，行和为 1）的 Perron–Frobenius 理论给出平稳分布；连续时间把幂换成矩阵指数 $e^{Qt}$，其中 $Q$ 是 rate matrix（速率矩阵）。这条「离散用幂、连续用指数」的对应，与矩阵方法课里「差分方程对应微分方程」是同一件事。
>
> 与 CSAPP 的接口。离散时隙模型就是 tick（时钟节拍）驱动的状态推进，连续时间模型是 event-driven（事件驱动）仿真；两者的数值误差来源不同。工程实现里几乎都用离散时隙，因为事件驱动仿真器要维护一个 priority queue（优先队列，堆），而按 tick 推进的循环只要一个计数器——这是 CLRS 里「堆还是数组」的经典取舍在仿真上的重现。
>
> 学习建议：学完本章做一次对位翻译练习。把每个离散结论写成连续版，逐条对照，标出哪一条需要用极限论证、哪一条能整句照搬。做不出的那几条，就是本章真正的技术内容；能整句照搬的那些，说明你之前的离散理解是对的。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 教材说随机过程「并未构成重大的概念突破」，这句话是精确的技术判断，不是谦辞。框架只有一套：样本空间 $Ω$、σ-field（σ 代数）$\mathcal{F}$、probability measure（概率测度）$P$ 一次性给定，之后每个 $X_t$ 都只是 $Ω → \mathbb{R}$ 的 measurable function（可测函数）。所谓「过程」不过是把指标从单个的 $n$ 换成 $t$ 之后的一族随机变量，没有新的公理，没有新的空间。
>
> 那么新东西在哪里——在 joint distribution（联合分布）。单个 marginal（边缘分布）根本不能确定过程：两组相关性完全不同的序列可以有逐点完全相同的 marginal（边缘分布），就像两个协方差不同的二元正态有相同的两条边缘曲线。过程的律由全部 finite-dimensional distributions（有限维联合分布）确定：两个过程同分布当且仅当所有有限维切片同分布。一个相容的有限维分布族能否真的拼出一个过程，是 Kolmogorov extension theorem（柯尔莫哥洛夫扩张定理，1933）回答的问题。这条定理是整章的地基，教材把它放在脚注里，但它是「过程」这个概念合法的唯一依据。
>
> 与 18.065 的接口要加一句限定。一列随机变量像无穷维向量，covariance（协方差）充当内积——但这个类比只到二阶为止。covariance（协方差）只抓二阶信息，一般过程的高阶结构被它整个丢掉；gaussian process（高斯过程）是「均值加协方差决定全部有限维分布」的例外，正因为它特殊，工程里才爱用它。
>
> 关注点发生了两次转移。第一次从「某时刻的取值」转到整条 path（路径）：关心过程生成的整个序列，例如 long-term average（长期平均）、首次穿越时刻、最大值分布。第二次从「分布」转到两种平均之间的关系——股票的平均价格是对一条 path（路径）沿时间取 time average（时间平均），而同一时刻大量同类系统的平均是 ensemble average（集合平均）。二者何时相等，是 ergodic theorem（遍历定理，Birkhoff 1931）的内容，也是第 6 章之后反复出现的主题。
>
> 与 CSAPP 的接口。「状态空间 + 随时间演化的规则」是过程的最小骨架：进程状态机、缓存一致性协议都是它的实例。差别在于过程论把规则换成 probability law（概率律），于是演化不再是确定的状态跳转，而是从 conditional distribution（条件分布）里抽样。
>
> 一条实操硬约束：采样一条 path（路径）必须一次性从联合分布里抽，不能分别从各时刻的 marginal（边缘分布）抽样再拼起来。后者得到的边缘分布全对、相关性全错，而画单变量直方图完全看不出问题——这是仿真里最常见的静默错误，也是「联合分布才是对象」这句话最实际的含义。
>
> 可测性视角收尾。一条 path（路径）是映射 $\omega ↦ (X_1(\omega), X_2(\omega), \ldots)$，即从 $Ω$ 到序列空间的可测映射，与实分析里讨论函数列的逐点收敛是同一件事：过程论只是给函数列装上了 probability measure（概率测度）。所以第 5 章那些 a.s. 收敛的定理，即 SLLN（强大数定律）与 Borel–Cantelli lemma（博雷尔–坎泰利引理），可以直接作用在过程上。突破发生在测度论那一层，而那笔账早就付过了。
>
> 留给第 7 章的伏笔：一旦加上马尔可夫约束，联合分布就被压缩成「初始分布 + 转移核」，无穷维对象塌缩成有限维数据。这类「用 conditional independence（条件独立）把联合分布压小」的操作，是教材后半部分统一的手法。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把它写成公式：对任意 $n$ 与任意 measurable set（可测集）$A$，有 $P(X_{n+1}∈A \mid X_1,\ldots,X_n) = P(X_{n+1}∈A \mid X_n)$。更紧凑的表述是 conditional independence（条件独立）：给定 $X_n$ 之后，未来 $X_{n+1},X_{n+2},\ldots$ 与过去 $X_1,\ldots,X_{n-1}$ 条件独立。教材那句「下一个值只通过当前值依赖过去」，是这句话的散文版。
>
> 它为什么有力量：把「整段历史」压缩成一个「状态」，于是 $n$ 步之后的分布可以由一步的转移迭代出来。形式化就是 Chapman–Kolmogorov equation（查普曼–柯尔莫哥洛夫方程）——$n$ 步转移矩阵等于一步转移矩阵的 $n$ 次幂。这与 18.06 直接接上：状态演化就是矩阵乘，长期行为就是矩阵幂的极限，极限由主特征向量给出。一个概率问题就这样变成了一道线代题。
>
> 与 state machine（状态机）的关系要说得准确。CSAPP 里的有限状态机、TCP 连接状态机、6.042J 的状态转换图，都是马尔可夫链的确定性特例：状态相同则下一步唯一。概率版只改了一件事——把「转移边唯一」换成「按转移概率抽样」。所以「马尔可夫性质就是状态机的数学化」这句话的准确含义是：它给出了「状态」这个概念的概率化定义，状态就是那个使未来与过去条件独立的 sufficient statistic（充分统计量）。
>
> 状态不是给定的，是被设计的，这是本节最实用的洞见。马尔可夫性是相对于「选定的状态变量」而言的性质，不是过程的固有属性。以抛硬币的最近一次结果作状态，序列是马尔可夫的；以「迄今正面总数」作状态，也是马尔可夫的；但若真实机制依赖前三次、却只记录一次，马尔可夫性立刻不成立。工程里加 feature（特征）之所以有效，正是因为它扩充状态，把非马尔可夫过程改造成马尔可夫的。CSAPP 里的处理器之所以能「只看寄存器和内存」，是因为整段历史已经被编码在状态里了。
>
> 历史值得单说。Andrey Markov 在 1906 年开始发展「链式相依」的模型，动机是反驳 Nekrasov 的主张——后者认为大数定律必须预设各次试验独立。1913 年 Markov 发表《欧根·奥涅金文本的统计研究示例》，把普希金这部长诗前 20000 个字母编码为元音 / 辅音两种状态，估出 $2×2$ 的 transition probability（转移概率），并据此说明相依序列依然服从大数定律。所以马尔可夫链的诞生不是抽象思辨，而是一次用数据反击哲学立场的行动。
>
> 与分治的对比。分治要求子问题相互独立，6.006 里归并排序的分析就靠这一条；马尔可夫允许序列逐步相依，只要求依赖在每一步被「当前状态」截断。分析上的差别很实在：分治给出 recurrence（递归式），靠主定理解；马尔可夫给出转移矩阵的幂，靠特征值解。两套工具不能互换。
>
> 边界也要说清。马尔可夫性不排除相关性，它排除的是「超出当前状态的那部分历史」。所以两个过程可以都是马尔可夫的，长期行为却完全不同；stationary distribution（平稳分布）的存在与唯一并不需要 aperiodic（非周期）：有限状态加上单一的 irreducible recurrent class（不可约常返类）就足以保证存在且唯一。aperiodic 是逐点收敛 $T_{ij}(n)→\pi_j$ 的前提，不是存在性前提——周期链同样有唯一平稳分布，只是 $T_{ij}(n)$ 不逐点收敛。这些是第 7 章的内容。这里先留一条可操作的判据：要验证马尔可夫性，就问「知道当前状态之后，再补上更多历史，预测会变吗」。


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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> first-step equation（首步方程）的全部内容是：站在任意一步上，只看下一步。$T$ 要么取 $1$，其 probability（概率）为 $p$，要么大于 $1$，此时首次试验失败，而失败之后整个过程重新开始，剩余等待与一个全新的 $T$ 同分布，这一步用的是 fresh-start（新开始性质）。于是 $E[T] = p\cdot 1 + (1-p)\cdot(1+E[T])$，解出 $E[T] = 1/p$。一行条件期望配一条无记忆性断言，是整章最经济的推理。
>
> 先补一个漏洞：方程成立的前提是 $E[T]<∞$，否则两边都是 $∞$，等式什么也没说。干净做法是 truncation（截断）：令 $T_N = \min(T,N)$，对 $T_N$ 写出递推 $E[T_N] = p + (1-p)(1+E[T_{N-1}])$，得 $E[T_N] = (1-(1-p)^N)/p$，再令 $N → ∞$，用 monotone convergence theorem（单调收敛定理，Beppo Levi 1906）取极限得 $1/p$。这一步正是实分析训练的用处：不经截断的递推在期望无穷时是无意义的等式。
>
> 二阶矩走同一条路。写出 $E[T^2] = p\cdot 1 + (1-p)(1 + 2E[T] + E[T^2])$，把 $E[T]=1/p$ 代进去解得 $E[T^2] = (2-p)/p^2$，故 $\mathrm{var}(T) = (1-p)/p^2$。注意 $p → 0$ 时均值与 variance（方差）都发散，而方差与均值之比 $(1-p)/p\approx1/p$ 同样发散：成功概率极低时，等待时间的绝对波动按 $1/p^2$ 增长，比它的期望更不可控。这里顺带纠一个常被搞反的量：$\mathrm{var}/\mathrm{mean}^2 = 1-p≤1$ 是有界的，$p=0.1$ 时给 $0.90$，根本不发散；发散的是「方差与均值之比」，不是「方差比均值平方」，两者差一个随 $1/p$ 增长的因子。
>
> 用级数路线做独立校验。$E[T] = \sum_{t≥1} t(1-p)^{t-1}p$，令 $q = 1-p$，先对几何级数 $q^t$ 求和再对 $q$ 求导，两步都得 $1/p$。这条路不需要任何概率论证，纯粹是 6.042J 的级数技巧；两条独立路线算出同一个数，说明首步方程没有偷换概念。凡是能两算的地方都值得算两遍，这是最便宜的错误检测。
>
> 无记忆性还给出了刻画性质：几何分布是唯一支撑在 $\{1,2,\ldots\}$ 上且满足 $P(T>n+m \mid T>n) = P(T>m)$ 的分布。正向只需把左边算成 $(1-p)^{n+m}/(1-p)^n = (1-p)^m$，与 $n$ 无关；反向的唯一性由这个等式对一切 $n,m$ 成立推出尾概率必须是几何尾 $c^n$。连续版对应物是指数分布，那里要求尾函数满足 functional equation（函数方程）$G(s+t)=G(s)G(t)$，唯一的非增解是 $G(t)=e^{-\lambda t}$。
>
> 这台机器还能直接推广到「等到第 $k$ 次成功」：设 $E_k$ 为该时刻的期望，则 $E_k = 1/p + E_{k-1}$，解出 $E_k = k/p$，与负二项分布的均值一致。换一个初值条件就能算出更复杂的等待量，这才是 first-step analysis（首步分析）作为工具的真正价值。
>
> 与工程的接口。retry loop（重试循环）的期望尝试次数就是 $1/p$，hit rate（命中率）给定期望查找次数同形。但若失败相关（真实网络、真实磁盘），无记忆性立刻失效，$1/p$ 会系统性低估延迟。工程上的 exponential backoff（指数退避）正是承认相关性存在、主动把尝试间隔拉开的做法。
>
> 与 6.006 的接口。随机算法分析里常见的「期望试验次数 $1/p$」与这里完全同源，差别只在 terminology（术语）：那边叫 expected number of trials（期望试验次数），这边叫 first success time（首次成功时刻），指的是同一个几何随机变量，连公式都不用改。
>
> 拿 $p = 0.1$ 手算一遍感受量级：$E[T] = 10$，$\mathrm{var}(T) = 0.9/0.01 = 90$，标准差约 $9.5$，与均值同量级；$P(T>10) = 0.9^{10}$ 约等于 $0.35$，即超过三分之一的概率要等过平均等待时间。这就是长尾的直接体感，任何把均值当典型的估计都会低估尾延迟。
>
> 最后一个易错点：$E[T]=1/p$ 是关于 mean（均值）的陈述，不告诉你 $T$ 集中在哪里。几何分布是长尾的，$P(T>1/p)=(1-p)^{1/p}$，只有 $p→0$ 时它才约等于 $e^{-1}$，即约 $0.37$——$p=0.1$ 给 $0.349$、$p=0.5$ 只给 $0.25$，所以那个「约 $e^{-1}$」是渐近陈述，不是对每个 $p$ 都成立的恒等式；但方向不变：「平均等 $1/p$ 步」绝不意味着「等 $1/p$ 步通常就成功」。这类「均值不等于典型值」的误读，在排队系统与超时参数设定里极其普遍。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 代数上一步到底。$P(T-n=t \mid T>n) = P(T=n+t)/P(T>n) = (1-p)^{n+t-1}p \big/ (1-p)^n = (1-p)^{t-1}p = P(T=t)$，对 $t≥1$ 成立。分子分母的 $(1-p)^n$ 正好抵消——这个抵消就是「记忆」消失的机制本身。它不是巧合，而是几何尾 $P(T>n)=(1-p)^n$ 的形状决定的：尾是纯指数型，除以它只改变系数不改变形状。
>
> 抽样视角把机制说透。条件事件 $\{T>n\}$ 属于由 $X_1,\ldots,X_n$ 生成的 σ-field（σ 代数），而未来 $X_{n+1},X_{n+2},\ldots$ 与它独立，所以对任何未来 event（事件）$B$ 与任何历史 event（事件）$A$ 都有 $P(B \mid A)=P(B)$。由此提炼一条原理：条件作用不能创造信息，只能暴露信息。若条件事件完全由一块与未来独立的历史决定，conditional distribution（条件分布）退回无条件分布；反过来，若条件事件含有关于未来的信息（例如「至少有一次成功」已经用掉了部分未来），无记忆性立刻失效。
>
> gambler's fallacy（赌徒谬误）的精确病灶。大数定律说的是 $S_n/n → p$，讲的是比例收敛，不是差额 $S_n-np$ 有界。事实上由 central limit theorem（中心极限定理），$S_n-np$ 的量级是 $n$ 的平方根，即 $n^{1/2}$，绝对偏差随 $n$ 增长而不是缩小。所以「连输之后该赢了」错在把「比例回归」读成了「差额补偿」：一条必然成立的长期比例，被替换成一条根本不存在的短期记忆。这是击碎该谬误最锋利的表述，比反复强调「硬币没有记忆」有效得多。
>
> 历史注脚。这类谬误在 1913 年蒙特卡洛赌场的轮盘上留下了名字：黑色连续出现 26 次，赌客据此加倍押红，损失惨重，于是「Monte Carlo fallacy（蒙特卡洛谬误）」成了同义词。这类谬误的结构值得记住：同一段有限观测总能用无穷多套模型拟合，缺了独立性假设与样本量作约束，就无从分辨哪一套才对。反过来，只要前提补齐，模型就会被数据排除：独立性一旦写进假设，「连输之后该赢了」在数学上就没有立足点，赌场里那套加倍策略也就失去了理论借口。
>
> 反例界定边界。不放回抽样，也就是抽签，在 hypergeometric distribution（超几何分布）里，抽出一个红球之后剩余红球比例真的变了，「记忆」在那里是真实的。差别不在分布的「形状」，而在采样机制是否独立。任何声称无记忆性的论证，都必须回到「各次试验独立」这个前提上重新确认一遍，而不是从结论的形状反推。
>
> 与泊松过程的接口。Poisson process（泊松过程）在任意时刻满足 fresh-start（新开始）：从任何划定时刻起，未来的到达序列与过去独立且同分布。指数分布的无记忆性正是这条性质在单个到达间隔上的投影。工程上它意味着「下一次到达不取决于已经空闲了多久」，这条假设是所有 M/M/1 队列分析的基础，也是它们在真实突发流量下失准的原因——真实流量有相关性，无记忆性被违背。
>
> 一条反驳工具，可以直接用。若有人主张「已经等了 $n$ 步，剩余等待的期望该变小了」，让他算 $E[T-n \mid T>n]$：由无记忆性它恒等于 $1/p$，与 $n$ 无关。这个等式干净、可数值验证，比争论直觉有效得多——把它写成三行模拟代码，跑出来的曲线就是平的。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把符号对齐，因为这一页的 OCR 数字彼此冲突，读之前必须先把矛盾摆明。图注给的是：上路径 $T=4$、$B=3$、$I=2$、$Z=\cdots$（被截断）；下路径 $T=5$、$B=4$、$Z=4$。若把 $T$ 读作「所考察的总区间」，上路径立刻自相矛盾：一个忙碌期加一个空闲期已经 $B+I=3+2=5$，超过 $T=4$，而循环长度按定义不可能超过所考察的区间。所以那个读法站不住，真正需要回查的是原书 Figure 6.2 的图注本身，此处只标出不一致，不臆造数字。$Z$ 也有麻烦：本页把它记作 renewal time（更新时刻），而同一节的承接说明又把 $Z$ 记作 interarrival time（到达间隔），同一个字母承担了两个量。⚠ 需回查原书 Figure 6.2。
>
> 图的结构本身是清楚的：把时间轴切开，得到交替出现的两种游程。busy period（忙碌期）是成功的极大游程，长度 $B$ 满足 $P(B=k)=p^{k-1}(1-p)$，均值 $E[B]=1/(1-p)$；idle period（空闲期）是失败的极大游程，长度 $I$ 满足 $P(I=k)=(1-p)^{k-1}p$，均值 $E[I]=1/p$。两个式子的底数与收尾因子正好互换，方向千万别记反：忙碌期要求「先成功若干次、再用一次失败收尾」，所以成功在指数里、失败在因子外；空闲期相反。量纲检验也简单：$p\to1$ 时 $E[B]\to\infty$、$E[I]\to1$，即几乎全是成功、空闲只剩一格；$p\to0$ 时反过来。顺带指出本页那行公式的标签错乱：它写作 $P_T(k)=(1-p)^{k-1}p$，可 $T$ 在同页被定义为「首个成功的时刻」，这个式子的形状确实是 $T$ 的 PMF，却又被说成「首个忙碌期的规律」；按忙碌期的定义应当是 $P_B(k)=p^{k-1}(1-p)$，两个式子只差指数与因子互换一位。
>
> 一个数值检查就能钉死方向。模拟 $2\times10^6$ 个时隙、取 $p=0.8$，成功游程的平均长度实测 $5.0071$，与理论 $1/(1-p)=5$ 吻合；若按错误的 $1/p$ 去预期，就只会给出 $1.25$，差四倍。注意 $p=1/2$ 时两个约定都等于 $2$，所以拿 $p=1/2$ 验算是抓不到这个错的——这正是参数检验要避开对称点的原因。
>
> 两个相邻长度为什么独立？不是因为它们服从不同分布，而是因为它们占据不相交的时隙集合，而 Bernoulli process（伯努利过程）在不同时隙上独立。这条理由必须写出来：一切「循环可以无限重复」的论证，最终都落在「不相交的坐标块独立」上。旧注写「都服从 geometric distribution（几何分布）且相互独立」，方向对，但没有给出这个前提，读者容易误以为是分布形状带来的。
>
> 把一个忙碌期加一个空闲期称为一个循环，循环长度 $C=B+I$ 是一列独立同分布的随机变量。这就是 renewal process（更新过程）的离散版：每到一个循环起点，过程在统计上回到同一状态。由独立性，$E[C]=1/(1-p)+1/p=1/\bigl(p(1-p)\bigr)$。这个数在 $p$ 接近 $0$ 或 $1$ 时急剧变大，正是「极端占用率让系统几乎只有一种时隙」的定量表现；$p=1/2$ 时它取最小值 $4$。这条式子还提供一个交叉校验：长期看时隙中成功的比例必须是 $p$，而 $E[B]/\bigl(E[B]+E[I]\bigr)=p$ 恰好成立——用错方向的 $1/p$ 与 $1/(1-p)$ 代进去就得不到 $p$。
>
> 这里值得种下 inspection paradox（检查悖论）：若在一个随机选定的时隙回头看，所在循环的平均长度不是 $E[C]$，而是 $E[C^2]/E[C]$——长的循环被抽中的概率与其长度成正比，这叫 length-biased sampling（长度偏倚抽样）。所以「平均忙碌期长度」与「随机看一眼看到的忙碌期长度」是两个不同的量，监控面板上的均值天然偏向长事件。这条与注 8 讨论的赌徒谬误同源：都是把「按比例抽样」误读成「按对象抽样」。
>
> 与数据结构的接口很直接：忙碌期就是一次连续命中，空闲期就是一次连续未命中。把 $p$ 读成缓存命中率、分支预测成功率或哈希探测的占用率，$E[B]$ 与 $E[I]$ 就分别是「平均连击长度」与「平均空窗长度」。CLRS 里分析哈希连续占用、CSAPP 里分析分支预测器状态机，用的都是同一套 run（游程）统计；差别只在 $p$ 的来源。
>
> 与 §6.2 的接口要提前指出：把时隙切细、把 $p$ 按比例缩小，离散的忙闲交替就收敛到 Poisson process（泊松过程），几何分布换成指数分布，游程结构换成相互独立的到达间隔。连续版之所以更常用，是因为它没有「时隙宽度」这个人为尺度——这正是下一节要清理掉的东西。
>
> 一条可执行的验证：模拟 $10^6$ 个时隙，记录每个循环的长度并取平均，结果应落在 $1/\bigl(p(1-p)\bigr)$ 附近；再随机抽 $10^5$ 个时隙，统计每个时隙所在循环的长度并取平均，这个平均值会明显更大，两者之比接近 $E[C^2]/E[C]^2$。一个实验同时验证更新结构与检查悖论，比记住两条公式有用。


> <span style="color:#7f8c8d;">![OCR 说明] 源页 `page_309.txt` 直接来自原书印刷页 300，其内容几乎完全被这幅 Figure 6.2 的示意图及其标注（$T$、$Z$、$\tt B$、$\tt I$、「first busy period」「up to …」「and idle」等）所占；图框内仅残留零星的正文文字，如括注 (a)、(b) $B = \cdots$、(c) $I = \cdots$，以及「mean, =」「1 - p, we …」「index …」等片段。这些碎片表明：本页正文本应紧接着讨论忙碌期与空闲期的期望（mean）等统计性质，但原文句子在这页几乎不可辨识。</span>

根据这些可辨的正文碎片并对照下一页的推导起点，本页正文原意大致是：考察第一个忙碌期与空闲期，并着手计算它们的均值等性质——这一步在下一页完成，那里出现了对应空闲期长度 $I$ 的概率质量函数 $P_I(k) = (1-p)^{k-1}\,p$ 以及 $\operatorname{var}(I)$，并最终指出该论证对第 $i$ 个忙碌期/空闲期（任意 $i$）都成立。

<span style="color:#7f8c8d;">[OCR 损坏说明]</span>

> <span style="color:#7f8c8d;">本页为纯示意图页，正文散文几乎全部被 OCR 吞没，只剩图内标注与零散片段；图中 $\tt Z$ 在顶部样本里的具体数值无法辨认（OCR 于该处断裂为「and Z」，数值缺失），故上方以 $\cdots$ 占位，不臆造数字。忙碌期与空闲期的 PMF、均值、方差完整推导在原书 300–301 页之间衔接完成，本页只呈现其开端的示意图。</span>

<!-- ===== PDF p310 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span> <span style="color:#7f8c8d;">（Sec. 6.1，PDF 页码 301；本页续接上一页 §6.1 关于忙/闲周期（busy/idle period）的讨论，随后给出「新开始性质」（fresh-start property）并以 Example 6.3 作正式论证。）</span>

> <span style="color:#7f8c8d;">承接上一页：设 $T$ 为首个成功的时刻，$B$ 为首个忙时段（busy period，连续成功的时段）长度，$I$ 为首个闲时段（idle period，连续失败的时段）长度，$Z$ 为到达间隔（interarrival time）。上一页已针对其中的部分量导出相应概率规律，本页先收尾忙/闲时段 PMF 的推导，再转入关于「随机时刻重新开始」的更一般讨论。</span>

对首个忙时段（first busy slot）的规律有（so that）

```math
P_T(k) = (1-p)^{k-1}\,p, \qquad k = 1, 2, \ldots
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 接下来原页本有一行关于闲时段方差 $\operatorname{var}(I)$ 的公式与式样，但该式在 OCR 中碎裂（仅余若干形似 $\frac{1-p}{p^{2}}$ 的残片），无法可靠复原，故此处不作臆造，按上一页几何分布的方差式补全。</span>

最后我们指出，这里给出的论证同样适用于第二个、第三个以及之后各次的忙（或闲）时段。因此，上面算出的各个概率质量函数对任意下标 $i$ 的第 $i$ 个忙时段与闲时段都成立。

如果我们从某个固定的时刻 $n$（a certain time $n$）开始观察一个伯努利过程（Bernoulli process），我们所见到的与一个刚刚开始的伯努利过程是无法区分的。事实表明，即便我们从某个随机的时刻 $N$（random time $N$）开始观察该过程，情形依然如此——只要 $N$ 仅由过程的过去历史（past history）决定、而不携带任何关于未来的信息。确实，在 Example 6.2 中我们断言过程从时刻 $L+1$ 开始重新开始时，就用到了这样的性质。再举一个例子：考虑一个轮盘赌（roulette wheel），把每次出现红色视为一次成功。从某一次固定的转动（比如第 25 次转动）开始生成的序列，与从连续五次出现红色之后立刻开始生成的序列，在概率上是无法区分的。无论哪种情形，过程都是重新开始的（尽管你总能找到持另类理论的赌徒）。下一个例子给出类似的论证，但来得更正式。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 6.3 的答案比证明过程更值得记住：$P(X_{N+1}=X_{N+2}=0)=(1-p)^2$，与 $p$ 无关。无论等连续两次成功等了多久，之后的两个时隙仍是两枚独立的硬币，因此答案里不该出现 $p$ 的任何别的组合。任何让结果依赖「等待时间长短」的直觉，都在这一点上被证伪；这是 fresh-start（重新开始）性质最强的一条内容，比「几何分布无记忆」更直接。
>
> $N$ 是一个 stopping time（停时）。定义不是「$N$ 随机」，而是：对每个 $n$，事件 $\{N\le n\}$ 落在 $\sigma(X_1,\ldots,X_n)$ 生成的 σ-field（σ 代数）里——取值只由到 $n$ 为止的观测决定，不偷看未来。教材写的是 $\{N=n\}$，两者等价，因为 $\{N\le n\}$ 是有限并 $\bigcup_{k\le n}\{N=k\}$。反过来，「最后一次成功的位置」「整条序列中第一个最大值的位置」都不是停时，它们要求先看完整条序列。
>
> 条件求和的合法性要单独交代，旧注在这里跳了一步。$\sum_n P(N=n)\,P(\cdot\mid N=n)$ 需要两件事：$\{N=n\}$ 构成划分，即两两不交、并起来覆盖全空间，以及条件概率在这组划分上可加。第二件是全概率公式的现成结论；第一件要证 $P(N<\infty)=1$，这不是免费的。
>
> $N$ 几乎必然有限，证明只要三行。把时隙按块 $(X_{2k-1},X_{2k})$ 两两分组，每块内部两个都是成功的概率为 $p^2$，块与块独立。于是前 $m$ 块里至少有一块成功的概率是 $1-(1-p^2)^m$，随 $m\to\infty$ 趋于 $1$。顺带得到一个定量的尾部界：$P(N>2m)\le(1-p^2)^m$，几何速度衰减。这同时保证了下面期望的有限性，也是 Wald 方程前提的来源。
>
> $E[N]$ 用 first-step analysis（首步分析）算最快，不要试图对 $\sum_t t\,p_{Y}(t)$ 硬求和。设 $a$ 为「上一个时隙不是成功」时还需等待的期望步数，$b$ 为「上一个时隙是成功」时的期望步数。从状态 $a$ 出发，下一步以 $p$ 进入状态 $b$、以 $1-p$ 留在 $a$：
>
> $a=1+p\,b+(1-p)\,a$，$b=1+(1-p)\,a$。第一式整理得 $a=(1+pb)/p$，代入第二式解出 $b=1/p^2$，再回代得 $a=1/p+1/p^2$。起点没有「上一个时隙」，属于状态 $a$，故 $E[N]=(1+p)/p^2$。校验：$p=1$ 时 $E[N]=2$，即第二个时隙就出现连续两次成功；$p=1/2$ 时 $E[N]=6$，与两状态链的数值解一致。
>
> 这里要纠正旧注的一处归属错误。旧注说 Wald 方程「第 7 章会以随机长度求和的形态出现」，这是错的：本书第 7 章是 Markov chains（Markov 链），用的是 Bertsekas 与 Tsitsiklis 的 Introduction to Probability 第 2 版，Athena Scientific 2008，§7.1 起于 p.340、章首页为 p.339；Wald 方程不在该章正文里。Wald 的原始工作属于 sequential analysis（序贯分析，Abraham Wald 在 1940 年代建立），是另一条脉络。教材真正反复用停时的地方是第 7 章的首步分析，那里处理的是「随机时刻的期望」，与 Wald 不是同一件事，混为一谈会让读者去找一个不存在的章节。
>
> Wald 方程本身仍然值得记住，但它的两个前提必须一起记：$E[S_N]=E[N]\,E[X]$ 要求 $N$ 关于 $\{X_i\}$ 是停时，且 $E[N]<\infty$；缺一条都会失败。一个常被引用的反例是让 $N$ 取「使 $S_n$ 达到最大值的下标」：它偷看未来，而且更糟——这个 $N$ 的 $E[N]=\infty$，于是 $E[N]\,E[X]$ 成了 $\infty\cdot0$ 这样的未定式，根本不能当 $0$ 用，两条前提被同时违反，拿它作「只违反停时条件」的反例并不干净。要干净的例子必须保住 $E[N]<\infty$：取 $X_i$ 独立、各以 $1/2$ 取 $+1$ 或 $-1$，令 $N=1$ 当 $X_2=+1$、否则 $N=2$。$N$ 偷看了 $X_2$，故不是停时；$E[N]=3/2<\infty$；而 $E[S_N]=\frac12\cdot0+\frac12\cdot(-1)=-\frac12\ne0=E[N]\,E[X]$。这一算把「停时条件不可省」钉死，也说明反例本身要检验：同时违反两条前提的反例什么也证明不了。这正是「条件作用不能创造信息，只能暴露信息」的另一种说法。
>
> 与流式系统的接口：停时在工程里对应「退出条件只依赖已读入的数据」。读到第一个满足谓词的元素就停，是停时；读完整个流再回头挑最好的，不是。online algorithm（在线算法）的竞争比分析之所以不能假设未来，根子就在这里——任何依赖未来的停止规则都会让「随机时刻重启」失效，教材那句「即便从随机时刻开始观察，情形依然如此，只要该时刻不携带关于未来的信息」讲的就是这个边界。
>
> 一个常被忽略的细节：教材严格化时用的是 $\{N=n\}$ 而不是 $\{N\le n\}$，两者在此题中都能用，但只有后者是停时的一般定义。若把停时写成「$\{N=n\}$ 与未来独立」，会漏掉「$N$ 可能取无穷」的情形；本节的 $N$ 有限性靠上面的分块论证补上，别处不一定成立。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 教材给的替代描述只有一句话，但它的分量在于「等价」二字。与其逐时隙记录 $0/1$，不如只记一列 interarrival time（到达间隔）。两种记录互为双射：给定 $0/1$ 序列，两个 $1$ 之间夹的 $0$ 的个数再加 $1$ 才等于该段的间隔，即 $T_k-1$ 恰是那一小段里 $0$ 的个数；给定间隔列，把每个长度为 $t$ 的间隔写成 $t-1$ 个 $0$ 后接一个 $1$，序列就重建出来。信息无损，样本路径一一对应。
>
> 要点在于独立性不是自动搬过去的。从「逐时隙独立」推出「间隔独立同分布」，是靠 fresh-start（重新开始）证出来的定理，不是同义反复：第一次成功后，其后所有时隙与之前独立，因此 $T_2$ 与 $T_1$ 独立；再用归纳推到 $T_3,T_4,\ldots$。跳过这一步、只凭「每个间隔都服从 geometric distribution（几何分布）」就断言它们联合独立，是把边缘分布当成了联合分布——这是本节最容易被读者糊过去的推理缺口。
>
> 选哪个视角取决于要问什么。问「第 $k$ 次成功的时刻」用间隔（求和）；问「$n$ 个时隙里成功几次」用计数（二项）；问「多久之后第一次成功」用首次到达时刻（几何）。三种问法对应三个坐标，选错就要多做一次卷积。教材后面每个例子的解法差异，几乎都能追溯到这一句。
>
> 旧注这里有一处事实错误要纠正：它把这件事类比成「6.042J/CSAPP 里的 run-length encoding（游程编码）」，但 6.042J 与 CSAPP 都不讲游程编码；游程编码属于数据压缩，出现在信息论、传真编码与 PNG 一类图像格式的语境里。类比方向可以留，出处必须换。
>
> 即便保留这个类比，也要加一条限定：标准游程编码记的是「长度 + 符号」两样，因为符号会交替；这里只记成功之间的失败个数，因为 $1$ 是固定分隔符。所以严格说这是单符号游程编码的特例，不是一般情形。
>
> 更硬的接口在熵上。逐时隙序列的 entropy rate（熵率）是 $H(p)$，以 bit（比特）为单位；间隔 $T$ 的 entropy（熵）是 $H(p)/p$，而 $E[T]=1/p$，于是「单位时间的熵」同样等于 $H(p)$。两个描述携带的信息量相等，这正是双射的定量版本。arithmetic coding（算术编码）自动发现的是同一件事：它不关心你把数据切成位还是切成游程。
>
> 但等价不等于等价价。逐位序列的字母表是二元、每位一比特；间隔序列的字母表是无限集，单个间隔要用变长码。工程上的取舍很直接：事件密集时逐位便宜，事件稀疏时间隔便宜。这正是 discrete-event simulation（离散事件仿真）用间隔推进、而不逐时隙扫描的原因——扫描空时隙是纯浪费。
>
> 均值方差一并记账：$Y_k=T_1+\cdots+T_k$ 给 $E[Y_k]=k/p$ 与 $\mathrm{var}(Y_k)=k(1-p)/p^2$。均值可加对任意随机变量成立；方差可加要独立，这里靠的就是上面那条定理。两条性质常被混为一谈，而混用会在组合多个随机量时直接算错。
>
> 一条可执行的检验：用间隔法生成 $10^6$ 个时隙的序列，与逐位法生成的序列比同样的统计量（成功总数、间隔直方图），两者应当无法区分。若间隔直方图系统性偏离几何形状，问题在随机数源而不在视角选择——这个判据能把两类 bug 分开。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> $Y_k=T_1+\cdots+T_k$ 是 $k$ 个独立同分布的几何随机变量之和，它计数的是「等到第 $k$ 次成功一共做了多少次试验」，PMF 为 $p_{Y_k}(t)=\binom{t-1}{k-1}p^{k}(1-p)^{t-k}$，$t=k,k+1,\ldots$。这里的参数记账方式最容易出错：negative binomial distribution（负二项分布）有「失败次数」与「试验总次数」两套参数化，差一个常数平移。教材用的是总次数，所以支撑从 $k$ 起、指数是 $t-k$；照抄成「支撑从 $0$ 起、指数是 $t$」会让整条公式错位一格，而错位后的表达式在 $t=k$ 处还能凑出对的值，很难被数值抽查发现。
>
> 归一化并不显然。$\sum_{t\ge k}\binom{t-1}{k-1}p^{k}(1-p)^{t-k}=1$ 等价于级数 $\sum_{j\ge0}\binom{k-1+j}{k-1}x^{j}=(1-x)^{-k}$，这是 generalized binomial theorem（广义二项式定理，Newton 1665）在负指数上的特例。「负二项」这个名字就是从 $(1-x)^{-k}$ 来的：系数是负指数二项式的展开系数，负号只是记号的结果。
>
> 便于记忆的写法是 $\binom{t-1}{k-1}=(-1)^{t-k}\binom{-k}{t-k}$。左边是普通组合数，右边是广义二项式系数，这条恒等式把「展开负幂次」与「隔板计数」两件看起来无关的事接上了。它的用途不止好看：把广义系数代回级数，可以一步验证归一化，不必再对几何级数求导。
>
> 卷积视角给的是矩，不是形状。$Y_k$ 是 $k$ 个独立几何变量之和，故 $E[Y_k]=k/p$、$\mathrm{var}(Y_k)=k(1-p)/p^2$。均值可加对任意随机量成立；方差可加要求独立，这里靠 §6.1 证过的间隔独立（见上一条注）。这两条在 CLRS 分析随机化算法时反复用到，尤其是「把总代价写成若干独立分量之和」那一步。
>
> 历史层次可以写得更准。Pascal 与 Fermat 1654 年的通信处理的是 problem of points（赌金分配问题）：赌局中途停止，赌注按什么比例分。旧注说它「为概率论奠基」，方向对，但可以精确：这类问题此前已有人碰过：Pacioli 在 1494 年、Cardano 在十六世纪的著作里都讨论过，Pascal 与 Fermat 的贡献是把「未完成赌局的期望收益」算成了一个确定的数——Fermat 穷举剩余路径，Pascal 用算术三角形做递推。Huygens 1657 年据两人方法写的小册子，是第一本印刷成书的概率论教科书。
>
> PMF 里的组合数就是 Pascal triangle（帕斯卡三角）的第 $t-1$ 行。为什么三角会出现在这里？因为「前 $t-1$ 次里恰有 $k-1$ 次成功」的计数本身就是二项式系数，而二项式系数的递推规则正是三角的生成规则。这条线索在下一条注的证明里显形，届时会看到同一个组合数被三种方式各自独立地得到。
>
> 连续版预告：把几何换成指数，$k$ 个独立指数之和就是 Erlang distribution（爱尔朗分布）的 $k$ 阶情形，$k=1$ 时退化为指数分布。这个分布以丹麦电话工程师 Agner Krarup Erlang（1878-01-01 至 1929-02-03）命名；他在 1909 年的论文《概率论与电话通话》（The Theory of Probabilities and Telephone Conversations）里证明泊松分布适用于随机电话话务，这被公认为 queueing theory（排队论）的起点。⚠ 「首创该分布」的归属有争议，更稳妥的表述是「以他命名、由他系统用于话务分析」。
>
> 支撑从 $k$ 起这件事在截断时有直接后果，紧接着的 Example 6.5 就是例子。上场时间 $Z=\min\{Y_6,30\}$，前 $24$ 个原子直接取 Pascal 值，最后一个原子必须用 $1-\sum_{z=6}^{29}p_Z(z)$ 补齐——因为 $Y_6>30$ 的全部质量被压到 $z=30$ 这一个点上。漏掉这一步，PMF 求和会小于 $1$，而这种偏差在小样本里看不出来。
>
> 数值上不要直接算大 $t$ 的组合数。稳妥做法有两条：用`lgamma`（对数伽马函数）在对数空间累加；或者用递推 $p_{Y_k}(t+1)=p_{Y_k}(t)\cdot\frac{t}{t+1-k}\,(1-p)$，从 $t=k$ 处的 $p^{k}$ 起步。后者每步一次乘法一次除法，天然保持非负，也不会在中间量上溢出，是写生成函数时的默认选择。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上性质框中三个公式在 OCR 中被拆散到多行（均值式读取为 `k(1-p) / p`、方差式读取为 `var(T1)+...+var(Tk) = k(1-p)/p^2`、Pascal PMF 读取为 `t(t-1)…1 / k … p^k (1-p)^{t-k}`）。此处按「第 $k$ 次到达时刻等于 $k$ 个彼此独立的参数 $p$ 几何随机变量之和」这一标准结果重建为规范 LaTeX；各数值均为标准导出，未作任何臆造。若有严格对照需要，请回查原书。</span>

为验证 $Y_k$ 的 PMF 公式，我们首先注意到 $Y_k$ 不可能小于 $k$。对 $t \geq k$，我们观察事件 $\{Y_k = t\}$（即第 $k$ 次成功……）——

<!-- 页末于句中截断（「the kth success …」未写完），下一例如/推导续接下一页。 -->

<!-- ===== PDF p313 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span> — §6.1（续）

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span> <span style="color:#7f8c8d;">（PDF p313，原书页 304；本页为续页——页首无新标题，续接上一页关于「伯努利过程中第 $k$ 次成功时刻 $Y_k$ 服从阶为 $k$ 的 Pascal 分布」之命题的证明后半段，随后进入 **Example 6.5**，该例自本页开始并延续到下一页。）</span>

（会使第 $k$ 次成功恰好发生在时刻 $t$ 的）这一结果当且仅当下述两个事件 $A$ 与 $B$ 同时发生时才会出现：

- (a) 事件 $A$：第 $t$ 次试验是成功的；

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这段证明把 $\{Y_k=t\}$ 拆成两块：$A=\{X_t=1\}$，即第 $t$ 个时隙是成功；$B$ 是「前 $t-1$ 个时隙里恰有 $k-1$ 次成功」这个事件。两块都能直接算：$P(A)=p$，$P(B)=\binom{t-1}{k-1}p^{k-1}(1-p)^{t-k}$，相乘即得目标式。
>
> 独立性的来源要说清，不能只写「显然无关」。$A$ 只涉及第 $t$ 个时隙，$B$ 只涉及第 $1$ 到 $t-1$ 个时隙，两个时隙集合不相交；伯努利过程的定义要求任意不相交时隙集合上的事件独立，这才是可以相乘的依据。同一条性质在本节已经用了三次，分别是注 9 的忙闲期独立、注 11 的间隔独立，以及此处，值得单独记住：**独立性总是靠「不相交的坐标块」来兑现**，而不是靠直觉。
>
> 我叫它末位剥离法：先钉住「最后一个位置发生了什么」，再对前面的位置计数。适用范围很宽——凡是「第 $k$ 次某事件恰在某时刻」的问题，都先剥离最后一步，剩下的就退化成二项计数。二项式系数的递推 $\binom{n}{k}=\binom{n-1}{k-1}+\binom{n-1}{k}$ 的组合证明也是同一招：按元素 $n$ 是否被选中分类。这条技巧与分治里「按最后一个元素分类」是同一种分解方向。
>
> 旧注把它等同于 dynamic programming（动态规划）的「先定最后一步再递归计数」，方向对但精度不够。动态规划要的是 optimal substructure（最优子结构）与 overlapping subproblem（重叠子问题），这里既没有最优化也没有重复子问题，只有一次计数分解。更准确的类比对象是组合计数里的 last-step decomposition，以及全概率公式按「最后一次成功的位置」分割。把两者混为一谈，会在需要真正做优化的问题上误用这条模板。
>
> 还有一条完全独立的验证路线：回到卷积。$T_i\ge1$ 且 $t_1+\cdots+t_k=t$ 的正整数解有 $\binom{t-1}{k-1}$ 个，这是 stars and bars（隔板法）的标准计数，而每个解的概率都是 $p^{k}(1-p)^{t-k}$，与具体的 $t_i$ 无关，乘起来就得到同一条 PMF。这条路线的额外收获是把组合数解释清楚了：它数的是「在 $t-1$ 个位置里挑 $k-1$ 个放成功」的方案数——最后一个位置已被钉死为成功，所以只在前 $t-1$ 个里挑。三条路线，即直接相乘、卷积计数、负二项级数，得到同一结果，这种交叉验证值得当成习惯。
>
> 最常见的写错是把组合数写成 $\binom{t}{k}p^{k}(1-p)^{t-k}$，即「$t$ 个位置里选 $k$ 个」。错在允许第 $t$ 个位置是失败，而那意味着第 $k$ 次成功早于 $t$，与事件 $\{Y_k=t\}$ 矛盾。这个错误很隐蔽：代入 $t=k$ 时两式都给 $p^{k}$，看不出差别；代入 $k=1$ 立刻露馅——正确式给 $(1-p)^{t-1}p$，错误式给 $t\,p(1-p)^{t-1}$，差一个因子 $t$。所以 $k=1$ 是检验这类错误的试纸。
>
> 边界校验再做两个。$t=k-1$ 时正确式给 $0$，因为 $\binom{k-2}{k-1}=0$，符合「$k$ 次成功不可能在 $k-1$ 步内完成」；$p=1$ 时只剩 $t=k$ 这一个原子，质量恰为 $1$。凡是能在这两个端点上通过检验的表达式，中间出错的可能性就小得多。
>
> 同一套分解在截断后仍然有效。Example 6.5 的 $Z=\min\{Y_6,30\}$：$z<30$ 直接取 Pascal 值，$z=30$ 把尾部全体压成一个原子。这是离散变量做 min 变换的标准手法——先算未被截断的部分，再用 $1$ 减求和补尾。手法本身与这个证明无关，但依赖同一个事实：$\{Y_k=t\}$ 对 $t\ge k$ 是一组互斥且穷尽的事件。
>
> 最后补一句这个证明隐含的前提：$\{Y_k=t\}$ 要构成划分，必须 $Y_k<\infty$ 几乎必然成立。教材在这里没有单独证，理由在注 10 那条（关于 stopping time（停时））里已经给过，用的是成块法：把时隙按 $(X_{2k-1},X_{2k})$ 成对分组，每块全成功的概率是 $p^2$，块与块独立，于是前 $m$ 块里至少一块全成功的概率 $1-(1-p^2)^m$ 趋于 $1$，成功因此无限次出现。若换一个 $p$ 依赖于时间的模型，这个前提会失效，那时 Pascal PMF 也不再归一化。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> splitting（分裂，也叫 thinning）是逐到达的独立挑拣：每个到达以概率 $q$ 保留、以 $1-q$ 丢弃，决策彼此独立。保留流在每个时隙出现到达的概率是 $pq$，丢弃流是 $p(1-q)$。教材把它当成新的一节的引子，但它其实是「逐时隙抛两枚硬币」的直接后果。
>
> 保留流仍是伯努利过程，要验两条。单时隙的边缘概率为 $pq$：到达且保留，两个独立事件相乘。跨时隙的独立性来自两处——原过程的时隙独立，加上决策序列的时隙独立。两条合起来才够，只验一条是常见遗漏：只验边缘概率，得到的是「每个时隙边缘相同的序列」，不足以称过程。
>
> 旧注在这里有一处数学错误要纠正。它说「两个流相互独立，因为每个时隙的保留/丢弃决策独立且互斥，两类事件分属不同的时隙序列，互不交叉」——后半句不成立：两类事件并不分属不同时隙，它们可以在不同时隙上任意重叠。而且结论也过强：两个子流在同一时隙上互斥，因此不可能按字面意义独立。
>
> 反例一行就够。设 $A_i$ 为「保留流在时隙 $i$ 有到达」，$B_i$ 为「丢弃流在时隙 $i$ 有到达」。则 $P(A_i\cap B_i)=0$（同一个到达不能被同时保留与丢弃），而 $P(A_i)\,P(B_i)=pq\cdot p(1-q)>0$。两者不等，独立性不成立。
>
> 正确的机制是 multinomial trial（多项试验）：每个时隙有「保留 / 丢弃 / 无到达」三种互斥结果，概率依次为 $pq$、$p(1-q)$、$1-p$，各时隙相互独立。要检验的独立性是「不同时隙之间」的因子化，例如 $i\ne j$ 时 $P(A_i\cap B_j)=pq\cdot p(1-q)=P(A_i)P(B_j)$，这一条成立。教材那句 independent 应读作后面这个意思：两个子流在互不相交的时隙集合上独立。图 6.3 的图注把结论说得更粗，写成「两个独立的伯努利过程」；按上面的反例，那个措辞只在「不相交时隙」这个限定下成立，严格表述应当是「两个伯努利过程，在不相交的时隙集合上独立」，记笔记时不要省掉后半句。
>
> 为什么连续版没有这个麻烦？因为泊松过程在一个点上出现两个到达的概率是零，「同一时刻互斥」这件事不产生正概率的约束。这是离散与连续在处理原子时的典型差别：时隙是原子的，时刻不是。教材在 §6.2 会不加限定地写「分裂后的两个泊松过程独立」，那句话在连续版里是干净的，把同一句话照搬到离散版就会出错。
>
> 一般化几乎不用改字。分成 $m$ 类、第 $i$ 类的保留概率为 $q_i$，且所有保留概率之和不超过 $1$，则第 $i$ 类构成参数为 $p\,q_i$ 的伯努利过程，各类在不相交时隙上独立，联合计数服从多项分布。这条是路由器按优先级分流、flow sampling（流采样）、A/B 测试按比例切流量的概率基础；后面 Example 6.7 处理噪声信道上的报文分组传输，用的正是它。
>
> 反方向是 merging（合并）：两条独立伯努利过程参数为 $p$ 与 $q$，叠加后每时隙至少有一个到达的概率是 $p+q-pq$，等于一减「两条都没有到达」的概率 $(1-p)(1-q)$。合并结果仍是伯努利过程，因为各时隙独立这条没有被破坏——合并操作只改变单时隙的边缘概率，不触及跨时隙结构。
>
> 分裂与合并不是一般意义上的互逆，这个边界要记住。先合并、再按固定概率 $q'$ 随便分裂，回不到原先的两条流；只有在「来源已知、且按与来源比例匹配的概率分流」时才能复原。多路复用系统里把这条搞混，会出现「分流后两路速率之和小于总速率」的静默错误。
>
> 期望层面做个守恒核算：$n$ 个时隙里保留数的期望是 $n\,p\,q$，丢弃数期望是 $n\,p(1-q)$，两者之和 $n\,p$ 恰是原流的期望到达数。合并方向的对应核算更弱一些：$E[\text{合并数}]\le np+nq$，等号差的那一项 $npq$ 正是两个流在同一时隙重复到达的期望次数——这也解释了为什么合并概率里要减去 $pq$。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 决定「保留或丢弃」的那句话在源 OCR 中被拆成零词（仅余「choose to」「it (with probability …)」「1−q」等残片），上句按分裂过程的标准表述重排：保留概率 $q$、丢弃概率 $1−q$，二者形成「保留的到达」与「丢弃的到达」两类流。</span>

出于同样的原因（for the same reason），被丢弃的到达也构成一个伯努利过程，其到达概率（with a probability）为 $p(1-q)$。

<span style="color:#7f8c8d;">**[图] Fig. 6.3**</span> <span style="color:#00838f;">**图 6.3　伯努利过程的分裂（Splitting of a Bernoulli Process）**</span>

> <span style="color:#7f8c8d;">图 6.3 展示：一个到达概率为 $p$ 的伯努利过程，其每次到达独立地以概率 $q$ 被保留进「保留」流、以概率 $1-q$ 被丢弃，从而分裂成两个伯努利过程（参数分别为 $pq$ 与 $p(1-q)$），它们在不相交的时隙集合上独立。</span>

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


```math
E[Z] = \lambda .
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本页 OCR 只剩 $E[Z]=\lambda$ 一行，推导要自己补。设 $Z$ 服从参数为 $\lambda$ 的 Poisson distribution（泊松分布），则 $E[Z]=\sum_{k\ge0}k\,e^{-\lambda}\lambda^{k}/k!$。$k=0$ 项为零，$k\ge1$ 时从 $k$ 与 $\lambda^{k}$ 里各取一个因子，得 $\lambda e^{-\lambda}\sum_{k\ge1}\lambda^{k-1}/(k-1)!$，指标平移后内层正是 $e^{\lambda}$，于是 $E[Z]=\lambda$。「分子分母相消」这个说法要落到这一步才算说清：消掉的不是 $\lambda$，而是 $k$ 与 $\lambda^{k}$ 各贡献的一个因子。
>
> 方差不必硬算 $E[Z^{2}]$，用 factorial moment（阶乘矩）更省。$E[Z(Z-1)]=\lambda^{2}\sum_{k\ge2}\lambda^{k-2}/(k-2)!=\lambda^{2}$，于是 $\mathrm{var}(Z)=E[Z^{2}]-(E Z)^{2}=\lambda^{2}+\lambda-\lambda^{2}=\lambda$。这条技巧对所有幂级数型分布都好用，因为它把「$k^{2}$ 的求和」换成了「指标平移两次」，避免了对发散级数做分部求和。
>
> 更一般的陈述是：$E[(Z)_r]=\lambda^{r}$，其中 $(Z)_r=Z(Z-1)\cdots(Z-r+1)$ 是 falling factorial（下降阶乘）。也就是说，泊松分布的全部阶乘矩都等于 $\lambda^{r}$。这条性质是它的 signature（签名），probability generating function（概率生成函数）$G(z)=E[z^{Z}]=e^{\lambda(z-1)}$ 的展开系数直接给出这些矩；对 $z$ 求导两次再取 $z=1$，得到的也正是上面两个式子。
>
> 均值等于方差不是巧合，而是 equidispersion（等散布）。对照二项分布：均值 $np$，方差 $np(1-p)$，方差严格小于均值，这叫 underdispersion（欠离散）。而当 $p\to0$ 且 $np\to\lambda$ 时，$np(1-p)\to\lambda$，方差追上均值——泊松正是稀有事件处的极限形态。旧注说「$p$ 大时方差远小于均值」，话本身没错，$p=1$ 时方差为 $0$，但重点该放在稀有事件那一头，否则读者会误以为等散布是「$p$ 取中间值」的性质。
>
> 等散布可以用数据检验，这是它最实用的地方。样本方差与样本均值之比，即 index of dispersion（离散指数），显著大于 $1$ 就提示 overdispersion（过离散），说明数据比泊松更集中成簇；显著小于 $1$ 则是欠离散，常见于有上限的计数。真实网络流量、请求到达、垃圾回收停顿都呈现过离散，这就是「泊松假设在突发流量下失效」的定量入口，比空泛地说「流量有相关性」有用。
>
> 可加性是另一条签名性质：若 $Z_1\sim\mathrm{Poisson}(\lambda_1)$ 与 $Z_2\sim\mathrm{Poisson}(\lambda_2)$ 独立，则 $Z_1+Z_2\sim\mathrm{Poisson}(\lambda_1+\lambda_2)$。连续版的对应命题是「独立泊松过程之和仍是泊松过程」，它是 queueing network（排队网络）分析的基础——把多条输入流叠加，再当作一个参数相加的流来处理，前提就是这条。
>
> PMF 的递推是 $p(k+1)=p(k)\cdot\lambda/(k+1)$，从 $p(0)=e^{-\lambda}$ 起步。由此还能读出众数：比值大于 $1$ 当且仅当 $k+1<\lambda$，所以众数是 $\lfloor\lambda\rfloor$，$\lambda$ 取整数值时则 $\lambda-1$ 与 $\lambda$ 并列。数值实现上要小心：大 $\lambda$ 时 $e^{-\lambda}$ 在双精度里先跌到可表示范围的边缘，$\lambda$ 超过约 $745$ 之后直接归零，于是整条 PMF 全部变成 $0$。正确做法是在对数空间累加，即用对数伽马函数算 $\log p(k)$，需要概率时再取指数。
>
> 采样有两条路线，按 $\lambda$ 的量级选。乘法法即 Knuth 的经典做法：每次乘一个 uniform random number（均匀随机数），直到乘积小于 $e^{-\lambda}$。设停止时已经抽了 $N$ 个，则 $N-1$ 服从参数为 $\lambda$ 的泊松分布，所以循环次数满足 $E[N]=\lambda+1$，而返回的那个计数 $K=N-1$ 的期望才是 $\lambda$。模拟给出的正是这个量级：$\lambda=1$ 时 $E[N]\approx1.9982$、$\lambda=3$ 时 $\approx4.0021$，都贴着 $\lambda+1$ 而不是 $\lambda$。$\lambda$ 小时这套足够；$\lambda$ 大时应换成 rejection sampling（拒绝采样）或对 normal approximation（正态近似）做修正，否则循环次数会变成瓶颈。一套代码通吃两种量级，往往是性能问题的来源。
>
> 与二项分布的关系值得明说：泊松分布是 $\mathrm{Bin}(n,\lambda/n)$ 在 $n\to\infty$ 时的极限，也就是下一条注的定理。因此可以把泊松计数读成「时隙无穷多、每格成功概率无穷小」的极限图像——这正是连续时间泊松过程里 $N(t)\sim\mathrm{Poisson}(\lambda t)$ 的来源，也是它的均值随时间线性增长的原因。理解这一层，后面连续版的推导只是把时隙宽度趋于零。
>
> 一条使用纪律：泊松是单参数模型，均值定了方差就定了，没有调节余地。所以正确顺序是先算样本方差与均值、再决定能不能用；反过来做，先假设泊松、再用同一批数据「确认」，会把过离散掩盖在均值的抽样噪声里，这是统计建模里最常见的自欺。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 定理的准确形式是逐点收敛：对每个固定的非负整数 $k$，当 $n\to\infty$ 且 $p=\lambda/n$（$\lambda$ 固定）时，$p_S(k)\to e^{-\lambda}\lambda^{k}/k!$。「$k$ 固定」是定理的一部分，不是技术上的方便——若 $k$ 随 $n$ 一起长，结论会失效，那时要用 local central limit theorem（局部中心极限定理），得到的是带高斯修正的形态。
>
> 三个因子各自的极限都有依据。阶乘比等于 $\prod_{j=0}^{k-1}(1-j/n)$，是 $k$ 个因子的乘积，每个趋于 $1$；$(1-\lambda/n)^{n}\to e^{-\lambda}$ 是标准极限；$(1-\lambda/n)^{-k}\to1$ 因为 $\lambda/n\to0$。逐因子取极限再相乘之所以合法，靠的是「有限个收敛数列之积收敛到积」——这正是 $k$ 必须固定的原因：$k$ 固定，因子个数才有限，极限运算才能逐项做。
>
> 旧注把这条模板叫三因子拆分法，概括准确，可以再补一层记账。三个因子里只有第二个是真极限，第一与第三都只是趋于 $1$ 的修正项。把误差写成显式：第一项的偏差是 $-\frac{k(k-1)}{2n}+O(n^{-2})$，第三项是 $\frac{k\lambda}{n}+O(n^{-2})$，两者加上 $(1-\lambda/n)^{n}$ 相对 $e^{-\lambda}$ 的 $O(1/n)$ 偏差，合起来就是泊松近似误差的量级 $O(1/n)$。
>
> 关键限定：这是逐点收敛，不是一致收敛。想用泊松近似去算总概率（例如「概率之和」或尾概率），需要 total variation（全变差）意义下的界。Le Cam（1960）给出 $\|\mathrm{Bin}(n,p)-\mathrm{Poisson}(np)\|_{TV}=O(np^{2})$，常用的显式形式是 $2np^{2}$，具体常数因文献版本而异。有了它，Example 6.6 的经验法则就有定量根据：$n\ge100$、$p\le0.01$，且 $\lambda=np\le1$ 时 $2np^{2}=2\lambda p\le0.02$；缺了 $\lambda\le1$ 这一条，界就不成立，例如 $n=10^{6}$、$p=0.01$ 会给出 $2np^{2}=200$，比 $1$ 大得多。
>
> 这条定理的意义不是「省一次计算」，而是稀有事件的 universality（普适性）：只要 $n$ 大、$p$ 小、$np$ 固定，极限只有一个，与具体的 $n$ 和 $p$ 无关。它和中心极限定理是姐妹：中心极限定理处理「和的涨落」，泊松极限处理「稀有计数的分布」，两条极限分工不同，谁也替代不了谁。
>
> 分界可以用尺度说清。$p$ 固定时，$S_n$ 的涨落尺度是 $\sqrt{np(1-p)}$，中心极限定理成立；$p\to0$ 且 $np\to\lambda$ 时，涨落尺度退化为常数 $\sqrt{\lambda}$，中心极限定理给不出信息，泊松极限接管。把 $(\lambda,p)$ 平面画出来，两个区域的分界落在「$\sqrt{np}$ 是否远大于 $1$」这条线上。
>
> 最常见的误用是只记住「$n$ 大」，忘了「$p$ 小」。反例：$n=10^{6}$、$p=0.5$ 时 $\lambda=5\times10^{5}$，二项的标准差约 $500$，而泊松的标准差约 $707$，两者的形状都接近正态，但尺度差了四成，泊松近似没有意义。判据是 $np^{2}$ 是否小，而不是 $n$ 是否大——这一点看 Le Cam 的界一目了然。
>
> 历史要写准。Poisson 1837 年在《关于刑事案件与民事案件判决概率的研究》（Recherches sur la probabilité des jugements en matière criminelle et en matière civile，Paris: Bachelier）里给出这个分布，处理的是「陪审团误判次数」这类稀有计数，不是为近似二项分布而写。把它与真实数据对上的是 Bortkiewicz 1898 年的小册子《小数目定律》（Das Gesetz der kleinen Zahlen），用的是普鲁士军队骑兵被马踢死的数据——「稀有事件定律」这个名字从那里来，而不是从 Poisson 本人来。
>
> 算法分析里的典型用处在 balls and bins：$n$ 个球投进 $n$ 个桶，每桶装载数近似服从参数为 $1$ 的泊松分布，由此得到最大装载为 $\Theta(\log n/\log\log n)$（CLRS 第三版 §5.4 一类的内容，⚠ 版本不同章节号会有偏移）。严格证明多走一步 Poissonization（泊松化）：先把固定的 $n$ 换成泊松随机数，独立性变好、计算变简单，算完再还原回固定 $n$ 的情形。
>
> 工程上的用法集中在「稀有事件计数」：单位时间的错误数、垃圾回收停顿次数、缓存击穿次数、样本中的坏点个数。这类量满足「次数多、单次概率小」，正是泊松近似的适用区间；反过来，一旦观测到方差远大于均值，就该换负二项或混合模型，而不是硬套泊松。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这张对照表真正要回答的问题不是「泊松近似准不准」，而是「准不准该用哪个数来衡量」。rule of thumb（经验法则）背下来快、忘得也快；能自己算出误差的人，遇到新场景（$n=10^{6}$、$p=10^{-6}$，或者 $n=20$、$p=0.05$）才知道还能不能用。
>
> 先做一件可以手算的事：写出逐点比值。把 binomial distribution（二项分布）的 probability mass function（概率质量函数）与 Poisson distribution（泊松分布）在同一点相除，组合系数被 $n^{k}$ 换掉、指数项被 $e^{\lambda}$ 抵掉，取对数后只剩三项：$\log\frac{p_X(k)}{p_Z(k)} \approx kp - \frac{\lambda p}{2} - \frac{k(k-1)}{2n}$。三项各有名字。$-\lambda p/2$ 是 collision（碰撞）项，管「同一格里挤进多次成功」被合并掉的部分；$+kp$ 是 thinning（稀疏化）项的补偿，因为每格只有一次机会，成功过的格子不能再中；$-\frac{k(k-1)}{2n}$ 是 sampling without replacement（无放回抽样）折扣，形状与 birthday problem（生日问题）里那个因子完全相同。
>
> 代真数验一遍。$n=100$、$p=0.01$、$\lambda=1$、$k=10$ 时三项分别是 $0.1$、$-0.005$、$-0.45$，合计 $-0.355$；实测对数是 $-0.3695$，比值 $0.691$。也就是说在 $k=10$ 这一点，binomial distribution（二项分布）只有 Poisson distribution（泊松分布）的七成，并不「吻合得相当好」。主导的是第三项，它按 $k^{2}$ 增长，所以误差集中在尾部而不在中心。
>
> 这里必须指出现行表格的一处数值问题：表中 $p_Z(10)$ 写作 $1.001\times10^{-8}$，而 $e^{-1}/10! = 1.0138\times10^{-7}$，相差整整十倍。若照表里的 $1.001\times10^{-8}$ 去比，$p_X(10)=7.006\times10^{-8}$ 反倒比泊松值大七倍，结论会整个翻转成「泊松严重低估尾部」。以 $1.0138\times10^{-7}$ 为准，正确结论是「泊松高估尾部约 $45\%$」。⚠ 需回查原书印刷值。
>
> $n=5$、$p=0.1$ 那一组把三项同时放大：比值在 $k=3$ 掉到 $0.641$、$k=5$ 掉到 $0.063$。用 total variation distance（全变差距离）量一下，两组分别是 $0.0028$ 与 $0.0248$，差约九倍。这个量正好落在 Le Cam's inequality（Le Cam 不等式）的射程内：独立 Bernoulli random variable（伯努利随机变量）之和与同均值的 Poisson distribution（泊松分布）之间，$\sum_k |p_X(k)-p_Z(k)| \le 2\sum_i p_i^{2}$，等概率时右边等于 $2\lambda p$。代入得 $0.02$ 与 $0.1$，方向正确但界很松：后者是实测全变差 $0.0248$ 的约 $4$ 倍（$0.1/0.0248=4.03$），若按 $L_1$ 距离比则是 $2$ 倍。界松也仍然有用，因为它指认了唯一该记的小参数——$\lambda p$，而不是 $n$ 或 $p$ 单独。
>
> 于是经验法则的三条里，起决定作用的是那个小参数 $\lambda p$，三条缺一不可。$n\ge100$ 与 $p\le0.01$ 只给出 $p$ 的上限，还要再加 $\lambda=np\le1$ 这一条，三条合起来才保证 $\lambda p = np^{2}\le0.01$——缺了 $\lambda$ 那条就什么都得不到，例如 $n=10^{6}$、$p=0.01$ 给出 $np^{2}=100$。而 $\lambda$ 适中的那一条，教材例题几乎都取 $\lambda\approx1$，保证的是你关心的 $k$ 落在 $\lambda\pm3\sqrt{\lambda}$ 以内，因为 $-\frac{k(k-1)}{2n}$ 只在 $k$ 远大于 $\sqrt{n}$ 时才咬人。换成一句更好记的判据：先算 $\lambda p$，$\lambda p<0.01$ 时中心几个点的相对误差在千分之几，$\lambda p>0.1$ 时不要拿这张表说话。
>
> 想要一个比 Le Cam's inequality（Le Cam 不等式）更紧、又能手算的一阶估计，换成 effective rate（有效速率）的写法：把 probability mass function（概率质量函数）整体写成 $(1-p+pz)^{n}$ 取对数，它等价于参数 $\nu = -n\ln(1-p)$ 的 Poisson distribution（泊松分布）近似，而 $\nu - \lambda = \frac{np^{2}}{2} + \frac{np^{3}}{3} + \cdots$。两组数字立刻有了可比性：$\nu = 1.00503$ 对 $\lambda = 1$，相对差 $0.5\%$；$\nu = 0.52680$ 对 $\lambda = 0.5$，相对差 $5.4\%$。差十倍，正好对上 total variation distance（全变差距离）差九倍的那个事实。这条式子的用处不止估算：它一次性解释了经验法则里那个凭空出现的 $p\le0.01$——相对误差的一阶项就是 $\lambda p/2$，要让它在百分之一以内，只能要求 $\lambda p\le0.02$。
>
> 跨课程连接两处。CLRS 里的 asymptotic notation（渐近记号）教你把量纲先找对再谈系数，这里读 $\lambda p$ 与读 $-\frac{k(k-1)}{2n}$ 是同一套动作。CSAPP 第 3 章的 floating point（浮点）一节提醒过，相对误差在小量上被放大：$k=10$ 处三成偏差就是「同一个绝对误差落到小概率上变成大相对误差」的实例，所以「吻合得相当好」这句只在 $k\le5$ 一带成立。
>
> 收束回正文：这张表不是用来背的，是用来自查的。以后看到任何「某近似很好」的断言，先问三件事——误差用什么模量、误差的主项是谁、它在哪一段失效。


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


```math
n < -\,\frac{\ln 0.999}{0.0001} = 10.005 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上式中分母 $0.0001$、负号及结果 $10.005$ 在 OCR 中被拆散，此处按条件 $1-e^{-\lambda}<0.001$ 的标准算法重建，数值一律未改动。</span>

由于 $n$ 必须是整数（n must be an integer），两种方法都归结到同一结论：$n$ 至多只能取 $10$。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Poisson approximation（泊松近似）这个说法容易被当成魔术，其实它只有一个来源：$(1-x/n)^{n}\to e^{-x}$ 这条极限。把符号对上——单个符号传输出错的概率是 $p$，数据包有 $n$ 个符号，于是「一个符号都不错」的概率是 $(1-p)^{n}$，而 Poisson approximation（泊松近似）把它换成 $e^{-\lambda}$，其中 $\lambda = np$。这一步的合法性只要求 $p$ 随 $n$ 一起变小、$\lambda$ 保持固定，除此之外不需要任何东西。
>
> 两条路线为什么差一个零头，可以逐字算出来。精确路线：$1-(1-p)^{n}<0.001$ 等价于 $(1-p)^{n}>0.999$，取对数后因为 $\ln(1-p)<0$，不等号要翻转，得 $n<\frac{\ln0.999}{\ln0.9999}=10.0045$。近似路线：$1-e^{-\lambda}<0.001$ 等价于 $\lambda<-\ln0.999=1.0005\times10^{-3}$，除以 $\lambda=np$ 得 $n<10.0050$。两条路差 $0.0005$，取整之后同为 $n\le10$，所以答案不受影响，但这个零头本身有信息。
>
> 方向不是巧合，一行就能证明。对 $u\in(0,1)$ 有 $\ln(1-u)<-u$，于是 $(1-p)^{n}=(1-\lambda/n)^{n}<e^{-\lambda}$ 对每个 $n$ 严格成立。左边更小意味着「零错误」更稀罕，「至少一次错误」的概率更大，所以真实的传输失败概率高于 Poisson approximation（泊松近似）给出的值。用它当判据就是 conservative（保守）方向：它要求更小的 $n$，实际执行起来一定达标。这条严格不等式不依赖 $p$ 小，可以直接当定理用。
>
> 差值的量级同样可以算。换成 effective rate（有效速率）$\nu=-n\ln(1-p)$ 来看，$\nu-\lambda$ 的主项是 $n p^{2}/2$，代入 $n\approx10$、$p=10^{-4}$ 得 $\Delta\lambda=5\times10^{-8}$。这个量相对 $\lambda\approx10^{-3}$ 只有 $5\times10^{-5}$，但换算成对阈值 $n$ 的影响要乘 $1/p=n/\lambda\approx10^{4}$，因为 $\lambda=np$ 意味着 $n=\lambda/p$：$5\times10^{-8}\times10^{4}=5\times10^{-4}$，恰好就是前面那条阈值差。一个 $10^{-8}$ 量级的率误差被放大成 $10^{-4}$ 量级的阈值差，这是「小误差在条件数大的地方被放大」的标准样本，比任何抽象说法都具体。
>
> 复利视角能把这条极限挂到熟悉的东西上：$(1+r/n)^{n}\to e^{r}$ 是离散复利的连续化，这里只是把利率 $r$ 换成 $-\lambda$，读成「负利率」或「每秒存活率」即可，$e^{-\lambda}$ 就是连续复利下的存活折扣。同一个极限在 18.06 里会以矩阵形式回归：matrix exponential（矩阵指数）$e^{At}$ 的定义正是 $(I+At/n)^{n}$ 的极限，标量换成 matrix（矩阵）之后不需要额外技巧，因为只涉及 $A$ 一个矩阵、幂次之间可交换；唯一的差别是收敛要在 operator norm（算子范数）意义下说，而不是逐点的。
>
> 工程上什么时候可以直接把 $(1-p)^{n}$ 换成 $e^{-\lambda}$，有一个可操作的门槛：两者的相对差约等于 $\lambda p/2$。本题 $p=10^{-4}$、$\lambda\approx10^{-3}$ 时这个差是 $5\times10^{-8}$，可以放心替换；反过来，若取 $p=0.05$、$\lambda=2$，此时 $n=40$，相对差约 $5\%$，再用 $e^{-\lambda}$ 就会在第三位小数上出错。判据一句话：先算 $\lambda p$，小于 $0.01$ 直接换，大于 $0.01$ 就老老实实用 $\nu=-n\ln(1-p)$。
>
> 还有一处容易滑过去的细节：两条路线给出的阈值都是实数，而真正能取的是整数 $n\le10$。这一步整数化把连续比较变成离散决策，误差最大可达一整个单位，所以判据不是「两条路线差多少」，而是「阈值离下一个整数有多远」。$10.0045$ 距离 $11$ 还有将近一个整单位，取 $10$ 是稳的；假如算出的是 $10.9$，同样量级的近似就足以把答案从 $10$ 翻成 $11$，那时必须回到精确式。作业与考试里「近似导致答案翻转」的事故，几乎都发生在阈值贴着整数的时候。
>
> 跨课程连接两处。CSAPP 第 3 章的 floating point（浮点）一节讲相对误差，这里的 $\lambda p/2$ 正是「被丢掉的高阶项有多大」的量化答案，与 ulp（单位舍入误差）是同一类记账方式。6.042J 里把 $e$ 当作「$n$ 步、每步 $1/n$ 的极端情形」引入，做题时只关心阶；这里是它的定量版本，关心系数。
>
> 收束回正文：这条注的重点不是「记住 $e$ 的定义」，而是把「近似」变成一个带方向、带误差量的断言——写成不等式，才知道自己在安全的一侧还是危险的一侧。

---

<span style="color:#c0392b;">**§6.2　泊松过程（The Poisson Process）**</span>

泊松过程（Poisson process）是伯努利过程（Bernoulli process）在连续时间（continuous time）下对应的版本，适用于那种没有自然而然的方法把时间划分成离散区间的情形。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一句是全书最重要的模型替换之一，它回答的问题不是「泊松过程怎么定义」，而是「为什么非要有第二个模型」。要看懂这句话，先看清 Bernoulli process（伯努利过程）缺什么。
>
> 缺的不是精度，是自洽性。把一小时切成六十个分钟格、每格只记「有没有事故」，这个 Bernoulli process（伯努利过程）能回答「一百分钟里有几格出过事故」，却答不了两件事。第一，同一分钟里的第二起事故被吞掉，而现实里连撞三车的事故恰恰是最要紧的那类。第二，更致命：$P(k,\tau)$ 对 $\tau$ 没有稳定含义——换成一秒、一毫秒，格子数变了，每格的成功概率也得跟着变，你永远说不清哪一个才是「真实发生率」。
>
> 用数字把第二点钉死。设真实强度是每小时两起，取分钟格则每格概率 $1/30$，六十格的 expectation（期望）是 $2$；取秒格则每格 $2/3600$，三千六百格的 expectation（期望）仍是 $2$。但 variance（方差）不一样：分钟格给出 $1.9333$，秒格给出 $1.9989$——后者的算法是 $3600\cdot(2/3600)\cdot(1-2/3600)=1.998889$，网格越细越逼近 $2$。同一个物理过程，均值对网格免疫、方差却把网格暴露出来——这说明模型里藏着一个你从没打算引入的参数 $\delta$，而它不该出现在答案里。
>
> 「那就再切细一点」不是解法，因为它只是把同一个问题换个尺度重复一遍：任何尺度上都能问「要不要更细」，而没有任何尺度是自然给定的。再切细还会把边界效应放大——总会存在两次事故落在同一格内，只是概率变小，于是模型的误差永远取决于你随手选的 $\delta$，这在工程上不可接受。
>
> 极限这一步做的不是「更细的格子」，而是把格子这个参数整个消掉：让 $P(k,\tau)$ 成为 $\tau$ 的连续函数，只依赖长度不依赖划分。数学上的代价是下一页那条 $o(\tau)$ 条件，收益是把「同时刻两次到达」的概率压到 $0$，于是「数了几次」与「什么时候发生」可以分开处理——这是后面所有计算的支点。
>
> 这一步在分析学里有标准名字：partition（划分）先细到 mesh（网格直径）趋于零，再谈极限。你在实分析里已经用过同样的动作——Riemann integral（黎曼积分）就是「任取划分、取 mesh（网格直径）趋于零、证明极限与划分无关」；CSAPP 里用固定频率 sampling（采样）近似连续信号，则正好展示了不做这一步的代价：采样率不够时高频被折叠成低频，而模型本身不会报警。6.042J 那边是把递归结构翻成闭式，动作相同：消掉一个不该出现在答案里的参数。
>
> 值得单独记一句：连续模型往往不是「更复杂」而是「更少参数」。带两个参数的是有限 $n$ 次试验的 binomial model（二项模型），Bernoulli process（伯努利过程）本身只由 $p$ 参数化，$n$ 只是你观察了多久；Poisson process（泊松过程）只剩一个 $\lambda$，因为 $n$ 被取极限吃掉了。参数越少，可被数据否证的空间越大，这也是为什么「到达像不像泊松」在实践中能真的被检验，而不是变成一句无法反驳的描述。
>
> 收束回正文：这句「适用于没有自然离散化的场合」不是修辞。它说的是一件具体的事——离散化本身要付出一个额外参数，而那个参数无法由数据确定。


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

- (b) （独立性 Independence）特定区间内到达的次数，与这一区间之外到达的历史（history）无关。
- (c) （小区间概率 Small interval probabilities）概率 $P(k, \tau)$ 满足

```math
\begin{aligned}
P(0, \tau) &= 1 - \lambda\tau + o(\tau),\\
P(1, \tau) &= \lambda\tau + o(\tau),\\
P(k, \tau) &= o_k(\tau), \qquad \text{对 } k = 2, 3, \ldots \text{成立}.
\end{aligned}
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> $o(\tau)$ 不是「很小」的修辞，而是一条可检验的极限断言：$o(\tau)/\tau\to0$。定义里非要写它而不是写 $\approx$，是因为后面要把这个误差乘上 $n=T/\delta$ 个格子——只有 little-o notation（小 o 记号）才保证乘完仍然趋零。
>
> 先把累积机制算清楚。把 $[0,T]$ 切成 $n=T/\delta$ 段，每一段「至多一次到达」失败的概率是 $\sum_{k\ge2}P(k,\delta)$，而每个 $P(k,\delta)=o_k(\delta)$。于是「至少一段出问题」的概率不超过 $n$ 倍的单段失败概率，量级是 $\frac{T}{\delta}\cdot o(\delta)$。这个式子必须趋于 $0$，也就是要求 $\frac{o(\delta)}{\delta}\to0$——定义里那条极限条件正好是为它准备的。若换成「误差 $=O(\tau)$」，即误差至多是 $\delta$ 的某个常数倍，则 $\frac{T}{\delta}\cdot O(\delta)=T\cdot O(1)$，无论 $\delta$ 多小都消不掉。这就是 $o$ 与 $O$ 在这里不能混用的原因：$o$ 的除法能吃掉一个 $\delta$，$O$ 不能。
>
> 下标 $k$ 也有实质含义。$o_k(\tau)$ 里的 $k$ 表示「对每个固定的 $k$ 各有一条函数」，它允许不同的 $k$ 有不同的收敛速度；而把 $k\ge2$ 的无穷多项加起来时，需要额外的控制才能保证和仍是 $o(\tau)$。对泊松过程这条成立，但这不是记号自动给的，是可以被破坏的——若在极短区间内可能出现任意多次到达，求和就会失控，这也是上一页 (c) 那条禁止 bulk arrival（批量到达）的假设真正在防的东西。
>
> 还要看清定义故意写弱了。正文说 $o(\tau)$ 可以看作 Taylor expansion（泰勒展开）里的 $O(\tau^{2})$ 项，那是更强的条件：$O(\tau^{2})$ 蕴含 $o(\tau)$，反之不成立。举一个具体的：若某过程的 $P(2,\tau)=3\tau^{1.5}$，则 $P(2,\tau)/\tau=3\tau^{0.5}\to0$，满足 $o(\tau)$；但它不是 $O(\tau^{2})$，因为 $\tau^{1.5}/\tau^{2}=1/\tau^{0.5}\to\infty$。这样的过程依然被定义接纳，且切段后误差 $\frac{T}{\delta}\cdot3\delta^{1.5}=3T\delta^{0.5}\to0$ 照样收敛。定义只取它需要的那一档，定理因此覆盖更多模型——公理写弱一点、结论反而更强，这是数学里反复出现的取舍。
>
> 紧接着要防一个误解：$o(\tau)$ 保证「取极限后消失」，不保证「取到你手上的 $\delta$ 已经够小」。仍旧用上面那个 $3\tau^{1.5}$ 的例子，$T=1$、$\delta=10^{-3}$ 时累计失败概率是 $3\delta^{0.5}=0.0949$，接近一成；要把它压到百分之一，需要 $3\delta^{0.5}\le0.01$，即 $\delta\le1.1\times10^{-5}$。也就是说差两个数量级的网格，才换来一个能接受的误差。极限记号给的是定性保证，工程上必须自己把 $\delta$ 解出来——这正是「近似只有带上误差界才有意义」那句话的具体形态。
>
> 与算法分析里的记号对照着记，才不会串味。CLRS 里的 $O(g(n))$ 面对的是 $n\to\infty$，说的是「增长不超过 $g$ 的常数倍」，用的场合是复杂度上界；这里的 $o(\tau)$ 面对 $\tau\to0$，说的是「与 $\tau$ 相比趋于零」，用的场合是误差预算。两者是同族符号，但极限点相反，一个看大、一个看小；关心的问题也不同，一个问「要多少资源」，一个问「误差能不能被消掉」。CSAPP 里讲浮点误差时用 ulp（单位舍入误差）做单位，思路与这里一致：误差必须写成一个可比较的量，才谈得上「可忽略」。
>
> 操作层面的判据只有一条：看到 $o(\tau)$，立刻问「下一步除以 $\tau$ 还是乘以 $n$」。如果接下来的推导既不除也不乘，这个记号就是空转；一旦除了，它就会变成一个干净的 $0$。这条习惯养成之后，连续概率里所有「先局部线性化、再整体取极限」的证明都能一眼看出骨架。
>
> 收束回正文：三条式子里真正携带信息的是误差项的形状，不是主项 $\lambda\tau$。主项告诉你平均每分钟来几个人，误差项告诉你这个「平均」能被信任到什么尺度。


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
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这三条不是「泊松过程恰好具有的性质」，而是它的定义，也就是判据：任何一个 arrival process（到达过程）只要满足 (a)(b)(c)，就必然是速率为 $\lambda$ 的泊松过程，下一页的推导只以这三条为输入。所以读这一段要换个姿势——不是在记结论，是在读一张「检验清单」。
>
> (a) time homogeneity（时间齐次性）翻译成离散语言，就是「每次试验成功的概率相同」。它只说 $P(k,\tau)$ 与区间的起点无关，不涉及任何时刻的联合分布，因此它比「平稳」要弱：平稳性还要约束不同时刻取值的联合规律，这里只约束单个区间的边际。
>
> (b) independent increments（独立增量）在正文里写成「区间外的历史无关」，严格说法是：任意有限个互不相交区间上的到达次数联合 independent（独立）。这里最容易出错的地方是把「互不相交」读成「不嵌套」——两个区间可以相隔很远，也可以不相邻，只要不重叠就行；而嵌套的两个区间显然不独立，因为大的区间包含小的区间。判断一个真实数据流是否满足这条，看的是有没有聚簇：暴雨天事故扎堆，就是不同时段不再独立的信号。
>
> (c) small interval probability（小区间概率）才是定义的核心，前两条只提供框架。把三条式子合起来看：$P(0,\tau)+P(1,\tau)=1-o(\tau)$，意思是「足够短的区间里至多一次到达」；而 $k\ge2$ 那一行 $o_k(\tau)$ 是真正的内容，它禁止 bulk arrival（批量到达）——不允许一个瞬间涌进两辆车。若把这一条放开，得到的是 compound Poisson process（复合泊松过程），每一次到达自带一个随机的大小，排队论里的「一批顾客同时到」正是这种模型。换句话说，(c) 用一个 $o(\tau)$ 把模型钉在了「一个一个来」这一侧。
>
> 要确认这三条只在 $\tau$ 小的时候有内容，代数字即可。取 $\lambda=0.2$ 每小时：$\tau$ 等于一分钟时 $\lambda\tau=0.0033$，$P(2,\tau)$ 约 $5.6\times10^{-6}$，确实是更高阶的小量；$\tau$ 等于一小时时 $\lambda\tau=0.2$，而 $P(k\ge2,\tau)=1-e^{-0.2}(1+0.2)=0.0175$，它显然不是 $o(1)$。所以 (c) 只在局部提供等式，大区间上的一切结论必须由 (a)(b) 加上 (c) 推出——这就是下一页「切段取极限」的全部工作。
>
> 三条之间不能互相替代，这一点值得看清。(c) 只约束 $\tau\to0$ 的局部行为，管不到长区间；(a) 管的是区间长度相同的两组之间是否同分布，管不到独立性；(b) 管的是不同区间之间是否互不影响，管不到单个区间的分布形状。三条各自只负责一个维度，合起来才唯一确定 $P(k,\tau)$。
>
> 从方法论上说，这是一种非常省力的定义方式：公理越弱越容易检验，代价是必须另证一个唯一性定理。实分析里你见过同样的结构——测度的定义只要求可数可加与规范性，所有具体性质都靠定理推出来；CSAPP 里接口与实现分离也是同一件事，只要接口约定成立，实现细节可以完全不同。6.042J 讲的「等价刻画」在这里表现为：同一个对象可以有极限面孔，即伯努利过程的极限；可以有公理面孔，即这三条；还可以有公式面孔，即下一页的泊松概率质量函数。三副面孔可以互相验算。
>
> 收束回正文：拿到一条到达数据时，检验清单就是这三条——看强度是否随时间漂移（(a)）、看有没有聚簇（(b)）、看有没有同一时刻的批量到达（(c)）。三条都过，才配用泊松公式。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这是本节的心脏公式，也是全书最值得背下来的一段推导模板。三步固定：把 $[0,T]$ 等分成 $n=T/\delta$ 段；每段至多一次到达，于是整段计数服从参数 $(n,\lambda\delta)$ 的 binomial distribution（二项分布）；再保持 $n\delta=T$ 不变、让 $\delta\to0$，二项概率质量函数逐点收敛到泊松概率质量函数。
>
> 第二步的合法性来自性质 (c)，第三步的关键则是「保持 $n\delta$ 固定」。这一条不能省：若固定每段概率 $p$ 不变而让 $n\to\infty$，$np$ 会发散，极限退化成正态而不再是泊松；若让 $p$ 缩得比 $\delta$ 快，$\lambda T\to0$，极限退化成一个质量全在 $0$ 的退化分布。只有当「段长与每段概率同步缩小」时，$\lambda$ 才保住「单位时间强度」的物理含义，$np=\lambda T$ 才是一个与网格无关的不变量。
>
> 收敛有多快可以算，而且算出来的答案很整齐。取 $\lambda=2$、$T=1$，$P(0,T)=(1-\lambda\delta)^{1/\delta}$ 在 $\delta=0.1,0.01,0.001,0.0001$ 时分别是 $0.107374$、$0.132620$、$0.135065$、$0.135308$，极限 $e^{-2}=0.135335$；对应误差 $2.8\times10^{-2}$、$2.7\times10^{-3}$、$2.7\times10^{-4}$、$2.7\times10^{-5}$。每把网格缩小十倍，误差就缩小十倍，这是一阶收敛，误差量级是 $\frac{(\lambda T)^{2}}{2n}=\frac{\lambda^{2}T\delta}{2}$。本题取 $\delta=10^{-3}$ 时它等于 $2\times10^{-3}$，比实测的 $2.7\times10^{-4}$ 大七倍左右——阶对、常数松，这正是误差界的常态。于是「要几位有效数字就切多细」变成一个可解的不等式：本题想要千分之一的精度，$\delta\le10^{-3}$ 就够。
>
> 这条推导与上一节的近似用的是同一个不等式。Le Cam's inequality（Le Cam 不等式）给 total variation distance（全变差距离）一个上界 $\sum_i p_i^{2}=n(\lambda\delta)^{2}=\frac{(\lambda T)^{2}}{n}$，与刚才算出的 $O(\delta)$ 完全同阶。区别在于：上一节里 $n$ 由数据给定，误差只能接受；这里 $n$ 是我们自己选的，可以任意大，所以极限是干净的。同一个界，一处当限制读，一处当工具读。
>
> 名字的来历只占一句：这个分布由 Siméon-Denis Poisson 在 1837 年的《Recherches sur la probabilité des jugements en matière criminelle et en matière civile》中首次写出显式形式，而处理的是「罕见事件」的极限——陪审团误判、事故这类每次概率极小、次数极多的事件；更早在 1712 年 de Moivre 近似二项分布时已经隐式得到它。记住这条脉络的用处不是背年份，而是理解「稀有事件的极限」才是这个公式的本体。
>
> 模板可复用的理由也在这里：凡是能找到一个 $\delta$ 使得「每 $\delta$ 内至多一次事件」且事件概率正比于 $\delta$ 的系统，都能套这四步。排队论里第 $k$ 个到达的时刻、随机算法「重复试验直到成功」的运行步数、哈希表里的碰撞数、网络分组的丢失数，骨架完全一样。判据只有两条：事件能否被拆成大量独立小概率尝试；这些尝试的概率是否与观察窗口成正比。
>
> 模板失效的情形也要记住：只要有批量到达（一次操作触发多个事件），第二步就崩，因为「至多一次」不成立，此时需要 compound Poisson process（复合泊松过程）或者干脆不做连续化。跨课程对照一句：CSAPP 里把连续时间采成离散 tick（时钟节拍）是同一个动作的工程版本，差别在于机器上取不到 $\delta\to0$，只能算出现在 $\delta$ 下的误差。
>
> 收束回正文：这个公式不是「记下来的结论」，而是一台机器。给定 $\lambda$ 与 $T$，它产出概率；给定精度要求，它反推网格。


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
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 均值与方差相等不是巧合，也不是「泊松分布的性格」，它是单参数的直接后果，两行就能算出来。算完也就明白为什么这个等式可以当判据用。
>
> 工具是 probability generating function（概率生成函数）。定义 $G(z)=E[z^{N}]$，它把整个分布打包成一个函数；两个基本事实是 $G'(1)=E[N]$、$G''(1)=E[N(N-1)]$，因为逐项求导后 $z$ 取 $1$ 就把 $k$ 与 $k(k-1)$ 的权重原样留下。对 Poisson distribution（泊松分布）有 $G(z)=e^{\lambda T(z-1)}$，于是 $G'(1)=\lambda T$、$G''(1)=(\lambda T)^{2}$，代入 $\operatorname{var}=G''(1)+G'(1)-G'(1)^{2}$ 得 $\operatorname{var}=(\lambda T)^{2}+\lambda T-(\lambda T)^{2}=\lambda T$。等式两边恰好是同一个量，因为它俩都是 $\lambda T$ 的函数。
>
> 同样的算法跑一遍 binomial distribution（二项分布）做对照：$G(z)=(1-p+pz)^{n}$，$G'(1)=np$，$G''(1)=n(n-1)p^{2}$，得 $\operatorname{var}=np(1-p)$。两式在 $p\to0$ 时合流，$1-p\to1$，方差贴着均值走。这也解释了为什么泊松分布的方差不可能独立于均值设定——取极限时顺手把那个自由度丢掉了。
>
> 顺带修正一条常见但不成立的论证。有人说「可加性要求均值与方差都随参数线性增长，二者必然同形」，这句话是错的：正态分布同样可以让均值与方差都随参数线性变化，位置尺度族里它们是两个互不相干的参数。真正的机制是单参数——$G(z)$ 里只有一个 $\lambda T$，$G'(1)$ 与 $G''(1)$ 都由它决定，方差无处独立。把「同形」归因于可加性，会在遇到非泊松的单参数族时立刻露馅。
>
> 这条等式最好用的形态是 index of dispersion（离散指数）$F=\operatorname{var}/\operatorname{mean}$。泊松恒有 $F=1$；二项分布 $F=1-p<1$，属于 underdispersion（欠离散），意思是到达比泊松更规律，因为上限压住了波动；负二项一类 $F>1$，属于 overdispersion（过离散），意思是强度本身在漂移，短时间密集、长时间稀疏。这三档是工程上最快的模型筛选器，但它只给必要条件：$F=1$ 并不能反推出泊松，只是「不像泊松」这件事可以被一个数直接否掉。
>
> 代一组数看看它怎么工作。某服务每小时平均到达 $\lambda=2$ 次，观察 $T=3$ 小时，模型预测均值与方差都是 $6$，标准差 $2.45$。若实测样本均值恰好是 $6$、样本方差却是 $11$，则 $F=1.83$，基本可以断定强度随时间漂移，高峰与低谷被混在了一起，此时应当换 compound Poisson process（复合泊松过程）或时变强度的模型，而不是硬套泊松公式。反过来，若样本方差只有 $3.2$，$F=0.53$，说明到达过于均匀，可能来自定时轮询而非随机事件。
>
> 可加性在这里与等式相互印证。两个独立泊松过程合并后仍是泊松，参数相加，于是均值与方差同时相加、$F$ 保持 $1$——这条性质让「泊松性」在合并下稳定，也是为什么把多个独立来源的稀有事件合起来建模时仍然成立。注意方向：合并保持泊松，但「合并后 $F=1$」不能倒推每一段都是泊松，因为过离散与欠离散可以在混合时互相抵消。
>
> 跨课程连接：CLRS 里用 expectation（期望）的线性把随机算法的代价拆开算，这里则要第二阶矩，因为可靠性问题关心的是波动而不只是平均；CSAPP 里做性能诊断看延迟分布的均值与尾部，道理相同——只看均值会漏掉抖动的来源，而抖动往往才是故障的原因。
>
> 收束回正文：两个公式并列写在一起，是要你记住「一个参数锁两件事」这个结构。见到均值与方差不成比例的数据，第一步就是怀疑模型里的独立性或强度恒定被破坏了。


其中 $N_T$ 表示长度为 $T$ 的时间区间内的到达次数。这两个公式毫不令人意外，因为我们面对的正是二项分布 PMF 的极限，该二项分布写为 $n = T/\delta$、$p = \lambda\delta$，其均值为 $np = \lambda T$，方差为 $np(1-p) \simeq np = \lambda T$。

现在我们来推导首次到达时间 $T$ 的概率规律，假定过程从时刻零开始。注意，当且仅当在区间 $[0,t]$ 内没有到达时才有 $T > t$。于是有

```math
F_T(t) = P(T \le t) = 1 - P(T > t) = 1 - P(0, t) = 1 - e^{-\lambda t}, \qquad t > 0 .
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一段的关键不在算，而在选路。要的是「首次到达时间」的分布，但直接算 cumulative distribution function（累积分布函数）$F_T(t)=P(T\le t)$ 需要处理「$t$ 之前发生过至少一次」这一堆互斥事件的并；反过来算它的补，事件变成「到时刻 $t$ 为止一次都没来」，而后者在泊松模型里是现成的一个值 $P(0,t)=e^{-\lambda t}$。绕行绕到更简单的一侧，这就是全部思想。
>
> 先修一个记号冲突，否则抄笔记必出事故。这一页的 $T$ 出现了两次、含义不同：$N_T$ 里的 $T$ 是固定的观察区间长度，从上一页起就当成常数用；而这里「首次到达时间 $T$」是 random variable（随机变量）。两者在同一段文字里撞名，是正文的一处记号冲突，不是数学错误。自己推导时把首次到达时间写成 $T_1$ 或 $\tau$，映射回正文再换名字，可以避免把期望 $E[N_T]=\lambda T$ 与 $E[T]=1/\lambda$ 混成一句话。
>
> 三步走完就是结论：survival function（生存函数）$P(T>t)=P(0,t)=e^{-\lambda t}$，取补得 $F_T(t)=1-e^{-\lambda t}$，再对 $t$ 求导得 probability density function（概率密度函数）$f_T(t)=\lambda e^{-\lambda t}$，$t>0$。求导合法，因为指数函数在 $(0,\infty)$ 上光滑；$t<0$ 时 $F_T=0$，因为「首次到达发生在负时刻」这件事按定义不发生。这条分布就叫 exponential distribution（指数分布）。
>
> 代一组数把三条公式连起来。取 $\lambda=0.2$ 每小时：均值为 $5$ 小时，方差为 $25$，标准差与均值同量级——这说明指数分布的波动极大，平均值完全没有代表性。中位数由 $e^{-\lambda t}=1/2$ 解出 $t=\ln2/\lambda=3.466$ 小时，比均值小三分之一，是右偏分布的典型特征。再看两个具体概率：$P(T>5)=e^{-1}=0.3679$，$P(2<T<4)=e^{-0.4}-e^{-0.8}=0.2210$。这几个数都该能手算出来，试卷上的答案基本落在这个量级。
>
> 更重要的是这条式子顺便证了 memoryless property（无记忆性）。条件概率 $P(T>s+t\mid T>s)=\frac{e^{-\lambda(s+t)}}{e^{-\lambda s}}=e^{-\lambda t}=P(T>t)$，无论 $s$ 多大都成立。注意这一步没有引入任何新假设：它用的是 (b) 的 independent increments（独立增量），即 $[s,s+t]$ 里没有到达这件事与 $[0,s]$ 的历史无关。所以无记忆性不是指数分布的附加性质，而是泊松假设的直接投影。
>
> 还可以把关系反过来读：在连续分布里，满足 $g(s+t)=g(s)g(t)$ 的单调函数只有 $g(t)=e^{-ct}$。证明骨架很短——方程给出 $g(nt)=g(t)^{n}$，于是 $g(t/n)=g(t)^{1/n}$，先对一切有理数成立，再用单调性把实数从两侧夹住。结论是：exponential distribution（指数分布）不是「碰巧算出来的形状」，而是无记忆性的唯一可能形状。这条唯一性以后会反复用到，凡是想给「无记忆」找模型，就别无选择。
>
> 工程语言里这件事叫 hazard rate（风险率）：$h(t)=\frac{f_T(t)}{1-F_T(t)}=\lambda$，一个与 $t$ 无关的常数。读法是「不管已经等了多久，下一刻发生事件的瞬时强度不变」。把常数换成 $k t^{k-1}$ 就得到 Weibull distribution（威布尔分布）：$k<1$ 时风险随时间下降，对应早期失效、坏件早坏；$k>1$ 时风险随时间上升，对应磨损老化；$k=1$ 正好是指数分布这条分界线。所以看到「越等越不容易坏」的先验直觉时，要意识到那对应的是 $k<1$，而不是指数分布。
>
> 跨课程连接三处。CLRS 里分析「重复独立试验直到首次成功」的期望步数是 $1/p$，对应的离散版本是 geometric distribution（几何分布），这里只是把步数换成连续时间，$1/p$ 换成 $1/\lambda$，两条推导骨架完全平行。6.042J 里反复用「补事件 + 独立性」把复杂事件化简，本例是它在连续情形的一次演练。实分析那边，$g(s+t)=g(s)g(t)$ 属于函数方程，解法与上面的有理数—单调性夹逼一模一样。
>
> 收束回正文：见到「首次」「首个」「第一次」这类随机变量，第一反应就该是生存函数，而不是分布函数。这条反射能省掉后面大量求和的功夫。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一页建的是离散—连续对照表，但先要把量纲这笔账记死。原书那句设定是：把时间切成小间隔 $\delta$，每个间隔对应一次 Bernoulli trial（伯努利试验），成功概率 $p=\lambda\delta$。右端的 $\lambda$ 单位是每单位时间多少次，乘上时间长度 $\delta$ 才无量纲、才配当概率；$p$ 必须落在 $[0,1]$ 里，所以 $p=\lambda\delta$ 只在 $\delta$ 足够小时成立，$\delta$ 大到 $\lambda\delta$ 超过 1，这个离散化就根本不存在。凡是把 $p$ 直接换成 $\lambda$ 的地方，都必须同时把「次数」换成「时间长度」，否则两边单位对不上。
>
> 四对关系逐条对账。第一对：一次 Bernoulli trial（伯努利试验）对应一个长度 $\delta$ 的小区间内是否有到达。第二对：binomial distribution（二项分布）对应 Poisson distribution（泊松分布），$n$ 次试验里的成功次数对应长度 $t$ 内的到达数，均值从 $np$ 到 $\lambda t$，方差从 $np(1-p)$ 到 $\lambda t$；方差这一项的极限值得多看一眼，$p\to 0$ 时 $1-p\to 1$，所以泊松方差等于均值不是巧合，而是稀罕事件假设的直接后果。第三对：geometric distribution（几何分布）对应 exponential distribution（指数分布）。原书 p.297（PDF p306）的定义是到包含首次成功那一次为止的试验次数，计数从 1 起、含终点；指数侧是到首次到达为止经过的时间长度，从 0 量到终点。两者都含终点、不含起点，均值 $1/p$ 对 $1/\lambda$，方差 $(1-p)/p^{2}$ 对 $1/\lambda^{2}$。最常见的错法是把几何说成首次成功之前的失败次数，那个版本从 0 起、均值 $(1-p)/p$，差一个 1，从此与指数再也对不上账。第四对：Pascal distribution（帕斯卡分布）对应 Erlang distribution（爱尔兰分布），第 $k$ 次成功所在的试验编号均值 $k/p$，对应第 $k$ 次到达的时刻均值 $k/\lambda$。
>
> 口诀「离散是固定的 $\delta$，连续是 $\delta\to 0$」要变成能验算的三行：$p=\lambda\delta$ 随 $\delta$ 一起变小；$np=n\lambda\delta$ 固定住 $\lambda t$ 不变；几何的 $\mathrm{var}/\mathrm{mean}^{2}=1-p$ 随 $p\to 0$ 趋于 1，正好等于指数的 $\mathrm{var}/\mathrm{mean}^{2}=1$。第三行最有说服力：它说明无记忆在离散与连续两边是同一个形状参数，只是格点被抹平了。
>
> 这张表真正的用处是迁移，不是记忆。凡是在 §6.1 伯努利过程里证过的命题，都先做两个替换——次数换成时间长度，$1/p$ 换成 $1/\lambda$——再验一遍极限是否收敛。举例：两路合并的加法封闭性，离散侧是二项分布的卷积，连续侧就变成泊松率相加；分裂的以概率 $p$ 保留，连续侧的率变成 $\lambda p$；首次成功的等待，连续侧就是指数分布。照着做三遍，你会发现自己能猜出后面一半的结论，再用 $\delta\to 0$ 验一遍即可。
>
> 用具体数字把表钉住。取 $\lambda=2$ 次每分钟，$\delta=1$ 秒，即 $1/60$ 分钟，则 $p=1/30$。几何侧均值 30 个 $\delta$，等于 30 秒，与 $1/\lambda=0.5$ 分钟吻合；离散方差 $(1-p)/p^{2}=(29/30)\times 900=870$ 秒平方，连续方差 $1/\lambda^{2}=0.25$ 分平方，等于 900 秒平方，相对差 $3.3\%$，而 $p=1/30$ 恰好是同一个量级——$\delta$ 再小十倍，这个差就再小十倍。这种差多少、为什么差、怎么变小的核对方式，比背结论可靠得多。
>
> 最后给一个自查标准：合上书，把四对关系各写一行，每行给概率质量函数或概率密度、均值、方差三项，并用上面的数字验算一遍；能默写算通过，写不出来说明还停在认得而不是会用。往后排队论、马尔可夫链、可靠性分析都会反复回到这张表。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 原书这一页要证的是 Example 6.9 的可加性：$M$ 是 $9{:}00$ 到 $9{:}10$ 的到达数，参数 $\mu=10\times 10=100$；$N$ 是 $9{:}30$ 到 $9{:}35$ 的到达数，参数 $\nu=10\times 5=50$；两段不重叠，所以 $M$ 与 $N$ 独立。原书自己交代了，4.4 节已经用 transform（变换）证过同一条结论，另见第 4 章 Problem 11。所以下面这条替换法不是新定理，而是把同一个事实改用过程语言重讲一遍。
>
> 替换法，英文 coupling（耦合）：与其算两个泊松的卷积，不如造一个同分布、但落在结构更干净的区间上的随机变量。这里取 $\tilde M$ 为 $9{:}10$ 到 $9{:}15$ 的到达数。三件事必须逐一核对：一是 $\tilde M$ 与 $N$ 同分布，参数都是 50，因为两段长度都是 5 分钟、率都是每分钟 10 次；二是 $\tilde M$ 与 $M$ 独立，因为两段时间不重叠；三是 $M+\tilde M$ 是总长 15 分钟的一段连续区间内的到达数，所以参数是 $10\times 15=150$。于是 $M+N$ 与 $M+\tilde M$ 同分布，答案立刻读出。
>
> 这条链为什么合法，值得写清。联合分布由各分量的边缘分布与独立性结构唯一确定：两个独立泊松的联合质量函数是两份边缘概率的乘积，把 $N$ 换成同分布的 $\tilde M$，只是换了同一个乘数中的一项，乘积不变。所以同分布加独立推出和的分布不变，是一条只用到边缘分布与独立性的引理，与泊松这个具体形状无关——换成任意两个独立同分布的族同样成立。
>
> 元规则那半句要改口。旧注说加法封闭性在此第一次正面出场，这与正文冲突：原书在这一页开头就写了正如 4.4 节用变换所说明的，加法封闭性早在第 4 章用生成函数证过。准确的记法是：它在这里第一次以过程语言重述——不再说卷积变成乘积，而说两段不重叠的区间拼起来还是一次泊松，率相加。同一个事实，两种语言。
>
> 过程语言这个版本为什么值得强调？因为它给出的是可迁移的结构：任意多个互不重叠的区间，长度相加、到达数相加，参数就是 $\lambda$ 乘总长度。正文紧接着写的那句总长度为 $T$ 的时刻集合内 $k$ 次到达的概率恒为 $P(k,T)$，就是这条的语言化版本——区间不必连续，只要能按长度记账就行。反过来，若两段重叠，或两个流的到达相关，结论立刻塌：相关的两路叠加方差大于均值，不再是泊松。
>
> 把替换法记进工具箱，用法是：先把要证的分布翻译成一个结构上显然的分布，再证明两者同分布。6.006 的平摊分析里同一个动作叫换一个等价但更好算的量：算法用一个虚拟账户记账，这里用一个虚构的时间窗记账；两者都不是近似，而是严格等价的重新表述，区别只在记账对象从字节变成了到达。
>
> 一句旁证：替换法之所以在这里显得轻巧，是因为泊松过程有增量独立这一条结构性事实；若换成两条相关的到达流，就连「造一个同分布的替身」这一步都做不成——替身必须与原对象独立，这是它唯一的代价。


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
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 无记忆性用 survival function（生存函数）写成 $S(s+t)=S(s)S(t)$，这是一条函数方程，不是一条统计性质。方向要看清楚：方程从无记忆性出发，结论是满足它的分布只能长成指数。换言之，不是指数分布恰好无记忆，而是无记忆性把分布逼成了指数——这是必然性，不是巧合。
>
> 解这条方程要三步，缺一步就是错的。第一步，$S(0)=1$、$S$ 不恒为 0，并且 $S(1)<1$。三条都不能省：恒等于 0 的函数满足乘法方程与 $S(0)=1$，但它对应 $T=0$（立即失效）；恒等于 1 的函数同样满足这两条，它对应 $T=\infty$，不是合法随机变量；$S(1)<1$ 才排掉后者，此时 $c=-\ln S(1)>0$。第二步，令 $c=-\ln S(1)$，由 $S(n)=S(1)^{n}$ 得整数点上 $S(n)=e^{-cn}$，再由 $S(1)=S(1/m)^{m}$ 得 $S(1/m)=e^{-c/m}$，于是所有有理点 $q$ 上 $S(q)=e^{-cq}$，这一步只用乘法方程。第三步，用单调性把有理点上的值夹到实数点：对任意 $t$，取有理数列从下方逼近 $t$、另一列从上方逼近 $t$，两边夹住 $S(t)$，得 $S(t)=e^{-ct}$。
>
> 于是结论该这样写：单调非零解必为 $e^{-ct}$，$c>0$；$\lambda$ 不由方程决定，由速率给定。旧注说满足它且单调的连续解只有一个，即 $S(t)=e^{-\lambda t}$，这句话漏了两处：漏了非零这个前提，也把唯一性错记成 $\lambda$ 唯一。取 $c=0.7$、$c=1.3$、$c=2.0$ 都能让乘法方程成立，对应三种不同的率。无记忆性把分布钉在指数这个族里，参数还得从别的地方拿——这就是为什么正文要另起一行算 $P(T-t>s)=e^{-\lambda s}$：率是设定给的，无记忆只管形状。
>
> 离散侧是同一台机器。条件 $P(T>m+n\mid T>m)=P(T>n)$ 写成 $g(m+n)=g(m)g(n)$，单调非零解只能是 $g(m)=(1-p)^{m}$，即 geometric distribution（几何分布）。所以「几何是指数的离散版本」不是比喻，而是同一个函数方程在两组格点上的解。这里要分清概率质量函数与生存函数：方程是写在生存函数上的，$S(k)=(1-p)^{k}$ 满足乘法方程，而 $P(T=k)=p(1-p)^{k-1}$ 本身不满足——把两者混着记，就会得出几何分布满足乘法的错误印象。
>
> 正文这一页的验证是反着做的：先算 $P(T-t>s)$ 等于 $[t,t+s]$ 内零次到达的概率，得 $e^{-\lambda s}$，再从结果读出无记忆性。这条路线不用解函数方程，但它只证明了指数无记忆，没有证明只有指数无记忆。两条路线互补：一条给验证，一条给唯一性；答证明题用哪条，取决于题目问的是「验证」还是「刻画」。
>
> 术语方向订正一处：Markov property（马尔可夫性质），英文在前、中文在后，旧注写成了中文在前。它说的是给定现在、未来与过去条件独立；无记忆性是它在连续时间里的最简形式——状态只有一个，且这个状态不携带任何历史。泊松过程的「未来与过去独立、未来重新开始」就是这条性质的原型，第 7 章的链只是把状态从一个时刻扩成一个有限集。
>
> 记住这条锁链：无记忆等价于乘法方程，等价于指数或几何。三个说法互相推得，任何一个都可以当起点；做题时看到哪一个，就往另外两个走。
>
> 最后补一句会不会被扣分的细节：写证明时必须显式声明 $S$ 右连续或单调，否则第三步的取极限没有依据；而在概率论里生存函数天然单调不增且右连续，所以这一条几乎总是自动成立——但「几乎总是」要在证明里说出来。

= P\big(\text{在 }[t,\,t+s]\ \text{内发生 0 次到达}\big)
= P(0, s)
= e^{-\lambda s} .

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 题目是这样：你走进银行，三位柜员都在忙着为别人服务，没有其他顾客在等，所有人的服务时间相互独立、同分布、服从 exponential distribution（指数分布）。问的是你成为最后一个离开者的概率，答案是 $1/3$。答案很短，但每一步都要交代清楚，否则就变成背结论。
>
> 关键一步是把观察起点挪到「你开始被服务的那一刻」。在你进门到开始服务之间，可能有柜员已经服务了很久；但由 memorylessness（无记忆性），已经服务了多久这条信息对剩余时间毫无影响——一个已经服务 40 分钟的顾客与一个刚坐下的顾客，剩余服务时间同分布。于是从你开始服务那一刻起，你和另外两位顾客的剩余服务时间，是三个独立同分布的指数随机变量。
>
> 三个人地位完全对称：谁的剩余时间最长，谁最后离开。既然三个随机变量独立同分布，那么「最长的那一个是谁」在三个人之间等可能，概率各为 $1/3$。注意这里根本不需要算最大值的分布——最大值服从什么分布是个麻烦问题，要算次序统计量、要积分；但「最大值落在谁身上」是纯对称性问题，不涉及计算。
>
> 把这个论证写成不必算的形式：设三人剩余时间为 $R_1,R_2,R_3$，独立同分布。联合分布在任意置换下不变，所以 $P(R_1=\max)=P(R_2=\max)=P(R_3=\max)$；三个概率相加为 1，故每个都是 $1/3$。这就是对称性论证的全部内容：用分布在置换下不变，换掉计算分布。它与 6.042J 里用双射计数的精神一脉相承——不硬算，而是找一个让问题变成等可能的视角。
>
> 代价也要说清：这条论证只回答「谁是最后」，不回答「最后一个人什么时候走」。后者需要最大值的分布，也就需要真正的积分，正文并没有给出；如果你把 $1/3$ 顺手当成「最后一个离开的平均时间」之类的信息，那就越界了。
>
> 边界条件有三条。第一，一旦三人不同分布，$1/3$ 立刻失效：若你的服务率是别人的两倍，你最后离开的概率就小于 $1/3$，这时没有对称性可用，只能回到次序统计量去积分。第二，若三人的服务时间相关，结论也不成立，因为置换不变的前提没了。第三，若还有人在排队，问题变成排队系统，你要等的不是三个人走完，而是轮到自己，机制完全不同。
>
> 别把它与 competing exponentials（竞争指数）混为一谈。竞争指数问的是谁先响，答案按率分账，即 $\lambda_i/\sum_j\lambda_j$；这里问的是谁最后响，答案是 $1/3$，因为三者同分布。前者用率的比例，后者只用对称性。两条结论出现在同一节，混着记就会把 $1/3$ 错记成某个率的比值。
>
> 一句话收束：同分布加独立，推出名次等可能；这条结论在次序统计量、随机化算法的锦标赛分析里反复出现，而它成立的理由从来不是计算，而是置换不变性。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 正文把「到达间隔独立且同为指数分布」称为泊松过程的另一种描述。这句话的分量在于，它把定义从性质换成了构造。前一种描述是性质定义：长度 $\delta$ 的小区间内一次到达的概率是 $\lambda\delta$ 加高阶小量，两次及以上可忽略，不重叠区间相互独立。后一种是构造定义：先采样一串 i.i.d.（独立同分布）的指数间隔 $T_1,T_2,\dots$，再在 $T_1$、$T_1+T_2$ 等位置放到达。
>
> 两者等价，两个方向各要一句。构造推出性质：第 $k$ 个到达落在某区间内的概率由 $k$ 个指数之和给出，不重叠区间的独立性则由「各段间隔独立采样」直接继承。性质推出构造：由无记忆性，给定 $t$ 时刻之前的历史，下一次到达的等待时间仍是参数 $\lambda$ 的指数，且与历史独立；把这条逐段用下去，每个间隔都独立且同分布。所以这不是巧合，是无记忆性的直接推论。
>
> 构造定义的用处全在生成上。要在程序里造一条泊松到达流，不需要每个小区间抛硬币，只需要三行：令 $t=0$；循环抽取 $E\sim\mathrm{Exp}(\lambda)$ 并令 $t$ 自增 $E$；输出 $t$。代价是每次一个指数采样，而这只要一个均匀随机数加一次取对数就能做出来，你已有的 CLRS 随机数知识完全够用。这是排队论仿真、网络负载生成、随机算法测试的标准做法。
>
> 给个量级感。取 $\lambda=3$ 次每分钟，间隔均值 $1/3$ 分钟，即 20 秒。一次模拟抽 10 个间隔，第 10 个到达的时刻是 10 个独立指数之和，均值 200 秒、方差 $10/9$ 分平方。这个「和」的身份很关键：它说明第 $k$ 个到达时刻就是 $k$ 个指数之和，均值 $k/\lambda$、方差 $k/\lambda^{2}$，与正文下一页的性质表逐项对上。
>
> 构造视角还顺带解释了 fresh-start（重新开始）现象：过程在任意时刻重新开始，因为在指数间隔的视角下，未来只由「当前还没到的下一次」决定，而这一次的等待与过去无关。所以正文在 $t^{*}$ 处得到的剩余等待仍是指数，不是近似，而是构造定义的直接后果。
>
> 边界也要写清：这套构造只在率恒定时成立。若率随时间变化，即 nonhomogeneous（非齐次）情形，间隔不再同分布，也不能简单累加指数采样，要改用强度函数的积分或 thinning（稀疏化）。写仿真时最常见的错误，就是把非平稳流量当成平稳流量直接累加指数间隔，结果平均到达数与真实值系统性偏离。
>
> 顺手记一条自查：如果你能只用「先抽间隔、再累加」这个说法，把「区间内到达数服从泊松」推出来，说明你真的掌握了两种描述的等价；若推不出来，就还停在背性质。
>
> 还有一层结构值得一并记住：构造定义让「泊松过程」变成了「更新过程的一个特例」——把指数间隔换成任意分布，就得到一般更新过程。有了这个坐标，你以后读到 renewal theory 时不会觉得是新东西，而是「把指数这个特例放开」；反过来，泊松过程所有漂亮的结论都依赖指数这个唯一无记忆的连续分布，一旦放开，独立增量立刻失效，只剩「间隔独立」这一条。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 命名与史实要分开记。Erlang distribution（爱尔兰分布）以丹麦工程师 Agner Krarup Erlang（1878–1929）命名，他 1908 年起在哥本哈根电话公司工作。1909 年那篇论文的题目是 The Theory of Probabilities and Telephone Conversations，它给的是通话时长的概率模型——把通话时长建成指数分布，这是排队论建模的起点；而为他赢得工程名声的呼损公式，也就是今天说的 Erlang B，要到 1917 年才出现。旧注把两件事压成「1909 年研究电话交换需要多少线路」，时间线就错了，读者会以为呼损 1909 年就有了。至于「话务量以 Erlang 计」，那是因为一个 Erlang 就是一条线被占满的占用率，单位沿用至今。
>
> 从第一性原理看，$k$ 阶 Erlang 就是等到第 $k$ 次到达的时间。由上一节，$Y_k=T_1+\cdots+T_k$，$k$ 个独立同分布的指数之和，均值 $k/\lambda$、方差 $k/\lambda^{2}$。这两个矩不需要积分，均值与方差对独立和都可加，直接用就完了。
>
> PDF $f(y)=\lambda^{k}y^{k-1}e^{-\lambda y}/(k-1)!$ 要读成三个因子相乘，不是两个。$e^{-\lambda y}$ 是从 $y$ 往后一直没有到达的生存概率；$(\lambda y)^{k-1}/(k-1)!$ 是 $y$ 之前恰好 $k-1$ 次到达的泊松概率；还差一个 $\lambda$，它来自 $y$ 附近那一小段里恰好有一次到达，概率约 $\lambda\delta$，除以 $\delta$ 才变成密度。旧注说两个视角相乘得到密度，少乘了这个 $\lambda$，数值会整整差一个因子。
>
> 用数字验证这个 $\lambda$。取 $\lambda=2$、$k=4$、$y=1.3$，则 $e^{-\lambda y}(\lambda y)^{k-1}/(k-1)!$ 等于 $0.2176$，而正确的密度是 $0.4351$，比值恰好是 2，也就是 $\lambda$。这不是小数点误差，而是漏了一个量纲为每单位时间的因子；凡是写成「概率相乘得密度」的地方，都要检查有没有做除以 $\delta$ 这一步。
>
> 与 Poisson distribution（泊松分布）的对偶关系是：泊松回答给定时间里有几件事，Erlang 回答第 $k$ 件事发生在何时，两者由 $\{Y_k\le y\}=\{N_y\ge k\}$ 连接。这条对偶给出另一条推密度的路线：对泊松右尾求导，不需要任何「$\delta$ 很小」的近似论证，是精确推导。两条路线互相印证，比只记一个公式稳。
>
> 工程上它出现得比想象中频繁：M/E$_k$/1 的停留时间、k 级备份的寿命、分组在若干同速链路串联时的时延，都是若干个指数相加的形状。原因很朴素——串联阶段的时延相加，而每个阶段在「独立、恒定率」假设下就是指数。你在做性能分析时最常用的那个近似，正是这条。
>
> 一句话收束：Erlang 的名字挂在一个「等待第 k 次事件」的分布上，它的全部内容是「$k$ 个独立指数之和」，而它的密度里同时住着生存概率、计数概率和一个率——三个因子缺一不可。
>
> 顺带把 $k=0$ 与 $k=1$ 两个端点的读法钉住：$k=1$ 时 Erlang 退化为 exponential distribution（指数分布），密度是 $\lambda e^{-\lambda y}$，此时 $k-1=0$，$(k-1)!=1$，公式仍成立；$k$ 增大时分布重心右移、形状从单调下降变成单峰，峰值出现在 $(k-1)/\lambda$ 附近。这条形状变化本身就是「多级串联」的直观：级数越多，总时延越集中在均值附近，变异系数平方 $\mathrm{var}/\mathrm{mean}^2=1/k$ 越小——这正是为什么流水线越深，总时延的相对波动越小。
>
> 最后提醒一句术语口径：阶数 $k$ 必须写在名字里，$k$ 阶 Erlang 与指数是两个分布，不是同一个分布的两种叫法；写成「Erlang(k)」或「$k$ 阶 Erlang」都行，但漏了阶数就退化成指数，公式里的 $(k-1)!$ 也会跟着丢掉。


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
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一页给的是一个可复用的求密度模板，可以叫 $\delta$ 乘 $f$ 法：要算密度 $f_Y(y)$，先写 $\delta f_Y(y)\approx P(y\le Y\le y+\delta)$，即密度乘小区间长近似落入小区间的概率，再把右边用已知事件拆开。
>
> 它为什么合法，理由不在概率论而在微积分：若分布函数在 $y$ 处可导，则 $[F_Y(y+\delta)-F_Y(y)]/\delta\to f_Y(y)$。所以这个模板不是玄学近似，而是导数差商定义的直译——除以 $\delta$ 再取极限这一步，正是把差商变成导数。记住这一点，你就不会在证明里心虚。
>
> 拆事件的要点在这里：把右边拆成两个独立事件的交，$A$ 是小区间 $[y,y+\delta]$ 内有一次到达，概率约 $\lambda\delta$；$B$ 是 $y$ 之前恰好 $k-1$ 次到达，概率 $P(k-1,y)$ 已知。两者独立，因为它们落在不相交的时间段上，这就是 independent increments（独立增量）。相乘得 $\lambda\delta\cdot P(k-1,y)$，再除以 $\delta$，$\lambda$ 留下、$\delta$ 消掉，密度立刻得到。
>
> 把模板写成四步，方便套用：一、写出 $\delta f$ 这一侧；二、把「$Y$ 落在小区间里」翻译成关于计数过程的事件；三、用独立增量把事件拆成独立因子相乘；四、除以 $\delta$ 取极限。求次序统计量的密度、求首达时间的密度、求更新过程某一点的密度，走的都是这四步，只是第三步换成本问题的结构。
>
> 给一个可手算的量级。取 $\lambda=2$、$k=3$、$y=1$、$\delta=0.001$，则 $P(1\le Y_3\le 1.001)\approx 0.001 f(1)$；而 $f(1)=\lambda^{3}e^{-2}/2=4e^{-2}\approx0.5413$，所以概率约 $5.41\times10^{-4}$。手算一遍能看清一件事：$\delta$ 必须足够小，但不需要无限小——只要二阶项已经低于你要的精度，这个近似就够用。
>
> 它与黎曼和同构：把区间切成宽 $\delta$ 的小条，条高是密度，面积是概率，求和取极限得积分。区别只在条高不是靠积分算出来的，而是靠计数过程的已知分布读出来的——所以这是「绕开积分」的手艺，不是微积分的应用。
>
> 什么时候不能用？拆出来的两个事件必须独立。若过程非齐次，或者两段区间重叠，$A$ 与 $B$ 就不再独立，乘积那一步当场失效，只能回到联合分布去算。同理，若「$Y$ 落在小区间里」不能唯一地翻译成一对事件的交，比如还可能出现同时两次到达，也必须把那些支路一并算进来，只是它们都是高阶小量。
>
> 一句话收束：这个模板的价值是把「求分布」降级成「拆事件」，而拆事件的许可证是独立增量与「两次及以上可忽略」这两条泊松过程的基本假设。
>
> 再举一个把模板用在「另一个研究对象」上的例子，说明它为什么是可复用的而不是一招一式的。若问的不是第 $k$ 个到达时刻，而是「某固定区间内最后一次到达的时刻」，拆事件仍然照做：$Y$ 落在 $[y,y+\delta]$ 内，要求 $y$ 之前至少一次到达、$y+\delta$ 之后零次到达；两段不相交，独立性照旧可用。真正危险的情形是让同一段时间同时出现在两个因子里，那时乘法就变成自乘，得到的是联合概率的平方，量级直接错一阶。
>
> 还有一个常被忽略的严格性细节：$P(A)\approx\lambda\delta$ 应写成 $P(A)=\lambda\delta+o(\delta)$。只写「约等于」的话，读者不知道误差是 $\delta^{2}$ 还是 $\delta^{3/2}$，也就不知道除以 $\delta$ 后能否取极限；而泊松过程的定义恰好保证误差是 $o(\delta)$，所以这一步才安全。


> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 上面末两行在 OCR 中把系数、指数与公式主体拆散到数行（如 `f_{Y_k}(y)` 主体、`\lambda \delta` 系数以及分母 $(k-1)!$ 各处零散），数值与结构均按泊松过程「区间内到达次数」的标准论证重建，所得 $f_{Y_k}(y) = \dfrac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!}$ 与下方脚注求导结果一致。</span>

> <span style="color:#7f8c8d;">脚注 $t$（给出一条不依赖近似论证（approximation arguments）的替代推导）：对给定的 $y \ge 0$，事件 $\{Y_k \le y\}$ 与事件「时间区间 $[0, y]$ 内的到达次数至少为 $k$」是同一个事件。因此，$Y_k$ 的 CDF 为
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 脚注里那条恒等式 $\{Y_k\le y\}\iff\{N_y\ge k\}$ 是本节最凝练的一句，可以叫计数—时间对偶：第 $k$ 次到达发生在 $y$ 之前，当且仅当到 $y$ 为止至少发生了 $k$ 次到达。左边是关于时刻的事件，右边是关于个数的事件，同一件事的两种说法。
>
> 严格性来自计数的单调性：$N_y$ 是到 $y$ 为止的到达次数，它随 $y$ 不减，每增加 1 就对应一次到达。于是「第 $k$ 次到达的时刻不超过 $y$」与「$y$ 时刻计数已经达到 $k$」是同一个集合。注意这里用的是「至少 $k$ 次」，不是「恰好 $k$ 次」——写成恰好就错，这是最容易失分的一处细节。
>
> 由此得到一条精确路线，一步近似都不用：$F_{Y_k}(y)=P(N_y\ge k)=\sum_{j=k}^{\infty} e^{-\lambda y}(\lambda y)^{j}/j!$，对 $y$ 求导，右尾求导只剩一项，得 $f_{Y_k}(y)=\lambda e^{-\lambda y}(\lambda y)^{k-1}/(k-1)!$。这条路线的好处是不依赖「$\delta$ 很小、二阶项可忽略」这类论证，完全由恒等式推出来，所以它是上一页那个模板的严格备份。
>
> 这条对偶的价值在于两个家族可以互相取用：想要时刻的分布，就去看个数的分布；想要个数的分布，就去看时刻的分布。本节其实用了两次——一次由个数得密度，一次由密度反推个数的性质（比如「区间内到达数服从泊松」可以看成「第 $k$ 个到达时刻是 $k$ 个指数之和」的等价陈述）。
>
> 算法里的镜像很清楚：6.006 里「找到第一个满足条件的索引」与「统计满足条件的元素个数」是同一个问题的两面，前者用二分算出的正是 lower_bound，也就是 $\mathrm{rank}(x)$（数有多少元素小于 $x$），后者是计数；注意 CLRS 的 select 是反方向——给定秩取元素，别与「按秩插入」混起来；CSAPP 里缓存替换的统计也常用「计数换时刻」的写法。这类对偶的共同结构是：有一个单调的计数器，把「首次达到某水平」与「达到水平之后再问时间」互相翻译。
>
> 离散版是同一句话：伯努利过程里「第 $k$ 次成功的时刻不超过 $n$」等价于「$n$ 次试验里成功至少 $k$ 次」，即二项分布的右尾。这正是 Pascal 分布与二项分布互为对偶的根源，也解释了为什么第 6 章的问题一半都能在两种语言里各写一遍。
>
> 把它写成速查卡：$\{Y_k\le y\}=\{N_y\ge k\}$。记住方向——左边是时刻、右边是计数，右边必须是「至少」。方向记反、或者把「至少」写成「恰好」，是这类题最常见的两处失分，而且两种错法都能在小例子上被手算抓住：取 $k=1$、$y$ 稍大于零，左端已经接近 1，右端若写成恰好一次则接近 0，一眼就看出来。
>
> 再补一个手算核对，把「至少」这个方向钉死。取 $\lambda=1$、$k=2$、$y=2$：左端 $P(Y_2\le 2)$ 是「第二次到达不晚于 2」，右端 $P(N_2\ge 2)$ 是「到 2 为止至少两次到达」。用泊松算右端得 $1-e^{-2}(1+2)\approx0.594$；用二阶 Erlang 的分布函数算左端得同一个式子，两条完全不同的公式给出同一个数，说明恒等式不是「看起来对」，而是真能互推。
>
> 还有一处同节内容要分开：对偶说的是时刻与计数之间的翻译，不是时刻与时刻之间。$Y_k$ 与 $Y_{k+1}$ 之间的间隔服从指数，那是无记忆性的结论；$Y_k$ 本身服从 $k$ 阶 Erlang，那是「$k$ 个独立和」的结论。两者都靠独立增量与独立性，但一个用「下一次等待重置」，一个用「和的卷积」，混成一条就会在写证明时用错依据。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「splitting（分裂）之后仍然是泊松过程」不是一句可以点头过去的话，它要按泊松过程的 defining properties（定义性质）逐条核对：time homogeneity（时间齐次性）、independence（独立性）、以及 sparsity（稀疏性），即一次到达的概率为 $\lambda\delta+o(\delta)$、两次及以上为 $o(\delta)$。三条里任何一条掉了，结论就塌，所以这个注的全部工作是把三条分别兑现，而不是复述「因为泊松所以泊松」。
>
> 先看许可证。分裂的操作是给每一次到达独立地抛一枚偏置硬币：以概率 $p$ 保留，以概率 $1-p$ 丢弃。这枚硬币的每一次投掷都必须与过程本身无关，也与别的投掷无关。有了这一点，时间齐次性自动继承——硬币不认时间，把时间平移一段，保留事件的统计结构不跟着变。独立性也自动继承——原来在两个不相交区间里发生的事件本来就独立，再各自乘上互不相干的硬币序列，独立性只会被加强而不会被削弱，因为乘上独立因子是把联合分布乘开、不是把它搅混。
>
> 关键是第三条。在长度 $\delta$ 的小区间里，「恰好保留一次」意味着「有一次原始到达」并且「这一枚硬币正面朝上」。两个事件独立，概率相乘，得到 $\lambda\delta\cdot p+o(\delta)$，这就是新的 rate（速率）$\lambda p$ 的来源：保留一次的概率不是凭空冒出来的常数，而是原速率乘上保留概率。再看「两次及以上」：要保留两次，先得有两次原始到达，这个概率已经是 $o(\delta)$，再乘上 $p^2$ 只会更小。于是稀疏性平方级地保住了，泊松过程的三条同时成立，速率正好是 $\lambda p$。
>
> 光对齐均值是不够的，得看二阶矩。取 $\lambda=3$ 次每分钟、$p=0.1$，则保留流的速率为 $0.3$ 次每分钟。$10$ 分钟内原始到达数 $N\sim\mathrm{Pois}(30)$，保留数记为 $M$；给定 $N$ 时 $M\sim\mathrm{Bin}(N,0.1)$。用 law of total expectation（全期望公式）得 $E[M]=30\times0.1=3$，用 law of total variance（全方差公式）得 $\mathrm{var}(M)=E[N]p(1-p)+\mathrm{var}(N)p^{2}=30\times0.09+30\times0.01=3$。均值与方差都等于 $3$，与 $\mathrm{Pois}(3)$ 完全吻合；这条核对很重要，因为只对齐均值时很多「错的」模型也能通过，方差相等才是泊松分布的指纹。顺带得到可用的数：$10$ 分钟内一次保留都没有的概率是 $e^{-3}\approx0.0498$，所以「至少保留一次」约 $0.950$。
>
> 反过来问一句「为什么非要独立」：如果硬币之间正相关——例如「上一次保留了，这一次就更可能保留」，那么保留事件会 burst（突发），在一个小区间里同时保留两次的概率不再与 $\delta^{2}$ 同阶，稀疏性第三款当场失效，得到的流也就不再是泊松流。这正是排队与网络里「突发流量」不是泊松建模对象的原因：突发意味着到达之间存在正相关，泊松假设的前提被破坏，用它算出来的队列长度会系统性偏乐观。
>
> 更反直觉的部分在下一页：分裂出来的两个流彼此独立，而且「类别序列」（本地分组还是中转分组）与「到达时刻」也相互独立。这条性质是泊松特有的 marking independence（标记独立性），伯努利过程里也有对应物，但 renewal process（一般更新过程）没有——那里标记会影响后续间隔。在 CS144 里你能看到它的工程镜像：网卡按哈希把每个分组独立地分配到某个 receive side scaling（接收侧分流），各队列的到达近似泊松、速率是该哈希桶的概率乘总线速率；但真实流量非平稳，所以这只能是近似，不是定理。
>
> 最后接一条方法论。伯努利过程可以看成泊松过程取 $\delta\to0$ 的极限，而分裂在两边都封闭：先在离散时钟上分裂、再取极限，与先取极限、再在连续时间上分裂，得到同一个结果。这次交换之所以合法，靠的是标记序列的i.i.d.（独立同分布）与概率的连续性；一般情形下交换极限与积分需要实分析里 dominated convergence（控制收敛）或 monotone convergence（单调收敛）那类条件，不能默认。旧注把最后这句挂到 6.042J 的「只需在生成族上验证 $P(A\cap B)=P(A)P(B)$」判据上，这个归属要更正：那是测度论里的 $\pi$-系判据，6.042J 不覆盖测度论。它其实只有三句话：一族集合若对有限交封闭，就叫 $\pi$-系，区间族是最典型的例子；两个概率测度只要在这样一个族上取值相同，就在整个 $\sigma$-代数上也相同；于是核对两个随机变量族独立，只需在生成它们的矩形、区间上验证乘积公式，其余事件由并、交、差与取极限自动继承。本注每一句「继承」的许可证正是这一条。


换一种方式，我们也可以从两个相互独立的泊松过程出发，其速率分别为 $\lambda_1$ 与 $\lambda_2$，并把它们合并（merge）在一起：只要任一过程中有一起到达，就记一次到达。结果是，合并后的过程也是泊松过程，速率为 $\lambda_1 + \lambda_2$。进一步地，合并后过程中的任意特定到达，来自第一个过程的概率为 $\lambda_1/(\lambda_1+\lambda_2)$，来自第二个过程的概率为 $\lambda_2/(\lambda_1+\lambda_2)$，并且与所有其他到达及其各自来源相互独立。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> merging（合并）的验证与 splitting（分裂）不是同一件事：分裂问的是「每一次到达要不要」，合并问的是「一小段时间里有没有人来」。在长度 $\delta$ 的小区间里，「合并流恰好一次到达」等于「流 1 恰一次、流 2 零次」或者「流 1 零次、流 2 恰一次」。这两个事件互斥，理由与 $o(\delta)$ 无关：按定义，第一个事件要求流 2 在这一小段里零次到达，第二个事件要求流 1 零次到达，两者不可能同时成立。至于「两流各来一次」那一支，它给出的是两次到达，落在「恰一次」之外，只贡献二阶小量，所以不进这个求和。既互斥、又覆盖了「恰一次」的全部情形，概率才可以直接相加：$P(1)\approx\lambda_1\delta(1-\lambda_2\delta)+(1-\lambda_1\delta)\lambda_2\delta\approx(\lambda_1+\lambda_2)\delta$。
>
> 交叉项为什么能扔，值得说透。展开后丢弃的是 $\lambda_1\lambda_2\delta^{2}$，它相对 $\lambda_1\delta$ 多带一个 $\lambda_2\delta$ 的因子，$\delta\to0$ 时必然归入 $o(\delta)$，这不是「差不多就行」，而正是「速率相加」的微观机制：rate（速率）就是小区间概率的一阶系数，两个流各自贡献一阶项，一阶项相加就得到 $\lambda_1+\lambda_2$。反过来看前提：如果两流不独立而是正相关（一阵拥堵同时触发两个源），那么「一小段里来两次」的概率是 $O(\delta)$ 而不是 $O(\delta^{2})$，一阶系数被污染，合并流不再是泊松——它的方差会超过均值，这种现象叫 over-dispersion（超离散），工程上表现为到达成串而不是均匀散布。
>
> 第二个问题是「这一次是谁来的」。给定合并流在小区间里出现一次到达，它来自流 1 的 conditional probability（条件概率）是 $\lambda_1/(\lambda_1+\lambda_2)$，做法就是把两个一阶系数相比，让「谁在这一小段里贡献了这次到达」按强度分账。更强的结论是：来源标签 $L_1,L_2,\ldots$ 相互独立同分布，并且与到达时刻独立，这又是 marking independence（标记独立性）的一次出场。于是合并与分裂构成一对对偶运算：分裂把速率乘上 $p$，合并把速率相加，泊松族对这两种运算都封闭，像线性空间对数乘与加法都封闭一样，这一句对偶是本节全部结论的骨架。
>
> 代进具体数字看量级。寄信者按 $\lambda_1=2$ 人每分钟到达，寄包裹者按 $\lambda_2=0.5$ 人每分钟到达，两者独立。合并后速率 $2.5$ 人每分钟，平均间隔 $0.4$ 分钟，即 $24$ 秒。下一位恰好是寄信者的概率是 $2/2.5=0.8$。$10$ 分钟内合并到达数服从 $\mathrm{Pois}(25)$，均值与方差都是 $25$——这里方差能相加全靠两个流独立；若二者相关，方差就不等于均值，泊松假设会给出偏小的队列长度估计。顺便算一个中点：恰好 $20$ 位的概率是 $e^{-25}25^{20}/20!\approx0.0519$，量级约百分之五。更细的一步是把方差拆开核对：$10$ 分钟内寄信数服从 $\mathrm{Pois}(20)$、寄包裹数服从 $\mathrm{Pois}(5)$，两者独立所以方差相加得 $25$，与合并流的 $\mathrm{Pois}(25)$ 一致；若有人只验均值就下结论，这一步会漏掉「相关性会污染方差」这个唯一能出问题的环节。
>
> 换到变换域看，为什么「泊松之和还是泊松」是一件必然的事。probability generating function（概率生成函数）把合并后的分布写成两个母函数相乘，而泊松的母函数是 $e^{\lambda(z-1)}$ 这种形状，两个相乘恰好等于参数相加：$e^{\lambda_1(z-1)}e^{\lambda_2(z-1)}=e^{(\lambda_1+\lambda_2)(z-1)}$。连续情形用 Laplace transform（拉普拉斯变换）得到同样结论。这与 Strang 18.06 里 circulant matrix（循环矩阵）被 Fourier basis（傅里叶基）对角化是同一件事：变换把卷积变成逐点乘法，于是「分布族的卷积封闭」退化成「参数的加法」。你在第 4 章见过这条路的另一种走法：直接用 transforms（生成函数）算，本节只是把它翻译成过程语言。
>
> 最后接一处工程与一处边界。CSAPP 的并发服务器里，多个客户端连接（各自近似泊松）汇入同一个 accept queue（接入队列），服务速率固定，利用率 $\rho=\lambda/\mu$ 决定排队长度，而这里的 $\lambda$ 正是各源速率之和——排队论的门就在这儿。边界在反方向：合并之后你只看得见「有到达」，看不出它来自哪个源，把合并流拆回各自分量叫 deconvolution（反卷积），统计上只能靠标签比例与二阶矩去反推，且需要额外假设；这也解释了为什么分裂（知道标签）容易、合并后还原（丢掉标签）很难。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 两个独立指数随机变量取小，结果仍是指数、参数相加——这是本节最反直觉的一句：一般函数会把随机变量踢出原来的分布族，取最小值却把它留在族里，只换了参数。为什么偏偏这个结论成立？因为它靠的是 survival function（生存函数），不是分布函数：最小值大于 $z$ 等价于每一个都大于 $z$，这是交集，独立性允许逐项相乘；而「最小值不超过 $z$」是并集，要容斥，一路会脏到底。
>
> 推导只有一行：$P(\min>z)=P(T_a>z)P(T_b>z)=e^{-(\lambda_a+\lambda_b)z}$，右端正是参数为和的那个指数的生存函数，于是立刻读出分布。期望用 tail integral（尾积分）$E[\min]=\int_0^{\infty}P(\min>z)dz=1/(\lambda_a+\lambda_b)$；这条对非负随机变量恒成立，交换求和与积分的依据是实分析里的 Tonelli theorem（托内利定理），不需要额外假设。
>
> 代数字，并且说清这个数对应什么系统。取 $\lambda_a=1/2$ 每小时、$\lambda_b=1/3$ 每小时，最小值服从率 $5/6$ 的指数，均值 $1.2$ 小时，比单件的 $2$ 小时和 $3$ 小时都短。取最小值对应的是 series（串联）系统，也就是 competing risk（竞争风险）模型：任一部件坏，系统就坏。旧注把它说成并联，方向反了——并联冗余要求全部坏掉系统才坏，寿命是最大值。
>
> 第二个问题是谁先响：$P(T_a<T_b)=\lambda_a/(\lambda_a+\lambda_b)=3/5$，率之比就是胜出概率之比，与合并里「这一次是谁来的」是同一个比值。更强的一条是胜者身份与获胜时刻独立：给定 $a$ 先坏，那个时刻仍然是率之和的指数。工程上这套结构叫竞争风险模型，串联系里它就是「哪一件先失效」，而「谁先」这个离散标签与「何时」这个连续量被彻底解耦。
>
> 换成 hazard rate（危险率）的语言看，率相加为什么干净：两个独立时钟同时走，单位时间里至少响一个的强度就是各自之和，因为 $\lambda_a\delta+\lambda_b\delta+o(\delta)$。危险率相加对应的正是取最小值，也就是串联。指数分布是唯一危险率恒等于常数的连续分布，所以串联系统仍是指数，同族封闭几乎是定义推出来的——前提说清：任一失败即系统失败。
>
> 并联冗余走的是另一条路，值得一并记住，因为它常被与串联搞混。并联系统的寿命是 $\max$，不是 $\min$；两盏同率 $\lambda$ 的灯，生存函数是 $1-(1-e^{-\lambda t})^{2}$，危险率随时间递减——早期有备份，坏一个还剩一个，风险比单件低；后期只剩一个，风险才回到单件的水平。所以并联的收益在均值上，而它的危险率不是常数。
>
> 并联要算就一笔写完：两个部件的最大值的期望是 $1/\lambda_a+1/\lambda_b-1/(\lambda_a+\lambda_b)$，代入 $1/2$ 与 $1/3$ 得 $2+3-1.2=3.8$ 小时。同一组参数，串联 $1.2$、并联 $3.8$——这才是冗余的收益，旧注把它写成「代价」，方向正好反了。
>
> 再看量级，避免把率相加读成概率相加：$P(\min>1)=e^{-5/6}\approx0.435$，一小时内至少坏一盏的概率约 $0.565$，比单看任一盏的 $0.393$ 与 $0.283$ 都高，但远不到 $1$。
>
> 推广：$n$ 个独立指数的最小值服从率 $\lambda_1+\cdots+\lambda_n$ 的指数，这是下一个例子把三盏灯拆成率 $3\lambda$、$2\lambda$、$\lambda$ 三段的全部依据——第 $k$ 个坏掉与第 $k+1$ 个坏掉之间的间隔，正是当时还活着的那些灯的最小值。
>
> 边界与接口。族外立刻失效：寿命若服从 Weibull distribution（韦布尔分布）或均匀分布，最小值就掉出同族，只能回到积分与容斥；并联的族外情形更糟，最大值几乎没有封闭性可言。跨课程接两处：6.006 里「多个随机试验谁先成功」就是这套竞争结构，6.042J 里独立几何取最小值仍是几何，但成功概率是 $p_1+p_2-p_1p_2$ 而不是率相加；只有连续侧才退化为 $\lambda_1+\lambda_2$，两边共用一句话——最小化对率是加法，对分布形状是保值。


为对这一事实给出更直观的解释，我们把 $T_a$ 与 $T_b$ 视为两个速率分别为 $\lambda_a$ 与 $\lambda_b$ 的相互独立泊松过程中首次到达的时刻。若把这两个过程合并（merge），首次到达时刻将是 $\min\{T_a, T_b\}$。但我们已知合并后的过程是速率为 $\lambda_a + \lambda_b$ 的泊松过程，于是可推出首次到达时刻 $\min\{T_a, T_b\}$ 是参数为 $\lambda_a + \lambda_b$ 的指数分布。

上述讨论可以推广到两个以上过程的情形。因此，把 $n$ 个到达速率分别为 $\lambda_1, \ldots, \lambda_n$ 的独立泊松过程的到达合并后所得的总到达过程，是到达速率等于和 $\lambda_1 + \cdots + \lambda_n$ 的泊松过程。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 6.16　更深入的竞争指数（More on Competing Exponentials）。**</span>

三只灯泡的寿命是相互独立的指数随机变量，具有公共参数 $\lambda$。问直到最后一盏灯泡烧坏为止的时间的期望值（expected value）是多少？

我们把每盏灯泡烧坏的时刻视为相互独立泊松过程中的首次到达时刻（first arrival times）。起初共有三只灯泡，合并后的过程速率为 $3\lambda$。因此首次烧坏时间 $T_1$ 服从参数为 $3\lambda$ 的指数分布，均值为 $1/(3\lambda)$。一盏灯泡烧坏之后，由指数分布的无记忆性（memorylessness），另外两只灯泡的剩余寿命又成为参数为 $\lambda$ 的相互独立的指数随机变量。于是我们有两个并行运行的泊松过程，这两个过程中任一过程的首次到达所剩余的等待时间 $T_2$ 现在服从参数为 $2\lambda$ 的指数分布，均值为 $1/(2\lambda)$。最后，当第二盏灯泡烧坏后，就只剩下一盏。再次利用无记忆性，直至最后一盏灯泡烧坏的剩余时间 $T_3$ 服从参数为 $\lambda$ 的指数分布，均值为 $1/\lambda$。因此，总时间的期望值为

```math
E[T_1 + T_2 + T_3] = \frac{1}{3\lambda} + \frac{1}{2\lambda} + \frac{1}{\lambda}.
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 6.16 要的是最后一盏灯烧坏的时刻，也就是三个独立指数随机变量的最大值。直接算会很难看：最大值不超过 $t$ 意味着三个都不超过 $t$，分布函数是立方的 $F(t)^{3}$，密度要按乘积求导裂成三支，期望又要写成积分再分部。chain decomposition（链条式分解）不改问题，只改记账方式：把时间轴按「还亮着的灯数」切成三段，每一段都是当前最小值的等待，于是最大值被写成三个等待之和。
>
> 逐段看。起初三盏都亮，第一盏坏的时刻是三个独立指数的最小值，由 competing exponentials（竞争指数）的结论服从参数 $3\lambda$ 的指数，均值 $1/(3\lambda)$。一盏坏掉之后，剩下两盏的剩余寿命靠 memorylessness（无记忆性）重新成为独立同分布、参数 $\lambda$ 的指数，并且与上一段的等待独立——严格理由是：把每盏灯看成各自独立泊松过程的首次到达，不相交区间上的到达互相独立，所以「已经活了多久」不影响「还要活多久」。第二段率 $2\lambda$，第三段率 $\lambda$。
>
> 代数字落地。取 $\lambda=1/1000$ 每小时，单灯平均寿命 $1000$ 小时，则期望 $=(1/3+1/2+1)\times1000=1833$ 小时，约 $76$ 天；方差 $=(1/9+1/4+1)\times10^{6}=49/36\times10^{6}$，标准差约 $1167$ 小时；变异系数是 $7/11\approx0.636$，比单个指数的 $1$ 小得多——三个独立分量相加时均值与方差同时相加，相对波动被压下去，这是「和」的一般行为。
>
> 这里有一个必须澄清的坑：三段相加不是三只灯各自的寿命相加。三只灯寿命之和的期望是 $3/\lambda=3000$ 小时，而最大值的期望只有 $1833$ 小时，且恒有 $\max\le\sum$。误读的根源在第二段：它的期望 $1/(2\lambda)$ 比单灯寿命 $1/\lambda$ 小一半，因为等到第一盏坏掉时，活着的那两盏已经不是刚出厂的两盏，剩余寿命被无记忆性重置了。
>
> 换一条完全不同的路验算一遍。最大值不超过 $t$ 的概率是 $(1-e^{-\lambda t})^{3}$，于是期望等于 $\int_0^{\infty}[1-(1-e^{-\lambda t})^{3}]dt$；把被积式展开成 $3e^{-\lambda t}-3e^{-2\lambda t}+e^{-3\lambda t}$，逐项积分得 $(18-9+2)/(6\lambda)=11/(6\lambda)$，与逐段相加一字不差。这条验算顺带说明链条分解为什么合法：展开式里每一项 $e^{-k\lambda t}$ 的特征率正是 $k\lambda$，对应「还亮 $k$ 盏」那一段；两种写法总和相同，因为按状态分段与按容斥展开本来就是同一件事的两种记账方式。
>
> 推广到 $n$ 盏同参数灯：还亮 $k$ 盏时的等待服从率 $k\lambda$ 的指数，于是 $E[\max]=H_n/\lambda$，$H_n$ 是 harmonic number（调和数），$n$ 大时约 $(\ln n+\gamma)/\lambda$；方差是 $\sum_{k=1}^{n}k^{-2}/\lambda^{2}$，$n\to\infty$ 时趋于 $\pi^{2}/(6\lambda^{2})$。取 $n=3$ 代入，$1+1/4+1/9=49/36$，与前面的数对上——调和数与平方倒数和不是背下来的，是一段一段数出来的。
>
> 跨课程接一处，但要接得准确。6.042J 的 coupon collector（赠券收集）里同一个调和数出现，离散侧的期望抽取次数是 $nH_n$。常见的错误读法是「每步平均耗时 $1/(n\lambda)$，乘 $nH_n$ 就回到 $H_n/\lambda$」——这样读把逐段变化藏起来了，而且「每步」指代不清：若步指抽取，平均每个抽取间隔是 $1/(n\lambda)$；若步指段，平均每段耗时是 $H_n/(n\lambda)$，取 $n=3$、$\lambda=1$ 得 $0.6111$，而首段 $0.3333$ 只是首段的均值。正确的配对是逐段的：还活 $k$ 盏那一段，连续侧期望 $1/(k\lambda)$；还缺 $k$ 个 coupon 时，离散侧期望 $n/k$ 次抽取；两段相乘 $n/k$ 乘 $1/(n\lambda)$ 恰为 $1/(k\lambda)$，逐项相等，求和得 $H_n/\lambda$ 对 $nH_n/(n\lambda)$。
>
> 最后一句方法论。期望那一步只用线性性，CLRS 的附录强调过 $E[X+Y]=E[X]+E[Y]$ 不要求独立，所以光求均值不需要三段独立；方差那一步才需要独立，而独立性是链条分解顺便多给的——无记忆性把联合分布切成了三个独立分量。这种「多证一点、换一个额外结论」的结构，在次序统计量与可靠性分析里会反复出现。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这张表的四行看起来是四个巧合，其实共用一套两行就能写完的算术。设 $Y=X_1+\cdots+X_N$，$N$ 与各 $X_i$ 独立，则 $E[Y]=E[N]E[X]$，而 $\mathrm{var}(Y)=E[N]\mathrm{var}(X)+\mathrm{var}(N)(E[X])^{2}$。这两条常合称 Wald 公式，不需要任何分布族假设，只要「先抽 $N$、再抽 $N$ 个独立同分布的 $X$」这个模板成立。所以表里每一行都可以当场核对，而不是背结论。
>
> 核对行 1：$X\sim\mathrm{Bernoulli}(p)$、$N\sim\mathrm{Bin}(m,q)$，则 $E[Y]=mqp$，方差为 $mqp(1-p)+mq(1-q)p^{2}=mqp(1-pq)$，与 $\mathrm{Bin}(m,pq)$ 的方差 $m(pq)(1-pq)$ 完全一致。核对行 2：$N\sim\mathrm{Pois}(\lambda)$，则 $E[Y]=\lambda p$、方差 $\lambda p(1-p)+\lambda p^{2}=\lambda p$，均值与方差相等，正是 $\mathrm{Pois}(\lambda p)$ 的指纹。两条核对都是两条独立路线给出同一个数，这种核对比记住结论可靠得多，因为它连错在哪里都能指出来。
>
> 但要说清机制：这里的机制有两条根，不是一条。行 1 与行 2 的根是 thinning（稀疏化）：把每次到达以概率 $p$ 独立保留，计数分布留在原族里，靠的是 Bernoulli 的卷积封闭与二项分布的稀有极限。行 3 与行 4 的根才是 memorylessness（无记忆性）：几何分布与指数分布是离散与连续两边的指数律，它们对随机次数的和封闭。
>
> 这里必须更正一条旧注。旧注说「无记忆在复合下保值」是表里四个结论的公共根，这句话过宽，等于把一个只对行 3、4 成立的机制推广到全表。反例就在表内：binomial distribution（二项分布）不无记忆。无记忆的定义是对所有 $s,t$ 有 $P(X>s+t\mid X>s)=P(X>t)$，而二项分布的支撑是有限集 $\{0,1,\ldots,m\}$，取 $s+t>m$ 时左端为 $0$、右端为正，立刻破功。所以行 1、2 与无记忆毫无关系；照「四条同根」去记，遇到「泊松与泊松的复合」或「正态与二项的复合」这种表外情形就会无据可依——那里没有无记忆，但 Wald 公式与卷积封闭照样能用。正确的说法是：两条根，外加一个共同工具，即全期望与全方差公式。
>
> 想把四行一次算完，用 probability generating function（概率生成函数）的复合：$G_Y(z)=G_N(G_X(z))$。以行 3 为例，$G_X(z)=pz/[1-(1-p)z]$、$G_N(z)=qz/[1-(1-q)z]$，代进去化简，分子分母同时约掉 $1-(1-p)z$，得 $pqz/[1-(1-pq)z]$，正是参数 $pq$ 的几何母函数。这条复合公式在 branching process（分支过程）里就是 $G_{n+1}=G_n\circ G$ 的递推，也是复合分布这个名字的出处。
>
> 再补一组数字，让行 3、4 也落地。取 $p=0.2$、$q=0.1$：行 3 说 $Y$ 服从参数 $0.02$ 的几何分布，于是 $E[Y]=50$；用 Wald 公式算，$E[N]=10$、$E[X]=5$，乘积 $50$，一致。方差这一边，Wald 给出 $10\times20+90\times25=2450$，而参数 $0.02$ 的几何方差是 $0.98/0.0004=2450$，两边又对上。行 4 取 $\lambda=2$、$q=0.1$：$Y$ 服从参数 $0.2$ 的指数分布，$E[Y]=5$，Wald 给出 $10\times0.5=5$；方差 Wald 给出 $10\times0.25+90\times0.25=25$，指数方差是 $1/0.04=25$，同样相等。两组核对合起来说明：这张表是同一台机器换四种输入，只要模板成立，均值与方差就都被两条公式钉住。
>
> 最后提醒一个坑，就在正文末尾关于 Problem 24 的那句说明里。原文写的是：若 $T$ 是一个长度服从参数 $v$ 的指数分布、且与该泊松过程相互独立的区间，则 $N_T+1$ 服从参数 $v/(\lambda+v)$ 的几何分布。注意 $T$ 的身份——它是与过程独立的 $\mathrm{Exp}(v)$ 时长，是区间的长度，不是第 $N_T+1$ 次到达的时刻。旧注把它读成「第 $N_T+1$ 次到达的时刻」，正好把因果读反了：不是先有那个到达再定义 $T$，而是先抽一个随机长度 $T$、再数这段区间里有几次到达。第 $N_T+1$ 次到达在 $T$ 之后，这一点只是结论的副产品。
>
> 读对身份之后，「看上去正好是行 4 的应用」这一句也站不住了。行 4 要求 $N$ 与各 $X_i$ 独立；这里 $N_T$ 由 $T$ 决定，$T$ 又是长度，最后一段间隔被 $T$ 截断，两者并不独立。硬套行 4 等于把「$T$ 加残余」的和当成 $T$ 本身，于是算出的分布是两独立指数之和hypoexponential（两指数之和），而题设是单个 $\mathrm{Exp}(v)$；两者形状不同——均值都是 $1/v+1/\lambda$，但 Laplace 变换在 $v=1,\lambda=2,s=1$ 时前者给 $1/3$、后者给 $0.4$，只看均值抓不到。这个矛盾恰好标出依赖性的位置。正确做法是直接把 $T$ 积掉：$P(N_T=k)=\int_0^{\infty}e^{-\lambda t}(\lambda t)^{k}/k!\cdot v e^{-vt}dt=v\lambda^{k}/(\lambda+v)^{k+1}$，关于 $k$ 求和为 $1$，形状就是几何分布。所以行 4 的前件「$N$ 独立于 $X_i$」不是装饰，缺了它结论就假，这条比结论本身更值得记。


前两条性质在 Problem 22 中给出证明，第三条性质在 Problem 6 中给出，最后一条性质在 Problem 23 中给出。最后三条性质还曾借助生成函数在第 4 章中证明过（见 Section 4.4 与第 4 章章末的最后一个习题）。还有一条相关的性质在 Problem 24 中给出：若以 $N_t$ 记参数为 $\lambda$ 的泊松过程在长度为 $t$ 的区间内的到达次数，而 $T$ 是一个长度服从参数为 $v$ 的指数分布、且与该泊松过程相互独立的区间，则 $N_T + 1$ 服从参数为 $v/(\lambda + v)$ 的几何分布。

> <span style="color:#7f8c8d;">[原页此处 OCR 已修正] 表中 $\lambda$ 与 $v$（原文写作 `A`；`v`）等参数名、以及破折号断字（`pro­cesses`、`parame­ter`）均由本 worker 依语境改正；`PMFsjPDFs` 复原为 「PMFs/PDFs」；第 18 行 `let Y 0 when N O` 复原为「let $Y = 0$ when $N = 0$」。数值一律未臆造。</span>

让我们还注意到相关且颇为深刻的一个事实：大量（未必为泊松的）相互独立的到达过程之和，可以用一个泊松过程来近似，其到达率等于各分到达率之和。各分量过程相对于总量必须具有足够小的比率（这样就不会有哪一分量把自己的概率特征强加于总的到达过程之上），并且它们还必须满足某些技术性（technical）的数学假设。对该事实的进一步讨论超出本书范围，但我们注意到，在相当程度上它正是泊松型过程在实践中大量出现的原因。例如，一座城市中产生的电话业务量（telephone traffic）由大量……
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本页末尾这句话点到的那条事实，文献里叫 Palm–Khintchine theorem（帕姆—欣钦定理）。它的精确形式值得写清楚，因为条件比结论更容易被记漏：设有 $n$ 个相互独立的 stationary point process（平稳点过程）叠加，第 $i$ 个过程的率为 $\lambda_i$，总率 $\lambda=\sum_i\lambda_i$ 固定，并且每个源相对稀疏，即 $\max_i\lambda_i/\lambda\to 0$；则叠加过程 weak convergence（弱收敛）到率为 $\lambda$ 的泊松过程。注意「稀疏」不是形容词，它与结论同权：少了它，定理是假的。
>
> 稀疏为什么是命门，一算就明白。设各源独立平稳，小区间 $\delta$ 内两次及以上到达的概率约为 $\frac{1}{2}\sum_i\lambda_i^{2}\delta^{2}$，与「恰好一次」的 $\lambda\delta$ 相比，比值是 $\frac{\delta}{2}\cdot\frac{\sum_i\lambda_i^{2}}{\lambda}$。由于 $\sum_i\lambda_i^{2}\le\lambda\max_i\lambda_i$，这个比值不超过 $\delta\max_i\lambda_i/2$；只要 $\delta$ 远小于 $1/\max_i\lambda_i$，二阶项就已经可以忽略——旧注接着说稀疏性不是被假设出来的、是被每个源都很弱这件事在可见尺度上逼出来的，这句其实是同义反复：二阶项可忽略，正是稀疏条件 $\max_i\lambda_i/\lambda\to0$ 在某个具体 $\delta$ 尺度上的展开，不是它的推论。真正推不出来的是另一层：单靠总率固定、各源平稳独立，既得不到 $n\to\infty$，也得不到 $\max_i\lambda_i/\lambda\to0$；这两条必须作为定理的条件写进去。定理的极限是源数趋于无穷而每个源越来越弱，不是多叠几次就自动泊松。再加上独立性给出的无后效，泊松过程的三条定义性质就全齐了。
>
> 反面要看清楚，否则会把它用错。定理的极限是「单个源强度趋于 $0$、总强度固定」，不是「源的数量变多」。若不固定总率，而是把 $n$ 个强度相同的源直接叠加（例如 $n$ 台周期固定的设备各自报一次心跳），叠加流的间隔变异系数并不按 $1/\sqrt{n}$ 收缩：同参数泊松叠加后间隔仍是指数、CV 恒为 1；同周期随机相位叠加的间隔近似均匀分割，CV 反而从 0 升向 1。按 $1/\sqrt{n}$ 收缩的是固定窗口内计数的相对波动，在局部窗口里更像确定性节拍而不是泊松散布。Cox 与 Smith 在 1953 年把这类「叠加」的另一端也理清了：$n$ 条周期互不可公度的严格周期序列叠加会趋近泊松，而同周期序列叠加只是把同一个节拍乘上 $n$。两端放在一起看，「每个源相对总率足够小」这条限制就是定理的生死线。
>
> 与中心极限定理对照，结构一目了然：central limit theorem（中心极限定理）说「大量独立小贡献之和趋于正态」，Palm–Khintchine 说「大量独立稀疏点过程叠加趋于泊松」。两者都需要三件事——独立、单个贡献小、总量有界；中心极限定理管的是和的分布（一维分布函数的弱收敛），Palm–Khintchine 管的是整条点过程的分布，而它的数学语言是局部有限测度空间上的 vague convergence（模糊收敛）。两个定理不在同一个拓扑里，所以后者更强也更难。所以城市电话话务、交通事故、柜台排队之所以普遍呈泊松特征，不是因为每一个源都是泊松的，而是「很多个稀疏源叠加」这个结构本身把泊松逼了出来——这正是 §6.2 里分裂与合并那一套的「无极限版本」。
>
> 归属核一遍。Conny Palm（瑞典，1907–1951）1943 年在斯德哥尔摩 KTH 的博士论文 Intensitätsschwankungen im Fernsprechverkehr（电话话务的强度涨落）里给出了这套叠加分析，并引入后来称为 Palm probability（帕姆概率）的工具；Aleksandr Khinchin 在 1955 年的排队论专著里给出更严格的版本。英文维基的 Palm–Khintchine theorem（帕姆—欣钦定理）条目与施普林格出版社的点过程文献都把时间点记作 Palm 1943、Khinchin 1955，与旧注一致。顺带一句：Palm 的概率工具后来长成了整个 point process（点过程）理论的主干，reliability（可靠性）建模与排队网络都建在它上面。
>
> 最后给一个能量化的话务例子。某话局 $1000$ 个用户、每人平均每小时呼叫 $1$ 次，总量是每小时 $1000$ 次，约每秒 $0.278$ 次；单个用户的率只占总量千分之一，稀疏条件成立，于是总量可当泊松用。某秒内零次到达的概率是 $e^{-0.278}\approx0.757$，某秒内至少两次的概率约 $1-e^{-0.278}(1+0.278)\approx0.032$。工程上「按泊松算话务」以及呼损公式能用的全部依据，就在这两个数里：它们来自「很多弱源叠加」这个结构，而不是来自某个用户的行为模型。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「随机到达悖论」的谜底是 length-biased sampling（长度偏置抽样），但叙述上要先修一处容易犯的错。旧注把它说成「一个人随机落在时间轴的某点」，这与正文的告诫冲突：正文特意指出 $t^*$ 只是一个确定的 time instance（时间实例），不是随机变量，把入场叫 random incidence（随机到达）本身就是误导性的命名。正确的说法是：$t^*$ 固定，随机性来自 interarrival interval（到达间隔）长度的分布；被抽中的对象是「间隔」而不是「时刻」，而一个长度 $l$ 的间隔被抽中的概率正比于 $l$。这个区分不是抠字眼——若真把 $t^*$ 当随机点，就会以为结论依赖 $t^*$ 的取值，而对任何 $t^*$ 结论都一样，这正是 stationarity（平稳性）的含义。
>
> 正式论证在正文里已经写全，值得重述一遍以看清每步用了什么。事件 $\{t^*-\underline V>x\}$ 等价于区间 $(t^*-x,\,t^*]$ 内零到达；长度为 $x$ 的区间内到达数服从 $\mathrm{Pois}(\lambda x)$，于是零到达的概率是 $e^{-\lambda x}$，所以 elapsed time（已流逝时间）服从参数 $\lambda$ 的指数分布。remaining time（剩余时间）同一结论来自 memorylessness（无记忆性）。两者的独立性则来自不相交区间上的 independent increments（独立增量）：一个只由 $t^*$ 之前的过去决定，一个只由 $t^*$ 之后的未来决定。于是 $L$ 是两个独立的率 $\lambda$ 指数随机变量之和，即二阶 Erlang distribution（爱尔朗分布），密度 $\lambda^{2}\tau e^{-\lambda\tau}$，均值 $2/\lambda$、方差 $2/\lambda^{2}$。
>
> 代数字看偏置有多大。取平均间隔 $10$ 分钟（$\lambda=1/10$ 每分钟）：典型间隔的期望是 $10$ 分钟，被观测间隔的期望是 $20$ 分钟；$P(L>30)=e^{-3}(1+3)=4e^{-3}\approx0.199$，即约两成的随机到达者落在超过 $30$ 分钟的间隔里——而典型间隔超过 $30$ 分钟的概率只有 $e^{-3}\approx0.0498$，两者正好差一个因子 $1+\lambda\tau=4$——这个因子就是长度加权的全部算术：$t^{*}$ 落在长间隔里的机会被放大了这么多倍。再看一句日常错觉：即使你已经等了 $25$ 分钟，剩余等待仍服从率 $1/10$ 的指数、期望还是 $10$ 分钟，等待过程不会「记账」。这就是「公交悖论」的全部内容。
>
> 为什么两半都能是指数？因为指数分布是唯一具有无记忆性的连续分布，而泊松过程在任意时刻都「重新开始」，过去与未来对称。所以 $L$ 的均值是 $2/\lambda$ 而不是 $\lambda^{-1}$：不是把典型值翻倍的错误，而是两个独立随机量各贡献一个 $\lambda^{-1}$。这一点也可以从条件分布验证：给定 $t^*-\underline V=x$，$\overline V-t^*$ 的分布仍是率 $\lambda$ 的指数，与 $x$ 无关。
>
> 更一般地，这条偏置不依赖泊松。对任意平稳点过程，只要 $E[I^{2}]<\infty$，被观测间隔的期望就是 $E[I^{2}]/E[I]$，正文下一页的 Example 6.17 用 $5$ 与 $55$ 分钟的两点分布验证了这一点（$1525/30\approx50.83$）。泊松只是让结论更强：不仅均值被放大，而且 $L$ 的整个分布是二阶埃尔朗，「两半各自指数」。所以读这一节要分清两件不同强度的事：均值层的偏置普遍成立，分布层的结果是泊松特有的。
>
> 最后说两个用法与一个陷阱。用法一：CS144 里统计流长与 round trip time（往返时延）时，若在随机时刻抓包，看到的流长天然按长度加权，统计量会系统性偏大，要报告「典型流长」必须用 arrival sampling（按到达采样）。用法二：智能科学里做数据采样与实验设计，凡是「样本被观测到的概率取决于样本自身性质」的场合都是同一台机器。陷阱一：把已流逝时间的指数性当成普适结论。上面那一步依赖 $\mathrm{Pois}(\lambda x)$，也就是速率恒定；对非齐次的泊松过程（速率 $\lambda(t)$ 随时间变），$e^{-\lambda x}$ 不再成立，已流逝时间也不再是指数分布，只剩一个能量化的近似：$\lambda$ 变化足够慢时，可以按 $t^*$ 处的瞬时速率当成指数。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个 $E[I^{2}]/E[I]$ 不是背下来的公式，是「按长度加权再归一化」的一步推导。设典型间隔长 $I$ 的分布已知，被观测的那个间隔记为 $I^{*}$；一个长度为 $i$ 的间隔占据时间轴的份额正比于 $i$，所以它被 $t^{*}$ 命中的概率正比于 $i$，于是 $P(I^{*}=i)=iP(I=i)/E[I]$（连续情形把 $P$ 换成密度），这就是 size-biased distribution（长度偏置分布）。权重之和为 $\sum i\,P(I=i)=E[I]$，分母正是归一化因子；于是 $E[I^{*}]=\sum i\cdot iP(I=i)/E[I]=E[I^{2}]/E[I]$。
>
> 换个写法，这条公式的结构立刻现形：$E[I^{2}]/E[I]=E[I]+\mathrm{var}(I)/E[I]$。偏置的量恰好等于方差除以均值。于是两句经验话有了出处：间隔长度完全相同（方差为零）时没有偏置；间隔波动越大偏得越狠。前提也要记住：需要平稳性，并且 $E[I^{2}]<\infty$——重尾间隔下（例如方差发散的分布）被观测间隔的期望真的是无穷大，这时「平均等多久」这个问题本身就失效了，不是估计得不准。
>
> 代入本题走一遍。典型间隔以各半的概率取 $5$ 分钟与 $55$ 分钟，所以 $E[I]=\frac12\cdot5+\frac12\cdot55=30$，$E[I^{2}]=\frac12\cdot25+\frac12\cdot3025=1525$，比值 $1525/30\approx50.83$。用分解式核对：$\mathrm{var}(I)=1525-900=625$，$625/30\approx20.83$，加上 $30$ 正好 $50.83$，两条路给出同一个数。这一步值得亲手做，因为它把「偏置 ＝ 方差惩罚」变成了可以验算的算术，而不是一句比喻。
>
> 再往二阶走一步，看被观测间隔的分布有多集中。时间份额给出 $P(I^{*}=55)=55/60=11/12\approx0.9167$、$P(I^{*}=5)=1/12$，所以随便挑一个时刻，八成多一点的概率落在 $55$ 分钟的间隔里。二阶矩同样由长度加权给出 $E[I^{*2}]=E[I^{3}]/E[I]=\left(\frac12\cdot125+\frac12\cdot166375\right)/30=83250/30=2775$，于是方差 $2775-50.833^{2}\approx191.0$，标准差约 $13.8$ 分钟。注意标准差并不小：虽然多数时候落在 $55$，但偶尔落进 $5$ 分钟的间隔会把均值拽下来，两种情形混合出的波动比「几乎总是 $55$」给人的印象要大。再对照个数份额：典型间隔里有一半是 $5$ 分钟的短间隔，可是随机到达者落在短间隔里的概率只有 $1/12$，约 $0.083$——「一半个数」与「百分之八的时间」这对数字，比任何比喻都更能说明长度加权在做什么。
>
> 同一台机器换个变量名就是下一页的公交车载客调查。挑车时每辆车等概率入选，得到的是「平均每辆车多少人」$E[C]$；挑乘客时每名乘客一票，车被选中的概率正比于载客量 $C$，得到的是「平均每位乘客所在的车上有多少人」$E[C^{2}]/E[C]$，必然更大。这不是谁算错了，而是两个 estimand（被估计量）不同：前者是车辆的均值，后者是乘客视角的均值，后者天然偏向大车。判断该用哪个，只需问一句「我要回答的是谁的问题」。
>
> 最后接加权方法，并强调一个方向问题。抽样概率不均匀时，survey sampling（抽样调查）里的 Horvitz–Thompson estimator（霍维茨—汤普森估计量）为 1952 年 JASA 47(260):663–685 那篇论文所提出，用 $1/\pi_{i}$ 做权重，使总量估计无偏——它放大稀有小样本以还原总量。长度偏置的校正方向恰好相反：把每个观测乘以 $E[I]/I$，也就是把长的压回去。两个方向相反是因为目标不同：估总量时长间隔贡献大、要保留；估典型分布时每个间隔的投票权应当相同、要压回去。把 importance sampling（重要性采样）的权重直接套到分布估计上，结果仍然是偏的，这是这一节最容易被误用的地方。顺带一句算法侧的镜像：在哈希表里随机命中一个 key（键），它所在 bucket（桶）的大小的期望是 $E[B^{2}]/E[B]$，桶越大越容易被命中——6.006 里分析「随机访问的代价」时会再次遇到这个比值。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一段把 random incidence（随机到达）从时间轴搬到了「人群」上，机制一字不改。sample a vehicle（挑车）时每辆车被选中的概率相同，统计量是车辆层面的 average occupancy（平均载客量），数学上就是按车等权求 $E[N]$；sample a rider（挑乘客）时每名乘客被选中的概率相同，而他必定坐在某辆车上，于是载客量大的车被命中的机会正比于它的载客量，统计量变成 weighted by occupancy（按载客量加权）的平均 $E[N^2]/E[N]$。
>
> 两者之差不是随机误差，而是可以精确算出的确定量：$E[N^2]/E[N] - E[N] = var(N)/E[N]$。只要载客量存在波动，$var(N) > 0$，按乘客采样就必然 biased upwards（向上偏），偏多少由波动的幅度决定，一分不多一分不少。这个式子是本节所有「悖论」的统一骨架：时间轴上被观测间隔的期望 $E[I^2]/E[I]$ 之所以大于 $E[I]$，无非是把 $N$ 换成了间隔长度 $I$，方差非负而已。
>
> 同一个骨架在别的学科里叫别的名字。社会学里它叫 friendship paradox（友谊悖论），由 Scott L. Feld 在 1991 年的论文《Why Your Friends Have More Friends Than You Do》中命名，刊登于 American Journal of Sociology 第 96 卷第 6 期：随机挑一个人，他的朋友的平均朋友数平均而言大于他自己的朋友数。原因与车上情形完全同构 —— 「被挑中」这一步发生在 edge（朋友关系）上而非 node（节点）上，degree（度数）大的节点握着更多关系名额，被命中的概率正比于度数，于是加权后的平均度数等于 $E[D^2]/E[D]$，比 $E[D]$ 多出 $var(D)/E[D]$。排队论里同一现象叫 inspection paradox（检查悖论），Feller 在《An Introduction to Probability Theory and Its Applications》第二卷中以 waiting time paradox（等待时间悖论）之名讨论过。
>
> 对建模者而言，后果是可操作的：如果想估计「一辆车平均载多少人」，直接用乘客样本的均值是 biased estimator（有偏估计），必须给每条乘客样本乘上 importance weight（重要性权重）$1/N_i$；这样一来，无论车上有几名乘客，该车贡献的总权重都恰好是 1，等于把按乘客抽样换回了按车抽样。这是 importance sampling（重要性抽样）最朴素的形态，也是 Horvitz-Thompson 估计量的雏形。这类偏差在系统里无处不在：按请求采样测得的平均延迟、按会话采样测得的平均用户活跃度、按论文采样测得的平均被引次数，全都偏向大对象，因为大对象天然占据更多「被采样位」。顺带一提，这类修正并不免费：权重 $1/N_i$ 在样本所属对象很小时会把噪声放大，bias（偏差）与 variance（方差）之间的取舍在这里就已经显形，后面做加权估计时会反复遇到。
>
> 因此旧注那句「抽样机制决定统计量」可以升级成一条可执行的判据：看到任何一个「平均」，先问 uniform over what（在哪个集合上均匀），再问被选中概率是否正比于 covariate（某个协变量）；若不是均匀抽取，就必须加权修正，或者把结论老实改写成「按某某加权的平均」。这与 6.042J 反复强调的 sample space（样本空间）必须先精确描述、随机化算法必须说明在哪个集合上均匀随机，是同一条纪律的三种说法。顺带订正一处页码：随机到达现象从 PDF p331 的子节标题起讲，该页即原书 322 页，$E[I^2]/E[I]$ 的算式落在 PDF p332，该页即原书 323 页，旧注笼统写作 p331。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 收束全节的这句话是本章的方法论落点，值得一个字一个字拆开：所谓 typical interval（典型间隔）并不是一个对象，而是「对象 + 抽样协议」的联合体。同一个 Poisson process（泊松过程）里，interarrival interval（到达间隔）本身是独立同分布的 exponential random variable（指数随机变量），参数为 $\lambda$，这一点没有任何争议；有争议的永远是「被提到的那一个间隔是怎么被挑出来的」。挑法一变，分布就变。
>
> 三种挑法给出三个答案，可以并排写出来对照。其一，固定编号，取第 $k$ 个到达间隔：它服从 exponential distribution（指数分布），均值 $1/\lambda$。其二，固定时刻 $t^*$，取包含 $t^*$ 的那一段间隔 $L$：它服从二阶 Erlang distribution（Erlang 分布），概率密度为 $\lambda^2 x e^{-\lambda x}$，均值 $2/\lambda$，恰好是前者的两倍。其三，若把过程起点补回 0 时刻，问 $t^{*}$ 落在从 0 起编号的第几个间隔，则编号 $K$ 满足 $P(K-1=n)=e^{-\lambda t^{*}}(\lambda t^{*})^{n}/n!$。这一条必须先补上起点条件：正文为了不纠缠「$t^{*}$ 之前到底有没有到达」这类枝节，假定泊松过程从一开始就一直在运行，即 running forever；在那种设定下「第几个间隔」没有编号可言，$K$ 根本没有定义。补上起点，$K$ 才有意义，而 $K-1$ 正是 $t^{*}$ 之前的到达数。三个答案互相不矛盾，因为它们回答的是三个不同的问题，只是题目都被含糊地叫作「一次到达间隔的长度」。
>
> 第三项值得补一句推导，因为它是三者里最容易被当成随手一写的：$t^*$ 落在第几个间隔，当且仅当 $t^*$ 之前恰好发生了 $k-1$ 次到达，于是 $K - 1$ 与 $t^*$ 之前的到达数 $N(t^*)$ 是同一个量，而它的分布正是泊松分布。换句话说，$K$ 不是几何分布，而是「泊松加一」，并且随 $t^*$ 增大整体右移 —— 「第几个间隔」这个问题根本没有与时间无关的答案，必须写成「在时刻 $t^*$ 处发问」。
>
> 差别的根源是 length bias（长度偏置）：把采样点扔到时间轴上，它落在某段间隔里的概率正比于该段长度，于是长间隔被 over-represented（过度代表）。形式化地说，被观测间隔的分布不是原来的 $F$，而是 size-biased distribution（尺寸偏置分布）$F^*(x) = \frac{1}{E[X]}\int_0^x t\,dF(t)$，它是把原分布的密度乘以 $t$ 再归一化得到的。其期望 $E[X^2]/E[X]$ 大于 $E[X]$，差值精确等于 $var(X)/E[X]$ —— 这是同一个公式的第四次现身，前三次分别是公交站等车的期望、公交载客量的向上偏，以及离散情形下的胜利间隔。
>
> 这条元教训在工程上有直接对应。做性能测量时，按调用次数取平均与按时间采样取平均给出不同的「单次调用开销」，因为耗时长的调用被时间采样过度代表，profiler 的采样偏差就来自这里；缓存命中率按访问加权还是按请求加权、服务端延迟按请求平均还是按用户平均，也都是同一件事的三种皮肤。数学上它们通通是一次 change of measure（测度变换）：权重函数一改写，期望跟着改写，而对象本身分毫未动。
>
> 所以往后遇到任何「平均」「典型」「随机挑一个」，第一反应应当是三问：在哪个集合上均匀？被选中概率是否正比于某个量？如果要的是另一个测度下的期望，权重该怎么补？把这三问与 $E[X^2]/E[X]$ 这个公式一起收进长期记忆，比背下任何一个具体结论都值钱。顺带订正：本节讨论位于 §6.2 的 random incidence paradox（随机到达悖论）子节，起于 PDF p331，即原书 322 页，$E[I^2]/E[I]$ 的显式算式在 PDF p332，即原书 323 页。


<!-- ===== PDF p335 ===== -->

<span style="color:#c0392b;">**第 6 章　伯努利与泊松过程（The Bernoulli and Poisson Processes）**</span>

<span style="color:#c0392b;">**习题区（PROBLEMS）**</span>

<span style="color:#c0392b;">**§6.1　伯努利过程（The Bernoulli Process）**</span>

> <span style="color:#7f8c8d;">本页为第 6 章习题区开篇（原书印刷页 326）。页眉题为「Chap. 6 / The Bernoulli and Poisson Processes / PROBLEMS / SECTION 7.1」；此处「SECTION 7.1」系 OCR 将「SECTION **6**.1」误认所致，本章题为第 6 章、正文内容实为伯努利过程（伯努利与泊松过程）习题，故按 §6.1 定位，不作按字面传播。习题编号自 Problem 1 起。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 1.**</span>

Each of $n$ packages is loaded independently onto either a red truck (with probability $p$) or onto a green truck (with probability $1-p$). Let $R$ be the total number of items selected for the red truck and let $G$ be the total number of items selected for the green truck.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 第 6 章 Problems（习题区）从 Problem 1 一直排到 Problem 27，带星号的解析题集中在两段：Problem 4—7 与 Problem 18—27。也就是说前半段多数只给题干，后半段几乎每题都附英文 Solution（解答）。这个分布本身就值得利用：前半段用来练独立手推，后半段用来对照标准写法，先自己写完再翻解答，收益最大。另需注意习题区页眉的编号问题：源扫描里页眉写作 SECTION 7.1、7.2，而本章正文的节号是 §6.1 与 §6.2。这份文件的处置是两种解释并存——一处判为 OCR 把 6 误认成 7，一处疑为原书笔误；两种都能自圆其说，靠扫描件无法区分，所以行文一律按章节结构读作 §6.1 与 §6.2，同时明确记下这个悬而未决的点，待回查纸本。
>
> 这二十七题是前五章工具箱的 stress test（压力测试），主要武器只有四件：binomial distribution（二项分布）与 geometric distribution（几何分布）的 probability mass function（概率质量函数）、Pascal distribution（帕斯卡分布）、conditional expectation（条件期望）与 law of total expectation（全期望定律）、indicator random variable（指示随机变量）与 linearity of expectation（期望的线性性）。后两件你在 CLRS 附录 C 的 hiring problem（雇佣问题）里已经见过威力，这里它们会在随机到达、splitting（分裂）、merging（合并）三条主线下反复登场。
>
> 拿 Problem 1 试手，它把同一个二项模型换了几种问法。$n$ 件包裹独立地以概率 $p$ 装红车，红车件数 $R$ 服从二项分布，绿车件数 $G = n - R$。(a) 问的三件事一句话答完：$p_R(k) = \binom{n}{k} p^k (1-p)^{n-k}$，$E[R] = np$，$var(R) = np(1-p)$。这些都是把 $n$ 个独立的指示变量相加的标准结果，逐项验证一遍比记结论更值。
>
> (b) 问「第一件恰好独自占一辆车」，等价于其余 $n-1$ 件全部装进另一辆车，概率是 $p(1-p)^{n-1} + (1-p)p^{n-1}$：两项分别对应第一件上红车与第一件上绿车，只写一项是本题最常见的失分点。(d) 问 $R - G = 2R - n$，由线性性立刻得 $E[R-G] = n(2p-1)$ 与 $var(R-G) = 4np(1-p)$ —— 这里只做了随机变量的线性变换，连独立性都不需要论证，而减法让方差翻四倍，正是 $-G$ 与 $R$ 完全负相关的结果。
>
> (c) 问「至少一辆车恰好装一件」需要 inclusion-exclusion（容斥），或者等价地算补事件：两辆车都不是恰好一件。写开来是 $1 - P(R = 1) - P(G = 1) + P(R = 1, G = 1)$，其中最后一项只在 $n = 2$ 时非零 —— 两个补事件并不是互斥的，这正是容斥项不能省的原因，漏掉它就只在 $n = 2$ 上出错，属于最难自查的那类错误。
>
> (e) 问是这套题的第一个 conditioning（条件化）训练：已知前两件都上红车，剩下 $n-2$ 件的去向与这条信息独立，所以 $R$ 的条件分布是「2 加上二项分布」，条件期望与条件方差就是把 $(n-2)p$ 与 $(n-2)p(1-p)$ 原样搬过来 —— 常数平移只动均值、不动方差。这个「剥离已确定的部分、其余照原样」的手法，在第 7 章 Markov chain（马尔可夫链）的条件化分析里会反复出现，值得现在就练熟。
>
> 顺带一提，本章不少 PMF 都能用 $n = 1$ 或 $n = 2$ 的小情形手算验算，这是概率题最便宜的自查手段，比事后怀疑公式写下标要可靠得多。
>
> 最后记一个全书级的伏笔：Bernoulli process（伯努利过程）与 Poisson process（泊松过程）的 memorylessness（无记忆性）说的是「未来完全不依赖过去」；马尔可夫链的 Markov property（马尔可夫性质）说的是「未来只通过现在依赖过去」。前者是后者的退化情形，中间隔的只是一层「允许有记忆、但记忆长度为一」的推广。做题时把每一道等待时间题都当成一次状态转移来读，进入第 7 章会省很多力气。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问是 negative binomial distribution（负二项分布）的入场。先把三个量摆清楚：$Y$ 是第 $r$ 次成功发生时的试验序号，服从 $r$ 阶 Pascal distribution（帕斯卡分布）；$X = Y - r$ 是此前累计的失败数；题目要的是 $X$ 的 probability mass function（概率质量函数）。两者只差一个常数平移，所以 $p_X(k) = p_Y(k + r)$，方差一模一样，均值差 $r$。
>
> 计数论证只依赖一个事实：第 $r$ 次成功必须落在序列的最后一位，于是前 $k + r - 1$ 位里恰好有 $k$ 次失败与 $r - 1$ 次成功，这些 $r - 1$ 次成功可以落在前 $k + r - 1$ 位中的任意 $r - 1$ 个位置上，组合数 $\binom{k+r-1}{r-1}$，再乘上每种排列的概率 $p^r (1-p)^k$，得 $p_X(k) = \binom{k+r-1}{r-1} p^r (1-p)^k$，$k = 0,1,2,\ldots$。注意这里「最后一位固定」是拆题的钥匙：若忘了这一条而把 $r$ 次成功也自由排列，会多算一个因子。
>
> 这里有一个常被口头说成「隔板法」的细节值得澄清：真正的 stars and bars（星与隔板）是把 $n$ 个不可区分的球放进 $m$ 个盒子，方案数是 $\binom{n+m-1}{m-1}$；本题是「在 $k + r - 1$ 个可区分的位置里挑 $r - 1$ 个放成功」，属于 choosing positions（选位置）而非隔板。两者只是恰好落在同一族二项系数上，论证完全不同 —— 记混了会在「非负整数解计数」与「多重集排列」两类题之间来回翻车。
>
> 名字的来历也值得一句：负二项这个名字来自把二项式定理的指数取负，$(1-x)^{-r} = \sum_{k\ge 0} \binom{k+r-1}{r-1} x^k$，右侧系数正是上式剥掉 $p^r$ 与 $(1-p)^k$ 之后剩下的形状。所以它不是「另一个分布」，而是二项系数的负指数版本；$r = 1$ 时它退化为 geometric distribution（几何分布），这就是「几何分布是负二项的特例」这句话的确切含义。
>
> 均值的直觉：试验以 $p : (1-p)$ 的比率产出成功与失败，$r$ 次成功自然配给约 $r(1-p)/p$ 次失败，与 (b) 的算式 $E[X] = r/p - r$ 一致。方差 $var(X) = r(1-p)/p^2$ 与帕斯卡变量相同，因为平移常数不改方差。这两个式子还可以用「$r$ 段独立几何等待相加」重新推一遍：每次成功之间的等待独立同分布，和的均值与方差各自相加，与上面完全吻合。第 4 章曾用 transform（变换）证过同一结论，这里是第二种到达方式 —— 同一个事实的两条独立通路，是检验自己有没有真的理解的最好标尺。
>
> 这条「相加」的思路还顺手解释了 (b) 问的方差为何与帕斯卡变量完全相同：平移不改变离散程度，只有尺度变换才会。
>
> (c) 问给出一个漂亮的等价改写：第 $i$ 次失败发生在第 $r$ 次成功之前，当且仅当失败总数 $X \ge i$，所以答案是 tail probability（尾概率）$\sum_{k \ge i} p_X(k)$。另一条路看前 $r + i - 1$ 次试验：失败至少 $i$ 次等价于成功少于 $r$ 次，于是答案又等于 $\sum_{k=0}^{r-1} \binom{r+i-1}{k} p^k (1-p)^{r+i-1-k}$。两条路相等本身就是一个 combinatorial identity（组合恒等式），可以把 $r, i$ 取小值手算验证，也可以单独当练习去证。
>
> 最后提醒一句前提：这一整套干净公式的唯一支点是「试验之间相互独立」。一旦出现依赖，第 7 章的马尔可夫链就是反例，等待第 $r$ 个事件就不能再用二项系数数位置，必须改用 state analysis（状态分析）与线性方程组。也就是说，本注给的公式不是「等待 $r$ 次的通用答案」，而是「独立同分布试验下的答案」—— 把适用条件一起背下来，比只背公式重要。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题是连续时间的 random incidence（随机到达）在离散时间里的镜像，也是全章最值得玩味的一题。设定是这样：堂弟从很久以前就在打同一个游戏，每一局独立地以概率 $p$ 获胜；你在午夜闯入房间，恰好目睹他正在输掉当前这一局。问的是「最近一次胜利与下一次胜利之间的失败局数」的 probability mass function（概率质量函数）。
>
> 要害在于「你看到的是一局失败」这个条件，它把三段时间的编号摆定了：$t$ 是你看到的那一局的编号，$M$ 是最近一次过去的胜利的编号，$N$ 是未来第一次胜利的编号。于是 $X=N-t$ 是从下一局数到首次胜利为止的局数——含末尾那次胜利、不含当前这局，等于此后的失败局数加一，也就是 $N-1-t$ 次失败再补上一次计数。旧注把它说成「还要输几局、当前这局也计入」，量词就错了：真正还要输的是 $N-t-1$ 局。另一侧 $Y=t-M$ 从第 $M$ 局那次胜利之后数起，含当前局、不含胜利局 $M$，所以严格夹在两场胜利之间的失败数是 $t-M-1=Y-1$。两侧合起来才是 $L=N-M-1=X+Y-1$。
>
> 由 memorylessness（无记忆性），$X$ 与 $Y$ 都服从参数为 $p$ 的 geometric distribution（几何分布），而且相互独立 —— 独立性来自「过去」与「未来」分属不相交的时间段，这正是 Bernoulli process（伯努利过程）的独立性性质。于是 $L = N - M - 1 = X + Y - 1$：两个独立的几何变量相加，得二阶 Pascal distribution（帕斯卡分布）。
>
> 具体写出来：$L + 1$ 的概率质量函数是 $p_{L+1}(k) = (k-1) p^2 (1-p)^{k-2}$，$k \ge 2$，这正是二阶帕斯卡的式子；整体左移一位得 $p_L(i) = i\, p^2 (1-p)^{i-1}$，$i \ge 1$。注意这个分布不能简化成几何分布，它的形状里多出一个因子 $i$ —— 那个 $i$ 就是 length bias（长度偏置）在离散情形下留下的显式签名，与连续情形里 $E[I^2]/E[I]$ 的那个平方同源。
>
> 一个便宜的验算：取 $p = 1/2$ 手算前几项，$p_L(1) = 1/4$，$p_L(2) = 2 \cdot (1/4) \cdot (1/2) = 1/4$，$p_L(3) = 3 \cdot (1/4) \cdot (1/4) = 3/16$，概率在缓慢向 1 爬，重心明显靠后；而均值 $E[L] = 2/p - 1 = 3$，比「典型胜利间隔」的 $1/p = 2$ 大了一半。这种一分钟的小数值验算，能在考场上拦住绝大多数下标错误，也顺手把「偏长」这个词量化成了具体倍数。
>
> 悖论在哪里？相邻两场胜利之间的间隔平均只有 $1/p$ 局，但你随机降落点所在的那段「包含当前局的胜利间隔」$N - M$，期望是 $2/p$，整整翻了一倍。原因不必计算就能说清：一段长度为 $m$ 的间隔里有 $m$ 个位置可能被你命中，于是被命中的概率正比于长度，长间隔被 over-represented（过度代表）。离散版还有一个端点约定要小心：$L$ 数的是失败局数，两端的胜利局不算在内，所以 $E[L] = 2/p - 1$，而 $E[N - M] = 2/p$，两者只差这一个端点，别在山寨的答案之间对不上号时误以为推导错了。
>
> 顺带一提，(b) 问还要算 $L$ 的均值与方差，都能由「两个独立几何相加、再整体平移一位」直接读出：均值相加再减一，方差相加不受平移影响，不必回去重做无穷级数求和。
>
> 这个现象在不同学科里有不同名字：排队论里叫 inspection paradox（检查悖论），Feller 以 waiting time paradox（等待时间悖论）之名讨论过；寿命分析里说成「随机时刻落进的那枚灯泡寿命偏长」；离散情形就是本题。它会在第 7 章 Markov chain（马尔可夫链）的 steady-state behavior（稳态行为）分析、本章 Problem 27\* 里反复出现。先把「随机点被长间隔过度代表」这条直觉焊牢，后面每遇到「随机时刻」，都先问一句「它落在哪一段里」。做题时顺手在纸上画一条时间轴，把 $M$、$t$、$N$ 三个点标出来，比空想快十倍。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 7\* 把 uniform distribution（均匀分布）与「无穷多次独立公平地抛硬币」证成同一件事，是全书把离散与连续接起来的最干净的一处。构造是 $Y = \sum_{k \ge 1} X_k / 2^k$，也就是把 $Y$ 写成二进制小数 $0.X_1 X_2 X_3 \ldots$。题目要证的是双向的：硬币序列形成 Bernoulli process（伯努利过程）时 $Y$ 均匀，反过来 $Y$ 均匀时各位 $X_k$ 构成参数 $1/2$ 的伯努利过程。
>
> (a) 的第一性原理是对半剖分：每读入一位二进制位，就把候选区间缩短一半。$X_1 = 0$ 对应左半段 $[0, 1/2)$，$X_1 = 1$ 对应右半段，两者概率各为 $1/2$，与均匀分布把质量对半分完全一致；再读一位，区间四等分，每段概率 $1/4$。归纳到深度 $k$：前缀 $X_1, \ldots, X_k$ 取定一个具体串，等价于 $Y$ 落在某个长度 $1/2^k$ 的 dyadic interval（二分区间）之内，概率恰为 $1/2^k$。
>
> 这一步能收尾，靠的是「二分区间族足够密」：任何开区间都能被这类区间从内部逼近，于是任意区间的概率都被迫等于它的长度，cumulative distribution function（累积分布函数）只能是最朴素的那个 $F(y) = y$，即均匀分布。这与你在 6.006 学过的 binary search decision tree（二分搜索决策树）同构：深度 $k$ 的完全二叉树有 $2^k$ 片叶子，每片叶子恰是一个长度 $1/2^k$ 的区间。同一种树，概率论用它统计质量分配，算法用它统计比较次数。
>
> 端点处必须补一句严谨性：二进制展开在二分点上不唯一，例如 $1/2 = 0.1000\ldots = 0.0111\ldots$，两条展开给出不同的硬币序列，所以「$Y$ 对应唯一序列」是假的。但这个歧义只发生在可数多个点上，每个点的概率都是零 —— 正文正是用「$Y = y$ 要求无穷多位取定值，是零概率事件」来证明 $P(Y = y) = 0$ 的。实分析课里你会看到同一件事的另一种说法：可数集是 null set（零测集），Lebesgue measure（勒贝格测度）对可数改动完全不敏感。这句话值得现在就拆开，别让它变成黑箱：长度这类测度满足可加性，单点的长度是零，可数多个零相加仍是零，所以一个集合加上或去掉可数多个点，测度不变。概率里同一件事的说法是零概率事件不影响分布——一个是测度，一个是概率，两个说法是同一台机器的两种语言。
>
> (b) 的方向反过来更漂亮：已知 $Y$ 均匀，证各位独立且 $p = 1/2$。手段同样朴素 —— 区间等长则概率等，联合概率写成边缘概率的乘积，独立性就自动掉出来。把 (a) 与 (b) 合起来看，这道题实际上构造了一个从 $\{0,1\}^{\mathbb{N}}$ 到 $[0,1]$ 的 measure-preserving isomorphism（保测同构），只是要忽略那个零测的可数例外集。
>
> 顺带回答一个常被跳过的问题：为什么必须是无穷多位？若只取前 $k$ 位，$Y$ 只能落在 $2^k$ 个值上，是离散的，绝无可能均匀连续；而截断带来的误差上界 $2^{-k}$ 恰好就是 quantization error（量化误差）。所以「位数」与「精度」在这里是同一个东西的两种说法，数值库里多取几位就是多要一位二进制精度，没有任何玄机。
>
> 请把结论焊进长期记忆：uniform random number（均匀随机数）等价于无穷多个独立公平的 bit（比特）。它在随机化算法里是「随机源可以从抛硬币造出连续分布」的根据，在信息论里是「均匀分布每一位恰好提供一比特 entropy（熵）」的根据，在数值计算里是「伪随机数生成器只要比特序列像抛硬币，就够用」的根据。三处不同领域，同一条定理的三个侧面。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 12 是 indicator random variable（指示随机变量）加 linearity of expectation（期望的线性性）的教科书级演练：顾客数随机、每位顾客点哪种披萨也随机，两层随机叠在一起，乍看无从下手；一换成指示变量，复杂度立刻塌缩成一串求和。这套路数在 CLRS 的期望分析里是主力，雇佣问题与生日问题都是同一个入口。
>
> 第一步是拆。设 $I_i$ 表示「第 $i$ 种披萨至少被点一次」的指示变量，不同披萨种类数就是 $\sum_{i=1}^{n} I_i$。第二步是取期望：$E[\sum_i I_i] = \sum_i E[I_i] = \sum_i P(I_i = 1)$。这一步的合法性只依赖线性性 —— 它不要求各个 $I_i$ 相互独立，也不要求顾客数 $K$ 与种类选择独立。这是本题最容易被误解的地方：$I_1$ 与 $I_2$ 显然负相关，因为点了一种就少了一份概率给另一种，但求和照样成立，因为期望运算是线性算子，不挑剔被加项之间的关系。
>
> 第三步算单个概率。给定 $K$ 位顾客，每位独立地以 $1/n$ 选中第 $i$ 种，所以无人点第 $i$ 种的条件概率是 $(1 - 1/n)^K$。要对 $K$ 消去，用 law of total expectation（全期望定律），得到这个概率等于 $E[(1-1/n)^K]$。此时需要一条 Poisson distribution（泊松分布）的 moment generating function（母函数）恒等式：若 $K$ 服从参数 $\lambda$ 的泊松分布，则 $E[a^K] = e^{-\lambda(1-a)}$。代入 $a = 1 - 1/n$，得无人点第 $i$ 种的概率为 $e^{-\lambda/n}$。
>
> 于是 $P(I_i = 1) = 1 - e^{-\lambda/n}$，种类数的期望为 $n(1 - e^{-\lambda/n})$。这个答案的两个极限都值得看一眼：当 $\lambda$ 远低于 $n$ 时，展开得近似 $\lambda$ —— 顾客太少、几乎不重复，种类数就是顾客数；当 $\lambda$ 远高于 $n$ 时，答案逼近 $n$ —— 顾客太多，每种都被点过。真正需要这个闭式的地方，恰在两者之间的中间地带。
>
> 顺带把三个容易混淆的近亲分清。本题问的是「被覆盖到的种类数的期望」，靠指示变量求和就够，独立性完全不必要。coupon collector problem（优惠券收集者问题）问的是「集齐所有种类要等多久」，那是最大值型的等待时间，指示变量求和不够用，得对「到某时刻仍未集齐」的概率做 tail sum（尾部求和），再叠加容斥。birthday problem（生日问题）问的又是「有无碰撞的概率」，需要的是联合概率而非期望。三者共享同一个入口（指示变量），出口却完全不同。
>
> 反过来想一步，就知道这条路为什么无可替代：若要直接算出「恰好 $m$ 种被点」的完整分布，就得枚举顾客点单的所有组合方式，状态数随 $n$ 指数增长；而期望只要 $n$ 个边缘概率的和，代价是线性的。这是「求期望比求分布便宜」的一般现象，第 7 章求吸收时间时同样成立 —— 分布难以写出，期望却能靠线性方程组直接解出。
>
> 至于指示变量加线性性这个杠杆，在第 7 章 §7.4 absorption probability and expected time to absorption（吸收概率与吸收时间的期望）的分析里仍是一线主力，只是依赖结构从「独立」升级为「一阶依赖」，求和随之让位给 system of linear equations（线性方程组）。订正一处旧注的编号错误：原文把 §7.4 写成「本章 §7.4」，实为第 7 章 §7.4、原书 362 页起；第 6 章的三节分别是 6.1 伯努利过程、6.2 泊松过程、6.3 小结与讨论。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 题设要看准：从 $t=0$ 起开始用灯，一次只点亮一枚，坏了立刻换，新灯泡独立地以等概率选自 A 型与 B 型；A 型寿命服从参数 1 的 exponential distribution（指数分布），B 型服从参数 3 的同一种分布。十个小题表面各异，其实只靠三件事：混合、贝叶斯更新，以及「这不是泊松过程」。
>
> 第一件事：首坏时刻是混合，不是竞争。因为一次只有一枚灯在亮，首枚的类型先抽、寿命再抽，于是 $T$ 的生存函数是 $(1/2)e^{-t}+(1/2)e^{-3t}$，期望 $E[T]=(1/2)\times1+(1/2)\times(1/3)=2/3$ 小时。(a) 的答案就是 $2/3$。旧注写的 $1/4$ 是另一道题：两型同时点亮、并联运行时的最小值 $\min(X_A,X_B)$ 的均值，率相加得 4、期望 $1/4$。本题一次一枚，根本没有两条失效通道同时开着，所以那个结论用不上。
>
> 把方差也算一遍做核对。(d) 需要 $E[T^{2}]=(1/2)\times2+(1/2)\times(2/9)=10/9$，于是 $\mathrm{var}(T)=10/9-4/9=2/3$，标准差约 $0.816$ 小时。本题期望与方差恰好都等于 $2/3$，纯属这组参数的巧合，别当规律记。
>
> 第二件事：贝叶斯更新。(b) 问「$t$ 之前没有失效」的概率，就是上面那条生存函数，即 $(1/2)e^{-t}+(1/2)e^{-3t}$。(c) 已知无失效到 $t$，首枚是 A 型的后验是 $P(A\mid T>t)=e^{-t}/(e^{-t}+e^{-3t})=1/(1+e^{-2t})$，随 $t$ 单调上升，$t=1$ 时约 $0.8808$。含义清楚：B 型更快夭折，能活到 $t$ 就更可能是慢的那一支，于是「活得久」本身成了「类型偏慢」的证据。
>
> 第三件事，也是最容易踩空的一处：无记忆性只能用在一个类型内部，不能直接用在整个混合上。旧注说「已知用了 $t$ 小时仍未坏，剩余寿命分布与全新灯泡完全相同」——这对单一类型成立，对混合不成立，因为混合的危险率不是常数。正确做法是先按 (c) 更新类型后验，再在两个类型的剩余均值上加权：(j) 的答案是 $E[T\mid T>t]=t+[3e^{2t}+1]/[3(e^{2t}+1)]$，$t=1$ 时约 $1.9205$，而不是 $t+1/4$。核对一下 $t=0$：右端退化为 $2/3$，正是无条件均值，说明这个式子自洽。
>
> 陷阱那条也要改写。失效时刻序列不构成 Poisson process（泊松过程），因为瞬时速率在 1 与 3 之间随机跳变；但没有「首个例外」——第一个间隔同样是两个指数按 $1/2$ 混合的形状，不是率 4 的指数。旧注写「除了首个失效时刻之外」，这个例外不存在。准确的说法是：整条间隔序列既不独立、也不同分布；只有条件于类型序列之后，每段才是参数 1 或 3 的指数。
>
> 类型序列本身是一个参数 $1/2$ 的 Bernoulli process（伯努利过程），与寿命分布无关。所以 (e) 问「第 12 次失效恰好也是第 4 次 A 型失效」只依赖这条类型序列：前 11 次里恰好 3 次 A、第 12 次是 A，概率是 $\binom{11}{3}(1/2)^{12}$。而 (g) 问第 12 次失效时刻的分布，就必须同时用上「12 段寿命相加」与「逐段按类型混合」两条线索，不能偷懒。
>
> 最后把两个容易混的量彻底分开。(a) 的 $2/3$ 是首坏时刻的均值，由「先选型、后取寿命」这条混合结构决定；而 $\lambda_A/(\lambda_A+\lambda_B)=1/4$ 是「两枚灯泡同时点亮时谁先坏」的概率，只适用于两支同时在跑的情形。旧注说本题两个数恰好都是 $1/4$，其中一个是错的、另一个不属于本题的模型，所以那段对照要整段删掉。混着记的后果很具体：遇到双灯并联的题会用 $2/3$，遇到单灯轮换的题会用 $1/4$，两边同时错。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 19\* 展示了全书最省力的证明策略之一：不硬算 PDF 与积分，而是把随机变量「物化」为底层泊松过程的到达时刻（interpretation-based proof 的路线）。两个关键事实：独立指数的 min 仍指数且参数相加；「min 来自哪个过程」的概率按速率加权（λ_1/(λ_1+λ_2) 与 λ_2/(λ_1+λ_2)）。把 max{X₁,X₂} 拆成「等 min 的期望 + 条件等待」，竞争分解让一切一目了然。第一性原理：把抽象变量还原成过程对象，复杂的分布运算就变成直观的「谁先到、再等多久」。这个技巧在第 7 章是双重伏笔——superposition（合并）过程本身就是马尔可夫性质的到达版本，而「竞争 + 条件等待」正是 §7.5 连续时间马尔可夫链与排队论（如 M/M/1 离开时间）的标准动作。建议对比「直接积分」与「物化解释」两条路线的开销差，体会建模视角如何决定计算复杂度。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 27\* 的收尾展示了一个高频模板——条件化再消去：对 K 偶、K 奇两种情形分别算出「含 t 的到达间隔长度」的条件 PDF，得到同一个三阶 Erlang 分布，于是无条件 PDF 也必为三阶 Erlang。第一性原理：若某量的条件分布不随条件变化，无条件分布就等于这个共同分布——「条件无关 ⟹ 无条件相同」是最便宜的消去。本题同时是 random incidence（随机涉入）的连续版：Erlang(均值 2/λ) 到达过程在普通观察下间隔均值是 2/λ，而外部观察者 t 随机落点看到的间隔均值是 3/λ——长了 1.5 倍。这个「观察者偏差」与 p337 Problem 5\* 的离散版遥相呼应，是排队论 PASTA 性质与网络测量的种子。理解「随机点被长间隔捕获的概率与长度成正比」，你就能直觉地解释为何等待时间总比平均更久。


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
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把 m×m 转移概率矩阵想成一张加权邻接矩阵——这是 6.042J 图论的直系延续：P_{ij} > 0 ⟺ 从节点 i 到节点 j 有一条弧，权重即转移概率。你在离散数学学过的邻接矩阵幂给出「路径计数」((A^k)_{ij} = i 到 j 的 k 步路径数)；这里完全平行，(P^k)_{ij} = P(X_{n+k}=j | X_n=i) 是 k 步转移概率——把「计数」换成「加权概率和」，一切照旧。每行和为 1 表示从每个状态出发的概率质量守恒，对应图中每个节点加权出度为 1。对齐 Strang / 18.065：本书用行随机（每行和为 1），Strang 讲 PageRank 用列随机（每列和为 1），两者互为转置，注意别混。特征值 1 总有对应的平稳分布（左特征向量），第二大特征值控制收敛速度——这正是 §7.3 稳态的数学入口。用矩阵幂 P^k 的极限行为去预览第 7 章后半段，是 18.065 眼光的最短路径。


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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 转移概率图 = 一张带权有向图：节点是状态，弧是允许的转移，权重是 P_{ij}。这与 CSAPP 的 FSM（有限状态机）形成完美对照：FSM 是确定性的（状态 + 输入 ⟹ 唯一后继），马尔可夫链是概率性 FSM（状态 ⟹ 一个概率分布）。两者的共同灵魂是「状态封装历史」——无论过去走过多长的路，未来只由当前状态决定，这正是你在 CSAPP 数字电路（时序逻辑）、正则表达式匹配器里反复见过的抽象。自转移（$P_{ii}>0$ 的情形）看似无趣实则有深意：它强调「时刻」推进了而「状态」未必改变，对应 FSM 里「留在原状态等待下一个时钟沿」。从图论看（6.042J），每个节点的加权出度和为 1（概率质量守恒），强连通分量、可达性这些老朋友将在 §7.2 状态分类中直接登场。把「马尔可夫链 = 概率版 FSM + 加权有向图」的三层身份刻进脑海，读第 7 章会一路顺畅。


<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 7.1（Alice 的概率课）**</span>

Alice 正在上一门概率课（probability class），在每一周，她要么跟得上进度（up-to-date），要么可能已落后（fallen behind）。如果某一周她跟得上进度，那么下一周她跟得上（或落后）的概率为 $0.8$（或 $0.2$）。如果某一周她已落后，那么下一周她跟得上（或落后）的概率为 $0.6$（或 $0.4$）。我们假定这些概率并不依赖于她前几周是跟得上还是落后，因此该问题具有典型的马尔可夫链特征（Markov chain character）——未来对过去的依赖仅通过现在（the future depends on the past only through the present）。
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 7.1 是整章最简但最完整的运行例子，值得现在就用手头的线性代数武器解剖它。转移矩阵 P = [[0.8, 0.2], [0.6, 0.4]]（行随机）。用 Strang / 18.065 的矩阵幂语言：P^k 的行收敛到平稳分布 π = (0.75, 0.25)——验证 πP = π：0.75·0.8 + 0.25·0.6 = 0.75 成立。特征值谱是 {1, 0.2}：特征值 1 对应平稳分布（Perron 根），第二大特征值 0.2 决定收敛速率——每步误差缩为 0.2 倍，约 10 步后误差小于百万分之一。这就是 §7.3 稳态与收敛速度定理的直观预览：链的长期行为由矩阵幂的极限刻画，「多快到达稳态」由第二大特征值控制。对 Alice 而言，「本周状态」就是预测下周的全部信息——她不必记得前几周，这正是马尔可夫性质的活标本。把这道两状态例题当作你检验后面所有定理的试验田，收益最大。


> <span style="color:#7f8c8d;">本页在陈述完 Example 7.1 的题面后结束；该例的转移概率图与后续求解延续到下一页。</span>


