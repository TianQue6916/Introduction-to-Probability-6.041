<!-- ===== PDF p451 ===== -->

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）（续）**</span>

<span style="color:#c0392b;">**小节：线性估计与正态模型（Linear Estimation and Normal Models）**</span>

> <span style="color:#7f8c8d;">本页是 §8.4 的续页（内部书页 p443，对应文件页 p451）。承接上一页（单元9 的 Example 8.16，位于「多观测与多参数情形」小节中段）继续 §8.4：覆盖「Linear Estimation and Normal Models」与「The Choice of Variables in Linear Estimation」两个小节段。本页不新增 Example 8.17+，故仍为 §8.4 正文收尾；例号基线停在上一页的 Example 8.16。</span>

线性最小均方（线性 LMS）估计量通常与最小均方（LMS）估计量 $E[\Theta \mid X_1, \ldots, X_n]$（Theta 与误差项的均方估计）不同，因而劣于后者。不过，如果 LMS 估计量恰好是关于观测 $X_1, \ldots, X_n$ 的线性函数，那么它同时也就是线性 LMS 估计量，即这两个估计量重合（coincide）。

一个出现这种情况的重要例子，是对一个正态随机变量（normal random variable）$\Theta$ 基于观测 $X_i = \Theta + W_i$ 进行估计的问题，其中 $W_i$ 是相互独立、均值为零（zero mean）的正态噪声项，且独立于 $\Theta$。这与 Example 8.3 中的模型相同——我们在那里看到，$\Theta$ 的后验分布（posterior distribution）是正态的，且条件均值（conditional mean）是关于观测的线性函数。因此，LMS 估计量与线性 LMS 估计量重合。事实上，本节给出的线性 LMS 估计量公式与 Example 8.3 中后验均值 $\hat{\Theta}$ 的表达式一致（这里记号 $\mu$ 对应于 Example 8.3 中的 $X_0$）。这是下述性质的一个具体表现，且可以证明该性质在更一般情形下也成立：如果 $\Theta, X_1, \ldots, X_n$ 都是一族独立正态随机变量的线性函数，那么 LMS 估计量与线性 LMS 估计量重合。它们还与最大后验（MAP）估计量重合（coincide），因为正态分布是对称且单峰的（symmetric and unimodal）。

> <span style="color:#1e8449;">**[t_note]** 注：这里『三种估计量重合』不是巧合，值得逐一从定义推：LMS=条件期望 $E[\Theta\mid X]$；正态+线性模型下条件期望是关于 $X$ 的线性函数，故它落在线性 LMS 那类估计量里（二者相等）；又因高斯后验是对称单峰，『峰』（MAP）恰落在对称中心=均值（LMS），于是三者是同一个数。跨课程（线性代数 Strang）：『条件期望是线性函数』正是你学过的正交投影——条件期望就是在可测函数空间按 $L^2$ 内积的投影，而在线性子空间上投影恰好是线性算子。</span>

上述讨论引出了对线性 LMS 估计的一个有趣诠释：该估计量与我们若假装所涉及的随机变量都是正态（具有给定的均值、方差和协方差）时所得的估计量完全相同。因此，对线性 LMS 估计存在两种互补的视角：要么把它看作一种计算上的捷径（避开求解一个可能很复杂的 $E[\Theta \mid X_1, \ldots, X_n]$ 公式），要么把它看作一种模型上的简化（用正态分布替代不那么容易处理的分布）。

> <span style="color:#1e8449;">**[t_note]** 注：这一段给出的两条互补视角给出理解线性 LMS 的路线图：①计算捷径——不必解可能很复杂的条件期望 $E[\Theta\mid X_1,\dots,X_n]$，只动均值/方差/协方差；②模型简化——假装一切正态，答案不变（因为正态族里条件期望就是线性的）。先证：第二视角点破『线性约束是这个方法存在的全部代价』——本质上你在逼近一个集合里挑简单的那个，牺牲了在非线性模型下的逼近能力（这正是紧接下段要展开的局限）。</span>

```math
E[\Theta \mid h(X_1), \ldots, h(X_n)] = E[\Theta \mid X_1, \ldots, X_n] .
```

<span style="color:#c0392b;">**小节：线性估计中变量的选择（The Choice of Variables in Linear Estimation）**</span>

让我们指出 LMS 估计与线性 LMS 估计之间一个重要的差别。考虑一个未知随机变量 $\Theta$、观测 $X_1, \ldots, X_n$，以及经变换的观测（transformed observations）$Y_i = h(X_i)$，$i = 1, \ldots, n$，其中函数 $h$ 是一一的（one-to-one）。经变换的观测 $Y_i$ 携带与原始观测 $X_i$ 相同的信息，因此基于 $Y_1, \ldots, Y_n$ 的 LMS 估计量，与基于 $X_1, \ldots, X_n$ 的估计量相同：

另一方面，线性 LMS 估计的成立前提是：观测 $X_1, \ldots, X_n$ 的线性函数这一类估计量中包含对 $\Theta$ 而言足够好的估计；然而这未必总能成立。例如，设想 $\Theta$ 是某个分布的未知方差，而 $X_1, \ldots, X_n$ 表示从该分布中抽取的独立随机变量。那么，期望用 $X_1, \ldots, X_n$ 的线性函数得到 $\Theta$ 的一个好估计便是不合理的。这提示我们，对数据做变换（transform）可能是

> <span style="color:#7f8c8d;">本页正文截至上一行戛然而止（原页正文到「 …transform the 」处结束），属于正常翻页截断，内容在下一页（内部书页 p444）继续。</span>

---

<!-- ===== PDF p452 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

> <span style="color:#7f8c8d;">本文件页位于书本页 444，页眉为「Bayesian Statistical Inference / 444 / Chap. 8」。页首为上一页 §8.4「贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）」收尾的余段（标题带「（续）」），随后本页另起第 8 章正文最后一节 §8.5「总结与讨论（Summary and Discussion）」，为纯叙述段，无例题、无习题。</span>

---

<span style="color:#c0392b;">**§8.4　贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）（续）**</span>

……变换后的观测（transformed observations）的线性函数类中，能够找到对 $\theta$ 的优良估计量（good estimators）。合适的变换（transformations）未必总是显而易见的，但对给定问题（problem）结构的直觉也许会提示一些不错的选择：参见 Problem 17 可获一个简单的例子。

> <span style="color:#1e8449;">**[t_note]** 注：这段讲的是线性族的真实局限与应对：若真值 $\Theta$ 与 $X$ 的关系非线性，$X$ 的原始线性函数里根本找不到好东西，此时对数据做变换 $Y_i=h(X_i)$ 可以『把非线性摆进基底里』。先证：一一变换 $h$ 不丢信息（LMS 在变换前后不变，见上一段公式），但线性 LMS 只对 $X$ 的线性函数建模——所以 Problem 17 专门去估 $\Theta$ 想用 $X^2$（因为 $\mathrm{var}\propto$ 某个关于 $X^2$ 的量）。直觉：线性搜索空间扎不进非线性，就把坐标换到『相对它是线性的』那套底座。</span>

---

<span style="color:#c0392b;">**§8.5　总结与讨论（Summary and Discussion）**</span>

我们引入了统计推断（statistical inference）方法，其目的在于从概率上相关的观测（probabilistically related observations）中，提取关于未知变量或模型的信息。我们把重点放在未知量为一个（可能是多维的）参数 $\theta$ 的情形上，并讨论了假设检验（hypothesis testing）与估计（estimation）问题。我们还区分了贝叶斯（Bayesian）与经典（classical）两种推断方法。

在本章中我们讨论了贝叶斯方法，它把参数当作具有已知先验分布（prior distribution）的随机变量 $\theta$ 来处理。这里所关心的关键对象，是给定观测之后 $\theta$ 的后验分布（posterior distribution）。后验分布原则上可以用贝叶斯准则（Bayes' rule）计算出来，尽管在实践中这可能相当困难。

> <span style="color:#1e8449;">**[t_note]** 注：理解贝叶斯 vs 经典的分水岭就看这一句：贝叶斯把 $\theta$ 当作带先验的随机变量，后验原则上可算——前提是你肯「先验地承诺一个 $\theta$ 的分布」。下一章丢弃先验，$\theta$ 变成未知常数，于是再没有『取平均』，所有结论都要对『每个可能的 $\theta$』同时成立。先证：这是两组记号的分界——本章写条件概率 $p_{X\mid\Theta}$、下一章写 $P(\cdot;\theta)$ 与 $E_\theta[\cdot]$，下标里的 $\theta$ 只是『参数取值』的标签而非随机事件。</span>

最大后验（MAP）准则通过对 $\theta$ 最大化后验分布，是一种既能处理估计问题、又能处理假设检验问题的一般性推断方法。我们还讨论了另外两种参数估计方法：最小均方（LMS，或条件期望）估计量（estimator）与线性最小均方（linear LMS）估计量，二者都基于对 $\theta$ 与其估计值之间均方误差（mean squared error）的最小化。后一种估计量会导致较高的均方误差，但只需简单的计算，仅涉及参数与观测的均值（means）、方差（variances）与协方差（covariances）。在参数与观测均满足正态性（normality）假设的条件下，MAP 准则与这两个 LMS 估计量重合。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页几处符号实体损坏：顶部标准句将「case」OCR 为 `ca.'le`，其完整拼写照上下文恢复为 case；「Problem 1 7」实为「Problem 17」（文件页中段也出现该题号），数字按上下文与相邻题号惯例还原为 17，非臆造；末句「L,£\18」实为受损的「LMS」字样，据其与上文给出的 LMS/linear LMS 定义意思复原为两个 LMS 估计量。</span>

---

<!-- ===== PDF p453 ===== -->

<span style="color:#7f8c8d;">书目页 p445（文件页 p453）。本页页眉为「Sec. 8.5 · Problems · 445」，是**第 8 章章末 Problems（习题区）的起始页**：自本页起 Problem 全章连续编号，从 **Problem 1** 开始。页内含 §8.1 的 Problems 1–2 与 §8.2 的 Problems 3–4 之起始。按规范，习题区 Problem 题干一律保持**英文原题、不翻译**；带 `*` 题的英文 Solution 保留。本页未出现 Example 8.17+；为此单元内第 8 章正文已收尾后的习题区。</span>

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span>

<span style="color:#c0392b;">**Problems（习题）**</span>

---

<span style="color:#c0392b;">**SECTION 8.1. Bayesian Inference and the Posterior Distribution（贝叶斯推断与后验分布）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 1.**</span> Artemisia moves to a new house and she is “fifty-percent sure” that the phone number is 2537267. To verify this, she uses the house phone to dial 2537267, she obtains a busy signal, and concludes that this is indeed the correct number. Assuming that the probability of a typical seven-digit phone number being busy at any given time is <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别该概率数值（源 OCR 作 "1 <ft"）]</span>, what is the probability that Artemisia’s conclusion was correct?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 2.**</span> Nefeli, a student in a probability class, takes a multiple-choice test with 10 questions and 3 choices per question. For each question, there are two equally likely possibilities, independent of other questions: either she knows the answer, in which case she answers the question correctly, or else she guesses the answer with probability of success $1/3$.

(a) Given that Nefeli answered correctly the first question, what is the probability that she knew the answer to that question?

(b) Given that Nefeli answered correctly 6 out of the 10 questions, what is the posterior PMF of the number of questions of which she knew the answer?

---

<span style="color:#c0392b;">**SECTION 8.2. Point Estimation, Hypothesis Testing, and the MAP Rule（点估计、假设检验与 MAP 准则）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 3.**</span> The number of minutes between successive bus arrivals at Alvin’s bus stop is exponentially distributed with parameter $\theta$, and Alvin’s prior PDF of $\theta$ is

```math
f_\Theta(\theta) =
\begin{cases}
100, & \text{if } \theta \in [0,\, 1/5],\\
0, & \text{otherwise}.
\end{cases}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源 OCR 将参数 $\theta$ 误写成 "e"、PDF 误写成 "!e ( O ) =" 且下标乱序（"1 0 0. if 0 [0. 1/5]'"、孤立的 "E"、"O."），上文按该均匀先验的真实语义重建为标准分段函数（$100$ 于 $\theta\in[0,1/5]$，其余为 $0$），数值沿用 OCR 可辨的 $100$ 与区间 $[0,1/5]$，未臆造。</span>

(a) Alvin arrives on Monday at the bus stop and has to wait 30 minutes for the bus to arrive. What is the posterior PDF, and the MAP and conditional expectation estimates of $\theta$?

(b) Following his Monday experience, Alvin decides to estimate $\theta$ more accurately, and records his waiting times for five days. These are 30, 25, 15, 40, and 20 minutes, and Alvin assumes that his observations are independent. What is the posterior PDF, and the MAP and conditional expectation estimates of $\theta$ given the five-day data?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 4.**</span> Students in a probability class take a multiple-choice test with 10 questions and 3 choices per question. A student who knows the answer to a question will answer it correctly, while a student that does not will guess the answer with probability of success $1/3$. Each student is equally likely to belong to one of three categories

---

> <span style="color:#7f8c8d;">衔接下一面（PDF p454）：Problem 4 在源 OCR 中于「…one of three categories」处中断（下一页继续给出三个类别的具体说明与小题）。本页为第 8 章习题区起始页，无需带「（续）」；Problem 4 属跨页续接至下一页正文。</span>

---

<!-- ===== PDF p454 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）**</span> — 习题区续接（Problems，续）

> <span style="color:#7f8c8d;">本页为第 8 章章末 Problems 习题区的延续页（书内页码 446，属 §8.2 的 MAP 准则习题，Problem 4–7 范围）。页首无新节/新标题，为上一页 Problem 4 的后半段（题干承接「…those who know the answer…」，故标注「（续）」），随后为 Problem 5、6 与 Problem 7 之首部。习题题干一律保持英文原题。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 4（续）——类别的 MAP 估计（MAP estimate of the category）**</span>

> <span style="color:#7f8c8d;">本小题题干承接上一页 Problem 4 的开头部分（其前半描述「学生可分三类、每题知道答案与否相互独立」等已在前页给出），本页为它的收尾段。</span>

…those who know the answer to each question with corresponding probabilities $\theta_i$, where $\theta_1 = 0.3$, $\theta_2 = 0.7$, and $\theta_3 = 0.95$ (independent of other questions). Suppose that a randomly chosen student answers $k$ questions correctly.

(a) For each possible value of $k$, derive the MAP estimate of the category that this student belongs to.
(b) Let $M$ be the number of questions that the student knows how to answer. Derive the posterior PMF, and the MAP and LMS estimates of $M$ given that the student answered correctly 5 questions.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 5.**（Example 8.4 的偏硬币问题（biased coin problem）的一个变体）</span>

Consider a variation of the biased coin problem in Example 8.4, and assume the probability of heads, $\theta$, is distributed over $[0, 1]$ according to the PDF

```math
f_\Theta(\theta) \;=\; 2\,[\,\text{[OCR 损坏]}\,],\qquad \theta \in [0, 1],\qquad 0 \;\text{otherwise}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 该先验 PDF $f_\Theta(\theta)$ 的解析式在源 OCR 中残碎到几乎无法辨认：仅可辨「= 2」、分段区间 $\theta \in [0,1]$ 与「0 otherwise」的框架，内层片断（如「4 1」「1]」）无法确定含义。故上式仅还原可辨的结构与约束，**未臆造内层具体函数与数值**；如需严格原文请回查原书页 446。</span>

Find the MAP estimate of $\theta$, assuming that $n$ independent coin tosses resulted in $k$ heads and $n - k$ tails.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 6.**（Professor May B. Hard 判断题目是否困难，MAP 准则）</span>

Professor May B. Hard, who has a tendency to give difficult problems in probability quizzes, is concerned about one of the problems she has prepared for an upcoming quiz. She therefore asks her TA to solve the problem and record the solution time. May's prior probability that the problem is difficult is 0.3, and she knows from experience that the conditional PDF of her TA's solution time $X$, in minutes, is

```math
f_{X\mid\Theta}(x \mid \Theta = 1) =
\begin{cases}
c_1\, e^{-0.04x}, & \text{if } 5 \le x \le 60,\\
0, & \text{otherwise},
\end{cases}
```

if $\theta = 1$ (problem is difficult), and is

```math
f_{X\mid\Theta}(x \mid \Theta = 2) =
\begin{cases}
c_2\, e^{-0.16x}, & \text{if } 5 \le x \le 60,\\
0, & \text{otherwise},
\end{cases}
```

if $\theta = 2$ (problem is not difficult), where $c_1$ and $c_2$ are normalizing constants. She uses the MAP rule to decide whether the problem is difficult.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 两式在源 OCR 中被截断为 `c e − 0.04x` 与 `c2 e − 0.16x` 等碎片，且条件 PDF 记号残缺。上文据可辨数值（指数 $e^{-0.04x}$ / $e^{-0.16x}$、区间 $5\le x\le 60$）及正文「where $C_1$ and $C_2$ are normalizing constants」还原标准的分段归一化指数形式与下标 $c_1,c_2$，未改动任何数值。</span>

(a) Given that the TA's solution time was 20 minutes, which hypothesis will she accept and what will be the probability of error?

(b) Not satisfied with the reliability of her decision, May asks four more TAs to solve the problem. The TAs' solution times are conditionally independent and identically distributed with the solution time of the first TA. The recorded solution times are 10, 25, 15, and 35 minutes. On the basis of the five observations, which hypothesis will she now accept, and what will be the probability of error?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 7.**（两盒取球的盒子身份推断的 MAP 准则）</span>

We have two boxes, each containing three balls: one black and two white in box 1; two black and one white in box 2. We choose one of the boxes at random, where the probability of choosing box 1 is equal to some given $p$, and then draw a ball.

(a) Describe the MAP rule for deciding the identity of the box based on whether the drawn ball is black or white.

> <span style="color:#7f8c8d;">[跨页续接] 本页止于本题的 (a)，后续小题（(b)(c) 等）翻页续接至下一页。</span>

---

<!-- ===== PDF p455 ===== -->

<span style="color:#c0392b;">**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）——章末 Problems（续）**</span>

> <span style="color:#7f8c8d;">书本页 p447（文件页 p455）。页眉为 `Sec. 8.5` 的印刷运行页眉（runhead），下接 `Problems` 与页脚 `447`，故本页处于第 8 章章末 Problems 区（本书页 p445–455），Problem 编号全章连续。本页顶部续接上一页 Problem 7（属 §8.2，Problems 3–9 范围）的第 (b) 小题，随后依次为 Problem 8、带 `*` 的 Problem 9（含英文 Solution）、§8.3 分组标题，以及 Problem 10 与 Problem 11（Problem 11 正文跨页续到下一页）。习题区 Problem 题干保持英文原文，不翻译。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 7（续）——第 (b) 小题**</span>

(b) Assuming that $p = 1/2$, find the probability of an incorrect decision and compare it with the probability of error if no ball had been drawn.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 8.**</span> The probability of heads of a given coin is known to be either $q_0$ (hypothesis $H_0$) or $q_1$ (hypothesis $H_1$) . We toss the coin repeatedly and independently, and record the number of heads before a tail is observed for the first time. We assume that $0 < q_0 < q_1 < 1$, and that we are given prior probabilities $P(H_0)$ and $P(H_1)$. For parts (a) and (b), we also assume that $P(H_0) = P(H_1) = 1/2$.

(a) Calculate the probability that hypothesis $H_1$ is true, given that there were exactly $k$ heads before the first tail.

(b) Consider the decision rule that decides in favor of hypothesis $H_1$ if $k \ge k^*$, where $k^*$ is some nonnegative integer, and decides in favor of hypothesis $H_0$ otherwise. Give a formula for the probability of error in terms of $k^*$, $q_0$, and $q_1$. For what value of $k^*$ is the probability of error minimized? Is there another type of decision rule that would lead to an even lower probability of error?

(c) Assume that $q_0 = 0.3$, $q_1 = 0.7$, and $P(H_1) > 0.7$. How does the optimal choice of $k^*$ (the one that minimizes the probability of error) change as $P(H_1)$ increases from $0.7$ to $1.0$?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 9.**</span> \* Consider a Bayesian hypothesis testing problem involving $m$ hypotheses, and an observation vector $X = (X_1, \ldots, X_n)$. Let $g_n(X_1, \ldots, X_n)$ be the decision resulting from the MAP rule based on $X_1, \ldots, X_n$, and $g_{n-1}(X_1, \ldots, X_{n-1})$ the decision resulting from the MAP rule based on $X_1, \ldots, X_{n-1}$ (i.e., the MAP rule that uses only the first $n-1$ components of the observation vector). Let $\mathbf{x} = (x_1, \ldots, x_n)$ be the realized value of the observation vector, and let

```math
e_n(X_1, \ldots, X_n) = P\bigl(\Theta \ne g_n(X_1, \ldots, X_n) \mid X_1 = x_1, \ldots, X_n = x_n\bigr),
```

```math
e_{n-1}(X_1, \ldots, X_{n-1}) = P\bigl(\Theta \ne g_{n-1}(X_1, \ldots, X_{n-1}) \mid X_1 = x_1, \ldots, X_{n-1} = x_{n-1}\bigr),
```

be the corresponding probabilities of error. Show that

```math
e_n(X_1, \ldots, X_n) \le e_{n-1}(X_1, \ldots, X_{n-1}),
```

so making the MAP decision with extra data cannot increase the probability of error.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 9 中 $e_n$ 与 $e_{n-1}$ 的定义式以及 "Show that" 与 "so making the MAP decision with extra data cannot increase the probability of error" 之间的那条不等式（显示公式）在源 OCR 中被拆散、字符残缺（如 $\Theta \ne g_n$、$g_{n-1}$ 的 `gn-l`、下标 `n-1` 的 `Xn-d` 等仅余零散字样）。上方不等式 $e_n(X_1,\ldots,X_n)\le e_{n-1}(X_1,\ldots,X_{n-1})$ 系依据紧随其后的结论句（"使 MAP 决策多用的数据不会增大误差概率"）与下方 Solution 的表述忠实重建，未臆造任何原文未含的数值或符号。</span>

**Solution.** We view $g_{n-1}(X_1, \ldots, X_{n-1})$ as a special case of a decision rule based on all components $X_1, \ldots, X_n$ of the observation vector. Since the MAP rule $g_n(X_1, \ldots, X_n)$ minimizes the probability of error over all decision rules based on $X_1, \ldots, X_n$, the result follows.

---

<span style="color:#c0392b;">**SECTION 8.3. Bayesian Least Mean Squares Estimation**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 10.**</span> A police radar always overestimates the speed of incoming cars by an amount that is uniformly distributed between 0 and 5 miles/hour. Assume that car speeds are uniformly distributed between 55 and 75 miles/hour. What is the LMS estimate of a car's speed based on the radar's measurement?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 11.**</span> The number $\Theta$ of shopping carts in a store is uniformly distributed between 1 and 100. Carts are sequentially numbered between 1 and $\Theta$. You enter

---

<!-- ===== PDF p456 ===== -->

> <span style="color:#7f8c8d;">书页 p448｜第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）　习题区（Problems）续页。本章页眉为 "Bayesian Statistical Inference / Chap. 8"（书页 448）。本页位于 §8.3 习题组（Problems 10–13）中段：页首为上页已开讲的第一题——Problem 11（续），紧接 Problem 12 与带 `*` 的 Problem 13（后附英文 Solution）。源 OCR 把参数符号 $\theta$ 误识作数字 `8`（如页眉引文 "estimate 8"、"prior distribution of 8"），下文按数学语义还原为 $\theta$，不属于臆造。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 11（续）**</span>

题干保持英文原文：

> the store, observe the number $X$ on the first cart you encounter, assumed uniformly distributed over the range $1,\ldots,\Theta$, and use this information to estimate $\theta$. Find and plot the MAP estimator and the LMS estimator. **Hint:** Note the resemblance with Example 8.2.

> <span style="color:#7f8c8d;">衔接前端（PDF p455）：Problem 11 的题干主体（关于在某商店抽中手推车编号 $X$ 以估计 $\theta$ 的 MAP/LMS 习题）起始于上一页，本页仅为此题的收尾字样。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 12**</span>

题干保持英文原文：

Consider the multiple observation variant of Example 8.2: given that $\Theta = \theta$, the random variables $X_1,\ldots,X_n$ are independent and uniformly distributed on the interval $[0,\theta]$, and the prior distribution of $\Theta$ is uniform on the interval $[0,1]$. Assume that $n > 3$.

(a) Find the LMS estimate of $\theta$, given the values $x_1,\ldots,x_n$ of $X_1,\ldots,X_n$.

(b) Plot the conditional mean squared error of the MAP and LMS estimators, as functions of $x = \max\{x_1,\ldots,x_n\}$, for the case $n = 5$.

(c) If $x$ is held fixed at $x = 0.5$, how do the MAP and the LMS estimates, and the corresponding conditional mean squared errors behave as $n \to \infty$?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 13 \***</span>

题干保持英文原文：

(a) Let $Y_1,\ldots,Y_n$ be independent identically distributed random variables and let $Y = Y_1 + \cdots + Y_n$. Show that

```math
E[Y_1 \mid Y] = \frac{Y}{n}.
```

(b) Let $\Theta$ and $W$ be independent zero-mean normal random variables, with positive integer variances $k$ and $m$, respectively. Use the result of part (a) to find $E[\Theta \mid \Theta + W]$, and verify that this agrees with the conditional expectation formula in Example 8.3. **Hint:** Think of $\Theta$ and $W$ as sums of independent random variables.

(c) Repeat part (b) for the case where $\Theta$ and $W$ are independent Poisson random variables with integer means $\lambda$ and $\mu$, respectively.

<span style="color:#00838f;">**[Solution]**</span> （英文解答保留）

(a) By symmetry, we see that $E[Y_i \mid Y]$ is the same for all $i$. Furthermore,

```math
E[Y_1 + \cdots + Y_n \mid Y] = E[Y \mid Y] = Y.
```

Therefore, $E[Y_1 \mid Y] = Y/n$.

(b) We can think of $\Theta$ and $W$ as sums of independent standard normal random variables:

```math
\Theta = \Theta_1 + \cdots + \Theta_k,
\qquad
W = W_1 + \cdots + W_m.
```

We identify $Y$ with $\Theta + W$ and use the result from part (a), to obtain

```math
E[\Theta \mid \Theta + W] = \frac{k}{k + m}\,(\Theta + W).
```

Thus,

```math
E[\Theta \mid \Theta + W]
= E[\Theta_1 + \cdots + \Theta_k \mid \Theta + W]
= \frac{k}{k + m}\,(\Theta + W).
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Part (b) 的中段（$\Theta$ 与 $W$ 记为独立标准正态变量之和、以及 $E[\Theta\mid\Theta+W]=\frac{k}{k+m}(\Theta+W)$ 的结论式）在源 OCR 中被切成碎片（如 `E[8d e + W] = 8k +`、`E [e} + . . . + ek I e + W] = k/+` 等），现按原书 p448 权威语义还原，未臆造任何数值。</span>

---

<!-- ===== PDF p457 ===== -->

<span style="color:#7f8c8d;">第 8 章章末 Problems（习题区）· 书页 449。页眉「Sec. 8.5 / 449 / Problems」。本页位于第 8 章 Exercises 习题区中部：页首为上一页（书页 448）某带 `*` 习题英文 `Solution` 的收尾（先收尾其 (b) 至末、再给 (c)，题号在上一页页首、本页未再现，故标「续」）；随后本页以引导标题 `SECTION 8.4. Bayesian Linear Least Mean Squares Estimation` 另起 §8.4 的 Problems 14–17（书页 449 属 §8.4 问题区，Problems 14–24）。习题区题干与带 `*` 题的英文 `Solution` 均保持英文原文，不翻译。</span>

<span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页为习题区英文区，以下引用的某带 `*` 习题 Solution 系承接上一页的英文解答跳页收尾；(b) 末句「conditional expectation is of the form」与其后所展示的公式（书上该面「is of the form」与「consistent with」两行之间的展示式）在源 OCR 中被整段丢失，下方以灰注释占位，未臆造公式数值。</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**…（某带 `*` 习题的英文 Solution，续）**</span>

The formula for the conditional mean derived in Example 8.3, specialized to the current context (zero prior mean and a single measurement) shows that the conditional expectation is of the form

（`is of the form` 之后的条件期望展示式，见下灰注释。）

consistent with the answer obtained here.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 「is of the form …」之后的条件期望展示式缺失：书上该面在「is of the form」与「consistent with the answer obtained here.」两行之间的展示式未出现在本页 OCR 中，仅句首引「Example 8.3 的公式在零先验均值、单次量测下的特化」与句尾「consistent with the answer obtained here.」可辨。未臆造该公式。</span>

Step (c). We recall that the sum of independent Poisson random variables is Poisson. Thus the argument in part (b) goes through, by thinking of $\Theta$ and $W$ as sums of $\lambda$ (respectively, $\mu$) independent Poisson random variables with mean one. We then obtain

```math
E\big[\Theta \mid \Theta + W\big] = \quad \text{(结果式在本页 OCR 中缺损)}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式中 `E[Θ|Θ+W] =` 之后的结果表达式缺失（源 OCR 在页底 `E[8 1 8 + W] =` 处截断；式中 `8`=$\Theta$、`A`=$\lambda$、`J.t`=$\mu$。）未臆造该结果数值。</span>

