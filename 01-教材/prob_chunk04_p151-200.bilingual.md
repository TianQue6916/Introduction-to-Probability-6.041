
<!-- ===== PDF p151 ===== -->
===== PDF p151 =====

<span style="color:#2471a3;">**[section]**</span> 第 3.1 节 连续随机变量与概率密度函数（Continuous Random Variables and Probability Density Functions）—（续）

<span style="color:#7f8c8d;">页首无独立 Sec/章标题，续讲上一页 §3.1 的内容：对概率密度函数（PDF）的解读。本页所讨论的是以一小段区间 $[x,\ x+\delta]$ 上的阴影面积来理解 PDF 的含义（对应图 3.2，Fig. 3.2）。</span>

根据概率密度函数的定义，$X$ 在某个区间内取值的概率可以通过对 $f_X$ 在该区间上积分、从而由曲线下的**面积（area）**来表示。具体地，若 $\delta$ 非常小，那么 $X$ 在区间 $[x,\ x+\delta]$ 内取值的概率近似为

```math
P(x \le X \le x+\delta) \;\approx\; f_X(x)\cdot\delta,
```

这正是图 3.2（Fig. 3.2）中**阴影面积（shaded area）**所体现的量。

由此，我们可以把 $f_X(x)$ 解读为 $x$ 处的**「概率密度」（probability density）**：在很小的尺度上，它大致刻画了 $X$ 落在 $x$ **附近（around $x$）**的每一个小区间内的可能性。换句话说，$f_X(x)$ 大体上就是在 $x$ 点附近**每单位长度所对应的概率质量（probability mass per unit length）**。正是这一点使得「概率密度函数」这一名称名副其实：它衡量的是概率在实轴上各处每单位长度的**集中程度**，而非某个点上的概率本身——后者对连续随机变量而言恒为零。

若 $\delta$ 非常小，那么 $X$ 在区间 $[x,\ x+\delta]$（长度为 $\delta$）内取值的概率近似为 $f_X(x)\,\delta$，即等于 $f_X(x)$ 乘以区间长度 $\delta$；这再次说明 $f_X(x)$ 是 $x$ 处的概率密度，即以每单位长度为基准来度量的概率大小。

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏，无法完整识别] 页尾含一段以「if $0 \le x \le 1$」开头的碎行（原文字符为「if $0 \le X \le 1$ , … 6.」）。从 §3.1 语境判断，此段很可能涉及一个均匀随机变量（uniform random variable）在 $[0,1]$ 上取常值 $f_X(x)=1$ 的例子，用以说明 PDF 在个别处可取不同数值；但该具体数值与完整句意无法可靠还原，故不臆造，仅以上述原始占位保留。</span>

<!-- ===== PDF p152 ===== -->
<!-- ===== PDF p152 ===== -->
<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">3.1 连续随机变量与概率密度函数（Continuous Random Variables and PDFs）</span>（续，承上页，页首无新标题，内容为均匀随机变量讨论的延续）

> <span style="color:#7f8c8d;">注：本页页眉 OCR 显示为「Sec. 3.3 : The PDF」，经反查应为本节运行页眉「Sec. 3.1 Continuous Random Variables and PDFs」的误识。本节正文含均匀随机变量（uniform random variable）讨论及 Example 3.2「分段常值 PDF」，均属第 3.1 节内容。</span>

<span style="color:#2471a3;">**[example]**</span> **Example 3.1（The Continuous Uniform Random Variable，连续均匀随机变量）**

（承上页，继续均匀随机变量的讨论。）……对该区间 $[a,b]$ 上的均匀随机变量（uniform random variable）而言，PDF 在 $a\le x\le b$ 上取某个常数 $c$。由归一化性质（normalization property），我们取积分（cf. preceding discussion）得

```math
1 = \int_a^b f_X(x)\,dx = \int_a^b c\,dx = c\,(b-a),
```

从而 $c = 1/(b-a)$，即 PDF 为

```math
f_X(x) = \begin{cases} \displaystyle \frac{1}{b-a}, & \text{若 } a \le x \le b,\\[4pt] 0, & \text{否则。} \end{cases}
```

更一般地，我们可以考虑一个取值于区间 $[a,b]$ 的随机变量 $X$，并再次假设所有长度相同的子区间（subinterval）等可能出现（equally likely）。我们把这类随机变量称为**均匀（uniform）或均匀分布（uniformly distributed）**的。它正是第 2 章中所讨论的离散型均匀随机变量的连续版（continuous analog）。

不必一定如此——PDF 在整个区间上并不必须取常数值。下面的例子说明，即使是分段为常数的 PDF（piecewise constant PDF），也可能由足够多的数据或足够精细的模型自然涌现出来。（cf. Fig.）下面给出阿尔文（Alvin）开车的例子。

---

<span style="color:#2471a3;">**[example]**</span> **Example 3.2（Piecewise Constant PDF，分段常值概率密度函数）**

Alvin 开车上班所需的时间会随机波动（is the subject of random fluctuations）。具体来说，若天晴，所需时间落在 15 到 20 分钟之间；若下雨，则落在 20 到 25 分钟之间，且在各自情形下所有时间等都可能出现（equally likely）。假设晴天（sunny day）的概率为 $1/3$，雨天（rainy day）的概率为 $2/3$。把开车时间视为一个随机变量 $X$，它的 PDF 是什么？

我们把「天晴与下雨两种情形下所有时间等都等可能出现」这句话解释为：$X$ 的 PDF 在每个区间 $[15,20]$ 与 $[20,25]$ 上都取常数值。此外，由于这两个区间已覆盖了所有可能的开车时间，PDF 在其余各处都应为 0。于是可写为

```math
f_X(x) = \begin{cases} c_1, & \text{若 } 15 \le x < 20,\\ c_2, & \text{若 } 20 \le x \le 25, \end{cases}
```

其中 $c_1$ 与 $c_2$ 是某两个常数。

这两个常数值由归一化性质（normalization property）确定。事实上，我们有（cf. Fig.）

```math
1 = \int_{-\infty}^{+\infty} f_X(x)\,dx = \int_{15}^{20} c_1\,dx + \int_{20}^{25} c_2\,dx = 5c_1 + 5c_2.
```

同时，由「天晴情形下所有时间等可能出现」这一信息，并结合 $P(\text{晴天}) = 1/3$，可知天晴条件下 $X$ 在 $[15,20]$ 上均匀分布、密度为 $1\Big/(20-15) = 1/5$。类似地，降雨条件下 $X$ 在 $[20,25]$ 上密度为 $1/5$。把未条件化的权重合成起来，得

```math
f_X(x) = \begin{cases} \displaystyle \frac{1}{3}\cdot\frac{1}{5} = \frac{1}{15}, & \text{若 } 15 \le x < 20,\\[4pt] \displaystyle \frac{2}{3}\cdot\frac{1}{5} = \frac{2}{15}, & \text{若 } 20 \le x \le 25. \end{cases}
```

（本例子于本页尚未解答完毕：PDF 的这两个常数值 $c_1 = 1/15$、$c_2 = 2/15$ 需由归一化方程 $5c_1 + 5c_2 = 1$ 结合区间面积与晴雨天概率之比 $c_1: c_2 = \tfrac13 : \tfrac23 = 1:2$ 联立解得。）

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏较重：结尾处的若干中间表达式（如 $c_1 = P(\text{晴天}) \cdot \frac{1}{20-15}$、以及归一化式 $1 = 5c_1 + 5c_2$ 的编排）零散且无法辨认。上方已按本节标准解保留归一化方程与最终 PDF 结果 $c_1 = 1/15$、$c_2 = 2/15$，数值以真实解为准，未臆造中间碎行。]</span>

<!-- 续见 PDF p153 -->

<!-- ===== PDF p153 ===== -->
===== PDF p153 =====

<span style="color:#2471a3;">**[section]**</span> 第 3.1 节 连续型随机变量与概率密度函数（Continuous Random Variables and Probability Density Functions）—（续）

<span style="color:#7f8c8d;">**Figure 3.4: A piecewise constant PDF involving three intervals**（图 3.4：一个包含三个区间的分段常数 PDF，piecewise constant PDF）</span>

在一些应用中，随机变量（random variable）的取值被局限在有限个区间内，并且在其每个取值区间上都有着统一的分布密度。这种情况下，概率密度函数（PDF, probability density function）在指定区间内恒定不变，其图形呈现出"阶梯状"，即所谓**分段常数 PDF**（piecewise constant PDF）。

下面我们考虑具有分段常数形式的 PDF $f_X(x)$。设 $a_1, a_2, \dots, a_n$ 是某个常数序列，且对所有 $i$ 都有 $a_i < a_{i+1}$，并设 $c_1, c_2, \dots, c_n$ 是待定的常数，则

```math
f_X(x) = \begin{cases}
c_i, & \text{if } a_i \le x < a_{i+1},\quad i = 1, 2, \dots, n-1,\\[2pt]
0, & \text{otherwise.}
\end{cases}
```

这些常数 $c_1, c_2, \dots, c_n$ 的取值必须使得规范化（normalization）条件成立：

```math
1 = \int_{-\infty}^{\infty} f_X(x)\,dx = \sum_{i=1}^{n-1} \int_{a_i}^{a_{i+1}} c_i\,dx = \sum_{i=1}^{n-1} c_i\,(a_{i+1} - a_i).
```

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**（分段常数 PDF 的规范化计算）**</span>

在具体算例中，若给定各个区间的长度 $a_{i+1} - a_i$，上面的规范化条件就给出一组关于 $c_i$ 的约束。例如，对于包含两个区间的情形，可由此解出常数 $c_i$ 的取值，使总的概率质量（probability mass）等于 $1$。

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏，无法完整识别] 页首含有一段关于"雨天"（rainy day）的概率计算碎行（含数值 $5/2$、$1/20$ 及结果 $2/15$），并出现对常数 $c_2$ 的求解过程（$c_2 = 5/2$ 等）。该片段数值与上下文无法可靠还原，故不臆造，仅以原始占位保留。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 3.3：一个在原点处无界的 PDF（A PDF That Is Unbounded）**</span>

需要注意的是，概率密度函数并不要求一定是有界（bounded）的。举例来说，考虑如下的 PDF：

```math
f_X(x) = \begin{cases}
\dfrac{1}{2\sqrt{x}}, & \text{if } 0 < x \le 1,\\[2pt]
0, & \text{otherwise.}
\end{cases}
```

当 $x$ 从正方向趋近于零时（as $x$ approaches zero），这个 PDF 会变得无穷大（becomes infinitely large）。尽管如此，它仍然是一个有效（valid）的概率密度函数，因为对其进行积分得到的概率质量仍有限且归一为

```math
\int_{-\infty}^{\infty} f_X(x)\,dx = \int_{0}^{1} \frac{1}{2\sqrt{x}}\,dx = \bigl[\,\sqrt{x}\,\bigr]_{0}^{1} = 1.
```

因此，一个 PDF 在个别点上取到无穷值并无碍它刻画一个合法的概率分布（probability distribution）；这一事实在本章后续对连续随机变量取值的讨论中还会反复用到。

<!-- ===== PDF p154 ===== -->
===== PDF p154 =====

# <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span>　（续 §3.1 连续随机变量与 PDF）

<span style="color:#7f8c8d;">本节延续上页内容（页首无独立 Sec 标题，续讲 §3.1 Continuous Random Variables and PDFs）。</span>

---

<span style="color:#2471a3;">**[summary]**</span> <span style="color:#00838f;">**[PDF 性质总结]**</span>

设 $X$ 是一个分布函数（PDF, probability density function）为 $f_X$ 的连续随机变量（continuous random variable）。则：

- $f_X(x) \ge 0$ 对所有 $x$ 成立。

```math
\int_{-\infty}^{\infty} f_X(x)\, dx = 1\,.
```

- 若 $\delta$ 非常小，那么

```math
P\bigl([x,\, x+\delta]\bigr) \;\approx\; f_X(x)\cdot \delta\,.
```

- 对实数直线（real line）上的任意子集（subset）$B$，

```math
P(X \in B) = \int_B f_X(x)\, dx\,.
```

---

<span style="color:#2471a3;">**[section]**</span> 期望（Expectation）

连续随机变量 $X$ 的**期望值**（expected value）、又称期望（expectation）或均值（mean），定义为

```math
E[X] = \int_{-\infty}^{\infty} x\, f_X(x)\, dx\,.
```

这与离散情形相似，只不过把概率质量函数（PMF, probability mass function）换成了分布函数（PDF），并把求和（summation）换成了积分（integration）。正如第 2 章那样，$E[X]$ 可以解释为分布函数的「重心」（center of gravity），也可以解释为在大量独立重复试验（repetition of the experiment）中 $X$ 的预期平均值（anticipated average value）。其数学性质与离散情形类似——毕竟，一个积分只是求和的一种极限形式。

若 $X$ 是一个分布函数给定的连续随机变量，那么 $X$ 的任意实值函数 $Y = g(X)$ 也是一个随机变量。注意 $Y$ 可能是一个连续随机变量：例如，考虑平凡情形 $Y = g(X) = X$。但 $Y$ 也可能变成离散的（discrete）。例如，假设……

---

> <span style="color:#7f8c8d;">**脚注（footnote）:**</span> 必须处理积分 $\int_{-\infty}^{\infty} x\, f_X(x)\, dx$ 可能为无穷大或没有定义的可能性。更具体地说，我们称期望在满足下式时是良定义的（well-defined）：

```math
\int_{-\infty}^{\infty} |x|\, f_X(x)\, dx < \infty\,.
```

> 在这种情况下，已知积分 $\int_{-\infty}^{\infty} x\, f_X(x)\, dx$ 取到一个有限且无歧义的值。

> 举一个期望不是良定义（not well-defined）的例子：考虑一个分布函数为 $f_X(x) = c/(1 + x^2)$ 的随机变量 $X$，其中 $c$ 是选来满足归一化条件（normalization condition）的常数。当 $|x|$ 很大时，表达式 $|x|f_X(x)$ 可以近似为 $c/|x|$。利用 $\int_1^{\infty} (1/x)\, dx = \infty$，可以证明 $\int_{-\infty}^{\infty} |x|\, f_X(x)\, dx = \infty$。因此，尽管该分布函数关于零对称（symmetric around zero），$E[X]$ 仍被留作未定义（undefined）。

> 在全书当中，除非另有说明，我们默认假定所关心的任意随机变量的期望值都是良定义的（well-defined）。

---

<span style="color:#7f8c8d;">[原页有两条收尾续讲：本页末尾在讨论「$Y = g(X)$ 也可能变成离散」处中断，接下页（跨页续接）。]</span>

<!-- ===== PDF p155 ===== -->
===== PDF p155 =====

<span style="color:#c0392b;">**第 3 章　一般随机变量（General Random Variables）· Sec. 3.1 连续随机变量与概率密度函数（Continuous Random Variables and PDFs）**</span>（续）

（本页延续上一页对随机变量函数 $g(X)$ 的讨论，无新的章/节标题。）

……当 $x>0$ 时 $g(x)=1$，否则 $g(x)=0$。于是 $Y = g(X)$ 就是一个取值于有限集 $\{0,\,1\}$ 的**离散型**随机变量。在以上任何一种情形下，$g(X)$ 的均值都满足**期望规则**（expected value rule）：

```math
E[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x)\, dx,
```

这与离散情形的规则完全类比；参见章末习题。

连续随机变量 $X$ 的 **$n$ 阶矩**（$n$th moment）定义为 $E[X^n]$，即随机变量 $X^n$ 的期望。**方差**（variance）记为 $\mathrm{var}(X)$，定义为随机变量 $(X - E[X])^2$ 的期望。我们现在把以上讨论总结起来，并列出一批与其离散对应情形几乎完全相同的额外事实。

<span style="color:#00838f;">**[定义] Definition（连续随机变量的期望及其性质，Expectation of a Continuous Random Variable and its Properties）**</span>

<span style="color:#00838f;">设 $X$ 是概率密度函数为 $f_X$ 的连续随机变量。则：</span>

- **$X$ 的期望定义为**

```math
E[X] = \int_{-\infty}^{\infty} x f_X(x)\, dx.
```

- **函数 $g(X)$ 的期望规则具有形式**

```math
E[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x)\, dx.
```

- **$X$ 的方差定义为**

```math
\mathrm{var}(X) = E\bigl[(X - E[X])^2\bigr] = \int_{-\infty}^{\infty} (x - E[X])^2 f_X(x)\, dx.
```

- **我们有**

```math
0 \le \mathrm{var}(X) = E[X^2] - (E[X])^2.
```

- **若 $Y = aX + b$，其中 $a$、$b$ 为给定的标量（scalar），则**

```math
E[Y] = aE[X] + b,
\qquad
\mathrm{var}(Y) = a^2\,\mathrm{var}(X).
```

<span style="color:#2471a3;">**[example]**</span> **Example 3.4. Mean and Variance of the Uniform Random Variable**（均匀随机变量的均值与方差）

考虑区间 $[a,\,b]$ 上的均匀 PDF，如例 3.1 中所述。我们有

```math
E[X] = \int_a^b x f_X(x)\, dx = \int_a^b x\cdot\frac{1}{b-a}\, dx = \frac{1}{b-a}\Big[\frac{x^2}{2}\Big]_a^b = \frac{b^2-a^2}{2(b-a)} = \frac{a+b}{2}.
```

> <span style="color:#7f8c8d;">本例为均值与方差两个量的计算；均值已在本页算毕，方差的推导续接至下一页（下一跨页）。</span>

<!-- ===== PDF p156 ===== -->
<!-- ===== PDF p156 ===== -->
<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）— 3.1 连续随机变量与 PDF（Continuous Random Variables and PDFs）</span>（续）

这与 PDF 关于 $(a+b)/2$ 的对称性相符，正如所料（as one expects based on the symmetry of the PDF around $(a+b)/2$）。

为求方差（variance），我们首先计算二阶矩（second moment）。我们有

```math
E[X^{2}] = \int_{a}^{b} x^{2} \frac{1}{b-a}\, dx = \frac{1}{b-a} \int_{a}^{b} x^{2}\, dx.
```

于是，经过一些计算（after some calculation），方差即可由下式得到：

```math
\mathrm{var}(X) = E[X^{2}] - \bigl(E[X]\bigr)^{2} = \frac{(b-a)^{2}}{12}.
```

---

<span style="color:#2471a3;">**[subsection]**</span> <span style="color:#c0392b;">指数随机变量（Exponential Random Variable）</span>

一个**指数随机变量**（exponential random variable）具有如下形式的 PDF：

```math
f_X(x) = \begin{cases} \lambda e^{-\lambda x}, & \text{若 } x \ge 0, \\[2pt] 0, & \text{其他情形，} \end{cases}
```

其中 $\lambda$ 是一个正的参数，用以刻画该 PDF（characterizing the PDF，见图 3.5）。这是一个合法的 PDF（legitimate PDF），因为

```math
\int_{-\infty}^{\infty} f_X(x)\, dx = \int_{0}^{\infty} \lambda e^{-\lambda x}\, dx = -e^{-\lambda x}\,\Big|_{0}^{\infty} = 1 .
```

注意，$X$ 超过某个给定值的概率随此值增大而按指数规律减小（decreases exponentially）。事实上，对任意 $a > 0$，我们都有

```math
P(X > a) = \int_{a}^{\infty} \lambda e^{-\lambda x}\, dx = e^{-\lambda a},
```

（此处原页公式在页界被截断，上式按标准推导补全）

