<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 7 解答（Problem Set 7: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 「第 $i$ 次成功发生在第 $j$ 次失败之前」这一事件，等价于第 $i$ 次成功出现在前 $i+j-1$ 次试验之内（因为第 $i$ 次成功必须不晚于紧邻第 $j$ 次失败之前的那一次试验发生）；这也等价于「前 $i+j-1$ 次试验中出现 $i$ 次或更多次成功」的事件（其中成功次数至多可达 $i+j-1$ 次）。设 $S_i$ 为第 $i$ 次成功的时刻，$F_j$ 为第 $j$ 次失败的时刻，$N_k$ 为前 $k$ 次试验中成功的次数（于是 $N_k$ 是 $k$ 次试验下的二项（binomial）随机变量）。因此我们有：
>
> ```math
> P(S_i < F_j) = P(N_{i+j-1} \ge i) = \sum_{k=i}^{i+j-1} \binom{i+j-1}{k}\, p^k (1-p)^{i+j-1-k}
> ```
>
> **(b)** 设 $K$ 为第 $j$ 次失败之前发生成功的次数，$L$ 为到达第 $j$ 次失败所用的试验次数。$L$ 就是一个 $j$ 阶帕斯卡（Pascal）随机变量，只不过其「成功」概率为 $1-p$（因为我们现在关心的是失败而非成功）。代入 $j$ 阶帕斯卡随机变量的公式：
>
> ```math
> E[L] = \frac{j}{1-p}, \qquad \sigma_K^2 = \frac{p}{(1-p)^2}\, j
> ```
>
> <span style="color:#1e8449;">**[note]** 原文此处方差的下标记作 $\sigma_K^2$；按上下文本行讨论的是 $L$ 的矩，应为 $\sigma_L^2$。该数值 $jp/(1-p)^2$ 本身无误，且与下一行 $K$ 的方差相同（因 $\mathrm{Var}(K)=\mathrm{Var}(L-j)=\mathrm{Var}(L)$）。</span>
>
> 由于 $K = L - j$：
>
> ```math
> E[K] = \frac{p}{1-p}\, j, \qquad \sigma_K^2 = \frac{p}{(1-p)^2}\, j
> ```
>
> **(c)** 这个表达式等同于说：我们至少需要 42 次试验才能得到第 17 次成功。因此它可以改述为「前 41 次试验中至多有 16 次成功」。故 $b = 41$，$a = 16$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> 一次成功通话发生的概率为 $p = \dfrac{3}{4}\cdot\dfrac{2}{3} = \dfrac{1}{2}$。
>
> **(a)** 若前两次通话均为失败、第三次为成功，Fred 就会在第三次通话时送出他的第一份样品。由于各次试验相互独立，这一事件序列的概率就是
>
> ```math
> (1-p)(1-p)\,p = \frac{1}{2}\cdot\frac{1}{2}\cdot\frac{1}{2} = \frac{1}{8}
> ```
>
> **(b)** 所求事件要求第 9 次与第 10 次试验失败、第 11 次试验成功。对伯努利（Bernoulli）过程而言，这三次试验的结果与其他任何试验的结果相互独立，故答案同样是
>
> ```math
> (1-p)(1-p)\,p = \frac{1}{8}
> ```
>
> **(c)** 我们要求「到第 2 次到达（arrival）为止的时刻 $L_2$ 恰为 5 次试验」的概率。已知 $p_{L_2}(\ell)$ 是 2 阶帕斯卡 PMF（概率质量函数），于是
>
> ```math
> p_{L_2}(5) = \binom{5-1}{2-1} p^2 (1-p)^{5-2} = 4\cdot\left(\frac{1}{2}\right)^5 = \frac{1}{8}
> ```

<!-- ===== PDF p2 ===== -->

