<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 9 解答（Recitation 9: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期，2010 年 10 月 7 日）</span>

<span style="color:#1e8449;">**[note]** 本解答 PDF 原文不含题面（各题直接给出解答或教材引用）。为便于阅读，以下各题题面均译自 MIT OCW 同课程配套的《Recitation 9》题目 PDF（官方原文，逐题对应）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

设 $X$ 为参数 $\lambda > 0$ 的 exponential random variable（指数随机变量）。计算 $X$ 属于诸区间 $[n,\, n+1]$（其中 $n$ 为奇数）中某一个的概率。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 我们先对任意非负整数 $n$ 计算 $X$ 落入区间 $[n, n+1]$ 的概率；随后再把所有奇的正整数值 $n$ 对应的概率相加。
>
> 我们本可以在给定区间上对 $X$ 的 PDF 积分，但这里改用 CDF。利用指数随机变量的 CDF：
>
> ```math
> P(n \le X \le n+1) = F_X(n+1) - F_X(n) = \bigl(1 - e^{-\lambda(n+1)}\bigr) - \bigl(1 - e^{-\lambda n}\bigr) = e^{-\lambda n}\bigl(1 - e^{-\lambda}\bigr).
> ```
>
> 由于这些区间互不相交（disjoint），我们可以对所有奇整数 $n$ 将该概率求和，得到所求概率：
>
> ```math
> P(\{X \in [n, n+1] \text{ 对某个奇数 } n\}) = \sum_{n\,\text{为奇数}} e^{-\lambda n}\bigl(1 - e^{-\lambda}\bigr) = \bigl(1 - e^{-\lambda}\bigr)\sum_{k=0}^{\infty} e^{-\lambda(2k+1)}
> ```
>
> ```math
> = \bigl(1 - e^{-\lambda}\bigr)\sum_{k=0}^{\infty} e^{-\lambda}\bigl(e^{-2\lambda}\bigr)^{k} = \bigl(1 - e^{-\lambda}\bigr)\,\frac{e^{-\lambda}}{1 - e^{-2\lambda}}
> ```
>
> ```math
> = \bigl(1 - e^{-\lambda}\bigr)\,\frac{e^{-\lambda}}{\bigl(1 - e^{-\lambda}\bigr)\bigl(1 + e^{-\lambda}\bigr)} = \frac{e^{-\lambda}}{1 + e^{-\lambda}}.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

（教材例 3.13（Example 3.13），第 165 页）指数随机变量是无记忆的（memoryless）。一只新灯泡烧坏前的工作时间 $T$ 是参数为 $\lambda$ 的指数随机变量。Ariadne 打开灯后离开房间，$t$ 个时间单位后回到房间，发现灯泡仍亮着——这对应事件 $A=\{T>t\}$。设 $X$ 为直到灯泡烧坏的额外等待时间。求在给定事件 $A$ 的条件下 $X$ 的 conditional CDF（条件分布函数）。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 见教材（textbook）例 3.13（Example 3.13），第 165 页。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

教材（text）第 191 页习题 3.23（Problem 3.23）。设随机变量 $X$ 与 $Y$ 的 joint PDF（联合概率密度函数）在以 $(0, 0)$、$(0, 1)$、$(1, 0)$ 为顶点的三角形上均匀分布（uniform）。

- **(a)** 求 $X$ 与 $Y$ 的联合 PDF。
- **(b)** 求 $Y$ 的 marginal PDF（边缘概率密度函数）。
- **(c)** 求在给定 $Y$ 条件下 $X$ 的 conditional PDF（条件概率密度函数）。
- **(d)** 求 $E[X \mid Y=y]$，并利用全期望定理（total expectation theorem）以 $E[Y]$ 表示 $E[X]$。
- **(e)** 利用问题的对称性求 $E[X]$ 的值。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 教材第 191 页习题 3.23（Problem 3.23, page 191 in text）。解答见在线解答（online solutions）。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

<span style="color:#1e8449;">**[note]** 解答 PDF 将本题标注为教材第 191 页习题 3.22 第 (i) 小问；配套题目 PDF 中该题的题面如下。</span>

我们有一根单位长度的木棒，要把它折成三段：用均匀 PDF（uniform PDF）随机且独立地在木棒上选取两个点，并在这两点处折断。剩下三段恰好能构成一个三角形的概率是多少？

> <span style="color:#2471a3;">**[solution]**</span>
>
> 教材（text）第 191 页习题 3.22（Problem 3.22）第 (i) 小问（part (i)）。解答见在线解答（online solution）。

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 标准版权尾页：MIT OpenCourseWare, http://ocw.mit.edu, 6.041/6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010；课程内容至此结束。）</span>
