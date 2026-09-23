# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 22 — Bayesian Statistical Inference II（贝叶斯统计推断 II）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Readings &amp; topics（阅读材料与本讲主题）</span>

**阅读（Readings）**：教材 pp. 225–226（§4.3，条件期望与条件方差重温）与 Sections 8.3–8.4（§8.3 贝叶斯 LMS 估计、§8.4 贝叶斯线性 LMS 估计）。

> <span style="color:#7f8c8d;">图：一个 object（目标物）位于未知位置，若干 sensors（传感器）分别对它做带噪声的观测（如 $X = \Theta + W$，噪声 $W \sim f_W$），全部数据汇入一个 Estimator（估计器），输出估计值 $\hat\Theta$——贝叶斯推断的标准场景图。</span>

**本讲主题（Topics）**：
- (Bayesian) Least Mean Squares (LMS) estimation（贝叶斯最小均方估计）。
- (Bayesian) Linear LMS estimation（贝叶斯线性 LMS 估计）。
- **MAP estimate（最大后验估计）**：$\hat\theta_{\mathrm{MAP}}$ 最大化 $f_{\Theta|X}(\theta \mid x)$。
- **LMS estimation（LMS 估计）**：$\hat\Theta = \mathrm{E}[\Theta \mid X]$ 在**所有**估计器 $g(\cdot)$ 中最小化 $\mathrm{E}[(\Theta - g(X))^2]$：
  - 对任意 $x$，$\hat\theta = \mathrm{E}[\Theta \mid X = x]$ 在所有估计值 $\hat\theta$ 中最小化 $\mathrm{E}[(\Theta - \hat\theta)^2 \mid X = x]$。

> <span style="color:#7f8c8d;">Bertsekas §8.3, p.430–436；§8.4, p.437–443；§4.3, p.225–226</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲把贝叶斯工具箱的第三件套摆上台面。上一讲（Lec 21，贝叶斯统计推断 I）已经完成：把未知参数 $\Theta$ 升格为随机变量、由先验 $f_\Theta$ 与观测 $X$ 算出后验 $f_{\Theta|X}$、并用 MAP 法则拍出"后验峰顶"那个单值。MAP 只回答"哪个 $\theta$ 最可能"，却不管估错了会错多远；LMS estimation（LMS 估计）换了一把尺子——最小化均方误差 $\mathrm{E}[(\Theta - g(X))^2]$，答案不是峰顶而是后验均值 $\mathrm{E}[\Theta \mid X]$。幻灯片同时给出两个层次的表述：全局版（在所有函数 $g(X)$ 中最优）与逐点版（固定 $X = x$ 后在所有数 $\hat\theta$ 中最优），后者是前者的证明跳板。本讲随后的全部内容——条件均方误差、误差的正交性质、以及"只许线性"的降级版——都围绕这一个估计器展开。教材章目录给出的页码：§8.3 从 p.430 起、§8.4 从 p.437 起，本讲恰好把第 8 章的两大节走完。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditional mean squared error（条件均方误差）</span>

- $\mathrm{E}[(\Theta - \mathrm{E}[\Theta \mid X])^2 \mid X = x]$：
  - 与 $\mathrm{Var}(\Theta \mid X = x)$ 相同：$\Theta$ 的 conditional distribution（条件分布）的 variance（方差）。

> <span style="color:#7f8c8d;">Bertsekas §8.3, p.430–431</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Predicting X based on Y（用 $Y$ 预测 $X$）</span>

- 两个随机变量 $X, Y$；观测到 $Y = y$。
  - 新宇宙：condition on（条件化于）$Y = y$。
- $\mathrm{E}[(X - c)^2 \mid Y = y]$ 在 $c = \underline{\qquad}$ 处取最小。

