<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 1 解答（Tutorial 1: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 9 月 16/17 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

<span style="color:#1e8449;">**[note]**</span> 本文件为 OCW「Tutorial 1: Solutions」解答版：题面见对应 Tutorial 题单，本文件仅含解答；解答中的事件记号沿用原文缩写。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> 若 $A\subset B$，则 $P(B\cap A)=P(A)$。但我们知道，要使 $A$ 与 $B$ 独立（independence，独立性），必须有 $P(B\cap A)=P(A)P(B)$。因此，$A$ 与 $B$ 独立当且仅当（if and only if）$P(B)=1$ 或 $P(A)=0$。例如，当 $B$ 为全集（universe，即整个样本空间）或 $A$ 为空集时，就会出现这种情况。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本题与教材（textbook）例 1.24（Example 1.24，第 40 页）性质类似。为了计算各 sub-system（子系统）的成功概率，我们利用该例中推导出的下面两条性质：
>
> - 若一个 serial（串联）子系统包含 $m$ 个成功概率分别为 $p_1,p_2,\ldots,p_m$ 的 component（部件），则整个子系统成功的概率为 $P(\text{whole system succeeds})=p_1p_2p_3\cdots p_m$；
> - 若一个 parallel（并联）子系统包含 $m$ 个成功概率分别为 $p_1,p_2,\ldots,p_m$ 的部件，则整个子系统成功的概率为 $P(\text{whole system succeeds})=1-(1-p_1)(1-p_2)(1-p_3)\cdots(1-p_m)$。
>
> 设 $P(X\to Y)$ 表示 node（节点）$X$ 与 $Y$ 之间 successful connection（成功接通）的概率。由于 $A\to C$、$C\to E$、$E\to B$ 三段为串联（in series），故
>
> ```math
> \begin{aligned}
> P(A\to B)&=P(A\to C)\,P(C\to E)\,P(E\to B),\\
> P(A\to C)&=p,\\
> P(C\to E)&=1-(1-p)\bigl(1-P(C\to D)\,P(D\to E)\bigr),\\
> P(E\to B)&=1-(1-p)^2.
> \end{aligned}
> ```
>
> 概率 $P(C\to D)$、$P(D\to E)$ 可同样算得：
>
> ```math
> P(C\to D)=1-(1-p)^3,\qquad P(D\to E)=p.
> ```
>
> 把各子系统的成功概率代入，即得整个系统成功的概率：
>
> ```math
> P(A\to B)=p\Bigl(1-(1-p)\Bigl(1-\bigl(1-(1-p)^3\bigr)p\Bigr)\Bigr)\Bigl(1-(1-p)^2\Bigr).
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 串联系统要成功，须每个部件都成功，故成功概率为各部件成功概率之积（用到独立性）；并联系统失败当且仅当所有支路同时失败，故成功概率为 $1-\prod_i(1-p_i)$。对整个网络自内向外逐层套用这两条性质即可。

---

<!-- ===== PDF p2 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3. The Chess Problem（国际象棋问题）**</span>

<span style="color:#1e8449;">**[note]**</span> 原文件此题仅含解答、未附题面；事件记号沿用原文缩写：2nd Rnd Req（需要进行第二轮）、Challenger（挑战者）、Champ（夺冠）、One Game（仅赛一局）。

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)**
>
> **i.** 事件「需要进行第二轮」（2nd Rnd Req）：
>
> ```math
> P(\text{2nd Rnd Req})=(0.6)^2+(0.4)^2=0.52.
> ```
>
> **ii.** 事件「Bo 赢得第一轮」（Bo Wins 1st Rnd）：
>
> ```math
> P(\text{Bo Wins 1st Rnd})=(0.6)^2=0.36.
> ```
>
> **iii.** 事件「Al 夺冠」（Al Champ）：
>
> ```math
> P(\text{Al Champ})=1-P(\text{Bo Champ})-P(\text{Ci Champ})=1-(0.6)^2\cdot(0.5)^2-(0.4)^2\cdot(0.3)^2=0.8956.
> ```
>
> **(b)**
>
> **i.**
>
> ```math
> P(\text{Bo Challenger}\mid \text{2nd Rnd Req})=\frac{(0.6)^2}{0.52}=\frac{0.36}{0.52}=0.6923.
> ```
>
> **ii.**
>
> ```math
> \begin{aligned}
> P(&\text{Al Champ}\mid \text{2nd Rnd Req})\\
> &=P(\text{Al Champ}\mid \text{Bo Challenger},\ \text{2nd Rnd Req})\times P(\text{Bo Challenger}\mid \text{2nd Rnd Req})\\
> &\quad+P(\text{Al Champ}\mid \text{Ci Challenger},\ \text{2nd Rnd Req})\times P(\text{Ci Challenger}\mid \text{2nd Rnd Req})\\
> &=\bigl(1-(0.5)^2\bigr)\times 0.6923+\bigl(1-(0.3)^2\bigr)\times 0.3077=0.7992.
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 这是按「挑战者是谁」对 $P(\text{Al Champ}\mid \text{2nd Rnd Req})$ 作 law of total probability（全概率定律）分解：在需要进行第二轮的条件下，挑战者为 Bo 的概率是 $0.6923$，为 Ci 的概率是 $1-0.6923=0.3077$；两种情形下 Al 最终夺冠的条件概率分别为 $1-(0.5)^2$ 与 $1-(0.3)^2$。
>
> **(c)** 在事件「需要进行第二轮」$\cap$「仅赛一局」（One Game）的条件下，Bo 是挑战者的概率：
>
> ```math
> P\bigl(\text{Bo Challenger}\mid\{\text{2nd Rnd Req}\}\cap\{\text{One Game}\}\bigr)=\frac{(0.6)^2\cdot(0.5)}{(0.6)^2\cdot(0.5)+(0.4)^2\cdot(0.7)}=\frac{(0.6)^2(0.5)}{0.2920}=0.6164.
> ```

---

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课件）　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关这些材料的引用方式或使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>
