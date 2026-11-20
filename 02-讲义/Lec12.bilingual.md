# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 12 — Conditional expectation; variance; sum of a random number of independent r.v.s（条件期望；方差；随机个独立随机变量之和）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline（本讲大纲）</span>

**阅读（Readings）**：教材 Section 4.3；Section 4.5 的部分内容（只要均值与方差；不讲变换）。

**本讲大纲（Lecture outline）**：
- 条件期望（Conditional expectation）：
  - 迭代期望律（law of iterated expectations）。
  - 全方差律（law of total variance）。
- 随机个独立随机变量之和（sum of a random number of independent r.v.'s）：
  - 均值、方差。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.222–228；§4.5, p.240–243</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这条注要回答的是一个很具体的设计问题：当求和的项数本身也是随机变量时，Lec 07 那套期望与方差规则为什么当场失灵，以及本讲拿什么把它补回来。固定项数的和之所以顺手，是因为它对应样本空间里一张有限表格上的有限次加法，你可以把每一项的下标逐一写出再相加，加法的个数是一个与抽样结果无关的常数；一旦项数 $N$ 也随机，样本空间里不同的结果对应的加数个数各不相同，任何统一的求和上下限都不存在，于是公式失效不是因为技巧不够，而是因为你要算的东西已经不再是原来那个对象。
>
> 补法只有一条主干：先条件化，再平均。给定 $N = n$，和退化成 $n$ 项固定求和，Lec 07 的期望线性与「独立才可加」的方差规则全部复活，这一步把「无穷多种可能的项数」压成「一个具体的 $n$」；随后把 $n$ 换回随机的 $N$，得到的是关于 $N$ 的函数，也就是一个随机变量；最后用一次 iterated expectations（迭代期望律）按 $p_N(n)$ 加权还原成无条件期望。为什么必须走这三步而没法一步到位：条件化那一步把 $n$ 以外的全部信息压缩成了「条件均值」一个数，信息已经不可逆地丢了；若不补上最后那次加权还原，你算出来的只是某一个 $n$ 之下的局部平均，量纲一样、含义完全不同。
>
> 给一组能直接代入的数字。设每周逛的商店家数 $N$ 满足 $\mathrm{E}[N] = 3$、$\mathrm{var}(N) = 2$，每家花的钱 $X$ 满足 $\mathrm{E}[X] = 20$ 元、$\mathrm{var}(X) = 25$，并设 $N$ 与各 $X_i$ 独立。两件工具立刻给出 $\mathrm{E}[Y] = 3 \times 20 = 60$ 元，以及 $\mathrm{var}(Y) = 3 \times 25 + 20^2 \times 2 = 75 + 800 = 875$，标准差约 29.6 元。重点看后一个数：项数随机这一项贡献了 800，占 875 的九成以上。如果有人照搬固定项数的公式写成 $3 \times 25 = 75$，标准差会被低估成 8.66，与真值 29.6 差了三倍多——随机项数不是小修正，它完全可能是一个系统里波动的主导来源，这正是本讲独立成章的理由。
>
> 跨课程连接要精确到路径与区别。CSAPP 第 6 章讲 cache（高速缓存）层次时算平均访问时间，做法是先把「命中」与「未命中」两个世界分开算耗时，再按命中率把它们加权合回一个数，这跟迭代期望律是同一个动作；区别在于 cache（高速缓存）的层数由硬件固定、权重是实测命中率，不存在「随机层数」这个额外随机源，所以它只需一层加权，而随机和需要两层：先对项数条件化，再对 $N$ 的分布平均。CLRS 的分治给出另一半类比：divide（分解）相当于条件化，把大问题切成规模已知的子问题；merge（合并）相当于把子解合回原问题；区别是 merge（合并）是确定性函数，合并出来是精确值，而这里合并用的是加权平均，条件化那一刻信息就丢了。6.042J 的 total probability theorem（全概率定理）是最干净的先验版本，把条件概率换成条件均值就得到本讲的均值版。
>
> 所以本讲不是在教两个孤立公式，而是把「分层、加权、还原」这条策略在均值与二阶矩上各落一刀，两个公式是同一把刀的两个刃口；读这一节的关键动作，是把每个条件化步骤都问一句「我丢了什么信息，后面靠什么补回来」。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditional expectations（条件期望）</span>

