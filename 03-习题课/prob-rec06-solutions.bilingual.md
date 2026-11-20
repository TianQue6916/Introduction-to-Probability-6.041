# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 11 — Derived distributions; convolution; covariance and correlation（导出分布；卷积；协方差与相关系数）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture overview（本讲导读）</span>

**阅读（Readings）**：完成 Section 4.1；Section 4.2。

本讲三条战线：导出分布收尾（一般单调公式；两个随机变量的函数之和与比）；convolution（卷积）——独立随机变量之和的分布；covariance（协方差）与 correlation（相关系数）——两个变量如何共舞的度量。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.202–218；§4.2, p.217–222</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲三条战线层层递进。其一，把上讲的两步 CDF 法压缩成一行公式——$g$ 严格单调时 $f_Y(y) = f_X(x) / |g'(x)|$，并把函数从一元推广到二元（和与比值）；其二，卷积：独立随机变量之和的分布怎么求，离散、连续各一套；其三，协方差与相关系数——不再制造新分布，而是给"两个变量的联动"造一个无量纲的度量，为下一讲的条件期望与"随机个随机变量之和"备好零件。经核对页码，§4.1 Derived Distributions（p.202 起，卷积小节在 p.213–218）本讲读完收尾，§4.2 Covariance and Correlation（标题页 p.217、总结页 p.222）随后展开——阅读说明里的"Finish Section 4.1"正指补完上讲只开了头的 §4.1。上讲铺垫的 $Y = X^3$ 与 $Y = aX + b$ 两例，将在本讲获得统一的公式化解释。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">A general formula（一般公式）</span>

- 设 $Y = g(X)$，$g$ strictly monotonic（严格单调）。

> <span style="color:#7f8c8d;">图：曲线 $y = g(x)$，在 $x$ 处标注斜率 $\frac{dg}{dx}(x)$；横轴上的小区间 $[x,\ x + \delta]$ 被曲线映到纵轴上对应的小区间 $[y,\ y + \cdot]$。</span>

