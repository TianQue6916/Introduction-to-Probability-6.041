# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 8 — Continuous Random Variables（连续随机变量）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Continuous r.v.&rsquo;s and pdf&rsquo;s（连续随机变量与概率密度函数）</span>

**阅读（Readings）**：教材 Sections 3.1–3.3。

**本讲大纲（Lecture outline）**：
- Probability density functions（概率密度函数）。
- Cumulative distribution functions（累积分布函数）。
- Normal random variables（正态随机变量）。

**正文**：一个 continuous r.v.（连续随机变量）由 probability density function（概率密度函数，PDF）$f_X$ 描述。

> <span style="color:#7f8c8d;">图：样本空间上的事件 $\{a < X < b\}$ 对应 $f_X(x)$ 曲线下从 $a$ 到 $b$ 的一块阴影面积。</span>

```math
P(a \le X \le b) = \int_a^b f_X(x)\, dx, \qquad \int_{-\infty}^{\infty} f_X(x)\, dx = 1,
```
```math
P(x \le X \le x + \delta) = \int_x^{x+\delta} f_X(s)\, ds \approx f_X(x) \cdot \delta, \qquad P(X \in B) = \int_B f_X(x)\, dx \quad (\text{对"好的"集合 } B) .
```

> <span style="color:#7f8c8d;">Bertsekas §3.1, p.140–141（PDF 定义、归一化、单点概率为零与 $\delta$ 解释）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 卡点诊断：$f_X(x)$ 不是概率，而是**概率的密度**——教材 p.141 的原话是"probability mass per unit length around $x$"（$x$ 附近单位长度上的概率质量），量纲是"概率/长度"，可以大于 1。真正的概率永远是密度下的**面积**：$P(a \le X \le b) = \int_a^b f_X\, dx$。由此立刻得到连续世界最反直觉的事实：$P(X = a) = \int_a^a f_X\, dx = 0$（教材 p.140），且区间端点开闭无关紧要——单点在连续模型里"轻如无物"，但零概率事件未必是不可能事件，它只是"测到精确值的可能性为零"。第一性原理：$\delta$-近似 $P(x \le X \le x + \delta) \approx f_X(x)\,\delta$ 不过是"小区间上密度近似不变"的局部线性化，它与 Lec 05 离散 PMF 的"收集—求和"逐字对应，只是求和换成了积分。幻灯片那句对 "nice" sets $B$ 的限定呼应教材 p.140 的脚注：$\int_B f_X\, dx$ 按寻常 Riemann（黎曼）意义理解——这你在 100B 实分析里恰好刚搭建完严格地基。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Means and variances（均值与方差）</span>

- 期望与期望值规则（求和换成积分）：
```math
\mathrm{E}[X] = \int_{-\infty}^{\infty} x f_X(x)\, dx, \qquad \mathrm{E}[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x)\, dx,
```
```math
\mathrm{var}(X) = \sigma_X^2 = \int_{-\infty}^{\infty} (x - \mathrm{E}[X])^2 f_X(x)\, dx .
```
- **Continuous uniform r.v.（连续均匀随机变量）**：

> <span style="color:#7f8c8d;">图：区间 $[a, b]$ 上高度恒定的平顶密度曲线。</span>

```math
f_X(x) = \begin{cases} \dfrac{1}{b-a}, & a \le x \le b, \\[2mm] 0, & \text{其他}. \end{cases}
```
- **课堂填空**：$\mathrm{E}[X] = \underline{\qquad}$
```math
\sigma_X^2 = \int_a^b \left(x - \frac{a+b}{2}\right)^2 \frac{1}{b-a}\, dx = \frac{(b-a)^2}{12} .
```

