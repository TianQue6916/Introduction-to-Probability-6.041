# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 7 — Multiple Discrete Random Variables: Expectations, Conditioning, Independence（多个离散随机变量：期望、条件化与独立性）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; review（本讲大纲与复习）</span>

**阅读（Readings）**：学完教材第 2 章。

**本讲大纲（Lecture outline）**：
- 多个随机变量（multiple random variables）：
  - 联合分布列（joint PMF）。
  - 条件化（conditioning）。
  - 独立性（independence）。
- 期望专题（more on expectations）。
- 二项分布重温（binomial distribution revisited）。
- 帽子问题（a hat problem）。

**复习（Review）**：单变量的 PMF（分布列）、两变量的 joint PMF（联合分布列）与 conditional PMF（条件分布列），再加上把它们连在一起的两条关系式：
```math
p_X(x) = P(X = x), \qquad p_{X,Y}(x,y) = P(X = x,\, Y = y), \qquad p_{X|Y}(x \mid y) = P(X = x \mid Y = y),
```
```math
p_X(x) = \sum_y p_{X,Y}(x,y), \qquad p_{X,Y}(x,y) = p_X(x)\, p_{Y|X}(y \mid x).
```

> <span style="color:#7f8c8d;">Bertsekas §2.5, p.92–94；§2.6, p.97–101</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲是教材第 2 章的收官：Readings 要求学完全部第 2 章——经核对教材页码，第 2 章正文到 p.118 结束，p.119 起进入习题（Problems）。右栏 Review 把前几讲攒下的五个公式一次摆上台面：联合分布列的定义在 p.92，由联合分布列按行、列求和得到的 marginal PMF（边缘分布列）在 p.93，期望值规则在 p.94，条件分布列与乘法公式在 p.98 与 p.100–101。本讲的任务是把这些两变量工具推广到任意多个随机变量，并补齐期望、方差在多维与独立性下的运算规则。大纲后两块“二项分布重温”与“帽子问题”是两台应用演示机：前者展示指示变量分解如何干净利落地算出二项分布的均值与方差，后者展示同样的技术在完全相依的场合依然给出与 $n$ 无关的漂亮答案。学完本讲，第 2 章“离散随机变量”这座大厦就封顶了。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Independent random variables（随机变量的独立性）</span>

- 乘法公式可以沿链条延伸，得到三变量的 chain rule（链式法则）：
```math
p_{X,Y,Z}(x,y,z) = p_X(x)\, p_{Y|X}(y \mid x)\, p_{Z|X,Y}(z \mid x, y) .
```
- **随机变量的独立性**（independence of random variables）：称 $X, Y, Z$ 相互 independent（独立），若对**所有**取值 $x, y, z$ 都有
```math
p_{X,Y,Z}(x,y,z) = p_X(x) \cdot p_Y(y) \cdot p_Z(z).
```

**课堂例题**：$X$ 与 $Y$ 的联合分布列如下表（空白格表示概率为零）：

| $y \backslash x$ | $1$ | $2$ | $3$ | $4$ |
|:---:|:---:|:---:|:---:|:---:|
| $4$ | $1/20$ | $2/20$ | $2/20$ | |
| $3$ | $2/20$ | $4/20$ | $1/20$ | $2/20$ |
| $2$ | | $1/20$ | $3/20$ | $1/20$ |
| $1$ | | $1/20$ | | |

> <span style="color:#7f8c8d;">图：二维格点表——横轴 $x = 1, \ldots, 4$，纵轴 $y = 1, \ldots, 4$，每格标注 $p_{X,Y}(x,y)$（以 $1/20$ 为单位），共 10 个非零格，质量和为 $1$；此表即教材 Fig. 2.15 所用的分布列，事件 $\{X \le 2,\ Y \ge 3\}$ 对应图中左上方加阴影的窗口。</span>

