# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 24 — Classical Statistical Inference II（经典统计推断 II）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; review（本讲大纲与复习）</span>

**参考（Reference）**：教材 Section 9.3（二元假设检验）；本讲前半的线性回归对应 Section 9.2。课程评估（Course Evaluations）截至 12/16：http://web.mit.edu/subjectevaluation 。

**复习（Review）**：
- 极大似然估计（Maximum likelihood estimation）：
  - 模型带未知参数：$X \sim p_X(x;\theta)$；
  - 挑选"让数据最可能出现"的 $\theta$：$\max_\theta p_X(x;\theta)$；
  - 与贝叶斯 MAP 估计对比：$\max_\theta p_{\Theta|X}(\theta \mid x)$，或 $\max_\theta \dfrac{p_{X|\Theta}(x \mid \theta)\, p_\Theta(\theta)}{p_X(x)}$。
- 样本均值估计 $\theta = \mathrm{E}[X]$：$\hat\Theta_n = (X_1 + \cdots + X_n)/n$。
- $1 - \alpha$ 置信区间：$P(\hat\Theta_n^- \le \theta \le \hat\Theta_n^+) \ge 1 - \alpha$，$\forall\, \theta$。
- 样本均值的置信区间：设 $z$ 满足 $\Phi(z) = 1 - \alpha/2$，则 $P\bigl(\hat\Theta_n - \frac{z\sigma}{\sqrt n} \le \theta \le \hat\Theta_n + \frac{z\sigma}{\sqrt n}\bigr) \approx 1 - \alpha$。

**本讲大纲（Outline）**：
- 线性回归（Linear regression）。
- 二元假设检验（Binary hypothesis testing）：
  - 误差类型（Types of error）；
  - 似然比检验（Likelihood ratio test, LRT）。

> <span style="color:#7f8c8d;">Bertsekas §9.2, p.475–484；§9.3, p.485–494</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲是经典统计推断的"应用双联画"：前半用一条直线去拟合数据（回归），后半在两个假设之间做裁决（检验），两者共用"让数据最可能出现"的极大似然灵魂。Lec 23 的三件套在这里全部被复用：回归的解靠"导数置零"，其正态解释靠 MLE 与似然函数；LRT 是 MAP 法则去掉先验后的产物；置信区间思想日后还会出现在回归的成果报告里。从教材章目录看，§9.2 从 p.475 起、§9.3 从 p.485 起，本讲恰好横跨两节——讲义标注 "Reference: Section 9.3" 是因为后半的假设检验是新增概念，前半的回归则承接 Lec 23 的估计框架。回指 Lec 22 的线性 LMS：那边是"用 $X$ 线性预测 $\Theta$"，这边是"用 $x$ 线性预测 $y$"，斜率公式将在本讲后半重逢，请留意对照。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Regression（回归）</span>

- 数据：$(x_1, y_1), (x_2, y_2), \ldots, (x_n, y_n)$。
- 模型：$y \approx \theta_0 + \theta_1 x$；最小化残差平方和：
```math
\min_{\theta_0, \theta_1}\ \sum_{i=1}^{n} \bigl(y_i - \theta_0 - \theta_1 x_i\bigr)^2 .
```
- 一种解读：$Y_i = \theta_0 + \theta_1 x_i + W_i$，$W_i \sim \mathrm{N}(0, \sigma^2)$ i.i.d.：
  - 似然函数 $f_{X,Y \mid \theta}(x, y; \theta)$ 为 $c \cdot \exp\bigl\{-\frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - \theta_0 - \theta_1 x_i)^2\bigr\}$；
  - 取对数，与上式相同（$\ast$）；
  - 最小二乘 $\iff$ 假装 $W_i$ 是 i.i.d. 正态。

> <span style="color:#7f8c8d;">图：散点 $(x_i, y_i)$ 与拟合直线 $\hat y = \hat\theta_0 + \hat\theta_1 x$；第 $i$ 条 residual（残差）为竖直线段 $y_i - \hat\theta_0 - \hat\theta_1 x_i$，回归选取的正是使残差平方和最小的直线（对应教材 Fig. 9.5）。</span>