- 给定随机变量 $Y$ 的取值 $y$：
```math
\mathrm{E}[X \mid Y = y] = \sum_x x\, p_{X|Y}(x \mid y) \qquad \text{（连续情形换成积分）}.
```
  其中 $p_{X|Y}(x \mid y)$ 是 conditional PMF（条件概率质量函数），即在已知 $Y = y$ 的条件下 $X$ 取各可能值 $x$ 的概率分布：$p_{X|Y}(x \mid y) = \mathrm{P}(X = x \mid Y = y)$。
- **Stick example（断棍例）**：长为 $\ell$ 的棍子，先在均匀随机选取的点 $Y$ 处折断（$Y$ 为折断点到棍子一端的距离，$Y \sim U[0,\ell]$，这里 $U[a,b]$ 表示区间 $[a,b]$ 上的 uniform distribution（均匀分布））；再在剩下的长为 $Y$ 的那一截上均匀随机选点 $X$ 折断（$X$ 为该截一端到折断点的距离，故给定 $Y = y$ 时 $X \sim U[0,y]$）。
- $\mathrm{E}[X \mid Y = y] = \dfrac{y}{2}$ ——一个 number（数）。
- $\mathrm{E}[X \mid Y] = \dfrac{Y}{2}$ ——一个 random variable（随机变量）。
- **迭代期望律（law of iterated expectations）**：
```math
\mathrm{E}\big[\mathrm{E}[X \mid Y]\big] = \sum_y \mathrm{E}[X \mid Y = y]\, p_Y(y) = \mathrm{E}[X].
```
- 断棍例中：$\mathrm{E}[X] = \mathrm{E}\big[\mathrm{E}[X \mid Y]\big] = \mathrm{E}[Y/2] = \ell/4$。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.222–224</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 本注要拆的是一个极容易被滑过去的动作：把 $\mathrm{E}[X \mid Y = y]$ 里的 $y$ 换成 $Y$。这不是记号游戏，它改变的是对象的类型——前者是一个数，后者是一个随机变量。初学时的困惑几乎全部来自这一步没有想透，后面的迭代期望律和全方差律就都变成需要背的条文。
>
> 回到最基本的定义。随机变量是样本空间上的函数，每个抽样结果对应一个实数；而 $\mathrm{E}[X \mid Y = y]$ 是「先按 $Y$ 的取值筛出一个小世界，再在这个小世界里按条件分布求加权平均」。把 $y$ 换成 $Y$，等于把这两步复合起来：先抽一次样得到 $Y$ 的取值，再在那个取值指定的小世界里平均。复合函数仍然以抽样结果为输入，所以输出仍随抽样变化——它就是随机变量。反过来问一句「为什么必须这样定义」：因为只有它是随机变量，你才能对它再取一次期望（函数可以再平均），也才能谈它的方差；如果硬把它当成数，迭代期望律左边就成了常数，等式根本写不出来。这就是双重身份的全部内容，不是约定，是被后续运算逼出来的。
>
> 用断棍例把每个数都算实。取棍长 $\ell = 1$，第一折点 $Y$ 在单位区间上均匀，给定 $Y = y$ 后第二折点在该截上均匀，于是 $\mathrm{E}[X \mid Y] = Y/2$、$\mathrm{E}[X] = \mathrm{E}[Y/2] = 1/4$ 米。再往深算一层就能验证两套机器自洽：$X \mid Y = y$ 的方差是 $y^2/12$、二阶矩是 $y^2/3$，故 $\mathrm{E}[X^2] = \mathrm{E}[Y^2/3] = (1/3)(1/3) = 1/9$，得 $\mathrm{var}(X) = 1/9 - 1/16 = 7/144 \approx 0.0486$；改用全方差律走另一条路：组内项 $\mathrm{E}[\mathrm{var}(X \mid Y)] = \mathrm{E}[Y^2/12] = 1/36$，组间项 $\mathrm{var}(\mathrm{E}[X \mid Y]) = \mathrm{var}(Y/2) = (1/4)(1/12) = 1/48$，两项相加 $1/36 + 1/48 = 7/144$，与直算完全吻合。两条路线给出同一个数，说明「条件化后当随机变量用」这套语法是自洽的，不是拼凑。
>
> 跨课程连接要落到实处。6.042J 里函数的复合与部分应用是最直接的类比：$\mathrm{E}[\cdot \mid Y]$ 像一个接受参数 $Y$ 的高阶函数，喂进去一个具体的 $y$ 返回一个数，不喂参数时它本身还是一个待求值的表达式；编程里的 closure（闭包）就是「捕获了环境、还没被调用」的函数，与 $\mathrm{E}[X \mid Y]$ 的地位完全对应。CSAPP 第 3 章讲过程调用时，caller（调用者）与 callee（被调用者）之间有返回值约定：同一个函数换个实参就换一个返回值；这里的区别在于程序里的函数是确定性的、参数空间是离散的寄存器与内存，而 $\mathrm{E}[X \mid Y]$ 的「参数」是按概率分布抽出来的，同一个 $y$ 给同一个数，但 $y$ 本身在抽签。CLRS 里分析随机化算法时的写法也是同款：先固定随机选择求一个条件量，再把随机选择当变量对整个分布取平均，两步之间的对象类型切换与这里一模一样。区别只有一处：算法分析里通常只需要条件期望这一层，本讲还要往下走到条件方差。
>
> 所以这一条注解真正要记住的只有一个判据：看到 $\mathrm{E}[X \mid Y = y]$ 就问「这是数」，看到 $\mathrm{E}[X \mid Y]$ 就问「这是谁的函数」；类型对了，两条律就是自然推论，类型错了，怎么背都会在方差那一步翻车。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">var(X | Y) and its expectation（条件方差及其期望）</span>

