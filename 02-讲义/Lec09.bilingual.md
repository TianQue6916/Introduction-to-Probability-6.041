# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 9 — Multiple Continuous Random Variables（多个连续随机变量）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; PDF review（本讲大纲与 PDF 复习）</span>

**阅读（Readings）**：教材 Sections 3.4–3.5。

**本讲大纲（Outline）**：
- PDF review（PDF 复习）。
- Multiple random variables（多个随机变量）：
  - conditioning（条件化）。
  - independence（独立性）。
- Examples（例题）。

**PDF 复习**：

> <span style="color:#7f8c8d;">图：样本空间上的事件 $\{a < X < b\}$ 对应 $f_X(x)$ 曲线下 $a$ 到 $b$ 的阴影面积。</span>

```math
P(a \le X \le b) = \int_a^b f_X(x)\, dx, \qquad P(x \le X \le x + \delta) \approx f_X(x) \cdot \delta, \qquad \mathrm{E}[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x)\, dx .
```

**Summary of concepts（概念对照表）**：

| 离散世界 | 连续世界 |
|:---:|:---:|
| $p_X(x)$ | $f_X(x)$ |
| $\sum_x x\, p_X(x) = \mathrm{E}[X]$ | $\int x f_X(x)\, dx = \mathrm{E}[X]$ |
| $F_X(x)$ | $F_X(x)$ |
| $\mathrm{var}(X)$ | $\mathrm{var}(X)$ |
| $p_{X,Y}(x, y)$ | $f_{X,Y}(x, y)$ |
| $p_{X|A}(x)$ | $f_{X|A}(x)$ |
| $p_{X|Y}(x \mid y)$ | $f_{X|Y}(x \mid y)$ |

> <span style="color:#7f8c8d;">Bertsekas §3.1, p.140, p.144–145（PDF 与期望的连续版复习）；§3.4, p.158 起（本讲 Readings 起点：联合 PDF）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这张概念对照表是本讲的"翻译字典"，也是整套连续化方法论的总装台。Lec 08 已完成前三行的翻译（$p_X \leftrightarrow f_X$、$\sum \leftrightarrow \int$、CDF 通用）；本讲的新行从第四行开始——$p_{X,Y} \leftrightarrow f_{X,Y}$（联合）、$p_{X|A} \leftrightarrow f_{X|A}$（条件于事件）、$p_{X|Y} \leftrightarrow f_{X|Y}$（条件于变量），正好对齐 Lec 07 在离散世界铺好的三条路。学习策略照旧：遇到任何新公式，先问"离散版长什么样"——几乎总是把求和换成积分、把表格换成曲面。卡点预警：字典里有一处不能机械直译——条件化于 $\{Y = y\}$ 是零概率事件，离散世界用"归一化一行"轻松过关，连续世界必须另起炉灶（本讲第四节的处理是全讲最精妙的一段）。大纲里的两个例题（Buffon 投针、折棍）则是两台演示机：一台演示"二维等可能模型如何算出 $\pi$"，一台演示分层建模。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Joint PDF $f_{X,Y}$（联合概率密度函数）</span>

```math
P\left((X, Y) \in S\right) = \iint_S f_{X,Y}(x, y)\, dx\, dy .
```
- **解释**：
```math
P(x \le X \le x + \delta,\ y \le Y \le y + \delta) \approx f_{X,Y}(x, y) \cdot \delta^2 .
```
- **期望**：
```math
\mathrm{E}[g(X, Y)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x, y)\, f_{X,Y}(x, y)\, dx\, dy .
```
- **从联合到边缘**：
```math
f_X(x) \cdot \delta \approx P(x \le X \le x + \delta) = \int f_{X,Y}(x, y)\, dy .
```
- **独立性**：称 $X$ 与 $Y$ independent（独立），若
```math
f_{X,Y}(x, y) = f_X(x) f_Y(y), \qquad \text{对所有 } x, y .
```

