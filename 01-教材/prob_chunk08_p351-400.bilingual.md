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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 马尔可夫性质是全章的引擎，但最容易被误读成「与过去独立」——它恰恰相反，允许任意强烈的过去依赖，只要求把这份依赖**压进当前状态**。Example 7.2 的蜘蛛与苍蝇正是标本：苍蝇每一步走向只由当前位置与那固定的 0.3/0.3/0.4 规则决定，从前的轨迹全被遗忘。第一性原理：状态就是给历史划等价类的栅栏，落进同一格的几条历史对链的未来不可区分，才能用单个状态无损顶替整段过往，当前状态于是成为过去的「充分统计量」（sufficient statistic）。命名模板：正因为「只看现在」、未来对过去只剩这一条管道，这才叫 Markov chain。跨课程（CSAPP 状态机 + 6.042J 等价关系）：这与「用有限状态摘要代替整段内存历史」同构，也承自等价类分划思想。反例：若把性质错念成「与过去独立」，会马上对 Example 7.1 那种「随时跟得上/落后」相互纠缠的两状态链失算——不依赖不等于没依赖，而是「有依赖，但只剩通过现在这一层薄壁」。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 转移概率矩阵 $P$ 是第 7 章与线性代数之间最顺滑的桥。它每行之和为 $1$（行随机矩阵），正好对应「从任何当前状态出发，下一步必落在 $m$ 个状态之一」；把分布写成行向量 $\mathbf{p}_{n+1}=\mathbf{p}_n P$，那么 n 步转移就是 $\mathbf{p}_n=\mathbf{p}_0 P^n$。第一性原理：$P$ 不必对称也不必可对角化，但行和为 1 在谱意义上保证「最大特征值 1、对应一个不变分布」，这正是后面稳态存在的根。命名模板：所谓 transition probability matrix，不过是把「从 i 到 j 的概率」这个二元函数按行 i、列 j 摊成一张表，matrix（矩阵）之名就是这样一张编号表。跨课程（Strang 18.06 / 18.065）：这就是线性代数里「矩阵乘向量=线性组合」在概率里的落地；但要盯紧记号契约——本课用行随机矩阵、行向量左乘 $\mathbf{p}_{n+1}=\mathbf{p}_n P$，而某些别的教材/语境常用列随机矩阵、列向量右乘，方向一反之稳态取法就对调。反例：哪一行和若不为 1（非随机矩阵），链的「总机会」就会泄漏，$\mathbf{p}_n$ 不再成分布——行和为 1 是模型自洽的生命线。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一页揭示了马尔可夫链概率的「积性（product form）」结构：一条状态序列的联合概率，等于初始概率乘上沿途每一条转移概率的连乘积。第一性原理：链式法则本要把每一步都条件化在整段历史上 $P(X_n=i_n\mid X_0,X_1,\ldots,X_{n-1})$，而马尔可夫性把这些高维条件一律压成「只看上一状态」的一步条件 $p_{i_{n-1}i_n}$，历史于是从联乘中被逐层剥掉，只剩一条由弧权组成的乘积。命名模板：这条序列对应图上一条有向路径，正因此我们才会在 John Duchi / CS229 的自回归模型里见到同样的分解——「路径概率等于边权之积」，而在图论里它就是「路径计数/路径概率的连乘版本」。跨课程（6.042J 图 + 概率条件部分）：事件「走了某条路径」是图上的一条具体路径，全体样本点正是列完所有路径，所以算任意事件只需把构成该事件的路径概率求和——这为 §7.4 用线性方程而非穷举全部轨道来计算吸收概率埋下了伏笔。反例最能暴露边界：若转移概率还依赖于更久远的历史（哪怕只是「前两步」），连乘式每步都要换成更高阶条件概率，乘积形态立刻崩塌，这就是为什么用「只看现在」作唯一支点如此关键。

---

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页中段若干过渡文字（如 "…we have…models. In…"、"So the state $X_0$ is…" 及其前后衔接）在 OCR 中被打散成碎片，仅能辨认出零散短语；上方马尔可夫性的支解证法、图形解释与末尾「规定初始状态概率律」为按下行文意的连贯转写。以下尾部一小段（涉及具体概率计算）正文在 OCR 中残损严重，仅左侧状态序列字面可辨。</span>

---

关于我们的状态序列，需要对**固定初始状态的条件化（conditioning on a fixed initial state）**给出说明。要对整个过程有一个完整的概率描述，我们还需要为初始状态 $X_0$ 规定一个概率律（probability law），即一组初始概率（initial probabilities）$P(X_0 = i)$（针对所有状态 $i$）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这里传达的是马尔可夫链的「完整配方」：一条马尔可夫链 = 初始分布（initial distribution）+ 转移概率矩阵 $P$，二者一旦给定，任何事件（任何长度、任何片段）的概率就可由上一页的连乘法则 直接计算。第一性原理：马尔可夫性把「无穷长历史的依赖」压缩成两类数据——「从头开始的分布」和「相邻两步之间的转移」；投影言之，$P(X_n=j)$ 就是从初始分布出发、左乘 $n$ 次 $P$ 得到的第 $j$ 个分量 $\mathbf{p}_0 P^n$。命名模板：initial probabilities 强调「0 时刻的那一刻」是过程唯一的自由度来源，其余一切都被转移矩阵接管。跨课程（CSAPP 状态机 + 有限自动机）：这与「有限自动机的初态 + 转移函数 唯一刻画行为」完全同构，也与线性代数里「初值 + 线性演化算子」决定轨迹的想法一脉相通。反例：若初始分布取错（比如把 $\pi$ 误当初始分布），那么就算转移矩阵全对，「从 $X_0$ 起的未来分布」也会整体偏移——初始分布装的是「从哪儿开始」，平稳分布装的是「终将到哪儿」，二者是方向盘与终点的区别，正如 Example 7.5 把初始函数换成平稳分布后一切才进入稳态。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 查普曼–柯尔莫哥洛夫方程是本章第一句把抽象变可解的方程，值得记住它的分量写法：第 n 步落在 j 的概率，等于先经某中间态 k 走 n-1 步、再一步到 j 的枚举求和 $T_{ij}(n)=\sum_k T_{ik}(n-1)p_{kj}$。第一性原理：这是全概率定理 + 马尔可夫性的双联锁——枚举中间态 k 用的是全概，而条件中悄悄丢掉 $X_0$ 靠的则是「只看现在」。命名模板：这条方程由提出者 Chapman 与 Kolmogorov 联名，其要义可浓缩成一句——「任何长跳都能拆成先短跳再接一跳」，从矩阵看它就是 $T(n)=T(n-1)P=P^n$。跨课程（18.06 矩阵幂 + 6.042J 图可达性）：左乘一次矩阵对应走一步，$P$ 的 n 次幂正是这张转移图上所有 n 步路径的计数，与 6.042J 里「邻接矩阵的幂列出长度为 n 的路径数」完全同构。反例：若不依赖马尔可夫性（转移概率还受更远历史影响），枚举式就不再是简单的逐项乘积、方程即告失败——马尔可夫性是这条递推能极简闭合的唯一前提。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 可达集合 $A(i)$ 是本章最被低估的概念工具：它把「概率意义上的能走」翻译成纯粹的图理由。第一性原理：从 $i$ 能否以正概率到达 $j$，等价于转移概率图上是否存在一条由 $p>0$ 的弧组成的路径——概率细节（0.2 还是 0.8）此刻全被丢掉，只留下「是否有边」这个布尔信息，于是整座链退化成一张有向图。命名模板：accessible（可达）强调「有条正概率的路」，与复习里曾见的 reachable 同义，区别仅在它出现在随机过程的语境中。跨课程（6.042J 图论/强连通分量）：$A(i)$ 的构造就是在有向图上做 BFS/DFS 求到的可达闭包，而常返类分解（下页）正是把这张骨架图拆成强连通分量的概率版——正如强连通分量把图划成「互相可达方阵」，常返类把状态空间划成「互相可达的家族」。反例：注意方向的不可逆性——$j\in A(i)$ 完全不保证 $i\in A(j)$；把握这一点，暂态（只能去、回不来）几乎可以目测判断，这才是读状态图最锋利的一式。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 以上句子涵盖「从 $A(i)$ 内任一状态 $j$ 再可由 $j$ 到达 $A(i)$ 全体」以及「闭集 / 不可约（closed set / irreducible）」性质的完整表述，此处 OCR 被打散为单词碎片，无法完整复原，未臆造原文；如需逐字原文请回查原书 p356。</span>

若状态 $i$ 从自身出发、在给定足够多步数之后，能把所有属于 $A(i)$、由 $i$ 可达的状态都访问无限多次（an infinite number of times），则称状态 $i$ 是**常返（recurrent）**的；反之，若 $i$ 不是常返的，则称状态 $i$ 是**暂态（transient）**的。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「常返 / 暂态」的严格定量定义（"从 $i$ 出发以概率 1 无限多次回到状态 $i$"）在本页句中被断行打散，本段的描述性复述据片段合理补全；页尾 "…… if it is not recurrent. Thus, a state i is transient ……" 落款相对完整。原文此处还提到对这些断言所作的更严谨论证见章末习题（end-of-chapter problems for a rigorous proof），此句亦残缺。</span>

因此，状态 $i$ 是暂态的当且仅当（if and only if）它不是常返的。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 常返（recurrent）与暂态（transient）把状态分成两类，定量本质一句话：常返态从自身出发将以概率 1 被无限多次访问，暂态态只有限多次、此后一去不回。第一性原理：判断一个状态是否常返，别去数它被访问的绝对次数，而要问「从它走出去的路，能否以概率 1 绕回来」——这正是 A(i) 的用武之地：存在 $j\in A(i)$ 而 $i\notin A(j)$，这条路有去无回，状态便暂态。命名模板：re- 意为「又」、c- 意为「来」，recurrent 就是「还会再来」；transient 是「过路客」，只是驻足而已。跨课程（6.042J 图论）：暂态/常返的判定与有向图中「能否回到起点」的拓扑判据同源，常返集合恰是强连通的一种概率强化。反例反直觉：比如 Example 7.2 的蜘蛛捕蝇，边界位置 $1$ 与 $m$ 是被吸住的常返态，而中间 $2,\ldots,m-1$ 看似被反复走过，却全是暂态——走得多不等于回得来，常返是「绕回自身」的概率保证而非访问频次。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这条「暂态⇄有限多次访问」的论证值得拆开看，因为它是反直观的工程师直觉与严格证明的分水岭：单凭「存在 $j\in A(i)$ 而 $i\notin A(j)$」居然能推出「$i$ 只被访问有限次」。第一性原理：一旦过程从 $i$ 真正踏进了那样的 $j$，就再也回不到 $i$；而只要这条路以正概率存在，在无限运行时间里它几乎必然（以概率 1）会被踩中一次——于是「回不去 $i$」从可能变成宿命。命名模板：transient 即「过客」，其英文词根（trans- 短暂经过）正是「只在历史中晃一眼」的意象。跨课程（6.042J + 概率零一依赖）：这里第一次用上「以概率 1 迟早发生」的强判据，与 Problem 7 里「暂态概率以几何速率 $\beta^k$ 衰减」遥相呼应，也预演了第三章「无限试验中 1% 事件以概率 1 必发生」的思想。反例：别把「走得多」当「回得来」——蜘蛛捕蝇例中边界 $1,m$ 是常返，中间的 $2,\ldots,m-1$ 看似被反复走过却是暂态；被访问次数是沿某条具体轨道看，而常返是「绕回自身」的存在性保证，两者据此可分。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「暂态—常返」判据一段的原文（如 "that $i$ is transient if … / … is a state $j \in A(i)$ … from $j$ … this win happen … i cannot be …"）被 OCR 切碎并缺失若干单词（win 应为 will）；译文按教科书对该判据的标准陈述重组，未臆造数值。</span>

---

<span style="color:#2471a3;">**[性质]**</span> <span style="color:#00838f;">**常返状态的可达类（Accessibility classes of a recurrent state）**</span>

对于常返状态（recurrent state）$i$，数学上对一切属于 $A(i)$ 的状态 $j$ 均有