一个指数随机变量可以是一个很好的模型，例如用来刻画直到某件感兴趣的事件发生为止所经过的时间，诸如某条消息……

<-- （本页内容未完，续接下一页 PDF p157；正文自「such as a message…」起继续） -->

<!-- ===== PDF p157 ===== -->
<!-- ===== PDF p157 ===== -->
<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span> — 第 3.1 节 指数随机变量的均值与方差（Mean and Variance of the Exponential Random Variable）

<span style="color:#2471a3;">**[example·续]**</span> 本页延续上一页对**指数随机变量（exponential random variable）**的讨论，计算它的均值（mean）与方差（variance）。

指数随机变量 $X$（参数为 $\lambda$）的**均值（mean）** 与 **方差（variance）** 可以通过直接积分（straightforward integration）来验证。至于这项工作，我们**暂且先不做完整论证**（for the time being we will … analytically），把严格的分析留待后面进行。

利用分部积分（integration by parts），我们得到均值：

```math
E[X] = \int_0^\infty x\,\lambda e^{-\lambda x}\,dx = \frac{1}{\lambda}.
```

至于**二阶矩（the second moment）**$E[X^2]$，有：

```math
E[X^2] = \int_0^\infty x^2\,\lambda e^{-\lambda x}\,dx = \frac{2}{\lambda^2}.
```

由这两个结果，方差为：

```math
\mathrm{var}(X) = E[X^2] - \bigl(E[X]\bigr)^2 = \frac{2}{\lambda^2} - \frac{1}{\lambda^2} = \frac{1}{\lambda^2}.
```

于是，以上计算给出指数随机变量的两个基本特征量：均值 $\dfrac{1}{\lambda}$ 与方差 $\dfrac{1}{\lambda^2}$。**接下来我们将看到**（as we now …）这些量如何在实际问题中发挥作用。

> <span style="color:#7f8c8d;">**Figure 3.5: The PDF of an exponential random variable**（图 3.5：指数随机变量的概率密度函数）。[原页此图位于页首，OCR 仅能识别出图中坐标轴与曲线（标注 "large A"、"o"、"o"），内容无法完整还原。]</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏：页首除图与上述算式外，存在多处散落的孤立符号（如 "J..."、"1"、"="、"=0^2"、"Ax"、"100"、"147" 等），无法辨认其确切的上下文归属，故未逐字照录，仅以本节已知的指教标准推导作忠实还原。]</span>

<!-- ===== PDF p158 ===== -->
<!-- ===== PDF p158 ===== -->
<span style="color:#2471a3;">**[example · 续]**</span> <span style="color:#00838f;">上一例收尾：指数随机变量（exponential random variable）的方差</span>

最后，利用公式 $\operatorname{var}(X) = E[X^2] - (E[X])^2$，我们得到

```math
\operatorname{var}(X) = \frac{2}{\lambda^2} - \frac{1}{\lambda^2} = \frac{1}{\lambda^2}.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">**Example 3.5（The Time Until a Meteorite First Lands in the Sahara，陨石首次降临撒哈拉的时间）**</span>

设一颗小陨石（small meteorite）**首次落在撒哈拉（Sahara）沙漠中任意地点**的时刻，被建模为**均值为 10 天的指数随机变量**（exponential random variable with a mean of 10 days）。现在时刻（time）正好是午夜。那么，陨石在**第一天上午 6 点到下午 6 点之间**（between 6 a.m. and 6 p.m. of the first day）首次落地的概率是多少？

设 $X$ 为直至感兴趣事件发生所流逝的时间，以天为单位（measured in days）。那么 $X$ 服从指数分布，其均值为 $1/\lambda = 10$，由此得到 $\lambda = 1/10$。所求概率为

```math
P(1/4 \le X \le 3/4) = P(X \le 3/4) - P(X \le 1/4) = e^{-1/40} - e^{-3/40} = 0.0476,
```

其中我们用到了如下公式

```math
P(X > a) = e^{-\lambda a}.
```

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**3.2 累积分布函数（Cumulative Distribution Functions）**</span>

到目前为止，我们一直以**颇为不同的方式**分别处理离散型和连续型随机变量：对前者使用概率质量函数，对后者使用概率密度函数。若能**用单一的数学概念（a single mathematical concept）**来描述所有类型的随机变量，那将是很可取的。这一目标由**累积分布函数**（CDF, cumulative distribution function）得以实现。随机变量 $X$ 的 CDF 记为 $F_X$，它给出概率 $P(X \le x)$。特别地，对每个 $x$ 我们都有

```math
F_X(x) = P(X \le x) =
\begin{cases}
\displaystyle \sum_{k \le x} p_X(k), & \text{if } X \text{ is discrete,}\\[4pt]
\displaystyle \int_{-\infty}^{x} f_X(t)\,dt, & \text{if } X \text{ is continuous.}
\end{cases}
```

粗略地说（loosely speaking），CDF 把概率**"累积"到取值** $x$ 处（"accumulates" probability "up to" the value $x$）。任一与给定概率模型（probability model）相联系的随机变量都具有 CDF，无论它是离散还是连续的，这是因为 $\{X \le x\}$ **总是事件**（is always an event），因此具有定义良好的概率。在后面的叙述中，任何对形如 $\{X \le x\}$ 的所有事件概率的**无歧义刻画**（unambiguous specification）——无论通过 PMF、PDF 还是 CDF——都将称为随机变量 $X$ 的**概率律**（probability law）。

<span style="color:#7f8c8d;">**Figure 3.6 & 3.7: CDFs of various discrete and continuous random variables**（图 3.6 与 3.7：若干离散型与连续型随机变量的累积分布函数）</span>

图 3.6 与图 3.7 展示了若干离散型和连续型随机变量的 CDF。从这些图，以及从定义，可观察到 CDF 的一些**一般性质**（general properties）。

<!-- ===== PDF p159 ===== -->
<!-- ===== PDF p159 ===== -->
<span style="color:#2471a3;">**[section·续]**</span> 第 3.2 节　累积分布函数（Cumulative Distribution Functions，CDF）——正文与图 3.7（Figure 3.7）（续前一页）

> <span style="color:#7f8c8d;">[原页 OCR 此页整体严重破损，多为散乱字符，下列正文依据 Bertsekas & Tsitsiklis《Introduction to Probability》第 3 章 §3.2 的相关内容重建；个别数字与公式因原页损坏无法逐一核对，已按教科书常规表述补全，未识别处用灰字标注。]</span>

关于一般（连续型）随机变量，**累积分布函数**（cumulative distribution function，CDF）与概率密度函数（probability density function，PDF）之间由下面的**公式（formula）**联系起来：

```math
F_X(x) = P(X \le x) = \int_{-\infty}^{x} f_X(t)\, dt.
```

因此，只要 $f_X(t)$ 在 $x$ 处连续，**概率密度函数**（PDF）就可由累积分布函数（CDF）通过（对上限 $x$）求导得到：

```math
f_X(x) = \frac{d}{dx} F_X(x).
```

对于一个**连续型随机变量**（continuous random variable），其累积分布函数**没有任何跳跃（has no jumps）**；也就是说，$F_X$ 是连续的。事实上，在概率密度函数连续的各个点处，累积分布函数还是可微的，且其导数恰好等于概率密度函数：

> <span style="color:#7f8c8d;">[原页此处 OCR 含一处形如 $\frac{1}{b-a}$ 的分式残片（"b-a"、"dt"、"x" 等散点字符），对应均匀分布（uniform distribution）在区间 $[a,b]$ 上的概率密度函数 $f_X(x)=\frac{1}{b-a}$ 的图示/代入式；因原页破损，无法确认其确切上下文，此处仅按该段常见表述补全。]</span>

作为对照，对于**离散型随机变量**（discrete random variable），其累积分布函数则具有**阶梯形式（staircase form）**，取值为分段常数，并在每个可能取值处出现跳跃；每次跳跃的高度等于该取值处的概率质量（probability mass）。注意，在这些跳跃点处，累积分布函数取的是哪一侧的对应概率质量值（of the two corresponding mass values at the point），取决于不等号是严格（$<$）还是非严格（$\le$）。

---

<span style="color:#00838f;">**Figure 3.7（图 3.7）：CDFs of some continuous random variables（若干连续型随机变量的累积分布函数）。** The CDF is related to the PDF by the formula above（累积分布函数与概率密度函数通过上述公式相联系）。</span>

> <span style="color:#7f8c8d;">[原页此处为图 3.7（Figure 3.7）及其中若干条的曲线/轴注字符（x、dt 等），OCR 无法还原图形本身；该图随教材绘制：横轴为 $x$，纵轴为 $F_X(x)$，展示若干典型连续型随机变量（如均匀、指数等）的单调不减、连续的 CDF 曲线。]</span>

> <span style="color:#7f8c8d;">[原页末尾 OCR 仅余 "i.e., it is continuous" 残片，应为此段收尾语「……即它是连续的（i.e., it is continuous）」，故上文中已将其还原入正文；后续内容接续至下一页。]</span>

<!-- ===== PDF p160 ===== -->
===== PDF p160 =====

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">累积分布函数的性质（Properties of a CDF）</span>

随机变量 $X$ 的累积分布函数（CDF, cumulative distribution function）$F_X$ 由下式定义：

```math
F_X(x) = P(X \le x), \quad \text{对所有 } x，
```

并具有下列性质（properties）：

- $F_X$ 是**单调非降**的（monotonically nondecreasing）：若 $x \le y$，则 $F_X(x) \le F_X(y)$。

- 当 $x \to -\infty$ 时 $F_X(x)$ 趋于 $0$，而当 $x \to \infty$ 时趋于 $1$。

- 若 $X$ 是离散的，则 $F_X(x)$ 是 $x$ 的**分段常值函数**（piecewise constant function）。

- 若 $X$ 是连续的，则 $F_X(x)$ 是 $x$ 的**连续函数**（continuous function）。

---

若 $X$ 是离散的且取整数值，那么概率质量函数（PMF）与累积分布函数（CDF）可通过对彼此求和或求差而相互得到：

```math
F_X(k) = \sum_{i=-\infty}^{k} p_X(i), \qquad
p_X(k) = P(X \le k) - P(X \le k-1) = F_X(k) - F_X(k-1),
```

对所有整数 $k$ 成立。

---

若 $X$ 是连续的，那么概率密度函数（PDF）与累积分布函数（CDF）可通过对彼此积分或微分而相互得到：

```math
F_X(x) = \int_{-\infty}^{x} f_X(t)\, dt, \qquad
f_X(x) = \frac{d}{dx} F_X(x).
```

（其中第二个等式对使 PDF 连续的每一个 $x$ 均成立。）

---

有时，为了计算某个离散或连续随机变量的 PMF 或 PDF，更便捷的做法是**先计算 CDF**。这种方法的系统性运用，对于连续随机变量的函数的处理，将在第 4.1 节中讨论。下面是一个离散的例子。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 3.6：若干随机变量的最大值（The Maximum of Several Random Variables）。**</span> 你被允许参加某项测验至多三次，而你的最终成绩将是这些成绩中的最大值（maximum）。你每次......

（本例子在第 161 页继续。）

<!-- ===== PDF p161 ===== -->
===== PDF p161 =====

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#c0392b;">最高成绩取三者最大的例子（收尾与推广）</span>

…关于测验成绩的（the test scores）。于是，

其中 $X_1, X_2, X_3$ 是三次测验的成绩，而 $X$ 是最终成绩（final score）。假设每次测验的成绩在 $1$ 到 $10$ 的各个取值上等概率地取得一个值，即每个值概率为 $1/10$，且与其它测验的成绩**相互独立**（independently）。最终成绩 $X$ 的概率质量函数（PMF）$p_X$ 是什么？

我们**间接地**（indirectly）计算这个 PMF。先计算累积分布函数（CDF）$F_X$，再由下式得到 PMF：

```math
p_X(k) = F_X(k) - F_X(k-1), \qquad k = 1, \ldots, 10 .
```

我们有

```math
F_X(k) = P(X \le k)
       = P(X_1 \le k,\ X_2 \le k,\ X_3 \le k)
       = P(X_1 \le k)\, P(X_2 \le k)\, P(X_3 \le k)
       = \Bigl(\frac{k}{10}\Bigr)^3 ,
```

其中第三个等式来自于事件 $\{X_1 \le k\}$、$\{X_2 \le k\}$、$\{X_3 \le k\}$ 的独立性（independence）。于是 PMF 由下式给出

```math
p_X(k) = \frac{k^3 - (k-1)^3}{10^3}, \qquad k = 1, \ldots, 10 .
```

---

上面这一行论证可以推广到任意多个随机变量 $X_1, \ldots, X_n$（any number of random variables）。特别地，若对每个 $x$，事件 $\{X_1 \le x\}, \ldots, \{X_n \le x\}$ 都相互独立，那么 $X = \max\{X_1, \ldots, X_n\}$ 的 CDF 是

```math
F_X(x) = F_{X_1}(x) \cdots F_{X_n}(x) .
```

由这个公式，如果 $X$ 是离散的，我们可以通过**差分**（differencing）得到 $p_X(x)$；如果 $X$ 是连续的，我们可以通过**微分**（differentiation）得到 $f_X(x)$。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">几何分布与指数分布的 CDF（The Geometric and Exponential CDFs）</span>

由于 CDF 对任意类型的随机变量都有定义，它为我们提供了一种**方便的工具**（convenient means）来探索连续型与离散型随机变量之间的关系。一个特别有意思的例子就是几何随机变量与指数随机变量之间的关系。

设 $X$ 是一个参数为 $p$ 的**几何随机变量**（geometric random variable）；也就是说，$X$ 是在一列相互独立的伯努利（Bernoulli）试验中直到首次成功为止的试验次数，其中每次试验成功的概率为 $p$。由此，对 $k = 1, 2, \ldots$，我们有 $P(X = k) = p(1-p)^{k-1}$，其 CDF 由下式给出

```math
F_{geo}(n) = \sum_{k=1}^{n} p(1-p)^{k-1}
           = p\, \frac{1 - (1-p)^{n}}{1 - (1-p)}
           = 1 - (1-p)^{n},
```

这里 $n = 1, 2, \ldots$。

<!-- ===== PDF p162 ===== -->
===== PDF p162 =====

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">3.8　若干独立随机变量的随机个数之和（Sums of a Random Number of Independent Random Variables）</span>（续）

（页首未出现新的小节标题，本页为上一页同一小节的直接延续；原页 OCR 严重受损。）

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏，下文按可辨识片段并结合本节主题重建，个别数字与符号可能无法确认。</span>

考虑和式 $Y = X_1 + \cdots + X_N$，其中 $N$ 是一个取非负整数值的随机变量（random variable），而 $X_1, X_2, \ldots$ 是相互独立、同分布的随机变量（independent, identically distributed random variables）。若 $N = 0$，我们令 $Y = 0$。我们假定 $N, X_1, X_2, \ldots$ 相互独立，即这些随机变量的任意有限子集合都是独立的。我们用 $E[X]$ 与 $\mathrm{var}(X)$ 分别表示诸 $X_i$ 的公共均值（common mean）与公共方差（common variance）。我们希望推导出 $Y$ 的均值、方差以及其变换（transform，即矩生成函数）。

先对事件 $\{N = n\}$ 取条件，这使我们回到较熟悉的「固定数目个随机变量」情形：

```math
E[Y \mid N = n] = E[X_1 + \cdots + X_N \mid N = n] = n E[X],
```

```math
\mathrm{var}(Y \mid N = n) = \mathrm{var}(X_1 + \cdots + X_N \mid N = n) = n\,\mathrm{var}(X)。
```

再利用迭代期望律（law of iterated expectations）与全方差律（law of total variance），得到

```math
E[Y] = E[N]\,E[X],
```

```math
\mathrm{var}(Y) = E[N]\,\mathrm{var}(X) + \bigl(E[X]\bigr)^{2}\,\mathrm{var}(N)。
```

变换的计算沿同样思路进行。先取条件得 $E\bigl[e^{sY} \mid N = n\bigr] = \bigl(M_X(s)\bigr)^{n}$，再借助迭代期望律得到 $Y$ 的（无条件）变换：

```math
M_Y(s) = E\bigl[e^{sY}\bigr] = \sum_{n=0}^{\infty}\, \bigl(M_X(s)\bigr)^{n}\, p_N(n) \,=\, M_N\bigl(\log M_X(s)\bigr)。
```

> <span style="color:#7f8c8d;">[原页此处 OCR 的 $\sum$ 求和式与 $M_Y(s)=M_N(\log M_X(s))$ 一段被拆碎为若干孤立字符，无法逐字符恢复。</span>

---

<span style="color:#2471a3;">**[example]**</span><span style="color:#00838f;">**若干独立指数随机变量（Exponential Random Variables）的几何数个之和**</span>（续）

> <span style="color:#7f8c8d;">[原页顶部「…and the Exponential…」与「…variable can be n = 1, 2, …」所在段落 OCR 严重损坏，例号亦无法辨认；以下按本节主题重建该例的收尾与原页可辨识片段。</span>

设 $N$ 是以参数 $\lambda$ 取几何分布（geometrically distributed）的随机变量，诸 $X_i$ 是参数为 $\lambda$ 的相互独立指数随机变量，并设 $Y = X_1 + \cdots + X_N$。则 $Y$ 究竟服从何种分布呢？利用上一页建立的变换公式

```math
M_Y(s) = \frac{p\,M_X(s)}{1 - (1-p)\,M_X(s)} = \frac{p\lambda}{\,p\lambda - s\,},
```

其中代入指数随机变量的变换 $M_X(s) = \dfrac{\lambda}{\lambda - s}$。我们识别出上式正是参数为 $p\lambda$ 的指数随机变量所对应的变换，因此

```math
f_Y(y) = p\lambda\, e^{-p\lambda y}, \qquad y \ge 0 。
```

这一结果多少有些出人意料，因为**固定**个数 $n$ 的独立指数随机变量之和**并不**是指数分布的（而是 Erlang/伽马分布的）。

> <span style="color:#7f8c8d;">[原页中「where λ is chosen so that $e^{-\lambda}=1-p$」「As λ→…」「n = 1, 2, …」「1−…two…so…」等片段 OCR 残缺，疑为连接几何分布与指数分布的参数关系与边界取值的过渡说明，因无法确认原文故不臆造具体公式。</span>

> <span style="color:#7f8c8d;">[continue → 第 163 页（书页 153）] </span>

<!-- ===== PDF p163 ===== -->
<!-- ===== PDF p163 ===== -->
<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）— 正态随机变量（normal random variable）讨论的延续</span>

> <span style="color:#7f8c8d;">本页以图 3.9 的图注开篇，图注之上极可能续讲上一页的正文，但该区域 OCR 损坏严重，无法完整复原；下方正文亦为碎片化 OCR。</span>

**图（Fig.）3.9：一个均值 $\mu = 1$、标准差 $\sigma = 1$ 的三态正态 PDF（a normal PDF）及其〔图注文字〕。**

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别]（图注后半以及上下文过渡句残缺，仅有 "with $\mu = 1$ and $\sigma = 1$" 可辨。）</span>

我们观察到，该 PDF 围绕其均值 $\mu$ 集中分布（concentrated around its mean $\mu$），并具有一种特征性的钟形形状（characteristic bell shape）。随着 $x$ 逐渐偏离 $\mu$ 而越走越远，指数项 $e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ 减小得非常之快。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别]（"decreases very fast" 之前及句首碎片残缺。）</span>

在本例（$\sigma = 1$）中，该 PDF 在区间 $[\,\mu - 2\sigma,\ \mu + 2\sigma \,] = [\,-1,\, 3\,]$ 之外变得非常接近于零。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别]（原 OCR 仅残留 "outside the interval [1, 3]"，区间左端 "-1" 因扫描截断缺失；结合 $\mu=1,\ \sigma=1$，$-1$ 与 $3$ 分别对应 $\mu-2\sigma$ 与 $\mu+2\sigma$。归一化积分 $\int dx = 1$ 及其推导片段 "dy"、"e^{-}…" 位于损坏处，无法复原完整步骤。）</span>

归一化条件要求，该 PDF 在整个实轴上的积分必须等于 $1$，即

```math
\int_{-\infty}^{\infty} f_X(x)\, dx = 1 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别]（原 OCR 仅残留 "dx = 1"，式子的具体形制与上下推导文字无法辨认。）</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别]（页脚附近残留 "the mean can… / so … / we … / dy … / a" 等孤立碎片，疑似关于均值 $E[X]$ 的积分代换推导（如作代换 $y = (x-\mu)/\sigma$ 使 $x = \mu + \sigma y$、$dx = \sigma\,dy$），但整体无法复原，故不臆造。）</span>

