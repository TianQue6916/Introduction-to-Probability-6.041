# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 19 — Limit Theorems – I（极限定理 I）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline（本讲大纲）</span>

**阅读（Readings）**：教材 Sections 5.1–5.3；开始 Section 5.4。

**核心问题**：设 $X_1, \ldots, X_n$ 为 i.i.d.（独立同分布）随机变量，
```math
M_n = \frac{X_1 + \cdots + X_n}{n},
```
当 $n \to \infty$ 时会发生什么？

**本讲大纲（Lecture outline）**：
- 为什么要操心？（Why bother?）
- 一个工具：Chebyshev's inequality（切比雪夫不等式）。
- 收敛"in probability"（依概率收敛）。
- $M_n$ 的收敛：弱大数定律（weak law of large numbers）。

> <span style="color:#7f8c8d;">Bertsekas §5.1, p.265–267；§5.2, p.269</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲开启"极限定理"单元，它给整个前半学期一个回响：教材 §5.1 开篇（p.265）列出三条"为什么要操心"——(a) 概念上，它把期望 $\mathrm{E}[X]$ 解释为"大量独立重复实验的平均值"，让第 1 章的公理化定义获得频率意义；(b) 分析上，它让你不必写出 $S_n$ 那个越来越臃肿的 PMF/PDF 就能把握其性质；(c) 统计上，一切基于大数据的推断都靠它兜底。技术路线是三步走：先把 Chebyshev 不等式造出来（唯一的重武器），再用它定义并证明"依概率收敛"，最后一步收敛到本讲主角——弱大数定律，$M_n$ 依概率收敛到 $\mu$。注意路线图的反向关系：**大数定律不是新公理，而是切比雪夫不等式的直接推论**，两行方差计算就够。下一讲再把同一台机器换成更锋利的正态近似（CLT），本讲埋好的"三种缩放"伏笔将在那里揭晓。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Chebyshev's inequality（切比雪夫不等式）</span>

- 设随机变量 $X$ 有有限均值 $\mu$ 与方差 $\sigma^2$。从方差定义出发：
```math
\sigma^2 = \int (x - \mu)^2 f_X(x)\, dx \;\ge\; \int_{-\infty}^{-c} (x - \mu)^2 f_X(x)\, dx + \int_{c}^{\infty} (x - \mu)^2 f_X(x)\, dx \;\ge\; c^2 \cdot P(|X - \mu| \ge c)
```
- 于是得到 **Chebyshev 不等式**：
```math
P(|X - \mu| \ge c) \le \frac{\sigma^2}{c^2}
```
- 换用标准差单位（取 $c = k\sigma$）的等价形式：
```math
P(|X - \mu| \ge k\sigma) \le \frac{1}{k^2}
```

> <span style="color:#7f8c8d;">Bertsekas §5.1, p.267–268</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 幻灯片的推导链要逐段看清"丢掉了什么、放大了什么"：第一步把全域积分砍成两翼（$|x - \mu| \ge c$ 之外的部分被扔掉，不等号向小走）；第二步在两翼上把 $(x-\mu)^2$ 放大到下界 $c^2$ 再提出来，恰好剩下 $P(|X-\mu| \ge c)$（不等号向大走）——两头夹逼即成。教材 p.267 还给出另一条不经过 Markov 不等式的路线：构造阶梯函数 $g(x) = c^2$（当 $|x - \mu| \ge c$，否则为 0），由 $(x - \mu)^2 \ge g(x)$ 对 $\sigma^2$ 的积分直接放缩。$k\sigma$ 形式同样可验证：$P(|X - \mu| \ge k\sigma) \le \sigma^2/(k^2\sigma^2) = 1/k^2$ ✓——偏离 $k$ 个标准差的概率不超过 $1/k^2$。卡点诊断：这界通常很松，教材 Example 5.2（p.268）对均匀分布算出的界"uninformative"（毫无信息量）；Example 5.3（p.268）补了一个有用的副产品——若 $X \in [a, b]$ 而方差未知，可用 $\sigma^2 \le (b - a)^2/4$ 代替（等号在两端点各半概率时取到）。第一性原理的启示：**只用均值和方差就能约束概率**，这正是下一讲民调问题敢在分布完全未知时开出的支票。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Deterministic limits（确定性序列的极限）</span>