---

<span style="color:#c0392b;">SECTION 8.4. Bayesian Linear Least Mean Squares Estimation</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 14.**</span> Consider the random variables $\Theta$ and $X$ in Example 8.11. Find the linear LMS estimator of $\Theta$ based on $X$, and the associated mean squared error.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 15.**</span> For the model in the shopping cart problem (Problem 11), derive and plot the conditional mean squared error, as a function of the number on the observed cart, for the MAP, LMS, and linear LMS estimators.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 16.**</span> The joint PDF of random variables $X$ and $\Theta$ is of the form

```math
f_{X,\Theta}(x,\theta) =
\begin{cases}
c, & \text{if } (x,\theta) \in S,\\
0, & \text{otherwise},
\end{cases}
```

where $c$ is a constant and $S$ is the set

```math
S = \{\, (x,\theta) \;|\; 0 \le x \le 2,\; 0 \le \theta \le 2,\; x - 1 \le \theta \le x \,\}.
```

We want to estimate $\Theta$ based on $X$.

(a) Find the LMS estimator $g(X)$ of $\Theta$.

(b) Calculate $E\big[(\Theta - g(X))^{2} \mid X = x\big]$, $E[g(X)]$, and $\mathrm{var}(g(X))$.

(c) Calculate the mean squared error $E\big[(\Theta - g(X))^{2}\big]$. Is it the same as $E[\mathrm{var}(\Theta \mid X)]$?

(d) Calculate $\mathrm{var}(\Theta)$ using the law of total variance.

(e) Derive the linear LMS estimator of $\Theta$ based on $X$, and calculate its mean squared error.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上题 (16) 联合 PDF 中 `C`（源 OCR 显示为 `CO`、`Co`）按常量化还原为常数 $c$，`S` 集合中不等式 `0 ≤ x ≤ 2`、`0 ≤ θ ≤ 2`、`x−1 ≤ θ ≤ x`（OCR 的 `0  x  2`）亦如实补齐；均为上下文可辨的确定性信息。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 17.**</span> Let $\Theta$ be a positive random variable, with known mean $\mu$ and variance $\sigma^{2}$, to be estimated on the basis of a measurement $X$ of the form $X = \sqrt{\Theta}\, W$. We assume that $W$ is independent of $\Theta$ with zero mean, unit variance, and known fourth moment $E[W^{4}]$. Thus, the conditional mean and variance of $X$ given $\Theta$ are $0$ and

（条件方差表达式在本页末尾开始、终结于下一页书页 450，见下注。）

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 17 中 `X = v'8 W` 复原为 $X=\sqrt{\Theta}\,W$（`8`=$\Theta$），`J..L`=$\mu$、`(12`=$\sigma^{2}$、`W 4`=$W^{4}$；句末「conditional mean and variance … are 0 and」之后的条件方差表达式与 Problem 17 后续内容跨越到下一页（书页 450），本页止于此。</span>

> <span style="color:#7f8c8d;">衔接下一页（书页 450，PDF p458）：Problem 17 的条件方差表达式及其余小题在下一页继续，本页结尾为 Problem 16/17 区间内的一处强行截断；§8.4 的 Problem 14–24 在本页已出现 14–17。</span>

---

<!-- ===== PDF p458 ===== -->

> <span style="color:#7f8c8d;">本书页（书页 450 = 文件页 458−8）位于**第 8 章　贝叶斯统计推断（Bayesian Statistical Inference）** 的**章末 Problems（习题）区**，属于 §8.4（Problems 14–24）。页眉显示「Bayesian Statistical Inference / Chap. 8 / 450」。本页没有新节标题，是**上一页的延续**：页首为上一页某题（Problem 17）的收尾片段，随后依次为 **Problem 18、Problem 19、Problem 20﹡**。Problem 20﹡ 今日之陈述在本页起头，其英文 `Solution` 续到下一页。</span>

> <span style="color:#7f8c8d;">习题区题干保持英文原文，不翻译；带 `*` 的题的英文 `Solution` 以英文保留（仅标签可中文）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 17（续，页首片段）**</span>

…$,\ $ respectively, so we are essentially trying to estimate the variance of $X$ given an observed value. Find the linear LMS estimator of $\Theta$ based on $X$, and the linear LMS estimator of $\Theta$ based on $X^2$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本段为上一页题意（估计方差）的结尾承接，页首仅残留 "…, respectively, so we are essentially trying to estimate the variance of …" 等碎片；题中的被估参数在 OCR 里时而作 `e` 时而作 `8`，疑均为 $\Theta$，此处按 $\Theta$ 还原并核对其「基于 $X$」与「基于 $X^2$」两种线性 LMS 估计的句式。Problem 17 的完整题面在上一页。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 18. Swallowed Buffon's needle.（呑下布丰之针）**</span>

A doctor is treating a patient who has accidentally swallowed a needle. The key factor in whether to operate on the patient is the length $\ell$ of the needle, which is unknown, but is assumed to be uniformly distributed between $0$ and $a > 0$. We wish to form an estimate of $\ell$ based on $X$, its projected length in an X-ray. We introduce a two-dimensional coordinate system and write

```math
X = \ell \cos\Theta,
```

where $\Theta$ is the acute angle formed by the needle and one of the axes. We assume that $\Theta$ is uniformly distributed in the interval $[0, \pi/2]$, and is independent from $\ell$.

**(a)**  Find the LMS estimator $E[\ell \mid X]$. In particular, derive $F_{\ell\mid X}(x\mid\theta)$, $f_{\ell\mid X}(x\mid\theta)$, $f_X(x)$, $f_{\ell\mid X}(\theta\mid x)$, and then compute $E[\ell \mid X = x]$. Hint: You may find the following integration formulas useful:

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别] 此处的两条积分公式在源 OCR 中被拆成碎片（如 `I J0.2 - c2 do. log (a. + vi0.2 c2 )`、`assignments...`），上下限 `a`、`b` 与被积式中含 $\sqrt{\theta^2-c^2}$、$\log$ 等字样隐约可辨。参考原书 §8.1 同类求导技巧可作如下**解释性重建（非权威原文，仅供占位，勿当原文数值使用）**：</span>

```math
\int_a^b \frac{d\theta}{\sqrt{\theta^2-c^2}}\;=\;
\left.\log\left(\theta + \sqrt{\theta^2-c^2}\right)\right|_a^b,
\qquad
\int_a^b \sqrt{\theta^2-c^2}\;d\theta\;=\;
\left.\tfrac{1}{2}\Big(\theta\sqrt{\theta^2-c^2} - c^2\log\big(\theta+\sqrt{\theta^2-c^2}\big)\Big)\right|_a^b .
```

> <span style="color:#7f8c8d;">请主控方以原书核对上述重建，必要时替换。</span>

**(b)**  Find the linear LMS estimate of $\ell$ based on $X$, and the associated mean squared error.

> <span style="color:#7f8c8d;">题目采用经典「布丰之针（Buffon's needle）呑针」范例，被估量由 OCR 的 `e` 还原为针长 $\ell$、随机夹角还原为 $\Theta$（OCR 偶作 `8`）；$[0,\pi/2]$ 由 OCR 的 `[0, 7r /2]`（`7r` 即 $\pi$）还原，非臆造。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 19.**</span>

Consider a photodetector in an optical communications system that counts the number of photons arriving during a certain interval. A user conveys information by switching a photon transmitter on or off. Assume that the probability of the transmitter being on is $p$. If the transmitter is on, the number of photons transmitted over the interval of interest is a Poisson random variable $\Theta$ with mean $\lambda$. If the transmitter is off, the number of photons transmitted is zero.

Unfortunately, regardless of whether or not the transmitter is on or off, photons may still be detected due to a phenomenon called "shot noise." The number $N$ of detected shot noise photons is a Poisson random variable with mean $\mu$. Thus, the total number $X$ of detected photons is equal to $\Theta + N$ if the transmitter is on, and is equal to $N$ otherwise. We assume that $N$ and $\Theta$ are independent, so that $\Theta + N$ is also Poisson with mean $\lambda + \mu$.

**(a)**  What is the probability that the transmitter was on, given that the photodetector detected $k$ photons?

**(c)**  Describe the MAP rule for deciding whether the transmitter was on.

**(d)**  Find the linear LMS estimator of the number of transmitted photons, based on the number of detected photons.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 传光子系统例中被估量 $\Theta$ 在 OCR 中偶作 `e` 或 `8`，此处按 $\Theta$ 还原；泊松均值 `)`、`λ`、`/1` 分别还原为 $\lambda$、$\lambda$、$\mu$。注意源 OCR 在本小题中直接从 (a) 跳到 (c) 与 (d)，缺了 (b)——疑 (b) 在 OCR 中漏页或确无，编号以源 OCR 为准，未擅自补 (b)。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 20.\*** Estimation with spherically invariant PDFs.**（具有球对称不变的 PDF 的估计）**</span>

Let $\Theta$ and $X$ be continuous random variables with joint PDF of the form

```math
f_{\Theta,X}(\theta, x) = h\big(q(\theta, x)\big),
```

where $h$ is a nonnegative scalar function, and $q(\theta, x)$ is a quadratic function of the form

```math
q(\theta, x) = a\,(\theta - \bar{\theta})^2 + b\,(x - \bar{x})^2 - 2 c\,(\theta - \bar{\theta})(x - \bar{x}).
```

> <span style="color:#7f8c8d;">带 `*` 题的英文 `Solution` 以英文保留于后续页；本页仅为其陈述开头。均值中心由 OCR 的 `0`/`X` 还原为 $\bar{\theta}$/$\,\bar{x}$，二次式下标 `a,b,c` 均为原符号，未臆造数值。</span>

> <span style="color:#7f8c8d;">衔接下一页（PDF p459）：Problem 20﹡ 陈述继续（给出其各子问与英文 `Solution`）。</span>

---

<!-- ===== PDF p459 ===== -->

<span style="color:#7f8c8d;">第 8 章　章末习题（Problems）区——§8.4（贝叶斯/最小二乘类题）续页，书页 451（页眉「Sec. 8.5 / 451」）。本页承接上一页，中段结束前一个带 `*` 习题的解（延续 Problem 编号；其题干已在上一页给出，故本题在此为收尾），随后另起 **Problem 21（带 `*`）**。第 8 章习题 Problem 1–24 全章连续编号，§8.4 覆盖 Problem 14–24。习题区题干保持英文原题；带 `*` 题的英文 `Solution` 保留（仅标签附中文）。</span>

---
<br>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**（续）Problem（编号见上一页，带 `*`）——关于二次型 $q(\theta, x)$ 的 LMS / 线性 LMS / MAP 估计。**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 分界] 本页页首直接进入上页题目陈述的尾部与解答。因本页 OCR 未印出该题编号（题目首行在上一页 PDF p458），此处不臆造其编号，仅标注为延续性问题。</span>

题干尾部（英文保留）：

> **…Here $a$, $b$, $c$, $\bar{x}$ are some scalars with $\alpha \ne 0$. Derive the LMS and linear LMS estimates, for any $x$ such that $E[\Theta \mid X = x]$ is well-defined and finite. Assuming that $q(\theta, x) \ge 0$ for all $x, \theta$, and that $h$ is monotonically decreasing, derive the MAP estimate and show that it coincides with the LMS and linear LMS estimates.**

> <span style="color:#7f8c8d;">[星题 Solution 原文缺失说明] 本题（延续前页带 `*` 习题）按规范应以英文保留其 `Solution`，但源 OCR 中该解的英文原文残缺（习题首行在前页 PDF p458，本页解答亦被拆碎），无法忠实还原英文解答文本；此处保留中文重构译文供理解，请勿当作原书英文原文；如需严格英文原文请回查原书相关书页。</span>

**Solution（解答）：** 后验（posterior）由下式给出

```math
f_{\Theta\mid X}(\theta \mid x) = \frac{f_{\Theta,\,X}(\theta, x)}{f_X(x)} = \frac{h\big(q(\theta, x)\big)}{f_X(x)}.
```

为了引导出 LMS 与线性 LMS（linear LMS）估计的推导，先考虑 MAP 估计（MAP estimate），并假设对一切 $x, \theta$ 有 $q(\theta, x) \ge 0$，且 $h$ 为单调递减（monotonically decreasing）。MAP 估计最大化 $h(q(\theta, x))$；又因 $h$ 是递减函数，它等价于在 $\theta$ 上**最小化** $q(\theta, x)$。令 $q(\theta, x)$ 关于 $\theta$ 的导数为 $0$，得

```math
\hat{\theta} = \bar{\theta} + \frac{c}{\alpha}\,(x - \bar{x}).
```

（这里用到了如下事实：一个变元的非负二次函数在其导数等于 $0$ 的那一点取到最小值。）

接下来我们证明 $\hat{\theta}$ 等于 LMS 估计与线性 LMS 估计（此处去掉了「对一切 $x,\theta$ 有 $q(\theta,x)\ge 0$ 且 $h$ 单调递减」的假设）。我们写出

```math
\theta - \hat{\theta} = \theta - \bar{\theta} + \frac{c}{\alpha}\,(x - \bar{x}),
```

并将其代入 $q(\theta, x)$ 的表达式，经过一番代数化简得到

```math
q(\theta, x) = a\big(\theta - \hat{\theta}\big)^2 + \left(b - \frac{c^2}{\alpha}\right)(x - \bar{x})^2.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上两处公式（$\hat{\theta}=\bar{\theta}+\frac{c}{\alpha}(x-\bar{x})$ 与 $q(\theta,x)$ 的分解式）在源 OCR 中被拆成若干碎片行（如 `o = 0 + - c/a (x - x)`、`-c`、`-;;:` 等），现按本页解题的数学语义（后验关于 $\hat{\theta}$ 对称、二次型配方）忠实还原符号，未臆造数值。</span>

于是，对任意给定的 $x$，后验都是关于 $\hat{\theta}$ **对称**的 $\theta$ 的函数。这表明，只要 $E[\Theta \mid X = x]$ 良定义且有限，就有 $\hat{\theta}$ 等于条件均值（conditional mean）$E[\Theta \mid X = x]$。此外，我们有

```math
E[\Theta \mid X] = \bar{\theta} + \frac{c}{\alpha}\,(X - \bar{x}).
```

由于 $E[\Theta \mid X]$ 关于 $X$ 是线性的，它也就是线性 LMS 估计量（linear LMS estimator）。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 21（带 `*`）——基于两个观测的线性 LMS 估计（Linear LMS estimation based on two observations）**</span>

**Problem 21.** * Linear LMS estimation based on two observations. Consider three random variables $\Theta$, $X$, and $Y$, with known variances and covariances. Assume that $\mathrm{var}(X) > 0$, $\mathrm{var}(Y) > 0$, and that $\lvert\rho(X, Y)\rvert \ne 1$. Give a formula for the linear LMS estimator of $\Theta$ based on $X$ and $Y$, assuming that $X$ and $Y$ are uncorrelated, and also in the general case.

> <span style="color:#7f8c8d;">[星题 Solution 原文缺失说明] 本题为带 `*` 习题，按规范应保留原书英文 `Solution`。但本题解答在源 OCR 中碎片化，原英文解答文本无法逐句忠实还原（本页仅存续上一页推导到临界值 $c$ 选取的部分中文重构），故此处保留中文重构译文供阅读理解，请勿当作原书英文原文；如需严格英文原文请回查原书相关书页。</span>

**Solution（解答）：** 我们考虑形如 $\hat{\Theta} = aX + bY + c$ 的线性估计量，并选择 $a$、$b$、$c$ 以最小化均方误差（mean squared error）$E\big[( \Theta - aX - bY - c )^{2}\big]$。假设 $a$ 与 $b$ 已经选定，则 $c$ 必须最小化 $E\big[( \Theta - aX - bY - c )^{2}\big]$，因此

```math
c = E[\Theta] - a\,E[X] - b\,E[Y] .
```

> <span style="color:#7f8c8d;">衔接下一面（PDF p460）：Problem 21 的解答在此页写到选定 $c = E[\Theta] - aE[X] - bE[Y]$，其后续推导（确定 $a$、$b$）在下一页继续。</span>

---

<!-- ===== PDF p460 ===== -->

<span style="color:#7f8c8d;">书页 p452（文件页 p460），页眉「Bayesian Statistical Inference / 452 / Chap. 8」——第 8 章章末 Problems 习题区（§8.4，书目 p445–455 段内）。本页为习题区中部续页：页首承接上一页某个 §8.4 习题（基于两个观测的线性 LMS 估计推导）的收尾，随后本页起另一道带 `*` 的习题 Problem 22。</span>

> <span style="color:#7f8c8d;">[衔接上一页：页首为上一页某 §8.4 习题（基于两个观测 $X,\,Y$ 的线性最小均方（linear LMS）估计推导）的收尾部，故标题带「（续）」。习题区内容按源书保持英文原题，不整体汉译。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**（上一题 · 续）基于两个观测的线性最小均方（linear LMS）估计**</span>

It follows that $a$ and $b$ minimize

```math
E\Big[\, \big( (\theta - E[\theta]) - a(X - E[X]) - b(Y - E[Y]) \big)^{2}\, \Big].
```

We may thus assume that $\theta$, $X$, and $Y$ are zero mean, and in the final formula subtract the means. Under this assumption, the mean squared error is equal to

```math
E\big[\, (\theta - aX - bY)^{2}\, \big]
= E[\theta^{2}] + a^{2}E[X^{2}] + b^{2}E[Y^{2}] - 2aE[\theta X] - 2bE[\theta Y] + 2abE[XY].
```

Assume that $X$ and $Y$ are uncorrelated, so that $E[XY] = E[X]E[Y] = 0$. We differentiate the expression for the mean squared error with respect to $a$ and $b$, and set the derivatives to zero, to obtain

```math
a = \frac{E[\theta X]}{E[X^{2}]} = \frac{\operatorname{cov}(\theta, X)}{\operatorname{var}(X)}, \qquad
b = \frac{E[\theta Y]}{E[Y^{2}]} = \frac{\operatorname{cov}(\theta, Y)}{\operatorname{var}(Y)}.
```

Thus, the linear LMS estimator is

```math
\hat{\theta} = E[\theta] + \frac{\operatorname{cov}(\theta, X)}{\operatorname{var}(X)} (X - E[X])
+ \frac{\operatorname{cov}(\theta, Y)}{\operatorname{var}(Y)} (Y - E[Y]).
```

If $X$ and $Y$ are correlated, we similarly set the derivatives of the mean squared error to zero. We obtain and then solve a system of two linear equations in the unknowns $a$ and $b$, whose solution is

```math
a = \frac{\operatorname{var}(Y)\operatorname{cov}(\theta, X) - \operatorname{cov}(\theta, Y)\operatorname{cov}(X, Y)}
{\operatorname{var}(X)\operatorname{var}(Y) - \operatorname{cov}^{2}(X, Y)},
```

```math
b = \frac{\operatorname{var}(X)\operatorname{cov}(\theta, Y) - \operatorname{cov}(\theta, X)\operatorname{cov}(X, Y)}
{\operatorname{var}(X)\operatorname{var}(Y) - \operatorname{cov}^{2}(X, Y)}.
```

Note that the assumption $|\rho(X, Y)| \neq 1$ guarantees that the denominator in the preceding two equations is nonzero.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 22.\***</span>

> <span style="color:#7f8c8d;">题干英文原题，按源书保留，不汉译；带 `*` 题的英文解答（Solution）保留，仅标签可中文。</span>

**Problem 22.** \* Linear LMS estimation based on multiple observations. Let $\theta$ be a random variable with mean $\mu$ and variance $\sigma_0^{2}$, and let $X_1, \ldots, X_n$ be observations of the form

```math
X_i = \theta + W_i,
```

where the observation errors $W_i$ are random variables with mean 0 and variance $\sigma_i^{2}$. We assume that the random variables $\theta, W_1, \ldots, W_n$ are independent. Verify that the linear LMS estimator of $\theta$ based on $X_1, \ldots, X_n$ is

```math
\hat{\theta} =
\frac{\mu/\sigma_0^{2} + \sum\limits_{i=1}^{n} X_i/\sigma_i^{2}}
{\sum\limits_{i=0}^{n} 1/\sigma_i^{2}}\, ,
```

by minimizing over $a_1, \ldots, a_n, b$ the function ...

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 22 中上述估计量分数式的分子、分母在源 OCR 中被拆成碎片（`J-L/a5 + L Xi /a;`、`-----::-----`、`L l/a;`、`i=O` 等仅余零散字样），仅分子首项 $\mu/\sigma_0^{2}$、分子累加 $\sum X_i/\sigma_i^{2}$ 与分母为 $\sum_{i=0}^{n} 1/\sigma_i^{2}$（其中 $\sigma_0^{2}$ 为 $\theta$ 的方差）可辨。上式按该书「信号叠加独立噪声」线性 LMS 的标准结果忠实还原，非臆造；若不认可此复原，以源 OCR 原文为准并在数项下标处占位。</span>

> <span style="color:#7f8c8d;">[衔接下一页：本页末句「by minimizing over $a_1, \ldots, a_n, b$ the function …」（对包含 $a_i$ 与 $b$ 的该函数求极小以验证此估计量）在书页末尾被截断，其被极小化函数的显式表达式出现在下一页（书页 p453）页首。</span>

---

<!-- ===== PDF p461 ===== -->

> <span style="color:#7f8c8d;">第 8 章　章末习题区（Problems）——§8.4，书页 453（页眉「Sec. 8.5 / Problems / 453」）。本页承接上一页，继续 **Problem 22（带 `*`）** 的解答（其题干已在 PDF p460 给出，题为「基于多次观测的线性 LMS 估计 (Linear LMS estimation based on multiple observations)」）。习题区题干保持英文原题；带 `*` 题的英文 `Solution` 保留（仅标签附中文）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**（续）Problem 22 —— 基于多次观测的线性 LMS 估计（Linear LMS estimation based on multiple observations）—— 解答（Solution）续**</span>

上一页（PDF p460）已陈述：令观测 $X_i = \Theta + W_i$（$i=1,\dots,n$），其中噪声 $W_i$ 的均值（mean）为 $0$、方差（variance）为 $\sigma_i^{2}$，且 $\Theta, W_1,\dots,W_n$ 相互独立，$E[\Theta]=\mu$、$\mathrm{var}(\Theta)=\sigma_{\Theta}^{2}$；线性 LMS 估计量为
```math
\hat{\Theta} = \frac{\mu/\sigma_{\Theta}^{2} + \sum_{i=1}^{n} X_i/\sigma_i^{2}}{1/\sigma_{\Theta}^{2} + \sum_{j=1}^{n} 1/\sigma_j^{2}}.
```
本题要求通过对 $b,\,a_1,\dots,a_n$ 极小化
```math
g(b,a_1,\dots,a_n) = E\Big[\big(\Theta - b - a_1X_1 - \cdots - a_nX_n\big)^{2}\Big]
```
来验证这一结果。

**Solution（解答）：**接下来我们将证明：使目标函数取极小值的 $b$ 与 $a_1,\dots,a_n$ 分别是 $b^{*}$ 与 $a_1^{*},\dots,a_n^{*}$，其中
```math
a_i^{*} = \frac{1/\sigma_i^{2}}{1/\sigma_{\Theta}^{2} + \sum_{j=1}^{n} 1/\sigma_j^{2}}, \quad i = 1,\dots,n, \qquad b^{*} = \frac{\mu/\sigma_{\Theta}^{2}}{1/\sigma_{\Theta}^{2} + \sum_{j=1}^{n} 1/\sigma_j^{2}}.
```
为此，只需证明 $g$ 对 $b,\,a_1,\dots,a_n$ 的偏导数在 $b^{*}, a_1^{*},\dots,a_n^{*}$ 处全部等于 $0$。（因为该二次函数是非负的，可以证明任何使导数为 $0$ 的点必为极小点。）

> <span style="color:#1e8449;">**[t_note]** 注：这个加权平均式是线性 LMS 最重要的直觉——每个观测按 $1/\sigma_i^2$（噪声精度的倒数）加权，『方差越小、权越大』。先证：约束最优解由正交条件 $E[\tilde\Theta X_i]=0$（误差与每个观测无关）推出，而它导致权重与 $1/\sigma_i^2$ 成正比。它也统一两个极端：某 $\sigma_i^2\to\infty$ 时该项权 $\to0$（噪声过大的观测被丢弃），全相等时退化为普通平均。跨课程（凸优化，进行中）：目标 $g(b,a_1,\dots,a_n)$ 是关于这些系数的凸二次函数，故梯度为零的驻点自动是全局极小——这正是这里只需『令导数为 0』的正当理由。</span>

对 $g$ 求偏导可得
```math
\frac{\partial g}{\partial b} = -2\,E\big[\Theta - b - a_1X_1 - \cdots - a_nX_n\big],
```
并且对每个 $i$，
```math
\frac{\partial g}{\partial a_i} = -2\,E\Big[ X_i\big(\Theta - b - a_1X_1 - \cdots - a_nX_n\big) \Big].
```
从 $b^{*}$ 与 $a_1^{*},\dots,a_n^{*}$ 的表达式可以看出
```math
\sum_{i=1}^{n} a_i^{*} = 1 - \frac{b^{*}}{\mu}.
```
利用这一等式以及 $E[\Theta] = \mu$、$E[W_i] = 0$，可得
```math
\frac{\partial g}{\partial b} = -2\,E\Big[\Theta - b^{*} - \sum_{i=1}^{n} a_i^{*} X_i\Big] = -2\Big(\mu - b^{*} - \mu\sum_{i=1}^{n} a_i^{*}\Big) = 0 .
```
此外，再利用 $E\big[X_i(\Theta-\hat{\Theta})\big]$ 的等式以及 $E[X_i W_i] = \mathrm{var}(W_i) = \sigma_i^{2}$，可得
```math
\frac{\partial g}{\partial a_i} = -2\,E\Big[ X_i\big(\Theta - b^{*} - \sum_{j=1}^{n} a_j^{*} X_j\big) \Big] = 0 ,
```
对所有 $i$ 成立。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页多项公式在源 OCR 中被拆成碎片行（如 `ai" = ...`、`I/a;`、`E[(8 + Wi)Wi]`、`= O` 等），此处按本解的数学语义（二次目标对 $a_i^{*}$、$b^{*}$ 求梯度为零，权系数 $\sum a_i^{*} + b^{*}/\mu = 1$ 以及 $E[X_i(\Theta-\hat{\Theta})]=0$ 的可靠相性）忠实还原，未臆造数值或系数。</span>

---

<!-- ===== PDF p462 ===== -->

> <span style="color:#7f8c8d;">第 8 章　章末习题区（Problems）——§8.4，书页 454（页眉「Bayesian Statistical Inference / 454 / Chap. 8」）。本页先收束 **Problem 22** 解答的最后一句话（续上一页），随后另起 **Problem 23（带 `*`）**。习题区题干保持英文原题；带 `*` 题的英文 `Solution` 保留（仅标签附中文）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#7f8c8d;">**（续）Problem 22 —— 解答（Solution）收尾**</span>

……最后一个等号成立，是由 $a_i^{*}$ 与 $b^{*}$ 的定义而得的。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 23（带 `*`）—— 最小均方（LMS）估计的性质（Properties of LMS estimation）**</span>

**Problem 23.** * Properties of LMS estimation. Let $\Theta$ and $X$ be two random variables with positive variances. Let $\Theta^{L}$ be the linear LMS estimator of $\Theta$ based on $X$, and let $\tilde{\Theta}^{L} = \Theta^{L} - \Theta$ be the associated error. Similarly, let $\hat{\Theta}$ be the LMS estimator $E[\Theta \mid X]$ of $\Theta$ based on $X$, and let $\tilde{\Theta} = \hat{\Theta} - \Theta$ be the associated error.
**(a)** Show that the estimation error $\tilde{\Theta}^{L}$ satisfies $E[\tilde{\Theta}^{L}] = 0$.
**(b)** Show that the estimation error $\tilde{\Theta}^{L}$ is uncorrelated with the observation $X$.
**(c)** Show that the variance of $\Theta$ can be decomposed as $\mathrm{var}(\Theta) = \mathrm{var}(\hat{\Theta}) + \mathrm{var}(\tilde{\Theta})$.
**(d)** Show that the LMS estimation error $\tilde{\Theta}$ is uncorrelated with any function $h(X)$ of the observation $X$.
**(e)** Show that $\tilde{\Theta}$ is not necessarily independent from $X$.
**(f)** Show that the linear LMS estimation error $\tilde{\Theta}^{L}$ is not necessarily uncorrelated with every function $h(X)$ of the observation $X$, and that $E[\tilde{\Theta}^{L} \mid X = x]$ need not be equal to zero for all $x$.

