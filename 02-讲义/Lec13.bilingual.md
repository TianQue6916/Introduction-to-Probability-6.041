# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 13 — The Bernoulli process（伯努利过程）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline（本讲大纲）</span>

**阅读（Readings）**：教材 Section 6.1。

**本讲大纲（Lecture outline）**：
- 伯努利过程的定义（definition of Bernoulli process）。
- 随机过程（random processes）。
- 伯努利过程的基本性质（basic properties）。
- 到达间隔的分布（distribution of interarrival times）。
- 第 $k$ 次成功的时刻（the time of the $k$th success）。
- 合并与分裂（merging and splitting）。

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.297–306</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 从本讲起，概率的对象从"一个随机变量"升级为"一串随机变量随时间展开"——random process（随机过程）。族谱预告三条路线：Bernoulli process（伯努利过程，无记忆、离散时间，本讲）、Poisson process（泊松过程，无记忆、连续时间，教材下一节/下一讲）、Markov chains（马尔可夫链，跨时间有记忆/相依）。经核对页码，教材第 6 章 The Bernoulli and Poisson Processes 自 p.295 起，§6.1 The Bernoulli Process 从 p.297 开始，本讲内容依次落在 p.297–306。战略上，伯努利过程就是把 Lec 02–07 的独立伯努利试验沿时间轴无限铺开：单时隙看是伯努利变量，$n$ 个时隙看是二项分布，等待首次成功看是几何分布——没有新数学，只有新视角。本讲真正新且难的两点是"样本空间怎么取"与"无记忆性怎么用"，其余都是老朋友的重新列队。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The Bernoulli process（伯努利过程的定义）</span>

- 一列 independent Bernoulli trials（独立伯努利试验）。
- 在每个 trial $i$：
  - $P(\text{success}) = P(X_i = 1) = p$；
  - $P(\text{failure}) = P(X_i = 0) = 1 - p$。
- **例**：
  - 彩票中/不中的序列；
  - 道琼斯指数（Dow Jones）的涨/跌序列；
  - 每秒到达银行的顾客；
  - 每个时隙（time slot）到达服务器的请求。

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.297–298</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Random processes（随机过程）</span>

- **第一种视角**：随机变量序列 $X_1, X_2, \ldots$
- **课堂填空**：
  - $\mathrm{E}[X_t] = \underline{\qquad}$
  - $\mathrm{Var}(X_t) = \underline{\qquad}$
- **第二种视角**：正确的样本空间（sample space）究竟是什么？
- **课堂填空**：$P(X_t = 1 \text{ for all } t) = \underline{\qquad}$
- 我们将研究的随机过程：
  - 伯努利过程（无记忆、离散时间）；
  - 泊松过程（无记忆、连续时间）；
  - 马尔可夫链（跨时间有记忆/相依）。

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.297–298</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 第一性原理）:**</span> 空栏验算：单时隙就是伯努利变量，$\mathrm{E}[X_t] = p$、$\mathrm{Var}(X_t) = p(1 - p)$ ✓（Lec 02/Lec 07 的老结论）。$P(X_t = 1 \text{ for all } t)$：对前 $n$ 个时隙用独立性连乘得 $p^n$，再取极限 $\lim_{n \to \infty} p^n = 0$（对 $p < 1$）✓——最后一步用的是 100B 实分析/微积分的极限语言。第一性原理的看点在样本空间：过程应取"完整的 0/1 无穷序列"为样本点，于是单个序列的概率为 0（$p^n \to 0$），但概率仍可赋给序列的集合（事件）——先对有限段谈概率、再取极限即可，不必先学测度论。卡点诊断："$P(\text{无限长全成功}) = 0$"与"$P(\text{任意有限段全成功}) = p^n > 0$"并不矛盾——有限与无限的鸿沟；也不要把它误读成"有限时间内不可能全成功"。教材 p.297–298 的正式定义与此一致：过程 = 概率规律 $+$ 时间索引。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Number of successes S in n time slots（n 个时隙中的成功次数）</span>

