# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 23 — Classical Statistical Inference I（经典统计推断 I）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Classical statistics（经典统计）</span>

**阅读（Readings）**：教材 Section 9.1（其中 pp. 471–473 的 t-based confidence intervals，t 置信区间，不列入考核）。

**本讲大纲（Outline）**：
- 经典统计（Classical statistics）。
- 极大似然（Maximum likelihood, ML）估计。
- 估计一个样本均值（Estimating a sample mean）。
- 置信区间（Confidence intervals, CIs）。
- 用估计出的方差构造置信区间（CIs using an estimated variance）。

**经典统计的世界观**：观测模型 $X \sim p_X(x;\theta)$，$\theta$ 未知但**不是**随机变量（对向量同样适用：$p_{X_1,\ldots,X_n}(x_1,\ldots,x_n;\,\theta_1,\ldots,\theta_m)$）。
- 这些**不是** conditional probabilities（条件概率）；$\theta$ 不是随机的。
- 数学上：**许多个模型**（many models），每个可能的 $\theta$ 值对应一个。

**题型（Problem types）**：
- 假设检验（Hypothesis testing）：$H_0: \theta = 1/2$ 对 $H_1: \theta = 3/4$。
- 复合假设（Composite hypotheses）：$H_0: \theta = 1/2$ 对 $H_1: \theta \ne 1/2$。
- 估计（Estimation）：设计估计器 $\hat\Theta$，使估计误差 $\hat\Theta - \theta$ 保持很小。

> <span style="color:#7f8c8d;">图：仍是贝叶斯推断那幅场景图（$\Theta \in \{0,1\}$、观测 $X = \Theta + W$、$W \sim f_W$、Estimator 输出 $\hat\Theta$），但此刻被重新解读：$\theta$ 不再是随机变量，$p_X(x;\theta)$ 是一族按 $\theta$ 索引的分布。</span>

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位 + 卡点诊断）:**</span> 从本讲起换世界观。第 9 章开篇（p.459）写得很直白：贝叶斯学派把未知参数当成随机变量、用先验一次性安放全部主观假设；经典学派（又称 frequentist，频率学派）把 $\theta$ 视为未知常数，"对每个可能的 $\theta$ 各摆一个完整模型"，并用 worst-case（最坏情形）视角评价方法——性质必须在**每个** $\theta$ 下都成立才算数。卡点诊断：$p_X(x;\theta)$ 里的分号不是排版装饰，它提醒你 $\theta$ 不是条件化变量而是模型索引——上一讲里 $f_{\Theta|X}(\theta \mid x)$ 依赖先验、是真正的条件分布，这里 $p_X(x;\theta)$ 对所有 $\theta$ 同时成立、无先验可言；同一幅传感器框图，读法已经完全不同。教材第 8 章开篇的 Bayesian versus Classical Statistics 一节（pp. 410–411）对两派有过正面交锋：贝叶斯把假设明码标价在先验里，而许多经典方法往往等价于某个隐含先验下的贝叶斯方法。题型三分法——简单假设检验、复合假设检验、估计——正是随后三讲的路线图：本讲走"估计"，Lec 24 走回归与检验，Lec 25 用显著性检验收尾。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Maximum likelihood estimation（极大似然估计）</span>

