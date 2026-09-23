<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 8 解答（Tutorial 8: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期 · MIT 电气工程与计算机科学系 Department of Electrical Engineering &amp; Computer Science）</span>

<span style="color:#1e8449;">**[note]**</span> <span style="color:#7f8c8d;">原始 PDF 仅含解答文本，题面见课程发布的 Tutorial 8 题目页；本文件对解答内容做完整行内双语翻译。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 设 $A$ = {到达的物品（item）是 A 型}。这 3 个相互独立的泊松过程（Poisson processes）可以合并（merge）为一个到达速率为每分钟 $a+b+c$ 个物品的泊松过程。若 $\delta$ 是一段很短的时间区间，则
>
> ```math
> \begin{aligned}
> P(A)&=P(\{\text{到达一件 A 型物品}\}\mid\{\text{到达一件物品}\})\\
> &=\frac{P(\{\text{到达一件 A 型物品}\})}{P(\{\text{到达一件物品}\})}
> \approx\frac{a\delta}{(a+b+c)\delta}=\frac{a}{a+b+c}.
> \end{aligned}
> ```
>
> 「第一个物品是 A 型，且接下来 9 个物品中恰有一个是 A 型」的概率为
>
> ```math
> P(A)\cdot\binom{9}{1}P(A)(1-P(A))^8=\binom{9}{1}P(A)^2(1-P(A))^8.
> ```
>
> **(b)** 设 $B$ = {到达的物品是 B 型}，$C$ = {到达的物品是 C 型}。要使 A 型物品的数量是 B 型物品数量的 5 倍，只能是下列两种情形之一：5 个 A 型物品、1 个 B 型物品、4 个 C 型物品；或者 0 个 A 型物品、0 个 B 型物品、10 个 C 型物品。这一事件的概率是两种情形的概率之和：
>
> ```math
> \frac{10!}{5!\,1!\,4!}\,P(A)^5P(B)P(C)^4+P(C)^{10},
> ```
>
> 其中 $P(A)=\dfrac{a}{a+b+c}$，$P(B)=\dfrac{b}{a+b+c}$，$P(C)=\dfrac{c}{a+b+c}$。
>
> **(c)** 相邻两次排放（discharge）之间的总时间，是阶数（order）为 10、参数为 $a+b+c$ 的埃尔朗随机变量（Erlang random variable），其 PDF（概率密度函数，probability density function）为
>
> ```math
> f_T(t)=
> \begin{cases}
> \dfrac{(a+b+c)^{10}t^9e^{-(a+b+c)t}}{9!}, & t\ge 0,\\[6pt]
> 0, & \text{其他情况}.
> \end{cases}
> ```
>
> 其均值与方差分别为 $E[T]=\dfrac{10}{a+b+c}$ 与 $\mathrm{var}(T)=\dfrac{10}{(a+b+c)^2}$。
>
> **(d)** 设 $X$ = {5 分钟内恰有两个 A 型物品到达}，$Y$ = {5 分钟内恰有两个 B 型物品到达}，$Z$ = {5 分钟内恰有两个 C 型物品到达}。由于 $X$、$Y$、$Z$ 是相互独立的事件（independent events），我们知道
>
> ```math
> \begin{aligned}
> &P(\{\text{5 分钟内三种类型各有两个物品到达}\})\\
> &\quad=P(X)P(Y)P(Z)
> =\frac{(5a)^2e^{-5a}}{2!}\cdot\frac{(5b)^2e^{-5b}}{2!}\cdot\frac{(5c)^2e^{-5c}}{2!}
> =\frac{(125abc)^2e^{-5(a+b+c)}}{8}.
> \end{aligned}
> ```

<!-- ===== PDF p2 ===== -->

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 由于每一位潜在顾客（potential customer）以概率 $p$ 成为实际顾客（actual customer），这里面对的是二项（binomial）概率：$\binom{5}{3}p^3(1-p)^2$ 即「前 5 位潜在顾客中恰有 3 位成为实际顾客」的概率。
>
> **(b)** 各潜在顾客是否成为实际顾客彼此独立。于是
>
> ```math
> \begin{aligned}
> &P(\text{第 5 位顾客是第 3 位实际顾客})\\
> &\quad=P(\text{前 4 位顾客中任意 2 位成为实际顾客})\cdot P(\text{第 5 位顾客成为实际顾客})\\
> &\quad=\left[\binom{4}{2}p^2(1-p)^2\right][p]=\binom{4}{2}p^3(1-p)^2.
> \end{aligned}
> ```
>
> **(c)** 到达的顾客流被随机分裂（randomly split）为两个独立的泊松过程：实际顾客的到达过程，速率为 $p\lambda$；以及未成为实际顾客的潜在顾客的到达过程，速率为 $(1-p)\lambda$。商店将在 10 位实际顾客到达后关门。因此，商店在速率为 $p\lambda$ 的实际顾客泊松过程发生第 10 次到达时关门。于是 $L=T_1+T_2+\cdots+T_{10}$，其中 $T_i$ 是参数为 $p\lambda$ 的指数分布（exponential distribution）到达间隔时间。$L$ 的分布是 10 阶埃尔朗 PDF（Erlang PDF）：
>
> ```math
> f_L(l)=\frac{(p\lambda)^{10}l^9e^{-(p\lambda)l}}{9!},\qquad l\ge 0.
> ```
>
> 由此可得 $L$ 的期望为 $\dfrac{10}{p\lambda}$。
>
> **(d)** 由于已到达 5 位潜在顾客，其中 3 位是实际顾客，我们关心的是接下来 7 位实际顾客到达所需的时间。由 (c) 可知，接下来 7 位实际顾客到达的期望时间为 $\dfrac{7}{p\lambda}$。再加上前 5 位潜在顾客到达所需的期望时间，便得到商店营业总时间的条件期望为
>
> ```math
> \frac{5}{\lambda}+\frac{7}{p\lambda}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 前 5 位潜在顾客按速率 $\lambda$ 的泊松过程到达，其到达总时间的期望即 $5/\lambda$。
>
> **(e)** 「没有任何两位实际顾客在 $\tau$ 个时间单位内相继到达」的概率，等价于「隔开这 10 位实际顾客的 9 个相互独立的到达间隔时间都至少相差 $\tau$ 个时间单位」的概率。于是
>
> ```math
> P(\text{无两位实际顾客在 }\tau\text{ 个时间单位内相继到达})=P\big([T_1\ge\tau]^9\big)=e^{-9p\lambda\tau}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 每个 $T_i$ 服从参数 $p\lambda$ 的指数分布，故 $P(T_i\ge\tau)=e^{-p\lambda\tau}$；9 个独立间隔相乘得 $[e^{-p\lambda\tau}]^9=e^{-9p\lambda\tau}$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本题见教材（textbook）第 334 页的 Problem 6.24（see problem 6.24, page 334 in the textbook）。

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 版权页：MIT OpenCourseWare，http://ocw.mit.edu；6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010。有关引用这些材料或使用条款（Terms of Use）的信息，请访问 http://ocw.mit.edu/terms。）</span>
