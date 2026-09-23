# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 16 — Markov Processes — I（马尔可夫过程 I）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline（本讲大纲）</span>

**阅读**：教材 Sections 7.1–7.2。

**本讲大纲（Lecture outline）**：
- 收银台例子（Checkout counter example）。
- 马尔可夫过程的定义（Markov process definition）。
- $n$ 步转移概率（n-step transition probabilities）。
- 状态的分类（Classification of states）。

> <span style="color:#7f8c8d;">Bertsekas §7.1, p.340–341；§7.2, p.346</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 教材第 7 章开篇（p.340）先给了一句话定位：Bernoulli 与 Poisson 过程是 memoryless（无记忆）的——未来与过去无关；而本章考虑的是**有记忆**的过程，只不过把"记忆"压缩到一个 state（状态）里：给定当前状态，未来与更早的历史无关。这是本讲一切内容的总纲。大纲四块恰好是四个台阶：先用具象的收银台队列示范"怎么把一个系统装进状态里"；再给 Markov chain（马尔可夫链）的正式定义（p.340–341 的转移概率与马尔可夫性质）；然后用 n-step transition probabilities（$n$ 步转移概率）回答"从 $i$ 出发 $n$ 步后在 $j$ 的概率"（p.345 的 Chapman-Kolmogorov 递归）；最后用 classification of states（状态分类）建立常返/暂态的语言（§7.2 从 p.346 起）。讲义标题说 Markov **Processes**，教材与后续限定在 discrete time、finite state 的 Markov chains（马尔可夫链）上——这两讲都处理这种最干净的情形。与前几讲的关系：到达过程研究"到达流"，这里研究"带记忆的系统状态轨线"，样本空间从时间点上的随机变量变成整条时间轴上的随机过程，但条件化、独立性的老工具一件都不少地沿用。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Checkout counter model（收银台模型）</span>

- 离散时间 $n = 0, 1, \ldots$
- 顾客到达：Bernoulli($p$)（伯努利过程）——到达间隔为 geometric（几何分布）。
- 顾客服务时长：geometric($q$)（参数 $q$ 的几何分布）。
- "State"（状态）$X_n$：时刻 $n$ 的顾客数（number of customers at time $n$）。

> <span style="color:#7f8c8d;">图：收银台前的队列示意——格子 $0, 1, 2, 3, \ldots, 9, 10$ 标出队列中可能出现的顾客数（容量上限 10）。</span>

转移结构的直觉：每一步有两个独立的伯努利事件——"新顾客到达"（概率 $p$）与"队首顾客服务完成"（队列非空时概率 $q$）。于是队列非空、未满时：到达且未完成则 $X_{n+1} = X_n + 1$，无到达且完成则 $X_{n+1} = X_n - 1$，其余情形 $X_{n+1} = X_n$。

> <span style="color:#7f8c8d;">Bertsekas §7.1, p.341–345（Examples 7.1–7.3 的建模范式）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 这个模型示范了马尔可夫建模的**三步配方**：先挑状态（这里取队列长度——它恰好是对未来有影响的全部历史信息的压缩：顾客几点来、服务了多久都无关紧要）；再定可能的转移（长度至多 $\pm 1$）；最后填转移概率（由 $p$、$q$ 两个伯努利参数复合而成）。注意到达侧的词汇与上一讲字典的对接：每槽以概率 $p$ 到达的 Bernoulli arrivals，其到达间隔正是 geometric($p$)（教材 §6.1, p.299–300），所以"离散时间到达流"在两章之间无缝换轨。跨课程连接：用你正在学的 6.006 的语言说，马尔可夫链就是一张**带概率权重的有向图**——节点是状态，边是转移，随机游走（random walk）每步沿一条出边移动；收银台模型就是链上带"驻留自环"的图。6.006 里图的复杂度取决于边数与状态数，这里同理：建模的艺术在于让状态空间尽量小、图尽量稀疏——队列长度只依赖"净流入"，所以状态是一维的而非"到达时刻集合"那样的高维怪物。把概率模型读成图、把图论直觉借给概率，这两讲会反复用到这条通道。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Finite state Markov chains（有限状态马尔可夫链）</span>

- $X_n$：$n$ 次 transition（转移）之后的状态。
  - 属于一个 finite set（有限集），如 $\{1, \ldots, m\}$。
  - $X_0$ 既可以是给定的，也可以是随机的。