- **课堂填空**：
  - $P(S = k) = \underline{\qquad}$
  - $\mathrm{E}[S] = \underline{\qquad}$
  - $\mathrm{Var}(S) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.298</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 空栏验算：$n$ 个时隙内的成功次数 $S$ 恰是二项随机变量——$P(S = k) = \binom{n}{k} p^k (1 - p)^{n - k}$ ✓，$\mathrm{E}[S] = np$ ✓，$\mathrm{Var}(S) = np(1 - p)$ ✓。后两条由 Lec 07 的指示变量分解 $S = X_1 + \cdots + X_n$ 原样搬上时间轴：各指示变量 i.i.d.，期望的线性与方差和规则全部适用。所以伯努利过程并未引入新分布，而是把二项分布装进时间框架：任意固定长 $n$ 的窗口看一眼，都是老朋友 $\mathrm{Binomial}(n, p)$。这个视角马上要在下一节数"等待时间"时发力，也将在本讲末尾取极限得到泊松分布时再度登场。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Interarrival times（到达间隔）</span>

- $T_1$：直到第一次成功的 trial 数。
- **课堂填空**：$P(T_1 = t) = \underline{\qquad}$
- **Memoryless property（无记忆性）**。
- **课堂填空**：
  - $\mathrm{E}[T_1] = \underline{\qquad}$
  - $\mathrm{Var}(T_1) = \underline{\qquad}$
- **课堂提问**：若你每天买一张彩票，第一串连续"不中"的天数长度服从什么分布？

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.299–301</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 空栏验算：$P(T_1 = t) = (1 - p)^{t - 1} p$（前 $t - 1$ 次全败、第 $t$ 次成功，独立性连乘）✓——geometric（几何）分布。$\mathrm{E}[T_1] = 1/p$：可用尾和公式 $\sum_{t \ge 1} P(T_1 \ge t) = \sum_{t \ge 1} (1 - p)^{t - 1} = 1/p$ ✓；也可用条件化两分支：第一次就成功（概率 $p$，历时 1）或先败一次再从头来（概率 $1 - p$，历时 $1 + \mathrm{E}[T_1]$），解方程 $\mathrm{E}[T_1] = p + (1 - p)(1 + \mathrm{E}[T_1])$ 得 $1/p$ ✓——第二种证法就是无记忆性的预演。$\mathrm{Var}(T_1) = (1 - p)/p^2$ ✓（教材 p.300–301 的标准计算）。彩票问题的答案：直到首次中奖的等待天数 $T_1$ 服从几何分布，故首段连败天数（$= T_1 - 1$）也由几何直接给出——无论已经连败多少天，"明天开始再等多少天"的分布不变，每天都是 fresh start（重新开张），赌徒谬误在此被无记忆性正面击破。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Time of the kth arrival（第 k 次到达的时刻）</span>

- 已知第一次到达发生在时刻 $t$（即 $T_1 = t$）：到下一次到达的附加时间 $T_2$：
  - 服从同样的（几何）分布；
  - 与 $T_1$ 独立。
- $Y_k$：到第 $k$ 次成功为止的 trial 数。
- **课堂填空**：
  - $\mathrm{E}[Y_k] = \underline{\qquad}$
  - $\mathrm{Var}(Y_k) = \underline{\qquad}$
  - $P(Y_k = t) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.303–304</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 命名模板——和的分解：$Y_k = T_1 + \cdots + T_k$。教材的 fresh-start 论证（p.300–301，含"在随机时刻重新开始"的正式例子）：每次成功一落地，后续过程与过去独立、分布如初，故 $T_1, \ldots, T_k$ 为 i.i.d. 几何变量；顺带解释了本页开头的论断——$T_2$ 与 $T_1$ 独立同分布。于是 $\mathrm{E}[Y_k] = k/p$ ✓（期望的线性）；$\mathrm{Var}(Y_k) = k(1 - p)/p^2$ ✓（Lec 07 方差和规则，"独立"在手故合法）。$P(Y_k = t) = \binom{t - 1}{k - 1} p^k (1 - p)^{t - k}$——Pascal（帕斯卡）分布，亦称 negative binomial（负二项）分布：第 $t$ 次必须成功（因子 $p$），前 $t - 1$ 次中恰有 $k - 1$ 次成功、位置任选（$\binom{t - 1}{k - 1}$，Lec 04 的组合计数）✓。对账：$k = 1$ 退化为几何 ✓；固定 $t$ 对 $k$ 求和可用二项定理核对归一化。另一个值得记住的现象：均值与方差都随 $k$ 线性增长，相对波动 $\sqrt{\mathrm{Var}}/\mathrm{E} \sim 1/\sqrt{k}$ 反而缩小——大数定律的影子。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Splitting and merging（分裂与合并）</span>

- **Splitting（分裂）**：参数为 $p$ 的伯努利过程，每次到达以概率 $q$ 保留（keep）、以概率 $1 - q$ 丢弃（discard）——用独立掷硬币决定，各次决策相互独立：
  - 保留流：每时隙出现保留到达的概率为 $pq$——仍是伯努利过程；
  - 丢弃流：每时隙概率 $p(1 - q)$——也是伯努利过程。
