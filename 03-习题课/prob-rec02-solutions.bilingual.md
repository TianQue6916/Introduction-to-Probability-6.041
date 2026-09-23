<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 2 解答（Recitation 2: Solutions）**</span> <span style="color:#7f8c8d;">（September 14, 2010，2010 年 9 月 14 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $A$ 为“第一次抛掷是正面”这一事件，$B$ 为“第二次抛掷是正面”这一事件。我们必须比较条件概率（conditional probabilities）$P(A\cap B\mid A)$ 与 $P(A\cap B\mid A\cup B)$。我们有
>
> ```math
> P(A\cap B\mid A)=\frac{P\big((A\cap B)\cap A\big)}{P(A)}=\frac{P(A\cap B)}{P(A)},
> ```
>
> 以及
>
> ```math
> P(A\cap B\mid A\cup B)=\frac{P\big((A\cap B)\cap(A\cup B)\big)}{P(A\cup B)}=\frac{P(A\cap B)}{P(A\cup B)}.
> ```
>
> 由于 $P(A\cup B)\ge P(A)$，上面的第一个条件概率至少与第二个一样大，所以无论硬币是否公平，Alice 都是对的。在硬币公平的情形下，即四个结果 HH、HT、TH、TT 等可能时，我们有
>
> ```math
> \frac{P(A\cap B)}{P(A)}=\frac{1/4}{1/2}=\frac{1}{2},
> \qquad
> \frac{P(A\cap B)}{P(A\cup B)}=\frac{1/4}{3/4}=\frac{1}{3}.
> ```
>
> Alice 推理的一个推广是：若 $A$、$B$、$C$ 是满足 $B\subset C$ 且 $A\cap B=A\cap C$ 的事件（例如 $A\subset B\subset C$），那么在已知 $B$ 发生的条件下，事件 $A$ 的可能性不小于在已知 $C$ 发生的条件下的可能性。Alice 的推理正对应 $C=A\cup B$ 的特例。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 每个可能结果的概率为 $1/36$。是“对子”（doubles，两骰点数相同）的可能结果有 6 种，所以掷出对子的概率为 $6/36=1/6$。
>
> **(b)** 条件事件“点数之和不超过 4”由 6 个结果 $\{(1,1),\,(1,2),\,(1,3),\,(2,1),\,(2,2),\,(3,1)\}$ 组成，其中 2 个是对子，所以对子的条件概率为 $2/6=1/3$。
>
>
> **(c)** 含有至少一个 6 的可能结果共有 11 种，即 $(6,6)$、$(6,i)$ 与 $(i,6)$，$i=1,2,\ldots,5$。因此至少有一枚骰子是 6 的概率为 $11/36$。
>
> **(d)** 两枚骰子落在不同点数上的可能结果共有 30 种。其中至少有一次掷出 6 的结果有 10 种。因此所求条件概率为 $10/30=1/3$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 见教材（textbook）例 1.13（Example 1.13），第 29 页。
>
> **(b)** 见教材例 1.17（Example 1.17），第 33 页。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">**[solution]**</span> 见教材例 1.12（Example 1.12，即蒙提霍尔问题 / The Monty Hall Problem），第 27 页。另一种解法如下：
>
> 设 $P_i$ 表示奖品在门 $i$ 后面的事件，$C_i$ 表示你最初选择门 $i$ 的事件，$O_i$ 表示你的朋友打开门 $i$ 的事件。对应的概率树（probability tree）为：

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">【图】原页此处为 Problem 4（Monty Hall 问题）的完整概率树（probability tree）：第一层为奖品所在门 $P_1,P_2,P_3$（分支标注 $P(P_i)$）；第二层为你初选的门 $C_1,C_2,C_3$（在给定 $P_i$ 的条件下展开，分支标注 $P(C_i\mid P_j)$）；第三层为朋友打开的门 $O_1,O_2,O_3$（分支标注 $P(O_k\mid P_i\cap C_j)$）。原图由后处理统一插入。</span>

<!-- ===== PDF p3 ===== -->

**（续）** Problem 4（解答续）

> **(a)** 不从初选中换门时的获胜概率，就是奖品在你最初所选门后面的概率：
>
> ```math
> \begin{aligned}
> P(\text{Win when not switching})
> &=P(P_1\cap C_1)+P(P_2\cap C_2)+P(P_3\cap C_3)\\
> &=P(P_1)P(C_1\mid P_1)+P(P_2)P(C_2\mid P_2)+P(P_3)P(C_3\mid P_3)\\
> &=P(P_1)P(C_1)+P(P_2)P(C_2)+P(P_3)P(C_3)\\
> &=\frac{1}{3}\cdot\big(P(C_1)+P(C_2)+P(C_3)\big)=\frac{1}{3}
> \end{aligned}
> ```
>
> **(b)** 从初选中换门时的获胜概率，就是奖品在剩下那扇（未打开的）门后面的概率：
>
> ```math
> \begin{aligned}
> P(\text{Win when switching})
> &=P(P_1\cap C_2\cap O_3)+P(P_1\cap C_3\cap O_2)+P(P_2\cap C_1\cap O_3)\\
> &\quad+P(P_2\cap C_3\cap O_1)+P(P_3\cap C_1\cap O_2)+P(P_3\cap C_2\cap O_1)\\
> &=P(P_1\cap C_2)+P(P_1\cap C_3)+P(P_2\cap C_1)+P(P_2\cap C_3)\\
> &\quad+P(P_3\cap C_1)+P(P_3\cap C_2)\\
> &=P(P_1)P(C_2)+P(P_1)P(C_3)+P(P_2)P(C_1)+P(P_2)P(C_3)\\
> &\quad+P(P_3)P(C_1)+P(P_3)P(C_2)\\
> &=\frac{2}{3}\cdot\big(P(C_1)+P(C_2)+P(C_3)\big)=\frac{2}{3}
> \end{aligned}
> ```
>
> **(c)** 给定 $C_1$（你第一次选门 1），采用“仅当门 3 被打开时才换门”的新策略，则当奖品在门 1 后且门 2 被打开，或奖品在门 2 后且门 3 被打开时，你获胜。
>
> ```math
> \begin{aligned}
> P(\text{Win with new strategy}\mid C_1)
> &=P(P_1\cap O_2\mid C_1)+P(P_2\cap O_3\mid C_1)\\
> &=P(P_1\mid C_1)P(O_2\mid P_1\cap C_1)+P(P_2\mid C_1)P(O_3\mid P_2\cap C_1)\\
> &=P(P_1)P(O_2\mid P_1\cap C_1)+P(P_2)P(O_3\mid P_2\cap C_1)\\
> &=\frac{1}{3}\cdot P(O_2\mid P_1\cap C_1)+\frac{1}{3}\cdot 1\\
> &=\frac{1}{3}\cdot\big(P(O_2\mid P_1\cap C_1)+1\big)
> \end{aligned}
> ```
>
> 在初选为门 1 的条件下，此新策略下的获胜概率取决于：当奖品也位于门 1 后面时，你的朋友如何在门 2 与门 3 之间决定开哪一扇。若他总开门 2，则 $P(O_2\mid P_1\cap C_1)=1$，且 $P(\text{Win with new strategy}\mid C_1)=2/3$。若他以相等概率在门 2 与门 3 之间选择，则 $P(O_2\mid P_1\cap C_1)=1/2$，且 $P(\text{Win with new strategy}\mid C_1)=1/2$。

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms</span>