- 设 $a_n$ 为数列，$a$ 为一个数。
- $a_n$ 收敛到 $a$："a_n 最终会且保持（任意接近地）靠近 a"：
```math
\lim_{n \to \infty} a_n = a
```
- **对每个** $\varepsilon > 0$，存在 $n_0$，使得**对每个** $n \ge n_0$ 都有
```math
|a_n - a| \le \varepsilon .
```

> <span style="color:#7f8c8d;">Bertsekas §5.3, p.271</span>

> <span style="color:#1e8449;">**[note] Note（译者注，跨课程连接）:**</span> 这一页是纯铺垫，却值得慢读，因为它搬出了你在 100B 实分析里反复打磨的 $\varepsilon$–$N$ 语言：$\forall \varepsilon > 0,\ \exists n_0,\ \forall n \ge n_0: |a_n - a| \le \varepsilon$。教材 p.271 特意把两种收敛定义并排放置以便对照——数列收敛里那句"a_n eventually gets **and stays** close to a"（最终靠近**并保持**靠近）是关键：一旦进入 $\varepsilon$-带就永不掉队。讲义为什么要在讲随机变量之前先复习确定性极限？因为下一页的"依概率收敛"将逐字复用这套句法，只把"序列必然落在带内"弱化为"序列以趋于 1 的概率落在带内"。实分析的训练在此兑现：谁对 $\varepsilon$–$N$ 的逻辑顺序（先给精度、再找时刻、之后全部有效）有肌肉记忆，谁就能一眼看穿"依概率收敛"的定义结构——甚至能预见到两种收敛的差异必然出现在"偶尔掉队"的环节上。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Convergence "in probability"（依概率收敛）</span>

- 设 $Y_n$ 为随机变量序列。称 $Y_n$ **依概率收敛**（converges in probability）到数 $a$："(almost all) 的 PMF/PDF 最终集中到 a 的（任意小的）邻域内"。
- **对每个** $\varepsilon > 0$：
```math
\lim_{n \to \infty} P(|Y_n - a| \ge \varepsilon) = 0 .
```

> <span style="color:#7f8c8d;">图：$Y_n$ 的 pmf——质量 $1 - 1/n$ 位于 $0$，质量 $1/n$ 位于 $n$。问题：$Y_n$ 收敛吗？</span>

> <span style="color:#7f8c8d;">Bertsekas §5.3, p.271–272</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 先验算图中的例子：取 $Y_n = 0$（概率 $1 - 1/n$）、$Y_n = n$（概率 $1/n$）。对任意固定 $\varepsilon > 0$，当 $n > \varepsilon$ 时事件 $\{|Y_n - 0| \ge \varepsilon\}$ 就是 $\{Y_n = n\}$，故 $P(|Y_n| \ge \varepsilon) = 1/n \to 0$ ✓——$Y_n$ 依概率收敛到 0。卡点诊断有二。其一，依概率收敛**容忍稀有的大偏离**：那个逃向无穷远的 $1/n$ 质量点从不消失，只是越来越稀薄；确定性收敛的"stays close"被弱化成"以趋于 1 的概率 close"，教材 p.271 的等价重述（对任意精度 $\varepsilon$ 与置信 $\delta$，$n$ 充分大后 $P(|Y_n - a| > \varepsilon) < \delta$）正是这个意思。其二，别把依概率收敛与矩的收敛混为一谈：此例中 $\mathrm{E}[Y_n] = n \cdot \tfrac{1}{n} = 1$ 恒成立，永远不趋于 0 ✓——期望可以被极小概率的巨值撑住。这两个卡点在后面讲 CLT 时会回响：$Z_n$ 的 CDF 收敛同样不保证 PMF/PDF 逐点收敛。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Convergence of the sample mean（样本均值的收敛：弱大数定律）</span>