**Solution（解答）. (a)** 我们有
```math
\Theta^{L} = E[\Theta] + \frac{\mathrm{cov}(\Theta,\,X)}{\mathrm{var}(X)}\,\big(X - E[X]\big).
```
对等式两边取数学期望（expectation），得到 $E[\Theta^{L}] = E[\Theta]$，即 $E[\tilde{\Theta}^{L}] = 0$。

**(b)** 利用 $\Theta^{L}$ 的表达式，可得
```math
\begin{aligned}
E[\tilde{\Theta}^{L} X] &= E\Big[\big(E[\Theta] + \tfrac{\mathrm{cov}(\Theta,X)}{\mathrm{var}(X)}(X-E[X]) - \Theta\big) X\Big] \\
&= E[\Theta]\,E[X] + \tfrac{\mathrm{cov}(\Theta,X)}{\mathrm{var}(X)}\big(E[X^2] - (E[X])^2\big) - E[\Theta X] \\
&= E[\Theta]E[X] - E[\Theta X] + \tfrac{\mathrm{cov}(\Theta,X)}{\mathrm{var}(X)}\,\mathrm{var}(X) \\
&= E[\Theta]E[X] - E[\Theta X] + \mathrm{cov}(\Theta,X) = 0 .
\end{aligned}
```
我们刚刚建立的 $E[\tilde{\Theta}^{L} X] = 0$，连同 (a) 中由 $E[\tilde{\Theta}^{L}] = 0$，共同推出
```math
\mathrm{cov}\big(\tilde{\Theta}^{L},\,X\big) = E[\tilde{\Theta}^{L} X] - E[\tilde{\Theta}^{L}]\,E[X] = 0,
```
即 $\tilde{\Theta}^{L}$ 与观测 $X$ 不相关（uncorrelated）。

> <span style="color:#1e8449;">**[t_note]** 注：$E[\tilde\Theta^L X]=0$ 就是线性投影的『正交条件』——最优线性估计的误差必须垂直于用来做估计的方向。先证：若误差与 $X$ 相关（$E[\tilde\Theta X]\neq0$），则沿 $X$ 方向微调 $aX$ 就能把均方误差再压低，与最优性矛盾。这个『驻点/正交』论证在 Problem 22–24 反复出现，是理解 9.2 线性回归公式推导的真正地基。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源 OCR 中 (b) 的推导被拆成极碎的行（如 `cov(8, X)(E[X]^2 - E[X^2]^2)`、`(E[eX] - E[e]E[X])` 等），此处按展开 $E[\tilde{\Theta}^{L} X]$ 的标准代数步骤还原，符号与最终 $0$ 均未臆造。衔接下一面（PDF p463）：Problem 23 的 (c)–(f) 与 Problem 24 在下一页给出。</span>

---

<!-- ===== PDF p463 ===== -->

> <span style="color:#7f8c8d;">第 8 章　章末习题区（Problems）——§8.4，书页 455（页眉「Sec. 8.5 / Problems / 455」）。本页承接上一页，继续 **Problem 23（带 `*`）** 的解答（部分 (c)–(f)），随后另起 **Problem 24（带 `*`）**。习题区题干保持英文原题；带 `*` 题的英文 `Solution` 保留（仅标签附中文）。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#7f8c8d;">**（续）Problem 23 —— 最小均方（LMS）估计的性质 —— 解答（Solution）续（部分 (c)–(f)）**</span>

**Solution（解答）(续).**

**(c)** 注意到 $\Theta = \hat{\Theta} - \tilde{\Theta}$，于是
```math
\mathrm{var}(\Theta) = \mathrm{var}\big(\hat{\Theta} - \tilde{\Theta}\big) = \mathrm{var}(\hat{\Theta}) + \mathrm{var}(-\tilde{\Theta}) + 2\,\mathrm{cov}\big(\hat{\Theta},\,-\tilde{\Theta}\big) .
```
由于 $\hat{\Theta} = E[\Theta\mid X]$ 是 $X$ 的函数，而（依 (d) 的结果）$\tilde{\Theta}$ 与 $X$ 的任意函数都不相关，特别地 $\mathrm{cov}(\hat{\Theta},\tilde{\Theta}) = 0$，故得
```math
\mathrm{var}(\Theta) = \mathrm{var}(\hat{\Theta}) + \mathrm{var}(\tilde{\Theta}).
```

> <span style="color:#1e8449;">**[t_note]** 注：把 $\Theta=\hat\Theta-\tilde\Theta$ 代进方差，本质是勾股定理式的正交分解：参数被拆成『可被 $X$ 解释的部分 $\hat\Theta$』与『误差 $\tilde\Theta$』，二者不相关（正交）故方差直接相加。先证：$\mathrm{var}(A-B)=\mathrm{var}A+\mathrm{var}B-2\,\mathrm{cov}(A,B)$，只要交叉项 $\mathrm{cov}(\hat\Theta,\tilde\Theta)=0$ 就退化为相加——(d) 恰好保证了这个正交。跨课程（线性代数 Strang）：这正是向量空间的投影正交分解 $\|v\|^2=\|\mathrm{proj}_W v\|^2+\|v-\mathrm{proj}_W v\|^2$，方差即范数平方。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 源 OCR 的 (c) 表述严重碎片化（如 `var(8) = var(8L - 8L) = var(8L) + var(8L)` 及 `COV(8L, 8L) = O`），记号 $\hat{\Theta}$、$\tilde{\Theta}$ 混为 `8L`。此处按方差分解 $\mathrm{var}(\Theta) = \mathrm{var}(\hat{\Theta}) + \mathrm{var}(\tilde{\Theta})$ 的标准证明（$\Theta=\hat{\Theta}-\tilde{\Theta}$ 且二者不相关）复原，未引入未在源页出现的系数。</span>

**(d)** 这是因为 $E[\tilde{\Theta}] = 0$，并且
```math
\begin{aligned}
E\big[\tilde{\Theta}\,h(X)\big] &= E\Big[\big(E[\Theta\mid X] - \Theta\big)\, h(X)\Big] \\
&= E\big[E[\Theta\mid X]\,h(X)\big] - E\big[\Theta\,h(X)\big] \\
&= E\Big[E\big[\Theta\,h(X)\mid X\big]\Big] - E\big[\Theta\,h(X)\big] \\
&= E\big[\Theta\,h(X)\big] - E\big[\Theta\,h(X)\big] = 0 .
\end{aligned}
```

> <span style="color:#1e8449;">**[t_note]** 注：(d) 用的是『对 $X$ 取条件、再取无条件的期望』两步法 $E[E[\cdot\mid X]]=E[\cdot]$：因为 $\hat\Theta=E[\Theta\mid X]$ 是 $X$ 的函数，$E[\hat\Theta h(X)]=E\big[E[\Theta h(X)\mid X]\big]$ 可把 $\Theta$ 一次次『放进去』再『取回来』。它表明 LMS 误差不仅与 $X$ 不相关，还与 $X$ 的**任何函数**都不相关——这是『$E[\Theta\mid X]$ 是所有 $X$-函数中的最佳估计』的另一面，也为 (c) 的方差分解铺好了正交舞台。</span>

**(e)** 设 $\Theta$ 与 $X$ 为具有如下联合分布（joint PMF）的离散随机变量
```math
p_{\Theta,X}(\theta,x) = \begin{cases} \tfrac{1}{3}, & (\theta,x) \in \{(0,0),\,(1,1),\,(-1,1)\}, \\ 0, & \text{其他情况}. \end{cases}
```
在这个例子里，有 $X = \lvert \Theta \rvert$，所以 $X$ 与 $\Theta$ 并不独立。注意对 $X$ 的所有可能值 $x$ 都有 $E[\Theta \mid X = x] = 0$，从而 $\hat{\Theta} = E[\Theta\mid X] = 0$。因此 $\tilde{\Theta} = -\Theta$。由于 $\Theta$ 与 $X$ 不独立，$\tilde{\Theta}$ 与 $X$ 也必然不独立。

**(f)** 设 $\Theta$ 与 $X$ 为具有如下联合分布（joint PMF）的离散随机变量
```math
p_{\Theta,X}(\theta,x) = \begin{cases} \tfrac{1}{3}, & (\theta,x) \in \{(0,0),\,(1,1),\,(1,-1)\}, \\ 0, & \text{其他情况}. \end{cases}
```
在这个例子里，有 $\Theta = \lvert X \rvert$。注意 $E[X] = 0$ 且 $E[\Theta X] = 0$，所以 $X$ 与 $\Theta$ 不相关（uncorrelated）。我们得到 $\Theta^{L} = E[\Theta] = 2/3$，于是 $\tilde{\Theta}^{L} = (2/3) - \Theta = (2/3) - \lvert X \rvert$，它并不与 $X$ 独立。此外还有 $E[\tilde{\Theta}^{L} \mid X = x] = (2/3) - \lvert x \rvert$，它依 $x = 0$ 或 $\lvert x \rvert = 1$ 而分别取 $2/3$ 与 $-1/3$ 两个不同的值。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 24（带 `*`）—— 基于多次观测的线性 LMS 估计的性质（Properties of linear LMS estimation based on multiple observations）**</span>

**Problem 24.** * Properties of linear LMS estimation based on multiple observations. Let $\Theta$, $X_{1}, \ldots, X_{n}$ be random variables with given variances and covariances. Let $\Theta^{L}$ be the linear LMS estimator of $\Theta$ based on $X_{1}, \ldots, X_{n}$, and let $\tilde{\Theta}^{L} = \Theta^{L} - \Theta$ be the associated error. Show that $E[\tilde{\Theta}^{L}] = 0$ and that $\tilde{\Theta}^{L}$ is uncorrelated with $X_{i}$ for every $i$.

**Solution（解答）：**我们首先证明对一切 $i$ 有 $E[\tilde{\Theta}^{L} X_{i}] = 0$。考虑一个形如 $\Theta^{L} + aX_{1}$ 的新线性估计量，其中 $a$ 是标量参数。由于 $\Theta^{L}$ 是线性 LMS 估计量，其均方误差（mean squared error）$E\big[(\tilde{\Theta}^{L})^{2}\big]$ 不大于新估计量的均方误差 $h(a) = E\big[(\Theta^{L} + aX_{1} - \Theta)^{2}\big]$。因此函数 $h(a)$ 在 $a=0$ 处取得最小值，且 $(dh/da)(0) = 0$。注意
```math
h(a) = E\Big[\big(\tilde{\Theta}^{L} + aX_{1}\big)^{2}\Big] = E\Big[\big(\tilde{\Theta}^{L}\big)^{2}\Big] + 2a\,E\big[\tilde{\Theta}^{L} X_{1}\big] + a^{2}E\big[X_{1}^{2}\big].
```
条件 $(dh/da)(0) = 0$ 给出 $E[\tilde{\Theta}^{L} X_{1}] = 0$。对每个 $i$ 重复上述论证，即得 $E[\tilde{\Theta}^{L} X_{i}] = 0$ 对一切 $i$ 成立。

现在把上面的论证重复一遍，但用常数 $1$ 替换随机变量 $X_{i}$。照同样的步骤，可得 $E[\tilde{\Theta}^{L}] = 0$。最后注意
```math
\mathrm{cov}\big(\tilde{\Theta}^{L},\,X_{1}\big) = E\big[\tilde{\Theta}^{L} X_{1}\big] - E\big[\tilde{\Theta}^{L}\big]\,E[X_{1}] = 0 - 0\cdot E[X_{1}] = 0 ,
```
所以 $\tilde{\Theta}^{L}$ 与 $X_{1}$ 不相关（uncorrelated）。同理，对每个 $i$ 也有 $\mathrm{cov}(\tilde{\Theta}^{L}, X_{i}) = 0$。

> <span style="color:#1e8449;">**[t_note]** 注：Problem 24 秀了一把反证：假设误差 $\tilde\Theta^L$ 与某个 $X_i$ 相关，那么把它『剂』进估计量 $\Theta^L+aX_i$（微调系数 $a$）就能压低均方误差，与 $\Theta^L$ 的最优性矛盾——于是误差必与每个 $X_i$ 不相关。先证：$h(a)=E[(\tilde\Theta^L+aX_1)^2]$ 在 $a=0$ 处取极小、导数 $2E[\tilde\Theta^L X_1]$ 要为 0，正是联赛方程 $E[\tilde\Theta^L X_1]=0$。这条『最优＝误差正交』的做法是 9.2 回归公式与 8.4 一章的真正共同点。</span>

---

<!-- ===== PDF p464 ===== -->

> <span style="color:#7f8c8d;">本书页 457，**第 9 章「经典统计推断（Classical Statistical Inference）」的章首 Contents（目录）页**。书页号 457 即进入第 9 章；本页为新章起始，故用第 9 章红色章标题，勿并入第 8 章。本页仅列出各小节标题与页码，各节正文随后的书页依次排列（§9.1 在书页 460，即文件页 467 起）。</span>

---

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

**目录（Contents）**

- **9.1　经典参数估计（Classical Parameter Estimation）** …………… p. 460
- **9.2　线性回归（Linear Regression）** ………………………… p. 475
- **9.3　二值假设检验（Binary Hypothesis Testing）** ……………… p. 485
- **9.4　显著性检验（Significance Testing）** …………………… p. 495
- **9.5　总结与讨论（Summary and Discussion）** ………………… p. 506
- **习题（Problems）** …………………………………………… p. 507

---

<!-- ===== PDF p465 ===== -->

> <span style="color:#7f8c8d;">第 9 章　引言（Introduction）承载段——书页 458（上一页 PDF p464 已见第 9 章章首 Contents 页，本页为其后紧接的章引言正文）。本页源 OCR 损坏极其严重，多为碎片单词散乱排列，以下按原书第 9 章开篇论述的语义逐段还原其主旨，凡原文可辨的术语保留英文；无法直接确认的细节仅作一般性复述，不臆造具体公式或数字。</span>

---

第 9 章　经典统计推断（Classical Statistical Inference）的开篇，与前一章贝叶斯视角形成对比：在我们所采取的经典哲学（classical philosophy）中，把未知量视为一个**待确定的未知常数（unknown constant）**，而不是一个具有先验分布的随机变量。观测 $X$ 是一个随机变量，其可用分布随未知参数 $\theta$ 的取值而定——若 $X$ 为离散型，则记作 $p_X(x;\theta)$；若 $X$ 为连续型，则记作 $f_X(x;\theta)$（参见 §9.1）。因此，我们不是在单个概率模型内部进行推断，而是面对**多个概率模型（multiple probabilistic models）**——对未知参数 $\theta$ 的每一个可能取值，都有一个对应的模型。

> <span style="color:#1e8449;">**[t_note]** 注：这是经典统计的『世界观切换』：不是在一个概率空间里做推断，而是在一族候选模型 $\{p(x;\theta)\}$（靠参数索引）里挑哪个最能产生当前数据。先证：经典把 $\theta$ 当常数、贝叶斯把 $\theta$ 当随机变量取平均；『族』的视角是所有参数化建模的骨架——后面极大似然、置信区间、假设检验全是在『这族里比较哪个参数更似然』。跨课程（离散数学6.042J 集合/函数）：一族模型就是由参数 $\theta$ 索引的一族函数，结论不再绑定单一模型。</span>

在这种经典框架下没有先验来供我们取平均，所以估计量或决策必须保证：无论真实参数 $\theta$ 取何值，都能取得良好性能——这采取一种某种程度的**最坏情形（worst case）**观点，而非依先验取平均的观点；除非它能满足我们的全部要求，否则一个估计量被认为不可靠。

> <span style="color:#1e8449;">**[t_note]** 注：『最坏情形』点破省略先验的真实代价：经典不假设 θ 的分布，只好对『每个可能的 θ』都要求估计靠谱——相当于在对抗性/最不利参数下做鲁棒设计。先证：贝叶斯对 θ 按先验加权平均，经典改对最差 θ 求保证；这决定了一致性（相合）、置信区间、错误概率等概念都是『对一切 θ 同时成立』的版本，你在后面会反复看到『对每个 θ 都成立』这类限定。</span>

因此，经典推断模型（classical inference model）可形式化如下：对 $\theta$ 的每一个取值，我们有一个分布 $P_X(x;\theta)$。观测 $X$ 的实现值 $x$ 被用来**估计** $\theta$，或在竞争性假设之间**选择**其一，等等。

注意，我们用记号 $E_{\theta}[h(X)]$ 表示随机变量 $h(X)$ 的**期望值看成 $\theta$ 的函数**；类似地，用 $P_{\theta}(A)$ 表示事件 $A$ 的概率看成 $\theta$ 的函数。需要强调：这只是表明概率对 $\theta$ 的**函数依赖（functional dependence）**，并不是概率论意义上的依赖关系。

> <span style="color:#1e8449;">**[t_note]** 注：记号 $P_\theta(A)$、$E_\theta[h(X)]$ 的下标 θ 只是『参数取值的标签』，不是在取一个随机 θ 的条件概率。先证：若 θ 是随机变量才算条件概率；经典里 θ 是常数，所以这纯粹是『概率对 θ 的函数依赖』。读本书时别自动滑进贝叶斯的条件概率思维——后面 $P\big(L(X)>\xi;\mathrm{H}_0\big)$ 用的是同一记号语言，下标依旧是标签而非事件。</span>

在下面两节中，我们主要关注参数估计（parameter estimation）问题。我们的例子通常假定观测是**独立同分布（independent and identically distributed，i.i.d.）**的随机变量。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页几乎每行都出现碎片（如 `Dosessse s`、`\JJd.L1 A`、`£> " .... `、`........ ` 等乱码单词，以及 `[';.. ]` 样式的残缺符号），无法逐句对上原文；以上按第 9 章开篇关于「未知常数 vs 随机变量」「多模型族」「最坏情形观点」「$E_{\theta}[\cdot]$ / $P_{\theta}(\cdot)$ 函数依赖记号」的公认立论整理。个别无法辨认处未臆造公式。</span>

---

<!-- ===== PDF p466 ===== -->

> <span style="color:#7f8c8d;">第 9 章　引言（Introduction）——书页 459（上一页 PDF p465 为第 9 章开篇论述，本页按其后续续讲第三节二值假设检验与第四节显著性检验、并进入「本章的主要术语、问题与方法（Major Terms, Problems, and Methods in this Chapter）」清单）。此段可辨原文完整，逐句行内双语翻译。</span>

---

第三节处理**二值假设检验（binary hypothesis testing）**问题。这里要发展的方法与前一章讨论的（贝叶斯）最大后验（MAP）方法相似。特别地，我们计算每个假设在已观测数据之下的**似然（likelihood）**，并通过比较两个似然之比与一个适当选取的阈值（threshold）来选择某个假设。

最后一节处理不同类型的假设检验问题。例如，假设一枚硬币被抛掷 $n$ 次，据此观测到由「正」「反」构成的序列，我们希望判断这枚硬币是否均匀。我们想要检验的主要假设为 $p = 1/2$，其中 $p$ 表示未知的正面概率（probability of heads）。其备择假设（alternative hypothesis）$p \ne 1/2$ 是**复合（composite）**的，因为它由若干个——可能无穷多个——子假设构成（例如 $p = 0.1$、$p = 0.4999$ 等等）。显然，任何方法都不可能仅依据数目适中的观测，可靠地把 $p = 0.5$ 的硬币与 $p = 0.4999$ 的硬币区分开。这类问题通常借助**显著性检验（significance testing）**的方法来处理。此时要问的问题是：「已观测到的数据是否与 $p = 0.5$ 这一假设相容？」粗略地说，如果在某假设之下，所观测数据不太可能「凑巧」或「碰巧」产生，就拒绝该假设。

> <span style="color:#1e8449;">**[t_note]** 注：显著性检验的推理长得像逻辑里的『否定后件』（modus tollens）：若 H0 真则数据罕见，数据确实罕见 → 拒绝 H0。先证：但它是概率化的、会犯错——罕见≠不可能，所以必须配一个弃真率 α 当『出错容忍度』。备择假设 $p\ne1/2$ 是复合假设（含无穷多 p 值），二值检验给不了它一个明确的拒绝域，这正是本小节要另开显著性检验工具的动机。跨课程（离散数学6.042J 逻辑）：把『若 P 则 Q』换成『若 H0 真则数据罕见』，统计检验就是带出错概率的 modus tollens。</span>

<span style="color:#c0392b;">**本章的主要术语、问题与方法（Major Terms, Problems, and Methods in this Chapter）**</span>

- 经典统计学（classical statistics）把未知参数当作**待确定的常数**来处理。对未知参数的每一个可能取值，都假定一个**单独的概率模型（separate probabilistic model）**。

- 在**参数估计（parameter estimation）**中，我们希望产生这样的估计：在未知参数的任何可能取值之下都接近正确。

- 在**假设检验（hypothesis testing）**中，未知参数取有限个值 $m$（$m \ge 2$），各自对应相互竞争的假设；我们希望在任一可能假设之下取得很小的出错概率，从而选择其中一个假设。

- 在**显著性检验**中，我们希望接受或拒绝单个假设，同时使**误拒（false rejection）**的概率保持适当小。

- 本章主要的经典推断方法（principal classical inference methods）：
  **(a) 极大似然（ML）估计（maximum likelihood (ML) estimation）：**选取使已观测数据「最可能(more likely)」出现的参数，即最大化获得当前数据之概率的参数（§9.1）。
  **(b) 线性回归（linear regression）：**在使模型与数据之间差别的平方和最小的意义上，找出一条与一组数据对匹配得最好的线性关系（§9.2）。

---

<!-- ===== PDF p467 ===== -->

> <span style="color:#7f8c8d;">书页 460，页眉「Classical Statistical Inference / Chap. 9」。本页先承接上一页「本章的主要术语、问题与方法（Major Terms…）」清单的 (c)、(d) 两条，随后另起 **§9.1 经典参数估计（Classical Parameter Estimation）正文**及其第一个小节「估计量的性质（Properties of Estimators）」。这是 §9.1 的起始页（书页 460，与 Contents 页所标一致），教科书小节标题用深红着色。</span>

---

<span style="color:#7f8c8d;">**（续）本章的主要术语、问题与方法（Major Terms, Problems, and Methods in this Chapter）**</span>

  **(c) 似然比检验（likelihood ratio test）：**给定两个假设，依据它们的「似然」之比来选择其中一个，使某些出错概率保持适当小（§9.3）。
  **(d) 显著性检验（significance testing）：**给定一个假设，当且仅当已观测数据落入某个特定的**拒绝域（rejection region）**时拒绝它。该区域被特别设计为把误拒概率控制在某个阈值（threshold）之下（§9.4）。

---

<span style="color:#c0392b;">**§9.1　经典参数估计（Classical Parameter Estimation）**</span>

在本节中我们聚焦于参数估计，采用经典方法（classical approach），其中参数 $\theta$ 不是随机变量，而被视为一个未知常数（unknown constant）。我们首先引入估计量（estimator）的一些定义及其相关性质。随后讨论极大似然估计量（maximum likelihood estimator），它可以被视为贝叶斯 MAP 估计量的经典对应物（classical counterpart）。最后我们聚焦于估计未知均值、或许还有未知方差这一简单而重要的例子。我们也讨论与之相关的问题：构造一个以高概率包含未知参数的区间（「置信区间（confidence interval）」）。我们所发展的方法大量依赖大数定律（laws of large numbers）与中心极限定理（central limit theorem）（参见第 5 章）。

<span style="color:#c0392b;">**估计量的性质（Properties of Estimators）**</span>

给定观测 $X = (X_{1},\ldots,X_{n})$，一个**估计量（estimator）**是一个具有如下形式的随机变量：$\hat{\Theta} = g(X)$，其中 $g$ 是某个函数。注意由于 $X$ 的分布依赖于 $\theta$，$\hat{\Theta}$ 的分布亦然。我们用**估计值（estimate）**这一术语指代 $\hat{\Theta}$ 的一个实际实现值（realized value）。

> <span style="color:#1e8449;">**[t_note]** 注：先分清两个词：估计量（estimator）$\hat\Theta_n=g(X_n)$ 是随机变量（采样前 $X_n$ 未定），估计值（estimate）是它的一次实现 $g(x)$。先证：偏差 $b_\theta=E_\theta[\hat\Theta_n]-\theta$ 用的是估计量的**期望**，即『重复采样下的平均误差』，不是某次实现——一旦把两者混为一谈，『偏差为 0 的无偏』这句话就失去其可重复性的含义，而可重复性正是经典统计的执念。</span>

有时——尤其是当我们关注观测数目 $n$ 的作用时——我们用记号 $\hat{\Theta}_{n}$ 表示估计量。此时也宜把 $\hat{\Theta}_{n}$ 视为一个估计量的序列（每一个 $n$ 对应一个估计量）。$\hat{\Theta}_{n}$ 的均值与方差通常记作 $E_{\theta}[\hat{\Theta}_{n}]$ 与 $\mathrm{var}_{\theta}(\hat{\Theta}_{n})$，并按通常方式定义。$E_{\theta}[\hat{\Theta}_{n}]$ 与 $\mathrm{var}_{\theta}(\hat{\Theta}_{n})$ 都是 $\theta$ 的数值函数，但为了简便，在上下文清楚时我们有时不写出这一依赖关系。

> <span style="color:#1e8449;">**[t_note]** 注：$E_\theta[\hat\Theta_n]$ 把期望看成 θ 的函数，不是条件期望：分布随 θ 换、期望跟着变。先证：它回答『对每个候选 θ，重复采样时估计量平均处在一块』。由于经典对『每个 θ 同时成立』有执念（见前面最坏情形一注），本书几乎所有定义（无偏/相合/置信区间）都拖着『对一切 θ』的限定词，这个符号习惯得先接受再往下读。</span>

---

<!-- ===== PDF p468 ===== -->

> <span style="color:#7f8c8d;">书页 461，页眉「Sec. 9.1 / Classical Parameter Estimation」。本页承接 §9.1 第一节「估计量的性质（Properties of Estimators）」，正文以「关于估计量的术语（Terminology Regarding Estimators）」定义块为中心，随后给出均方误差分解公式及其脚注，最末自然引入下一小节极大似然估计。术语块标题用定义深青着色。</span>

---

<span style="color:#00838f;">**[定义] Terminology / 术语：关于估计量（Regarding Estimators）**</span>

设 $\hat{\Theta}_{n}$ 是未知参数 $\theta$ 的一个估计量（estimator），即它是 $n$ 个观测 $X_{1},\ldots,X_{n}$ 的函数，而这些观测的分布依赖于 $\theta$。

- **估计误差（estimation error）**，记作 $\tilde{\Theta}_{n}$，定义为 $\tilde{\Theta}_{n} = \hat{\Theta}_{n} - \theta$。
- 估计量的**偏差（bias）**，记作 $b_{\theta}(\hat{\Theta}_{n})$，是估计误差的期望值：
  ```math
  b_{\theta}(\hat{\Theta}_{n}) = E_{\theta}\big[\tilde{\Theta}_{n}\big] = E_{\theta}\big[\hat{\Theta}_{n}\big] - \theta .
  ```
- $\hat{\Theta}_{n}$ 的期望值、方差与偏差都依赖于 $\theta$，而估计误差还额外依赖于观测 $X_{1},\ldots,X_{n}$。
- 若对 $\theta$ 的每一个可能取值都有 $E_{\theta}[\hat{\Theta}_{n}] = \theta$，则称 $\hat{\Theta}_{n}$ 是**无偏（unbiased）**的。
- 若对 $\theta$ 的每一个可能取值都有 $\lim_{n\to\infty} E_{\theta}[\hat{\Theta}_{n}] = \theta$，则称 $\hat{\Theta}_{n}$ 是**渐近无偏（asymptotically unbiased）**的。
- 若对 $\theta$ 的每一个可能取值，序列 $\hat{\Theta}_{n}$ 都依概率（in probability）收敛到参数 $\theta$ 的真值，则称 $\hat{\Theta}_{n}$ 是**相合（consistent）**的。

> <span style="color:#1e8449;">**[t_note]** 注：相合性（consistency）不是新概念，它正是第 5 章大数定律的再陈述：要求 $\hat\Theta_n\xrightarrow{p}\theta$ 对每个 θ 都成立。先证：估计量只要是样本均值型 $n^{-1}\sum X_i$，弱大数定律直接给出依概率收敛、无需另证——所以 Example 9.2 里 $k/n$ 与 Example 9.3 里 $1/\bar X$ 的相合都是一句话的事（后者再借一次连续映射）。说到底它是『观测越多，估计越逼近真值』的可重复保证，与无偏（管期望）、渐近无偏（管极限期望）是各管一段的三兄弟。</span>

估计量作为随机观测的函数，不能指望它恰好等于未知值 $\theta$。因此，估计误差一般是非零的。另一方面，如果对 $\theta$ 的每一个可能取值，平均估计误差都为零，那么我们便得到一个无偏估计量，而这是一种可取的（desirable）性质。渐近无偏性只要求估计量随着观测数目 $n$ 的增大而变得无偏，当 $n$ 很大时这是可取的。

