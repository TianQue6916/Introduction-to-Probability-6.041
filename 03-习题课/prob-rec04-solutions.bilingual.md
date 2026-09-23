<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）</span>

<span style="color:#c0392b;">**Recitation 4 解答（Recitation 4 Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 9 月 21 日）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span> 该 sample space（样本空间）由每个人的生日的全部可能选择组成。由于共有 $n$ 个人，而每人的生日有 $365$ 种选择，故样本空间共有 $365^n$ 个元素。
>
> 现在考虑"没有任意两人生日相同"的那些生日选择。设 $n \le 365$，则第一个人有 $365$ 种选择，第二个人有 $364$ 种，依此类推，总数为 $365 \cdot 364 \cdots (365 - n + 1)$。于是，"没有两人生日相同"（no two birthdays coincide）的概率为
>
> ```math
> P(\text{no two birthdays coincide}) = \frac{365 \cdot 364 \cdots (365 - n + 1)}{365^n}.
> ```
>
> 有趣的是，当 $n$ 小至 $23$ 时，"存在两人生日相同"的概率就已经大于 $1/2$。
>
> <span style="color:#1e8449;">[mathtip] 可验证：$n = 23$ 时，至少两人生日相同的概率为 $1 - \dfrac{365 \cdot 364 \cdots 343}{365^{23}} \approx 0.507 > 1/2$，这就是著名的 birthday problem（生日问题）。</span>

<span style="color:#7f8c8d;">【图】原页此处为图：不同人数之下"生日互不相同"的概率随人数变化的曲线（原页图注：Graphs of the probability of having a distinct birthday vs. number of people present，图由 MIT OpenCourseWare 提供）。原图由后处理统一插入。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">[solution]</span> 与之前的做法一样：先数出能够安全放置 $8$ 只车（rooks，即任意两只车互不攻击）的有利位置（favorable positions）数，再把它除以 $8 \times 8$ 棋盘上放置 $8$ 只车的位置总数。先数车的有利位置数：我们将把这些车一只一只地放置。第一只车没有任何约束，故有 $64$ 种选择；然而放好这只车后，它所在的一行与一列便不能再用了。于是放置第二只车时，可以想象把这一行一列从棋盘中移除，剩下一张 $7 \times 7$ 的棋盘，因而有 $49$ 种选择；类似地，第三只车有 $36$ 种选择，第四只 $25$ 种，依此类推……

<!-- ===== PDF p2 ===== -->

> **（续）** 若不加任何限制，放置 $8$ 只车共有 $64 \cdot 63 \cdots 57$ 种方式，因此所求概率为：
>
> ```math
> \frac{64 \cdot 49 \cdot 36 \cdot 25 \cdot 16 \cdot 9 \cdot 4}{\dfrac{64!}{56!}}
> ```
>
> <span style="color:#1e8449;">[mathtip] 第 $k$ 只车有 $(9-k)^2$ 种放法：$64 = 8^2$、$49 = 7^2$、$\ldots$、$4 = 2^2$（第 $8$ 只车只剩 $1$ 格，乘 $1$ 不改变乘积），故分子等于 $(8!)^2$；而分母 $\frac{64!}{56!} = 64 \cdot 63 \cdots 57$ 是 $8$ 只可区分的车占据 $64$ 格中互不相同格子的方式数。</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">[solution]</span> 见教材（textbook）习题 1.61（Problem 1.61），第 69 页。

<span style="color:#7f8c8d;">（原 PDF 此题仅给出教材出处。）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">[solution]</span> 把由 $n$ 个槽位（slots）构成的组划分为长度分别为 $n_1, \ldots, n_r$ 的若干段（segments）。这 $n$ 个物品共有 $n!$ 种排法，其中每一种排列都对应一个把这 $r$ 个段划分出来的方式。但同一段之内物品的各种排列给出的都是同一个划分，而第 $i$ 段内物品的排法有 $n_i!$ 种。因此，对每一段都必须除以该段内物品的排列方式数。解答即为：
>
> ```math
> \frac{\text{Ways to arrange } n \text{ items}}{(\text{Ways to arrange items in segment 1}) \cdots (\text{Ways to arrange items in segment } r)} = \frac{n!}{n_1! \cdots n_r!}
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5**</span>

> <span style="color:#2471a3;">[solution]</span> 抽到"恰好含 $n_i$ 个颜色 $i$ 的球"的某一条特定抽球序列，其概率为 $p_1^{n_1} \cdots p_r^{n_r}$。而含 $n_i$ 个颜色 $i$ 的球的序列条数，等于把 $n$ 个不同槽位划分成基数（cardinality）分别为 $n_1, \ldots, n_r$ 的子集的方式数，即
>
> ```math
> \binom{n}{n_1, \ldots, n_r}.
> ```
>
> 因此，"颜色 $i$ 恰好抽到 $n_i$ 个"（对各颜色同时成立）的概率为：
>
> ```math
> \binom{n}{n_1, \ldots, n_r}\, p_1^{n_1} \cdots p_r^{n_r}.
> ```
>
> <span style="color:#1e8449;">[mathtip] 这正是 multinomial（多项）分布的 PMF；其中 $\binom{n}{n_1, \ldots, n_r} = \frac{n!}{n_1! \cdots n_r!}$ 为多项式系数（multinomial coefficient），与上面第 4 题按段划分槽位的计数一致。</span>

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu　6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）。</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
