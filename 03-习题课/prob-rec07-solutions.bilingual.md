<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 7 解答（Recitation 7: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期，2010 年 9 月 30 日）</span>

<span style="color:#1e8449;">**[note]** 本解答 PDF 原文不含题面（各题直接给出解答或教材引用）。为便于阅读，以下各题题面均译自 MIT OCW 同课程配套的《Recitation 7》题目 PDF（官方原文，逐题对应）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

教材（text）第 130 页习题 2.35（Problem 2.35）。试利用单个随机变量情形的期望法则（expected value rule，即对任意函数 $g$ 有 $E[g(X)] = \sum_x g(x)\, p_X(x)$，连续情形把求和换成积分）验证

```math
E[g(X, Y)] = \sum_{x} \sum_{y} g(x, y)\, p_{X,Y}(x, y),
```

再将该法则用于线性函数这一特殊情形，以验证公式

```math
E[aX + bY] = a\,E[X] + b\,E[Y],
```

其中 $a$、$b$ 为给定标量（scalar）。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 见教材（textbook）习题 2.35（Problem 2.35），第 130 页。

> <span style="color:#1e8449;">**[note]** 由单变量法则到第一个式子的推广：把 $(X,Y)$ 看作一个取值在平面点集 $\{(x,y): p_{X,Y}(x,y)>0\}$ 上的「单个」随机变量，套用单变量期望法则即得 $E[g(X,Y)] = \sum_{(x,y)} g(x,y)\, p_{X,Y}(x,y)$（双重求和 $\sum_x\sum_y$ 是其展开写法）。再取线性函数 $g(X,Y) = aX+bY$ 代入并展开：$\sum_x\sum_y (ax+by)\, p_{X,Y}(x,y) = a\sum_x x \sum_y p_{X,Y}(x,y) + b\sum_y y \sum_x p_{X,Y}(x,y) = a\sum_x x\, p_X(x) + b\sum_y y\, p_Y(y) = aE[X] + bE[Y]$。中间一步用到了边缘化（marginalization，由联合分布对另一变量求和得到单变量分布）：$p_X(x)=\sum_y p_{X,Y}(x,y)$，$p_Y(y)=\sum_x p_{X,Y}(x,y)$。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

随机变量 $X$ 与 $Y$ 可取集合 $\{1, 2, 3\}$ 中的任意值。关于二者的 joint PMF（joint probability mass function，联合概率质量函数，即联合分布列）$p_{X,Y}(x,y)$ 已知如下信息，其中标 $*$ 的项未指定（left unspecified）：

<span style="color:#1e8449;">**[note]** 原题中的联合分布表为图片、未随文本提取。下表中带 $*$ 的三项在原题中即「未指定项」；其余六项为题面给定值，已依解答 (a)–(f) 所用数值逐一反推核验。</span>

| $p_{X,Y}(x,y)$ | $y=1$ | $y=2$ | $y=3$ |
|:---:|:---:|:---:|:---:|
| $x=1$ | $1/12$ | $2/12$ | $1/12$ |
| $x=2$ | $2/12$ | $*$ | $1/12$ |
| $x=3$ | $0$ | $*$ | $*$ |

- **(a)** $p_X(1)$ 等于多少？
- **(b)** 试给出在 $X=1$ 条件下 $Y$ 的 conditional PMF（条件分布列）的清晰标注草图（sketch）。
- **(c)** $E[Y \mid X=1]$ 等于多少？
- **(d)** 是否存在对诸未指定项的一种取法，使得 $X$ 与 $Y$ 相互独立？

设 $B$ 为事件「$X \le 2$ 且 $Y \le 2$」。已知在条件 $B$ 之下，随机变量 $X$ 与 $Y$ 条件独立（conditionally independent）。

- **(e)** $p_{X,Y}(2,2)$ 等于多少？（若信息不足以确定答案，请予以说明。）
- **(f)** $p_{X,Y\mid B}(2,2 \mid B)$ 等于多少？（若信息不足以确定答案，请予以说明。）