- 事件 $\{x \le X \le x + \delta\}$ 与 $\{g(x) \le Y \le g(x + \delta)\}$ 相同，近似地即 $\{g(x) \le Y \le g(x) + \delta\, |(dg/dx)(x)|\}$。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：图解注 + 第一性原理。** 上面那张图只有四个零件：横轴上的小区间 $[x,\ x+\delta]$、竖轴上的像区间、曲线 $y = g(x)$、以及标在 $x$ 处的那条切线斜率。读图的顺序是固定的三步：先在横轴上框出一小段，再把这段的两端顺着曲线抬到纵轴上，最后发现纵轴上也落下了一小段。关键位置是那支斜率笔——它决定了两段长度之间的兑换价，其余一切都是它的派生。看懂这一点，后面的公式就不必背了。
>
> probability density（概率密度）的数值本身没有独立含义，它只是一张汇率表，把一段 interval（区间）的长度换算成 mass（概率质量）。所以图中横轴那一段装的质量是 $\delta f_X(x)$，而不是 $f_X(x)$。为什么必须乘 $\delta$：密度的量纲是「每单位长度的概率」，只有乘上长度才回到无量纲；不乘就等于把「每公里有几个加油站」当成「有几个加油站」，量级全错。这个近似的误差来自 $f_X$ 在区间内并非严格常值，把 $f_X$ 在 $x$ 处展开，误差是 $\delta$ 的二阶小量，所以 $\delta$ 越小越准，取极限时误差彻底消失。
>
> 这一段质量被 $g$ 搬到竖轴上以后，长度变了。变化率是 $|g'(x)|$：因为 $g(x+\delta) - g(x)$ 的一阶近似就是 $g'(x)\,\delta$，这正是 Taylor expansion（泰勒展开）在一点邻域里的标准用法。跨课程连接：在 Strang 的 linear algebra（线性代数）里，一个线性映射把体积放大 determinant（行列式）的绝对值倍；一维时这个映射就是 $u \mapsto g'(x)\,u$，一个 $1 \times 1$ 的 matrix（矩阵），它的 determinant 就是 $g'(x)$。所以公式里的 $|g'|$ 不是天上掉下来的一个导数，它是 Jacobian determinant（雅可比行列式）在一维退化后的样子。这也解释了为什么多元换元的 formula（公式）里永远是 $|\det J|$，形状完全一致，只是把一维的乘数换成了行列式。
>
> 绝对值不是装饰。$g$ 递减时，像区间的两端左右互换，长度仍然是正数，而 $g'$ 本身是负的，所以必须取 absolute value（绝对值）才配称长度。真正的边界条件在 $g'(x) = 0$ 处：那里一阶近似退化为零长度，压缩比趋于无穷，公式的分母归零，说明这种情形必须回退到 CDF（cumulative distribution function，累积分布函数）法重算。$Y = |X|$ 就是典型——在 $0$ 附近两条支路被折叠到一起，质量在一点上叠加，strictly monotonic（严格单调）这个前提已经被破坏，公式对它不成立。
>
> 代数字进去看第一个例子。取 $X$ uniform（均匀）落在 $[0,1]$ 上，于是 $f_X(x) = 1$；令 $Y = 2X$，则 $g'(x) = 2$，反解 $x = y/2$，代入公式得 $f_Y(y) = 1/2$，范围 $0 < y < 2$。验算：$\int_0^2 (1/2)\, dy = 1$。反证一下不除 $|g'|$ 的后果：若错写成 $f_Y(y) = 1$，则 $\int_0^2 1\, dy = 2$，总质量变成二；而且它会推出 $P(Y \le 1) = 1$，可真实值是 $P(Y \le 1) = P(X \le 1/2) = 1/2$，当场自相矛盾。这就是质量守恒这条第一性原理的用法：任何候选密度先过「总积分为一」这一关，过不了就一定是错的。
>
> 再看一个非线性的例子。同样 $X$ 在 $[0,1]$ 上 uniform，令 $Y = X^2$，则 $g'(x) = 2x$，反解 $x = \sqrt{y}$，代入得 $f_Y(y) = 1/(2\sqrt{y})$，范围 $0 < y \le 1$。验算：$\int_0^1 \frac{1}{2\sqrt{y}}\, dy = [\sqrt{y}]_0^1 = 1$。注意 $y$ 趋于零时这个密度趋于无穷，但概率一点都没爆炸：$P(Y \le 0.01) = \int_0^{0.01} \frac{dy}{2\sqrt{y}} = 0.1$，只有一成。这条要记牢——density（密度）的绝对值大小不能用来比较「哪个更可能」，它只在与长度相乘之后才有意义。$X^2$ 把靠近零的一长段 $x$ 压进了靠近零的一小段 $y$，质量被挤稠，密度就飙高；反过来 $y$ 接近一时 $x$ 的变化被拉伸，密度降到 $1/2$。
- 因此（$y = g(x)$）：
```math
\delta\, f_X(x) = \delta\, f_Y(y)\, \left| \frac{dg}{dx}(x) \right| \qquad \Longrightarrow \qquad f_Y(y) = \frac{f_X(x)}{\left| \frac{dg}{dx}(x) \right|} .
```

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.211–213</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 公式的发动机是概率质量守恒：$x$ 处长 $\delta$ 的小段含质量 $\delta f_X(x)$；$g$ 严格单调时它被一一映到 $y = g(x)$ 附近长约为 $\delta\, |g'(x)|$ 的小段，该段质量是 $\delta f_Y(y)\, |g'(x)|$。两者是同一批质量的两种记账，相等；除以 $\delta$ 取极限即得 $f_Y(y) = f_X(x) / |g'(x)|$（$y = g(x)$）。绝对值照顾递减情形：$g$ 下降时像区间在 $y$ 轴上反向放置，长度仍是 $|g'| \delta$——上讲的 $T = 200/V$ 就吃到了这个负号。与上讲对账：$Y = X^3$（$X$ 在 $[0,1]$ 上均匀分布，故 $f_X(x) = 1/2$），$g' = 3x^2$，反解 $x = y^{1/3}$，代入得 $f_Y(y) = \frac{1}{2} \cdot \frac{1}{3 y^{2/3}} = \frac{1}{6 y^{2/3}}$ ✓，与两步 CDF 法逐点吻合。卡点：使用公式必须配套"反解 $x = g^{-1}(y)$"并逐段携带定义域；$g'(x) = 0$ 的驻点处公式失效，需回退到 CDF 法单独处理。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example: the ratio Z = Y/X（例：比值 Z = Y/X 的分布）</span>

> <span style="color:#7f8c8d;">图：单位正方形上 $f_{X,Y}(y,x) = 1$ 的均匀联合密度（横轴 $x$、纵轴 $y$、高度 $1$）；任务是求 $Z = g(X, Y) = Y/X$ 的 PDF。</span>

