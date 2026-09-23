<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 21 解答（Recitation 21: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；2010 年 11 月 23 日）</span>

<span style="color:#7f8c8d;">麻省理工学院电气工程与计算机科学系（Massachusetts Institute of Technology, Department of Electrical Engineering & Computer Science）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)** 为了使用 Markov inequality（马尔可夫不等式），令 $X=\sum_{i=1}^{10}X_i$。则
>
> ```math
> E[X]=10\,E[X_i]=5
> ```
>
> 马尔可夫不等式给出
>
> ```math
> P(X\ge 7)\le\frac{5}{7}=0.7142
> ```
>
> **(b)** 用 Chebyshev inequality（切比雪夫不等式），可得
>
> ```math
> 2P(X-5\ge 2)=P(|X-5|\ge 2)\le\frac{\mathrm{var}(X)}{4}=\frac{10/12}{4}=\frac{5}{24}
> ```
>
> ```math
> P(X-5\ge 2)\le\frac{5}{48}=0.1042
> ```
>
> **(c)** 最后，用 Central Limit Theorem（中心极限定理），可得
>
> ```math
> P\Bigl(\sum_{i=1}^{10}X_i\ge 7\Bigr)=1-P\Bigl(\sum_{i=1}^{10}X_i\le 7\Bigr)
> ```
>
> ```math
> =1-P\Biggl(\frac{\sum_{i=1}^{10}X_i-5}{\sqrt{10/12}}\le\frac{7-5}{\sqrt{10/12}}\Biggr)\approx 1-\Phi(2.19)\approx 0.0143
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> <span style="color:#7f8c8d;">本题解答请参见网上发布的版本（Check online solutions）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> **(a)** 若把 $X_i$ 解释为速率为 $1$ 的 Poisson process（泊松过程）中长度为 $1$ 的区间内的到达次数，那么 $S_n=X_1+\cdots+X_n$ 就可以看成该速率为 $1$ 的泊松过程在长度为 $n$ 的区间内的到达次数。因此 $S_n$ 是均值与方差都等于 $n$ 的 Poisson（泊松）随机变量。
>
> **(b)** 我们利用随机变量 $X_1,\ldots,X_n$ 以及随机变量 $S_n=X_1+\cdots+X_n$。记 $Z$ 为 standard normal（标准正态）随机变量，并应用 central limit theorem（中心极限定理）。对较大的 $n$，有

<!-- ===== PDF p2 ===== -->

> **（续）**
>
> ```math
> \begin{aligned}
> P(S_n=n)&=P\Bigl(n-\tfrac{1}{2}<S_n<n+\tfrac{1}{2}\Bigr)\\
> &=P\Bigl(-\frac{1}{2\sqrt{n}}<\frac{S_n-n}{\sqrt{n}}\le\frac{1}{2\sqrt{n}}\Bigr)\\
> &\approx P\Bigl(-\frac{1}{2\sqrt{n}}<Z\le\frac{1}{2\sqrt{n}}\Bigr)\\
> &=\int_{-1/(2\sqrt{n})}^{1/(2\sqrt{n})}\frac{1}{\sqrt{2\pi}}\,e^{-z^2/2}\,dz\\
> &\approx\frac{1}{\sqrt{2\pi}}\sqrt{\frac{1}{n}}\;e^{-z^2/2}\Big|_{z=0}=\frac{1}{\sqrt{2\pi n}}
> \end{aligned}
> ```
>
> 其中第一个等号源于「$S_n$ 只取整数值」这一事实；第一个近似由 central limit theorem（中心极限定理）所提示；第二个近似则使用了 fundamental theorem of calculus（微积分基本定理）——小区间上定积分的值，等于区间长度乘以被积函数在该区间内某一点处的取值。由于 $S_n$ 是均值为 $n$ 的 Poisson（泊松）随机变量，故有
>
> ```math
> P(S_n=n)=e^{-n}\,\frac{n^n}{n!}
> ```
>
> 把前述关系结合起来，即得
>
> ```math
> n!\approx n^{n}e^{-n}\sqrt{2\pi n}=\Bigl(\frac{n}{e}\Bigr)^{n}\sqrt{2\pi n}
> ```
>
> 可以证明
>
> ```math
> \lim_{n\to\infty}\frac{n!}{n^{n}e^{-n}\sqrt{2\pi n}}=1
> ```
>
> 所以该近似的 relative error（相对误差）随 $n\to\infty$ 趋于 $0$。一个更精确的估计是
>
> ```math
> n!=n^{n}e^{-n}\sqrt{2\pi n}\;e^{\lambda_n}
> ```
>
> 其中 $\dfrac{1}{12n+1}<\lambda_n<\dfrac{1}{12n}$。不过，这些关系式是无法从中心极限定理推导出来的。
>
> 注意，这一近似的形式最早由 de Moivre（棣莫弗）发现，形如 $n!\approx n^{n+1/2}e^{-n}\cdot(\text{constant})$（常数），他给出了该常数的一个复杂表达式。棣莫弗的朋友 Stirling（斯特林）随后证明：该常数具有简洁的形式 $\sqrt{2\pi}$。

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（http://ocw.mit.edu）　6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010。如需了解这些材料的引用方式或我们的使用条款（Terms of Use），请访问：http://ocw.mit.edu/terms。</span>
