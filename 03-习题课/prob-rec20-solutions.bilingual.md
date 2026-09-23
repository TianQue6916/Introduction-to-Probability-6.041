<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 20 解答（Recitation 20: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 11 月 18 日）</span>

<span style="color:#7f8c8d;">麻省理工学院电气工程与计算机科学系（Massachusetts Institute of Technology, Department of Electrical Engineering & Computer Science）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)** 设 $X_i$ 为指示第 $i$ 个灯泡（bulb）质量的随机变量（「1」表示好灯泡，「0」表示坏灯泡）。各 $X_i$ 为相互独立的 Bernoulli（伯努利）随机变量。令
>
> ```math
> Z_n=\frac{X_1+X_2+\cdots+X_n}{n}
> ```
>
> 则
>
> ```math
> E[Z_n]=p,\qquad \mathrm{var}(Z_n)=\frac{n\,\mathrm{var}(X_i)}{n^2}=\frac{\sigma^2}{n},
> ```
>
> 其中 $\sigma^2$ 为 $X_i$ 的方差。应用 Chebyshev inequality（切比雪夫不等式）得
>
> ```math
> P\bigl(|Z_n-p|\ge\epsilon\bigr)\le\frac{\sigma^2}{n\epsilon^2}
> ```
>
> 当 $n\to\infty$ 时，$\sigma^2/(n\epsilon^2)\to 0$，从而 $P(|Z_n-p|\ge\epsilon)\to 0$。因此 $Z_n$ converges in probability（依概率收敛）到 $p$。
>
> **(b)** 由切比雪夫不等式，
>
> ```math
> P\bigl(|Z_{50}-p|\ge 0.1\bigr)\le\frac{\sigma^2}{50(0.1)^2}
> ```
>
> 由于 $X_i$ 是 Bernoulli random variable（伯努利随机变量），其方差 $\sigma^2=p(1-p)\le \dfrac{1}{4}$。于是
>
> ```math
> P\bigl(|Z_{50}-p|\ge 0.1\bigr)\le\frac{1/4}{50(0.1)^2}=0.5
> ```
>
> **(c)** 由切比雪夫不等式，
>
> ```math
> P\bigl(|Z_n-p|\ge 0.1\bigr)\le\frac{\sigma^2}{n\epsilon^2}\le\frac{1/4}{n(0.1)^2}
> ```
>
> 要保证以概率 $0.95$ 落在所需范围内，需要
>
> ```math
> \frac{1/4}{n(0.1)^2}<0.05
> ```
>
> 由此得 $n\ge 500$。注意，即使对最高的方差（即 $1/4$），$n\ge 500$ 也能保证精度指标（accuracy specification）；方差更小时，保证所需精度所需的 $n$ 也更小。例如，若 $\sigma^2=1/16$，则 $n\ge 125$ 就足够了。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#1e8449;">**[note]** 本题的随机变量设定（可由 (a) 中的计算读出）：$X_n$ 以概率 $1/n$ 取值 $1$、以概率 $1-1/n$ 取值 $0$；$Y_n$ 以概率 $1/n$ 取值 $n$、以概率 $1-1/n$ 取值 $0$。</span>
>
> **(a)**
>
> ```math
> E[X_n]=0\cdot\Bigl(1-\frac{1}{n}\Bigr)+1\cdot\frac{1}{n}=\frac{1}{n}
> ```
>
> ```math
> \mathrm{var}(X_n)=\Bigl(0-\frac{1}{n}\Bigr)^{2}\Bigl(1-\frac{1}{n}\Bigr)+\Bigl(1-\frac{1}{n}\Bigr)^{2}\cdot\frac{1}{n}=\frac{n-1}{n^2}
> ```
>
> ```math
> E[Y_n]=0\cdot\Bigl(1-\frac{1}{n}\Bigr)+n\cdot\frac{1}{n}=1
> ```
>
> ```math
> \mathrm{var}(Y_n)=(0-1)^{2}\Bigl(1-\frac{1}{n}\Bigr)+(n-1)^{2}\cdot\frac{1}{n}=n-1
> ```

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> **(b)** 由切比雪夫不等式，
>
> ```math
> \lim_{n\to\infty}P\Bigl(\Bigl|X_n-\frac{1}{n}\Bigr|\ge\epsilon\Bigr)\le\lim_{n\to\infty}\frac{n-1}{n^2\epsilon^2}=0
> ```
>
> 此外，$\lim_{n\to\infty}\dfrac{1}{n}=0$。因此 $X_n$ 依概率收敛到 $0$。对 $Y_n$，切比雪夫不等式给出
>
> ```math
> \lim_{n\to\infty}P\bigl(|Y_n-1|\ge\epsilon\bigr)\le\lim_{n\to\infty}\frac{n-1}{\epsilon^2}=\infty
> ```
>
> 因此，我们无法通过切比雪夫不等式对 $Y_n$ 的收敛性（convergence）得出任何结论。
>
> **(c)** 对每个 $\epsilon>0$，
>
> ```math
> \lim_{n\to\infty}P\bigl(|Y_n|\ge\epsilon\bigr)\le\lim_{n\to\infty}\frac{1}{n}=0
> ```
>
> 因此 $Y_n$ 依概率收敛到 $0$。
>
> **(d)** 该命题不成立。一个反例（counterexample）就是 $Y_n$：它依概率收敛到 $0$，但其期望对一切 $n$ 都等于 $1$。
>
> **(e)** 利用 Markov bound（马尔可夫界），
>
> ```math
> P\bigl(|X_n-c|\ge\epsilon\bigr)=P\bigl(|X_n-c|^2\ge\epsilon^2\bigr)\le\frac{E\bigl[(X_n-c)^2\bigr]}{\epsilon^2}
> ```
>
> 令 $n\to\infty$ 取极限，得
>
> ```math
> \lim_{n\to\infty}P\bigl(|X_n-c|\ge\epsilon\bigr)=0
> ```
>
> 这就确立了依概率收敛（convergence in probability）。
>
> **(f)** 一个反例是 $Y_n$：$Y_n$ 依概率收敛到 $0$，但是
>
> ```math
> E\bigl[(Y_n-0)^2\bigr]=0\cdot\Bigl(1-\frac{1}{n}\Bigr)+n^2\cdot\frac{1}{n}=n
> ```
>
> 因此
>
> ```math
> \lim_{n\to\infty}E\bigl[(Y_n-0)^2\bigr]=\infty
> ```
>
> 即 $Y_n$ 并不 in the mean square（依均方）收敛到 $0$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)** 不收敛。因为对任意 $i\ge 1$，$X_i$ 都在 $-1.0$ 与 $1.0$ 之间 uniformly distributed（均匀分布）。
>
> **(b)** 收敛，且极限为 $0$。因为对 $\epsilon>0$，
>
> ```math
> \lim_{i\to\infty}P\bigl(|Y_i-0|>\epsilon\bigr)=\lim_{i\to\infty}P\Bigl(\Bigl|\frac{X_i}{i}-0\Bigr|>\epsilon\Bigr)=\lim_{i\to\infty}\bigl[P(X_i>i\epsilon)+P(X_i<-i\epsilon)\bigr]=0
> ```
>
> **(c)** 收敛，且极限为 $0$。因为对 $\epsilon>0$，
>
> ```math
> \lim_{i\to\infty}P\bigl(|Z_i-0|>\epsilon\bigr)=\lim_{i\to\infty}P\bigl(\bigl|(X_i)^i-0\bigr|>\epsilon\bigr)
> ```
>
> ```math
> =\lim_{i\to\infty}\Bigl[P\bigl(X_i>\epsilon^{1/i}\bigr)+P\bigl(X_i<-(\epsilon)^{1/i}\bigr)\Bigr]=\lim_{i\to\infty}\Bigl[\frac{1-\epsilon^{1/i}}{2}+\frac{1-\epsilon^{1/i}}{2}\Bigr]=\lim_{i\to\infty}\bigl(1-\sqrt[i]{\epsilon}\bigr)=0
> ```

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（http://ocw.mit.edu）　6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010。如需了解这些材料的引用方式或我们的使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>
