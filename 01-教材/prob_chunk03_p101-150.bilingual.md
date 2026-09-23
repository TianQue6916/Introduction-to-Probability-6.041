
<!-- ===== PDF p101 ===== -->
<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">例 2.3：问答问题（The Quiz Problem）</span>（续）

如果第一次尝试回答的问题答错了，问答测验就提前终止，也就是说，此人**不允许再尝试回答第二道题**（is not allowed to attempt the second question）。

答案并不显而易见，因为这里存在一个权衡（tradeoff）：先试着回答更<mark>难</mark>但奖励更高的问题，一旦答对可获得更高奖励，但答对的概率更低；反之，先回答较简单的问题虽然成功概率更高，但随后仍有机会去争取更高的奖励。因此我们就把奖励金额 $X$ 视为一个**随机变量**（as a random variable），并针对两种策略分别计算 $X$ 的**期望值**（expected value）$E[X]$（cf. 图 2.9）：

---

**策略 (a)：先回答第 1 题。** 此时 $X$ 的概率质量函数（PMF, probability mass function）由下式给出（cf. 图 2.9 的左半部分）：

<span style="color:#00838f;">$X$ 取 0 元（第 1 题答错，测验以此终止）：</span>

```math
p_X(0) = 0.2,
```

<span style="color:#00838f;">$X$ 取 100 元（第 1 题答对、第 2 题答错）：</span>

```math
p_X(100) = 0.8 \cdot 0.5,
```

<span style="color:#00838f;">$X$ 取 300 元（两道题都答对）：</span>

```math
p_X(300) = 0.8 \cdot 0.5,
```

于是我们得到

```math
E[X] = 0.8 \cdot 0.5 \cdot 100 + 0.8 \cdot 0.5 \cdot 300 = \$160.
```

---

**策略 (b)：先回答第 2 题。** 此时 $X$ 的概率质量函数为（cf. 图 2.9 的右半部分）：

<span style="color:#00838f;">$X$ 取 0 元（第 2 题答错，测验以此终止）：</span>

```math
p_X(0) = 0.5,
```

<span style="color:#00838f;">$X$ 取 200 元（第 2 题答对、第 1 题答错）：</span>

```math
p_X(200) = 0.5 \cdot 0.2,
```

<span style="color:#00838f;">$X$ 取 300 元（两道题都答对）：</span>

```math
p_X(300) = 0.5 \cdot 0.8,
```

于是我们得到

```math
E[X] = 0.5 \cdot 0.2 \cdot 200 + 0.5 \cdot 0.8 \cdot 300 = \$140.
```

由于策略 (a) 下的期望奖励更高，因此先回答第 1 题是更优的策略（preferred strategy）。

---

<span style="color:#7f8c8d;">**Figure 2.9: Sequential description of the sample space of the quiz problem**（图 2.9：问答问题样本空间的序列化描述，sequential description）</span>

<!-- ===== PDF p102 ===== -->
# <span style="color:#c0392b;">第 2 章 离散型随机变量（Discrete Random Variables）</span>

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#c0392b;">答 题 得 奖 例 子 的 收 尾 与 推 广</span>

因此，最好先尝试较简单的那道题。

现在我们来推广这个分析。设 $P_1$ 与 $P_2$ 分别为正确回答第 1、2 两题的概率，并设 $V_1$ 与 $V_2$ 为与之对应的奖品（prize）价值。如果先回答第 1 题，我们有

```math
E_1 = P_1 V_1 + P_1 P_2 V_2 = P_1 \bigl( V_1 + P_2 V_2 \bigr),
```

而如果先回答第 2 题，我们有

```math
E_2 = P_2 V_2 + P_2 P_1 V_1 = P_2 \bigl( V_2 + P_1 V_1 \bigr).
```

由此可见，当且仅当

```math
\frac{P_1 V_1}{1 - P_1} \; > \; \frac{P_2 V_2}{1 - P_2}
```

时，先回答第 1 题才是最优的。

因此，最优的做法是**按照表达式 $P V/(1 - P)$ 递减的顺序**来排列各题；对于一个正确回答概率为 $P$、价值为 $V$ 的题目而言，这个表达式恰好提供了一种便捷的"品质指标"（index of quality）。有趣的是，这一规则可以推广到多于两题的情形（见章末习题）。

> <span style="color:#1e8449;">**[note] 译者注:**</span> 这里导师用一个数字 $E[X]$ 比较两种策略，背后其实是一次更底层的方法论选择：为什么用期望，而不是"最大可能奖励"或"最坏情况"。第一性原理是，期望在"重复试验取平均"的意义下度量单位投入的平均回报，它是可线性相加的标量，于是能把一整个随机结果压缩成一条可排序的数字；而"最大值"只盯着最好的分支、看不见概率权重，"最坏情形"又过度保守。你在 6.042J 的排序与博弈讨论里其实已见过同一动机：当结果不确定时，理性决策往往收敛于最大化某个"概率加权的收益"，而不是咬住一个极端分支。注意适用边界：期望适合"可以重复、越平均越稳"的场景；若你只能玩一次而且输不起，最坏情形或方差才是更合适的抓手——这正是本章后面引入方差的伏笔。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">2.5 多个随机变量的联合分布律（Joint PMFs of Multiple Random Variables）</span>

概率模型常常涉及多个随机变量（random variable）。例如，在医学诊断的情境（context）中，若干项检验（test）的结果可能具有重要意义；在网络的情境中，若干台路由器（router）的工作负载（workload）可能令人关注。所有这些随机变量都联系于同一个试验（experiment）、同一个样本空间（sample space）和同一条概率律（probability law），而它们的取值之间可能以有趣的方式相互关联。这促使我们去考虑那些**同时涉及多个随机变量**的事件的概率。在本节中，我们将把迄今所建立的分布律（PMF）与期望（expectation）的概念推广到多个随机变量。稍后，我们还会建立与第 1 章所讨论思想密切平行的条件作用（conditioning）与独立性（independence）的概念。

考虑两个与同一试验相联系（associated with the same experiment）的离散型随机变量 $X$ 与 $Y$。$X$ 与 $Y$ 所能取的各值的概率，由 $X$ 与 $Y$ 的联合分布律（joint PMF）刻画，记为 $P_{X,Y}$。

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">特别地，若 $(x,y)$ 是 $X$ 与 $Y$ 的一组可能取值（pair of possible values），那么这一组 $(x,y)$ 的概率质量（probability mass）就是事件 $\{X = x,\ Y = y\}$ 的概率：</span>

```math
P_{X,Y}(x, y) = P(X = x,\ Y = y).
```

在本文及别处，我们都使用缩写的记号 $P(X = x,\ Y = y)$，以取代更严格、更完整的写法 $P(\{X = x\} \cap \{Y = y\})$ 或 $P(X = x \text{ 且 } Y = y)$。

<!-- ===== PDF p103 ===== -->
<span style="color:#2471a3;">**[section]**</span> 第 2.5 节 多随机变量的联合概率质量函数（Joint PMFs of Multiple Random Variables） — 页 93

联合 PMF 决定了任何可用随机变量 $X$ 和 $Y$ 描述的**事件（event）**的概率。例如，若 $A$ 是全体具有某种性质的二元组 $(x,\,y)$ 所构成的集合，那么

```math
P\bigl((X,Y) \in A\bigr) = \sum_{(x,y)\in A} P_{X,Y}(x,y)\,.
```

事实上，我们还可以利用以下公式计算 $X$ 和 $Y$ 各自的概率质量函数：

```math
p_X(x) = \sum_y P_{X,Y}(x,y)\,,
```

```math
p_Y(y) = \sum_x P_{X,Y}(x,y)\,.
```

$p_X(x)$ 的公式可用如下计算加以验证：

```math
p_X(x) = P(X = x) = \sum_y P(X = x,\ Y = y)\,,
```

其中第二个等式成立是因为事件 $\{X = x\}$ 正是当 $y$ 遍历 $Y$ 的一切不同取值时，互不相交事件 $\{X = x,\ Y = y\}$ 之并。$p_Y(y)$ 的公式可类似地验证。我们有时把 $p_X$ 和 $p_Y$ 称为**边际概率质量函数（marginal PMF）**，以区别于联合 PMF。

我们可以用**表格法（tabular method）**由联合 PMF 计算边际 PMF。在这里，$X$ 与 $Y$ 的联合 PMF 排布在一张二维表中，$X$ 或 $Y$ 在某一给定取值处的边际 PMF 分别通过对表格中相应一列或一行的表项求和得到。该方法由下面的例子与图（Fig.）2.10 说明。

---

<span style="color:#2471a3;">**[example]**</span> **例 2.9（Example 2.9）**　　考虑两个随机变量 $X$ 和 $Y$，其联合 PMF 如图 2.10（Fig. 2.10）所示。边际 PMF 通过沿各列（对 $X$ 的边际 PMF）与沿各行（对 $Y$ 的边际 PMF）对表项求和而算出，正如图中所示。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**多随机变量的函数**</span>

当存在多个感兴趣的随机变量时，可以通过考虑涉及这些随机变量中若干者的**函数（function）**来生成新的随机变量。特别地，随机变量 $X$ 与 $Y$ 的某一函数 $Z = g(X, Y)$ 定义了另一个随机变量。其 PMF 可根据联合 PMF 依下式计算：

```math
p_Z(z) = \sum_{ \{(x,y)\,:\, g(x,y) = z\} } P_{X,Y}(x,y)\,.
```

<!-- ===== PDF p104 ===== -->
<span style="color:#2471a3;">**[本节接续]**</span> 2.5 相互独立下的多个随机变量&#160;§2.5&#160;Joint PMFs and their Marginals（联合 PMF 及其边缘分布）——本页为 **Example 2.9 的续接（PDF 续接自 103，内容跨至 105）**。

<span style="color:#2471a3;">**[OCR 残缺/图注提示]**</span> 本页顶部为 **Fig. 2.10** 图注区域（横轴为 $x$、纵轴为 $y$ 的坐标标注 `<span style="color:#7f8c8d;">[OCR 残缺]</span>`，为例 2.9 中联合 PMF 的联合分布图）。图中每个方格中的数字即表示 $\boldsymbol{p}_{X,Y}(x,y)$ 的取值。

---

## <span style="color:#c0392b;">2.5 联合 PMF 及其边缘分布（续）</span>

**计算某函数/边缘 PMF 的表格方法（method for calculating PMFs from the joint PMF table）：**

当 $X,Y$ 的联合 PMF $\boldsymbol{p}_{X,Y}(x,y)$ 以表格给出时，表中每个方格 `(x, y)` 的数字即给出 $\boldsymbol{p}_{X,Y}(x,y)$ 的值。

计算边缘 PMF（marginal PMF）$P_X(x)$：对给定的 $x$ 值，把表格中**对应 $x$ 的一列**的数字相加。对于任意 $y$ 值，则可得到 $P_Y(y)$。
同理，为计算 $P_Y(y)$：对给定的 $y$ 值，把表格中**对应 $y$ 的一行**的数字相加。
例如（for example）：

```math
P_X(2) = \frac{7}{20}
```

<span style="color:#7f8c8d;">[OCR 残缺：上式的中间若干分母项 $\frac{\cdot}{20}+\frac{\cdot}{20}+\cdots=\frac{7}{20}$ 未能清晰辨识；边缘求和中以列求和实现，其加和结果 $P_X(2)=7/20$ 可确认。]</span>

---

### <span style="color:#c0392b;">期望值法则（Expected Value Rule）用于函数的情形</span>

期望值法则（the expected value rule）对于函数的情形自然推广为如下形式：

```math
\boxed{\ \text{E}\big[g(X,Y)\big]=\sum_{x}\sum_{y} g(x,y)\,p_{X,Y}(x,y)\ }
```

**线性特殊情形（linear special case）：** 当 $g$ 具有形如 $aX+bY+c$ 的**线性（linear）**形式时，有：

```math
\text{E}[aX+bY+c]=a\,\text{E}[X]+b\,\text{E}[Y]+c
```

---

> <span style="color:#1e8449;">**[note] 译者注:**</span> 这一页把两个动作缝合在一起：由联合 PMF 沿列/沿行求和得到边缘 PMF $p_X,p_Y$，再对函数 $Z=g(X,Y)$ 用 $E[Z]=\sum_x\sum_y g(x,y)p_{X,Y}(x,y)$ 取期望。请把"按行/按列把表格全部项加总"命名成模板「表格边缘化求和」——它就是 6.042J 里多重求和的顺序重排，也是 Strang《18.065 矩阵》中"按列法与按行法得到同一总数"的离散版本：一张二维表就是联合分布，沿 $y$ 求和就坍缩回关于 $x$ 的一维分布。与 6.042J product-rule 的接通点在联合概率上：求 $\{X=x,Y=y\}$ 这类交事件的概率，正是"先按 $y$ 划分、再在每片内按规则累加"。要记住的分界是：边缘求和永远成立(因为 $\{X=x,Y=y\}$ 两两互斥)，而把它继续拆成更简单的乘积则要看独立性——那是下一节的引子。

### <span style="color:#c0392b;">例 2.9（续，Z=X+2Y）（Example 2.9, continued, Z=X+2Y）</span>

给定 $X$ 与 $Y$ 的联合 PMF（joint PMF）：其**联合分布表见图（Fig. 2.10）**，并考虑由此定义的一个**新随机变量（random variable）**

```math
Z=X+2Y
```

则 $Z$ 的 PMF $p_Z(z)$ 可通过遍历集合（the set）

```math
\{(x,y)\ \big|\ x+2y=z\}
```

将其中所有相应的联合概率 $p_{X,Y}(x,y)$ 求和而得到（<span style="color:#7f8c8d;">[OCR 残残缺]</span> 本页为 **Example 2.9（续）之开端**，具体求和运算与逐项结果续接至 PDF 第 105 页）。

<span style="color:#7f8c8d;">[OCR 残余提示]</span> 本页文字在 $p_Z(z)$ 求和的集合定义处断续，行末 "$Z$ 可取的 case / 对应的 $z$ 值分类" 等文字残缺，无法审定，故以续接方式标注。

<!-- ===== PDF p105 ===== -->
# <span style="color:#c0392b;">Discrete Random Variables（离散随机变量）— 第 2 章 · 第 95 页（接上页）</span>

<span style="color:#2471a3;">**[section]**</span> ## 2.5 多个随机变量的联合 PMF（Joint PMFs of Multiple Random Variables）

本页为 **Example 2.9（续）**（$Z = X + 2Y$）的**续接**——继续利用 Fig. 2.10 中的联合 PMF 计算 $Z$ 的 PMF 及其期望值；页末开启新小节「多于两个随机变量的情形」。

---

### <span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b">Example 2.9（续，Z=X+2Y）：compute the PMF and expectation of $Z$</span>

利用 Fig. 2.10 给出的 joint PMF（联合 PMF），我们有如下的 PMF 取值（denominator（分母）统一为 $20$）：

```math
\begin{aligned}
p_Z(3) &= \tfrac{1}{20}, & p_Z(4) &= \tfrac{1}{20}, & p_Z(5) &= \tfrac{2}{20}, \\
p_Z(6) &= \tfrac{2}{20}, & p_Z(7) &= \tfrac{4}{20}, & p_Z(8) &= \tfrac{3}{20}, \\
p_Z(9) &= \tfrac{3}{20}, & p_Z(10) &= \tfrac{2}{20}, & p_Z(11) &= \tfrac{1}{20}, \\
p_Z(12) &= \tfrac{1}{20}.
\end{aligned}
```

$Z$ 的期望值（expected value）可从其 PMF 直接求得：

```math
E[Z] = \sum_z z\,p_Z(z)
= 3\cdot\frac{1}{20} + 4\cdot\frac{1}{20} + 5\cdot\frac{2}{20} + 6\cdot\frac{2}{20} + 7\cdot\frac{4}{20}
+ 8\cdot\frac{3}{20} + 9\cdot\frac{3}{20} + 10\cdot\frac{2}{20} + 11\cdot\frac{1}{20} + 12\cdot\frac{1}{20}
= \frac{151}{20} = 7.55 \; .
```

若数值总和复算：$\big(3 + 4 + 10 + 12 + 28 + 24 + 27 + 20 + 11 + 12\big)/20 = 151/20$。

---

此外，我们也可以利用下述公式得到 $E[Z]$：

```math
E[Z] = E[X] + 2E[Y] \; .
```

由图 2.10 给出的 marginal PMFs（边缘 PMF / 边缘分布），我们有：

```math
E[Y] = 1\cdot\frac{3}{20} + 2\cdot\frac{7}{20} + 3\cdot\frac{7}{20} + 4\cdot\frac{3}{20} = \frac{50}{20} \; .
```

即边缘分布 $p_Y(y)$ 取值为 $\frac{3}{20},\frac{7}{20},\frac{7}{20},\frac{3}{20}$（对 $y = 1, 2, 3, 4$，总和为 $20$）。

<span style="color:#7f8c8d;">[OCR 残缺：$E[X]$ 表中式 $E[X] = 1\cdot p_X(1) + 2\cdot p_X(2) + 3\cdot p_X(3) + 4\cdot p_X(4)$ 右侧各分式分子在提取时错位（读到 $\frac{3}{20},\frac{8}{20},\frac{3}{20},\frac{6}{20}$ 之类，但其加权和与结果不符），无法一一核对；可确认的拼版结果（result）为 $E[X] = 51/20$。]</span>

```math
E[X] = \frac{51}{20} \; , \qquad E[Y] = \frac{50}{20} \; .
```

因此

```math
E[Z] = \frac{51}{20} + 2\cdot\frac{50}{20} = \frac{151}{20} = 7.55 \; .
```

此结果与前面对 $Z$ 的 PMF 直接求期望得到的一致，验证了期望的线性性质（linearity of expectation）。

---

### <span style="color:#2471a3;">**[section]**</span> More than Two Random Variables（多于两个随机变量的情形）

三个随机变量 $X, Y, Z$ 的 joint PMF（联合 PMF）的界定方式与上述情形完全类似（by analogy with the above）：

```math
p_{X,Y,Z}(x, y, z) = P(X = x,\; Y = y,\; Z = z),
```

对所有可能的数值三元组（all possible triplets of numerical values）$(x, y, z)$ 成立。相应的 marginal PMFs（边缘 PMF）也类似地由如下形式的等式得到：

```math
p_{X,Y}(x, y) = \sum_z p_{X,Y,Z}(x, y, z),
```

以及

```math
p_X(x) = \sum_y \sum_z p_{X,Y,Z}(x, y, z) \; .
```

> <span style="color:#7f8c8d;">[跨页续接：本页在 $p_X(x) = \sum_y \sum_z p_{X,Y,Z}(x, y, \cdot)$ 求和式处截断，后续关于「三变量及以上情形」的展开（含函数期望值法则推广）续接至 PDF 第 96 页。]</span>

<!-- ===== PDF p106 ===== -->
# <span style="color:#c0392b;">Discrete Random Variables（离散随机变量）— 第 2 章 · 第 96 页（接上页）</span>

<span style="color:#2471a3;">**[公式规则]**</span> 关于函数的期望值规则（期望规则，expected value rule for functions）由下式给出：