<span style="color:#c0392b;">**Problem 2（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> **(d)** 这里我们要求的是条件概率：在 $L_2$ 的实验值（experimental value）大于 2 的条件下，它等于 5。
>
> ```math
> P(L_2 = 5 \mid L_2 > 2) = \frac{p_{L_2}(5)}{P(L_2 > 2)} = \frac{p_{L_2}(5)}{1 - p_{L_2}(2)} = \frac{\dbinom{5-1}{2-1} p^2 (1-p)^{5-2}}{1 - \dbinom{2-1}{2-1} p^2 (1-p)^{0}} = \frac{4\cdot\left(\tfrac{1}{2}\right)^5}{1-\left(\tfrac{1}{2}\right)^2} = \frac{1}{6}
> ```
>
> **(e)** 「Fred 在需要新供应之前至少完成 5 次通话」的概率，等于「$L_2$ 的实验值大于或等于 5」的概率。
>
> ```math
> P(L_2 \ge 5) = 1 - P(L_2 \le 4) = 1 - \sum_{\ell=2}^{4} \binom{\ell-1}{2-1} p^2 (1-p)^{\ell-2} = 1-\left(\frac{1}{2}\right)^2 - \binom{2}{1}\left(\frac{1}{2}\right)^3 - \binom{3}{1}\left(\frac{1}{2}\right)^4 = \frac{5}{16}
> ```
>
> **(f)** 设离散随机变量 $F$ 表示「在 Fred 第 $m$ 次成功通话（样品用完）之前失败的次数」。由于 $L_m$ 是直到并包含第 $m$ 次成功在内的试验次数，我们有 $F = L_m - m$。给定 Fred 在需要新供应之前共进行 $L_m$ 次通话，我们可以把这 $F$ 次不成功的通话看作另一个参数为 $r$ 的伯努利过程中的诸次试验，其中 $r$ 是「成功」（即遇到一条失望的狗，disappointed dog）的概率，由下式得到：
>
> ```math
> r = P(\text{该处有狗} \mid \text{Fred 未留下样品}) = \frac{P(\text{该处有狗 且 无人应门})}{1 - P(\text{送出一份样品})} = \frac{\dfrac{1}{4}\cdot\dfrac{2}{3}}{1-\dfrac{1}{2}} = \frac{1}{3}
> ```
>
> 我们定义 $X$ 为参数为 $r$ 的伯努利随机变量。于是，在 Fred 用完样品之前「被跳过」的狗的数目 $D_m$，等于 $F$ 个参数均为 $r = \dfrac{1}{3}$ 的伯努利随机变量之和，而 $F$ 本身也是一个随机变量。换言之：
>
> ```math
> D_m = X_1 + X_2 + X_3 + \cdots + X_F
> ```
>
> 注意，$D_m$ 是「个数随机的一列独立随机变量」之和。此外，$F$ 与诸 $X_i$ 相互独立，因为诸 $X_i$ 定义在「无人应门」这一条件情境（conditional universe）之中；在该情境下，该处有没有狗并不影响某次试验成为失败试验的概率。利用课上的结论，可以计算其期望与方差：
>
> ```math
> E[D_m] = E[F]\, E[X]
> ```
>
> ```math
> \mathrm{var}(D_m) = E[F]\,\mathrm{var}(X) + (E[X])^2\,\mathrm{var}(F)
> ```
>
> 其中作如下代入：

<!-- ===== PDF p3 ===== -->

