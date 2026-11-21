<!-- ===== PDF p401 ===== -->

<span style="color:#7f8c8d;">书页 p392 · 第 7 章（Chap. 7）习题区。本页页首承接单元 8 遗留的一张 Problem 解答的收尾（稳态归一化与平衡方程部分），其后才另起 **Problem 23**。</span>

<span style="color:#7f8c8d;">**[problem]**（续，解答收尾）</span>

<span style="color:#1e8449;">[note] 本页页首为上一 Problem（单元 8 遗留，§7.3 稳态求解题）解答的结尾，主题为「各 $\pi_i$ 之和为 $1$ 由此解得 $\pi_i=1/m$，并据此验证平衡方程与归一化方程」。编号与题面在前一页，此处以「（续）」续接，不另起新题。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页首对上一 Problem 解答的收尾在 OCR 中被打成碎片（如 "…an d…i s t he s ame for all i ."、"S i n c e the 1Ti add to L we obtai n 1Tl = 1 1m"、"…shows the b al ance and normalizat ion eq uation s ." 等仅余零散字样）。此解答给出的稳态分布为各项均匀的 $\pi_i = 1/m$，可按原书语义连同上下文忠实转写，下文未补充任何原文未有的具体数值。</span>

…对所有的状态 $i$ 而言都相同（the same for all i）。由于各 $\pi_i$ 之和为 $1$，我们便得到 $\pi_i = 1/m$（对所有 $i$）。据此可直接验证平衡方程（balance equations）与归一化方程（normalization equations）均得到满足。

---

<br>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 23\***</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 23 题面在 OCR 中严重碎裂（如 "Consider the q ueueing Exam ple…"、"p robabi l i ties of a packet arr ival and a packet transm ission depend on the state of the node…"、"h, > 0 for i < m . and bm = O."、"d i > 0 if i  1" 等，仅余零散短语与符号），并缺失「某一新分组到达（(i)/one new packet arrives）」「某一分组完成传输（(ii)/one packet is transmitted）」等事件的完整措辞。下文按原书 §7.3 关于有限容量分组传输结点的生灭链（birth–death chain）语义做忠实重建，所涉参数均为符号（$b_i,d_i,m$），未臆造任何原文未给出的具体数字。</span>

<span style="color:#7f8c8d;">**Problem 23（英文原题）**  Consider the queueing Example, but assume that the following occurs: the probabilities of a packet arrival and a packet transmission depend on the state of the node. Specifically, let $b_i > 0$ for $i < m$ and $b_m = 0$, and let $d_i > 0$ for $i \ge 1$. Then:
(i) one new packet arrives and no packet is transmitted with probability $b_i$, for $i < m$;
(ii) one packet is transmitted and no new packet arrives with probability $d_i$, for $i \ge 1$;
(iii) no new packet arrives and no packet is transmitted with probability $1 - b_i - d_i$ if $i \ge 1$, and with probability $1 - b_i$ if $i = 0$.
Calculate the steady-state probabilities of the chain.</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（解答）**</span>

<span style="color:#7f8c8d;">**Solution（英文保留，因本题带 \*）**  The states of the chain are $0, 1, \ldots, m$, corresponding to the number of packets currently stored at the node. The transition probability graph is given in Figure 7.23.

Thus we may write the balance equations in the form

```math
\pi_{j+1} = \rho_j \pi_j, \qquad \rho_j = \frac{b_j}{d_{j+1}}, \quad j = 0, 1, \ldots, m-1,
```

and by iteration,

```math
\pi_j = \rho_{j-1} \cdots \rho_0 \, \pi_0, \qquad j = 1, \ldots, m.
```

By $1 = \pi_0 + \pi_1 + \cdots + \pi_m$, we obtain

```math
1 = \pi_0 \Bigl( 1 + \rho_0 + \rho_0 \rho_1 + \cdots + \rho_0 \rho_1 \cdots \rho_{m-1} \Bigr),
```

so that

```math
\pi_0 = \frac{1}{1 + \rho_0 + \rho_0 \rho_1 + \cdots + \rho_0 \rho_1 \cdots \rho_{m-1}}.
```</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题是 §7.3 的 queuing example（排队例）的状态相关版本：缓冲节点容量为 $m$，状态取当前存包数 $0,1,\ldots,m$，每个时隙只可能发生三件事之一——来一个包而不发（概率 $b_i$）、发一个包而不来（概率 $d_i$）、两者都不发生（概率 $1-b_i-d_i$）。把常数到达率与服务率换成随状态变化的 $b_i$、$d_i$，表面只是参数变复杂，实际上是 birth–death chain（生灭链）求解模板的一次完整演示：三条对角线的结构不变，变的只是每条斜线上的系数。
>
> 第一性原理：为什么不直接解 $m$ 元全局平衡方程组？因为 transition matrix（转移矩阵）是三对角的，非零元素只落在主对角线与两条次对角线上。取「前 $j$ 个状态」组成的截断集合 $A_j=\{0,\ldots,j\}$，稳态下这个集合的概率质量恒定，于是跨过截面的净流量必然为零；而进出 $A_j$ 的通道各只有一条——从 $j$ 涨到 $j+1$ 的 $b_j$，和从 $j+1$ 跌回 $j$ 的 $d_{j+1}$。所以 $\pi_jb_j=\pi_{j+1}d_{j+1}$。这条式子常被误当作额外假设，其实它是一维结构下从全局平衡方程推出来的结论：把 $j$ 与 $j+1$ 两处的平衡方程相减，所有中间项成对抵消，剩下的正是这一条。全局平衡只要求每个状态进出总量相等，而「相邻两态之间的双向流量相等」在一维链上比它更强、也更容易用。
>
> 这条式子就是 local balance（局部平衡）在一维链上的特例。它的价值在于把「解线性方程组」换成「一次除法加一次连乘」：记 $\rho_j=b_j/d_{j+1}$，则 $\pi_{j+1}=\rho_j\pi_j$，于是 $\pi_j=\pi_0\prod_{k=0}^{j-1}\rho_k$。剩下的唯一自由度由归一化钉死，$\pi_0$ 就是那个连乘分母的倒数。换一种写法：稳态概率正比于沿链累乘的权重，取对数后 $\log\rho_j$ 就是相邻两态之间的 potential difference（势差），整套递推与统计力学里的 Boltzmann weight（玻尔兹曼权重）同构——局部分支比决定全局占据比，与配分函数决定各能级占据数完全同一个算理。
>
> 命名与出处要写准。$\rho_j$ 在排队论里叫 utilization（利用因子）或 load factor（负载因子），量的是「单位时间想进来多少、能出去多少」，稳态解按它逐级缩放。Kendall 在 1953 年的论文《Stochastic Processes Occurring in the Theory of Queues and Their Analysis by the Method of the Imbedded Markov Chain》（Annals of Mathematical Statistics 第 24 卷第 3 期，338–354 页）里定下的是 A/B/c 记法：A 指到达间隔的分布、B 指服务时间的分布、c 指服务员台数，后来常见的 A/S/c 写法只是把 B（service 的通用符号）改成 S 的变体，含义不变。本题连续时间、常数参数的版本就是 M/M/1/m，即容量为 $m$ 的有限缓冲队列，其稳态为 $\pi_j=\rho^{j}(1-\rho)/(1-\rho^{m+1})$，其中 $\rho=\lambda/\mu$。排队论的系统分析则始于 Erlang 1909 年对哥本哈根电话交换机的计算。
>
> 一个必须分清的语义差别：这里的 $b_i$、$d_i$ 是「一个时隙内发生某事件」的概率，不是速率，所以不能像连续时间模型那样直接相除得到流量；真正的流量对比只在 $\pi_j b_j=\pi_{j+1}d_{j+1}$ 这一层成立。把概率当速率、再把两者相加，是最常见的量纲错误：离散时隙里 $b_i+d_i<1$ 的部分是空转，而连续时间链里「跳变速率之和」乘上期望逗留时间才等于一，两种语言不能混着写。
>
> 跨课程连接：同一组递推在 18.06 的语言里是「以 $\rho$ 为边权的路径连乘」，稳态解可写成对所有生成树求和后的比值，即 matrix–tree theorem（矩阵树定理），这是 Markov chain（马尔可夫链）稳态的树形公式；在 MCMC 里，birth–death 型 proposal 的接受率正是按 $\pi_{j+1}/\pi_j$ 的比例设计的。物理侧的 Ehrenfest urn model（埃伦费斯特瓮模型）也属同一族，只不过它的 $b_i$、$d_i$ 由抽球规则决定。
>
> 反例与边界：题目专门要求 $b_m=0$，这不是装饰——若满缓冲仍能以正概率到达，状态 $m$ 就会「溢出」，截断集合的净流量论证不再闭合，链也不再封闭在这 $m+1$ 个状态里。若某个 $d_{j+1}=0$，则从 $j+1$ 往上全部不可达，链退化成分段结构、稳态不唯一。若所有 $b_i=d_i=0$，链原地不动，稳态就是出发状态。非周期性靠自环 $1-b_i-d_i$ 保证：只要有一个状态满足 $b_i+d_i<1$，链就非周期；反之若对所有 $i$ 都有 $b_i+d_i=1$，链周期为 $2$，$\pi$ 存在但 $n$ 步转移概率不收敛于它。

> <span style="color:#7f8c8d;">本页止于此，Problem 23 的 Solution 继续到下一页（PDF p402）。</span>
<!-- ===== PDF p402 ===== -->

> <span style="color:#7f8c8d;">§7.3 并行发射的排队例（queuing example）习题区，书页 393。本页承接上一页 Problem 23\*（缓冲节点排队例）英文 Solution 的收尾段（稳态概率公式），随后进入 Problem 24\* 与 Problem 25\*。三题皆带 `*`，其英文 Solution 按规范原样保留（仅标签注中文）。本页 Problem 编号沿用第 7 章习题区连续编号（承接单元 8，从 23 起）。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页首 Problem 23 Solution 收尾段及两题题干的数学符号在 OCR 中严重碎裂（如 `7T"i` 代表 $\pi_i$、`Po` 代表 $p_0$、`Pkj` 代表 $P_{kj}$、连加分段错行等）。现按原书页 393 权威文本还原下列各公式，数值与结构均依据上一页（书页 392）推出的 $\pi_0 = \frac{1}{1+p_0+p_0p_1+\cdots+p_0\cdots p_{m-1}}$ 与递推 $\pi_{i+1}=p_i\pi_i$ 反推核验，非臆造。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 23\*（续）（排队例 Solution 收尾）**</span>

The remaining steady-state probabilities are

```math
\pi_i = \frac{p_0\, p_1 \cdots p_{i-1}}
{1 + p_0 + p_0 p_1 + \cdots + p_0 \cdots p_{m-1}},
\qquad i = 1, \ldots, m.
```

> <span style="color:#7f8c8d;">衔接上一面（PDF p401）：这是 Problem 23 英文 Solution（其开头在书页 392）推导 $\pi_0$ 之后给出的其余稳态概率公式的收尾。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 24\*．平衡方程的相关性（Dependence of the balance equations）**</span>

Show that if we add the first $m-1$ balance equations

```math
\pi_j = \sum_{k=1}^{m} \pi_k P_{kj}, \qquad j = 1, \ldots, m-1,
```

we obtain the last equation

```math
\pi_m = \sum_{k=1}^{m} \pi_k P_{km}.
```

<span style="color:#00838f;">**[solution] Solution（解答）**</span>

By adding the first $m-1$ balance equations, we obtain

```math
\sum_{j=1}^{m-1} \pi_j
= \sum_{j=1}^{m-1} \sum_{k=1}^{m} \pi_k P_{kj}
= \sum_{k=1}^{m} \pi_k \sum_{j=1}^{m-1} P_{kj}
= \sum_{k=1}^{m} \pi_k \,(1 - P_{km}),
```

```math
= \pi_m + \sum_{k=1}^{m-1} \pi_k - \sum_{k=1}^{m} \pi_k P_{km}.
```

This equation is equivalent to the last balance equation

```math
\pi_m = \sum_{k=1}^{m} \pi_k P_{km}.
```

---

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 题目要证的是「前 $m-1$ 条 balance equations（平衡方程）相加恰好等于第 $m$ 条」。这不是计算技巧，而是一条关于方程组秩的断言：$m$ 条方程不可能彼此独立，rank（秩）至多 $m-1$。这条冗余性是 transition matrix（转移矩阵）结构的必然结果，不是巧合，所以它在任何有限 Markov chain（马尔可夫链）上都成立，与具体数值无关。
>
> 先把证明走一遍。左端是 $\sum_{j=1}^{m-1}\pi_j$；右端交换求和次序得 $\sum_{k=1}^{m}\pi_k\sum_{j=1}^{m-1}P_{kj}$，再用行和为一把内层求和写成 $1-P_{km}$，于是右端等于 $\sum_k\pi_k-\sum_k\pi_kP_{km}$。移项即得 $\sum_k\pi_kP_{km}=\sum_k\pi_k-\sum_{j=1}^{m-1}\pi_j$，而右边正是 $\pi_m$ 本身——纯记账，一分不多一分不少。关键点值得单独强调：这一步完全不需要归一化。用非归一化的向量 $\pi$ 验证，只要它是任意一个满足前 $m-1$ 条方程的向量，$\sum_k\pi_k-\sum_{j<m}\pi_j=\pi_m$ 就恒成立，因为两边只是同一个和式的两种数法。所以严格的表述是：前 $m-1$ 条方程蕴含第 $m$ 条，与尺度无关；归一化是后来为了把解压成唯一一点才加上的。
>
> 顺便纠正一处极易写反的记号。$\sum_jP_{kj}=1$ 对每个固定的 $k$ 沿列指标 $j$ 求和等于一，这恰恰是行和为一，即 row-stochastic（行随机），也就是 Markov chain（马尔可夫链）的定义本身；列和为一即 column-stochastic（列随机），是另一件事，只有 doubly stochastic（双随机）矩阵才同时具备，本题不保证。这个区分不是抠字眼：行和为一给的是右特征向量——常向量 $\mathbf{1}$ 满足 $P\mathbf{1}=\mathbf{1}$；而稳态方程 $\pi P=\pi$ 说的是 $\pi$ 是 $P$ 的 left eigenvector（左特征向量）。一句话里把行列搞反，后面所有「为什么 $1$ 是特征值」的论证都会跟着漂。
>
> 代数视角更干净。稳态方程就是 $\pi(P-I)=0$，即 $\pi$ 落在 $P-I$ 的左零空间里。转置之后变成 $(P^T-I)\pi^T=0$：$\pi^T$ 是 $P^T$ 的特征向量、特征值 $1$。$P$ 的行和为一保证 $P$ 有特征值 $1$，又因 $P$ 与 $P^T$ 有相同的特征多项式，$1$ 必也是 $P^T$ 的特征值，故 $P^T-I$ 奇异、秩至多 $m-1$。更直接的看法是：把 $P^T-I$ 的每一列加起来，得到的是「该列的列和减一」，而 $P^T$ 的列和就是 $P$ 的行和，于是每列之和为零，行向量 $\mathbf{1}^T$ 从这个矩阵左边把它零化掉，它必然奇异。整条论证只用了「行和为一」这一条结构信息。
>
> 唯一性从哪里来？这里有个必须纠正的等价关系：秩亏一（零空间维数为一）等价于「常返类只有一个」，**不等价于** irreducible（不可约）。反例：$P=\begin{pmatrix}1&0\\1&0\end{pmatrix}$，状态 $2$ 是 transient（暂态）、常返类只有 $\{1\}$，$\dim\ker(I-P)=1$，但链显然不是不可约的——$2$ 能到 $1$，$1$ 回不到 $2$，可达矩阵不连通。秩亏数的其实是「一旦进入就不再离开的封闭类」的个数。Perron–Frobenius theorem（佩龙–弗罗贝尼乌斯定理）的准确形式也与此对齐：非负矩阵的谱半径是特征值，其重数由 final class（终类，即常返类）的个数决定；只有当矩阵 irreducible（不可约）时这个重数才是 $1$，并且对应的特征向量可以取成全正。原注把「秩 $=m-1$」直接说成「等价于不可约」，漏掉了暂态状态不影响零空间维数这一层。
>
> 归一化条件 $\sum_i\pi_i=1$ 的作用是把这条一维解空间与超平面相交，得到唯一一点。所以「稳态概率必须和为 1」不是附赠的美化条件，而是把一个一维解空间压成零维的必需方程；同时也要注意，题面（Problem 24）本身并没有「单一常返类」这一假设，冗余性在任何行随机矩阵上都成立，只有唯一性需要单类。
>
> 数值上的直接后果：拿 $P^T-I$ 去求逆一定奇异。标准做法是把其中一行替换成全一（等价于把归一化方程换进来），或追加归一化方程后解最小二乘；也可以完全不解方程，直接做 power iteration（幂迭代）$\pi_{n+1}=\pi_nP$，非周期时它收敛到 $\pi$，每步只需一次稀疏矩阵向量乘，代价与边数同阶。PageRank 用的就是这条路，只不过额外加了 damping（阻尼）来强制非周期、并避免悬挂节点破坏行和。
>
> 反例与边界：若链可约、含 $k$ 个常返类，零空间维数为 $k$，这时即使补上归一化也不唯一——每个类内各自归一化的任意凸组合都是解，稳态依赖于初始分布落在哪个类。另一个常见误解是：只写平衡方程而漏掉归一化，解集会是一整条过原点的射线，任意正倍数都满足方程；这说明那条冗余方程确实少了、而且少的正好是「尺度」这一维，补上尺度信息之后解才落定。

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 25\*．局部平衡方程（Local balance equations）**</span>

We are given a Markov chain that has a single recurrent class which is aperiodic. Suppose that we have found a solution $\pi_1, \ldots, \pi_m$ to the following system of local balance and normalization equations:

```math
\pi_i P_{ij} = \pi_j P_{ji}, \qquad i, j = 1, \ldots, m,
```

```math
\sum_{i=1}^{m} \pi_i = 1, \qquad i = 1, \ldots, m.
```

(a) Show that the $\pi_j$ are the steady-state probabilities.

(b) What is the interpretation of the equations $\pi_i P_{ij} = \pi_j P_{ji}$ in terms of expected long-term frequencies of transitions between $i$ and $j$?

(c) Construct an example where the local balance equations are not satisfied by the steady-state probabilities.

<span style="color:#00838f;">**[solution] Solution（解答）**</span>

(a) By adding the local balance equations $\pi_i P_{ij} = \pi_j P_{ji}$ over $i$, we obtain

```math
\sum_{i=1}^{m} \pi_i P_{ij} = \sum_{i=1}^{m} \pi_j P_{ji} = \pi_j,
```

so the $\pi_j$ also satisfy the balance equations. Therefore, they are equal to the steady-state probabilities.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 25 的 (a) 问只有一行代数：把 $\pi_iP_{ij}=\pi_jP_{ji}$ 对 $i$ 求和，右端 $\sum_iP_{ji}$ 是第 $j$ 行之和，等于一，于是得到 $\sum_i\pi_iP_{ij}=\pi_j$，正是 balance equations（平衡方程）。真正要读的是这一行背后关于「流」的两种条件，以及它们之间的强弱关系。
>
> 先把流的图像建立起来。稳态链在每条有向边 $i\to j$ 上有一个长期流量 $\pi_iP_{ij}$，单位是「每步的期望转移次数」。全局平衡说的是：每个顶点进出的总量相等，即每个顶点的 net flux（净流量）为零。这允许一种情况——流在图上绕圈：$1\to2\to1$ 与 $1\to3\to2\to1$ 这样的 circulation（环流）可以在每个顶点都收支平衡，却让某些边单向有流。local balance（局部平衡）要求更强的东西：每一条边自身两个方向的流量相等，于是环流被逐条掐死。
>
> 借向量场的语言说一句（这只是比喻，不是要引入外微分）：全局平衡像 divergence（散度）为零，局部平衡像旋度也为零。散度为零不蕴含旋度为零，这正是「局部平衡比全局平衡强」的确切含义，也是 (c) 问能构造出反例的根本原因：反例里的链处处收支平衡，却存在净环流。
>
> (b) 问的解释就落在这个流量上：$\pi_iP_{ij}$ 是 $i\to j$ 这条转移的长程期望频率，所以局部平衡读作「任意一对状态之间，两个方向的长期转移次数相等」。这个「一对状态一对状态地相等」是比「每个状态总量平衡」细得多的信息：前者是 $O(m^2)$ 条约束，后者只有 $m$ 条。
>
> 命名：这套性质叫 time reversibility（时间可逆性）。名字的来源可以精确化——把稳态链倒着看，得到的反向链转移概率为 $\hat P_{ij}=\pi_jP_{ji}/\pi_i$，即「原链里从 $j$ 到 $i$ 的流量，除以 $i$ 的稳态质量」，它自动满足行和为一。若 $\hat P=P$，正放与倒放的单步统计完全一样，任何有限长轨道的概率都等于它反向写出的概率，于是没有「时间箭头」。这就是 reversible（可逆）一词的意思：不是「能倒回去」，而是「倒过来的过程与原过程同分布」。
>
> (c) 的反例值得逐边检查，配一组具体数最清楚。状态 $1,2,3$，取 $P_{12}=P_{13}=1/2$、$P_{21}=1$、$P_{32}=1$，其余为零（第 $3$ 行只有 $3\to2$）。稳态解出来是 $\pi=(0.4,\,0.4,\,0.2)$：验算 $1$ 号点流入 $0.4\times1+0=0.4$、流出 $0.4\times1=0.4$；$2$ 号点流入 $0.4\times0.5+0.2\times1=0.4$、流出 $0.4\times1=0.4$；$3$ 号点流入 $0.4\times0.5=0.2$、流出 $0.2\times1=0.2$。全局平衡处处成立，而局部平衡处处不成立：边 $1\to3$ 的单向流量 $0.2$ 在反方向恒为零，边 $1\to2$ 的两向流量是 $0.2$ 对 $0.4$。这个例子也顺带说明它为何仍满足 (a) 的前提（单一常返类且非周期）：从 $1$ 出发存在长度 $2$ 的回路 $1\to2\to1$ 与长度 $3$ 的回路 $1\to3\to2\to1$，两者最大公约数为一。
>
> 周期这一句要说准确，因为「删掉一条边就变成 $2$ 周期」是错的。若把 $1\to3$ 这条边删掉，状态 $3$ 就再没有入边，它立刻变成 transient（暂态）——从 $1$ 出发的轨道会走到 $3$、停在 $2$，链整体变可约，剩下的常返类 $\{1,2\}$ 才是 $2$ 周期的。也就是说，删边同时改变了可达性与周期性，而不可约性的损失比周期更要紧：可控的只是「常返类内部周期为 $2$」这一句话，全局的极限分布已经不存在了。
>
> 跨课程连接（统计物理与 MCMC）：detailed balance（细致平衡）就是统计力学里的微观可逆性，是平衡态的标志。Metropolis、Rosenbluth 夫妇与 Teller 夫妇在 1953 年给出的算法，以及 Hastings 在 1970 年推广到非对称 proposal 的版本，其全部设计要点就是「构造一条对目标分布满足细致平衡的链」，接受率取 $\min\!\left(1,\pi_jq_{ji}/(\pi_iq_{ij})\right)$ 正是为了让 $\pi_iP_{ij}=\pi_jP_{ji}$ 精确成立；Gibbs sampling（吉布斯采样）是它的一个特例。这条思路之所以有效，是因为一旦 detailed balance（细致平衡）加上不可约，稳态分布就被唯一钉住，不必再验证收敛。
>
> 跨课程连接（线性代数）：细致平衡可以写成矩阵等式 $DP=(DP)^T$，其中 $D$ 是以 $\pi_i$ 为对角的矩阵。也就是说，把 $P$ 用 $D$ 加权之后变成 symmetric（对称）矩阵，于是它可正交对角化、特征值全为实。这一步把非对称的 Markov 算子变成自伴算子，18.06 里的谱定理与实分析里自伴算子的理论就此接上；而「特征值实、可按特征向量展开」正是 $n$ 步转移概率能写成指数衰减和的技术前提。
>
> 边界与反例：局部平衡是充分条件，不是必要条件。任何 birth–death chain（生灭链）自动可逆，因为一维链上没有环可绕，任何稳态流场都只能是相邻两态之间的往返；任何树形图上的链也自动可逆。但一般图上的链不必可逆，(c) 的三状态链就是最小反例——三个状态是能构造出环流的最小规模，两个状态做不到：两状态链的局部平衡条件 $\pi_1P_{12}=\pi_2P_{21}$ 恰好就是它唯一的平衡方程，两件事在这里重合。所以「可逆」不是 Markov chain（马尔可夫链）的普遍性质，而是需要逐边验证的结构性质；反过来说，凡是能证明可逆的地方，求解就从解方程组退化成解一维递推，这正是相邻那道 birth–death 题的比值公式的来源。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页止于 Problem 25 英文 Solution 的第 (a) 问作答（$\sum_i \pi_i P_{ij} = \sum_i \pi_j P_{ji} = \pi_j$，故 $\pi_j$ 亦满足平衡方程，因而等于稳态概率）。第 (b)、(c) 两问解答位于后续页。</span>
<!-- ===== PDF p403 ===== -->

<span style="color:#7f8c8d;">本书页 p394（Chap. 7）。本页为第 7 章习题区（Problems 23–39）中部续页，承接上一页：页首为该带 `*` 题英文 Solution 的收尾部分（(b)、(c) 两小问，与时间可逆性（time reversibility）及局部平衡方程相关），紧随其后的 **Problem 26**（带 `*`）题干与其英文 Solution 均在下一页页界之内完整呈现。</span>

> <span style="color:#7f8c8d;">页首这段 (b)(c) 承接上一页的英文 Solution 尾部（上页未走完的同题解答如局部平衡方程的频率解释、最小三状态反例等），因该题带 `*` 且按规范习题区英文 Solution 保留、仅标签可标注中文，此处不加打断地续接上页英文解答。</span>

<span style="color:#00838f;">**Solution. (continuation of a starred problem)**</span> 

(b) We know that $\sum_i \pi_i P_{ij}$ can be interpreted as the expected long-term frequency of transitions from $i$ to $j$, so the local balance equations imply that the expected long-term frequency of any transition is equal to the expected long-term frequency of the reverse transition. (This property is also known as time reversibility of the chain.)

(c) We need a minimum of three states for such an example. Let the states be $1$, $2$, $3$, and let $P_{12} > 0$, $P_{13} > 0$, $P_{21} > 0$, $P_{32} > 0$, with all other transition probabilities being $0$. The chain has a single recurrent aperiodic class. The local balance equations do not hold because the expected frequency of transitions from $1$ to $3$ is positive, but the expected frequency of reverse transitions is $0$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 26.（\*）抽样的马尔可夫链（Sampled Markov chains）。**</span>

Consider a Markov chain $X_n$ with transition probabilities $P_{ij}$, and let $r_{ij}(n)$ be the $n$-step transition probabilities.

(a) Show that for all $n \ge 1$ and $l \ge 1$, we have

```math
r_{ij}(n + l) = \sum_{k=1}^m r_{ik}(n)\, r_{kj}(l).
```

(b) Suppose that there is a single recurrent class, which is aperiodic. We sample the Markov chain every $l$ transitions, thus generating a process $Y_n$, where $Y_n = X_{nl}$. Show that the sampled process can be modeled by a Markov chain with a single aperiodic recurrent class and transition probabilities $r_{ij}(l)$.

(c) Show that the Markov chain of part (b) has the same steady-state probabilities as the original process.

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution.**</span>

(a) We condition on $X_n$ and use the total probability theorem. We have

```math
\begin{aligned}
r_{ij}(n + l)
&= P(X_{n+l} = j \mid X_0 = i)\\
&= \sum_{k=1}^m P(X_n = k \mid X_0 = i)\, P(X_{n+l} = j \mid X_n = k,\, X_0 = i)\\
&= \sum_{k=1}^m P(X_n = k \mid X_0 = i)\, P(X_{n+l} = j \mid X_n = k)\\
&= \sum_{k=1}^m r_{ik}(n)\, r_{kj}(l),
\end{aligned}
```

where in the third equality we used the Markov property.

(b) Since $X_n$ is Markov, once we condition on $X_{nl}$, the past of the process (the states $X_k$ for $k < nl$) becomes independent of the future (the states $X_k$ for $k > nl$). This implies that given $Y_n$, the past (the states $Y_k$ for $k < n$) is independent of the future (the states $Y_k$ for $k > n$). Thus, $Y_n$ has the Markov property. Because of our assumptions on $X_n$, there is a time $\bar{n}$ such that

```math
P(X_n = j \mid X_0 = i) > 0,
```

for every $n \ge \bar{n}$, every state $i$, and every state $j$ in the single recurrent class $R$ of the process $X_n$. This implies that

```math
P(Y_n = j \mid Y_0 = i) > 0,
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 26 的三小问连起来是一条完整的工具链：(a) 证明转移矩阵的半群性质，(b) 证明等间隔抽样之后 Markov property（马尔可夫性质）仍然成立，(c) 证明两条链共享同一个 stationary distribution（平稳分布）。整道题的主题可以压成一句话：Markov 性质对时间轴的等间隔粗粒化是免疫的。
>
> (a) 只是把 Chapman–Kolmogorov equation（查普曼–柯尔莫哥洛夫方程）写一遍：$r_{ij}(n+\ell)=\sum_k r_{ik}(n)r_{kj}(\ell)$。证明的全部内容是「对中间时刻 $X_n$ 条件化」——总概率定理展开，再用 Markov property（马尔可夫性质）把 $P(X_{n+\ell}=j\mid X_n=k,X_0=i)$ 砍成 $P(X_{n+\ell}=j\mid X_n=k)$。矩阵语言里这就是 $P^{n+\ell}=P^nP^{\ell}$：矩阵乘法那层「对所有中间状态 $k$ 求和」的语义，恰好就是「在 $n$ 时刻把轨道一刀切开、对切点求和」。这条等式由 Chapman 在 1928 年前后研究布朗运动位移时给出，Kolmogorov 在 1931 年《概率论中的解析方法》里得到连续时间版本并给出微分方程形式，所以今天通称 Chapman–Kolmogorov。
>
> (b) 是真正有内容的一步。设 $Y_n=X_{n\ell}$，要证 $Y$ 仍是 Markov chain（马尔可夫链）。关键在于 $X_{n\ell}$ 是原链的一个「分割点」：给定它之后，$n\ell$ 之前的轨道与之后的轨道条件独立。而 $Y$ 的过去 $\{Y_0,\ldots,Y_{n-1}\}$ 由 $X_0,\ldots,X_{(n-1)\ell}$ 生成，未来 $\{Y_{n+1},\ldots\}$ 由 $X_{(n+1)\ell},\ldots$ 生成，中间那段 $X_{n\ell+1},\ldots,X_{(n+1)\ell-1}$ 只作为「内部路径」被求和掉 —— 而 $P^\ell$ 的元素正是这条内部路径的概率和。于是「给定 $Y_n$ 时过去与未来条件独立」自动成立，$Y$ 的 transition matrix（转移矩阵）就是 $P^{\ell}$。这里有个容易滑过去的点：不是「丢掉一些状态就自动变 Markov」——在别的结构里丢掉中间变量完全可能制造 collider（对撞点）而破坏条件独立；这里能成立，是因为被丢掉的恰好是两个分割点之间的内部点，而分割点被完整保留。
>
> (b) 里还有一半是验证抽样链仍不可约。标准事实是：有限、irreducible（不可约）且 aperiodic（非周期）的转移矩阵是 primitive（本原）的，即存在整数 $N$，使得 $n\ge N$ 时 $r_{ij}(n)>0$ 对一切 $i,j$ 成立——注意这不是「存在某个 $n$ 使某对状态可达」，而是「从某个时刻起全部为正」，后半句才是抽样论证用得到的。抽样后看到的是 $r_{ij}(\ell n)$，只要 $\ell n\ge N$ 就全正，故 $Y$ 不可约。
>
> (c) 最干净的论证是代数：由 $\pi P=\pi$ 反复右乘 $P$，得 $\pi P^{2}=(\pi P)P=\pi P=\pi$，归纳得 $\pi P^{\ell}=\pi$（左乘会得到 $P\pi P$ 这种既不是矩阵乘法惯例、也不是任何有意义量的东西，方向不能反）。而 $P^{\ell}$ 正是 $Y$ 的转移矩阵，所以 $\pi$ 也是 $Y$ 的平稳分布。若要用分析语言说同一件事，就得加上非周期：$r_{ij}(\ell n)\to\pi_j$，与 $Y$ 的 $n$ 步转移概率取极限所得一致。代数说法不需要非周期，分析说法需要——这个差别以后在连续时间链与数值计算里会反复出现。
>
> 周期的精确结论值得写下来。设原链常返类周期为 $d$，抽样间隔为 $\ell$，则 $Y$ 把该常返类按 $\gcd(d,\ell)$ 切成同样多的子类，每个子类内部的周期是 $d/\gcd(d,\ell)$。两个极端：$d=1$（原链非周期）时 $\gcd(1,\ell)=1$，$Y$ 必非周期，这就是 (b) 的题设为什么要写 aperiodic（非周期），而不必另外去找「第一步就可能有自环」；$d=2$ 且 $\ell$ 为偶数时，$Y$ 被切成两个互不往来的子类，每个子类内部反而变成非周期——看上去「抽样治好了周期性」，代价是不可约性丢了。所以抽样间隔不能乱选：它同时改变周期与可约性，后者比前者更致命。
>
> 随机间隔这一条要按正确的方向写。若抽样间隔 $\tau_1,\tau_2,\ldots$ 是 iid（独立同分布）且与链本身独立，抽样序列照样是齐次 Markov chain（马尔可夫链），转移矩阵是混合 $M=\sum_{k}p_kP^{k}$，其中 $p_k=P(\tau=k)$。举个可算的例子：两状态链 $P=\begin{pmatrix}0.5&0.5\\0.2&0.8\end{pmatrix}$，间隔以 $1/2$ 的概率取 $1$、以 $1/2$ 的概率取 $2$，则 $M=\frac12P+\frac12P^2=\begin{pmatrix}0.425&0.575\\0.23&0.77\end{pmatrix}$，检验三阶条件概率 $P(Y_2\mid Y_1,Y_0)$ 的四组取值，全部等于 $M$ 的对应元素。所以「随机间隔一般破坏 Markov 性」是错的。真正会破坏的只有一种情形：间隔的分布依赖链的路径细节（等价地，偷看了未来），这时抽样时刻不是 stopping time（停时），强 Markov property（强马尔可夫性质）无从下手；若间隔是只依赖已发生历史的停时，抽样链仍是 Markov 的，只是不齐次——$M$ 随所处状态改变，原来的常数矩阵换成逐个状态各一个混合矩阵。
>
> 跨课程连接：信号处理里把「每 $\ell$ 个样本取一个」叫 decimation（抽取），频域上等价于先滤波再降采样，会引入 aliasing（混叠）；Markov chain（马尔可夫链）的 $\ell$ 步抽样是同一动作在概率空间的版本，抽样后的链对应 $P^{\ell}$，而 $P^{\ell}$ 的元素是 $P$ 的 $\ell$ 步路径和——稀疏的 $P$ 可能变得稠密，于是「跳步省时间」在状态数大时会变成「每次转移更贵」。代数上要把「集合」说准：行和为一的非负矩阵集合是 $m$ 个概率单纯形的 Cartesian product（笛卡尔积），对矩阵乘法封闭，它的极点是每行恰有一个 $1$ 的 $0$-$1$ 矩阵；Birkhoff polytope（伯克霍夫多面体）指的是 doubly stochastic（双随机）矩阵那个集合，两者的极点不同（后者的极点是 permutation matrix（置换矩阵）），不要混用。$P^{\ell}$ 不会跑出前者，这就是「抽样链仍是 Markov chain（马尔可夫链）」的代数根据。

<!-- ===== PDF p404 ===== -->

> <span style="color:#7f8c8d;">§7.3 习题区续页（书页 p395）。本页顶端是上一页（PDF p403）某道**带 \*** 题的解题尾部——含 **(b)** 与 **(c)** 两个小问的收尾（题设「构造过程 $Y_n$，其每个时刻都考虑查看过去 $\ell$ 步」当在上一页）；页首无新题目标题，故按「（续）」续接。随后本页另起 **Problem 27\***，并在其后进入 **§7.4** 小节、另起 **Problem 28**。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem（上一带 \* 题解答收尾，续）**</span>

> <span style="color:#7f8c8d;">以下为该 \* 题英文解答的 (b)、(c) 两段收尾。习题区带 \* 题的英文 Solution 照规范保留英文。</span>

(b) For every $n \geq 11$, every $i$, and every $j \in R$. Therefore, the process $Y_n$ has a single recurrent class, which is aperiodic.

(c) The $n$-step transition probabilities $r_{ij}(n)$ of the process $X_n$ converge to the steady-state probabilities $\pi_j$. The $n$-step transition probabilities of the process $Y_n$ are of the form $r_{ij}(\ell n)$, and therefore also converge to the same limits $\pi_j$. This establishes that the $\pi_j$ are the steady-state probabilities of the process $Y_n$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 27.**</span> \* Given a Markov chain $X_n$ with a single recurrent class which is aperiodic, consider the Markov chain whose state at time $n$ is $(X_{n-1}, X_n)$. Thus, the state in the new chain can be associated with the last transition in the original chain.

(a) Show that the steady-state probabilities of the new chain are

```math
\pi_{ij} = \pi_i p_{ij},
```

where the $\pi_i$ are the steady-state probabilities of the original chain.

(b) Generalize part (a) to the case of the Markov chain $(X_{n-k}, X_{n-k+1}, \ldots, X_n)$, whose state can be associated with the last $k$ transitions of the original chain.

<span style="color:#00838f;">**Solution（解答）.**</span>

(a) For every state $(i, j)$ of the new Markov chain, we have

```math
P\big((X_{n-1}, X_n) = (i, j)\big) = P(X_{n-1} = i)\, P(X_n = j \mid X_{n-1} = i) = P(X_{n-1} = i)\, p_{ij}.
```

Since the Markov chain $X_n$ has a single recurrent class which is aperiodic, $P(X_{n-1} = i)$ converges to the steady-state probability $\pi_i$, for every $i$. It follows that $P\big((X_{n-1}, X_n) = (i, j)\big)$ converges to $\pi_i p_{ij}$, which is therefore the steady-state probability of $(i, j)$.

(b) Using the multiplication rule, we have

```math
P\big((X_{n-k}, \ldots, X_n) = (i_0, \ldots, i_k)\big) = P(X_{n-k} = i_0)\, p_{i_0 i_1} \cdots p_{i_{k-1} i_k}.
```

Therefore, by an argument similar to the one in part (a), the steady-state probability of state $(i_0, \ldots, i_k)$ is equal to $\pi_{i_0} p_{i_0 i_1} \cdots p_{i_{k-1} i_k}$.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 27 给的是一条可以反复使用的外科手术：把「模型记不住的那部分历史」直接搬进状态里。新链的状态取 $(X_{n-1},X_n)$，稳态概率是 $\pi_{ij}=\pi_ip_{ij}$；推广到记忆深度 $k$ 的窗口，状态是向量 $(X_{n-k},\ldots,X_n)$，它有 $k+1$ 个分量，稳态概率是 $\pi_{i_0}p_{i_0i_1}\cdots p_{i_{k-1}i_k}$。两问合起来说的是同一件事：稳态落在「转移边」或「路径」上，而不是只落在单个状态上。
>
> 第一性原理：Markov property（马尔可夫性质）失效，从来不是因为「随机性太强」，而是因为「预测未来所需的过去信息没有被当前状态完全承载」。若过程实际依赖最近 $k$ 步，那么把 $k+1$ 个分量的窗口整体当作状态，新链的转移就变成确定性的平移：$(i_0,\ldots,i_k)\mapsto(i_1,\ldots,i_k,j)$，概率 $p_{i_kj}$。于是「未来」只通过这个窗口依赖过去，性质自动恢复。这就是 state augmentation（状态增广）的标准动作——凡是有记忆的项，全部搬进状态，让状态自己承载记忆。
>
> (a) 的证明甚至不需要解平衡方程，只需乘法规则加收敛：$P((X_{n-1},X_n)=(i,j))=P(X_{n-1}=i)P(X_n=j\mid X_{n-1}=i)=P(X_{n-1}=i)p_{ij}$，而原链不可约非周期保证 $P(X_{n-1}=i)\to\pi_i$，所以联合概率收敛到 $\pi_ip_{ij}$。这里没有任何「解方程」的步骤，全部内容就是「联合分布的极限等于边际极限乘条件概率」。把 $\pi_{ij}$ 对 $j$ 求和回到 $\pi_i$，说明它确实是二维状态空间上的概率分布，归一化自动成立。
>
> (b) 把同一句话沿路径重复 $k$ 次：$P((X_{n-k},\ldots,X_n)=(i_0,\ldots,i_k))=P(X_{n-k}=i_0)p_{i_0i_1}\cdots p_{i_{k-1}i_k}$，取极限即得。这个乘积有一个非常有用的读法：它是以 $\pi$ 为初始分布、按 $P$ 走 $k$ 步所得「轨道」的联合分布，即路径空间上的 Markov measure（马尔可夫测度）。换句话说，增广链的平稳分布不是新算出来的东西，而是原链在长度为 $k+1$ 的轨道上的稳态统计。把稳态从点搬到路径，是很多后续构造（隐马尔可夫模型、排队网络、MCMC 的路径空间方法）的通用起点。
>
> 代价必须说准，而且要分清两种增长方向。状态数从 $m$ 涨到 $m^{k+1}$（假定所有转移为正）。方向一：固定状态数 $m$、让记忆深度 $k$ 增大，状态数是 $m^{k+1}$，随 $k$ 每加一步乘 $m$，这就是指数增长，也是「增广不可行」的真正根源；方向二：固定记忆深度 $k$、让原链状态数 $m$ 增大，$m^{k+1}$ 只是关于 $m$ 的 $k+1$ 次多项式。凡是需要长时间记忆的问题，显式枚举必然爆炸，这就是 state explosion（状态爆炸）。
>
> 工程上的修正更重要：状态空间是数学对象，不是存储需求。在线运行时不需要真的 materialize（物化）出 $m^{k+1}$ 个状态，只需一个长度为 $k$ 的 ring buffer（环形缓冲）维护窗口，内存是 $O(k)$，每次更新的代价是 $O(1)$。只有当算法必须「在状态空间上做动态规划」时——例如求吸收概率、做值迭代——指数代价才真实存在，因为那时你确实要遍历每一个窗口。把这两件事分开，是判断「增广能不能用」的唯一标准：作为表示，它几乎总是免费的；作为枚举，它几乎总是付不起的。
>
> 跨课程连接（体系结构与自动机）：识别「最近 $k$ 个符号」的 DFA 在最坏情形下需要 $m^{k+1}$ 个状态，这正是 $k+1$ 阶 $k$-gram 展开。CSAPP 里的分支预测器就是这套结构的硬件版：用 branch history register（分支历史寄存器）把最近若干次分支结果拼成一个索引，去查预测表——索引本身就是「被物化的历史」，表的大小随历史位数指数增长，于是真实处理器只敢用很短的全局历史或做哈希压缩。理论与工程的同一条约束在这里重合：记忆长度每加一位，状态数翻倍。
>
> 另外两个同构：动力系统里的时间延迟嵌入（Takens 定理）用延迟坐标把一条标量观测序列重建成与原系统同构的相空间，靠的正是「窗口里已经含有足够的历史」；强化学习里 Atari 上的 DQN 把连续四帧叠成一个观测，理由完全相同——单帧不含速度信息，四帧窗口才让 MDP 假设成立。
>
> 反例与易错点：其一，增广链的不可约性继承自原链——若原链不可约非周期，则任意窗口都能从任意窗口到达，增广链也不可约；若原链可约，增广链按窗口首分量分块，同样是可约的，不会因为「装进了更多历史」而凭空连通。其二，窗口内元素的顺序不能随意调换：$(X_{n-1},X_n)$ 的稳态是 $\pi_ip_{ij}$，而 $(X_n,X_{n-1})$ 的稳态是 $\pi_jp_{ji}$，两者只有在 detailed balance（细致平衡）成立时才相等；本题不假设可逆，把下标顺序写反是最常见的静默错误。其三，窗口长度与记忆深度差一格：说「记忆 $k$ 步」就必须写下标跨 $k$ 步、共 $k+1$ 个分量，凡是把这两者混用，指数上的 $k$ 就会差一。

---

<span style="color:#c0392b;">**§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 28.**</span> There are $m$ classes offered by a particular department, and each year, the students rank each class from $1$ to $m$, in order of difficulty, with rank $m$ being the highest. Unfortunately, the ranking is completely arbitrary. In fact, any given class is equally likely to receive any given rank on a given year (two classes may not receive the same rank). A certain professor chooses to remember only the highest ranking his class has ever gotten.

(a) Find the transition probabilities of the Markov chain that models the ranking that the professor remembers.

(b) Find the recurrent and the transient states.

(c) Find the expected number of years for the professor to achieve the highest ranking given that in the first year he achieved the $i$th ranking.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题的全部难点不在计算，而在读题时的方向感：题面写的是 rank $m$ 最高（with rank $m$ being the highest），也就是数字越大、名次越好，而教授记住的是 his class has ever gotten 的最高名次。于是状态取历史最大值，最优处在 $m$ 这一端，链从低处往高处单调爬升。先把这一点钉死，后面每一问才有意义。
>
> 这个方向不能反。若误把 $1$ 当成最优，就会写出「一旦触及 $1$ 便永远停在 $1$」这种与题面相反的链，于是吸收态、暂态与常返的结论整体翻转，得到一个自洽但与本题无关的模型。这类「把排名数字的大小当成名次优劣」的符号错误在本章很常见，代价是整道题白做，所以值得在页边记一笔：建模前先问一句「状态变量的哪一端是我想要的」。
>
> (a) 的转移概率。设当前记得的最好名次为 $i$，下一年学生的排名 $R$ 在 $1,\ldots,m$ 上均匀，且与历史独立（题面原文如此：各班级拿到任一排名同分布）。若 $R>i$，状态跳到 $R$，对每个 $j>i$ 的概率都是 $1/m$；若 $R\le i$，什么都不更新，状态保持 $i$，总概率 $i/m$。所以 $P(i\to j)=1/m$ 当 $j>i$，$P(i\to i)=i/m$，其余为零。这个 transition matrix（转移矩阵）是上三角的：所有质量都在对角线及其上方，这就是「单调」在矩阵上的样子。
>
> (b) 由单调性直接读出结构：$m$ 是 absorbing state（吸收态，$P(m\to m)=1$），其余 $m-1$ 个状态全是 transient（暂态）。每个暂态每步都有 $(m-i)/m>0$ 的概率严格上升，而状态数有限，故落到 $m$ 的时间 almost surely（几乎必然）有限，$m$ 是唯一的 recurrent class（常返类）。这一步不需要解方程，只需要「有限个正概率台阶」这个论证。
>
> (c) 的关键洞察是绕开整个链：状态 $m$ 只有在某一年恰好抽到排名 $m$ 时才能到达，而到达之后就永远停住。所以吸收时间就是首次抽到 $m$ 的等待时间，与起始名次 $i$ 无关：只要 $i<m$，$T=\min\{n:R_n=m\}$，而 $R_n$ iid（独立同分布）、每次命中概率 $1/m$，故 $T$ 服从参数 $1/m$ 的 geometric distribution（几何分布，按「首次成功」计数），期望为 $m$。用 first-step analysis（首步分析）验证一遍：$E_m=0$，对 $i<m$ 有 $E_i=1+\frac{i}{m}E_i+\frac{1}{m}\sum_{j=i+1}^{m}E_j$，把 $E_j=m$（$j<m$）与 $E_m=0$ 代入，右端 $=1+i+\frac{(m-1-i)}{m}\cdot m=m$，方程成立，故 $E_i=m$ 是解、且由 $(I-P_T)$ 可逆知是唯一解。两个途径给出同一个数，说明结论不是巧合。
>
> 整条分布也有闭式，但必须分段，这里是最容易写错的地方。因为 $X_n\le i$ 等价于前 $n$ 年的排名全部不超过 $i$，所以对 $i>i_0$ 有 $P(X_n=i)=(i/m)^n-((i-1)/m)^n$——两个「历史最大值不超过 $i$」的事件相减。而起点情形不同：$X_n=i_0$ 只要求前 $n$ 年全部不超过 $i_0$，于是 $P(X_n=i_0)=(i_0/m)^n$，不能套上面的差式（差式会减掉 $((i_0-1)/m)^n$，凭空丢了一块概率）。数值检验：$m=3$、$i_0=2$、$n=2$ 时，$(2/3)^2=4/9\approx0.4444$，与直接枚举 $9$ 条等可能路径中「两年都不超过 $2$」的 $4$ 条一致；若误用差式会得到 $4/9-1/9=1/3$。整条链的分布都有闭式，根本不必迭代。
>
> 命名与出处：这是 record process（记录过程）的一个变体。Rényi 在 1962 年系统研究了 iid 序列的记录值（《Théorie des éléments saillants d'une suite d'observations》，该文有 Clermont-Ferrand 与 Aarhus 两个流传版本、页码各说不一，此处不钉死具体页）：对连续分布，第 $n$ 个观测成为新记录的概率恰好是 $1/n$，而且各记录指示变量 $I_n=\mathbf{1}_{\{X_n>\max(X_1,\ldots,X_{n-1})\}}$ 相互独立（这一条常称 Dwass–Rényi 引理）。本题问的不是记录次数，而是「记录值何时达到上界」，属同一族的极值等待问题；区别在于上界只有一个点，所以等待时间是几何的，而不是记录计数那种调和级数型增长。
>
> 边界与反例：若排名分布不均匀（课程难度彼此相关、某些名次更难拿到），转移概率就不再是各 $1/m$，链仍单调但期望不再是 $m$，闭式也失去。若允许并列（两门课可同名次），结构不变——历史最好名次仍是单个数值、$m$ 仍是唯一的吸收态——改变的是单步抽到每个名次的概率与到达 $m$ 的等待时间分布（最大值不再以 $1/m$ 的概率一举命中），所以「并列会造出一族吸收态」的说法不成立。若教授只记最近一年的排名，链退化成 iid 序列，没有吸收结构，(c) 问的无吸收期望无从谈起。$m=1$ 时是平凡情形：已在最优，期望年数为零。
>
> 跨课程连接：与 CLRS 里「一次线性扫描维护 running maximum（运行最大值）」同构——每次都拿新值与当前最大值比较，只有更大才更新；差别在于这里的「更新」是随机的，而且我们关心的不是最大值本身，而是它追上理论上界要多久。与 coupon collector（优惠券收集）对照更清楚：集齐全部 $m$ 张的期望是 $mH_m$（约 $m\log m$），而本题只要命中特定的一张，期望就是 $m$——目标从「一整个集合」缩小成「一个点」，代价从 $m\log m$ 掉到 $m$，两者相差的正好是那个调和级数。

<!-- ===== PDF p405 ===== -->

<span style="color:#7f8c8d;">§7.4 / §7.5　第 7 章习题区（Problems）续页。本页含两题：顶部一段为 **Problem 29** 的题干（任给一组转移概率确定的马尔可夫链与稳态概率 $\pi_1,\pi_2,\pi_3,\pi_4$，问若干次转移后回到状态 1 的概率、期望与方差、(a)(b)(c) 各问）；随后以「Problem … for Problem 30」交叉引用承接，转入 **Problem 30**（关于暂态（transient）/常返（recurrent）状态、常返类（recurrent classes）与稳态概率、基于图 7.25（Figure 7.25）给出的马尔可夫链，(a)(b)(c) 各问，其 (d)(e) 在下一页）。本页两题的编号标签在源 OCR/合并过程中缺失，现按第 7 章习题区连续编号（28→29→30）复原为 Problem 29 与 Problem 30，题面本身未变。本题区按规范要求，习题题干与带 `*` 题的英文 Solution 一律保留英文原文。</span>

---

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题三小问其实是同一个量的三种时间尺度：$n=6$ 的有限步分布、返回状态的等待时间、$n=1000$ 的极限分布。题目给出的 $\pi_1=1/6$ 在这里起了两次作用——一次作为 $n$ 很大时的目标值，一次作为平均返回时间的倒数。这两个角色重合不是巧合，而是 Kac 等式的内容。
>
> 先说 (a) 与 (c)。(a) 要 $r_{11}(6)$，做法只有两条：把 6 步路径按全概率定理展开（等价于算 $P^6$ 的第 $(1,1)$ 元），或者对 $P$ 做特征分解后取幂。(c) 要 $n=1000$ 的分布，看上去是更重的计算，实际上更轻：只要链 irreducible（不可约）且 aperiodic（非周期），就有 $r_{i1}(n)\to\pi_1$，$1000$ 步早已进入收敛区。这里的「approximately」指的不是含糊其辞，而是收敛速率：误差大致按第二大特征值的模 $|\lambda_2|^n$ 衰减。若 $|\lambda_2|<1$，$|\lambda_2|^{1000}$ 小到可以忽略；但若链是周期的（$|\lambda_2|=1$），它根本不收敛——所以 (c) 的成立完全依赖题设的非周期条件。
>
> (b) 的期望是 Kac's formula（卡茨公式）。Mark Kac 在 1947 年的论文《On the Notion of Recurrence in Discrete Stochastic Processes》（Bulletin of the AMS 第 53 卷，1002–1010 页）里证明：对不可约、正常返的链，从状态 $i$ 出发首次返回 $i$ 的期望恰为 $1/\pi_i$。所以这里 $E_1[T_1]=6$。这个结论有一个不需要公式的读法：长程看，链有 $\pi_1$ 比例的时间待在状态 $1$；把时间轴按「每次回到 $1$」切成长度不等的块，块的出现频率是每 $E[T_1]$ 步一次，而「待在 $1$ 的时间比例」等于「每块贡献一步除以块长」，于是 $\pi_1=1/E[T_1]$，即 $E[T_1]=1/\pi_1$。这就是 renewal reward（更新报酬）论证，它同时解释了为什么答案必须是 $\pi_1$ 的倒数，而不是别的什么周期数。
>
> 测度论形式要写对：对概率测度 $\mu$ 与集合 $A=\{i\}$，Kac 给的是等式 $\int_A\tau\,d\mu=\mu(i)\,E_i[T_i]=1$，不是不等式——「小于等于一」是常见的误记。它的条件版本 $\frac{1}{\mu(A)}\int_A\tau\,d\mu=1/\mu(A)$ 才是「平均返回时间等于 $1/\mu(A)$」这句话。与 Birkhoff 遍历定理的关系也在这里：Birkhoff 说时间平均收敛到空间平均，Kac 是它在「返回时间」这个具体可观测量上的定量版本，两者一个是极限、一个是恒等式。
>
> 方差是另一回事，而且这里藏着一条重要教训：只看 $\pi$ 无法确定方差。方差的背后是返回时间的二阶矩，二阶矩依赖整条链的结构（等价地，依赖 $P$ 的 fundamental matrix（基本矩阵），或 $(I-P)$ 在去掉常向量之后那部分的逆），不是单个稳态概率能编码的。两个反例可以把这一点钉死：链甲是 $1\leftrightarrow2$ 的确定性往返，$\pi_1=1/2$，返回时间恒为 $2$，方差为零；链乙是 $1\to1$ 概率 $1/2$、$1\to2\to3\to1$ 概率 $1/2$，同样 $\pi_1=1/2$，返回时间取 $1$ 或 $3$ 各半，均值仍是 $2$，方差却是 $E[\tau^2]-4=(1+9)/2-4=1$。两条链的稳态分布完全一样，返回时间的波动却从零跳到一。这正是 (b) 问为什么要同时问期望与方差的理由：稳态是一阶信息，风险是二阶信息。
>
> 有一个经常被混淆的量，必须当场分开。由稳态加权平均的首次到达时间 $\sum_i\pi_iE_i[T_s]$（约定从 $s$ 出发记 $0$）不依赖二阶矩，它由一阶的 first-passage（首达）方程组唯一确定；以链乙、$s=1$ 为例，$E_1[T_1]=0$、$E_2[T_1]=2$、$E_3[T_1]=1$，稳态 $\pi=(0.5,0.25,0.25)$，加权和为 $0.75$。它既不等于 $1/\pi_1=2$，也和方差无关。真正需要二阶矩的是另一个问题：在稳态下随机挑一个时刻，若它落在 $s$ 的一次访问内部，问「还要等多久才离开 $s$」——这是 inspection paradox（检验悖论），答案是 $E[\tau^2]/(2E[\tau])$，在链乙上是 $5/4$，明显大于 $E[\tau]/2=1$。把三种量（首达加权、Kac 倒数、剩余逗留）混成一个，是这类题最常见的失分点。
>
> 命名上还要分清两个词。mean recurrence time（平均返回时间）指从 $i$ 出发、首次回到 $i$ 的期望步数，Kac 等式管的就是它；first passage time（首达时间）指从 $i$ 首次到达另一个状态 $j$ 的时间，$j$ 不能等于 $i$ 时其期望没有 $1/\pi$ 这种漂亮形式，只能解 $(I-P_{TT})^{-1}$ 那套线性方程组。把「返回自身的倒数关系」错误地推广到「任意两状态之间的距离」，是最常见的误用。
>
> 跨课程连接：与 §7.4 的吸收概率、吸收期望时间是同一套机器——把状态 $1$ 看成吸收目标，返回时间就是吸收时间，只不过目标恰好是出发点。与排队论的 Little's law（利特尔法则）也是同一句话的两种说法：平均在系统里的个数等于到达率乘以平均停留时间，把到达率换成「每块一次」、停留时间换成块长，就回到 $\pi=1/E[T]$。
>
> 边界与陷阱。第一，Kac 等式给的是 positive recurrent（正常返）情形；在可数无限、零常返的链上 $1/\pi_i$ 可能是无穷，等式退化，对称随机游走就是例子。第二，$E[T]=1/\pi_1$ 计数的是「从 $1$ 出发、包含下一步」的首次返回；若改问「从稳态下的随机时刻出发、等到下一次进入 $1$」，拿到的是上面那个 $0.75$ 型的加权首达量，不等于 $1/\pi_1$，两者差在「$s$ 自身算不算等待时间为零」。第三，(a)(c) 里「第 6 次」「第 1000 次」是转移次数而不是年份，与上一题的时间轴没有任何关系。
>
> 最后做一个数值自检：既然 $\pi_1=1/6$，那么 (a) 的 $n=6$ 只是一个中间时刻，答案一般不等于 $1/6$；而 (c) 的 $n=1000$ 应当非常接近 $1/6$。同时 (b) 的 $E[T]=6$ 与 $\pi_1$ 的分母相同——看到「稳态概率」和「平均返回时间」出现在同一道题里，第一反应就该把它们相乘验一下是否为 $1$，这是检测计算错误最快的一招。

> <span style="color:#7f8c8d;">[编号复原说明] Problem 29 的编号标签在本页源 OCR 中缺失（此前被误作「Solution（续）」）。以下内容为一道独立 Problem 的题干（任给马尔可夫链与稳态概率、以若干次转移后的状态概率及返回时间期望方差设问），其后接 Problem 30，再于下一页给出 (d)(e) 小问（即合并稿 p406 的 Problem 30（续））。故此处按 28→29→30 连续编号复原为 Problem 29。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 29.**</span>

Transition probabilities are specified. Consider the Markov chain with steady-state probabilities

```math
\pi_1 = \frac{1}{6}, \qquad \pi_2 = \frac{9}{?}, \qquad \pi_3 = \frac{1}{6}, \qquad \pi_4 = \;?,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 此页顶部四个稳态概率（$\pi_1,\pi_2,\pi_3,\pi_4$）的精确数值在 OCR 中被拆成碎片（如 `π₁ = …6`、`π₂ == 9 / …29`、`π₃ = …,6`、`π₄ == 1 0` 等字面），仅 $\pi_1$ 的 `1/6`、$\pi_3$ 的 `1/6` 相对可辨；$\pi_2$、$\pi_4$ 的分母/大小未能完整辨认。上式为按可辨字面所做的占位，未臆造确切数值，请以原书为准反查补全。</span>

The steady-state probabilities sum to $1$.

Assume that the process is in state 1 just before the first transition.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 紧接着的若干叙述句（"…with…"、"…p robabi l i t ies are …spec i fie d" 及其与马尔可夫链的衔接措辞）在 OCR 中残碎到只剩零散单词，无法逐字复原；上句按 "in state 1 just before the first transition" 这一可辨核心句重排。</span>

**(a)** … what is the probability that the process will be in state 1 at the sixth transition?

**(b)** Determine the expected value and variance of the number of transitions up to the next time the process returns to state 1.

**(c)** What is (approximately) the probability that the state … [after] 1000 …

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本块中段数条语句 OCR 严重碎裂（如 "…process w i l l …that …is …tr a n s i t i on ?…sixth…in state 1"、"…n e xt…process ret urns to state 1."、"…1 000 is…"），上文按可辨片段做了忠实拼接，(a)(c) 两问中标示 `…` 处为无法复原的残缺字面。</span>

---

> <span style="color:#7f8c8d;">[编号复原说明] 以下为 **Problem 30** 的题干（页内交叉引用「Problem … for Problem 30」即指向本题），编号标签在本页源 OCR 中缺失，现按 28→29→30 连续编号复原；题干主体为关于暂态/常返状态、常返类、稳态概率存在性，并基于图 7.25（Figure 7.25）设问，其 (d)(e) 续于下一页（合并稿 p406 的 Problem 30（续））。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 30.**</span>

Problem … for Problem 30.

… transient and recurrent states. Also, determine the recurrent classes … ones, if …

**(b)** Do there exist steady-state probabilities given … are …

**(c)** … I DO Ⅰ ?

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本段为交叉引用与后续一问的条件性内容，OCR 几乎只余零散单词与文内数学占位（如 "…I DO Ⅰ ?" 片段对应某数学式子），难以逐字复原；此处不再臆造题干措辞，仅保留可辨字面。</span>

Consider the Markov chains specified in Fig. 7.25.

<span style="color:#7f8c8d;">**[figure] Figure 7.25**（某马尔可夫链的转移概率示意图，fig caption 处 OCR 仅余 "7.25 : Transition …" 字样）</span>

**(a)** … the system resulting …

… exist steady-state probabilities … are …

… the process starts … state 1?

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末尾关于图 7.25（Figure 7.25）所示马尔可夫链的 (a)(b)(c) 各问，OCR 严重碎裂（"…the system resulting…"、"…exist steady-state probabilities…"、"…the process starts … state I ?" 等），仅能辨认出零散短语；各问完整措辞此处不臆造，请以原书为准。</span>

> <span style="color:#7f8c8d;">衔接下一面：本页处于第 7 章习题区（Problems 23–39）的中部，随后的习题承接 §7.4 吸收概率（absorption probabilities）与 §7.5 连续时间马尔可夫链（continuous-time Markov chains）相关题目。</span>
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 30 的 (d)(e) 把本章两条主线并排放置：(d) 站在 steady state（稳态）上观察，问随机时刻看到的转移长什么样；(e) 从 transient（暂态）出发，问最终落到哪个 recurrent class（常返类）、要等多久。前者是长期平均，后者是首次到达。
>
> (d) 的题面藏着一个刻意的陷阱：Assume that the process starts in state $1$ but we begin observing it after it reaches steady-state。前半句是无关信息——经过足够长时间再开始观察，起点分布已被抹平，观察时刻的状态服从 $\pi$。把起点当成固定状态 $1$ 去算，会得到一串看似合理但全错的数字；这正是题干把两句话并置的用意。
>
> (d)(i) 求「第一次观测到的转移使状态加一」的概率。起点是稳态，于是这只可能来自某条 $i\to i+1$ 的边，按 $\pi$ 加权求和：$\sum_i\pi_iP_{i,i+1}$。它就是所有向上边的稳态流量之和，量纲是「每次转移的概率」，不是速率。
>
> (d)(ii) 是标准的 Bayes（贝叶斯）反推：分子是「起点为 $2$ 且发生 $2\to3$」的概率 $\pi_2P_{23}$，分母就是 (i) 那个总量。图 7.25 处印的转移矩阵在本页 OCR 中已经碎裂，需要以书页 p397（PDF p405）的印刷页为准，此处不代入具体数值。这一步的教学价值在于说明：稳态条件下做条件化，等价于在 $\pi$ 上加权，先验乘似然再归一化，与有限维离散 Bayes 公式逐字对应。
>
> (d)(iii) 换的是条件事件的粒度：「第一次观测到的 state change（状态变化）」意味着跳过 self-loop（自环）。把每个 $P_{ii}$ 抹掉、剩余质量重新归一化，得到 jump chain（跳跃链），于是所求概率是 $\sum_i\pi_iP_{i,i+1}\big/\sum_i\pi_i(1-P_{ii})$：分子不变，分母从 $1$ 变成「发生变化的概率」。两个细节：自环越多，(i) 的答案越小而 (iii) 基本不变，因为除以变化率正好抵消；若链中有 absorbing state（吸收态，$P_{ii}=1$），它的 $1-P_{ii}=0$，公式自动把它排除在外，但手算时若用 $1-\pi_k$ 之类的写法替代分母，就会把吸收态的质量错算进来，把答案抬高。另一个常被忽略的点：跳步之后时间轴被压扁，跳跃链的「一步」等于原链若干步，所以跳跃链上的期望步数不能直接当原链的期望时间用。
>
> (e) 从状态 $4$ 出发，两问问的是 absorption probability（吸收概率）与 expected time to absorption（吸收期望时间）。设暂态集合为 $T$，则 $a_i=\sum_jP_{ij}a_j$ 在常返类上取 $0/1$ 边界值，$t_i=1+\sum_{j\in T}P_{ij}t_j$ 在常返类上取零。两者共用同一个矩阵 $I-P_{TT}$，只有右端项不同：一个是目标类的指示向量，一个是全一向量。所以工程上做一次 LU 分解就能回答任意多个目标类，每换一个类只换右端项——这是马尔可夫链分析的标准做法。
>
> 这个矩阵还有漂亮解读：$N=(I-P_{TT})^{-1}$ 是 fundamental matrix（基本矩阵），元素 $n_{ij}$ 等于从 $i$ 出发、在吸收前访问 $j$ 的期望次数（含 $0$ 时刻）。于是 $t=N\mathbf{1}$ 是「把所有状态的期望访问次数加起来」，$a=Nb$ 是「按到达边界的概率加权」。把线性代数读成计数，往往能立刻看出答案的量级：$N$ 的元素之和就是平均轨道长度。
>
> 唯一性从哪里来？有限链里每个暂态每步都有正概率向常返类靠近，故必以概率一逃出；此时 $I-P_{TT}$ 是 nonsingular M-matrix（非奇异 M 矩阵）。这里有一个必须纠正的常见说法：收敛的原因不是「$I-P_{TT}$ 的谱半径小于一」，而是「$P_{TT}$ 的 spectral radius（谱半径）$\rho(P_{TT})<1$」。$I-P_{TT}$ 的特征值是 $1-\lambda$（$\lambda$ 取遍 $P_{TT}$ 的特征值），它们的模一般大于一。取 $P_{TT}=\begin{pmatrix}0&1/2\\1/2&0\end{pmatrix}$：$\rho(P_{TT})=1/2$，而 $I-P_{TT}$ 的特征值是 $1/2$ 与 $3/2$，谱半径是 $3/2$。M-matrix 的定义正是「$A=sI-B$、$B\ge0$ 且 $\rho(B)<s$」，这里 $s=1$、$B=P_{TT}$；它保证 $A^{-1}\ge0$、$N$ 的元素全为非负有限数。判据放对位置，证明才走得通。
>
> 还有一个措辞要抠：题目写 up to and including the transition at which we reach a recurrent state，即「包含进入那一步」。若把期望写成「进入常返态前的期望步数」，整体会差一步——这是把 $t_i=1+\cdots$ 里的那个 $1$ 丢掉或重复计算的结果。
>
> 跨课程连接：$a_i=\sum_jP_{ij}a_j$ 是离散的 harmonic function（调和函数）方程，边界值取 $0/1$。它与实分析的 mean value property（中值性质）是同一句话——函数在一点的值等于邻域平均；也是 Strang 18.06 里解 $Ax=b$ 的差分方程结构，连续版本就是 Dirichlet problem（狄利克雷问题）：给定边界温度求内部温度，而 $a_i$ 正是「从 $i$ 出发最终撞到哪段边界的概率」。同一个方程在偏微分方程、随机游走、电阻网络三处出现，这是本章最值得带走的一条连接。
>
> 反例与边界：若 state space（状态空间）无限，暂态可能存在正概率永不落入任何常返类，此时 $I-P_{TT}$ 不可逆、$N$ 的元素发散，吸收概率仍然存在但不再是有限线性方程组的解——有限链排除了这种情况。另一个反例：常返类哪怕周期，$a_i$ 也照常存在（它只问最终去处，不问何时），但极限分布不收敛；「吸收」与「收敛」是两件事，不要因为都涉及极限就混为一谈。

<!-- ===== PDF p406 ===== -->

> <span style="color:#7f8c8d;">本页为第 7 章（Markov Chains，马尔可夫链）§7.4　Absorption Probabilities and Expected Time to Absorption（吸收概率与吸收期望时间）习题区续页，书页 397。页首为上一页 Problem 30 的（d）、（e）两部分的延续（题干起于上一页，故标注「续」），随后另起 Problem 31（带 `*` 难度标记）及其英文 Solution。本节习题题干与解答均保持英文原题。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 30（续）——（吸收概率 / 吸收期望时间）**</span>

**(d)** Assume that the process starts in state 1 but we begin observing it after it reaches steady-state.

(i) Find the probability that the state increases by one during the first transition we observe.

(ii) Find the conditional probability that the process was in state 2 when we started observing it, given that the state increased by one during the first transition that we observed.

(iii) Find the probability that the state increased by one during the first change of state that we observed.

**(e)** Assume that the process starts in state 4.

(i) For each recurrent class, determine the probability that we eventually reach that class.

(ii) What is the expected number of transitions up to and including the transition at which we reach a recurrent state for the first time?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 31.** \* Absorption probabilities.（吸收概率）</span>

Consider a Markov chain where each state is either transient or absorbing. Fix an absorbing state $s$. Show that the probabilities $a_i$ of eventually reaching $s$ starting from a state $i$ are the unique solution to the equations

```math
a_s = 1,
```

for all absorbing $i \neq s$,

```math
a_i = 0,
```

```math
a_i = \sum_{j=1}^{m} P_{ij}\, a_j, \qquad \text{for all transient } i.
```

**Hint.** If there are two solutions, find a system of equations that is satisfied by their difference, and look for its solutions.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.** The fact that the $a_i$ satisfy these equations was established in the text, using the total probability theorem (全概率定理). To show uniqueness, let $\bar{a}_i$ be another solution, and let $\delta_i = a_i - \bar{a}_i$. Denoting by $A$ the set of absorbing states and using the fact that $\delta_j = 0$ for all $j \in A$, we have

```math
\delta_i = \sum_{j=1}^{m} P_{ij}\, \delta_j = \sum_{j \notin A} P_{ij}\, \delta_j, \qquad \text{for all transient } i .
```

Applying this relation $m$ successive times, we obtain

```math
\delta_i = \sum_{j_1 \notin A} \sum_{j_2 \notin A} \cdots \sum_{j_m \notin A}
P_{i j_1}\, P_{j_1 j_2}\, \cdots \, P_{j_{m-1} j_m}\, \delta_{j_m} .
```

Hence

```math
\delta_i \;=\; P\bigl(X_1 \notin A,\, \ldots,\, X_m \notin A \mid X_0 = i\bigr)\, \bigl|\delta_{j_m}\bigr|
\;\le\; P\bigl(X_1 \notin A,\, \ldots,\, X_m \notin A \mid X_0 = i\bigr)\,
\max_{j \notin A}\, \bigl|\delta_j\bigr| .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 Problem 31 的 Solution 符号在 OCR 中严重碎片化：$\delta$（delta）被读成 `t5`，$\notin$（不属于）被读成 `` / `rJ`，绝对值 $|\cdot|$ 被读成 `l ... I`，求和 $\sum$ 被读成 `L`，下标 $j_1, j_2, \ldots, j_m$ 与乘积 $P_{i j_1} P_{j_1 j_2} \cdots P_{j_{m-1} j_m}$ 被打散。上文按标准数学记号与「相继应用该关系 $m$ 次」及反证法的规范论证还原，未臆造任何数值。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把这道题的代数骨架摆平。记 $A$ 为 absorbing states（吸收态）的集合、$T$ 为 transient states（暂态）的集合。题面的意思不是「被 $A$ 里随便哪一个吸收」，而是「最终到达指定的那一个吸收态 $s$」：边界条件是 $a_s=1$、其余吸收态 $a_i=0$，暂态则满足 $a_i=\sum_jP_{ij}a_j$。这一点极易写错——若把 $a$ 定义成「被 $A$ 中任意一个吸收态吸收」的概率，它在有限链上就恒等于 $1$，整套论证退化成平凡恒等式，什么都证不出来。
>
> 按 $T$、$A$ 分块，方程写成矩阵式是 $a_T=P_{TT}a_T+P_{TA}e_s$，即 $(I-P_{TT})a_T=P_{TA}e_s$，其中 $e_s$ 是 $s$ 在 $A$ 上的指示向量（若 $A$ 只有一个吸收态，它就退化成全一向量）。于是「吸收概率由方程唯一确定」这件事，被翻译成一句纯线性代数的话：$I-P_{TT}$ 是 invertible（可逆）的。
>
> 为什么可逆？第一性原理落在 $P_{TT}$ 的幂上。$P_{TT}^{k}$ 的第 $(i,j)$ 元，就是「从 $i$ 出发、前 $k$ 步一直没有离开 $T$、且第 $k$ 步恰在 $j$」的概率，所以 $P_{TT}^{k}\mathbf{1}_{T}$ 的第 $i$ 个分量正是 $P(X_1\notin A,\ldots,X_k\notin A\mid X_0=i)$。若能找到统一的 $m$ 与 $\beta<1$，使对每个暂态起点这个概率都不超过 $\beta$，就有 $\lVert P_{TT}^{m}\mathbf{1}_{T}\rVert_\infty\le\beta$，连乘 $k$ 次得 $\lVert P_{TT}^{mk}\mathbf{1}_{T}\rVert_\infty\le\beta^{k}\to0$，即 $P_{TT}^{mk}\to0$，于是 spectral radius（谱半径）满足 $\rho(P_{TT})<1$，Neumann series（诺伊曼级数）$\sum_{k\ge0}P_{TT}^{k}=(I-P_{TT})^{-1}$ 收敛。唯一性就是这条几何级数的另一种说法。
>
> 这里有个必须点明的技术细节：$\beta$ 依赖起点。正确写法是 $\beta=\max_{i\notin A}P(X_1\notin A,\ldots,X_m\notin A\mid X_0=i)$，$i$ 上的最大值不能省。不取这个最大值，只能得到逐点的 $\delta_i\le\beta_i\max_j|\delta_j|$，而 $\beta_i$ 各不相同，无法凑出 $\max|\delta|\le\beta\max|\delta|$ 这种能把公因子提出来的闭合不等式。取 $\max$ 这一步不是修辞，是证明的承重墙。
>
> 再说 contraction（收缩）这个名字的严格含义。Banach fixed point theorem（巴拿赫不动点定理）要求的是：完备 metric space（度量空间）上的映射 $F$ 存在 $0\le\beta<1$，使 $d(Fa,Fb)\le\beta\,d(a,b)$。本题的 $F(a)=P_{TT}a+P_{TA}e_s$ 在 sup-norm（上确界范数）下的 Lipschitz 常数是 $\max_i\sum_{j\in T}P_{ij}\le1$，单步并不收缩。真正收缩的是它的 $m$ 次复合，其常数 $\le\beta<1$。所以课本证明的准确内容是「$F^{m}$ 是 contraction（收缩），故 $F^{m}$ 有唯一不动点」；而 $F$ 与 $F^m$ 的不动点集相同（$Fa=a$ 显然给出 $F^ma=a$；反之若 $F^ma=a$，则 $Fa$ 也是 $F^m$ 的不动点，由 $F^m$ 的唯一性得 $Fa=a$），结论照旧成立。这个层级差别是把「收缩」从比喻变成定理的唯一缝隙：一旦有人把单步范数当成小于一，证明立刻失效。
>
> 两处容易点错对象的地方要说清。第一，$(I-P)^{-1}$ 这个写法不成立：若 $P$ 取整条链的 transition matrix（转移矩阵），每个吸收态对应的行都是单位行，$I-P$ 相应整行为零，determinant（行列式）为零，根本不可逆；可逆的只有暂态子矩阵 $Q=P_{TT}$，$N=(I-Q)^{-1}$ 才叫 fundamental matrix（基本矩阵）。$N_{ij}$ 是从 $i$ 出发、在被吸收之前访问 $j$ 的 expected number of visits（期望访问次数），$N\mathbf{1}_{T}$ 才是期望吸收时间；把「基本矩阵」与「期望逗留时间」压成一句，且点错矩阵，是两处独立的错误。第二，「暂态必被吸收」在 finite state（有限状态）下是定理，不是前提：若从某暂态出发有正概率永不进 $A$，这份概率质量只能永远留在有限的 $T$ 内，于是 $T$ 中存在 closed（封闭）子集，它本身是常返类，与「这些状态是暂态」直接矛盾。所以 $\beta<1$ 自动成立，无需额外假设。
>
> 真正会崩的是可数无限的状态空间：此时可能出现零常返结构，$\rho(P_{TT})=1$，方程的有界解不再唯一。整数上的对称随机游走就是例子，$a_i=\frac12(a_{i-1}+a_{i+1})$ 的有界解只能是常数，任何一侧边界都定不出唯一答案。把「有限」这一条挪走，塌的才是地基。
>
> 跨课程的一句话：$I-P_{TT}$ 是 random-walk Laplacian（随机游走拉普拉斯）的化身，$a_T$ 是离散 Dirichlet problem（狄利克雷问题）的解；「解唯一」等价于 electrical network（电网络）里在 $A$ 上接 $1$ 伏、其余接地时各节点 voltage（电压）被唯一确定（Kemeny–Snell 的经典对应）。同一个可逆性，在 18.06 里叫「对角占优加不可约」，在概率里叫「暂态必被吸收」，在电路里叫「漏电网络的稳态唯一」。

> <span style="color:#7f8c8d;">跨页续接：Problem 31 的英文 Solution 尚未在本页收尾——其唯一性证明（通过 $\beta<1$ 的收缩（contraction）技术导出 $\max_{j\notin A}|\delta_j|$ 的上界）延续到下一页（PDF p407）才完成；Problem 32 亦出现在下一页。本页正文至此结束。</span>
<!-- ===== PDF p407 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）　§7.4 吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）· 习题收尾（续）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页顶部延续上一页（PDF p406）某一道带 `*` 题英文 Solution 的收尾段（即 Problem 31 的唯一性收敛论证）。原文为一套关于转移概率收敛性（convergence）与稳态概率唯一性（uniqueness）的论证（含 $\max_{j\notin A}|\delta_j|$ 与吸收态集 $A$、暂态（transient）集），在 OCR 中被切碎为多个残片（如 `max 18j I`, `f3 . max 1 8j I`, `at for all i that are not`, `absorbing. It follows that…`, `0, or ai`, `aj = aj` 等）。因本题带 `*`，其英文 Solution 按规范保留英文；下方按原书 §7.4 惯例的收敛证法做忠实连贯转写，未臆造原文未含的任何数值。</span>

We use the above relation for every transient state $i$, and we obtain

```math
\max_{j\notin A} |\delta_j| \;\le\; \beta \cdot \max_{j\notin A} |\delta_j|,
```

where

```math
\beta \;=\; P(X_1 \notin A,\, \ldots,\, X_m \notin A \mid X_0 = i).
```

Note that $\beta < 1$, because starting from any state, there is a positive probability that $X_m$ is in an absorbing state. Hence, $\max_{j\notin A}|\delta_j| = 0$, which implies that $\delta_i = 0$ for all nonabsorbing $i$. Since $\delta_j = 0$ for all absorbing $j$ as well, we have $\delta_i = 0$ for all $i$, i.e., $a_i = \bar{a}_i$ for all $i$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 顶部结尾两行的等式残片（第二行 `=`,`0, or ai`，及末尾 `aj = aj for all absorbing j, so ai = ai for all i` 与两处 `=`）排版错乱，此处按行文语义（经 $\beta<1$ 得出 $\max_{j\notin A}|\delta_j|=0$，再由吸收态与暂态逐类接通）整理为收敛结论，未新增数值。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 32\*（多个常返类，Multiple recurrent classes。英文原题与解答保留。）**</span>

Problem 32. \* Multiple recurrent classes. Consider a Markov chain that has more than one recurrent class, as well as some transient states. Assume that all the recurrent classes are aperiodic.

(a) For any transient state $i$, let $a_i(k)$ be the probability that starting from $i$ we will reach a state in the $k$th recurrent class. Derive a system of equations whose solutions are the $a_i(k)$.

(b) Show that each of the $n$-step transition probabilities $r_{ij}(n)$ converges to a limit, and discuss how these limits can be calculated.

<span style="color:#00838f;">**Solution.**</span> (a) We introduce a new Markov chain that has only transient and absorbing states. The transient states correspond to the transient states of the original, while the absorbing states correspond to the recurrent classes of the original. The transition probabilities $\bar{p}_{ij}$ of the new chain are as follows: if $i$ and $j$ are transient, $\bar{p}_{ij} = p_{ij}$; if $i$ is a transient state and $k$ corresponds to a recurrent class, $\bar{p}_{ik}$ is the sum of the transition probabilities from $i$ to states in the recurrent class in the original Markov chain. The desired probabilities $a_i(k)$ are the absorption probabilities in the new Markov chain and are given by the corresponding formulas:

```math
a_i(k) = \bar{p}_{ik} + \sum_{j:\ \text{transient}} \bar{p}_{ij}\, a_j(k), \qquad \text{for all transient } i.
```

(b) If $i$ and $j$ are recurrent but belong to different classes, $r_{ij}(n)$ is always $0$. If $i$ and $j$ are recurrent but belong to the same class, $r_{ij}(n)$ converges to the steady-state probability of $j$ in a chain consisting of only this particular recurrent class. If $j$ is transient, $r_{ij}(n)$ converges to $0$. Finally, if $i$ is transient and $j$ is recurrent, then $r_{ij}(n)$ converges to the product of two probabilities: (1) the probability that starting from $i$ we will reach a state in the recurrent class of $j$, and (2) the steady-state probability of $j$ conditioned on the initial state being in the class of $j$.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题的核心动作是一次 lumping（合并）：把每个 recurrent class（常返类）整体捏成一个 absorbing state（吸收态），于是原链变成一个只有暂态与吸收态的辅助链，转移概率取 $\bar p_{ik}=\sum_{j\in C_k}P_{ij}$。第 (a) 问的方程 $a_i(k)=\bar p_{ik}+\sum_{j\ \text{transient}}\bar p_{ij}a_j(k)$ 就是 Problem 31 那套吸收概率方程原样搬过来，边界条件为 $a_i(k)=1$ 当 $i\in C_k$、$a_i(k)=0$ 当 $i$ 属于别的类。为什么合并合法？因为从暂态出发一旦进入某个类就再也出不来，类内怎么游走不影响「落进哪一类」这件事——这正是 Markov property（马尔可夫性质）允许把一整块状态当作黑箱的原因。
>
> 第 (b) 问的答案是四种情形的拼接，逐条写清才不会混。其一，$i$ 与 $j$ 同属一个类：$r_{ij}(n)$ 收敛到「只看这一个类、把它当成整条链」时的 steady-state probability（稳态概率）$\pi^{(k)}_j$。其二，$i$ 与 $j$ 属于不同类：$r_{ij}(n)\equiv0$，永不可达。其三，$i$ 暂态、$j$ 属于第 $k$ 类：$r_{ij}(n)\to a_i(k)\,\pi^{(k)}_j$，即「先落进第 $k$ 类的概率」乘「类内稳态」。其四，$i$ 暂态、$j$ 也是暂态：$r_{ij}(n)\to0$，因为暂态只被访问有限多次。第三种情形的因子化是全部要点：暂态决定的是投递分布，类内分布由该类自己混合，两者相乘而非耦合。
>
> 用矩阵写，极限 $H=\lim_n P^{n}$ 存在，且 $H_{ij}=a_i(\kappa(j))\,\pi^{(\kappa(j))}_j$，其中 $\kappa(j)$ 表示 $j$ 所属的常返类；$j$ 暂态时整列为零。等价地 $H=\sum_k r^{(k)}(\pi^{(k)})^{T}$，其中 $r^{(k)}$ 是列向量、第 $i$ 个分量等于 $a_i(k)$（类内取 $1$）。这个 $H$ 是 idempotent（幂等）的，$H^2=H$。
>
> 三个量容易混，必须分开记，其中第一个是本条最需要纠正的。$H$ 的 rank（秩）等于常返类的个数，不是常返状态的个数：理由是上面那个分解，若 $\sum_k c_k r^{(k)}=0$，把等式限制在 $C_k$ 上，只有 $r^{(k)}$ 在 $C_k$ 上非零，于是 $c_k=0$，各列线性无关。举个能一眼看出差别的例子：两个常返类、每类两个状态（设各类非周期；否则 $P^n$ 不收敛，$H$ 根本不存在）、外加暂态，$P^{4000}$ 的数值秩是 $2$，而常返状态有 $4$ 个，相等的是前者与类数。第二个量：$P$ 在 $\lambda=1$ 处的 geometric multiplicity（几何重数）与 algebraic multiplicity（代数重数）都等于常返类数，因为 $\dim\ker(I-P)$ 恰好数出「有几个互不相通、一旦进入就不再离开的封闭类」。第三个量：$P_{TT}^{n}\to0$ 的衰减速度由 $\rho(P_{TT})<1$ 决定，是指数级的。三者的共同点是「都等于类数」或「都由 $P_{TT}$ 的谱决定」，但把「秩」写成「常返状态数」会让 $H$ 看起来比实际大得多。
>
> 术语上还有一处要更正：非负矩阵理论里与本题对应的标准名字是 Frobenius normal form（Frobenius 标准型）：存在一个 permutation matrix（置换矩阵）使 $P$ 化成 block lower triangular（块下三角），对角块 irreducible（不可约），每一块对应一个 communicating class（互通类）。「Levinson 分解」不是这个领域的术语——Levinson–Durbin recursion（Levinson–Durbin 递推）是 Norman Levinson 于 1947 年、James Durbin 于 1960 年先后给出的，用途是以 $O(n^2)$ 解 Toeplitz 线性方程组，与马尔可夫链的分类无关。两者都姓「分解」，但一个拆状态空间、一个拆 Toeplitz 结构，混用会让检索失效。至于 Perron–Frobenius：Oskar Perron 在 1907 年证明正矩阵情形，Ferdinand Georg Frobenius 在 1912 年推广到不可约非负矩阵，这正是本题「一个类对应一个主特征向量」的来源。
>
> 「所有常返类都要 aperiodic（非周期）」这条假设不是装饰品，而是收敛性的开关。取一个二周期类：状态在 $0$、$1$ 之间交替，$P=\begin{pmatrix}0&1\\1&0\end{pmatrix}$，则 $r_{00}(n)$ 在 $1,0,1,0,\ldots$ 之间摆，极限不存在；此时 $P$ 的特征值里有 $-1$，落在单位圆上但不在 $1$ 处，$P^n$ 整体不收敛。所以 (b) 问的结论依赖「每类非周期」，缺了它连「极限存在」这一句都写不出来，更不用谈怎么算。
>
> 最后一条工程化的读法：既然暂态部分以指数速度消失，那么「长期行为」完全由各常返类内部的稳态决定，暂态只留下一个投递权重 $a_i(k)$。这就是把一个大链拆成「一个漏斗加若干水池」的正确数学形态——漏斗只回答落点，水池各自内部混合。实际算的时候，(a) 给出漏斗，类内解平衡方程给出水池，两者相乘即得 (b)。这条分解也是 PageRank 与 Markov chain 聚类里反复使用的结构：先找封闭类，再在类内求稳态。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 33\*（平均首达时间，Mean first passage times。英文原题保留。）**</span>

Problem 33. \* Mean first passage times. Consider a Markov chain with a single recurrent class, and let $s$ be a fixed recurrent state. Show that the system of equations

```math
t_s = 0,
```

```math
t_i = 1 + \sum_{j=1}^{m} p_{ij}\, t_j , \qquad \text{for all } i \neq s,
```

satisfied by the mean first passage times, has a unique solution. **Hint:** If there are two solutions, find a system of equations that is satisfied by their difference, and look for its solutions.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题问的是「唯一解」，但更该被追问的是「解是否真的存在」。两者是两件事，而课本只证了后者的一半。先把 first-step analysis（首步分析）的推导钉死：设 $t_i$ 为从 $i$ 出发首次到达固定常返态 $s$ 的期望步数，$t_s=0$。从 $i\ne s$ 出发，第一步必然发生、必然消耗 $1$ 步，之后以 $P_{ij}$ 落在 $j$，于是总期望等于 $1$ 加上「从 $j$ 重新开始的期望」，把第一步单独条件化就得到 $t_i=1+\sum_jP_{ij}t_j$。这不是技巧，而是 total expectation theorem（全期望定理）作用在「第一步落点」这个有限 partition（划分）上的直接结果。
>
> 存在性靠的是有限与单一常返类。设链有 $m$ 个状态、只有一个常返类，则存在整数 $k$ 与 $\epsilon>0$，使从任意起点出发、在 $k$ 步内到达 $s$ 的概率至少 $\epsilon$（取 $k=m$ 即可：任一状态到 $s$ 有长不超过 $m-1$ 的正概率路径，取这些概率的最小值作 $\epsilon$）。于是 $P(T>nk)\le(1-\epsilon)^{n}$，几何尾界把期望压住：$E[T]\le\sum_{n\ge0}(1-\epsilon)^{n}k=k/\epsilon<\infty$。注意这里「有限状态」被用了两次：一次保证 $\epsilon>0$，一次保证 $k$ 有限。可数无限链条上这条推理整段失效，这正是反例的来源。
>
> 唯一性只是把吸收概率那套论证换一个字母重抄。设 $\tilde t_i$ 是另一组解，$\delta_i=\tilde t_i-t_i$，两式相减得 $\delta_i=\sum_{j\ne s}P_{ij}\delta_j$，且 $\delta_s=0$。注意求和里 $j=s$ 的项自动消失，因为 $\delta_s=0$——这个细节让「$m$ 步内一直避开 $s$」的概率顶上那个收缩常数。把关系反复代入 $m$ 次，$\delta_i$ 就被写成「$m$ 步内不碰 $s$ 的概率」乘 $\max_{j\ne s}|\delta_j|$ 的加权和，取 $\beta=\max_{i\ne s}P(X_1\ne s,\ldots,X_m\ne s\mid X_0=i)<1$，便得 $\max|\delta|\le\beta\max|\delta|$，只能是零。与 Problem 31 对照着读：吸收概率证的是 $I-P_{TT}$ 可逆，首达时间证的是 $I-P_{T}$ 可逆（$T$ 为除 $s$ 外的状态集），两个矩阵都是 sub-stochastic（次随机）且去掉了一个吸收/目标行，收缩论证一字不改。
>
> 矩阵语言把整件事压缩成一行：$(I-P_T)t=\mathbf{1}_{T}$，故 $t=(I-P_T)^{-1}\mathbf{1}_{T}=N\mathbf{1}_{T}$，其中 $N=\sum_{k\ge0}P_T^{k}$ 是 fundamental matrix（基本矩阵）在本题的样子。$N_{ij}$ 读作「从 $i$ 出发、在碰到 $s$ 之前访问 $j$ 的期望次数」；对 $j$ 求和才得到期望步数。这个 $N$ 与 18.06 里的 resolvent（预解式）$(I-A)^{-1}$ 是同一个对象：把 $\lambda=1$ 处的极点避开，$N$ 就是「瞬态部分的逆」。电网络视角更强：$I-P_T$ 是 random-walk Laplacian（随机游走拉普拉斯），$t$ 是离散 Dirichlet problem（狄利克雷问题）在边界 $s$ 上取 $0$、源项恒为 $1$ 时的解；换成「边界取 $1$、源项为 $0$」就退回吸收概率。同一个方程，两种解释。
>
> 反例的机制必须说透，因为这里的结论是与直觉相反的。若 $s$ 只是暂态，方程组不是「解不唯一」，而是根本没有解。论证用到 Fredholm alternative（二择一定理）：$s$ 暂态时，剩下的集合 $T$ 里必然含至少一个常返类 $C$，于是指示向量 $y=\mathbf{1}_{C}$ 满足 $y^{T}(I-P_T)=0$（$C$ 是封闭的，从 $C$ 出不去的质量行和为 $1$，转置后正好被 $y$ 零化）；而 $y^{T}\mathbf{1}_{T}=|C|>0$，说明右端向量 $\mathbf{1}_{T}$ 与 $I-P_T$ 的左零空间不正交，故方程无解。
>
> 一个两行的具体例子把这句断言钉死：取 $T=\{1,2\}$、$P_T=\begin{pmatrix}1&0\\1&0\end{pmatrix}$（状态 $1$ 是留在 $T$ 里的常返类，状态 $2$ 必跳进 $1$），则 $I-P_T=\begin{pmatrix}0&0\\-1&1\end{pmatrix}$，秩为 $1$，而增广矩阵 $[\,I-P_T\mid\mathbf{1}\,]$ 的秩是 $2$，rank（秩）不相等意味着无解——直观上就是两个方程要求同一个未知组合同时等于 $0$ 和 $1$。若把右端换成落在列空间里的向量（例如只对某一个起点设 $1$ 而其余设 $0$，恰好与 $y$ 正交），才会有解，而且此时解是无限多个：齐次方程 $\delta=P_T\delta$ 的非零解就是「常数取在常返类上、别处取零」。所以正确的因果链是：$s$ 暂态 ⇒ 矩阵奇异且右端一般不在值域内 ⇒ 无解；只有在右端碰巧相容的边上，才退化为不唯一。
>
> 算之前先确认 $s$ 常返、且从每个状态都能到达 $s$（等价于 $P_T$ 没有封闭类，也等价于 $\rho(P_T)<1$）——这是判断「方程有没有唯一解」的实用准则。顺带把两组「首达」与「首返」区分开：本题的 $t_i$ 是从 $i$ 出发首次到达 $s$ 的期望（$i$ 任意、$s$ 固定）；$t_s$ 被规定为 $0$，是「已经在那里」，不计数。而 mean recurrence time（平均循环时间）是从 $s$ 出发首次回到 $s$ 的期望，恒正，且等于 $1/\pi_s$（Kac 1947，见下一题的注）。课本把 $s$ 那一行直接钉成 $0$，等于把「首达」定义成「不含出发时刻」，这个约定一旦写错，$N$ 的行和与 $1/\pi_s$ 就对不上。

<!-- ===== PDF p408 ===== -->

<span style="color:#7f8c8d;">§7.4 习题区（Problems，习题 28–35）——吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）中部续页。本页开头顶部是**上一题（Problem 33，平均首达时间）解答的收尾部分**（页首无新节/新题目标题，故以其为承接延续），随后本页另起 **Problem 34**（带 `*` 星号，关于平衡方程与平均循环时间）。本页**不含第 8 章章题目行**，仍属第 7 章习题区；第 8 章红色章标题在后续页（书页 p408）出现。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本页为习题区（Problems），题干与英文解答照规范**保留英文原文**。顶部承接段落中的符号 `Ii`、`8i` 为 OCR 碎裂，实为 $\tilde{t}_{i}$（另一组解）与 $\delta_{i}=\tilde{t}_{i}-t_{i}$（差值）；其余求和下标 `j#s`、`jm#s` 等系 OCR 对 `\sum_{j\neq s}`、`\sum_{i_m\neq s}` 的残片，均已按体积反查校准，未臆造数值。</span>

---

承上题（关于平均首达时间 mean first passage times、唯一性证明）的英文解答收尾（承接延续）：

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Solution（解答收尾，承接上一题）**</span>

Solution. Let $t_i$ be the mean first passage times (平均首达时间). These satisfy the given system of equations. To show uniqueness, let $\tilde{t}_i$ be another solution. Then we have for all $i \neq s$

```math
t_i = 1 + \sum_{j \neq s} P_{ij} \, t_j,
\qquad
\tilde{t}_i = 1 + \sum_{j \neq s} P_{ij} \, \tilde{t}_j,
```

and by subtraction, we obtain

```math
\delta_i = \sum_{j \neq s} P_{ij} \, \delta_j,
```

where $\delta_i = \tilde{t}_i - t_i$. By applying this relation $m$ successive times, it follows that

```math
\delta_i
= \sum_{i_1 \neq s} P_{i i_1}\,
 \sum_{i_2 \neq s} P_{i_1 i_2}
 \cdots
 \sum_{i_m \neq s} P_{i_{m-1} i_m}\,\delta_{i_m}.
```

Hence, we have for all $i \neq s$

```math
|\delta_i|
= P(X_{1} \neq s, \ldots, X_{m} \neq s \mid X_{0} = i)\cdot \max_{j} |\delta_j|.
```

On the other hand, we have $P(X_{1} \neq s, \ldots, X_{m} \neq s \mid X_{0} = i) < 1$. This is because starting from any state there is positive probability that $s$ is reached in $m$ steps. It follows that all the $\delta_i$ must be equal to zero.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 34 \*．平衡方程与平均循环时间（Balance equations and mean recurrence times）**</span>

Consider a Markov chain (马尔可夫链) with a single recurrent class (单一常返类), and let $s$ be a fixed recurrent state (常返状态). For any state $i$, let

```math
p_i = E[\text{Number of visits to } i \text{ between two successive visits to } s],
```

where by convention, $p_s = 1$.

(a) Show that for all $i$, we have

```math
p_i = \sum_{k=1}^{m} p_k \, P_{ki}.
```

(b) Show that the numbers

```math
\pi_i = \frac{p_i}{t_s}, \qquad i = 1, \ldots, m,
```

sum to 1 and satisfy the balance equations (平衡方程), where $t_s$ is the mean recurrence time (平均循环时间) of $s$ (the expected number of transitions up to the first return to $s$, starting from $s$).

(c) Show that if $\pi_1, \ldots, \pi_m$ are nonnegative, satisfy the balance equations, and sum to 1, then

```math
\pi_i =
\begin{cases}
\displaystyle \frac{1}{t_s}, & \text{if } i \text{ is recurrent},\\
0, & \text{if } i \text{ is transient},
\end{cases}
```
<!-- ===== PDF p409 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

<span style="color:#7f8c8d;">§7.4 习题区（Problems，习题 28–35）——**Problem 34 \*（平衡方程与平均循环时间，Balance equations and mean recurrence times）解答续页**。承接 PDF p408 的题干部分 (c)（本页页首先补完 part (c) 那条公式的「其中 $t_s$ 为平均循环时间」之结尾），随后给出 part (d) 与题末 Note，最后转入该题的英文解答 Solution (a)。本页**无第 8 章章题目行**，仍属第 7 章习题区；题干与带 `*` 题的英文解答照规范**保留英文原文**。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本页为习题区（Problems），**题干与英文解答均保留英文**。页内公式与后续可辨符号中，`X1 = s, …, Xn-1 = s` 之等号系 OCR 丢失**否定符号**（应为 $X_{1}\neq s,\ldots,X_{n-1}\neq s$，即两次相继访问 $s$ 之间尚未返回 $s$），已按前后文（Problem 34 对 $P_i$ 的定义及下一页 p410 的同类公式）反查校准；`∑_{n=1}^∞`、`∑_{k\neq s}` 等求和符号亦为 OCR 残片重排。全部仅作符号复原，未臆造任何数值。</span>

---

承接 PDF p408 的 Problem 34 题干（延续上页 part (c) 那条在 p408 收尾处的公式，本页页首补其条件说明末端）：

该式即：对常返状态 $i$ 有 $\pi_i = \dfrac{p_i}{t_s}$，对暂态状态 $i$ 有 $\pi_i = 0$；本页页首补其条件说明的末端——**where $t_s$ is the mean recurrence time of $s$**（即：其中 $t_s$ 是 $s$ 的平均循环时间）。

**(d)** Show that the distribution of part (b) is the unique probability distribution that satisfies the balance equations (平衡方程).

<span style="color:#7f8c8d;">**Note:**</span> This problem not only provides an alternative proof of the existence and uniqueness of probability distributions that satisfy the balance equations, but also makes an intuitive connection between steady-state probabilities (稳态概率) and mean recurrence times (平均循环时间). The main idea is to break the process into "cycles" (循环), with a new cycle starting each time that the recurrent state $s$ is visited. The steady-state probability of $i$ can be interpreted as the long-term expected frequency of visits to state $i$, which is inversely proportional to the average time between consecutive visits (the mean recurrence time $t_s$); cf. part (c). Furthermore, if a state $i$ is expected to be visited, say, twice as often as some other state $j$ during a typical cycle, it is plausible that the long-term expected frequency $\pi_i$ of state $i$ will be twice as large as $\pi_j$. Thus, the steady-state probabilities $\pi_i$ should be proportional to the expected number of visits $p_i$ during a cycle; cf. part (b).

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题的构造是「把轨道沿着 $s$ 剪开」。定义 $p_i$ 为一个 cycle（循环）内访问状态 $i$ 的期望次数，$t_s$ 为 mean recurrence time（平均循环时间），即从 $s$ 出发首次回到 $s$ 的期望步数。剪开之后有两件立刻成立的事，很多人跳过不证就直接用：其一，每个时刻恰处在一个状态，所以一个循环的长度等于各状态被访问次数之和，取期望得 $t_s=\sum_ip_i$；其二，每个循环恰好含一个 $s$（起点计、终点不计），所以 $p_s=1$。这两条一凑，$\pi_i=p_i/t_s$ 的和自动为 $1$：分子之和就是分母。归一化不是额外条件，而是「每个时刻只能在一个状态」这条记账规则的推论。
>
> (a) 的方程是 $p_i=\sum_{k=1}^{m}p_kP_{ki}$，求和从 $k=1$ 开始、到 $m$ 结束，指标是「出发状态 $k$」，不是对 $i$ 求和。它的读法是「入流计数」：一个循环里进入 $i$ 的次数，等于从各状态 $k$ 离开并落到 $i$ 的次数之和；而循环内离开 $k$ 的期望次数恰是 $p_k$（$k=s$ 时把循环起点那一次出发也算进去），每次以 $P_{ki}$ 落到 $i$。把 $p_s=1$ 代入即得 $\pi_i=p_i/t_s$ 满足 $\pi_i=\sum_k\pi_kP_{ki}$：两边同除 $t_s$ 就完事。这个方程的概率含义是：离开 $k$ 的流量按 $P_{ki}$ 分流，稳态下来到 $i$ 的流入等于 $i$ 的驻留份额。注意这里的求和是「入流」形式，与课本 §7.3 常写的「出流」形式互为转置，两者等价靠的是行和为 $1$。
>
> 于是 (b) 的两句话各有独立内容：和为 $1$ 是循环记账的算术，满足平衡方程是「把方程除以常数」的自动结果，两件事都不需要额外假设。真正的定理在 (d)：单一常返类时，满足平衡方程且和为 $1$ 的分布唯一。为什么唯一？$I-P^{T}$ 的零空间维数等于常返类个数（理由见 Problem 32 那条注里对 $\dim\ker(I-P)$ 的说明：它数的是封闭类的个数），单类时为 $1$，所以解空间是一维直线，再钉上归一化就只剩一点。反过来说，若链有 $k>1$ 个常返类，解空间是 $k$ 维，所有「按类加权混合」的分布都满足平衡方程且和为 $1$，唯一性彻底失效——这也解释了 Problem 32 为什么要先把类压成吸收态再谈极限。
>
> 长期频率的解释：$p_i/t_s$ 等于轨迹长期停留在 $i$ 的时间比例。这条断言不能一笔带过，它需要 strong law of large numbers（强大数定律）作用在循环长度这个 i.i.d.（独立同分布）序列上——相继两次回到 $s$ 之间的块，其长度与内容由强马尔可夫性保证是独立同分布的，于是每块的指示量求平均即收敛到期望，这正是 Problem 35 用模进夹逼证明的那件事。把「时间比例」与「空间平均」连起来的一般定理叫 ergodic theorem（遍历定理），Birkhoff 在 1931 年证明的 pointwise（逐点）遍历定理是它的源头；马尔可夫链只是它最易验证的特例。工程上这套记账叫 renewal reward theorem（更新报酬定理）：把「回到 $s$」看作 renewal（更新）点，把「访问 $i$ 的次数」看作每个周期领到的报酬，长期平均报酬率等于单周期期望报酬除以单周期期望长度，形式完全一样。
>
> 必须标出一处与正文对不上的地方。(c) 问印出的结论是：若 $i$ 常返则 $\pi_i=1/t_s$，若 $i$ 暂态则 $\pi_i=0$。前一半在数学上只在 $p_i=1$ 时成立，一般应为 $\pi_i=p_i/t_s$。理由两条：第一，与 (b) 直接冲突——(b) 说的是 $\pi_i=p_i/t_s$，两者相等要求所有常返态的 $p_i$ 都等于 $1$；三状态环 $1\to2\to3\to1$ 里每个 $p_i$ 都等于 $1$ 只是巧合，一旦有自环或不等权转移，$p_i$ 立刻偏离 $1$（例如状态 $i$ 有两个自环的平均逗留，$p_i$ 就等于 $2$）。第二，与归一化冲突：若所有常返 $i$ 都取 $1/t_s$，和就是「常返状态数除以 $t_s$」，只有单状态链才等于 $1$。因此正确形式应是 $\pi_i=p_i/t_s$（$i$ 常返），暂态为零——也就是 (b) 的结论在 (d) 的假设下重复一遍。此处疑为 OCR 丢掉了 $p_i$ 这个因子（待回查纸本 p400 印刷页确认）（本页页首的碎裂说明已指出该页符号严重残缺），建议以书页 p400–p401（PDF p408–p409）的印刷式为准；无论如何，按现印的 $1/t_s$ 读不通，这一点以数学为准而不以 OCR 为准。
>
> 暂态为什么会拿到零权重，理由比「比值被压到零」更硬。单一常返类加上 $s$ 常返，就排除了「从 $s$ 可达的暂态」：若某个暂态 $i$ 从 $s$ 可达，那么从 $s$ 出发就有一条正概率的路径走进 $i$ 且永不返回，$s$ 立刻不再是常返态，矛盾。所以暂态从 $s$ 根本不可达，$p_i=0$，$\pi_i=0$ 是 $p_i$ 本身为零，而不是 $t_s$ 取到无穷大尺度的结果。做题时若把暂态也配非零稳态权重，平衡方程仍可能被满足（只要流入等于流出），归一化却会与 (b) 的解错位——这是最常见的失分点。

---

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（解答，Problem 34 \*，英文解答保留）.**</span> (a) Consider the Markov chain $X_n$, initialized with $X_0 = s$. We claim that

```math
p_i = \sum_{n=1}^{\infty} P(X_{1}\neq s, \ldots,\, X_{n-1}\neq s,\, X_{n} = i).
```

To see this, we first consider the case $i \neq s$, and let $I_n$ be the random variable that takes the value $1$ if $X_{1} \neq s, \ldots,\, X_{n-1}\neq s$, and $X_{n}=i$, and the value $0$ otherwise. Then, the number of visits to state $i$ before the next visit to state $s$ is equal to $\sum_{n=1}^{\infty} I_n$. Thus,

```math
p_i = \mathbb{E}\!\left[\sum_{n=1}^{\infty} I_n\right]
    = \sum_{n=1}^{\infty} \mathbb{E}[I_n]
    = \sum_{n=1}^{\infty} P(X_{1}\neq s, \ldots,\, X_{n-1}\neq s,\, X_{n} = i),
```

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本页脚注（原页以 t 标示）用于证明随后计算中「无限求和与数学期望可交换」这一论断，其文字大体可辨，但中间的**一条不等式**残碎到无法逐字复原（涉及对任意 $k>0$ 的截断求和，以及「$T$ 为首次正向到达 $s$ 的时刻，均值 $\sum_t t\,P(T=t)$ 有限，故 $k\to\infty$ 时 $\sum_{t>k}P(T=t)\to 0$」），此处按语义做平滑连贯转写，未臆造具体数值。</span>

> <span style="color:#7f8c8d;">脚注（footnote）译文大意：**随后的计算中，无限求和与期望的交换可用如下论证加以说明。** We have for any $k > 0$，截断后的有限和与后续尾项之间成立相应关系。Let $T$ be the first positive time that state $s$ is visited. Since the mean recurrence time $\sum_t t\,P(T=t)$ is finite, the limit, as $k\to\infty$, of $\sum_{t>k} P(T=t)$ is equal to zero. We take the limit of both sides of the earlier equation, as $k\to\infty$, to obtain the desired relation.（因脚注公式损坏，此处以中文转述脚注大意；正文 Solution 仍为英文。）</span>

（解答在本页止于 part (a) 的论断与期望换序之说明；$i=s$ 情形及 part (b)、(c) 的后续论证在下一页 PDF p410 继续。）
<!-- ===== PDF p410 ===== -->

<span style="color:#7f8c8d;">§7.4 习题区（Problems，习题 28–35）——吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）中部续页。本页页首无新节/新标题，是**上一页（书页 p400）Problem 34 英文 Solution 的第（a）部分收尾的延续**，随后本页继续该解答的第（b）、（c）部分。本页为带 `*` 星号题（Problem 34），其题干与英文 Solution 照规范**保留英文原文**（仅标签可注中文）。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本页为习题区（Problems），照规范保留英文原文。第（a）部分尾部推导的中间等式在 OCR 中支离破碎（如 `Ps p si +`、多处 `S,`/`#` 残片、`L PkiPk`/`L PkPki`、`1n`/`t;`、`2:::; : 1` 等零散符号），下方已按「常返状态前后两次访问之间的访问次数」及总概率定理的标准语义整合成规范 LaTeX，并按已知关系 $p_s = 1$ 校准了合并为全和 $\sum_{k=1}^{m} p_k P_{ki}$ 的一步；未臆造原文未含的任何数值。</span>

---

上一题解答（续，**Problem 34** ——平衡方程与平均循环时间 Balance equations and mean recurrence times，带 `*` 的英文 Solution）：

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（解答，续）**</span>

When $i = s$, the events

```math
\{X_1 \neq s,\, \ldots,\, X_{n-1} \neq s,\, X_n = s\},
```

for the different values of $n$, form a partition (划分) of the sample space (样本空间), because they correspond to the different possibilities for the time of the next visit to state $s$. Thus,

```math
\sum_{n=1}^{\infty} P(X_1 \neq s,\, \ldots,\, X_{n-1} \neq s,\, X_n = s) \;=\; 1 \;=\; p_s,
```

which completes the verification of our assertion.

We next use the total probability theorem (全概率定理) to write for $n \geq 2$,

```math
P(X_1 \neq s,\, \ldots,\, X_{n-1} \neq s,\, X_n = i)
\;=\; \sum_{k \neq s} P(X_1 \neq s,\, \ldots,\, X_{n-2} \neq s,\, X_{n-1} = k)\, P_{ki}.
```

We thus obtain

```math
p_i
\;=\; \sum_{n=1}^{\infty} P(X_1 \neq s,\, \ldots,\, X_{n-1} \neq s,\, X_n = i)
\;=\; P_{si} + \sum_{n=2}^{\infty} P(X_1 \neq s,\, \ldots,\, X_{n-1} \neq s,\, X_n = i)
```

```math
\;=\; P_{si} + \sum_{n=2}^{\infty}\sum_{k \neq s} P(X_1 \neq s,\, \ldots,\, X_{n-2} \neq s,\, X_{n-1} = k)\, P_{ki}
```

```math
\;=\; P_{si} + \sum_{k \neq s} P_{ki}\, \sum_{n=2}^{\infty} P(X_1 \neq s,\, \ldots,\, X_{n-2} \neq s,\, X_{n-1} = k)
```

```math
\;=\; p_s\, P_{si} + \sum_{k \neq s} p_k\, P_{ki}
\;=\; \sum_{k=1}^{m} p_k\, P_{ki}.
```

**(b)** Dividing both sides of the relation established in part (a) by $t_s$, we obtain

```math
\pi_i \;=\; \sum_{k=1}^{m} \pi_k\, P_{ki},
```

where $\pi_i = p_i / t_s$. Thus, the $\pi_i$ solve the balance equations (平衡方程). Furthermore, the $\pi_i$ are nonnegative, and we clearly have $\sum_{i=1}^{m} p_i = t_s$ or $\sum_{i=1}^{m} \pi_i = 1$. Hence, $(\pi_1, \ldots, \pi_m)$ is a probability distribution (概率分布).

**(c)** Consider a probability distribution $(\pi_1, \ldots, \pi_m)$ that satisfies the balance equations. Fix a recurrent state (常返状态) $s$, let $t_s$ be the mean recurrence time (平均循环时间) of $s$, and let $t_i$ be the mean……

> <span style="color:#7f8c8d;">本页在此处结束。第（c）部分（证明 $\pi_s t_s = 1$）及第（d）部分（唯一性）在下一页（PDF p411，书页 p402）延续。</span>
<!-- ===== PDF p411 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

<span style="color:#c0392b;">**§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）· 习题区（续）**</span>

> <span style="color:#7f8c8d;">本页（书页 402，§7.4 习题区）页首为上一页 Problem 34 解答（用平衡方程证明平均循环时间关系、验证平衡方程解的唯一性）的收尾段——上面几行 OCR 被切成碎片（如 `1+ t:`、`P Sj tj`、`j# s`、`L ti` 等只余零散符号），下方已按真实语义整合成规范的方程组；随后本页进入 **Problem 35**（本文件页首为跨页续接，故带「（续）」）。本页习题为带 `*` 题，其题干与英文 Solution（仅标签可加中文）按规范保留英文原题。</span>

---

上一题解答（续，Problem 34 的英文 Solution 收尾：证明 $\pi_s t_s = 1$，其中 $t_s$ 为状态 $s$ 的平均循环时间 mean recurrence time）：

“……let $t_i$ be the mean first passage time from $i$ to $s$ (first passage time). We prove that $\pi_s t_s = 1$. Indeed, we have

```math
t_s = 1 + \sum_{j\ne s} p_{sj}\, t_j ,\qquad
t_i = 1 + \sum_{j\ne s} p_{ij}\, t_j ,\ \ \text{for} \ i \ne s .
```

Multiplying these equations by $\pi_s$ and $\pi_i$, respectively, and adding, we obtain

```math
\pi_s\, t_s + \sum_{i\ne s} \pi_i\, t_i
= \sum_{i=1}^{m} \pi_i + \sum_{i=1}^{m} \pi_i \sum_{j\ne s} p_{ij}\, t_j .
```

Using the balance equations (balance equations), that is, $\sum_i \pi_i p_{ij} = \pi_j$, the right-hand side becomes

```math
1 + \sum_{j\ne s} \pi_j\, t_j .
```

Combining the last two equations, we obtain $\pi_s\, t_s = 1$.

If a probability distribution $(\pi_1, \ldots, \pi_m)$ satisfies the balance equations, then, if the initial state $X_0$ is chosen according to this distribution, all subsequent states $X_n$ have the same distribution. If we start from a transient (transient) state $i$, the probability of being in a transient state at time $n$ tends to $0$ as $n\to\infty$. This implies that $\pi_i = 0$.

(d) Part (b) shows that there exists at least one probability distribution satisfying the balance equations, and part (c) shows that there is at most one such distribution.”

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 顶部这一段（$\pi_s t_s = 1$ 的平衡方程证明）中，方程组诸行的 OCR 碎裂严重（如 `1+ t:`、`t:P Sj tj`、`j# s`、`L ti`、`L Pij tj`、`j'i-s` 等仅余散碎符号），其中「右边等于」一行的中间求和式（$\sum_{j\ne s} \pi_j t_j$，由 $\sum_i \pi_i\sum_{j\ne s} p_{ij} t_j$ 经平衡方程化简而来）尤其残损；上正文已按首达时间 / 平衡方程证明的标准语义忠实整合，未臆造原文未含的任何数值。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 35.\* The strong law of large numbers for Markov chains. （马尔可夫链的强大数定律。）**</span>

Consider a finite-state Markov chain in which all states belong to a single recurrent class which is aperiodic. For a fixed state $s$, let $Y_k$ be the time of the $k$th visit to state $s$. Let also $V_n$ be the number of visits to state $s$ during the first $n$ transitions.

(a) Show that $Y_k / k$ converges with probability 1 to the mean recurrence time $t_s$ of state $s$.

(b) Show that $V_n / n$ converges with probability 1 to $1 / t_s$.

(c) Can you relate the limit of $V_n / n$ to the steady-state probability of state $s$?

---

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（解答）. \(问题 35 为带 \* 题，其英文 Solution 保留原文。\)**</span>

(a) Let us fix an initial state $i$, not necessarily the same as $s$. Thus, the random variables $Y_{k+1} - Y_k$, for $k \ge 1$, correspond to the time between successive visits to state $s$. Because of the Markov property (the past is independent of the future, given the present), the process "starts fresh" at each revisit to state $s$ and, therefore, the random variables $Y_{k+1} - Y_k$ are independent and identically distributed, with mean equal to the mean recurrence time $t_s$. Using the strong law of large numbers, we obtain

```math
\frac{Y_k}{k} \;\xrightarrow[\text{w.p. 1}]{}\; t_s , \qquad \text{with probability 1}.
```

本页在此处结束，上述证明与第（b）、（c）部分在下一页（PDF p412）延续。
<!-- ===== PDF p412 ===== -->

> <span style="color:#7f8c8d;">§7.4 吸收概率与吸收期望时间的习题区（书页 403，页眉 Chap. 7）。本页承接上一页（书页 402）的 **Problem 35\***（马尔可夫链的强数定律，The strong law of large numbers for Markov chains）英文 Solution，先续解其第 (b)、(c) 两问及其后的一段 Note（注意），随后页中转入 **§7.5 Continuous-Time Markov Chains** 小节，并给出 **Problem 36** 题干的开头。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页强数定律（S.L.L.N.）证明的两处公式被 OCR 打成碎片：如 `Yk  n < Yk+!` 实为 $Y_k \le n < Y_{k+1}$、`t;` 表示平均重现时间 $\tau_s$、极限式被拆成 `lim __ = lim + . lim __ = lim .!:.. = .!..` 等残留片段、`E[Yn] = 1 . 2'n = 21` 实为 $E[Y_n] = (1/n)\cdot n = 1$。现按原书页 403 权威文本重建下述公式，全部数值均由前文 $Y_k/k \to \tau_s$ 及概率计算 $P(X<1/n)=1/n$ 反推核验，未臆造任何原文未出现的数字。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 35\*（续）——马尔可夫链的强数定律（The strong law of large numbers for Markov chains）**</span>

<span style="color:#00838f;">**[solution] Solution（解答）**</span>

(b) Let us fix an element of the sample space (a trajectory of the Markov chain). Let $Y_k$ and $V_n$ be the values of the random variables $Y_k$ and $V_n$, respectively. Furthermore, let us assume that the sequence $Y_k/k$ converges to $\tau_s$; according to the result of part (a), the set of trajectories with this property has probability 1. Let us consider some $n$ between the time of the $k$th visit to state $s$ and the time just before the next visit to that state:

```math
Y_k \;\le\; n \;<\; Y_{k+1}.
```

For every $n$ in this range, we have $V_n = k$, and also

```math
\frac{1}{Y_{k+1}} \;<\; \frac{1}{n} \;\le\; \frac{1}{Y_k},
```

from which we obtain

```math
\frac{k}{Y_{k+1}} \;<\; \frac{V_n}{n} \;\le\; \frac{k}{Y_k}.
```

Note that

```math
\lim_{k\to\infty}\frac{k}{Y_{k+1}}
= \lim_{k\to\infty}\frac{k}{k+1}\cdot\lim_{k\to\infty}\frac{k+1}{Y_{k+1}}
= \lim_{k\to\infty}\frac{k}{Y_k}
= \frac{1}{\tau_s}.
```

If we now let $n$ go to infinity, the corresponding values of $k$, chosen to satisfy $Y_k \le n < Y_{k+1}$, also go to infinity. Therefore, the sequence $V_n/n$ is between two sequences both of which converge to $1/\tau_s$, which implies that the sequence $V_n/n$ converges to $1/\tau_s$ as well. Since this happens for every trajectory in a set of trajectories that has probability equal to 1, we conclude that $V_n/n$ converges to $1/\tau_s$, with probability 1.

(c) We have $1/\tau_s = \pi_s$, as established in Problem 35. This implies the intuitive result that $V_n/n$ converges to $\pi_s$, with probability 1.

Note: It is tempting to try to establish the convergence of $V_n/n$ to $\pi_s$ by combining the facts that $V_n/n$ converges [part (b)] together with the fact that $E[V_n]/n$ converges to $\pi_s$ (cf. the long-term expected frequency interpretation of steady-state probabilities in Section 7.3). However, this line of reasoning is not valid. This is because it is generally possible for a sequence $Y_n$ of random variables to converge with probability 1 to a constant, while the expected values converge to a different constant. An example is the following. Let $X$ be uniformly distributed in the unit interval $[0,1]$, let

```math
Y_n =
\begin{cases}
0, & \text{if } X \ge 1/n,\\
n, & \text{if } X < 1/n.
\end{cases}
```

As long as $X$ is nonzero (which happens with probability 1), the sequence $Y_n$ converges to zero. On the other hand, it can be seen that

```math
E[Y_n] = P(X < 1/n)\, E[Y_n \mid X < 1/n] = \tfrac{1}{n}\cdot n = 1,
```

for all $n$.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把它补全成一个自足的模型。取 $X$ 为 $(0,1)$ 上的 uniform（均匀）变量，令 $Y_n=n$ 当 $X<1/n$、否则 $Y_n=0$。为什么要这个 $X$？因为需要 $P(X<1/n)=1/n$ 恰好成立，而这正是均匀分布的尾概率。于是 $E[Y_n]=P(X<1/n)\cdot n=(1/n)\cdot n=1$ 对所有 $n$ 恒成立，一分不变。
>
> 另一边，逐条轨道的命运完全相反。对每个满足 $X(\omega)>0$ 的样本点，取 $n>1/X(\omega)$，此后 $Y_n(\omega)=0$ 永远。$X>0$ almost surely（几乎必然）成立，所以 $Y_n\to0$ almost surely（几乎必然），而且还顺带得到 $P(\lvert Y_n\rvert>\epsilon)=P(X<1/n)=1/n\to0$，即 in probability（依概率）收敛到 $0$。两个「几乎」都站在 $0$ 这边，只有期望站在 $1$ 那边：$E[Y_n]\to1\ne0$。
>
> 这里的层级关系必须说准。收敛强度有一条链：almost sure（几乎必然）$\Rightarrow$ in probability（依概率）$\Rightarrow$ in distribution（依分布），箭头单向，反例分别是「$Y_n$ 按类型轮转的移动鼓包」与「分布相同但变量不靠近」。而 $L^{1}$ 收敛（均值收敛，即 $E\lvert Y_n-Y\rvert\to0$）与这条链不互相蕴含：$L^1$ 收敛蕴含依概率收敛，但不蕴含几乎必然收敛；几乎必然收敛不蕴含 $L^1$ 收敛，本例就是后者。本例的正确读法是：$Y_n$ 在 almost surely（几乎必然）与 in probability（依概率）两种意义下都收敛到 $0$，唯独 $L^{1}$ 收敛失败，因为 $E\lvert Y_n-0\rvert=1$ 恒等于 $1$。所以说「期望收敛与依概率收敛之间有鸿沟」是把对比项写反了——依概率收敛恰恰成立，失败的是均值收敛；这个区分决定了你能不能用期望去论证概率，答案是不能，方向是反的。
>
> 为什么失败？一句话：质量以宽度 $1/n$、高度 $n$ 的方式堆成一个面积恒为 $1$ 的 spike（尖峰），尖峰越来越窄、越来越高。窄到任何固定样本点终将被它甩下（这是 a.s. 收敛），高到它贡献的积分始终是 $1$（这是 $L^1$ 不收敛）。这就是「质量逃逸到高值」的标准图景，测度论课上通常叫 moving bump（移动鼓包）或 typewriter sequence（打字机序列）的连续版。
>
> Fatou lemma（法图引理）在这里不是可选项而是唯一的合法通道：$E[\liminf Y_n]\le\liminf E[Y_n]$，代入得 $0\le1$，不等式严格成立。Fatou 从来只给「小于等于」，严格不等正说明有质量从下界手里溜走了。要把它变成等号，需要再加一个条件：monotone convergence（单调收敛）要求 $Y_n$ 单调，本题不单调；dominated convergence（控制收敛）要求存在可积的 $g$ 使 $\lvert Y_n\rvert\le g$，本题 $Y_n$ 无界，取不到这样的 $g$；更弱的一档是 uniform integrability（一致可积），即 $\sup_nE[Y_n;\ Y_n>K]\to0$ 当 $K\to\infty$，而本题取任意 $K$ 后都能找到 $n>K$ 使该项等于 $1$，一致可积彻底破功。Vitali 收敛定理说：依概率收敛加上一致可积，才等价于 $L^1$ 收敛（几乎必然收敛更强，当然也够）。这道题的全部内容就是「缺的那个条件具体是哪一个」。Fatou 的结果出自 Pierre Fatou 1906 年的博士论文《Séries trigonométriques et séries de Taylor》（Acta Mathematica 第 30 卷），与他研究 Poisson 积分边界行为的工作同源。
>
> 这段反例在 Problem 35 里的位置不是装饰。正文刚刚用模进（$Y_k\le n<Y_{k+1}$，这里的 $Y_k$ 是第 $k$ 次访问 $s$ 的时刻，与反例里的 $Y_n$ 重名，读时注意区分）夹出 $k/Y_{k+1}<V_n/n\le k/Y_k$，两端都由强大数定律控制，于是 $V_n/n$ 被夹到 $1/\tau_s$。整条路径只用逐轨道的几乎必然收敛，一次也没碰期望。然后课本提醒：有人会想反过来走——既然已经知道 $E[V_n]/n\to\pi_s$（长期频率解释），又知道 $V_n/n$ 收敛，就想用期望去定极限。这个反例正是说明这一步非法：期望的极限与逐点的极限可以毫不相干。$E[V_n]/n$ 收敛这件事本身没错，错在把它当成 $V_n/n$ 的极限值来源。
>
> 工程上的译法：任何「平均性能指标收敛」都不能代替「单个样本轨迹收敛」，前者是 ensemble average（系综平均），后者是 time average（时间平均）。遍历定理之所以值钱，正是因为它在特定条件下把两者接起来；而这里用到的接法不是期望，是夹逼加数定律。把这条纪律记住，就不会在仿真里拿「跑了一千次取平均」去冒充「一条长轨迹的极限」。

---

<span style="color:#c0392b;">**§7.5　连续时间马尔可夫链（Continuous-Time Markov Chains）**</span>

> <span style="color:#7f8c8d;">任务的核对点提示第 8 章 §8.1 例 8.1 可能进入本页——经反查，本页书页号为 403（页眉 Chap. 7），仍在第 7 章习题区，未进入第 8 章；例号从 8.1 起应出现在后续更晚页份。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 36．**</span>

A facility of $m$ identical machines is sharing a single repairperson. The time to repair a failed machine is exponentially distributed with mean $1/\lambda$. A machine…

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页止于 Problem 36 题干中途（"A machine…" 后即截断）；题干续接于下一页（PDF p413），且下一页给出其后的文字 "…once operational, fails after a time that is exponentially distributed with mean $1/\mu$"。此处修复时长的均值符号在源 OCR 中被压成 `1/>.` 残片，依下一页配套的机器运转损坏时长 $1/\mu$ 反推，重建为 $1/\lambda$（不臆造数字，仅还原被 OCR 吞掉的 $1/\lambda$）。</span>
<!-- ===== PDF p413 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

> <span style="color:#7f8c8d;">页眉 Chap. 7 · 书目页 404 · 属 §7.5 Continuous-Time Markov Chains（连续时间马尔可夫链）习题区收尾，页首为上一页 Problem 36 的续接。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 36（续）**</span>

… once operational, fails after a time that is exponentially distributed with mean $1/\mu$.
All failure and repair times are independent.
(a) Find the steady-state probability that there is no operational machine.
(b) Find the expected number of operational machines, in steady-state.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> continuous-time Markov chain（连续时间马尔可夫链，CTMC）的建模纪律只有一条：方程的对象是「下一次跳变发生在哪个方向、以多快」，而不是时间本身。本题把状态取成 failed（失败）机器的台数 $i=0,1,\ldots,m$。每台运行中的机器以速率 $\mu$ 熔断（其寿命期望为 $1/\mu$），修理工只有一名，以速率 $\lambda$ 修好一台（修复时间期望为 $1/\lambda$）；所有时间相互独立。
>
> 于是状态 $i$ 下有两个独立的 exponential（指数）时钟在赛跑：向上跳（又坏一台）的总速率是 $(m-i)\mu$——注意是运行台数 $m-i$ 乘单台失效率；向下跳（修好一台）的速率是 $\lambda$ 当 $i>0$、否则不跳。两个独立指数取最小值仍是指数，参数相加，所以状态 $i$ 的 exit rate（离出速率）为 $v_i=(m-i)\mu+\lambda\cdot\mathbf{1}_{\{i>0\}}$，跳变方向的条件概率按各自速率占比分。
>
> 这里有一个极常见的下标笔误，值得单独指出来：若把状态定义成「停机台数 $i$」，则运行台数是 $m-i$，failure rate（总失效率）必须是 $(m-i)\mu$，写成 $i\mu$ 就把两个量对调了；而如果中途又把 $i$ 理解成「运行台数」，同一符号就被赋了两个含义，套出来的平衡方程与下标自然整体错位。正确写法是：向上速率 $(m-i)\mu$、向下速率 $\lambda$，状态 $i$ 的平衡方程为 $\pi_i[(m-i)\mu+\lambda]=\pi_{i-1}(m-i+1)\mu+\pi_{i+1}\lambda$（$0<i<m$），两端边界为 $\pi_0m\mu=\pi_1\lambda$ 与 $\pi_m\lambda=\pi_{m-1}\mu$。检查边界的办法很简单：把 $i=0$ 代入通式并删掉不存在的 $\pi_{-1}$ 项，剩下的正是第一式。
>
> 这条链是 birth-death（生灭）结构，而有限生灭链一定 reversible（可逆），于是 detailed balance（细致平衡）逐对成立：$\pi_i(m-i)\mu=\pi_{i+1}\lambda$，即 $\pi_{i+1}=\pi_i(m-i)\mu/\lambda$。递推到底得 $\pi_i=\pi_0\frac{m!}{(m-i)!}\left(\frac{\mu}{\lambda}\right)^{i}$，$\pi_0$ 由归一化 $\sum_{i=0}^{m}\pi_i=1$ 定出。注意这里出现的比值是 $\mu/\lambda$（故障率除以修复率），与排队论惯用的 $\rho=\lambda/\mu$ 方向相反——这个模型里 $\mu/\lambda$ 越大，停机越重，别把两个比值搞混。第 (a) 问「没有任何运行机器」就是全停，答案 $\pi_m$；第 (b) 问期望运行台数等于 $\sum_{i=0}^{m}(m-i)\pi_i=m-\sum_i i\pi_i$，两者都从同一个稳态分布直接取出，不需要另立方程。
>
> 名字要叫准。这套结构在文献里的标准名是 machine repairman model（机器修理模型），也叫 finite-source queue（有限源排队）：顾客（机器）总数固定为 $m$，只有处于「坏掉」状态的那部分才在系统里排队，所以到达率随系统内人数增加而线性下降。它跟 M/M/m（$m$ 个并列服务员）完全不同：这里服务员始终是 $1$ 个，$m$ 是顾客数。与它同族但容易混淆的是 Engset 模型（T. O. Engset，1918）：有限源、无等待位、超员直接阻塞；本题有排队（多台机器可以同时等修），属于 finite-source（有限源）的 delay system（延迟系统）。Erlang（1917）的 Erlang-B 则是无限源、无等待位。三者的区别全在「源是否有限」与「有没有等待位」这两个开关上。
>
> reliability（可靠性）方向的读法值得补一句。取 $m=1$，模型退化成单台机器在两态间来回切换，$\pi_0=\frac{1}{1+\mu/\lambda}$，这就是最基本的 availability（可用度）公式：可用时间占比等于平均无故障时间除以（平均无故障时间加平均修复时间）。$m>1$ 时没有这种单行闭式，必须落到求和，这是「共享一个修理工」带来的耦合——机器越多，修理工越忙，每台的等待修复时间越长，可用度随 $m$ 单调下降。这条单调性本身就是本题最有工程价值的定性结论。
>
> 假设一旦松动，马尔可夫性就断在哪，也必须说清。若寿命不是指数分布，比如是 deterministic（确定性）的「运行满 $T$ 小时必坏」，那么「还剩多久会坏」取决于这台机器已经运行了多久，状态必须扩充为每台机器的 age（年龄），状态空间从 $m+1$ 个计数态炸成连续统，$X(t)$ 不再是马尔可夫链。若修理工能同时修 $c$ 台，向下速率变成 $\min(i,c)\lambda$，公式整体换一套（有限源 M/M/c）。若修复时间与故障时间相关，连乘积形式都不再有。指数分布的 memorylessness（无记忆性）在这里不是「简化假设」，而是「把每台机器的剩余时间压缩成一个整数计数」的唯一凭据。
>
> 最后给一句跨课程的坐标：连续时间链的稳态由 generator matrix（生成矩阵）$Q$ 满足 $\pi Q=0$ 加归一化刻画；本题的 $Q$ 是 tridiagonal（三对角）的，所以才有逐对 detailed balance（细致平衡）可写。这也解释了为什么把转移速率取成常数就能把连续时间链的稳态方程直接降成离散链的平衡方程：当 $v_i$ 处处相等时，约掉公因子后 $Q$ 与 $P-I$ 同型。$I+Q/\nu$ 对足够大的 $\nu$ 是合法的 transition matrix（转移矩阵），这叫 uniformization（一致化），是把连续时间问题搬回离散时间的标准桥。

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 37（空格出租车、Poisson 到达与顾客等待）**</span>

Empty taxis pass by a street corner at a Poisson rate of two per minute
and pick up a passenger if one is waiting there. Passengers arrive at the street corner
at a Poisson rate of one per minute and wait for a taxi only if there are less than four
persons waiting; otherwise they leave and never return. Penelope arrives at the street
corner at a given time. Find her expected waiting time, given that she joins the queue.
Assume that the process is in steady-state.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把模型对齐到标准记号。出租车以速率 $\mu=2$（每分钟）按 Poisson process（泊松过程）到达，乘客以速率 $\lambda=1$ 到达；等待人数上限为 $4$（「少于四人等待才加入」，加入后最多四人）。把「等待人数」取为状态 $i\in\{0,1,2,3,4\}$，就得到一个 birth-death（生灭）chain：上行速率 $\lambda$（只要 $i<4$），下行速率 $\mu$（只要 $i>0$），因为一辆出租车到达就带走一位。这就是 M/M/1/4：单服务员、容量 $4$，服务时间等于「等下一辆 taxi 的时间」，指数、均值 $1/2$ 分钟。
>
> 稳态分布可以一行写出。以 $\rho=\lambda/\mu=1/2$，有限容量的 birth-death（生灭）分布为 $\pi_i=\pi_0\rho^{i}$，归一化给出 $\sum_{i=0}^{4}\rho^{i}=(1-\rho^{5})/(1-\rho)=31/16$，故 $\pi_i=\frac{16}{31}\left(\frac12\right)^{i}$，从 $\pi_0=16/31$ 单调降到 $\pi_4=1/31$。加入概率为 $P(i<4)=1-\pi_4=30/31$。
>
> 关键一步是把「她加入」翻译成「她看到 $i<4$ 人」。这一步依赖 PASTA（Poisson arrivals see time averages，到达见时间平均）：Poisson 到达的乘客看到的状态分布就是时间平均分布 $\pi$，不需要额外修正。若乘客到达不是 Poisson 而是等间隔，看到的就是「事件平均」而非「时间平均」，答案会变——这是本题题干特意写明 Poisson 的原因，也是排队论里最常被悄悄用错的一条前提。
>
> 给定她看到 $i$ 人，等待时间是多少？她前面有 $i$ 人，每人各占一辆车，加上她自己，共需 $i+1$ 辆车；每两次相隔 Exp(2)，由 memorylessness（无记忆性），从她加入那一刻到第一辆车之间剩余的时间仍服从 Exp(2)。所以等待等于 $i+1$ 个独立 Exp(2) 之和，期望 $(i+1)/2$。条件化求和得 $E[W\mid\text{joins}]=\dfrac{\sum_{i=0}^{3}\pi_i(i+1)/2}{\sum_{i=0}^{3}\pi_i}$，其中分母是「她确实加入」的概率权重之和。代入 $\pi_i=\frac{16}{31}2^{-i}$：分子为 $\frac{16}{31}\cdot\frac12\cdot(1+1+0.75+0.5)=\frac{26}{31}$，分母为 $\frac{30}{31}$，比值得 $13/15$ 分钟，约 $52$ 秒。
>
> 这个结果可以用 Little's law（利特尔法则）独立验算，这是检验排队答案最快的手段。稳态平均等待人数 $L=\sum_{i=0}^{4}i\pi_i=\frac{16}{31}(0.5+0.5+0.375+0.25)=\frac{26}{31}$；有效到达率 $\lambda_{\text{eff}}=\lambda\cdot P(i<4)=\frac{30}{31}$；两式相除得 $W=L/\lambda_{\text{eff}}=13/15$，与上面的条件期望完全一致。两条路径一条走时间、一条走人数，能对上说明 $\pi$、PASTA（到达见时间平均）、无记忆三处都没写错。
>
> 三处常见误解要顺手清掉。第一处是比喻用错了场景：把等待说成「两个随机时间的竞争」只在「两个过程赛跑、谁先到算谁」时才成立，比如顾客与不耐烦离开的阈值赛跑。本题的等待不是竞争，而是串联：$i+1$ 段独立指数服务时间首尾相接，期望线性相加。真正让计算成立的是 memorylessness（无记忆性）——剩余服务时间与全新服务时间同分布，所以每一段都可以重新起算，不需要知道她到达时那辆车已经「等了多久」。把机制说成竞争，会让人误以为要处理「最小值分布」，方向就偏了。
>
> 第二处是稳定性条件。说「若服务强度 $\ge1$，队列在稳态上根本不收敛、期望等待时间发散」，对无限容量的 M/M/1 是对的（$\rho\ge1$ 时无稳态），对本题这个容量为 $4$ 的链却是错的：状态空间只有 $5$ 个、闭且不可约，任何有限状态不可约链都有唯一稳态分布，与 $\rho$ 取多大无关；$\rho$ 变大只会让 $\pi_4$ 变大、更多人 balking（拒绝加入），等待时间反而被容量顶住。真正会发散的是「容量无限加 $\rho\ge1$」，那才是没有稳态的场合。把有限容量与无限容量混在一起谈稳定性，是排队论里最常见的误判。
>
> 第三处是术语统一。本文一律写成 queue（队列）、balking（拒绝加入）、service rate（服务速率），便于全文检索；「有限容量队列」不要写成别的同音字。
>
> 家族定位：本题属于有等待位、有容量上限的损失-延迟混合系统。Erlang-B（1917）是 M/M/c/c，即「有 $c$ 个服务员、没有等待位、满了就丢」，属于纯 loss system（损失系统）；本题是 M/M/1/K（$K=4$），有队列也有上限，超限才丢。两者的稳态都是截断的 birth-death（生灭）分布，差别只在状态数上限的取法。真正把「系统大了会怎样」说清楚的是 machine repairman model（机器修理模型）（即 $m$ 台机器配一台修理工），两者状态结构同型，只是到达率一个恒定、一个随人数线性下降。

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 38（多个用户共享计算机系统的马尔可夫链建模）**</span>

There are $m$ users who share a computer system. Each user alternates between "thinking" intervals whose durations are independent exponentially distributed with parameter $\lambda$, and an "active" mode that starts by submitting a service request. The server can only serve one request at a time, and will serve a request completely before serving other requests. The service times of different requests are independent exponentially distributed random variables with parameter $\mu$, and also independent of the thinking times of the users. Construct a Markov chain model and derive the steady-state distribution of the number of pending requests, including the one presently served, if any.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题的建模动作叫 aggregation（聚合）：每个用户自己是一条两阶段的 continuous-time Markov chain（连续时间马尔可夫链，CTMC），在 thinking（思考，速率 $\lambda$）与 active（活跃，速率 $\mu$）之间来回；把 $m$ 条独立的微观链合并，状态只保留「系统内活跃用户数」$i$。合法性的依据是 strong lumpability（强可合并性）：同一个宏观计数下的所有微观状态，其下一跳的总速率与「跳到哪个宏观态」的概率完全一致——因为 $i$ 个活跃用户彼此对称、各阶段全是指数，对称性把差别抹平了。这就是 $2^{m}$ 个 phase assignment（相位分配）被压成 $m+1$ 个整数 $i$ 的全部理由。
>
> 状态 $i$ 的速率要数清谁在动。$m-i$ 个用户在 thinking（思考），每个以 $\lambda$ 提交请求，所以上行速率是 $(m-i)\lambda$；server（服务器）只有一台，正在服务的那一个请求以 $\mu$ 完成，一旦完成该用户立刻回到 thinking，所以下行速率恒为 $\mu$（只要 $i>0$，且被服务者必在 $i$ 个活跃用户之中）。$i$ 中包含「正在服务」的那一个，其余 $i-1$ 个在排对。容易混淆的说法是「服务速率 $\mu$，服务中的那台」——把服务器当成了用户；正确的说法是：服务器容量为 $1$、服务速率 $\mu$，与活跃用户数无关，而活跃用户数是状态。
>
> 平衡方程就是这两条速率拼起来的 birth-death（生灭）方程：$\pi_i[(m-i)\lambda+\mu]=\pi_{i-1}(m-i+1)\lambda+\pi_{i+1}\mu$，$i=0,\ldots,m$，两端各自退化成一项。这条链与机器修理模型完全同型——把「停机台数」换成「活跃用户数」，故障率与修复率互换位置，矩阵一模一样。解用 detailed balance（细致平衡）逐对递推：$\pi_{i+1}=\pi_i\frac{(m-i)\lambda}{\mu}=\pi_i(m-i)\rho$，其中 $\rho=\lambda/\mu$，于是 $\pi_i=\pi_0\frac{m!}{(m-i)!}\rho^{i}$，而 $\pi_0$ 由 $\sum_{i=0}^{m}\pi_i=1$ 的归一化定出，即 $\pi_0=\left[\sum_{i=0}^{m}\frac{m!}{(m-i)!}\rho^{i}\right]^{-1}$。
>
> 这里有个高频误判，正好借本题澄清：很多人凭直觉写 $\pi_i=\binom{m}{i}p^{i}(1-p)^{m-i}$，也就是 binomial（二项）分布。二项分布对应的是 M/M/$\infty$——每个用户独占一台服务器，谁处于活跃阶段立刻被服务，彼此不排对。单服务器一旦引入排对，「谁在等」就与计数 $i$ 相关（只有 $i-1$ 个在等、而 $i$ 个都算在系统内），分布立刻从 binomial（二项）变成上面的 factorial（阶乘）型。两者在 $m$ 大、$\rho$ 小时形状接近，但公式不同，别在推导里混用。
>
> 两个自洽校验，用来确认解没写错。其一，throughput（吞吐）有两条算法：按服务端算 $\theta=\mu(1-\pi_0)$，按用户端算 $\theta=\lambda\sum_i(m-i)\pi_i$（单位时间提交并被完成的请求数），平衡方程保证两者相等，动手验一遍比值是否为 $1$。其二，当 $m$ 增大而 $\rho$ 固定时，$\pi$ 向大 $i$ 一侧倾斜，$\pi_0$ 指数级变小，期望活跃数趋向 $m$ 而吞吐饱和在 $\mu$——这解释了为什么「加用户」在负载高时几乎不提吞吐，只会加延迟。饱和点的位置由乘积 $m\rho$ 决定：$m\rho\ll1$ 时服务器远远快于用户，$\pi$ 集中在 $i=0$ 附近；$m\rho\gg1$ 时请求排队，系统进入以服务器为瓶颈的区间。
>
> 家族定位上有两个易混的邻居要分清。machine repairman model（机器修理模型）与本题完全同构，可以等同；Engset 模型（T. O. Engset，1918）虽然也是有限源，但它是没有等待位的纯 loss system（损失系统），请求撞上忙碌直接被丢弃，不会排对。本题有排对，所以属于 delay system（延迟系统）。Engset 只能算同胞，不能算别名。
>
> 失效条件要说全。除了「服务器可并发处理」（此时下行速率变成 $\min(i,c)\mu$）与「思考时间非指数」（此时须记各自已流逝的时间）这两条，还有最常见也最隐蔽的一种：用户异构。只要不同用户的 $\lambda_i$、$\mu_i$ 不同，即便全是指数、服务器也只有一台，$m+1$ 个计数态就不再充分——因为「活跃的是快的那个还是慢的那个」直接改变下一跳速率，而这信息被计数丢掉了。此时必须记录完整的相位向量，聚合失效。建模时的判据是：被合并的微观状态必须对未来完全等价，一旦参数破坏了对称性，聚合就得重新论证。
>
> 跨课程的坐标：本题是 closed queueing network（闭排队网络）最简单的一例——只有两个节点，总人口 $m$ 固定；thinking（思考）节点是 infinite-server（无限服务器，思考阶段永远不等），服务节点是 single-server（单服务器）加队列。Jackson 定理（James R. Jackson，1957 与 1963）说这类网络的稳态具有 product form（乘积形式），本题的 $\pi_i$ 就是乘积形式在只有两个节点、人口固定时的投影。工程上讲，它给出的是「吞吐-延迟曲线」的解析版本：加 $m$ 与加 $\mu$ 的效果不可线性外推，饱和点的位置由 $m\rho$ 决定。

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 39（转移速率等值情形）**</span>

$\ast$ Consider a continuous-time Markov chain in which the transition rates $v_i$ are the same for all $i$. Assume that the process has a single recurrent class.
(a) Explain why the sequence $Y_n$ of transition times form a Poisson process.
(b) Show that the steady-state probabilities of the Markov chain $X(t)$ are the same as the steady-state probabilities of the embedded Markov chain $X_n$.

<span style="color:#2471a3;">**[solution]** **Solution.**</span> (a) Denote by $v$ the common value of the transition rates $v_i$. The sequence $\{Y_n\}$ is a sequence of independent exponentially distributed time intervals with parameter $v$. Therefore they can be associated with the arrival times of a Poisson process with rate $v$.

(b) The balance and normalization equations for the continuous-time chain are

```math
\pi_j \sum_{k\neq j} q_{jk} = \sum_{k\neq j} \pi_k q_{kj}, \quad j = 1, \ldots, m,
```

```math
\sum_{k=1}^{m} \pi_k = 1.
```

By using the relation $q_{jk} = v\,p_{jk}$, and by canceling the common factor $v$, these equations are written as

```math
\pi_j \sum_{k\neq j} p_{jk} = \sum_{k\neq j} \pi_k p_{kj}, \quad j = 1, \ldots, m,
```

```math
\sum_{k=1}^{m} \pi_k = 1,
```

which are precisely the balance and normalization equations of the embedded Markov chain $X_n$, proving the claim. （解答末尾于本页页脚被 OCR 截断，后续续接于下一页。）

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** Problem 39（书页 p405–406，PDF p413–414；解答跨页，末句在 PDF p413 页脚被 OCR 截断、续接于 p414）。设 continuous-time Markov chain（连续时间马尔可夫链）的 transition rate（转移速率）$v_i$ 全等、记作 $v$，且只有单一 recurrent class（常返类）。要证两件事：(a) 跳变时刻 $Y_n$ 构成 Poisson process（泊松过程）；(b) 该链与其 embedded Markov chain（嵌入链）有相同的 steady-state probability（稳态概率）。
>
> **(a)：速率与状态无关，等于等待与历史无关。** 状态 $i$ 的逗留时长服从参数 $v_i$ 的 exponential distribution（指数分布）。$v_i\equiv v$ 时每次逗留都是 $\mathrm{Exp}(v)$ 且相互独立，跳变间隔因而 iid（独立同分布）、增量平稳且独立，再加 $h\to0$ 时 $P(N(t+h)-N(t)=1)=vh+o(h)$，正合 Poisson process（泊松过程）的刻画；反过来，间隔 iid 指数也是它的等价定义，所以 (a) 是同一件事的两种说法。措辞要校正：Poisson process（泊松过程）指计数过程 $\{N(t)\}$ 本身，$Y_n$ 是它的 arrival times（到达时刻）序列，不能说成「$Y_n$ 服从泊松分布」。
>
> **(b)：两条路，同一结论。** 代数路：平衡方程 $\pi_j\sum_{k\ne j}q_{jk}=\sum_{k\ne j}\pi_k q_{kj}$，代入 $p_{jk}=q_{jk}/v_j$ 与 $v_j\equiv v$，约去公共因子得 $\pi_j\sum_{k\ne j}p_{jk}=\sum_{k\ne j}\pi_k p_{kj}$，恰是嵌入链的 balance equation（平衡方程）。概率路更直观：连续时间链的稳态是**时间平均**，嵌入链的稳态是**步平均**，两者之间差一个权重 $1/v_j$，即 $\pi_j^{\mathrm{CT}}$ 正比于 $\pi_j^{\mathrm{emb}}/v_j$；$v_j$ 全相等时权重为常数，归一化后两套稳态完全重合。这条路顺手说明「速率全等」为何是关键条件——它让两种平均只差一个全局常数。
>
> **方向不能互换。** 左边 $\pi_j\sum_{k\ne j}q_{jk}$ 是离开 $j$ 的 outflow（出流），右边 $\sum_{k\ne j}\pi_k q_{kj}$ 是进入 $j$ 的 inflow（入流）；若把右边写成 $\sum_{k\ne j}\pi_j q_{jk}$，两边就是同一个式子，等式恒成立而丧失全部内容（写成「$0=0$」正是这种恒等式的症状）。口诀：$j$ 在第一个下标位（$q_{jk}$）表示「出」，在第二个下标位（$q_{kj}$）表示「入」；$j$ 是被守衡的那个状态，固定在 $\pi$ 的下标上，不参与求和。
>
> **行和与列和。** $\sum_{k\ne j}p_{jk}$ 是转移矩阵 $P$ 第 $j$ 行删去对角元后的和，由行和 $\sum_k p_{jk}=1$ 得 $1-p_{jj}$；$\sum_{k\ne j}\pi_k p_{kj}$ 则是第 $j$ 列按 $\pi_k$ 加权。正文 PDF p414（书页 p406）的 $\sum_{k\ne j}\pi_k p_{kj}=\pi_j(1-p_{jj})$ 正做了这一替换，下标方向无误，没有把行和当列和。该替换只在 $P$ 为 row-stochastic（行随机）时成立；换成列随机约定，等式两边要整体换位。
>
> **唯一性与「当且仅当」。** 「单一常返类 + aperiodic（非周期）」保证稳态唯一，但 aperiodic（非周期）是对离散时间的嵌入链说的：连续时间链在任意时刻都可能跳，本身没有周期概念，这个限定只能挂在嵌入链上。另需收紧一处：不能写成「当且仅当各状态速率相等」，教材只证了「若」方向。逆命题不成立——两状态链取 $q_{12}=a$、$q_{21}=b$，嵌入链稳态恒为 $(1/2,1/2)$，连续时间稳态满足 $\pi_1a=\pi_2b$ 即正比于 $(b,a)$，$a\ne b$ 时二者不同，尽管稳态都存在。
>
> **一句话收束。** 稳态之所以「稳」，是因为长期占比等于「在该状态的停留总量」除以「总时长」。速率全等时每个状态的期望停留都是 $1/v$，权重相同，(b) 才成立；(a) 则保证跳变发生的节奏与所处状态无关。两问看似独立，其实是同一个假设的两种读法：一个说「等待无记忆」，一个说「占比不随步数换算而变形」。
>
> **返回时间别与稳态等待混同。** 本题只谈稳态占比，不涉及「从某状态出发、下次返回的期望时间」。后者要按步计：在嵌入链上 $m_{jj}=1/\pi_j^{\mathrm{emb}}$（Kac 等式作用在嵌入链上），换到连续时间则要乘期望逗留，得 $1/(\pi_j^{\mathrm{CT}}v_j)$；只有 $v_j\equiv v$ 时两者才成比例关系，而「把每步期望逗留直接乘步数当成返回时间」是这类习题里最常见的混淆之一。
>
> **附记：** uniformization（均匀化）取 $\nu\ge\max_i v_i$、以概率 $1-v_i/\nu$ 加 self-loop（自环），所得离散链与原来那条连续时间链稳态一致，$v_i$ 全等时退化为本题的嵌入链。课程坐标：指数分布的无记忆性、Poisson process（泊松过程）、连续时间链的生成矩阵三条线索在此交汇，本章后面所有 CTMC 题都是这三件事的组合。

> <span style="color:#7f8c8d;">[注] 本页末尾原 OCR 碎裂，已将平衡方程与归一化方程依连续性马尔可夫链·嵌入链标准形式整理合并；数值与公式未臆造。</span>
<!-- ===== PDF p414 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）　习题区收尾（Problems Continuation）· 解答收尾（续）**</span>

> <span style="color:#7f8c8d;">本页页首即为 `Problems` 习题区页眉（书页 p405，对应 PDF p414），承接上一页（PDF p413）某一 §7.5 连续时间马尔可夫链（Continuous-Time Markov Chains）习题英文解答的收尾段，讲的是嵌入马尔可夫链（embedded Markov chain）的平衡方程与稳态概率，故以「（续）」续接，未另起新题号。含公式部分 OCR 碎裂（`7rj`、`Pjj`、`7rk`、`pkj`、`7rj(l - Ph)` 与孤立残行 `m`、`k = l` 等），下方按嵌入链标准稳态方程忠实转写，未臆造原文未含的数值。</span>

We have $\sum_{k \ne j} \pi_k\, p_{kj} = \pi_j (1 - p_{jj})$, so the first of these two equations is written as

```math
\pi_j (1 - p_{jj}) = \sum_{k \ne j} \pi_k\, p_{kj}, \qquad j = 1, \ldots, m,
```

together with the normalization $\sum_{j=1}^{m} \pi_j = 1$.

These are the balance equations for the embedded Markov chain, which have a unique solution since the embedded Markov chain has a single recurrent class, which is aperiodic. Hence the $\pi_j$ are the steady-state probabilities for the embedded Markov chain.

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 页中残行 `m = L 7rk Pk]. k = l L#j 7rkPkj, k`（即书页 §7.5 嵌入链稳态方程组 $\pi_j(1-p_{jj})=\sum_{k\ne j}\pi_k p_{kj}$，$j=1,\ldots,m$ 及归一化 $\sum_j\pi_j=1$）排版错乱，此处按行文语义整理为两组并列块级公式，未新增数值。</span>
<!-- ===== PDF p415 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

> <span style="color:#7f8c8d;">本章章前页（章首 Contents 目录页，书页 p407，对应 PDF p415）。页首数字「8」为本章章号（章 8），其下即章标题行「贝叶斯统计推断（Bayesian Statistical Inference）」与本章完整目录。本页仅列出本章各节目录及其对应书页页码，无正文内容。</span>

<span style="color:#7f8c8d;">**Contents（目录）**</span>

- <span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）**</span> …… p. 412
- <span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）**</span> …… p. 420
- <span style="color:#c0392b;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）**</span> …… p. 430
- <span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）**</span> …… p. 437
- <span style="color:#c0392b;">**§8.5　小结与讨论（Summary and Discussion）**</span> …… p. 444
- <span style="color:#7f8c8d;">**Problems（习题）**</span> …… p. 446

> <span style="color:#7f8c8d;">衔接说明：本章（第 8 章）正文自此起，下一节进入 **§8.1 贝叶斯推断与后验分布**（书页 p412），叙述 Bayesian vs Classical/Frequentist（贝叶斯与经典/频率派之争）、模型选择 vs 估计（model selection vs estimation）等章引言议题。本页为纯目录页，无 OCR 损坏数值。</span>
<!-- ===== PDF p416 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

统计推断（statistical inference）是从可得数据中提取关于某个未知变量或未知模型信息的过程。在本章及下一章，我们的宗旨是：

(a) 培养对两种主要方法——贝叶斯方法（Bayesian）与经典方法（classical）——的体会，认清它们的差异与相似之处。

(b) 呈现各类主要推断问题（inference problems），即参数估计（parameter estimation）、假设检验（hypothesis testing）与显著性检验（significance testing）。

(c) 讨论最重要的方法论，包括最大后验概率准则（maximum a posteriori probability rule）、最小均方估计（least mean squares estimation）、极大似然（maximum likelihood）、回归（regression）、似然比检验（likelihood ratio tests）等。

(d) 结合若干具体例子来阐述这套理论。

<span style="color:#c0392b;">**概率论与统计学（Probability versus Statistics）**</span>

统计推断在一些根本性的方面有别于概率论。概率论是一门自成体系的数学学科，建立在第 1 章引入的公理之上。在概率推理中，我们假定一个完全指定、且满足这些公理的概率模型（probabilistic model）。随后我们运用数学方法来量化这一模型的推论，或回答各种感兴趣的问题。特别是，每一个没有歧义的问题都有唯一正确的答案，尽管这个答案有时并不容易找到。模型被认为是理所当然的，原则上它不必与现实有丝毫相似之处（不过要让模型有用，最好还是与现实相符）。

统计学则不同，它带有一种艺术的成分。对任何特定的问题，可能都存在若干种都说得通的方法，它们会给出不同的答案。一般而言，除非你对推断问题（inference problem）作出若干假设并施加额外的约束，否则并没有一种有原则的方式去挑选「最佳」方法。例如，给定最近五年的股票市场收益率历史，估计明年收益率并不存在唯一「最佳」的方法。

我们可以通过要求某些可取的性质来收窄对「恰当」方法的搜寻范围（例如，当可得数据的数量无限时，该方法能作出正确的推断）。选择一种方法而非另一种，通常取决于若干因素：性能保证（performance guarantees）、既往经验、常识，以及统计学界就某一特定方法是否适用某一特定问题类型所达成的共识。我们将着力把读者引介到一些最流行的方法/选择，以及分析、比较它们的主要途径。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** 第 8 章引言中「概率论与统计学」一段（书页 p408，PDF p416）。它是全书方法论立场的正式声明，给整章定调：probability theory（概率论）是演绎，statistics（统计学）是「带艺术成分」的归纳。
>
> **「唯一答案」的精确含义。** 概率推理的全部输入是一个完全给定的 probabilistic model（概率模型）加一个无歧义的问句；在这个前提下答案唯一，是因为它是同一组公理的必然推论，而不是因为它「更接近真理」。这一点值得替读者钉死：唯一性属于演绎系统内部，模型与现实的关系不在其中——教材紧接着那句「原则上模型不必与现实有丝毫相似」正是此意。换句话说，概率论回答的是「若模型为真，则某事必然如何」；它从不回答「这个模型对不对」。
>
> **统计学为什么没有唯一最优。** 从数据反推模型是 inverse problem（反问题），信息不足则 underdetermined（欠定）。这与 Strang 18.06 里的 $Ax=b$ 同构：$A$ 的列多于行时解集是仿射子空间，必须再加一条 criterion（准则）才有唯一解，最小范数解只是众多合法补充之一。所以「没有最佳方法」的准确说法是：best 这个词在指定 criterion（准则）之前根本没有定义；一旦选定 loss function（损失函数），最优就重新唯一。这也是为什么统计学的争论总是落在「该用什么准则」上，而不是落在「哪个答案对」上。
>
> **「艺术」落地为三处选择。** 本章后文把三次选择都写成了公式：选 loss function（损失函数）——squared error（平方误差）给 LMS 估计，0-1 loss（0-1 损失）给 MAP 判决；选 prior distribution（先验分布），它把「我认为参数该在哪」写成密度；选模型类，即在 parametric（参数化）与 nonparametric（非参数化）之间定一个函数类。教材举股票收益率的例子说的正是同一件事：给定五年历史，估计明年收益率没有唯一最佳方法，因为在说清惩罚什么之前，「最佳」不是一句有内容的话。跨课程接点：6.036 与 CS229 的 model selection（模型选择）、regularization（正则化）、cross-validation（交叉验证）都是在这三处做选择。
>
> **两个易误读。** 其一，不要把这段读成「统计学不严谨」。它的主张是 problem formulation（问题表述）本身属于判断，推导只能发生在此之后；严谨性并未被放弃，只是被限定在既定表述之内。其二，注意方向：概率论是「模型 → 数据」的正向推演，统计学是「数据 → 模型」的反向推断；若把统计学的任务写成「求数据在给定模型下的分布」，方向就反了。ill-posed（不良定，Hadamard 意义：解不唯一或不连续依赖数据）一词刻画的正是统计学的常态，而概率论问题按构造是良定的。
>
> **为什么这段要放在章首。** 因为接下来每一节都会给出「同一份数据、两个都说得通的答案」：MAP 与 LMS 给出不同的数，先验换一个后验跟着换，第 9 章还会用频率派的置信区间给出第三个答案。若读者仍带着「概率问题有唯一正确答案」的预期，会把这种差异误当成错误。教材提前把预期换掉，正是为了让后面的每个例子都被读成「一种合理选择」，而不是「唯一真理」。
>
> **一个可以做的小检验。** 拿一枚硬币掷十次得八次正面：频率派会说「$p$ 的极大似然估计是 $0.8$，置信区间约从 $0.44$ 到 $0.97$」；贝叶斯派在 Beta$(1,1)$ 先验下会说「后验均值是 $9/12=0.75$，$95\%$ 可信区间是某个更窄的区段」。两个答案都正确，因为它们回答的不是同一个问题——一个问「什么取值最能让这份数据显得合理」，一个问「在给定先验后我该相信什么」。把两个数放在一起比较「谁更准」，等于把准则之争误当成计算之争。
>
> **一句话收束。** 两门学科的分工可以用一句话对齐：概率论检验「模型是否自洽」，统计学检验「模型是否配得上数据」。前者靠证明，后者靠准则、比较与共识；教材要求的「培养对两种方法的体会」，本质就是要求读者同时握有这两把尺子，并在具体问题上说清自己在用哪一把。

<span style="color:#c0392b;">**贝叶斯与经典统计学（Bayesian versus Classical Statistics）**</span>

在统计学的领域中存在两大执相对立观点的思想流派：贝叶斯学派（Bayesian）与经典学派（classical，也称为频率派，frequentist）。它们根本的分歧与未知模型或未知变量的本性有关。在贝叶斯观点（Bayesian view）看来，它们被看作具有已知分布的随机变量……
<!-- ===== PDF p417 ===== -->

<span style="color:#7f8c8d;">本节继续第 8 章引言（书目 p409），承接上一页关于先验 / 后验分布的论述，进入「贝叶斯（Bayesian）与经典 / 频率派（Classical/Frequentist）之争」的讨论，页末转入小节 **Model versus Variable Inference（模型推断与变量推断）** 的开头。</span>

本节承接上文：在频率派 / 经典的观点中，它们（这些分布 / 参数）被视为**确定性但恰好未知的量（deterministic quantities）**。

贝叶斯方法（Bayesian approach）本质上试图把统计学的领域拉回到概率论的范畴——在那里，每个问题都有唯一确定的答案。特别是，当试图推断一个未知模型的性质时，它把该模型看作是从给定的一类模型中随机选出来的。这一点是通过引入一个刻画模型的随机变量 $\Theta$，并假设一个**先验概率分布（prior probability distribution）** $p_\Theta(\theta)$ 来实现的。在得到观测数据 $x$ 之后，从原则上可以利用**贝叶斯准则（Bayes' rule）**导出一个**后验概率分布（posterior probability distribution）** $p_{\Theta|X}(\theta\mid x)$。该分布囊括了 $x$ 所能提供的关于 $\Theta$ 的全部信息。

相比之下，经典方法把未知量 $\theta$ 看作一个恰好未知的常数。随后它致力于构造 $\theta$ 的一个带有某种**性能保证（performance guarantees）**的估计。这就与本书中其他方法产生了一个重要的概念性差异：我们面对的不是单个概率模型，而是多个候选的概率模型——每一个可能的 $\theta$ 取值都对应一个模型。

> <span style="color:#7f8c8d;">[原页此处 OCR 有误] 源 OCR 将 $\Theta$、$\theta$ 分别讹读为 `8`、`O`/`0`（如 `pe (O)`→$p_\Theta(\theta)$、`Pe l x (O I x)`→$p_{\Theta|X}(\theta\mid x)$），已按第 8 章符号约定（$\Theta$=未知参数，取值 $\theta$）校正，非臆造。</span>

两个学派之间的这场争论已持续约一个世纪，且往往带有哲学色彩。更进一步，每一派都构造了例子，以表明对方学派的那些方法有时会产出荒谬或令人不快的答案。我们在此简要回顾这场辩论中的若干观点。

设想我们试图通过带噪声的实验来测量某一个物理常数，比如电子的质量。经典统计学家会论证：电子的质量虽然未知，但只是一个常数，没有任何理由把它建模成一个随机变量。贝叶斯统计学家则会反驳：先验分布（prior distribution）无非反映我们**关于知识的状态（state of knowledge）**。例如，如果我们已经从过去的实验中对这个量的取值范围有了粗略的了解，就可以通过假设一个集中（concentrated）在那个范围内的先验分布来表达这一知识。

经典统计学家往往会反对挑选某个特定先验（prior）的任意性。贝叶斯统计学家则会反驳：每一种统计方法都包含某些隐藏的选择；而且，在某些情形下，经典方法恰恰等价于某种特定先验选择下的贝叶斯方法。通过把所有假设集中在先验这**一处**，贝叶斯统计学家主张让这些假设浮现到表面，从而便于审视。

最后，还有实用层面的考量。在很多情形下，贝叶斯方法在计算上不可行（computationally intractable），例如当它们需要求多维积分（multidimensional integrals）的值时。另一方面，随着更快计算的可用，近年来贝叶斯学界的很多研究都聚焦于使贝叶斯方法变得实用可行。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** 第 8 章引言末段（书页 p408–409，PDF p416–417），两派争论的收束。分歧不在数学，而在未知参数的本体论地位：贝叶斯把 $\Theta$ 当随机变量并给 prior distribution（先验分布）；frequentist（频率派）把它当 deterministic quantity（确定性但未知的常数），只对估计量索取 performance guarantee（性能保证）。
>
> **两派各要什么。** 贝叶斯要的是「数据之后我认为参数在哪」，答案就是 posterior distribution（后验分布）本身，任何点估计都从它派生。频率派要的是「这套程序在重复实验下的表现」：unbiasedness（无偏性）、置信区间的 coverage（覆盖率）、检验的 size（第一类错误率）与 power（功效）。同一个问题，前者输出一个分布，后者输出一个带保证的程序——这是本章所有分歧的根，比「先验是否主观」更本质。
>
> **历史坐标。** Thomas Bayes（约 1701 年生，1761 年 4 月 7 日卒）的《An Essay towards solving a Problem in the Doctrine of Chances》在他身后由 Richard Price 送交 Royal Society，1763 年刊于 Philosophical Transactions 第 53 卷 370–418 页；Laplace 独立地于 1774 年在《Mémoire sur la probabilité des causes par les événements》中给出一般形式。频率派一侧的检验框架成形于 20 世纪 20–30 年代，代表是 Ronald Fisher、Jerzy Neyman 与 Egon Pearson（Neyman–Pearson lemma）。客观贝叶斯路线由 Harold Jeffreys 的 Theory of Probability（1939）推动，其 noninformative prior（无信息先验）即 Jeffreys prior。
>
> **「先验任意」的三条回应。** 正文给了三条：其一，prior（先验分布）编码的是 state of knowledge（知识状态），不是凭空捏造；其二，任何方法都含隐藏选择，经典方法在某些问题上恰等价于某个特定先验下的贝叶斯方法；其三，把假设集中到先验这一处，便于审查，即 transparency（透明性）。数学上还可以说得更硬：先验一旦选定，贝叶斯准则就是唯一的更新规则，于是「任意性」被压缩成单一自由度，而不再弥散在整套程序里。反过来说，这条回应的代价也必须承认：先验选错时，后验会以很高的置信度错下去，而频率派的方法至少在多重复实验的意义下有覆盖率兜底。
>
> **与 regularization 的同构。** 选先验与选正则项是同一件事：$L^{2}$ 正则对应高斯先验下的 MAP（maximum a posteriori，最大后验），$L^{1}$ 对应 Laplace 先验，早停对应某种约束先验。这也解释了为什么「超参怎么选」两派都躲不掉——它是 problem formulation（问题表述）的自由度，不是推导能消掉的东西。sensitivity analysis（敏感性分析）就是把这个自由度的后果显式报出来，而不是假装它不存在。
>
> **计算与现实。** 后验常需 multidimensional integral（多维积分），一般不可行；MCMC（Markov chain Monte Carlo，马尔可夫链蒙特卡洛）与 variational inference（变分推断）分别把它换成「可采样的 Markov chain（马尔可夫链）」与「可优化的下界」，前者正接回上一章。这也解释了教材那句「计算上不可行、近年趋于可行」的现实含义：变的不是数学，是算力与算法。
>
> **读法：正文三个例子的分工。** 电子质量一例交代 classical（经典）的立场：一个常数没有理由被随机化；「先验集中在一个范围」说明 prior（先验分布）是知识的编码而不是迷信；「经典方法在某些问题上等价于某个先验下的贝叶斯方法」则是最锋利的一击——它把争论从「要不要先验」改写成「先验有没有被说出口、有没有被检验」。
>
> **一个具体的分歧实例。** Jeffreys 1939 年的教科书里已经注意到：同一批数据，贝叶斯后验与频率派的 p 值可以给出方向相反的结论，这个现象后来被称为 Lindley 悖论（Lindley 于 1957 年著文讨论）。它说明分歧不只是哲学姿态，在假设检验的边界上会给出可观测的不同判决，而这正是本章与第 9 章要读者自己掂量的地方。
>
> **一处方向提醒。** 贝叶斯准则把 likelihood（似然）$f_{X\mid\Theta}(x\mid\theta)$ 乘上先验得到 posterior（后验）$f_{\Theta\mid X}(\theta\mid x)$；两者不是同一个函数，把似然写成 $f_{\Theta\mid X}$ 是本章最高频的方向错误——竖线左边的箭头处理的永远是「已知 $\Theta$ 时 $X$ 怎么分布」，而我们要的恰是反过来的那个。判别口诀：不确定的量永远在竖线右边。

---

<span style="color:#c0392b;">**模型推断与变量推断（Model versus Variable Inference）**</span>

统计推断（statistical inference）的应用往往属于两种类型。在**模型推断（model inference）**中，所研究的对象是一个真实的现象或过程，而对我们而言，它——
<!-- ===== PDF p418 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

> <span style="color:#7f8c8d;">本章（书页 p408 起）开篇关于模型推断（model inference，针对模型结构/参数的构造与验证）与变量推断（variable inference，针对未知变量取值的估计）之区别的导言论述延续至本页。本页承接前述「模型推断」段的中段，随后给出 **Example 8.1**（有噪信道，A Noisy Channel）、小节标题「统计推断问题的粗略分类」（A Rough Classification of Statistical Inference Problems）及对估计（estimation）问题的引述。</span>

……希望基于现有数据来构造或验证一个模型（model），例如行星是否遵循椭圆轨道（elliptical trajectories）？这样的模型随后可用来对未来作出预测（predictions），或用来推断某些隐藏的根本原因。而在变量推断（variable inference）中，我们希望利用若干相关的、可能含噪的信息来估计一个或多个未知变量的取值，例如给定几次 GPS 读数，我的当前位置是哪里？

模型推断与变量推断之间的区别并不泾渭分明；例如，通过用一组变量（variables）来描述一个模型，我们可以把模型推断问题转化为变量推断问题。不管怎样，在后续我们将不再强调这一区别，因为同样的方法论原理适用于这两类推断。

在某些应用中，模型推断与变量推断问题可能会同时出现。例如，我们可能收集一些初始数据，用它们来构建一个模型，然后再用该模型对某些变量的取值作出推断。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** 书页 p409–410（PDF p417–418）「模型推断与变量推断」一节。二分不按问题难度，而按未知物的类型：model inference（模型推断）的未知物是生成机制（结构加参数），variable inference（变量推断）的未知物是有限个具体取值。
>
> **判据是问句，不是参数个数。** 模型推断问「是哪个机制在生成数据」，答案会改变概率模型本身；变量推断问「这次观测背后的潜状态是什么」，模型给定，只在模型内部求解 latent variable（潜变量）。因此更实用的判别法是看「换一个答案是否需要换一套模型」：需要，就是模型推断。用参数个数判会出错——一个三参数的模型与一个十参数的模型都可能属于同一个模型族，而估一个标量参数也可能需要换族（当这个参数决定族的形状时）。
>
> **书里的两个例子正好配成一对。** 行星是否沿椭圆轨道运行是模型推断（问的是机制的形状）；给定若干次 GPS 读数、问「我此刻在哪」是变量推断（机制已知，只差取值）。前者改模型族，后者在模型内定位——同一个数学工具（先验乘似然再归一），落在完全不同的对象上。
>
> **可转化，但只有一个方向。** 正文那句「通过用一组变量来描述一个模型，可以把模型推断问题转化为变量推断问题」说的是 model inference 转 variable inference：把「选哪个模型」编码成「$\Theta$ 取哪个值」，于是 MAP（maximum a posteriori，最大后验）一套公式同时覆盖参数估计与 model selection（模型选择）。反方向不普遍成立——把一个具体估计问题还原成模型推断，等于要求先枚举出全部可能的机制，通常做不到。
>
> **转化的代价。** 一旦把结构塞进 $\Theta$，它的取值域就从 $\mathbb{R}^d$ 变成离散的模型族，先验只能在模型族上定义，可计算性随之下降；模型族一大，先验的归一化本身就是难题。这是下一章把模型选择单列出来的原因：它不是「多一个参数」，而是「参数空间换了形状」。
>
> **同一方程、两种问句。** Example 8.1 的 noisy channel（有噪信道）是最干净的示范：$\alpha$ 未知、$S_i$ 是已知的 pilot signal（导频）时，估 $\alpha$ 就是模型推断；$\alpha$ 已知、$S_i$ 未知时，逐个判定比特就是变量推断。方程一个字没改，问句一换，数学问题就换了一类——这正是这一段要读者建立的直觉。
>
> **方向写反的检查。** 本节最容易犯的错误是把转化方向写反：只有 model → variable 这条路是常规可行的，反过来要么不可行，要么需要先穷举机制。判别口诀：忘掉 $\Theta$ 是什么名字，只看「谁知道什么」——若数据的生成方式仍然未知，问题在模型层；若生成方式已定、只缺一次取值，问题在变量层。
>
> **一个易混的边界例子。** 「这个骰子是否公平」看着是模型推断（要换机制），但一旦把「公平 / 偏斜」编码成参数 $p$ 的两个候选值，它就退化成变量推断；反过来，「估计 $p$」看似变量推断，若同时允许骰子可能是 6 面也可能是 20 面，又升回模型层。可见二分取决于你划定的模型族边界，而不是问题本身固有的属性——同一个物理问题，换一种建模约定，落点就换一层。
>
> **收束。** 正文随后声明「不再强调这一区别」，理由是方法同源：两者都写成「先验 × 似然 → 后验」。但读的时候仍要保留这个区分，因为它决定后验长什么样、能不能算。跨课程接点：CS229 的 density estimation（密度估计）属变量层，feature selection（特征选择）与模型族选择属模型层，两者共用一套贝叶斯工具却对应不同的算法工程。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.1（有噪信道，A Noisy Channel）。**</span>

一台发射机（transmitter）发送一串二进制消息 $S_i \in \{0, 1\}$，接收机（receiver）观测到

```math
X_i = \alpha S_i + W_i, \qquad i = 1, \ldots, n,
```

其中 $W_i$ 是零均值（zero mean）正态随机变量（normal random variables），用于刻画信道噪声（channel noise），而 $\alpha$ 是一个标量，表示信道衰减（channel attenuation）。在模型推断（model inference）的设定下，$\alpha$ 是未知的。发射机发送一个由一串值已知的消息构成的导频信号（pilot signal $S_1, \ldots, S_n$），其取值接收机已知。基于观测 $X_1, \ldots, X_n$，接收机希望估计 $\alpha$ 的值，即为信道构建一个模型。

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本例观测方程（此处写作 $X_i = \alpha S_i + W_i$）在源 OCR 中被打散（仅余二值消息 $S_i \in \{a, I\}$ 与附录式 "$i=1,\ldots,n$" 的碎片），正文亦以 "a"/"a" 混排表示 $\alpha$；上方传动机方程按原书 Noisy Channel 例的权威语义还原，并以 $\alpha$ 规范成文，未臆造数值。</span>

或者，在变量推断（variable inference）的设定下，$\alpha$ 假定为已知（可能如上述那样，已通过导频信号推断出来）。接收机观测到 $X_1, \ldots, X_n$，并希望推断 $S_1, \ldots, S_n$ 的值。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** Example 8.1（书页 p410，PDF p418）。transmitter（发射机）发送二值消息 $S_i\in\{0,1\}$，receiver（接收机）观测 $X_i=\alpha S_i+W_i$，$W_i$ 是零均值正态噪声，$\alpha$ 是 channel attenuation（信道衰减）。同一方程在两种设定下是两类问题：$\alpha$ 未知时为模型推断（用导频估 $\alpha$），$\alpha$ 已知时为变量推断（逐个判定 $S_i$）。
>
> **估 $\alpha$ 的本质是投影。** 噪声 iid（独立同分布）正态时，likelihood（似然）正比于 $\exp\!\left(-\frac{1}{2\sigma^2}\sum_i(X_i-\alpha S_i)^2\right)$，最大化似然等价于最小化残差平方和，闭式解 $\hat\alpha=\sum_i S_iX_i/\sum_i S_i^2$。几何上这就是把观测向量 $X\in\mathbb{R}^n$ 正投影到由导频向量 $S=(S_1,\ldots,S_n)$ 张成的一维子空间：residual（残差）$X-\hat\alpha S$ 与 $S$ 正交。这正是 Strang 18.06 的 normal equation（正规方程）$S^{T}(X-\hat\alpha S)=0$，也是 least squares（最小二乘）这个名字的全部内容。
>
> **三种估计器并不等同，重合的条件要说全。** maximum likelihood（极大似然）在均匀先验下与 MAP（maximum a posteriori，最大后验）一致；而 LMS（least mean squares，最小均方）估计取的是 posterior mean（后验均值），它等于 MAP 只发生在后验分布对称且单峰的时候——对本题来说就是「高斯先验 + 高斯似然」，两者相乘后后验仍是高斯，均值与众数重合，平方损失的最优决策又正好是后验均值。只说「高斯先验 + 平方损失」并不够：平方损失确实让最优估计变成后验均值，但没有高斯似然，后验一般不是高斯，均值也不等于众数，MAP 与它仍然分家。教材把三者并列，读者容易误以为可以互换——它们最小化的目标函数不同，重合需要这一整套条件。
>
> **一个初等但重要的边界。** 若导频全为 $0$，分母 $\sum_i S_i^2=0$，$\hat\alpha$ 无定义——这是 identifiability（可辨识性）最小的例子：数据里没有关于 $\alpha$ 的信息，任何估计器都无解。模型推断的第一步从来不是挑估计器，而是确认数据含有待估参数的信息；这一步失败，后面的最优性讨论全部落空。
>
> **联合估计时 $\hat\alpha$ 不变。** 一个常见误解是「$\hat\alpha$ 只在噪声方差 $\sigma^2$ 已知时才是极大似然解」。把 $\sigma$ 也当作未知参数一起最大化，似然的对数多出一项 $-n\log\sigma-\frac{1}{2\sigma^2}\sum(X_i-\alpha S_i)^2$；先对 $\alpha$ 求导，$\sigma$ 只以正因子的身份出现，不改变驻点方程，所以 $\hat\alpha$ 仍是那个最小二乘解，与 $\sigma$ 是否已知无关。变的是 $\hat\sigma^2$：把 $\hat\alpha$ 代入再对 $\sigma$ 求导，得 $\hat\sigma^2=\frac1n\sum_i(X_i-\hat\alpha S_i)^2$，分母是 $n$ 而不是无偏估计常用的 $n-1$，因此这个方差估计是有偏的。记住这个分工：$\alpha$ 的解不受 $\sigma$ 影响，$\sigma$ 的解依赖 $\alpha$ 且用 $n$。
>
> **变量推断一侧。** $\alpha$ 已知后，$S_i$ 是二值的，噪声独立时对单个 $X_i$ 的 MAP（maximum a posteriori，最大后验）判决就是与 $\alpha/2$ 比大小（等先验时，这正是两簇高斯密度的分界）；若消息带编码约束，则要把整串 $X_1,\ldots,X_n$ 联合推断，这正是纠错码与 Viterbi 算法的入口。同一个观测序列，两种推断的难度结构完全不同：前者是连续参数的估计，后者是离散序列的搜索。
>
> **方向别再错。** 信道的因果方向是 $S\to X$，而我们手里能写出的条件分布只有 $f_{X\mid\Theta}$；贝叶斯准则正是用来反转这个箭头的工具，输出 $f_{\Theta\mid X}$。把 likelihood（似然）写成 $f_{\Theta\mid X}$ 就等于预先假设了答案，是本章最典型的方向错误。判别口诀：$f_{X\mid\Theta}$ 的参数与观测各归其位，不确定的那个永远在竖线右边。
>
> **为什么它像一块接插件。** 线性叠加加独立噪声是最小的可解模型：噪声一除，估计就退化成投影；把 $S_i$ 从常量换成未知量，它立刻变成检验问题；把 $S_i$ 换成一个向量 $S_i\in\mathbb{R}^k$，同一套推导原封不动变成多元回归。学会这一个例子，等于拿到后面所有「线性模型 + 高斯噪声」的母版。
>
> **收束。** 本例之所以被放在章首，是因为它把「模型推断 / 变量推断」的二分压缩进一个公式：改 $\alpha$ 的状态，问题就换类。课程坐标：6.041 第 8 章 §8.1（本例作为二分示范）、§8.3（LMS 给出后验均值）、第 9 章（假设检验与似然比）；6.036 的线性回归与正规方程在此完全对齐，差别只在于前者从「最小化损失」出发，本书从「给定先验求后验」出发。

---

<span style="color:#c0392b;">**统计推断问题的粗略分类（A Rough Classification of Statistical Inference Problems）**</span>

我们在此描述几类不同的推断问题。在估计问题（estimation problem）中，一个模型除一个未知的、可能为多维的参数 $\theta$ 外被完全给定，我们希望估计该参数。这个参数既可以看作一个随机变量（random variable，贝叶斯方法，Bayesian approach），也可以看作一个未知常数（classical approach，经典方法）。通常的目标是得到一个在某种意义下接近真实值的 $\theta$ 估计。例如：

(a) 在 Example 8.1 的有噪传输问题中，利用导频序列（pilot sequence）与观测来估计 $\alpha$。

(b) 利用民意调查（polling）数据，估计选民总体中偏好候选人 A 胜过候选人 B 的比例。

(c) 基于历史股票市场数据，估计某只股票每日价格变动的均值（mean）与方差（variance）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** 书页 p410–411（PDF p418–419）「统计推断问题的粗略分类」。按「参数连续 / 离散」区分 estimation（估计）与 hypothesis testing（假设检验），只是在描述现象；真正的判据是决策空间与 loss function（损失函数）：估计的动作是报一个数或向量，损失通常是 squared error（平方误差）；检验的动作是从有限个假设里挑一个，损失是 0-1 loss（0-1 损失）。
>
> **三层结构。** ① 估计：动作落在与参数同维的连续空间；② 二值检验：$\Theta$ 只取两个值，$m=2$；③ $m$ 元检验：有限个互斥假设。三者可以写成同一个四元组（参数、观测、decision rule（决策规则）$\delta$、损失 $L$），选 $\delta$ 使期望损失最小。这个期望损失在文献里叫 risk（风险），即 $\mathrm{risk}(\delta)=E[L(\delta(X),\Theta)]$；平方损失下它就是 mean squared error（均方误差），展开后等于 variance（方差）加 bias（偏差）的平方。「选择方法」于是被翻译成「选择使风险最小的 $\delta$」。
>
> **risk 不等于偏差。** 这里最容易写错的一处是：risk 是损失函数的期望，而不是「估计量与真值之差的期望」。后者 $E[\delta(X)-\theta]$ 是 bias（偏差），只是 risk 在平方损失下展开出的一项；无偏估计（bias 为零）照样可能有很大的 risk，因为方差还在。把 risk 说成「偏差」会让「最小化 risk」看起来像是在要求无偏，正好错位。
>
> **三个例子各自落在哪。** (a) 有噪信道的 $\alpha$ 是估计；(b) 民调里偏好 A 胜过 B 的比例是估计，本质是一个 Bernoulli 参数的估计；(c) 股票日收益的均值与 variance（方差）是二维估计。三者的共同点是动作等于报数，所以都能写成 $\hat\theta(x)$ 这种函数形式，区别只在维数与损失形状。
>
> **统一之后的好处。** 一旦写成四元组，两派的差别就变成「$\Theta$ 是否有先验」：有先验则最小化 Bayes risk（贝叶斯风险），无先验则最小化最坏情形风险，即 minimax（极小极大）。估计与检验也不再是两个工具箱，而是同一台机器换一个损失函数。文献上这套语言叫 statistical decision theory（统计决策论），它把「估计」与「检验」的差别降级为损失函数的一个特例。
>
> **与机器学习的对齐。** 估计约等于 regression（回归），检验约等于 classification（分类）；6.036 与 CS229 的损失表可以逐格对上：squared error（平方误差）给回归，0-1 loss（0-1 损失）给分类，logistic loss（逻辑损失）给概率输出。这层对齐不是类比而是同一件事：那门课的 empirical risk minimization（经验风险最小化）就是这里的 risk 用样本平均替代期望之后的版本。
>
> **两处易混。** 其一，cross-entropy（交叉熵）是负对数似然，最小化它等于 ML 而不是 MAP，要加上先验项（正则项）才变成 MAP。其二，估计问题的「误差」要分清三个层次：risk（风险）是损失的期望，squared error 下等于方差加偏差平方；variance（方差）只解释其中一部分；bias（偏差）解释另一部分。二者此消彼长正是 bias-variance（偏差-方差）权衡的来源。
>
> **一个技术细节。** $m$ 元检验的损失仍取 0-1，而不是「错几个」——一次决策只挑一个假设，要么对要么错，损失只占一个比特。若错误真有分级（把良性判成恶性的代价高于反向），就要换成加权损失，此时 MAP（maximum a posteriori，最大后验）判决也跟着变：最优判决变为「选使 $\sum_\theta L(\hat\theta,\theta)p_{\Theta\mid X}(\theta\mid x)$ 最小的那个」，无权重的 0-1 损失恰好把它压小成「取后验最大的那个」，这正是 §8.2 要证的结论。
>
> **工程含义。** 估计的解通常是一个闭式公式，代价是一次遍历或一次求逆；检验则要多选一个阈值，而阈值从不中立——它编码了对两类错误代价的估计。把阈值写死却不说清「为什么是这个数」，是实践中最常见的隐性假设泄漏。
>
> **收束。** 这一段的功能是给读者一张地图：后面每一节都会落回「动作空间 + 损失」这两个坐标上。检验问题的例子随后在正文里展开（人像检测、医学方案比较），它们与估计问题的唯一差别就是动作集从连续变成有限——公式不必重学，只需把积分换成求和、把平方损失换成 0-1 损失。

<!-- ===== PDF p419 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，仍是第 8 章引言（章首叙事，书页 p408–411）的收尾部分：先讲完二值及多值假设检验（hypothesis testing）的概要，交代本章与下一章的分工，并以一个非参数化（nonparametric）问题的例子说明统计推断的问题范围之广；随后转入本章的「本章主要术语、问题与方法（Major Terms, Problems, and Methods in this Chapter）」要点清单。第 8 章正文（§8.1）从书页 p412 起。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 例 8.1 噪声传输问题那条引述中，个别字母/下标在 OCR 中被误读打散（如 `of a and Xi` 当为 已知 $\alpha$ 与 $X_i$、`Si was 0 or l` 即被判定对象 $S_i$ 是 0 还是 1、`Y g(X)` 中的 `9` 当为未知函数 $g$）。在变量推断（variable inference）设定下，待判定的二值量是传输比特 $S_i\in\{0,1\}$（此时衰减 $\alpha$ 已知），故上引 `Si was 0 or l` 沿用原文，非 $\Theta$ 是 0 或 1。下按原书 411 页权威语义还原，未新增原文未含的数值。</span>

在二元假设检验问题（binary hypothesis testing problem）中，我们从两个假设（hypotheses）出发，并利用手头的观测数据（data）来判定二者中哪一个为真。例如：

(a) 在例 8.1 的噪声传输问题（noisy transmission problem）中，利用 $\alpha$ 与 $X_i$ 的已知取值，来判定 $S_i$ 究竟是 0 还是 1。

(b) 给定一幅含噪图像（noisy picture），判定其中是否有人。

(c) 给定针对两种备选医学治疗方案（medical treatments）的一组试验，判定哪一种治疗最有效。

更一般地，在一个 $m$ 元假设检验问题（$m$-ary hypothesis testing problem）中，存在有限数目 $m$ 个相互竞争的假设。某种特定方法的性能，通常由它作出错误决策（erroneous decision）的概率来衡量。同样地，贝叶斯（Bayesian）方法与经典（classical）方法此时也都是可行的。

本章我们主要聚焦于贝叶斯估计（Bayesian estimation）类问题，但也会讨论假设检验（hypothesis testing）。在下一章中，除了估计之外，我们还会讨论更广泛的一类假设检验问题。我们的处理是入门性质的，远未穷尽实际中会遇到的统计推断（statistical inference）问题范围。作为另一类不同于前述类型的问题的示例，考虑构造一个形如

```math
Y = g(X) + W
```

的、把两个随机变量 $X$ 与 $Y$ 关联起来的模型。这里 $W$ 是零均值噪声（zero mean noise），而 $g$ 是一个待估计的未知函数。这类问题中，其不确定对象（此处即函数 $g$）无法用固定有限数目的参数来描述，因而被称为非参数化（nonparametric）问题，超出了我们的讨论范围。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** 书页 p411（PDF p419）末段，用 $Y=g(X)+W$ 引出 nonparametric（非参数化）问题。这个标签容易被误读，所以定义要写准：nonparametric（非参数化）不是「没有参数」，而是「参数个数不预先固定为有限值，而随样本量 $n$ 一起增长」；等价说法是模型所在的函数类是 infinite-dimensional（无穷维）的。
>
> **判据只有一条。** 能否用固定维数 $\theta\in\mathbb{R}^d$（$d$ 不随 $n$ 变）索引整个模型族。据此判定，参数上百万的神经网络仍是 parametric（参数化）；而每加一个样本就多一个节点的 spline（样条）却是 nonparametric（非参数化）。所以「参数多」绝不等价于「非参数」，这是这个标签最常被混淆的地方。
>
> **本章方法为何在此失效。** MAP（maximum a posteriori，最大后验）与 LMS（least mean squares，最小均方）都要求「先验 × 似然」在有限维参数上成为可积密度；一旦 $\Theta$ 是函数空间的一个元素，先验就变成函数空间上的测度（如 Gaussian process（高斯过程）先验），后验不再是有限维密度，「求后验均值」变成求一个函数。数学上完全可行，但超出入门工具包，这正是正文把它标为「超出讨论范围」的实际理由。
>
> **无穷维并不神秘。** 对 $g$ 加光滑性先验，无穷维会被压成 effective degrees of freedom（有效自由度）；kernel smoothing（核平滑）、spline（样条）、Gaussian process 回归最终都实现为有限维线性代数，规模是 $n\times n$ 的 Gram 矩阵。与 Strang 18.06 的接点在正则化最小二乘：$(A^{T}A+\lambda I)^{-1}A^{T}y$ 就是把函数空间投影到由样本张成的有限维子空间，$\lambda$ 控制投影的软硬——无穷维模型的「容量」最终由 $\lambda$ 一个标量决定。
>
> **一处表述要收边界。** 「参数数目随数据增长而无界」应读作「随 $n$ 增长」：固定 $n$ 时它有限，谈无界必须带上「当 $n\to\infty$」这个前提。另需防一个误读：nonparametric（非参数化）不等于 model-free（无模型），恰恰相反，它用的是一个更宽的函数类模型，假设不是消失了，而是从「形状固定」换成「光滑性 / 稀疏性」这类更弱的约束。
>
> **一个具体对照。** 同样 $n$ 个点：若假定 $g$ 是三次多项式，参数量恒为 $4$，样本再多也不变，这是 parametric（参数化）；若用 kernel smoothing（核平滑）在每个样本点上放一个核，参数量随 $n$ 增长，这是 nonparametric（非参数化）。两者拟合同一条曲线时结果可以极其接近，差别不在当下的拟合值，而在「样本量增加时它能不能变得更细」。
>
> **有效自由度怎么算。** 对线性平滑器 $\hat y=Hy$（$H$ 是 hat matrix（帽子矩阵）），effective degrees of freedom（有效自由度）取 $\mathrm{tr}(H)=\sum_i h_{ii}$；$H$ 是投影矩阵时它恰等于子空间维数，于是「无穷维模型」被一个整数刻画。这正是非参数方法在实践中并不真的携带无穷多参数的原因：容量由 $\mathrm{tr}(H)$ 或 $\lambda$ 这类少数标量管住。
>
> **还有一个同名但不同的用法。** 统计里的 nonparametric test（非参数检验）指不假定总体分布形状的检验，如符号检验、秩和检验；它与回归里的 nonparametric（非参数化）不是一回事——前者放松的是分布假设，后者放松的是函数形状假设。读文献时若不区分这两层，很容易把「不假设正态」与「不假设线性」混为一谈。
>
> **收束。** 这一段的真正目的是划定本章的势力范围：后面所有估计器都建立在「$\Theta$ 落在 $\mathbb{R}^d$、先验有密度」之上。看到 $Y=g(X)+W$ 这类问题，正确的反应不是硬套 MAP，而是先问两件事：$g$ 的光滑性假设是什么、样本量相对自由度够不够。前者决定模型，后者决定它能不能算得出来。

---

<span style="color:#00838f;">**[本章要点]**</span> <span style="color:#00838f;">**本章主要术语、问题与方法（Major Terms, Problems, and Methods in this Chapter）**</span>

- 贝叶斯统计（Bayesian statistics）把未知参数视为随机变量（random variables），且带有已知的先验分布（prior distributions）。
- 在参数估计（parameter estimation）中，我们希望以某种概率意义（probabilistic sense）上接近参数真实值的方式，来产生估计（estimates）。
- 在假设检验（hypothesis testing）中，未知参数取有限个数个值之一，各值对应相互竞争的假设；我们要在这些假设中作出选择，目标是获得较小的误差概率（probability of error）。
- 主要的贝叶斯推断方法（Bayesian inference methods）：
  (a) 最大后验概率（maximum a posteriori probability，MAP）准则：在可能的参数值/假设中，选出在给定数据下条件/后验概率（posterior probability）最大（maximum）的那一个（第 8.2 节）。
  (b) 最小均方（least mean squares，LMS）估计：选取一个估计量（estimator），即数据的某个函数，使其最小化参数与其估计之间的均方误差（mean squared error）（第 8.3 节）。
<!-- ===== PDF p420 ===== -->

<span style="color:#7f8c8d;">§8.1 贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）续页。本页书页号为 412，页眉为「8 / Sec. 8.1」，§8.2 尚未开始。本页开头顶部为上页关于「如何选取观测并刻画贝叶斯推断问题三要素」论述的收尾部分（故以「（续）」衔接），随后转入对推断模型（inference model）的总结性段落的展开叙述。</span>

<span style="color:#00838f;">**[note] 推断模型的总结（A Summary of the Inference Model）**</span>

…我们据此选定一个观测（observation）$X$——既可以当作一个随机变量（random variable）来处理，也可以视为对所研究物理量（physical quantities）的一种表示，诸如某一被选「对象」的位置（position）与速度（velocity）之类。我们对某个未知参数（parameter）$\Theta$ 抱持某种先验信念。除非我们事先掌握了关于 $\Theta$ 足够多的信息，否则这一信念便只能由先验分布（prior distribution）来刻画；而在真正着手从数据中提取关于 $\Theta$ 的信息之前，我们其实并不会预先知道 $\Theta$ 的取值……（此处正文源 OCR 碎裂，仅余片段）

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页整页 OCR 严重碎裂：绝大多数字词被切成零散单字或短片段（如页首 "(c) Select an…"、"(a)…(Xl"、"(b) A…" 三处列表式下的文字仅余 "of random variable"、"physical quantities…position / velocity"、"we know the joint … distribution … continuous" 等零散字样）。下文按原书 §8.1「推断模型」一节的标准语义做忠实重建，仅还原可辨识的关键术语与总体思路；凡原文确切的措辞已无法逐字复原处，均在此注出，绝不臆造原文未出现的数值或符号。</span>

以上讨论依赖于一个关键事实：要计算后验分布，我们需要知道观测 $X$ 在给定 $\Theta$ 之下的条件分布，即似然（likelihood）——当 $X$ 为离散随机变量时它是条件分布列（conditional PMF）$p_{X\mid\Theta}(x\mid\theta)$，当 $X$ 为连续随机变量时它是条件概率密度函数（conditional PDF）$f_{X\mid\Theta}(x\mid\theta)$。究竟采用分布列还是密度函数，取决于 $X$ 是离散的还是连续的；与此类似，我们还需要根据 $\Theta$ 取值域是离散还是连续，来相应地选择 $\Theta$ 的先验分布列 $p_\Theta(\theta)$ 或先验密度 $f_\Theta(\theta)$。

```math
\text{给定观测值 } X = x \text{，贝叶斯推断问题（Bayesian inference problem）的完整解答}
```

将由后验分布（posterior distribution）$f_{\Theta\mid X}(\theta\mid x)$（当 $\Theta$ 连续时；离散情形则写作 $p_{\Theta\mid X}(\theta\mid x)$）给出。它是把先验分布与似然通过贝叶斯准则（Bayes' rule）相乘并按分母归一化后得到的。该后验分布浓缩并封装了可得观测数据所能提供的关于 $\Theta$ 的全部信息（encapsulates all the available information）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源 OCR 中后验密度被读成残缺片段（如 "posterior distribution Pe l x ( () I"、"fe I x ( () I ：::ie c…" 等），此处按 $\Theta$ 连续的一贯记号 $f_{\Theta\mid X}(\theta\mid x)$ 与贝叶斯准则的归一化过程还原，未添加任何原文未含之公式。</span>

一旦求得了后验分布，它便可用于回答（answer）各种各样进一步（additional）的推断问题，也可用于计算对未知量（如某概率或误差方差（error variances）……）的估计（estimates）。例如，后验分布可以用于……（此处正文转至对误差方差以及其他推断量的估计，后续表述被源 OCR 打碎，仅余片段）。

于是便得到了一个十分简洁、在贝叶斯统计推断（Bayesian statistical inference）中反复出现的推断模型（inference model）：它由未知参数 $\Theta$（带有先验分布）与观测 $X$（带有条件分布列或条件概率密度函数）两大部分构成，而推断的终点就是由贝叶斯准则算出的后验分布。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 末段「后验可计算估计量」「可计算均方误差/误差方差等」的过渡句在源 OCR 中残损严重（仅 ".…can be used to the calculation of estimates of"、"probabilities or error variances" 及 "answer additional inference questions" 可辨），确切接线措辞无法逐字复原，故上段仅作连贯化转写。</span>
<!-- ===== PDF p421 ===== -->

> <span style="color:#7f8c8d;">§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）· 书目 p.413。本页承接上一页（PDF p420，书目 p412）的 §8.1 论述，转入「贝叶斯推断总结」小节，并以规则框列出「贝叶斯准则的四种版本」。页内无新例，属正文叙述与小节收尾，故直接分段呈现。</span>

<span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）**</span>

<span style="color:#2471a3;">**[summary]**</span> <span style="color:#2471a3;">**贝叶斯推断总结（Summary of Bayesian Inference）**</span>

- 我们从未知随机变量 $\Theta$ 的一个先验分布（prior distribution）$p_\Theta$ 或 $f_\Theta$ 出发。
- 我们有一个观测向量（observation vector）$X$ 的模型 $p_{X|\Theta}$ 或 $f_{X|\Theta}$。
- 在观测到 $X$ 的取值 $x$ 之后，我们利用相应版本的贝叶斯准则（Bayes' rule），形成 $\Theta$ 的后验分布（posterior distribution）。

注意，贝叶斯准则共有四种不同版本，这里为方便参考把它们逐一重复列出。它们对应 $\Theta$ 与 $X$ 分别为离散或连续的四种组合。然而，这四种版本在句式上相似：从最简单的一版（所有变量均为离散）出发，只须在涉及连续随机变量时，把概率质量函数（probability mass function，PMF）换成概率密度函数（probability density function，PDF）、把求和换成求积分即可。此外，当 $\Theta$ 是多维（multidimensional）时，相应的求和或积分都应理解为多维和或积。

<span style="color:#2471a3;">**[rule]**</span> <span style="color:#2471a3;">**贝叶斯准则的四种版本（The Four Versions of Bayes' Rule）**</span>

- $\Theta$ 离散，$X$ 离散：

```math
p_{\Theta|X}(\theta \mid x) =
\frac{p_\Theta(\theta)\,p_{X|\Theta}(x \mid \theta)}
{\sum_{\theta'} p_\Theta(\theta')\,p_{X|\Theta}(x \mid \theta')}.
```

- $\Theta$ 离散，$X$ 连续：

```math
p_{\Theta|X}(\theta \mid x) =
\frac{p_\Theta(\theta)\,f_{X|\Theta}(x \mid \theta)}
{\sum_{\theta'} p_\Theta(\theta')\,f_{X|\Theta}(x \mid \theta')}.
```

- $\Theta$ 连续，$X$ 离散：

```math
f_{\Theta|X}(\theta \mid x) =
\frac{f_\Theta(\theta)\,p_{X|\Theta}(x \mid \theta)}
{\int f_\Theta(\theta')\,p_{X|\Theta}(x \mid \theta')\,d\theta'}.
```

- $\Theta$ 连续，$X$ 连续：

```math
f_{\Theta|X}(\theta \mid x) =
\frac{f_\Theta(\theta)\,f_{X|\Theta}(x \mid \theta)}
{\int f_\Theta(\theta')\,f_{X|\Theta}(x \mid \theta')\,d\theta'}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源 OCR 中「贝叶斯准则的四种版本」仅第二种（$\Theta$ 离散、$X$ 连续）的公式完整可辨，即
> $p_{\Theta|X}(\theta \mid x)=\dfrac{p_\Theta(\theta)\,f_{X|\Theta}(x\mid\theta)}{\sum_{\theta'} p_\Theta(\theta')\,f_{X|\Theta}(x\mid\theta')}$，
> 且仅两个子项（$\Theta$ 离散、$\Theta$ 连续）的批注开头字样可辨。其余三种版本的公式（以及第一种、第三种、第四种版本前的条目句式）在 OCR 中被打散成碎片（如 `Pe l x ( 0 I x )`、`L pe ( 0' ) ix Ie`、`(Jf` 等）。页面上方正文「以离散版为基础、PMF 换 PDF、求和换积分、多维情形的多维和积」这段指引文字完整，故此处仅据此忠实还原四种版本的标准形式——即下方 1–4 四条公式均为按标准形式重建、非逐字还原，未臆造任何正文未声明之外的数值或符号。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p422）：贝叶斯准则的四种版本列出后，本页结束于第四条版本（$\Theta$ 连续、$X$ 连续）的公式；后续页将据此转入新的 Example 或进阶讨论。</span>
> <span style="color:#1e8449;">[note] Note（译者注）:</span> **定位。** 书页 p413–414（PDF p421–422）§8.1 末尾的规则框「The Four Versions of Bayes' Rule」。四式不是四个定理，而是「$\Theta$ 与 $X$ 各取离散 / 连续」的笛卡尔积：骨架恒定，都是「后验正比于先验乘似然，再除以 normalizing constant（归一化常数）」，差别只在于把求和换成积分、把 PMF（概率质量函数）换成 PDF（概率密度函数）。
>
> **一条规则替代四次背诵。** 分母的求和或积分永远对哑变量 $\theta'$ 进行，与 $X$ 的离散 / 连续性无关；$X$ 的类型只决定分子里写 $f_{X\mid\Theta}$ 还是 $p_{X\mid\Theta}$，$\Theta$ 的类型只决定分母用 $\sum_{\theta'}$ 还是 $\int d\theta'$。于是四版分别落在：离散对离散、离散对连续、连续对离散、连续对连续，两条选择相互独立，$2\times2$ 恰好四种。记住这条，四种版本无需逐一背。
>
> **逐版核对。** 已核对正文四条公式，上下标方向均正确：分子第一因子是 prior（先验）$p_\Theta$ 或 $f_\Theta$，第二因子是 likelihood（似然）$f_{X\mid\Theta}$ 或 $p_{X\mid\Theta}$；分母把 $\theta$ 换成 $\theta'$ 后按 $\Theta$ 的类型求和或积分，$x$ 保持为观测值不变。竖线的左右两侧没有互换，这是本节最需要盯住的一处。
>
> **两条记号纪律。** 其一，$x$ 是已观测的固定值，$\theta$ 是自变量，分母必须换用哑变量 $\theta'$；分子分母共用同一个 $\theta$，形式上看像约分，实质是变量名冲突，等比写错更难察觉。其二，$f_{X\mid\Theta}(x\mid\theta)$ 是 likelihood（似然），$f_{\Theta\mid X}(\theta\mid x)$ 是 posterior（后验）；箭头方向相反，写反是本章最高频的错误。
>
> **四个公式实为一个。** 用测度论语言，后验就是 Radon–Nikodym derivative（Radon–Nikodym 导数）$dP_{\Theta\mid X=x}/d\mu$：$\mu$ 取 counting measure（计数测度）时得到 PMF（概率质量函数），取 Lebesgue measure（Lebesgue 测度）时得到 PDF（概率密度函数）。四种版本只是同一个导数在不同参考测度下的密度表示——先有测度、后有公式，而不是反过来。
>
> **连续版的真实麻烦要写对。** 两边都连续时，若 $(\Theta,X)$ 没有联合密度，后验就不再是密度函数。最极端的例子是 $X=\Theta$（观测就是参数本身）：这时给定 $X=x$，$\Theta$ 必然等于 $x$，后验是点质量 $\delta_x$，唯一且无任何歧义——这类情形并不构成悖论，只是不能写成密度。真正的麻烦是另一个：在零概率事件上条件化时，答案依赖你把该事件写成哪个坐标、哪个版本的函数，不同写法给出互相矛盾的「条件分布」，这就是 Borel–Kolmogorov 悖论的实质。它是「正则条件概率不唯一」的问题，而不是「后验存不存在」的问题；把它说成「$X=\Theta$ 就触发悖论」是把病因安错了地方。入门课程通常绕开这些，但读者应知道四式的前提是「$\Theta$ 与 $X$ 有联合密度」。
>
> **历史一句。** Bayes 1763 年那篇文章只处理了二项（伯努利）似然配均匀先验的特例，也就是今天的 Beta$(1,1)$ 先验；把一般的「先验 × 似然」形式写出来的是 Laplace 1774 年的《Mémoire sur la probabilité des causes par les événements》。教材把它叫 Bayes' rule 而不叫 Bayes–Laplace rule，是历史惯例而非归属判断。
>
> **最容易记错的一版。** 第三版（$\Theta$ 连续、$X$ 离散）的分子是 $f_\Theta(\theta)p_{X\mid\Theta}(x\mid\theta)$：两种记号的角色与前两版相反，因为 $\Theta$ 连续才出现密度 $f_\Theta$，$X$ 离散才出现概率 $p_{X\mid\Theta}$。记不住时只问一句「哪个量在积分域里走」——它在分母里配 $\int$，另一个配 $\sum$。附带说明：正文第 2 版公式 OCR 完整可辨，其余三版按标准形式重建，未臆造任何数值。
>
> **与第 1 章的连接。** 离散对离散那一版就是第 1 章最基础的条件概率公式：分子是「先验乘似然」，分母按全概率公式展开。其余三版不是新定理，只是同一个定义在连续轴上把 $P(X=x)$ 换成密度后的合法版本——这件事在概率论里不平凡（零概率事件的条件化需要极限或测度论），所以教材只给公式、把论证留给后续课程。
>
> **一个可算的最小例子。** 取 $\Theta$ 只在两个值中取、先验各半，$X$ 在给定 $\Theta$ 下为高斯；观测到一个 $x$ 后，后验只需两次密度求值加一次归一化，不涉及任何积分。这条「先验乘似然、再归一」的操作顺序，是后面所有例子的计算模板，例 8.2 的朱丽叶迟到问题也是照这个顺序走的，只不过归一化常数要用积分算出来。
>
> **收束。** 这一框的价值在于把「四套公式」降维成「一个骨架加两条轴」。以后遇到混合情形（$\Theta$ 连续而 $X$ 的某些分量离散），不必另找公式：逐坐标决定用 $\sum$ 还是 $\int$，骨架不动。

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，继续 §8.1 的讨论。页首一句「下面用一些例子来演示后验的计算」，随后进入本章新例 **Example 8.2**：罗密欧与朱丽叶约会——朱丽叶迟到的时长在 $[0, \theta]$ 上均匀分布而 $\theta$ 未知、服从先验（prior），并通过贝叶斯准则（Bayes' rule）求后验 PDF（posterior PDF）。本页在同一例子内给出 $n$ 次约会的推广（把后验中的归一化常数 $c(x)$ 表达为关于最大迟到时长 $\bar{x}$ 的积分）。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 部分损坏] 本页多处 OCR 碎裂：未知参数的符号在原文中为 $\Theta$/$\theta$，但 OCR 常被读成 `O`（如先验 `!e (O)`、`[0, OJ`、$^\circ \le x \le 0 \le 1$ 等）；后验公式右端 `1 /(O • I log x l)` 亦碎。现按原书 §8.1 的权威语义还原为 $\theta$ 与后验 $\frac{1}{\theta\,\lvert\log x\rvert}$，未臆造任何原文未含的数值。</span>

下面用一些例子（examples）来演示后验（posterior）的计算。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.2．罗密欧与朱丽叶的约会（Romeo and Juliet start dating）**</span>

罗密欧（Romeo）与朱丽叶（Juliet）开始约会，但朱丽叶每次约会都会迟到一段随机的时长 $X$，该时长在区间 $[0, \theta]$ 上均匀分布（uniformly distributed）。参数 $\theta$ 未知，被建模为随机变量 $\Theta$ 的值，而 $\Theta$ 在零到一小时之间均匀分布。假定朱丽叶在她们第一次约会时迟到了时长 $x$，那么罗密欧应如何用这一信息来更新 $\Theta$ 的分布？

此处先验 PDF（prior PDF）为

```math
f_{\Theta}(\theta) =
\begin{cases}
1, & \text{若 } 0 \le \theta \le 1,\\
0, & \text{其他情形,}
\end{cases}
```

而观测的条件 PDF（conditional PDF of the observation）为

```math
f_{X|\Theta}(x \mid \theta) =
\begin{cases}
1/\theta, & \text{若 } 0 \le x \le \theta,\\
0, & \text{其他情形.}
\end{cases}
```

利用贝叶斯准则（Bayes' rule），并考虑到 $f_{\Theta}(\theta) f_{X|\Theta}(x \mid \theta)$ 仅在 $0 \le x \le \theta \le 1$ 时非零，我们得出对任意 $x \in [0, 1]$ 后验 PDF 为

```math
f_{\Theta|X}(\theta \mid x) =
\frac{
f_{\Theta}(\theta)\, f_{X|\Theta}(x \mid \theta)
}{
\displaystyle\int f_{\Theta}(\theta')\, f_{X|\Theta}(x \mid \theta')\, d\theta'
}
=
\frac{1/\theta}{
\displaystyle\int_{x}^{1} (1/\theta')\, d\theta'
}
=
\frac{1}{\theta\,\lvert \log x \rvert},
\quad \text{若 } x \le \theta \le 1,
```

且当 $\theta < x$ 或 $\theta > 1$ 时，$f_{\Theta|X}(\theta \mid x) = 0$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这句话读的是后验的定义域，而不是它的函数值。正文在书页 p422 的例 8.2 里给出 $n=1$ 时的后验密度 $f_{\Theta|X}(\theta\mid x)=1/(\theta\lvert\log x\rvert)$ 于 $x\le\theta\le1$，紧接着补一句「当 $\theta<x$ 或 $\theta>1$ 时它为零」。前一句说密度长什么样，后一句说它定义在哪；后一句更硬：那里的概率不是「很小」，而是恰好为零，并且这个零不可逆。
>
> 第一性原理是「乘法看支撑」。Bayes' rule（贝叶斯准则）的分子是 $f_\Theta(\theta)f_{X|\Theta}(x\mid\theta)$，乘积为正要求两个因子同时为正。先验 $f_\Theta$ 在 $[0,1]$ 上恒等于 $1$，处处为正；似然 $f_{X|\Theta}(x\mid\theta)=1/\theta$ 只在 $0\le x\le\theta$ 时非零。两条合起来给出 $x\le\theta\le1$。所以「$\theta<x$ 处为零」不是积分算出来的性质，而是两个 support（支撑）取交集的结果：后验的定义域等于先验支撑与似然支撑之交，任何一方的零都会把整个乘积压成零。
>
> 把归一化做一遍，等于给这句话做一次自检。分母是 $\int_x^1 d\theta'/\theta'=-\log x=\lvert\log x\rvert$（$0<x\le1$ 时 $\log x\le0$，故取绝对值），于是 $f_{\Theta|X}(\theta\mid x)=1/(\theta\lvert\log x\rvert)$，再验 $\int_x^1 d\theta/(\theta\lvert\log x\rvert)=1$。这一步同时检查两件事：积分限的方向，与常数的位置。这里原注的说法要改：它把两种错误合写成「积分不为 $1$」，太轻。若把下限写成 $0$，$\int_0^1 d\theta/\theta$ 在 $\theta=0$ 处对数发散，得到的是无定义的无穷大，而不是某个不等于 $1$ 的常数；若漏掉 $\lvert\log x\rvert$，得到的则是一个正比关系，形状对、刻度错。发散与比例错是两类病，必须分开说。
>
> 从信息的角度看，观测 $x$ 的作用是把参数的下界从 $0$ 抬到 $x$，也就是把参数空间里 $[0,x)$ 这一段整段剪掉。关键在于剪除不是靠密度数值实现，而是靠一个取 $0/1$ 的 indicator function（指示函数）实现：即使 $1/\theta$ 在 $\theta<x$ 处「看起来很可观」，乘上零之后就不存在了。所以支撑携带的信息比密度数值携带的信息更硬——它是逻辑层面的排除，不是「证据较弱」这种能靠更多数据慢慢抵消的东西。
>
> 命名模板：support（支撑）指密度的非零集；support truncation（支撑截断）指观测把后验支撑从 $[0,1]$ 压成 $[x,1]$。与之对照的是 full support（全支撑）情形，例如正态观测 $X=\Theta+W$，任何有限观测都不会造成硬零，后验在整条实轴上处处为正。两者的差别不在计算技巧而在模型结构：一个是端点随参数移动，一个是形状随参数平移。
>
> 这里常被类比成 Cromwell 规则，但要点明边界。Cromwell 规则说的是先验若给某个事件 $0$ 或 $1$ 的概率，后续再多的数据也翻不动它；本页的情形是似然在 $\theta<x$ 处恒等于零，于是后验在那里出现 hard zero（硬零）。机制相同而对象不同，一个在似然上、一个在先验上，所以说「同一机制的类比」是稳的，说「Cromwell 规则的推论」就是过度引用，严格讲它并不覆盖似然取零这一支。
>
> 跨课程（实分析 / 统计学的正则性条件）：支撑依赖参数会破坏「积分号下求导」的可交换性，$\frac{d}{d\theta}\int f_{X|\Theta}(x\mid\theta)\,dx$ 会多出边界项，即 Leibniz 规则的边界项。这正是 Fisher information（Fisher 信息）与 score function（得分函数）的标准推导要求「支撑与参数无关」的原因，也是极大似然估计渐近正态性定理里那条反复声明却少被解释的 regularity condition（正则性条件）。本例的后验在 $x\le\theta\le1$ 上连续，却在 $\theta=x$ 处有由指示函数造成的跳变，任何对该点求导的操作都得先说明如何处理它。
>
> 反例与常见误读三条。其一，别把「后验在这里为零」读成「后验在这里很小」：前者是硬零，后者还能被数据修正。其二，别把「一次观测剪掉整个 $[0,x)$」读成「观测越极端知识越多」：$x$ 越接近 $1$，$\lvert\log x\rvert\to0$，密度在 $\theta=1$ 附近被抬得越高，这是后验更尖（更集中），不是信息量更大。其三，$n$ 次观测要剪的是 $\theta<\max_i x_i$，因为约束 $\theta\ge x_i$ 要对每个 $i$ 同时成立，取交集即把下界取为各 $x_i$ 的最大值。
>
> 正文有一处记号问题必须标出。位置改用内容指认，不再写行号，因为行号随分批改动整体漂移、已经全部对不上：正文先把 $x$ 用在观测向量 $(x_1,\dots,x_n)$ 里，随后又写「其中 $x$ 表示各次迟到时长的最大值」并给出 $x=\max\{x_1,\dots,x_n\}$；后文所有 $x\le\theta\le1$ 用的都是「最大值」这一含义，而页内的灰色衔接注却称原文用 $\bar x$ 表示最大值。三处说法并存，读者极易把 $x\le\theta\le1$ 误读成逐分量条件。数学结论不受影响，因为 $x$ 取最大值时 $x_i\le x\le\theta$ 自动蕴含每个 $x_i\le\theta$，但 notation overload（记号过载）应统一记为 $\bar x=\max_i x_i$。⚠ 需回查 PDF p422 的原始印刷式确认原文符号。

现在考虑一个涉及前 $n$ 次约会的变体。假设朱丽叶每次都迟到一段随机的时长 $X_1, \ldots, X_n$，这些时长在给定 $\Theta = \theta$ 的条件下，都在区间 $[0, \theta]$ 上均匀分布，并且条件相互独立（conditionally independent）。记 $X = (X_1, \ldots, X_n)$，$x = (x_1, \ldots, x_n)$。与 $n = 1$ 的情形类似，我们得到

```math
f_{\Theta}(\theta)\, f_{X|\Theta}(x \mid \theta) =
\begin{cases}
1/\theta^n, & \text{若 } x \le \theta \le 1,\\
0, & \text{其他情形,}
\end{cases}
```

其中 $x$ 表示各次迟到时长的最大值，即

```math
x = \max\{x_1, \ldots, x_n\}.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这句话的实质是「似然只通过一个标量依赖数据」。正文在书页 p422 把 $n$ 次观测的分子写成 $1/\theta^n$（当 $x\le\theta\le1$），并说明「其中 $x$ 表示各次迟到时长的最大值」。为什么 $n$ 个似然相乘会退化成一句「$\theta$ 不小于最大值」：每个因子 $f_{X_i|\Theta}(x_i\mid\theta)=1/\theta$ 的支撑是 $0\le x_i\le\theta$，$n$ 个支撑取交就是 $\min_i x_i\ge0$ 与 $\max_i x_i\le\theta$ 两条，密度值相乘给出 $\theta^{-n}$。于是整条似然可写成 $\theta^{-n}\mathbf 1\{\theta\ge\max_i x_i\}\mathbf 1\{\min_i x_i\ge0\}$：数据只通过 $\max$（与一个平凡的下界条件）进场，中间每个 $x_i$ 的具体取值都不再重要。
>
> 这就是 factorization theorem（因子分解定理）的实例。$T$ 是 sufficient statistic（充分统计量），当且仅当似然能写成 $g(T(x),\theta)h(x)$ 的形状；本例取 $T(x)=\max_i x_i$、$g(T,\theta)=\theta^{-n}\mathbf 1\{\theta\ge T\}$、$h(x)=\mathbf 1\{\min_i x_i\ge0\}$ 即可。历史坐标：Fisher 在 1922 年的 On the mathematical foundations of theoretical statistics 里提出 sufficiency（充分性）概念并给出因子分解判别，Neyman 1935 给出一种形式，Halmos 与 Savage 1949 用 Radon–Nikodym 导数把它推广到一般的 dominated family（受控族）。所以书上常写的 Fisher–Neyman factorization（Fisher–Neyman 因子分解），严格版本属于 Halmos–Savage。
>
> 命名模板（这里要顺手纠正一个术语误用）：sufficient（充分）的意思不是「够用」，而是「相对于参数无损」——只要知道 $T(x)$，后验 $f_{\Theta|X}(\theta\mid x)$ 与用全样本算出来的完全相同。更锋利的等价说法是：$T$ 充分，当且仅当给定 $T$ 之后 $X$ 的条件分布不依赖 $\theta$。原注紧接着说「即 $T$ 以外的部分是 ancillary（辅助的）」，这句把两个概念焊在了一起。ancillary（辅助统计量）的定义是「自身的分布不依赖 $\theta$ 的统计量」，讲的是某个统计量的边缘分布；而充分性的等价刻画讲的是给定 $T$ 之后的条件分布，两者不是同义词，也不能互相替换。本例里 $h(x)=\mathbf 1\{\min_i x_i\ge0\}$ 在模型成立时恒等于 $1$，它确实不携带参数信息，但它不属于 ancillary（辅助统计量）的典型用法，因为它的分布只取决于样本量、与 $\theta$ 无关这件事在这里是平凡的。
>
> 为什么是最大值而不是均值，要看这个族的结构。$X_i$ 在 $[0,\theta]$ 上均匀，参数只移动区间的右端点、不改形状，所以密度值 $\theta^{-n}$ 对任何样本都一样，数据唯一能做的事是指出「$\theta$ 必须落在哪里」——信息全部装在支撑里。对照正态模型 $X_i=\Theta+W_i$：形状随参数平移，密度值随 $x_i-\theta$ 变化，对数似然对 $\theta$ 求导得 $\sum_i(x_i-\theta)/\sigma_i^2$，于是充分统计量是（加权）样本均值。一句话：location family（位置族）看均值，endpoint family（端点族）看极值。
>
> 跨课程（CLRS / 算法）：$\max$ 只需 $n-1$ 次比较、$O(n)$ 时间、$O(1)$ 额外空间，读一遍顺带维护即可；而全体 order statistics（顺序统计量）$x_{(1)},\dots,x_{(n)}$ 要 $O(n\log n)$ 排序才拿得到。两者都无损（sufficient 不唯一：任何 $T$ 的一一函数仍充分），但代价差一个 $\log n$，数据约简的全部价值就在这个差上。CLRS 第 9 章把这件事推到极限：最大值有确定性的线性时间算法，中位数则要先设计 median of medians（中位数的中位数）才有线性时间保证。
>
> 反例三条。其一，区间若改成 $[\theta,\theta+1]$，充分统计量变成 $(\min_i x_i,\max_i x_i)$ 这个二元组，只留 $\max$ 会丢掉下界信息；这个族不是 exponential family（指数族），却仍有有限维充分统计量，可见「充分」比「指数族」弱。其二，观测不独立时乘积不分解，$\max$ 立刻失效。其三，若参数还改变形状（例如 Beta density（Beta 密度）里的 $\alpha$ 同时影响峰值与陡度），$\max$ 与参数完全无关，谈不上充分。
>
> 对后文而言，这条结论只用到一层：后验形如 $c(x)\theta^{-n}$，而 $c(x)$ 只依赖那个标量 $x$。于是「记住 $n$ 次观测」在存储上退化成「记住一个数」，这也是下一条注可以安心只讨论 $c(x)$ 的原因——数据压缩发生在计算归一化常数之前，而不是之后。
>
> 最后标一处极易误读的记号：正文那行 $x\le\theta\le1$ 里的 $x$ 是最大值，不是任一分量。若读成「每个 $x_i$ 都要落在 $[x,\theta]$」，就会同时要求 $x_i\ge x$ 与 $x=\max_i x_i$，除最大的那个以外全部自相矛盾。这条与上一条注末尾指出的 notation overload（记号过载）是同一个问题的两面。

后验 PDF 为

```math
f_{\Theta|X}(\theta \mid x) =
\begin{cases}
\dfrac{c(x)}{\theta^{n}}, & \text{若 } x \le \theta \le 1,\\
0, & \text{其他情形,}
\end{cases}
```

其中 $c(x)$ 是仅依赖于 $x$ 的归一化常数（normalizing constant）：

```math
c(x) = \frac{1}{
\displaystyle\int_{x}^{1} \dfrac{1}{(\theta')^{n}}\, d\theta'
}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 部分损坏] 本页末尾归一化常数公式 `c(x) = 1 / ∫_{x}^{1} (1/(θ')^n) dθ'` 的积分限在 OCR 中被切碎（仅见 `Jx (O,)n dO` 等残片），现按 §8.1 的标准推导补全为关于 $\theta'$ 从 $\bar{x}$ 到 $1$ 的积分；原文以 $\bar{x}$ 表示 $\max\{x_1,\ldots,x_n\}$，其归一化常数仅依赖 $x$，未引入原文之外的数值。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p423）：本页例 8.2 的 $n$ 次约会推广已给出归一化常数 $c(x)$ 的积分表达式，下一页将完成再次用后验归一化得到显式结果（$\theta^{\,1-n}/\lvert\log x\rvert$ 等）的收尾。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 定义先说清。正文把 $n$ 次观测的后验写成 $c(x)/\theta^n$（$x\le\theta\le1$），其中 $c(x)=1/\int_x^1(\theta')^{-n}d\theta'$（书页 p422 末行那个归一化常数式，页内灰色说明已交代其积分限在 OCR 中被切碎、现按 §8.1 的标准推导补全）。这个 $c(x)$ 就是 Bayes' rule（贝叶斯准则）的分母，也叫 marginal likelihood（边缘似然）或 evidence（证据）。它不是可有可无的尾巴，而是把「密度」变成「概率密度」的那把尺子。
>
> 算一遍，别只信符号。$n\ne1$ 时 $\int_x^1(\theta')^{-n}d\theta'=\left[(\theta')^{1-n}/(1-n)\right]_x^1=\frac{x^{1-n}-1}{n-1}$，故 $c(x)=\frac{n-1}{x^{1-n}-1}$。取 $n=2$ 验算：$c=x/(1-x)$，则 $\int_x^1\frac{x}{1-x}\cdot\frac{d\theta}{\theta^2}=\frac{x}{1-x}\cdot\frac{1-x}{x}=1$，对。$n=1$ 是退化情形：$\int_x^1 d\theta/\theta=\lvert\log x\rvert$，与正文写成 $1/(\theta\lvert\log x\rvert)$ 的那一式一致。$n=1$ 必须单独算的理由是 $1-n=0$ 处出现除零，不是因为排版习惯。
>
> 第一性原理：分子定形状，分母定尺度。贝叶斯准则里 $\theta$ 只出现在分子；作为 $\theta$ 的函数，后验的形状完全由 $f_\Theta(\theta)f_{X|\Theta}(x\mid\theta)$ 决定，$c(x)$ 只是一个与 $\theta$ 无关的缩放因子。工程上因此常写 $f_{\Theta|X}\propto f_\Theta f_{X|\Theta}$（proportional to，正比于）。但正比号丢掉的只是「$\theta$ 方向的尺度」：一旦要算期望、要算区间概率、要比较不同 $x$ 下的似然，$c(x)$ 就必须回来。
>
> 同一个积分有两种用途。$c(x)^{-1}=\int f_\Theta(\theta)f_{X|\Theta}(x\mid\theta)d\theta$ 是模型对观测 $x$ 的 marginal likelihood（边缘似然）：把参数积掉之后剩下的、只依赖数据的东西。做参数估计时它叫 normalizing constant（归一化常数），做模型比较时它叫 evidence（证据），两个模型取比值即 Bayes factor（贝叶斯因子）。所以看到这个积分先问一句：这里是在估 $\theta$，还是在挑模型。
>
> 命名模板：normalizing constant（归一化常数）指把密度积分凑成 $1$ 的那个数；marginal likelihood（边缘似然）指积分消元之后剩下的似然——marginal（边缘）在这里与概率论中「边缘分布」是同一个动作，把不要的变量积掉。两者是同一个对象在两个场景下的名字。
>
> 跨课程（统计物理 / 配分函数）：把被积函数看成权重 $e^{-\beta E(\theta,x)}$，则 $c(x)^{-1}$ 就是 partition function（配分函数）$Z$，而 $-\log Z$ 是 free energy（自由能）。这不是牵强类比：模型的 evidence（证据）与统计系统的配分函数在数学上是同一个积分，两者的对数都在做「对不可见变量求和」；模型比较里 $-\log c(x)$ 与自由能一样，同时惩罚拟合得不好与参数空间太大，这正是 BIC 这类准则的来源。理解了配分函数为什么难算（通常没有闭式），就理解了为什么贝叶斯模型比较在计算上比参数估计难一个量级。
>
> 跨课程（数值 / CSAPP）：这里原注有两个数必须更正。其一，$x=0.5$、$n=1100$ 时 $x^{1-n}=2^{1099}$，实算为 $6.7914926\times10^{330}$，不是注里写的 $5.4\times10^{330}$；后者偏小约四分之一。结论方向不变，因为它仍然远高于 IEEE 754 binary64 的最大有限值 $1.7977\times10^{308}$，直接变 inf，于是 $c=0$、后验恒零。其二，原注说「$x$ 接近 $1$ 时是 $0/0$ 型」，这句不成立：$n>1$ 时分子 $n-1$ 固定，而 $x^{1-n}\to1$，分母 $x^{1-n}-1\to0^{+}$，所以 $c(x)\to+\infty$，是「常数除以趋零的正数」，不是 $0/0$。相应地，对数域的公式也必须改：原注写的 $\log(1-x^{1-n})$ 在 $x<1$ 时是对负数取对数，根本没有定义，正确写法是 $\log c=\log(n-1)-\log(x^{1-n}-1)$。工程上再稳一层：令 $y=(n-1)(-\log x)>0$，则 $x^{1-n}-1=e^{y}-1$，用 expm1 求它、用 log1p 求 $\log x=\mathrm{log1p}(x-1)$，于是 $\log c=\log(n-1)-y-\mathrm{log1p}(-e^{-y})$，两个方向都不溢出。这不是洁癖：$n=1$ 时后验只依赖 $\lvert\log x\rvert$，若 $x$ 与 $1$ 差到 $10^{-16}$ 量级，朴素算法直接给 $0$，后验算出无穷大。
>
> 有一处必须保留原注的更正：原先这条注说「若换成 Beta 先验（见 Example 8.4），分母会闭合成 Beta 函数」，这不成立。本例的似然是截断形式 $\theta^{-n}\mathbf 1\{\theta\ge x\}$，不是二项式的 $\theta^k(1-\theta)^{n-k}$；Beta 先验乘上去得到的是「截断在 $[x,1]$ 上的 Beta density（Beta 密度）」，需要 incomplete beta function（不完全 Beta 函数）才能归一，结果既不是 Beta 密度，也没有闭式。conjugacy（共轭）是「先验族 × 似然族」的配对性质：Example 8.4 里配对的是二项似然与 Beta 先验，不是这个模型。
>
> 顺带一个记号提醒：正文同时出现 $c$（Example 8.4 中不依赖 $\theta$ 的常数）与 $c(x)$（本例依赖数据的归一化常数）。前者是纯常数，后者是数据的函数，二者在往后的公式里都还会出现，别把「$c$ 可以提出积分号」这个性质错用到 $c(x)$ 上。
>
> 反例两条。其一，只比分子不归一化，得到的不是概率密度：$E[\Theta\mid X=x]$、$P(\Theta\le0.5\mid X=x)$ 都算不出来，而且「密度值大」不等于「概率大」，后者要把密度在一个区间上积分。其二，把 $c(x)$ 当常数提出积分号、随后又忘了它依赖 $x$，于是在比较两个观测时把两个不同分母当成同一个，得出「观测越极端后验越高」这类结论——这正是漏写 $x$ 的典型后果。
<!-- ===== PDF p423 ===== -->
<span style="color:#c0392b;">**第八章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）（续）**</span>

> <span style="color:#7f8c8d;">本页为书页 415，承接上一页 §8.1 的正文，转入一个新的例题 **Example 8.3——正态随机变量公共均值的推断**。例题在本页起笔并推演至分子配平方化简与 $m$、$v$ 的表达式，其「后验为正态分布、均值为 $m$、方差为 $v$」的结论收尾出现在下一页。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.3．正态随机变量公共均值的推断（Inference of a Common Mean of Normal Random Variables）**</span>

我们观测到一族随机变量 $X = (X_1, \ldots, X_n)$，它们具有一个未知的公共均值（common mean），我们希望推断出该均值之值。我们假定：在公共均值取值给定的条件下，这些 $X_i$ 服从正态分布（normal）且相互 independent（独立），其方差（variances）$\sigma_1^2, \ldots, \sigma_n^2$ 已知。在这种问题的贝叶斯做法中，我们把公共均值建模为一个随机变量 $\Theta$，并给定一个先验分布（prior）。为具体起见，我们假设该先验为正态先验（normal prior），其均值 $X_0$ 与方差 $\sigma_0^2$ 均已知。

为了以后引用方便，让我们指出：我们的模型等价于如下形式

```math
X_i = \Theta + W_i ,\qquad i = 1, \ldots, n,
```

其中随机变量 $\Theta, W_1, \ldots, W_n$ 相互独立且服从正态分布，其均值与方差均已知。特别地，对任意取值 $\theta$，有

```math
E[W_i] = E[W_i \mid \Theta = \theta] = 0 ,
```

对 $i = 1, \ldots, n$ 成立。这种类型的模型在许多涉及对未知量进行多次独立测量的工程应用中很常见。

根据我们的假设，我们有

```math
f_{\Theta}(\theta) = c_1 \cdot \exp\!\left\{ -\frac{(\theta - X_0)^2}{2\sigma_0^2} \right\} ,
```

以及

```math
f_{X\mid\Theta}(x\mid\theta) = c_2 \cdot \exp\!\left\{ -\frac{(x_1 - \theta)^2}{2\sigma_1^2} \right\} \cdots \exp\!\left\{ -\frac{(x_n - \theta)^2}{2\sigma_n^2} \right\} ,
```

其中 $c_1$ 与 $c_2$ 是不依赖于 $\theta$ 的归一化常数（normalizing constants）。我们引用贝叶斯准则（Bayes' rule）

```math
f_{\Theta\mid X}(\theta\mid x)
= \frac{ f_{\Theta}(\theta)\, f_{X\mid\Theta}(x\mid\theta) }
       { \displaystyle\int f_{\Theta}(\theta')\, f_{X\mid\Theta}(x\mid\theta')\, d\theta' } ,
```

并注意到分子项 $f_{\Theta}(\theta)\, f_{X\mid\Theta}(x\mid\theta)$ 具有如下形式

```math
c_1 c_2 \cdot \exp\!\left\{ - \sum_{i=0}^{n} \frac{(x_i - \theta)^2}{2\sigma_i^2} \right\} .
```

经过一些代数运算——这一步涉及在指数内部完成配平方（completing the square）——我们得出分子具有如下形式

```math
d \cdot \exp\!\left\{ -\frac{(\theta - m)^2}{2v} \right\} ,
```

其中

```math
m = \frac{ \displaystyle\sum_{i=0}^{n} x_i / \sigma_i^{2} }
        { \displaystyle\sum_{i=0}^{n} 1 / \sigma_i^{2} } ,
\qquad
v = \frac{ 1 }{ \displaystyle\sum_{i=0}^{n} 1 / \sigma_i^{2} } .
```

> <span style="color:#7f8c8d;">说明：上面求和的下标从 $i = 0$ 起算，其中第 $0$ 项对应先验（prior）——即取 $x_0 = X_0$（先验均值）、$\sigma_0^2$（先验方差）。由分子的形式可知，后验密度 $f_{\Theta\mid X}(\theta\mid x) \propto \exp\{-(\theta - m)^2/(2v)\}$ 是均值为 $m$、方差为 $v$ 的正态密度；该结论的完整陈述收尾于下一页。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损伤] 本页原排版较密，多处下标/上标被当作每行首字符切行（如 $\sigma_0^2$ 的指数、$X_0$ 的下标、求和 $\sum_{i=0}^{n}$ 的行内下/上标、以及 $x_i/\sigma_i^2$ 的上下标），OCR 中散落为 `Xo`、`(7?`、`(75`、`(7;`、`i=O`、`Xn` 等碎片；方差指标与求和上下标经与公式语义核对后按规范 LaTeX 复原，未臆造任何数值。全页数值仅 $\frac{1}{2}$、系数 $c_1, c_2, d$、先验均值 $X_0$ 与各 $\sigma_i^2$，其余为符号推导。</span>

> <span style="color:#7f8c8d;">衔接下一页（PDF p424）：Example 8.3 在本页完成先验/似然展开、配平方化简并给出 $m$、$v$ 之后，下一页给出其收尾结论——后验分布即均值为 $m$、方差为 $v$ 的正态分布，并对其含义（先验与各观测按方差加权融合）加以诠释。</span>
<!-- ===== PDF p424 ===== -->

<span style="color:#7f8c8d;">§8.1 贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）续页。本页为文献页 416，属第 8 章（Chap. 8）贝叶斯统计推断（Bayesian Statistical Inference）。本页承接上一页，继续 **Example 8.3**（正态先验、正态观测）收尾段——证明后验为正态密度，随后转入对该例「后验与先验同族、可递归推断」性质的讨论（故标题带「（续）」）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.3（续）——正态先验、已知方差的独立正态观测（Normal Prior, Independent Normal Observations of Known Variance）**</span>

其中 $d$ 是一个常数，它依赖于 $X_i$ 却不依赖于 $\theta$。由于贝叶斯准则（Bayes' rule）中的分母项对二者都没有依赖，我们得出结论：后验概率密度函数（posterior PDF）具有如下形式

```math
f_{\Theta|X}(\theta\mid x) \;=\; a \phantom{0} \exp\left\{-\frac{(\theta-m)^2}{2v}\right\},
```

其中 $a$ 是某个归一化常数（normalizing constant），它依赖于 $X_i$ 但不依赖于 $\theta$。我们认出这是一个正态（normal）概率密度函数，于是得出结论：后验概率密度函数是均值为 $m$、方差为 $v$ 的正态分布。

作为一个特殊情形，假设 $\sigma_0^2, \sigma_1^2, \ldots, \sigma_n^2$ 共有一个公共值 $\sigma^2$。那么，$\Theta$ 的后验概率密度是正态的，其均值与方差分别为

```math
m \;=\; \frac{x_0 + \cdots + x_n}{n+1}, \qquad v \;=\; \frac{\sigma^2}{n+1}.
```

在这种情形下，先验均值 $x_0$ 就像又一个观测一样，对确定 $\Theta$ 的后验均值 $m$ 起着同样分量的作用。还可以注意到，$\Theta$ 的后验概率密度函数的标准差随观测数目增大而趋于零，其粗略速率为 $1/\sqrt{n+1}$。

如果方差 $\sigma_i^2$ 各不相同，后验均值 $m$ 的公式仍然是各 $X_i$ 的加权平均（weighted average），但对那些方差较小的观测赋予了更大的权重。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先把公式摆平。正文给出后验为均值 $m$、方差 $v$ 的正态，其中 $m=\frac{\sum_{i=0}^n x_i/\sigma_i^2}{\sum_{i=0}^n 1/\sigma_i^2}$、$v=\frac{1}{\sum_{i=0}^n 1/\sigma_i^2}$，求和从 $i=0$ 起、第 $0$ 项是先验（$x_0$ 为先验均值、$\sigma_0^2$ 为先验方差）。随后那句「对那些方差较小的观测赋予了更大的权重」就是全部内容，但它值得掰开：把「置信」翻译成「精度」这件事，正是这里完成的。
>
> 唯一的实质结构是精度可加。记 $\tau_i=1/\sigma_i^2$，则 $1/v=\tau_0+\tau_1+\cdots+\tau_n$，而 $m=\frac{\sum_i\tau_ix_i}{\sum_i\tau_i}$。也就是说：后验 precision（精度）等于各来源精度之和，均值是按精度配重的加权平均，方差是总精度的倒数。其余全是算术。
>
> 为什么倒数是权重？看对数似然的曲率。$\log f_{X_i|\Theta}(x_i\mid\theta)=-\frac{(x_i-\theta)^2}{2\sigma_i^2}+\mathrm{const}$，对 $\theta$ 求二阶导得 $-1/\sigma_i^2$，这正是一个观测携带的 observed information（观测信息，取负号的二阶导）。独立观测的对数似然相加，二阶导也相加，于是精度相加。所以「按 $1/\sigma^2$ 加权」不是人为约定，而是二次型对数似然可加的必然结果；若似然换成 Cauchy（柯西）之类重尾形式，这个可加性立刻消失，后验也不再是正态。
>
> 特例自检。所有 $\sigma_i^2$ 都等于 $\sigma^2$ 时，$m=(x_0+\cdots+x_n)/(n+1)$、$v=\sigma^2/(n+1)$，先验均值与一个真实观测同权。注意正文那句「其粗略速率为 $1/\sqrt{n+1}$」说的是 standard deviation（标准差）：方差按 $1/(n+1)$ 收缩，标准差才按 $1/\sqrt{n+1}$，两者差一个平方。把这两句混起来是这类题最常见的口误。
>
> 等价地，这是加权最小二乘。最小化 $S(\theta)=\sum_{i=0}^n w_i(x_i-\theta)^2$，一阶条件 $\sum_iw_i(x_i-\theta)=0$ 给出 $\hat\theta=\sum_iw_ix_i/\sum_iw_i$，取 $w_i=\tau_i$ 就得到 $m$。至于 $v$，要先把 $S$ 展成标准二次式：$S(\theta)=(\sum_iw_i)\theta^2-2(\sum_iw_ix_i)\theta+\mathrm{const}$，配平方得 $S(\theta)=(\sum_iw_i)(\theta-m)^2+\mathrm{const}$。原注在这里写错了一处：它说「目标函数在极值点的二阶导 $2\sum_iw_i$ 给出 $v$」，但二阶导给出的是曲率、也就是精度，方差是曲率的倒数的两倍，即 $v=2/S''=1/\sum_iw_i$；把 $2\sum_iw_i$ 直接当成方差，量纲与方向都不对，正确读法是 $\exp(-S/2)$ 的方差。修好这一处之后结论仍然成立：在这个模型里，贝叶斯后验均值与频率派的 weighted least squares（加权最小二乘，WLS）点估计是同一个数，不是巧合，两边都在解同一个二次型。
>
> 跨课程（估计理论 / 18.06）：Gauss 在 Theoria combinationis（1821 与 1823 两部分）里证明最小二乘的最优性，Aitken 在 1935 年的 On Least Squares and Linear Combinations of Observations 中把它推广到误差相关、方差不等的情形，即 generalized least squares（广义最小二乘，GLS）；Gauss–Markov 定理的当代表述是：误差零均值、同方差、互不相关时，OLS 是 best linear unbiased estimator（BLUE，最佳线性无偏估计）。本注对应的是对角协方差的异方差情形，权重矩阵为 $\mathrm{diag}(\tau_i)$；协方差非对角时换成 $\Sigma^{-1}$。用 18.06 的话说，这是把内积换成 $\langle u,v\rangle_\Sigma=u^\top\Sigma^{-1}v$ 之后再做投影，投影公式形式不变。
>
> 反例：独立性被破坏时权力反转。$1/\sigma_i^2$ 的推导预设「给定 $\Theta$ 下观测 conditionally independent（条件独立）」，只有这样才能把对数似然相加。若两个观测共享同一份噪声，例如 $X_1=\Theta+Z$ 与 $X_2=\Theta+Z$ 是同一台仪器同一时段的漂移，它们其实只提供一份证据，却按两份计，总精度被高估成两倍，后验方差被压到真值的一半，于是 overconfidence（过度自信）。正确做法是写协方差 $\mathrm{Cov}=\sigma_Z^2\mathbf 1\mathbf 1^\top+\mathrm{diag}(\varepsilon_i^2)$ 并用 $\Sigma^{-1}$ 加权，公共分量于是只被计一次。这正是正文模型 $X_i=\Theta+W_i$ 里「$W_i$ 相互独立」这句话的实际分量：它不是技术假设，而是权重的合法性来源。
>
> 正文检查。求和下标从 $0$ 起、灰色说明指出第 $0$ 项是先验，与推导一致，此处无错。需要提防的是页内那条 OCR 说明里提到的上下标碎裂：若照着碎掉的 OCR 把 $\sigma_i^2$ 抄成 $\sigma_i$，权重就变成 $1/\sigma_i$，与方差差一个量纲，最终仍能算出一个「数」，但那个数既不是 $m$ 也不是任何有意义的估计。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上文特殊情形（公共方差 $\sigma^2$，$m=(x_0+\cdots+x_n)/(n+1)$、$v=\sigma^2/(n+1)$）中，原页角标碎裂（如 `x_0...x_n` 的 `n+1` 分母、`1/\sqrt{n+1}` 速率项所对应的字面 `1/JTi`），已按后验 $\sigma^2/(n+1)$ 推导的必然结论与正文语义还原为 $\sqrt{n+1}$，未臆造原文未出现的数值。</span>

前面这个例子具有一个显著性质：$\Theta$ 的后验分布（posterior distribution）与先验分布（prior distribution）同属一族，即正态分布族（family of normal distributions）。这一点之所以诱人，原因有二：

- **（a）** 后验只需用两个数——均值与方差——即可刻画。
- **（b）** 解的形式为高效的递归推断（recursive inference）打开了可能。设想在 $x_1, \ldots, x_n$ 被观测之后，又获得了一个额外的观测 $x_{n+1}$。我们不必从零开始求解推断问题，而是可以把 $f_{\Theta \mid x_1, \ldots, x_n}$ 视作我们的先验，并用这个新观测来获取新的后验 $f_{\Theta \mid x_1, \ldots, x_n, x_{n+1}}$。然后即可把 Example 8.3 的解应用于这个新问题。于是可以合理地（并且能够被正式确立）认为，$\Theta$ 的新后验将具有均值

```math
\frac{(m/v) + (x_{n+1}/\sigma_{n+1}^2)}{(1/v) + (1/\sigma_{n+1}^2)}
```

以及方差

```math
\frac{1}{(1/v) + (1/\sigma_{n+1}^2)},
```

其中 $m$ 和 $v$ 是旧后验 $f_{\Theta \mid x_1, \ldots, x_n}$ 的均值与方差。

「后验与先验同属一族分布」这种情形并不常见。除正态族之外，另一个突出的例子涉及抛硬币/伯努利试验（Bernoulli trials）与二项分布（binomial distributions）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 递推式先摆出来。设旧后验为均值 $m$、方差 $v$，新观测为 $x_{n+1}$、其噪声方差 $\sigma_{n+1}^2$，则新后验的均值与方差分别是 $\frac{m/v+x_{n+1}/\sigma_{n+1}^2}{1/v+1/\sigma_{n+1}^2}$ 与 $\frac{1}{1/v+1/\sigma_{n+1}^2}$（正文在书页 p423 给出的就是这两式，紧接着一句「其中 $m$ 和 $v$ 是旧后验的均值与方差」）。它们不是新公式，只是把上一条注的精度加法再做一遍：$\tau_{\mathrm{new}}=\tau_{\mathrm{old}}+\tau_{n+1}$，其中 $\tau=1/v$。所谓「递归」，在算术层面就只有这一行。
>
> 递归为什么可能，要靠一个维数论证。一般情形下后验是 $[0,1]$ 上的一条曲线，把它当先验传下去等于传递无穷维对象，无法计算。这里只传两个数，是因为正态族对「乘似然再归一化」这个操作 closed（封闭），也就是 conjugacy（共轭）。封闭性的通行刻画是 exponential family（指数族），其 sufficient statistic（充分统计量）维数固定；DKP theorem（Fisher–Darmois–Koopman–Pitman 定理）说：在光滑、支撑不依赖参数、密度处处非零的条件下，有限维充分统计量存在当且仅当这族是指数族。正态族的 $T(x)=(x,x^2)$ 恰好两维，对应 $(m,v)$ 两个数。
>
> 命名模板：recursive inference（递归推断）指用上一轮的后验充当这一轮的先验，用一次局部更新替代全量重算。控制论把同一个东西叫 state（状态），定义是「足以预测未来的最小信息集」；正态情形下状态就是 $(m,v)$，两套语言指同一个对象。
>
> 跨课程（Kalman filter，卡尔曼滤波）：离散 Kalman filter（卡尔曼滤波，Kalman 1960）的两步与这里逐字对应。predict（预测）步 $P^{-}=P+Q$，精度写成 $1/P^{-}=1/(P+Q)$ 就变宽；update（更新）步 $1/P=1/P^{-}+1/R$、$K=P^{-}/(P^{-}+R)$、$x^{+}=x^{-}+K(z-x^{-})$。把 $\sigma_{n+1}^2$ 认成测量噪声 $R$、把 $v$ 认成预测方差 $P^{-}$，本注的公式就是它的全部内容。
>
> 顺带读懂增益的形态。$K=P^{-}/(P^{-}+R)$ 与 $K=\tau_R/(\tau_{P^{-}}+\tau_R)$ 等价，即「新测量的精度在总精度中的份额」。这句话给出增益的概率含义：后验均值等于把旧信念按份额让给新测量，让多少完全由两边谁更准决定。$R\to0$（测量无噪声）时 $K\to1$、后验直接跳到 $z$；$R\to\infty$ 时 $K\to0$、后验纹丝不动。两个极限都能一眼验算，是检验公式有没有写反的最快办法。
>
> 历史坐标。Kalman 那篇是 A New Approach to Linear Filtering and Prediction Problems（Trans. ASME, J. Basic Eng. 82(1): 35–45, 1960），它把 Wiener 在二战期间发展起来的频域滤波搬到状态空间与时域，使非平稳与非线性的推广成为可能。而在贝叶斯这条线上，「旧后验当先验」的想法更早以 sequential Bayes（序贯贝叶斯）的形式出现：数据一条一条来，推断就该一条一条更新，全量重算是没有必要的工作量。
>
> 反例与定理边界三条。其一，模型错了递推也照跑，后验方差仍按 $1/(n+1)$ 单调收缩到 $0$——精度累加的只是「假设的方差」，与数据是否真来自该模型无关，所以「方差趋零」只证明信息被用完了，不证明估计是对的。其二，参数随时间漂移（非平稳）时，窄化的后验会锁死在旧值上，必须加过程噪声 $Q>0$ 或 forgetting factor（遗忘因子），让旧信息按几何级数衰减。其三，非高斯、非共轭时「递归」要退化成 particle filter（粒子滤波）或变分近似，状态不再是两维。
>
> 数值上的要点。精度随 $n$ 线性增长，$n$ 到 $10^8$ 量级时 $v\sim10^{-8}\sigma^2$，仍在 double 范围内；真正的麻烦在累加：$\tau_0+\tau_1+\cdots$ 逐项相加时大数吃小数，量级差到 $10^{16}$ 之后小数项直接被舍掉，用 Kahan 求和、或干脆只维护 $\tau$ 而不维护 $v$，都能缓解。工程实现普遍存信息矩阵（精度）而非协方差，原因就在这里：加法比除法稳。
>
> 必须更正原注一处。原先写「后验方差会随 $n$ 大约按 $1/\sqrt n$ 收紧到零」，把两个量混了：方差按 $1/n$ 收缩，标准差按 $1/\sqrt n$ 收缩。正文说的那句「其粗略速率为 $1/\sqrt{n+1}$」主语是 standard deviation（标准差），本身正确；把 $1/\sqrt n$ 安到方差头上才是错的。这类混淆在答案里很常见，验算办法是取 $n=4$ 到 $n=16$：方差应缩到四分之一，标准差只缩到二分之一。
<!-- ===== PDF p425 ===== -->

<span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）（续）**</span>

> <span style="color:#7f8c8d;">本页为书页 p417，属 §8.1 中段。承接上一页关于连续型未知参数的贝叶斯推断论述，本页给出关于「硬币偏置的 Beta 先验（Beta priors on the bias of a coin）」的 **Example 8.4**（涉及连续型参数估计），页末转入「二进制假设检验」的离散例子过渡段。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.4——硬币偏置的 Beta 先验（Beta Priors on the Bias of a Coin）**</span>

我们希望估计一枚有偏硬币（biased coin）抛出正面的概率，将其记为 $\theta$。我们把 $\theta$ 建模为某个随机变量 $\Theta$ 的取值，且 $\Theta$ 有已知的先验概率密度函数（prior PDF）$f_\Theta$。我们考虑 $n$ 次独立的抛掷，并令 $X$ 表示观察到的正面次数。

由贝叶斯准则（Bayes' rule），$\Theta$ 的后验概率密度函数（posterior PDF）在 $\theta \in [0, 1]$ 上具有如下形式：

```math
f_{\Theta|X}(\theta\mid k) = c\, f_\Theta(\theta)\, p_{X|\Theta}(k\mid \theta)
= d\, f_\Theta(\theta)\,\theta^k(1-\theta)^{n-k},
```

其中 $c$ 是一个归一化常数（normalizing constant，与 $\theta$ 无关），而 $d = c\,\binom{n}{k}$。

现假定先验是一个具有正整数参数 $\alpha > 0$ 与 $\beta > 0$ 的 Beta 密度（beta density），形式为

```math
f_\Theta(\theta) =
\begin{cases}
\dfrac{1}{B(\alpha,\beta)}\,\theta^{\alpha-1}(1-\theta)^{\beta-1}, & \text{若 } 0<\theta<1,\\[2mm]
0, & \text{否则},
\end{cases}
```

其中 $B(\alpha,\beta)$ 是一个归一化常数，称为 Beta 函数（Beta function），由下式给出：

```math
B(\alpha,\beta) = \int_0^1 \theta^{\alpha-1}(1-\theta)^{\beta-1}\,d\theta
= \frac{(\alpha-1)!\,(\beta-1)!}{(\alpha+\beta-1)!},
```

最后一个等号可以通过分部积分（integration by parts），或通过一个概率性的论证来得到（见第 3 章 Problem 30）。于是，$\Theta$ 的后验概率密度函数具有如下形式：

```math
f_{\Theta|X}(\theta\mid k) = \frac{d}{B(\alpha,\beta)}\,\theta^{k+\alpha-1}(1-\theta)^{n-k+\beta-1},
\qquad 0 \le \theta \le 1,
```

从而它是一个参数为

```math
\alpha' = k + \alpha,\qquad \beta' = n - k + \beta
```

的 Beta 密度。

在 $\alpha = \beta = 1$ 的特例中，先验 $f_\Theta$ 是 $[0,1]$ 上的均匀密度（uniform density）。在这种情况下，后验密度是以 $k+1$ 与 $n-k+1$ 为参数的 Beta 密度。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 后验参数先摆清。正文给出 $f_{\Theta|X}(\theta\mid k)\propto\theta^{k+\alpha-1}(1-\theta)^{n-k+\beta-1}$，即后验是参数 $\alpha'=k+\alpha$、$\beta'=n-k+\beta$ 的 Beta density（Beta 密度）；在 $\alpha=\beta=1$ 的特例中它退化成 Beta$(k+1,n-k+1)$。也就是说：均匀先验（uniform density，均匀密度）加上 $k$ 次正面、$n-k$ 次反面，两个指数各比计数多 $1$。
>
> 先把记账约定声明在明处，本条与后面讲抛硬币对照、以及 §8.3 末那条线性 LMS 的注，全部按同一套算，不许串。这里采用 $a=\alpha-1$ 版：Beta$(\alpha,\beta)$ 等价于「在均匀先验之上看过 $a=\alpha-1$ 次正面、$b=\beta-1$ 次反面」。选它的理由有两条：它让伪计数（pseudo-count，伪计数）与数据计数落在同一个加法结构里（后验参数等于先验的 $a$、$b$ 加上 $1$，再加上数据计数），并且 $\alpha=\beta=1$ 时它诚实地给出零个虚拟观测。另一套 $\alpha$ 版（先验等价于 $\alpha$ 次正面、$\beta$ 次反面）也自洽，只是把「下一次预测」提前记成了已发生的观测；两套差整整一个试验，混用就必差一。
>
> 于是那个 off-by-one 要停一下：若按 $\alpha$ 版说「$(1,1)$ 等于预先看见一正一反」，则真看过一正一反得到的先验应是 Beta$(2,2)$，密度正比于 $\theta(1-\theta)$，中间拱起、两端压低，与均匀先验根本不是一个形状。所以本约定下 Beta$(1,1)$ 等价于「一次都没看过」，这才是准确的读法。
>
> 那「$+1$」到底从哪来？来自 predictive（预测）尺度，而不是历史计数。$E[\Theta\mid X=k]=\frac{\alpha'}{\alpha'+\beta'}=\frac{k+\alpha}{n+\alpha+\beta}$，$\alpha=\beta=1$ 时是 $\frac{k+1}{n+2}$。注意在本约定下这**不是**「先验加了一正一反」：先验的伪计数是 $\alpha-1=\beta-1=0$，可预测分布的参数却是 $\alpha$ 与 $\beta$，$+1$ 恰好是「从 $\alpha-1$ 走到 $\alpha$」这一步的影子。原注把它说成「预先看见一次正面与一次反面，所以加一不是魔数」，是自相矛盾的：真那样记账，后验会是 Beta$(k+2,n-k+2)$。准确的因果是：均匀先验在 $\theta=0$ 与 $\theta=1$ 两端的幂次为零（$\theta^0$ 与 $(1-\theta)^0$），不对端点做任何惩罚，加一来自这层零幂次，而不是来自任何虚假观测。
>
> 命名模板：pseudo-count（伪计数）、virtual sample（虚拟样本）、equivalent prior sample size（等价先验样本量）。这三个词让人混乱，正因它们分属两套记账，本注这一套记 $\alpha-1$，另一套记 $\alpha$；读任何教材都要先确认它用哪一套，否则差一，结论就全歪。
>
> rule of succession（Laplace 后继率）是这个公式最著名的用法。取 $\alpha=\beta=1$、$k=n$（$n$ 次全成功），下一次成功的预测概率是 $\frac{n+1}{n+2}$。时间线要说准，免得与后面对抛硬币的注打架：Laplace 在 1774 年的 Mémoire sur la probabilité des causes par les événements 里首次给出这条规则，1812 年的 Théorie analytique des probabilités 把它系统化，1814 年的 Essai philosophique 里用它算「太阳明天照常升起」，$n=1826213$ 天时 $\frac{n+1}{n+2}=0.99999945$。这一算成了贝叶斯方法最著名的靶子，争议不在公式而在建模：把每天的日出当成独立同分布的 Bernoulli trial（伯努利试验）本身就是极强假设。
>
> 跨课程（机器学习 / 平滑）：把加一搬到多项分布就是 Laplace smoothing（拉普拉斯平滑，亦称 add-one smoothing），$P(w)=\frac{\mathrm{count}(w)+1}{N+V}$，$V$ 为词表大小。它解决的正是 $\mathrm{count}(w)=0$ 时概率为零、进而让整个连乘归零的问题：在朴素贝叶斯里，一个未登录词就能把后验打死。这里也要说清 $+1$ 的身份：它对应对称的 $\alpha=2$、$\beta=2$，在本约定下等价于一正一反两个伪计数，在 $\alpha$ 版里则等价于各两次——所以讲「加一平滑等于一正一反」时，必须同时讲清用的是哪套记账，否则同一个公式会读出两个数。
>
> 反例与取舍。伪计数的强度不是免费的：$\alpha+\beta$ 越大先验越硬。数据多时（$n\gg\alpha+\beta$）它被稀释，影响可忽略；数据少时它主导结论。极端例子：$n=0$ 而 $\alpha=\beta=100$，后验均值为 $0.5$、方差约 $1/800$，等于「什么数据都没有，却对 $0.5$ 极度自信」。反过来，$n=0$、$\alpha=\beta=1$ 给出均匀密度与方差 $1/12$，这才是「一无所知」的诚实表达。
>
> 最后做一次自检，用正文给出的矩递推式，即 $E[\Theta^m]=B(\alpha+m,\beta)/B(\alpha,\beta)$ 那一行。由它得 $E[\Theta]=\frac{\alpha}{\alpha+\beta}$、$E[\Theta^2]=\frac{\alpha(\alpha+1)}{(\alpha+\beta)(\alpha+\beta+1)}$，故 $\mathrm{Var}=\frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$。代入 $\alpha=k+1$、$\beta=n-k+1$ 得 $\frac{(k+1)(n-k+1)}{(n+2)^2(n+3)}$；$k=n/2$ 时约为 $\frac{1}{4(n+3)}$，与 $1/n$ 同阶。这里的分母是 $n+2$ 而不是 $n+\alpha+\beta$ 的别种写法，正因为本约定已经把「各一枚」的伪计数折算进了 $\alpha-1$ 与 $\beta-1$。这条式子把「共轭给出可算的收敛速率」落到具体数字上，也是下一条注的入口。

Beta 密度经常出现在推断（inference）应用中，并具有一些有趣的性质。尤其是，若 $\Theta$ 具有正整数参数 $\alpha > 0$ 与 $\beta > 0$ 的 Beta 密度，则它的 $m$ 阶矩（$m$th moment）由下式给出：

```math
\mathbb{E}[\Theta^m]
= \int_0^1 \frac{1}{B(\alpha,\beta)}\,\theta^m\,\theta^{\alpha-1}(1-\theta)^{\beta-1}\,d\theta
= \frac{B(\alpha+m,\beta)}{B(\alpha,\beta)}
= \frac{\alpha(\alpha+1)\cdots(\alpha+m-1)}{(\alpha+\beta)(\alpha+\beta+1)\cdots(\alpha+\beta+m-1)}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页内上方 Beta 函数 $B(\alpha,\beta)$ 与积分 $\int_0^1 \theta^{\alpha-1}(1-\theta)^{\beta-1}\,d\theta = \frac{(\alpha-1)!(\beta-1)!}{(\alpha+\beta-1)!}$ 一行的 OCR 被打得极碎（如 `(a(a- +I )!(3((3- -1)!I)!` 等碎片），上方按标准 Beta 函数定义忠实还原其两个等号；各指数与阶乘项由原文「分部积分 / 概率性论证（第 3 章 Problem 30）」的说明核对，未臆造数值。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 定义先说准。conjugacy（共轭）是族与族的性质：先验族对似然族共轭，意思是「取该族中任一先验、配该族中任一似然、看任一观测，后验仍落在该族里」。注意这是族对族，不是单个分布对单个分布——这一点决定了它是设计工具而不是巧合。
>
> 代数机制只有一句话：同底幂相乘、指数相加。Beta density（Beta 密度）正比于 $\theta^{\alpha-1}(1-\theta)^{\beta-1}$，二项似然正比于 $\theta^k(1-\theta)^{n-k}$，相乘得 $\theta^{\alpha+k-1}(1-\theta)^{\beta+n-k-1}$，形状不变，参数相加。没有更深的魔法。
>
> 推广一下就能看出共轭为什么总能被造出来。指数族写成 $f(x\mid\theta)=h(x)\exp\{\eta(\theta)^\top T(x)-A(\theta)\}$，似然对参数的全部依赖只有 $\eta(\theta)^\top\sum_iT(x_i)$ 这一项；于是取先验正比于 $\exp\{\eta(\theta)^\top\chi-\psi(\chi)\}$，后验就是把 $\chi$ 换成 $\chi+\sum_iT(x_i)$。所以共轭先验族本质上是以 sufficient statistic（充分统计量）为坐标的参数族，超参数就是「虚拟的统计量和」。这条推导解释了为什么每个指数族成员都自动有一个共轭先验。
>
> 一张必须记得的对照表：Bernoulli（伯努利）与二项 → Beta；Poisson（泊松）→ Gamma（伽马）；正态均值（方差已知）→ 正态；正态方差（均值已知）→ inverse-gamma（逆伽马）；多项 → Dirichlet（狄利克雷）；指数族中的指数分布 → Gamma（伽马）。这张表的价值在于回答「该用哪个先验」——答案是似然决定的，不是审美选择。
>
> 命名模板与词源。conjugate（共轭）来自拉丁语 con-jugare（套在同一根轭上），本义「配对」。数学里「共轭」至少有三种互不相干的用法，别串成一条线：其一是复数的复共轭（把虚部取反，作用是让模长可算），其二是共轭梯度法（用一组互相「配」的方向把线性方程组解出来），其三就是这里的共轭先验（后验与先验同族）。三者共同的只有「配对」这个比喻，内容各不相同；原注在这里还举了群论中的共轭类作第四例，但那个概念要引入群、子群与群作用才讲得清，与本注要说的「乘似然后仍同族」没有可迁移的结构，故删去，改用上面三例。
>
> Beta 函数与矩构成一条完整的链条。$B(\alpha,\beta)=\int_0^1\theta^{\alpha-1}(1-\theta)^{\beta-1}d\theta=\frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}$，整数时 $\Gamma(m)=(m-1)!$ 给出正文的 $\frac{(\alpha-1)!(\beta-1)!}{(\alpha+\beta-1)!}$。阶乘式的来源是分部积分给出的递推 $B(\alpha,\beta)=\frac{\alpha-1}{\alpha+\beta-1}B(\alpha-1,\beta)$，逐次降到 $B(1,\beta)=1/\beta$ 就得到它；正文的 $E[\Theta^m]=\frac{B(\alpha+m,\beta)}{B(\alpha,\beta)}$ 是同一个递推用 $m$ 次，展开成 $\frac{\alpha(\alpha+1)\cdots(\alpha+m-1)}{(\alpha+\beta)\cdots(\alpha+\beta+m-1)}$。
>
> 这条递推顺手解释一个常见疑问：Beta 密度的归一化常数为什么必须是 $B(\alpha,\beta)$？因为只有取它，$\int_0^1\theta^{\alpha+m-1}(1-\theta)^{\beta-1}d\theta$ 才能被同一个递推一路降到 $B(1,\beta)$，得到干净的阶乘比。参数化与归一化在这里是同一件事的两面，不是两套约定。
>
> 反例三条，划出共轭的边界。其一，似然一变共轭就没了：贝叶斯准则里分子的形状决定一切，若似然是截断形式（如书页 p422 的 $\theta^{-n}\mathbf 1\{\theta\ge x\}$），Beta 先验乘上去得到「截断 Beta」，必须用 incomplete beta function（不完全 Beta 函数）才能归一，不再闭式。其二，mixture of Betas（Beta 混合先验）严格说也不共轭：后验仍是同分量的混合，但分量权重被数据改写，等于每来一个观测就要重算全部权重，超参数从 $2$ 个变成 $2k+(k-1)$ 个。其三，参数化本身会破坏共轭：把 $\theta$ 换成 logit $\log\frac{\theta}{1-\theta}$ 之后，同一族看起来就不共轭了——共轭是「先验乘似然」的配对性质，不是分布的固有属性。
>
> 计算上的意义（也是它历史上的分量）。共轭让后验有 closed form（闭式）：一次更新是 $O(1)$ 次算术。不共轭时只能数值积分、Laplace approximation（拉普拉斯近似）、variational inference（变分推断）或 MCMC（Markov chain Monte Carlo，马尔可夫链蒙特卡洛），代价是成千上万次似然求值。所以共轭不是数学上的雅致，而是计算上的分水岭——这也是指数族在二十世纪统计实践里占了那么大篇幅的原因。

前述各个例子都涉及一个连续型随机变量 $\Theta$，且是参数估计（parameter estimation）问题的典型情形。接下来的例子是一个离散例子，也是那些出现在二进制假设检验（binary hypothesis testing）问题中的典型情形。
<!-- ===== PDF p426 ===== -->

<span style="color:#7f8c8d;">书页 p418／Chap. 8。页首承接上页 §8.1 贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）的论述，本页起出现新例 **Example 8.5**（在其语境下此页为 §8.1 的新例开端，非上页续讲）；随后是「多参数问题（Multiparameter Problems）」过渡小节与新例 **Example 8.6**。两例均属 §8.1，编号承接上页 Example 8.4 连续为 8.5、8.6。Example 8.6 在本页为第一部分（题干、先验、检测概率模型），其后续正文出现在下一页。</span>

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）（续）**</span>

> <span style="color:#7f8c8d;">本页页眉为「Chap. 8 / Bayesian Statistical Inference」，正文无新的小节号，即延续 §8.1 的正文叙述。新例 Example 8.5 在本页完整给出（上下文完整、非上页中断延续），故标题不作「（续）」；紧接其后的 Example 8.6 则持续到下一页。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.5（垃圾邮件过滤，Spam Filtering。）**</span>

一封电子邮件可能是「垃圾邮件（spam）」也可能是「正常邮件（legitimate）」。我们引入一个参数 $\Theta$，它取值为 1 与 2，分别对应该邮件为垃圾邮件与正常邮件，其概率分别为给定的 $p_\Theta(1)$ 与 $p_\Theta(2)$。设 $\{W_1, \ldots, W_n\}$ 是一组特殊单词（或多个单词的组合）的集合，其出现往往暗示一封垃圾邮件。对每个 $i$，设 $X_i$ 为贝努利随机变量（Bernoulli random variable），用以刻画单词 $W_i$ 在邮件中的出现情况：若 $W_i$ 出现则 $X_i = 1$，否则 $X_i = 0$。我们假定条件概率 $p_{X_i \mid \Theta}(x_i \mid \theta)$（对 $i = 1, \ldots, n$ 及 $\theta = 1, 2$）是已知的。为简单起见，我们还假设在给定 $\Theta$ 的条件下，随机变量 $X_1, \ldots, X_n$ 相互独立。

我们利用贝叶斯准则（Bayes' rule）来计算垃圾邮件与正常邮件的后验概率（posterior probabilities）。我们有

```math
p_{\Theta \mid X_1,\ldots,X_n}(\theta \mid x_1,\ldots,x_n)
= \frac{ p_\Theta(\theta) \prod_{i=1}^{n} p_{X_i \mid \Theta}(x_i \mid \theta) }
{ \sum_{j=1}^{2} p_\Theta(j) \prod_{i=1}^{n} p_{X_i \mid \Theta}(x_i \mid j) },
\qquad \theta = 1, 2.
```

这些后验概率可用来将邮件分类为垃圾邮件或正常邮件，所用的方法将在后文讨论。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先分清「报概率」与「做决定」。正文算出的是后验概率，而分类是一个决策，必须有损失函数：把每次误分类记为 $1$（0-1 loss，0-1 损失），则给定 $x$ 时选 $\theta$ 的 conditional risk（条件风险）为 $R(\theta\mid x)=1-p_{\Theta\mid X}(\theta\mid x)$，最小化它就等价于最大化后验，即 MAP（maximum a posteriori，最大后验）规则。所以「判给后验最大的那一类」不是直觉，而是 0-1 损失下的精确解。
>
> 二元的门槛要写清楚，方向在这里最容易翻。判 $\theta=1$ 当且仅当 $p_\Theta(1)\prod_ip_{X_i|\Theta}(x_i\mid1)\ge p_\Theta(2)\prod_ip_{X_i|\Theta}(x_i\mid2)$，等价于 likelihood ratio（似然比）条件 $\frac{\prod_ip_{X_i|\Theta}(x_i\mid1)}{\prod_ip_{X_i|\Theta}(x_i\mid2)}\ge\frac{p_\Theta(2)}{p_\Theta(1)}$。右边是 prior odds（先验赔率）的倒数：先验越偏向「正常邮件」，判为垃圾的门槛就越高。自检办法是令两侧先验与似然全相等，规则应退化成「无所谓」；任何在此情形下仍严格偏向一侧的写法，都是不等号方向错了。
>
> 「朴素」到底朴素在哪。给出类别之后各特征 conditional independence（条件独立）：$p_{X\mid\Theta}(x\mid\theta)=\prod_{i=1}^np_{X_i\mid\Theta}(x_i\mid\theta)$。正文的分母正是把这个乘积在 $\theta=1,2$ 上求和（全概率公式），分子是单个 $\theta$ 的乘积。两个连乘号的位置不同，抄公式时最容易把分子分母写混。
>
> 命名模板：naive Bayes（朴素贝叶斯）里的 naive 专指那条条件独立假设，不是说算法粗糙；generative model（生成式模型）指先建模 $p(X\mid\Theta)$ 再用贝叶斯准则反推后验，与之相对的是 discriminative model（判别式模型），直接建模 $p(\Theta\mid X)$。两者的差别在本例里看得最清楚：前者要为每个词在每个类别存一份概率表，后者只存一条分类边界。
>
> 跨课程（数值 / CSAPP）：连乘必然下溢。即使每个因子是 $0.1$，$n=400$ 时乘积也只有 $10^{-400}$，低于 double 的最小正规数 $2.2\times10^{-308}$，直接变 $0$；两侧都下溢时比值变成 $0/0$。实际实现一律在对数域算，$\log p=\log p_\Theta(\theta)+\sum_i\log p_{X_i\mid\Theta}(x_i\mid\theta)$，比较时不必 exp；若要还原概率，用 log-sum-exp，$\log(p_1+p_2)=M+\log(e^{a-M}+e^{b-M})$，其中 $M=\max(a,b)$。这不是工程技巧，是必须遵守的数值纪律。
>
> 反例三条。其一，关键词高度相关时会重复计数：一封邮件同时出现 free、prize、winner，朴素贝叶斯把三份证据连乘，后验被推到极接近 $1$ 的量级。具体数值取决于词频假设，教材没有给，所以原注写的「$1-10^{-12}$」属于无出处的具体化，这里去掉数字只保留机制：分类可能仍然正确，但那个概率已经不可信——这属于 calibration（校准）失效，而风控、医疗这类要拿概率做决策的场景不能接受。其二，训练集与线上的先验不同（垃圾邮件比例从两成变到六成）时 $p_\Theta$ 必须重估，否则门槛整体偏移，哪怕似然估计得很准。其三，未登录词让某个因子为零，整条乘积归零，所以必须平滑——这正是上一条注里那个「$+1$」的工程归宿。
>
> 历史坐标。把朴素贝叶斯用于垃圾邮件过滤，公认的普及起点是 Paul Graham 的随笔 A Plan for Spam（2002 年 8 月），随后 bogofilter、SpamBayes 等实现把它变成日常工程。教科书里它是 Example 8.5，工程上它是第一个「人人跑得通」的贝叶斯分类器——两条线的交汇点，正是本节这条后验公式。
>
> 再往上一层看（信息论）：取对数的似然比是逐特征相加的 $\sum_i\log\frac{p_{X_i\mid\Theta}(x_i\mid1)}{p_{X_i\mid\Theta}(x_i\mid2)}$，所以「证据」是按特征累积的。长期平均下来每个特征贡献的对数似然比，正是两个分布之间 KL divergence（KL 散度）之差；于是证据累积得多快，由两类分布的可分性决定，这条线接到假设检验的 Stein 引理与 Chernoff 界。本例因此不只是一个工程样板，它是 6.041 的贝叶斯准则通向信息论的最短路径。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上文后验公式（分母上的求和 $\sum_{j=1}^{2} p_\Theta(j)\prod p_{X_i\mid\Theta}(x_i\mid j)$）在源 OCR 中被切成碎片（如 `p{\Theta\mid X}(\theta\mid x)$` 写法与 `=-2-...ln-... j )` 残片），现按标准 $2\times 2$ 后验公式还原书写；求和指标在 OCR 中记作 `j`，被积段则误作 `m`，此处统一为 $\theta = 1, 2$。此还原与原文文句相符，非臆造数值。</span>

---

<span style="color:#c0392b;">**多参数问题（Multiparameter Problems）**</span>

迄今为止，我们的讨论都集中于只有一个未知参数（single unknown parameter）的情形。多个未知参数的情形与之完全类似。我们的下一个例子涉及一个二维参数（two-dimensional parameter）。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.6（基于传感器网络进行定位，Localization Using a Sensor Network。）**</span>

设有一个地理区域（interest region），其内散布着 $n$ 个声学传感器（acoustic sensors）。第 $i$ 个传感器的坐标为 $(a_i, b_i)$。一辆具有已知声学特征（acoustic signature）的载具位于该区域内，其笛卡尔坐标（Cartesian coordinates）$\Theta = (\Theta_1, \Theta_2)$ 未知。每个传感器都有一个与距离相关的概率，用于测得（i.e.，「捕捉到」车辆的声学特征）该载具。基于哪些传感器测得该载具、哪些没有测得，我们希望尽可能多地推断出它的位置信息。

先验概率密度函数（prior PDF）$f_\Theta$ 旨在刻画我们对载具位置的先验信念，该信念可能基于以往的观测。为简单起见，我们假定 $\Theta_1$ 与 $\Theta_2$ 是相互独立的、均值为 0、方差为 1 的正态随机变量（normal random variables），于是

```math
f_\Theta(\theta_1, \theta_2) = \frac{1}{2\pi}\, e^{-(\theta_1^2 + \theta_2^2)/2}.
```

设 $X_i$ 等于 1（相应地，等于 0），当且仅当传感器 $i$ 已测得该载具。为刻画信号衰减（signal attenuation），我们假定测得概率随载具与传感器之间的距离呈指数衰减，记该距离为 $d_i(\theta_1, \theta_2)$。更精确地说，我们采用如下模型……

> <span style="color:#7f8c8d;">衔接下一面（PDF p427）：Example 8.6 在本页完成第一部分——问题描述、两个零均值单位方差正态分量的先验密度 $f_\Theta(\theta_1,\theta_2)$，以及「测得概率随距离指数衰减」的模型设定；下一页给出该检测概率模型的具体形式及其随后的计算（后验推断）。页末模型公式行（原书紧接其后的 `d_i(\theta_1,\theta_2)` 概率表达式）在 OCR 中只余单词碎片，故终止于「……我们采用如下模型」。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页末「More precisely, we use the model …」之后随附的检测概率显式公式在源 OCR 中未可辨认（仅见 `di(...)` 残片与断行），下一页（PDF p427）首部应有其正文；此处不作臆造。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个例子是全章的结构转折点。single parameter（单参数）问题时参数空间是一条线，后验是一元函数；这里参数升级成向量，参数空间从一个区间变成一张平面，后验从一条曲线变成一张曲面。看似只多了一维，实际改变了三件事：似然因子怎么乘、后验能不能闭式求得、以及「有把握」这件事该怎么画。
>
> 每个传感器给出一个 Bernoulli random variable（伯努利随机变量）$X_i$。它的两个取值必须互补：$p_{X_i|\Theta}(1\mid\theta)+p_{X_i|\Theta}(0\mid\theta)=1$。正文取 $p_{X_i|\Theta}(1\mid\theta)=e^{-d_i^2(\theta)/2}$，指数随距离衰减：载具贴得近，测到的概率接近 $1$；离得远，测到概率趋于 $0$。那么「没测到」的概率只能是 $1-e^{-d_i^2(\theta)/2}$，不是 $1$。
>
> 这里有一处必须指出的错误。正文说「若 $X_i=0$，其贡献的概率因子即为 $1$，不改变后验的形式」，不成立。把距离 $1$ 与 $3$ 代进去：测得概率分别是 $0.6065$ 与 $0.0111$，于是未测到概率分别是 $0.3935$ 与 $0.9889$。后者确实接近 $1$，前者离 $1$ 相当远。把未测到因子取成 $1$ 只是远距离极限，不是恒等式；一取成 $1$，「传感器什么都没听到」这件事就凭空失去了全部信息。
>
> 这个错误要紧不要紧，要看它是否改变后验的函数形式。测到时因子是 $\exp(-d_i^2/2)$，是 Gaussian kernel（高斯核），与先验的高斯核相乘仍是高斯核，completing the square（配平方）之后闭合。未测到时因子是 $1-\exp(-d_i^2/2)$，是「1 减去高斯核」；这种形状取对数不产生二次型，乘进去以后后验不再是高斯。
>
> 正文随后又说「先验密度与测得概率都是高斯指数形式，配平方后后验仍是二维高斯」，这句只在全部传感器都测到时成立。只要有一个 $X_i=0$，后验就失去 closed form（闭式），归一化积分没有初等表达，只能数值网格或采样。这不是教材的疏忽，而是这个例子出场的本意：它恰恰要展示贝叶斯方法不要求后验可解，只要求能写出分子。
>
> 具体算一次，验证闭合条件。先验两个分量独立、各为标准正态；传感器 A 在 $(0,0)$，传感器 B 在 $(2,0)$，两个都测到。总指数是三项相加：先验的 $-\frac12(\theta_1^2+\theta_2^2)$、A 的 $-\frac12(\theta_1^2+\theta_2^2)$、B 的 $-\frac12((\theta_1-2)^2+\theta_2^2)$。合并后，$\theta_1$ 方向是 $-\frac32\theta_1^2+2\theta_1$，配方成 $-\frac32(\theta_1-\frac23)^2$；$\theta_2$ 方向是 $-\frac32\theta_2^2$。后验是均值 $(\frac23,0)$、两个方差都是 $\frac13$ 的对角正态。
>
> 用 precision（精度）读这个结果更省事。二次型系数的和是 $1+1+1=3$，正好是方差 $\frac13$ 的倒数；均值是三个伪观测按精度加权平均，先验贡献一个落在原点、权重 $1$ 的伪观测，于是 $(0\cdot1+0\cdot1+2\cdot1)/3=\frac23$。这正是 Kalman filter（卡尔曼滤波）的一次更新，只是用矩阵写时会多一层协方差乘法。
>
> 反过来看未测到。因子 $1-e^{-d^2/2}$ 在 $d=0$ 处为零，在 $d\to\infty$ 处趋近 $1$，密度上它的效果是「在传感器附近挖掉一块」，把后验质量推离该传感器。所以定位系统里的沉默不是没有信息，而是带方向的排除信息，与 erasure channel（擦除信道）同构：没收到不是随机噪声，而是一个已知的缺失事件，缺失本身参与更新。
>
> 跨课程看，这个例子同时落在三处。Strang 18.06 里，加权最小二乘的解就是精度加权平均，权重是方差的倒数；机器人学的 Markov localization（马尔可夫定位）把它写成离散网格上的乘积更新，Monte Carlo localization（蒙特卡洛定位）在非线性非高斯时用粒子代表后验；信息论里，每个观测削减的方差与它与参数之间的 mutual information（互信息）同向变化，但**不成比例**。原注在这里说「削减的方差正比于互信息」，不成立，可以算给读者看：取先验方差 $1$、噪声方差 $1$，$n$ 个观测后总互信息是 $\frac12\log(1+n)$ nat，方差削减是 $\frac{n}{n+1}$，比值 $\frac{\frac12\log(1+n)}{n/(n+1)}$ 在 $n=0.1$ 时是 $0.524$，$n=1$ 时 $0.693$，$n=100$ 时 $2.331$，跨两档就翻了四倍多，比例关系无从谈起。正确的一句话是：方差按精度相加的方式被削减，而互信息的换算随信噪比改变。三处讲的是同一件事：加法在精度域，不在方差域。
<!-- ===== PDF p427 ===== -->

<span style="color:#7f8c8d;">书页 p419 · 第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）。本页处于 §8.1 ↦ §8.2 的分界处：页眉同时出现 "8.1" 与 "8.2"（后者即 OCR 中被拆碎的 `8.2. LOC:a11Z;a.tu:>n`，实为 §8.2 的小节标题条 "POINT ESTIMATION, HYPOTHESIS TESTING, AND THE MAP RULE" 的残片）。本页正文全部为上一页 **Example 8.6（基于传感器网络进行定位）** 的收尾——承接检测概率模型、用贝叶斯准则写出后验（分子乘积 / 分母积分），故本页为 §8.1 的延续，标题以「（续）」处理；页末出现 §8.2 小节标题，其正文自下一页起。</span>

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）（续）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 OCR 严重破碎：除「sensor network」（传感器网络）、"we assume"、"$X_i$"、"$= 1$"、「the numerator over… integral」（分子……积分）等零星片段外，序数句几乎全部被切成单词（如 `i f/. S`、`IX …J`、`, . . . ,`、`integral` 等残片），且本例的检测概率公式行与后验显式结果在 OCR 中均无法辨认。下文按《Introduction to Probability》原书 Example 8.6 的真实语义与上一页（p426）已还原的设定做忠实转写与重建；凡具体系数/数值均以灰注释标明无法自本页 OCR 核实，绝不臆造原文未给出的数字。</span>

---
<br>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.6（续）——基于传感器网络进行定位（Localization Using a Sensor Network）**</span>

承接上一页关于传感器的设定。为刻画信号随距离的衰减（signal attenuation），我们假定传感器 $i$ 测到（detect）载具的概率随载具与传感器之间的距离 $d_i(\theta_1,\theta_2)$ 呈指数衰减；具体而言，测到概率可取如下形式：

```math
P(X_i = 1 \mid \Theta = \theta) \;=\; e^{-\,\tfrac{1}{2}\,d_i^{\,2}(\theta)},
```

其中 $d_i(\theta)^2 = (\theta_1 - a_i)^2 + (\theta_2 - b_i)^2$ 为载具位置 $\theta$ 与第 $i$ 个传感器位置 $(a_i, b_i)$ 之间距离的平方。若 $X_i = 0$（未测到），其贡献的概率因子即为 $1$，不改变后验的形式。

给定各传感器的测到结果 $X = (X_1, \ldots, X_n)$，由贝叶斯准则（Bayes' rule）可写出后验概率密度函数（posterior PDF）：它正比于似然（likelihood）$\prod_i p_{X_i\mid\Theta}(x_i\mid\theta)$ 与先验密度（prior PDF）$f_\Theta(\theta)$ 的乘积，分子为这一乘积，分母则为该乘积关于整个平面积分所得的归一化常数：

```math
f_{\Theta \mid X}(\theta \mid x)
\;=\; \frac{
  \Big(\prod_{i=1}^{n} p_{X_i\mid\Theta}(x_i \mid \theta)\Big)\; f_\Theta(\theta)
}{
  \int \Big(\prod_{i=1}^{n} p_{X_i\mid\Theta}(x_i \mid \theta')\Big)\; f_\Theta(\theta')\; d\theta'
}.
```

上式正是「the numerator over an integral」所指的构造：分子是似然与先验之积，分母是对参数 $\theta'$ 取全积分的归一化项。由于先验密度（两个独立的标准正态分量）与测到概率都是高斯指数形式，把二者相乘并配平方（completing the square）后，所得后验仍是一个二维高斯（bivariate normal / two-dimensional normal）分布；其后验均值与协方差表达为测到该载具的各传感器位置 $a_i, b_i$ 的函数，据此即可在测得结果的约束下对载具位置做出推断。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本例检测概率的指数系数（此处写为 $e^{-d_i^{\,2}(\theta)/2}$）、测到情况下 $X_i$ 的概率取值归一等，是依原书 Example 8.6 的语义自上一页（p426）设定顺延重建的；本页 OCR 仅能辨认 `sensor network`、`we assume`、$X_i$、`$=1$` 与「分子/积分」字样，具体常数与结果后验的均值向量、协方差矩阵之显式取值均无法自本页核实，故不在此给出具体数值。</span>

---
<br>

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）**</span>

> <span style="color:#7f8c8d;">本页页末出现 §8.2 小节标题（页眉条 `8.2. …ESTIMATION, …`）；其正文自下一页（PDF p428，书页 p420）起，接续后验分布 $P_{\Theta\mid X}(\theta\mid x)$ / $f_{\Theta\mid X}(\theta\mid x)$ 的表述、图 8.3 与 MAP 准则的错误概率最小化讨论。</span>
<!-- ===== PDF p428 ===== -->

<span style="color:#7f8c8d;">书页 420 · 第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）· §8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）中部续页。本页页眉为 §8.2 的小节标题条（"POINT ESTIMATION, HYPOTHESIS TESTING, AND THE …"，即 running header），页首无新 §/新标题，故本页是对上一页的延续。本页承接 §8.1 后验分布（posterior distribution）的表述（$P_{\Theta|X}(\theta|x)$ / $f_{\Theta|X}(\theta|x)$，对应书内公式 (8.15)/(8.16) 一带），随后引出**图 8.3（Figure 8.3）**并讨论 MAP 准则（MAP rule）：它等价于对不同观测值 $x$ 逐点的错误概率做最小化，从而最小化总体的错误概率（overall probability of error）。</span>

<span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 OCR 严重破碎：几乎每个叙述句都被切成单词或半字（页首 "…discuss its…"、"posterior distribution … x(θ|x) …", 中段 "…Equivalently, the…"、"…incorrect decision…of error…over x)…" 等），仅图 8.3 图注、后验表达式记号与指标随机变量 $I$、$g_{MAP}$、$E[I \mid X]$ 等数处可辨。下文按第 8 章 §8.2 关于「MAP 规则等价地最小化总体错误概率」的标准语义忠实重建，未从原文恢复处保留灰注释，绝不臆造未在原文出现的具体数值或公式编号。</span>

---

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）（续）**</span>

我们讨论它的……对 $X$ 观测值……后验分布（posterior distribution）$P_{\Theta|X}(\theta\mid x)$ [或 $f_{\Theta|X}(\theta\mid x)$]……（离散情形），……（……）……∫ 参见图 8.3。

<span style="color:#00838f;">**[图] Figure 8.3**（用于推断连续参数（a continuous parameter）时 MAP 准则（MAP rule）的图示（Illustration））</span>

> <span style="color:#7f8c8d;">图注（Figure 8.3）：用于推断连续参数时 MAP 准则的图示。图注原文 "8.3. Illustration of the MAP rule for inference of a continuous parameter…" 中的 "8.3" 前的编号字样在 OCR 中被拆成 "8 . 3 ."，此处以 "Figure 8.3" 还原。</span>

等价地，MAP 准则实现对总体错误概率（overall probability of error）的最小化〔对每一个观测值（observation value）$x$ 分别最小化条件错误概率，并随之对 $x$ 上的总体错误概率取平均作出最小化〕。†

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上句中的 "overall probability of error" 两处、括号内的连读片段及 "over x)]" 均为碎片还原，具体措辞如原书略有出入，但不改变「对应每个观测值最小化逐点错误概率、再对 $x$ 平均即得总体错误概率最小化」的数学含义。</span>

† <span style="color:#7f8c8d;">脚注（footnote）</span> 要更精确（more precisely）地陈述这一点，让我们考虑一个一般性的判定准则（decision rule，译作判定准则），它针对观测值（observation value）$x$……的取值 $\theta$……〔由此，事件 $\{I = 1\}$〕与事件 $\{g(X) = \theta\}$ 相同，其中 $I$ 按判定准则 $g$ 的定义取……〔$I$ 为一次正确判定（correct decision）的示性指标（indicator）〕；从而……为一次正确判定的概率（probability）……；且类似地对……矩阵成立。由于 MAP 准则（the MAP rule）的取法，对任何可能的……都有

```math
E[\, I_{MAP} \mid X \,] \;\geq\; E[\, I \mid X \,],
```

其中 $I_{MAP}$ 对应 $g_{MAP}$。于是按全期望定律（law of total expectation）……两边对 $X$ 取期望……即得总体错误概率被最小化。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 脚注段被 OCR 拆得几乎只余单词（"I } is the same as the event {g(X )、"、"the definition of the…E[I∣X]…any possible…g(x). Denote…rule,…to 1…a correct decision; thus, …and similarly for…I X ) ≤ (gMAP(X) = e I X)…law…(−)…by…gMAP. By…E[IMAP∣X],"）；上段按第 8 章 §8.2 关于 MAP 规则最小化错误概率的标准论证（以指标变量 $I=\mathbf 1_{\{g(X)=\Theta\}}$ 及条件期望 $E[I\mid X]$，因 $g_{MAP}$ 逐点最大化后验、故 $E[I_{MAP}\mid X]\ge E[I\mid X]$，再由全期望定律得全局最优）作忠实重建。其中等式 $I = \mathbf 1_{\{g(X)=\Theta\}}$ 的示性定义系按常规记号补出，属重建而非原文逐字还原；OCR 中 "$I X) \leq (g_{MAP}(X) = \theta \mid X)$" 的精确形式无法复原，未臆造。</span>

> <span style="color:#7f8c8d;">衔接：本页集中于「MAP 准则逐点最小化条件错误概率、进而最小化总体错误概率」的论证与图 8.3；后续页将继续 §8.2 中对该论断的收尾与点估计/假设检验的更细节讨论。</span>
<!-- ===== PDF p429 ===== -->

> <span style="color:#7f8c8d;">书页 p421，处于 **§8.2 点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）**（此处为续页，页眉为 `Sec. 8.2`）。本页无新章节起始横幅；页首承接上页关于「最大后验（MAP）准则」辞店的论述：先讲后验分布计算捷径与分母可省略，随后立起 MAP 准则的定义框及其等价的四种最大化形式，末再以有限的离散 $\Theta$ 情形说明 MAP 准则使选择到错误假设的概率最小，并辅以正确决策概率的表述。本页中部还以「（续）」的方式续讲 **Example 8.3**（$\Theta$ 与 $X$ 均为正态的情形）。</span>

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）（续）**</span>

由贝叶斯准则（Bayes' rule）给出的后验分布形式，带来一个重要的计算捷径（computational shortcut）：分母对所有 $\theta$ 都相同，且只依赖于观测（observation）值 $x$。因此，要最大化后验分布（posterior distribution），我们只需选取一个能最大化下列分子的 $\theta$ 值——若 $\Theta$ 与 $X$ 均为离散型，则最大化

```math
p_\Theta(\theta)\,p_{X\mid\Theta}(x\mid\theta);
```

若 $\Theta$ 和/或 $X$ 为连续型，则用相应的类似表达式。分母的计算没有必要。

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**[定义] 最大后验概率（MAP）准则（The Maximum a Posteriori Probability (MAP) Rule）**</span>

给定观测值 $x$，MAP 准则选取一个能（关于参数 $\Theta$）最大化后验分布的 $\theta$ 值：若 $\Theta$ 为离散型，则最大化概率质量函数 $p_{\Theta\mid X}(\theta\mid x)$；若 $\Theta$ 为连续型，则最大化概率密度函数 $f_{\Theta\mid X}(\theta\mid x)$。

等价地，它选取一个能（关于参数）最大化下列式子之一的 $\theta$ 值：

```math
\begin{aligned}
&p_\Theta(\theta)\,p_{X\mid\Theta}(x\mid\theta), \qquad &&\text{（$\Theta$ 与 $X$ 均为离散型）},\\
&p_\Theta(\theta)\,f_{X\mid\Theta}(x\mid\theta), \qquad &&\text{（$\Theta$ 为离散型、$X$ 为连续型）},\\
&f_\Theta(\theta)\,p_{X\mid\Theta}(x\mid\theta), \qquad &&\text{（$\Theta$ 为连续型、$X$ 为离散型）},\\
&f_\Theta(\theta)\,f_{X\mid\Theta}(x\mid\theta), \qquad &&\text{（$\Theta$ 与 $X$ 均为连续型）}.
\end{aligned}
```

如果 $\Theta$ 只取有限多个数值，那么 MAP 准则在所有决策准则（decision rules）之中使得选择到一个错误假设（incorrect hypothesis）的概率最小。无论对于无条件误差概率（unconditional probability of error），还是给定任意观测值 $x$ 的条件误差概率，这一点都成立。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 那句「分母的计算没有必要」是全书最容易被读过就忘、也最容易被误用的一句。它讲的是一个纯代数事实：在固定的观测 $x$ 下，后验密度的分母 $\int p_{X|\Theta}(x\mid\theta')f_\Theta(\theta')\,d\theta'$ 不含 $\theta$，是一个只依赖 $x$ 的常数。既然是常数，乘它除它都不改变函数在 $\theta$ 轴上的形状，自然也不改变最大值点的位置。
>
> 严格说法是 argmax（最大值点）对正常数因子不变。设分母为 $c(x)>0$，则后验等于分子除以 $c(x)$，两边同乘 $c(x)$ 后是同一个优化问题，最优解集合一模一样。这个论证不需要任何光滑性，也不要求 $\theta$ 是连续的，只要分母不为零就成立。
>
> 这也解释了为什么 MAP rule（最大后验准则）在四种离散与连续的组合下写出来的都是「先验乘似然」。概率质量函数与概率密度函数在各自情形下扮演相同的角色，而分子恰好是这两者的乘积：$p_\Theta(\theta)p_{X|\Theta}(x\mid\theta)$ 或它的连续版本。所以教科书把四行公式并列，实际上是一行。
>
> 代价在于正比符号。写「后验正比于先验乘似然」时丢掉的是 $1/c(x)$，而 $c(x)$ 是 $x$ 的函数。任何需要对 $x$ 求和或积分的量都不能用这个等价式代换：marginal likelihood（边缘似然）就是 $c(x)$ 本身，区间概率 $\int_a^b f_{\Theta|X}(\theta\mid x)\,d\theta$ 也带着 $c(x)$。省略分母只对「给定一个 $x$ 求最大值点」这一种用法安全。
>
> 第二个坑是 support（支撑）依赖参数。若似然在 $\theta$ 的不同取值上有不同的支撑，比如 $[0,\theta]$ 上的均匀分布，密度含 $1/\theta$ 且定义域随 $\theta$ 滑动。此时直接对密度求导会漏掉边界项，正确做法是逐个 $\theta$ 核对支撑，或者改用分布函数。本例的朱丽叶模型就是这种形状：后验要求 $\theta\ge x$，把 $\theta<x$ 整段剪掉；剪掉的不是数值很小，而是恰好为零。
>
> 工程上还有一个更常见的坑：underflow（下溢）。$n$ 个似然因子相乘，每个都小于 $1$，$n=1000$ 时乘积落到 $10^{-300}$ 以下，IEEE 754 双精度在约 $10^{-308}$ 处归零。CSAPP 里讲过的 denormal（非规格化数）也救不了这个量级。正确做法是在对数域相加：$\sum_i\log p_{X_i|\Theta}(x_i\mid\theta)$。加法不会下溢，只会在负无穷处饱和，而那正好对应「这个假设不可能」。
>
> 代一个具体数字。垃圾邮件先验是 $0.3$ 与 $0.7$，某封邮件在两类下的似然比是 $1000$。后验 odds（几率）等于先验比乘似然比，即 $(0.3/0.7)\times1000\approx428.6$，对应后验概率 $428.6/429.6=0.9977$。整个过程没有算分母，只用了先验比与似然比。这里原注的量级说法要改：如果把分子 $0.3\times0.001$ 当成概率报出去，得到 $3\times10^{-4}$，与真值 $0.9977$ 相差 $3325$ 倍，也就是 $3.5$ 个数量级，不是「三个数量级」；写成三个，误差本身就有一个数量级。
>
> 跨课程看，这是 6.042J 的 partition（划分）与全概率在连续情形的一次应用：分母是把 $\theta$ 的所有取值按先验与似然加权求和，它的唯一职责是保证后验是归一化的概率测度。6.006 里比较大小、取最大值点也是同一类操作：只关心相对次序，不关心绝对刻度。优化里这叫 monotone transformation（单调变换）不改最优解，取对数是最常用的一例。
>
> 反例要记牢：省略分母之后，手里的是相对后验，不是概率。任何需要跨 $x$ 比较的量，比如平均错误率、期望损失、ROC curve（ROC 曲线）下的面积，都必须把分母补回来。很多人算出最大值点之后顺手把分子当概率报出去，这种错误在论文里也偶有出现，量级可以差几个数量级。

> <span style="color:#7f8c8d;">[交叉引用] 该性质（MAP 准则最小化错误概率）的表述衔接下方关于「正确决策概率」的讨论，并与「$\Theta$ 离散时相关」的说明相互印证。§8.2，p.421。</span>

让我们通过重温前面一节中的若干例子来说明 MAP 准则。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.3（续）——正态先验、正态观测**</span>

在本例中，$\Theta$ 是一个正态随机变量（normal random variable），均值为 $\theta_0$，方差为 $\sigma_0^2$。我们观测一组随机变量 $X = (X_1, \ldots, X_n)$——在给定 $\Theta$ 取值为 $\theta$ 的条件下，这些随机变量是相互 independent（独立）的正态随机变量，均值均为 $\theta$，方差分别为 $\sigma_1^2, \ldots, \sigma_n^2$。我们已经知道，后验概率密度函数（posterior PDF）是正态的。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上方「后验 PDF 是正态的」之后，本应紧接该后验正态密度的具体表达式（其均值与方差的代数形式），但源 OCR 在此处断裂，只剩 `We found that the posterior PDF is normal`（"…后验概率密度函数是正态的"）一句，正态后验的均值/方差公式无法逐字复原。此处留空占位，未臆造任何数值。</span>

对任一其他决策准则 $g$，记 $I_{\{g(X)=\Theta\}}$ 为「$g(X)=\Theta$（即决策正确）」的示性变量（indicator），则有

```math
E\big[I_{\{g(X)=\Theta\}}\big] \;\le\; E\big[I_{\{g_{MAP}(X)=\Theta\}}\big],
```

也就是说

```math
p\big(g(X)=\Theta\big) \;\le\; p\big(g_{MAP}(X)=\Theta\big).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源 OCR 中上述两条不等式被读取为碎片（如 `E[I] $\le$ E[I_{MAP}] , or` 与 `p(g(X)=$\Theta$) $\le$ p(g_{MAP}(X)=$\Theta$)` 的行首、行尾残缺，方向记号 `$\le$` 亦一度被读作 `$\ge$`）。现按「MAP 准则最大化正确决策概率」的语义将方向与示性变量下标复原；方向与概率语义均已核对正文措辞，未臆造原文未含的数值。</span>

因此，MAP 准则在所有决策准则 $g$ 之中使得正确决策（correct decision）的总体概率达到最大。注意，这一论证当 $\Theta$ 为离散型时最有意义：若在给定 $X=x$ 的条件下 $\Theta$ 是一个连续型随机变量（continuous random variable），那么任何准则下正确决策的概率都为 $0$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这句话初读像一个悖论：MAP 是「最优准则」，而它在一个连续参数上的正确概率竟然是零。解开这个悖论要分清两件事，即「准则选出的点」与「真值恰好等于这个点」。在连续型里后者的概率恒为零，与准则好坏完全无关。
>
> 实分析的语言更清楚。连续随机变量的分布没有原子，任意单点集的 Lebesgue measure（勒贝格测度）为零，于是它在密度下的积分也为零。这不是「很小」，而是恰好为零；而且这件事对任何准则、任何取点都成立。所以「正确概率」这个打分方式在连续参数上恒等于零分，无法区分好坏。
>
> 这就把 MAP 的两种读法分开了。离散参数上，MAP 最小化的是 0-1 loss（0-1 损失）的期望，也就是「选错假设」的概率，那种情形下正确概率是一个有意义的实数。连续参数上，0-1 损失退化成「只在单点为零、别处为一」的怪函数，任何准则的期望损失都是 $1$，它不再是可用的判据。硬套离散结论就会得到「所有准则得分都是零，谁也不比谁好」的荒谬推论。这一条也定下了后文的分工：连续参数下要让 MAP 有意义，必须把 0-1 损失改写成「落在估计点周围一小段区间里」的形式，见下段。
>
> 正确的连续版本是把目标换成邻域。对任意小 $\epsilon>0$，真值落在估计点 $\epsilon$ 邻域内的概率约等于 $2\epsilon\,f_{\Theta|X}(\hat\theta\mid x)$，这是区间长度乘密度的近似，因为区间足够窄时密度近似常数。要让这个概率最大，就要让密度最大。于是「最大密度」成为「逐点正确概率最大」的极限形式，这也正是 posterior mode（后验众数）的严格意义。注意 $\epsilon$ 必须先固定再比较：把 $\epsilon$ 与估计点一起优化是没有定义的，这一点是本条与后面「0-1 损失下最优是众数」那句话的分界，那边的众数结论只在固定 $\epsilon$ 的邻域版里成立。
>
> 代一个数看量级。后验是标准正态，取 $\epsilon=0.01$，则邻域概率约 $2\times0.01\times0.3989=0.0080$。把估计点从 $0$ 挪到 $1$，密度从 $0.3989$ 掉到 $0.2420$，邻域概率掉到 $0.0048$，只剩六成。所以「密度最大」在有限精度下确实在挑更好的点，只是这个「更好」不以命中的形式表现。
>
> 顺带指出后文一处漏项。正文把 Example 8.3 的后验均值写成「各观测按方差倒数加权」，却漏了先验那一项。正确的后验均值必须同时含先验均值与先验精度：分子是先验精度乘先验均值、加上各观测的精度加权和，分母是全部精度之和。少了这一项，就等于假定先验方差无穷大、先验完全无信息。
>
> 用数值确认这个差异。先验均值 $0$、先验方差 $4$；两次观测分别是 $1$ 与 $3$，观测方差都是 $1$。正确均值是 $(0/4+1+3)/(1/4+1+1)=4/2.25=1.778$，后验方差是 $1/2.25=0.444$。只按观测加权的公式给出 $(1+3)/2=2$。差异 $0.222$，而且方向固定：先验在 $0$，只算观测的公式总是把估计拉得离先验更远。样本量越大差异越小，这正是「先验被数据淹没」的速度。
>
> 跨课程看，这是「精度相加」的三处同构。Strang 18.06 的加权最小二乘用同一个加权平均，权重是方差的倒数；Kalman filter（卡尔曼滤波）的协方差更新就是把精度矩阵相加；实分析上，它是「零测集不改变积分」的直接推论，正因为测度在单点上没有质量，才必须用密度而不是用点概率来打分。
<!-- ===== PDF p430 ===== -->

> <span style="color:#7f8c8d;">第 8 章 §8.2 点估计、假设检验与最大后验（MAP）准则（Point Estimation, Hypothesis Testing, and the MAP Rule）中部续页。本页页首为上一页某个例子（正态后验 / MAP 估计）的收尾，随后为垃圾邮件分类例子在 §8.2 中沿用 MAP 准则的续讲，页末进入 §8.2 的「Point Estimation（点估计）」正文。§8.2 的节标题在上一页已出现，故本节小节标题记为（续）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.3（续）——正态后验与最大后验（MAP）估计（收尾）**</span>

该例收尾处给出后验分布（posterior distribution）：它以均值 $m$、方差 $v$ 的正态分布（normal）为后验，具体由下式给出——

```math
m = \mathrm{E}[\Theta \mid X = x] = \frac{\sum_{i=1}^{n} x_i / \sigma_i^2}{\sum_{i=1}^{n} 1 / \sigma_i^2},
\qquad
v = \mathrm{var}(\Theta \mid X = x) = \frac{1}{\sum_{i=1}^{n} 1 / \sigma_i^2}.
```

由于正态概率密度函数（normal PDF）在其均值处取得最大值，因此最大后验（MAP）估计为 $\hat{\theta} = m$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页首为承接上一页的例子收尾，其例号因跨页未在本页重现（前一页已定义）。后验均值 $m$ 与方差 $v$ 的表达式在 OCR 中残碎（读数如 `E [e I X xl`、`L xi/a?`、`L I/a;`、`i=O` 等），上方按「以方差倒数（精度）加权合并正态观测」的标准后验形式重建：$m$ 为各 $x_i$ 按 $1/\sigma_i^2$ 加权的平均，$v$ 为各精度之和的倒数。求和指标 $i=1\ldots n$ 与 $\sigma_i^2$ 系据原书语义复原，非臆造数值。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.5（续）——垃圾邮件分类（spam filtering）与 MAP 准则**</span>

这里参数 $\Theta$ 取值为 1 和 2，分别对应垃圾邮件（spam）与正常／合法邮件（legitimate），并带有给定的概率 $p_\Theta(1)$ 与 $p_\Theta(2)$；$X_i$ 是伯努利随机变量（Bernoulli random variable），对关键词 $W_i$ 在消息中的出现与否加以建模：若 $W_i$ 出现则 $X_i = 1$，若未出现则 $X_i = 0$。我们已算出消息为垃圾邮件与正常邮件的后验概率（posterior probabilities），对 $m = 1, 2$ 成立

```math
P(\Theta = m \mid X_1 = x_1, \ldots, X_n = x_n)
\;\propto\; p_\Theta(m)\,\prod_{i=1}^{n} P(X_i = x_i \mid \Theta = m),
\qquad m = 1, 2.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述后验概率的具体表达式在源 OCR 中严重残缺，仅余片段 `Xi`、`(Xi`、`n`、`m = 1 , 2` 等若干字样，其精确的似然乘积结构与归一化因子无法完全复原。上方按「（先验）×（因子条件似然乘积），再对两类 $m$ 归一化」的标准 MAP 后验结构给出占位；具体参数（如各关键词在两类消息中的出现概率）本页 OCR 未出现，故不臆造其具体数值。</span>

假设我们想根据相应的向量 $(X_1, \ldots, X_n)$ 把一条消息判定为垃圾邮件或正常邮件。那么，MAP 准则（MAP rule）会把该消息判定为垃圾邮件，当且仅当

```math
P(\Theta = 1 \mid X_1 = x_1, \ldots, X_n = x_n) > P(\Theta = 2 \mid X_1 = x_1, \ldots, X_n = x_n),
```

或等价地，当

```math
p_\Theta(1)\,\prod_{i=1}^{n} P(X_i = x_i \mid \Theta = 1)
\;>\;
p_\Theta(2)\,\prod_{i=1}^{n} P(X_i = x_i \mid \Theta = 2).
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「把比较后验换成比较先验乘似然」这一句之所以值得单独立注，是因为它是把分类改写成比值阈值的入口。比值形式有一个巨大的工程优势：它把「两类各自算什么」压缩成「一条轴上取一个阈值」，于是模型换、类别换、代价换，只要移动阈值的位置就行。
>
> 严格推导一次。判为第 $1$ 类，当且仅当先验乘第 $1$ 类似然大于先验乘第 $2$ 类似然。两边同除以第 $2$ 类的乘积，得到 likelihood ratio（似然比）大于第 $2$ 类先验与第 $1$ 类先验之比。注意右边是先验比的倒数：先验越偏向第 $2$ 类，判第 $1$ 类所需的似然比阈值就越高。
>
> 方向这一步最容易写反。设垃圾邮件先验 $0.2$、正常邮件先验 $0.8$，则阈值是 $4$；一个证据若在两类下等可能，似然比是 $1$，小于 $4$，应判正常。若把阈值写成四分之一，同一封邮件会被判成垃圾。阈值方向由「谁是分子」决定，换了分子就要取倒数，这是抄公式时最常见的翻车点。
>
> 取对数后判据变成加法：各特征的对数似然比之和，大于两类先验之比的对数。左边每一项只依赖一个特征，可以增量更新，来一个词就加一项、减一项。这就是词典式过滤器能流式工作的原因，也解释了为什么 log-odds（对数几率）是这类系统的标准坐标系。
>
> 代数字算一次。先验 $0.2$ 与 $0.8$ 给出阈值 $\log4=1.386$。若 free 这个词在垃圾邮件中出现概率 $0.4$、正常邮件中 $0.02$，单项贡献是 $\log20=3.00$；meeting 在两类中分别是 $0.01$ 与 $0.15$，贡献是 $\log(0.067)=-2.71$。一封同时含两词的信，净贡献 $0.29$，小于 $1.386$，判为正常；只出现 free 则 $3.00$ 超过阈值，判垃圾。
>
> naive Bayes（朴素贝叶斯）的代价就在这里。连乘假设各特征在给定类别下条件独立，而自然语言里 free 与 viagra 高度共现。把同一份证据算两遍，对数几率被放大，输出概率过度自信。工程上的修法是 calibration（校准）：保留排序，重新映射概率。Paul Graham 在 2002 年 8 月那篇 A Plan for Spam 里推的正是这条路线，他只信排序，不信绝对数值。
>
> 跨课程看，这就是检测理论里 Neyman–Pearson 引理与 ROC curve（ROC 曲线）的同一条轴：似然比把所有可能的判决压缩成「阈值取在哪」，改变代价或先验只是移动阈值。这里把「引理的发源地」改成「同一思想的近代形式」更稳妥：Neyman–Pearson 引理是 1933 年才正式提出的固定显著性水平下的最优检验，而本节做的是给定先验后最小化错误概率的贝叶斯判决，两者共享似然比这一条轴，但优化目标不同，说「发源地」是把两件事的时序与条件都混了。6.042J 的划分与全概率保证分子分母的归一化；信息论里每个特征贡献的期望对数似然比，正是两类分布之间的 KL divergence（KL 散度），于是证据累积得多快由两类可分性决定。
>
> 顺带说一个常被忽略的点：阈值里只出现先验之比，没有出现先验本身。这说明判决只依赖两类的相对先验，不依赖它们的绝对大小。把先验从 $0.2$ 与 $0.8$ 同时乘一半变成 $0.1$ 与 $0.4$，阈值不动，判决也不动。这条性质来自后验的归一化，与本节前面「只需分子就够」是同一个原因的两个侧面。
>
> 反例补一条。若某特征在两类下概率都是 $0$，似然比是 $0$ 除以 $0$，公式失效。实际系统必须做加一平滑，否则一个没见过的词就能让整封信的判据变成未定义。原注接着说这也是后来改用 TF-IDF 加权与特征筛选的动因之一，这个因果链站不住：平滑修的是 $0/0$ 这种数值事故，TF-IDF 处理的是「哪些词更该被加权」，两件事在工程里常同时出现，但前者不是后者的原因。把两者串成因果，读者会误以为加了平滑就不需要加权。

> <span style="color:#7f8c8d;">[OCR 标签考] 源 OCR 将本例读作 "Example 8.5 (continued)"，与 §8.1 中同一垃圾邮件例（Example 8.5）的编号一致：本例系在 §8.2 的 MAP 语境下续讲 §8.1 的 Example 8.5，故标为 **Example 8.5（续）**，不再重编号。§8.2 各数值例号已按源 OCR 核对为 8.7（朱丽叶迟到）、8.8（有偏硬币）、8.9（两枚有偏硬币）并与本页分开，故本页不占用 8.7。确切例号以原书为准。</span>

---

<span style="color:#c0392b;">**Point Estimation（点估计）**</span>

在一个估计问题（estimation problem）中，给定观测（observation）$X$ 的取值 $x$，后验分布（posterior distribution）囊括了 $x$ 所提供的全部相关信息。另一方面，我们可能只对某些能概括后验分布性质的量感兴趣。例如，我们可以选取一个点估计（point estimate），即一个单独的数值，用来代表我们对 $\Theta$ 取值所做的最佳猜测。

让我们引入一些与估计相关的概念与术语。为简单起见，我们假定 $\Theta$ 是一维的，但这一套方法同样可推广到其他情形。我们用术语 estimate（估计值）指代我们基于实际观测 $x$ 而选择去报告的那个数值 $\theta$。$\theta$ 的取值通过对观测 $x$ 施加某个函数 $g$ 来确定，即 $\theta = g(x)$。随机变量 $\hat{\Theta} = g(X)$ 被称为估计量（estimator），每当随机变量 $X$ 取到值 $x$ 时，它的实现值恰等于 $g(x)$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> estimator（估计量）与 estimate（估计值）这组区分，是统计里第一个真正要求把随机性放在正确位置的概念。观测 $X$ 在抽取之前是随机变量，把它放进函数 $g$ 之后，得到的 $\hat\Theta$ 仍然是随机变量；只有当 $x$ 真的落地，$g(x)$ 才是一个数。一个对象、一个数值，混读之后所有下游推理都会错位。
>
> 用函数与函数值来类比最贴切。Strang 18.06 里矩阵与向量不能互相代入，这里三层也要分开：$g$ 是规则、$g(X)$ 是随机变量、$g(x)$ 是数。代码里同样如此，估计量是那个函数本身，估计值是一次调用的返回值。把返回值当函数去求方差，等于对一个常数求方差，答案恒为零。
>
> 这个区分之所以必要，是因为所有评价标准都定义在估计量的分布上。bias（偏差）是估计量的期望减真值，variance（方差）是估计量的方差，mean squared error（均方误差）是两者的平方和。这三者都要求估计量有分布，也就是要求它是随机变量。单次报出的 $3.2$ 没有分布，谈不上偏差，也谈不上 consistency（相合性）。
>
> 相合性尤其能说明问题。它说的是 $n\to\infty$ 时估计量依概率收敛到真值，是一个关于整列随机变量的陈述，不是关于某次实验结果的陈述。无偏性同理，它说的是重复抽样无限多次、平均下来不偏，单次抽样无所谓偏不偏。把这两句话里的估计量换成估计值，陈述立刻变得不可定义。
>
> 代数字看。若用样本均值估计正态均值，方差为 $1$，则估计量的期望等于真值、方差是 $1/n$、均方误差也是 $1/n$。$n=4$ 时标准差 $0.5$，一次报出 $3.2$ 无法判断偏不偏，只能说这个估计量的典型误差是 $0.5$ 量级。若反过来把 $3.2$ 当估计量，它的方差是零，均方误差退化成一个与 $n$ 无关的数，整套理论随之失效。
>
> 贝叶斯框架里还要多一层。参数本身也是随机变量，于是估计量与参数都是随机变量，条件均方误差写成观测给定下的期望，期望是对后验取的。这里的偏差不再相对某个固定真值，而是相对后验分布；两种框架的公式长得像，含义不同，这也是初学最容易混过去的一处。
>
> 跨课程看，6.006 的 amortized analysis（摊还分析）是同一个思想在算法里的版本：单次操作可能很贵，摊还代价说的是一整串操作平均下来的界，而不是哪一次。把单次耗时当摊还代价，就会得出「这个数据结构每次只花常数时间」的错误自信。估计量的期望与它单次输出的关系，与这两者完全同构。
>
> 最后一个反例把错误显形。若某人说「本估计量的方差是零，因为它报出的值是 $0.32$」，错在两处：一是把估计值当估计量，二是把报告出的那个数当成了常数。正确说法是「这个估计量在重复抽样下的方差是若干」，而 $0.32$ 只是它这一次的取值。一字之差，整个统计推断的对象换了。

> <span style="color:#7f8c8d;">[OCR 说明] 末二句中的 $\hat{\Theta} = g(X)$ 在 OCR 中被读作 `e = g(X)`，其中 `e` 应为 $\hat{\Theta}$（即带帽参数估计量）；此处按字义还原为带 hat 的参数记号，未改动语义。</span>
<!-- ===== PDF p431 ===== -->

<span style="color:#7f8c8d;">§8.2 点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）中部续页（书页 423）。本页页首无新的节标题或新例，正文承接上一页对「估计量与两种常用估计方法」的介绍，故本节标题带「（续）」。本页先陈述条件期望估计量并将它预告为下一节指定的 LMS 估计量，再给出 MAP 估计量的两点说明，末尾转入本节要点小结框「点估计（Point Estimates）」。本页引用了例题 Example 8.3 与第 4.3 节。排版注：源 OCR 中把估算符号退化读成普通字母（`e` 表示估计 $\hat\theta$、`8` 表示未知参数 $\Theta$、`()` 表示其取值 $\theta$、`!` 表示密度 $f$），下文已按原书符号还原，未臆造数值。</span>

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）（续）**</span>

估计量 $\hat{\theta} = g(X)$ 之所以是一个随机变量（random variable），其原因在于：估计流程（estimation procedure）的输出结果依赖于观测（observation）$X$ 的随机取值。

我们可以选用不同的函数 $g$ 来构造不同的估计量（estimators），其中有的会比另一些更好。举一个极端的例子，考虑满足「对所有 $x$ 都有 $g(x) = 0$」的那个函数。由此得到的估计量 $\hat{\theta} = 0$ 完全没有利用数据，因而并不是一个好的选择。我们已经见到两个最常用的估计量：

- (a) **最大后验概率（Maximum a Posteriori Probability，MAP）估计量**：在这里，观察到 $x$ 之后，我们选取能使后验分布（posterior distribution）在所有 $\theta$ 上取到最大值的估计量 $\hat{\theta}$；若遇到并列（ties），则任意打破选择。

- (b) **条件期望估计量（Conditional Expectation estimator）**：它在第 4.3 节引入。在这里，我们把估计量取为 $\hat{\theta} = E[\Theta \mid X = x]$。

条件期望估计量将在下一节详细讨论。届时它将被称为最小均方（least mean squares，LMS）估计量，因为它具有一条重要性质：正如我们稍后将要证明的那样，它能在所有估计量中使均方误差（mean squared error）最小。关于 MAP 估计量，我们有如下两点说明。

- (a) 若 $\Theta$ 的后验分布关于其（条件）均值对称，并且是单峰（unimodal，即只有一个最大值），那么最大值就出现在均值处。此时，MAP 估计量与条件期望估计量重合。举例说，若后验分布被保证为正态分布（normal），则正是这种情况，参见例题 Example 8.3。

- (b) 若 $\Theta$ 是连续的，则 MAP 估计 $\hat{\theta}$ 的实际求值有时可以解析地完成；例如，当 $\theta$ 不存在约束条件时，可通过令 $f_{\Theta|X}(\theta \mid x)$ 或其对数 $\log f_{\Theta|X}(\theta \mid x)$ 的导数为零，并对 $\theta$ 求解来完成。然而在其他情形下，则可能需要进行数值搜索（numerical search）。

---

<span style="color:#00838f;">**[点估计] Point Estimates**</span>

- <span style="color:#00838f;">**估计量（estimator）**</span> 是一个具有形如 $\hat{\theta} = g(X)$ 的随机变量，其中 $g$ 是某个函数。$g$ 的不同选取对应不同的估计量。

- <span style="color:#00838f;">**估计值（estimate）**</span> 是某个估计量 $\hat{\theta}$ 所取的取值，它由观测 $X$ 的实现值（realized value）$x$ 决定。

- 一旦观测到 $X$ 的值 $x$，<span style="color:#00838f;">**最大后验概率（MAP）估计量**</span>就把估计值 $\hat{\theta}$ 设为这样一个值：它使后验分布在所有可能的 $\theta$ 取值上取到最大值。

- 一旦观测到 $X$ 的值 $x$，<span style="color:#00838f;">**条件期望（LMS）估计量**</span>就把估计值 $\hat{\theta}$ 设为 $E[\Theta \mid X = x]$。
<!-- ===== PDF p432 ===== -->

<span style="color:#7f8c8d;">书页 p424，第 8 章 Bayesian Statistical Inference（贝叶斯统计推断）· §8.2 Point Estimation, Hypothesis Testing, and the MAP Rule（点估计、假设检验与 MAP 准则）续页（本章第 8 章）。例号 `S.7`/`S.S` 为 OCR 破损，实为 Example 8.7 与 Example 8.8（按已知序列 8.1→8.16 反推）。</span>

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）（续）**</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.7**</span>

考察 Example 8.2 的情形：Juliet（朱丽叶）在第一次约会时迟到了一个随机量 $X$。$X$ 的分布是 $[0, \Theta]$ 区间上的均匀分布（uniform），而 $\Theta$ 是一个未知的随机变量，其在 $[0, 1]$ 区间上具有均匀的先验概率密度函数（prior PDF）$f_\Theta$。在那个例子中我们看到，对 $x \in [0, 1]$，后验概率密度函数（posterior PDF）为

```math
f_{\Theta|X}(\theta\mid x) = \frac{1}{\theta\,|\ln x|}, \qquad x \le \theta \le 1,
\qquad 0,\ \text{其他情形}.
```

对于给定的 $x$，在 $\Theta$ 的一切可能取值区间 $[x, 1]$ 上，$f_{\Theta|X}(\theta\mid x)$ 随 $\theta$ 递减。因此，最大后验（MAP）估计（MAP estimate）等于 $x$。注意，这是一个「乐观（optimistic）」的估计：如果 Juliet 在第一次约会迟到的时间很少（$x \approx 0$），那么对未来迟到时间的估计也就很小。

而条件期望估计（conditional expectation estimate）被证明不那么「乐观」。特别地，我们有

```math
E[\Theta \mid X = x] = \frac{1 - x}{|\ln x|}.
```

这两种估计作为 $x$ 的函数绘于图 8.4（Fig. 8.4）。可以看出，对任何观测到的迟到量 $x$，$E[\Theta \mid X = x]$ 都大于 $\Theta$ 的 MAP 估计。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个例子值得细看，因为它是全书唯一一处「两种最优估计在同一后验上给出不同答案」的干净对照。同一份后验，一个算子取峰、一个算子取重心，差多少、为什么差，都能手算出来。
>
> 形状先看清。对固定的 $x\in(0,1)$，后验密度是 $1/(\theta\lvert\ln x\rvert)$，定义在 $\theta\in[x,1]$ 上，随 $\theta$ 单调递减。密度在左端点最大，所以 posterior mode（后验众数）就是 $x$。这就是 MAP（maximum a posteriori，最大后验）估计，它把「最可能」读成「密度最高」。
>
> 这条单调性是两件事相乘的必然结果。先验在 $[0,1]$ 上均匀，乘进去只剩一个常数；似然是把观测 $x$ 埋在长度为 $\theta$ 的区间里的均匀分布的密度，值是 $1/\theta$。于是后验在 $\theta\ge x$ 上就是 $1/\theta$ 的倍数，单调递减没有第二种可能。
>
> 条件期望则是重心：把密度乘 $\theta$ 再积分，$1/\theta$ 恰好与 $\theta$ 约掉，积分只剩区间长度，结果是 $(1-x)/\lvert\ln x\rvert$，正文把它写作 $E[\Theta\mid X=x]=\frac{1-x}{\lvert\ln x\rvert}$ 并画在图 8.4 上。这个式子可以手算，不需要任何特殊函数，这也是这个例子适合做练习的原因。
>
> 大小关系能严格证明，不是数值巧合。令 $u=-\ln x>0$，则 $x=e^{-u}$。要证 $(1-e^{-u})/u>e^{-u}$，两边乘 $ue^{u}$ 得 $e^{u}-1>u$，而 $e^{u}$ 的展开每项都为正，严格大于 $1+u$。所以对一切 $x\in(0,1)$ 都有均值大于众数，等号只在 $x\to1$ 的极限处出现。这就是正文说条件期望「不那么乐观」的严格来源。
>
> 换个角度看众数落在哪里。它钉在支撑的左边界上，统计上叫 boundary estimate（边界估计），意思是估计量把「数据能支持的最小值」当成答案。原注在这里写了一句必须更正的话：「它对观测的响应斜率是 $1$，而均值的斜率小于 $1$」。前半句对，众数就是 $x$，斜率恒为 $1$；后半句错。对 $g(x)=(1-x)/(-\ln x)$ 求导得 $g'(x)=\frac{(1-x)/x+\ln x}{(\ln x)^2}$，在 $x=0.05$ 处 $g'=1.783$，在 $x=0.1$ 处 $g'=1.263$，都大于 $1$；只有当 $x$ 大约超过 $0.168$ 之后它才小于 $1$，并且 $x\to1$ 时趋于 $0.5$。所以真实图景是：均值的斜率在左端大于 $1$、在右端趋于 $0.5$，而众数斜率恒为 $1$，两条曲线在 $x\to1$ 处汇合、但斜率始终不同。把它们说成「斜率处处更小」既不符合算出来的数，也解释不了为什么两条曲线在右端才贴合。
>
> 代数字。$x=0.5$ 时 $\lvert\ln0.5\rvert=0.6931$。MAP 是 $0.5$，均值是 $0.5/0.6931=0.7213$，差 $0.221$。再算均方误差：后验二阶矩是 $0.375/0.6931=0.5411$，方差是 $0.5411-0.7213^2=0.0207$。均值估计的均方误差就是方差 $0.0207$；MAP 估计要多加 $(0.5-0.7213)^2=0.0490$，合计 $0.0697$，是前者的 $3.4$ 倍。
>
> 把中位数也算出来作对照。让后验分布函数等于一半，解得中位数是 $\sqrt{x}$。$x=0.5$ 时它是 $0.7071$，正好夹在 MAP 的 $0.5$ 与均值的 $0.7213$ 之间。三个算子排成一列，位置由各自的损失函数决定，这个排序在大多数单峰右偏的后验上都成立。
>
> 这个差距不是 MAP 差，而是损失函数不同。一般的贝叶斯点估计是让期望损失最小的那个值。取 squared error loss（平方误差损失）时最优解是均值，取 absolute error loss（绝对误差损失）时是中位数，取 0-1 loss（0-1 损失）时是众数——但这最后一句必须加限定，否则与前面「连续参数下任何准则的正确概率都是零」那句直接冲突：在连续参数上，0-1 损失的期望恒为 $1$，任何点都不可区分。众数之所以在 0-1 损失下「最优」，前提是把损失改成「落在估计点 $\epsilon$-邻域内」的版本并固定 $\epsilon$，那时最优解是邻域概率最大、也就是密度最大的点。漏掉这个前提，三个算子就不是同一个框架下并列，而是把两种不同的损失混为一谈。
>
> 反例也要说清。不能因为均值的均方误差更小，就说均值更准。若下游代价是估小了要赔钱、估大了没事，不对称损失会把最优点推到众数甚至更低。真实工程里选哪个算子，先问代价函数长什么样，再问后验长什么样，顺序不能反。

> <span style="color:#7f8c8d;">图 8.4（Figure 8.4）图注：MAP 估计与条件期望估计作为观测值（observation）$x$ 的函数，见 Example 8.7。图中坐标轴刻度（0…1）与两条曲线（MAP Estimates、Conditional Expectation Estimates）的图例文字在源 OCR 中被拆成碎片，仅能认出图注部分；曲线数据无法逐点复原，此图按原书含义忠实转述。上文后验密度与条件期望公式（$\frac{1}{\theta|\ln x|}$、$\frac{1-x}{|\ln x|}$）中分母的 $|\ln x|$ 来自源 OCR 的 `log x` 片段与归一化核对的忠实还原，未源自原文之外的数值。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.8**</span>

我们考察 Example 8.4 中的模型：观测一枚有偏硬币（biased coin）$n$ 次独立抛掷中出现正面的次数 $X$。我们假定 $\Theta$（即正面的概率）的先验分布（prior distribution）在 $[0, 1]$ 上均匀。我们将推导 $\Theta$ 的 MAP 估计与条件期望估计（estimators）。

> <span style="color:#7f8c8d;">[原页此处 OCR 有破损] 本条 Example 8.8 上两行（"…transition probability graph …" 之外的正文）在本页源 OCR（`Example S.S. We consider the model in Example 8.4...`）中总体可读，唯个别数字/符号残缺；上句按原书语义完整转述。Example 8.8 的推导在下一页（p425）继续。</span>
<!-- ===== PDF p433 ===== -->

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）**</span>

<span style="color:#7f8c8d;">本页位于书目页 425，页眉为「Sec. 8.2 / Point Estimation, Hypothesis Testing, and the MAP Rule」。页首承接上一页对掷硬币示例（其后验在 §8.1 的 Example 8.4 中给出）的点估计（point estimation）讨论——先行并给出后验概率密度函数（posterior PDF）为 Beta 密度（beta density），据此推出最大后验（MAP）估计与条件期望估计；页中部转入本节的「假设检验（Hypothesis Testing）」小节。注意：本书以 $\Theta$ 记未知参数（取值为 $\theta$），页内侧与正文中的 `8`/`e`/`9` 均为 OCR 对希腊字母 $\Theta$、$\theta$ 的误读。</span>

---

承接上一页的论述：如 Example 8.4 所示，当 $X = k$ 时，$\Theta$ 的后验概率密度函数（posterior PDF）是一个参数为 $\alpha = k + 1$、$\beta = n - k + 1$ 的 Beta 密度（beta density）：

```math
f_{\Theta|X}(\theta \mid k) =
\begin{cases}
\dfrac{1}{B(k+1,\, n-k+1)} \,\theta^{k}(1-\theta)^{n-k}, & \text{若 } \theta \in [0,1],\\[2pt]
0, & \text{其他情形}.
\end{cases}
```

这个后验概率密度函数（posterior PDF）恰好只有一个峰。为确定其位置，我们把表达式 $\theta^{k}(1-\theta)^{\,n-k}$ 对 $\theta$ 求导，并令导数为零，得到

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏]「令导数为零，得到」之后的中间一步公式在源 OCR 中被打散成碎片（`"which yields … L) _ u - k. n _"`），其确切形状无法逐字复原；但紧接其后的结果可辨，即下方 $\hat{\theta} = \frac{k}{n}$，此即最大后验（MAP）估计的位置。</span>

由此得到

```math
\hat{\theta} = \frac{k}{n}.
```

这就是最大后验（MAP，maximum a posteriori）估计（MAP estimate）。

为得到条件期望估计（conditional expectation estimate），我们使用 Beta 密度的均值公式（参见 Example 8.4）：

```math
E[\Theta \mid X = k] = \frac{k+1}{n+2}.
```

注意，当 $n$ 的值较大时，最大后验（MAP）估计与条件期望估计几乎重合。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先声明记账约定，本条与前面讲 Beta 后验参数、以及后面讲线性 LMS 的那条注共用同一套：采用 $a=\alpha-1$ 版，即 Beta$(\alpha,\beta)$ 等价于「在均匀先验之上看过 $\alpha-1$ 次成功、$\beta-1$ 次失败」。所以本条的「伪计数」一律指 $\alpha-1$，不是 $\alpha$；换个约定数就会整体差一。
>
> 先说 MAP 为什么恰好等于样本频率。Beta density（Beta 密度）的对数在 $\theta$ 上是对数似然加一个常数：uniform prior（均匀先验）是常数，求导后整个消失，剩下的正是二项似然的导数，零点落在 $k/n$。换句话说，均匀先验下的 MAP（maximum a posteriori，最大后验）与 maximum likelihood estimate（最大似然估计）重合，先验没有移动最优点，只改变了曲线的整体高度。
>
> 条件期望则读 Beta 的均值，等于 $(k+1)/(n+2)$。在本约定下这**不是**「先验预置了一成一败」：先验的伪计数是 $\alpha-1=\beta-1=0$，一个虚拟样本都没有；$+1$ 出现在分子分母上，是因为可预测分布的参数是 $\alpha$ 与 $\beta$ 而不是 $\alpha-1$ 与 $\beta-1$。原注写「这一对伪计数相当于先验里预置了一次成功、一次失败」，与前面那条注的声明正好相反，属于串了记账法；按本约定应读作「均匀先验加零个伪计数，$(k+1)/(n+2)$ 的加一是端点零幂次的影子」。工程上仍叫它 Laplace smoothing（拉普拉斯平滑）没有问题，只是解释时必须点明用哪套约定。
>
> 时间线也顺手对齐：这条规则首次出现在 Laplace 1774 年的 Mémoire sur la probabilité des causes par les événements，系统化在 1812 年的 Théorie analytique des probabilités，通俗化在 1814 年的 Essai philosophique。原注只写「1812 年前后」并不错，但把三个年份写全会更清楚，也不会与前面注里的 1774 与 1814 打架。
>
> 两者的差可以精确写出：$\frac{k+1}{n+2}-\frac{k}{n}=\frac{n-2k}{n(n+2)}$。分母恒正，符号由 $k$ 与 $n/2$ 的大小决定。$k<n/2$ 时均值大于众数，$k>n/2$ 时均值小于众数。也就是说，条件期望总是被拉向 $1/2$，拉的量随 $n$ 增大而衰减。这就是 shrinkage（收缩）的代数形式，方向与距离都能一眼读出。
>
> 代数字确认方向。$n=10$、$k=8$ 时，MAP 是 $0.8$，均值是 $9/12=0.75$，被拉向 $0.5$；$n=10$、$k=2$ 时，MAP 是 $0.2$，均值是 $3/12=0.25$，同样被拉向 $0.5$。两端偏差方向相反、衰减速度相同，都是 $n+2$ 分之一量级。这也解释了为什么大样本下两个估计几乎重合：正文那句「当 $n$ 的值较大时，最大后验估计与条件期望估计几乎重合」不是修辞，是误差项的阶。
>
> 边界情形值得单独看。$k=0$ 时 MAP 是 $0$，条件期望是 $1/(n+2)$；$n=100$ 时后者约 $0.0098$。前者断言下次必不出现，后者给出一个随 $n$ 衰减的小正数。哪个更合理取决于怎么看「一百次都没出现」这件事：频率派的极大似然说「下次必不出现」，贝叶斯则给后验 Beta$(1,101)$，它的均值 $1/102$ 天然带着均匀先验在两端零幂次留下的余量，于是给出一个随 $n$ 衰减的小正数。这是两种学派在同一公式上的可见分界线。
>
> 还有一个常被忽略的性质：MAP 依赖参数化，条件期望在各自坐标系下按变量代换仍对得上。把 $\theta$ 换成 $u=\theta^2$，密度的 Jacobian（雅可比）因子会改变峰的位置。上面 $k=8$、$n=10$ 的 Beta 后验可以验算：$\theta$ 的众数在 $0.8$，换成 $u$ 之后密度的众数对应 $\theta=7/9\approx0.7778$，位置确实移动了。所以 MAP 不是坐标无关的，这是贝叶斯统计界对它的标准批评之一。
>
> 顺便把不确定性也对比一下，这里原注的阶判断要改。Beta 后验的方差是 $\alpha\beta/((\alpha+\beta)^2(\alpha+\beta+1))$，$n=10$、$k=8$ 时它是 $27/1872=0.0144$，标准差 $0.12$。方差本身按 $1/n$ 衰减（$O(1/n)$），而两个点估计之间的差 $\frac{\lvert n-2k\rvert}{n(n+2)}$ 同样是 $O(1/n)$——同一个阶，谈不上谁衰减得更慢。定 $k/n$ 为常数 $x$ 时，比值 $V/\Delta$ 趋于 $x(1-x)/(1-2x)$，是个与 $n$ 无关的常数：$n=10$、$k=2$ 时比值 $0.289$，$n=100$、$k=20$ 时 $0.270$，$n=1000$、$k=200$ 时 $0.267$，三个数稳定在 $0.27$ 附近，正好说明了「同阶」。所以「差衰减得慢一点」这句话没有依据，正确的说法是二者同阶、比值有界。
>
> 跨课程看，加一平滑与 ridge regression（岭回归）是同一件事的两种度量：都在分母上加一个常数，都把估计拉向先验中心。机器学习里它叫 regularization（正则化），统计里它叫收缩估计，信息论里它对应把经验分布向均匀分布做一次混合。名字不同，机制是同一个「往中心拉一点」，拉多拉少由伪计数的个数与样本量之比决定。

在没有额外假设的情况下，一个点估计（point estimate）对其精度并不带有任何保证。例如，最大后验（MAP）估计可能落在后验分布主体（bulk of the posterior distribution）相当远之外。因此，通常宜再报告一些附加信息，例如条件均方误差（conditional mean squared error）$E\big[(\hat{\Theta}-\Theta)^{2} \mid X = x\big]$。在下一小节中，我们将进一步讨论这一问题。特别地，我们将重新回到前面两个例子，并为最大后验（MAP）估计与条件期望估计计算条件均方误差。

<span style="color:#c0392b;">**假设检验（Hypothesis Testing）**</span>

在假设检验（hypothesis testing）问题中，$\Theta$ 取 $m$ 个值中的一个，即 $(\theta_1, \ldots, \theta_m)$，这里 $m$ 通常是一个很小的整数；经常 $m = 2$，此时我们处理的是一个二元假设检验（binary hypothesis testing）问题。我们把事件 $\{\Theta = \theta_i\}$ 称为第 $i$ 个假设（hypothesis，记为 $H_i$）。

一旦观测到 $X$ 的取值 $x$，我们就可以用贝叶斯准则（Bayes' rule）为每个 $i$ 计算后验概率（posterior probabilities）$P(\Theta = \theta_i \mid X = x) = P_{\Theta|X}(\theta_i \mid x)$。然后，依据最大后验（MAP）准则（MAP rule），我们选择后验概率最大的那个假设。（如果出现平局——若干个假设同时取得最大的后验概率——我们可在它们之间任意选择。）如前文所述，就所有决策准则（decision rules）而言，MAP 准则是最优的，因为它使正确决策（correct decision）的概率达到最大。
<!-- ===== PDF p434 ===== -->

> <span style="color:#7f8c8d;">本页书页号 426，页眉为 Bayesian Statistical Inference / Chap. 8，属第 8 章 §8.2「点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）」内部。本页顶部展开该节下的小节「The MAP Rule for Hypothesis Testing（假设检验的 MAP 准则）」，先陈述该准则及其两个性质公式，随后给出本节第 3 个、也就是最后一个例题 **Example 8.9**（两枚有偏硬币例）——承接同一节 §8.2 的 Example 8.7、8.8 之后，编号连续。</span>

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）（续）**</span>

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）（续）**</span>

<span style="color:#c0392b;">**假设检验的 MAP 准则（The MAP Rule for Hypothesis Testing）**</span>

给定观测值（observation value）$x$，MAP 准则（MAP rule）会选择使得后验概率（posterior probability）$P(\Theta = \theta_i \mid X = x)$ 取值最大的那个假设（hypothesis）$\Theta = \theta_i$。

等价地，它会选择使得下面两式中对应的那个表达式取值最大的假设 $\theta_i$：若 $X$ 为离散，则取 $p_{\Theta}(\theta_i)\,p_{X|\Theta}(x \mid \theta_i)$；若 $X$ 为连续，则取 $p_{\Theta}(\theta_i)\,f_{X|\Theta}(x \mid \theta_i)$。

MAP 准则对任意观测值 $x$ 都使选择错误假设（incorrect hypothesis）的概率最小化，并且是在所有决策准则（decision rules）中使错误概率（probability of error）最小化的那个准则。

一旦我们推导出 MAP 准则，也可以把相应的正确决策（correct decision，或错误）概率，看作观测值 $x$ 的函数来计算。具体地，若 $\hat{\Theta}_{MAP}(x)$ 是当 $X = x$ 时由 MAP 准则选出的假设，则正确决策的概率为

```math
P\left( \Theta = \hat{\Theta}_{MAP}(x) \mid X = x \right).
```

进一步，若 $S_i$ 表示所有使得 MAP 准则选出假设 $\theta_i$ 的 $x$ 之集合，则正确的整体决策概率为

```math
P\left( \Theta = \hat{\Theta}_{MAP}(X) \right) = \sum_i P(\Theta = \theta_i,\ X \in S_i),
```

而相应的错误概率为

```math
P\left( \Theta \neq \hat{\Theta}_{MAP}(X) \right) = 1 - P\left( \Theta = \hat{\Theta}_{MAP}(X) \right).
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一段是「为什么 MAP 最优」的最后一块拼图，也是那个不起眼的集合记号真正的用处。它把「对每个 $x$ 选后验最大的假设」翻译成「把观测空间切成若干块」，于是逐点最优与整体最优之间只差一次求和。
>
> 划分要先写清楚。每个观测值归给后验最大的那个假设，并列时固定一种打破方式，于是观测空间被切成互不相交的区域，并集是全部可能观测。这个集合族就是决策规则的全部内容：任何决策规则都对应一个划分，反过来任何划分也对应一个规则。所以「在所有准则中挑最好的」等价于「在所有划分中挑最好的」。
>
> 正确概率就写成全概率：对每个假设，取参数等于该假设且观测落在对应区域内的概率，再对假设求和。这是 6.042J 的 partition（划分）加全概率在连续情形的一次直接应用，只不过要求每个区域是可测集，用 Lebesgue 积分写时更自然。
>
> 最优性的证明只有三行。对任意准则，其正确概率是每个区域上「观测密度的积分再乘该区域内后验最大的那份」之和；把每个点上的被积函数换成对所有假设取最大，积分只会变大；再把这些最大值归到它自己所属的区域，得到的就是 MAP（maximum a posteriori，最大后验）的正确概率。两步合起来就是「任意准则不超过 MAP」，等号只在两个准则几乎处处一致时成立。
>
> 关键是「逐点」这两个字。整体正确率是各点贡献的积分，而积分是线性算子，所以逐点最大必然整体最大。反过来，若在某个点上放弃最大，就等于自愿让出那一小块概率，其它点无法补偿，因为每个点只贡献自己那一份。这个可加性是整个证明的支点，也是它不能直接推广到「整体相关」问题上的原因。
>
> 代数字看先验的分量。两类等方差高斯，第一类下观测服从均值 $0$ 的单位方差正态，第二类下均值 $2$。等先验时边界在 $x=1$，正确率是 $\Phi(1)=0.8413$。若先验改成 $0.7$ 与 $0.3$，对数后验差是线性的，边界移到 $1+\frac12\log(0.7/0.3)=1.424$，正确率变成 $0.7\times0.9225+0.3\times0.7180=0.8612$。先验换了、边界动了，正确率涨 $0.02$，这是「先验不是装饰」的定量版本。
>
> 边界的几何也值得看。等方差高斯下，两类的对数密度差是观测的线性函数，边界解出来是一条直线；方差不等时差是二次的，边界变成圆锥曲线。所以决策边界是不是线性，完全由似然形状决定，与算法是否叫线性分类器无关。Strang 18.06 里两条曲线的交点、二次型等值线的相切，都是这一句话的几何版本。
>
> 反例：如果为了省事硬把边界定在 $1$，而先验其实是 $0.7$ 与 $0.3$，正确率就退回到 $0.8413$，白丢 $0.02$。更糟的是把区域按输入顺序而非后验切分，那时每个点都可能选到次优假设，错误率会显著上升。最优性定理的每个字都在说同一件事：划分必须由后验决定，不能由别的规则决定。
>
> 跨课程看，这就是模式识别里 Bayes decision boundary（贝叶斯决策边界）的原型，也是 6.006 里「贪心逐点最优推出全局最优」的少见成功案例。多数问题里贪心不最优，这里之所以成立，是因为目标函数按点可加；一旦目标里出现跨点的耦合项，逐点最优就不再推出整体最优。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 源 OCR 中，正确决策公式下方紧跟英文「and the corresponding probability of error is」（对应于错误概率为……）这一半句后，错误概率的公式本体缺失/被打碎，未给出具体算式（原书动机与上一行为同一主题）。上文按逻辑补出错误概率为整体正确决策概率的补 $\left(1 - P(\Theta = \hat{\Theta}_{MAP}(X))\right)$，此为数学上必然成立的互补关系；若原书式样略有差异，以原书为准。未见需臆造的数值。</span>

下面是一个典型的、针对两个假设情景做 MAP 准则计算的例子。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.9（两枚有偏硬币，Two Biased Coins。）**</span>

我们有两枚有偏硬币（biased coins），分别称为硬币 1 与硬币 2，它们抛出正面的概率分别是 $p_1$ 与 $p_2$。我们随机选择一枚硬币（两枚硬币被选中的可能性相同），并想根据单次抛掷的结果来推断所选的是哪一枚。令 $\Theta = 1$ 与 $\Theta = 2$ 分别表示「选中硬币 1」与「选中硬币 2」这两个假设。令 $X$ 依抛掷结果是正面还是反面而分别取值为 $1$ 或 $0$。

运用 MAP 准则，我们比较 $p_{\Theta}(1)\,p_{X|\Theta}(x \mid 1)$ 与 $p_{\Theta}(2)\,p_{X|\Theta}(x \mid 2)$，并选择使相应表达式取值最大的那枚硬币。由于 $p_{\Theta}(1) = p_{\Theta}(2) = 1/2$，我们只需比较 $p_{X|\Theta}(x \mid 1)$ 与 $p_{X|\Theta}(x \mid 2)$，并选出其所对应的观测抛掷结果最为可能出现的那一方。于是，例如若 $p_1 = 0.46$，$p_2 = 0.52$，且抛掷结果是反面，则我们注意到

```math
P(\text{tail} \mid \Theta = 1) = 1 - 0.46 > 1 - 0.52 = P(\text{tail} \mid \Theta = 2),
```

> <span style="color:#7f8c8d;">衔接下一面（PDF p435）：Example 8.9 在本页给出开头与「反面结果」情形的比较算式后，下一页继续完成该例（处理正面情形与最终结论）。</span>
<!-- ===== PDF p435 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，正文为 **Example 8.9** 的收尾部分（页首无新节、无新标题，内容明显延续上一页关于「两枚硬币、按观测到的正面数进行假设检验」的讨论），故标题带「（续）」。本页给出 MAP 决策准则的归纳、其对观测空间 {0,1,…,n} 的划分、误差概率（probability of error）公式，以及图 8.5 的图注。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏] 本页为整套教材中文字密度最高的页之一，OCR 仅存零散单词与碎片（如 `and decide in favor of coin 1`、`come is most likely …`、`k(l PI − PI)n−k`、`Θ = 1 if k ≤ k*, where k* =`、`k = k* + 1`、`> P2 1 − P2 )n−k` 等）。下方按本节（§8.2 两硬币假设检验）的真实语义做忠实重建，凡关键数值/符号无法从原文核实的均加灰注释标明，未臆造原文未出现的具体数字。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.9（续）——两枚硬币的假设检验与 MAP 准则（coin selection / hypothesis testing）**</span>

……并因此**决定选择硬币 1（coin 1）**，即判定硬币 1 在给定观测下更为可能（is most likely）。需要指出的是，这一判定**关键取决于先验（prior）假设** $p_{\Theta}(1) = p_{\Theta}(2) = 1/2$：正是这个「两枚硬币先验等可能」的设定，才使决策可以完全由似然（likelihood）比较驱动。

因此，若 $X = k$，我们通过如下方式决定：**选取使得后验概率（posterior probability）最大的那个假设 $\Theta = i$**。具体地，后验为

```math
p_{\Theta|X}(i\mid k) = c(k)\, p_{\Theta}(i)\, p_{X|\Theta}(k\mid \Theta = i),
```

其中 $c(k) = 1/p_X(k)$ 是一个仅依赖 $k$ 的归一化常数（normalization constant）。于是对两个假设分别比较上面的量即可。

由于本例中 $p_{\Theta}(1) = p_{\Theta}(2) = 1/2$，MAP 准则便等价于**选取使 $p_i^{\,k}(1-p_i)^{\,n-k}$ 最大的那个假设 $\Theta = i$**，$i=1,2$。等价地，对似然比（likelihood ratio）做比较：

```math
p_{\Theta|X}(1\mid k) \;\overset{?}{\gtrless}\; p_{\Theta|X}(2\mid k)
\iff p_1^{\,k}(1-p_1)^{\,n-k} \;\overset{?}{\gtrless}\; p_2^{\,k}(1-p_2)^{\,n-k}.
```

这一准则把观测空间（observation space）$\{0,1,\ldots,n\}$ 划分成两个互不相交（disjoint）的集合，在这两个集合中，两个假设 $\Theta = 1$ 与 $\Theta = 2$ 分别各占优势。在取定一个适当的阈值（threshold）$k^\ast$ 后，决策准则即为：

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 决策阈值 $k^\ast$ 的显式表达式在 OCR 中被破坏（残片仅余 `where k* = … yo …`），无法逐字复原；此处按标准假设检验推理方向给出「决定 $\Theta = 1$，当 $k \le k^\ast$；否则选择 $\Theta = 2$」。方向依据：图 8.5 中 $p_1 = 0.46 < p_2 = 0.52$，故正面数越少越倾向硬币 1，即 $k \le k^\ast$ 判 $\Theta = 1$。</span>

<span style="color:#00838f;">**决定选择 $\Theta = 1$，当且仅当 $k \le k^\ast$；否则选择 $\Theta = 2$。**</span>

据此，误差概率（probability of error）可由全概率公式（total probability theorem）求得：对 $\Theta=1$ 却落在 $X \ge k^\ast+1$ 的区域、以及 $\Theta=2$ 却落在 $X \le k^\ast$ 的区域这两种情形求和。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 二选一假设检验其实是所有「判决」任务的骨架。原文那句加粗的结论是「决定选择 $\Theta = 1$，当且仅当 $k \le k^\ast$；否则选择 $\Theta = 2$」，把这句话拆开看，它只做了一件事：把观测空间 $\{0,1,\dots,n\}$ 切成两段，切口就是阈值 $k^\ast$。所谓检验，就是把「连续证据」换成「一次比较」。
>
> 第一性原理是后验之比与似然比只差一个先验比常数。$\frac{P(\Theta=1\mid k)}{P(\Theta=2\mid k)}=\frac{p_\Theta(1)}{p_\Theta(2)}\cdot\frac{p_{X\mid\Theta}(k\mid1)}{p_{X\mid\Theta}(k\mid2)}$，左边大于 $1$ 就判 $\Theta=1$，等价于右边那个 likelihood ratio（似然比）超过先验比的倒数。于是 MAP（maximum a posteriori，最大后验）判决等价于「似然比超过阈值」，并把错误概率压到最低。这里原注有一句必须删掉：「这是全书第一次见到似然比」——同一页在推导阈值之前，正文已经明确写过一次 likelihood ratio（似然比）的比较，并给出了两个后验的比值式。准确的说法是：这是全书第一次把似然比写成显式的阈值判据，而不是第一次出现这个对象。
>
> 命名模板：hypothesis（假设）配 testing（检验）＝「拿数据去审理一组候选命题」。这个词组与统计推断里的 hypothesis testing（假设检验）同名，但本书这一节的 domain（适用范围）更窄：只有两个假设、只做点判决、不设显著性水平，所以不要拿 $p$-值那一套语言直接套进来。反过来，纯 MAP 也不等于 Neyman–Pearson 检验：前者固定先验、最小化平均错误率，后者固定第一类错误的概率、最小化第二类错误，两者的优化目标不同，只是共用似然比这条轴。
>
> 跨课程（通信 / 检测理论）：本例在判别哪枚硬币，与判定来信是哪种信号本质相同。在加性高斯噪声下、且两个候选信号能量相等（$\lVert a\rVert=\lVert b\rVert$）时，阈值规则进一步退化为比较两个内积，见后面的 matched filter（匹配滤波器）例。第二处要收一收的说法是「这正是 Neyman–Pearson 引理与 ROC curve（ROC 曲线）的发源地」：ROC 曲线与 Neyman–Pearson 引理是 1930 至 1940 年代才被系统提出的，把 6.041 这道硬币题说成它们的发源地是修辞而非史实；可以说的是一句更软也更有用的话：这里出现的「把判决压成一条阈值轴」的结构，正是后来 ROC 曲线横轴与纵轴的来历。
>
> 反例：若两类误判代价不对称（把垃圾邮件当正常，与把正常邮件当垃圾），纯 MAP 的 0-1 loss（0-1 损失）不再最优，阈值要向代价高的一侧偏移。设把 $\Theta=2$ 判成 $\Theta=1$ 的代价是 $c_{12}$、反向代价是 $c_{21}$，则判决条件变成 $\frac{p(k\mid1)}{p(k\mid2)}>\frac{c_{12}}{c_{21}}\cdot\frac{p_\Theta(2)}{p_\Theta(1)}$；等代价时 $c_{12}=c_{21}$，才退化成纯 MAP。原注说「无代价均衡只是等代价情形下的特例」方向是对的，但原文写作「判公」，应为「判决」，这属于错字而非用词问题。
>
> 再补一层数值直觉。取 $p_1=0.46$、$p_2=0.52$（图 8.5 的取值）、$n=10$，似然比随 $k$ 变化：$k=5$ 时是 $(0.46/0.52)^5(0.54/0.48)^5$ 的比值，约 $1.44$，还没越过先验比（等先验时为 $1$）；再往小走就会越过。阈值落在哪一格，完全由这个单调函数的零点决定，而单调性来自对数似然比 $\log\frac{p_1}{p_2}$ 与 $\log\frac{1-p_1}{1-p_2}$ 的符号相反——这正是「观测空间被切成两段」的代数解释，不是几何巧合。
>
> 跨课程再补一处（信息论）：把判决看作一次信息传输，错误概率的下界由两分布之间的 KL divergence（KL 散度）控制，Chernoff 界给出指数衰减率。于是「阈值取在哪」决定的是常数因子，「两类分布差多远」才决定指数；这也是为什么工程上先把特征做可分、再调阈值，而不是反过来。

```math
P(\text{error}) 
= P(\Theta = 1,\; X \ge k^\ast+1) \;+\; P(\Theta = 2,\; X \le k^\ast)
= p_{\Theta}(1)\,P(X \ge k^\ast+1\mid \Theta=1) \;+\; p_{\Theta}(2)\,P(X \le k^\ast \mid \Theta=2).
```

---

<span style="color:#00838f;">**[图] Figure 8.5**</span> —— Example 8.9 情形下的 **MAP 准则（MAP rule）**，其中 $n = 50$，$p_1 = 0.46$ 且 $p_2 = 0.52$。它绘制了两种假设各自的后验概率（posterior probabilities）$p_{\Theta|X}(i\mid k)$，$i = 1, 2$，并刻画了把观测空间划分成「选取 $\Theta=1$」与「选取 $\Theta=2$」两个部分的决策边界 $k^\ast$。
<!-- ===== PDF p436 ===== -->

> <span style="color:#7f8c8d;">§8.2 点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）中的续页。本页页首无新的小节标题，承接上一页关于“基于阈值的决策准则”的论述（故正文按「（续）」处理）。本页包含：阈值决策准则下误差概率关于阈值 $k$ 的函数曲线（图 8.5、图 8.6），例题的问题数据（$n=50$、$P_1$、$P_2 = 0.52$）、MAP 阈值决策规则（$\delta = 1$ 当 $k < k^*$），并在页末引入一个经典的通信（communication）例题——两台候选信号在被加性噪声污染后如何被接收与判决。源页为双栏排版，OCR 严重错乱、多处残损；下列译文仅还原可辨认的结构与数字，未臆造任何 OCR 未能给出数值。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">**Example 8.9（续，阈值型决策准则与误差概率，threshold-type decision rule）**</span>

……该[误差概率]是阈值（threshold）$k$ 的函数，对应一类基于阈值的决策准则（threshold-type decision rule）。当前例题中，MAP 准则（MAP rule）恰好对应[某个使误差最小的阈值 $k^*$]。

```math
\delta = 1 \quad \text{若 } k < k^* , \qquad \delta = 0 \quad \text{否则},
```

即[决策]规则由阈值 $k'$ 确定（cf. Example 8.9）[此处指该阈值规则与本域传播判定问题之间的对照]。

> <span style="color:#7f8c8d;">图注（Figure 8.6）：某类[阈值]决策准则下，误差概率（probability of error）关于阈值 $k$ 的一条曲线。（源 OCR 中该图注的宾语（“误差概率”前的成分）残碎无法辨认，仅「as a function of the threshold $k$」「probability of error」等可辨。）</span>

> <span style="color:#7f8c8d;">图注（Figure 8.5）：使误差概率最小化的决策准则的阈值（the threshold of the decision rule which minimizes the probability of error）。（源 OCR 中图注对象字面残碎，按可辨单词「8.5. The threshold of the … probability of error … and minimizes…」还原。）</span>

本题数据为 $n = 50$，[两类误差概率]分别取 $P_1 = [无法辨认]$ 与 $P_2 = 0.52$，[这些取值]与[前一例]相同……

```math
P_1 = [\;], \qquad P_2 = 0.52, \qquad \text{阈值 } k = [\;] .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中 $P_1$ 的数值、以及阈值 $k$（或 $k^*$）的具体数值在源 OCR 中残缺（仅见「P2 = 0.52」「rule is k = …」「n = 50」等字样），无法识别，故留空，不臆造。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**（§8.2 未编号的说明例）经典的通信检测例（A Classical Example from Communication）**</span>

下面是一个出自通信（communication）领域、非常经典（classical）的例子。

考虑[两个候选信号] $\mathbf{a} = (a_1, \ldots, a_n)$ 与 $\mathbf{b} = (b_1, \ldots, b_n)$（原文[respectively]）。我们假设这两个候选信号[的能量] $A = a_1^2 + \cdots + a_n^2$ 与 $B = b_1^2 + \cdots + b_n^2$ [已知]。接收机（receiver）观测到[某一信号经信道传输后受到噪声污染的接收值]

```math
Y_i = [\;] F_i + W_i, \qquad i = 1, \ldots, n,
```

其中 $W_i$ 是相互 independent（独立）、且与[所发送信号]independent（独立）的标准正态随机变量（standard normal random variables）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上文含 $\mathbf{a}$、$\mathbf{b}$、能量 $A$、$B$、接收机观测 $Y_i$、发射信号项 $F_i$（或给定信号项）以及 $W_i$ 的标准正态假设等结构在上页与本源中均能辨认（「energy,!l, ai + … + b²」「Wi are standard normal random variables, independent of …」「transmitted …」等），但具体符号与数值（$F_i$ 的写法、能量 $A$/$B$ 之值、观测模型 ``Y_i`` 的精确形式）在 OCR 中残碎到无法逐字复原。该校验点将在后续页给出 MAP 判决（选距离更近的信号）及阈值规则，届时可据以锚定核对。本页仅还原骨架，未臆造公式细节。</span>

> <span style="color:#7f8c8d;">衔接说明：本页为 §8.2 的尾页段（书页约 p428，尚未进入书页 p430 起的 §8.3）。页末新起的通信检测例是 §8.2 中一个**未编号**的说明性例子（源页先说 "The following is a classical example from communication…"，随后并无任何例号标注），其主体将延续到后续页；此处未给它套用「Example 8.9」等编号，确切归属以原书为准。</span>
<!-- ===== PDF p437 ===== -->

<span style="color:#7f8c8d;">§8.2　点估计、假设检验与 MAP 准则（Point Estimation, Hypothesis Testing, and the MAP Rule）中部续页。书页 p429。本页承接上一页（书页 p428）正在进行的信号检测/匹配滤波器（matched filter）例子（§8.2 中那个**未编号**的说明性通信检测例）之继续，页首无新节标题，故以「（续）」续讲；本页为该通信例的收尾，并在段末给出其 $m>2$ 个等可能消息情形的推广。§8.2 的 8.7 / 8.8 / 8.9 这三个编号例子已在前页翻毕，本页所续为未编号的说明例。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**信号检测与匹配滤波器（matched filter）（上接 §8.2 未编号的通信检测例，续）**</span>

在假设 $\Theta = 1$ 之下，各 $X_i$ 是均值为 $a_i$、方差为单位方差（unit variance）的相互独立正态随机变量（independent normal random variables）。于是，由贝叶斯准则（Bayes' rule），第一个消息被发射的后验概率依如下似然（likelihood）密度计算。

```math
f_{X\mid\Theta}(x\mid 1) \;=\; \left(\frac{1}{\sqrt{2\pi}}\right)^{\!n}
\exp\Big(-\tfrac{1}{2}\sum_{i=1}^{n}(x_i-a_i)^2\Big).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页顶「Thus,」与「Similarly,」两处之后所对应的似然密度公式在源 OCR 中呈空白（仅余 "Thus," / "Similarly," 字样，无公式本体），且「From Bayes' rule … is」之后的后验概率公式同样缺失。上文与下文均按该例已知的匹配滤波器结构与 "$a_i$ 换成 $b_i$ 得 $\Theta=2$ 情形"的原文提示重建，未臆造任何原文未暗示的数值或系数。</span>

类似地，在假设 $\Theta = 2$ 之下，各 $X_i$ 以 $b_i$ 为均值、仍为单位方差。

```math
f_{X\mid\Theta}(x\mid 2) \;=\; \left(\frac{1}{\sqrt{2\pi}}\right)^{\!n}
\exp\Big(-\tfrac{1}{2}\sum_{i=1}^{n}(x_i-b_i)^2\Big).
```

由贝叶斯准则，在给定观测 $X=x$ 时，第一个消息被发射（即假设 $\Theta=1$）的概率为

```math
P(\Theta = 1 \mid X = x)
\;=\; \frac{p_1\, f_{X\mid\Theta}(x\mid 1)}
{p_1\, f_{X\mid\Theta}(x\mid 1) + p_2\, f_{X\mid\Theta}(x\mid 2)},
```

其中 $p_1 = P(\Theta=1)$、$p_2 = P(\Theta=2)$ 为两个消息的先验概率（prior probabilities）。

对平方项（squared terms）展开并利用假设
$\sum_{i=1}^{n} a_i^2 = \sum_{i=1}^{n} b_i^2$ 之后，上述表达式可化简为关于内积（inner product）$\sum_{i=1}^{n} a_i x_i$ 与 $\sum_{i=1}^{n} b_i x_i$ 的大小比较。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「After expanding the squared terms … this expression simplifies to」与「The formula for $p(\Theta=2\mid X=x)$ is similar, with the $a_i$ in the numerator replaced by $b_i$」两处之间的最终化简式在源 OCR 中缺失（原文「。」后直接跳到下一句）。该化简式根据标准推导重建为"将 $\sum_{i=1}^n a_i^2 = \sum_{i=1}^n b_i^2$ 代入后，后验比较退化为内积 $\sum a_i x_i$ 与 $\sum b_i x_i$ 之比/大小关系"，此关系与下页判断规则形式一致；未臆造具体后验数值。</span>

$p(\Theta = 2 \mid X = x)$ 的公式与之类似，只是把分子中的 $a_i$ 替换为 $b_i$。

按照 MAP 准则（MAP rule），我们应选择具有最大后验概率（posterior probability）的假设，从而得到：

```math
\begin{aligned}
\text{选择 } \Theta = 1, \quad & \text{若} \quad \sum_{i=1}^{n} a_i X_i > \sum_{i=1}^{n} b_i X_i,\\
\text{选择 } \Theta = 2, \quad & \text{若} \quad \sum_{i=1}^{n} a_i X_i < \sum_{i=1}^{n} b_i X_i.
\end{aligned}
```

（若上述内积相等，则两个假设都可任选其一。）这种用于判定期所发信号（signal transmitted）的特定结构被称为**匹配滤波器（matched filter）**：我们把接收到的信号 $(X_1, \ldots, X_n)$ 通过与两个候选信号各自形成内积 $\sum_{i=1}^{n} a_i X_i$ 与 $\sum_{i=1}^{n} b_i X_i$，来「匹配（match）」这两个候选信号；随即选择产生较高值（"最佳匹配（best match）"）的那个假设。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述判断规则中 $\sum_{i=1}^{n} a_i X_i$ 与 $\sum_{i=1}^{n} b_i X_i$ 的求和上下限在源 OCR 中被打散（出现孤立的光标碎片如 `L aiXi`、`L biXi`、零散的 `i= l` 等），此处按文中「Earlier forming inner products」与上文出现的 $\sum_{i=1}^n a_i^2 = \sum_{i=1}^n b_i^2$ 约定，统一还原为标准求和 $\sum_{i=1}^{n}$；不等号之上限与前文首个公式的方向一致。该页原文「最大后验概率，即得：」处的破折号与编号碎片未影响语义。</span>

这个例子可以推广到 $m>2$ 个等可能（equally likely）消息的情形。我们假设对消息 $k$，发射机发出固定的信号 $(a_1^k, \ldots, a_n^k)$，其中 $(a_1^k)^2 + \cdots + (a_n^k)^2$ 对所有 $k$ 都相同。于是，在同样的噪声模型（noise model）下，类似的推导表明：MAP 准则把接收信号 $(X_1, \ldots, X_n)$ 解码为使得 $\sum_{i=1}^{n} a_i^k X_i$ 最大的那个消息 $k$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> matched filter（匹配滤波器）把概率论的结论翻译成一张能被硬件直接执行的「内积打分表」。原文的说法是：把接收信号 $(X_1,\dots,X_n)$ 与两个候选信号各自形成内积 $\sum_i a_iX_i$ 与 $\sum_i b_iX_i$，选内积较大的那个假设；这种结构就叫 matched filter（匹配滤波器）。
>
> 第一性原理要从距离不等式出发，而不是从内积出发。噪声是 i.i.d.（独立同分布）高斯时，两类的对数似然差正比于
> $\lVert x-b\rVert^2-\lVert x-a\rVert^2=2(a-b)^\top x+\lVert b\rVert^2-\lVert a\rVert^2$。
> 判 $\Theta=a$ 当且仅当这个量大于零，两边除以 $2$ 就得
> $a^\top x-\frac12\lVert a\rVert^2\;>\;b^\top x-\frac12\lVert b\rVert^2$。
> 也就是说，正确的打分函数是 $a^\top x-\frac12\lVert a\rVert^2$，即「内积减去半个能量」。当 $\lVert a\rVert=\lVert b\rVert$ 时两个常数相消，判据才退化成单纯比内积——原文的设定正是这一情形，所以它写内积并没有错，错的只是把这一点当成了普遍规律。
>
> 这里必须更正原注的一处。它说「若两个候选信号能量不等，必须先归一化能量后再比」，这个处方不对，而且可以被一个反例直接推翻。取 $a=(1,0)$、$b=(1.5,0)$、$x=(1.2,0)$：内积分别是 $1.2$ 与 $1.8$，按内积会选 $b$；把内积除以各自的模长，两个数都等于 $1.2$，平分秋色，什么也没判出来；而按 $a^\top x-\frac12\lVert a\rVert^2$ 算，$a$ 得 $0.7$、$b$ 得 $0.675$，选 $a$。哪个对？直接算距离更硬：$\lVert x-a\rVert^2=0.04$，$\lVert x-b\rVert^2=0.09$，$a$ 更近，所以 MAP（maximum a posteriori，最大后验）确实选 $a$。归一化内积在这里恰好失效，因为它丢掉了能量差这一项信息，而那一项正是判据的一部分。
>
> 命名模板：matched filter（匹配滤波器）里的「匹配」指滤波器冲激响应与候选信号本身匹配，也就是对信号做相关，而不是去匹配噪声；correlation receiver（相关接收机）是它在模拟实现里的名字，两者是同一个运算的两个说法。
>
> 跨课程（信号与系统 / 18.065 内积几何）：这正是在欧氏空间里把点投影到信号方向上，$a^\top x$ 是 $x$ 在 $a$ 方向上的投影长度乘 $\lVert a\rVert$。几何上有用的读法是：等能量时「离谁近」与「在谁方向上投影长」等价；能量不等时两者不等价，必须回到 $-\frac12\lVert a\rVert^2$ 这个偏移项，它相当于把每个候选点球心从原点平移出去。把 $a,b$ 换成一般信号向量即得一般线性检测，多类情形就是对每个 $k$ 算 $a^{k\top}x-\frac12\lVert a^k\rVert^2$ 取最大，这也正好解释了正文推广到 $m>2$ 时为何要求「$(a_1^k)^2+\cdots+(a_n^k)^2$ 对所有 $k$ 都相同」——只有能量相等，那个偏移项才可以被统一丢掉。
>
> 反例三条。其一，就是上面那组数：能量不等时纯内积会向「更长的信号」倾斜，长约 $1.5$ 倍的 $b$ 白拿了 $50$ 分之一的优势，恰好把本该判给 $a$ 的点抢走。其二，噪声不是白高斯时（有色噪声、相关噪声），内积要换成 $\Sigma^{-1}$ 加权的内积 $a^\top\Sigma^{-1}x-\frac12a^\top\Sigma^{-1}a$，形状不变、内积变；把白噪声的结论直接搬过去，等于假定协方差是单位阵。其三，先验不等时还要再加 $\log p_\Theta(a)$ 这一项，于是「比内积」连在等能量下也不够了。
>
> 数值上再补一句：$a^\top x-\frac12\lVert a\rVert^2$ 与 $\lVert x-a\rVert^2$ 只差一个与假设无关的 $\lVert x\rVert^2$，所以两者给出同一个 argmax（最大值点）。工程上更常算距离平方，因为它是非负的、能直接用平方和硬件累加；只在需要把判决写成一条阈值时才改用内积形式。
<!-- ===== PDF p438 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）**</span>

> <span style="color:#7f8c8d;">本页（书页 p430）为 §8.3 小节标题「Bayesian Least Mean Squares Estimation（贝叶斯最小均方估计）」的起始页（running header「LEAST MEAN ESTIMATION」见于源页），故此处标出**新的 §8.3 小节标题**（非续页）。页首承接上一页（书页 p429）末尾关于条件均方误差（conditional mean squared error）的论述收束而来，正文自该叙述的中段接续。本页通篇为 LMS 估计的推导正文：先论证「在没有观测时，用常数 $\hat\theta=E[\Theta]$ 估计 $\Theta$ 可最小化均方误差（mean squared error）$E\big[(\Theta-\hat\theta)^2\big]$，最小值即方差 $\mathrm{var}(\Theta)$」，并给出图 8.7；页末转入「引入观测 $X$ 后的条件情形」。本页未出现新的 Example 编号，仅为衔接 Example 8.10 的推导铺垫。</span>

---

接着上一页，我们更加细致地考察条件均方误差（conditional mean squared error）这一层面。我们采用最小化均方误差（mean squared error）

<span style="color:#7f8c8d;">（原页此处式为横排连续性叙述，源 OCR 中被打散为断片，其确切排版不可复原。为忠实行文，以下按正文语义以一条顶格数学式概括。）</span>

```math
E\big[(\Theta-\hat\theta)^2\big],
```

作为估计 $\hat\theta$ 好坏的准则。我们说明这一准则会导出尽可能小的均方误差，从而顺带反映出估计量（estimator）的若干其他性质。

首先考虑没有观测的情形，即我们只能用一个**常数** $\hat\theta$ 来估计随机变量 $\Theta$。为把这一准则应用到 $\hat\theta$ 的选取上，我们把均方误差视为 $\hat\theta$ 的函数（见图 8.7），并对 $\hat\theta$ 求最小。

```math
E\big[(\Theta-\hat\theta)^2\big]
= \mathrm{var}(\Theta) + \big(E[\Theta]-\hat\theta\big)^2.
```

这个恒等式之所以成立，是因为当常数 $\hat\theta$ 从随机变量 $\Theta$ 中被减去时（零均值化），方差保持不变，即 $\mathrm{var}(\Theta-\hat\theta)=\mathrm{var}(\Theta)$，而期望则变为 $E[\Theta-\hat\theta]=E[\Theta]-\hat\theta$。于是均方误差 $E\big[(\Theta-\hat\theta)^2\big]$ 是 $\hat\theta$ 的二次函数，在 $\hat\theta = E[\Theta]$ 处取得最小值，且该最小值等于方差（variance）$\mathrm{var}(\Theta)$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这条恒等式 $E\big[(\Theta-\hat\theta)^2\big]=\mathrm{var}(\Theta)+\big(E[\Theta]-\hat\theta\big)^2$ 的分解，是把「最优估计」从公式变成几何的钥匙。原文把它放在「没有观测、只能用一个常数 $\hat\theta$ 估计 $\Theta$」这一步，接着指出均方误差是 $\hat\theta$ 的二次函数，在 $\hat\theta=E[\Theta]$ 处取得最小值，最小值等于方差。
>
> 第一性原理：均方误差关于 $\hat\theta$ 是严格下凸的二次式，二次项系数为 $1$，顶点自然落在 $E[\Theta]$ 处。把它写开就能看见结构：$E\big[(\Theta-\hat\theta)^2\big]=E[\Theta^2]-2\hat\theta E[\Theta]+\hat\theta^2$，配方成 $\mathrm{var}(\Theta)+\big(E[\Theta]-\hat\theta\big)^2$，其中 $\mathrm{var}(\Theta)=E[\Theta^2]-(E[\Theta])^2$。原文的证明走的正是这条：常数平移不改变方差，即 $\mathrm{var}(\Theta-\hat\theta)=\mathrm{var}(\Theta)$，而期望被平移成 $E[\Theta]-\hat\theta$，于是「方差 + 偏差的平方」两项各归各位。
>
> 几何读法更耐用。把随机变量当成向量，内积取 $E[UV]$，那么「常数」就是由常量函数张成的一条直线（一维子空间），把一个随机变量投影到这条直线上，得到的正是 $E[\Theta]$。投影的三个性质在这里一一对应：垂足唯一（二次式严格凸，最小点唯一）、残差与子空间正交（$E[\Theta-E[\Theta]]=0$）、勾股定理成立（$E\big[(\Theta-\hat\theta)^2\big]=\lVert\Theta-E[\Theta]\rVert^2+\lVert E[\Theta]-\hat\theta\rVert^2$）。这就是「方差 + 偏差平方」的几何来源，不是巧合的配方。
>
> 命名模板：把「取期望」称作 projection（投影）初看费解，实则只是换了一套内积：以 $E[\cdot]$ 作内积之后，随机变量就是函数向量，常量就是那条直线，而投影只是「在子空间里找最近点」的通用动作。identity（恒等式）这个词也别读成「公式变形」——它是勾股定理在概率空间里的一次实例。
>
> 跨课程（概率 ＋ 线性代数 / 18.06）：条件期望「是到可测子空间上的正交投影」这条概率论与线性代数之间最深的桥，在这里露出第一只脚：先投影到常量直线（无条件期望），后面再投影到「$X$ 生成的子空间」（条件期望），最后投影到「$X$ 的线性函数子空间」（线性 LMS）。三次投影共用同一个机制，只是子空间越来越大。18.06 里最小二乘的正规方程 $A^\top Ax=A^\top b$ 说的就是「残差与列空间正交」，逐字对应。
>
> 代数字：若 $\Theta$ 的均值是 $3$、方差是 $4$，那么 $\hat\theta$ 取 $3$ 时均方误差是 $4$；取 $5$ 时多出 $(3-5)^2=4$，合计 $8$；取 $-1$ 时多出 $16$，合计 $20$。差别全部落在偏差平方项上，方差那一项与 $\hat\theta$ 无关——这也是为什么「最小化均方误差」等于「把偏差压到零」。
>
> 反例：只要把目标换成绝对误差 $E\lvert\Theta-\hat\theta\rvert$，最优解就从均值挪到中位数（$x=0.5$ 的一维情形下，任何落在两观测之间的点都同样最优，不唯一）。再换成 0-1 损失，最优解更变成众数。这说明「最优」由损失函数定义，绝不能默认均值总是对的；同一条恒等式在更换损失后就不再成立，因为它依赖平方展开这个特殊结构。
>
> 还有一处容易忽略的适用边界：这条恒等式对任何随机变量都成立，不要求 $\Theta$ 连续、不要求二阶矩以外的任何条件（只要二阶矩有限）。所以它可以当作「均值是最佳常数估计」的完整证明，而不是某种渐近结论；一旦 $\mathrm{var}(\Theta)=\infty$（例如重尾分布），三项全部发散，等式退化成无意义的无穷减无穷。

> <span style="color:#7f8c8d;">图注（Figure 8.7）：均方误差 $E\big[(\Theta-\hat\theta)^2\big]$ 作为估计 $\hat\theta$ 的函数。最低点（最小值点）位于 $\hat\theta=E[\Theta]$ 处，此时最小均方误差（minimum mean squared error）即为 $\mathrm{var}(\Theta)$。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页为 §8.3 的推导性正文页，源 OCR 损坏极为严重：段落叙述大多被切成单词级碎片（如 `we`/`mean`/`by`/`and can`、残文 `i n more detail the cond i t i on al …`、`... we s h o w that i t resul ts in the least possible mean squared error ( hence` 等），图注 `Fig. 8 . 7 … The mean squared error E …` 亦不完整。正文中唯一可辨的完整式子为恒等式分解 `var(Z)+(E[Z])^2`（即 $\mathrm{var}(\Theta)+(E[\Theta]-\hat\theta)^2$）与「最小值即方差 var」这一结论。上文按原书 §8.3「先无观测、后引入观测」的标准叙述路径做忠实重建，未臆造任何原文未出现的具体数值、符号或额外疏例。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页末「引入观测 $X$」的过渡段（碎片 `now that we use an observation … we know the… error …`）在 OCR 中残损到仅余零散单词，其确切措辞无法逐字复原；此处按 §8.3 原文走向（转向「已知观测 $X=x$ 后，用条件期望 $E[\Theta\mid X=x]$ 作为最优估计」）忠实衔接，下一页（书目 p431）将继续这一发展并呈现逐点条件最小均方误差的公式。</span>

> <span style="color:#7f8c8d;">衔接下一面（书目 p431）：本页完成了「无观测情形下估计量为常数 $E[\Theta]$、最小均方误差为 $\mathrm{var}(\Theta)$」的论证（图 8.7），并引入观测 $X$。下一面将把同一论证推广到已知观测 $x$ 的条件情形，得出后验期望（posterior mean）$E[\Theta\mid X=x]$ 逐点最小化条件均方误差的结论，随后引出考察离散/连续观测的 Example 8.10 及后续例子。</span>
<!-- ===== PDF p439 ===== -->

<span style="color:#c0392b;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页（书目 p430）关于最小均方（least mean squares，LMS）估计的论述：页首 `Generally, the (unconditional) mean squared estimation error …` 紧接上一页中文句继续推进，随后落到本页正文核心——「最小均方估计的关键事实（Key Facts About Least Mean Squares Estimation）」框（含三条最小化事实及其证明脚注）。本页**没有出现新的 Example 8.x 标签**，故按 §8.3 正文续页处理，未新增例号。</span>

---

一般地，与某个估计量（estimator）$g(X)$ 相关联的（无条件）均方估计误差（mean squared estimation error）被定义为
```math
E\big[(g(X) - \Theta)^2\big].
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 该定义式在源 OCR 中整段缺失（"…is defined as" 之后公式区（pdf 第 8–9 行）为空白），此处按本段前后文（"estimator g(X)"）与 §8.3 的 LMS 定义补出形如 $E[(g(X)-\Theta)^2]$ 的常规定义式，非出自原件可辨认文字，仅为忠实还原，未虚构任何额外数值。</span>

如果我们把 $E[\Theta\mid X]$ 看作 $X$ 的一个估计量/函数（estimator/function），那么前面的分析表明：在所有可能的估计量之中，均方估计误差在 $g(X) = E[\Theta\mid X]$ 处达到最小。†

> <span style="color:#7f8c8d;">脚注（†）：</span>对于 $X$ 的任意给定取值 $x$，$g(x)$ 是一个数，因此
```math
E\big[(\Theta - g(x))^2 \mid X = x\big] \ge E\big[(\Theta - E[\Theta\mid X = x])^2 \mid X = x\big].
```
于是
```math
E[(\Theta - g(X))^2 \mid X] \ge E[(\Theta - E[\Theta\mid X])^2 \mid X],
```
这现在是不等式，但它涉及的是（作为 $X$ 的函数的）随机变量（random variables）。我们对两边取期望，并利用迭代期望律（law of iterated expectations），便可得出结论：对一切估计量 $g(X)$ 成立（即均方误差在 $g(X) = E[\Theta\mid X]$ 处最小）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 前一段脚注（†）在源 OCR 中被拆成碎片，仅余 "t For any given value x of X, g(x) is a number, and therefore, / Thus, …" 等零散字样，中间过渡句（"…which is now an inequality between random variables (functions of X). We take expectations of both sides, and use the law of iterated expectations, to conclude that …"）可逐字辨认；上文据此连贯转写，未增补原件未含的数值。</span>

---

<span style="color:#00838f;">**最小均方估计的关键事实（Key Facts About Least Mean Squares Estimation）**</span>

<span style="color:#2471a3;">**[key-facts]**</span>

• 在没有观测值（observations）的情况下，$E\big[(\Theta - \theta)^2\big]$ 在 $\theta = E[\Theta]$ 处取得最小：
```math
E\big[(\Theta - E[\Theta])^2\big] \le E\big[(\Theta - \theta)^2\big],
```
对一切 $\theta$ 成立。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 第一条不等式在源 OCR 中被拆碎（仅存 `E [(8 - 0) 2 ]`、`for all O` 等残片，"minimized when $\theta = E[\Theta]$" 的结论式与不等号方向由上下文还原）；上文按标准 LMS 事实补成上式，未虚构数值，仅补规格化符号（$\Theta$、$\theta$、平方、$\le$）。</span>

• 对 $X$ 的任意给定取值 $x$，$E\big[(\Theta - \theta)^2 \mid X = x\big]$ 在 $\theta = E[\Theta\mid X = x]$ 处取得最小：
```math
E\big[(\Theta - E[\Theta\mid X = x])^2 \mid X = x\big] \le E\big[(\Theta - \theta)^2 \mid X = x\big],
```
对一切 $\theta$ 成立。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 第二条不等式在源 OCR 中残缺（`E [ (8 - E[8 I X = xj) 2 1 X = x] < E [(8 - 0) 2 I X = x]`，其中 "xj" 为 "]$"、"2" 为平方、"<" 为原书所用的 $\le$）；上文据 §8.3 的 LMS 事实补成规范形式，未臆造数值。</span>

• 在所有基于 $X$ 估计 $\Theta$ 的估计量 $g(X)$ 之中，均方估计误差 $E\big[(\Theta - g(X))^2\big]$ 在 $g(X) = E[\Theta\mid X]$ 处取得最小：
```math
E\big[(\Theta - E[\Theta\mid X])^2\big] \le E\big[(\Theta - g(X))^2\big],
```
对一切估计量 $g(X)$ 成立。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 第三条（也是最核心）不等式在源 OCR 中仅余 `E (8 - g ( X)) 2` 与残缺的不等式块（pdf 第 31–36 行），结论式（"minimized when $g(X)=E[\Theta\mid X]$"）文字可辨、式本身缺损；上文按 §8.3 标准 LMS 结论补成上式，未虚构数值。此条即前面正文"在一切估计量中均方误差最小者"之概括。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 三条「最小均方事实」其实是同一件事的三层缩放：没有观测、已知 $x$、面对全部 $X$，最小点永远是（条件）期望。原文把它们并列写成三条，最后一条是核心：在所有基于 $X$ 的估计量 $g(X)$ 中，均方误差 $E\big[(\Theta-g(X))^2\big]$ 在 $g(X)=E[\Theta\mid X]$ 处最小。
>
> 第一性原理：对固定的 $x$，条件均方误差当作 $\hat\theta$ 的二次式，顶点在 $E[\Theta\mid X=x]$。展开写就是 $E\big[(\Theta-g(x))^2\mid X=x\big]=\mathrm{Var}(\Theta\mid X=x)+\big(E[\Theta\mid X=x]-g(x)\big)^2$，与上一条注的恒等式同一个结构，只是把期望换成了条件期望、把常数换成了 $g(x)$。再对 $x$ 取期望（迭代期望律，即 tower rule，塔律），就把逐点最优汇成全局最优：对每个 $x$ 都取最小的那个 $g$，积分之后仍然最小。
>
> 三层的分工要看清。第一层没有观测，可用的只有 $E[\Theta]$，子空间是常量直线；第二层已知 $x$，可用的就是那个数 $E[\Theta\mid X=x]$，子空间退化成「给定 $x$ 后的一切函数」；第三层要在所有 $g(X)$ 里挑，而逐点最优已经给出答案，所以第三层不需要新的数学，只需要把第二层的结果按 $x$ 拼起来。这就是为什么第三条看起来最强，证明却最短。
>
> 命名模板：LMS 全称 least mean squares（最小均方），名字点明的是目标——最小化「平方误差」，别按读音误读成「均方最小」；与之并列的还有 minimum mean squared error（最小均方误差，MMSE），在很多教材里是同义词，区别只在 LMS 更常指线性情形、MMSE 更常指无约束情形。conditional mean（条件均值）指「在断定为这一 $x$ 之后对 $\Theta$ 的均值」，与无条件的 $E[\Theta]$ 相对。
>
> 跨课程（18.06 / 18.065）：正交投影加平方目标是广义最小二乘、Kalman filter（卡尔曼滤波）与 Wiener filter（维纳滤波）共享的几何内核。§8.4 的线性 LMS 就是在「$X$ 的线性函数子空间」上重做同一投影——把 $g$ 限制成 $aX+b$ 之后，最优解由正规方程给出，一般不再等于条件期望；只有当条件期望本身是 $X$ 的线性函数时两者才重合，这正是后面抛硬币模型里那个好看的巧合。
>
> 代数字确认第三层比第二层多不了什么。设 $\Theta\mid X=x$ 服从均值 $x$、方差 $1$ 的正态，观测 $X$ 自身服从标准正态。则 $E[\Theta\mid X]=X$，最小均方误差是 $1$。若改用常数估计 $g\equiv0$，均方误差是 $E[X^2]+1=2$；若改用 $g(X)=0.5X$，均方误差是 $0.25E[X^2]+E[(0.5X-\Theta)^2\mid X]$ 的期望，算下来是 $0.25+1+0.25=1.5$。三种估计的排序是 $1<1.5<2$，与「$\Theta$ 在 $X$ 上的投影系数是 $1$」完全一致。
>
> 反例：若某 $x$ 下 $\Theta$ 的后验是双峰（例如两峰在 $0$ 与 $10$、各占一半），条件期望落在 $5$ 附近，也就是两峰之间的谷底——它给出均方误差最小的点，却偏离「最可能的取值」（posterior mode，后验众数）甚远。这时报 $5$ 在均方误差意义下正确，在「猜中一次」意义下几乎必错。提醒我们「期望 ≠ 最可能的代表值」，选哪个算子取决于下游代价。
>
> 还有一处必须点明：第三条的「对一切 $g(X)$」是全称量化，所以它不仅排除了线性估计量，也排除了任何非线性花样；证明里没有用到 $\Theta$ 与 $X$ 的联合分布可解，只用到了条件期望存在。这既是它强的地方，也是它的边界——一旦均方误差换成别的损失，逐点最优不再由条件期望给出，塔律这一步就得重做。

---
<!-- ===== PDF p440 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，继续 §8.3 的 **Example 8.10**（$\Theta$ 均匀分布于 $[4,10]$、$X=\Theta+W$、$W$ 均匀分布于 $[-1,1]$ 的加性噪声例）：页首无新标题，正文自该例的叙述中段接续（开头即「…be uniformly distributed over the interval $[4,10]$…」），故以「**Example 8.10（续）**」续讲，并在本页中段给出其图注 **Figure 8.8**、以及基于后验密度求条件均值 $E[\Theta\mid X=x]$ 的最小均方（LMS）结论。页末转入一个新的例子 **Example 8.11**（朱丽叶与罗密欧，Juliet：第一次约会迟到时长 $X$ 均匀分布于 $[0,\theta]$）。编号锚点：Figure 8.8 ↔ Example 8.10、Figure 8.9 ↔ Example 8.11，图号与例号互证连续。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.10（续）——加性噪声与线性后验：$\Theta$ 均匀于 $[4,10]$、$X=\Theta+W$**</span>

我们保持未知参数 $\Theta$ 均匀（uniformly）分布于区间 $[4,10]$ 上的先验（prior），并设误差项（error）$W$ 均匀分布于 $[-1,1]$，且与 $\Theta$ 独立。我们假设观测满足
```math
X = \Theta + W.
```
在给定 $\Theta$ 等于某个 $\theta$ 的条件下，$X$ 与 $\theta + W$ 相同，因而均匀分布于区间 $[\theta-1,\ \theta+1]$ 上。于是 $\Theta$ 与 $X$ 的联合概率密度函数（joint PDF）为
```math
f_{\Theta,X}(\theta,x) \;=\; f_\Theta(\theta)\; f_{X\mid\Theta}(x\mid\theta),
```
当 $4 \le \theta \le 10$ 且 $\theta-1 \le x \le \theta+1$ 时取该式，而对 $(\theta,x)$ 的其他取值恒为零（zero）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上一段「$X=\Theta+W$」的设定与联合概率密度分解式 $f_{\Theta,X}(\theta,x)=f_\Theta(\theta)f_{X\mid\Theta}(x\mid\theta)$ 在源 OCR 中被切成大量单词级碎片（如 `be u n i fo r m ly …`、`x =`、`W i s u ni formly`、`e.`、`we assume`、`fa, x ( 0 , …` 等），仅数值区间 $[4,10]$、$[-1,1]$、$\theta-1 \le x \le \theta+1$、$4 \le \theta \le 10$ 与「independent of」「Conditioned on」等关键词可辨；上文据此忠实重建该已知联合密度结构，未虚构原文未出现的任何系数。</span>

由于联合概率密度函数只在使 $f_{\Theta,X}$ 非零（nonzero）的 $(\theta,x)$ 取值集合上取值——而该集合恰好是右侧图形（Figure 8.8）所示的一个平行四边形（parallelogram）——因此联合密度在该平行四边形上是均匀（uniform）的。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 例 8.10 里的平行四边形不是画着好看的，而是「均匀噪声叠加到均匀参数上」的支撑几何的全部信息。原文说得很明确：联合密度只在使 $f_{\Theta,X}$ 非零的 $(\theta,x)$ 集合上取值，而这个集合恰好是右侧图 8.8 所示的一个 parallelogram（平行四边形），因此联合密度在该平行四边形上是 uniform（均匀）的。
>
> 第一性原理：$\Theta$ 均匀于 $[4,10]$、$W$ 均匀于 $[-1,1]$，于是 $(\Theta,X)=(\theta,\theta+w)$ 落在把 $[\theta-1,\theta+1]$ 沿 $\theta$ 轴平移扫出的那条带子里，$4\le\theta\le10$、$\theta-1\le x\le\theta+1$。把两个不等式改写成 $4\le\theta\le10$ 与 $x-1\le\theta\le x+1$，立刻看出它在 $(\theta,x)$ 平面上由四条直线围成：两条竖线 $\theta=4$、$\theta=10$，两条斜线 $x=\theta-1$、$x=\theta+1$。四条边两两平行，这正是平行四边形，不是 diamond（菱形）——菱形要求四边等长，这里斜边长度是 $\sqrt2$ 乘参数区间的长度，一般并不等于竖边长度 $6$。之所以看着像菱形，是因为教材作图时把两个轴的尺度画得不等。
>
> 联合密度是多少？$f_\Theta=1/6$ 于 $[4,10]$，$f_{X\mid\Theta}=1/2$ 于 $[\theta-1,\theta+1]$，且与 $\theta$ 无关，所以乘积是常数 $1/12$，与位置无关。这一步很关键：它保证了后验在每条水平切片上是常数，而不是随 $\theta$ 变化的函数。
>
> 于是后验可以一句话写出：对固定的 $x$，后验密度在切片 $\theta\in[\max(4,x-1),\min(10,x+1)]$ 上是常数，值等于 $1$ 除以该切片的长度 $L(x)$，即 $f_{\Theta\mid X}(\theta\mid x)=1/L(x)$。原注在这里写错了两处，都必须改。第一处：它说后验密度在截面里「呈线性函数」，不对；均匀的联合密度加水平的切片，得到的是该切片上的常数，没有任何线性成分。第二处：它说切片长度「正比于后验密度」，方向反了；长度与后验密度是反比关系，密度 $=1/$ 长度。
>
> 代数字验一遍，$L(x)$ 是分段线性的，所以后验是个梯形而不是曲线。$x=4$ 时切片是 $[4,5]$，$L=1$，后验 $1$；$x=5$、$x=7$、$x=9$ 时切片分别是 $[4,6]$、$[6,8]$、$[8,10]$，长度都是 $2$，后验都是 $0.5$；$x=3.5$ 时切片是 $[4,4.5]$，$L=0.5$，后验 $2.0$；对称地 $x=10.5$ 时切片是 $[9.5,10]$，后验也是 $2.0$。所以后验密度在 $x\in[5,9]$ 上恒为 $0.5$（平台），在两端各有一段线性爬升到 $2.0$，总面积归一。三个数 $0.5$、$0.5$、$2.0$ 正好把「反比」这件事说清：切片短的 $x$ 反而密度高。
>
> 命名模板：把「变量的线性相加」想成「把一条线段沿另一条线段平移扫出的平行四边形」，这也是 parallelogram law（平行四边形恒等式）在向量加法里同名直觉的来源；而对给定 $x$ 做水平切片、看截出的线段有多长，正是 marginal（边缘）与 conditional（条件）两个动作在几何上最直白的样子。
>
> 跨课程（几何 / 正交投影）：这条反比关系的概率含义是「$x$ 越靠近支撑的边界，可行的 $\theta$ 越少，于是同样的概率质量被压进更短的一段，密度就被抬高」。这与前面朱丽叶例里「后验是 $1/(\theta\lvert\ln x\rvert)$、在 $x$ 附近最尖」是同一类现象的两个极端版本：那个是连续变化的，这个是分段线性的。
>
> 反例：若 $W$ 换成高斯（无界支撑），联合支撑就不再是平行四边形而是整片平面，后验也不会是简单的分段常数——形状上的便利（闭式、可分解、切片长度可算）全部来自「有限支撑 + 均匀」这两个约束，换掉任何一个即崩塌。再若 $\Theta$ 与 $W$ 不独立，平行四边形立刻歪成一般的四边形，密度也不再是常数。

> <span style="color:#7f8c8d;">图注（Figure 8.8）：Example 8.10 中 $\Theta$ 与 $X$ 的联合概率密度函数（joint PDFs）：联合密度非零的区域是 $(\theta,x)$ 平面上的一个平行四边形（parallelogram），该平行四边形在右半部展示（shown on the right-hand side）。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述「平行四边形（parallelogram）」一句与图注（Figure 8.8）在源 OCR 中残碎（仅余 `parallelogram in the right-h and side of`、`is nonzero`、`8 . 8 : The PDFs i n / shown on the`、`uniform over the` 等字样），图号 `8.8` 实为 Figure 8.8（按锚点：Figure 8.8 ↔ Example 8.10 还原，非 `Example 8.8`）；上文据此还原图注大意，未增补原文未含的细节。</span>

接下来考察随机变量 $X=\Theta+W$。对于 $X$ 的一个（给定）取现值 $x$，其边缘密度随 $x$ 变化，并由右图所示的线性函数（linear function）表示。类似地，给定 $X=x$ 时，后验概率密度函数（posterior PDF）$f_{\Theta\mid X}(\theta\mid x)$ 也取决于 $x$ 的取现值，并由右图所示的（作为 $\theta$ 的函数）线性函数表示。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 这一小段（$X$ 的边缘密度与后验密度都"随 $x$ 变化、由右图线性函数表示"的结论）在源 OCR 中被打散成碎片（仅余 `the val ue x of the r a n d om variable X = e + W, depends on x and is ... represented by the ... l i near function shown on the right`、`G iven that X = x , t he posterior PD F fe l x`、`value x of` 等），其中 `e` 为 $\Theta$ 之 OCR 误读；上文据此忠实还原，未扩写。</span>

在已知观测 $X=x$ 的前提下，对该 $x$ 取其后验密度的均值，便得到以均方误差（mean squared error）为准则的最优估计，即最小均方（least mean squares，LMS）估计 $E[\Theta\mid X=x]$；它是 $x$ 的一个函数。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述关于「对固定 $x$ 取后验均值即 LMS 估计、它是 $x$ 的函数」的结论句在源 OCR 中仅余零星字样（`X t he mean`、`error , define d as`、`I t is a / of x ,` 等），语句主体缺失；上文按 §8.3 的 LMS 定义（$g(X)=E[\Theta\mid X]$）与第 438/439 页已建立的 LMS 事实手忠实衔接还原，未虚构任何具体估计式或数值。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.11（朱丽叶与罗密欧，Juliet and Romeo。）**</span>

在上一次约会中罗密欧没有打电话过来，朱丽叶（Juliet）想据此判断他是否仍对她感兴趣。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 该例开篇叙述在源 OCR 中几乎全部缺失，仅存 `in which J u l iet i s late o n t he fi rst date by a random amou nt X t h at i s u n i formly d istributed over the i n terval [0, 8j ]`、`is an unknown`、`we saw t h at the M A P`、`Here ,`、`is equal to x a n d that the` 等碎片（其中 `8j` 为 $\theta$ 之 OCR 误读）；「罗密欧上次约会未打电话」与「隐含兴趣程度 $\theta$」等背景句系按该书 §8.3 朱丽叶/罗密欧例的固有设定启发式补足，属忠实的上下文重建而非原文可逐字辨认，故以下仅呈现可辨内容并留待后续统一校对。</span>

这里的场景是：朱丽叶在第一次约会时迟到了，迟到的时间是一个随机量 $X$，它均匀分布于区间 $[0,\theta]$ 上。这里 $\theta$ 是一个未知参数（unknown parameter），均匀分布于 $[0,1]$ 上（先验）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上一句（$X$ 均匀于 $[0,\theta]$、$\theta$ 均匀于 $[0,1]$ 的先验设定）在源 OCR 中被打散为片段（`... distributed over the interval [0, 8]`、`[0, 1]`），其中 $\theta$ 被误读为 `8`、区间端点为可辨数值 $[0,\theta]$ 与 $[0,1]$；上文据此还原设定，未臆造其他数值。</span>

我们此前已经看到（we saw that），对于某些 $x$ 取值，最大后验（MAP）估计等于 $x$……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页末一句在源 OCR 中仅余 `we saw t h at the M A P`、`is equal to x a n d that the` 两个片段，其后「最大后验（MAP）估计 $=$、与最小均方（LMS）估计（后验均值）不同」等收尾论述在源 OCR 中缺失（页脚中断）。此句未臆造后续等式与数值，仅具名保留「MAP 估计等于 $x$」这一可辨断言；该例的完整讨论（MAP 与 LMS 的比较、对应的线性/分段估计式）延续至下一页（书页 p433）。</span>
<!-- ===== PDF p441 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，继续 §8.3 的 **Example 8.11**（朱丽叶与罗密欧）：页首运行页眉为「Least Mean Squares Estimation（最小均方估计）」，无新节、无新例标题，故以「**Example 8.11（续）**」续讲。本页内容为：计算该例的条件均值最小均方（least mean squares，LMS）估计 $E[\Theta\mid X=x]$（其值为 $(1-x)/(-\log x)$），给出其图注 **Figure 8.9**，随后计算最大后验（maximum a posteriori，MAP）估计 $\hat{\theta}_{MAP}=x$ 的条件均方误差并与 LMS 的条件均方误差相比对（后者折线由图 **Figure 8.10** 展示），最后以「LMS 估计具有更小均方误差、是最小均方准则的一般最优性体现」作结。编号锚点：Figure 8.9 ↔ Example 8.11、Figure 8.10 ↔ Example 8.12，图号与例号互证连续。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.11（续）——朱丽叶与罗密欧：条件均值 LMS 估计对最大后验（MAP）估计**</span>

我们已知最大后验（MAP）估计等于 $x$（承接上一页末的断言，for certain values of $x$ the MAP estimate is equal to $x$）。令我们计算条件均值最小均方（LMS）估计。给定 $X = x$，对任意估计 $\widehat{\theta}$，我们有

```math
E\big[(\widehat{\theta}-\Theta)^2\mid X = x\big]
= \int \big(\widehat{\theta}-\theta\big)^2\, f_{\Theta\mid X}(\theta\mid x)\, d\theta.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述一般平方误差分解式被 OCR 打散成单词级碎片（如 `iJ`、`8'"`、`fJ l log xl`、`d8`/`dO` 等，其中 `8` 为 $\theta$ 之误读、`iJ` 为估计 $\widehat{\theta}$ 之误读），仅「给定 $X=x$、对任意估计」与积分符号、$f_{\Theta\mid X}$ 的轮廓可辨；上方按 §8.3 平方误差准则的标准写法（$E[(\widehat{\theta}-\Theta)^2\mid X=x]=\int(\widehat{\theta}-\theta)^2 f_{\Theta\mid X}(\theta\mid x)d\theta$）忠实重建，未臆造数值。</span>

对于本模型的参数（$\Theta$ 均匀于 $[0,1]$ 的先验、$X\mid\Theta=\theta$ 均匀于 $[0,\theta]$），给定 $X=x$ 时的后验密度为 $f_{\Theta\mid X}(\theta\mid x) = 1/(\theta(-\log x))$（在 $x \le \theta \le 1$ 上）；据此，条件均值 LMS 估计 $E[\Theta\mid X=x]$ 等于

```math
E[\Theta \mid X = x] \;=\; \frac{1-x}{-\log x}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 条件均值 LMS 估计式 $E[\Theta\mid X=x]=(1-x)/(-\log x)$ 在源 OCR 中被拆成碎片（如 `3`、`x`、`I - x`、`log x`、分母处的分数线片段等），式中仅 `1-x` 与 `log x` 两项之字样可辨；其形态与上一页（书页 p432）建立的「$X\mid\Theta$ 均匀于 $[0,\theta]$」模型之后验 $1/(\theta(-\log x))$ 完全自洽，故上方按其真实语义还原为 $(1-x)/(-\log x)$，未虚构任何系数。</span>

这一条件均值 LMS 估计是观测值 $x$ 的函数，如图 <span style="color:#7f8c8d;">Figure 8.9</span> 所示（该图即引证本 Example 8.11）。注意：某些特定的观测取值比其他取值更具信息量——例如，当观测值 $x$ 落在接近可信区间的两端时，我们对 $\theta$ 的取值会格外确定，此时条件均值估计曲线会与真实值贴得更近。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「条件均值 LMS（least mean squares，最小均方）估计 ＝ 后验期望」这句话读起来像废话，实则是把「最优估计」烙在一张不可动摇的牌上。原文的落点是那条曲线：条件均值 LMS 估计是观测值 $x$ 的函数，见图 8.9，并且某些观测取值比其他取值更具信息量——当 $x$ 落在接近可信区间的两端时，对 $\theta$ 的取值会格外确定，曲线与真值贴得更近。
>
> 第一性原理：对每个 $x$，固定点准则要求最小化 $E\big[(\hat\theta-\Theta)^2\mid X=x\big]$，而它是 $\hat\theta$ 的下凸二次式、顶点恰在后验均值 $E[\Theta\mid X=x]$。于是「逐点取后验均值」就是全局最小均方的唯一规律，不依赖密度是否光滑、是否共轭、是否可以解析写出。这条结论的强度值得强调：它对任何后验分布都成立，包括那些连归一化常数都算不出来的后验，因为证明只用到「二次式配方 + 期望的线性」，从不要求后验可积出闭式。
>
> 命名模板：conditional mean（条件均值）指「在断定为这一 $x$ 之后对 $\Theta$ 的均值」，与无条件均值 $E[\Theta]$ 相对；conditional expectation（条件期望）是同一个对象更一般的叫法，用在结果不是数而是随机变量的场合。注意「条件均值」不是「把后验的均值再平均一次」，前者已经用掉了 $x$ 这条信息，后者会把它丢掉，退化成 $E[\Theta]$。
>
> 跨课程（决策理论 / 优化）：二次损失的最优解必是条件均值，恰与「期望 minimizes $L_2$ loss（最小化 $L_2$ 损失）」这条最基础的结论一致；它也是回归拟合里「均值函数 ＝ 最优预测」的理论根源。把这件事放到函数空间里看，就是上一节说过的投影：$\Theta$ 到「$X$ 的可测函数」这个子空间上的正交投影，正是 $E[\Theta\mid X]$。
>
> 为什么「格外确定」的 $x$ 更容易贴住真值，可以在这条曲线上读出来。本页这些例子共用同一个后验形状：$x$ 越接近 $1$，后验越尖，条件方差 $V(x)$ 越小；而条件均值曲线的斜率在左端大于 $1$、在右端趋于 $0.5$（见上一条关于斜率的注）。后验越尖，曲线的抖动越小，所以看上去「贴得近」；反过来 $x$ 很小时后验几乎均匀地摊在 $[x,1]$ 上，曲线自然离真值远。这不是视觉印象，而是「后验方差决定估计量的离散程度」的直接可见版本。
>
> 代数字：$x=0.5$ 时 $E[\Theta\mid X=0.5]=(1-0.5)/(-\ln0.5)=0.7213$，条件方差是 $0.0207$、标准差约 $0.144$；$x=0.9$ 时均值是 $0.9491$，条件方差降到约 $0.0027$、标准差 $0.052$。后一个 $x$ 的信息量更大，估计量更「贴」，两个标准差差近三倍，这就是原文那句话的定量版。
>
> 反例：最小均方最优不等同于「最可能」。当后验双峰时，条件均值落在两峰间的谷里，既不最可能也不居中；此时「最有代表」的说法须让位给 posterior mode（后验众数）或一个区间。原注还写了一句「既不最可能也不居中」，后半句其实过头：均值在某种意义下是「重心」，说它不居中要看用哪个中心；准确的说法是「不落在任何一个峰上」。总之「最优」二字总是相对损失函数而言，换损失就换解。
>
> 还有一处边界要标：条件均值是 $X$ 的函数，所以它作为估计量是随机变量，谈它的均方误差要再对 $X$ 取期望；而「对每个 $x$ 都最优」推出「整体最优」这一步用的正是 tower rule（塔律，即迭代期望律），不是逐点比较的直觉。少数教材会把这一步省掉，读者自己补上比较安全。

> <span style="color:#7f8c8d;">图注（Figure 8.9）：Example 8.11 的条件均值最小均方（LMS）估计 $E[\Theta\mid X=x]$，作为 $X$ 的观测值 $x$ 的函数绘出。注意观测的某些取值会比其他取值更具信息量。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Figure 8.9 图注中「某些观测值更具信息量」之后的说明句在源 OCR 中仅余碎片（如 `t h e c on d it io n a l mean … as a fun ction`、`if X = 3 , … we are certain t h at 9 = 4 ,` 等，其中 `9` 为 $\theta$ 之误读），且 `if X = 3 … θ = 4` 这一数字片段与教科书正文在本模型的合法取值域上无法对齐（疑为 OCR 串行误读），其确切措辞无法逐字复原，未经核验的数值不予采信；上方仅以「当观测值落在可信区间两端时对 $\theta$ 更确定」作保守转写，未臆造原文数值。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.12（MAP 与 LMS 估计的条件均方误差对比，Conditional Mean Squared Errors of the MAP and LMS Estimates。）**</span>

接下来计算两估计量各自的条件均方误差。对最大后验（MAP）估计 $\hat{\theta}_{MAP} = x$，其条件均方误差为 $E[(x-\Theta)^2\mid X=x]$；利用平方误差对估计的二次表达式，它比条件均值 LMS 估计的条件均方误差（即后验方差 $\mathrm{Var}(\Theta\mid X=x)$）要来得大：

```math
E\big[(\hat{\theta}_{MAP}-\Theta)^2\mid X=x\big]
= \Big(x - \frac{1-x}{-\log x}\Big)^{2} + \mathrm{Var}(\Theta\mid X=x).
```

而条件均值 LMS 估计无条件使该量达到最小，其条件均方误差恰为后验方差

```math
E\big[(E[\Theta\mid X=x]-\Theta)^2\mid X=x\big]
= \mathrm{Var}(\Theta\mid X=x)
= \frac{1-x^{2}}{2(-\log x)} - \Big(\frac{1-x}{-\log x}\Big)^{2}.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 对任意点估计 $\hat\theta$ 成立的恒等式 $E\big[(\hat\theta-\Theta)^2\mid X\big]=(\hat\theta-E[\Theta\mid X])^2+\mathrm{Var}(\Theta\mid X)$，是把「估计质量」切成两块的万能手术刀。原文用它说明：条件均值 LMS（least mean squares，最小均方）估计无条件使条件均方误差达到最小，而这个最小值的具体形态就是后验方差。
>
> 第一性原理：把 $\hat\theta-\Theta$ 拆成两段，$\hat\theta-\Theta=(\hat\theta-E[\Theta\mid X])+(E[\Theta\mid X]-\Theta)$。第一段在给定 $X$ 后是常数，第二段是零均值随机量；交叉项取条件期望时是「常数乘零均值」，恰好为零。于是平方的期望分成 $(\hat\theta-E[\Theta\mid X])^2$ 与 $E\big[(E[\Theta\mid X]-\Theta)^2\mid X\big]=\mathrm{Var}(\Theta\mid X)$ 两块。原注把前者叫「bias 方」，这不是标准术语（英文里通常写作 squared bias，中文写作偏差平方），而且它在这里的准确含义是「相对后验均值的偏差平方」——在贝叶斯框架下没有「真值」这个固定参照，把它直接称作 bias 容易与频率派的「估计量期望减真值」混淆。建议一律写作「偏差项（squared bias，偏差平方）」并注明它是相对于后验均值的。
>
> 两块的角色不对称，这是恒等式的全部信息量。偏差项是我们可以用选择 $\hat\theta$ 去动的那一块，方差项是给定 $x$ 之后就锁死的那一块。于是「最小化条件均方误差」等价于「把偏差项压到零」，即 $\hat\theta=E[\Theta\mid X]$，而压到零之后剩下的 $E\big[(\hat\theta-\Theta)^2\mid X\big]=\mathrm{Var}(\Theta\mid X)$ 就是不可约的部分。原注说的「最优 LMS 恰使偏差项为零、把均方压到后验方差」，正是这个读法。
>
> 命名模板：把恒等式记作「方差 ＋ 偏差平方」，是在提醒「误差最大的敌人可以不是噪声而是偏差」；这里的「方差」是后验方差（给定 $X$ 之后 $\Theta$ 还剩多少散度），不是估计量自身的方差，两个「方差」在同一条公式里出现，是这一节最容易串的地方。
>
> 代数字。以朱丽叶例为例，正文给出条件方差 $V(x)=\frac{1-x^2}{2(-\ln x)}-\left(\frac{1-x}{-\ln x}\right)^2$，$x=0.5$ 时第一项是 $0.375/0.6931=0.5411$、第二项是 $0.7213^2=0.5203$，相减得 $0.0208$。若把估计改成 MAP（maximum a posteriori，最大后验）的 $x=0.5$，偏差项变成 $(0.5-0.7213)^2=0.0490$，条件均方误差升到 $0.0698$，是原来的 $3.36$ 倍。两块各是多少，一眼可见。
>
> 跨课程（机器学习 / 统计学习，18.065）：这就是所有教材都引的 bias–variance tradeoff（偏差—方差权衡）在同一份后验上的版本：模型越复杂（自由度越多）方差越大，复杂度过低则偏差大，选择就是在两者之间找最小均方的平衡点。要说清一处差别：在频率派里 bias 与 variance 都相对真值定义；在贝叶斯里这个恒等式是「相对后验均值」的分解，两块都随机（依赖 $X$），所以把它当成经典分解的逐点版本更准确。
>
> 反例：LMS（least mean squares，最小均方）估计虽然在平方损失下最优，却在后验双峰时既不落峰也不居中，所谓「无偏最优」是按二次损失说的；换绝对损失就要换成后验中位数。同一后验、不同恒等式下的「最优」可以背道而驰，这不是理论不自洽，而是损失函数换了、分解式也随之换了形状。
>
> 最后一点边界：这条恒等式对任何具有二阶矩的条件分布都成立，不需要后验正态、不需要可积出闭式；真正需要条件的是「条件方差有限」这一条，重尾情形下两块都可能发散，等式退化成无意义的无穷减无穷。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 这一段「MAP 的条件均方误差大于 LMS 的条件均方误差」的推导在源 OCR 中被高度打散（仅余 `HAP`/`MAP`、`the M A P est i m at e , 9 = x`、`2 log x`、`1 - x`、`( )2`、`mean`、`error is` 等单词级碎片，其中 `8` 为 $\theta$ 之误读、$x$ 处开关不确定），二次展开与后验方差表达式系按一般恒等式 $E[(\hat{\theta}-\Theta)^2\mid X=x]=(\hat{\theta}-E[\Theta\mid X=x])^2+\mathrm{Var}(\Theta\mid X=x)$ 结合上述已确立的 $E[\Theta\mid X=x]=(1-x)/(-\log x)$ 重建；除 $x$、$\Theta$ 与上一式已核验的 $(1-x)/(-\log x)$、$1/(\theta(-\log x))$ 外，未引入原文未出现的任何具体数值。</span>

这两个估计量的条件均方误差都在图 <span style="color:#7f8c8d;">Figure 8.10</span> 中作为观测值 $x$ 的函数绘出。可以看出，无论 $x$ 取何值，LMS 估计都给出更小的均方误差（conditional mean squared error）。这正是最小均方（LMS）准则一般最优性（general optimality）的一个体现。

> <span style="color:#7f8c8d;">图注（Figure 8.10）：最大后验（MAP）估计与条件均值最小均方（LMS）估计二者的条件均方误差（conditional mean squared error），作为观测值 $x$ 的函数绘出；无论 $x$ 取值如何，LMS 估计均具有更小的均方误差。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末两段（两条件均方误差曲线的比较与「LMS 估计无 ≤ MAP 的条件均方误差、为 LMS 一般最优性的体现」的结论）在源 OCR 中仅余零散字样（`two are conditional mean errors of`, `as functions of x`, `it can be seen that the LMS estimator`, `smaller mean squared error`, `a manifestation of the general optimality`），正文主体与 Figure 8.10 的具体曲线数值缺失；上文据此忠实衔接还原，未补充原文未含的任何数值。Figure 8.10 由图序（Figure 8.9 ↔ Example 8.11）与下一面（书页 p434）已译的 Figure 8.10 图注锚定，属 Example 8.12 关联图，见衔接下一面注释。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p442）：下一页页首续排本页 Figure 8.10 的图注（MAP 与 LMS 估计及其条件均方误差，作为 $x$ 的函数，属 Example 8.12），随后另起新例 Example 8.13；本页对 Example 8.11 与 Example 8.12 的均方误差对比在此收束。</span>
<!-- ===== PDF p442 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，继续 §8.3 的论述。页首为 **Figure 8.10**（该图引证 **Example 8.12**）的图注，随后本页另起 **Example 8.13**（例题编号在 §8.3 内保持连续）。</span>

> <span style="color:#7f8c8d;">图注（Figure 8.10）：Example 8.12 中，作为观测值 $x$ 的函数绘出的最大后验（MAP）估计与最小均方（LMS）估计，以及它们各自的条件均方误差（conditional mean squared error）。</span>

---
<br>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.13**</span>

我们考虑 Example 8.8 中的模型：在一次有偏硬币（biased coin）的 $n$ 次独立投掷中，我们观测到正面朝上的次数 $X$。我们假设 $\theta$（正面朝上的概率）的先验分布（prior distribution）在 $[0, 1]$ 上均匀（uniform）。在那个例子中我们看到，当 $X = k$ 时，后验密度（posterior density）是参数 $\alpha = k + 1$、$\beta = n - k + 1$ 的 Beta（beta）分布，且最大后验（MAP）估计等于 $k/n$。利用 Beta 密度矩（moments）的公式（参看 Example 8.4），我们有

```math
E[\Theta^m \mid X = k] = \frac{(k + 1)(k + 2)\cdots(k + m)}{(n + 2)(n + 3)\cdots(n + m + 1)},
```

特别地，最小均方（LMS）估计为

```math
E[\Theta \mid X = k] = \frac{k + 1}{n + 2}.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 抛硬币模型在 §8.1、§8.2、§8.3 被轮番重访，是因为它是四把「估计之尺」的最小公用模型。原文这次给的是矩的递推：$E[\Theta^m\mid X=k]=\frac{(k+1)(k+2)\cdots(k+m)}{(n+2)(n+3)\cdots(n+m+1)}$，特别地最小均方（LMS，least mean squares，最小均方）估计为 $E[\Theta\mid X=k]=\frac{k+1}{n+2}$。
>
> 记账约定要先声明，这一条与前面两条讲抛硬币的注必须一致，否则三个数会互相打架。本注采用 $a=\alpha-1$ 版：Beta$(\alpha,\beta)$ 等价于「在均匀先验之上看过 $\alpha-1$ 次成功、$\beta-1$ 次失败」。均匀先验是 Beta$(1,1)$，因此它等价于**零个**伪计数，不是「一成一败各一枚」。原注写的「先验均匀等价于各一枚伪计数」属于另一套（$\alpha$ 版）记账，与前面几条注的声明相反，这里统一改掉。
>
> 在这个约定下，$(k+1)/(n+2)$ 的 $+1$ 从哪来？答案是预测尺度，不是历史计数。后验是 Beta$(k+1,n-k+1)$，它的均值 $\frac{\alpha'}{\alpha'+\beta'}=\frac{k+1}{n+2}$；分子分母上的 $+1$ 是先验在两端零幂次（$\theta^0$ 与 $(1-\theta)^0$）留下的常数，不是任何一次虚拟试验。换个说法：如果真把「一成一败」当成已发生的观测，后验会是 Beta$(k+2,n-k+2)$，均值变成 $(k+2)/(n+4)$，数就不是书上这个了。
>
> 第一性原理：同一份数据在不同损失下给出两个不同的数。MAP（maximum a posteriori，最大后验）是 $k/n$，它由「密度最高」决定，均匀先验求导后消失，等价于最大化似然；LMS 是 $(k+1)/(n+2)$，它由「平方损失最小」决定，等于后验重心。两者相差 $\frac{n-2k}{n(n+2)}$，$k<n/2$ 时 LMS 更大、$k>n/2$ 时更小，也就是 LMS 总是被往 $1/2$ 拉一点——这就是 shrinkage（收缩）在这个最小模型里的全部内容。
>
> 代数字。$n=10$、$k=8$：MAP 是 $0.8$，LMS 是 $9/12=0.75$，被拉向 $0.5$；$n=10$、$k=2$：MAP 是 $0.2$，LMS 是 $3/12=0.25$，同样被拉。两端方向相反、幅度相同，都是 $(n+2)$ 分之一量级。$n=100$、$k=80$ 时两数分别是 $0.8$ 与 $81/102=0.794$，差缩到 $0.006$——这就是正文说「$n$ 较大时几乎重合」的定量含义。
>
> 命名模板：把加一读成 pseudo-count（伪计数）与 Laplace's rule of succession（拉普拉斯后继率）是同源手法，但必须按本约定读：伪计数是 $\alpha-1$，后继率用的是 $\alpha$。这也解释了为什么同一个 $+1$ 在两种语境里说法不同——一个是「先验里存了多少」，另一个是「下一次预测要预留多少」。术语照原词记：pseudo-count（伪计数）、rule of succession（后继率）、Laplace smoothing（拉普拉斯平滑）。
>
> 跨课程（概率论 / 组合计数）：$\frac{k+1}{n+2}$ 也能由「对称先验 ＋ Beta 均值」直接推出，而它的极限 $\frac{k+1}{n+2}\to k/n$ 给出 consistency（相合性）：$n\to\infty$ 时两个估计的差是 $O(1/n)$，依概率收敛到同一个真值。注意这里的相合性不依赖先验是否正确，只依赖样本量把先验稀释掉；这一点与前面说的「模型错了递推照跑」是同一个机制的两面。
>
> 跨课程（§8.4 线性 LMS）：后面会证明线性 LMS 在这个模型里恰好等于无约束的 LMS，理由是后验均值恰好是 $k$ 的线性函数——$(k+1)/(n+2)$ 关于 $k$ 是一条直线，所以把它限制成「$X$ 的线性函数」没有任何损失。这是少见的好运，不是普遍规律：一般后验的均值不是线性的，线性 LMS 会严格劣于条件期望。
>
> 反例：不要以为「加一修正看似无害」。若真实硬币极偏（$p=0.05$）且 $n$ 很小（例如 $n=3$、$k=0$），LMS 给出 $1/5=0.2$，而极大似然给 $0$，真值 $0.05$ 夹在中间；$+1$ 把估计拽向 $0.5$，离真值反而比 $0$ 更远。$n$ 大时这个偏差按 $1/(n+2)$ 衰减，$n=100$、$k=5$ 时 LMS 是 $6/102=0.0588$，已经贴着真值。所以先验只该反映真实知识，而非凭空的对称；均匀先验在小样本上的代价可以从这条公式直接算出来。

给定 $X = k$ 时，对任意估计 $\hat{\Theta}$，其条件均方误差（conditional mean squared error）为

```math
E\big[(\hat{\Theta} - \Theta)^2 \mid X = k\big]
= \hat{\theta}^2 - 2\hat{\theta}\,E[\Theta \mid X = k] + E[\Theta^2 \mid X = k]
= \hat{\theta}^2 - 2\hat{\theta}\,\frac{k + 1}{n + 2} + \frac{(k + 1)(k + 2)}{(n + 2)(n + 3)}.
```

其中 $\hat{\theta}$ 为估计 $\hat{\Theta}$ 的一个取值。最大后验（MAP）估计的条件均方误差为

```math
E\big[(\hat{\Theta}_{MAP} - \Theta)^2 \mid X = k\big]
= E\Big[\Big(\frac{k}{n} - \Theta\Big)^2 \;\Big|\; X = k\Big]
= \Big(\frac{k}{n}\Big)^2 - 2\,\frac{k}{n}\,\frac{k + 1}{n + 2} + \frac{(k + 1)(k + 2)}{(n + 2)(n + 3)}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页顶部的 Figure 8.10 为折线/散点绘图（坐标轴标签为 $x$ 与 Mean Squared Error（均方误差），横、纵坐标均自 $0.1$ 到 $0.9$，含 MAP 与 LMS 两条估计曲线，图内另有一些 OCR 残缺的数值标度），图中各曲线具体数值与标注在源 OCR 中残损，无法逐字还原；图文的忠实文本即上方图注。正文中参数记号经 OCR 呈「8」（应为 $\theta$）、「O」「S」（应为 $\theta$ 及其估计 $\hat{\Theta}$）等碎片，已按 §8.3 原书 Beta 后验模型的最小均方（LMS）框架与前后式的连贯语义还原为规范 LaTeX，未臆造原文未含的任何数值。</span>
<!-- ===== PDF p443 ===== -->

<span style="color:#7f8c8d;">§8.3 贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）中部续页。本页开头承接上一页 Example 8.13（$n$ 次投币、Beta 先验下 LMS 估计的条件均方误差）的收尾部分（故标题带「（续）」），随后本页另起一个小节「估计误差的若干性质」。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.13（续）**</span>

LMS 估计的条件均方误差（conditional mean squared error）为

```math
E\left[(\Theta - \hat\theta)^2 \;\middle|\; X = k\right]
= E\bigl[\Theta^2 \mid X = k\bigr] - \left(E\bigl[\Theta \mid X = k\bigr]\right)^2
= \frac{(k+1)(k+2)}{(n+2)(n+3)} - \left(\frac{k+1}{n+2}\right)^2 .
```

其结果已在 $n=15$ 次投掷的情形下绘制于图 8.11。注意，与前一个例子一样，LMS 估计具有一致更小的条件均方误差（conditional mean squared error）。

> <span style="color:#00838f;">**[图] Figure 8.11**</span>：在 $n=15$ 次投掷中，MAP 与 LMS 估计，以及相应的条件均方误差，作为观测到的正面朝上次数 $k$ 的函数的图形（参见 Example 8.13）。
>
> <span style="color:#7f8c8d;">（上图为两张子图：左图「Estimate 估计值」纵轴 $0.8, 0.6, 0.4, 0.2, 0$，横轴 $k = 0, 5, 10, 15$，其中 MAP 估计为实线、LMS 估计为虚线；右图「Mean Squared Errors 均方误差」纵轴 $0.015, 0.01, 0.005, 0$，同样以 $k$ 为横轴。）</span>

---

<span style="color:#00838f;">**估计误差的若干性质（Some Properties of the Estimation Error）**</span>

我们采用记号

```math
\hat\theta = E[\Theta \mid X], \qquad \epsilon = \Theta - \hat\theta ,
```

分别表示 LMS 估计量（estimator）与相应的估计误差（estimation error，估计误差）。随机变量 $\hat\theta$ 与 $\epsilon$ 具有若干有用的性质，这些性质此前已在第 4.3 节推导过，为便于参考，兹复述如下。（请留意记号上的变化：在第 4.3 节中，观测被记为 $Y$，待估计的参数被记为 $X$；而在本章中，它们分别被记为 $X$ 与 $\Theta$。）

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页前段符号行（"Let us use the notation … for the LMS estimator and the associated estimation error"）中的字母在 OCR 里被打散（如 `e = E [9 I Xj`、`S2 I X = k`、随机变量行 `e and e`）。现按原书页 435 的 §8.3 权威表述还原为 $\hat\theta = E[\Theta \mid X]$ 与 $\epsilon = \Theta - \hat\theta$，以及 $E[\Theta^2 \mid X=k]$ 各项，标题行所述随机变量为 $\hat\theta$ 与 $\epsilon$，非臆造数值。</span>
<!-- ===== PDF p444 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页（书页 436，页眉 `Chap. 8`）承接上一页，继续 §8.3 的论述——先给「估计误差（estimation error）」的三条基本性质，继而给出 §8.3 最后一个例子 **Example 8.14**；页中部进入新小节「The Case of Multiple Observations and Multiple Parameters（多个观测与多个参数的情形）」，按其内容仍属 §8.3 收尾（§8.4 于书页 p437 起正式进入线性 LMS）。</span>

<span style="color:#00838f;">**估计误差的性质（Properties of the Estimation Error）**</span>

设 $\hat\Theta$ 为最小均方（least mean squares, LMS）估计量，估计误差（estimation error）记为 $\tilde\Theta$。

• 估计误差 $\tilde\Theta$ 是无偏（unbiased）的，即它具有零无条件均值与零条件均值：

```math
E[\tilde\Theta \mid X = x] = 0, \qquad \text{对一切 } x,
```

```math
E[\tilde\Theta] = 0.
```

• 估计误差 $\tilde\Theta$ 与估计量 $\hat\Theta$ 不相关（uncorrelated）：

```math
\operatorname{cov}(\hat\Theta, \tilde\Theta) = 0.
```

• $\Theta$ 的方差可分解为

```math
\operatorname{var}(\Theta) = \operatorname{var}(\hat\Theta) + \operatorname{var}(\tilde\Theta).
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 无偏（$E[\tilde\Theta]=0$）、不相关 $(\mathrm{cov}(\hat\Theta,\tilde\Theta)=0)$、方差可加 $(\mathrm{var}(\Theta)=\mathrm{var}(\hat\Theta)+\mathrm{var}(\tilde\Theta))$——这三条合在一起，正是在内积空间里"正交分解"的随机变量版。第一性原理：把 $\hat\Theta$ 与 $\tilde\Theta=\Theta-\hat\Theta$ 视为两个"向量"，"不相关"即内积为零（正交），方差平方可加则恰是勾股定理 $\|\Theta\|^2=\|\hat\Theta\|^2+\|\tilde\Theta\|^2$ 的概率写照；三条性质其实由"最小均方最优性"一步到位推出。命名模板：orthogonal（正交）在这里指"不相关"，是比 independent（独立）弱得多却够用的几何条件。跨课程（线性代数 / 18.065）：这意味着条件期望 $E[\Theta\mid X]$ 就是把 $\Theta$ 向「由 $X$ 的可测函数构成的子空间」做正交投影，$E[(\hat\Theta)^2]$ 是投影长度、$E[(\tilde\Theta)^2]$ 是余长——维纳滤波、卡尔曼与岭回归共享同一勾股骨架。反例：方差可加是"不相关"的推论而非"独立"的推论——独立必不相关，反之不然；若只凭 $\hat\Theta$ 与 $\tilde\Theta$ 不相关就断言独立，就滑进了贝叶斯里最常见的误读。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页顶部三条性质中的记号在 OCR 中被读成 `8`/`e` 的混排（如 `E[e I X = x] = 0`、`coV(8, e)`、`var(8) = var(8) + var(e)`，且 `for all x`、`=`、`0` 各符号被拆散在相邻若干行），无法逐字还原其原书写。上文统一按 §8.3 的标准记号 $\hat\Theta = E[\Theta\mid X]$（估计量）与 $\tilde\Theta = \Theta - \hat\Theta$（估计误差）复原为 $E[\tilde\Theta\mid X=x]=0$、$E[\tilde\Theta]=0$、$\mathrm{cov}(\hat\Theta,\tilde\Theta)=0$、$\mathrm{var}(\Theta)=\mathrm{var}(\hat\Theta)+\mathrm{var}(\tilde\Theta)$；三者与下页 Example 8.14 的推证交叉吻合，非臆造。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.14（无信息观测，Uninformative Observation。）**</span>

我们说观测 $X$ 是无信息（uninformative）的，如果均方估计误差（mean squared estimation error）$E[\tilde\Theta^2]$ 与 $\operatorname{var}(\Theta)$、即 $\Theta$ 的无条件方差相同。何时会出现这种情况呢？

利用公式 $\operatorname{var}(\Theta) = \operatorname{var}(\hat\Theta) + \operatorname{var}(\tilde\Theta)$，我们看出 $X$ 是无信息的当且仅当 $\operatorname{var}(\hat\Theta) = 0$。一个随机变量的方差为零，当且仅当该随机变量是一个常数、等于其均值。由此我们得出结论：$X$ 是无信息的，当且仅当估计量 $\hat\Theta = E[\Theta\mid X]$ 对 $X$ 的每个取值都等于 $E[\Theta]$。

若 $\Theta$ 与 $X$ 独立，则对一切 $x$ 有 $E[\Theta\mid X = x] = E[\Theta]$，从而 $X$ 确为无信息的，这十分直观。然而，其逆命题并不成立：有可能 $E[\Theta\mid X = x]$ 恒等于常数 $E[\Theta]$，而 $\Theta$ 与 $X$ 并不独立。（你能构造出这样的一个例子吗？）

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 8.14 那句"你能构造出这样的例子吗"是抛给读者的钩子，也点破了方差分解 $\mathrm{var}(\Theta)=\mathrm{var}(\hat\Theta)+\mathrm{var}(\tilde\Theta)$ 的信息含义。第一性原理：估计误差 $\tilde\Theta$ 与估计 $\hat\Theta$ 不相关（协方差为零），故总方差被干净地切成"signal（被解释部分）"与"noise（未解释部分）"两块；观测 $X$ 提供信息，就是从 $\Theta$ 的方差里成功剥出一块归给 $\hat\Theta$。命名模板：uninformative（无信息）直接以"方差是否被压减"来定义，而非看 $X$ 本身在不在变化。跨课程（信号处理/通信）：这就是信噪比 SNR $=\mathrm{var}(\hat\Theta)/\mathrm{var}(\tilde\Theta)$ 的静态版，本质与维纳滤波的一致最优重构同一主题。反例：$E[\Theta\mid X]$ 恒为常数只说明该函数是平的（均方意义下无信息），绝不意味着统计独立——例如让 $X=\Theta$、再把观测换成 $X^2$，$E[\Theta\mid X^2]$ 仍可能就是常数，可 $\Theta$ 与 $X^2$ 显然相关；独立是远比"无信息"苛刻的条件。

---

<span style="color:#c0392b;">**§8.3　多个观测与多个参数的情形（The Case of Multiple Observations and Multiple Parameters）（续）**</span>

> <span style="color:#7f8c8d;">小节：本页在 Example 8.14 之后新起小节「The Case of Multiple Observations and Multiple Parameters」，将 LMS 推广到观测为向量的情形；按规范其仍属 §8.3 收尾（§8.4 自书页 p437 起才正式起节），此处标为 §8.3 下的小节。</span>

前面的讨论一直是把 $X$ 当作单个随机变量来表述的。然而，整个论证及其全部结论即便在 $X$ 是随机变量的向量、即 $X = (X_1, \ldots, X_n)$ 时依然成立。因此，均方估计误差在采用 $E[\Theta \mid X_1, \ldots, X_n]$ 作为估计量时达到最小，即

```math
E\big[ \big( \Theta - E[\Theta \mid X_1, \ldots, X_n] \big)^2 \big]
\;\le\;
E\big[ \big( \Theta - g(X_1, \ldots, X_n) \big)^2 \big],
```

对所有估计量 $g(X_1, \ldots, X_n)$ 都成立。

这为一般性的最小均方（LMS）估计问题提供了一个完整的解，但由于下述原因常常难以实施：

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页中「..., i.e.,」与「for all estimators $g(X_1, \ldots, X_n)$」之间的不等式公式在 OCR 中整体缺失（原页仅以 `. .` 呈现）；上文按 §8.3 的条件期望最小均方误差的标准性质 $E[(\Theta - E[\Theta\mid X_1,\dots,X_n])^2] \le E[(\Theta - g(X_1,\dots,X_n))^2]$ 复原，未臆造原文未含的任何具体数值。本页并以「由于下述原因难以实施：」的列举句收尾，读者的原因列表承接于下一页（PDF p445）。</span>
<!-- ===== PDF p445 ===== -->

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）**</span>

> <span style="color:#7f8c8d;">本节为 §8.3/§8.4 的分界页（书页 p437）。页首承接上一页（PDF p444）§8.3「多观测与多参数的情形（The Case of Multiple Observations and Multiple Parameters）」的论述——即条件期望 $E[\Theta \mid X_1, \ldots, X_n]$ 作为最优估计量难以实现的 (a)、(b) 两原因以及「估计多个参数」的讨论；随后在中部以粗题「8.4 Bayesian Linear Least Mean Squares Estimation」另起新节 §8.4。故本页前段为 §8.3 的续接，后段为新节 §8.4。</span>

<span style="color:#00838f;">**§8.3　贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）（续）**</span>

原因如下：

(a) 为了计算条件期望（conditional expectation）$E[\Theta \mid X_1, \ldots, X_n]$，我们需要一个完整的概率模型，即联合概率密度函数（joint PDF）$f_{\Theta, X_1, \ldots, X_n}$。

(b) 即使具备这样的联合概率密度函数，$E[\Theta \mid X_1, \ldots, X_n]$ 也可能是 $X_1, \ldots, X_n$ 的一个非常复杂的函数。

因此，实践者往往求助于条件期望的某种近似（approximations），或者把注意力集中在那些并非最优、但实现起来简单而容易的估计量（estimators）上。最常用的方法将在下一节讨论，它把范围限制在『线性估计量（linear estimators）』这一类中。

最后，考虑我们希望估计多个参数（multiple parameters）$\Theta_1, \ldots, \Theta_m$ 的情形。这时很自然地要考虑如下准则

```math
\sum_{i=1}^{m} E\Big[\big(\hat{\Theta}_i - \Theta_i\big)^2\Big],
```

并在所有估计量 $\hat{\Theta}_1, \ldots, \hat{\Theta}_m$ 上将其最小化。但这等价于：对每一个 $i$，都去求一个使 $E\big[(\hat{\Theta}_i - \Theta_i)^2\big]$ 最小的估计量 $\hat{\Theta}_i$；于是我们实质上是在处理 $m$ 个两两 decoupled（解耦）的估计问题，每个对应一个未知参数 $\Theta_i$，最后得出 $\hat{\Theta}_i = E[\Theta_i \mid X_1, \ldots, X_n]$（对一切 $i$ 成立）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「多参数的最小均方 = 各参数各自最小均方」读来顺理成章，实则点破了平方准则与范数的优雅耦合。第一性原理：对每个 $\Theta_i$ 单独最小化 $E[(\hat\Theta_i-\Theta_i)^2]$，再看总目标 $\sum_i E[(\hat\Theta_i-\Theta_i)^2]$——因为平方和的每一项只含自己的 $\Theta_i$、不含交叉项，各参数彼此 decoupled（解耦），全局最小化退化为 $m$ 个独立的单参数问题。命名模板：decoupled（解耦）指"目标函数是各项之和、无交叉项"；一旦出现交叉项（如 $E[\hat\Theta_1\hat\Theta_2]$），解耦即告破碎。跨课程（线性代数 / 18.05）：这正像二次型 $f(x_1,\dots,x_m)=\sum_i a_ix_i^2$（对角矩阵）的最优在各自坐标处各取极小——把分母换成协方差矩阵的投资组合里，各分量才真正两两耦合；所谓"各参数独立求解"成立的条件，正是目标函数 separable（可分离）。反例：解耦依赖"逐分量平方损失"这一准则选择；若改目标为 $\sum_i(\hat\Theta_i-\Theta_i)^2$ 之上加权重或耦合交叉项（如联合协方差惩罚），解耦即失效、必须联合求解——Lasso/ridge 的组稀疏正是在这一步扔掉分量解耦、换取结构信息。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 多参数准则的公式在 OCR 中丢失：页行「consider the criterion」与「and minimize it」之间是一个空白（源 OCR 该处缺失公式，仅余空行）。此处按书 §8.3 多参数标准 L MS 准则还原为 $\sum_{i=1}^{m} E\big[(\hat{\Theta}_i - \Theta_i)^2\big]$，且与后文「对每个 i 独立最小化 $E[(\hat{\Theta}_i - \Theta_i)^2]$」的叙述恰好一致；所还原内容未含任何原文未出现的数值。</span>

---

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）**</span>

在本节中，我们导出一个在受限估计量类（restricted class of estimators）内使均方误差（mean squared error）最小的估计量：即那些为观测（observations）线性函数（linear functions）的估计量。虽然该估计量可能导致较大的均方误差，但它有一个显著的实用优势：只需进行简单的计算，且只涉及参数与观测的均值（means）、方差（variances）与协方差（covariances）。因此，在条件期望/LMS 估计量难以计算的场合，它是一个有用的替代选择。

基于观测 $X_1, \ldots, X_n$ 的随机变量 $\Theta$ 的线性估计量（linear estimator）具有如下形式

```math
\hat{\Theta} = a_1 X_1 + \cdots + a_n X_n + b.
```

对标量（scalars）$a_1, \ldots, a_n, b$ 的某一个特定选择，相应的均方误差为

```math
E\Big[\big(\Theta - a_1 X_1 - \cdots - a_n X_n - b\big)^2\Big].
```

线性 LMS 估计量（linear LMS estimator）选择 $a_1, \ldots, a_n, b$ 以使上式最小。我们首先针对 $n = 1$ 的情形给出解，然后再加以推广。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把最优估计从"任意函数"缩到"线性组合"，是用一个小小的 b 换回巨大的可算性。第一性原理：完整 LMS 需要联合分布 $f_{\Theta,X}$ 和无约束的最优函数 $g(X)=E[\Theta\mid X]$；线性 LMS 只在 affine（仿射）函数 $a_1X_1+\cdots+b$ 里找最好，只需一阶、二阶矩（均值/方差/协方差）即可定解——牺牲的是全局最优，换来的是只要矩、不要分布就能落地的工程友好性。命名模板：linear（线性）指"估计器是观测的线性组合（加常数）"，由之把问题从函数空间压缩到 $n+1$ 维参数空间。跨课程（信号处理 / 18.065 维纳滤波）：受限线性类是维纳滤波与自适应 LMS 算法的一切前提——在线估计只根据梯度更新系数、无需联合密度，靠的正是"一阶二阶矩"这丁点信息。反例：当后验均值恰好是 $X$ 的线性函数时（如高斯共轭或 Beta 例），线性 LMS 与全局 LMS 重合、零损失；而当后验均值强烈非线性（如例 8.11 的对数函数），压进直线后偏差骤增——"线性"是省了计算却不保最优的折价。

<span style="color:#2471a3;">**[§]**</span> <span style="color:#00838f;">**基于单个观测的线性最小均方估计（Linear Least Mean Squares Estimation Based on a Single Observation）**</span>

我们感兴趣的是求出能最小化均方估计误差（mean squared estimation error）$E\big[(\Theta - aX - b)^2\big]$ 的 $a$ 与 $b$，这里它对应于 $\Theta$ 的一个线性估计量 $aX + b$。假设 $a$ 已被选定，那么我们应当如何选择 $b$？这与如下问题相同……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 线性估计量的形式式（紧接「has the form」之后）与「给定标量选择下的均方误差」式（紧接「the corresponding mean squared error is」之后）在 OCR 中被丢失（源 OCR 该两处均为空白行）。此处按书 §8.4 标准形式还原为 $\hat{\Theta} = a_1 X_1 + \cdots + a_n X_n + b$ 与其均方误差 $E\big[(\Theta - a_1 X_1 - \cdots - a_n X_n - b)^2\big]$，与本页末已知的 $n=1$ 情形 $E[(\Theta - aX - b)^2]$ 一致；另，末「How should we choose b?」句中均方误差式原文 $E[(\Theta - aX - b)^2]$ 的右括号在 OCR 中缺失，已按语义补全。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p446）：本页在「基于单个观测的线性最小均方估计」小节开头处截断（"This is the same as…"），关于如何优化选择 $b$（即当 $a$ 固定时均方误差关于 $b$ 的一阶条件）将在下一页继续。</span>
<!-- ===== PDF p446 ===== -->

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）**</span>

<span style="color:#00838f;">**§8.4　基于单个观测的线性最小均方估计（Linear Least Mean Squares Estimation Based on a Single Observation）（续）**</span>

> <span style="color:#7f8c8d;">本页（书页 p438）承接上一页（PDF p445）§8.4「基于单个观测的线性最小均方估计」小节的开头（"This is the same as…"）。为求出均方估计误差 $E[(\Theta - aX - b)^2]$ 的最小化参数 $a, b$，本页先讨论当 $a$ 已选定时间应如何选 $b$，再把已得表达式对 $a$ 求极值，最终得到「线性 LMS 估计公式」框（Linear LMS Estimation Formulas）。本页全为推导，不含编号例子（Example）。</span>

我们感兴趣的是求使均方估计误差（mean squared estimation error）$E\big[(\Theta - aX - b)^2\big]$ 最小的 $a$ 与 $b$。现在，选定一个常数 $b$ 来估计随机变量 $\Theta - aX$。根据第 8.3 节开头的讨论，最佳选择是

```math
b = E[\Theta - aX] = E[\Theta] - a E[X].
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 第一步先给最优 $b$、第二步再来优化 $a$，这不是偷懒，而是利用了"可分离"的结构把二维问题切成两步。第一性原理：对固定的 $a$，关于 $b$ 的最小化是"无条件常数估计"的直接应用——最佳 $b$ 必取 $b=E[\Theta-aX]$ 使偏差归零、恰把误差化到 $\operatorname{var}(\Theta-aX)$；由此剩下的只是关于 $a$ 的一维最小化，把两参数一步求导改写成了"先中心化、再定斜率"的两段式。命名模板：把这种"先定截距、再定斜率"的次序称作 intercept–slope decoupling（截距-斜率分离），是仿射拟合的惯用套路。跨课程（优化 / 18.065）：这等价于把均方误差看成 $(a,b)$ 的二次型、先对齐其无偏平移、再最小化剩下关于 $a$ 的二次——与梯度下降先归一化、再迭代的常见流程同构。反例：分离成立的前提是损失在 $b$ 上是二次且无约束、且目标关于 $(a,b)$ 可分；若给 $b$ 加约束（如 $b\ge0$）或目标含 $a,b$ 交叉的正则项，"先修 $b$ 再解 $a$"就会不再最优，须改为联合求解。

在这一 $b$ 的选择下，剩下的任务就是关于 $a$ 最小化表达式

```math
E\Big[\big(\Theta - aX - E[\Theta] + aE[X]\big)^2\Big].
```

我们把这一表达式写成

```math
\mathrm{var}(\Theta - aX) = \sigma_\Theta^2 + a^2 \sigma_X^2 + 2\,\mathrm{cov}(\Theta, -aX)
= \sigma_\Theta^2 + a^2 \sigma_X^2 - 2a \cdot \mathrm{cov}(\Theta, X),
```

其中 $\sigma_\Theta$ 与 $\sigma_X$ 分别是 $\Theta$ 与 $X$ 的标准差（standard deviations），并且

```math
\mathrm{cov}(\Theta, X) = E\Big[\big(\Theta - E[\Theta]\big)\big(X - E[X]\big)\Big]
```

是 $\Theta$ 与 $X$ 的协方差（covariance）。为最小化 $\mathrm{var}(\Theta - aX)$（它是 $a$ 的二次函数（quadratic function）），我们令其关于 $a$ 的导数为零并解出 $a$。于是得到

```math
a = \frac{\mathrm{cov}(\Theta, X)}{\sigma_X^2} = \rho\,\frac{\sigma_\Theta}{\sigma_X},
```

其中

```math
\rho = \frac{\mathrm{cov}(\Theta, X)}{\sigma_\Theta\, \sigma_X}
```

是相关系数（correlation coefficient）。在这一 $a$ 的选择下，所得线性估计量 $\hat{\Theta}$ 的均方估计误差（mean squared estimation error）为

```math
\begin{aligned}
\mathrm{var}\big(\Theta - \hat{\Theta}\big)
&= \sigma_\Theta^2 + a^2 \sigma_X^2 - 2a \cdot \mathrm{cov}(\Theta, X)\\
&= \sigma_\Theta^2 + \rho^2\,\frac{\sigma_\Theta^2}{\sigma_X^2}\,\sigma_X^2
\;-\; 2\rho\,\frac{\sigma_\Theta}{\sigma_X}\,\big(\rho\,\sigma_\Theta\,\sigma_X\big)\\
&= (1 - \rho^2)\,\sigma_\Theta^2.
\end{aligned}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 本页方差、标准差与相关系数符号在 OCR 中被严重误读：随机变量 $\Theta$ 被读作数字 `8`，协方差下标处方差符号被拆读成 `ae`/`ax`/` a2` 等碎片（如源 OCR「where ae and ax are the standard deviations of 8 and X」实为「where $\sigma_\Theta$ and $\sigma_X$ are the standard deviations of $\Theta$ and $X$」）。上文按书 §8.4 单观测情形的标准推导忠实还原为 $\sigma_\Theta^2$、$\sigma_X^2$、$\rho = \mathrm{cov}(\Theta, X)/(\sigma_\Theta \sigma_X)$ 及 $a = \mathrm{cov}(\Theta, X)/\sigma_X^2 = \rho\,\sigma_\Theta/\sigma_X$，与「(1 - $\rho^2$)$\sigma_\Theta^2$」的最终结果一致，未臆造任何数值。</span>

<span style="color:#00838f;">**线性 LMS 估计公式（Linear LMS Estimation Formulas）**</span>

* 基于 $X$ 的 $\Theta$ 的线性 LMS 估计量（linear LMS estimator）$\hat{\Theta}$ 为

```math
\hat{\Theta} = E[\Theta] + \frac{\mathrm{cov}(\Theta, X)}{\mathrm{var}(X)}\,(X - E[X])
= E[\Theta] + \rho\,\frac{\sigma_\Theta}{\sigma_X}\,(X - E[X]),
```

  其中

```math
\rho = \frac{\mathrm{cov}(\Theta, X)}{\sigma_\Theta\, \sigma_X}
```

  是相关系数（correlation coefficient）。

* 对应的均方估计误差（mean squared estimation error）等于

```math
\mathrm{var}\big(\Theta - \hat{\Theta}\big) = (1 - \rho^2)\,\sigma_\Theta^2.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 最优线性 LMS 的误差 $(1-\rho^2)\sigma_\Theta^2$ 是一块把"相关有多强"与"估计有多准"焊在一起的配方。第一性原理：最优斜率 $a=\rho\,\sigma_\Theta/\sigma_X$ 是"单位 $X$ 变化能带动的 $\Theta$ 变化"；把 $X$ 的信息折进 $\Theta$，剩余不确定性由相关系数平方 $\rho^2$ 决定——$\rho\to\pm1$ 时误差归零（$X$ 几乎完全决定 $\Theta$），$\rho=0$ 时回到原始方差 $\sigma_\Theta^2$（$X$ 毫无用处）。命名模板：$\rho$ 名 correlation coefficient（相关系数），它度量"线性可解释"的方差所占比例，故有决定系数 $R^2$。跨课程（线性代数 / 18.065，投影定理）：$\rho^2\sigma_\Theta^2$ 正是 $\Theta$ 向"由 $X$ 张成的一维子空间"投影的长度，$(1-\rho^2)\sigma_\Theta^2$ 是垂直余长——与 §8.3 的正交分解同宗，只是把投影对象从"可测函数空间"换成"线性子空间"。反例：$\rho=0$ 只说明 $X$ 与 $\Theta$ 线性无关，却可能隐藏强非线性关系（如 $X=\pm\sqrt{|\Theta|}$ 造成 $\rho=0$ 却携带丰富信息）；此时线性 LMS 无能为力、但全局 LMS 仍会利用它——相关性不为零才是线性可改写的前提。

> <span style="color:#7f8c8d;">衔接下面（PDF p447）：本页已收敛到最优线性均方误差 $(1-\rho^2)\sigma_\Theta^2$（该式已在上文推导及「线性 LMS 估计公式」框中两次给出）；页尾在「…equal to（等于）」处截断，下一页将继续 §8.4 对该线性估计量诸性质的解释与后续讨论。</span>
<!-- ===== PDF p447 ===== -->

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，继续 §8.4 的论述：先是收尾上一页关于线性 LMS 估计量性质的讨论（其公式直观解释、相关系数对估计质量的影响、以及估计误差性质可推广到线性 LMS 的情形），随后本页开始新的 **Example 8.15**（基于 X 的 Θ 的线性 LMS 估计量推导，即 Juliet 迟到模型）。例 8.15 的推导在本页中途被截断，其线性 LMS 估计量的最终表达式在下一面完成。</span>

> <span style="color:#7f8c8d;">[OCR 说明] 本页源 OCR 中，参数 $\Theta$ 多被误读为数字 8 或字母 e（如 "covariance of 8 and X"、"E[eX]"），相关系数 $\rho$ 被误读为字母 p（如 "I p i" 即 $|\rho|$）。以上均按 §5 符号约定（$\Theta$ 表示未知参数、$X$ 表示观测）忠实还原，非臆造数值。</span>

---

线性 LMS 估计量（linear LMS estimator）的公式只涉及 $\Theta$ 与 $X$ 的均值（means）、方差（variances）和协方差（covariance）。此外，它具有直观的解释。为具体起见，假设相关系数（correlation coefficient）$\rho$ 为正。估计量（estimator）以 $E[\Theta]$ 作为 $\Theta$ 的基线估计（baseline estimate），然后通过纳入 $X - E[X]$ 的值来对其加以调整。例如，当 $X$ 大于其均值时，$X$ 与 $\Theta$ 之间的正相关（positive correlation）表明 $\Theta$ 预期会大于其均值。相应地，得到的估计值被设为一个大于 $E[\Theta]$ 的值。$\rho$ 的值也影响估计的质量。当 $|\rho|$ 接近 $1$ 时，这两个随机变量高度相关，知道 $X$ 就能让我们精确地估计 $\Theta$，从而得到较小的均方误差（mean squared error）。

最后我们指出，第 8.3 节（Section 8.3）中给出的关于估计误差（estimation error）的那些性质，可以证明当 $\Theta$ 为线性 LMS 估计量（linear LMS estimator）时仍然成立；请参见章末习题（end-of-chapter problems）。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.15（ X 在 $[0,\Theta]$ 上均匀、$\Theta$ 在 $[0,1]$ 上均匀先验时的线性 LMS 估计。）**</span>

我们重新考察示例 8.2、8.7 与 8.12（Examples 8.2, 8.7, and 8.12）中的模型：在该模型中，Juliet 总是迟到一段量 $X$，它在区间 $[0,\Theta]$ 上均匀分布（uniformly distributed），而 $\Theta$ 是一个具有均匀先验概率密度函数 $f_{\Theta}(\theta)$（uniform prior PDF）的随机变量，其取值区间为 $[0,1]$。让我们推导基于 $X$ 的 $\Theta$ 的线性 LMS 估计量（linear LMS estimator）。

利用 $E[X \mid \Theta] = \Theta/2$ 这一事实以及迭代期望定律（law of iterated expectations），$X$ 的期望值为

```math
E[X] = E\big[\,E[X \mid \Theta]\,\big] = E[\Theta/2] = E[\Theta]/2 = \frac{1}{2}\cdot\frac{1}{2} = \frac{1}{4}\;.
```

此外，利用 law of total variance（全方差定律）（这与第 4 章中示例 4.17 的计算相同），我们有

```math
\operatorname{var}(X) = \frac{7}{144}\;.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「$\operatorname{var}(X)=\frac{7}{144}$」这一格数字，是 law of iterated expectations（迭代期望）与 law of total variance（全方差定律）经手运算一次的具体果实。第一性原理：$E[X]=E[E[X\mid\Theta]]$ 先剥掉 $\Theta$ 得 $\frac12\cdot\frac12=\frac14$；全方差 $\operatorname{var}(X)=E[\operatorname{var}(X\mid\Theta)]+\operatorname{var}(E[X\mid\Theta])$ 把总方差拆成"组内噪声"与"组间（随 $\Theta$）波动"两块，本例恰好凑出 $\frac{7}{144}$——这是把"未知参数混合造成的额外散布"量化的标准脚本。命名模板：$\operatorname{var}(X)=E[\cdot]+\operatorname{var}(\cdot)$ 双项合计，是"条件方差的期望 + 条件期望的方差"两个各自独立的来源相加。跨课程（随机信号 / 18.065 ANOVA）：这正是"组间方差 + 组内方差 = 总方差"的 ANOVA 分解——把 $X$ 的变异性归因到参数的随机性而非纯噪声，是信噪比与方差分量分析的基础。反例：不少读者把 $\frac{7}{144}$ 当常数背，其实它完全依赖模型设定——换 $\Theta$ 的方差或 $W$ 的分布，这个数立刻变；若误用全方差定律而把 $\Theta$ 当非随机、只算 $E[\operatorname{var}(X\mid\Theta)]$，就会丢掉"参数不确定"这一大项贡献，严重低估 $\operatorname{var}(X)$。

现在我们用公式

```math
\operatorname{cov}(\Theta,\; X) = E[\Theta X] - E[\Theta]\, E[X],
```

以及如下事实

```math
E[\Theta^2] = \operatorname{var}(\Theta) + E[\Theta]^2
```

来求 $X$ 与 $\Theta$ 的协方差（covariance）。我们有

```math
E[\Theta X] = E\big[\,E[\Theta X \mid \Theta]\,\big] = E\big[\,\Theta\, E[X \mid \Theta]\,\big] = E[\Theta^2/2]
= \frac{1}{2}\, E[\Theta^2]
= \frac{1}{2}\Big(\operatorname{var}(\Theta) + E[\Theta]^2\Big)
= \frac{1}{2}\left(\frac{1}{12} + \frac{1}{4}\right) = \frac{1}{6},
```

其中第一个等号由迭代期望定律（law of iterated expectations）得出，第二个等号成立，是因为对一切 $\theta$ 有

```math
E[\Theta X \mid \Theta = \theta] = E[\,\theta X \mid \Theta = \theta\,] = \theta\, E[X \mid \Theta = \theta]\;.
```

> <span style="color:#7f8c8d;">衔接下一面（PDF p448）：Example 8.15 在本页求得了 $E[\Theta X]$，并随后应用公式 $\operatorname{cov}(\Theta,X) = E[\Theta X] - E[\Theta]\,E[X]$；线性 LMS 估计量的最终表达式（给定已知的 $E[\Theta] = \tfrac12$、$E[X] = \tfrac14$、$\operatorname{var}(X) = \tfrac{7}{144}$ 与协方差）将在下一页据此求出。</span>
<!-- ===== PDF p448 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，继续 §8.4 的 **Example 8.15**：本页在其第二部分完成线性 LMS 估计量（linear LMS estimator）的数值计算——先计算 $\Theta$ 与观测 $X$ 的协方差（covariance），代入线性 LMS 公式得估计量的显式形式 $\hat\Theta = \tfrac67 X + \tfrac27$；随后用 Example 8.12 导出的公式计算对应的条件均方误差（conditional mean squared error），并把该线性 LMS 估计量与 MAP 估计量、LMS 估计量在 figure 8.12 中并以图形方式进行比较。本页末即为 **Figure 8.12** 的图注。本页不含新例子编号。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.15（续）——线性 LMS 估计量的计算与比较**</span>

于是，协方差（covariance）为

```math
\operatorname{cov}(\Theta, X) \;=\; \mathbb{E}[\Theta X] - \mathbb{E}[\Theta]\,\mathbb{E}[X]
\;=\; \tfrac16 - \tfrac12\cdot\tfrac14
\;=\; \tfrac{1}{24}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上面这行协方差数值（$\mathbb{E}[\Theta X]=\tfrac16$、$\mathbb{E}[\Theta]=\tfrac12$、$\mathbb{E}[X]=\tfrac14$，即原文括注中的 $6,1,2,1,4,1$ 被 OCR 打散成碎片如 `61 21 41 = 241`）在旧源 OCR 中严重残碎，无法逐字确证。此处按全页中可辨且自洽的数值链重建：原页随后给出 $\operatorname{cov}(\Theta,X)=\tfrac{1}{24}$、$\operatorname{var}(X)=\tfrac{7}{144}$、$\operatorname{cov}/\operatorname{var}=\tfrac67$，以及估计量 $\hat\Theta = \tfrac67 X + \tfrac27$，据此反推上述三个中间值（$E[\theta X]=\tfrac16$、$E[\theta]=\tfrac12$、$E[X]=\tfrac14$）与之严格自洽（$\tfrac16-\tfrac12\cdot\tfrac14=\tfrac{1}{24}$，且 $E[\theta]=\tfrac12$ 代入估计量得 $\tfrac12+\tfrac67(X-\tfrac14)=\tfrac67X+\tfrac27$），非臆造新数值。</span>

线性 LMS 估计量（linear LMS estimator）为

```math
\hat\Theta \;=\; \mathbb{E}[\Theta] + \frac{\operatorname{cov}(\Theta, X)}{\operatorname{var}(X)} \left(X - \mathbb{E}[X]\right)
\;=\; \tfrac12 + \frac{\tfrac{1}{24}}{\tfrac{7}{144}} \left(X - \tfrac14\right)
\;=\; \tfrac67 X + \tfrac27.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> $\hat\Theta=\frac67X+\frac27$ 这个漂亮数字里的 $\frac67$ 系数，藏着"线性 LMS 有多相信观测"的全部秘密。第一性原理：$\frac67=\frac{\operatorname{cov}(\Theta,X)}{\operatorname{var}(X)}=\frac{1/24}{7/144}$，它是"观测 $X$ 每偏离均值 $1$，对 $\Theta$ 的估计就跟着动 $\frac67$"的斜率；因 $X$ 含噪声（$\operatorname{var}(X)=7/144$）远大于信号的方差 $\operatorname{var}(\Theta)=1/12$，斜率被压到不足 1——这正是"数据被噪声稀释、估计向先验均值 1/2 收缩"的数学言说。命名模板：把小于 1 的系数读出 shrinkage（收缩率），估计量总被拉回先验均值，绝不信到饱和。跨课程（回归 / 18.065）：这恰是与均方最优回归系数一模一样的"最小二乘斜率"，只是分母换成了总的观测方差；用方差比决定置信程度，是卡尔曼增益的雏形。反例：$\frac67$ 是对"线性"模型量身定做的常数——若 $\Theta X$ 关系根本不线性（如例 8.11 的对数型后验），这个斜率会给出一律偏低、且在大 $x$ 处落出 $[0,1]$ 的荒谬估计；正因为如此，正文才提醒在 $x\to1$ 附近线性逼近会越界 $\theta>1$。

其中 $\operatorname{var}(X) = \tfrac{7}{144}$。

对应的条件均方误差（conditional mean squared error）用一个由 **Example 8.12** 中所推导的公式来计算，把刚才导出的表达式（$\hat\Theta = \tfrac67 X + \tfrac27$）代入即可。

在图 8.12 中，我们把该线性 LMS 估计量与 MAP 估计量（MAP estimator）以及 LMS 估计量放在一起比较（cf. Examples 8.2、8.7 与 8.12）。请注意：在感兴趣的区域（region of interest）的大部分范围内，LMS 估计量与线性 LMS 估计量几乎相同，两者对应的条件均方误差也几乎相同；而 MAP 估计量的均方误差（mean squared error）比其余两个估计量显著更大。当 $x$ 与 1 很接近时，线性 LMS 估计量的表现要差于另外两个估计量，并且确实可能给出一个估计值 $\hat\theta > 1$，这样它就落在了 $\Theta$ 的可能取值范围之外。

> <span style="color:#7f8c8d;">[图] **Figure 8.12**——三种估计量及其均方误差（mean squared errors）作为观测值 $x$ 的函数（as functions of the observed value $x$），对应于 Example 8.15 中的问题。上图面板为各估计（Estimates，含 MAP、LMS 与线性 LMS 估计曲线），横轴为观测值 $x$（约 $0$–$1$）；下图面板为标注 Mean Squared Error 的均方误差曲线，横轴同样为 $x$。此图文本框内各轴刻度在旧源 OCR 中被切碎，仅文字标签（Estimates／MAP Estimates／LMS Estimates／Linear LMS Estimates／Mean Squared Error）可辨。</span>

> <span style="color:#7f8c8d;">衔接下一面：本页（书页 p440）完成 Example 8.15 的线性 LMS 估计量与均方误差比较后，下一页（书页 p441）转入 §8.4 中 Example 8.16（涉及多个观测量与多个参数的情形，再次验证例号序列 8.15 → 8.16 连续）。</span>
<!-- ===== PDF p449 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页 §8.4 的论述：页首无新节标题，直接进入 **Example 8.16**（一元硬币偏差的线性 LMS 估计，Linear LMS Estimation of the Bias of a Coin），故小节标题带「（续）」，而例本身是新例（非续页）。该例重访例 8.4、8.8、8.13 的抛硬币问题，导出其线性最小均方（linear LMS）估计量；本页末已将各系数（$E[\Theta]$、$E[X]$、$\text{var}(X)$、$E[\Theta X]$、$\text{cov}(\Theta,X)$）计算完毕，并得出线性 LMS 估计量的最终形式。编号锚点：Example 8.13 的 LMS 估计结果与本页线性 LMS 估计结果相互印证（PDF p442／书目 p434 处有 Figure 8.10 图注与本结论呼应）。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.16（一元硬币偏差的线性 LMS 估计，Linear LMS Estimation of the Bias of a Coin。）**</span>

我们重新审视例 8.4、8.8 与 8.13 中的抛硬币（coin tossing）问题，并导出线性最小均方（linear LMS）估计量。这里，硬币正面朝上的概率被建模为一个随机变量 $\Theta$，其先验分布（prior distribution）在区间 $[0,1]$ 上均匀分布。硬币被独立地抛掷 $n$ 次，得到正面朝上的次数为一随机变量，记为 $X$。于是，若 $\Theta$ 等于 $\theta$，则随机变量 $X$ 服从参数为 $n$ 与 $\theta$ 的二项分布（binomial distribution）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页中符号 $\Theta$ 与 $\theta$ 在源 OCR 中被反复误读（如「random variable e … if e is equal to 0 … with parameters n and O」中，`e`/`0`/`O` 实为 $\Theta$ / $\theta$）；均匀先验区间 $[0,1]$、二项参数 $n$ 与 $\theta$ 等数值为可辨项，上文据此忠实还原为标准书写，未臆造其他数值。</span>

我们计算线性 LMS 估计量公式中所出现的各个系数。我们有 $E[\Theta] = 1/2$，且

```math
E[X] = E\bigl[E[X \mid \Theta]\bigr] = E[n\Theta] = \frac{n}{2}.
```

$\Theta$ 的方差为 $1/12$，故 $\sigma_\Theta = 1/\sqrt{12}$。此外，正如前一例所计算的，$E[\Theta^2] = 1/3$。若 $\Theta$ 取值为 $\theta$，则 $X$ 的（条件）方差为 $n\theta(1-\theta)$。利用全方差公式（law of total variance），我们得到

```math
\operatorname{var}(X)
= E\bigl[\operatorname{var}(X \mid \Theta)\bigr] + \operatorname{var}\bigl(E[X \mid \Theta]\bigr)
= E\bigl[n\Theta(1-\Theta)\bigr] + \operatorname{var}(n\Theta)
= \frac{n}{2} - \frac{n}{3} + \frac{n^2}{12}
= \frac{n(n+2)}{12}.
```

为求 $X$ 与 $\Theta$ 的协方差（covariance），我们使用公式

```math
\operatorname{cov}(\Theta, X)
= E[\Theta X] - E[\Theta]\,E[X]
= E[\Theta X] - \frac{n}{4}.
```

与例 8.15 类似，我们又有

```math
E[\Theta X] = \frac{n}{3},
```

故

```math
\operatorname{cov}(\Theta, X) = \frac{n}{3} - \frac{n}{4} = \frac{n}{12}.
```

将这些全部综合起来，我们得出结论：线性 LMS 估计量具有如下形式

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「takes the form」与「Notice that this agrees…」之间的线性 LMS 估计量公式行在源 OCR 中整行缺失（仅余空行）。按 §8.4 线性 LMS 估计的标准形式 $\hat\Theta = E[\Theta] + \dfrac{\operatorname{cov}(\Theta,X)}{\operatorname{var}(X)}(X-E[X])$，并代入本页已计算的可辨系数 $E[\Theta]=\tfrac12$、$\operatorname{cov}(\Theta,X)=\tfrac{n}{12}$、$\operatorname{var}(X)=\tfrac{n(n+2)}{12}$、$E[X]=\tfrac n2$，忠实推导得 $\hat\Theta = \dfrac{X+1}{n+2}$；此结果与本页下文及例 8.13 的 LMS 估计结论一致，绝非臆造数值，但该行原文具体排版未知，留待统一校对。</span>

```math
\hat\Theta
= E[\Theta] + \frac{\operatorname{cov}(\Theta,X)}{\operatorname{var}(X)}\bigl(X - E[X]\bigr)
= \frac{1}{2} + \frac{n/12}{n(n+2)/12}\left(X - \frac{n}{2}\right)
= \frac{X+1}{n+2}.
```

注意到这与我们在例 8.13 中所导出的 LMS 估计量一致。这并不令人意外：如果 LMS 估计量恰好是线性的——正如例 8.13 中的情形——那么该估计量在更窄的线性估计量（linear estimators）类中也是最优的。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「线性 LMS 与（不受限）LMS 一致」不是巧合，而是"后验均值恰好是观测的线性函数"时两条路线的殊途同归。第一性原理：全局 LMS 的最优解是 $g(X)=E[\Theta\mid X]$；若这个函数本身就是 $X$ 的仿射函数（本例 $E[\Theta\mid X]=\frac{X+1}{n+2}$ 确为线性），那么把候选类收窄到所有仿射函数并不会丢掉最优解——受限最优恰好落在非受限最优上。命名模板：把这种"窄类的解恰为全局最优"性质，对应到 constrained/unconstrained 两个优化问题的解重合；是"窄化可行集不损失最优"的特例。跨课程（高斯分布 / 18.05，Bickel）：对高斯共轭模型，后验均值恒为观测的仿射函数，所以线性 LMS 与全局 LMS 在此类下永远重合——这正是"线性 + 高斯 ＝ 最优"成立的关键所在。反例：后验均值为线性是"强到有点奢求"的性质——只要先验与观测稍有非共轭（如例 8.11 的对数后验），受限最优立刻劣于全局最优；教材因此用多个反例（$\frac{1-x}{-\log x}$ 型）反复提醒：线性相等靠的是模型结构，而非任何"线性的自然优越"。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 线性 LMS 只须知道一阶与二阶矩（均值、方差、协方差）即可写出答案，这正是它作为工程主力被追捧的根源。第一性原理：若把估计限制为 $a_1X_1+\cdots+a_nX_n+b$，优化目标仍是一元/多元二次式，最优系数由 normal equations（法方程）给出——即把 $\Theta$ 正交投影到由常量 $1$ 与各 $X_i$ 张成的线性子空间（函数空间）上。命名模板：linear（线性）限定"估计器必须是观测的线性组合"，宁可牺牲一点均方最优也要保住可算性。跨课程（信号与系统 / 18.065 维纳滤波）：这正是离散 Wiener filter（维纳滤波）与自适应 LMS 算法推导的入口——只依赖二阶矩、不要求完整联合分布，因而能在线稳定更新。反例：Example 8.16 里线性 LMS 与（非受限）LMS 恰一致，是因为该模型的后验均值恰好是观测的线性函数；而像 Example 8.11 那种 $E[\Theta\mid X]=\frac{1-x}{-\log x}$ 的非线性情形，强行套线性逼近就会给出偏离最优的解——"线性"是一桩划算的折扣，并不是免费的。
<!-- ===== PDF p450 ===== -->

<span style="color:#7f8c8d;">§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）中部续页。书页 p442（页眉 "Bayesian Statistical Inference / Chap. 8"）。本页承上页（书页 p441 的 Example 8.16 收尾）继续 §8.4 的论述，但页首出现新的小节标题 **The Case of Multiple Observations and Multiple Parameters（多观测与多参数的情形）**，故本页起为一个新的小节（不另起 Example 编号）。本页为**本单元（单元 9）的最后一页**——单元止于书页 p442；紧接其后的书页（§8.4 后续与小节外部内容）属单元 10。</span>

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）（续）**</span>

<span style="color:#c0392b;">**多观测与多参数的情形（The Case of Multiple Observations and Multiple Parameters）**</span>

线性 LMS 方法论可推广到多重观测（multiple observations）的情形。对于线性 LMS 估计量（linear LMS estimator），存在一个以类似方式推导出来的类似公式。它只涉及各种随机变量两两之间的均值（means）、方差（variances）与协方差（covariances）。此外，若存在多个待估参数 $\Theta_i$，我们可以考虑如下准则

```math
E\Big[(\hat\Theta_1 - \Theta_1)^2 + \cdots + (\hat\Theta_m - \Theta_m)^2\Big],
```

并在所有作为观测之线性函数的估计量 $\hat\Theta_1,\ldots,\hat\Theta_m$ 之上对其最小化。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述多参数准则公式所在的一行（源 OCR 中位于「we may consider the criterion」与「and minimize it over all estimators $\hat\Theta_1,\ldots,\hat\Theta_m$」之间的空行）在源 OCR 中为空白，公式本体未捕获。这里按随后的「对每个 $i$ 寻找最小化 $E[(\hat\Theta_i-\Theta_i)^2]$ 的线性估计量」的原文提示，重建为标准的多参数均方误差和 $E[(\hat\Theta_1-\Theta_1)^2+\cdots+(\hat\Theta_m-\Theta_m)^2]$；未臆造任何原文未暗示的系数或数值。</span>

这等价于对每个 $i$，寻找一个使 $E[(\hat\Theta_i - \Theta_i)^2]$ 最小的线性估计量（linear estimator）$\hat\Theta_i$，从而我们实质上是在处理 $m$ 个相互 decoupled（解耦）的线性估计问题，每个对应一个未知参数。

在存在多重观测且满足某种独立性性质的情形下，线性 LMS 估计量（linear LMS estimator）的公式得以简化，我们现在就来描述这一点。设 $\Theta$ 是均值为 $\mu$、方差为 $\sigma_0^2$ 的随机变量，并设 $X_1,\ldots,X_n$ 是如下形式的观测

```math
X_i = \Theta + W_i, \qquad i = 1,\ldots,n,
```

其中 $W_i$ 是均值为 $0$、方差为 $\sigma_i^2$ 的随机变量，它们代表观测误差（observation errors）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「observations of the form」之后、叙述 $W_i$「代表观测误差」之前的观测表达式行（源 OCR 中为空行）在源 OCR 中缺失。这里依据其后「$\Theta, W_1,\ldots,W_n$ 互不相关」「$W_i$ 均值为 $0$、方差 $\sigma_i^2$」以及下页线性 LMS 估计量公式中出现的 $X_i/\sigma_i^2$ 项，重建为标准的叠加噪声形式 $X_i = \Theta + W_i$（$i=1,\ldots,n$）；未臆造原文未含的数字。</span>

在随机变量 $\Theta, W_1,\ldots,W_n$ 互不相关（uncorrelated）的假设之下，基于观测 $X_1,\ldots,X_n$ 的 $\Theta$ 的线性 LMS 估计量被发现为

```math
\hat\Theta
= \frac{\dfrac{\mu}{\sigma_0^2} + \displaystyle\sum_{i=1}^{n}\dfrac{X_i}{\sigma_i^2}}
{\displaystyle\sum_{i=0}^{n}\frac{1}{\sigma_i^2}}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中源 OCR 把 $\sigma_0^2$（参数 $\Theta$ 的方差）误读为 `a5` / `a6`（亦见后文），且分子、分母及求和上下限被打散成多行碎片（仅余孤立记号如 `μ/a6`、`Σ Xi/σᵢ² (i=1 到 n)`、`Σ 1/σᵢ² (i=0 到 n)`、`i=l` 等）。此处按后文推导所得的 $b = (\mu/\sigma_0^2)/\sum_{i=0}^{n}(1/\sigma_i^2)$ 与 $a_j=(1/\sigma_j^2)/\sum_{i=0}^{n}(1/\sigma_i^2)$ 一致地还原为上面的 $\hat\Theta$ 表达式，下标 $0$ 指参数自身、下标 $1,\ldots,n$ 指各观测误差；未臆造数值。</span>

推导过程先构造如下函数

```math
E\Big[\Big(\Theta - (a_1 X_1 + \cdots + a_n X_n + b)\Big)^2\Big],
```

并通过令其关于 $a_1,\ldots,a_n,b$ 的偏导数（partial derivatives）等于零来把它最小化。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「the function」之后的具体函数式行（源 OCR 中为空行）未捕获。这里依据其关于 $a_1,\ldots,a_n,b$ 求偏导、最终再现上述 $\hat\Theta$ 公式的原文提示，重建为线性估计量 $a_1X_1+\cdots+a_nX_n+b$ 的均方误差 $E[(\Theta-(a_1X_1+\cdots+a_nX_n+b))^2]$，下标与求和范围与前文保持一致；未臆造系数或数值。</span>

经过一些计算（给出于章末习题之中），结果是

```math
b = \frac{\mu/\sigma_0^2}{\displaystyle\sum_{i=0}^{n}\frac{1}{\sigma_i^2}},
\qquad
a_j = \frac{1/\sigma_j^2}{\displaystyle\sum_{i=0}^{n}\frac{1}{\sigma_i^2}},
\qquad j = 1,\ldots,n,
```

由之即得前面给出的线性 LMS 估计量公式。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 最后一个公式 $\hat\Theta=\dfrac{\mu/\sigma_0^2+\sum_i X_i/\sigma_i^2}{\sum_i 1/\sigma_i^2}$ 把"多个观测如何合并"一锤定音，是整章最值得背的收尾。第一性原理：把 $(X_i,\sigma_i^2)$ 与"参数自身的先验 $(\mu,\sigma_0^2)$"一视同仁，每个数据源都按精度 $1/\sigma^2$ 加权、合力确定后验均值；先验均值 $\mu$ 在这里只是又一个"伪观测"，精度越低贡献越小——这正是把"先验＝伪数据"贯彻到最后的立场。命名模板：把这种精度加权平均称作 precision-weighted average（精度加权平均），又因其在方差视角下线性最优、也常记为 BLUE（Best Linear Unbiased Estimator，最优线性无偏估计）。跨课程（回归 / 18.065）：这与加权最小二乘的最优权重 $\propto 1/\sigma^2$ 完全同构；当先验也当观测时，它就是"岭回归往先验均值收缩"的贝叶斯版出口。反例：一切建立在 $W_i$ 互不相关、$\Theta,W_1,\ldots,W_n$ 互不相关这一假设上；一旦观测误差互相相关或有共同系统偏差，各 $\sigma_i^2$ 就不能被简单相加、权重须改成协方差矩阵的逆、交叉项的简单性立刻破产——"只认二阶矩"的简单是有前提的。

> <span style="color:#7f8c8d;">衔接下一面：本页为单元 9 结尾（书页 p442）。书页 p443 起（§8.4 后续内容及单元 10）不在本单元范围内。</span>