```math
E[g(X, Y, Z)] = \sum_x \sum_y \sum_z g(x, y, z)\, p_{X, Y, Z}(x, y, z)
```

若 $g$ 是线性函数（linear），且具有形式：

```math
g(x, y, z) = ax + by + cz + d
```

那么

```math
E[aX + bY + cZ + d] = aE[X] + bE[Y] + cE[Z] + d \, .
```

此外，上述结论可自然地推广到超过三个随机变量的情形。例如，对任意随机变量 $X_1, X_2, \ldots, X_n$ 和任意标量（scalars）$a_1, a_2, \ldots, a_n$，我们有：

```math
E\!\left[\sum_{i=1}^{n} a_i X_i\right] = \sum_{i=1}^{n} a_i E[X_i] \, .
```

---

> <span style="color:#1e8449;">**[note] 译者注:**</span> $E\big[\sum_{i=1}^{n}a_iX_i\big]=\sum a_iE[X_i]$ 是整章"最危险又最强大"的一条性质，因为它**不需要 $X_i$ 相互独立**。第一性原理是：期望本质是一个"把每个结果乘以概率再加总"的线性算子，求和号与系数 $a_i$ 都能直接穿进内层累加里交换次序，而这个交换只用到加法交换/结合律，和 $X_i$ 之间是否有关、有多少关联毫无关系。你可以用 CSAPP 的思维来锚定：把每个 $X_i$ 看作一个"带权随机贡献"、把 $E$ 看作一个线性累加器，只要累加器对每个分量分别记账，总账就等于各分账之和；依赖结构只改动"波动"(联合分布)，不碰"账本合计"。这与下一节的方差形成鲜明对照——均值恒可线性叠加，而 $var(\sum X_i)$ 必须具备独立性。6.006(CLRS) 里无数随机化分析(如线性搜索期望次数、快排期望复杂度)其实都在反复调用这一条。

<span style="color:#2471a3;">**[例]**</span> <span style="color:#c0392b;">**Example 2.10. Mean of the Binomial（二项分布的均值）.**</span> 你的概率班有 300 名学生（students），每名学生以概率 $1/3$ 获得 A，且与其他任何学生相互独立。设 $X$ 为获得 A 的学生人数（number of students that get an A），问 $X$ 的均值（mean）是多少？记

```math
X_i = \begin{cases} 1, & \text{若第 } i \text{ 名学生获得 A，}\\ 0, & \text{否则。} \end{cases}
```

于是 $X_1, X_2, \ldots, X_n$ 是以公共均值 $p = 1/3$ 的伯努利随机变量（Bernoulli random variables）。它们的和

```math
X = X_1 + X_2 + \cdots + X_n
```

即为获得 A 的学生人数。由于 $X$ 是 $n$ 次独立试验（independent trials）中“成功”（successes）的次数，因此它是参数为 $n$ 和 $p$ 的二项随机变量（binomial random variable）。利用 $X$ 作为 $X_i$ 之和的线性性质（linearity），我们有

```math
E[X] = \sum_{i=1}^{300} E[X_i] = \sum_{i=1}^{300} \frac{1}{3} = 300 \cdot \frac{1}{3} = 100 .
```

若将同样的计算推广到一般的学生人数 $n$ 和等于 $p$ 的获得 A 的概率，我们得到

```math
E[X] = \sum_{i=1}^{n} E[X_i] = \sum_{i=1}^{n} p = np .
```

---

<span style="color:#2471a3;">**[例]**</span> <span style="color:#c0392b;">**Example 2.11. The Hat Problem（帽子问题）.**</span> 假设 $n$ 个人把帽子都扔进一个盒子里，然后每人随机拿取一顶帽子（Each hat can be picked by only one person，每顶帽子只能被一个人拿走；且每个帽子到人的分配等可能）。设 $X$ 为拿回自己帽子的人数（number of people that get back their own hat），问 $X$ 的期望值（expected value）是多少？

对第 $i$ 个人，我们引入一个随机变量 $X_i$，当此人选回/拿到自己的帽子时取值 1，否则取值 0。由于 $P(X_i = 1) = 1/n$ 且 $P(X_i = 0) = 1 - 1/n$，故 $X_i$ 的均值为

```math
E[X_i] = 1 \cdot \frac{1}{n} + 0 \cdot \left(1 - \frac{1}{n}\right) = \frac{1}{n} .
```

<!-- ===== PDF p107 ===== -->
# <span style="color:#c0392b;">97</span>

> 承接上一页的例题（指示随机变量 indicator random variables 的应用）：
>
> 现在我们得到
>
> ```math
> E[X] = E[X_1] + E[X_2] + \cdots + E[X_n] = n \cdot \frac{1}{n} = 1 .
> ```

---

> <span style="color:#1e8449;">**[note] 译者注:**</span> 帽子问题把"拿回自己帽子的人数 $X$"拆成 $n$ 个最简单的伯努利指示变量 $X_i$(第 $i$ 人拿回帽子则取 1)，再用期望线性性 $E[X]=\sum E[X_i]=n\cdot\tfrac{1}{n}=1$ 一笔算毕。请把「指示随机变量法(Indicator Trick)」当作一条命名模板背下来：凡是"计数型"随机变量，几乎总能写成一系列取值 0/1 的指示变量之和，于是期望退化为把各"命中概率"相加，而 $E[X_i]$ 又等于单点概率 $P(X_i=1)$。这里的诀窍是：要找期望，只需单个事件概率 $1/n$，根本不用碰"至少一人拿回自己帽子"这类带依赖的联合事件，正是线性性让我们绕开了相关性。CSAPP 的随机化与 6.006 的算法分析里这是家常便饭——分析哈希表期望冲突数、随机化快排交换次数，本质都在重复这一招。

# <span style="color:#c0392b;">关于联合 PMF 的事实小结（Summary of Facts About Joint PMFs）</span>

<span style="color:#2471a3;">**[定义/说明]**</span>
设 $X$ 和 $Y$ 是与同一个实验（experiment）相关联的随机变量（random variables）。$X$ 与 $Y$ 的联合 PMF（joint PMF）$p_{X,Y}$ 定义为

```math
p_{X,Y}(x,\, y) = P(X = x,\ Y = y).
```

- $X$ 与 $Y$ 的边缘 PMF（marginal PMFs）可由联合 PMF 通过如下公式求得：

```math
p_X(x) = \sum_y p_{X,Y}(x,\, y), \qquad
p_Y(y) = \sum_x p_{X,Y}(x,\, y).
```

- $X$ 与 $Y$ 的函数 $g(X, Y)$ 定义了另一个随机变量（another random variable），且

```math
E\big[\,g(X, Y)\,\big] = \sum_x \sum_y g(x,\, y)\, p_{X,Y}(x,\, y).
```

- 若 $g$ 是线性的（linear），形如 $aX + bY + c$，则

```math
E\big[\,aX + bY + c\,\big] = a\,E[X] + b\,E[Y] + c.
```

- 以上结论当涉及两个以上的随机变量时，均有自然的推广（natural extensions）。

---

# <span style="color:#c0392b;">2.6 条件作用（CONDITIONING）</span>

与我们在第 1 章的讨论类似，条件概率（conditional probabilities）可用于捕获各类事件（events）关于某随机变量各可能取值所传达的信息。由此我们自然而然引入条件 PMF（conditional PMFs），即针对某一特定事件发生、或针对另一个随机变量取某给定值的情形。在本节中，我们将发展这一思想，并讨论条件 PMF 的性质。实际上，其中并没有多少全新的内容，只是对第 1 章已熟悉的诸多概念做进一步的阐述（elaboration），并引入一些新的记号（notation）。

<!-- ===== PDF p108 ===== -->
# <span style="color:#c0392b;">Discrete Random Variables（离散随机变量）</span>

## <span style="color:#c0392b;">Conditioning a Random Variable on an Event（对事件条件下的随机变量条件化）</span>

随机变量 $X$ 在特定事件 $A$（其中 $P(A)>0$）下的**条件分布列**（conditional PMF）由下式定义：

```math
P_{X\mid A}(x)=P(X=x \mid A)=\frac{P(\{X=x\}\cap A)}{P(A)}.
```

注意，对不同取值 $x$，事件 $\{X=x\}\cap A$ 是互不相交的，它们的并集为 $A$，因此

```math
P(A)=\sum_{x} P(\{X=x\}\cap A).
```

将上面两式结合，我们看到 $P_{X\mid A}$ 是一个**合法的分布列**（legitimate PMF）。

条件分布列的计算与其无条件情形相似：要求得 $P_{X\mid A}(x)$，我们把导致 $X=x$ 且属于条件事件 $A$ 的那些结果概率相加，然后除以 $P(A)$ 进行**归一化**（normalize）。

---

<span style="color:#2471a3;">**[Example 例题 2.12]**</span>

**单次掷出偶数面（例 2.12，原文为英文）**

掷一枚均匀的六面骰子，设 $X$ 为掷出的点数，设 $A$ 为事件「掷出的点数为偶数」。则由上述公式可得：

```math
P_{X\mid A}(k)=P(X=k\mid \text{roll is even})=\frac{P(X=k\text{ and }X\text{ is even）}}{P(\text{roll is even})}
```

即

```math
P_{X\mid A}(k)=
\begin{cases}
1/3, & \text{if } k=2,\,4,\,6,\\
0, & \text{otherwise}.
\end{cases}
```

---

<span style="color:#2471a3;">**[Example 例题 2.13]**</span>

**重复参加考试（例 2.13，原文为英文）**

一名学生将反复参加某次考试，最多可参加 $n$ 次，每次通过的概率为 $p$，且与之前的尝试次数独立。已知该学生通过了考试，求所需尝试次数的分布列（PMF）。

设 $A$ 为事件「该学生通过了考试」（在至多 $n$ 次尝试内）。我们引入随机变量 $X$，它表示在允许无限次尝试的情况下所需的尝试次数。于是 $X$ 是参数为 $p$ 的**几何随机变量**（geometric random variable），且 $A=\{X\le n\}$。我们有

```math
P(A)=\sum_{m=1}^{n}(1-p)^{m-1}p.
```

---

<span style="color:#7f8c8d;">[OCR 残缺：本页末尾的求和与推导在原文 OCR 中字符错乱，已按几何分布求和语义还原；公式部分字符无法辨认处未臆造。例 2.13 的求解（对 $P_{X\mid A}$ 的归一化）延续至下一页。]</span>

<!-- ===== PDF p109 ===== -->
# <span style="color:#c0392b;">Discrete Random Variables（离散随机变量）</span>

## <span style="color:#c0392b;">对事件条件下的随机变量条件化（续 Example 2.13，p.109）</span>

---

<span style="color:#2471a3;">**[figure]**</span> <span style="color:#c0392b">**Fig. 2.11**</span>

> <span style="color:#7f8c8d;">Bertsekas & Tsitsiklis, §2.4, p.109</span>

**图 2.11：条件分布列 $p_{X\mid A}$ 的 Visualization（可视化）与 calculation（计算）。**

我们沿用连续上一页的 Example（例题）2.13。我们从 $X$ 的分布列（PMF）出发，将不属于条件事件 $A$ 的所有 $k$ 所对应的 PMF 取值**设为 $0$**（set to zero），然后用 $P(A)$ 对这些取值进行 **归一化**（normalize），从而得到条件分布列（conditional PMF）：

```math
p_{X\mid A}(k) =
\begin{cases}
\ldots, & \text{if } k=1,\ldots,12,\\
\ldots, & \text{otherwise}.
\end{cases}
```

<span style="color:#7f8c8d;">[OCR 残缺：原图中该分段函数在 $k=1,\ldots,12$ 与 otherwise 时的具体取值因字符错乱无法辨认，此处未臆造，仅保留可辨识的取值域与分界结构 $k=1,\ldots,12$。]</span>

---

<span style="color:#2471a3;">**[figure]**</span> <span style="color:#c0392b">**Fig. 2.12**</span>

> <span style="color:#7f8c8d;">Bertsekas & Tsitsiklis, §2.4, p.109</span>

**图 2.12：条件分布列 $p_{X\mid A}(x)$ 的 Visualization（可视化）与 calculation（计算）。**

对于每个 $x$，我们把落在交集 $\{X=x\}\cap A$ 中那些结果的概率**相加**（add），再用 $P(A)$ 进行 **归一化**（normalize）：

```math
p_{X\mid A}(x) = \frac{\sum_{\text{outcomes in }\{X=x\}\cap A} P(\text{outcome})}{P(A)}.
```

> 两种视角（图 2.11 的「置零 + 归一化」与图 2.12 的「交集切片求和 + 归一化」）在数学上等价，都源自定义式 $p_{X\mid A}(x)=P(\{X=x\}\cap A)/P(A)$ 的直接演绎。

<span style="color:#7f8c8d;">[OCR 残缺：图 2.12 下方用于标注具体概率数值的坐标轴刻度行（原文形如 "JI." '-' Jl... 的一行）在图片 OCR 中完全乱码，无法还原，故外部数值轴未予转录。]</span>

---

## <span style="color:#c0392b;">在观测到另一随机变量取值下的条件化（Conditioning on a Random Variable）</span>

<span style="color:#2471a3;">**[section]**</span>

在许多情况下，我们并不精确知道随机变量（random variable）$X$ 的实现值，而只知道某**部分信息**（partial knowledge）——例如，我们可能对另一个随机变量 $Y$ 的取值有了局部的了解，即已知 $Y$ 落在了某个取值上（其满足 $p_Y(y)>0$）。这种知识（This knowledge）便由**条件分布列**（conditional PMF）……

<span style="color:#7f8c8d;">[OCR 残缺：本页结尾关于“该部分知识如何被条件分布列 $p_{X\mid Y}$ 捕获”的完整叙述在 OCR 中仅有零散单词（"is captured…"），句子不完整，故未臆造补全；内容继续衔接至下一页图 2.13（条件 PMF $p_{X\mid Y}(x\mid y)$ 的可视化）。]</span>

---

<span style="color:#7f8c8d;">[跨页续接：本节「在给定另一随机变量 $Y$ 的取值下求 $X$ 的条件分布」正式定义与公式见下一页（Fig. 2.13，第 110 页）。]</span>

<!-- ===== PDF p110 ===== -->
# <span style="color:#c0392b;">2.13 图：条件 PMF $P_{X\mid Y}(x\mid y)$ 的可视化</span>

<span style="color:#2471a3;">图注</span>

**Figure 2.13**: Visualization of the conditional PMF $P_{X\mid Y}(x\mid y)$ (图 2.13：条件 PMF $P_{X\mid Y}(x\mid y)$ 的可视化)。

For each $y$, we view the slice $Y = y$ and renormalize so that we obtain the conditional PMF $P_{X|Y}$ and its normalization equals $1$.

（对于每个 $y$，我们取切片 $Y = y$（the slice $Y=y$）并重新归一化（renormalize），从而得到条件 PMF $P_{X|Y}$，其归一化结果为 $1$。）

<span style="color:#7f8c8d;">[本页为插图页，正文 OCR 不可用]</span>

<!-- ===== PDF p111 ===== -->
# <span style="color:#c0392b;">Sec. 2.6 Conditioning（条件化）</span>

## <span style="color:#c0392b;">用序贯方法计算联合分布列（Joint PMF via the Sequential Approach）</span>

**条件分布列**（conditional PMF）在计算**联合分布列**（joint PMF）时往往很方便，可采用序贯（sequential）的方法，并利用如下公式：

```math
p_{X,Y}(x,y)=p_Y(y)\,p_{X\mid Y}(x\mid y),
```

或其对偶形式：

```math
p_{X,Y}(x,y)=p_X(x)\,p_{Y\mid X}(y\mid x).
```

该方法与第 1 章中**乘法规则**（multiplication rule）的用法完全类似。下面的例子给出说明。

---

> <span style="color:#1e8449;">**[note] 译者注:**</span> $p_{X,Y}(x,y)=p_Y(y)\,p_{X\mid Y}(x\mid y)$ 是把"条件的先后顺序"写进分布律里，本质就是 6.042J 中"先按条件分组、再在组内按比例分配"思想的随机变量版本。直觉读法是：先问 $Y=y$ 有多常见(权重 $p_Y(y)$)，再在"已知 $Y=y$"的切片内部，用 $p_{X\mid Y}(x\mid y)$ 这个在切片上已归一的分布去分配 $X$。这其实是第一章全概率定理的随机变量版：把样本空间按 $Y$ 的全部取值切分成互斥的片，再对各片加权求和 $p_X(x)=\sum_y p_Y(y)p_{X\mid Y}(x\mid y)$。命名成模板「给定条件的归一化」：在 $Y=y$ 的切片上"重新归一化"得到的 $p_{X\mid Y}$，在这个子集内部自行满足概率和为 1，与第一章序贯树状图中"分支权重×叶条件概率"的乘法规则完全同构。

<span style="color:#2471a3;">**[Example 例题 2.14]**</span>

**梅·B·赖特教授（Professor May B. Right）**

赖特教授经常把事实搞错，她对学生每个问题的回答都是错误的概率为 $1/4$，且与其他问题**相互独立**（independent）。在每节课中，赖特教授会被问到 $0$、$1$ 或 $2$ 个问题，概率相等，各为 $1/3$。设 $X$ 为赖特教授在某节课被问到的题目数，设 $Y$ 为该节课上她答错的题目数。为构造联合分布列 $p_{X,Y}(x,y)$，我们需要对 $x$ 与 $y$ 的各种取值组合计算概率 $P(X=x,\,Y=y)$。这可以通过对实验进行序贯描述并运用乘法规则来完成，如图 2.14 所示。例如，对于「被问到一道题且答错」的情形，我们有：

```math
p_{X,Y}(1,1)=p_X(x)\,p_{Y\mid X}(y\mid x)=\frac{1}{3}\cdot\frac{1}{4}=\frac{1}{12}.
```

联合分布列可用一个二维表格表示，如图 2.14 所示。它可用来计算任何感兴趣事件的概率。例如，我们有：

```math
P(\text{至少答错一道题})=p_{X,Y}(1,1)+p_{X,Y}(2,1)+p_{X,Y}(2,2)=\frac{1}{12}+\frac{6}{48}+\frac{1}{48}=\frac{4}{48}+\frac{6}{48}+\frac{1}{48}=\frac{11}{48}.
```

<span style="color:#2471a3;">图注</span> **Figure 2.14**: The joint PMF represented as a two-dimensional table（图 2.14：以二维表格表示的联合分布列，本页图内具体取值在原文 OCR 中未完整给出）。

<span style="color:#7f8c8d;">[本页无独立插图，图 2.14 为上文所述「二维表格」示意；表中各单元格数值由正文箭头文中的公式核对，'11/48' 结果按 $p_{X,Y}(1,1)=\frac{1}{12}=\frac{4}{48}$、$p_{X,Y}(2,1)=\frac{6}{48}$、$p_{X,Y}(2,2)=\frac{1}{48}$ 求和还原。]</span>

---

## <span style="color:#c0392b;">条件分布列与边缘分布列（Conditional PMF and Marginal PMFs）</span>

条件分布列也可用来计算**边缘分布列**（marginal PMFs）。特别地，利用定义可得：

```math
p_X(x)=\sum_{y}p_{X,Y}(x,y),\qquad p_Y(y)=\sum_{x}p_{X,Y}(x,y).
```

