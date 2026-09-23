# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 25 — Classical Statistical Inference III（经典统计推断 III）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; review（本讲大纲与复习）</span>

**参考（Reference）**：教材 Section 9.4（显著性检验）。课程评估（Course Evaluations）截至 12/16：http://web.mit.edu/subjectevaluation 。

**本讲大纲（Outline）**：
- 简单二元假设检验的复习（Review of simple binary hypothesis tests）——举例（examples）。
- 检验复合假设（Testing composite hypotheses）：
  - 我的硬币公平吗（is my coin fair?）；
  - 我的骰子公平吗（is my die fair?）；
  - 拟合优度检验（goodness of fit tests）。

> <span style="color:#7f8c8d;">Bertsekas §9.3, p.485–494；§9.4, p.495–505</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 全课的收官一讲，任务是把 Lec 24 的检验机器推到真实场景。Lec 24 的 LRT 要求两个假设都"简单"——各自把分布完全指定（如 $X_i \sim \mathrm{N}(0,1)$ 对 $\mathrm{N}(1,1)$）；现实中的假设常是复合的："$p \ne 1/2$"里塞着无穷多个子假设（$p = 0.1$、$p = 0.4999$……），没有单一似然比可算。教材第 9 章开篇（p.459 附近）把困境说得很透：中等数量的观测根本无法可靠区分 $p = 0.5$ 与 $p = 0.4999$，于是问题改问成 significance testing（显著性检验）的句式——"观测数据与 $H_0$ 相容吗？"——只在数据于 $H_0$ 下"碰巧出现得太过罕见"时才拒绝。本讲四台例子机（正态均值、正态方差、硬币、骰子）跑的都是同一条流水线：选统计量、选拒绝域形状、定显著性水平、查分布定阈值。讲完这页，整门 25 讲的课程也随之画上句号，最后一页幻灯片就是全课的"退出动画"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Simple binary hypothesis testing（简单二元假设检验）</span>

- 原假设 $H_0$：$X \sim p_X(x;\, H_0)$（或 $f_X(x;\, H_0)$）；备择假设 $H_1$：$X \sim p_X(x;\, H_1)$（或 $f_X(x;\, H_1)$）。
- 选定拒绝域 $R$；当且仅当数据 $\in R$ 时拒绝 $H_0$。
- Likelihood ratio test（似然比检验）：当
```math
\frac{p_X(x;\, H_1)}{p_X(x;\, H_0)} > \xi
\qquad \text{或} \qquad
\frac{f_X(x;\, H_1)}{f_X(x;\, H_0)} > \xi
```
  时拒绝 $H_0$：
  - 固定错误拒绝概率 $\alpha$（如 $\alpha = 0.05$）；
  - 选 $\xi$ 使得 $P(\text{reject } H_0 \,;\ H_0) = \alpha$。

> <span style="color:#7f8c8d;">Bertsekas §9.3, p.485–494</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example (test on normal mean)（例：正态均值的检验）</span>

- $n$ 个 i.i.d. 数据点：$H_0$：$X_i \sim \mathrm{N}(0, 1)$；$H_1$：$X_i \sim \mathrm{N}(1, 1)$。
- 似然比检验；拒绝域：
```math
\frac{(1/\sqrt{2\pi})^n \exp\{-\sum_i (X_i - 1)^2/2\}}{(1/\sqrt{2\pi})^n \exp\{-\sum_i X_i^2/2\}} > \xi ,
```
  - 代数化简：当 $\sum_i X_i > \xi'$ 时拒绝 $H_0$。
- 求 $\xi'$ 使得
```math
P\Bigl(\sum_{i=1}^{n} X_i > \xi' \,;\ H_0\Bigr) = \alpha :
```
  - 使用 normal tables（正态分布表）。

