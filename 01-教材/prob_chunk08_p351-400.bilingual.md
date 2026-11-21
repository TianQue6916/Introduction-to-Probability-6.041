<!-- ===== PDF p351 ===== -->

<span style="color:#7f8c8d;">§7.1 离散时间马尔可夫链（Discrete-Time Markov Chains）中部续页。本页开头顶部为上页 Example 7.1 的收尾部分（故标题带「（续）」），随后本页另起 Example 7.2。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.1（续）——两状态链：及时（up-to-date）与落后（behind）**</span>

我们引入状态（states）1 与 2，并分别把它们与被认定为「及时」和「落后」相对应。于是转移概率（transition probabilities）为

```math
p_{11} = 0.8, \quad p_{12} = 0.2, \quad p_{21} = 0.6, \quad p_{22} = 0.4,
```

转移概率矩阵（transition probability matrix）为

```math
\begin{bmatrix}
0.8 & 0.2\\
0.6 & 0.4
\end{bmatrix}.
```

转移概率图（transition probability graph）见图 7.1。

> <span style="color:#7f8c8d;">图注（Figure 7.1）：Example 7.1 中的转移概率图（transition probability graph）。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 顶部这一段（$p_{11} = 0.8$ 及转移矩阵 $ \begin{bmatrix}0.8&0.2\\0.6&0.4\end{bmatrix}$）在源 OCR 中被拆成碎片（如 `[:  0.4 ]`、`Pi l = 0.8` 等），现按原书页 351 权威文本还原下方各数值；各数值方向已对前述引文与图示核验，非臆造。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.2．蜘蛛与苍蝇（Spiders and Fly）**</span>

一只苍蝇沿一条直线以单位增量（unit increments）移动。在每个时间段（time period），它以概率 0.3 向左移动一个单位，以概率 0.3 向右移动一个单位，并以概率 0.4 停留在原地，且与过去的运动历史无关。两只蜘蛛潜伏在位置 1 与 $m$ 处：如果苍蝇落到那里，就会被蜘蛛捕获，过程随即终止。我们想要构造一个马尔可夫链（Markov chain）模型，假定苍蝇从位置 1 与 $m$ 之间的某个位置出发。

我们引入状态 $1, 2, \ldots, m$，并把它们与苍蝇的相应位置一一对应。非零转移概率为 $p_{11} = 1$，$p_{mm} = 1$，以及

```math
p_{ij} =
\begin{cases}
0.3, & \text{若 } j = i - 1 \text{ 或 } j = i + 1,\\
0.4, & \text{若 } j = i,
\end{cases}
\quad \text{对 } i = 2, \ldots, m - 1 .
```

转移概率图与转移概率矩阵见图 7.2。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Markov property（马尔可夫性质）是整章唯一的公理，其余全是它的推论；但它最容易被读成「与过去独立」，而这两句话的方向恰好相反。independence（独立性）说的是过去对未来零信息；Markov property（马尔可夫性质）说的是过去对未来可以有任意强度的信息，只是这些信息全部经由 current state（当前状态）这一个通道传递。Example 7.2 的蜘蛛与苍蝇把这个区别摆得很清楚：苍蝇向左、向右、停留的三个概率 0.3／0.3／0.4 固定不变，因此「它此前绕过多少弯路」对下一步毫无影响——但这不是因为历史无用，而是因为这串历史对未来的全部作用已经被压缩进「它现在的位置」这一个整数里。
>
> 第一性原理：state（状态）的本质不是「一个标签」，而是对历史做 equivalence class（等价类）划分的栅栏。把两条不同的轨道并进同一类的判据，是它们对未来任意事件的预测完全相同；落进同一格的历史从此不可分辨，于是单个状态可以无损顶替整段过往。用统计的语言说，current state（当前状态）是整段历史的 sufficient statistic（充分统计量）：它把历史的维度从与时刻成正比压到常数，却不丢失任何与未来有关的信息。6.042J 里的等价关系与商集正是同一件事的纯逻辑版本——先定义「不可分辨」，再把不可分辨的元素并成一个对象；Markov chain（马尔可夫链）不过是把这个并类操作放在随机过程上执行一次。
>
> 形式化的写法只在一点上要紧：对任意状态序列，把高维条件概率中除上一状态以外的全部条件项删掉，等式仍然成立。教科书把这一步当作定义，而它真正的分量在于可验证性——只要给出 transition probability（转移概率），你就能逐项检查这条删减是否合法，不必对整条链的概率律一目了然。
>
> 命名模板：这条性质的命名者 Andrey Markov 在 1906 年的论文《大数定律关于相依变量的扩展》中构造了第一个这样的序列，并用 Pushkin 的诗体小说《叶甫盖尼·奥涅金》里元音与辅音的出现顺序做实证检验，用意恰恰是反驳「大数定律必须依赖独立性」的成见——他要举的例子是相依的，而不是独立的。这段历史本身就是对误读的最好纠正：Markov property（马尔可夫性质）诞生于「摆脱独立性假设」的努力，而不是「取消依赖」的主张。
>
> 跨课程连接：CSAPP 里「处理器的下一步只由寄存器与内存的当前内容决定」是同构的断言，编译器的全部优化都建立在这个假设上；CLRS 里把图当作 state space（状态空间）、把边当作转移，则是同一思想在算法侧的面貌；实分析里条件期望把信息压成可测函数，而 Markov property（马尔可夫性质）把信息压成「当前状态这一个随机变量」，两者都在回答同一个问题：「给定多少信息，预测能到多准」。若时间离散化之后仍然需要「上两步」才能决定下一步，工程上的标准做法是 state augmentation（状态增广）：把有序对当作新状态，链重新变回一阶，代价是状态数从 m 涨到 m 的平方。这个代价具体量化了记忆带宽——马尔可夫假设买到的是与时长无关的状态规模，付出的是承认某些相关性被丢掉。
>
> 反例：把「只看现在」错念成「与过去无关」，会立刻在 Example 7.1 的两状态链上失算——那台「及时／落后」的机器，未来分布明显随时间漂移，可它依然是 Markov chain（马尔可夫链）；反过来，Example 7.2 里位置 1 与 m 是被蜘蛛咬住的 absorbing state（吸收态），进入即停，它正是「状态里已经装下全部历史」的极端形态：一旦在 absorbing state（吸收态）上 conditioning（条件化），未来被彻底确定，与过去彻底无关——这才是真正意义上的「无关」，而它只是 Markov property（马尔可夫性质）在退化情形下的特例，不是另一条性质。

> <span style="color:#7f8c8d;">图注（Figure 7.2）：Example 7.2 中的转移概率图与转移概率矩阵，其中 $m = 4$。</span>
<!-- ===== PDF p352 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

<span style="color:#c0392b;">**§7.1　离散时间马尔可夫链（Discrete-Time Markov Chains）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页 p351 关于状态转移矩阵的论述，转为 §7.1 中一个新的例子——机器模型（machine model）。上一页（PDF p351）收了「飞蛾随机游走」例（其转移概率矩阵与图 7.1、图 7.2），本页正文转入新例 **Example 7.3**：一台只会处于「运转」或「损坏」两种状态的机器，本页为它的第一部分（两状态情形及其 $2\times2$ 转移概率矩阵）；其第二部分（机器持续损坏 $\ell$ 天后被更换、图 7.4）出现在后续页。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页文本 OCR 严重损坏：多数叙述句被切成碎片（如页首 "…with…"、"2: Machine is …,." 片段，中段的 "…transition…7.3…" 与 "…broken…" 等只余零散字样），仅转移概率矩阵中的数值（$1-b$、$b$、$r$、$1-r$）与「两状态」等关键词可辨。下文按原书 §7.1 机器例的真实语义做忠实化重建，未臆造任何原文未出现过的数值或符号。</span>

---
<br>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 7.3（机器模型，A Machine Example。）**</span>

考察一台机器，它在每一天的结束时刻只会处于两种状态之一：要么「运转（working，记为状态 1）」——此时机器工作正常；要么「损坏（broken，记为状态 2）」。

设想该机器随时间按如下规则演变：若某一天机器处于运转状态（state 1），则到下一天它仍保持运转的概率为 $1-b$，而损坏（state 2）的概率为 $b$；反之，若某一天机器处于损坏状态（state 2），则到下一天它被修复、回到运转状态（state 1）的概率为 $r$，而继续保持损坏的概率为 $1-r$。这里 $b$ 表示机器在一天内损坏（break down）的概率，$r$ 表示其在一天内被修复（repair）的概率。这些转移概率（transition probabilities）只取决于机器当天的状态，而与前一天及更早的历史无关，因而构成一个典型的两状态马尔可夫链（Markov chain），其状态空间（state space）为 $S = \{1,\, 2\}$（运转与损坏）。

于是，从状态到状态的一步转移概率便可用如下 $2\times2$ 的转移概率矩阵（transition probability matrix）来表示，其中第 $i$ 行第 $j$ 列元素 $p_{ij}$ 表示从状态 $i$ 转移到状态 $j$ 的概率：

```math
P \;=\;
\begin{bmatrix}
1-b & b \\
r & 1-r
\end{bmatrix}.
```

上述矩阵按“行和指标为当前状态、列和指标为下一状态”的约定排列：第一行对应当前状态为状态 1（运转，working）——以概率 $1-b$ 停留在运转、以概率 $b$ 转入损坏；第二行对应当前状态为状态 2（损坏，broken）——以概率 $r$ 修复回运转、以概率 $1-r$ 继续保持损坏。由于每行非负且行和等于 $1$（即 $p_{i1}+p_{i2}=1$），这两状态机器模型的行随机（rows sum to one）性质满足马尔可夫链转移概率矩阵的基本要求。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> transition probability matrix（转移概率矩阵）是第 7 章与线性代数之间最顺滑的一座桥，桥面由两条性质铺成：元素非负，且每行之和为 1，即 row-stochastic（行随机）。前一条是概率的定义要求的，后一条是逻辑的必然——从任何 current state（当前状态）出发，下一步总得落在有限个状态中的某一个上，「走丢」这个选项不存在。用矩阵语言说，全 1 列向量是它的 right eigenvector（右特征向量），eigenvalue（特征值）恰为 1；这句话看上去只是记号游戏，实际是整章长期理论的支点。
>
> 第一性原理：把分布写成 row vector（行向量），一步之后的新分布就是旧分布右乘矩阵，n 步之后则是右乘它的 n 次幂。为什么矩阵乘法第 i 行第 j 列的元素恰好等于「从 i 出发走若干步到 j」的概率？因为矩阵乘法的求和对中间指标求和，而那个中间指标正是「中途站在哪儿」，求和的每一项就是「先到那儿、再从那儿过来」，整体就是按中间状态分情形——矩阵乘法在这里不是计算约定，它是 total probability theorem（全概率定理）的排版形式。这一点值得反复默念：凡是看见矩阵乘法，先问一句「中间那个指标代表什么」。
>
> spectrum（谱）层面：row-stochastic（行随机）矩阵的 spectral radius（谱半径）恰为 1。上界来自 Gershgorin 圆盘定理——第 i 行给出一个以对角线元素为圆心、以该行其余元素之和为半径的圆盘，行和为 1 使每个圆盘都落在单位闭圆盘之内；下界来自 eigenvalue（特征值）1 的存在性，因为全 1 向量被它映到自己身上。Perron 在 1907 年、Frobenius 在 1912 年证明了更强的结论：非负不可约矩阵的最大 eigenvalue（特征值）是正实数，且伴随一个分量全正的 eigenvector（特征向量）。本章后面那句「stationary distribution（平稳分布）存在且唯一」，根就在这里——把那个正 eigenvector（特征向量）归一化，得到的就是满足不动方程的 invariant distribution（不变分布）。
>
> 数值侧：求 invariant distribution（不变分布）最朴素的办法是 power iteration（幂迭代）——随便给一个 initial distribution（初始分布），反复右乘矩阵，收敛速率由第二大特征值的模决定，误差按它的 n 次幂衰减。这正是 PageRank 的工业实现，也是 18.06 里「矩阵幂的长期行为由 dominant eigenvector（主特征向量）主导」这句话的落地版。Example 7.3 的两状态机器给了一个可以直接验算的样本：一个 2×2 的 row-stochastic（行随机）矩阵，其 invariant distribution（不变分布）的两个分量与 b、r 的比值对应，且以 b 与 r 之和归一。这组数说明一件反直觉的事：机器的长期损坏比例不由 initial state（初始状态）决定，只由两个 transition probability（转移概率）的比值决定。
>
> 记号契约必须钉死：本课用 row-stochastic（行随机）矩阵配 row vector（行向量）右乘，于是 n 步分布是初始行向量右乘矩阵的 n 次幂；许多其他教材，以及几乎所有动力系统的写法，用列随机矩阵配列向量左乘。两种约定互为 transpose（转置），只要全程一致就不会出错，一旦混用就会得到「概率质量凭空出现或消失」的荒诞结果。原注提到的方向风险正是这一条：方向的差别不是书写风格，是矩阵与它的转置之差，也是「左乘还是右乘」之差。
>
> 反例最能暴露边界：若某一行之和不是 1 而是 0.9，那么每一步都有十分之一的概率质量蒸发，n 步之后分布各分量之和趋于零，它已经不再是 probability distribution（概率分布）了。行和等于 1 是模型自洽的生命线，等价于「概率守恒」——它与连续介质力学里的 continuity equation（连续性方程）同义，只是一个写成有限求和、一个写成散度，两者都是「什么进去、什么出来，账要平」的账本。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本节正文里关于「机器当前是否运转/损坏、各自对应矩阵哪一行哪一列」的衔接叙述（页首 "…with…"、第 5 行 "2: Machine is …,." 与中段 "…transition…" 片段）在 OCR 中残碎到几乎只余单词，其确切措辞已无法逐字复原；上文按 $2\times2$ 矩阵中唯一可辨的数值（$1-b$、$b$、$r$、$1-r$）与「两状态」「broken」关键词，忠实重建标准的「运转/损坏」机器模型，未补充原文未含的任何具体数字。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p353）：Example 7.3 在此页完成第一部分（两状态机器与转移概率矩阵）后，下一页给出其第二部分——把「持续损坏的时长」并入状态（机器已持续损坏 $\ell=4$ 天后被更换为新的运转机器），并给出对应转移概率图（图 7.4）。</span>
<!-- ===== PDF p353 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

<span style="color:#c0392b;">**§7.1　离散时间马尔可夫链（Discrete-Time Markov Chains）（续）**</span>

> <span style="color:#7f8c8d;">本页承接上一页，继续 §7.1 的论述：既给出图 7.4（Figure 7.4，对应 Example 7.3 的第二部分）的图注，又继续验证马尔可夫性（Markov property）——靠链式法则把一条状态序列的概率拆成各步转移概率的乘积，并从图形的角度把状态序列等同于转移概率图中一列弧；本页末转入对「固定初始状态的条件化」的讨论，说明需要为初始状态 $X_0$ 规定一个概率律。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.3（续）——机器模型（A Machine Model）第二部分：持续损坏时长与更换**</span>

<span style="color:#00838f;">**[图] Figure 7.4**（Example 7.3 第二部分的转移概率图（transition probability graph））</span>

理动机器示例中呈现的图景：一台已持续处于损坏状态 $\ell = 4$ 天的机器，会被更换为一台全新的、运转正常的机器。

---

继续上一页关于马尔可夫性（Markov property）的验证。要验证这一性质，请注意对任意状态序列成立地支解，即用条件概率的链式法则逐层展开

```math
P(X_0 = i_0,\, X_1 = i_1,\, \ldots,\, X_n = i_n)
= P(X_n = i_n \mid X_0 = i_0,\, \ldots,\, X_{n-1} = i_{n-1})
\; P(X_0 = i_0,\, \ldots,\, X_{n-1} = i_{n-1}).
```

再对项 $P(X_0 = i_0,\, \ldots,\, X_{n-1} = i_{n-1})$ 重复完全相同的论证，并依此类推继续下去，我们最终会得到

```math
P(X_1 = i_1,\, \ldots,\, X_n = i_n \mid X_0 = i_0)
= P(X_n = i_n \mid X_{n-1} = i_{n-1})
\; P(X_{n-1} = i_{n-1} \mid X_{n-2} = i_{n-2})
\; \cdots \;
P(X_1 = i_1 \mid X_0 = i_0),
```

即一条状态序列（state sequence）的条件概率，等于沿此序列各相邻状态之间的转移概率（transition probabilities）逐项乘积。

从图形上看，一条状态序列（state sequence）可以等同于转移概率图（transition probability graph）中一列被依次遍历的弧（arcs）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一页给出 Markov chain（马尔可夫链）概率的 product form（积性形式）：一条状态序列的 joint distribution（联合分布）中某个样本点的概率，等于 initial probability（初始概率）乘上沿途每一条 transition probability（转移概率）的连乘积。式子本身很短，但两个成分必须分清——chain rule（链式法则）是恒等式，对任何随机变量序列都无条件成立；Markov property（马尔可夫性质）是额外的压缩假设，它才是把「一长串高维条件概率」变成「一串一步条件概率」的真正原因。二者混为一谈，就会误以为 product form（积性形式）是概率论的一般定理，而事实上它只对链成立。
>
> 第一性原理：joint distribution（联合分布）住在一个维数极高的单纯形里，degree of freedom（自由度）的数量随序列长度指数增长；马尔可夫假设把它压到「initial distribution（初始分布）的有限个参数加 transition matrix（转移矩阵）每行的有限个参数」，总量与序列长度彻底脱钩。这就是为什么链是「可学的」：参数从天文数字降到可以计数的量级。这也揭示了统计建模里所有假设的共同功能——用一个小参数族去近似一个巨大的分布族，用偏差换可估。压缩当然不是免费的，代价是任何超出「只看上一状态」的相关性都被抹平；真实数据的相关性一旦跨越两三个时间步，链就会系统性低估 long-range structure（长程结构）。
>
> 图形语言是这条式子的第二张脸：一条状态序列等于 transition probability graph（转移概率图）上一列依次被遍历的 arc（弧），序列的概率等于这列弧的权重之积，任意 event（事件）的概率等于构成该事件的全部 path（路径）的概率之和。这把「概率」翻译成了「加权路径计数」——6.042J 里 adjacency matrix（邻接矩阵）的幂，数的是 path 条数，这里换成了路径权重之和。更值得注意的是形状：与这里的递推式严格同形的是 CLRS 25.1 的「至多 $m$ 条边的最短路」EXTEND-SHORTEST-PATHS——两个把步数封顶的矩阵相乘、一层一层往外推；差别只在 semiring（半环），最短路在 min-plus semiring（最小加半环）里做，路径概率在 sum-product semiring（求和乘积半环）里做。而 CLRS 25.2 的 Floyd–Warshall 是另一条 DP 路线：它按「允许使用前 $k$ 个中间顶点」分阶段，递推里换的是中间顶点而不是边数，因此它不是 matrix power（矩阵幂）。同一个「剥掉最后一步、对中间点求和」的归纳，换一个代数结构就换掉整个应用领域，这是离散数学里最可迁移的一招。
>
> 跨课程连接：实分析里 product measure（乘积测度）的构造与之同构——有限维乘积空间上的 measure（测度）由各坐标的 marginal measure（边缘测度）与逐层 conditional measure（条件测度）拼接起来，Kolmogorov 的 extension theorem（扩张定理）不过是把这种拼接推到可数无穷维；本页的连乘式正是它的有限版本，而且因为 state space（状态空间）有限，交换求和与极限、交换乘法与求和这些操作全都无需附加条件，这是有限维带来的奢侈。
>
> 反例说明边界在哪里。第一种：transition probability（转移概率）依赖时间，即 time-inhomogeneous chain（非齐次链），连乘式仍然成立，但每一项要带时间下标，matrix power（矩阵幂）的把戏立刻失效——两次转移用的矩阵不同，两个乘积一般不相等，因此「转移矩阵的 $n$ 次幂」不再代表任何东西，你必须保留全部中间矩阵。第二种：记忆更长，若下一步还依赖前两步，连乘式里每项都要换成二阶条件概率，product form（积性形式）的结构随即崩塌。第二种反例恰好反证了「只看现在」这一条在整章中的承重地位——它不是便利的近似，而是让连乘能够闭合的唯一支点。

---

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页中段若干过渡文字（如 "…we have…models. In…"、"So the state $X_0$ is…" 及其前后衔接）在 OCR 中被打散成碎片，仅能辨认出零散短语；上方马尔可夫性的支解证法、图形解释与末尾「规定初始状态概率律」为按下行文意的连贯转写。以下尾部一小段（涉及具体概率计算）正文在 OCR 中残损严重，仅左侧状态序列字面可辨。</span>

---

关于我们的状态序列，需要对**固定初始状态的条件化（conditioning on a fixed initial state）**给出说明。要对整个过程有一个完整的概率描述，我们还需要为初始状态 $X_0$ 规定一个概率律（probability law），即一组初始概率（initial probabilities）$P(X_0 = i)$（针对所有状态 $i$）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本页补上了 Markov chain（马尔可夫链）的第二个组件：一条链的完整规格是「initial distribution（初始分布）加 transition probability matrix（转移概率矩阵）」，二者缺一不可。Markov property（马尔可夫性质）只约束相邻两步之间的关系，它是局部条款；它管得了「从 i 走一步去哪儿」，管不了「凭什么从 i 出发」。全局的概率律需要一个出发点，这正是 initial probabilities（初始概率）的职责所在。
>
> 第一性原理：给定 initial state（初始状态）取定某个 i，我们得到的是一条「以 i 起始」的条件链；无条件的链，就是把这些条件链按 initial distribution（初始分布）做的 mixture（混合）。用测度论的话说，这是一次 disintegration（测度分解）：一族条件概率测度配上一个 marginal measure（边缘测度），重新拼回原测度。实分析里「先对条件期望、再对条件变量取期望」的两层积分，与这里是同一件事的两种写法——整条链的概率律，就是把「先走哪条链路」与「在链路上怎么走」两层随机性叠起来。
>
> 动力系统一侧的对照极为直接：线性系统的下一步等于矩阵乘状态，解是矩阵的幂作用于初值；本课把分布写成行向量右乘，解是 transition probability matrix（转移概率矩阵）的幂作用于 initial distribution（初始分布）。两套写法只差一次 transpose（转置）——概率的习惯是「状态写在左边」，线性代数的习惯是「状态写成列」，转置一下即可对齐。记住这一点，18.06 里关于矩阵幂的一切结论，包括对角化、幂的收敛速率由第二大特征值决定、以及主特征向量的极限形状，都可以原样搬过来，不必重新推导。
>
> 一个必须分清的层次：initial distribution（初始分布）对长期行为的影响有多大，取决于链的结构，而不是笼统的「很快被遗忘」。若整条链只有一个 recurrent class（常返类）且非周期，初始分布的影响随时间指数衰减，最终所有起点都收敛到同一个 invariant distribution（不变分布）；但若链有多个 recurrent class（常返类），初始分布决定你最终落进哪一个——这个影响永不清零，因为类与类之间没有 positive probability（正概率）的通路。这也说明后面「状态分类」不是纯技术细节：它决定了「初始条件重不重要」这个建模问题的答案。
>
> 命名模板：initial（初始）一词强调的是时刻零的单一性——整条轨道上只有这一刻由外部指定，此后一切被转移矩阵接管。这与 finite state machine（有限状态机）的「初始状态加转移函数」是同一种设计哲学，也与 dynamic programming（动态规划）的「基例加递推式」完全对应：基例错了，整张表都错，而递推式再漂亮也救不回来。
>
> 反例：把 stationary distribution（平稳分布）当成 initial distribution（初始分布）来用，是最常见的混淆。二者数值上可能相同，语义上完全不同——初始分布回答「从哪儿出发」，stationary distribution（平稳分布）回答「长期停在哪儿」，前者是方向盘，后者是终点。只有当过程已经处于稳态时两者才重合；把稳态当作初值，等于假设「过程已经跑过无穷长时间」，任何关于「多少步之后趋于稳定」的结论都会失真。本页那个具体序列正是用来打断这种幻觉的：它给出前几步的取值，把「起点」与「长期位置」硬生生摆在同一条时间轴上，让人看得见两者并不是同一件事。

作为计算说明，考虑如下一条具体序列（其右侧概率数值在本页 OCR 中残损严重，未能识别，故不臆造）：对

```math
P(X_0 = 2,\, X_1 = 2,\, X_2 = 2,\, X_3 = 3,\, X_4 = \cdots)
```

这一类序列，我们将其概率表达为相应初始概率与各步转移概率之积；一旦给定初始概率律与转移概率矩阵，整条状态序列的概率便由此完全确定。

---

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末尾 "…there is no…to…a…of…" 等零散文句损毁，无法还原整句；以上按 §7.1 论述脉络做了忠实于术语的衔接性转写，未补充任何未见于原义的数值或结论。本页结束于「为初始状态 $X_0$ 规定概率律」这一定讨论点，下一页预计转入 n 步转移等相关论述。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p354）</span>
<!-- ===== PDF p354 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

<span style="color:#c0392b;">**§7.1　离散时间马尔可夫链（Discrete-Time Markov Chains）**</span> — <span style="color:#00838f;">**n 步转移概率（n-Step Transition Probabilities）**</span>

许多马尔可夫链问题都需要计算在**当前状态（current state）**给定时，某个未来时刻系统所处状态的概率分布。这个概率分布由 **n 步转移概率（n-step transition probabilities）** 刻画，其定义为

```math
T_{ij}(n) = P( X_n = j \mid X_0 = i ).
```

用文字来说，$T_{ij}(n)$ 是在当前状态为 $i$ 的前提下，$n$ 个时间周期之后状态为 $j$ 的概率。它可以用下面这条被称为 **查普曼-柯尔莫哥洛夫方程（Chapman-Kolmogorov equation）** 的基本递推式来计算。

<span style="color:#00838f;">**[定义] n 步转移概率的查普曼-柯尔莫哥洛夫方程（Chapman-Kolmogorov Equation for the n-Step Transition Probabilities）**</span>

n 步转移概率可通过递归公式生成：

```math
T_{ij}(n) = \sum_{k=1}^{m} T_{ik}(n-1)\, p_{kj}, \qquad \text{对所有 } n \ge 1 \text{ 及所有 } i, j,
```

并以 $T_{ij}(1) = p_{ij}$ 为出发起点（starting with）。

> <span style="color:#7f8c8d;">[原页此处 OCR 中断] 源页在 "starting with" 之后即被页脚截断/换页，递推的初值条件按上文语境应为 $T_{ij}(1) = p_{ij}$（即一步转移概率矩阵），此为合理性补全，未在原页直接显示；如需最严格原文请回查原书页 345 或下一页。</span>

为验证上述公式，我们如下运用**全概率定理（total probability theorem）**：

```math
P( X_n = j \mid X_0 = i )
= \sum_{k=1}^{m} P( X_{n-1} = k \mid X_0 = i )\, P( X_n = j \mid X_{n-1} = k,\, X_0 = i )
= \sum_{k=1}^{m} T_{ik}(n-1)\, p_{kj};
```

参见图 7.5（Fig. 7.5）的示意。这里我们已用到了**马尔可夫性质（Markov property）**：一旦在 $X_{n-1} = k$ 上取条件，那么对 $X_0 = i$ 的条件作用就不会影响下一步到达 $j$ 的概率 $p_{kj}$。

我们可以把 $T_{ij}(n)$ 看作一个二维数组的第 $i$ 行、第 $j$ 列元素，这个数组称为 **n 步转移概率矩阵（n-step transition probability matrix）**。图 7.6 和图 7.7（Figs. 7.6 and 7.7）分别给出了某些情形的 n 步转移概率 $T_{ij}(n)$……

> <span style="color:#7f8c8d;">[原页此处 OCR 截断] 正文在图 7.5、7.6、7.7 的列举处因页脚被截断，具体图示说明于次一页续接。</span>

> <span style="color:#7f8c8d;">[脚注] 熟悉矩阵乘法的读者可能会认出，查普曼-柯尔莫哥洛夫方程可以表达如下：n 步转移概率矩阵 $T_{ij}(n)$ 由 $(n-1)$ 步转移概率矩阵 $T(n-1)$ 乘以一步转移概率矩阵得到。因此，n 步转移概率矩阵就是转移概率矩阵的 $n$ 次幂。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Chapman–Kolmogorov equation（查普曼–柯尔莫哥洛夫方程）是本章第一句把 abstract definition（抽象定义）变成 computable recursion（可计算递推）的式子。它的分量形式值得抄在纸上念一遍：n-step transition probability（$n$ 步转移概率）等于「先经某个 intermediate state（中间状态）走 $n-1$ 步、再走一步」对全部中间状态的求和。一项未知、一项已知，未知被降阶一次，递归就可以落地。
>
> 第一性原理是两把锁扣在一起。第一把是 total probability theorem（全概率定理）：按「第 $n-1$ 步站在哪个状态」把事件分情形，这一族事件互斥且穷尽，求和恒成立，与链本身的性质无关。第二把才是 Markov property（马尔可夫性质）：条件概率里本该还挂着「从 $i$ 出发」这个条件，马尔可夫性把它删掉，求和项才退化成「前一段的概率乘最后一步的 transition probability（转移概率）」这种可以相乘的形状。少任何一把锁，方程都不成立——少了全概率，没有求和；少了马尔可夫，求和项里还套着无法拆开的高维条件。
>
> 矩阵形式是这条方程的第二张脸：把 n-step transition probability（$n$ 步转移概率）排成矩阵，递推式就变成「$n$ 步矩阵等于 $n-1$ 步矩阵乘一步矩阵」，于是 n-step transition probability matrix（$n$ 步转移概率矩阵）就是 transition probability matrix（转移概率矩阵）的 $n$ 次幂。这一步转换的价值在于，递推的每一步是一次矩阵乘法，而 matrix power（矩阵幂）可以用 binary exponentiation（平方技巧）加速，把线性的乘法次数压到对数级的 $O(\log n)$——这是 CLRS 里幂运算的标准手法，也是 18.06 里「算矩阵幂靠 diagonalization（对角化）」在本章的入场券。
>
> 算法侧的对应干净得几乎不用解释：这就是 dynamic programming（动态规划）的 Bellman equation（贝尔曼方程）。把「长度为 $n$ 的路径权重之和」当作 state value（状态值），递推式做的事是「剥掉最后一条边，对所有 predecessor（前驱）求和」——与 CLRS 里最短路、edit distance（编辑距离）的递推是同一个套路：optimal substructure（最优子结构）加无后效性。无后效性在概率语言里就是 Markov property（马尔可夫性质），子结构在图语言里就是「路径的前缀仍然是一条路径」。这里要小心一个流行的类比：与矩阵幂严格同形的是 CLRS 25.1 的「至多 $m$ 条边最短路」——它就是 min-plus semiring（最小加半环）里的 matrix power（矩阵幂）；而 Floyd–Warshall 换的是「允许经过的中间顶点」这个阶段参数，不是步数，属于另一条 DP 路线，只是恰好在同一个 semiring（半环）里做加法与取小。把两者混为一谈，就会误以为 FW 是某个矩阵的幂。
>
> 命名与归属：这条方程由 Sydney Chapman 与 Andrey Kolmogorov 各自独立得到，前者在 1928 年研究 Brownian motion（布朗运动）时写下连续版本（部分二手资料记 1926，未核实一手文献），后者在 1931 年的《概率论中的解析方法》一文里把它系统化。两个姓氏恰好既合字母序（C 在 K 前）也合年代序（1928 在 1931 前），这只是巧合，不必从中读出「先有具体计算、后有一般理论」的剧本——独立性本身已经说明谁先写下并不重要。
>
> 反例：time-inhomogeneous chain（非齐次链）里每一步用的是不同的矩阵，$n$ 步矩阵成了各步矩阵的有序乘积，而 matrix multiplication（矩阵乘法）不满足 commutative law（交换律），于是「矩阵的 $n$ 次幂」这个说法直接失效。这不是细节瑕疵，而是递推结构的崩塌——你必须保留全部中间矩阵，存储与计算代价都随之上涨。第二个反例是 infinite state space（无穷状态空间）：求和变成级数，把有限和换成级数需要 monotone convergence（单调收敛）或 dominated convergence（控制收敛）的许可，实分析里的这些定理在这里不再是装饰，而是方程能否成立的前提；有限状态空间之所以让人省心，正因为这些麻烦全被「只有有限项」这件事挡在门外。
<!-- ===== PDF p355 ===== -->

> <span style="color:#7f8c8d;">[页首 OCR 提示] 本页为第 7 章前文（§7.1 尾段关于 n 步转移概率公式的推导与举例）的**延续**；页尾出现新节标题「7.2 Classification of States（状态分类）」。本页 OCR 损坏极其严重，字句大量碎行/乱码，下面按识别出的语义尽力复原。凡无法辨认之处均以灰注释标注，**未臆造任何数值或公式**。</span>

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span> — 承上前文（§7.1 内容延续）

<span style="color:#00838f;">**[定义] §7.1 尾段（续）——n 步转移概率公式的推导**</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**（承接上一页的推导）**</span> 这里推导 7.5 所给 [n 步转移概率] 的公式：概率 $T_{ij}(n)$ 表示在时刻 $n$ 处于状态 $j$（state $j$）的[概率]，它等于从初始状态出发、经各种不同途径（different ways）在时刻 $n$ 到达状态 $j$ 的各项概率[之和]。

```math
T_{ij}(n) = \sum_{k} T_{ik}(n-1)\, p_{kj}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式按残缺片段「$…_{ik}(n-1) P_{kj}$」重建，为标准的逐步递推关系（第 $n$ 步处于 $j$ = 第 $n-1$ 步处于某中间状态 $k$ 后经一步转移 $p_{kj}$）。上方 T_{ij}(n) 的求和限、以及「7.5 公式」的确切编号，OCR 均不可辨认。</span>

接着正文引入两个尚未给出的结果（编号互相对比，展示不同的长期行为）：

- 参见 <span style="color:#7f8c8d;">图 7.6</span>：我们看到这个极限（this limit）**不**依赖于初始状态 $i$（initial state）。[原页此... OCR 损坏：相关段落「Furthermore, the probability … , but over time this …」多处乱码，语义为：某一[到达/返回]概率，但随着时间的推移该[量]…… ]。
- 参见 <span style="color:#7f8c8d;">图 7.7</span>：我们看到一种性质上不同的行为（a qualitatively different behavior）：[该[极限] 依[赖]于初始状态 $i$。 [原页此处 OCR 损坏：该句后半残缺。「Here, we …」段仅识别到零散词，语义为：这里我们……] ]

接着讨论「吸收态」：

<span style="color:#00838f;">**[定义] 吸收态与吸收行为（absorbing states，续讲）**</span>

这里我们考虑被称作「吸收型」（absorbing）的状态：—旦进入 [这样的状态便再难离开]。存在这样的状态，它们使得 [某一类] 状态 [在某时刻以后] 的概率 [为] 零，[并且在] 某种意义 [下] 它们是被无限 [次访问] 的…… [原页此处 OCR 损坏：此句断句支离破碎，仅能复原关键词，数字符号（如孤立的 $1,4,2$）无法归属，作占位保留。]

随后引出两个蜘蛛捕蝇（捕获飞蝇）的例子：

<span style="color:#2471a3;">**[example]**</span> **[两蜘蛛与一只飞蝇（two spiders and a fly）· 捕蝇，续]** 飞蝇被两只蜘蛛之一捕获（capture of the fly by one of the two spiders）。给定足够的时间（Given enough time）：几乎可以肯定某 [个] 吸收状态最终 [会被进入]。

由此引出下文：

相应地（Accordingly），[处于某] 状态的 [长期] 概率……我们从这里开始 [对状态进行分类]。这些例子 [说明]……这正是 [下一节] 的主题（this is the subject of the [next section]）：

---

<span style="color:#c0392b;">**7.2　状态分类（Classification of States）**</span>

<span style="color:#2471a3;">**[section]**</span>本节的[主题是]：对[状态空间中的]状态进行[分类]，尤其是[区分那些会反复访问与不会被反复访问的状态]。 [原页此处 OCR 损坏：本节开头仅识别到「states, particularly …」，正文首句残缺，仅作如上大意复原。]

> <span style="color:#7f8c8d;">[页脚 OCR 提示] 本页结尾恰好进入 §7.2 开头，其后内容承接至下一页（p356）。顶部碎片（孤立数字、符号 $\Sigma_k$、时间下标 $n$ 等）均因 OCR 打散无法可靠还原，已按其上下文归位或标注残缺，不补编数值。</span>
<!-- ===== PDF p356 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）—— §7.2　状态分类（Classification of States）（续）</span>

本页承接前页：页首先收束 §7.1 中例 7.1（"及时 / 滞后" up-to-date/behind 的两状态马尔可夫链）及其图 7.6 的相应讨论，随后转入 §7.2 状态分类的开头部分，故标注「续」。

> <span style="color:#7f8c8d;">页首冲突处 OCR 断裂严重，以下按原文语义重申（见灰色注释处）。</span>

对图 7.6（Figure 7.6，即 "up-to-date/behind" 例子的 $n$ 步转移概率，$n$-step transition probabilities）所展示的情形，我们观察到：当 $n \to \infty$ 时，$n$ 步转移概率 $T_{ij}(n)$ 收敛到一个<b>不依赖于初始状态（initial state）$i$</b> 的极限（limit）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上句之后的过渡段旨在说明：有些链中，各状态被访问的次数 / 频率随 $n$ 增大趋于与初始状态 $i$ 无关的稳定值，而另一些链则并非如此（"not be the case"）。该断行零散，无法完整复原原文措辞。</span>

在本节中，我们将注意力集中于（focus on）一条马尔可夫链中各状态被访问的频率（frequency with which states are visited），并希望对状态加以分类（classify the states），进而刻画这一极限行为在何种情况下出现。

**可达状态（accessible states）。** 我们说状态 $j$ 从状态 $i$ **可达（accessible）**，指的是：对某个 $n$，$n$ 步转移概率（$n$-step transition probability）$T_{ij}(n)$ 为正；也就是说，从 $i$ 出发，经过若干时间周期之后，有正概率（positive probability）处于状态 $j$。等价地，这意味着从 $i$ 到 $j$ 存在一条正概率的可能路径（possible path），即如下状态对序列

```math
(i,\ i_1),\ (i_1,\ i_2),\ \ldots,\ (i_{n-1},\ j),
```

其中每一步对应一次具有正概率的转移，序列起始于 $(i, i_1)$，终止于 $(i_{n-1}, j)$。

记 $A(i)$ 为从状态 $i$ 可达的所有状态所构成的集合（the set of states accessible from $i$）。若对 $A(i)$ 中的每一个状态 $j$ 都成立相应的可达条件 [下方断行残缺]，则从 $i$ 出发，我们只能访问那些属于 $A(i)$ 的状态 $j$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> accessible set（可达集合）是本章被低估得最厉害的一件工具：它把「概率意义上的能走」翻译成「图论意义上的有路」，一次性扔掉了全部数值信息。定义只看一件事——存在某个步数使 n-step transition probability（n 步转移概率）为正。注意这里的量词是「存在」，不是「很大」：概率 0.001 与 0.999 在可达性判据里完全等价，因为只要不是零，路就通。
>
> 第一性原理：正概率的路径，其概率是沿途各步正概率的乘积，而有限个正数相乘仍然为正；反过来，若某步为零，整条路径的概率即为零。于是「某步转移概率为正」与「存在一条每步 transition probability（转移概率）都为正的弧序列」互为充要条件。丢掉数值、只保留「是否为正」，等价于把 transition probability matrix（转移概率矩阵）的每个正元素换成 1、零元素留着，得到一个 adjacency matrix（邻接矩阵）；整条链随即退化成一张有向图，概率论暂时退场，图论接手。
>
> 这个粗化之所以值得，是因为本章的长期行为全部由 support（支撑）决定，与具体数值无关。recurrence（常返）、transience（暂态）、闭集、不可约、absorbing state（吸收态）——这些概念的判据里只出现「是否为正」，不出现「多大多小」。数值决定速率，结构决定命运。这句话可以当作读整章的口诀：先看骨架，再算皮肉。也正是它让后面那些「告诉你怎么算稳态概率」的长篇推导变得可以忍受——因为分类早就在纯图上做完了。
>
> 值得补一句「为什么支撑决定一切」的形式化理由：任意有限步的转移概率都能写成沿路径各边概率的乘积，而乘积的正负完全由因子决定——只要有一个因子为零，整项即为零。于是「是否为正」是逐条路径独立判定的布尔事件，而最后那次对路径的求和只可能把零变成正，不可能把正变成零。这就是把概率矩阵换成 adjacency matrix（邻接矩阵）不会丢失任何定性信息的严格原因：定性信息住在乘积的零模式里，而零模式正是图。
>
> 算法侧：求 accessible set（可达集合）就是从 i 出发做一次 breadth-first search（广度优先搜索），代价与状态数、弧数成线性。也可以取 adjacency matrix（邻接矩阵）的布尔幂之并，因为 m 个状态的图上若存在路径，必存在长度不超过 m 减 1 的简单路径。这个上界是有限状态空间专有的福利；一旦状态可数无穷，路径可以任意长，「m 减 1」直接失效，论证得从头另起。
>
> 跨课程连接：CSAPP 里的指针图与 garbage collection（垃圾回收）完全同构——标记清除算法要判定的正是「从根集合出发是否可达」，不可达的对象被回收，那个可达集合与本页的集合同样是「从起点能摸到的一切」，只是权重从概率换成了「是否存在指针」。6.042J 的 strongly connected component（强连通分量）则是它的对称化版本：从 i 能到的集合，与能回到 i 的集合，二者之交正是 i 所在的 strongly connected component（强连通分量）；本章后面的「常返类」，就是在这个交集上加一句「以概率 1 反复返回」。
>
> 反例与陷阱：可达关系不对称，这是全部技巧的来源，也是最容易踩空的地方。j 能从 i 到达，完全不蕴含 i 能从 j 到达；正是这种单向性让「有去无回」成为可能，也正是它让暂态的判定可以目测完成。第二个陷阱在步数上：只盯一步转移概率会漏掉长路，Example 7.2 里苍蝇一步到不了的位置，走十步之后可能就以 positive probability（正概率）到达。可达性必须对「某个步数」量化，钉死在第一步上，是把「存在」当成了「立刻」。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 以上句子涵盖「从 $A(i)$ 内任一状态 $j$ 再可由 $j$ 到达 $A(i)$ 全体」以及「闭集 / 不可约（closed set / irreducible）」性质的完整表述，此处 OCR 被打散为单词碎片，无法完整复原，未臆造原文；如需逐字原文请回查原书 p356。</span>

若状态 $i$ 从自身出发、在给定足够多步数之后，能把所有属于 $A(i)$、由 $i$ 可达的状态都访问无限多次（an infinite number of times），则称状态 $i$ 是**常返（recurrent）**的；反之，若 $i$ 不是常返的，则称状态 $i$ 是**暂态（transient）**的。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「常返 / 暂态」的严格定量定义（"从 $i$ 出发以概率 1 无限多次回到状态 $i$"）在本页句中被断行打散，本段的描述性复述据片段合理补全；页尾 "…… if it is not recurrent. Thus, a state i is transient ……" 落款相对完整。原文此处还提到对这些断言所作的更严谨论证见章末习题（end-of-chapter problems for a rigorous proof），此句亦残缺。</span>

因此，状态 $i$ 是暂态的当且仅当（if and only if）它不是常返的。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> recurrent（常返）与 transient（暂态）把状态空间一分为二，定量内核只有一句话：常返状态从自身出发，以概率 1 被无限多次访问；暂态状态只被访问有限多次，此后一去不回。两种说法看似在数次数，实际在谈「返回」这件事的必然性——次数是结论，返不回来才是原因。
>
> 第一性原理：判断常返与否，不要数访问频次，要问「从它走出去的每一条路，是否都能把它带回来」。accessible set（可达集合）在这里派上用场：若存在某个 j 从 i 可达、而 i 从 j 不可达，这条路一旦踏上就回不了头，i 便只能被访问有限多次，因而是 transient（暂态）；反之，若 accessible set（可达集合）中的每个状态都能回到 i，那么无论岔到哪条路上都能折返，i 就是 recurrent（常返）的。注意这个判据一次数值都没碰，只用了「能否」——这正是上一页把概率粗化成布尔结构的目的。
>
> 等价刻画有两种常见形态，值得并排记住。其一是概率形态：在起点为 i 的条件下，访问 i 的次数为无穷的概率等于 1。其二是级数形态：各步返回 i 的概率之和发散。两者的等价不是形式把戏——把时间轴切成「每次返回 i 之后重新开始」的若干块，级数发散意味着无限次重新尝试，而 Borel 与 Cantelli 的名字在这里会出场两次：第一引理给出「概率之和有限则只发生有限次」，第二引理给出「概率之和发散且块间独立则必然发生无限次」。教材把严格论证推到章末习题，正因为这里需要「块间独立」这一条不那么显然的结论，而它其实是 Markov property（马尔可夫性质）的加强版——strong Markov property（强马尔可夫性质）的雏形：在一个停时上「重新开机」，链的规律不变。
>
> 书上这里的定义值得单独说一句：它要求的是「accessible set（可达集合）里的每一个状态都被访问无限多次」，而不是标准教材常写的「i 自身被无限多次访问」。两者等价，理由就在结构上——若 i 常返，则对 accessible set（可达集合）里的每个 j 都有 j 能回到 i，于是 i 与 j 互达，i 每回来一次就有正概率顺路去 j；而访问 i 无限多次这件事已经由常返保证，稠密地散布在时间轴上，于是每个 j 都会被命中无穷多次。这不是加强条件，而是把「常返」这个单点性质摊开成一族的等价表述。
>
> 结构性结论：常返与暂态是 class property（类性质），同一个 strongly connected component（强连通分量）里的状态同进同退，不会一半常返一半暂态。于是「给状态分类」实际是「给状态空间做分解」——把图拆成若干个互达的族，族内常返，通往族外的入口都属于 transient（暂态）。这与 6.042J 里把有向图分解成 strongly connected component（强连通分量）、再把缩点结果看作有向无环图的做法在结构上是同一件事：常返类正是那些「没有出边」的强连通块，一旦进入就再也出不去。
>
> 反例最能校正直觉：一维对称 random walk（随机游走）在整数网格上以概率 1 返回原点，但期望返回时间是无穷大——这类状态称为 null recurrent（零常返），它常返却不是 positive recurrent（正常返），因此根本不存在 invariant distribution（不变分布）。三维及以上的对称 random walk（随机游走）反而是 transient（暂态）的，返回概率严格小于 1；这条由 Pólya 在 1921 年给出的「维数决定常返性」的结论，是本课程之外最著名的反直觉案例。回头看 Example 7.2 的蜘蛛与苍蝇：边界位置 1 与 m 是 absorbing state（吸收态），当然常返；中间的 2 到 m 减 1 看似被反复踩过，却全部是 transient（暂态）。走得多不等于回得来——这条区分是本页最锋利的一刀，也是把「频率」与「可达」两个直觉分开的唯一办法。
<!-- ===== PDF p357 ===== -->

<span style="color:#c0392b;">**§7.2　状态分类（Classification of States）—— 续接**</span>

本页承接上一页（p356），正文无新节、无新标题，属第 7.2 小节「状态分类」的延续，故标题作「（续接）」。本页集中在：n 步转移概率（n-step transition probabilities）收敛极限的观察、暂态（transient）与常返（recurrent）状态的判定逻辑、由常返状态构成的可达类，以及引入图 7.8（Figure 7.8）所给的转移概率图（transition probability graph）分类示例（其状态判定延续到下一页 p358）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 OCR 全面劣化，大量行被切成单词碎片（如 "7.7:", "Tij(n) 的笔画碎为 r T i 2/ Tz 3"、行末被换页符截断）。下列译文按教科书原意与可辨认片段重组，作为忠实还原；凡涉及具体数值、图内坐标或无法确定的确切措辞均不作臆造，以原书 p357 为准。</span>

---

<span style="color:#2471a3;">**[观察]**</span> <span style="color:#00838f;">**图 7.7：n 步转移概率的极限**</span>

图 7.7（Figure 7.7）展示了从某初始状态 $i$ 出发的 n 步转移概率（n-step transition probabilities）。这些概率是用以刻画马尔可夫链趋近行为的量。我们观察到，随着 $n$ 增大，$T_{ij}(n)$ 收敛到某个极限，但该极限并不一定与所考察的状态无关；尤其值得注意的是，对某些状态而言，对应的可达概率（probability of reach-…）会随 $n$ 增大而趋于零。

在本例中，进入状态 2 或 3（{2 or 3}）的概率 $T_{i2}(n)$ 与 $T_{i3}(n)$ 会随着 $n$ 的增大而趋于零。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图 7.7 的说明被 OCR 读成 "shows n-step transition probabilities … 7.2. These are the … from state i … converge to a limit, but the limit … note that the … of reach-… probabilities … state …"，图示曲线数值与横纵轴坐标均无法识别，故此处仅保留可确认的定性结论，未填写任何具体极限值。</span>

---

<span style="color:#2471a3;">**[定义/讨论]**</span> <span style="color:#00838f;">**暂态（Transient）状态**</span>

由上一页引入的可达集合（set $A(i)$，即从状态 $i$ 可达的全部状态之集）出发，若存在某个状态 $j \in A(i)$ 使得 $i \notin A(j)$，则状态 $i$ 称为**暂态（transient）**。也就是说，从 $i$ 出发能以正概率到达某个 $j$，但从 $j$ 却无法返回到 $i$。

一旦过程进入这样的 $j$（the state enters such a $j$），给定足够长的时间，这件事终会发生（given enough [time], … this will happen）；而进入 $j$ 之后，由于 $j$ 到不了 $i$，过程便无法再回到 $i$。因此，状态 $i$ 只会被访问有限多次（will only be visited a finite number of times），此后便不再被访问。于是：一个暂态状态只会被访问有限多次，故若状态 $i$ 非暂态（即为常返，recurrent），则它会以概率 $1$ 被无限多次访问。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一段论证值得逐句拆开，因为它是「工程师直觉」与「严格证明」之间的分水岭：只用「存在某个 $j$ 从 $i$ 可达、而 $i$ 从 $j$ 不可达」这一条纯结构信息，居然推出了「$i$ 只被访问有限多次」这个概率结论。从结构跨到概率的这一步，是整章第一次出现，也是后面 absorption probability（吸收概率）、长期频率、limit distribution（极限分布）等全部结果的模板。
>
> 第一性原理有两条腿。第一条是「迟早发生」：只要那条通往 $j$ 的路以 positive probability（正概率）存在，并且过程可以反复尝试，那么失败无穷多次的概率为零——这正是 geometric distribution（几何分布）的尾部衰减，也是 Borel 与 Cantelli 第二引理的直观形态。这里的关键量化是「每次尝试的成功率有正的下界」：state space（状态空间）有限意味着最小的 positive probability（正概率）是一个正数，试验再多，成功率也不会缩到零；一旦状态空间可数无穷，这个下界消失，同样的论证随即失效，null recurrent（零常返）正是它失效的现场。第二条是「一旦失守就永久失守」：$i$ 不属于 $j$ 的 accessible set（可达集合）是一个布尔事实，与任何数值无关，所以过程踏进 $j$ 之后再也回不到 $i$——这不是「很难」，而是「不可能」。
>
> 两条腿合起来才够用。只有「迟早发生」而没有「永久失守」，回到 $i$ 之后一切照旧，次数并不会被截断；只有「永久失守」而没有「迟早发生」，过程可能永远不踩那条路，结论也就落空。Markov property（马尔可夫性质）在这里以「块间独立」的面貌出场——每次回到 $i$，过程就像重新开机，此前的尝试不改变之后的成功概率。这一步其实是 strong Markov property（强马尔可夫性质）的朴素版本，教材把它推到习题里，但使用它需要的只是「conditioning（条件化）之后规律不变」这一条直觉。
>
> 定量副产品值得顺手记住：若每次尝试的失败率不超过某个严格小于 1 的常数，则第 $k$ 次访问的概率按几何速率衰减，于是 expected number of visits（期望访问次数）有限。把「以概率 1 有限次」升级成「期望有限」，需要的正是 geometric distribution（几何分布）的求和公式：若概率按 $\alpha^{k}$ 衰减，$\sum_k k\,\alpha^{k}$ 收敛，尾部衰减压得住总和。这里要提防一个流行的误配类比——CLRS 里的 amortized analysis（均摊分析）是确定性算法在 worst case 下的均摊，它既不含任何概率假设，也不谈 expected value（期望值），与本段做的「几何尾压求和」不是同一件事。本卷后面讲长期频率时还会强调这一点：概率意义上的平均需要 ergodicity（遍历性）与尾部的可积性，均摊分析只需要一段确定性的操作序列。把两者混为一谈，就会得出「均摊结论对随机算法自动成立」这种错误推论。
>
> 命名模板：transient（暂态）来自拉丁语动词 transire（意为「穿过」），其形容词形态强调「只是路过」；与它相对的 recurrent（常返）则是「跑回来」——前缀 re（意为「又」）接上 currere（意为「跑」）。两个词的词根已经把判据写清楚了——一个只在时间轴上打一个照面，另一个必定折返。
>
> 反例与常见误读有三个。第一，把「访问次数有限」听成「停留时间短」——transient（暂态）说的是次数而非单次时长，每次停留都可以很长，甚至无界，但次数有限。第二，把「走得多」当成「回得来」：苍蝇与蜘蛛那个例子里，中间那些位置被反复踩过许多次，看上去常来常往，却全是 transient（暂态），因为终究会被某只蜘蛛吃掉；观察窗口越长，越容易误判。第三，拿单条轨道当证据：某条轨道上恰好在第 100 步之后再没回到 $i$，证明不了 $i$ 是 transient（暂态）；transient（暂态）是「对全部轨道以概率 1」的断言，不是对某一条轨道的观察。三个误读共同指向一件事——概率的结论必须由概率论证给出，sample path（样本路径）只能提供线索，不能提供判决。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「暂态—常返」判据一段的原文（如 "that $i$ is transient if … / … is a state $j \in A(i)$ … from $j$ … this win happen … i cannot be …"）被 OCR 切碎并缺失若干单词（win 应为 will）；译文按教科书对该判据的标准陈述重组，未臆造数值。</span>

---

<span style="color:#2471a3;">**[性质]**</span> <span style="color:#00838f;">**常返状态的可达类（Accessibility classes of a recurrent state）**</span>

对于常返状态（recurrent state）$i$，数学上对一切属于 $A(i)$ 的状态 $j$ 均有

```math
A(i) = A(j),
```

这可由常返（recurrence）的定义直接看出。也就是说，$A(i)$ 中的全部状态都是常返的：它们彼此互达、构成一个类（a class，或简称 recurrence class）；而且从 $A(i)$ 中任一状态出发，都无法到达 $A(i)$ 之外的任何状态。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这句话的份量不在等式本身，而在于它把一种「单向」的关系补成了「双向」。accessibility（可达性）单独看只是 preorder（预序）：自反、传递，偏偏不满足对称。一个 preorder（预序）只能把状态空间切成一条条有方向的长链，切不出块。recurrence（常返性）在这里做的事，就是补上缺失的那个方向——于是链状结构坍缩成块状结构，这才是后面「分解成 recurrent class（常返类）」能够成立的全部理由。
>
> 第一性原理要看清「从 $j$ 必回 $i$」为什么是被迫的，而不是定义出来的。反设存在 $j$ 属于 $i$ 的可达集，而从 $j$ 回不到 $i$。$i$ 能到 $j$，意味着每次从 $i$ 出发落进 $j$ 都用一个有正下界的概率发生（状态有限保证这个下界是正数，不随试验次数趋零）；落进 $j$ 之后，游戏规则从 $j$ 重新起算，$j$ 到不了 $i$，就再也回不到 $i$。于是「某一次尝试失败」的概率是正的，而尝试可以无限次重复，所以「至少在某个时刻失败一次」的概率为一——这里只需一次就够：踏上 $j$ 之后回不来，$i$ 的访问序列从此被掐断，摧毁性的失败不需要重复发生，也不存在「回来再试一次」的第二次机会。这与 $i$ 常返（以概率一被无限次访问）直接冲突。这段推理只用到两件事：正概率的边永不失效、有限状态让最小正概率有正下界。丢掉有限性，结论立刻垮掉——infinite state space（无穷状态空间）里的 random walk（随机游走），可达却不再回来是常态。
>
> 等式两个方向都值得交代一遍。左边那半：$j$ 能到 $i$，$i$ 又能到可达集里任何一点，传递性给出 $j$ 也能到那些点。右边那半：$i$ 能到 $j$，$j$ 够得着的一切点也就被 $i$ 够得着。两向合起来，可见集完全相同。换成图语言重述：以类内任意一点为 source（源点）做一次 reachability search（可达性搜索），得到的 vertex set（顶点集）一模一样，也就说明类内不存在「能出去」的 arc（弧）。
>
> 三种刻画（互达、闭、常返）在此合流：互达是 equivalence relation（等价关系）的样子，闭是没有出逃路径，常返是不死在半路。三者任意两条能推出第三条，而这一命题补上的正是其中最不显然的一环——从「回不来会怎样」的概率论证，倒推出「闭」这个纯结构事实。这一步是整章的桥。
>
> 命名模板：class（类）一词来自拉丁语 classis（意为「等级」），本来是罗马人按财产给公民分的等级，后来数学借去专指「由某个判据切出的一批等价物件」——conjugacy class（共轭类）、homotopy class（同伦类）、complexity class（复杂度类）都是这个用法。说一个集合是 class（类），就意味着有一个判据把所有物件筛进互不相交的抽屉里。
>
> 跨课程：6.042J 里 equivalence relation（等价关系）的三条件与 partition（划分）互为表里，这里是同一个定理换了外衣；有向图上它的名字叫 strong connectivity（强连通），把每个类缩成一点得到的 condensation（凝聚图）是 directed acyclic graph（有向无环图），常返类恰好是其中没有出边的 sink（汇点）。CLRS 6.006 的 Tarjan algorithm（Tarjan 算法，1972 年发表于 SIAM Journal on Computing，第 1 卷第 146 页起）与 Kosaraju 算法都是 linear time（线性时间），所以判定常返不必解方程组，做一次强连通分解再看缩图出度即可——一个概率命题被降级成 graph algorithm（图算法）。18.06 的语言里，限制在单个常返类上的 transition matrix（转移矩阵）是 irreducible（不可约）的，不可约加上非负性正是 Perron 1907 与 Frobenius 1912 那条 Perron–Frobenius theorem（佩龙–弗罗贝尼乌斯定理）的适用条件，spectral radius（谱半径）一成为单重特征值，这就是「唯一稳态」的代数根。
>
> 反例与常见误读三条。第一，把可达集相等当成「所有可达集都相等」：只在 $i$ 常返时成立，$i$ 若是 transient（暂态），某个 $j$ 的可达集可能严格更大，等式当场失效。第二，以为「互达」单独就够成类：两个暂态可以互达，但它们没有把出口堵死，照旧会逃，可互达而不常返只是跳板。第三，以为类里的状态必须一步互通：判据用的是若干步正概率，图上是 path（路径），不是一条边。另有一处措辞要替读者点明：教材说「由常返的定义直接看出」，其实「直接」二字把上一段那套反复尝试的论证藏了起来，它并不比前一条命题更显然。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 该性质段原文（"Mathematically, for a recurrent state $i$, we have $A(i)=A(j)$ for all $j$ that belong to $A(i)$, as can be seen from … recurrence …"）部分行被打散（"a recurrent state, the set", "that states in A(i) are all", "from them", "no state" 等碎片），相等关系 $A(i)=A(j)$ 为可辨认核心，据此重组。</span>

---

<span style="color:#2471a3;">**[图]**</span> <span style="color:#00838f;">**Figure 7.8 —— 一个转移概率图（transition probability graph）的分类示例（源 OCR 作 &quot;7.8 provides an example of a transition probability graph&quot;，其中的 7.8 为图号而非例号）**</span>

图 7.8（Figure 7.8）给出一个转移概率图（transition probability graph）的实例，其中转移概率图中保留所有满足 $p_{ij} > 0$ 的有向弧（arcs），而不显示 $p_{ij} = 0$ 的弧。其状态集为 $\{1, 2, 3, 4\}$。

依可达判据观察该图：从状态 $1$ 出发，可达状态……（由状态 $1$ 出发的可达关系详见下图描述。）

由图 7.8 可见，状态 3 与 4（以及可能的其他状态）相互可达并共同构成一个类，而状态 1 自身也构成一个类。各状态的常返（recurrent）/ 暂态（transient）归属判定延续到下一页 p358。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图 7.8 图的文字说明被 OCR 打散（如 "7.8 provides an example of a transition probability … / … of 7.8, states 3 [and 4] … form a class, and state 1 itself also forms a …"），图中各节点间的弧线、环路与自环的准确方向无法从 OCR 辨认，故此处只给出可确认的定性与状态集合，状态 1 / 2 / 3 / 4 的具体判定排版下页（p358）。</span>

---

（本页内容在下一页 §7.2 处继续。）
<!-- ===== PDF p358 ===== -->

<span style="color:#c0392b;">**§7.2　状态分类（Classification of States）—— 续接**</span>

本页承接上一页，继续 §7.2 对状态（state）分类的讨论（页首无新节标题，故标「续接」）。此页核心内容包括：给定转移概率（transition probability）矩阵的例题与所得结论（返回态判据、把状态空间分解为常返类）、紧接着的续讲区段（OCR 严重损坏），以及收尾处把「给定暂态时进入某个常返类」与「一个常返类内的行为」这两类推迟到本节之后的小节（即 §7.3、§7.4 的 focus）的过渡段。

---

<span style="color:#2471a3;">**[图]**</span> <span style="color:#00838f;">**Figure 7.8（续）—— 状态分类判定：给定转移概率矩阵，判定各状态的归属**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「由状态 1（from state 1, the …）」及紧邻的早期转移概率矩阵描述残缺，无法准确识别完整的矩阵元素；下方结论依赖的判据与状态间可达关系详见原文（原书 7.2 节、页 358）。下列仅记录 OCR 中可辨认的核心判定。</span>

一个可达状态（accessible state）与自身门类一致，因此 $1$ 是常返状态（recurrent state）。由状态 $1$，……

状态 $2$ 出发可达状态 $1$、$3$ 和 $4$（States $1$, $3$, and $4$ are accessible from $2$），但 $2$ 无法由其中任何一个状态到达（$2$ is not accessible from any of them），因此状态 $2$ 是暂态（transient）。状态 $3$ 与 $4$ 彼此互达（accessible from each other），二者均为常返状态（recurrent）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一段是把图 7.8 读成状态分类的实操示范，它的价值不在于结论，而在于给出一条可以机械执行的流程。三步：先画出 transition probability graph（转移概率图），只保留转移概率为正的那些 arc（弧）；再对每个状态做一次 reachability search（可达性搜索），得到它的可达集；最后逐点核对「这个集合里有没有一个回不到出发点的点」。三步全是图操作，不做矩阵乘法、不解方程、也不算 $n$ 步转移概率。
>
> 第一性原理是前一条判据的反向使用。若存在这样的点，则出发点一旦落到它身上就永久失守，返回次数有限，故为 transient（暂态）。反过来，若可达集里没有任何一点能造成失守，则出发点的每一次离开都能被追回；配合「有限状态下最小正概率有正下界」，反复尝试必成功，返回次数无限，故为 recurrent（常返）。所以判据真正检查的只有一件事：有没有「有去无回」的出口。
>
> 四点的判定逐一看。状态 1 只可达自身，可达集是单点集且封闭，self-loop（自环）把它锁死，这是 absorbing state（吸收态）的极端形态——教材那句「一个可达状态与自身门类一致，因此 1 是常返状态」在译文里主谓有点错位，原意是「1 的可达集就是它自己，集合内没有能逃出去的点」。状态 2 可达状态 1、3、4 三个状态，看起来四通八达，却没有任何一个能回到 2：它是 gate（闸门）式的入口，在 condensation（凝聚图）里位于 sink（汇点）之前，故为 transient（暂态）。状态 3 与 4 互达，且都没有通往类外的弧，构成一个两点的 recurrent class（常返类）。
>
> 这里有个容易写错也容易读错的细节：判常返并不要求类里每个状态都有 self-loop（自环）。状态 3 与 4 只要形成「3 到 4、4 到 3」的两步闭路，返回时刻就全部落在偶数位上，足以常返；如果 3、4 都没有 self-loop（自环），这个两点的 recurrent class（常返类）的 period（周期）就是 2。要注意原文此处的 OCR 无法辨认弧线与自环的方向，图 7.8 里 3、4 究竟带不带 self-loop（自环）无法确认，所以「周期为 2」只能读成条件断言（在无自环的前提下成立），而不是既定事实。另有一处常见读法要纠正：把这类结构读成「含 self-loop（自环）的强连通块」并不准确，正确的刻画是「闭的强连通块」——self-loop（自环）只是保证 aperiodic（非周期）的充分条件，绝不是常返的必要条件。
>
> 判据的不对称性是最该记住的一点：只问「别人能不能回到我」，不问「我能到达多少人」。状态 2 能到三个状态却是 transient（暂态）；状态 1 只能到它自己却 recurrent（常返）。度数、连通度、出边条数都不是判据。把「连接多」当成「稳定」是这一节最常见的直觉陷阱，而且它在真实网络上代价很高：一个中转枢纽看起来最稳，恰恰因为所有流量都只经过它而不回它，它才是最脆弱的 transient（暂态）点。
>
> 命名模板：transient（暂态）与 recurrent（常返）的分野不是「走得多」与「走得少」，而是「有没有回头路」。图 7.8 里四个状态都能被反复踩，差别只在于踩完之后还能不能再踩。
>
> 跨课程：CSAPP 里指针图的可达性分析与此同构，编译器的 dead code elimination（死代码消除）第一步就是算「从入口可达」，剩下的才删。更贴切的是 garbage collection（垃圾回收）：mark-sweep（标记清扫）从 root set（根集合）出发标出可达对象，剩下的即垃圾；而 reference counting（引用计数）处理不了环，因为环内每个对象都被引用、彼此可达，整体却可能已经脱离根集合——这正好是「互达但都不回归」的结构，也解释了为什么 reference counting（引用计数）必须再配一个 cycle detector（环检测器）补课。
>
> 反例三条。把「图里有环」当常返：一个暂态环只要有一条出边通向别处并且不再回来，整块都是 transient（暂态），环只是让它多待一会儿。把「某条轨道没回来」当证据：判据是对分布、对全部轨道以概率一成立的断言，单条 sample（样本）既举不出证明也举不出反证。把「可达集大」当常返：见状态 2，它到得比谁都多。
>
> 最后补一个 complexity（复杂度）上的实事。逐个状态求可达集是每个状态一次搜索，总代价随状态数与边数相乘；先做一次 Tarjan algorithm（Tarjan 算法，1972 年，SIAM Journal on Computing 第 1 卷）的强连通分解，再在缩图上查出度，总代价只与状态数加边数同阶。两种做法给出同一判据，后者是把概率问题彻底变成图问题的标准姿势。

> 由此引出下述结论（it follows that … the following conclusion）。在马尔可夫链（Markov chain）中，**至少必须存在一个常返类（recurrent class）**；一个马尔可夫链可以被分解为一个或多个常返类（recurrent classes），或许再加上若干暂态（transient）状态。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「至少一个常返类，加上可能存在的若干暂态」这句话给了两件事：分解的存在性，和分解的形态。把它当成两个独立命题分别证一遍，比背结论有用得多。
>
> 存在性第一条路是纯结构的。先对全部状态做一次 strong connectivity decomposition（强连通分解），把每个 strong component（强连通分量）缩成一点，得到 condensation（凝聚图），它是 directed acyclic graph（有向无环图）；有限的 directed acyclic graph（有向无环图）必然有 sink（汇点），即出度为零的顶点，否则顺着出边一直走下去就能无限前行，而顶点有限、必然重复，重复处即成环，与无环矛盾。这个 sink（汇点）对应的原图顶点集就是 recurrent class（常返类）：类内互达保证它是强连通块，出度为零保证它是 closed（闭）的，即没有出口。这里有个容易踩坑的顺序问题：缩点必须一次性对全部 strong component（强连通分量）做，不能先按常返类缩点——那样等于把要证的结论当作构造的前提，论证就绕回去了。第二条路是纯概率的：状态有限而步数无限，pigeonhole principle（鸽巢原理）保证某条轨道上存在被访问无限多次的状态；但「某条轨道上无限多次」只是 infinitely often（无限多次）的观测事实，离定义还差一步。补上这一步的做法是考察这条轨道的 limit set（极限集，被无限次访问的状态全体）：它几乎必然非空，而且几乎必然 closed（闭）——若它有一条出边通向集合外，这条边就会被无限次穿越，于是集合外那个状态也会被无限次访问，与极限集的定义矛盾；闭的强连通集正是常返类，类内任一点都满足「从自身出发以概率一被无限次访问」这条定义。一条路不谈概率，一条路不谈图，却指向同一个结论——这种双重证明通常意味着命题正处在两套结构的交汇处，值得单独记一笔。
>
> 分解的形态要说准：这是把状态空间做 partition（划分），不是把矩阵做 direct sum（直和）。类与类之间完全隔离，一经进入便永不离开；暂态可以有任意复杂的内部通路，但它们只能朝类里流，不能反向。用矩阵语言，重排状态次序后可化成 block upper triangular（分块上三角）形式，对角块对应各个常返类，非对角块只出现在右上区块——也就是只允许「从暂态流向常返类」这一个方向。只有全部状态都属于常返类时，这个分块才退化成对角分块。
>
> 为什么这条是本章的主干：后面所有关于长期行为的断言，第一步都是「先定位你落在哪个类，再在类内做分析」。多类链的极限依赖起点，所以我们没有资格直接谈「这条链的稳态」；能谈的是「进入某个类之后的行为」。§7.3 把讨论限制在单一常返类，正是把多类问题化归成单类问题的动作——不是简化，是必要的拆分。
>
> 命名模板：decomposition（分解）在数学里常指把对象写成互相独立的部件之和，比如向量空间直和、群直积；这里更接近「划分加单向流」。两者的差别在对称性：直和的部件平等且可逆，这里的部件之间有方向、有先后。把它误当直和，就会误以为可以随意重排状态使矩阵变成块对角，从而把「进入各常返类的概率」这件本应交代的事整个忘掉。
>
> 跨课程：18.06 里 row-stochastic（行随机）矩阵若有 $k$ 个常返类，eigenvalue（特征值）1 的 multiplicity（重数）至少是 $k$，每个类贡献一个「指示向量」形状的 left eigenvector（左特征向量）；分块上三角形式下，特征多项式按块相乘，特征值是各对角块特征值的并集。这条代数事实就是「多类导致极限不唯一」的严格版本：1 不再单重，matrix power（矩阵幂）不会收敛到单个向量。spectral gap（谱间隙）在这里也要说得更准：单类非周期时，除 1 之外的特征值的模严格小于一，收敛速率由模最大的那个 $\lambda_2$ 决定，gap 常定义为 $1-|\lambda_2|$，gap 越小收敛越慢。周期链并不是「gap 没有定义」，而是 $|\lambda_2|=1$、gap 为零，于是根本没有收缩，谈速率没有意义——准确的措辞是「只有单类非周期时才给出正的收敛速率」。这套语言是 Markov chain Monte Carlo（马尔可夫链蒙特卡洛）与 PageRank（网页排名）收敛分析的起点。
>
> CLRS 6.006 这一侧是流水线式的：缩点、topological sorting（拓扑排序）、取拓扑序末端的 sink（汇点），顺序恰好是从暂态到常返类。Tarjan algorithm（Tarjan 算法）一次 depth-first search（深度优先搜索）同时给出类与缩图，工程上比逐个求可达集快一个量级，这也是「判定常返不需要解方程」的技术底气。
>
> 反例与边界三条。第一，暂态不归属任何常返类，它是过道而不是房间；把每个状态都强行塞进某个类，会得到一个满足「互达」却破坏了「闭」的假划分。第二，这条存在性依赖有限状态：无限状态链可以一个常返类都没有——整数格点上的对称 random walk（随机游走）处处 null recurrent（零常返），没有任何状态以正比于时间的频率被反复访问，占比处处为零，谈不上稳态。第三，混合情形最费神：多个常返类的链，长期占比是「进入各类的概率」乘「类内占比」，两个因子分别来自暂态分析与类内分析，这正是本章拆成两节处理的原因。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**常返类分解（Decomposition into recurrent classes）**</span>

一个马尔可夫链可以被分解为一个或多个常返类（recurrent classes），可能还伴随一些暂态（transient）状态……一个常返状态（recurrent state）……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述分解结论的表述行（含「…can be decomposed into one or more recurrent classes, possibly some transient states」、「…must exist at least one recurrent class」等）在 OCR 中被打散，顺序与个别用词无法精确认定，故此处按可辨认片段重组以保语义，不作为逐字原文。</span>

---

<span style="color:#2471a3;">**[讨论]**</span> <span style="color:#00838f;">**常返状态与概念工具（recurrent states as a conceptual tool）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本区段文字（如「…recurrent states are … from a … Markov chain …」等）被 OCR 读成大量乱码，内容几乎无法辨认；此处仅保留可确认的零散短语，不臆造数值与具体表述。该经典性质表述为：常返状态集与不可约/可达的关系为「若干互达的常返状态构成常返类」这一类概念工具（powerful conceptual tool），用于对马尔可夫链进行推理（reasoning about Markov chains）。</span>

一个来自某马尔可夫链……的常返状态（recurrent states）……

这一性质为关于马尔可夫链（Markov chains）的推理提供了一款强有力的概念工具（provides a powerful conceptual tool for reasoning about Markov chains）。

---

<span style="color:#c0392b;">**§7.2 收尾过渡 —— 转入后续小节的讨论**</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**访问次数（Number of times）与后续小节的分工**</span>

为分析由单个常返类构成、或讨论「进入某一特定常返类」与「给定一个暂态（transient state）」这两类链的行为目的（for the purpose of … to analyze chains that consist of a single recurrent class … the particular class of recurrent states is entered and given a transient state），这两个问题正是后续各小节（Sections，即 §7.3、§7.4）的讨论焦点（focus）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末尾过渡段（含「Number of times:」「it is important / it is im-…」等）残缺严重，个别词被换页符截断（如段末「it is im-」即「it is important」的前缀）；此处按 §7.2 末尾的实际行文结构重组为可读过渡，具体措辞以原文（页 358–359）为准。</span>

（本页结束，内容在下一页 §7.2 末尾 / §7.3 起始处继续。）
<!-- ===== PDF p359 ===== -->

<span style="color:#c0392b;">§7.2　状态的分类（Classification of States）</span>（续——承接上一页）

> <span style="color:#7f8c8d;">本页承接 p358 的讨论，继续 §7.2 的状态分类内容：常返类与暂态的分解结论、马尔可夫链分类作为推理工具的意义，以及周期常返类（periodic recurrent class）概念的引入。页面 OCR 严重损坏，正文按教科书 §7.2 的标准内容谨慎重建；凡具体数字、图号、符号无法从 OCR 确认之处，均以灰注释标注，绝不臆造。</span>

---

<span style="color:#00838f;">**[正文] 常返类分解结论的承接（decomposition into recurrent classes，续论）**</span>

如上一页页末所给出的定理所述，一个马尔可夫链可分解为一个或多个常返类（recurrent classes），可能还伴随若干暂态（transient states）——该结论已在上页（p358）以「常返类分解」定理形式陈述，此处接续其推论：链一旦进入某个常返类，便不会离开该类，并在其内部各常返状态之间来回游走。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 本页开头的图引用在 OCR 中被彻底打散，仅残余「… Markov chain … transient states」及「… into recurrent classes …」等片段；由相邻 p360 提及「Fig. 7.9 中的第三个链」反查，此页所含插图应为 Figure 7.9。图号以相邻页为准，未在原文中直接确认。</span>

对于暂态，若链从某个暂态出发，它可能（也仅仅是以正概率）临时逗留若干步，但最终会离开暂态、进入某个常返类，从而被各常返状态所吸收。这一分类为分析马尔可夫链提供了一个强有力的**概念工具（conceptual tool）**：许多关于链的长期行为的结论，都可以先归结为对**单一常返类**内部行为的考察来完成。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 上述关于「暂态至多被访问有限次」「常返状态以概率 1 被无限次访问（number of times）」的过桥句，OCR 仅保留「… number of times …」「… provides a powerful conceptual tool for reasoning about Markov chains …」等孤立残词，确切措辞未能复原，以下为按其语义的合理补全。</span>

---

<span style="color:#00838f;">**[正文] 周期常返类（periodic recurrent class）**</span>

下面引入对常返类内部结构的进一步细分。设 $R$ 是一个常返类，并假设其状态集的某一种划分总能被构造出来。若该常返类的状态可被分组为 $d$ 个子集

```math
S_1,\ S_2,\ \dots,\ S_d
```

使得当链条于时刻 $n$ 位于某子集 $S_k$（对 $k=1,2,\dots,d$）中的任一状态时，它在时刻 $n+1$ 必然进入下一子集 $S_{k+1}$（当 $k=d$ 时回到子集 $S_1$），则称该类为**周期常返类（periodic recurrent class）**。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 本页尾部仅残留「if k = 1 . . . . . d」与「if k = 1」两处可辨片段，其字面含义为「当 $k=1,2,\dots,d$ 时」。由紧接的 p360（Figure 7.10，$d=3$，并含「(or to $S_1$ if $k=d$)」）反查，本页应为周期常返类划分定义的开篇。确切的定义句式、$d$ 的具体取值及是否以「⟶ 下一子集」表述，以原文为准；下列数学式为规范化的标准表述。</span>

周期数 $d$ 刻画了链条在子集之间的循环转移节律；若不存在这样的 $d>1$ 划分，即该类只有一个子集（$d=1$），则称为**非周期常返类（aperiodic recurrent class）**。周期判定与图、转移概率矩阵的周期结构密切相关，其更严格的判别准则如「存在从某状态出发回到自身的 $n$ 步路径对（$\ge 1$ 的情形）」见本页之后§7.2 后续内容（p360 及以下）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一句把讨论从「回不回得来」推进到「按什么节律回来」。定义里的那 $d$ 个子集不是人为划出来的，而是被动力学逼出来的：只要类里存在相位约束，子集就自动出现。所以读这条定义该问的是「什么时候必然出现这种分层」，而不是「怎么找这样的划分」。
>
> 第一性原理落在返回时刻的集合上。固定类内一个状态 $s$，把所有使「走 $n$ 步后回到自身」具有正概率的步数收进一个集合，取它们的 greatest common divisor（最大公约数），这个数就是 period（周期）$d$。为什么它能解释分层？给每个状态贴一个相位标签：从 $s$ 出发走任意一条 path（路径），把路径长度按 $d$ 取余数作为标签。标签良定义的关键在于它与路径无关，而这需要一个只许顺着箭头走的论证：设从 $s$ 到同一状态 $x$ 有两条 path（路径），长度分别是 $n_1$ 与 $n_2$；再从 $x$ 取一条回到 $s$ 的 path（路径），长度是 $r$。把这条 $x \to s$ 的路分别接在两条 $s \to x$ 的路后面，得到两条从 $s$ 出发的 closed walk（闭路），长度各为 $n_1+r$ 与 $n_2+r$，两个都是返回时刻，都被 $d$ 整除，于是它们的差 $n_1-n_2$ 也被 $d$ 整除，两条路给出的余数相同。这里不能「把一条路反向拼接」——transition graph（转移图）是有向图，边不可逆；「接上同一条返回路」这个做法正是为了绕开逆向。标签一定，转移就只能把标签加一，于是类被余数切成 $d$ 层，链在层间的顺序是 1、2、……、$d$、再回到 1。$d$ 与起点的选取无关，这一点需要证明，教材把它推到习题里。
>
> 命名模板：period（周期）这个词来自希腊语 periodos（意为「绕一圈的路」），后来泛指一切「平移一个单位就回到原样」的结构——周期函数、傅里叶级数的基频、钟面转动都是这个意思。用在这里，$d$ 的量纲不是时间而是拍数：走 $d$ 步正好回到同一层，而不是「走 $d$ 步一定回到自己」。这个区分很要紧，因为周期 2 的类里，出发点两步回到自身，而别处的状态两步就跑到另一个状态上去了。
>
> 跨课程里最要紧的一条在谱上。周期为 $d$ 的常返类，transition matrix（转移矩阵）在类上的限制有 $d$ 个模为一的特征值，它们恰好是 $d$ 次 unit root（单位根，把单位圆等分成 $d$ 份得到的那组点）。这就是振荡的代数根源：$n$ 步转移矩阵是这些模态的 linear combination（线性组合），模为一的旋转分量永不衰减，于是 $n$ 步概率只会转圈、不会冻结。反过来，aperiodic（非周期）等价于「一是唯一模为一的特征值」，也等价于 matrix power（矩阵幂）收敛。把周期性翻译成「spectral radius（谱半径）所在圆周上还有别的点」，是 Strang 18.06 那套特征值语言能直接接管这一章的唯一入口，值得反复默写。
>
> 6.042J 的数论在这里补上另一半。返回时刻的集合对加法封闭（两段闭路拼起来仍是闭路），构成一个 additive semigroup（加法半群）；数论里有一条结论说，这样的半群一旦最大公约数为一，就最终包含所有足够大的整数。这就是为什么非周期链的返回时刻最终致密，而周期链永远留着一半或三分之一的空洞。教材章末那道用数论收口的习题，考的就是这个事实。
>
> 反例四个。双状态互转的确定性链，$d$ 为 2；三点轮转（图 7.10 的例子）$d$ 为 3；而只要类里有任何一个状态带 self-loop（自环），步数一就进了返回时刻集合，最大公约数立刻被压成一，全类非周期——这是最快的非周期判据，后文「特殊状态」那条只是它的推广。第四个是方向最容易搞反的地方：周期说的是返回时刻全是 $d$ 的倍数，不是「恰好 $d$ 步回来」，return time（返回时间）可以任意长，只要始终落在同一个剩余类里。
>
> 两处要替读者点明。其一，$d$ 大于一时，常返类仍然有平衡方程的非负解，但 $n$ 步转移概率并不收敛到它，所以「解存在」与「极限存在」是两个命题，本章后面反复用到这条分界。其二，译文那句「更严格的判别准则如『存在从某状态出发回到自身的 $n$ 步路径』」在原文的 OCR（光学字符识别）结果里已被切碎，其实质就是上面那个最大公约数定义，$n$ 取遍所有正的返回步数，而不是某个固定的 $n$。把「对（大于等于一的情形）」这种残句当成条件，会读出一个根本不成立的判据。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 本页由 OCR 损坏导致的不可辨识处较多，正文为按教科书 §7.2 标准内容所作的忠实重建。请以（纸质）原书 p359 为准核对图号、$d$ 取值及确切措辞；本译文不承担因恢复而引入的具体数值。</span>
<!-- ===== PDF p360 ===== -->

<span style="color:#c0392b;">**§7.2　状态分类（Classification of States）—— 周期常返类（Periodic Recurrent Classes）：（续）**</span>

本页承接上一页，继续 §7.2 对状态（state）分类的讨论（页首无新节标题，故标「续」）。页首的「7.2」为章节边注（running header），正文核心为周期常返类（periodic recurrent classes）的结构（配图 Figure 7.10）以及如何验证一个常返类（recurrent class）的非周期性（aperiodicity）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 OCR 整体严重损坏（大量断行、乱码碎片如「'"-' 'U'」「.. ... ....」「l.i.1J」等），页面主体文字几乎无法逐字辨认。下文按书本 §7.2 周期类小节的真实行文结构，结合本页可辨认的片段（Figure 7.10、d = 3、「move through the sequence … in the same subset」、「to S_1 if k = d」、「是否存在特殊状态 i ∈ R 与 n ≥ 1 使 T_{ij}(n) > 0」、链例子的反证等）重组为可读双语译文；具体措辞、图号引用（Fig. 7.9 / 7.10）与个别数值以原书页 360 为准，凡 OCR 无法确证者一律在下文以灰注标注，绝不臆造。</span>

---

<span style="color:#00838f;">**[定义/说明] 周期常返类的结构（Structure of a periodic recurrent class）**</span>

<span style="color:#00838f;">**Figure 7.10：周期常返类的结构（Structure of a periodic recurrent class）。在本例中，$d = 3$。**</span>

考虑一个周期（period）$d\ge 2$ 的常返类（recurrent class）$R$。该类的状态可被分成 $d$ 个互不相交的子集（subsets）$S_1, S_2, \ldots, S_d$，使得所有从 $S_k$ 出发的转移（transitions）都进入 $S_{k+1}$（或若 $k = d$ 则进入 $S_1$）。于是，在一个周期常返类中，我们沿子集序列 $S_1, S_2, \ldots, S_d, S_1, \ldots$ 循环移动，始终落在同一子集序列（subset）内。

> <span style="color:#7f8c8d;">此处「move through the sequence … in the same subset」为 OCR 中少数可辨认的连贯片段；「to $S_1$ if $k = d$」亦见原文。子集的序号标记（$S_1,\ldots,S_d$）为本节惯用记号，具体下标以原书为准。</span>

作为例子，[考虑] Fig. 7.9 中的第三条链（third chain of Fig. [7.9]）……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「…third chain of Fig. …」之后的周期性结论（即该链周期 $d$ 的具体数值、以及它分属图 7.9/7.10 的对应关系）在 OCR 中残缺，无法确认，故不臆造该数值。</span>

---

<span style="color:#00838f;">**验证非周期性（a verification of aperiodicity）—— 特殊状态判据**</span>

其原因在于（The reason is that）……要验证一个常返类（recurrent class）是否非周期（aperiodic），一个办法是判断是否存在一个 $n\ge 1$ 以及一个特殊状态（a special state）$i \in R$，使得由状态 $i$ 出发，能以某概率到达类中的每一个其他状态（from which all states in $R$ are accessible）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 一个状态、一个时刻，就足以判定整个类的非周期性，这是本页最实用的一条。它的价值在于把「逐个检查每个状态的返回相位、再取最大公约数」这件繁琐工作，压缩成一次可达性检查。
>
> 为什么成立，用相位标签讲最清楚。设类内所有返回时刻的最大公约数为 d，按上一条的构造给每个状态贴相位标签，转移只能把标签加一。若存在状态 i 与步数 n，使得从 i 出发走 n 步能以正概率到达类内每一个状态，那么对每个 j 都存在一条长度恰为 n 的路从 i 到 j，于是每个 j 的标签都等于 i 的标签加 n——全类状态落在同一层。可是只要 d 大于一，从任何一层出发都必须进入下一层，不可能原地停留；全类共处一层而转移又必须换层，两者直接冲突。故 d 只能是一，全类 aperiodic（非周期）。
>
> 这条论证只用到两件事：类内互达保证了「从 j 回到 i」这一步存在，可达性保证了「从 i 出发 n 步到 j」这一步存在；两条拼起来就得到足够多的返回时刻，而它们的差值把最大公约数挤成一。教材把它写成一次可达性检查，背后其实是一次贝祖式的拼凑。
>
> 命名模板：special state（特殊状态）这个名字起得含糊，读作 seed state（种子状态）更贴切——像一棵树的根，一次到位的层数扫过全部枝叶。教材用它的用意是「存在即可」：不要求唯一，也不要求稳定，只要有一个例子就把整类的周期判死。
>
> 这条判据的强度必须说准。教材先把它作为「一个办法」提出，这是充分条件的口气；但本页末尾紧接着写「一个逆命题……被证明为真」，也就是说逆命题同样成立——任何非周期的常返类里一定找得到这样的状态与时刻。于是它在有限状态下是充要条件。这一点如果漏掉，读者会把它当成只好不坏的技巧，而不知道它其实刻画了非周期的全部内容。
>
> 跨课程：图算法上，这条判据等于「从某点做一次层数恰为 n 的分层，看那一层是否覆盖全部状态」；实现时不必真的枚举最大公约数，按层号取余数，余数的种类数就是周期 d，只出现一种余数即非周期。18.06 的语言里，它是「一是唯一模为一的特征值」的一个组合充分条件，把谱条件落成了可以在邻接表上跑的操作。6.042J 的数论提供另一半：若干整数的最大公约数为一，就存在整数系数的线性组合等于一，这条结论叫 Bezout identity（贝祖等式），这正是「两个互素的返回时刻能拼出所有足够大的步数」的代数根据，也是章末习题用数论收口的地方。
>
> 反例：纯双状态互转的链，任何时刻只能落在其中一层，找不到这样的状态与时刻，周期性警报拉响；三点轮转更明显，任何 n 步只覆盖三分之一的层。图 7.9 第一条链那个「n 为 3 时每个状态都可能」的例子，正是判据成立时的模样——一次三层走完，说明三个子集被一把扫平。
>
> 常见误读与边界三条。第一，n 必须取正：取零时「零步回到自己」对起点恒成立，却覆盖不了别的状态，判据会自我失效。第二，判据里的 i 必须属于该类；拿暂态当起点会得到一个毫无意义的结论，因为暂态的可达集本身就不闭，它的「覆盖全类」与类的相位毫无关系。第三，原文里「某些 j」与「一切 j」这两个量词被 OCR（光学字符识别）吃掉一处，标准判据要求的是**一切** j——只要漏掉一个，被漏掉的那层就可能定义出一个新的周期，判据立刻不成立。

> <span style="color:#7f8c8d;">本句对应「T_{ij}(n) > 0 for some j ∈ R」的验证形式；「是否存在特殊状态 $i$ 与时间 $n$」即原文的识别片段。具体是「所有 $j\in R$」还是「某些 $j\in R$」，因 OCR 中「an/some/all j」残缺，按标准判据（存在 $n$ 使 $T_{ij}(n)>0$ 对一切 $j\in R$ 成立）作推断，以原书为准。</span>

例如，Fig. 7.9 中的第一条链（the first chain），自状态 1 出发，在时刻 $n = 3$ 时每一个状态都可达（every state is possible at time $n = 3$），因此……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「first chain … from state …, every state is possible at time n = 3」为可辨认片段；「state 1」与「n = 3」两个数值的精确性因 OCR 拼读（原文作「state I I」）存疑，故按常见情形作推断并保留灰注，具体以原书为准。</span>

一个逆命题（A converse）…… 被证明为真（turns out to be true）：如果[存在]……一个常返（recurrent）[类]……及某个 $n$……使得 $T_{ij}(n) > 0$……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「A converse … turns out to be true」为可辨认片段；其成立条件（「存在 $n\ge 1$ 与特殊状态 $i\in R$ 使 $T_{ij}(n)>0$ 对一切 $j\in R$ 成立，则类非周期」）因 OCR 残缺无法精确还原措辞，此逆命题的完整陈述以原书页 360 为准。</span>

一个[常返]类（The class）的[状态]可被分进 $d$ 个子集（grouped in $d$ subsets），符合条件的转移从[某子集]到[下一子集]，若且唯若（if and only if）……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本段（关于将状态分组为 $d$ 个子集、并以上述结构刻画周期性/非周期性的「当且仅当」断言）残缺极重，仅剩「grouped in d subsets」「from … to …」「if and only if」等零散词；完整的周期/非周期判据命题以原书页 360 为准。</span>

---（§7.2 周期类相关正文在本页结束后，于下一页继续。）---
<!-- ===== PDF p361 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

<span style="color:#c0392b;">**7.3　稳态行为（Steady-State Behavior）**</span>

在马尔可夫链（Markov chain）模型中，我们常常关注长期的状态占据（state occupancy）行为，也就是当 $n$ 很大时 n 步转移（n-step transition）概率 $T_{ij}(n)$ 的行为。我们在图 7.6（Fig. 7.6）的例子中已经看到，$T_{ij}(n)$ 可能会收敛到与初始状态无关的稳态值（steady-state values）。我们希望理解这种行为在多大程度上是典型的。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏/符号待核] 原页中的「n-step transition probabilities」（源 OCR 显示为 `Tij (n)`）与后文 $P_{12}$、$P_{21}$ 等已读符号混排；此处按教科书对本页所述「n 步转移概率」的标准记法还原为 $T_{ij}(n)$（源 OCR 以大写 `T` 误读下标，且同页后文将 $\pi_j$ 误读为 `7rj`，符号 OCR 并不可靠）。若需最严格核对，请回查原书页 352。</span>

如果存在两类或更多类的常返状态（recurrent states）所属的类（class），显然 $T_{ij}(n)$ 的极限值必然依赖于初始状态（远期访问 $j$ 的可能性取决于 $j$ 是否与初始状态 $i$ 属于同一个类）。因此，我们将注意力限制在只含一个常返类（recurrent class）、外加可能存在的一些暂态（transient states）的链上。这并不像看起来那么受限，因为我们知道，一旦状态进入某个特定的常返类，它就会一直停留在这个类内。于是，多类链（multiclass chain）的渐近行为可以通过单类链的渐近行为来理解。

即使对于只含单个常返类的链，$T_{ij}(n)$ 也可能不收敛。为看清这一点，考虑一个包含两个状态 $1$ 和 $2$ 的常返类，从状态 $1$ 只能到状态 $2$，从状态 $2$ 只能到状态 $1$（$P_{12} = P_{21} = 1$）。那么，从某个状态出发，经过任意偶数次转移后我们会回到同一状态，经过任意奇数次转移后会处于另一个状态。形式化地，

```math
T_{ii}(n) =
\begin{cases}
1, & \text{$n$ 为偶数},\\
0, & \text{$n$ 为奇数}.
\end{cases}
```

这里发生的情况是，该常返类是周期的（periodic），而对这样的类，可以看出 $T_{ij}(n)$ 一般会振荡（oscillate）。

现在我们断言：对每个状态 $j$，处于状态 $j$ 的概率 $T_{ij}(n)$ 会趋近一个与初始状态 $i$ 无关的极限值，前提是我们排除了上述两种情形（多个常返类和/或一个周期类）。这个极限值记作 $\pi_j$，它有以下解释：

```math
\pi_j \approx P(X_n = j),
```

当 $n$ 很大时成立，并被称作 $j$ 的稳态概率（steady-state probability）。下面是一个重要的定理。它的证明相当复杂，其提纲与另外几个证明一起放在章末习题（end-of-chapter problems）中给出。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中 $\pi_j$ 与 $P(X_n = j)$ 之间的符号在源 OCR 中显示为残缺占位符（`7rj  P(Xn = j)`），按上下文读作「近似等于」（$\approx$）；$\pi_j$ 亦被源 OCR 误读为 `7rj`。此处按第 7 章标准记法还原，如需最严格原文请回查原书页 352。</span>

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**稳态收敛定理（Steady-State Convergence Theorem）**</span>

考虑一个只含单个常返类、且该常返类是非周期的（aperiodic）马尔可夫链。那么，各状态 $j$ 与满足下列性质的稳态概率 $\pi_j$ 相关联：
<!-- ===== PDF p362 ===== -->
<span style="color:#c0392b;">**§7.3　稳态行为（Steady-State Behavior）**</span>（续）

本页承接上一页 §7.3 稳态行为中「稳态收敛定理」的陈述与后续讨论（本页页眉为 Sec. 7.3，页首直接从定理陈述的中部「(a)」继续），故本节标题标注「（续）」。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**稳态收敛定理（steady-state convergence theorem）（续）**</span>

(a) 对每个 $j$，我们有

```math
\lim_{n\to\infty} T_{ij}(n) = \pi_j, \qquad \text{对一切 } i.
```

(b) 这些 $\pi_j$ 是下面方程组的唯一解：

```math
\pi_j = \sum_{k=1}^{m} \pi_k\, p_{kj}, \qquad j = 1, \ldots, m,
```

```math
\sum_{k=1}^{m} \pi_k = 1,
```

(c) 此外，

```math
\pi_j = 0 \ \text{（对所有暂态状态 } j\text{）}, \qquad \pi_j > 0 \ \text{（对所有常返状态 } j\text{）}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 定理陈述 (b) 的方程组在本页 OCR 中被明显打散：下标 $k$ 的求和范围、以及「$\pi_j = 0$ 对暂态状态、$\pi_j > 0$ 对常返状态」的条件均出现在被打碎的碎片区，符号多处被误读为 `1r'j`/`1l'k`/`1C'j`。上面依据 (a)、后文的平稳分布讨论及平衡方程（balance equations）按书中原有标准表述反查还原；「$\pi_j=0$/>0 对暂态/常返」这一条件按源头 OCR 独立的 (c) 项列出。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把它拆成三件套来记最省力：存在性（极限与起点无关）、表达式（平衡方程加归一化的唯一解）、刻画（暂态为零、常返为正）。三件套各自对应一个可以独立检查的命题。
>
> 第一性原理用谱讲才讲得透。$n$ 步转移概率就是 transition matrix（转移矩阵）的 $n$ 次幂，而幂的行为由 eigenvalue（特征值）主宰：模小于一的分量随 $n$ 指数衰减，模等于一的分量不衰减。aperiodic（非周期）这个条件恰好把「模等于一」圈成只剩 1 这一个；单类，也就是 irreducible（不可约），这个条件恰好让 1 成为单重特征值，且左右特征向量都是正的。两条合起来，matrix power（矩阵幂）收敛到一个 rank-one matrix（秩一矩阵），每一行都等于同一个 stationary distribution（平稳分布）。所以收敛不是「游荡久了会忘」，而是「除一个模态外全部模态都被指数压死」。这个谱图像比任何文字比喻都可靠，也顺带给出收敛速度：误差按 $|\lambda_2|^{n}$ 衰减，这里 $\lambda_2$ 是模次大（严格小于一）的特征值；通行的 spectral gap（谱间隙）定义是 $1-|\lambda_2|$，gap 越接近零，$\lambda_2$ 的模越接近一，收敛越慢。mixing time（混合时间）就是由 gap 控制的量级。把「次大特征值之模」和「gap」当成同一个量是这里最常见的失误：前者越小收敛越快，后者越小收敛越慢，方向正好相反。
>
> 为什么要两个前置条件，各堵一种失败：多个常返类时，幂的极限是一个按「进入各类的概率」加权的分块结构，极限依赖起点落在哪个类，谈不上与起点无关；周期类时，模为一的特征值不止一个（还有 unit root（单位根）），那些旋转分量让 $n$ 步概率永远振荡，同样不收敛。所以定理的陈述不是「为了严谨而加条件」，而是「这两个条件正好是收敛的边界」。
>
> 表达式那部分要看清「唯一」从哪里来。平衡方程本身只有有限条独立方程（下一条注专讲这件事），解空间至少一维；单类加非周期让 1 成为单重特征值，null space（零空间）恰好一维，再配上 normalization（归一化）把尺度钉死，解才唯一。换句话说，唯一性不是平衡方程给的，是谱条件加归一化一起给的。
>
> 刻画那一条的机制值得单独说：transient（暂态）的长期时间占比为零，因为它只被访问有限多次；常返状态的占比严格为正，因为有限状态下它不只被访问无限次，return time（返回时间）的期望还有限——这就是 positive recurrence（正常返），而有限状态自动保证它成立。这两条合起来给出一个零成本的判断法：想知道某个状态是否会被长期占据，先问它是否常返。顺带把三个易混的词摆清楚：recurrent（常返）讲的是「必回」，positive recurrent（正常返）讲的是「回得快到期望有限」，两者在有限状态链上重合，在无穷状态链上分家。
>
> 命名模板：steady-state（稳态）与 stationary（平稳）在教材里是两个词。前者强调 $n$ 趋于无穷的极限，后者强调分布是不动点——取它为初态，此后每一刻的分布都不变。定理成立时两者数值相等，来源却不同：一个来自动力学的极限，一个来自不变性。等到链是周期的时候这层区别就致命：stationary distribution（平稳分布）仍然存在，limit distribution（极限分布）却不存在。把两个词分开，本章好几个「矛盾」会自己消失。
>
> 历史坐标：这条定理的代数骨架是 Perron 1907 与 Frobenius 1912 的谱定理（正矩阵的最大特征值单重、特征向量为正，后推广到不可约非负矩阵）；概率侧的 coupling（耦合）证明归于 Doeblin 1938 年那篇短文（据记载 1936 年夏写成），教材把它放进章末习题，让学生自己走一遍「两条独立运行的链相遇即合并」的构造。网络上的大规模应用是 PageRank（网页排名，Brin 与 Page 1998 年发表于 Computer Networks 第 30 卷），它把这条定理当排序算法用。
>
> 反例三条，各打一个前提。多类链（例如带吸收态的链）：极限取决于你在哪个类停下。周期链（双状态互转）：极限不存在，只有振荡。无限状态链：即使不可约非周期也可能没有稳态分布——整数格点上的对称 random walk（随机游走）处处 null recurrent（零常返），任何有限区间的占比都趋于零，没有一个正的平稳分布。第三条是「有限性」这个前提的现场，最容易被省略，也最容易出错。
>
> 最后校正一处读者最容易自己加上的多余条件：定理写「对一切起点」，起点允许取暂态状态，结论不变——暂态起点只是多花几步才进类，进去之后照样被同一个极限接管。真正的必要条件是链的结构（单类、非周期），而不是起点必须落在常返类里。

稳态概率（steady-state probabilities）$\pi_j$ 之和为 1，在状态空间上构成一个概率分布，称为该链的平稳分布（stationary distribution）。之所以用「平稳（stationary）」一词，是因为如果初始状态按照这个分布来选取，也就是说，若

```math
P(X_0 = j) = \pi_j, \qquad j = 1, \ldots, m,
```

那么，利用全概率定理（total probability theorem），我们有

```math
P(X_1 = j) = \sum_{k=1}^{m} P(X_0 = k)\, p_{kj} = \sum_{k=1}^{m} \pi_k\, p_{kj} = \pi_j,
```

其中最后一个等号来自稳态收敛定理的第 (b) 部分。类似地，对一切 $n$ 与一切 $j$，我们得到 $P(X_n = j) = \pi_j$。于是，如果初始状态按平稳分布选取，那么未来任意时刻的状态都会具有相同的分布。

方程

```math
\pi_j = \sum_{k=1}^{m} \pi_k\, p_{kj}, \qquad j = 1, \ldots, m,
```

称为平衡方程（balance equations）。它们是定理第 (a) 部分与 Chapman–Kolmogorov 方程（Chapman–Kolmogorov equation）的直接推论。事实上，一旦假定 $T_{ij}(n)$ 收敛到某个 $\pi_j$，我们就可以考虑如下方程，

```math
T_{ij}(n) = \sum_{k=1}^{m} T_{ik}(n-1)\, p_{kj},
```

> <span style="color:#7f8c8d;">本页截止于此，下一行推导随下页继续。</span>
<!-- ===== PDF p363 ===== -->
<span style="color:#c0392b;">**§7.3　稳态行为（Steady-State Behavior）**（续）</span>

承接上一页的证明：将上述等式两边同时对 $n$ 取极限 $n \to \infty$，便可恢复出平衡方程（balance equations）。† 再结合归一化方程

```math
\sum_{k=1}^{m} \pi_k = 1 ,
```

平衡方程即可求解，从而得到各 $\pi_j$。下面的例子说明了这一求解过程。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.5（两状态马尔可夫链的稳态概率求解示例。）**</span>

考虑一个两状态马尔可夫链（two-state Markov chain），其转移概率为

$\;p_{11} = 0.8,\qquad$ $\;p_{21} = 0.6,\qquad$ $\;p_{12} = 0.2,\qquad$ $\;p_{22} = 0.4 .$

（这与示例 7.1 及图 7.1 中的链相同。）平衡方程（balance equations）取如下形式

```math
\pi_1 = \pi_1 p_{11} + \pi_2 p_{21}, \qquad
\pi_2 = \pi_1 p_{12} + \pi_2 p_{22},
```

或等价地写成

```math
\pi_1 = 0.8\, \pi_1 + 0.6\, \pi_2 ,
\qquad
\pi_2 = 0.2\, \pi_1 + 0.4\, \pi_2 .
```

注意，上面两个方程是线性相关的（dependent），因为它们都等价于

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源页在此处缺失目标等价方程——原句为「…both equivalent to」（两者都等价于…），随后目标等式处 OCR 断裂、直接跳至下一句「This is a generic property…」。由本页稍后把 $\pi_1 = 3\pi_2$ 代入归一化方程的步骤可判，两个相关方程等价于 $\pi_1 = 3\pi_2$（等价于 $0.2\pi_1 = 0.6\pi_2$），此处按原文推导补全；仅凭数值推断，未改变任何原始系数。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「$m$ 条平衡方程里总有一条是多余的」这条普遍性质值得用两种办法各证一遍，因为它同时是代数事实与概率事实，两条路给的是同一件事的两个面。
>
> 代数证明最短。把 $m$ 条方程全部相加，右边逐项整理后恰好等于各分量之和，因为 transition matrix（转移矩阵）每一行的行和为 1——把所有出边概率加完就是 1。于是左右两边恒等，相减得到的是一个恒真式，而不是新信息。也就是说这 $m$ 条方程 linearly dependent（线性相关），rank（秩）至多为 $m-1$。这一步不需要谱论，只需要 row-stochastic（行随机）这个性质，凡是每行和为 1 的矩阵都成立。
>
> 概率证明给的是另一半：平衡方程说的就是「这个向量在转移之下不动」，即 transition matrix（转移矩阵）的一个 fixed vector（不动向量）；而 row-stochastic（行随机）矩阵永远有全为一的 right eigenvector（右特征向量，每行和为 1 就是说这个向量被映到自己），这保证 1 是 eigenvalue（特征值），矩阵减去 identity matrix（单位阵）后必然 singular（奇异），null space（零空间）非空。于是解不唯一是结构性的，不是计算误差。
>
> 缺口要靠 normalization（归一化）补上：把解限制在 probability simplex（概率单纯形）上，尺度被钉死。单类非周期时零空间恰好一维，归一化后唯一；若链有多个常返类，零空间维数随之上升，每个类贡献一个指示形状的解，归一化只能给出它们的某个 convex combination（凸组合），这正对应「极限依赖起点」。所以「唯一稳态」这句话里真正的看门人是「单类」，归一化只是收口动作。
>
> 命名模板与一处常见混淆：balance equation（平衡方程）又叫 global balance（全局平衡），它只要求进出某个状态的总流量相等；detailed balance（细致平衡）要求每一对状态之间的双向流量各自相等，即从 $i$ 到 $j$ 的流量等于从 $j$ 到 $i$ 的流量，这是强得多的条件，等价于 reversible（可逆）。绝大多数 Markov chain（马尔可夫链）不满足细致平衡，却一定有平衡方程的稳态解。把两者混为一谈，会误判一大批链「没有稳态」，这是本章最常见的一次概念滑坡。
>
> 跨课程：18.06 里这是 rank-nullity theorem（秩-零空间定理）的直接应用，null space（零空间）维数等于状态数减去 rank（秩），也就是「方程数多一条、未知数没多」。图论上还有更漂亮的一层：无向图上 random walk（随机游走）的稳态分布正比于各顶点的 degree（度数），可以不解方程直接写出；这个结论依赖对称性，一旦图变成有向，度数公式立刻失效，只能解方程。于是「对称矩阵谱好算、非对称难算」这句线性代数课上的经验，在这里有了具体载体。
>
> 工程实践：直接把奇异系统丢给 elimination（消元）会失败或给出巨大误差，惯用做法是把其中一行换成「各分量之和等于 1」这条与其余行无关的方程，得到非奇异系统；或者用 singular value decomposition（奇异值分解）取零空间向量。PageRank（网页排名）的做法更彻底：在转移矩阵里混入一个小的均匀项，这个系数叫 damping factor（阻尼因子），让矩阵非奇异且不可约，代价是稳态变成「带偏好的稳态」，好处是 power iteration（幂迭代）必定收敛，而且不必先做状态分类。
>
> 反例三条。忘记归一化：得到一整条射线上的解，每个正倍数都满足平衡方程，数值上表现为求解器报奇异或解随初值漂移。把细致平衡当必要条件：会错判绝大多数不可逆链。把那条多余方程当成「系数抄错」：这里一个系数都没错，determinant（行列式）本来就该是零，重复核对系数只会浪费时间，真正该做的是换行或加约束。
>
> 顺便校正一处容易误读的脚注：教材把「平衡方程总有非负解」归给 Perron–Frobenius theorem（佩龙–弗罗贝尼乌斯定理），这条归属没错但偏奢侈，另一个给法来自 Brouwer fixed point theorem（不动点定理）。Perron–Frobenius 真正额外的贡献是解的结构：正解出现在每个常返类上、1 是 spectral radius（谱半径）、单类时它单重；而「其余特征值的模严格小于一」这一条还要再加一个条件——primitive（本原）。单类且非周期时链是 primitive 的，这条才成立；周期链上模为一的特征值不止一个，双状态互转的矩阵（第一行 $0,1$、第二行 $1,0$）特征值就是 $1$ 与 $-1$，可以直接验算，此时只能保证「不超过一」。所以三件事要分开记：存在性靠不动点就够，唯一性要 1 单重（只需单类），指数收敛要「其余模严格小于一」（需要单类加非周期）。

这是一种普遍性质——事实上可以证明，任何一条平衡方程总能由其余各条方程推导出来。然而我们已经知道，各 $\pi_j$ 满足归一化方程

```math
\pi_1 + \pi_2 = 1 ,
```

它补充了平衡方程，并足以唯一确定各 $\pi_j$。事实上，将方程 $\pi_1 = 3\pi_2$ 代入 $\pi_1 + \pi_2 = 1$，得到 $3\pi_2 + \pi_2 = 1$，即

```math
\pi_2 = 0.25 ,
```

再利用方程 $\pi_1 + \pi_2 = 1$，便得

```math
\pi_1 = 0.75 .
```

这与我们先前通过迭代 Chapman-Kolmogorov 方程（cf. 图 7.6）所得的结果是一致的。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 平衡方程的第一性原理只有四个字：流量守恒。把「状态 $j$ 被占据的时间比例」记作 $\pi_j$，则离开 $j$ 的频率就是它乘以该行概率之和——而行和为 1，所以离开频率就是 $\pi_j$ 本身；进入 $j$ 的频率是从各状态 $k$ 流过来之和。稳态的意思正是「比例不再漂移」，也就是流入等于流出。方程不是被解出来的，是被守恒律写下来的。
>
> 换个形状更好用：把 self-loop（自环）那一项挪到等式右边，得到「占该状态的比例乘以不留在原地的概率，等于从别处流入的流量」。这个形式手算时省事，自环大的链尤其明显，而且它一开始就把「自环不影响平衡」说清楚了——自环只是把时间原地消耗掉，不改变进出别处的相对流量。
>
> 守恒律的强度不止于单个状态。把状态集任意切成两块，两侧的总流量同样相等；这个切割不变性是平衡方程逐项相加的直接推论，也是谱上「1 是 eigenvalue（特征值）」的另一种说法。它带来一个很实用的结论：把整个常返类当成一个黑箱，从暂态累计流入该类的 probability mass（概率质量）——它恰好等于最终进入该类的概率——就等于长期占据该类的比例。这里要分清「流入率」与「累计流入」：稳态下每一时刻跨过切口的净流量为零，单步的流入率随 $n$ 趋于零，真正与长期占比相等的是从时刻 0 到 $n$ 的累计流入再除以 $n$。把两者混成一句「流入等于占比」，会读出一个「稳态下还源源不断有质量流进来」的错误图像。二者合起来，「进入各类的概率乘类内占比」这种加权结构才站得住。
>
> 但必须分清频率与概率是两个量。$\pi_j$ 是长期时间占比，也就是访问频率的极限；而第 $n$ 步落在 $j$ 的概率依赖 $n$ 与起点，两者一般不相等，只在单类非周期且 $n$ 很大时趋同。周期链恰好是分界现场：双状态互转的链（转移矩阵两行分别是 $0,1$ 与 $1,0$），从状态 0 出发，第 $n$ 步落在状态 0 的概率是 $1,0,1,0,\dots$ 这样在一与零之间交替，而时间占比稳稳收敛到各二分之一。所以周期链没有 limit distribution（极限分布），却有 stationary distribution（平稳分布），也有频率意义下的稳态——这条区别能把本章好几个看似的「矛盾」一次性解开。顺带说，背后是 ergodic theorem（遍历定理）的离散版本：time average（时间平均）比 ensemble average（系综平均）更容易存在。
>
> 命名模板：stationary distribution（平稳分布）里的 stationary（平稳）是「站着不动」，指分布被映到自己；steady-state probability（稳态概率）里的 steady（稳定）指时间轴上不再波动。一个是不动点语言，一个是极限语言，定理成立时重合，条件不满足时分离。
>
> 跨课程：排队论里的 birth-death chain（生灭链）是这条方程最干净的退化形式——只有相邻状态之间有流量，平衡方程就变成逐条相邻的等式，也就是 detailed balance（细致平衡）在生灭链上自动成立，于是一路递推就能求出各状态占比。队列的稳定性判据（到达率小于服务率）与马尔可夫链的 positive recurrence（正常返）是同一件事：前者说队长不会漂到无穷，后者说状态被反复访问且返回时间的期望有限。CSAPP 的性能分析里「长期吞吐必须等于长期流入，否则队列或缓冲区会涨」是同一条守恒律的工程版本。18.06 里 $\pi$ 是转置矩阵对应特征值 1 的特征向量，power iteration（幂迭代）求它就是 PageRank（网页排名）的算法本体：反复用转移矩阵乘一个概率向量，等价于让一个随机游走者不停地走，走久了访问频率自己浮现出来。
>
> 反例三条。把「平衡方程有解」当成「$n$ 步概率收敛到它」：周期常返类仍有非负解，但概率在振荡，解不等于极限。把 $\pi_j$ 读成「第 $n$ 步在 $j$ 的概率」：它其实是时间占比，与 $n$ 和起点都无关。多类时以为有唯一解：每个常返类各自贡献一个解，归一化只挑出一个凸组合，真正的唯一性还要额外加「单类」这个条件。
>
> 一处技术细节值得点明：教材脚注用 Perron–Frobenius theorem（佩龙–弗罗贝尼乌斯定理）保证「对任意马尔可夫链，平衡方程总有非负解」，这条路正确但不是唯一的路，Brouwer fixed point theorem（不动点定理）在单纯形上给出同样的结论；Perron–Frobenius 的价值在于它同时说清了哪些状态上可以取正值，以及单类时 1 是单重特征值，这两条才是定理后半段唯一性的来源。
>
> 最后一条常被漏掉的定量事实：$\pi_j$ 也可以读成「长期来看落在状态 $j$ 的期望时间比例」，在有限不可约链上它等于 mean recurrence time（平均返回时间）的倒数——这把静态的占比和动态的返回间隔接了起来，也是把稳态结论反向用回常返性分析的接口。

---

> <span style="color:#7f8c8d;">† 据一个著名且重要的线性代数定理（称为 Perron-Frobenius 定理，Perron-Frobenius theorem），对任意马尔可夫链，平衡方程总存在一个非负解。对于一个具有单个常返类（recurrent class）、且该常返类非周期（aperiodic）的链，其特殊之处在于：在同时给出归一化方程的前提下，解是唯一的，且等于 n 步转移概率 $T_{ij}(n)$（n-step transition probabilities）的极限。</span>
<!-- ===== PDF p364 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）　·　§7.3　稳态行为（Steady-State Behavior，续）</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.6（三状态马尔可夫链的稳态概率求解）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页为 §7.3 中求解平衡方程（balance equations）的第三道示例。页首的示例描述文字已被 OCR 打散成不可读碎片，仅能辨认出零散的 "states: 1, 2" 与 "… example 7.6 …" 字样。既有内容能推断出：这是一个涉及状态 $0$、$1$、$2$ 的三状态链，以参数 $p$ 刻画转移概率，并满足 $0\lt p<1$；本页在演示如何由平衡方程与归一化方程解出各稳态概率 $\pi_j$。**具体转移概率矩阵及链的图形描述（图序、边概率）在上页未能完整保留，以下按可辨认的等式碎片与流通式给出，凡无法确认的系数一律以方括号占位，不回填臆造数值。** 如需逐字原文，请回查原书页 355。</span>

本页承接上一页"关于如何求解平衡方程"的讨论：考察某一个转移概率可用参数 $p$ 表示的三状态链。设稳态概率为 $\pi_0, \pi_1, \pi_2$。由平衡方程（balance equation，即 $\pi_j$ 的流量守恒关系 $\pi_j = \sum_i \pi_i p_{ij}$）与归一化方程（normalization equation）$\pi_0+\pi_1+\pi_2=1$ 联立求解。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 平衡方程的完整形态无法从 OCR 中恢复，仅能辨认出下列两个方程的信息：</span>

```math
\pi_1 = [ \ldots ] + p\, \pi_2, \qquad \pi_1 = \frac{1}{3-p}.
```

```math
\pi_2 = \pi_0 + p\, \pi_1, \qquad \pi_2 = \frac{1}{3-p}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述两式分别为本页可辨认的方程碎片：其左端项（$\pi_1$、$\pi_2$）、含参数 $p$ 的转移项结构、以及解的结果 $1/(3-p)$ 均可确认。但两个方程各自的完整右式（即 $\pi_1$ 的完整线性组合、$\pi_0$ 的具体来源项）中，除 $p\pi_2$ 与 $p\pi_1$ 两项外其余系数被 OCR 抹去，故以 $[ \ldots ]$ 占位，未按教科书常见三状态链的对称形式脑补。</span>

由归一化方程 $\pi_0+\pi_1+\pi_2=1$，并结合上述各 $\pi_j$ 的结果，即可全部确定稳态概率。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页末倒数一行原为关于稳态行为的叙述句（OCR 仅辨出孤立的 "… are"），其完整含义缺失，故此处不展开，仅确认该页正文以对平衡方程解法的说明收束，随后的内容翻入下一页（原书页 356）续接。</span>

---

> 注：本页所属小节为第 7.3 小节"稳态行为（Steady-State Behavior）"，对应平衡方程的求解示例 Example 7.6。由于页顶示例概述与多数转移系数在原 PDF 扫描与 OCR 中严重损坏，本页译文刻意保守——凡无法确证的数值、图坐标与公式系数一律以方括号/灰注占位，不作任何臆造补全。
<!-- ===== PDF p365 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）　·　§7.3　稳态行为（Steady-State Behavior，续）</span>

<span style="color:#2471a3;">**[example]**（续）</span> <span style="color:#2471a3;">**Example 7.6（续）——由两状态推广到 $m$ 个状态的稳态概率求解**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页为上一页 Example 7.6 的延续：上页（原书页 355）已对状态 $1,2$ 的情形求出 $\pi_1=\pi_2=1/(3-p)$，本页（原书页 356）把同一模型推广到 $m$ 个状态。页首与页中大量文字（包括 "5 doors / m doors"、可达性叙述、转移矩阵的完整元素、平衡方程的系数与下标）被 OCR 打散成碎片，仅能辨认出转移概率参数 $p$、$1-p$、若干 $0$ 元素、取值 $\pi_1$、$\pi_i$、$\pi_m$ 与范围 $i=1,\ldots,m$，以及孤立的 $(1-p)\pi_{i-1}$、$+p\pi_m$ 等分项。**以下按可辨识的碎片给出大意，凡无法确证的矩阵元素、边概率与方程系数一律以方括号/灰注占位，绝不回填臆造数值。** 如需逐字原文，请回查原书页 356。</span>

本页承接上页关于求解平衡方程（balance equation）的讨论，将两状态的模型推广到 $m$ 个状态的情形。设链的状态空间为 $\{1, 2, \ldots, m\}$，转移概率以参数 $p$（满足 $0\lt p<1$）来刻画。为便于理解，可借助右侧的转移（概率）图（transition probability graph）观察链的结构。

<span style="color:#2471a3;">**[figure]**</span> 图 7.12：Example 7.6 中针对「$m$ 扇门」情形的转移（概率）图（Transition … in Example 7.6 for the case of … doors）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图 7.12 的节点布置与各条边上的概率数值均无法从 OCR 中读取（出现 "5 doors" 与 "m doors" 两种碎片，具体取哪个数值未知），此处不臆造图的坐标与边概率，请回查原书页 356 的图 7.12。</span>

由此图可以直观地看出：在 $0\lt p<1$ 的假设下，从任一状态都能够在若干步内到达（reachable）另一个状态，因此该链在 $m$ 个状态上 [构成……]。于是其转移概率矩阵（transition probability matrix）$P$ 的各行元素主要为 $1-p$、$p$ 与 $0$：

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 转移矩阵仅在 OCR 中残留若干个 $1-p$、$p$、$0$ 元素，完整位置与行列排布无法确认，此处不给出具体矩阵，仅以灰注说明其组成，请回查原书页 356。</span>

相应的稳态概率 $\pi_1, \ldots, \pi_m$ 由各状态的平衡方程（balance equation）与归一化方程（normalization equation）$\sum_{i=1}^{m} \pi_i = 1$ 联立确定。本页可辨认的方程分项表明，对内部状态 $i$ 其方程涉及 $(1-p)\pi_{i-1}$ 一类的线性组合，对状态 $1$ 与状态 $m$ 则出现相应的端点截断与 $p\,\pi_m$、$\pi_1$ 等项：

```math
\pi_1 = [\,\ldots\,] ,\qquad
\pi_i = [\,(1-p)\,\pi_{i-1} + \ldots\,]\quad (i=1,\ldots,m),\qquad
\pi_m = [\,\ldots\, + p\,\pi_m\,] .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式仅为对本页平衡方程形态的分段还原——能确认的因素包括：左端取值 $\pi_1$ 与 $\pi_m$、取值范围 $i=1,\ldots,m$、以及分项 $(1-p)\pi_{i-1}$ 与 $+p\pi_m$。但每个方程右端完整的系数与下标组合被 OCR 抹去，故以 $[\,\ldots\,]$ 占位，未按常用的对称随机游走形式（如 $\pi_i=p\pi_{i-1}+(1-p)\pi_{i+1}$）脑补。真实方程请回查原书页 356。</span>

联立上述平衡方程与归一化方程，即可解出该 $m$ 态链的稳态概率 $\pi_1,\ldots,\pi_m$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页末一行原文为继续叙述性的收束句（OCR 仅辨出 "once we reach …" 即「一旦我们到达……」等片段），其完整含义缺失，此处不展开，仅确认本页正文以对 $m$ 态链平衡方程解法的说明收束，随后翻入下一页（原书页 356 之后）续接。</span>

---

> 注：本页为第 7.3 小节「稳态行为（Steady-State Behavior）」中求解平衡方程示例 Example 7.6 的延续页（页首无新节/新标题，内容明显在续讲上例的 $m$ 态推广），故标题标为「续」。由于本页正文、转移矩阵与平衡方程在原 PDF 扫描与 OCR 中严重损坏，译文刻意保守——凡无法确证的数值、图坐标与公式系数一律以方括号/灰注占位，不作任何臆造补全。
<!-- ===== PDF p366 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span> — §7.3 稳态行为（Steady-State Behavior）（续）

> <span style="color:#7f8c8d;">本页页眉为「Sec. 7.3 Steady-State Behavior（稳态行为）」。页首承接上一页（p365）「m 扇门、按循环顺序使用」的例题（见图 Figure 7.12），故标题带「（续）」。该例题即 p364–p365 已确认的 Example 7.6（其 $m$ 门推广），此处续接该编号。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.6（续）——门（循环）链例题续：稳态概率均匀分布与周期性讨论**</span>

……每一扇门（door）都应具有**相同的稳态概率（steady-state probability）**。这提示解为

```math
\pi_j = \frac{1}{m}, \qquad j = 1, \dots, m .
```

确实，我们可看到这些 $\pi_j$ 满足**平衡方程（balance equations）**，也满足**归一化方程（normalization equation)**，因此它们必为所求的**稳态概率（steady-state probabilities）**（依据稳态收敛定理的唯一性部分）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这条例题表面上只是「猜一个答案再对一对」，实际是稳态理论最省力的用法：symmetric guess（对称性猜测）不是投机，而是把一个 $m$ 维方程组压成一个标量的合法推理。要看清为什么合法，得把原文那句「依据稳态收敛定理的唯一性部分」拆成三件独立的事——稳态分布的定义式、验证的三个条件、唯一性成立的前提。三者缺一，猜解就只是巧合。
>
> 先回到第一性原理。balance equation（平衡方程）说的不是「概率不再变化」也不是「时间停住」，而是概率流守恒：在长期里，单位时间内离开状态 $j$ 的质量，必须等于从别处流进 $j$ 的质量。这正是 $\pi = \pi T$ 这一行向量等式的逐分量写法，再配上非负性与 $\sum_j \pi_j = 1$ 这条 normalization（归一化）约束。几何上，这 $m$ 个 linear equation（线性方程）加一个 affine constraint（仿射约束）在 probability simplex（概率单纯形）上切出一个 convex set（凸集）；而「解唯一」不是线性代数白送的，是链的结构给的——只有当链是 single class（单个类）时，那个凸集才退化成一点。
>
> 于是「代入验证」为什么够用就有了答案：只要写下的向量同时满足非负、和为一、以及 $\pi = \pi T$ 三件事，它就已经是 stationary distribution（平稳分布）；再由 single class（单个类）保证的唯一性，它必然是那唯一的一个。不必会解方程组，只要有一台能核对等式的机器。
>
> 对称性论证的严格版本是 permutation invariance（置换不变性）。若存在状态集到自身的 permutation（置换），既保持链的转移规律不变（把这个置换同时作用到 transition matrix（转移矩阵）的行与列上，矩阵不动），又能在整个状态集上 transitive（传递，即任两状态都可由某个置换送到），则任何平稳分布都必须在这个置换的每条 orbit（轨道）上取常值。这里的 transitive（传递）必须与 irreducible（不可约）分开：transitive 讲的是 permutation group（置换群）把任意一点送到任意一点，是单向可送达；irreducible 讲的是图上的 accessibility（可达性），是状态之间互相能到。两者名字里都带「到处通」的意思，判据却完全不同，混用会在下一步读多类链时出错。传递性把轨道并成一条，常值就升级为全局常数，再由归一化钉死成 $1/m$。机制是「对称性把 $m$ 个未知数压成 1 个」，而不是「每扇门看起来一样」这种视觉判断。
>
> 还有一条更硬的判据，连对称性都不必谈：若 transition matrix（转移矩阵）每列之和也为 1，即 doubly stochastic（双随机）矩阵，则全一行向量是它的 right eigenvector（右特征向量，对应 eigenvalue（特征值）1），于是均匀向量同时是 $T$ 的 left eigenvector（左特征向量），直接满足 $\pi = \pi T$。这一条只要求查列和，是纯算术验证。Strang 18.06 的语言里，稳态问题就是求 $T^{\top}$ 在 $\lambda = 1$ 处的特征向量；Perron–Frobenius theorem（佩龙–弗罗贝尼乌斯定理，Perron 1907 处理正矩阵、Frobenius 1912 推广到不可约非负矩阵）保证 spectral radius（谱半径）为 1、在此处单重且特征向量可取非负值。再往上一层，Birkhoff 1946 证明双随机矩阵恰是 permutation matrix（置换矩阵）的 convex combination（凸组合，Birkhoff–von Neumann theorem，von Neumann 1953 补了另一条路径）——双随机链就是「随机挑一个置换再执行」的混合，均匀分布显然不动。
>
> 补一刀：唯一性与收敛性不同。平稳分布的存在唯一只需要 single class（单个类）；而 n-step transition probability（$n$ 步转移概率）真正收敛到极限，还需要 aperiodic（非周期）。下一段正是在说这件事：$p$ 取 0 或 1、或 $m$ 取偶数时，链仍只有一个 recurrent class（常返类），却是 periodic（周期的），转移概率不收敛。此时 $\pi_j = 1/m$ 依然唯一，但按本书对 steady-state probability（稳态概率）的定义（要求极限存在），严格说它只是时间平均意义下的极限，即 long-term fraction of time（长期时间比例）那一支。读者若把「唯一性」直接当成「收敛性」，在这两个端点上会算错。
>
> 代价值得记一笔。稠密情形解 $m$ 元线性方程组是 $O(m^3)$；本链若保留 tridiagonal（三对角）结构，Gaussian elimination（高斯消元）能压到 $O(m)$；猜解验证只是一次矩阵向量乘法，$O(m)$ 次乘加。这套路子在别处也出现：无向图上的 PageRank（网页排名）因转移矩阵双随机而均匀，加了 dangling node（悬挂节点）修正后不再双随机，于是出现偏置；Markov chain Monte Carlo（马尔可夫链蒙特卡洛）里 detailed balance（细致平衡）是比平衡方程更强的充分条件，reversible chain（可逆链）靠它把目标分布建成平稳分布。
>
> 反例留给「看起来对称」。若链由两个互不连通的 closed block（闭合块）组成、各块内部均匀而块间权重任意，平衡方程与归一化照样成立，解却是一整条线段而不是一点，此时猜 $1/m$ 立刻错。transitive（传递）这个前提不能省：对称性论证只在置换作用 transitively（传递地）作用时才能把常值推成全局常数。所以可靠流程是两件一起做——代入验证等式，并确认 single class（单个类，保证唯一）。缺任一件，猜解就退回巧合。

注意到：若 $p = 0$ 或 $p = 1$，此链仍只有一个**常返类（recurrent class）**，但它是**周期的（periodic）**。在这种情况下，**n 步转移概率（n-step transition probabilities）** $T_{ij}(n)$ 不收敛到极限，因为门是按**循环顺序（cyclic order）**使用的。类似地，若 $m$ 为偶数，此链的常返类也是周期的，因为状态可分成两个子集——编号为偶数与编号为奇数的状态——使得从每个子集出发只能进入另一个子集。

---

<span style="color:#c0392b;">**Long-Term Frequency Interpretations（长期频率解释）**</span>

概率常被解释为在一串**无限长的独立试验（independent trials）**中的**相对频率（relative frequencies）**。马尔可夫链的稳态概率尽管缺乏独立性，却也有着类似的解释。

考虑例如一台机器的马尔可夫链，它在任一天结束时可能处于两个状态之一：**正常工作（working）**或**损坏（broken down）**。每当它损坏时，会立即以 1 美元的成本被修复。我们应如何对**每日期望修理成本的长期均值（long-term expected cost of repair per day）**建模？一种可能做法是把它看成在**遥远的未来（far into the future）**随机挑选的某一天修理成本的**期望值（expected value）**；这正是损坏状态的稳态概率。另一种做法是计算在 $n$ 天内的总期望修理成本——其中 $n$ 很大——再把它除以 $n$。直觉表明这两种计算方法应给出相同结果。理论支持了这种直觉，并且一般而言我们有以下关于稳态概率的解释（其论证见章末习题）：

---

<span style="color:#00838f;">**[定义] Steady-State Probabilities as Expected State Frequencies（稳态概率作为期望状态频率）**</span>

对具有**单个类（a single class）**且**非周期（aperiodic）**的马尔可夫链，其**稳态概率（steady-state probabilities）** $\pi_j$ 满足

```math
\pi_j = \lim_{n \to \infty} \frac{V_{ij}(n)}{n},
```

其中 $V_{ij}(n)$ 是从状态 $i$ 出发、在前 $n$ 次转移内访问状态 $j$ 的次数之**期望值（expected value）**。

基于这一解释，$\pi_j$ 是**状态等于 $j$ 所占时间的长期期望比例（long-term expected fraction of time）**。每次访问状态 $j$ 时，有概率 $p_{jk}$ 使下一次转移把我们带到状态 $k$。由此我们可得出结论：$\pi_j p_{jk}$ 可以……

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个定义做的是换轴：把 $\pi_j$ 从「$n$ 很大时 $X_n$ 等于 $j$ 的概率」换成「一条轨道上访问 $j$ 的次数所占的长期比例」。前者是 ensemble average（系综平均），后者是 time average（时间平均）；断言二者相等，就是 ergodicity（遍历性）这句话的全部内容。它的分量在于可操作性——不需要知道 initial distribution（初始分布）、不需要解矩阵，只要跑一条轨道数次数。
>
> 先把定义的结构读准。$V_{ij}(n)$ 是访问次数的 expected value（期望值），不是随机次数本身；除以 $n$ 得到的仍是期望频率。除以 $n$ 而非 $n+1$ 属于约定：前 $n$ 次转移对应 $n$ 个时刻（若把时刻 0 也计入则是 $n+1$ 个），这个差别在极限里消失，但手算小 $n$ 的例子时会对不上——这是本类定义最常见的 off-by-one（差一错误），不必怀疑自己算错。
>
> 为什么次数占比就等于时间占比？因为在离散等步长的链里，每次访问恰好占一个时刻，$V_{ij}(n)$ 的归一化正是指示函数之和的期望，也就是概率的平均。读者若改到连续时间，这个换算就要换成 sojourn time（停留时长）——占时间的不是访问次数，而是每次停留的期望长度，两套口径不可混用。
>
> 关键的一步升级藏在下一页（PDF 第 367 页）那句「还有一些更强的命题也成立」里。本页只把结论说成 expected state frequency（期望状态频率），下一页才把它升到轨道层面：对一条实际观测到的 sample path（样本路径），长期访问频率随概率 1 趋于 $\pi_j$。两句话的差别是「期望相等」与「几乎必然相等」，后者才是 ergodicity（遍历性）通常的被引形式。这就是 pointwise ergodic theorem（逐点遍历定理，Birkhoff 1931）在有限状态链上的特例，也可以看成相依序列版本的 strong law of large numbers（强大数定律）。这一步不是形式主义：工程现场只给你一条轨道，若结论只停在期望层面，就无法保证单次实验的可复现性。更弱的版本是 von Neumann 1932 的 mean ergodic theorem（均值遍历定理），即均方意义下的收敛，对本课程足够，但读者要知道两者差别。
>
> 再看它与平衡方程的关系。$\pi_j = \sum_k \pi_k p_{kj}$ 的右端正好是「从各个状态流进 $j$ 的频率」，左端是「$j$ 占用的时间比例」；两句话说的是同一件事的两面——一个刻画质量在概率空间里怎么挪，一个刻画状态在时间轴上占多久。本页正文之所以能从「时间占比」直接推出「流入等于占比」，靠的就是这个等价。
>
> 正文给的那台「任一天结束时或正常或损坏、损坏即花一美元修好」的机器（PDF p366 那段 long-term expected cost of repair per day）可以验证这套读法：每日期望修理成本的长期均值就是 $\pi_{\mathrm{broken}} \times 1$ 美元。两种算法（在遥远的未来随机挑一天、以及把 $n$ 天总成本除以 $n$）能给出同一答案，依赖两件事——ergodicity（遍历性）保证时间平均等于系综平均，成本取 0 或 1 的有界性保证极限与期望可以交换。若单次成本无界，还需要 uniform integrability（一致可积）才能交换，这是实分析里交换极限与积分那套条件在概率里的翻版。
>
> 跨课程连接：排队论里的 utilization（利用率），即服务器忙碌的时间比例，就是这个 $\pi_{\mathrm{busy}}$；CSAPP 里的 CPI、cache（缓存）命中率同样是时间占比口径，硬件性能计数器量的本来就是 $\pi$。要当心 CLRS 的 amortized analysis（均摊分析）——它看着也像「长期平均」，但那是确定性操作序列上的均摊分析，不需要任何概率假设，与本节的时间平均不是同一个东西。
>
> 一个可以手验的小例：两状态链里 0 以概率 0.8 留驻、以 0.2 跳到 1，而 1 以 0.6 留驻、以 0.4 回到 0。平衡方程给出 $0.2\,\pi_0 = 0.4\,\pi_1$，配合归一化得 $\pi_0 = 2/3$、$\pi_1 = 1/3$；反向核对流量 $\pi_0 \times 0.2 = \pi_1 \times 0.4$ 两边同为 $2/15$，一致。这种「先解再核对流量」的两步检查，比单纯相信矩阵运算更能发现系数抄错。
>
> 反例留给周期链。若链是 periodic（周期的），则极限 $\lim_n P(X_n = j)$ 不存在，而 $\lim_n V_{ij}(n)/n$ 依然存在——次数累计是 Cesàro 平均，比逐项极限更宽容。所以「时间占比」这条读法比「极限概率」更稳，教材先讲频率解释、后补 aperiodic（非周期）条件，正是这个次序：先给不怕周期性的那个量，再谈什么时候逐项收敛。
<!-- ===== PDF p367 ===== -->

<span style="color:#c0392b;">**§7.3　稳态行为（Steady-State Behavior）——长期频率解释（Long-Term Frequency Interpretations）**（续）</span>

> <span style="color:#7f8c8d;">本页为上一页 §7.3 中「长期频率解释（Long-Term Frequency Interpretations）」一节的直接延续（页首无新节标题），承接上页末尾「…we can conclude that $\pi_j p_{jk}$ can …」一语，继续阐释平衡方程（balance equation）的频率意义。</span>

> <span style="color:#7f8c8d;">⚠ 本页 OCR 严重损坏：几乎全部为散落残词与乱码，多数句子无法完整重组。下方仅译出可辨认的词组与分句；凡无从辨认处一律以灰色占位注释标出，绝不臆造数值、图坐标或公式系数（如需最严格原文，请回查原书页 357）。</span>

本页承接关于一个只有单一常返类 aperiodic（非周期）链 `with a single class which is aperiodic` 之稳态概率的讨论，继续阐明 $\pi_j$ 的频率解释 `the frequency interpretation of $\pi_j$`，并述及如下的极限公式片段：

```math
\pi_j = \lim_{n \to \infty} \frac{?}{n}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式应承接上一页「期望状态频率」叙述中的极限式（上页残文为 $\pi_j = \lim_{n\to\infty} V_{ij}(n)/n$），本页分子部分 OCR 只剩「$(n)$」残片，无法确认是否与上页相同，故以占位「?」表示，不臆断。</span>

随后页文给出该平衡关系的直观含义 `has an intuitive meaning`，并指出它表达了如下事实 `It expresses the fact that`：期望频率 $\pi_j$ 等于各项 $\pi_k p_{kj}$ 之求和 `the sum $\sum_k \pi_k p_{kj}$`。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 句中出现多处引导短词（「of …to $j$ …a very …from $k$ to $j$…」「In …number of transitions, we expect a fraction $\pi_k p_{kj}$ that bring the state …」）及残句「…the balance …in terms of …」，因乱码重叠无法还原完整原文；可辨主旨为：在大规模转移中，期望比例的转移由 $k$ 进入 $j$，其期望频率与由 $j$ 离开的转移频率相平衡。</span>

括号内插入语亦只有残片：

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 方括号插入句（残文「(This also …to transitions from $j$ to …which occur with …of such transitions is the …」）只能辨认大意（关于由 $j$ 至 $k$ 的转移及其发生的期望频率），英文原句无法还原。</span>

在状态 $j$ 处，诸期望频率之和 `the sum of the expected …at state $j$` 该给出……（下句残缺）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 该句及其后接续叙述（含 「…of …」残词）分散在乱码中，含义仅能部分推断，未满句无法翻译。</span>

事实上，还有一些更强的命题也成立 `some stronger statements are also true, such as the following`：每当我们进行一次概率实验并观测马尔可夫链的一条样本轨道 `a trajectory of the Markov chain`，则…状态 $j$ 是…所观测到的长期 `the observed long-term` 转移频率…尽管轨道本身是随机的 `Even though the trajectory is random`，…

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 此段为公司中「被观测的长期状态/转移频率几乎必然（with probability 1）趋于 $\pi_j$」的更强断言，页尾仅存分条编号「1.」与若干残词，其英文原文因污迹无法辨认，以上仅译出可辨片段；原文后续应续接至下一页。</span>
<!-- ===== PDF p368 ===== -->
<span style="color:#c0392b;">**§7.3　稳态行为（Steady-State Behavior）—— 生灭过程的稳态分布（Birth-Death Processes，续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页从一句子的中部开始（「……引入了转移概率的一般记号」），延续上一页 §7.3 中关于「生灭过程（birth-death process）」稳态概率求法的推导，故本章节标题加「（续）」。页首无明显新节标题。</span>

……这里引入了转移概率（transition probabilities）的一种一般记号（generic notation）。具体地，记状态 $i$ 的**出生概率**（birth probability），即从状态 $i$ 转移到状态 $i+1$ 的概率，为 $b_i$；（相应地，记状态 $i$ 的**死亡概率**（death probability），即从状态 $i$ 转移到状态 $i-1$ 的概率，为 $d_i$）。

<span style="color:#7f8c8d;">图 7.14　生灭过程的转移概率图（transition probability graph for a birth-death process）。</span>

> <span style="color:#7f8c8d;">[原页此处图注内容 OCR 残缺] 图 7.14 的具体图形与各转移系数（$b_i$、$d_i$）在图上的标注位置在本页 OCR 中无法辨认（原文仅见捕捉到的图题 IN 及零星图片噪点）。此处仅给出图题大意，图中方向与系数请以原书页 368 为准，不作臆造。</span>

因为稳态概率 $\pi_i$ 表示长期中，被访问状态等于 $i$ 的期望时间比例（long-term expected fraction of time that the state is equal to $i$），每当状态 $i$ 被访问时，下一次转移使系统到达状态 $i+1$ 的概率为 $b_i$。因此，从 $i$ 到 $i+1$ 的这类转移的**期望频率**（expected frequency of transitions）为 $\pi_i b_i$；同理，从 $i+1$ 到 $i$ 的相应频率为 $\pi_{i+1} d_{i+1}$。在稳态下，跨过这两个状态之间界线的流量必须相等，由此得到一组**局部平衡方程**（local balance equations）

```math
\pi_i\, b_i = \pi_{i+1}\, d_{i+1}, \qquad i = 0, 1, \ldots, m-1.
```

利用这组局部平衡方程，并结合**归一化条件**（normalization）$\sum_{i=0}^{m}\pi_i = 1$，稳态概率 $\pi_i$ 可以递推求出如下。由局部平衡方程出发，从 $i$ 到 $i+1$ 解出

```math
\pi_{i+1} = \pi_i\,\frac{b_i}{d_{i+1}}, \qquad i = 0, 1, \ldots, m-1,
```

反复迭代即得

```math
\pi_i = \pi_0\,\frac{b_0\, b_1 \cdots b_{i-1}}{d_1\, d_2 \cdots d_i}, \qquad i = 1, \ldots, m,
```

而 $\pi_0$ 再由归一化方程 $\sum_{i=0}^{m}\pi_i = 1$ 唯一确定。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一节做的事情是把 $m+1$ 个全局平衡方程换成 $m$ 条彼此独立的一维方程。状态是 $0,1,\dots,m$ 共 $m+1$ 个，全局写法 $\pi_j = \sum_k \pi_k p_{kj}$ 因此就有 $m+1$ 条等式；但它们是 linearly dependent（线性相关）的——rank（秩）只有 $m$，比如四状态生灭链的 $\mathrm{P}^{\top}-I$ 秩为 3，可以直接用数值验算，独立方程只有 $m$ 条，必须靠归一化才凑成唯一解。所以「有一条多余」的准确说法是「$m+1$ 条里独立 $m$ 条」。local balance equation（局部平衡方程）给出的 $\pi_i b_i = \pi_{i+1} d_{i+1}$ 是逐条边界上的双边等式，形式更强，却恰好在这个结构下自动成立；局部平衡也正好是 $m$ 条（$i = 0,1,\dots,m-1$），与独立方程数对齐，这不是巧合，它本来就是把全局方程组重新参数化的结果。
>
> 第一性原理是 cut argument（截断论证）。把状态集切成左右两半 $\{0,\dots,i\}$ 与 $\{i+1,\dots,m\}$，在稳态下跨过这条切口的净流量必须为零：若不为零，质量会在某一侧无限累积，稳态就不可能。生灭链的跳跃半径恰为一，因此只有一条边连接两半，净流量为零这个条件就退化成单独一条等式。这解释了为什么局部平衡不是额外假设，而是「相邻性加稳态」推出来的必然结果。
>
> 同一套方程在电网络里有现成的名字。给每条边配上 conductance（电导）$c_i = \pi_i b_i$，局部平衡立刻变成 Kirchhoff 的 current law（电流定律）：每个节点流入等于流出，局部平衡等价于「每条边的净电流为零」，这一条本身不含电势，birth rate（出生率）与 death rate（死亡率）之比就是相邻电导之比。这条同构在 Doyle 与 Snell 1984 年的《Random Walks and Electric Networks》里被系统化，它的好处是把「求稳态概率」翻译成「求串并联电阻」——后面那个连乘公式，本质就是电导连乘。
>
> 这条同构还顺带说明了一个不太直观的事实：生灭链的稳态分布不是随便什么分布都能当的。递推只给出相邻两项的比值，于是整条分布被这串比值完全决定——反过来，给定任何正的概率向量，只要取 $b_{k-1}/d_k$ 等于相邻比值，就能反解出一对 birth rate（出生率）与 death rate（死亡率），使它以该向量为稳态。这是「逆构造」的原型：MCMC 里设计 transition kernel（转移核）时，正是先钉住目标分布，再按它反推 reversible（可逆）的转移概率。
>
> 递推形式 $\pi_i = \pi_0 \prod_{k=1}^{i} \frac{b_{k-1}}{d_k}$ 因此只值两遍扫描：正向推出全部相对值，再除以总和完成归一化，总代价 $O(m)$。这与 tridiagonal system（三对角线性系统）的 Thomas algorithm（追赶法，Thomas 1949）是同一件事——后者同样是前代加回代两趟、$O(m)$，而通用 Gaussian elimination（高斯消元）要 $O(m^3)$。代价低是有条件的：所有 $d_k > 0$，否则连乘会断链，对应到概率上就是某些状态回不去。
>
> 原文接着证明局部平衡与整体平衡相容，那个推导的技巧是 telescoping sum（裂项求和）。把 $m$ 条全局方程相加，中间每一项都出现两次、方向相反、全部抵消，只剩两端；于是只要逐边等式成立，全局等式必然成立。方向要说细一点：逐边平衡推出全局平衡，这个方向对任何链都恒成立——把逐边等式逐条相加就得到全局；反过来，全局平衡推出逐边平衡，只在生灭这样的结构下成立，因为要把「一条切口的净流量为零」归约到「单条边上的净流量为零」，必须依赖每次跳跃只跨一格这条相邻性。一般的链没有这种逐边可分解的结构，这正是生灭链的特殊之处——不是定理更强，而是结构更窄。
>
> 换到矩阵视角，全局平衡方程组的系数矩阵是 identity matrix（单位阵）减去 transition matrix（转移矩阵），稠密而满秩缺一；局部平衡把这同一个系统改写成 tridiagonal（三对角）结构，于是求解从「解一个稠密系统」变成「走一条链」。数值上这就是为什么稀疏化值得做：同一个数学问题换个等价写法，代价差一个量级。
>
> 边界状态 0 的方程 $\pi_0(1-b_0) + \pi_1 d_1 = \pi_0$ 里出现 self-loop（自环）概率 $1-b_0$，那正是 reflecting boundary（反射边界）的标记：不可能向下跳出。这个细节不只是记账：只要某处 $1-b_i-d_i > 0$，链就 aperiodic（非周期），转移概率本身收敛；若所有 self-loop（自环）为零，链可能是 periodic（周期的），这时只有 Cesàro 平均意义下的极限还存在。
>
> 应用上最值钱的例子是 M/M/1 排队。取 $b_i = \lambda$、$d_i = \mu$ 与状态无关，递推给出 $\pi_i = (1-\rho)\rho^{i}$，即 geometric distribution（几何分布），其中 $\rho = \lambda/\mu$ 就是 utilization（利用率）。它要求 $\rho < 1$，否则归一化常数发散——无限缓冲的队列在过载时根本没有稳态，这正是「有限缓冲能兜住过载、无限缓冲不能」的定量版本。
>
> 陷阱在于把局部平衡当成普适工具。逐边平衡只在 reversibility（可逆性）成立时可用，判据是 Kolmogorov's criterion（柯尔莫哥洛夫判据）：任一 cycle（环）上正向转移概率之积等于反向之积。跨越超过一步的跳跃、或者状态图上存在多条并行 path（路径）的链，一般都不满足，此时只能退回全局平衡方程老老实实解。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上面两式的系数形态在本页 OCR 中严重残缺：原文仅见「$0,1,\ldots,m-1$」（第 46 行）、「$i=1,\ldots,m$」与「归一化（the normalization）条件」等片段，以及若干被打散的 $\pi_i$、$b_i$、$d_i$ 碎片（如 $\pi_1(1-b_1-d_1)$、$\pi_0 b_0$ 等）。此处按生灭过程「流量平衡 $\pi_i b_i = \pi_{i+1} d_{i+1}$ 逐环递推」的标准方法还原为以上等价形式；分子分母乘积的具体次序（$b$ 连乘在上、$d$ 连乘在下）与原书是否逐符一致请以原书页 368 为准，如需最严格原文请回查原书。</span>

> <span style="color:#7f8c8d;">(footnote) 一更形式化的论证（A more formal approach）：[原页此脚注在此处 OCR 仅捕捉到「A more formal」一词，后续论证内容无法辨认，留待原文确认。]</span>

这些局部平衡方程事实上与**整体平衡方程**（balance equations）相容，即它们并不会与整体平衡方程相矛盾。特别地，注意从状态 $0$ 出发只能发生向右的转移，即到达状态 $1$，故状态 $0$ 处唯一可能的外部到达来源于状态 $1$。于是状态 $0$ 的平衡方程为

```math
\pi_0\,(1 - b_0) + \pi_1\, d_1 = \pi_0,
```

两边消去 $\pi_0$ 后即化简为

```math
\pi_0\, b_0 = \pi_1\, d_1,
```

这恰是 $i=0$ 情形的局部平衡方程。类似地，对于 $i = 1, \ldots, m$ 的任一中间状态 $i$，其平衡方程为

```math
\pi_{i-1}\, b_{i-1} + \pi_i\,(1 - b_i - d_i) + \pi_{i+1}\, d_{i+1} = \pi_i,
```

将它重新整理（this is rewritten），并代入相邻位置的局部平衡关系 $\pi_{i-1} b_{i-1} = \pi_i d_i$（即上一状态处，at the previous state）与 $\pi_i b_i = \pi_{i+1} d_{i+1}$ 后，可两边相消、恒等地成立。因此这些局部平衡方程与整体平衡方程一致。由此，一旦由归一化确定出 $\pi_0$，我们便可继而求出其余所有状态的稳态概率（steady-state probabilities of all states）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 中间状态 $i$ 平衡方程的具体三项系数（$\pi_{i-1} b_{i-1}$、$\pi_i(1-b_i-d_i)$、$\pi_{i+1} d_{i+1}$）在本页 OCR 中残缺（原文仅见几个碎片如「$\pi_0(1-b_0)+\pi_1 d_1=\pi_0$」「$\pi_0 b_0+\pi_1(1-b_1-d_1)+\cdots=\pi_1$，化简为 $\pi_1 b_1=\cdots$」及「$\pi_1 d_1$ 上一状态处」），按生灭链标准平衡方程还原为上述等价形式；$b$、$d$ 的具体位置与下标范围请以原书页 368 为准。</span>
<!-- ===== PDF p369 ===== -->

<span style="color:#c0392b;">**§7.3　稳态行为（Steady-State Behavior）——生灭过程的局部平衡与随机游走（续）**</span>

> <span style="color:#7f8c8d;">本页为上一页 §7.3 中关于**生灭过程（birth-death process）**局部平衡方程（local balance equations）讨论的延续（页首无新节标题，页眉「Sec. 7.3 Steady-State Behavior」），继续衔接上页「…the local balance equations for a birth-death process…」与 Figure 7.14，并引出 Figure 7.15 的随机游走（random walk）特例，随后于页尾开始一个新的缓冲/分组存储例题（见页尾灰注）。例号无法从本页 OCR 确认，故不以「Example 7.z」断言编号。</span>

> <span style="color:#7f8c8d;">⚠ 本页 OCR 损坏极端严重：几乎整页为散落残词与乱码，多数句子无法完整重组。下方仅译出可辨认的词组与分句；凡系数、指数、图坐标、数值无法辨认处一律以灰色占位注释标出，**绝不**按教科书常见内容臆造（如需最严格原文，请回查原书页 369）。</span>

本页承接上文的随机游走叙述「but if …」，页面可辨内容如下。

关于行走在一条线上、状态为位置 $1,\ldots,m$（positions）的**随机游走（random walk）**，若身处两端的某个边界位置，则越界移动会被禁止或反射：即当处于位置 1（或相应地位置 $m$）时，移出范围到位置 0（或位置 $m+1$）的转移概率视为 0，或者等价地**瞬间被反射返回**位置 1 `instantly reflected back to position 1`（或位置 $m$，respectively）。等价地 `Equivalently`，我们可假设当人处于该边界位置时，将**停留**在该位置 `will stay in that position`。

于是考查一个**生灭链模型（birth-death chain model）**，其状态为位置 $1,\ldots,m$。该链的（转移概率图）见 Figure 7.15（随机游走情形）：

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图题式为「Fig. 7.15: Transition probability graph for the random walk」（OCR 残字「7.15 : Transition probability … for the random walk」）。图中指向相邻状态的两个转移概率标号显然为 $[\cdot]$ 与 $1-[\cdot]$ 两个互补值（OCR 残出「1 − b」「b」），但具体是多少、边界反射处的自环/转向概率为何值，由于图上标号破损无法确认，一律以占位表示，绝不臆造。</span>

在此基础上，页文陈述**局部平衡方程（local balance equations）**：

> <span style="color:#2471a3;">**[关键公式]** The local balance equations are …</span>

```math
\pi_i\,[\text{邻状态转移系数}] = \pi_{i+1}\,[\text{邻状态转移系数}],\qquad i = 1,\ldots, m-1 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 局部平衡方程式的确切系数破损（OCR 仅残出「$p$」「$b$」「$1-b$」等零散符号，无法判定究竟为 $\pi_i b = \pi_{i+1}(1-b)$、$\pi_i b_i = \pi_{i+1} d_{i+1}$ 还是其它），故系数一律以括号占位表示，不按教科书默认形式补全。</span>

继而页文指出：利用这些方程，可将 $\pi_j$（OCR 残字「$\pi_j$ in terms …」）用 $\pi_1$ 表达出来 `we can express … in terms of …`，即对 $i=1,\ldots,m-1$ 有下面的递推形态：

```math
\pi_{i+1} = \pi_1 \cdot [\rho^i],\qquad i = 1, \ldots, m-1 ,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 三角递推的底/比值 $\rho$（OCR 残出「$P$」「$p$」，疑为一步比值 $\rho = b/(1-b)$、$p/(1-p)$ 或 $b/d$ 之类）的具体表达式无法辨认，指数 $i-1$ 亦来自相邻残行推断，故以占位 $[\rho^i]$ 表示，不臆断。</span>

再结合**归一化条件（normalization condition）** $\pi_1 + \cdots + \pi_m = 1$，即得 $\pi_1$ 的表达式（OCR 残文「$\pi_1 = \dfrac{1}{1 + P + \cdots + P^{m-1}}$」，「if $P = 1$ …are equally likely」）：

```math
\pi_1 = \frac{1}{1 + \rho + \cdots + \rho^{\,m-1}} ,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 当比值 $\rho = 1$ 时，各状态概率相等（「…are equally likely」）。该归一化推导的中间步骤与 $\rho=1$ 情形是否翻页统一切割、以及上式是否与随机游走或后述缓冲例题的 $m$ 个状态对应，因 OCR 乱码无法完全判定。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页中段残出「…7.8.」之编号，但依上下文既可读作公式编号 (7.8)，也可能为某例题号「Example 7.8」；因上下文乱码无法锁定，此处不臆断其归属，仅作记录备查。</span>

---

页尾开始一个新的叙述段，涉及**分组/缓冲存储（packet / buffer storage）**问题（应为 §7.3 中一个新的马尔可夫链例题）：

在一个**节点（node）**中，为避免冲突，任意给定时刻至多能发生**一个事件（at most one event）**——即一个新**分组（packet）**的到达 `an arrival of a new packet …`；被**存储（stored）**于**缓冲区（buffer）**中，随后**被传输（then transmitted）**。该缓冲区的**存储容量（storage capacity）**为 …；若缓冲区中已有 $m$ 个分组 `if $m$ packets are already present`，则……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页尾开启的新例题（缓冲/分组存储）仅存开头几句残文（「in a buffer」「storage capacity」「if $m$ packets are already present」「at most one event can happen in the node (an arrival of a new packet …)」「then transmitted」「newly」），其后应定义传输或缓冲区状态、以及何时分组被拒绝/等待的具体规则，但这些内容翻页续接且本页 OCR 已断，无法翻译，留待下页。</span>
<!-- ===== PDF p370 ===== -->
<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.7（通信链路缓存，Buffer over a communication link，稳态分析）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页页首无新小节/新标题，内容是上一页 p369 已经开始的 Example 7.6 缓存（buffer）模型的延续，故标题标注「续」。示例编号 7.6 系按第 7.3 节（§7.3 稳态行为 Steady-State Behavior）内例子连续编号并参照本页指向的图 7.16（Figure 7.16）承接 p369 的 Example 7.5 随机游走反射（random walk with reflecting barriers，图 7.15）反推所得；若原书编号有出入，以后续统一校验为准。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页整页 OCR 破损严重：模型条件句、转移图边标、以及多个方程/符号（如 $b$、$d$、$\rho = b/d$、式 7.9 编号）均被打散成孤零零的碎片。下列翻译按上游公式收尾（$\pi_{i+1}=\rho\pi_i$、归一化 $1=\pi_0+\dots+\pi_m$、$\rho\neq1$ 与 $\rho=1$ 两情形的稳态解）并在可辨认碎片（$1-b-d$、$1-b$、$m+1$、$\pi_i=\rho^i\pi_0$）支撑下重建；所有未见明文、仅靠惯例补全的细节均以灰注标注，绝不臆造。</span>

设该缓存可容纳至多 $m$ 个数据包（packets）。在一个时隙（time slot）内我们假设至多下列事件之一（only one of the following occurs）发生：

- **(a) 一个新数据包到达（one new packet arrives）并存入缓存**，其概率为 $b > 0$；
- **(b) 若节点中至少有一个数据包，则一个数据包离开（one packet departs）**，其概率为 $d > 0$；否则（otherwise）其概率为 $0$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (b) 项行被破坏（OCR 仅剩 "o ot herwise;"），完整条件子句「若至少有一个包则以概率 $d>0$ 完成传输、否则为 0」依源书对离开事件的规范表述补全。离开/发送的具体条件以原书为准。</span>

- **(c) 没有新事件发生（no new event happens）**，其概率为 $1 - b - d$，如果……（if …）；否则（otherwise）其概率为 $1 - b$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (c) 项中的两个条件子句（"if…" 及 "otherwise" 所对应的状态）在 OCR 中残缺不清，无法确定是「缓存未满/未空」还是「缓存已满/已空」等具体条件；此处仅按可辨认片段给出概率 $1-b-d$ 与 $1-b$，条件本身留白待原书复核。</span>

我们引入一个马尔可夫链（Markov chain），其状态为 $0,1,\ldots,m$，对应缓存中的数据包数（states $0,1,\ldots,m$, corresponding to the number of packets in the buffer）。其转移概率图（transition probability graph）见图 7.16（Figure 7.16: Transition …）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图 7.16 的具体坐标与全部边标残缺（仅能辨出 $1-b-d$、$\ldots-d$、$d$、$d$、$d$ 等碎片），未能完整还原。依照生灭过程（birth-death process）的结构定性描述如下：自状态 $i$ 以概率 $b$ 跃迁至 $i+1$（到达），以概率 $d$ 跃迁至 $i-1$（离开），在内部状态自环概率为 $1-b-d$，而在边界状态 $0$ 与 $m$ 处自环概率分别为 $1-b$ 与 $1-d$（因空/满时只能有一种可能事件）。图为教科书 §7.3 典型框（square）图，非本页完整复原，仅供参考。</span>

局部平衡方程（local balance equations）为 $i = 0,1,\ldots,m$：

```math
\pi_{i}\, b \;=\; \pi_{i+1}\, d, \qquad i = 0,1,\ldots,m-1,
```

从而得到 $\pi_{i+1} = \rho\,\pi_i$，其中 $\rho = b/d$；由此递推得出（引向式 7.9，Equation 7.9）：

```math
\pi_i = \rho^{\,i}\,\pi_{0}, \qquad i = 0,1,\ldots,m .
```

利用归一化条件 $1 = \pi_0 + \pi_1 + \cdots + \pi_m$（normalization），我们得到

```math
\pi_0 =
\begin{cases}
\dfrac{1-\rho}{1-\rho^{m+1}}, & \text{if } \rho \neq 1,\\[6pt]
\dfrac{1}{m+1}, & \text{if } \rho = 1 ,
\end{cases}
```

再代入 $\pi_i = \rho^{\,i}\,\pi_0$，稳态概率（steady-state probabilities）为

```math
\pi_i =
\begin{cases}
\dfrac{1-\rho}{1-\rho^{m+1}}\;\rho^{\,i}, & \text{if } \rho \neq 1,\\[6pt]
\dfrac{1}{m+1}, & \text{if } \rho = 1 ,
\end{cases}
\qquad i = 0,1,\ldots,m .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末尾式（$\pi_i$ 的分段稳态概率）在 OCR 中仅剩分裂片段（"if $\rho\neq1$"、"if $\rho=1$"、"$i=0,1,\ldots,m$"），两分支的闭合形式 $(\frac{1-\rho}{1-\rho^{m+1}})\,\rho^i$ 与 $\frac{1}{m+1}$ 为依上游公式与归一化条件重建的标准结果；若与原书严格字面有出入，以原书为准。此外页尾 "we assume / following occurs" 一栏显示本模型该处应在缓冲器例子，未扩展为新的编号。原文在此翻页续接。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一页把「有限缓冲的数据包队列」彻底解完：状态 0 到 $m$ 共 $m+1$ 个，到达率与离开率不随状态变化，于是局部平衡给出一个等比关系，整条分布被一个无量纲比值决定。这是 birth-death process（生灭过程）里最干净的一例——解出来的形式叫做 truncated geometric distribution（截断几何分布），它同时也是排队论里 M/M/1/m 模型的标准答案。
>
> 第一性原理只有一句：稳态下每多占一格缓冲，概率就乘上同一个因子 $\rho = b/d$。所以 $\pi_i$ 必然是 $\rho^i$ 乘一个常数——比值恒定，几何就是唯一形态。这也解释了为什么整个分布只依赖一个参数：把 $b$ 与 $d$ 同时放大同一个倍数，比值不变，稳态也不变。这是 scale invariance（标度不变性）的直接后果（在连续时间模型里严格成立，在离散时间版本里要小心 $b+d$ 不得超过 1 的可行域）。
>
> 归一化把常数钉死，于是出现三支。$\rho<1$ 时分母是 $1-\rho^{m+1}$，几何尾巴被 $i \le m$ 切掉，补一个因子把质量重新凑成一；$\rho=1$ 时等比退化为等差数列，结果是 $1/(m+1)$ 的均匀分布；$\rho>1$ 时概率堆在高端，越接近满仓越可能。三支共用一个结构，差别只在等比数列求和时分子分母是否为零。
>
> 一个能心算核对的例子：取 $m=3$、$\rho=1/2$，则 $\pi_0 = \frac{1/2}{1-1/16} = 8/15$，四格依次是 $8/15,\,4/15,\,2/15,\,1/15$，相加恰为 1。任何一次套公式之后都该做这个加法；它比重新推导便宜，却能立刻抓出指数写成 $m$ 而不是 $m+1$ 的错误。
>
> 极限 $m \to \infty$ 才是这一节的重点。$\rho<1$ 时分母趋于 $1/(1-\rho)$，拿回无限缓冲的 $\pi_i = (1-\rho)\rho^{i}$，即标准 geometric distribution（几何分布），归一化常数收敛，一切正常。$\rho \ge 1$ 时情形全变：对每个固定的 $i$，$\pi_i^m$ 都趋于零，但两个分支的机制并不相同，不能合成一句。$\rho>1$ 时质量确实堆到 $m$ 那一端：归一化常数由 $\rho^{m}$ 主导，越靠右的格子分到的比例越大，固定下标 $i$ 上的质量趋于零。$\rho=1$ 时质量不是堆在端点，而是均匀弥散在全部 $m+1$ 个状态上，每个格子占 $1/(m+1)$——对固定的 $i$ 它当然仍趋于零，但这是分母变大把它稀释掉的结果，与「推向某一端」是两回事。把两支混成一句「质量全都推向了 $m$ 那一端」，会和上面 $\rho=1$ 给出均匀分布的结论当场自相矛盾。用概率的语言说：有限 $m$ 的稳态解存在，但它作为 $m$ 的函数不收敛到一个 probability distribution（概率分布）。
>
> 这段的工程价值在于它把「过载」翻译成了一个可计算的判据。利用率 $\rho$ 逼近 1 时，溢出概率 $\pi_m \approx 1/(m+1)$ 只按 $1/m$ 的速度下降，即使把缓冲加倍，溢出率也只减半；这就是为什么负载接近饱和时排队延迟会爆炸式上升，而加大 buffer（缓冲容量）无法根治。反过来，$\rho$ 明显小于 1 时 $\pi_m$ 按 $\rho^{m}$ 指数衰减，加一点缓冲就能把溢出压到极低——同样是加缓冲，两种区域的收益差一个数量级。
>
> 边界并不改变这条链的性质，只改变 self-loop（自环）。状态 0 处不能向下跳，自环概率是 $1-b$；状态 $m$ 处不能向上跳，自环概率是 $1-d$。但跨越每一条边界的两股流量依旧是 $\pi_i b$ 与 $\pi_{i+1} d$，所以局部平衡在 $i=0,\dots,m-1$ 上一字不改地成立——边界影响的是「留在原地的概率」，不影响「跨过去的概率」，这条区分在算 absorption time（吸收时间）之类的量时才显出分量。
>
> 要留意的两个技术细节。其一，$\rho = 1$ 这一支不能由 $\frac{1-\rho}{1-\rho^{m+1}}$ 直接代入得到，那会得到 0/0，必须回到等比数列「$m+1$ 项全部相等」的求和事实，或者用一次 limit（极限）展开。其二，分母的指数是 $m+1$ 而不是 $m$，因为状态从 0 数到 $m$ 共 $m+1$ 个——这类差一错误是套公式时最常见的翻车点，验算办法是取 $\rho=1$ 时结果必须等于 $1/(m+1)$。
>
> 还有一处记号要提防：本页正文在讨论极限时改用 $p$ 表示同一个比值（原文「$b<d$，即 $p<1$」），而前面的公式用 $\rho = b/d$。两者是同一个量，读者不要把 $p$ 误当成单步到达概率。
>
> 跨课程看，这就是排队论里 M/M/1 的有限容量版本；Little's law（利特尔定律）把队列长度的期望与平均等待时间联系起来，配合这里的 $\pi_i$ 就能算出平均队长与平均延迟。CSAPP 讲的流水线缓冲与 TCP 接收窗口，物理形态不同，稳态分析却是同一套方程。
<!-- ===== PDF p371 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）（续）**</span>

本页页首承接上一页「生灭过程 / 排队模型」分析的续讲（§7.3 稳态行为下的无限缓冲两种情形延展）；§7.4 新节自本页中部开始，为「吸收概率与吸收期望时间」。页首未见独立 Example 编号出现在 OCR 中，故按 § 正文续讲标注「（续）」。左侧页眉书为 "Markov Chains　362　Chap. 7"。

> <span style="color:#7f8c8d;">承接上一页：上页给出了缓冲队列模型的稳态概率（steady-state probabilities）$\pi_i^m$（缓冲大小为 $m$），并讨论了缓冲较小、缓冲较大各不相同的情形。本页续接"缓冲大到可视为无界"时的两种情形。</span>

值得考虑的是：当缓冲大小（buffer size）大到可视为实际上无界时会发生什么。我们区分两种情形。

**(a) 假设 $b < d$，即 $p < 1$。** 此时新数据包（packets）到达的概率小于已有数据包离开的概率。这抑制了缓冲中数据包数量的增长，使稳态概率 $\pi_i^m$ 随 $i$ 递减，正如截断的几何概率质量函数（truncated geometric PMF）那样。我们观察到，当 $m \to \infty$ 时，有

```math
\pi_0^m \to 1 - p, \qquad \pi_i^m \to (1-p)\,p^i,\quad \text{对所有 } i .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原页该式标记为 `1 pm l 1` 之类的碎片形式，上式按后续核验注 $\sum_{i=0}^{\infty} p^i(1-p) = 1$ 与几何稳态分布 $\pi_i^m = (1-p)p^i$ 的反查还原为规范 LaTeX；极限下标 $m\to\infty$ 与 $1-p$ 项的真实排布（是 $\pi_0^m\to 1-p$ 还是整体 $\pi_i^m\to (1-p)p^i$）以原书为准。</span>

我们可以把上式视为在具有无限缓冲的系统中得到的稳态概率。[作为核验，注意我们有 $ \sum_{i=0}^{\infty} p^i(1-p) = 1$。]

> <span style="color:#7f8c8d;">[脚注 · 原页此处 OCR 损坏] 原页此处（紧跟"作为核验"的核验注附近）以此为底有一个脚注（OCR 脚注采集到的残片仅为 `m`、`m \to`、`\infty` 等碎字），其完整文字与编号无法辨认，索引关系不明，暂以占位处理，不臆造内容。</span>

**(b) 假设 $b > d$，即 $p > 1$。** 此时新数据包到达的概率大于已有数据包离开的概率。缓冲中数据包的数量趋于增加，稳态概率 $\pi_i^m$ 随 $i$ 递增。当我们考虑越来越大的缓冲大小时，任一固定状态 $i$ 的稳态概率都递减到零：

```math
\pi_i^m \to 0, \quad \text{当 } m \to \infty, \ \ \text{对所有 } i .
```

> <span style="color:#7f8c8d;">[原页此公式 OCR 损坏] 原页该式仅残留 `for all i.` 及散布的 `\to 0` 碎片，上式是按句意（"递减到零"）反查补全的标准极限式；若需最严格字形请回查原书页 362/371。</span>

假如我们考虑一个无限缓冲的系统，就会得到一个状态空间可数无穷的马尔可夫链。虽然我们还没有研究这类链的工具，但前面的计算提示：每个状态都会有零稳态概率，并且是"暂态的（transient）"。队列中的数据包数量通常会增长到无穷，而任何特定状态都只会被访问有限多次。

上述分析让我们窥见了具有无穷多个状态的马尔可夫链（infinite-state Markov chains）的一斑。在这类链中，即使存在唯一的非周期常返类（single aperiodic recurrent class），链也可能永远达不到稳态，因而不存在平稳分布（steady-state distribution）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这段插曲只有两句话，却是全章最锋利的提醒：前面每一道关于稳态的定理都写着「有限状态」这个前提，一旦把它抽掉，结论会直接崩掉。读者若把定理记成「不可约非周期就有稳态」，在这里会算出不存在的答案。值得把前提逐条清点一遍：有限性、单个闭类、positive recurrence（正常返）、非周期——四个条件各管一件事，教材在不同定理里分别用到。
>
> 第一性原理在于「解集不再紧」。有限状态下，probability simplex（概率单纯形）是 compact set（紧集），平衡方程的解集是紧集与超平面的交，种种极值论证和线性方程组「存在唯一解」的代数条件都能落地。状态可数无穷时，概率向量所在的集合不再是紧的，那些论证全部失去支点；平衡方程逐条仍然成立，但把它们全加起来可能得到发散的和，归一化这一步就过不去。
>
> $\rho>1$ 的无限缓冲队列正是活标本。解出来的形式仍是 $\pi_i$ 与 $\rho^{i}$ 成正比，但这个等比级数发散，没有任何非负解能满足归一化（零向量同样不可归一）。于是教材说「每个状态的稳态概率为零」：不是说概率很小，而是说这条链根本不存在 stationary distribution（平稳分布）。过程的典型行为是 drift to infinity（漂向无穷），任何固定的 $i$ 只被访问有限多次。
>
> 这里要精确一下原文那句「即使存在唯一的非周期常返类，链也可能永远达不到稳态」。正确的分层是：不可约且非周期的 infinite state chain（无穷状态链），要么 positive recurrent（正常返），此时存在唯一的概率型稳态分布，转移概率确实收敛；要么 null recurrent（零常返），此时不存在概率型（可和且归一）的平稳解，$T_{ij}(n)$ 对每个 $j$ 都趋于零。后一句要加一个限定语才准确：「没有概率型平稳解」不等于「方程 $\pi = \pi P$ 只有零解」——零常返链完全可以有 non-summable invariant measure（不可和的不变测度），整数格点上的对称随机游走取 $\pi \equiv 1$ 就满足 $\pi = \pi P$，它既不是概率分布，也不是零向量。把「找不到概率型解」说成「解只有零向量」，会把不变测度这一整类对象误删掉，后面讲更新方程时会付代价。有限状态链不可能出现零常返这一支——这正是有限性在暗中兜底的地方。
>
> 一维随机游走是这套分类最干净的例子。对称情形（左右各一半）在整数轴上常返，但从起点出发的 mean recurrence time（平均返回时间）是无穷，属于零常返；只要漂移不为零，连常返都保不住，直接 transient（暂态）。再往上，Polya 的结论是：二维方格上的对称 random walk（随机游走）仍常返，三维及以上变成 transient（暂态）。同一个「维数」参数改变了整个定性结论，这在有限状态里是不可想象的。
>
> 工程上要记住的是「有稳态」与「有界」不是同一件事。有限缓冲总能算出唯一稳态，因为状态被容量封顶；真实系统无界，过载时那道稳态解并不存在，数值仿真只会看到队列一路漂高。所以做仿真必须先设上限，并检查上限是否已经影响了结论——这与数值分析里「truncation error（截断误差）是否主导」是同一类警觉。
>
> 反例与判据一起记：不能靠「看起来有个常数解」来判断稳态存在。可靠的判据是 Foster–Lyapunov 型条件——找一个 drift function（漂移函数）使状态越远、回拉的倾向越强，则是 positive recurrent（正常返）；若漂移朝外，就是 transient（暂态）。对生灭链，这条判据退化成检查 $\pi_i$ 的连乘是否 summable（可和），等价于 $\rho<1$。
>
> 方法论提示：这段只是预告，不作证明，所以不必在这里追严格条件。真正要带走的是负结论的用法——凡要断言某系统有稳态，先问 state space（状态空间）是否有限；若不能确定，就必须额外给出可和性判据（这里的连乘可和、上文的 Foster–Lyapunov 漂移条件），否则那只是一句猜测。
>
> 最后提醒一个容易被糊过去的边界：$\rho=1$ 的无限缓冲队列同样没有稳态，不能因为「恰好临界」就当成安全。教材把 $\rho=1$ 与 $\rho>1$ 合并在同一支讨论，正是这个意思；均匀分布在有限 $m$ 下存在，在 $m\to\infty$ 时退化没了。

---

<span style="color:#c0392b;">**§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）**</span>

在本节中，我们研究马尔可夫链的短期行为（short-term behavior）。我们首先考虑马尔可夫链从某个暂态（transient state）出发的情形。我们关心第一个被进入的常返状态（recurrent state），以及直到这一事件发生所经历的时间。

处理这类问题时，马尔可夫链的后续行为（在遇到常返状态之后）是无关紧要的。因此我们可以集中考虑每个常返状态 $k$ 都是吸收态（absorbing）的情形，即

```math
p_{kk} = 1, \qquad p_{kj} = 0, \quad \text{对所有 } j \neq k .
```

若存在唯一的一个吸收态 $k$，其稳态概率为 $1$（因为所有其他状态都是暂态，具有零稳态概率），并且将…
<!-- ===== PDF p372 ===== -->
<span style="color:#c0392b;">**§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption，续）**</span>

> <span style="color:#7f8c8d;">承接上一页 §7.4 的叙述：本页续讲吸收概率（absorption probability）的定义、吸收概率方程组及其推导，并在页末引出下一例。页眉仍为 Sec. 7.4。</span>

承接上一页：如果只有一个吸收态，那么无论从哪个初始状态出发，都必然以概率 1 被到达（reached with probability 1）。若存在多个吸收态，则其中某一个最终必然会被到达的概率仍为 1，但究竟最终进入哪一个吸收态是随机的，且相应的概率可能取决于起始状态。为便于下文叙述，我们固定一个特定的吸收态，记作 $s$，并考虑从 $i$ 出发最终到达 $s$ 的吸收概率 $a_i$（absorption probability）：

```math
a_i = P\bigl(\text{最终 } X_n \text{ 变为吸收态 } s \mid X_0 = i \bigr).
```

吸收概率可以通过求解一个线性方程组得到，如下所述。

<span style="color:#00838f;">**[定义] Definition　吸收概率方程组（Absorption Probability Equations）**</span>

考虑一个每个状态要么是暂态（transient）、要么是吸收态（absorbing）的马尔可夫链，并固定一个特定的吸收态 $s$。那么，从 $i$ 出发最终到达状态 $s$ 的概率 $a_i$，是下列方程组的唯一解：

```math
a_i = \sum_{j=1}^{m} p_{ij}\, a_j, \qquad \text{对所有吸收态 } i \neq s \text{ 以及所有暂态 } i .
```

其中 $a_s = 1$，且对所有吸收态 $i \neq s$ 有 $a_i = 0$，这两条从定义上看是显然的。为验证其余方程，我们论证如下。考虑一个暂态 $i$，并设 $A$ 为「状态 $s$ 最终被到达」这一事件。则有

```math
a_i = P(A \mid X_0 = i)
    = \sum_{j=1}^{m} P(A \mid X_0 = i,\ X_1 = j)\, P(X_1 = j \mid X_0 = i)
```

（其中的第二个恒等号用到全概率定理 total probability theorem，随后将每个 $P(A \mid X_0 = i,\, X_1 = j)$ 利用马尔可夫性 Markov property 化为 $P(A \mid X_1 = j)$，因其与 $X_0$ 无关）

```math
    = \sum_{j=1}^{m} P(A \mid X_1 = j)\, p_{ij}
    = \sum_{j=1}^{m} a_j\, p_{ij}.
```

吸收概率方程组之解的唯一性需要一个单独的论证，这一论证将放在章末习题中给出。

下面的例子说明如何用上述方法计算进入某一给定常返类（recurrent class）的概率，而非进入某一给定吸收态的概率。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> §7.4 这套方程的形状值得记住：$a_i = \sum_j p_{ij} a_j$，配上一句 boundary condition（边界条件）「选定的吸收态处取 1，其余吸收态处取 0」。这不是新定理，而是 first-step analysis（第一跳分析）的标准动作——把「最终会怎样」拆成「走一步之后会怎样」。total probability theorem（全概率定理）负责按第一跳分类，Markov property（马尔可夫性质）负责把「从 $j$ 出发」重置掉历史。
>
> 用它要区分两种对象：$a$ 是一个定义在状态集上的 function（函数）。在暂态上它满足「等于近邻值的加权平均」，在吸收态上被钉死为给定值。这在数学上就是 boundary value problem（边值问题）的离散版本，$a$ 是一个 harmonic function（调和函数）——和讲局部平衡与电网络那条注里的那一幕同源：把吸收态接地或接 1 伏，中间节点的 potential（电势）就是 absorption probability（吸收概率）。
>
> 为什么这套写法能处理「无限时域」而不失严谨？因为 $\{X_n\}$ 最终是否进入 $s$ 是一个只依赖整条轨道、与任何有限时刻的截断无关的事件，而转移规律不随时间变化，于是「从 $i$ 出发最终进入 $s$」的条件概率可以被第一跳完整切分，不需要对任何极限作交换。这一点比表面看到的强：它意味着这类问题从不要求「$n$ 趋于无穷的极限存在」，只要吸收发生，答案就是一个确定的数。
>
> 唯一性才是这套方法的命门。把暂态排成 $T$、吸收态排成边界，方程写成向量的形式 $a_T = Q a_T + r$，其中 $r$ 是「一步就进 $s$」的那部分贡献；解出 $a_T = (I - Q)^{-1} r$。所以「唯一」等价于 $I - Q$ invertible（可逆），而它可逆等价于 $Q$ 的 spectral radius（谱半径）小于 1，等价于暂态部分会以概率 1 走完。一旦链里存在另一个闭的常返类，$I - Q$ 成为 singular（奇异），方程有整族解，这时必须补上「最终一定被吸收」这个前提才谈得上答案。正文在列出吸收概率方程组之后紧接着写的那句「解的唯一性需要一个单独的论证，这一论证将放在章末习题中给出」，代价就在这里。
>
> 计算上还能再省一步。若暂态之间没有 cycle（环），按 topological order（拓扑序）倒着扫一遍就能把 $a$ 算出来，代价是边数级别；有环才真正需要解 linear system（线性系统）。稀疏系统也不必用稠密消元，Jacobi 或 Gauss–Seidel 这类 iterative method（迭代法）的收敛条件恰好是谱半径小于 1——也就是「吸收必然发生」这个概率前提，被数值方法原样复用了。
>
> 用 Example 7.10 的数字做一次验算，可以确认译文补出的系数自洽：$a_2 = 21/31$，代入 $a_3 = 0.2\,a_2 + 0.8$，右边是 $21/155 + 124/155 = 145/155 = 29/31$，与页尾给的 $a_3$ 完全一致。这种「拿已知解回代」的检查很便宜，却能发现抄错的系数——本页 OCR 破损严重，正是需要它兜底的地方。
>
> 一个常被忽略的恒等式：若每个常返状态都是 absorbing state（吸收态），则对任一出发状态 $i$，各个吸收态的吸收概率之和为 1，即 $\sum_s a_i^{(s)} = 1$。它说的就是「最终一定会落进某个吸收态」这件事，可以用它检查算出的整组概率有没有漏项。注意 $a$ 依赖你固定的是哪个 $s$，不同 $s$ 得到的是同一个方程族的不同解。
>
> 把它当通用模板记：第一步写边界（吸收态取定值），第二步对每个暂态写一条「第一步之后」的方程，第三步解系统或迭代。下一节的 expected time to absorption（吸收期望时间）用的是同一套模板，唯一的差别是方程多出一个常数项——期望时间满足「当前这一步花掉一个单位，其余交给邻居」，其余字样完全一样。看到这一点，§7.4 的两节其实只是一节。
>
> 陷阱集中在边界条件的写法。把 $a_s$ 写错一格，整组数值就全偏；忘记「其余吸收态取零」则方程组多出一个未知量。另一类错误是把 $a_i$ 读成「第 $n$ 步落在 $s$ 的概率」，那个量随时间变化、且不必收敛，与本节的「最终必然到达」不是一回事——前者要解的是逐时演化，后者只需解一次线性系统。
>
> 跨课程看，这正是 Bellman equation（贝尔曼方程）的原型：盯住目标状态就给 1，盯住失败就给 0，中间由转移概率加权——reinforcement learning（强化学习）里 value function（价值函数）的计算就是这组方程的迭代版本。PageRank（网页排名）之所以要加 damping factor（阻尼因子），也可以从这个角度理解：纯链接图的链可能没有「必然出口」，方程从而不唯一，阻尼把吸收性人工造出来。
<!-- ===== PDF p373 ===== -->
<span style="color:#c0392b;">**§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页中部续讲 Example 7.10 吸收概率（absorption probabilities）的求解，故本节正文标题标注「（续）」。页首为 Fig. 7.17 的图注（图分 (a)、(b) 两部分，描述 Example 7.10 中吸收态并入相关的转移概率图）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.10（续）（吸收概率的求解）**</span>

本页顶部为下列图 7.17 的图注：

- **(a)** Example 7.10 中的转移概率图（transition probability graph）。
- **(b)** 一张新图，其中状态 4 与 5 已被并入吸收态 6（absorbing state 6）中。

随后正文继续求解吸收概率。设 **$a_i$（absorbing probability）** 表示"从暂态（transient）状态 $i$ 出发、最终进入状态 6（即被吸收到状态 6）的概率"。利用已知条件 $a_1 = 0$ 与 $a_6 = 1$，我们可写出关于未知量 $a_2$ 与 $a_3$ 的方程为：

```math
a_3 = 0.2\, a_2 + 0.8 \qquad \text{（这里用到 } a_6 = 1 \text{）}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述 $a_3$ 的方程由可辨认片段 `a3 = 0.2a2` 与单独出现的 `+ 0.8` 拼合而成，且与页尾给出的解 $a_2=21/31$、$a_3=29/31$ 相互吻合；但方程中各项系数的精确原文朝向需回查原书页 373 核对。关于 $a_2$ 的另一条方程在 OCR 中严重破损（可辨残片如 `+ OAa3 + O.`、独立的 `2`、`+ 0.8`、`+ 1.` 等无法复原为确定的系数式），此处不臆造、不补全，保留占位。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 第二条方程的系数无法辨认，故此处仅给出可确认的信息；两式联立为「二元一次方程组」，原文随后写道：</span>

这是一个只含两个未知量 $a_2$ 与 $a_3$ 的二元方程组，可以轻易求解，得到

```math
a_2 = \frac{21}{31}, \qquad a_3 = \frac{29}{31}.
```

（即 $a_2 \approx 0.677$，$a_3 \approx 0.935$，其中 $a_3 = 0.935$ 由 $a_3 = 0.2 a_2 + 0.8$ 代入 $a_2=21/31$ 验证成立。）

---

<br>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏 —— 页尾新片段] 本页结尾另起一段新的内容，其例题编号与标题在 OCR 中损坏，无法辨认（可能为下一例题的开头）。可辨认残片为「概率 $P$」「每轮/每一回（round）获得 $\$1$」「不同轮次被假设为（相互独立，different rounds are assumed …）」等措辞，暗示这是一段与"逐轮进行、每轮以概率 $P$ 赢取 1 元"相关的马尔可夫链内容。具体示例数据与题干在此页上无法辨认，待下页续读。</span>
<!-- ===== PDF p374 ===== -->
<span style="color:#c0392b;">§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）</span>

> <span style="color:#7f8c8d;">页眉滚动标题为「Expected Time to Absorption（吸收期望时间）」，本页为 §7.4 内 Example 7.11 赌徒破产问题的延续（页首无新小节标题）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.11（续）（赌徒破产问题，The Gambler's Ruin Problem）**</span>

赌徒持续不断地玩下去（plays continuously），直到他要么累积到目标金额、要么把全部资本输光为止。赌徒的资本（the gambler's wealth）的变化……对应……当处于这两个端点态时的状态是**吸收的**（absorbing）。因此，问题归结为求到达这两个吸收态（absorbing state）中某一个的概率，即在两个吸收态上各处的吸收概率（absorption probabilities）。当然，这些吸收概率……处于状态 $i$……

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图题行多处被打散（「Figure 1.1 8」「7.1 1）」「Here m = 4」碎片化），图号与公式号无法从 OCR 可靠辨认，故下按语义还原但不臆造具体图号。</span>

图：赌徒破产问题（gambler's ruin problem）的**转移概率图**（transition probability graph）。此图中 $m = 4$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上句「此图中 $m=4$」对应的图号、状态标注（各节点间的转移权重如 $p$、$1-p$）在图题区 OCR 中残缺，此处仅能确认 $m=4$。</span>

令 $s = i$（取定起点状态），此时吸收概率 $a_i$ 就是从状态 $i$（state $i$）出发最终到达目标态的概率。这些吸收概率满足

```math
a_0 = 0, \qquad a_i = (1-p)\, a_{i-1} + p\, a_{i+1}, \qquad a_m = 1,
```

```math
i = 1, \ldots, m - 1 .
```

这些方程有许多种不同的解法。事实证明存在一个很优雅的方法：先引入差分量 $\delta_i = a_i - a_{i-1}$（为 $i = 0, 1, \ldots, m$ 定义，并注意到 $a_0 = 0$，从而 $\delta_1 = a_1$），再将方程组改写为

```math
\delta_{i+1} = \frac{1-p}{p}\, \delta_i = \rho\, \delta_i, \qquad i = 1, \ldots, m - 1,
```

其中 $\rho = \dfrac{1-p}{p}$。由此我们得到

```math
\delta_i = \rho^{\,i - 1}\, \delta_1, \qquad i = 1, \ldots, m - 1 ,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末段「$\ldots, m-1$」后的文字（求和累计 $\sum_{i=1}^m \delta_i = a_m - a_0 = 1$，从而分 $p \neq 1/2$ 与 $p = 1/2$ 两种情况给出 $a_i$ 的闭式解）在翻页处被打断，完整推导续于下一页 p375。差分量本页 OCR 未能给出清晰符号，按下一页（p375）一致改用 $\delta_i$ 记号。</span>
<!-- ===== PDF p375 ===== -->

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span> — §7.4 吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption），书页 p.366，延续上一页内容。

> <span style="color:#7f8c8d;">承接上一页：本页开头继续 §7.4 中赌徒输光问题，随后转入本节的「Expected Time to Absorption（吸收期望时间）」小节。赌徒输光问题在本节标号为 Example 7.11（见上一页对 Figure 7.18 的图注 "see Example 7.11", m = 4）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.11（续）——赌徒输光问题（gambler's ruin problem）**</span>

这一结果，连同方程 $\delta_0 + \delta_1 + \cdots + \delta_{m-1} = a_m - a_0 = 1$，蕴含

```math
(1 + p + \cdots + p^{m-1})\, \delta_0 = 1,
```

以及

```math
\delta_0 = \frac{1}{1 + p + \cdots + p^{m-1}} .
```

由于 $a_0 = 0$ 且 $a_{i+1} = a_i + \delta_i$，从财富（fortune）$i$ 出发获胜的概率（probability）$a_i$ 等于

```math
a_i
= \delta_0 + \delta_1 + \cdots + \delta_{i-1}
= (1 + p + \cdots + p^{i-1})\, \delta_0
= \frac{1 + p + \cdots + p^{i-1}}{1 + p + \cdots + p^{m-1}},
```

它化简为

```math
a_i =
\begin{cases}
\dfrac{1 - p^i}{1 - p^{m}}, & \text{if } p \ne 1,\\[8pt]
\dfrac{i}{m}, & \text{if } p = 1 .
\end{cases}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中第一分支分子的幂指数 $i$（原式呈 $1 -\,/\, /\,1-p^{m}$ 碎片）与第二分支的分子 $i$（原式呈 $\,-\, /\,\,\, m$ 碎片）在 OCR 中被错读；此处按前一页已建立的 $\delta_i$ 递推与教科书标准的赌徒输光公式补全为 $p^{i}$ 与 $i/m$。若需最严格原文，请回查原书页 366（约 p366 中部）。</span>

这一结果揭示：若 $p > 1$，即对应 $p < 1/2$、对赌徒而言赔率不利（unfavorable odds）的情形，则对任意固定的初始财富，获胜的概率 $a_i$ 都随 $m \to \infty$ 趋近于 $0$。这暗示，如果你打算在不利的赔率下去追求巨额利润，财务破产（financial ruin）几乎是必然的。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 赌徒破产是 absorption probability（吸收概率）最经典的应用，而真正优雅的一步是差分：不硬解 $a_i$ 的二阶递推，而是令 $\delta_i = a_i - a_{i-1}$（$i \ge 1$），把三项递推降成一阶等比，再用「差分量总和等于端点差」收口。这一步值得从 linear difference equation（线性差分方程）的角度看透——不是技巧，而是结构。
>
> 第一性原理：$a_i = (1-p)a_{i-1} + p a_{i+1}$ 是常系数二阶线性递推，它的解空间是二维的，基底恰好由 characteristic equation（特征方程）的两根给出：一根是 1，一根是 $\rho = (1-p)/p$。于是所有解都是「常数项加等比项」的叠加。差分操作本质上是在消掉那个常数方向——相邻两点相减，常数项自动消失，只剩 $\rho$ 方向的一阶递推。这与解常系数 linear ODE（线性常微分方程）时「两个独立解加两个边界条件定常数」是同一套逻辑。
>
> 于是边界条件把两个常数钉死：资本为 0 处必输（取 0），资本达到 $m$ 处必胜（取 1）。解出来是 $a_i = \frac{1-\rho^{i}}{1-\rho^{m}}$，$\rho \neq 1$；$\rho = 1$ 时退化为直线 $a_i = i/m$。三种区制一眼可见：胜率占优（$p > 1/2$，此时 $\rho<1$）时曲线在直线之上，公平（$p = 1/2$）时正好是直线，赔率不利（$p < 1/2$，此时 $\rho>1$）时压在直线之下并向 0 弯曲。
>
> 收口那一步也值得说清。本注用的是 $\delta_i = a_i - a_{i-1}$（$i \ge 1$），于是 $\delta_1 + \cdots + \delta_m = a_m - a_0 = 1$，中间项两两抵消，这叫 telescoping sum（裂项求和）。它把「$m$ 个差分量」压成一个归一约束；而差分量本身构成等比数列 $\delta_i = \rho^{i-1}\delta_1$，于是首项立刻被定死：$\delta_1 = 1/(1+\rho+\cdots+\rho^{m-1})$，它同时就是 $a_1$（因为 $a_0 = 0$）。原文推导用的是另一套下标（$\delta_0,\dots,\delta_{m-1}$，其中 $\delta_0 = a_1 - a_0$），两套写法的数值完全相同，读的时候不要因为下标差一就以为公式错了。手上验一个数：$p = 1/2$、$m = 4$、$i = 1$ 时答案为 $1/4$；换成 $p = 2/3$（此时 $\rho = 1/2$），$a_1$ 应为 $(1/2)/(15/16) = 8/15$——胜率变大，概率确实涨上去，且仍小于 1。
>
> 这里有一处记号混淆必须点明：正文在给出结论时写「若 $p > 1$，即对应 $p < 1/2$」，这句自相矛盾——概率不可能大于 1。按上下文，这里应是 $\rho > 1$，等价于 $p < 1/2$。同样的记号漂移还出现在推导区：正文既用 $p$ 表示单步获胜概率，又在 $\delta_0$ 公式里把它当成比值 $\rho=(1-p)/p$ 来用，于是 $(1+p+\cdots+p^{m-1})\,\delta_0 = 1$ 与 $a_i = (1-p^i)/(1-p^m)$ 这两式里的 $p$ 按推导都应为 $\rho$。判据很硬：$\rho = 1$（即 $p = 1/2$）时公式必须退化成 $a_i = i/m$；反过来，若把字面上的 $p = 1/2$ 直接代进 $(1-p^i)/(1-p^m)$，$m=4$ 会得到 $8/15$、$4/5$、$14/15$ 这样一串既不等于 $i/m$、又随 $m$ 变化的值，一眼就能看出不是那条退化直线。阅读时以 $\rho$ 为准，不必怀疑推导。
>
> 还有一条更短的路，能把这组结果一句话证出来：$p = 1/2$ 时资本过程是 martingale（鞅），吸收时间虽然随机，但在有限状态吸收链里其期望有限且停止位置有界，于是 optional stopping theorem（可选停止定理）允许在停止时刻取期望：$\mathrm{E}[X_\tau] = X_0 = i$。而终值只取 0 或 $m$，故 $m\,a_i = i$，直接得 $a_i = i/m$。一般情形把 $(q/p)^{X_n}$ 看作 exponential martingale（指数鞅），同样一步得到 $\frac{1-\rho^{i}}{1-\rho^{m}}$。差分法教你看结构，鞅法教你走捷径；两者结论必须一致，这是一次免费的交叉验证。
>
> 也要清楚这套手法的边界。差分能降阶，靠的是状态空间是一条线、转移只发生在相邻两格；换成二维平面上的 random walk（随机游走），就不存在这种一维差分，只能退回到解 discretized（离散化）的偏微分方程——那正是 harmonic function（调和函数）的 mean value property（平均值性质）在做的事。本节拿一维例子讲方法，但不等于方法能原样搬到高维。
>
> 这个问题的历史位置也值得一提：它由 Pascal 与 Fermat 在 1654 年的通信中解决，1657 年由 Huygens 在《De ratiociniis in ludo aleae》里公开发表，与「点数分配问题」同属概率论的起点。今天读到的差分技巧，是三百多年前就在用的原味方法。
>
> 结论的含义值得从两面看。赔率不利（$p < 1/2$，即 $\rho > 1$）时，$a_i$ 随目标 $m$ 指数级衰减：想赢大钱不是「概率低一点」，而是「概率按倍数坍塌」，这与「负期望游戏反复玩必然破产」是同一件事的两种说法。而 $\rho = 1$ 时 $a_i = i/m$ 看似公平，破产概率 $1 - i/m$ 依然为正——公平游戏里「迟早破产」并不矛盾，因为破产者的损失由赢家更高的终值补偿，期望守恒。
>
> 应用面上，这条曲线是 Kelly criterion（凯利准则，Kelly 1956）的直观来源：下注比例过大时，单局胜率再高也挡不住长期几何增长率为负。风险理论里把 $a_i$ 的补看成 ruin probability（破产概率），与本节方程完全同构。反例提醒：不要把这个公式套到有多个非吸收常返类的链上——那时 $I-Q$ 不再 invertible（可逆），方程组有多解，$a_i$ 必须靠「吸收必然发生」这个前提才唯一。

<span style="color:#c0392b;">**吸收期望时间（Expected Time to Absorption）**</span>

我们接下来关注的是：从某个特定的暂态（transient state）出发，直到进入某个常返状态（recurrent state）为止所需的期望步数——我们把这个事件称为「吸收」（absorption）。对任意状态 $i$，记

```math
\mu_i = \mathrm{E}\,[\text{number of transitions until absorption, starting from } i]
= \mathrm{E}\,[\,\min\{ n > 0 \mid X_n \text{ is recurrent} \} \mid X_0 = i\,] .
```

注意：按照此定义，若 $i$ 是常返状态，则 $\mu_i = 0$。

我们可以利用全期望定理（total expectation theorem）来推出关于 $\mu_i$ 的方程。我们的论证是：从暂态 $i$ 出发到达吸收所用的时间，等于 $1$ 加上从下一状态出发到吸收的期望时间，而下一状态以概率 $p_{ij}$ 取为 $j$。从而我们得到一个线性方程组，陈述如下，已知它有唯一解（其主要思路见 Problems 第 33 题）。

> <span style="color:#7f8c8d;">本节关于 $\mu_i$ 的线性方程组、以及随后的 Example 7.12（含 Fig. 7.19 与 $\mu_2=\mu_3=10/3$ 的求解）将于下一页 p376 展开。</span>
<!-- ===== PDF p376 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — <span style="color:#c0392b;">**§7.4　吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）（续）**</span>

> <span style="color:#7f8c8d;">页眉滚动标题（running head）为「Sec. 7.4 / Expected Time to Absorption」，页首无新小节名，本页为上一页（§7.4 内吸收期望时间的通用方程推导）的延续，故标「（续）」。本页中段引出并求解示例 Example 7.12。</span>

承接上一页，我们继续求解**期望吸收时间**（expected time to absorption）的方程组。该方程组对每一个状态 $i$ 给出一个未知量，其结构为：对**吸收态**（absorbing state）$i$ 成立

```math
\mu_i = 0,
```

而对每一个**暂态**（transient state）$i$，则成立「当前一步」再加上「从下一步出发的期望时间」的关系，即

```math
\mu_i = 1 + \sum_{j} p_{ij}\, \mu_j .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述方程组（含 $\mu_i = 0$ 与 $\mu_i = 1 + \sum_j p_{ij}\mu_j$ 两行）是§7.4 期望吸收时间的通用框架；本例此处对应页首碎片「the equations / = 0, / == 1 + … / $\mu_m$」。原文中该框架的文字起于上一页（p375），本页仅收尾到结论。系统对一切暂态 $i$ 存在唯一解（unique solution），但「先取吸收态，再对暂态展开」的完整枚举在 OCR 中被打散，故此处按上述通式归纳，不作为原文字面的逐字呈现。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一组方程与上一节的 absorption probability（吸收概率）方程是一对双胞胎，唯一的差别是那个孤独的 $+1$。它记录的东西很具体：走这一步本身要花掉一个单位时间。数学上它仍然只是 total expectation theorem（全期望定理）——从 $i$ 到吸收所需步数等于「眼下这一步」加上「从下一步出发还剩多少」，后者取 conditional expectation（条件期望），按第一跳的概率加权。
>
> 把这一点讲透，就能看清这类方程的通用形状：$\mu_i = c_i + \sum_j p_{ij}\mu_j$，其中 $c_i$ 是停在状态 $i$ 的每步 cost（成本）。本节的 absorption time（吸收时间）是 $c_i = 1$ 的特例；换成「每天的电费」就是 long-run average cost（长期平均成本）的期望；换成「折扣因子」就成了 discounted reward（折扣回报）。reinforcement learning（强化学习）里 Bellman equation（贝尔曼方程）的最简版本，正是这一行字。
>
> 与吸收概率对照着看，结构完全同源：把暂态聚成块，两个问题分别是 $a = r + Q a$ 与 $\mu = \mathbf{1} + Q\mu$，解出来是 $a = (I-Q)^{-1} r$、$\mu = (I-Q)^{-1}\mathbf{1}$。同一个 inverse matrix（逆矩阵）反复出现，于是它有自己的名字：$N = (I-Q)^{-1}$ 称为 fundamental matrix（基本矩阵），Kemeny 与 Snell 在 1960 年的《Finite Markov Chains》里把它系统化。$N$ 的 $(i,j)$ 元有一个漂亮的解释：从 $i$ 出发、在被吸收之前访问 $j$ 的期望次数（含初始那一次）。
>
> 于是得到一个能当恒等式用的关系：$\mu = N \mathbf{1}$，也就是「期望步数等于对各状态期望访问次数求和」。这其实是不需要概率的常识——总时间就是各段停留时间相加，而每次停留恰好一步。它的用处在于把「时间」问题换算成「访客计数」问题，后者常常更好算，也更容易在 simulation（仿真）里抽样验证。
>
> 唯一性的讨论与吸收概率一字不差：$I-Q$ invertible（可逆），等价于 $Q^n$ 趋于零矩阵，等价于暂态部分必然走完。凡是存在某个闭的、不被吸收的常返类，这个可逆性就崩掉，方程组有整族解。本节的前提「所有常返态都是吸收态」正是为了堵住这个漏洞；教材把严格论证推到章末习题（Problems 区第 33 题），不是省事，而是那套论证要用到 matrix power（矩阵幂）的估计，属于线性代数侧的工作。
>
> 一处口径要留意：定义式用 $\min\{n>0 : X_n \text{ 是常返态}\}$ 计数，而从常返态出发时按这个式子本该得 1（下一步仍是常返态），教材却直接规定 $\mu_i = 0$。两者不是矛盾，而是「把已经处于吸收态的那一瞬当作第 0 步」这个约定。做题时按教材的约定走，否则边界项会多出一个 1。
>
> 拿赌徒破产验一下这套机器。公平局 $p = 1/2$ 时吸收期望时间是 $\mu_i = i(m-i)$：取 $m = 4$、从资本 2 出发得 4 步，从资本 1 出发得 3 步。这个公式有个立刻能查的结构——它关于 $i$ 与 $m - i$ 对称，因为把赌局输赢标签对调不改变步数分布。赔率不利（$p < 1/2$）时公式换成 $\mu_i = \frac{i - m\,a_i}{1-2p}$，其中 $a_i$ 要用 $\rho = (1-p)/p$ 计算。分母为正、$a_i$ 压在直线 $i/m$ 之下，于是分子 $i - m a_i$ 为正，商也为正——符号是公式自己守住的，不必额外讨论。但「$\mu$ 被单纯抬高」这个直觉是错的。取 $m=4$、$p=1/3$（此时 $\rho = 2$）：$(a_1,a_2,a_3) = (1/15,\,1/5,\,7/15)$，代入得 $(\mu_1,\mu_2,\mu_3) = (11/5,\,18/5,\,17/5)$，即 $(2.2,\,3.6,\,3.4)$；同一组参数下公平局给出 $(3,\,4,\,3)$。可见靠近 0 的一端 $\mu$ 反而变小（2.2 对 3、3.6 对 4），只有靠近 $m$ 的一端变大（3.4 对 3）。机理是分母 $1-2p = 1/3$ 带来的三倍放大压不过 $m a_i$ 那项的削减：$i$ 小时 $a_i$ 虽小，乘以 $m$ 之后已经把分子拉得很低。反过来 $p > 1/2$ 时分母为负、分子也为负，商仍为正，公式照样自动保号。
>
> 数值上有三条路。其一，直接解 $n \times n$ 线性系统，$O(n^3)$，状态少时最省心。其二，稀疏时用 iterative method（迭代法，Gauss–Seidel 之类），收敛条件又是谱半径小于 1，与「吸收必然发生」是同一句话。其三，Monte Carlo（蒙特卡洛）仿真：跑 $k$ 条轨道取平均，unbiased（无偏）但误差按 $1/\sqrt{k}$ 收缩，要多一位精度就得一百倍的样本。解析解与仿真互为校验，是最实惠的组合。
>
> 下一页 Example 7.12 给出 $\mu_2 = \mu_3 = 10/3$ 这样的数值，正好可以用本节的方法独立复核：写出暂态子矩阵 $Q$，算 $(I-Q)^{-1}$ 的行和，与题给答案对照。凡是这类例题，都建议做一次这样的机械核对——它与手算的推导互为保险，尤其在 OCR 破损、系数靠语义重建的页面上。
>
> 最后记两个陷阱。第一，这里的 $\mu_i$ 是「到吸收」的期望，不是「首次到达某个特定状态」的期望——后者叫 hitting time（首达时间），方程要多加一层边界条件，两者别混。第二，有限状态保证 $\mu$ 有限，无穷状态则不保证：零常返的链上 mean recurrence time（平均返回时间）是无穷，那时方程组的解会发散发到无穷，看起来像「算错了」，实际是模型本身没有有限答案。

当吸收态为 $1$ 与 $m$、而暂态为其余状态时，这些方程对所有暂态 $i$ 具有**一个唯一解**（unique solution）。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.12（期望吸收时间的数值示例，期望平均步数 $\mu_i$）**</span>

例 7.12 恰好对应图 7.19 所示的那条**马尔可夫链**（Markov chain）。其“可处的可能位置”（possible positions）为若干离散位置，其中的两个**吸收态**（absorbing state）$1$ 与 $m$ 对应于两个可能的吸收端点，而其间的状态 $i = 2, \ldots, m-1$ 均为暂态。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本段对应的原页碎片为「Example 7.12. This corresponds to the Markov chain shown in Fig. 7.19 … the absorbing states 1 and m correspond … possible positions … i = … m - 1 …」。图中每个暂态 $i$ 向相邻状态转移的具体概率与 $m$ 的具体取值（如回到 $i-1$、$i+1$ 或停留）在图中 OCR 完全碎裂（对应碎片「-I / of / fly is / to」等），无法可靠辨认；示例的确切转移系数与状态个数 $m$ 均无法从本页 OCR 读出，故不予臆造。若需精确系数请回查原书图 7.19。</span>

设 $\mu_i$ 为从状态 $i$ 出发的**期望吸收时间**（即期望的吸收步数）。由上述方程组，对本例可写出

```math
\mu_2 = 1 + (\cdots), \qquad \mu_3 = 1 + (\cdots),
\qquad \ldots, \qquad \mu_{m} = 1 + (\cdots),
```

其中每个等式右边“$+$”之后为转移到相邻状态后各自期望时间的加权和，并伴随若干形如 $\pm (1-p)$ 的转移概率系数。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中「$\mu_2 = 1 + \cdots$」「$\mu_3 = 1 + \cdots$」及末端「$\mu_m = 1 + \cdots$」各等式右边的详细项（各转移概率系数、$(1-p)$ 项）在本页 OCR 中被打散（碎片如「J..L 2 = 1 + / + / + / I.」「J..L 3 = 1 + / +」「+ (1」等），具体系数无法识别，故此处以省略号占位，绝不臆造数值。</span>

求解这一小方程组时，我们可以先从第二个方程解出 $\mu_3$。由此求得 $\mu_3 = 10/3$，再代回（by substitution）原方程，又得 $\mu_2 = 10/3$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本段对应可辨读片段：「…we can … second equation and solve for $\mu_3$. We obtain $\mu_3 = 10/3$ and by substitution again. $\mu_2 = 10/3$.」。原文中从第二个方程解出 $\mu_2$（对应碎片「112 = ( 1…」）与 $\mu_3$ 的过程之完整转移系数亦残缺，此处只保留可辨认的结论 $\mu_2 = 10/3$ 与 $\mu_3 = 10/3$。</span>

图：<span style="color:#00838f;">Fig. 7.19 —— 转移（Transition）…</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图题行只剩「7.19 : Transition …」可辨，图题其余文字与图中各边上的转移概率标注（$\pm p$、$1-p$、各节点间的转移权重）全部缺失，故仅能确认图号为 Fig. 7.19、主题为转移（transition）图，不作任何补充。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末尾为承接后面的过渡句，原文大意是：上述方法（如 Example 7.12 所示）可用来计算从任何其他状态出发、最终到达某个给定状态的期望首达时间（expected time to reach a given state）。此句的汉语译文按语义补全，对应可辨碎片「…to calculate the expected time … (as illustrated) in Example 7.12 … to reach a … state, starting …」；其完整句子的后半段续于下一页 p377。</span>
<!-- ===== PDF p377 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span> — <span style="color:#c0392b;">**§7.4 吸收概率与吸收期望时间（Absorption Probabilities and Expected Time to Absorption）（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页继续推导马尔可夫链中某个指定状态的平均首次通过时间（mean first passage time）与平均递归时间（mean recurrence time）。页首「from any other state」是上一页句子的尾端，故本页为续页，无新节号。本页末尾引出示例 Example 7.13，其计算于下页继续。</span>

……从任何其他状态出发。为简化起见，我们考虑一个只有**单一常返类（single recurrent class）**的马尔可夫链。我们把注意力放在一个特殊的**常返态（recurrent state）**$s$ 上，并记 $t_i$ 为从状态 $i$ 到状态 $s$ 的平均首次通过时间（mean first passage time），其定义为：

```math
t_i = E[\text{从 } i \text{ 出发首次到达 } s \text{ 所需的转移次数}]
   = E\!\left[ \min\{ n > 0 : X_n = s \} \;\middle|\; X_0 = i \right].
```

出状态 $s$ 的转移与平均首次通过时间的计算无关，因此我们可以考虑一个新的马尔可夫链，它与原链完全相同，唯一的区别是把特殊状态 $s$ 变成一个**吸收态（absorbing state）**（即置 $p_{ss}=1$，且对一切 $j \neq s$ 令 $p_{sj}=0$）。经过这一变换后，除 $s$ 以外的所有状态都变为**暂态（transient）**。于是我们可以利用本节前面给出的公式，把 $t_i$ 看作是**从 $i$ 出发到吸收**（absorption）的期望步数来加以计算。我们有

```math
t_i = 1 + \sum_{j=1}^{m} p_{ij}\, t_j, \qquad \text{对一切 } i \neq s,
```
```math
t_s = 0 .
```

这一线性方程组可以针对未知量 $t_i$ 求解，并且**有唯一解（unique solution）**（见章末问题）。

上述方程组给出从任何其他状态出发到达特殊状态 $s$ 的期望时间。我们可能还想计算特殊状态 $s$ 的平均**递归时间（mean recurrence time）**，其定义为：

```math
t_s^{*} = E[\text{从 } s \text{ 出发到首次回到 } s \text{ 所经历的转移次数}]
        = E\!\left[ \min\{ n \geq 1 : X_n = s \} \;\middle|\; X_0 = s \right].
```

只要我们已知首次通过时间 $t_i$，就可以利用下式求出 $t_s^{*}$：

```math
t_s^{*} = 1 + \sum_{j=1}^{m} p_{sj}\, t_j .
```

为证明该式，我们论证如下：从 $s$ 出发回到 $s$ 所需的时间，等于 $1$ 加上从下一状态（该下一状态以概率 $p_{sj}$ 等于 $j$）出发到达 $s$ 的期望时间，然后运用**全期望定理（total expectation theorem）**。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 正文先给出 first passage time（首次通过时间）的方程组，紧接着定义 mean recurrence time（平均递归时间）。两个量都以「转移次数」为单位，都写成「$1$ 加一步之后的条件期望」，所以极易混用；区分它们的唯一钥匙是出发点：前者从别处出发、把 $s$ 当靶心，后者从 $s$ 自己出发、把「再回来」当任务。
>
> 两个方程要并排盯住。首达那一组是 $t_s=0$ 配 $t_i=1+\sum_j p_{ij}t_j$（对 $i\ne s$），形状是 boundary value（边值）问题：目标态被人工钉成零，其余每个状态只问一步，剩下的交给递归。递归那一行是 $t_s^{*}=1+\sum_j p_{sj}t_j$，它不能钉零，因为问题问的正是「离开之后再回来」；但它的右边只出现已经求好的 $t_j$，所以是借用已有结果，而不是重开战场。
>
> 机制上，为什么借用就够？从 $s$ 走一步落到 $j$ 的概率是 $p_{sj}$，而落到 $j$ 之后「首次回到 $s$」的期望步数正是 $t_j$；由 total expectation theorem（全期望定理）加权求和，再加掉那一步。self-loop（自环）在这里自动被处理：$j=s$ 那一项贡献 $p_{ss}t_s=0$，等于说自环只消耗一步、不改变剩余问题——这正是 $t_s=0$ 这个边界的第二重作用。若把这一项误写成 $p_{ss}t_s^{*}$，就回到自我指涉，见下面反例。
>
> 线性代数（Strang 的 18.06）那边，把 transient state（暂态）的下标收成 $Q$，$(I-Q)^{-1}=\sum_{k\ge0}Q^{k}$ 是 Neumann series（诺伊曼级数）。这里有一处极常见的误读必须纠正：$(I-Q)^{-1}$ 的第 $(i,j)$ 个元素是「从 $i$ 出发、在被吸收之前访问 $j$ 的期望访问次数」，不是「从 $i$ 首次到 $j$ 的期望时间」；首达期望是它的行和，即 $(I-Q)^{-1}\mathbf{1}$。两者不是同一个对象。
>
> 一个一秒钟就能识别的判据：元素可以小于 $1$（很可能根本不去 $j$），而有限的首达时间必不小于 $1$（至少要迈一步）。见到矩阵里有 $0.0568$ 这类小元素就把它当首达时间，立刻自相矛盾。
>
> 算一个能对的例子。设三个暂态，$Q$ 的三行分别为 $(0.2,0.8,0)$、$(0.1,0.4,0.3)$、$(0,0.1,0.5)$，其余概率漏向 absorbing state（吸收态）。算得 $(I-Q)^{-1}$ 的第一行为 $(1.5341,2.2727,1.3636)$，第三行为 $(0.0568,0.4545,2.2727)$，行和依次是 $5.1705$、$3.9205$、$2.7841$。把 $1.5341$ 读成「从第一个暂态到第一个暂态的期望首达时间」就是错的：对角元素量的是「停在这块区域期间平均被访问几次」，它说的是次数，不是步数。
>
> 第三个锚点来自 Kac 的公式：对 irreducible（不可约）且 positive recurrent（正常返）的链，$t_s^{*}=1/\pi_s$。正文 Example 7.13 里 $\pi_1=0.75$，$1/\pi_1=4/3$ 正好是它给出的 $t_1^{*}$。这条恒等式把「绕一圈的期望步数」与「长时间里停在 $s$ 的时间比例」绑在一起，也顺手说明为什么 null recurrent（零常返）链上它给不出有限值——那时 $\pi_s=0$，倒数是无穷，与「返回时间期望无穷」同义。
>
> 第二处要纠正的说法是「周期链套这套方程会算错」。首达方程只用到 transition probability（转移概率）与全期望定理，对周期链照样成立：确定性两状态环上 $t_2=1$ 完全正确，因为一步就到靶。周期性真正影响的是 $P^{n}$ 的极限、stationary distribution（平稳分布）作为极限分布的解释，以及收敛速度那一套定理；把它说成「方程失效」是把收敛性的问题错记到方程组头上。
>
> 反例收束：若把 $t_s=0$ 换成一般式，正文 Example 7.13 的两条方程立刻互推到 $0=20/3$，方程无解——边界不是装饰，它决定方程组是否可解。一句话记住：$t$ 是「到靶的距离」，$t^{*}$ 是「绕一圈的周长」，后者由 $t$ 与一步转移概率拼出，绝不由 $t^{*}$ 自己递归。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.13（"up-to-date"—"behind" 模型的平均首次通过时间）**</span>

考虑 Example 7.1 中的「跟上进度（up-to-date）」—「落后（behind）」模型。状态 1 与状态 2 分别对应「跟上进度」与「落后」，其转移概率为：

```math
p_{11} = 0.8,\qquad p_{12} = 0.2,
```
```math
p_{21} = 0.6,\qquad p_{22} = 0.4 .
```
<!-- ===== PDF p378 ===== -->

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.13（续）——mean first passage time 与 mean recurrence time 的计算**</span>

> <span style="color:#7f8c8d;">承接上一页（p377 / 书页 368）：题设同上，例 7.1 的「up-to-date–behind」模型，状态 1 为按时（up-to-date），状态 2 为落后（behind），转移概率为 $p_{11}=0.8$、$p_{12}=0.2$、$p_{21}=0.6$、$p_{22}=0.4$。本页续接该例平均首次通过时间与平均递归时间的数值计算。</span>

我们把注意力集中在状态 $s = 1$ 上，并计算从状态 $2$ 出发、首次到达状态 $1$ 的平均首次通过时间（mean first passage time）。我们有 $t_1 = 0$，且

```math
t_2 = 1 + p_{21} t_1 + p_{22} t_2 = 1 + 0.4\, t_2 .
```

由此得 $0.6\, t_2 = 1$，故 $t_2 = \tfrac{5}{3}$。

状态 $1$ 的平均递归时间（mean recurrence time）为

```math
t_1^{*} = 1 + p_{11} t_1 + p_{12} t_2 = 1 + 0 + 0.2 \cdot \tfrac{5}{3} = \tfrac{4}{3}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页顶部两处结果的数值在 OCR 中被智能断行并打散（如把 $t_2$ 的结论读成碎片 `0.61 = -35`，把 $t_1^{*}$ 式中的 $\tfrac{5}{3}$、$\tfrac{4}{3}$ 误读为 `35`、`34` 等）。此处 $t_2=\tfrac{5}{3}$ 与 $t_1^{*}=\tfrac{4}{3}$ 系由页内已给出的完整方程 $t_2 = 1 + p_{22} t_2$、$t_1^{*} = 1 + p_{12} t_2$ 直接解算所得（由 $t_1=0$ 代入即得），并非臆造；如需最严格逐字原文请回查原书页 369。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 正文 Example 7.13 的数字很小，却把 first-step analysis（第一步分析）的全部语法演示完：$p_{11}=0.8$、$p_{12}=0.2$、$p_{21}=0.6$、$p_{22}=0.4$，目标态取 $s=1$。第一步永远是钉边界：$t_1=0$，因为站在靶上不需要再走。
>
> 第二步只对唯一的 transient state（暂态）写一条方程：$t_2=1+p_{21}t_1+p_{22}t_2=1+0.4\,t_2$，于是 $0.6\,t_2=1$、$t_2=5/3\approx1.667$。把它读成 random experiment（随机试验）更透：从状态 2 出发，每步以 $0.6$ 直接进门、以 $0.4$ 原地兜圈，这就是一枚成功率为 $0.6$ 的 geometric（几何）等待，期望次数 $1/0.6=5/3$，与解方程同值。有了这条「几何等待」的读法，二状态题基本可以口算。
>
> 把全期望定理拆开看，那个 $1$ 是「这一步」，那一项是「下一步之后还要多久」：从 2 出发的一步以 $0.6$ 落到 1（此后还要 $t_1=0$ 步）、以 $0.4$ 留在 2（此后还要 $t_2$ 步），于是 $E[T]=1+0.6\cdot 0+0.4\cdot t_2$，与方程逐项对齐。方程与期望是同一句话的两种写法，不是两套方法。
>
> 第三步算平均递归时间，不重开战场：$t_1^{*}=1+p_{11}t_1+p_{12}t_2=1+0.2\cdot 5/3=4/3\approx1.333$。注意它比 $t_2$ 小：从状态 1 出发，一步就有 $0.2$ 的运气直接回来；从状态 2 出发却要先跨过 $0.6$ 那道门。数字的大小关系本身就是对模型的体检。
>
> 再来一条互不依赖的对账。这条链是 irreducible（不可约）的，其 stationary distribution（平稳分布）满足 $\pi_1=p_{21}/(p_{12}+p_{21})=0.6/0.8=0.75$，而「平均递归时间等于平稳概率的倒数」给出 $t_1^{*}=1/0.75=4/3$，与上一步一致。一条算路走一步分析，一条走平稳分布，两者共同锁住答案。
>
> 反例有两个，方向相反。其一，丢掉 $t_1=0$：两式互推得 $0=20/3$，方程组直接矛盾——边界缺失不是「少一个条件」，而是让系数矩阵奇异。其二，把递归写成自我指涉 $t_1^{*}=1+0.8\,t_1^{*}+0.2\,t_2$，解出 $t_1^{*}=20/3\approx6.667$，整整大了五倍；错因是 $0.8\,t_1^{*}$ 把「还停在状态 1 的这一步」重复计时，而递归时间只该计一次出发。
>
> 线性代数（18.06）里这一步是一行：$Q$ 取暂态块 $[0.4]$，$(I-Q)^{-1}\mathbf{1}=(1-0.4)^{-1}=5/3$ 就是 $t_2$；递归时间则要再乘上「从 $s$ 出发的一步分布」，本题退化成 $1+0.2\cdot5/3$。矩阵形式的价值在于它把「逐态回代」变成一次求逆，状态一多就显出差距：$m$ 个暂态的高斯消元是 $O(m^{3})$ 量级。
>
> 6.006 与 CLRS 里的dynamic programming（动态规划）给了一个漂亮的对照：如果转移图是一张 directed acyclic graph（有向无环图），一步方程退化成「先算没有后继的状态、再倒着填表」，每个状态只算一次，根本不需要解方程组；只有出现环（状态可以互相回到对方）时，才会出现自我指涉，才需要「解线性系统」这件工具。所以「先画图、再看有没有环」是判断该用递推还是该用求逆的实用分界线。
>
> 再补一个三状态的版本，让「求逆」不显得多余。设暂态 $1$、$2$ 与吸收态 $0$，转移为 $1\to0$ 概率 $0.5$、$1\to2$ 概率 $0.5$，$2\to0$ 概率 $0.25$、$2\to1$ 概率 $0.75$。方程是 $t_1=1+0.5\,t_2$、$t_2=1+0.75\,t_1$；回代得 $t_1=1.5+0.375\,t_1$，故 $t_1=2.4$、$t_2=2.8$。矩阵口径 $Q$ 的两行为 $(0,0.5)$ 与 $(0.75,0)$，$(I-Q)^{-1}\mathbf{1}$ 给出同样的 $(2.4,2.8)$，而回代时分母 $0.625$ 正是行列式 $1-0.375$。两种算法在这里完全咬合。
>
> 最后校正一处出处。原文把这一例挂到章末某道讲吸收链基本矩阵的习题上，编号对不上——那一段实际问的是平衡方程解的唯一性，与此例无关。本题的完整方法是三步：目标态人工置 $0$、每个暂态写一条一步方程、回代或求逆；任何一步省掉，得到的都是另一个数。

---

<span style="color:#2471a3;">**[summary]**</span> <span style="color:#00838f;">**平均首次通过时间与平均递归时间的方程组（Equations for Mean First Passage and Recurrence Times）**</span>

考虑一个只有一个常返类（single recurrent class）的马尔可夫链，并令 $s$ 为一个特定的常返状态（recurrent state）。

- 平均首次通过时间（mean first passage times）$t_i$，即从状态 $i$ 出发到达状态 $s$ 的平均步数，是下列方程组关于未知量 $t_i$ 的唯一解（unique solution）：

```math
t_s = 0,
\qquad
t_i = 1 + \sum_{j=1}^{m} p_{ij} t_j ,
\qquad \text{对一切 } i \neq s .
```

- 状态 $s$ 的平均递归时间（mean recurrence time）$t_s^{*}$ 为

```math
t_s^{*} = 1 + \sum_{j=1}^{m} p_{sj} t_j .
```

---

<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span>

<span style="color:#c0392b;">**7.5　连续时间马尔可夫链（Continuous-Time Markov Chains）**</span>

到目前为止我们考虑过的马尔可夫链模型中，都假设状态之间的转移（transitions）花费单位时间。在本节中，我们考虑另一类相关模型，它们在连续时间（continuous time）中演化，可用于研究涉及连续时间到达过程（arrival processes）的系统。典型例子如分布式中心（distribution centers）或通信网络中的节点（nodes），在这些地方，某些我们关注的事件（例如订单或新呼叫的到来）是用泊松过程（Poisson processes）来描述的。

和之前一样，我们将考虑一个过程，它按给定的转移概率（transition probabilities）从一个状态过渡到下一个状态，但我们会把两次转移之间所花费的时间建模为连续随机变量（continuous random variables）。我们仍假设状态数是有限的（finite），并且在没有特别说明的情况下，令状态空间（state space）为集合 $S = \{ \, 1, \ldots, m \, \}$。
<!-- ===== PDF p379 ===== -->
<span style="color:#c0392b;">**§7.5　连续时间马尔可夫链（Continuous-Time Markov Chains）（续）**</span>

> <span style="color:#7f8c8d;">Chap. 7, 本章页码 370。本节内容承接上一页（§7.5 起始段），故标题标注「续」；本页末尾的参数称号「被称为转移…（transition …）」在下一页续完。</span>

为了描述该过程，我们引入若干我们感兴趣的随机变量：

- $X_n$：第 $n$ 次转移（transition）之后所处的状态；
- $Y_n$：第 $n$ 次转移发生的时刻；
- $T_n$：第 $(n-1)$ 次与第 $n$ 次转移之间经过的时间（time elapsed）。

为完整起见，我们记 $X_0$ 为初始状态（initial state），并令 $Y_0 = 0$。我们还引入一些假设。

<span style="color:#00838f;">**[定义] 连续时间马尔可夫链假设（Continuous-Time Markov Chain Assumptions）**</span>

- 若当前状态（current state）为 $i$，则到下一次转移为止的时间服从指数分布（exponentially distributed），参数（parameter）为给定的 $\nu_i$，且与过程过去的历史以及下一状态相互独立。

- 若当前状态为 $i$，则下一状态将以给定的概率 $p_{ij}$ 取为 $j$，且与过程过去的历史以及到下一次转移的时间相互独立。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 两条假设是被 OCR 断行重排的文本（如首条在「exponen-」处换行、次条列表符断行），已按其语义合并复原；首条「exponentially distributed」仅为连字符断行，非真正损坏。</span>

上述假设完整地描述了这个过程，并为我们提供了一种无歧义的仿真（simulate）方法：给定我们刚刚进入状态 $i$，我们会在状态 $i$ 停留一段服从参数为 $\nu_i$ 的指数分布的时间，然后根据转移概率（transition probabilities）$p_{ij}$ 转移到下一状态 $j$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> continuous-time Markov chain（连续时间马尔可夫链）与离散版的分野只有一句话：离散版把「下一次转移」记在整数拍子上，连续版把「下一次转移何时来」也随机化，而这个随机化必须用 exponential distribution（指数分布）。不是「常用」，是「非它不可」。
>
> 机制在 memoryless property（无记忆性）：$P(\tau>t+s\mid\tau>t)=P(\tau>s)$。离散链的 Markov property（马尔可夫性质）只要求「给定现在，未来与过去条件独立」；连续版多背了一个随机变量——剩余驻留时间，若它不无记忆，它的条件分布就会编码「已经待了多久」，于是「只看现在」这句话当场失效。换成确定性驻留（每步恰好一秒）或 uniform distribution（均匀分布），抽样链立刻不再是马尔可夫链，因为它必须记住自己等了多久。
>
> 记号与量纲要分清。$q_{ij}$ 是 transition rate（转移速率），单位是「次数每单位时间」，不是概率；总速率 $V_i=\sum_{j\ne i}q_{ij}$，平均驻留时间是 $1/V_i$。它与 Poisson process（泊松过程）里的 $\lambda$ 地位相同：$\lambda$ 是到达率，$V_i$ 是离开率，短区间内「没有事件」的概率是 $1-V_i\delta+o(\delta)$。把 rate 当 probability 用，平衡方程的量纲立刻错位，因为一边是「次数每时间」、另一边是「一步的概率」。
>
> 竞争时钟的图景能一次讲清所有细节：每个目标 $j$ 各挂一只速率为 $q_{ij}$ 的指数钟，谁先响就去谁那里，驻留时长就是「最早响的那只钟」的读数。指数分布的最小值仍是指数分布，速率相加，所以 $V_i=\sum_j q_{ij}$；又因为「谁先响」与「多久才响」独立（联合概率可分解），转移概率 $P_{ij}=q_{ij}/V_i$ 与驻留时长互不携带信息。这一条独立性是后面嵌入链能单独成链的全部理由。
>
> 给一个可算的采样例子。设 $V_1=2$、$V_2=5$（每秒），平均驻留分别是 $0.5$ 秒与 $0.2$ 秒。取 $\delta=0.01$ 秒做 sampling（抽样），状态 1 在一步内发生转移的概率约 $2\times0.01=0.02$；两步（即 $0.02$ 秒内）发生转移的概率约 $0.04$，而二次项量级 $(V_1\delta)^{2}=4\times10^{-4}$，相对误差约 $1\%$。把 $\delta$ 减到 $0.001$，误差降到 $0.1\%$。这就是 little-o（高阶无穷小）记号 $o(\delta)$ 的实操含义：它保证「一步之内不超过一次转移」在 $\delta\to0$ 时以概率 $1$ 成立。
>
> 于是抽样链的一步转移写得出：$P_{ii}=1-V_i\delta+o(\delta)$，$P_{ij}=q_{ij}\delta+o(\delta)$。注意这两个式子并不是定义，而是上面竞争时钟图景的推论；顺序若颠倒（先定义再解释），就会漏掉「为什么必须指数」。
>
> balance equation（平衡方程）在连续版里守恒的对象换了：离散守恒「每一步的概率质量」，连续守恒「单位时间的发生次数」，写成 $\sum_{k\ne j}\pi_k q_{kj}=\pi_j\sum_{k\ne j}q_{jk}$，左边流入、右边流出。它和离散版是同一套结构，只是把「一步」换成「单位时间」，所以推导只需把 $p_{kj}$ 展开成 $q_{kj}\delta$ 再令 $\delta\to0$，无需新原理。
>
> 18.065 的视角把这条链压缩成 generator（生成元）$Q$：非对角元是 $q_{ij}$、对角元是 $-V_i$，转移半群是 matrix exponential（矩阵指数）$e^{Qt}$；stationary distribution（平稳分布）$\pi$ 满足 $\pi Q=0$。这一步与第 6 章把泊松过程写成计数过程的做法是同一套语言：那边用 $\lambda$ 描述到达，这边用 $V_i$ 描述离开，速率是共同的主角。
>
> 反例收束：把驻留时间换成 uniform distribution 后，剩余时间的条件分布显式依赖已等时长，要做到马尔可夫就得把「已经等了多久」塞进状态，状态空间从有限个整数变成连续统，本章所有「有限状态 + 矩阵」的工具全部作废。指数假设不是修饰，而是这条链只用有限状态描述世界的承重墙。

作为直接推论，在相继转移后得到的状态序列 $X_n$ 是一个转移概率为 $p_{ij}$ 的离散时间马尔可夫链，称为嵌入马尔可夫链（embedded Markov chain）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> embedded Markov chain（嵌入马尔可夫链）做的事情只有一件：把「等了多久」全部丢掉，只记「跳到哪」。$X_n$ 表示第 $n$ 次跳转之后所在的状态，转移概率是 $P_{ij}=q_{ij}/V_i$（$i\ne j$），其中 $V_i=\sum_{k\ne i}q_{ik}$ 是离开 $i$ 的总速率。跳转序列与驻留时长就这样被拆成两个组件。
>
> 为什么拆得干净？看竞争时钟：每个目标 $j$ 挂一只速率 $q_{ij}$ 的指数钟，最短的那只决定去向、也决定停留多久。指数分布的联合概率分解成「谁最先响」乘「最早时刻超过 $t$」两个因子，所以「下一个状态是 $j$」与「驻留超过 $t$」互相独立。独立性正是嵌入链能单独成为一条完整马尔可夫链的理由——它不欠连续链任何信息。
>
> 两套 steady-state probability（稳态概率）必须分开记。时间占比记 $\pi$，跳转频次记 $\pi'$。正文 Example 7.14 的三状态机器给出 $\pi=(30/41,6/41,5/41)$，$\pi'=(2/5,2/5,1/5)$，速率 $V_1=1$、$V_2=5$、$V_3=3$。前者说「钟表时间里有七成多停在状态一」，后者说「每五次跳转有两次落在状态一」，两个数都叫稳态，却不是同一个问题。
>
> 换算关系是 $\pi_iV_i=C\pi'_i$，$C=\sum_k\pi_kV_k=75/41$ 是平均转移速率。逐状态验：状态一 $\pi_1V_1=30/41$，而 $C\pi'_1=(75/41)(2/5)=30/41$；状态二 $\pi_2V_2=(6/41)(5)=30/41$，$C\pi'_2$ 同为 $30/41$；状态三 $\pi_3V_3=(5/41)(3)=15/41$，$C\pi'_3=(75/41)(1/5)=15/41$。三对数字全部咬合，说明「速率乘时间占比」与「平均速率乘频次」是同一个量。
>
> 这条式子顺手给出反解：$\pi_i\propto\pi'_i/V_i$，也就是「频次除以速率再归一化」。它解释了两套分布何时重合：只有在 $\pi'$ 的支撑集上所有 $V_i$ 相等时，除以常数才不改形状；某一个状态若从不被访问，它的速率取值无关紧要，不必参与条件。本题状态一与状态二频次相等而时间占比差五倍，根源就是 $V_1=1$ 与 $V_2=5$ 相差五倍。
>
> 线性代数（18.06）的读法：$Q=V(P-I)$，其中 $V$ 是以 $V_i$ 为对角元的对角矩阵，$P$ 是嵌入链的转移矩阵；代入 $\pi Q=0$ 得 $\pi VP=\pi V$。也就是说 $\pi V$ 是 $P$ 关于特征值 $1$ 的左特征向量，两套稳态之间只差一个对角相似变换。这样看，「除以驻留时长再归一化」不是经验口诀，而是一次变量替换。
>
> 排队论里的对应很具体：$\pi_i$ 是服务器在状态 $i$ 的占用率，$\pi'_i$ 是「完成一次作业后，下一类作业落在 $i$ 的频次」；Little's law（利特尔定律）$L=\lambda W$ 也是在「次数乘时间」这个换算上做文章，与本节是同一套记账法。工程上要看吞吐就取 $\pi'$ 乘速率，要看资源占用就取 $\pi$，混用会系统性偏袒快状态。
>
> 再看一个两状态的小例，把公式压到能口算。设 $q_{12}=2$、$q_{21}=1$，则 $V_1=2$、$V_2=1$；连续链解 $\pi_1q_{12}=\pi_2q_{21}$ 得 $\pi=(1/3,2/3)$，嵌入链因为两状态互跳只有一条路，故 $\pi'=(1/2,1/2)$。平均速率 $C=(1/3)(2)+(2/3)(1)=4/3$，检验 $\pi_1V_1=2/3$ 与 $C\pi'_1=(4/3)(1/2)=2/3$ 相等，$\pi_2V_2=2/3$ 同样对上。速率差两倍、频次却对半，这就是「快状态被时间占比压低」的最小样本。
>
> 最后说明本注在原文里的边界：正文那句「用数学语言表述，我们的假设可如下规范化地表述」属于下一段的开头，不是注的内容，回填时应止于「分水岭」那句为止。收束一句：嵌入链是「数次数」的眼睛，连续链是「数时长」的眼睛，两副眼睛看同一个过程，得到的两个稳态用 $\nu$ 相互翻译。

```math
A = \{ T_1 = t_1, \ldots, T_n = t_n,\; X_0 = i_0, \ldots, X_{n-1} = i_{n-1},\; X_n = i \}
```

为捕获直到第 $n$ 次转移为止过程历史的事件。于是我们有

```math
P\bigl(X_{n+1} = j,\; T_{n+1} \ge t \mid A\bigr)
= P\bigl(X_{n+1} = j,\; T_{n+1} \ge t \mid X_n = i\bigr)
= P(X_{n+1} = j \mid X_n = i)\; P(T_{n+1} \ge t \mid X_n = i),
```

对一切 $t \ge 0$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式的成品不等式符号（$\ge$）在 OCR 中被打散成不可辨字形；此处按上下文（到下次转移的时间服从指数分布、后文衔接期望时间）推定为 $\ge$，若需严格原文请回查原书页 370。拆分为两项乘积是依赖「给定当前状态 $i$ 时，$T_{n+1}$ 与下一状态独立」这条假设。</span>

到下一次转移的期望时间为 $1/\nu_i$，因此我们可以把 $\nu_i$ 解释为：单位时间停留在状态 $i$ 期间，离开状态 $i$ 的平均转移次数。从而，参数 $\nu_i$ 被称为转移…

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原文末行「Consequently, the parameter $v_i$ is called the transition …」在「transition」处被换页截断，称号的其余部分（应为 transition rate，转移速率）落在下一页，本页不臆补。</span>
<!-- ===== PDF p380 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**　—　<span style="color:#2471a3;">§7.5 连续时间马尔可夫链（Continuous-Time Markov Chains，续）</span></span>

> <span style="color:#7f8c8d;">本页页首无新节标题，为上一页 §7.5 正文的延续（转移速率 out-of-state-全状态速率 $V_i$ 与转移速率 $q_{ij}$ 的引入与说明），故标题标注「（续）」。页内起新例 Example 7.14。</span>

承接上页关于「离开状态 $i$ 的速率」（rate out of state $i$）的讨论：由于离开状态 $i$ 的转移中，只有一部分（比例 $P_{ij}$）会通往状态 $j$，我们还可以把

```math
q_{ij} = V_i P_{ij}
```

视为：在状态 $i$ 每停留一个单位时间，从状态 $i$ 转移到状态 $j$ 的平均次数。据此，我们称 $q_{ij}$ 为从 $i$ 到 $j$ 的转移速率（transition rate from $i$ to $j$）。注意，当已知转移速率 $q_{ij}$ 时，可利用下式求得转移速率 $V_i$：

```math
V_i = \sum_{j=1}^{m} q_{ij},
```

并可利用下式求得转移概率（transition probabilities）：

```math
P_{ij} = \frac{q_{ij}}{V_i}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损伤] 上两式的求和上限、下标等在 OCR 中被断行打散（原文形如「$V_i = \sum_{j=1}^{m} q_{ij}$」「$P_{ij} = \dfrac{q_{ij}}{V_i}$」），此处按上下文（$q_{ij}=V_i P_{ij}$）与下页通行定义补全为规范记法。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> transition rate（转移速率）$q_{ij}$ 是把「连续时间链」与「速率」接上的关键代号，读懂它整节就能通读。第一性原理只有一句：离散链给你 transition probability（转移概率）$P_{ij}$（跳到哪），连续链另外给你总速率 $V_i=\sum_{j\ne i}q_{ij}$（走得多快），两者相乘才得到「单位时间里从 $i$ 走到 $j$ 的次数」。
>
> 三个量之间的关系是全节的语法：$q_{ij}=V_iP_{ij}$、$V_i=\sum_j q_{ij}$、$P_{ij}=q_{ij}/V_i$。任给两个可推第三个，所以三种写法在不同场合各有用处：讲故事时用 $V_i$ 与 $P_{ij}$（「平均持续多久、结束后去哪」），解平衡方程时用 $q_{ij}$（「每单位时间多少次」）。地址相同、单位不同，这是整节最容易翻车的地方。
>
> 量纲必须分开记。$P_{ij}$ 无量纲、行和为 $1$；$q_{ij}$ 的单位是「次数每单位时间」，行和是 $V_i$ 而不是 $1$。把 $q_{ij}$ 当概率用，错误不会在 $\boldsymbol\pi Q=\mathbf 0$ 上暴露——那个方程对整行的统一缩放不敏感——却会在「一步转移」「$P^{n}$」「时间占比」这三处同时错位。
>
> 拿正文 Example 7.14 逐格验一遍。$V_1=1$、$V_2=5$、$V_3=3$；生产结束必去测试，故 $q_{12}=1\times1=1$；测试结束以 $1/2$ 回生产、$1/2$ 去修理，故 $q_{21}=5\times(1/2)=5/2$、$q_{23}=5\times(1/2)=5/2$，两只出口相加正好 $5=V_2$；修理结束必回生产，故 $q_{31}=3\times1=3$。三行写作 $(0,1,0)$、$(5/2,0,5/2)$、$(3,0,0)$，每一行加总都等于该状态的 $V_i$。
>
> 反解也在同一张表上：$P_{21}=q_{21}/V_2=(5/2)/5=1/2$，$P_{23}=1/2$，与故事里的「阳性/阴性」对得上。若有人把 $(5/2,5/2)$ 直接当概率，行和变成 $5$，$P^{n}$ 就会把质量放大成 $5^{n}$ 倍，根本无法解释为一个分布；更麻烦的是平衡方程本身不会报警（方程与行的统一缩放无关），错误只会在解释「一步」与「时间占比」时悄悄失真。
>
> 连续时间版里 $q_{ij}$ 与 Poisson process（泊松过程）的 $\lambda$ 是同一个量纲：$\lambda$ 说「单位时间到达几次」，$q_{ij}$ 说「单位时间从 $i$ 到 $j$ 几次」。排队论里服务率 $\mu$ 也是速率族的一员，所以「到达率 $\lambda$、服务率 $\mu$」的模型可以直接写成 $q_{i,i+1}=\lambda$、$q_{i,i-1}=\mu$，不必再乘什么概率。
>
> 线性代数（18.06）那边，$Q$ 不是随机矩阵：把 $q_{ij}$ 摆成矩阵后行和是 $V_i$，要让它成为 generator（生成元）就得把对角元填成 $-V_i$，此时行和为零、常向量落在右零空间。也正因为如此，$\pi Q=0$ 是一个关于 $\pi$ 的线性方程组，而不是「$\pi$ 是 $Q$ 的特征向量」这么一句含糊话。
>
> 建模顺序为什么是「先速率、后概率」？因为从故事里直接读出来的是时长，而不是概率：「报警平均一分钟来一次」给出的是 $1/V_1=1$，不是「一步之后去哪」。把时长取倒数得速率，再用「结束后发生的试验」分摊成 $P_{ij}$，才是顺着信息的流向建模。反过来做（先猜概率再补速率）几乎总要回头改。
>
> 边界情形也要交代：若某状态是 absorbing state（吸收态），则 $V_i=0$，此时 $P_{ij}=q_{ij}/V_i$ 根本无定义，只能保留 $q_{ij}=0$ 的说法。这不是记号的瑕疵，而是「没有离开」这件事无法用「离开之后的去向分布」表达。写代码时若不检查 $V_i=0$，就会在那里除零。
>
> 6.042J 的图论视角可作对照：把 $q_{ij}$ 看成有向带权图的边权，$V_i$ 是顶点出度（按权重计），$P_{ij}$ 是「从 $i$ 出发的随机游走选哪条边」的概率。离散链的正是在这张图上每步走一条边；连续链则额外给每条边挂一只时钟，谁先响走谁。两张图共用同一副骨架，只是「何时走」的信息多了一层。
>
> 反例收束：把 $P_{ij}$ 与 $q_{ij}$ 混用之后，最容易出现的症状是「时间占比与频次算出来差一个因子」，而这正是下一段 Example 7.14 要用两套稳态对照的地方。记住一句话：$P$ 分配去向，$V$ 决定快慢，$q$ 是两者之积；三者混用，模型就会在任何一处出现量纲裂缝。

注意，该模型允许自转移（self-transition），即从某个状态回到它自身，这在自转移概率 $P_{ii}$ 非零时确实可能发生。然而，这样的自转移没有可观测的影响：由于指数分布（exponential distribution）的无记忆性（memorylessness），无论刚刚是否发生过一次自转移，距离下一次转移所剩余的时间都是相同的。出于这一原因，我们可以忽略自转移，并且自此假设对所有 $i$ 均有

```math
P_{ii} = q_{ii} = 0,
\qquad \text{对所有 } i .
```

---

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「自转移不可观测，所以干脆无视」这句话在全章里只出现过一次，却是连续时间链特有的一种奢侈：离散时间链里 self-transition（自转移）$p_{ii}>0$ 会实实在在地消耗一步、改变访问次数与周期，而连续时间里自转移「什么都没发生，时钟却在走」。
>
> 机制拆成两层。第一层是指数分布的 memorylessness（无记忆性）：站在 $i$ 上的剩余停留时间与「已经站了多久」无关，所以一次自转移发生之后，剩余的等待仍是同一个 exponential distribution（指数分布），分布形状一丝不变。第二层是「可观测性」：任何只依赖状态轨道的量——长时间占比、首次通过时间、吸收概率——都只看 $X(t)$ 落在哪个状态，不看中间被标记了几次，于是自转移在模型里完全冗余。
>
> 换一种写法更清楚：若允许 $q_{ii}>0$，则轨迹在 $i$ 上多出一些标记时刻，但这些标记之间的间隔仍是指数分布，且下一次真正离开 $i$ 的去向分布仍是 $q_{ij}/V_i$。把自环从图上删掉、把 $V_i$ 重新定义为 $\sum_{j\ne i}q_{ij}$，所有可观测量逐点不变。这就是正文随后约定 $q_{ii}=P_{ii}=0$ 的全部理由。
>
> 给一个可算的对照。正文 Example 7.14 里 $V_2=5$、$P_{21}=P_{23}=1/2$。若在状态 2 上额外加一条速率 $5$ 的自环，取 $\delta=0.01$ 抽样：一步内自环概率约 $0.05$，去状态 1 与去状态 3 各约 $0.025$。把自环合并掉再重新归一化，出口比例仍是 $0.025/0.05=1/2$，与原来一字不差；而「平均驻留 $0.2$ 秒」这条也没变，因为自环只是把两次标记之间的距离重新分配，不改变从进入状态到离开状态的总时长。
>
> 离散链上就完全不同。$p_{ii}>0$ 会把周期 $d$ 压成 $1$（这正是 PageRank 里 damping（阻尼）项的作用），也会让平均首达时间改变，因为每一步都要重新抛一次硬币。把「自转移无用」照搬到离散链上，周期与首达时间会同时算错，而且错得很隐蔽——矩阵的行和仍是 $1$，看上去一切正常。
>
> 排队论与 18.065 各有一个镜像。排队系统里「服务完成但队列已空」的时刻不会被记成状态变化，它可以看作一次自转移，统计上只影响时间占比的细分、不影响忙闲结构；生成元 $Q$ 的对角元写成 $-V_i$，等于把所有自转移的速率一次性吸收进对角，这也解释了为什么 $Q$ 的行和必须为零——零行和与「自环被合并」是同一件事的两种说法。
>
> 还要避免一个误读：无记忆性保证的是「剩余时间分布不变」，不是「自转移概率为零」。在抽样链 $Z_n=X(n\delta)$ 里，自转移概率 $1-V_i\delta+o(\delta)$ 是正的，而且随 $\delta$ 增大而增大；我们能做的是在理论上忽略它，而不是声称它不存在。
>
> 收束一句：连续时间的自环是「没有内容的等待」，删掉它不丢失信息；离散时间的自环是「占了一拍的空转」，删掉它会改变节拍。两者的差别不在图，而在「一拍」是概率步长还是钟表时间。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.14（一台机器的生产、测试与修理模型。）**</span>

一台机器，一旦进入生产模式（production mode），将持续运行直到产生一个报警信号（alarm signal）。到达报警信号的时间是一个参数为 $1$ 的指数随机变量。在报警信号之后，机器被测试一段指数分布的时长，其参数为 $5$。测试结果以概率 $1/2$ 为阳性（positive），此时机器返回生产模式；或以概率 $1/2$ 为阴性（negative），此时机器被送去修理（repair）。修理的持续时间服从参数为 $3$ 的指数分布。我们假设上述提到的所有随机变量都互相独立，并且都独立于测试结果。

令状态 $1$、$2$、$3$ 分别对应生产模式、测试和修理。转移速率为 $V_1 = 1$、$V_2 = 5$、$V_3 = 3$。转移概率和转移速率由以下两个矩阵给出：

```math
P = \begin{bmatrix}
0 & 1 & 0 \\
1/2 & 0 & 1/2 \\
1 & 0 & 0
\end{bmatrix}
\qquad
Q = \begin{bmatrix}
0 & 1 & 0 \\
5/2 & 0 & 5/2 \\
3 & 0 & 0
\end{bmatrix}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 两个矩阵的布局在 OCR 中被严重打散（原页文字出现「[0 0 0」「3.」「5/2 5/2 .」等碎片）。因上方正文已显式给出 $V_1=1,\,V_2=5,\,V_3=3$ 及各跳到下一状态的转移概率（生产→测试为 $1$；测试以此法 $1/2$ 回生产、$1/2$ 去修理；修理→生产为 $1$），故按 $q_{ij}=V_i P_{ij}$ 与行和 $=V_i$ 自洽重建如上二矩阵（$P$ 的各行为 $[0,1,0],\,[1/2,0,1/2],\,[1,0,0]$；$Q$ 的各行为 $[0,1,0],\,[5/2,0,5/2],\,[3,0,0]$）。若需最严格原文，请回查原书。</span>

> <span style="color:#7f8c8d;">See Fig. 7.20 for an illustration.（图 7.20 见本页之外作图示说明。）</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 正文 Example 7.14 把「生活故事 → 转移速率矩阵」这一整套建模动作演到底：先数出三种模式（生产、测试、修理）当状态，再把每段「持续多久」翻译成指数分布的参数当速率，最后把「结束后去哪」的转移概率与速率相乘。三步各管一件事，混淆任何一步矩阵就建不起来。
>
> 第一步是数状态。故事里机器只有三种可观测的处境，于是 state（状态）就取三个：生产记 $1$、测试记 $2$、修理记 $3$。这里没有「已经生产了多久」这一类信息，因为指数分布 memorylessness（无记忆性）保证剩余时间与历史无关——这正是能用一个状态顶住整段历史的原因。
>
> 第二步是把时长换成速率。报警信号到达时间是参数为 $1$ 的 exponential distribution（指数分布），平均持续 $1$ 分钟，故 $V_1=1$；测试时长参数为 $5$，平均 $0.2$ 分钟，故 $V_2=5$；修理时长参数为 $3$，平均 $1/3$ 分钟，故 $V_3=3$。rate（速率）与平均时长互为倒数，这一步的量纲是「每分钟次数」。
>
> 第三步是把去向写成 transition probability（转移概率）再乘速率。生产结束必然报警并进入测试，故 $P_{12}=1$；测试结果阳性（概率 $1/2$）回生产、阴性（概率 $1/2$）去修理，故 $P_{21}=P_{23}=1/2$；修理完成必回生产，故 $P_{31}=1$。于是 $q_{ij}=V_iP_{ij}$ 给出三行 $(0,1,0)$、$(5/2,0,5/2)$、$(3,0,0)$，行和分别等于 $1$、$5$、$3$。
>
> 这里必须纠正原文的一处措辞：它把 $Q=V\cdot P$ 称作「归一化概率」，这是错的。$Q$ 不是概率矩阵，而是 transition rate matrix（转移速率矩阵）；$VP$ 只给出它的非对角部分，对角元要补成 $-V_i$ 才成为 generator（生成元）。若真把 $VP$ 当概率矩阵，行和是 $V_i$ 而非 $1$，求平稳分布时会解出一个和不为 $1$ 的向量。
>
> 用更新周期做一次独立验算。一次完整循环是「生产 $1$ 分钟 → 测试 $0.2$ 分钟 → 以 $1/2$ 的概率去修理 $1/3$ 分钟」，平均一个循环长 $1+0.2+(1/2)(1/3)=1+0.2+0.1667=1.3667$ 分钟。生产时间占 $1/1.3667=0.7317$，正是正文后文给出的 $30/41$；测试占 $0.2/1.3667=0.1463$，即 $6/41$；修理占 $0.1667/1.3667=0.1220$，即 $5/41$。三个份额相加为 $1$，这条「按循环平均」的算法与解平衡方程得到同一组数。
>
> 排队论里这张表就是一台「服务台 + 返工环节」的骨架：生产是服务、测试是质检、修理是返工，返工概率 $1/2$ 决定有效服务时间被放大成 $1+0.5\times(1/3)$ 倍。18.065 里则是三对角之外的稀疏结构——这台机器的 $Q$ 只有四条非零出边，稀疏性是故事本身给的，不是数值巧合。
>
> 还有一个建模决定值得说明：状态里不必记「这是第几次测试」或「已经生产了多久」。前者不需要，因为每次测试都是独立的同分布试验，历史不改变下一次的阳性概率；后者不需要，因为报警信号的到达时间无记忆。两个「不必」都来自同一条性质，这也是为什么三个状态就够，而某些看起来相似的机器（例如会磨损的设备）必须把年龄写进状态。
>
> 反例收束：若把测试阶段的 $V_2$ 误记成 $1$，则 $q_{21}=q_{23}=1/2$，行和变成 $1$，测试在时间轴上被拉长五倍，生产占比会从 $0.7317$ 掉到 $0.5$ 附近，整套占用率结论随之作废。速率是这张矩阵唯一的记分牌，改它等于改模型。
<!-- ===== PDF p381 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）・§7.5 连续时间马尔可夫链（Continuous-Time Markov Chains）（续）**</span>

> <span style="color:#7f8c8d;">本节为上一页正文的延续：本页页首没有出现新的小节标题，内容继续讨论连续时间马尔可夫链（continuous-time Markov chain）如何通过转移速率（transition rates）及其与离散时间版本之间的关系来描述。本页 OCR 整体损坏严重，多个句子与公式被拆散成碎片。</span>

内容承接上一页，继续描述连续时间马尔可夫链。文中提到，标在各条弧（arc）旁的正是转移速率（transition rates）$q_{ij}$。

[原页此处 OCR 损坏] 原文此处涉及状态（state）与马尔可夫性质（Markov property）的句子残缺，仅可辨认出零散片段，大意与「……（$t$）是系统的状态…… 现在的（present）…… $X(\tau)$ 对 $\tau > t$…… 以及对 $\tau < t$……」有关，无法完整还原，此处不臆造其余措辞。

我们接下来详细阐述连续时间马尔可夫链与一个对应的离散时间版本之间的关系。（原文此处为 "We now elaborate on the relation between a continuous-time Markov chain and a corresponding version"，但 OCR 将「抽样（sampling）/ 相应版本」等关键措辞打散。）描述一个连续时间马尔可夫链，$Z_n = X(n\delta)$，$n = 0,\, 1,\, \ldots$

也就是说：把连续时间链在间隔为 $\delta$ 的时间点上抽样（sampling），得到的序列 $Z_n = X(n\delta)$ 构成一个离散时间马尔可夫链，可借助（……对……的马尔可夫性质……）来描述 $Z_n$ 的转移概率（transition probabilities）。

[原页此处 OCR 损坏] 原文中有关 $(n+1)\delta$、某一个转移概率（transition probability）、在时刻 $t$ 的一次转移（transition）等句子严重残缺、被断行分散，仅保留上述零散可读片段；其中涉及的数值与转移速率的实际取值一概不臆造。

一个常见的约定（common convention）是让 $X(t)$ 指称恰好在该次转移之后紧随的状态，从而使……与……相同……（其中 $(Y_n)$ 为……）。

> <span style="color:#7f8c8d;">§7.5 连续时间马尔可夫链。本页为上一页的延续，论述连续时间链经抽样化为离散时间链 $Z_n = X(n\delta)$ 及其转移概率的描述方式（延续前述以转移速率 $q_{ij}$ 标注各弧的链图刻画）。</span>
<!-- ===== PDF p382 ===== -->
<span style="color:#c0392b;">**§7.5　连续时间马尔可夫链（Continuous-Time Markov Chains）**</span> ——正文续接（续）

> <span style="color:#7f8c8d;">承接上一页：在把连续时间马尔可夫链离散化采样为时间步长为 $\delta$ 的链 $Z_n$ 之后，本节继续由转移速率（transition rate）$q_{ij}$ 写出一步转移概率 $P_{ij}$。本页开头为 §7.5 正文中部，故标注「续」。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「抽样」这一步是连续与离散之间的翻译器，值得把记号 little-o（高阶无穷小）$o(\delta)$ 读透。做法是把连续时间链在间隔为 $\delta$ 的网格上取点，得到 $Z_n=X(n\delta)$；要证的是 $Z_n$ 本身是一条离散时间马尔可夫链，并且它的一步转移概率可以只用 $q_{ij}$ 写出来。
>
> 第一性原理是「短时段内事件的阶」。在长度 $\delta$ 的窗口里，从 $i$ 跳到 $j$ 的概率按 $q_{ij}\delta$ 线性增长；发生两次以上转移的概率是 $\delta$ 的高阶量，写成 $o(\delta)$，即它比 $\delta$ 更快趋于零。于是保留一次项、丢掉高阶项，就得到 $P_{ij}=q_{ij}\delta+o(\delta)$ 与 $P_{ii}=1-V_i\delta+o(\delta)$。
>
> 用竞争时钟能算得更实：$\delta$ 内至少发生一次转移的概率是 $1-e^{-V_i\delta}=V_i\delta+o(\delta)$；至少两次需要两只时钟先后响，概率量级是 $(V_i\delta)^{2}$，相对误差约 $V_i\delta$。所以 $o(\delta)$ 不是敷衍的符号，它精确地标出「被丢掉的那部分有多小」。
>
> 代正文 Example 7.14 的数字。取 $\delta=0.01$ 分钟（$0.6$ 秒），状态 1 的 $V_1=1$、$q_{12}=1$，于是 $P_{12}\approx0.01$、$P_{11}\approx0.99$；状态 2 的 $V_2=5$、$q_{21}=q_{23}=5/2$，于是 $P_{21}=P_{23}\approx0.025$、$P_{22}\approx0.95$。丢掉的高阶项量级是 $(5\times0.01)^{2}=0.0025$，相当于 $0.25\%$，这就是「小 $\delta$ 近似」的实际误差。
>
> 反例把边界画得很清楚：若取 $\delta=0.5$ 分钟，$V_2\delta=2.5>1$，公式会给出「自转移概率 $1-2.5=-1.5$」这种荒谬结果。也就是说线性近似只在 $\delta<1/\max_i V_i$ 时才有意义，取 $\delta$ 太大时一个窗口里可能发生多次转移，一步转移矩阵不再是原链的忠实指纹。
>
> 线性代数（18.06）给了这条近似一个精确身份：抽样链的一步矩阵其实是 matrix exponential（矩阵指数）的一阶截断，$e^{Q\delta}=I+Q\delta+\frac{1}{2}Q^{2}\delta^{2}+\cdots$。丢掉 $o(\delta)$ 就是只留前两项，误差项由 $Q^{2}\delta^{2}/2$ 控制；这也解释了为什么 $P_{ii}=1-V_i\delta$ 里的 $V_i$ 正好是 $-Q_{ii}$。
>
> 第 6 章的泊松过程是同一件事的标量版：短区间内「恰好一个到达」的概率是 $\lambda\delta+o(\delta)$，「两个及以上」是 $o(\delta)$，正文在这里只是把它从一维计数推广到多状态跳转。两处共用同一句「短窗口里最多一件事」，这也是全章从离散跨到连续的共同跳板。
>
> 抽样链真正的用途是把连续问题搬进已经会算的工具箱：一旦 $Z_n$ 是离散链，$n$ 步之后的状态分布就是 $P^{n}$ 乘初始向量，平稳分布、首达时间、吸收概率全部回到第 7 章前面的矩阵方法。换句话说，抽样不是近似掉精度，而是换取「矩阵幂」这件现成武器，代价是误差随 $\delta$ 收缩。
>
> 误差会随步数累积，这一点要算清楚。单步截断误差是 $O(\delta^{2})$，$n$ 步之后总误差最坏是 $O(n\delta^{2})$；若关注的是时长 $t=n\delta$ 内的行为，则误差量级是 $O(t\delta)$。所以「小 $\delta$」应当读成「$\delta$ 相对 $1/\max_i V_i$ 很小」，而不是「$\delta$ 是某个绝对值」——同一台机器把 $V_2$ 从 $5$ 提到 $50$，可用的 $\delta$ 就小了十倍。
>
> 实际使用里最常见的错法不是取太小，而是为了省计算量把 $\delta$ 取大：$V_2=5$ 时取 $\delta=0.1$ 还能勉强用（误差 $0.5\%$），取 $\delta=0.3$ 就已经 $1.5$，一步之内平均一点五次转移，线性项彻底失真，模型会凭空给出负概率。
>
> 收束：$o(\delta)$ 是这条推导的许可证——它允许我们把无限复杂的「窗口内任意多次转移」压成一次，并明确代价是误差随 $\delta$ 线性消失。$\delta$ 越小，抽样链越像原链；但 $\delta$ 永远取不到 $0$，因为一旦取 $0$，抽样链就退化为恒等映射，什么也测不到。

```math
P_{ij} = P(Z_{n+1} = j \mid Z_n = i) = \nu_i p_{ij}\delta + o(\delta) = q_{ij}\delta + o(\delta),
```

（若 $j \ne i$），其中 $o(\delta)$ 表示一项随 $\delta$ 变小而与 $\delta$ 相比可忽略不计的小量（a term that is negligible compared to $\delta$，as $\delta$ gets smaller）。保持在状态 $i$ 的概率（即时间 $n\delta$ 与 $(n+1)\delta$ 之间不发生转移的概率）为

```math
P_{ii} = P(Z_{n+1} = Z_n = i) = 1 - \sum_{j \ne i} P_{ij}.
```

这就引出了下面这种等价的描述（alternative description）。<span style="color:#7f8c8d;">t</span>

<span style="color:#00838f;">**[描述] Alternative Description of a Continuous-Time Markov Chain（连续时间马尔可夫链的等价描述）**</span>

给定一个连续时间马尔可夫链的当前状态（current state）$i$，并且对任意 $j \ne i$，在 $\delta$ 个时间单位之后该状态等于 $j$ 的概率为

q_{ij}\delta + o(\delta)，

并且与过程的历史（past history）无关。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 该描述盒中「以概率 …」与「与整个过程的历史无关」之间的显式公式在 OCR 中被省略，未捕获到算式。此处按本页前文同页推导直接给出的同一恒等式还原为 $q_{ij}\delta + o(\delta)$；若需最严格原文请回查原书页 373。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.14（续）。**</span> 忽略掉 $o(\delta)$ 项之后，对应的离散时间马尔可夫链 $Z_n$ 的转移概率矩阵（transition probability matrix）为

```math
\begin{bmatrix}
\phantom{\delta} & \phantom{\delta} \\
\phantom{\delta} & \phantom{\delta}
\end{bmatrix}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Example 7.14（续）所给出的那个离散时间链 $Z_n$ 的转移概率矩阵，在第 373 页原书中以矩阵/分块形式排版，但其内容在 OCR 中被切碎得无法辨认（OR 读取到的形如「$1{-}1\,\delta$ / $\tfrac{5}{2}\delta$（或 $5\delta/2$）/ $3\delta$ / $\delta$ …」的碎片，行与列的结构关系不明）。该例为三状态链（$\pi_1,\pi_2,\pi_3$），故真实矩阵应为 $3\times 3$，此处以占位矩阵替代并在维数上也作占位；矩阵各系数的真实数值请回查原书页 373，此处绝不臆造系数。</span>

> <span style="color:#7f8c8d;">[footnote] <span style="color:#7f8c8d;">t</span> 我们迄今的论证表明，一个连续时间马尔可夫链满足上述等价描述。反过来，可以证明：如果我们从这种等价描述出发，则直到离开状态 $i$ 的那一次转移为止的等待时间是一个以参数 $\nu_i = \sum_j q_{ij}$ 计的指数随机变量（exponential random variable）。再者，给定刚刚发生了这样一次转移，则下一个状态等于 $j$ 的概率为 $q_{ij}/\nu_i = p_{ij}$。这就确立了：该等价描述与原描述是等价的。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.15（排队问题，Queueing）。**</span> 分组（packets）按照速率为 $\lambda$ 的泊松过程（Poisson process）到达通信网络（communication network）的一个节点。这些分组被存放在一个容量最多可容纳 $m$ 个分组的缓冲器（buffer）中，然后逐一分组地（one at a time）被发出。但是，若某个分组在到达时发现缓冲器已满（a full buffer），它就会被丢弃。传输一个分组所需的时间服从参数为 $\mu$ 的指数分布（exponentially distributed with parameter $\mu$）。不同分组的传输时间相互独立，并且与所有的到达间隔时间（interarrival times）也都相互独立。

我们将用状态为 $X(t)$ 的连续时间马尔可夫链来为这个系统建模，其中 $X(t)$ 等于在时刻 $t$ 时系统中的分组数（如果 $X(t) > 0$，则 ……

> <span style="color:#7f8c8d;">§7.5, p.373（Example 7.15 语句在本页末被切断：「if $X(t) > 0$, then …」，续接至下一页）。</span>
<!-- ===== PDF p383 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — §7.5 连续时间马尔可夫链（Continuous-Time Markov Chains）续接

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 7.15（续）—— 一个带传输排队系统的连续时间马尔可夫模型（包队列生灭过程 birth–death process）**</span>

> <span style="color:#7f8c8d;">承接上一页：某系统在某节点上对数据包（packet）进行传输，传输时长服从指数分布且其速率由服务站能力决定；设 $X(t)$ 表示当前时刻 $t$ 系统的状态，即系统中「在传 + 排队」的数据包总数。本页从状态 $X(t)$ 的语义分析开始续讲，进一步给出各状态的转移速率 $q_{ij}$，并说明其确为一马尔可夫链。图号与例号以本页原文为准而非编者自造。</span>

系统状态 $X(t)$ 的解释为：当前有 $X(t)-1$ 个数据包正在队列中等待（waiting in the queue），且有 $1$ 个数据包正在传输（under transmission）。当一个新的数据包到达（a new packet arrives）时，状态便加一（increases by one）；当一个已有的数据包完成传输离开（an existing packet departs）时，状态便减一（decreases by one）。为了说明 $X(t)$ 确实是一个马尔可夫链（Markov chain），我们来验证其转移速率 $q_{ij}$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述「状态含义 + 到达/离开各使状态±1 + 验证马尔可夫性」的过渡段，在 OCR 中被打散为碎片词（如 state / by one / a new packet / an existing packet departs / To show that X(t) is indeed a Markov chain, we verify rates q_ij 等），此处按标准语义连贯复原；无新增数值。</span>

先考虑状态 $X(t)=0$ 的情形，即队列为空、没有包在传输的场合（the case where the state $X(t)$ is equal to $0$, i.e. the queue is empty）。离开状态 $0$ 的转移（a transition out of state $0$）只能发生在有新的数据包到达时，于是

```math
P\bigl(X(t+\delta)=1 \mid X(t)=0\bigr) = \lambda\delta + o(\delta),
```

故 $q_{0j}=\lambda$（当 $j=1$ 时），其余 $j$ 取 $0$。

接着考虑系统满载的情形，即状态 $X(t)=m$ 的场合。离开状态 $m$ 的转移将发生在当前这包传输完成之时，把状态带到 $m-1$。由于传输时长是指数分布（exponential）的，从而尤其具有无记忆性（memoryless），我们有

```math
P\bigl(X(t+\delta)=m-1 \mid X(t)=m\bigr) = \mu\delta + o(\delta),
```

故 $q_{mj}=\mu$（当 $j=m-1$ 时），其余 $j$ 取 $0$。

再考虑一般的中间状态 $i$，其中 $0\lt i\lt m$。在接下来的 $\delta$ 个时间单位内，有一个新数据包到达的概率为 $\lambda\delta+o(\delta)$，它会把状态带到 $i+1$；同时，传输完成从而把状态带到 $i-1$ 的概率为 $\mu\delta+o(\delta)$。（其余情形所对应概率的阶 $o(\delta^2)$ 项与其它 $o(\delta)$ 项一并列出。）即

```math
P\bigl(X(t+\delta)=i-1 \mid X(t)=i\bigr) = \mu\delta + o(\delta),\qquad
P\bigl(X(t+\delta)=i+1 \mid X(t)=i\bigr) = \lambda\delta + o(\delta),
```

故 $q_{ij}=\lambda$（当 $j=i+1$）、$\mu$（当 $j=i-1$），$i=1,2,\dots,m-1$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述状态 $m$ 与中间状态 $i$ 的说明、以及两个条件概率式与 $q_{ij}$ 的分类定义，在 OCR 中被切为极零碎的断片（如 `= p.6 + 0(6)`、`(t+δ)=m-1 ∣ (t)=m`、`probability .x 8 + 0(8)`、`µδ+o(δ)`、`if j=i-1`、`i=1,2,...,m-1` 等）。参数名 $\lambda$（到达速率）与 $\mu$（传输速率），以及必经 $m-1$、状态±1 的上述结构，均与本节稍后给出的转移速率图（Fig.~7.21）相符，此处按标准语义连贯复原；未引入任何非原文的数值。</span>

该转移速率关系可在转移速率图（transition rate diagram）中直观呈现（见 Fig. 7.21：各中间状态 $i$ 以速率 $\lambda$ 通向 $i+1$、以速率 $\mu$ 通向 $i-1$，边界状态 $0$、$m$ 分别只有到来与离开支路），其形态即为一类生灭过程（birth–death process）-型的链。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页末端原文提到图 "Fig. 7.21: Transition rate diagram"（OCR 残作 "7.21: Transition ... 7.15."），并指出该转移图「属于某类……型」（OCR 残作 `[, is of`）结构，结尾落入换页符。此处仅以与原书一致的「转移速率图、生灭过程型」语义作保守复原；图的精确坐标/标注无法辨认，一律按原图残缺处理，不做数值化。</span>
<!-- ===== PDF p384 ===== -->
<span style="color:#c0392b;">**Sec. 7.5　连续时间马尔可夫链（Continuous-Time Markov Chains）**</span>

<span style="color:#00838f;">**[小节]**</span> <span style="color:#00838f;">**Steady-State Behavior（稳态行为）**</span>

现在我们转而关注连续时间马尔可夫链（continuous-time Markov chain）的长期行为（long-term behavior），并聚焦于当 $t$ 变大时状态占据概率（state occupancy probabilities）$P(X(t) = i)$ 的极限。我们通过研究相应的离散时间链 $Z_n$ 的稳态概率（steady-state probabilities）来逼近这个问题。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本行「Since $Z_n = X(n\delta)$」中「$Z_n = X(n\delta)$」部分被 OCR 打散（如将 $X(n\delta)$ 误读为 `X ( n8 )`）。按上文可读英文「Since $Z_n =$… it is clear that the limit of $P(Z_n = j \mid Z_0 = i)$」及第 7.5 节上下文复原为 $Z_n = X(n\delta)$。若需最严格原文，请回查原书该页。</span>

由于 $Z_n = X(n\delta)$，显然 $P(Z_n = j \mid Z_0 = i)$ 的极限（若存在）与 $P(X(t) = j \mid X(0) = i)$ 的极限相同。因此仅需考虑与 $Z_n$ 相关联的稳态概率即可。仿照离散时间情形的推理，我们看到：要使稳态概率独立于初始状态（initial state），我们需要链 $Z_n$ 具有唯一的常返类（recurrent class），此后我们始终假设这一点成立。我们还注意到，马尔可夫链 $Z_n$ 自动是非周期的（aperiodic）。这是因为其自转移概率（self-transition probabilities）具有如下形式

```math
p_{ii} = 1 - \delta \sum_{j \ne i} q_{ij} + o(\delta),
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式自转移概率 $p_{ii}$ 被 OCR 打散成碎片（如将减号误读为 `+`、将 $\sum_{j\ne i} q_{ij}$ 误读为 `8 L qij 0(8)`）。按可读英文「self-transition probabilities are of the form… which is positive when $\delta$ is small」及生灭速率结构 $q_{ii} = -\sum_{j\ne i}q_{ij}$ 复原为 $p_{ii} = 1 - \delta \sum_{j\ne i} q_{ij} + o(\delta)$；若需最严格原文请回查原书该页。</span>

当 $\delta$ 很小时其为正，而具有非零自转移概率的链总是非周期的。

链 $Z_n$ 的平衡方程（balance equations）具有如下形式

```math
\pi_j = \sum_{k=1}^{m} \pi_k p_{kj}, \qquad \text{对所有 } j,
```

即

```math
\begin{aligned}
\pi_j &= \pi_j p_{jj} + \sum_{k \ne j} \pi_k p_{kj} \\
    &= \pi_j \Bigl( 1 - \delta \sum_{k \ne j} q_{jk} + o(\delta) \Bigr)
     + \sum_{k \ne j} \pi_k \bigl( \delta\, q_{kj} + o(\delta) \bigr).
\end{aligned}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述平衡方程（连续时间情形的两行推导式）被 OCR 打成碎片（如将 $\pi_j = \pi_j p_{jj} + \sum_{k\ne j} \pi_k p_{kj}$ 误读为 `'Trj 'TrjPjj + L 'TrkPkj`，并将下标的 $\ne j$ 误读为 `k:j:.j`）。按可读英文「The balance equations for the chain $Z_n$ are of the form $\pi_j = \sum_{k=1}^m \pi_k p_{kj}$」以及随后中文所述「消去 $\pi_j$、除以 $\delta$、令 $\delta\to 0$」的步骤复原为如上标准形式；若需最严格原文请回查原书该页。</span>

我们消去方程两边都出现的项 $\pi_j$，两边除以 $\delta$，再令 $\delta$ 递减为零取极限，得到平衡方程（即连续时间的平衡方程）

```math
\sum_{k \ne j} \pi_k q_{kj}
= \pi_j \sum_{k \ne j} q_{jk}.
```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一对方程是整章从离散跨进连续的那道门：$\sum_{k\ne j}\pi_k q_{kj}=\pi_j\sum_{k\ne j}q_{jk}$。左边是单位时间里从别处流进 $j$ 的期望次数，右边是从 $j$ 流出的期望次数，一句话：稳态下每个状态的进出口相抵。它叫 balance equation（平衡方程），因为守恒的对象换了——离散版守恒「每一步的概率质量」，连续版守恒「单位时间的发生次数」。
>
> 推导就在紧邻的两行里，逐符号读一遍。把离散平衡方程里的 $p_{kj}$ 换成 $q_{kj}\delta+o(\delta)$、$p_{jj}$ 换成 $1-V_j\delta+o(\delta)$，两边都出现 $\pi_j$，约掉；两边都线性挂着 $\delta$，除掉；再令 $\delta\to0$，$o(\delta)$ 与 $\delta$ 之比蒸发，剩下的正是速率版。整步只做了一件事：把「每一步的概率」换算成「单位时间的次数」，等式两边因此从无量纲变成 transition rate（转移速率）的量纲。
>
> 线性代数把它压成一行：令 generator（生成元）$Q$ 的非对角元为 $q_{jk}$、对角元为 $-V_j$，则平衡方程就是 $\boldsymbol\pi Q=\mathbf 0$，再配 normalization（归一化）$\sum_j\pi_j=1$。两个零空间要分清：$Q$ 的每一行之和为零，所以常向量 $\mathbf 1$ 是右 null space（零空间）里的元素；而 $\boldsymbol\pi$ 是 $\lambda=0$ 的 left eigenvector（左特征向量）。stationary distribution（平稳分布）是分量全正、和为 $1$ 的那个唯一左零向量，它由 $Q$ 单独决定，与 initial distribution（初始分布）无关。
>
> 代入正文 Example 7.14 验一遍。取 $\boldsymbol\pi=(30/41,6/41,5/41)$，$Q$ 的三行是 $(-1,1,0)$、$(5/2,-5,5/2)$、$(3,0,-3)$，逐行内积得 $0$、$0$、$0$。再看列和：第一列 $-1+5/2+3=9/2$，第二列 $1-5=-4$，第三列 $5/2-3=-1/2$，没有一列是零。这个不对称必须记住，但它的含义不是「可逆性」。
>
> 第一处纠正：列和为零并不等价于 reversible（可逆）。对一个行和为零的 generator，列和为零等价于 $\mathbf 1^{T}Q=\mathbf 0$，也就是「均匀分布是平稳分布」；它与细致平衡无关。反例是三状态确定性环：$a\to b$、$b\to c$、$c\to a$ 各速率 $1$，反向全为 $0$。它的列和是 $(0,0,0)$，$\boldsymbol\pi$ 均匀，但 detailed balance（细致平衡）明显失败——$\pi_aq_{ab}=1/3$ 而 $\pi_bq_{ba}=0$。所以「列和为零」标出的是均匀稳态，不是可逆链。
>
> 第二处纠正：不能把 $\boldsymbol\pi Q=\mathbf 0$ 写成 $Q\boldsymbol\pi=\mathbf 0$。右零空间被常向量 $\mathbf 1$ 占据（行和为零的直接后果），而 $\boldsymbol\pi$ 是左零向量；一般的 $Q$ 左右零空间并不重合，把 $\boldsymbol\pi$ 塞进右边解出来的是另一个向量，数值上却完全像模像样。只有两种情形两式同解：$Q$ 左右对称（可逆链的相似对称化版本），或者 $\boldsymbol\pi$ 恰好均匀（此时 $\boldsymbol\pi\propto\mathbf 1$，正好落在右零空间里）。
>
> 与 local balance（局部平衡）的分野要现在立起来。逐状态求和的全局方程总是成立；只有生死结构这类相邻跳跃，才能拆成逐边的 $\pi_iq_{ij}=\pi_jq_{ji}$。有环流的链上逐边等式失败而全局等式照样成立，所以下一节的局部平衡不是新公理，而是结构白送的额外结论；Kolmogorov 判据（沿闭环正反两方向速率乘积相等）给出它成立的充要条件。
>
> 还有一处量纲陷阱：$Q$ 不是 transition probability matrix（转移概率矩阵），行和是 $0$（或未加对角时是 $V_i$）而不是 $1$，所以不能拿它直接做 $P^{n}$。要那样做须先 uniformization（均匀化），把 $Q$ 换成 $I+Q/\gamma$，$\gamma$ 取不小于 $\max_iV_i$ 的数，此时它才是真正的随机矩阵，且保持同一个 $\boldsymbol\pi$。
>
> 把「$\boldsymbol\pi Q=0$ 与 PageRank（网页排名）对应」读精确一点：PageRank 的平稳分布属于带 damping（阻尼）的离散链，连续对应必须在 $Q$ 上再加一条恒定 restart（重启）速率；$\boldsymbol\pi Q=\mathbf 0$ 本身没有这一项，两者只在加了重启的生成元上对齐。
>
> 收束：这一节真正要带走的是三件事——平衡方程是「次数守恒」，$\boldsymbol\pi$ 坐在左边、常向量坐在右边，以及 $Q$ 不是概率矩阵。三件事各自对应一类常见错误：守恒对象搞错会算错量纲，左右搞反会解出假向量，拿 $Q$ 当 $P$ 会让矩阵幂发散。

现在我们即可对链 $Z_n$ 援引稳态收敛定理（Steady-State Convergence Theorem），得到如下结论。

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**Steady-State Convergence Theorem（稳态收敛定理）**</span>

考虑具有唯一常返类的连续时间马尔可夫链。那么，各状态 $j$ 与满足如下性质的稳态概率 $\pi_j$ 相关联：

> <span style="color:#7f8c8d;">本节定理的 1)、2)、3) 三条性质随翻页续至下一页（本页止于此定理引入句）。</span>

<!-- ===== end of PDF p384 ===== -->
<!-- ===== PDF p385 ===== -->
<span style="color:#c0392b;">**§7.5　连续时间马尔可夫链（Continuous-Time Markov Chains）** — 稳态行为（steady-state behavior）续</span>

> <span style="color:#7f8c8d;">承接上一页：本页开头继续上一页已开始的稳态收敛定理（其编号与开头陈述位于上一页，OCR 未捕捉到编号），随后以正文例题 7.14 验证平衡方程（balance equations）与归一化方程（normalization equations）。页末转入嵌入式马尔可夫链（embedded Markov chain）$X_n$ 的平衡分析，句子在换页处中断，续至下一页。</span>

<span style="color:#2471a3;">**[theorem]**</span> <span style="color:#00838f;">**[定理]（续）**</span> 连续时间马尔可夫链的稳态收敛

(a) 对每个状态 $j$，有

```math
\lim_{t \to \infty} p\left(X(t) = j \mid X(0) = i\right) = \pi_j ,
```

对所有 $i$ 成立。

(b) 这些稳态概率 $\pi_j$ 是下列方程组的唯一解（unique solution），$j = 1, \ldots, m$：

```math
\pi_j \sum_{k \neq j} q_{jk} = \sum_{k \neq j} \pi_k\, q_{kj}, \qquad j = 1, \ldots, m,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 本页 (b) 中「唯一解的方程组」与归一化方程 $\sum_j \pi_j = 1$ 的完整排版式被 OCR 打散（原文 p.376 该行平衡方程系数排样残缺，仅残余碎片 `j = 1, …, m` 范围标注）。上方平衡方程依据本页紧随其后的「平衡方程解读」段落中所明确给出的左右两项 $\pi_j \sum_{k\neq j} q_{jk}$ 与 $\sum_{k\neq j} \pi_k q_{kj}$ 还原；归一化方程亦由后文「balance and normalization equations」佐证。若需最严格原文，请回查原书页 376。</span>

(c) 我们有

```math
\pi_j = 0, \quad \text{对所有暂态状态（transient states） } j, \qquad
\pi_j > 0, \quad \text{对所有常返状态（recurrent states） } j .
```

为解读平衡方程，我们把 $\pi_j$ 视为过程处于状态 $j$ 的期望长期时间占比（expected long-term fraction of time）。由此可知，$\pi_k q_{kj}$ 可视为从 $k$ 到 $j$ 转移的期望频率（expected frequency of transitions from $k$ to $j$），即单位时间内从 $k$ 转移到 $j$ 的期望转移次数（expected number of transitions from $k$ to $j$ per unit time）。因此可见，平衡方程表达了如下直观事实：离开状态 $j$ 的转移频率（左边项 $\pi_j \sum_{k \neq j} q_{jk}$）等于进入状态 $j$ 的转移频率（右边项 $\sum_{k \neq j} \pi_k q_{kj}$）。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 7.14（续）**</span> 本例承接上一页的连续时间链实例。其平衡方程与归一化方程为

```math
\pi_1 + \pi_2 + \pi_3 = 1,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 例 7.14 的完整平衡方程组（各状态的 $\sum \pi_k q_{kj}$ 与 $\sum q_{jk}$ 项）在本页 OCR 中残缺，未能完整捕捉（仅残余归一化片断 `π₁ + π₂ + π₃ =`）。按文意此处为上式的平衡方程加归一化方程；严格原式请回查原书页 376。</span>

与离散时间情形类似，其中一个方程是冗余的（redundant），例如第三个方程可由前两个方程推出。尽管如此，仍存在唯一解：

```math
\pi_1 = \frac{30}{41}, \qquad \pi_2 = \frac{6}{41}, \qquad \pi_3 = \frac{5}{41}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 上式中 $\pi_1 = 30/41$ 与 $\pi_2 = 6/41$ 直接见于 OCR；$\pi_3 = 5/41$ 在原文排版中残缺，系由归一化方程 $1 = 41/41$ 减去前两者（$41/41 - 30/41 - 6/41 = 5/41$）按归一化推导而得，原文数值请以原书页 376 为准。</span>

于是，例如若让此过程长时间运行，$X(t)$ 将以概率 $30/41$ 处于状态 1，与初始状态无关。

稳态概率 $\pi_j$ 须与嵌入式马尔可夫链（embedded Markov chain）$X_n$ 的稳态概率 $\pi'_j$ 相区分。确实，嵌入式马尔可夫链的平衡方程与归一化方程为

> 页面在此处结束，该句承接待推导的嵌入式链方程，续至下一页。
<!-- ===== PDF p386 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span> — <span style="color:#c0392b;">**§7.5 连续时间马尔可夫链（Continuous-Time Markov Chains）（续）**</span>

（本页为上一页内容的延续：开篇先收尾上一示例——给出稳态转移频率 $\pi_i'$ 的解及与稳态概率 $\pi_i$ 的对比；随后新起子节「生灭过程（Birth-Death Processes）」；最后续接 Example 7.15。）

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**上一页示例的收尾（续）——稳态转移频率（transition frequencies）$\pi_i'$ 的解及解读**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页页首承接上一页，示例编号在本页 OCR 中未捕获（页首仅见 "yielding the solution …"，依后文 "Note that even though $\pi_1'=\pi_2'$ … $\pi_1>\pi_2$" 与紧随的 Example 7.15 判断，此收尾段应为前一编号的示例（很可能为 Example 7.14）。若需严格例号，请回查原书页 376。</span>

解得（yielding the solution）：

```math
\pi_1' = \frac{2}{5}, \qquad \pi_2' = \frac{2}{5}, \qquad \pi_3' = \frac{1}{5}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中 $\pi_1'$、$\pi_2'$ 的分母 $5$ 及分子 $2$ 在读页中可辨（见 "$2 = 5$"），故写为 $2/5$；而 $\pi_3'$ 处 OCR 仅剩下划线残片（"11\"3 = 5'  … 2 / 1 / "），其取值 $1/5$ 是按三状态之和归一化为 $1$（且 $\pi_1'=\pi_2'$）反推补全，并非原页直接可见，请以原书为准。</span>

要解读这些概率 $\pi_i'$，我们可举例说明：若让过程长时间运行，那么在全部转移里转移到状态 1 的转移数所占的期望比例等于 $2/5$。
注意，尽管 $\pi_1' = \pi_2'$（即转入状态 1 的转移数与转入状态 2 的转移数大致一样多），我们却有 $\pi_1 > \pi_2$。其原因在于，过程在状态 1 中一次典型驻留所花费的时间，要多于在状态 2 中一次典型驻留所花费的时间。因此，在给定时刻 $t$，过程 $X(t)$ 更可能停留在状态 1。这种情况是典型的，两组稳态概率（$\pi_i$ 与 $\pi_i'$）一般而言是不同的。主要的例外出现在特殊情形：即当所有 $i$ 的转移速率（transition rate）$\nu_i$ 都相同时；参见章末习题。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> <span style="color:#1e8449">[note] Note（译者注）:</span> 这里给出的两组数是全章最锋利的一处对照：steady-state probability（稳态概率）$\pi=(30/41,6/41,5/41)$，而 embedded Markov chain（嵌入马尔可夫链）的 steady-state probability（稳态概率）$\pi'=(2/5,2/5,1/5)$。前两个分量在第二组里相等，在第一组里却相差五倍。凡把「转进某状态的次数」与「某状态占用的时间」混为一谈的人，都会在这里栽跟头，而这两个量偏偏都叫「稳态」。
>
> 第一性原理只有一句：这是两把独立标尺。$\pi'_i$ 量的是「多少次转移落到 $i$」，分母是转移总数；$\pi_i$ 量的是「长时间里钟表停在 $i$ 的比例」，分母是总时间。把前者换成后者必须乘上「单次驻留有多长」——exponential distribution（指数分布）给的平均驻留时间是 $1/V_i$——于是两者之间夹着一个速率因子，方向是除以 $V_i$：走得快的状态，同样多的到达次数换来的时间少，占比自然更低。
>
> 写成精确关系是 $\pi_iV_i=C\pi'_i$，其中 $C=\sum_k\pi_kV_k$ 是平均转移速率。左端 $\pi_iV_i$ 是「单位时间内从 $i$ 出发的转移次数」，右端 $C\pi'_i$ 是「单位时间内到达 $i$ 的次数」，稳态下两者必相等，因为每一次离开都对应某一次到达。这条恒等式顺手给出反解 $\pi\propto V^{-1}\pi'$，$V$ 是速率对角矩阵；本题 $C=75/41$，约等于每秒一点八三次转移。
>
> 把三个状态逐个代进去验，一个都不能漏。状态一：$\pi_1V_1=30/41$，$C\pi'_1=(75/41)(2/5)=30/41$。状态二：$\pi_2V_2=(6/41)(5)=30/41$，$C\pi'_2=(75/41)(2/5)=30/41$。状态三：$\pi_3V_3=(5/41)(3)=15/41$，$C\pi'_3=(75/41)(1/5)=15/41$。三对数字全部咬合，说明两条算路指向同一个量。
>
> 顺带读出 $\pi_1/\pi_2=V_2/V_1=5$：两者频次相等，占用时间之比就等于速率之反比。这正是正文那句「状态一的驻留更长」的定量版——状态一平均待 $1$ 秒，状态二平均待 $0.2$ 秒，五倍的差距直接写在时间占比里。
>
> 矩阵来源在线性代数（18.06）里一句话讲清。$Q=V(P-I)$（嵌入链无自环时成立），代入 $\boldsymbol\pi Q=\mathbf 0$ 得 $\boldsymbol\pi VP=\boldsymbol\pi V$。也就是说 $\boldsymbol\pi V$ 是 $P$ 关于特征值 $1$ 的左特征向量，与嵌入链的平凡分布只差一个归一化常数；两条链的稳态通过 $V$ 相互变换，谁也不能单独当另一个用。这一步的价值在于把「时间」与「次数」的换算压成一个相似变换，而不是一个要背的经验公式。
>
> 同一件事还有 uniformization（均匀化）这个说法：取 $\gamma$ 不小于 $\max_iV_i$，令 $P^{\ast}=I+Q/\gamma$ 成为真正的随机矩阵，则 $\boldsymbol\pi P^{\ast}=\boldsymbol\pi$ 依然成立，连续链的每一条轨迹都能看成速率为 $\gamma$ 的 Poisson process（泊松过程）驱动的离散链。这个 1953 年由 Jensen 给出的构造，把连续链的瞬态计算全部转成离散矩阵幂。
>
> 排队论里这两个量的分工很具体：$\pi_i$ 是服务器占用率，$\pi'_i$ 是「完成一次作业后，下一个作业落在哪一类」的频次；Little's law（利特尔定律）$L=\lambda W$ 同样在「次数乘时间」这个换算上做文章。工程上要算吞吐就乘 $\pi'$，要算资源占用就取 $\pi$，混用会系统性偏袒快状态。
>
> 两处要收紧。原注说「当且仅当 $V_i$ 全相等时两套稳态合体」，精确条件是「在 $\pi'$ 的支撑集上 $V_i$ 相同」——某状态若从不被访问，它的速率取值无关紧要。另一处是更常见的误用：拿转移频次当占用率会系统性偏袒快状态。本题里 $\pi'_1=0.4$ 而 $\pi_1=0.7317$，低估将近一半；反之若把 $\pi$ 当频次，会高估慢状态的到达次数，据此算出的拒绝率整体跑偏，且偏的方向与速率分布相关，不是随机误差。

---

<span style="color:#c0392b;">**生灭过程（Birth-Death Processes）**</span>

与离散时间情形一样（as in the discrete-time case），生灭过程（birth-death process）中的状态按线性方式排列，转移只能发生在相邻状态之间，否则保持状态不变；形式化地说，我们有

```math
q_{ij} = 0, \qquad \text{对 } |i - j| > 1 \text{ 成立}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上行的下标条件在本页 OCR 中被截断（仅见 "qij = 0, for [ ] > 1"），现按标准生灭过程定义补全为 $|i-j|>1$。</span>

在生灭过程中，从 $i$ 转移到 $j$ 的长期期望频率与从 $j$ 转移到 $i$ 的长期期望频率必须相同，由此导出局部平衡方程（local balance equations）：

```math
\pi_i q_{ij} = \pi_j q_{ji}, \qquad \text{对所有 } i, j \text{ 成立}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页局部平衡方程的具体式形被 OCR 打散（仅存 "local balance equations … i … for all i, j"），此处按标准形式补全为 $\pi_i q_{ij} = \pi_j q_{ji}$，请以原书为准。</span>

局部平衡方程与离散时间情形具有相同的结构，从而导出稳态概率的闭式公式（closed-form formulas）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> birth-death process（生灭过程）的定义只有一条：$q_{ij}=0$ 对 $|i-j|>1$ 成立。这一条窄得几乎像废话，却把整组 balance equation（平衡方程）从「每个状态与其余全部状态耦合」压成「每个状态只与左右两个邻居耦合」，于是求和式里只剩两项，整组方程退化为逐边的 local balance equation（局部平衡方程）$\pi_iq_{ij}=\pi_jq_{ji}$。关键在于：这是推出来的，不是另立的公理。
>
> 机制是一个 cut（割）的论证。把状态集沿 $i$ 与 $i+1$ 之间切成左右两半，考察跨过这条割的流：稳态下左半的概率质量既不能无界增长也不能枯竭，故单位时间从左跨到右的次数必须等于从右跨到左的次数。生灭结构让「跨割」只剩一条通道，这条通道上双向流量相等，正是 $\pi_iq_{i,i+1}=\pi_{i+1}q_{i+1,i}$。换个说法：稳态在图上是一个 divergence-free（无散度）的流场，而每一层割只有一条通道，通道上的流量被迫处处相同。
>
> 递推与闭式随之滚出：把逐边等式改写成 $\pi_{i+1}=\pi_i\cdot(q_{i,i+1}/q_{i+1,i})$，从 $\pi_0$ 一路乘上去得 $\pi_i=\pi_0\prod_{k<i}(q_{k,k+1}/q_{k+1,k})$，再由 normalization（归一化）定 $\pi_0$。手算一个三状态例：出生率取 $1$ 与 $3$，死亡率取 $2$ 与 $1$，则 $\pi_1=\pi_0\cdot(1/2)=\pi_0/2$，$\pi_2=\pi_1\cdot(3/1)=3\pi_0/2$，归一化给 $\pi_0(1+0.5+1.5)=3\pi_0=1$，故 $\pi_0=1/3$，$\pi=(1/3,1/6,1/2)$。回头验一条边：左端 $\pi_0\cdot1=1/3$，右端 $\pi_1\cdot2=1/3$，咬合；另一条边同理得 $1/2$ 对 $1/2$。
>
> 这条递推的价值容易被低估：直接解 $m$ 元线性方程组要走高斯消元，代价随维数立方增长，而逐边相乘只需一次线性遍历，$\pi$ 的几何型结构也一眼可见。代价是这套便利只对生灭结构成立，跨出这个结构就要退回全局方程组。换句话说，模型结构换来的是算法复杂度上的实打实折扣，不只是书写上的省事。
>
> 18.06 的读法能解释这个结构为什么好用。令 $\Pi$ 为以 $\pi_i$ 为对角元的矩阵，逐边等式等价于 $\Pi Q$ 为对称矩阵，这种链叫 reversible（可逆）的，也说它满足 detailed balance（细致平衡）。可逆性的后果立刻兑现：$Q$ 相似于对称矩阵，特征值全为实数、特征向量可正交归一、谱隙有 Rayleigh quotient（瑞利商）型的变分刻画，$I-Q$ 的正定性也能从变分式读出。Strang 讲对称矩阵与正定矩阵的那一章，在这里变成「生灭链天生好解」的真正理由——不是运气，是对称性。
>
> 跨课程的结构对应至少三处。电阻网络里把 $\pi_i$ 当电势、$q_{ij}$ 当电导，逐边等式就是欧姆定律加 Kirchhoff 电流定律，全局平衡是节点电流守恒，局部平衡是「每条支路上电流处处相同」的特殊情形；化学动力学里的细致平衡出自 Boltzmann，说的是平衡时正逆反应速率相等；Markov chain Monte Carlo（马尔可夫链蒙特卡洛，MCMC）里 Metropolis–Hastings 的接受率正是被设计成满足细致平衡，从而让目标分布成为平稳分布。三处用的是同一句「逐边守恒」。
>
> 反例最能校正直觉。取三状态确定性环：$a\to b$、$b\to c$、$c\to a$ 各速率 $1$，反向速率全为 $0$。它满足全局平衡，$\boldsymbol\pi=(1/3,1/3,1/3)$ 对每个状态进出相抵；但它不满足逐边平衡，因为 $\pi_aq_{ab}=1/3$ 而 $\pi_bq_{ba}=0$。可见使局部平衡失效的不是「跳得远」，而是存在 non-zero circulation（非零环流）。以 Kolmogorov 命名的循环判据给出充要条件：沿任一闭环正反两方向的速率乘积相等；生灭链没有环，所以自动过关。
>
> 收束：生灭结构把一个「$m$ 元线性系统」换成「$m$ 次乘法」，代价是把适用面缩到一条线；这条线的边界由「有无环流」划定，而不是由状态数或图形美观决定。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 7.15（生灭过程/有限容量排队示例，续）**</span>

局部平衡方程取如下形式：

```math
\pi_i \lambda = \pi_{i+1} \mu, \qquad i = 0, 1, \ldots, m - 1,
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页局部平衡方程的具体表达在此处 OCR 中被截断（仅存 "i = 0, 1, ..., m - 1"），此处按后文 $\pi_{i+1} = \rho\,\pi_i$、$\rho = \lambda/\mu$ 反推补全为 $\pi_i \lambda = \pi_{i+1} \mu$，请以原书为准。</span>

并得到 $\pi_{i+1} = \rho\,\pi_i$，其中 $\rho = \lambda / \mu$。于是，对所有 $i$ 都有 $\pi_i = \rho^i \pi_0$。归一化方程（normalization equation）$1 = \sum_{i=0}^{m} \pi_i$ 给出：

```math
1 = \pi_0 \sum_{i=0}^{m} \rho^i,
```

从而稳态概率（steady-state probabilities）为：

```math
\pi_i = \frac{\rho^i}{1 + \rho + \cdots + \rho^{m}}, \qquad i = 0, 1, \ldots, m .
```
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 正文 Example 7.15 把一个通信节点排成 birth-death process（生灭过程）：状态是队列里现有的任务数，从 $0$ 到 $m$ 共 $m+1$ 个，到达速率 $\lambda$、服务速率 $\mu$，队满时新到的任务被丢弃。local balance（局部平衡）给出 $\pi_i\lambda=\pi_{i+1}\mu$，于是 $\pi_{i+1}=\rho\pi_i$（$\rho=\lambda/\mu$）；归一化 $\sum_{i=0}^{m}\pi_i=1$ 的分母是一段几何和，闭式即 $\pi_i=\rho^{i}(1-\rho)/(1-\rho^{m+1})$。
>
> 第一性原理只用一个词：无记忆。Poisson process（泊松过程）让「下一个任务何时来」与队列长短无关，指数服务让「这一单还差多久」与服务过多久无关；两条无记忆合起来才保证「状态等于任务数」是充分的——若服务时间有记忆，任务数就不够，还必须记住每个任务已经服务了多久。归一化之所以能写成有限和，全靠容量封顶。
>
> 代 $m=3$、$\rho=1/2$ 手算一遍。分母是 $1+1/2+1/4+1/8=15/8$，故 $\pi=(8/15,4/15,2/15,1/15)$。期望队长 $L=\sum_i i\pi_i=(4+4+3)/15=11/15$；队满概率 $\pi_3=1/15$ 就是 blocking probability（阻塞概率）；有效到达率 $\lambda_{\mathrm{eff}}=\lambda(1-\pi_3)=(14/15)\lambda$；取 $\mu=1$，由 Little's law（利特尔定律）$L=\lambda_{\mathrm{eff}}W$ 得平均逗留 $W=(11/15)/(7/15)=11/7$，比纯服务时间 $1$ 多出 $4/7$，多出来的正是排队时间。
>
> 这里要纠正一处流传很广的误认：$\pi_m$ 可以叫 blocking probability（阻塞概率），但它不是 Erlang B 公式给出的那个量。Erlang B 描述的是 loss system（损失制系统）M/M/c/c——$c$ 条并行线路、没有排队缓冲、到达时全忙即被拒；本题是 M/M/1/m——一个服务器加 $m-1$ 个等待位。两者数值不同：$m=3$、$\rho=0.5$ 时本题 $\pi_3=1/15\approx0.0667$，而 Erlang B 在 $c=3$、负载 $a=0.5$ 时给出 $0.01266$，差五倍多。只有 $m=1$ 时两者巧合相等（都是 $0.3333$），因为 M/M/1/1 恰好就是一个单服务器损失制系统——这个巧合正是误解的来源。
>
> 两个极限值值得单独记住。$\rho\to1$ 时几何和等于 $m+1$，$\pi_i\to1/(m+1)$，分布变均匀，阻塞率约 $1/(m+1)$；固定 $\rho<1$ 让 $m\to\infty$，分母收敛到 $1/(1-\rho)$，于是 $\pi_i\to(1-\rho)\rho^{i}$，无限容量的 M/M/1 稳态重现。$\rho\ge1$ 时无上限系统没有稳态：$\rho=1$ 是零常返，$\rho>1$ 是暂态，概率质量持续逃向无穷。
>
> 还有一处必须纠正的定量说法：容量 $m$ 变大时 spectral gap（谱隙）并不按 $m$ 的平方分之一缩小。固定 $\rho<1$，谱隙单调下降但有正极限 $(\sqrt\mu-\sqrt\lambda)^{2}$；取 $\mu=1$、$\lambda=0.5$，极限是 $(1-0.7071)^{2}\approx0.0858$，数值上 $m=3$ 时谱隙 $0.5$、$m=20$ 时 $0.1016$、$m=100$ 时 $0.0865$，而 $\text{gap}\cdot m^{2}$ 从 $4.5$ 一路涨到 $864.6$——若真按 $1/m^{2}$ 缩，$m=100$ 时应是 $5\times10^{-5}$ 量级，实际大了四个数量级。
>
> 只有临界情形 $\rho=1$ 才出现扩散标度：此时谱隙确实约等于 $\pi^{2}/m^{2}$，$m=100$ 时实测 $9.67\times10^{-4}$，而 $\pi^{2}/m^{2}=9.87\times10^{-4}$。所以「容量换稳定性」的汇率分两段：$\rho<1$ 时有上界，恢复时间不超过约 $11.7$ 个时间单位；$\rho=1$ 时才按平方增长。把两段混成一条结论，就会把一个有界的量说成随 $m$ 无界增长。
>
> 反例集中在三处。其一，把 $\pi_0=1-\rho$ 硬套到有限容量：这只在 $m=\infty$ 时成立，有限时要除以几何和，直接代会让概率之和偏离 $1$。其二，用 $\lambda$ 而不是 $\lambda_{\mathrm{eff}}$ 套 Little's law（利特尔定律），队长会被系统性高估，被丢弃的那部分到达根本没进入系统。其三，把 $\pi_m$ 理解成「服务被拒绝」——被拒绝的是到达，服务本身从未被拒，所以 $\pi_m$ 该乘在到达率上。
>
> 线性代数（18.06）的视角补一句：生成元 $Q$ 是三对角矩阵，可经对角相似变成对称三对角，故特征值全实、可正交归一；最大特征值 $0$ 对应稳态，第二大特征值的绝对值就是谱隙。Strang 讲三对角与特征值的那一节在这里直接用得上，也解释了为什么生死链的谱型总能画成一条整齐的实数轴。
<!-- ===== PDF p387 ===== -->
<span style="color:#c0392b;">**7.6　小结与讨论（Summary and Discussion）**</span>

在本章中，我们引入了具有**有限个状态**的马尔可夫链模型（Markov chain models with a finite number of states）。在离散时间马尔可夫链（discrete-time Markov chain）中，转移（transition）发生在整数时刻，遵循给定的转移概率（transition probabilities）$p_{ij}$。将马尔可夫链与一般随机过程（general random processes）区分开来的关键性质在于：每当状态等于某个 $i$ 时，转移概率 $p_{ij}$ 都会适用，而与状态在此前的任何取值无关。因此，在给定当前（present）状态的前提下，过程的未来与过去相独立（independent of the past）。

为一个给定的物理情形构想合适的马尔可夫链模型，在某种程度上是一门艺术。一般来说，我们需要引入一组足够丰富的状态（states），使得当前状态（current state）能够概括过程历史中所有与其未来演化相关的信息。在满足这一要求的前提下，我们通常倾向于采用一个不包含多余状态的简单模型。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一小节用两段话收口整章，真正要紧的是那句「在某种程度上是一门艺术」。把它翻译成可检验的判据只有一句：state（状态）必须是未来的 sufficient statistic（充分统计量），而且在满足这一点的前提下要取最精简的那个。前一半是马尔可夫性的要求，后一半是计算可行性的要求。
>
> 第一性原理要把「足够」与「不冗余」拆开。足够，指当前状态对未来条件分布所承载的信息与原整段历史完全一样——不满足这条，过程立刻失去 Markov property（马尔可夫性质）；不冗余，指在满足足够的那些划分里取最粗的那个，也就是统计学里 minimal sufficient statistic（最小充分统计量）的同一个要求，只是这里的「统计量」是从历史到状态空间的映射，而不是从样本到参数的映射。两句话方向相反，取舍的张力全在中间。
>
> 张力的定量版本是两条误差曲线。状态太少，记忆被丢掉，模型失配，稳态分布与真实物理之间出现系统性偏差，而且偏差不随观察变长而缩小；状态太多，矩阵阶数上升，求平稳分布要解特征问题、求首达时间要解线性方程组，代价随阶数立方增长，仿真每一步的内存也要按阶数铺开。工程上要找的是两条曲线的交点，不是某一端的极值。
>
> 18.06 的语言让这件事更清楚：设计状态就是设计矩阵。状态数定了矩阵阶数，矩阵的谱定了收敛速度，收敛速度决定你在仿真里要跑多久才算看见稳态。这里有一条反直觉结论——加状态不一定让收敛更快：有限容量队列把容量加大，谱隙从 $0.5$ 降到 $0.0865$（$m$ 从 $3$ 到 $100$，$\rho=0.5$ 时实测），恢复时间反而变长。所以「模型更精细」与「计算更便宜」并不总是同向。
>
> 跨课程至少三处结构对应。CSAPP 里的抽象机器只暴露寄存器与内存，因为那正是「下一步行为所需信息的全部」，其余历史封进文件系统或直接丢弃，与状态封装历史是同一句断言；CLRS 里的动态规划先声明状态再写递推，Bellman 方程就是 first-step analysis（第一步分析）的优化版本，状态设计错了两件事一起错；6.042J 的等价关系与商集给出纯逻辑版本——先定义「不可分辨」，再把不可分辨的元素并成一个对象，马尔可夫链不过是在随机过程上执行这一次并类。
>
> 具体算一个可合并的例子，让判据落地。四状态链，把状态分成 $A=\{1,2\}$、$B=\{3,4\}$。从 $1$ 出发的一步分布是 $(0.2,0.3,0.3,0.2)$，跨进 $B$ 的概率 $0.5$；从 $2$ 出发是 $(0.4,0.1,0.2,0.3)$，跨进 $B$ 也是 $0.5$，判据在这一块通过。再看 $B$：从 $3$ 出发跨进 $A$ 是 $0.1+0.2=0.3$，从 $4$ 出发是 $0.2+0.1=0.3$，同样通过。于是粗链的两行是 $(0.5,0.5)$ 与 $(0.3,0.7)$，它的平稳分布解出来是 $(3/8,5/8)$，$0.5\times3/8=0.3\times5/8$ 正好对账。
>
> 反例有两个方向。Problem 2 把走廊折叠成左右两个信号、Problem 3 把四状态并成两状态，都因为桶内各点「跨进目标块的转移概率之和」不相等而失败，历史从粗标签里漏了出去；另一个方向是把整段历史都装进状态，链确实是马尔可夫的，但状态空间无限，方程根本写不出来。
>
> 要纠正的是「艺术即凭感觉」这个印象：Kemeny 与 Snell 在 1960 年的《Finite Markov Chains》里给出明确判据——一个划分可 lumpable（可合并），当且仅当对每个源块 $A$ 与目标块 $B$，$\sum_{j\in B}p_{ij}$ 不随 $i\in A$ 变化。所以「精简」不是审美判断，而是可以逐块逐列验算的命题；上面那个四状态例就是照着这条式子算出来的。
>
> 收束：状态设计的两条命令——带上一切未来需要的信息，别的都别带——前者由马尔可夫性强制，后者由计算代价强制。判据可以验算，模型才算工程而不是玄学。

给定一个马尔可夫链模型，有若干值得关注的问题。

(a) **关于过程在有限时域（finite time horizon）内统计量的问题。** 我们已经看到，可以通过把沿某条特定路径的转移概率相乘，来计算过程沿这条路径前进的概率。更一般事件的概率则可通过对导致该事件发生的各条路径的概率求和而得到。在某些情形下，我们可以利用马尔可夫性质（Markov property）来避免逐一列出对应于某个特定事件的每一条路径。一个突出的例子是利用 Chapman–Kolmogorov 方程递归地计算 n 步转移概率（n-step transition probabilities）。

(b) **关于马尔可夫链稳态行为（steady-state behavior）的问题。** 为处理此类问题，我们将马尔可夫链的状态区分为暂态（transient）和常返（recurrent）。我们讨论了常返状态如何被划分为互不相交的常返类（recurrent classes），使得某个常返类中的每个状态都能由此类中的任意其他状态到达（accessible）。我们还区分了周期的与非周期的常返类。马尔可夫链理论的**核心结果**是：如果某条链由单独一个非周期常返类加上可能的一些暂态状态构成，那么状态等于某个 $j$ 的概率会随时间趋于无穷而收敛到某个稳态概率（steady-state probabilities）$\pi_j$，且该稳态概率不依赖于初始状态 $i$。换言之，当 $n$ 很大时，初始状态的身份对 $X_n$ 的统计量没有任何影响。稳态概率可以通过求解一个线性方程组而得到，该方程组由平衡方程组（balance equations）与归一化方程（normalization equation）$\sum_j \pi_j = 1$ 构成。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本段末两句中，「the probability …converges to a steady-state probability $\pi_j$」的原文符号在 OCR 中残缺：式中下标写为「Tij(n)」、稳态符号写为「7rj」、归一化式写为「Ej 7rj = 1」。均按第 7 章标准记号还原为 n 步转移概率与 $\pi_j$（违反 $\sum_j \pi_j=1$ 处原文为 OCR 数字 7 + 残缺符号）。若需严格逐一字符，请回查原书 p387。</span>

(c) **关于马尔可夫链暂态行为（transient behavior）的问题。** 我们讨论了吸收概率（absorption probabilities），即在初始处于某个给定暂态状态的条件下，状态最终进入某个给定常返类的概率；以及平均首达时间（mean first passage times），即在假定该链只有一个常返…

> <span style="color:#7f8c8d;">[原页此处 OCR 到手为止，正文随后于第四段 (c) 即被换页截断于「assuming that the chain has a single recurrent …」，句子后续（「class」及之后）续于下一页 PDF p388。</span>
<!-- ===== PDF p388 ===== -->
<span style="color:#c0392b;">**§7.6　小结与讨论（Summary and Discussion）（续）**</span>

> <span style="color:#7f8c8d;">承接上一页：本页延续 §7.6 的小结讨论正文，页首无新标题，为上一页文字中间的中部续接（首句「class）」为承接上文对各类（class）讨论的收尾片段）。本页为 §7.6 结束语，随后进入章末习题区。</span>

……类（class）。在两种情形下，我们都说明了：所关心的量都可以通过考察一个线性方程组（system of linear equations）的唯一解来求得。

我们最后考虑连续时间马尔可夫链（continuous-time Markov chains）。在这类模型中，给定当前状态（current state）之后，下一个状态由与离散时间马尔可夫链（discrete-time Markov chains）相同的机制来确定。然而，直到下一次转移（transition）所经历的时间是一个服从指数分布（exponentially distributed）的随机变量（random variable），其参数仅取决于当前状态。连续时间马尔可夫链在很多方面与其离散时间情形（discrete-time counterparts）相似。它们具有同样的马尔可夫性（Markov property），即在给定当前（present）的条件下，未来（future）与过去（past）相互独立。事实上，我们可以借助一条通过对时间轴进行细密离散化（fine discretization）而得到的相关离散时间马尔可夫链，来对一条连续时间马尔可夫链加以可视化。正是由于这种对应关系（correspondence），连续时间与离散时间马尔可夫链的稳态行为（steady-state behaviors）是相似的：假定存在唯一的常返类（single recurrent class），则任意特定状态的占用概率（occupancy probability）都会收敛到某一稳态概率（steady-state probability），该概率不依赖于初始状态。这些稳态概率可以通过求解一组适当的平衡与归一化方程（balance and normalization equations）来得到。
<!-- ===== PDF p389 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — 习题区开始（PROBLEMS）

> <span style="color:#7f8c8d;">本页为第 7 章章末 Problems 习题区的开头（书内页码 380），其下为按小节分组的习题。页首出现「PROBLEMS」，故本节为习题区起始，非正文延续。习题题干按规范保持英文原题。</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">SECTION 7.1　离散时间马尔可夫链（Discrete-Time Markov Chains）</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 1.**（顾客到达间隔时间，构造四状态马尔可夫链）</span>

The times between successive customer arrivals at a facility are independent and identically distributed random variables with the following PMF:

```math
p(k) =
\begin{cases}
0.2, & k = 1,\\
0.3, & k = 3,\\
0.5, & k = 4,\\
0, & \text{otherwise}.
\end{cases}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页 PMF 式被 OCR 打散（碎行含「k=1」「0.3 k=3」「0.5, k=4」「otherwise」「0」「{ 0.2,」），且存在一个孤立逗号疑似 OCR 多出的 k=2 残留。按出现在原文的数值 0.2 / 0.3 / 0.5 且三者之和恰为 1，上式将取值还原为 k=1、k=3、k=4 的分段（原书该题即此 PMF）。若需最严格原文请回查原书页 380。</span>

Construct a four-state Markov chain model that describes the arrival process. In this model, one of the states should correspond to the times when an arrival occurs.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 1 的 PMF（概率质量函数）只有三个取值：间隔 $1$ 的概率 $0.2$、$3$ 的概率 $0.3$、$4$ 的概率 $0.5$。要点不在算数，而在要求你构造一个四状态模型，并且指定其中一个状态专门表示「顾客恰好在这一步到达」。四个状态这个数字本身就是提示：三个取值不需要三个状态，反而需要四个。
>
> 为什么三个状态不够，道理在 memorylessness（无记忆性）。间隔分布若是指数或几何，剩余等待时间与已等多久无关，一个状态就能装下全部记忆；而这里的间隔只取 $1$、$3$、$4$，既不几何也不同分布，剩余等待就成了必须被记录的量，它可能取 $1$、$2$、$3$、$4$ 四个值——间隔取 $4$ 时倒计时要经过 $3$、$2$、$1$ 三档，间隔取 $3$ 时经过 $2$、$1$ 两档，于是状态集必须是四个。
>
> 一种合法构造（不是唯一）：令状态 $r$ 表示「距下次到达还需 $r$ 步，含到达那一步本身」。状态 $1$ 就是到达发生的时刻，从它出发按间隔分布跳到下次的倒计时：到 $1$ 的概率 $0.2$、到 $3$ 的概率 $0.3$、到 $4$ 的概率 $0.5$。其余三个状态是确定性递减：$2\to1$、$3\to2$、$4\to3$，概率都是 $1$。四行写下来，每行之和为 $1$，transition matrix（转移矩阵）就齐了。
>
> 验证马尔可夫性只需看一件事：给定当前 $r$，下一步的分布是否唯一确定。逐行检查，每一行的转移分布只由本行决定，与「上一步从哪个状态跳来」无关；递减那三行尤其干脆，它们根本不看历史，只看还剩几步。历史中所有与未来有关的信息，只剩「还剩几步」这一个整数——这就是 sufficient statistic（充分统计量）的字面意思。
>
> 用 renewal（更新）理论做独立交叉验证。平均间隔 $0.2\cdot1+0.3\cdot3+0.5\cdot4=3.1=31/10$，于是「某一步恰好是到达步」的长期比例为 $10/31$。解 $\pi P=\pi$ 与归一化，得 $\pi_1=10/31$、$\pi_2=\pi_3=8/31$、$\pi_4=5/31$，与更新论证一致。再换个角度对账：每个周期里倒计时停在状态 $2$ 的步数恒为 $1$（只要间隔不小于 $2$），其期望 $0.8$，除以平均周期长 $3.1$ 得 $8/31$；状态 $4$ 的出现率则只有间隔取 $4$ 的那些周期贡献，$0.5/3.1=5/31$。
>
> 这类构造的学名是 phase-type（相位型）分布，想法在 1955 年由 D. R. Cox 以 method of stages（分阶段法）提出。这里的适用范围要说准：有限支撑的分布一定可以用有限状态链实现（本题就是），更一般地，能被写成「有限个几何变量之和的有限混合」的分布都叫 discrete phase-type（离散相位型），它们都可以用有限状态的吸收时刻表示；但并非任意正整数值分布都行——无限支撑且生成函数不是有理式的分布，需要可数无穷个状态才能精确实现。
>
> 工程上它对应离散事件模拟里的「下次事件时刻」变量，也对应 CLRS 里事件驱动模拟的那只优先队列——把「还要等多久」显式存成状态，是所有事件驱动系统共同的骨架。18.06 的语言里，这就是把一条长度可变的链拆成若干固定长度的阶段，用一个上三角的转移结构实现任意等待分布。
>
> 反例最能说明必要性。只留两个状态（「这一步到达」与「这一步不到达」），等待期的长度彻底丢失，两行转移矩阵无法区分间隔 $1$ 与间隔 $4$，模型必然失真；反过来把「已经等了几天」也塞进状态，状态数会按最大间隔翻倍。四状态之所以是标准答案，是因为它既是充分的，也是最小的。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 2.**（走廊瓷砖上移动的老鼠，信号 L/R 是否构成马尔可夫链）</span>

A mouse moves along a tiled corridor with $2m$ tiles, where $m > 1$. From each tile $i$, $1 \le i \le 2m$, it moves to either tile $i - 1$ or $i + 1$ with equal probability. From tile $1$ or tile $2m$, it moves to tile $2$ or $2m - 1$, respectively, with probability $1$. Each time the mouse moves to a tile $i \le m$ or $i > m$, an electronic device outputs a signal $L$ or $R$, respectively. Can the generated sequence of signals $L$ and $R$ be described as a Markov chain with states $L$ and $R$?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 2 的场景是走廊上 $2m$ 块瓷砖，老鼠在第 $i$ 块时以各 $1/2$ 的等概率移到 $i-1$ 或 $i+1$，只在两端 $1$ 与 $2m$ 处退化为「撞墙反弹」，以概率 $1$ 移向 $2$ 与 $2m-1$。每当它落进左半（$i\le m$）就发信号 $L$、落进右半就发信号 $R$，问信号序列本身是不是一条马尔可夫链。答案是：不是（对 $m>1$ 而言）。
>
> 判据必须先写清楚，否则容易凭感觉争论。按 Kemeny 与 Snell 在 1960 年给出的 lumpable（可合并）定理，把 state（状态）分成若干块后，粗过程仍是 Markov chain（马尔可夫链），当且仅当对每一对「源块 $A$、目标块 $B$」，块内任一状态一步跨进 $B$ 的概率之和都相同，即 $\sum_{j\in B}p_{ij}$ 不随 $i\in A$ 变化。判据看的是转移概率之和，不是稳态值，也不是图形对称性。
>
> 把左半块 $A=\{1,\dots,m\}$ 代进去，立刻裂开。内部的 $i=2,\dots,m-1$ 两个邻居都在左半，故一步跨进右半的概率是 $0$；$i=1$ 只会跳到 $2$，同样是 $0$；唯独 $i=m$ 有一个邻居是 $m+1$，跨进右半的概率是 $1/2$。同一个块里出现 $0$ 与 $1/2$ 两个值，判据不成立，粗过程不是马尔可夫链。
>
> 右半块以同样的方式失败，只是分裂点换到另一端：$i=m+1$ 跨回左半的概率是 $1/2$，而 $i=m+2,\dots,2m-1$ 与 $i=2m$ 都是 $0$。两块都失败，所以答案是否定的，与初始分布无关。
>
> 题设要求 $m>1$ 正是为了让这个分裂存在。若 $m=1$，两块砖 $1$ 与 $2$ 确定性互跳：$1\to2$、$2\to1$。信号在 $i\le1$ 时取 $L$、在 $i=2$ 时取 $R$，于是信号序列是 $L,R,L,R,\ldots$ 严格交替。这不是「恒为一个值」，而是一条两点周期链——它当然仍是马尔可夫链（给定当前值，下一个值确定）。所以 $m=1$ 时判据自动成立，反例必须靠 $m\ge2$ 才立得住。
>
> 取 $m=3$ 具体化：六块砖，左半是 $1,2,3$。站在 $3$ 有一半机会一步跨到 $4$，站在 $1$ 与 $2$ 则一步也跨不过去，三个起点对同一个目标块给出两个不同的概率，判据当场破碎。
>
> 有意义的做法是换一个划分。这条链对「关于中点的反射」$i\mapsto2m+1-i$ 不变，把对称的两端并成一块：$B_1=\{1,2m\}$、$B_2=\{2,2m-1\}$，直到 $B_m=\{m,m+1\}$，块的含义正是「到最近一端的距离加一」。逐块验：$1$ 与 $2m$ 都以概率 $1$ 进 $B_2$；$2$ 与 $2m-1$ 都以各 $1/2$ 进 $B_1$ 与 $B_3$；中间各块同理对称。这一次判据处处成立，商链是一条在 $m$ 个块上的反射随机游走，稳态为均匀分布 $1/m$。
>
> 18.06 的读法给这套判据一个几何解释。设 $T$ 把粗状态映成块指示向量，$P$ 是细链的转移矩阵；可合并等价于存在粗矩阵 $\bar P$ 使 $PT=T\bar P$。也就是说，块指示向量张成的子空间在 $P$ 的作用下保持闭合，$\bar P$ 不过是这个算子在该子空间上的限制。Strang 讲不变子空间的那一节讲的就是这件事：能不能把大算子限制到小空间，取决于小空间是否被封住。
>
> 两处常见误读。其一，把「折叠后仍有稳态分布」当成马尔可夫性的证据——每个有限链随便怎么折叠都能算出一条概率流的极限分布，问题在于这条极限分布是否由一条马尔可夫链生成；其二，把右半块单独看成「$m+1$ 到 $2m$ 都等价」——它们不等价，$m+1$ 紧贴中线，$2m$ 贴着反弹墙。
>
> 收束：折叠的资格由块内一致性决定，而块内一致性一旦被边界打破，任何事后修补都救不回来；这也解释了为什么题目预先要求 $m>1$——$m=1$ 时边界不存在，反例自动消失。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中「tile $i$，$1 \le i \le 2m$」原 OCR 为「tile i l' 1 , 2m」（下标范围残缺）；「$i \le m$ or $i > m$」原 OCR 为「tile i $ m or i > m」（不等号误识别）。此处按上下文补全，若需最严格原文请回查原书页 380。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中「tile $i$，$1 \le i \le 2m$」原 OCR 为「tile i l' 1 , 2m」（下标范围残缺）；「$i \le m$ or $i > m$」原 OCR 为「tile i $ m or i > m」（不等号误识别）。此处按上下文补全，若需最严格原文请回查原书页 380。</span>

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 3.**（聚集为两态 $Y_n$ 后是否仍为马尔可夫链）</span>

Consider the Markov chain in Example 7.2, for the case where $m = 4$, as in Fig. 7.2, and assume that the process starts at any of the four states, with equal probability. Let $Y_n = 1$ whenever the Markov chain is at state $1$ or $2$, and $Y_n = 2$ whenever the Markov chain is at state $3$ or $4$. Is the process $Y_n$ a Markov chain?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Problem 3 回到 Example 7.2 的蜘蛛与苍蝇：$m=4$ 时四块瓷砖，两端 $1$ 与 $4$ 是 absorbing state（吸收态）（苍蝇被吃掉，$p_{11}=p_{44}=1$），内部状态走到左右各以 $0.3$、原地停留 $0.4$。把状态按 $Y_n=1$ 对应 $\{1,2\}$、$Y_n=2$ 对应 $\{3,4\}$ 折叠成两值，初始四状态等概率，问 $Y_n$ 是不是马尔可夫链。答案是否定的。
>
> 判据还是那条块内一致性：给定 $Y_n=1$，下一步落进 $Y=2$ 的概率必须与「此刻究竟在 $1$ 还是在 $2$」无关。实际算一下：站在 $X=1$ 时是吸收态，一步之后必然还在 $\{1,2\}$ 里，落进右半的概率是 $0$；站在 $X=2$ 时以 $0.3$ 走到 $3$、以 $0.3$ 走到 $1$、以 $0.4$ 留在 $2$，落进右半的概率是 $0.3$。同一个块里 $0$ 与 $0.3$ 并存，判据当场破碎。
>
> 只说「概率不同」还不够，最好给一个三阶的见证数，把历史泄漏量化出来。由均匀初始分布，$X_1$ 的四点分布是 $(0.325,0.175,0.175,0.325)$，故 $P(Y_1=1)=0.5$，其中来自 $X_1=2$ 的比重为 $0.175/0.5=0.35$，于是 $P(Y_2=2\mid Y_1=1)=0.3\times0.35=0.105$。若再补上 $Y_0=1$：联合概率 $P(Y_1=1,Y_0=1)=0.425$，而 $P(X_1=2,Y_1=1,Y_0=1)=0.25\times0.4=0.1$，条件比重降到 $0.1/0.425=0.2353$，于是 $P(Y_2=2\mid Y_1=1,Y_0=1)=0.3\times0.2353=0.0706$。两个数 $0.105$ 与 $0.0706$ 不相等，历史确实透过了粗标签。
>
> 为什么「初始四状态等概率」救不回来，值得单独说清。等初始分布只决定 $Y$ 的第一步预测，把桶内两个成员的权重抹成对半；但随后权重会自己漂移——$X=1$ 是吸收态，越久越沉；$X=2$ 每步有 $0.3$ 的机会逃出去，越久越少。于是每一步重新条件化时，桶内比例都是新的，粗过程的转移概率随时间变化，马尔可夫性从根本上不成立。初始条件只是一个参数，救不了结构性的失败。
>
> 换一个划分立刻就好用：按关于中点的反射并块，$\{1,4\}$ 与 $\{2,3\}$，含义是「到最近一端的距离」。验证：从 $1$ 与从 $4$ 都必然留在本块；从 $2$ 出发有 $0.3$ 进 $\{1,4\}$、$0.7$ 留在 $\{2,3\}$；从 $3$ 出发同样是 $0.3$ 与 $0.7$。块内一致，商链写成两行就是 $[1,0]$ 与 $[0.3,0.7]$，它的稳态退化到第一块，正对应「苍蝇终究被吃掉」。
>
> 18.06 的说法能一句话讲完：可合并等价于存在粗矩阵使 $PT=T\bar P$。本题失败的划分对应块指示向量 $(1,1,0,0)$ 与 $(0,0,1,1)$，它们张成的子空间在 $P$ 下不闭合，$\bar P$ 因此不存在；而 $\{1,4\}$ 与 $\{2,3\}$ 对应的 $(1,0,0,1)$ 与 $(0,1,1,0)$ 张成的子空间闭合，粗矩阵就写得出来。这就是「折叠失败」在线性代数里的准确含义。
>
> 最后纠正一处归因。原文说「$1$ 在区段边缘、$2$ 在内部」，把失配归因于位置，这不够准确；但把它归因于「$1$ 是吸收态」也不完整。真正的根源是：块 $\{1,2\}$ 把「边界状态」与「内部状态」并在一起，两者的一步外逃概率不同（$0$ 对 $0.3$）。若把 $1$ 改成普通反弹（$1\to2$ 概率 $1$），它的一步外逃概率仍然是 $0$——因为一步之内只能到 $2$，仍在块内——所以 $0$ 与 $0.3$ 的失配照旧存在，反例并不依赖吸收性，只是吸收把这个 $0$ 钉得更死。
>
> 反过来说，$\{1,4\}$ 与 $\{2,3\}$ 之所以可用，是因为它把两个边界并在一起、两个内点并在一起，块内两成员的一步外逃概率天然相同。这条经验可以直接迁移：要折叠，先按「离边界的距离」或「局部环境」分层，而不是按空间位置或标号切一刀。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">SECTION 7.2　状态分类（Classification of States）</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 4.**（蜘蛛与苍蝇相对运动，暂态与常返状态）</span>

A spider and a fly move along a straight line in unit increments. The spider always moves towards the fly by one unit. The fly moves towards the spider by one unit with probability $0.3$, moves away from the spider by one unit with probability $0.3$, and stays in place with probability $0.4$. The initial distance between the spider and the fly is integer. When the spider and the fly land in the same position, the spider captures the fly.

(a) Construct a Markov chain that describes the relative location of the spider and fly.

(b) Identify the transient and recurrent states.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题名义上考 transient（暂态）与 recurrent（常返）的判定，真正的技术动作只有一步：把二维的绝对坐标压成一维的 relative coordinate（相对坐标）。设蜘蛛位置 $S_n$、苍蝇位置 $F_n$，两者都在整数格点上漂移，粗看状态空间是二维无穷格；但两条更新规则都只问「谁在谁哪边、差几格」，与绝对位置无关，这就是 translation invariance（平移不变性）的作用。
>
> 令 $D_n=F_n-S_n$，取苍蝇在右侧为正。蜘蛛每步朝苍蝇走一格，故 $S_{n+1}=S_n+1$；苍蝇以 $0.3$ 朝蜘蛛走近一格、以 $0.3$ 背向走远一格、以 $0.4$ 原地不动，即 $F_{n+1}-F_n$ 取 $-1$、$+1$、$0$。合并得一步增量 $\Delta D_n\in\{-2,0,-1\}$，对应权重 $0.3$、$0.3$、$0.4$。注意 $\Delta D_n$ 的上界是 $0$ 而不是 $+1$：苍蝇想逃的那一格恰好被蜘蛛的前进吃掉。
>
> 这里有一处必须写明的约定：$D=1$ 时若抽到 $\Delta D=-2$，形式上会落到 $-1$。物理上这是「越过 $0$ 被捕获」，所以状态定义要写成 $D_{n+1}=\max(D_n+\Delta D_n,0)$，并规定落到 $0$ 即吸收。没有这条截断，状态集就不是 $\{0,1,\dots,d\}$，$\rho(Q)$ 的计算也会引入一个不存在的负状态。
>
> 第一个结构性事实：$\Delta D_n\le0$ 恒成立，且以 $0.7$ 的概率严格为负，所以 $D_n$ 是 monotonically nonincreasing（单调不增）的。第二个事实：$D_n=0$ 就是捕获条件，一旦命中过程终结，$p_{00}=1$，这是 absorbing state（吸收态）。合起来分类：$\{0\}$ 是唯一的 recurrent class（常返类），且带 self-loop（自环），因此 nonperiodic（非周期）；每个 $d\ge1$ 都是 transient（暂态），离开后再也回不去。
>
> 算 drift（漂移）：$\mathbb{E}[\Delta D_n\mid D_n\ge1]=0.3\times(-2)+0.3\times0+0.4\times(-1)=-1$，每步平均缩短整整一格。用 optional stopping（可选停时）把它转成时间界：若允许最后一步落到 $-1$（越过即止，不截断），则 $\mathbb{E}[D_T]=d-\mathbb{E}[T]$，而 $D_T\ge-1$，故 $\mathbb{E}[T]\le d+1$；这正是「多出来的那个 $1$」的来源，它来自一步最多降 $2$ 格造成的超额。
>
> 具体验一个小数：取 $d=1$，则一步之内有 $0.3$（$\Delta=-2$）与 $0.4$（$\Delta=-1$）两种方式直接捕获，只有 $0.3$（$\Delta=0$）留在原地，于是 $\mathbb{E}[T]=1+0.3\,\mathbb{E}[T]$，得 $\mathbb{E}[T]=1/0.7\approx1.4286$，确实不超过 $d+1=2$。这组数字顺手说明了截断与不截断两种口径给出的界一致。
>
> 原注有两处方向错误。第一，它说「若 $D_n$ 是带正漂移、趋向更大的随机游走，则它永远回不到 $0$」，并把本题归进这一支；实际 drift 是 $-1$，方向相反，本题的 $D$ 被推向 $0$ 而不是推向无穷。第二，它说「本题的 (b) 才需要先算净期望步进再定暂态/常返」；transient（暂态）与 recurrent（常返）的判据只有「能否返回」，与期望毫无关系，期望只决定 $\mathbb{E}[T]$ 是否有界。
>
> 反例最能定位关键机关：若蜘蛛不追、原地不动，$D_n$ 就变成增量 $\{-1,0,+1\}$、drift 为 $0$ 的对称随机游走，一维情形下它是 null recurrent（零常返），返回概率为 $1$ 但期望返回时间无穷，「$D\ge1$ 全 transient」的结论随之瓦解。跨课程一眼就通：把暂态块写成 substochastic matrix（次随机矩阵）$Q$，本题非对角元只向下、对角元是 $0.3$（$\Delta=0$ 那一支留在原地），故 spectral radius（谱半径）$\rho(Q)=0.3$，$Q^{n}$ 指数衰减、吸收几乎必然；这正是线性代数（18.06）里「矩阵幂的收敛速率由第二大特征值决定」在吸收链上的特例。
>
> 还要点明这一步为何不可省。原始模型的状态是「蜘蛛在第 $s$ 格、苍蝇在第 $f$ 格」，可数无穷；本章后面几乎所有结论都建立在 finite（有限性）上。压成 $D$ 之后状态集变成 $\{0,1,\dots,d\}$，有限性才回来，而 $d$ 恰好是题面给的初始距离——「初始距离是整数」这句看着啰嗦的话，实际是在保证状态空间有限。
>
> 收束：本章把「能否返回」与「多久返回」拆成两套工具，前者是 classification（分类），后者是 absorption time（吸收时间）。本题两个问题都有好答案，才有上面那套整齐结论；而在 drift 为 $0$ 的对称游走上，前者答「能」、后者答「无穷」，两者分离得干干净净。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 5.**（常返类是否为周期）</span>

Consider a Markov chain with states $1, 2, \ldots, 9$, and the following transition probabilities: $P_{12} = P_{17} = 1/2$, $P_{i(i+1)} = 1$ for $i \neq 1, 6, 9$, and $P_{61} = P_{91} = 1$. Is the recurrent class of the chain periodic or not?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把题面的转移写成图：$1$ 是唯一的分叉点，$P_{12}=P_{17}=1/2$；两支各自单向推进，$2\to3\to4\to5\to6\to1$ 回到 $1$ 共 $5$ 条边（连同出发的 $1\to2$ 构成 $6$ 步回路），$7\to8\to9\to1$ 连同 $1\to7$ 构成 $4$ 步回路；$6$ 与 $9$ 的出口都被钉死为 $1$，没有第三条路。
>
> 先定类。$1$ 可达全部 $9$ 个状态，而全部状态都能回到 $1$，于是 $R=\{1,\ldots,9\}$ 是唯一的 recurrent class（常返类）。所以题目问的不是某个状态的私事，而是这个常返类的 period（周期）。
>
> 按定义算：令 $Q=\{n:T_{11}(n)>0\}$，则 $4\in Q$、$6\in Q$，且 $Q$ 对加法封闭（两条回到 $1$ 的回路可以首尾拼接），所以 $4a+6b\in Q$ 对任意非负整数 $a,b$ 成立。取 greatest common divisor（最大公约数）得 $d=\gcd(4,6)=2$。这就是本题要的数值。
>
> 周期为 $2$ 意味着类能切成两层，正确的切法按「从 $1$ 出发的最短步数对 $d$ 取余」：距离 $0,1,2,\ldots,5$ 依次落到 $1;\,2,7;\,3,8;\,4,9;\,5;\,6$，于是偶数层 $S_1=\{1,3,5,8\}$、奇数层 $S_2=\{2,4,6,7,9\}$。逐条边核对：$1\to2$、$1\to7$ 是 $S_1\to S_2$；$2\to3$、$4\to5$、$8\to9$ 是 $S_2\to S_1$；$3\to4$、$5\to6$ 是 $S_1\to S_2$；$6\to1$、$7\to8$、$9\to1$ 是 $S_2\to S_1$。十条边没有一条留在层内，等价于说转移图是 bipartite（二部图）。
>
> 这里必须纠正一处极易犯的错：不能按状态标号奇偶分层。若写 $S_1=\{1,3,5,7,9\}$、$S_2=\{2,4,6,8\}$，则 $1\to7$ 与 $7\to8$ 立刻出错——前者的两端都在「奇数层」，成了层内边；后者的方向也反了（$7$ 在 $S_1$、$8$ 在 $S_2$）。正确分层里 $8$ 属于偶数层、$7$ 属于奇数层，与标号奇偶恰好相反。所谓「标号取模」在这道题上只是错觉：题面按环路顺序编号，才让它看着像按奇偶分层。
>
> 第二处要收紧的是「周期等于所有闭环回路长度的最大公约数」这句话。严格的对象是 $Q=\{n:T_{ii}(n)>0\}$，即「从 $i$ 出发恰好 $n$ 步回到 $i$」的那些长度；它与「经过 $i$ 的回路长度」一致，但若把不经过 $i$ 的回路也算进来，gcd 只会更小，未必等于类的周期。定义里的下标 $i$ 不能省。
>
> 周期之所以是类的属性、而不是状态的私货，一行就够：若 $i$ 与 $j$ 互通，取 $i\to j$ 的长度 $q$、$j\to i$ 的长度 $p$，则对每个 $n\in Q_j$ 有 $n+p+q\in Q_i$，故 $\gcd(Q_i)$ 整除 $\gcd(Q_j)$；把 $i,j$ 互换得反向整除，两者相等。
>
> 反例用来确认判据的锐度：要让周期消失，最干净的手法是加 self-loop（自环）。令 $P_{55}$ 取一个正数、其余按比例缩放，则长度 $1$、$4$、$6$ 同时落在 $Q$ 里，$\gcd(1,4,6)=1$，链立刻变成 nonperiodic（非周期）。这正是 PageRank（网页排名）里 damping（阻尼）项的作用：加自环把 $d$ 压成 $1$，保证幂迭代收敛。反过来，若把 $9\to1$ 改成 $9\to10\to11\to1$ 而总长度仍是偶数，$d$ 依旧是 $2$——光改结构不改长度的奇偶性，周期不会动。
>
> 线性代数（18.06）对齐一句：$d=2$ 就是二分，谱上必有 eigenvalue（特征值）$-1$；一般 $d$ 时 $P$ 的谱绕着 $d$ 次单位根轮转，Perron–Frobenius 把 $d>1$ 的情形叫 imprimitivity（非本原性），$d=1$ 时最大模特征值唯一、$P^{n}$ 收敛到秩一的 $\mathbf 1\boldsymbol\pi$。周期这个概念的全部内容，就是「单位根有几个」。
>
> 再补一个 $d=3$ 的样板，好在脑内固定图像：把三条等长的环路并联在同一个汇点上，每条长 $3$，回到该点的长度只能是 $3,6,9,\ldots$，gcd 仍是 $3$，状态按「从该点出发的步数对 $3$ 取余」分成三层，层与层单向轮转。
>
> 收束：这类题在考场上只有三步——确认全链只有一个常返类，取回到起点的长度集合求最大公约数，再用余数分层并逐条边核对去向。三步都不碰矩阵，却能推出「从某状态出发走 $n$ 步必落在哪一层」这种精确结论。

---
<!-- ===== PDF p390 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — 习题区续接（Problems，续）

> <span style="color:#7f8c8d;">本页为第 7 章章末 Problems 习题区的延续页，承接上一页（含 Problem 1–5），本页含 Problem 6 与 Problem 7，两题均带 `*` 难度标记，其题干与解答一律保持英文原题。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 6. \* Existence of a recurrent state（常返状态的存在性）</span>

Show that in a Markov chain at least one recurrent state must be accessible from any given state, i.e., for any $i$, there is at least one recurrent $j$ in the set $A(i)$ of accessible states from $i$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本题证明中的集合隶属符号在 OCR 中被误识别（如将 $\in$ 读作 `E`、将 $\notin$ 读作 `rJ.`、下标 $i_1$/$i_2$ 读作 `i l`/`i2`、$\neq$ 读作 `'#`、并将首处出现的 $i_1$ 误读为 `h`），上下面裁决按标准数学记号还原，未改动任何数值或论证步骤。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.** Fix a state $i$. If $i$ is recurrent, then every $j \in A(i)$ is also recurrent, so we are done. Assume that $i$ is transient. Then there exists a state $i_1 \in A(i)$ such that $i \notin A(i_1)$. If $i_1$ is recurrent, then we have found a recurrent state that is accessible from $i$, and we are done. Suppose now that $i_1$ is transient. Then $i_1 \neq i$, because otherwise the assumptions $i_1 \in A(i)$ and $i \notin A(i_1)$ would yield $i \in A(i)$ and $i \notin A(i)$, which is a contradiction. Since $i_1$ is transient, there exists some $i_2$ such that $i_2 \in A(i_1)$ and $i_1 \notin A(i_2)$. In particular, $i_2 \in A(i)$. If $i_2$ is recurrent, we are done. So suppose that $i_2$ is transient. The same argument as before shows that $i_2 \neq i_1$. Furthermore, we must also have $i_2 \neq i$. This is because if we had $i_2 = i$, we would have $i_1 \in A(i) \cap A(i_2)$, contradicting the assumption $i_1 \notin A(i_2)$. Continuing this process, at the $k$th step, we will either obtain a recurrent state $i_k$ which is accessible from $i$, or else we will obtain a transient state $i_k$ which is different than all the preceding states $i, i_1, \dots, i_{k-1}$. Since there is only a finite number of states, a recurrent state must ultimately be obtained.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题的结论「从任何状态出发，一定存在可达的常返态」是 finite（有限性）马尔可夫链的结构性铁律：它把 transient（暂态）与 recurrent（常返）这套分类，落回到可达关系的偏序结构上。整套证明只用两件工具，一是可达集的 transitivity（传递性），二是有限集合上的降链。
>
> 记 $A(i)$ 为从 $i$ 出发以正概率到达的状态集。两个基本事实先摆好：$j\in A(i)$ 且 $k\in A(j)$ 蕴含 $k\in A(i)$，因为两段正概率路径可以首尾相接；以及 $i\in A(i)$ 恒成立，走 $0$ 步也算到达。
>
> 第一步。若 $i$ 本身常返，则 $A(i)$ 里每个 $j$ 都常返，结论立即成立。理由是常返类没有再出去的边：$i$ 常返意味着从 $i$ 出发走不出它所在的类，而 $j\in A(i)$ 说明 $j$ 就在这个类里，同类则同命运。
>
> 第二步。设 $i$ 暂态。此时存在 $i_1\in A(i)$ 使 $i\notin A(i_1)$。这是暂态定义在图上的一句话翻译：暂态意味着 $i$ 所在的类有出边，走出去就回不来，那个落点就是 $i_1$。由传递性 $A(i_1)\subseteq A(i)$，而 $i\in A(i)$ 却 $i\notin A(i_1)$，故 $A(i_1)\subsetneq A(i)$，可达集严格缩水。
>
> 第三步。把同一句话反复用：只要当前状态还是暂态，就还能再切一刀，得到 $A(i)\supsetneq A(i_1)\supsetneq A(i_2)\supsetneq\cdots$。状态总数有限，严格递减的集合套不能无限延续，于是必在某个 $i_k$ 处停下。停下的含义是「$i_k$ 不再是暂态」，也就是 $i_k$ 常返，结论得证。
>
> 原文有一处跳步要补。它说「$i_k$ 的所有可达态都含 $i_k$ 自己，所以 $i_k$ 常返」，这一步不成立：$i_k\in A(i_k)$ 是恒等式，对判定毫无信息，拿它当判据等于用同义反复证明结论。真正的补法是回到类的语言：若 $i_k$ 暂态，它的类 $C$ 必有出边通向另一个类 $C'$，取 $i'\in C'$，则 $i_k\notin A(i')$，正好与停机条件正面相撞。所以停机处只能是常返的。
>
> 第二处要纠的是术语。原文把这个词译成「可达图的形式化」，只在后面附了一句英文原词 condensation，但 condensation 不是形式化，而是凝聚、压缩的意思，标准术语是 condensation graph（凝聚图）：把每个 strongly connected component（强连通分量，SCC）压成一个点，得到一张 directed acyclic graph（有向无环图），马尔可夫链的常返类正是其中的 sink（汇点），也就是出度为零的汇聚点。整段意思没错，只是名字被译歪，读者照「形式化」去检索会一无所获。
>
> 有限性是这条铁律的命根子：状态可数无穷时，$1\to2\to3\to\cdots$ 这样确定性右移的链一个常返态也没有，$A(i)$ 一路严格缩小永不停止。6.042J 的偏序语言里，这正是 well-founded（良基）关系上「不存在无穷降链」的要求，名字叫 descending chain condition（降链条件）；18.06 的矩阵语言里同一件事表现为封闭类与 irreducible（不可约）块的对应，$P$ 的每个封闭类都对应一个不可约块，块之间按可达关系排成 DAG。
>
> 这里要把两个容易混的论证分开，它们给出的东西不同。降链只证明「存在一个常返态」：切刀次数有限（至多 $m-1$ 刀），但每一刀之间走了多少步并没有被控制。而「$m$ 步以内必可达某个常返态」是另一条论证：从 $i$ 到它可达的某个常返态取一条最短路径，最短路径的顶点不重复，至多经过 $m-1$ 条边，所以 $m$ 步之内确有正概率落到常返区。前者给存在性，后者给步数上界，二者独立，不能互相替代。
>
> 这个论证还有一个可执行版本：从任意状态出发做一次图搜索，把可达图里的 SCC 全部找出来，再挑出没有出边的那个，它的任意一个状态就是常返态；对应地，只要沿「可达集缩水」的路径走，每走一步就固定一个新的 SCC。证明的每一步都对应一次宽度优先的推进，没有任何非构造性的成分。
>
> 最后点一下下游用途。Problem 7 的指数衰减正是靠这条结论起跳：正因为每个状态都能在 $m$ 步内以正概率摸到常返区，$\beta=\max_i q_i(m)$ 才严格小于 $1$，后面的 $c\gamma^{n}$ 才有意义。两题合起来，才把「常返态存在」升级成「进入常返区的时间有指数尾」；若跳过本题直接读 Problem 7，$\beta<1$ 会像一个凭空掉下来的常数。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 7. \* Markov chain with transient and recurrent states（兼有暂态与常返状态的马尔可夫链）</span>

Consider a Markov chain with some transient and some recurrent states.

(a) Show that for some numbers $c$ and $\gamma$ with $c > 0$ and $0 < \gamma < 1$, we have

```math
P(X_n \text{ is transient} \mid X_0 = i) \le c\, \gamma^n,
```

for all $i$ and $n \ge 1$.

(b) Let $T$ be the first time $n$ at which $X_n$ is recurrent. Show that such a time is certain to exist (i.e., the probability of the event that there exists a time $n$ at which $X_n$ is recurrent is equal to $1$) and that $E[T] < \infty$.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.** (a) For notational convenience, let

```math
q_i(n) = P(X_n \text{ transient} \mid X_0 = i).
```

A recurrent state that is accessible from state $i$ can be reached in at most $m$ steps, where $m$ is the number of states. Therefore, $q_i(m) < 1$. Let

```math
\beta = \max_{i = 1, \dots, m} q_i(m)
```

and note that for all $i$, we have $q_i(m) \le \beta < 1$. If a recurrent state has not been reached by time $m$, which happens with probability at most $\beta$, the conditional probability that a recurrent state is not reached in the next $m$ steps is at most $\beta$ as well, which suggests that $q_i(2m) \le \beta^2$. Indeed, conditioning on the possible values of $X_m$, we obtain

```math
\begin{aligned}
q_i(2m) &= P(X_{2m} \text{ transient} \mid X_0 = i) \\
&= \sum_{j \text{ transient}} P(X_{2m} \text{ transient} \mid X_m = j, X_0 = i)\; P(X_m = j \mid X_0 = i) \\
&= \sum_{j \text{ transient}} P(X_{2m} \text{ transient} \mid X_m = j)\; P(X_m = j \mid X_0 = i) \\
&= \sum_{j \text{ transient}} P(X_m \text{ transient} \mid X_0 = j)\; P(X_m = j \mid X_0 = i).
\end{aligned}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页尾部解答在最后一个和式处中断（其概率项 $P(X_m \text{ transient} \mid X_0 = j)$ 与劫持项 $P(X_m = j \mid X_0 = i)$ 的下标/分支在 OCR 中被断行混排），上一等式及不等式 $q_i(2m) \le \beta^2$ 的推导按原文语义还原，论证在换页处未完成。</span>
<!-- ===== PDF p391 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）**</span> — §7.4 习题区续接（Problems，续：承接上一页 Problem 7 的中段解答与本页新题 Problem 8）

> <span style="color:#7f8c8d;">本页无新节/新章标题，页首为上一页某题解答的中段延续（据后文 Problem 8 提示"use the result of Problem 7(b)"可确认为 Problem 7 的 Solution 下半部分），故标题标注「续」。页首碎片含页眉 "Markov Chains / 382"、"Chap. 7" 及循环引用页码的杂噪，已剔除。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答，续 Problem 7）：** By the Markov property, the probability of being in a transient state at time $2m$, given $X_0 = i$, can be decomposed into an intermediate step, and applying the induction bound yields

```math
P(X_{2m}\, \text{transient} \mid X_0 = i)
= \sum_{j\, \text{transient}} P(X_m = j \mid X_0 = i)\; P(X_m\, \text{transient} \mid X_m = j)
\leq \beta\; P(X_m\, \text{transient} \mid X_0 = i)
\leq \beta^2 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上面等式（求和与串联条件概率）为按题设与马尔可夫性质还原的规范形式；原页碎片为："L P(X_m … j transient … = β P(X_m transient | X0=i) … ≤ β²."，中间若干转移概率下标在 OCR 中丢失，未臆造具体数值，仅以通用 $\beta$ 与归纳步呈现。</span>

Continuing similarly, for all $i$ and $k \ge 1$, we have

```math
P(X_{km}\, \text{transient} \mid X_0 = i) \leq \beta^k ,\qquad \forall\, i,\; k \geq 1 .
```

Let $n$ be an arbitrary positive integer and let $k$ be the integer such that $km \le n < (k+1)m$. Then

```math
P(X_n\, \text{transient} \mid X_0 = i) \leq \beta^k \leq c\, \gamma^n .
```

Therefore, the required relation holds by taking $c = \beta^{-1}$ and $\gamma = \beta^{1/m}$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] "km < n < (k+l)m" 中的 "l" 系 "1" 的误识，已按 $(k+1)m$ 还原；末步 $\beta^k \le \beta^{n/m-1}=c\gamma^n$ 依赖 $\beta<1$ 与 $n < (k+1)m$，为标准还原。</span>

**(b)** Let $A$ be the event that the chain never enters the set of recurrent states. Using the result of part (a), we have

```math
P(A) \leq P(X_n\, \text{transient}) \leq c\, \gamma^n .
```

Since this holds for every $n$ and $\gamma < 1$, we must have $P(A) = 0$. This shows that, with probability 1, there is a finite time $T$ at which a recurrent state is first entered. Thus

```math
E[T] = \sum_{n=1}^{\infty} n\, P(X_{n-1}\, \text{transient},\, X_n\, \text{recurrent})
\leq \sum_{n=1}^{\infty} n\, P(X_{n-1}\, \text{transient})
\leq c \sum_{n=1}^{\infty} n\, (1-\gamma)\, \gamma^{\,n-1}
= \frac{c}{1-\gamma},
```

where the last equality follows from the mean of the geometric distribution.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问把「暂态终究会离开」量化成可证的速度。两小问各管一件事：(a) 给出 tail（尾概率）的几何上界 $c\gamma^{n}$，(b) 证明首次进入常返区的时刻 $T$ 几乎必然有限、且 expectation（期望）有限。(a) 是 (b) 的全部燃料，(b) 只是把 (a) 沿 $n$ 求和加一次放缩。
>
> 先看 (a) 的燃料从哪来。设状态总数为 $m$。从任何状态出发，到某个常返态的最短路径长度至多 $m-1$：最短路径的顶点不重复，最多 $m$ 个。于是 $m$ 步之内必有正概率摸到常返区，故 $q_i(m)<1$ 对所有 $i$ 成立。取 $\beta=\max_iq_i(m)$，有限个严格小于 $1$ 的数取最大，仍严格小于 $1$。这一步的合法性完全来自 Problem 6，不是凭空假设。
>
> 归纳那步要看实现细节。对 $n\ge m$，把「$n$ 步后仍在暂态」按 $X_{n-m}$ 的取值分解，再条件于 $X_{n-m}=j$ 用一次 $m$ 步的界，得 $q_i(n)\le\beta q_i(n-m)$，于是 $q_i(km)\le\beta^{k}$。这里不需要 $q_i(n)$ 关于 $n$ 单调，只需要「$m$ 步的坏运气能逐块相乘」，而逐块可乘正是 Markov property（马尔可夫性质）的全部内容。
>
> 换成任意 $n$：取 $k=\lfloor n/m\rfloor$，则 $km\le n<(k+1)m$，而 $q_i(n)\le\beta^{k}$。因 $\beta<1$，指数越小值越大，由 $k\ge n/m-1$ 得 $\beta^{k}\le\beta^{n/m-1}$。于是取 $c=\beta^{-1}$、$\gamma=\beta^{1/m}$，就有 $q_i(n)\le c\gamma^{n}$。(a) 到此为止，两个常数都是显式的。
>
> (b) 的前半是标准的「任意小只能为零」。设 $A$ 为链永不进入常返集的事件。对每个 $n$ 都有 $A\subseteq\{X_n\ \text{still transient}\}$，故 $P(A)\le q_i(n)\le c\gamma^{n}$。左边与 $n$ 无关，右边随 $n$ 趋于 $0$，只能 $P(A)=0$。正文这一步省掉了条件 $X_0=i$，记号上应写 $P_i(A)$，含义不变。
>
> 后半的 $\mathbb{E}[T]$ 有一处常数松动，值得记下来。正确的链路是 $P(T=n)\le P(X_{n-1}\ \text{still transient})\le c\gamma^{n-1}$，于是 $\mathbb{E}[T]\le\sum_{n\ge1}nc\gamma^{n-1}=c/(1-\gamma)^{2}$。书上多塞了一个因子 $(1-\gamma)$，写成 $c/(1-\gamma)$；这个上界比逐项所能给的更小，作为不等式并不成立。补救只需一句话：常数 $c$ 本来只要求存在，把 (a) 里的 $c$ 放宽成 $c/(1-\gamma)$ 即可，「$\mathbb{E}[T]<\infty$」的结论分毫不动。
>
> 还要补一句顺序问题：$\mathbb{E}[T]=\sum_nnP(T=n)$ 这个写法默认 $T$ 几乎必然有限，否则求和漏掉了 $T=\infty$ 那块质量。上一段的 $P(A)=0$ 正好提供这个前提，两半的顺序不能颠倒。
>
> 换成线性代数（18.06）的矩阵语言更清楚，因为这把「离开暂态区」翻译成矩阵幂的收敛问题，所以上面的逐块放缩就变成一次范数估计。把常返状态的行与列都删掉，剩下暂态块 $Q$，它是 substochastic matrix（次随机矩阵）；$q_i(n)$ 就是 $Q^{n}$ 第 $i$ 行的行和。$\rho(Q)<1$ 等价于「所有暂态都会离开」，而 $Q^{n}\to0$ 的速率由 spectral radius（谱半径）控制。书上用 $\beta$ 而不是 $\rho$ 是有意的：$\beta$ 给出 $\|Q^{m}\|_\infty$ 的一个上界，走的是 induced infinity norm（诱导无穷范数），比谱半径粗，但只用到正性与行和这类初等量，完全避开特征值。这套「每 $m$ 步统一收缩一次」的手法在随机过程里叫 uniform geometric ergodicity（一致几何遍历性）。
>
> 反例确认有限性不可省，但例子要挑对。正确的例子是半直线上的对称随机游走：状态集取 $\{0,1,2,\ldots\}$，$0$ 为 absorbing state（吸收态），其余每步以 $1/2$ 向左、$1/2$ 向右。此时 $1,2,3,\ldots$ 全是暂态，而「到第 $n$ 步仍未被吸收」的概率按 $n^{-1/2}$ 量级衰减，于是 $\mathbb{E}[T]=\infty$，指数界 $c\gamma^{n}$ 不复存在。注意不能拿整条整数轴上的对称随机游走当例子：那条链是 null recurrent（零常返），根本没有暂态区，与本题讨论的对象不是一回事。
>
> 再补两点，让 $m$ 这个数不显得神秘。第一，为什么按 $m$ 步整块切而不是每步一刀：单步的量 $q_i(1)$ 完全可能等于 $1$，暂态状态可以在小圈里打转，只有凑够 $m$ 步才保证有正概率真的跳出去。第二，$\gamma$ 是保守估计：真实的渐近速率是 $\rho(Q)$，而 $\beta^{1/m}\ge\rho(Q)$，书上的几何速率只会比谱半径更慢、绝不会更快；它买到的是初等性与显式性，付出的是常数与速率上的松弛。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本式在 OCR 中被严重打散（如 "$=1$"、"$c\_ {\sum}$" 等碎片），已按几何分布均值论证还原为上述规范形式（$\sum_{n\ge1} n(1-\gamma)\gamma^{n-1} = 1/(1-\gamma)$），未臆造系数。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 8.\* 常返状态（Recurrent states）**</span>

Show that if a recurrent state is visited once, the probability that it will be visited again in the future is equal to 1 (and, therefore, the probability that it will be visited an infinite number of times is equal to 1). Hint: Modify the chain to make the recurrent state of interest the only recurrent state, and use the result of Problem 7(b).

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：** Let $s$ be a recurrent state, and suppose that $s$ has been visited once. From then on, the only possible states are those in the same recurrence class as $s$. Therefore,

> <span style="color:#7f8c8d;">[跨页续接] 本页止于 "Therefore,"，后续论证翻页续接至下一页（Problem 8 的 Solution 尚未结束）。</span>
<!-- ===== PDF p392 ===== -->

> <span style="color:#7f8c8d;">第 7 章 Markov Chains（马尔可夫链）— 习题区续接（Problems，续）。本页页首延续上一页 Problem 8 的 Solution（该题带 `*`，Solution 保持英文），随后为 Problem 9「Periodic classes（周期类）」，页尾在该题 Solution 中部断开、延续到下一页。</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 8（续）——Recurrent states（常返态）的解答后半段**</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution.** … without loss of generality, we can assume that there is a single recurrent class. Suppose that the current state is some $i \neq s$. We want to show that $s$ is guaranteed to be visited some time in the future.

Consider a new Markov chain in which the transitions out of state $s$ are disabled, so that $p_{ss} = 1$. The transitions out of states $i$, for $i \neq s$, are unaffected. Clearly, $s$ is recurrent in the new chain. Furthermore, for any state $i \neq s$, there is a positive probability path from $i$ to $s$ in the original chain (since $s$ is recurrent in the original chain), and the same holds true in the new chain. Since $i$ is not accessible from $s$ in the new chain, it follows that every $i \neq s$ in the new chain is transient. By the result of Problem 7(b), state $s$ will be eventually visited by the new chain (with probability $1$). But the original chain is identical to the new one until the time that $s$ is first visited. Hence, state $s$ is guaranteed to be eventually visited by the original chain. By repeating this argument, we see that $s$ is guaranteed to be visited an infinite number of times (with probability $1$).

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 题干要证两件事：常返态只要被访问过一次，未来再被访问的概率为 $1$；因此被访问无穷多次的概率也为 $1$。提示只有一句：改造链，让目标常返态成为唯一常返态，再用 Problem 7(b) 的尾估计。
>
> 先分清这两件事并不等价。「还会再来一次」只续一条命，要拿到无穷次必须把它迭代到可数个事件上，这一步靠 strong Markov property（强马尔可夫性），或者用更朴素的说法「每次回到 $s$ 就把计数清零、重新出发」。原书解答只写了前半，后半是归纳。
>
> 改造的做法：设 $s$ 是常返态且已被访问过一次，此后只在 $s$ 所在的类里活动，故不妨假设全链只有一个常返类。现在令 $p_{ss}=1$、其余从 $s$ 出发的转移全部清零，$s$ 立刻成为 absorbing state（吸收态），而其他状态的入边、出边原样保留。
>
> 这里有一处看似矛盾、其实同一件事的说法要理顺：「切断所有从 $s$ 出去的边」与「只能进不能出」不是两种相反的做法，而是同一件事的两种描述——把出边改成一条指向自己的边，等价于令 $p_{ss}=1$。原文把它们写成相反的两句，是把「删边」与「加自环」当成两个操作了；矩阵上二者给出同一行 $(0,\dots,1,\dots,0)$。
>
> 关键的一步是判定新链里谁常返，而这里最容易读漏一件事：$s$ 的入边仍然通着。对任何 $i\ne s$，原链同类内互通，故存在正概率路径 $i\to s$，并且可以安排成「只在最后一步踏进 $s$」。既然 $s$ 只进不出，任何 $i\ne s$ 若在新链里 recurrent（常返），就必须以概率 $1$ 回到 $i$；但它有正概率走到 $s$ 后被永久困住，返回概率于是小于 $1$，矛盾。所以新链里 $s$ 之外全是 transient（暂态），唯一的常返态就是 $s$。
>
> 于是 Problem 7(b) 直接可用：新链几乎必然在有限时间内进入常返态集，而这个集合只有 $\{s\}$ 一个元素，所以几乎必然到达 $s$。
>
> 最后一步是把新链的结论搬回原链，靠 coupling（耦合）：两条链在「首次访问 $s$ 之前」共享同一批随机数，轨迹逐点相同；一旦原链首次到达 $s$，之后的事不必再管。因此原链也几乎必然再访问 $s$，而且这个「再次」发生在某个有限时刻之后。
>
> 无穷次靠迭代：定义 $\tau_k$ 为第 $k$ 次访问 $s$ 的时刻，同一条论证给出 $P(\tau_{k+1}<\infty\mid\tau_k<\infty)=1$，取可数交仍是概率 $1$。这就是「常返」与「访问无穷次」的严格等价，也是后面 renewal theorem（更新定理）与平均返回时间 $1/\pi_s$ 的前提。
>
> 还有一处术语要改：原文自造了 absorption-fication 一词，标准说法就是 absorption（吸收）。跨课程看，这套「把目标做成吸收面、再看概率流进去多少」的手法，在 18.06 的线性代数里就是吸收链的分块形式：$(I-Q)^{-1}=\sum_{k\ge0}Q^{k}$ 是 Neumann series（诺伊曼级数），$Q$ 为暂态块、是 substochastic（次随机）矩阵，$\rho(Q)<1$ 保证级数收敛，而「进入吸收态的概率」正是 $1$ 与行和之差（行和是期望吸收步数，不是概率，但两者的收敛性同源）。
>
> 反例确认 $s$ 必须常返：若 $s$ 只是暂态，单次返回概率记为 $f<1$，则从「刚访问过 $s$ 之后」起算，再访问次数 $N$ 服从 geometric（几何）分布，正确写法是 $P(N=k)=f^{k}(1-f)$（$k\ge0$），其和恰为 $1$。若把下标写成 $k\ge1$ 而公式不变，总和只有 $f$——取 $f=0.5$ 时是 $0.5$——少掉的 $1-f$ 正是「一次都不再访问」的质量；要写成 $k\ge1$ 的形式，公式必须是 $f^{k-1}(1-f)$。两种写法都对，混用就错。
>
> 收束：结论不是「一般状态都会无限次被访问」，而是常返类专属的权利；暂态即使被访问过，未来仍以正概率永别。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 9. \* Periodic classes（周期类）**</span>

Consider a recurrent class $R$. Show that exactly one of the following two alternatives must hold:

(i) The states in $R$ can be grouped in $d > 1$ disjoint subsets $S_1, \ldots, S_d$, so that all transitions from $S_k$ lead to $S_{k+1}$, or to $S_1$ if $k = d$. (In this case, $R$ is periodic.)

(ii) There exists a time $n$ such that $T_{ij}(n) > 0$ for all $i, j \in R$. (In this case $R$ is aperiodic.)

**Hint:** Fix a state $i$ and let $d$ be the greatest common divisor of the elements of the set $Q = \{n \mid T_{ii}(n) > 0\}$. If $d = 1$, use the following fact from elementary number theory: if the positive integers $a_1, a_2, \ldots$ have no common divisor other than $1$, then every positive integer $n$ outside a finite set can be expressed in the form $n = k_1 a_1 + k_2 a_2 + \cdots + k_t a_t$ for some nonnegative integers $k_1, \ldots, k_t$, and some $t \geq 1$.

<span style="color:#2471a3;">**[solution]**</span> **Solution.** Fix a state $i$ and consider the set $Q = \{n \mid T_{ii}(n) > 0\}$. Let $d$ be the greatest common divisor of the elements of $Q$. Consider first the case where $d \neq 1$. For $k = 1, \ldots, d$, let $S_k$ be the set of all states that are reachable from $i$ in $ld + k$ steps for some nonnegative integer $l$. Suppose that $s \in S_k$ and $p_{ss'} > 0$. Since $s \in S_k$, we can reach $s$ from $i$ in $ld + k$ steps for some $l$, which implies that we can reach $s'$ from $i$ in $ld + k + 1$ steps. This shows that $s' \in S_{k+1}$ if $k < d$, and that $s' \in S_1$ if $k = d$. It only remains to show that the sets $S_1, \ldots, S_d$ are disjoint. Suppose, to derive a contradiction, that $s \in S_k$ and $s \in S_{k'}$ for some $k \neq k'$. Let $q$ be the length of some positive probability path from $s$ to $i$. Starting from $i$, we can get to $s$ in $ld + k$ steps, and then return to $i$ in $q$ steps. Hence $ld + k + q$ belongs to $Q$, which implies that $d$ divides $k + q$. By the same argument, $d$ must also divide $k' + q$. Hence $d$ divides $k - k'$, which is a contradiction because $1 \leq |k - k'| \leq d - 1$.

Consider next the case where $d = 1$. Let $Q = \{a_1, a_2, \ldots\}$. Since these are the possible lengths of positive probability paths that start and end at $i$, it follows that any integer $n$ of the form $n = k_1 a_1 + k_2 a_2 + \cdots + k_t a_t$ is also in $Q$. (To see this, use $k_1$ times a path of length $a_1$, followed by using $k_2$ times a path of length $a_2$, etc.) By the number-theoretic fact given in the hint, the set $Q$ contains all but finitely many positive integers. Let $\bar n$ be such that

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 此位置原文应有「$T_{ii}(n) > 0$ 对所有 $n > \bar n$」之类的条件式，但 OCR 将公式字段打断成碎片（如 `for all n > ni`），无法还原原文朝向，已保留为下方的英文语句骨架，未臆造系数/下标。</span>

for all $n > \bar n$.

Fix some $j \neq i$ and let $q$ be the length of a shortest positive probability path from $i$ to $j$, so that $q < m$, where $m$ is the number of states. Consider some $n$ that satisfies

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原文在「Consider some $n$ that satisfies」后有一表达式被换页符截断、本页到此中断，未识别完整公式；后续内容延续到下一页。</span>
<!-- ===== PDF p393 ===== -->

> <span style="color:#7f8c8d;">第 7 章 Markov Chains（马尔可夫链）— 习题区续接（Problems，续）。本页页首延续上一页 Problem 9「Periodic classes（周期类）」（带 `*`，Solution 保持英文）的解答中部，随后进入 SECTION 7.3 Steady-State Behavior（稳态行为），页尾列出 Problem 10 题干并在此截断、延续到下一页。</span>

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 9（续）——Periodic classes（周期类）的解答后半段**</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution.** … $n > \bar{n} + \square$ and note that $n - q > \bar{n} + \square - q > \bar{n}$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上一页「Consider some $n$ that satisfies」后的条件式在本页续接为「$n > \bar{n} + \cdot$ and note that $n - q > \bar{n} + \cdot - q > \bar{n}$」。OCR 丢失了跟在两个「+」号后的常数（按上下文应为某个取整/余量常数，使 $n - q > \bar{n}$ 成立），故以 `+ \square` 占位，未臆造数值。</span>

Thus, we can go from $i$ to itself in $n - q$ steps, and then from $i$ to $j$ in $q$ steps. Therefore, there is a positive probability path from $i$ to $j$, of length $n$, so that $T_{ij}(n) > 0$.

We have so far established that at least one of the alternatives given in the problem statement must hold. To establish that they cannot hold simultaneously, note that the first alternative implies that $T_{ii}(n) = 0$ whenever $n$ is not an integer multiple of $d$, which is incompatible with the second alternative.

For completeness, we now provide a proof of the number-theoretic fact that was used in this problem. We start with the set of positive integers $a_1, a_2, \ldots$, and assume that they have no common divisor other than $1$. We define $M$ as the set of all positive integers of the form $\sum_{i=1}^{t} k_i a_i$, where the $k_i$ are nonnegative integers. Note that this set is closed under addition (the sum of two elements of $M$ is of the same form and must also belong to $M$). Let $g$ be the smallest difference between two distinct elements of $M$. Then, $g \geq 1$ and $g \leq a_i$ for all $i$, since $a_i$ and $2 a_i$ both belong to $M$.

Suppose that $g > 1$. Since the greatest common divisor of the $a_i$ is $1$, there exists some $a_{i^*}$ which is not divisible by $g$. We then have

```math
a_{i^*} = f\, g + r
```

for some positive integer $f$, where the remainder $r$ satisfies $0 < r < g$. Furthermore, in view of the definition of $g$, there exist nonnegative integers $k_1, k_1', \ldots, k_t, k_t'$ such that

```math
\sum_{i=1}^{t} k_i a_i = \sum_{i=1}^{t} k_i' a_i + g .
```

Multiplying this equation by $f$ and using the equation $a_{i^*} = f g + r$, we obtain

```math
\sum_{i=1}^{t}(f k_i)\, a_i = \sum_{i=1}^{t}(f k_i')\, a_i + f g = \sum_{i=1}^{t}(f k_i')\, a_i + a_{i^*} - r .
```

This shows that there exist two numbers in the set $M$, whose difference is equal to $r$. Since $0 < r < g$, this contradicts our definition of $g$ as the smallest possible difference. This contradiction establishes that $g$ must be equal to $1$.

Since $g = 1$, there exists some positive integer $x$ such that $x \in M$ and $x + 1 \in M$. We will now show that every integer $n$ larger than $a_1 x$ belongs to $M$. Indeed, by dividing $n$ by $a_1$, we obtain $n = k a_1 + r$, where $k \geq x$ and where the remainder $r$ satisfies $0 \le r < a_1$. We rewrite $n$ in the form

```math
n = x(a_1 - r) + (x + 1) r + (k - x) a_1 .
```

Since $x$, $x + 1$, and $a_1$ all belong to $M$, this shows that $n$ is the sum of elements of $M$ and must also belong to $M$, as desired.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题把周期的定义式命题化：对任何 recurrent class（常返类）$R$，只有两种可能。(i) 能把 $R$ 切成 $d>1$ 个不相交子集，转移严格按 $S_1\to S_2\to\cdots\to S_d\to S_1$ 逐层推进，这叫 periodic（周期）。(ii) 存在某个 $n$，使 $R$ 里任意 $i,j$ 都满足 $T_{ij}(n)>0$（恰好 $n$ 步可达），这叫 aperiodic（非周期）。这一问的价值在于把「周期性」从画图手感变成可判定的二选一。
>
> 判据的锚点是 $d$。固定 $i$，令 $Q=\{n:T_{ii}(n)>0\}$，$d=\gcd(Q)$。$Q$ 对加法封闭：一条长 $a$ 的回路接上一条长 $b$ 的回路，就是长 $a+b$ 的回路，故 $a,b\in Q$ 蕴含 $a+b\in Q$。这条封闭性是后面所有拼接论证的引擎。
>
> $d>1$ 时这样切：$S_k=\{s:\exists l\ge0,\ T_{is}(ld+k)>0\}$，$k=1,\ldots,d$，这里 $T_{is}$ 的下标顺序是「从 $i$ 出发、到 $s$」。若 $s\in S_k$ 且 $p_{ss'}>0$，则从 $i$ 走 $ld+k$ 步到 $s$、再走一步到 $s'$，故 $s'\in S_{k+1}$，$k=d$ 时绕回 $S_1$。逐层推进就这样落了地。
>
> 唯一需要技巧的是两两不交。设 $s\in S_k\cap S_{k'}$ 而 $k\ne k'$。取一条从 $s$ 到 $i$ 的正概率路径，长为 $q$：从 $i$ 走 $ld+k$ 步到 $s$ 再走 $q$ 步回到 $i$，故 $ld+k+q\in Q$，于是 $d\mid(k+q)$；同法得 $d\mid(k'+q)$；两式相减得 $d\mid(k-k')$。但 $0<|k-k'|<d$，矛盾。这条论证只依赖一个事实：类内任意状态都能回到 $i$。
>
> $d=1$ 时走另一支。数论事实说 $Q$ 包含所有足够大的整数，即 $T_{ii}(n)>0$ 对 $n>\bar n$ 成立。再取 $j\ne i$，设 $i\to j$ 的最短路径长为 $q<m$；对 $n>\bar n+q$ 有 $n-q>\bar n$，故 $T_{ii}(n-q)>0$，接上那条路径得 $T_{ij}(n)>0$。对有限个 $j$ 取最大的 $q$，就得到 (ii) 所需的那个公共的 $n$。
>
> 两支互斥：$d>1$ 时 $T_{ii}(n)=0$ 对所有非 $d$ 倍数的 $n$ 成立，而 (ii) 要求从某个 $n$ 起所有步数都正，取 $i=j$ 立刻矛盾。所以「恰有一支成立」是完整的。
>
> 数论事实的骨架值得复述。$M=\{\sum k_ia_i:k_i\ge0\}$ 对加法封闭，取 $g$ 为 $M$ 中两个不同元素之差的最小正值，则 $g\le a_i$，因为 $a_i$ 与 $2a_i$ 都在 $M$。若 $g>1$，因 $a_i$ 的公因数是 $1$，存在某个 $a_{i^\ast}$ 不被 $g$ 整除，写成 $a_{i^\ast}=fg+r$（$0<r<g$）；按 $g$ 的定义存在 $M$ 中两元素之差为 $g$，同乘 $f$ 后与 $a_{i^\ast}$ 相减，得到 $M$ 中两元素之差为 $r$，于是 $r\ge g$，矛盾。故 $g=1$，即存在 $x$ 使 $x$ 与 $x+1$ 都在 $M$ 里。
>
> 收尾：对任何 $n>a_1x$ 写 $n=ka_1+r$（$0\le r<a_1$），必 $k\ge x$，于是 $n=x(a_1-r)+(x+1)r+(k-x)a_1$ 落在 $M$ 里。这就是「两枚硬币能否凑出某金额」问题的可达性上界。那个界在数论里有名字，但名字要写准：conductor（导子）指的是「此后所有整数都属于 $M$」的最小起点，等于 $\bar n+1$；而 $\bar n$ 本身是「最后一个可能缺席的整数」。把两者混说会差 $1$。
>
> 原文还有三处要修。第一，它写「两条回路能且只能拼接成一长回路」，那个「只能」既多余又错：回路可拼也可不拼；正确表述是「可拼接」，所以 $Q$ 对加法封闭。第二，它写「若 $d>1$，则所有返回时间的长度都落在某个同余类里」，精确说法是落在 $0\bmod d$ 这唯一的一个同余类里，即 $Q\subseteq d\mathbb{Z}_{>0}$，不是「某个」。第三，它把分层键说成「到 $i$ 的步数 $\bmod d$」，方向反了：应当是「从 $i$ 出发的步数 $\bmod d$」，$k$ 是状态所属的层号，不是状态名。
>
> 跨课程：$d$ 在线性代数（18.06）的矩阵论里有名字，叫 imprimitivity index（非本原指数），$d=1$ 时 $P$ 称为 primitive（本原）。Perron–Frobenius 说不可约链的谱在每个 $d$ 次单位根上都有特征值，$d>1$ 时「唯一主导特征值」失效，这正是幂迭代在周期链上不收敛的原因。数论那一半是 numerical semigroup（数值半群）的经典结论，Frobenius coin problem（弗罗贝尼乌斯硬币问题）问的就是互素硬币凑不出的最大面额，本题证的正是「凑不出的数只有有限多个」。
>
> 顺带答一个常被追问的细节：$S_1,\ldots,S_d$ 的并为什么正好是整个 $R$。$R$ 里每个状态都能从 $i$ 走到，设最短步数为 $n$，把 $n$ 除以 $d$ 得余数，非零时它落在对应的 $S_k$；$i$ 自身落在 $S_d$，因为 $0$ 步、余数 $0$ 记作 $d$。这一句让「切分」真正成为分划，而不只是覆盖。

---

<span style="color:#c0392b;">**SECTION 7.3　Steady-State Behavior（稳态行为）**</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 10.**</span>

> <span style="color:#7f8c8d;">第 7 章习题区的英文题干保持英文原题，不翻译，此处仅作题号定位。</span>

Consider the two models of machine failure and repair in Example 7.3. Find conditions on $b$ and $T$ for the chain to have a single recurrent class which is

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页在 Problem 10 题干「…a single recurrent class which is」处被换页符截断，引导性从句的其余内容（该句后续成分及可能的 (a)/(b) 小问）延续到下一页，本页未出现，不臆造。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 先交代口径：题干在换页处被截断，源文件只剩前半句。据教材原题的外部转录，完整问法是「Find conditions on $b$ and $T$ for the chain to have a single recurrent class which is aperiodic and, under those conditions, find closed form expressions for the steady-state probabilities」。后半句的显式稳态解只能算「按题意推演」，不能当作原书结论引用。
>
> 两个模型的差别只在状态怎么定义。模型一只用两个状态：working（工作）记 $1$、broken（损坏）记 $2$，一天内损坏概率 $b$、被修复概率 $r$，转移矩阵为 $P=[[1-b,b],[r,1-r]]$。模型二把「已连续损坏多少天」编进 state（状态），坏满 $T$ 天就整机换新。所以 $T$ 只活在模型二里，模型一的参数是 $b$ 与 $r$；把 $T$ 说成模型一的「更换周期」并略去 $r$，是第一处混淆。
>
> 这是 state augmentation（状态增广）的标准案例。马尔可夫性要求状态携带所有影响未来的信息；模型一的 broken 丢掉了「坏多久了」，无法表达「满 $T$ 天更换」这条机制，于是必须把计时器显式编进状态。代价是状态数从 $2$ 变成 $T+1$，收益是把「确定性等待」变成一眼可读的结构。
>
> 模型一的单一常返类条件要重新算。两个状态各自成为 absorbing state（吸收态）的条件是 $b=0$（$1$ 自锁）与 $r=0$（$2$ 自锁）。所以「只有一个常返类」的充要条件不是 $0<b<1$ 且 $0<r<1$，而是 $b+r>0$：$b=0$、$r>0$ 时类只有 $\{1\}$，状态 $2$ 是 transient（暂态），仍然是单类；$r=0$、$b>0$ 时类只有 $\{2\}$，同样单类。这个区别不只是措辞：$b=1$、$r=0.5$ 时矩阵是 $[[0,1],[0.5,0.5]]$，两状态互通，属单类，而 $0<b<1$ 的说法会把它排除。
>
> 模型一的非周期性几乎自动成立。只要 $b<1$，状态 $1$ 就有 self-loop（自环）$1-b>0$，周期为 $1$；若 $b=1$ 而 $r<1$，状态 $2$ 有自环 $1-r>0$，回到 $1$ 的长度同时有 $2$ 与 $3$，gcd 仍为 $1$。唯一失效的是 $b=r=1$：此时链是确定性二循环，周期 $2$。所以「单类且非周期」在模型一上的条件是 $b+r>0$ 且 $(b,r)\ne(1,1)$。
>
> 模型二的条件简单些。状态 $0$ 为 working，$1,\ldots,T$ 为已坏 $k$ 天，转移是 $0\to1$ 概率 $b$、$0\to0$ 概率 $1-b$、$k\to k+1$ 概率 $1$、$T\to0$ 概率 $1$。单一常返类当且仅当 $b>0$（$b=0$ 时 $0$ 吸收、其余暂态，分成两类）；非周期当且仅当 $b<1$（自环 $1-b$ 消失后，唯一回路长度是 $T+1$）。合起来就是 $0<b<1$。
>
> 把两件事分开看能避免一个常见误判：$b=1$ 的模型二仍然只有一个常返类（全部 $T+1$ 个状态互通），只是周期为 $T+1$，$T=4$ 时 $P$ 就是一个五步循环置换矩阵，$P^{5}=I$。所以「单类」与「非周期」是两个独立条件，前者管可达性，后者管节拍。
>
> 稳态概率也写出来方便核对。模型一解 $\pi P=\pi$ 加归一化，得 $\pi_1=r/(b+r)$、$\pi_2=b/(b+r)$（要求 $b+r>0$），验证只需一行 $\pi_1b=\pi_2r$；这是 birth-death（生灭）型链，detailed balance（细致平衡）一步到位。模型二用平衡方程：$\pi_0=(1-b)\pi_0+\pi_T$ 给出 $\pi_T=b\pi_0$；坏态走廊是确定性推进，故 $\pi_1=\cdots=\pi_T=b\pi_0$；归一化 $\pi_0(1+bT)=1$，得 $\pi_0=1/(1+bT)$，每个坏态为 $b/(1+bT)$。
>
> 这个结果有一句物理读法：一个 renewal（更新）周期是「平均 $1/b$ 天 working 加 $T$ 天损坏」，所以 working 的占比自然是 $1/(1+bT)$。把它与模型一的 $r/(b+r)$ 对照，就能看出「把 $r$ 换成确定性 $1/T$」的差别在哪：模型二里 $r$ 被换成了「恰好 $T$ 天」，二者只有在 $r=1/T$ 附近才对得上。
>
> 原文还有两处术语要改。它说「若维修有去无回，那么『正在更换』这一过程只是暂态走廊」，但模型二的走廊是「已坏未满 $T$ 天」的等待，不是「正在更换」的施工过程；它又说「常返类就是那台好机器的全体状态」，而模型二的常返类是全部 $T+1$ 个状态，整个循环都在类里，只提 working 会让读者以为类是单点，与 (a) 的结论自相矛盾。
>
> 最后一处术语也要改：$b=1$ 时 $P$ 不是「循环置换的伴随矩阵」，而是线性代数（18.06）里的 circulant matrix（循环矩阵），即每行是上一行的循环右移；adjugate（伴随矩阵）是完全不同的对象。$b=1$ 时它的特征值全落在 $T+1$ 次单位根上，幂迭代开始振荡而不收敛，稳态分布作为「极限分布」不再存在，只剩时间平均——这就是 Problem 5 的二部图现象换了马甲。

---
<!-- ===== PDF p394 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">[原页 OCR 严重损坏] 本页为第 7 章章末 Problems 习题区，处于后半段（页面上可见 Problem 11、Problem 12 及其后一题）。源页 OCR 被打乱成大量碎片，且很多数值/系数、题号、图与小题编号残缺。下面对两张凭可靠来源（教材原文转录）可完整还原的题给出还原双语；对过度损坏的一题仅保留可辨认片段，并在行内用灰注释标明占位，**不臆造任何转移概率、系数或小题原句**。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 11（教授的试题难度在 hard/medium/easy 间循环，求稳态概率）</span>

A professor gives tests that are hard, medium, or easy. If she gives a hard test, her next test will be either medium or easy, with equal probability. However, if she gives a medium or easy test, there is a 0.5 probability that her next test will be of the same difficulty, and a 0.25 probability for each of the other two levels of difficulty. Construct an appropriate Markov chain and find the steady-state probabilities.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这题的关键不在马尔可夫，而在建模：先要看出「渔竿总数守恒」，状态空间才会自己塌成 $n+1$ 维。题干只说天好就带一根杆上路、天坏就不带，而杆永远只在主屋与岛上小屋之间周转，总数恒为 $n$；于是只要记住其中一处有几根，另一处自动确定。记 $X$ 为岛上小屋的杆数，$X\in\{0,\ldots,n\}$，恰好 $n+1$ 个状态，与题面要求的状态数对上了。
>
> 时间单位取一次往返：去岛上一程、回主屋一程，两程各以概率 $p$ 好天气，且与过去无关，所以两程相互独立。去程天好则从主屋带一根上岛，回程天好则从岛上带一根回主屋；某一程天气不好就不带，杆留在原处。规则只有这两句，剩下的全是记账。
>
> 内部状态 $0<x<n$ 有四种组合：两程都好，一进一出，净变化为零；只去程好，$x\to x+1$；只回程好，$x\to x-1$；两程都坏，不动。于是 $P(x\to x+1)=p(1-p)$、$P(x\to x-1)=(1-p)p$，两个方向的概率相等，这正是 detailed balance（细致平衡）的形状，也预告了稳态在内部是平的。
>
> 边界要单独算，这是本题唯一的坑。$x=n$ 时主屋一根也没有：去程天好也无杆可带，于是「天好但没杆」的事件正好在这里发生；回程天好则从岛上带一根下去，故 $n\to n-1$ 的概率是 $p$（与去程无关），$n\to n$ 的概率是 $1-p$。反过来 $x=0$ 时岛上无杆，去程好必能带一根上去，但随后回程好又会把它带回来，所以 $0\to1$ 只在「去程好且回程坏」时保留，概率 $p(1-p)$。
>
> 稳态随之落地。内部比值 $\pi_{x+1}/\pi_x=1$，故 $\pi_0=\pi_1=\cdots=\pi_{n-1}$；边界给出 $\pi_n/\pi_{n-1}=1-p$，由 $\pi_{n-1}p(1-p)=\pi_np$ 得到。归一化时一共 $n+(1-p)$ 份，于是 $\pi_0=\cdots=\pi_{n-1}=1/(n+1-p)$，而 $\pi_n=(1-p)/(n+1-p)$。代 $n=5$、$p=0.3$ 验一遍：每个内部状态 $1/5.7\approx0.1754$，端点 $0.7/5.7\approx0.1228$，六个分量相加为 $1$。
>
> (b) 的两个答案都从这张表里读。去程的坏运气：天好但主屋无杆，即 $X=n$ 且去程好，概率 $p\pi_n=p(1-p)/(n+1-p)$。回程的坏运气：天好但岛上一根也没有，即 $X=0$ 且去程天气坏（否则一定有杆被带上去），概率 $p(1-p)\pi_0=p(1-p)/(n+1-p)$。两条腿答案相同，这不是巧合。
>
> 对称性的来源是 reversibility（时间可逆性）。内部转移已满足细致平衡，端点那一步虽然看上去偏心，但 $n$ 与 $0$ 两处的折减因子恰好抵消了「去程/回程」的差别；若把往返顺序整个倒过来重新建模，稳态分布与 (b) 的数值一字不改。这是检验算错没算错最快的办法：两条腿的答案不相等，就一定有地方漏了「身边必须先是有点杆」这个前提。
>
> 原文有几处要改。它把题目标成「Vincent/Alvin 渔竿题」，而题干里只有 Alvin，Vincent 是凭空添加；它说「天气好就拖一根走」，漏掉「身边得先有杆」这个前提，而这正是 (b) 的全部内容；它也没给出稳态分布与 (b) 的式子，而这道题的价值恰恰就在那两个式子上。
>
> 还有一处计数错误要纠正：它说「把状态错设成两处的杆数，就得到 $2(n+1)$ 个状态的冗余模型」。这不对。若记 $(x,y)$ 为两处的杆数并已知守恒 $x+y=n$，可行取值只有 $n+1$ 组，冗余只是同一状态被两种坐标描述，状态数并没有翻倍；若连守恒都没看出、让 $x,y$ 各自独立取 $0,\ldots,n$，才有 $(n+1)^{2}$ 个候选，其中绝大多数「凭空多杆或少杆」根本不可达。正确说法是：$n+1$ 个状态（守恒），而不是 $2(n+1)$。
>
> 跨课程：这种「总量守恒、只记一处」的建模，与 CSAPP 里的缓冲区计数、与 6.042J 的 birth-death（生灭）链是同一套思路；18.06 的语言里，平稳分布是 $P^{T}$ 属于特征值 $1$ 的特征向量，边界的修正不改特征值、只改特征向量。反例确认建模的敏感：若忘了守恒，会写出「凭空多出一根」的转移，那才是真错；而多记一个坐标只是浪费，不会算错。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中的两个系数在源 OCR 中缺失（只剩 "the same difficulty, and a probability for ... the other two levels of difficulty"），上表 "$0.5$"、"$0.25$" 及 "with equal probability" 依据教材原文权威转录补全；若需最严格原文请回查原书第 7 章 Problem 11。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 12（Alvin 每周六出海钓鱼 —— 天晴才带渔竿，共 $n$ 根）</span>

Alvin likes to sail each Saturday to his cottage on a nearby island off the coast. Alvin is an avid fisherman, and enjoys fishing off his boat on the way to and from the island, as long as the weather is good. Unfortunately, the weather is good on the way to or from the island with probability $p$, independent of what the weather was on any past trip (so the weather would be nice on the way to the island, but poor on the way back). Now, if the weather is nice, Alvin will take one of his $n$ fishing rods for the trip, but if the weather is bad, he will not bring a fishing rod with him. We want to find the probability that on a given leg of the trip to or from the island the weather will be nice, but Alvin will not fish because all his fishing rods are at his other home.

(a) Formulate an appropriate Markov chain model with $n + 1$ states and find the steady-state probabilities.

(b) What is the steady-state probability that on a given trip, Alvin sails with nice weather but without [his] fishing rod?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道 Vincent/Alvin 渔竿题是把「库存转移」问题译成马尔可夫链稳态的经典一幕，妙在「共 $n$ 根渔竿」这个守恒量让状态空间自动剩下 $n+1$ 维。第一性原理：渔竿永远只在「主屋」与「岛上小屋」这两处周转，总数恒为 $n$，所以只要记住其中一处现有多少根即可——例如记 $X$＝岛上小屋的渔竿数，$X\in\{0,\dots,n\}$ 正好 $n+1$ 个状态。天气按概率 $p$ 每次独立独立地「好/坏」，天气好就拖一根走（从一个住处移往另一处），天气坏就不动，这给出一个整齐的「只在相邻状态间跳动、可能停留」的链。答案落在求解稳态分布 $\pi$：平衡方程加上 $\sum\pi=1$ 就解出「各存量配置的长期占比」；而 (b) 问的「天气好却没渔竿」正是「存量在某一端为 $n$（另一端为 $0$）且当天想带却找不着」的重叠事件，把按钮搬到概率表达即可。命名模板：可称为「守恒量截断 / rod-count chain」——凡是「总量守恒、只在一侧计数」的迁移过程都长这样，与酒精分子在两容器间扩散、Erdos–Rényi 坛子对换同构。跨课程（§7.5 生灭/扩散 + Problem 15-16）：桥连兄弟模型的单侧计数正是这里 $n+1$ 状态的原型；稳态分布往往是「各项成几何/二项式」形状，因为每一步只在隔壁状态流动（通量守恒）。反例兜底：若天气不再是独立同分布而是有记忆，状态 $X$ 单独就不够了，还得把「上一程天气」也编进状态——这恰好演示了「马尔可夫状态要装下全部可记忆信息」这条总纪律。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上表依教材原文转录补全：概率 $p$（天晴概率）、"fishing rod/rods" 等词源 OCR 断成 "o n any … o ne of h is n fishing"、"w ill not bring a fishing rod"，均按权威原文还原；题中变量 $p$ 与 $n$（渔竿数目）非臆造，源页确有 "n + 1 states" 字样（对应 OCR 行 "+ 1 states"）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 13 —— 带转移概率图（transition probability graph）的出生-死亡型链例题（前段 (a)–(e)；其 (f)(g) 续于下一页）</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏] 本题源 OCR 仅剩如下可辨认碎片，且多数小题原文与所附转移概率图（图号源 OCR 显示为 "7.22: Transition probability graph for Problem …"）均无法还原，请回查原书。题号「Problem 13」系根据下一页（p395）明确标注为「Problem 13（续）」并给出其 (f)(g) 判断而得：本品为 Problem 13 的前段 (a)–(e)，从而修复了 11→12→13 的题号链。下面仅列出可辨认的字句，不作补全、不臆造转移概率或数值。</span>

- 可辨认碎片：关于 "each state $i$" 与 "the probability that … current state is $i$" 的小问（a）—（b）；
- 可辨认碎片：关于 "the first time the process was in state 2" 以及 "… this change of state was a birth"（即这次状态改变是否为一次"出生"/向上转移）的小问（c）—（e）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 各小题的完整英文原句、转移概率图本身及其上的转移概率数值在源页 OCR 中缺失，故无法给出可读题干；以上仅还原题干所涉关键词，未补全任何数值，请回查原书对应习题页。</span>
<!-- ===== PDF p395 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — 习题区续接（Problems，续）。本页自上方页尾的 **Problem 13** 后半部分起，沿续到 **Problem 18**。

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 13（续）——出生-死亡过程：给定「状态发生改变」时的条件概率（conditional probability given a change of state）**</span>

(f) The conditional probability that the first observed transition is a birth given that it resulted in a change of state.

(g) The conditional probability that the first observed transition leads to state 2, given that it resulted in a change of state.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道出生-死亡链的「条件概率（given a change of state）」把视线从「每一时刻」挪到「每观测到一次状态改变」——这正是连续时间链与embedded chain（嵌入链）的接口。第一性原理：死亡型链从状态 $i$ 出发，每次「确实发生状态改变」的概率是「这次真的动了」；而条件「改变」等价于「这一次观测到的是出生还是死亡」。把自转移 $\lambda_i+\mu_i$ 之外那部分的概率照比例重归一化，就得到「当它动了一次，往上是出生、往下是死亡」的条件分布——瞬时率之比 $\lambda_i : \mu_i$。这组量把离散马尔可夫链里「每步也许停在原地」的闲聊抹掉，只剩「真正跳变」的骨架，正是连续时间链里「在状态 $i$ 停留任意时长后再以速率比选下一个去向」的离散投影。命名模板：可叫「jump chain / 跳变骨架」，凡先给 rate（速率）再定去向的模型都可拆成「时钟 + 转移核」两层，慢速率链就是右侧 $\frac{\lambda_i}{\lambda_i+\mu_i}$ 形式的条件概率。跨课程（§7.5 生灭过程 / 排队论 M/M/1）：排队论里算「到达 vs 服务完成的先后」全是这类「速率比」条件概率；也正好预告了下一节连续时间链条的构造逻辑。反例兜底：若链全是自转移（$p_{ii}=1$），「条件在状态改变上」的概率分布就是空集，量无穷大/未定义——所以这类问题一律要求「存在正概率改变」，这也是（f）（g）都先设「it resulted in a change of state」的用意。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 14**</span>（非周期、单一常返类的马氏链的近似多步转移概率）

Consider a Markov chain with given transition probabilities and with a single recurrent class that is aperiodic. Assume that for $n \geq 500$, the $n$-step transition probabilities are very close to the steady-state probabilities.

(a) Find an approximate formula for $P \left( X_{1000} = j,\, X_{1001} = k,\, X_{2000} = \ell \mid X_0 = i \right)$.

(b) Find an approximate formula for $P \left( X_{1000} = i \mid X_{1001} = j \right)$.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题把「$n$ 步转移概率趋近稳态」这条 §7.3 结论物化成长程联合概率的近似公式，训练你在稳态达成后怎样做「马尔可夫骨架」的拆解。第一性原理：已知对 $n\ge500$，$n$ 步转移概率逼近稳态 $\pi$，所以从 $X_0$ 出发到 $X_{1000}$ 已经「忘了起点」——$P(X_{1000}=j\mid X_0=i)\approx\pi_j$。又因为链只有一步记忆，(a) 里给定 $X_{1001}=k$ 之后，$X_{2000}$ 相对 $X_{1001}$ 又可被稳态近似（999＋步足够），于是联合近似分解为 $P(X_{1000}{=}j,\,X_{1001}{=}k,\,X_{2000}{=}\ell \mid X_0{=}i)\approx \pi_j\, p_{jk}\,\pi_\ell$，中间那一步 $p_{jk}$ 是唯一「还没被稳态吞掉」的精确信息。命名模板：这种「长程处用稳态填空、短缝保留一步转移」的策略可叫「steady-state plug-in / 稳态填空法」，是mixing time（混合时间）之后做长程事件概率的标准招。跨课程（§7.3 收敛定理 + 马尔可夫性的连锁）：它也道出「多步联合概率 ≈ 若干稳态与少量转移的乘积」的直观——链条越长，独立化程度越高；(b) 里用条件概率公式把「给 $X_{1001}=j$ 时的 $X_{1000}$」反过来算，正是可逆/整理时的标准转向，答案近似回到 $\pi_i$ 或相应转移比。反例兜底：假设链在 $n=500$ 才真正收敛；若链是「高耗散/慢混合」，实际混合时间可能远大于 500，这时 $X_{1000}$ 还没到稳态，直接用 $\pi_j$ 填就会错——所以「已知 $n\ge500$ 很近稳态」这一前提是整道题成立的命门，换个慢链它立刻崩。这也是「先估 mixing time、再谈稳态近似」这一工程直觉的由来。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 15**</span>（Ehrenfest 扩散模型，diffusion）

**Ehrenfest model of diffusion.** We have a total of $n$ balls, some of them black, some white. At each time step, we either do nothing, which happens with probability $f$, where $0 < f < 1$, or we select a ball at random, so that each ball has probability $(1-f)/n > 0$ of being selected. In the latter case, we change the color of the selected ball (if white it becomes black, and vice versa), and the process is repeated indefinitely. What is the steady-state distribution of the number of white balls?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Ehrenfest 扩散模型是最早展示「物理系统会自发性地走向均衡分布」的玩具，而本文要求只用马尔可夫链稳态导出它的答案。第一性原理：记状态 $k$＝白球数。每步以 $(1-f)$ 概率随机挑一个球变色：选中白球（$k\to k-1$）的概率 $(1-f)\tfrac{k}{n}$，选中黑球（$k\to k+1$）的概率 $(1-f)\tfrac{n-k}{n}$，其余概率留在原地。直接解 $m+1$ 个未知的线性方程组可行，但更快、也更物理的是用reversibility / detailed balance（可逆性／细平衡）：在稳态下相邻两态之间向上与向下的「概率流」必须相等，即 $\pi_k\cdot (1-f)\tfrac{k}{n} = \pi_{k+1}\cdot (1-f)\tfrac{n-k}{n}$，一递推就得 $\pi_k \propto \binom{n}{k}$——白球数服从 $\mathrm{Bin}(n,\tfrac12)$。命名模板：把「用相邻流的相等反向推出稳态」叫「detailed balance / 细平衡法」，它比解全体平衡方程省力得多，凡是「只在与自己相邻的状态间流动」的链（生灭型）都适用。跨课程（§7.3 平衡方程 + 热力学直觉 + Problem 12/16）：细平衡正是「微观可逆 → 宏观均衡」的骨架，也把本题与生灭过程、以及下一题的 Bernouilli–Laplace 两坛模型连成同一族；自转移概率 $f$ 被巧妙地约掉了，说明留步率不影响均衡分布形状。反例兜底：链并非一定可逆——若「向上」与「向下」不对称到流无法配对，就不存在细平衡，只能回到完整平衡方程 $P\pi=\pi$ 硬解；本题恰是对称、可逆的幸运儿。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 16**</span>（Bernoulli–Laplace 扩散模型，diffusion）

**Bernoulli–Laplace model of diffusion.** Each of two urns contains $m$ balls. Out of the total of the $2m$ balls, $m$ are white and $m$ are black. A ball is simultaneously selected from each urn and moved to the other urn, and the process is indefinitely repeated. What is the steady-state distribution of the number of white balls in each urn?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Bernouilli–Laplace 两坛模型是 Ehrenfest 的「加冕版本」：不再是挑一颗球变色，而是从两个坛同时各抽一颗互换。第一性原理：过程每一步选出的一颗从坛 1 移到坛 2、另一颗反向移回，总数在各坛内守恒；关键的简化是「每个具体的『球配置』都是可逆且等权的」——从配置 $A$ 到配置 $B$ 与从 $B$ 到 $A$ 的互换概率相等，detailed balance（细平衡）成立。于是稳态下每个满分配置概率相同，剩下就是计数：问「坛 1 里有 $k$ 颗白球」的稳态概率，即「在全部 $\binom{2m}{m}$ 种「$m$ 白 $m$ 黑」的颜色分配里，坛 1 恰好买到 $k$ 颗白的占比」——这就是超几何分布。命名模板：把「配置等权 → 稳态就是均匀枚举配置 + 数组合」的路子叫「uniform-configuration 法」；它是玻尔兹曼「各微观态等先验」在离散马尔可夫上的化身。跨课程（§7.5 生灭 / 扩散 + Problem 15 + 组合计数）：本题把「出生-死亡」从单变量 $k\to k\pm1$ 推广到「两坛联动的置换」，但稳态仍由可逆性给出来，与 Ehrenfest 的单侧守恒 $k$ 统计（二项 $\tfrac12$）构成对照：这里多一维调制、是超几何而非二项。反例兜底：若是「各抽一颗但稍不对称」的规则（如抽球概率不等），配置就不再等权、细平衡破裂，超几何答案失效，只能回头解 $\pi P=\pi$ 的大型方程组——对称性一旦松动，简洁稳态立刻蒸发。本题恰恰展示了「对称可逆 → 组合计数直接出头」这条捷径的力量。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 17**</span>（两状态马氏链的转移概率推导与稳态概率）

Consider a Markov chain with two states denoted $1$ and $2$, and transition probabilities

```math
p_{11} = 1 - \alpha, \qquad p_{12} = \alpha, \qquad p_{21} = \beta, \qquad p_{22} = 1 - \beta,
```

where $\alpha$ and $\beta$ are such that $0 < \alpha < 1$ and $0 < \beta < 1$.

(a) Show that the two states of the chain form a recurrent and aperiodic class.

(b) Use induction to show that for all $n$, we have

```math
\begin{aligned}
p_{11}(n) &= \frac{\beta}{\alpha + \beta} + \frac{\alpha}{\alpha + \beta}\,\left(1 - \alpha - \beta\right)^{n},\\[4pt]
p_{12}(n) &= \frac{\alpha}{\alpha + \beta} - \frac{\alpha}{\alpha + \beta}\,\left(1 - \alpha - \beta\right)^{n},\\[4pt]
p_{21}(n) &= \frac{\beta}{\alpha + \beta} - \frac{\beta}{\alpha + \beta}\,\left(1 - \alpha - \beta\right)^{n},\\[4pt]
p_{22}(n) &= \frac{\alpha}{\alpha + \beta} + \frac{\beta}{\alpha + \beta}\,\left(1 - \alpha - \beta\right)^{n}.
\end{aligned}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本小题 (b) 的四条 $n$ 步转移概率公式在源 OCR 中被逐行打散、碎片化（下标、分子分母、$(1-\alpha-\beta)^n$ 幂次均被断行重排），同时原本的转移概率记号也被误读成 `r`。以上按本题已给出的 $p_{ij}$（$p_{11}=1-\alpha$、$p_{12}=\alpha$、$p_{21}=\beta$、$p_{22}=1-\beta$）及两状态马氏链的确定结果重建为规范 LaTeX；各条公式中分子的归属（$\alpha$ 或 $\beta$）与稳态项的分母 $\alpha+\beta$ 均由给定转移矩阵唯一确定，非臆造。若需最严格原文排版，请回查原书页 395。</span>

(c) What are the steady-state probabilities $\pi_{1}$ and $\pi_{2}$?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道两状态题把第 7 章的「宏观结论」落到一条能用手算到底的最简量子上——一条只有两个状态的链，正是所有「谱论引擎」的最佳试验台。第一性原理：转移矩阵 $P=\begin{pmatrix}1-\alpha&\alpha\\ \beta&1-\beta\end{pmatrix}$。求 $n$ 步转移概率 $p_{ij}(n)$ 的标准武器是对角化：$P$ 的特征多项式给出两个特征值 $\lambda_1=1$ 与 $\lambda_2=1-\alpha-\beta$，把它们分别投影到两个特征向量，$P^n$ 便拆成「稳态项（特征值 1 的部分）+ 瞬态项（$\lambda_2^n$ 的部分）」——这正是 (b) 四条公式里那一串 $\tfrac{1-\alpha-\beta}{}^{n}$ 来源。取 $n\to\infty$，瞬态项消失，$p_{ij}(n)\to\pi_j$，稳态 $\pi_1=\tfrac{\beta}{\alpha+\beta},\,\pi_2=\tfrac{\alpha}{\alpha+\beta}$。命名模板：这套「对角化 + 特征值 1 给出稳态、第二特征值给出收敛速率」叫「谱法 / spectral treatment」，其中 $|\lambda_2|=|1-\alpha-\beta|$ 就是 mixing 的收缩因子。跨课程（Strang 18.06/18.065 特征分解 + §7.3 稳态收敛）：任一不可约非周期链 $T_{ij}(n)\to\pi_j$ 都可以照此理解——特征值为 1 的左特征向量是稳态，其余特征值都落在复平面上以 $<1$ 的模，决定收敛快慢；本题正是这门代数的一个两维缩影。反例兜底：若 $\alpha=\beta=0$ 则 $\lambda_2=1$，链退化成两条纯自环、从不可约变成两个分离常返类，「稳态项 vs 瞬态项」的分裂失效，$p_{ij}(n)$ 根本不再收敛到单一分布——这恰好点出「非周期不可约是收敛的前提」这条 §7.3 硬命。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 18**</span>（MIT 停车场门禁的更换频率）

The parking garage at MIT has installed a card-operated gate, which, unfortunately, is vulnerable to absent-minded faculty and staff. In particular, in each day, a car crashes the gate with probability $P$, in which case a new gate must be installed. Also a gate that has survived for $m$ days must be replaced as a matter of periodic maintenance. What is the long-term expected frequency of gate replacements?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 停车场门禁问题是「长期平均更换频率」的经典折算，答案其实是一条「每台门一生平均可服役的天数」的反数。第一性原理：可以用一条「从刚装好的门倒计时其剩余寿命」的马尔可夫链来读——记状态为「这台门已用了 $j$ 天」，每到新一天要么以概率 $P$ 被撞毁、要么再撑一天，到第 $m$ 天即按月保养强制换掉。更换就发生在「这一天的生命周期终了、装下一台新门」的那个时刻。长期看，「每次更换后重新计时」让过程进入一个由「门的使用周期」构成的renewal（再生成）结构：长期更换频率恰好等于「每个周期长度的期望的倒数」$1/(\mathbb{E}[\text{lifetime}]+1)$。这样就不必真的解全体平衡方程，只需算明「每台门平均能用多少天」（等于 $\mathbb{E}[T]$，其中 $T$ 是「要么撞毁要么撑满 $m$ 天」的最小者），频率即为它的倒数。命名模板：可叫「再生频率公式 / renewal-rate 法」——凡「事件发生后从头再算、天然重置」的系统，长期事件率都收敛到周期期望的倒数，这是比「稳态概率 × 转移率」更直观的一招。跨课程（§7.3 稳态频率 + 期望寿命 §7.4 吸收时间 + 排队/可靠性工程）：门的使用寿命建模正是吸收链里「$\mathbb{E}[\text{absorption time}]=$ 平均首达时间」的用武之地；也直接对应马氏链「长期访次率 = 稳态」的 (c)。反例兜底：若把「月保养」与「撞毁」两个终止条件算错（少算了保养当天也算一次服役），周期期望就偏，频率随即偏——这类题最易漏算的就是「服役满 $m$ 天的那天也算一次服役」的边缘情形。

---
<!-- ===== PDF p396 ===== -->
<span style="color:#c0392b;">**第 7 章　马尔可夫链（Markov Chains）** — 习题区（Problems，书页 387）</span>

> <span style="color:#7f8c8d;">承接上文：本页位于第 7 章章末 Problems 习题区，开启新题 Problem 19（Markov chain 稳态收敛 Standstill convergence 等证明）。本页题解 Solution 已开始但（a）小题接续到下一页，故有「续」。书页印号 387（PDF p396）。</span>
>
> <span style="color:#7f8c8d;">本篇 O3 局部 OCR 损伤：原文多处将 n 步转移概率 $T_{ij}(n)$ 错读为「Tij (n)」，将判断将 $\lim_{n\to\infty}$ 拆成断行的「nlim … -+oc」，将 $\gamma$ 错读为「'y」，将 $\beta$ 错读为「{3」。以下已按第 7 章标准记号恢复；凡显示式为原文缺失（OCR 留空）之处皆以灰注释标明。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 19（\* 稳态收敛，Steady-state convergence）**</span>

Consider a Markov chain with a single recurrent class, and assume that there exists a time $n$ such that

```math
T_{ij}(n) > 0,
```

for all $i$ and all recurrent $j$. (This is equivalent to assuming that the class is aperiodic.) We wish to show that for any $i$ and $j$, the limit

```math
\lim_{n \to \infty} T_{ij}(n)
```

exists and does not depend on $i$. To derive this result, we need to show that the choice of the initial state has no long-term effect. To quantify this effect, we consider two different initial states $i$ and $k$, and consider two independent Markov chains, $X_n$ and $Y_n$, with the same transition probabilities and with $X_0 = i$, $Y_0 = k$. Let $T = \min\{n \mid X_n = Y_n\}$ be the first time that the two chains enter the same state.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问把「从不同初始状态出发的两条同参数链，最终是否『吞并』成同一条」转化成一个可量化的事件——它们的相遇时间 $T$。第一性原理：既然两条链从事后相遇点之后拥有完全相同的一步转移规则，那么从相遇那一刻起它们「永远并列而行」，任何未来走位都一致；因此「$X_n$ 与 $Y_n$ 落在同一状态」这件事，其分布差完全被「还没相遇」($T>n$) 的几何上界所控制。剩下要做的，是给 $T$ 的长尾找个几何上界：由于常返类不可约非周期，存在某个状态 $\ell$ 和一个固定窗口 $n$，使两链在同一个窗里同时落进 $\ell$ 的概率至少 $\beta^2>0$，于是每个长度 $n$ 的窗「都错过」的概率被一个固定因子 $1-\beta^2$ 累积压低，得到 $P(T>kn)\le(1-\beta^2)^k\le c\gamma^{kn}$。命名模板：这就是「coupling（耦合）法」的骨架，用它可给出「total variation（全变差）距离$\le P(T>n)$」这类衡量两链分布贴近度的最干净上界。跨课程（§7.3 收敛定理 + 概率收敛速率）：耦合是现代马氏链「混合速度」证明的标准武器——两条链能相遇 ⇔ 分布充分趋同；本题正是它在手工层面的演示。反例兜底：若链是周期的（如相绕而行的对位），两链会永远「恰好错过」，相遇时间没有几何尾巴，$P(T>n)$ 变得很慢——这印证了「非周期」在本题假设里不可省。

(a) Show that there exist positive constants $c$ and $\gamma < 1$ such that

```math
P(T > n) \le c\,\gamma^{n}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (a) 的目标显示式在源页留空（该式原文为一整块显示式，OCR 未识别出内容）。上式 $P(T > n) \le c\gamma^n$ 为按本小题题意、以及(c)(e)的提示（{T>n} 与 {T≤n} 两个事件、与 $c\gamma^n$ 同形的界）补全的标准形式；参数 $c$、$\gamma$ 为泛指常量，未涉及具体数值。</span>

(b) Show that if the states of the two chains became equal by time $n$, their occupancy probabilities at time $n$ are the same, that is,

```math
P(X_n = j \mid T \le n) = P(Y_n = j \mid T \le n).
```

(c) Show that $\bigl| T_{ij}(n) - T_{kj}(n) \bigr| \le c\,\gamma^{n}$, for all $i$, $j$, $k$, and $n$. Hint: Condition on the two events $\{T > n\}$ and $\{T \le n\}$.

(d) Let $\bar{q}_j(n) = \max_i T_{ij}(n)$ and $\underline{q}_j(n) = \min_i T_{ij}(n)$. Show that

```math
\bar{q}_j(n) - \underline{q}_j(n) \le c\,\gamma^{n}
```

for all $n$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] (d) 所求显示式在源页留空。上式「$\bar{q}_j(n) - \underline{q}_j(n) \le c\gamma^n$（上标的 j ——下标的 j 之差受 $c\gamma^n$ 控制）」为按(e)的提示（要求 (c)、(d) 合起来能推出 $\bar{q}_j(n)$ 与 $\underline{q}_j(n)$ 收敛到同一极限）补全的标准形式；符号 $\bar{q}_j(n)$ 与 $\underline{q}_j(n)$ 分别对应 OCR 中的两个「qj (n)」（按题干说明为 max 与 min）。</span>

(e) Show that the sequence $T_{ij}(n)$ converges to a limit that does not depend on $i$. Hint: Combine the results of parts (c) and (d) to show that the two sequences $\bar{q}_j(n)$ and $\underline{q}_j(n)$ converge and have the same limit.

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）**. (a) The argument is similar to the one used to bound the PMF of the time until a recurrent state is entered (Problem 7). Let $\ell$ be some recurrent state and let $\beta = \min_i T_{i\ell}(n) > 0$. No matter what is the current state of $X_n$ and $Y_n$, there is a probability of at least $\beta^2$ that both chains are at state $\ell$ after $n$ time steps. Thus,

```math
P\bigl(T > (k+1)n \mid T > kn\bigr) \le 1 - \beta^{2}.
```

Similarly, by repeated application of this bound,

```math
P(T > kn) \le (1-\beta^{2})^{k},
```

and hence there exist constants $c$ and $\gamma < 1$ such that

```math
P(T > m) \le c\,\gamma^{m},
```

for all $m$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Solution 中「Thus」「Similarly」「and」之后的三个显示式均在源页留空（OCR 未识别）。以上按源页已给出的 $\beta = \min_i T_{i\ell}(n) > 0$ 与「…至少 $\beta^2$ 的概率」补全标准几何衰减论证；$\beta^2$、$(1-\beta^2)^k$ 均为由已知 $\beta$ 推导出的泛指结构，未臆造具体数值。题解自本页起，继续到下一页，故标注「续」。</span>

<!-- 本页末尾，Solution (a) 未完，续接下页（书页 388 / PDF p397）。 -->
<!-- ===== PDF p397 ===== -->

<span style="color:#2471a3;">**[solution]**</span>  <span style="color:#c0392b;">Solution of Problem 19.\*（续）—— 稳态收敛（Steady-State Convergence）</span>

> <span style="color:#7f8c8d;">承接上一页（p396）。本页为带 `*` 题 Problem 19（稳态收敛，Steady-State Convergence）英文 Solution 与题干小问的**续接**：页首续讲 (a) 的收尾并给出常数形式，随后依次完成 (b)、(c)、(d)。标 `*` 题其行内 Solution 按规范保持英文，仅标签可标注中文。</span>

This implies that

```math
P(T > n) \le c\,\gamma^n,
```

where $\gamma = \bigl(1 - \beta^{2}\bigr)^{1/n}$, and $c = 1\big/\bigl(1 - \beta^{2}\bigr)^{1/n}$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 首行 "This implies that P(T　n)　er^n" 中的不等号与 `c` 后紧跟的 `γ`（小写 gamma，被误读为小写 r）均被打散为替换符；按其上下文（与 (c) 尾部结论 **P(T>n) ≤ cγ^n** 一致）复原为 `P(T > n) \le c\gamma^n`。次行 `'Y` 读作 γ，`(32` 读作 β²，括号后的上标 `I/n` 与 `'n` 均按其形读作 $^{1/n}$，故下式的底数/指数以本页源 OCR 为准，未作改动。</span>

**(b)** We condition on the possible values of $T$ and on the common state $\ell$ of the two chains at time $T$, and use the total probability theorem. We have

```math
P(X_n = j \mid T \le n)
= \sum_{t=0}^{n} \sum_{\ell=1}^{m} P\bigl(X_n = j \mid T = t,\; X_t = \ell\bigr)\, P\bigl(T = t,\; X_t = \ell \mid T \le n\bigr)
```

```math
= \sum_{t=0}^{n} \sum_{\ell=1}^{m} P\bigl(X_n = j \mid X_t = \ell\bigr)\, P\bigl(T = t,\; X_t = \ell \mid T \le n\bigr)
```

```math
= \sum_{t=0}^{n} \sum_{\ell=1}^{m} T_{\ell j}(n - t)\, P\bigl(T = t,\; X_t = \ell \mid T \le n\bigr).
```

Similarly,

```math
P(Y_n = j \mid T \le n)
= \sum_{t=0}^{n} \sum_{\ell=1}^{m} T_{\ell j}(n - t)\, P\bigl(T = t,\; Y_t = \ell \mid T \le n\bigr).
```

But the events $\{T = t, X_t = \ell\}$ and $\{T = t, Y_t = \ell\}$ are identical, and therefore have the same probability, so that $P(X_n = j \mid T \le n) = P(Y_n = j \mid T \le n)$.

**(c)** We have

```math
T_{ij}(n) = P(X_n = j) = P(X_n = j \mid T \le n)\, P(T \le n) + P(X_n = j \mid T > n)\, P(T > n)
```

and

```math
T_{kj}(n) = P(Y_n = j) = P(Y_n = j \mid T \le n)\, P(T \le n) + P(Y_n = j \mid T > n)\, P(T > n).
```

By subtracting these two equations, using the result of part (b) to eliminate the first terms in their right-hand sides, and by taking the absolute value of both sides, we obtain

```math
\bigl|\,T_{ij}(n) - T_{kj}(n)\,\bigr|
\ \le\ \Bigl|\,P(X_n = j \mid T > n)\, P(T > n) - P(Y_n = j \mid T > n)\, P(T > n)\,\Bigr|
```

```math
\le\ P(T > n)
```

```math
\le\ c\,\gamma^{n}.
```

**(d)** By conditioning on the state after the first transition, and using the total probability theorem, we have the following variant of the Chapman–Kolmogorov equation:

```math
T_{ij}(n + 1) = \sum_{k=1}^{m} p_{ik}\, T_{kj}(n).
```
<!-- ===== PDF p398 ===== -->
<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 19（续）—— n 步转移概率上下界序列的单调性与收敛（monotonicity and convergence of the lower/upper bound sequences）**</span>

> 承接上一页 Problem 19（第 7 章习题区的校核,Proof 型解答）：本页开头是该题解答（Solution）的中部，证明由 n 步转移概率 $T_{ij}(n) = P(X_n = j \mid X_0 = i)$ 递归得到的下、上界序列 $q_j(n)$ 与 $\bar q_j(n)$ 的单调性，并由此推出 $T_{ij}(n)$ 收敛且极限与 $i$ 无关（该结论为下一页 Problem 20 所调用）。习题区题干/解答遵循规范保留英文原题,此处照录。

（接上文，part (d) 中段）

Using this equation, we obtain

```math
\bar q_j(n+1) = \max_{i} T_{ij}(n+1)
= \max_{i} \sum_{k=1}^{m} p_{ik}\, T_{kj}(n)
\le \max_{i} \sum_{k=1}^{m} p_{ik}\, \bar q_j(n)
= \bar q_j(n).
```

The inequality $q_j(n) \le q_j(n+1)$ is established by a symmetrical argument (the same reasoning applied to the lower bound). The inequality $q_j(n+1) \le \bar q_j(n+1)$ is a consequence of the definitions.

(e) The sequences $q_j(n)$ and $\bar q_j(n)$ converge because they are monotonic. The inequality $|\,T_{ij}(n) - T_{kj}(n)\,| \le c\gamma^n$, for all $i$ and $k$, implies that $\bar q_j(n) - q_j(n) \le c\gamma^n$. Taking the limit as $n \to \infty$, we obtain that the limits of $q_j(n)$ and $\bar q_j(n)$ are the same. Let $\pi'_j$ denote this common limit. Since $q_j(n) \le T_{ij}(n) \le \bar q_j(n)$, it follows that $T_{ij}(n)$ also converges to $\pi'_j$, and the limit is independent of $i$.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这是整份「稳态收敛定理」的收官一步，靠的是单调有界加两面对夹（sandwich/挤压）。第一性原理：定义随初始状态变化的上下包络 $\bar q_j(n)=\max_i T_{ij}(n)$ 与 $\underline q_j(n)=\min_i T_{ij}(n)$——所谓「从任一状态出发的尽量好与尽量差」。配合 Chapman–Kolmogorov 的向前一步 $T_{ij}(n+1)=\sum_k p_{ik}T_{kj}(n)$，可证上包络单调不增、下包络单调不减（把 $\max/\min$ 之后再做线性组合仍被包络框住）；而两条单调有界序列必收敛，加之 (c) 得到的包络间距被 $c\gamma^n$ 压到 0，故两包络收敛于同一极限 $\pi'_j$。真正的 $T_{ij}(n)$ 被上下包络夹住，自然也被逼到同一个 $\pi'_j$——且极限对 $i$ 统一，这正是「稳态与起点无关」的总根源。命名模板：把「用单调包络收敛 + 夹逼定极限」叫「squeeze / 夹逼证法的马尔可夫版」，是证明 $\lim T_{ij}(n)$ 存在且与 $i$ 无关的标准招数。跨课程（§7.3 稳态收敛 + 实数完备性夹逼 + Strang 谱论）：单调有界 + 间距压零这两件套，几乎是所有马氏链收敛定理的通用引擎；(c) 的几何间距正是「第二特征值收缩」在概率层的表现。反例兜底：若链是周期的，上下包络不夹到一点而在两值间振荡，$T_{ij}(n)$ 不再收敛，只在循环子类上摆动——这解释了为何周期性破坏「极限存在」，使收敛只能以Cesàro（切萨罗）平均意义达成。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 页首 part (d) 的中段「Using this equation, we obtain」及其后的极大化推导在 OCR 中被切分得较碎（上下界记号 $\bar q_j$、求和下标、以及末项 $= \bar q_j(n)$ 的归类均受影响）。上面依据「末项回落到 $\bar q_j(n)$」这一可辨认关系，将退化为 $\max_{i}\sum_k p_{ik}\, T_{kj}(n) \le \max_{i}\sum_k p_{ik}\,\bar q_j(n) = \bar q_j(n)$ 的等价形式还原。part (e) 的界 $c\gamma^n$ 系将源 OCR 的碎片 `e,n`/`ern` 按上下文（即 part (c) 的几何界 $c\gamma^n$，$c>0$、$\gamma<1$）辨识复原，是随 $n$ 呈指数衰减的几何界而非 $\varepsilon_n$ 形式的量。若需逐字原文，请回查原书页 398 首段。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 20　\* （平衡方程组解的唯一性，Uniqueness of Solutions to the Balance Equations）**</span>

Consider a Markov chain with a single recurrent class, plus possibly some transient states.

(a) Assuming that the recurrent class is aperiodic, show that the balance equations together with the normalization equation have a unique nonnegative solution.

Hint: Given a solution different from the steady-state probabilities, let it be the PMF of $X_0$ and consider what happens as time goes to infinity.

(b) Show that the uniqueness result of part (a) is also true when the recurrent class is periodic.

Hint: Introduce self-transitions in the Markov chain, in a manner that results in an equivalent set of balance equations, and use the result of part (a).

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答，`* 题解答保持英文原题）.****

(a) Let $\pi'_1, \ldots, \pi'_m$ be the steady-state probabilities, that is, the limits of the $T_{ij}(n)$. These satisfy the balance and normalization equations. Suppose that there is another nonnegative solution $\pi''_1, \ldots, \pi''_m$. Let us initialize the Markov chain according to these probabilities, so that $P(X_0 = j) = \pi''_j$ for all $j$. Using the argument given in the text, we obtain $P(X_n = j) = \pi''_j$ for all times. Thus,

```math
\pi''_j = \lim_{n \to \infty} P(X_n = j).
```

Since by Problem 19 every entry $T_{ij}(n)$ converges to the common steady-state value $\pi'_j$ (the limit being independent of $i$), we obtain $\pi''_j = \pi'_j$ for all $j$. Hence the nonnegative solution of the balance and normalization equations is unique.

(b) Consider a new Markov chain, whose transition probabilities $\bar p_{ij}$ are given by

```math
\bar p_{jj} = (1-\alpha) p_{jj} + \alpha, \qquad \bar p_{ij} = (1-\alpha) p_{ij} \quad \text{for } i \neq j,
```

where $\alpha$ is a number satisfying $0 < \alpha < 1$. The balance equations for the new Markov chain take the form

```math
\pi'_j = \pi'_j \big((1-\alpha) p_{jj} + \alpha\big) + \sum_{i\neq j} \pi'_i (1-\alpha) p_{ij}.
```

(收尾论证继续于下一页——本页截此。)

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 20(b) 中新链转移概率仅清晰给出对角项 $\bar p_{jj} = (1-\alpha) p_{jj} + \alpha$，非对角项 $\bar p_{ij} = (1-\alpha)p_{ij}$（$i \neq j$）系依据随后的平衡方程中 $\sum_{i \neq j}\pi'_i(1-\alpha)p_{ij}$ 这一项反推补充，构成一列合法的概率转移矩阵描述；$\alpha$ 为满足 $0<\alpha<1$ 的常数。本页结束于所得新平衡方程处，其「与原方程组等价」的收尾论证在下一页给出。</span>
<!-- ===== PDF p399 ===== -->

> <span style="color:#7f8c8d;">[承接上一页]　本页开头为上一页末尾证明/推导的延续：讨论将原链改造成非周期（aperiodic）链后，稳态方程解的唯一性。页首无新 Sec./无新标题，故标「（续）」。随后进入第 7 章习题区（Problems）的 Problem 21（带 `*` 的高阶题）。</span>

<span style="color:#2471a3;">**[equation]**</span> 或写作（or）

```math
(1-\alpha)\, \pi_j = (1-\alpha)\sum_{i=1}^{m} \pi_i\, p_{ij}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏]　原式第 6 行 OCR 为 `( 1 - O: )7rj = ( 1 - 0: )`（`α` 被误读为 `O:`，`π_j` 被误读为 `7rj`），第 12 行 `L 7riPij` 为 $\sum_{i=1}^{m}\pi_i p_{ij}$。上面按原意补齐为规范式，未引入任何新数值或系数。</span>

这些方程与原链（original chain）的平衡方程（balance equations）等价。注意新链是非周期的（aperiodic），因为自转移（self-transitions）具有正概率。这便确立了新链解的唯一性，并由此推出原链的解也同样唯一。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问把「稳态解唯一」提升成了「无论周期与否都成立」的普适结论，技巧是在原链上「每个状态都补一条self-loop（自环）增肥」，把它变成非周期的那把保护伞。第一性原理：(a) 的直达路径是「把一个（非周期的）解当作初始分布，让链跑无穷久」——若 $\pi''$ 是平衡方程的解，把它摊到 $X_0$ 上，则链处处保持在 $\pi''$；另一方面由 Problem 19，从任何态出发 $T_{ij}(n)$ 都收敛到公共稳态 $\pi'$，故 $\lim P(X_n=j)=\pi'_j$，把两种说法拼起来就得到 $\pi''=\pi'$。(b) 处理周期情形：周期会让有效转移时间被 $d$ 整除而无法逐点收敛，但给每个状态补一条概率 $\alpha>0$ 的自环后，新链仍满足同一组平衡方程、却变成非周期（gcd 立即为 1）；对这条非周期新链套用 (a) 的唯一性，再读回平衡方程，原链的解也唯一。命名模板：把「用自环打散周期却不扰动平衡方程」叫「lazy(ization) / 惰化或自环增肥」——给它建模的成本是少换概率、多换可证性。跨课程（§7.2 周期 + §7.3 稳态 + 随机游走惰化）：给每条边加自环是谱论与马尔可夫蒙特卡洛加速的惯用手段，既有 Strang 谱论的投影味道，也呼应 Problem 17 两状态里「自环把 $\lambda_2$ 拉回 $\le 1$」的思路。反例兜底：若是「两个互相不可达的常返类」，即便增肥自环也救不回来——平衡方程会在两类之间给出任意配比的解，唯一性天然失效；所以「单一常返类」这一前提是 (a)(b) 共同的生命线。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 21（期望长期频率解释，带 `*`）</span>

**Problem 21. \*** **Expected long-term frequency interpretation.** Consider a Markov chain with a single recurrent class which is aperiodic. Show that

```math
\pi_j = \lim_{n\to\infty} \frac{V_{ij}(n)}{n},
\qquad \text{for all } i,\, j = 1, \ldots, m,
```

where the $\pi_j$ are the steady-state probabilities, and $V_{ij}(n)$ is the expected value of the number of visits to state $j$ within the first $n$ transitions, starting from state $i$. **Hint:** Use the following fact from analysis. If a sequence $a_n$ converges to a number $a$, the sequence $b_n$ defined by $b_n = (1/n) \sum_{k=1}^{n} a_k$ also converges to $a$.

<span style="color:#2471a3;">**[solution]**</span> **Solution.** We first assert that for all $n$, $i$, and $j$, we have

```math
V_{ij}(n) = \sum_{k=1}^{n} T_{ij}(k).
```

To see this, note that $V_{ij}(n) = \sum_{k=1}^{n} E\!\left[ I_k \mid X_0 = i \right]$, where $I_k$ is the random variable that takes the value $1$ if $X_k = j$, and the value $0$ otherwise, so that

```math
E\!\left[ I_k \mid X_0 = i \right] = T_{ij}(k).
```

Since

```math
\frac{V_{ij}(n)}{n} = \frac{1}{n} \sum_{k=1}^{n} T_{ij}(k),
```

and $T_{ij}(k)$ converges to $\pi_j$, it follows that $V_{ij}(n)/n$ also converges to $\pi_j$, which is the desired result.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问给稳态概率补上了「长期频率」的直觉尾巴：$\pi_j$ 不只是「长时间后落在状态 $j$ 的概率」，更是「每步平均造访 $j$ 多少次」在统计意义上的极限。第一性原理：定义 $V_{ij}(n)=\mathbb{E}[\text{前 }n\text{ 步造访 }j\text{ 的次数}\mid X_0=i]$。由于「造访次数」是各时刻指示函数之和 $\sum_{k=1}^n \mathbb{E}[I_k]$，而 $\mathbb{E}[I_k]=T_{ij}(k)$（单步概率的线性期望），所以 $V_{ij}(n)=\sum_{k=1}^n T_{ij}(k)$。左右同除 $n$ 得 $V_{ij}(n)/n=\tfrac1n\sum_{k=1}^n T_{ij}(k)$——这恰是 $\{T_{ij}(k)\}$ 的 Cesàro 平均。既然 $T_{ij}(k)\to\pi_j$（据 Problem 19），Cesàro 平均也收敛到同一极限（提示里那条分析事实），于是 $\pi_j=\lim V_{ij}(n)/n$。命名模板：把「用时间均值解释稳态」叫「long-run frequency / 长期访次率」；它和「空间均值」共同构成ergodic（遍历性）直觉的两面。跨课程（§7.3 稳态 + 大数定律 + 分析 Cesàro 求和）：这正是弱大数定律在马尔可夫不独立的场合的翻版——指标虽相关，但平均照旧收敛，Cesàro 事实替我们把「逐点趋稳」升级成「时间平均趋稳」。反例兜底：若链是周期的，$T_{ij}(n)$ 本身不收敛、只在若干值间振荡，此时单侧极限失效，可 Cesàro 平均 $V_{ij}(n)/n$ 仍收敛到 $\pi_j$——这就是「周期链也谈稳态但这必须按平均意义读」的精确理由，Problem 19 里那道坎在此被绕开。

For completeness, we also provide the proof of the fact given in the hint, and which was used in the last step of the above argument. Consider a sequence $a_n$ that converges to some $a$, and let $b_n = (1/n) \sum_{k=1}^{n} a_k$. Fix some $\epsilon > 0$. Since $a_n$ converges to $a$, there exists some $n_0$ such that $a_k \le a + (\epsilon/2)$, for all $k > n_0$. Let also $c = \max_k a_k$. We then have

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏]　该行下方用于估计 $b_n \le \tfrac{1}{n}\sum_{k=1}^{n_0} a_k + a + \tfrac{\epsilon}{2}$ 的不等式公式在 OCR 中残缺/缺失（原式为对上界取 split 分解的推导），按上文语义补出占位，精确式样请回查原书页 399。</span>

The limit of the right-hand side, as $n$ tends to infinity, is $a + (\epsilon/2)$. Therefore, there exists some $n_1$ such that $b_n \le a + \epsilon$, for every $n \ge n_1$. By a symmetrical argument, [本页于此处截止，证明在下页 p400 续接。]

---

> <span style="color:#7f8c8d;">§7 章末 Problems，Problem 21（续）见 p400。</span>
<!-- ===== PDF p400 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — 习题区（Problems，续）— 第 7 章末页

> <span style="color:#7f8c8d;">本页处于第 7 章章末习题区，承接前一页：页首是上一题（含收敛论证的证明题）解答（Solution）的尾部，随后为 Problem 22*（双随机 doubly stochastic 矩阵）。本页末尾为 Problem 22* 解答（c）小问的中段，翻页到下一张（p401）继续。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">（续）上一题解答（Solution）收尾</span>

> <span style="color:#7f8c8d;">此为前一页某问题解答的收尾段（承接上页，讲述序列 $b_n$ 收敛到 $a$ 的证明）。沿用英文解答原文。</span>

there exists some $n_2$ such that $|b_n - a| < \varepsilon$, for every $n \ge n_2$. We have shown that for every $\varepsilon > 0$, there exists some $n_3$ (namely, $n_3 = \max\{n_1, n_2\}$) such that $|b_n - a| \le \varepsilon$, for all $n \ge n_3$. This means that $b_n$ converges to $a$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 22\* —— doubly stochastic（双随机）矩阵</span>

> 题干保持英文原题，仅冒号下方说明本页为第 7 章最后一题（其后习题区收束）。

Consider a Markov chain with a single recurrent class which is aperiodic, and whose transition probability matrix is doubly stochastic, i.e., it has the property that the entries in any column (as well as in any row) add to unity, so that

```math
\sum_{i=1}^{m} p_{ij} = 1, \qquad j = 1, \ldots, m.
```

(a) Show that the transition probability matrix of the chain in Example 7.7 is doubly stochastic.

(b) Show that the steady-state probabilities are

```math
\pi_j = \frac{1}{m}, \qquad j = 1, \ldots, m.
```

(c) Suppose that the recurrent class of the chain is instead periodic. Show that $\pi_1 = \cdots = \pi_m = 1/m$ is the unique solution to the balance and normalization equations. Discuss your answer in the context of Example 7.7 for the case where $m$ is even.

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#00838f;">**[解答] Solution（英文原文）**</span>

因为本题带 `*`，其解答（Solution）保持英文原文，仅标签标注中文。

**(a)** Indeed the rows and the columns of the transition probability matrix in this example all add to $1$.

**(b)** We have

```math
\sum_{i=1}^{m} \frac{1}{m}\, p_{ij} = \frac{1}{m} \sum_{i=1}^{m} p_{ij} = \frac{1}{m}.
```

Thus, the given probabilities $\pi_j = 1/m$ satisfy the balance equations and must therefore be the steady-state probabilities.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> doubly stochastic（双随机）矩阵给全章画了个完美的句号：若每列（自然也包括每行）概率之和都为 1，那么均匀分布 $\pi_j=1/m$ 自动满足平衡方程。第一性原理：把 $\pi_j=1/m$ 代进平衡方程右端，$(1/m)\sum_i p_{ij}=(1/m)\cdot(\text{第 }j\text{ 列之和})=(1/m)$，正是左端 $\pi_j$——「此列和为 1」这一结构直接让均匀分布变成不动点；再叠加 Problem 20 的唯一性（单一不可约常返类且已非周期），这个解就是唯一稳态。(c) 即便常返类变成周期，均匀解仍是平衡方程＋归一化的唯一解：取一个取到最大值的 $q=\pi_j$，由平衡方程和列和为 1 推出所有用到 $\le$ 都得变成等号，进而沿正概率路径把 $q$ 传遍整个常返类。命名模板：把「列和也是 1 → 稳态是均匀分布」叫「doubly stochastic ⇒ uniform steady state」；正则图、以及每步等概率挑一邻点的链（如 Example 7.7 随机游走）都满足。跨课程（Strang 18.06 谱论 + 图论正则图 + PageRank）：双随机正是「转移矩阵 $P$ 每个行与列和都是 1 ⇔ $\mathbf{1}^\top$ 同时是左、右特征向量」，均匀分布就是左特征向量 $\mathbf 1$ 归一化所得；这也在暗中呼应网页 PageRank 里「每行归一化是不均匀、每列也归一则均匀」的分野。反例兜底：若某列和 <1（信息在列方向「泄漏」），均匀分布就被打破，稳态偏向「入流多」的那列对应的状态——把「漏列」vs「保列」对照，就能看清均匀性完全来自「列守恒」，这也是 (c) 里要检查列和的用意。

**(c)** Let $(\pi_1, \ldots, \pi_m)$ be a solution to the balance and normalization equations. Consider a particular $j$ such that $\pi_j \ge \pi_i$ for all $i$, and let $q = \pi_j$. The balance equation for state $j$ yields

```math
q = \pi_j = \sum_{i=1}^{m} \pi_i\, p_{ij} \le q \sum_{i=1}^{m} p_{ij} = q,
```

where the last step follows because the transition probability matrix is doubly stochastic. It follows that the above inequality is actually an equality and

```math
\sum_{i=1}^{m} \pi_i\, p_{ij} = \sum_{i=1}^{m} q\, p_{ij}.
```

Since $\pi_i \le q$ for all $i$, we must have $\pi_i\, p_{ij} = q\, p_{ij}$ for every $i$. Thus, $\pi_i = q$ for every state $i$ from which a transition to $j$ is possible. By repeating this argument, we see that $\pi_i = q$ for every state $i$ such that there is a positive probability path from $i$ to $j$. Since all states are recurrent and belong to the same class, all states $i$ have this property,

> <span style="color:#7f8c8d;">本页至此结束，句意在中途截断（「all states $i$ have this property, …」），接续下一张 p401。</span>
