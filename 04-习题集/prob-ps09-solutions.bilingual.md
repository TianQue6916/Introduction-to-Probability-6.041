<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 9 解答（Problem Set 9: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering &amp; Computer Science）。本 PDF 为解答文档：仅含各题解答，题目陈述与原题插图见对应习题集原卷。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 会收敛，且收敛到 0。应用弱大数定律（weak law of large numbers），可得：对一切 $\epsilon > 0$，
>
> ```math
> P(|U_i - \mu| > \epsilon) \to 0 \quad \text{as } i \to \infty .
> ```
>
> 此处 $\mu = 0$，因为 $X_i \sim U(-1.0,\, 1.0)$。
>
> **(b)** 会收敛，且收敛到 1。由于 $W_i \le 1$，对任意 $\epsilon > 0$，有
>
> ```math
> \begin{aligned}
> \lim_{i\to\infty} P(|W_i - 1| > \epsilon)
> &= \lim_{i\to\infty} P\bigl(\max\{X_1,\cdots,X_i\} < 1-\epsilon\bigr)\\
> &= \lim_{i\to\infty} P(X_1 < 1-\epsilon)\cdots P(X_i < 1-\epsilon)
> = \lim_{i\to\infty}\Bigl(1-\frac{\epsilon}{2}\Bigr)^{i}
> = 0 .
> \end{aligned}
> ```
>
> **(c)** 会收敛，且收敛到 0。$|V_n| \le \min\{|X_1|, |X_2|, \cdots, |X_n|\}$，而 $\min\{|X_1|,\cdots,|X_n|\}$ 依概率（in probability）收敛到 0；又因 $|V_n| \ge 0$，故 $|V_n|$ 依概率收敛到 0。要看出 $\min\{|X_1|,\cdots,|X_n|\}$ 为何依概率收敛到 0，注意：
>
> ```math
> \begin{aligned}
> \lim_{i\to\infty} P\bigl(\,\bigl|\min\{|X_1|,\cdots,|X_i|\} - 0\bigr| > \epsilon\bigr)
> &= \lim_{i\to\infty} P\bigl(\min\{|X_1|,\cdots,|X_i|\} > \epsilon\bigr)\\
> &= \lim_{i\to\infty} P(|X_1| > \epsilon)\cdot P(|X_2| > \epsilon)\cdots P(|X_i| > \epsilon)\\
> &= \lim_{i\to\infty} (1-\epsilon)^i = 0 ,
> \end{aligned}
> ```
>
> 最后一步用到 $|X_i|$ 在 0 与 1 之间均匀分布（uniform）这一事实。（源 PDF 此处印作 $(1+\epsilon)^i$，按 $P(|X_i|>\epsilon)=1-\epsilon$ 应为 $(1-\epsilon)^i$，已按数学正确形式还原。）
>
> <span style="color:#1e8449;">**[note]**</span> 译者注：由 (b) 的推导可知 $W_i=\max\{X_1,\ldots,X_i\}$；(c) 中 $|V_n|$ 被 $\min\{|X_1|,\ldots,|X_n|\}$ 从上方控制。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 考虑一个 PMF（概率质量函数，probability mass function）如下的随机变量 $X$：
>
> ```math
> p_X(x) =
> \begin{cases}
> p, & \text{if } x = \mu - c,\\
> p, & \text{if } x = \mu + c,\\
> 1-2p, & \text{if } x = \mu .
> \end{cases}
> ```
>
> $X$ 的均值为 $\mu$，方差（variance）为 $2pc^2$。要使方差等于 $\sigma^2$，可令 $p = \dfrac{\sigma^2}{2c^2}$。对该随机变量，有
>
> ```math
> P(|X - \mu| \ge c) = 2p = \frac{\sigma^2}{c^2},
> ```
>
> 因此切比雪夫不等式（Chebyshev inequality）取等——它是紧的（tight）。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 设 $t_i$ 为从状态 $i$ 出发直到到达状态 HT 所需的期望时间，即从状态 $i$ 出发到达 HT 的平均首次通过时间（mean first passage time）。注意 $t_S$ 就是首次观察到『正面紧接反面（heads directly followed by tails）』所需抛掷次数的期望。我们有：
>
> ```math
> \begin{aligned}
> t_S &= 1 + \tfrac{1}{2}\,t_H + \tfrac{1}{2}\,t_T,\\
> t_T &= 1 + \tfrac{1}{2}\,t_H + \tfrac{1}{2}\,t_T,\\
> t_H &= 1 + \tfrac{1}{2}\,t_H .
> \end{aligned}
> ```

