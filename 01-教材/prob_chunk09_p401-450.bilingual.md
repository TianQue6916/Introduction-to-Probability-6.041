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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道排队链稳态题把生灭链（birth–death chain）的求解压缩成一个漂亮的比值公式。第一性原理：在有限容量 $m$ 的缓冲节点里，从状态 $j$ 出发只能靠某一次「到达且不服务（$b_j$）」涨到 $j+1$、靠某一次「服务且不到达（$d_{j+1}$）」跌回来，故往返流量平衡给出 $\pi_j b_j = \pi_{j+1} d_{j+1}$，即 $\pi_{j+1}=\frac{b_j}{d_{j+1}}\pi_j$——这就是 $\rho_j$ 的来源，也是全局平衡方程被拆成「相邻两态对」逐个成立的局部平衡。命名模板：把 $\rho_j=\frac{b_j}{d_{j+1}}$ 联想成「净上移倾向」，权重连乘 $\pi_j=\rho_{j-1}\cdots\rho_0\pi_0$ 就是沿链的一次次放大或衰减。跨课程（排队论 M/M/1/m / 6.041）：$n$ 台机器的共享服务员正是经典有限缓冲排队模型，$\pi_0$ 用归一化 $\sum_j\pi_j=1$ 定出，本质是总量守恒。反例：一旦允许 $b_m\neq 0$（满缓冲仍能到达），链就不是「从 $m$ 必回退」，上面的收敛比值会被破坏、稳态可能不存在——容量上限 $b_m=0$ 正是保证可遍历的那道闸门。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道「前 $m-1$ 条平衡方程相加即得第 $m$ 条」的题揭示了平衡方程组内部的一条代数恒等关系。第一性原理：因为每一行转移概率之和为 $1$（$\sum_j P_{kj}=1$ 即列和为 $1$），把前 $m-1$ 条方程对 $j$ 求和时，右端的 $\sum_j\sum_k\pi_kP_{kj}$ 先换序、再利用 $\sum_{j=1}^{m-1}P_{kj}=1-P_{km}$，便恰好消去同样的 $\sum_{k=1}^{m-1}\pi_k$，剩下的正是第 $m$ 条方程——也就是说，归一化（$\sum_j\pi_j=1$）已被隐含在平衡方程里，写方程组时它并不独立。命名模板：把这称作「方程的相关性（dependence）」是说它们线性相关、并不彼此独立。跨课程（线性代数 / 18.06）：这等价于说转移矩阵 $P$ 的转置乘以稳态向量 $\pi$ 等于 $\pi$，而「矩阵的行和都为 $1$（随机矩阵）」这一结构保证 $1$ 是它的一个特征值、$\pi$ 是左特征向量；$m$ 条方程线性相关、秩至多 $m-1$，所以总得补上归一化 $\sum_i\pi_i=1$ 才能确定唯一解。反例：若你只写平衡方程而漏掉归一化，解空间会是一整个过原点的直线族，任意缩放都是解——故「稳态概率必须和为 1」不是附赠的，是求解的必备第 $m$ 个方程。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 局部平衡方程 $\pi_i P_{ij}=\pi_j P_{ji}$ 的价值在于它把「全局稳态」升级成「每对状态双向流量相等」这一更精细的对称性。第一性原理：若对每一个 $i$ 都让「从 $i$ 流向 $j$ 的长程期望频率」等于「从 $j$ 流向 $i$ 的」——而不是只让每个状态的「总流入＝总流出」——那么逐个叠加这些两两平衡自然得到全局平衡方程，故局部平衡是全局平衡的充分条件（更强的条件）。命名模板：把这称作 time reversibility（时间可逆性），是因为若把整条轨迹倒过来放，单步转移概率仍由同一套 $\pi_iP_{ij}$ 决定，正放逆放看起来无法区分。跨课程（物理 / 统计力学 图论）：这恰是「细致平衡（detailed balance）」在马尔可夫链上的化身，也是 Metropolis–Hastings 算法构造可逆链、从而保证收敛到给定目标分布的全部数学依据。反例：(c) 问用仅含 3 个状态的三角链构造反例——从 1 可直接跳到 3 却没有反向路径，于是频率明显不对称、局部平衡被破坏；这说明可逆性绝非「任何马尔可夫链都自动满足」的平凡性质，而是需要逐对验证的非平凡结构。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 26 的灵魂是一条贴近工具层面的洞察：对一个马尔可夫链「每隔 $\ell$ 步抽样拍照」，得到的 $Y_n=X_{n\ell}$ 仍然是一个马尔可夫链，因为合并后的转移概率 $r_{ij}(\ell)$ 依旧是随机矩阵、马尔可夫性质在抽样时间序列上照样成立。第一性原理：给定 $X_{n\ell}$，过去 $X_{(n-1)\ell},\ldots$ 与未来 $X_{(n+1)\ell},\ldots$ 之间隔着一串中间的马尔可夫转移，条件独立性被保留，故马尔可夫性质不因粗粒化而丢失。命名模板：把这套式子 $r_{ij}(n+\ell)=\sum_k r_{ik}(n)r_{kj}(\ell)$ 称作 Chapman–Kolmogorov 方程，它是「用中间所有可能状态 $k$ 做中转」的全概率定理的逐次版本。跨课程（线性代数）：$r_{ij}(\ell)$ 正是转移矩阵的 $\ell$ 次幂 $P^\ell$ 之元素，故抽样链对应 $P^\ell$，而稳态是 $P$ 的不动左特征向量、自然也为 $P^\ell$ 所共享——(a)(c) 问在此视角下不过是「同一特征向量的两种写法」。反例：抽样会改变周期结构，若原链是周期的，抽样间隔取错会让常返类变得周期性依旧或丢失非周期假设的适用性，从而 $r_{ij}(\ell)$ 的极限可能不存在。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道「状态增广」题展示了一条威力极大的建模技巧：把长度有限的历史装进状态本身，就能把「依赖若干步过去」的非马尔可夫过程重新改写成马尔可夫链。第一性原理：用 $(X_{n-1},X_n)$ 取代 $X_n$ 作状态，新增的组件恰好记录了最后一次转移，于是未来只通过这个较胖的状态依赖过去，马尔可夫性质自动恢复；稳态概率也用乘法规则拆成 $\pi_i\cdot p_{ij}$——这就是「原始链处在 $i$ 且刚跳到 $j$」的长程频率。命名模板：把这种技巧称作「增广状态（state augmentation）」，是处理记忆性（memory）的标准外科手术：凡是有记忆的项，全部塞进球/状态里睁着眼睛看。跨课程（CSAPP 有限状态机 / 计算理论）：这正是把「需要记住最后 $k$ 个符号」的识别器升级为携带固定长度记忆的自动机，这也就牢牢绑定了「所需状态数随记忆长度 $k$ 指数/多项式增长」的代价。反例：增广会让状态空间从 $m$ 暴涨到 $m^{k+1}$，当 $k$ 很大时计算不可行——增广只解决「有没有效」，不解决「划不划算」。

---

<span style="color:#c0392b;">**§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 28.**</span> There are $m$ classes offered by a particular department, and each year, the students rank each class from $1$ to $m$, in order of difficulty, with rank $m$ being the highest. Unfortunately, the ranking is completely arbitrary. In fact, any given class is equally likely to receive any given rank on a given year (two classes may not receive the same rank). A certain professor chooses to remember only the highest ranking his class has ever gotten.

(a) Find the transition probabilities of the Markov chain that models the ranking that the professor remembers.

(b) Find the recurrent and the transient states.

(c) Find the expected number of years for the professor to achieve the highest ranking given that in the first year he achieved the $i$th ranking.
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「教授只记住自己课程拿到过的最好排名」这道题其实是「记录过程（record process）」与「吸收期望时间」的温柔开场。第一性原理：记 $X_n$ 为教授在 $[1,m]$ 内记得的最好名次，若当年排名比既往最好更靠前，$X_n$ 就会上涨，否则保持不动——因此状态只能在「变好」方向单调攀升，一旦触及 $1$（绝对最好）便永远停在 1，$1$ 就是一个吸收态；转移概率由「新的最好排名恰等于 $j$」的均匀概率给出。命名模板：把这类「只看历史极值」的统计量称作记录/极值过程，它天然单调，链条是有向吸收链。跨课程（排序算法 / CLRS）：这与「线性扫一遍选出最大」同构，只是这里每一步都以概率更新记录；(c) 问要求的期望年数正是首次吸收/首达时间。反例：若排名允许并列或并非均匀，转移概率就不再有干净的闭式、链也未必逐级单调——均匀独立排名的假设是整套计算成立的地基。

<!-- ===== PDF p405 ===== -->

<span style="color:#7f8c8d;">§7.4 / §7.5　第 7 章习题区（Problems）续页。本页含两题：顶部一段为 **Problem 29** 的题干（任给一组转移概率确定的马尔可夫链与稳态概率 $\pi_1,\pi_2,\pi_3,\pi_4$，问若干次转移后回到状态 1 的概率、期望与方差、(a)(b)(c) 各问）；随后以「Problem … for Problem 30」交叉引用承接，转入 **Problem 30**（关于暂态（transient）/常返（recurrent）状态、常返类（recurrent classes）与稳态概率、基于图 7.25（Figure 7.25）给出的马尔可夫链，(a)(b)(c) 各问，其 (d)(e) 在下一页）。本页两题的编号标签在源 OCR/合并过程中缺失，现按第 7 章习题区连续编号（28→29→30）复原为 Problem 29 与 Problem 30，题面本身未变。本题区按规范要求，习题题干与带 `*` 题的英文 Solution 一律保留英文原文。</span>

