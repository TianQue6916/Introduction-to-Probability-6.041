<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 13 解答（Recitation 13: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 10 月 21 日）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 我们先写出 $E[Z \mid X, Y]$ 的定义：
>
> > ```math
> > E[Z \mid X = x, Y = y] = \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)
> > ```
>
> 由于 $E[Z \mid X, Y]$ 是随机变量 $X$ 与 $Y$ 的函数，并且在 $X = x$、$Y = y$ 发生时（该情况以概率 $p_{X,Y}(x, y)$ 发生）等于 $E[Z \mid X = x, Y = y]$，于是由 expected value rule（期望值法则，即：若 $W = g(X, Y)$ 是 $X, Y$ 的函数，则 $E[W] = \sum_x \sum_y g(x, y)\, p_{X,Y}(x, y)$），
>
> > ```math
> > \begin{aligned}
> > E\big[E[Z \mid X, Y]\big]
> > &= \sum_x \sum_y E[Z \mid X = x, Y = y]\, p_{X,Y}(x, y) \\
> > &= \sum_x \sum_y \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)\, p_{X,Y}(x, y) \\
> > &= \sum_x \sum_y \sum_z z\, p_{X,Y,Z}(x, y, z) \\
> > &= E[Z].
> > \end{aligned}
> > ```
>
> 〔上面第三行用到乘法法则（multiplication rule）$p_{Z\mid X,Y}(z\mid x,y)\,p_{X,Y}(x,y) = p_{X,Y,Z}(x,y,z)$；第四行用到边际化（marginalization）$\sum_x\sum_y p_{X,Y,Z}(x,y,z) = p_Z(z)$，故 $\sum_z z\, p_Z(z) = E[Z]$。〕
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：第一性原理洞察。** 先说这条注要拆的东西：为什么 $E[Z\mid X,Y]$ 必须被定义成一条 random variable（随机变量），而不能只是一个数。关键在于"信息本身是随机的"这句话。当 $x,y$ 还没有被观测到，你能拿出来的只有一个随 $(x,y)$ 浮动的猜测；只有 $X=x$、$Y=y$ 真的发生之后，这个猜测才凝固成一个具体的数。conditional expectation（条件期望）同时具备"数"与"函数"两种身份，不是因为数学家偏爱双重身份，而是因为观测这件事本身由 $(X,Y)$ 的抽样结果决定：抽到哪一对，你就站在哪一条分支上。一旦把它写死成常数，第三行的求和号就失去了被加的下标，整条等式链立刻断掉。
>
> 再看这四行各自的职责，缺一行就少一个维度。第一行是 expected value rule（期望值法则）：它把"对 $X$ 与 $Y$ 的函数取期望"翻译成"按联合概率 $p_{X,Y}$ 加权求和"，而这一步的合法性恰恰以"$E[Z\mid X,Y]$ 是一条 random variable（随机变量）"为前提；前提不成立，法则无处施加。第二行把定义代进去，把内层的数写成和式，于是出现三重求和，此时被求和的对象才真正落到 $Z$ 的取值上。第三行用 multiplication rule（乘法法则）把条件概率与边缘概率拼成联合概率 $p_{X,Y,Z}$；漏掉这一步，和式里会残留 $p_{X,Y}$，算出来的根本不是 $Z$ 的期望，而是一个与 $Z$ 的取值无关的常数。第四行用 marginalization（边际化）消去 $x,y$ 两个下标，剩下的才恰好是 $E[Z]$。换句话说：第三行负责升维，把两条边缘分布拼成一条联合分布；第四行负责降维，把三个下标压成一个。一升一降必须配套，否则连量纲都对不上。
>
> 用具体数字走一遍最不容易骗自己。取 $X,Y$ 独立、各以 $1/2$ 取 $0$ 或 $1$，令 $Z=XY$，四个格子的概率都是 $1/4$。四个条件值分别是 $0,0,0,1$，按 $1/4$ 加权得 $1/4$；而 $E[Z]$ 就是 $P(X=1,Y=1)=1/4$，两边相等，说明本条结论在这个能摁计算器的例子里确实成立。更有意思的是"少剥一层"会怎样：$E[Z\mid X=0]=0$，$E[Z\mid X=1]=E[Y]=1/2$，于是 $E\big[E[Z\mid X]\big]=1/4$ 同样对。两个量最终都收敛到 $1/4$，但它们在过程中并不相同：在 $X=1$ 上，一个恒为 $1/2$，另一个随 $Y$ 摇摆。这说明"先对细信息取条件、再对粗信息取条件"与反过来的顺序，中间产物完全不同，只是末端同值而已。
>
> 这个"中间不同、末端同值"的结构，正是 law of iterated expectations（期望迭代法则）能被反复套用的原因，也是 (b) 问存在的理由：如果中间产物都一样，就没有必要再证一次条件化版本。顺带一提，(c) 把 (b) 的结果两边再取一次期望，看上去像是同样的动作重复了一遍，其实第二次取的是对 $X$ 的无条件期望，把还残留的 $X$ 也一并平均掉；这一步之后式子里不再有自由下标，才真正落回一个数。分清"对谁取期望"，是这道题唯一容易含糊的地方。最后一句警告：上面每一步求和都默认绝对收敛。若 $E[|Z|]$ 有限性不成立，重排求和次序可以把有限的部分抵消成任意值，结论随之失效。做题时一般不必逐一验证，但一旦碰上重尾分布，这条前提就是全部推理的地基。
>
> **(b)** 我们从 $E[Z \mid X, Y]$ 的定义出发——它是随机变量 $X$ 与 $Y$ 的函数，并且在 $X = x$、$Y = y$ 时等于 $E[Z \mid X = x, Y = y]$，因此
>
> > ```math
> > E[Z \mid X = x, Y = y] = \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)
> > ```
>
> 仿照上面的步骤推进，但改为在事件 $X = x$ 上取条件，得
>
> > ```math
> > \begin{aligned}
> > E\big[E[Z \mid X, Y = y] \,\big|\, X = x\big]
> > &= \sum_y E[Z \mid X = x, Y = y]\, p_{Y\mid X}(y \mid x) \\
> > &= \sum_y \sum_z z\, p_{Z\mid X,Y}(z \mid x, y)\, p_{Y\mid X}(y \mid x) \\
> > &= \sum_y \sum_z z\, p_{Y,Z\mid X}(y, z \mid x) \\
> > &= E[Z \mid X = x].
> > \end{aligned}
> > ```
>
> 〔第三行用到条件形式的乘法法则 $p_{Z\mid X,Y}(z\mid x,y)\,p_{Y\mid X}(y\mid x) = p_{Y,Z\mid X}(y,z\mid x)$；第四行用到边际化 $\sum_y p_{Y,Z\mid X}(y,z\mid x) = p_{Z\mid X}(z\mid x)$。〕
>
> 由于上式对 $x$ 的一切可能取值都成立，故有 $E\big[E[Z \mid Y, X] \mid X\big] = E[Z \mid X]$。（$E[Z \mid Y, X]$ 与 $E[Z \mid X, Y]$ 是同一个随机变量，只是书写次序不同。）
>
> **(c)** 对 (b) 中公式的两边取期望，得
>
> > ```math
> > E\big[E[Z \mid X]\big] = E\big[E\big[E[Z \mid X, Y] \,\big|\, X\big]\big].
> > ```
>
> 由 law of iterated expectations（期望迭代法则，又称 tower property（塔性质），即 $E[Z] = E\big[E[Z \mid X]\big]$），上式左边即为 $E[Z]$，从而证得所要的结果。
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：跨课程连接（18.06 线性代数 → 条件期望的投影结构）。** 你在 Strang 18.06 里学过 least squares（最小二乘）：把向量往一个 subspace（子空间）上投，残差与那个 subspace（子空间）正交，投影算子满足 $P^2=P$。conditional expectation（条件期望）的骨架与此一模一样，只换掉一个 inner product（内积）：在平方可积的 random variable（随机变量）构成的向量空间里定义 $\langle U,V\rangle=E[UV]$，那么 $E[Z\mid X]$ 就是把 $Z$ 往"所有 $X$ 的函数"这个 subspace（子空间）上做的 orthogonal projection（正交投影）。残差 $Z-E[Z\mid X]$ 与每一个 $X$ 的函数都正交，写成式子就是 $\langle Z-E[Z\mid X],\,h(X)\rangle=0$ 对一切 $h$ 成立。
>
> 把这个正交条件取 $h\equiv 1$，立刻得到 $E[Z]-E\big[E[Z\mid X]\big]=0$，也就是 $E[Z]=E\big[E[Z\mid X]\big]$。所谓"塔"在几何上只是"残差与常数正交"这一句话，很多教材把它当成一条需要单独背的公式，其实它压根不是新定理，而是投影定义的直接推论：只要承认残差与整个 subspace（子空间）正交，就自动与其中那条最特殊的向量 $1$ 正交。这也顺带解释了为什么取条件不改变均值、只改变"看法"——平均这件事由常数方向决定，而残差在那个方向上没有分量。
>
> 本条第三个式子则是投影算子的 idempotent（幂等）性质。记 $P_X$ 为投到"$X$ 的函数"全体的算子，$P_{X,Y}$ 为投到"$X$ 与 $Y$ 的联合函数"全体的算子。由于"$X$ 的函数"整体被包含在"$X$ 与 $Y$ 的函数"里，先投到大空间再投到小空间，与直接投到小空间完全等价，即 $P_XP_{X,Y}=P_X$。把它作用在 $Z$ 上，就是本条要证的 $E\big[E[Z\mid X,Y]\mid X\big]=E[Z\mid X]$。而 $P_XP_X=P_X$ 对应 $E\big[E[Z\mid X]\mid X\big]=E[Z\mid X]$：对已经掌握的信息再取一次条件，猜不出任何新东西，所以这个算子是 idempotent（幂等）的。次序也值得记一笔：两个 subspace（子空间）有包含关系时方可交换，否则 $P_XP_{X,Y}$ 与 $P_{X,Y}P_X$ 会给出不同的东西。
>
> 用 $Z=XY$、$X,Y$ 独立且各以 $1/2$ 取 $0$ 或 $1$ 验一遍。候选投影是 $E[Z\mid X]=X/2$，检验两个正交条件：$\langle Z-X/2,\,1\rangle=1/4-1/4=0$，$\langle Z-X/2,\,X\rangle=E[XZ]-E[X^2]/2$。这里 $E[XZ]=E[X^2Y]=E[X^2]E[Y]=(1/2)(1/2)=1/4$，而 $E[X^2]/2=1/4$，两项相等，故第二个内积也是 $0$。两个条件都满足，说明 $X/2$ 确实落在投影位置，而不是随便画的一条直线。方差也跟着分开：$Z$ 的方差是 $1/4-1/16=3/16$，投影的方差是 $1/16$，残差平方的期望 $E\big[(Z-X/2)^2\big]=(0+0+0.0625+0.0625)/4=1/8$；$1/16+1/8=3/16$，勾股定理在方差上照样成立。这条"总方差等于投影方差加残差方差"的等式，就是 Problem 2 (b) 里那个分解的几何版本。
>
> 但类比的边界必须说清，否则它会带你走歪。18.06 里的投影算子由给定的 inner product（内积）与固定的 subspace（子空间）唯一确定，换一组基并不改变算子本身；而这里的 inner product（内积）由概率分布定义，分布换了，内积就换了，投影随之改变，同一组变量在不同分布下投影到完全不同的地方。更实质的差别在维度：线性代数的 subspace（子空间）通常有限维，可以写出 $A(A^\top A)^{-1}A^\top$ 这种显式矩阵；而"$X$ 的所有函数"是无穷维的，没有这样的矩阵，$E[Z\mid X]$ 只能靠条件分布或正交性来刻画。还有一层容易被忽略的差别：18.06 的投影算子对右端是线性的，把 $aU+bV$ 送进去就出来 $aPU+bPV$；此处对 $Z$ 的线性同样成立，但对"取条件的对象"并不线性——把 $X$ 换成 $f(X)$，投影空间就整个换了，算子也跟着换。这种"半边线性、半边随信息变化"的性质，正是 conditional expectation（条件期望）看起来像线性算子、却不完全像的根本原因。最后，正交性只在二阶矩存在时成立，一旦二阶矩不存在，投影就不存在，勾股分解也无从谈起。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $Y$ 为第一次折断后所得一段的长度，$X$ 为第二次折断后所得一段的长度。
>
> 〔模型补充：这里考虑的是一根长度为 $\ell$ 的木棍。先在 $[0, \ell]$ 上均匀随机取一点折断，取其中一段，其长度记为 $Y$，故 $Y$ 在 $[0, \ell]$ 上均匀分布；再对这段长为 $Y$ 的木棍在 $[0, Y]$ 上均匀随机取一点折断，取其中一段，其长度记为 $X$，故给定 $Y$ 时 $X$ 在 $[0, Y]$ 上均匀分布。下文 $E[X \mid Y] = Y/2$、$E[Y] = \ell/2$ 均由此模型而来。〕

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> **(a)** law of iterated expectations（期望迭代法则）指出：
>
> > ```math
> > E[X] = E\big[E[X \mid Y]\big]
> > ```
>
> 我们有 $E[X \mid Y] = Y/2$（因为给定 $Y$，$X$ 在 $[0, Y]$ 上均匀分布，均值为 $Y/2$），以及 $E[Y] = \ell/2$（因为 $Y$ 在 $[0, \ell]$ 上均匀分布，均值为 $\ell/2$）。于是：
>
> > ```math
> > E[X] = E\big[E[X \mid Y]\big] = E[Y/2] = \frac{1}{2}\, E[Y] = \frac{1}{2}\cdot\frac{\ell}{2} = \frac{\ell}{4}.
> > ```
>
> **(b)** 我们用 law of total variance（全方差定律：$\mathrm{var}(X) = E\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(E[X \mid Y]\big)$）来求 $\mathrm{var}(X)$：
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：证明策略模板。** 这条式子看起来只是把方差拆成两项，其实它是一套可以照抄的动作序列，招法名字叫"二阶矩拆解"：凡是遇到"求某个 random variable（随机变量）的方差，而这个 random variable（随机变量）背后挂着一个可观测的中间量"，就按下面四步走，不要一上来直接对方差本身动手。直接动方差之所以行不通，是因为方差不是线性运算，你对它取不了条件，只能先把它拆成"一阶矩"与"二阶矩"这两块可以被条件化的东西。
>
> 第一步，把方差还原成矩：$\mathrm{var}(Z)=E[Z^2]-\big(E[Z]\big)^2$。这一步的目的是把非线性的方差换成可以对 $Y$ 取条件的线性量，代价是后面要多处理一项 $(E[Z])^2$。第二步，对二阶矩用 tower property（塔性质），写成 $\mathrm{var}(Z)=E\big[E[Z^2\mid Y]\big]-\big(E[Z]\big)^2$；能把条件塞进内层，正是因为 $E[\cdot]$ 是线性的。第三步，在条件内部补项，把二阶矩拆成 conditional variance（条件方差）加条件均值的平方，即 $E[Z^2\mid Y]=\mathrm{var}(Z\mid Y)+\big(E[Z\mid Y]\big)^2$；这个恒等式不过是把第一步的配方在给定 $Y$ 的世界上重讲一遍。第四步，两式相减凑出 $\mathrm{var}\big(E[Z\mid Y]\big)$：注意 $\mathrm{var}\big(E[Z\mid Y]\big)=E\big[\big(E[Z\mid Y]\big)^2\big]-\big(E[E[Z\mid Y]]\big)^2$，而后一项由塔性质等于 $\big(E[Z]\big)^2$，正好与前面欠下的那一项抵消。四步走完，law of total variance（全方差定律）就是一个恒等式，全程没有用到任何不等式，也没有用到任何独立性假设——这一点最值得记住：它只要求二阶矩存在。
>
> 这套模板最常出错的地方只有一个：把 $E[Z\mid Y]$ 当成常数。它是 $Y$ 的函数，本身是一条 random variable（随机变量），所以它还能再取方差；若当成常数，第二项会被算成 $0$，答案就只剩"组内"那一半，而且算出来的数往往还挺像样，不容易发现。第二处细节是次序与语义：$E\big[\mathrm{var}(Z\mid Y)\big]$ 是组内方差的加权平均，$\mathrm{var}\big(E[Z\mid Y]\big)$ 是各组均值的离散程度，两项量纲都是 $Z$ 的平方单位，写反不会报错，只会得到一个看起来合理的错值。第三处是条件：$\mathrm{var}(Z\mid Y)$ 里的 $Z$ 必须是同一个对象，若中途把 $\sum_{i=1}^{N}X_i$ 与 $X_i$ 混着用，第三步的配方就会失效。
>
> 代进这道题的数验一遍，取 $\ell=1$。$\mathrm{var}(X\mid Y)=Y^2/12$，$Y$ 在 $[0,1]$ 上均匀，故 $E\big[\mathrm{var}(X\mid Y)\big]=E[Y^2]/12=(1/3)/12=1/36\approx0.02778$。$E[X\mid Y]=Y/2$，其方差是 $\mathrm{var}(Y)/4=(1/12)/4=1/48\approx0.02083$。相加得 $7/144\approx0.04861$。若取 $\ell=144$，两项分别是 $576$ 与 $432$，合计 $1008$，与 $7\cdot144^2/144$ 完全一致。这两个数字还可以读出信息：组内项 $576$ 比组间项 $432$ 大，说明方差的主要来源是"每一小段内部还均匀地摊着一层"，而不是"不同 $Y$ 给出的均值差异"。
>
> 最后说说这套模板的边界，这也是它可被信任的原因。整个推导只依赖两件事：二阶矩有限，以及条件期望作为 $Y$ 的函数确实存在；独立性、连续性、有界性一概不需要。反过来说，只要 $\mathrm{var}(Z)$ 发散，第一步的 $E[Z^2]$ 就是无穷，第四步的相减变成无穷减无穷，形式上的抵消毫无意义，此时 law of total variance（全方差定律）只能当作扩展等式来读，不能拿来算数。若题目给的是重尾分布又问方差，稳妥的路子是先对 $Z$ 截断成 $\min(Z,M)$ 算一遍，再让 $M$ 增大观察走向，而不是硬套公式。
>
> 复用面很宽：Problem 3 的随机和、分层抽样、实验设计里的组间组内分解、乃至机器学习的偏差方差分解，走的都是同一组动作。记住这个条件反射就够了：方差与条件同时出现，先写二阶矩。
>
> > ```math
> > \mathrm{var}(X) = E\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(E[X \mid Y]\big).
> > ```
>
> 回顾：在区间 $[a, b]$ 上均匀分布（uniform）的随机变量，其方差为 $(b-a)^2/12$。由于 $Y$ 在 $[0, \ell]$ 上均匀分布，我们有
>
> > ```math
> > \mathrm{var}(Y) = \frac{\ell^2}{12}, \qquad \mathrm{var}(X \mid Y) = \frac{Y^2}{12}.
> > ```
>
> 已知 $E[X \mid Y] = Y/2$，于是
>
> > ```math
> > \mathrm{var}\big(E[X \mid Y]\big) = \mathrm{var}(Y/2) = \frac{1}{4}\,\mathrm{var}(Y) = \frac{\ell^2}{48}.
> > ```
>
> 另外，
>
> > ```math
> > \begin{aligned}
> > E\big[\mathrm{var}(X \mid Y)\big]
> > &= E\!\left[\frac{Y^2}{12}\right] \\
> > &= \int_0^{\ell} \frac{y^2}{12}\, f_Y(y)\, dy \\
> > &= \frac{1}{12} \cdot \frac{1}{\ell} \int_0^{\ell} y^2\, dy \\
> > &= \frac{\ell^2}{36}.
> > \end{aligned}
> > ```
>
> 〔上式中 $f_Y(y) = 1/\ell$（$0 \le y \le \ell$）是 $Y$ 在 $[0, \ell]$ 上均匀分布的密度。〕
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：图解注。** 这道题没有配图，但它的抽样机制可以画成一张平面图，把这张图读对，后面两个积分就不必死记。画法是：横轴放第一次折断的位置 $y$，纵轴放第二次折断后取出的那一段长度 $x$，两者都从 $0$ 量到 $\ell$。可行域不是整个正方形，而是三角形 $0\le x\le y\le \ell$，理由很朴素：第二刀只能落在第一段内部，长度 $x$ 永远不可能超过 $y$。图上那条斜边 $x=y$ 是全图最关键的位置，它代表"第二刀正好落在段的端点"，此时两段等长，属于零面积的退化情形，不承载概率；任何把质量算到斜边右侧的做法，都等于承认第二段比第一段还长，模型当场就错了。
>
> 然后再读密度。固定一条竖线（即固定 $y$），竖条内部 $x$ 的 density（密度）是常数 $1/y$，因为给定 $Y=y$ 时 $X$ 在 $[0,y]$ 上服从 uniform distribution（均匀分布）；而 $Y$ 自身的 density（密度）在 $[0,\ell]$ 上是 $1/\ell$。两者相乘，得联合 density（密度）$f(x,y)=1/(\ell y)$，它只随 $y$ 变、不随 $x$ 变。于是等密度线是一族水平线：越靠左（$y$ 越接近 $0$）越密，越靠右越稀。这个"左密右疏"是全图最该记住的特征，它决定了概率质量堆在左下角那片面积很小的区域。顶点附近密度虽然发散（正比于 $1/y$），但面积元按 $\mathrm{d}y\,\mathrm{d}x$ 收缩，$1/y$ 乘上竖条长度 $y$ 恰好得 $1$，所以总质量仍是 $1$——这张图是"尖而不胖"的，这个读法比任何一次换元都稳。
>
> 把归一化在图上一步步算出来：每条竖条宽 $y$、高 $1/(\ell y)$，面积是 $1/\ell$；把 $y$ 从 $0$ 积到 $\ell$，得 $1$。这条"竖条宽乘高"的读法顺带说明：不能用面积占比代替概率占比。可行域只占正方形面积的一半，却要承载全部质量，而且质量在其中的分布极不均匀，所以看图时该盯的是竖条的高度，不是三角形的胖瘦。
>
> 最后看 law of total variance（全方差定律）在图上落在哪个位置。$E\big[\mathrm{var}(X\mid Y)\big]=E[Y^2/12]$ 是"每条竖条内部的离散度，再按竖条的概率加权"，权重天然偏向 $y$ 大的一侧，因为那里的竖条更长、承载的质量更多；$\mathrm{var}\big(E[X\mid Y]\big)$ 只用到竖条中心 $y/2$ 的位置，与竖条内部怎么摊开无关。取 $\ell=144$ 把这些数落到图上：总方差 $1008$，其中 $576$ 来自竖条内部（$144^2/36$），$432$ 来自竖条之间（$144^2/48$），前者更大，说明"内部还摊着一层"才是方差的主要来源。
>
> 图上还能读出为什么不能偷懒把 $X$ 当成均匀分布。沿水平条把 $y$ 积掉，得到 $X$ 的分布 $\int_x^{\ell}\frac{1}{\ell y}\,\mathrm{d}y=\frac{1}{\ell}\ln\frac{\ell}{x}$，它在 $x\to 0$ 处发散，对应图上左下角那团堆积。也就是说 $X$ 在小值附近远比大值附近密，若照均匀来算会得 $E[X]=\ell/2$，比正确的 $\ell/4$ 整整大一倍。图的作用就在这里：它把"哪里密"摊在你眼前，省掉一次试错。
>
> 这张图还能纠正一个直觉。只断一刀时，长度在 $[0,\ell]$ 上均匀，方差是 $\ell^2/12$，取 $\ell=144$ 得 $1728$；断两刀反而只有 $1008$，比一刀还小。图上的原因很清楚：第二段的长度被 $Y$ 卡住，上界随 $y$ 缩小，而质量又堆在小 $y$ 一侧，整体尺度被压低，所以多随机了一次，结果反而更集中。把这个数记在图上：$1728$ 是"一刀"的刻度，$1008$ 是"两刀"的刻度，两者相差近 $42\%$，不是笔误。
>
> 综合以上结果，得
>
> > ```math
> > \mathrm{var}(X) = E\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(E[X \mid Y]\big) = \frac{\ell^2}{36} + \frac{\ell^2}{48} = \frac{7\ell^2}{144}.
> > ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $X_i$ 表示第 $i$ 个箱子中 widgets（小部件）的数目，则 $T = \sum_{i=1}^{N} X_i$。
>
> 〔模型补充：这里 $N$ 是箱子的总数（一个随机变量），每个箱子里小部件的数目 $X_i$ 是独立同分布（i.i.d.，independently and identically distributed）的随机变量，且都独立于 $N$。记共同分布为 $E[X_i] = E[X]$、$\mathrm{var}(X_i) = \mathrm{var}(X)$。题目给定 $E[X] = 10$、$\mathrm{var}(X) = 16$、$E[N] = 10$、$\mathrm{var}(N) = 16$（这四个数值可由最终结果 $E[T] = 100$、$\mathrm{var}(T) = 1760$ 唯一反推得出）。〕
>
> > ```math
> > \begin{aligned}
> > E[T] &= E\!\left[E\!\left[\sum_{i=1}^{N} X_i \,\middle|\, N\right]\right] \\
> > &= E\!\left[\sum_{i=1}^{N} E[X_i \mid N]\right] \\
> > &= E\!\left[\sum_{i=1}^{N} E[X]\right] \\
> > &= E[X] \cdot E[N] = 100.
> > \end{aligned}
> > ```
>
> 〔第二、三行用到 $X_i$ 与 $N$ 独立，故 $E[X_i \mid N] = E[X_i] = E[X]$；第四行 $E\big[\sum_{i=1}^{N} E[X]\big] = E[X]\, E[N]$，因为 $E[X]$ 是常数。〕

<!-- ===== PDF p3 ===== -->

> **（续）** 以及，
>
> > ```math
> > \begin{aligned}
> > \mathrm{var}(T) &= E\big[\mathrm{var}(T \mid N)\big] + \mathrm{var}\big(E[T \mid N]\big) \\
> > &= E\!\left[\mathrm{var}\!\left(\sum_{i=1}^{N} X_i \,\middle|\, N\right)\right] + \mathrm{var}\!\left(E\!\left[\sum_{i=1}^{N} X_i \,\middle|\, N\right]\right) \\
> > &= E\big[N\, \mathrm{var}(X)\big] + \mathrm{var}\big(N\, E[X]\big) \\
> > &= \big(\mathrm{var}(X)\big)\, E[N] + \big(E[X]\big)^2\, \mathrm{var}(N) \\
> > &= 16 \cdot 10 + 100 \cdot 16 = 1760.
> > \end{aligned}
> > ```
>
> 〔第三行用到 $X_i$ 独立同分布且独立于 $N$：$\mathrm{var}\big(\sum_{i=1}^{N} X_i \mid N\big) = N\,\mathrm{var}(X)$，$E\big[\sum_{i=1}^{N} X_i \mid N\big] = N\,E[X]$；第四行用到 $E[N\,\mathrm{var}(X)] = \mathrm{var}(X)\,E[N]$（$\mathrm{var}(X)$ 是常数）以及 $\mathrm{var}(N\,E[X]) = (E[X])^2\,\mathrm{var}(N)$（$\mathrm{var}(aN) = a^2\,\mathrm{var}(N)$）。〕
> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> **类别：历史与人物。** 这一行算的是 random sum（随机和）的方差，而这类式子背后站着 Abraham Wald（1902–1950）。1944 年他在 The Annals of Mathematical Statistics 第 15 卷第 3 期发表 On Cumulative Sums of Random Variables（第 283–296 页），给出的正是 $\sum_{i=1}^{N}X_i$ 这种"项数本身随机"的和的期望等式，后来被称作 Wald's equation（Wald 方程）。这个时间点不是巧合：1943 年他在哥伦比亚大学的 Statistical Research Group 主持工作，为军方做检验，sequential analysis（序贯分析）要求"试验做多少次"由数据决定而不是事先钉死，样本量 $N$ 于是从常数变成一条 random variable（随机变量），"和式里有随机个数的项"从数学游戏变成了必须交付的工程问题。
>
> 代价与限制值得说清，因为很多人把它当成无条件成立的恒等式。Wald's equation（Wald 方程）要求 $E[N]$ 有限、每一项的期望也有限；更关键的是 $N$ 必须由已经发生的观测决定，不能偷看还没抽到的项——允许偷看就可能构造出等式失败的例子。这道题给的条件比 Wald 的原版更强：$N$ 与所有 $X_i$ 满足 independence（独立性），于是 $E[X_i\mid N]=E[X]$ 直接成立，推导短得几乎不用动脑。按原版走则只需"$N$ 是相对于 $\{X_i\}$ 的 stopping time（停时）"这个更弱的假设，独立性只是它的特例。教材在这里只给独立版本，是为了避开一套大二还用不上的语言。
>
> 还有一个流传很广的插曲，能说明这个人的思维方式。二战期间军方想知道轰炸机该在哪里加装甲，统计返航飞机的中弹分布，得到的图是机翼弹孔最多、发动机几乎没有。Wald 指出样本只会是飞回来的飞机，发动机中弹的那些根本没有机会被统计，于是该加固的恰恰是没有弹孔的部位，这就是 survivorship bias（幸存者偏差）最著名的出处。它和本条式子的共同点在于：他关心的永远不是"看见的那部分有多大"，而是"看不见的那部分有多重"。$\mathrm{var}(T)$ 拆成组内与组间两项，本质也是把"看得见的均值差"和"看不见的组内波动"分别称重。
>
> 后续发展也值得一提。1947 年他把战时报告整理成 Sequential Analysis 一书，由 Wiley 出版，正文 212 页，把 sequential analysis（序贯分析）从保密报告变成一门可教学的学科；1948 年他与 Wolfowitz 一起给出了序贯概率比检验的最优性证明。random sum（随机和）的等式随后进入更新理论与复合泊松过程，成为排队、风险模型与分支过程的入口；今天你在算法分析里看到的"随机规模递归树"，走的也是同一个骨架。
>
> 最后回到数值上体会一下"不做会怎样"。这道题里若错把 $N$ 当成固定常数 $10$，方差会被算成 $10\cdot 16=160$，而正确值是 $16\cdot 10+100\cdot 16=1760$，差了整整 $11$ 倍。差的这一大截正是组间项 $100\cdot 16$：箱子数本身在波动，而每个箱子都按比例放大这份波动。忽略它，就等于假设箱子数永远等于期望值，这不是近似，是换了一道题。把比值写出来更清楚：$1760/160=11$，恰好等于 $1+\frac{(E[X])^2\mathrm{var}(N)}{\mathrm{var}(X)E[N]}=1+\frac{100\cdot 16}{16\cdot 10}$。也就是说，箱子数的相对波动与每箱件数的相对波动之比，直接决定你错得有多离谱。

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">【尾页】本页为 MIT OpenCourseWare（麻省理工学院开放式课程）封底版权页：注明课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）、Fall 2010 学期，以及引用条款网址 http://ocw.mit.edu/terms，无实质教学内容，不译。</span>