```math
A(i) = A(j),
```

这可由常返（recurrence）的定义直接看出。也就是说，$A(i)$ 中的全部状态都是常返的：它们彼此互达、构成一个类（a class，或简称 recurrence class）；而且从 $A(i)$ 中任一状态出发，都无法到达 $A(i)$ 之外的任何状态。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「$i$ 常返 $\Rightarrow A(i)=A(j)$ 对所有 $j\in A(i)$」是常返类三种刻画（互达、闭集、无出弧）合流的枢纽，也是整章结构性的一个断言。第一性原理：若 $i$ 常返，则它从任何可达的 $j$ 都能绕回 $i$（否则 $j$ 就是让 $i$ 有去无回的暂态陷阱）；既然 $j$ 能到 $i$ 又能回 $j$，二者互达，可达集自然相同。命名模板：recurrence class 里 class 一词继承了离散数学「等价类」的严格含义——「互达」本身是等价关系（自反、对称、传递），常返类不外乎是「互达」等价关系下的等价类。跨课程（6.042J 等价关系与强连通分量）：正如等价关系把集合剖成互不相交的块，这一性质证明常返类把整个状态空间剖成互不相交的块，且「块内互达、块间无出弧」；它与有向无环图上的强连通分量分解天然同构。反例：暂态态之间可互达却不足以成块——互达+常返才构成类，只有互达而无常返只是「跳板」，这正是 Example 7.2 里内部暂态「互为通路却不自持」的原因。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一小段是把图 7.8 读成状态类的实操示范，提供一个可照搬的速判流程：一条 \(\mathrm{transient}\iff\) 有去无回、\(\mathrm{recurrent}\iff\) 在强连通环上。第一性原理：状态 1（自环）走不出去、能绕回自己，故常返；2 能到 1、3、4 却一个都回不来，故暂态；3 与 4 互相可达，是一个含自环的强连通块，故常返。命名模板：这正是 6.042J「有向图强连通分量」在日常里训练出的直觉——强连通分量内互达、有出无回的源头即成暂态跳板。跨课程（图论 SCC + 线性代数不可约）：常返类 = 转移图的强连通分量，且每个强连通块（无常出边）的一整个 SCC 是常返类，这判断因此可以交给 DFS 层次的图算法，也是 Problem 6 用「每个状态必有常返可达」所依据的结构。反例：别被「绕得回来」骗到——若 3、4 之间的往返略去自环也不影响其常返（互达 + 无出弧即可），而 2 即便出现在连通子图里也仍是暂态，判据是「能否从他人回 2」而非「2 能到几人」。

> 由此引出下述结论（it follows that … the following conclusion）。在马尔可夫链（Markov chain）中，**至少必须存在一个常返类（recurrent class）**；一个马尔可夫链可以被分解为一个或多个常返类（recurrent classes），或许再加上若干暂态（transient）状态。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「至少存在一个常返类，且链可分解为一或多个常返类加上若干暂态」是本章推理的主干，第一性原理一个词：进入一个常返类之后永不离开。因为类内各态互达、类内不存在通往类外的正概率弧，链一落地就被锁死在该类内反复打转。命名模板：recurrent class 中 class（类）一词，指的正是「一批互相可达、并把我们困在里面的状态族」，它跟离散数学里「等价类」的直觉一脉相承。跨课程（6.042J 强连通分量 + 18.06 不可约矩阵）：常返类分解就是对转移图做「强连通分量分解」的概率化表述；在线性代数里，单类常返链对应不可约（irreducible）随机矩阵，而把链限制进单一常返类隐含「只有一个不变分布」的谱特征。反例：暂态归属到哪个类？——都不归属，暂态是能从别处到达某常返类、却注定被该类抛离的过渡态；多常返类链的渐进行为必须逐类拆看，这正是 §7.3 开头「把注意力限制在单一常返类」的深层原因。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 周期常返类（periodic recurrent class）刻画的不再是「回不回得来」，而是「按什么节律回来」。若类内状态可分成 $d$ 个子集 $S_1,\ldots,S_d$，从 $S_k$ 必进 $S_{k+1}$（$k=d$ 时回 $S_1$），链便以周期 $d$ 循环游走。第一性原理：判断周期性只需一条——能否在某个 $n$ 下让链从某固定 $i$ 出发、同时可达类内全部状态；若处处受制于 gcd 相位，就必然分成 $d$ 个交错子集。命名模板：period 即「周期」，源自「一步必换子集、$d$ 步回到起点」这一节律，而非状态访问的绝对快慢。跨课程（6.042J 初等数论）：周期的本质是集合 $Q=\{n:T_{ii}(n)>0\}$ 诸元素的最大公约数 gcd，这正是章末 Problem 9 用「gcd=1 则大数皆可表」这一数论事实来证非周期性的钥匙。反例：确定性两状态链 $1\to2\to1$ 周期 $d=2$，$T_{ii}(n)$ 在 0、1 间振荡永不收敛——所以 §7.3 的稳态收敛定理必须先把「唯一非周期常返类」前置为结论存在的前提。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「找特殊状态」是一条把非周期性从「所有状态绕来绕去都对不上相位」里解放出来的捷径：不必逐一检查每个状态的返回相位，只要找到一个状态 $i$、与一个时刻 $n$，使得从 $i$ 出发经 $n$ 步能以正概率到达类内**每一个**状态，就足以断定全类非周期。第一性原理：若能一步跑到任何一个状态（配合类内互达），那么把「从 $i$ 走 $n$ 步到任意 $j$」与「在 $j$ 上游荡一段」自由拼接，就能构造出相差交错的返回路径，使返回时刻的 gcd 被「挤出成 1」。命名模板：this special state 被称为「seed state」/「带根状态」更形象——它像一棵树的根，能同时触达所有枝叶。跨课程（6.042J 初等数论 + 矩阵不可约）：这正是 Problem 9 里「$d=\gcd Q$ 为 1 即非周期」这一数论判据的一个可操作落点，也是判断「唯一常返类非周期」从而可套 §7.3 稳态收敛定理的一把钥匙。反例：若找不到这样的 $i$（class 处处卡在固定相位），比如纯双状态 $1\to2\to1$，则任何时刻只可能到达一半状态，special state 不存在——周期性警报由此拉响。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 稳态收敛定理是全章的支点，值得把它拆成「存在＋表达式＋刻画」三件套来消化：存在性说极限 $\pi_j$ 与起点 $i$ 无关，表达式说这个极限就是平衡方程 $\pi_j=\sum_k\pi_k p_{kj}$ 加归一化的唯一解，刻画说暂态态归零、常返态取正。第一性原理只有一句话——「单个非周期常返类 = 忘掉起点」。紧挨的两条前置条件（唯一个常返类、且非周期）各堵住一种不收敛：多类让极限依赖起点所在类，周期类让 $T_{ij}(n)$ 振荡不冻结。命名模板：steady-state（稳态）强调极限的三重性质——不随 $n$ 变、不随 $i$ 变、是概率分布。跨课程（Strang 18.065 谱论 + Perron–Frobenius）：$\pi$ 正是 $P^\top$ 的 1-特征向量，定理的第一条断言等价于（在非周期不可约条件下）幂迭代 $P^n$ 收敛到行重复的秩一矩阵；Problem 19/20 正是用耦合（coupling）与唯一性两条路各自重证这一事实。反例：把「有平衡方程解」误当「有稳态」是常见陷阱——周期性常返类仍有非负解，但 $T_{ij}(n)$ 并不收敛到它（见 7.1 双状态 $1\to2\to1$），解的唯一性与可达性是两回事。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「m 条平衡方程中必有一条可由其余推出」不是 Example 7.5 的巧合，而是矩阵理论的必然：对行随机矩阵，平衡方程太调和，秩只有 $m-1$。第一性原理把它说透——把 $\pi$ 视为行向量，平衡方程即 $\pi(P-I)= 0$，而 $P$ 的每行和为 1 使列向量 $\mathbf{1}$ 满足 $P\mathbf{1}=\mathbf{1}$，故对角化 $P\mathbf{1}=\mathbf{1}$ 与转置自伴下 $\mathbf{1}$ 落在 $(P-I)^\top$ 的零空间，从而 $\pi(P-I)=0$ 的解空间维数至少为 1，唯一性只能靠外加的归一化 $\sum_j\pi_j=1$ 收口。命名模板：这就是线性代数里「齐次方程解的空间＝1 维、再加一条非齐次约束定尺」的手法。跨课程（Strang 18.06 秩零空间 + 谱论）：秩亏 $m-1$ 意味着需要「归一化」这条独立的竖线补足一个自由度；在 PageRank 里同样如此——不知道先验尺度时 $\pi$ 只能定到比例，归一化把它钉成概率。反例：没有归一化方程时解是一个 $m-1$ 维仿射族——任何 $\alpha\pi+(1-\alpha)\pi'$ 都仍满足平衡，唯独不保证落在概率单纯形上；所谓「唯一稳态」的全部约束正在这条被译者读者反复背下来的归一化上。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 平衡方程 $\pi_j=\sum_k\pi_k p_{kj}$ 的第一性原理只有四个字——流量守恒：稳态下「进入状态 $j$ 的频率」必须等于「离开 $j$ 的频率」，否则 $j$ 的占比就会持续漂移。于是 $\pi_j$ 被解读为「处在 $j$ 的长期期望时间比例」，$\pi_k p_{kj}$ 则是从各 $k$ 涌进 $j$ 的单位时间期望次数。命名模板：steady-state（稳态）强调「不再随 n 波动、也不依赖起点 $i$」的长期冻结状态，stationary distribution（平稳分布）则强调「初态若取它、则任意时刻分布都不再变」——一个从极限而来，一个从不变量而来。跨课程（Strang 18.065 / Perron–Frobenius 定理）：$\pi$ 正是行随机矩阵 $P$ 对应特征值 1 的左特征向量，稳态定理其实是谱论的落地，也是 PageRank 的引擎；这里还有个线性相关陷阱——m 条平衡方程中总有一条可由其余推出，必须靠加和为一的归一化方程收口。反例：若链含多个常返类或某常返类恰是周期类，平衡方程仍有非负解，但并不等于 $T_{ij}(n)$ 的极限——解的唯一性以「唯一非周期常返类」为界，别把「有解」误当成「有稳态」。

---

> <span style="color:#7f8c8d;">† 据一个著名且重要的线性代数定理（称为 Perron-Frobenius 定理，Perron-Frobenius theorem），对任意马尔可夫链，平衡方程总存在一个非负解。对于一个具有单个常返类（recurrent class）、且该常返类非周期（aperiodic）的链，其特殊之处在于：在同时给出归一化方程的前提下，解是唯一的，且等于 n 步转移概率 $T_{ij}(n)$（n-step transition probabilities）的极限。</span>
<!-- ===== PDF p364 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）　·　§7.3　稳态行为（Steady-State Behavior，续）</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 7.6（三状态马尔可夫链的稳态概率求解）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页为 §7.3 中求解平衡方程（balance equations）的第三道示例。页首的示例描述文字已被 OCR 打散成不可读碎片，仅能辨认出零散的 "states: 1, 2" 与 "… example 7.6 …" 字样。既有内容能推断出：这是一个涉及状态 $0$、$1$、$2$ 的三状态链，以参数 $p$ 刻画转移概率，并满足 $0<p<1$；本页在演示如何由平衡方程与归一化方程解出各稳态概率 $\pi_j$。**具体转移概率矩阵及链的图形描述（图序、边概率）在上页未能完整保留，以下按可辨认的等式碎片与流通式给出，凡无法确认的系数一律以方括号占位，不回填臆造数值。** 如需逐字原文，请回查原书页 355。</span>

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

本页承接上页关于求解平衡方程（balance equation）的讨论，将两状态的模型推广到 $m$ 个状态的情形。设链的状态空间为 $\{1, 2, \ldots, m\}$，转移概率以参数 $p$（满足 $0<p<1$）来刻画。为便于理解，可借助右侧的转移（概率）图（transition probability graph）观察链的结构。