- **课堂提问一**：$X$ 与 $Y$ 独立吗？$\underline{\qquad}$
- **课堂提问二**：若改以事件“$X \le 2$ 且 $Y \ge 3$”对联合分布列做条件化，结论又如何？$\underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.6, p.101, p.103；§2.7, p.109–113</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 先验算表格：10 个非零格子相加得 $20/20 = 1$ ✓。判断“不独立”最干净的抓手是不可能格：$p_{X,Y}(1,1) = 0$，但 $p_X(1) = 3/20$、$p_Y(1) = 1/20$ 都为正，乘积 $3/400 \ne 0$ ✓；用格 $(2,3)$ 检验同样失败：$p_{X,Y}(2,3) = 4/20 \ne p_X(2)\, p_Y(3) = \tfrac{8}{20} \cdot \tfrac{9}{20} = 72/400$ ✓。条件化重算：把 $A = \{X \le 2,\ Y \ge 3\}$ 窗口外的格子全部删去，窗口内 4 格 $(1,3),(1,4),(2,3),(2,4)$ 的原值 $2/20,\ 1/20,\ 4/20,\ 2/20$ 除以 $P(A) = 9/20$，得条件联合分布列 $2/9,\ 1/9,\ 4/9,\ 2/9$。此时边缘为 $p_{X|A}(1) = 3/9 = 1/3$、$p_{X|A}(2) = 6/9 = 2/3$，$p_{Y|A}(3) = 6/9 = 2/3$、$p_{Y|A}(4) = 3/9 = 1/3$，逐一检验 4 个格子，$p_{X|A}(x)\, p_{Y|A}(y)$ 与条件联合分布列完全吻合 ✓——条件化之后竟然独立了。这正是教材 Fig. 2.15（p.111）的例子，书中给出的 $p_{X|A}$ 取值（$x = 1$ 时 $1/3$，$x = 2$ 时 $2/3$）与我们算出的完全一致。

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 第一性原理）:**</span> 这页最容易卡住的点是“条件化竟然能制造独立性”。关键在于把独立性理解为分布列（一族数）的性质，而不是变量固有的属性——它只问 $p_{X,Y}(x,y)$ 能否分解成两个边缘的乘积，删掉或重加权某些格子之后，分解性质当然可能从无到有。直觉上，原表的主力质量压在“对角”附近，把 $X$ 与 $Y$ 拴在一起，而事件 $A$ 恰好圈出一块乘积结构规整的窗口，窗口外的一切被清零后，剩下的 $2 \times 2$ 块恰好可分解。回看知识路径：Lec 03–04 的条件概率里你已经见过“条件化制造均匀性”（掷硬币问题中条件概率与硬币偏好 $p$ 无关），本例是它的升级版——条件化不仅能拉平分布，还能拆掉变量之间的依赖。教材（p.110–111）把这一现象归入 conditional independence（条件独立）名下，并强调条件独立与无条件独立互不蕴含。卡点预警：不要把“给定 $A$ 后独立”误读为“$A$ 与 $X$、$Y$ 独立”——前者是重加权后新分布列的性质，后者是另一回事。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Expectations（期望）</span>

