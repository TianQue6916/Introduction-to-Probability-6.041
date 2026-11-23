<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 1 解答（Quiz 1 — SOLUTIONS）**</span> <span style="color:#7f8c8d;">（Spring 2009，2009 春季学期；考试时间：2009 年 3 月 11 日（周三）19:30–21:30）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

<span style="color:#7f8c8d;">原封面设有姓名（Name）与复习课教师（Recitation Instructor）填写栏，并附如下评分表与考试须知。</span>

| 题号（Question） | 各小题满分（Out of） | 小计 |
|:---:|:---|:---:|
| 0 | — | 2 |
| 1 | 全部（all） | 40 |
| 2 | a=5，b=2，c=5，d=5，e=5，f=5 | 27 |
| 3 | a=2，b=2，c=2，d=5，e=5，f=5，g=5，h=5 | 31 |
| **总分（Total）** | | **100** |

<span style="color:#7f8c8d;">（原卷为 Question / Part / Score / Out of 四列评分表，Score（得分）列在解答卷中留空。）</span>

**考试须知：**

- 请在本试卷册内作答，只有写在试卷册内的解答才会被评分。
- 第一题为多项选择题，不给部分分（no partial credit）；第二、三题可以获得部分分。
- 允许携带一张双面 8.5×11 英寸公式纸和一台计算器。
- 考试时长为 120 分钟。
- 请书写工整！无法辨认的内容将得不到分数。
- 评分后的试卷将于 3 月 17 日（周二）在复习课（recitation）上发还。

---

<!-- ===== PDF p2 ===== -->

<span style="color:#c0392b;">**Question 1　多项选择题（Multiple Choice Questions）**</span>

<span style="color:#2471a3;">**[problem]**</span> 请清晰地圈出正确选项。如有需要可使用草稿纸，但多项选择题**不给部分分**。每道多项选择题 4 分。

**a.** 下列哪项陈述是**不**正确的（NOT true）？

- (i) 若 $A\subset B$，则 $P(A)\le P(B)$。
- (ii) 若 $P(B)>0$，则 $P(A\mid B)\ge P(A)$。
- (iii) $P(A\cap B)\ge P(A)+P(B)-1$。
- (iv) $P(A\cap B^c)=P(A\cup B)-P(B)$。

> <span style="color:#2471a3;">**[solution]**</span> 反例：取两个事件 $A$、$B$，使得 $P(B)>0$、$P(A)>0$，但 $A\cap B=\emptyset$，那么 $P(A\mid B)=0$，而 $P(A)>P(A\mid B)$。这样的例子很容易构造：例如，取任意一个样本空间及事件 $A$，满足 $P(A)>0$ 且 $P(A^c)>0$，于是 $P(A\mid A^c)=0$，但 $P(A)>0$。
>
> <span style="color:#1e8449;">**[mathtip]**</span> 选项 (iv) 恒成立：$P(A\cap B^c)=P(A)-P(A\cap B)=P(A\cup B)-P(B)$；选项 (iii) 亦恒成立（把 $P(A\cup B)\le 1$ 移项即得）。故不成立的只有 (ii)。

**b.** 把 $n$ 只相同的球随机地抛入 $m$ 个瓮中，每个瓮被选中的可能性相同，且每次抛掷与其他任何一次抛掷相互独立。第 $i$ 个瓮是空的概率是多少？

- (i) $\left(1-\dfrac{1}{m}\right)^{n}$
- (ii) $\left(1-\dfrac{1}{n}\right)^{m}$
- (iii) $\dbinom{m}{n}\left(1-\dfrac{1}{n}\right)^{m}$
- (iv) <span style="color:#7f8c8d;">原文此选项的公式在 PDF 提取时残缺（仅余 $n$、$\frac{1}{n}$、$m$、$m$ 等符号片段），无法可靠还原。</span>

> <span style="color:#2471a3;">**[solution]**</span> 第 $j$ 只球进入第 $i$ 个瓮的概率是 $1/m$；因此第 $j$ 只球**不**进入第 $i$ 个瓮的概率是 $\left(1-\frac{1}{m}\right)$。由于各次抛掷彼此独立，可以把这些概率相乘：全部 $n$ 只球都不进入第 $i$ 个瓮（即该瓮为空）的概率为
>
> ```math
> \left(1-\frac{1}{m}\right)^{n}.
> ```

