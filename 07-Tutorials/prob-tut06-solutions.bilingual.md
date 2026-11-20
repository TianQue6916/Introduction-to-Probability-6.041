<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 6 解答（Tutorial 6: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 电气工程与计算机科学系）</span>

> <span style="color:#1e8449;">**[note]** 原解答 PDF 仅印出解答正文、未附题目文字；以下按原页题号完整翻译解答内容（解答本身已含所需的题设上下文）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $Z = X + Y$。使用两步 CDF 方法（2-step CDF method）：
>
> ```math
> F_Z(z) = P(Z \le z) = P(X + Y \le z).
> ```
>
> 利用全概率定理（Total Probability Theorem），有
>
> ```math
> F_Z(z) = \sum_x p_X(x)\, P(x + Y \le z) = \sum_x p_X(x)\, P(Y \le z - x) = \sum_x p_X(x)\, F_Y(z - x).
> ```
>
> 两边对 $z$ 求导，得
>
> ```math
> f_Z(z) = \frac{d}{dz} F_Z(z) = \sum_x p_X(x)\, f_Y(z - x).
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 对 $x$ 求和表明 $X$ 为离散随机变量（以 PMF（概率质量函数）$p_X$ 描述），而 $f_Y$ 为连续密度，故这是离散-连续混合情形的卷积（convolution）公式。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **为什么“先算 CDF（累积分布函数）再求导”不是技巧，而是唯一不带额外假设的入口。**
>
> 把随机变量看成函数 $X: \Omega \to \mathbb{R}$（$\Omega$ 为样本空间）。则“$Z$ 的分布”这句话的严格含义只有一条：集合函数 $A \mapsto P(\{\omega : Z(\omega) \in A\})$。CDF（累积分布函数）只是这个函数在射线 $(-\infty, z]$ 上的取值。PDF（概率密度函数）根本不在定义里 —— 它是“当那个集合函数恰好能写成积分时”才存在的导数，是派生对象。谁可以无条件使用、谁需要额外假设，就由这一句话区分开。这是本题方法的第一性原理：分布不是密度，密度是分布在可微情形下的一个坐标。
>
> 于是 2-step CDF method（两步 CDF 方法）的真实结构是三步，“求导”只是第三步。第一，preimage（原像）：把条件 $g(X) \le z$ 翻译成关于 $X$ 的集合 $\{x : g(x) \le z\}$。第二，测度：用 $X$ 已知的 PMF（概率质量函数）或 PDF（概率密度函数）去度量这个集合的概率。第三，求导：只有当 $F_Z$ 可微时才做，目的是换回密度，好接卷积或最大似然。三步都不要求 $g$ 单调、可逆或可微，这就是它比“直接套变量替换公式”更根本的地方；教材 §4.1 把它单列为 derived distribution（派生分布），本课程第 10、11 讲都按这个顺序推。
>
> 本题还多一层：$X$ 离散、$Y$ 连续，所以第二步的“测度”不是积分而是求和。Total Probability Theorem（全概率定理）在这里的作用是把二维问题逐点降成一维：先固定 $x$，问“$Y$ 要落在哪里才使 $x + Y \le z$”，答案是 $Y \le z - x$，再按 $p_X(x)$ 加权。注意求和号吃的是 $X$ 的 PMF（概率质量函数），$F_Y$ 只是被当作“给定 $x$ 之后关于 $z$ 的一个函数”搬来搬去。求导之后得到的 $\sum_x p_X(x) f_Y(z - x)$ 与连续-连续情形的积分是同一个对象：都是 $X$ 的分布与 $Y$ 的密度的 convolution（卷积）。离散用求和、连续用积分，只是“测度长什么样”的差别，不是两套理论。
>
> 跨课程连接（跨到 18.065 与 CSAPP）。卷积在傅里叶基下变成逐点相乘，原因是加法映射 $(x, y) \mapsto x + y$ 在指数函数基底下是对角的 —— 这就是 18.065（矩阵方法）反复讲的那句话：选对基，算子变对角，耦合变独立。落到数值上：直接算这个求和是 $O(n^2)$（$n$ 为 $z$ 的网格点数），FFT（快速傅里叶变换）是 $O(n \log n)$。但 CSAPP 第 2 章（浮点表示）提醒你：浮点加法不满足结合律，快速卷积的舍入误差随 $\log n$ 增长，$n$ 很大时会遇到“理论更快、实测更不准”的交换。这条交换没有任何概率内容，纯粹由 IEEE 754（浮点标准）的形状决定。
>
> 还有一层实分析的味道，值得现在埋下。求导这一步之所以被称作“可选”，是因为 CDF（累积分布函数）作为单调函数几乎处处可导，但它可以在一个零测集上不可导，甚至整体不存在密度 —— 这时分布是奇异的，两步法只能停在第一步。所以 2-step CDF method（两步 CDF 方法）真正的安全性来自第一步与第二步（原像与测度），第三步只是考试与工程报告里的便利。你在实分析里会碰到单调函数的可微性定理，那时回头看这条注，会发现概率论把这件事当工具用了很久才被严格化。
>
> 最后一个容易漏的边界：这个求和只在 $z$ 落在有限多个平移区间的并集里才非零，也就是两个支撑集的 Minkowski（闵可夫斯基）和。出了那个并集，$f_Z = 0$，而 $\sum_x p_X(x) f_Y(z - x)$ 会自动给出 $0$ —— 因为每个 $x$ 对应的 $f_Y(z - x)$ 都为零。所以做数值实现时不需要手工写分段，只需要保证 $z$ 的网格覆盖面足够宽。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 我们以 $X$ 为条件，使用全方差定律（law of total variance）：
>
> ```math
> \mathrm{var}(X + Y) = E\big[\mathrm{var}(X + Y \mid X)\big] + \mathrm{var}\big(E[X + Y \mid X]\big).
> ```
>
> 给定 $X$ 的取值 $x$，随机变量 $Y$ 在区间 $[x, x+1]$ 上均匀分布，而随机变量 $X + Y$ 在区间 $[2x, 2x+1]$ 上均匀分布。因此 $E[X + Y \mid X] = 0.5 + 2X$，$\mathrm{var}(X + Y \mid X) = 1/12$。于是
>
> ```math
> \mathrm{var}(X + Y) = \mathrm{var}(0.5 + 2X) + E[1/12] = 4\,\mathrm{var}(X) + E[1/12] = \frac{5}{12}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 由 $4\,\mathrm{var}(X) + 1/12 = 5/12$ 可知本题中 $\mathrm{var}(X) = 1/12$。</span>

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **law of total variance（全方差定律）就是勾股定理；条件化是一次正交投影。**
>
> 先把方差翻译成几何语言。在“二阶矩有限的随机变量”这个集合上定义 $\langle U, W \rangle = E[UW]$。它对称、双线性、正定（$\langle U, U \rangle = 0$ 当且仅当 $U$ 在几乎必然意义下为零），所以就是一个 inner product（内积），$\|U\|^2 = E[U^2]$ 就是范数平方。于是 $\mathrm{var}(Y) = E[(Y - E[Y])^2] = \|Y - E[Y]\|^2$，读作“$Y$ 到常数子空间的正交距离的平方”。这句话里没有概率内容，全是 Strang（斯特朗）线性代数里的内积与投影。
>
> 第二个观察：$E[Y \mid X]$ 是 $Y$ 在子空间 $V$ 上的正交投影，$V$ 由所有形如 $\varphi(X)$ 的随机变量张成（$\varphi$ 取遍你能写的任意函数）。判据是残差正交：$Y - E[Y \mid X]$ 与 $V$ 中任何元素都正交，即对任意 $\varphi$ 有 $E[(Y - E[Y \mid X])\,\varphi(X)] = 0$。这条性质由 conditional expectation（条件期望）的定义与迭代期望直接推出；它同时说明了“给定 $X$ 之后，$Y$ 的最优最小二乘预测正是 $E[Y \mid X]$”。你不必先掌握子空间的严格定义，只要承认这里的投影和 $\mathbb{R}^n$ 里的投影遵守同一套代数规则：分解唯一、残差正交、范数平方可加。
>
> 于是 $Y - E[Y] = \big(E[Y \mid X] - E[Y]\big) + \big(Y - E[Y \mid X]\big)$ 是一个正交分解，勾股定理立刻给出 $\mathrm{var}(Y) = \mathrm{var}(E[Y \mid X]) + E[\mathrm{var}(Y \mid X)]$。右边第二项等于 $\|Y - E[Y \mid X]\|^2$，因为条件方差是“在每根纤维内部算距离平方”、再取期望是“按纤维加权平均”，合起来正是那个范数平方；第一项等于 $\|E[Y \mid X] - E[Y]\|^2$，因为 $E[E[Y \mid X]] = E[Y]$（迭代期望）。定理证完，一行代数没写，全是分解。
>
> 命名的证明策略模板：**projection decomposition（投影分解法）**。步骤固定为：先问“条件化能提供哪个子空间”，再把待求量按这个子空间做正交分解，最后用勾股定理把范数平方拆成“可解释部分 + 残差部分”。它和把向量 $b$ 拆成 $A\hat{x}$ 与 $b - A\hat{x}$ 是同一个动作，区别只是内积换了；最小二乘、卡尔曼滤波、以及用条件期望替换估计量以降低方差的 Rao-Blackwell（拉奥-布莱克韦尔）化，都用这个模板。
>
> 回到本题的数值链：给定 $X = x$，$Y$ 在 $[x, x+1]$ 上均匀，于是 $X + Y$ 在 $[2x, 2x+1]$ 上均匀 —— 注意这一步是平移而不是缩放，所以条件期望 $E[X + Y \mid X] = 2X + 0.5$ 是 $X$ 的线性函数，条件方差 $\mathrm{var}(X + Y \mid X) = 1/12$ 是常数（平移不改变离散度）。代入两条支路：$E[\mathrm{var}(X + Y \mid X)] = 1/12$，$\mathrm{var}(E[X + Y \mid X]) = \mathrm{var}(2X + 0.5) = 4\,\mathrm{var}(X)$。这里用了 $\mathrm{var}(aX + b) = a^2 \mathrm{var}(X)$：几何上就是“线性映射把向量拉长 $a$ 倍，距离平方乘 $a^2$”，和矩阵的算子范数是同一件事。
>
> 一个可以立刻验证的离散特例：令 $X$ 只取 $a, b$ 两值，$p = P(X = a)$。则 $E[Y \mid X]$ 在每个纤维上取常值，直接代入可得 $\mathrm{var}(E[Y \mid X]) = p(1-p)\big(E[Y \mid X = a] - E[Y \mid X = b]\big)^2$，而 $E[\mathrm{var}(Y \mid X)] = p\,\mathrm{var}(Y \mid X = a) + (1-p)\,\mathrm{var}(Y \mid X = b)$。两式相加就是“组间 + 组内”的分解，把 $p(1-p)$ 认成两组均值的加权方差之后，勾股关系一眼可见。
>
> 跨课程连接（接 6.042J 的等价关系）。条件化在离散数学里的原型是“按 $X$ 的取值做商集”：每个等价类就是 $X$ 的一根 fiber（纤维）$\{\omega : X(\omega) = x\}$。$E[Y \mid X]$ 是“在每根纤维内取平均”得到的函数，$\mathrm{var}(Y \mid X)$ 是“在每根纤维内算离散度”。全方差定律于是读作：总离散度 = 类内离散度的加权平均 + 类间离散度。这正是 ANOVA（方差分析）的分解式，也是“为什么要分层抽样”的定量理由 —— 层间差异大、层内差异小时，按层加权比整体抽样省样本。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#00838f;">**(a)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $X_i$ 为相互独立的伯努利（Bernoulli）随机变量，若第 $i$ 次抛掷结果为正面（heads）则取值为 1。设 $N$ 为抛硬币的总次数。我们有 $E[X_i] = 1/2$、$\mathrm{var}(X_i) = 1/4$、$E[N] = 7/2$、$\mathrm{var}(N) = 35/12$（最后一个等式由离散均匀（discrete uniform）随机变量的方差公式得到）。因此，正面出现次数的期望为
>
> ```math
> E[X_i]\, E[N] = \frac{7}{4},
> ```
>
> 方差为
>
> ```math
> \mathrm{var}(X_i)\, E[N] + \big(E[X_i]\big)^2\, \mathrm{var}(N) = \frac{1}{4} \cdot \frac{7}{2} + \frac{1}{4} \cdot \frac{35}{12} = \frac{77}{48}.
> ```

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **随机个随机变量之和：为什么必须把求和上限拆成指示变量。**
>
> 答案 $E[X_i]\,E[N] = 7/4$ 看起来很自然，但自然不等于已证。麻烦出在求和上限：$\sum_{i=1}^{N} X_i$ 里的 $N$ 本身是随机变量，所以“几项相加”在抽样之前是不确定的。期望的线性性 $E[\sum] = \sum E[\,\cdot\,]$ 只对固定项数成立，不能直接套用。
>
> 标准解法的第一步是一个恒等变形。对每个 $i \ge 1$ 定义 indicator variable（指示变量）$I_i$：$I_i = 1$ 表示 $N \ge i$，$I_i = 0$ 表示 $N < i$。于是 $\sum_{i=1}^{N} X_i = \sum_{i \ge 1} X_i I_i$，右边是无穷多项，但只有有限多项非零（因为 $N$ 有限）。这一步把“随机的项数”换成“固定的项数 + 每项带一个开关”，问题的形状从可变边界变成了固定边界加开关。
>
> 第二步用线性性：$E\big[\sum_{i \ge 1} X_i I_i\big] = \sum_{i \ge 1} E[X_i I_i]$，这一步不需要任何独立性。第三步才是关键，需要 $E[X_i I_i] = E[X_i]\,P(N \ge i)$，也就是 $X_i$ 与 $I_i$ independent（独立）——“第 $i$ 次抛掷的结果”与“还要不要抛第 $i$ 次”无关。这件事由 $N$ 是 stopping time（停时）保证：事件 $\{N \ge i\}$ 只看 $X_1, \dots, X_{i-1}$，不看 $X_i$ 及以后。本题的 $N$ 由一枚独立的骰子决定，比停时还强，天然满足。
>
> 第四步把概率求和换成期望：对非负整值随机变量有 $\sum_{i \ge 1} P(N \ge i) = E[N]$（尾和公式，本质是把 $N$ 拆成 $N$ 个 $1$）。于是 $E\big[\sum_{i=1}^{N} X_i\big] = E[X]\sum_{i \ge 1} P(N \ge i) = E[X]\,E[N]$。这就是 Wald's equation（瓦尔德等式）。
>
> 命名的证明策略模板：**indicator decomposition（指示变量拆加法）**。三件套是“把计数写成指示变量之和 → 交换求和与期望（此步不需要独立）→ 对每个指示变量单独算期望（此步才用独立或停时）”。CLRS（算法导论）§5.2 的 HIRE-ASSISTANT（雇佣问题）分析是同款模板：把“一共雇了几个人”写成指示变量之和，再对每个指示变量单独求期望，得到调和数 $H_n \approx \ln n$。你在 6.006 里见过的那套推理与本题是同一条定理的两个化身；区别只在于本题的开关由“随机个数的上限”产生，那里由“是否出现新的最大值”产生。
>
> 历史坐标（以机制为主，年份只作点缀）。这套“随机项数”的记账法属于 Abraham Wald（亚伯拉罕·瓦尔德，1902 年生于克卢日，1950 年死于印度上空的一次空难）。1938 年他因纳粹迫害从维也纳移居美国，在 Columbia University（哥伦比亚大学）工作；1943 年前后在哥伦比亚的 Statistical Research Group（战时统计研究组）发展 sequential analysis（序贯分析），1947 年出版同名专著 Sequential Analysis（序贯分析）。Wald's equation（瓦尔德等式）是序贯检验里计算“平均样本量”的工具，回答的正是本题的连续抽样版本：我平均要观测多少个样本才会停止？他另一件被反复讲述的事——二战期间根据返航轰炸机的弹孔分布推断该加固哪里——是 survivorship bias（幸存者偏差）的经典案例：能飞回来的飞机是活下来的样本，机翼弹孔多恰恰说明机翼中弹不致命。两件事属于同一个人、同一个年代，但机制不同，不要混为一谈。
>
> 失效边界值得记住：如果 $N$ 与 $X_i$ 不独立（例如看到结果之后再决定数几项），那么 $E[X_i I_i] \ne E[X_i]\,P(N \ge i)$，Wald's equation（瓦尔德等式）立刻失效。这正是定理条件里写“停时”而不是“任意随机变量”的原因，也是所有把随机性拿来做优化的场景必须先检查的前置条件。