- **Markov property/assumption（马尔可夫性质/假设）**：给定当前状态，过去无关紧要（given current state, the past does not matter）：
```math
p_{ij} = P(X_{n+1} = j \mid X_n = i) = P(X_{n+1} = j \mid X_n = i,\, X_{n-1}, \ldots, X_0) .
```
- **模型规定（model specification）**：
  - 识别可能的 states（状态）。
  - 识别可能的 transitions（转移）。
  - 识别转移概率（transition probabilities）。

> <span style="color:#7f8c8d;">Bertsekas §7.1, p.340–341（转移概率矩阵与转移概率图）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> 本页最值得诊断的是马尔可夫性质到底"弱化"了什么。公式 $P(X_{n+1} = j \mid X_n = i, X_{n-1}, \ldots, X_0) = p_{ij}$ 说的是**条件独立**：在给定 $X_n$ 的条件下，$X_{n+1}$ 与更早的历史条件独立。它**不**等于"$X_{n+1}$ 与 $X_0, \ldots, X_{n-1}$ 独立"——事实上 $X_{n+1}$ 与 $X_{n-1}$ 通常就是相依的（比如队列长度两步后大概率更长），只是这层相依必须经过 $X_n$ 中转。教材 p.340 的措辞是 the future depends on the past only through the present（未来对过去的依赖只经由现在）——"只经由"三个字就是全部内容。另一处卡点是 time-homogeneous（时齐）假设：$p_{ij}$ 不随 $n$ 变化，无论状态 $i$ 是第几次被访问、怎么被到达（教材 p.341：no matter how state $i$ was reached）。模型规定三步（状态/转移/概率）在 p.341 有标准封装：transition probability matrix（转移概率矩阵，每行和为 1）与 transition probability graph（转移概率图，节点加带权弧）——同一个模型的两种视图，前者便于代数（下一页的递归），后者便于读结构性结论（本讲末的状态分类）。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">n-step transition probabilities（n 步转移概率）</span>

- 给定初始状态 $i$ 的状态占据概率（state occupancy probabilities）：
```math
r_{ij}(n) = P(X_n = j \mid X_0 = i) .
```

> <span style="color:#7f8c8d;">图：三段时刻轴 Time 0 → Time $n-1$ → Time $n$——从 $i$ 出发经 $n-1$ 步以概率 $r_{i1}(n-1), \ldots, r_{ik}(n-1), \ldots, r_{im}(n-1)$ 落到各个中间状态 $k$，再各以 $p_{1j}, \ldots, p_{kj}, \ldots, p_{mj}$ 走到 $j$（对应教材 Fig. 7.5）。</span>

- **关键递归（key recursion，Chapman-Kolmogorov 方程）**：
```math
r_{ij}(n) = \sum_{k=1}^{m} r_{ik}(n-1)\, p_{kj} .
```
- 初始状态随机时：
```math
P(X_n = j) = \sum_{i=1}^{m} P(X_0 = i)\, r_{ij}(n) .
```

> <span style="color:#7f8c8d;">Bertsekas §7.1, p.345（Fig. 7.5）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 递归的推导只有两行，却是全讲的引擎：先用全概率定理按第 $n-1$ 步的位置拆分 $P(X_n = j \mid X_0 = i) = \sum_k P(X_{n-1} = k \mid X_0 = i)\, P(X_n = j \mid X_{n-1} = k, X_0 = i)$，再用马尔可夫性质把最后一个因子削成 $p_{kj}$（教材 p.345 的验证正是这两步）——"全概率 + 马尔可夫"的组合你已在 Lec 02–03 的条件概率里反复使用，这里只是把样本空间换成了状态轨线。第二式 $P(X_n = j) = \sum_i P(X_0 = i)\, r_{ij}(n)$ 则是对初始分布再作一次全概率展开。跨课程连接：教材 p.345 脚注专门写给熟悉矩阵乘法的读者——把 $r_{ij}(n)$ 排成矩阵 $R(n)$，递归恰好读作 $R(n) = R(n-1)\, P$，于是 $R(n) = P^n$，$n$ 步转移矩阵就是一步转移矩阵的 $n$ 次幂。这正是 Strang 线性代数里矩阵幂与线性算子迭代的语言：$P$ 是"分布空间"上的线性算子（保持行和为 1），链的演化就是该算子的反复作用；后面 steady-state（平稳态）的存在性、收敛性，都会回到"$P$ 的幂什么时候稳定"这个线代问题。两条公式请对照记忆：固定 $i$ 用递归，随机起点用左乘初始分布。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example（例题：二状态链的 n 步演化）</span>

