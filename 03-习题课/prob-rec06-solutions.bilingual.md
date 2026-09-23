<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）</span>

<span style="color:#c0392b;">**Recitation 6 解答（Recitation 6 Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 9 月 28 日）</span>

<span style="color:#7f8c8d;">（本 PDF 为解答版：各题仅含解答文字，未附题面。）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> **(a)** 第一小问只需用到掷骰子（die roll）的结果即可完成：
>
> <span style="color:#7f8c8d;">【图】原页此处为 $p_N(n)$ 的 PMF 图：在 $n = 0, 1, 2, 3$ 处各有 $1/4$ 的质量（横轴为 $n$）。原图由后处理统一插入。</span>
>
> **(b)** 当 $N = 0$ 时，硬币一次都不掷，故 $K = 0$；当 $N = n$（$n \in \{1, 2, 3\}$）时，硬币掷 $n$ 次，所得 $K$ 的分布是 conditionally binomial（条件二项）分布。由于 $p_N(n) = 1/4$（$n \in \{0, 1, 2, 3\}$），这些二项概率都要乘以 $1/4$。于是 joint PMF（联合概率质量函数）$p_{N,K}(n, k)$ 取下表所列数值，在表外取值为零：
>
> |  | $k = 0$ | $k = 1$ | $k = 2$ | $k = 3$ |
> |---|---|---|---|---|
> | $n = 0$ | $1/4$ | $0$ | $0$ | $0$ |
> | $n = 1$ | $1/8$ | $1/8$ | $0$ | $0$ |
> | $n = 2$ | $1/16$ | $1/8$ | $1/16$ | $0$ |
> | $n = 3$ | $1/32$ | $3/32$ | $3/32$ | $1/32$ |
>
> **(c)** 在 $N = 2$ 的条件下，$K$ 是一个 binomial（二项）随机变量。于是立即可得
>
> ```math
> p_{K|N}(k \mid 2) =
> \begin{cases}
> 1/4, & k = 0, \\
> 1/2, & k = 1, \\
> 1/4, & k = 2, \\
> 0, & \text{otherwise}.
> \end{cases}
> ```
>
> 这正是上一小问表格中相应一行的归一化（normalized row）结果。
>
> <span style="color:#7f8c8d;">【图】原页此处为 $p_{K|N}(k \mid 2)$ 的 PMF 图：$k = 0, 1, 2$ 处分别为 $1/4$、$1/2$、$1/4$（横轴为 $k$）。原图由后处理统一插入。</span>
>
> **(d)** 要得到 $K = 2$ 次正面（heads），必须至少掷了 3 次硬币，因此在 $K = 2$ 的条件下只有 $N = 3$ 与 $N = 4$ 具有正的条件概率。
>
> <span style="color:#1e8449;">[note] 原文如此（"at least 3 coin tosses" 与 "N = 3 and N = 4"）。由 (b) 的联合 PMF 表可知 $p_{N,K}(2,2) = 1/16 \ne 0$、$p_{N,K}(3,2) = 3/32 \ne 0$，且 $N$ 只取 $\{0,1,2,3\}$；得到 2 次正面只需至少掷 2 次硬币。下式的分母与结果（$2/5$、$3/5$）也正对应 $N = 2, 3$，故原文这两处数字系笔误，应为"至少掷 2 次硬币"与"$N = 2$ 和 $N = 3$"。</span>
>
> ```math
> p_{N|K}(2 \mid 2) = \frac{P(\{N = 2\} \cap \{K = 2\})}{P(\{K = 2\})} = \frac{1/16}{1/16 + 1/32 + 1/32 + 1/32} = \frac{2}{5}.
> ```
>
> 类似地，$p_{N|K}(3 \mid 2) = 3/5$。
>
> <span style="color:#1e8449;">[mathtip] 分母中 $1/16 = p_{N,K}(2,2)$；三个 $1/32$ 对应 $N = 3$ 时恰含两次正面的三种投掷序列（HHT、HTH、THH），每种概率为 $(1/4) \cdot (1/2)^3 = 1/32$，合计 $3/32 = p_{N,K}(3,2)$。</span>

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> <span style="color:#7f8c8d;">【图】原页此处为 $p_{N|K}(n \mid 2)$ 的 PMF 图：$n = 2$ 处为 $2/5$、$n = 3$ 处为 $3/5$（横轴为 $n$）。原图由后处理统一插入。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> <span style="color:#1e8449;">[note] 由 (d) 的计算式可反推本题的联合分布：joint PMF（联合 PMF）集中在 8 个各具概率 $1/8$ 的点质量上，位于 $(0,3)$、$(4,3)$、$(2,2)$、$(4,2)$、$(0,1)$、$(2,1)$、$(4,1)$、$(4,0)$。</span>
>
> **(a)** $x = 0$ 使 $E[Y \mid X = x]$ 达到最大，因为
>
> ```math
> E[Y \mid X = x] =
> \begin{cases}
> 2, & x = 0, \\
> 3/2, & x = 2, \\
> 3/2, & x = 4, \\
> \text{undefined}, & \text{otherwise}.
> \end{cases}
> ```
>
> **(b)** $y = 3$ 使 $\mathrm{var}(X \mid Y = y)$ 达到最大，因为
>
> ```math
> \mathrm{var}(X \mid Y = y) =
> \begin{cases}
> 0, & y = 0, \\
> 8/3, & y = 1, \\
> 1, & y = 2, \\
> 4, & y = 3, \\
> \text{undefined}, & \text{otherwise}.
> \end{cases}
> ```
>
> **(c)**
>
> <span style="color:#7f8c8d;">【图】原页此处为 $p_R(r)$ 的 PMF 图（横轴为 $r$，图中标注的值包括 $3/8$、$1/4$、$1/8$）。原图由后处理统一插入。</span>
>
> <span style="color:#1e8449;">[note] 原解答此小问只给出 PMF 图，未在文字中给出 $R$ 的定义（应在配套习题单中）。按上面的联合分布反推：当 $R = |X - Y|$ 时，$p_R(0) = 1/8$、$p_R(1) = 3/8$、$p_R(2) = 1/8$、$p_R(3) = 1/4$、$p_R(4) = 1/8$，与图中标注值（$3/8$、$1/4$、$1/8$）完全吻合。</span>
>
> **(d)** 自上而下、自左向右地遍历图中各点（traversing the points top to bottom and left to right），得
>
> ```math
> E[XY] = \frac{1}{8}\left(0 \cdot 3 + 4 \cdot 3 + 2 \cdot 2 + 4 \cdot 2 + 0 \cdot 1 + 2 \cdot 1 + 4 \cdot 1 + 4 \cdot 0\right) = \frac{15}{4}.
> ```
>
> 在事件 $A$ 上取条件会去掉 $(0, 1)$ 与 $(0, 3)$ 处的点质量，于是其余每个点质量的条件概率为 $1/6$，且
>
> ```math
> E[XY \mid A] = \frac{1}{6}\left(4 \cdot 3 + 2 \cdot 2 + 4 \cdot 2 + 2 \cdot 1 + 4 \cdot 1 + 4 \cdot 0\right) = 5.
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">[solution]</span> 见教材（textbook）例 2.17（Example 2.17），第 105–106 页。

<span style="color:#7f8c8d;">（原 PDF 此题仅给出教材出处。）</span>

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu　6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）。</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
