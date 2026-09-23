# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 18 — Markov Processes – III（马尔可夫过程 III）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline（本讲大纲）</span>

**阅读（Readings）**：教材 Section 7.4。

**本讲大纲（Lecture outline）**：
- 复习稳态行为（Review of steady-state behavior）。
- 被阻塞电话的概率（Probability of blocked phone calls）。
- 吸收概率的计算（Calculating absorption probabilities）。
- 吸收期望时间的计算（Calculating expected time to absorption）。

> <span style="color:#7f8c8d;">Bertsekas §7.4, p.362–363；§7.3, p.352–353</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 马尔可夫链三部曲在本讲收官，视角发生一次根本切换：Lec 16–17 关心的是**长期行为**——跑了很久之后链"忘记"初值、稳定在平稳分布；本讲则转向**短期行为**——从暂态出发，链会被哪个常返类/吸收态"抓住"？需要多少步？教材 §7.4 开篇（p.362）正是这样定位的：研究 short-term behavior，"链遇到常返态之后的后续行为无关紧要"。大纲四块对应两条主线：其一是应用演示（电话公司问题：用稳态平衡方程算出被阻塞电话的概率，把抽象的 $\pi_j$ 变成可以卖钱的工程量）；其二是方法论沉淀（吸收概率 $a_i$、期望吸收时间 $\mu_i$、平均首达时间 $t_i$ 三套方程，结构完全同型，只是边界条件不同）。学完本讲应当带走一个模板意识：**"首次进入某状态"类问题 = 全概率定理 + 马氏性 + 线性方程组**，后面三节会反复强化这一点。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Review（复习：稳态行为）</span>

- 假设链只有**单一常返类**（single recurrent class）且非周期（aperiodic），外加若干暂态（transient）状态，则
```math
\lim_{n \to \infty} r_{ij}(n) = \pi_j ,
```
  其中 $\pi_j$ 不依赖初始条件：
```math
\lim_{n \to \infty} P(X_n = j \mid X_0 = i) = \pi_j .
```
- $\pi_1, \ldots, \pi_m$ 可作为下述平衡方程（balance equations）的**唯一解**求出：
```math
\pi_j = \sum_{k} \pi_k\, p_{kj}, \qquad j = 1, \ldots, m,
```
  再加上归一化条件
```math
\sum_{j} \pi_j = 1 .
```

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.352–353</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 跨课程连接）:**</span> 这页把 Lec 17 的结论压缩成四行，卡点通常藏在两个前提里。其一，"单一常返类 + 非周期"缺一不可：若有两个常返类，链会永远困在初始所在的那个类里，$\lim r_{ij}(n)$ 显然依赖初值；若常返类周期为 $d$，则 $r_{ij}(n)$ 会像 $n$ 奇偶交替那样振荡（教材 Fig. 7.10 的例子，p.346 起的分类讨论），极限不存在。其二，暂态状态并不被排除在方程组之外，但稳态收敛定理的部分 (c)（p.353）补了一句：暂态 $j$ 的 $\pi_j = 0$，常返 $j$ 的 $\pi_j > 0$——暂态质量随 $n$ 增大流失殆尽。跨课程连接：用 Strang 线性代数的语言看，平衡方程 $\pi_j = \sum_k \pi_k p_{kj}$ 写成矩阵形式就是 $\pi P = \pi$（行向量 $\pi$ 是转移矩阵 $P$ 的特征值 $1$ 对应的左特征向量），归一化再从特征空间里挑出唯一的概率向量——Strang 讲 Markov 矩阵时正是这么引入稳态的，"各列之和为 1 保证了 1 必是特征值"这一事实现在有了概率解释。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example（两状态链示例）</span>

> <span style="color:#7f8c8d;">图：两状态转移图——状态 1 自环 0.5、$1 \to 2$ 为 0.5；状态 2 自环 0.8、$2 \to 1$ 为 0.2。解平衡方程得稳态 $\pi_1 = 2/7$，$\pi_2 = 5/7$。</span>