- $\mathrm{var}(X \mid Y = y) = \mathrm{E}\big[(X - \mathrm{E}[X \mid Y = y])^2 \mid Y = y\big]$。
- $\mathrm{var}(X \mid Y)$：一个随机变量——当 $Y = y$ 时取值 $\mathrm{var}(X \mid Y = y)$。
- **全方差律（law of total variance）**：
```math
\mathrm{var}(X) = \mathrm{E}\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(\mathrm{E}[X \mid Y]\big).
```
- **证明（Proof）**：
  - (a) 回顾：$\mathrm{var}(X) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2$；
  - (b) $\mathrm{var}(X \mid Y) = \mathrm{E}[X^2 \mid Y] - (\mathrm{E}[X \mid Y])^2$；
  - (c) $\mathrm{E}\big[\mathrm{var}(X \mid Y)\big] = \mathrm{E}[X^2] - \mathrm{E}\big[(\mathrm{E}[X \mid Y])^2\big]$；
  - (d) $\mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \mathrm{E}\big[(\mathrm{E}[X \mid Y])^2\big] - (\mathrm{E}[X])^2$；
  - (c)、(d) 右端相加：$\mathrm{E}[X^2] - (\mathrm{E}[X])^2 = \mathrm{var}(X)$。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.225–227</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 这条注要把那四行证明拆成可以独立检查的零件：它看着只是移项，其实是同一个矩恒等式在三个不同的世界里各用一次，中间夹一次塔性质。搞清楚每一次用在哪、为什么必须用它，比记住结论有用得多。
