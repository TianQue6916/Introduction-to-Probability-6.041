<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 8 解答（Recitation 8: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期，2010 年 10 月 5 日）</span>

<span style="color:#1e8449;">**[note]** 本解答 PDF 原文不含题面（各题直接给出解答或教材引用）。为便于阅读，以下各题题面均译自 MIT OCW 同课程配套的《Recitation 8》题目 PDF（官方原文，逐题对应）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

设 $Z$ 为连续随机变量（continuous random variable），其 probability density function（概率密度函数，PDF）为

```math
f_Z(z) = \begin{cases} \gamma\,(1+z^2), & -2 < z < 1, \\ 0, & \text{其余情形（otherwise）}. \end{cases}
```

- **(a)** $\gamma$ 取何值时这才可能成立？
- **(b)** 求 $Z$ 的 cumulative distribution function（累积分布函数，CDF）。

**（a）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 我们知道 PDF 必须积分为 1。因此
>
> ```math
> \int_{-\infty}^{\infty} f_Z(z)\,dz = \int_{-2}^{1} \gamma\,(1+z^2)\,dz = \gamma\left(z + \frac{z^3}{3}\right)\Bigg|_{-2}^{1} = 6\gamma.
> ```
>
> 最后一个等号的代入过程为：$\gamma\Bigl[\bigl(1+\tfrac{1}{3}\bigr)-\bigl(-2-\tfrac{8}{3}\bigr)\Bigr]=\gamma\cdot 6=6\gamma$。由此我们得出 $\gamma = 1/6$。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这一步看起来只是把上下限代进原函数，实质上是在执行 normalization（归一化）条件。probability density function（概率密度函数）在某个点上的取值不是概率，它甚至允许大于 1；只有在一个集合上做积分，才给出该集合的概率。因此 $\int_{-\infty}^{\infty} f_Z(z)\,dz = 1$ 不是额外约定，而是 probability measure（概率测度）总质量为 1 这件事在密度语言下的翻译：整个样本空间就是实数轴，它的概率必须是 1，多一分少一分都不行。
>
> 如果不做这一步会怎样。假设把 $\gamma$ 留着不管，算出的 cumulative distribution function（累积分布函数）在 $z>1$ 处就是 $6\gamma$，而分布函数必须满足 $\lim_{z\to\infty}F(z)=1$。取 $\gamma=1/12$ 试一下：$F(1)=1/2$，于是「$Z$ 落在 $(-2,1)$ 之外」仍有 $1/2$ 的概率，可那一段的密度全是 0。一个密度恒为零的集合却分走半个概率，这直接拆掉了可加性与总质量条件。可见 $\gamma=1/6$ 不是算出来的巧合，而是被逼出来的唯一缩放因子：密度只能决定形状，归一化才把它钉到绝对的尺度上。
>
> 做几个能落到纸上的数。第二段 CDF 在 $z=0$ 处的值是 $\frac{1}{6}\left(0+0+\frac{14}{3}\right)=\frac{14}{18}=\frac{7}{9}\approx0.7778$，说明分布明显偏左，大半质量压在负半轴。再算 $P(-1\le Z\le0)=\frac{1}{6}\left[z+\frac{z^3}{3}\right]_{-1}^{0}=\frac{1}{6}\left(0-\left(-1-\frac{1}{3}\right)\right)=\frac{1}{6}\cdot\frac{4}{3}=\frac{2}{9}\approx0.2222$。区间宽度是 1，概率却只有 0.2222，原因在该处的密度：$f_Z(-1)=\frac{1}{6}(1+1)=\frac{1}{3}$，$f_Z(0)=\frac{1}{6}$，密度小于 1，密度乘长度才会小于长度，这正是「密度不是概率」最直白的证据。
>
> 换到左边一段复核：$P(-2\le Z\le-1)=\frac{1}{6}\left[\left(-1-\frac{1}{3}\right)-\left(-2-\frac{8}{3}\right)\right]=\frac{1}{6}\left(-\frac{4}{3}+\frac{14}{3}\right)=\frac{1}{6}\cdot\frac{10}{3}=\frac{5}{9}\approx0.5556$。两段相加 $\frac{2}{9}+\frac{5}{9}=\frac{7}{9}$，正好等于上面单独算出的 $F_Z(0)$。这不是巧合，而是可加性在实算层面的样子：把 $(-\infty,0]$ 切成两块分别积，和一次性积的结果必须相同；若不同，一定是归一化或代入上下限时出了错，可以拿它当一道免费的验算。
>
> 跨课程看，6.042J discrete mathematics（离散数学）里 probability mass function（概率质量函数）的归一化 $\sum_k p_X(k)=1$ 与这里是同一条要求，连续情形只是把求和换成了 Riemann integral（Riemann 积分）。Thomson 实分析里的结论——Riemann 可积函数的不定积分具有 absolute continuity（绝对连续性），并且在被积函数的连续点处可导且导数等于被积函数——保证了本题的 $F_Z'=f_Z$ 在 $(-2,1)$ 内部处处成立，而在 $z=-2$ 与 $z=1$ 两个断点处 $F_Z$ 没有导数。所以「对 CDF 求导得密度」这条捷径在端点必须单独交代，不能默认整条实轴都可导。这也顺带解释了为什么 PDF 可以在有限个点上任意改值而不改变任何概率：积分对零测集视而不见，唯一的要求是改完之后仍然非负。初学者常把 $f_Z$ 当成 $P(Z=z)$，于是不敢动这些点，其实真正携带概率信息的对象是 CDF，它才是概率的载体。
>
> 至于分段写成 $-2<z<1$ 还是 $-2\le z\le1$，对积分没有任何影响，因为单个点的 Lebesgue measure（Lebesgue 测度）为零。真正要小心的是 CDF 的端点约定：分布函数定义为 $F_Z(z)=P(Z\le z)$，所以 $z=1$ 处必须取 1，$z>1$ 也取 1。若误用 $P(Z<z)$，端点会差出一个 atom（质点）的质量；本题没有质点，看不出差别，但紧接着的 $Y$ 在 $0$ 与 $5$ 处都有质点，那时这个习惯立刻决定对错。
>
> 最后看 $\gamma$ 对区间的依赖。把支撑换成 $(-1,1)$，则 $\int_{-1}^{1}(1+z^2)\,dz=2+\frac{2}{3}=\frac{8}{3}$，$\gamma$ 变成 $\frac{3}{8}$；本题得到 6，是因为支撑长度 3 贡献了 3，而立方项 $\frac{1^3-(-2)^3}{3}$ 也贡献了 3，两项恰好相等，才凑出漂亮的 6。换句话说，$\gamma$ 的量纲是「$z$ 的倒数」，数值只在 $z$ 取定单位时才有意义；把 $z$ 从分钟改成秒，$\gamma$ 要乘 60。这类 scaling（尺度变换）与 CSAPP 里 IEEE 754 只能表示无量纲数的处境相通：单位不由浮点数携带，必须由人维护，一旦糊涂，数字再精确也没有意义。
>
> 按六类的分法，这条属于第一性原理洞察：它拆的是「为什么必须归一化」，而不是「怎么把这个积分算出来」。

