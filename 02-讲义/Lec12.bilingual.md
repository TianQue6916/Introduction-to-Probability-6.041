# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 12 — Conditional expectation; variance; sum of a random number of independent r.v.s（条件期望；方差；随机个独立随机变量之和）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline（本讲大纲）</span>

**阅读（Readings）**：教材 Section 4.3；Section 4.5 的部分内容（只要均值与方差；不讲变换）。

**本讲大纲（Lecture outline）**：
- 条件期望（Conditional expectation）：
  - 迭代期望律（law of iterated expectations）。
  - 全方差律（law of total variance）。
- 随机个独立随机变量之和（sum of a random number of independent r.v.'s）：
  - 均值、方差。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.222–228；§4.5, p.240–243</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> Lec 07 的期望运算规则在此升级：不再只问"固定项数之和的期望"，而问"连项数 $N$ 都是随机的和怎么办"——答案是把"先条件化、再平均"练成条件反射。本讲两大件：其一，条件期望 $\mathrm{E}[X \mid Y]$ 的双重身份（既是数又是随机变量），由此导出迭代期望律与全方差律；其二，把这套机器用在 $Y = X_1 + \cdots + X_N$ 上，得 $\mathrm{E}[Y] = \mathrm{E}[N]\mathrm{E}[X]$ 与 $\mathrm{var}(Y) = \mathrm{E}[N]\mathrm{var}(X) + (\mathrm{E}[X])^2 \mathrm{var}(N)$。经核对页码，§4.3 Conditional Expectation and Variance Revisited（p.222 起，全方差律在 p.227 附近）与 §4.5 Sum of a Random Number of Independent Random Variables（p.240–243）是阅读范围；Readings 特别注明"只取均值与方差，不碰变换"——§4.4 Transforms（p.229 起）整节跳过。断棍例与分班例是两台演示机：前者小而通透，后者全是可验算的数字。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditional expectations（条件期望）</span>

- 给定随机变量 $Y$ 的取值 $y$：
```math
\mathrm{E}[X \mid Y = y] = \sum_x x\, p_{X|Y}(x \mid y) \qquad \text{（连续情形换成积分）}.
```
- **Stick example（断棍例）**：长为 $\ell$ 的棍子，在均匀选取的点 $Y$ 处折断；再在均匀选取的点 $X$ 处折断。
- $\mathrm{E}[X \mid Y = y] = \dfrac{y}{2}$ ——一个 number（数）。
- $\mathrm{E}[X \mid Y] = \dfrac{Y}{2}$ ——一个 random variable（随机变量）。
- **迭代期望律（law of iterated expectations）**：
```math
\mathrm{E}\big[\mathrm{E}[X \mid Y]\big] = \sum_y \mathrm{E}[X \mid Y = y]\, p_Y(y) = \mathrm{E}[X].
```
- 断棍例中：$\mathrm{E}[X] = \mathrm{E}\big[\mathrm{E}[X \mid Y]\big] = \mathrm{E}[Y/2] = \ell/4$。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.222–224</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 双重身份是本讲的枢纽：$\mathrm{E}[X \mid Y = y]$ 是按条件分布列加权的平均，一个数；把 $y$ 换成随机的 $Y$，$\mathrm{E}[X \mid Y] = Y/2$（断棍例）就成了随机变量——它是 $Y$ 的函数。迭代期望律说的是"先按 $Y$ 分层求平均，再按 $Y$ 的分布把各层平均加权回来"，两层平均还原总体平均。断棍例的第一性验算：棍长 $\ell$，第一折点 $Y \sim U[0, \ell]$；给定 $Y = y$，第二折点在长 $y$ 的剩余段上均匀，$X \mid Y = y \sim U[0, y]$，条件均值 $y/2$ ✓；再对 $Y$ 平均：$\mathrm{E}[Y/2] = \ell/4$ ✓——每一段的期望长度都是对半分，直觉吻合。卡点：写成 $\mathrm{E}[X \mid Y]$ 时它随 $Y$ 抽签取值，这正是它能被再次取期望、能进方差公式的原因；把"数"与"随机变量"混为一谈是初学最大的坑。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">var(X | Y) and its expectation（条件方差及其期望）</span>

