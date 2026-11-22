<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 10 解答（Problem Set 10: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering &amp; Computer Science）。本 PDF 为解答文档：仅含各题解答，题目陈述与原题插图见对应习题集原卷。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1. A Financial Parable（一则金融寓言）**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 若资产的收益（gain）$R \le -5$（即亏损超过 5%），银行就会资不抵债（insolvent）。这一概率就是 $R$ 的 CDF（累积分布函数，cumulative distribution function）在 $-5$ 处的取值。由于 $R$ 服从正态分布（normal distribution），可以把该 CDF 化成标准正态随机变量的形式——减去均值、再除以标准差——然后查标准正态 CDF 表。
>
> ```math
> \begin{aligned}
> E[R] &= 7, \qquad \mathrm{var}(R) = 10^2 = 100,\\
> P(R \le -5) &= P\!\left(\frac{R-7}{10} \le \frac{-5-7}{10}\right) = \Phi(-1.2) \approx 0.115 .
> \end{aligned}
> ```
>
> 因此，若只投资这一项资产，银行有 11.5% 的概率变得资不抵债。
>
> **(b)** 若把各 $R_i$ 建模为相互独立的正态随机变量，则它们的和 $R = (R_1 + \cdots + R_{20})/20$ 也是正态随机变量（见教材（textbook）第 214 页例 4.11（Example 4.11））。于是可以先算出新 $R$ 的均值与方差，再按 (a) 的步骤进行。注意，由于假设各随机变量相互独立，和的方差就是各方差之和。
>
> ```math
> \begin{aligned}
> E[R] &= (E[R_1] + \cdots + E[R_{20}])/20 = 7,\\
> \mathrm{var}(R) &= \frac{1}{20^2}\bigl(\mathrm{var}(R_1) + \cdots + \mathrm{var}(R_{20})\bigr) = \frac{1}{400}\cdot 100\cdot 20 = 5,\\
> P(R \le -5) &= P\!\left(\frac{R-7}{\sqrt{5}} \le \frac{-5-7}{\sqrt{5}}\right) = \Phi(-5.367) \approx 0.0000000439 = 4.39\times 10^{-8} .
> \end{aligned}
> ```
>
> 这样，通过分散投资（diversifying）并假设 20 项资产的收益相互独立，银行表面上把资不抵债的概率降到了一个『可以接受』的数值。
>
> **(c)** 现在若各收益 $R_i$ 之间正相关（positively correlated），就不能再把各方差直接相加了；还必须计入随机变量两两之间的协方差（covariance）。协方差由下式给出：
>
> ```math
> \mathrm{cov}(R_i, R_j) = \rho(R_i, R_j)\sqrt{\mathrm{var}(R_i)\,\mathrm{var}(R_j)} = \frac{1}{2}\cdot\sqrt{10^2\cdot 10^2} = 50 .
> ```
>
> 由教材第 220 页可知，此时的方差为
>
> ```math
> \begin{aligned}
> \mathrm{var}(R) &= \mathrm{var}\!\left(\frac{1}{20}\sum_{i=1}^{20} R_i\right)
> = \frac{1}{400}\left(\sum_{i=1}^{20}\mathrm{var}(R_i) \; + \!\!\sum_{\{(i,j)\,|\,i\neq j\}}\!\!\mathrm{cov}(R_i, R_j)\right)\\
> &= \frac{1}{400}\bigl(20\cdot 100 + 380\cdot 50\bigr) = 52.5 .
> \end{aligned}
> ```
>
> 由于仍假设 $R = (R_1 + \cdots + R_{20})/20$ 是正态的，可以再次按 (a)、(b) 两问的步骤：
>
> ```math
> \begin{aligned}
> E[R] &= (E[R_1] + \cdots + E[R_{20}])/20 = 7,\\
> \mathrm{var}(R) &= 52.5,\\
> P(R \le -5) &= P\!\left(\frac{R-7}{\sqrt{52.5}} \le \frac{-5-7}{\sqrt{52.5}}\right) = \Phi(-1.656) \approx 0.0488 .
> \end{aligned}
> ```

<!-- ===== PDF p2 ===== -->

