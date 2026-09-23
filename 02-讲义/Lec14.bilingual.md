# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 14 — The Poisson process（泊松过程）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; Bernoulli review（本讲大纲与伯努利过程复习）</span>

**阅读**：开始阅读教材 Section 6.2（The Poisson Process，泊松过程）；右栏复习对应 Section 6.1（伯努利过程）。

**本讲大纲（Lecture outline）**：
- 伯努利过程复习（Review of Bernoulli process）。
- 无记忆性（Memorylessness）。
- 泊松过程的定义（Definition of Poisson process）。
- 到达次数的分布（Distribution of number of arrivals）。
- 到达间隔时间的分布（Distribution of interarrival times）。
- 泊松过程的其他性质（Other properties of the Poisson process）。

**伯努利过程复习（Bernoulli review）**：
- 离散时间（discrete time）；每次试验成功概率 $p$。
- $n$ 个时间槽（time slots）内的到达次数：binomial pmf（二项分布列）。
- 到达间隔时间（interarrival times）：geometric pmf（几何分布列）。
- 直到第 $k$ 次到达的时间：Pascal pmf（帕斯卡分布列）。

> <span style="color:#7f8c8d;">Bertsekas §6.1, p.297–301；p.303–304；§6.2, p.309</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲开启教材第 6 章"到达过程"的下半场：把上一讲的 Bernoulli process（伯努利过程）从离散时间平移到连续时间，得到 Poisson process（泊松过程）。讲义把大纲与伯努利复习并置在一页，是在提示全讲的展开方式——泊松过程的每一条性质都能在伯努利过程里找到"离散原型"：教材 §6.1（p.297 起）把伯努利过程定义为独立伯努利试验序列，p.298 给出 $n$ 槽内到达次数的二项分布列，p.299–300 给出到达间隔的几何分布列，p.303–304 给出第 $k$ 次到达时间的 Pascal 分布列；而 §6.2 从 p.309 起，把"每槽成功概率 $p$"换成"每单位时间到达率 $\lambda$"。大纲里单列的 Memorylessness（无记忆性）是贯穿两者的发动机：伯努利过程"看过即忘"、未来与过去独立，泊松过程将继承同一条性质。读法建议：先复习 §6.1 的四件套（二项/几何/Pascal/无记忆性），再进 §6.2，全程带着"离散原型是谁"这个问题对照听讲，本讲的公式就不再是新东西，而是同一条思想在不同时间轴上的两次显影。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Definition of the Poisson process（泊松过程的定义）</span>

- **时间齐次性（time-homogeneity）**：$P(k, \tau)$ = 时长为 $\tau$ 的区间内恰有 $k$ 次 arrival（到达）的概率。
- **假设（assumptions）**：
  - 不相交（disjoint）时间区间内的到达次数相互 independent（独立）。
  - 对 VERY small（极小）的 $\delta$：
```math
P(k, \delta) \approx \begin{cases} 1 - \lambda\delta, & \text{if } k = 0, \\ \lambda\delta, & \text{if } k = 1, \\ 0, & \text{if } k > 1; \end{cases}
```
  - $\lambda$：arrival rate（到达率）。

> <span style="color:#7f8c8d;">图：时间轴上的到达流——在时刻 $0, t_1, t_2, t_3, \ldots$ 处以 "×" 标记一次次到达；每次到达把时间轴切成一段段 interarrival time（到达间隔）。</span>

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.309–310</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 为什么泊松过程用"三条假设"来定义？教材 p.310 的正式定义把小区间概率写成 $P(0,\tau) = 1 - \lambda\tau + O(\tau)$、$P(1,\tau) = \lambda\tau + O_1(\tau)$、$P(k,\tau) = O_k(\tau)$（$k \ge 2$），其中误差项满足 $\lim_{\tau \to 0} O(\tau)/\tau = 0$——这正是 100B 实分析里 little-o 记号 $\tau = o(\tau)$ 式的语言，幻灯片用 "$\approx$" 就是它的口语版。第一性原理的验证：把长度为 $\tau$ 的区间切成 $\tau/\delta$ 个宽 $\delta$ 的小格，若每格以概率 $\lambda\delta$ "有一次到达"，则一格两次到达的概率是 $\lambda\delta$ 的二阶量，可以忽略——所以 $P(2,\delta) \approx 0$ 不是拍脑袋，而是"到达彼此独立且稀有"的直接后果。合理性核对：忽略高阶项后 $P(0,\delta) + P(1,\delta) + P(2,\delta) \approx (1 - \lambda\delta) + \lambda\delta + 0 = 1$ ✓，概率归一没有被破坏，前提只是 $\lambda\delta$ 足够小。与右栏复习对照：这里的 $\lambda\delta$ 恰好扮演伯努利过程中的 $p$——"每小格一次伯努利试验"的图像是下一页推导泊松分布列的全部秘密。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">PMF of Number of Arrivals N（到达次数 N 的分布列）</span>

