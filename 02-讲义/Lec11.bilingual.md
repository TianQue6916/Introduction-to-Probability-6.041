# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 11 — Derived distributions; convolution; covariance and correlation（导出分布；卷积；协方差与相关系数）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture overview（本讲导读）</span>

**阅读（Readings）**：完成 Section 4.1；Section 4.2。

本讲三条战线：导出分布收尾（一般单调公式；两个随机变量的函数之和与比）；convolution（卷积）——独立随机变量之和的分布；covariance（协方差）与 correlation（相关系数）——两个变量如何共舞的度量。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.202–218；§4.2, p.217–222</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲三条战线层层递进。其一，把上讲的两步 CDF 法压缩成一行公式——$g$ 严格单调时 $f_Y(y) = f_X(x) / |g'(x)|$，并把函数从一元推广到二元（和与比值）；其二，卷积：独立随机变量之和的分布怎么求，离散、连续各一套；其三，协方差与相关系数——不再制造新分布，而是给"两个变量的联动"造一个无量纲的度量，为下一讲的条件期望与"随机个随机变量之和"备好零件。经核对页码，§4.1 Derived Distributions（p.202 起，卷积小节在 p.213–218）本讲读完收尾，§4.2 Covariance and Correlation（标题页 p.217、总结页 p.222）随后展开——阅读说明里的"Finish Section 4.1"正指补完上讲只开了头的 §4.1。上讲铺垫的 $Y = X^3$ 与 $Y = aX + b$ 两例，将在本讲获得统一的公式化解释。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">A general formula（一般公式）</span>

- 设 $Y = g(X)$，$g$ strictly monotonic（严格单调）。

> <span style="color:#7f8c8d;">图：曲线 $y = g(x)$，在 $x$ 处标注斜率 $\frac{dg}{dx}(x)$；横轴上的小区间 $[x,\ x + \delta]$ 被曲线映到纵轴上对应的小区间 $[y,\ y + \cdot]$。</span>

- 事件 $\{x \le X \le x + \delta\}$ 与 $\{g(x) \le Y \le g(x + \delta)\}$ 相同，近似地即 $\{g(x) \le Y \le g(x) + \delta\, |(dg/dx)(x)|\}$。
- 因此（$y = g(x)$）：
```math
\delta\, f_X(x) = \delta\, f_Y(y)\, \left| \frac{dg}{dx}(x) \right| \qquad \Longrightarrow \qquad f_Y(y) = \frac{f_X(x)}{\left| \frac{dg}{dx}(x) \right|} .
```

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.211–213</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 公式的发动机是概率质量守恒：$x$ 处长 $\delta$ 的小段含质量 $\delta f_X(x)$；$g$ 严格单调时它被一一映到 $y = g(x)$ 附近长约为 $\delta\, |g'(x)|$ 的小段，该段质量是 $\delta f_Y(y)\, |g'(x)|$。两者是同一批质量的两种记账，相等；除以 $\delta$ 取极限即得 $f_Y(y) = f_X(x) / |g'(x)|$（$y = g(x)$）。绝对值照顾递减情形：$g$ 下降时像区间在 $y$ 轴上反向放置，长度仍是 $|g'| \delta$——上讲的 $T = 200/V$ 就吃到了这个负号。与上讲对账：$Y = X^3$，$g' = 3x^2$，反解 $x = y^{1/3}$，$f_X(x) = 1/2$，代入得 $f_Y(y) = \frac{1}{2} \cdot \frac{1}{3 y^{2/3}} = \frac{1}{6 y^{2/3}}$ ✓，与两步 CDF 法逐点吻合。卡点：使用公式必须配套"反解 $x = g^{-1}(y)$"并逐段携带定义域；$g'(x) = 0$ 的驻点处公式失效，需回退到 CDF 法单独处理。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example: the ratio Z = Y/X（例：比值 Z = Y/X 的分布）</span>

> <span style="color:#7f8c8d;">图：单位正方形上 $f_{X,Y}(y,x) = 1$ 的均匀联合密度（横轴 $x$、纵轴 $y$、高度 $1$）；任务是求 $Z = g(X, Y) = Y/X$ 的 PDF。</span>