> **（续）** 因此，把资产收益之间的正相关考虑进来之后，我们对资不抵债的概率就不再像 (b) 中那样放心了。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $M$、$N$ 分别为投票的男性与女性人数。我们要求 $P(M > N)$，即 $P(M - N > 0)$。中心极限定理（central limit theorem）不能直接施加于随机变量 $M - N$；但它意味着 $M$ 与 $N$ 都能很好地用正态随机变量近似。于是 $M - N$ 是两个相互独立的、近似正态的随机变量之差；而两个正态随机变量之差仍是正态的，故 $M - N$ 近似服从正态分布。$M - N$ 的均值与方差为
>
> ```math
> \begin{aligned}
> E[M - N] &= 300\cdot 0.4 - 196\cdot 0.5 = 120 - 98 = 22,\\
> \mathrm{var}(M - N) &= \mathrm{var}(M) + \mathrm{var}(N) = 300\cdot 0.4\cdot 0.6 + 196\cdot 0.5\cdot 0.5 = 121 .
> \end{aligned}
> ```
>
> 因此 $M - N$ 的标准差（standard deviation）为 11。设 $Z$ 为标准正态随机变量，用中心极限定理近似可得
>
> ```math
> P(M - N > 0) = P\!\left(\frac{M - N - 22}{11} > -\frac{22}{11}\right) \approx P(Z \ge -2) = 0.9772 .
> ```
>
> 若把所关心的事件写成 $P(M - N \ge 1/2)$，则可得到一个稍更精细的估计：
>
> ```math
> P(M - N > 1/2) = P\!\left(\frac{M - N - 22}{11} \ge \frac{1/2 - 22}{11}\right) = P\!\left(\frac{M - N - 22}{11} \ge -\frac{21.5}{11}\right) \approx P(Z \ge -1.95) = 0.974 .
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 利用中心极限定理（Central Limit Theorem），可得
>
> ```math
> P\!\left(\frac{n}{2} - 10 \le S_n \le \frac{n}{2} + 10\right) \approx \Phi\!\left(\frac{20}{\sqrt{n}}\right) - \Phi\!\left(-\frac{20}{\sqrt{n}}\right) \to 0 \quad \text{as } n \to \infty .
> ```
>
> **(b)** 由弱大数定律（weak law of large numbers），该极限为 1。
>
> **(c)** 利用中心极限定理，可得
>
> ```math
> P\!\left(\frac{n}{2} - \frac{\sqrt{n}}{2} \le S_n \le \frac{n}{2} + \frac{\sqrt{n}}{2}\right) \approx \Phi(1) - \Phi(-1) = 0.6826 .
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 原文该处分数在文本提取时顺序错乱（形如「$\sqrt{2n}$」）；按解答给出的数值 $\Phi(1)-\Phi(-1)=0.6826$ 及 $\mathrm{sd}(S_n)=\sqrt{n/4}=\sqrt{n}/2$ 反推，窗口应为 $\pm\sqrt{n}/2$，恰为一个标准差。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 设 $C$ 表示 Bob 收到的硬币：$C = 1$ 表示收到第一枚，$C = 2$ 表示收到第二枚。则 $P(C = 1) = p$，$P(C = 2) = 1 - p$。给定 $C$ 时，3 次独立抛掷中正面（heads）的次数 $Y$ 是二项（binomial）随机变量。利用贝叶斯法则（Bayes' rule），可以求出『Bob 观察到 $k$ 次正面的条件下，他收到的是第一枚硬币』的概率：
>
> ```math
> \begin{aligned}
> P(C = 1 \mid Y = k)
> &= \frac{P(Y = k \mid C = 1)\,P(C = 1)}{P(Y = k \mid C = 1)\,P(C = 1) + P(Y = k \mid C = 2)\,P(C = 2)}\\
> &= \frac{\binom{3}{k}(1/3)^k (2/3)^{3-k}\,p}{\binom{3}{k}(1/3)^k (2/3)^{3-k}\,p + \binom{3}{k}(2/3)^k (1/3)^{3-k}\,(1-p)}
> = \frac{2^{3-k}\,p}{2^{3-k}\,p + 2^k(1-p)}
> = \frac{1}{1 + \dfrac{1-p}{p}\,2^{2k-3}} .
> \end{aligned}
> ```

<!-- ===== PDF p3 ===== -->