**c.** 我们同时且独立地抛两枚均匀硬币。若两枚硬币的结果相同，我们获胜；否则我们输。令 $A$ 为事件「第一枚硬币正面朝上」，$B$ 为事件「第二枚硬币正面朝上」，$C$ 为事件「我们获胜」。下列哪项陈述是正确的？

- (i) 事件 $A$ 与 $B$ 不独立。
- (ii) 事件 $A$ 与 $C$ 独立。
- (iii) 给定 $C$，事件 $A$ 与 $B$ 条件独立。
- (iv) 获胜的概率是 $3/4$。

> <span style="color:#2471a3;">**[solution]**</span> 此时的样本空间为 $\Omega=\{(H,H),(H,T),(T,H),(T,T)\}$，概率律是该空间上的均匀分布。我们有 $A=\{(H,H),(H,T)\}$，$B=\{(H,H),(T,H)\}$，$C=\{(H,H),(T,T)\}$。由 discrete uniform law（离散均匀分布律），

<!-- ===== PDF p3 ===== -->

> **Question 1.c（续）** $P(A)=P(B)=P(C)=1/2$。又因 $P(A\cap C)=1/4$，故 $P(A\cap C)=P(A)P(C)$，这两个事件独立。直观地说，知道"你赢了"并不会提供任何关于你的硬币是否正面朝上的信息：形式化地表述，即 $P(A\mid C)=P(A)$。

**d.** 一枚不均匀硬币出现"正面"的概率为 $1/3$。令 $H$ 为五次独立抛掷中正面出现的次数。求概率 $P(\text{第一次抛出正面}\mid H=1\ \text{或}\ H=5)$。

- (i)–(iii) <span style="color:#7f8c8d;">原文此三个选项为含 $\left(\frac{1}{3}\right)$、$\left(\frac{2}{3}\right)^{4}$、$\binom{5}{1}$、$\binom{5}{5}$ 等的分数表达式，PDF 提取时交错损毁，无法逐一可靠还原。</span>
- (iv) $\dfrac{1}{5}$

