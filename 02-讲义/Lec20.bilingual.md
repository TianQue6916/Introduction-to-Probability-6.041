# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 20 — The Central Limit Theorem（中心极限定理）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The theorem（定理陈述）</span>

**阅读（Readings）**：教材 Section 5.4。

- 设 $X_1, \ldots, X_n$ 为 i.i.d.，方差 $\sigma^2$ 有限。对"标准化"的和 $S_n = X_1 + \cdots + X_n$：
```math
Z_n = \frac{S_n - \mathrm{E}[S_n]}{\sigma_{S_n}} = \frac{S_n - n\,\mathrm{E}[X]}{\sigma \sqrt{n}}
```
  - $\mathrm{E}[Z_n] = 0$，$\mathrm{var}(Z_n) = 1$。
- 设 $Z$ 为标准正态随机变量（零均值、单位方差）。
- **定理**：对每个 $c$：
```math
P(Z_n \le c) \;\longrightarrow\; P(Z \le c)
```
- $P(Z \le c)$ 是标准正态 CDF，记作 $\Phi(c)$，查正态分布表可得。

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.273–274</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 两条标准化性质可当场验算：$\mathrm{E}[Z_n] = (\mathrm{E}[S_n] - n\mu)/(\sigma\sqrt{n}) = 0$ ✓；$\mathrm{var}(Z_n) = \mathrm{var}(S_n)/(\sigma^2 n) = n\sigma^2/(n\sigma^2) = 1$ ✓（分子分母分别用到 Lec 05–06 的期望线性与方差和规则）。定理本体（教材 p.274 框）的惊人之处在假设之少：除 i.i.d. 与有限方差外对分布不作任何要求——$X_i$ 可离散、可连续、可混合，教材 p.274 明言"it places no other requirement on the distribution"，其证明概要留在章末习题。读定理时务必盯住收敛的对象：$Z_n$ 的**累积分布函数**逐点收敛到 $\Phi$，而不是密度或分布列的收敛——这一字之差是本讲最重要的概念分水岭，后面"它究竟说了什么"一节会专门展开。上讲埋下的"第三种缩放"伏笔在此兑现：$S_n/\sqrt{n}$ 刻度上方差不再漂移，形状才有稳定的极限，而极限形状竟是正态——与父分布是什么毫无关系。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Convergence illustrated（收敛的直观演示）</span>

> <span style="color:#7f8c8d;">图：六幅小图，分别对应 $n = 2, 4, 8, 16, 32$ 时若干 i.i.d. 随机变量之和的密度曲线——随 $n$ 增大，曲线从中等偏斜的形状逐步抹平、展开为对称的钟形，与正态密度的吻合肉眼可见（原图无文字说明，此处按图意概述）。</span>

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.277</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Usefulness（中心极限定理的用处）</span>

- universal（普适）：只用得到均值与方差。
- accurate computational shortcut（精确的计算捷径）。
- justification of normal models（为正态模型提供正当性）。

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.274–275</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 把教材 p.274 的两段议论对齐到这三条上。**普适性**来自定理只消费均值与方差两个数——你不需要知道 $X_i$ 的完整分布就能把 $S_n$ 的概率问题送进 $\Phi$ 表，这解释了它为何是概率论里被引用最频繁的定理。**计算捷径**在教材 p.274–275 说得直白：它"eliminates the need for detailed probabilistic models"，免掉 PMF/PDF 的繁琐卷积（回看 Lec 10：两个独立变量之和要卷积一次，$n$ 个就是 $n-1$ 次——CLT 把这一切压缩成一次查表）。**正态模型的正当性**则是概念层面的馈赠：噪声常是大量微小独立随机因素的总和，CLT 证明了这类总和理应长得像正态，教材 p.274 称其为对经验现象"a convincing explanation"——工程里"噪声假设为高斯"从此不再是拍脑袋，而是有定理背书的建模选择。三条用处层层递进：第一条管理论，第二条管算题，第三条管建模。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">What exactly does it say?（它究竟说了什么？）</span>