- 带未知参数的模型：$X \sim p_X(x;\theta)$。
- 挑选"让数据最可能出现"的 $\theta$：
```math
\hat\theta_{\mathrm{ML}} = \arg\max_{\theta}\ p_X(x;\theta) .
```
- 与贝叶斯 MAP 估计对比：
```math
\hat\theta_{\mathrm{MAP}} = \arg\max_{\theta}\ p_{\Theta|X}(\theta \mid x) = \arg\max_{\theta}\ \frac{p_{X|\Theta}(x \mid \theta)\, p_\Theta(\theta)}{p_X(x)} .
```
- **例**：$X_1, \ldots, X_n$ i.i.d.，服从 exponential($\theta$)（指数分布）：
```math
\max_{\theta}\ \prod_{i=1}^{n} \theta e^{-\theta x_i}
\qquad\Longleftrightarrow\qquad
\max_{\theta}\ n\log\theta - \theta \sum_{i=1}^{n} x_i ,
```
```math
\hat\theta_{\mathrm{ML}} = \frac{n}{x_1 + \cdots + x_n}, \qquad
\hat\Theta_n = \frac{n}{X_1 + \cdots + X_n} .
```

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验算指数例：对 $\ell(\theta) = n\log\theta - \theta\sum_i x_i$ 求导得 $\ell'(\theta) = n/\theta - \sum_i x_i$，置零解出 $\hat\theta_{\mathrm{ML}} = n / \sum_i x_i$ ✓；二阶导 $-n/\theta^2 < 0$ 确认是峰不是谷。卡点诊断：ML 与 MAP 的差别只在先验因子——$p_{\Theta|X}(\theta \mid x) \propto p_{X|\Theta}(x \mid \theta)\, p_\Theta(\theta)$，分母 $p_X(x)$ 与 $\theta$ 无关可以丢弃；先验若为均匀，两者完全重合。这也解释了"样本均值往往就是 ML 估计"的现象：在正态模型（方差已知）下，似然 $\propto \exp\{-\frac{1}{2\sigma^2}\sum_i (x_i - \theta)^2\}$ 是 $\theta$ 的开口向下抛物线，峰顶恰在样本均值处——"最大化似然"与"最小化残差平方和"在此是同一件事，这条线索会在 Lec 24 的线性回归里再次接通。术语提醒：likelihood（似然）是把 $p_X(x;\theta)$ 读成 $\theta$ 的函数（数据固定、参数流动），probability（概率）是把它读成 $x$ 的函数（参数固定、数据流动）——同一个公式，两种阅读方向，统计推断的全部魔法都藏在这趟换座里。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Desirable properties of estimators（估计量的合意性质）</span>

（应当对**所有** $\theta$ 成立！！！）

- **Unbiased（无偏）**：$\mathrm{E}[\hat\Theta_n] = \theta$。
  - 指数例，$n = 1$：$\mathrm{E}[1/X_1] = \infty \ne \theta$（biased，有偏）。
- **Consistent（一致）**：$\hat\Theta_n \to \theta$（in probability，依概率）。
  - 指数例：$(X_1 + \cdots + X_n)/n \to \mathrm{E}[X] = 1/\theta$。
  - 由此可证：$\hat\Theta_n = n/(X_1 + \cdots + X_n) \to 1/\mathrm{E}[X] = \theta$。
- **"小"的 mean squared error（MSE，均方误差）**：
```math
\mathrm{E}[(\hat\Theta - \theta)^2]
= \mathrm{var}(\hat\Theta - \theta) + \bigl(\mathrm{E}[\hat\Theta - \theta]\bigr)^2
= \mathrm{var}(\hat\Theta) + (\text{bias})^2 .
```

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> "对所有 $\theta$ 成立"这行感叹号是经典统计的印章：评价估计量时 $\theta$ 不是随机变量而是被逐点扫描的参数，任何好性质都必须在每一个 $\theta$ 处兑现——这正是 p.459 开篇 worst-case 思想的落实。逐条验算 MSE 分解：把 $Y = \hat\Theta - \theta$ 代入 Lec 07 用过的矩公式 $\mathrm{Var}(Y) = \mathrm{E}[Y^2] - (\mathrm{E}[Y])^2$，得 $\mathrm{E}[(\hat\Theta-\theta)^2] = \mathrm{var}(\hat\Theta - \theta) + (\mathrm{E}[\hat\Theta - \theta])^2$；常数平移不改变方差，$\mathrm{var}(\hat\Theta - \theta) = \mathrm{var}(\hat\Theta)$ ✓，而 $\mathrm{E}[\hat\Theta - \theta] = \mathrm{E}[\hat\Theta] - \theta$ 正是 bias（偏差）✓。$\mathrm{E}[1/X_1] = \infty$ 的病灶在 $x \to 0$：$\int_0^\infty \frac{1}{x}\,\theta e^{-\theta x}\,\mathrm{d}x$ 的被积函数在零点附近被 $1/x$ 拖垮（$\int_0^\epsilon \frac{\mathrm{d}x}{x}$ 发散）。一致性走两步：WLLN（教材第 7 章极限定理的讲次已见）先给 $(X_1 + \cdots + X_n)/n \to \mathrm{E}[X] = 1/\theta$ 依概率成立；倒数函数在远离零处连续，故 $n/(X_1 + \cdots + X_n) \to \theta$ ✓。最后记住这个权衡结构：无偏但方差大，或有偏但 MSE 小——MSE $=$ 方差 $+$ 偏差$^2$ 把两条路线的代价摆在同一张账单上，没有免费午餐。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Estimate a mean（估计一个均值）</span>

