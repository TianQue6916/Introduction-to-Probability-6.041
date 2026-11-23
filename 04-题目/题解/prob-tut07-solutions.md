<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 7 解答（Tutorial 7: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期 · MIT 电气工程与计算机科学系 Department of Electrical Engineering &amp; Computer Science）</span>

<span style="color:#1e8449;">**[note]**</span> <span style="color:#7f8c8d;">原始 PDF 仅含解答文本，题面见课程发布的 Tutorial 7 题目页；本文件对解答内容做完整行内双语翻译。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 每一轮（round）中，Alice 与 Bob 同时输的概率为 $\frac{1}{3}\cdot\frac{1}{3}=\frac{1}{9}$。设随机变量（random variable）$X$ 表示直到两人首次同时输为止所进行的总轮数，则 $X$ 是参数 $p=1/9$ 的几何随机变量（geometric random variable），其 PMF（概率质量函数，probability mass function）为
>
> ```math
> p_X(x)=(1-p)^{x-1}p=\left(\frac{8}{9}\right)^{x-1}\frac{1}{9},\qquad x=1,2,\ldots
> ```
>
> **(b)** 首先考虑 Bob 直到第三次输为止所玩的局数（number of games）$K_3$。$K_3$ 是帕斯卡随机变量（Pascal random variable），其 PMF 为
>
> ```math
> p_{K_3}(k)=\binom{k-1}{3-1}\left(\frac{1}{3}\right)^{3}\left(\frac{2}{3}\right)^{k-3},\qquad k=3,4,5,\cdots
> ```
>
> 在本问中，我们关心另一个随机变量 $Z$，它定义为 Bob 第三次输发生的时刻（time）。注意 $Z=2K_3$。经变量代换（changing variables），得到
>
> ```math
> p_Z(z)=\binom{z/2-1}{3-1}\left(\frac{1}{3}\right)^{3}\left(\frac{2}{3}\right)^{z/2-3},\qquad z=6,8,10,\cdots
> ```
>
> **(c)** 设 $A$ 为「Alice 获胜」事件，$B$ 为「Bob 获胜」事件。事件 $A\cup B$ 即「$A$ 获胜、或 $B$ 获胜、或两者都获胜」的事件，事件 $A\cap B$ 即「两者都获胜」的事件。假设我们观察这一赌博（gambling）过程，并设 $U$ 为直到至少一人获胜为止我们观察到的轮数。$U$ 是参数 $p=P(A\cup B)=1-\frac{1}{3}\cdot\frac{1}{3}=\frac{8}{9}$ 的几何随机变量。
>
> 再考虑另一个随机变量 $V$，表示直到另一人也获胜为止我们还须观察的额外轮数。若 Alice 与 Bob 在第 $U$ 轮同时获胜，则 $V=0$；这以概率 $P(A\cap B\mid A\cup B)=\dfrac{(2/3)(2/3)}{8/9}$ 发生。若 Alice 在第 $U$ 轮获胜，则直到 Bob 获胜的时间 $V$ 是参数 $p=1/2+1/6=2/3$ 的几何随机变量；这以概率 $P(A\cap B^c\mid A\cup B)=\dfrac{(2/3)(1/3)}{8/9}$ 发生。同理，若 Bob 在第 $U$ 轮获胜，则直到 Alice 获胜的时间 $V$ 是参数 $p=1/2+1/6=2/3$ 的几何随机变量；这以概率 $P(B\cap A^c\mid A\cup B)=\dfrac{(2/3)(1/3)}{8/9}$ 发生。直到两人各自都至少获胜过一次的轮数 $N$ 满足
>
> ```math
> N=U+V
> ```
>
> 于是 $N$ 的期望为：
>
> ```math
> \begin{aligned}
> E[N]&=E[U]+E[V]\\
> &=\frac{1}{8/9}+0\cdot P(A\cap B\mid A\cup B)+\frac{1}{2/3}\,P(A\cap B^c\mid A\cup B)+\frac{1}{2/3}\,P(B\cap A^c\mid A\cup B)\\
> &=\frac{9}{8}+\frac{(2/3)(1/3)}{8/9}\cdot\frac{3}{2}+\frac{(2/3)(1/3)}{8/9}\cdot\frac{3}{2}=\frac{15}{8}
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> $\dfrac{(2/3)(2/3)}{8/9}=\dfrac{1}{2}$，$\dfrac{(2/3)(1/3)}{8/9}=\dfrac{1}{4}$：三种情形的概率分别为 $1/2$、$1/4$、$1/4$，恰好归一。

<!-- ===== PDF p2 ===== -->

**（续）**

> 本题另有如下解法。考虑下述分割（partition）：
>
> - $A_1$：第一轮两人都赢（both win first round）
> - $A_2$：仅 Alice 赢第一轮（Only Alice wins first round）
> - $A_3$：仅 Bob 赢第一轮（Only Bob wins first round）
> - $A_4$：第一轮两人都输（both lose first round）
>
> 事件 $A_1$ 以概率 $\frac{2}{3}\cdot\frac{2}{3}$ 发生；事件 $A_2$ 以概率 $\frac{2}{3}\cdot\frac{1}{3}$ 发生；事件 $A_3$ 以概率 $\frac{1}{3}\cdot\frac{2}{3}$ 发生；事件 $A_4$ 以概率 $\frac{1}{3}\cdot\frac{1}{3}$ 发生。当事件 $A_2$（$A_3$）发生时，直到 Bob（Alice）获胜所需时间的分布是均值为 $\frac{1}{2/3}$ 的几何随机变量。当事件 $A_4$ 发生时，由重新开始性质（fresh-start property），Alice 与 Bob 获胜所需的附加时间与时刻 0 时的分布完全相同。由全期望定理（total expectation theorem），
>
> ```math
> \begin{aligned}
> E[N]&=E[N\mid A_1]P(A_1)+E[N\mid A_2]P(A_2)+E[N\mid A_3]P(A_3)+E[N\mid A_4]P(A_4)\\
> &=1\cdot\frac{2}{3}\cdot\frac{2}{3}+\left(1+\frac{3}{2}\right)\cdot\frac{2}{3}\cdot\frac{1}{3}+\left(1+\frac{3}{2}\right)\cdot\frac{1}{3}\cdot\frac{2}{3}+(1+E[N])\cdot\frac{1}{3}\cdot\frac{1}{3}
> \end{aligned}
> ```
>
> 解出 $E[N]$，得 $E[N]=\dfrac{15}{8}$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本题即教材（textbook）第 328 页的 Problem 6.6；解答见教材（see text for solutions）。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#1e8449;">**[note]**</span> <span style="color:#7f8c8d;">由解答中「参数 $3\lambda=9$」可知，本题中火车按每天 $\lambda=3$ 列的泊松过程到达。</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 第 1、2、3 天到达的火车数与第 0 天到达的火车数相互独立。设 $N$ 为第 1、2、3 天到达的火车总数，则 $N$ 是参数为 $3\lambda=9$ 的泊松随机变量（Poisson random variable），于是
>
> ```math
> P(\text{第 1、2、3 天无火车}\mid\text{第 1 天恰有一列火车})=P(\text{第 1、2、3 天无火车})=P(N=0)=\frac{e^{-9}9^0}{0!}=e^{-9}.
> ```
>
> **(b)** 「下一列火车在第 0 天火车到达之后超过三天才到达」这一事件，等价于「第 0 天火车到达后的三天内到达数为零」这一事件。因此所求概率与 (a) 中所得相同，即 $e^{-9}$。
>
> **(c)** 前 2 天到达的火车数与第 4 天到达的火车数相互独立。因此
>
> ```math
> \begin{aligned}
> &P(\text{前 2 天 0 列火车且第 4 天 4 列火车})\\
> &\quad=P(\text{前 2 天 0 列火车})\cdot P(\text{第 4 天 4 列火车})
> =\frac{e^{-2\lambda}(2\lambda)^0}{0!}\cdot\frac{e^{-\lambda}\lambda^4}{4!}
> =\frac{3^4}{4!}\,e^{-9}.
> \end{aligned}
> ```

<!-- ===== PDF p3 ===== -->

**（续）**

> **(d)** 「第 5 次到达需要超过 2 天」这一事件，等价于「前 2 天内至多有 4 次到达」这一事件。因此所求概率等于
>
> ```math
> \sum_{k=0}^{4}P(\text{前 2 天恰有 }k\text{ 次到达})=\sum_{k=0}^{4}e^{-2\lambda}\frac{(2\lambda)^k}{k!}
> ```
>
> ```math
> =e^{-6}\left(\frac{(2\lambda)^0}{0!}+\frac{(2\lambda)^1}{1!}+\frac{(2\lambda)^2}{2!}+\frac{(2\lambda)^3}{3!}+\frac{(2\lambda)^4}{4!}\right)=e^{-6}(1+6+18+36+54)=115e^{-6}.
> ```

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 版权页：MIT OpenCourseWare，http://ocw.mit.edu；6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010。有关引用这些材料或使用条款（Terms of Use）的信息，请访问 http://ocw.mit.edu/terms。）</span>
