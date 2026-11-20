<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）</span>

<span style="color:#c0392b;">**Recitation 5 解答（Recitation 5 Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 9 月 23 日）</span>

<span style="color:#7f8c8d;">（本 PDF 为解答版：各题仅含解答文字，未附题面。）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> <span style="color:#1e8449;">[note] 本题要求从「$n$ 次独立投掷、每次正面概率为 $p$」这一模型出发，逐层推导出 binomial（二项）分布的三条结论。教材对应位置是第 2 章（离散随机变量）：(a) 二项 PMF 的计数推导在 Section 2.2 例 2.6（中译本第 84–85 页）；(b) 二项期望在 Section 2.3（第 86 页）；(c) 二项方差在 Section 2.4（第 87 页）。为便于对照，把三段推导完整列出如下。</span>
>
> **(a)** 二项 PMF 的推导：设一次 Bernoulli（伯努利）试验成功概率为 $p$（失败概率 $1-p$）。考虑 $n$ 次独立试验中成功次数为 $k$ 的事件。任一**特定**成功顺序（例如前 $k$ 次成功、后 $n-k$ 次失败）发生的概率为 $p^{k}(1-p)^{n-k}$（由独立性，各次概率相乘）。而成功 $k$ 次的不同顺序共有 $\binom{n}{k}$ 个（从 $n$ 个位置中选出 $k$ 个放成功）。这些顺序两两互斥，故把概率相加即得
>
> ```math
> p_X(k) = \binom{n}{k}\, p^k (1-p)^{n-k}, \qquad k = 0, 1, \ldots, n.
> ```
>
> **(b)** 二项期望的推导：把成功次数 $X$ 写成 $n$ 个 indicator（指示）随机变量之和 $X = X_1 + \cdots + X_n$，其中 $X_i$ 在第 $i$ 次试验成功时为 $1$、否则为 $0$。每个 $X_i$ 是 Bernoulli 随机变量，故 $E[X_i] = 1 \cdot p + 0 \cdot (1-p) = p$。由期望的 linearity（线性性，无论 $X_i$ 是否独立都成立）：
>
> ```math
> E[X] = E[X_1 + \cdots + X_n] = E[X_1] + \cdots + E[X_n] = np.
> ```
>
> **(c)** 二项方差的推导：由于各次试验相互独立，$X_1, \ldots, X_n$ 相互独立。对独立随机变量，和的方差等于方差之和（variances add），故
>
> ```math
> \mathrm{var}(X) = \mathrm{var}(X_1) + \cdots + \mathrm{var}(X_n).
> ```
>
> 每个 $X_i$ 的方差：$E[X_i^2] = E[X_i] = p$（因 $X_i^2 = X_i$），故
>
> ```math
> \mathrm{var}(X_i) = E[X_i^2] - (E[X_i])^2 = p - p^2 = p(1-p),
> ```
>
> 于是
>
> ```math
> \mathrm{var}(X) = n\,p(1-p).
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** $X$ 是一个 binomial（二项）随机变量，参数 $n = 10$、$p = 0.2$。因此
>
> ```math
> p_X(k) = \binom{10}{k}\, 0.2^k\, 0.8^{10-k}, \qquad k = 0, \ldots, 10,
> ```
>
> 且当 $k$ 取其他值时 $p_X(k) = 0$。
>
> <span style="color:#7f8c8d;">【图】原页此处为 $p_X$（$n = 10$、$p = 0.2$ 的二项 PMF）的条形图：横轴为命中次数（number of hits）$0$–$10$，纵轴为概率（probability）$0$–$1$。原图由后处理统一插入。</span>
>
> **(b)** 无命中（no hits）的概率：
>
> ```math
> P(\text{No hits}) = p_X(0) = (0.8)^{10} = 0.1074.
> ```
>
> **(c)** 命中多于未命中（more hits than misses）的概率：
>
> ```math
> P(\text{More hits than misses}) = \sum_{k=6}^{10} p_X(k) = \sum_{k=6}^{10} \binom{10}{k}\, 0.2^k\, 0.8^{10-k} = 0.0064.
> ```
>
> <span style="color:#1e8449;">[note] 原文此小问写作 "More hists than misses"，其中 "hists" 应为 "hits"（命中）之笔误。另外，$n = 10$ 时"命中多于未命中"即 $k \ge 6$（命中 $k$ 次意味着未命中 $10-k$ 次，$k > 10-k$ 即 $k > 5$，故整数 $k$ 从 $6$ 起）。</span>
>
> **(d)** 由于 $X$ 是 binomial（二项）随机变量（其均值与方差公式即 Problem 1 所推导的 $np$ 与 $np(1-p)$），
>
> ```math
> E[X] = 10 \cdot 0.2 = 2, \qquad \mathrm{var}(X) = 10 \cdot 0.2 \cdot 0.8 = 1.6.
> ```
>
> **(e)** $Y = 2X - 3$，因此
>
> ```math
> E[Y] = 2E[X] - 3 = 1, \qquad \mathrm{var}(Y) = 4\,\mathrm{var}(X) = 6.4.
> ```
>
> <span style="color:#1e8449;">[note] 此处用期望的线性性 $E[aX+b] = aE[X]+b$（取 $a=2,b=-3$）；方差用 $\mathrm{var}(aX+b) = a^2\,\mathrm{var}(X)$（常数 $b$ 平移不改变散布，缩放 $a$ 使方差乘 $a^2$）。</span>
>
> **(f)** $Z = X^2$，因此
>
> ```math
> E[Z] = E[X^2] = \left(E[X]\right)^2 + \mathrm{var}(X) = 4 + 1.6 = 5.6.
> ```
>
> <span style="color:#1e8449;">[note] 最后一步用恒等式 $\mathrm{var}(X) = E[X^2] - (E[X])^2$ 变形得 $E[X^2] = (E[X])^2 + \mathrm{var}(X)$，代入 $E[X]=2$、$\mathrm{var}(X)=1.6$ 即 $4 + 1.6 = 5.6$。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> <span style="color:#1e8449;">[note] 由 (a)(b) 可反推题意：四辆巴士分别载有 $40$、$33$、$25$、$50$ 名学生；$X$ 为随机抽取的一名学生所乘巴士的载客数，$Y$ 为随机抽取的一辆巴士的载客数。总学生数为 $40 + 33 + 25 + 50 = 148$。</span>
>
> **(a)** 我们预期 $E[X]$ 高于 $E[Y]$：因为如果先选学生，我们就更有可能挑到载客较多的车。
>
> **(b)** 为把这道题形式化地解出，我们先计算每个随机变量的 PMF（概率质量函数），再计算它们的 expectation（期望）。
>
> ```math
> p_X(x) =
> \begin{cases}
> 40/148, & x = 40, \\
> 33/148, & x = 33, \\
> 25/148, & x = 25, \\
> 50/148, & x = 50, \\
> 0, & \text{otherwise}.
> \end{cases}
> ```

<!-- ===== PDF p2 ===== -->

> **（续）** 且
>
> ```math
> E[X] = 40 \cdot \frac{40}{148} + 33 \cdot \frac{33}{148} + 25 \cdot \frac{25}{148} + 50 \cdot \frac{50}{148} = 39.28.
> ```
>
> ```math
> p_Y(y) =
> \begin{cases}
> 1/4, & y = 40, 33, 25, 50, \\
> 0, & \text{otherwise}.
> \end{cases}
> ```
>
> 且
>
> ```math
> E[Y] = 40 \cdot \frac{1}{4} + 33 \cdot \frac{1}{4} + 25 \cdot \frac{1}{4} + 50 \cdot \frac{1}{4} = 37.
> ```
>
> <span style="color:#1e8449;">[note] 原文此处结论句为"显然，$E[X] > E[Y]$"。"显然"不可作为论证——把比较说清楚：$E[X]$ 是把各车载客数按**学生占比**（$x/148$）加权，$E[Y]$ 是按**车辆均分**（各 $1/4$）加权。前者给大车更大的权重（$50/148 > 1/4$，$25/148 < 1/4$），故 $E[X]$ 更大。</span>
>
> <span style="color:#1e8449;">[mathtip] $E[X] > E[Y]$ 的原因是尺寸偏置（size-biasing）：按学生抽样时，大小为 $x$ 的车被抽中的可能性与 $x$ 成正比——实际上 $p_X(x) = \dfrac{x}{148} = \dfrac{x}{37} \cdot \dfrac{1}{4} = \dfrac{x}{37}\, p_Y(x)$。</span>
>
> <span style="color:#1e8449;">[mathtip] 这里 $\sum_x x\,p_Y(x) = 37$ 恰是平均每车载客数，而 $x/37$ 是"载 $x$ 人的车相对于平均车"的放大倍数：$p_X(x) = \frac{x}{37} p_Y(x)$ 正说明按学生抽样时，$x$ 越大的车越容易被抽中。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">[solution]</span> 单次博弈（game）的收益（gain）的期望值为无穷大：因为若 $X$ 是你的收益，则
>
> ```math
> E[X] = \sum_{k=1}^{\infty} 2^k \cdot 2^{-k} = \sum_{k=1}^{\infty} 1 = \infty.
> ```
>
> <span style="color:#1e8449;">[note] 这个博弈的规则是：反复投掷一枚公平硬币，直到第一次出现正面为止；若第一次正面出现在第 $k$ 次投掷，则你得到 $2^k$ 元。由于第 $k$ 次才首次出现正面要求前 $k-1$ 次都是反面、第 $k$ 次是正面，故其概率为 $(1/2)^{k-1} \cdot (1/2) = 2^{-k}$，收益恰为 $2^k$，于是第 $k$ 项的期望贡献 $2^k \cdot 2^{-k} = 1$。把这些项对 $k = 1, 2, 3, \ldots$ 全部加起来，得到无穷多个 $1$，故期望为无穷大。</span>
>
> 因此，如果要在"支付给定费用 $f$ 参与博弈"与"干脆不玩"之间做选择，而你的目标是使期望净收益（expected net gain）最大化，那么你愿意支付任意大小的 $f$。然而，这与个人的实际行为严重相悖：事实上，实验表明大多数人只愿意支付约 \$20 至 \$30 来玩这个游戏。这一偏差源于一个预设：愿意支付的金额由期望收益决定。然而，期望收益并没有把一个人对待冒险（risk taking）的态度考虑在内。
>
> <span style="color:#1e8449;">[mathtip] 这就是著名的 St. Petersburg paradox（圣彼得堡悖论）：第 $k$ 次投掷才首次出现正面时收益为 $2^k$，其概率为 $2^{-k}$，故每一项 $2^k \cdot 2^{-k} = 1$，级数发散。</span>
>
> 下方几张直方图（histograms）展示了该博弈在不同模拟次数下的支付（payout）结果：
>
> **20 次模拟，观测平均值（observed average）= \$19.20**
>
> <span style="color:#7f8c8d;">【图】原页此处为直方图：20 次模拟的单次支付金额分布（横轴约 \$0–\$300，纵轴为频数）。原图由后处理统一插入。</span>
>
> **200 次模拟，观测平均值（observed average）= \$11.16**
>
> <span style="color:#7f8c8d;">【图】原页此处为直方图：200 次模拟的单次支付金额分布（横轴约 \$0–\$600，纵轴为频数）。原图由后处理统一插入。</span>

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu　6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）。</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
