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
  - 与贝叶斯 MAP（maximum a posteriori，最大后验概率）估计对比：$\max_\theta p_{\Theta|X}(\theta \mid x)$，或 $\max_\theta \dfrac{p_{X|\Theta}(x \mid \theta)\, p_\Theta(\theta)}{p_X(x)}$。
- 样本均值估计 $\theta = \mathrm{E}[X]$：$\hat\Theta_n = (X_1 + \cdots + X_n)/n$。
- $1 - \alpha$ 置信区间：$P(\hat\Theta_n^- \le \theta \le \hat\Theta_n^+) \ge 1 - \alpha$，$\forall\, \theta$。
- 样本均值的置信区间：设 $z$ 满足 $\Phi(z) = 1 - \alpha/2$，则 $P\bigl(\hat\Theta_n - \frac{z\sigma}{\sqrt n} \le \theta \le \hat\Theta_n + \frac{z\sigma}{\sqrt n}\bigr) \approx 1 - \alpha$。

**本讲大纲（Outline）**：
- 线性回归（Linear regression）。
- 二元假设检验（Binary hypothesis testing）：
  - 误差类型（Types of error）；
  - 似然比检验（Likelihood ratio test, LRT）。

> <span style="color:#7f8c8d;">Bertsekas §9.2, p.475–484；§9.3, p.485–494</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲是经典统计推断的"应用双联画"：前半用一条直线去拟合数据（回归），后半在两个假设之间做裁决（检验），两者共用 maximum likelihood（极大似然）那套"让数据最可能出现"的灵魂。这句并列不是修辞，它说的是一件很硬的事：两件事在算法层面共用同一次计算——先把"数据在某个世界模型下出现的相对可能性"算出来，再看你要的是连续参数，还是两个离散解释里更可信的那一个。
>
> 机制上，这台机器只做一次角色翻转。平常算概率是"已知世界、预测数据"；现在数据已经握在手里，翻转过来问"什么样的世界最可能产出这组数据"，那个被反问的世界就是参数 $\theta$。regression（回归）让 $\theta$ 在连续区间里取值，"最可能"因此变成一次求峰，峰位由导数置零给出；hypothesis testing（假设检验）让 $\theta$ 只在两个取值里挑，"最可能"退化成一次比较，两个取值下的可能性相除，比值与阈值相撞便出判决。参数空间是连续还是二元，决定了同一台机器的输出是一个点还是一个 bit（比特）。
>
> Lec 23 的三件套在这里全部被复用，这是检验"是否真听懂"最省力的办法。回归的解靠"导数置零"，它的正态解释靠 likelihood function（似然函数）——把噪声假设成高斯，对数似然就变形为 sum of squared residuals（残差平方和）的相反数；likelihood ratio test（似然比检验）是 MAP 法则把先验搬进阈值之后的产物，先验一拿掉，剩下的比值就成无先验的判据；confidence interval（置信区间）思想日后会出现在回归的成果报告里，每个系数旁边那根误差棒，用的正是同一种区间语言。
>
> 教材的编排印证了这个分工：§9.2 自 p.475 起、§9.3 自 p.485 起，本讲恰好横跨两节；讲义写 "Reference: Section 9.3"，是因为后半的检验是全新概念，前半的回归只是 Lec 23 估计框架向下延伸。再回指 Lec 22 的 linear least mean squares（线性最小均方）：那边是"用 $X$ 线性预测 $\Theta$"，这边是"用 $x$ 线性预测 $y$"，同一个斜率公式将在本讲后半重逢，读到那里请主动对照。
>
> 手算一遍能把两条分支都落地。取三点 $(0,1)$、$(1,2)$、$(2,4)$，则 $\bar x = 1$、$\bar y = 7/3 \approx 2.333$，代入斜率公式得 $\hat\theta_1 = 3/2 = 1.5$、截距 $\hat\theta_0 = 7/3 - 1.5 = 5/6 \approx 0.833$，拟合线为 $\hat y = 0.833 + 1.5x$；三个 residual（残差）是 $0.167$、$-0.333$、$0.167$，平方和 $1/6 \approx 0.167$。把同一组数字换到检验一侧：连抛十次硬币见到七次正面，$H_0$ 主张 $p = 0.5$、$H_1$ 主张 $p = 0.8$，两个模型下的二项概率都带同一个组合数 $\binom{10}{7}$，相除时整块约掉，剩下的核心因子是 $0.5^{10} = 0.0009766$ 与 $0.8^{7} \cdot 0.2^{3} = 0.0016777$，比值 $1.718$；两假设先验各半时阈值恰为 $1$，$1.718 > 1$，判决倒向 $H_1$。十个观测的全部信息被压缩成一个超过 $1$ 的数，这个压缩动作就是后半讲要反复用的工具。
>
> 跨课程连接放在这里最合适：CLRS 的 binary search（二分搜索）与上面的 likelihood ratio（似然比）是同一个动作的两种包装——都先把一批证据折叠成一个标量，再拿标量与阈值比较，一次比较砍掉一半可能性空间。区别在失败模式：二分的比较是精确的，砍错只能是代码写错；似然比的比较对象是随机变量，阈值定死后，$H_0$ 为真仍有 $\alpha$ 的概率往错误方向砍，$H_1$ 为真仍有 $\beta$ 的概率没砍过去，两种错误不能同时清零。这多出来的一个自由度，正是后半讲全部分量的来源。另一处锚点在 Strang 的 linear algebra（线性代数）：least squares（最小二乘）的 normal equation（正规方程）把拟合化成一次矩阵求解，与这里"逐个求偏导置零"是同一件事的代数写法，区别只在一个按坐标算、一个整体做 projection（投影）。
>
> 于是读本讲时别把它当两门学问：先认出那台共用的机器，再看参数空间是连续还是二元，剩下的推导都只是它在两种输入下的展开。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Regression（回归）</span>