> <span style="color:#7f8c8d;">Bertsekas §3.4, p.158–164（定义与 $\delta^2$ 解释 p.159；边缘 PDF 与二维均匀例 p.160；联合 CDF p.162；期望值规则与线性特例 p.163；汇总框 p.164）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 第一性原理：联合 PDF 的量纲是"**每单位面积的概率**"——教材 p.159 的原话正是 $f_{X,Y}(a, c)$ 是 $(a, c)$ 附近的 "probability per unit area"；$\delta^2$ 解释即"密度 × 面积"，几何上是密度曲面下的**体积**，与单变量"密度 × 长度 = 面积"逐级放大。验证与旧知识的对接：边缘化公式 $f_X(x) = \int f_{X,Y}(x, y)\, dy$ 是"把另一维积掉"，恰如 Lec 06/07 里联合表格的"按列求和"；独立性判据 $f_{X,Y} = f_X f_Y$（对所有 $x, y$）与 Lec 07 的 $p_{X,Y} = p_X p_Y$（教材 p.112 汇总）逐字同构——注意"对所有取值"不可省略，这是 Lec 07 课堂例题（不可能格拆穿独立性）的连续版回声。期望值规则的线性特例 $\mathrm{E}[aX + bY + c] = a\,\mathrm{E}[X] + b\,\mathrm{E}[Y] + c$（教材 p.163）预告了 Lec 07 期望线性的连续版本。校准例：教材 Example 3.9（p.160）的 Romeo & Juliet 约会模型——单位正方形上均匀联合密度 $c = 1$，是最简单的二维等可能试验。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Buffon&rsquo;s needle（蒲丰投针）</span>

- 平行线间距为 $d$，针长为 $\ell$（设 $\ell < d$）。求 $P(\text{针与某条线相交})$。

> <span style="color:#7f8c8d;">图：一组间距 $d$ 的平行线，一根长 $\ell$ 的针斜搭其间——$x$ 为针中点到最近直线的距离，$\theta$ 为针与平行线的夹角。</span>

- 建模：$X \in [0, d/2]$ 为针中点到最近直线的距离；模型取 $X, \Theta$ uniform（均匀）且 independent（独立）：
```math
f_{X,\Theta}(x, \theta) = \frac{4}{\pi d}, \qquad 0 \le x \le \frac{d}{2},\ 0 \le \theta \le \frac{\pi}{2} .
```
- 相交条件：$X \le \dfrac{\ell}{2} \sin \Theta$。
```math
P\left(X \le \frac{\ell}{2} \sin \Theta\right) = \iint_{x \le \frac{\ell}{2} \sin \theta} f_X(x) f_\Theta(\theta)\, dx\, d\theta = \frac{4}{\pi d} \int_0^{\pi/2} \frac{\ell}{2} \sin \theta\, d\theta = \frac{2\ell}{\pi d} .
```

> <span style="color:#7f8c8d;">Bertsekas §3.4, p.161–162（Example 3.11: Buffon&rsquo;s needle，含史料与"实验估计 $\pi$"）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，历史与人物 + 验证）:**</span> 历史与人物：教材 p.161 记载，此问题由法国博物学家 Buffon（布丰）**于 1733 年提出并解决**，后世称"蒲丰投针实验"；教材 p.162 特别指出：既然 $P = \frac{2\ell}{\pi d}$，反复投针统计频率即可**实验估计 $\pi$**——用随机性逼近确定量，这是 Monte Carlo（蒙特卡洛）方法的思想祖先，与 CLRS 随机化算法"以随机换确定"的哲学一脉相承。验证每个零件：$f_{X,\Theta} = \frac{4}{\pi d}$ 的归一化——矩形面积 $\frac{d}{2} \cdot \frac{\pi}{2} = \frac{\pi d}{4}$，密度取倒数 $\frac{4}{\pi d}$ ✓（也可拆成 $f_X = \frac{2}{d}$ 乘 $f_\Theta = \frac{2}{\pi}$，独立性自洽）；相交条件：针端相对中点在垂直方向的投影是 $\frac{\ell}{2}\sin\theta$，不超过距离 $x$ 即不相交，故相交 $\iff X \le \frac{\ell}{2}\sin\Theta$；最后 $\int_0^{\pi/2} \sin\theta\, d\theta = 1$，故 $P = \frac{4}{\pi d} \cdot \frac{\ell}{2} \cdot 1 = \frac{2\ell}{\pi d}$ ✓。$\ell < d$ 的假设保证针至多与一条线相交，模型因此干净。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditioning（条件化）</span>

- 回顾：$P(x \le X \le x + \delta) \approx f_X(x) \cdot \delta$。
- 依此类比，希望有：
```math
P(x \le X \le x + \delta \mid Y \approx y) \approx f_{X|Y}(x \mid y) \cdot \delta .
```
- 由此引出定义：
```math
f_{X|Y}(x \mid y) = \frac{f_{X,Y}(x, y)}{f_Y(y)}, \qquad \text{若 } f_Y(y) > 0 .
```
- 对固定的 $y$，conditional PDF（条件概率密度函数）是联合 PDF 的一个（归一化的）"section"（切片）。
- 若独立（$f_{X,Y} = f_X f_Y$），则得
```math
f_{X|Y}(x \mid y) = f_X(x) .
```

