# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 10 — Continuous Bayes rule; Derived distributions（连续贝叶斯法则；导出分布）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Review（复习：从离散到连续的词典）</span>

**阅读（Readings）**：教材 Section 3.6；开始 Section 4.1。

**复习（Review）**——第 2 章的离散机器与第 3 章的连续机器逐行对应（左：离散，右：连续）：

| 离散 | 连续 |
|:---:|:---:|
| $p_X(x)$ | $f_X(x)$ |
| $p_{X,Y}(x,y)$ | $f_{X,Y}(x,y)$ |
| $p_{X|Y}(x \mid y) = \dfrac{p_{X,Y}(x,y)}{p_Y(y)}$ | $f_{X|Y}(x \mid y) = \dfrac{f_{X,Y}(x,y)}{f_Y(y)}$ |
| $p_X(x) = \displaystyle\sum_y p_{X,Y}(x,y)$ | $f_X(x) = \displaystyle\int_{-\infty}^{\infty} f_{X,Y}(x,y)\, dy$ |

无论离散连续都通用的两件工具：$F_X(x) = P(X \le x)$，以及 $\mathrm{E}[X]$、$\mathrm{var}(X)$。

> <span style="color:#7f8c8d;">Bertsekas §3.5, p.165–167；§3.6, p.179–182</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这一页是全讲的总纲：把 Lec 05–07 在离散世界攒下的机器（PMF 分布列、联合/条件分布列、边缘化求和）逐行翻译到连续世界——分布列换 PDF（概率密度函数）、求和换积分，而 CDF（累积分布函数）与期望、方差两件工具原封不动。经核对教材页码，§3.5 Conditioning（p.165 起）给出条件 PDF 与混合情形的成套公式，§3.6 The Continuous Bayes' Rule（p.179–182）是本讲阅读的第一站。本讲的战略分两段：前半把贝叶斯法则的四种组合（离散/连续的 $X$ 与 $Y$ 搭配）一次配齐，后半进入 derived distributions（导出分布）这门新工艺——已知 $X$ 的概率规律，求 $g(X)$ 乃至 $g(X,Y)$ 的规律。前者是"条件化的收尾"，后者是"函数的随机变量"的开篇，两者的公共底座都是这页词典。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The Bayes variations（贝叶斯法则的种种变体）</span>

离散情形的贝叶斯法则（乘法公式代换分子）：
```math
p_{X|Y}(x \mid y) = \frac{p_{X,Y}(x,y)}{p_Y(y)} = \frac{p_X(x)\, p_{Y|X}(y \mid x)}{p_Y(y)}, \qquad p_Y(y) = \sum_x p_X(x)\, p_{Y|X}(y \mid x).
```
**例**：$X \in \{1, 0\}$——天空中有/没有飞机；$Y \in \{1, 0\}$——雷达上有没有记录到点什么。

> <span style="color:#7f8c8d;">Bertsekas §3.5, p.165–167</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 用译者为雷达例自设的数值跑一遍（模型结构照幻灯片）：先验 $p_X(1) = 0.05$（有飞机），似然 $p_{Y|X}(1 \mid 1) = 0.99$（真有飞机时报警的概率）、$p_{Y|X}(1 \mid 0) = 0.10$（误报率）。全概率公式给分母 $p_Y(1) = 0.05 \times 0.99 + 0.95 \times 0.10 = 0.0495 + 0.095 = 0.1445$，贝叶斯法则给后验 $p_{X|Y}(1 \mid 1) = 0.0495 / 0.1445 \approx 0.343$ ✓——听到警报，飞机在场的概率也只有约三分之一，因为先验太悬殊；这正是"先验 × 似然 → 后验"的语义。再验算幻灯片右端等式：由乘法公式 $p_{X,Y} = p_X\, p_{Y|X}$（Lec 06 已见），两个分式恒等 ✓。分母 $p_Y(y)$ 的角色是归一化：把似然按先验加权混成"证据"，除掉它后验质量和恰为 1。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Continuous counterpart（连续的对应版本）</span>

```math
f_{X|Y}(x \mid y) = \frac{f_{X,Y}(x,y)}{f_Y(y)} = \frac{f_X(x)\, f_{Y|X}(y \mid x)}{f_Y(y)}, \qquad f_Y(y) = \int_x f_X(x)\, f_{Y|X}(y \mid x)\, dx .
```
**例**：$X$：某个信号，"先验" $f_X(x)$；$Y$：$X$ 的含噪版本（noisy version）；$f_{Y|X}(y \mid x)$：噪声模型。

> <span style="color:#7f8c8d;">Bertsekas §3.6, p.179–181</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Discrete X, Continuous Y（离散 X、连续 Y）</span>

```math
p_{X|Y}(x \mid y) = \frac{p_X(x)\, f_{Y|X}(y \mid x)}{f_Y(y)}, \qquad f_Y(y) = \sum_x p_X(x)\, f_{Y|X}(y \mid x).
```
**例**：$X$：离散信号，"先验" $p_X(x)$；$Y$：$X$ 的含噪版本；$f_{Y|X}(y \mid x)$：连续噪声模型。