**课堂填空**：
- 当 $z \le 1$：$F_Z(z) = \underline{\qquad}$
- 当 $z \ge 1$：$F_Z(z) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.215–218</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 逐段推导并验算：$F_Z(z) = P(Y/X \le z) = P(Y \le zX)$（$X \ge 0$ 可直接乘过去）。$0 \le z \le 1$：直线 $y = zx$ 从单位正方形切下三角形，面积 $\int_0^1 zx\, dx = z/2$，故 $F_Z(z) = z/2$ ✓。$z \ge 1$：取补集更省事——正方形内 $y > zx$ 的三角形面积 $\int_0^{1/z} (1 - zx)\, dx = \frac{1}{2z}$，故 $F_Z(z) = 1 - \frac{1}{2z}$ ✓。$z < 0$ 时 $F_Z(z) = 0$（两变量非负）。连续性对账：$F_Z(1^-) = 1/2 = F_Z(1^+)$ ✓；又由 $X, Y$ 地位对称，$P(Y \le X) = 1/2$ 本在情理之中。求导得 $f_Z(z) = 1/2$（$0 < z \le 1$）、$f_Z(z) = 1/(2z^2)$（$z \ge 1$）；归一化 $\frac{1}{2} + \int_1^\infty \frac{dz}{2z^2} = \frac{1}{2} + \frac{1}{2} = 1$ ✓。卡点诊断：比值分布的右尾按 $1/z^2$ 衰减得很慢——分母偶尔贴近 $0$ 会制造极端比值，这是比率型统计量的通病，值得记住。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The distribution of X + Y（X + Y 的分布：离散情形）</span>

- $W = X + Y$；$X, Y$ independent（独立）。

> <span style="color:#7f8c8d;">图：二维格点图——把 $(x, y)$ 格点摆平面，质量沿斜线 $x + y = w$ 收集；图中 $w = 3$ 的对角线上标出 $(0,3), (1,2), (2,1), (3,0)$ 四个点。</span>

```math
p_W(w) = P(X + Y = w) = \sum_x P(X = x)\, P(Y = w - x) = \sum_x p_X(x)\, p_Y(w - x).
```
- **Mechanics（机械步骤）**：
  - 把两张 PMF 上下对齐摆放；
  - 翻转（flip）$Y$ 的 PMF；
  - 把翻转后的 PMF 平移 $w$（$w > 0$ 时向右移）；
  - 逐点交叉相乘再相加。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.213–218</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 跨课程连接）:**</span> 命名模板——flip-and-shift（翻转–平移）卷积机械：把 $p_Y$ 翻转得 $p_Y(-x)$、平移 $w$、与 $p_X$ 逐点相乘再累加，输出恰为 $p_W(w) = \sum_x p_X(x) p_Y(w - x)$。最小验算：$X, Y$ 独立同取 $\{0, 1\}$ 上均匀，则 $p_W(0) = 1/4$、$p_W(1) = 1/2$、$p_W(2) = 1/4$ ✓——与二项 $B(2, 1/2)$ 完全一致，且 $\mathrm{E}[W] = 1$ 与 Lec 07 的期望线性吻合。跨课程连接：你在 6.042J 见过生成函数——独立和的 PGF 等于各自 PGF 的乘积，"多项式相乘、按 $w$ 次幂收集系数"正是 $\sum_x p_X(x) p_Y(w - x)$ 的代数化身；flip-shift 的几何操作与多项式乘法的对位是同一件事的两面。这页"沿斜线 $x + y = w$ 收集质量"的格点图像值得在脑中存一份——下一页它将被积分解读。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The continuous case（连续情形：卷积）</span>

- $W = X + Y$；$X, Y$ 独立。

> <span style="color:#7f8c8d;">图：把格点图换成连续平面——质量沿直线 $x + y = w$ 收集，竖直线 $x$ 固定处，$w$ 轴上平移量为 $w - x$。</span>

