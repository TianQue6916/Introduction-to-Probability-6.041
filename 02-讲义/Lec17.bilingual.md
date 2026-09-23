# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 17 — Markov Processes — II（马尔可夫过程 II）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; review（本讲大纲与复习）</span>

**阅读**：教材 Section 7.3。

**本讲大纲（Lecture outline）**：
- 复习（Review）。
- 平稳行为（Steady-State behavior）：
  - 平稳收敛定理（Steady-state convergence theorem）。
  - 平衡方程（Balance equations）。
- 生灭过程（Birth-death processes）。

**复习（Review）**：
- 离散状态、离散时间、时齐（time-homogeneous）：
  - 转移概率 $p_{ij}$；马尔可夫性质（Markov property）。
- $r_{ij}(n) = P(X_n = j \mid X_0 = i)$。
- 关键递归（key recursion）：
```math
r_{ij}(n) = \sum_{k} r_{ik}(n-1)\, p_{kj} .
```

> <span style="color:#7f8c8d;">Bertsekas §7.1, p.340–345；§7.3, p.352</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲只做一件事：回答上一讲留下的收敛问题——$r_{ij}(n)$ 何时收敛、收敛到什么、怎么算。复习页摆出的三行是全部装备：时齐马尔可夫链的定义（$p_{ij}$ 不随时间变）、$n$ 步转移概率的含义、以及 Chapman-Kolmogorov 递归（教材 p.345）——注意最后的平衡方程（balance equations）就是对这个递归取极限得到的，所以"关键递归"这名字名副其实。今天的路线图：先补一块拼图——periodic states（周期态，§7.2 收尾、§7.3 开篇 p.352 接住）；然后陈述 steady-state convergence theorem（平稳收敛定理，p.352–353），给出收敛的两个前提条件（单一常返类 + 非周期）；接着从递归推出 balance equations（p.353–354）并配上频率解释（p.357 的 Long-Term Frequency Interpretations）；最后用 birth-death processes（生灭过程, p.357–362）展示平衡方程在一条链上大开杀戒。与前后讲的接续：上一讲的二状态例题已数值上看到 $5/7$、$2/7$，本讲要把"看到"升级成"算出并证明唯一"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Warmup（热身练习）</span>

> <span style="color:#7f8c8d;">图：9 状态分类示例链（与下两页"常返与暂态"所用为同一张图；弧上的转移概率数值未随文本提取保留）。</span>

- $P(X_1 = 2,\, X_2 = 6,\, X_3 = 7 \mid X_0 = 1) = \underline{\qquad}$
- $P(X_4 = 7 \mid X_0 = 2) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §7.1, p.345（n 步转移概率）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 两空的答案都以路径公式给出（讲义图中弧上的具体概率数值未随 OCR 保留，代入图中数值即得数值结果）。第一空：事件"$X_1 = 2$ 且 $X_2 = 6$ 且 $X_3 = 7$"就是沿路径 $1 \to 2 \to 6 \to 7$ 的转移，由乘法公式（Lec 02）逐段条件化：$P(X_1{=}2, X_2{=}6, X_3{=}7 \mid X_0{=}1) = p_{12}\, p_{26}\, p_{67}$ ✓——路径概率 = 各段转移概率连乘，这正是"链"之所以叫链的意义。第二空：$P(X_4 = 7 \mid X_0 = 2) = r_{27}(4)$，没有唯一路径，须**枚举求和**：用关键递归展开一层，$r_{27}(4) = \sum_k r_{2k}(3)\, p_{k7}$，其中 $k$ 取一切"三步内能从 2 到达、且一步可到 7"的状态；继续展开就是所有长度为 4 的路径的概率求和 ✓。两空合起来正好复述本讲的方法论：单条路径用乘法，多条路径用加法，$n$ 步整体用递归——Chapman-Kolmogorov 不是新公式，而是"乘法 + 加法 + 马尔可夫"的封装；这套"路径展开"与 6.006 里数 DAG（有向无环图）路径的递推一脉相承，只是那里数条数、这里按概率加权求和。第二问还预告了周期性：若某些回路长度有公因子 $> 1$，$r_{27}(4)$ 这类固定步数的概率会出现整块的零。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Periodic states（周期态）</span>

