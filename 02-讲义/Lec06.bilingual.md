# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 6 — Discrete Random Variable Examples; Joint PMFs（离散随机变量例题与联合分布列）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; review（本讲大纲与复习）</span>

**阅读（Readings）**：教材 Sections 2.4–2.6。

**本讲大纲（Lecture outline）**：
- 复习：PMF（分布列）、expectation（期望）、variance（方差）。
- Conditional PMF（条件分布列）。
- Geometric PMF（几何分布列）。
- Total expectation theorem（全期望定理）。
- 两个随机变量的 joint PMF（联合分布列）。

**复习（Review）**：
- 随机变量 $X$：从样本空间到实数集的函数。
- PMF（离散随机变量）：$p_X(x) = P(X = x)$。
- 期望：
```math
\mathrm{E}[X] = \sum_x x \, p_X(x), \qquad \mathrm{E}[g(X)] = \sum_x g(x) \, p_X(x), \qquad \mathrm{E}[\alpha X + \beta] = \alpha\, \mathrm{E}[X] + \beta .
```
```math
\mathrm{E}\left[X - \mathrm{E}[X]\right] = 0, \qquad \mathrm{var}(X) = \mathrm{E}\left[(X - \mathrm{E}[X])^2\right] = \sum_x (x - \mathrm{E}[X])^2 p_X(x) = \mathrm{E}[X^2] - (\mathrm{E}[X])^2 .
```
- Standard deviation（标准差）：$\sigma_X = \sqrt{\mathrm{var}(X)}$。

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.87（线性函数规则与矩公式）；§2.4–2.6（本讲 Readings）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 战略定位）:**</span> 复习页里唯一"新面孔"是恒等式 $\mathrm{E}[X - \mathrm{E}[X]] = 0$：由期望的线性 $\mathrm{E}[X - \mathrm{E}[X]] = \mathrm{E}[X] - \mathrm{E}[\mathrm{E}[X]] = \mathrm{E}[X] - \mathrm{E}[X] = 0$ ✓——常数可以从期望里自由进出，居中之后的变量期望必为零。这个看似平凡的式子是方差的根：$\mathrm{var}(X)$ 正是"居中变量取平方的期望"。战略定位：本讲的任务是把 Lec 05 的三件套（PMF、期望、方差）逐一升级——先学会在 partial information（部分信息）下使用它们（条件分布列与条件期望），再用全期望定理把"分块计算"合法化，最后引入第二个随机变量（联合分布列），为 Lec 07 的多维世界铺路。标准差 $\sigma_X = \sqrt{\mathrm{var}(X)}$ 的意义在量纲：方差单位是 $X$ 单位的平方，开根号后才能与 $X$ 本身同台比较。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Random speed（随机车速）</span>

- 以恒定但 random（随机）的速度 $V$ 行驶 200 英里路程。
```math
p_V(v) = \begin{cases} 1/2, & v = 1, \\ 1/2, & v = 200 . \end{cases}
```
- $d = 200$，$T = t(V) = 200/V$。
- **课堂填空**：
  - $\mathrm{E}[V] = \underline{\qquad}$
  - $\mathrm{var}(V) = \underline{\qquad}$
  - $\sigma_V = \underline{\qquad}$

> <span style="color:#7f8c8d;">图：两点分布列——$v = 1$ 与 $v = 200$ 处各有高度 $1/2$ 的竖条。</span>

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.87–88（矩公式与同型例）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 逐项验算。$\mathrm{E}[V] = 1 \cdot \tfrac{1}{2} + 200 \cdot \tfrac{1}{2} = 100.5$ ✓。二阶矩 $\mathrm{E}[V^2] = 1^2 \cdot \tfrac{1}{2} + 200^2 \cdot \tfrac{1}{2} = \tfrac{1 + 40000}{2} = 20000.5$，故 $\mathrm{var}(V) = 20000.5 - (100.5)^2 = 20000.5 - 10100.25 = 9900.25$ ✓，恰是 $99.5^2$，所以 $\sigma_V = 99.5$ ✓（精确值，无需近似）。两个值得咂摸的细节：其一，$\mathrm{E}[V] = 100.5$ 这个"平均速度"在本例的两种车速里根本不会出现——期望不必是可能的取值，它是分布的重心而非众数；其二，$\sigma_V \approx \mathrm{E}[V]$：摆动幅度与均值同量级，说明这个分布的相对离散度极大，这正是下一页"平均时间的陷阱"的温床。本例结构上就是教材 p.87 线性函数规则的舞台：知道 $p_V$ 后，任何 $g(V)$ 的期望都可以用期望值规则 $\mathrm{E}[g(V)] = \sum_v g(v)\, p_V(v)$ 直接写出。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Average speed vs. average time（平均速度对平均时间）</span>

