# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 21 — Bayesian Statistical Inference I（贝叶斯统计推断 I）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Sample applications（样本应用与开场）</span>

**阅读（Readings）**：教材 Sections 8.1–8.2。

> "It is the mark of truly educated people to be deeply moved by statistics."
> （"真正有教养的人的标志，是能被统计数字深深打动。"——Oscar Wilde 王尔德）

**样本应用（Sample applications）**：
- 民调（Polling）：
  - 实验/抽样设计（design of experiments/sampling）。
  - 柳叶刀关于伊拉克死亡人数的研究（Lancet study on Iraq death toll）。
- 医学/药物试验（Medical/pharmaceutical trials）。
- 数据挖掘（Data mining）——Netflix 竞赛（Netflix competition）。
- 金融（Finance）。
- 实验的设计与解读（Design &amp; interpretation of experiments）——民调、医学/药物试验等。
- 信号处理（Signal processing）——跟踪、检测、说话人识别等（tracking, detection, speaker identification, …）。

> <span style="color:#7f8c8d;">Bertsekas 第 8 章引言，p.407–408</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲是全书最后一座大山——统计推断——的入口。教材第 8 章开篇（p.407–408）先划清学科边界：概率论是自洽的演绎系统，模型给定后任何清晰的问题都有唯一正确答案；统计学则"involves an element of art"，同一份数据可以有多种合理方法、给出不同答案，没有无条件"最好"的方法。这门课把推断分成两大门派——贝叶斯（把未知量当随机变量、注入先验）与经典（把未知量当固定常数），本章主攻贝叶斯，经典派留给教材第 9 章。大纲上六类应用值得扫一遍：民调与医学试验是"设计实验 + 估计比例"，Netflix 矩阵补全是"稀疏观测下预测缺失值"，金融是"从历史回报推断模型"，信号处理是"噪声中恢复信号"——它们都会在本讲与下一讲化作同一个数学形状：未知量 $\Theta$ + 观测 $X$ + 后验分布。王尔德那句俏皮话是全课程的压轴注脚：这门课教会你的不只是算概率，更是**被数据打动的能力**。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">From reality to model（从现实到模型）</span>

> <span style="color:#7f8c8d;">图：现实（Reality，如顾客到达 customer arrivals）$\to$ 模型（Model，如泊松过程 Poisson）；矩阵补全（Matrix Completion，Netflix 竞赛）：部分观测的矩阵，目标是预测未观测条目；传感器（sensors）：未知位置的目标物与传感器测量；S&amp;P 500 指数曲线（因版权原因移除）；跟踪模型：$Z_t = \Theta_0 + t\Theta_1 + t^2\Theta_2$，$X_t = Z_t + W_t$，$t = 1, \ldots, n$。</span>

> <span style="color:#7f8c8d;">Bertsekas §8.1, p.412–413</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Types of inference（推断的类型与两大门派）</span>

- **建模 vs 推断未知变量**（model building versus inferring unknown variables）。例：设 $X = aS + W$——
  - 模型构建（model building）：方法论。已知"信号" $S$，观测 $X$，推断 $a$。
  - 噪声中的估计（estimation in the presence of noise）：已知 $a$，观测 $X$，估计 $S$。
- **假设检验**（hypothesis testing）：未知量只取少数几个可能值；目标是让错误决策的概率小。

> <span style="color:#7f8c8d;">图：$\Theta \in \{0, 1\}$，观测 $X = \Theta + W$（$W \sim f_W$），由估计器（estimator）输出 $\hat{\Theta}$。</span>

- **估计**（estimation）：目标是让估计误差小。
- **经典统计学**（classical statistics）：$\theta$ 是未知参数（**不是**随机变量）。例：$\theta$ = 电子的质量。
- **贝叶斯**（Bayesian）：使用先验（priors）与贝叶斯法则（Bayes rule）。

> <span style="color:#7f8c8d;">Bertsekas 第 8 章引言，p.408</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 前后讲回指）:**</span> 卡点：贝叶斯派与经典派的分歧到底在哪？答案是**未知量的本体论地位**——教材 p.408 的原话：贝叶斯派把未知模型/变量当作"random variables with known distributions"，经典派把它当作待估的固定常数（电子质量不会每天变，凭什么给它配分布？）。回指：其实你在 Lec 02–03 早已是贝叶斯派的徒孙——那时解"测试呈阳性，真患病概率"就用贝叶斯法则把"患病/健康"当带先验的随机假设处理；本讲只是把那个二值假设升级为一般随机变量 $\Theta$，把单次观测升级为观测向量。图中 $\Theta \in \{0, 1\}$、$X = \Theta + W$ 的设定正是 Lec 03 判决问题的连续版：假设检验 = 少数候选假设间做选择（管错误概率），估计 = 连续参数给单值（管误差大小），两者共享"观测 + 估计器"的管道结构。经典派的方法（最大似然、置信区间）在教材第 9 章——先学好贝叶斯这把"带先验的瑞士军刀"，届时对比才有手感。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Bayesian inference: Use Bayes rule（贝叶斯推断：运用贝叶斯法则）</span>