> <span style="color:#7f8c8d;">图：二状态链——状态 1 自环 $p_{11} = 0.8$、转到 2 的概率 $p_{12} = 0.2$；状态 2 自环 $p_{22} = 0.5$、转回 1 的概率 $p_{21} = 0.5$。</span>

- $n = 0$，$n = 1$，$n = 2$，$n = 100$，$n = 101$ 时的 $r_{11}(n)$、$r_{12}(n)$、$r_{21}(n)$、$r_{22}(n)$：

| | $n=0$ | $n=1$ | $n=2$ | $n=100$ | $n=101$ |
|:---:|:---:|:---:|:---:|:---:|:---:|
| $r_{11}(n)$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ |
| $r_{12}(n)$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ |
| $r_{21}(n)$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ |
| $r_{22}(n)$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ | $\underline{\qquad}$ |

> <span style="color:#7f8c8d;">Bertsekas §7.1, p.345（Fig. 7.6 同型链的 $n$ 步迭代行为）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 逐格验算。$n = 0$：从 $i$ 出发仍在 $i$，得 $(r_{11}, r_{12}, r_{21}, r_{22}) = (1, 0, 0, 1)$ ✓。$n = 1$：直接读转移概率 $(0.8, 0.2, 0.5, 0.5)$ ✓。$n = 2$ 用关键递归：$r_{11}(2) = r_{11}(1) p_{11} + r_{12}(1) p_{21} = 0.8 \times 0.8 + 0.2 \times 0.5 = 0.74$ ✓，$r_{12}(2) = 0.8 \times 0.2 + 0.2 \times 0.5 = 0.26$ ✓，$r_{21}(2) = 0.5 \times 0.8 + 0.5 \times 0.5 = 0.65$ ✓，$r_{22}(2) = 0.5 \times 0.2 + 0.5 \times 0.5 = 0.35$ ✓。$n = 100$ 与 $n = 101$：迭代数值上趋于稳定，极限由"占住不动"的平衡条件反解——设极限为 $(\pi_1, \pi_2)$，则 $\pi_1 = 0.8\pi_1 + 0.5\pi_2$ 给出 $0.2\pi_1 = 0.5\pi_2$，即 $\pi_1 = 2.5\,\pi_2$；连同 $\pi_1 + \pi_2 = 1$ 解得 $\pi_1 = 5/7 \approx 0.714$、$\pi_2 = 2/7 \approx 0.286$ ✓，于是两行的 $n = 100, 101$ 格都填 $(5/7, 2/7, 5/7, 2/7)$。两个值得注意的现象：其一，无论从状态 1 还是状态 2 出发，行向量都收敛到**同一个**极限（下一讲的主题）；其二，$n = 100$ 与 $n = 101$ 几乎无差别——因为两个状态都有正的自环，链不可能"卡节奏"（周期性话题在下一讲展开）。另做一道免费的健全性检查：每一行都应归一，$r_{11}(2) + r_{12}(2) = 0.74 + 0.26 = 1$、$r_{21}(2) + r_{22}(2) = 0.65 + 0.35 = 1$ ✓——转移矩阵的幂每行仍是概率分布，任何一步算出两元素之和不为 1 就说明递归抄错了行。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Generic convergence questions（一般性的收敛问题）</span>