- $X_1, \ldots, X_n$ i.i.d.，均值 $\theta$、方差 $\sigma^2$；写成 $X_i = \theta + W_i$，$W_i$ i.i.d.、均值 $0$、方差 $\sigma^2$。
- sample mean（样本均值）：
```math
\hat\Theta_n = M_n = \frac{X_1 + \cdots + X_n}{n} .
```
- 性质：
  - $\mathrm{E}[\hat\Theta_n] = \theta$（unbiased，无偏）。
  - WLLN：$\hat\Theta_n \to \theta$（consistency，一致性）。
  - MSE：$\sigma^2/n$。
- 样本均值往往同时也是 ML 估计，例如 $X_i \sim \mathrm{N}(\theta, \sigma^2)$（i.i.d.）时。

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 三条性质全部真算。无偏：$\mathrm{E}[M_n] = \frac{1}{n}\sum_i \mathrm{E}[X_i] = \theta$ ✓——只用了 Lec 07 的期望线性，连独立性都不需要。MSE：独立时方差和规则（Lec 07 已见）给 $\mathrm{var}(M_n) = \frac{1}{n^2}\cdot n\sigma^2 = \sigma^2/n$，加上零偏差得 MSE $= \sigma^2/n$ ✓。一致性：即 WLLN（i.i.d.、方差有限 $\Rightarrow$ 样本均值依概率收敛到总体均值，教材第 7 章）。跨课程连接：CLRS 分析随机算法时，把"期望比较次数、期望运行时间"的估计层层落在"用样本均值估总体期望"上——indicator random variable（指示随机变量，Lec 07 的帽子问题同款技术）求和后取平均，正是这里的 $M_n$。另一个值得默记的数字直觉：方差按 $1/n$ 收缩，精度只按 $\sqrt{n}$ 增长——想把答案多逼出一位有效数字，观测数要乘上一百；这是实验科学与蒙特卡洛模拟（用大量重复随机采样估期望，脚手架：把 $M_n$ 的 $\sigma^2/n$ 直接搬过去用）共同的地基。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Confidence intervals（置信区间）</span>

- 点估计 $\hat\Theta_n$ 的信息量可能不够。
- $1 - \alpha$ confidence interval（置信区间）是一个（随机的）区间 $[\hat\Theta_n^-, \hat\Theta_n^+]$，满足
```math
P\bigl(\hat\Theta_n^- \le \theta \le \hat\Theta_n^+\bigr) \ge 1 - \alpha, \qquad \forall\, \theta,
```
  - 常取 $\alpha = 0.05$ 或 $0.01$ 等小值。
  - 解读很微妙（subtle）。
- 均值估计中的 CI：$\hat\Theta_n = (X_1 + \cdots + X_n)/n$：
  - 正态表：$\Phi(1.96) = 1 - 0.05/2$；
```math
P\left(\frac{|\hat\Theta_n - \theta|}{\sigma/\sqrt{n}} \le 1.96\right) \approx 0.95 \quad \text{(CLT)} ,
```
```math
P\left(\hat\Theta_n - \frac{1.96\,\sigma}{\sqrt{n}} \le \theta \le \hat\Theta_n + \frac{1.96\,\sigma}{\sqrt{n}}\right) \approx 0.95 .
```
  - 更一般地：设 $z$ 满足 $\Phi(z) = 1 - \alpha/2$，则
