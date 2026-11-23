<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 20 解答（Recitation 20: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 11 月 18 日）</span>

<span style="color:#7f8c8d;">麻省理工学院电气工程与计算机科学系（Massachusetts Institute of Technology, Department of Electrical Engineering & Computer Science）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)** 设 $X_i$ 为指示第 $i$ 个灯泡（bulb）是否为好灯泡的 indicator random variable（指示随机变量），取「1」表示好灯泡、「0」表示坏灯泡。各 $X_i$ 为相互独立的 Bernoulli（伯努利）随机变量。令
>
> ```math
> Z_n=\frac{X_1+X_2+\cdots+X_n}{n}
> ```
>
> 则
>
> ```math
> E[Z_n]=p,\qquad \mathrm{var}(Z_n)=\frac{n\,\mathrm{var}(X_i)}{n^2}=\frac{\sigma^2}{n},
> ```
>
> 其中 $\sigma^2$ 为 $X_i$ 的方差。应用 Chebyshev inequality（切比雪夫不等式）得
>
> ```math
> P\bigl(|Z_n-p|\ge\epsilon\bigr)\le\frac{\sigma^2}{n\epsilon^2}
> ```
>
> 当 $n\to\infty$ 时，$\sigma^2/(n\epsilon^2)\to 0$，从而 $P(|Z_n-p|\ge\epsilon)\to 0$。因此 $Z_n$ converges in probability（依概率收敛）到 $p$。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这一段把两个完全不同类型的东西接在了一起：variance（方差）是一个可积性条件，只谈二阶矩这一条数值；而 convergence in probability（依概率收敛）是一个事件概率条件，只谈概率质量有没有逃出一个固定区间。Chebyshev inequality（切比雪夫不等式）就是这两者之间唯一一座不需要知道分布形状的桥，它只要求 expectation（期望）存在、variance（方差）有限，对分布是两点分布、正态分布还是任何奇形怪状一律不问。这条「不问形状」的性格既是它最大的优点，也正是它后来被嫌「界太松」的全部原因，两条评价其实来自同一个设计决定。
>
> 先把 convergence in probability（依概率收敛）的定义拆开。它说的是：对每一个固定的 $\epsilon>0$，都有 $\lim_{n}P(|Z_n-p|\ge\epsilon)=0$。这里的量词顺序是全部要害 —— $\epsilon$ 先被任意给定、然后冻结不动，极限只在 $n$ 上取。如果把 $\epsilon$ 也掺进 $n$ 里，比如取 $\epsilon_n=1/n$，结论立刻变质：$P(|Z_n-p|\ge 1/n)$ 根本不趋于零，因为 $Z_n$ 的涨落尺度是 $\sigma/\sqrt{n}$，比 $1/n$ 大了整整 $\sqrt{n}$ 倍。所以「样本越多越准」这句话必须钉死在一个固定的 tolerance（容差）上才有意义，不能顺手改写成「误差以 $1/n$ 的速度消失」。不做这个区分，就会把 weak law of large numbers（弱大数定律）误读成一条确定性的误差衰减率，然后在 $n=10^{6}$ 时以为精度能到 $10^{-6}$，实际只到 $10^{-3}$。
>
> 为什么这座桥只能用 Chebyshev inequality（切比雪夫不等式）搭？因为推导只有两步，而第一步就是全部技巧。第一步把事件 $\lbrace |Z_n-p|\ge\epsilon \rbrace$ 改写成 $\lbrace (Z_n-p)^2\ge\epsilon^2 \rbrace$ —— 这两个集合完全相等，因为平方在非负数上是 monotone bijection（单调双射）。第二步对非负随机变量 $(Z_n-p)^2$ 套 Markov bound（马尔可夫界），立刻得到 $\sigma^2/(n\epsilon^2)$。为什么不平方？不平方只能拿到 $E|Z_n-p|/\epsilon$，而绝对值的 expectation（期望）在任何对称分布下都被正负相消压得很小，界会假装乐观；平方把「带符号的偏差」变成「能量」，同时正好把假设里已经给出的 variance（方差）接到分子上。换句话说，平方不是凑巧，是为了让分子恰好吃到已知量。
>
> 关键机制落在 $n$ 的幂次上。$E[Z_n]=p$ 是「除以 $n$ 之后 expectation（期望）不变」的结果；而 variance（方差）之所以是 $\sigma^2/n$ 而不是 $\sigma^2$，唯一靠的是 independence（独立性）—— 交叉项 $E[(X_i-p)(X_j-p)]$ 在 $i\ne j$ 时为零，$n(n-1)$ 个交叉项一起消失，只剩 $n$ 个对角项。去掉 independence（独立性）会塌成什么样？让所有 $X_i$ 都等于同一个 $X$，也就是完全相关。这时 $Z_n$ 恒等于 $X$，variance（方差）仍然是 $\sigma^2$，界退化成 $\sigma^2/\epsilon^2$，对 $n$ 一点不衰减，convergence in probability（依概率收敛）直接不成立。所以 independence（独立性）不是行文修辞，是这条定律的全部燃料。
>
> 一个能代入到底的算例：取 $p=0.5$、$\epsilon=0.1$、$n=2500$。界给出 $\frac{0.25}{2500\times 0.01}=0.01$。真值可以估：标准差是 $\sigma/\sqrt{n}=0.5/50=0.01$，所以 $0.1$ 正好是十个标准差，概率约为 $2\Phi(-10)\approx 1.5\times 10^{-23}$。界 0.01 与真值 $10^{-23}$ 差了二十一个数量级。这不是算错，而是 Chebyshev inequality（切比雪夫不等式）按「最坏分布」结算的代价：它要对所有二阶矩相同的分布同时成立，就必须照顾那个把质量堆在 $\pm\sigma$ 上的极端分布。
>
> 跨课程看一眼：CSAPP 里对 cache（缓存）命中率做 amortized（摊还）分析，走的是同一套骨架 —— 拿「$n$ 次操作的总代价」配「单次最坏代价」得一条不等式，把全局平均和局部保证锁在一起。区别只在确定性：那边的不等式对每个输入都成立，这边的 Chebyshev inequality（切比雪夫不等式）只是以大概率成立。认清这个「几乎」与「总是」的差别，就不会把概率界当成硬性上界，去写实时系统的截止时限论证。
>
> **(b)** 由切比雪夫不等式，
>
> ```math
> P\bigl(|Z_{50}-p|\ge 0.1\bigr)\le\frac{\sigma^2}{50(0.1)^2}
> ```
>
> 由于 $X_i$ 是 Bernoulli 随机变量，其方差 $\sigma^2=p(1-p)\le \dfrac{1}{4}$。于是
>
> ```math
> P\bigl(|Z_{50}-p|\ge 0.1\bigr)\le\frac{1/4}{50(0.1)^2}=0.5
> ```
>
> **(c)** 由切比雪夫不等式，
>
> ```math
> P\bigl(|Z_n-p|\ge 0.1\bigr)\le\frac{\sigma^2}{n\epsilon^2}\le\frac{1/4}{n(0.1)^2}
> ```
>
> 要保证以概率 $0.95$ 落在所需范围内，需要
>
> ```math
> \frac{1/4}{n(0.1)^2}<0.05
> ```
>
> 由此得 $n\ge 500$。注意，即使对最高的方差（即 $1/4$），$n\ge 500$ 也能保证 accuracy specification（精度指标）；方差更小时，保证所需精度所需的 $n$ 也更小。例如，若 $\sigma^2=1/16$，则 $n\ge 125$ 就足够了。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 先把 $n\ge 500$ 这个数从哪来一步步做实，再谈它有多松、松在哪里、后来被什么取代。代数是纯机械的：把 $\sigma^2=1/4$、$\epsilon=0.1$ 代进 $\frac{1/4}{n(0.1)^2}<0.05$，左边等于 $\frac{0.25}{0.01n}=\frac{25}{n}$，于是 $25/n<0.05$，即 $n>500$。注意严格不等式解出的是严格大于，教材写 $\ge 500$ 是按整数取整的习惯写法，$n=500$ 时左边正好等于 $0.05$ 而非小于，边界上差一丝。同一式子换成 $\sigma^2=1/16$ 得 $6.25/n<0.05$，即 $n>125$，与正文给的 125 一致。这两个数字不是巧合：$n$ 与 $\sigma^2$ 成正比、与 $\epsilon^2$ 成反比，所以精度翻一倍就要四倍样本，这是 Laplacian 式的平方律代价，任何基于二阶矩的样本量公式都逃不掉。
>
> 现在算一算这个 500 到底有多保守，这是本条注的核心。同样的题目换一条不等式：Hoeffding inequality（霍夫丁不等式）对 $[0,1]$ 上的独立有界变量给 $P(|Z_n-p|\ge\epsilon)\le 2\exp(-2n\epsilon^2)$。代入 $\epsilon=0.1$ 并令右端等于 $0.05$，得 $\exp(-0.02n)=0.025$，即 $0.02n=\ln 40=3.689$，$n\ge 184.4$，取整为 185。再换一条更贴近的：因为 $Z_n$ 是 $n$ 个独立同分布变量之和除以 $n$，central limit theorem（中心极限定理）说它近似正态，标准差为 $0.5/\sqrt{n}$，于是 $P(|Z_{n}-p|\ge 0.1)\approx 2\Phi(-0.1\sqrt{n}/0.5)=2\Phi(-0.2\sqrt{n})$；令它等于 $0.05$ 需 $0.2\sqrt{n}=1.96$，得 $\sqrt{n}=9.8$，$n\approx 96$。同一道题，三条路给出 500、185、96，最大与最小差五倍多。
>
> 差别的来源可以定位得很精确：Chebyshev inequality（切比雪夫不等式）只用到 variance（方差），而方差对分布的一切「形状信息」做了彻底平均 —— 它把 $n$ 个变量的所有高阶结构压成一个数，代价就是必须对「最坏的那个二阶矩相同的分布」负责。那个最坏分布是两点分布：质量各一半落在 $p\pm\sigma$ 上，它的 tail（尾部）恰好顶到不等式的等号。Hoeffding inequality（霍夫丁不等式）额外用上了有界性，把「值域宽度」当资源；Chernoff bound（切尔诺夫界）则用上 moment generating function（矩母函数），也就是整条分布的信息，代价是要求它在一个邻域内有限。三条界的差别，本质上就是「你允许自己用多少分布信息」的差别，不是谁对谁错。
>
> 历史这一层值得记住，因为它解释了为什么这门课先教最松的那条。Bienaymé 在 1853 年先证了这个不等式的特例，Chebyshev inequality（切比雪夫不等式）的一般形式出现在 1867 年那篇题为「论平均值」的论文里，他做这件事的动机不是造一条实用界，而是要给大数定律一个只依赖矩的证明 —— 在那个年代，分布函数这个概念还不成形，能手头有的只有矩。Hoeffding inequality（霍夫丁不等式）发表于 1963 年的《美国统计学会会刊》第 58 卷，Chernoff bound（切尔诺夫界）发表于 1952 年的《数学统计年刊》第 23 卷，两者都比 Chebyshev inequality（切比雪夫不等式）晚了近一个世纪，等的正是「独立性怎么被结构化使用」这套语言成熟。
>
> 拓展到前沿：这条「算 $n$」的线索今天叫 sample complexity（样本复杂度），是 learning theory（学习理论）的入门砖。把 Chebyshev inequality（切比雪夫不等式）换成 Hoeffding inequality（霍夫丁不等式），再对假设空间做 union bound（并集界），立刻得到「训练误差与真实误差差距不超过 $\epsilon$ 的概率至少 $1-\delta$，所需样本量约为 $\frac{1}{2\epsilon^2}\ln\frac{2|\mathcal{H}|}{\delta}$」—— 这叫 generalization bound（泛化界），是 Vapnik 与 Chervonenkis 那条路线的起点，也是今天 PAC learning（可能近似正确学习）教材第一页的公式。它与本题的公式只差一个常数因子，结构完全同形，这说明 6.041 这道习题不是在练算术，是在练「用一条不等式把概率目标翻译成样本预算」这个动作。
>
> 再往上接一层：6.042J 里的 union bound（并集界）是同一家族里最省的版本，它一条 variance（方差）都不用，只把概率加总，所以对任何事件都成立，但给出的 $n$ 通常要大一个数量级。工程上的意义很直接：如果按 500 定采样预算而真值只需 96，就白烧了五倍算力；反过来，若分布可能重尾、variance（方差）未知，只有 Chebyshev inequality（切比雪夫不等式）这条路不需要额外假设，此时多花算力买的是「不问分布形状」的自由。围绕这个 $n$ 的区间就是 confidence interval（置信区间）的原始形态，后面的统计课只是把它从「最坏情况」换成「渐近精确」。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#1e8449;">**[note]** 本题的随机变量设定（可由 (a) 中的计算读出）：$X_n$ 以概率 $1/n$ 取值 $1$、以概率 $1-1/n$ 取值 $0$；$Y_n$ 以概率 $1/n$ 取值 $n$、以概率 $1-1/n$ 取值 $0$。</span>
>
> **(a)**
>
> ```math
> E[X_n]=0\cdot\Bigl(1-\frac{1}{n}\Bigr)+1\cdot\frac{1}{n}=\frac{1}{n}
> ```
>
> ```math
> \mathrm{var}(X_n)=\Bigl(0-\frac{1}{n}\Bigr)^{2}\Bigl(1-\frac{1}{n}\Bigr)+\Bigl(1-\frac{1}{n}\Bigr)^{2}\cdot\frac{1}{n}=\frac{n-1}{n^2}
> ```
>
> ```math
> E[Y_n]=0\cdot\Bigl(1-\frac{1}{n}\Bigr)+n\cdot\frac{1}{n}=1
> ```
>
> ```math
> \mathrm{var}(Y_n)=(0-1)^{2}\Bigl(1-\frac{1}{n}\Bigr)+(n-1)^{2}\cdot\frac{1}{n}=n-1
> ```

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> **(b)** 由切比雪夫不等式，
>
> ```math
> \lim_{n\to\infty}P\Bigl(\Bigl|X_n-\frac{1}{n}\Bigr|\ge\epsilon\Bigr)\le\lim_{n\to\infty}\frac{n-1}{n^2\epsilon^2}=0
> ```
>
> 此外，$\lim_{n\to\infty}\dfrac{1}{n}=0$。因此 $X_n$ 依概率收敛到 $0$。对 $Y_n$，切比雪夫不等式给出
>
> ```math
> \lim_{n\to\infty}P\bigl(|Y_n-1|\ge\epsilon\bigr)\le\lim_{n\to\infty}\frac{n-1}{\epsilon^2}=\infty
> ```
>
> 因此，我们无法通过切比雪夫不等式对 $Y_n$ 的 convergence（收敛性）得出任何结论。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这一段是整份解答最值得停下来看的地方，因为它教的是一个方法论判断，不是一条计算。先看清楚 $Y_n$ 的账目：expectation（期望）对一切 $n$ 恒为 1，而 variance（方差）是 $n-1$，随 $n$ 线性发散。这两个事实合起来只可能有一种机制：存在一条概率为 $1/n$ 的 tail（尾部），它在逃逸时携带 $n$ 这个量级。检验一下就明白 —— $n\times(1/n)=1$ 让 expectation（期望）纹丝不动，$n^2\times(1/n)=n$ 让 second moment（二阶矩）爆炸。换句话说，variance（方差）发散不是「波动变大」，而是「同一个平均值由越来越极端的少数样本撑着」。
>
> 于是 Chebyshev inequality（切比雪夫不等式）在这里输出的是 $\frac{n-1}{\epsilon^2}\to\infty$。很多人看到这一步会下结论说 $Y_n$ 不收敛，这是本题设的唯一陷阱。上界是无穷并不意味着概率是 1，它只意味着这条不等式什么也没说 —— 一条不等式给出一个超过 1 的界，等于没给界。紧接着的小题 (c) 直接算 $P(|Y_n|\ge\epsilon)\le 1/n\to 0$，$Y_n$ 确实收敛到 0。所以这里失败的是方法，不是现象。教材把小 (b)(c) 并排放，就是要读者分清 bound（界）与 truth（真值）是两个对象：前者是某条不等式能挤出的信息，后者是概率本身。
>
> 为什么会失败，可以说得更结构性一点。convergence in probability（依概率收敛）只关心一件事：概率质量有没有逃出 $\epsilon$-邻域，完全不问逃出去的时候值有多大。$Y_n$ 逃出去时值高达 $n$，但它逃出去的概率是 $1/n$，衰减得比 1 快，所以「逃出比例」仍然趋于零。二阶矩方法要求的却是另一件事：逃逸质量必须被 second moment（二阶矩）惩罚到可忽略。一旦 tail（尾部）的重量刚好抵消掉概率的衰减 —— 这里 $n^2$ 的惩罚对上 $1/n$ 的概率，乘积恰好是 $n$ —— 二阶矩就失去控制，界随之失效。判据很干脆：只有当 $E[Y_n^2]$ 保持有界或趋于零时，这条路才走得通。
>
> 换成一张对照表的读法，两个小题就是两行四列。行是 $X_n$ 与 $Y_n$；列依次是「expectation（期望）是否稳定」「second moment（二阶矩）是否有界」「Chebyshev inequality（切比雪夫不等式）是否给结论」「实际是否收敛」。$X_n$ 那一行四格读作：$1/n\to 0$ 稳定、$(n-1)/n^2\to 0$ 有界、给结论、收敛。$Y_n$ 那一行读作：恒等于 1 稳定、$n-1\to\infty$ 无界、不给结论、仍然收敛。第三列与第四列在第二行分叉，这个分叉就是全题的考点所在；把两行并排看，就能一眼看出「界失效」与「不收敛」是两件不同的事。
>
> 给一个能算到数字的核对。取 $n=100$、$\epsilon=0.5$。真值只有一种逃逸方式：$Y_{100}$ 以概率 $0.01$ 等于 100，所以 $P(|Y_{100}|\ge 0.5)=0.01$。Chebyshev inequality（切比雪夫不等式）的界是 $\frac{99}{0.25}=396$，大于 1，完全无用。再把 $n$ 提到 $10^{4}$：真值掉到 $10^{-4}$，界涨到 $\frac{9999}{0.25}=39996$。真值单调下降、界单调上升，两条曲线朝相反方向走 —— 这正是「界失效」在数值上的样子，比任何形容词都清楚。
>
> 跨课程接一下：Thomson 实分析里 $L^2$ 空间与 $L^1$ 空间的包含关系，在这里有一个概率版本的影子。概率空间总质量为 1，所以 $L^2$ 收敛到常数必然推出依概率收敛 —— 因为平方期望把「大偏差」按平方加倍惩罚，偏差想大就必须付平方的账。反过来不成立，理由不需要任何测度论语言就能说清：$L^2$ 范数只看「能量总量」，而依概率收敛只看「面积占比」，一份能量很大但面积极小的尖峰，两者给出的判决可以完全相反。$Y_n$ 就是那根尖峰，它的 counterexample（反例）身份来自「能量有限而面积可忽略」这个几何事实，与后面 (f) 小题说的是同一件事。
>
> **(c)** 对每个 $\epsilon>0$，
>
> ```math
> \lim_{n\to\infty}P\bigl(|Y_n|\ge\epsilon\bigr)\le\lim_{n\to\infty}\frac{1}{n}=0
> ```
>
> 因此 $Y_n$ 依概率收敛到 $0$。
>
> **(d)** 该命题不成立。一个 counterexample（反例）就是 $Y_n$：它依概率收敛到 $0$，但其期望对一切 $n$ 都等于 $1$。
>
> **(e)** <span style="color:#1e8449;">**[note]** 本小题的命题是「若 $E[(X_n-c)^2]\to 0$，则 $X_n$ 依概率收敛到 $c$」——即均方收敛蕴含依概率收敛；下文 (f) 将用反例说明其逆命题（依概率收敛蕴含均方收敛）不成立。</span> 利用 Markov bound（马尔可夫界），
>
> ```math
> P\bigl(|X_n-c|\ge\epsilon\bigr)=P\bigl(|X_n-c|^2\ge\epsilon^2\bigr)\le\frac{E\bigl[(X_n-c)^2\bigr]}{\epsilon^2}
> ```
>
> 令 $n\to\infty$ 取极限，得
>
> ```math
> \lim_{n\to\infty}P\bigl(|X_n-c|\ge\epsilon\bigr)=0
> ```
>
> 这就确立了依概率收敛。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这一小题的证明只有三行，但它的价值全在「为什么只有三行」上，值得当成一个可以搬走的模板来记。模板的骨架是：第一步把目标事件翻译成一个等价的高阶事件，第二步对高阶事件套一条只吃一阶矩的不等式，第三步用假设里已经给出的极限把不等式右端压到零。三步的接口必须对齐 —— 第一步的输出必须是「非负随机变量超过某个正数」，第二步的输出必须是「一个 expectation（期望）除以那个正数」，第三步的假设必须正好是那个 expectation（期望）趋于零。任何一步错位，模板就套不上。
>
> 第一步为什么要把 $\lbrace |X_n-c|\ge\epsilon \rbrace$ 抬成 $\lbrace |X_n-c|^2\ge\epsilon^2 \rbrace$？因为这两个集合逐点相等（平方在非负半轴上是严格递增的），而抬成平方之后，左边那个随机变量就正好是假设里出现的 $(X_n-c)^2$。这一步不是「放缩」，是「换装」：同一个事件换一件能让下一步认得出来的衣服。很多人误以为这里是丢掉信息，其实一点信息都没丢，事件完全一样，只是改写形式。
>
> 第二步为什么只能用 Markov bound（马尔可夫界）？因为它是整个工具箱里唯一只需要两个条件的界：随机变量非负，expectation（期望）有限。它不问 variance（方差），不问分布，也不问 independence（独立性）。这条「门槛低到地板」的性质，正是它排在所有集中不等式最底层的原因，别的不等式要么由它推出，要么在它之上再加假设。把它写成 $P(U\ge a)\le E[U]/a$，其中 $U=(X_n-c)^2$、$a=\epsilon^2$，立刻得到 $E[(X_n-c)^2]/\epsilon^2$。这一步之后，证明已经完成九成，剩下全是代数。
>
> 第三步最容易出错，因为它是唯一一个和 quantifier（量词）打交道的地方。$\epsilon$ 在定义里是「对每个给定值」先固定下来的常数，所以在取 $n\to\infty$ 的极限时它必须冻结：$\frac{E[(X_n-c)^2]}{\epsilon^2}$ 里分子趋于零、分母不动，整个分式才趋于零。假如允许 $\epsilon$ 随 $n$ 变小，比如取 $\epsilon_n=1/n$，结论立刻崩：$Z_n$ 的涨落尺度是 $\sigma/\sqrt{n}$，比 $1/n$ 大 $\sqrt{n}$ 倍，于是 $P(|Z_n-p|\ge 1/n)$ 不但不趋于零，反而趋于 1。这个反直觉的算例说明，「依概率收敛」这四个字里藏着一条不能动的时间顺序，谁把 $\epsilon$ 和 $n$ 搅在一起，谁就得到相反结论。6.042J 里 $\epsilon$-$N$ 论证的陷阱与此同源，都是「先任意、后存在」的顺序问题。
>
> 为什么逆命题是假的，(f) 小题给的是最省的反例。要有「均方收敛」推不出「依概率收敛」的反面例子，只需要一个 expectation（期望）能量发散而概率质量收缩的变量，$Y_n$ 正好两条都满足：$E[Y_n^2]=n\to\infty$，而 $P(|Y_n|\ge\epsilon)\le 1/n\to 0$。要让它成立需要额外的一条假设，现代教材称之为 uniform integrability（一致可积性），用这门课的语言就是「二阶矩一致有界」。机器学习里对应的条件是 bounded loss（有界损失）：损失函数被同一个常数压住，才能从「训练误差小」推到「真实误差小」。条件不是装饰，去掉之后 (f) 就是现成的反例。
>
> 把可算的数字代进去核一遍：取 $n=4$、$\epsilon=2$。假设给出 $E[(Y_4-0)^2]=4$，于是界是 $4/4=1$，即「概率不超过 1」，一句废话。真值只有一种逃逸方式，$Y_4$ 以概率 $0.25$ 等于 4，所以 $P(|Y_4|\ge 2)=0.25$。界与真值差四倍，而且界是恒真的平凡界，说明这条路在 $n$ 小时的输出基本没有信息量 —— 这正是为什么这条定理只能保证「极限成立」，不能保证「有限 $n$ 好用」，两者在工程上要分开对待。
>
> 这个模板的通用形态值得单独拎出来：要证明「某个量以某条不等式控制的收敛」，永远先问三件事 —— 我的假设里有什么可算的量，我有什么不等式只吃这个量，我的目标事件能不能改写成那条不等式的前件。三问对齐，证明就是三行；三问对不上，就要换不等式或者换事件。教材把 (e) 与 (f) 并排，用的是一个通用编排：先用直接法证一个方向，再用单个最小反例证另一个方向不成立，这样「充分不必要」这个关系被两侧夹死，没有第三种可能留给人猜。
>
> **(f)** 一个反例是 $Y_n$：$Y_n$ 依概率收敛到 $0$，但是
>
> ```math
> E\bigl[(Y_n-0)^2\bigr]=0\cdot\Bigl(1-\frac{1}{n}\Bigr)+n^2\cdot\frac{1}{n}=n
> ```
>
> 因此
>
> ```math
> \lim_{n\to\infty}E\bigl[(Y_n-0)^2\bigr]=\infty
> ```
>
> 即 $Y_n$ 并不 converge in mean square（均方收敛）到 $0$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)** 不收敛。因为对任意 $i\ge 1$，$X_i$ 都在 $-1.0$ 与 $1.0$ 之间 uniformly distributed（均匀分布）。
>
> **(b)** 收敛，且极限为 $0$。因为对 $\epsilon>0$，
>
> ```math
> \lim_{i\to\infty}P\bigl(|Y_i-0|>\epsilon\bigr)=\lim_{i\to\infty}P\Bigl(\Bigl|\frac{X_i}{i}-0\Bigr|>\epsilon\Bigr)=\lim_{i\to\infty}\bigl[P(X_i>i\epsilon)+P(X_i<-i\epsilon)\bigr]=0
> ```
>
> 最后一个等号成立的原因是：$X_i$ 在 $[-1,1]$ 上均匀分布，一旦 $i$ 大到使 $i\epsilon>1$，事件 $\{X_i>i\epsilon\}$ 与 $\{X_i<-i\epsilon\}$ 就都落在区间 $[-1,1]$ 之外、不可能发生，故两项概率均为 $0$。
>
> **(c)** 收敛，且极限为 $0$。因为对 $\epsilon>0$，
>
> ```math
> \lim_{i\to\infty}P\bigl(|Z_i-0|>\epsilon\bigr)=\lim_{i\to\infty}P\bigl(\bigl|(X_i)^i-0\bigr|>\epsilon\bigr)
> ```
>
> ```math
> =\lim_{i\to\infty}\Bigl[P\bigl(X_i>\epsilon^{1/i}\bigr)+P\bigl(X_i<-\epsilon^{1/i}\bigr)\Bigr]=\lim_{i\to\infty}\Bigl[\frac{1-\epsilon^{1/i}}{2}+\frac{1-\epsilon^{1/i}}{2}\Bigr]=\lim_{i\to\infty}\bigl(1-\epsilon^{1/i}\bigr)=0
> ```
>
> 其中第三个等号用到 $|X_i|\le 1$ 且函数 $x\mapsto x^i$ 单调：$|X_i|^i>\epsilon$ 等价于 $|X_i|>\epsilon^{1/i}$；第四个等号用到均匀分布的概率计算——对 $0<a<1$，有 $P(X_i>a)=\frac{1-a}{2}$、$P(X_i<-a)=\frac{1-a}{2}$（区间 $[-1,1]$ 总长为 $2$）；最后一步用到 $\epsilon^{1/i}\to 1$（当 $i\to\infty$）。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这一小题只有一行真正的技术动作，其余全是读图。那个动作是：把「取幂之后超过阈值」翻译成「取幂之前超过另一个阈值」。因为 $x\mapsto x^{i}$ 在 $[0,1]$ 上严格递增，所以对任何一个正数 $c$，事件 $\lbrace |X_i|^{i}>c \rbrace$ 与事件 $\lbrace |X_i|>c^{1/i} \rbrace$ 是同一个集合，一步不差。这个搬移是 monotone bijection（单调双射）在事件上的用法，和 6.042J 里用双射数集合基数是同一件事，只不过这里搬的不是元素个数，而是概率质量。
>
> 为什么必须搬？因为 $X_i^{i}$ 的分布不好直接写，它要在 $[-1,1]$ 上做一次非线性 change of variable（变量替换），密度会被 $i x^{i-1}$ 扭得很厉害；而搬回 $X_i$ 之后，面对的仍然是一个 uniform distribution（均匀分布），密度永远是 $1/2$，只剩纯几何。这就是「不搬会怎样」的答案：不搬要算一条被幂函数拉变形的密度，搬了只需算两段线段的长度。所谓技巧，绝大多数时候就是「换一个等价的问题，让已知工具能接上」。
>
> 现在读图。$[-1,1]$ 上的 density（密度）是常数 $1/2$，所以任何区间的概率就是区间长度的一半。阈值 $a=c^{1/i}$ 满足 $a^{i}=c$，事件 $\lbrace |X_i|>a \rbrace$ 对应左端 $[-1,-a]$ 与右端 $[a,1]$ 两段，总长 $2(1-a)$，概率是 $1-a$。关键位置就在这个 $a$ 上：它随 $i$ 增大而向 1 靠拢，于是两段越来越窄，全部质量向中间收。换句话说，幂函数 $x^{i}$ 在 $[0,1)$ 上把接近 1 的值压成接近 1、把中段压成 0，取幂这个动作本身就是一个把质量往 0 挤的压缩器，而 $a$ 度量的是「挤压还剩多厚的一层皮」。
>
> 数字能把这一步钉死。取 $c=0.5$：$i=1$ 时 $a=0.5$，概率 $1-0.5=0.5$；$i=10$ 时 $a=0.5^{0.1}=\exp(-0.06931)=0.9330$，概率 $0.0670$；$i=100$ 时 $a=0.5^{0.01}=\exp(-0.006931)=0.99309$，概率 $0.00691$。再取 $c=0.25$、$i=10$：$a=0.25^{0.1}=\exp(-0.13863)=0.8706$，概率 $0.1294$。四组数字全部落在同一族曲线 $1-\exp(\ln c/i)$ 上。
>
> 速率可以从这族曲线直接读出来，这比结果本身更有用。由 $a=\exp(\ln c/i)$ 与 $1-\exp(u)\approx -u$（$u$ 接近 0），得 $1-a\approx -\ln c/i=|\ln c|/i$。也就是说概率以「$1/i$ 的速度」下降，不是指数速度。核对：$c=0.5$、$i=100$ 时近似给 $0.6931/100=0.006931$，真值 $0.006910$，相对误差 0.3%。这个 $1/i$ 与前面第 1 题的 $1/\sqrt{n}$ 形成对照：两个题目都用 Chebyshev（切比雪夫）式的语言问收敛，但真正的衰减速率来自具体分布，不能靠一般不等式读出来。这也解释了为什么教材只要求证 convergence in probability（依概率收敛），而不问速率 —— 速率是分布的函数，定理给不出来。
>
> 再往上一层，这条线索通向一个更强的结论。$x^{i}$ 在 $x$ 属于 $[0,1)$ 时逐点趋于 0，只在 $x=1$ 这一个点等于 1，而单点对 uniform distribution（均匀分布）的概率为零，所以实际上 $Z_i=X_i^{i}$ 以概率 1 收敛到 0，这叫 almost sure convergence（几乎必然收敛），比依概率更强。教材只证弱的那一个，是因为这门课此刻手上的工具只有切比雪夫那一套；强收敛要等 Borel 与 Cantelli 的语言。注意「逐点收敛但不一致收敛」在这里同时成立：$x^{i}$ 与极限函数的偏离在 $x\to 1$ 处始终保持为 1，上确界距离不趋于零，可那条「不收敛的尾巴」被压缩在测度为零的一点上，于是概率完全不受影响。这正是「逐点」与「几乎处处」两套语言必须分开的原因。
>
> 最后接一条反向的线索，它在这门课后面会重新出现。若改用 cumulative distribution function（累积分布函数）来描述，$Z_i$ 的表达式是 $F(z)=\frac{1+z^{1/i}}{2}$（对 $z$ 介于 0 与 1 之间），$i\to\infty$ 时它逐点趋于 1，当 $z>0$ 时；趋于 0，当 $z<0$ 时。这个逐点极限是一条阶跃函数，描述的是「质量全部堆在 0 上」的退化分布。把这一族分布函数当对象来看收敛，得到的是 weak convergence（弱收敛），它与依概率收敛在极限为常数时等价，在极限为随机变量时不等价。probability integral transform（概率积分变换）是同一个观察的逆用：任何连续分布喂进自己的累积分布函数都被拉回 uniform distribution（均匀分布），所以「$x^{i}$ 把质量挤向 0」与「取 $i$ 次根把它拉平」是同一枚硬币的两面，这两面在后面做 simulation（模拟）与采样时天天要用。

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（http://ocw.mit.edu）　6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010。如需了解这些材料的引用方式或我们的使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>