---

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 关于「回到状态 1 所需转移次数」的两个数字——期望与方差——其实是用第 7 章的词汇重新包装第 1、2 章的回归时间统计。第一性原理：若 $X_0=1$，记 $T$ 为第一次回到状态 $1$ 的时刻，则期望 $E[T]$ 恰是状态 1 的平均返回时间/循环时间 $t_1$，它与稳态概率的倒数 $\pi_1^{-1}$ 精确相连——这正是 Problem 34、(c) 问与 §7.4 会反复出现的「平均循环时间＝稳态概率倒数（$t_s=1/\pi_s$）」定理；方差则要求二阶返回时间的矩。命名模板：mean recurrence time（平均返回时间）= 从自己出发回到自己的期望步数，别与 first passage time（首达时间，从一个状态首次到达另一状态）混淆。跨课程（随机过程 / 遍历理论）：对取平均返回时间处的「$\pi_1=1/6$」直读 $E[T]=6$，体现长程频率解释；这也与 Kac 定理（平均返回时间恰为稳态概率倒数）相合。反例：(b) 问问方差就说明「只有期望不够」——一条链可稳定地每 6 步回一次（方差极小），也可能忽而 1 步忽而 20 步地摆动（方差很大），二者期望相同但风险天差地别。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 30 的 (d)(e) 问把「从稳态观察」与「从暂态出发」两种设定并置，考察的是同一枚硬币的两面。第一性原理：(d) 让你在稳态下开拍，这时初始状态的边际分布就是 $\pi$，又要条件化「第一次转移使状态 +1」，本质是求两个事件「$X_1=X_0+1$」与「$X_0=2$」之间的条件概率，用贝叶斯/联合概率反推即可，不必重跑整条链；(e) 则从暂态 $4$ 出发，问「最终落入哪个常返类」及各常返类的吸收概率、以及进入常返态前的期望步数——这正是 §7.4 吸收概率与吸收期望时间一体两面的设问。命名模板：absorbing probability（吸收概率）回答「落到哪块墊底」，expected time to absorption（吸收期望时间）回答「要等多久」。跨课程（随机游走 / 排队首达）：这是「从任意起点、进入吸收集合的时间与去处」这一通用随机过程问题的最简载体，后续连续时间链、扩散与停时理论都以它为第一性图景。反例：若从暂态出发却对「最终会否进任何常返类」心存侥幸，须知暂态集的随机游走终会以概率 1 落入某个常返类——「永不落定」的概率为零。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 吸收概率的唯一性证明用上了「收缩映射（contraction）」这套极具代表性的手法，值得读第二遍。第一性原理：设两组解 $a_i$、$\bar a_i$，它们的差 $\delta_i$ 满足同一条齐次方程 $\delta_i=\sum_{j\notin A}P_{ij}\delta_j$；反复代入 $m$ 次后，$\delta_i$ 等于「在 $m$ 步内一直待在暂态集」的概率（这是 $<1$ 的因子 $\beta$）乘上 $\max|\delta_j|$，于是 $\max|\delta_j|\le\beta\max|\delta_j|$，只能 $\max=0$，唯一性得证。命名模板：把「代入 $m$ 次后多出一个小因子 $\beta<1$」称作收缩——每次迭代都让某个当量缩小，是证明线性系统解唯一的万金油。跨课程（数值线性代数 / 18.06）：这里矩阵 $P_{\text{transient}}$ 的谱半径 $<1$（所以幂次收敛于零矩阵），$\delta=P\delta$ 恰恰迫使 $\delta=0$；这正是判断矩阵「$I-P$ 是否可逆」的同款判据（$(I-P)^{-1}$ 即命中吸收态前的期望逗留时间）。反例：若暂态子链不是「必被吸收」，而存在闭的非常返子集，则 $m$ 步内永留在暂态集并非必然、$\beta<1$ 不再自动成立，唯一性便崩坏——「暂态 ⇔ 必被吸收」是整套论证的地基。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 多个常返类让「极限」与「稳态」脱钩，本解的关键是把每个常返类都“压缩”成一个吸收态。第一性原理：若 $i,j$ 属不同常返类则从未可达、$r_{ij}(n)\equiv0$；同类的取类内稳态；而暂态出发到 $j$ 的极限＝「先吸收到 $j$ 所在类」的概率 ×「类内到 $j$」的条件稳态——因子化反映了「暂态只决定"落到哪类"，类内分布由该类自己遍历」的分层结构。命名模板：把这一类比作「漏斗+水池」：暂态集是漏斗把概率分流到各常返类水池，每个池内各自混合均匀。跨课程（线性代数 / 谱理论）：多类时转移矩阵 $P$ 有多于一个「1」特征根，极限 $\lim_n P^n$ 不再是单一秩一的投影，而退化为每个常返类各一个投影之和——Levinson 分解 / Perron–Frobenius 在此给出可分解结构。反例：若类不是非周期的，$r_{ij}(n)$ 会随时间震荡、极限根本不存在——「每类都要非周期」的假设与单类情形同样关键，否则连收敛性都保证不了。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 平均首达时间（mean first passage time）的方程 $t_i=1+\sum_j p_{ij}\,t_j$、$t_s=0$ 是「首步方程（first-step equations）」的旗舰应用，值得背下推导骨架。第一性原理：从任一 $i\neq s$ 出发，第一跳必花 1 步，之后要么已在 $s$（$t_j$ 为 $0$），要么从新状态 $j$ 重新按同一期望继续——把第一步单独拆出便得 $t_i=1+\sum_j p_{ij}t_j$；方程是线性的，解的存在唯一性再一次靠「从暂态必达 $s$」保证。命名模板：first-step equation（首步方程）的名字直白——「对第一步条件化」这一招，就能把无数首达/吸收时间的期望算出来，不必纠缠路径细节。跨课程（随机游走 / 18.06 泊松方程）：这正是线性方程组 $(I-P_{T})t=\mathbf 1$，其中 $t$ 可理解为「拉普拉斯算子 $I-P$ 的 Green 函数」的期望版本；与随机微分方程里求解「过定界的期望停时」用的是同一套线性代数。反例：若 $s$ 不是常返而只是暂态，那么从 $s$ 出发未必能回头、方程组可能无解或解出 $+\infty$——首达期望「有限且唯一」的前提是目标态常返。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题把「稳态概率」翻译成「循环切分后的访问计数」，是理解 $t_s=1/\pi_s$ 的最直观入口。第一性原理：把轨迹在每次访问 $s$ 处切开，两个相邻 $s$ 之间构成一个独立「循环」；$p_i$ 定义为一个循环内访问 $i$ 的平均次数，$t_s$ 则是循环长度。于是 $\pi_i=p_i/t_s$ 自然成立：长程访问 $i$ 的比例＝每个循环里访问 $i$ 的次数 ÷ 循环长度。命名模板：cycle（循环）指「回到 $s$ 为止的一段」，recurrence time（循环时间）即循环的期望长度；这是「更新理论（renewal theory）」的最小模型。跨课程（随机游走 / 组合计数）：这正是「每个 $s$ 访问点都是更新点、各循环独立同分布」的更新论证，Kac 定理 $E_s[\text{首次返回}]=1/\pi_s$ 在此被一步一步重新证明；而把总频率写成「分子除以分母」的套路，也直接舀进了大数定律的证明（Problem 35）。反例：(d)(e) 问要证唯一性与非负条件，说明「满足平衡方程且和为 1」的分布至多一个且必存在——若忽略暂态态上 $\pi_i=0$ 的强制条件，可能误把暂态配非零权重，违背稳态定义。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 35 末尾那个「$Y_n\to0$ 逐点成立而 $E[Y_n]\equiv1$」的例子，是全书对「期望收敛」与「依概率收敛」之鸿沟的当头一棒。第一性原理：$Y_n=n$（当 $X<1/n$）、否则为 $0$，对几乎所有样本 $Y_n$ 最终恒为 0（因为 $X>0$），但期望 $E[Y_n]=(1/n)\cdot n=1$ 恒定不变——逐点极限与期望极限可以完全不同，二者根本是两个叠加次序。命名模板：把这种「逐点收敛到 0、期望却永远等于 1」的序列称作「爱心小尖峰（spike）」，它本质是个可积性不足的「移动高原」；由此而生的教训是：不能拿「$E[V_n]/n\to\pi_s$」当作「$V_n/n\to\pi_s$」的论据。跨课程（实分析 / 测度论）：这正是 Fatou 引理和 Lebesgue 控制收敛定理存在的理由——「$\lim\int\ne\int\lim$」除非有控制或单调性；而 (a)(b) 问本身能成立，靠的是逐条轨迹上的模进（$Y_k\le n\lt Y_{k+1}$）与强数定律，压根没碰期望。反例：若试图用「期望收敛＋马尔可夫性质」去硬推，只会被这个反例打脸——正确的通路是逐轨迹的收敛论证。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道「$m$ 台机器一台修理工」题告诉我们对连续时间马尔可夫链（CTMC），真正能方程化的对象是「发生跳变的事件」而不是时间本身。第一性原理：处于状态 $i$（$i$ 台停机）时，下一事件的等待时间是指数分布的——任一运行机器以速率 $\mu$ 坏掉（$i$ 台运行时，总坏率 $i\mu$）、修理工以速率 $\lambda$ 修好一台——两个独立的指数竞争，最小值仍是指数、参数相加，于是链在整数状态 $0,\ldots,m$ 上以速率 $\mu_i$、$\lambda_i$ 作生灭跳变，稳态由平衡方程微分式 $\pi_i(\lambda_i+\mu_i)=\pi_{i-1}\lambda_{i-1}+\pi_{i+1}\mu_{i+1}$ 刻画。命名模板：把每个状态上的「总离出速率＝速率参数之和」称作转移速率（transition rate）模型，它把「连续时间」翻译成「事件驱动的跳变」。跨课程（排队论 M/M/m / 6.041）：这就是多服务器排队系统的对偶（修理站当服务员），$m$ 台机器共享一名修理工对应「机器数有限、服务员一个」的有限源模型。「无运行机器」与「期望运行台数」都是由稳态分布直接取出的两个指标。反例：若修理工可同时修多台、或机器非指数寿命，链将失去马尔可夫性——指数（无记忆）假设是 CTMC 能运转的根本。

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 37（空格出租车、Poisson 到达与顾客等待）**</span>

Empty taxis pass by a street corner at a Poisson rate of two per minute
and pick up a passenger if one is waiting there. Passengers arrive at the street corner
at a Poisson rate of one per minute and wait for a taxi only if there are less than four
persons waiting; otherwise they leave and never return. Penelope arrives at the street
corner at a given time. Find her expected waiting time, given that she joins the queue.
Assume that the process is in steady-state.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 空格出租车题是「两个独立泊松过程相互耦合」的精致小品，解答要诀在于把「等待时长」翻译成「两个随机时间的竞争」。第一性原理：出租车以速率 $2$/分泊松到达，乘客以速率 $1$/分到达；若永远允许无限排队，顾客的期望等待时间就等于「下一辆出租车到来（Exp(2)）的期望」加「自己前面乘客造成的前置量」，而「等少于四人」的截断（超过四人不排队）则让系统成为一个有限容量撾列。命名模板：把「（出租车）到 /（乘客）到」抬高看成两个时钟的赛跑，稳态下顾客加入时队列长分布已知，等待时长为「排空自己前面 $k$ 人的服务时间」加上等待下一辆空车——服务时间仍因无记忆而指数。跨课程（排队论 M/M/1 与 Erlang 损失 / 6.041）：这与电话交换的 Erlang-B（无等待、直接阻塞）或有限等待撾列同源；难点是「顾客要判断加不加队」，而判断本身依赖当下队列长度，故要用稳态分布条件化。反例：若出租车到达速率与乘客到达速率之比偏离稳态稳定性条件（如服务强度 $\ge1$），队列在稳态上根本不收敛、期望等待时间发散——「假设处于稳态」就是稳定性的预设前提。

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 38（多个用户共享计算机系统的马尔可夫链建模）**</span>

