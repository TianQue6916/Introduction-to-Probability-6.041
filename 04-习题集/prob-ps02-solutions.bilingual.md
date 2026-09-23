<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 2 解答（Problem Set 2: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；Due September 22, 2010，截止日期：2010 年 9 月 22 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 · 电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：预报说“有雨（Rain）”的概率为 $p$，随季节取值——冬季 $p=0.7$、夏季 $p=0.2$（(c) 中秋季与冬季相同）；预报报雨时实际下雨的概率为 0.8，报无雨时实际下雨的概率为 0.1。事件 $A$ = 预报为“有雨”，$B$ = 实际下雨。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 冬季的树图（tree representation）可以画成下图：
>
> <span style="color:#7f8c8d;">【图】原页此处为树图：根分两支——「The forecast is "Rain"（预报为“有雨”）」，概率 $p$，其下分 Rain（下雨）0.8 / No Rain（无雨）0.2；「The forecast is "No Rain"（预报为“无雨”）」，概率 $1-p$，其下分 Rain 0.1 / No Rain 0.9。原图由后处理统一插入。</span>
>
> 设 $A$ 为事件「预报为“有雨（Rain）”」，$B$ 为事件「天真的下了雨」，$p$ 为预报说“有雨”的概率。若是在冬季，则 $p = 0.7$，且
>
> ```math
> P(A \mid B) = \frac{P(B \mid A)\,P(A)}{P(B)} = \frac{(0.8)(0.7)}{(0.8)(0.7) + (0.1)(0.3)} = \frac{56}{59}
> ```
>
> 类似地，若是在夏季，则 $p = 0.2$，且
>
> ```math
> P(A \mid B) = \frac{P(B \mid A)\,P(A)}{P(B)} = \frac{(0.8)(0.2)}{(0.8)(0.2) + (0.1)(0.8)} = \frac{2}{3}
> ```
>
> (b) 设 $C$ 为事件「Victor 带了伞」，$D$ 为事件「预报为无雨」。此时的树图如下：
>
> <span style="color:#7f8c8d;">【图】原页此处为树图：根分「Saw the forecast（看到了预报）」0.8 与「Missed the forecast（错过了预报）」0.2 两支；看到预报时按预报结果分「Rain (umbrella)（报雨→带伞）」$p$ 与「No Rain (no umbrella)（报无雨→不带伞）」$1-p$；错过预报时分 Umbrella（带伞）0.5 / No umbrella（不带伞）0.5。原图由后处理统一插入。</span>
>
> $P(D) = 1 - p$；$P(C) = (0.8)p + (0.2)(0.5) = 0.8p + 0.1$；$P(C \mid D) = (0.8)(0) + (0.2)(0.5) = 0.1$。

<!-- ===== PDF p2 ===== -->

> **（续）** 因此，$P(C) = P(C \mid D)$ 当且仅当 $p = 0$。然而 $p$ 只能取 0.7 或 0.2，这说明事件 $C$ 与 $D$ 永远不可能相互独立（independence），且该结论与季节无关。
>
> (c) 我们先求「Victor 错过预报时下雨」的概率：
>
> ```math
> P(\text{actually rains} \mid \text{missed forecast}) = (0.8)p + (0.1)(1-p) = 0.1 + 0.7p
> ```
>
> 然后，我们可以把 (b) 中的树图扩展如下：
>
> <span style="color:#7f8c8d;">【图】原页此处为扩展树图：错过预报（0.2）分 Umbrella（带伞）0.5 / No umbrella（不带伞）0.5，每支再按实际下雨 $0.1+0.7p$ / 实际无雨 $0.9-0.7p$ 分支；看到预报（0.8）按预报分「Rain (umbrella)」$p$（再分实际有雨 0.8 / 实际无雨 0.2）与「No Rain (no umbrella)」$1-p$（再分实际有雨 0.1 / 实际无雨 0.9）；「带伞且未下雨」的两个分支为阴影。原图由后处理统一插入。</span>
>
> 因此，在已知「Victor 带着伞且没有下雨」的条件下，我们关注的是图中两个阴影分支：
>
> ```math
> P(\text{saw forecast} \mid \text{umbrella and not raining}) = \frac{(0.8)\,p\,(0.2)}{(0.8)\,p\,(0.2) + (0.2)(0.5)(0.9 - 0.7p)}
> ```
>
> 秋、冬季 $p = 0.7$，该概率为 $\dfrac{112}{153}$；春、夏季 $p = 0.2$，该概率为 $\dfrac{8}{27}$。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：两枚 5 面骰（点数 1–5）各掷一次，共 25 个等可能结果；事件 $A$ = 点数之和为 10，$B$ = 至少出现一个 5，$C$ = 至少出现一个 1，$D$ = 点数之和为 7（由条件样本可知），$E$ = 两点数相差 1（相邻），$F$ = 第二个点数大于第一个；各小问判断相应的条件概率/独立性。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a)
>
> i. 否（No）。样本空间中共有 25 个不同结果。要使总和为 10，两次都必须掷出 5，因此 $A \subset B$，且
>
> ```math
> P(B \mid A) = \frac{P(A \cap B)}{P(A)} = \frac{P(A)}{P(A)} = 1
> ```
>
> <span style="color:#7f8c8d;">【图】原页此处为 $5\times 5$ 网格图：横轴 Die 1、纵轴 Die 2（各 1–5 点），并在 $(5,5)$ 处标注「total is 10（和为 10）」。原图由后处理统一插入。</span>