> <span style="color:#7f8c8d;">Bertsekas §8.3, p.430–431；§4.3, p.225–226</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 先验算两件事。其一，条件均方误差恒等式：$\mathrm{E}[(\Theta - \mathrm{E}[\Theta \mid X = x])^2 \mid X = x] = \mathrm{E}[\Theta^2 \mid X = x] - (\mathrm{E}[\Theta \mid X = x])^2 = \mathrm{Var}(\Theta \mid X = x)$ ✓——末步就是矩公式 $\mathrm{Var}(Y) = \mathrm{E}[Y^2] - (\mathrm{E}[Y])^2$，Lec 07 的老朋友。其二，填空答案：$c = \mathrm{E}[X \mid Y = y]$ ✓；把 $\mathrm{E}[(X-c)^2 \mid Y = y]$ 展开成 $\mathrm{E}[X^2 \mid Y = y] - 2c\,\mathrm{E}[X \mid Y = y] + c^2$，对 $c$ 求导置零即得。再命名一个证明模板——**"逐点打包 + 重期望合并"**：要证全局最优 $\mathrm{E}[(\Theta - \mathrm{E}[\Theta|X])^2] \le \mathrm{E}[(\Theta - g(X))^2]$，先固定 $x$ 把 $g(x)$ 看成数字、用"围绕均值的二阶矩最小"得逐点不等式；再对 $X$ 取期望，用本讲指定阅读 pp. 225–226（§4.3）的 law of iterated expectations（重期望法则）$\mathrm{E}[\mathrm{E}[\cdot \mid X]] = \mathrm{E}[\cdot]$ 把逐点不等式打包成全局不等式——教材 p.431 的脚注正是这三步。至于"用 $Y$ 预测 $X$"这一页：数学上与估计 $\Theta$ 是同一个定理换了个座位，只是宇宙从"以 $X = x$ 为条件"切换到"以 $Y = y$ 为条件"（Lec 02 条件化世界观的重演）——LMS 因此同时是参数估计与预测理论的核心。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Some properties of LMS estimation（LMS 估计的若干性质）</span>

- Estimator（估计器）：$\hat\Theta = \mathrm{E}[\Theta \mid X]$。
- Estimation error（估计误差）：$\tilde\Theta = \hat\Theta - \Theta$。
- $\mathrm{E}[\tilde\Theta] = 0$，且 $\mathrm{E}[\tilde\Theta \mid X = x] = 0$。
- $\mathrm{E}[\tilde\Theta\, h(X)] = 0$，对任意函数 $h$。
- $\mathrm{cov}(\tilde\Theta, \hat\Theta) = 0$。
- 由 $\Theta = \hat\Theta - \tilde\Theta$：
```math
\mathrm{var}(\Theta) = \mathrm{var}(\hat\Theta) + \mathrm{var}(\tilde\Theta) .
```

> <span style="color:#7f8c8d;">Bertsekas §8.3, p.434–436</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 跨课程连接）:**</span> 这五条性质有一个统一的几何读法——**正交性**。验证第三条：$\mathrm{E}[\tilde\Theta\, h(X)] = \mathrm{E}\bigl[\mathrm{E}[\tilde\Theta \mid X]\, h(X)\bigr] = \mathrm{E}[0 \cdot h(X)] = 0$ ✓，中间一步再次动用重期望法则（pp. 225–226）；取 $h = \hat\Theta$（$\hat\Theta$ 是 $X$ 的函数）立刻得 $\mathrm{cov}(\tilde\Theta, \hat\Theta) = \mathrm{E}[\tilde\Theta \hat\Theta] - 0 = 0$ ✓；方差分解 $\mathrm{var}(\Theta) = \mathrm{var}(\hat\Theta) + \mathrm{var}(\tilde\Theta)$ 是协方差为零时的勾股式展开 ✓。跨课程连接：用 Strang 线性代数的语言说，$\hat\Theta = \mathrm{E}[\Theta \mid X]$ 是把 $\Theta$ 正交投影到"$X$ 的一切函数"所张成的空间上，$\mathrm{E}[\tilde\Theta h(X)] = 0$ 正是投影正交方程 $A^{\mathrm T} e = 0$ 的概率化身——误差与投影方向的每一个方向都"垂直"。教材 p.436 顺带处理了一个诊断问题：观测 $X$ 何时毫无信息？答案：当且仅当 $\mathrm{var}(\tilde\Theta) = 0$，即 $\mathrm{E}[\Theta \mid X = x]$ 对每个 $x$ 都等于 $\mathrm{E}[\Theta]$；教材还提醒逆命题不真——$\mathrm{E}[\Theta \mid X = x]$ 恒为常数并不意味着 $\Theta$ 与 $X$ 独立，并留了构造反例的练习。卡点预警：$\tilde\Theta$ 的符号约定（这里是估计减真值）不影响任何结论，换个教材读到相反定义时不必慌。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Linear LMS（线性 LMS）</span>