- 假设过程从状态 1 出发（$X_0 = 1$）。
- **课堂填空**：
  - $P(X_1 = 1,\ \text{且}\ X_{100} = 1) = \underline{\qquad}$
  - $P(X_{100} = 1\ \text{且}\ X_{101} = 2) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.353</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 逐项验算。第一空用乘法法则拆成两段：$P(X_1 = 1,\ X_{100} = 1) = P(X_1 = 1)\, P(X_{100} = 1 \mid X_1 = 1)$。由 $X_0 = 1$ 得 $P(X_1 = 1) = p_{11} = 0.5$；从 $X_1 = 1$ 到 $X_{100} = 1$ 恰好走了 99 步，$r_{11}(99) \approx \pi_1 = 2/7$（99 步足以"忘记"初值）。故答案 $\approx 0.5 \times \tfrac{2}{7} = \tfrac{1}{7} \approx 0.143$ ✓。第二空：到第 100 步时初始条件早已被冲刷掉，$P(X_{100} = 1) \approx \pi_1 = 2/7$；而下一步的转移概率是纯粹的马氏量，$P(X_{101} = 2 \mid X_{100} = 1) = p_{12} = 0.5$，故答案 $\approx \tfrac{2}{7} \times 0.5 = \tfrac{1}{7}$ ✓。两个空答案相同并非巧合：第一空是"确定性首步 × 长期频率"，第二空是"长期频率 × 确定性首步"，乘法交换而已。这道小题的真正用意是训练**何时用 $\pi_j$、何时用 $p_{ij}$**：凡是"远处的边缘分布"用 $\pi_j$，凡是"下一跳的条件概率"用 $p_{ij}$，两者不可混用。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The phone company problem（电话公司问题）</span>

- 电话呼叫按泊松过程（Poisson process）到达，速率为 $\lambda$。
  - 每次通话时长服从指数分布（exponential distribution），参数为 $\mu$。
  - 共有 $B$ 条线路可用（$B$ lines available）。
- 把时间切成长度很小的**离散区间** $\delta$：状态 $0, 1, \ldots, i-1, i, \ldots, B-1, B$（忙线路数）。
- **平衡方程**：
```math
\lambda\, \pi_{i-1} = i \mu\, \pi_i
```
- 解出
```math
\pi_i = \pi_0\, \frac{(\lambda / \mu)^i}{i!}, \qquad \pi_0 = \frac{1}{\sum_{i=0}^{B} \dfrac{(\lambda / \mu)^i}{i!}} .
```

> <span style="color:#7f8c8d;">Bertsekas §7.3, p.353–357</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 平衡方程要从"流量守恒"的第一性原理读起：稳态下，流入状态 $i$ 的概率流量必须等于流出。进入 $i$ 的主要通道是从 $i-1$ 新接通一通电话——长度 $\delta$ 的区间内到达一通电话的概率约为 $\lambda \delta$，故流量为 $\lambda \pi_{i-1}\delta$；离开 $i$ 的通道是某条忙线路挂断——$i$ 条独立忙线各以速率 $\mu$ 完成通话，单位时间完成数合计 $i\mu$（卡点：是 $i\mu$ 而非 $\mu$，每条忙线都是一台独立的指数"时钟"）。两边约去 $\delta$ 即得 $\lambda\pi_{i-1} = i\mu\pi_i$，逐层递推得 $\pi_i \propto (\lambda/\mu)^i / i!$。跨课程连接：这个形状正是教材第 6 章泊松过程的 PMF——$\pi_i$ 就是参数为 $\lambda/\mu$ 的泊松分布截断到 $B$ 再归一化（泊松 PMF 与二项的关系见教材 §6.1, p.307 的近似讨论）。工程上真正想要的是"被阻塞电话的概率"：新呼叫到达时 $B$ 条线全忙，即 $P(\text{阻塞}) = \pi_B$——大纲里的第二块就落在这个数上。$\pi_0$ 的分母是截断指数级数，手算时逐项加即可，不必引入任何特殊函数。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Calculating absorption probabilities（吸收概率的计算）</span>

> <span style="color:#7f8c8d;">图：五状态转移链——状态 4 与 5 为吸收态（自环概率为 1），状态 1、2、3 为暂态，各弧线标注相应的转移概率；本图与下一页"期望时间"图共用同一链结构。</span>

- **问题**：$a_i$ = 从初始状态 $i$ 出发，过程最终停在状态 4 的概率是多少？
- **课堂填空**：
  - 对 $i = 4$：$a_i = \underline{\qquad}$
  - 对 $i = 5$：$a_i = \underline{\qquad}$
- 对其余所有状态 $i$：
```math
a_i = \sum_{j} p_{ij}\, a_j
```
  —— 该方程组有唯一解。

> <span style="color:#7f8c8d;">Bertsekas §7.4, p.362–363</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 先补全两个空：目标态 4 本身就是吸收态，落到它即"停在那里"，故 $a_4 = 1$ ✓；而吸收态 5 一旦进入便永不离开、也永远不会再到 4，故 $a_5 = 0$ ✓——两个边界值是"白送"的，余下的只是解暂态上的方程组。命名模板——**首步分解法**（first-step analysis）：对暂态 $i$，用全概率定理按第一步落点展开 $a_i = \sum_j P(X_1 = j \mid X_0 = i)\, a_j$，再用马氏性把条件概率 $P(X_1 = j \mid X_0 = i)$ 换成 $p_{ij}$——教材 p.363 的推导框正是这两步，并注明唯一性证明放在章末习题。教材 Example 7.10（Fig. 7.17，§7.4 内）是同一技术的完整演练：把常返态 4、5 "合并"成一个吸收态 6，解出 $a_2 = 21/31$、$a_3 = 29/31$——若目标是一整个常返类而非单个吸收态，先合并再套方程即可。跨课程连接：把暂态看成有向图的内部节点、吸收态看成 sink（汇点），方程组就是"从每个内部节点出发、随机游走到某个 sink 的到达概率"，这正是 6.042J 图论里随机游走问题的代数化身。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Expected time to absorption（吸收的期望时间）</span>