> <span style="color:#7f8c8d;">Bertsekas §9.4, p.495–505</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 化简验算：分子分母的归一化因子 $(1/\sqrt{2\pi})^n$ 相同而抵消，比值 $= \exp\{-\tfrac{1}{2}\sum_i (X_i - 1)^2 + \tfrac{1}{2}\sum_i X_i^2\} = \exp\{\sum_i X_i - n/2\}$ ✓（展开 $(X_i-1)^2 = X_i^2 - 2X_i + 1$ 后逐项相消）。它是 $\sum_i X_i$ 的严格递增函数，故"比值 $> \xi$"等价于"$\sum_i X_i > \xi'$"（$\xi' = \log\xi + n/2$）✓。定阈值：$H_0$ 下各 $X_i \sim \mathrm{N}(0,1)$ 独立，由 Lec 07 的均值方差叠加规则 $\sum_i X_i \sim \mathrm{N}(0, n)$，标准化后 $\sum_i X_i / \sqrt n \approx \mathrm{N}(0,1)$；取 $\xi' = \sqrt n\, z$（如 $\alpha = 0.05$ 时 $\Phi(z) = 0.95$，$z = 1.645$）即有 $P(\text{reject}\,;\,H_0) = \alpha$ ✓。方向感体检：$H_1$ 把均值从 $0$ 挪到 $1$（右侧），拒绝域也在右侧——检验火力对准备择假设偏离的方向；若 $H_1$ 是 $\mathrm{N}(-1, 1)$，拒绝域就该翻到左边。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example (test on normal variance)（例：正态方差的检验）</span>

- $n$ 个 i.i.d. 数据点：$H_0$：$X_i \sim \mathrm{N}(0, 1)$；$H_1$：$X_i \sim \mathrm{N}(0, 4)$。
- 似然比检验；拒绝域：
```math
\frac{(1/(2\sqrt{2\pi}))^n \exp\{-\sum_i X_i^2/(2 \cdot 4)\}}{(1/\sqrt{2\pi})^n \exp\{-\sum_i X_i^2/2\}} > \xi ,
```
  - 代数化简：当 $\sum_i X_i^2 > \xi'$ 时拒绝 $H_0$。
- 求 $\xi'$ 使得
```math
P\Bigl(\sum_{i=1}^{n} X_i^2 > \xi' \,;\ H_0\Bigr) = \alpha :
```
  - $\sum_i X_i^2$ 的分布是已知的（derived distribution 派生分布问题）；
  - "chi-square" distribution（卡方分布）；有表可查。

> <span style="color:#7f8c8d;">Bertsekas §9.4, p.495–505</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 化简验算：比值 $= \bigl(\tfrac{1}{2}\bigr)^n \exp\{\sum_i X_i^2 \bigl(\tfrac{1}{2} - \tfrac{1}{8}\bigr)\} = 2^{-n} \exp\{\tfrac{3}{8}\sum_i X_i^2\}$ ✓，仍是 $\sum_i X_i^2$ 的递增函数，拒绝域"$\sum_i X_i^2 > \xi'$" ✓（常数 $2^{-n}$ 被并入 $\xi'$）。分布从哪来：$H_0$ 下每个 $X_i^2$ 是标准正态的平方，对平方做换元（$y = x^2$，正负两支各摊一半质量）得 $f_{X^2}(y) \propto y^{-1/2} e^{-y/2}$，$n$ 个独立同分布之和卷积出自由度 $n$ 的 chi-square distribution（卡方分布）——这正是幻灯片所说的 derived distribution problem（派生分布问题），换元与卷积都是前面讲次练过的基本功。方向感 again：$H_1$ 方差更大（$4 > 1$），数据偏离原点更远，平方和偏大，拒绝域在右侧 ✓。命名模板——本讲全部例子的流水线：**"选统计量（似然比的单调函数）→ 化简 → 求其在 $H_0$ 下的分布 → 按尾概率 $= \alpha$ 定阈值"**；下一页起 $H_1$ 变成复合假设，这条流水线的前两步改由人来设计。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Composite hypotheses（复合假设）</span>

- $n = 1000$ 次投掷得到 $S = 472$ 次正面；硬币公平吗？
  - $H_0: p = 1/2$ 对 $H_1: p \ne 1/2$。