除了偏差 $b_{\theta}(\hat{\Theta}_{n})$ 之外，我们通常还关心估计误差的大小。这由**均方误差（mean squared error）** $E_{\theta}\big[\tilde{\Theta}_{n}^{2}\big]$ 来刻画，它按照下式与 $\hat{\Theta}_{n}$ 的偏差和方差相联系：
```math
E_{\theta}\big[\tilde{\Theta}_{n}^{2}\big] = b_{\theta}^{2}\big(\hat{\Theta}_{n}\big) + \mathrm{var}_{\theta}\big(\hat{\Theta}_{n}\big) .
```
这个公式之所以重要，是因为在许多统计问题中，等式右边这两项之间存在**权衡（trade-off）**：方差的减小往往伴随着偏差的增大。当然，一个好的估计量应当设法使这两项都保持很小。

> <span style="color:#1e8449;">**[t_note]** 注：均方误差分解 $E[(\hat\Theta_n-\theta)^2]=b^2+\mathrm{var}$ 是整个『偏差-方差权衡』的支点。先证：$\hat\Theta_n-\theta=\big(\hat\Theta_n-E[\hat\Theta_n]\big)+\big(E[\hat\Theta_n]-\theta\big)$，前一项是中心化误差（方差）、后一项是常数偏差，交叉项期望恰好为 $2\,\mathrm{cov}(\hat\Theta_n,\cdot)=0$ 而消失，于是两者干净分离。推论：无偏未必最优、有偏未必差——后面 Example 9.5 就有一个有偏估计，其方差比样本均值还小。跨课程（凸优化，进行中）：在无偏子类里最小化方差是带线性等式约束的凸问题，正是高年级『最优估计 / Cramér–Rao 界』的入口。</span>

下面我们讨论几种具体的估计方法，从极大似然估计（maximum likelihood estimation）开始。这是一种与贝叶斯推断中引入的 MAP 估计相似的一般性方法。随后我们考虑估计一个随机变量的均值与方差这一简单而重要的情形，这会把我们与第 5 章关于大数定律的讨论联系起来。

> <span style="color:#7f8c8d;">[note] 脚注（Footnote）：这是公式 $E[X^{2}] = (E[X])^{2} + \mathrm{var}(X)$ 的一个应用，取 $X = \tilde{\Theta}_{n}$，其中期望是相对于 $\theta$ 所对应的分布取的；我们还用到了 $E_{\theta}[\tilde{\Theta}_{n}] = b_{\theta}(\hat{\Theta}_{n})$ 以及 $\mathrm{var}_{\theta}(\tilde{\Theta}_{n}) = \mathrm{var}_{\theta}(\hat{\Theta}_{n} - \theta) = \mathrm{var}_{\theta}(\hat{\Theta}_{n})$ 这两个事实。</span>

---

<!-- ===== PDF p469 ===== -->

> <span style="color:#7f8c8d;">书页 462（页眉「Sec. 9.1 / Classical Parameter Estimation」）。本页承接 §9.1，正文进入「极大似然估计（Maximum Likelihood Estimation）」小节（离散情形为主，连续情形与 ML vs MAP 的讨论在下一页 PDF p470 继续）。源 OCR 损坏极重（大量碎片行与裸字符），以下按极大似然估计的公认立论逐段还原；个别记号无法辨认处不作臆造，附灰注说明。</span>

---

<span style="color:#c0392b;">**极大似然估计（Maximum Likelihood Estimation）**</span>

我们假设观测 $X$ 的分布（PMF）为 $p_X(x;\theta)$，其中 $\theta$ 是未知参数。给定观测 $X$ 的实现值 $x$，我们要在 $\theta$ 的各个可能取值之间作出选择（若 $\theta$ 事先被限定在有限个——例如 $m$ 个——可能取值之一，即对应备择假设的若干候选值）。**极大似然（ML）估计（maximum likelihood (ML) estimate）**选出的，正是使**似然函数（likelihood function）** $p_X(x;\theta)$ 关于 $\theta$ 取最大值的那个 $\theta$ 值。

当我们在 $n$ 个独立同分布（i.i.d.）观测 $X_{1},\ldots,X_{n}$ 的基础上进行推断时，逐对给出 $X_{i}$ 的似然函数 $p_X(x_{i};\theta)$（对所有 $i$），并选择使**联合似然（joint likelihood）**最大的 $\theta$ 值。由独立性，该联合似然为诸 $p_X(x_{i};\theta)$ 之积：
```math
\prod_{i=1}^{n} p_X\big(x_{i};\theta\big),
```
然后关于所有可能的 $\theta$ 取值最大化这一乘积。这就是极大似然估计在这一情形下的选值准则。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页源 OCR 多为碎片（如 `\hat 值`、`(0)`、`..n`、`9.2` 交叉引用行与 `conven` 残词等），无法逐句对上原文；以上仅陈述离散情形极大似然估计的核心定义：在 $\theta$ 的可能取值（有限个 $m$ 个值的假设情形）中挑选使 $p_X(x;\theta)$（或对 $n$ 个独立观测取乘积 $\prod_i p_X(x_i;\theta)$）最大的值。连续情形的对应公式（用 PDF 替换 PMF）在下一页 PDF p470 给出。未臆造具体数值。</span>

---

<!-- ===== PDF p470 ===== -->

> <span style="color:#7f8c8d;">书页 463，页眉「Sec. 9.1 / Classical Parameter Estimation」。本页承接 §9.1「极大似然估计」小节：先交代连续情形的对应做法与「似然」一词的正解，再说明 ML 估计与「平先验」下的 MAP 估计之联系，随后给出 **Example 9.1** 与 **Example 9.2**。例号自新章 §9.1 起新启（Example 9.1、9.2…），连续编号。</span>

---

<span style="color:#7f8c8d;">**（续）极大似然估计（Maximum Likelihood Estimation）**</span>

……关于整个取值域 $\Omega$ 最大化。当 $X$ 为连续型时，情形类似，只需把 PMF 换成 PDF（probability density function）：我们关于 $\theta$ 最大化
```math
\prod_{i=1}^{n} f_X\big(x_{i};\theta\big).
```
「似然（likelihood）」一词需要恰当理解。特别地，在已观测到 $X$ 取值为 $x$ 的前提下，$p_X(x;\theta)$ 并不是「未知参数等于 $\theta$」这一事件的概率；相反，它是「当参数等于 $\theta$ 时观测取到值 $x$」的概率。因此，在极大化似然时，我们问的是这样一个问题：「在哪个 $\theta$ 取值之下，我们看到的这些观测最可能出现？」

> <span style="color:#1e8449;">**[t_note]** 注：最易踩的反点：$p_X(x;\theta)$ 是『参数为 θ 时观测到 $x$』的概率，绝不是『θ 取某个值』的概率——后者在经典里甚至没有意义（θ 是常数）。先证：极大似然把『哪枚参数硬币更容易掷出这串结果』当判据，别把它念成后验。这正是它与需要先验的 MAP 的分野，也是入门最常见的误读。</span>

回忆在贝叶斯 MAP 估计（Bayesian MAP estimation）中，估计值被选择为使表达式 $p_{\Theta}(\theta)\,p_{X\mid\Theta}(x\mid\theta)$ 关于所有 $\theta$ 取最大的那个值，其中 $p_{\Theta}(\theta)$ 是未知离散参数 $\Theta$ 的先验 PMF（prior PMF）。因此，若把 $p_X(x;\theta)$ 视作条件 PMF，我们即可把 ML 估计解释为**采用平先验（flat prior）的 MAP 估计**，即对一切 $\theta$ 都相同的先验，它表明没有任何有用的先验知识。类似地，在 $\theta$ 具有有界取值域的连续情形下，我们可以把 ML 估计解释为**采用均匀先验（uniform prior）的 MAP 估计**：对一切 $\theta$ 及某个常数 $c$ 有 $f_{\Theta}(\theta) = c$。

> <span style="color:#1e8449;">**[t_note]** 注：把 ML 说成『平先验下的 MAP』是理解二者血缘的钥匙。先证：MAP 最大化 $f_\Theta(\theta)\,f_{X\mid\Theta}(x\mid\theta)$；当先验是常数 $c$，乘上 $c$ 不影响 argmax，便退化为极大似然。这也解释了为何 Example 9.1、9.2 的结论常与前章贝叶斯例子一致——差别只在『先验常数』被 arg max 吸收、消失不见。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.1（重温 Example 8.2 的经典视角。）**</span>

让我们重温 Example 8.2，其中 Juliet 总是迟到，迟到时间 $X$ 在区间 $[0,\theta]$ 上服从均匀分布，而 $\theta$ 是未知参数。在那个例子中，我们用先验 PDF 取平直（flat）的随机变量 $\Theta$（在 $[0,1]$ 上均匀）来为该参数建模，并证明了 MAP 估计值是 $X$ 的实现值 $x$。在本节经典框架下没有先验，$\theta$ 被当作常数处理，但 ML 估计也同样是 $\hat{\theta} = x$。

> <span style="color:#1e8449;">**[t_note]** 注：Example 9.1 的『平凡』是故意为之：对 $[0,\theta]$ 均匀，观测到 $x$ 要求 $\theta\ge x$（否则密度为 0），而密度 $1/\theta$ 随 θ 递减——故 ML 恰是 θ 的最小可行值 $x$。先证：它示范了『ML 会吹到可行域硬边界』——浅层叫『取 x』，深层是『最大似然落点是下沿』。它也同步说明经典 ML 与贝叶斯 MAP（平先验）在这一题给出同一个数。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.2　估计一个 Bernoulli 随机变量的均值（Estimating the Mean of a Bernoulli Random Variable）**</span>

我们希望基于一枚不均匀硬币 $n$ 次独立抛掷的结果 $X_{1},\ldots,X_{n}$（正面时 $X_i=1$，反面时 $X_i=0$）来估计其正面概率 $\theta$。这与我们假定平先验的 Example 8.8 的贝叶斯设定相似。在那里我们发现后验 PDF 的峰（即 MAP 估计）位于 $\theta = k/n$，其中 $k$ 是观测到的正面次数。由此可知 $k/n$ 也是 $\theta$ 的 ML 估计，故 ML 估计量为
```math
\hat{\Theta}_{n} = \frac{X_{1} + \cdots + X_{n}}{n}.
```
该估计量是无偏（unbiased）的。它也是相合（consistent）的，因为按弱大数定律（weak law of large numbers），$\hat{\Theta}_{n}$ 依概率收敛到 $\theta$。

把该 ML 估计量与用贝叶斯方法在 Example 8.8 中得到的 LMS 估计量作比较是有趣的。在那里我们证明：在平先验下，后验均值是 $(k+1)/(n+2)$。因此，ML 估计 $k/n$ 与贝叶斯方法得到的 LMS 估计相似但不完全相同。不过，随着 $n \to \infty$，这两个估计渐近一致。

> <span style="color:#1e8449;">**[t_note]** 注：$k/n$ 无偏+相合、$(k+1)/(n+2)$（平先验下的后验均值）有偏但渐近无偏，二者随 $n$ 趋于同一极限。先证：$E\big[(k+1)/(n+2)\big]=\frac{n\theta+1}{n+2}\to\theta$。这条『ML 与贝叶斯在 $n\to\infty$ 汇合』是统计里很深的主题：先验的影响随数据量被稀释——观测越多，先验越不重要。</span>

---

<!-- ===== PDF p471 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 464（页眉「Cla.ssical Statistical Inference / 464 / Chap. 9」）。本页承接 §9.1 中段：页首为 **Example 9.3**（完整给出），随后是过渡段并开启 **Example 9.4**（本页给出似然函数，推导续至下一页）。§9.1 内例题编号从 9.1 起连续，本页为 Example 9.3、9.4。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.3（估计指数随机变量的参数，Estimating the Parameter of an Exponential Random Variable）**</span>

顾客（customers）前往某设施，第 $i$ 位顾客的到达时刻记为 $Y_i$。我们假设第 $i$ 个到达间隔时间（interarrival time，
$X_i = Y_i - Y_{i-1}$，并约定 $Y_0 = 0$）服从参数未知为 $\theta$ 的指数分布（exponential distribution），且随机变量 $X_1, \dots, X_n$ 相互独立。（这就是第 6 章研究过的泊松到达（Poisson arrivals）模型。）我们希望基于观测 $X_1, \dots, X_n$ 来估计 $\theta$ 的值（将其解释为到达速率 arrival rate）。

对应的似然函数（likelihood function）为

```math
f_X(x; \theta) = \prod_{i=1}^{n} \theta e^{-\theta x_i} = \theta^{\,n} e^{-\theta y_n},
```

而对数似然函数（log-likelihood function）为

```math
\log f_X(x; \theta) = n \log \theta - \theta Y_n,
```

其中

```math
Y_n = \sum_{i=1}^{n} X_i.
```

关于 $\theta$ 的导数是 $(n / \theta) - Y_n$，将其置为 $0$，我们看到 $\log f_X(x; \theta)$ 在 $\theta \ge 0$ 上的最大值在 $\hat{\theta}_n = n / Y_n$ 处取得。由此得到的估计量（estimator）是

```math
\hat{\theta}_n = \left( \frac{Y_n}{n} \right)^{-1} .
```

它是到达间隔时间样本均值（sample mean）的倒数，可被解释为一种经验到达速率（empirical arrival rate）。

> <span style="color:#1e8449;">**[t_note]** 注：Example 9.3 示范『对数似然』技巧：因为 $\log$ 单调递增，最大化 $\log f$ 与 $f$ 等价，却把乘积变求和、求导大幅化简。先证：$\log\big(\prod \theta e^{-\theta x_i}\big)=n\log\theta-\theta\sum_i x_i$，令导数为 0 解出 $\hat\theta_n=\big(\frac1n\sum_i X_i\big)^{-1}$（均值倒数=经验到达率）。其相合来自弱大数定律 $\frac1n\sum_i X_i\xrightarrow{p}E[X_1]=1/\theta$ 加上连续映射；注意『均值倒数』有偏（Jensen：$1/\cdot$ 凸，$E[1/\bar X]\neq1/E[\bar X]$），所以这里只断言相合/渐近无偏、不断言无偏——正是前面偏差三兄弟分家的用武之地。</span>

注意，由大数定律弱形式（weak law of large numbers），$Y_n / n$ 随 $n \to \infty$ 依概率收敛于 $E[X_1] = 1 / \theta$。由此可用来证明 $\hat{\theta}_n$ 依概率收敛于 $\theta$，所以该估计量是相合的（consistent）。

到目前为止，我们的讨论与例子都聚焦于单一未知参数 $\theta$ 的情形。下一个例子涉及一个二维参数。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.4（估计正态分布的均值与方差，Estimating the Mean and Variance of a Normal）**</span>

考虑利用 $n$ 个独立观测 $X_1, \dots, X_n$ 来估计正态分布（normal distribution）的均值 $\mu$ 与方差 $v$ 的问题。这里的参数向量为 $\theta = (\mu,\, v)$。对应的似然函数为

```math
f_X(x; \mu, v) = \frac{1}{(2\pi v)^{n/2}} \cdot \exp\left\{ -\frac{n \tilde{s}_n^2}{2v} \right\} \cdot \exp\left\{ -\frac{n(m_n - \mu)^2}{2v} \right\},
```

经一番计算可写成上式。$^{\,t}$ 其中 $m_n$ 是随机变量 $M_n = \frac{1}{n}\sum_{i=1}^{n}X_i$ 的实现值，$\tilde{s}_n^2$ 是随机变量 $\tilde{S}_n^2 = \frac{1}{n}\sum_{i=1}^{n}(X_i - M_n)^2$ 的实现值。

---

<!-- ===== PDF p472 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 465（页眉「Sec. 9.1 / 465」）。本页继续 **Example 9.4**（估计正态分布均值与方差）：导出 log-likelihood、求解 ML 估计量，随后转入极大似然（ML）方法的一般性质讨论。上一页 Example 9.4 的似然函数分解脚注文本在本页出现，置于作注之处。</span>

---

……其中 $m_n$ 是随机变量 $M_n = \frac{1}{n}\sum_{i=1}^{n}X_i$ 的实现值，$\tilde{s}_n^2$ 是随机变量 $\tilde{S}_n^2 = \frac{1}{n}\sum_{i=1}^{n}(X_i - M_n)^2$ 的实现值。

对数似然函数为

```math
\log f_X(x; \mu, v) = -\frac{n}{2} \log(2\pi) - \frac{n}{2} \log v - \frac{n\tilde{s}_n^2}{2v} - \frac{n(m_n - \mu)^2}{2v}.
```

令该函数关于 $\mu$ 与 $v$ 的导数分别为 $0$，我们分别得到下面的估计值（estimate）与估计量（estimator）：

```math
\hat{\mu} = m_n, \qquad \hat{v} = \tilde{s}_n^2 .
```

注意 $M_n$ 是样本均值（sample mean），而 $\tilde{S}_n^2$ 可被视为「样本方差（sample variance）」。正如稍后将证明的，$E_{\theta}[\tilde{S}_n^2]$ 随 $n$ 增大而趋于 $v$，因此 $\tilde{S}_n^2$ 是渐近无偏（asymptotically unbiased）的。再借助大数定律弱形式，可以证明 $M_n$ 与 $\tilde{S}_n^2$ 分别是对 $\mu$ 和 $v$ 的相合估计量（consistent estimators）。

> <span style="color:#1e8449;">**[t_note]** 注：Ex9.4 的似然分解靠一条恒等式（对应脚注 t）：$\sum_i(x_i-\mu)^2=\sum_i(x_i-m_n)^2+n(m_n-\mu)^2$，其中交叉项 $\sum_i(x_i-m_n)=nm_n-nm_n=0$ 抵消。先证：这相当于『总离差平方和 = 组内离差 + n × 组间离差』，把对 μ 和对 v 的优化解耦——于是分别求导互不牵连，得 $\hat\mu=m_n$、$\hat v=\tilde s_n^2$。跨课程（线性代数 Strang）：这又是向零均值子空间的投影分解，交叉项为 0 正是投影正交性的代数记号。</span>

极大似然（ML）估计具有一些讨人喜欢的性质。例如，它满足不变量原则（invariance principle）：若 $\hat{\theta}_n$ 是 $\theta$ 的 ML 估计，则对 $\theta$ 的任意一一（one-to-one）函数 $h$，参数 $\zeta = h(\theta)$ 的 ML 估计就是 $h(\hat{\theta}_n)$。此外，当观测是独立同分布（i.i.d.）且在一些温和的附加假设下，可以证明 ML 估计量是相合的。

> <span style="color:#1e8449;">**[t_note]** 注：不变量原则说『$\zeta=h(\theta)$ 的 ML 估计就是 $h(\hat\theta)$』。先证：因为 $h$ 一一（单射），把关于 ζ 最大化改写回关于 θ 最大化、再复合 $h$，argmax 的位置在单射重参数化下保持不变。这也与贝叶斯 MAP 在变量代换下的行为一致——它是『先算出 $\hat\theta$、再把它带进别的公式』这种最常用整理做法的逻辑后台。</span>

另一个有趣的性质是：当 $\theta$ 为标量参数时，在一些温和条件下，ML 估计量具有渐近正态性（asymptotic normality）性质。特别地，可以证明 $(\hat{\theta}_n - \theta)/a(\hat{\theta}_n)$ 的分布（其中 $a^2(\hat{\theta}_n)$ 是 $\hat{\theta}_n$ 的方差）趋近标准正态分布。于是，如果我们还能估计出 $a(\hat{\theta}_n)$，就可以据此导出基于正态近似（normal approximation）的误差方差估计。当 $\theta$ 是向量参数时，其每一个分量都有类似的陈述成立。

> <span style="color:#1e8449;">**[t_note]** 注：渐近正态性是 ML 最实用的礼物：大样本下 $\hat\theta_n$ 像绕着真值 θ 的正态噪声，于是可以照抄后面 Example 9.6 的置信区间套路。先证：直觉来自 log-似然在最大点附近的局部二次（抛物线）近似，加上『若干独立项之和→正态』的中心极限倾向，合起来让 $\hat\theta_n$ 渐近正态。这条『估计量 → 近似正态 → 构造区间』的链路在后面要反复调用。</span>

> <span style="color:#7f8c8d;">[原页脚注 $t$] 为验证本例似然函数中均值—方差的二次型分解（$\sum (x_i - \mu)^2 = \sum (x_i - m_n)^2 + n(m_n - \mu)^2$）：对 $i = 1, \dots, n$ 写出恒等式 $x_i - \mu = (x_i - m_n) + (m_n - \mu)$，对 $i$ 求和，并注意 $\sum_{i=1}^{n}(x_i - m_n)^2$ 展开中的交叉项 $\sum_{i=1}^{n}(x_i - m_n) = nm_n - nm_n = 0$，即可完成分解。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本例多处算子与平方符号被 OCR 误读（如 $\tilde{S}_n^2$ 的平方、指数中的负号与 `e p` 碎片等），已按标准正态似然推导的数学语义（$\sum(x_i-\mu)^2$ 的均值—方差分解、ML 求导置零）忠实还原，未臆造数值。</span>

---

<!-- ===== PDF p473 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 466（页眉「Cla.ssical Statistical Inference / 466 / Chap. 9」）。页首为 §9.1 的框内小结「极大似然估计（Maximum Likelihood Estimation）」，随后开启新小节「估计一个随机变量的均值与方差」，并开启 **Example 9.5**（页尾起步，续至下一页）。</span>

---

<span style="color:#00838f;">**[定义] 极大似然估计（Maximum Likelihood Estimation）——本章小结框**</span>

- 给定随机向量 $X = (X_1, \dots, X_n)$ 的实现 $(x_1, \dots, x_n)$，它按 PMF $p_X(x; \theta)$ 或 PDF $f_X(x; \theta)$ 分布。
- **极大似然（ML）估计**是对所有 $\theta$ 上使得似然函数（likelihood function）$p_X(x; \theta)$ 或 $f_X(x; \theta)$ 取最大值的那个 $\theta$ 值。
- $\theta$ 的一一函数 $h(\theta)$ 的 ML 估计是 $h(\hat{\theta}_n)$，其中 $\hat{\theta}_n$ 是 $\theta$ 的 ML 估计（不变量原则 invariance principle）。
- 当随机变量 $X_i$ 独立同分布，且在一些温和的附加假设下，ML 估计量的每一个分量都是相合的（consistent）且渐近正态（asymptotically normal）的。

---

<span style="color:#c0392b;">**估计一个随机变量的均值与方差（Estimation of the Mean and Variance of a Random Variable）**</span>

我们现在讨论估计一个概率分布的均值与方差这一简单而重要的问题。这与前面的 Example 9.4 相似，但与那个例子不同，我们并不假设分布是正态的。事实上，这里给出的估计量并不需要知道分布 $p_X(x; \theta)$（若 $x$ 连续则为 $f_X(x; \theta)$）的形式。

假设观测 $X_1, \dots, X_n$ 独立同分布，具有未知的公共均值 $\theta$。$\theta$ 最自然的估计量是样本均值（sample mean）：

```math
M_n = \frac{X_1 + \dots + X_n}{n}.
```

该估计量是无偏（unbiased）的，因为 $E_{\theta}[M_n] = E_{\theta}[X] = \theta$。它的均方误差（mean squared error）等于它的方差，即 $v / n$，其中 $v$ 是 $X_i$ 的公共方差。注意，这里的均方误差并不依赖于 $\theta$。此外，由大数定律弱形式，该估计量依概率收敛于 $\theta$，因此是相合的（consistent）。

> <span style="color:#1e8449;">**[t_note]** 注：样本均值的均方误差恰是 $v/n$ 且与 θ 无关——这是置信区间『半宽随样本方差缩小』的种子。先证：无偏性给出 $E[(\hat\theta_n-\theta)^2]=\mathrm{var}(\hat\theta_n)=\mathrm{var}(X)/n=v/n$；误差 ~$\sigma/\sqrt n$ 衰减，所以把区间做成 $\hat\theta_n\pm z_{\alpha/2}S_n/\sqrt n$ 才能以指定概率夹住未知 θ。这也直观说明『样本量翻倍、误差只压到 $1/\sqrt 2$』，加样本的边际回报正在递减。</span>

样本均值未必是方差最小的估计量。例如，考虑估计量 $\hat{\theta}_n = 0$，它忽略所有观测、总是输出 $0$ 作为估计值。$\hat{\theta}_n$ 的方差为零，但它的偏差（bias）为 $b_{\theta}(\hat{\theta}_n) = -\theta$。特别地，其均方误差依赖于 $\theta$，等于 $\theta^2$。

下一个例子将样本均值与我们曾在第 8 章 §8.2 在特定假设下导出的一个贝叶斯 MAP 估计量进行比较。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.5（贝叶斯 MAP 估计量 vs 样本均值）**</span>

假设观测 $X_1, \dots, X_n$ 是正态、独立同分布的，具有未知公共均值 $\theta$ 与已知方差 $v$。在 Example 8.3 中，我们采用了贝叶斯方法（Bayesian approach），并在参数 $\theta$ 上假设了一个正态先验分布（prior distribution）。

---

<!-- ===== PDF p474 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 467（页眉「Sec. 9.1 / 467」）。本页继续 **Example 9.5**：给出贝叶斯先验均值取零时的估计量及其偏差、方差，并进一步对（非常规假设下的）样本方差估计量 $\tilde{S}_n^2$ 计算其期望，证明其有偏而渐近无偏。</span>

---

……$\theta$。对于先验均值（prior mean）取为零的情形，我们得到了如下估计量：

```math
\hat{\theta}_n = \frac{X_1 + \dots + X_n}{n + 1}.
```

该估计量是有偏（biased）的，因为 $E_{\theta}[\hat{\theta}_n] = n\theta/(n+1)$，且 $b_{\theta}(\hat{\theta}_n) = -\theta/(n+1)$。然而，$\lim_{n \to \infty} b_{\theta}(\hat{\theta}_n) = 0$，所以 $\hat{\theta}_n$ 是渐近无偏（asymptotically unbiased）的。它的方差为

```math
\mathrm{var}_{\theta}(\hat{\theta}_n) = \frac{n\cdot v}{(n+1)^2},
```

比样本均值的方差 $v/n$ 略小。

> <span style="color:#1e8449;">**[t_note]** 注：Example 9.5 的教训是『先验（把均值拉向 0）换来了更小的方差，却付出了偏差』：$\hat\theta_n=\frac{n}{n+1}\bar X$ 有偏差 $-\frac{\theta}{n+1}$、方差 $\frac{nv}{(n+1)^2}<\frac{v}{n}$。先证：只有把无偏与有偏两个估计都代进 $E[(\cdot-\theta)^2]=b^2+\mathrm{var}$ 才能公平比较——有偏未必更差。这与 Problem 里『ML vs 贝叶斯 LMS』的取舍、以及凸优化里的 bias-variance trade 是同一个骨架。</span>

注意，本例子这一特殊情况下的 $\mathrm{var}_{\theta}(\hat{\theta}_n)$ 与 $\theta$ 无关。其均方误差等于