- 给定 $X = x$，$W = x + Y$ 只是 $Y$ 的平移：$f_{W|X}(w \mid x) = f_Y(w - x)$。
- 乘法公式展开联合密度：$f_{W,X}(w, x) = f_X(x)\, f_{W|X}(w \mid x) = f_X(x)\, f_Y(w - x)$。
- 对 $x$ 积分（边缘化）：
```math
f_W(w) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(w - x)\, dx .
```

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.217–218</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Two independent normal r.v.s（两个独立的正态随机变量）</span>

- $X \sim N(\mu_x, \sigma_x^2)$，$Y \sim N(\mu_y, \sigma_y^2)$，相互独立：
```math
f_{X,Y}(x, y) = f_X(x)\, f_Y(y) = \frac{1}{2\pi \sigma_x \sigma_y} \exp\!\left( -\frac{(x - \mu_x)^2}{2\sigma_x^2} - \frac{(y - \mu_y)^2}{2\sigma_y^2} \right).
```
- 该 PDF 在椭圆 $\dfrac{(x - \mu_x)^2}{2\sigma_x^2} + \dfrac{(y - \mu_y)^2}{2\sigma_y^2} =$ 常数 上取常值。
- $\sigma_x = \sigma_y$ 时椭圆成为圆（circle）。

> <span style="color:#7f8c8d;">Bertsekas §3.4, p.157–164；§3.3, p.154</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The sum of independent normal r.v.s（独立正态随机变量之和）</span>

- $X \sim N(0, \sigma_x^2)$，$Y \sim N(0, \sigma_y^2)$，独立；令 $W = X + Y$：
```math
f_W(w) = \int_{-\infty}^{\infty} f_X(x)\, f_Y(w - x)\, dx = \frac{1}{2\pi \sigma_x \sigma_y} \int_{-\infty}^{\infty} e^{-x^2/2\sigma_x^2}\, e^{-(w - x)^2/2\sigma_y^2}\, dx \overset{\text{（代数整理）}}{=} c\, e^{-\gamma w^2}.
```
- **结论**：$W$ 是 normal（正态）的：
  - mean（均值）$= 0$，variance（方差）$= \sigma_x^2 + \sigma_y^2$；
  - 均值非零的情形用同样的论证处理。

> <span style="color:#7f8c8d;">Bertsekas §4.1, p.217–218</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 被卷积代数吞掉的细节补全：把指数展开 $-\frac{x^2}{2\sigma_x^2} - \frac{(w - x)^2}{2\sigma_y^2}$，按 $x$ 配方后剩余项恰为 $-\frac{w^2}{2(\sigma_x^2 + \sigma_y^2)}$，即 $\gamma = \frac{1}{2(\sigma_x^2 + \sigma_y^2)}$——被积函数是 $e^{-\gamma w^2}$ 乘一个 $x$ 的高斯核，对 $x$ 积分只贡献常数 $c$。形状已是正态，常数由归一化自动定为 $c = 1/\sqrt{2\pi(\sigma_x^2 + \sigma_y^2)}$，无需硬算 ✓。交叉验证方差：零均值时 $\mathrm{var}(W) = \sigma_x^2 + \sigma_y^2$，恰是 Lec 07 方差和规则给出的值——卷积与方差两条独立推导互相咬合 ✓。均值非零时，把 $W$ 写成"零均值部分 $+ (\mu_x + \mu_y)$"，再用上讲 $Y = aX + b$ 的平移结论即可 ✓。跨课程连接：配方在 Strang 线代里是"二次型相加仍是二次型"的一维情形——正定型对加法封闭，正是正态族卷积封闭性的线代影子；这层封闭性让正态族成为后续讲义反复调用的高斯工具箱。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Covariance（协方差）</span>

- 定义：$\mathrm{cov}(X, Y) = \mathrm{E}\big[(X - \mathrm{E}[X]) \cdot (Y - \mathrm{E}[Y])\big]$。
- 零均值情形：$\mathrm{cov}(X, Y) = \mathrm{E}[XY]$。

> <span style="color:#7f8c8d;">图：两张散点图——左图点云沿正向倾斜（正协方差：两个中心化变量同进退），右图点云沿负向倾斜（负协方差：一升一降）。</span>