- $Z_n$ 的 **CDF** 收敛到正态 CDF。
  - **不是**关于 PDF 或 PMF 收敛的陈述。

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.274</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> 这是本讲最容易失分的一句话，值得用反例钉死。取 $X_i$ 为 Bernoulli($p$)，则 $Z_n$ 是离散变量，其 PMF 永远是一根根分离的尖刺：无论 $n$ 多大，$Z_n$ 的分布列在任意两点之间都是零，而正态密度处处连续为正——逐点看 PMF 永远不收敛到正态密度 ✓。连续父分布同样要小心：和的支撑会随 $n$ 变化、密度抖动可以很剧烈，逐点收敛同样无保证。那 CDF 收敛究竟给了什么？它保证的只是"概率质量落在 $(-\infty, c]$ 里的总量"趋于 $\Phi(c)$——质量怎么**分配**在小区间上，定理一概不问。这也正是下一节"二项近似的 1/2 修正"的伏笔：对离散的 $S_n$，事件 $\{S_n \le 21\}$ 的概率是若干尖刺的求和，而正态近似把它换成密度曲线下的面积，两种离散化方案（端点 21 还是 21.5）给出的面积不同——差之毫厘的根源正在"CDF 收敛不约束质量如何摆放"。教材 p.274 的定理框措辞（"the CDF of $Z_n$ converges to the standard normal CDF"）精确且克制，读定理时要逐字。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Normal approximation（正态近似）</span>

- 把 $Z_n$ **当作**正态处理——等价地，也把 $S_n$ 当作正态处理（均值 $n\mu$、方差 $n\sigma^2$）。
- $n$ "适中"（moderate）时能用吗？
  - 能，但没有漂亮的定理作保证（no nice theorems to this effect）。
  - 对称性帮大忙（symmetry helps a lot）。

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.275–277</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> "把 $S_n$ 当正态"的合法性来自教材 p.275 的 Approximations 框：正态性在线性变换下保持，故 $Z_n$ 近似正态 $\Leftrightarrow$ $S_n$ 近似 $\mathrm{N}(n\mu, n\sigma^2)$；三步流程是——算 $n\mu$ 与 $n\sigma^2$、算标准化值 $z = (c - n\mu)/(\sigma\sqrt{n})$、查表 $P(S_n \le c) \approx \Phi(z)$ ✓。卡点在"moderate $n$"：教材 p.277 坦白"there are no simple and general guidelines"——近似质量取决于父分布离正态有多远，尤其取决于**对称性**：$X_i$ 均匀时 $n = 58$ 已非常接近正态，$X_i$ 指数（重偏斜）时则需要大得多的 $n$；且 $c$ 越靠近 $S_n$ 的均值，近似越忠实 ✓。这与上面的演示图呼应：对称父分布从 $n = 2$ 起步就更快地"钟形化"。实操守则由此而来：父分布对称、求和居中，中等 $n$ 就敢用；偏斜重、算尾部，就加倍谨慎或换泊松近似。没有定理保航的近似，靠的是这类经验法则加自查。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The pollster's problem using the CLT（用 CLT 重解民调问题）</span>

