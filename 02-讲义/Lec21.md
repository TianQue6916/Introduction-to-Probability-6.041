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

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这一讲要回答的设计问题是：为什么 statistics（统计学）没有唯一正确答案，而概率论有。这条边界不钉死，后面每个公式都会被误读成"求唯一真理的算法"。
>
> 机制要从两门学科各自缺什么说起。概率论是 deductive system（演绎系统）：model（模型）一旦给定，任何表述清晰的问题都有唯一答案，因为答案早已编码在公理与分布里，推导只是把已有信息换一种排列。统计学的方向相反：数据固定，model（模型）里却留着一个 free parameter（自由参数），你还得额外挑一个 loss function（损失函数）来定义什么叫"好"。两个自由选择叠加，解自然不唯一。教材说它 involves an element of art，这不是修辞而是逻辑事实：art 占据的位置，恰好等于"未被数据决定的那部分自由度"。所以一个"最优估计"的说法永远要补两个尾巴——关于哪个参数的哪个损失，否则这句话没有真值。
>
> 算一遍就知道两个自由度各自值多少。设真实支持率 $\theta$ 未知，民调抽 $n = 1000$ 人，观测到 520 人支持。frequentist（频率派）直接用样本比例 $0.52$，标准误 $\sqrt{0.52 \times 0.48 / 1000} \approx 0.0158$，九十五百分位区间约 $[0.489, 0.551]$。Bayesian（贝叶斯派）取均匀 prior（先验）$\mathrm{Beta}(1,1)$，posterior（后验）就是 $\mathrm{Beta}(521, 481)$，均值 $521/1002 \approx 0.520$，与 $0.52$ 几乎重合。差别藏在样本量里：把 $n$ 缩到 4、观测 3 人支持，frequentist（频率派）仍报 $0.75$，Bayesian（贝叶斯派）的 posterior（后验）$\mathrm{Beta}(4,2)$ 均值是 $0.667$。可见 prior（先验）的等效权重约为两次虚拟观测，占比 $2/(n+2)$，$n$ 大就被数据淹没，$n$ 小才开口说话。这条刻度线解释了两派为何在小样本上吵、在大样本上握手。
>
> 六个应用之所以值得先扫一遍，是因为它们最后会塌缩成同一个数学形状。民调与医学试验的未知量是一个比例，观测是计数；信号处理里未知量是一条轨迹的系数，观测是带噪采样；Netflix 竞赛的 matrix completion（矩阵补全）里未知量是整张评分矩阵的缺失条目，观测是少量已评分格位，它之所以可解，靠的是一个 low rank（低秩）的 prior（先验）——假设每个人的品味由少数几个隐因子决定，未知格位就能借相似用户的信息补出来，这正是 Strang 的矩阵分解在统计里的化身。
>
> 跨课程连接给到 CSAPP 第 6 章。cache（缓存）的 locality（局部性）假设，本质就是一个硬编码的 prior（先验）：硬件赌"刚用过的地址还会被再用"，命中率就是这份信念的回报。一旦访问模式违背 locality（局部性）——比如顺序扫一遍 1 GB 的数组——cache（缓存）全线 miss，恰似 prior（先验）错位时 posterior（后验）被整个拉偏。区别在于可更新性：cache（缓存）的信念写死在 replacement policy（替换策略，如 LRU 与组相联映射）里，运行期改不了；贝叶斯 prior（先验）是一份显式写下的分布，观测到手就按法则改写成 posterior（后验）。工程语言里，"不可更新的信念"叫 policy（策略），"可更新的信念"叫 inference（推断），这条分界线贯穿整门课。
>
> 收束：本讲与下一讲把上述六类应用全压成同一个形状——未知量 $\Theta$、观测 $X$、posterior（后验）——而开头那句俏皮话真正的分量在于：你从此有两套语言，一套描述世界怎么运行，一套描述看到证据之后该相信什么，且第二套必须显式交代自己的 prior（先验）。
>
> 顺手补一条考据上的警告：那句"被统计数字打动"的话常被挂在 Wilde（王尔德）名下，但引语考据站 Quote Investigator 追下来只找到转述链条，2007 年才经由一档电视节目挂到他头上，Wilde 伪引档案也把它列为存疑——按本讲的语法说，这是一条 provenance（出处）不明的断言，却借到了一个看起来很有权威的 prior（先验）标签。这个例子提醒你：对引语用贝叶斯法则，和对数据用贝叶斯法则，是同一种谨慎。

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

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 前后讲回指）:**</span> 这条卡点的真正名字不是"两派算法不同"，而是"probability（概率）这个词在两派嘴里指的不是同一个东西"。先把这一点拆开，后面所有争吵都会变成可预测的分歧。
>
> 机制分三层。第一层，frequentist（频率派）的概率是相对频率：把同一实验重复无穷次，事件出现的比例。这个定义要求实验可重复，而未知参数 $\theta$ 是那个世界的固定常量——电子质量今天多少明天还是多少，"重复测量"重复的是测量动作，不是质量本身。所以 frequentist（频率派） 拒绝写 $p(\theta)$，那个句子在他们语法里不合法。第二层，Bayesian（贝叶斯派）的概率是信念强度：它衡量的是你对某个命题的相信程度，可以针对一次性的、不可重复的事件。既然 $\theta$ 值不值得信也是一个命题，它就可以带 probability（概率），且这份信念能被数据按法则改写。第三层，后果：同一句"九十五百分位"，两派给的是完全不同的对象——Bayesian（贝叶斯派）说的是"这个区间包含 $\theta$ 的 posterior（后验）概率是 0.95"，frequentist（频率派）说的是"若无限次重复抽样，95% 的区间会盖住 $\theta$"，而对手上这一个区间，他们不能下任何断言。
>
> 手算一个例子把差别钉住。设电子质量 $\theta$ 用某仪器测两次，观测 $X_i = \theta + W_i$，噪声标准差 $\sigma = 1$（单位任意），读数 9.11 与 9.13。frequentist（频率派）只给点估计 $\hat{\theta} = 9.12$，标准误 $1/\sqrt{2} \approx 0.707$，而它不能宣称"$\theta$ 落在 $9.12 \pm 1.4$ 内的概率是 0.95"。Bayesian（贝叶斯派）若取 prior（先验）$N(9.11, 1)$，则 precision（精度，即方差的倒数）直接相加：prior（先验）精度 1，两次观测精度各 1、合计 2，posterior（后验）精度 3，posterior（后验）均值 $= (9.11 \times 1 + 9.12 \times 2)/3 \approx 9.1167$，标准差 $1/\sqrt{3} \approx 0.577$。注意两件事：均值被 prior（先验）往 9.11 拉了一点，不确定度从 0.707 缩到 0.577。这就是"信息叠加"的具体算术，也是为什么测量仪器越多次，prior（先验）的影响越被稀释。
>
> 回指上一段课程：Lec 02–03 里你算"检测呈阳性、真患病概率多少"时，其实已经在做 Bayesian（贝叶斯派）的事——把"患病"当成带 prior（先验）的二值假设，用 Bayes rule（贝叶斯法则）从 likelihood（似然）反推 posterior（后验）。本讲只是把那个二值假设升级成一般随机变量 $\Theta$，把一次观测升级成观测向量，语法一字未改。
>
> 跨课程连接给到 6.042J。布尔代数只有两个真值 0 与 1，命题或者真或者假；概率论把真值扩展成 $[0,1]$ 上的连续权重，这是第一次让渡确定性；Bayesian（贝叶斯派）再把这种权重用到"关于参数的断言"上，等于第二次让渡——连"世界有一个确定答案"这件事也让渡了一部分，换成"我手上有一份可更新的信念分布"。三级台阶形状一致，区别在于让渡的对象：布尔代数让渡的是"部分为真"，经典概率让渡的是"未知但固定"，Bayesian（贝叶斯派）让渡的是"未知本身可以是随机的"。
>
> 一句话判据：当未知量是物理常量、且实验可重复时，frequentist（频率派）的语言更省心；当未知量本身是从某个总体里抽出来的一个样本（每个用户的品味、每个格位的真实评分），prior（先验）就有实打实的内容可写，Bayesian（贝叶斯派）反而更自然。教材第 9 章补上另一半工具箱，届时你会发现 max likelihood（最大似然）正是"prior（先验）取平坦"这一特例下的极限。

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

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 幻灯片上那三个式子不是三个公式，而是同一个公式的四次排版。要看清这件事，得先问：Bayes rule（贝叶斯法则）到底依赖哪两条最基础的事实？
>
> 只依赖两条。第一条，联合分布可以写成"先写 prior（先验）、再写条件"的连乘：$p_{\Theta,X}(\theta, x) = p_\Theta(\theta)\, p_{X|\Theta}(x \mid \theta)$，这条在离散与连续情形下逐字相同，因为它是概率的乘法定义，与变量取值空间无关。第二条，边缘化就是"把不关心的那个变量抹掉"，抹的方式是对它求和或积分。两条合起来，$p_{\Theta|X}(\theta \mid x) = p_{\Theta,X}(\theta, x) / p_X(x)$，两次代入就得到幻灯片上的形状。于是"变装"只发生在两个位置：把 probability mass function（概率质量函数）换成 probability density function（概率密度函数），把求和符号换成积分符号，其余语法一字不动。
>
> 反过来若不换会怎样失败，这才是关键。连续情形下若硬用求和，每个单点的概率都是零，分子分母同时为零，posterior（后验）变成 $0/0$，整个式子无定义；若硬用离散的归一化，又得不到积分为 1。所以"两处替换"不是风格选择，而是让除法有意义的最低条件。教材 p.413 把它列成 $2 \times 2$ 的四格，就是为了让你一眼看出：格与格的差别只在"哪个变量离散、哪个连续"。
>
> 手算第三格——$\Theta$ 离散、$X$ 连续，也就是 prior（先验）是 pmf、likelihood（似然）是 pdf 的混合情形。取 $\Theta \in \{1, 2\}$ 各占一半，$X \mid \Theta \sim N(\Theta, 1)$，观测到 $x = 2$。标准正态密度在 1 与 0 处的值分别约 $0.24197$ 与 $0.39894$，于是联合权重 $0.5 \times 0.24197 = 0.120985$ 与 $0.5 \times 0.39894 = 0.19947$，边缘 $p_X(2) = 0.320455$。posterior（后验）$p_{\Theta|X}(2 \mid 2) = 0.19947 / 0.320455 \approx 0.6224$，另一格 $0.3776$，两者相加为 1。注意分母这个数没有任何概率含义，它只是让两个后验权重加起来等于 1 的缩放因子——这正说明归一化常数不携带关于 $\theta$ 的信息。
>
> 拓展一层：为什么有的 prior（先验）让后验仍旧是同一族分布？因为 likelihood（似然）的核是 $\theta^x (1-\theta)^{n-x}$，$\mathrm{Beta}(a,b)$ 的 prior（先验）核是 $\theta^{a-1}(1-\theta)^{b-1}$，两者相乘等于指数相加，积分只剩一个归一化常数，不改变形状。这类配对叫 conjugate prior（共轭先验），它让"更新"退化成"参数作加法"。把所有具备这种封闭性的分布写成统一形式 $\exp(\eta \cdot T(x) - A(\eta))$，就得到 exponential family（指数族）：$\eta$ 是自然参数，$T(x)$ 是 sufficient statistic（充分统计量，即概括数据所需的全部信息），$A(\eta)$ 只是保证积分为 1 的归一化项。这个写法的好处是：任何指数族成员配上共轭 prior（先验），后验参数都只做加法，不需要碰积分。
>
> 跨课程连接给到 6.006。写代码时"对数组求和"是一个有限循环，每一项都真实存在，结果精确；换成积分后没有"全部项"可加，只能采样 $N$ 个点做数值近似，左端点矩形法的误差是 $O(1/N)$，梯形法能到 $O(1/N^2)$。语法上 $\sum$ 与 $\int$ 平行，代价上却一个是精确的、一个是逼近的——这条区别解释了为什么本讲后面的公式都停在"写出 posterior（后验）"这一步，而不真去算那个积分。若 posterior（后验）连闭式都写不出，工程上就改用采样近似，这条路叫 MCMC（马尔可夫链蒙特卡洛：构造一条平稳分布恰好是后验的随机游走链，从链上取样当样本用），它与 6.006 里随机化快排同属一个思路——用随机性换可计算性，区别是随机化快排赌的是运行时间，MCMC（马尔可夫链蒙特卡洛） 赌的是输出分布。
>
> 收束：四个版本、共轭配对、MCMC（马尔可夫链蒙特卡洛） 都在同一件事上做文章——把"先验乘似然再归一"这套代数保持住，只在"能否算出那个积分"上让步。

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

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 硬币例的价值不在算出一个 posterior（后验），而在于它暴露了一条更硬的事实：当 prior（先验）与 likelihood（似然）属于同一族时，更新退化成"参数作加法"，整个数据集被压成两个整数。
>
> 机制分四步拆。第一步，$n$ 次独立投掷是 iid（独立同分布），likelihood（似然）因此是 $n$ 个因子的乘积；又因为每次只有"正/反"两种结果，乘积里只剩 $\theta$ 的幂与 $(1-\theta)$ 的幂，即 $\theta^x(1-\theta)^{n-x}$。第二步最要紧：这个核只认"正面几次、反面几次"，完全不认出现次序——先正后反与先反后正给出同一个 likelihood（似然）。这说明在 Bernoulli（伯努利） 模型下，排列顺序不携带关于 $\theta$ 的任何信息，$2^n$ 条序列被压成 $n+1$ 个等价类，类的标号就是 $x$。第三步，若 prior（先验）取 $\mathrm{Beta}(a,b)$，其核 $\theta^{a-1}(1-\theta)^{b-1}$ 与 likelihood（似然）相乘，指数直接相加，形状仍是 Beta（贝塔），参数变成 $(a+x,\ b+n-x)$。第四步，归一化常数由 Beta（贝塔） 函数给出，$\int_0^1 \theta^x(1-\theta)^{n-x}d\theta = x!\,(n-x)!/(n+1)!$，于是完整 posterior（后验）为 $(n+1)\binom{n}{x}\theta^x(1-\theta)^{n-x}$；那个组合数其实是在替每一类次序"数个数"。
>
> 再往下一层，posterior（后验）均值可以写成两个东西的加权平均：$\frac{a+x}{a+b+n} = \frac{a+b}{a+b+n}\cdot\frac{a}{a+b} + \frac{n}{a+b+n}\cdot\frac{x}{n}$，即"prior（先验）均值"与"样本比例"按虚拟样本量 $a+b$ 与真实样本量 $n$ 分权重。这个式子解释了前面所有关于先验强度的讨论：先验不是一道开关，而是一个可精确计量的砝码。
>
> 数字核对一遍。prior（先验）取 $\mathrm{Beta}(1,1)$（均值 $0.5$、虚拟样本量 2），观测 3 正 1 反，权重是 $2/6$ 与 $4/6$，均值 $= 0.5 \times (1/3) + 0.75 \times (2/3) \approx 0.6667$，与 $\mathrm{Beta}(4,2)$ 的 $4/6$ 一致。MAP（最大后验）为何是 $0.75$ 而不是均值？因为 Beta（贝塔） 密度的驻点在 $(a-1)/(a+b-2) = 3/4$，它把先验也当成两次观测来数人头。方差 $ab/[(a+b)^2(a+b+1)] = 8/(36 \times 7) \approx 0.0317$，标准差约 $0.178$。若接着再观测 2 个正面，posterior（后验）变 $\mathrm{Beta}(6,2)$，均值 $0.75$；一次性观测 5 正 1 反得到的也是 $\mathrm{Beta}(6,2)$——两条路径同终点，因为加法可交换，这就是 streaming（流式）更新的合法性来源：数据可以一条一条喂，不必攒齐。
>
> 还有一层工程上的追问：prior（先验）的参数 $a,b$ 从哪来？若手上有一万个硬币、每个都投过几次，就可以用这一万个数据先估出"硬币总体的偏置分布"，把它当成每个硬币的 prior（先验），这套做法叫 empirical Bayes（经验贝叶斯）。它省掉了主观设定，代价是同一批数据被用了两次——先估先验，再算 posterior（后验），于是区间会偏窄，这是它必须付的账。
>
> 两个卡点。其一，均匀 prior（先验）不是"无信息"的免罪金牌：它对 $\theta$ 均匀，但对 odds（赔率）$\theta/(1-\theta)$ 就不均匀，说明"我不知道"这句话本身依赖你用什么坐标度量无知，选它也要给理由。其二，"两个整数就够"是模型假设的产物，不是数据的本性：若硬币有惯性（正后面更容易再出正），likelihood（似然）不再是乘积，sufficient statistic（充分统计量）立刻从两个计数膨胀成四个转移计数（正转正、正转反、反转正、反转反），参数也从一维变二维。所以看到漂亮的一维共轭，先问模型替你做掉了哪些假设。
>
> 跨课程连接给到 CSAPP 第 6 章。cache（缓存）把一整段 address（地址）历史压成 tag、valid bit 与若干 LRU 位；$\mathrm{Beta}(a,b)$ 把 $2^n$ 条投掷序列压成两个整数。两者都是"只保留够用的摘要"，但判据不同：cache（缓存）的摘要必须能精确重建 address（地址），tag 比对不能有损；统计的 sufficient statistic（充分统计量）只要求 likelihood（似然）形状不变，允许丢弃信息。工程摘要追求可逆，统计摘要只追求"不改变结论"。
>
> 收束：本页之后所有"漂亮"的共轭配对都长这样——先验一套参数，数据贡献两个计数，后验做一次加法。

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

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 验证）:**</span> 这里要回答的设计问题是：柜台上明明摆着完整的 posterior（后验），为什么还要再挑一个数？答案是——估计器不是数据的函数，而是 loss function（损失函数）的函数。
>
> 机制先讲清"压缩必有损失"这句。posterior（后验）是对未来的全部信息，而任何一个动作只接受一个数，于是信息必须被压掉。压法不同，压掉的部位不同，代价也不同。所以"哪个估计更好"这个问题在没指定 loss function（损失函数）之前根本没有真值，正如没指定度量衡就争论长短。
>
> 三种常见 loss function（损失函数）各配一个答案，而且每个答案的证明骨架是同一个模板。0-1 loss（零一损失）只问对错：$\mathrm{E}[\mathbf{1}(\hat\theta \ne \Theta) \mid X = x] = 1 - p_{\Theta|X}(\hat\theta \mid x)$，对这个式子关于 $\hat\theta$ 取最小，等价于取 posterior（后验）的最大点，这就是 MAP（最大后验）估计。squared loss（平方损失）问偏差多大，答案是 conditional expectation（条件期望），证明留到下一页。absolute loss（绝对损失）问偏差多远，答案是 conditional median（条件中位数）。模板只有一句话：逐点最优即全局最优——若对每个 $x$ 都有 $a(x) \le b(x)$，则由期望保序得 $\mathrm{E}[a(X)] \le \mathrm{E}[b(X)]$。所以只要能对每个固定的 $x$ 把局部问题解掉，全局最优自动到手，不需要任何关于 $X$ 分布的假设。
>
> 用数字验证，取 posterior（后验）为 $\Theta = 0$ 占 $0.4$、$\Theta = 1$ 占 $0.6$。MAP（最大后验）判 $1$，出错概率 $0.4$；若判 $0$，出错概率 $0.6$，确实更差。conditional expectation（条件期望）是 $0 \times 0.4 + 1 \times 0.6 = 0.6$——注意它根本不在取值集合 $\{0,1\}$ 里，它不是"答案"而是"平均"。conditional median（条件中位数）在这里不唯一：任何 $t \in [0,1]$ 都满足两侧各占一半，于是绝对损失下有一整条线段的解。三个 loss function（损失函数）给出三个不同的对象，其中一个还不唯一，这就是"先声明损失"的必要性。
>
> 再加一个反直觉的算术：若 posterior（后验）在 $2$ 与 $10$ 各占一半，均值 $6$ 落在密度几乎为零的谷底，看上去荒谬。但按 squared loss（平方损失）算风险：猜 $6$ 的期望平方误差是 $0.5 \times 16 + 0.5 \times 16 = 16$，猜 $2$ 的是 $0.5 \times 0 + 0.5 \times 64 = 32$。谷底那个答案仍然赢一倍。若换成 0-1 loss（零一损失）要求落在真实峰附近，猜 $6$ 就几乎必错。所以"荒谬"是相对于损失说的，不是相对于分布说的。
>
> 顺带钉一个接口：若把 prior（先验）取成均匀分布，posterior（后验）与 likelihood（似然）只差一个常数，此时 MAP（最大后验）退化成 max likelihood（最大似然）。这正是教材第 9 章那套方法的入口——所谓"经典派不用先验"，准确的说法是"用了均匀先验却不再声明"，而均匀先验未必真的无信息，这一点上一讲已经算过账。
>
> 跨课程连接给到 CSAPP 第 4 章的 branch prediction（分支预测）。处理器对每个跳转指令赌方向，赌错的代价是流水线冲刷，代价大小与"偏了多少"无关，只与"错没错"有关——这是标准的 0-1 loss（零一损失），所以正确做法就是取最可能方向，也就是 MAP（最大后验），两位饱和计数器学的正是"哪个方向后验更大"。区别有两处：branch predictor（分支预测器）只能取两个值，假设空间天然离散；而它是硬件在线更新（表项随执行流改写），贝叶斯则是按法则一次性改写 posterior（后验）再取最大点。若把误预测代价改成与偏差成正比，最优策略立刻从"赌多数"变成"取条件期望"，这也是本讲的分水岭。
>
> 收束：本页末行那句提醒不是修辞——只要你肯写下 loss function（损失函数），它就会逼你说清"到底怕哪种错"，而估计器只是这个回答的算术后果。

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

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 这一页要回答的设计问题是：在没有任何观测时，"最好的猜测"是什么？答案是 mean（均值），而这个最好的猜测所对应的均方误差恰好等于 variance（方差）——于是 variance（方差）从一个描述性的数字，升格为"你必须支付的最低代价"。
>
> 机制靠一行配方，但配方不是技巧而是定义的反用。把偏差拆成两段：$\Theta - c = (\Theta - \mu) + (\mu - c)$，其中 $\mu = \mathrm{E}[\Theta]$。平方展开得 $(\Theta-\mu)^2 + 2(\mu-c)(\Theta-\mu) + (\mu-c)^2$，取期望时交叉项变成 $2(\mu-c)\,\mathrm{E}[\Theta-\mu]$，而 $\mathrm{E}[\Theta-\mu] = 0$ 正是 mean（均值）的定义，于是交叉项整段消失，剩下 $\mathrm{Var}(\Theta) + (\mu-c)^2 \ge \mathrm{Var}(\Theta)$，等号当且仅当 $c = \mu$。关键在于解释为什么必须先减掉 $\mu$：因为只有"中心化后的变量期望为零"这一条能保证交叉项消失，而任何别的中心点（比如中位数）都不会让 $\mathrm{E}[\Theta - c_0] = 0$ 成立，交叉项就消不掉，配方就失败。这就是平方损失与 mean（均值）绑定的根本原因——不是习惯，是等式逼出来的。
>
> 手算一个能把直觉打醒的例子。设 $\Theta$ 以各一半的概率取 $0$ 与 $10$，则 $\mu = 5$、$\mathrm{Var}(\Theta) = 25$。取 $c = 5$ 时均方误差 $25 + 0 = 25$；取 $c = 0$ 时 $25 + 25 = 50$；取 $c = 4$ 时 $25 + 1 = 26$。注意 $c = 0$ 这个策略有一半时间完全猜对（误差为零），听上去很聪明，但它的均方误差是 $50$，比"永远不准"的 $5$ 差一倍。原因在平方：错的时候偏差是 $10$，平方后是 $100$，摊到两次样本上就是 $50$，把"猜对的那次"白送的收益全吃掉了。这条算术是 squared loss（平方损失）的核心性格——它极度厌恶大偏差，宁可接受"每次都差一点"，也不接受"偶尔差很多"。
>
> 平方损失还有一个容易漏掉的性质：代价对称。若低估的代价是高估的两倍，最优常数就不再是 mean（均值），而是一个加权平均。设 $\Theta$ 取 $0$ 与 $10$ 各一半，低估的权是 $2$、高估的权是 $1$，则最优 $c = (2 \times 0.5 \times 0 + 1 \times 0.5 \times 10)/(2 \times 0.5 + 1 \times 0.5) = 5/1.5 \approx 3.33$，明显低于 $5$。这说明"用均值猜"本身也是对称假设的产物，一旦代价不对称，配方要重做。
>
> 为什么默认用 squared loss（平方损失）而不是别的？三条理由都可验证：其一可微，能对 $c$ 求导并令导数为零，这是唯一能让"最优"有闭式解的性质；其二可分解，下一节会看到总方差被拆成"组内期望方差"加"组间方差"，这正是配方在条件宇宙里的复演；其三与高斯噪声天然配套，因为 normal（正态）likelihood（似然）取对数之后恰好是平方，最大似然与最小二乘于是同一件事。若换成 absolute loss（绝对损失），最优解变成 conditional median（条件中位数），它对离群值更稳健；若换成 0-1 loss（零一损失），最优解变成 mode（众数）。三种损失对应三个统计量，一个都不"更正确"。
>
> 跨课程连接给到 Strang 的线性代数，而这次的对应严格到可以逐项核对。least squares（最小二乘）要解 $\min_x \|Ax - b\|^2$，normal equation（正规方程）是 $A^TAx = A^Tb$。把矩阵取成只有一列全 $1$ 的特殊情形 $A = \mathbf{1}_{m\times 1}$，未知量 $x$ 退化成一个标量 $c$，此时 $A^TA = m$、$A^Tb = \sum_i b_i$，解得 $c = \frac{1}{m}\sum_i b_i$，正是样本均值。也就是说，本页说的"常数最优猜测是 mean（均值）"，就是最小二乘在"只允许拟合常数"这一退化子空间里给出的答案。区别在于语言：Strang 那边目标是确定向量、运算是求和、几何解释是投影到列空间；这边目标是随机变量、运算是取期望、几何解释是投影到常数张成的子空间。骨架完全相同，只是把"求和取平均"换成了"期望取平均"。
>
> 收束：本页把"无知时该猜什么"这件事彻底解决了，剩下的全部问题是——有了观测之后，该把哪个空间拿来投影。

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

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 跨课程连接）:**</span> 这一页要建立的是本讲最可复用的一条模板：**逐点成立 → 取期望 → 全局成立**。它的作用是把一个"在所有函数里挑最优"的无限维问题，拆成一族"对每个固定的 $x$ 挑一个数"的一维问题。
>
> 机制的第一步是承认条件化没有改变任何代数结构。给定 $X = x$ 之后，$\Theta$ 在条件宇宙里仍然是一个随机变量，有自己的 mean（均值）与 variance（方差），上一页的配方可以逐字重演：最优常数是条件均值，最优值是条件方差。第二步是承认这一步只对单个 $x$ 有效，得到的东西是 $c^*(x) = \mathrm{E}[\Theta \mid X = x]$，它是一个函数而不是常数。第三步才是关键：对每个固定的 $x$ 都有 $a(x) \le b(x)$，而期望保序，于是 $\mathrm{E}[a(X)] \le \mathrm{E}[b(X)]$。这条保序性不需要独立性、不需要同分布，只需要两个函数在每一点上可比，所以它把"逐点"升级为"全局"时一点额外代价都没付。
>
> 为什么要绕这一道？因为直接在函数空间里求最优要解变分问题，而逐点化把它拆成连续多个标量问题，每个都只有一行配方。这与物理学里"把整体作用量逐点最小化"是同一种降维手法：无限多个自由度之间没有耦合时，就一个一个解。
>
> 手算一个能同时验证公式和解的正例。设 $\Theta \in \{0, 1\}$ 各占一半，观测经过 binary symmetric channel（二进制对称信道）：$X = \Theta \oplus W$，$W$ 以 $\epsilon = 0.1$ 的概率取 $1$。当 $X = 1$ 时，$\mathrm{E}[\Theta \mid X = 1] = \frac{0.5 \times 0.9}{0.5 \times 0.9 + 0.5 \times 0.1} = 0.9$；两点分布的方差是 $p(1-p) = 0.09$。由对称性，$X = 0$ 时条件均值是 $0.1$，条件方差同为 $0.09$。于是估计器 $g(X) = \mathrm{E}[\Theta \mid X]$ 的均方误差是 $\mathrm{E}[\mathrm{Var}(\Theta \mid X)] = 0.09$，而常数估计器 $g \equiv 0.5$ 的误差是 $\mathrm{Var}(\Theta) = 0.25$，降幅 $64\%$。核对方差分解：$\mathrm{Var}(\mathrm{E}[\Theta \mid X])$ 的两个取值是 $0.9$ 与 $0.1$，各半，方差 $= 0.5 \times 0.16 + 0.5 \times 0.16 = 0.16$，而 $0.09 + 0.16 = 0.25$ ✓，正好把总方差切成"观测解释掉的"与"消不掉的噪声底"。
>
> 这个例子还能顺手钉住"损失决定估计器"。若换成 MAP（最大后验）判决，错概率是 $0.1$；但同一个 MAP（最大后验） 估计器的均方误差也是 $0.1$，比条件期望的 $0.09$ 差。两个损失各选各的赢家：0-1 loss（零一损失）要的是"尽量完全正确"，squared loss（平方损失）要的是"平均偏差小"，而后者允许你永远差一点点也别偶尔差很多。
>
> 跨课程连接给到 Strang 的 projection（投影）。把"所有 $g(X)$"收成一个集合，配上 inner product（内积）$\langle U, V \rangle = \mathrm{E}[UV]$，它就构成一个 subspace（子空间）；$\mathrm{E}[\Theta \mid X]$ 正是 $\Theta$ 在该 subspace（子空间）上的 orthogonal projection（正交投影），判据是误差与子空间内每个元素正交。这个判据可以手算验证：取 $h(X) = \mathbf{1}(X = 1)$，则 $\mathrm{E}[(\Theta - g(X))h(X)] = 0.5 \times 0.9 \times (1 - 0.9) + 0.5 \times 0.1 \times (0 - 0.9) = 0.045 - 0.045 = 0$ ✓。区别在维度：Strang 那里子空间是有限维、内积是点积；这里是无限维可测函数空间、内积是期望。但"最近点 ⟺ 误差正交"这一条完全一样。
>
> 这条模板的适用面比估计宽得多。凡属"对每个样本点独立决策"的问题，都能逐点化：把实数压成 $k$ 个电平的 quantizer（量化器）设计，逐点选最近的合法电平，最优性证明与此处一字不差；判决问题里逐点选 posterior（后验）最大的假设，也是同一模板的 0-1 版本。它们的共同前提只有一个——决策的代价不跨样本耦合，一旦代价允许"跨点联动"，逐点化立刻失效，就得回到真正的变分问题。
>
> 最后一个卡点：$\mathrm{E}[\Theta \mid X]$ 是随机变量，$\mathrm{E}[\Theta \mid X = x]$ 是数，符号只差一个等号，含义差一整个宇宙，混写会让后面所有推导失义。

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