> <span style="color:#7f8c8d;">Bertsekas §3.5, p.169–172</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Continuous X, Discrete Y（连续 X、离散 Y）</span>

```math
f_{X|Y}(x \mid y) = \frac{f_X(x)\, p_{Y|X}(y \mid x)}{p_Y(y)}, \qquad p_Y(y) = \int_x f_X(x)\, p_{Y|X}(y \mid x)\, dx .
```
**例**：$X$：连续信号（如光束的 intensity（强度）），"先验" $f_X(x)$；$Y$：受 $X$ 影响的离散随机变量（如 photon count（光子计数））；$p_{Y|X}(y \mid x)$：该离散随机变量的模型。

> <span style="color:#7f8c8d;">Bertsekas §3.5, p.169–172</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> 两种混合情形最容易翻车的是"求和还是积分"。判据只看被边缘化变量的类型：给连续 $Y$ 求 $f_Y(y)$，对离散 $X$ 求和——$f_Y(y) = \sum_x p_X(x)\, f_{Y|X}(y \mid x)$，这是"几条噪声密度按先验权重混合成 mixture（混合密度）"；给离散 $Y$ 求 $p_Y(y)$，对连续 $X$ 积分——$p_Y(y) = \int f_X(x)\, p_{Y|X}(y \mid x)\, dx$，这是"按连续先验加权平均离散似然"。分子一侧同理：$p_{X|Y}(x \mid y) = p_X(x) f_{Y|X}(y \mid x) / f_Y(y)$ 里"点概率乘密度"并不违和，量纲由分母统一。卡点：$p_{Y|X}(y \mid x)$ 是"给定 $X = x$ 时事件 $\{Y = y\}$"的普通条件概率，不是密度，所以"连续 $X$、离散 $Y$"一侧不会出现"单点概率为零"的尴尬。光子计数的直觉：光束越亮，单位时间的计数越容易偏大。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">What is a derived distribution（什么是导出分布）</span>

- 它是"一个或多个具有已知概率规律的随机变量的函数"的 PMF 或 PDF。例如下图：

> <span style="color:#7f8c8d;">图：单位正方形上的均匀联合密度 $f_{X,Y}(y,x) = 1$（横轴 $x$、纵轴 $y$）；"求 $g(X,Y) = Y/X$ 的 PDF"就是一次导出分布计算（下一讲完整求解）。</span>

- 求出 $g(X,Y) = Y/X$ 的 PDF，就涉及 deriving a distribution（导出一个分布）。
- 注意：$g(X,Y)$ 本身是一个随机变量。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.202</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 导出分布的第一性原理只有一句话：随机变量的函数仍是随机变量，其分布由原分布经映射诱导。$(X,Y)$ 落在平面小区域 $dA$ 内的概率是 $f_{X,Y}(x,y)\, dA$；函数 $g$ 把这些"质量块"搬到 $z = g(x,y)$ 轴上重新摆放，摆好后的质量密度就是 $f_Z$——所以本质问题永远是"原空间里哪些区域被映到 $z$ 附近"。这也解释了导出分布为何一般难写：区域形状随 $g$ 变形，只有 $g$ 单调或线性时才有一行公式（下一讲）。本页刻意选了 $Z = Y/X$ 这个"会切出两种几何形状"的函数作演示，此处只需记住幻灯片的提醒：$g(X,Y)$ 是定义在 $\Omega$ 上的函数，谈它的分布之前先承认这个身份；而"何时值得算分布、何时绕开"，正是下一页的话题。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">When not to find them（何时不必求出导出分布）</span>

- 若只想计算期望，就不需要 $g(X,Y)$ 的 PDF：
```math
\mathrm{E}[g(X,Y)] = \iint g(x,y)\, f_{X,Y}(x,y)\, dx\, dy .
```

> <span style="color:#7f8c8d;">Bertsekas §3.4, p.161–164</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">How to find them（如何求导出分布：离散情形）</span>

- 对 $Y = g(X)$ 的每个可能取值求出概率质量：
```math
p_Y(y) = P(g(X) = y) = \sum_{x:\, g(x)=y} p_X(x) .
```

> <span style="color:#7f8c8d;">图：每个 $x$ 经函数 $g$ 映到 $y$ 轴上的对应点；若干个 $x$ 挤进同一个 $y$ 时，把它们的概率质量相加、堆到该点。</span>

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.213–215</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The continuous case（连续情形）</span>

**两步走（two-step procedure）**：
- 先求 $Y$ 的 CDF：$F_Y(y) = P(Y \le y)$；
- 再求导：$f_Y(y) = \dfrac{dF_Y}{dy}(y)$。