> **（续）**
>
> **(b)** 我们要找使下列不等式成立的 $k$：
>
> ```math
> P(C = 1 \mid Y = k) > p
> \quad\Longleftrightarrow\quad
> \frac{2^{3-k}\,p}{2^{3-k}\,p + 2^k(1-p)} > p .
> ```
>
> 注意：若 $p = 0$ 或 $p = 1$，则没有 $k$ 满足该不等式。现对 $0 < p < 1$ 求解：
>
> ```math
> \begin{aligned}
> \frac{2^{3-k}}{2^{3-k}p + 2^k(1-p)} &> 1\\
> 2^{3-k} &> 2^{3-k}\,p + 2^k(1-p)\\
> 2^{3-k}(1-p) &> 2^k(1-p)\\
> 2^{3-k} &> 2^k\\
> 2k &< 3\\
> k &< 3/2
> \end{aligned}
> ```
>
> 当 $0 < p < 1$ 时，$k = 0$ 或 $k = 1$ 会使『Alice 发送的是第一枚硬币』的概率上升。该不等式与 $p$ 无关，因而不随 $p$ 的增大而改变。直观上这很合理：$k$ 值越低，Bob 越相信自己拿到的是正面概率较低的那枚硬币。
>
> **(c)** 给定 Bob 观察到 $k$ 次正面，他必须决定用的是第一枚还是第二枚硬币。为使错误概率最小，当 $P(C = 1 \mid Y = k) \ge P(C = 2 \mid Y = k)$ 时，他应判定为第一枚。于是决策规则（decision rule）为
>
> ```math
> \begin{aligned}
> P(C = 1 \mid Y = k) &\ge P(C = 2 \mid Y = k)\\
> \frac{2^{3-k}p}{2^{3-k}p + 2^k(1-p)} &\ge \frac{2^k(1-p)}{2^{3-k}p + 2^k(1-p)}\\
> 2^{3-k}p &\ge 2^k(1-p)\\
> 2^{2k-3} &\le \frac{p}{1-p}\\
> k &\le \frac{3}{2} + \frac{1}{2}\log_2\frac{p}{1-p}
> \end{aligned}
> ```

<!-- ===== PDF p4 ===== -->

> **（续）**
>
> **(d)**
>
> **i.** 若 $p = 2/3$，上述规则中的门限（threshold）等于 $\dfrac{3 + \log_2 2}{2} = 2$。因此，Bob 观察到 0、1 或 2 次正面时会判定自己收到的是第一枚硬币，观察到 3 次正面时则判定是第二枚。用全概率定律（total probability law）求正确决策的概率：
>
> ```math
> \begin{aligned}
> P(\text{Correct}) &= P(\text{Correct}\mid C = 1)\cdot p + P(\text{Correct}\mid C = 2)\cdot(1-p)\\
> &= P(Y < 3 \mid C = 1)\cdot p + P(Y = 3 \mid C = 2)\cdot(1-p)\\
> &= \bigl(1 - (1/3)^3\bigr)\cdot\frac{2}{3} + \left(\frac{2}{3}\right)^{3}\cdot\frac{1}{3}
> = \frac{20}{27} \approx 0.741
> \end{aligned}
> ```
>
> **ii.** 在没有任何数据的情况下，Bob 只能以某个概率 $q$ 判定自己收到的是第一枚硬币。注意这一规则也包括确定性地判定第一枚（$q = 1$）或第二枚（$q = 0$）的情形。此时正确决策的概率等于
>
> ```math
> P(\text{Correct}) = P(\text{Correct}\mid C = 1)\cdot p + P(\text{Correct}\mid C = 2)\cdot(1-p) = qp + (1-q)(1-p) = 1 - p + q(2p-1) = \frac{1}{3} + \frac{q}{3}
> ```
>
> 显然，当 $q = 1$（即 Bob 确定性地判定自己收到第一枚硬币）时，正确决策的概率最大（错误概率最小）。此时 $P(\text{Correct}) = 2/3 \approx 0.667$。观察 3 次抛掷使正确决策的概率提高了 $2/27 \approx 0.074$。
>
> **(e)** 若 $p$ 增大，(c) 中决策规则的门限随之上升，即『Bob 判定自己收到第一枚』的 $k$ 取值范围只会扩大。
>
> **(f)** 若上述规则的门限低于零，Bob 将永远不会判定自己收到第一枚：
>
> ```math
> \frac{3}{2} + \frac{1}{2}\log_2\frac{p}{1-p} < 0
> \;\Rightarrow\; \log_2\frac{p}{1-p} < -3
> \;\Rightarrow\; \frac{p}{1-p} < \frac{1}{8}
> \;\Rightarrow\; p < \frac{1}{9}
> ```
>
> 若 $p < 1/9$，先验概率（prior probability）太低，以至于 3 次抛掷所能提供的任何证据都无法使 Bob 判定自己收到第一枚。
>
> **(g)** 若上述规则的门限大于或等于 3，Bob 将总是判定自己收到第一枚：
>
> ```math
> \frac{3}{2} + \frac{1}{2}\log_2\frac{p}{1-p} \ge 3
> \;\Rightarrow\; \log_2\frac{p}{1-p} \ge 3
> \;\Rightarrow\; \frac{p}{1-p} \ge 8
> \;\Rightarrow\; p \ge \frac{8}{9}
> ```