- $r_{ij}(n)$ 会收敛到什么吗？
> <span style="color:#7f8c8d;">图（周期反例）：周期 2 的链——从状态 2 出发各以 $0.5$ 进入状态 1 或 3，而 1、3 下一步以概率 $1$ 返回 2；从 2 出发每逢偶数步回到 2、奇数步离开 2。填空：$n$ 奇时 $r_{22}(n) = \underline{\qquad}$；$n$ 偶时 $r_{22}(n) = \underline{\qquad}$。</span>
- 极限依赖于初始状态吗？
> <span style="color:#7f8c8d;">图（初态依赖反例）：苍蝇与蜘蛛链（教材 Example 7.2 取 $m = 4$）——状态 1、4 为蜘蛛（吸收态，自环概率 $1$）；苍蝇在 2、3 处各以 $0.3$ 左移/右移、$0.4$ 原地不动。填空：$r_{11}(n) = \underline{\qquad}$，$r_{31}(n) = \underline{\qquad}$，$r_{21}(n) = \underline{\qquad}$。</span>

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.352（周期类不收敛的论述）；§7.1, p.345（Fig. 7.7：极限依赖初态）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 上图验算：从状态 2 出发，奇数步必在 1 或 3（$r_{22}(n) = 0$，$n$ 奇 ✓），偶数步必回到 2（$r_{22}(n) = 1$，$n$ 偶 ✓）——序列 $1, 0, 1, 0, \ldots$ 永不收敛，教材 p.352 用两状态版（$p_{12} = p_{21} = 1$）给出同样的诊断：recurrent class 是 periodic（周期的），$r_{ij}(n)$ 一般会振荡。下图验算：$r_{11}(n) = 1$ 对一切 $n \ge 1$ ✓（蜘蛛 1 是吸收态，进去出不来）；而 $r_{21}(n)$、$r_{31}(n)$ 的极限是"被蜘蛛 1 抓住"的概率，用首步分析（first-step analysis）解方程：$h_2 = 0.3 \cdot 1 + 0.4 h_2 + 0.3 h_3$，$h_3 = 0.3 h_2 + 0.4 h_3$，由第二式 $h_3 = h_2 / 2$，代回第一式 $0.45\,h_2 = 0.3$，得 $h_2 = 2/3$、$h_3 = 1/3$ ✓——故 $r_{21}(n) \to 2/3$、$r_{31}(n) \to 1/3$，而 $r_{41}(n) \to 0$。结论：这链条确实收敛，但极限**依赖初始状态**（从 4 出发永远到不了 1）。卡点诊断：两幅反例分别击破"一定会收敛"与"收敛就与初态无关"两个想当然；下一讲将证明只要"单一常返类 + 非周期"同时成立，二者同时修复。首步分析这个工具本身就是一张递归方程组，将在 §7.4 吸收概率里大规模返场。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Recurrent and transient states（常返态与暂态）</span>

- 状态 $i$ 是 recurrent（常返）的，如果：从 $i$ 出发，且从你能到达的任何地方出发，都存在一条回到 $i$ 的路。
- 若非常返，则称为 transient（暂态）。
  - $i$ 暂态：$P(X_n = i) \to 0$，且 $i$ 只被访问有限次。
- **Recurrent class（常返类）**：彼此 "communicate"（互通）、且不与任何其他状态互通的常返状态之集合。

> <span style="color:#7f8c8d;">图：多状态分类示例链（本讲与下一讲反复使用的同一张图，图中可见状态 $5, 1, 2$ 一行与上方的 $3, 4, 6, 7$、右侧的 $8$）——用于辨认哪些状态互通、哪些常返；各弧上的转移概率数值未随文本保留。</span>

> <span style="color:#7f8c8d;">Bertsekas §7.2, p.346（accessible/recurrent/transient 的定义；Example 7.2 与 Fig. 7.8）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 定义的关键词是 accessible（可达）：$j$ 从 $i$ 可达，若存在某个 $n$ 使 $r_{ij}(n) > 0$——即图上存在一条从 $i$ 到 $j$ 的有向路径（教材 p.346）。"常返"的直觉版本是"进了我的势力范围就跑不出去"：从 $i$ 出发能到的所有状态里，每一个都必须能回到 $i$；只要有一个 $j$ 回不来，$i$ 就是暂态——因为链迟早（概率 1）会溜进那个 $j$ 并从此回访无门，于是 $P(X_n = i) \to 0$、$i$ 只被访问有限次 ✓。第一性原理推论：常返性把状态切成"封闭势力范围"——若 $i$ 常返，则从 $i$ 可达的状态全部与 $i$ 互通，它们构成一个 recurrent class（常返类），从类内任何状态都到不了类外（教材 §7.2：recurrent states are all accessible from each other）。跨课程连接：这套结构在 6.006 有向图里就是 strongly connected components（强连通分量）——常返类恰是"没有出边的"强连通分量（sink component），暂态则是其余分量；识别常返类就是一遍图搜索的工作量。图论直觉（可达性、闭包、缩点）在这里全额兑现：先在图上找封闭分量，再谈概率，顺序不要反。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