- 同一设定：恒定但随机的速度 $V$ 行驶 200 英里，时间（小时）为 $T = t(V) = 200/V$。
- **课堂填空**：
```math
\mathrm{E}[T] = \mathrm{E}[t(V)] = \sum_v t(v) \, p_V(v) = \underline{\qquad} \quad (\text{小时}) .
```
- $\mathrm{E}[T V] = 200 \ne \mathrm{E}[T] \cdot \mathrm{E}[V]$。
- $\mathrm{E}[200/V] = \mathrm{E}[T] \ne 200 / \mathrm{E}[V]$。

> <span style="color:#7f8c8d;">Bertsekas §2.4, p.88（Example 2.4: Average Speed Versus Average Time）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验算填空：$t(1) = 200$ 小时、$t(200) = 1$ 小时，$\mathrm{E}[T] = 200 \cdot \tfrac{1}{2} + 1 \cdot \tfrac{1}{2} = 100.5$ 小时 ✓。于是三条不等式逐一落实：$\mathrm{E}[TV] = \mathrm{E}[200] = 200$，而 $\mathrm{E}[T]\,\mathrm{E}[V] = 100.5^2 = 10100.25$，确实不等 ✓；$200/\mathrm{E}[V] = 200/100.5 \approx 1.99$ 小时，与真实的 $\mathrm{E}[T] = 100.5$ 小时相差五十余倍 ✓。卡点诊断：为什么差距如此悬殊？因为"先平均速度再取倒数"完全抹掉了**慢速场景的主导地位**——$V = 1$ 的那次行程耗掉 200 小时，把期望时间整个拉走；倒数是非线性函数，对小值极端敏感。教材 Example 2.4（p.88）的 Alice 例同型：她以 5 mph 步行或 30 mph 骑摩托，$\mathrm{E}[V] = 15$ mph，但 $\mathrm{E}[T] = 0.6 \cdot \tfrac{2}{5} + 0.4 \cdot \tfrac{2}{30} \approx 0.267$ 小时，而 $2/\mathrm{E}[V] = 2/15 \approx 0.133$ 小时——恰差一倍 ✓。口诀：**时间平均要走时间的路，别搭速度的便车**；这正是 Lec 05 警告 $\mathrm{E}[g(X)] \ne g(\mathrm{E}[X])$ 的头号案例。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditional PMF and expectation（条件分布列与条件期望）</span>

- $p_{X|A}(x) = P(X = x \mid A)$。
```math
\mathrm{E}[X \mid A] = \sum_x x \, p_{X|A}(x) .
```
- **例**：$p_X(x)$ 在 $x = 1, 2, 3, 4$ 上均匀（各 $1/4$）。

> <span style="color:#7f8c8d;">图：四根等高竖条（高度 $1/4$，位于 $x = 1, 2, 3, 4$）——条件化后重画为 $x = 2, 3, 4$ 上的三根等高竖条（高度 $1/3$）。</span>