<span style="color:#7f8c8d;">[OCR 残缺：原文此处两行公式字符错乱（仅余两个孤立的 “y”），无法逐字符辨认；上方为边缘分布列的标准求和公式，系按语义词义还原，未臆造具体内容。]</span>

该公式提供了计算边缘分布列的一种**分而治之**（divide-and-conquer）方法。它在本质上与第 1 章给出的**全概率定理**（total probability theorem）相同，只是换用了不同的记号来表述。下面的例子给出说明。

---

<span style="color:#2471a3;">**[Example 例题 2.15]**</span>

**计算机网络上的消息传输时间（transmitter over a computer network）**

考虑一台在计算机网络中发送消息的**发射机**（transmitter）。我们定义如下两个随机变量：

- $X$：给定消息的**传输时间**（travel time）；
- $Y$：给定消息的**长度**（length）。

我们知道具有给定长度的消息其传输时间的分布列，也知道消息长度的分布列。我们想要找到消息传输时间的（无条件的）分布列（the (unconditional) PMF of the travel time of a message）。

<span style="color:#7f8c8d;">[本页结尾处：例 2.15 的求解（所谓「无条件」分布列即用前一节的边缘求和公式求得 $p_X$）延续至下一页。]</span>

<!-- ===== PDF p112 ===== -->
## <span style="color:#c0392b;">2.6 条件（Conditioning）—— 例 2.15（续）</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b">**Example 2.15（例 2.15，续）**</span>

（本页为例 2.15 的续页，讨论给定另一随机变量 $Y$ 时随机变量 $X$ 的条件计算。OCR 文本损坏严重，以下仅还原可辨识的叙述与公式，无法辨认的表述以灰色［OCR 残缺］标注，不臆造。）

---

…这里考虑的是 joint PMF（联合 PMF）$p_{X,Y}(x,y)$ 在 $Y=y$ 的切片下条件概率的运用。网络在传输时刻存在 congestion（拥塞）……<span style="color:#7f8c8d;">[OCR 残缺]</span> 具体而言，及 travel time（传输时间/旅行时间）……

——给定 $Y=y$ 时，$X$ 取 $y$ seconds 的概率为 $1/2$，取 $10^{-3}y$ seconds 的概率为 $1/3$，以及……<span style="color:#7f8c8d;">[OCR 残缺]</span> 我们使用 total probability formula（全概率公式）得到如下结果。

---

给出 $Y$ 的 marginal PMF（边缘 PMF）：

```math
p_{Y}(y)=
\begin{cases}
1/6, & \text{if } y=10^{-2},\\[2pt]
1/3, & \text{if } y=1,\\[2pt]
1/2, & \text{if } y=100.
\end{cases}
```

（核验：$\tfrac16+\tfrac13+\tfrac12 = \tfrac16+\tfrac26+\tfrac36=1$，概率归一正确。）

条件 PMF <span style="color:#7f8c8d;">[OCR 残缺]</span>

```math
p_{X\mid Y}(x\mid y)=
\begin{cases}
1/3, & \text{if } \ldots\\[2pt]
1/6, & \text{if } x=1,\\[2pt]
\ldots, & \text{if } x=10,\\[2pt]
1/2, & \text{if } x=100,
\end{cases}
```

（其中条件取值的组合方式及 $X=10^{-2}$、$X=10$ 的对应项因 OCR 残缺无法完全还原，见下页核对。）

---

由 total probability formula（全概率公式）逐值计算 $X$ 的 marginal PMF $p_X$：

```math
p_X(10^{-2})=\frac{1}{6}\cdot\frac{1}{2},
```

```math
p_X(10)=\frac{1}{6}\cdot\frac{1}{3},
```

```math
p_X(1)=\frac{1}{6}\cdot\frac{1}{2}+\frac{1}{3}\cdot\frac{1}{3}+\ldots,
```

```math
p_X(100)=\frac{1}{6}\cdot\frac{1}{6}+\ldots
```

<span style="color:#7f8c8d;">［OCR 残缺：本例中条件概率项的组合方式、中间因子的正确配对（哪一项来自哪个 $y$ 切片）以及各 $x$ 值的全部求和项未能可靠识别。上述公式中的数值均已按可见 OCR 逐字还原，未加臆造；建议比对原版 PDF 就该处推导做人工核对。］</span>

---

<span style="color:#7f8c8d;">[本页为中缝插图/公式密集页，OCR 极差，正文叙述缺失严重]</span>

<!-- ===== PDF p113 ===== -->
# <span style="color:#c0392b;">Sec. 2.6 Conditioning</span>

## <span style="color:#c0392b;">页 103</span>

我们最后指出，可以定义涉及**两个以上随机变量**的**条件 PMF**，例如 $p_{X,\,Y\mid Z}(x,\,y)$ 或 $p_{X\mid Y,\,Z}(x,\,y)$。上述概念与方法可以很容易地推广。

---

<hr style="border:none;border-top:1px solid #2471a3;margin:12px 0;"/>

<span style="color:#2471a3;">**[要点总结]**</span> **关于条件 PMF 的一些事实（Summary of Facts About Conditional PMFs）**

设 $X$ 与 $Y$ 是与同一**随机试验**（same experiment）相关联的随机变量。

- **条件 PMF** 与普通 PMF 相似，但适用于**条件事件已知发生**的那一"世界/母体"（universe）。

- 给定事件 $A$（且 $P(A)>0$）时，$X$ 的**条件 PMF** 定义为
  $p_{X\mid A}(x) = P(X=x \mid A)$，
  并且满足 [下面的边际公式]。

- 若 $A_1, \dots, A_n$ 是构成**样本空间**（sample space）的一个分割的**互不相交事件**，且对所有 $i$ 有 $P(A_i)>0$，则
  $p_X(x) = \sum_{i=1}^{n} P(A_i)\, p_{X\mid A_i}(x)$ 。
  （这是**全概率定理**（total probability theorem）的特例。）进一步地，对任何满足 $P(B_i)>0$（对所有 $i$）的事件 $B$，我们有
  $p_{X\mid B}(x) = \sum_{i=1}^{n} P(A_i \mid B)\, p_{X\mid A_i\cap B}(x)$ 。

- 给定 $Y=y$ 时 $X$ 的**条件 PMF** 与**联合 PMF** 由下式联系：
  $p_{X,Y}(x,y) = p_Y(y)\, p_{X\mid Y}(x \mid y)$ 。

- $X$ 给定 $Y$ 的**条件 PMF** 可用来通过下式计算 $X$ 的**边际 PMF**：
  $p_X(x) = \sum_{y} p_Y(y)\, p_{X\mid Y}(x \mid y)$ 。

- 上述结论有涉及**两个以上随机变量**的自然推广。

---

<!-- ===== PDF p114 ===== -->
## <span style="color:#c0392b;">第 2 章 离散随机变量（Discrete Random Variables）· 标称页 104</span>

---

### <span style="color:#c0392b;">条件期望（Conditional Expectation）</span>

一种条件概率质量函数（conditional PMF，即 conditional probability mass function）可以被视作某个由条件事件（conditioning event）所确定的新宇宙（universe）上的普通概率质量函数。同理，条件期望（conditional expectation）与普通期望（expectation）含义相同，只是它指向这个新宇宙，且所有概率与概率质量函数（PMF）都被替换为其条件对应版本。

（条件方差（conditional variance）亦可以类似方式处理。）下面列出主要的定义及相关事实。

---

<span style="color:#2471a3">要点归纳</span>：关于条件期望的要点归纳（Summary of Facts About Conditional Expectations）

设 $X$ 与 $Y$ 为与同一试验相关的随机变量（random variables）。

- 对满足 $P(A) > 0$ 的事件 $A$，给定 $A$ 时 $X$ 的条件期望（conditional expectation）定义为：

```math
E[X \mid A] = \sum_{x} x\, p_{X \mid A}(x)
```

- 对于某个函数 $g(X)$，我们有：

```math
E[g(X) \mid A] = \sum_{x} g(x)\, p_{X \mid A}(x)
```

- 给定 $Y$ 的某个取值 $y$ 时，$X$ 的条件期望定义为：

```math
E[X \mid Y = y] = \sum_{x} x\, p_{X \mid Y}(x \mid y)
```

- 若 $A_1, \ldots, A_n$ 为互不相交的事件，对每个 $i$ 都有 $P(A_i) > 0$，且它们构成样本空间（sample space）的一个分割（partition），则：

```math
E[X] = \sum_{i=1}^{n} P(A_i)\, E[X \mid A_i]
```

- 此外，对任意满足对每个 $i$ 都有 $P(A_i \cap B) > 0$ 的事件 $B$，我们有：

```math
E[X \mid B] = \sum_{i=1}^{n} P(A_i \mid B)\, E[X \mid A_i \cap B]
```

- 我们有：

```math
E[X] = \sum_{y} p_Y(y)\, E[X \mid Y = y]
```

上述最后三个等式分别适用于不同情形，但本质上是等价的，并将被统称为全期望定理（total expectation theorem）……

> <span style="color:#1e8449;">**[note] 译者注:**</span> $E[X]=\sum_{i=1}^{n}P(A_i)\,E[X\mid A_i]$ 叫全期望定理(total expectation theorem)，它把第一章全概率定理里的"事件概率"原地升级成"数值期望"：把样本空间按互斥分割 $A_i$ 切块，再对每块的条件平均按块概率加权求和。请命名成模板「树状全期望」：把样本空间看成 $n$ 条树杈，每条杈上挂两块——权重 $P(A_i)$ 与叶子含量 $E[X\mid A_i]$，最后在树根汇成无条件期望。它与第一章贝叶斯公式一母同胞，区别只在累加的对象：贝叶斯累加的是"条件概率"，这里累加的是"条件期望"，度量对象从一个集合(事件)换成了一个函数($X$)。向前预告两点：第 4 章会把 $E[X\mid Y]$ 本身当作一个随机变量(条件期望的随机变量版)并推出 law of iterated expectation；而 LOTUS 则让你用 $X$ 的分布直接算 $E[g(X)]$，不必先去求 $g(X)$ 自己的分布。

<span style="color:#7f8c8d;">[跨页继续：此页末句截至「total expectation」，后接「theorem」及全期望定理正文应位于下一页]</span>

<!-- ===== PDF p115 ===== -->
# <span style="color:#c0392b;">Sec. 2.6 Conditioning（条件作用 / 条件概率）</span>

<页面续接前文 total expectation theorem（全期望定理）>

> <span style="color:#7f8c8d;">Bertsekas & Tsitsiklis, *Introduction to Probability, 2nd ed.* §2.6, p.105</span>

---

<span style="color:#2471a3;">**[theorem]**</span> 上文所述 **total expectation theorem（全期望定理）** 的三条等式都可由 **total probability theorem（全概率定理）** 推得，它们表达的核心事实是：**"无条件平均值可以通过对条件平均值求平均来得到"**——也就是 *"the unconditional average can be obtained by averaging the conditional averages"*。这些等式可用于一种 **divide-and-conquer（分而治之）** 的思路，通过条件 PMF 或期望来计算无条件期望 $\mathrm{E}[X]$。

为验证三条等式中的第一条，我们写出

```math
p_X(x) = \sum_{i=1}^{n} P(A_i)\, p_{X \mid A_i}(x),
```

两边同时乘以 $x$，并对所有 $x$ 求和：

```math
\mathrm{E}[X]
= \sum_x x\, p_X(x)
= \sum_{i=1}^{n} P(A_i)\, \mathrm{E}[X \mid A_i].
```

<span style="color:#2471a3;">**[proof]**</span> 其余两条等式同理可证（*the remaining two equalities are verified similarly*）。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">**Example 2.16（例 2.16）—— 传输时延的平均值**</span>

一台位于 Boston（波士顿）的计算机通过数据网络发送消息，这些消息以概率 $0.5$ 发往 New York（纽约）、以概率 $0.3$ 发往 Chicago（芝加哥）、以概率 $0.2$ 发往 San Francisco（旧金山）。消息的 **transit time（传输时间）** $X$ 是随机的。若目的地是纽约，其均值（mean）为 $0.05$ 秒；若目的地是芝加哥，均值为 $0.1$ 秒；若目的地是旧金山，均值为 $0.3$ 秒。于是利用 **total expectation theorem（全期望定理）** 即可轻松算得 $\mathrm{E}[X]$：

```math
\mathrm{E}[X] = 0.5 \cdot 0.05 + 0.3 \cdot 0.1 + 0.2 \cdot 0.3 = 0.115 \ \text{秒}.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">**Example 2.17（例 2.17）—— 几何分布的均值与方差（Mean and Variance of the Geometric）**</span>

<span style="color:#2471a3;">**[note]**</span> *Question（问题）：* 你反复编写一个软件程序，每次尝试都以概率 $p$ 使其正确运行，且各次尝试相互独立（independent of previous attempts）。求 $X$（直到程序首次正确运行所需的尝试次数）的均值与方差是多大？

我们识别出 $X$ 是一个 **geometric random variable（几何随机变量）**，其 PMF 为

```math
p_X(k) = (1-p)^{k-1} p, \qquad k = 1, 2, \ldots
```

<span style="color:#2471a3;">**[note]**</span> $X$ 的均值与方差由下式给出：

```math
\mathrm{E}[X] = \sum_{k=1}^{\infty} k (1-p)^{k-1} p,
```

```math
\mathrm{var}(X) = \sum_{k=1}^{\infty} \bigl(k - \mathrm{E}[X]\bigr)^2 (1-p)^{k-1} p.
```

<br/>

<此后为下一页内容——利用几何级数级数求和技巧分别计算上述无穷级数。>

<!-- ===== PDF p116 ===== -->
# <span style="color:#c0392b;">Discrete Random Variables（离散随机变量）</span>

<span style="color:#7f8c8d;">〔接上页：几何分布的期望与方差计算〕</span>

但是逐一计算这些无穷和稍显繁琐。作为一种替代方案，我们将应用<span style="color:#2471a3;">全期望定理（total expectation theorem）</span>，令 $A_1 = \{X = 1\} = \{\text{第一次尝试成功}\}$，$A_2 = \{X > 1\} = \{\text{第一次尝试失败}\}$，从而得到一个远为简单的计算。

如果第一次尝试成功，则有 $X = 1$，且

```math
E[X \mid X = 1] = 1.
```

如果第一次尝试失败（$X > 1$），我们浪费了一次尝试，并回到了初始状态。因此，剩余尝试次数的期望为 $E[X]$，于是

```math
E[X \mid X > 1] = 1 + E[X].
```

由此，

```math
E[X] = P(X = 1)\,E[X \mid X = 1] + P(X > 1)\,E[X \mid X > 1]
```

```math
= p + (1 - p)(1 + E[X]),
```

据此我们得到

```math
E[X] = \frac{1}{p}.
```

用类似的推理，我们还有

```math
E[X^2 \mid X = 1] = 1,
```

并且 $E[X^2 \mid X > 1] = E[(1 + X)^2]$，从而由此得到

```math
E[X^2] = \frac{1 + 2(1 - p)E[X]}{p},
```

再利用上面导出的公式 $E[X] = 1/p$，可得

```math
E[X^2] = \frac{2 - p}{p^2}.
```

我们得出结论

```math
\operatorname{var}(X) = E[X^2] - (E[X])^2 = \frac{2 - p}{p^2} - \frac{1}{p^2} = \frac{1 - p}{p^2}.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">例题 2.18 两个信封悖论（The Two-Envelopes Paradox）</span> 这是一个被广泛讨论的谜题，其中涉及一个关于条件期望的微妙数学要点。有人递给你两个信封，并告诉你其中一个里装着的钱是另一个信封的 $m$ 倍，其中 $m$ 是满足 $m > 1$ 的整数。你打开其中一个信封，看到里面的金额。你现在可以选择保留这个金额，也可以切换信封并保留另一个信封里的金额。什么是最优策略？

<!-- ===== PDF p117 ===== -->
# <span style="color:#c0392b;">第 2 章 · 第 2.6 节 条件化（Conditioning）</span>

**Sec. 2.6** ｜ **页 107** ｜ **Conditioning（条件化）**

<span style="color:#2471a3;">**[例题：双信封悖论（The Two-Envelope Paradox）（续，跨页）]**</span>

---

下面是一条支持更换（switching）信封的推理思路。设 A 为你打开的信封，B 为你可能换到的信封；再设 x 与 y 分别为 A 与 B 中的金额（amounts）。于是，按这一论证的逻辑，要么 $y = x/m$，要么 $y = mx$，二者的概率各为 $1/2$，所以在给定 x 的条件下，y 的期望值（expected value）为

```math
E[Y \mid X = x]\;=\;\frac12\cdot\frac{x}{m}\;+\;\frac12\cdot mx\;=\;\frac{1+m^2}{2m}\,x\;>\;x
```

因为当 $m > 1$ 时，总有 $1+m^2 > 2m$。因此，你应当始终换到信封 B！

---

然而，既然无论 A 中的金额是多少你都应当更换，那么你不如一开始就打开 B；可一旦你打开 B，你又应当再次更换，如此循环不止……

支撑这一悖论式（paradoxical）推理的，是两个在某种程度上都有缺陷的假设（assumption）：

- (a) 你对信封中的金额没有任何先验知识（a priori knowledge），因此在给定 x 时，你对 y 所能知道的仅仅是它要么是 $x/m$、要么是 m 乘以 x，并且没有任何理由假定二者之一比另一个更可能。
- (b) 给定两个表示金额的随机变量（random variables）X 与 Y，若对 X 的所有可能取值 x 都有 $\mathbf{E}[Y \mid X = x] > x$，那么总是换到 Y 的策略（strategy）会带来更高的期望货币收益（expected monetary gain）。

让我们来仔细审视这两个假设。

---

假设 (a) 之所以有缺陷，是因为它依赖于一个未被完整指定的概率模型（probabilistic model）。事实上，在任何正确的模型中，所有事件——包括 X 与 Y 的可能取值——都必须具有定义良好（well-defined）的概率。一旦具备了关于 X 与 Y 的这种概率知识，X 的取值就可能揭示关于 Y 的大量信息。

例如，假设如下概率模型：某人按某种分布（distribution）从一个已知范围 $\left[\,\underline{z},\,z\,\right]$ 中选取一个整数美元金额 Z，将这一金额放入随机选定的一个信封，并在另一个信封中放入该金额的 m 倍。<span style="color:#7f8c8d;">[OCR 残缺：范围下界符号损坏，此处以 $\underline{z}$ 作复原，下界的具体写法因 OCR 无法辨认]</span>

然后你选择打开两个信封之一（概率相等），并查看其中封装的金额 X：

- 如果 X 结果大于范围上限（upper range limit）$z$，你就知道 X 是两个金额中较大的那一个，因此不应更换信封。
- 另一方面，对 X 的某些其他取值，例如范围下限（lower range limit）$\underline{z}$，你则应更换信封。

因此，在该模型中，是否更换信封的选择应当取决于 X 的取值。粗略地说，如果你对 X 取值的范围与似然（likelihood）有所了解，你便能判断 A 中的金额 X 相对较小还是相对较大，并据此决定更换或不更换信封。

---