<!-- ===== PDF p3 ===== -->

> **（续）** 我们观察到：要至少出现一个 5，可以是第一次掷出 5、第二次掷出 5、或两次都是 5，对应样本空间中 9 个不同结果。因此 $P(B) = \dfrac{9}{25} \ne P(B \mid A)$，故二者不独立。
>
> ii. 否（No）。已知事件 $A$，我们知道两次结果都必须是 5，因此事件 $C$（至少出现一个 1）不可能发生。形式化地说，$C$ 中有 9 个结果，即 $P(C) = \dfrac{9}{25}$，但是
>
> ```math
> P(C \mid A) = 0 \ne P(C)
> ```
>
> (b)
>
> i. 否（No）。在全部 25 个结果中，有 5 个结果对应两次点数相等；在其余 20 个结果中，一半是第二个数大于第一个数，另一半则相反。因此 $P(F) = \dfrac{10}{25}$。
>
> 属于事件 $E$ 的结果有八个：
> $E = \{(1, 2),\, (2, 3),\, (3, 4),\, (4, 5),\, (2, 1),\, (3, 2),\, (4, 3),\, (5, 4)\}$。
> 为求 $P(F \mid E)$，需要计算 $E$ 中「第二个数大于第一个数」的结果所占的比例：
>
> ```math
> P(F \mid E) = \frac{1}{2} \ne P(F) = \frac{10}{25}
> ```
>
> ii. 是（Yes）。以事件 $D$ 为条件，样本空间缩小为 4 个等可能的结果
> $\{(2, 5),\, (3, 4),\, (4, 3),\, (5, 2)\}$。容易看出
>
> ```math
> P(E \mid D) = \frac{2}{4} = \frac{1}{2},\qquad
> P(F \mid D) = \frac{2}{4} = \frac{1}{2},\qquad
> P(E \cap F \mid D) = \frac{1}{4} = P(E \mid D)\,P(F \mid D)
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：老式零件（old widgets）共 500 件、次品率 15%；新式零件（new widgets）共 1500 件、次品率 5%；以等概率（$1/2$）选定老/新类型后从中取出两件。(a) 求「两件皆为次品」的概率，(b) 在已知两件皆次品时求其来自老式的概率。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 假设我们选的是老式零件。在选取任何零件之前，共有 $500 \cdot 0.15 = 75$ 件次品老零件。取到两件次品零件的概率为
>
> ```math
> P(\text{two defective} \mid \text{old}) = P(\text{first is defective} \mid \text{old}) \cdot P(\text{second is defective} \mid \text{first is defective, old}) = \frac{75}{500}\cdot\frac{74}{499} = 0.02224
> ```
>
> 现在考虑新式零件。在选取任何零件之前，共有 $1500 \cdot 0.05 = 75$ 件次品新零件。与上面的计算类似，
>
> ```math
> P(\text{two defective} \mid \text{new}) = P(\text{first is defective} \mid \text{new}) \cdot P(\text{second is defective} \mid \text{first is defective, new}) = \frac{75}{1500}\cdot\frac{74}{1499} = 0.002568
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 末项数值按源 PDF 照录为 0.002568；按公式 $\frac{75}{1500}\cdot\frac{74}{1499}$ 精确计算应为 $\frac{5550}{2248500}\approx 0.002468$，原文应为笔误（后文 0.01240 与 0.8965 两处沿用该值，受影响幅度在小数点后第三位，结论不变）。