- 设 $X_1, X_2, \ldots$ 为 i.i.d.，具有有限均值 $\mu$ 与方差 $\sigma^2$，$M_n = \dfrac{X_1 + \cdots + X_n}{n}$。
- **课堂填空**：
  - $\mathrm{E}[M_n] = \underline{\qquad}$
  - $\mathrm{Var}(M_n) = \underline{\qquad}$
- 于是对任意 $\varepsilon > 0$：
```math
P(|M_n - \mu| \ge \varepsilon) \le \frac{\mathrm{Var}(M_n)}{\varepsilon^2} = \frac{\sigma^2}{n \varepsilon^2} \;\xrightarrow[n \to \infty]{}\; 0
```
- 即 **$M_n$ 依概率收敛到 $\mu$**——这就是弱大数定律（weak law of large numbers）。

> <span style="color:#7f8c8d;">Bertsekas §5.2, p.269–270</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 前后讲回指）:**</span> 两个空全部来自已学工具：由期望的线性（Lec 05–06 已建立，Lec 07 推广到多维，对任意联合分布成立），$\mathrm{E}[M_n] = \frac{1}{n}\sum_i \mathrm{E}[X_i] = \mu$ ✓；由 Lec 07 的方差和规则（独立时 $\mathrm{Var}(X_1 + \cdots + X_n) = n\sigma^2$），$\mathrm{Var}(M_n) = \frac{1}{n^2} \cdot n\sigma^2 = \sigma^2/n$ ✓。代入 Chebyshev 不等式，右边 $\sigma^2/(n\varepsilon^2) \to 0$，弱大数定律两行到手——教材 p.269 的推导与我们逐字相同。卡点预警：方差和规则用到独立性，但期望的线性不需要，所以 $\mathrm{E}[M_n] = \mu$ 的适用面其实更宽。教材 p.269 还留了一句惊人的备注：弱大数定律在 $X_i$ 方差无穷时依然成立（只需 $\mathrm{E}[X_i]$ 有定义），只是证明要换一整套重机器——切比雪夫路线只是众多路径中最平的一条。直觉图像：$n$ 增大时 $M_n$ 的分布"收拢"到 $\mu$ 附近，这正是"把期望理解为长期平均"的第一块严谨基石。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The pollster's problem（民调问题）</span>

- $f$：人群中回答"……"的比例。
- 第 $i$ 个（被随机抽中的）受访者：
```math
X_i = \begin{cases} 1, & \text{if yes（回答"是"）}, \\ 0, & \text{if no（回答"否"）}.\end{cases}
```
- $M_n = (X_1 + \cdots + X_n)/n$：样本中回答"是"的比例。
- **目标**：95% 的置信度、误差不超过 1%：
```math
P(|M_n - f| \ge .01) \le .05
```
- 使用 Chebyshev 不等式：
```math
P(|M_n - f| \ge .01) \le \frac{\sigma_M^2}{(0.01)^2} = \frac{\sigma_X^2}{n (0.01)^2} \le \frac{1}{4 n (0.01)^2}
```
- 若 $n = 50{,}000$，则 $P(|M_n - f| \ge .01) \le .05$（偏保守 conservative）。

> <span style="color:#7f8c8d;">Bertsekas §5.2, p.270</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 两处关键不等式都可真算。其一，$X_i$ 是 Bernoulli 变量，$\sigma_X^2 = f(1 - f)$；配方得 $f(1 - f) = \tfrac{1}{4} - (f - \tfrac{1}{2})^2 \le \tfrac{1}{4}$ ✓，最坏情形 $f = 1/2$（民意五五开，最难测）。其二，要求 $\dfrac{1}{4n(0.01)^2} \le 0.05$，即 $\dfrac{2500}{n} \le 0.05$，解得 $n \ge 50{,}000$ ✓——与教材 Example 5.5（p.270）的数字完全一致，书中还明说这"fairly conservative"。保守性从哪来？切比雪夫只用方差、完全不问分布形状，等于把所有分布的最坏情形一并打包承保。跨课程连接：把 $X_i$ 看成"第 $i$ 位受访者说'是'"的指示变量（indicator），$M_n$ 就是经验频率——这正是 Lec 07 帽子问题与 CLRS 第 5 章指示随机变量分解的同款引擎：样本比例的期望与方差都由微观指示变量拼装而成。预告：下一讲用 CLT 重做本题，样本量将缩小约五倍——保守支票终于可以打折兑现。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Different scalings of $M_n$（样本均值的几种缩放）</span>