**课堂填空**：
- 当 $z \le 1$：$F_Z(z) = \underline{\qquad}$
- 当 $z \ge 1$：$F_Z(z) = \underline{\qquad}$
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：第一性原理 + 证明策略模板。** 先回答「凭什么要分 $z \le 1$ 和 $z \ge 1$ 两段」。$Z = Y/X$ 定义在 unit square（单位正方形）$[0,1]^2$ 上，联合密度恒为 $1$，所以任何事件的概率都等于面积。事件 $\{Z \le z\}$ 翻译成区域 $\{y \le zx\}$。这条直线从原点出发往上扫，扫到哪条边界停下，决定了积分上限写什么。$z \le 1$ 时直线与正方形在右边界 $x = 1$ 处相交，纵坐标是 $z \le 1$，没顶到上边界；$z > 1$ 时它先撞上边界 $y = 1$，交点的横坐标是 $x = 1/z$。所以「哪条边界在起作用」在 $z = 1$ 处换班，分段点就诞生在这里。
>
> 这个现象在 6.006 反复出现：约束集合的形状由「哪一组约束取等号」决定，取等号的那组一换，解就换公式。在 linear programming（线性规划）里它叫 active constraint（有效约束）切换；在 Dijkstra 里它是「当前最短的未访问点」换人。分布推导里的分段点，本质是同一个几何事实在二维面积上的投影。
>
> 先算 $0 \le z \le 1$。用 double integral（二重积分）：对每个 $x$，$y$ 从 $0$ 走到 $zx$，再让 $x$ 从 $0$ 走到 $1$，联合密度是 $1$，所以面积直接给出概率：$\int_0^1 zx\, dx = z/2$。换个积分次序验算：固定 $y$，$x$ 从 $y/z$ 走到 $1$，得 $\int_0^z (1 - y/z)\, dy = z - z/2 = z/2$，两条路径同值。这一步的合法性来自 Fubini 定理，对连续密度恒成立，不用担心。
>
> 再算 $z \ge 1$。此时区域 $\{y \le zx\}$ 几乎占满整个正方形，直接积要按 $x \le 1/z$ 和 $x > 1/z$ 分两段，多一次讨论。改用 complement（补集）法：算剩下那个上三角 $\{y > zx\}$ 的 area（面积），$x$ 从 $0$ 走到 $1/z$，$y$ 从 $zx$ 走到 $1$，面积 $\int_0^{1/z} (1 - zx)\, dx = 1/z - 1/(2z) = 1/(2z)$。所以 $F_Z(z) = 1 - 1/(2z)$。判断用不用补集的准则很实用：目标区域「大」就补，「小」就直算；这里大区域是正方形减一块三角形，补出来的那块积分上限还带 $z$，但只需要一段。
>
> 代数字检验。$z = 1/2$：$F_Z = 1/4$，求导得 $f_Z = 1/2$。$z = 2$：$F_Z = 1 - 1/4 = 3/4$，$f_Z = 1/(2 \cdot 4) = 1/8$。$z = 1$：两边公式都给 $1/2$，故 $F$ 连续；两支求导也同在 $1/2$，故 density（密度）也连续，这不是巧合——两段本来就是同一块区域在分界线处的两种描述。尾部抽查：$P(Z > 10) = 1 - F_Z(10) = 1/20 = 0.05$，说明比值超过十的概率还有五个百分点。
>
> 把上面的动作提炼成模板，一共四步。第一步定范围：$Z$ 取哪些值，$F$ 从 $0$ 单调升到 $1$。第二步翻译事件：把 $\{Z \le z\}$ 写成 $\{(X, Y) \in D_z\}$，等价变形里凡是除以 $X$、乘过不等号的地方，都要交代 $X > 0$ 这类前提，否则符号会翻。第三步找分界：$D_z$ 的形状（被哪条边界截断）改变的地方就是分段点，通常出现在 $z$ 让直线穿过某个顶点时。第四步求导：若积分上限带 $z$，用 Leibniz rule（莱布尼茨法则）逐项求导。这套四步适用于一切「随机变量的函数」问题，比值、乘积、最大值、最小值都能套。求导之前再做一次自检：把两端的极限代进去，$F_Z$ 必须分别落在零与一，任何一段算错都会在这一步露馅。
>
> 最后留一个警钟。如果懒得分段，把 $F_Z(z) = z/2$ 一路用到 $z = 2$，会算出 $F_Z(2) = 1$，真值是 $3/4$——错得不算离谱，但机制已经全错；再求导会得到 $f_Z(z) = 1/2$ 对一切 $z$ 成立，尾部整个消失，归一化立刻崩掉。顺带一个更狠的事实：$\mathrm{E}[Z]$ 根本不存在，因为 $\int_1^\infty z \cdot \frac{1}{2z^2}\, dz = \int_1^\infty \frac{dz}{2z}$ 发散；这也对得上原始定义 $\mathrm{E}[Y/X] = \int_0^1\!\!\int_0^1 \frac{y}{x}\, dx\, dy$，内层对 $x$ 积分时在零附近对数发散。均值不存在的分布并不稀奇，比值型统计量是最常见的出处。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.215–218</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 逐段推导并验算：$F_Z(z) = P(Y/X \le z) = P(Y \le zX)$（$X \ge 0$ 可直接乘过去）。$0 \le z \le 1$：直线 $y = zx$ 从单位正方形切下三角形，面积 $\int_0^1 zx\, dx = z/2$，故 $F_Z(z) = z/2$ ✓。$z \ge 1$：取补集更省事——正方形内 $y > zx$ 的三角形面积 $\int_0^{1/z} (1 - zx)\, dx = \frac{1}{2z}$，故 $F_Z(z) = 1 - \frac{1}{2z}$ ✓。$z < 0$ 时 $F_Z(z) = 0$（两变量非负）。连续性对账：$F_Z(1^-) = 1/2 = F_Z(1^+)$ ✓；又由 $X, Y$ 地位对称，$P(Y \le X) = 1/2$ 本在情理之中。求导得 $f_Z(z) = 1/2$（$0 < z \le 1$）、$f_Z(z) = 1/(2z^2)$（$z \ge 1$）；归一化 $\frac{1}{2} + \int_1^\infty \frac{dz}{2z^2} = \frac{1}{2} + \frac{1}{2} = 1$ ✓。卡点诊断：比值分布的右尾按 $1/z^2$ 衰减得很慢——分母偶尔贴近 $0$ 会制造极端比值，这是比率型统计量的通病，值得记住。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The distribution of X + Y（X + Y 的分布：离散情形）</span>