>
> 第一步是把 $\mathrm{var}(X) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2$ 展开得到，纯代数，不涉及任何概率假设，只要两个矩存在。第二步是把同一条恒等式搬进「给定 $Y = y$」的条件世界：在那个世界里，条件分布就是一个普通分布，符号整体替换即可，条件方差就是围绕条件均值的二阶矩，不含新内容。真正的关节在第三步：对第二步两边取期望时，右端出现 $\mathrm{E}\big[\mathrm{E}[X^2 \mid Y]\big]$，要让它塌回 $\mathrm{E}[X^2]$，靠的是塔性质对函数 $g(X) = X^2$ 同样成立，而不是只对 $X$ 本身成立。这是全条证明唯一的隐含依赖：如果塔性质只是「对 $X$ 成立」的一条特殊事实，第三步立刻断掉，整个推导作废。第四步换一个对象：令 $Z = \mathrm{E}[X \mid Y]$，$Z$ 本身就是随机变量，于是第一步的恒等式可以原封不动套在它身上，得 $\mathrm{var}(Z) = \mathrm{E}[Z^2] - (\mathrm{E}[Z])^2$，而 $\mathrm{E}[Z] = \mathrm{E}[X]$ 又用了一次塔性质。最后相加，两项里同一个 $\mathrm{E}\big[(\mathrm{E}[X \mid Y])^2\big]$ 一带负号一带正号，必然精确对消，剩下的就是 $\mathrm{var}(X)$。对消不是巧合，而是这两项在结构上就是同一件东西被减了两次、加了一次。
>
> 给一组能逐一手算的数字验证。设 $Y$ 以各半的概率取 1 或 2；给定 $Y = 1$ 时 $X$ 取 8 或 12 各半（均值 10、方差 4），给定 $Y = 2$ 时 $X$ 取 17 或 23 各半（均值 20、方差 9）。于是组间项 $\mathrm{var}(\mathrm{E}[X \mid Y]) = 0.5 \times (10-15)^2 + 0.5 \times (20-15)^2 = 25$，组内项 $\mathrm{E}[\mathrm{var}(X \mid Y)] = 0.5 \times 4 + 0.5 \times 9 = 6.5$，公式给出 $\mathrm{var}(X) = 31.5$。换直算法核对：四个取值等概率，$\mathrm{E}[X] = (8+12+17+23)/4 = 15$，$\mathrm{E}[X^2] = (64+144+289+529)/4 = 256.5$，减去 $225$ 得 $31.5$，两路一致。这个例子里组间项占了八成，说明分层信息的价值密度：如果只看总方差 31.5，你会以为这批数据很散；拆开看才知道散在「组与组之间的距离」，组内其实很紧。
>
> 跨课程连接放在线性代数上最清楚。Strang 的课程里，正交投影把向量分解成 $\mathbf{x} = P\mathbf{x} + (I-P)\mathbf{x}$，两块互相垂直，于是范数平方可加，交叉项为零；全方差律是同一件事在概率里的版本，把随机变量分解成「条件均值的部分」加「围绕条件均值的残差部分」，两块在协方差意义下不相关，于是方差可加。区别在于：投影分解靠内积正交，交叉项为零是一个几何事实；这里的交叉项为零是纯代数对消，两种分解的合法性来源并不相同。统计学里的 ANOVA（方差分析）表就是这条律的有限样本版，把总平方和拆成组内平方和加组间平方和，回归分析里判断变量有没有解释力，看的正是组间那一块占总量的比例，这与上面 25 比 31.5 的算术是同一个判据。CSAPP 里没有直接对应物，最接近的是第 6 章的平均访问时间公式，它只用到了迭代期望律的均值版，没有走到二阶矩这一层。
>
> 合起来看，全方差律把「总波动」拆成两个互不重复计费的来源：组内是同一条件下你还要面对的随机性，组间是条件本身在漂移；拿它去判断一个模型，就等于问「我用来分层的那个变量，到底解释掉了多少方差」。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Section means and variances（分班示例：均值）</span>

两个班：$y = 1$（10 名学生）；$y = 2$（20 名学生）。

- $y = 1$：$\dfrac{1}{10} \displaystyle\sum_{i=1}^{10} x_i = 90$；$\quad y = 2$：$\dfrac{1}{20} \displaystyle\sum_{i=11}^{30} x_i = 60$。
- 总平均：
```math
\mathrm{E}[X] = \frac{1}{30} \sum_{i=1}^{30} x_i = \frac{90 \cdot 10 + 60 \cdot 20}{30} = 70 .
```
- $\mathrm{E}[X \mid Y = 1] = 90$，$\quad \mathrm{E}[X \mid Y = 2] = 60$；
```math
\mathrm{E}[X \mid Y] = \begin{cases} 90, & \text{w.p.（以概率） } 1/3, \\ 60, & \text{w.p. } 2/3; \end{cases}
```
```math
\mathrm{E}\big[\mathrm{E}[X \mid Y]\big] = \frac{1}{3} \cdot 90 + \frac{2}{3} \cdot 60 = 70 = \mathrm{E}[X],
```
```math
\mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \frac{1}{3} (90 - 70)^2 + \frac{2}{3} (60 - 70)^2 = \frac{600}{3} = 200 .
```

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.223–227</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Section means and variances (ctd.)（分班示例（续）：方差）</span>

