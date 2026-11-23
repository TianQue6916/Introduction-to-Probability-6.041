<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 5 解答（Tutorial 5: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 电气工程与计算机科学系）</span>

> <span style="color:#1e8449;">**[note]** 原解答 PDF 仅印出解答正文、未附题目文字；以下按原页题号完整翻译解答内容（解答本身已含所需的题设上下文）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

<span style="color:#00838f;">**(a)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $A$ 为"机器正常运行（functional）"这一事件。在随机变量 $Q$ 取某个特定值 $q$ 的条件下，$P(A \mid Q = q) = q$。利用全概率定理的连续形式（continuous form of the total probability theorem），事件 $A$ 的概率为：
>
> ```math
> P(A) = \int_0^1 P(A \mid Q = q)\, f_Q(q)\, dq = \int_0^1 q\, dq = \frac{1}{2}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 第二个等号用到了 $P(A \mid Q = q) = q$ 以及 $f_Q(q) \equiv 1$（$0 \le q \le 1$），后者即 $Q$ 服从 $[0,1]$ 上的均匀分布（uniform distribution）。</span>

<span style="color:#00838f;">**(b)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $B$ 为"机器在最近 $n$ 天中有 $m$ 天正常运行"这一事件。在 $Q$ 取值 $q$（即每天正常运行的概率为 $q$）的条件下，事件 $B$ 的（条件）概率由二项（binomial）分布给出：$n$ 次试验、成功 $m$ 次、每次试验成功概率为 $q$。再次利用全概率定理，事件 $B$ 的概率为：
>
> ```math
> P(B) = \int_0^1 P(B \mid Q = q)\, f_Q(q)\, dq = \int_0^1 \binom{n}{m} q^m (1-q)^{n-m} f_Q(q)\, dq = \binom{n}{m}\, \frac{m!\,(n-m)!}{(n+1)!}.
> ```
>
> 然后利用贝叶斯法则（Bayes' rule）求出事件 $B$ 发生条件下 $Q$ 的分布：
>
> ```math
> f_{Q|B}(q) = \frac{P(B \mid Q = q)\, f_Q(q)}{P(B)} = \frac{q^m (1-q)^{n-m}}{\dfrac{m!\,(n-m)!}{(n+1)!}}, \qquad 0 \le q \le 1,\ n \ge m.
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 该后验密度与 $q^m (1-q)^{n-m}$ 成正比，是参数为 $(m+1,\, n-m+1)$ 的 Beta 分布（Beta distribution）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 由于 $Y = |X|$，对任意给定的 $y$，可以把 $Y$ 的 PDF（概率密度函数，probability density function）写成：
>
> ```math
> f_Y(y) =
> \begin{cases}
> f_X(y) + f_X(-y), & \text{if } y \ge 0,\\
> 0, & \text{if } y < 0.
> \end{cases}
> ```
>
> 同时注意：由于 $Y = |X|$，必有 $Y \ge 0$。

<span style="color:#00838f;">**(a)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 此情形下
>
> ```math
> f_X(x) =
> \begin{cases}
> 1/3, & \text{if } -2 < x \le 1,\\
> 0, & \text{otherwise.}
> \end{cases}
> ```
>
> 于是，$-1 \le x \le 0$ 段的 $f_X(x)$ 会被叠加到 $0 \le x \le 1$ 段的 $f_X(x)$ 上：
>
> ```math
> f_Y(y) =
> \begin{cases}
> 2/3, & \text{if } 0 \le y \le 1,\\
> 1/3, & \text{if } 1 < y \le 2,\\
> 0, & \text{otherwise.}
> \end{cases}
> ```

<!-- ===== PDF p2 ===== -->

**（续）**

<span style="color:#00838f;">**(b)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本小问已知 $X > 0$，因此不存在需要考虑的 $X$ 的负值。于是
>
> ```math
> f_Y(y) = f_X(y) =
> \begin{cases}
> 2e^{-2y}, & \text{if } y \ge 0,\\
> 0, & \text{otherwise.}
> \end{cases}
> ```

<span style="color:#00838f;">**(c)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 如开头所解释，$f_Y(y) = f_X(y) + f_X(-y)$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 我们要计算救护车（ambulance）行驶时间 $T$ 的 CDF（累积分布函数，cumulative distribution function）：$P(T \le t) = P(|X - Y| \le vt)$，其中 $X$ 与 $Y$ 分别为救护车与事故地点的位置（在 $[0, l]$ 上均匀分布（uniform））。由于 $X$ 与 $Y$ 相互独立（independent），可知：
>
> ```math
> f_{X,Y}(x, y) =
> \begin{cases}
> 1/l^2, & \text{if } 0 \le x, y \le l,\\
> 0, & \text{otherwise.}
> \end{cases}
> ```
>
> ```math
> P(T \le t) = P(|X - Y| \le vt) = P(-vt \le Y - X \le vt) = P(X - vt \le Y \le X + vt).
> ```
>
> 可以看出，$P(X - vt \le Y \le X + vt)$ 对应于 $X$ 与 $Y$ 的联合密度（joint density）在下图阴影区域上的积分：
>
> <span style="color:#7f8c8d;">【图】原页此处为示意图：$x$-$y$ 平面上的 $[0,l] \times [0,l]$ 正方形，夹在两条直线 $y = x + vt$ 与 $y = x - vt$ 之间的带状区域为阴影，旁注 $f_{X,Y}(x, y) = 1/l^2$。原图由后处理统一插入。</span>
>
> 因此，由于联合密度在整个区域上均匀，我们有：
>
> ```math
> F_T(t) = (1/l^2) \times (\text{Shaded area}) =
> \begin{cases}
> 0, & \text{if } t < 0,\\[6pt]
> \dfrac{2lvt - (vt)^2}{l^2}, & \text{if } 0 \le t < l/v,\\[8pt]
> 1, & \text{if } t \ge l/v.
> \end{cases}
> ```
>
> <span style="color:#1e8449;">**[note]**</span> 阴影面积的表达式在源 PDF 文本层缺损为 $2vt-(vt)^2$（缺少因子 $l$）；按几何（带状区域是边长 $l\sqrt{2}$ 的正方形被两条相距 $2vt/\sqrt{2}$ 的平行线所截，面积为 $2lvt-(vt)^2$）及边界条件 $F_T(l/v)=1$、与下式 $f_T(t)$ 求导自洽，分子应为 $2lvt-(vt)^2$，已按数学正确形式还原。
>
> 对 CDF 求导，即得 $T$ 的密度：
>
> ```math
> f_T(t) =
> \begin{cases}
> \dfrac{2lv - 2v^2 t}{l^2}, & \text{if } 0 \le t \le l/v,\\[8pt]
> 0, & \text{otherwise.}
> \end{cases}
> ```

<!-- ===== PDF p3 ===== -->

<span style="color:#7f8c8d;">**（本页为 MIT OpenCourseWare 版权/引用说明页）**</span>

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课程）· http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。</span>

<span style="color:#7f8c8d;">有关引用本材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