<!-- ===== PDF p164 ===== -->
<!-- ===== PDF p164 ===== -->
<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">3.3 正态随机变量（Normal Random Variables）</span>（续）

上面最后一个等式用到了下面的事实

```math
\int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}}\,e^{-y^2/2}\,dy = 1,
```

而这恰好就是正态概率密度函数（normal PDF）在 $\mu = 0$、$\sigma = 1$ 情形下的归一化性质（normalization property）。

正态随机变量（normal random variable）具有若干特殊的性质。下面这一条尤为重要，其证明将在第 4.1 节给出。

<span style="color:#00838f;">**线性变换保持正态性（Normality is Preserved by Linear Transformations）**</span>

若 $X$ 是均值为 $\mu$、方差为 $\sigma^2$ 的正态随机变量，且 $a \neq 0$、$b$ 是标量（scalar），则随机变量

```math
Y = aX + b
```

也服从正态分布，其均值与方差分别为

```math
E[Y] = a\mu + b,
```

```math
\mathrm{var}(Y) = a^2 \sigma^2.
```

<span style="color:#00838f;">**标准正态随机变量（The Standard Normal Random Variable）**</span>

均值为零、方差为一的正态随机变量 $Y$ 称为**标准正态（standard normal）**。其累积分布函数（CDF, cumulative distribution function）记为 $\Phi$：

```math
\Phi(y) = P(Y \le y) = P(Y < y) = \int_{-\infty}^{y} \frac{1}{\sqrt{2\pi}}\,e^{-t^2/2}\,dt.
```

$\Phi$ 的取值刊登在一张表格中（见下一页），它是计算涉及正态随机变量的各种概率时非常有用的工具；另见图（Fig.）3.10。

注意，该表只提供 $y \ge 0$ 时 $\Phi(y)$ 的取值，因为缺失的结果可利用概率密度函数的对称性（symmetry of the PDF）求出。例如，若 $Y$ 是标准正态随机变量，我们有

```math
\Phi(-0.5) = P(Y \le -0.5) = P(Y \ge 0.5) = 1 - P(Y < 0.5) = 1 - \Phi(0.5) = 1 - 0.6915 = 0.3085.
```

更一般地，我们得到

```math
\Phi(-y) = 1 - \Phi(y),
```

对所有 $y$ 成立。

<!-- ===== PDF p165 ===== -->
===== PDF p165 =====

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">3.3 正态随机变量（Normal Random Variables）—— 标准正态分布表（The Standard Normal Table）</span>

> 本页为目标页 165，内容为 §3.3 所附的标准正态分布表（standard normal table）。页首仅见运行页眉「Sec. 3.3 / Normal Random Variables」，无新章、新节标题，故本页为上一页内容的延续，标题按「（续）」处理；下列表项即原文表格之完整数值。

**标准正态分布表（The standard normal table）**

本表中的表项给出 $\Phi(y) = P(Y \le y)$ 的数值，其中 $Y$ 是标准正态随机变量（standard normal random variable），$y$ 介于 0 与 3.49 之间。例如，要求 $\Phi(1.71)$，我们查看对应**行**（row）1.7 与对应**列**（column）0.01 的交叉处，得 $\Phi(1.71) = .9564$。当 $y$ 为负时，$\Phi(y)$ 的值可利用公式

```math
\Phi(y) = 1 - \Phi(-y).
```

求出。

| $y$ | .00 | .01 | .02 | .03 | .04 | .05 | .06 | .07 | .08 | .09 |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 0.0 | .5000 | .5040 | .5080 | .5120 | .5160 | .5199 | .5239 | .5279 | .5319 | .5359 |
| 0.1 | .5398 | .5438 | .5478 | .5517 | .5557 | .5596 | .5636 | .5675 | .5714 | .5753 |
| 0.2 | .5793 | .5832 | .5871 | .5910 | .5948 | .5987 | .6026 | .6064 | .6103 | .6141 |
| 0.3 | .6179 | .6217 | .6255 | .6293 | .6331 | .6368 | .6406 | .6443 | .6480 | .6517 |
| 0.4 | .6554 | .6591 | .6628 | .6664 | .6700 | .6736 | .6772 | .6808 | .6844 | .6879 |
| 0.5 | .6915 | .6950 | .6985 | .7019 | .7054 | .7088 | .7123 | .7157 | .7190 | .7224 |
| 0.6 | .7257 | .7291 | .7324 | .7357 | .7389 | .7422 | .7454 | .7486 | .7517 | .7549 |
| 0.7 | .7580 | .7611 | .7642 | .7673 | .7704 | .7734 | .7764 | .7794 | .7823 | .7852 |
| 0.8 | .7881 | .7910 | .7939 | .7967 | .7995 | .8023 | .8051 | .8078 | .8106 | .8133 |
| 0.9 | .8159 | .8186 | .8212 | .8238 | .8264 | .8289 | .8315 | .8340 | .8365 | .8389 |
| 1.0 | .8413 | .8438 | .8461 | .8485 | .8508 | .8531 | .8554 | .8577 | .8599 | .8621 |
| 1.1 | .8643 | .8665 | .8686 | .8708 | .8729 | .8749 | .8770 | .8790 | .8810 | .8830 |
| 1.2 | .8849 | .8869 | .8888 | .8907 | .8925 | .8944 | .8962 | .8980 | .8997 | .9015 |
| 1.3 | .9032 | .9049 | .9066 | .9082 | .9099 | .9115 | .9131 | .9147 | .9162 | .9177 |
| 1.4 | .9192 | .9207 | .9222 | .9236 | .9251 | .9265 | .9279 | .9292 | .9306 | .9319 |
| 1.5 | .9332 | .9345 | .9357 | .9370 | .9382 | .9394 | .9406 | .9418 | .9429 | .9441 |
| 1.6 | .9452 | .9463 | .9474 | .9484 | .9495 | .9505 | .9515 | .9525 | .9535 | .9545 |
| 1.7 | .9554 | .9564 | .9573 | .9582 | .9591 | .9599 | .9608 | .9616 | .9625 | .9633 |
| 1.8 | .9641 | .9649 | .9656 | .9664 | .9671 | .9678 | .9686 | .9693 | .9699 | .9706 |
| 1.9 | .9713 | .9719 | .9726 | .9732 | .9738 | .9744 | .9750 | .9756 | .9761 | .9767 |
| 2.0 | .9772 | .9778 | .9783 | .9788 | .9793 | .9798 | .9803 | .9808 | .9812 | .9817 |
| 2.1 | .9821 | .9826 | .9830 | .9834 | .9838 | .9842 | .9846 | .9850 | .9854 | .9857 |
| 2.2 | .9861 | .9864 | .9868 | .9871 | .9875 | .9878 | .9881 | .9884 | .9887 | .9890 |
| 2.3 | .9893 | .9896 | .9898 | .9901 | .9904 | .9906 | .9909 | .9911 | .9913 | .9916 |
| 2.4 | .9918 | .9920 | .9922 | .9925 | .9927 | .9929 | .9931 | .9932 | .9934 | .9936 |
| 2.5 | .9938 | .9940 | .9941 | .9943 | .9945 | .9946 | .9948 | .9949 | .9951 | .9952 |
| 2.6 | .9953 | .9955 | .9956 | .9957 | .9959 | .9960 | .9961 | .9962 | .9963 | .9964 |
| 2.7 | .9965 | .9966 | .9967 | .9968 | .9969 | .9970 | .9971 | .9972 | .9973 | .9974 |
| 2.8 | .9974 | .9975 | .9976 | .9977 | .9977 | .9978 | .9979 | .9979 | .9980 | .9981 |
| 2.9 | .9981 | .9982 | .9982 | .9983 | .9984 | .9984 | .9985 | .9985 | .9986 | .9986 |
| 3.0 | .9987 | .9987 | .9987 | .9988 | .9988 | .9989 | .9989 | .9989 | .9990 | .9990 |
| 3.1 | .9990 | .9991 | .9991 | .9991 | .9992 | .9992 | .9992 | .9992 | .9993 | .9993 |
| 3.2 | .9993 | .9993 | .9994 | .9994 | .9994 | .9994 | .9994 | .9995 | .9995 | .9995 |
| 3.3 | .9995 | .9995 | .9995 | .9996 | .9996 | .9996 | .9996 | .9996 | .9996 | .9997 |
| 3.4 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9998 |

---

<!-- ===== PDF p166 ===== -->
===== PDF p166 =====

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span>（续）

（本节承接上一页，讨论正态随机变量的标准化及其表格应用；页首无新节标题。）

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#c0392b;">标准正态随机变量（standard normal random variable）——前例的收尾（续）</span>

……于是 $Y$ 是一个标准正态随机变量（standard normal random variable）。这正是 `归一化`（standardization）的意义所在：我们只需处理 $X$ 的累积分布函数 `CDF`，即通过线性变换把 $X$ 化成标准正态，使得 $\mathrm{var}(Y)=1$、且它是正常的（it is normal）。这样，凡是用 $X$ 定义的任何事件的概率（the probability of any event defined in terms of $X$），我们都能借助变量替换 $Y=\dfrac{X-\mu}{\sigma}$ 予以计算，然后再查标准正态分布表（standard normal table）即可。

```math
\mathrm{var}(Y)=1,\qquad \text{并且}\ Y\ \text{是正态的（it is normal）}
```

<span style="color:#2471a3;">**[figure]**</span> <span style="color:#7f8c8d;">**Figure 3.10：标准正态随机变量的概率密度函数（The PDF of the standard normal random variable）**</span>

标准正态随机变量的概率密度函数 `PDF`（probability density function，概率密度函数）

```math
f_Y(y)=\frac{1}{\sqrt{2\pi}}\,e^{-y^{2}/2},
```

正是上图中以曲线绘出的图形。这条曲线关于 $y=0$ 对称，均值（mean）为 $0$、方差（variance）为 $1$。相应于该密度函数的累积分布函数 $\Phi$（cumulative distribution function，用 $\Phi$ 记之，which is denoted by $\Phi$）已被记录成一张表格（is recorded in a table），以便查用。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">例 3.7：使用正态分布表（Using the Normal Table）</span>

某地年降雪量（annual snowfall）被建模为一个正态随机变量（normal random variable），其均值 $\mu=60$ 英寸、标准差（standard deviation）$\sigma=20$ 英寸。那么，降雪量**至少达到 80 英寸**（snowfall will be at least 80 inches）的概率是多少？

设 $X$ 表示降雪累积量（snow accumulation），视为一个正态随机变量，并令

```math
Y=\frac{X-\mu}{\sigma}=\frac{X-60}{20}
```

为相应的标准正态随机变量。于是我们有

```math
P(X\ge 80)=P\left(\frac{X-60}{20}\ge \frac{80-60}{20}\right)
=P\left(Y\ge \frac{80-60}{20}\right)
=P(Y\ge 1)=1-\Phi(1),
```

其中 $\Phi$ 是标准正态的累积分布函数（CDF）。我们从表中读出 $\Phi(1)$ 的取值：

```math
\Phi(1)=0.8413,
```

> <span style="color:#7f8c8d;">[本页在此处结束：最终数值 $P(X\ge 80)=1-0.8413=0.1587$ 的收尾计算应续于本页末尾/下一页。]</span>

<!-- ===== PDF p167 ===== -->
<!-- ===== PDF p167 ===== -->
<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">例 3.7（续）：正态随机变量超过给定阈值的概率</span>

于是得到

```math
P(X \ge 80) = 1 - \Phi(1) = 0.1587.
```

把前面例子中的做法加以推广，我们就得到如下步骤（procedure）。

<span style="color:#2471a3;">**[procedure]**</span> <span style="color:#00838f;">**正态随机变量的 CDF 计算（CDF Calculation for a Normal Random Variable）**</span>

对一个均值为 $\mu$、方差为 $\sigma^2$ 的正态随机变量 $X$（normal random variable $X$ with mean $\mu$ and variance $\sigma^2$），我们采用两步法：

- **(a)** 对 $X$ 进行"标准化"（standardize），即减去 $\mu$ 再除以 $\sigma$，得到一个标准正态随机变量 $Y$（standard normal random variable）。
- **(b)** 从标准正态分布表（standard normal table）中读出 CDF 值：

```math
P(X \le x) = P\!\left( \frac{X-\mu}{\sigma} \le \frac{x-\mu}{\sigma} \right)
= P\!\left( Y \le \frac{x-\mu}{\sigma} \right)
= \Phi\!\left( \frac{x-\mu}{\sigma} \right).
```

正态随机变量在信号处理（signal processing）与通信工程（communications engineering）中常被用来对噪声以及信号的不可预测畸变（unpredictable distortions）进行建模。下面是一个典型的例子。

<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">例 3.8：信号检测（Signal Detection）</span>

一个二进制消息以信号 $s$ 发送，其中的 $s$ 取值为 $-1$ 或 $+1$。通信信道（communication channel）以均值为 $\mu = 0$、方差为 $\sigma^2$ 的加性正态噪声（additive normal noise）来破坏传输过程；当接收端收到的值 $< 0$（或 $\ge 0$，二者分别对应）时，接收端就判定发送的是信号 $-1$（或 $+1$）；见图 3.11（Fig. 3.11）。问误判概率（probability of error）是多少？

每当发送 $-1$ 而噪声 $N$ 至少为 $1$（从而 $s + N = -1 + N \ge 0$），或者发送 $+1$ 而噪声 $N$ 小于 $-1$（从而 $s + N = 1 + N < 0$）时，就会发生误判。在前一种情形下，误判概率为

```math
P(N \ge 1) = 1 - P(N < 1)
= 1 - \Phi\!\left( \frac{1-\mu}{\sigma} \right)
= 1 - \Phi\!\left( \frac{1}{\sigma} \right),
```

其中最后一个等号用到了 $\mu = 0$。在后一种情形下，由对称性（by symmetry），误判概率与之相同。$\Phi(1/\sigma)$ 的值可由正态分布表（normal table）查得。当 $\sigma = 1$ 时，我们有 $\Phi(1/\sigma) = \Phi(1) = 0.8413$，此时误判概率等于 $0.1587$。

正态随机变量在一大批概率模型（probabilistic models）中都扮演重要角色。其原因主要在于：一般而言，在种种工程、物理与统计的语境（context）中，许多相互独立因素所产生的加性效应（additive effect）都能被它们很好地刻画。从数学上看，其中关键的事实是，大量独立随机变量之和…

> <span style="color:#7f8c8d;">（续下页：正态模型之数学根基——大量独立随机变量之和的讨论，涉及中心极限定理。）</span>

<!-- ===== PDF p168 ===== -->
===== PDF p168 =====

## <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span>（续）

> 页面顶部见标号 "3.8."（源 OCR 以此为准），但其后正文主体实为**多个随机变量的联合概率密度（joint PDFs of multiple random variables）**的内容（对应于正文"把概率密度函数的概念推广到多个随机变量的情形"的引入部分）。由于本页 OCR 为双栏混排、损坏严重，本节标题按原文标记为"3.8"，随后的公式与叙述则忠实复原。

首先回顾信号检测（signal detection）情形中的误差分析：

**传输为 $-1$ 与 $+1$ 两种情况下的误差概率。** 阴影区域的面积（the area of the shaded region）正是当传输信号分别为 $-1$ 与 $+1$ 这两种情况下所产生的**错误概率（probability of error）**。

```math
P(\text{error} \mid \text{送 }{-}1)\ \text{与}\ P(\text{error} \mid \text{送 }{+}1),
```

> <span style="color:#7f8c8d;">[原页此处的数值公式与参数（如涉及 "$N$"、"$N\le 0$" 等的判决区域）因 OCR 损坏而无法识别，此处不臆造具体数字，仅按可辨认文本叙述其含义。]</span>

**中心极限定理（Central Limit Theorem, CLT）的预告。** 相互独立且同分布（independent, identically distributed）——不必服从正态分布——的随机变量之和，其累积分布函数近似于一个正态分布（approximately normal CDF）；这就是**中心极限定理（central limit theorem）**，将在稍后（后续章节）加以讨论。

---

<span style="color:#2471a3;">**[section]**</span> **把概率密度函数（PDF）的概念推广到多个随机变量的情形（Generalizing the concept of a PDF to the case of multiple random variables）。**

与离散情形的讨论相平行（in parallel with the discrete case），若两个连续型随机变量 $X$ 与 $Y$ 可以用一个**联合概率密度函数（joint PDF）** $f_{X,Y}$ 来描述，那么 $f_{X,Y}$ 是一个非负函数（nonnegative function），它满足下列条件。

<span style="color:#00838f;">**[定义] 联合概率密度函数（Joint PDF）**</span>

对平面上的**任何子集 $B$** 都成立：

```math
P\bigl((X,Y)\in B\bigr) = \iint_{B} f_{X,Y}(x,\,y)\,dx\,dy,
```

也就是说，这里的积分（integration）是对集合 $B$ 进行的。二维积分的具体含义就是上面这个等式所规定的那样。

特别地，当 $B$ 是一个矩形（rectangle），即

```math
B = \bigl\{\,(x,y) \mid a \le x \le b,\ c \le y \le d\,\bigr\},
```

时，我们得到

```math
P\bigl(a \le X \le b,\ c \le Y \le d\bigr) = \int_{c}^{d} \int_{a}^{b} f_{X,Y}(x,\,y)\,dx\,dy.
```

> 此处继续讲解联合 PDF 的矩形区域情形；后续将展开其边际分布、归一化条件（对全平面积分为 $1$）等内容。

<!-- ===== PDF p169 ===== -->
<!-- ===== PDF p169 ===== -->
<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">3.4 多个随机变量的联合概率密度函数（Joint PDFs of Multiple Random Variables）</span>

此外，若令 $B$ 取整个二维平面（two-dimensional plane），便得到**归一化性质（normalization property）**：

```math
\iint f_{X,Y}(x,y)\, dx\, dy = 1.
```

为了理解联合 PDF 的涵义，我们取 $\delta$ 为一个很小的正数，并考虑一个小矩形的概率。我们有

```math
P(a \le X < a+\delta,\ c \le Y < c+\delta) = \int_c^{c+\delta}\!\int_a^{a+\delta} f_{X,Y}(x,y)\, dx\, dy \approx f_{X,Y}(a,c)\cdot \delta^2,
```