- **假设检验**：
  - 离散数据：
```math
p_{\Theta|X}(\theta \mid x) = \frac{p_\Theta(\theta)\, p_{X|\Theta}(x \mid \theta)}{p_X(x)}
```
  - 连续数据：
```math
p_{\Theta|X}(\theta \mid x) = \frac{p_\Theta(\theta)\, f_{X|\Theta}(x \mid \theta)}{f_X(x)}
```
- **估计**；连续数据：
```math
f_{\Theta|X}(\theta \mid x) = \frac{f_\Theta(\theta)\, f_{X|\Theta}(x \mid \theta)}{f_X(x)}
```
- 跟踪例：$Z_t = \Theta_0 + t\Theta_1 + t^2\Theta_2$，$X_t = Z_t + W_t$，$t = 1, 2, \ldots, n$。贝叶斯法则给出：
```math
f_{\Theta_0,\Theta_1,\Theta_2 \mid X_1,\ldots,X_n}(\theta_0, \theta_1, \theta_2 \mid x_1, \ldots, x_n)
```

> <span style="color:#7f8c8d;">Bertsekas §8.1, p.413</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 幻灯片上三个公式其实是同一个贝叶斯法则的变装，教材 p.413 的"The Four Versions of Bayes' Rule"框把它们配齐成 $2 \times 2$ 矩阵：$\Theta$ 离散/连续 × $X$ 离散/连续——变装规则只有两条，PMF 换 PDF、求和 $\sum$ 换积分 $\int$，语法完全平行（p.413 原话：syntax 上只需这两处替换）。第一性原理的读法：后验 = 先验 × 似然 ÷ 归一化常数——$p_\Theta(\theta)$ 是观测前你对各 $\theta$ 的下注，$p_{X|\Theta}(x \mid \theta)$ 是"若 $\theta$ 为真、看到数据 $x$ 的可能性"（似然，likelihood），两者相乘再整体归一，就把下注重排成观测后的信念。分母 $p_X(x) = \sum_\theta$ 或 $\int \cdots$ 只是个常数（不依赖 $\theta$），作用是让后验积/和为 1——下一页会看到它用全概率定理计算。跟踪例展示了公式的伸缩性：三维参数 $(\Theta_0, \Theta_1, \Theta_2)$ 对应二次轨迹的截距、斜率、曲率，$n$ 次带噪观测 $X_t$ 灌进同一个公式，输出的是三维联合后验 PDF——公式不变，维度照升。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Estimation with discrete data（离散数据的估计）</span>

```math
f_{\Theta|X}(\theta \mid x) = \frac{f_\Theta(\theta)\, p_{X|\Theta}(x \mid \theta)}{p_X(x)}, \qquad p_X(x) = \int f_\Theta(\theta)\, p_{X|\Theta}(x \mid \theta)\, d\theta
```
- **例**：参数 $\theta$ 未知的硬币（coin with unknown parameter $\theta$）——掷 $n$ 次观测到 $X$ 次正面。
- **贝叶斯方法怎么做？**
  - 想求 $f_{\Theta|X}(\theta \mid x)$；
  - 给 $\Theta$ 设一个先验（prior on $\Theta$，例如均匀先验 uniform prior）。

> <span style="color:#7f8c8d;">图：先验 $f_\Theta(\theta) = 1/6$（$\theta \in [4, 10]$ 上的均匀密度）；目标物位置未知，各传感器在与其距离不超过 1 时"感知"目标，观测 $Y = X + W$（$W \sim f_W$ 为噪声）。</span>