> <span style="color:#2471a3;">**[solution]**</span> 令 $A$ 为事件「第一次抛出正面」。
>
> ```math
> P\bigl(A\mid\{H=1\}\cup\{H=5\}\bigr)
> =\frac{P\bigl(A\cap(\{H=1\}\cup\{H=5\})\bigr)}{P(\{H=1\}\cup\{H=5\})}
> =\frac{P\bigl((A\cap\{H=1\})\cup(A\cap\{H=5\})\bigr)}{P(\{H=1\}\cup\{H=5\})}
> ```
>
> ```math
> =\frac{P(\{H=5\})+P(A\cap\{H=1\})}{P(\{H=1\})+P(\{H=5\})}
> =\frac{(1/3)^{5}+(1/3)(2/3)^{4}}{\dbinom{5}{1}(1/3)(2/3)^{4}+\dbinom{5}{5}(1/3)^{5}}
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 该值为 $\dfrac{1+16}{80+1}=\dfrac{17}{81}\approx 0.210$（分子 $=\frac{1}{243}+\frac{16}{243}$，分母 $=5\times\frac{16}{243}+\frac{1}{243}$）。

**e.** 一副充分洗乱的 52 张扑克牌被平均发给两名玩家（每人 26 张）。玩家 1 拿到全部 A（4 张）的概率是多少？

- (i)–(ii)、(iv) <span style="color:#7f8c8d;">原文选项为含 $\dbinom{48}{22}$、$\dbinom{52}{26}$、$\dfrac{26\times25\times24\times23}{52\times51\times50\times49}$、因子 $4$ 与 $4!$ 等的分数表达式，PDF 提取时各选项的分数结构严重交错，无法可靠还原。</span>
- (iii) $\dfrac{48!\;26!}{22!\;52!}$

<!-- ===== PDF p4 ===== -->

> <span style="color:#2471a3;">**[solution]**</span> 令 $A$ 为事件「玩家 1 拿到全部 A」。由离散均匀分布律，
>
> ```math
> P(A)=\frac{|A|}{|\Omega|}\qquad (1)
> ```
>
> 其中 $|\Omega|=\dbinom{52}{26}$ 是玩家 1 可能拿到的手牌数目（从 52 张中取 26 张）。此外，一旦把所有 A 都发给了玩家 1，还必须从剩下 48 张牌中再发给他 22 张。因此，
>
> ```math
> P(A)=\frac{\dbinom{48}{22}}{\dbinom{52}{26}}.
> ```

**f.** 设 $X$、$Y$、$Z$ 是三个相互独立的离散随机变量。那么 $X$ 与 $Y+Z$ 是

- (i) always（总是）
- (ii) sometimes（有时）
- (iii) never（从不）

独立的。

> <span style="color:#2471a3;">**[solution]**</span> 由于 $X$ 与 $Y$、$Z$ 都独立，$X$ 与任意函数 $g(Y,Z)$ 独立，其中也包括 $g(Y,Z)=Y+Z$。<span style="color:#7f8c8d;">（见教材第 114 页。）</span> <span style="color:#7f8c8d;">（故应选 (i) always/总是。）</span>

**g.** 为了拿到驾驶执照，Mina 需要通过驾驶考试。Mina 每次参加驾驶考试，都会以 $1/2$ 的概率通过，且与她过去的经历无关。Mina 第一次考试没有通过。给定这一事实，令 $Y$ 为 Mina 在拿到执照之前还需参加的额外考试次数。那么，

- (i) $E[Y]=1$。
- (ii) $E[Y]=2$。
- (iii) $E[Y]=0$。

> <span style="color:#2471a3;">**[solution]**</span> $Y$ 被定义为 Mina 额外参加的考试次数，所以它与"她第一次考试未通过"这一事实无关。$Y$ 是 $p=1/2$ 的 geometric RV（几何随机变量）。因此 $E[Y]=1/p=2$。

**h.** 考虑两个随机变量 $X$ 与 $Y$，各自取值于 $\{1,2,3\}$。设它们的联合 PMF 满足：对任意 $1\le x,y\le 3$，若 $(x,y)\in\{(1,3),(2,1),(3,2)\}$，则 $P_{X,Y}(x,y)=0$；若 $(x,y)\in\{(1,1),(1,2),(2,2),(2,3),(3,1),(3,3)\}$，则 $P_{X,Y}(x,y)>0$。那么，

- (i) $X$ 与 $Y$ 可能独立也可能不独立，取决于 $P_{X,Y}(x,y)$ 在 $\{(1,1),(1,2),(2,2),(2,3),(3,1),(3,3)\}$ 上的取值。
- (ii) $X$ 与 $Y$ 总是独立的。
- (iii) $X$ 与 $Y$ 永远不可能独立。

> <span style="color:#2471a3;">**[solution]**</span> 举例来说，若我们获知 $X=1$，就知道 $Y$ 永远不可能取值 3；然而在没有关于 $X$ 的这一信息时，$p_Y(3)$ 严格为正。于是对 $x=1$、$y=3$ 有 $p_{Y\mid X}(y\mid x)\ne p_Y(y)$，即 $X$ 与 $Y$ 永远不可能独立。

<!-- ===== PDF p5 ===== -->

**i.** 设想你和一位朋友玩如下的"配硬币"（matching coins）游戏。你和朋友各有一枚自己的硬币。每一轮，你们两人同时向对方亮出硬币的一面（正面 H 或反面 T）。若两面相同，你从朋友那里赢得 1 美元；若两面不同，你输给朋友 1 美元。你的朋友在长期选择亮哪一面时有一套复杂（未知的）策略。你决定采用如下简单策略：每一轮，你都独立地抛你那枚均匀硬币，并把结果亮给朋友（当然，在你亮出之前，朋友并不知道你随机抛掷的结果）。那么，

- (i) 平均而言，你会输钱给这位聪明的朋友。
- (ii) 平均而言，你既不输也不赢，也就是说，你的平均盈亏为 0。
- (iii) 平均而言，你会从朋友那里赚钱。

> <span style="color:#2471a3;">**[solution]**</span> 令 $X_i$ 为表示你在游戏第 $i$ 轮中盈亏的随机变量，即你赢时 $X_i=1$、输时 $X_i=-1$。每一轮你的朋友都会用某种你并不知道的策略选择正面或反面。关键性质是：无论朋友作出何种选择，我们都有 $p_{X_i}(1)=p_{X_i}(-1)=0.5$，也就是说，我们的抛掷结果总以 0.5 的概率与朋友的选择相匹配。可以验证 $E[X_i]=0$，因此你的平均盈亏为 0。

**j.** 设 $X_i$（$1\le i\le 4$）为独立的 Bernoulli random variable（伯努利随机变量），均值均为 $p=0.1$。令 $X=\sum\limits_{i=1}^{4}X_i$。那么，

- (i) $E[X_1\mid X=2]=0.1$。
- (ii) $E[X_1\mid X=2]=0.5$。
- (iii) $E[X_1\mid X=2]=0.25$。

> <span style="color:#2471a3;">**[solution]**</span> 我们有 $P(X_1=1\mid X=2)=0.5$，因为
>
> ```math
> P(X_1=1\mid X=2)=\frac{P(X_1=1\cap X=2)}{P(X=2)}
> =\frac{p\times\dbinom{3}{1}p(1-p)^{2}}{\dbinom{4}{2}p^{2}(1-p)^{2}}
> =\frac{\dbinom{3}{1}}{\dbinom{4}{2}}=\frac{1}{2}=0.5
> ```
>
> （注意：$\dbinom{4}{2}p^{2}(1-p)^{2}$ 是 4 次抛掷中恰出现 2 次正面的概率，而 $\dbinom{3}{1}p(1-p)^{2}$ 是后 3 次抛掷中恰出现 1 次正面的概率。）
>
> 因此，
>
> ```math
> E[X_1\mid X=2]=1\times P(X_1=1\mid X=2)+0\times P(X_1=0\mid X=2)=0.5
> ```

<!-- ===== PDF p6 ===== -->

---

<span style="color:#c0392b;">**Question 2（第 2 题）**</span>

<span style="color:#2471a3;">**[problem]**</span> Alice 和 Bob 都需要买一辆自行车。车行库存有 4 辆绿色、3 辆黄色和 2 辆红色的自行车。Alice 随机挑选其中一辆并买下；紧接着 Bob 做同样的事。绿色、黄色、红色自行车的售价分别为 300 美元、200 美元和 100 美元。令 $A$ 为事件「Alice 买了一辆绿色自行车」，$B$ 为事件「Bob 买了一辆绿色自行车」。

**a.**（5 分）$P(A)$ 是多少？$P(A\mid B)$ 是多少？

> <span style="color:#2471a3;">**[solution]**</span> 我们有 $P(A)=4/9$（9 辆车中有 4 辆绿车），以及 $P(A\mid B)=3/8$（既然已知 Bob 买了一辆绿车，Alice 就只能从剩下 8 辆中的 3 辆绿车里选）。

**b.**（2 分）$A$ 与 $B$ 是独立事件吗？请说明理由。

> <span style="color:#2471a3;">**[solution]**</span> 由于 $P(A)\ne P(A\mid B)$，这两个事件不独立。非正式地说：绿车的数量是固定的，如果 Alice 买走了一辆，那么 Bob 也买到一辆的机会就会略微下降。

**c.**（5 分）两人中至少有一人买到绿车的概率是多少？

> <span style="color:#2471a3;">**[solution]**</span> 所求概率为 $P(A\cup B)$。我们有
>
> ```math
> \begin{aligned}
> P(A\cup B)&=P(A)+P(B)-P(A\cap B)\\
> &=P(A)+P(B)-P(A\mid B)\cdot P(B)\\
> &=\frac{4}{9}+\frac{4}{9}-\frac{3}{8}\cdot\frac{4}{9}
> =\frac{13}{18}=0.722.
> \end{aligned}
> ```

<!-- ===== PDF p7 ===== -->

**d.**（5 分）Alice 和 Bob 买到不同颜色自行车的概率是多少？

> <span style="color:#2471a3;">**[solution]**</span> 我们先计算两人买到同色自行车的概率。我们有
>
> ```math
> P(\{G,G\})=\frac{4\cdot 3}{9\cdot 8},\qquad
> P(\{Y,Y\})=\frac{3\cdot 2}{9\cdot 8},\qquad
> P(\{R,R\})=\frac{2\cdot 1}{9\cdot 8}.
> ```
>
> 因此，买到不同颜色自行车的概率为
>
> ```math
> P(\text{不同颜色})=1-P(\text{同色})=1-\left(\frac{12}{72}+\frac{6}{72}+\frac{2}{72}\right)
> =\frac{13}{18}=0.722.
> ```

**e.**（5 分）已知 Bob 买了一辆绿车，Alice 花费金额的期望值是多少？

> <span style="color:#2471a3;">**[solution]**</span> 若 Bob 买了一辆绿车，则 Alice 买到绿、黄、红车的条件概率分别为 $\dfrac{3}{8}$、$\dfrac{3}{8}$ 与 $\dfrac{2}{8}$。因此 Alice 花费金额的期望为
>
> ```math
> \$300\cdot\frac{3}{8}+\$200\cdot\frac{3}{8}+\$100\cdot\frac{2}{8}=\$212.50.
> ```

**f.**（5 分）令 $G$ 为 Alice 和 Bob 光顾之后店里剩余绿车的数量。计算 $P(B\mid G=3)$。

> <span style="color:#2471a3;">**[solution]**</span> 若 $G=3$，则恰好有一辆绿车被买走。由对称性，Alice 与 Bob 买走它的机会相等，故 $P(B\mid G=3)=\dfrac{1}{2}$。另一种做法：定义 $A\setminus B$ 为属于 $A$ 但不属于 $B$ 的元素。我们有：
>
> ```math
> P(B\mid G=3)=P\bigl(B\mid\{A\setminus B\}\cup\{B\setminus A\}\bigr)
> =\frac{P(B\setminus A)}{P(\{A\setminus B\}\cup\{B\setminus A\})}
> =\frac{20/72}{40/72}=\frac{1}{2}.
> ```

<!-- ===== PDF p8 ===== -->

---

<span style="color:#c0392b;">**Question 3（第 3 题）**</span>

<span style="color:#2471a3;">**[problem]**</span> Magic Games Inc.（魔法游戏公司）是一家出售各种趣味游戏的商店。它的热门产品之一是魔法四面骰（magic 4-sided dice）。这种骰子成对出售；每枚骰子既可以是公平的（fair）也可以是不规则的（crooked），而且一对骰子可以彼此独立地工作，某些情况下骰子内部还装有磁铁，使它们一起掷出时的表现不可预测。

Xavier 和 Yvonne 一起从这家店买了一对骰子。两人各从这对骰子中挑出一枚；然后由其中一人把两枚骰子一起掷出。令 $X$ 为 Xavier 骰子的点数，$Y$ 为 Yvonne 骰子的点数。$X$ 与 $Y$ 的联合 PMF（joint PMF，联合概率质量函数）$p_{X,Y}(x,y)$ 由下表给出：

| | $X=1$ | $X=2$ | $X=3$ | $X=4$ |
|:---:|:---:|:---:|:---:|:---:|
| $Y=4$ | 1/20 | 1/20 | 1/20 | 2/20 |
| $Y=3$ | 1/20 | 1/20 | 2/20 | 1/20 |
| $Y=2$ | 1/20 | 2/20 | 1/20 | 1/20 |
| $Y=1$ | 2/20 | 1/20 | 1/20 | 1/20 |

**（a）**（2 分）求 Xavier 骰子点数的 PMF $p_X(x)$。

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> p_X(x)=\sum_{y=1}^{4}p_{X,Y}(x,y)=
> \begin{cases}
> \dfrac{1}{4}, & x=1,2,3,4,\\[4pt]
> 0, & \text{o.w.（其他情形）}.
> \end{cases}
> ```