- $f$：人群中回答"……"的比例；$X_i$：第 $i$ 位受访者（"是"为 1、"否"为 0）；$M_n = (X_1 + \cdots + X_n)/n$。
- 目标同前：
```math
P(|M_n - f| \ge .01) \le .05
```
- 关键事件链：$|M_n - f| \ge .01$ 等价于
```math
\left| \frac{X_1 + \cdots + X_n - nf}{n} \right| \ge .01
\qquad \Longleftrightarrow \qquad
\left| \frac{X_1 + \cdots + X_n - nf}{\sigma \sqrt{n}} \right| \ge \frac{.01\, \sqrt{n}}{\sigma}
```
- 用 CLT 近似并利用 $\sigma \le 1/2$：
```math
P(|M_n - f| \ge .01) \;\approx\; P\!\left(|Z| \ge \frac{.01\, \sqrt{n}}{\sigma}\right) \;\le\; P(|Z| \ge .02\, \sqrt{n})
```

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.276–277</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 把链条最后一步解到底。$\sigma^2 = \mathrm{var}(X_i) = f(1 - f) \le 1/4$，故 $\sigma \le 1/2$，于是阈值 $0.01\sqrt{n}/\sigma \ge 0.01\sqrt{n}/(1/2) = 0.02\sqrt{n}$ ✓（阈值放大只会让尾概率变小，所以是上界）。再要求 $P(|Z| \ge 0.02\sqrt{n}) \le 0.05$：由正态表 $\Phi(1.96) = 0.975$，即 $P(|Z| \ge 1.96) = 0.05$，故需 $0.02\sqrt{n} \ge 1.96$，解得 $\sqrt{n} \ge 98$，$n \ge 9604$ ✓——教材 Example 5.11（p.276–277）正是这笔账，并总结"This is significantly better than the sample size of 50,000"。对比上讲：切比雪夫要 5 万人，CLT 只要约 9604 人，**节省约五倍**；差价的来源是切比雪夫把非正态的最坏形状也一并承保，而 CLT 利用了"和最终长得像正态、尾部比切比雪夫假设的细"这一事实。工程注脚：实际民调还需考虑抽样非独立、无回答偏差等模型失效问题——定理给的是数学下限，不是操作手册。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Apply to binomial（应用于二项分布）</span>

- 固定 $p$，其中 $0 < p < 1$。
- $X_i$：Bernoulli($p$)；则 $S_n = X_1 + \cdots + X_n$：Binomial($n$, $p$)——均值 $np$、方差 $np(1 - p)$。
- $S_n$ 的 CDF 满足：
```math
\frac{S_n - np}{\sqrt{np(1 - p)}} \;\longrightarrow\; \text{standard normal}
```
- **例**：$n = 36$，$p = 0.5$；求 $P(S_n \le 21)$。
- 精确答案：
```math
\sum_{k=0}^{21} \binom{36}{k} \left(\frac{1}{2}\right)^{36} = 0.8785
```

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.277</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 参数先算清：$np = 18$，$np(1-p) = 9$，$\sigma_{S_n} = 3$。二项即伯努利指示变量之和，是 CLT 的直接特例——教材把这条特例单列成 De Moivre–Laplace 近似（p.277），因为它的历史最老、用途最广。精确值 $0.8785$ 的出身是纯计数（教材 §1.5 的二项公式；Lec 04 已见 $\binom{n}{k}p^k(1-p)^{n-k}$，6.042J 的组合恒等式在这里供给分子）：21 个及以下位置放正面的方式数比上总数 $2^{36}$。近似一路怎么做？**带上 1/2 修正**（下一节主角）：$P(S_n \le 21) \approx \Phi\!\big(\tfrac{21.5 - 18}{3}\big) = \Phi(7/6) = \Phi(1.17) \approx 0.879$，与精确值 $0.8785$ 只差千分之一 ✓；若偷懒不修正，$\Phi\!\big(\tfrac{21-18}{3}\big) = \Phi(1) = 0.8413$，偏差超过 0.037——整整大了四倍。同一个定理，修正与否天壤之别，这正是下一页要专门补偿"离散对连续"的结构性误差的原因。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The 1/2 correction for binomial approximation（二项近似的 1/2 修正）</span>

- $P(S_n \le 21) = P(S_n < 22)$，因为 $S_n$ 是整数。
- **折中（compromise）**：考虑 $P(S_n \le 21.5)$。

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.277</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">De Moivre–Laplace CLT for the binomial PMF（De Moivre–Laplace CLT：近似二项分布列）</span>