- $W = X + Y$；$X, Y$ independent（独立）。

> <span style="color:#7f8c8d;">图：二维格点图——把 $(x, y)$ 格点摆平面，质量沿斜线 $x + y = w$ 收集；图中 $w = 3$ 的对角线上标出 $(0,3), (1,2), (2,1), (3,0)$ 四个点。</span>

```math
p_W(w) = P(X + Y = w) = \sum_x P(X = x)\, P(Y = w - x) = \sum_x p_X(x)\, p_Y(w - x).
```
- **Mechanics（机械步骤）**：
  - 把两张 PMF 上下对齐摆放；
  - 翻转（flip）$Y$ 的 PMF；
  - 把翻转后的 PMF 平移 $w$（$w > 0$ 时向右移）；
  - 逐点交叉相乘再相加。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：证明策略模板 + 跨课程连接。** 先把公式的来历拆开。$\{W = w\}$ 这个事件被按 $X$ 的取值切成互斥的片：对每个 $x$，片是 $\{X = x,\ Y = w - x\}$。切法合法靠的是 countable additivity（可列可加性），片与片不重叠，并起来正好是整个事件。每一片的概率写成边缘乘条件，即 $p_X(x)$ 乘以条件概率，再用 independence（独立）把条件概率换成边缘概率 $p_Y(w - x)$。所以这条公式不是定义，是两条公理的合成物：划分给出「怎么切」，独立给出「每片多重」。
>
> 为什么 $Y$ 的指标偏偏是 $w - x$？因为一旦 $X = x$ 定下，总和要等于 $w$，$Y$ 就只剩 $w - x$ 这一条路，没有任何自由度。这就是「沿斜线收集质量」那句画意的代数版：所有和为 $w$ 的点对 $(x,\ w - x)$ 落在同一条斜线上，公式做的就是把这条线上的质量逐点累加。顺带做一次量纲检查：每片的权重必须是两个概率相乘。若误写成相加，在 $p_X = p_Y = p$ 的最简情形下每片就有 $2p$，累加几片立刻越过一，整张表就不再是分布——这是判断公式对不对最快的哨兵。
>
> flip-and-shift 里的「翻转」也不是硬造的花招。令 $j = w - x$，则 $x = w - j$：$p_Y(w - x)$ 作为 $x$ 的函数，正着走过去等于把 $p_Y$ 倒着读一遍，视觉上就是把一条纸带翻面。翻过来以后，两个序列里「脚标相加等于 $w$」的那些项正好上下对齐，逐点相乘再求和就是一次内积。这套动作与 polynomial（多项式）相乘完全同构：两组系数相乘后按次数归并，$\sum_x p_X(x)\,p_Y(w - x)$ 正是 $w$ 次项的系数。CLRS 第 30 章讲的 polynomial multiplication（多项式乘法）就是同一件事，只是换了个名字。
>
> 再往上一层，把它写成 dynamic programming（动态规划）的递推。记 $q_m(w) = P(X_1 + \cdots + X_m = w)$，则有 $q_m(w) = \sum_x q_{m-1}(w - x)\, p_{X_m}(x)$：前 $m - 1$ 个变量的和已经算好，最后一个补上 $x$。这与 6.006 的 knapsack（背包）里那条 $dp[i][s] = \sum_k dp[i-1][s-k]$ 是同一个模板——状态是「前 $i$ 件、和 $s$」，转移是「枚举第 $i$ 件的取值」。差别只在语义：背包累加的是价值，这里累加的是概率，所以输出天然仍是 probability mass function（概率质量函数）。
>
> 复杂度上，支撑集各含 $N$ 个点时一次卷积是 $O(N^2)$，$m$ 个变量逐个卷是 $O(mN^2)$；用 doubling（倍增）可以压到 $O(N^2 \log m)$，因为两两卷、四四卷、八八卷，卷的次数只按对数增长。真正把 $N^2$ 打掉的是 FFT（fast Fourier transform，快速傅里叶变换）：1965 年 Cooley 与 Tukey 在 Mathematics of Computation 上给出 $O(N\log N)$ 的算法，原理是把序列送进频率域，在那里 convolution（卷积）退化成逐点相乘。值得注意的是 Gauss 早在 1805 年为 Pallas 与 Juno 两颗小行星做轨道插值时就用过同一种分解，只是没有发表，这条算法因此在纸上被埋了一百六十年才被现代机器重新捡起来。
>
> 代入数字收尾。设 $X$ 取 $0,1,2$ 的概率为 $1/4,\ 1/2,\ 1/4$（正是二项分布 $B(2, 1/2)$），$Y$ 取 $0,1$ 的概率各为 $1/2$。则 $p_W(0) = (1/4)(1/2) = 1/8$；$p_W(1) = (1/4)(1/2) + (1/2)(1/2) = 3/8$；$p_W(2) = (1/2)(1/2) + (1/4)(1/2) = 3/8$；$p_W(3) = (1/4)(1/2) = 1/8$。四项合计为一，且与 $B(3, 1/2)$ 逐项相同；期望 $\mathrm{E}[W] = 1 \cdot \frac{3}{8} + 2 \cdot \frac{3}{8} + 3 \cdot \frac{1}{8} = 1.5$，恰等于 $1 + 0.5$，与期望的线性性吻合。这说明 binomial（二项）分布在卷积下封闭：独立二项相加，参数 $n$ 与 $p$ 各自相加，这是本讲第一个「卷积不制造新家族」的例子，下一个例子就是正态。这一点在工程上很实用：要抽一个 $B(3, 1/2)$ 样本，只需独立抽三个 Bernoulli（伯努利）变量再相加，不必为每个 $n$ 单独写一套抽样代码。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.213–218</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 跨课程连接）:**</span> 命名模板——flip-and-shift（翻转–平移）卷积机械：把 $p_Y$ 翻转得 $p_Y(-x)$、平移 $w$、与 $p_X$ 逐点相乘再累加，输出恰为 $p_W(w) = \sum_x p_X(x) p_Y(w - x)$。最小验算：$X, Y$ 独立同取 $\{0, 1\}$ 上均匀，则 $p_W(0) = 1/4$、$p_W(1) = 1/2$、$p_W(2) = 1/4$ ✓——与二项 $B(2, 1/2)$ 完全一致，且 $\mathrm{E}[W] = 1$ 与 Lec 07 的期望线性吻合。跨课程连接：你在 6.042J（Mathematics for Computer Science，计算机科学的数学）见过 generating function（生成函数）——独立和的 PGF（probability generating function，概率生成函数，即把 PMF 的每一项 $p(k)$ 作为 $z^k$ 的系数拼成的幂级数 $\sum_k p(k) z^k$）等于各自 PGF 的乘积，"多项式相乘、按 $w$ 次幂收集系数"正是 $\sum_x p_X(x) p_Y(w - x)$ 的代数化身；flip-shift 的几何操作与多项式乘法的对位是同一件事的两面。这页"沿斜线 $x + y = w$ 收集质量"的格点图像值得在脑中存一份——下一页它将被积分解读。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The continuous case（连续情形：卷积）</span>