- $y = 1$：$\dfrac{1}{10} \displaystyle\sum_{i=1}^{10} (x_i - 90)^2 = 10$；$\quad y = 2$：$\dfrac{1}{20} \displaystyle\sum_{i=11}^{30} (x_i - 60)^2 = 20$。
- $\mathrm{var}(X \mid Y = 1) = 10$，$\quad \mathrm{var}(X \mid Y = 2) = 20$；
```math
\mathrm{var}(X \mid Y) = \begin{cases} 10, & \text{w.p. } 1/3, \\ 20, & \text{w.p. } 2/3; \end{cases} \qquad \mathrm{E}\big[\mathrm{var}(X \mid Y)\big] = \frac{1}{3} \cdot 10 + \frac{2}{3} \cdot 20 = \frac{50}{3}.
```
- 全方差律合龙：
```math
\mathrm{var}(X) = \mathrm{E}\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \frac{50}{3} + 200 ,
```
  即（各班内部的平均波动）$+$（班与班之间的波动）。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.227</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example（例：把公式用起来）</span>

$\mathrm{var}(X) = \mathrm{E}[\mathrm{var}(X \mid Y)] + \mathrm{var}(\mathrm{E}[X \mid Y])$

> <span style="color:#7f8c8d;">图：$f_X(x)$ 按 $Y = 1$、$Y = 2$ 两个班分层标出的示意——两班的混合权重分别为 $1/3$ 与 $2/3$（与 30 人分班一致）。</span>

**课堂填空**：
- $\mathrm{E}[X \mid Y = 1] = \underline{\qquad}$，$\quad \mathrm{E}[X \mid Y = 2] = \underline{\qquad}$
- $\mathrm{var}(X \mid Y = 1) = \underline{\qquad}$，$\quad \mathrm{var}(X \mid Y = 2) = \underline{\qquad}$
- $\mathrm{E}[X] = \underline{\qquad}$
- $\mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.223–227</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 课堂填空的四个横线上写的都是数，但填空真正的考点不是算术，而是权重从哪来。同一批学生的成绩，按人数加权得 70，按班级等权得 75；两个答案都「算得对」，只有一个对得上题目设定的抽样方式。这条注就是把这条机制钉死，再用一组自己的小数据把它验一遍。这类错误危险的地方在于它不会报错，两个答案都干净利落，错的只是你没有说出口的那句假设。
>
> 机制可以拆成三句话。第一，随机变量是「随机抽一个学生看他的分数」，所以抽样单位是人，不是班，任意一个学生被抽到的机会相同，落进 $y = 1$ 的概率就是该班人数占总人数的比例 $1/3$，落进 $y = 2$ 就是 $2/3$；这个权重完全由抽样单位决定，跟班级个数无关。第二，迭代期望律的加权就是按 $p_Y(y)$ 加权，而 $p_Y$ 的含义正是「抽到该层的概率」，所以权重只能是人数比。第三，如果换成「先等概率抽一个班、再从班里抽一个人」，模型变了，$p_Y$ 变成各半，同样 30 个分数算出来的总体均值是 75，方差也不是原来的数——这不是精度问题，而是两个不同的概率模型给出的两个不同答案。拿错权重会错多少，可以量化：若用各半，组间项变成 $0.5 \times (90-75)^2 + 0.5 \times (60-75)^2 = 225$，组内项变成 $0.5 \times 10 + 0.5 \times 20 = 15$，合计 240；正确答案是 $50/3 + 200 \approx 216.7$，相对偏差约一成。
>
> 再造一组能一行行手加的小数据，把「人数加权」和「总方差」两条都走通。设甲班 2 人，分数 78 与 82，班均值 80、班内方差 4；乙班 3 人，分数 57、60、63，班均值 60、班内方差 6。总人数 5，权重分别是 $2/5$ 与 $3/5$。总体均值 $\mathrm{E}[X] = (2/5) \times 80 + (3/5) \times 60 = 32 + 36 = 68$，与把五个分数直接相加除以五得到的 $340/5 = 68$ 一致。组内项 $\mathrm{E}[\mathrm{var}(X \mid Y)] = (2/5) \times 4 + (3/5) \times 6 = 1.6 + 3.6 = 5.2$；组间项 $\mathrm{var}(\mathrm{E}[X \mid Y]) = (2/5) \times (80-68)^2 + (3/5) \times (60-68)^2 = 57.6 + 38.4 = 96$；合计 $101.2$。直算核对：五个分数的平方和是 $6084 + 6724 + 3249 + 3600 + 3969 = 23626$，除以五得 $4725.2$，减去 $68^2 = 4624$，正好 $101.2$。这里组间项占九成五，说明两个班的水平差异远大于班内差异，任何按班分层的统计报告都该先报班均值再报班内离散度。
>
> 跨课程连接最硬的一条在 CSAPP 第 6 章。存储层次的平均访问时间写成「命中时间加上未命中率乘未命中代价」，拆开看就是 $\mathrm{E}[\text{时间}] = \mathrm{E}[\text{时间} \mid \text{命中}]\, p_{\text{命中}} + \mathrm{E}[\text{时间} \mid \text{未命中}]\, p_{\text{未命中}}$，与分班求总平均是同一个式子，权重同样不是随便取的，而是「一次访问落进这一层的概率」，由工作集大小与该层容量共同决定。区别在于存储层次的层数固定为两三层、每层的条件分布近乎确定，所以工程上只关心均值，很少去问它的方差；而分班例子里权重由人数决定、层数只有两层，我们还需要方差来判断分层解释掉了多少波动。6.042J 里加权平均与期望的定义是更早的同一块肌肉，那边的权重是从分布表里直接读出来的。
>
> 所以那六个空填完之后要回看一眼：每一个数都能从「抽样单位是谁」推出权重、从权重推出总数，这条链路通了，全方差律就不再是需要记忆的公式，而是把两个乘法各做一遍的记账。顺带一个自检习惯：算完分层平均，把权重换成等权再算一遍，若两个数差得离谱，先回头确认抽样单位到底是人还是班。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Sum of a random number of independent r.v.s（随机个独立随机变量之和）</span>

