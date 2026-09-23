<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 17 解答（Recitation 17: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；November 4, 2010，2010 年 11 月 4 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）。原 PDF 共 3 页，其中 p3 为 MIT OpenCourseWare 版权页；原文只含解答、不含题面。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）** $K$ 服从 Poisson 分布（Poisson distribution），均值为 $\mu = \lambda_c T$：
>
> ```math
> p_K(k) = \frac{(\lambda_c T)^k\,e^{-\lambda_c T}}{k!},\qquad k=0,1,2,\ldots;\quad T\ge 0.
> ```
>
> **（b）**
>
> **i.** $P(\text{有意识反应}) = \dfrac{\lambda_c}{\lambda_c+\lambda_s}$。
>
> **ii.** $P(\text{有意识且正确的反应}) = P(\text{有意识反应})\cdot P(\text{反应正确}\mid \text{有意识反应}) = \dfrac{\lambda_c}{\lambda_c+\lambda_s}\,p_c$。
>
> **（c）** 由于有意识反应与潜意识反应是相互独立地产生的，
>
> ```math
> P(\text{在时段 } T \text{ 内有 } r \text{ 个有意识反应且 } s \text{ 个潜意识反应}) = P(\text{T 内 } r \text{ 个有意识反应})\cdot P(\text{T 内 } s \text{ 个潜意识反应})
> ```
>
> ```math
> = \frac{(\lambda_c T)^r\,e^{-\lambda_c T}}{r!}\cdot\frac{(\lambda_s T)^s\,e^{-\lambda_s T}}{s!}
> ```
>
> **（d）** 令 $X_s$ 为从考试开始到第一个潜意识反应出现的时间，$X_c$ 为从第一个潜意识反应到下一个有意识反应出现的时间。注意 $X_s$ 与 $X_c$ 是相互独立的指数（exponential）随机变量，参数分别为 $\lambda_s$ 与 $\lambda_c$：
>
> ```math
> f_{X_s}(x_s) = \begin{cases}\lambda_s\,e^{-\lambda_s x_s}, & x_s\ge 0,\\[2pt] 0, & \text{其他情形;}\end{cases}
> ```
>
> ```math
> f_{X_c}(x_c) = \begin{cases}\lambda_c\,e^{-\lambda_c x_c}, & x_c\ge 0,\\[2pt] 0, & \text{其他情形.}\end{cases}
> ```
>
> $X = X_s + X_c$，所以它的 PDF 是两个指数分布的卷积（convolution）。当 $x\ge 0$ 时
>
> ```math
> f_X(x) = \int_{-\infty}^{\infty} \lambda_s\,e^{-\lambda_s(x-x_c)}\,\lambda_c\,e^{-\lambda_c x_c}\,dx_c
> ```
>
> ```math
> = \int_0^x \lambda_s\lambda_c\,e^{-\lambda_s x}\,e^{(\lambda_s-\lambda_c)x_c}\,dx_c \qquad(\text{因为 } x-x_c>0)
> ```
>
> ```math
> = \lambda_s\lambda_c\,e^{-\lambda_s x}\int_0^x e^{(\lambda_s-\lambda_c)x_c}\,dx_c = \frac{\lambda_s\lambda_c}{\lambda_s-\lambda_c}\,e^{-\lambda_s x}\left(e^{(\lambda_s-\lambda_c)x}-1\right) \qquad(\text{因为 } \lambda_s\ne\lambda_c)
> ```
>
> ```math
> = \frac{\lambda_s\lambda_c}{\lambda_s-\lambda_c}\left(e^{-\lambda_c x}-e^{-\lambda_s x}\right)
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）** 由于我们求的是直到并包含第一次"成功"在内的"试验"次数，$N$ 是参数为 $p$ 的几何（geometric）随机变量：
>
> ```math
> p_N(n) = (1-p)^{n-1}\,p,\qquad n\ge 1.
> ```

<!-- ===== PDF p2 ===== -->

**（续 Problem 2）**

> **（b）** 开车到每个路口所花的时间服从参数为 $\lambda$ 的指数分布。由于 Shem 在某个给定路口观察到事故的概率是 $p$，两次事故报告之间时间长度的分布是指数分布，但参数为 $p\lambda$（可以从 Poisson 分裂（Poisson splitting）的角度理解）。于是
>
> ```math
> f_Q(q) = (p\lambda)\,e^{-(p\lambda)q},\qquad q\ge 0.
> ```
>
> **（c）** 由于事故报告的到达间隔时间服从参数为 $p\lambda$ 的指数分布，给定时段 $\tau$ 内的到达次数就是参数为 $p\lambda\tau$ 的 Poisson 随机变量。于是
>
> ```math
> P(\text{2 小时内 } m \text{ 次到达}) = p_M(m) = e^{-2p\lambda}\,\frac{(2p\lambda)^m}{m!},\qquad m\ge 0.
> ```
>
> **（d）** 我们可以把打给 Shem 的电台呼叫与事故报告看作两个独立的 Poisson 过程（Poisson process），到达率分别为 $\mu$ 与 $p\lambda$。当两个独立 Poisson 过程合并（join）时，合成过程是到达率为 $\mu+p\lambda$ 的 Poisson 过程；而且某一次到达来自电台呼叫的概率为 $\dfrac{\mu}{\mu+p\lambda}$。由于我们关心的是两次电台呼叫之间的事故报告数，可以把它看作参数为 $\dfrac{\mu}{\mu+p\lambda}$ 的移位几何（shifted Geometric）随机变量。于是
>
> ```math
> p_K(k) = \left(\frac{p\lambda}{\mu+p\lambda}\right)^{k}\left(\frac{\mu}{\mu+p\lambda}\right),\qquad k\ge 0.
> ```
>
> **（e）** 如果我们从某个随机时刻开始观察 Shem 的电台呼叫，那么由 Poisson 到达间隔的无记忆性（memoryless property），从该时刻直到他接到下一个呼叫的时间仍服从参数为 $\mu$ 的指数分布；而且从上一次呼叫直到我们开始观察的那一刻，这段时间也服从参数为 $\mu$ 的指数分布。于是 $W = X_1 + X_2$，其中 $X_1$、$X_2$ 都服从指数分布，即 $W$ 的 PDF 是二阶 Erlang 分布（second order Erlang）：
>
> ```math
> f_W(w) = \mu^2\,w\,e^{-\mu w}.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本题解答见教材（textbook）习题 6.27（Problem 6.27），第 337 页。<span style="color:#7f8c8d;">（原解答仅给出此出处。）</span>

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（http://ocw.mit.edu）· 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010。有关引用这些材料或使用条款的信息，请访问 http://ocw.mit.edu/terms。（此页为 OCW 版权页。）</span>