> <span style="color:#7f8c8d;">Bertsekas §9.2, p.475–484</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 教材 p.476 的展开可作本页注脚：以"受教育年限 $x$ 与年收入 $y$"为例，散点图常显出近似的线性关系，于是设 $y \approx \theta_0 + \theta_1 x$；模型的预测值 $\hat y_i = \hat\theta_0 + \hat\theta_1 x_i$ 与真值之差 $\tilde y_i = y_i - \hat y_i$ 就是 residual（残差），"残差小 = 拟合好"，于是最小化 $\sum_i (y_i - \theta_0 - \theta_1 x_i)^2$。"最小二乘 $\iff$ 假装噪声正态"值得验算一遍：若 $W_i$ i.i.d. $\mathrm{N}(0, \sigma^2)$，则似然为 $\prod_i \frac{1}{\sqrt{2\pi}\,\sigma}\exp\{-\frac{(y_i - \theta_0 - \theta_1 x_i)^2}{2\sigma^2}\}$，取对数后是 $-\frac{1}{2\sigma^2}\sum_i(\cdot)^2 + \text{常数}$——最大化似然与最小化平方和给出同一组 $(\hat\theta_0, \hat\theta_1)$ ✓。跨课程连接：这架"正态桥"是双向的——加正态假设把概率问题化成平方和问题（本页方向），反过来任何平方和目标都自动获得一个正态解释（于是最小二乘的答案总可被读作 MLE）；Strang 线代的最小二乘几何（把 $y$ 正交投影到列空间、残差垂直于拟合方向）正是无正态假设时的那半边故事。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Linear regression（线性回归）</span>

- 模型 $y \approx \theta_0 + \theta_1 x$；解（令导数为零）：
```math
\bar x = \frac{x_1 + \cdots + x_n}{n}, \qquad \bar y = \frac{y_1 + \cdots + y_n}{n},
```
```math
\hat\theta_1 = \frac{\sum_{i=1}^{n} (x_i - \bar x)(y_i - \bar y)}{\sum_{i=1}^{n} (x_i - \bar x)^2}, \qquad
\hat\theta_0 = \bar y - \hat\theta_1 \bar x .
```
- 解的形状之解读：
  - 假设模型 $Y = \theta_0 + \theta_1 X + W$，$W$ 与 $X$ independent（独立）、均值为零；
  - 验证：
```math
\theta_1 = \frac{\mathrm{cov}(X, Y)}{\mathrm{var}(X)} = \frac{\mathrm{E}\bigl[(X - \mathrm{E}[X])(Y - \mathrm{E}[Y])\bigr]}{\mathrm{E}\bigl[(X - \mathrm{E}[X])^2\bigr]} ;
```
  - $\hat\theta_1$ 的公式使用的正是 variance（方差）与 covariance（协方差）的 natural estimates（自然估计）。

> <span style="color:#7f8c8d;">Bertsekas §9.2, p.475–484</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验证斜率的概率公式：由 $Y = \theta_0 + \theta_1 X + W$ 且 $W$ 与 $X$ 独立、均值为零，$\mathrm{E}[(X - \mathrm{E}[X])(Y - \mathrm{E}[Y])] = \theta_1\,\mathrm{E}[(X - \mathrm{E}[X])^2] + \mathrm{E}[(X - \mathrm{E}[X])\,W] = \theta_1\,\mathrm{var}(X) + 0 = \theta_1\,\mathrm{var}(X)$ ✓——协方差里只装得下斜率，截距 $\theta_0$ 被中心化自动吸收。卡点诊断：所谓 natural estimates（自然估计）就是把总体矩换成样本矩——$\mathrm{cov}$ 换成 $\frac{1}{n}\sum_i (x_i - \bar x)(y_i - \bar y)$、$\mathrm{var}(X)$ 换成 $\frac{1}{n}\sum_i (x_i - \bar x)^2$，比值恰是 $\hat\theta_1$ 的最小二乘公式 ✓；换言之，回归斜率是"理论关系 $\theta_1 = \mathrm{cov}/\mathrm{var}$ 的矩估计"。跨课程连接：把本式与 Lec 22 的线性 LMS 斜率 $a = \mathrm{cov}(\Theta, X)/\mathrm{var}(X)$ 并排放看——完全同款！那边是"用 $X$ 线性估计 $\Theta$"，这边是"用 $X$ 线性解释 $Y$"，最小均方与最小二乘在斜率层面本是同一个公式。顺带一提，下一页"选对变量"里 $y \approx \theta_0 + \theta_1 h(x)$ 的想法，正是 Lec 22 "Choosing $X_i$"（喂 $X, X^2, X^3$）的回归版：换基不换法。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The world of linear regression（线性回归的世界）</span>