- $N$：光顾的商店家数（nonnegative integer r.v.，非负整数值随机变量）。
- $X_i$：在第 $i$ 家店花的钱数：
  - 假定 $X_i$ 为 i.i.d.（independent and identically distributed，独立同分布）；
  - 且与 $N$ 独立。
- 令 $Y = X_1 + \cdots + X_N$：
```math
\begin{aligned}
\mathrm{E}[Y \mid N = n] &= \mathrm{E}[X_1 + X_2 + \cdots + X_n \mid N = n] \\
&= \mathrm{E}[X_1 + X_2 + \cdots + X_n] \\
&= \mathrm{E}[X_1] + \mathrm{E}[X_2] + \cdots + \mathrm{E}[X_n] \\
&= n\, \mathrm{E}[X];
\end{aligned}
```
  （中间一步：$X_1, \ldots, X_n$ 与事件 $\{N = n\}$ 独立）
- 于是 $\mathrm{E}[Y \mid N] = N\, \mathrm{E}[X]$，且
```math
\mathrm{E}[Y] = \mathrm{E}\big[\mathrm{E}[Y \mid N]\big] = \mathrm{E}\big[N\, \mathrm{E}[X]\big] = \mathrm{E}[N]\, \mathrm{E}[X].
```

> <span style="color:#7f8c8d;">Bertsekas §4.5, p.240–241</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 验证）:**</span> 这条注要把「把随机项数钉死再推理」抽象成一个可以反复套用的模板，并验证它的每一步为什么合法。模板的名字叫 freeze（冻结）：遇到「项数随机」这种麻烦，先假装它是常数，把已知工具全用上，最后再把常数换回随机变量、用一次条件期望收尾。这个套路值钱的地方在于它不依赖题目的具体分布，只依赖两条假设。
>
> 逐步看因果。第一步只是把条件期望按定义写开，无条件成立。第二步是全条的命门：$X_1, \ldots, X_n$ 与事件 $\{N = n\}$ 独立，意味着这个事件不携带任何关于各笔金额的信息，于是条件分布与无条件分布重合，条件期望塌成无条件期望；反过来，只要这条假设松动——比如「店逛得越多、每笔花得越少」——第二步就会把条件信息抹掉，结果必然错。第三步是期望线性，它不需要任何独立性，这条在 Lec 07 已经练过，这里只是把 $n$ 项各拆一次。第四步用同分布把 $n$ 个相同的数并成 $n\,\mathrm{E}[X]$。最后一步对 $N$ 取期望，外层又是一次线性，因为 $\mathrm{E}[X]$ 是常数可以提到外面。整条链只有一处真正用到「独立」，但少了它结论立刻变成不等式。
>
> 这条结论在文献里有名字：它是 Wald's equation（沃尔德等式）在「项数与各项独立」这一简化假设下的特例，由 Abraham Wald 在 1944 年发表于 Annals of Mathematical Statistics 第 15 卷第 3 期第 283 至 296 页的论文里给出；一般版本只需要项数与停时满足弱得多的条件，代价是证明要用到停时论证，本课程不涉及。
>
> 数一遍。设光顾家数满足 $\mathrm{P}(N = 0) = 0.1$、$\mathrm{P}(N = 1) = 0.4$、$\mathrm{P}(N = 2) = 0.3$、$\mathrm{P}(N = 3) = 0.2$，于是 $\mathrm{E}[N] = 0 + 0.4 + 0.6 + 0.6 = 1.6$；单笔金额均值 $\mathrm{E}[X] = 20$ 元。公式给 $\mathrm{E}[Y] = 1.6 \times 20 = 32$ 元。逐层核对：$n = 0, 1, 2, 3$ 时条件均值分别是 $0, 20, 40, 60$，按权重加权得 $0.4 \times 20 + 0.3 \times 40 + 0.2 \times 60 = 8 + 12 + 12 = 32$，两个方向对上。再看假设被破坏的代价，构造一组相依数据：$N$ 仍以各半概率取 1 或 2，但令第 $i$ 笔金额为 $20 - 10N$，即逛一家时花 10 元、逛两家时每笔 0 元。此时 $N = 1$ 给出 $Y = 10$、$N = 2$ 给出 $Y = 0$，故 $\mathrm{E}[Y] = 5$；而公式会算成 $\mathrm{E}[N]\,\mathrm{E}[X] = 1.5 \times 5 = 7.5$，高了五成。差距的来源很直接：金额随逛店数下降，公式却假设两者互不知情。
>
> 跨课程连接有三条，路径要写清。6.042J 里的 indicator variable（指示变量）技巧把「有多少个」编码成若干个 0 与 1 相加，配合期望线性得到期望；freeze（冻结）是把「有多少项」编码成一个先固定后放开的整数，两者都是把难问题翻译成「一堆简单项之和」，区别在于指示变量处理的是「是否发生」，这里处理的是「发生多少次」。CLRS 分析随机化快排时先固定某次 pivot（枢轴）的选择再对所有随机选择求平均，是同一套两层期望的写法，区别是那边的项数是确定的、随机性在 pivot（枢轴）的位置。CSAPP 第 6 章估算未命中次数时也用同一个式子：总未命中数的期望等于访问条数乘每次未命中的概率，前提正是「访问条数与每次是否命中互不影响」；如果程序的分支让某些数据只在特定访问序列下才出现，这条前提就破了。
>
> 所以模板只有一句口诀：先冻结、后放开、最后平均；而所有出错都出在「放开」那一步——独立假设是它唯一的通行证。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Variance of sum of a random number of independent r.v.s（随机个独立随机变量之和的方差）</span>