<span style="color:#2471a3;">**[figure]**</span> 图 7.12：Example 7.6 中针对「$m$ 扇门」情形的转移（概率）图（Transition … in Example 7.6 for the case of … doors）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 图 7.12 的节点布置与各条边上的概率数值均无法从 OCR 中读取（出现 "5 doors" 与 "m doors" 两种碎片，具体取哪个数值未知），此处不臆造图的坐标与边概率，请回查原书页 356 的图 7.12。</span>

由此图可以直观地看出：在 $0<p<1$ 的假设下，从任一状态都能够在若干步内到达（reachable）另一个状态，因此该链在 $m$ 个状态上 [构成……]。于是其转移概率矩阵（transition probability matrix）$P$ 的各行元素主要为 $1-p$、$p$ 与 $0$：

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个「门循环」例题带着一道漂亮的猜解捷径：因为状态在循环里完全对称，每扇门地位相等，大胆假设 $\pi_j=1/m$ 均匀分布，再代入平衡方程验证即可——猜得对是因为通配，验证靠稳态定理的唯一性兜底。第一性原理把这条套路拆成三步——「由对称性提出猜测 → 代入平衡方程校准 → 用唯一性封口」，比直接解 $m$ 元方程组省得多。命名模板：这种「先猜后验」法常称 symmetric guess 或「利用对称性」，在排队论、PageRank 对称图里屡见不鲜。跨课程（线性代数 + 组合对称）：均匀就是「转置不变性」在概率上的指纹，恰如对角线对称图的 PageRank 支部到 1/周围顶点；反过来，不对称链（如 Example 7.5 的 0.8/0.6）绝不会得到均匀解。反例：答案当 $\rho=1$（$b=d$）时也是均匀，但同样解法的前提是「真对称」；若偷懒把不对称问题也平摊，代入平衡方程必然露馅——唯一的判别式是验证而非直觉。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一定义把 $\pi_j$ 从「极限概率」升级成「时间占比」，因而具有纯频率的味道，是全章第一个能直接喂给工程学的读法。第一性原理：往一处叠加——$\pi_j=\lim V_{ij}(n)/n$ 说的是长期的「访问次数 / 运行时长」之比，这正是「时间平均」，而稳态定理给的是「系综平均 $P(X_n=j)$」；二者相等是一次典型的遍历性（ergodicity）宣言，也是为什么可以用一次「随机挑一天」$=$ 长期平均来处理修理成本。命名模板：$V_{ij}(n)$ 里的 $V$ 即 visits（访问），下标记录「从 $i$ 出发、在 $n$ 步内落到 $j$ 的次数」这一历史计数。跨课程（第 6 章泊松 / 大数定律 + Problem 21）：$\pi_j=\lim T_{ij}(n)$ 对 $n$ 取算术平均回到 $V_{ij}(n)/n$，恰是对大数定律在马尔可夫语境下的重述——Problem 21 直接给这一频率解释的严格证明。反例：别把「期望占比」和「几乎必然占比」混为一谈——教科书此处给的是期望版本；更强的几乎必然收敛（对几乎每条轨道成立）在 Problem 21 的评论里被补上，两条路线在概率里是不同强度的同一结论。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 生灭过程的局部平衡方程，是把「全局平衡」拆成逐条边上的微型天平：跨过 $i$ 与 $i+1$ 的交界，向右的期望频率 $\pi_i b_i$ 必须等于向左的 $\pi_{i+1} d_{i+1}$。第一性原理：稳态不是整条链处处都不动，而是每条边界上的净流量为零；因为状态只沿直线相邻跳跃，中间态 $i$ 只能从 $i-1$、$i+1$ 出入，于是守恒定律被切成 m 条独立的双边方程逐环递推。命名模板：birth（出生）指向上跳 $i\to i+1$（新个体进入），death（死亡）指向下跳 $i\to i-1$（个体离开），birth–death process 之名正是这对「一增一减」动作的转录。跨课程（排队论 M/M/1、M/M/m → 6.042J）：这类链是经典排队系统的原型——§7.3 的缓冲区、§7.5 的通信节点都由它承载。反例：局部平衡不自洽于非生灭链——一旦状态跨度超过一（如带二阶跃迁的游走），逐边天平无处安放，只能退回全局平衡方程求解；这正是「相邻性」这一生灭结构不可替代之处。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个有限缓冲队列的稳态解呈现「截断几何分布」，是 §7.3 家庭里最能照应排队论的一幕：到达速率 $b$、服务（离开）速率 $d$ 各自固定，局部平衡给出 $\pi_{i+1}=\rho\pi_i$，其中 $\rho=b/d$ 是「单位流量比」的全部体现。第一性原理：把 $b<d$（$\rho<1$，坐等)的填满趋势、$b>d$（$\rho>1$，趋于满队列）、$b=d$（$\rho=1$，均匀）三种情形装进同一副公式 $\pi_i=(1-\rho)\rho^i/(1-\rho^{m+1})$。命名模板：truncated geometric 指「几何分布的头部被 $i\le m$ 切掉」——没有上限时概率按 $\rho^i$ 无限几何衰减，有上限后要除以有限和归一化。跨课程（排队论 M/M/1 + 6.042J）：这就是经典 M/M/1 队列稳态占比 $\pi_i=(1-\rho)\rho^i$ 的有限容量（M/M/1/m 或 M/M/1/K）版本，当 $m\to\infty$ 时归一化分母趋近 $1/(1-\rho)$、$\pi_0\to1-\rho$，拿回的正是无穷队长情形。反例：$m$ 有限与否在 $\rho\ge1$ 时是天壤之别——$m\to\infty$ 时 $\rho>1$ 的系统无稳态可归宿，有限缓冲却始终有唯一稳态，问题出在「队列被容量封顶」上。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这篇「无限状态链可以永不稳态」的插曲，是对前面所有定理的前提最锋利的一次亮相：§7.3 的稳态收敛定理通通要求**有限状态**，一旦状态空间可数无穷，结论就可能失效。第一性原理：无限队长让「总量守恒」没处安放——每条状态 $i$ 的平衡方程都仍成立，但所有 $\pi_i$ 加起来发散，归一化坏掉，于是 $\pi_i\equiv0$ 是唯一「解」，实质上是队列有偏向地漂向无穷。命名模板：这里「暂态」的含义回到本章词根——每个 $i$ 只被有限次访问，因为过程以正概率不安地越走越远。跨课程（随机游走常返判据 + Problem 15 Ehrenfest）：一维无偏向随机游走是常返、有偏向游走是暂态，全由漂移方向与参数边界（如 $\rho=1$）决定；这类无穷态再常返的讨论是本科外的随机游走理论（Polya 定理）伏笔。反例记忆点：$\rho=b/d>1$ 的无限缓冲与 $\rho<1$ 的命运分道扬镳——前者无稳态、后者收敛到几何分布，同一个公式只是是否被封顶，就决定了「稳态是否存在」这个根本问题。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 吸收概率的求解是第一跳分析（first-step analysis）最干净的样本：要算「最终进入 $s$ 的概率 $a_i$」，就把第一跳拆开，全概率定理 + 马尔可夫性把 $a_i$ 变成自身及其近邻的线性组合 $a_i=\sum_j p_{ij}a_j$。第一性原理：与其在整个未来上空想，不如只问「这一步之后怎么办」——递推式把无限时域的问题压成一个有限线性方程组，一个状态一条方程。命名模板：absorption（吸收）取「进入某态就被吸住、再也出不来」之义，故把吸收态置 $p_{ss}=1$、$p_{sj}=0$ 后一切都可算。跨课程（概率图模型 / 18.065）：这组线性方程在结构上与信念传播（belief propagation）里求稳态的线性系统、以及随机游走在电气网络中求解电位（harmonic function）完全同源——同一组方程在不同语境换了名字。反例：当存在多个吸收态 $s$ 时，$a_i$ 不再单一，而是随起点 $i$ 变化的一族概率（赌徒破产的 0 与 $m$ 两个吸收端即典型）；若误以为所有 $a_i$ 都收敛到同一个全局概率，就会把 Example 7.10 的 $21/31$、$29/31$ 彻底算错。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 赌徒破产是吸收概率最经典的应用，而引爆全场的是那个优雅的差分量手法：不直接解 $a_i$ 的递推，而是令 $\delta_i=a_i-a_{i-1}$，把二阶递推降成一阶等比 $\delta_{i+1}=\rho\delta_i$，再求和 $\sum_i\delta_i=a_m-a_0=1$ 收口。第一性原理：差分捕捉的是「相邻状态的概率差」，而比值 $\rho=(1-p)/p$ 正是单步偏向的度量——p 偏大则朝赢头累积，p 偏小则朝破产塌陷。命名模板：gambler's ruin 直译「赌徒的倾覆」，ruin 一词已预告结局——不利赔率下财务破产近乎必然。跨课程（18.065 / 随机游走调和函数）：$a_i$ 满足离散调和方程，赌徒破产概率正是边界取 0、1 的调和函数，与 PageRank、电位求解是同一数学。反例总是清醒剂：并非所有赔率都注定破产——当 $p=1/2$ 公平赌局时 $a_i=i/m$ 随起点线性增长，直觉仍合理；「必输」的结论只系于 $\rho>1$ 即 $p<1/2$ 这一条参数线上。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 期望吸收时间的方程组 $\mu_i=1+\sum_j p_{ij}\mu_j$ 与吸收概率方程组 $a_i=\sum_j p_{ij}a_j$ 是「第一跳分析」的一对双胞胎，唯一的区别是那个孤独的「$+1$」——它记录的正是「先迈出当前这一步」的代价。第一性原理：把吸收态钉成 $\mu_i=0$，其余方程连成的线性系统正是「吸收基本矩阵」的登场处——把所有暂态聚成 $Q$，则 $I-Q$ 可逆，$(I-Q)^{-1}$ 的第 $(i,j)$ 元就是从 $i$ 出发期望「去 $j$ 访问的次数」，而 $\boldsymbol\mu=(I-Q)^{-1}\mathbf{1}$ 给出期望吸收步数。命名模板：这个实质上就是吸收马尔可夫链里教科书标配的 fundamental matrix $N=(I-Q)^{-1}$，许多资料直接称其为 Neumann series $\sum_{k\ge0}Q^k$。跨课程（Strang 18.06 逆矩阵 + 概率图模型）：求和 $\mathbf{1}+Q\mathbf{1}+Q^2\mathbf{1}+\cdots=(I-Q)^{-1}\mathbf{1}$ 与几何级数在矩阵世界的推广完全同构，也与随机游走到达电位的求解呼应。反例：若吸收态也混进暂态方程（没把 $\mu_j=0$ 钉死），方程组就退化为退化——每个吸收态给一条「$0=0$」冗余行，解的唯一性立刻崩塌。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 平均首达时间与平均递归时间是两个极易混用的量，命名模板一拆即明：first passage（首次经由）指从任意 $i$ 出发**第一次**撞见指定态 $s$ 的平均步数，记 $t_i$；recurrence（递归/再来）指从 $s$ 出发**绕一圈回到自己**的平均步数，记 $t_s^*$。第一性原理：二者都靠「第一步之后递归地再问同题」来解——$t_i=1+\sum_j p_{ij}t_j$，而 $t_s^*=1+\sum_j p_{sj}t_j$ 恰因「从 $s$ 出发第一步逃开、再从逃到的那处回 $s$」而要借已经求好的 $t_j$ 才能算。跨课程（吸收马尔可夫链基本矩阵）：这两者本质是对应线性方程组 $(I-Q)\mathbf{t}=\mathbf{1}$ 的可逆解——把 $I-P$ 中吸收态对应行截掉后求逆，得到的 $(I-Q)^{-1}$ 之元素正是期望首达，这是教材里反复出现的标准工具箱。反例：对周期链，$t_i$ 与 $t_s^*$ 的步数口径会打架——第一次首达只能发生在特定相位（如偶数步），若忽略周期相位直接套方程，得到的就不是真实期望首达。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这个小小的数值例把第一跳方程「实操化」得再清楚不过，正是我们把抽象框架落地成算术的标准模板。第一性原理：先钉紧特殊态 $t_1=0$（首达命中的靶心），再把每个暂态写「1＋下一步加权期望」，于是 $t_2=1+p_{21}t_1+p_{22}t_2=1+0.4\,t_2$，这是一条只有 $t_2$ 一个未知量的自指方程，一项回代即得 $t_2=5/3$。第二跳——递归时间——不重开战场，只借用已得之果：因为从 $s$ 出发的第一步（以概率 $p_{sj}$）把问题抛给已经解好的 $t_j$，故 $t_1^{*}=1+\sum_j p_{1j}t_j=1+p_{12}t_2=4/3$。命名模板：这就是 first-step analysis——「别一次跳到终点，只问一步，把剩下交给递归」贯穿 §7.4 全程。跨课程（全期望定理 + 基础线性系统）：$t_1^{*}=1+\sum_j p_{sj}t_j$ 正是全期望定理的应用，也是 Problem 20/吸收基本矩阵在「回归问题」沙盘的支臂。反例：若把 state 1 也想当然写 $t_1=1+\cdots$ 而非钉死 0，方程将多一个未知、失却唯一性；「吸收/目标态必须人工置 0」是全程不二法门。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 连续时间马尔可夫链让人眼前一亮的地方：离散版本把每次转移记作整数时刻，连续版本则让「下一次转移来得有多快」也随机化，而随机化用的必须是**指数分布**。第一性原理：指数分布是「无记忆」（memoryless）的守护者——停留在状态 $i$ 的剩余时间与已经待了多久无关，于是「只看现在」的马尔可夫性质才能跨进连续时间；一旦换用其他分布，剩余时间的条件分布就会泄露历史、性质崩塌。命名模板：continuous-time 直白地标出「时间轴连续」，相对 discrete-time 的整数拍子。跨课程（第 6 章泊松过程 + 18.065 生成元）：这里的 $\nu_i$ 与 $q_{ij}$ 其实是转移速率——单位时间离开 $i$ 的期望转移次数，与泊松过程把 $\lambda$ 解作「单位时间到达率」同构；离散化步长 $\delta$ 下的 $p_{ii}=1-\delta\sum_{j\ne i}q_{ij}+o(\delta)$ 对应泊松「短间隔内无事发生」的表达式，而连续时间平衡方程 $\sum_{k\ne j}\pi_k q_{kj}=\pi_j\sum_{k\ne j}q_{jk}$ 就是生灭守恒在本小节的再版。反例：若把状态停留时间改成确定性或均匀分布，抽样链 $Z_n=X(n\delta)$ 失去马尔可夫性，前几章那套「只看现在」的武器全部失效——指数假设不是调料，而是模型的承重墙。