- $W = X + Y$；$X, Y$ 独立。

> <span style="color:#7f8c8d;">图：把格点图换成连续平面——质量沿直线 $x + y = w$ 收集，竖直线 $x$ 固定处，$w$ 轴上平移量为 $w - x$。</span>

- 给定 $X = x$，$W = x + Y$ 只是 $Y$ 的平移：$f_{W|X}(w \mid x) = f_Y(w - x)$。
- 乘法公式展开联合密度：$f_{W,X}(w, x) = f_X(x)\, f_{W|X}(w \mid x) = f_X(x)\, f_Y(w - x)$。
- 对 $x$ 积分（边缘化）：
```math
f_W(w) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(w - x)\, dx .
```

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.217–218</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Two independent normal r.v.s（两个独立的正态随机变量）</span>

- $X \sim N(\mu_x, \sigma_x^2)$，$Y \sim N(\mu_y, \sigma_y^2)$，相互独立：
```math
f_{X,Y}(x, y) = f_X(x)\, f_Y(y) = \frac{1}{2\pi \sigma_x \sigma_y} \exp\!\left( -\frac{(x - \mu_x)^2}{2\sigma_x^2} - \frac{(y - \mu_y)^2}{2\sigma_y^2} \right).
```
- 该 PDF 在椭圆 $\dfrac{(x - \mu_x)^2}{2\sigma_x^2} + \dfrac{(y - \mu_y)^2}{2\sigma_y^2} =$ 常数 上取常值。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：跨课程连接 + 图解注。** 先说这张等高线图为什么长成椭圆。把 PDF 取对数再取负号，指数上的两个平方项就露了出来：等密度线就是让 $\frac{(x-\mu_x)^2}{\sigma_x^2} + \frac{(y-\mu_y)^2}{\sigma_y^2}$ 等于常数的点集。这不是什么新对象，它就是 center（中心）在 $(\mu_x, \mu_y)$、半轴分别沿两个坐标轴的一条 ellipse（椭圆）。取常数等于 $2c$，半轴长度就是 $\sigma_x\sqrt{2c}$ 与 $\sigma_y\sqrt{2c}$；特别地取 $c = 1/2$，得到所谓的「一西格玛椭圆」，两条半轴恰好就是 $\sigma_x$ 与 $\sigma_y$——这才是「标准差是椭圆半径」这句话的准确含义。
>
> 换成 Strang 的 linear algebra（线性代数）语言，一切都对上。令 $v = (x - \mu_x,\ y - \mu_y)$，协方差矩阵写成 $\Sigma = \mathrm{diag}(\sigma_x^2,\ \sigma_y^2)$，则刚才那个表达式就是 $v^T \Sigma^{-1} v$，一个 positive definite（正定）二次型。Strang 课上讲过：正定二次型的 level set（等值集）是椭圆，主轴方向是特征向量，半轴长度由 eigenvalue（特征值）倒数开方给出。这里 $\Sigma^{-1}$ 的两个特征值是 $1/\sigma_x^2$ 与 $1/\sigma_y^2$，于是半轴是 $\sigma_i\sqrt{2c}$，与直接配方得到的完全一致。还有一条等价链值得记住：两个变量 independent（独立）等价于 $\Sigma$ 是 diagonal（对角）矩阵，也等价于 eigenvector（特征向量）正落在坐标轴上，即椭圆不旋转。三个说法是同一件事的三种语言。
>
> 代数字进去。取 $\sigma_x = 2$、$\sigma_y = 1$、均值为零。在点 $(2, 0)$ 处二次型等于 $1$，在点 $(0, 1)$ 处也等于 $1$，所以两点的 density（密度）完全相同，都等于 $\frac{1}{2\pi \cdot 2} e^{-1/2} \approx 0.0483$。原点处二次型为零，密度取其最大值 $1/(4\pi) \approx 0.0796$。两值之比是 $e^{-1/2} \approx 0.6065$，正是「离开中心一个标准差」的标准衰减倍数——这个数在单变量情形也一样，一维正态在 $\mu \pm \sigma$ 处的密度就是峰值的 0.6065 倍。
>
> 再看等轴的特殊情形 $\sigma_x = \sigma_y = 1$，等高线退化成 circle（圆），密度只依赖半径 $r = \sqrt{x^2 + y^2}$。用极坐标积一次：$P(R \le r) = \int_0^{r} \int_0^{2\pi} \frac{1}{2\pi} e^{-\rho^2/2}\, \rho\, d\theta\, d\rho = 1 - e^{-r^2/2}$。代入 $r = 1$ 得 $1 - e^{-1/2} = 0.3935$，即一个标准差圆内只装了 39.35% 的概率；$r = 2$ 时是 $1 - e^{-2} = 0.8647$。这里有个必须纠正的直觉：很多人以为「一个标准差内六成八」在二维也成立，那是单变量的一维经验法则；二维的圆面积随半径平方长，所以同一半径要掉到不足四成。
>
> 读这张图按三步走。第一步找中心，它就是 mean（均值）向量。第二步沿两条坐标轴量到等高线的距离，量出来的就是两个标准差，同一条等高线上任意方向量都是同一个「距离单位」。第三步看椭圆有多扁，扁的程度就是两个方向不确定性的比值，$\sigma_x / \sigma_y = 2$ 的那个例子扁成二比一，一眼就能看出哪个方向更「散」。等轴即圆，说明两个方向同等不确定，这就是各向同性的图形版本。
>
> 这套几何对下一节的卷积直接有用：两个独立正态相加，协方差矩阵相加，对角阵加对角阵仍是对角阵，二次型相加仍是二次型，所以等高线仍是轴对齐椭圆，和的分布仍是正态。后面那段配方运算看起来很代数，几何上只是「两个椭圆叠起来还是椭圆」。再往前一步：若 $\Sigma$ 非对角，椭圆就旋转，主轴方向由 eigenvector（特征向量）给出，把数据投到主轴上就是 PCA（principal component analysis，主成分分析），也就是 SVD 的一次应用；现代的高斯混合模型与卡尔曼滤波，全都建立在这张等高线图上。
- $\sigma_x = \sigma_y$ 时椭圆成为圆（circle）。