- 多元线性回归（Multiple linear regression）：
  - 数据：$(x_i, x_i', x_i'', y_i)$，$i = 1, \ldots, n$；
  - 模型：$y \approx \theta_0 + \theta x + \theta' x' + \theta'' x''$；
  - 形式化：
```math
\min_{\theta, \theta', \theta''}\ \sum_{i=1}^{n} \bigl(y_i - \theta_0 - \theta x_i - \theta' x_i' - \theta'' x_i''\bigr)^2 .
```
- 选对变量（Choosing the right variables）：
  - 模型 $y \approx \theta_0 + \theta_1 h(x)$，例如 $y \approx \theta_0 + \theta_1 x^2$；
  - 改用数据点 $(y_i, h(x_i))$；
  - 形式化：
```math
\min_{\theta}\ \sum_{i=1}^{n} \bigl(y_i - \theta_0 - \theta_1 h_1(x_i)\bigr)^2 .
```

> <span style="color:#7f8c8d;">Bertsekas §9.2, p.475–484</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The world of regression (ctd.)（回归的世界·续）</span>

- 实践中还会报告：
  - 各 $\theta_i$ 的置信区间（confidence intervals）；
  - "standard error"（标准误，$\sigma$ 的估计）；
  - $R^2$——"explanatory power"（解释力）的度量。
- 一些常见的担忧（common concerns）：
  - Heteroskedasticity（异方差性）。
  - Multicollinearity（多重共线性）。
  - 有时被滥用来断言 causal relations（因果关系）。
  - 等等。

> <span style="color:#7f8c8d;">Bertsekas §9.2, p.475–484</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 第一性原理）:**</span> 这两页是"交付清单 + 避坑指南"。交付清单逐项对应已学工具：各 $\theta_i$ 的置信区间——Lec 23 的 CI 机器直接开过来用；standard error 是噪声标准差 $\sigma$ 的估计，报告系数时"误差棒"多粗全看它；$R^2$ 度量"平方和被模型吃掉了多大比例"，越接近 1 解释力越强。避坑指南里最要紧的是最后一条：回归只能证明**关联**，不能证明**因果**——"受教育年限与收入正相关"的拟合背后，可能藏着同时驱动两者的遗漏变量（如家庭背景），把 $\hat\theta_1$ 读成"多读一年书带来多少收入"就是滥用；这正是 Lec 22 "选观测/选特征"的暗面——没进模型的变量不会自己消失，只会把偏差塞进进模型的系数里。异方差性（噪声方差随 $x$ 变化）会破坏"等方差正态"解读，多重共线性（解释变量彼此高度相关）会让各系数估计在彼此间来回摇摆、单个系数失真——诊断与补救属于后续统计课程，本讲只立"警示牌"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Binary hypothesis testing（二元假设检验）</span>

- 二元 $\theta$；新术语：
  - null hypothesis（原假设）$H_0$：$X \sim p_X(x; H_0)$（或 $f_X(x; H_0)$）；
  - alternative hypothesis（备择假设）$H_1$：$X \sim p_X(x; H_1)$（或 $f_X(x; H_1)$）。
- 把可能的数据向量空间做 partition（划分）：rejection region（拒绝域）$R$——当且仅当数据 $\in R$ 时拒绝 $H_0$。
- 误差类型（Types of error）：
  - Type I（false rejection，错误拒绝；false alarm，虚警）：$H_0$ 为真却被拒绝——
```math
\alpha(R) = P(X \in R \,;\ H_0) ;
```
  - Type II（false acceptance，错误接受；missed detection，漏检）：$H_0$ 为假却被接受——
```math
\beta(R) = P(X \notin R \,;\ H_1) .
```

> <span style="color:#7f8c8d;">Bertsekas §9.3, p.485–494</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 假设检验的第一性原理：一切规则都归结为"在数据空间里画一块拒绝域 $R$"，之后所有性能指标都是 $R$ 的函数。两类错误天生此消彼长：把 $R$ 圈得越大，$H_0$ 为真时越容易误伤（$\alpha$ 升），$H_1$ 为真时越难漏检（$\beta$ 降）；把 $R$ 缩小则反向。卡点诊断：注意分号——$\alpha(R) = P(X \in R; H_0)$ 是"在 $H_0$ 对应的模型下"取概率，不是条件概率（$H_0$ 不是随机事件，承接 Lec 23 开篇的世界观）；分号就是经典统计给"按哪个模型算"立的规矩。回指：贝叶斯检测（Lec 21 的 MAP 法则与传感器例）里同样有 $P(\text{false alarm})$ 与 $P(\text{miss})$ 两个错误概率，但那边允许给两个假设配先验、按后验大小裁决，且目标是平均错误概率最小；这边不设先验，改为"控制第一类错误 + 尽量压第二类"的不对称策略——先保住"不冤枉 $H_0$"，再在预算内增强检出力。这一不对称在下一页变成对阈值 $\xi$ 的具体选法。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Likelihood ratio test (LRT)（似然比检验）</span>

- 贝叶斯情形（MAP 法则）：当满足下列任一等价条件时选择 $H_1$：
```math
P(H_1 \mid X = x) > P(H_0 \mid X = x),
```
```math
\Longleftrightarrow\ P(X = x \mid H_1)\, P(H_1) > P(X = x \mid H_0)\, P(H_0)
\ \Longleftrightarrow\
\frac{P(X = x \mid H_1)}{P(X = x \mid H_0)} > \frac{P(H_0)}{P(H_1)}
\quad \text{（likelihood ratio test，似然比检验）}.
```
- 非贝叶斯版本：当
```math
\frac{P(X = x;\, H_1)}{P(X = x;\, H_0)} > \xi \ \text{（离散情形）},
\qquad
\frac{f_X(x;\, H_1)}{f_X(x;\, H_0)} > \xi \ \text{（连续情形）}
```
  时选择 $H_1$。
- 阈值 $\xi$ 在两类误差之间做 tradeoff（权衡）：
  - 选 $\xi$ 使得 $P(\text{reject } H_0\,;\ H_0) = \alpha$（如 $\alpha = 0.05$）。

> <span style="color:#7f8c8d;">Bertsekas §9.3, p.485–494</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 把 MAP 到 LRT 的推导链完整验算一遍：$P(H_1 \mid X = x) > P(H_0 \mid X = x)$ 两边除以 $P(X = x)$ 并展开贝叶斯法则（Lec 02 的老规矩），得 $P(X = x \mid H_1)P(H_1) > P(X = x \mid H_0)P(H_0)$；再两边同除以 $P(X = x \mid H_0)P(H_1)$，先验被搬到了阈值里：$\frac{P(X = x \mid H_1)}{P(X = x \mid H_0)} > \frac{P(H_0)}{P(H_1)}$ ✓——似然比（数据说了什么）与先验比（出发时信什么）分居不等号两侧，结构一目了然。非贝叶斯版的"去先验化"动作：既然 $\theta$ 不是随机变量、没有 $P(H_i)$ 可言，就把阈值换成自由参数 $\xi$，事后按"控制 $\alpha$"来标定。命名模板——**"似然比拍板法"**：无论数据维度多高，先把全部证据压缩成一个数（两模型下数据概率之比），再与阈值比较；Lec 25 的所有检验例都将跑这条流水线。卡点预警：阈值 $\xi$ 的标定方向是"$P(\text{reject}\,;\,H_0) = \alpha$"——固定冤枉好人的概率，再看漏检率 $\beta$ 还剩多少；两类错误由同一个 $\xi$ 联动，不存在同时最小化两者的免费午餐。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