- 数据：$(x_1, y_1), (x_2, y_2), \ldots, (x_n, y_n)$。
- 模型：$y \approx \theta_0 + \theta_1 x$；最小化残差平方和：
```math
\min_{\theta_0, \theta_1}\ \sum_{i=1}^{n} \bigl(y_i - \theta_0 - \theta_1 x_i\bigr)^2 .
```
- 一种解读：$Y_i = \theta_0 + \theta_1 x_i + W_i$，$W_i \sim \mathrm{N}(0, \sigma^2)$，i.i.d.（independent and identically distributed，独立同分布）：
  - 似然函数 $f_{X,Y \mid \theta}(x, y; \theta)$ 为 $c \cdot \exp\bigl\{-\frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - \theta_0 - \theta_1 x_i)^2\bigr\}$；
  - 取对数，与上式相同（$\ast$）；
  - 最小二乘 $\iff$ 假装 $W_i$ 是 i.i.d. 正态。

> <span style="color:#7f8c8d;">图：散点 $(x_i, y_i)$ 与拟合直线 $\hat y = \hat\theta_0 + \hat\theta_1 x$；第 $i$ 条 residual（残差）为竖直线段 $y_i - \hat\theta_0 - \hat\theta_1 x_i$，回归选取的正是使残差平方和最小的直线（对应教材 Fig. 9.5）。</span>