从数学上看，在一个正确的概率模型中，我们必须拥有随机变量 X 与 Y（分别是信封 A 与 B 中的金额）的联合概率质量函数（joint PMF）。该联合 PMF 通过为随机变量 Z——即两个信封中金额的较小者——引入一个 PMF $p_Z$ 而给出。于是，对所有 z，有

```math
p_{X,Y}(mz,\, z)\;=\;p_{X,Y}(z,\, mz)\;=\;\tfrac12\,p_Z(z)\,,
```

并且

```math
p_{X,Y}(x,\, y)\;=\;0\,,
```

<span style="color:#7f8c8d;">[跨页：关于其余情形下联合 PMF 取零的说明及其推导延续至下一页]</span>

<!-- ===== PDF p118 ===== -->
# <span style="color:#c0392b;">离散随机变量 Discrete Random Variables</span>

<span style="color:#2471a3;">**续：信封悖论例（Conditional Expectation，条件期望）**</span>

对于每个不是形如 $(m^z\,,\,z)$ 或 $(z\,,\, m^z)$ 的 $(x, y)$，据此规定 $p_{X\mid Y}(x, y)$，并且在给定了 $X = x$ 的前提下，就可以用如下规则（rule）：

> **当且仅当** $\mathrm{E}[Y \mid X = x] > x$ **时才交换信封 switch。**

按照这一决策规则（decision rule），你可能交换也可能不交换信封，取决于 $X$ 的值，如前所述。

那么，在上述概率模型（probabilistic model）和决策规则下，是否应当对某些值 $x$ 交换、对另一些值 $x$ 不交换呢？通常是的，正如前面那个 $Z$ 在有界范围内取值的例子所示。

然而，这里有一个恶作剧般的例子（devilish example），由于一个微妙的数学怪癖（subtle mathematical quirk），你**总是会交换！**

---

掷一枚公平硬币（fair coin），直到出现正面为止。设 $N$ 为投掷次数。于是，一个信封中放入 $m^N$ 美元，另一个信封中放入 $m^{N-1}$ 美元。设 $X$ 为你打开的那个信封（信封 $A$）里的金额，$Y$ 为另一个信封（信封 $B$）里的金额。

现在，如果 $A$ 中包含 1 美元，显然 $B$ 中应该包含 $m$，所以你应该交换信封。另一方面，如果 $A$ 中包含 $m^n$ 美元，其中 $n > 0$，那么 $B$ 中要么包含 $m^{n-1}$ 要么包含 $m^{n+1}$ 美元。由于 $N$ 具有几何 PMF（geometric PMF，几何概率质量函数），我们有

```math
\frac{\mathrm{P}(Y = m^{n+1} \mid X = m^n)}{\mathrm{P}(Y = m^{n-1} \mid X = m^n)}
= \frac{\mathrm{P}(Y = m^{n+1},\, X = m^n)}{\mathrm{P}(Y = m^{n-1},\, X = m^n)}
= \frac{\mathrm{P}(N = n+1)}{\mathrm{P}(N = n)}
= \frac{1}{2}
```

因此

```math
\mathrm{P}(Y = m^{n+1} \mid X = m^n) = \frac{1}{3},
\qquad
\mathrm{P}(Y = m^{n-1} \mid X = m^n) = \frac{2}{3}
```

且有

```math
\mathrm{E}[\text{ 金额 } B \mid X = m^n] = \frac{1}{3} m^{n+1} + \frac{2}{3} m^{n-1}
= \frac{m^2 + 2}{3m}\, m^n
```

我们有：$(2 + m^2)/3m > 1$ 当且仅当 $m^2 - 3m + 2 > 0$，即 $(m-1)(m-2) > 0$。因此，如果 $m > 2$，则

```math
\mathrm{E}[\text{ 金额 }B \mid X = m^n] > m^n
```

即为了最大化期望货币收益（expected monetary gain），你应该**总是交换到 $B$！**

这个例子中发生的是：你之所以对所有值 $x$ 都交换，是因为

```math
\mathrm{E}[Y \mid X = x] > x
\qquad \text{对一切 }x \text{ 成立}
```

对全期望定理（total expectation theorem）的天真应用似乎会表明 $\mathrm{E}[Y] > \mathrm{E}[X]$。然而这不可能成立，因为 $X$ 与 $Y$ 具有相同的 PMF。相反，我们实际拥有的是

```math
\mathrm{E}[Y] = \mathrm{E}[X] = \infty
```

这与关系式 $\mathrm{E}[Y \mid X = x] > x$ 对一切 $x$ 成立并不必然矛盾。

结论是：**当且仅当** $\mathrm{E}[Y \mid X = x] > x$ **才交换**的这条决策规则，在 $\mathrm{E}[Y] = \mathrm{E}[X] = \infty$ 的情形下并不能改善期望货币收益，表面的悖论（paradox）就此化解。

> <span style="color:#1e8449;">**[note] 译者注:**</span> 悖论的裂纹不在"贪心交换"的逻辑推演，而在 $E[Y]=E[X]=\infty$ 这一行，它是第一性原理的一记重击：全期望定理"条件平均的加权和等于无条件平均"的直觉，只在所有相关期望有限时才站得住；一旦 $X,Y$ 的期望发散到无穷，"对一切 $x$ 都有 $E[Y\mid X=x]>x$"就不能再推出 $E[Y]>E[X]$。原因在于无穷情形下"平均"失去代表性，条件都开始各自为政。这正是你正在学的 100B 实分析"条件收敛对重排敏感"的一个概率投影：$\sum_k k(1-p)^{k-1}p$ 只有在绝对收敛时才能放心重排与加括号，而这里恰是它不绝对收敛的反例。它与早期"无穷对应"这类数论直觉的关键区别是：那讨论的是"能否比较"，而这讨论的是"在发散的分布上，期望这个工具本身失灵"。它和 St. Petersburg 悖论同源——重尾 / 期望无穷让"最大化期望"的人脑直觉脱钩。

---

<span style="color:#7f8c8d;">[OCR 残缺：页面底部页码/页眉信息无法辨认]</span>

<!-- ===== PDF p119 ===== -->
# <span style="color:#c0392b;">Sec. 2.7 Independence（独立性）</span>

<页面始自本章 2.7 节 "Independence（独立性）" 一节开头，印刷页 p.109>

> <span style="color:#7f8c8d;">Bertsekas & Tsitsiklis, *Introduction to Probability, 2nd ed.* §2.7, p.109</span>

---

我们下面讨论与随机变量相关的独立性概念（*concepts of independence related to random variables*）。这些概念与（参见 Chapter 1 第 1 章）诸事件之间的独立性概念相类似。它们的建立方法是：直接引入若干涉及各个随机变量可能取值的合适事件，并考虑这些事件的独立性（independence）。

---

## <span style="color:#c0392b;">随机变量与事件的独立性（Independence of a Random Variable from an Event）</span>

一个随机变量与一个事件的独立性，类似于两个事件之间的独立性。其核心思想是：**知道条件事件是否发生，不会为随机变量的取值提供任何新信息**（knowing the occurrence of the conditioning event provides no new information on the value of the random variable）。更形式化地说，我们称随机变量 $X$ 独立于事件 $A$（*the random variable $X$ is independent of the event $A$*），若对所有 $x$ 都有

```math
P(X = x,\ A) = P(X = x)\, P(A) = p_X(x)\, P(A),
```

这等同于要求：对任意 $x$ 的取值，两个事件 $\{X = x\}$ 与 $A$ 相互独立（independent）。由条件 PMF（conditional PMF）的定义，我们有

```math
P(X = x,\ A) = p_{X \mid A}(x)\, P(A),
```

因此，只要 $P(A) > 0$，独立性就等价于条件：对所有 $x$ 有