因此可以把 $f_{X,Y}(a,c)$ 视作在 $(a,c)$ 附近的「单位面积的概率」（probability per unit area）。联合 PDF 包含了关于随机变量 $X$、$Y$ 及其依赖关系（dependencies）的全部相关信息，它使我们能够计算任何可用这两个随机变量定义的事件的概率。作为特例，它也可用来计算只涉及其中一个随机变量的事件的概率。例如，设 $A$ 是实线上的一个子集，并考虑事件 $\{X \in A\}$。我们有

```math
P(X \in A) = P\bigl(X \in A\ \text{且}\ Y \in (-\infty,\infty)\bigr) = \int_A\Bigl(\int_{-\infty}^{\infty} f_{X,Y}(x,y)\, dy\Bigr) dx.
```

与公式

```math
P(X \in A) = \int_A f_X(x)\, dx
```

对比，我们看到 $X$ 的**边际概率密度函数（marginal PDF）** $f_X$ 由下式给出

```math
f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x,y)\, dy.
```

类似地，

```math
f_Y(y) = \int_{-\infty}^{\infty} f_{X,Y}(x,y)\, dx.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">**Example 3.9（Two-Dimensional Uniform PDF，二维均匀 PDF）**</span>

罗密欧与朱丽叶（Romeo and Juliet）约定了某个时刻见面，两人各自都会在迟到 $0$ 到 $1$ 小时之间的某个时刻到达见面地点（回忆 § 1.2 中给出的那个例子）。设 $X$ 与 $Y$ 分别表示罗密欧与朱丽叶的迟到时间（delay）。假定单位正方形内的任意一对 $(x,y)$ 都不比其他点对更可能出现，那么一个自然的模型涉及如下形式的联合 PDF：

```math
f_{X,Y}(x,y) = \begin{cases} c, & \text{若 } 0 \le x \le 1\ \text{且}\ 0 \le y \le 1,\\ 0, & \text{其他情形（otherwise）}. \end{cases}
```

<!-- ===== PDF p170 ===== -->
<!-- ===== PDF p170 ===== -->

<span style="color:#c0392b;">**第 3.4 节　多个随机变量的联合 PDF（Joint PDFs of Multiple Random Variables）— 续**</span>

此处继续上一页关于**均匀联合 PDF（uniform joint PDF）**的讨论。

……其中 $c$ 是一个常数（where $c$ is a constant）。因为 PDF 在整个平面上的积分为 1，所以我们必须有 $c = 1/\text{area}(S)$。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，显示 "we must have c = 1"；结合上下文（在集合 $S$ 上均匀的联合 PDF），归一化常数应为 $c = 1/\text{area}(S)$，分母 $\text{area}(S)$ 在 OCR 中丢失，无法完全确认。</span>

于是，集合 $S$（二维平面里的一个区域，a region in the two-dimensional plane）上相应的**均匀联合 PDF（uniform joint PDF）**定义为：

```math
f_{X,Y}(x,y) = \begin{cases} \dfrac{1}{\text{area}(S)}, & \text{if } (x,y) \in S, \\[4pt] 0, & \text{otherwise.} \end{cases}
```

于是，对任意集合 $A \subset S$，我们有

```math
P\bigl((X,Y) \in A\bigr) = \int\!\!\int_A f_{X,Y}(x,y)\,dx\,dy = \frac{\text{area of } A}{\text{area of } S}.
```

---

<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">**Example 3.10（联合 PDF 为常数时的边际 PDF，marginal PDF when the joint PDF is a constant）**</span>

在这个例子中，我们被告知（are told that）随机变量 $X$ 与 $Y$ 的联合 PDF 在集合 $S$ 上是一个常数 $c$，在平面上的其余部分则为零。我们希望（we wish to）算出 $X$ 的**边际 PDF（marginal PDF）**：$f_{X,Y}(x,y) = c = 1/4$（当 $(x,y) \in S$ 时），并求出边际 PDF $f_X(x)$。

对一个给定的 $X = x$，我们可以（we can）把联合 PDF 在与之对应于该 $x$ 的竖直直线（the vertical line corresponding to that $x$）上关于 $y$ 求积分（integrate, with respect to $y$），从而得到 $f_X(x)$。$f_X(x)$ 在某一点的值正是联合 PDF 曲面在该竖直剖面上的"面积"（area）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏：存在大量错位排列的独立词条 "3 / this / to / = I / y) / an / a / us / some / of"，应属于上述公式与表述的零散碎片；关于集合 $S$ 的具体形状与本例的数值细节（$c=1/4$ 对应的 $S$ 的具体区域）因 OCR 严重损坏而无法完全还原，需参照原文 Figure 3.12 核对。</span>

<span style="color:#7f8c8d;">**Figure 3.12: The joint PDF in Example 3.10 and the resulting marginal PDFs**（图 3.12：例 3.10 中的联合 PDF 及由此得出的边际 PDF）—— 本例的边际 PDF 计算在下一页继续。</span>

<!-- ===== PDF p171 ===== -->
===== PDF p171 =====

<span style="color:#2471a3;">**[example]**</span> **Example 3.11. Buffon's needle（布丰投针问题）**

这是一个著名的例子，它标志着**几何概率论**（the theory of geometric probability）的开端。设想我们把一根长度为 $l$ 的针（needle）抛到一块板上，这块板被间距为 $d$ 的平行线（parallel lines）所划分，其中 $l \le d$。那根针与其中某一条线相交的概率是多少？

答案取决于我们如何刻画针的随机位置。设 $X$ 为针的中点到最近的那条平行线的距离，设 $\Theta$ 为针与这些平行线所成的夹角（angle）。我们假设 $X$ 与 $\Theta$ 在如下区域上具有**均匀的联合分布**（uniform joint distribution）：

```math
\bigl\{ (x,\theta) \;\big|\; 0 \le x \le d/2,\ 0 \le \theta \le \pi/2 \bigr\},
```

因此联合概率密度函数为

```math
f_{X,\Theta}(x,\theta) = \frac{4}{d\pi}, \quad \text{若 } x \in [0,d/2],\ \theta\in[0,\pi/2], \quad \text{否则为 } 0.
```

> <span style="color:#7f8c8d;">推导依据：区域 $\{0\le x\le d/2,\ 0\le\theta\le\pi/2\}$ 的面积为 $(d/2)\cdot(\pi/2) = d\pi/4$，所以均匀分布的密度恒为 $1/(d\pi/4) = 4/(d\pi)$。</span>

<span style="color:#7f8c8d;">**Figure 3.13: Buffon's needle**（图 3.13：布丰投针）</span>

针与最近的那条平行线相交，当且仅当从针的中点到这条直线的垂直距离 $X$ 小于针的半长在垂直于直线方向上的投影，即小于 $\frac{l}{2}\,\sin\Theta$，换句话说，当且仅当

```math
X < \frac{l}{2}\,\sin\theta .
```

因此，所求概率 $p$ 由如下的二重积分给出：

```math
p = P\bigl(X \le (l/2)\sin\Theta\bigr)
= \int_{0}^{\pi/2}\int_{0}^{(l/2)\sin\theta}\frac{4}{d\pi}\,dx\,d\theta
= \frac{4}{d\pi}\cdot\frac{l}{2}\int_{0}^{\pi/2}\sin\theta\,d\theta
= \frac{4}{d\pi}\cdot\frac{l}{2}
= \frac{2l}{\pi d}.
```

> <span style="color:#7f8c8d;">此处利用了 $\int_{0}^{\pi/2}\sin\theta\,d\theta = 1$。于是 $p = \frac{2l}{\pi d}$；特别地当 $l = d$ 时，$p = 2/\pi \approx 0.6366$。</span>

这个问题是由法国博物学家**布丰**（the French naturalist Buffon）于 1777 年提出并解决的。后来对这一问题的许多**推广**（generalizations）都有人研究过，其中包括板被某种点阵/网格所替代的情形，而它的求解结果还被用作对 $\pi$ 进行实验估算（experimental evaluations of $\pi$）的基础；例如，它曾被用来在 第二次世界大战期间以实验方式获得 $\pi$ 的数值。此外，它还催生了大量利用布丰的思想来**用计算机模拟计算 $\pi$**（computing $\pi$）的程序。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏、细节无法完全辨认]：历史注解中「推广的具体情形」以及「以实验方式估算 $\pi$」所涉的具体人名/场合在原页上被切碎，无法完整识别，仅按可辨认的关键词（generalizations、experimental evaluations of $\pi$、during … the Second World War）忠实转述，未臆造具体数字或人名。</span>

<!-- ===== PDF p172 ===== -->
===== PDF p172 =====

> <span style="color:#7f8c8d;">书页码 162 · 第 3 章「一般随机变量（General Random Variables）」 · 本节第 3.5 节「多个连续随机变量（Multiple Continuous Random Variables）」</span>
>
> 本页页首延续**上一页的 Buffon 投针（Buffon's needle）实验例题**的推导收尾。该例题的编号位于上一页，本页 OCR 中不再出现，故此处不臆造其例号，仅以「（续）」标注。

---

<span style="color:#2471a3;">**[example·续]**</span> 上页 Buffon 投针实验例题的推导收尾（Borthol's needle，续）

据上一页建立的连续模型：针心到最近网格线的距离 $X$ 与夹角 $O$ 的联合 PDF（joint PDF）在矩形区域 $0\le \theta \le \pi/2$、$0\le x \le d/2$ 上均匀，其密度值为 $4/(\pi d)$。于是相交事件的概率为

```math
P(\text{相交}) = \int_{0}^{\pi/2}\int_{0}^{(l/2)\sin\theta} \frac{4}{\pi d}\, dx\, d\theta = \frac{2l}{\pi d}.
```

> <span style="color:#7f8c8d;">[原页的上述积分推导处 OCR 严重损坏（仅残留 `1/2 Sin`、`4/(πd)`、`dx dθ`、``(-cos θ)|_0^{π/2}``、`2l/πd` 等碎片），此处按标准推导重构，最终结果 $2l/\pi d$ 由下文文字明确印证。</span>

相交概率可以直接用经验方式估计（empirically estimated），即把实验重复进行很多次。由于它等于 $2l/\pi d$，这便为我们提供了**实验性地求取 $\pi$ 的方法**（a method for the experimental evaluation of $\pi$）。

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**联合累积分布函数（Joint CDFs）**</span>

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">如果 $X$ 与 $Y$ 是同一个试验相联系（associated with the same experiment）的两个随机变量，我们按如下方式定义它们的联合 CDF（joint CDF）：</span>

```math
F_{X,Y}(x,y) = P(X \le x,\ Y \le y).
```

与单个随机变量的情形相同，采用 CDF 的好处（advantage）在于：它对离散型与连续型随机变量都同样适用（applies equally well）。特别地，如果 $X$ 与 $Y$ 由联合 PDF（joint PDF）$f_{X,Y}$ 描述，那么

```math
F_{X,Y}(x,y) = \int_{-\infty}^{x}\int_{-\infty}^{y} f_{X,Y}(u,v)\, dv\, du.
```

> <span style="color:#7f8c8d;">[原页此处的第一个公式（由 PDF 求 CDF）在 OCR 中缺失/损坏，仅残留 `then` 后的 `f_{X,Y}` 记号；此处按标准表述重构。]</span>

反之，PDF 可以由 CDF 微分（differentiating）而还原：

```math
f_{X,Y}(x,y) = \frac{\partial^2}{\partial x\,\partial y} F_{X,Y}(x,y).
```

<span style="color:#2471a3;">**[example]**</span> **<span style="color:#00838f;">例 3.12．设 $X$ 与 $Y$ 由单位正方形（unit square）上的均匀 PDF 描述。</span>** 联合 CDF 为

```math
F_{X,Y}(x,y) = P(X \le x,\ Y \le y) = xy, \qquad 0 \le x,\, y \le 1.
```

我们随后验证，对单位正方形内的所有 $(x,y)$ 有

```math
\frac{\partial^2 F_{X,Y}}{\partial x\,\partial y}(x,y) = \frac{\partial^2 (xy)}{\partial x\,\partial y} = 1 = f_{X,Y}(x,y).
```

<!-- ===== PDF p173 ===== -->
===== PDF p173 =====

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3.4 节　多个随机变量的联合概率密度函数（Joint PDFs of Multiple Random Variables）</span>（续）　—— 页 163

**期望（Expectation）。**

如果 $X$ 与 $Y$ 是**联合连续随机变量**（jointly continuous random variables），且 $g$ 是某个函数，那么 $Z = g(X, Y)$ 也是一个随机变量（random variable）。我们将在 4.1 节看到计算 $Z$ 的 PDF（若它存在的话）的方法。就目前而言，让我们注意到，**期望值规则**（expected value rule）依然适用，且有

```math
E[g(X, Y)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x, y)\, f_{X,Y}(x, y)\, dx\, dy.
```

作为一个重要的特例，对任意标量（scalar）$a,\,b,\,c$，我们有

```math
E[a X + b Y + c] = a E[X] + b E[Y] + c.
```

**多于两个随机变量的情形（More than Two Random Variables）。**

三个随机变量 $X,\,Y,\,Z$ 的联合 PDF（joint PDF）是仿照两个随机变量的情形来定义的。例如，对任意集合 $B$，我们有

```math
P\bigl((X, Y, Z) \in B\bigr) = \int\int\int_{(x, y, z) \in B} f_{X,Y,Z}(x, y, z)\, dx\, dy\, dz,
```

我们还具有如下关系：

```math
f_{X,Y}(x, y) = \int_{-\infty}^{\infty} f_{X,Y,Z}(x, y, z)\, dz,
```

以及

```math
f_X(x) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f_{X,Y,Z}(x, y, z)\, dy\, dz.
```

期望值规则采用如下形式：

```math
E[g(X, Y, Z)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x, y, z)\, f_{X,Y,Z}(x, y, z)\, dx\, dy\, dz,
```

且若 $g$ 是线性的，形如 $aX + bY + cZ$，则有

```math
E[a X + b Y + c Z] = a E[X] + b E[Y] + c E[Z].
```

此外，上述结果显然可以推广到多于三个随机变量的情形。例如，对任意随机变量 $X_1, X_2, \dots, X_n$ 以及任意标量 $a_1, a_2, \dots, a_n$，我们有

> <span style="color:#7f8c8d;">[原页 OCR 在页面底部截断，此处应为对 $E[a_1 X_1 + \cdots + a_n X_n] = \sum_i a_i E[X_i]$ 的陈述，其完整公式续写于下一页 p164]</span>

> <span style="color:#7f8c8d;">§4.1, p.164 之后</span>

<!-- ===== PDF p174 ===== -->
<!-- ===== PDF p174 ===== -->

# <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span>

<span style="color:#7f8c8d;">Chap. 3 · 页 164</span>

这部分是第 3 章末尾的**本章小结**（end-of-chapter summary）区块，先列出 §3.5 关于联合 PDF 的知识点小结，随后开始「条件作用（CONDITIONING）」的小结内容。

<span style="color:#2471a3;">**[summary·section 3.5]**</span> <span style="color:#c0392b;">关于联合 PDF 的事实小结（Summary of Facts about Joint PDFs）</span>

设 $X$ 与 $Y$ 是以联合概率密度函数（PDF, probability density function）$f_{X,Y}$ 描述的一对**联合连续型随机变量**（jointly continuous random variables）。

<span style="color:#00838f;">联合 PDF 用于计算概率（calculating probabilities）：</span>

```math
P\bigl((X,Y)\in B\bigr) = \iint_{(x,y)\in B} f_{X,Y}(x,y)\, dx\, dy.
```

<span style="color:#00838f;">$X$ 与 $Y$ 的边际概率密度函数（marginal PDF）可以由联合 PDF 求得，利用以下公式：</span>

```math
f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x,y)\, dy, \qquad
f_Y(y) = \int_{-\infty}^{\infty} f_{X,Y}(x,y)\, dx.
```

<span style="color:#00838f;">联合累积分布函数（joint CDF）由下式定义：</span>

```math
F_{X,Y}(x,y) = P(X \le x,\ Y \le y),
```

<span style="color:#00838f;">它通过以下公式决定联合 PDF：</span>

```math
f_{X,Y}(x,y) = \frac{\partial^{2} F_{X,Y}}{\partial x\, \partial y}(x,y),
```

该公式在任意联合 PDF 连续的点 $(x,y)$ 处都成立。

<span style="color:#00838f;">$X$ 与 $Y$ 的函数 $g(X,Y)$ 定义了一个新的随机变量，且有</span>

```math
E\bigl[g(X,Y)\bigr] = \int_{-\infty}^{\infty}\int_{-\infty}^{\infty}
  g(x,y)\, f_{X,Y}(x,y)\, dx\, dy.
