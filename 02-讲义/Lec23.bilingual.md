# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 23 — Classical Statistical Inference I（经典统计推断 I）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Classical statistics（经典统计）</span>

**阅读（Readings）**：教材 Section 9.1（其中 pp. 471–473 的 t-based confidence intervals（t 置信区间），不列入考核）。

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

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位 + 卡点诊断）:**</span>
> 这条注要回答的设计问题只有一个：当一个未知量不再是随机变量时，整台推断机器该怎么重建。classical statistics（经典统计）把观测模型写成 $X \sim p_X(x;\theta)$，分号右边那个 $\theta$ 只是给模型编了个号；于是"我们知道什么"不再由 prior（先验）承担，而由一族分布承担——每个可能的 $\theta$ 对应这一族里的一个成员。教材把这种结构叫 many models（多个模型），它不是比喻，是字面意思：数学上你手里同时摆着无数个完整模型，其中只有一个是产出了你眼前这份数据的那一个。
>
> 因果链得逐句拆开。Bayesian（贝叶斯）路线里有一个 prior（先验），它把"哪些 $\theta$ 更可信"压成一个概率测度，于是风险可以在 $\theta$ 上做加权平均，压成一个标量；比较两个 estimator（估计量）就是比较两个数。经典路线里这个测度不存在，加权平均根本没有定义，所以"平均风险"不是难算，而是不成立。剩下的唯一可算之量是：固定某一个 $\theta$ 之后，在 sampling distribution（抽样分布）上取的那个期望。单个 $\theta$ 只给一个数，而你要评的是方法而不是某一次结果，于是唯一自洽的比较方式，是让 $\theta$ 跑遍所有可能取值，每值各得一个数，凑成一条曲线，再逐点比较——worst-case（最坏情形）视角不是审美偏好，是 prior（先验）缺席逼出来的唯一选项。
>
> 反过来的失败长什么样，用数字最清楚。设 $X_1,\ldots,X_n$ 是 Bernoulli（伯努利）试验，$n = 100$。估计量一取 sample mean（样本均值）$\hat\Theta_n = M_n$，其 variance（方差）为 $\theta(1-\theta)/100$：在 $\theta = 0.5$ 处等于 $0.0025$，在 $\theta = 0.01$ 处等于 $0.000099$。估计量二取常数 $0.5$，它在 $\theta = 0.5$ 处的误差平方是 $0$，单看这一点完胜；但在 $\theta = 0.01$ 处误差平方是 $0.2401$。若评分只在 $\theta = 0.5$ 上进行，常数估计量赢；放到整条曲线上，$0.2401$ 是 $0.000099$ 的 $2425$ 倍。单点评分能把一个几乎无用的方法评成最优，这就是必须逐点验收的量化理由。
>
> 跨课程连接落在 MIT 6.042J。那门课证全称命题的模板是"取任意元素，只用定义里写明的性质，不许用它的任何特殊性"；这里的 $\forall \theta$ 是同一套纪律搬到概率语境：允许你在推导中途固定一个 $\theta$，禁止使用任何只对这个 $\theta$ 成立的额外信息。区别必须说清：6.042J 的全称断言是离散结构上的确定性结论，一步归纳就能收口；这里的断言内部还套着一层期望 $\mathrm{E}_\theta$，每换一个 $\theta$ 就要重算一次积分，工作量随取值连续增长，所以教材只能用几条能对所有 $\theta$ 一次性收口的通用性质来覆盖整条曲线：unbiasedness（无偏）、consistency（一致性）、MSE（均方误差）分解，各管一段。
>
> 第二条连接在 CSAPP 第 6 章：跑性能测试只在一个输入规模上量 cache 命中率，与这里只在一个 $\theta$ 上评 estimator（估计量）是同一种错误——把一个点的成绩当成整条曲线的成绩。区别在于 CSAPP 那条曲线是硬件行为随规模变化的经验曲线，你只能采样几个规模；这里的风险曲线可以解析写出，"逐点"于是变成证明而不是采样。
>
> 收束：分号、many models（多个模型）、$\forall \theta$ 是同一件事的三种写法——prior（先验）缺席，模型按 $\theta$ 编号，性质逐点验收。后面三讲的估计、检验、回归全部继承这条纪律。

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
- **例**：$X_1, \ldots, X_n$ i.i.d.（独立同分布，independent and identically distributed），服从 exponential($\theta$)（指数分布）：
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

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span>
> 这条注处理两个具体问题：maximum likelihood（极大似然）凭什么只靠"让数据最可能出现"一句话就能定义估计量，以及它与 maximum a posteriori（最大后验）差的到底是哪一步。
>
> 机制先从合法性说起。$\theta$ 是模型编号，$\log$ 是单调递增函数，单调变换不改变 argmax（取到最大值的自变量），所以 $\arg\max_\theta p_X(x;\theta) = \arg\max_\theta \log p_X(x;\theta)$；这一步用的是单调性，不是任何概率性质。真正需要 $\log$ 的理由在后面：i.i.d.（独立同分布，independent and identically distributed）假设把联合密度变成连乘，求导要面对 $n$ 个因子；取 $\log$ 后连乘变连加，导数逐项独立，偏导算子可以穿过求和号。
>
> 还有一处前提必须先说清：把 likelihood（似然）读成 $\theta$ 的函数，这件事成立的前提是"数据已经固定"。样本 $x$ 是观测值而非随机量，随机性已经在抽取样本那一刻用掉了。若把 $x$ 重新当作随机量代入，$\arg\max$ 的结果就是随机变量 $\hat\Theta_n$，那是另一个对象——前者是算出来的一串数，后者是随样本变化的函数。教材同一段里 $\hat\theta_{\mathrm{ML}}$ 与 $\hat\Theta_n$ 并排出现，大小写之别就是这个区别，不是排版随意。
>
> 数值理由同样硬。设单个样本的密度值等于 $0.001$、$n = 1000$，连乘是 $10^{-3000}$；IEEE double（双精度）的最小正规数约 $2.2\times 10^{-308}$，结果直接下溢成 $0$，梯度信息全丢。换成 $\log$ 后是 $1000 \times \log 0.001 \approx -6907.8$，稳稳落在可表示区间内。这就是 log-likelihood（对数似然）在真实代码里几乎必然出现的原因，不是数学洁癖。
>
> 手算一遍指数例。取 $n = 5$，观测值 $0.5, 1.0, 1.5, 2.0, 3.0$，和是 $8.0$，故 $\hat\theta_{\mathrm{ML}} = 5/8 = 0.625$。代回 $\ell(\theta) = 5\log\theta - 8\theta$：$\theta = 0.625$ 时得 $5 \times (-0.4700) - 5.0 = -7.3500$；$\theta = 0.5$ 时得 $5 \times (-0.6931) - 4.0 = -7.4657$。峰值确实在 $0.625$，两者差 $0.1157$。
>
> 与 MAP 的差别只在 prior（先验）因子。后验密度正比于似然乘先验，分母 $p_X(x)$ 与 $\theta$ 无关，可以整个丢掉，于是 argmax（取到最大值的自变量）只看分子；若 prior（先验）是均匀的，因子是常数，两个最大值点完全重合。这也解释了"样本均值常常就是 ML 估计"：正态模型、方差已知时，log-likelihood（对数似然）等于 $-\dfrac{1}{2\sigma^2}\sum_{i}(x_i - \theta)^2$ 加常数，最大化它就是最小化 residual sum of squares（残差平方和），峰顶落在 sample mean（样本均值）上。这条线索在 Lec 24 的线性回归里接通：线性回归的 ML 解就是最小二乘。
>
> 参数变换下的不变性值得单记一条：若 $g$ 严格单调，则 $g(\hat\theta_{\mathrm{ML}})$ 就是 $g(\theta)$ 的 ML 估计，因为 argmax（取到最大值的自变量）在单调变换下不动。指数例里 $\bar x$ 既是 $\theta$ 的 ML 估计，也是 $1/\theta$ 的 ML 估计，后者正是平均寿命的估计，不必重做求导。maximum a posteriori（最大后验）没有这条性质：后验密度换元要乘 Jacobian（雅可比因子），prior（先验）会被拉变形，结论随参数化方式变化。
>
> 跨课程连接在 CSAPP 第 6 章：讲 AMAT 时反复强调平均值必须在正确的层上取，否则把不同尺度的量混加；这里换座到 $\log$ 层是同一手法——乘法层上的比较在加法层上等价，换层是为了让求和可做。区别要标出：AMAT 的换层是近似（假设命中时间与缺失率独立），$\log$ 换座是精确等号，不丢任何信息。
>
> 术语提醒：probability（概率）是把同一个密度读成数据的函数，likelihood（似然）是把它读成参数的函数；数据固定、参数流动，这才是"似然"二字的全部内容。缩写一并记下：ML = maximum likelihood（极大似然），MAP = maximum a posteriori（最大后验）。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Desirable properties of estimators（估计量的合意性质）</span>

