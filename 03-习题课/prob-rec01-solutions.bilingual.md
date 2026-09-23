<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 1 解答（Recitation 1: Solutions）**</span> <span style="color:#7f8c8d;">（September 9, 2010，2010 年 9 月 9 日）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> 由于事件 $A\cap B^{c}$ 与 $A^{c}\cap B$ 互不相交（disjoint），由可加性公理（additivity axiom）可得
>
> ```math
> P\big((A\cap B^{c})\cup(A^{c}\cap B)\big)=P(A\cap B^{c})+P(A^{c}\cap B).
> ```
>
> 又因 $A=(A\cap B)\cup(A\cap B^{c})$ 是两个互不相交集合之并，再次由可加性公理得
>
> ```math
> P(A)=P(A\cap B)+P(A\cap B^{c}),
> ```
>
> 从而
>
> ```math
> P(A\cap B^{c})=P(A)-P(A\cap B).
> ```
>
> 同理，
>
> ```math
> P(B\cap A^{c})=P(B)-P(A\cap B).
> ```
>
> 因此，
>
> ```math
> P(A\cap B^{c})+P(A^{c}\cap B)=P(A)-P(A\cap B)+P(B)-P(A\cap B)=P(A)+P(B)-2P(A\cap B).
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设
>
> - $A$：随机选出的一名学生是天才（genius）这一事件；
> - $B$：随机选出的一名学生热爱巧克力（loves chocolate）这一事件。
>
> 由课堂上证明过的概率律（probability laws）性质，有
>
> ```math
> \begin{aligned}
> 1&=P(A\cup B)+P\big((A\cup B)^{c}\big)\\
> &=P(A)+P(B)-P(A\cap B)+P(A^{c}\cap B^{c})\\
> &=0.6+0.7-0.4+P(A^{c}\cap B^{c})\\
> &=0.9+P(A^{c}\cap B^{c}).
> \end{aligned}
> ```
>
> 因此
>
> ```math
> P(\text{随机选出的学生既不是天才也不热爱巧克力})=P(A^{c}\cap B^{c})=1-0.9=0.1.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $c$ 表示单个奇数面（odd face）的概率，则单个偶数面（even face）的概率为 $2c$。把 3 个奇数面与 3 个偶数面的概率相加，得 $9c=1$，故 $c=1/9$。所求概率为
>
> ```math
> P(\{1,2,3\})=P(\{1\})+P(\{2\})+P(\{3\})=c+2c+c=4c=\frac{4}{9}.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">**[solution]**</span> 见教材（textbook）例 1.5（Example 1.5），第 13 页。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem G1**†</span>

> <span style="color:#2471a3;">**[solution]**</span> 见教材习题 1.13（Problem 1.13），第 56 页。

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms</span>