<!-- ===== PDF p4 ===== -->

> **（续）** 由全概率定律（total probability law），
>
> ```math
> P(\text{two defective}) = P(\text{old})\cdot P(\text{two defective} \mid \text{old}) + P(\text{new})\cdot P(\text{two defective} \mid \text{new}) = \frac{1}{2}\cdot 0.02224 + \frac{1}{2}\cdot 0.002568 = 0.01240
> ```
>
> 注意，这个数值非常接近于「忽略取走第一件次品对第二件选取的影响」时所得到的结果：
>
> ```math
> P(\text{two defective}) \approx \frac{1}{2}\cdot 0.15^2 + \frac{1}{2}\cdot 0.05^2 = 0.0125
> ```
>
> (b) 利用贝叶斯法则（Bayes' rule），
>
> ```math
> P(\text{old} \mid \text{two defective}) = \frac{P(\text{old})\cdot P(\text{two defective} \mid \text{old})}{P(\text{old})\cdot P(\text{two defective} \mid \text{old}) + P(\text{new})\cdot P(\text{two defective} \mid \text{new})} = \frac{\frac{1}{2}\cdot 0.02224}{\frac{1}{2}\cdot 0.02224 + \frac{1}{2}\cdot 0.002568} = 0.8965
> ```

<span style="color:#1e8449;">[note]</span> 原文在引入新式零件时误写为 "there are 1500·0.05 = 75 defective **old** widgets"，应为 defective **new** widgets（次品新零件）。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 4**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：狗以 0.4 的概率在森林 A、0.6 的概率在森林 B；在 A 中每天找到狗的条件概率为 0.25，在 B 中为 0.15；(c) 中 Oscar 每天以等概率（0.5）选择搜索的森林；(d) 涉及狗在第二天仍存活的概率 $1 - 1/3$。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a)
>
> ```math
> P(\text{find in A and in A}) = P(\text{in A}) \cdot P(\text{find in A} \mid \text{in A}) = 0.4 \cdot 0.25 = 0.1
> ```
>
> ```math
> P(\text{find in B and in B}) = P(\text{in B}) \cdot P(\text{find in B} \mid \text{in B}) = 0.6 \cdot 0.15 = 0.09
> ```
>
> Oscar 应当先在森林 A（Forest A）中搜索。
>
> (b) 利用贝叶斯法则（Bayes' Rule），
>
> ```math
> P(\text{in A} \mid \text{not find in A}) = \frac{P(\text{not find in A} \mid \text{in A})\cdot P(\text{in A})}{P(\text{not find in A} \mid \text{in A})\cdot P(\text{in A}) + P(\text{not find in A} \mid \text{in B})\cdot P(\text{in B})} = \frac{(0.75)\cdot(0.4)}{(0.4)\cdot(0.75) + (1)\cdot(0.6)} = \frac{1}{3}
> ```
>
> (c) 同样利用贝叶斯法则，
>
> ```math
> P(\text{looked in A} \mid \text{find dog}) = \frac{P(\text{find dog} \mid \text{looked in A})\cdot P(\text{looked in A})}{P(\text{find dog})} = \frac{(0.25)(0.4)(0.5)}{(0.25)(0.4)(0.5) + (0.15)(0.6)(0.5)} = \frac{10}{19}
> ```
>
> (d) 要让 Oscar 找到狗，必须：狗在森林 A 中、第一天没被找到、仍然存活、并且第二天被找到。注意这一计算需要「不同日子里没找到狗」与「狗保持存活」之间的条件独立性（conditional independence）。
>
> ```math
> P(\text{find live dog in A day 2}) = P(\text{in A}) \cdot P(\text{not find in A day 1} \mid \text{in A}) \cdot P(\text{alive day 2}) \cdot P(\text{find day 2} \mid \text{in A})
> ```
>
> ```math
> = 0.4 \cdot 0.75 \cdot \Bigl(1 - \frac{1}{3}\Bigr) \cdot 0.25 = 0.05
> ```