作为直接推论，在相继转移后得到的状态序列 $X_n$ 是一个转移概率为 $p_{ij}$ 的离散时间马尔可夫链，称为嵌入马尔可夫链（embedded Markov chain）。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「嵌入马尔可夫链」是连续时间链与离散时间链之间最干净的桥：丢掉所有「等多久」的信息，只记下状态依次跳到哪儿，$X_n$ 便是一条标准离散链。第一性原理：连续时间链 =「跳转序列」×「驻留时长」两个独立组件——转移法则给出前者，速率 $\nu_i$ 给出后者的均值；嵌入链单看前者，也就自动继承上一页的完备概率结构。命名模板：embedded（嵌入）指这条离散链「潜藏」在连续时间链每两个跳转点之间，如同把连续轨道做列采样后在撞点上抽帧。跨课程（泊松过程合并/分拆 + 排队论）：嵌入链的稳态 $\pi_i'$ 与连续链的时间占比 $\pi_i$ 一般不相等（见后文 Example 7.14），正是这只「在跳转瞬间数次数」与「在钟表时间里数时长」的眼睛不同所致。反例：若让 $\nu_i$ 随状态剧烈变化，嵌入链与时间链的稳态会面目全非（如 $\pi_1>\pi_2$ 但 $\pi_1'=\pi_2'$）；只有各 $\nu_i$ 皆相同时二者才一致——这是识别那套「既当过程又当频率」歧义的分水岭。用数学语言表述，我们的假设可如下规范化地表述。设

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 转移速率 $q_{ij}$ 是把「连续时间链」与「速率」接上的关键代号，看懂它就能通读全节。第一性原理：离散链给你条件概率 $P_{ij}$（跳到哪），连续链额外给你驻留速率 $\nu_i$（走得多快），两者相乘得到 $q_{ij}=\nu_i P_{ij}$——单位时间里「从 $i$ 转移到 $j$」的平均次数；反向 $V_i=\sum_j q_{ij}$ 与 $P_{ij}=q_{ij}/V_i$ 就是两片通配的拼图。命名模板：transition rate（转移速率）刻意用 rate（速率）而非 probability，提醒你它是「每单位时间的次数」，量纲与概率不同，正因如此连续时间的平衡方程以速率而非概率出现。跨课程（第 6 章泊松 + 生灭排队）：$\nu_i$ 对应的正是泊松过程参数 $\lambda$ 的「单位时间到达率」解读，而 $q_{ij}$ 是随机游走「转移强度」的标准矩阵对象，$Q$ 对角元通常取 $q_{ii}=-\sum_{j\ne i}q_{ij}$ 以保证行和为零。反例：混淆 $P_{ij}$ 与 $q_{ij}$ 是最常见的翻车——二者数值不同（一个是概率、一个是速率），混用会让平衡方程的量纲对不上，稳态概率立即算错。

注意，该模型允许自转移（self-transition），即从某个状态回到它自身，这在自转移概率 $P_{ii}$ 非零时确实可能发生。然而，这样的自转移没有可观测的影响：由于指数分布（exponential distribution）的无记忆性（memorylessness），无论刚刚是否发生过一次自转移，距离下一次转移所剩余的时间都是相同的。出于这一原因，我们可以忽略自转移，并且自此假设对所有 $i$ 均有

```math
P_{ii} = q_{ii} = 0,
\qquad \text{对所有 } i .
```

---

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 「自转移不可观测，所以干脆无视」这句全凭无记忆性撑起来的论断，是连续时间链特有的奢侈：在离散时间链里，自转移 $p_{ii}>0$ 也会改变访问次数统计（正是 Problem 20 里用来把周期链改造成非周期链的杠杆），但在连续时间里自转移「什么都没发生，时钟却在走」。第一性原理：指数分布的无记忆性意味着「待了多久」不改变「还要待多久」，既然自转移既不改变状态、又不重置寿命，它在概率意义上彻底无用。命名模板：self-loop（自环）是图论词汇，指「出发点和终点是同一个顶点的弧」。跨课程（连续时间系统 + 排队论）：这条直觉在与泊松过程里「自参考」建模、以及连续时间马尔可夫链的生成元 $Q$ 定常表达（$q_{ii}=-\sum_{j\ne i}q_{ij}$）完全自洽。反例：这个「忽略」只在连续时间成立——离散时间里 $p_{ii}$ 会实实在在地增加返回统计，若非连续语境而照搬「自转移无用」，就会在周期/自环分析上翻车。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Example 7.14 是个把「生活故事 → 转移速率矩阵」这一建模动作演到底的标本：先数出三种模式（生产/测试/修理）当状态，再把「××持续多久」翻译成指数参数当速率（$\nu_1=1,\nu_2=5,\nu_3=3$），最后把「跳向谁」的转移概率 $P_{ij}$ 与行速率相乘得到 $q_{ij}$。第一性原理：「故事里每个可选动作」在指数（无记忆）世界里各自带一个速率，「同时发生」靠相互独立 + 速率相加；于是转移矩阵的行速和给出离开速率，归一化概率 $Q=V\cdot P$ 由 $q_{ij}=\nu_i p_{ij}$ 一张表装完。命名模板：这叫从 CTMC 的「速率定义」倒推出「转移概率定义」，是先用指数假设把分布压成单参数、再把所有依赖装进速率矩阵的工艺。跨课程（排队论 + 系统可靠性）：这正是一台 repair/reboot 机器的生灭式 CTMC 骨架，指数假设把「剩余寿命无记忆」变成可分解的三角结构。反例：若漏掉行速率（比如测试阶段误把 $\nu_2$ 当 $1$），则 $Q$ 每行速度不一致，局部平衡与均衡全盘错位——行速率是矩阵忠诚度的唯一记分牌。
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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这条「抽样」步骤是连续↔离散本我沟通的钥匙，值得把记号 $o(\delta)$ 读透：把连续时间链在密度为 $\delta$ 的网格上逐点采样，得到 $Z_n=X(n\delta)$。第一性原理：短时段 $\delta$ 内「发生一次转移」的概率按 $q_{ij}\delta$ 线性（一阶）增长，而「一次以上转移」的概率是 $o(\delta)$ 量级的高阶无穷小——于是含 $\delta$ 的一次项保留、$o(\delta)$ 忽略，恰好得一步转移 $P_{ij}=q_{ij}\delta+o(\delta)$ 与自转移 $P_{ii}=1-\delta\sum_{j\ne i}q_{ij}+o(\delta)$。命名模板：$o(\delta)$（little-o）是数分里「比 $\delta$ 更快趋于零」的标准记号，此处用它滤掉高阶事件、让推导只剩线性主项。跨课程（微积分小量 + 泊松过程直觉）：这是对泊松「短区间最多一个点到达」形式化，也是把速率 $q_{ij}$ 翻译成离散转移概率的必经之桥。反例：若采样间隔 $\delta$ 足够大，同一个 $\delta$ 内可能多次转移，$P_{ij}$ 的线性近似失真，$Z_n$ 不再是原连续链的忠实指纹——所以所有结论都写明「当 $\delta$ 很小时」。$\delta$ 越小公式越精确。

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