- 一个 recurrent class（常返类）中的状态是 periodic（周期）的，如果它们能被分成 $d > 1$ 个 group（组），使得所有从一组出发的转移都通向下一组。

> <span style="color:#7f8c8d;">图：与热身页相同的分类示例链（9 个状态）——用于观察哪些常返类天然带循环结构。</span>

> <span style="color:#7f8c8d;">Bertsekas §7.2, p.346；§7.3, p.352（周期类使 $r_{ij}(n)$ 振荡；Fig. 7.10 结构示意）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> 周期性说的是常返类的一种"列队行进"结构：把类内状态分成 $d$ 组并依次编号，所有转移只能从第 $k$ 组走到第 $k+1$ 组（末组绕回首组），于是每走一步组号 +1（模 $d$），每 $d$ 步才可能回到原组——教材 Fig. 7.10（§7.2 之末）画的就是 $d = 3$ 的三组循环。后果直接致命于收敛：从任一状态出发，$r_{ii}(n)$ 只在 $n$ 是 $d$ 的倍数时才可能非零，序列必然整块振荡（上一讲反例 $r_{22}(n) = 1, 0, 1, 0, \ldots$ 正是 $d = 2$ 的情形，教材 p.352 原话：generically oscillate）。卡点诊断一：周期性是**类**的整体属性——$d$ 是类内一切回路长度的最大公约数，只要有一条回路长度与 $d$ 不互素，$d$ 就得缩小。卡点诊断二：最快的判据（教材 §7.2 末）：常返类中某状态有自环（$p_{ii} > 0$），或存在 $n$ 使该类所有 $r_{ij}(n) > 0$，则类是非周期的（aperiodic）——自环让到达时刻的奇偶约束失效。定理的第二个前提"单一常返类且非周期"由此而来：前者保证极限与初态无关，后者保证极限存在。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Recurrent and transient states（常返态与暂态·复习）</span>

- 状态 $i$ 是 recurrent（常返）的，如果：从 $i$ 出发，且从你能到达的任何地方出发，都存在一条回到 $i$ 的路。
- 若非常返，则称为 transient（暂态）。
- **Recurrent class（常返类）**：彼此 "communicate"（互通）、且不与任何其他状态互通的常返状态之集合。

> <span style="color:#7f8c8d;">图：与热身页相同的 9 状态分类示例链——常返类是其中封闭互通的状态集团，暂态位于集团之外。</span>

> <span style="color:#7f8c8d;">Bertsekas §7.2, p.346（Example 7.2 与 Fig. 7.8）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板）:**</span> 本页是上一讲的复习回放，这里补一个可复用的判定模板——**"闭包检验法"**：第一步，在转移概率图上从 $i$ 做可达性搜索，得到从 $i$ 出发能到的全体状态 $A(i)$；第二步，检验 $A(i)$ 中每个状态是否都能回到 $i$（等价地，$A(i)$ 内每个状态彼此可达）；若都回到，则 $A(i)$ 是一个常返类（封闭 + 互通），$i$ 常返；若存在"只出不进"的状态，$i$ 暂态 ✓。教材 Example 7.2（§7.1 的苍蝇与蜘蛛）与 Fig. 7.8（§7.2：状态 1 常返、2 暂态、3 与 4 互达且常返）都是这个模板的演练题。为什么暂态必然"只被访问有限次、$P(X_n = i) \to 0$"？第一性原理：只要存在 $j \in A(i)$ 无法回到 $i$，而链以正概率到达 $j$，则由马尔可夫性质，到达 $j$ 后回访 $i$ 的大门永久关闭；重复独立的"逃离机会"终有一次成功（Lec 10 的 Borel–Cantelli 直觉），故 $i$ 的访问次数以概率 1 有限 ✓。这也解释了平稳行为为何只需研究常返类：暂态是"路过的站台"，不是"居住的城市"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Steady-State Probabilities（平稳概率）</span>