**（b）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 为求 CDF，我们积分：
>
> ```math
> F_Z(z) = \int_{-\infty}^{z} f_Z(t)\,dt =
> \begin{cases}
> 0, & z < -2, \\
> \dfrac{1}{6}\left(t + \dfrac{t^3}{3}\right)\Bigg|_{-2}^{z}, & -2 \le z \le 1, \\
> 1, & z > 1,
> \end{cases}
> ```
>
> ```math
> = \begin{cases}
> 0, & z < -2, \\
> \dfrac{1}{6}\left(z + \dfrac{z^3}{3} + \dfrac{14}{3}\right), & -2 \le z \le 1, \\
> 1, & z > 1.
> \end{cases}
> ```
>
> 第二段中 $\dfrac{14}{3}$ 的来历：把下限 $-2$ 代入 $t+\dfrac{t^3}{3}$ 得 $-2-\dfrac{8}{3}=-\dfrac{14}{3}$，减去它等于加上 $\dfrac{14}{3}$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

教材（text）第 186–187 页习题 3.9（Problem 3.9）。Al 家附近的出租车站与公交站在同一处。Al 在某一给定时刻到达该处：若已有出租车在等候（以概率 $2/3$ 发生），他就上车；否则他等待出租车或公交车中先到者。下一辆出租车到达所需的时间均匀分布于 0 到 10 分钟之间，而下一辆公交车恰好在 5 分钟后到达。求 Al 等待时间的 CDF 与期望值。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 题面本身编码了一个结构，先把它读出来，后面所有计算都会变简单：$Y$ 有 $2/3$ 的质量压在 $0$ 这一点上，只有剩下的 $1/3$ 才展开成一段连续分布。这种「一部分质量落在点上、一部分连续铺开」的对象叫 mixed random variable（混合型随机变量）。它既没有纯粹的 probability mass function（概率质量函数），也没有纯粹的 probability density function（概率密度函数）；谁若硬写一个密度，就会在 $0$ 处丢掉 $2/3$ 的质量。正确的统一载体是 cumulative distribution function（累积分布函数），它对离散、连续、混合三种情形一律有效。识别这种结构的办法很朴素：先问「有没有哪几个点各自携带正概率」，若有，就把它们连同各自的质量单独记下，剩下的部分再当连续分布处理，永远不要指望一个公式吞下全部。
>
> 分情形的依据是 law of total probability（全概率定律）。把样本空间按事件 $A=\{\text{已有出租车在候}\}$ 切成 $A$ 与补集 $A^c$ 两块，已知 $P(A)=2/3$。对任意事件 $B$ 有 $P(B)=P(B\mid A)P(A)+P(B\mid A^c)P(A^c)$。这不是新定理，而是可加性加条件概率定义的直接后果：$A$ 与 $A^c$ 互斥且并为全集，所以 $P(B)=P(B\cap A)+P(B\cap A^c)$，再把每一项按条件概率的定义展开。跨课程看，这与 Strang 18.06 里的 direct sum（直和）$V=U\oplus W$ 结构同形：每个向量唯一分解成两块，线性泛函在分块上相加；概率是定义在事件上的可加集函数，分块之后同样相加。区别在于线性代数的补子空间可以任选，概率的分块必须互斥且覆盖全集，而且「块内怎么分布」由条件概率决定，不能自由指定。
>
> 同一件事搬到期望上就是 law of total expectation（全期望定律）：$E[Y]=E[Y\mid A]P(A)+E[Y\mid A^c]P(A^c)$。本题 $E[Y\mid A]=0$，所以只剩 $\frac{1}{3}E[\min\{T,5\}]$。这里有一个高频错误：把 $E[\min\{T,5\}]$ 写成 $\min\{E[T],5\}$。本题 $E[T]=5$，$\min\{5,5\}=5$，而真值是 $3.75$，一下子高估 $1.25$ 分钟，即三分之一。错因是 min 与期望不能交换：$\min\{t,5\}$ 关于 $t$ 是 concave（凹）函数，斜率从 $1$ 掉到 $0$，由 Jensen inequality（Jensen 不等式）只能得到 $E[\min\{T,5\}]\le\min\{E[T],5\}$，等号要求 $T$ 退化。把这条不等式记牢，以后遇到 truncation（截断）、封顶收益、上限保险这类量，先判凸凹就能预判偏差方向，不必等算完才发现不对。
>
> 具体形状算到底。$P(Y=0)=\frac{2}{3}$；因为 $T$ 在 $[0,10]$ 上均匀，$P(T<5)=\frac{1}{2}$，所以 $P(0<Y<5)=\frac{1}{3}\cdot\frac{1}{2}=\frac{1}{6}$；同理 $P(T\ge5)=\frac{1}{2}$，于是 $P(Y=5)=\frac{1}{6}$。请注意 $5$ 处也是一个 atom（质点），题解写「$y\ge5$ 时 $F_Y(y)=1$」其实隐含了一次跳变：$F_Y(5^-)=\frac{2}{3}+\frac{5}{30}=\frac{2}{3}+\frac{1}{6}=\frac{5}{6}$，而 $F_Y(5)=1$，跳幅正好 $\frac{1}{6}$。若读者把 $F_Y$ 当成连续函数直接求导当密度，就会漏掉这 $\frac{1}{6}$ 的质量，算出的期望少了 $\frac{1}{6}\times5=0.8333$：只积连续段得 $\frac{1}{3}\int_{0}^{5}\frac{y}{10}\,dy=\frac{1}{3}\cdot1.25=0.4167$，比正确的 $1.25$ 少 $0.8333$。这个差额可以当成原子是否漏掉的体检指标。
>
> 数值自查。$E[Y]=1.25$ 分钟。对照三种策略：只等出租车，平均 $5$ 分钟；只等公交车，固定 $5$ 分钟；而混合策略下 $2/3$ 的概率根本不用等，期望被压到 $1.25$ 分钟，只有 $5$ 分钟的四分之一。这不是「公交车更快」，而是「有很大概率零等待」——期望被 $0$ 处的质点拉低，尾部的具体形状反而次要。这类结构在统计建模里叫 zero-inflated（零膨胀）模型：先以概率 $p$ 判零，再以 $1-p$ 走一个计数或连续分布，与本题的 $2/3$ 加 $1/3$ 是同一个套路。反过来说，若你只报期望 $1.25$ 分钟，会掩盖「要么立刻走、要么等最多五分钟」的双峰形态，所以描述这种变量时必须同时给 CDF 或分位数。顺带一提，若题目改问「等待超过 $y$ 分钟的概率」，用 $1-F_Y(y)$ 一步可得，根本不必去积密度，这正是 CDF 作为统一载体的好处。
>
> 按六类的分法，这条属于跨课程连接：把全概率定律接到 Strang 18.06 的直和分解上，同时点明两者在分块自由度上的差别。