```math
p_{X \mid A}(x) = p_X(x).
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 2.19（例 2.19）**</span>

考虑一枚公平硬币的两次独立投掷（*two independent tosses of a fair coin*）。设 $X$ 为正面出现的次数，设 $A$ 为"出现正面的次数为偶数"这一事件。$X$ 的（无条件，unconditional）PMF 为

```math
p_X(x) =
\begin{cases}
1/4, & \text{if } x = 0,\\
1/2, & \text{if } x = 1,\\
1/4, & \text{if } x = 2,
\end{cases}
```

并且 $P(A) = 1/2$。条件 PMF 由定义 $p_{X \mid A}(x) = P(X = x\ \text{and}\ A)/P(A)$ 得到：

```math
p_{X \mid A}(x) =
\begin{cases}
1/2, & \text{if } x = 0,\\
0, &\text{if } x = 1,\\
1/2, & \text{if } x = 2.
\end{cases}
```

显然 $X$ 与 $A$ 并不独立，因为 PMF $p_X$ 与 $p_{X \mid A}$ 不同。为给出一个独立于 $A$ 的随机变量的例子，可考虑如下随机变量：若第一次投掷为正面，则该变量取值为 $0$；若第一次投掷为反面，则该变量取值为 $1$。这一结论凭直觉清晰可见，也可通过独立性的定义加以验证。

<!-- ===== PDF p120 ===== -->
<span style="color:#2471a3;">**Discrete Random Variables（离散随机变量）**</span> 　Chap. 2

---

### <span style="color:#c0392b;">随机变量的独立性（Independence of Random Variables）</span>

两个随机变量（random variables）的**独立性**（independence）概念，与“一个随机变量独立于某个事件”相类似。我们说两个随机变量 $X$ 与 $Y$ 是**独立的**（independent），如果

对于所有 $x,\,y$，有

```math
p_{X,Y}(x,y) = p_X(x)\, p_Y(y).
```

这等同于要求：对每一个 $x$ 和 $y$，事件 $\{X=x\}$ 与 $\{Y=y\}$ 是独立的。最后，公式

```math
p_{X,Y}(x,y) = p_{X\mid Y}(x\mid y)\, p_Y(y)
```

表明独立性等价于条件

```math
p_{X\mid Y}(x\mid y) = p_X(x),
```

即对于所有满足 $p_Y(y) > 0$ 的 $y$ 以及所有的 $x$ 都成立。

直观上，独立性（independence）意味着 $Y$ 的取值不提供关于 $X$ 取值的任何信息（provides no information on the value of $X$）。

---

### <span style="color:#c0392b;">条件独立性（Conditional Independence）</span>

在给定一个具有 $P(A) > 0$ 的事件 $A$ 的条件下，两个随机变量也存在类似的条件独立性（conditional independence）概念。条件事件 $A$ 定义了一个新的全集（new universe），所有概率（或 PMF）都必须换成其条件对应物（conditional counterparts）。例如，给定一个正概率事件 $A$，若

```math
P(X=x,\, Y=y \mid A) = P(X=x \mid A)\, P(Y=y \mid A),
```

对所有 $x$ 和 $y$ 成立，则称 $X$ 与 $Y$ 在 $A$ 给定下**条件独立**（conditionally independent）；或用本节的记号写作

```math
p_{X,Y\mid A}(x,y)=p_{X\mid A}(x)\,p_{Y\mid A}(y)
```

对于所有 $x$ 和 $y$，成立。

再一次地，这等价于

```math
p_{X\mid Y,A}(x\mid y)=p_{X\mid A}(x)
```

对于所有满足 $p_{Y\mid A}(y) > 0$ 的 $x$ 和 $y$，成立。

如同事件的情形（第 1.5 节）一样，条件独立性（conditional independence）不一定蕴含无条件独立性（unconditional independence），反之亦然。这一点由图 2.15（Fig. 2.15）中的例子加以说明。

---

### <span style="color:#c0392b;">独立随机变量的乘积期望（Expectation of Product of Independent Random Variables）</span>

如果 $X$ 与 $Y$ 是独立随机变量（independent random variables），则

```math
E[XY] = E[X]\, E[Y],
```

如下面的计算所示：

```math
E[XY] = \sum_x \sum_y xy\, p_{X,Y}(x, y)
```

```math
= \sum_x \sum_y xy\, p_X(x)\, p_Y(y) \qquad \text{（by independence，利用独立性）}
```

```math
= E[X]\, E[Y].
```

<!-- ===== PDF p121 ===== -->
# <span style="color:#c0392b;">第 2 章 离散随机变量（续）</span>

<span style="color:#2471a3;">**图 2.15**</span>

对于图中所示的一维边缘概率质量函数 join P M F **joint PMF（联合概率质量函数）**，随机变量 $X$ 与 $Y$ **不独立（not independent）**。例如，我们有

$P(X=1,\ Y=1) = 1/2 \neq p_X(1)\,p_Y(1) = 1/4$

的情形，说明二者不独立。

另一方面，在事件 $A=\{X \le 2,\ Y \ge 3\}$（图中**灰色阴影部分 shaded set（阴影集合）**）的条件下，可以看作随机变量 $X$ 与 $Y$ **条件独立（conditionally independent）**。

特别地，对两个值 $y = 3$ 与 $y = 4$ 均有

$p_{X \mid A}(x) = 1/3,\qquad x = 1, 2$

即给定事件 $A$ 后，$X$ 与 $Y$ 的条件分布相互独立。

---

<span style="color:#2471a3;">**性质 / 命题（条件独立与无条件独立的关系）**</span>

条件独立（conditional independence）**不一定蕴含（may not imply）**无条件独立（unconditional independence），反之亦然。

需要注意的是：若随机变量 $X$ 与 $Y$ **独立（independent）**，则对于任意函数 $g$ 与 $h$ 有

```math
E[g(X)\,h(Y)] = E[g(X)]\,E[h(Y)].
```

事实上，这一关系直观上显然成立（intuitively clear）：因为联合 PMF 可分解为各分量 PMF 之积，从而期望可拆成乘积。更一般地，一旦我们证明了两随机变量可交换性（interchangeability）的讨论，对一般函数 $g(X)$ 与 $h(Y)$ 同样成立。其完整证明留给读者作为练习（verification is left as an exercise）。

---

<span style="color:#2471a3;">**例题（相互独立随机变量之和的方差）**</span>

设 $X$ 与 $Y$ 相互独立，我们利用中心化技巧推导：

$\operatorname{var}(X + Y) = \operatorname{var}(X) + \operatorname{var}(Y).$

先引入**零均值（zero-mean）**变量：当随机变量被平移（shifted）一个常数时，方差保持不变，因此可设

$\tilde X = X - E[X], \qquad \tilde Y = Y - E[Y],$

其中 $\tilde X$ 与 $\tilde Y$ 仍相互独立。由于 $\tilde X$、$\tilde Y$ 均值为 0，$E[\tilde X+\tilde Y]=0$，故方差等于 $E[(\tilde X+\tilde Y)^2]$。于是

```math
\operatorname{var}(X+Y) = E[(X+Y)^2] - \bigl(E[X+Y]\bigr)^2 = E[(\tilde X + \tilde Y)^2] = E[\tilde X^2 + 2\tilde X \tilde Y + \tilde Y^2].
```

由于 $\tilde X$、$\tilde Y$ 相互独立且均为零均值，交叉项期望为零：

```math
E[\tilde X \tilde Y] = E[\tilde X]\,E[\tilde Y] = 0.
```

因此

```math
\operatorname{var}(X+Y) = E[\tilde X^2] + E[\tilde Y^2] = \operatorname{var}(X) + \operatorname{var}(Y).
```

即相互独立随机变量之和的方差等于各分量方差之和。

<!-- ===== PDF p122 ===== -->
# <span style="color:#c0392b;">第 2 章 离散随机变量（续）</span>

<span style="color:#2471a3;">**方差可加性的证明收尾（续上页）**</span>

我们已在上面使用了性质 $E[\tilde X \tilde Y] = 0$，其理由如下。随机变量 $\tilde X = X - E[X]$ 与 $\tilde Y = Y - E[Y]$ **相互独立（independent）**（因为它们是相互独立的随机变量 $X$ 与 $Y$ 的函数），并且它们又是**零均值（zero-mean）**的，于是我们得到

```math
E[\tilde X \tilde Y] = E[\tilde X]\,E[\tilde Y] = 0.
```

总之，两个相互独立随机变量的**和的方差（variance of the sum）**等于它们各自方差之和。一个有趣的对比值得注意：两个随机变量之和的**均值（mean）**总是等于它们均值之和，即使这两个随机变量**不独立（not independent）**也是如此。

> <span style="color:#1e8449;">**[note] 译者注:**</span> $var(X+Y)=var(X)+var(Y)$ 的证明全靠一个漂亮动作——「零均值中心化」：令 $\tilde X=X-E[X]$，它把期望归零而方差不变(平移不改散布)，于是交叉项 $E[\tilde X\tilde Y]$ 变成天然为零的量(因 $\tilde X,\tilde Y$ 独立又零均值，期望之积为 0)。请把「零均值中心化」存成模板：想看清一个量的"波动"，先扣掉期望只看偏离量，很多交叉效应立刻消失。务必盯紧它和均值的关键分歧：均值线性性永不需要独立性，而方差可加性**严格需要 $X_i$ 相互独立**——因为唯一的交叉修正项协方差 $cov$ 只有在独立时才是 0。对应统计直觉"方差分解"：一批独立误差的总方差是各单误差方差之和，所以把 $n$ 个独立测量取平均能把方差压到单次的 $1/n$。到第 6 章你会看到，正是这一条支撑着中心极限定理与弱大数定律的成型。

---

### 关于独立随机变量的若干事实总结 <span style="color:#7f8c8d;">（Summary of Facts About Independent Random Variables）</span>

设 $A$ 是一个事件，且 $P(A) > 0$，并设 $X$ 与 $Y$ 是与同一实验相关的随机变量。

- $X$ 独立于事件 $A$，当且仅当
  ```math
  p_{X \mid A}(x) = p_X(x), \qquad \text{对所有 } x,
  ```
  也就是说，若对任意 $x$，事件 $\{X = x\}$ 与 $A$ 均相互独立。

- $X$ 与 $Y$ 相互独立，如果对所有 pairs（有序对）$(x, y)$，事件 $\{X = x\}$ 与 $\{Y = y\}$ 均相互独立，或等价地
  ```math
  p_{X,Y}(x, y) = p_X(x)\,p_Y(y), \qquad \text{对所有 } x, y。
  ```

- 若 $X$ 与 $Y$ 是相互独立的随机变量，则
  ```math
  E[XY] = E[X]\,E[Y].
  ```
  更进一步，对任意函数 $g$ 与 $h$，随机变量 $g(X)$ 与 $h(Y)$ 相互独立，并且我们有
  ```math
  E\bigl[g(X)\,h(Y)\bigr] = E\bigl[g(X)\bigr]\,E\bigl[h(Y)\bigr].
  ```

- 若 $X$ 与 $Y$ 相互独立，则
  ```math
  \operatorname{var}(X + Y) = \operatorname{var}(X) + \operatorname{var}(Y).
  ```

---

### <span style="color:#c0392b">多个随机变量的独立性（Independence of Several Random Variables）</span>

前面的讨论可以自然地推广到多于两个随机变量的情形。例如，三个随机变量 $X$、$Y$ 与 $Z$ 被称为……

<!-- ===== PDF p123 ===== -->
第 2.7 节、第 113 页（Sec. 2.7, p. 113）

# <span style="color:#c0392b;">独立性（Independence）</span>

若 $X, Y, Z$ 相互独立（independent），则对任意 $x, y, z$ 成立

```math
p_{X,Y,Z}(x,y,z) = p_X(x)\,p_Y(y)\,p_Z(z).
```

如果 $X, Y$ 和 $Z$ 是独立随机变量，那么形如 $f(X)$、$g(Y)$ 和 $h(Z)$ 的任何三个随机变量（any three random variables）也是独立的。类似地，形如 $g(X,Y)$ 和 $h(Z)$ 的任何两个随机变量也是独立的。另一方面，形如 $g(X,Y)$ 和 $h(Y,Z)$ 的两个随机变量通常**并非**独立（independent），因为它们都受到 $Y$ 的影响。如果把独立性理解为互不干预的（子）试验（noninteracting (sub)experiments），上述诸如此类的性质在直观上是清晰的。它们可以形式化地加以验证，但这有时很繁琐。幸运的是，直观与数学上正确的结果之间存在普遍的一致。这基本上证明了我们对独立性的定义充分反映了其预期的含义。

---

# <span style="color:#c0392b;">独立随机变量之和的方差（Variance of the Sum of Independent Random Variables）</span>

独立随机变量之和在多种情境下特别重要。例如，它们出现在统计应用中当我们要"平均"若干独立的测量值（independent measurements），以最小化测量误差的影响时。它们也出现在处理多个独立随机性来源的累积效应时。我们在后续的例子中给出一些说明，并将在后面的章节中再次回到这一主题。

在下面的例子中，我们将用到如下关键性质。如果 $X_1, X_2, \dots, X_n$ 是独立随机变量，那么

```math
\mathrm{var}(X_1 + X_2 + \cdots + X_n) = \mathrm{var}(X_1) + \mathrm{var}(X_2) + \cdots + \mathrm{var}(X_n).
```

这可以通过反复使用对两个独立随机变量 $X$ 和 $Y$ 成立的公式 $\mathrm{var}(X+Y) = \mathrm{var}(X) + \mathrm{var}(Y)$ 来加以验证。

---

> <span style="color:#2471a3;">**[例题]**</span> <span style="color:#c0392b;">**例 2.20 二项分布与泊松分布的方差（Variance of the Binomial and the Poisson）。**</span>

我们考虑 $n$ 次独立的抛硬币试验，每次抛掷出现正面的概率为 $p$。对每个 $i$，我们令 $X_i$ 为伯努利随机变量（Bernoulli random variable）：若第 $i$ 次抛掷出现正面则取 $1$，否则取 $0$。于是 $X = X_1 + X_2 + \cdots + X_n$ 是一个二项随机变量（binomial random variable）。其均值为 $E[X] = np$，如例 2.10 中所推导的那样。由抛硬币试验的独立性，随机变量 $X_1, \dots, X_n$ 相互独立，且

```math
\mathrm{var}(X) = \sum_{i=1}^{n} \mathrm{var}(X_i) = np(1-p).
```

正如第 2.2 节所讨论的，参数为 $\lambda$ 的泊松随机变量 $Y$（Poisson random variable）可视为当 $n \to \infty$、$p \to 0$ 而 $np = \lambda$ 时二项分布的"极限"。因此，对二项分布的均值与方差取极限，我们非形式化地得到泊松分布的均值与方差：$E[Y] = \mathrm{var}(Y) = \lambda$。我们确实 \\

<!-- ===== PDF p124 ===== -->
# <span style="color:#c0392b;">离散随机变量（Discrete Random Variables）</span>

## <span style="color:#c0392b;">第 2 章（Chap. 2）</span>

---

- **第 124 页（page 124）** — 上接例 2.7，验证泊松随机变量 $Y$ 的均值与方差公式 $E[Y] = \mathrm{var}(Y) = \lambda$；本例源于泊松分布（Poisson distribution）。

我们在例 2.7（Example 2.7）中验证了泊松分布的均值 $E[Y] = \lambda$。为验证方差公式 $\mathrm{var}(Y) = \lambda$，我们写出

```math
\sum_{m=0}^{\infty} m\,(m{-}1)\,p_Y(m) \;=\; \lambda\big(E[Y]+1\big) \;=\; \lambda(\lambda+1),
```

由此得到

```math
\mathrm{var}(Y) = \lambda(\lambda+1) - \lambda^{2} = \lambda .
```

---

> <span style="color:#1e8449;">**[note] 译者注:**</span> $E[Y]=var(Y)=\lambda$ 对泊松分布是它的"身份指纹"，且绝非巧合，而是出身使然：泊松就是二项分布的极限，当 $n\to\infty,\ p\to0,\ np=\lambda$ 固定时，$E[X]=np=\lambda$、$var[X]=np(1-p)\to\lambda$，均值和方差一起被钉在同一个 $\lambda$ 上。你已会用 $(1-\lambda/n)^n\to e^{-\lambda}$ 推泊松的 PMF，现在只消把均值与方差也罩进同一套极限。第一性原理：均值=方差=λ 意味着泊松刻画的是"低概率×大时空窗"的稀有事件计数，其波动 $\sqrt{\lambda}$ 随均值同步增长，与方差固定的分布(如伯努利/均匀)气质截然不同；这也是"均方差相等"能作为"它是泊松"快速判据的原因。与实分析/组合里的 Poisson(二项) 近似一脉相承：常见结论是"稀有事件遵循泊松律"。预告：到第 6 章泊松会被升级成计数过程，均方差相等正是其稀疏、无记忆假设的概率签名。

随机变量加权和（weighted sum of random variables）的均值与方差的公式，构成了许多统计方法的基础；这些方法通过平均大量独立样本（independent samples）来估计一个随机变量的均值。典型的情形在下面的例题中说明。

---

<span style="color:#2471a3;">**█ 例题 2.21　样本均值（Sample Mean）的均值与方差**</span>

我们希望估计一位总统的支持率，记其为 $B$。为此，我们从选民总体（voter population）中随机抽取 $n$ 人，并令 $X_i$ 为对第 $i$ 个人的回答进行编码的随机变量（random variable）：

```math
X_i = \begin{cases} 1, & \text{若第 } i \text{ 个人认可 } B \text{ 的表现（approves } B\text{'s performance）},\\ 0, & \text{若第 } i \text{ 个人不认可 } B \text{ 的表现（disapproves } B\text{'s performance）}. \end{cases}
```

我们将 $X_1, X_2, \ldots, X_n$ 建模为相互独立的伯努利随机变量（independent Bernoulli random variables），具有共同的均值 $p$ 与方差 $p(1-p)$。自然，我们把 $p$ 视为 $B$ 的真实支持率（true approval rating）。我们对这些回答取“平均”，并计算样本均值（sample mean）$S_n$，定义为

```math
S_n = \frac{X_1 + X_2 + \cdots + X_n}{n}.
```

因此，随机变量 $S_n$ 就是我们这 $n$ 人样本中 $B$ 的支持率。

利用 $S_n$ 作为 $X_i$ 的函数所具有的线性性（linearity），我们得到

```math
E[S_n] = \frac{1}{n}\sum_{i=1}^{n} E[X_i] = \frac{1}{n}\sum_{i=1}^{n} p = p,
```

并且利用 $X_1, \ldots, X_n$ 的独立性（independence），得到

```math
\mathrm{var}(S_n) = \frac{1}{n^2}\sum_{i=1}^{n} \mathrm{var}(X_i) = \frac{p(1-p)}{n}.
```

<!-- ===== PDF p125 ===== -->
### <span style="color:#c0392b;">Sec. 2.8（第 125 页，接上页 Example 2.21 讨论）</span>

样本均值 $S_n$ 可被看作批准率 $p$ 的一个「好」估计（*good estimate*）。这是因为它具有正确的期望值，即批准率 $p$，而且它的精度——由方差反映——会随样本容量（*sample size*）增大而提高。注意，即便随机变量 $X_i$ 并非伯努利（*Bernoulli*）分布，只要 $X_i$ 相互独立、具有公共均值 $E[X]$ 与公共方差 $\text{var}(X)$，同样的计算仍给出

```math
\text{var}(S_n) = \frac{\text{var}(X)}{n}
```

因此，再次地，随着样本容量增大，样本均值便成为真实均值 $E[X]$ 的一个好估计（就方差而言）。我们将在第 5 章结合大数定理（*laws of large numbers*）重新审视样本均值的这些性质，并作远为详细的讨论。

---

<span style="color:#2471a3;">**【例题 2.22｜用模拟估算概率（Estimating Probabilities by Simulation）】**</span>

在许多实际情形中，对某个感兴趣事件的概率进行解析计算（*analytical calculation*）是非常困难的。然而，如果我们有一台物理或计算机模型（*model*），能够按照真实概率生成给定实验的结果，我们就可以用模拟（*simulation*）来高精度地计算任何给定事件 $A$ 的概率。具体来说，我们用模型独立地生成 $n$ 个结果，记录落入感兴趣事件 $A$ 的结果个数 $m$，并用 $m/n$ 来近似 $P(A)$。例如，为了计算一枚硬币正面朝上的概率 $p = P(\text{Heads})$，我们抛掷硬币 $n$ 次，并用比值（记录到的正面次数）/ $n$ 来近似 $p$。

为考察这一过程的精度，考虑相互独立的伯努利随机变量 $X_1, X_2, \dots, X_n$，每个都具有如下的 PMF（概率质量函数）：

```math
p_{X_i}(k) =
\begin{cases}
P(A), & \text{若 } k = 1,\\[2mm]
1 - P(A), & \text{若 } k = 0.
\end{cases}
```

在模拟语境中， $X_i$ 对应第 $i$ 个结果，当第 $i$ 个结果属于事件 $A$ 时取值为 $1$。随机变量

```math
X = \frac{X_1 + X_2 + \cdots + X_n}{n}
```

的值即为模拟所提供的对 $P(A)$ 的估计。根据 Example 2.21， $X$ 具有均值 $P(A)$ 和方差 $P(A)(1-P(A))/n$，因此对于大的 $n$，它能提供 $P(A)$ 的精确估计。

> <span style="color:#1e8449;">**[note] 译者注:**</span> 例 2.22 用样本均值 $X=(X_1+\cdots+X_n)/n$ 代替 $P(A)$：$n$ 个独立 0/1 变量相加正好是二项，其样本均值的期望恰为 $P(A)$、方差为 $P(A)(1-P(A))/n$——也就是说估计以 $\mathrm{O}(1/\sqrt n)$ 的标准差随 $n$ 收敛，这是"随机模拟/蒙特卡洛"最朴素又可靠的理由：只要拥有能按真实概率生成结果的模型，用大样本频率逼近解析概率就能让误差受控，无需手工去算联合分布。它与 6.006 的随机化算法思路同构：随机化判定/算法正确性的概率分析，靠的往往也是"大量独立试验的样本均值集中于期望"。务请注意它与精确计算的差别：模拟给出的是"估计 + 误差界"，而非精确值，真正把它钉死的是第 5 章的大数定律(以及后续的中心极限定理)，它们把"样本均值 − 总体均值"的差距写成依概率收敛/依分布收敛的语言。

---

### <span style="color:#c0392b;">2.8 总结与讨论（SUMMARY AND DISCUSSION）</span>

随机变量（*random variables*）为处理这样一类概率模型——其中结果决定了我们关心的若干个数值——提供了自然的工具。在本章中，我们聚焦于离散随机变量（*discrete random variables*），并建立了一个概念框架及若干相关工具。

具体来说，我们引入了如 PMF、均值（*mean*）与方差（*variance*）等概念，它们在不同程度上刻画了概率性质的细节……

<!-- ===== PDF p126 ===== -->
# <span style="color:#c0392b;">离散随机变量（Discrete Random Variables）</span>

## <span style="color:#c0392b;">第 2 章（Chap. 2）</span>

---

- **第 126 页（page 126）** — 特殊随机变量（special random variables）结论汇总（Summary of Results）。

我们展示了如何利用一个随机变量 $X$ 的概率质量函数（PMF，probability mass function）来计算相关随机变量 $Y = g(X)$ 的均值与方差，而无需计算 $Y$ 的概率质量函数。在 $g$ 是线性函数（linear function）$Y = aX + b$ 的特殊情形下，$X$ 与 $Y$ 的均值和方差由下式相关联：

```math
E[Y] = aE[X] + b,\qquad \mathrm{var}(Y) = a^{2}\,\mathrm{var}(X).
```

我们还讨论了几种特殊的随机变量，并推导出它们的概率质量函数、均值与方差，如下面表格所汇总。

---

## <span style="color:#c0392b;">特殊随机变量结论汇总（Summary of Results for Special Random Variables）</span>

<span style="color:#2471a3;">**█ 离散均匀分布（Discrete Uniform）于 $[a, b]$：**</span>

随机变量 $X$ 以等概率取值 $k = a, a+1, \ldots, b$。

```math
p_X(k) = \begin{cases} \dfrac{1}{b-a+1}, & \text{若 } k = a, a+1, \ldots, b,\\[6pt] 0, & \text{其他情形（otherwise）}, \end{cases}
```

```math
E[X] = \frac{a+b}{2},\qquad \mathrm{var}(X) = \frac{(b-a)(b-a+2)}{12}.
```

---

<span style="color:#2471a3;">**█ 参数为 $p$ 的伯努利分布（Bernoulli with Parameter $p$）：**</span>（描述单次试验（a single trial）中的成功或失败。）

```math
p_X(k) = \begin{cases} p, & \text{若 } k = 1,\\ 1-p, & \text{若 } k = 0, \end{cases}
```

```math
E[X] = p,\qquad \mathrm{var}(X) = p(1-p).
```

---

<span style="color:#2471a3;">**█ 参数为 $p$ 与 $n$ 的二项分布（Binomial with Parameters $p$ and $n$）：**</span>（描述 $n$ 次独立伯努利试验（independent Bernoulli trials）中成功的次数。）

```math
p_X(k) = \binom{n}{k}p^{\,k}(1-p)^{\,n-k},\qquad k = 0, 1, \ldots, n,
```

```math
E[X] = np,\qquad \mathrm{var}(X) = np(1-p).
```

---

<span style="color:#2471a3;">**█ 参数为 $p$ 的几何分布（Geometric with Parameter $p$）：**</span>（描述在一列独立伯努利试验中，直到首次成功（the first success）为止所需的试验次数。）

```math
p_X(k) = (1-p)^{\,k-1}\,p,\qquad k = 1, 2, \ldots,
```

```math
E[X] = \frac{1}{p},\qquad \mathrm{var}(X) = \frac{1-p}{p^{2}}.
```

---

<span style="color:#2471a3;">**█ 参数为 $\lambda$ 的泊松分布（Poisson with Parameter $\lambda$）：**</span>（用于近似二项分布 PMF，条件为 $n$ 很大、$p$ 很小且 $\lambda = np$。）

```math
p_X(k) = \frac{e^{-\lambda}\lambda^{k}}{k!}, \qquad k = 0, 1, 2, \ldots,
```

```math
E[X] = \lambda, \qquad \mathrm{var}(X) = \lambda .
```

---

<!-- ===== PDF p127 ===== -->
## <span style="color:#c0392b;">Joint PMFs 与 Conditional PMFs（联合/条件概率质量函数）</span>

我们还考虑了多个随机变量，并引入了 joint PMFs（联合 PMF）、conditional PMFs（条件 PMF）以及与之相关的期望值。Conditional PMFs（条件 PMF）常常是概率模型（probabilistic models）的出发点，可以借助**顺序法**（sequential approach）或**分治法**（divide-and-conquer approach）用于计算其他感兴趣的量，例如 marginal PMFs（边际 PMF）、joint PMFs（联合 PMF）和期望。特别地，给定条件 PMF

```math
p_{X\mid Y}(x \mid y),
```

可进行如下计算：

- **(a) 联合 PMF 可以由下式计算：**
```math
p_{X,Y}(x, y) = p_Y(y)\, p_{X\mid Y}(x \mid y).
```
这可以推广到三个或更多随机变量的情形，例如
```math
p_{X,Y,Z}(x, y, z) = p_Z(z)\, p_{Y\mid Z}(y \mid z)\, p_{X\mid Y,Z}(x \mid y, z),
```
这与第 1 章讨论过的基于 multiplication rule（乘法规则）的 sequential tree-based calculation method（顺序树式计算法）相类似。

- **(b) 边际 PMF 可以由下式计算：**
```math
p_X(x) = \sum_y p_Y(y)\, p_{X\mid Y}(x \mid y),
```
它推广了我们第 1 章讨论过的 divide-and-conquer calculation method（分治计算法）。

- **(c) 上述 (b) 中的分治计算法可以进一步推广，用于借助 total expectation theorem（全期望定理）计算期望值：**
```math
E[X] = \sum_y p_Y(y)\, E[X \mid Y = y].
```

---

我们引入了随机变量独立（independence of random variables）的概念，这与事件的独立（independence of events）概念相类似。在其余主题中，我们重点关注了由若干独立随机变量相加所得的随机变量
```math
X_1, \dots, X_n,
```
即
```math
X = X_1 + \dots + X_n.
```

---

<!-- ===== PDF p128 ===== -->
# <span style="color:#c0392b;">离散随机变量（Discrete Random Variables）</span>

## <span style="color:#c0392b;">第 2 章（Chap. 2）</span>

---

- **第 128 页（page 128）** — 第 2 章章末小结段：和的均值（mean）等于均值之和、和的方差（variance）等于方差之和；均值公式无需独立性（independence），方差公式则需；并预告方法与概念将自然延拓到下一章的连续随机变量（continuous random variables）。

我们论证了，和的均值与方差分别等于均值之和与方差之和：

```math
E[X] = E[X_1] + \cdots + E[X_n],
```

```math
\mathrm{var}(X) = \mathrm{var}(X_1) + \cdots + \mathrm{var}(X_n).
```

均值公式并不要求各 $X_i$ 相互独立（independent），但方差公式需要独立性。

本章的概念与方法能恰当地延拓到一般的随机变量（general random variables，参见下一章），并且是我们这门学科的基础。

---

<!-- ===== PDF p129 ===== -->
# <span style="color:#c0392b;">Problems</span>

## <span style="color:#c0392b;">SECTION 2.2. Probability Mass Functions</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 1.</span> The MIT soccer team has 2 games scheduled for one weekend. It has a $0.4$ probability of not losing the first game, and a $0.7$ probability of not losing the second game, independent of the first. If it does not lose a particular game, the team is equally likely to win or tie, independent of what happens in the other game. The MIT team will receive $2$ points for a win, $1$ for a tie, and $0$ for a loss. Find the PMF of the number of points that the team earns over the weekend.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 2.</span> You go to a party with $500$ guests. What is the probability that exactly one other guest has the same birthday as you? Calculate this exactly and also approximately by using the Poisson PMF. (For simplicity, exclude birthdays on February 29.)

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 3.</span> Fischer and Spassky play a chess match in which the first player to win a game wins the match. After $10$ successive draws, the match is declared drawn. Each game is won by Fischer with probability $0.4$, is won by Spassky with probability $0.3$, and is a draw with probability $0.3$, independent of previous games.

(a) What is the probability that Fischer wins the match?
(b) What is the PMF of the duration of the match?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 4.</span> An internet service provider uses $50$ modems to serve the needs of $1000$ customers. It is estimated that at a given time, each customer will need a connection with probability $0.01$, independent of the other customers.

(a) What is the PMF of the number of modems in use at the given time?
(b) Repeat part (a) by approximating the PMF of the number of customers that need a connection with a Poisson PMF.
(c) What is the probability that there are more customers needing a connection than there are modems? Provide an exact, as well as an approximate formula based on the Poisson approximation of part (b).

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 5.</span> A packet communication system consists of a buffer that stores packets from some source, and a communication line that retrieves packets from the buffer and transmits them to a receiver. The system operates in time-slot pairs. In the first slot, the system stores a number of packets that are generated by the source according to a Poisson PMF with parameter $\lambda$; however, the maximum number of packets that can be stored is a given integer $b$, and packets arriving to a full buffer are discarded. In the second slot, the system transmits either all the stored packets or $c$ packets (whichever is less). Here, $c$ is a given integer with $0 < c < b$.

<!-- ===== PDF p130 ===== -->
## <span style="color:#c0392b;">Discrete Random Variables</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 5.</span> <span style="color:#7f8c8d;">[本题题设见上一页，此处仅收录本页可见的 (a)–(b) 两问]</span>

(a) Assuming that at the beginning of the first slot the buffer is empty, find the PMF of the number of packets stored at the end of the first slot and at the end of the second slot.

(b) What is the probability that some packets get discarded during the first slot?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 6.</span> The Celtics and the Lakers are set to play a playoff series of $n$ basketball games, where $n$ is odd. The Celtics have a probability $p$ of winning any one game, independent of other games.

(a) Find the values of $p$ for which $n = 5$ is better for the Celtics than $n = 3$.

(b) Generalize part (a), i.e., for any $k > 0$, find the values for $p$ for which $n = 2k + 1$ is better for the Celtics than $n = 2k - 1$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 7.</span> You just rented a large house and the realtor gave you 5 keys, one for each of the 5 doors of the house. Unfortunately, all keys look identical, so to open the front door, you try them at random.

(a) Find the PMF of the number of trials you will need to open the door, under the following alternative assumptions: (1) after an unsuccessful trial, you mark the corresponding key, so that you never try it again, and (2) at each trial you are equally likely to choose any key.

(b) Repeat part (a) for the case where the realtor gave you an extra duplicate key for each of the 5 doors.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 8.</span> *Recursive computation of the binomial PMF.* Let $X$ be a binomial random variable with parameters $n$ and $p$. Show that its PMF can be computed by starting with

```math
p_X(0) = (1 - p)^n,
```

and then using the recursive formula

```math
p_X(k+1) = \frac{p}{1-p} \cdot \frac{n-k}{k+1} \cdot p_X(k), \qquad k = 0, 1, \ldots, n-1.
```

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 9.</span> *Form of the binomial PMF.* Consider a binomial random variable $X$ with parameters $n$ and $p$. Let $k^{*}$ be the largest integer that is less than or equal to $(n+1)p$. Show that the PMF $p_X(k)$ is monotonically nondecreasing with $k$ in the range from $0$ to $k^{*}$, and is monotonically decreasing with $k$ for $k \ge k^{*}$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 10.</span> *Form of the Poisson PMF.* Let $X$ be a Poisson random variable with parameter $\lambda$. Show that the PMF $p_X(k)$ increases monotonically with $k$ up to the point where $k$ reaches the largest integer not exceeding $\lambda$, and after that point decreases monotonically with $k$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 11. ***</span> *The matchbox problem — inspired by Banach's smoking habits.* A smoker mathematician carries one matchbox in his right pocket and one in his left pocket. Each time he wants to light a cigarette, he selects a matchbox from either pocket with probability $p = 1/2$, independent of earlier selections. The two matchboxes have initially $n$ matches each. What is the PMF of the number of remaining matches at the moment when the mathematician reaches for a match and discovers that the corresponding matchbox is empty? How can we generalize to the case where the probabilities of a left and a right pocket selection are $p$ and $1 - p$, respectively?

<!-- ===== PDF p131 ===== -->
## <span style="color:#c0392b;">Problems</span>

<span style="color:#c0392b;">**Problem 11.**</span> *(solution, continued)*

Solution. Let $X$ be the number of matches that remain when a matchbox is found empty. For $k = 0, 1, \ldots, n$, let $L_k$ (or $R_k$) be the event that an empty box is first discovered in the left (respectively, right) pocket while the number of matches in the right (respectively, left) pocket is $k$ at that time. The PMF of $X$ is

```math
p_X(k) = \binom{2n-k}{n}\left(\frac{1}{2}\right)^{2n-k}, \qquad k = 0, 1, \ldots, n.
```

Viewing a left and a right pocket selection as a "success" and a "failure," respectively, in $2n-k$ trials, $P(L_k)$ is the probability that there are $n$ successes in the first $2n-k$ trials, and trial $2n-k+1$ is a success, or

```math
P(L_k) = \binom{2n-k}{n}\left(\frac{1}{2}\right)^{2n-k+1}, \qquad k = 0, 1, \ldots, n.
```

By symmetry, $P(L_k) = P(R_k)$, so

```math
p_X(k) = P(L_k) + P(R_k) = 2 \cdot \binom{2n-k}{n}\left(\frac{1}{2}\right)^{2n-k+1}
= \binom{2n-k}{n}\left(\frac{1}{2}\right)^{2n-k}, \qquad k = 0, 1, \ldots, n.
```

In the more general case, where the probabilities of a left and a right pocket selection are $p$ and $1 - p$, using a similar reasoning, we obtain

```math
P(L_k) = \binom{2n-k}{n} p^{n+1}(1-p)^{n-k}, \qquad k = 0, 1, \ldots, n,
```

and

```math
P(R_k) = \binom{2n-k}{n} p^{n-k}(1-p)^{n+1}, \qquad k = 0, 1, \ldots, n,
```

which yields

```math
p_X(k) = P(L_k) + P(R_k)
= \binom{2n-k}{n}\Bigl(p^{n+1}(1-p)^{n-k} + p^{n-k}(1-p)^{n+1}\Bigr), \qquad k = 0, 1, \ldots, n.
```

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 12.**</span> * Justification of the Poisson approximation property. Consider the PMF of a binomial random variable with parameters $n$ and $p$. Show that asymptotically, as $n \to \infty$, $p \to 0$, while $np$ is fixed at a given value $\lambda$, this PMF approaches the PMF of a Poisson random variable with parameter $\lambda$.

**Solution.** Using the equation $\lambda = np$, write the binomial PMF as

```math
p_n(k) = \frac{n!}{(n-k)!\,k!}\, p^k (1-p)^{n-k}
= \frac{n(n-1)\cdots(n-k+1)}{n^k} \cdot \frac{\lambda^k}{k!} \cdot \left(1 - \frac{\lambda}{n}\right)^{n-k}.
```

<!-- ===== PDF p132 ===== -->
<span style="color:#c0392b;">**Problem 12.**</span> *(solution, continued)*

**Solution.** ... Fix $k$ and let $n \to \infty$. We have, for $j = 1, \ldots, k$,

```math
\frac{n - k + j}{n} \to 1, \qquad \left(1 - \frac{\lambda}{n}\right)^{n-k+j} \to e^{-\lambda}.
```

Thus, for each fixed $k$, as $n \to \infty$ we obtain

```math
p_n(k) \to e^{-\lambda}\cdot\frac{\lambda^{k}}{k!},
```

（<span style="color:#7f8c8d;">[OCR 缺式，按教材重建]</span>）

## <span style="color:#c0392b;">SECTION 2.3. Functions of Random Variables</span>

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 13.**</span> A family has 5 natural children and has adopted 2 girls. Each natural child has equal probability of being a girl or a boy, independent of the other children. Find the PMF of the number of girls out of the 7 children.

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 14.**</span> Let $X$ be a random variable that takes values from 0 to 9 with equal probability $1/10$.

(a) Find the PMF of the random variable $Y = X \bmod 3$.

(b) Find the PMF of the random variable $Y = 5 \bmod (X + 1)$.

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 15.**</span> Let $K$ be a random variable that takes, with equal probability $1/(2n+1)$, the integer values in the interval $[-n, n]$. Find the PMF of the random variable $Y = a|K|$, where $a$ is a positive number. <span style="color:#7f8c8d;">[OCR 残缺]</span>

## <span style="color:#c0392b;">SECTION 2.4. Expectation, Mean, and Variance</span>

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 16.**</span> Let $X$ be a random variable with PMF

```math
p_X(x) = \begin{cases} x^2/a, & \text{if } x = -3, -2, -1, 0, 1, 2, 3, \\ 0, & \text{otherwise.} \end{cases}
```

(a) Find $a$ and $E[X]$.

(b) What is the PMF of the random variable $Z = (X - E[X])^2$?

(c) Using the result from part (b), find the variance of $X$.

(d) Find the variance of $X$ using the formula $\operatorname{var}(X) = \sum_x (x - E[X])^2\, p_X(x)$.

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 17.**</span> A city's temperature is modeled as a random variable with mean and standard deviation both equal to 10 degrees Celsius. A day is described as "normal" if the temperature during that day ranges within one standard deviation from the mean. What would be the temperature range for a normal day if temperature were expressed in degrees Fahrenheit?

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 18.**</span> Let $a$ and $b$ be positive integers with $a \leq b$, and let $X$ be a random variable that takes as values, with equal probability, the powers of 2 in the interval $[2^a, 2^b]$. Find the expected value and the variance of $X$.

<!-- ===== PDF p133 ===== -->
## <span style="color:#c0392b;">Problems</span>

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 19.**</span> A prize is randomly placed in one of ten boxes, numbered from 1 to 10. You search for the prize by asking yes-no questions. Find the expected number of questions until you are sure about the location of the prize, under each of the following strategies.

(a) An enumeration strategy: you ask questions of the form "is it in box $k$?".

(b) A bisection strategy: you eliminate as close to half of the remaining boxes as possible by asking questions of the form "is it in a box numbered less than or equal to $k$?"

**Solution.** We will find the expected gain for each strategy, by computing the expected number of questions until we find the prize.

(a) With this strategy, the probability $1/10$ of finding the location of the prize with $i$ questions, where $i = 1, \ldots, 10$, is $1/10$. Therefore, the expected number of questions is

```math
\frac{1}{10}\sum_{i=1}^{10} i \;=\; \frac{1}{10} \cdot 55 \;=\; 5.5.
```

(b) It can be checked that for 4 of the 10 possible box numbers, exactly 4 questions will be needed, whereas for 6 of the 10 numbers, 3 questions will be needed. Therefore, with this strategy, the expected number of questions is

```math
\frac{4}{10}\cdot 4 \;+\; \frac{6}{10}\cdot 3 \;=\; 3.4.
```

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 20.**</span> As an advertising campaign, a chocolate factory places golden tickets in some of its candy bars, with the promise that a golden ticket is worth a trip through the chocolate factory, and all the chocolate you can eat for life. If the probability of finding a golden ticket is $p$, find the mean and the variance of the number of candy bars you need to eat to find a ticket.

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 21.**</span> *St. Petersburg paradox.* You toss independently a fair coin and you count the number of tosses until the first tail appears. If this number is $n$, you receive $2^n$ dollars. What is the expected amount that you will receive? How much would you be willing to pay to play this game?

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 22.**</span> Two coins are simultaneously tossed until one of them comes up a head and the other a tail. The first coin comes up a head with probability $p$ and the second with probability $q$. All tosses are assumed independent.

(a) Find the PMF, the expected value, and the variance of the number of tosses.

(b) What is the probability that the last toss of the first coin is a head?

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">**Problem 23.**</span>

(a) A fair coin is tossed repeatedly and independently until two consecutive heads or two consecutive tails appear. Find the PMF, the expected value, and the variance of the number of tosses.

(b) Assume now that the coin is tossed until we obtain a tail that is immediately preceded by a head. Find the PMF and the expected value of the number of tosses.

<!-- ===== PDF p134 ===== -->
## <span style="color:#c0392b;">2.5 Joint PMFs of Multiple Random Variables</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 24.</span> A stock market trader buys 100 shares of stock A and 200 shares of stock B. Let $X$ and $Y$ be the price changes of A and B, respectively, over a certain time period, and assume that the joint PMF of $X$ and $Y$ is uniform over the set of integers $x$ and $y$ satisfying

```math
-2 \le x \le 4, \qquad -1 \le y - x \le 1.
```

(a) Find the marginal PMFs and the means of $X$ and $Y$.
(b) Find the mean of the trader's profit.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 25.</span> A class of $n$ students takes a test consisting of $m$ questions. Suppose that student $i$ submitted answers to the first $m_i$ questions.

(a) The grader randomly picks one answer, call it $(I, J)$, where $I$ is the student ID number (taking values $1, \dots, n$) and $J$ is the question number (taking values $1, \dots, m$). Assume that all answers are equally likely to be picked. Calculate the joint and the marginal PMFs of $I$ and $J$.
(b) Assume that an answer to question $j$, if submitted by student $i$, is correct with probability $p_{ij}$. Each answer gets $a$ points if it is correct and gets $b$ points otherwise. Calculate the expected value of the score of student $i$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 26.</span> PMF of the minimum of several random variables. On a given day, your golf score takes values from the range 101 to 110, with probability 0.1, independent of other days. Determined to improve your score, you decide to play on three different days and declare as your score the minimum $X$ of the scores $X_1$, $X_2$, and $X_3$ on the different days.

(a) Calculate the PMF of $X$.
(b) By how much has your expected score improved as a result of playing on three days?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 27. ...</span> The multinomial distribution. A die with $r$ faces, numbered $1, \dots, r$, is rolled a fixed number of times $n$. The probability that the $i$th face comes up on any one roll is denoted $p_i$, and the results of different rolls are assumed independent. Let $X_i$ be the number of times that the $i$th face comes up.

(a) Find the joint PMF $p_{X_1, \dots, X_r}(k_1, \dots, k_r)$.
(b) Find the expected value and variance of $X_i$.
(c) Find $E[X_i X_j]$ for $i \ne j$.

<span style="color:#c0392b;">Solution.</span> (a) The probability of a sequence of rolls where, for $i = 1, \dots, r$, face $i$ comes up $k_i$ times is $p_1^{k_1} \cdots p_r^{k_r}$. Every such sequence determines a partition of the set of $n$ rolls into $r$ subsets with the $i$th subset having cardinality $k_i$ (this is the set of rolls <span style="color:#7f8c8d;">[OCR 残缺]</span>

<!-- ===== PDF p135 ===== -->
## <span style="color:#c0392b;">Solution (continued)</span>

for which the $i$th face came up). The number of such partitions is the multinomial coefficient (cf. Section 1.6)

```math
\binom{n}{k_1, \ldots, k_r} = \frac{n!}{k_1! \cdots k_r!}.
```

Thus, if $k_1 + \cdots + k_r = n$,

```math
P_{X_1, \ldots, X_r}(k_1, \ldots, k_r) = \frac{n!}{k_1! \cdots k_r!}\, p_1^{k_1} \cdots p_r^{k_r},
```

and otherwise, $P_{X_1, \ldots, X_r}(k_1, \ldots, k_r) = 0$.

**(b)** The random variable $X_1$ is binomial with parameters $n$ and $p_1$. Therefore, $E[X_1] = n p_1$, and $\operatorname{var}(X_1) = n p_1 (1 - p_1)$.

**(c)** Suppose that $i \neq j$, and let $Y_{i,k}$ (or $Y_{j,k}$) be the Bernoulli random variable that takes the value $1$ if face $i$ (respectively, $j$) comes up on the $k$th roll, and the value $0$ otherwise. Note that $Y_{i,k} Y_{j,k} = 0$, and that for $l \neq k$, $Y_{i,k}$ and $Y_{j,l}$ are independent, so that $E[Y_{i,k} Y_{j,l}] = p_i p_j$. Therefore,

```math
E[X_i X_j] = E\left[ (Y_{i,1} + \cdots + Y_{i,n})(Y_{j,1} + \cdots + Y_{j,n}) \right]
= n(n-1)E[Y_{i,1} Y_{j,2}]
= n(n-1) p_i p_j .
```

## <span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 28.</span> * The quiz problem.

Consider a quiz contest where a person is given a list of $n$ questions and can answer these questions in any order he or she chooses. Question $i$ will be answered correctly with probability $p_i$, and the person will then receive a reward $v_i$. At the first incorrect answer, the quiz terminates and the person is allowed to keep his or her previous rewards. The problem is to choose the ordering of questions so as to maximize the expected value of the total reward obtained. Show that it is optimal to answer questions in a nonincreasing order of $p_i v_i / (1 - p_i)$.

**Solution.** We will use a so-called interchange argument, which is often useful in sequencing problems. Let $i$ and $j$ be the $k$th and $(k+1)$st questions in an optimally ordered list $L$. Consider the list $L'$ obtained from $L$ by interchanging the order of questions $i$ and $j$. We compute the expected values of the rewards of $L$ and $L'$, and note that since $L$ is optimally ordered, we have

```math
E[\text{reward of } L] \geq E[\text{reward of } L'].
```

Define the weight of question $i$ to be

```math
w(i) = \frac{p_i v_i}{1 - p_i}.
```

<!-- ===== PDF p136 ===== -->
# <span style="color:#c0392b;">Discrete Random Variables — Chapter 2 (Problems)</span>

## <span style="color:#c0392b;">Solution (conclusion of the expected-reward problem)</span>

We will show that any permutation of the questions in a nonincreasing order of weights maximizes the expected reward.

If $L = (i_1, \ldots, i_n)$ is a permutation of the questions, define $L^{(k)}$ to be the permutation obtained from $L$ by interchanging questions $i_k$ and $i_{k+1}$. Let us first compute the difference between the expected reward of $L$ and that of $L^{(k)}$. We have

```math
E[\text{reward of }L] = p_{i_1}v_{i_1} + p_{i_1}p_{i_2}v_{i_2} + \cdots + p_{i_1}\cdots p_{i_{k-1}}v_{i_{k-1}}
+ p_{i_1}\cdots p_{i_{k-1}}p_{i_k}v_{i_k} + p_{i_1}\cdots p_{i_{k-1}}p_{i_k}p_{i_{k+1}}v_{i_{k+1}}
+ p_{i_1}\cdots p_{i_{k+2}}v_{i_{k+2}} + \cdots + p_{i_1}\cdots p_{i_n}v_{i_n},
```

and

```math
E[\text{reward of }L^{(k)}] = p_{i_1}v_{i_1} + p_{i_1}p_{i_2}v_{i_2} + \cdots + p_{i_1}\cdots p_{i_{k-1}}v_{i_{k-1}}
+ p_{i_1}\cdots p_{i_{k-1}}p_{i_{k+1}}v_{i_{k+1}} + p_{i_1}\cdots p_{i_{k-1}}p_{i_{k+1}}p_{i_k}v_{i_k}
+ p_{i_1}\cdots p_{i_{k+2}}v_{i_{k+2}} + \cdots + p_{i_1}\cdots p_{i_n}v_{i_n}.
```

Therefore,

```math
\begin{aligned}
E[\text{reward of }L^{(k)}] - E[\text{reward of }L]
&= p_{i_1}\cdots p_{i_{k-1}}\bigl(p_{i_{k+1}}v_{i_{k+1}} + p_{i_{k+1}}p_{i_k}v_{i_k} - p_{i_k}v_{i_k} - p_{i_k}p_{i_{k+1}}v_{i_{k+1}}\bigr)\\
&= p_{i_1}\cdots p_{i_{k-1}}\,(1 - p_{i_k})(1 - p_{i_{k+1}})\bigl(w_{i_{k+1}} - w_{i_k}\bigr).
\end{aligned}
```

Now, let us go back to our problem. Consider any permutation $L$ of the questions. If $w_{i_k} < w_{i_{k+1}}$ for some $k$, it follows from the above equation that the permutation $L^{(k)}$ has an expected reward larger than that of $L$. So, an optimal permutation of the questions must be in a nonincreasing order of weights.

Let us finally show that any two such permutations have equal expected rewards. Assume that $L$ is such a permutation and say that $w_{i_k} = w_{i_{k+1}}$ for some $k$. We know that interchanging $i_k$ and $i_{k+1}$ preserves the expected reward. So, the expected reward of any permutation $L'$ in a non-increasing order of weights is equal to that of $L$, because $L'$ can be obtained from $L$ by repeatedly interchanging adjacent questions having equal weights.

## <span style="color:#c0392b;">Problem 29.* — The inclusion–exclusion formula</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 29.***</span> The inclusion–exclusion formula. Let $A_1, A_2, \ldots, A_n$ be events.

Let $S_1 = \{i_1 \mid 1 \le i_1 \le n\}$, $S_2 = \{\{i_1, i_2\} \mid 1 \le i_1 < i_2 \le n\}$, and more generally, let $S_m$ be the set of all $m$-tuples $(i_1, \ldots, i_m)$ of indices that satisfy $1 \le i_1 < i_2 < \ldots < i_m \le n$. Show that

<span style="color:#7f8c8d;">[OCR 残缺：此处应为容斥公式 (inclusion–exclusion formula)]</span>

**Hint:** Let $X_i$ be a binary random variable which is equal to $1$ when $A_i$ occurs, and equal to $0$ otherwise. Relate the event of interest to the random variable $(1 - X_1)(1 - X_2)\cdots(1 - X_n)$.

## <span style="color:#c0392b;">Solution</span>

Let us express the event $B = \cup_{k=1}^n A_k$ in terms of the random variables $X_1, \ldots, X_n$. The event $B^c$ occurs when all of the random variables $X_1, \ldots, X_n$ are zero, which happens when the random variable $Y = (1 - X_1)(1 - X_2)\cdots(1 - X_n)$ is equal to $1$.

<!-- ===== PDF p137 ===== -->
##

Note that $Y$ can only take values in the set $\{0, 1\}$, so that $P(B) = P(Y = 1) = E[Y]$. Therefore,

```math
P(B) = 1 - E\Big[ (1 - X_1)(1 - X_2)\cdots(1 - X_n) \Big]
= E[X_1 + \cdots + X_n] - E\!\Big[\sum_{(i_1, i_2) \in S_2} X_{i_1} X_{i_2} \Big]
+ \cdots + (-1)^{r-1} E[X_1\cdots X_n].
```

We note that

```math
E[X_i] = P(A_i),
```

```math
E[X_{i_1} X_{i_2}] = P\big(A_{i_1} \cap A_{i_2}\big),
```

```math
E[X_{i_1} X_{i_2} X_{i_3}] = P\big(A_{i_1} \cap A_{i_2} \cap A_{i_3}\big),
```

```math
E[X_1 X_2 \cdots X_n] = P\Big(\bigcap_{k=1}^{n} A_k\Big),
```

etc., from which the desired formula follows.

##

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 30.</span> * Alvin's database of friends contains $n$ entries, but due to a software glitch, the addresses correspond to the names in a totally random fashion. Alvin writes a holiday card to each of his friends and sends it to the (software-corrupted) address. What is the probability that at least one of his friends will get the correct card? **Hint:** Use the inclusion-exclusion formula.

<span style="color:#c0392b;">Solution.</span> Let $A_k$ be the event that the $k$th card is sent to the correct address. We have for any $k$, $j$, $i$,

```math
P(A_k) = \frac{1}{n} = \frac{(n-1)!}{n!},
```

```math
P(A_k \cap A_j) = P(A_k)\,P(A_j \mid A_k) = \frac{1}{n}\cdot\frac{1}{n-1} = \frac{(n-2)!}{n!},
```

```math
P(A_k \cap A_j \cap A_i) = \frac{1}{n}\cdot\frac{1}{n-1}\cdot\frac{1}{n-2} = \frac{(n-3)!}{n!},
```

etc., and

Applying the inclusion-exclusion formula,

```math
P\!\Big(\bigcup_{k=1}^{n} A_k\Big) = \sum_{i \in S_1} P(A_i) \;-\; \sum_{(i_1, i_2) \in S_2} P\big(A_{i_1} \cap A_{i_2}\big) + \cdots
```

we obtain the desired probability

```math
P\!\Big(\bigcup_{k=1}^{n} A_k\Big)
= \binom{n}{1}\frac{(n-1)!}{n!} \;-\; \binom{n}{2}\frac{(n-2)!}{n!}
\;+\; \binom{n}{3}\frac{(n-3)!}{n!} \;-\; \cdots \;+\; (-1)^{n-1}\frac{1}{n!}
```

```math
= 1 - \frac{1}{2!} + \frac{1}{3!} - \cdots + (-1)^{n-1}\frac{1}{n!}.
```

When $n$ is large, this probability can be approximated by $1 - e^{-1}$.

<!-- ===== PDF p138 ===== -->
## <span style="color:#c0392b;">SECTION 2.6. Conditioning</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 31.</span> Consider four independent rolls of a 6-sided die. Let $X$ be the number of 1s and let $Y$ be the number of 2s obtained. What is the joint PMF of $X$ and $Y$?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 32.</span> D. Bernoulli's problem of joint lives. Consider $2m$ persons forming $m$ couples who live together at a given time. Suppose that at some later time, the probability of each person being alive is $p$, independent of other persons. At that later time, let $A$ be the number of persons that are alive and let $S$ be the number of couples in which both partners are alive. For any survivor number $a$, find $E[S \mid A = a]$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 33. \*</span> A coin that has probability of heads equal to $p$ is tossed successively and independently until a head comes twice in a row or a tail comes twice in a row. Find the expected value of the number of tosses.

**Solution.** One possibility here is to calculate the PMF of $X$, the number of tosses until the game is over, and use it to compute $E[X]$. However, with an unfair coin, this turns out to be cumbersome, so we argue by using the total expectation theorem and a suitable partition of the sample space. Let $H_k$ (or $T_k$) be the event that a head (or a tail, respectively) comes at the $k$th toss, and let $p$ (respectively, $q$) be the probability of $H_k$ (respectively, $T_k$). Since $H_1$ and $T_1$ form a partition of the sample space, and $P(H_1) = p$ and $P(T_1) = q$, we have

```math
E[X] = pE[X \mid H_1] + qE[X \mid T_1].
```

Using again the total expectation theorem, we have

```math
E[X \mid H_1] = pE[X \mid H_1 \cap H_2] + qE[X \mid H_1 \cap T_2] = 2p + q(1 + E[X \mid T_1]),
```

where we have used the fact $E[X \mid H_1 \cap H_2] = 2$ (since the game ends after two successive heads), and

```math
E[X \mid H_1 \cap T_2] = 1 + E[X \mid T_1]
```

(since if the game is not over, only the last toss matters in determining the number of additional tosses up to termination). Similarly, we obtain

```math
E[X \mid T_1] = 2q + p(1 + E[X \mid H_1]).
```

Combining the above two relations, collecting terms, and using the fact $p + q = 1$, we obtain after some calculation

```math
E[X \mid T_1] = \frac{2 + p^2}{1 - pq},
```

and similarly

```math
E[X \mid H_1] = \frac{2 + q^2}{1 - pq}.
```

<!-- ===== PDF p139 ===== -->
## <span style="color:#c0392b;">Problems</span>

Thus,

```math
E[X] = p \cdot \frac{2+q^{2}}{1-pq} + q \cdot \frac{2+p^{2}}{1-pq},
```

and finally, using the fact $p+q=1$,

```math
E[X] = \frac{2+pq}{1-pq}.
```

In the case of a fair coin ($p=q=1/2$), we obtain $E[X]=3$. It can also be verified
that $2 \le E[X] \le 3$ for all values of $p$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 34.</span>* A spider and a fly move along a straight line. At each second, the fly moves a unit step to the right or to the left with equal probability $p$, and stays where it is with probability $1-2p$. The spider always takes a unit step in the direction of the fly. The spider and the fly start $D$ units apart, where $D$ is a random variable taking positive integer values with a given PMF. If the spider lands on top of the fly, it's the end. What is the expected value of the time it takes for this to happen?

**Solution.** Let $T$ be the time at which the spider lands on top of the fly. We define

$A_d$: the event that initially the spider and the fly are $d$ units apart.
$B_d$: the event that after one second the spider and the fly are $d$ units apart.

Our approach will be to first apply the (conditional version of the) total expectation theorem to compute $E[T \mid A_d]$, then use the result to compute $E[T \mid A_{2}]$, and similarly compute sequentially $E[T \mid A_d]$ for all relevant values of $d$. We will then apply the (unconditional version of the) total expectation theorem to compute $E[T]$.

We have

$P(B_d \mid A_d) = p$, $\;$ $P(B_{d-1} \mid A_d) = 1 - 2p$, $\;$ $P(B_{d-2} \mid A_d) = p$,

if $d > 1$.

This is because if the spider and the fly are at a distance $d > 1$ apart, then one second later their distance will be $d$ (if the fly moves away from the spider) or $d-1$ (if the fly does not move) or $d-2$ (if the fly moves towards the spider). We also have, for the case where the spider and the fly start one unit apart,

$P(B_1 \mid A_1) = 2p$, $\;$ $P(B_0 \mid A_1) = 1 - 2p$.

Using the total expectation theorem, we obtain

```math
E[T \mid A_d] = P(B_d \mid A_d)E[T \mid A_d \cap B_d] + P(B_{d-1} \mid A_d)E[T \mid A_d \cap B_{d-1}] + P(B_{d-2} \mid A_d)E[T \mid A_d \cap B_{d-2}],
```

if $d > 1$,

and

```math
E[T \mid A_1] = P(B_1 \mid A_1)E[T \mid A_1 \cap B_1] + P(B_0 \mid A_1)E[T \mid A_1 \cap B_0],
```

if $d = 1$.

It can be seen based on the problem data that

$P(B_1 \mid A_1) = 2p$,

$P(B_0 \mid A_1) = 1 - 2p$,

<!-- ===== PDF p140 ===== -->
## <span style="color:#c0392b;">Solution（续 · Problem 34）</span>

We have

$E[T \mid A_1 \cap B_1] = 1 + E[T \mid A_1]$, $\;$ $E[T \mid A_1 \cap B_0] = 1$,

so by applying the formula for the case $d = 1$, we obtain

```math
E[T \mid A_1] = 2p\,(1 + E[T \mid A_1]) + (1 - 2p),
```

or

```math
E[T \mid A_1] = \frac{1}{1 - 2p}.
```

By applying the formula with $d = 2$, we obtain

We have

$E[T \mid A_2 \cap B_0] = 1$,

$E[T \mid A_2 \cap B_1] = 1 + E[T \mid A_1]$,

$E[T \mid A_2 \cap B_2] = 1 + E[T \mid A_2]$,

so by substituting these relations in the expression for $E[T \mid A_2]$, we obtain

```math
E[T \mid A_2] = p\,(1 + E[T \mid A_2]) + (1 - 2p)\,(1 + E[T \mid A_1]) + p
```

```math
\qquad = p\,(1 + E[T \mid A_2]) + (1 - 2p)\left(1 + \frac{1}{1 - 2p}\right) + p.
```

This equation yields after some calculation

```math
E[T \mid A_2] = \frac{2}{1 - p}.
```

Generalizing, we obtain for $d \geq 2$,

```math
(1 - p)\,E[T \mid A_d] = (1 - 2p)\,E[T \mid A_{d-1}] + p\,E[T \mid A_{d-2}] + 1.
```

Thus, $E[T \mid A_d]$ can be generated recursively for any initial distance $d$, using as initial
conditions the values of $E[T \mid A_1]$ and $E[T \mid A_2]$ obtained earlier.

Finally, the expected value of $T$ can be obtained using the given PMF for the
initial distance $D$ and the total expectation theorem:

```math
E[T] = \sum_d p_D(d)\,E[T \mid A_d].
```

## <span style="color:#c0392b;">Problem 35</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 35.</span>* Verify the expected value rule

```math
E[g(X, Y)] = \sum_x \sum_y g(x, y)\,p_{X,Y}(x, y),
```

using the expected value rule for a function of a single random variable. Then, use the
rule for the special case of a linear function, to verify the formula

```math
E[aX + bY] = aE[X] + bE[Y].
```

<!-- ===== PDF p141 ===== -->
## <span style="color:#c0392b;">Problem 35 Solution（续）</span>

...where $a$ and $b$ are given scalars.

**Solution.** We use the total expectation theorem to reduce the problem to the case of
a single random variable. In particular, we have

```math
E[g(X, Y)] = \sum_y p_Y(y)\,E[g(X, Y) \mid Y = y]
```

```math
= \sum_y p_Y(y)\,E[g(X, y) \mid Y = y]
```

```math
= \sum_y \sum_x g(x, y)\,p_{X,Y}(x, y),
```

as desired. Note that the third equality above used the expected value rule for the
function of a single random variable $X$, i.e., for $g(X, y)$.

For the linear special case, the expected value rule gives

```math
E[aX + bY] = \sum_y \sum_x (ax + by)\,p_{X,Y}(x, y)
```

```math
= a \sum_x x \sum_y p_{X,Y}(x, y) \;+\; b \sum_y y \sum_x p_{X,Y}(x, y)
```

```math
= a \sum_x x\,p_X(x) \;+\; b \sum_y y\,p_Y(y)
```

```math
= aE[X] + bE[Y].
```

## <span style="color:#c0392b;">Problem 36</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 36.</span>* The multiplication rule for conditional PMFs. Let $X$, $Y$, and $Z$ be random variables.

(a) Show that

```math
p_{X,Y,Z}(x, y, z) = p_X(x)\,p_{Y \mid X}(y \mid x)\,p_{Z \mid X, Y}(z \mid x, y).
```

(b) How can we interpret this formula as a special case of the multiplication rule
given in Section 1.3?

(c) Generalize to the case of more than three random variables.

**Solution.** (a) We have

```math
p_{X,Y,Z}(x, y, z) = P(X = x, Y = y, Z = z)
```

```math
= P(X = x)\,P(Y = y, Z = z \mid X = x)
```

```math
= P(X = x)\,P(Y = y \mid X = x)\,P(Z = z \mid X = x, Y = y)
```

```math
= p_X(x)\,p_{Y \mid X}(y \mid x)\,p_{Z \mid X, Y}(z \mid x, y).
```

(b) The formula can be written as

```math
P(X = x, Y = y, Z = z) = P(X = x)\,P(Y = y \mid X = x)\,P(Z = z \mid X = x, Y = y),
```

<!-- ===== PDF p142 ===== -->
# <span style="color:#c0392b;">Discrete Random Variables</span>

*(续前页，第 2.6 节示例收尾)*

which is a special case of the multiplication rule.

**(c)** The generalization is

```math
P_{X_1,\ldots,X_n}(x_1,\ldots,x_n) \;=\; P_{X_1}(x_1)\;P_{X_2\mid X_1}(x_2\mid x_1)\cdots P_{X_n\mid X_1,\ldots,X_{n-1}}(x_n\mid x_1,\ldots,x_{n-1}).
```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 37.</span> *<span style="color:#c0392b;">Splitting a Poisson random variable.</span>* A transmitter sends out either a **1** with probability $p$ or a **0** with probability $1-p$, independent of earlier transmissions. If the number of transmissions within a given time interval has a Poisson PMF with parameter $\lambda$, show that the number of **1**s transmitted in that same time interval has a Poisson PMF with parameter $p\lambda$.

**Solution.** Let $X$ and $Y$ be the numbers of **1**s and **0**s transmitted, respectively. Let $Z = X + Y$ be the total number of symbols transmitted. We have

```math
\begin{aligned} P(X=n,\;Y=m) &= P(X=n,\;Y=m \mid Z = n+m)\,P(Z = n + m) \\ &= \binom{n+m}{n}p^{n}(1-p)^{m}\,\frac{e^{-\lambda}\lambda^{n+m}}{(n+m)!} \\ &= \frac{e^{-\lambda p}(\lambda p)^{n}}{n!}\,\frac{e^{-\lambda(1-p)}(\lambda(1-p))^{m}}{m!}. \end{aligned}
```

Thus,

```math
\begin{aligned} P(X=n) &= \sum_{m=0}^{\infty}P(X=n,\;Y=m) \\ &= \frac{e^{-\lambda p}(\lambda p)^{n}}{n!}\;e^{-\lambda(1-p)}\sum_{m=0}^{\infty}\frac{(\lambda(1-p))^{m}}{m!} \\ &= \frac{e^{-\lambda p}(\lambda p)^{n}}{n!}\;e^{-\lambda(1-p)}\,e^{\lambda(1-p)} \\ &= \frac{e^{-\lambda p}(\lambda p)^{n}}{n!}, \end{aligned}
```

so that $X$ is Poisson with parameter $\lambda p$.

---

## <span style="color:#c0392b;">SECTION 2.7. Independence</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 38.</span> Alice passes through four traffic lights on her way to work, and each light is equally likely to be green or red, independent of the others.

**(a)** What is the PMF, the mean, and the variance of the number of red lights that Alice encounters?

**(b)** Suppose that each red light delays Alice by exactly two minutes. What is the variance of Alice's commuting time?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 39.</span> Each morning, Hungry Harry eats some eggs. On any given morning, the number of eggs he eats is equally likely to be 2, 3, 4, 5, or 6, independent of every other morning. <span style="color:#7f8c8d;">[OCR 残缺：题面续至下一页]</span>

<!-- ===== PDF p143 ===== -->
## <span style="color:#c0392b;">Problems</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 39.</span> ... what he has done in the past. Let $X$ be the number of eggs that Harry eats in 10 days. Find the mean and variance of $X$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 40.</span> A particular professor is known for his arbitrary grading policies. Each paper receives a grade from the set $\{A,\ A^{-},\ B^{+},\ B,\ B^{-},\ C^{+}\}$, with equal probability, independent of other papers. How many papers do you expect to hand in before you receive each possible grade at least once?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 41.</span> You drive to work 5 days a week for a full year (50 weeks), and with probability $p = 0.02$ you get a traffic ticket on any given day, independent of other days. Let $X$ be the total number of tickets you get in the year.

(a) What is the probability that the number of tickets you get is exactly equal to the expected value of $X$?

(b) Calculate approximately the probability in (a) using a Poisson approximation.

(c) Any one of the tickets is \$10 or \$20 or \$50 with respective probabilities $0.5$, $0.3$, and $0.2$, and independent of other tickets. Find the mean and the variance of the amount of money you pay in traffic tickets during the year.

(d) Suppose you don't know the probability $p$ of getting a ticket, but you got 5 tickets during the year, and you estimate $p$ by the sample mean

```math
\hat{p} = \frac{5}{250} = 0.02.
```

What is the range of possible values of $p$ assuming that the difference between $\hat{p}$ and the sample mean $p$ is within 5 times the standard deviation of the sample mean?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 42.</span> Computational problem. Here is a probabilistic method for computing the area of a given subset $S$ of the unit square. The method uses a sequence of independent random selections of points in the unit square $[0,1] \times [0,1]$, according to a uniform probability law. If the $i$th point belongs to the subset $S$ the value of a random variable $X_i$ is set to $1$, and otherwise it is set to $0$. Let $X_1, X_2, \ldots$ be the sequence of random variables thus defined, and for any $n$, let

```math
S_n = \frac{X_1 + X_2 + \cdots + X_n}{n}.
```

(a) Show that $E[S_n]$ is equal to the area of the subset $S$, and that $\mathrm{var}(S_n)$ diminishes to $0$ as $n$ increases.

(b) Show that to calculate $S_n$, it is sufficient to know $S_{n-1}$ and $X_n$, so the past values of $X_k$, $k = 1, \ldots, n-1$, do not need to be remembered. Give a formula.

(c) Write a computer program to generate $S_n$ for $n = 1, 2, \ldots, 10000$, using the computer's random number generator, for the case where the subset $S$ is the circle inscribed within the unit square. How can you use your program to measure experimentally the value of $\pi$?

(d) Use a similar computer program to calculate approximately the area of the set of all $(x, y)$ that lie within the unit square and satisfy $0 \le \cos \pi x + \sin \pi y \le 1$.

<!-- ===== PDF p144 ===== -->
<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">Problem 43.</span> * Suppose that $X$ and $Y$ are independent, identically distributed, geometric random variables with parameter $p$. Show that

```math
P\{X = i \mid X + Y = n\} = \frac{1}{n - 1}, \qquad i = 1, \dots, n - 1.
```

**Solution.** Consider repeatedly and independently tossing a coin with probability of heads $p$. We can interpret $P\{X = i \mid X + Y = n\}$ as the probability that we obtained a head for the first time on the $i$th toss given that we obtained a head for the second time on the $n$th toss. We can then argue, intuitively, that given that the second head occurred on the $n$th toss, the first head is equally likely to have come up at any toss between $1$ and $n - 1$.

To establish this precisely, note that we have

```math
P\{X = i \mid X + Y = n\} = \frac{P\{X = i,\ X + Y = n\}}{P\{X + Y = n\}} = \frac{P\{X = i\}P\{Y = n - i\}}{P\{X + Y = n\}}.
```

Also

```math
P\{X = i\} = p(1 - p)^{i - 1}, \qquad \text{for } i \ge 1,
```

and

```math
P\{Y = n - i\} = p(1 - p)^{n - i - 1}, \qquad \text{for } n - i \ge 1.
```

It follows that

```math
P\{X = i\}P\{Y = n - i\} = \begin{cases} p^2 (1 - p)^{n - 2} & \text{if } i = 1, \dots, n - 1, \\ 0 & \text{otherwise.} \end{cases}
```

Therefore, for any $i$ and $j$ in the range $[1, n - 1]$, we have

```math
P\{X = i \mid X + Y = n\} = P\{X = j \mid X + Y = n\}.
```

Hence

```math
P\{X = i \mid X + Y = n\} = \frac{1}{n - 1}, \qquad i = 1, \dots, n - 1.
```

---

<span style="color:#2471a3;">**[problem]**</span>

<span style="color:#c0392b;">Problem 44.</span> * Let $X$ and $Y$ be two random variables with given joint PMF, and let $g$ and $h$ be two functions of $X$ and $Y$, respectively. Show that if $X$ and $Y$ are independent, then the same is true for the random variables $g(X)$ and $h(Y)$.

**Solution.** Let $U = g(X)$ and $V = h(Y)$. Then, we have

```math
P_{U,V}(u, v) = \sum_{\{(x, y) : g(x) = u,\ h(y) = v\}} P_{X,Y}(x, y) = \sum_{\{(x, y) : g(x) = u,\ h(y) = v\}} P_X(x)P_Y(y)
```

```math
= \left( \sum_{\{x : g(x) = u\}} P_X(x) \right) \left( \sum_{\{y : h(y) = v\}} P_Y(y) \right) = P_U(u)P_V(v),
```

so $U$ and $V$ are independent.

<!-- ===== PDF p145 ===== -->
## <span style="color:#c0392b;">Problems</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 45.\*</span> **Variability extremes.** Let $X_1,\ldots,X_n$ be independent random variables and let $X = X_1 + \cdots + X_n$ be their sum.

(a) Suppose that each $X_i$ is Bernoulli with parameter $p_i$, and that $p_1,\ldots,p_n$ are chosen so that the mean of $X$ is a given $\mu > 0$. Show that the variance of $X$ is maximized if the $p_i$ are chosen to be all equal to $\mu/n$.

(b) Suppose that each $X_i$ is geometric with parameter $p_i$, and that $p_1,\ldots,p_n$ are chosen so that the mean of $X$ is a given $\mu > 0$. Show that the variance of $X$ is minimized if the $p_i$ are chosen to be all equal to $n/\mu$. [Note the strikingly different character of the results of parts (a) and (b).]

<span style="color:#00838f;">**Solution.**</span> (a) We have

```math
\operatorname{var}(X) = \sum_{i=1}^n \operatorname{var}(X_i) = \sum_{i=1}^n p_i(1-p_i) = \mu - \sum_{i=1}^n p_i^2 .
```

Thus maximizing the variance is equivalent to minimizing $\sum_{i=1}^n p_i^2$. It can be seen (using the constraint $\sum_{i=1}^n p_i = \mu$) that

```math
\sum_{i=1}^n p_i^2 \ge \frac{1}{n}\Bigl(\sum_{i=1}^n p_i\Bigr)^2 = \frac{\mu^2}{n},
```

so $\sum_{i=1}^n p_i^2$ is minimized when $p_i = \mu/n$ for all $i$.

(b) We have

```math
\mu = \sum_{i=1}^n E[X_i] = \sum_{i=1}^n \frac{1}{p_i}
```

and

```math
\operatorname{var}(X) = \sum_{i=1}^n \operatorname{var}(X_i) = \sum_{i=1}^n \frac{1 - p_i}{p_i^2}.
```

Introducing the change of variables $Y_i = 1/p_i = E[X_i]$, we see that the constraint becomes

```math
\sum_{i=1}^n Y_i = \mu
```

and that we must minimize $\sum_{i=1}^n (Y_i^2 - Y_i) = \sum_{i=1}^n Y_i^2 - \mu$ subject to that constraint. This is the same problem as the one of part (a), so the method of proof given there applies.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">Problem 46.\*</span> **Entropy and uncertainty.** Consider a random variable $X$ that can take $n$ values $x_1,\ldots,x_n$, with corresponding probabilities $p_1,\ldots,p_n$. The entropy of $X$ is defined to be

```math
H(X) = -\sum_{i=1}^n p_i \log p_i .
```

<!-- ===== PDF p146 ===== -->
## 

<span style="color:#2471a3;">**[problem]**</span>
<span style="color:#c0392b;">Problem 46</span> (续) — *Entropy and uncertainty*.

(All logarithms in this problem are with respect to base two.) The entropy $H(X)$ provides a measure of the uncertainty about the value of $X$. To get a sense of this, note that $H(X) \ge 0$ and that $H(X)$ is very close to $0$ when $X$ is "nearly deterministic," i.e., takes one of its possible values with probability very close to $1$ (since we have $p\log p \approx 0$ if either $p \approx 0$ or $p \approx 1$).

The notion of entropy is fundamental in information theory, which originated with C. Shannon's famous work and is described in many specialized textbooks. For example, it can be shown that $H(X)$ is a lower bound to the average number of yes-no questions (such as "is $X = x_1$?" or "is $X < x_5$?") that must be asked in order to determine the value of $X$. Furthermore, if $k$ is the average number of questions required to determine the value of a string of independent identically distributed random variables $X_1, X_2, \ldots, X_n$, then, with a suitable strategy, $k/n$ can be made as close to $H(X)$ as desired, when $n$ is large.

(a) Show that if $q_1, \ldots, q_n$ are nonnegative numbers such that $\sum_{i=1}^n q_i = 1$, then

```math
H(X) \le -\sum_{i=1}^n p_i \log q_i,
```

with equality if and only if $p_i = q_i$ for all $i$. As a special case, show that $H(X) \le \log n$, with equality if and only if $p_i = 1/n$ for all $i$. Hint: Use the inequality $\ln Q \le Q - 1$, for $Q > 0$, which holds with equality if and only if $Q = 1$; here $\ln Q$ stands for the natural logarithm.

(b) Let $X$ and $Y$ be random variables taking a finite number of values, and having joint PMF $p_{X,Y}(x,y)$. Define

```math
I(X, Y) = \sum_x \sum_y p_{X,Y}(x , y) \log \frac{p_{X,Y}(x, y)}{p_X(x)\, p_Y(y)} .
```

Show that $I(X, Y) \ge 0$, and that $I(X, Y) = 0$ if and only if $X$ and $Y$ are independent.

(c) Show that

```math
I(X, Y) = H(X) + H(Y) - H(X, Y),
```

where

```math
H(X, Y) = - \sum_x \sum_y p_{X,Y}(x , y) \log p_{X,Y}(x, y),
\qquad
H(X) = - \sum_x p_X(x) \log p_X(x),
\qquad
H(Y) = - \sum_y p_Y(y) \log p_Y(y).
```

(d) Show that

```math
I(X, Y) = H(X) - H(X \mid Y),
```

where <span style="color:#7f8c8d;">[OCR 残缺：条件熵公式仅存零散下标，依据下方释义重建为 $H(X \mid Y) = \sum_y p_Y(y) H(X \mid Y = y)$，$H(X \mid Y = y) = - \sum_x p_{X \mid Y}(x \mid y) \log p_{X \mid Y}(x \mid y)$]</span>

[Note that $H(X \mid Y)$ may be viewed as the conditional entropy of $X$ given $Y$, that is, the entropy of the conditional distribution of $X$, given that $Y = y$, averaged over $y$.]

<!-- ===== PDF p147 ===== -->
<span style="color:#2471a3;">**[problem]**</span>（上接前一页 Problem 续）... over all possible values $y$. Thus, the quantity

```math
I(X, Y) = H(X) - H(X \mid Y)
```

is the reduction in the entropy (uncertainty) of $X$, when $Y$ becomes known. It can be therefore interpreted as the information about $X$ that is conveyed by $Y$, and is called the *mutual information* of $X$ and $Y$.

## <span style="color:#c0392b;">Solution</span>

**Solution.** We will use the inequality $\ln a \le a - 1$. (To see why this inequality is true, write

```math
\ln a = \int_1^a \beta^{-1}\,d\beta < \int_1^a d\beta = a - 1
```

for $a > 1$, and write

```math
\ln a = -\int_a^1 \beta^{-1}\,d\beta < -\int_a^1 d\beta = a - 1
```

for $0 < a < 1$.)

We have

```math
H(X) = -\sum_i p_i \log p_i \le -\sum_i p_i \log q_i,
```

with equality if and only if $p_i = q_i$ for all $i$. Since $\ln p = (\log p)\,\ln 2$, we obtain the desired relation

```math
H(X) \le -\sum_i p_i \log q_i.
```

The inequality $H(X) \le \log n$ is obtained by setting $q_i = \frac{1}{n}$ for all $i$.

**(b)** The numbers $p_X(x)\,p_Y(y)$ satisfy

```math
\sum_x \sum_y p_X(x)\,p_Y(y) = 1,
```

so by part (a), we have

```math
\sum_x \sum_y p_{X,Y}(x,y)\,\log\bigl(p_{X,Y}(x,y)\bigr) \ge \sum_x \sum_y p_{X,Y}(x,y)\,\log\bigl(p_X(x)\,p_Y(y)\bigr),
```

with equality if and only if

```math
p_{X,Y}(x,y) = p_X(x)\,p_Y(y)
```

for all $x$ and $y$, which is equivalent to $X$ and $Y$ being independent.

**(c)** We have

```math
I(X, Y) = \sum_x \sum_y p_{X,Y}(x,y)\,\log p_{X,Y}(x,y) - \sum_x \sum_y p_{X,Y}(x,y)\,\log\bigl(p_X(x)\,p_Y(y)\bigr),
```

and

```math
\sum_x \sum_y p_{X,Y}(x,y)\,\log p_{X,Y}(x,y) = -H(X, Y).
```

Also,

```math
\begin{aligned}
-\sum_x \sum_y p_{X,Y}(x,y)\,\log\bigl(p_X(x)\,p_Y(y)\bigr)
&= -\sum_x \sum_y p_{X,Y}(x,y)\,\log p_X(x) - \sum_x \sum_y p_{X,Y}(x,y)\,\log p_Y(y) \\
&= -\sum_x p_X(x)\,\log p_X(x) - \sum_y p_Y(y)\,\log p_Y(y) \\
&= H(X) + H(Y).
\end{aligned}
```

Combining the above three relations, we obtain

```math
I(X, Y) = H(X) + H(Y) - H(X, Y).
```

<!-- ===== PDF p148 ===== -->
##

<span style="color:#00838f;">**Solution.**</span> (continued)

**(d)** From the calculation in part (c), we have

```math
I(X;Y) \;=\; \sum_x \sum_y p_{X,Y}(x,y)\log p_{X,Y}(x,y) \;-\; \sum_x p_X(x)\log p_X(x) \;-\; \sum_x \sum_y p_{X,Y}(x,y)\log p_Y(y)
```

```math
=\; H(X) \;+\; \sum_x \sum_y p_{X,Y}(x,y)\log\left(\frac{p_{X,Y}(x,y)}{p_Y(y)}\right)
```

```math
=\; H(X) \;+\; \sum_y p_Y(y) \sum_x p_{X{\mid}Y}(x{\mid}y)\log p_{X{\mid}Y}(x {\mid} y)
```

```math
=\; H(X) \;-\; H(X {\mid} Y)\;.
```

<!-- ===== PDF p149 ===== -->
<span style="color:#c0392b;">**3**</span>

<span style="color:#c0392b;">**General Random Variables（一般随机变量）**</span>

<span style="color:#2471a3;">**[section]**</span> **Contents（目录）**

3.1 Continuous Random Variables and PDFs（连续随机变量与 PDF），见 p. 140
3.2 Cumulative Distribution Functions（累积分布函数），见 p. 148
3.3 Normal Random Variables（正态随机变量），见 p. 153
3.4 Joint PDFs of Multiple Random Variables（多元随机变量的联合 PDF），见 p. 158
3.5 Conditioning（条件作用），见 p. 164
3.6 The Continuous Bayes' Rule（连续贝叶斯公式），见 p. 178
3.7 Summary and Discussion（总结与讨论），见 p. 182
Problems（习题），见 p. 184

139

<!-- ===== PDF p150 ===== -->

# <span style="color:#c0392b;">第 3 章　General Random Variables（一般随机变量）</span>

具有连续取值范围的随机变量（random variables）相当常见；例如，沿高速公路行驶的车辆的速度就是一个例子。如果速度是用数字式速度表（digital speedometer）来测量的，那么我们可以把速度表的读数看作一个离散随机变量（discrete random variable）。但如果我们希望对精确速度进行建模，就需要用到连续随机变量（continuous random variable）。涉及连续随机变量的模型之所以有用，原因有几方面。除了颗粒度更细、可能更精确之外，它们还能利用来自微积分（calculus）的强大工具，并常常能给出在离散模型下不可能得到的、富有洞察力的分析。

第 2 章中引入的所有概念和方法，例如期望（expectation）、PMF 以及条件作用（conditioning），都有相应的连续版本。本章的主题就是建立并阐释这些对应版本。

---

## <span style="color:#c0392b;">3.1 连续随机变量与 PDF（Continuous Random Variables and PDFs）</span>

<span style="color:#2471a3;">**[definition]**</span>

连续随机变量（continuous random variable）与概率密度函数（probability density function）的定义如下：

<span style="color:#00838f;">一个随机变量 $X$ 被称为**连续的（continuous）**，如果存在一个非负函数 $f_X$，称为 $X$ 的概率密度函数（probability density function，简称为 **PDF**），使得</span>

```math
P(X \in B) = \int_B f_X(x) \, dx ,
```

<span style="color:#00838f;">对该实轴上（real line）每一个子集 $B$ 都成立。</span>

特别地，$X$ 的值落在某个区间内的概率为

```math
P(a < X < b) = \int_a^b f_X(x) \, dx,
```

它可被解释为 PDF 图像下方的面积（area under the graph of the PDF，见图 3.1）。

对于任何单个数值 $a$，我们都有 $P(X = a) = \int_a^a f_X(x) \, dx = 0$。因此，一个区间包含端点还是不包含端点，对其概率没有影响：

```math
P(a \le X \le b) = P(a < X \le b) = P(a \le X < b) = P(a < X < b) .
```

注意，要成为 PDF，一个函数 $f_X$ 必须是非负的（nonnegative），即对每个 $x$ 都有 $f_X(x) \ge 0$，而且必须满足规范化性质（normalization property）

```math
\int_{-\infty}^{\infty} f_X(x) \, dx = P(-\infty < X < \infty) = 1 .
```

---

> <span style="color:#1e8449;">**[note] 译者注:**</span> 这一页第一次告别"求和"改用积分定义 $P(X\in B)=\int_B f_X(x)dx$，把离散的 PMF 换成一枚连续的 PDF。第一性原理是"以密度计价"：$f_X$ 本身不是概率($P(X=a)=0$)，概率只来自"区间上曲线围出的面积"——正如 Strang 微积分里的"面积 = 高×宽的极限"，积分把无数细长条累加。所以 PDF 必须满足 $f_X\ge0$ 且 $\int_{-\infty}^{\infty}f_X=1$，这与 PMF 的"非负 + 总和为 1"完全同构，只是把求和换成积分。这里是你正在学的 100B 实分析的绝佳脚手架：目前这个 $\int$ 按黎曼(Riemann)积分理解(见脚注 t)，而当你想放开到任意"子集 $B$"、处理真正一般的密度时，就会滑向测度论里的勒贝格积分——那时 $f_X$ 会被重新解释为"概率测度关于勒贝格测度的 Radon–Nikodym 导数"，即密度本质上是一个"比例取极限"的比。教材强调分段连续 + 可数个不连续点，正是避开黎曼积分陷阱的充分条件，也是第 4 章做变量替换(雅可比公式)的可用前提。

脚注 t：

> <span style="color:#7f8c8d;">积分 $\int_B f_X(x) \, dx$ 应按照通常的微积分/黎曼（calculus/Riemann）意义来解释，并且我们隐含地假设它是良定义的（well-defined）。对于非常奇特的函数和集合，这个积分可能更难甚至根本无法定义，但这类问题属于对该主题更为深入处理的范畴。无论如何，令人欣慰的是，只要 $f_X$ 是一个分段连续的（piecewise continuous）函数，且其不连续点个数有限或可数（countable），并且 $B$ 是有限个或可数个区间的并集，那么这类数学上的微妙之处就不会出现。</span>