<!-- ===== PDF p2 ===== -->

> **（续）** 解上述方程组，可知首次观察到『正面紧接反面』所需抛掷次数的期望为 $t_S = 4$。
>
> **(b)** 为求再次观察到『正面后接反面』所需的额外抛掷次数的期望，我们注意到：这就是状态 HT 的平均回归时间（mean recurrence time）$t_{HT}^{*}$。它可以由下式确定：
>
> ```math
> t_{HT}^{*} = 1 + p_{HT,H}\,t_H + p_{HT,T}\,t_T = 1 + \tfrac{1}{2}\cdot 2 + \tfrac{1}{2}\cdot 4 = 4 .
> ```
>
> **(c)** 考虑一个状态为 S、H、T、TT 的马尔可夫链（Markov chain）：S 是起始状态，H 表示当前一次抛掷为正面，T 表示当前一次抛掷为反面（且前一次不是反面），TT 表示最近两次抛掷都是反面。该马尔可夫链的转移概率如下面的状态转移图（state transition diagram）所示：
>
> <span style="color:#7f8c8d;">【图】原页此处为该马尔可夫链的状态转移图（状态 S、H、T、TT，各转移概率均标注为 $1/2$：自 S 出发等可能到 H 或 T；自 H 出发等可能到 H 或 T；自 T 出发等可能到 H 或 TT；自 TT 出发等可能到 H 或 TT）。原图由后处理统一插入。</span>
>
> 设 $t_i$ 为从状态 $i$ 出发直到到达状态 TT 所需的期望时间，即从状态 $i$ 出发到达 TT 的平均首次通过时间。注意 $t_S$ 就是首次观察到『反面紧接反面（tails directly followed by tails，即两次连续反面）』所需抛掷次数的期望。我们有：
>
> ```math
> \begin{aligned}
> t_S &= 1 + \tfrac{1}{2}\,t_H + \tfrac{1}{2}\,t_T,\\
> t_T &= 1 + \tfrac{1}{2}\,t_H,\\
> t_H &= 1 + \tfrac{1}{2}\,t_H + \tfrac{1}{2}\,t_T .
> \end{aligned}
> ```
>
> <span style="color:#1e8449;">**[mathtip]**</span> 第二个方程中，从 T 出发再掷出一次反面即到达 TT（该分支的剩余时间为 0），故方程中只剩 H 一项。
>
> 解上述方程组，可知首次观察到两次连续反面（two consecutive tails）所需抛掷次数的期望为 $t_S = 6$。
>
> **(d)** 为求再次观察到『正面后接反面』所需的额外抛掷次数的期望，我们注意到：这就是状态 TT 的平均回归时间 $t_{TT}^{*}$。
>
> <span style="color:#1e8449;">**[note]**</span> 原文此句沿用 (b) 的措辞「again observe heads followed by tails」，应为笔误：本小问讨论的对象是状态 TT（两次连续反面）。

<!-- ===== PDF p3 ===== -->

> **（续）** 它可以由下式确定：
>
> ```math
> t_{TT}^{*} = 1 + p_{TT,H}\,t_H + p_{TT,TT}\,t_{TT} = 1 + \tfrac{1}{2}\cdot 6 + \tfrac{1}{2}\cdot 0 = 4 .
> ```
>
> 平均而言，直到首次出现两次连续反面的抛掷次数，竟然大于直到首次出现『正面紧接反面』的抛掷次数——考虑到『正面后接反面』的抛掷对之间的平均回归时间，恰好等于『两次连续反面』的抛掷对之间的平均回归时间（等价地，前者的长期频率（long-term frequency）等于后者的长期频率¹），这一点也许令人惊讶。这是一种启动效应（start-up artifact）。注意：从状态 S 出发到达状态 HT（或 TT）的首次通过时间（first passage time）的分布，与状态 HT（或 TT）的回归时间在『大于 1』条件下的条件分布（conditional distribution）相同。虽然两种情形下回归时间的期望相等（这正是 (b) 与 (d) 两小问告诉我们的），但在『回归时间大于 1』的条件下，其条件期望在两种情形并不相同（这是可能的，因为无条件分布并不相等）。
>
> <span style="color:#7f8c8d;">脚注 1：关于平均回归时间与稳态概率（steady-state probabilities）之间这一对应关系的详细解释，见教材第 399 页习题 7.34（Problem 7.34）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