> <span style="color:#7f8c8d;">**（续）**</span>
>
> ```math
> E[F] = E[L_m - m] = \frac{m}{p} - m = m
> ```
>
> ```math
> \mathrm{var}(F) = \mathrm{var}(L_m - m) = \mathrm{var}(L_m) = \frac{m(1-p)}{p^2} = 2m
> ```
>
> ```math
> E[X] = r = \frac{1}{3}, \qquad \mathrm{var}(X) = r(1-r) = \frac{2}{9}
> ```
>
> 最后，代入这些数值，我们得到
>
> ```math
> E[D_m] = m\cdot\frac{1}{3} = \frac{m}{3}
> ```
>
> ```math
> \mathrm{var}(D_m) = m\cdot\frac{2}{9} + \left(\frac{1}{3}\right)^2\cdot 2m = \frac{4m}{9}
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> 我们把随机变量 $T_1$、$T_2$ 看作两个相互独立、速率均为 $\lambda$ 的泊松（Poisson）过程的到达间隔（interarrival）时间，把 $S$ 看作第三个泊松过程（与前两个独立）中速率为 $\mu$ 的到达间隔时间。我们关心的是时间 $Z$ 的期望——即直到「第一个过程已发生 2 次到达」或「第二个过程已发生 1 次到达」二者之一为止的时间。
>
> 若第一次到达来自第二个过程，则这次到达的期望等待时间为 $\frac{1}{\mu+\lambda}$；第一次到达来自第二个过程的概率为 $\frac{\mu}{\mu+\lambda}$。若第一次到达来自第一个过程，则期望等待时间应为第一次到达的等待时间 $\frac{1}{\mu+\lambda}$，再加上合并（merged）过程中下一次到达的期望等待时间。类似地，第一次到达来自第一个过程的概率为 $\frac{\lambda}{\mu+\lambda}$。于是：
>
> ```math
> E[Z] = P(\text{首次到达来自过程 2})\, E[\text{等待时间} \mid \text{首次到达来自过程 2}] + P(\text{首次到达来自过程 1})\, E[\text{等待时间} \mid \text{首次到达来自过程 1}]
> ```
>
> ```math
> = \frac{\mu}{\mu+\lambda}\cdot\frac{1}{\mu+\lambda} + \frac{\lambda}{\mu+\lambda}\cdot\left(\frac{1}{\mu+\lambda}+\frac{1}{\mu+\lambda}\right)
> ```
>
> 经过一些化简，可得
>
> ```math
> E[Z] = \frac{1}{\mu+\lambda} + \frac{\lambda}{\mu+\lambda}\cdot\frac{1}{\mu+\lambda}
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> 纱线上红点（dot）的位置，与裁给某位特定顾客的那段纱线长度之间的关系，可以用随机入射悖论（random incident paradox）来看待。
>
> **(a)** 这里，每段纱线的长度服从指数（exponential）分布。如教材第 298 页所解释，由于指数分布的无记忆性（memorylessness），含红点的那段纱线的长度服从二阶 Erlang（埃尔朗）分布。因此 $E[R] = 2E[L] = \dfrac{2}{\lambda}$。
>
> **(b)** 设想在纱线上按指数间隔作出标记，于是每位顾客所要求的长度都由三个这样的指数分布长度节段构成（因为 $L$ 的 PDF（概率密度函数）是三阶 Erlang 分布）。带红点的那段纱线，其红点将落在这三个节段中的某一个里；由 (a)，该节段的期望长度为 $\frac{2}{\lambda}$，而另外两个节段的期望长度各为 $\frac{1}{\lambda}$。因此，含红点部分的总期望长度为 $\frac{4}{\lambda}$。
>
> 一般地，对「到达间隔分布为 $F_X(x)$ 且相互独立同分布（IID）」的过程而言，任意被选中间隔的期望长度为 $\dfrac{E[X^2]}{E[X]}$。可以看到，对上面各小问，这一公式确实成立。
>
> **(c)** 利用上式，
>
> ```math
> E[L] = \int_0^1 \ell^2 e^{\ell}\, d\ell = \left. e^{\ell}\left(\ell^2 - 2\ell + 2\right) \right]_0^1 = e - 2
> ```
>
> ```math
> E[L^2] = \int_0^1 \ell^3 e^{\ell}\, d\ell = \left. e^{\ell}\left(\ell^3 - 3\ell^2 + 6\ell - 6\right) \right]_0^1 = 6 - 2e
> ```
>
> 故
>
> ```math
> E[R] = \frac{6-2e}{e-2}
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 由 $E[L]=\int_0^1 \ell^2 e^{\ell}\,d\ell$ 可读出本题设定 $f_L(\ell)=\ell e^{\ell}$（$0\le\ell\le 1$）。验证其归一性：$\int_0^1 \ell e^{\ell}\,d\ell = \left.e^{\ell}(\ell-1)\right]_0^1 = 1$，确为合法 PDF。</span>

<!-- ===== PDF p4 ===== -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 5**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 已知在时长 $t$ 内有 $n$ 次到达，因此我们要求的是时长 $s$ 内「额外」到达的次数：
>
> ```math
> p_{M|N}(m \mid n) = \frac{(\lambda s)^{m-n} e^{-\lambda s}}{(m-n)!}, \qquad m \ge n \ge 0
> ```
>
> **(b)** 按定义：
>
> ```math
> p_{N,M}(n, m) = p_{M|N}(m \mid n)\, p_N(n) = \frac{\lambda^{m} s^{m-n}\, t^{n}\, e^{-\lambda(s+t)}}{(m-n)!\, n!}, \qquad m \ge n \ge 0
> ```
>
> **(c)** 按定义：
>
> ```math
> p_{N|M}(n \mid m) = \frac{p_{M,N}(m, n)}{p_M(m)} = \binom{m}{n}\, \frac{s^{m-n}\, t^{n}}{(s+t)^{m}}, \qquad m \ge n \ge 0
> ```
>
> **(d)** 我们要求 $P(N = n \mid M = m)$。给定 $M = m$，这 $m$ 次到达在 0 与 $t+s$ 之间均匀分布。把每次到达视为一次试验：若它发生在时刻 $t$ 之前则记为「成功」，否则记为「失败」。于是在 $M = m$ 的条件下，$N$ 是试验次数为 $m$、成功概率为 $\dfrac{t}{t+s}$ 的二项随机变量。所求概率为：
>
> ```math
> P(N = n \mid M = m) = \binom{m}{n}\left(\frac{t}{t+s}\right)^{n}\left(\frac{s}{t+s}\right)^{m-n}, \qquad m \ge n \ge 0
> ```
>
> **(e)** 我们可以把该期望改写为：
>
> ```math
> E[NM] = E\left[N(M-N) + N^2\right] = E[N]\, E[M-N] + E[N^2] = (\lambda t)(\lambda s) + \left(\mathrm{var}(N) + (E[N])^2\right) = (\lambda t)(\lambda s) + \lambda t + (\lambda t)^2
> ```
>
> 其中第二个等号由泊松过程的独立增量（independent increment）性质得到。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 6**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> 题所述汽车通过检查站的过程，是到达率为 $\lambda = 2$ 辆/分钟的泊松过程。
>
> **(a)** 一阶矩与三阶矩分别为：
>
> ```math
> E[T] = \frac{1}{\lambda} = \frac{1}{2}
> ```
>
> ```math
> E[T^3] = \int_0^{\infty} t^3\, 2e^{-2t}\, dt = \frac{3!}{2^{3}} \underbrace{\int_0^{\infty} \frac{2^{4} t^{3} e^{-2t}}{3!}\, dt}_{=1} = \frac{3}{4}
> ```
>
> 其中我们认出被积函数是一个 4 阶 Erlang PDF，因此它在随机变量整个取值范围上的积分必为 1。

<!-- ===== PDF p5 ===== -->

<span style="color:#c0392b;">**Problem 6（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> **(b)** 泊松过程是无记忆的（memoryless），因此之前 4 分钟内的事件历史不影响未来。所以 $K$ 的条件 PMF 等价于「描述一段时长内泊松到达次数」的无条件 PMF；这里该时长为 $\tau = 6$ 分钟，故 $(\lambda\tau) = 12$：
>
> ```math
> p_K(k) = \frac{12^{k} e^{-12}}{k!}, \qquad k = 0, 1, 2, \ldots
> ```
>
> **(c)** 第一打（12 张）计算机卡片在第 36 辆车到达时用完。记这段总时间为 $D$，则 $D = T_1 + T_2 + \cdots + T_{36}$，其中各独立的 $T_i$ 服从参数 $\lambda = 2$ 的指数分布，因此 $D$ 服从 36 阶 Erlang 分布，其 PDF 与期望分别为：
>
> ```math
> f_D(d) = \frac{2^{36} d^{35} e^{-2d}}{35!}, \qquad d \ge 0
> ```
>
> ```math
> E[D] = 36\, E[T] = 18
> ```
>
> **(d)** 在两个实验中，由于一张卡片在登记 3 辆车后即告用完，我们考虑的都是「3 辆车通过检查站所需的时间」。然而在第二个实验中，注意挑选特定卡片的方式偏向于「服役更久」的卡片。也就是说，我们来到街角的时刻更可能落在较长的到达间隔之内——构成该卡片服役总时间的三个到达间隔之一是按随机入射（random incidence）方式被选中的（见教材 6.2 节末尾）。
>
> **i.** 任何一张特定用完卡片的服务时间为 $Y = T_1 + T_2 + T_3$，因此 $Y$ 由参数 $\lambda = 2$ 的 3 阶 Erlang 分布描述：
>
> ```math
> E[Y] = \frac{3}{\lambda} = \frac{3}{2}, \qquad \mathrm{var}(Y) = \frac{3}{\lambda^2} = \frac{3}{4}
> ```
>
> **ii.** 若某张特定用完卡片的三个到达间隔之一是按随机入射选出的，则其服务时间为 $W = T_1 + T_2 + L$，其中 $L$ 是包含我们到达街角那一刻的到达间隔。按照教材中的论证，$L$ 服从二阶 Erlang 分布，于是 $W$ 由参数 $\lambda = 2$ 的 4 阶 Erlang 分布描述：
>
> ```math
> E[W] = \frac{4}{\lambda} = 2, \qquad \mathrm{var}(W) = \frac{4}{\lambda^2} = 1
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**G1†**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> 为简便起见，引入记号 $N_i = N(G_i)$（$i = 1, \ldots, n$）与 $N_G = N(G)$。于是：
>
> ```math
> P(N_1 = k_1, \ldots, N_n = k_n \mid N_G = k) = \frac{P(N_1 = k_1, \ldots, N_n = k_n,\, N_G = k)}{P(N_G = k)} = \frac{P(N_1 = k_1)\cdots P(N_n = k_n)}{P(N_G = k)}
> ```
>
> ```math
> = \frac{\left(\dfrac{(c_1\lambda)^{k_1} e^{-c_1\lambda}}{k_1!}\right)\cdots \left(\dfrac{(c_n\lambda)^{k_n} e^{-c_n\lambda}}{k_n!}\right)}{\dfrac{(c\lambda)^{k} e^{-c\lambda}}{k!}} = \frac{k!}{k_1!\ldots k_n!}\left(\frac{c_1}{c}\right)^{k_1}\cdots \left(\frac{c_n}{c}\right)^{k_n} = \binom{k}{k_1, \ldots, k_n}\left(\frac{c_1}{c}\right)^{k_1}\cdots \left(\frac{c_n}{c}\right)^{k_n}
> ```

<!-- ===== PDF p6 ===== -->

<span style="color:#c0392b;">**G1†（续）**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">**（续）**</span>
>
> 这一结果可以解释为多项分布（multinomial distribution）。设想我们抛掷一颗 $n$ 面骰子 $k$ 次，其中第 $i$ 面朝上的概率为 $p_i = c_i/c$，则「第 $i$ 面恰好朝上 $k_i$ 次」的概率由上式给出。现在把它与我们手头的泊松过程联系起来：每一面对应一个被我们抽样的区间，而抽到它的概率直接取决于其相对长度。这与如下直观一致：给定某指定区间内的泊松到达总数，这些到达在该区间内是均匀分布的。
>
> <span style="color:#7f8c8d;">†6.431 必做；6.041 选做。（†Required for 6.431; optional for 6.041）</span>

<!-- ===== PDF p7 ===== -->

<span style="color:#7f8c8d;">【页】本页为 MIT OpenCourseWare 版权与引用说明页（MIT OpenCourseWare，http://ocw.mit.edu；6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010；引用与本材料使用条款见 http://ocw.mit.edu/terms），无课程内容，不译。</span>