- $r_{ij}(n)$ 会收敛到某个 $\pi_j$ 吗？（与初始状态 $i$ 无关）
- 会，如果：
  - recurrent states（常返态）全部位于单一 class（类）中，**且**
  - 该单一 recurrent class（常返类）不是 periodic（周期的）。
- 假设"会"，从关键递归（key recursion）出发
```math
r_{ij}(n) = \sum_{k} r_{ik}(n-1)\, p_{kj}
```
  - 令 $n \to \infty$ 取极限：
```math
\pi_j = \sum_{k} \pi_k\, p_{kj}, \qquad \text{for all } j
```
  - 附加方程（additional equation）：
```math
\sum_{j} \pi_j = 1
```

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.352–354（Steady-State Convergence Theorem 与平衡方程）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 收敛定理（教材 p.352–353）的两个前提与上一讲的两幅反例一一对应：多常返类破坏"与初态无关"（落到哪个类取决于起点），周期性破坏"收敛"本身（整块振荡）。推导平衡方程只用一步——对关键递归两边取极限：$r_{ij}(n) = \sum_k r_{ik}(n-1) p_{kj}$ 中令 $n \to \infty$，右边 $r_{ik}(n-1) \to \pi_k$，左边 $r_{ij}(n) \to \pi_j$，得 $\pi_j = \sum_k \pi_k p_{kj}$ ✓（教材 p.354）。归一化 $\sum_j \pi_j = 1$ 补足方程组的秩亏损——教材 p.354 特别指出：任一条平衡方程都可由其余方程推出（其 Example 7.5 中两式同价于 $\pi_1 = 3\pi_2$；本讲的例题则是 $\pi_1 = 2.5\pi_2$），所以没有归一化就解不出唯一解。定理第三条给出生死簿：暂态 $\pi_j = 0$、常返态 $\pi_j > 0$——"路过的地方不留脚印"。最后一个概念锚点：$\pi_j$ 全体构成 stationary distribution（平稳分布，p.353）——若 $X_0$ 按它抽取，则对一切 $n$，$P(X_n = j) = \pi_j$ 不再漂移；"收敛到 $\pi$"与"从 $\pi$ 出发保持 $\pi$"是同一条方程的两种读法，这正是"平稳"二字的分量。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Visit frequency interpretation（访问频率解释）</span>

- 平衡方程：$\pi_j = \sum_k \pi_k p_{kj}$。
- (Long run) frequency of being in $j$（处于 $j$ 的长期频率）：$\pi_j$。
- Frequency of transitions $k \to j$（$k \to j$ 转移的频率）：$\pi_k p_{kj}$。
- Frequency of transitions into $j$（流入 $j$ 的转移频率）：$\sum_k \pi_k p_{kj}$。

> <span style="color:#7f8c8d;">图：各状态的转移频率 $\pi_1 p_{1j},\ \pi_2 p_{2j},\ \ldots,\ \pi_j p_{jj},\ \ldots,\ \pi_m p_{mj}$ 一并汇入状态 $j$（对应教材 Fig. 7.13）。</span>