<span style="color:#1e8449;">**[note]**</span> 译者注：本 PDF 仅含解答（题目陈述与状态转移图见原习题集）。由解答中的方程可读出转移概率：自状态 1：$p_{11}=\tfrac{1}{3}$（见 (d)）、$p_{12}=\tfrac{7}{15}$、$p_{1,1A}=\tfrac{2}{15}$、$p_{1,1B}=\tfrac{1}{15}$；自状态 2：$p_{21}=\tfrac{5}{9}$、$p_{22}=\tfrac{4}{9}$（无直接转移到 $2A/2B$）。(a) 小问就 $\{1,2\}$ 两状态子链求稳态。类 $\{1A,2A\}$ 内：$p_{1A,2A}=\tfrac{3}{5}$、$p_{2A,1A}=\tfrac{1}{5}$、$p_{2A,2A}=\tfrac{4}{5}$；类 $\{1B,2B\}$ 内：$p_{1B,2B}=\tfrac{3}{4}$、$p_{2B,1B}=\tfrac{1}{8}$、$p_{2B,2B}=\tfrac{7}{8}$。

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 获胜的长期频率（long-term frequency）可以由『从 1 到 2』与『从 2 到 2』两类转移的长期频率相加得到。这些频率可由稳态概率（steady-state probabilities）$\pi_1$ 与 $\pi_2$ 求出；由于该链是非周期的（aperiodic）且常返的（recurrent），稳态概率已知存在。局部平衡方程（local balance equations）与归一化方程如下：
>
> ```math
> \pi_1\cdot\frac{7}{15} = \pi_2\cdot\frac{5}{9}, \qquad \pi_1 + \pi_2 = 1 .
> ```
>
> 解之得
>
> ```math
> \pi_1 = \frac{25}{46} \approx 0.54, \qquad \pi_2 = \frac{21}{46} \approx 0.46 .
> ```
>
> 获胜概率（即『1→2』与『2→2』转移的长期频率）现在可求出为
>
> ```math
> P(\text{winning}) = \pi_1 p_{12} + \pi_2 p_{22} = \frac{25}{46}\cdot\frac{7}{15} + \frac{21}{46}\cdot\frac{4}{9} = \frac{21}{46} \approx 0.46 .
> ```
>
> 注意：由状态 2 的平衡方程 $\pi_2 = \pi_1 p_{12} + \pi_2 p_{22}$ 可知，获胜的长期概率总等于 $\pi_2$。
>
> **(b)** 本题实际上是求被常返类（recurrent class）$\{1A, 2A\}$ 吸收（absorption）的概率。这个吸收概率可以这样求：它就是两个概率之比
>
> ```math
> \frac{p_{1,1A}}{p_{1,1A} + p_{1,1B}} = \frac{2/15}{2/15 + 1/15} = \frac{2/15}{3/15} = \frac{2}{3} .
> ```

<!-- ===== PDF p4 ===== -->

> **（续）** 更系统的方法：若定义 $a_i$ 为从状态 $i$ 出发被吸收进类 $\{1A, 2A\}$ 的概率，则可通过解下列方程组求出各 $a_i$：
>
> ```math
> \begin{aligned}
> a_1 &= p_{1,1A} + p_{11}a_1 + p_{12}a_2 = \frac{2}{15} + \frac{1}{3}\,a_1 + \frac{7}{15}\,a_2,\\
> a_2 &= p_{21}a_1 + p_{22}a_2 = \frac{5}{9}\,a_1 + \frac{4}{9}\,a_2,
> \end{aligned}
> ```
>
> 由此定出
>
> ```math
> a_1 = \frac{p_{1,1A}}{p_{1,1A}+p_{1,1B}} = \frac{2}{3} .
> ```
>
> **(c)** 设 $A$、$B$ 分别表示『从状态 1 出发时 Jack 最终使用牌组 1A &amp; 2A』与『最终使用牌组 1B &amp; 2B』的事件。由 (b) 知 $P(A) = a_1 = \tfrac{2}{3}$，$P(B) = 1 - a_1 = \tfrac{1}{3}$。获胜概率可确定为
>
> ```math
> P(\text{winning}) = P(\text{winning}\mid A)\,P(A) + P(\text{winning}\mid B)\,P(B).
> ```
>
> 通过考察相应的常返类并求解一个与 (a) 类似的问题，可以定出 $P(\text{winning}\mid A)$ 与 $P(\text{winning}\mid B)$；在这两种情形里，各常返类的稳态概率都是在『被吸收进该特定常返类』的假设下定义的。先看 $P(\text{winning}\mid A)$。常返类 $\{1A, 2A\}$ 的局部平衡方程与归一化方程为
>
> ```math
> \pi_{1A}\cdot\frac{3}{5} = \pi_{2A}\cdot\frac{1}{5}, \qquad \pi_{1A} + \pi_{2A} = 1 .
> ```
>
> 解之得
>
> ```math
> \pi_{1A} = \frac{1}{4}, \qquad \pi_{2A} = \frac{3}{4},
> ```
>
> 从而得出
>
> ```math
> P(\text{winning}\mid A) = p_{1A,2A}\,\pi_{1A} + p_{2A,2A}\,\pi_{2A} = \pi_{2A} = \frac{3}{4} .
> ```
>
> 类似地，常返类 $\{1B, 2B\}$ 的局部平衡方程与归一化方程为
>
> ```math
> \pi_{1B}\cdot\frac{3}{4} = \pi_{2B}\cdot\frac{1}{8}, \qquad \pi_{1B} + \pi_{2B} = 1 .
> ```
>
> 解之得
>
> ```math
> \pi_{1B} = \frac{1}{7}, \qquad \pi_{2B} = \frac{6}{7},
> ```
>
> 从而得出
>
> ```math
> P(\text{winning}\mid B) = p_{1B,2B}\,\pi_{1B} + p_{2B,2B}\,\pi_{2B} = \pi_{2B} = \frac{6}{7} .
> ```

