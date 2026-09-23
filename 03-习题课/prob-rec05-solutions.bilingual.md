<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）</span>

<span style="color:#c0392b;">**Recitation 5 解答（Recitation 5 Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 9 月 23 日）</span>

<span style="color:#7f8c8d;">（本 PDF 为解答版：各题仅含解答文字，未附题面。）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 推导见教材（textbook）第 84–85 页。
>
> **(b)** 推导见教材第 86 页。
>
> **(c)** 推导见教材第 87 页。

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
> <span style="color:#1e8449;">[note] 原文此小问写作 "More hists than misses"，其中 "hists" 应为 "hits"（命中）之笔误。另外，$n = 10$ 时"命中多于未命中"即 $k \ge 6$。</span>
>
> **(d)** 由于 $X$ 是 binomial（二项）随机变量，
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
> **(f)** $Z = X^2$，因此
>
> ```math
> E[Z] = E[X^2] = \left(E[X]\right)^2 + \mathrm{var}(X) = 5.6.
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> <span style="color:#1e8449;">[note] 由 (a)(b) 可反推题意：四辆巴士分别载有 $40$、$33$、$25$、$50$ 名学生；$X$ 为随机抽取的一名学生所乘巴士的载客数，$Y$ 为随机抽取的一辆巴士的载客数。</span>
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
> 显然，$E[X] > E[Y]$。
>
> <span style="color:#1e8449;">[mathtip] $E[X] > E[Y]$ 的原因是尺寸偏置（size-biasing）：按学生抽样时，大小为 $x$ 的车被抽中的可能性与 $x$ 成正比——实际上 $p_X(x) = \dfrac{x}{37}\, p_Y(x)$。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">[solution]</span> 单次博弈（game）的收益（gain）的期望值为无穷大：因为若 $X$ 是你的收益，则
>
> ```math
> E[X] = \sum_{k=1}^{\infty} 2^k \cdot 2^{-k} = \sum_{k=1}^{\infty} 1 = \infty.
> ```
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