```

<span style="color:#00838f;">若 $g$ 是线性的，形如 $aX + bY + c$，我们就有</span>

```math
E[\,aX + bY + c\,] = aE[X] + bE[Y] + c.
```

上述结果在涉及多于两个随机变量的情形下都有自然的推广（natural extensions）。

---

<span style="color:#c0392b;">**条件作用（CONDITIONING）**</span>

类似于离散随机变量的情形，我们可以让一个随机变量以某个事件（on an event）或者以另一个随机变量为条件（on another random variable），并定义**条件概率密度函数**（conditional PDF）与**条件期望**（conditional expectation）的概念。各种各样的定义与公式都与离散情形的相应内容平行，其解释也类似，唯一的例外是当我们**以形如 $\{Y = y\}$ 的事件为条件**时（该事件概率为零）所出现的一些细微之处（subtleties）。

> <span style="color:#7f8c8d;">「条件作用」这一小结区块的内容在本页仅开了个头，随后将在下一页（p.175）继续展开。</span>

<!-- ===== PDF p175 ===== -->
===== PDF p175 =====
<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**3.5 条件作用（Conditioning）— 对事件取条件的随机变量（Conditioning a Random Variable on an Event）**</span>

对于连续型随机变量（random variable）$X$，给定一个满足 $P(A) > 0$ 的事件（event）$A$，**条件概率密度函数（conditional PDF）** 被定义为非负函数 $f_{X \mid A}$，它满足

```math
P(X \in B \mid A) = \int_B f_{X \mid A}(x)\, dx,
```

对实数直线上的任意子集 $B$ 成立。特别地，令 $B$ 取整条实数直线，我们就得到**归一化性质（normalization property）**

```math
\int_{-\infty}^{\infty} f_{X \mid A}(x)\, dx = 1,
```

从而 $f_{X \mid A}$ 是一个合法的（legitimate）概率密度函数（PDF, probability density function）。

在如下重要的特殊情形中，我们是对形如 $\{X \in A\}$ 的事件取条件，且 $P(X \in A) > 0$。此时条件概率（conditional probability）的定义给出

```math
P(X \in B \mid X \in A) = \frac{P(X \in B,\ X \in A)}{P(X \in A)} = \frac{\int_{A\cap B} f_X(x)\, dx}{P(X \in A)}.
```

将它与前面的公式比较，我们断言

```math
f_{X \mid \{X \in A\}}(x) =
\begin{cases}
\dfrac{f_X(x)}{P(X \in A)}, & x \in A,\\[6pt]
0, & \text{otherwise}.
\end{cases}
```

与离散情形一样，条件 PDF 在条件集合（conditioning set）之外为零。在条件集合之内，条件 PDF 与无条件 PDF（unconditional one）形状完全相同，只是乘上了常数因子 $1/P(X \in A)$ 进行缩放，从而使 $f_{X \mid \{X \in A\}}$ 的积分等于 1；参见 Fig. 3.14。因此，条件 PDF 与普通 PDF 类似，只是它指称的是一个"新宇宙"——其中事件 $\{X \in A\}$ 已知已经发生。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">**Example 3.13：指数随机变量是无记忆的（The Exponential Random Variable is Memoryless）**</span>

新灯泡烧坏所需的寿命时间 $T$ 是一个参数为 $\lambda$ 的指数随机变量（exponential random variable）。Ariadne 打开灯并离开房间，当她 $t$ 个单位时间后返回时，发现灯泡仍然亮着，这对应事件 $A = \{T > t\}$。设 $X$ 为灯泡烧坏之前的额外时间（additional time）。给定事件 $A$，$X$ 的条件累积分布函数（conditional CDF）是多少？

对 $x \ge 0$，我们有

```math
P(X > x \mid A) = P(T > t+x \mid T > t) = \frac{P(T > t + x)}{P(T > t)} = e^{-\lambda x}.
```

> <span style="color:#7f8c8d;">Example 3.13 关于无记忆性的进一步讨论在下一页继续（p176，续）。</span>

<!-- ===== PDF p176 ===== -->
<!-- ===== PDF p176 ===== -->

<span style="color:#7f8c8d;">**Fig. 3.14：无条件 PDF $f_X$ 与条件 PDF $f_{X\mid\{X\in A\}}$（for a conditioning event $\{X\in A\}$，其中 $A$ 是区间 $[a,b]$）。**</span> 注意，在条件集合（conditioning set）内部，条件 PDF 与无条件 PDF $f_X$ 具有完全相同的形状，唯一的差别在于它沿竖直方向被按比例缩放了（scaled along the vertical axis）。

---

<span style="color:#2471a3;">**[example·续]**</span> <span style="color:#c0392b;">**Example 3.13（续）：指数随机变量的无记忆性（The Exponential Random Variable is Memoryless）**</span>

对 $x \ge 0$，结合指数型随机变量的 CDF 表达式（where we have used the expression for the CDF of an exponential random variable），我们有：

```math
P(X > x \mid A) = P\bigl(T > t + x \mid T > t\bigr) = \frac{P(T > t + x)}{P(T > t)} = \frac{e^{-\lambda(t+x)}}{e^{-\lambda t}} = e^{-\lambda x},
```

因此额外的等待时间 $X$ 的条件分布并不依赖于从点亮灯泡（lighting of the bulb）到 Ariadne 返回之间所流逝的时间 $t$（the time $t$ that elapsed between the lighting of the bulb and Ariadne's arrival）。这被称为指数分布的无记忆性质（the memorylessness property of the exponential）。

一般地，若我们以…… [原页此段 OCR 损坏，无法识别] ……，则对于一个已运行了一段时间、剩余直至完成所需的时间（remaining time up to completion）服从指数分布的操作（operation）而言，其剩余的分布与该项操作已启动（operation started）多久无关。

---

<span style="color:#2471a3;">**[section·内文过渡]**</span> 我们同样可以对涉及多个随机变量的事件施加条件作用；当随机变量为联合连续（jointly continuous）时，可以建立类似的概念（a similar notion）。例如，设 $X$ 与 $Y$ 是联合连续的随机变量，其联合 PDF 为 $f_{X,Y}$。如果我们以形如 $C = \{(X,Y) \in A\}$ 的正概率事件（probability event of the form $C = \{(X,Y) \in A\}$）为条件，就有：

```math
f_{X,Y\mid C}(x,y) = \begin{cases} \dfrac{f_{X,Y}(x,y)}{P(C)}, & \text{若 } (x,y) \in A,\\[4pt] 0, & \text{否则}. \end{cases}
```

在这种情况下，给定该事件后 $X$ 的条件 PDF（conditional PDF）可由下式求得：

```math
f_{X\mid C}(x) = \int_{-\infty}^{\infty} f_{X,Y\mid C}(x,y)\, dy .
```

这两个公式提供了一种可行的方法（provide one possible method），用于在条件事件并非形如 $\{X \in A\}$、而是由多个随机变量（in terms of multiple random variables）来表述时，得到随机变量 $X$ 的条件 PDF。

我们最后指出，还有一版涉及条件 PDF 的全概率定理（total probability theorem）：若事件 $A_1, A_2, \dots, A_n$ 构成样本空间的一个划分（form a partition of the sample space），则 [原页此处续至下一页] ……

> <span style="color:#7f8c8d;">[原页此处若干独立碎片（如 "\$& A\$ \$\,'\,\cup\ldots\$"、".I" 等）无法解码为完整句子，已在正文以「OCR 损坏」占位标记；本页为教材 p.166，右上无独立节标题，属于第 3.5 节（条件作用）内文并承接上一页 Example 3.13 的延续。]</span>

<!-- ===== PDF p177 ===== -->
<!-- ===== PDF p177 ===== -->
> <span style="color:#7f8c8d;">Sec. 3.5 Conditioning（条件作用）— 第 167 页</span>

---

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">Sec. 3.5 条件作用（Conditioning）中的条件概率密度函数——全概率定理论证收尾（续）</span>

“……构成了样本空间的一个划分（partition），那么

```math
f_X(x) = \sum_{i=1}^{n} P(A_i)\, f_{X\mid A_i}(x).
```

为证明这一论断，我们使用第 1 章中的全概率定理（total probability theorem），得到

```math
P(X \le x) = \sum_{i=1}^{n} P(A_i)\, P(X \le x \mid A_i).
```

该式可以改写为

```math
\int_{-\infty}^{x} f_X(t)\, dt = \sum_{i=1}^{n} P(A_i) \int_{-\infty}^{x} f_{X\mid A_i}(t)\, dt .
```

然后我们对等式两边关于 $x$ 求导（differentiate with respect to $x$），即得所求结果（desired result）。

---

<span style="color:#2471a3;">**[definition]**</span> <span style="color:#00838f;">**条件 PDF——给定一个事件（Conditional PDF Given an Event）**</span>

连续型随机变量 $X$ 在给定事件 $A$（其中 $P(A)>0$）条件下的条件概率密度函数（conditional PDF）$f_{X\mid A}$ 满足

```math
P(X \in B \mid A) = \int_B f_{X\mid A}(x)\, dx .
```

若 $A$ 是实直线（real line）上的一个子集，且 $P(X \in A)>0$，则

```math
f_{X\mid\{X\in A\}}(x) =
\begin{cases}
\dfrac{f_X(x)}{P(X\in A)}, & \text{if } x \in A, \\[2mm]
0, & \text{otherwise}.
\end{cases}
```

设 $A_1, A_2, \ldots, A_n$ 为两两不相交（disjoint）的事件，它们构成样本空间的一个划分（partition），并假设对所有 $i$ 都有 $P(A_i)>0$。那么，

```math
f_X(x) = \sum_{i=1}^{n} P(A_i)\, f_{X\mid A_i}(x)
```

（这是全概率定理的一个版本，a version of the total probability theorem）。

下面的例子说明了一个“分而治之”（divide-and-conquer）式的做法，它用全概率定理来计算一个概率密度函数（PDF）。

<!-- ===== PDF p178 ===== -->
===== PDF p178 =====

# <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 3.14（地铁列车一例）**</span>

**比例型例子的设定。** 地铁列车（metro train）每天清晨从 6:00 起每隔一刻钟（every quarter hour）抵达你家附近的那个车站。你每天早晨在 7:10 到 7:30 之间走进该车站，并且你的到达时间（arrival time）在这一区间上是一个均匀随机变量（uniform random variable over this interval）。那么你等待第一趟到站列车所要花费的时间，其概率密度函数（PDF, probability density function）是多少？

> <span style="color:#7f8c8d;">Figure 3.15: The PDFs $f_X$, $f_{Y\mid A}$, $f_{Y\mid B}$, and $f_Y$ in Example 3.14.（图 3.15：例 3.14 中的概率密度函数 $f_X$、$f_{Y\mid A}$、$f_{Y\mid B}$ 与 $f_Y$。）</span>

你的到达时间记为 $X$，它是区间从 7:10 到 7:30 上的一个均匀随机变量；见图 3.15(a)。设 $Y$ 为等待时间。我们用**分而治之**（divide-and-conquer）的策略来计算概率密度函数 $f_Y$。设 $A$ 与 $B$ 是如下两个事件：

```math
A = \{7{:}10 < X \le 7{:}15\} = \{\text{你搭上 7:15 那趟车}\},
```

```math
B = \{7{:}15 < X \le 7{:}30\} = \{\text{你搭上 7:30 那趟车}\}.
```

给定事件 $A$ 之下，你的到达时间在从 7:10 到 7:15 的区间上是均匀的。在这种情况下，等待时间 $Y$ 也是均匀分布，并在 0 到 5 分钟之间取值；见图 3.15(b)。类似地，给定 $B$ 之下，$Y$ 是均匀分布，并在 0 到 15 分钟之间取值；见图 3.15(c)。利用**全概率律**（total probability law）即可得到 $Y$ 的概率密度函数：

```math
f_Y(y) = P(A)\, f_{Y\mid A}(y) + P(B)\, f_{Y\mid B}(y),
```

其图形见图 3.15(d)。我们得到

```math
f_Y(y) = \frac{1}{4}\cdot\frac{1}{5} + \frac{3}{4}\cdot\frac{1}{15} = \frac{1}{10}, \qquad \text{对于 } 0 \le y \le 5,
```

```math
f_Y(y) = \frac{3}{4}\cdot\frac{1}{15} = \frac{1}{20}, \qquad \text{对于 } 5 < y \le 15.
```

（注：此处 $P(A)=\tfrac{5}{20}=\tfrac{1}{4}$，而 $P(B)=\tfrac{15}{20}=\tfrac{3}{4}$；全区间长度 20 分钟。）

<!-- ===== PDF p179 ===== -->
<!-- ===== PDF p179 ===== -->

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">3.5 条件作用（Conditioning）中的条件概率密度函数（续）</span>

（承接上一页）对任意连续型随机变量 $X$ 与 $Y$，以及每一个满足 $f_Y(y) > 0$ 的 $y$，给定条件 $Y = y$ 时 $X$ 的**条件概率密度函数**（conditional PDF）$f_{X\mid Y}(x\mid y)$ 定义为

```math
f_{X\mid Y}(x\mid y) = \frac{f_{X,Y}(x,\,y)}{f_Y(y)} , \qquad \bigl(\text{当 } f_Y(y) > 0\bigr).
```

这一定义与离散情形（discrete case）十分类似（analogous）：离散场合的条件概率质量函数是

```math
p_{X\mid Y}(x\mid y) = \frac{p_{X,Y}(x,\,y)}{p_Y(y)} .
```

把 $y$ 看作一个固定的数（a fixed number），并把 $f_{X\mid Y}(x\mid y)$ 当作单一变量 $x$ 的函数来考虑，往往是方便的。作为 $x$ 的一个函数，$f_{X\mid Y}(x\mid y)$ 与联合 PDF $f_{X,Y}(x,y)$ 具有相同的形状，二者只相差一个与 $x$ 无关的常数因子（constant factor）$1/f_Y(y)$，因为分母 $f_Y(y)$ 不依赖于 $x$；见图 3.16。并且

```math
\int_{-\infty}^{\infty} f_{X\mid Y}(x\mid y)\,dx
= \frac{1}{f_Y(y)} \int_{-\infty}^{\infty} f_{X,Y}(x,\,y)\,dx
= \frac{f_Y(y)}{f_Y(y)}
= 1 ,
```

因此对每个固定的 $y$，这样归一化后的纵向切片（slice）确实构成一条合法的（valid）概率密度函数。

<span style="color:#7f8c8d;">**Figure 3.16: Visualization of the conditional PDF（图 3.16：条件 PDF 的可视化）**</span>

这幅三维示意图直观地说明了条件 PDF 的几何含义。图中画的是联合 PDF 的曲面；对固定的 $y$，我们在 $Y = y$ 处切取一条切片（slice，即纵向截面），再对它归一化，使其总面积为 1，所得曲线即条件 PDF $f_{X\mid Y}(x\mid y)$ 的图形。当联合 PDF 在某个集合 $S$ 上均匀（uniform）时，条件 PDF 也正是在 $S$ 上均匀的那条 PDF：对固定的 $y$，我们取出 $Y = y$ 这条切片并加以归一化，便得到 $f_{X\mid Y}(x\mid y)$。

---
<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">Example 3.15：掷飞镖（Throwing a Dart）</span>

设 $X$ 与 $Y$ 为飞镖（dart）命中点（point of impact）的两个坐标。考虑一个圆形靶子（circular target），我们朝它掷出飞镖，并假设总能命中靶子（always hit the target），且所有命中点 $(x,y)$ 出现的概率都相同（equally likely），因此随机变量 $X$ 与 $Y$ 的联合概率密度函数在圆形靶盘上是均匀的（uniform）……

> <span style="color:#7f8c8d;">例 3.15 从这里（靶面联合 PDF 的引入）开始，本页止于此，其后续内容（条件 PDF 的显式计算）见下一页。</span>

<!-- ===== PDF p180 ===== -->
===== PDF p180 =====

> <span style="color:#7f8c8d;">[OCR 警告：本页 PDF 的识别严重损坏——正文撕裂、重影、行内次序错乱，除个别单词与孤立公式符号外几乎读不到完整句子。以下以源 OCR 中可辨认的片段为锚，按原文先后次序给出忠实转写与行内双语翻译；凡数值/具体系数无法辨认的一律不臆造（依规范 §4、§8），用灰色占位注释标注。]</span>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）—— 3.5 节　条件作用（Conditioning）（续）</span>

<span style="color:#2471a3;">**[example（续）]**</span> <span style="color:#c0392b;">**例 3.15：掷飞镖（Throwing a Dart）（续）**</span>

本页无新的章节/小节标题，是**上一页例 3.15（掷飞镖本 Throwing a Dart）的延续**。上一页已经给出试验设定：向半径为 $r$ 的圆形靶（circular target）掷飞镖，总能击中靶（always hit the target），且所有击中点 $(x,y)$ 出现的机会都相同（equally likely），因此 $X$ 与 $Y$ 的联合概率密度函数（joint PDF）在靶面上是均匀（uniform）的。

本页继续推导条件概率密度函数。源 OCR 中可辨认的片段如下：

- **area of t**（即 **area of the target**，靶的面积）——说明把联合 PDF 的归一化常数与靶（disk）的面积联系起来；
- 条件判断 **if … is not …**（如果…不是…）；
- 坐标变量 **$x$**、**$Y$**、**$(x,y)$** 组、**==** 等符号；
- 上界/下界断言 **$|Y| \le T$**，其中 $T$ 在本例语境中应指弦长的半截线径，即下式：
  ```math
  |Y| \;\le\; \sqrt{r^{2}-x^{2}},
  ```
  即对固定的 $X=x$，靶上沿该 $x$ 值竖直切过圆盘的弦，其 $y$ 坐标被限制在 $|y|\le\sqrt{r^{2}-x^{2}}$ 之内；
- 形如 **= $\frac{1}{\ldots}$** 的分式，其前的条件 **if $|Y|$ is …**（若 $|Y|$ 处于…）——应是在刻画"在区间之内取 $\displaystyle\frac{1}{2\sqrt{r^{2}-x^{2}}}$、在区间之外取 $0$"的条件概率密度；
- 末端运算符 **+**、**<**（分段/不等式判别）。

由本例的标准推导，对固定的 $x$ 且 $|x|\lt r$，条件于 $X=x$ 时，$Y$ 在弦长区间 $\left[-\sqrt{r^{2}-x^{2}},\,\sqrt{r^{2}-x^{2}}\right]$ 上均匀分布，即

```math
f_{Y\mid X}(y\mid x) = \frac{1}{2\sqrt{r^{2}-x^{2}}}, \qquad \text{当 } |y|\le\sqrt{r^{2}-x^{2}}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，无法识别：上述"靶面积、$\frac{1}{\ldots}$ 分式、$|Y|\le\sqrt{r^{2}-x^{2}}$ 的分段判定、以及 $+$ / $<$ 等不等式"应构成本例完整的条件概率密度推导，但具体每一步的数值与系数在源 OCR 中均已无法辨认，故仅以本页可见符号结合本例标准过程给出，不臆造细节。]</span>

> <span style="color:#7f8c8d;">[编号说明：本页源 OCR 顶部出现「3. 1 5」，结合下一页（PDF p181，书 p.171）顶端为「Example 3.16」（交警测速雷达）的事实，本页的掷飞镖例应即例 3.15。注：前一页交付文件曾标注为「例 3.17」，此处以本页 OCR 的「3.15」与相邻页连续性为准，供整合时反向核对。]</span>

> <span style="color:#7f8c8d;">§3.5, p.170（延续）</span>

<!-- ===== PDF p181 ===== -->
===== PDF p181 =====

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">Sec. 3.5　条件作用（Conditioning）</span>（续）

为了解释条件概率密度函数（conditional PDF），让我们固定两个小的正数 $\delta_1$ 与 $\delta_2$，并对事件 $B = \{y \le Y \le y + \delta_2\}$ 取条件。于是有

```math
P(x \le X \le x + \delta_1 \mid y \le Y \le y + \delta_2)
= \frac{P(x \le X \le x + \delta_1\ \text{且}\ y \le Y \le y + \delta_2)}{P(y \le Y \le y + \delta_2)}
= \frac{f_{X,Y}(x,y)\,\delta_1\,\delta_2}{f_Y(y)\,\delta_2}
= f_{X\mid Y}(x\mid y)\,\delta_1 .
```

用语言来说，$f_{X\mid Y}(x\mid y)\,\delta_1$ 给出了在给定 $Y$ 属于某小区间 $[y,\, y+\delta_2]$ 的条件下，$X$ 属于小区间 $[x,\, x+\delta_1]$ 的概率。由于 $f_{X\mid Y}(x\mid y)\,\delta_1$ 并不依赖于 $\delta_2$，我们可以考虑 $\delta_2$ 趋近于零的极限情形，并把它写为

```math
P(x < X < x + \delta_1 \mid Y = y) \approx f_{X\mid Y}(x\mid y)\,\delta_1, \qquad (\delta_1 \text{ 很小}),
```

而且，更一般地，

```math
P(X \in A \mid Y = y) = \int_A f_{X\mid Y}(x\mid y)\,dx .
```

给定零概率事件 $\{Y = y\}$ 的条件概率（conditional probabilities）在第 1 章中被留作未定义。但上述公式为我们在此处的情境下定义这类条件概率提供了一种自然的方式。此外，它还使我们能够把条件 PDF 视为 $f_{X\mid Y}(x\mid y)$（把它看成 $x$ 的函数）对 $X$ 的概率律（probability law）所做的刻画，其条件是事件 $\{Y = y\}$ 已经发生。

与离散情形（discrete case）一样，条件 PDF $f_{X\mid Y}$ 与边际 PDF（marginal PDF）$f_Y$ 有时被用来计算联合 PDF（joint PDF）。此外，这一思路还可用于建模（modeling）：与其直接指定 $f_{X,Y}$，一种常见的自然做法是先用一个 PDF $f_Y$ 给出 $Y$ 的概率律，然后再针对 $Y$ 的任何可能取值 $y$，提供一个 $X$ 的条件 PDF $f_{X\mid Y}(x\mid y)$。

<span style="color:#2471a3;">**[example]**</span>

**Example 3.16．** 一辆典型车辆驶过警用雷达（police radar）时的车速被建模为一个**指数分布**（exponentially distributed）的随机变量 $X$，其**均值**（mean）为每小时 50 英里。警用雷达对车速的测量值 $Y$ 带有误差，该误差被建模为**正态随机变量**（normal random variable），其均值为零，标准差（standard deviation）等于车速的十分之一。$X$ 与 $Y$ 的联合 PDF 是什么？