- 从全方差律出发：$\mathrm{var}(Y) = \mathrm{E}[\mathrm{var}(Y \mid N)] + \mathrm{var}(\mathrm{E}[Y \mid N])$。
- 第二项：$\mathrm{E}[Y \mid N] = N\, \mathrm{E}[X]$，故 $\mathrm{var}\big(\mathrm{E}[Y \mid N]\big) = (\mathrm{E}[X])^2\, \mathrm{var}(N)$。
- 第一项：$\mathrm{var}(Y \mid N = n) = n\, \mathrm{var}(X)$，即 $\mathrm{var}(Y \mid N) = N\, \mathrm{var}(X)$，故 $\mathrm{E}\big[\mathrm{var}(Y \mid N)\big] = \mathrm{E}[N]\, \mathrm{var}(X)$。
- 合并：
```math
\mathrm{var}(Y) = \mathrm{E}\big[\mathrm{var}(Y \mid N)\big] + \mathrm{var}\big(\mathrm{E}[Y \mid N]\big) = \mathrm{E}[N]\, \mathrm{var}(X) + (\mathrm{E}[X])^2\, \mathrm{var}(N).
```

> <span style="color:#7f8c8d;">Bertsekas §4.5, p.240–243</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 这条注要回答的问题是：随机个独立随机变量之和的方差，为什么必须拆成两项，而不是像均值那样一次乘完就收工。答案藏在全方差律的结构里——方差有两个来源，均值的公式只有一项，天然只覆盖其中一个。把两个零件分别验一遍、再手工拼一次，是理解这条公式最省力的路径。
>
> 先看内层零件。给定 $N = n$，$Y$ 就是 $n$ 个独立同分布变量之和，独立性让所有协方差项为零，方差直接相加，得 $n\,\mathrm{var}(X)$；这一步如果独立性不成立，就得把 $\binom{n}{2}$ 个协方差项全带上，公式立刻从一行变成一页。再看外层零件：条件均值是 $N\,\mathrm{E}[X]$，它是一个随机变量，对它求方差时用到缩放规则，常数因子平方后提到外面，得 $(\mathrm{E}[X])^2\,\mathrm{var}(N)$；这里是平方，因为方差是二阶量，单位是「元」的平方，$-1$ 倍的缩放必须消掉。装配靠全方差律：组内那一项取期望后变成 $\mathrm{E}[N]\,\mathrm{var}(X)$，组间那一项原样保留，两者相加就是最终公式。
>
> 卡点值得单独说清：第二项的系数为什么是 $(\mathrm{E}[X])^2$ 而不是 $\mathrm{E}[X^2]$？因为组间项统计的只是「条件均值绕总均值的摆动」，而条件均值只用到单笔金额的均值这一个数；单笔金额围绕自身均值的摆动已经全部进了组内那一项。若误用 $\mathrm{E}[X^2]$，就等于把同一次波动计了两遍，方差会被系统性高估。用数字看：$\mathrm{E}[X] = 20$、$\mathrm{E}[X^2] = 425$ 时两者差二十倍，代入后结果从 875 膨胀到 2075，量级完全错位。
>
> 现在代数字。沿用 $\mathrm{E}[N] = 3$、$\mathrm{var}(N) = 2$、$\mathrm{E}[X] = 20$、$\mathrm{var}(X) = 25$，得 $\mathrm{var}(Y) = 3 \times 25 + 400 \times 2 = 75 + 800 = 875$，标准差约 29.6 元，而均值只有 60 元。换一个计数分布再验一次一致性：若 $N$ 服从 Poisson distribution（泊松分布）且均值 $\lambda = 3$，则 $\mathrm{var}(N) = \lambda = 3$，公式给 $3 \times 25 + 400 \times 3 = 1275$；另一边用恒等式 $\mathrm{var}(Y) = \lambda\,\mathrm{E}[X^2] = 3 \times 425 = 1275$，两条路给出同一个数——这个恒等式只在 Poisson distribution（泊松分布）下成立，因为它的方差等于均值，正好把两项合成一项，可以当作公式正确性的旁证。
>
> 跨课程连接要说清路径与区别。CLRS 分析随机化快排时，先固定整条 pivot（枢轴）选择序列求条件期望，再对随机性求平均，两步的骨架与这里完全相同；区别在于算法分析几乎只停在期望这一层，很少追问比较次数的方差，而本讲的第二项恰恰来自方差分解，是期望那套工具的升级版。Strang 的线性代数给出几何解释：正交投影把向量分解成投影分量与残差分量，两块的平方和可加，全方差律是同一个分解在概率上的对应物，区别是那里的合法性来自内积正交、这里的合法性来自代数对消。CSAPP 第 6 章级的工程实践则提示为什么要方差：平均访问时间只回答典型情况，而 p99 尾部延迟才是用户抱怨的来源，$875$ 里那 $800$ 就是「行为本身在变」带来的不可消除的部分，靠优化单笔金额的分布收效有限。
>
> 所以这条公式的读法是：随机和的波动等于「平均做多少次」乘「单次的抖动」，加上「单次平均值的平方」乘「次数本身的抖动」；前一项靠减少单次方差压，后一项只能靠稳住次数来压，两条互不替代。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