- 考虑形如 $\hat\Theta = aX + b$ 的估计器。
- 最小化 $\mathrm{E}[(\Theta - aX - b)^2]$。
- $a, b$ 的最优选择；最优线性估计器（best linear estimator）：
```math
\hat\Theta_L = \mathrm{E}[\Theta] + \frac{\mathrm{Cov}(X, \Theta)}{\mathrm{var}(X)}\,\bigl(X - \mathrm{E}[X]\bigr) .
```

> <span style="color:#7f8c8d;">Bertsekas §8.4, p.437–438</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Linear LMS properties（线性 LMS 的性质）</span>

```math
\mathrm{E}\bigl[(\hat\Theta_L - \Theta)^2\bigr] = (1 - \rho^2)\,\sigma_\Theta^2 .
```

> <span style="color:#7f8c8d;">Bertsekas §8.4, p.438–439</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 把教材 p.437–438 的推导完整走一遍当验算。第一步选 $b$：固定 $a$ 后，选 $b$ 等价于用常数估计随机变量 $\Theta - aX$，而"常数最优估计是均值"给出 $b = \mathrm{E}[\Theta - aX] = \mathrm{E}[\Theta] - a\,\mathrm{E}[X]$ ✓（p.438）。第二步选 $a$：此时目标只剩 $\mathrm{var}(\Theta - aX) = \sigma_\Theta^2 + a^2 \sigma_X^2 - 2a\,\mathrm{cov}(\Theta, X)$，对 $a$ 求导置零得 $a = \dfrac{\mathrm{cov}(\Theta, X)}{\sigma_X^2} = \rho\,\dfrac{\sigma_\Theta}{\sigma_X}$，其中 $\rho = \dfrac{\mathrm{cov}(\Theta, X)}{\sigma_\Theta \sigma_X}$ 是 correlation coefficient（相关系数）✓。第三步代回算代价：$a^2\sigma_X^2 = \rho^2 \sigma_\Theta^2$、$2a\,\mathrm{cov} = 2\rho^2\sigma_\Theta^2$，合并得 $\mathrm{E}[(\hat\Theta_L - \Theta)^2] = (1 - \rho^2)\sigma_\Theta^2$ ✓。两个极端做体检：$\rho = 0$ 时 MSE $= \sigma_\Theta^2$，估计器退化为常数 $\mathrm{E}[\Theta]$——不相关的数据榨不出线性信息；$|\rho| = 1$ 时 MSE $= 0$——$\Theta$ 与 $X$ 有严格线性关系，被 $a, b$ 一网打尽。卡点预警：$\rho = 0$ 只宣判"线性 LMS 无能为力"，不宣判 $\mathrm{E}[\Theta \mid X] = \mathrm{E}[\Theta]$——非线性依赖仍可能被通用 LMS 利用，这正是后面 Choosing $X_i$ 一页的伏笔。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Linear LMS with multiple data（多观测数据的线性 LMS）</span>