我们已知 $f_X(x) = (1/50)\,e^{-x/50}$（对 $x \ge 0$）。同时，在给定 $X = x$ 的条件下，测量值 $Y$ 具有均值 $x$、方差 $x^2/100$ 的正态 PDF。因此

```math
f_{Y\mid X}(y\mid x) = \frac{1}{\sqrt{2\pi}\,(x/10)}\,e^{-(y-x)^2/(2x^2/100)} .
```

于是，对一切 $x \ge 0$ 和一切 $y$，

```math
f_{X,Y}(x,y) = f_X(x)\,f_{Y\mid X}(y\mid x) = \frac{1}{50}\,e^{-x/50} \cdot \frac{1}{\sqrt{2\pi}\,(x/10)}\,e^{-(y-x)^2/(2x^2/100)} .
```

<!-- ===== PDF p182 ===== -->
===== PDF p182 =====

### <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）　§条件 PDF（续）</span>

<span style="color:#2471a3;">**[section·续]**</span> 条件 PDF —— 给定一个随机变量（Conditional PDF Given a Random Variable）

设 $X$ 与 $Y$ 是联合连续的随机变量（jointly continuous random variables），其联合 PDF 为 $f_{X,Y}$。联合、边际以及条件 PDF 通过下列公式相互联系（are related to each other by the formulas）：

```math
f_{X,Y}(x, y) = f_Y(y)\, f_{X \mid Y}(x \mid y),
```

```math
f_X(x) = \int f_Y(y)\, f_{X \mid Y}(x \mid y)\, dy.
```

条件 PDF $f_{X \mid Y}(x \mid y)$ 仅对那些使得 $f_Y(y) > 0$ 的 $y$ 才有定义。

我们有：

```math
P\bigl(X \in A \mid Y = y\bigr) = \int_A f_{X \mid Y}(x \mid y)\, dx.
```

对于多于两个随机变量的情形，上述结果有着自然的推广（natural extensions）。例如，我们可以通过如下公式来定义条件 PDF：

```math
f_{X, Y \mid Z}(x, y \mid z) = \frac{f_{X, Y, Z}(x, y, z)}{f_Z(z)}\,, \qquad \text{若} f_Z(z) > 0,
```

```math
f_{X \mid Y, Z}(x \mid y, z) = \frac{f_{X, Y, Z}(x, y, z)}{f_{Y, Z}(y, z)}\,, \qquad \text{若} f_{Y, Z}(y, z) > 0.
```

乘法规则（multiplication rule）也存在相应的类比：

```math
f_{X, Y, Z}(x, y, z) = f_{X \mid Y, Z}(x \mid y, z)\, f_{Y \mid Z}(y \mid z)\, f_Z(z),
```

本节中推导出的其他公式也同样如此。

---

### <span style="color:#c0392b;">条件期望（Conditional Expectation）</span>

对于一个连续随机变量 $X$，我们仿照无条件（unconditional）的情形来定义其给定某一事件 $A$ 的条件期望 $E[X \mid A]$，唯一的差别在于现在需要用到条件 PDF $f_{X \mid A}$。

条件期望 $E[X \mid Y = y]$ 以类似的方式、借助条件 PDF $f_{X \mid Y}$ 来定义。

期望的许多熟悉性质（familiar properties）在此情境下依然成立，现于下文中加以总结。我们注意到，除将求和替换为积分、并将概率质量函数（PMF）替换为 PDF 之外，所有这些公式都与离散型随机变量情形的对应公式相类似。

<!-- ===== PDF p183 ===== -->
===== PDF p183 =====

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">**3.5 条件作用（Conditioning）**</span> — 页 173

<span style="color:#2471a3;">**[summary]**</span> <span style="color:#c0392b;">关于条件期望的事实总结（Summary of Facts About Conditional Expectations）</span>

设 $X$ 与 $Y$ 是联合连续（jointly continuous）随机变量，并设 $A$ 是一个满足 $P(A) > 0$ 的事件。

<span style="color:#2471a3;">**[definition]**</span> **定义（Definitions）：** 给定事件 $A$ 时 $X$ 的**条件期望（conditional expectation）**定义为

```math
E[X \mid A] = \int x\, f_{X \mid A}(x)\, dx.
```

给定 $Y = y$ 时 $X$ 的条件期望定义为

```math
E[X \mid Y = y] = \int x\, f_{X \mid Y}(x \mid y)\, dx.
```

<span style="color:#2471a3;">**[theorem]**</span> **期望值法则（The expected value rule）：** 对函数 $g(X)$，我们有

```math
E[g(X) \mid A] = \int g(x)\, f_{X \mid A}(x)\, dx,
```

以及

```math
E[g(X) \mid Y = y] = \int g(x)\, f_{X \mid Y}(x \mid y)\, dx.
```

<span style="color:#2471a3;">**[theorem]**</span> **全期望定理（Total expectation theorem）：** 设 $A_1, A_2, \ldots, A_n$ 是构成样本空间一个划分（partition）的不相交事件，并假设对每个 $i$ 都有 $P(A_i) > 0$。则

```math
E[X] = \sum_{i=1}^{n} P(A_i)\, E[X \mid A_i].
```

类似地，

```math
E[X] = \int E[X \mid Y = y]\, f_Y(y)\, dy.
```

对多个随机变量的函数情形，也存在自然的类似结果（natural analogs）。例如

```math
E[g(X, Y) \mid Y = y] = \int g(x, y)\, f_{X \mid Y}(x \mid y)\, dx,
```

以及

```math
E[g(X, Y)] = \int E[g(X, Y) \mid Y = y]\, f_Y(y)\, dy.
```

期望值法则的建立方式与无条件期望（unconditional expectations）的情形完全相同。为了论证全期望定理的第一个版本，……

> <span style="color:#7f8c8d;">[页界] 本页末句「…the first version of the total expectation」在原文中并未结束，属于跨页续接，论证的后续内容应在下一页开头继续（下一页应为 Sec. 3.5 条件期望的论证与例题）。</span>

<!-- ===== PDF p184 ===== -->
<!-- ===== PDF p184 ===== -->

<span style="color:#c0392b;">**第 3 章　一般随机变量（General Random Variables）**</span>

（本页为上一页**全期望定理（total expectation theorem）**证明的延续，页首无新的小节标题。）

**全期望定理（total expectation theorem）的证明（续）。**

为证明该定理，我们先从**全概率定理（total probability theorem）**出发：

```math
f_X(x) = \sum_{i=1}^{n} P(A_i)\, f_{X \mid A_i}(x),
```

再在等式两边同时乘以 $x$，并从 $-\infty$ 到 $\infty$ 积分，即可得到全期望定理。

为了确证全期望定理的第二种形式，我们观察

```math
\begin{aligned}
E[X] &= \int_{-\infty}^{\infty} E[X \mid Y=y]\, f_Y(y)\, dy \\
&= \int_{-\infty}^{\infty} \Bigl( \int_{-\infty}^{\infty} x\, f_{X \mid Y}(x \mid y)\, dx \Bigr) f_Y(y)\, dy \\
&= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x\, f_{X \mid Y}(x \mid y)\, f_Y(y)\ dx\, dy \\
&= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x\, f_{X,\,Y}(x,y)\ dx\, dy \\
&= \int_{-\infty}^{\infty} x \Bigl( \int_{-\infty}^{\infty} f_{X,\,Y}(x,y)\ dy \Bigr) dx \\
&= \int_{-\infty}^{\infty} x\, f_X(x)\ dx \\
&= E[X].
\end{aligned}
```

利用这样的**分而治之（divide-and-conquer）**方法，全期望定理往往能大大方便随机变量的均值、方差及其他各阶矩的计算。

---

<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#00838f;">**Example 3.17（Mean and Variance of a Piecewise Constant PDF，分段常数概率密度函数的均值与方差。）**</span>

设随机变量 $X$ 具有如下的分段常数（piecewise constant）概率密度函数

```math
f_X(x) =
\begin{cases}
1/3, & \text{若 } 0 \le x \le 1,\\
2/3, & \text{若 } 1 < x \le 2,\\
0, & \text{其他情形},
\end{cases}
```

（参见图 3.18，Fig. 3.18）。考虑下列事件

```math
A_1 = \{X \text{ 落入第一个区间 } [0,1]\},
```

```math
A_2 = \{X \text{ 落入第二个区间 } (1,2]\} .
```

由给定的概率密度函数，我们有

```math
P(A_1) = \int_0^1 f_X(x)\, dx = \frac{1}{3},
```

```math
P(A_2) = \int_1^2 f_X(x)\, dx = \frac{2}{3} .
```

进而，由于对应的条件概率密度函数 $f_{X \mid A_1}$ 与 $f_{X \mid A_2}$ 易于求得，以 $A_1$ 和 $A_2$ 为条件时 $X$ 的条件均值与条件二阶矩都很容易计算。……（本页结束，Example 3.11 在下一页继续。）

<!-- ===== PDF p185 ===== -->
<!-- ===== PDF p185 ===== -->
<span style="color:#2471a3;">**[example·续]**</span>

## <span style="color:#c0392b;">例 3.17：分段常数 PDF 的均值与方差（Mean and Variance of a Piecewise Constant PDF）</span>（续）

由于相应的条件 PDF $f_{X \mid A_1}$ 与 $f_{X \mid A_2}$ 分别在 $[0,1]$ 与 $(1,2]$ 上为**均匀分布**（uniform），因此条件化于 $A_1$ 与 $A_2$　后 $X$ 的**均值**（mean）与**二阶矩**（second moment）可以轻而易举地算得：

```math
E[X \mid A_1] = \frac{1}{2}, \qquad E[X^2 \mid A_1] = \frac{1}{3},
```

```math
E[X \mid A_2] = \frac{3}{2}, \qquad E[X^2 \mid A_2] = \frac{7}{3}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏严重，分式与叙述高度碎片化；以下数值依据例 3.11 已被完全确定的数学关系重建，而非取自可读原文]</span>

**现在我们利用**（now we use）全期望定理（total expectation theorem）来求 $X$ 的均值：

```math
E[X] = P(A_1)\,E[X \mid A_1] + P(A_2)\,E[X \mid A_2]
     = \frac{1}{3}\cdot\frac{1}{2} + \frac{2}{3}\cdot\frac{3}{2}
     = \frac{1}{6} + 1
     = \frac{7}{6}.
```

再求二阶矩（second moment）：

```math
E[X^2] = P(A_1)\,E[X^2 \mid A_1] + P(A_2)\,E[X^2 \mid A_2]
       = \frac{1}{3}\cdot\frac{1}{3} + \frac{2}{3}\cdot\frac{7}{3}
       = \frac{1}{9} + \frac{14}{9} = \frac{15}{9} = \frac{5}{3}.
```

于是，**方差**（variance）为

```math
\mathrm{Var}(X) = E[X^2] - \bigl(E[X]\bigr)^2
                = \frac{5}{3} - \left(\frac{7}{6}\right)^2
                = \frac{60}{36} - \frac{49}{36}
                = \frac{11}{36}.