**例**：$X$ 在 $[0, 2]$ 上 uniform（均匀）分布，求 $Y = X^3$ 的 PDF。
- 解：
```math
F_Y(y) = P(Y \le y) = P(X^3 \le y) = P(X \le y^{1/3}) = \frac{y^{1/3}}{2},
```
```math
f_Y(y) = \frac{dF_Y}{dy}(y) = \frac{1}{6\, y^{2/3}} .
```

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.211–213</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 逐步验算：$X \sim U[0,2]$，$Y = X^3$；因 $g$ 严格递增，"$X^3 \le y$"可等价改写为"$X \le y^{1/3}$"，故 $F_Y(y) = \frac{1}{2} y^{1/3}$（$0 \le y \le 8$），求导得 $f_Y(y) = \frac{1}{6} y^{-2/3}$ ✓（与幻灯片一致）。归一化检验：$\int_0^8 \frac{1}{6} y^{-2/3} dy = \frac{1}{6} \cdot 3 y^{1/3} \big|_0^8 = \frac{1}{6} \cdot 6 = 1$ ✓。三个卡点：其一，PDF 必须连同定义域 $0 \le y \le 8$ 书写（板书省略了；$y > 8$ 时 $F_Y = 1$、$f_Y = 0$，$y < 0$ 时均为 0）；其二，$y \to 0^+$ 时密度无界"爆表"，但 $\int_0^\epsilon$ 有限——可积的奇异点完全合法；其三，"开三次方"依赖单调性：若 $g$ 不单调，等价改写要按分支拆开，这正是下一讲一般公式中 $|dg/dx|$ 登场的理由。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example（例：波士顿到纽约的车程）</span>

- Joan 从 Boston 开车去 New York，车速在 30–60 mph 之间均匀分布。行程时间（duration of the trip）的分布是什么？
- 令 $T(V) = \dfrac{200}{V}$，求 $f_T(t)$。

> <span style="color:#7f8c8d;">图：$V$ 的 PDF——在 $[30, 60]$ 上高度恒为 $1/30$ 的均匀密度，横轴标注 $30$ 与 $60$。</span>

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.211–213</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 完整求解：$T = 200/V$ 关于 $V$ 递减，不等号要翻转：$F_T(t) = P(T \le t) = P(V \ge 200/t)$。支撑集由 $30 \le 200/t \le 60$ 给出 $10/3 \le t \le 20/3$（小时）。区间内 $F_T(t) = \int_{200/t}^{60} \frac{1}{30} dv = 2 - \frac{20}{3t}$，求导得 $f_T(t) = \frac{20}{3 t^2}$ ✓。归一化：$\int_{10/3}^{20/3} \frac{20}{3t^2} dt = \frac{20}{3}\left(\frac{3}{10} - \frac{3}{20}\right) = 1$ ✓。期望走两条路互相印证：期望值规则（上一节"何时不必求分布"）给 $\mathrm{E}[T] = \int_{30}^{60} \frac{200}{v} \cdot \frac{1}{30} dv = \frac{20}{3} \ln 2 \approx 4.62$ 小时；导出密度给 $\int t\, f_T(t)\, dt = \frac{20}{3} \ln\frac{20/3}{10/3} = \frac{20}{3} \ln 2$ ✓ 完全一致。卡点诊断：变换递减时 CDF 的"$\ge$"是最常见的翻车点；另一处是把支撑端点写错——端点由 $V$ 的端点经 $t = 200/v$ 映射而来，不是照抄 $[30, 60]$。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The pdf of Y = aX + b（线性函数 Y = aX + b 的 PDF）</span>

$Y = 2X + 5$：

> <span style="color:#7f8c8d;">图：三张 PDF 的对比——$f_X$、经缩放得到的 $f_{aX}$（横轴拉伸、高度压低）、再平移得到的 $f_{aX+b}$（整体右移）；横轴标注 $-2$、$3$ 等端点随"拉伸 $\times 2$、右移 $5$"而移动。</span>

```math
f_Y(y) = \frac{1}{|a|}\, f_X\!\left(\frac{y - b}{a}\right).
```
- 用它检验：若 $X$ 是 normal（正态）随机变量，则 $Y = aX + b$ 也是正态。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.202；§3.3, p.154</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 跨课程连接）:**</span> 从量纲看线性变换：$f_X$ 是"每单位 $x$ 长度上的概率质量"，$Y = aX + b$ 把 $x$ 轴拉伸 $|a|$ 倍再平移——长 $\Delta x$ 的区间映成长 $|a| \Delta x$ 的区间，质量不变，密度必须除以 $|a|$，这就是 $f_Y(y) = \frac{1}{|a|} f_X\big(\frac{y-b}{a}\big)$ 的第一性来源：总面积守恒。正态检验：代入正态密度并配方，指数化为 $-\frac{(y - b - a\mu)^2}{2 a^2 \sigma^2}$，得 $Y \sim N(a\mu + b,\ a^2 \sigma^2)$ ✓——教材 §3.3（p.154）早早预告"线性变换保持正态性"，并注明将在 Section 4.1 兑现，本页正是兑现处。跨课程连接：用 Strang 线性代数的语言，$aX + b$ 是一维 affine（仿射）映射，因子 $1/|a|$ 是 Jacobian（雅可比行列式）的一维特例；下一讲把它推广为一般单调 $g$ 的 $f_X(x) / |g'(x)|$。幻灯片的 $Y = 2X + 5$ 图像口诀：先拉伸压矮、再整体右移。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