- 考虑形如下式的估计器：
```math
\hat\Theta = a_1 X_1 + \cdots + a_n X_n + b .
```
- 找出 $a_1, \ldots, a_n, b$ 的最优选择；最小化：
```math
\mathrm{E}\bigl[(a_1 X_1 + \cdots + a_n X_n + b - \Theta)^2\bigr] .
```
- 令各导数为零——得到关于 $b$ 与各 $a_i$ 的 linear system（线性方程组）。
- 只有 means（均值）、variances（方差）、covariances（协方差）起作用。

> <span style="color:#7f8c8d;">Bertsekas §8.4, p.439–441</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 跨课程连接）:**</span> 命名模板——**"导数置零得正规方程"**：目标函数是 $(a_1, \ldots, a_n, b)$ 的凸二次型，梯度为零既是必要也是充分条件，求导产出的恰是一个线性方程组。跨课程连接：这与 Strang 线性代数里的 normal equations（正规方程）$A^{\mathrm T}A\hat\theta = A^{\mathrm T}y$ 同构——那里是"拟合直线的残差正交于列空间的每一列"，这里是"估计误差 $\tilde\Theta$ 与每个观测 $X_i$ 正交"（$\mathrm{E}[\tilde\Theta X_i] = 0$），同一枚硬币的代数面与概率面。教材 pp.436–437 补了两笔：其一，多参数 $\Theta_1, \ldots, \Theta_m$ 时目标按参数解耦，每个参数各自 $\mathrm{E}[\Theta_i \mid X_1, \ldots, X_n]$，互不纠缠；其二，"只有前二阶矩起作用"意味着——把模型换成均值、方差、协方差完全相同的另一个模型，线性 LMS 的答案纹丝不动。这正是它的双重性格：信息被压缩到二阶矩层面，所以便宜（不用完整联合分布）、可移植，也因此上限低于通用 LMS。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The cleanest linear LMS example（最干净的线性 LMS 例子）</span>

- $X_i = \Theta + W_i$，其中 $\Theta, W_1, \ldots, W_n$ 相互 independent（独立）；
- $\Theta \sim (\mu, \sigma_0^2)$，$W_i \sim (0, \sigma_i^2)$：
```math
\hat\Theta_L = \frac{\mu/\sigma_0^2 + \sum_{i=1}^{n} X_i/\sigma_i^2}{\sum_{i=0}^{n} 1/\sigma_i^2}
```
  （$\mu, X_1, \ldots, X_n$ 的 weighted average（加权平均））。
- 若全部分布都是 normal（正态）的，则 $\hat\Theta_L = \mathrm{E}[\Theta \mid X_1, \ldots, X_n]$。

> <span style="color:#7f8c8d;">Bertsekas §8.4, p.442</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 用 $n = 1$ 验算加权平均公式：$\mathrm{cov}(\Theta, X_1) = \mathrm{cov}(\Theta, \Theta + W_1) = \sigma_0^2$，$\mathrm{var}(X_1) = \sigma_0^2 + \sigma_1^2$，代入线性 LMS 公式得 $\hat\Theta_L = \mu + \frac{\sigma_0^2}{\sigma_0^2 + \sigma_1^2}(X_1 - \mu) = \frac{\mu\,\sigma_1^2 + X_1\,\sigma_0^2}{\sigma_0^2 + \sigma_1^2} = \frac{\mu/\sigma_1^2 + X_1/\sigma_0^2}{1/\sigma_1^2 + 1/\sigma_0^2}$ ✓——与幻灯片的精度加权形式完全一致。权重 $1/\sigma_i^2$ 是 precision（精度）：第 $i$ 个传感器噪声方差越大、权重越小，"按可靠性加权融合信息"就是这页幻灯片的一切。跨课程连接：正态情形下 $\hat\Theta_L$ 恰好等于真后验均值 $\mathrm{E}[\Theta \mid X_1, \ldots, X_n]$，因为正态先验与正态似然是共轭搭档（教材 Example 8.3 的 common mean 例，p.415 起即此模型）。这一"旧估计与新测量按精度加权"的更新结构，在信号处理里被递归化就成了 Kalman filter（卡尔曼滤波器）——脚手架式一句话：把每次更新读作"先验提供旧估计、新观测提供似然、按各自精度分配权重、递归进行"，就是滤波的全部灵魂； Lec 25 收尾幻灯片说的 "efficient and recursive signal processing" 指的正是这一路。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Choosing Xi in linear LMS（线性 LMS 中观测量的选择）</span>