- 展开式：$\mathrm{cov}(X, Y) = \mathrm{E}[XY] - \mathrm{E}[X]\,\mathrm{E}[Y]$。
- 多变量方差公式：
```math
\mathrm{var}\!\left( \sum_{i=1}^{n} X_i \right) = \sum_{i=1}^{n} \mathrm{var}(X_i) + 2 \sum_{(i,j):\, i<j} \mathrm{cov}(X_i, X_j).
```
- 独立 $\Rightarrow \mathrm{cov}(X, Y) = 0$（converse is not true，逆命题不真）。

> <span style="color:#7f8c8d;">Bertsekas §4.2, p.221–222</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> "独立 $\Rightarrow$ 不相关"一行证完：$\mathrm{E}[XY] = \mathrm{E}[X]\mathrm{E}[Y]$（Lec 07 已证），代入 $\mathrm{cov}(X,Y) = \mathrm{E}[XY] - \mathrm{E}[X]\mathrm{E}[Y] = 0$ ✓。逆命题不真——反例（译者补）：$X \sim U[-1, 1]$，$Y = X^2$。$\mathrm{E}[X] = 0$ 且 $\mathrm{E}[XY] = \mathrm{E}[X^3] = 0$，故 $\mathrm{cov}(X, Y) = 0$；但 $Y$ 由 $X$ 完全决定，相依到极致 ✓。含义：协方差只捕捉"线性同向/反向"的关联，对二次曲线型的关联视而不见。多变量方差公式是 Lec 07 两个幽灵陷阱的解剖图：$X = Y$ 时 $\mathrm{cov}(X, Y) = \mathrm{var}(X)$，和的方差翻 4 倍；$X = -Y$ 时 $\mathrm{cov} = -\mathrm{var}(X)$，完全对消；独立时全部交叉项消失。中心化乘积 $(X - \mathrm{E}[X])(Y - \mathrm{E}[Y])$ 的符号语义：两家同时高于/低于各自的平均为正，一高一低为负——散点图的倾斜方向由此而来。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Correlation coefficient（相关系数）</span>

- 协方差的无量纲（dimensionless）版本：
```math
\rho = \mathrm{E}\!\left[ \frac{X - \mathrm{E}[X]}{\sigma_X} \cdot \frac{Y - \mathrm{E}[Y]}{\sigma_Y} \right] = \frac{\mathrm{cov}(X, Y)}{\sigma_X\, \sigma_Y}.
```
- $-1 \le \rho \le 1$。
- $|\rho| = 1 \iff (X - \mathrm{E}[X]) = c\, (Y - \mathrm{E}[Y])$（linearly related，线性相关）。
- 独立 $\Rightarrow \rho = 0$（逆命题不真）。

> <span style="color:#7f8c8d;">Bertsekas §4.2, p.221–222</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 界的验算：对任意实数 $t$，$0 \le \mathrm{var}\big(\frac{X}{\sigma_X} + t\, \frac{Y}{\sigma_Y}\big)$，展开得 $0 \le 1 + t^2 + 2 t \rho$；取 $t = \pm 1$ 得 $0 \le 2 \pm 2\rho$，即 $-1 \le \rho \le 1$ ✓。端点语义：取等时该线性组合方差为 0，即退化为常数，故 $|\rho| = 1 \iff$ 标准化后的 $X, Y$ 严格线性相关 ✓。无量纲化的意义：$\mathrm{cov}$ 带着两个变量的量纲（米 × 秒），数值大小不可跨问题比较；$\rho$ 先把两变量各自标准化（除以 $\sigma$）再取期望，成为纯粹形状指标。跨课程连接：用 Strang 线代语言，在中心化随机变量空间上定义内积 $\langle X, Y \rangle = \mathrm{E}[XY]$，则 $\rho$ 恰是 cosine（余弦）相似度 $\cos\theta$，$-1 \le \rho \le 1$ 就是 Cauchy–Schwarz 不等式的概率化身；"独立 $\Rightarrow \rho = 0$ 而逆不真"对应"内积为零（正交）但非线性无关"。上一节的反例 $Y = X^2$ 在此依然成立：完全相依却 $\rho = 0$。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