> <span style="color:#7f8c8d;">Bertsekas §8.1, p.413–417</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 把硬币例算到底：先验取 $[0, 1]$ 均匀，$n$ 次独立投掷 $X$ 次正面，似然 $p_{X|\Theta}(x \mid \theta) \propto \theta^x (1 - \theta)^{n - x}$，代入贝叶斯法则得后验 $f_{\Theta|X}(\theta \mid x) \propto \theta^x (1 - \theta)^{n - x}$（$\theta \in [0,1]$）。验证归一化：$\int_0^1 \theta^x (1-\theta)^{n-x} d\theta = \frac{x!\,(n-x)!}{(n+1)!}$，用 $n = 1, x = 1$ 核对：$\int_0^1 \theta\, d\theta = 1/2 = \frac{1!\,0!}{2!}$ ✓。故后验为 $(n+1)\binom{n}{x}\theta^x (1-\theta)^{n-x}$——Beta 分布形状，教材在 §8.2（p.424–425）对同款硬币问题算出 MAP 估计 $\theta^* = x/n$。传感器例的先验 $f_\Theta = 1/6$（$[4,10]$ 均匀）与观测 $Y = X + W$ 正是教材 Example 8.8（p.431–432）的场景：$p_Y(y) = \int f_\Theta(\theta) f_W(y - \theta)\, d\theta$ 是一次卷积——此前处理独立随机变量之和时已见过同一操作，只是这里按"先验 $\times$ 噪声"的语义重新解读。卡点：先验是"注入的信念"，不同先验给出不同后验——均匀先验并非"无信息"的免罪金牌，选它也要给理由。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Output of Bayesian Inference（贝叶斯推断的输出）</span>

- **后验分布**（posterior distribution）：
  - pmf $p_{\Theta|X}(\cdot \mid x)$ 或 pdf $f_{\Theta|X}(\cdot \mid x)$。
- 若只想要**单一答案**（single answer）：
  - **最大后验概率准则**（MAP，maximum a posteriori probability）：
```math
p_{\Theta|X}(\theta^* \mid x) = \max_{\theta}\, p_{\Theta|X}(\theta \mid x)
```
    最小化出错概率（minimizes probability of error）；常用于假设检验。连续版：$f_{\Theta|X}(\theta^* \mid x) = \max_\theta f_{\Theta|X}(\theta \mid x)$。
  - 条件期望（conditional expectation）：
```math
\mathrm{E}[\Theta \mid X = x] = \int \theta\, f_{\Theta|X}(\theta \mid x)\, d\theta
```
  - **单一答案可能产生误导**（Single answers can be misleading!）。

> <span style="color:#7f8c8d;">Bertsekas §8.2, p.420–422</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 验证）:**</span> 卡点：既然后验已是"完整答案"，为什么还要挑单一估计？因为行动只需要一个数，而**压缩必有损失**——幻灯片末行"Single answers can be misleading"正是对这种损失的警告：设想后验在 $\theta = 2$ 与 $\theta = 10$ 处双峰，条件期望落在 6 附近——一个后验认为几乎不可能的值；此时 MAP 至少落在真实峰上。两条选择路线的优劣各有所本：MAP 在 $\Theta$ 只取有限个值时**最小化出错概率**（对无条件与条件错误概率都成立，教材 p.421 的 MAP 框明言），所以假设检验用它；条件期望则是均方误差意义下的最优选择（下一节证明），所以数值估计用它。验算一个小例：$\Theta \in \{0, 1\}$、后验 $p_{\Theta|X}(1 \mid x) = 0.6$ 时，MAP 判 $\hat\Theta = 1$，出错概率 $0.4$，确实小于判 0 的 $0.6$ ✓；而条件期望 $0.6$ 根本不在假设空间里——它不是"答案"，是"平均"。先问损失结构，再选估计器，这是本页的方法论。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Least Mean Squares Estimation（最小均方估计）</span>

- **无信息时的估计**（estimation in the absence of information）：求估计值 $c$，使
```math
\mathrm{E}\big[(\Theta - c)^2\big]
```
  最小。
- **最优估计**：$c = \mathrm{E}[\Theta]$。
- **最优均方误差**：
```math
\mathrm{E}\big[(\Theta - \mathrm{E}[\Theta])^2\big] = \mathrm{Var}(\Theta)
```

> <span style="color:#7f8c8d;">Bertsekas §8.3, p.430–431</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 证明只需一行配方，值得亲手做：$\mathrm{E}[(\Theta - c)^2] = \mathrm{E}[(\Theta - \mu)^2 + 2(\mu - c)(\Theta - \mu) + (\mu - c)^2]$（$\mu = \mathrm{E}[\Theta]$），交叉项是常数乘 $\mathrm{E}[\Theta - \mu] = 0$，于是 $= \mathrm{Var}(\Theta) + (\mu - c)^2 \ge \mathrm{Var}(\Theta)$ ✓，等号当且仅当 $c = \mu$。教材 p.431 的 Key Facts 框第一條即此。它顺带回答了一个老问题：方差为什么叫"方差"——它就是"用均值去猜 $\Theta$"这一最朴素策略的最好平方误差，任何别的常数猜法都更差。更深一层：平方损失不是唯一选择（绝对值损失会把你引向中位数），但平方损失可微、可分解、与高斯噪声天然配套，于是成为默认选项。跨课程连接：这与 Strang 线性代数里的最小二乘是同一思想的连续版——在一族候选里找"离目标平方距离最近"的成员；下一页把"候选常数 $c$"换成"观测的函数 $g(X)$"，配方法会在条件宇宙里原样重演。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">LMS Estimation of $\Theta$ based on $X$（基于 $X$ 的 LMS 估计）</span>