- **Merging（合并）**：两条独立的伯努利过程（参数分别为 $p$ 与 $q$），只要至少一条在某时隙有到达就记一次到达（collisions（碰撞）算一次到达）：
  - 某时隙有到达的概率 $= p + q - pq = 1 - (1 - p)(1 - q)$；
  - 合并过程是参数 $p + q - pq$ 的伯努利过程。

> <span style="color:#7f8c8d;">图：教材 Fig. 6.3/6.4——原过程经 $q$（保留）与 $1 - q$（丢弃）两条分支分裂为两个伯努利过程；两条独立过程 Bernoulli($p$)、Bernoulli($q$) 汇入合并过程 Bernoulli($p + q - pq$)。</span>

- **应用**：两机器工件的随机分派（一股到达流分裂给两台机器）；反之，不同类型的到达合并成一股。

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.305–306</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 跨课程连接）:**</span> 分裂侧的机理：某时隙出现"保留的到达" $=$ 试验成功（概率 $p$）$\wedge$ 独立掷币保留（概率 $q$），两事件独立，交概率 $pq$；各时隙用的硬币互相独立，跨时隙独立性原封不动——所以保留流是参数 $pq$ 的伯努利过程 ✓，丢弃流同理参数 $p(1 - q)$ ✓。合并侧：某时隙有到达 $=$ 两过程至少一个有到达，概率 $p + q - pq = 1 - (1 - p)(1 - q)$ ✓——inclusion–exclusion（容斥原理）的一行应用，6.042J 集合计数与 Lec 02 的老朋友；跨时隙独立同样保住。卡点诊断两条：其一，合并时同一时隙两线都到（"碰撞"）只记一次——合并是逐时隙的逻辑 OR，不是到达数的相加；其二，别把"分裂出的两条流各自是伯努利过程"与"两条流之间相互独立"混为一谈，后者是额外事实。应用直觉：随机分流如把工件随机派给两台机器，汇聚如把多源请求并成一队——排队网络的两大基本操作。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The Poisson approximation to the binomial（二项分布的泊松近似）</span>

- $n$ 次独立伯努利试验的成功次数服从参数 $n, p$ 的二项分布，均值为 $np$。关注 $n$ 大、$p$ 小、$np$ 适中的情形（如：一天的事故数——大量航班、每班极小的事故概率；一本书的 typos（错拼词）数——大量单词、每个词极小的错拼概率）：令 $n$ 增大、$p$ 减小、乘积 $np$ 保持常数 $\lambda$，二项 PMF 的公式在极限下化简为 Poisson PMF（泊松分布列）。
- 参数 $\lambda$ 的泊松随机变量 $Z$ 取非负整数值：
```math
p_Z(k) = e^{-\lambda}\, \frac{\lambda^k}{k!}, \qquad k = 0, 1, 2, \ldots
```
- 均值与方差：
```math
\mathrm{E}[Z] = \lambda, \qquad \mathrm{var}(Z) = \lambda .
```

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.306</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 极限的第一性验算：固定 $\lambda = np$，看 $k = 0$ 项：$(1 - p)^n = \left(1 - \frac{\lambda}{n}\right)^n \to e^{-\lambda}$——正是 $e$ 的极限定义（100B 实分析/微积分的级数语言）。一般 $k$ 项：$n$ 大 $k$ 固定时 $\binom{n}{k} \approx \frac{n^k}{k!}$，乘 $p^k = (\lambda/n)^k$ 得 $\lambda^k / k!$，末尾 $(1 - p)^{n - k} \to e^{-\lambda}$，合计 $e^{-\lambda} \lambda^k / k!$ ✓。均值与方差在极限下"合流"：$\mathrm{E}[S] = np = \lambda$ 不变，$\mathrm{var}(S) = np(1 - p) = \lambda(1 - p) \to \lambda$ ✓——"均值 $=$ 方差"是泊松族的身份证，也是它与二项分布的分辨特征。教材举的直觉场景：一天的事故数 $=$ 海量航班 $\times$ 极小单班事故率；一本书的错拼词 $=$ 海量单词 $\times$ 极小单词出错率。跨课程连接：CLRS 分析"大量独立小概率事件计数"时反复用到同一近似；而把"时隙不断加密"推到极致——从离散时间过渡到连续时间——就是教材下一节与下一讲的泊松过程，$\lambda$ 摇身变为单位时间的到达率。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