- **（讲义援引教材）Expected Frequency of a Particular Transition（一类特定转移的期望频率）**：考虑单常返类、非周期的马尔可夫链自某初始状态出发的 $n$ 次转移。设 $q_{jk}(n)$ 为使状态从 $j$ 转到 $k$ 的转移的期望次数，则与初始状态无关地有
```math
\lim_{n \to \infty} \frac{q_{jk}(n)}{n} = \pi_j\, p_{jk} .
```
- （教材脚注）事实上还有更强的陈述：沿无限时间轴生成一条轨迹后，状态 $j$ 被访问的长期频率将**恰好**等于 $\pi_j$，从 $j$ 到 $k$ 的转移频率恰好等于 $\pi_j p_{jk}$；尽管轨迹随机，这些等式以 probability 1（概率 1）成立。

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.357–362（Long-Term Frequency Interpretations；Expected State Frequencies；Fig. 7.13）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 平衡方程最有味道的读法是"流量守恒"：$\pi_j$ 是系统长期停留在 $j$ 的时间占比（教材 p.357：$\pi_j = \lim_n \nu_{ij}(n)/n$，$\nu_{ij}(n)$ 为前 $n$ 步访问 $j$ 的期望次数）；每当链位于 $j$，下一步从 $j$ 走向 $k$ 的概率是 $p_{jk}$，故"从 $j$ 流向 $k$"的转移频率为 $\pi_j p_{jk}$；守恒式 $\pi_j = \sum_k \pi_k p_{kj}$ 说的是：**停留频率 = 各路流入频率之和**，自环 $\pi_j p_{jj}$ 也算一路（教材 Fig. 7.13 的原话：The sum of the expected frequencies of such transitions is the expected frequency of being at state $j$）✓。讲义援引的期望频率版（$\lim_n q_{jk}(n)/n = \pi_j p_{jk}$）与脚注的"概率 1"版本是两层强化——前者依期望取平均，后者几乎必然，100B 的极限语言在此分成两级。跨课程连接：把 $\pi$ 读成"每步平均行为"，与 6.006 摊还分析（amortized analysis）同构——那里把昂贵的偶发操作摊成长期平均代价，这里把随机轨迹摊成长期占比 $\pi_j$，都体现"逐点随机、长期确定"的平均化思想。下一页的生灭过程会展示：有了守恒式，方程常常只剩一阶递归那么好解。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example（例题：平衡方程求解）</span>

> <span style="color:#7f8c8d;">图：二状态链（同上一讲例题）——状态 1 自环 $p_{11} = 0.8$、$p_{12} = 0.2$；状态 2 自环 $p_{22} = 0.5$、$p_{21} = 0.5$。</span>

- **解**：平衡方程两条
```math
\pi_1 = 0.8\,\pi_1 + 0.5\,\pi_2, \qquad \pi_2 = 0.2\,\pi_1 + 0.5\,\pi_2 ,
```
两式等价（各自化简均为 $0.2\,\pi_1 = 0.5\,\pi_2$，即 $\pi_1 = 2.5\,\pi_2$）——任一条可由另一条推出，须补归一化 $\pi_1 + \pi_2 = 1$：
```math
2.5\,\pi_2 + \pi_2 = 1 \;\Longrightarrow\; \pi_2 = \frac{2}{7} \approx 0.286, \qquad \pi_1 = \frac{5}{7} \approx 0.714 .
```

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.354（Example 7.5：同型二状态链的平衡方程求解）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 验算：$0.2\,\pi_1 = 0.5\,\pi_2 \Rightarrow \pi_1 = 2.5\,\pi_2$；代入归一化 $3.5\,\pi_2 = 1$，得 $\pi_2 = 2/7 \approx 0.2857$、$\pi_1 = 5/7 \approx 0.7143$ ✓。反向核对：把 $\pi = (5/7, 2/7)$ 代回第二条方程，$\pi_2 \stackrel{?}{=} 0.2 \cdot \tfrac{5}{7} + 0.5 \cdot \tfrac{2}{7} = \tfrac{1 + 1}{7} = \tfrac{2}{7}$ ✓；再看频率解释：状态 1 的停留频率 $5/7$ 应等于流入频率 $\pi_1 p_{11} + \pi_2 p_{21} = \tfrac{5}{7}\cdot\tfrac{4}{5} + \tfrac{2}{7}\cdot\tfrac{1}{2} = \tfrac{4}{7} + \tfrac{1}{7} = \tfrac{5}{7}$ ✓，流量守恒闭合。与上一讲对照：$n = 100$ 时表格里填的 $(5/7, 2/7, 5/7, 2/7)$ 正是这里解出的 $\pi$——上一讲"迭代猜极限"，本讲"方程定极限"，且教材 Example 7.5（p.354）证明这个解是**唯一**的（平衡方程 + 归一化的解由收敛定理保证等于 $r_{ij}(n)$ 的极限）。卡点预警：解方程组时若两条平衡方程"解不出来"（无穷多解），第一反应不是惊慌，而是想起教材 p.354 的提示——它们必然线性相关，缺的只是归一化方程。收尾再强调书写纪律：平衡方程是"对每个状态写一条"，$m$ 个状态共 $m$ 条，其中必有且仅有一条是冗余的，连同归一化一共 $m$ 个独立条件，恰好定出 $m$ 个未知数——本例 $m = 2$，故"两条平衡方程取一条 + 归一化"就是全部；这个计数规律在下一页生灭过程中同样生效。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Birth-death processes（生灭过程）</span>