**（b）**（2 分）求 Yvonne 骰子点数的 PMF $p_Y(y)$。

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> p_Y(y)=\sum_{x=1}^{4}p_{X,Y}(x,y)=
> \begin{cases}
> \dfrac{1}{4}, & y=1,2,3,4,\\[4pt]
> 0, & \text{o.w.（其他情形）}.
> \end{cases}
> ```

**（c）**（2 分）$X$ 与 $Y$ 独立吗？

> <span style="color:#2471a3;">**[solution]**</span> 不独立。众多反例之一：$p_X(x)\ne p_{X\mid Y}(x\mid 2)$。

<!-- ===== PDF p9 ===== -->

Zach 和 Wendy 对 Xavier 和 Yvonne 的骰子很感兴趣。他们来到这家店，买了一对属于自己的骰子。同样，两人各挑一枚；然后由其中一人把两枚一起掷出。令 $Z$ 为 Zach 骰子的点数，$W$ 为 Wendy 骰子的点数。$Z$ 与 $W$ 的联合 PMF $p_{Z,W}(z,w)$ 由下表给出：

| | $Z=1$ | $Z=2$ | $Z=3$ | $Z=4$ |
|:---:|:---:|:---:|:---:|:---:|
| $W=4$ | 2/24 | 1/24 | 2/24 | 1/24 |
| $W=3$ | 2/24 | 1/24 | 2/24 | 1/24 |
| $W=2$ | 2/24 | 1/24 | 2/24 | 1/24 |
| $W=1$ | 2/24 | 1/24 | 2/24 | 1/24 |

这家店还出售各式各样的魔法硬币，有些是公平的，有些是不规则的。Alice 买了一枚每次抛掷都以 $3/4$ 概率正面朝上的硬币。

**（d）**（5 分）Alice 还在犹豫要不要也买些骰子，于是决定先试用朋友们的骰子。她这样做：首先抛自己的硬币；若正面朝上，就借 Xavier 和 Yvonne 的那对骰子来掷；若反面朝上，就改借 Zach 和 Wendy 的那对。求她掷出"对子"（double，即她所掷那一对骰子显示相同点数）的概率。

> <span style="color:#2471a3;">**[solution]**</span> 令事件 $D$ 为所有"对子"结果的集合，事件 $A$ 为 Alice 抛硬币正面朝上。利用 law of total probability（全概率定律）：
>
> ```math
> P(D)=P(D\mid A)P(A)+P(D\mid A^c)P(A^c)
> =\frac{3}{4}\times\frac{4}{10}+\frac{1}{4}\times\frac{1}{4}
> =\frac{58}{160}=0.3625
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 其中 $P(D\mid A)=\sum_{x}p_{X,Y}(x,x)=4\times\frac{2}{20}=\frac{4}{10}$，$P(D\mid A^c)=\sum_{z}p_{Z,W}(z,z)=\frac{2+1+2+1}{24}=\frac{1}{4}$，均可在上表中对角线读出。