> <span style="color:#2471a3;">**[solution]**</span>
>
> <span style="color:#1e8449;">**[note]** 原解答仅写「见教材习题 3.9」，此处按教材第 187 页的解法补全，便于读者直接阅读。</span>
>
> 设 $Y$ 为 Al 的等待时间（waiting time）。分两种情况：
>
> - 以概率 $\dfrac{2}{3}$，已有出租车在等候，Al 立即上车，故 $Y=0$；
> - 以概率 $\dfrac{1}{3}$，无出租车在候，此时 $Y=\min\{T,5\}$，其中 $T$ 是下一辆出租车到达所需时间，$T$ 在区间 $[0,10]$ 上均匀分布，即 $T\sim\text{Uniform}(0,10)$（$T$ 的 PDF 为 $f_T(t)=1/10,\ 0\le t\le 10$）。
>
> **求 CDF。** 对 $0\le y<5$，事件 $\{Y\le y\}$ 由「出租车已在候」（概率 $2/3$）与「无车在候且 $T\le y$」两个互斥情形构成，故
>
> ```math
> F_Y(y)=P(Y\le y)=\frac{2}{3}+\frac{1}{3}\,P(T\le y)=\frac{2}{3}+\frac{1}{3}\cdot\frac{y}{10}=\frac{2}{3}+\frac{y}{30}.
> ```
>
> 对 $y\ge 5$，公交车 5 分钟后必到，Al 至多等 5 分钟，故 $F_Y(y)=1$；对 $y<0$，$F_Y(y)=0$。于是
>
> ```math
> F_Y(y)=\begin{cases} 0, & y<0, \\[4pt] \dfrac{2}{3}+\dfrac{y}{30}, & 0\le y<5, \\[4pt] 1, & y\ge 5. \end{cases}
> ```
>
> **求期望。** 由于有 $\dfrac{2}{3}$ 的概率 $Y=0$，故
>
> ```math
> E[Y]=\frac{1}{3}\,E\!\left[\min\{T,5\}\right].
> ```
>
> 对非负随机变量 $\min\{T,5\}$，其期望可用尾部概率公式（tail-sum formula）$E[X]=\int_0^{\infty}P(X>x)\,dx$ 计算：
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条公式值得单独抄成一张卡片：对 nonnegative random variable（非负随机变量），$E[X]=\int_{0}^{\infty}P(X>x)\,dx$。它的价值不在于形式好看，而在于把「求期望」从「密度乘变元再积分」改写成「对生存概率积分」。一旦对象带 truncation（截断）、取 min、或者含 atom（质点），密度写法就得拆成好几段分别处理，而尾部公式一步吞下。本题正是这种情形：$\min\{T,5\}$ 在 $5$ 处压着 $1/2$ 的质量，用密度写必须同时处理连续段与质点，用尾部公式则完全不必拆。
>
> 为什么成立，有两条互不依赖的路。第一条是交换积分次序：$P(X>x)=\int_{x}^{\infty}f(t)\,dt$，于是 $\int_{0}^{\infty}P(X>x)\,dx=\int_{0}^{\infty}\int_{x}^{\infty}f(t)\,dt\,dx=\int_{0}^{\infty}f(t)\left(\int_{0}^{t}dx\right)dt=\int_{0}^{\infty}t f(t)\,dt$。被积函数非负，可以直接套 Fubini theorem（Fubini 定理）的非负版本，也就是 Tonelli theorem（Tonelli 定理）；它保证交换合法，而且不需要事先证明可积，这一点的好处在末尾会看到。第二条是几何读法：$E[X]$ 是曲线 $y=P(X>x)$ 下方的面积，常规算法是竖着切、每列高度 $t$、宽度 $f(t)dt$；尾部公式是横着切、每层厚度 $dx$、长度 $P(X>x)$。同一块面积换了个切法，这就是 layer cake representation（千层饼表示）的字面意思。
>
> 离散版与验算。对非负整值变量有 $E[X]=\sum_{n\ge0}P(X>n)$，同样是横着切。取 geometric distribution（几何分布）$P(X=k)=(1-p)^{k-1}p$，则 $P(X>n)=(1-p)^{n}$，求和 $\sum_{n\ge0}(1-p)^{n}=1/p$，与已知期望一致，说明公式没有漏掉常数项。代一个具体数：$p=1/4$ 时 $1/p=4$，而 $\sum_{n\ge0}(3/4)^{n}=4$，两边对上。这条验算的意义在于：几何分布的期望是教科书结论，若公式与它不符，一定是积分限或写法搞错了；尤其要分清 $P(X>x)$ 与 $P(X\ge x)$，连续情形两者相同，整值情形恰好差一个 $P(X=x)$，这是最容易翻车的细节。回到本题的连续版本：$\int_{0}^{5}\left(1-\frac{y}{10}\right)dy=\left[y-\frac{y^{2}}{20}\right]_{0}^{5}=5-\frac{25}{20}=\frac{15}{4}=3.75$，与题解第 L0095 行一致。
>
> 再用密度写法复核一遍，顺便检验质点有没有被正确处理。$\min\{T,5\}$ 在 $[0,5)$ 上的密度是 $\frac{1}{10}$，在 $5$ 处有质量 $P(T>5)=\frac{1}{2}$。于是 $E=\int_{0}^{5}y\cdot\frac{1}{10}\,dy+5\cdot\frac{1}{2}=1.25+2.5=3.75$，与尾部公式完全一致。这个复核说明尾部公式的真正优势不是「写起来短」，而是对 atom 免疫：它只问 $P(X>x)$ 这一个数，而 CDF 已经把质点编码进去了；密度写法必须记得手动补上「值乘质量」那一项，少写一项就少 $2.5$，占真值的三分之二。
>
> 条件不能丢。$X\ge0$ 是本质前提。若 $X$ 可以取负值，$\int_{0}^{\infty}P(X>x)\,dx$ 算出来的是 $E[X^{+}]$，也就是 positive part（正部）的期望，差额是 $E[X^{-}]$。给个反例：$X\equiv-1$，左边 $\int_{0}^{\infty}P(-1>x)\,dx=0$，右边 $E[X]=-1$，差了整整 1。所以动手前必须先确认下界为零；本题 $Y\ge0$ 由题意保证，题目里那句「等待时间」不是客套话，它就是在保证这个条件。另一个常见疑虑是 $E[X]=\infty$ 时公式还成不成立：成立，因为两边同时发散，而这正是选 Tonelli 版本而不选要求可积的 Fubini 版本的原因。
>
> 顺带一提，若下界是 $a$ 而不是 $0$，平移一下即可：$E[X]=a+\int_{a}^{\infty}P(X>x)\,dx$，推导与上面逐字相同，只是积分从 $a$ 起算。例如 $X$ 在 $[3,8]$ 上均匀，则 $E[X]=3+\int_{3}^{8}\left(1-\frac{x-3}{5}\right)dx=3+2.5=5.5$，与中点 $\frac{3+8}{2}=5.5$ 一致，说明平移版本没有破坏均匀分布的性质。这类平移检查很便宜，却是发现积分限写错的最快手段。
>
> 把它做成可复用的检查清单：遇到 $E[\min\{X,c\}]$、$E[(X-c)^{+}]$、混合分布、以及只给了 survival function（生存函数）而没有密度的可靠性数据，先写 $\int_{0}^{\infty}P(X>x)\,dx$，再用 $P(X>x)=1-F(x)$ 代进去。这个式子在 survival analysis（生存分析）里就是「期望寿命等于生存函数曲线下的面积」，Kaplan–Meier 估计量算平均生存时间用的正是它的离散版本，所以这条公式不是习题技巧，而是那个领域的日常工具。
>
> 按六类的分法，这条属于证明策略模板：核心是「交换积分次序」这一招，以及判断它何时合法的条件。
>
> ```math
> E\!\left[\min\{T,5\}\right]=\int_{0}^{\infty}P\bigl(\min\{T,5\}>y\bigr)\,dy=\int_{0}^{5}P(T>y)\,dy=\int_{0}^{5}\left(1-\frac{y}{10}\right)dy=\left[y-\frac{y^2}{20}\right]_{0}^{5}=5-\frac{25}{20}=\frac{15}{4}.
> ```
>
> 因此
>
> ```math
> E[Y]=\frac{1}{3}\cdot\frac{15}{4}=\frac{5}{4}\ \text{分钟}.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

设 $\lambda$ 为正数。当连续随机变量 $X$ 的概率密度函数为

```math
f_X(x) = \begin{cases} \lambda e^{-\lambda x}, & x \ge 0, \\ 0, & \text{其余情形（otherwise）} \end{cases}
```

时，称 $X$ 为参数（parameter）为 $\lambda$ 的 exponential random variable（指数随机变量）。

- **(a)** 求 $X$ 的累积分布函数（CDF）。
- **(b)** 求 $X$ 的均值（mean）。
- **(c)** 求 $X$ 的方差（variance）。
- **(d)** 设 $X_1$、$X_2$、$X_3$ 为相互独立的、参数均为 $\lambda$ 的指数随机变量。求 $Z = \max\{X_1, X_2, X_3\}$ 的 PDF。
- **(e)** 求 $W = \min\{X_1, X_2\}$ 的 PDF。

**（a）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 对 $x \ge 0$：
>
> ```math
> F_X(x) = \int_{-\infty}^{x} f_X(t)\,dt = \int_{0}^{x} \lambda e^{-\lambda t}\,dt = \Bigl[-e^{-\lambda t}\Bigr]_{0}^{x} = 1 - e^{-\lambda x}.
> ```
>
> 对 $x < 0$，有 $F_X(x) = \int_{-\infty}^{x} f_X(t)\,dt = 0$。于是我们得到
>
> ```math
> F_X(x) = \begin{cases} 0, & x < 0, \\ 1 - e^{-\lambda x}, & x \ge 0. \end{cases}
> ```

**（b）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 下列计算的关键步骤用到分部积分（integration by parts），即以 $u = x$、$dv = \lambda e^{-\lambda x}\,dx$（从而 $du = dx$、$v = -e^{-\lambda x}$）应用公式
>
> ```math
> \int_{0}^{\infty} u\,dv = \Bigl.uv\Bigr|_{0}^{\infty} - \int_{0}^{\infty} v\,du
> ```
>
> 如此有
>
> ```math
> E[X] = \int_{-\infty}^{\infty} x f_X(x)\,dx = \int_{0}^{\infty} x\lambda e^{-\lambda x}\,dx = \Bigl[-x e^{-\lambda x}\Bigr]_{0}^{\infty} + \int_{0}^{\infty} e^{-\lambda x}\,dx = \frac{1}{\lambda}.
> ```
>
> 其中边界项 $\Bigl[-x e^{-\lambda x}\Bigr]_{0}^{\infty}=0$（因为当 $x\to\infty$ 时 $xe^{-\lambda x}\to 0$，且 $x=0$ 时该项为 0），余下 $\int_{0}^{\infty}e^{-\lambda x}\,dx=\dfrac{1}{\lambda}$。

**（c）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 在下式第二行中以 $u = x^2$、$dv = \lambda e^{-\lambda x}\,dx$（从而 $du = 2x\,dx$、$v = -e^{-\lambda x}$）作分部积分，得
>
> ```math
> E[X^2] = \int_{-\infty}^{\infty} x^2 f_X(x)\,dx = \int_{0}^{\infty} x^2 \lambda e^{-\lambda x}\,dx = \Bigl[-x^2 e^{-\lambda x}\Bigr]_{0}^{\infty} + 2\int_{0}^{\infty} x e^{-\lambda x}\,dx = \frac{2}{\lambda}E[X] = \frac{2}{\lambda^2}.
> ```
>
> 其中边界项 $\Bigl[-x^2 e^{-\lambda x}\Bigr]_{0}^{\infty}=0$；且由 $\int_{0}^{\infty}x e^{-\lambda x}\,dx=\dfrac{1}{\lambda}E[X]$（因为 $E[X]=\int_{0}^{\infty}x\lambda e^{-\lambda x}\,dx$），故 $2\int_{0}^{\infty}x e^{-\lambda x}\,dx=\dfrac{2}{\lambda}E[X]$。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这两次 integration by parts（分部积分）其实在算同一个家族：对整数 $n\ge0$ 有 $\int_{0}^{\infty}x^{n}e^{-\lambda x}\,dx=\frac{n!}{\lambda^{n+1}}$。本题 $n=1$ 得 $\frac{1}{\lambda}$，$n=2$ 得 $\frac{2}{\lambda^{2}}$，于是 $\mathrm{var}(X)=\frac{2}{\lambda^{2}}-\left(\frac{1}{\lambda}\right)^{2}=\frac{1}{\lambda^{2}}$。把这个家族记住，以后就不必每次重做分部积分，直接查表即可；它正是 Gamma function（伽马函数）的定义 $\Gamma(n+1)=\int_{0}^{\infty}t^{n}e^{-t}\,dt=n!$ 在尺度变换 $t=\lambda x$ 下的形式。
>
> 把这条递推写出来更有意思：由一次分部积分得 $E[X^{n}]=\frac{n}{\lambda}E[X^{n-1}]$，因为边界项消失后剩下的积分正好是 $n\int_{0}^{\infty}x^{n-1}e^{-\lambda x}\,dx=\frac{n}{\lambda}E[X^{n-1}]$。从 $E[X^{0}]=1$ 出发连乘，立刻得到 $E[X^{n}]=\frac{n!}{\lambda^{n}}$，与查表结果一致。这条递推正是题解里 $E[X^{2}]=\frac{2}{\lambda}E[X]$ 的一般形式，看懂它就不必背公式：每一次分部积分只贡献一个因数 $\frac{n}{\lambda}$，而边界项每一次都归零。
>
> 边界项为什么必须是零。$\left[-x^{n}e^{-\lambda x}\right]_{0}^{\infty}$ 的上限要证 $x^{n}e^{-\lambda x}\to0$，这不是「显然」，因为一端趋于无穷、一端趋于零，是无穷乘零的未定形。给一条可以自己验的不等式链：由 Taylor series（Taylor 级数）的展开，$e^{\lambda x}\ge\frac{(\lambda x)^{n+1}}{(n+1)!}$ 对 $x\ge0$ 成立，右端只是正项级数中的一项，截断后仍然不超过全和；于是 $x^{n}e^{-\lambda x}\le\frac{(n+1)!}{\lambda^{n+1}}\cdot\frac{1}{\lambda x}\to0$。这条链只用到指数函数的级数定义，比反复用 L'Hôpital 法则干净，还顺带说明一件事：任何多项式增长都赢不过指数衰减，阶数再高也一样。
>
> 如果边界项不为零会怎样。把 $\lambda$ 换成负数，$e^{-\lambda x}$ 变成增长，积分发散，$E[X]=\infty$；取 $\lambda=0$，被积函数恒为 $1$，同样发散。所以定义里那句「$\lambda$ 为正数」不是装饰，它是让 $\int_{0}^{\infty}\lambda e^{-\lambda x}dx=1$ 与所有阶矩有限同时成立的前提。这也解释了为什么 parameter（参数）要写成 rate（速率）而不是 scale（尺度）：若改用 $\theta=\frac{1}{\lambda}$，密度变成 $\frac{1}{\theta}e^{-x/\theta}$，公式里到处多一个倒数，量纲也更容易搞混。
>
> dimensional analysis（量纲分析）在这里非常好用。$\lambda$ 的单位必须是「每时间」，否则 $\lambda x$ 无量纲这件事不成立，而指数只接受无量纲的量。于是 $E[X]=\frac{1}{\lambda}$ 的单位是时间，$\mathrm{var}(X)=\frac{1}{\lambda^{2}}$ 的单位是时间的平方，标准差 $\frac{1}{\lambda}$ 与均值同量纲。代具体数：$\lambda=0.5$ 每分钟，则均值 $2$ 分钟，方差 $4$ 分钟平方，标准差 $2$ 分钟，三阶原点矩 $\frac{6}{\lambda^{3}}=48$ 分钟立方。若有人把 $\lambda$ 当时间直接写 $E[X]=\lambda$，得到的 $0.5$ 分钟量纲上就站不住，这个检查比任何代数验算都快。物理与工程里习惯先查量纲再看数值，原因就在这里：单位错了，数量级常常差几个幂次，肉眼就能发现，不必等算到结尾。
>
> 历史坐标。Euler 在 1729 年 10 月 13 日写给 Goldbach 的信里给出了用无穷乘积与积分插值阶乘的方案，动机是把 $n!$ 延拓到非整数，这正是 $\Gamma$ 函数的起点；Legendre 在 1811 年的《Exercices de calcul intégral》里定下 $\Gamma$ 这个记号并沿用至今。这条历史线索解释了一个常见困惑：为什么 $\Gamma(n)=(n-1)!$ 而不是 $n!$，因为 Legendre 选的是让 $\Gamma(1)=1$ 的那个平移版本，与 Euler 的积分 $\int_{0}^{\infty}t^{n}e^{-t}dt=n!$ 差一个下标。今天这个函数是 Gamma distribution（伽马分布）、Beta 分布与 Dirichlet 分布归一化常数的骨架，也是贝叶斯里共轭先验的标准零件。
>
> 两个自检。第一，方差必须非负：$\frac{2}{\lambda^{2}}-\frac{1}{\lambda^{2}}=\frac{1}{\lambda^{2}}>0$，符合一般事实；若谁算出负方差，一定是把 $E[X^{2}]$ 与 $(E[X])^{2}$ 弄反了。第二，$\frac{E[X^{2}]}{(E[X])^{2}}=2$，说明 coefficient of variation（变异系数）恰为 $1$，即标准差等于均值，这是 exponential distribution（指数分布）的一个不变量；换成形状参数不等于 $1$ 的 Weibull distribution（Weibull 分布），这个比值就会偏离 $1$，所以它可以当作「数据是否像指数」的粗筛。
>
> 按六类的分法，这条属于历史与人物：从 1729 年那封信到 1811 年的记号，再到今天各个分布族里的用法。
>
> 结合前一小问的计算，我们得到
>
> ```math
> \mathrm{var}(X) = E[X^2] - \bigl(E[X]\bigr)^2 = \frac{2}{\lambda^2} - \left(\frac{1}{\lambda}\right)^{2} = \frac{1}{\lambda^2}.
> ```

<!-- ===== PDF p2 ===== -->

**（续）**

**（d）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 当集合中每个元素都以 $z$ 为上界（upper bounded by $z$）时，该集合的最大值（maximum）也就以 $z$ 为上界。于是对任意正数 $z$：
>
> ```math
> P(Z \le z) = P(\max\{X_1, X_2, X_3\} \le z) = P(X_1 \le z,\, X_2 \le z,\, X_3 \le z) = P(X_1 \le z)\,P(X_2 \le z)\,P(X_3 \le z) = \bigl(1 - e^{-\lambda z}\bigr)^3,
> ```
>
> 其中第三个等号利用了 $X_1$、$X_2$、$X_3$ 的独立性（independence）。于是
>
> ```math
> F_Z(z) = \begin{cases} 0, & z < 0, \\ \bigl(1 - e^{-\lambda z}\bigr)^3, & z \ge 0. \end{cases}
> ```
>
> 对 CDF 求导，即得所求的 PDF：
>
> ```math
> f_Z(z) = \begin{cases} 0, & z < 0, \\ 3\lambda e^{-\lambda z}\bigl(1 - e^{-\lambda z}\bigr)^2, & z \ge 0. \end{cases}
> ```

**（e）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 当集合中每个元素都以 $w$ 为下界（lower bounded by $w$）时，该集合的最小值（minimum）也就以 $w$ 为下界。于是对任意正数 $w$：
>
> ```math
> P(W \ge w) = P(\min\{X_1, X_2\} \ge w) = P(X_1 \ge w,\, X_2 \ge w) = P(X_1 \ge w)\,P(X_2 \ge w) = \bigl(e^{-\lambda w}\bigr)^2 = e^{-2\lambda w},
> ```
>
> 其中第三个等号利用了 $X_1$ 与 $X_2$ 的独立性。于是
>
> ```math
> F_W(w) = \begin{cases} 0, & w < 0, \\ 1 - e^{-2\lambda w}, & w \ge 0. \end{cases}
> ```
>
> 我们可以认出这就是参数为 $2\lambda$ 的指数随机变量的 CDF。其 PDF 为
>
> ```math
> f_W(w) = \begin{cases} 0, & w < 0, \\ 2\lambda e^{-2\lambda w}, & w \ge 0. \end{cases}
> ```

<span style="color:#1e8449;">**[mathtip]** 独立指数随机变量的最小值仍服从指数分布，其参数为各参数之和（此处即 $2\lambda$）；而最大值（(d) 中的 $Z$）不服从指数分布——其 CDF 为各 CDF 之积 $\bigl(1-e^{-\lambda z}\bigr)^3$，相应 PDF 为 $3\lambda e^{-\lambda z}\bigl(1-e^{-\lambda z}\bigr)^2$。</span>
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条 mathtip 可以展开成一条结构性结论：minimum（最小值）运算把指数族封闭起来，maximum（最大值）运算不封闭。根源在事件的方向。$\{W>w\}$ 写成交集 $\{X_1>w\}\cap\{X_2>w\}$，independence（独立性）把交集概率乘起来，$e^{-\lambda w}\cdot e^{-\lambda w}=e^{-2\lambda w}$，指数相加仍是指数，所以最小值还是 exponential distribution（指数分布）。而 $\{Z\le z\}$ 是「全部都不超过」，乘出来是 $\left(1-e^{-\lambda z}\right)^{3}$，一个三次幂，幂不再是指数形式，所以最大值落到另一个分布族。判断封闭性时先看事件写成交还是写成并，这一步比记结论可靠。
>
> 竞速读法。把两个指数变量想成两盏灯的寿命，最小值就是「先坏的那盏」。因为 memorylessness（无记忆性），在任一时刻 $w$，两盏灯剩余寿命的分布与出厂时相同，于是 hazard rate（危险率）可以相加：单个指数分布的危险率 $h(w)=\frac{f(w)}{1-F(w)}=\lambda$ 是常数，而 $n$ 个独立分量组成的 series system（串联系统）的危险率是各分量之和。这就是可靠性工程里「串联系统寿命仍是指数、速率相加」的根据，也是 competing risks（竞争风险）模型的基本事实：多个失效原因同时存在时，总失效时间由速率之和支配。
>
> 谁先发生，概率也可以算到底。$P(X_1<X_2)=\int_{0}^{\infty}\lambda_1e^{-\lambda_1x}e^{-\lambda_2x}\,dx=\frac{\lambda_1}{\lambda_1+\lambda_2}$，而且「谁先」与「何时」相互独立。代具体数：$\lambda_1=0.5$ 与 $\lambda_2=1.5$（每时间单位），则最小值服从速率 $2$ 的指数分布，均值 $0.5$，且 $P(\min>1)=e^{-2}\approx0.1353$；$X_1$ 先发生的概率为 $\frac{0.5}{2}=0.25$，与其速率占比完全相同。这个比例分配性质正是 Poisson process（泊松过程）的 thinning（稀疏化）在连续时间上的版本：把到达流按固定比例分成两支，每一支仍是泊松过程，速率按比例缩水。
>
> 无记忆性的唯一性也值得说清，因为它解释了「为什么偏偏是指数」。连续分布中只有指数分布满足 $P(X>s+t\mid X>s)=P(X>t)$。证明只有一句话：令 $g(t)=P(X>t)$，则 $g(s+t)=g(s)g(t)$，这是 Cauchy functional equation（Cauchy 函数方程），在有界或单调的条件下唯一解是 $g(t)=e^{-ct}$。这条论证把 6.042J discrete mathematics（离散数学）里的函数方程、Thomson 实分析里的连续性条件串成一条线，也说明凡是要「重置之后与原来同分布」的建模，指数是唯一选项；换成 Weibull distribution（Weibull 分布）就必然带有「越用越容易坏」或「越用越耐用」的倾向。
>
> 最大值那边后来发展成什么。既然最大值不服从指数分布，它服从什么？extreme value theory（极值理论）回答：对独立同分布样本的最大值做适当的中心化与尺度化，若极限非退化，只能是三种类型之一，这就是 Fisher–Tippett–Gnedenko theorem（Fisher–Tippett–Gnedenko 定理）。Fisher 与 Tippett 在 1928 年给出三种极限形式，Gnedenko 在 1943 年证明只有这三种，并给出各自的吸引域条件。三型对应三种尾部：Gumbel distribution（Gumbel 分布）对应指数尾，Fréchet distribution（Fréchet 分布）对应幂律尾，Weibull distribution（Weibull 分布）对应有界尾。本题的 $Z$ 只是有限个指数变量的最大值，还不是极限；但只要把样本量推到无穷并做归一化，它就会落进 Gumbel 型。
>
> 工程含义。这条 mathtip 的实用价值在选择模型：要建「最早失效时间」，用指数，或用形状参数小于 $1$ 的 Weibull 版本（它的危险率是幂函数，不是常数）；要建「最大载荷、最高水位、最大回撤」，用 generalized extreme value distribution（广义极值分布）或超阈值方法。反过来，若把最大值硬套指数分布，尾部会系统性低估：指数尾按 $e^{-\lambda z}$ 衰减，而真实极值尾常常是幂律，$z$ 一大就差出几个数量级。金融风控里 value at risk（在险价值）与 expected shortfall（预期短缺）之所以不默认用正态或指数，正是这个原因；它们关心的是尾部那几个分位点，而尾部的形状恰恰是简单模型最容易弄错的地方。
>
> 按六类的分法，这条属于拓展前沿：从一道习题里的 max 出发，接到极值理论的三型定理与风控里的尾部建模。

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 标准版权尾页：MIT OpenCourseWare, http://ocw.mit.edu, 6.041/6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010；课程内容至此结束。）</span>