> <span style="color:#7f8c8d;">Bertsekas §9.2, p.475–484</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 这一步要拆的不是结论，而是那句 iff 里为什么"平方"必然出现。教材 p.476 的展开可作本页注脚：以"受教育年限 $x$ 与年收入 $y$"为例，散点图常显出近似线性，于是设 $y \approx \theta_0 + \theta_1 x$；模型预测值 $\hat y_i = \hat\theta_0 + \hat\theta_1 x_i$ 与真值之差 $\tilde y_i = y_i - \hat y_i$ 就是 residual（残差），"残差小 = 拟合好"，于是最小化 $\sum_i (y_i - \theta_0 - \theta_1 x_i)^2$。但"好"凭什么用平方来量？这才是本注要回答的问题。
>
> 因果链有四步，一步都不能省。第一步：若 $W_i$ 是 i.i.d.（独立同分布）的，整组观测的联合密度就是各点密度的乘积，因为条件独立把联合密度因子化了。第二步：乘积的极值不好求，求导会拖出一堆交叉项，但密度处处为正，取对数不改变极值位置，而 log 把乘积变成求和，于是最大化联合密度等价于最大化 $\sum_i \log f(y_i - \theta_0 - \theta_1 x_i)$。第三步：正因如此，最终式子的形状完全由单个误差的 log 密度决定——该密度是二次的，和式就是平方和；是线性的，和式就是绝对值之和。第四步：normal distribution（正态分布）的 log 密度恰好是 $-\frac{u^2}{2\sigma^2}$ 加常数，这就是它唯一特殊的地方，也是"平方"登场的全部原因。
>
> 反向更值得警惕：任何平方和目标都自动获得一个正态解释，因为只要把 $\exp\{-\mathrm{SSE}/(2\sigma^2)\}$ 凑成一个密度，凑出来的必然是正态。所以 least squares（最小二乘）与"假装噪声正态"不是巧合，而是同一个二次型在两套语言里的两次命名。若噪声换成 Laplace distribution（拉普拉斯分布），log 密度变成 $-\lvert u\rvert/b$，最大化似然立刻变成最小化绝对偏差之和，最优直线随之移动——同一组点、不同噪声假设，答案不同。这就是"平方不是天经地义，它是正态的指纹"的实际含义。顺带把 $\sigma$ 也估出来：对数似然对 $\sigma$ 求偏导置零给出 $\hat\sigma^2 = \mathrm{SSE}/n$，本例为 $0.1667/3 \approx 0.0556$、$\hat\sigma \approx 0.236$；但这个除法忽略了"两个参数已经花掉两个自由度"，无偏版本用 $n-2$ 做分母，得 $0.1667/1 = 0.1667$、$\hat\sigma \approx 0.408$。两个数差了一倍多，$n = 3$ 时这点差异不容忽略，样本量做大以后两者才靠近。
>
> 数字上验一遍。三点 $(0,1)$、$(1,2)$、$(2,4)$，最优解 $\hat\theta_0 = 5/6$、$\hat\theta_1 = 3/2$ 给出 SSE $= 1/6 \approx 0.1667$；随手取 $\theta_0 = 1$、$\theta_1 = 1$，预测值 $(1,2,3)$，SSE $= 0 + 0 + 1 = 1$。设 $\sigma = 0.5$，两个候选的对数似然之差是 $-(0.1667 - 1)/(2 \times 0.25) = 1.6667$，换回原尺度是 $e^{1.6667} \approx 5.29$ 倍——最优那组参数下的似然，是随手那组的五倍还多。再把这组点配上 $b = 0.5$ 的拉普拉斯噪声：同一对候选的绝对偏差分别是 $0.1667 + 0.3333 + 0.1667 = 0.6667$ 与 $0 + 0 + 1 = 1$，对数似然之差只剩 $0.6667$，倍数掉到 $e^{0.6667} \approx 1.95$——证据强度被噪声假设改写了，而 SSE 一个数都没变。
>
> 跨课程连在这条机制的末端：Strang 的 linear algebra（线性代数）里，least squares 是一个纯几何问题——把 $y$ 做 projection（投影）到 $x$ 张成的列空间上，残差垂直于该子空间，normal equation（正规方程）就是"垂直"这条几何约束的代数翻译。几何路线不需要任何噪声分布假设，也不产生"倍数"这种概率量；它与本注的 MLE 路线在同一处汇合，汇合点正是那个二次型。区别在于：几何路线回答"最近点在哪"，这是恒等式；概率路线回答"这组参数有多可信"，这依赖 $\sigma$。两条线历史上几乎同时出现——Legendre 1805 年在彗星轨道的小册子里第一次印出平方和准则，Gauss 1809 年用正态误差为它辩护，那正是本注这座桥的原始版本。
>
> 所以下次看到有人对你说"就用平方损失吧"，该追问的不是平方好不好看，而是他默认了什么噪声。

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

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验证斜率的概率公式，验的不是代数，而是"协方差为什么恰好只能装下斜率"这件事。设模型 $Y = \theta_0 + \theta_1 X + W$，其中 $W$ 与 $X$ independent（独立）、$\mathrm{E}[W] = 0$。先做中心化：由 $\mathrm{E}[Y] = \theta_0 + \theta_1 \mathrm{E}[X]$ 与模型式相减，得 $Y - \mathrm{E}[Y] = \theta_1 (X - \mathrm{E}[X]) + W$。这一步把 $\theta_0$ 整个消掉了——截距只是把整条直线上下平移，平移不改变"围绕均值怎么波动"，所以它进不了 covariance（协方差）。
>
> 再代入算协方差：$\mathrm{E}\bigl[(X - \mathrm{E}[X])(Y - \mathrm{E}[Y])\bigr] = \theta_1 \mathrm{E}\bigl[(X - \mathrm{E}[X])^2\bigr] + \mathrm{E}\bigl[(X - \mathrm{E}[X])\, W\bigr]$。第二项为什么是零？因为 $W$ 与 $X$ 独立，而 $X - \mathrm{E}[X]$ 只是 $X$ 的函数，独立变量的函数仍独立，于是乘积的期望拆成期望的乘积，而 $\mathrm{E}[X - \mathrm{E}[X]] = 0$，整项消失。所以 $\theta_1 = \mathrm{cov}(X,Y)/\mathrm{var}(X)$，且分子里只留得下 $\theta_1 \mathrm{var}(X)$ 这一份。若把独立换成不独立，第二项就变成 $\mathrm{E}[(X - \mathrm{E}[X])W] \ne 0$，比值里立刻掺进别的东西——这是斜率估计出错的第一条通路，后面会算成具体数字。
>
> 卡点诊断：natural estimate（自然估计）这个词的准确含义是"把总体矩原样换成样本矩"。covariance 换成 $\frac{1}{n}\sum_i (x_i - \bar x)(y_i - \bar y)$、variance（方差）换成 $\frac{1}{n}\sum_i (x_i - \bar x)^2$，两者相除，$1/n$ 恰好约掉，剩下的正是讲义上那条 $\hat\theta_1$ 的最小二乘表达式。这不是两个公式碰巧同形，而是"总体恒等式加矩替换"这条通用流水线在二维情形下的产物：任何写成矩之比的参数，都能照这个样子得到一个估计量。
>
> 手算核对一遍。三点 $(0,1)$、$(1,2)$、$(2,4)$，$\bar x = 1$、$\bar y = 7/3$；离差乘积之和是 $(-1)\bigl(-\frac{4}{3}\bigr) + 0 \cdot \bigl(-\frac{1}{3}\bigr) + 1 \cdot \frac{5}{3} = 3$，离差平方和是 $1 + 0 + 1 = 2$，两者之比 $3/2 = 1.5$。若按矩估计的口径各除 $n = 3$，得到 $1$ 与 $2/3$，比值仍是 $1.5$——这就是 $1/n$ 约掉的具体样子。再验截距 $\hat\theta_0 = \bar y - \hat\theta_1 \bar x = 7/3 - 1.5 = 5/6 \approx 0.833$，与前面回归分支给出的数一致。
>
> 再补一句分母为什么是 variance：slope（斜率）的含义是"每单位 $x$ 的波动带来多少 $y$ 的波动"，所以要先量 $y$ 与 $x$ 同向波动的部分（分子），再按 $x$ 自身波动的尺度做归一化（分母）。若 $x$ 的散布整体放大一倍，分子放大一倍、分母也放大一倍，比值不变——这正是"斜率与单位无关"在概率层面的写法。顺带的观察：$\hat\theta_0 = \bar y - \hat\theta_1 \bar x$ 让两部分的误差在 $x = \bar x$ 附近相消得最彻底，所以拟合线在样本中心处最可信，越往外推越不可靠。
>
> 把"独立被破坏"这条通路算成数。设真实关系是 $Y = 2 X^{*} + W$，真实斜率 $2$；但 $X^{*}$ 测不到，只能观测 $X = X^{*} + E$，$E$ 是测量误差，$\mathrm{var}(X^{*}) = 1$、$\mathrm{var}(E) = 0.25$，$E$ 与 $X^{*}$ 独立。此时用观测到的 $X$ 做回归，交叉项不再为零，斜率退化为 $\theta_1 \cdot \frac{\mathrm{var}(X^{*})}{\mathrm{var}(X^{*}) + \mathrm{var}(E)} = 2 \cdot \frac{1}{1.25} = 1.6$，整整少了 $20\%$。这个现象叫 attenuation（衰减），它只会朝零偏、不会朝反方向偏；所以"斜率不显著"有时根本不是关系不存在，而是自变量测不准。
>
> 跨课程连接：把本式与 Lec 22 的 linear least mean squares（线性最小均方）斜率 $a = \mathrm{cov}(\Theta, X)/\mathrm{var}(X)$ 并排放看，公式完全同款，但回答的问题不同。那边 $X$ 与 $\Theta$ 都是随机变量，$a$ 是"用 $X$ 线性逼近 $\Theta$"的最优系数，本质是一个逼近问题的解；这边 $X$ 是给定的实验点、$\theta_1$ 是固定常数，$\hat\theta_1$ 是它的估计量，于是可以问"是否无偏、方差多大"。同一个表达式，一边是 projection（投影）系数，一边是统计估计，差别由"谁在随机"决定。顺带把下一页的想法接上：$y \approx \theta_0 + \theta_1 h(x)$ 正是 Lec 22 喂 $X, X^2, X^3$ 的回归版，换的是基，不换的是方法。
>
> 所以这条公式真正要记的不是符号，而是它成立的两个前提：$W$ 与 $X$ 独立、$W$ 的均值为零。前提一破，斜率就从"真参数"变成"掺了杂质的数"，而杂质的浓度恰好是方差之比。

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
\min_{\theta_0, \theta_1}\ \sum_{i=1}^{n} \bigl(y_i - \theta_0 - \theta_1 h(x_i)\bigr)^2 .
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

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 第一性原理）:**</span> 这两页是"交付清单 + 避坑指南"。清单回答跑完一次拟合该报告什么，指南回答哪些话不能从结果里读出来。清单逐项都能对上已学工具：各系数 $\theta_i$ 的 confidence interval（置信区间）就是 Lec 23 那台机器直接开过来用；standard error（标准误）是噪声标准差 $\sigma$ 的估计，报告系数时误差棒多粗全看它；$R^2$ 度量平方和里被模型吃掉的比例，越接近 $1$ 解释力越强。
>
> 先说 $R^2$ 为什么能当"解释力"。把 $y$ 的总波动拆成两块：模型预测值自身的波动，与 residual（残差）的波动。这两块在最小二乘解处恰好正交，于是平方和能直接相加，$\mathrm{SST} = \mathrm{SSE} + \mathrm{SSR}$。把 SST 除到左边，得 $R^2 = 1 - \mathrm{SSE}/\mathrm{SST}$，读作"残差占到原本波动的比例被扣掉之后还剩多少"。这个量本身只是算术，它与"回归有没有用"之间还隔着一层假设，下面会撞见。
>
> 用同一组三点 $(0,1)$、$(1,2)$、$(2,4)$ 把清单走完。$\mathrm{SST} = 16/9 + 1/9 + 25/9 = 14/3 \approx 4.667$，$\mathrm{SSE} = 1/6 \approx 0.167$，于是 $R^2 = 1 - (1/6)/(14/3) = 27/28 \approx 0.964$，数字很体面。standard error 按 $s^2 = \mathrm{SSE}/(n-2) = 0.1667$ 给出 $s \approx 0.408$，$\hat\theta_1$ 的标准误是 $s/\sqrt{S_{xx}} = 0.408/1.414 \approx 0.289$。取 $t_{0.975,1} = 12.706$，$95\%$ 的区间是 $1.5 \pm 12.706 \times 0.289$，即 $(-2.17,\, 5.17)$——这个区间把 $0$ 包在里面，意味着凭这三个点连"斜率不为零"都说不出口。$R^2 = 0.964$ 与"不显著"同时成立，正是本讲最该记住的对照：解释力高不等于证据足。
>
> 把同样结构重复四遍（$n = 12$、$S_{xx} = 8$、$\mathrm{SSE} = 0.667$），自由度升到 $10$，$s \approx 0.258$，标准误降到 $0.258/2.828 \approx 0.091$，$t_{0.975,10} = 2.228$，区间收窄成 $1.5 \pm 0.203$，即 $(1.297,\, 1.703)$，这才把 $0$ 甩开。区间宽度里 $\sqrt{n}$ 在分母、自由度躲在 $t$ 的取值里，两个因素一起发力，这解释了为什么"多攒点数据"比"把 $R^2$ 做高"更值钱。
>
> 避坑指南里最要紧的是最后一条：regression（回归）只能证明 association（关联），不能证明 causation（因果）。"受教育年限与收入正相关"的拟合背后，可能藏着同时驱动两者的遗漏变量（家庭背景、地域经济），把 $\hat\theta_1$ 读成"多读一年书带来多少收入"就是滥用；这正是 Lec 22 里选观测、选特征的暗面——没进模型的变量不会消失，只会把偏差塞进已经进模型的系数里。heteroskedasticity（异方差性）指噪声方差随 $x$ 变化，它破坏"等方差正态"的解读，让所有以 $s$ 为地基的区间整体失准；multicollinearity（多重共线性）指解释变量彼此高度相关，此时列空间几乎退化成同一块，系数在彼此之间来回摆动、单个系数无法解读，但整体预测值仍然稳。诊断与补救属于后续统计课程，本讲只立警示牌。
>
> 跨课程连接有两处。第一处在 Strang 的 18.065 matrix methods（矩阵方法）里：$R^2$ 本质是"$y$ 落在指定子空间里那部分能量占总能量的比例"，而 singular value decomposition（奇异值分解）把同一个能量占比思想推到极致——它不指定子空间，让数据自己挑方向，于是 $\sigma_1^2/\sum_i \sigma_i^2$ 告诉你"第一个方向吃掉了多少"。区别很关键：奇异值分解的占比随维数单调上升，是客观分解；$R^2$ 会随你往模型里塞变量而虚增，所以比较两个 $R^2$ 必须在同一套自变量上做。第二处在 CSAPP 第 6 章 cache（高速缓存）：报告"命中率从 $82\%$ 提到 $91\%$，所以优化有效"，与本页把高 $R^2$ 读成"模型对"是同一类滑坡——两者都只是可观测量变了，中间那个"因此"需要额外证据。
>
> 所以这两页的正确读法是：清单告诉你"能报告哪些数"，指南告诉你"这些数不许被翻译成什么话"，二者缺一，回归就会从工具变成话术。

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

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 假设检验的第一性原理只有一句：一切规则都归结为"在数据空间里画一块 rejection region（拒绝域）$R$"，此后所有性能指标都是 $R$ 的函数。这句之所以算原理而不算口号，是因为它把"怎么设计一个好检验"这个开放问题，压成了"怎么选一块集合"这个能逐点讨论的问题——你选的其实不是公式，而是数据的哪一部分会触发报警。
>
> 接着看两类错误的定义，tradeoff（权衡）的来处就透明了。$\alpha(R) = P(X \in R\,;\,H_0)$ 与 $\beta(R) = P(X \notin R\,;\,H_1)$ 是同一个集合在两个概率测度下的读数。把 $R$ 换成更大的 $R'$，第一个读数只会变大、第二个只会变小，因为 $H_0$ 下的质量被更多地圈进去、$H_1$ 下的质量被更少地漏在外面。这个单调性是集合包含关系的直接后果，不是巧合，也没法靠聪明设计绕开；能做的只是沿着这条单调曲线挑一个落点。
>
> 卡点诊断：注意那个分号。$\alpha(R) = P(X \in R\,;\,H_0)$ 是"在 $H_0$ 对应的模型下"取概率，不是 conditional probability（条件概率）——$H_0$ 不是随机事件，谈不上"给定 $H_0$ 发生"，这一点承接 Lec 23 开篇的世界观。分号就是经典统计给"按哪个模型算"立的规矩，它与竖线之间的差别，正是"参数不是随机变量"这句话的全部内容。这个符号读错，后面所有区间与阈值都会跟着错，而且错得很安静。
>
> 把 tradeoff 算成数。设 $H_0$ 下 $X \sim \mathrm{N}(0,1)$、$H_1$ 下 $X \sim \mathrm{N}(1,1)$，只观测一次，规则取 $X > \xi$ 即拒绝。$\xi = 1.645$ 时 $\alpha = 0.05$、$\beta = \Phi(0.645) \approx 0.741$，power（检出力）只有 $0.259$；把阈值降到 $1.0$，$\alpha$ 涨到 $0.159$、$\beta$ 掉到 $0.5$；把阈值抬到 $2.0$，$\alpha$ 收到 $0.023$、$\beta$ 却涨到 $0.841$，检出力只剩 $0.159$。三个点连成一条单调曲线：若硬要 $\beta = 0.1$，得让 $\xi = 1 - 1.282 = -0.282$，此时 $\alpha = 1 - \Phi(-0.282) \approx 0.611$——为把漏检压到一成，虚警要付六成，单次观测根本不划算。
> 把这条曲线画出来更清楚：横轴放 $\alpha$、纵轴放检出力 $1-\beta$，让 $\xi$ 从 $-\infty$ 一路扫到 $+\infty$，落点就沿曲线从 $(1,0)$ 滑向 $(0,1)$，这条曲线叫 operating characteristic（工作特性）。曲线的形状只由两个分布的分离度决定，分离度越大，曲线越往左上角鼓出去；但两个端点永远够不着，正如没有免费的能量。
>
> 真正的解法是加观测。取 $n$ 个 i.i.d.（独立同分布）样本，均值的标准差在两个模型下都缩到 $1/\sqrt{n}$，而两者仍相距 $1$，标准化之后的距离就是 $\sqrt{n}$。要保持 $\alpha = 0.05$、$\beta = 0.1$，需要 $\sqrt{n} \ge 1.645 + 1.282 = 2.927$，即 $n \ge 8.57$，取 $n = 9$：此时 $\sqrt{9} = 3$，$\beta = \Phi(1.645 - 3) = \Phi(-1.355) \approx 0.088$，检出力 $0.912$；若只取 $n = 8$，$\sqrt{8} \approx 2.828$，检出力回落到 $\Phi(2.828 - 1.645) = \Phi(1.183) \approx 0.882$。样本量是唯一能同时压低两类错误的旋钮，阈值只能搬动它们之间的分配比例。
>
> 跨课程连接：6.042J 里 partition（划分）的概念在这里是精确同构——$R$ 与它的补集把数据空间切成两块，互不相交、并为全集，与等价关系切分集合的方式一模一样。区别在于数学里任意划分都合法，检验里 $R$ 还要额外满足两条工程要求：对每个观测要能快速判定（所以通常取 $X > \xi$ 这类简单形状），并且在所有花得起 $\alpha$ 预算的集合里挑出力最大的那个（这是下一页 Neyman–Pearson 引理的活）。另一处锚点在 CSAPP 第 11 章 TCP 栈：checksum（校验和）也是一个 rejection region，差别在于它完全确定，只有"出错"一种可能，$\alpha$ 与 $\beta$ 无处安放；统计检验多出来的，正是"两种错法都可能"这一层。
>
> 所以本讲之后每个具体检验，骨子里都在回答同一个问题：这块 $R$ 该怎么画，才能在一个给定的 $\alpha$ 预算下把 $\beta$ 压到最低。

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

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 把 MAP 到 likelihood ratio test（似然比检验）的推导链完整验算一遍，重点不在代数，而在每一步折叠掉了什么。起点是 $P(H_1 \mid X = x) > P(H_0 \mid X = x)$，两边同除以 $P(X = x)$ 并展开 Bayes rule（贝叶斯法则，Lec 02 的老规矩），得 $P(X = x \mid H_1)P(H_1) > P(X = x \mid H_0)P(H_0)$。第一步折叠的是分母：同一个观测在两个假设下的后验共用同一个 $P(X = x)$，比大小可以整块丢掉。
>
> 再两边同除以 $P(X = x \mid H_0)P(H_1)$，先验被搬到了阈值里：$\frac{P(X = x \mid H_1)}{P(X = x \mid H_0)} > \frac{P(H_0)}{P(H_1)}$。这一步折叠的是"四个量"——左边只剩数据说了什么，右边只剩出发时信什么，两团东西分居不等号两侧。这个分离不是为了好看：若数据项与先验项混在一起，使用者每改一次先验，你都得把整张数据表重算一遍；分离之后，左边可以在数据到手那刻算完，阈值是事先谈妥的常量，判定退化成一次比较。
>
> 更深一层的意义：似然比是一个 sufficient statistic（充分统计量），它把整个数据向量 $x$ 压成一个标量，却不损失任何关于"哪个假设为真"的信息。这正是上面那句"退化成一次比较"之所以成立的根据——压缩是无损的。任何高维数据进了这条流水线，出来都只剩一个数。
>
> 非贝叶斯版的"去先验化"动作很轻：既然 $\theta$ 不是随机变量、没有 $P(H_i)$ 可说，就把右侧换成自由参数 $\xi$，事后按"控制 $\alpha$"来标定。结构一个字没改，只是右边那个数从"先验比"变成了"设计者手里的旋钮"。
>
> 命名模板——"似然比拍板法"：无论数据维度多高，先把全部证据压成一个数（两个模型下数据出现概率之比），再与阈值比较。这条模板的可复用性在于，它把"设计一个检验"拆成两件独立的事：选比值（由两个模型决定，几乎没有余地），与选阈值（由 $\alpha$ 预算决定，是唯一的自由度）。
>
> 算成数。抛十次得七次正面，$H_0$ 说 $p = 0.5$、$H_1$ 说 $p = 0.8$，似然比是 $0.8^7 \cdot 0.2^3 / 0.5^{10} = 0.0016777/0.0009766 \approx 1.718$；阈值若取先验比 $1$，判决倒向 $H_1$。换到非贝叶斯口径标定阈值：拒绝域取 $k \ge 7$ 时 $\alpha = 176/1024 \approx 0.172$、$\beta \approx 0.121$，检出力 $0.879$；若把预算卡死成 $\alpha \le 0.05$，就只能退到 $k \ge 9$，此时 $\alpha = 11/1024 \approx 0.0107$，而 $\beta \approx 1 - (0.268 + 0.107) = 0.625$，检出力掉到 $0.375$——预算与检出力之间的汇率，一次就读出来了。
>
> 卡点预警：离散分布下 $\alpha$ 取不到连续值，只能落在网格上。$k \ge 8$ 给 $\alpha = 56/1024 \approx 0.0547$，比 $0.05$ 大那么一点点；$k \ge 9$ 给 $\alpha \approx 0.0107$，又小得可惜。所谓"选 $\xi$ 使 $\alpha = 0.05$"在连续模型里总能做到，在离散模型里往往只能做到"不超过"。补这个缝的办法（随机化判定）本课程不展开，但它存在这件事你该记住，别以为自己的检验写错了。
>
> 跨课程连接放在 CSAPP 第 11 章 TCP 栈最自然：checksum（校验和）判定也是同一条流水线——收到分组先算一个标量，再与校验字段比，不等就丢。区别在于它是确定性的：阈值两侧只有"一定对"和"一定错"，没有 $\alpha$ 与 $\beta$ 两种错法的位置；似然比多出来的那一层，是因为它的标量本身是随机变量。历史上一句：这套"先固定虚警预算、再最大化检出力"的框架，是 Neyman 与 Pearson 在 1933 年 Philosophical Transactions 上那篇文章立下的，标题直译是"论统计假设的最有效检验问题"，那一年之后检验才有"两类错误"这套词汇。
>
> 所以阈值 $\xi$ 的标定方向永远只有一个：固定 $P(\text{reject}\,;\,H_0) = \alpha$，再看 $\beta$ 还剩多少；两类错误被同一个 $\xi$ 联动，不存在同时最小化两者的免费午餐。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