```math
P\left(\hat\Theta_n - \frac{z\,\sigma}{\sqrt{n}} \le \theta \le \hat\Theta_n + \frac{z\,\sigma}{\sqrt{n}}\right) \approx 1 - \alpha .
```

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 验证）:**</span> "解读很微妙"微妙在哪？$\theta$ 是常数、区间端点 $\hat\Theta_n \pm z\sigma/\sqrt n$ 才是随机变量，所以 $0.95$ 说的是"**抽样之前**，这个随机区间盖住真值的频率约 95%"；而"$\theta$ 有 95% 的概率落在这个已经算出的具体区间里"是偷跑随机性的错误读法——那是贝叶斯 credible interval（可信区间）的口吻，但这里根本没有先验可用。推导验算：CLT（教材第 7 章的讲次已见）给 $\dfrac{M_n - \theta}{\sigma/\sqrt n} \approx \mathrm{N}(0, 1)$，于是 $P\bigl(|M_n - \theta| \le 1.96\,\sigma/\sqrt n\bigr) \approx 2\Phi(1.96) - 1 = 0.95$ ✓；事件 $\{|M_n - \theta| \le 1.96\sigma/\sqrt n\}$ 与事件 $\{M_n - 1.96\sigma/\sqrt n \le \theta \le M_n + 1.96\sigma/\sqrt n\}$ 是同一个集合的两种写法 ✓——代数上毫无新意，语义上却完成了一次倒转：从"随机变量落进固定区间"翻转为"随机区间罩住固定参数"。最后那个 $\forall\, \theta$ 量词不可省略：覆盖率必须在每个可能的 $\theta$ 处成立，worst-case 思想再次现身。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The case of unknown σ（σ 未知的情形）</span>

- 方案一（Option 1）：用 $\sigma$ 的上界。
  - 若 $X_i$ 为 Bernoulli（伯努利）：$\sigma \le 1/2$。
- 方案二（Option 2）：用 ad hoc（临时拼凑）的 $\sigma$ 估计。
  - 若 $X_i \sim \mathrm{Bernoulli}(\theta)$：$\hat\sigma = \sqrt{\hat\Theta\,(1 - \hat\Theta)}$。
- 方案三（Option 3）：用方差的通用估计。
  - 从 $\sigma^2 = \mathrm{E}[(X_i - \theta)^2]$ 出发：
```math
\hat\sigma_n^2 = \frac{1}{n}\sum_{i=1}^{n}(X_i - \theta)^2 \to \sigma^2
```
  （但 $\theta$ 未知）；
```math
\hat S_n^2 = \frac{1}{n-1}\sum_{i=1}^{n}\bigl(X_i - \hat\Theta_n\bigr)^2 \to \sigma^2
```
  （unbiased：$\mathrm{E}[\hat S_n^2] = \sigma^2$）。

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474；t 置信区间位于 pp. 471–473（本讲不要求）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 逐项验算。Bernoulli 上界：$\mathrm{var}(X_i) = \theta(1-\theta)$ 是开口向下的抛物线，在 $\theta = 1/2$ 处封顶 $1/4$，故 $\sigma \le 1/2$ ✓。方案二是 plug-in（插件式）估计：拿 $\hat\Theta_n$ 顶替未知参数的位子。方案三的关键是分母为什么是 $n-1$ 而不是 $n$：利用 $\sum_i (X_i - M_n)^2 = \sum_i (X_i - \theta)^2 - n(M_n - \theta)^2$（配方恒等式），取期望得 $\mathrm{E}\bigl[\sum_i (X_i - M_n)^2\bigr] = n\sigma^2 - n\cdot\frac{\sigma^2}{n} = (n-1)\sigma^2$ ✓，除以 $n-1$ 才无偏。直觉诊断：$n$ 个偏差 $X_i - M_n$ 之和恒为零（$\sum_i (X_i - M_n) = 0$），独立自由变动的只有 $n-1$ 个——一个线性约束吃掉一个自由度，与 Strang 线代"约束方程降一维"是同一句话。三方案的共同逻辑：CI 公式里的每个量必须"已知或可估计"，$\sigma$ 不肯现身后就用上界、插值、通用估计顶上，代价是覆盖率只是近似成立；教材 pp. 471–473 用 t 分布把这最后一步精确化（本讲不考，知道方向即可）。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
