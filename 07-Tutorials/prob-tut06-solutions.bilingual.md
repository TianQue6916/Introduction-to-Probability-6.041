<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 6 解答（Tutorial 6: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 电气工程与计算机科学系）</span>

> <span style="color:#1e8449;">**[note]** 原解答 PDF 仅印出解答正文、未附题目文字；以下按原页题号完整翻译解答内容（解答本身已含所需的题设上下文）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $Z = X + Y$。使用两步 CDF 方法（2-step CDF method）：
>
> ```math
> F_Z(z) = P(Z \le z) = P(X + Y \le z).
> ```
>
> 利用全概率定理（Total Probability Theorem），有
>
> ```math
> F_Z(z) = \sum_x p_X(x)\, P(x + Y \le z) = \sum_x p_X(x)\, P(Y \le z - x) = \sum_x p_X(x)\, F_Y(z - x).
> ```
>
> 两边对 $z$ 求导，得
>
> ```math
> f_Z(z) = \frac{d}{dz} F_Z(z) = \sum_x p_X(x)\, f_Y(z - x).
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 对 $x$ 求和表明 $X$ 为离散随机变量（以 PMF（概率质量函数）$p_X$ 描述），而 $f_Y$ 为连续密度，故这是离散-连续混合情形的卷积（convolution）公式。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 我们以 $X$ 为条件，使用全方差定律（law of total variance）：
>
> ```math
> \mathrm{var}(X + Y) = E\big[\mathrm{var}(X + Y \mid X)\big] + \mathrm{var}\big(E[X + Y \mid X]\big).
> ```
>
> 给定 $X$ 的取值 $x$，随机变量 $Y$ 在区间 $[x, x+1]$ 上均匀分布，而随机变量 $X + Y$ 在区间 $[2x, 2x+1]$ 上均匀分布。因此 $E[X + Y \mid X] = 0.5 + 2X$，$\mathrm{var}(X + Y \mid X) = 1/12$。于是
>
> ```math
> \mathrm{var}(X + Y) = \mathrm{var}(0.5 + 2X) + E[1/12] = 4\,\mathrm{var}(X) + E[1/12] = \frac{5}{12}.
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 由 $4\,\mathrm{var}(X) + 1/12 = 5/12$ 可知本题中 $\mathrm{var}(X) = 1/12$。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

<span style="color:#00838f;">**(a)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 设 $X_i$ 为相互独立的伯努利（Bernoulli）随机变量，若第 $i$ 次抛掷结果为正面（heads）则取值为 1。设 $N$ 为抛硬币的总次数。我们有 $E[X_i] = 1/2$、$\mathrm{var}(X_i) = 1/4$、$E[N] = 7/2$、$\mathrm{var}(N) = 35/12$（最后一个等式由离散均匀（discrete uniform）随机变量的方差公式得到）。因此，正面出现次数的期望为
>
> ```math
> E[X_i]\, E[N] = \frac{7}{4},
> ```
>
> 方差为
>
> ```math
> \mathrm{var}(X_i)\, E[N] + \big(E[X_i]\big)^2\, \mathrm{var}(N) = \frac{1}{4} \cdot \frac{7}{2} + \frac{1}{4} \cdot \frac{35}{12} = \frac{77}{48}.
> ```

<span style="color:#00838f;">**(b)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本小问的试验可以视为由 (a) 小问的试验独立重复（independent repetitions）两次构成。因此，均值与方差都翻倍，分别变为 $7/2$ 与 $77/24$。

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">**（本页为 MIT OpenCourseWare 版权/引用说明页）**</span>

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课程）· http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。</span>

<span style="color:#7f8c8d;">有关引用本材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
