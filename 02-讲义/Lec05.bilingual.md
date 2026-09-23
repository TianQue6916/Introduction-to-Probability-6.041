# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 5 — Discrete Random Variables; Probability Mass Functions; Expectations（离散随机变量、分布列与期望）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Random variables（随机变量）</span>

**阅读（Readings）**：教材 Sections 2.1–2.3，起步 Section 2.4。

**本讲大纲（Lecture outline）**：
- 随机变量（random variables）。
- 分布列（probability mass function，PMF）。
- 期望（expectation）。
- 方差（variance）。

**随机变量的定义**：给每一个 possible outcome（可能结果）赋一个值（数）。
- 数学上：一个从样本空间 $\Omega$ 到实数集的 function（函数）。
  - 取值可以是 discrete（离散）或 continuous（连续）的。
- 在同一样本空间上可以同时定义多个随机变量。
- 记号（notation）：
  - 随机变量用 $X$；
  - 数值取值用 $x$。

> <span style="color:#7f8c8d;">Bertsekas §2.1（本讲 Readings：§2.1–2.3，起步 §2.4）；§2.4, p.87–88</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这一页是整门课的转折点。前四讲里我们操作的对象是 event（事件）——样本空间的子集；从本讲起，主角换成 random variable（随机变量）——定义在 $\Omega$ 上的实值函数 $X: \Omega \to \mathbb{R}$。视角一换，工具箱立刻升级：既然结果被表示成数，就能求平均（expectation，期望）、度量摆动（variance，方差），整条概率律也被压缩成一个函数 PMF。用 CSAPP 的视角看，这一步相当于给每个样本点做 encoding（编码）——信息一旦被表示成数字，算术与比较运算就全部可用，后续所有推导都建立在这层"数字化"之上。卡点预警：$X$ 与 $x$ 的大小写分立不是排版习惯——$X$ 是函数，$x$ 是它可能取的具体数值，$P(X = x)$ 里二者各司其职，混写是初学最常见的笔误。同一样本空间允许多个随机变量共存，这一点从下一讲的 joint PMF（联合分布列）起将反复用到。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Probability mass function（PMF，分布列）</span>

- PMF 就是 $X$ 的 "probability law"（概率律），也叫 "probability distribution"（概率分布）。
- 记号：
```math
p_X(x) = P(X = x) = P(\{\omega \in \Omega \text{ s.t. } X(\omega) = x\}) .
```
- $p_X(x) \ge 0$，且 $\sum_x p_X(x) = 1$。
- **例**：$X$ = 掷出首次正面所需的抛硬币次数。
  - 设各次投掷 independent（独立），$P(H) = p > 0$：
```math
p_X(k) = P(X = k) = P(TT \cdots TH) = (1-p)^{k-1} p, \qquad k = 1, 2, \ldots
```
  - 这就是 geometric PMF（几何分布列）。

> <span style="color:#7f8c8d;">Bertsekas §2.1–2.2（本讲 Readings）；§2.6, p.105–106（Example 2.17 复述同一几何 PMF 并给出其均值方差）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 两条基本性质里，归一化对几何分布是一次非平凡检查：$\sum_{k=1}^{\infty} p_X(k) = \sum_{k=1}^{\infty} (1-p)^{k-1} p = p \cdot \dfrac{1}{1-(1-p)} = 1$ ✓——公比 $1-p \in (0,1)$ 的 geometric series（几何级数）恰使质量和为一，其收敛性你在 100B 实分析里已有严格工具（部分和单调有界）。卡点诊断：$p_X(x) = P(X = x)$ 的右端是"原像"的概率——$P(\{\omega \in \Omega : X(\omega) = x\})$。$X$ 把 $\Omega$ 上的概率质量"压"到实数轴上，同一个 $x$ 往往承接多个 $\omega$ 的质量，所以任何 PMF 计算的动作都是"收集所有满足 $X = x$ 的结果，把它们的概率加起来"——这正是下一页三步口诀的来源。另注意几何 PMF 的推导依赖独立性：$P(TT \cdots TH) = (1-p)^{k-1} p$ 是把 $k$ 次投掷的概率沿路径连乘，用的完全是 Lec 03 树模型的法则。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">How to compute a PMF（如何计算分布列）</span>

- 收集所有使 $X = x$ 的 possible outcomes（可能结果）。
- 把它们的概率相加。
- 对每个 $x$ 重复上述步骤。

**例**：一颗 fair tetrahedral die（公平的四面骰）独立掷两次。
- $F$：第一次掷出的结果；$S$：第二次掷出的结果。
- $X = \min(F, S)$。

> <span style="color:#7f8c8d;">图：$4 \times 4$ 格点表——横轴 $F = 1, \ldots, 4$（第一次掷出），纵轴 $S = 4, \ldots, 1$（第二次掷出），共 16 个等可能格；$X = \min(F, S)$ 的取值逐格可读。</span>