> <span style="color:#7f8c8d;">Bertsekas §3.1, p.144–146（期望定义 p.144、期望值规则与方差 p.145、Example 3.4 均匀分布的均值与方差 p.145–146）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 验算填空：$\mathrm{E}[X] = \int_a^b \dfrac{x}{b-a}\, dx = \dfrac{b^2 - a^2}{2(b-a)} = \dfrac{a+b}{2}$ ✓——密度关于中点 $\frac{a+b}{2}$ 对称，重心必落在对称中心，与教材 Example 3.4（p.145–146）"as one expects based on the symmetry" 的说法互相印证。幻灯片给出的方差积分也值得复算一遍：先算 $\mathrm{E}[X^2] = \dfrac{1}{b-a} \cdot \dfrac{b^3 - a^3}{3} = \dfrac{a^2 + ab + b^2}{3}$，再由矩公式 $\mathrm{var}(X) = \dfrac{a^2+ab+b^2}{3} - \dfrac{(a+b)^2}{4} = \dfrac{(b-a)^2}{12}$ ✓，与教材 p.146 一致。跨课程连接：把本例与 Lec 05 的离散均匀 $\{a, a+1, \ldots, b\}$ 对照（教材 p.90：$\mathrm{var} = \frac{(b-a)(b-a+2)}{12}$）——连续版的方差恰是"格点被抹平"后的极限，二者只差一个来自计数的 $+2$ 项；从离散到连续的过渡在这里第一次显出"积分替换求和、极限抹平格点"的全套语法，这正是 100B 实分析里 Riemann 和取极限的 probabilistic（概率论）化身。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Cumulative distribution function（CDF，累积分布函数）</span>

```math
F_X(x) = P(X \le x) = \int_{-\infty}^{x} f_X(t)\, dt .
```

> <span style="color:#7f8c8d;">图：左为 PDF $f_X$（$[a,b]$ 上的平顶），右为对应 CDF $F_X$——在 $a$ 前为 $0$，$[a,b]$ 上线性爬升，$b$ 后恒为 $1$。</span>

- 对离散随机变量同样成立：
```math
F_X(x) = P(X \le x) = \sum_{k \le x} p_X(k) .
```
- **例**：$p_X$ 在 $x = 1, 2, 4$ 处分别取 $1/6,\ 2/6,\ 3/6$。

> <span style="color:#7f8c8d;">图：左为 PMF（$x = 1, 2, 4$ 上高度 $1/6, 2/6, 3/6$ 的三根竖条），右为对应 CDF——阶梯曲线，台阶高度 $1/6 \to 3/6 \to 1$，分别在 $x = 1, 2, 4$ 处跃升。</span>

> <span style="color:#7f8c8d;">Bertsekas §3.2, p.148（CDF 定义与"用单一概念描述一切随机变量"的动机）；p.150（CDF 性质与 PMF/CDF 互化）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 第一性原理：CDF 是概率世界的"统一货币"。教材 p.148 的动机原话是：PMF 与 PDF 各管离散与连续，而 $F_X(x) = P(X \le x)$ 对**任何**随机变量都有定义——因为 $\{X \le x\}$ 总是一个事件。对离散变量它是右连续的阶梯（跳变高度 = 点质量），对连续变量它是连续曲线且 $F_X' = f_X$（教材 p.150 的性质清单与 PMF/CDF 互化公式：$F_X(k) = \sum_{i \le k} p_X(i)$，$p_X(k) = F_X(k) - F_X(k-1)$）。验算骰子例：$F_X(2) = \tfrac{1}{6} + \tfrac{2}{6} = \tfrac{3}{6}$ ✓，$F_X(4) = 1$ ✓。跨课程连接：PMF 与 CDF 的这层关系你在 CLRS 里见过同款——**前缀和与差分**互为逆运算：CDF 是 PMF 的前缀和，PMF 是 CDF 的差分；Lec 05 的"累积差分法"（四面骰 $p_X(2)$）正是反着用了一次。教材 Example 3.6（p.150–151，三次考试取最高分）会展示 CDF 的实战价值：有时先算 $F$ 再差分，比直接算 $p$ 便宜得多。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Mixed distributions（混合分布）</span>

- PDF 与 PMF 的组合之 schematic drawing（示意图）。

> <span style="color:#7f8c8d;">图：上半为 PDF/PMF 叠加示意——在 $x_0$ 处一根离散点质量的竖线（标注 $1/2$），叠加一段高度 $1/2$ 的平坦密度；下半为对应 CDF——纵轴可见 $1/4$、$1/2$、$3/4$、$1$ 刻度，曲线由竖直跳变段与线性爬升段拼成，最终到达 $1$。</span>