There are $m$ users who share a computer system. Each user alternates between "thinking" intervals whose durations are independent exponentially distributed with parameter $\lambda$, and an "active" mode that starts by submitting a service request. The server can only serve one request at a time, and will serve a request completely before serving other requests. The service times of different requests are independent exponentially distributed random variables with parameter $\mu$, and also independent of the thinking times of the users. Construct a Markov chain model and derive the steady-state distribution of the number of pending requests, including the one presently served, if any.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 多用户共享系统的建模要诀是「把 2 型连续时间马尔可夫链合成一个状态计数器」。第一性原理：每个用户是「思考（Exp($\lambda$)) ↔ 活跃/提交请求（Exp($\mu$)）」的双态 CTMC；把所有用户合并后，状态只取「待处理请求总数 $i$（含正在服务的那个）」即可刻画——服务速率是 $\mu$（单服务员，服务中的那台），而「有人从思考转入活跃」的总速率是 $(m-i)\lambda$（还有 $m-i$ 人闲着）。命名模板：把「每个用户独立两态、合并成一个"活跃数"状态」称作合并/聚合（aggregation），它把 $2^m$ 个微观态压缩成 $m+1$ 个宏观计数。跨课程（排队论 M/M/1 有限源 / 排队网络）：这正是「有限源（finite-population）M/M/1」排队模型，又称机器修理模型/Engset、或闭杰克逊网络的一块砖，庄闲交替分别对应"思考"与"服务"。稳态由平衡方程 $\pi_i\,[(m-i)\lambda+\mu]=\pi_{i-1}(m-i+1)\lambda+\pi_{i+1}\mu$ 解出。反例：若服务员可并发处理、或思考时间非指数，则状态必须记到每个用户的完整相位，$m+1$ 计数态不再充分还原真实过程——马尔可夫性又一次挂在"无记忆"上。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 39 把「连续时间马尔可夫链的稳态」与「嵌入链稳态」用一条干净的条件桥接起来：当各状态转移速率相等（$v_i\equiv v$）时，二者一致。第一性原理：平衡方程左边 $q_{jk}=v\,p_{jk}$（$v$ 是离开每个状态的公共速率），左右若能约去公共因子 $v$，剩下的正是嵌入链（只记跳变序列、不计逗留时间）的平衡方程——所以当且仅当「每个状态的速率都一样」时，嵌入链不管每步等待多久都不改变稳态占比，比例完全继承。命名模板：embedded Markov chain（嵌入链）指「只保留跳变：$X_0,X_1,X_2,\ldots$」，把连续时间里的等待间隔丢掉；其转移概率 $p_{jk}=\frac{q_{jk}}{v_j}$。跨课程（排队论 / 泊松过程）：$v_i$ 全相等时跳变时刻构成速率为 $v$ 的泊松过程（(a) 问），这正是「单位速率链可作为点过程采样」的反面；而 $v_i$ 不等时稳态会向「少离开」的慢速状态倾斜，嵌入链便不再和原链同分布。反例：若某状态 $i$ 的 $v_i$ 远小于别的状态，原链会逗留很久、该状态的长期占比被放大，而嵌入链只看跳变占比、忽略了逗留时间——这正是二者「通常不等、仅在同速率时相等」的根源。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一段「概率论是数学、统计学是艺术」的对照，是全书方法论立场的正式声明。第一性原理：概率论里模型完全给死、答案唯一（尽管求起来费劲）；统计学里模型带未知量，同一个问题可以有多个都说得通的答案，选择方法是一桩「在若干合理方法里挑一个」的判断而非推导。命名模板：把「方法没有唯一最优解」对应到优化里的非良定（ill-posed）、把「挑方法」对应到 model selection（模型选择）。跨课程（机器学习 / 6.036）：这里预告的正是机器学习的日常——「性能保证、既往经验、共识」就是验证集、先验信念与社区惯例的另一种叫法；而「随着数据无限估计趋于正确」这一条可取性质，正是统计估计的相合性（consistency），也是正则化/伯方差权衡的底色。反例：若误把统计学当成纯粹概率演算，面对同一历史收益率你仍会对「该用均值还是中位数」这样的问题无言以对——因为答案不在公理里，而在你愿意作的假设里。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 贝叶斯与频率派之争的落点，最终都系在"如何把先验藏起来"上。第一性原理：先验不是玄学，而是把"模型与参数都是随机的"这一共同前提、以及我们对取值域的全部既有信念，浓缩进 $p_\Theta(\theta)$ 这一个因子；观测到数据后，贝叶斯准则只是把先验当"权重"拿似然去更新它。命名模板：prior（先验）直译"在前"、posterior（后验）即"随后"——一个取数据之先、一个取数据之后，正好对应乘积里先后两个因子的位置。跨课程（CS229/6.036 机器学习）：对 MAP 目标取负对数，-$\,\log f_\Theta$ 就成了参数的惩罚项——若先验取零均值高斯，得到的正是岭回归（ridge）、即 $\ell_2$ 正则化，"贝叶斯"与"正则化"在此是同一枚硬币的两面。反例：若干脆不要先验、只看似然（经典极大似然），高维或数据稀少时估计会随噪声过拟合地乱跳；而先验一旦定错方向（均值严重偏离真实），即便数据充足后验也会被拽向错误一侧——所以先验既是免费的正则化，也是你必须诚实交代的假设。

---

<span style="color:#c0392b;">**模型推断与变量推断（Model versus Variable Inference）**</span>

统计推断（statistical inference）的应用往往属于两种类型。在**模型推断（model inference）**中，所研究的对象是一个真实的现象或过程，而对我们而言，它——
<!-- ===== PDF p418 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

> <span style="color:#7f8c8d;">本章（书页 p408 起）开篇关于模型推断（model inference，针对模型结构/参数的构造与验证）与变量推断（variable inference，针对未知变量取值的估计）之区别的导言论述延续至本页。本页承接前述「模型推断」段的中段，随后给出 **Example 8.1**（有噪信道，A Noisy Channel）、小节标题「统计推断问题的粗略分类」（A Rough Classification of Statistical Inference Problems）及对估计（estimation）问题的引述。</span>

……希望基于现有数据来构造或验证一个模型（model），例如行星是否遵循椭圆轨道（elliptical trajectories）？这样的模型随后可用来对未来作出预测（predictions），或用来推断某些隐藏的根本原因。而在变量推断（variable inference）中，我们希望利用若干相关的、可能含噪的信息来估计一个或多个未知变量的取值，例如给定几次 GPS 读数，我的当前位置是哪里？

模型推断与变量推断之间的区别并不泾渭分明；例如，通过用一组变量（variables）来描述一个模型，我们可以把模型推断问题转化为变量推断问题。不管怎样，在后续我们将不再强调这一区别，因为同样的方法论原理适用于这两类推断。

在某些应用中，模型推断与变量推断问题可能会同时出现。例如，我们可能收集一些初始数据，用它们来构建一个模型，然后再用该模型对某些变量的取值作出推断。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「模型推断」对「变量推断」的二分，本质上刻画的是「未知物是函数/结构」还是「未知物是取值」两条不同的路子。第一性原理：当未知量是可以无限描述的（如一个函数 $g$），它就是模型问题、要作函数估计（回归）；当未知量是有限个实值坐标（如位置 $(\theta_1,\theta_2)$），它就是变量问题、要作参数估计。命名模板：model inference（模型推断）答「世界长什么样」，variable inference（变量推断）答「眼下在哪」。跨课程（机器学习 / 6.036）：这正是「system identification（系统辨识）↔ 状态估计（state estimation）」的分类，也用「参数化 / 非参数化（parametric/nonparametric）」区分——考 Cur：例 8.1 用导频估计 $\alpha$（模型）、用已知 $\alpha$ 判 $S_i$（变量）。反例：两者实为连续谱的两端，例如「估计一个模型参数 $\alpha$」介于其间，作者也明言后续不再强调其界限——分类是教学工具，不是硬边界。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.1（有噪信道，A Noisy Channel）。**</span>

一台发射机（transmitter）发送一串二进制消息 $S_i \in \{0, 1\}$，接收机（receiver）观测到

```math
X_i = \alpha S_i + W_i, \qquad i = 1, \ldots, n,
```

其中 $W_i$ 是零均值（zero mean）正态随机变量（normal random variables），用于刻画信道噪声（channel noise），而 $\alpha$ 是一个标量，表示信道衰减（channel attenuation）。在模型推断（model inference）的设定下，$\alpha$ 是未知的。发射机发送一个由一串值已知的消息构成的导频信号（pilot signal $S_1, \ldots, S_n$），其取值接收机已知。基于观测 $X_1, \ldots, X_n$，接收机希望估计 $\alpha$ 的值，即为信道构建一个模型。

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 本例观测方程（此处写作 $X_i = \alpha S_i + W_i$）在源 OCR 中被打散（仅余二值消息 $S_i \in \{a, I\}$ 与附录式 "$i=1,\ldots,n$" 的碎片），正文亦以 "a"/"a" 混排表示 $\alpha$；上方传动机方程按原书 Noisy Channel 例的权威语义还原，并以 $\alpha$ 规范成文，未臆造数值。</span>