- 设 $X_1, \ldots, X_n$ 为 i.i.d.，方差 $\sigma^2$ 有限。考察和的三种变体：
  - $S_n = X_1 + \cdots + X_n$：方差 $n\sigma^2$；
```math
M_n = \frac{S_n}{n} \qquad \text{方差 } \sigma^2/n, \quad \text{依概率收敛到 } \mathrm{E}[X] \text{（WLLN）}
```
  - $S_n / \sqrt{n}$：方差恒为 $\sigma^2$ —— 渐近形状（asymptotic shape）是什么？

> <span style="color:#7f8c8d;">Bertsekas 第 5 章引言，p.263–264</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 前后讲回指）:**</span> 这页是全讲的结构性伏笔，值得用"方差去哪儿了"来串讲。同一条和 $S_n$，乘上不同的常数就得到三种命运：$S_n$ 本身的方差 $n\sigma^2$ 随 $n$ 线性膨胀，分布越摊越宽、不存在有意义的极限；$M_n = S_n/n$ 的方差 $\sigma^2/n$ 衰减到零，分布坍缩成 $\mu$ 处的一根尖刺（Lec 06 已见 $\mathrm{Var}(aX) = a^2\mathrm{Var}(X)$，缩放的代价与收益全在这条规则里）——这是弱大数定律的几何面貌；而中间刻度 $S_n/\sqrt{n}$ 的方差恒为 $\sigma^2$，分布既不膨胀也不坍缩，于是"形状"才有资格谈极限。教材第 5 章引言（p.263–264）正是按这三行方差计算铺陈的：减去 $n\mu$、除以 $\sigma\sqrt{n}$ 得到的标准化变量 $Z_n$ 均值 0、方差 1，其渐近形状即中心极限定理的主题。一句话：**大数定律管"位置"，中心极限定理管"形状"，而选对缩放尺度是提问的前提**——尺度选错，问题本身就无解。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The central limit theorem（中心极限定理：预告）</span>

- "标准化"的和 $S_n = X_1 + \cdots + X_n$：
```math
Z_n = \frac{S_n - \mathrm{E}[S_n]}{\sigma_{S_n}} = \frac{S_n - n\,\mathrm{E}[X]}{\sigma \sqrt{n}}
```
  - 零均值；
  - 单位方差。
- 设 $Z$ 为标准正态随机变量（standard normal r.v.，零均值、单位方差）。
- **定理**：对每个 $c$：
```math
P(Z_n \le c) \;\longrightarrow\; P(Z \le c)
```
- $P(Z \le c)$ 即标准正态 CDF（记作 $\Phi(c)$），查正态分布表即可得到。

> <span style="color:#7f8c8d;">Bertsekas §5.4, p.273–274</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 为什么标准化必须做到"减均值、除以 $\sigma\sqrt{n}$"这么精确？第一性原理的答案：极限要存在，就必须先消灭所有会"发散或坍缩"的自由度。$S_n$ 携带两阶信息——位置（$n\mu$，线性增长）与尺度（$\sigma\sqrt{n}$，平方根增长）——减与除恰好把这两层剥掉，剩下的才是纯粹形状；若尺度除错（比如除 $n$），就退回弱大数定律的尖刺，形状问题无解。定理陈述（教材 p.274 框）要咬文嚼字：收敛的是 $Z_n$ 的 **CDF** 在每一点 $c$ 的取值，$\lim_n P(Z_n \le c) = \Phi(c)$——不是 PMF/PDF 的收敛，这个伏笔下一讲会专门引爆。另外请注意定理的假设之少：只需 i.i.d. 与有限方差，对分布形态毫无要求（离散、连续、混合皆可，教材 p.274 原话）。下一讲将全程展开这台"万能正态机"的用法：一张 $\Phi$ 表，就能替代无数卷积计算。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