<!-- ===== PDF p5 ===== -->

> **（续）** 若 $p \ge 8/9$，先验概率太高，以至于 3 次抛掷所能提供的任何证据都无法使 Bob 判定自己收到第二枚。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 5**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 利用全概率定理（total probability theorem），有
>
> ```math
> p_{T_1}(t) = \int_0^1 p_{T_1\mid Q}(t \mid q)\,f_Q(q)\,dq = \int_0^1 (1-q)^{t-1}q\,dq = \frac{1}{(t+1)\,t}, \qquad t = 1, 2, \ldots
> ```
>
> **(b)** 最小二乘估计（least squares estimate）与给定 $T_1$ 时 $Q$ 的条件期望（conditional expectation）重合，后者推导如下：
>
> ```math
> \begin{aligned}
> E[Q \mid T_1 = t] &= \int_0^1 p_{Q\mid T_1}(q \mid t)\,q\,dq
> = \frac{1}{p_{T_1}(t)}\int_0^1 p_{T_1\mid Q}(t \mid q)\,f_Q(q)\,q\,dq\\
> &= t(t+1)\int_0^1 q^2(1-q)^{t-1}\,dq
> = t(t+1)\,\frac{2!\,(t-1)!}{(t+2)!}
> = \frac{2}{t+2}
> \end{aligned}
> ```
>
> **(c)** 写出给定 $T_1 = t_1, \ldots, T_k = t_k$ 时 $Q$ 的后验（posterior）分布：
>
> ```math
> f_{Q\mid T_1,\ldots,T_k}(q \mid t_1, \ldots, t_k)
> = \frac{f_Q(q)\,\prod_{i=1}^{k} p_{T_i}(T_i = t_i \mid Q = q)}{\int_0^1 f_Q(q)\,\prod_{i=1}^{k} p_{T_i}(T_i = t_i \mid Q = q)\,dq}
> = \frac{q^k (1-q)^{\sum_i t_i - k}}{c},
> ```
>
> 其中分母把 $q$ 积掉了，故可视为常数标量 $c$。为使上式最大，令其对 $q$ 的导数为零：
>
> ```math
> k\,q^{k-1}(1-q)^{\sum_i t_i - k} - \Bigl(\sum_i t_i - k\Bigr)q^{k}(1-q)^{\sum_i t_i - k - 1} = 0,
> ```
>
> 等价地，
>
> ```math
> k(1-q) - \Bigl(\sum_i t_i - k\Bigr)q = 0,
> ```
>
> 从而得到 MAP 估计（MAP estimate）
>
> ```math
> \hat{q} = \frac{k}{\sum_{i=1}^{k} t_i} .
> ```
>
> *（仅本小问：设 $q$ 抽自随机变量 $Q$，且 $Q$ 现在改为在 $[0.5, 1]$ 上均匀分布。）*

<!-- ===== PDF p6 ===== -->