- $\mathrm{var}(X \mid Y = y) = \mathrm{E}\big[(X - \mathrm{E}[X \mid Y = y])^2 \mid Y = y\big]$。
- $\mathrm{var}(X \mid Y)$：一个随机变量——当 $Y = y$ 时取值 $\mathrm{var}(X \mid Y = y)$。
- **全方差律（law of total variance）**：
```math
\mathrm{var}(X) = \mathrm{E}\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(\mathrm{E}[X \mid Y]\big).
```
- **证明（Proof）**：
  - (a) 回顾：$\mathrm{var}(X) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2$；
  - (b) $\mathrm{var}(X \mid Y) = \mathrm{E}[X^2 \mid Y] - (\mathrm{E}[X \mid Y])^2$；
  - (c) $\mathrm{E}\big[\mathrm{var}(X \mid Y)\big] = \mathrm{E}[X^2] - \mathrm{E}\big[(\mathrm{E}[X \mid Y])^2\big]$；
  - (d) $\mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \mathrm{E}\big[(\mathrm{E}[X \mid Y])^2\big] - (\mathrm{E}[X])^2$；
  - (c)、(d) 右端相加：$\mathrm{E}[X^2] - (\mathrm{E}[X])^2 = \mathrm{var}(X)$。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.225–227</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 四步证明逐条核对：(a) 矩公式 $\mathrm{var}(X) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2$，Lec 07 已见 ✓；(b) 把 (a) 用在"给定 $Y = y$"的条件世界上——条件方差是围绕条件均值的二阶矩 ✓；(c) 对 (b) 两边取期望：$\mathrm{E}[\mathrm{var}(X \mid Y)] = \mathrm{E}[\mathrm{E}[X^2 \mid Y]] - \mathrm{E}[(\mathrm{E}[X \mid Y])^2] = \mathrm{E}[X^2] - \mathrm{E}[(\mathrm{E}[X \mid Y])^2]$，中间用了迭代期望律对函数 $X^2$ 同样成立 ✓；(d) 把 (a) 用在随机变量 $Z = \mathrm{E}[X \mid Y]$ 自身上：$\mathrm{var}(Z) = \mathrm{E}[Z^2] - (\mathrm{E}[Z])^2$ ✓。(c) $+$ (d) 相加时，交叉项 $\mathrm{E}[(\mathrm{E}[X \mid Y])^2]$ 精确对消，余下 $\mathrm{E}[X^2] - (\mathrm{E}[X])^2 = \mathrm{var}(X)$。全方差律的结构一目了然：总方差 = 围绕条件均值的摆动（组内波动）$+$ 条件均值自身的摆动（组间波动）。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Section means and variances（分班示例：均值）</span>

两个班：$y = 1$（10 名学生）；$y = 2$（20 名学生）。

- $y = 1$：$\dfrac{1}{10} \displaystyle\sum_{i=1}^{10} x_i = 90$；$\quad y = 2$：$\dfrac{1}{20} \displaystyle\sum_{i=11}^{30} x_i = 60$。
- 总平均：
```math
\mathrm{E}[X] = \frac{1}{30} \sum_{i=1}^{30} x_i = \frac{90 \cdot 10 + 60 \cdot 20}{30} = 70 .
```
- $\mathrm{E}[X \mid Y = 1] = 90$，$\quad \mathrm{E}[X \mid Y = 2] = 60$；
```math
\mathrm{E}[X \mid Y] = \begin{cases} 90, & \text{w.p.（以概率） } 1/3, \\ 60, & \text{w.p. } 2/3; \end{cases}
```
```math
\mathrm{E}\big[\mathrm{E}[X \mid Y]\big] = \frac{1}{3} \cdot 90 + \frac{2}{3} \cdot 60 = 70 = \mathrm{E}[X],
```
```math
\mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \frac{1}{3} (90 - 70)^2 + \frac{2}{3} (60 - 70)^2 = \frac{600}{3} = 200 .
```

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.223–227</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Section means and variances (ctd.)（分班示例（续）：方差）</span>

