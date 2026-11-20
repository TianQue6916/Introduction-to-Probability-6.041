<!-- ===== PDF p1 ===== -->
<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>
<span style="color:#c0392b;">**Recitation 3 解答（Recitation 3: Solutions）**</span> <span style="color:#7f8c8d;">（September 16, 2010，2010 年 9 月 16 日）</span>
<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>
---
<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>
> <span style="color:#2471a3;">**[solution]**</span> 见教材（textbook）例 1.20（Example 1.20），第 37 页。为便于读者不翻教材也能读通，此处补全该例题的题目与解答。
>
> **例 1.20（题目）** 考虑两次独立的公平抛硬币（fair coin toss，即正、反面各以概率 $1/2$ 出现），四种可能结果 $HH,\ HT,\ TH,\ TT$ 等可能，各为 $\tfrac{1}{4}$。记 $H_1=\{\text{第一次抛得正面}\}$，$H_2=\{\text{第二次抛得正面}\}$，$D=\{\text{两次抛得结果不同}\}$。
>
> **(a)** 事件 $H_1$ 与 $H_2$ 是否（无条件地）独立（independent）？
>
> **(b)** 已知事件 $D$ 已发生，$H_1$ 与 $H_2$ 是否条件独立（conditionally independent）？
>
> **例 1.20（解答）** 先说明记号：$P(A\mid B)$ 表示「在 $B$ 已发生的条件下，$A$ 发生的概率」，称为条件概率（conditional probability），其定义为 $P(A\mid B)=\dfrac{P(A\cap B)}{P(B)}$（当 $P(B)>0$）。两个事件 $X$、$Y$ 独立是指 $P(X\cap Y)=P(X)P(Y)$；而两个事件 $X$、$Y$ 在给定事件 $C$（$P(C)>0$）的条件下独立，是指 $P(X\cap Y\mid C)=P(X\mid C)\,P(Y\mid C)$。
>
> **(a)** $P(H_1)=P(H_2)=\tfrac{1}{2}$，且 $P(H_1\cap H_2)=P(\{HH\})=\tfrac{1}{4}=P(H_1)P(H_2)$，故 $H_1$ 与 $H_2$ 独立。
>
> **(b)** $D=\{HT,TH\}$，故 $P(D)=\tfrac{1}{2}$。给定 $D$ 后，$P(H_1\mid D)=\tfrac{1}{2}$、$P(H_2\mid D)=\tfrac{1}{2}$，但 $P(H_1\cap H_2\mid D)=0$（因为 $H_1\cap H_2=\{HH\}$ 与 $D$ 不相交）。于是 $P(H_1\cap H_2\mid D)\ne P(H_1\mid D)\,P(H_2\mid D)$，故 $H_1$ 与 $H_2$ 在给定 $D$ 时不条件独立。
---
<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>
> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 要在两步之后回到原处，走钢丝者（tightrope walker）可以先向前一步再向后一步，或者反之。因此所求概率为
>
> ```math
> 2\cdot p\cdot(1-p).
> ```
>
> **(b)** 三步之后他比起点前移一步的概率，等于在总共 3 步中有 2 步向前、1 步向后的概率。该概率为
>
> ```math
> 3\cdot p^{2}\cdot(1-p).
> ```
>
> **(c)** 已知他的三步中只有一步向后，该实验的样本空间（sample space，即该随机实验所有可能结果的集合）为
>
> ```math
> \{(F,F,B),\ (F,B,F),\ (B,F,F)\},
> ```
>
> 其中 $F$ 表示向前一步，$B$ 表示向后一步。这些样本点（sample point，即样本空间中的单个结果）中每一个都是等可能的，因此他的第一步是向前一步的概率为 $\dfrac{2}{3}$。
---
<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>
> <span style="color:#2471a3;">**[solution]**</span> 见教材习题 1.31（Problem 1.31），第 60 页。为便于读者不翻教材也能读通，此处补全该习题的题目与解答。
>
> **习题 1.31（题目）** 通过有噪声信道进行通信（Communication through a noisy channel）。一个二进制（0 或 1）消息通过有噪声的信道传输：符号 0 被错误接收（错成 1）的概率为 $\epsilon_0$，符号 1 被错误接收（错成 0）的概率为 $\epsilon_1$。不同符号传输中发生的错误相互独立。信源（channel source）以概率 $p$ 发送 0，以概率 $1-p$ 发送 1。
>
> **(a)** 一个随机选中的符号被正确接收的概率是多少？
>
> **(b)** 假设传输的符号串为 1011，求其中所有符号都被正确接收的概率。
>
> **(c)** 为提高可靠性，每个符号重复传输 3 次，接收端按多数表决（majority rule）解码：即 0（或 1）被传输为 000（或 111），接收端收到的三符号串中 0（或 1）的个数不少于 2 时，才解码为 0（或 1）。求一个被传输的 0 被正确解码的概率。
>
> **(d)** 沿用 (c) 的方案，已知收到的字符串为 101，求「原始传输的是 0」的概率。
>
> **习题 1.31（解答）**
>
> **(a)** 正确接收 =「发送 0 且被正确接收」或「发送 1 且被正确接收」，二者互斥，故所求概率为
>
> ```math
> p\,(1-\epsilon_0)+(1-p)\,(1-\epsilon_1).
> ```
>
> **(b)** 串 1011 依次是符号 1、0、1、1，各符号独立且各自正确接收的概率分别为 $1-\epsilon_1$、$1-\epsilon_0$、$1-\epsilon_1$、$1-\epsilon_1$，故所求概率为
>
> ```math
> (1-\epsilon_1)\,(1-\epsilon_0)\,(1-\epsilon_1)\,(1-\epsilon_1)=(1-\epsilon_0)\,(1-\epsilon_1)^{3}.
> ```
>
> **(c)** 0 被传输为 000。按多数表决，它被正确解码当且仅当 3 个接收位中出错不超过 1 个（否则 1 的个数 $\ge 2$，会解码成 1）。每个位独立出错、错成 1 的概率都是 $\epsilon_0$，故正确解码的概率为「0 个错」加「1 个错」：
>
> ```math
> (1-\epsilon_0)^{3}+3\,(1-\epsilon_0)^{2}\,\epsilon_0.
> ```
>
> **(d)** 用贝叶斯规则（Bayes' rule）。已知收到 101，求发送 0 的后验概率。发送 0（即 000）时收到 101，意味着第 1、3 位出错（各 $\epsilon_0$）、第 2 位正确（$1-\epsilon_0$），故 $P(101\mid 0)=\epsilon_0\,(1-\epsilon_0)\,\epsilon_0=\epsilon_0^{2}(1-\epsilon_0)$；发送 1（即 111）时收到 101，意味着第 1、3 位正确（各 $1-\epsilon_1$）、第 2 位出错（$\epsilon_1$），故 $P(101\mid 1)=(1-\epsilon_1)\,\epsilon_1\,(1-\epsilon_1)=(1-\epsilon_1)^{2}\epsilon_1$。于是
>
> ```math
> P(0\mid 101)=\frac{p\,\epsilon_0^{2}\,(1-\epsilon_0)}{p\,\epsilon_0^{2}\,(1-\epsilon_0)+(1-p)\,(1-\epsilon_1)^{2}\,\epsilon_1}.
> ```
---
<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>
> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 先回顾定义：两个事件 $X$、$Y$ 独立（independent）是指它们同时发生的概率等于各自概率的乘积，即 $P(X\cap Y)=P(X)\,P(Y)$。据此，事件 $A$ 与其自身独立，当且仅当 $P(A\cap A)=P(A)P(A)$。由于 $A\cap A=A$，故 $A$ 必须满足 $P(A)=\big(P(A)\big)^{2}$。因此，当且仅当 $P(A)=1$ 或 $P(A)=0$ 时，$A$ 与其自身独立。
>
> **(b)** 见教材第 63–64 页习题 1.43(a)（Problem 1.43(a)）的解答。为便于读者不翻教材也能读通，此处补全题目与解答。
>
> **习题 1.43(a)（题目）** 设 $A$、$B$ 为独立事件。利用独立的定义证明：事件 $A$ 与 $B^{c}$（$B$ 的补事件）也独立。
>
> **习题 1.43(a)（解答）** 事件 $A$ 是不相交事件 $A\cap B^{c}$ 与 $A\cap B$ 的并。由概率的可加性（additivity）以及 $A$、$B$ 的独立性，
>
> ```math
> P(A)=P(A\cap B^{c})+P(A\cap B)=P(A\cap B^{c})+P(A)\,P(B).
> ```
>
> 由此移项得
>
> ```math
> P(A\cap B^{c})=P(A)-P(A)\,P(B)=P(A)\,\big(1-P(B)\big)=P(A)\,P(B^{c}),
> ```
>
> 故 $A$ 与 $B^{c}$ 独立。
>
> **(c)** 见教材第 64 页习题 1.44（Problem 1.44）的解答。为便于读者不翻教材也能读通，此处补全题目与解答。
>
> **习题 1.44（题目）** 设 $A$、$B$、$C$ 为独立事件，且 $P(C)>0$。证明：$A$ 与 $B$ 在给定 $C$ 时条件独立（conditionally independent）。
>
> **习题 1.44（解答）** 由条件概率定义、三事件独立性以及 $A$、$B$ 分别与 $C$ 独立，
>
> ```math
> P(A\cap B\mid C)=\frac{P(A\cap B\cap C)}{P(C)}=\frac{P(A)\,P(B)\,P(C)}{P(C)}=P(A)\,P(B).
> ```
>
> 同时
>
> ```math
> P(A\mid C)=\frac{P(A\cap C)}{P(C)}=\frac{P(A)\,P(C)}{P(C)}=P(A),\qquad P(B\mid C)=\frac{P(B\cap C)}{P(C)}=\frac{P(B)\,P(C)}{P(C)}=P(B).
> ```
>
> 因此 $P(A\cap B\mid C)=P(A)\,P(B)=P(A\mid C)\,P(B\mid C)$，故 $A$ 与 $B$ 在给定 $C$ 时条件独立。
<!-- ===== PDF p2 ===== -->
<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>
<span style="color:#7f8c8d;">6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）</span>
<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms</span>