> <span style="color:#7f8c8d;">图：生灭链——状态 $0, 1, 2, \ldots, m$ 排成一条线；向上（"出生"）转移概率 $p_i$（从 $i$ 到 $i+1$），向下（"死亡"）转移概率 $q_{i+1}$（从 $i+1$ 到 $i$）；边界自环为 $1 - p_0$（状态 0）与 $1 - q_m$（状态 $m$）。</span>

- 局部平衡（local balance）：
```math
\pi_i\, p_i = \pi_{i+1}\, q_{i+1}
```
- 特例：$p_i = p$、$q_i = q$（对一切 $i$），记 $\rho = p/q$ = load factor（负载率）：
```math
\pi_{i+1} = \pi_i \cdot \frac{p}{q} = \pi_i\, \rho \qquad \Longrightarrow \qquad \pi_i = \pi_0\, \rho^i, \quad i = 0, 1, \ldots, m
```
- 设 $p < q$ 且 $m \approx \infty$：
```math
\pi_0 = 1 - \rho, \qquad \mathrm{E}[X_n] = \frac{\rho}{1 - \rho} \quad \text{（in steady-state，平稳时）}
```

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.357–362（Birth-Death Processes 与局部平衡方程；Fig. 7.14）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 局部平衡方程的来历是"割边守恒"：在图中把 $\{0, \ldots, i\}$ 与 $\{i+1, \ldots, m\}$ 之间只留一条边，长期看向上流量 $\pi_i p_i$ 必须等于向下流量 $\pi_{i+1} q_{i+1}$（教材 §7.3 的 local balance 论证）——比解全组平衡方程省事得多。特例验算：$\pi_{i+1} = \pi_i \rho$ 连乘得几何序列 $\pi_i = \pi_0 \rho^i$ ✓；归一化用几何级数（100B：$|\rho| < 1$ 时 $\sum_{i \ge 0} \rho^i = \frac{1}{1-\rho}$）：$\sum_i \pi_0 \rho^i = \pi_0 / (1-\rho) = 1$，故 $\pi_0 = 1 - \rho$ ✓；期望即几何分布均值：$\mathrm{E}[X_n] = \sum_i i (1-\rho) \rho^i = \frac{\rho}{1-\rho}$ ✓（对 $\sum \rho^i$ 逐项求导或错位相减皆可）。条件 $p < q$ 使 $\rho < 1$、级数收敛——"死亡率高于出生率，队伍才不会无界膨胀"。跨课程连接：$\rho = p/q$ 这个 load factor（负载率）与 CLRS 第 11 章哈希表的 load factor $\alpha = n/m$ 出奇一致——都是"每单位服务容量压了多少需求"；$\rho \to 1$ 时队列期望 $\rho/(1-\rho)$ 爆炸，正如哈希链长随 $\alpha$ 增长恶化——你在 6.006/算法进阶里熟悉的"负载因子决定性能"在此有了概率论意义上的精确曲线。生灭过程也是排队论（$M/M/1$ 队列）的离散时间雏形，值得把这道特例背下来。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
