<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis and Applied Probability）**</span>

<span style="color:#c0392b;">**Recitation 15 解答（Recitation 15: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 10 月 28 日）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 设 $X$ 为直到第一只灯泡失效为止所经历的时间。设 $A$（相应地，$B$）为"第一只灯泡是 A 型（相应地，B 型）"这一事件。由于两只灯泡被选中的可能性相等，由 total expectation theorem（全期望定理）可得
>
> > ```math
> > E[X] = E[X \mid A]\, P(A) + E[X \mid B]\, P(B) = 1 \cdot \frac{1}{2} + \frac{1}{3} \cdot \frac{1}{2} = \frac{2}{3}.
> > ```
>
> **(b)** 设 $D$ 为"时刻 $t$ 之前没有灯泡失效"这一事件。利用 total probability theorem（全概率定理）以及两种灯泡寿命的 exponential distribution（指数分布），我们得到
>
> > ```math
> > P(D) = P(D \mid A)\, P(A) + P(D \mid B)\, P(B) = \frac{1}{2}\, e^{-t} + \frac{1}{2}\, e^{-3t}.
> > ```
>
> **(c)** 我们有
>
> > ```math
> > P(A \mid D) = \frac{P(A \cap D)}{P(D)} = \frac{\frac{1}{2}\, e^{-t}}{\frac{1}{2}\, e^{-t} + \frac{1}{2}\, e^{-3t}} = \frac{1}{1 + e^{-2t}}.
> > ```
>
> **(d)** 设第一只 A 型灯泡的寿命为 $X_A$，其 PDF（probability density function，概率密度函数）为：
>
> > ```math
> > f_{X_A}(x) = \begin{cases} e^{-x}, & x \geq 0, \\ 0, & \text{其他}. \end{cases}
> > ```
>
> 设 $Y$ 为两只 B 型灯泡的寿命之和。由于每只 B 型灯泡的寿命服从参数 $\lambda = 3$ 的指数分布，其和 $Y$ 服从参数 $\lambda = 3$ 的二阶 Erlang distribution（爱尔朗分布）。$Y$ 的 PDF 为：
>
> > ```math
> > f_Y(y) = \begin{cases} 9y\, e^{-3y}, & y \geq 0, \\ 0, & \text{其他}. \end{cases}
> > ```
>
> 于是
>
> > ```math
> > \begin{aligned}
> > P(G) &= P(Y \geq X_A) \\
> > &= \int_{-\infty}^{\infty} f_Y(y) \int_{-\infty}^{y} f_{X_A}(x)\, dx\, dy \\
> > &= \int_0^{\infty} \int_0^{y} 9y\, e^{-3y}\, e^{-x}\, dx\, dy = 9 \int_0^{\infty} y\, e^{-3y} \left[-e^{-x}\right]_{x=0}^{x=y} dy \\
> > &= 9 \int_0^{\infty} y\, e^{-3y}\left(1 - e^{-y}\right) dy = 9 \int_0^{\infty} y\, e^{-3y}\, dy - 9 \int_0^{\infty} y\, e^{-4y}\, dy \\
> > &= 9\left[-\frac{y}{3}\, e^{-3y} - \frac{1}{9}\, e^{-3y} + \frac{y}{4}\, e^{-4y} + \frac{1}{16}\, e^{-4y}\right]_{y=0}^{y=\infty} = 9\left[\frac{1}{9} - \frac{1}{16}\right] = \frac{7}{16}.
> > \end{aligned}
> > ```
>
> 还有一种不涉及积分的更简单解法，思路如下：我们所关心的那些灯泡失效时刻（第 1 只 A 型灯泡失效的时刻、第 2 只 B 型灯泡失效的时刻）可以视为

<!-- ===== PDF p2 ===== -->