> <span style="color:#1e8449;">**[note] Note（译者注，跨课程连接 + 前后讲回指）:**</span> 这一页只有一句话，但它是全讲的转折点：多观测在数学上毫无新意，在计算上却是一次维度爆炸。幻灯片那句 hard to compute/implement 不是谦虚，是对工程现实的精确描述。
>
> 机制先拆清楚。理论上把条件化从 $X = x$ 换成向量 $(X_1, \ldots, X_n) = (x_1, \ldots, x_n)$ 之后，最优估计器仍是 $\mathrm{E}[\Theta \mid X_1, \ldots, X_n]$，上一页的逐点模板可以逐字套用，一个字都不用改。难度出现在实现那一侧：posterior（后验）的归一化常数是一个积分，被积函数里 $\theta$ 只出现一次，但要把它之外的所有自由度都抹掉，而每个观测都带进来一个新维度。以最简单的 quadrature（求积）为例，每个维度取 $m$ 个格点，$n$ 个观测就需要 $m^n$ 个格点，而且这些格点必须张成完整网格，没法逐维独立处理——因为 likelihood（似然）一般不能分解成"每个观测只管自己那个 $\theta_j$"的乘积。
>
> 维度楼梯长这样，每一级都把前一级的整块再积一遍：$n = 1$ 时一重循环，$n = 2$ 时二重循环套在一重之外，$n = 3$ 时三重……循环层数等于观测数，最内层的工作量乘上 $m$ 的幂次。所以问题的形状不是"变复杂"，而是"指数地变复杂"。
>
> 把量级算出来就知道为什么必须换路。取 $m = 100$（每一维都算很粗）、$n = 10$（十个传感器），格点总数 $100^{10} = 10^{20}$。按每秒 $10^{9}$ 次浮点运算估计，需要 $10^{11}$ 秒，约合三千一百七十年。而若限制估计器为线性形式，未知系数只有 $n + 1$ 个，解一个 $11 \times 11$ 的线性方程组，$O(n^3)$ 量级约一千次运算——两条路的差距不是十倍百倍，是十七个数量级。
>
> 于是工程上有三条绕行路线，判据都是同一个问题：能不能把那个积分换掉。第一条，限制函数形式，只在线性函数族里找最优，这就是下一讲的 linear LMS（线性最小均方估计），把积分换成解 normal equation（正规方程）。第二条，选共轭 prior（先验），让积分退化成参数加法，这就是上一讲的 Beta（贝塔） 那个套路。第三条，用采样代替积分，误差约 $O(1/\sqrt{N})$，与维数的关系温和得多，这就是本讲开头提到的跟踪应用里真正在跑的东西——particle filter（粒子滤波），用一堆带权样本代表 posterior（后验），权重按 likelihood（似然）更新，重采样淘汰低权样本。
>
> 跨课程连接给到 CLRS 的 dynamic programming（动态规划）。DP 能用，靠两条：最优子结构，以及子问题重叠——把指数多条路径压成多项式张表。贝叶斯推断里对应物是递推：若观测满足条件独立且状态满足马尔可夫性，$n$ 步的联合 posterior（后验）可以一步一更新地算，不必一次性面对 $n$ 维网格。高斯情形下这个递推就是 Kalman filter（卡尔曼滤波）：整条链只需要携带均值与协方差两个量，每步代价 $O(d^2)$，其中 $d$ 是状态维数。区别在于表的项不是数而是分布——DP 的记忆化存"值"，Kalman filter（卡尔曼滤波）存"信念"，所以后者每步都要做一次预测加一次修正，两部曲不能省。
>
> 回指本讲开头：tracking（跟踪）例里 $Z_t = \Theta_0 + t\Theta_1 + t^2\Theta_2$、$X_t = Z_t + W_t$，未知量只有三个，所以三维网格还能硬算；一旦未知量维数上去（比如一条曲线用二十个基函数表示），同一套公式立刻变成上面那三千一百年。收束：本讲的公式到此完整，下一讲开始换的不是数学，而是"允许在哪些函数里找解"这个前提。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