（应当对**所有** $\theta$ 成立！！！）

- **Unbiased（无偏）**：$\mathrm{E}[\hat\Theta_n] = \theta$。
  - 指数例，$n = 1$：$\mathrm{E}[1/X_1] = \infty \ne \theta$（biased（有偏））。
- **Consistent（一致）**：$\hat\Theta_n \to \theta$（in probability（依概率））。
  - 指数例：$(X_1 + \cdots + X_n)/n \to \mathrm{E}[X] = 1/\theta$（这一步是 WLLN，Weak Law of Large Numbers（弱大数定律），见下）。
  - 由此可证：$\hat\Theta_n = n/(X_1 + \cdots + X_n) \to 1/\mathrm{E}[X] = \theta$。
- **"小"的 mean squared error（MSE，均方误差）**：
```math
\mathrm{E}[(\hat\Theta - \theta)^2]
= \mathrm{var}(\hat\Theta - \theta) + \bigl(\mathrm{E}[\hat\Theta - \theta]\bigr)^2
= \mathrm{var}(\hat\Theta) + (\text{bias})^2 .
```

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span>
> "对所有 $\theta$ 成立"这行感叹号是经典统计的印章：评价 estimator（估计量）时 $\theta$ 不是随机变量，而是被逐点扫描的索引，任何性质都必须在每一个 $\theta$ 处兑现——这是 p.459 开篇 worst-case（最坏情形）思想的落实。
>
> 先验算 MSE（均方误差）分解。令 $Y = \hat\Theta - \theta$，代入矩公式 $\mathrm{var}(Y) = \mathrm{E}[Y^2] - (\mathrm{E}[Y])^2$，移项即得 $\mathrm{E}[(\hat\Theta-\theta)^2] = \mathrm{var}(\hat\Theta-\theta) + (\mathrm{E}[\hat\Theta-\theta])^2$；常数平移不改 variance（方差），故第一项等于 $\mathrm{var}(\hat\Theta)$，第二项的底数是 $\mathrm{E}[\hat\Theta]-\theta$，正是 bias（偏差）。这个恒等式不含任何估计量特有的信息，它只把误差平方拆成"抖动"与"瞄准偏移"两笔账——所以它成立的代价是零，可疑之处也就为零。
>
> $\mathrm{E}[1/X_1] = \infty$ 的病灶在原点：$x \to 0$ 时 $e^{-\theta x} \to 1$，被积函数等价于 $\theta/x$，而 $\int_0^\epsilon \mathrm{d}x/x$ 发散。这不是修修补补能救的技术问题，它说明 $n = 1$ 时这个估计量连平均值都不存在。$n \ge 2$ 才活过来：取 $\theta = 1$、$n = 100$，和 $\sum_i X_i$ 服从形状参数为 $100$ 的 Gamma（伽马）分布，$\mathrm{E}[n/\sum_i X_i] = \frac{n}{n-1}\theta = 100/99 \approx 1.0101$，bias（偏差）约 $0.0101$，即百分之一；而 $n \to \infty$ 时偏差趋于零——consistency（一致性）把 unbiasedness（无偏）丢掉的那一点买了回来。
>
> 无偏不是免费的午餐，算一个"有偏但更省"的例子。取 $\hat\Theta = c M_n$，$\theta = 1$、$\sigma = 2$、$n = 100$，则 $\mathrm{MSE}(c) = (c-1)^2\theta^2 + c^2\sigma^2/n = (c-1)^2 + 0.04c^2$。对 $c$ 求导置零得 $c^{*} = 1/1.04 \approx 0.9615$，代入得 $\mathrm{MSE}(c^{*}) = 0.04/1.04 \approx 0.03846$，比无偏时的 $0.04$ 小约 $3.85\%$。把 sample mean（样本均值）乘上 $0.9615$ 换来 MSE（均方误差）下降，这就是 shrinkage（收缩）的最朴素形态：用一点偏差买掉一截方差。代价也得交底：$c^{*}$ 依赖 $\theta$ 与 $\sigma$，真做起来必须先估再代，估计误差会吃掉一部分收益；而且 $c^{*}$ 与 $\sigma^2/n$ 同步变化，样本一大就有 $c^{*} \to 1$，收缩自己消失。
>
> 跨课程连接在 CLRS（Cormen、Leiserson、Rivest、Stein 著《算法导论》）的算法分析。那里有两条平行的评价线：amortized analysis（摊还分析）给一个操作序列上的平均代价，worst-case analysis（最坏情形分析）给每个输入都成立的界；而 average-case analysis（平均情形分析）必须先假设输入的分布，那个分布就是算法分析里的 prior（先验）。没有 prior（先验）就只能给 worst-case（最坏情形）界，与经典统计的处境完全同构。量级差异很实在：$n = 10^6$ 时快排的 $n\log_2 n \approx 1.99\times 10^{7}$ 次比较，按每次 $10\ \mathrm{ns}$ 计约 $0.2\ \mathrm{s}$；而 $n^2/2 = 5\times 10^{11}$ 次比较要 $5000\ \mathrm{s}$，相差两万五千倍。区别在于对抗者不同：算法分析里的对抗者是输入生成者，统计里的对抗者是 $\theta$ 本身，两者都不必给出分布。
>
> 再补一层机制：逐点比较给出的不是全序而是偏序。若两个 estimator（估计量）的 risk（风险）曲线一条在 $\theta = 0.5$ 处低、另一条在 $\theta = 0.01$ 处低，两条曲线交叉，则谁都不占优，只能说"在这个区间里甲更好"。这正是经典统计很少下"最优估计量"结论的原因，它改给一致、无偏、渐近有效这一串分别成立的性质——每一条都是对曲线施加的局部约束，不是对全体 $\theta$ 的排序。只有当一条曲线对所有 $\theta$ 都不高于另一条时，那种占优才配叫定理。
>
> 收束：unbiasedness（无偏）是逐点零偏差，MSE（均方误差）是逐点误差平方，consistency（一致性）是 $n \to \infty$ 的逐点极限；三条性质都是函数与函数的比较，不是数与数的比较。这也是"这个估计量的 MSE（均方误差）是多少"这种问法本身残缺的原因——必须补上"在哪个 $\theta$ 处"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Estimate a mean（估计一个均值）</span>

