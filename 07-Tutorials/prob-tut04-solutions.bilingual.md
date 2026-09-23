<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Tutorial 4 解答（Tutorial 4: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology · Department of Electrical Engineering & Computer Science（麻省理工学院 电气工程与计算机科学系）</span>

> <span style="color:#1e8449;">**[note]** 原解答 PDF 仅印出解答正文、未附题目文字（第 2、3 题只给出教材出处），以下按原页题号完整翻译解答内容。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

<span style="color:#00838f;">**(a)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 由标准正态随机变量 $X$ 的 CDF（累积分布函数）$\Phi$：
>
> ```math
> P(X \le 1.5) = \Phi(1.5) = 0.9332.
> ```
>
> <span style="color:#1e8449;">**[mathtip]** 标准正态分布关于 $0$ 对称，故 $P(X \le -1) = P(X \ge 1) = 1 - \Phi(1)$。</span>
>
> ```math
> P(X \le -1) = 1 - P(X \le 1) = 1 - \Phi(1) = 1 - 0.8413 = 0.1587.
> ```

<span style="color:#00838f;">**(b)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 计算 $\dfrac{Y-1}{2}$ 的期望（expectation）与方差（variance）：
>
> ```math
> E\!\left[\frac{Y-1}{2}\right] = \frac{E[Y]-1}{2} = 0.
> ```
>
> ```math
> \mathrm{var}\!\left(\frac{Y-1}{2}\right) = \frac{\mathrm{var}(Y)}{2^2} = \frac{\mathrm{var}(Y)}{4} = 1.
> ```
>
> 因此，$\dfrac{Y-1}{2}$ 的分布为 $N(0, 1)$（标准正态分布）。

<span style="color:#00838f;">**(c)**</span>

> <span style="color:#2471a3;">**[solution]**</span> 对区间 $-1 \le Y \le 1$ 的两端作同一标准化代换：
>
> ```math
> P(-1 \le Y \le 1) = P\!\left(\frac{-1-1}{2} \le \frac{Y-1}{2} \le \frac{1-1}{2}\right) = \Phi(0) - \Phi(-1) = \Phi(0) - (1 - \Phi(1)) = 0.3413.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span> 见教材（textbook）第 169 页例 3.15（Example 3.15）。解答见教材正文。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span> 见教材第 191 页习题 3.20（Problem 3.20）。解答见线上解答（online solutions）。

<!-- ===== PDF p2 ===== -->

<span style="color:#7f8c8d;">**（本页为 MIT OpenCourseWare 版权/引用说明页）**</span>

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课程）· http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。</span>

<span style="color:#7f8c8d;">有关引用本材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