- 课堂填空：$p_X(2) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.1（本讲 Readings）；求和思想对照 §2.5, p.93 的 tabular method（表格法）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 验算填空 $p_X(2)$：样本空间是 $4 \times 4 = 16$ 个等可能格。直接数：$\min(F, S) = 2$ 的格子是 $(2,2), (2,3), (2,4), (3,2), (4,2)$，共 5 个，故 $p_X(2) = 5/16$ ✓。更值得带走的是第二条路——命名模板：**累积差分法**。$P(\min \ge 2) = P(F \ge 2)\, P(S \ge 2) = (3/4)^2 = 9/16$（两次投掷独立），$P(\min \ge 3) = (1/2)^2 = 1/4$，相减得 $9/16 - 4/16 = 5/16$ ✓。"至少"型事件往往好算，"恰好"型用相邻差分——这个模板在连续情形会升级为 $p_X(k) = F_X(k) - F_X(k-1)$（教材 §3.2, p.150 的 PMF–CDF 互化公式），此处已是它的雏形。$\min$ 与 $\max$ 型随机变量在教材 Example 3.6（三次考试取最高分，p.150–151）还会正式出场，这里先混个脸熟：凡是"多变量合取后取极值"，先算累积、再做差分。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Binomial PMF（二项分布列）</span>

- $X$：$n$ 次 independent coin tosses（独立掷硬币）中正面出现的次数，$P(H) = p$。
- 取 $n = 4$：
```math
p_X(2) = P(HHTT) + P(HTHT) + P(HTTH) + P(THHT) + P(THTH) + P(TTHH) = 6\,p^2 (1-p)^2 = \binom{4}{2} p^2 (1-p)^2 .
```
- 一般情形：
```math
p_X(k) = \binom{n}{k} p^k (1-p)^{n-k}, \qquad k = 0, 1, \ldots, n .
```

> <span style="color:#7f8c8d;">Bertsekas §2.2（本讲 Readings）；§2.7, p.113–114（Example 2.20：二项分布的均值与方差）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，跨课程连接 + 验证）:**</span> 二项 PMF 的两步结构值得拆开看：单条序列的概率 $p^k (1-p)^{n-k}$（独立性下沿路径连乘，Lec 03 的树模型）× 含 $k$ 个正面的序列条数 $\binom{n}{k}$（Lec 04 的组合计数）。验证 $n = 4$：$p_X(2) = \binom{4}{2} p^2 (1-p)^2 = 6 p^2 (1-p)^2$ ✓——幻灯片把 HHTT、HTHT、HTTH、THHT、THTH、TTHH 六条序列一一列出，正是在"手动执行" $\binom{4}{2} = 6$。跨课程连接：CLRS 第 5 章的 indicator random variable（指示随机变量）在分析雇佣问题时用的就是这套"独立试验计成功数"的二项模型；而 6.042J 的二项式定理 $(p + (1-p))^n = \sum_k \binom{n}{k} p^k (1-p)^{n-k} = 1$ 还顺带解释了为什么这个 PMF 自动归一化——左边恒为 $1$。均值 $\mathrm{E}[X] = np$ 与方差 $\mathrm{var}(X) = np(1-p)$ 留待 Lec 07 用指示变量分解优雅推出，本讲只需会写出 PMF 本身。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Expectation（期望）</span>

- **定义**：
```math
\mathrm{E}[X] = \sum_x x \, p_X(x) .
```
- **两种解释**：
  - PMF 的 center of gravity（重心）。
  - 大量重复实验中的 average（平均）取值（本课程稍后予以论证）。
- **例**：$\{0, 1, \ldots, n\}$ 上的均匀分布。
```math
\mathrm{E}[X] = 0 \times \frac{1}{n+1} + 1 \times \frac{1}{n+1} + \cdots + n \times \frac{1}{n+1} = \frac{n}{2} .
```

> <span style="color:#7f8c8d;">图：平顶分布列——$p_X(x)$ 在 $x = 0, 1, \ldots, n$ 处恒为 $\frac{1}{n+1}$，其余处为零。</span>

> <span style="color:#7f8c8d;">Bertsekas §2.4（本讲 Readings：起步 §2.4）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 期望的两条解释对应两种第一性原理视角。其一是**重心**：把单位质量按 $p_X(x)$ 铺在数轴上，$\mathrm{E}[X] = \sum_x x\, p_X(x)$ 恰是"权重 × 位置再求和"的力矩平衡式，重心即均值。其二是**长程平均**：大量独立重复实验的样本平均会稳定在 $\mathrm{E}[X]$ 附近——这一解释要到 Lec 19 的大数定律才正式兑现，幻灯片括号里的 "(to be substantiated later in this course)" 打的就是这张期票。验证均匀分布例：$p_X(x) = \frac{1}{n+1}$（$x = 0, 1, \ldots, n$），$\mathrm{E}[X] = \frac{0 + 1 + \cdots + n}{n+1} = \frac{n(n+1)/2}{n+1} = \frac{n}{2}$ ✓。也可以不动笔：分布关于 $n/2$ 对称，重心必落在对称中心——对称性求期望是零成本技巧，Lec 04 发牌例与教材 p.89 例 2.6（六面骰均值 $3.5$）用的都是它。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Properties of expectations（期望的性质）</span>