再考虑一般的中间状态 $i$，其中 $0<i<m$。在接下来的 $\delta$ 个时间单位内，有一个新数据包到达的概率为 $\lambda\delta+o(\delta)$，它会把状态带到 $i+1$；同时，传输完成从而把状态带到 $i-1$ 的概率为 $\mu\delta+o(\delta)$。（其余情形所对应概率的阶 $o(\delta^2)$ 项与其它 $o(\delta)$ 项一并列出。）即

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 连续时间的平衡方程 $\sum_{k\ne j}\pi_k q_{kj}=\pi_j\sum_{k\ne j}q_{jk}$ 是离散版平衡方程在「取极限」之后的化身，读起来就是一句流量守恒：进入 $j$ 的速率之和等于离开 $j$ 的速率之和。第一性原理：把离散平衡 $\pi_j=\sum_k\pi_k p_{kj}$ 展开成含 $\delta$ 的两部分，约去 $\pi_j$ 项、除以 $\delta$、令 $\delta\to0$，$o(\delta)$ 随之蒸发，剩下的正是速率版守恒——因为连续时间没有「整数步长」可言，守恒必须以速率为单位。命名模板：这正是 Markov chain 生成元（infinitesimal generator）$Q$ 的平衡列形式，$\boldsymbol\pi Q=0$ 的那组方程。跨课程（§7.3 平衡方程 + 排队论 + 谱论）：它是 PageRank 连续对应、M/M/c 排队稳态根基，也是 §7.5 结束时稳态收敛定理的常返庄严。反例：别把离散平衡方程直接套到连续链上——离散里的概率 $p_{kj}$ 会被速率 $q_{kj}$ 替换、量纲换了、也要保证 $q_{kj}$ 前的 $\pi_k$ 使命不宣；漏了「除以 $\delta$ 取极限」这一步，两边就量纲失衡。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这组数值把「概率 $\pi_i$」与「频率 $\pi_i'$」的分野讲得入木三分：虽然转进状态 1 和状态 2 的转移一样频繁，但 $X(t)$ 停留在 1 的概率却更高。第一性原理就一句——「转移次数」与「停留时长」是两把独立标尺：$\pi_i'$ 量的是「多少次转移落到 $i$」，$\pi_i$ 量的是「长时间里钟表指针停在 $i$ 多久」，后者多了一项权重「单次驻留的平均时长 $1/\nu_i$」；两者经归一化连接起来才是真正的 $\pi_i$（时间占比）。命名模板：$\pi_i'$ 常称 embedded steady-state 或「跳转稳态」，与 $\pi_i$（时间稳态）相对。跨课程（排队论 / 修理模型）：这解释了为何 Example 7.14 里 $\pi_1>\pi_2$——状态 1 的一次驻留比状态 2 长得多；当且仅当 $\nu_i$ 全相等时两套稳态合体。反例：若忽略驻留时长、直接用转移频率当时间占比，会把排队系统的真实占用率严重算错——这是连续时间链最易犯的单位混用。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 连续时间的生灭局部平衡 $\pi_i q_{ij}=\pi_j q_{ji}$ 是离散版逐边天平在速率世界里的再版，差异只在用速率 $q$ 取代概率 $p$。第一性原理：生灭的相邻跳跃保证了「跨过 $i$ 与 $i+1$ 这条界」的流量朝一个方向只能是 $\pi_i q_{i,i+1}$，反向是 $\pi_{i+1}q_{i+1,i}$，稳态下必相等——把整条链切成一串可逐环迭代的两态双流方程，从而闭式解 $\pi_{i+1}=\pi_i\cdot(q_{i,i+1}/q_{i+1,i})$ 顺势滚出。命名模板：local（局部）指守恒只在每一条相邻界上独立成立，无需看全场，这是它比全局平衡更省事、也更稳健的关键。跨课程（排队论 + 生灭定律）：这正是 M/M/1 诸稳态公式（$\pi_{i+1}=(\lambda/\mu)\pi_i$）的母版，也是物理化学反应里细致平衡（detailed balance）的直接镜像。反例：若非相邻跳跃（如存在二步跳），局部天平无处安放，只好退回全局平衡方程；即谓「相邻性」是生灭结构不可少之根脚。

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
> <span style="color:#1e8449;">[note] Note（译者注）:</span> 例 7.15 这一套 $\pi_i=\rho^i/(1+\rho+\cdots+\rho^m)$ 把「有限容量通信节点」的稳态全部摊在一纸闭式里，是全章把排队论、生灭与连续时间三股线拧成一股的收官示范。第一性原理：泊松到达 $\lambda$、指数服务 $\mu$（无记忆）使系统是生灭链，局部平衡给 $\pi_{i+1}=(\lambda/\mu)\pi_i$，$m$ 个队列位封顶后归一化的分母是几何和，于是截断几何即一切。命名模板：这一类模型在排队文献里即有限位 M/M/1 或 Erlang-B 型阻塞系统，$\rho=\lambda/\mu$ 是「业务强度/流量强度」。跨课程（排队论 Erlang 公式 + 通信工程）：$\pi_m$ 恰是「到达遭拒概率」（blocking/丢弃概率），Erlang 阻挡公式在电信工程里用同一数学；随着 $m\to\infty$ 它退化为无穷队长几何稳态。反例：当 $\rho\ge1$ 时无上限系统没有稳态、有限系统仍存在——这正是「容量封顶把病灶（无限堆积）治住」的典型教训，也是对前面 Example 7.7「缓冲无限时暂态性」的连续版注解。
<!-- ===== PDF p387 ===== -->
<span style="color:#c0392b;">**7.6　小结与讨论（Summary and Discussion）**</span>

在本章中，我们引入了具有**有限个状态**的马尔可夫链模型（Markov chain models with a finite number of states）。在离散时间马尔可夫链（discrete-time Markov chain）中，转移（transition）发生在整数时刻，遵循给定的转移概率（transition probabilities）$p_{ij}$。将马尔可夫链与一般随机过程（general random processes）区分开来的关键性质在于：每当状态等于某个 $i$ 时，转移概率 $p_{ij}$ 都会适用，而与状态在此前的任何取值无关。因此，在给定当前（present）状态的前提下，过程的未来与过去相独立（independent of the past）。

为一个给定的物理情形构想合适的马尔可夫链模型，在某种程度上是一门艺术。一般来说，我们需要引入一组足够丰富的状态（states），使得当前状态（current state）能够概括过程历史中所有与其未来演化相关的信息。在满足这一要求的前提下，我们通常倾向于采用一个不包含多余状态的简单模型。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一小节是「建模方法论」，把它理解成一句话收口全书：**状态 = 未来的充分统计量，且要挑最精简的**。第一性原理：马尔可夫性要求「当前状态忠实地总结一切与未来相关之历史」，所以建模的唯一任务是把物理量压缩进状态；而「艺术」二字指的是那个张力——状态太少漏掉记忆、过程失去马尔可夫性，状态太多则矩阵爆炸、模型难解，两者间的平衡全凭手感。命名模板：这条「足够丰富又不冗余」的取舍通常叫 Markovian state 设计 或「充分状态选择（sufficient state）」，是 example 7.3 里「把已坏天数也装进状态」的刻意为之。跨课程（CSAPP 状态机 + 6.042J 等价关系）：与用有限状态抽象替代整段内存历史同构——能区分才分状态，不能区分就合并且忽略细粒度差别；Problem 2/3（L/R 折叠、$Y_n$ 聚合）正是检验「这个折叠还保持马尔可夫性吗」的反面教材。反例：折叠信号可能丢失关键历史，比如 Problem 2 把瓷砖折叠成 L/R 后信号序列不再马尔可夫——少一个状态的代价往往正是马尔可夫性的崩塌。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题是「把非几何到达间隔装进马尔可夫链」的启蒙：间隔在 $\{1,3,4\}$ 上取值，既非几何也非无记忆，必须用「自拆时间」补足历史。第一性原理：让一个状态专门表示「此刻恰好有顾客到」，再用其余状态记录「离下次到达还差几天」——把原本被丢掉的等待期转译成附加状态，正是第二章「用状态吸收记忆」思想的反向练习。命名模板：这类把非几何间隔的过程嵌入有限状态链的做法，是排队论里 phase-type / PH 分布（D.R. Cox 表示）的原型，也是离散事件模拟的「下次事件时刻」状态。跨课程（第 6 章泊松假设 + 6.042J 状态机）：泊松假设「间隔几何/指数」是为了省状态；此题偏要只给 PMF 不省状态，正好对照「记忆程度 ↔ 状态空间大小」的权衡。反例：若只留两个状态（到/不到），等待期的长度丢失，转移矩阵对间隔分布失忆，模型必然失真——所以必须四个状态，一个都不能省。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 2.**（走廊瓷砖上移动的老鼠，信号 L/R 是否构成马尔可夫链）</span>

A mouse moves along a tiled corridor with $2m$ tiles, where $m > 1$. From each tile $i$, $1 \le i \le 2m$, it moves to either tile $i - 1$ or $i + 1$ with equal probability. From tile $1$ or tile $2m$, it moves to tile $2$ or $2m - 1$, respectively, with probability $1$. Each time the mouse moves to a tile $i \le m$ or $i > m$, an electronic device outputs a signal $L$ or $R$, respectively. Can the generated sequence of signals $L$ and $R$ be described as a Markov chain with states $L$ and $R$?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这是一道「聚合会丢历史」的绝佳反例：把 $2m$ 块砖折叠成 L/R 两个信号，问折叠后的信号序列还是不是马尔可夫链。第一性原理：要把状态压成 $L,R$ 仍成立，必须让「同信号内各砖对下一步信号等价」——但砖 $m$ 与砖 $m-1$ 虽同为 $L$，下一步撞入 $R$ 区却取决于「处在 $L$ 区哪一端」，折叠后这条信息从状态里蒸发。命名模板：这种把多个状态合并成一个的「状态坍缩」叫 lumpability（可分组性）；检查它不是看「合并后稳态是否像样」，而是看「转移性质是否对坍缩不变」。跨课程（第 6 章马尔可夫性 + 6.042J 等价类）：折叠本质是对原链做等价类分桶，能分的条件是「桶内任意状态对桶外目标的转移分布完全相同」；不满足就得退回原始状态或加大桶之划分。反例：仅仅因为「L/R 出现频率有稳态」就以为可折叠，是很多自动机建模的慢性病——本题答案是否定的，寻根即「桶内不对称」。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中「tile $i$，$1 \le i \le 2m$」原 OCR 为「tile i l' 1 , 2m」（下标范围残缺）；「$i \le m$ or $i > m$」原 OCR 为「tile i $ m or i > m」（不等号误识别）。此处按上下文补全，若需最严格原文请回查原书页 380。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 题干中「tile $i$，$1 \le i \le 2m$」原 OCR 为「tile i l' 1 , 2m」（下标范围残缺）；「$i \le m$ or $i > m$」原 OCR 为「tile i $ m or i > m」（不等号误识别）。此处按上下文补全，若需最严格原文请回查原书页 380。</span>

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 3.**（聚集为两态 $Y_n$ 后是否仍为马尔可夫链）</span>

Consider the Markov chain in Example 7.2, for the case where $m = 4$, as in Fig. 7.2, and assume that the process starts at any of the four states, with equal probability. Let $Y_n = 1$ whenever the Markov chain is at state $1$ or $2$, and $Y_n = 2$ whenever the Markov chain is at state $3$ or $4$. Is the process $Y_n$ a Markov chain?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 把 Example 7.2 的四个状态（$m=4$，如图 7.2）按 $\{1,2\}\to 1$、$\{3,4\}\to 2$ 折叠成两状态，问折叠后的 $Y_n$ 还是不是马尔可夫链——答案是否定的。第一性原理：马尔可夫性的全部承诺是「未来只依赖当前状态」；把多个状态并成一个桶（bucket）后仍想成立，必须有「桶内任意状态对桶外每个粗标签的下一跳分布完全相同」，从而桶的信息足以钉死下一步。而图 7.2 里 $1$ 在「区段边缘」、$2$ 在内部：两者下一步对撞进 $\{3,4\}$ 区的概率不同，折叠后这条「桶内位置」信息从状态里蒸发，历史透过 $Y$ 泄漏出来，链就断了。命名模板：这种「把状态并类后仍为链」叫 lumpability（可合并性 / 聚合性），合格的并类是满足转移良定义（well-defined）的 partition；此时的 $Y_n$ 才是原链的「quotient（商链）」。跨课程（6.042J 等价关系 / 商结构）：折叠就是取等价类之后要求转移在类上良定义，做不到就只能回到更细划分或补状态。有个微妙点：本题设初始四状态等概率，仍救不回来——等初始分布只能抹平「第一口」，救不了往后的桶内不对称。反例对照：若把路径两端的对称挂点合并，转移在邻类上往往良定义，那就能合；本题之所以不能，恰是「桶边≠桶心」不对称，物理上就是两个末端不对称的链不可粗粒化。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">SECTION 7.2　状态分类（Classification of States）</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 4.**（蜘蛛与苍蝇相对运动，暂态与常返状态）</span>

A spider and a fly move along a straight line in unit increments. The spider always moves towards the fly by one unit. The fly moves towards the spider by one unit with probability $0.3$, moves away from the spider by one unit with probability $0.3$, and stays in place with probability $0.4$. The initial distance between the spider and the fly is integer. When the spider and the fly land in the same position, the spider captures the fly.

(a) Construct a Markov chain that describes the relative location of the spider and fly.

(b) Identify the transient and recurrent states.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道「蜘蛛追苍蝇」习题示范了把高维随机动态压成单个标量的降维技巧。第一性原理：两者的绝对坐标都随步数漂移，但「蜘蛛与苍蝇的相对位移」才决定生死——因为更新规则是平移不变的（translation-invariant），只与相隔几格有关。于是定义相对位置 $D_n$＝（苍蝇坐标 − 蜘蛛坐标）：蜘蛛每步向苍蝇走近一格，把 $D_n$ 减 1；苍蝇按 $0.3/0.3/0.4$ 朝蜘蛛、朝反方向、原地不动，分别把 $D_n$ 再减 1、加 1、不变。状态空间就坍缩成 $\{D_n \ge 0\}$，且 $D_n=0$ 表示被捕捉。命名模板：这正是一般「reduction by symmetry / relative-coordinate 截断」——讲我们为何能把无穷位置链约化成有限距离链；撞在一起 $D_n=0$ 是天然吸收态（一旦为 0 就捕获，过程终结）。分类眼光（跨课程 6.042J / 随机游走）：当 $D>0$ 时，下一步「把距离减小」与「把距离增大」的净漂移决定一切——若 $D_n$ 是带正漂移（趋向更大）的随机游走，则它永远回不到 0，捕捉概率小于 1，于是每个 $D$ 状态都是暂态（transient）；若漂移偏小（趋向 0），则会被捕获，$D>0$ 的状态都「几乎必然进入 0」。正因如此，本题的 (b) 才需要先算净期望步进再定暂态/常返，正是第一章随机游走分类论的翻版。反例最能醒脑：若蜘蛛不会逼近（只待在原地），$D_n$ 变成普通对称随机游走，在一维是常返态，就永远「在 0 与无穷之间游荡」，捕捉概率为 0——极限行为天壤之别，全靠那个净漂移在分岔。