> <span style="color:#7f8c8d;">Bertsekas §3.5, p.169–171（条件 PDF 的定义、解释与归一化）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 卡点诊断）:**</span> 第一性原理：定义式 $f_{X|Y} = f_{X,Y}/f_Y$ 在形式上与 Lec 06 的 $p_{X|Y} = p_{X,Y}/p_Y$ 一模一样，但它背后的逻辑难得多——事件 $\{Y = y\}$ 在连续世界里概率为**零**，Lec 01 的条件概率定义 $P(\cdot \mid A) = P(\cdot \cap A)/P(A)$ 直接失效（分母为零）。教材 p.171 的破解之道是**极限论证**：先条件化于正概率的窄带 $\{y \le Y \le y + \delta_2\}$，算出 $P(x \le X \le x + \delta_1 \mid y \le Y \le y + \delta_2) \approx \frac{f_{X,Y}(x,y)\,\delta_1 \delta_2}{f_Y(y)\,\delta_2} = f_{X|Y}(x \mid y)\,\delta_1$——$\delta_2$ 消失，窄带收窄到线即得定义 ✓。卡点诊断：$f_{X|Y}(x \mid y)$ 是 $x$ 的函数、$y$ 只是参数，且只在 $f_Y(y) > 0$ 处有定义；验证独立性推论：$f_{X|Y} = \frac{f_X f_Y}{f_Y} = f_X$ ✓——"知道 $Y$ 的值不改变 $X$ 的密度"，与 Lec 03 事件独立、Lec 07 变量独立是同一条原则在第三种对象上的落位。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Joint, Marginal and Conditional Densities（联合、边缘与条件密度）</span>

- 读图要点：
  - **Area of slice = Height of marginal density at $x$**：固定 $x$ 的切片面积 = 边缘密度在该处的高度。
  - **Slice through density surface for fixed $x$**：沿固定 $x$ 用竖直平面切开密度曲面所得的截面。
  - **Renormalizing slices for fixed $x$ gives conditional densities for $Y$ given $X = x$**：把各切片除以自身面积重新归一化，即得给定 $X = x$ 时 $Y$ 的条件密度。

> <span style="color:#7f8c8d;">图：三维密度曲面示意——曲面下总体积为 $1$；沿固定 $x$ 的一刀切出截面曲线，其面积即 $f_X(x)$；把截面缩放到面积为 $1$ 便得到 $f_{Y|X}(\cdot \mid x)$。图源：Image by MIT OpenCourseWare, adapted from *Probability*, by J. Pittman, 1999.</span>

> <span style="color:#7f8c8d;">Bertsekas §3.5, p.169–171（同主题可视化与"切片归一化"论证）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> 这页全图无公式，却把条件化最难的几何直觉画透了，读图分三步。第一步：联合密度 $f_{X,Y}$ 是一张"体积为 $1$"的曲面，概率 = 曲面下的体积。第二步：**边缘是切片面积的轨迹**——沿固定 $x$ 切一刀，截面曲线下的面积恰为 $f_X(x)$；把每个 $x$ 处的切片面积记录下来，就"压"出一维边缘密度（这正是 $f_X(x) = \int f_{X,Y}(x,y)\, dy$ 的几何读法）。第三步：**条件是切片形状的归一化**——单个切片的形状正比于 $f_{X,Y}(x, y)$ 沿 $y$ 的轮廓，除以切片面积 $f_X(x)$ 后总面积凑成 $1$，得到 $f_{Y|X}(\cdot \mid x)$。卡点诊断：边缘与条件用的是**同一批切片**的两种信息——面积回答"$X$ 落在 $x$ 附近的可能性"，形状回答"若真落在那里，$Y$ 如何分布"；分母 $f_Y(y)$ 与 $f_X(x)$ 的角色随切片方向对调，公式 $f_{X|Y}$ 与 $f_{Y|X}$ 因此成对出现。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Stick-breaking example（折棍例子）</span>