```

我们由此看出（we see）…（页脚在数字 9 处中断；$y > 0$ 等残片疑为下一页内容或图注之误读）

> <span style="color:#7f8c3d;">[note] 本页 OCR 损坏极其严重，公式数字（1/3、2/3、1/2、3/2 及均值 7/6、方差 11/36）均依据例 3.11 的既定数学关系补足；若需与实体书/更清晰扫描件严格逐字校对，请据此校正。</span>

<!-- ===== PDF p186 ===== -->
<!-- ===== PDF p186 ===== -->
<span style="color:#2471a3;">**[example]**</span> <span style="color:#c0392b;">多个连续型随机变量的联合概率密度（Joint PDFs of Multiple Continuous Random Variables）（续）</span>

### <span style="color:#c0392b;">Example 3.18：两个独立正态随机变量的联合概率密度（Joint PDF of Two Independent Normal Random Variables）</span>

> <span style="color:#7f8c8d;">[编号说明：本页 OCR 碎裂未见显式「Example 3.18」字样，此例号由前后例号链强制闭合推断——前例 Example 3.17（p184–185 分段 PDF）、后例 Example 3.19（p189 灯泡），其间唯一缺口即本页双变量正态等高线段，故定位为此例。源小节标题「3.5」疑与 §3.4（Joint PDFs of Multiple Random Variables）章节归属不符，请以清晰扫描件最终核对例号与节号。]</span>

> <span style="color:#7f8c8d;">[本页 OCR 严重损坏，仅能识别部分图题与若干短语；下方按可辨认内容重建，无法辨认处以灰注占位，不臆造数值。]</span>

对于两个相互独立（independent）的随机变量 $X$ 与 $Y$，其联合概率密度函数（joint PDF）形如

```math
f_{X,Y}(x,y) =\ \cdots\ \exp\!\left\{\,\cdots\,\right\}
```

> <span style="color:#7f8c8d;">[原页此处公式 OCR 碎裂（可见 `exp`、`=`、数字 3 与 0 等零散符号），具体系数无法确认，按原文占位。]</span>

<span style="color:#00838f;">**[说明，依可辨认片段重建]**</span> 该联合分布的**等高线（contours）**，即联合概率密度函数取常数的那些点集（constant sets），由下式描述：在联合概率密度函数为常数的集合上，$X$、$Y$ 的取值满足某一确定的约束关系，从而这些等值线呈**椭圆**状，其中心位于 $(\mu_x,\mu_y)$ 处。

> <span style="color:#7f8c8d;">[原页此处正文 OCR 碎裂（可见 `contours are described`、`constant`、`two axes are orthogonal` 等零散短语），整体语义无法完整恢复，上段为最小重建，细节以原文为准。]</span>

<span style="color:#7f8c8d;">**Figure 3.19: Contours of the PDF of two independent normal random variables $X$ and $Y$ with means $\mu_x$, $\mu_y$ and variances $\sigma_x^2$, $\sigma_y^2$**（图 3.19：两个相互独立的正态随机变量 $X$ 与 $Y$ 的联合概率密度函数的等高线，其均值分别为 $\mu_x$、$\mu_y$，方差分别为 $\sigma_x^2$、$\sigma_y^2$）</span>

> <span style="color:#7f8c8d;">[图中两条坐标轴相互正交（two axes are orthogonal）；等高线为一组同心椭圆。]</span>

<!-- ===== PDF p187 ===== -->
===== PDF p187 =====

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">3.5 节　条件作用（Conditioning）· 连续性设定下的独立性</span>

如果 $X$ 与 $Y$ 是独立的（independent），那么任意形如 $\{X \in A\}$ 与 $\{Y \in B\}$ 的两个事件都是独立的。事实上，

```math
\begin{aligned}
P(X \in A,\ Y \in B)
&= \int_{x\in A}\int_{y\in B} f_{X,Y}(x,y)\;dy\,dx \\
&= \int_{x\in A}\int_{y\in B} f_X(x)f_Y(y)\;dy\,dx \\
&= \left( \int_{x\in A} f_X(x)\,dx \right) \left( \int_{y\in B} f_Y(y)\,dy \right) \\
&= P(X \in A)\; P(Y \in B).
\end{aligned}
```

特别地，独立性（independence）蕴含（implies）：

```math
F_{X,Y}(x,y) = P(X \le x,\ Y \le y) = P(X \le x)\,P(Y \le y) = F_X(x)\,F_Y(y),
```

对一切 $x, y$ 成立。

这些结论的逆命题（converse）也为真，见章末习题。性质

```math
F_{X,Y}(x,y) = F_X(x)\,F_Y(y)
```

对一切 $x, y$ 成立，可用来给出两个随机变量之间独立性的一般定义（general definition of independence），例如当 $X$ 为离散型而 $Y$ 为连续型的情形。

与离散情形相类似的论证表明：若 $X$ 与 $Y$ 独立，则

```math
E[g(X)h(Y)] = E[g(X)]\,E[h(Y)],
```

对任意两个函数 $g$ 与 $h$ 成立。最后，独立随机变量之和的方差（variance）等于它们各自方差之和。

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">连续随机变量的独立性（Independence of Continuous Random Variables）</span>

设 $X$ 与 $Y$ 为联合连续（jointly continuous）的随机变量。

- 若对一切 $x, y$ 有 $f_{X,Y}(x,y) = f_X(x)\,f_Y(y)$，则 $X$ 与 $Y$ 独立。
- 若 $X$ 与 $Y$ 独立，则 $E[XY] = E[X]\,E[Y]$。

<!-- ===== PDF p188 ===== -->
===== PDF p188 =====

<span style="color:#7f8c8d;">（本页为教材页 178。页首是第 3.5 节的收尾内容，随后进入第 3.6 节「推断（Inference）」。）</span>

---

<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">第 3.5 节　多个随机变量（More Than Two Random Variables）</span>（续）

…且 $g(X)$ 与 $h(Y)$ **相互独立**（are independent），于是我们有

```math
E\bigl[g(X)\,h(Y)\bigr] = E[g(X)]\cdot E[h(Y)].
```

若 $X$ 与 $Y$ 相互独立，则

```math
\mathrm{var}(X+Y) = \mathrm{var}(X) + \mathrm{var}(Y).
```

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">推断（Inference）</span>

在许多情形中，我们用随机变量（random variable）$X$ 来刻画一个**未被观测到**（unobserved）的现象，其概率密度函数（PDF, probability density function）为 $f_X$；我们又得到一个**带有噪声**（noisy）的测量值 $Y$，它由一条条件 PDF $f_{Y\mid X}$ 建模：

```math
f_{Y\mid X}(y \mid x).
```

一旦 $Y$ 的取值 $y$ 被观测到，它为 $X$ 的未知取值提供了多少**信息**（information）？也就是说，我们希望在已知 $Y=y$ 的条件下，评估 $X$ 的条件 PDF $f_{X\mid Y}(x\mid y)$。

这种情形与**第 1.4 节**：其中我们运用贝叶斯规则（Bayes rule）来处理离散随机变量之处的设定相类似，区别在于我们现在面对的是连续型随机变量。唯一的难度在于求解贝叶斯规则中的**归一化常数**（normalization constant）。

> <span style="color:#7f8c8d;">**Figure 3.16: Schematic description of the inference problem**（图 3.16：推断问题的示意图，schematic description of the inference problem）</span>
>
> 我们有一个概率密度函数 $f_X$ 已知的随机变量 $X$，并按条件 PDF $f_{Y\mid X}$ 得到一次测量 $Y$。给定 $Y$ 的一个已观测值 $y$，推断问题就是要评估条件 PDF $f_{X\mid Y}(x\mid y)$。

由 $X$ 与 $Y$ 倒向的两个公式，即

```math
f_{X\mid Y}(x\mid y) \;=\; \frac{f_X(x)\,f_{Y\mid X}(y\mid x)}{f_Y(y)},
```

以及

```math
f_Y(y) \;=\; \int_{-\infty}^{\infty} f_X(t)\,f_{Y\mid X}(y\mid t)\;dt,
```

可得

```math
f_{X\mid Y}(x\mid y) =
\frac{f_X(x)\,f_{Y\mid X}(y\mid x)}
{\displaystyle \int_{-\infty}^{\infty} f_X(t)\,f_{Y\mid X}(y\mid t)\;dt}.
```

这是一个用于……（本页止于此，下页续接）

> <span style="color:#7f8c8d;">[原页此处 OCR 严重损坏，公式中部与末段文字（"an expression to evaluate…"）无法完整辨认，已尽力由第 3.6 节标准内容复原；编号 3.6 及公式结构以经典教材文本为准。]</span>

<!-- ===== PDF p189 ===== -->
<!-- ===== PDF p189 ===== -->
> <span style="color:#7f8c8d;">§3.6, p.179（第 3 章　一般随机变量，General Random Variables）</span>

# <span style="color:#c0392b;">3.6 连续贝叶斯法则（The Continuous Bayes' Rule）</span>

<span style="color:#2471a3;">**[example]**</span>

### <span style="color:#c0392b;">Example 3.19（依据指数寿命推断做工参数：通用照明公司灯泡）</span>

由通用照明公司（General Illumination Company）生产的一个灯泡，已知其寿命 $Y$ 服从指数分布（exponentially distributed lifetime）。然而，该公司近来一直存在质量控制（quality control）问题。在任意给定的一天里，$Y$ 的概率密度函数的参数 $\lambda$ 实际上是一个随机变量，在区间 $[1,\ \tfrac{3}{2}]$ 上服从均匀分布（uniformly distributed）。我们测试一个灯泡并记录其寿命。那么我们对其底层参数 $\lambda$ 能做出怎样的推断呢？

我们用均匀随机变量 $A$ 来刻画参数 $\lambda$，其概率密度函数为

```math
f_A(\lambda) = \begin{cases} 2, & 1 < \lambda < \tfrac{3}{2},\\ 0, & \text{其他（otherwise）}. \end{cases}
```

关于 $A$ 的可用信息，由条件概率密度函数（conditional PDF）$f_{A \mid Y}(\lambda \mid y)$ 所刻画。利用连续贝叶斯法则（continuous Bayes' rule），它由下式给出：

```math
f_{A \mid Y}(\lambda \mid y) = \frac{f_A(\lambda)\, f_{Y \mid A}(y \mid \lambda)}{\displaystyle\int_{-\infty}^{\infty} f_A(t)\, f_{Y \mid A}(y \mid t)\, dt} \,= \frac{2\,\lambda\, e^{-\lambda y}}{\displaystyle\int_{1}^{3/2} 2\, t\, e^{-t y}\, dt},\qquad 1 < \lambda < \tfrac{3}{2}.
```

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">关于离散随机变量的推断（Inference about a Discrete Random Variable）</span>

在一些情况下，被观测到的那些现象（unobserved phenomenon）本质上是离散的。举例而言，设想一个二值信号（binary signal）是在正态分布噪声（normally distributed noise）的干扰下被观测到的；或设想一个医疗诊断（medical diagnosis）是在体温、血细胞计数等连续测量值（continuous measurements）的基础上作出的。在这些情况下，适用的是贝叶斯法则的某种略有不同的版本。

我们首先考虑这样的情况：未被观测到的现象是用某个发生与否未知的事件（event）来描述的。设 $A$ 为该事件，$P(A)$ 为其概率。设 $Y$ 为一个连续随机变量，并假定条件概率密度函数 $f_{Y \mid A}(y)$ 与 $f_{Y \mid A^c}(y)$ 均已知。我们感兴趣的是给定 $Y$ 的取值时事件的条件概率 $P(A \mid Y = y)$。

与其处理那个零概率（zero probability）的条件事件 $\{Y = y\}$，不如改而对事件 $\{y \le Y \le y + \delta\}$ 施加条件，其中 $\delta$ 是一个小的正数，然后令 $\delta$ 趋近于零（tends to zero）取极限。利用贝叶斯法则（Bayes' rule），并假定 $\delta > 0$，我们得到

```math
\begin{aligned}
P(A \mid Y = y) &= \lim_{\delta \to 0}\; P(A \mid y \le Y \le y + \delta)\\
&= \lim_{\delta \to 0}\; \frac{P(A)\, P(y \le Y \le y + \delta \mid A)}{P(y \le Y \le y + \delta)}\\
&= \lim_{\delta \to 0}\; \frac{P(A)\, f_{Y \mid A}(y)\, \delta}{f_Y(y)\, \delta}\\
&= \frac{P(A)\, f_{Y \mid A}(y)}{f_Y(y)}.
\end{aligned}
```

分母（denominator）可以利用下面这个全概率定理（total probability theorem）的版本求值：

> <span style="color:#7f8c8d;">本页在此处结束，「…全概率定理的版本求值：」后的 $f_Y(y)$ 展开公式位于下一页开头。</span>

<!-- ===== PDF p190 ===== -->
<!-- ===== PDF p190 ===== -->
<span style="color:#2471a3;">**[section·续]**</span> <span style="color:#c0392b;">第 3.6 节 连续情况下的贝叶斯法则（The Continuous Bayes Rule）（续）</span>

于是（so that）

```math
P(A \mid Y = y) = \frac{P(A)\,f_{Y\mid A}(y)}{P(A)\,f_{Y\mid A}(y) + P(A^{c})\,f_{Y\mid A^{c}}(y)}.
```

在这个公式的一个变体（variant）中，我们考虑形如 $A = \{N = n\}$ 的事件，其中 $N$ 是一个**离散型随机变量**（discrete random variable），它代表了我们所关注的未观测现象的可能的不同离散情形。记 $P_{N}$ 为 $N$ 的概率质量函数（PMF）。设 $Y$ 是一个**连续型随机变量**（continuous random variable），对 $N$ 的任一给定值 $n$，它由条件概率密度函数（conditional PDF）$f_{Y\mid N}(y \mid n)$ 描述。于是上述公式变为

```math
P(N = n \mid Y = y) = \frac{P_{N}(n)\,f_{Y\mid N}(y \mid n)}{f_{Y}(y)}.
```

其中分母（denominator）可以用如下全概率定理（total probability theorem）的版本加以计算：

```math
f_{Y}(y) = \sum_i P_{N}(i)\,f_{Y\mid N}(y \mid i),
```

于是

```math
P(N = n \mid Y = y) = \frac{P_{N}(n)\,f_{Y\mid N}(y \mid n)}{\sum_i P_{N}(i)\,f_{Y\mid N}(y \mid i)}.
```

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#00838f;">**Example 3.20．信号检测（Signal Detection）**</span>

一个**二元（二进制）信号**（binary signal）$S$ 被发送出去，已知 $P(S=1)=p$、$P(S=-1)=1-p$。接收到的信号为 $Y = N + S$，其中 $N$ 是**正态（高斯）噪声**（normal noise），均值为零、方差为一，且与 $S$ 独立。把 $S=1$ 的概率表示为观测值 $Y=y$ 的函数，它是多少？

在给定 $S=s$ 的条件下，随机变量 $Y$ 服从均值为 $s$、方差为一的正态分布。应用上面给出的公式，我们得到

```math
P(S=1 \mid Y=y) = \frac{p_S(1)\,f_{Y\mid S}(y \mid 1)}{f_{Y}(y)}
= \frac{p\,e^{-(y-1)^{2}/2}/\sqrt{2\pi}}{p\,e^{-(y-1)^{2}/2}/\sqrt{2\pi} + (1-p)\,e^{-(y+1)^{2}/2}/\sqrt{2\pi}},
```

化简（simplifies）为

```math
P(S=1 \mid Y=y) = \frac{p\,e^{y}}{p\,e^{y} + (1-p)\,e^{-y}}.
```

注意，概率 $P(S=1 \mid Y=y)$ 随 $y$ 趋于 $-\infty$ 而趋于零，随 $y$ 趋于 $+\infty$ 而趋于一，并且在其间**单调递增**（monotonically increasing），这与直觉是一致的。

<!-- ===== PDF p191 ===== -->
<!-- ===== PDF p191 ===== -->

> <span style="color:#7f8c8d;">续 §3.6 The Continuous Bayes' Rule（连续随机变量的贝叶斯准则）；本节从上一页延续而来，页首无新章/节标题。</span>

正文承接上文：最后，我们注意到，前面用 $f_Y(y)$ 表达 $f_{Y|A}(y)$（条件概率密度函数，conditional PDF）的那个公式，可以反过来改写，从而得到一个用 $f_{Y|A}(y)$ 表达 $P(A \mid Y=y)$ 的等价公式。

回顾前面那个公式

```math
f_{Y|A}(y) = \frac{f_Y(y)\, P(A \mid Y=y)}{\int_{-\infty}^{\infty} f_Y(t)\, P(A \mid Y=t)\, dt} = \frac{f_Y(y)\, P(A \mid Y = y)}{P(A)}.
```

把它反过来，即得

```math
P(A \mid Y = y) = \frac{P(A)\, f_{Y|A}(y)}{f_Y(y)} = \frac{f_{Y|A}(y)}{f_Y(y)} \int_{-\infty}^{\infty} f_Y(t)\, P(A \mid Y = t)\, dt.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏，公式分式的分子/分母与积分表达式在提取时被打乱，以上按教材标准形重建，未引入任何具体数值。]</span>

该公式可用于：当观察到事件 $A$ 时，对随机变量 $Y$ 作出推断（inference）。

<span style="color:#c0392b;">**基于离散观测的推断（Inference Based on Discrete Observations）**</span>

当事件取形如 $\{N=n\}$ 的形式时，也有一个类似的公式，其中 $N$ 是一个已观测的离散型随机变量，它以一种由条件概率质量函数（PMF, probability mass function）$p_{N|Y}(n \mid y)$ 刻画的方式依赖于 $Y$。

由规范化性质（normalization property）$\int_{-\infty}^{\infty} f_{Y|N}(y \mid n)\, dy = 1$，可得

```math
f_{Y|N}(y \mid n) = \frac{f_Y(y)\, p_{N|Y}(n \mid y)}{\int_{-\infty}^{\infty} f_Y(t)\, p_{N|Y}(n \mid t)\, dt} = \frac{f_Y(y)\, p_{N|Y}(n \mid y)}{p_N(n)}.
```

<p align="center">
<span style="color:#2471a3;">**[box·结果]**</span> <span style="color:#00838f;">**连续随机变量的贝叶斯准则（Bayes' Rule for Continuous Random Variables）**</span>
</p>

设 $Y$ 为连续型随机变量（continuous random variable）。

- 若 $X$ 是连续型随机变量，则
```math
f_Y(y)\, f_{X|Y}(x \mid y) = f_X(x)\, f_{Y|X}(y \mid x),
```
且
```math
f_{X|Y}(x \mid y) = \frac{f_X(x)\, f_{Y|X}(y \mid x)}{\int_{-\infty}^{\infty} f_X(t)\, f_{Y|X}(y \mid t)\, dt}.
```

- 若 $N$ 是离散型随机变量，则
```math
f_Y(y)\, p_{N|Y}(n \mid y) = p_N(n)\, f_{Y|N}(y \mid n),
```
由此得到以下公式

> 页面在此戛然而止，余下公式延续到下一页（续接）。

<!-- ===== PDF p192 ===== -->
<!-- ===== PDF p192 ===== -->

> <span style="color:#7f8c8d;">本章内部页码 182（对应 PDF 第 192 页）。页首无新章节标题，为第 3.6 节末尾推导公式的续接。</span>

> <span style="color:#7f8c8d;">**（承接上一页 §3.6 的推导）** 当 $Y$ 是连续随机变量、$N$ 是取整数值的离散随机变量时，给定 $N=n$ 的条件下 $Y$ 的条件概率密度函数（conditional PDF）为：</span>

```math
f_{Y\mid N}(y\mid n) \;=\; \frac{f_Y(y)\;P(N = n \mid Y = y)}{f_Y(t)\;P(N = n \mid Y = t)\;} ,
```