```math
E_{\theta}\big[(\hat{\theta}_n - \theta)^2\big] = \mathrm{var}_{\theta}(\hat{\theta}_n) + b_{\theta}(\hat{\theta}_n)^2 = \frac{nv}{(n+1)^2} + \frac{\theta^2}{(n+1)^2}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上文方差与均方误差的具体公式在源 OCR 中仅以碎片与不完整行出现（如 `v/(n+1)`、函数行缺项），此处按 $\hat{\theta}_n = \frac{1}{n+1}\sum X_i$ 的标准统计量方差/偏差推导（$\mathrm{var}(\sum X_i)=(n+1)\cdot v$）忠实还原，未臆造数值。</span>

假设计除了对 $\theta$ 的样本均值估计量

```math
M_n = \frac{X_1 + \dots + X_n}{n},
```

我们还想对方差 $v$ 做一个估计量。一个自然的估计是

```math
\tilde{S}_n^2 = \frac{1}{n}\sum_{i=1}^{n}(X_i - M_n)^2,
```

它在正态性假设下与 Example 9.4 中导出的 ML 估计量一致。

利用恒等式 $E_{(\theta,\,v)}[X_1^{\,2}] = \theta^2 + v$，我们有

```math
\begin{aligned}
E_{(\theta,\,v)}\big[\tilde{S}_n^2\big]
&= E_{(\theta,\,v)}\left[\frac{1}{n}\sum_{i=1}^{n}X_i^{\,2} - 2M_n\cdot\frac{1}{n}\sum_{i=1}^{n}X_i + M_n^{2}\right] \\[2pt]
&= E_{(\theta,\,v)}\left[\frac{1}{n}\sum_{i=1}^{n}X_i^{\,2} - M_n^{2}\right] \\[2pt]
&= (\theta^2 + v) - \left(\theta^2 + \frac{v}{n}\right) \\[2pt]
&= \frac{n-1}{n}\,v .
\end{aligned}
```

所以 $E_{(\theta,\,v)}[\tilde{S}_n^2] = \frac{n-1}{n} v$。

---

<!-- ===== PDF p475 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 468（页眉「Cla.ssical Statistical Inference / 468 / Chap. 9」）。本页承接上页 $\tilde{S}_n^2$ 的期望计算：指出其有偏，给出经缩放的无偏方差估计量 $S_n^2$，随后是框内小结「估计一个随机变量的均值与方差」，并开启新小节「置信区间（Confidence Intervals）」。</span>

---

因此，$\tilde{S}_n^2$ 并不是 $v$ 的无偏估计量，尽管它是渐近无偏（asymptotically unbiased）的。

> <span style="color:#1e8449;">**[t_note]** 注：$E[\tilde S_n^2]=\frac{n-1}{n}v$ 有偏的根，在于用样本均值 $M_n$ 替代真均值 μ 时『吃掉』了 1 个自由度——$n$ 个数在固定 $M_n$ 之后，真正自由的是 $n-1$ 个。先证：$\tilde S_n^2=\frac1n\sum_i(X_i-M_n)^2$ 算出期望 $\frac{n-1}{n}v$，故乘上 $n/(n-1)$ 得无偏的 $S_n^2$。这个『为什么除以 $n-1$』的谜底就是自由度损失；$n$ 较大时两个估计几乎重合。</span>

经过适当的缩放，我们可以得到一个无偏的方差估计量。这就是估计量

```math
S_n^2 = \frac{1}{n-1}\sum_{i=1}^{n}(X_i - M_n)^2 = \frac{n}{n-1}\,\tilde{S}_n^2 .
```

前面的计算表明

```math
E_{(\theta,\,v)}\big[S_n^2\big] = v,
```

所以 $S_n^2$ 对一切 $n$ 都是 $v$ 的无偏估计量。不过，当 $n$ 较大时，估计量 $\tilde{S}_n^2$ 与 $S_n^2$ 实质上是相同的。

<span style="color:#00838f;">**[定义] 估计一个随机变量的均值与方差（Estimates of the Mean and Variance of a Random Variable）——本章小结框**</span>

- 设观测 $X_1, \dots, X_n$ 独立同分布，均值 $\theta$ 与方差 $v$ 未知。
- 样本均值

```math
M_n = \frac{X_1 + \dots + X_n}{n}
```

是 $\theta$ 的无偏估计量，其均方误差为 $v / n$。

- 两个方差估计量是

```math
\tilde{S}_n^2 = \frac{1}{n}\sum_{i=1}^{n}(X_i - M_n)^2, \qquad S_n^2 = \frac{1}{n-1}\sum_{i=1}^{n}(X_i - M_n)^2 .
```

- 若 $X_i$ 是正态的，$\tilde{S}_n^2$ 与 ML 估计量一致。它有偏但渐近无偏；$S_n^2$ 无偏。当 $n$ 较大时两个方差估计量实质上重合。

---

<span style="color:#c0392b;">**置信区间（Confidence Intervals）**</span>

考虑未知参数 $\theta$ 的一个估计量 $\hat{\theta}_n$。除了一个估计值所提供的数值之外，我们往往还关心构造所谓的置信区间（confidence interval）。粗略地说，这是一个对 $\theta$ 的每个可能取值都以某一高概率包含 $\theta$ 的区间。

为使定义精确，先固定一个期望的置信水平（confidence level）$1 - \alpha$，其中 $\alpha$ 通常是一个小数值。然后，我们把点估计量 $\hat{\theta}_n$ 替换为一个下估计量（lower estimator）$\hat{\theta}_n^{-}$ 与一个上估计量（upper estimator）$\hat{\theta}_n^{+}$，二者被设计得满足 $\hat{\theta}_n^{-} \le \hat{\theta}_n^{+}$，且（对 $\theta$ 的每个可能取值）……（续至下一页）

---

<!-- ===== PDF p476 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 469（页眉「Sec. 9.1 / 469」）。本页承接上页「置信区间」小节的定义，给出 **Example 9.6**（正态、方差已知时基于样本均值的置信区间，含脚注 $t$），并讨论置信区间的正确解释。</span>

---

……且满足

```math
P_{\theta}\big(\hat{\theta}_n^{-} \le \theta \le \hat{\theta}_n^{+}\big) = 1 - \alpha,
```

对 $\theta$ 的每个可能取值都成立。注意，与估计量类似，$\hat{\theta}_n^{-}$ 与 $\hat{\theta}_n^{+}$ 都是观测的函数，因而是分布依赖于 $\theta$ 的随机变量。我们把区间 $[\hat{\theta}_n^{-},\ \hat{\theta}_n^{+}]$ 称为一个 $1 - \alpha$ 置信区间。

> <span style="color:#1e8449;">**[t_note]** 注：读这条定义要抓住『谁是随机变量』。$\hat{\theta}_n^{-}$、$\hat{\theta}_n^{+}$ 是观测的函数、因而是随机的；而 $\theta$ 是固定的未知常数。所以 $P_{\theta}\big(\hat{\theta}_n^{-}\le\theta\le\hat{\theta}_n^{+}\big)=1-\alpha$ 说的是『随机区间盖住常数』的频率，绝不是『这一次算出的具体区间盖住 θ』的概率。这正是后面 Example 9.6 那句『反复构造区间、约 95% 会盖住 θ』直觉的出处。跨课程（离散数学 6.042J）：这是『随机性在于过程、而非单次结果』的量化版——与『一步随机运行是随机的、单次执行快照是确定的』同构，不把二者混淆是基本素养。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.6（方差已知时均值 $\theta$ 的置信区间）**</span>

假设观测 $X_i$ 独立同分布、为正态，均值 $\theta$ 未知、方差 $v$ 已知。于是，样本均值估计量 $M_n$ 是正态的，$^{\,t}$ 均值为 $\theta$、方差为 $v/n$。令 $\alpha = 0.05$。利用标准正态分布的 CDF $\Phi(z)$（可在正态分布表 normal tables 中查到），我们有 $\Phi(1.96) = 0.975 = 1 - \alpha/2$，从而得到

```math
P_{\theta}\left(\frac{\lvert M_n - \theta\rvert}{\sqrt{v/n}} \le 1.96\right) = 0.95 .
```

我们可以把这一陈述改写为

```math
P_{\theta}\left(M_n - 1.96\sqrt{v/n} \le \theta \le M_n + 1.96\sqrt{v/n}\right) = 0.95,
```

这意味着

```math
\left[M_n - 1.96\sqrt{\frac{v}{n}},\ \ M_n + 1.96\sqrt{\frac{v}{n}}\right]
```

是一个 95% 置信区间，其中我们分别把下端点认作 $M_n - 1.96\sqrt{v/n}$、把上端点认作 $M_n + 1.96\sqrt{v/n}$。

> <span style="color:#1e8449;">**[t_note]** 注：Example 9.6 的核心招数是『拿起一个枢轴量（pivot）$\frac{M_n-\theta}{\sqrt{v/n}}$』：它含未知量 θ，但它的分布（$\mathcal{N}(0,1)$）却不含 θ。于是先对枢轴写概率 $P\big(|Z|\le1.96\big)=0.95$，再对不等式做代数反解、把 θ 夹到中间，就得到置信区间。先证：$\frac{M_n-\theta}{\sqrt{v/n}}$ 正是 $M_n$ 中心化又按标准差缩放后的量，正态性与 θ 无关使上面两步全都合法。这个『构造分布已知、仅把未知量孤立在不等式一端的量』的通用技巧，是所有置信区间乃至后面既有 LRT（9.12）的共用骨架。</span>

> <span style="color:#7f8c8d;">注意：这里用到了「相互独立的正态随机变量之和仍是正态的」这一重要事实（参见第 4 章）。</span>

在前面这个例子中，我们也许会忍不住用这样一句话来描述 95% 置信区间的概念：「真实参数以 $0.95$ 的概率落在置信区间之内」。然而，这类陈述可能是有歧义的。例如，假设得到观测之后，置信区间碰巧是 $[-2.3,\ 4.1]$。我们不能说 $\theta$ 以 $0.95$ 的概率落在 $[-2.3,\,4.1]$ 之中，因为后一句陈述不涉及任何随机变量；说到底，在经典方法（classical approach）中，$\theta$ 是一个常数。相反，在「真实参数落在置信区间内」这一短语中，随机的实体是置信区间，而不是真实参数。

> <span style="color:#1e8449;">**[t_note]** 注：原文特意点破一个高频误读——『置信区间以 95% 概率盖住 θ 』正确，『θ 以 95% 概率落在本次算出的某个固定区间里』错误。根源（先证）：经典框架里 θ 不是随机变量，没有分布、也就谈不上概率；有概率的是端点 $\hat\theta_n^{-},\hat\theta_n^{+}$，它们随观测变化。所以正确读法是把『置信水平』理解成**同一程序被反复执行时的覆盖频率**（约 95% 的区间盖住 θ），而非单次结论的可信度。这与你前面在 8.x 学的贝叶斯『θ 的分布』形成鲜明对照——同一『区间可信度』问题，贝叶斯给后验、经典给覆盖频率，别把两者混为一谈。</span>

为了给出具体的解释，假设 $\theta$ 固定。我们用同一种统计程序反复构造置信区间，也就是说，每次获得一组独立的 $n$ 个观测并构造相应的 95% 置信区间……（续至下一页）

---

<!-- ===== PDF p477 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 470（页眉「Cla.ssical Statistical Inference / 470 / Chap. 9」）。本页先结束上页 Example 9.6 的讨论（跨页的「each time」一句至此收束），随后是框内小结「置信区间（Confidence Intervals）」，并开启新小节「基于估计量方差近似的置信区间（Confidence Intervals Based on Estimator Variance Approximations）」，页尾进入该小节正文。</span>

---

……时间，我们获得一组独立的 $n$ 个观测并构造相应的 95% 置信区间。于是我们预期其中约有 95% 的置信区间会把 $\theta$ 包含在内。无论 $\theta$ 的取值是什么，这一点都应当成立。

<span style="color:#00838f;">**[定义] 置信区间（Confidence Intervals）——本章小结框**</span>

- 对标量未知参数 $\theta$ 的置信区间（confidence interval）是一个端点 $\hat{\theta}_n^{-}$ 与 $\hat{\theta}_n^{+}$ 以给定高概率把 $\theta$ 夹在其中的区间。
- $\hat{\theta}_n^{-}$ 与 $\hat{\theta}_n^{+}$ 是依赖观测 $X_1, \dots, X_n$ 的随机变量。
- 一个 $1 - \alpha$ 置信区间满足

```math
P_{\theta}\big(\hat{\theta}_n^{-} \le \theta \le \hat{\theta}_n^{+}\big) = 1 - \alpha,
```

对 $\theta$ 的一切可能取值成立。

置信区间通常是在一个估计量 $\hat{\theta}_n$ 周围构造区间得到（cf. Example 9.6）。此外，在各种可行的置信区间中，通常希望选取宽度尽可能小的那个。然而，由于误差 $\hat{\theta}_n - \theta$ 的分布要么未知、要么依赖于 $\theta$，这种构造有时十分困难。幸运的是，对许多重要的模型，$\hat{\theta}_n - \theta$ 是渐近正态（asymptotically normal）且渐近无偏（asymptotically unbiased）的。所谓渐近无偏，我们是指随机变量

```math
\frac{\hat{\theta}_n - \theta}{\sqrt{\mathrm{var}_{\theta}(\hat{\theta}_n)}}
```

的 CDF 随 $n$ 增大而对 $\theta$ 的每个取值都趋近标准正态 CDF。只要 $\mathrm{var}_{\theta}(\hat{\theta}_n)$ 已知或可被近似，我们随后就可以完全按照此前正态例子（Example 9.6）中的方式继续下去。

<span style="color:#c0392b;">**基于估计量方差近似的置信区间（Confidence Intervals Based on Estimator Variance Approximations）**</span>

假设观测 $X_i$ 独立同分布，均值 $\theta$ 与方差 $v$ 未知。我们可以用样本均值

```math
\hat{\theta}_n = \frac{X_1 + \dots + X_n}{n}
```

来估计 $\theta$，并用无偏估计量

```math
S_n^2 = \frac{1}{n-1}\sum_{i=1}^{n}(X_i - \hat{\theta}_n)^2
```

来估计 $v$。

---

<!-- ===== PDF p478 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 471（页眉「Sec. 9.1 / 471」）。本页继续「基于估计量方差近似的置信区间」小节：用 $S_n^2/n$ 近似样本均值方差构造近似置信区间，并引入 t-分布（t-distribution）。页尾为 t-分布背景脚注 $t$，其表解续至下一页。</span>

---

……也就是我们此前引入的那个估计量。特别地，我们可以用 $S_n^2 / n$ 来估计样本均值的方差 $v / n$。于是，对给定的 $\alpha$，我们可以借助这些估计与中心极限定理（central limit theorem）构造一个（近似的）$1 - \alpha$ 置信区间。这就是区间

```math
\hat{\theta}_n \pm z_{\alpha/2}\, \frac{S_n}{\sqrt{n}},
```

其中 $z_{\alpha/2}$ 由关系式

```math
\Phi(z) = 1 - \frac{\alpha}{2}
```

与正态分布表确定，$S_n$ 是 $S_n^2$ 的正平方根。例如，若 $\alpha = 0.05$，我们利用 $\Phi(1.96) = 0.975 = 1 - \alpha/2$（来自正态分布表）而得到一个形如

```math
\hat{\theta}_n \pm 1.96\,\frac{S_n}{\sqrt{n}}
```

的近似 95% 置信区间。

> <span style="color:#7f8c8d;">注意：在这个方法中实际存在两种不同的近似。首先，我们把 $\hat{\theta}_n$ 当作正态随机变量来对待；其次，我们用 $\hat{\theta}_n$ 真实方差 $v / n$ 的估计 $S_n^2 / n$ 去替换它。</span>

即便在 $X_i$ 就是正态随机变量的特殊情形下，上述程序所构造的置信区间也仍是近似的。原因在于，$S_n^2$ 只是真实方差 $v$ 的一个近似，而随机变量

```math
T_n = \frac{\sqrt{n}\,(\hat{\theta}_n - \theta)}{S_n}
```

并不是正态的。不过，当 $X_i$ 为正态时，可以证明 $T_n$ 的 PDF 并不依赖于 $\theta$ 与 $v$，并且可以被显式地计算出来。这个分布被称为具有 $n-1$ 个自由度（degrees of freedom）的 t-分布（t-distribution）。$^{\,t}$ 与标准正态 PDF 一样，它是关于零点对称的钟形（bell-shaped）分布，但它略为铺展得更开、尾部更重（参见 Fig. 9.3）。各种感兴趣区间的概率可查表获得，与正态分布表类似。因此，当 $X_i$ 是正态（或近似正态）且 $n$ 相对较小时，一个更精确的置信区间的形式为

```math
\hat{\theta}_n \pm w_{n-1}\!\left(1 - \frac{\alpha}{2}\right)\frac{S_n}{\sqrt{n}},
```

其中 $w_{n-1}$ 是 t-分布的 CDF $W_{n-1}$ 的反函数（其表解续至下一页）。

> <span style="color:#1e8449;">**[t_note]** 注：t-分布回答的是『方差未知、只能用 $S_n$ 去估』时，比值 $T_n=\frac{\sqrt{n}\,(\hat\theta_n-\theta)}{S_n}$ 到底多大才算反常。先证它与正态的三个点：第一，当 $X_i$ 正态时 $T_n$ 的分布**不含 θ 也不含 v**（分子分母的 $v$ 恰好约掉），故可据自由度查表定分位；第二，它比标准正态略『胖』、尾部更重——因为分母 $S_n$ 本身带随机性，让小样本时大偏差更常见；第三，自由度 $n-1$ 正来自 $S_n^2$ 里那个除以 $n-1$（估均值损失 1 个自由度，见上一小节 $n-1$ 的出处）。记忆锚：$n\to\infty$、自由度→∞时 t 化为标准正态（表里最末行正是 $z$ 分位 1.96、1.645）。跨课程（统计学导论）：这就是『何时必须用 t、何时可退用 z』的总纲。</span>

> <span style="color:#7f8c8d;">[原页脚注 $t$] t-分布具有许多有趣的性质，也可以写成闭式（closed form）表达，但对我们而言精确公式并不重要。它有时被称为「学生分布（Student's distribution）」。它于 1908 年由威廉·戈塞特（William Gosset）发表，当时他在都柏林的一家酿酒厂工作。因为被禁止以自己的名义发表论文，他以笔名 Student 撰写该文。戈塞特当时关心的是高产大麦品种的选育问题，不得不用很小的样本量来工作。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本节置信区间公式在源 OCR 中被切碎成多行（上、下端点的 `+`/`−` 符号、$w_{n-1}$ 参数与 `Wn−1` 等形式残缺），已按 t-分布置信区间（$\hat{\theta}_n \pm t\cdot S_n/\sqrt{n}$）的标准形式忠实还原，未臆造数值。</span>

---

<!-- ===== PDF p479 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 472（页眉「Chap. 9 / 472」）。本页承接上页 t-分布置信区间公式：给出其取 $z$ 的方式、t-分布表 CDF 说明与 Fig. 9.3，随后开启 **Example 9.7**（用 t-分布构造物体称重数据的 95% 置信区间，页尾起步、续至下一页）。</span>

---

……其中 $z$（此处应作相应 t-分布分位点）由关系式 $W_{n-1}(z) = 1 - \alpha/2$ 确定，$W_{n-1}(z)$ 是具有 $n-1$ 个自由度的 t-分布的 CDF，可从表中查得。这些表在许多资料中都能找到；本页对面的那页给出了一个简略本。

**概率密度函数（Probability Density Function）**

（此处为 Fig. 9.3 示意图：同图比较具有不同自由度下 t-分布的 PDF 与标准正态 PDF。）

<figure>
<figcaption><span style="color:#7f8c8d;">**Figure 9.3.**—— 具有 $n-1$ 个自由度的 t-分布 PDF 与标准正态 PDF 的对比。</span></figcaption>
</figure>

另一方面，当 $n$ 中等偏大时（例如 $n \ge 50$），t-分布与正态分布已经十分接近，此时可以直接使用正态分布表。

> <span style="color:#1e8449;">**[t_note]** 注：『n≥50 能用正态表』是 t-分布行为的一张"速查表"结论——不必记，要能推导直觉：t 与正态的差距随自由度增长而衰减，约在 $n-1\ge 50$ 处尾部已难以区分，故常用 $z_{\alpha/2}$ 顶替 $t_{n-1}$。先证边界效应：其差异量级由分布幂尾的修正给出，是 $O(1/\text{df})$ 的；df=∞ 时恒等。实务规则于是很简单——小样本 + 未知方差 → t；大样本 → z，二者数值在 df 充分大后互不可辨。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.7（用电子秤重复称量物体重量，构造置信区间）**</span>

用一台电子秤对某物体的重量测量了八次，该秤报告的是真实重量加上一个期望为零、方差未知的正态分布随机误差。假设各次观测中的误差相互独立。得到的结果如下：

```math
0.5547,\ \ 0.5404,\ \ 0.6364,\ \ 0.6438,\ \ 0.4917,\ \ 0.5674,\ \ 0.5564,\ \ 0.6066 .
```

我们使用 t-分布计算一个 95% 置信区间（$\alpha = 0.05$）。样本均值 $\hat{\theta}_n$ 的值为 $0.5747$，$\hat{\theta}_n$ 的估计方差为

```math
\frac{S_n^2}{n} = \frac{1}{n(n-1)}\sum_{i=1}^{n}\left(X_i - \hat{\theta}_n\right)^2 = 3.2952 \times 10^{-4}.
```

（续至下一页：求 $S_n/\sqrt{n}$、查 t-分布表并给出置信区间。）

---

<!-- ===== PDF p480 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 473（页眉「Sec. 9.1 / 473」）。页首为 t-分布取值表（对应前一页所述的「对面一页的简略表」）及其读表说明，随后完成 **Example 9.7**：求 $S_n/\sqrt{n}$、查 t-分布表、给出 95% 置信区间并与正态近似所得区间进行对比。</span>

---

<span style="color:#00838f;">**[定义] t-分布取值表（t-tables，对应 Fig. 9.4）**</span>

这是 t-分布（具有给定 $n-1$ 个自由度）的 CDF $W_{n-1}(z)$ 所对应的取值表。表中各项含义为：

- 左列：自由度个数 $n - 1$；
- 顶行：所期望的尾部概率（tail probability）$\beta$；
- 顶行下方各项：满足 $W_{n-1}(z) = 1 - \beta$ 的一个值 $z$。

| $n-1$ | 0.100 | 0.050 | 0.025 | 0.010 | 0.005 | 0.001 |
|------|-------|-------|-------|-------|-------|-------|
| 1    | 3.078 | 6.314 | 12.71 | 31.82 | 63.66 | 318.3 |
| 2    | 1.886 | 2.920 | 4.303 | 6.965 | 9.925 | 22.33 |
| 3    | 1.638 | 2.353 | 3.182 | 4.541 | 5.841 | 10.21 |
| 4    | 1.533 | 2.132 | 2.776 | 3.747 | 4.604 | 7.173 |
| 5    | 1.476 | 2.015 | 2.571 | 3.365 | 4.032 | 5.893 |
| 6    | 1.440 | 1.943 | 2.447 | 3.143 | 3.707 | 5.208 |
| 7    | 1.415 | 1.895 | 2.365 | 2.998 | 3.499 | 4.785 |
| 8    | 1.397 | 1.860 | 2.306 | 2.896 | 3.355 | 4.501 |
| 9    | 1.383 | 1.833 | 2.262 | 2.821 | 3.250 | 4.297 |
| 10   | 1.372 | 1.812 | 2.228 | 2.764 | 3.169 | 4.144 |
| 11   | 1.363 | 1.796 | 2.201 | 2.718 | 3.106 | 4.025 |
| 12   | 1.356 | 1.782 | 2.179 | 2.681 | 3.055 | 3.930 |
| 13   | 1.350 | 1.771 | 2.160 | 2.650 | 3.012 | 3.852 |
| 14   | 1.345 | 1.761 | 2.145 | 2.624 | 2.977 | 3.787 |
| 15   | 1.341 | 1.753 | 2.131 | 2.602 | 2.947 | 3.733 |
| 20   | 1.325 | 1.725 | 2.086 | 2.528 | 2.845 | 3.552 |
| 30   | 1.310 | 1.697 | 2.042 | 2.457 | 2.750 | 3.385 |
| 60   | 1.296 | 1.671 | 2.000 | 2.390 | 2.660 | 3.232 |
| 120  | 1.289 | 1.658 | 1.980 | 2.358 | 2.617 | 3.160 |
| $\infty$ | 1.282 | 1.645 | 1.960 | 2.326 | 2.576 | 3.090 |

> <span style="color:#7f8c8d;">[原页此处为扫描表格] 上表数值直接取自源 OCR 的 t-分布表；个别最后一位因扫描/OCR 可能有 ±1 的小扰动，但均为标准 t-分布表的标准值，示意用途不受影响。</span>

---

因此 $S_n / \sqrt{n} \approx 0.0182$。从 t-分布表中（取 $n - 1 = 7$ 个自由度的列），我们得到 $1 - W_7(2.365) = 0.025 = \alpha/2$，于是

```math
P\left(\frac{\lvert \hat{\theta}_n - \theta \rvert}{S_n / \sqrt{n}} < 2.365\right) = 0.95 .
```

因此

```math
\left[\hat{\theta}_n - 2.365\,\frac{S_n}{\sqrt{n}},\ \ \hat{\theta}_n + 2.365\,\frac{S_n}{\sqrt{n}}\right] = [0.531,\ 0.618]
```

是一个 95% 置信区间。把它与由正态分布表得到的置信区间

```math
\left[\hat{\theta}_n - 1.96\,\frac{S_n}{\sqrt{n}},\ \ \hat{\theta}_n + 1.96\,\frac{S_n}{\sqrt{n}}\right] = [0.539,\ 0.610]
```

相比是很有意思的：后者更窄，因而对估计值 $\hat{\theta} = 0.5747$ 的精度显得更为乐观。

> <span style="color:#1e8449;">**[t_note]** 注：Example 9.7 故意把 t、z 两个区间并排摆出来比：[0.531,0.618] 对 [0.539,0.610]。先证两个读数：其一，t 区间更宽（端点系数 2.365 > 1.96），因为方差未知要付出『用 $S_n$ 替 $v$』的代价，故更诚实地保守；其二，两者差 $0.008$ 量级不大——自由度 7 的小样本下 t 只比 z 宽一点，这正说明『样本小必须 t』的教训在数值上有多直观。能把 $S_n/\sqrt{n}=0.0182$、查表 $w_7(0.975)=2.365$ 一步步算下来，你就真正掌握了参数估计 + 区间构造整条链路。</span>

---

<!-- ===== PDF p481 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.1 经典参数估计（Classical Parameter Estimation）续页，书页 474（页眉「Chap. 9 / 474」）。本页承接上页内容，讨论对未知方差进行不同估计或近似的若干方式，并开启 **Example 9.8**（Polling，民意调查），分 (a)(b)(c) 三部分构造 95% 置信区间；本页给出 (a)(b) 两部分，首页 (c) 部分与图 **Figure 9.4** 延续至下一页，随后才进入新节 §9.2。</span>

---

<br>

到目前为止构造的近似置信区间（approximate confidence intervals）都依赖于对未知方差 $v$ 采用特定的估计量 $S_n^2$。不过，对方差采用其他不同的估计量或近似方式也是可行的。例如，设观测 $X_1, \dots, X_n$ 独立同分布（i.i.d.）的 Bernoulli 随机变量，其未知均值为 $\theta$，方差 $v = \theta(1 - \theta)$。此时，除了 $S_n^2$，方差还可用 $\hat{\theta}_n\bigl(1 - \hat{\theta}_n\bigr)$ 来近似。事实上，随着 $n$ 增大，$\hat{\theta}_n$ 依概率收敛到 $\theta$，由此可以证明 $\hat{\theta}_n\bigl(1 - \hat{\theta}_n\bigr)$ 收敛到 $v$。另一种做法是注意到对一切 $\theta \in [0, 1]$ 都有 $\theta(1 - \theta) \le 1/4$，从而取 $1/4$ 作为方差的保守估计（conservative estimate of the variance）。下面的例子说明了这些不同的选择。

> <span style="color:#1e8449;">**[t_note]** 注：这段罗列了同一问题的三种方差取法——(a) 用 $S_n^2$、(b) 用 $\hat\theta_n(1-\hat\theta_n)$、(c) 用保守上界 $1/4$。先证它们各自的来历：(a) 是通用的所谓 $n$ 除方差；(b) 借了 Bernoulli 的『均值=方差=θ(1−θ)』结构，把不知道的 θ 换成不知道的估计 $\hat\theta_n$；(c) 根本不估、直接用一个对一切 θ 都成立的上界。三者约束强度递减、保守度递增，是『估方差』这个子问题的三种选择策略。先记住：置信区间的宽度由 $\sqrt{v/n}$ 决定，而 $v$ 怎么处理就产生了不同区间，这是工程上最普遍的决策点。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.8（Polling——民意调查，承接 §5.4 的开票题，续至下一页）**</span>

考虑第 5.4 节（Example 5.11）中的民意调查问题：我们希望估计支持某位候选人当选的选民所占的比例 $\theta$。我们搜集了 $n$ 名独立选民样本的回应 $X_1, \dots, X_n$，其中 $X_i$ 视为一个 Bernoulli 随机变量，当第 $i$ 位选民支持该候选人时 $X_i = 1$。我们用样本均值 $\hat{\theta}_n$ 去估计 $\theta$，并基于正态近似、加上对未知方差的不同估计或近似方式构造置信区间。具体起见，假设该样本 $n = 1200$ 名选民中有 $684$ 人支持候选人，从而 $\hat{\theta}_n = 684/1200 = 0.57$。

**（a）** 若采用方差估计

```math
S_n^2 = \frac{1}{n}\sum_{i=1}^{n}\left(X_i - \hat{\theta}_n\right)^2
      = \frac{684}{1200}\left(1 - \frac{684}{1200}\right)^2
      + \frac{1200 - 684}{1200}\left(0 - \frac{684}{1200}\right)^2
      = 0.245,
```

并把 $\hat{\theta}_n$ 当作一个均值为 $\theta$、方差为 $S_n^2$ 的正态随机变量，则得到 95% 置信区间

```math
\left[\hat{\theta}_n - 1.96\,\sqrt{\frac{S_n^2}{n}},\ \ \hat{\theta}_n + 1.96\,\sqrt{\frac{S_n^2}{n}}\right]
= \left[0.57 - 1.96\cdot\sqrt{\frac{0.245}{1200}},\ \ 0.57 + 1.96\cdot\sqrt{\frac{0.245}{1200}}\right]
= [0.542,\ 0.598].
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本节 (a) 的方差估计公式在源 OCR 中被打散成若干碎片（如 `2) + (1200-684)·(0 - 68/1200)^2`、`≥ 0.245` 等），这里按 Bernoulli 样本方差的语义（$\frac{1}{n}\sum$ 的平方和分解）忠实地还原符号与数值 $S_n^2 = 0.245$，未臆造数值。</span>