- $X_1, \ldots, X_n$ i.i.d.，均值 $\theta$、方差 $\sigma^2$；写成 $X_i = \theta + W_i$，$W_i$ i.i.d.、均值 $0$、方差 $\sigma^2$。
- sample mean（样本均值）：
```math
\hat\Theta_n = M_n = \frac{X_1 + \cdots + X_n}{n} .
```
- 性质：
  - $\mathrm{E}[\hat\Theta_n] = \theta$（unbiased（无偏））。
  - WLLN：$\hat\Theta_n \to \theta$（consistency（一致性））。
  - MSE：$\sigma^2/n$。
- 样本均值往往同时也是 ML 估计，例如 $X_i \sim \mathrm{N}(\theta, \sigma^2)$（i.i.d.）时。

> <span style="color:#7f8c8d;">Bertsekas §9.1, p.460–474</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span>
> sample mean（样本均值）之所以是默认 estimator（估计量），是因为三条性质各自只需要一个很便宜的事实就能兑现；便宜到你容易误以为它们免费，其实代价全藏在假设里。
>
> unbiasedness（无偏）只用了期望的线性：$\mathrm{E}[M_n] = \frac{1}{n}\sum_i \mathrm{E}[X_i] = \theta$，连独立性都没用到。这条的廉价也正是它的弱点——它只管一阶矩，对离散程度一言不发。取 $n = 4$，观测 $2,4,6,8$ 时 $M_4 = 5$，改成 $2,4,6,80$ 时 $M_4 = 23$；两次都无偏，可后者的单次读数离 $\theta$ 差着一个数量级。所以"无偏"两个字只保证平均下来不偏，绝不保证你手里这一份不偏。
>
> 顺带记一条脆弱性：$2,4,6,80$ 这组数的 $M_4 = 23$，而 median（中位数）仍是 $5$。当模型真是正态、真没有离群值时，$M_n$ 的方差严格更小，是更优的 estimator（估计量）；一旦模型假设错了，单点就能把它拖出十倍。工程里常说的"先看分布再选统计量"，讲的就是这层依赖。
>
> MSE（均方误差）就贵了：$\mathrm{var}(M_n) = \sigma^2/n$ 的推导里，$\frac{1}{n^2}\sum_{i,j}\mathrm{cov}(X_i,X_j)$ 的 $n(n-1)$ 个非对角项必须整体消失，靠的正是独立性。若只是相关而不独立、correlation（相关系数）记为 $\rho$，则 $\mathrm{var}(M_n) = \sigma^2/n + (1-1/n)\rho\sigma^2$。取 $\sigma = 1$、$\rho = 0.5$、$n = 100$：方差是 $0.01 + 0.99 \times 0.5 = 0.505$，标准差 $0.711$，而不是 $0.1$——差 $7.1$ 倍；$\rho = 1$ 时方差恒为 $1$，加多少样本都不降。这就是"样本必须独立"这句话的量化内容。
>
> 再算一个精确数：$X_i \sim \mathrm{Uniform}[0,1]$ 时 $\sigma^2 = 1/12$，取 $n = 12$ 得 $\mathrm{var}(M_{12}) = 1/144$，标准差 $1/12 \approx 0.0833$。$\sqrt{n}$ 律的代价在此现形：要把标准差减半到 $0.0417$，样本量得从 $12$ 涨到 $48$；要多逼出一位十进制数字，样本量得涨 $100$ 倍。
>
> 再补一层机制：为什么权重必须均匀。取 $n = 3$，权重 $w_1,w_2,w_3$ 且和为 $1$，方差是 $\sigma^2\sum_i w_i^2$；要在约束下最小化就得让三者相等，均匀权重给 $\sigma^2/3 \approx 0.333\sigma^2$，而 $(0.5, 0.25, 0.25)$ 给 $\sum_i w_i^2 = 0.375$，方差涨 $12.5\%$。所以"取平均"不是随手的选择，它是这条约束下的唯一最优解；一旦允许有偏，最优性立刻失效：把 $M_n$ 缩放成 $c M_n$ 再挑合适的 $c$，就可能比均匀平均更省。
>
> consistency（一致性）用 Chebyshev 不等式就能证：$P(|M_n - \theta| \ge \epsilon) \le \sigma^2/(n\epsilon^2)$。取 $\sigma = 1$、$\epsilon = 0.1$、$n = 1000$，右端是 $0.1$；而 CLT（Central Limit Theorem，中心极限定理）给的实际值约 $2(1-\Phi(3.16)) \approx 0.0016$，差六十多倍。两个数都对：Chebyshev 只要 variance（方差）有限，CLT 要多付假设换更紧的结论——这个取舍在整门课里反复出现。
>
> 跨课程连接两条。其一在 CLRS：分析随机算法时用 indicator random variable（指示随机变量）求和再取平均，得到正是 $M_n$ 的特例，$\sigma^2/n$ 搬过去就是 Monte Carlo simulation（蒙特卡洛模拟）的误差条。其二在 CSAPP 第 6 章：在循环里重复量 AMAT 时，时间局部性让各次测量强相关，误差条根本不收缩——那是本注公式在 $\rho = 1$ 端点的活样本。区别在于相关性来源：CSAPP 里由缓存状态造成，是系统行为；这里由模型假设写定，写出来才算数。
>
> 顺便说清为什么偏偏用平方：平方误差展开时交叉项刚好整体消掉，才换来"var（方差）加 bias（偏差）平方"这条干净恒等式；换成绝对值误差，分解不再成立，可算性就没了。代价是大错被平方放大，一次 $3\sigma$ 的偏离贡献 $9$ 倍，所以 MSE（均方误差）天然偏向稳的方案。这也是 risk（风险）取 MSE（均方误差）的原因：它让偏差与方差真正解耦。
>
> 收束：$\sqrt{n}$ 不是修辞，它是"精度只能用样本量换、且按平方根汇率换"的牌价。

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
  - 正态表：$\Phi(1.96) = 1 - 0.05/2$（其中 $\Phi$ 是标准正态 $\mathrm{N}(0,1)$ 的 CDF（累积分布函数，cumulative distribution function））；
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

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 验证）:**</span>
> "解读很微妙"微妙在随机性坐错了位置。$\theta$ 是常数，随机的是区间端点 $\hat\Theta_n \pm z\sigma/\sqrt n$；所以 $0.95$ 描述的是 procedure（做法）的长期频率，不是某个已经算出区间的属性。
>
> 推导验算一遍。CLT（Central Limit Theorem，中心极限定理）给 $\dfrac{M_n - \theta}{\sigma/\sqrt n} \approx \mathrm{N}(0,1)$，于是 $P(|M_n - \theta| \le 1.96\sigma/\sqrt n) \approx 2\Phi(1.96) - 1 = 0.95$。事件 $\{|M_n-\theta| \le c\}$ 与 $\{M_n - c \le \theta \le M_n + c\}$ 是同一个集合的两种不等式写法，代数上毫无新意，语义上却完成一次倒转：从"随机变量落进固定区间"翻成"随机区间罩住固定参数"。confidence interval（置信区间）的全部哲学就压在这一步移项里。
>
> 代入数字。取 $n = 100$、$\sigma = 2$、算得 $M_n = 5.0$，半宽 $1.96 \times 2/10 = 0.392$，区间 $[4.608, 5.392]$，全长 $0.784$。换成 $99\%$，$z = 2.576$，半宽 $0.5152$，得 $[4.4848, 5.5152]$。要把半宽砍掉一半需 $n = 400$；要半宽 $0.1$ 需 $n = (1.96 \times 2/0.1)^2 = 1536.64$，向上取整 $1537$。宽度与 $\sqrt n$ 成反比，成本与 $n$ 成正比——精度每翻一倍，采样量翻四倍。
>
> $z$ 是标准正态的分位数，信心越高 $z$ 越大：$90\%$ 对应 $1.645$，$95\%$ 对应 $1.96$，$99\%$ 对应 $2.576$。同样 $n = 100$、$\sigma = 2$ 时半宽分别是 $0.329$、$0.392$、$0.5152$，$99\%$ 的区间比 $90\%$ 宽 $57\%$，样本量一点没加。所以 confidence（信心）是最贵的商品：每提高一档都要用宽度或样本量付账，不存在又窄又准还省数据的区间。
>
> CLT（Central Limit Theorem，中心极限定理）在这里只是近似，适用边界要点明。取 $n = 100$ 的 Bernoulli（伯努利）试验、真值 $\theta = 0.01$，期望成功数只有 $1$，此时正态近似严重失真：设 $\hat\Theta = 0.01$、$\hat\sigma \approx 0.0995$，半宽 $0.0195$，区间下限落在 $-0.0095$——概率不可能为负，这个界就是废的。常用判据是 $n\theta \ge 5$ 且 $n(1-\theta) \ge 5$；不满足时教材后面改用 exact（精确）的办法，本讲只要求你知道近似朝哪个方向崩。
>
> 错误读法要指名。说"$\theta$ 落在 $[4.608,5.392]$ 的概率是 $0.95$"时，$\theta$ 是常数，那个事件要么真要么假，概率只能是 $0$ 或 $1$。它借的是 Bayesian（贝叶斯）的 credible interval（可信区间）语感，但 credible interval（可信区间）必须先有 prior（先验），这里没有。诚实的说法是：这套造区间的手续重复一万次，大约九千五百次罩住真值。
>
> 再给一个两样本对照，把"频率"变成看得见的东西。设真值 $\theta = 5.1$、$\sigma = 2$、$n = 100$。第一次抽得 $M_n = 5.0$，区间 $[4.608, 5.392]$，没罩住真值；第二次抽得 $M_n = 5.2$，区间 $[4.808, 5.592]$，罩住了。同一套 procedure（做法），答案一正一误，$0.95$ 说的就是这样的抽样重复一万次里大约九千五百次罩住——它落在做法上，不落在某一次结果上。这也是为什么写论文时区间照报、但没人说"该参数有九成五的概率在此区间"。
>
> 量词位置也要看清：$\forall \theta$ 在 $P$ 外面。挪进去写成"存在某个 $\theta$ 使覆盖率达标"，条件立刻被抽空——随便挑一个 $\theta$ 都能凑出 $0.95$，worst-case（最坏情形）约束就消失了。这正是 p.459 那条纪律在区间估计上的形态。
>
> 跨课程连接在 CLRS 的 randomized quicksort（随机快排）：那里 $\mathrm{E}[T]$ 是在算法自己抛的硬币上取期望，对每个固定输入都给同一个结论，随机性属于算法；这里的随机性属于数据，同一套 procedure（做法）换一批样本就换一个区间。区别很关键：快排的期望时间能靠换随机种子调整，置信区间的覆盖率不是你能对单次抽样调整的量。
>
> 收束：区间随机、参数固定；这句话反着读就全错。下次见到别人说"95% confidence interval（置信区间）"，先问一句"随机的是谁"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The case of unknown σ（σ 未知的情形）</span>