- **问题**：$\mu_i$ = 从初始状态 $i$ 出发、到进入吸收态为止的期望转移次数是多少？
- **课堂填空**：
  - 对 $i = \underline{\qquad}$：$\mu_i = 0$
- 对其余所有暂态 $i$：
```math
\mu_i = 1 + \sum_{j} p_{ij}\, \mu_j
```
  —— 该方程组有唯一解。

> <span style="color:#7f8c8d;">Bertsekas §7.4, p.366–367</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 填空答案：$\mu_i = 0$ 对 $i = 4$ 成立 ✓——已经站在吸收态上，无需任何转移；事实上按教材 p.366 的定义（"number of transitions until absorption, starting from $i$"，且明确写道 if $i$ is recurrent, $\mu_i = 0$），吸收态 5 同样给出 $\mu_5 = 0$。卡点诊断：方程里的 "+1" 是新手最容易丢的项——从暂态 $i$ 出发，无论下一步走到哪，**第一步本身都要花掉一次转移**，然后用全期望定理对下一步落点 $j$（概率 $p_{ij}$）加权平均"剩余时间"，于是 $\mu_i = 1 + \sum_j p_{ij}\mu_j$，其中落入吸收态的项贡献 $\mu = 0$、自动消失。这套方程与上一页吸收概率方程是**同一模板、不同边界条件**：$a$ 方程把边界钉在 $\{0, 1\}$，$\mu$ 方程把边界钉在 $0$。教材 §7.4 的姊妹例是"蜘蛛与苍蝇"（Example 7.12，Fig. 7.19，p.367）：苍蝇待在端点、蜘蛛在相邻格点间随机游走，解出 $\mu_2 = \mu_3 = 10/3$——方程组只有两三个未知数时手算即可，代入消元即可收工。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Mean first passage and recurrence times（平均首达时间与平均回访时间）</span>

- 设链只有单一常返类；固定常返态 $s$。
- **平均首达时间**（mean first passage time）——从 $i$ 到 $s$：
```math
t_i = \mathrm{E}\big[\min\{n \ge 0\ \text{such that}\ X_n = s\} \,\big|\, X_0 = i\big]
```
- $t_1, t_2, \ldots, t_m$ 是如下方程组的唯一解：
```math
t_s = 0, \qquad t_i = 1 + \sum_{j} p_{ij}\, t_j \quad \text{for all } i \ne s .
```
- **平均回访时间**（mean recurrence time）——$s$ 回到自身：
```math
t^*_s = \mathrm{E}\big[\min\{n \ge 1\ \text{such that}\ X_n = s\} \,\big|\, X_0 = s\big]
```
```math
t^*_s = 1 + \sum_{j} p_{sj}\, t_j .
```

> <span style="color:#7f8c8d;">Bertsekas §7.4, p.368–369；p.402</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 用教材 Example 7.13（p.368–369）做完整验算：链的转移概率为 $p_{11} = 0.8$、$p_{12} = 0.2$、$p_{21} = 0.6$、$p_{22} = 0.4$，取 $s = 1$。由 $t_1 = 0$ 与 $t_2 = 1 + 0.4\,t_2$ 解得 $t_2 = 1/0.6 = 5/3$ ✓；再算回访时间 $t^*_1 = 1 + p_{11}t_1 + p_{12}t_2 = 1 + 0.2 \times \tfrac{5}{3} = \tfrac{4}{3}$ ✓。另一路独立验证：该链的稳态解为 $\pi_1 = 0.75$、$\pi_2 = 0.25$，而教材 p.402 证明了一般公式 $t^*_s = 1/\pi_s$——$1/\pi_1 = 4/3$，两路完全吻合 ✓。这个恒等式值得单独记住：**回访越"勤"的状态稳态概率越大**，长期频率 $\pi_s$ 就是"每隔 $1/\pi_s$ 步回访一次"的倒数措辞。跨课程连接：$t_i$、$\mu_i$、$a_i$ 三套方程在结构上就是 CLRS 算法分析里的 recurrence（递归式）——"一步代价 + 各分支子问题的期望"——边界条件扮演 base case，解线性方程组扮演"展开递归求闭式"；随机化算法的期望复杂度分析与这里的期望吸收时间，是同一枚硬币的两面。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