- $\mathrm{E}[\Theta \mid X]$ 与 $\mathrm{E}[\Theta \mid X^3]$ 相同。
- Linear LMS 则不同：
  - $\hat\Theta = aX + b$ 与 $\hat\Theta = aX^3 + b$ 不一样；
  - 也可考虑 $\hat\Theta = a_1 X + a_2 X^2 + a_3 X^3 + b$。

> <span style="color:#7f8c8d;">Bertsekas §8.4, p.437–443</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 为什么 $\mathrm{E}[\Theta \mid X] = \mathrm{E}[\Theta \mid X^3]$？回到第一性原理：条件期望只依赖"观测能分辨哪些事件"。$x \mapsto x^3$ 是严格单调的一一映射，知道 $X$ 与知道 $X^3$ 是同一份信息——对每个 $x$ 都能唯一反解。用 6.042J 的 partition（划分）视角说：条件化就是按观测值给样本空间切格子，"按 $X$ 切"与"按 $X^3$ 切"切出完全相同的格子，条件期望当然相同。线性 LMS 却没有这种不变性：它只在 $\mathrm{span}\{1, X\}$ 里挑最优，把数据换成 $X^3$ 后张成的空间变了，答案自然不同。卡点诊断：这暴露了两者的本质差别——通用 LMS 在"$X$ 的一切函数"这个大空间里自动搜索，线性 LMS 只在你提供的特征张成的小空间里搜索；想让它看见非线性结构，就得自己把 $X, X^2, X^3$ 一起喂进去（幻灯片最后一行）。工程教训："选观测、造特征"从后台细节变成了前台决策——现代机器学习管这叫特征工程，逻辑起点就是这一页。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Big picture（全局图景）</span>

- **标准例子**（standard examples）：
  - $X_i$ 在 $[0, \theta]$ 上 uniform（均匀分布）；对 $\theta$ 取 uniform prior（均匀先验）。
  - $X_i \sim \mathrm{Bernoulli}(p)$（伯努利）；对 $p$ 取 uniform（或 Beta）先验。
  - $X_i$ 服从均值 $\theta$、已知方差 $\sigma^2$ 的 normal（正态分布）；对 $\theta$ 取正态先验；模型为 $X_i = \Theta + W_i$。
- **估计方法**（estimation methods）：
  - MAP。
  - LMS。
  - 线性 LMS。

> <span style="color:#7f8c8d;">Bertsekas §8.1–8.2, p.412–429；§8.5, p.444–445</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 收束页把第 8 章的骨架一次摆齐。三个标准例子各是一台样例机：均匀先验 + 均匀观测是 §8.1 里手工计算后验的样板；伯努利 + Beta 先验是教材 Example 8.4（p.417 起）——Beta 先验与伯努利似然共轭，后验仍是 Beta，"先验吸收数据后形状不变"；正态-正态是 Example 8.3（p.415 起）——本讲最干净例子的原型。三种方法的选型逻辑也值得默记：能维护完整后验时用 LMS（均方最优，$\mathrm{E}[\Theta \mid X]$）；只掌握均值方差协方差、或后验难算时用线性 LMS（便宜、稳健、二阶矩就够）；需要"最可能的单值"做硬判定时用 MAP（上一讲的遗产）。至此 Bayesian statistical inference（贝叶斯统计推断）一章收束（教材 §8.5 总结在 pp. 444–445）；下一讲起切换到 classical statistics（经典统计）——同样的问题，换一副"$\theta$ 不是随机变量"的眼镜，评价标准也从后验最优变成对一切 $\theta$ 的一致优异。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