- 方案一（Option 1）：用 $\sigma$ 的上界。
  - 若 $X_i$ 为 Bernoulli（伯努利，取值 0 或 1 的随机变量，$\mathrm{P}(X_i = 1) = \theta$）：$\sigma \le 1/2$。
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

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span>
> $\sigma$ 缺席时能做的事只有三档：用上界、用 plug-in（插件式）估计、用通用方差估计。三档的代价不同，选哪一档取决于你对 $\theta$ 落在哪里有多少把握。
>
> 上界档：Bernoulli（伯努利）的 $\mathrm{var}(X_i) = \theta(1-\theta)$ 是开口向下的抛物线，顶点在 $\theta = 1/2$ 处等于 $1/4$，故 $\sigma \le 1/2$。这个界不花钱但保守：真值靠近 $\theta = 0.5$ 时几乎无损，靠两端时浪费极大——$\theta = 0.05$ 处真实 $\sigma = \sqrt{0.0475} \approx 0.2179$，不到界的一半。
>
> plug-in（插件式）档：拿 $\hat\Theta_n$ 顶替未知参数。$100$ 次试验成功 $60$ 次，$\hat\Theta = 0.6$，$\hat\sigma = \sqrt{0.6 \times 0.4} = \sqrt{0.24} \approx 0.4899$，半宽 $1.96 \times 0.4899/10 = 0.0960$，区间 $[0.504, 0.696]$；改用最坏界 $0.5$，半宽 $0.098$，区间 $[0.502, 0.698]$——只省下 $0.002$。换个位置就差得多：$\hat\Theta = 0.05$ 时 $\hat\sigma \approx 0.2179$，半宽 $0.0427$，比最坏界窄 $2.3$ 倍。结论是：最坏界只有 $\theta$ 靠近 $1/2$ 时才算免费。
>
> 先把 plug-in（插件式）的偏差算清，别当它免费。由 $\mathrm{E}[\hat\Theta^2] = \theta^2 + \theta(1-\theta)/n$ 可得 $\mathrm{E}[\hat\Theta(1-\hat\Theta)] = \theta(1-\theta)(1-1/n)$。取 $\theta = 0.6$、$n = 100$：真方差 $0.24$，plug-in（插件式）的期望只有 $0.24 \times 0.99 = 0.2376$，缩小 $1\%$，半宽跟着缩 $0.5\%$。方向确定偏低，于是覆盖率略低于名义值；偏差小到可忽略，但性质上它确实有偏，与 $M_n$ 的无偏不是一回事。
>
> 通用档为什么除 $n-1$：恒等式 $\sum_i (X_i - M_n)^2 = \sum_i (X_i - \theta)^2 - n(M_n - \theta)^2$ 成立，证法是把 $X_i - \theta$ 拆成 $(X_i - M_n) + (M_n - \theta)$ 展开，交叉项因 $\sum_i (X_i - M_n) = 0$ 整体消失。取期望后右边是 $n\sigma^2 - n \cdot \sigma^2/n = (n-1)\sigma^2$，所以除 $n-1$ 才无偏。手算核对：数据 $2,4,6,8$，$M = 5$，偏差平方和 $9+1+1+9 = 20$，除 $3$ 得 $6.667$，除 $4$ 得 $5.0$，比值 $3/4$ 正是 $(n-1)/n$。
>
> 更本质的说法在这里：$M_n$ 是使 $\sum_i (X_i - c)^2$ 最小的那个 $c$，所以对任何 $\theta$ 都有 $\sum_i (X_i - M_n)^2 \le \sum_i (X_i - \theta)^2$——偏差平方和永远被压低，除 $n$ 必然系统性低估 $\sigma^2$。拿 $2,4,6,8$ 试：取 $\theta = 4$ 得 $4+0+4+16 = 24$，取 $M = 5$ 得 $20$，确实更小。这不是巧合，是最小二乘的极小性；$n-1$ 就是为这次人为压低付的补偿费。
>
> 分母的量级顺手记下：$n = 20$ 时除以 $n$ 与除以 $n-1$ 差 $5\%$，$n = 100$ 时差 $1\%$。小样本下选错分母看得见，大样本下两者几乎一样；但覆盖率要求对每个 $n$ 都成立，所以代码里照样写 $n-1$。
>
> 跨课程连接在 Strang 的线性代数。偏差向量 $x - \bar x \mathbf{1}$ 是 $x$ 在分量和为零那个子空间上的投影，投影矩阵 $P = I - \frac{1}{n}\mathbf{1}\mathbf{1}^{T}$，它的 trace（迹）与 rank（秩）都等于 $n-1$；代入 $x = \theta\mathbf{1} + w$ 得 $Px = Pw$，于是 $\mathrm{E}\lVert Px \rVert^2 = \mathrm{trace}(P)\sigma^2 = (n-1)\sigma^2$——$n-1$ 不是口诀，它是投影的秩。区别要标出：Strang 那里的秩对每一次具体算例都是同一个整数，这里的 $n-1$ 是期望的系数，单次实现的平方和可以远大于或远小于它。
>
> t distribution（学生 t 分布）的代价可以量化：degrees of freedom（自由度）为 $24$（即 $n = 25$）时 $97.5\%$ 分位数是 $2.064$，比 $1.96$ 宽 $5.3\%$；自由度为 $10$ 时是 $2.228$，宽 $13.7\%$。样本越小代价越大——这也反过来说明，前面那套 $z$ 公式默认了大样本。
>
> 最后指个方向：$\sigma$ 被换成估计量之后，$(M_n - \theta)/(\hat S_n/\sqrt n)$ 不再服从正态，而是 t distribution（学生 t 分布），覆盖率要用它重算——这就是 pp. 471–473 那段本讲不列入考核的内容。机制一句话：分母自带随机性，尾部变厚，$z$ 得让位给更大的分位数。
>
> 工程上的选择规则可以一句话记住：量的是比例，直接上 plug-in（插件式）；量的是连续量且样本不小，用 $\hat S_n^2$；只有样本极小、又必须给硬保证时，才退回最坏界收口。顺序其实是先看数据长什么样，再决定要付多少保守税。
>
> 收束：三档方案是同一条原则的三次让步——confidence interval（置信区间）公式里每个量必须已知或可估；$\sigma$ 不肯现身，就用上界、插值、通用估计顶上，代价只是覆盖率从精确变成近似。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