> <span style="color:#7f8c8d;">Bertsekas §3.4, p.157–164；§3.3, p.154</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The sum of independent normal r.v.s（独立正态随机变量之和）</span>

- $X \sim N(0, \sigma_x^2)$，$Y \sim N(0, \sigma_y^2)$，独立；令 $W = X + Y$：
```math
f_W(w) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(w - x)\, dx = \frac{1}{2\pi \sigma_x \sigma_y} \int_{-\infty}^{\infty} e^{-x^2/(2\sigma_x^2)}\, e^{-(w - x)^2/(2\sigma_y^2)}\, dx \overset{\text{（代数整理）}}{=} c\, e^{-\gamma w^2}.
```
- **结论**：$W$ 是 normal（正态）的：
  - mean（均值）$= 0$，variance（方差）$= \sigma_x^2 + \sigma_y^2$；
  - 均值非零的情形用同样的论证处理。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.217–218</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 被卷积代数吞掉的细节补全：把指数展开 $-\frac{x^2}{2\sigma_x^2} - \frac{(w - x)^2}{2\sigma_y^2}$，按 $x$ 配方后剩余项恰为 $-\frac{w^2}{2(\sigma_x^2 + \sigma_y^2)}$，即 $\gamma = \frac{1}{2(\sigma_x^2 + \sigma_y^2)}$——被积函数是 $e^{-\gamma w^2}$ 乘一个 $x$ 的高斯核，对 $x$ 积分只贡献常数 $c$。形状已是正态，常数由归一化自动定为 $c = 1/\sqrt{2\pi(\sigma_x^2 + \sigma_y^2)}$，无需硬算 ✓。交叉验证方差：零均值时 $\mathrm{var}(W) = \sigma_x^2 + \sigma_y^2$，恰是 Lec 07 方差和规则给出的值——卷积与方差两条独立推导互相咬合 ✓。均值非零时，把 $W$ 写成"零均值部分 $+ (\mu_x + \mu_y)$"，再用上讲 $Y = aX + b$ 的平移结论即可 ✓。跨课程连接：配方在 Strang（Gilbert Strang）线代里是"二次型相加仍是二次型"的一维情形——正定型对加法封闭，正是正态族卷积封闭性的线代影子；这层封闭性让正态族成为后续讲义反复调用的高斯工具箱。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Covariance（协方差）</span>