- 把长为 $\ell$ 的棍子折断两次：第一次在 $X$ 处折断，$X$ 在 $[0, \ell]$ 上均匀；再在 $Y$ 处折断，$Y$ 在 $[0, X]$ 上均匀。
```math
f_X(x) = \frac{1}{\ell}, \qquad f_{Y|X}(y \mid x) = \frac{1}{x} \ \ (0 \le y \le x),
```
```math
f_{X,Y}(x, y) = f_X(x)\, f_{Y|X}(y \mid x) = \frac{1}{\ell x}, \qquad 0 \le y \le x \le \ell .
```

> <span style="color:#7f8c8d;">图：左为 $f_X$（$[0, \ell]$ 上的平顶密度）与棍子在 $x$ 处折断的示意；右为 $f_{Y|X}$（$[0, x]$ 上的平顶密度，高度随 $x$ 变化）与第二段折断的示意。</span>

- 边缘与期望：
```math
f_Y(y) = \int f_{X,Y}(x, y)\, dx = \int_y^{\ell} \frac{1}{\ell x}\, dx = \frac{1}{\ell} \log \frac{\ell}{y}, \qquad 0 \le y \le \ell,
```
```math
\mathrm{E}[Y] = \int_0^{\ell} y f_Y(y)\, dy = \int_0^{\ell} \frac{y}{\ell} \log \frac{\ell}{y}\, dy = \frac{\ell}{4}, \qquad \mathrm{E}[Y \mid X = x] = \int y f_{Y|X}(y \mid X = x)\, dy = \frac{x}{2} .
```

> <span style="color:#7f8c8d;">Bertsekas §3.5, p.169–173（条件 PDF 乘法规则与条件期望机制）；同型折棍问题另见 §3.5 习题区 p.191（Problems 21–22）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 命名模板：**分层建模法**（sequential modeling）——不直接硬写联合密度，而是先给 $X$ 的规律、再给"给定 $X$ 后 $Y$ 的条件规律"，由乘法规则 $f_{X,Y} = f_X \cdot f_{Y|X}$（教材 p.172 汇总框）自动合成联合密度；折棍的物理顺序（先折 $X$、再折 $Y$）与公式顺序一一对应。逐项验算：$f_Y(y) = \int_y^{\ell} \frac{dx}{\ell x} = \frac{1}{\ell}(\ln \ell - \ln y) = \frac{1}{\ell} \ln \frac{\ell}{y}$ ✓；$\mathrm{E}[Y]$ 用换元 $u = y/\ell$ 化为 $\ell \int_0^1 u \ln \frac{1}{u}\, du = \ell \cdot \frac{1}{4} = \frac{\ell}{4}$ ✓（$\int_0^1 -u \ln u\, du = \frac{1}{4}$，恰是 100B 实分析的分部积分标准练习）；$\mathrm{E}[Y \mid X = x]$：给定 $X = x$ 后 $Y$ 在 $[0, x]$ 上均匀，均值自然是 $x/2$ ✓。对照读法：$\mathrm{E}[Y] = \ell/4$ 与 $\mathrm{E}[\mathrm{E}[Y \mid X]] = \mathrm{E}[X]/2 = \ell/4$ 相互印证——这正是全期望定理（Lec 06）在连续世界的预演，严格版本在 Lec 12 的 iterated expectations 登场。

> <span style="color:#1e8449;">**[note] Note（译者注，跨课程连接）:**</span> 跨课程连接：折棍的"先随机定 $X$、再在 $[0, X]$ 内随机定 $Y$"结构，与 CLRS 第 7 章 quicksort 的随机化分治完全同构——随机 pivot 把数组切成两段，各段再递归随机切分，"每层的切割点均匀随机"正是本例的分层均匀模型；两者的期望分析也都依赖"以条件期望分块、再汇总"的递归思路（quicksort 的期望比较次数方程与这里的 $\mathrm{E}[Y \mid X = x] = x/2$ 是同一套条件化语言）。回到 6.042J 的视角：折棍两次后得到三段，"三段能拼成三角形"是离散数学里的经典计数趣题，教材 p.191 的 Problems 21–22 恰好收录了折棍的概率版变体（比较不同折断次序下的分段分布）——学完本页的分母 $\ell x$ 与对数边缘密度，那些习题就有了现成的机械。卡点预警：$f_Y(y) = \frac{1}{\ell}\log\frac{\ell}{y}$ 在 $y \to 0^+$ 时趋于无穷，但它是合法 PDF（积分有限）——"密度可以无界"在连续世界是常态，勿与离散 PMF 的有界直觉混淆。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
