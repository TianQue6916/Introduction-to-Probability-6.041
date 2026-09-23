<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 18 解答（Recitation 18: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；November 9, 2010，2010 年 11 月 9 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）。本件主题为马尔可夫链（Markov chains）。原 PDF 共 4 页，其中 p4 为 MIT OpenCourseWare 版权页；原文只含解答、不含题面。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **a)** 时刻 $n$ 剩余绿鱼的数目完全决定了系统全部历史中与预测未来状态相关的所有信息。因此，绿鱼的数目就是系统的状态，且该过程具有马尔可夫性（Markov property），这是显而易见的：
>
> ```math
> P\left(X_{m+1}=j \mid X_m=i,\ X_{m-1}=i_{m-1},\ \ldots,\ X_1=i_1\right) = P\left(X_{m+1}=j\mid X_m=i\right).
> ```
>
> **b)** 当 $j>i$ 时，显然 $p_{ij}=0$，因为蓝鱼永远不会被涂成绿色。对 $0\le i,\ j\le k$，有：
>
> ```math
> p_{ij} = P(\text{有 } i-j \text{ 条绿鱼被钓起}\mid \text{当前状态}=i) =
> \begin{cases}
> \dfrac{n-i}{n}, & j=i,\\[8pt]
> \dfrac{i}{n}, & j=i-1,\\[8pt]
> 0, & \text{其他情形}
> \end{cases}
> ```
>
> **c)** 状态 0 是吸收态（absorbing state），因为系统以正概率进入该状态，而且一旦进入就会永远留在其中。因此，0 条绿鱼的状态是唯一的常返态（recurrent state），从而其余所有状态都是非常返态（transient）。

<span style="color:#7f8c8d;">【原文注】其后的教材题目因版权限制移除（Textbook problem removed due to copyright restrictions）：Drake, *Fundamentals of Applied Probability Theory*, Problem 5.02。该题（Problem 2）的题面与解答均未收录于本 PDF，故本文件从 Problem 1 直接跳至 Problem 3。</span>

<!-- ===== PDF p2 ===== -->

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **（a）** 令 $A_k$ 为过程在第 $k$ 次试验（trial）首次进入状态 $s_2$ 的事件。要在第 $k$ 次试验首次进入 $s_2$，唯一的方式是：第一次试验进入 $s_3$，在接下来的 $k-2$ 次试验中停留在 $s_3$，最后一次试验进入 $s_2$。于是
>
> ```math
> P(A_k) = p_{03}\cdot p_{33}^{\,k-2}\cdot p_{32} = \left(\frac{1}{3}\right)\left(\frac{1}{4}\right)^{k-2}\left(\frac{1}{4}\right) = \frac{1}{3}\left(\frac{1}{4}\right)^{k-1}\qquad (k=2,3,\ldots)
> ```
>
> **（b）** 令 $A$ 为过程永不进入 $s_4$ 的事件。$A$ 发生有三种可能的方式。前两种是第一次转移从 $s_0$ 到 $s_1$ 或从 $s_0$ 到 $s_5$，这发生的概率为 $\frac{2}{3}$。另一种是第一次转移从 $s_0$ 到 $s_3$，且其后状态的下一次改变是转到状态 $s_2$。我们知道从 $s_0$ 到 $s_3$ 的概率是 $\frac{1}{3}$；在此发生的前提下，若从状态 $s_3$ 发生一次状态改变，则所转移到的是状态 $s_2$ 的概率就是
>
> ```math
> \frac{1/4}{1/4+1/2} = \frac{1}{3}.
> ```
>
> 于是，从 $s_0$ 转移到 $s_3$ 并最终转移到 $s_2$ 的概率是 $\frac{1}{9}$。因此，永不进入 $s_4$ 的概率是
>
> ```math
> \frac{2}{3} + \frac{1}{9} = \frac{7}{9}.
> ```

<!-- ===== PDF p3 ===== -->

**（续 Problem 3）**

> **（c）**
>
> ```math
> P(\{\text{过程进入 } s_2 \text{ 并在下一次试验离开 } s_2\}) = P(\{\text{过程进入 } s_2\})\,P(\{\text{下一次试验离开 } s_2\}\mid\{\text{在 } s_2\})
> ```
>
> ```math
> = \sum_{k=2}^{\infty} P(A_k)\cdot\frac{1}{2} = \sum_{k=2}^{\infty} \frac{1}{3}\left(\frac{1}{4}\right)^{k-1}\cdot\frac{1}{2} = \frac{1}{6}\cdot\frac{1/4}{1-1/4} = \frac{1}{18}.
> ```
>
> **（d）** 该事件只可能在状态转移序列恰如下列时发生：
>
> ```math
> s_0 \longrightarrow s_3 \longrightarrow s_2 \longrightarrow s_1.
> ```
>
> 于是，$P(\{\text{过程在第 3 次试验首次进入 } s_1\}) = p_{03}\cdot p_{32}\cdot p_{21}$：
>
> ```math
> p_{03}\cdot p_{32}\cdot p_{21} = \frac{1}{3}\cdot\frac{1}{4}\cdot\frac{1}{2} = \frac{1}{24}.
> ```
>
> **（e）**
>
> ```math
> P(\{\text{过程在第 } N \text{ 次试验后立即处于 } s_3\}) = P(\{\text{第一次试验转移到 } s_3 \text{ 且随后 } N-1 \text{ 次试验停留在 } s_3\}) = \frac{1}{3}\left(\frac{1}{4}\right)^{n-1}\qquad (n=1,2,3,\ldots)
> ```
>
> <span style="color:#7f8c8d;">† 6.431 必做（Required for 6.431）；6.041 选做（optional for 6.041）。（原文脚注。）</span>

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（http://ocw.mit.edu）· 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability，Fall 2010。有关引用这些材料或使用条款的信息，请访问 http://ocw.mit.edu/terms。（此页为 OCW 版权页。）</span>