- 对应的 CDF：$F_X(x) = P(X \le x)$。

> <span style="color:#7f8c8d;">Bertsekas §3.2, p.148–150（用 CDF 统一处理离散/连续/混合随机变量的框架）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> 卡点诊断：mixed distribution（混合分布）= **离散点质量 + 连续密度的叠加**。它既没有处处存在的 PMF（连续部分给不出点概率），也没有处处可导的 PDF（点质量处密度"无穷高"），唯一的通用语言是 CDF：跳变的高度 = 该点的离散质量，线性爬升段的斜率 = 该段的连续密度。读图口诀：**竖直跳变看离散，斜坡看连续**——上半图中 $x_0$ 处标注 $1/2$ 的竖线使 CDF 一步跳升，平坦密度段则让 CDF 匀速爬坡，两段机制在一条曲线上和平共处。这正是教材 p.148 设计 CDF 的深层理由："用单一数学概念描述所有类型的随机变量"——无论离散、连续还是混合，$F_X(x) = P(X \le x)$ 一视同仁。工程里混合模型很常见：例如"以某概率恰好在整点发车（离散）+ 以其余概率在区间内随机到达（连续）"的复合等待时间，用 CDF 处理最省力。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Gaussian (normal) PDF（高斯/正态概率密度函数）</span>

- **Standard normal（标准正态）$N(0, 1)$**：
```math
f_X(x) = \frac{1}{\sqrt{2\pi}}\, e^{-x^2/2},
```

> <span style="color:#7f8c8d;">图：左为钟形的正态 PDF（峰在 $0$），右为对应的 S 形正态 CDF（$-1, 0, 1, 2$ 处的参考刻度）。</span>

- $\mathrm{E}[X] = 0$，$\mathrm{var}(X) = 1$。
- **General normal（一般正态）$N(\mu, \sigma^2)$**：
```math
f_X(x) = \frac{1}{\sigma\sqrt{2\pi}}\, e^{-(x-\mu)^2/(2\sigma^2)} .
```
- $\mathrm{E}[X] = \mu$，$\mathrm{var}(X) = \sigma^2$。
- 令 $Y = aX + b$：
  - **课堂填空**：$\mathrm{E}[Y] = \underline{\qquad}$，$\mathrm{var}(Y) = \underline{\qquad}$
  - **Fact（事实）**：$Y \sim N(a\mu + b,\ a^2\sigma^2)$。

> <span style="color:#7f8c8d;">Bertsekas §3.3, p.153–155（正态 PDF 的钟形与归一化；p.154：线性变换保正态、标准正态 CDF $\Phi$ 的定义）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 验算两个空栏：由期望的线性 $\mathrm{E}[Y] = \mathrm{E}[aX + b] = a\,\mathrm{E}[X] + b = a\mu + b$ ✓；由 Lec 05 的缩放规则 $\mathrm{var}(Y) = \mathrm{var}(aX + b) = a^2\, \mathrm{var}(X) = a^2 \sigma^2$ ✓——两条都是旧规则的直接代账，而幻灯片的 Fact 更进一步：$Y$ 不仅参数如此，**整个分布仍是正态**。教材 p.154 把这条命名为 "Normality is Preserved by Linear Transformations"（线性变换保持正态性），其严格证明要等 Lec 10 的 derived distributions（导出分布）工具。跨课程连接：归一化常数 $\frac{1}{\sqrt{2\pi}}$ 背后是著名的高斯积分 $\int_{-\infty}^{\infty} e^{-y^2/2} dy = \sqrt{2\pi}$（教材 p.154 以 $\frac{1}{\sqrt{2\pi}}\int e^{-y^2/2} dy = 1$ 的形式引用）——这个反常积分的收敛与求值正是 100B 实分析练过的基本功；而"为什么钟形无处不在"的最终答案是中心极限定理（Lec 20）：大量独立因素的叠加效应趋于正态，教材 p.157 末尾已埋下这句预告。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Calculating normal probabilities（计算正态概率）</span>