- 令 $A = \{X \ge 2\}$。
- **课堂填空**：
  - $p_{X|A}(x) = \underline{\qquad}$
  - $\mathrm{E}[X \mid A] = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §2.6, p.97–98（条件分布列定义；Example 2.12 的骰子取偶数例同型）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 第一性原理）:**</span> 验算填空：$P(A) = P(X \ge 2) = 3/4$；对 $x = 2, 3, 4$，$p_{X|A}(x) = \dfrac{P(X = x)}{P(A)} = \dfrac{1/4}{3/4} = \dfrac{1}{3}$，对其他 $x$ 为 $0$ ✓；$\mathrm{E}[X \mid A] = \dfrac{2 + 3 + 4}{3} = 3$ ✓。第一性原理：条件化 = **截断 + 归一化**——先把 $A$ 之外的分布列值清零，再把剩下的质量除以 $P(A)$ 凑回 1；新的 $p_{X|A}$ 是合法分布列，因为 $\{X = x\} \cap A$ 对不同 $x$ 互不相交且并为 $A$（教材 p.98 正是这样验证归一性的）。它与 Lec 02 的条件概率定义完全同构，只是把"事件"换成了"随机变量的取值"。这个例子里条件分布仍是均匀的——条件化保留形状、只重缩放（教材 p.98 的 Example 2.12：骰子掷出偶数的条件下各偶数点概率 $1/3$，一模一样）；下一页的几何分布将展示形状平移的版本。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Geometric PMF（几何分布列）</span>

- $X$：独立掷硬币直到首次出现正面所需的次数。
```math
p_X(k) = (1-p)^{k-1} p, \qquad k = 1, 2, \ldots
```
```math
\mathrm{E}[X] = \sum_{k=1}^{\infty} k \, p_X(k) = \sum_{k=1}^{\infty} k (1-p)^{k-1} p .
```
- **Memoryless property（无记忆性）**：已知 $X > 2$，随机变量 $X - 2$ 仍服从同一个几何分布列。

> <span style="color:#7f8c8d;">图：三幅并排的分布列条形图——$p_X(k)$（从 $k=1$ 起公比 $1-p$ 递减）、$p_{X|X>2}(k)$（前两根清零、其余按 $P(X>2) = (1-p)^2$ 重缩放，图中可见 $p(1-p)^2$）、$p_{X-2|X>2}(k)$（整体左移两格后与 $p_X$ 同形同高）。</span>

> <span style="color:#7f8c8d;">Bertsekas §2.6, p.105–106（Example 2.17：用全期望定理求几何分布的均值与方差）；§3.2, p.151–152（几何 CDF 与指数 CDF 的联系）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 无记忆性的验算：对 $m = 1, 2, \ldots$，$P(X - 2 = m \mid X > 2) = \dfrac{P(X = m + 2)}{P(X > 2)} = \dfrac{(1-p)^{m+1} p}{(1-p)^2} = (1-p)^{m-1} p$ ✓——与 $p_X(m)$ 完全相同，几何分布"忘掉"了已经烧掉的两次等待。卡点诊断：无记忆性的根源是**独立性**——硬币没有记忆，前两次全反面（概率 $(1-p)^2$）与后续试验无关，条件化只是把起点重新标定；任何"每步成功概率恒为 $p$ 且各步独立"的过程都自带这一性质。至于 $\mathrm{E}[X] = \sum_k k(1-p)^{k-1} p$，直接求和需要等比数列求导技巧；幻灯片故意把它挂起，下一页用全期望定理三行解决——"先挂账、再巧还"是本讲的教学节奏。教材 §3.2（p.151–152）还给出几何 CDF $1 - (1-p)^n$ 与指数 CDF $1 - e^{-\lambda n}$ 的对照：二者是同一"无记忆家族"的离散与连续成员。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Total expectation theorem（全期望定理）</span>

- 把样本空间 partition（分割）为互不相交的事件 $A_1, A_2, \ldots, A_n$：

> <span style="color:#7f8c8d;">图：样本空间被剖分为区域 $A_1, A_2, A_3$（可延伸至 $A_n$），事件 $B$ 横跨各区域、被切成 $B \cap A_i$ 若干块。</span>

```math
P(B) = P(A_1) P(B \mid A_1) + \cdots + P(A_n) P(B \mid A_n),
```
```math
p_X(x) = P(A_1)\, p_{X|A_1}(x) + \cdots + P(A_n)\, p_{X|A_n}(x),
```
```math
\mathrm{E}[X] = P(A_1)\, \mathrm{E}[X \mid A_1] + \cdots + P(A_n)\, \mathrm{E}[X \mid A_n] .
```
- **几何分布例**：$A_1 = \{X = 1\}$，$A_2 = \{X > 1\}$。
```math
\mathrm{E}[X] = P(X = 1)\, \mathrm{E}[X \mid X = 1] + P(X > 1)\, \mathrm{E}[X \mid X > 1] .
```
- 解方程得 $\mathrm{E}[X] = 1/p$。