**核心任务**：把 expectation（期望）的运算规则推广到多个随机变量。
```math
\mathrm{E}[X] = \sum_x x\, p_X(x), \qquad \mathrm{E}[g(X,Y)] = \sum_x \sum_y g(x,y)\, p_{X,Y}(x,y) .
```
- **一般警示**：$\mathrm{E}[g(X,Y)] \ne g(\mathrm{E}[X],\ \mathrm{E}[Y])$——期望运算不与任意函数交换。
- $\mathrm{E}[\alpha X + \beta] = \alpha\, \mathrm{E}[X] + \beta$。
- **期望的线性**（linearity of expectations）：$\mathrm{E}[X + Y + Z] = \mathrm{E}[X] + \mathrm{E}[Y] + \mathrm{E}[Z]$——对任意联合分布列成立。
- **若 $X, Y$ 独立**：
  - $\mathrm{E}[XY] = \mathrm{E}[X]\, \mathrm{E}[Y]$；
  - $\mathrm{E}[g(X)\, h(Y)] = \mathrm{E}[g(X)] \cdot \mathrm{E}[h(Y)]$。

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.87；§2.5, p.94, p.97；§2.7, p.110, p.112</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 期望值规则（expected value rule）的成立理由可以追溯到第一性原理。把样本空间按 $(X, Y)$ 的取值切成原子块 $\{X = x,\ Y = y\}$，$g(X, Y)$ 在每块上取常值 $g(x, y)$，块的权重是 $p_{X,Y}(x, y)$，“常值乘权重再求和”就是期望——这与 Lec 05–06 单变量情形的推导逐字相同，只是格点从一维铺成二维。警惕反例：取 $g = x^2$，则 $\mathrm{E}[X^2] = \mathrm{Var}(X) + (\mathrm{E}[X])^2 > (\mathrm{E}[X])^2$，教材 p.87 的警告 $\mathrm{E}[g(X)] \ne g(\mathrm{E}[X])$ 正源于此，幻灯片的二维版 $\mathrm{E}[g(X,Y)] \ne g(\mathrm{E}[X],\ \mathrm{E}[Y])$ 是同一警告的推广。验算 $\mathrm{E}[\alpha X + \beta] = \alpha\, \mathrm{E}[X] + \beta$：$\sum_x (\alpha x + \beta)\, p_X(x) = \alpha \sum_x x\, p_X(x) + \beta \sum_x p_X(x) = \alpha\, \mathrm{E}[X] + \beta$ ✓，末步用到归一性 $\sum_x p_X(x) = 1$。期望的线性（linearity of expectations）是本讲后面两台应用机器的总开关，请与下一节对照记忆——和的期望永远成立，和的方差要独立才成立。

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 页面底部两条由独立性解锁的规则值得单独咀嚼：$\mathrm{E}[XY] = \mathrm{E}[X]\, \mathrm{E}[Y]$ 与 $\mathrm{E}[g(X)\, h(Y)] = \mathrm{E}[g(X)]\, \mathrm{E}[h(Y)]$ 的证明在教材 p.110 只有寥寥三行——把联合分布列分解为边缘乘积后，双重求和拆成两个独立求和的乘积，第二个式子再代入 $g$、$h$ 的逐点常值性即可。对比之下，期望的线性根本不挑食：$\mathrm{E}[X + Y] = \mathrm{E}[X] + \mathrm{E}[Y]$ 对任意联合分布列成立，无论相依还是独立。这一不对称的根源是：求和只是同一张概率表格上的加权平均，而乘积 $\mathrm{E}[XY]$ 依赖联合分布列的具体形状，必须靠独立性把表格“拆开”。跨课程连接：用 Strang 线性代数的语言说，$\mathrm{E}[\cdot]$ 是随机变量空间上的 linear operator（线性算子）——对加法与数乘封闭，$\mathrm{E}[\alpha X + \beta] = \alpha\, \mathrm{E}[X] + \beta$ 正是线性加平移的合成。卡点预警：别把 $\mathrm{E}[XY]$ 当成 $\mathrm{E}[X]\, \mathrm{E}[Y]$ 的简写——两者一般不等，教材 p.112 的“独立随机变量事实汇总”把这条规则与方差和规则并列，是第 2 章的核心记忆点。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Variances（方差）</span>

- variance（方差）对缩放与平移的规则：
  - $\mathrm{Var}(aX) = a^2\, \mathrm{Var}(X)$；
  - $\mathrm{Var}(X + a) = \mathrm{Var}(X)$——平移不改变摆动幅度。