或者，在变量推断（variable inference）的设定下，$\alpha$ 假定为已知（可能如上述那样，已通过导频信号推断出来）。接收机观测到 $X_1, \ldots, X_n$，并希望推断 $S_1, \ldots, S_n$ 的值。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 8.1 的信道模型 $X_i=\alpha S_i+W_i$ 是全书最常用的一副"接插件"：噪声 $W_i$ 贴着信号线性叠加。第一性原理：估计 $\alpha$ 的本质，是在由导频 $S_i$ 张成的那条直线（一维子空间）上，把观测向量 $X$ 的投影找出来——最小二乘解正是"残差与子空间正交"的那一点。命名模板：least squares（最小二乘）得名于"让误差平方和 $\sum_i(X_i-\alpha S_i)^2$ 最小"，平方是为了让目标处处可导、也便于配柯西不等式。跨课程（18.06 线性代数）：若 $W_i$ 是 i.i.d. 零均值噪声，则最优 $\hat\alpha=\dfrac{\sum_i S_iX_i}{\sum_i S_i^2}$，即把 $X$ 正交投影到 $\mathrm{span}(S)$ 拿到的系数，正是法方程（normal equations）的解。反例：若所有导频 $S_i$ 相同（激励不张开方向），则 $\sum_iS_i^2$ 退化、分母可趋于零，投影病态且方差爆炸——这正是通信里"激励要足够丰富（sufficient excitation）"理念的雏形。

---

<span style="color:#c0392b;">**统计推断问题的粗略分类（A Rough Classification of Statistical Inference Problems）**</span>

我们在此描述几类不同的推断问题。在估计问题（estimation problem）中，一个模型除一个未知的、可能为多维的参数 $\theta$ 外被完全给定，我们希望估计该参数。这个参数既可以看作一个随机变量（random variable，贝叶斯方法，Bayesian approach），也可以看作一个未知常数（classical approach，经典方法）。通常的目标是得到一个在某种意义下接近真实值的 $\theta$ 估计。例如：

(a) 在 Example 8.1 的有噪传输问题中，利用导频序列（pilot sequence）与观测来估计 $\alpha$。

(b) 利用民意调查（polling）数据，估计选民总体中偏好候选人 A 胜过候选人 B 的比例。