- 选一个 statistic（统计量）（如 $S$）。
- 选拒绝域的形状（如 $|S - n/2| > \xi$）。
- 选显著性水平（significance level）（如 $\alpha = 0.05$）。
- 选临界值 $\xi$ 使得 $P(\text{reject } H_0 \,;\ H_0) = \alpha$。用 CLT：
```math
P(|S - 500| \le 31 \,;\ H_0) \approx 0.95, \qquad \xi = 31 .
```
- 本例中：$|S - 500| = 28 < \xi$——$H_0$ 不被拒绝（在 5% 水平上）。

> <span style="color:#7f8c8d;">Bertsekas §9.4, p.495–505</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验算 $\xi = 31$：$H_0$ 下 $S \sim \mathrm{Bin}(1000, 1/2)$（Lec 04 的二项概率），均值 $500$、标准差 $\sqrt{1000 \cdot \tfrac12 \cdot \tfrac12} = \sqrt{250} \approx 15.81$；CLT 给 $P(|S - 500| \le 31) \approx P(|Z| \le 31/15.81) = P(|Z| \le 1.96) \approx 0.95$ ✓，故 $\xi = 31$ 恰是 5% 水平的临界值。本例数据：$|S - 500| = 28$，折合 $28/15.81 \approx 1.77$ 个标准差，双侧尾概率 $\approx 0.077 > 0.05$——不拒绝 ✓。卡点诊断：**"不拒绝 $H_0$"绝不等于"接受 $H_0$"或"证明硬币公平"**——它只说 472 次正面与公平硬币不矛盾（事实上 $p = 0.472$ 的硬币同样落在不拒绝区）。司法类比：拒绝域是"定罪的证据门槛"，$\alpha$ 是"冤案率上限"，证据不足只能疑罪从无，不是无罪证明。复合 $H_1: p \ne 1/2$ 无法算单一似然比，流程里的三处自由度——统计量选 $S$、形状选 $|S - n/2|$、水平选 $\alpha$——全由人设计；这正是显著性检验的"设计"面，也是它比 LRT 灵活又比 LRT 主观的地方。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Is my die fair?（我的骰子公平吗？）</span>

- 假设 $H_0$：$P(X = i) = p_i = 1/6$，$i = 1, \ldots, 6$。
- 观测到各面出现的次数 $N_i$。
- 选定拒绝域的形式；chi-square test（卡方检验）：
```math
\text{当}\quad T = \sum_{i} \frac{(N_i - n p_i)^2}{n p_i} > \xi \quad \text{时拒绝 } H_0 .
```
- 选 $\xi$ 使得：
```math
P(\text{reject } H_0 \,;\ H_0) = 0.05, \qquad P(T > \xi \,;\ H_0) = 0.05 .
```
- 需要 $T$ 的分布（CLT + 派生分布问题）：
  - $n$ 大时，$T$ 近似服从卡方分布；
  - 有表可查。

> <span style="color:#7f8c8d;">Bertsekas §9.4, p.495–505</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 统计量 $T$ 的读法：$N_i - np_i$ 是"观测频数减期望频数"，逐项平方、除以期望频数 $np_i$ 完成标准化，再求和——$T$ 大意味着某些面出现得离谱地多或少，任何一面的异常都会点亮它。跨课程连接（自由度脚手架）：$n$ 大时 $T$ 近似服从自由度为 $k - 1$ 的卡方分布（$k$ 为类别数，骰子是 $5$）——为什么减一：$k$ 个频数 $N_i$ 受硬约束 $\sum_i N_i = n$，能独立自由变动的只有 $k - 1$ 个；这与 Lec 23 里 $\hat S_n^2$ 分母取 $n - 1$ 的"约束吃掉一个自由度"完全同款，在 Strang 线代里则是"一个独立约束把维数降一"。两个零件都是课程老朋友：各频数是大量独立计数之和，CLT 让正态近似登场；对正态量做二次型派生，卡方现身——"CLT + 派生分布"正是幻灯片点名的两件工具。设计上的取舍也值得记：卡方检验把所有偏离揉进一个数，简单通用，但"哪一面出了问题"要回头看逐项残差 $(N_i - np_i)$。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Do I have the correct pdf?（我的 PDF 选对了吗？）</span>