```math
P(k, \tau) = \frac{(\lambda\tau)^k\, e^{-\lambda\tau}}{k!}, \qquad k = 0, 1, \ldots
```
- $\mathrm{E}[N] = \lambda\tau$，$\sigma_N^2 = \lambda\tau$，$M_N(s) = e^{\lambda\tau (e^s - 1)}$。
- **细离散化（finely discretize）$[0, t]$**：近似为 Bernoulli（伯努利过程）——离散近似下的 $N_t$ 服从 binomial（二项分布）。
- 取 $\delta \to 0$（或 $n \to \infty$）得：$\mathrm{E}[N_t] = \lambda t$，$\mathrm{var}(N_t) = \lambda t$。
- **例**：你按泊松过程收到 email（电子邮件），$\lambda = 0.4$ messages/hour（条/小时）。你每三十分钟查一次邮箱：
  - Prob(no new messages)（没有新邮件）$= \underline{\qquad}$
  - Prob(one new message)（恰有一封新邮件）$= \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.310–312（Fig. 6.5 细离散化论证）；Example 6.8, p.312–314</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 先验算空栏：半小时即 $\tau = 0.5$ 小时，参数 $\lambda\tau = 0.4 \times 0.5 = 0.2$，于是 $P(N = 0) = e^{-0.2} \approx 0.8187$ ✓，$P(N = 1) = 0.2\,e^{-0.2} \approx 0.1637$ ✓。教材 Example 6.8（p.312–314 处，$\lambda = 0.2$ 条/小时、每小时查一次）与此同型：$\lambda = 0.2$ 条/小时、每小时查一次，得 $e^{-0.2} \approx 0.819$ 与 $0.2\,e^{-0.2} \approx 0.164$，数字几乎复现。均值与方差的来历走细离散化：$n = t/\delta$ 个小槽、每槽成功概率 $p = \lambda\delta$，二项近似给出 $\mathrm{E}[N_t] = np = \lambda t$、$\mathrm{var}(N_t) = np(1-p) = \lambda t (1 - \lambda\delta) \to \lambda t$，教材 Fig. 6.5（p.311）画的正是这张"格点变密"的图 ✓。矩母函数 $M_N(s) = e^{\lambda\tau(e^s - 1)}$ 也可核对：Lec 12 的 transform（变换）表中泊松分布列的变换是 $e^{\lambda(e^s - 1)}$，把强度 $\lambda$ 换成 $\lambda\tau$ 即得；再对 $s$ 求导在 $s = 0$ 处取值，$M_N'(0) = \lambda\tau$ 与均值吻合 ✓——三条信息（PMF、矩、变换）互相咬合，这是"同一分布的多种身份证"。解题纪律上再提醒两点：其一，看到"每小时 $\lambda$ 条、每半小时查一次"这类句式，第一步永远是统一单位、写出 $\lambda\tau$；其二，$P(N=0) + P(N=1) \approx 0.982$ 说明这半小时的邮件流几乎只有"零封或一封"两种剧本——当 $\lambda\tau$ 不大时，泊松分布列的质量集中在前几项，这也正是它可以充当"稀有事件计数"的原因。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example（邮件例题）</span>