(c) 基于历史股票市场数据，估计某只股票每日价格变动的均值（mean）与方差（variance）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这段把推断问题粗分成「估计」与「假设检验」两大类，是本章路线的预览清单。第一性原理：估计问题中参数是连续域（如 $\alpha$、比例、均值/方差），要报一个数；假设检验问题中参数只在有限个离散假设里（$S_i$ 是 0 还是 1、图里有没有人），要做一个「对/错」的判决。命名模板：estimation（估计）＝「多大？」、hypothesis testing（检验）＝「是哪个？」，二者都用后验分布但输出类型不同。跨课程（机器学习分类/回归 / 6.036）：估计≈回归、检验≈二分类，这是把「预测类型」从建模第一步就区分开的标准划分；而 (b) 的民意测验估计比例、正是比例参数 $p$ 的换算。反例：本段刻意不提「显著性检验（significance testing）」，它是非贝叶斯框架下的离岸概念，要到第 9 章经典假设检验才登场——别把本章的贝叶斯二值检验与「$p$-value/显著性」混为一谈。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「非参数化」这个标签很容易被误读成「没有参数」，更准确的说法是「参数数目不固定、且会随数据规模增长而无界」。第一性原理：把 $g$ 看成「每个点都有独立自由度」的函数，就等价于拥有无限多个待估参数；而本章所有方法（MAP、LMS、线性 LMS）都预设未知量能用有限个标量压缩编码，当未知物是函数 $g$ 时，后验公式在操作层面便不再适用。命名模板：parametric（参数化）指「模型形状完全给定、只剩有限个标量未知」，nonparametric 的 non- 是「无限维参数意义」的反面。跨课程（机器学习 / 6.036）：这正是 kernel methods 与神经网络「模型容量随数据自适应」的由来——当预测目标是函数而非单个数时，就跳出了「有限维参数向量」的舒适区。反例：作者明言此类问题超纲，但并非不可解，局部平均或核回归照样能逼近 $g$；只是它们没有固定维度的参数向量、无法套用本章的后验公式——这提醒我们「贝叶斯方法好用与否」与「未知量维数是否有限」高度相关，维数一旦发散，共轭与闭式解都无从谈起。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「贝叶斯准则的四种版本」看起来是四个公式，实则是把「四个离散/连续组合」硬塞进同一个骨架。第一性原理：无论 $\Theta$ 与 $X$ 是离散还是连续，后验都恒为「先验 × 似然 ÷ 分母」，唯一差别是 PMF（求和 $\sum_{\theta'}$）还是 PDF（积分 $\int_{\theta'}d\theta'$）——(离散,离散) 版就是第 1 章那个最基础的贝叶斯准则，其余三版只是在两个轴上各做一次「求和换积分」的翻译。命名模板：把这四式统称「连续版贝叶斯准则」，本质上是用密度/质量函数把连续参数并入同一个除法结构。跨课程（实分析 / 概率论）：规整性（正则性）要求分母那个和/积分为有限正数，一旦 $\int f_\Theta(\theta')f_{X|\Theta}(x|\theta')d\theta'=0$（比如先验与观测支撑不交叠），后验无定义——这提醒我们「支撑（support）」匹配是贝叶斯准则可用性的隐藏前提。反例：当 $\Theta$ 连续、$X$ 也连续时仍可对 $\theta$ 求导取极大（MAP），但「最大密度」与「众数」在连续意义下都是密度值而非概率值，切勿把某个区间的高密度误当作该区间的高概率（二者隔着积分测度）。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 后验「当 $\theta < x$ 或 $\theta > 1$ 时为零」这一行，常常比整页的密度公式更值钱——它说的是：一次迟到 $x$ 就足以把 $\theta$ 的一切小于 $x$ 的候选直接排除。第一性原理：参数 $\theta$ 是 $[0,X]$ 的上界，而观测 $X \le \theta$，所以「$\theta \ge X$」是这个模型里刻进模型的硬约束（structural constraint），与概率无关，反映的是支撑（support）结构本身携带的信息。命名模板：把「观测把参数可能域切掉一块」称作支撑截断（support truncation），是贝叶斯里先验与似然支撑不交叠时的必然结果。跨课程（实分析 / 测度论）：后验在 $\theta\lt x$ 处为 $0$，本质是「先验 $[0,1]$ 与似然支撑 $[x,\theta]$ 交叠后剩 $[x,1]$」这一交集在起作用；这也是为什么 Rényi/实变里要强调 density 的支撑——支撑不同会影响积分区域而不只影响函数值。反例：不要被「一次观测排除掉所有 $\theta\lt x$」误导成「观测越极端知识越多」——被排除的只是 $\theta$ 的上界方向，正确结论是 $\max$ 观测（订单统计）成了这条链的天然充分统计量，多看几次到的仍是同一个下缘截断，只是截得更紧。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「$n$ 次迟到压缩成 $\bar{x}=\max\{x_i\}$ 这一个数」不是偷懒，而是抓住了充分统计量（sufficient statistic）的雏形。第一性原理：在 $X_i\mid\Theta=\theta$ 均匀于 $[0,\theta]$ 的模型里，似然 $\prod_i f_{X_i\mid\Theta}(x_i\mid\theta) = \theta^{-n}\mathbf 1\{\theta \ge \max_i x_i\}$ 只透过 $\max$ 依赖数据——小于 $\max$ 的观测一次也没被直接使用，因为它们能提供的信息都已包含在「$\theta$ 至少要大过最大的那次」里。命名模板：sufficient（充分）意为「只要这一个函数，就足以不减损信息地决定后验」，其余数据是冗余的。跨课程（概率论 / 统计充分性原理，Berger）：由 Neyman 因子分解定理可见，当似然能写成「$(x)$ 的部分」×「含 $\theta$ 的部分」而含 $\theta$ 的部分仅经 $T(x)$ 依赖 $x$ 的乘积形式时，$T$ 就是充分统计量——本例 $T=\max$，密度因子恰好不漏 $\theta$。反例：充分不是「唯一的」取舍——$\{X_{(1)},\dots,X_{(n)}\}$ 全体也无损，只有像 $\max$ 这种「低维压缩」才谈得上数据约简；若观测自身不独立或支撑不与 $\theta$ 挂钩（如高斯噪声），充分统计量就不再是 $\max$，套用本例会丢掉平方和项里的信息。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 归一化常数 $c(x)$ 是贝叶斯里最容易被跳过、却最值得读懂的一步。第一性原理：后验＝先验×似然／（对分母积分），分子决定后验"长什么形"，分母 $c(x)$ 只负责把总质量凑回 1——所以算后验时常盯着分子、把常量当配角；但判断哪个观测更"有信息"，看的是分母那个积分收缩到多尖。命名模板：normalizing constant（归一化常数）取义"把概率质量规范化回 1"。跨课程（概率论/实分析）：本例 $\Theta$ 的先验取了均匀分布，可它配非均匀似然并不共轭，致使 $f_{\Theta|X}\propto 1/\theta$、积出 $\lvert\log x\rvert$；若换成 Beta 先验（见 Example 8.4），分母会闭合成 Beta 函数，这就是"共轭让积分能闭式出解"的用意。反例：若不归一化只比分子大小，后验的绝对水平失效，无法用它求期望或区间、算出的概率还会荒谬地不求和 1；而 $n$ 次观测后 $c(x)$ 把后验压向 $x=\max$ 附近的尖峰，正是"数据越多、估计越收敛"的一致性直觉。
<!-- ===== PDF p423 ===== -->
<span style="color:#c0392b;">**第八章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**§8.1　贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）（续）**</span>

> <span style="color:#7f8c8d;">本页为书页 415，承接上一页 §8.1 的正文，转入一个新的例题 **Example 8.3——正态随机变量公共均值的推断**。例题在本页起笔并推演至分子配平方化简与 $m$、$v$ 的表达式，其「后验为正态分布、均值为 $m$、方差为 $v$」的结论收尾出现在下一页。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.3．正态随机变量公共均值的推断（Inference of a Common Mean of Normal Random Variables）**</span>

我们观测到一族随机变量 $X = (X_1, \ldots, X_n)$，它们具有一个未知的公共均值（common mean），我们希望推断出该均值之值。我们假定：在公共均值取值给定的条件下，这些 $X_i$ 服从正态分布（normal）且相互独立（independent），其方差（variances）$\sigma_1^2, \ldots, \sigma_n^2$ 已知。在这种问题的贝叶斯做法中，我们把公共均值建模为一个随机变量 $\Theta$，并给定一个先验分布（prior）。为具体起见，我们假设该先验为正态先验（normal prior），其均值 $X_0$ 与方差 $\sigma_0^2$ 均已知。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「按 $1/\sigma^2$ 加权」这句话值得单独拆开品——它把"置信"翻译成了"精度"。第一性原理：正态后验均值 $m=\dfrac{\sum_i x_i/\sigma_i^2}{\sum_i 1/\sigma_i^2}$ 的分母是"精度（precision）"之和，恰好对应方差 $\sigma^2$ 的倒数 $1/\sigma^2$：观测方差越小、权重越大，这正符合"信息越多越可信"。命名模板：precision（精度）被许多人记成"置信"，但其实特指 $1/\sigma^2$，它让"贝叶斯合并"成了一台按精度配重的加法器。跨课程（信号处理 / 18.065）：把式中的 $x_i$ 换成测量、$\sigma_i^2$ 换成噪声方差，这正是加权最小二乘（WLS）的最优解——最优权重恰是"误差方差倒数"，这是高斯-马尔可夫定理的贝叶斯话版本。反例：权重倒数是建在多观测**独立**之上的；若 $X_i$ 共享未知的系统偏差（含共同的 $W$ 项），按 $1/\sigma_i^2$ 加权会高估相互独立程度、把共享部分当成多重独立的证据，得到过度自信的 $m$——此时须先对协方差结构建矩，权重也得换成协方差逆阵的多维推广。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 8.3 的"后验与先验同族、可递归更新"常被轻视，却正是贝叶斯计算史上的转折点。第一性原理：把上一步的后验直接当作本步的先验，新观测只做一次精度加权合并——因为正态族对"乘法＋归一化"是封闭的（closed），后验仍是正态，只需均值与方差两张卡就能无损携带全部信息。命名模板：recursive（递归）指"新后验＝旧后验与新似然的单次融合"，不必重放全部历史。跨课程（信号处理/卡尔曼滤波，18.065 亦触及）：这正是离散卡尔曼滤波（Kalman filter）那套"按精度 $1/\sigma^2$ 合并新测量"的迭代——先验精度加似然精度得后验精度，后验均值是各自的精度加权和，与正文 $m$、$v$ 的表达式一一对应。反例：若各测量方差 $\sigma_i^2$ 普遍偏小，后验方差 $v=\big(\sum_i1/\sigma_i^2\big)^{-1}$ 会随 $n$ 大约按 $1/\sqrt{n}$ 收紧到 0——这是好消息；但若"独立、同方差、正态"的模型假设本身是错的，递归就会越自信地收敛到错误的均值上，即所谓"过度自信的渐进误差"。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「$\alpha=\beta=1$」看似朴素，落到后验却是「$k+1$」里那个「$+1$」的来历——这一步要揭开的正是均匀先验＝伪计数（pseudo-count）。第一性原理：后验 Beta 参数由 $\alpha'=k+\alpha$、$\beta'=n-k+\beta$ 给出，故先验参数 $\alpha,\beta$ 等价于「事先假定看过 $\alpha$ 次成功、$\beta$ 次失败」：$(\alpha,\beta)=(1,1)$ 就等于「预先看见一次正面与一次反面」，后验 $k+1$ 与 $n-k+1$ 的加一因此不是魔数而是一种先验注入。命名模板：把先验当作"虚拟样本（virtual samples）"是理解共轭最快捷的直觉，均匀先验的伪计数就是各一颗。跨课程（机器学习 / 概率论，Laplace）：取期望 $E[\Theta\mid X=k]=\frac{k+1}{n+2}$ 正是名闻天下的拉普拉斯后继率（rule of succession）——用经验成功比 $(k+1)/(n+2)$ 去估计下一个试次的成功概率，避免了 $k=0$ 时"永远失败"的悖论，也是朴素贝叶斯光滑（Laplace smoothing）的同一数学根。反例：伪计数的大小不是免费的——若数据真的海量（$n$ 很大），固定加一被常数稀释到可忽略；但若改用较大的伪计数（如 $\alpha=\beta=10$ 的强先验）且数据本就稀少，后验会被拖向 $1/2$，这时"以前见过的先例"反而压过了"眼前的数据"，需谨慎取舍先验强度。

Beta 密度经常出现在推断（inference）应用中，并具有一些有趣的性质。尤其是，若 $\Theta$ 具有正整数参数 $\alpha > 0$ 与 $\beta > 0$ 的 Beta 密度，则它的 $m$ 阶矩（$m$th moment）由下式给出：

```math
\mathbb{E}[\Theta^m]
= \int_0^1 \frac{1}{B(\alpha,\beta)}\,\theta^m\,\theta^{\alpha-1}(1-\theta)^{\beta-1}\,d\theta
= \frac{B(\alpha+m,\beta)}{B(\alpha,\beta)}
= \frac{\alpha(\alpha+1)\cdots(\alpha+m-1)}{(\alpha+\beta)(\alpha+\beta+1)\cdots(\alpha+\beta+m-1)}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页内上方 Beta 函数 $B(\alpha,\beta)$ 与积分 $\int_0^1 \theta^{\alpha-1}(1-\theta)^{\beta-1}\,d\theta = \frac{(\alpha-1)!(\beta-1)!}{(\alpha+\beta-1)!}$ 一行的 OCR 被打得极碎（如 `(a(a- +I )!(3((3- -1)!I)!` 等碎片），上方按标准 Beta 函数定义忠实还原其两个等号；各指数与阶乘项由原文「分部积分 / 概率性论证（第 3 章 Problem 30）」的说明核对，未臆造数值。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 共轭（conjugacy）是被名字掩盖的重要机制。第一性原理：Beta 先验配二项似然，分子仍同形为 $\theta^{(k+\alpha-1)}(1-\theta)^{(n-k+\beta-1)}$——与先验同形，故后验仍是 Beta，只是把参数 $\alpha,\beta$ 各累加若干计数；因此"先验"等价于"假设已经见过 $\alpha$ 次成功、$\beta$ 次失败"的经验折进一个分布。命名模板：conjugate（共轭）在拉丁语里意为"联合、配对"——指两个函数相乘后保持同一分布族，故此得名。跨课程（概率论/实分析）：Beta 函数的矩公式 $E[\Theta^m]=\frac{B(\alpha+m,\beta)}{B(\alpha,\beta)}$ 可由分部积分、或第 3 章 Problem 30 的概率性论证得出，落点是阶乘式 $B(\alpha,\beta)=\frac{(\alpha-1)!(\beta-1)!}{(\alpha+\beta-1)!}$，与离散组合计数一脉相承。反例：一旦先验换上非共轭形式（如无界范围的一般密度），后验通常不再能闭式写出、只能退化为数值积分；共轭的"免费午餐"仅在先验与似然确实同族时才成立。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 垃圾邮件过滤是"贝叶斯分类器"的标准样板。第一性原理：要想分错邮件的次数最少，就该把消息判给后验最大的那一类——把每个误分类当作 0-1 损失（0-1 loss），期望损失最小等价于逐点选 $\arg\max_\theta p_{\Theta\mid X}(\theta\mid x)$，与通信里 MAP 同构。命名模板：naive Bayes（朴素贝叶斯）的"朴素"专指"各特征在给定类别下条件独立"这个偷懒却极有效的假设——本例对 $X_1,\dots,X_n$ 恰作了此假设。跨课程（CS229/6.036 机器学习）：这正是一个生成式分类器（generative classifier）——先建模 $p(X\mid\Theta)$ 再反推后验；把每个关键词的出现概率都存成一份表，就是朴素贝叶斯可直接上线的实现。反例：若关键词高度共现（如 "free" 与 "prize" 常同现身），条件独立假设被严重破坏，连乘的似然会把后验挤向极端的 0/1、分类边界失真——实务就用 log-sum-exp 与拉普拉斯平滑（Laplace smoothing）来稳住数值与概率。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 传感器定位例标志着从「单参数」跨进「多参数（二维）贝叶斯」，几何随之从一条线升级成一个平面。第一性原理：参数是向量 $\Theta=(\Theta_1,\Theta_2)$，先验取成两个独立标准正态之积 $\frac{1}{2\pi}e^{-(\theta_1^2+\theta_2^2)/2}$；「第 $i$ 个传感器是否测到」按距离 $d_i(\theta)$ 的指数衰减概率 $e^{-d_i^2(\theta)/2}$，于是后验（先验 × 似然）仍是指数平方和的形式，配平方后为二维高斯——这是「高斯先验 × 高斯/指数似然 → 高斯后验」在二维的又一次共轭胜利。命名模板：把「用一批二分检测结果反推连续位置」称作基于检测/观测的定位（localization），与 GPS 多边定位一脉相承。跨课程（机器人学 / 卡尔曼滤波 / 18.065）：这与「贝叶斯滤波的测量更新步骤」同构，可能在二维由均值向量与协方差矩阵一张图概括；(中心) 每个传感器协方差等价地表达「不确定性在第 $i$ 个观测量方向被收紧」。反例：若某个传感器从未测到（$X_i=0$ 恒成立），它虽不直接贡献信息，却把「未测到」也算进似然，指数因子的方向随之翻转，坐标联合仍闭合但协方差形状会被那些"负观测"塑造——二分类的"否定观测"同样携带着信息。</span>
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> MAP 定义下面那句「分母的计算没有必要」是全书最常被抄错、也最容易被忽略的关键。第一性原理：$\arg\max_\theta p_{\Theta\mid X}(\theta\mid x)$ 只在乎使后验最大的那个 $\theta$，而分母 $\int$（或 $\sum$）对一切 $\theta$ 相同、只是凑满总质量的常量，故最大化时把它约掉不影响 argmax——于是中等规模问题里可直接改求「先验×似然」这一分子。命名模板：把这种"只比分子"的技巧称作最大化时的分母省略（denominator-free maximization），不是"后验的绝对值不重要"，而是"最大点不受均匀拉伸影响"。跨课程（优化 / 机器学习）：这正是"目标函数的单调变换不改最优解"的又一个例证——primal/discriminative 分类里最大化后验与最大化 $\log$ 后验等价；同理极大似然（MLE）就是"先验取均匀"的特例 MAP。反例：分母虽可约，却并非无信息——它正是求区间、算边缘、做归一化的载体（如 Example 8.2 的 $c(x)$）；若比后验的绝对高度（而非 argmax），分母决定绝对尺度，此时不能省。

> <span style="color:#7f8c8d;">[交叉引用] 该性质（MAP 准则最小化错误概率）的表述衔接下方关于「正确决策概率」的讨论，并与「$\Theta$ 离散时相关」的说明相互印证。§8.2，p.421。</span>

让我们通过重温前面一节中的若干例子来说明 MAP 准则。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.3（续）——正态先验、正态观测**</span>

在本例中，$\Theta$ 是一个正态随机变量（normal random variable），均值为 $\theta_0$，方差为 $\sigma_0^2$。我们观测一组随机变量 $X = (X_1, \ldots, X_n)$——在给定 $\Theta$ 取值为 $\theta$ 的条件下，这些随机变量是相互独立（independent）的正态随机变量，均值均为 $\theta$，方差分别为 $\sigma_1^2, \ldots, \sigma_n^2$。我们已经知道，后验概率密度函数（posterior PDF）是正态的。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 末尾那句"连续情形下任何决策的正确概率都为 $0$"带着点悖论味，却是理解 MAP 的两层含义的分水岭。第一性原理：当 $\Theta$ 连续时，$P(\Theta=\hat\theta)=0$ 恒成立，因为单点是零测集；"正确概率为 $0$"并非"准则差劲"，而是"从连续密度里精确命中某一点的概率天然为 $0$"——这时 MAP 的价值不在"命中"，而在把密度质量尽可能集中到峰附近。命名模板：把连续参数的 MAP 读出"最大密度（mode）"而非"命中点"；离散情形才谈得上真正意义的"选对假设的概率"。跨课程（测度论 / 信息论）：连续型的零测单点正是洛贝格测度在实直线上"无原子（atomless）"的表现；与之呼应，连续随机变量的熵因此不含平移到矢量的信息量。反例：若在连续 $\Theta$ 上仍按离散理解"正确概率"，会得出"所有准则都零分"的荒谬结论；正确的做法是把目标改为"落在 $\hat\theta$ 附近 $\epsilon$ 邻域内的概率"——这正是区间估计/边际后验的意义，也是把 MAP 的连续表述改述为逐点最优的原因。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「把比较后验换成比较先验×似然」一句，其实暗藏着把分类拉回"比值阈值"这一最通用的决策语法。第一性原理：因为两类的后验共享同一个归一化分母 $p_X(x)$，所以比较 $P(\Theta=1\mid x)$ 与 $P(\Theta=2\mid x)$ 完全等价于比较 $p_\Theta(1)\prod_i P(x_i\mid1)$ 与 $p_\Theta(2)\prod_i P(x_i\mid2)$——先验与似然的地位对等，各占一个因子。命名模板：likelihood ratio（似然比）指"两颗球相同的似然之比"，若先验相等，判"垃圾"当且仅当似然比超过 1；若令阈值 T 对应先验比，则有通用的"似然比 $\gtrless$ 阈值"判决。跨课程（检测理论 / 信息论，Cover）：这就是 Neyman-Pearson 与 ROC 直线的前提——把任意代价/先验都化约为"在一根似然比轴上取一个阈值"。反例：似然比最优是建立在"每个特征的条件概率都被准确建模"上的；垃圾邮件里关键词常高度相关、也远超 0/1 二值，若仍按独立连乘，似然比会把重叠的"证据"计两遍，阈值就会失真——因此业界用 log-likelihood 加校正、或换用判别性模型（如逻辑回归）绕开特征独立性假设。

> <span style="color:#7f8c8d;">[OCR 标签考] 源 OCR 将本例读作 "Example 8.5 (continued)"，与 §8.1 中同一垃圾邮件例（Example 8.5）的编号一致：本例系在 §8.2 的 MAP 语境下续讲 §8.1 的 Example 8.5，故标为 **Example 8.5（续）**，不再重编号。§8.2 各数值例号已按源 OCR 核对为 8.7（朱丽叶迟到）、8.8（有偏硬币）、8.9（两枚有偏硬币）并与本页分开，故本页不占用 8.7。确切例号以原书为准。</span>

---

<span style="color:#c0392b;">**Point Estimation（点估计）**</span>

在一个估计问题（estimation problem）中，给定观测（observation）$X$ 的取值 $x$，后验分布（posterior distribution）囊括了 $x$ 所提供的全部相关信息。另一方面，我们可能只对某些能概括后验分布性质的量感兴趣。例如，我们可以选取一个点估计（point estimate），即一个单独的数值，用来代表我们对 $\Theta$ 取值所做的最佳猜测。

让我们引入一些与估计相关的概念与术语。为简单起见，我们假定 $\Theta$ 是一维的，但这一套方法同样可推广到其他情形。我们用术语 estimate（估计值）指代我们基于实际观测 $x$ 而选择去报告的那个数值 $\theta$。$\theta$ 的取值通过对观测 $x$ 施加某个函数 $g$ 来确定，即 $\theta = g(x)$。随机变量 $\hat{\Theta} = g(X)$ 被称为估计量（estimator），每当随机变量 $X$ 取到值 $x$ 时，它的实现值恰等于 $g(x)$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> "估计量是随机变量、估计值只是一个数"这组区分，是进入统计后最容易踩的第一道坑。第一性原理：观测 $X$ 在抽取前是随机的，把它放进函数 $g$ 得到的估计量 $\hat\Theta=g(X)$ 因此也是一个随机变量；只有当我们真的拿到 $x$ 的那一刻，它才坍缩成一个具体数值 $g(x)$（估计值）。于是"估计量的性质"（期望、方差、无偏性）都是"重复多次实验会怎样"的长期承诺，而非单次报告的特性。命名模板：estimator（估计量）是"按某种规则运行的函数/机器"，estimate（估计值）是"这台机器在某次输入上的输出"，二者一为实体一为数值，中文常被混读。跨课程（频率派统计 / 概率论）：统计学的"相合、无偏"都是对估计量随 $n$ 增大的极限承诺——只有把 $\hat\Theta$ 当随机变量看，才能定义 $E[(\hat\Theta-\Theta)^2]$ 这类准则。反例：把"本例报告的估计值 $=0.32$"说成"估计量是 $0.32$"是常见错误——一个数谈不上什么方差、更谈不上"误差最小"；这些指标只对随机变量估计量有意义，所以讲最优性时必须回到 $g$ 与 $X$ 的层面。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> MAP 估计「乐观」而条件期望「不乐观」（即 $E[\Theta\mid X]>x$）不是特例，而是两种损失函数对参数形状偏好不同的必然结果。第一性原理：后验 $f\propto 1/\theta$ 在 $\theta\in[x,1]$ 上单调递减，其众数（mode）必钉在左端点 $x$、对"最可能"负责；而条件期望按密度加权平均，被右侧 $\theta$ 的大值拽着走，故落在 $x$ 右侧——同一堆数据喂给"众数"与"加权均值"两个算子，自然得出不同答案。命名模板：把"MAP 贴上数据恰好支持的最大值"称乐观估计，是说它无视了 $\theta$ 实际更大的可能性只挑了边界值；而均值则把全部支撑都算进权重。跨课程（决策理论 / 统计 18.05）：两者分别是最小化 0-1 损失与平方损失的贝叶斯估计，损失函数不同、最优解必然不同；均值在平方误差下无偏而 MAP 通常有偏（本例对大多数 $x$ 都偏低）。反例：不能因为"均值比 MAP 高"就断言均值更准——若 $\theta$ 真值靠近 $x$，MAP 反而更贴；"乐观/悲观"只是曲率方向的说法，真正的好坏要由均方误差或实际代价来定夺，并非固定优劣。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> MAP 估计 $\hat\theta=k/n$ 与条件期望 $(k+1)/(n+2)$ 之间只差一两个伪计数，却写下了一条"收缩到先验均值"的统计恒量。第一性原理：均匀先验等价于各一枚伪计数，故条件期望 $(k+1)/(n+2)$ 是"经验比" $k/n$ 被 $n+2$ 个总频次压向先验均值 $1/2$ 的加一修正；当 $n\to\infty$，分母的 $+2$ 和分子的 $+1$ 都趋向可忽略，两者自然重合。命名模板：把这些"加一"读出 shrink（收缩/缩水），指"先验把小额样本的估计拽向 $1/2$"，等价于拉普拉斯后继率（rule of succession）的再版。跨课程（机器学习 / 正则化）：$(k+1)/(n+2)$ 是"加 $1/\alpha+\beta$ 平滑后在概率空间的正则化"，与岭回归把系数拽向零同构——数据少时先验优势大、数据足则让位于数据。反例：收缩方向取决于先验均值——若换强先验 $\alpha=20,\beta=20$，估计会被强力推向 $1/2$、几乎无视 $k$；这正是"先验力量与样本量权衡"（即正则化强度与样本量之比）的活教材，先验不是装饰，而是决定曲线在样本稀少处行为的主角。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把观测空间按 "选哪个假设" 切成区域 $S_i$、再把正确概率写成 $\sum_i P(\Theta=\theta_i,\ X\in S_i)$，这一步是"为什么 MAP 在所有准则里最优"的几何收官。第一性原理：每个 $x$ 都被 MAP 归给后验最大的 $\theta$，等价于把观测空间 $X\in S_i$ 划分成互不相交的"决策区"，正确概率是各先验×区上分布求和；若把某个 $x$ 改判给另一假设，只会降低该点的条件正确概率，故逐点最优推出整体最优。命名模板：把这些 $S_i$ 叫作 decision regions（决策区域），它们的边界（boundary）是由"两个后验相等"的方程刻出的曲线/超曲面。跨课程（模式识别 / 决策论，Duda & Hart）：这正是"贝叶斯决策边界"——当先验与损失对称时，边界处两个类后验相等、恰在二维图中把空间劈成两部分；Fisher 线性判别与 SVM 都在追求逼近这条最优边界。反例：$S_i$ 的刻画依赖对似然形状的信任；若模型错置（如把非对称分布当对称），即使"按后验切分"也非真最优——最优性只在模型正确的世界里成立，模型错则决策区只是"看起来最优"。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 二选一假设检验其实是所有"判别"任务的骨架。第一性原理：后验之比 $\dfrac{P(\Theta=1\mid x)}{P(\Theta=2\mid x)}$ 与似然比 $\dfrac{p_{X\mid\Theta}(x\mid 1)}{p_{X\mid\Theta}(x\mid 2)}$ 只差一个先验比常量，故 MAP 判公等价于"似然比超过阈值"，并把错误概率压到最低——这是全书第一次见到 likelihood ratio（似然比）的机制。命名模板：hypothesis（假设）配 testing（检验）＝"拿数据审理一组候选命题"，与统计推断的 hypothesis testing 同名而域更窄。跨课程（通信/检测理论）：本例来判别哪枚硬币，与判定来信哪种信号本质相同；在附录加性高斯噪声 + $\|a\|=\|b\|$ 时，该阈值规则进一步退化为比较两个内积（见之后匹配滤波例）——这正是 Neyman-Pearson 引理与 ROC 曲线的发源地。反例：若两类误判代价不对称（把垃圾邮件当正常 vs 把正常当垃圾），纯 MAP 的 0-1 损失不再最优，阈值要向代价高的一侧偏移；"无代价均衡"只是等代价情形下的特例。

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

其中 $W_i$ 是相互独立（independent）、且与[所发送信号]独立（independent）的标准正态随机变量（standard normal random variables）。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 匹配滤波器（matched filter）把概率论的结论翻译成一张能被硬件直接执行的"内积打分表"。第一性原理：当噪声是 i.i.d. 高斯、且 $\|\mathbf{a}\|=\|\mathbf{b}\|$ 时，比较两个候选信号的最优准则不是看幅度大小，而是比接收信号与各候选信号的内积 $\sum_i a_iX_i$——因为距离平方差正比于内积差，最大后验便等价于"离谁的内积更大"。命名模板：matched filter 的"匹配"指滤波器冲激响应与候选信号本身匹配（即做相关），而非去匹配噪声。跨课程（信号与系统 / 18.065 内积几何）：这正是在欧氏空间里的最近邻分类，那套"内积＝投影"正是相关接收机（correlation receiver）的构造；把 $\mathbf{a},\mathbf{b}$ 换成一般信号向量即得一般线性检测。反例：若两个候选信号能量不等（$\sum_i a_i^2 \ne \sum_i b_i^2$），纯内积比较会向"更长的信号"倾斜而失真，必须先归一化能量后再比，否则'最近'并不等价于'后验最大'。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这条 $E\big[(\Theta-\hat\theta)^2\big]=\mathrm{var}(\Theta)+\big(E[\Theta]-\hat\theta\big)^2$ 的分解，是把"最优估计"从公式变成几何的钥匙。第一性原理：均方误差关于 $\hat\theta$ 是严格下凸的二次式（平方系数为 1），顶点自然落在 $E[\Theta]$ 处；把随机变量 $\Theta$ 当向量、把常数 $\hat\theta$ 看成由常量函数张成的"直线"，最佳逼近正是 $\Theta$ 在这条直线上的正交投影 $E[\Theta]$。命名模板：把"取期望"称作投影（projection）看似费解，实则是以 $E[\cdot]$ 作内积、把随机变量当函数向量来看的惯用语言。跨课程（概率＋线性代数 / 18.06）：条件期望"是到可测子空间上的正交投影"这条概率论与线性代数之间最深的桥，在此露出第一只脚；后面 LMS 的无条件最小性不过是该投影定理的逐点版。反例：只要目标是绝对误差 $E|\Theta-\hat\theta|$，最优解就从均值挪到中位数——说明"最优"由损失函数定义，绝不能想当然默认均值总是对的。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 三条"最小均方事实"其实是同一件事的三层缩放：没有观测、已知 $x$、面对全部 $X$，最小点永远是条件期望 $E[\Theta\mid X]$。第一性原理：对固定的 $x$，条件均方误差当作 $\theta$ 的二次式、顶点在 $E[\Theta\mid X=x]$；再对 $x$ 取期望（迭代期望律）就把逐点最优汇成全局最优——三层共用同一个"投影到常数直线取均值"的动作。命名模板：LMS 全称 least mean squares（最小均方），名字点明的目标是最小"平方误差"，别按发音误读成"均方最小"。跨课程（18.06 / 18.065）："正交投影＋平方目标"是广义最小二乘、卡尔曼与维纳滤波共享的几何内核，第 8.4 节线性 LMS 就是在"线性子空间"上重做同一投影。反例：若某 $x$ 下 $\Theta$ 的后验是双峰，条件期望落在两峰之间的谷里——它给出均方误差最小的点，却偏离"最可能的取值"（MAP 峰）甚远，提醒我们"期望 ≠ 最可能代表值"。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 例 8.10 里的平行四边形不是画着好看的，而是"均匀噪声叠加到均匀参数上"的支撑几何的全部信息。第一性原理：$\Theta$ 均匀于 $[4,10]$、$W$ 均匀于 $[-1,1]$，则 $(\Theta,X)=(\theta,\theta+w)$ 落在把 $[\theta-1,\theta+1]$ 沿 $\theta$ 轴扫出来的菱形里——联合支撑是个平行四边形，且因其由两段均匀维而来、联合密度在支撑上恒定。命名模板：把"变量的线性相加"想成"把一条段沿另一条段平移扫出的平行四边形"（parallelogram），这也是辛几何与线性变换里平行四边形恒等式（parallelogram law）的同名直觉。跨课程（几何 / 正交投影）：对给定 $x$ 作水平切片，截出的片段长度正比于该 $x$ 下的后验密度——故后验密度在这些截面里呈线性函数；这正是"边缘/条件分布由几何投影决定"的最小实例。反例：若 $W$ 换成高斯（无界支撑），联合支撑就不再是平行四边形而是整片平面，后验也不会是简单的线性函数——形状的优势（闭式、可分解）全部来自"有限支撑 + 均匀"这两个软约束，换任一分布即崩塌。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> `条件均值最小均方（LMS）估计 = 后验期望`，这句话读起来像废话，实则是把"最优估计"烙在一张不可动摇的牌上。第一性原理：对每个 $x$，固定点准则要求最小化 $E[(\hat\theta-\Theta)^2\mid X=x]$，而它是 $\hat\theta$ 的下凸二次、顶点恰在后验均值 $E[\Theta\mid X=x]$——于是"逐点取后验均值"就是全局最小均方的唯一规律，不依赖密度是否光滑或是否共轭。命名模板：conditional mean（条件期望/条件均值）指"在断定为这一 $x$ 后对 $\Theta$ 的均值"，与无条件均值 $E[\Theta]$ 相对。跨课程（决策理论 / 优化）：二次损失的最优解必是条件均值，恰与"expectation minimizes L2 loss"这一最基础的定理一致；它也是回归拟合里"均值函数=最优预测"的理论根源。反例：最小均方最优不等同于"最可能"——当后验双峰时，条件均值落在两峰间的谷底，既不最可能也不居中，此时"最有代表"的说法须让位给后验众数或区间；"最优"二字总是相对损失函数而言，换损失就换解。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 对任意点估计 $\hat\theta$ 成立的恒等式 $E[(\hat\theta-\Theta)^2\mid X]=(\hat\theta-E[\Theta\mid X])^2+\mathrm{Var}(\Theta\mid X)$，是把"估计质量"切成两块的万能手术刀。第一性原理：均方误差的交叉项在取期望后恰好消掉，剩下的两块分别是"（估计的后验期望）偏多远"与"后验自身有多散"——前者叫 bias 方（系统性偏移）、后者叫 variance（不可约噪声），最优 LMS 恰使偏差项为零、把均方压到后验方差。命名模板：把恒等式记作 variance + bias²，是在提醒"误差最大的敌人可以不是噪声而是偏差"。跨课程（机器学习 / 统计学习，18.065）：这正是全教科书都引的 bias–variance tradeoff——模型越复杂（更多自由度）方差越大、复杂度过低则偏差大；选择是在两者间找最小均方的平衡点。反例：均值（LMS）虽然在平方损失下最优，却在后验双峰时既不落峰也不居中，所谓"无偏最优"是按二次损失说的；换绝对损失就要换成后验中位数——同一后验、不同恒等式下的"最优"可以背道而驰。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 抛硬币模型在 §8.1、8.2、8.3 被轮番重访，是因为它是四把"估计之尺"的最小公用模型。第一性原理：先验均匀等价于各一枚伪计数，故 $E[\Theta\mid X=k]=\frac{k+1}{n+2}$ 恰是"经验成功比" $k/n$ 被 $n+2$ 的总频次压向 $1/2$ 的加一修正——同一数据在不同损失/先验下得出 MAP=$k/n$ 与 LMS=$(k+1)/(n+2)$ 两个看似相近却不同的值。命名模板：把加一读出 Pseudo-Count（伪计数）与 Laplace's rule of succession（拉普拉斯后继率），是做贝叶斯平滑的同源手法。跨课程（概率论 / 组合计数）：$\frac{k+1}{n+2}$ 还能由"对称先验 + Beta 期望"推到，其极限 $\frac{k+1}{n+2}\to k/n$ 又给出相合性（consistency）；而 §8.4 将证明线性 LMS 在贝塔模型里恰等于非受限 LMS——因为该后验均值恰好是观测的线性函数。反例：不要以为"加一修正看似无害"——若真实硬币极偏（$p=0.05$）且 $n$ 很小，$+1$ 修正会把估计死死拽向 $0.5$，此时先验的"均匀＝等可能"假设对先验不明的小样本反而最有害；先验只该反映真实知识，而非凭空的对称。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 无偏（$E[\tilde\Theta]=0$）、不相关 $(\mathrm{cov}(\hat\Theta,\tilde\Theta)=0)$、方差可加 $(\mathrm{var}(\Theta)=\mathrm{var}(\hat\Theta)+\mathrm{var}(\tilde\Theta))$——这三条合在一起，正是在内积空间里"正交分解"的随机变量版。第一性原理：把 $\hat\Theta$ 与 $\tilde\Theta=\Theta-\hat\Theta$ 视为两个"向量"，"不相关"即内积为零（正交），方差平方可加则恰是勾股定理 $\|\Theta\|^2=\|\hat\Theta\|^2+\|\tilde\Theta\|^2$ 的概率写照；三条性质其实由"最小均方最优性"一步到位推出。命名模板：正交（orthogonal）在这里指"不相关"，是比独立（independent）弱得多却够用的几何条件。跨课程（线性代数 / 18.065）：这意味着条件期望 $E[\Theta\mid X]$ 就是把 $\Theta$ 向「由 $X$ 的可测函数构成的子空间」做正交投影，$E[(\hat\Theta)^2]$ 是投影长度、$E[(\tilde\Theta)^2]$ 是余长——维纳滤波、卡尔曼与岭回归共享同一勾股骨架。反例：方差可加是"不相关"的推论而非"独立"的推论——独立必不相关，反之不然；若只凭 $\hat\Theta$ 与 $\tilde\Theta$ 不相关就断言独立，就滑进了贝叶斯里最常见的误读。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页顶部三条性质中的记号在 OCR 中被读成 `8`/`e` 的混排（如 `E[e I X = x] = 0`、`coV(8, e)`、`var(8) = var(8) + var(e)`，且 `for all x`、`=`、`0` 各符号被拆散在相邻若干行），无法逐字还原其原书写。上文统一按 §8.3 的标准记号 $\hat\Theta = E[\Theta\mid X]$（估计量）与 $\tilde\Theta = \Theta - \hat\Theta$（估计误差）复原为 $E[\tilde\Theta\mid X=x]=0$、$E[\tilde\Theta]=0$、$\mathrm{cov}(\hat\Theta,\tilde\Theta)=0$、$\mathrm{var}(\Theta)=\mathrm{var}(\hat\Theta)+\mathrm{var}(\tilde\Theta)$；三者与下页 Example 8.14 的推证交叉吻合，非臆造。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 8.14（无信息观测，Uninformative Observation。）**</span>

我们说观测 $X$ 是无信息（uninformative）的，如果均方估计误差（mean squared estimation error）$E[\tilde\Theta^2]$ 与 $\operatorname{var}(\Theta)$、即 $\Theta$ 的无条件方差相同。何时会出现这种情况呢？

利用公式 $\operatorname{var}(\Theta) = \operatorname{var}(\hat\Theta) + \operatorname{var}(\tilde\Theta)$，我们看出 $X$ 是无信息的当且仅当 $\operatorname{var}(\hat\Theta) = 0$。一个随机变量的方差为零，当且仅当该随机变量是一个常数、等于其均值。由此我们得出结论：$X$ 是无信息的，当且仅当估计量 $\hat\Theta = E[\Theta\mid X]$ 对 $X$ 的每个取值都等于 $E[\Theta]$。

若 $\Theta$ 与 $X$ 独立，则对一切 $x$ 有 $E[\Theta\mid X = x] = E[\Theta]$，从而 $X$ 确为无信息的，这十分直观。然而，其逆命题并不成立：有可能 $E[\Theta\mid X = x]$ 恒等于常数 $E[\Theta]$，而 $\Theta$ 与 $X$ 并不独立。（你能构造出这样的一个例子吗？）

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 8.14 那句"你能构造出这样的例子吗"是抛给读者的钩子，也点破了方差分解 $\mathrm{var}(\Theta)=\mathrm{var}(\hat\Theta)+\mathrm{var}(\tilde\Theta)$ 的信息含义。第一性原理：估计误差 $\tilde\Theta$ 与估计 $\hat\Theta$ 不相关（协方差为零），故总方差被干净地切成"被解释（signal）"与"未解释（noise）"两块；观测 $X$ 提供信息，就是从 $\Theta$ 的方差里成功剥出一块归给 $\hat\Theta$。命名模板：uninformative（无信息）直接以"方差是否被压减"来定义，而非看 $X$ 本身在不在变化。跨课程（信号处理/通信）：这就是信噪比 SNR $=\mathrm{var}(\hat\Theta)/\mathrm{var}(\tilde\Theta)$ 的静态版，本质与维纳滤波的一致最优重构同一主题。反例：$E[\Theta\mid X]$ 恒为常数只说明该函数是平的（均方意义下无信息），绝不意味着统计独立——例如让 $X=\Theta$、再把观测换成 $X^2$，$E[\Theta\mid X^2]$ 仍可能就是常数，可 $\Theta$ 与 $X^2$ 显然相关；独立是远比"无信息"苛刻的条件。

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

并在所有估计量 $\hat{\Theta}_1, \ldots, \hat{\Theta}_m$ 上将其最小化。但这等价于：对每一个 $i$，都去求一个使 $E\big[(\hat{\Theta}_i - \Theta_i)^2\big]$ 最小的估计量 $\hat{\Theta}_i$；于是我们实质上是在处理 $m$ 个两两解耦（decoupled）的估计问题，每个对应一个未知参数 $\Theta_i$，最后得出 $\hat{\Theta}_i = E[\Theta_i \mid X_1, \ldots, X_n]$（对一切 $i$ 成立）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「多参数的最小均方 = 各参数各自最小均方」读来顺理成章，实则点破了平方准则与范数的优雅耦合。第一性原理：对每个 $\Theta_i$ 单独最小化 $E[(\hat\Theta_i-\Theta_i)^2]$，再看总目标 $\sum_i E[(\hat\Theta_i-\Theta_i)^2]$——因为平方和的每一项只含自己的 $\Theta_i$、不含交叉项，各参数彼此解耦（decoupled），全局最小化退化为 $m$ 个独立的单参数问题。命名模板：decoupled（解耦）指"目标函数是各项之和、无交叉项"；一旦出现交叉项（如 $E[\hat\Theta_1\hat\Theta_2]$），解耦即告破碎。跨课程（线性代数 / 18.05）：这正像二次型 $f(x_1,\dots,x_m)=\sum_i a_ix_i^2$（对角矩阵）的最优在各自坐标处各取极小——把分母换成协方差矩阵的投资组合里，各分量才真正两两耦合；所谓"各参数独立求解"成立的条件，正是目标函数可分离（separable）。反例：解耦依赖"逐分量平方损失"这一准则选择；若改目标为 $\sum_i(\hat\Theta_i-\Theta_i)^2$ 之上加权重或耦合交叉项（如联合协方差惩罚），解耦即失效、必须联合求解——Lasso/ridge 的组稀疏正是在这一步扔掉分量解耦、换取结构信息。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把最优估计从"任意函数"缩到"线性组合"，是用一个小小的 b 换回巨大的可算性。第一性原理：完整 LMS 需要联合分布 $f_{\Theta,X}$ 和无约束的最优函数 $g(X)=E[\Theta\mid X]$；线性 LMS 只在仿射（affine）函数 $a_1X_1+\cdots+b$ 里找最好，只需一阶、二阶矩（均值/方差/协方差）即可定解——牺牲的是全局最优，换来的是只要矩、不要分布就能落地的工程友好性。命名模板：linear（线性）指"估计器是观测的线性组合（加常数）"，由之把问题从函数空间压缩到 $n+1$ 维参数空间。跨课程（信号处理 / 18.065 维纳滤波）：受限线性类是维纳滤波与自适应 LMS 算法的一切前提——在线估计只根据梯度更新系数、无需联合密度，靠的正是"一阶二阶矩"这丁点信息。反例：当后验均值恰好是 $X$ 的线性函数时（如高斯共轭或 Beta 例），线性 LMS 与全局 LMS 重合、零损失；而当后验均值强烈非线性（如例 8.11 的对数函数），压进直线后偏差骤增——"线性"是省了计算却不保最优的折价。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 第一步先给最优 $b$、第二步再来优化 $a$，这不是偷懒，而是利用了"可分离"的结构把二维问题切成两步。第一性原理：对固定的 $a$，关于 $b$ 的最小化是"无条件常数估计"的直接应用——最佳 $b$ 必取 $b=E[\Theta-aX]$ 使偏差归零、恰把误差化到 $\operatorname{var}(\Theta-aX)$；由此剩下的只是关于 $a$ 的一维最小化，把两参数一步求导改写成了"先中心化、再定斜率"的两段式。命名模板：把这种"先定截距、再定斜率"的次序称作截距-斜率分离（intercept–slope decoupling），是仿射拟合的惯用套路。跨课程（优化 / 18.065）：这等价于把均方误差看成 $(a,b)$ 的二次型、先对齐其无偏平移、再最小化剩下关于 $a$ 的二次——与梯度下降先归一化、再迭代的常见流程同构。反例：分离成立的前提是损失在 $b$ 上是二次且无约束、且目标关于 $(a,b)$ 可分；若给 $b$ 加约束（如 $b\ge0$）或目标含 $a,b$ 交叉的正则项，"先修 $b$ 再解 $a$"就会不再最优，须改为联合求解。

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

此外，利用全方差定律（law of total variance）（这与第 4 章中示例 4.17 的计算相同），我们有

```math
\operatorname{var}(X) = \frac{7}{144}\;.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「$\operatorname{var}(X)=\frac{7}{144}$」这一格数字，是迭代期望（law of iterated expectations）与全方差定律（law of total variance）经手运算一次的具体果实。第一性原理：$E[X]=E[E[X\mid\Theta]]$ 先剥掉 $\Theta$ 得 $\frac12\cdot\frac12=\frac14$；全方差 $\operatorname{var}(X)=E[\operatorname{var}(X\mid\Theta)]+\operatorname{var}(E[X\mid\Theta])$ 把总方差拆成"组内噪声"与"组间（随 $\Theta$）波动"两块，本例恰好凑出 $\frac{7}{144}$——这是把"未知参数混合造成的额外散布"量化的标准脚本。命名模板：$\operatorname{var}(X)=E[\cdot]+\operatorname{var}(\cdot)$ 双项合计，是"条件方差的期望 + 条件期望的方差"两个各自独立的来源相加。跨课程（随机信号 / 18.065 ANOVA）：这正是"组间方差 + 组内方差 = 总方差"的 ANOVA 分解——把 $X$ 的变异性归因到参数的随机性而非纯噪声，是信噪比与方差分量分析的基础。反例：不少读者把 $\frac{7}{144}$ 当常数背，其实它完全依赖模型设定——换 $\Theta$ 的方差或 $W$ 的分布，这个数立刻变；若误用全方差定律而把 $\Theta$ 当非随机、只算 $E[\operatorname{var}(X\mid\Theta)]$，就会丢掉"参数不确定"这一大项贡献，严重低估 $\operatorname{var}(X)$。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 线性 LMS 只须知道一阶与二阶矩（均值、方差、协方差）即可写出答案，这正是它作为工程主力被追捧的根源。第一性原理：若把估计限制为 $a_1X_1+\cdots+a_nX_n+b$，优化目标仍是一元/多元二次式，最优系数由法方程（normal equations）给出——即把 $\Theta$ 正交投影到由常量 $1$ 与各 $X_i$ 张成的线性子空间（函数空间）上。命名模板：linear（线性）限定"估计器必须是观测的线性组合"，宁可牺牲一点均方最优也要保住可算性。跨课程（信号与系统 / 18.065 维纳滤波）：这正是离散维纳滤波（Wiener filter）与自适应 LMS 算法推导的入口——只依赖二阶矩、不要求完整联合分布，因而能在线稳定更新。反例：Example 8.16 里线性 LMS 与（非受限）LMS 恰一致，是因为该模型的后验均值恰好是观测的线性函数；而像 Example 8.11 那种 $E[\Theta\mid X]=\frac{1-x}{-\log x}$ 的非线性情形，强行套线性逼近就会给出偏离最优的解——"线性"是一桩划算的折扣，并不是免费的。
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

这等价于对每个 $i$，寻找一个使 $E[(\hat\Theta_i - \Theta_i)^2]$ 最小的线性估计量（linear estimator）$\hat\Theta_i$，从而我们实质上是在处理 $m$ 个相互解耦（decoupled）的线性估计问题，每个对应一个未知参数。

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
