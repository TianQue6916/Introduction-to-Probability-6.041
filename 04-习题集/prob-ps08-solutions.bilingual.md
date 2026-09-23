<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 8 解答（Problem Set 8: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 我们考虑一个状态为 $0, 1, 2, 3, 4, 5$ 的马尔可夫链（Markov chain），其中状态 $i$ 表示：Oscar 早晨出门跑步之前，前门处有 $i$ 双鞋可用。
>
> 现在可以确定转移概率。设在 Oscar 出发跑步前前门有 $i$ 双鞋：他以 $\frac{1}{2}$ 的概率回到出发时的同一扇门，这样下次跑步之前前门仍会有 $i$ 双鞋；另一种情况是，他以 $\frac{1}{2}$ 的概率回到另一扇门，此时下次跑步之前前门的鞋数为 $\min\{i+1, 5\}$ 或 $\max\{i-1, 0\}$（两者以相等概率出现）。这些转移概率如下图中的马尔可夫链所示：
>
> <span style="color:#7f8c8d;">【图】原页此处为马尔可夫链状态转移图（状态 $0\sim 5$：状态 0 与状态 5 的自环概率为 $3/4$，状态 1–4 的自环概率为 $1/2$；相邻状态之间的转移概率各为 $1/4$）。原图由后处理统一插入。</span>
>
> **(b)** 当前门处有 0 双或 5 双鞋时，Oscar 以 $\frac{1}{2}$ 的概率恰好从没有鞋的那扇门出发跑步，因而只能赤脚跑步（run barefooted）。为求 Oscar 长期赤脚跑步的比例，必须求出处于状态 0 与状态 5 的稳态概率（steady-state probabilities）$\pi_0$ 与 $\pi_5$。注意，稳态概率是存在的，因为该链是常返的（recurrent）且非周期的（aperiodic）。
>
> 由于这是一个生灭过程（birth-death process），可以使用局部平衡方程（local balance equations）。我们有
>
> ```math
> \pi_0\, p_{01} = \pi_1\, p_{10}
> ```
>
> 由此得
>
> ```math
> \pi_1 = \pi_0
> ```
>
> 类似地，
>
> ```math
> \pi_5 = \ldots = \pi_1 = \pi_0
> ```
>
> 由
>
> ```math
> \sum_{i=0}^{5} \pi_i = 1
> ```
>
> 可得 $\pi_i = \dfrac{1}{6}$（$i = 0, 1, \ldots, 5$）。因此：
>
> ```math
> P(\text{Oscar 长期来看赤脚跑步}) = \frac{1}{2}\left(\pi_0 + \pi_5\right) = \frac{1}{6}
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 考虑 $X_1, X_2, \ldots, X_t$ 的任何一列可能取值 $x_1, x_2, \ldots, x_{t-1}, i$，并注意：
>
> ```math
> P\left(|X_{t+1}| = |i|+1 \mid X_t = i,\, X_{t-1} = x_{t-1},\, \ldots,\, X_1 = x_1\right) = \begin{cases} \dfrac{1}{2} & 0 < |i| < m \\[4pt] 1 & i = 0 \\[4pt] 0 & |i| = m \end{cases}
> ```
>
> ```math
> P\left(|X_{t+1}| = |i| \mid X_t = i,\, X_{t-1} = x_{t-1},\, \ldots,\, X_1 = x_1\right) = \begin{cases} \dfrac{1}{2} & |i| = m \\[4pt] 0 & |i| \ne m \end{cases}
> ```

<!-- ===== PDF p2 ===== -->

<span style="color:#c0392b;">**Problem 2（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> ```math
> P\left(|X_{t+1}| = |i|-1 \mid X_t = i,\, X_{t-1} = x_{t-1},\, \ldots,\, X_1 = x_1\right) = \begin{cases} \dfrac{1}{2} & 0 < |i| \le m \\[4pt] 0 & i = 0 \end{cases}
> ```
>
> ```math
> P\left(|X_{t+1}| = j \mid X_t = i,\, X_{t-1} = x_{t-1},\, \ldots,\, X_1 = x_1\right) = 0, \qquad \bigl|\,|i| - j\,\bigr| > 1
> ```
>
> 由于上面的条件概率只依赖于 $|i|$（其中 $|X_t| = |i|$），故 $|X_1|, |X_2|, \ldots$ 满足马尔可夫性（Markov property）。与之对应的马尔可夫链如下图所示：
>
> <span style="color:#7f8c8d;">【图】原页此处为 $\lvert X_t\rvert$ 对应马尔可夫链的状态转移图（状态 $0,1,\ldots,m$：状态 0 以概率 1 转移到 1；状态 $1,\ldots,m-1$ 向上、向下转移的概率各为 $1/2$；状态 $m$ 处自环概率 $1/2$、向 $m-1$ 转移概率 $1/2$）。原图由后处理统一插入。</span>
>
> **(b)** 注意，当 $m > 1$ 时 $Y_1, Y_2, \ldots$ 不是马尔可夫链，因为对 $0 < d < m$：
>
> ```math
> P\left(Y_{t+1} = d+1 \mid Y_t = d,\, Y_{t-1} = d-1\right) = \frac{1}{2}
> ```
>
> 并不等于
>
> ```math
> P\left(Y_{t+1} = d+1 \mid Y_t = d,\, Y_{t-1} = d,\, Y_{t-2} = d-1\right) = 0
> ```
>
> （其道理是：若 $Y_{t-2} = d-1$、$Y_{t-1} = d$、$Y_t = d$，则 $|X_t| = d-1$；而若 $Y_{t-1} = d-1$、$Y_t = d$，则 $|X_t| = d$。）
>
> 然而，若我们同时记录 $|X_t|$ 与 $Y_t$，则确实得到一个马尔可夫链。因为对 $(|X_1|, Y_1), \ldots, (|X_{t-1}|, Y_{t-1}), (|X_t|, Y_t)$ 的任何一列可能取值 $(x_1, y_1), \ldots, (x_{t-1}, y_{t-1}), (i_1, i_2)$，都有：
>
> ```math
> P\left((|X_{t+1}|, Y_{t+1}) = (i_1+1,\, i_2+1) \mid (|X_t|, Y_t) = (i_1, i_2),\, \ldots,\, (|X_1|, Y_1) = (x_1, y_1)\right) = \begin{cases} \dfrac{1}{2} & 0 < i_1 = i_2 < m \\[4pt] 1 & i_1 = i_2 = 0 \\[4pt] 0 & \text{其他} \end{cases}
> ```
>
> ```math
> P\left((|X_{t+1}|, Y_{t+1}) = (i_1-1,\, i_2) \mid (|X_t|, Y_t) = (i_1, i_2),\, \ldots,\, (|X_1|, Y_1) = (x_1, y_1)\right) = \begin{cases} \dfrac{1}{2} & 0 < i_1 \le i_2 \le m \\[4pt] 0 & \text{其他} \end{cases}
> ```
>
> ```math
> P\left((|X_{t+1}|, Y_{t+1}) = (i_1,\, i_2) \mid (|X_t|, Y_t) = (i_1, i_2),\, \ldots,\, (|X_1|, Y_1) = (x_1, y_1)\right) = \begin{cases} \dfrac{1}{2} & i_1 = i_2 = m \\[4pt] 0 & \text{其他} \end{cases}
> ```
>
> <span style="color:#1e8449;">**[note]** 原文仅列出上列三式。当 $i_1 < i_2$ 时，三式给出的概率合计只有 $1/2$；结合下一页状态转移图与 $Y_t$ 的含义（截至 $t$ 时刻的最大偏差 $Y_t=\max\{|X_1|,\ldots,|X_t|\}$）可知，此时还应有转移 $(i_1+1,\, i_2)$（概率 $1/2$），且 $(0,\,j)\to(1,\,j)$ 的概率为 $1$（$j>0$），这样各情形概率之和才为 1。</span>
>
> 由此显然，这些条件概率只依赖于 $(i_1, i_2)$，即 $|X_t|$ 与 $Y_t$ 的取值。对应的马尔可夫链如下图所示。

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">【图】原页此处为 $(\lvert X_t\rvert, Y_t)$ 配对链的状态转移图（状态为 $(i, j)$、$0 \le i \le j \le m$，按第二坐标 $j$ 分层排列：底层为 $(0,0)$，其上为 $(0,1),(1,1)$，直至顶层 $(0,m),(1,m),\ldots,(m-1,m),(m,m)$；图中标注 $1/2$ 与 $1$ 的转移概率，$(m,m)$ 处有 $1/2$ 自环）。原图由后处理统一插入。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 若 $n$ 名个体中有 $m$ 名被感染，则必有 $n - m$ 名易感（susceptible）个体。在一天之内，这些个体中的每一名都会以概率 $\rho = 1 - (1-p)^m$ 被独立地感染。于是，新增感染人数 $I$ 是参数为 $n - m$ 与 $\rho$ 的二项随机变量，即：
>
> ```math
> p_I(k) = \binom{n-m}{k}\, \rho^{k} (1-\rho)^{n-m-k}, \qquad k = 0, 1, \ldots, n-m
> ```
>
> **(b)** 取 SIS 模型的状态为「被感染个体的数目」。当 $n = 2$ 时，对应的马尔可夫链如下图所示：
>
> <span style="color:#7f8c8d;">【图】原页此处为 SIS 模型（$n=2$）的马尔可夫链状态转移图（状态 $0,1,2$：$P(0\to0)=1$；$P(1\to2)=p(1-q)$、$P(1\to0)=q(1-p)$、$P(1\to1)=pq+(1-p)(1-q)$；$P(2\to1)=2q(1-q)$、$P(2\to0)=q^2$、$P(2\to2)=(1-q)^2$）。原图由后处理统一插入。</span>
>
> **(c)** 唯一的常返状态是「感染人数为 0」的状态。
>
> **(d)** 取 SIR 模型的状态为 $(S, I)$，其中 $S$ 为易感个体数、$I$ 为感染个体数。当 $n = 2$ 时，对应的马尔可夫链如下图所示：

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">【图】原页此处为 SIR 模型（$n=2$）的马尔可夫链状态转移图（状态 $(S,I)\in\{(0,0),(1,0),(2,0),(0,1),(1,1),(0,2)\}$，转移概率标注为 $(1-p)q$、$pq$、$q$、$2q(1-q)$、$(1-p)(1-q)$、$(1-q)$、$p(1-q)$、$(1-q)^2$）。原图由后处理统一插入。</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> 如果在无人感染时不想区分「易感者」与「康复者」的细分情况，可以把三个「零感染」状态合并为单一状态，如下图所示：
>
> <span style="color:#7f8c8d;">【图】原页此处为合并后的简化马尔可夫链图（以 $(\ast,0)$ 表示统一的零感染状态，其余状态与转移概率标注同上）。原图由后处理统一插入。</span>
>
> **(e)** 任何「感染人数为 0」的状态都是常返状态。当 $n = 2$ 时，依 (d) 中所画马尔可夫链的不同，常返状态可以是一个或三个。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 该过程在第一次转移之前处于状态 3。过程一旦离开状态 3，就再也无法回到状态 3。因此，$J$——表示「直到并包含过程最后一次离开状态 3 的那次转移」为止的转移次数——是成功概率为 0.6 的几何（geometric）随机变量。$J$ 的方差为：
>
> ```math
> \sigma_J^2 = \frac{1-p}{p^2} = \frac{10}{9}
> ```

<!-- ===== PDF p5 ===== -->

<span style="color:#c0392b;">**Problem 4（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> **(b)** 存在正的概率使我们永远不进入状态 4，即 $P(K < \infty) < 1$。因此 $K$ 的期望值为 $\infty$。
>
> **(c)** 该马尔可夫链有 3 个不同的常返类（recurrent classes）：第一常返类由状态 $\{1, 2\}$ 组成，第二常返类由状态 $\{7\}$ 组成，第三常返类由状态 $\{4, 5, 6\}$ 组成。从瞬态（transient）状态 3 出发被吸收进第一常返类的概率为：
>
> ```math
> \frac{1/10}{1/10 + 2/10 + 3/10} = \frac{1}{6}
> ```
>
> 即「给定发生一次状态改变」时转移到第一常返类的概率。类似地，被吸收进第二、第三常返类的概率分别为 $\dfrac{3}{6}$ 与 $\dfrac{2}{6}$。
>
> 接下来，我们在每个常返类内部求解平衡方程（balance equations），得到「给定从状态 3 被吸收到该常返类」条件下的概率。把条件稳态概率按「被吸收到各常返类的概率」加权，即得无条件的稳态概率。
>
> 第一常返类是生灭过程。我们写出下列方程并求解条件概率，记其为 $p_1$ 与 $p_2$：
>
> ```math
> p_1 = \frac{p_2}{2}
> ```
>
> ```math
> p_1 + p_2 = 1
> ```
>
> 解得 $p_1 = \dfrac{1}{3}$，$p_2 = \dfrac{2}{3}$。对第二常返类，$p_7 = 1$。第三常返类也是生灭过程，其条件稳态概率可如下求得：
>
> ```math
> p_4 = 2p_5
> ```
>
> ```math
> p_5 = 2p_6
> ```
>
> ```math
> p_4 + p_5 + p_6 = 1
> ```
>
> 从而 $p_4 = \dfrac{4}{7}$，$p_5 = \dfrac{2}{7}$，$p_6 = \dfrac{1}{7}$。
>
> 利用这些数据，所有状态的无条件稳态概率求得如下：
>
> ```math
> \pi_1 = \frac{1}{3}\cdot\frac{1}{6} = \frac{1}{18}
> ```
>
> ```math
> \pi_2 = \frac{2}{3}\cdot\frac{1}{6} = \frac{1}{9}
> ```
>
> ```math
> \pi_3 = 0 \quad (\text{瞬态状态})
> ```
>
> ```math
> \pi_7 = 1\cdot\frac{3}{6} = \frac{1}{2}
> ```
>
> ```math
> \pi_4 = \frac{4}{7}\cdot\frac{2}{6} = \frac{4}{21}
> ```
>
> ```math
> \pi_5 = \frac{2}{7}\cdot\frac{2}{6} = \frac{2}{21}
> ```
>
> ```math
> \pi_6 = \frac{1}{7}\cdot\frac{2}{6} = \frac{1}{21}
> ```

<!-- ===== PDF p6 ===== -->

<span style="color:#c0392b;">**Problem 4（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> **(d)** 所给条件事件「过程永不进入状态 4」改变了被吸收到各常返类的概率：被吸收到第一常返类的概率为 $\dfrac{1}{4}$，到第二常返类为 $\dfrac{3}{4}$，到第三常返类为 0。因此稳态概率为：
>
> ```math
> \pi_1 = \frac{1}{3}\cdot\frac{1}{4} = \frac{1}{12}
> ```
>
> ```math
> \pi_2 = \frac{2}{3}\cdot\frac{1}{4} = \frac{1}{6}
> ```
>
> ```math
> \pi_3 = \pi_4 = \pi_5 = \pi_6 = 0
> ```
>
> ```math
> \pi_7 = 1\cdot\frac{3}{4} = \frac{3}{4}
> ```
>
> 出于教学目的，让我们实际画出「给定过程永不进入状态 4」这一事件下新马尔可夫链的样子，所得的链如下图所示。下面看看这些转移概率是如何得出的：
>
> <span style="color:#7f8c8d;">【图】原页此处为条件事件下的新马尔可夫链图（状态 $S_1, S_2, S_3, S_7$：$S_1 \leftrightarrow S_2$ 互转概率各 $1/2$；$S_3$ 自环 $4/10$、转向 $\{1,2\}$ 类 $3/20$、转向 $S_7$ $9/20$；$S_7$ 自环 $1$）。原图由后处理统一插入。</span>
>
> 在对新转移概率作重新缩放（rescaling）时必须小心。首先，显然常返类 $\{S_1, S_2\}$ 与 $\{S_7\}$ 内部的概率不受影响。我们还注意到，瞬态状态 $S_3$ 的自环转移概率也不变（这对任何其他瞬态状态同样成立）。
>
> 为说明自环概率 $p_{3,3}$ 不变，我们以「最终进入 $S_2$ 或 $S_7$」这一事件为条件。记新的自环概率为 $q_{3,3}$，则：
>
> ```math
> q_{3,3} = P(X_1 = S_3 \mid \text{被吸收进 2 或 7},\, X_0 = S_3) = \frac{p_{3,3}\cdot P(\text{被吸收进 2 或 7} \mid X_1 = S_3,\, X_0 = S_3)}{P(\text{被吸收进 2 或 7} \mid X_0 = S_3)} = \frac{p_{3,3}\,(a_{3,2} + a_{3,7})}{(a_{3,2} + a_{3,7})} = p_{3,3} = \frac{4}{10}
> ```
>
> 接下来计算 $q_{3,7}$ 与 $q_{3,2}$：
>
> ```math
> q_{3,7} = P(X_1 = S_7 \mid \text{被吸收进 2 或 7},\, X_0 = S_3) = \frac{p_{3,7}\cdot P(\text{被吸收进 2 或 7} \mid X_1 = S_7,\, X_0 = S_3)}{P(\text{被吸收进 2 或 7} \mid X_0 = S_3)} = \frac{p_{3,7}\cdot 1}{(a_{3,2} + a_{3,7})} = \frac{\dfrac{3}{10}}{\dfrac{1}{6}+\dfrac{1}{2}} = \frac{9}{20}
> ```

<!-- ===== PDF p7 ===== -->

<span style="color:#c0392b;">**Problem 4（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> ```math
> q_{3,2} = P(X_1 = S_2 \mid \text{被吸收进 2 或 7},\, X_0 = S_3) = \frac{p_{3,2}\cdot P(\text{被吸收进 2 或 7} \mid X_1 = S_2,\, X_0 = S_3)}{P(\text{被吸收进 2 或 7} \mid X_0 = S_3)} = \frac{p_{3,2}\cdot 1}{(a_{3,2} + a_{3,7})} = \frac{\dfrac{1}{10}}{\dfrac{1}{6}+\dfrac{1}{2}} = \frac{3}{20}
> ```
>
> 现在，可以计算这条新马尔可夫链的吸收概率。从 $S_3$ 出发被吸收进常返类 $\{1, 2\}$ 的概率为：
>
> ```math
> \frac{\dfrac{3}{20}}{\dfrac{3}{20}+\dfrac{9}{20}} = \frac{1}{4}
> ```
>
> 从 $S_3$ 出发被吸收进常返类 $\{7\}$ 的概率为：
>
> ```math
> \frac{\dfrac{9}{20}}{\dfrac{3}{20}+\dfrac{9}{20}} = \frac{3}{4}
> ```
>
> 可见，我们算得的吸收概率与之前凭直觉得出的概率相符。从这个例子应带走的重要一点是：做这类题目时（即「给定我们进入/不进入某组特定常返类」），必须对新链中出自**所有**瞬态状态的转移概率进行重新缩放。换言之，为求每一个新的转移概率，应以给定事件（进入或不进入特定常返类）为条件。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**G1†**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **a)** 首先设诸 $p_{ij}$ 为该马尔可夫链的转移概率。则：
>
> ```math
> \begin{aligned}
> m_{k+1}(1) &= E\left[R_{k+1} \mid X_0 = 1\right] \\
> &= E\left[g(X_0) + g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1\right] \\
> &= \sum_{i=1}^{n} p_{1i}\, E\left[g(X_0) + g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1,\, X_1 = i\right] \\
> &= \sum_{i=1}^{n} p_{1i}\, E\left[g(1) + g(X_1) + \ldots + g(X_{k+1}) \mid X_1 = i\right] \\
> &= g(1) + \sum_{i=1}^{n} p_{1i}\, E\left[g(X_1) + \ldots + g(X_{k+1}) \mid X_1 = i\right] \\
> &= g(1) + \sum_{i=1}^{n} p_{1i}\, m_k(i)
> \end{aligned}
> ```
>
> 从而一般地，当 $c \in \{1, \ldots, n\}$ 时：
>
> ```math
> m_{k+1}(c) = g(c) + \sum_{i=1}^{n} p_{ci}\, m_k(i)
> ```
>
> 注意，第三个等号正是使用了全期望定理（total expectation theorem）。
>
> **b)**
>
> ```math
> \begin{aligned}
> v_{k+1}(1) &= \mathrm{Var}\left[R_{k+1} \mid X_0 = 1\right] \\
> &= \mathrm{Var}\left[g(X_0) + g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1\right] \\
> &= \mathrm{Var}\left[E\left[g(X_0) + g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1,\, X_1\right]\right] \\
> &\qquad + E\left[\mathrm{Var}\left[g(X_0) + g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1,\, X_1\right]\right]
> \end{aligned}
> ```

<!-- ===== PDF p8 ===== -->

<span style="color:#c0392b;">**G1†（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> ```math
> \begin{aligned}
> &= \mathrm{Var}\left[g(1) + E\left[g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1,\, X_1\right]\right] \\
> &\qquad + E\left[\mathrm{Var}\left[g(1) + g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1,\, X_1\right]\right] \\
> &= \mathrm{Var}\left[E\left[g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1,\, X_1\right]\right] + E\left[\mathrm{Var}\left[g(X_1) + \ldots + g(X_{k+1}) \mid X_0 = 1,\, X_1\right]\right] \\
> &= \mathrm{Var}\left[E\left[g(X_1) + \ldots + g(X_{k+1}) \mid X_1\right]\right] + E\left[\mathrm{Var}\left[g(X_1) + \ldots + g(X_{k+1}) \mid X_1\right]\right] \\
> &= \mathrm{Var}\left[m_k(X_1)\right] + E\left[v_k(X_1)\right] \\
> &= E\left[\left(m_k(X_1)\right)^2\right] - \left(E\left[m_k(X_1)\right]\right)^2 + \sum_{i=1}^{n} p_{1i}\, v_k(i) \\
> &= \sum_{i=1}^{n} p_{1i}\, m_k^2(i) - \left(\sum_{i=1}^{n} p_{1i}\, m_k(i)\right)^2 + \sum_{i=1}^{n} p_{1i}\, v_k(i)
> \end{aligned}
> ```
>
> 从而一般地，当 $c \in \{1, \ldots, n\}$ 时：
>
> ```math
> v_{k+1}(c) = \sum_{i=1}^{n} p_{ci}\, m_k^2(i) - \left(\sum_{i=1}^{n} p_{ci}\, m_k(i)\right)^2 + \sum_{i=1}^{n} p_{ci}\, v_k(i)
> ```
>
> <span style="color:#7f8c8d;">†6.431 必做；6.041 选做。（†Required for 6.431; optional for 6.041）</span>

<!-- ===== PDF p9 ===== -->

<span style="color:#7f8c8d;">【页】本页为 MIT OpenCourseWare 版权与引用说明页（MIT OpenCourseWare，http://ocw.mit.edu；6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010；引用与本材料使用条款见 http://ocw.mit.edu/terms），无课程内容，不译。</span>