- 设 $X$ 为随机变量，$Y = g(X)$。
  - Hard（硬路）：$\mathrm{E}[Y] = \sum_y y \, p_Y(y)$——先求出 $Y$ 自己的分布列。
  - Easy（易路）：$\mathrm{E}[Y] = \sum_x g(x) \, p_X(x)$——直接在 $X$ 的分布列上加权。
- **警示**：一般地，$\mathrm{E}[g(X)] \ne g(\mathrm{E}[X])$。
- **性质**：若 $\alpha, \beta$ 为常数，则：
  - $\mathrm{E}[\alpha] = \underline{\qquad}$
  - $\mathrm{E}[\alpha X] = \underline{\qquad}$
  - $\mathrm{E}[\alpha X + \beta] = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.87（期望值规则的警示与线性函数规则）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 三个空栏逐一验算：$\mathrm{E}[\alpha] = \sum_x \alpha\, p_X(x) = \alpha \sum_x p_X(x) = \alpha$ ✓；$\mathrm{E}[\alpha X] = \sum_x \alpha x\, p_X(x) = \alpha\, \mathrm{E}[X]$ ✓；合并得 $\mathrm{E}[\alpha X + \beta] = \alpha\, \mathrm{E}[X] + \beta$ ✓——末步用的正是归一性 $\sum_x p_X(x) = 1$，三条性质其实是同一行代数的三次亮相。"Hard vs. Easy" 的对比是真知：硬路要先逐点收集原像求出 $p_Y$，易路（expected value rule，期望值规则）直接在 $p_X$ 上加权，跳过整道工序。卡点诊断：$\mathrm{E}[g(X)] \ne g(\mathrm{E}[X])$ 的警告在教材 p.87 随即落地——除非 $g$ 是线性函数，否则"先平均再作用"与"先作用再平均"一般不等；经典陷阱是平均速度与平均时间（教材 Example 2.4, p.88），Lec 06 将完整展开。眼下只需刻死一条：期望只与线性函数可交换。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Variance（方差）</span>

- 回顾期望值规则：$\mathrm{E}[g(X)] = \sum_x g(x) \, p_X(x)$。
- **二阶矩**（second moment）：$\mathrm{E}[X^2] = \sum_x x^2 \, p_X(x)$。
- **方差**：
```math
\mathrm{var}(X) = \mathrm{E}\left[(X - \mathrm{E}[X])^2\right] = \sum_x (x - \mathrm{E}[X])^2 \, p_X(x) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2 .
```
- **性质**：
  - $\mathrm{var}(X) \ge 0$。
  - $\mathrm{var}(\alpha X + \beta) = \alpha^2 \, \mathrm{var}(X)$。

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.87（矩公式与线性函数的方差规则）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 第一性原理）:**</span> 方差的两条等价定义各有一用。$\mathrm{var}(X) = \mathrm{E}[(X - \mathrm{E}[X])^2]$ 是**第一性原理式**：先把随机变量平移到均值（居中），再取平方平均，度量"相对重心的摆动幅度"。$\mathrm{var}(X) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2$ 是**计算式**——命名模板：**矩公式降维**，展开平方项 $\mathrm{E}[X^2 - 2X\,\mathrm{E}[X] + (\mathrm{E}[X])^2] = \mathrm{E}[X^2] - 2(\mathrm{E}[X])^2 + (\mathrm{E}[X])^2$，期望的线性（对任意分布成立）一路放行。性质 $\mathrm{var}(\alpha X + \beta) = \alpha^2\, \mathrm{var}(X)$ 中 $\beta$ 彻底消失：平移不改变摆动，缩放按平方进账——这也解释了为什么还需要 standard deviation（标准差）$\sigma_X = \sqrt{\mathrm{var}(X)}$：它把量纲还原成与 $X$ 相同的单位，Lec 06 的复习页会把它请回前台。$\mathrm{var}(X) \ge 0$ 由"平方的期望非负"直接读出 ✓。教材 p.87 把这套公式对线性函数 $Y = aX + b$ 一并给出：$\mathrm{E}[Y] = a\,\mathrm{E}[X] + b$，$\mathrm{var}(Y) = a^2\, \mathrm{var}(X)$，与本页两条性质完全一致 ✓。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