- $y = 1$：$\dfrac{1}{10} \displaystyle\sum_{i=1}^{10} (x_i - 90)^2 = 10$；$\quad y = 2$：$\dfrac{1}{20} \displaystyle\sum_{i=11}^{30} (x_i - 60)^2 = 20$。
- $\mathrm{var}(X \mid Y = 1) = 10$，$\quad \mathrm{var}(X \mid Y = 2) = 20$；
```math
\mathrm{var}(X \mid Y) = \begin{cases} 10, & \text{w.p. } 1/3, \\ 20, & \text{w.p. } 2/3; \end{cases} \qquad \mathrm{E}\big[\mathrm{var}(X \mid Y)\big] = \frac{1}{3} \cdot 10 + \frac{2}{3} \cdot 20 = \frac{50}{3}.
```
- 全方差律合龙：
```math
\mathrm{var}(X) = \mathrm{E}\big[\mathrm{var}(X \mid Y)\big] + \mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \frac{50}{3} + 200 ,
```
  即（各班内部的平均波动）$+$（班与班之间的波动）。

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.227</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Example（例：把公式用起来）</span>

$\mathrm{var}(X) = \mathrm{E}[\mathrm{var}(X \mid Y)] + \mathrm{var}(\mathrm{E}[X \mid Y])$

> <span style="color:#7f8c8d;">图：$f_X(x)$ 按 $Y = 1$、$Y = 2$ 两个班分层标出的示意——两班的混合权重分别为 $1/3$ 与 $2/3$（与 30 人分班一致）。</span>

**课堂填空**：
- $\mathrm{E}[X \mid Y = 1] = \underline{\qquad}$，$\quad \mathrm{E}[X \mid Y = 2] = \underline{\qquad}$
- $\mathrm{var}(X \mid Y = 1) = \underline{\qquad}$，$\quad \mathrm{var}(X \mid Y = 2) = \underline{\qquad}$
- $\mathrm{E}[X] = \underline{\qquad}$
- $\mathrm{var}\big(\mathrm{E}[X \mid Y]\big) = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §4.3, p.223–227</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 六个空栏逐一验算（沿用分班数据）：$\mathrm{E}[X \mid Y = 1] = 90$、$\mathrm{E}[X \mid Y = 2] = 60$ ✓（题面给的班均值）；$\mathrm{var}(X \mid Y = 1) = 10$、$\mathrm{var}(X \mid Y = 2) = 20$ ✓（题面给的班内方差）。$\mathrm{E}[X] = \mathrm{E}[\mathrm{E}[X \mid Y]] = \frac{1}{3} \cdot 90 + \frac{2}{3} \cdot 60 = 30 + 40 = 70$ ✓。$\mathrm{var}(\mathrm{E}[X \mid Y])$：随机变量 $\mathrm{E}[X \mid Y]$ 以 1/3 概率取 90、2/3 概率取 60，均值 70，故 $\frac{1}{3}(90 - 70)^2 + \frac{2}{3}(60 - 70)^2 = \frac{400}{3} + \frac{200}{3} = \frac{600}{3} = 200$ ✓。补全拼图：$\mathrm{E}[\mathrm{var}(X \mid Y)] = \frac{1}{3} \cdot 10 + \frac{2}{3} \cdot 20 = \frac{50}{3}$，全方差律给 $\mathrm{var}(X) = \frac{50}{3} + 200 = \frac{650}{3} \approx 216.7$——组内波动贡献不足一成，组间波动（均值 90 对 60）才是方差主力，这正是全方差律想讲的故事。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Sum of a random number of independent r.v.s（随机个独立随机变量之和）</span>

- $N$：光顾的商店家数（nonnegative integer r.v.，非负整数值随机变量）。
- $X_i$：在第 $i$ 家店花的钱数：
  - 假定 $X_i$ 为 i.i.d.（independent and identically distributed，独立同分布）；
  - 且与 $N$ 独立。
- 令 $Y = X_1 + \cdots + X_N$：
```math
\begin{aligned}
\mathrm{E}[Y \mid N = n] &= \mathrm{E}[X_1 + X_2 + \cdots + X_n \mid N = n] \\
&= \mathrm{E}[X_1 + X_2 + \cdots + X_n] \\
&= \mathrm{E}[X_1] + \mathrm{E}[X_2] + \cdots + \mathrm{E}[X_n] \\
&= n\, \mathrm{E}[X];
\end{aligned}
```
  （中间一步：$X_1, \ldots, X_n$ 与事件 $\{N = n\}$ 独立）