---

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 5.**（常返类是否为周期）</span>

Consider a Markov chain with states $1, 2, \ldots, 9$, and the following transition probabilities: $P_{12} = P_{17} = 1/2$, $P_{i(i+1)} = 1$ for $i \neq 1, 6, 9$, and $P_{61} = P_{91} = 1$. Is the recurrent class of the chain periodic or not?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道题考察「常返类的周期」如何从图上读出来——按本节定义，周期是这个常返类里所有「回到某状态的闭环回路长度」的最大公约数（gcd），gcd 为 1 则非周期、否则周期。第一性原理：一个状态能回到自己的步数集合 $Q=\{n: T_{ii}(n)>0\}$，其 gcd 记作 $d$；周期只是「走完 $d$ 步整体平移后把可达性叠回原样」。这不是某个状态的个人属性，而是整个常返类的共性：类内任意两状态周期相同，故我们说「类的周期」。命名模板：判断任务可以机械化成「找一张当前的回路，把这个类的各状态按离顶点的同余类 $i \bmod d$ 分层」——这就是周期的「partition 意义」（见 Problem 9）。落回本题，给出一张带 $P_{61}=P_{91}=1$ 的环状回路与 $P_{12}=P_{17}=1/2$ 的岔路，凑出 $d>1$ 的约束，答案即周期性。抓错点常在「把简单的循环图看成非周期」：只要所有可行回路长度都共享一个大于 1 的公因子，例如全是偶数步，它一定是周期的，尽管也能找到长得随心所欲的路径。跨课程（6.042J 图论强连通分量 + 本单元 Problem 9）：周期判别正是「图上回路长度的 gcd」这一定理的直观来源；课本里的非周期（aperiodic）常拿自转移（self-loop）造出来——加上 $p_{ii}>0$ 立即把 gcd 拉回 1，这也是 Problem 20(b) 用「务虚自转移」让周期链变非周期的那一招。反例：一个二部图（所有回路长度都是偶数）就是周期为 2 的典型，若把某一状态加一条自环，所有回路立即都能改成长度任何整数，gcd=1，周期立刻没了。

---
<!-- ===== PDF p390 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — 习题区续接（Problems，续）

> <span style="color:#7f8c8d;">本页为第 7 章章末 Problems 习题区的延续页，承接上一页（含 Problem 1–5），本页含 Problem 6 与 Problem 7，两题均带 `*` 难度标记，其题干与解答一律保持英文原题。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 6. \* Existence of a recurrent state（常返状态的存在性）</span>

Show that in a Markov chain at least one recurrent state must be accessible from any given state, i.e., for any $i$, there is at least one recurrent $j$ in the set $A(i)$ of accessible states from $i$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本题证明中的集合隶属符号在 OCR 中被误识别（如将 $\in$ 读作 `E`、将 $\notin$ 读作 `rJ.`、下标 $i_1$/$i_2$ 读作 `i l`/`i2`、$\neq$ 读作 `'#`、并将首处出现的 $i_1$ 误读为 `h`），上下面裁决按标准数学记号还原，未改动任何数值或论证步骤。</span>

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）.** Fix a state $i$. If $i$ is recurrent, then every $j \in A(i)$ is also recurrent, so we are done. Assume that $i$ is transient. Then there exists a state $i_1 \in A(i)$ such that $i \notin A(i_1)$. If $i_1$ is recurrent, then we have found a recurrent state that is accessible from $i$, and we are done. Suppose now that $i_1$ is transient. Then $i_1 \neq i$, because otherwise the assumptions $i_1 \in A(i)$ and $i \notin A(i_1)$ would yield $i \in A(i)$ and $i \notin A(i)$, which is a contradiction. Since $i_1$ is transient, there exists some $i_2$ such that $i_2 \in A(i_1)$ and $i_1 \notin A(i_2)$. In particular, $i_2 \in A(i)$. If $i_2$ is recurrent, we are done. So suppose that $i_2$ is transient. The same argument as before shows that $i_2 \neq i_1$. Furthermore, we must also have $i_2 \neq i$. This is because if we had $i_2 = i$, we would have $i_1 \in A(i) \cap A(i_2)$, contradicting the assumption $i_1 \notin A(i_2)$. Continuing this process, at the $k$th step, we will either obtain a recurrent state $i_k$ which is accessible from $i$, or else we will obtain a transient state $i_k$ which is different than all the preceding states $i, i_1, \dots, i_{k-1}$. Since there is only a finite number of states, a recurrent state must ultimately be obtained.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题的结论「从任何状态出发，一定存在可达的常返状态」是有限状态空间马尔可夫链的一条结构性铁律，它把抽象的常返/暂态分类落回图论拓扑上。第一性原理：对状态 $i$ 记可达集 $A(i)$；若 $i$ 是暂态，就存在某个 $i_1 \in A(i)$ 满足 $i \notin A(i_1)$——即「从 $i$ 能到，但不准 $i_1$ 绕回 $i$」，这意味着 $A(i_1) \subsetneq A(i)$ 严格缩水。于是我们可以一路构造 $i \to i_1 \to i_2 \to \cdots$，每步得到一个严格递减的可达集套 $A(i) \supsetneq A(i_1) \supsetneq \cdots$。关键来了：状态只有有限多个，可达集不可能无限严格递减，因此这套过程必须在某个 $i_k$ 处停下——停下只能是「这个状态没有可满足「到不了它自己」的下一跳」，换句话说 $i_k$ 的所有可达态都含 $i_k$ 自己，$i_k$ 就是常返状态。命名模板：可达集构成偏序，真正在做的是「沿严格递减链向下跑，直到掉进一个不动点」——也就是在「可达图的形式化（condensation）」这个有向无环图里往下走到一个 sink（出度为 0 的汇聚点），而这个 sink 正是一个强连通分量、恰为常返类。跨课程（6.042J 有向图 / 强连通分量）：一个有限有向图的 SCC 凝聚图必为 DAG、必有汇点，而马尔可夫链的常返类正是「没出口的 SCC」；这就是两个记号 $A(i)$ 与「同 $i$ 强可达不可逆」为何殊途同归。反例最能兜底：若状态无限多，这个论证立刻断裂——一列严格递减的可达集可以一路无限钻下去而不停（如「向右无限走」的链），那时根本不保证有常返态。这正是有限性（finite）在所有证明中反复救场的根源。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问把「暂态终究会离开」量化成了可证的速度：暂态的占据概率按几何级数 $c\gamma^n$ 指数衰减，而 $E[T]<\infty$ 保证进入常返类的时刻几乎必然有限且有界期望。第一性原理：设状态总数 $m$，从任何状态出发只要 $m$ 步内必能以正概率碰到某个常返状态，那么把 $m$ 步当作一个「时间块」，每一整块仍停在暂态区的概率总被同一个 $\beta<1$ 上界压住；块与块之间因马尔可夫性可独立复乘，于是 $n$ 步后仍在暂态区的概率最多 $\beta^{\lfloor n/m\rfloor}\le c\gamma^n$。真正在起作用的是「暂态子块是一个严格缩小的线性映射」：把所有暂态之间的转移收进矩阵 $Q$，常返区就像一块「海绵」不断抽走概率，块算子 $Q^m$ 的谱半径严格小于 1。命名模板：这就是「暂态块（transient block）」的几何衰减；把吸收基本矩阵 $(I-Q)^{-1}=\sum_{k\ge0}Q^k$ 里每一项逐块求和，正是「从暂态出发平均访问次数有限」的代数倒影（见本书吸收期望时间，跨课程 Strang 18.06：谱半径 $<1$ 的矩阵幂收敛于零）。(b) 里 $P(A)=0$ 是因为对每个 $n$ 都有 $P(A)\le c\gamma^n$ 而对一切 $n$ 成立——这就是「任意小 → 只能为 0」的标准手法，也就是 Borel–Cantelli 思想的雏形。反例最能点醒：若暂态区无限（例如常返区后拖着无限长的「逃离尾巴」），$m$ 步块论证失效，占据概率可能只按幂律衰减（如 $1/n$），$E[T]$ 也可能无穷——有限性是这里一切指数速率的命根子。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题证明用了「改造参照系 + 调用上一题」的双层把戏，值得抽出来当模板。第一性原理：要证「进过一次的常返态以后还会再来」，最干净的办法是把它变成一个「吸收态」——在原问题上改造出一条临时链 $p_{ss}=1$（把 $s$ 变成只出不进的吸收点），于是 $s$ 之外的所有状态在新链里都是暂态（因为不能再回 $s$）。这时上一题 Problem 7(b) 恰好告诉我们：几乎必然在有限时间内进入某个常返状态；而新链唯一能成为常返的就是吸收态 $s$，于是几乎必然到达 $s$。由于改造仅当 $s$ 首次被访问前才与原链一致，一旦 $s$ 被访问，就重复同样论证（把计数清零重新出发），从而 $s$ 被访问无穷多次。这套「把对象变成吸收态 → 借有限链必入常返」的手法，是许多「几乎必然进入 / 几乎必然无穷次」结论的统一骨架。命名模板：可叫它「吸收化 / absorption-fication 参照链」，本质是「把目标事件做成吸收面，再把概率丢进去」。跨课程（第 6 章 / 概率论公理）：这一步把「回到状态」的长期事件换算成「每个区块都几乎必然发生」的无穷事件；配合 Problem 7 的 $P(A)=0$ 手法，其实是 Borel–Cantelli 定理的雏形——若各次「回来」概率的和趋于无穷、且不越界，则无穷次发生。反例兜底：若把「进来一次」替换成「从暂态进入常返类」则不成立——除非从常返类内部出发；而上面「吸收化」的意义恰在把这一颠簸理顺。这正是「常返 = 访问无穷次」在概率 1 意义下的确切含义，命题 7.后面的吸收/平均递归时间都建立在这根基石上。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问把「周期/非周期」判断题全部化归为一条初等数论事实，是全章最有「做减法」味道的证明。第一性原理：周期之所以是「最大公约数 $d$」，是因为一个常返类里「回到某状态的所有可行回路长度」是一个对未来可加集合 $Q$（两条回路能且只能拼接成一长回路，故 $Q+Q\subseteq Q$）。把 $Q$ 的各元素求 gcd 得 $d$：若 $d>1$，则所有返回时间的长度都落在某个同余类里，于是把类按「到 $i$ 的步数 $\bmod d$」切成 $d$ 个不相交子集 $S_1,\dots,S_d$，任何一次转移都必然从这里跳到下一块，这就是周期分层；若 $d=1$，则 $Q$ 的 gcd 是 1，坚持用数论引理「gcd 为 1 的集合能生成全部（除有限个外的）正整数」，便可让任意两状态间的转移时间都正概率可达，链非周期。命名模板：整套方法可叫「gcd 分辨 / 返回时间 gcd 分层法」——先看返回时间集合的最小公因数，再决定分层还是可生成。跨课程（6.042J 数论 + 本单元周期定义）：gcd 引理的证明（反复取集合中两元素之差 $g$，证 $g$ 必为更大公因子 → 矛盾得 $g=1$）本质是「欧几里得算法」的集合版；这与「两互素步长能走遍充分大的所有整数」同源，也回答了第一章随机游走里「为何偶数/可自由拼接」的困惑。反例兜底：一个二部图（所有回路长度 $2,4,6,\dots$）的 $d=2$，可切成奇偶两块，属于周期情形（i）；立即对照：给某个状态补一条自环，$Q$ 里一下多出奇数长度，gcd 变 1，跳到 (ii) 的非周期情形。同一张图，是否周期只取决于「返回长度能拼出 1 吗」这一票之差——数论事实正是这「一票」的裁判。

