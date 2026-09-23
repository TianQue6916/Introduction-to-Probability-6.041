<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Quiz 1 解答（Quiz 1 Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期，2010 年 10 月 12 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **1.**（10 分）设 $R_i$ 为 Stephen 在第 $i$ 个红灯处花费的时间。$R_i$ 是参数 $p=\dfrac{1}{3}$ 的 Bernoulli random variable（伯努利随机变量），其 PMF（概率质量函数）为：
>
> ```math
> P_{R_i}(r)=
> \begin{cases}
> 2/3, & r=0,\\
> 1/3, & r=1,\\
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> $R_i$ 的期望与方差为：
>
> ```math
> E[R_i]=p=\frac{1}{3},\qquad \mathrm{var}(R_i)=p(1-p)=\frac{1}{3}\cdot\frac{2}{3}=\frac{2}{9}.
> ```
>
> 设 $T_S$ 为 Stephen 通勤时间的总时长（单位：分钟）。则
>
> ```math
> T_S=18+\sum_{i=1}^{5}R_i.
> ```
>
> $T_S$ 是一个 shifted binomial（平移二项分布），试验次数 $n=5$、参数 $p=1/3$。于是 $T_S$ 的 PMF 为：
>
> ```math
> P_{T_S}(k)=
> \begin{cases}
> \dbinom{5}{k-18}\left(\dfrac{1}{3}\right)^{k-18}\left(\dfrac{2}{3}\right)^{23-k}, & k\in\{18,19,20,21,22,23\},\\[8pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> $T_S$ 的期望与方差为：
>
> ```math
> E[T_S]=E\!\left[18+\sum_{i=1}^{5}R_i\right]=\frac{59}{3},\qquad
> \mathrm{var}(T_S)=\mathrm{var}\!\left[18+\sum_{i=1}^{5}R_i\right]=\frac{10}{9}.
> ```
>
> **2.**（10 分）设 $N$ 为 Stephen 通勤途中遇到的红灯数量。给定 $T_S\le 19$，则 $N=0$ 或 $N=1$。$N=0$ 的无条件概率为 $P(N=0)=\left(\dfrac{2}{3}\right)^{5}$；$N=1$ 的无条件概率为 $P(N=1)=\dbinom{5}{1}\left(\dfrac{2}{3}\right)^{4}\left(\dfrac{1}{3}\right)$。

<!-- ===== PDF p2 ===== -->

> **Problem 1（续）**
>
> **2.（续）** 为求条件期望，先计算如下 conditional PMF（条件概率质量函数）：
>
> ```math
> P_{N\mid T_S\le 19}(n\mid T_S\le 19)=
> \begin{cases}
> \dfrac{\left(\frac{2}{3}\right)^{5}}{\left(\frac{2}{3}\right)^{5}+\binom{5}{1}\left(\frac{2}{3}\right)^{4}\left(\frac{1}{3}\right)}=\dfrac{2}{7}, & n=0,\\[10pt]
> \dfrac{\binom{5}{1}\left(\frac{2}{3}\right)^{4}\left(\frac{1}{3}\right)}{\left(\frac{2}{3}\right)^{5}+\binom{5}{1}\left(\frac{2}{3}\right)^{4}\left(\frac{1}{3}\right)}=\dfrac{5}{7}, & n=1,\\[10pt]
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> 因此
>
> ```math
> E[N\mid T_S\le 19]=\frac{5}{7}.
> ```
>
> **3.**（10 分）给定 Stephen 遇到的最后一个红灯是第 4 个灯，即 $R_4=1$ 且 $R_5=0$。
>
> 题目要求计算 $\mathrm{var}(N\mid\{R_4=1\}\cap\{R_5=0\})$。于是
>
> ```math
> \begin{aligned}
> \mathrm{var}(N\mid\{R_4=1\}\cap\{R_5=0\})
> &=\mathrm{var}(R_1+R_2+R_3+R_4+R_5\mid\{R_4=1\}\cap\{R_5=0\})\\
> &=\mathrm{var}(R_1+R_2+R_3+1+0)\\
> &=\mathrm{var}(R_1+R_2+R_3)\\
> &=3\,\mathrm{var}(R_1)\\
> &=\frac{6}{9}.
> \end{aligned}
> ```
>
> **4.**（10 分）在给定条件下，可用 discrete uniform law（离散均匀分布律）来计算所求概率。Stephen 在 5 个灯中总共遇到 3 个红灯，共有 $\dbinom{5}{3}$ 种方式；其中"前三个灯中有两个是红灯"共有 $\dbinom{3}{2}$ 种方式，剩下 1 个红灯出现在后两个灯中，有 $\dbinom{2}{1}$ 种方式。综合起来：
>
> ```math
> P(\text{前三个灯中有两个红灯}\mid\text{总共有三个红灯})
> =\frac{\dbinom{3}{2}\dbinom{2}{1}}{\dbinom{5}{3}}=\frac{3}{5}.
> ```
>
> **5.**（5 分）设 $T_J$ 为 Jon 通勤时间的总时长（单位：分钟）。Jon 通勤时间的 PMF 为：
>
> ```math
> P_{T_J}(\ell)=
> \begin{cases}
> 1/4, & \ell\in\{20,21,22,23\},\\
> 0, & \text{otherwise（其他情形）}.
> \end{cases}
> ```
>
> **6.**（10 分）设 $A$ 为事件「Jon 在 20 分钟内到达工作地点」，$B$ 为事件「恰好有一人在 20 分钟时到达」。则
>
> ```math
> \begin{aligned}
> P(A\mid B)=\frac{P(A\cap B)}{P(B)}
> &=\frac{P(\{T_J=20\}\cap\{T_S\ne 20\})}{P(\{T_J=20\}\cap\{T_S\ne 20\})+P(\{T_J=20\}\cap\{T_S=20\})}\\[4pt]
> &=\frac{P(T_J=20)P(T_S\ne 20)}{P(T_J=20)P(T_S\ne 20)+P(T_J=20)P(T_S=20)}.
> \end{aligned}
> ```

<!-- ===== PDF p3 ===== -->

> **Problem 1（续）**
>
> **6.（续）** Jon 在 20 分钟内到达工作地点（即 $T_J=20$）当且仅当他在车站不必等火车（即 $X=0$）。该事件发生的概率为：
>
> ```math
> P(T_J=20)=P(X=0)=\frac{1}{4}.
> ```
>
> Stephen 在 20 分钟内到达工作地点当且仅当他遇到 2 个红灯。该事件的概率是一个 binomial probability（二项概率）：
>
> ```math
> P(T_S=20)=\binom{5}{2}\left(\frac{1}{3}\right)^{2}\left(\frac{2}{3}\right)^{3}.
> ```
>
> 于是
>
> ```math
> P(A\mid B)=
> \frac{\dfrac{1}{4}\left[1-\dbinom{5}{2}\left(\dfrac{1}{3}\right)^{2}\left(\dfrac{2}{3}\right)^{3}\right]}
> {\dfrac{1}{4}\left[1-\dbinom{5}{2}\left(\dfrac{1}{3}\right)^{2}\left(\dfrac{2}{3}\right)^{3}\right]+\dfrac{1}{4}\,\dbinom{5}{2}\left(\dfrac{1}{3}\right)^{2}\left(\dfrac{2}{3}\right)^{3}}.
> ```
>
> **7.**（10 分）所求概率为 $P(T_S\le T_J)$。可以用 total probability theorem（全概率定律），以 Jon 的通勤时长（即 Jon 在车站的等待时间）为条件来计算：若 Jon 的通勤为 20 分钟（即 $X=0$），则 Stephen 最多遇到 2 个红灯就能满足 $T_S\le T_J$；类似地，若 Jon 的通勤为 21 分钟（即 $X=1$），Stephen 最多可遇到 3 个红灯，依此类推。
>
> ```math
> \begin{aligned}
> P(T_S\le T_J)&=\sum_{x=0}^{3}P(T_S\le T_J\mid X=x)P(X=x)\\
> &=\sum_{x=0}^{3}\frac{1}{4}\sum_{k=0}^{2+x}\binom{5}{k}\left(\frac{1}{3}\right)^{k}\left(\frac{2}{3}\right)^{5-k}\\
> &=0.9352.
> \end{aligned}
> ```
>
> 下面给出另一种做法。我们先计算 Stephen 与 Jon 通勤时间的 joint PMF（联合概率质量函数）$P_{T_S,T_J}(k,\ell)$。由独立性，$P_{T_S,T_J}(k,\ell)=P_{T_S}(k)P_{T_J}(\ell)$。因此
>
> ```math
> \begin{aligned}
> P(T_S\le T_J)&=P(T_S=18)+P(T_S=19)+P(T_S=20)+P(\{T_S=21\}\cap\{T_J\ge 21\})\\
> &\quad+P(\{T_S=22\}\cap\{T_J\ge 22\})+P(\{T_S=23\}\cap\{T_J=23\})\\[4pt]
> &=\left(\frac{2}{3}\right)^{5}+\binom{5}{1}\left(\frac{1}{3}\right)\left(\frac{2}{3}\right)^{4}
> +\binom{5}{2}\left(\frac{1}{3}\right)^{2}\left(\frac{2}{3}\right)^{3}\\
> &\quad+\binom{5}{3}\left(\frac{1}{3}\right)^{3}\left(\frac{2}{3}\right)^{2}\cdot\frac{3}{4}
> +\binom{5}{4}\left(\frac{1}{3}\right)^{4}\left(\frac{2}{3}\right)\cdot\frac{2}{4}
> +\binom{5}{5}\left(\frac{1}{3}\right)^{5}\cdot\frac{1}{4}\\[4pt]
> &=0.9352.
> \end{aligned}
> ```
>
> **8.**（10 分）把条件概率表示为：
>
> ```math
> P(X=3\mid T_S\le T_J)=\frac{P(\{X=3\}\cap\{T_S\le T_J\})}{P(T_S\le T_J)}.
> ```

<!-- ===== PDF p4 ===== -->

> **Problem 1（续）**
>
> **8.（续）** 若 Jon 在车站等了 3 分钟，则他的通勤时间为 23 分钟，而 Stephen 的通勤时间不会超过 Jon（因为 Stephen 可能的最长通勤时间正是 23 分钟）。因此上式分子等于 $P(X=3)=\dfrac{1}{4}$，分母则已在上一小问中算出：
>
> ```math
> P(X=3\mid T_S\le T_J)=\frac{\dfrac{1}{4}}{\displaystyle\sum_{x=0}^{3}\frac{1}{4}\sum_{k=0}^{2+x}\binom{5}{k}\left(\frac{1}{3}\right)^{k}\left(\frac{2}{3}\right)^{5-k}}=0.2673.
> ```

---

<span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **1.**（10 分）**Always True（恒成立）。** 我们需要证明
>
> ```math
> P(A\cap B^c)=P(A)P(B^c).
> ```
>
> 先把 $P(A)$ 写成 $P(A\cap B)+P(A\cap B^c)$。于是
>
> ```math
> \begin{aligned}
> P(A\cap B^c)&=P(A)-P(A\cap B)\\
> &=P(A)-P(A)P(B)\\
> &=P(A)\bigl(1-P(B)\bigr)\\
> &=P(A)P(B^c),
> \end{aligned}
> ```
>
> 这就说明 $A$ 与 $B^c$ 相互独立。
>
> **2.**（10 分）**Not Always True（不恒成立）。** 利用下图，令 $C=A\cap B$，并设 $P(A)>P(C)$、$P(B)>P(C)$。则 conditional probability（条件概率）$P(A\cap B\mid C)=1$；同时 $P(A\mid C)=1$、$P(B\mid C)=1$。由于 $P(A\cap B\mid C)=P(A\mid C)P(B\mid C)$，所以 $A$ 与 $B$ 在给定第三个事件 $C$ 的条件下是 conditionally independent（条件独立的）。而在给定 $C^c$ 时，$A$ 与 $B$ 互斥（disjoint），也就是说 $A$ 与 $B$ 不独立。
>
> <span style="color:#7f8c8d;">【图】原页此处为 Venn 图/示意图（三个事件 $A$、$B$、$C$ 的关系图，其中 $C=A\cap B$，且 $A$、$B$ 在 $C^c$ 内互斥）。原图由后处理统一插入。</span>
>
> 下面是一个另一种的反例。设想有 3 枚硬币，正面朝上的概率分别为 $p=\dfrac{1}{5}$、$p=\dfrac{1}{3}$、$p=\dfrac{2}{3}$，每枚硬币被选中的概率相同。令 $C$ 为事件「你选中了 $p=\frac{1}{5}$ 的那枚硬币」，$C^c$ 为事件「你选中的是另外两枚硬币之一」。令 $A$ 为事件「第一次抛掷结果为正面」，$B$ 为事件「第二次抛掷结果为正面」。对给定的某枚硬币，两次抛掷相互独立，于是有：
>
> ```math
> P(B\mid A\cap C)=P(B\mid C).
> ```

<!-- ===== PDF p5 ===== -->

> **Problem 2（续）**
>
> **2.（续）** 在给定 $C^c$ 的条件下，$A$ 与 $B$ 不独立，因为我们手里可能是 $p=\frac{1}{3}$ 的硬币，也可能是 $p=\frac{2}{3}$ 的硬币；知道 $A$ 的结果会改变我们对第二次抛掷结果的判断（beliefs）。
>
> ```math
> P(B\mid A\cap C^c)=\frac{P(B\cap A\cap C^c)}{P(A\cap C^c)}
> =\frac{\dfrac{1}{2}\left(\dfrac{1}{3}\right)^{2}+\dfrac{1}{2}\left(\dfrac{2}{3}\right)^{2}}
> {\dfrac{1}{2}\cdot\dfrac{1}{3}+\dfrac{1}{2}\cdot\dfrac{2}{3}}
> =\frac{5}{9}.
> ```
>
> 然而
>
> ```math
> P(B\mid C^c)=\frac{P(B\cap C^c)}{P(C^c)}
> =\frac{\dfrac{1}{3}\cdot\dfrac{1}{3}+\dfrac{1}{3}\cdot\dfrac{2}{3}}{\dfrac{2}{3}}
> =\frac{1}{2}.
> ```
>
> 如上所示，$P(B\mid A\cap C^c)\ne P(B\mid C^c)$。
>
> **3.**（10 分）**Always True（恒成立）。** 利用 $X$ 与 $Y$ 的独立性，$\mathrm{var}(X+Y)=\mathrm{var}(X)+\mathrm{var}(Y)$。由于方差总是非负的，故 $\mathrm{var}(X)+\mathrm{var}(Y)\ge\mathrm{var}(X)$。

<!-- ===== PDF p6 ===== -->

<span style="color:#7f8c8d;">【图】本页为 MIT OpenCourseWare 封面页：MIT OpenCourseWare（http://ocw.mit.edu），课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010；并含引用信息与使用条款（Terms of Use）链接 http://ocw.mit.edu/terms。无正文内容。</span>