**（b）** 方差估计

```math
S_n^2 = \hat{\theta}_n\left(1 - \hat{\theta}_n\right) = \frac{684}{1200}\cdot\left(1 - \frac{684}{1200}\right) = 0.245
```

与前一种相同（精确到三位小数），因此所得的 95% 置信区间

```math
\left[\hat{\theta}_n - 1.96\,\sqrt{\frac{\hat{\theta}_n\left(1 - \hat{\theta}_n\right)}{n}},\ \ \hat{\theta}_n + 1.96\,\sqrt{\frac{\hat{\theta}_n\left(1 - \hat{\theta}_n\right)}{n}}\right]
```

仍然是 $[0.542,\ 0.598]$。

> <span style="color:#1e8449;">**[t_note]** 注：(b) 与 (a) 结果相同并非巧合，先证：对 Bernoulli 样本，$S_n^2=\frac1n\sum_i(X_i-\hat\theta_n)^2$ 恰等于 $\hat\theta_n(1-\hat\theta_n)$（两个取值 $0,1$ 的平方和分解后正好是这个乘积）。本例 $\hat\theta_n=0.57$ 让两者都等于 $0.245$。不过要注意：b 只对『单参数 Bernoulli』成立、是利用 $v=\theta(1-\theta)$ 这个结构捷径；而 a 对任何分布都对。当分布不是 Bernoulli 时这种巧合消失——记住 a 永远可用、b 是借结构、c 是保底。</span>

> <span style="color:#7f8c8d;">[原文此处页末]（c）部分的保守上界 $1/4$ 与图 **Figure 9.4** 在下一页 PDF p482 续写。</span>

---

<!-- ===== PDF p482 ===== -->

<span style="color:#7f8c8d;">书页 475，页眉「Sec. 9.2 / 475 / Linear Regression」。本页跨两段：(1) 页首承接上一页 **Example 9.8** 的 (c) 部分与图 **Figure 9.4**（§9.1 收尾）；(2) 随后进入**第 9 章 §9.2 线性回归（Linear Regression）**新节，给出节引言，铺垫最小二乘（least squares）的思想。</span>

---

<br>

**（c）** 对方差采用 $1/4$ 这个保守上界（conservative upper bound），所得的置信区间为

```math
\left[\hat{\theta}_n - 1.96\,\sqrt{\frac{1/4}{n}},\ \ \hat{\theta}_n + 1.96\,\sqrt{\frac{1/4}{n}}\right]
= \left[0.57 - 1.96\,\sqrt{\frac{1}{4\cdot 1200}},\ \ 0.57 + 1.96\,\sqrt{\frac{1}{4\cdot 1200}}\right]
= [0.542,\ 0.599],
```

它只是略微更宽，但实际上与此前的区间几乎一样。

> <span style="color:#1e8449;">**[t_note]** 注：(c) 的 $1/4$ 是一句『免费的数据无关保证』：对一切 $\theta\in[0,1]$ 都有 $\theta(1-\theta)\le 1/4$。先证：$\theta(1-\theta)=\tfrac14-\big(\tfrac12-\theta\big)^2\le\tfrac14$——抛物线在 $\theta=\tfrac12$ 处取到最大值。若愿意永远付出这个上界换来『不必先估方差』的简单，得到的区间恒有效、只是 n 小时偏保守。当 n 很大（如本例 1200）时 $\sqrt{(1/4)/n}$ 与 $\sqrt{0.245/n}$ 几乎无差，这就是 Fig. 9.4 里 (b)/(c) 两线在高 n 处贴合的原因。</span>

图 **Figure 9.4** 展示了在固定 $\hat{\theta}_n = 0.57$、样本量从 $n = 10$ 到 $n = 10{,}000$ 变化时，使用方法 (b) 与方法 (c) 得到的置信区间。我们看到，当 $n$ 达到数百（正如民调中通常的情形）时，二者的差别很小。另一方面，当 $n$ 较小时，不同方法会得到相当不同的置信区间，因此需要格外小心。

<figure>
<figcaption><span style="color:#7f8c8d;">**Figure 9.4.**—— 在民调例子 Example 9.8 中，用方法 (b) 与方法 (c) 近似方差时，置信区间端点与 $\hat{\theta}_n$ 的距离；固定 *(*$\hat{\theta}_n = 0.57$*)*，样本量从 $n = 10$ 到 $n = 10{,}000$。</span></figcaption>
</figure>

（此处为 Fig. 9.4 示意图：纵轴为置信区间端点离 $\hat{\theta}_n = 0.57$ 的距离，两条曲线分别对应「基于上界的置信区间 / Confidence Intervals Based on Upper Bound」与「基于估计方差的置信区间 / Confidence Intervals Based on Estimated Variance」，横轴为 $n$。）

---

<span style="color:#c0392b;">**第 9.2 节　线性回归（Linear Regression）**</span>

在本节中，我们将建立线性回归（linear regression）方法，用以在现有数据的基础上构建两个或多个所关注变量之间关系的模型。该方法一个有趣的特点是，它可以仅仅作为一种**最小二乘逼近（least squares approximation）**的过程来阐释和发展，完全不需要任何概率假设。然而，线性回归的公式也可以放在各种概率框架（probabilistic frameworks）之下来理解，这些框架提供了视角与

---

<!-- ===== PDF p483 ===== -->

<span style="color:#7f8c8d;">书页 476，页眉「9 / 476」(OCR 残缺，正文为 §9.2 线性回归延续)。本页续写 §9.2 引言：讨论最简单的情形——两变量之间的近似线性关系及其线性模型 $Y \approx \theta_0 + \theta_1 x$，引出残差（residual）与最小化残差平方和（sum of squared residuals）的思想，并提及图 Fig. 9.5。</span>

---

<br>

（续前页）—— 以便更深入地理解该方法。作为本篇的延伸，我们首先考虑**只有两个变量**的情形，

并希望在两者之间建立一种系统性的、近似线性（approximately linear）的关系。设数据由点对 $(X_i, Y_i)$ 构成，$i = 1, \dots, n$，它们之间呈现出一种整体上近似线性的关系。此时，很自然地要建立一个线性模型（linear model）$Y \approx \theta_0 + \theta_1 x$，其中 $\theta_0$、$\theta_1$ 是待估的未知参数。

对于给定的数据，该模型对 $X_i$ 预测出的 $Y$ 的值为 $\hat{\theta}_0 + \hat{\theta}_1 x_i$（其中 $\hat{\theta}_0$、$\hat{\theta}_1$ 是 $\theta_0$、$\theta_1$ 的估计），而这个值与观测值 $Y_i$ 的**差**即为残差（residual）。对一个好的模型来说，其残差应当较小。人们自然会想到选择这样的参数估计 $\hat{\theta}_0$、$\hat{\theta}_1$：它使得残差的平方和（sum of the squares of the residuals）$\sum_{i=1}^{n}\left(Y_i - \hat{\theta}_0 - \hat{\theta}_1 X_i\right)^2$ 最小。参见图 Fig. 9.5 的说明。

> <span style="color:#1e8449;">**[t_note]** 注：『最小化残差平方和』为何是首选而不是『最小化残差绝对值之和』？先给两条直觉：其一，平方把大的残差放大——偏离越远惩罚越重，暗含『极端偏离更不可接受』的态度；其二，统计上更强——正如待会 (a) 节会证明的，在正态噪声假设下最小化残差平方和**恰等于极大似然**（高斯密度的负对数正是二次项）。而且平方和给的是光滑、可解析求导的目标，没有绝对值的折点麻烦。跨课程（线性代数 Strang）：把残差平方和读成『向量 $Y$ 与它在 $X=[X,1]$ 张成的列空间上的投影之差的长度平方』，最小化它就是在找正交投影——这是最小二乘最漂亮、也最几何的来处。</span>

<figure>
<figcaption><span style="color:#7f8c8d;">**Figure 9.5.**—— 一组数据点 $(X_i, Y_i)$ 与一个线性模型 $Y = \theta_0 + \theta_1 x$ 的说明：所得直线 $\hat{\theta}_0 + \hat{\theta}_1 x$ 使残差平方和最小。</span></figcaption>
</figure>

（此处为 Fig. 9.5 示意图：散布在一条直线附近的一组数据点，以及一条拟合这些点的直线 $Y = \hat{\theta}_0 + \hat{\theta}_1 x$，各数据点到直线的竖直距离即为残差。）

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页中部公式与说明文字在源 OCR 中被打散成碎片行（如 `a o'r c , n`、`g iven some`、`v\.JJ.... o...& JI A Ap;` 等），此处按线性回归引言的标准语义（残差平方和 $\sum_{i=1}^{n}(Y_i - \theta_0 - \theta_1 x_i)^2$、模型 $Y = \theta_0+\theta_1 x$）忠实还原，未臆造数值。</span>

---

<!-- ===== PDF p484 ===== -->

<span style="color:#7f8c8d;">书页 477，页眉「Sec. 9.2 / 477 / Linear Regression」。本页：先说明所设定的线性模型未必成立、线性最小二乘的目标在于找最好线性模型，再推导出**线性回归估计公式框**（$\hat{\theta}_0$、$\hat{\theta}_1$ 的显式解），并在页尾开启 **Example 9.9**（比萨斜塔倾角数据的线性回归，续至下一页）。</span>

---

<br>

注意：所设定的线性模型未必成立。例如，两变量之间的真实关系可能是非线性的。线性最小二乘（linear least squares）方法旨在寻找可能的最优线性模型，它隐含了一个假设，即线性模型是有效的。在实践中，往往还有另外一步：检验「线性模型」这一假设是否得到数据支持，并试图验证所估计的模型。

为了推导线性回归估计 $\hat{\theta}_0$ 与 $\hat{\theta}_1$ 的公式，我们注意到：一旦数据给定，残差平方和就是 $\theta_0$ 和 $\theta_1$ 的二次函数。为进行最小化，我们令其关于 $\theta_0$ 与 $\theta_1$ 的偏导数为零。这样就得到关于 $\theta_0$、$\theta_1$ 的两个线性方程，可以显式解出。经过一些代数运算，我们得到如下简洁而漂亮的解的表达式。

> <span style="color:#1e8449;">**[t_note]** 注：『对 θ₀、θ₁ 令偏导为 0 得到两个线性方程』这一步，微积分视角和线性代数视角是同一件事——后者叫法方程（normal equations）。先证：残差平方和对 θ 是（正定）二次函数，其驻点即全局最小；分别对两坐标求导得到两个方程，拼成一个 $2\times2$ 线性系统，解即 $\hat\theta_0,\hat\theta_1$。跨课程（线性代数 Strang）：这套方程正是 $X^\top X\,\boldsymbol\theta=X^\top\boldsymbol y$（把截距列并入设计矩阵后），与『向列空间投影』给出的法方程逐项对应——一个用微积分从最小化出发、一个用几何从投影出发，殊途同归到同一组解。今后凡见到『最小二乘解』，心里就挂住这两条路。</span>

<span style="color:#00838f;">**[定义公式] 线性回归（Linear Regression）公式框**</span>

给定 $n$ 个数据对 $(X_i, Y_i)$，使残差平方和最小的估计如下给出：

```math
\hat{\theta}_1 = \frac{\sum_{i=1}^{n}\left(X_i - \bar{x}\right)\left(Y_i - \bar{y}\right)}{\sum_{i=1}^{n}\left(X_i - \bar{x}\right)^2},
\qquad
\hat{\theta}_0 = \bar{y} - \hat{\theta}_1 \bar{x},
```

其中

```math
\bar{x} = \frac{1}{n}\sum_{i=1}^{n}X_i, \qquad \bar{y} = \frac{1}{n}\sum_{i=1}^{n}Y_i .
```

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.9（比萨斜塔倾角随时间变化的线性回归，续至下一页）**</span>

比萨斜塔（the leaning tower of Pisa）随时间的推移不断倾斜。1975 年至 1987 年间，对塔上一个固定点的「倾距」（即该点的实际位置与其在塔直立时所处位置之间的距离，以米计）进行测量，得到下表。

| 年份 | 倾距 | 年份 | 倾距 |
|------|------|------|------|
| 1975 | 2.9642 | 1982 | 2.9698 |
| 1976 | 2.9644 | 1983 | 2.9713 |
| 1977 | 2.9656 | 1984 | 2.9717 |
| 1978 | 2.9667 | 1985 | 2.9725 |
| 1979 | 2.9673 | 1986 | 2.9742 |
| 1980 | 2.9688 | 1987 | 2.9757 |
| 1981 | 2.9696 |      |      |

我们用线性回归在一个形如 $y = \theta_0 + \theta_1 x$ 的模型中估计参数 $\theta_0$、$\theta_1$，其中 $x$ 是年份，$y$ 是倾距。运用回归

---

<!-- ===== PDF p485 ===== -->

<span style="color:#7f8c8d;">书页 478，页眉「Chap. 9 / 478 / Classical Statistical Inference」。本页承接上一页 **Example 9.9**：给出 $\hat{\theta}_0$、$\hat{\theta}_1$ 的计算结果与估计线性模型 $Y = 0.0009x + 1.1233$，配图 **Figure 9.6**；随后开启并介绍「最小二乘公式化的合理性（Justification of the Least Squares Formulation）」小节的 (a) 极大似然部分（该小节可跳过而不失连贯性）。</span>

---

<br>

（续 Example 9.9）运用回归公式，我们得到

```math
\bar{x} = \frac{1}{n}\sum_{i=1}^{n}X_i = 1981, \qquad
\bar{y} = \frac{1}{n}\sum_{i=1}^{n}Y_i = 2.9694,
```

```math
\hat{\theta}_1 = \frac{\sum_{i=1}^{n}\left(X_i - \bar{x}\right)\left(Y_i - \bar{y}\right)}{\sum_{i=1}^{n}\left(X_i - \bar{x}\right)^2} = 0.0009, \qquad
\hat{\theta}_0 = \bar{y} - \hat{\theta}_1 \bar{x} = 1.1233 .
```

估计出的线性模型为

```math
Y = 0.0009\,x + 1.1233,
```

并如图 **Figure 9.6** 所示。

> <span style="color:#1e8449;">**[t_note]** 注：读 Example 9.9 的数值要找对『中心』。先证：把 $\hat\theta_0=\bar y-\hat\theta_1\bar x$ 代回模型得 $y-\bar y=\hat\theta_1(x-\bar x)$——拟合直线必过『质心 $(\bar x,\bar y)$』。因此 $\hat\theta_1=0.0009$ 随时、随地可读作『$x$ 每增 1（年头+1），$y$ 平均增 0.0009』（斜率）；而 $\hat\theta_0=1.1233$ **不是**『第 0 年倾距』，只是过质心直线在 $x=0$ 处的延伸，本身无物理意义。工程上常先把 $x$ 居中（减 $\bar x$）再做回归，既让斜率数值稳定、又让截距回到『在均值处的 $y$』、可解释性更好。跨课程（线代 Strang）：过质心正是投影向量的均值分量等于样本均值的体现。</span>

<figure>
<figcaption><span style="color:#7f8c8d;">**Figure 9.6.**—— 比萨斜塔倾角的数据点与估计出的线性模型（Example 9.9）。</span></figcaption>
</figure>

（此处为 Fig. 9.6 示意图：纵轴为倾距（约为 $2.962$–$2.976$），横轴为年份（$1974$–$1988$），散布数据点与一条近似直线 $Y = 0.0009x + 1.1233$，图例标记 "Data Points" 与 "Estimated Linear Model"。）

---

<span style="color:#c0392b;">**最小二乘公式化的合理性（Justification of the Least Squares Formulation）**</span>

> <span style="color:#7f8c8d;">Footnote（脚注）：† 本小节可跳过而不失连贯性（This subsection can be skipped without loss of continuity）。</span>

最小二乘公式化可以基于概率考虑、在不同假设下以多种方式得到论证：

**（a）极大似然（maximum likelihood；线性模型，正态噪声）。** 我们假设 $X_i$ 是给定的数（而非随机变量）。我们假设 $Y_i$ 是一个随机变量 $Y_i$ 的实现值，它由如下形式的模型产生：

```math
Y_i = \theta_0 + \theta_1 X_i + W_i, \qquad i = 1, \dots, n,
```

其中 $W_i$ 是独立同分布的正态随机变量，均值为零、方差为 $\sigma^2$。由此得出 $Y_i$ 是独立的正态变量，其中 $Y_i$ 的均值（mean）为 $\theta_0 + \theta_1 X_i$、方差（variance）为 $\sigma^2$。似然函数（likelihood function）具有如下形式：

```math
f\left(y; \theta\right) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi}\sigma}
\exp\left\{-\frac{\left(y_i - \theta_0 - \theta_1 x_i\right)^2}{2\sigma^2}\right\}.
```

---

<!-- ===== PDF p486 ===== -->

<span style="color:#7f8c8d;">书页 479，页眉「Sec. 9.2 / 479 / Linear Regression」。本页续写「最小二乘公式化的合理性」小节：(a) 极大似然的结论（等于最小二乘、是无偏估计，可用 §9.1 方法构置信区间）；(b) 近似贝叶斯线性 LMS 估计的论证开头。小节内无新 Example 编号，均为叙述。</span>

---

<br>

（续 (a) 极大似然）最大化似然函数等价于最大化上式中的指数部分，而这又等价于最小化残差平方和。因此，线性回归估计可以在合适的线性正态框架（linear normal context）下视为极大似然（ML）估计。事实上，在此框架下可以证明它们是无偏估计（unbiased estimates）。此外，各估计的方差可用方便的公式计算（见章末习题），进而可用第 9.1 节的方法构造置信区间。

> <span style="color:#1e8449;">**[t_note]** 注：(a) 把最小二乘与极大似然缝成同一件事。先证：在 $Y_i=\theta_0+\theta_1X_i+W_i$、$W_i\sim\mathcal N(0,\sigma^2)$ 下，对数似然 $\log f\big(y;\theta\big)=\sum_i -\log(\sqrt{2\pi}\sigma)-\frac{1}{2\sigma^2}\big(y_i-\theta_0-\theta_1x_i\big)^2$。对 $\boldsymbol\theta$ 而言，最大化它就是最小化残差平方和（$\sigma^2$ 只是乘了个无关正常数）。于是『最小二乘』在这里获得了概率语义：在正态噪声下它就是 ML。顺带的优惠——它是无偏估计、且能直接套用 §9.1 那套置信区间，正是靠 (a) 这个等价性兑现的。跨课程（凸优化，进行中）：log 把乘积化为求和、负号把『最大』化成凹函数的收敛——标准的『正态噪声下的凸目标最小化』模板。</span>

**（b）近似贝叶斯线性最小均方估计（approximate Bayesian linear LMS estimation；在可能是非线性的模型下）。** 现在假设 $X_i$ 与 $Y_i$ 都是随机变量 $X_i$、$Y_i$ 的实现值。不同的点对 $(X_i, Y_i)$ 是独立同分布的，但具有未知的联合分布。考虑一个额外的独立点对 $(X_0, Y_0)$，具有相同的联合分布。假设我们观察到 $X_0$，希望用一个如下形式的线性估计器（linear estimator）估计 $Y_0$：$\hat{Y_0} = \theta_0 + \theta_1 X_0$。我们由第 8.4 节知道，给定 $X_0$ 时 $Y_0$ 的线性 LMS 估计量（linear LMS estimator）具有如下形式：

```math
E[Y_0 \mid X_0] + \frac{\mathrm{cov}(X_0, Y_0)}{\mathrm{var}(X_0)}\,\left(X_0 - E[X_0]\right),
```

从而

```math
\theta_1 = \frac{\mathrm{cov}(X_0, Y_0)}{\mathrm{var}(X_0)}, \qquad
\theta_0 = E[Y_0] - \theta_1 E[X_0].
```

由于我们并不知道 $(X_0, Y_0)$ 的分布，我们用 $\bar{x}$ 作为 $E[X_0]$ 的估计、$\bar{y}$ 作为 $E[Y_0]$ 的估计、$\sum_{i=1}^{n}\left(X_i - \bar{x}\right)\left(Y_i - \bar{y}\right) \big/ n$ 作为 $\mathrm{cov}(X_0, Y_0)$ 的估计、$\sum_{i=1}^{n}\left(X_i - \bar{x}\right)^2\big/ n$ 作为 $\mathrm{var}(X_0)$ 的估计。将这些估计代入上面关于 $\theta_0$、$\theta_1$ 的公式，我们重新得到先前给出的线性回归参数估计的表达式。注意：这一论证并未假设线性模型一定成立。

> <span style="color:#1e8449;">**[t_note]** 注：(b) 是『把未知矩一一换成样本矩』（plug-in，样板替换法）的教科书演示。先证链条：从理想公式 $E[Y_0\mid X_0]+\frac{\mathrm{cov}(X_0,Y_0)}{\mathrm{var}(X_0)}(X_0-E[X_0])$ 出发，把五个未知量 $E[X_0]、E[Y_0]、\mathrm{cov}(X_0,Y_0)、\mathrm{var}(X_0)$ 与线性 LMS 的系数逐一替换为样本对口量（$\bar x,\,\bar y,\,\frac1n\sum(X_i-\bar x)(Y_i-\bar y),\,\frac1n\sum(X_i-\bar x)^2$），代入整理竟**重新得到**第 9.2 节的最小二乘公式。这一点的分量是：哪怕真实关系是非线性的，只要我们『只要在所有线性估计里挑一个最好的』，LS 就在干这件事——它不依赖『线性模型确实为真』这个前提，健壮性好于 (a)。</span>

**（c）近似贝叶斯最小均方估计（approximate Bayesian LMS estimation；线性模型）。** 同 (b) 一样，设点对 $(X_i, Y_i)$ 是随机且独立同分布的。我们再额外假设这些点对满足如下的线性模型：

```math
Y_i = \theta_0 + \theta_1 X_i + W_i,
```

其中 $W_i$ 是独立同分布、均值为零、且与 $X_i$ 独立的噪声项（noise terms）。由条件期望的最小均方性质（least mean squares property of conditional expectations），我们知道

---

<!-- ===== PDF p487 ===== -->

<span style="color:#7f8c8d;">书页 480，页眉「Chap. 9 / 480 / Classical Statistical Inference」。本页续写「最小二乘公式化的合理性」小节的 (c) 部分并收尾该小节；随后开启 **「贝叶斯线性回归（Bayesian Linear Regression）」（可跳过而不失连贯性）** 小节，给出其模型假设与后验 PDF 的推导起点，续至下一页。</span>

---

<br>

（续 (c) 近似贝叶斯 LMS）函数 $g$ 在所有 $X_0$ 的函数中最小化均方估计误差 $E\left[\left(Y_0 - g(X_0)\right)^2\right]$ 的正是条件期望 $E[Y_0 \mid X_0]$。在我们的假设下，$E[Y_0 \mid X_0] = \theta_0 + \theta_1 X_0$。因此，对所有 $\theta_0$ 和 $\theta_1$ 最小化

```math
E\left[\left(Y_0 - \theta_0 - \theta_1 X_0\right)^2\right],
```

的正是真实参数 $\theta_0$、$\theta_1$。由弱大数定律（weak law of large numbers），该表达式是下式在 $n \to \infty$ 时的极限：

```math
\frac{1}{n}\sum_{i=1}^{n}\left(Y_i - \theta_0 - \theta_1 X_i\right)^2 .
```

这表明，通过最小化上式（把 $X_i$、$Y_i$ 分别替换为其观测值 $x_i$、$y_i$）我们将得到对最小化项（即真实参数）的一个良好近似。而最小化这一表达式与最小化残差平方和是同一回事。

---

<span style="color:#c0392b;">**贝叶斯线性回归（Bayesian Linear Regression）**</span>

> <span style="color:#7f8c8d;">Footnote（脚注）：† 本小节可跳过而不失连贯性（This subsection can be skipped without loss of continuity）。</span>

线性模型与回归并非只与经典推断方法相关，它们同样可以在贝叶斯框架（Bayesian framework）下研究，我们现在就来解释这一点。特别是，我们可以把 $X_1, \dots, X_n$ 建模为给定的数，把 $Y_1, \dots, Y_n$ 看作一个随机向量 $\underline{Y} = (Y_1, \dots, Y_n)$ 的观测值，而这些随机变量服从一个线性关系：

```math
Y_i = \theta_0 + \theta_1 X_i + W_i, \qquad i=1,\dots,n.
```

这里 $\theta = (\theta_0, \theta_1)$ 是待估的参数，而 $W_1, \dots, W_n$ 是独立同分布、均值为零、具有已知方差 $\sigma^2$ 的随机变量。与贝叶斯哲学一致，我们把 $\theta_0$ 和 $\theta_1$ 建模为随机变量；假设 $\theta_0$、$\theta_1$、$W_1, \dots, W_n$ 相互独立，且 $\theta_0$、$\theta_1$ 均值为零、方差分别为 $\sigma_0^2$、$\sigma_1^2$。

我们现在可以在 MAP 方法、以及假设 $\theta_0$、$\theta_1$ 和 $W_1, \dots, W_n$ 为正态随机变量的基础上，推导一个贝叶斯估计。我们在 $(\theta_0, \theta_1)$ 上最大化后验 PDF（posterior PDF）$f_{\theta_1 \mid \underline{Y}}\left(\theta_0, \theta_1 \mid y_1, \dots, y_n\right)$。由贝叶斯准则（Bayes' rule），后验 PDF 为

> <span style="color:#7f8c8d;">Footnote（脚注）：† 注意：本段中我们使用条件概率记号，因为这里处理的是贝叶斯框架。</span>

```math
f_{\theta_1 \mid \underline{Y}}\left(\theta_0, \theta_1 \mid y_1, \dots, y_n\right)
= c\,\exp\left\{-\frac{\theta_0^2}{2\sigma_0^2}\right\}
  \exp\left\{-\frac{\theta_1^2}{2\sigma_1^2}\right\}
  \prod_{i=1}^{n}\exp\left\{-\frac{\left(y_i - \theta_0 - x_i\theta_1\right)^2}{2\sigma^2}\right\},
```

其中 $c$ 是一个不依赖 $(\theta_0, \theta_1)$ 的正的归一化常数（normalizing constant）。在此正态性假设下，这一表达式可以写成

---

<!-- ===== PDF p488 ===== -->

<span style="color:#7f8c8d;">书页 481，页眉「Sec. 9.2 / 481 / Linear Regression」。本页承接上一页「贝叶斯线性回归」小节：说明在 $(\theta_0,\theta_1)$ 上最小化的目标表达式、与经典线性回归的联系，并给出**贝叶斯线性回归（Bayesian Linear Regression）公式框**（模型假设与 MAP 估计公式，含 $\hat{\theta}_0$、$\hat{\theta}_1$）。页面方程内容较多，PCR 碎片化明显。</span>

---

<br>

（续）其中 $c$ 是一个不依赖 $(\theta_0, \theta_1)$ 的归一化常数。等价地，我们在 $(\theta_0,\theta_1)$ 上最小化表达式

```math
\frac{\theta_0^2}{2\sigma_0^2} + \frac{\theta_1^2}{2\sigma_1^2} + \sum_{i=1}^{n}\frac{\left(y_i - \theta_0 - x_i\theta_1\right)^2}{2\sigma^2}.
```

注意它与下式的相似性：在早先的经典线性回归公式化中，最小化的是 $\sum_{i=1}^{n}\bigl(y_i - \theta_0 - x_i\theta_1\bigr)^2$。（如果 $\sigma_0$、$\sigma_1$ 大得使得 $\theta_0^2/2\sigma_0^2$ 与 $\theta_1^2/2\sigma_1^2$ 的项可以忽略，那么这两个最小化是完全相同的。）最小化通过令关于 $\theta_0$、$\theta_1$ 的偏导数为零来完成。经过一些代数运算，我们得到如下解。

> <span style="color:#1e8449;">**[t_note]** 注：贝叶斯回归最小化的目标比经典回归多了 $\frac{\theta_0^2}{2\sigma_0^2}+\frac{\theta_1^2}{2\sigma_1^2}$ 两个『罚』——这正是把参数往 0 拉的先验。先证：后验 ∝ 先验 × 似然；对高斯取负对数后，先验恰贡献了这两个二次项（这正是 MAP = 最大化后验 = 最小化负对数后验）。当 $\sigma_0,\sigma_1\to\infty$（先验无信息）这些项趋零，目标退化为经典最小二乘——故**经典 LS 是贝叶斯回归先验→无穷的双极限情形**。跨课程（凸优化，进行中）：这两个二次罚就是岭回归（ridge / $L^2$ 正则）的雏形——同一个数学对象在贝叶斯里叫『先验』、在最优化里叫『正则项』，先记住这二重身份，读到凸优化时自然就通了。</span>