- 两个随机变量 $\Theta$、$X$；观测到 $X = x$。
  - **新的宇宙**（new universe）：以 $X = x$ 为条件。
- $\mathrm{E}\big[(\Theta - c)^2 \,\big|\, X = x\big]$ 在下式处最小：
```math
c = \mathrm{E}[\Theta \mid X = x]
```
- 于是对任意函数 $g$：
```math
\mathrm{E}\big[(\Theta - \mathrm{E}[\Theta \mid X = x])^2 \,\big|\, X = x\big] \;\le\; \mathrm{E}\big[(\Theta - g(x))^2 \,\big|\, X = x\big]
```
- 进而：
```math
\mathrm{E}\big[(\Theta - \mathrm{E}[\Theta \mid X])^2 \,\big|\, X\big] \le \mathrm{E}\big[(\Theta - g(X))^2 \,\big|\, X\big], \qquad \mathrm{E}\big[(\Theta - \mathrm{E}[\Theta \mid X])^2\big] \le \mathrm{E}\big[(\Theta - g(X))^2\big]
```
- 即：在所有估计器 $g(\cdot)$ 中，$\mathrm{E}[\Theta \mid X]$ 最小化 $\mathrm{E}\big[(\Theta - g(X))^2\big]$。

> <span style="color:#7f8c8d;">Bertsekas §8.3, p.430–431</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 跨课程连接）:**</span> 这一页的推理链是"条件化降维"的标准示范：给定 $X = x$ 后，一切都在条件宇宙里发生，上一页的配方法逐字重演——常数 $c$ 换成 $\mathrm{E}[\Theta \mid X = x]$，方差换成条件方差——于是教材 p.431 Key Facts 框的第二条到手 ✓。真正的妙步在最后两行：对每个固定的 $x$ 成立的不等式，两边恰是 $X$ 的函数，直接取期望再用重期望法则（law of iterated expectations，教材 p.431 脚注正是这么做的），就升格为无条件不等式——**逐点成立 $\to$ 取期望 $\to$ 全局成立**，这个三步模板在概率论里反复出现。卡点：$\mathrm{E}[\Theta \mid X]$ 是随机变量（$X$ 的函数），别与数 $\mathrm{E}[\Theta \mid X = x]$ 混写；"最优估计器"的"最优"是均方误差意义下的，换损失函数结论会变。跨课程连接：用 Strang 的几何语言，$\{\text{所有 } g(X)\}$ 构成"观测的函数"空间，$\mathrm{E}[\Theta|X]$ 是 $\Theta$ 在该空间上的投影——最小二乘投影 $\hat{x} = A(A^TA)^{-1}A^Tb$ 与这里是同一个"最近点"骨架，只是内积换成了期望意义。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">LMS Estimation with several measurements（多观测下的 LMS 估计）</span>

- 未知随机变量 $\Theta$。
- 观测随机变量 $X_1, \ldots, X_n$ 的取值。
- **最优估计器**：
```math
\mathrm{E}[\Theta \mid X_1, \ldots, X_n]
```
- 可能难以计算/实现——涉及多维积分等（multi-dimensional integrals）。

> <span style="color:#7f8c8d;">Bertsekas §8.3, p.430–434</span>

> <span style="color:#1e8449;">**[note] Note（译者注，跨课程连接 + 前后讲回指）:**</span> 理论上多观测毫无新意：把条件化从 $X = x$ 换成向量 $(X_1, \ldots, X_n) = (x_1, \ldots, x_n)$，最优估计器仍是条件期望——教材 p.431 的第三条 Key Facts 就是这个一般形态，p.433–434 还给出多观测版的展开。实践上却是另一回事：后验要用 $n$ 维联合密度对 $n-1$ 维积分归一化，维度一高，"写出并算出积分"迅速失控——幻灯片"hard to compute/implement"是对工程现实的坦白。回指：Lec 07 处理多个**离散**随机变量时，联合分布列是张表格、求和是有限循环，多维不算障碍；如今换成连续变量，表格变成 $n$ 维连续体，同样的语法（$\sum \to \int$）背后是指数级的计算代价。前瞻：下一讲的 Bayesian Linear LMS（教材 §8.4，p.437 起）干脆限制估计器为观测的**线性**函数 $g(X) = a_1 X_1 + \cdots + a_n X_n + b$——最优系数只需解线性方程组，绕开一切高维积分。这是贯穿工程数学的老智慧：宁可牺牲最优性，也要换来可计算性。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