<span style="color:#00838f;">**(b)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本小问的试验可以视为由 (a) 小问的试验独立重复（independent repetitions）两次构成。因此，均值与方差都翻倍，分别变为 $7/2$ 与 $77/24$。

> <span style="color:#1e8449;">[note] Note（译者注）:</span> **“方差翻倍”为什么成立：方差是二次型，独立让它对角。**
>
> 小问 (b) 说“独立重复两次，均值与方差都翻倍”。均值那一半是线性性的直接后果，方差那一半值得展开，因为它把好几门课的概念钉在同一处。
>
> 第一条：$\mathrm{var}(U + W) = \mathrm{var}(U) + \mathrm{var}(W) + 2\,\mathrm{cov}(U, W)$，其中 $\mathrm{cov}(U, W) = E[(U - E[U])(W - E[W])]$。covariance（协方差）就是上一条注里那个内积的中心化版本。independent（独立）推出 $E[UW] = E[U]E[W]$，所以 $\mathrm{cov}(U, W) = 0$，交叉项消失。于是“独立则方差可加”本质上是“正交向量满足勾股定理”—— 与 Problem 2（第 2 题）那条注用的是同一套几何，只是从“条件化子空间”换成了“独立子空间”。
>
> 第二条：把它写成矩阵。设 $\mathbf{X} = (X_1, \dots, X_n)^{\mathsf{T}}$，covariance matrix（协方差矩阵）为 $\Sigma = E[(\mathbf{X} - \boldsymbol{\mu})(\mathbf{X} - \boldsymbol{\mu})^{\mathsf{T}}]$。对任意常向量 $\mathbf{a}$ 有 $\mathrm{var}(\mathbf{a}^{\mathsf{T}}\mathbf{X}) = \mathbf{a}^{\mathsf{T}}\Sigma\mathbf{a}$，右边是一个 quadratic form（二次型）。独立推出非对角元为零，$\Sigma$ 是对角矩阵，于是 $\mathbf{a}^{\mathsf{T}}\Sigma\mathbf{a} = \sum_k a_k^2 \sigma_k^2$，可加性就退化成“对角线元素直接相加”。一般情形下 $\Sigma$ 对称半正定，可正交对角化为 $\Sigma = Q\Lambda Q^{\mathsf{T}}$，此时 $\mathbf{a}^{\mathsf{T}}\Sigma\mathbf{a} = \sum_k \lambda_k (\mathbf{q}_k^{\mathsf{T}}\mathbf{a})^2$：方差是“沿各特征方向的分量的平方按特征值加权”。18.065（矩阵方法）第 5 讲把同一件事讲成正定矩阵的能量表达式 $\mathbf{x}^{\mathsf{T}}A\mathbf{x} > 0$，那里的对象就是这里的同一个二次型。
>
> 第三条：为什么提升精度要按 $\sqrt{n}$ 而不是按 $n$。独立重复 $n$ 次给方差乘 $n$，standard deviation（标准差）只乘 $\sqrt{n}$。这条 $\sqrt{n}$ 定律是 6.041 第 19 讲（弱大数定律，§5.1 到 §5.3）与第 20 讲（中心极限定理，§5.4）分母的来源：样本均值 $\bar{X}_n$ 的标准差是 $\sigma/\sqrt{n}$，中心极限定理把 $\sqrt{n}(\bar{X}_n - \mu)/\sigma$ 的分布钉到标准正态。定量的代价很硬：要把误差再减半，样本量得乘四。所有 Monte Carlo（蒙特卡洛）方法的成本曲线都长这样，这也是 6.006 里“随机化算法重复几次才够”的成本估算依据。
>
> 跨课程连接（接 6.006）。随机化算法里“重复 $k$ 次取多数”降低出错概率是指数速度的，而“估计量的精度按 $\sqrt{k}$ 改善”只是二阶矩的速度。两句话都对，不矛盾：前者是 tail probability（尾概率）的指数界，后者是方差的线性律。混淆这两件事会在设计实验时选错 $k$：要压住“偶发大错”靠指数界，要压住“平均偏差”只能靠更多样本。二者的区别用一句话说：指数界管的是尾部，方差管的是主体。
>
> 用矩阵语言把本题小问 (b) 重算一遍，可以检验上面的抽象。把两次独立重复的两个副本记作 $S_1$ 与 $S_2$，则 $\mathrm{cov}(S_1, S_2) = 0$，$2 \times 2$ 的 covariance matrix（协方差矩阵）是 $\Sigma = \mathrm{diag}(77/48,\, 77/48)$。所求为 $\mathrm{var}(S_1 + S_2) = \mathbf{1}^{\mathsf{T}}\Sigma\,\mathbf{1}$，其中 $\mathbf{1} = (1, 1)^{\mathsf{T}}$，于是 $\mathbf{1}^{\mathsf{T}}\Sigma\mathbf{1} = 77/48 + 77/48 = 77/24$。极端对照：若两个副本完全正相关，$\Sigma$ 的两个非对角元都是 $77/48$，同样的计算给出 $4 \times 77/48 = 77/12$，是独立情形的四倍 —— 这就是“correlation coefficient（相关系数）等于 $1$ 时方差按 $n^2$ 增长”的含义。
>
> 数值感觉：本题小问 (a) 的方差是 $77/48 \approx 1.604$，小问 (b) 是 $77/24 \approx 3.208$，正好翻倍；而标准差从约 $1.267$ 涨到约 $1.791$，只涨了 $\sqrt{2} \approx 1.414$ 倍。方差按 $n$、标准差按 $\sqrt{n}$ 这一条差别，就是“多测几次取平均”这个直觉的数学来源。
>
> 把上面三条压成一句可执行的判据：算和的方差之前，先问“各分量之间有没有相关性”。没有相关性，方差就是各分量方差之和（矩阵语言：covariance matrix（协方差矩阵）$\Sigma$ 是对角矩阵）；有相关性，就必须把非对角元一起算进来（矩阵语言：$\mathbf{a}^{\mathsf{T}}\Sigma\mathbf{a}$ 里的交叉项不能丢）。本题小问 (b) 属于前者，因为“独立重复”这四个字保证两次试验之间不存在任何共享的随机源。

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">**（本页为 MIT OpenCourseWare 版权/引用说明页）**</span>

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课程）· http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。</span>

<span style="color:#7f8c8d;">有关引用本材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