<!-- ===== PDF p10 ===== -->

**（e）**（5 分）Alice 对骰子还没拿定主意，又做了另一个实验。她先抛硬币：若正面朝上，就拿起 Xavier 和 Yvonne 的骰子对反复地掷，直到掷出对子为止；若反面朝上，就对 Zach 和 Wendy 的骰子做同样的事。求她需要掷她所选那对骰子的期望次数。（假设同一对骰子被反复投掷时，各次投掷的结果相互独立。）

> <span style="color:#2471a3;">**[solution]**</span> 令随机变量 $N$ 为直到掷出对子为止的投掷次数。在给定所掷骰子对的条件下，$N$ 的分布是 geometric random variable（几何随机变量）。利用 total expectation theorem（全期望定理），$N$ 的期望值为：
>
> ```math
> E[N]=E[N\mid A]P(A)+E[N\mid A^c]P(A^c)
> =\frac{3}{4}\times\frac{10}{4}+\frac{1}{4}\times 4
> =\frac{23}{8}=2.875
> ```

**（f）**（5 分）Alice 对骰子失去了兴趣，决定改用她的硬币做实验。她不断抛硬币，直到总共看到 11 次正面为止。令 $R$ 为她看到的反面次数，求 $E[R]$。（假设各次抛掷相互独立。）