- 你按泊松过程收到 email，$\lambda = 5$ messages/hour（条/小时）。你每三十分钟查一次邮箱。
- Prob(no new messages) $= \underline{\qquad}$
- Prob(one new message) $= \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.312–314</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验算：$\tau = 0.5$ 小时，参数 $\lambda\tau = 5 \times 0.5 = 2.5$，故 $P(N = 0) = e^{-2.5} \approx 0.0821$ ✓，$P(N = 1) = 2.5\,e^{-2.5} \approx 0.2052$ ✓。卡点诊断一：最容易犯的错是把泊松分布列的参数写成 $\lambda = 5$——它必须是"区间长度乘以到达率" $\lambda\tau$，"到达率"描述的是单位时间的平均强度，而分布列描述的是一段具体区间。卡点诊断二：单位换算，"三十分钟"要化为 $0.5$ 小时，与 $\lambda$ 的"每小时"对齐；若题设改成"每分钟 $\lambda$ 条"而检查间隔是九十秒，同样的换算纪律适用。对比上一页 $\lambda = 0.4$ 的同型例题：结构完全一样，$P(0) = e^{-\lambda\tau}$、$P(1) = \lambda\tau e^{-\lambda\tau}$，只是参数从 $0.2$ 涨到 $2.5$，"零事件"概率从约 $82\%$ 跌到约 $8\%$——均值越大，"什么都没发生"越稀有，这与 $\mathrm{E}[N] = \lambda\tau$ 给出的直觉（平均每次查到 2.5 封）互相印证，也是泊松 PMF 峰值随参数右移的具体体现。顺手补一个有用的派生量：$P(\text{至少一封}) = 1 - e^{-2.5} \approx 0.918$——取补集一步到位，比逐项相加便宜得多，这类 $1 - e^{-\lambda\tau}$ 的形式在"至少一次"型问题里会反复出现。两个例题（$\lambda = 0.4$ 与 $\lambda = 5$）合并来看，它们其实演练的是同一套动作：确认过程是泊松 → 换算出区间长度 $\tau$ → 相乘得参数 $\lambda\tau$ → 查泊松分布列，请把这套动作练成肌肉记忆。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Interarrival Times（到达间隔时间）</span>

- $Y_k$：第 $k$ 次到达的时刻。
- **Erlang distribution（尔朗分布）**：
```math
f_{Y_k}(y) = \frac{\lambda^k\, y^{k-1}\, e^{-\lambda y}}{(k-1)!}, \qquad y \ge 0 .
```

> <span style="color:#7f8c8d;">图：$r = 1, 2, 3$ 阶 Erlang PDF 曲线 $f_{Y_r}(y)$ 的叠加对比——阶数越高，峰越靠右（均值 $r/\lambda$ 递增）、形状越趋于对称（Image by MIT OpenCourseWare）。</span>

- 第 $k = 1$ 次到达（首次到达）的时刻：exponential（指数分布）：
```math
f_{Y_1}(y) = \lambda e^{-\lambda y}, \qquad y \ge 0 .
```
  - **无记忆性（memoryless property）**：直到下一次到达的时间与过去 independent（无关）。

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.312–317</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 首达时间的 PDF 可以从定义零成本推出：事件 $\{T > t\}$ 等价于"$[0, t]$ 内零到达"，故 $P(T > t) = P(0, t) = e^{-\lambda t}$，对 $t$ 求导得 $f_T(t) = \lambda e^{-\lambda t}$ ✓——这是教材 p.312 的推导，也是"到达次数分布"反哺"时间分布"的第一例。无记忆性的验算（教材 p.314）：$P(\bar{T} - t > s) = P\big([t, t+s] \text{ 内零到达}\big) = P(0, s) = e^{-\lambda s}$，与"已经等了多久"无关 ✓，教材称之为 fresh start（重新开始）：从任何时刻 $t$ 切开，未来都是一个全新的泊松过程。Erlang 一侧：$Y_k = T_1 + \cdots + T_k$ 是 $k$ 个独立同分布指数变量之和（p.316），故 $\mathrm{E}[Y_k] = k/\lambda$、$\mathrm{var}(Y_k) = k/\lambda^2$；其 PDF 的推导（p.317）与伯努利版 Pascal 的论证逐字同构——事件 $A$ = "$[y, y+\delta]$ 内恰有一次到达"（$\approx \lambda\delta$），事件 $B$ = "此前恰有 $k-1$ 次到达"，$A$、$B$ 独立，相乘除以 $\delta$ 即得 ✓。100B 视角：$\int_0^\infty \lambda^k y^{k-1} e^{-\lambda y}\, dy = 1$ 可用分部积分对 $k$ 归纳验证，指数族对卷积封闭在这里显形。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Bernoulli/Poisson Relation（伯努利过程与泊松过程的对应）</span>

> <span style="color:#7f8c8d;">图：把长度为 $t$ 的区间切成 $n = t/\delta$ 个小槽，每槽成功概率 $p = \lambda\delta$，故 $np = \lambda t$；令槽宽 $\delta \to 0$，离散到达流收敛为连续到达流。</span>