> <span style="color:#7f8c8d;">Bertsekas §2.6, p.104（total expectation theorem 的三种形式）；p.105–106（Example 2.16 与 Example 2.17）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板 + 跨课程连接）:**</span> 命名模板：**首次成功分解法**（重启动论证）。把"第一次就成功"与"第一次失败后从头再来"两种情形拆开：$\mathrm{E}[X \mid X = 1] = 1$；若首次失败则白烧一次、过程从零重启，故 $\mathrm{E}[X \mid X > 1] = 1 + \mathrm{E}[X]$。代入全期望定理：$\mathrm{E}[X] = p \cdot 1 + (1-p)(1 + \mathrm{E}[X])$，移项解出 $\mathrm{E}[X] = 1/p$ ✓——这正是教材 Example 2.17（p.105–106）的推导，避开无穷级数，一行代数定乾坤。为什么合法？教材 p.104–105 的验证是：对 $p_X(x) = \sum_i P(A_i) p_{X|A_i}(x)$ 两边乘 $x$ 再对 $x$ 求和，交换次序即得——全期望定理本质是全概率定理（Lec 02）乘上 $x$。跨课程连接：这种"用期望自身表示期望、解自相似方程"的手法，与 CLRS 随机化算法分析中"对随机决策取条件、层层递归求期望"的手法同构（典型如随机化 quicksort 对 pivot 位置的期望分析），你在 6.042J 解 recurrence（递推方程）时的手感可直接迁移——只是这里的"递推"作用在期望值上。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Joint PMFs（联合分布列）</span>

- $p_{X,Y}(x, y) = P(X = x \text{ and } Y = y)$。本页沿用如下联合分布列表格：

| $y \backslash x$ | $1$ | $2$ | $3$ | $4$ |
|:---:|:---:|:---:|:---:|:---:|
| $4$ | $1/20$ | $2/20$ | $2/20$ | |
| $3$ | $2/20$ | $4/20$ | $1/20$ | $2/20$ |
| $2$ | | $1/20$ | $3/20$ | $1/20$ |
| $1$ | | $1/20$ | | |

- $\sum_x \sum_y p_{X,Y}(x, y) = 1$。
- 边缘化：$p_X(x) = \sum_y p_{X,Y}(x, y)$。
- 条件分布列：
```math
p_{X|Y}(x \mid y) = P(X = x \mid Y = y) = \frac{p_{X,Y}(x, y)}{p_Y(y)}, \qquad \sum_x p_{X|Y}(x \mid y) = 1 .
```

> <span style="color:#7f8c8d;">Bertsekas §2.5, p.92–95（联合分布列的定义、tabular method 与期望值规则；Example 2.9 即本页表格，$p_X(2) = 7/20$）；§2.6, p.101（乘法公式 $p_{X,Y} = p_Y \cdot p_{X|Y}$）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 第一性原理）:**</span> 验算：10 个非零格相加 $\sum p_{X,Y} = 20/20 = 1$ ✓；按列求和得边缘分布列，例如 $p_X(2) = \tfrac{1+4+1+1}{20} = \tfrac{7}{20}$ ✓——这正是教材 Example 2.9（p.93–94）的 tabular method：对固定 $x$ 把所在列的数竖着加一遍。第一性原理：**联合 → 边缘 → 条件**是同一张二维表格的三种读法。联合是全部概率质量的存放处；边缘是"把另一维积分掉"——对固定 $x$ 沿 $y$ 方向求列和；条件 $p_{X|Y}(\cdot \mid y)$ 是"把第 $y$ 行切下来、除以行和 $p_Y(y)$ 归一化"——每一行都是一个合法的一维分布列。乘法公式 $p_{X,Y}(x,y) = p_Y(y)\, p_{X|Y}(x \mid y)$（教材 p.101）则把方向反过来：先用边缘定行、再用条件分布填行内形状。这张表会在 Lec 07 以完全相同的面孔再次登场，用于条件独立性实验（教材 Fig. 2.15, p.111）——本页先把它读熟，下一讲直接开算。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