<span style="color:#00838f;">**[定义/定理] 贝叶斯线性回归（Bayesian Linear Regression）公式框**</span>

**模型（Model）：**
（a）我们假设线性关系 $Y_i = \theta_0 + \theta_1 x_i + W_i$；
（b）把 $X_i$ 建模为已知常数；
（c）随机变量 $\theta_0$、$\theta_1$、$W_1, \dots, W_n$ 相互独立且均为正态；
（d）$\theta_0$ 均值为零、方差 $\sigma_0^2$，$\theta_1$ 均值为零、方差 $\sigma_1^2$；
（e）每个 $W_i$ 均值为零、方差 $\sigma^2$。

**估计公式（Estimation Formulas）：** 给定数据对 $(X_i, Y_i)$，$\theta_0$、$\theta_1$ 的 MAP 估计为

```math
\hat{\theta}_1 = \frac{\sigma_1^2}{\sigma_1^2 + \sigma^2\!\!\big/ \sum_{i=1}^{n} (x_i - \bar{x})^2}\,
\frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{n} (x_i - \bar{x})^2},
\qquad
\hat{\theta}_0 = \frac{\sigma_0^2}{\sigma_0^2 + \sigma^2/n}\left(\bar{y} - \hat{\theta}_1 \bar{x}\right),
```

其中