<!-- ===== PDF p5 ===== -->

> **（续）** 把这些结果合起来，可得
>
> ```math
> P(\text{winning}) = P(\text{winning}\mid A)\,P(A) + P(\text{winning}\mid B)\,P(B) = \frac{3}{4}\cdot\frac{2}{3} + \frac{6}{7}\cdot\frac{1}{3} = \frac{11}{14} \approx 0.79,
> ```
>
> 也就是说，Jack 通过往牌组里塞入额外的牌，使胜率显著地朝有利于自己的方向提高了。
>
> **(d)** Jack 塞牌（slips cards into the deck）之前的期望时间，等于马尔可夫链进入某个常返状态之前的期望时间。设 $\mu_i$ 为从状态 $i$ 出发直到到达常返状态所需的期望时间，则有方程
>
> ```math
> \begin{aligned}
> \mu_1 &= 1 + p_{11}\mu_1 + p_{12}\mu_2 = 1 + \frac{1}{3}\,\mu_1 + \frac{7}{15}\,\mu_2,\\
> \mu_2 &= 1 + p_{21}\mu_1 + p_{22}\mu_2 = 1 + \frac{5}{9}\,\mu_1 + \frac{4}{9}\,\mu_2,
> \end{aligned}
> ```
>
> 解之，得到 Jack 塞牌之前的期望时间
>
> ```math
> \mu_1 = 9.2 .
> ```
>
> **(e)** 设 $S$ 为庄家（dealer）从牌组 #2 换到牌组 #1 的次数，它等于他从牌组 #1 换到牌组 #2 的次数。设 $p = P(S = 0)$，它是『状态的第一次改变就是从状态 1 变到 1A 或 1B』的所有方式之概率总和：
>
> ```math
> p = \left(\frac{2}{15}+\frac{1}{15}\right) + \frac{1}{3}\left(\frac{2}{15}+\frac{1}{15}\right) + \left(\frac{1}{3}\right)^{2}\left(\frac{2}{15}+\frac{1}{15}\right) + \ldots = \frac{1}{1-1/3}\cdot\frac{3}{15} = \frac{3}{10} .
> ```
>
> 另一种做法：$p$ 是下面这个修改后的链（modified chain）从状态 1 出发被某个吸收态（absorbing state，即 1A 或 1B）吸收的概率：
>
> <span style="color:#7f8c8d;">【图】原页此处为修改后的马尔可夫链示意图：从状态 1 出发，以 1A、1B 为吸收态，分支分别标注 (win)／(loss)，可见转移概率 $7/15$、$1/3$、$2/15$、$1/15$ 等。原图由后处理统一插入。</span>
>
> 由于 $P(S > 0) = 1 - p$，且类似地有 $P(S > k+1 \mid S > k) = 1 - p$，应当清楚 $S$ 是一个平移几何（shifted geometric）随机变量，于是
>
> ```math
> p_S(k) = \left(\frac{7}{10}\right)^{k}\frac{3}{10}, \qquad k = 0, 1, 2, \ldots .
> ```

<!-- ===== PDF p6 ===== -->