---

<span style="color:#c0392b;">**SECTION 7.3　Steady-State Behavior（稳态行为）**</span>

<span style="color:#2471a3;">**[problem]**</span>  <span style="color:#c0392b;">**Problem 10.**</span>

> <span style="color:#7f8c8d;">第 7 章习题区的英文题干保持英文原题，不翻译，此处仅作题号定位。</span>

Consider the two models of machine failure and repair in Example 7.3. Find conditions on $b$ and $T$ for the chain to have a single recurrent class which is

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页在 Problem 10 题干「…a single recurrent class which is」处被换页符截断，引导性从句的其余内容（该句后续成分及可能的 (a)/(b) 小问）延续到下一页，本页未出现，不臆造。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 尽管题干被换页截断，仍能提炼出它想考察的核心理念：在 Example 7.3 的「机器故障维修」两类模型里，「何时只有一个常返类」完全取决于你如何把「维修/更换」周期织进状态空间。第一性原理：有限状态链必有常返类；要「恰好一个非周期的单一常返类」，等价于说「从任何状态，都能以正概率到达这个唯一常返类、并对其它任何状态不会滞留」。两个模型的差别，在于把「已经连续损坏多少天」是否编成状态：若维修有去无回（一次性更换成崭新的机器），那么「正在更换」这一过程只是一个到达新机器的暂态走廊，关键在换新的那一步以正概率把状态弹回运转族，于是全链凝结成单个常返类；反倒是若留了一个「永远卡住、再也回不去」的暂态出口，常返类就不再唯一。命名模板：可以叫「唯一常返类判据（unique recurrent class criterion）」，判断方法即「把图化成 SCC 凝聚图，看是不是只有一个 sink」。参数 $b$ 与 $T$（损坏持续天数、更换周期）正是决定「能否从任一状态回到同一族」的旋钮——例如让「更换后必回 new」这一跳概率为正、且维修途中不回原点，则常返类就是那台「好机器」的全体状态。跨课程（6.042J 强连通分量 / 本单元 Problem 5 的周期视角）：所谓唯一常返类正是「可达图只有一个 sink SCC」；若不小心让两个分支互不可达但内部各自常返，就会出现两个常返类。反例兜底：把「维修设施永远坏掉、机器永远停在坏态」的状态留着不去掉，就人为制造了第二个常返类——这类「信心满满却漏了出口」正是这类判据题最常见的失分点。

---
<!-- ===== PDF p394 ===== -->
<span style="color:#c0392b;">第 7 章　马尔可夫链（Markov Chains）</span> — 习题区（Problems，续）

> <span style="color:#7f8c8d;">[原页 OCR 严重损坏] 本页为第 7 章章末 Problems 习题区，处于后半段（页面上可见 Problem 11、Problem 12 及其后一题）。源页 OCR 被打乱成大量碎片，且很多数值/系数、题号、图与小题编号残缺。下面对两张凭可靠来源（教材原文转录）可完整还原的题给出还原双语；对过度损坏的一题仅保留可辨认片段，并在行内用灰注释标明占位，**不臆造任何转移概率、系数或小题原句**。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 11（教授的试题难度在 hard/medium/easy 间循环，求稳态概率）</span>

A professor gives tests that are hard, medium, or easy. If she gives a hard test, her next test will be either medium or easy, with equal probability. However, if she gives a medium or easy test, there is a 0.5 probability that her next test will be of the same difficulty, and a 0.25 probability for each of the other two levels of difficulty. Construct an appropriate Markov chain and find the steady-state probabilities.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道「出题难度循环」习题是求解稳态概率的基础操练：它让你亲自把「题目难度状态」装成一条不可约、非周期、有限的链，再解剩下的线性方程组。第一性原理：三条状态（hard/medium/easy）从条件里读出来，hard 之后各半跳到 medium/easy，medium/easy 之后各按 $0.5$ 同难度、$0.25/0.25$ 到另两级——于是转移矩阵唯一确定。稳态概率 $\pi$ 满足平衡方程 $\pi P = \pi$ 加上归一化 $\sum \pi=1$；只要你确认链不可约非周期（这里每个状态经正概率都能到其它状态且可回），定理保证解存在且唯一、且恰恰是长期占据比例。命名模板：把这种「默认各题难度能自由往返 → 稳态解存在唯一」的固定流程叫「平衡方程 + 归一化法」；它和染色马尔可夫链、词典翻页、网页跳转的稳态问题共用同一套方程，只是系数不同。跨课程（Strang 18.06 特征向量/谱论）：$P$ 的稳态就是特征值 1 的左特征向量，除去归一化才唯一；若出现两个互相不可达的常返类，就是特征值 1 有「重根」，稳态态不再唯一——这正是「为何要检验常返类多少」的代数底色。反例兜底：若把 hard 后的概率抄错成「永远 hard 自循环」，链立刻多出常返类或失去不可约，稳态概率随之翻车。结论：本题答案是一组干净的比例（$\pi_{\text{H}}:\pi_{\text{M}}:\pi_{\text{E}}$），验算时把三个方程解回归一化，就看得出自洽。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这道出生-死亡链的「条件概率（given a change of state）」把视线从「每一时刻」挪到「每观测到一次状态改变」——这正是连续时间链与嵌入链（embedded chain）的接口。第一性原理：死亡型链从状态 $i$ 出发，每次「确实发生状态改变」的概率是「这次真的动了」；而条件「改变」等价于「这一次观测到的是出生还是死亡」。把自转移 $\lambda_i+\mu_i$ 之外那部分的概率照比例重归一化，就得到「当它动了一次，往上是出生、往下是死亡」的条件分布——瞬时率之比 $\lambda_i : \mu_i$。这组量把离散马尔可夫链里「每步也许停在原地」的闲聊抹掉，只剩「真正跳变」的骨架，正是连续时间链里「在状态 $i$ 停留任意时长后再以速率比选下一个去向」的离散投影。命名模板：可叫「jump chain / 跳变骨架」，凡先给速率（rate）再定去向的模型都可拆成「时钟 + 转移核」两层，慢速率链就是右侧 $\frac{\lambda_i}{\lambda_i+\mu_i}$ 形式的条件概率。跨课程（§7.5 生灭过程 / 排队论 M/M/1）：排队论里算「到达 vs 服务完成的先后」全是这类「速率比」条件概率；也正好预告了下一节连续时间链条的构造逻辑。反例兜底：若链全是自转移（$p_{ii}=1$），「条件在状态改变上」的概率分布就是空集，量无穷大/未定义——所以这类问题一律要求「存在正概率改变」，这也是（f）（g）都先设「it resulted in a change of state」的用意。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 14**</span>（非周期、单一常返类的马氏链的近似多步转移概率）

Consider a Markov chain with given transition probabilities and with a single recurrent class that is aperiodic. Assume that for $n \geq 500$, the $n$-step transition probabilities are very close to the steady-state probabilities.

(a) Find an approximate formula for $P \left( X_{1000} = j,\, X_{1001} = k,\, X_{2000} = \ell \mid X_0 = i \right)$.

(b) Find an approximate formula for $P \left( X_{1000} = i \mid X_{1001} = j \right)$.

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 本题把「$n$ 步转移概率趋近稳态」这条 §7.3 结论物化成长程联合概率的近似公式，训练你在稳态达成后怎样做「马尔可夫骨架」的拆解。第一性原理：已知对 $n\ge500$，$n$ 步转移概率逼近稳态 $\pi$，所以从 $X_0$ 出发到 $X_{1000}$ 已经「忘了起点」——$P(X_{1000}=j\mid X_0=i)\approx\pi_j$。又因为链只有一步记忆，(a) 里给定 $X_{1001}=k$ 之后，$X_{2000}$ 相对 $X_{1001}$ 又可被稳态近似（999＋步足够），于是联合近似分解为 $P(X_{1000}{=}j,\,X_{1001}{=}k,\,X_{2000}{=}\ell \mid X_0{=}i)\approx \pi_j\, p_{jk}\,\pi_\ell$，中间那一步 $p_{jk}$ 是唯一「还没被稳态吞掉」的精确信息。命名模板：这种「长程处用稳态填空、短缝保留一步转移」的策略可叫「steady-state plug-in / 稳态填空法」，是混合时间（mixing time）之后做长程事件概率的标准招。跨课程（§7.3 收敛定理 + 马尔可夫性的连锁）：它也道出「多步联合概率 ≈ 若干稳态与少量转移的乘积」的直观——链条越长，独立化程度越高；(b) 里用条件概率公式把「给 $X_{1001}=j$ 时的 $X_{1000}$」反过来算，正是可逆/整理时的标准转向，答案近似回到 $\pi_i$ 或相应转移比。反例兜底：假设链在 $n=500$ 才真正收敛；若链是「高耗散/慢混合」，实际混合时间可能远大于 500，这时 $X_{1000}$ 还没到稳态，直接用 $\pi_j$ 填就会错——所以「已知 $n\ge500$ 很近稳态」这一前提是整道题成立的命门，换个慢链它立刻崩。这也是「先估 mixing time、再谈稳态近似」这一工程直觉的由来。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 15**</span>（Ehrenfest 扩散模型，diffusion）

**Ehrenfest model of diffusion.** We have a total of $n$ balls, some of them black, some white. At each time step, we either do nothing, which happens with probability $f$, where $0 < f < 1$, or we select a ball at random, so that each ball has probability $(1-f)/n > 0$ of being selected. In the latter case, we change the color of the selected ball (if white it becomes black, and vice versa), and the process is repeated indefinitely. What is the steady-state distribution of the number of white balls?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Ehrenfest 扩散模型是最早展示「物理系统会自发性地走向均衡分布」的玩具，而本文要求只用马尔可夫链稳态导出它的答案。第一性原理：记状态 $k$＝白球数。每步以 $(1-f)$ 概率随机挑一个球变色：选中白球（$k\to k-1$）的概率 $(1-f)\tfrac{k}{n}$，选中黑球（$k\to k+1$）的概率 $(1-f)\tfrac{n-k}{n}$，其余概率留在原地。直接解 $m+1$ 个未知的线性方程组可行，但更快、也更物理的是用可逆性（reversibility / detailed balance）：在稳态下相邻两态之间向上与向下的「概率流」必须相等，即 $\pi_k\cdot (1-f)\tfrac{k}{n} = \pi_{k+1}\cdot (1-f)\tfrac{n-k}{n}$，一递推就得 $\pi_k \propto \binom{n}{k}$——白球数服从 $\mathrm{Bin}(n,\tfrac12)$。命名模板：把「用相邻流的相等反向推出稳态」叫「detailed balance / 细平衡法」，它比解全体平衡方程省力得多，凡是「只在与自己相邻的状态间流动」的链（生灭型）都适用。跨课程（§7.3 平衡方程 + 热力学直觉 + Problem 12/16）：细平衡正是「微观可逆 → 宏观均衡」的骨架，也把本题与生灭过程、以及下一题的 Bernouilli–Laplace 两坛模型连成同一族；自转移概率 $f$ 被巧妙地约掉了，说明留步率不影响均衡分布形状。反例兜底：链并非一定可逆——若「向上」与「向下」不对称到流无法配对，就不存在细平衡，只能回到完整平衡方程 $P\pi=\pi$ 硬解；本题恰是对称、可逆的幸运儿。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 16**</span>（Bernoulli–Laplace 扩散模型，diffusion）

**Bernoulli–Laplace model of diffusion.** Each of two urns contains $m$ balls. Out of the total of the $2m$ balls, $m$ are white and $m$ are black. A ball is simultaneously selected from each urn and moved to the other urn, and the process is indefinitely repeated. What is the steady-state distribution of the number of white balls in each urn?