- 定义：$\mathrm{cov}(X, Y) = \mathrm{E}\big[(X - \mathrm{E}[X]) \cdot (Y - \mathrm{E}[Y])\big]$。
- 零均值情形：$\mathrm{cov}(X, Y) = \mathrm{E}[XY]$。

> <span style="color:#7f8c8d;">图：两张散点图——左图点云沿正向倾斜（正协方差：两个中心化变量同进退），右图点云沿负向倾斜（负协方差：一升一降）。</span>

- 展开式：$\mathrm{cov}(X, Y) = \mathrm{E}[XY] - \mathrm{E}[X]\,\mathrm{E}[Y]$。
- 多变量方差公式：
```math
\mathrm{var}\!\left( \sum_{i=1}^{n} X_i \right) = \sum_{i=1}^{n} \mathrm{var}(X_i) + 2 \sum_{(i,j):\, i<j} \mathrm{cov}(X_i, X_j).
```
- 独立 $\Rightarrow \mathrm{cov}(X, Y) = 0$（converse is not true，逆命题不真）。

> <span style="color:#7f8c8d;">Bertsekas §4.2, p.221–222</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> "独立 $\Rightarrow$ 不相关"一行证完：$\mathrm{E}[XY] = \mathrm{E}[X]\mathrm{E}[Y]$（Lec 07 已证），代入 $\mathrm{cov}(X,Y) = \mathrm{E}[XY] - \mathrm{E}[X]\mathrm{E}[Y] = 0$ ✓。逆命题不真——反例（译者补）：$X \sim U[-1, 1]$（$U$ 即 uniform，均匀分布），$Y = X^2$。$\mathrm{E}[X] = 0$ 且 $\mathrm{E}[XY] = \mathrm{E}[X^3] = 0$（奇函数在对称区间上的积分为零），故 $\mathrm{cov}(X, Y) = 0$；但 $Y$ 由 $X$ 完全决定，相依到极致 ✓。含义：协方差只捕捉"线性同向/反向"的关联，对二次曲线型的关联视而不见。多变量方差公式是 Lec 07 两个幽灵陷阱的解剖图：$X = Y$ 时 $\mathrm{cov}(X, Y) = \mathrm{var}(X)$，和的方差翻 4 倍；$X = -Y$ 时 $\mathrm{cov} = -\mathrm{var}(X)$，完全对消；独立时全部交叉项消失。中心化乘积 $(X - \mathrm{E}[X])(Y - \mathrm{E}[Y])$ 的符号语义：两家同时高于/低于各自的平均为正，一高一低为负——散点图的倾斜方向由此而来。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Correlation coefficient（相关系数）</span>