> <span style="color:#2471a3;">**[solution]**</span> Alice 直到看到总共 11 次正面为止所用的次数 $T$，是 11 个独立同分布、参数为 $p=\dfrac{3}{4}$ 的几何随机变量之和。随机变量 $R$（她看到的反面次数）为 $T-11$。于是：
>
> ```math
> E[R]=E[T]-11=11\times\frac{1}{3/4}-11=\frac{11}{12}=0.9167
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 经验算，$E[R]=11\times\dfrac{1}{3/4}-11=\dfrac{44}{3}-11=\dfrac{11}{3}\approx 3.667$（等价地，负二项均值 $r\frac{1-p}{p}=11\times\frac{1/4}{3/4}=\frac{11}{3}$）。原文印作 $\frac{11}{12}=0.9167$，疑为把 $\frac{1}{3/4}$ 误简约成 $\frac{1}{3\times4}$ 所致的笔误。

<!-- ===== PDF p11 ===== -->

**（g）**（5 分）Alice 用她的硬币又试了一个实验。令 $A$ 为事件「她看到的第二次正面出现在第 7 次抛掷」，$S$ 为第一次正面出现的位置。求给定事件 $A$ 时 $S$ 的条件 PMF $p_{S\mid A}(s)$。

> <span style="color:#2471a3;">**[solution]**</span> 事件 $A$ 的概率可以这样求：在前 6 次结果中选出 1 次作为正面、其余为反面，再令第 7 次抛掷为正面，即 $\dbinom{6}{1}(1-p)^{5}p^{2}$，其中 $p=\dfrac{3}{4}$。而 $S=s$ 与事件 $A$ 的交 $P(S=s\cap A)$，对所有 $s$（$s=1,\ldots,6$）都具有概率 $(1-p)^{5}p^{2}$。因此 $p_{S\mid A}(s)=\dfrac{P(S=s\cap A)}{P(A)}$ 是 $s$ 在 $1,\ldots,6$ 范围上的均匀分布：
>
> ```math
> p_{S\mid A}(s)=
> \begin{cases}
> \dfrac{1}{6}, & s=1,\ldots,6,\\[4pt]
> 0, & \text{o.w.（其他情形）}.
> \end{cases}
> ```

**（h）**（5 分）Alice 的朋友 Bob 从同一家店买了一枚硬币，结果这枚硬币是公平的，即每次抛掷正面朝上的概率为 $1/2$。他反复抛这枚硬币，直到总共看到 11 次正面或总共 11 次反面为止。令 $U$ 为他需要抛硬币的次数，求 $U$ 的 PMF $p_U(u)$。（假设各次抛掷相互独立。）

> <span style="color:#2471a3;">**[solution]**</span> Bob 至少要抛 11 次、至多抛 21 次，才能凑齐 11 次正面或 11 次反面。「Bob 恰好需要 $u$ 次抛掷、且其中 11 次是正面」这一交事件，等于把所有"以一次正面收尾、且总共有 11 次正面"的 $\dbinom{u-1}{10}$ 个序列（即前 $u-1$ 次中恰含 10 次正面）的概率相加；每个这样的序列的概率为 $\left(\dfrac{1}{2}\right)^{u}$。由于硬币是公平的，$u$ 次抛掷的任何序列"出现 11 次正面、$u-11$ 次反面"与"出现 11 次反面、$u-11$ 次正面"是等可能的。因此，「Bob 恰好需要 $u$ 次抛掷、且其中 11 次是反面」的概率与"11 次正面"情形的概率相同。把这两个互斥的概率相加，即得 $p_U(u)$：
>
> ```math
> p_U(u)=
> \begin{cases}
> \dbinom{u-1}{10}\left(\dfrac{1}{2}\right)^{u-1}\cdot\left(\dfrac{1}{2}\right)\times 2
> =2\dbinom{u-1}{10}\left(\dfrac{1}{2}\right)^{u}, & u=11,\ldots,21,\\[8pt]
> 0, & \text{o.w.（其他情形）}.
> \end{cases}
> ```

<!-- ===== PDF p12 ===== -->

<span style="color:#7f8c8d;">【图】本页为 MIT OpenCourseWare 封面页：MIT OpenCourseWare（http://ocw.mit.edu），课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010（OCW 发布学期标注）；并含引用信息与使用条款（Terms of Use）链接 http://ocw.mit.edu/terms。无正文内容。</span>