- 正态 CDF **没有 closed form（闭式表达式）**。
  - 但有现成的 table（数表）——针对标准正态。
- 若 $X \sim N(\mu, \sigma^2)$，则
```math
\frac{X - \mu}{\sigma} \sim N\left(\underline{\qquad}\right) .
```
- **例**：$X \sim N(2, 16)$：
```math
P(X \le 3) = P\left(\frac{X-2}{4} \le \frac{3-2}{4}\right) = \Phi(0.25) .
```

> <span style="color:#7f8c8d;">图：标准正态分布表——行 $0.0$–$2.8$、列 $.00$–$.09$，给出 $\Phi(z)$ 的四位小数取值（教材同款表见 p.155）。</span>

> <span style="color:#7f8c8d;">Bertsekas §3.3, p.154–157（$\Phi$ 的定义与对称性 $\Phi(-y) = 1 - \Phi(y)$ 见 p.154；正态表 p.155；标准化两步法与 Example 3.7 见 p.156–157）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验算填空：$\frac{X-\mu}{\sigma} \sim N(0, 1)$ ✓——标准化就是把"中心搬回原点、尺度缩成 1"，参数归零归一后才能查同一张表。例题收尾：查表（行 $0.2$、列 $.05$）得 $\Phi(0.25) = 0.5987$ ✓（教材 p.155 的表逐位一致），故 $P(X \le 3) \approx 0.5987$。教材 p.156–157 的两步法（先 standardize、再查表）与 Example 3.7（降雪量 $N(60, 20^2)$，求 $P(X \ge 80) = 1 - \Phi(1) = 0.1587$）是同一套流程。卡点诊断：为什么只能查表？因为 $e^{-x^2}$ 的原函数不是初等函数（100B/微积分视角下的经典事实），"无闭式"是数学本性而非表格匮乏。对称性 $\Phi(-y) = 1 - \Phi(y)$（教材 p.154，例：$\Phi(-0.5) = 1 - 0.6915 = 0.3085$）让半张表覆盖整条数轴——负值、反向区间全靠它换算，做题时先标准化、再翻对称、最后查表。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The constellation of concepts（概念星座）</span>

> <span style="color:#7f8c8d;">图：两列对照的概念图——左列离散：$p_X(x)$、$F_X(x)$、$\mathrm{E}[X], \mathrm{var}(X)$、$p_{X,Y}(x,y)$、$p_{X|Y}(x|y)$；右列连续：$f_X(x)$、$F_X(x)$、$f_{X,Y}(x,y)$、$f_{X|Y}(x|y)$；上下行按"单个变量 / 联合 / 条件"排布。</span>

- 离散世界与连续世界共享同一套概念星座：PMF 对 PDF、联合对联合、条件对条件，期望与方差的算法一脉相承。

> <span style="color:#7f8c8d;">Bertsekas §2.5, p.92（离散联合分布列对照）；§3.4, p.158（下一讲：联合 PDF）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这页"星座图"是本讲的方法论总结，也是接下来两讲的学习地图：**字典式学习法**——不背新定理，而是把第 2 章的每条离散公式逐条"翻译"成连续版本：$p_X \leftrightarrow f_X$、$\sum \leftrightarrow \int$、$\sum\sum \leftrightarrow \int\int$。翻译后的句子结构不变：期望值规则、归一化、条件化、独立性全部平移。已翻译完的条目：单变量 PMF→PDF（本讲）、期望与方差（§3.1, p.144–145）、CDF 的统一表达（§3.2, p.148）。尚未翻译的条目留作悬念：联合 $p_{X,Y} \to f_{X,Y}$ 与条件 $p_{X|Y} \to f_{X|Y}$（教材 §3.4, p.158 起）正是下一讲 Lec 09 的正餐。卡点预警：翻译中有一处"语法例外"——连续情形下条件化于 $\{Y = y\}$ 这个零概率事件需要全新论证（切片取极限），不是逐字替换就能糊弄过去的；下一讲会专门拆解这个精妙之处。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