- 协方差的无量纲（dimensionless）版本：
```math
\rho = \mathrm{E}\!\left[ \frac{X - \mathrm{E}[X]}{\sigma_X} \cdot \frac{Y - \mathrm{E}[Y]}{\sigma_Y} \right] = \frac{\mathrm{cov}(X, Y)}{\sigma_X\, \sigma_Y}.
```
- $-1 \le \rho \le 1$。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：历史与人物 + 第一性原理。** 这个量不是 Pearson 一个人造出来的。1846 年法国矿物学家 Bravais 研究测量点的误差椭圆时，第一次写下二维正态的联合密度并引入乘积矩，所以老文献里它叫 Bravais coefficient（布拉维系数）。Galton 在 1886 年分析九百多名成年子女与中亲身高，发现等高线是同心椭圆，并造出 regression（回归）一词来描述「极端父母的子女没那么极端」这一现象。Pearson 在 1895 年 9 月提交、1896 年发表在 Philosophical Transactions of the Royal Society A 第 187 卷 253 至 318 页的那篇长文里，才把它整理成今天的公式与符号。代价要记住：Pearson 的推导假设二维正态，而样本相关系数的精确分布直到 1915 年才由 Fisher 在 Biometrika 第 10 卷 507 至 521 页给出，这中间十几年想对 $\rho$ 做显著性检验，只能靠查表凑。
>
> 第二层问题是：界为什么恰好是正负一。把两个变量各自中心化再除以标准差，得 $u = (X - \mu_X)/\sigma_X$ 与 $v = (Y - \mu_Y)/\sigma_Y$，这两个新变量的平方期望都是 $1$。在随机变量空间上定义 inner product（内积）为 $\langle A, B\rangle = \mathrm{E}[AB]$，则 $u$、$v$ 都是单位向量，而 $\rho = \langle u, v\rangle$ 正是夹角余弦。于是 $|\rho| \le 1$ 根本不需要技巧：它是 Cauchy–Schwarz（柯西–施瓦茨）不等式的直接推论。
>
> 端点也直白：$\rho = 1$ 意味着 $u = v$，两者完全正比例；$\rho = -1$ 意味着 $u = -v$，完全负比例。中间的值只是「线性成分」的带符号刻度，没有额外语义。顺便补一段命名史：这个不等式 1821 年由 Cauchy 在《Analyse algébrique》中对有限和给出，1859 年 Bunyakovsky 给出积分形式，1888 年 Schwarz 独立证明并把思想推广到内积空间，三个名字各挂一段历史，所以有的书把它写成 Cauchy–Bunyakovsky–Schwarz（柯西–布尼亚科夫斯基–施瓦茨）不等式。
>
> 代数字检查一个最容易误读的地方。设 $X \sim N(0, 1)$，$\varepsilon \sim N(0, 1)$ 与 $X$ 独立，令 $Y = X + \varepsilon$。则 $\mathrm{cov}(X, Y) = \mathrm{var}(X) + \mathrm{cov}(X, \varepsilon) = 1$，$\sigma_Y = \sqrt{1 + 1} = \sqrt{2}$，所以 $\rho = 1/\sqrt{2} \approx 0.7071$。注意 $Y$ 有一半的方差来自纯噪声，$\rho$ 仍然给出 $0.707$——把 $0.7$ 读成「七成线性」是错的，$\rho$ 与方差占比不是同一个刻度。要问方差占比，看的是 $\rho^2 = 1/2$，它恰好等于可由 $X$ 解释的那部分方差比例，这才是平方 $\rho$ 的正当理由。
>
> 再看这个量的边界在哪。$\rho$ 只认线性，$Y = X^2$ 这种完全相依也能给出零，所以后续发展分成两路。第一路改秩：把每个样本换成它在样本里的排名，再算同样的乘积矩系数，得到 Spearman rank correlation（斯皮尔曼秩相关），它对单调非线性敏感、对 outlier（离群点）稳健，代价是丢掉数值之间的距离信息。第二路换度量：Székely、Rizzo 与 Bakirov 在 2007 年 Annals of Statistics 第 35 卷第 6 期 2769 至 2794 页提出 distance correlation（距离相关），它是第一个满足「取零当且仅当独立」的相依度量，代价是要算 $n^2$ 的距离矩阵，样本一多就吃不动。
>
> 最后给一条读法。$\rho$ 的符号给方向，绝对值给线性强度，平方给可解释比例；它对方差里的大偏差格外敏感，因为每一项都带平方，一个 outlier（离群点）就足以把 $0.9$ 拖到 $0.3$。它也不能倒过来推因果：两个变量同受第三个变量驱动时，$\rho$ 照样很高。这三句话比公式本身更值得记牢——公式翻手册就有，误读的代价却要由用它的人自己承担。
- $|\rho| = 1 \iff (X - \mathrm{E}[X]) = c\, (Y - \mathrm{E}[Y])$（linearly related，线性相关）。
- 独立 $\Rightarrow \rho = 0$（逆命题不真）。

> <span style="color:#7f8c8d;">Bertsekas §4.2, p.221–222</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 界的验算：对任意实数 $t$，$0 \le \mathrm{var}\big(\frac{X}{\sigma_X} + t\, \frac{Y}{\sigma_Y}\big)$，展开得 $0 \le 1 + t^2 + 2 t \rho$；取 $t = \pm 1$ 得 $0 \le 2 \pm 2\rho$，即 $-1 \le \rho \le 1$ ✓。端点语义：取等时该线性组合方差为 0，即退化为常数，故 $|\rho| = 1 \iff$ 标准化后的 $X, Y$ 严格线性相关 ✓。无量纲化的意义：$\mathrm{cov}$ 带着两个变量的量纲（米 × 秒），数值大小不可跨问题比较；$\rho$ 先把两变量各自标准化（除以 $\sigma$）再取期望，成为纯粹形状指标。跨课程连接：用 Strang 线代语言，在中心化随机变量空间上定义内积 $\langle X, Y \rangle = \mathrm{E}[XY]$，则 $\rho$ 恰是 cosine（余弦）相似度 $\cos\theta$，$-1 \le \rho \le 1$ 就是 Cauchy–Schwarz（柯西–施瓦茨）不等式的概率化身；"独立 $\Rightarrow \rho = 0$ 而逆不真"对应"内积为零（正交）但非线性无关"。上一节的反例 $Y = X^2$ 在此依然成立：完全相依却 $\rho = 0$。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