- 把取值范围切成 bins（箱）：
  - $n p_i$：第 $i$ 箱的 expected incidence（期望出现数，由待检的 PDF 算出）；
  - $N_i$：observed incidence（观测出现数）；
  - 使用卡方检验（同骰子问题）。
- Kolmogorov-Smirnov 检验：由数据构造 empirical CDF（经验分布函数）$\hat F_X$：
  - $D_n = \max_x\, |F_X(x) - \hat F_X(x)|$；
  - $P(\sqrt{n}\, D_n \ge 1.36) \approx 0.05$；
  - （参考手册：http://www.itl.nist.gov/div898/handbook/ ）

> <span style="color:#7f8c8d;">Bertsekas §9.4, p.495–505</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 两种拟合优度检验的分野值得一辨。卡方检验先把连续分布"装箱"离散化、再比较频数——箱怎么切、切多粗都会左右结果；K-S 检验直接比较 CDF 的全程最大竖直距离 $D_n = \max_x |F_X(x) - \hat F_X(x)|$，不用选箱、不丢信息。100B 实分析的语言在这里正好接上：$\hat F_X(x)$（落在 $\le x$ 的样本比例）逐点收敛到 $F_X(x)$，而 Glivenko–Cantelli 的思想（脚手架式一句：把逐点收敛加强到"最坏点上也收敛"，即 $\sup_x$ 误差趋于零）保证 $\max_x$ 这个量本身是有意义的统计量；$\sqrt n$ 因子来自 $\hat F_X$ 在每个固定 $x$ 处是 Bernoulli 指示变量之和（Lec 07 的指示变量技术）、方差 $\propto F(1-F)/n$ 的 $\sqrt n$ 缩放，极限分布与 $n$ 无关，$1.36$ 即其 5% 分位点 ✓。方法论收获：连续与离散从来不是两个世界——装箱与派生分布是往返两岸的渡船，本课程从第 2 章起反复演示这条统一化路线。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">What else is there?（还有些什么？）</span>

- 系统地给出拒绝域形状的方法。
- 估计未知 PDF 的方法（如先做 histogram（直方图）再"smooth"（平滑））。
- 高效且递归的信号处理（efficient and recursive signal processing）。
- 在较简单与较复杂模型之间做选择的方法（如在回归模型中识别相关的"explanatory variables"（解释变量））。
- 面向高维未知参数向量与海量数据点的方法（data mining，数据挖掘）。
- 等等等等……

> <span style="color:#7f8c8d;">Bertsekas §9.4, p.495–505；§9.5, p.506</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 课程最后一页，既是统计推断的"接下来还有什么"，也是整门 25 讲的谢幕辞。回望课程弧线：概率模型与条件化（Lec 01–02）→ 离散随机变量与计数（Lec 03–07）→ 连续随机变量与派生分布 → 随机过程（Bernoulli 与 Poisson 过程、Markov 链）→ 极限定理（WLLN、CLT）→ 统计推断（第 8–9 章）。两大流派就此对照收束：贝叶斯——$\theta$ 是随机变量，先验是全部主观假设的明码入口，后验喂出 MAP、LMS、线性 LMS；经典——$\theta$ 是常数，按 worst-case 评价一切，工具是 MLE、置信区间、LRT 与显著性检验；两派在 MAP 与 ML、贝叶斯检测与 LRT 处反复握手（教材第 8 章开篇 pp.410–411 与第 9 章开篇 p.459 附近各有正论）。幻灯片那串"等等等等"不是敷衍：直方图平滑通向核密度估计，模型选择通向现代统计学习，数据挖掘通向高维大数据——每一项都能在后续课程里找到独栋厂房；Lec 22 见过的"递归信号处理"（精度加权更新的递归化）也在此重逢。把这一页当作全课目录的最后一行来读：每个名词背后，都有一讲练出的肌肉记忆。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