> **（续）**
>
> **(f)** 注意 (e) 中的 $S$ 就是从 1 到 2 再回到 1 的循环（cycle）总次数。在第 $i$ 个循环中，获胜次数 $W_i$ 是参数 $q = \tfrac{5}{9}$ 的几何随机变量（geometric random variable）。于是 Jack 在塞入额外的牌之前获得的总获胜次数为
>
> ```math
> W = W_1 + W_2 + \ldots + W_S,
> ```
>
> 这是『随机个数个随机变量之和』，且所有变量相互独立。在 $S>0$ 的条件下，$W$ 是『参数为 $p$ 的几何』个『参数为 $q$ 的几何』随机变量之和（各变量条件独立），于是由伯努利过程的分裂（splitting of Bernoulli processes）理论，
>
> ```math
> p_{W\mid S>0}(k) = (1-pq)^{k-1}\,pq, \qquad k = 1, 2, \ldots,
> ```
>
> 其中 $pq = \tfrac{3}{10}\cdot\tfrac{5}{9} = \tfrac{1}{6}$。当 $S = 0$ 时 $W = 0$，于是由全概率（total probability），
>
> ```math
> p_W(k) =
> \begin{cases}
> \dfrac{3}{10}, & k = 0,\\[8pt]
> \dfrac{7}{10}\cdot\left(\dfrac{5}{6}\right)^{k-1}\cdot\dfrac{1}{6}, & k = 1, 2, \ldots .
> \end{cases}
> ```
>
> **(g)** 设 $W$ 为塞牌之前的总获胜次数（如 (f)），类似地设 $L$ 为被吸收之前的总失败次数。由 (d) 知 $E[W+L] = \mu_1 = 9.2$。由 (f) 并用全期望（total expectation）可求 $E[W]$：
>
> ```math
> E[W] = E[W\mid S=0]\,P(S=0) + E[W\mid S>0]\,P(S>0) = \frac{7/10}{1/6} = \frac{42}{10} = 4.2,
> ```
>
> 因为在 $S>0$ 的条件下，获胜次数 $W$ 是参数 $pq = \tfrac{1}{6}$ 的几何随机变量。由期望的线性性（linearity of expectation），
>
> ```math
> E[L - W] = E[W+L] - 2E[W] = 9.2 - 2\cdot 4.2 = 0.8 .
> ```
>
> **(h)** 仍用 $A$ 表示从状态 1 出发被吸收进常返类 $\{1A, 2A\}$ 的概率，则
>
> ```math
> \begin{aligned}
> P(X_n = 2A \mid X_{n+1} = 1A)
> &= \frac{P(X_{n+1} = 1A \mid X_n = 2A)\,P(X_n = 2A)}{P(X_{n+1} = 1A)}\\
> &= \frac{P(X_{n+1} = 1A \mid X_n = 2A)\,P(X_n = 2A \mid A)\,P(A)}{P(X_{n+1} = 1A \mid A)\,P(A)}
> = \frac{p_{2A,1A}\,\pi_{2A}}{\pi_{1A}}\\
> &= \frac{1}{5}\cdot\frac{3}{4}\bigg/\frac{1}{4} = \frac{3}{5} .
> \end{aligned}
> ```
>
> 注意上式右端恰等于 $p_{1A,2A}$，这由局部平衡方程 $\pi_{1A}\,p_{1A,2A} = \pi_{2A}\,p_{2A,1A}$ 立即可见。

---

<!-- ===== PDF p7 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**G1†**</span> <span style="color:#7f8c8d;">（†6.431 必做；对 6.041 为选做挑战题）</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> 设 $a > 0$ 且 $c \ge 0$，则
>
> ```math
> P(X - \mu \ge a) = P(X - \mu + c \ge a + c) \le P\bigl((X-\mu+c)^2 \ge (a+c)^2\bigr) \le \frac{E\bigl[(X-\mu+c)^2\bigr]}{(a+c)^2} = \frac{\sigma^2 + c^2}{(a+c)^2},
> ```
>
> 其中第一个不等式由 $a + c > 0$ 这一事实得到，第二个不等式由马尔可夫不等式（Markov inequality）得到。
>
> 为收紧（tighten）这个界，把 $(\sigma^2+c^2)/(a+c)^2$ 视为 $c$ 的函数，并求使导数为 0 的 $c$。最小值在 $c = \sigma^2/a$ 处取得。因此
>
> ```math
> P(X - \mu \ge a) \le \frac{\sigma^2 + \left(\sigma^2/a\right)^2}{\left(a + \sigma^2/a\right)^2} = \frac{\sigma^2}{\sigma^2 + a^2} .
> ```

<!-- ===== PDF p8 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu　6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability　Fall 2010。有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