- 设 $Z = X + Y$。若 $X, Y$ 独立，则**方差和规则**成立：
```math
\mathrm{Var}(X + Y) = \mathrm{Var}(X) + \mathrm{Var}(Y) .
```
- **课堂填空**：
  - 若 $X = Y$，则 $\mathrm{Var}(X + Y) = \underline{\qquad}$
  - 若 $X = -Y$，则 $\mathrm{Var}(X + Y) = \underline{\qquad}$
  - 若 $X, Y$ 独立且 $Z = X - 3Y$，则 $\mathrm{Var}(Z) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.87；§2.7, p.112–113</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 三个空栏逐一验算。若 $X = Y$，则 $X + Y = 2X$，故 $\mathrm{Var}(X + Y) = 4\, \mathrm{Var}(X)$ ✓——不是 $2\, \mathrm{Var}(X)$，方差对尺度是二次的。若 $X = -Y$，则 $X + Y \equiv 0$，故 $\mathrm{Var}(X + Y) = 0$ ✓，完全对消的波动让和退化成常数。若 $Z = X - 3Y$，把 $-3Y$ 看成 $a = -3$ 的缩放，则 $\mathrm{Var}(Z) = \mathrm{Var}(X) + (-3)^2\, \mathrm{Var}(Y) = \mathrm{Var}(X) + 9\, \mathrm{Var}(Y)$ ✓，负号平方后消失——相减并不自动产生抵消。两条基础规则也可验算：$\mathrm{Var}(X + a) = \mathrm{E}[(X - \mathrm{E}[X])^2] = \mathrm{Var}(X)$ ✓，平移不改变摆动幅度；$\mathrm{Var}(aX) = \mathrm{E}[(aX)^2] - (a\, \mathrm{E}[X])^2 = a^2\, \mathrm{Var}(X)$ ✓，教材 p.87 给出成套推导。卡点诊断：$X = Y$ 与 $X = -Y$ 正是方差和规则的两个幽灵陷阱——独立时协变项消失，非独立时它可正可负，这就是独立假设的代价与回报。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Binomial mean and variance（二项分布的均值与方差）</span>

- 设 $X$ 为 $n$ 次独立试验（independent trials）中成功的次数，每次成功的概率为 $p$。按定义直接计算均值：
```math
\mathrm{E}[X] = \sum_{k=0}^{n} k \binom{n}{k}\, p^k (1 - p)^{n - k} .
```
- **换一条路**：引入指示变量
```math
X_i = \begin{cases} 1, & \text{if success in trial } i, \\ 0, & \text{otherwise}; \end{cases}
```
  则 $X = X_1 + X_2 + \cdots + X_n$。
- **课堂填空**：
  - $\mathrm{E}[X_i] = \underline{\qquad}$
  - $\mathrm{E}[X] = \underline{\qquad}$
  - $\mathrm{Var}(X_i) = \underline{\qquad}$
  - $\mathrm{Var}(X) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.5, p.96；§2.7, p.113–114</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 跨课程连接）:**</span> 命名模板——indicator decomposition（指示变量分解法）：把成功总次数写成 $X = X_1 + \cdots + X_n$，每个 $X_i$ 只记录第 $i$ 次试验的成败（Bernoulli（伯努利）变量）。先算微观：$\mathrm{E}[X_i] = p$ ✓，$\mathrm{Var}(X_i) = \mathrm{E}[X_i^2] - p^2 = p(1 - p)$ ✓，其中 0/1 变量的性质 $X_i^2 = X_i$ 是下一页帽子问题的同款引擎。再由期望的线性（无需独立性）得 $\mathrm{E}[X] = np$ ✓，由试验独立与方差和规则得 $\mathrm{Var}(X) = np(1 - p)$ ✓，教材分别记于 Example 2.10（p.96）与 Example 2.20（p.113）。对比幻灯片顶部 $\sum_k k \binom{n}{k} p^k (1 - p)^{n-k}$ 的直接求和——那是需要组合恒等式技巧的硬路，指示变量法三行结束战斗，口诀是“换目标、拆结构、用线性”。跨课程连接：你正在学的 CLRS 第 5 章 indicator random variable（指示随机变量）一节，在分析雇佣问题的期望雇佣次数时用的正是 $\mathrm{E}[X] = \sum_i \mathrm{E}[X_i]$，且同样不需要各指示变量相互独立。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The hat problem（帽子问题）</span>