> **（续）**
>
> **(d)** $T_2$ 基于 $T_1$ 的线性最小二乘估计（LLSE，linear least squares estimator）为
>
> ```math
> \hat{T}_2 = E[T_2] + \frac{\mathrm{cov}(T_1, T_2)}{\mathrm{var}(T_1)}\,(T_1 - E[T_1]),
> ```
>
> 其中各系数为
>
> ```math
> E[T_1] = E[T_2] = \int_{0.5}^{1} f_Q(q)\,E[T \mid Q = q]\,dq = \int_{0.5}^{1} 2\cdot\frac{1}{q}\,dq = 2\ln 2,
> ```
>
> 且由全方差公式（law of total variance）
>
> ```math
> \begin{aligned}
> \mathrm{var}(T_1) = \mathrm{var}(T_2) &= E\bigl[\mathrm{var}(T_1 \mid Q)\bigr] + \mathrm{var}\bigl(E[T_1 \mid Q]\bigr)
> = E\!\left[\frac{1-Q}{Q^2}\right] + \mathrm{var}\!\left[\frac{1}{Q}\right]\\
> &= E[1/Q^2] - E[1/Q] + E[1/Q^2] - \bigl(E[1/Q]\bigr)^2\\
> &= \int_{0.5}^{1} f_Q(q)\,\frac{1}{q^2}\,dq - \int_{0.5}^{1} f_Q(q)\,\frac{1}{q}\,dq + \int_{0.5}^{1} f_Q(q)\,\frac{1}{q^2}\,dq - \left(\int_{0.5}^{1} f_Q(q)\,\frac{1}{q}\,dq\right)^{2}\\
> &= 2 - 2\ln 2 + 2 - (2\ln 2)^2 = 4 - 2\ln 2 - (2\ln 2)^2,
> \end{aligned}
> ```
>
> 以及协方差
>
> ```math
> \begin{aligned}
> \mathrm{cov}(T_1, T_2) &= E[T_1 T_2] - E[T_1]E[T_2]
> = E\bigl[E[T_1 T_2 \mid Q]\bigr] - E[T_1]E[T_2]\\
> &= E\bigl[E[T_1 \mid Q]\,E[T_2 \mid Q]\bigr] - E[T_1]E[T_2]
> = E[1/Q^2] - E[T_1]E[T_2]
> = 2 - 4(\ln 2)^2
> \end{aligned}
> ```
>
> 于是我们得到线性最小二乘估计
>
> ```math
> \hat{T}_2 = 2\ln 2 + \frac{2 - 4(\ln 2)^2}{4 - 2\ln 2 - (2\ln 2)^2}\,(T_1 - 2\ln 2) \approx 1.543 + 0.113\,T_1 .
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 两点译者注：(1) 原文该小问首句的文字层为「The LLSE of T1 given T2」，与其后公式（$\hat{T}_2$ 由 $T_1$ 表示）不一致，现按公式译为「$T_2$ 基于 $T_1$ 的 LLSE」；(2) 原文数值近似「$\approx 1.543 + 0.113\,T_1$」的常数项有误：按公式展开应为 $E[T_2] - 0.113\,E[T_1] \approx 1.386 - 0.157 = 1.230$（原文疑似把 $0.113\times 2\ln 2$ 误加而非相减），斜率 $0.113$ 正确。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 6**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 为求归一化常数 $c$，对联合 PDF（joint PDF）积分：
>
> ```math
> \int_0^1\!\!\int_0^1 f_{X,Y}(x,y)\,dy\,dx = c\int_0^1\!\!\int_0^1 xy\,dy\,dx = c\int_0^1 \frac{1}{2}x\,dx = \frac{c}{4} .
> ```
>
> 因此 $c = 4$。
>
> **(b)** 为构造条件期望估计量（conditional expectation estimator），需要求条件概率密度：
>
> ```math
> f_{X\mid Y}(x \mid y) = \frac{f_{X,Y}(x,y)}{f_Y(y)} = \frac{4xy}{\int_0^1 4xy\,dx} = \frac{4xy}{2y} = 2x, \qquad x \in (0, 1]
> ```
>
> 于是
>
> ```math
> \hat{x}_{\mathrm{CE}}(y) = E[X \mid Y = y] = \int_0^1 x\cdot 2x\,dx = \frac{2}{3} .
> ```

<!-- ===== PDF p7 ===== -->

> **（续）**
>
> **(c)** 首先注意：条件概率密度不依赖于 $y$。因此 $X$ 与 $Y$ 相互独立（independence），无论是否观察到 $Y = y$，都不影响 (b) 中的估计。另一种看法是：若不观察 $y$，可以算出边际密度（marginal density）$f_X(x) = \int_0^1 4xy\,dy = 2x$，它与条件密度相同，因此会给出同样的估计。
>
> **(d)** 由于 $X$ 与 $Y$ 相互独立，任何估计量都无法利用 $Y$ 的观测值来估计 $X$。$X$ 的 MAP 估计量（MAP estimator）等于 1，且与我们观察到什么 $y$ 值无关，因为条件密度（以及边际密度）在 1 处取得最大值。
>
> <span style="color:#7f8c8d;">（原文页脚：† 6.431 必做；对 6.041 为选做挑战题。）</span>

<!-- ===== PDF p8 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu　6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability　Fall 2010。有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