**（a）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> p_X(1) = P(X=1,\,Y=1) + P(X=1,\,Y=2) + P(X=1,\,Y=3) = 1/12 + 2/12 + 1/12 = 1/3
> ```

**（b）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 解即为如下 conditional PMF（条件分布列）的概写（sketch）：
>
> ```math
> p_{Y|X}(y \mid 1) = \frac{p_{X,Y}(1,\,y)}{p_X(1)} =
> \begin{cases}
> 1/4, & \text{若 } y = 1, \\
> 1/2, & \text{若 } y = 2, \\
> 1/4, & \text{若 } y = 3, \\
> 0, & \text{其余情形（otherwise）}.
> \end{cases}
> ```
>
> 其中 $p_{Y|X}(y \mid x) = P(Y = y \mid X = x)$ 是 conditional PMF（条件分布列）的记号，由定义 $p_{Y|X}(y\mid x) = p_{X,Y}(x,y)/p_X(x)$（即「在 $X=x$ 已知的前提下 $Y$ 取 $y$ 的概率」等于「联合分布取值除以 $X$ 的边缘分布取值」）。

**（c）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> ```math
> E[Y \mid X = 1] = \sum_{y=1}^{3} y\, p_{Y|X}(y \mid 1) = 1\cdot\frac{1}{4} + 2\cdot\frac{1}{2} + 3\cdot\frac{1}{4} = 2
> ```

**（d）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 假设 $X$ 与 $Y$ 相互独立（independent）。由于 $p_{X,Y}(3,1)=0$ 且 $p_Y(1)=1/4$，必有 $p_X(3)=0$。这进一步意味着 $p_{X,Y}(3,2)=0$ 与 $p_{X,Y}(3,3)=0$。于是全部剩余的概率质量（probability mass）都必须落到 $(X,Y)=(2,2)$ 上，使得 $p_{X,Y}(2,2)=5/12$、$p_X(2)=8/12$、$p_Y(2)=7/12$。然而 $p_{X,Y}(2,2)\neq p_X(2)\cdot p_Y(2)$，与独立性假设矛盾；故 $X$ 与 $Y$ 不独立（not independent）。
>
> 一种更简单的论证只用到 $X$ 的两个取值与 $Y$ 的两个取值，且对应的全部四个 $(X,Y)$ 组合的概率均已给定。注意：若 $X$ 与 $Y$ 独立，则 $p_{X,Y}(1,3)/p_{X,Y}(1,1)$ 与 $p_{X,Y}(2,3)/p_{X,Y}(2,1)$ 必须相等，因为二者都必须等于 $p_Y(3)/p_Y(1)$。这一必要等式并不成立，所以 $X$ 与 $Y$ 不独立。

> <span style="color:#1e8449;">**[note]** 第一段论证的跳步逐一补全：</span>
>
> (1) 先算 $p_Y(1)$：对联合分布列按 $y=1$ 列求和得边缘分布，$p_Y(1) = p_{X,Y}(1,1) + p_{X,Y}(2,1) + p_{X,Y}(3,1) = 1/12 + 2/12 + 0 = 3/12 = 1/4$。
>
> (2) 独立性给出 $p_{X,Y}(3,1) = p_X(3)\, p_Y(1)$，即 $0 = p_X(3)\cdot(1/4)$，故 $p_X(3)=0$。
>
> (3) 再由独立性，$p_{X,Y}(3,2) = p_X(3)\, p_Y(2) = 0$，$p_{X,Y}(3,3) = p_X(3)\, p_Y(3) = 0$。
>
> (4) 表中已给定的六项之和为 $1/12 + 2/12 + 1/12 + 2/12 + 1/12 + 0 = 7/12$；概率归一要求全部九项相加为 $1$，故 $p_{X,Y}(2,2) = 1 - 7/12 = 5/12$。
>
> (5) 算 $p_X(2)$、$p_Y(2)$：$p_X(2) = p_{X,Y}(2,1) + p_{X,Y}(2,2) + p_{X,Y}(2,3) = 2/12 + 5/12 + 1/12 = 8/12$；$p_Y(2) = p_{X,Y}(1,2) + p_{X,Y}(2,2) + p_{X,Y}(3,2) = 2/12 + 5/12 + 0 = 7/12$。
>
> (6) 检验独立性：$p_X(2)\, p_Y(2) = (8/12)(7/12) = 56/144 = 7/18$，而 $p_{X,Y}(2,2) = 5/12 = 15/36$；因 $7/18 = 14/36 \neq 15/36$，故 $p_{X,Y}(2,2) \neq p_X(2)\, p_Y(2)$，与独立性矛盾。
>
> 第二段「更简单论证」的由来：若独立，则对任意 $x$ 有 $p_{X,Y}(x,3)/p_{X,Y}(x,1) = \big[p_X(x)\,p_Y(3)\big]/\big[p_X(x)\,p_Y(1)\big] = p_Y(3)/p_Y(1)$，与 $x$ 无关；故应 $p_{X,Y}(1,3)/p_{X,Y}(1,1) = p_{X,Y}(2,3)/p_{X,Y}(2,1)$。但实际 $(1/12)/(1/12) = 1$，而 $(1/12)/(2/12) = 1/2$，二者不相等，故不独立。

**（e）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 已知 $X$ 与 $Y$ 在给定 $B$ 的条件下条件独立（conditionally independent given $B$），故必须有
>
> ```math
> \frac{p_{X,Y}(1,1)}{p_{X,Y}(1,2)} = \frac{p_{X,Y}(2,1)}{p_{X,Y}(2,2)}
> ```
>
> 因为等式中出现的诸 $(X,Y)$ 组合都落在 $B$ 内。于是
>
> ```math
> p_{X,Y}(2,2) = \frac{p_{X,Y}(1,2)\,p_{X,Y}(2,1)}{p_{X,Y}(1,1)} = \frac{(2/12)\,(2/12)}{1/12} = \frac{4}{12} = \frac{1}{3}.
> ```

> <span style="color:#1e8449;">**[note]** 比值等式的推导：给定 $B$ 下 $X,Y$ 条件独立，即对 $B$ 内所有 $(x,y)$ 有 $p_{X,Y\mid B}(x,y) = p_{X\mid B}(x)\, p_{Y\mid B}(y)$。于是对任意使 $(x,1),(x,2)\in B$ 的 $x$，$\dfrac{p_{X,Y\mid B}(x,1)}{p_{X,Y\mid B}(x,2)} = \dfrac{p_{X\mid B}(x)\,p_{Y\mid B}(1)}{p_{X\mid B}(x)\,p_{Y\mid B}(2)} = \dfrac{p_{Y\mid B}(1)}{p_{Y\mid B}(2)}$，与 $x$ 无关。又对 $B$ 内的组合，$p_{X,Y\mid B}(x,y) = p_{X,Y}(x,y)/P(B)$，比值中 $P(B)$ 约掉，故 $p_{X,Y}(x,1)/p_{X,Y}(x,2)$ 也与 $x$ 无关，即 $p_{X,Y}(1,1)/p_{X,Y}(1,2) = p_{X,Y}(2,1)/p_{X,Y}(2,2)$。代入 $p_{X,Y}(1,1)=1/12$、$p_{X,Y}(1,2)=2/12$、$p_{X,Y}(2,1)=2/12$，解出 $p_{X,Y}(2,2)$。</span>

**（f）**

> <span style="color:#2471a3;">**[solution]**</span>
>
> 由于 $P(B)=9/12=3/4$，我们做归一化（normalize），得 $p_{X,Y\mid B}(2,2)=\dfrac{p_{X,Y}(2,2)}{P(B)}=\dfrac{4}{9}$。

> <span style="color:#1e8449;">**[note]** 验算 $P(B)$：$B = \{(1,1),(1,2),(2,1),(2,2)\}$，故 $P(B) = p_{X,Y}(1,1) + p_{X,Y}(1,2) + p_{X,Y}(2,1) + p_{X,Y}(2,2) = 1/12 + 2/12 + 2/12 + 4/12 = 9/12 = 3/4$。归一化即对 $B$ 内的组合把联合概率除以 $P(B)$ 得条件概率，$p_{X,Y\mid B}(2,2) = (4/12)/(9/12) = 4/9$。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

教材（text）第 128 页习题 2.33（Problem 2.33）。一枚正面概率为 $p$ 的硬币被连续、独立地抛掷，直到正面连续出现两次或反面连续出现两次为止。求抛掷次数的期望值。

> <span style="color:#2471a3;">**[solution]**</span>
>
> 见教材（textbook）习题 2.33（Problem 2.33），第 128 页。

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">（本页为 MIT OpenCourseWare 标准版权尾页：MIT OpenCourseWare, http://ocw.mit.edu, 6.041/6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010；课程内容至此结束。）</span>