- $n$ 个人把各自的帽子抛进一个箱子，再每人随机取出一顶。
- 记 $X$ 为拿到自己帽子的人数，求 $\mathrm{E}[X]$。引入指示变量：
```math
X_i = \begin{cases} 1, & \text{if } i \text{ selects own hat}, \\ 0, & \text{otherwise}; \end{cases}
```
- 于是 $X = X_1 + X_2 + \cdots + X_n$。
- **课堂填空**：
  - $P(X_i = 1) = \underline{\qquad}$
  - $\mathrm{E}[X_i] = \underline{\qquad}$
  - 各 $X_i$ 相互独立吗？$\underline{\qquad}$
  - $\mathrm{E}[X] = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.5, p.96–97</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 逐项验算：$P(X_i = 1) = 1/n$——帽子指派相当于给第 $i$ 个人在 $n$ 顶帽子里均匀抽一顶，由 symmetry（对称性）他拿到任何一顶的概率都相同 ✓（教材 Example 2.11，p.96–97 即此计算）。$\mathrm{E}[X_i] = 1 \cdot \tfrac{1}{n} + 0 \cdot (1 - \tfrac{1}{n}) = \tfrac{1}{n}$ ✓。独立性检验：$P(X_1 = 1,\ X_2 = 1) = \tfrac{1}{n} \cdot \tfrac{1}{n-1} \ne \tfrac{1}{n^2}$，故各 $X_i$ 不独立 ✓——第 1 个人拿走自己的帽子后，第 2 个人面对的是剩下的 $n - 1$ 顶。于是 $\mathrm{E}[X] = \sum_i \mathrm{E}[X_i] = n \cdot \tfrac{1}{n} = 1$ ✓。卡点诊断：期望的线性不要求独立，所以答案在完全相依的场合依然干净；更惊人的是它连 $n$ 都不依赖——两人乱拿或一万人乱拿，期望拿对自己帽子的人数恒为 1。跨课程连接：把 $n$ 顶帽子的指派看成 $n!$ 个等可能排列（Lec 04 的计数视角），$X$ 恰是 random permutation（随机排列）的 fixed point（不动点）个数——期望恒为 1，这正是 CLRS 随机化算法一章用指示变量处理的那类排列计数问题。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Variance in the hat problem（帽子问题的方差）</span>

- 从矩公式入手：$\mathrm{Var}(X) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2 = \mathrm{E}[X^2] - 1$。
- 把 $X^2$ 展开成对角与非对角两部分：
```math
X^2 = \sum_i X_i^2 + \sum_{i,\, j\,:\, i \ne j} X_i X_j .
```
- **课堂填空**：
  - $\mathrm{E}[X_i^2] = \underline{\qquad}$
  - $P(X_1 X_2 = 1) = P(X_1 = 1) \cdot P(X_2 = 1 \mid X_1 = 1) = \underline{\qquad}$
  - $\mathrm{E}[X^2] = \underline{\qquad}$
  - $\mathrm{Var}(X) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.87；§2.6, p.101</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 命名模板——**对角–非对角拆分法**：把 $X^2 = (X_1 + \cdots + X_n)^2$ 展开成对角项 $\sum_i X_i^2$ 与非对角项 $\sum_{i \ne j} X_i X_j$ 之和，对角项用 0/1 性质 $X_i^2 = X_i$ 化简，非对角项靠对称性打包。逐项验算：$\mathrm{E}[X_i^2] = \mathrm{E}[X_i] = 1/n$ ✓。非对角项必须动用 Lec 02–03 的乘法公式：$\mathrm{E}[X_1 X_2] = P(X_1 X_2 = 1) = P(X_1 = 1)\, P(X_2 = 1 \mid X_1 = 1) = \tfrac{1}{n} \cdot \tfrac{1}{n-1}$ ✓——两变量相依，$\mathrm{E}[X]\, \mathrm{E}[Y]$ 在此不可用。由对称性，$n(n-1)$ 个有序对的贡献完全相同，故 $\mathrm{E}[X^2] = n \cdot \tfrac{1}{n} + n(n-1) \cdot \tfrac{1}{n(n-1)} = 1 + 1 = 2$ ✓。最后 $\mathrm{Var}(X) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2 = 2 - 1 = 1$ ✓，矩公式见教材 p.87。对照本讲方差一节：$X_i$ 独立时可直接用方差和规则，恰因相依才被迫绕道 $\mathrm{E}[X^2]$——两种处境、两条路线，模板的价值正在于此；方差同样恒为 1、与 $n$ 无关，与均值交相辉映。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