- 于是 $\mathrm{E}[Y \mid N] = N\, \mathrm{E}[X]$，且
```math
\mathrm{E}[Y] = \mathrm{E}\big[\mathrm{E}[Y \mid N]\big] = \mathrm{E}\big[N\, \mathrm{E}[X]\big] = \mathrm{E}[N]\, \mathrm{E}[X].
```

> <span style="color:#7f8c8d;">Bertsekas §4.5, p.240–241</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 验证）:**</span> 命名模板——freeze-N（冻结 $N$）：把随机项数先钉在具体值 $n$ 上再推理。链式等式逐步验：第一步是条件期望的定义式写法 ✓；第二步去掉条件——题设明说各 $X_i$ 与 $N$ 独立，事件 $\{N = n\}$ 不携带任何关于 $X_i$ 的信息，条件期望坍缩为无条件期望 ✓；第三步是期望的线性（Lec 07：不要求独立）✓；第四步用 i.i.d. 同均值合并为 $n\, \mathrm{E}[X]$ ✓。最后对 $N$ 取期望：$\mathrm{E}[\mathrm{E}[Y \mid N]] = \mathrm{E}[N \mathrm{E}[X]] = \mathrm{E}[N]\mathrm{E}[X]$，外层又是一次期望线性。退化检验：$N \equiv n$（方差为零的随机变量）时公式给 $\mathrm{E}[Y] = n\, \mathrm{E}[X]$，与固定项数的情形一致 ✓。卡点诊断：若"逛的店越多、单店花得越少"（$X_i$ 与 $N$ 相依），第二步立即塌方——假设清单不是装饰品。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Variance of sum of a random number of independent r.v.s（随机个独立随机变量之和的方差）</span>

- 从全方差律出发：$\mathrm{var}(Y) = \mathrm{E}[\mathrm{var}(Y \mid N)] + \mathrm{var}(\mathrm{E}[Y \mid N])$。
- 第二项：$\mathrm{E}[Y \mid N] = N\, \mathrm{E}[X]$，故 $\mathrm{var}\big(\mathrm{E}[Y \mid N]\big) = (\mathrm{E}[X])^2\, \mathrm{var}(N)$。
- 第一项：$\mathrm{var}(Y \mid N = n) = n\, \mathrm{var}(X)$，即 $\mathrm{var}(Y \mid N) = N\, \mathrm{var}(X)$，故 $\mathrm{E}\big[\mathrm{var}(Y \mid N)\big] = \mathrm{E}[N]\, \mathrm{var}(X)$。
- 合并：
```math
\mathrm{var}(Y) = \mathrm{E}\big[\mathrm{var}(Y \mid N)\big] + \mathrm{var}\big(\mathrm{E}[Y \mid N]\big) = \mathrm{E}[N]\, \mathrm{var}(X) + (\mathrm{E}[X])^2\, \mathrm{var}(N).
```

> <span style="color:#7f8c8d;">Bertsekas §4.5, p.240–243</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 公式的两个零件各有出处：内层 $\mathrm{var}(Y \mid N = n) = n\, \mathrm{var}(X)$——固定 $N = n$ 后是 $n$ 个 i.i.d. 之和，用 Lec 07 的方差和规则（独立才可加）✓；外层 $\mathrm{var}(N\, \mathrm{E}[X]) = (\mathrm{E}[X])^2 \mathrm{var}(N)$——缩放规则 $\mathrm{var}(aX) = a^2 \mathrm{var}(X)$ ✓；拼装靠本讲全方差律。退化检验两连：$N \equiv n$ 给 $\mathrm{var}(Y) = n\, \mathrm{var}(X)$ ✓；$\mathrm{E}[X] = 0$ 时第二项蒸发，$\mathrm{var}(Y) = \mathrm{E}[N]\, \mathrm{var}(X)$——每笔收支均值为零、笔数随机，总波动只由"平均笔数 × 单笔方差"决定 ✓。卡点：第二项系数为何是 $(\mathrm{E}[X])^2$ 而非 $\mathrm{E}[X^2]$？全方差律的第二项只统计"条件均值绕总均值的摆动"，单笔围绕自身均值的摆动已折进第一项，两者不重复计费。跨课程连接：CLRS 分析随机化算法（如随机 pivot 的快排）时"先固定随机选择、再对分布求平均"的两层期望与全方差思想同源；6.042J 的期望线性练习也是同款肌肉训练。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