```math
\bar{x} = \frac{1}{n}\sum_{i=1}^{n}x_i .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页公式在源 OCR 中被拆散成大量碎片（如 `a + nao (y - 81x)`、`Ll`、`OS/2a5`、`8I/2aI` 等；`σ0²/σ0²+σ2̸n`、`σ1²/σ1²+σ2̸Σ(xi-x̄)²` 结构可见）。此处按贝叶斯线性回归 MAP 估计的标准公式（先验收缩/加权平均形式）忠实还原，未臆造数值。</span>

---

<!-- ===== PDF p489 ===== -->

<span style="color:#7f8c8d;">书页 482，页眉「Chap. 9 / 482 / Classical Statistical Inference」。本页承接上一页「贝叶斯线性回归」公式框，给出关于其估计的 (a)–(d) 四点说明；随后开启**「多元线性回归（Multiple Linear Regression）」**小节，介绍多解释变量的回归模型。</span>

---

<br>

（续）我们作几点说明：

**（a）** 如果 $\sigma^2$ 相对 $\sigma_0^2$、$\sigma_1^2$ 非常大，则得到 $\hat{\theta}_0 \approx 0$、$\hat{\theta}_1 \approx 0$。这里发生的是：观测值噪声太大、基本被忽略，于是估计变得与先验均值（prior means）相同——而我们假设先验均值为零。

**（b）** 如果让先验方差 $\sigma_0^2$、$\sigma_1^2$ 增大到无穷，这是在表明对于 $\theta_0$、$\theta_1$ 没有任何有用的先验信息（prior information）。此时，MAP 估计变得与 $\sigma^2$ 无关，并且与先前推导的经典线性回归公式一致。

**（c）** 为简单起见，假设 $\bar{x} = 0$。在估计 $\theta_1$ 时，观测值 $y_i$ 的值按其所对应的 $x_i$ 成比例地加权。这很直观：当 $x_i$ 较大时，$\theta_1 x_i$ 对 $Y_i$ 的贡献相对较大，因此 $y_i$ 含有关于 $\theta_1$ 的有用信息；反之，若 $x_i = 0$，则观测 $Y_i$ 与 $\theta_1$ 无关，可以忽略。

**（d）** 估计 $\hat{\theta}_0$、$\hat{\theta}_1$ 是 $Y_i$ 的线性函数，而非 $X_i$ 的线性函数。但请记住，$X_i$ 被当作外生的、非随机的量，而 $Y_i$ 是随机变量 $Y_i$ 的观测值。因此，按第 8.4 节所定义的意义，MAP 估计量 $\hat{\theta}_0$、$\hat{\theta}_1$ 是线性估计量（linear estimators）。在我们正态性假设的前提下，这些估计量同时也就是贝叶斯线性 LMS 估计量以及（最小均方）LMS 估计量（参见第 8.4 节末尾的讨论）。

---

<span style="color:#c0392b;">**多元线性回归（Multiple Linear Regression）**</span>

我们目前关于线性回归的讨论只涉及单个解释变量（explanatory variable），即 $X$，这是一个称为**简单回归（simple regression）**的特例。其目标是根据 $X_i$ 的值构建一个解释观测值 $Y_i$ 的模型。然而许多现象涉及多个潜在的或解释性的变量。（例如，我们可能会考虑一个试图用年龄与受教育年数这两个变量共同解释年收入（annual income）的模型。）这类模型称为**多元回归模型（multiple regression models）**。

举例来说，设我们的数据由三元组 $(X_i, Y_i, Z_i)$ 组成，并希望估计如下形式模型中的参数 $\theta_j$：

```math
Y_i = \theta_0 + \theta_1 X_i + \theta_2 Z_i .
```

例如 $Y_i$ 可以是第 $i$ 个随机样本个体的收入，$X_i$ 是其年龄，$Z_i$ 是其受教育年数。此时，我们要对所有 $\theta_0$、$\theta_1$、$\theta_2$ 最小化残差平方和

```math
\sum_{i=1}^{n}\left(Y_i - \theta_0 - \theta_1 X_i - \theta_2 Z_i\right)^2 .
```

更一般地，对打算采用的解释变量的数目没有限制。回归估计

---

<!-- ===== PDF p490 ===== -->

<span style="color:#7f8c8d;">书页 483，页眉「Sec. 9.2 / 483 / Linear Regression」。本页承接上一页「多元线性回归」小节（多项式/一般线性模型），随后开启并介绍**「非线性回归（Nonlinear Regression）」**小节。本页为 §9.2 中段，无新 Example 编号（下一页进入 §9.3 二值假设检验前仍有内容）。</span>

---

<br>

（续多元线性回归）—— $\hat{\theta}_i$ 的计算在概念上与单解释变量情形相同，当然公式要复杂得多。

作为一个特例，设 $Z_i = X_i^2$，此时我们处理的是如下形式的模型：

```math
Y_i = \theta_0 + \theta_1 X_i + \theta_2 X_i^2 .
```

假如我们有充分理由预期 $Y_i$ 对 $X_i$ 呈二次依赖（quadratic dependence），这样的模型就是合适的（当然，更高阶的多项式模型也是可能的）。虽然这种二次依赖本身是非线性的，但底层模型仍被认为是**线性的**，其含义是：未知参数 $\theta_j$ 与观测到的随机变量 $Y_i$ 之间是线性关系。更一般地，我们可以考虑如下形式的模型：

```math
Y_i = \theta_0 + \sum_{j=1}^{m}\theta_j\,h_j(x_i),
```

其中 $h_j$ 是刻画所预期的 $y$ 对 $x$ 依赖关系的总体形式的函数。通过在所有 $\theta_0, \theta_1, \dots, \theta_m$ 上最小化表达式

```math
\sum_{i=1}^{n}\left(Y_i - \theta_0 - \sum_{j=1}^{m}\theta_j\,h_j(x_i)\right)^2,
```

我们就可以得到参数 $\theta_0, \theta_1, \dots, \theta_m$。这个最小化问题既有闭式解（closed form），也有高效的数值解法。

> <span style="color:#1e8449;">**[t_note]** 注：『线性回归』的『线性』指对**参数** $\boldsymbol\theta$ 线性，不是对**变量** $x$ 线性——这是最容易栽的地方。先证：不管 $h_j(x)$ 是多非线性的基函数，$\sum_i\big(Y_i-\sum_j\theta_j h_j(x_i)\big)^2$ 关于 $\theta_j$ 仍是二次，驻点仍由线性方程组给出、仍有闭式解。这就是为什么放进 $X_i^2,\log X_i$ 等仍『线性』。深层直觉（跨课程，线性代数 Strang）：所谓基函数就是给设计矩阵换列、在原特征空间做一族向量，最小二乘解=原空间上的正交投影——把 $h_j$ 换掉，只是换了一组投影基底，『投影求最优』的机制一分不动。</span>

---

<span style="color:#c0392b;">**非线性回归（Nonlinear Regression）**</span>

在假设模型结构对未知参数呈非线性的情形下，线性回归方法有相应的非线性扩展（nonlinear extensions）。特别是，我们假设变量 $x$ 与 $Y$ 服从如下形式的关系：

```math
Y = h(x; \theta),
```

其中 $h$ 是给定的函数，$\theta$ 是待估的参数。我们已知数据对 $(X_i, Y_i)$（$i = 1, \dots, n$），并寻找使残差平方和

```math
\sum_{i=1}^{n}\left(Y_i - h(X_i; \theta)\right)^2
```

最小的一个 $\theta$ 值。

> <span style="color:#1e8449;">**[t_note]** 注：非线性回归与线性的分水岭在『残差平方和对 $\boldsymbol\theta$ 是否还是参数二次』。先证：线性时对 $\theta$ 求导得到的方程仍是线性的（正是 9.2 的方程组）；当 $h(x;\theta)$ 对 $\theta$ 非线性时，$\frac{\partial}{\partial\theta}\sum_i(Y_i-h(X_i;\theta))^2=0$ 不再是线性方程，闭式解这个优惠就没了，只能靠数值迭代（高斯–牛顿、Levenberg–Marquardt 等）。跨课程（凸优化，进行中）：目标是凸二次 → 闭式解（经典 LS）；目标只凸不一定二次、甚至非凸 → 迭代法。『闭式解是否可得』几乎就等于『目标是否参数二次』，这是判据式的直觉。</span>

与线性回归不同，这个最小化问题一般没有闭式解；不过，实际求解它已有相当高效的计算方法。如同线性回归，可以把非线性最小二乘（nonlinear least squares）看作在如下形式的模型下做极大似然（ML）估计：

---

<!-- ===== PDF p491 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.2 线性回归（Linear Regression）续页，书页 484（章运行页眉「Classical Statistical Inference / Chap. 9」）。本页承接上一页：先完成非线性回归（Nonlinear Regression）以极大似然（ML）解释一段的推导（似然函数为含正态噪声的乘积形式），随后以 **Practical Considerations（实际考量）** 小标题进入 §9.2 末段的实践告诫小节，逐条列出 (a) 异方差、(b) 非线性、(c) 多重共线性、(d) 过拟合。底部 (d) 过拟合在段末进入过渡，内容延续至下一页。</span>

---

<br>

<span style="color:#c0392b;">**§9.2 线性回归（Linear Regression）——（续）非线性回归（Nonlinear Regression）**</span>

其中 $W_i$ 是零均值的独立同分布（i.i.d.）正态随机变量（normal random variables）。为看清这一动机，注意似然函数（likelihood function）取如下形式：

```math
f(Y;\theta) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi\sigma^2}}\, \exp\!\left\{ -\frac{\big(Y_{i} - h(X_{i};\theta)\big)^{2}}{2\sigma^{2}} \right\},
```

其中 $\sigma^2$ 是 $W_i$ 的方差。最大化似然函数等同于最大化上式中指数中的那一项，而这又等价于最小化平方残差之和（sum of the squared residuals）。

> <span style="color:#1e8449;">**[t_note]** 注：这段把『非线性情形下的最小二乘也是 ML』再说了一遍——与 (a) 节是同一个结论搬到一个 $h$ 非线性的壳里。先证：似然 $\prod_i \frac1{\sqrt{2\pi\sigma^2}}\exp\{-(Y_i-h(X_i;\theta))^2/2\sigma^2\}$ 对 $\theta$ 取 $-\log$ 后，只剩 $\frac1{2\sigma^2}\sum_i\big(Y_i-h(X_i;\theta)\big)^2$＋常数。可见『在正态噪声下，ML = 最小化平方和』这个等价性**不要求 $h$ 线性**——线性与否只决定闭式解的有无，不改变『最小二乘即 ML』的性质。把两处对照读，就能抽离出那条跨越 §9.2 的一致性主线。</span>

---

<span style="color:#c0392b;">**实际考量（Practical Considerations）**</span>

回归在许多领域中都被广泛使用，从工程到社会科学莫不如此。然而，它的应用往往需要谨慎。本节我们讨论若干在应用时必须牢记的重要问题，以及回归在哪些主要情形下可能无法产生可靠的估计（reliable estimates）。

**(a) 异方差（Heteroskedasticity）。** 将线性回归作为「存在正态噪声项 $W_i$ 时的 ML 估计」这一动机，包含着一个假设：$W_i$ 的方差对所有 $i$ 都相同。然而，$W_i$ 的方差常常在数据对之间差异很大。例如，$W_i$ 的方差可能严重受到取值 $x_i$ 的影响。（举一个具体的例子：设 $x_i$ 是年收入、$y_i$ 是年消费额。自然可以预期，富人消费额的方差远比穷人消费额的方差大得多。）在这种情况下，少数具有大方差的噪声项可能最终对参数估计产生不相称的影响。相应的补救办法是考虑如下形式的**加权最小二乘（weighted least squares）**准则

```math
\sum_{i=1}^{n} \omega_{i}\,\big(y_{i} - \theta_{0} - \theta_{1}x_{i}\big)^{2},
```

其中，对 $W_i$ 方差较大的那些 $i$，权重（weight）$\omega_i$ 取得更小。

> <span style="color:#1e8449;">**[t_note]** 注：(a) 异方差的修正是加权最小二乘：给噪声大的观测更小的权重。先证直觉：普通 LS 把所有点一视同仁，若富人的噪声方差大，其大偏差点会在平方和里占过重的分量、把拟合线往那儿拽。加权后 $\omega_i$ 小的项贡献小，噪声大的点被『压下去』。教科书最常用的取法是 $\omega_i\propto 1/\sigma_i^2$——按方差的倒数加权，这在线性高斯模型下是近似最优的，因为它等价于把每个 $Y_i$ 先缩放到同方差、再跑普通 LS。工程的判别口诀：画『残差 vs 拟合值』图，若散点呈喇叭口/漏斗状，就是在提示异方差。</span>

**(b) 非线性（Nonlinearity）。** 常常有这样的情形：某个变量 $x$ 能够解释变量 $y$ 的取值，但影响是非线性的。如前所述，基于形如 $\big(h(x_i),\,y_i\big)$ 的数据对的回归模型，配合适当选取的函数 $h$，往往更为合适。

**(c) 多重共线性（Multicollinearity）。** 设想我们在一个用来预测另一变量 $y$ 的模型中使用两个解释变量（explanatory variables）$X$ 和 $Z$。如果 $X$ 与 $Z$ 之间存在强关联，那么估计过程可能无法可靠地区分每个解释变量的相对作用。举一个极端的例子：假设真实关系形如 $y = \theta_0 x + \theta_1 + 1$，并且关系 $z = 2x$ 恒成立。那么形如 $y = \tilde{\theta}_0 z + \tilde{\theta}_1$ 的模型同样成立，于是没有任何估计过程能够在这两种模型之间作出判别。

> <span style="color:#1e8449;">**[t_note]** 注：(c) 多重共线性的要害在『$X,Z$ 高度相关 → 设计矩阵近奇异 → $\hat\theta$ 对系数拆分极不稳定』。先证那个极端例子：若 $z=2x$ 恒成立，则 $\theta_0x+\theta_1$ 与 $\tilde\theta_0 z+\tilde\theta_1$ 描述的是同一条直线，存在无穷多种系数组合等价，$\theta_0,\theta_1$ 在观测上根本不可辨识。实务表现是把 X 与 Z 都放进去时，单个系数的标准差暴涨、符号都可能震荡，但『y 的拟合预测』却往往依然不错——即解释不可靠、预测还行。跨课程（线性代数 Strang）：设计矩阵的列几乎线性相关 ⟺ $X^\top X$ 特征值几乎为 0 ⟺ 法方程病态，理论上与奇异值分解最大/最小奇异值比（条件数）直接挂钩。</span>

**(d) 过拟合（Overfitting）。** 当多元回归具有大量解释变量、相应地有大量待估参数时，就可能出现这样的危险：产生一个能够很好地拟合数据、但在其他方面却毫无用处的模型。例如，假设某个线性模型是真实有效的，但我们 [下一页继续讨论过拟合的告诫]——

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p492）：(d) 过拟合段在「but we」处中断，其完整告诫与「经验法则（rule of thumb）：数据点个数应约为参数个数的约十倍」在下一页给出，随后进入 §9.2 的 (e) 因果性与 §9.3 的引入。</span>

---

<!-- ===== PDF p492 ===== -->

<span style="color:#7f8c8d;">第 9 章过渡页，书页 485。本页上段为 §9.2「实际考量（Practical Considerations）」的收尾：(d) 过拟合告诫的结论部分 + (e) 因果性/伪相关告诫（第 8(9).2 节的最后内容）；下段开始进入 §9.3 二值假设检验（Binary Hypothesis Testing）的引言框架（统计假设作为预测、假设/观测/错误概率的记号，以及 图 9.7 Classical inference framework）。因本页 OCR 页眉严重破损，未捕捉到「Sec. 9.3 / 486」页眉，故 §9.3 红色小节标题依正文内容在本页正文语义转入假设检验框架处标出。图 9.7 图注源 OCR 亦破损，按上下文补全，具体编号以正文为准。</span>

---

<br>

**(d) 过拟合（Overfitting）——（结论，续）** ……但仍然会（就数据外的预测目的而言）得出不正确的估计。作为一条经验法则（rule of thumb），数据点（data points）的个数应至少约为待估参数（parameters）个数的十倍；相应地，当数据相对不足时，过拟合模型往往不稳定。

> <span style="color:#1e8449;">**[t_note]** 注：(d) 过拟合的第一道防线的确是『约 10× 数据点』这条经验法则。先证机理：待估参数越多，模型越能贴合训练数据的噪声；残差平方和在训练集上单调不增（参数增加不会让最小误差升高），但真到未见数据上预测反而变差——『拟合』≠『推广』，这正是『好拟合』与『好预测』脱节的地方。要把它讲得更具体可这样想：太多参数 ⟹ 别想要好的预测，先满足『数据量为每参数供上足够证据』（约 10 倍）。跨课程（算法/学习理论，后续会细讲）：过拟合=方差增大、偏差可忽略的一端，与『偏差–方差权衡』（§9.1 那个分解）是同一枚硬币的两面。</span>

**(e) 因果性（Causality）。** 变量 $x$ 与 $y$ 之间的紧密相关不应被误认为 $x$ 对 $y$ 具有因果影响（causal relation）。例如，设 $x_i$ 为某个家庭中老二孩子的财富、而再以某种共同的成长环境因素把它们联系起来：我们可能预期 $y_i$ 随 $x_i$ 大体线性增长，但这一增长实际上可追溯到一个共同原因所产生的效应，而非其中一个变量对另一个变量的因果作用。

> <span style="color:#1e8449;">**[t_note]** 注：(e) 的告诫是整个『回归可识别相关、不能自动识别因果』的原则。最容易误导的栗子正是这个老二孩子财富：$y$(全家/家庭环境)与 $x$(老二财富)都被某个共同因素驱动，于是回归显著、$x$ 对 $y$ 有很强预测力，却没有任何一个方向是因果。先证判据：回归证据只能说明条件相关，不能区分『$x\to y$』、『$y\to x$』还是『存在混淆变量 $C$ 同时驱动两者』三类结构。要谈因果，需要干预/实验或可识别性假设（后续因果推断课程会系统化它）；本书在此只立红线——相关≠因果。</span>

<br>

---

<span style="color:#c0392b;">**§9.3 二值假设检验（Binary Hypothesis Testing）**</span>

本节我们放宽对先验概率（prior probabilities）的假设，并舍弃部分贝叶斯语言，转而采用传统的（经典的）统计语言（traditional / classical statistical language）。在经典框架中，某个给定的假设起着「默认模型（default model）」的作用，它可能为真、也可能为假，但**并不被当作随机事件**加以处理。

可用的观测是一个随机变量向量 $X=(X_1,\dots,X_n)$。与假设相关的记号我们记作 $P(\cdot\,; \mathrm{H}_0)$ 与 $P(\cdot\,; \mathrm{H}_1)$，即「在假设 $\mathrm{H}_0$ / $\mathrm{H}_1$ 为真时」的概率。需要特别注意：这些**不是**条件概率（conditional probabilities），因为真实的假设并不被视作随机变量。类似地，我们用 $p_X(x;\,\mathrm{H}_0)$、$p_X(x;\,\mathrm{H}_1)$（或 PDF 情形下的 $f_X(x;\,\mathrm{H}_0)$、$f_X(x;\,\mathrm{H}_1)$）表示在相应假设下观测向量 $X$ 取到各取值 $x$ 的概率，并用 $x$ 表示观测向量这一随机变量的实现值（realized value）。

> <span style="color:#1e8449;">**[t_note]** 注：这里的分号（$P(\cdot;\mathrm{H}_i)$）是频率派哲学的纹章，值得较真。先证两种写法：贝叶斯写 $P(\cdot\mid \mathrm{H}_i)$——用竖线，因为假设是随机事件、有先验概率，可作条件；经典写 $P(\cdot;\mathrm{H}_i)$——用分号，因为真实假设是固定但未知的真值、**不是随机事件**、没有先验可条件化。这个记号差异不是纯形式：它代表『我不能谈『$\mathrm{H}_0$ 为真的概率』』这一硬约束，也正因如此，LRT 的阈值 $\xi$ 才不能由任何先验比给出、只能靠使用者权衡（见后文）。先想通这一层，后面 Neyman–Pearson 为何那么‘绕’就顺了——他们在不引入先验的前提下仍想给 LRT 一个最优性定理。</span>

> <span style="color:#7f8c8d;">图 9.7（Figure 9.7）：Classical inference framework for hypothesis testing（经典假设检验推断框架）。[原页此处为插图图注，OCR 破损，依上下文补全文字，未臆造图内细节。]</span>

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p493）：本页转入 §9.3 框架后，下一页给出「判定划分观测空间为拒绝域/接受域」这一决策规则（decision rule）结构（图 9.8）以及第一类/第二类错误（type I / type II error）的定义。</span>

---

<!-- ===== PDF p493 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 二值假设检验（Binary Hypothesis Testing）续页，书页 486。本页为 §9.3 决策规则的结构化内容：把观测空间划分为拒绝域（rejection region）$R$ 与其补集接受域（acceptance region）$R^{c}$（图 9.8 Structure of a decision rule），随后定义两类错误——第一类错误（type I error / false rejection）与第二类错误（type II error / false acceptance）。本页源 OCR 破损较重，公式与关键词按上下文忠实重构，无法辨认处留有灰注释。</span>

---

<br>

**决策规则（decision rule）**：一个决策规则可以由观测空间（observation space）的一个划分（partition）来描述——把观测向量 $X=(X_1,\dots,X_n)$ 的所有可能取值划分为两个区域：拒绝域（rejection region）$R$ 与其补集 $R^{c}$，后者称为接受域（acceptance region）。

> <span style="color:#7f8c8d;">图 9.8（Figure 9.8）：Structure of a decision rule for binary hypothesis testing（二值假设检验中一个决策规则的结构）。[原页此处为插图图注，OCR 破损，文字依上下文补全。]</span>

当所观测到的实现值落在拒绝域 $R$ 中时，我们拒绝 $\mathrm{H}_{0}$（即判定 $\mathrm{H}_{1}$ 成立）；当观测值落在接受域 $R^{c}$ 中时，我们接受 $\mathrm{H}_{0}$（即判定 $\mathrm{H}_{0}$ 成立）。原假设（null hypothesis）$\mathrm{H}_{0}$ 起着前述「默认模型」的作用。

对一个决策规则而言，可能产生两类错误（errors）：

**(a) 在第一类错误（type I error）中，$\mathrm{H}_{0}$ 实际上为真，却拒绝了 $\mathrm{H}_{0}$。** 这称为弃真（false rejection，拒真），其发生概率为

```math
\alpha(R) = P\big(X \in R;\, \mathrm{H}_{0}\big).
```

**(b) 在第二类错误（type II error）中，$\mathrm{H}_{0}$ 实际上为假，却接受了 $\mathrm{H}_{0}$。** 这称为误纳（false acceptance，存伪），其发生概率为

```math
\beta(R) = P\big(X \notin R;\, \mathrm{H}_{1}\big).
```

> <span style="color:#1e8449;">**[t_note]** 注：两类错误的命名务必当场印牢——**第一类（Type I）= 弃真**：$\mathrm{H}_0$ 为真却被拒绝，概率 $\alpha(R)=P(X\in R;\mathrm{H}_0)$；**第二类（Type II）= 误纳**：$\mathrm{H}_0$ 为假却被接受，概率 $\beta(R)=P(X\notin R;\mathrm{H}_1)$。中文选『弃真/误纳』比直译『拒真/存伪』更对仗,任取其一保持全篇一致即可。核心结构只有一个 $R$，$\alpha$ 与 $\beta$ **共用同一个拒绝域**、此消彼长——这正是后文『不存在唯一最优阈值』与『有效前沿』的根。跨课程（信号检测/通信，后续）：这就是虚断概率（false alarm）与漏检概率（miss）的翻版，同一套数学。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上述两类错误的概率公式在源 OCR 中被拆成碎片（关键字如 `α(R)=`、`β(R)=`、`P(X∈R; Ho)`、`P(X∉R; H1)` 分散在不同行且夹杂乱码），现按本页题意的数学语义（第一类错误=原假设为真时落入拒绝域，第二类错误=备择假设为真时落入接受域）忠实重构，未臆造数值。本页末段「In analogy with …（与…相类比）」一句源 OCR 严重损坏，无法辨认其完整内容，以下略过不译。</span>

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p494）：本页末尾原文既有转入似然比（likelihood ratio）与 MAP 准则改写的内容，该部分在下一页页首「（assuming that X is discrete）……」处续接展开。</span>

---

<!-- ===== PDF p494 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 二值假设检验（Binary Hypothesis Testing）续页，书页 487（页眉「Sec. 9.3 / 487」）。本页承接上一页的决策规则记号，引入似然比（likelihood ratio）$L(x)$ 与临界值（critical value）$\xi$，给出 MAP 准则的改写形式、似然比检验（LRT）的拒绝域以及 $\xi=1$ 时的 ML 准则特例，随后新启 **Example 9.10**（骰子公平性检验）。自 §9.3 起（书页 487 处）例号连续为 9.10；上一例（9.9）在 §9.2。页末两处脚注（†）说明似然比记号的物理含义。源 OCR 大体清晰。</span>

---

<br>

（假设 $X$ 是离散的。）† 上述决策规则可改写如下：定义似然比（likelihood ratio）$L(x)$ 为

```math
L(x) = \frac{p_{X\mid\Theta}(x \mid \theta_{1})}{\;p_{X\mid\Theta}(x \mid \theta_{0})\;},
```

并判定 $\theta=\theta_{1}$ 为真——只要观测向量 $X$ 的实现值 $x$ 满足

```math
L(x) > \xi,
```

其中临界值（critical value）$\xi$ 为

```math
\xi = \frac{p_{\Theta}(\theta_{0})}{\;p_{\Theta}(\theta_{1})\;}.
```

若 $X$ 连续，方法与上述相同，唯一区别在于似然比定义为两个 PDF 之比：

```math
L(x) = \frac{f_{X\mid\Theta}(x \mid \theta_{1})}{\;f_{X\mid\Theta}(x \mid \theta_{0})\;}.
```

受上述 MAP 准则形式的启发，我们考虑形如

```math
R = \big\{x \mid L(x) > \xi\big\}
```

的拒绝域，其中似然比 $L(x)$ 的定义与贝叶斯情形类似：†

```math
L(x) = \frac{p_{X}(x; \mathrm{H}_{1})}{p_{X}(x; \mathrm{H}_{0})},
\qquad \text{或} \qquad
L(x) = \frac{f_{X}(x; \mathrm{H}_{1})}{f_{X}(x; \mathrm{H}_{0})}.
```

临界值 $\xi$ 仍可自由选取，依据其他考量而定。特殊情况 $\xi = 1$ 对应 ML 准则（ML rule）。

> <span style="color:#1e8449;">**[t_note]** 注：LRT 的全部设计自由度都浓缩在临界值 $\xi$ 上——而它**不来自任何先验比**（经典里根本没有先验），只由使用者的权衡取舍反定。先证结构：似然比 $L(x)=\frac{p_X(x;\mathrm{H}_1)}{p_X(x;\mathrm{H}_0)}$ 完全由数据决定、与 $\xi$ 无关；$\xi$ 只是在门槛上决定『$L$ 要大到多少才够格判 $\mathrm{H}_1$』。$\xi$ 越小→拒绝域越大→更容易判 $\mathrm{H}_1$。特殊点 $\xi=1$ 是『看哪个假设更可能就说哪个』（ML 准则），是对称、自然的基线。对照记忆：贝叶斯里 $\xi$ 被先验比 $\frac{p_\Theta(\theta_0)}{p_\Theta(\theta_1)}$ 锁死，经典里把它释放成可调旋钮——两个框架对『阈值从哪儿来』给出了两种不同答案。</span>

> <span style="color:#7f8c8d;">脚注 †（本段使用条件概率记号，因为这里是在贝叶斯框架内讨论。）——位于原页页脚。</span>

> <span style="color:#7f8c8d;">脚注 †（注意我们使用 $L(x)$ 表示基于随机观测 $X$ 的实现值 $x$ 计算出的似然比取值。另一方面，在实验开展之前，似然比最好是视为观测 $X$ 的一个函数形式的随机变量，此时记作 $L(X)$。当然，$L(X)$ 的概率分布取决于哪一个假设为真。）——位于原页页脚。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.10（骰子公平性检验，Testing a die for fairness）**</span>

我们有一颗六面骰子，想要检验它是否公平，并为六个面的概率提出了两个假设：

<center>$\mathrm{H}_{0}$（公平骰子 fair die）：$\;p_X(x; \mathrm{H}_{0})=\dfrac{1}{6}$，对 $x=1,\dots,6$；</center>

<center>$\mathrm{H}_{1}$（灌铅/偏置骰子 loaded die）：$\;p_X(x; \mathrm{H}_{1})=\begin{cases} \tfrac{1}{4}, & \text{若 } x=1,2,\\ \tfrac{1}{8}, & \text{若 } x=3,4,5,6.\end{cases}$</center>

（该例的似然比取值与三种临界值情形在下一页分析。）

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p495）：Example 9.10 在此给出两个假设的分布，下一页计算单次投掷下似然比 $L(x)$ 的取值、三种临界值 $\xi$ 对应拒绝域，以及两类错误概率 $\alpha(\xi)$、$\beta(\xi)$。</span>

---

<!-- ===== PDF p495 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 续页，书页 488（运行页眉「Classical Statistical Inference / Chap. 9」）。本页为 **Example 9.10（续）**：对单次投掷计算似然比 $L(x)$ 的两个取值，继而给出临界值 $\xi$ 的三种区间对应的三个拒绝域，直观地解释为何 $\xi$ 过高时会「从不拒绝 $\mathrm{H}_{0}$」，并据此计算两类错误概率 $\alpha(\xi)$ 与 $\beta(\xi)$ 的分段表达式（结合 Fig. 9.9 的权衡讨论在此收于「最常见的选择办法如下」）。源 OCR 大体清晰，个别字母扫描乱码（如 thE'=the）已按语义校正。</span>

---

<br>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#7f8c8d;">**Example 9.10（续）**</span>

骰子单次投掷 $x$ 的似然比（likelihood ratio）为

```math
L(x) =
\begin{cases}
\dfrac{1/4}{1/6} = \dfrac{3}{2}, & \text{if } x=1,2,\\[1ex]
\dfrac{1/8}{1/6} = \dfrac{3}{4}, & \text{if } x=3,4,5,6.
\end{cases}
```

由于似然比只取两个不同的值，故对临界值 $\xi$ 只需考虑三种可能区间，各对应三个拒绝域：

<center>$\xi < \tfrac{3}{4}$：对一切 $x$ 都拒绝 $\mathrm{H}_{0}$；</center>

<center>$\tfrac{3}{4} < \xi < \tfrac{3}{2}$：若 $x=3,4,5,6$ 则接受 $\mathrm{H}_{0}$，若 $x=1,2$ 则拒绝 $\mathrm{H}_{0}$；</center>

<center>$\tfrac{3}{2} < \xi$：对一切 $x$ 都接受 $\mathrm{H}_{0}$。</center>

直觉上，掷出 $1$ 或 $2$ 提供了有利于 $\mathrm{H}_{1}$ 的证据，我们倾向于拒绝 $\mathrm{H}_{0}$。另一方面，若把临界值设得过高（$\xi > \tfrac{3}{2}$），我们便从不拒绝 $\mathrm{H}_{0}$。事实上，对骰子的单次投掷而言，该检验仅在区间 $\tfrac{3}{4} < \xi < \tfrac{3}{2}$ 内才有意义，因为对其它取值，决策将不依赖于观测值。

> <span style="color:#1e8449;">**[t_note]** 注：Example 9.10 示范了离散情形 LRT 的『三区域展开』，读懂的钥匙是 $L(x)$ 只取两个值。先证：$L(x)\in\{3/2,\,3/4\}$，于是把 $\xi$ 与这两个数比大小，只有三种相对位置 → 只有三个截然不同的拒绝域：(1) $\xi<3/4$ 全拒；(2) $3/4<\xi<3/2$ 只见 $x=1,2$ 才拒；(3) $\xi>3/2$ 全受。第 (1)(3) 是『不看数据就做决定』的退化规则，真正有信息量的只有 (2)。这同时也预告了下一节的要点：$L(X)$ 离散时 $\alpha(\xi)$ 是不连续阶梯，无法精确命中任一预设 $\alpha$——只能用近似或随机化。</span>

对每个临界值，都能由题设数据计算出错误概率（error probabilities）。特别是，弃真概率（false rejection probability）为

```math
\alpha(\xi) \;=\; P\big(X \in R;\, \mathrm{H}_{0}\big) \;=\;
\begin{cases}
1, & \text{if } \xi < \tfrac{3}{4},\\[1ex]
P\big(X=1,2;\, \mathrm{H}_{0}\big)=\tfrac{1}{3}, & \text{if } \tfrac{3}{4} < \xi < \tfrac{3}{2},\\[1ex]
0, & \text{if } \tfrac{3}{2} < \xi,
\end{cases}
```

而误纳概率（false acceptance probability）为

```math
\beta(\xi) \;=\; P\big(X \notin R;\, \mathrm{H}_{1}\big) \;=\;
\begin{cases}
0, & \text{if } \xi < \tfrac{3}{4},\\[1ex]
P\big(X=3,4,5,6;\, \mathrm{H}_{1}\big)=\tfrac{1}{2}, & \text{if } \tfrac{3}{4} < \xi < \tfrac{3}{2},\\[1ex]
1, & \text{if } \tfrac{3}{2} < \xi .
\end{cases}
```

注意，正如上述例子所表明的，选取 $\xi$ 是在两类错误的概率之间作权衡（tradeoff）。确实，随着 $\xi$ 增大，拒绝域随之变小。其结果是弃真概率 $\alpha(R)$ 减小，而误纳概率 $\beta(R)$ 增大（见图 9.9，Figure 9.9）。正是由于这种权衡，不存在唯一最优的临界值选取方式。最常见的选取办法如下（见下一页）。

> <span style="color:#1e8449;">**[t_note]** 注：『$\xi$ 增大 → 拒绝域缩小 → $\alpha$ 降、$\beta$ 升』这条单调权衡曲线，就是后面『有效前沿』的雏形，先把它想穿。先证：拒绝域 $R$ 变小后，$P(X\in R;\mathrm{H}_0)=\alpha$ 只降不升；同时 $R^c$ 变大、$P(X\notin R;\mathrm{H}_1)=\beta$ 严格上升。因为**同一个 $R$ 同时决定 $\alpha$ 与 $\beta$**，想压低一类错误就必然抬升另一类——这是一条硬权衡、没有免费午餐。所以『唯一最优 $\xi$』根本不存在；标准出路是先锁定一个可接受的 $\alpha$，再反解 $\xi$（下一页的处理）。记住‘卡 $\alpha$ ’这个约定，是整节最关键的操作约定。</span>

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p496）：本页以「最常见的办法如下」收尾；下一页引入图 9.9（Error probabilities in a likelihood ratio test）的权衡图示，并说明针对预设的弃真概率 $\alpha$ 来选取临界值 $\xi$ 的通用程序（当 $L(X)$ 只取有限多个值时 $\alpha$ 对 $\xi$ 的依赖可能不连续）。</span>

---

<!-- ===== PDF p496 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 续页，书页 489。本页承接上一页「最常见的选取临界值的办法如下」，给出图 9.9（Error probabilities in a likelihood ratio test）的权衡图示说明，并讲解通用程序：为达到预设的弃真概率 $\alpha$，站在 $\alpha$ 出发反求临界值 $\xi$，即令 $P(L(X)>\xi; \mathrm{H}_{0})=\alpha$；同时指出当似然比 $L(X)$ 只取有限多个值时，$\alpha$ 对 $\xi$ 的依赖可能不连续，并列出 $\alpha$ 的典型取法（$\alpha=0.1,\,0.05,\,0.01$）。本页源 OCR 破损较重，正文句式按上下文忠实重构，无法辨认处留有灰注释。</span>

---

<br>

> <span style="color:#7f8c8d;">图 9.9（Figure 9.9）：Error probabilities in a likelihood ratio test（似然比检验中的错误概率）。随着临界值 $\xi$ 变小，拒绝域随之增大：弃真概率 $\alpha$ 减小，而误纳概率 $\beta$ 增大。[原页此处为插图图注，OCR 破损，文字依上下文及图名补全。]</span>

**最常见的选取临界值的办法**如下：我们站在预设的弃真概率出发，而不是直接选取 $\xi$。具体地，先选定一个期望的弃真概率值 $\alpha$（type I error level），然后取满足

```math
P\big(L(X) > \xi ;\, \mathrm{H}_{0}\big) = \alpha
```

的临界值 $\xi$。典型地，$\alpha$ 取 $\alpha = 0.1$、$\alpha = 0.05$ 或 $\alpha = 0.01$ 等常见数值。

> <span style="color:#1e8449;">**[t_note]** 注：『锁定 $\alpha$、反向解 $\xi$』是频率派的可操作约定——它把最受控的那类错误（Type I）钉在一个可对外声明的水平上。先证含义：这里的 $\alpha$ 是**同一检验程序被长期复用时**的弃真频率（重复试验约 $\alpha$% 冤枉 $\mathrm{H}_0$），不是这一次操作对错的后验概率——这正好呼应置信区间的覆盖频率解读，同一种『频率式正确』的世界观。$\alpha=0.05$ 是最常见的门槛（0.10、0.01 次之），源于 Fisher 时代‘显著’阈值的约定俗成。跨课程（科研方法）：整条『$p<0.05$ 才算显著』的行话就从这个 $\alpha$ 出发，理解它你才看得懂一半文献。</span>

需要指出，$\alpha$ 对 $\xi$ 的依赖未必连续。例如，当似然比 $L(x)$ 只取有限多个不同的值时（如 Example 9.10 的骰子例），就可能无法精确地解出上述等式对 $\xi$ 的要求；此时只能近似逼近预设的 $\alpha$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页中段两句（涉及「What is needed to … / so that … probability α」）源 OCR 破碎，无法辨认其完整措辞；据上下文判断其大意是「对给定一个问题，为达到想要的弃真概率 $\alpha$，需要相应地选取临界值 $\xi$。」此处以下略过对无法辨认片段的逐字翻译。</span>

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p497）：本页既论述「为达到规定弃真概率 $\alpha$ 而反求 $\xi$」的一般程序，亦提及「当 $L(X)$ 离散、无法精确达 $\alpha$ 时需近似处理」，下一页（Example 9.11）以一个连续观测的算例展示完整求解过程。</span>

---

<!-- ===== PDF p497 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 续页，书页 490，包含 **Example 9.11**。本页源 OCR 严重破损，几乎每一行的文字都被切碎和乱码化，仅能辨认出若干关键词（连续观测的似然比、拒绝域形如 $R=\{x \mid x > \gamma\}$、选取 $\gamma$ 使弃真概率等于预设 $\alpha$、随后计算误纳概率 $\beta$ 等）以及「Example 9.11」的转引。为遵守「绝不臆造数值」的铁律，本页只重建可辨识的结构骨架，所有具体公式与数值以灰注释标注为无法辨识，不强行补全。</span>

---

<br>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.11（连续观测下的似然比检验——拒绝域 $R=\{x\mid x>\gamma\}$）**</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏] 本节 Example 9.11 的正文在源 OCR 中被切成大量碎片行（如 `exp {...}`、`if x>γ`、`R = {x | x>γ}`、`α=…`、`γ=…`、`β=…` 等，彼此间夹杂乱码与散落的 `1`、`1/2`、`√(2π)` 等孤立的数学符号），无法恢复其完整的题设数值与推导。根据可辨认片段与上下文判定，该例大致结构为：给定某个连续观测 $X$，假设其 PDF 在 $\mathrm{H}_0$ 与 $\mathrm{H}_1$ 下取不同的指数族形式；似然比 $L(x)$ 单调，从而使 LRT 等价于「当 $X > \gamma$ 时拒绝 $\mathrm{H}_{0}$」；再选取临界值 $\gamma$ 以满足预设的弃真概率 $\alpha=\alpha(\gamma)$，最后借此计算误纳概率 $\beta$。以下仅转写可辨识的结构，具体函数形式与数值不再臆造。</span>

设置拒绝域（rejection region）

```math
R = \big\{x \mid x > \gamma\big\},
```

其中 $\gamma$ 依题意选取。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页另含「Example 9.11」、「and corresponds 」、「as in the preceding example」等呼应前文（Example 9.10 与前一页的 $\alpha$ 选取程序）的过渡片段，其完整措辞无法辨认，略过不译。下一页（PDF p498）将给出本节引出的 **Neyman–Pearson 引理（Neyman–Pearson Lemma）** 对 LRT 最优性的证明。</span>

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p498）：Example 9.11 页末源 OCR 完全断裂，无法给出 $\beta$ 的最终数值；其正反推导在下一页页首处，以「当 $L(X)$ 为连续随机变量…… $P(L(X)>\xi; \mathrm{H}_0)$ 随 $\xi$ 增大从 1 连续降到 0」衔接续讲。</span>

---

<!-- ===== PDF p498 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 续页，书页 491（页眉「Sec. 9.3 / 491」）。本页承接上一页对「反设弃真概率来选取 $\xi$」的讨论：先说明 $L(X)$ 连续时能精确解出 $\alpha$，离散时（cf. Example 9.10）只能近似或随机化处理；随后给出本节核心结果 **Neyman–Pearson 引理（Neyman–Pearson Lemma）**，并用一个虚构的贝叶斯题例（先验比 $p_{\Theta}(\theta_{0})/p_{\Theta}(\theta_{1})=\xi$）为其合理性论证。源 OCR 大体清晰。</span>

---

<br>

当 $L(X)$ 是连续随机变量时（正如上一例那样），概率 $P\big(L(X) > \xi;\, \mathrm{H}_{0}\big)$ 随 $\xi$ 增大而从 $1$ 连续地降到 $0$。于是，总可以找到一个 $\xi$，使要求 $P\big(L(X) > \xi;\, \mathrm{H}_{0}\big) = \alpha$ 得到满足。然而，若 $L(X)$ 是离散随机变量，则无论 $\xi$ 如何选取，都可能无法精确满足等式 $P\big(L(X) > \xi;\, \mathrm{H}_{0}\big) = \alpha$；参见 Example 9.10。在这种情形下有若干种可行的做法：

- **(a)** 力求近似满足等式（strive for approximate equality）。
- **(b)** 选取满足 $P\big(L(X) > \xi;\, \mathrm{H}_{0}\big) \le \alpha$ 的最小 $\xi$。
- **(c)** 利用某外部随机源，在两个备选的临界值候选之间进行随机选择。这种做法（称为「随机化似然比检验，randomized likelihood ratio test」）具有一定理论意义。不过它对实际应用不够重要，本书不予进一步讨论。

> <span style="color:#1e8449;">**[t_note]** 注：离散 $L(X)$ 卡住『精确命中 $\alpha$』时，三个退路各有分量。先证为何会卡：$\alpha(\xi)=P\big(L(X)>\xi;\mathrm{H}_0\big)$ 随 $\xi$ 在有限个值之间跳变，可能存在 $\alpha(\xi_0)>\alpha>\alpha(\xi_1)$ 的空档而无解。(a) 近似——直接挑最接近的 $\xi$；(b) 保守——取 $\alpha'(\xi)\le\alpha$ 的最严 $\xi$（不超预算，但不把预算用满）；(c) 随机化——在 $\xi_0,\xi_1$ 间掷一次硬币，把 $\alpha$ 精确调到夹在中间的目标值，理论最优但实务罕见。先记住序贯悬念：连续 $L(X)$ 无此烦恼，Example 9.12 正是光滑情形，下一节的手法全在连续背景下展开。</span>

截至目前，我们只是通过类比贝叶斯推断（Bayesian inference）来论证 LRT 的合理性。下面我们给出一个更强的理由：**对给定的弃真概率，LRT 提供尽可能小的误纳概率。**

---

<span style="color:#00838f;">**[定理] Neyman–Pearson 引理（Neyman–Pearson Lemma，内曼–皮尔逊引理）**</span>

考虑 LRT 中临界值 $\xi$ 的一个特定取法，它产生如下的错误概率：

```math
P\big(L(X) > \xi;\, \mathrm{H}_{0}\big) = \alpha,
\qquad
P\big(L(X) \le \xi;\, \mathrm{H}_{1}\big) = \beta .
```

假设某个其它检验具有拒绝域 $R$，并且取得了不大于上述弃真概率的弃真概率：

```math
P\big(X \in R;\, \mathrm{H}_{0}\big) \;\le\; \alpha .
```

那么

```math
P\big(X \notin R;\, \mathrm{H}_{1}\big) \;\ge\; \beta,
```

并且在 $P\big(X \in R;\, \mathrm{H}_{0}\big) < \alpha$ 时成立严格不等式 $P\big(X \notin R;\, \mathrm{H}_{1}\big) > \beta$。

> <span style="color:#1e8449;">**[t_note]** 注：Neyman–Pearson 引理是 LRT 的‘金奖状’，值得逐词拆。先证它的断言：在所有把弃真概率压到 $\le\alpha$ 的检验里（即任意拒绝域 $R$ 满足 $P(X\in R;\mathrm{H}_0)\le\alpha$），LRT 的误纳概率 $\beta$ 是**最小**的；而且若别的检验的 $\alpha'<\alpha$（更严），则其 $\beta'$ 严格更大（更差）。一句话记住：**先控制住 $\alpha$，LRT 就把 $\beta$ 压到最低。** 空前可贵之处在于：这一定理**对任何分布都成立**、不依赖正态或指数假设——是这类最优性结论里少有的‘无参数假设’版本。也正因如此，‘买保险’式新检验在固定 $\alpha$ 的前提下没有销量，LRT 已占住最优。</span>

**（论证）** 为论证 Neyman–Pearson 引理的合理性，设想一个虚构的贝叶斯决策问题，其中 $\mathrm{H}_{0}$、$\mathrm{H}_{1}$ 的先验概率满足

```math
\frac{p_{\Theta}(\theta_{0})}{\;p_{\Theta}(\theta_{1})\;} = \xi ,
```

从而有

```math
p_{\Theta}(\theta_{0}) = \frac{\xi}{1 + \xi} .
```

于是，如本节开头所讨论，MAP 准则所用的阈值恰等于 $\xi$，故 MAP 准则与 LRT 准则完全相同。而 MAP 规则是（在该允许的决策规则类中）贝叶斯最优的——

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p499）：Neyman–Pearson 引理的论证在此页建立了「LRT 等价于阈值为 $\xi$ 的虚设贝叶斯 MAP 规则」这一关键联系；下一页据此收敛到「LRT 落在可达错误概率族的有效前沿（efficient frontier）上」的结论。</span>

---

<!-- ===== PDF p499 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 续页，书页 492。本页完成 Neyman–Pearson 引理的论证收束，并引入「可达错误概率对集合 $\mathcal{E}$ 与其有效前沿（efficient frontier）」的概念（附图 Fig. 9.11 与图 9.12，其图注在下一页页首续有一则关于观测空间子集的补充）。源 OCR 破损较重，论证推进与关键概念按上下文忠实重构；无法辨认的具体比式以灰注释标注。</span>

---

<br>

**（论证续）** ……由于具有阈值 $\xi$ 的 MAP 准则在该（允许的）决策规则类中是最优的，因此任何与它等价的 LRT 所对应的错误概率对 $\big(\alpha(\xi),\,\beta(\xi)\big)$ 便不可能被其它检验同时改进。这正好给出了 Neyman–Pearson 引理：在要求的弃真概率上界 $\alpha$ 之内，其它检验都无法取得比 LRT 更小的误纳概率。

为更直观地刻画这一最优性，把注意力放到**所有可达错误概率对的集合（set of achievable error pairs）$\mathcal{E}$** 上：当拒绝域 $R$ 遍历观测空间的一切可行子集时，每一对错误概率
 $\big(\alpha(R),\,\beta(R)\big)=\big(P(X\in R; \mathrm{H}_{0}),\;P(X\notin R; \mathrm{H}_{1})\big)$ 构成 $\mathcal{E}$ 中的一个点。$\mathcal{E}$ 的**有效前沿（efficient frontier）** 指的是其中那些「无法被改进」的点：即不存在另一个点，其弃真概率与误纳概率（$\alpha$ 与 $\beta$）都更小。恰如 Neyman–Pearson 引理所表明的，LRT 给出的错误概率对落在（或趋近于）这一有效前沿之上。

> <span style="color:#1e8449;">**[t_note]** 注：『有效前沿（efficient frontier）』说到底就是多目标权衡里的帕累托前沿（Pareto frontier）——跟你在凸优化/经济里碰到的是同一个东西。先证定义在几何上的样子：把每个可行拒绝域 $R$ 画成一个点 $(\alpha(R),\beta(R))$，所有点组成集合 $\mathcal{E}$；前沿=那些『再减 $\alpha$ 必增 $\beta$、再减 $\beta$ 必增 $\alpha$』的（西南角）点。Neyman–Pearson 引理告诉你的正是：LRT 随 $\xi$ 扫出的这些点**恰好描出整条前沿**（没有别的点能把 $\alpha$ 与 $\beta$ 同时压得更小）。跨课程（凸优化/多准则优化，进行中）：(极小元) 集合的帕累托边界 = 有效前沿，这是『权衡』思想的统一图示。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页源 OCR 中的定义域写法（如「$\mathcal{E}$」的集合表述及「for any point in $\mathcal{E}$ there is no point with $\alpha \le \alpha(R)$ and $\beta \le \beta(R)$」的完整条件句式）被切碎，现按教材原意（有效前沿=帕累托前沿）忠实重构，未臆造数值。涉及图 9.11/9.12 的具体集合形状读图细节源 OCR 亦无法辨认，略去对其图内的数值点朗读。</span>

<br>

> <span style="color:#7f8c8d;">衔接下一页（PDF p500）：本页以「有效前沿」概念收尾，下一页页首为图 9.12 补充图注（「Set of pairs $\big(\alpha(R),\beta(R)\big)$ as $R$ ranges over all subsets of the observation space」），随后新启 **Example 9.12**：两个单位方差、相互独立的（i.i.d.）正态观测 $X_1,X_2$，$\mathrm{H}_0$ 下共同均值为 $0$、$\mathrm{H}_{1}$ 下共同均值为 $2$，并取目标 $\alpha=0.05$。</span>

---

<!-- ===== PDF p500 ===== -->

<span style="color:#7f8c8d;">第 9 章 §9.3 二值假设检验（Binary Hypothesis Testing）续页，书页 493。本页页首补截图 9.12 的一句话图注（Set of pairs $\big(\alpha(R),\beta(R)\big)$ as $R$ ranges over all subsets of the observation space），随后新启 **Example 9.12**：两个独立同分布（i.i.d.）的单位方差正态观测 $X_1,\,X_2$，$\mathrm{H}_0$ 下共同均值为 $0$、$\mathrm{H}_{1}$ 下共同均值为 $2$，目标弃真概率取 $\alpha=0.05$。推导似然比 $L(x)=\exp\{2(X_1+X_2)-4\}$，把对临界值 $\xi$ 的比较等价化为对 $X_1+X_2 > \gamma$（$\gamma=(4+\log \xi)/2$）的比较，并取 $\gamma=\sqrt{2}\cdot 1.645$ 使弃真概率等于 $0.05$，拒绝域为 $\{X_1+X_2 > \sqrt{2}\cdot 1.645\}$；页末转入在 $\mathrm{H}_{1}$ 下计算误纳概率 $\beta$。该例在下一页继续（本单元止于此例中途）。</span>

---

<br>

> <span style="color:#7f8c8d;">图 9.12（Figure 9.12）：Set of pairs $\big(\alpha(R),\, \beta(R)\big)$ as $R$ ranges over all subsets of the observation space（当 $R$ 遍历观测空间的一切子集时，所有点对 $\big(\alpha(R),\beta(R)\big)$ 的集合）。[原页此处为插图图注的一部分，承接上一页的有效前沿讨论。]</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.12（两个正态观测的似然比检验与最优性对比）**</span>

我们观测两个独立同分布（i.i.d.）的单位方差正态随机变量 $X_1$ 和 $X_2$。在 $\mathrm{H}_0$ 下它们的共同均值为 $0$；在 $\mathrm{H}_1$ 下它们的共同均值为 $2$。我们选取临界值，使对应的弃真概率达到预设值 $\alpha=0.05$。

似然比（likelihood ratio）取如下形式：

```math
L(x) = \frac{\exp\big\{-\big((x_{1}-2)^{2} + (x_{2}-2)^{2}\big)/2\big\}}{\exp\big\{-\big(x_{1}^{2} + x_{2}^{2}\big)/2\big\}}
= \exp\big\{2\,(x_{1} + x_{2}) - 4\big\}.
```

把 $L(x)$ 与某个临界值 $\xi$ 比较，等价于把 $X_1+X_2$ 与临界值

```math
\gamma = \frac{4 + \log \xi}{2}
```

比较。因此，在 LRT 下，只要 $X_1+X_2 > \gamma$，我们就判定接受 $\mathrm{H}_{1}$。

为确定拒绝域的确切形式，需要求出 $\gamma$，使弃真概率 $P\big(X_1+X_2 > \gamma;\, \mathrm{H}_{0}\big)$ 等于 $0.05$。注意在 $\mathrm{H}_0$ 下，随机变量

```math
Z = \frac{X_{1} + X_{2}}{\sqrt{2}} \sim \mathcal{N}(0,1)
```

是标准正态（standard normal）的，于是我们取

```math
\gamma = \sqrt{2}\cdot 1.645,
```

使得

```math
P\big(X_{1}+X_{2} > \sqrt{2}\cdot 1.645\,;\, \mathrm{H}_{0}\big) = 0.05,
```

从而得到拒绝域（rejection region）

```math
R = \big\{ x \,\big|\, X_{1}+X_{2} > \sqrt{2}\cdot 1.645 \big\}.
```

> <span style="color:#1e8449;">**[t_note]** 注：Example 9.12 是『连续 LRT 三招手』的合演，注意里面对似然比的拿捏。先证每一步：(1) 化简——$L(x)=\exp\{2(X_1+X_2)-4\}$ 随 $X_1+X_2$ **单调递增**，所以比较 $L(x)>\xi$ 可换成一个更直接的比较 $X_1+X_2>\gamma$，把二维观测压成一维统计量；(2) 定标定界——在 $\mathrm{H}_0$ 下 $X_1+X_2\sim\mathcal N(0,2)$，$\frac{X_1+X_2}{\sqrt2}$ 才是标准正态，故取 $\gamma=\sqrt2\cdot1.645$（而非 $1.645$）——这个 $\sqrt2$ 是初学者最易漏的一步；(3) 反证——$1.645=\Phi^{-1}(0.95)$ 让弃真概率恰为 0.05。整段示范了『似然比→单调统计量→反解阈值』的机械流程，务必亲手算一遍。</span>

> <span style="color:#7f8c8d;">[原页此处源 OCR 有少量乱码] 上式中 $\gamma=\sqrt{2}\cdot 1.645$ 与拒绝域 $\{X_1+X_2>\sqrt{2}\cdot 1.645\}$ 的扫别在源 OCR 中被拆为 `γ=√2·1.645`、`1.645·…`、`=0.05`、`X1+X2>…` 等碎片，现按正态分位数 $\Phi^{-1}(0.95)=1.645$ 的语义忠实复原，未臆造其它数值。</span>

接下来求出误纳概率（false acceptance probability）。注意在 $\mathrm{H}_1$ 下，$X_1+X_2$ 服从均值为 $4$、方差为 $2$ 的正态分布，于是

```math
Z = \frac{X_{1} + X_{2} - 4}{\sqrt{2}} \sim \mathcal{N}(0,1)
```

是标准正态随机变量，据此即可把 $\beta$ 表达为 $\Phi$ 在相应节点之值——

<br>

> <span style="color:#7f8c8d;">衔接后续（Example 9.12 续）：本单元止于此例中途。在 $\mathrm{H}_1$ 下单变量 $Z=\big(X_{1}+X_{2}-4\big)/\sqrt{2}$ 为标准正态；利用 $X_1+X_2 \sim \mathcal{N}(4,2)$ 即可把误纳概率 $\beta=P\big(X_{1}+X_{2}\le \sqrt{2}\cdot 1.645;\, \mathrm{H}_{1}\big)$ 化为 $\Phi$ 在某分位点之值，并据此说明 LRT 在该两正态观测情形下取得最小的误纳概率。此后续内容属下一单元（书页 494 之后），本单元不再展开。</span>