| | POISSON（泊松） | BERNOULLI（伯努利） |
|:---|:---:|:---:|
| Times of Arrival（到达时刻） | Continuous（连续），$\lambda$ /unit time | Discrete（离散），$p$ /per trial |
| PMF of # of Arrivals（到达次数的分布列） | Poisson | Binomial |
| Interarrival Time Distr.（到达间隔的分布） | Exponential | Geometric |
| Time to k-th arrival（到第 $k$ 次到达的时间） | Erlang | Pascal |

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.311–314（Fig. 6.5–6.6）；§6.1, p.303–304；p.307（二项 → 泊松近似）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 这张对应表是本讲战略价值最高的一页，它的底层机制只有一条：二项分布列的泊松近似（罕见事件定律）。教材 p.307 的证明值得在脑内重放：固定 $k$，令 $n \to \infty$、$p = \lambda/n$，则 $\binom{n}{k} p^k (1-p)^{n-k} \to e^{-\lambda}\lambda^k / k!$，其中起承重作用的是 $(1 - \lambda/n)^n \to e^{-\lambda}$——这正是 100B 实分析里用对数展开处理过的标准极限（也是 6.042J 讲复利式增长时的近亲）。表中其余各行都是同一条极限的另一面：到达次数 Binomial $\to$ Poisson 已由上式给出；到达间隔 Geometric $\to$ Exponential 对应 $(1-p)^t \approx e^{-\lambda t}$；到第 $k$ 次到达的时间 Pascal $\to$ Erlang 则是"间隔之和"的极限。Pascal 一侧的计数推导在教材 p.303–304：$\{Y_k = t\}$ 等价于"第 $t$ 次试验成功 **且** 前 $t - 1$ 次中恰有 $k - 1$ 次成功"，两事件独立、相乘即得——用的正是 Lec 04 的组合计数工具 $\binom{t-1}{k-1}$。方法论收束：离散原型提供可计算的精确分布，极限过程把它连续化；"先离散、后取极限"从此成为处理连续时间到达模型的标准套路，本讲后面每一页都在重演它。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Merging Poisson Processes（泊松过程的叠加与合并）</span>

- independent Poisson random variables（独立泊松随机变量）之和是 Poisson。
- independent Poisson processes（独立泊松过程）的 merging（合并）仍是 Poisson。

> <span style="color:#7f8c8d;">图：红灯泡闪烁（Poisson，速率 $\lambda_1$）与绿灯泡闪烁（Poisson，速率 $\lambda_2$）两串闪光汇成一条合并到达流（仍为 Poisson）。</span>

- **课堂提问**：下一次到达来自第一个过程的概率是多少？$\underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.318–320（Example 6.14, p.319）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 合并的验证走小区间论证（教材 p.319 的邮局例：寄信者流 $\lambda_1$、寄包裹者流 $\lambda_2$）：宽 $\delta$ 的区间内红灯闪 $\approx \lambda_1\delta$、绿灯闪 $\approx \lambda_2\delta$，两者不相容且独立，故合并流满足 $P(1, \delta) \approx (\lambda_1 + \lambda_2)\delta$、$P(0, \delta) \approx 1 - (\lambda_1 + \lambda_2)\delta$、多次到达可忽略——定义的三条性质逐一过关，合并流是速率 $\lambda_1 + \lambda_2$ 的泊松过程 ✓。课堂提问的答案：给定 $\delta$ 内恰有一次到达，它来自第一个过程的条件概率为 $\dfrac{\lambda_1\delta}{\lambda_1\delta + \lambda_2\delta} = \dfrac{\lambda_1}{\lambda_1 + \lambda_2}$ ✓——两个 $\delta$ 约掉，答案与"观察窗多小"无关；教材 p.319 进一步指出各次到达的来源相互独立，"来源标签"像一枚正面概率为 $\lambda_1/(\lambda_1+\lambda_2)$ 的独立硬币。跨课程连接：离散侧的合并（教材 p.303–304）给出每槽到达概率 $p + q - pq$，用 6.042J 的 inclusion-exclusion（容斥）一眼看穿；代入 $p = \lambda_1\delta$、$q = \lambda_2\delta$ 并令 $\delta \to 0$，二阶项 $pq$ 消失，恰得 $\lambda_1 + \lambda_2$——容斥公式在连续极限下只留下一阶残骸。这条"竞争指数"机制还是下一讲灯泡例题（哪只先烧断）的引擎，请留意它的反复出场。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