- 使用 1/2 修正后，CLT 还能近似二项 **pmf**（而不只是 CDF）：
```math
P(S_n = 19) = P(18.5 \le S_n \le 19.5)
```
```math
18.5 \le S_n \le 19.5 \;\Longleftrightarrow\; \frac{18.5 - 18}{3} \le \frac{S_n - 18}{3} \le \frac{19.5 - 18}{3} \;\Longleftrightarrow\; 0.17 \le Z_n \le 0.5
```
```math
P(S_n = 19) \approx P(0.17 \le Z \le 0.5) = P(Z \le 0.5) - P(Z \le 0.17) = 0.6915 - 0.5675 = 0.124
```
- **精确答案**：
```math
\binom{36}{19} \left(\frac{1}{2}\right)^{36} = 0.1251
```

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.277</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 命名模板——**单点展开为半宽区间法**：离散概率 $P(S_n = 19)$ 在正态近似下没有直接对应物（连续分布单点概率为零），于是把"点 19"撑开成 $[18.5, 19.5]$ 这段宽 1 的区间（上节折中思想的一般化：教材 p.277 的 De Moivre–Laplace 框给的方案正是"从 $k - 1/2$ 到 $k + 1/2$"取正态概率）。验算端点：$(18.5 - 18)/3 = 1/6 \approx 0.17$ ✓，$(19.5 - 18)/3 = 0.5$ ✓；查表 $\Phi(0.5) = 0.6915$、$\Phi(0.17) = 0.5675$，差 $0.124$ ✓。对照精确值 $\binom{36}{19}/2^{36} = 0.1251$，相对误差约 1% ✓——对 $n = 36$ 这般"适中"的样本量已足够体面。几何直觉：正态密度在 $19 \pm 0.5$ 这段近似平顶，单点概率 $\approx$ 密度值 $\times$ 区间宽 1；$Z$ 刻度下区间宽 $1/3$，恰好把尖刺质量摊成一条小面积。近似 CDF 时同样的修正把端点推到 $k + 1/2$——一招两用。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Poisson vs. normal approximations of the binomial（二项分布的泊松近似与正态近似）</span>

- 单位时间段内的泊松到达数 = $n$ 个长度为 $1/n$ 的小段内（相互独立的）泊松到达之和。
  - 令 $n \to \infty$，套用 CLT（？？）
  - ——泊松 = 正态（????）
- Binomial($n$, $p$)：
  - $p$ 固定，$n \to \infty$：正态。
  - $np$ 固定，$n \to \infty$，$p \to 0$：泊松。
- $p = 1/100$，$n = 100$：用泊松。
- $p = 1/10$，$n = 500$：用正态。

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.277；§6.1, p.307</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 幻灯片上的两个问号是全讲最深的一问：泊松变量能写成 $n$ 个独立小段到达之和，那按 CLT 它岂不该是正态？卡点的解法是**看清两条极限路线互不兼容**。路线一：$p$ 固定、$n \to \infty$，均值 $np$ 与方差 $np(1-p)$ 同步走向无穷，标准化后形状趋于正态——CLT 的地盘。路线二：$\lambda = np$ 固定、$n \to \infty$、$p = \lambda/n \to 0$，均值方差别动（都是 $\lambda$），极限是泊松 PMF——这是教材 §6.1（p.307）的泊松近似（"rare events"），也是本课程前面泊松过程单元的基石（泊松分布正是单位时段泊松过程的到达数）。两条路线里 $p$ 与 $n$ 的联动方式不同，极限自然不同，"泊松 = 正态"的悖论感来自把两条路线偷偷混用。判据落到参数上：$np = 1$（p.1/100 例）事件稀有且计数小，泊松近似既准又省；$np = 50$（p.1/10 例）计数不小，正态（连同 1/2 修正）更合适。同一台 CLT，走哪条路线由极限方式说了算。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