> **（续）** 两个速率分别为 $\lambda_A = 1$ 与 $\lambda_B = 3$ 的独立 Poisson process（泊松过程）的到达时刻。我们可以把这两个过程想象成是从一个速率 $\lambda_A + \lambda_B$ 的联合泊松过程中 split（分裂）出来的：联合过程每次到达时，以 $P(A) = \dfrac{\lambda_A}{\lambda_A + \lambda_B} = 1/4$ 的概率分给过程 A，以 $P(B) = \dfrac{\lambda_B}{\lambda_A + \lambda_B} = 3/4$ 的概率分给过程 B。这样一来，我们只需关注联合过程的每次到达究竟分给了过程 A 还是过程 B。联合过程的每次到达对应一次独立试验，它只有两种可能结果：该到达以概率 $P(A)$ 交给过程 A，或以概率 $P(B)$ 交给过程 B。于是，我们所关心的事件发生在"第一次到达分给 A"，或"第一次到达分给 B 且第二次到达分给 A"这两种情形之一出现时。因此对应的概率为
>
> > ```math
> > P(A \text{ 或 } BA) = P(A) + P(BA) = P(A) + P(B)\, P(A) = 7/16.
> > ```
>
> **(e)** 设 $V$ 为过程运行期间 B 型灯泡所提供的总照明时长。设 $N$ 为前 12 只灯泡中 B 型灯泡的数目，并设 $X_i$ 为第 $i$ 只 B 型灯泡所提供的照明时长。于是 $V = X_1 + \cdots + X_N$。<span style="color:#1e8449;">**[note]** 原文此处记作 $V = Y_1 + \cdots + Y_N$，其中 $Y_i$ 与前一句定义的 $X_i$（第 $i$ 只 B 型灯泡的照明时长）指同一对象，下文公式统一使用 $X_i$；且 (d) 小问中 $Y$ 已被用来表示两只 B 型灯泡的总寿命，原文符号存在冲突，此处照实保留。</span>
>
> 注意 $N$ 是参数为 $n = 12$、$p = 1/2$ 的 binomial random variable（二项随机变量），因此
>
> > ```math
> > E[N] = 6, \qquad \mathrm{var}(N) = 12 \cdot \frac{1}{2} \cdot \frac{1}{2} = 3.
> > ```
>
> 此外，$E[X_i] = 1/3$，$\mathrm{var}(X_i) = 1/9$。利用"随机个数的随机变量之和"的均值与方差公式，我们得到
>
> > ```math
> > E[V] = E[N]\, E[X_i] = 2, \qquad \mathrm{var}(V) = \mathrm{var}(X_i)\, E[N] + \big(E[X_i]\big)^2 \mathrm{var}(N) = \frac{1}{9} \cdot 6 + \frac{1}{9} \cdot 3 = 1.
> > ```
>
> **(f)** 利用 (a)–(c) 中的记号以及 (c) 的结论，我们有
>
> > ```math
> > \begin{aligned}
> > E[T \mid D] &= t + E[T - t \mid D \cap A]\, P(A \mid D) + E[T - t \mid D \cap B]\, P(B \mid D) \\
> > &= t + 1 \cdot \frac{1}{1 + e^{-2t}} + \frac{1}{3}\left(1 - \frac{1}{1 + e^{-2t}}\right) \\
> > &= t + \frac{1}{3} + \frac{2}{3} \cdot \frac{1}{1 + e^{-2t}}.
> > \end{aligned}
> > ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 总的到达过程由两个独立泊松过程合并（merging）而成，因此它是速率 $\lambda = \lambda_A + \lambda_B = 7$ 的泊松过程。于是，在给定的三分钟区间内到达的工作数 $N$ 是 Poisson random variable（泊松随机变量），满足 $E[N] = 3\lambda = 21$，$\mathrm{var}(N) = 21$，其 PMF（probability mass function，概率质量函数）为
>
> > ```math
> > p_N(n) = \frac{(21)^n e^{-21}}{n!}, \qquad n = 0, 1, 2, \ldots
> > ```
>
> **(b)** 这 10 份工作中的每一份都以概率 $\lambda_A / (\lambda_A + \lambda_B) = 3/7$ 为 A 型，且各份工作之间相互独立。因此这里适用 binomial PMF（二项分布的概率质量函数），所求概率等于
>
> > ```math
> > \binom{10}{3}\left(\frac{3}{7}\right)^3 \left(\frac{4}{7}\right)^7.
> > ```

<!-- ===== PDF p3 ===== -->

> **（续）**
>
> **(c)** 每个未来的到达都以概率 $\lambda_A / (\lambda_A + \lambda_B) = 3/7$ 为 A 型，且各到达之间相互独立。因此，直到第一次 A 型到达为止的到达总数 $K$ 服从参数为 $3/7$ 的 geometric distribution（几何分布）。在第一次 A 型到达之前出现的 B 型到达数等于 $K - 1$，其 PMF 与几何分布的 PMF 形状相同，只是整体向左平移了一个单位。特别地，
>
> > ```math
> > p_K(k) = \frac{3}{7}\left(\frac{4}{7}\right)^k, \qquad k = 0, 1, 2, \ldots
> > ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 事件 $\{X < Y < Z\}$ 可以表示为 $\{X < \min\{Y, Z\}\} \cap \{Y < Z\}$。设 $Y$ 和 $Z$ 分别是两个相互独立的、速率分别为 $\mu$ 与 $\nu$ 的泊松过程的第一次到达时间。把这两个过程合并之后就可以清楚地看到：$Y < Z$ 成立，当且仅当合并过程的第一次到达来自原来速率为 $\mu$ 的那个过程，因此
>
> > ```math
> > P(Y < Z) = \frac{\mu}{\mu + \nu}.
> > ```
>
> 设 $X$ 为第三个独立泊松过程（速率 $\lambda$）的第一次到达时间。现在，$\{X < \min\{Y, Z\}\}$ 成立，当且仅当由速率 $\lambda$ 与 $\mu + \nu$ 的两个过程合并所得泊松过程的第一次到达来自原来速率为 $\lambda$ 的那个过程，因此
>
> > ```math
> > P(X < \min\{Y, Z\}) = \frac{\lambda}{\lambda + \mu + \nu}.
> > ```
>
> 注意，事件 $\{X < \min\{Y, Z\}\}$ 与事件 $\{Y < Z\}$ 是相互独立的，因为速率为 $\mu + \nu$ 的合并过程的第一次到达时间，与该第一次到达究竟来自速率为 $\mu$ 的过程还是速率为 $\nu$ 的过程无关。因此，
>
> > ```math
> > P(X < Y < Z) = P(X < \min\{Y, Z\}) \cdot P(Y < Z) = \frac{\lambda\mu}{(\lambda + \mu + \nu)(\mu + \nu)}.
> > ```

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">【尾页】本页为 MIT OpenCourseWare（麻省理工学院开放式课程）封底版权页：注明课程 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）、Fall 2010 学期，以及引用条款网址 http://ocw.mit.edu/terms，无实质教学内容，不译。</span>