<!-- ===== PDF p5 ===== -->

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 5**</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 我们如下进行：
>
> ```math
> \begin{aligned}
> P\bigl(A \cap (B \cup C)\bigr) &= P\bigl((A \cap B) \cup (A \cap C)\bigr)\\
> &= P(A \cap B) + P(A \cap C) - P(A \cap B \cap C)\\
> &\stackrel{*}{=} P(A)P(B) + P(A)P(C) - P(A)P(B)P(C)\\
> &= P(A)\,\bigl[P(B) + P(C) - P(B)P(C)\bigr]\\
> &= P(A)\,P(B \cup C),
> \end{aligned}
> ```
>
> 其中带 $*$ 号的等号由 $A$、$B$、$C$ 的独立性（independence）得到。
>
> (b) 证明 1（Proof 1）：若 $A$ 与 $B$ 独立，则 $A^c$ 与 $B^c$ 也独立（证明见教材习题 1.43，第 63 页）。
>
> 对任意两个独立事件 $U$、$V$，德摩根定律（DeMorgan's Law）给出
>
> ```math
> P(U \cup V) = P\bigl((U^c \cap V^c)^c\bigr) = 1 - P(U^c \cap V^c) = 1 - P(U^c)\cdot P(V^c) = 1 - \bigl(1 - P(U)\bigr)\bigl(1 - P(V)\bigr)
> ```
>
> 我们用归纳法（induction）证明原命题。取 $U = A_1$、$V = A_2$，即证得基础情形。现在假设结论对某个 $n$ 成立，证明它对 $n+1$ 也成立。对于独立的 $\{A_1, \ldots, A_n, A_{n+1}\}$，令 $B = \bigcup_{i=1}^{n} A_i$。容易证明 $B$ 与 $A_{n+1}$ 独立。因此
>
> ```math
> P(A_1 \cup A_2 \cup \ldots \cup A_{n+1}) = 1 - \bigl(1 - P(B)\bigr)\cdot\bigl(1 - P(A_{n+1})\bigr) = 1 - \prod_{i=1}^{n+1}\bigl(1 - P(A_i)\bigr)
> ```
>
> 证毕。
>
> 证明 2（Proof 2）：或者，我们可以使用德摩根定律对 $n$ 个事件的形式：
>
> ```math
> P(A_1 \cup A_2 \cup \ldots \cup A_n) = P\bigl((A_1^c \cap A_2^c \cap \ldots \cap A_n^c)^c\bigr) = 1 - P(A_1^c \cap A_2^c \cap \ldots \cap A_n^c)
> ```
>
> 而 $A_1^c, A_2^c, \ldots, A_n^c$ 相互独立，因此
>
> ```math
> P(A_1 \cup A_2 \cup \ldots \cup A_n) = 1 - P(A_1^c)P(A_2^c)\ldots P(A_n^c) = 1 - \prod_{i=1}^{n}\bigl(1 - P(A_i)\bigr)
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**G1†**</span>

<span style="color:#7f8c8d;">（原解答未重述题干；由解答可知：Alice、Bob、Carol 三人进行如下比赛（tournament）——第一局由 Alice 对 Bob（Carol 轮空），此后每局由上一局的胜者对阵上一局轮空者；当上一局的胜者再度获胜时比赛结束（到达叶节点）；每局双方各以 $1/2$ 的概率获胜。）</span>

> <span style="color:#2471a3;">[solution]</span>
>
> (a) 下图用一棵无穷树（infinite tree）来描述样本空间。这棵树的叶节点恰好是所有有限的比赛历史（finite tournament histories）；此外，两条无穷路径代表两种可能的无限比赛历史。注意，第一局的胜者要么是 Alice，要么是 Bob；从那以后，一局的胜者要么是上一局的胜者（此时我们到达一个叶节点，比赛结束），要么是上一局轮空（sat out）的选手。样本空间的结果对应于各条有限历史（与树的叶节点一一对应）以及两条无限历史：
>
> ```math
> ACBACB\ldots \quad\text{与}\quad BCABCA\ldots
> ```

<!-- ===== PDF p6 ===== -->

> **（续）**
>
> <span style="color:#7f8c8d;">【图】原页此处为样本空间的无穷树图：根部按第一局胜者分 $A$、$B$ 两支，此后每个节点按「上一局胜者 / 上一局轮空者」继续分支（节点标注 $A$、$B$、$C$），并向深处延伸（…）。原图由后处理统一插入。</span>
>
> (b) 一个事件的概率是 $1/2^k$ 乘以该事件所包含的有限历史的条数（长度为 $k$ 的每条有限历史概率为 $1/2^k$）；由一条或两条无穷历史构成的事件概率为 0。我们要证明该概率律满足概率三公理（probability axioms）。显然它满足非负性（nonnegativity）与可加性（additivity）；为验证归一化（normalization），需要核实所有比赛历史的概率之和为 1。
>
> 首先注意，其中有两条历史是无穷的，概率为 0；其余每条历史都有某个有限的长度 $k \ge 2$（因而由上图树中深度为 $k$ 的两个叶节点之一表示），概率为 $1/2^k$。于是，把所有概率相加得
>
> ```math
> 2\cdot 0 + \sum_{k=2}^{\infty} 2\cdot\frac{1}{2^k} = \sum_{k=2}^{\infty}\frac{1}{2^{k-1}} = \sum_{k=0}^{\infty}\frac{1}{2^{k+1}} = \frac{1}{2}\sum_{k=0}^{\infty}\frac{1}{2^{k}} = \frac{1}{2}\cdot\frac{1}{1-1/2} = 1
> ```
>
> (c) 恰好进行 2 场比赛的概率是深度为 2 的两个叶节点概率之和，即
>
> ```math
> P(\text{exactly 2 games}) = \frac{1}{2^2} + \frac{1}{2^2} = \frac{1}{2}
> ```
>
> 类似地，恰好进行 $i$ 场比赛（$i = 3, 4, 5$）的概率为
>
> ```math
> P(\text{exactly 3 games}) = \frac{1}{2^3} + \frac{1}{2^3} = \frac{2}{2^3} = \frac{1}{4},\qquad
> P(\text{exactly 4 games}) = \frac{1}{2^4} + \frac{1}{2^4} = \frac{2}{2^4} = \frac{1}{8},\qquad
> P(\text{exactly 5 games}) = \frac{1}{2^5} + \frac{1}{2^5} = \frac{1}{16}
> ```
>
> 因此，比赛不超过 5 场的概率为
>
> ```math
> P(\text{at most 5 games}) = \frac{1}{2} + \frac{1}{4} + \frac{1}{8} + \frac{1}{16} = \frac{15}{16}
> ```
>
> 因此，比赛很可能进行到至多这个场数就结束了。
>
> Alice 赢得比赛的概率是树上标着「A」的叶节点概率之和，即
>
> ```math
> \Bigl(\frac{1}{2^2} + \frac{1}{2^5} + \frac{1}{2^8} + \cdots\Bigr) + \Bigl(\frac{1}{2^4} + \frac{1}{2^7} + \frac{1}{2^{10}} + \cdots\Bigr)
> ```
>
> 其中第一个求和涵盖树上半部分的所有叶节点，第二个求和对应下半部分的叶节点。计算得
>
> ```math
> \frac{1}{4}\Bigl(1 + \frac{1}{8} + \frac{1}{8^2} + \cdots\Bigr) + \frac{1}{16}\Bigl(1 + \frac{1}{8} + \frac{1}{8^2} + \cdots\Bigr) = \frac{5}{16}\cdot\frac{1}{1-1/8} = \frac{5}{14}
> ```

<!-- ===== PDF p7 ===== -->

> **（续）** 由对称性（注意 Alice 获胜的那些历史与 Bob 获胜的那些历史之间的对应关系），Bob 获胜的概率同样是 $\dfrac{5}{14}$。于是，由于「无人获胜」的结果（即两条无穷比赛历史）的总概率为 0，Carol 获胜的概率为 $1 - \dfrac{5}{14} - \dfrac{5}{14} = \dfrac{4}{14}$。因此，没有参加第一局的 Carol，进入比赛时就带着劣势。

<span style="color:#7f8c8d;">† 对 6.431 为必做（Required）；对 6.041 为选做（optional）。</span>

<!-- ===== PDF p8 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 尾页：6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010，http://ocw.mit.edu/terms —— 无实质题目内容。）</span>