> <span style="color:#1e8449;">[note] Note（译者注）:</span> Bernouilli–Laplace 两坛模型是 Ehrenfest 的「加冕版本」：不再是挑一颗球变色，而是从两个坛同时各抽一颗互换。第一性原理：过程每一步选出的一颗从坛 1 移到坛 2、另一颗反向移回，总数在各坛内守恒；关键的简化是「每个具体的『球配置』都是可逆且等权的」——从配置 $A$ 到配置 $B$ 与从 $B$ 到 $A$ 的互换概率相等，细平衡（detailed balance）成立。于是稳态下每个满分配置概率相同，剩下就是计数：问「坛 1 里有 $k$ 颗白球」的稳态概率，即「在全部 $\binom{2m}{m}$ 种「$m$ 白 $m$ 黑」的颜色分配里，坛 1 恰好买到 $k$ 颗白的占比」——这就是超几何分布。命名模板：把「配置等权 → 稳态就是均匀枚举配置 + 数组合」的路子叫「uniform-configuration 法」；它是玻尔兹曼「各微观态等先验」在离散马尔可夫上的化身。跨课程（§7.5 生灭 / 扩散 + Problem 15 + 组合计数）：本题把「出生-死亡」从单变量 $k\to k\pm1$ 推广到「两坛联动的置换」，但稳态仍由可逆性给出来，与 Ehrenfest 的单侧守恒 $k$ 统计（二项 $\tfrac12$）构成对照：这里多一维调制、是超几何而非二项。反例兜底：若是「各抽一颗但稍不对称」的规则（如抽球概率不等），配置就不再等权、细平衡破裂，超几何答案失效，只能回头解 $\pi P=\pi$ 的大型方程组——对称性一旦松动，简洁稳态立刻蒸发。本题恰恰展示了「对称可逆 → 组合计数直接出头」这条捷径的力量。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 停车场门禁问题是「长期平均更换频率」的经典折算，答案其实是一条「每台门一生平均可服役的天数」的反数。第一性原理：可以用一条「从刚装好的门倒计时其剩余寿命」的马尔可夫链来读——记状态为「这台门已用了 $j$ 天」，每到新一天要么以概率 $P$ 被撞毁、要么再撑一天，到第 $m$ 天即按月保养强制换掉。更换就发生在「这一天的生命周期终了、装下一台新门」的那个时刻。长期看，「每次更换后重新计时」让过程进入一个由「门的使用周期」构成的再生成（renewal）结构：长期更换频率恰好等于「每个周期长度的期望的倒数」$1/(\mathbb{E}[\text{lifetime}]+1)$。这样就不必真的解全体平衡方程，只需算明「每台门平均能用多少天」（等于 $\mathbb{E}[T]$，其中 $T$ 是「要么撞毁要么撑满 $m$ 天」的最小者），频率即为它的倒数。命名模板：可叫「再生频率公式 / renewal-rate 法」——凡「事件发生后从头再算、天然重置」的系统，长期事件率都收敛到周期期望的倒数，这是比「稳态概率 × 转移率」更直观的一招。跨课程（§7.3 稳态频率 + 期望寿命 §7.4 吸收时间 + 排队/可靠性工程）：门的使用寿命建模正是吸收链里「$\mathbb{E}[\text{absorption time}]=$ 平均首达时间」的用武之地；也直接对应马氏链「长期访次率 = 稳态」的 (c)。反例兜底：若把「月保养」与「撞毁」两个终止条件算错（少算了保养当天也算一次服役），周期期望就偏，频率随即偏——这类题最易漏算的就是「服役满 $m$ 天的那天也算一次服役」的边缘情形。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问把「从不同初始状态出发的两条同参数链，最终是否『吞并』成同一条」转化成一个可量化的事件——它们的相遇时间 $T$。第一性原理：既然两条链从事后相遇点之后拥有完全相同的一步转移规则，那么从相遇那一刻起它们「永远并列而行」，任何未来走位都一致；因此「$X_n$ 与 $Y_n$ 落在同一状态」这件事，其分布差完全被「还没相遇」($T>n$) 的几何上界所控制。剩下要做的，是给 $T$ 的长尾找个几何上界：由于常返类不可约非周期，存在某个状态 $\ell$ 和一个固定窗口 $n$，使两链在同一个窗里同时落进 $\ell$ 的概率至少 $\beta^2>0$，于是每个长度 $n$ 的窗「都错过」的概率被一个固定因子 $1-\beta^2$ 累积压低，得到 $P(T>kn)\le(1-\beta^2)^k\le c\gamma^{kn}$。命名模板：这就是「coupling（耦合）法」的骨架，用它可给出「全变差距离（total variation）$\le P(T>n)$」这类衡量两链分布贴近度的最干净上界。跨课程（§7.3 收敛定理 + 概率收敛速率）：耦合是现代马氏链「混合速度」证明的标准武器——两条链能相遇 ⇔ 分布充分趋同；本题正是它在手工层面的演示。反例兜底：若链是周期的（如相绕而行的对位），两链会永远「恰好错过」，相遇时间没有几何尾巴，$P(T>n)$ 变得很慢——这印证了「非周期」在本题假设里不可省。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这是整份「稳态收敛定理」的收官一步，靠的是单调有界加两面对夹（sandwich/挤压）。第一性原理：定义随初始状态变化的上下包络 $\bar q_j(n)=\max_i T_{ij}(n)$ 与 $\underline q_j(n)=\min_i T_{ij}(n)$——所谓「从任一状态出发的尽量好与尽量差」。配合 Chapman–Kolmogorov 的向前一步 $T_{ij}(n+1)=\sum_k p_{ik}T_{kj}(n)$，可证上包络单调不增、下包络单调不减（把 $\max/\min$ 之后再做线性组合仍被包络框住）；而两条单调有界序列必收敛，加之 (c) 得到的包络间距被 $c\gamma^n$ 压到 0，故两包络收敛于同一极限 $\pi'_j$。真正的 $T_{ij}(n)$ 被上下包络夹住，自然也被逼到同一个 $\pi'_j$——且极限对 $i$ 统一，这正是「稳态与起点无关」的总根源。命名模板：把「用单调包络收敛 + 夹逼定极限」叫「squeeze / 夹逼证法的马尔可夫版」，是证明 $\lim T_{ij}(n)$ 存在且与 $i$ 无关的标准招数。跨课程（§7.3 稳态收敛 + 实数完备性夹逼 + Strang 谱论）：单调有界 + 间距压零这两件套，几乎是所有马氏链收敛定理的通用引擎；(c) 的几何间距正是「第二特征值收缩」在概率层的表现。反例兜底：若链是周期的，上下包络不夹到一点而在两值间振荡，$T_{ij}(n)$ 不再收敛，只在循环子类上摆动——这解释了为何周期性破坏「极限存在」，使收敛只能以平均（Cesàro）意义达成。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问把「稳态解唯一」提升成了「无论周期与否都成立」的普适结论，技巧是在原链上「每个状态都补一条自环（self-loop）增肥」，把它变成非周期的那把保护伞。第一性原理：(a) 的直达路径是「把一个（非周期的）解当作初始分布，让链跑无穷久」——若 $\pi''$ 是平衡方程的解，把它摊到 $X_0$ 上，则链处处保持在 $\pi''$；另一方面由 Problem 19，从任何态出发 $T_{ij}(n)$ 都收敛到公共稳态 $\pi'$，故 $\lim P(X_n=j)=\pi'_j$，把两种说法拼起来就得到 $\pi''=\pi'$。(b) 处理周期情形：周期会让有效转移时间被 $d$ 整除而无法逐点收敛，但给每个状态补一条概率 $\alpha>0$ 的自环后，新链仍满足同一组平衡方程、却变成非周期（gcd 立即为 1）；对这条非周期新链套用 (a) 的唯一性，再读回平衡方程，原链的解也唯一。命名模板：把「用自环打散周期却不扰动平衡方程」叫「lazy(ization) / 惰化或自环增肥」——给它建模的成本是少换概率、多换可证性。跨课程（§7.2 周期 + §7.3 稳态 + 随机游走惰化）：给每条边加自环是谱论与马尔可夫蒙特卡洛加速的惯用手段，既有 Strang 谱论的投影味道，也呼应 Problem 17 两状态里「自环把 $\lambda_2$ 拉回 $\le 1$」的思路。反例兜底：若是「两个互相不可达的常返类」，即便增肥自环也救不回来——平衡方程会在两类之间给出任意配比的解，唯一性天然失效；所以「单一常返类」这一前提是 (a)(b) 共同的生命线。

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 这一问给稳态概率补上了「长期频率」的直觉尾巴：$\pi_j$ 不只是「长时间后落在状态 $j$ 的概率」，更是「每步平均造访 $j$ 多少次」在统计意义上的极限。第一性原理：定义 $V_{ij}(n)=\mathbb{E}[\text{前 }n\text{ 步造访 }j\text{ 的次数}\mid X_0=i]$。由于「造访次数」是各时刻指示函数之和 $\sum_{k=1}^n \mathbb{E}[I_k]$，而 $\mathbb{E}[I_k]=T_{ij}(k)$（单步概率的线性期望），所以 $V_{ij}(n)=\sum_{k=1}^n T_{ij}(k)$。左右同除 $n$ 得 $V_{ij}(n)/n=\tfrac1n\sum_{k=1}^n T_{ij}(k)$——这恰是 $\{T_{ij}(k)\}$ 的 Cesàro 平均。既然 $T_{ij}(k)\to\pi_j$（据 Problem 19），Cesàro 平均也收敛到同一极限（提示里那条分析事实），于是 $\pi_j=\lim V_{ij}(n)/n$。命名模板：把「用时间均值解释稳态」叫「long-run frequency / 长期访次率」；它和「空间均值」共同构成遍历性（ergodic）直觉的两面。跨课程（§7.3 稳态 + 大数定律 + 分析 Cesàro 求和）：这正是弱大数定律在马尔可夫不独立的场合的翻版——指标虽相关，但平均照旧收敛，Cesàro 事实替我们把「逐点趋稳」升级成「时间平均趋稳」。反例兜底：若链是周期的，$T_{ij}(n)$ 本身不收敛、只在若干值间振荡，此时单侧极限失效，可 Cesàro 平均 $V_{ij}(n)/n$ 仍收敛到 $\pi_j$——这就是「周期链也谈稳态但这必须按平均意义读」的精确理由，Problem 19 里那道坎在此被绕开。

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

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 22\* —— 双随机（doubly stochastic）矩阵</span>

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

> <span style="color:#1e8449;">[note] Note（译者注）:</span> 双随机（doubly stochastic）矩阵给全章画了个完美的句号：若每列（自然也包括每行）概率之和都为 1，那么均匀分布 $\pi_j=1/m$ 自动满足平衡方程。第一性原理：把 $\pi_j=1/m$ 代进平衡方程右端，$(1/m)\sum_i p_{ij}=(1/m)\cdot(\text{第 }j\text{ 列之和})=(1/m)$，正是左端 $\pi_j$——「此列和为 1」这一结构直接让均匀分布变成不动点；再叠加 Problem 20 的唯一性（单一不可约常返类且已非周期），这个解就是唯一稳态。(c) 即便常返类变成周期，均匀解仍是平衡方程＋归一化的唯一解：取一个取到最大值的 $q=\pi_j$，由平衡方程和列和为 1 推出所有用到 $\le$ 都得变成等号，进而沿正概率路径把 $q$ 传遍整个常返类。命名模板：把「列和也是 1 → 稳态是均匀分布」叫「doubly stochastic ⇒ uniform steady state」；正则图、以及每步等概率挑一邻点的链（如 Example 7.7 随机游走）都满足。跨课程（Strang 18.06 谱论 + 图论正则图 + PageRank）：双随机正是「转移矩阵 $P$ 每个行与列和都是 1 ⇔ $\mathbf{1}^\top$ 同时是左、右特征向量」，均匀分布就是左特征向量 $\mathbf 1$ 归一化所得；这也在暗中呼应网页 PageRank 里「每行归一化是不均匀、每列也归一则均匀」的分野。反例兜底：若某列和 <1（信息在列方向「泄漏」），均匀分布就被打破，稳态偏向「入流多」的那列对应的状态——把「漏列」vs「保列」对照，就能看清均匀性完全来自「列守恒」，这也是 (c) 里要检查列和的用意。

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