> <span style="color:#7f8c8d;">[原页此处分式为分数形式，分母为对 $t$ 的积分 $\int_0^\infty f_Y(t)P(N=n\mid Y=t)\,dt$；源 OCR 将积分号误读为「100」、将 $y$ 误读为「100」/「00」，此处已按规范合并为正规 LaTeX，积分上下限系由上下文推算。</span>

对于 $P(A \mid Y = y)$ 与 $f_{Y\mid A}(y)$ 也有类似的公式。

此外，以下乘积恒等式（product identity）在推导中同样成立：

```math
f_Y(y)\;P(N = n \mid Y = y) \;=\; f_{Y\mid N}(y\mid n)\;P_N(n),
```

> <span style="color:#7f8c8d;">[原页此段 OCR 严重破碎（仅存 $f_Y(y)P(N=n\mid Y=y)$ 与 $f_{Y\mid N}(y\mid n)P_N(n)$ 等残片），上述等式是按连续-离散混合贝叶斯标准结论重建。</span>

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">3.7 小结与讨论（Summary and Discussion）</span>

连续随机变量（continuous random variable）由概率密度函数（PDF, probability density function）刻画，改而用来计算事件概率（probability）。这与离散情形下用概率质量函数（PMF）是类似的，只不过现在我们需要用**积分**代替**求和**。联合 PDF（joint PDF）与联合 PMF 类似，用来确定由多个随机变量所定义的事件的概率。此外，条件 PDF 与条件 PMF 类似，用来计算给定条件随机变量取值时的条件概率。一个重要的应用出现在**推断**（inference）问题中，采用的就是本章所建立的贝叶斯法则（Bayes' rule）的各种形式。

有若干特殊连续随机变量频繁地出现在概率模型中。我们介绍了其中一部分，并推导了它们的**均值**（mean）与**方差**（variance）。下表给出了总结。

#### <span style="color:#c0392b;">特殊随机变量的结果总结（Summary of Results for Special Random Variables）</span>

> <span style="color:#7f8c8d;">（下表为跨页延续，本页收录「连续均匀分布」与「指数分布」两项，其余分布见后续页。）</span>

<span style="color:#00838f;">**[定义表项] 区间 $[a,b]$ 上的连续均匀分布（Continuous Uniform Over $[a,b]$）：**</span>

```math
f_X(x) \;=\; \begin{cases} \dfrac{1}{\,b-a\,}, & \text{if}\; a \le x \le b, \\[2mm] 0, & \text{otherwise,} \end{cases}
```

```math
E[X] \;=\; \frac{a+b}{2}, \qquad \mathrm{var}(X) \;=\; \frac{(b-a)^2}{12}.
```

---

<span style="color:#00838f;">**[定义表项] 参数为 $\lambda$ 的指数分布（Exponential with Parameter $\lambda$）：**</span>

```math
F_X(x) \;=\; \begin{cases} 0, & \text{if}\; x \le 0, \\ 1 - e^{-\lambda x}, & \text{if}\; x > 0, \end{cases}
\qquad
f_X(x) \;=\; \begin{cases} 0, & \text{if}\; x \le 0, \\ \lambda e^{-\lambda x}, & \text{if}\; x > 0, \end{cases}
```

```math
E[X] \;=\; \frac{1}{\lambda}, \qquad \mathrm{var}(X) \;=\; \frac{1}{\lambda^2}.
```

<!-- ===== PDF p193 ===== -->
<!-- ===== PDF p193 ===== -->
<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3.7 节　总结与讨论（Summary and Discussion）</span>（续）

<span style="color:#00838f;">**参数为 μ 与 σ² > 0 的正态分布（Normal with Parameters $\mu$ and $\sigma^2>0$）：**</span>

```math
f_X(x) = \frac{1}{\sqrt{2\pi}\,\sigma}\, e^{-\,\frac{(x-\mu)^2}{2\sigma^2}},
\qquad
E[X] = \mu,
\qquad
\operatorname{var}(X) = \sigma^2.
```

我们还引入了累积分布函数（CDF, cumulative distribution function），它可以用来刻画那些既非离散也非连续（neither discrete nor continuous）的一般随机变量。累积分布函数与概率质量函数（PMF）、概率密度函数（PDF）都有联系，但更具一般性。对于离散型随机变量，我们可以通过对累积分布函数求差分（differencing）来获得其概率质量函数；对于连续型随机变量，我们则可以通过对累积分布函数求导（differentiating）来获得其概率密度函数。

<!-- ===== PDF p194 ===== -->
===== PDF p194 =====

> <span style="color:#c0392b;">**第 3 章　一般随机变量（General Random Variables）　——　习题（PROBLEMS）**</span>

> 本页为第 3 章章末习题区（Problems）的第 3.1 节开头。按规范 §5：习题题干保持英文原文，不翻译；带 `*` 的题（Problem 3）保留其英文 Solution，仅「Solution」标签可标注中文。

<span style="color:#7f8c8d;">Chap. 3 · PROBLEMS · Section 3.1（续接上页开始的问题区标题之后）</span>

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3.1 节　连续随机变量与概率密度函数（Section 3.1: Continuous Random Variables and PDFs）</span>

<span style="color:#2471a3;">**[problem 1]</span>

**Problem 1.** Let $X$ be uniformly distributed in the unit interval $[0,1]$. Consider the random variable $Y = g(X)$, where

```math
g(x) = \begin{cases} 2, & \text{if } x \le \frac{1}{3},\\[2pt] 1, & \text{if } x > \frac{1}{3}. \end{cases}
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原 片断 "g(x) = { 21., if x ≤ 1/3, if x > 1/3 }" 将 $g(x)=2$ 与 $g(x)=1$ 两分支揉成一团（"21."）；按上下文应拆为 $g(x)=2$ 当 $x\le 1/3$、$g(x)=1$ 当 $x>1/3$。此推断基于题面（构造两段常值函数），未见原数值故已在上方给出并注明。</span>

Find the expected value of $Y$ by first deriving its PMF. Verify the result using the expected value rule.

---

<span style="color:#2471a3;">**[problem 2]**</span>

**Problem 2.** *Laplace random variable.* Let $X$ have the PDF

```math
f_X(x) = \tfrac{1}{2}\,\lambda\, e^{-\lambda |x|},
```

where $\lambda$ is a positive scalar. Verify that $f_X$ satisfies the normalization condition, and evaluate the mean and variance of $X$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原 片断 "f_x(x) = '2.A e - >' I x l" 中 "2.A" 应为 $\tfrac{1}{2}\lambda$，".A" 应为 $\lambda$，负号与指数上的 $|x|$ 被拆分；按归一化条件反查确认为 $f_X(x) = \tfrac{1}{2}\lambda e^{-\lambda|x|}$。</span>

---

<span style="color:#2471a3;">**[problem 3·starred]**</span>

**Problem 3.** * Show that the expected value of a discrete or continuous random variable $X$ satisfies

```math
E[X] = \int_{0}^{\infty} P(X > x)\, dx \;-\; \int_{0}^{\infty} P(X < -x)\, dx.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原片断 "E[X] = ∫ .x P(X > x) dx ∫ .x P(X −x) dx . (" 中第二个积分漏印了 "< −x" 的行内负号（仅在后面遗留 "<"），已按标准尾部公式修正为 $\int_0^\infty P(X<-x)\,dx$（其中 $X_-=\max(-X,0)$ 对应负部）。</span>

<span style="color:#00838f;">**[Solution（解答）]**</span>

Suppose that $X$ is continuous. We then have

```math
\int_{0}^{\infty} P(X > x)\, dx
= \int_{0}^{\infty} \left[ \int_{x}^{\infty} f_X(y)\, dy \right] dx
= \int_{0}^{\infty} \left[ \int_{0}^{y} dx \right] f_X(y)\, dy
= \int_{0}^{\infty} y\, f_X(y)\, dy .

```

where for the second equality we have reversed the order of integration by writing the set $\{ (x,y) \mid 0 \le x < \infty,\; x \le y < \infty \}$ as $\{ (x,y) \mid 0 \le x \le y,\; 0 \le y < \infty \}$. Similarly, we can show that

```math
-\int_{0}^{\infty} P(X < -x)\, dx
= \int_{-\infty}^{0} y\, f_X(y)\, dy .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原第二处分式片断 "= J. P(X −x) dx − 1°= y f_X(y) dy .<" 无法直接转写；此推导为课本标准解法（负部整体反号为 $\int_{-\infty}^0 y f_X(y)\,dy$）并按上下文整理合并。第一个等式的推导过程（含 $x\le y$ 的区域改写）与原页一致，末项 $\int_0^\infty y f_X(y) dy$ 对应正部 $E[X_+]$；第二式对应负部，两式相加即得题给等式。</span>

<!-- ===== PDF p195 ===== -->
===== PDF p195 =====

<span style="color:#c0392b;">**第 3 章　一般随机变量（General Random Variables）**</span>

<span style="color:#7f8c8d;">Problems（习题）— 本章习题区，本页为前页 Problem 解答的收尾 + Problem 4（页码 185）</span>

<span style="color:#2471a3;">**[problem·续]**</span> 前一题（Problem 3）解答的尾部（continuation of the preceding Problem's solution）

Combining the two relations above, we obtain the desired result. If $X$ is discrete, we have

```math
P(X > x) = \sum_{y > x} p_X(y)
         = \sum_{y > 0} \left( \int_0^y p_X(y)\, dx \right)
         = \sum_{y > 0} p_X(y) \left( \int_0^y dx \right),
```

and the rest of the argument is similar to the continuous case.

---
<span style="color:#2471a3;">**[problem]**</span> **Problem 4.&#42;** Establish the validity of the expected value rule

```math
E[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x)\, dx,
```

where $X$ is a continuous random variable with PDF $f_X$.

<span style="color:#00838f;">**[Solution（解答）]**</span> Let us express the function $g$ as the difference of two nonnegative functions,

```math
g(x) = g_{+}(x) - g_{-}(x),
```

where $g_{+}(x) = \max\{g(x), 0\}$, and $g_{-}(x) = \max\{-g(x), 0\}$. In particular, for any $t \ge 0$, we have $g(x) > t$ if and only if $g_{+}(x) > t$.

We will use the result

```math
E[g(X)] = \int_0^\infty P\bigl(g(X) > t\bigr)\, dt - \int_0^\infty P\bigl(g(X) < -t\bigr)\, dt
```

from the preceding problem. The first term in the right-hand side is equal to

```math
\int_0^\infty \int_{\{x \mid g(x) > t\}} f_X(x)\, dx\, dt
= \int_{-\infty}^{\infty} \int_{\{t \mid 0 \le t < g(x)\}} f_X(x)\, dt\, dx
= \int_{-\infty}^{\infty} g_{+}(x) f_X(x)\, dx.
```

By a symmetrical argument, the second term in the right-hand side is given by

```math
\int_0^\infty P\bigl(g(X) < -t\bigr)\, dt = \int_{-\infty}^{\infty} g_{-}(x) f_X(x)\, dx.
```

Combining the above equalities, we obtain

```math
E[g(X)] = \int_{-\infty}^{\infty} g_{+}(x) f_X(x)\, dx - \int_{-\infty}^{\infty} g_{-}(x) f_X(x)\, dx
        = \int_{-\infty}^{\infty} g(x) f_X(x)\, dx.
```

<!-- ===== PDF p196 ===== -->
===== PDF p196 =====

<span style="color:#c0392b;">**第 3 章　一般随机变量（General Random Variables）**</span>

<span style="color:#7f8c8d;">§ 3.2，p.186　Sec. 3.2. Cumulative Distribution Functions（累积分布函数）</span>

<span style="color:#2471a3;">**[problem]**</span> **Problem 5.** Consider a triangle and a point chosen within the triangle according to the uniform probability law. Let $X$ be the distance from the point to the base of the triangle. Given the height of the triangle, find the CDF and the PDF of $X$.

<span style="color:#2471a3;">**[problem]**</span> **Problem 6.** Calamity Jane goes to the bank to make a withdrawal, and is equally likely to find 0 or 1 customers ahead of her. The service time of the customer ahead, if present, is exponentially distributed with parameter $\lambda$. What is the CDF of Jane's waiting time?

<span style="color:#2471a3;">**[problem]**</span> **Problem 7.** Alvin throws darts at a circular target of radius $r$ and is equally likely to hit any point in the target. Let $X$ be the distance of Alvin's hit from the center.

(a) Find the PDF, the mean, and the variance of $X$.

(b) The target has an inner circle of radius $t$. If $X \le t$, Alvin gets a score of $S = 1/X$. Otherwise his score is $S = 0$. Find the CDF of $S$. Is $S$ a continuous random variable?

<span style="color:#2471a3;">**[problem]**</span> **Problem 8.** Consider two continuous random variables $Y$ and $Z$, and a random variable $X$ that is equal to $Y$ with probability $p$ and to $Z$ with probability $1 - p$.

(a) Show that the PDF of $X$ is given by

```math
f_X(x) = p f_Y(x) + (1 - p) f_Z(x).
```

(b) Calculate the CDF of the two-sided exponential random variable that has PDF given by

```math
f_X(x) = \begin{cases} p\lambda e^{\lambda x}, & \text{if } x < 0,\\ (1 - p)\lambda e^{-\lambda x}, & \text{if } x \ge 0, \end{cases}
```

where $\lambda > 0$ and $0 < p < 1$.

<span style="color:#2471a3;">**[problem]**</span> **Problem 9.&#42;** *Mixed random variables.* Probabilistic models sometimes involve random variables that can be viewed as a mixture of a discrete random variable $Y$ and a continuous random variable $Z$. By this we mean that the value of $X$ is obtained according to the probability law of $Y$ with a given probability $p$, and according to the probability law of $Z$ with the complementary probability $1 - p$. Then, $X$ is called a mixed random variable and its CDF is given, using the total probability theorem, by

```math
F_X(x) = P(X \le x) = p\,P(Y \le x) + (1 - p)\,P(Z \le x) = p F_Y(x) + (1 - p) F_Z(x).
```

Its expected value is defined in a way that conforms to the total expectation theorem:

```math
E[X] = p E[Y] + (1 - p) E[Z].
```

The taxi stand and the bus stop near Al's home are in the same location. Al goes there at a given time and if a taxi is waiting (this happens with probability 2/3) he — [stanza continues on the next page]

<!-- ===== PDF p197 ===== -->
<!-- ===== PDF p197 ===== -->
# <span style="color:#c0392b;">第 3 章　一般随机变量（General Random Variables）—— 习题区（Problems），页 187</span>

<span style="color:#2471a3;">**[problem·续]**</span> <span style="color:#00838f;">（承上页某带 `*` 习题，题干见前页；本页为该题的英文 Solution 续文）</span>

boards it. Otherwise he waits for a taxi or a bus to come, whichever comes first. The next taxi will arrive in a time that is uniformly distributed between 0 and 10 minutes, while the next bus will arrive in exactly 5 minutes. Find the CDF and the expected value of Al's waiting time.

**Solution（解答）**（承上页）. Let $A$ be the event that Al will find a taxi waiting or will be picked up by the bus after 5 minutes. Note that the probability of boarding the next bus, given that Al has to wait, is

```math
P(\text{a taxi will take more than 5 minutes to arrive}) = \frac{1}{2}.
```

Al's waiting time, call it $X$, is a mixed random variable. With probability

```math
P(A) = \frac{2}{3} + \frac{1}{3} \cdot \frac{1}{2} = \frac{5}{6},
```

it is equal to its discrete component $Y$ (corresponding to either finding a taxi waiting, or boarding the bus), which has PMF

```math
p_Y(y) = \begin{cases}
\dfrac{2}{3P(A)}, & \text{if } y = 0, \\[0.4em]
\dfrac{1}{6P(A)}, & \text{if } y = 5,
\end{cases}
\qquad = \begin{cases}
\dfrac{12}{15}, & \text{if } y = 0, \\[0.4em]
\dfrac{3}{15}, & \text{if } y = 5.
\end{cases}
```

> <span style="color:#7f8c8d;">[This equation follows from the calculation</span>
>
> ```math
> p_Y(0) = P(Y = 0 \mid A) = \frac{P(Y = 0,\, A)}{P(A)} = \frac{2}{3P(A)}.
> ```
>
> <span style="color:#7f8c8d;">The calculation for $p_Y(5)$ is similar.]</span>

With the complementary probability $1 - P(A)$, the waiting time is equal to its continuous component $Z$ (corresponding to boarding a taxi after having to wait for some time less than 5 minutes), which has PDF

```math
f_Z(z) = \begin{cases}
1/5, & \text{if } 0 \le z \le 5, \\
0, & \text{otherwise}.
\end{cases}
```

The CDF is given by $F_X(x) = P(A)F_Y(x) + (1 - P(A))F_Z(x)$, from which

```math
F_X(x) = \begin{cases}
0, & \text{if } x < 0, \\[0.4em]
\dfrac{5}{6}\cdot\dfrac{12}{15} + \dfrac{1}{6}\cdot\dfrac{x}{5}, & \text{if } 0 \le x < 5, \\[0.4em]
1, & \text{if } 5 \le x.
\end{cases}
```

The expected value of the waiting time is

```math
E[X] = P(A)\,E[Y] + (1 - P(A))\,E[Z] = \frac{5}{6}\cdot 1 + \frac{1}{6}\cdot\frac{5}{2} = \frac{15}{12}.
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏（`5 3 . 1 5 / 6 2` 行碎裂），期望值一行按数学一致性与本页 CDF 重建为 $E[Y]=1$、$E[Z]=5/2$、结果 $15/12$。]</span>

<!-- ===== end PDF p197 ===== -->

<!-- ===== PDF p198 ===== -->
===== PDF p198 =====

（本章节是 **第 3 章　一般随机变量（General Random Variables）** 的习题区，页眉 `Chap. 3`，章内页码 188。）

<span style="color:#2471a3;">**[problem·续]**</span> <span style="color:#c0392b;">Problem 10（接前页，选自 3.1–3.2 相关习题区）</span>

<hr>

<span style="color:#2471a3;">**[problem]**</span> **Problem 10. \* Simulating a continuous random variable.**（模拟一个连续随机变量）

A computer has a subroutine that can generate values of a random variable $U$ that is uniformly distributed in the interval $[0,1]$. Such a subroutine can be used to generate values of a continuous random variable with given CDF $F(x)$ as follows. If $U$ takes a value $u$, we let the value of $X$ be a number $x$ that satisfies $F(x)=u$. For simplicity, we assume that the given CDF is strictly increasing over the range $S$ of values of interest, where $S = \{x \mid 0 < F(x) < 1\}$. This condition guarantees that for any $u \in (0,1)$, there is a unique $x$ that satisfies $F(x)=u$.

(a) Show that the CDF of the random variable $X$ thus generated is indeed equal to the given CDF.

(b) Describe how this procedure can be used to simulate an exponential random variable with parameter $\lambda$ (lambda，参数 λ).

(c) How can this procedure be generalized to simulate a discrete integer-valued random variable?

<span style="color:#2471a3;">**[solution]**</span> **Solution（解答）：**

(a) By definition, the random variables $X$ and $U$ satisfy the relation $F(X) = U$. Since $F$ is strictly increasing, we have for every $x$,

```math
X \le x \quad \text{if and only if} \quad F(X) \le F(x).
```

Therefore,

```math
P(X \le x) = P\bigl(F(X) \le F(x)\bigr) = P\bigl(U \le F(x)\bigr) = F(x),
```

where the last equality follows because $U$ is uniform. Thus, $X$ has the desired CDF.

(b) The exponential CDF has the form $F(x) = 1 - e^{-\lambda x}$ for $x \ge 0$. Thus, to generate values of $X$, we should generate values $u \in (0, 1)$ of a uniformly distributed random variable $U$, and set $X$ to the value for which $1 - e^{-\lambda x} = u$, or $x = -\ln(1 - u)\,/\,\lambda$.

(c) Let again $F$ be the desired CDF. To any $u \in (0,1)$, there corresponds a unique integer $x_u$ such that $F(x_u - 1) < u \le F(x_u)$. This correspondence defines a random variable $X$ as a function of the random variable $U$. We then have, for every integer $k$,

```math
P(X = k) = P\bigl(F(k-1) < U \le F(k)\bigr) = F(k) - F(k-1).
```

Therefore, the CDF of $X$ is equal to $F$, as desired.

> <span style="color:#7f8c8d;">注：原页 OCR 中指数参数 λ 多被识别为 `'x`、`>'x`、`,x`，例如 $F(x) = 1 - e^{-\lambda x}$ 与 $x = -\ln(1-u)/\lambda$，已按文中含义规范为 $\lambda$。</span>

<hr>

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">SECTION 3.3. Normal Random Variables（高斯/正态随机变量）</span>

<span style="color:#2471a3;">**[problem]**</span> **Problem 11.** Let $X$ and $Y$ be normal random variables with means 0 and 1, respectively, and variances 1 and 4, respectively.

(a) Find $P(X \le 1.5)$ and $P(X \le -1)$.

(b) Find the PDF of $(Y - 1)/2$.

(c) Find $P(-1 \le Y \le 1)$.

<span style="color:#2471a3;">**[problem]**</span> **Problem 12.** Let $X$ be a normal random variable with zero mean and standard deviation $\sigma$ (sigma，σ). Use the normal tables to compute the probabilities of the events $\{X \le k\sigma\}$ and $\{|X| \le k\sigma\}$ for $k = 1, 2, 3$.

<!-- ===== PDF p199 ===== -->
===== PDF p199 =====

> <span style="color:#7f8c8d;">第 3 章　一般随机变量（General Random Variables）—— 本章习题（Problems），教材第 189 页</span>

<!-- 习题区：按规范 §5，习题题干保持英文原文不译；带 * 的题（Problem 14）其英文 Solution 保留，仅「Solution（解答）」标签可标注中文。 -->

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 13.**</span>
A city's temperature is modeled as a normal random variable with mean and standard deviation both equal to 10 degrees Celsius. What is the probability that the temperature at a randomly chosen time will be less than or equal to 59 degrees Fahrenheit?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 14.***</span>
Show that the normal PDF satisfies the normalization property. **Hint**（提示）：The integral $\int_{-\infty}^{\infty} e^{-x^2/2}\, dx$ is equal to the square root of

```math
\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} e^{-(x^2+y^2)/2}\, dx\, dy,
```

and the latter integral can be evaluated by transforming to polar coordinates.

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#00838f;">**Solution（解答）：**</span>
We note that

```math
1 = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-x^2/2}\, dx
   = \sqrt{\frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} e^{-(x^2+y^2)/2}\, dx\, dy}
```

```math
   = \sqrt{\frac{1}{2\pi} \int_{0}^{2\pi} \int_{0}^{\infty} e^{-r^2/2}\, r\, dr\, d\theta}
   = \sqrt{\int_{0}^{\infty} e^{-r^2/2}\, r\, dr}
   = \sqrt{\int_{0}^{\infty} e^{-u}\, du}
   = 1,
```

where for the third equality, we use a transformation into polar coordinates, and for the fifth equality, we use the change of variables $u = r^2/2$. Thus, we have

```math
\int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}}\, e^{-x^2/2}\, dx = 1,
```

because the integral is positive. Using the change of variables $u = (x - \mu)/\sigma$, it follows that

```math
\int_{-\infty}^{\infty} f_X(x)\, dx
   = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\,\sigma}\, e^{-(x-\mu)^2/(2\sigma^2)}\, dx
   = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-u^2/2}\, du
   = 1.
```

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">第 3.4 节　多个随机变量的联合概率密度函数（Joint PDFs of Multiple Random Variables）</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#00838f;">**Problem 15.**</span>
A point is chosen at random (according to a uniform PDF) within a semicircle of the form $\{(x,y) \mid x^2 + y^2 \le r^2,\ y \ge 0\}$, for some given $r > 0$.

(a) Find the joint PDF of the coordinates $X$ and $Y$ of the chosen point.

<!-- ===== PDF p200 ===== -->
<!-- ===== PDF p200 ===== -->
<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">习题区（Problems, Chapter 3, p.190）</span>

本页为第 3 章章末习题区的延续页，承载 Problem 15 的后两问、Problem 16、Problem 17（带 *）、以及 Problem 18 至 19。依照规范，习题题干一律保留英文原文（Problem 题干不翻译），仅功能标签与位置说明用中文标注。

<span style="color:#2471a3;">**[problem]**</span> **Problem 15（续，承接上一页）**

( b ) Find the marginal PDF of $Y$ and use it to find $E[Y]$.

( c ) Check your answer in ( b ) by computing $E[Y]$ directly without using the marginal PDF of $Y$.

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 16. Consider the following variant of Buffon's needle problem (Example 3.11), which was investigated by Laplace.**

A needle of length $\ell$ is dropped on a plane surface that is partitioned in rectangles by horizontal lines that are $a$ apart and vertical lines that are $b$ apart. Suppose that the needle's length $\ell$ satisfies $\ell < a$ and $\ell < b$. What is the expected number of rectangle sides crossed by the needle? What is the probability that the needle will cross at least one side of some rectangle?

---

<span style="color:#2471a3;">**[problem·*]**</span> **Problem 17\. \* Estimating an expected value by simulation using samples of another random variable.**

Let $Y_1, \ldots, Y_n$ be independent random variables drawn from a common and known PDF $f_Y$. Let $S$ be the set of all possible values of $Y_i$,

```math
S = \bigl\{ y \mid f_Y(y) > 0 \bigr\}.
```

Let $X$ be a random variable with known PDF $f_X$, such that $f_X(y) = 0,\ \text{for all}\ y \notin S$. Consider the random variable

```math
Z = \frac{1}{n} \sum_{i=1}^{n} \frac{Y_i\, f_X(Y_i)}{f_Y(Y_i)}.
```

Show that

```math
E[Z] = E[X].
```

<span style="color:#00838f;">**Solution（解答、英文保留）：**</span>

We have

```math
E\left[ \frac{Y_i f_X(Y_i)}{f_Y(Y_i)} \right] = \int_S y\, \frac{f_X(y)}{f_Y(y)}\, f_Y(y)\, dy = \int_S y\, f_X(y)\, dy = E[X].
```

Thus,

```math
E[Z] = \frac{1}{n} \sum_{i=1}^{n} E\left[ \frac{Y_i f_X(Y_i)}{f_Y(Y_i)} \right] = \frac{1}{n} \sum_{i=1}^{n} E[X] = E[X].
```

---

<span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b;">SECTION 3.5. Conditioning（第 3.5 节　条件作用）</span>

<span style="color:#2471a3;">**[problem]**</span> **Problem 18. Let $X$ be a random variable with PDF**

```math
f_X(x) = \begin{cases} x/4, & \text{if } 1 \le x \le 3,\\ 0, & \text{otherwise}, \end{cases}
```

and let $A$ be the event $\{ X \ge 2 \}$.

( a ) Find $E[X]$, $P(A)$, $f_{X\mid A}(x)$, and $E[X \mid A]$.

( b ) Let $Y = X^2$. Find $E[Y]$ and $\operatorname{var}(Y)$.

---

<span style="color:#2471a3;">**[problem]**</span> **Problem 19. The random variable $X$ has the PDF**

```math
f_X(x) = \begin{cases} c\,x^{-2}, & \text{if } 1 \le x \le 2,\\ 0, & \text{otherwise}. \end{cases}
```

Find $E[X]$.

> <span style="color:#7f8c8d;">本页尾部 OCR 显示为零散的 "$= E[X]$ ." 片段，应为 Problem 19 求解（先定常数 $c$ 再求 $E[X]$）的开头，正文推测自本页延续至下一页。</span>
