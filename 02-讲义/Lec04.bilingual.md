# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 4 — Counting（计数）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Discrete uniform law（离散均匀律）</span>

**阅读**：教材 Section 1.6。

**本讲大纲（Lecture outline）**：
- 计数原理（Principles of counting）。
- 大量例子：
  - 排列（permutations）。
  - $k$-排列（k-permutations）。
  - 组合（combinations）。
  - 划分（partitions）。
- 二项概率（Binomial probabilities）。

**离散均匀律**：设所有样本点 equally likely（等可能），则
```math
P(A) = \frac{\text{属于 } A \text{ 的样本点个数}}{\text{样本点总数}} = \frac{|A|}{|\Omega|} .
```
- **只需要数数**（Just count…）。

> <span style="color:#7f8c8d;">Bertsekas §1.2, p.11；§1.6, p.44</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 这一页把上一讲收尾的承诺兑现了：**在等可能模型下，概率计算完全约化为计数**——$P(A) = |A|/|\Omega|$，分子分母都是"数个数"。教材 §1.6 开篇（p.44）指出计数出现在两类场景：其一是等可能样本空间下直接套均匀律；其二是各结果概率同为已知 $p$ 的情形，此时 $P(A) = p \cdot |A|$——只需数 $|A|$，二项概率（本讲后面）就是这类。幻灯片那句"只需要数数"正是这一约化的口号：余下的全部工作，只是把分子分母各自数出来。所以本讲表面上是"计数技巧课"，实质是**均匀律的弹药库**：排列、组合、划分都是为"数 $|A|$"服务的工具。计数本身"原则上简单、实践中挑战"（教材原话），它的艺术正是你在 6.042J 组合数学里练过的基本功，本讲把那些工具接入概率计算。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Basic counting principle（基本计数原理）</span>

- **基本计数原理**：实验分 $r$ 个 stage（阶段），第 $i$ 阶段有 $n_i$ 种选择，则选择总数为
```math
n_1 n_2 \cdots n_r .
```

> <span style="color:#7f8c8d;">图：$r$ 级计数树（分支不带概率）——根节点经第 1 阶段的 $n_1$ 个分支、第 2 阶段的 $n_2$ 个分支……直到第 $r$ 阶段的 $n_r$ 个分支；树叶总数 = 沿各级分支数连乘 $n_1 n_2 \cdots n_r$（对应教材 Fig. 1.17）。</span>

> <span style="color:#7f8c8d;">Bertsekas §1.6, p.44–45</span>

**例**：连续掷一颗六面骰子六次，全部给出不同数字的概率是多少？
- 使事件发生的结果数：$\underline{\qquad}$
- 样本空间中的元素个数：$\underline{\qquad}$
- 答案：$\underline{\qquad}$

**更多填空**：
- 3 个字母 + 4 个数字的车牌数（可重复）= $\underline{\qquad}$
- ……若禁止重复 = $\underline{\qquad}$
- 排列（Permutations）：$n$ 个元素排序的方式数 = $\underline{\qquad}$
- $\{1, \ldots, n\}$ 的子集数 = $\underline{\qquad}$

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 逐个验算空栏（每题都拆成"分阶段乘"）：
> - 六骰全不同：有利结果 = 各阶段依次少一种选择，$6 \cdot 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 6! = 720$；样本空间 $|\Omega| = 6^6 = 46656$；答案 $6!/6^6 = 720/46656 \approx 0.0154$（约 1.5%）✓。
> - 车牌（可重复）：字母与数字独立分段，$26^3 \cdot 10^4 = 175760000$ ✓（约 1.76 亿）。
> - 禁止重复：$26 \cdot 25 \cdot 24 \cdot 10 \cdot 9 \cdot 8 \cdot 7 = 78624000$ ✓——注意"禁止重复"只是让**每段内部**的选择逐次递减，分段结构不变。
> - $n$ 个元素排序 = $n!$（$k = n$ 的 $k$-排列特例）；$\{1,\ldots,n\}$ 的子集数 = $2^n$——把"选子集"看成 $n$ 个阶段的"收/不收"二元决策，$2 \cdot 2 \cdots 2 = 2^n$ ✓（教材 Example 1.27，p.46）。
> 教材同类例是电话号码（Example 1.26，p.45–46：首位非 0/1，共 $8 \cdot 10^6$ 个 7 位号码）——与车牌是同一套路。计数原理本质是**分治**：把一个大的计数问题切成 $r$ 个小阶段，逐阶段数完再连乘；树状图上就是"数树叶"。这与你在 CLRS 见过的分治套路一脉相承——都是"切阶段、解子问题、按既定规则合并"，只是计数里的合并规则是乘法。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Combinations（组合）</span>

- $\binom{n}{k}$：给定的 $n$ 元素集合中含 $k$ 个元素的子集个数。
- **两种方式**构造 $k$ 个不同元素的有序序列：
  - 一次选一个，共选 $k$ 次：$n(n-1) \cdots (n-k+1) = \dfrac{n!}{(n-k)!}$ 种选择。
  - 先选出 $k$ 个元素（$\binom{n}{k}$ 种），再排序（$k!$ 种排法）。
- 因此：
```math
\binom{n}{k} \cdot k! = \frac{n!}{(n-k)!} \qquad \Longrightarrow \qquad \binom{n}{k} = \frac{n!}{k!\,(n-k)!} .
```
- 又有：
```math
\sum_{k=0}^{n} \binom{n}{k} = 2^n .
```

> <span style="color:#7f8c8d;">Bertsekas §1.6, p.46–48</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板）:**</span> 这页的核心是一个可复用模板——**double counting（双计数）**：对同一批对象用两种方式计数，两个答案必须相等，由此解出未知量。这里"有序 $k$-序列"被数了两遍：一遍按"逐个选"（$n!/(n-k)!$，即 $k$-排列公式，p.46），一遍按"先选后排"（$\binom{n}{k} \cdot k!$），相等即得组合公式。命名模板：**"先选后排"分解**——任何"有序选取"问题都能拆成"无序选取 $\times$ 排列数"，这是 6.042J 组合证明的老朋友。至于 $\sum_k \binom{n}{k} = 2^n$：教材（p.48）的路径是先概率后计数——由 §1.5 的二项公式 $\sum_k \binom{n}{k} p^k(1-p)^{n-k} = 1$ 取 $p = 1/2$，两边同除 $(1/2)^n$ 即得恒等式；随后教材才给出计数解释：左边按"子集大小"分类数子集，右边直接数子集（每元素收/不收，$2 \cdot 2 \cdots 2 = 2^n$）——两条论证互相印证，同属双计数思想。**概率论证反哺组合恒等式**，这是两门学科互相输血的第一个样本。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Binomial probabilities（二项概率）</span>

- $n$ 次 independent coin tosses（独立掷硬币），$P(H) = p$。
- **课堂计算**：$P(\text{HTTHHH}) = \underline{\qquad}$
- 每个具体序列：
```math
P(\text{sequence}) = p^{\#\text{heads}} \,(1-p)^{\#\text{tails}} .
```
- 于是：
```math
P(k \text{ heads}) = \sum_{\text{k-head seq.}} P(\text{seq.}) = (\#\text{ of } k\text{-head seqs.}) \cdot p^k (1-p)^{n-k} = \binom{n}{k}\, p^k (1-p)^{n-k} .
```

> <span style="color:#7f8c8d;">Bertsekas §1.5, p.41–43；§1.6, p.44</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 结构洞察）:**</span> 验算：HTTHHH 含 4 个 H、2 个 T，由独立投掷模型（Lec 03 的树）概率沿路径连乘，$P(\text{HTTHHH}) = p^4(1-p)^2$ ✓。二项公式的推导是**两步走**："单序列概率"（独立模型下每条含 $k$ 个 H 的序列概率同为 $p^k(1-p)^{n-k}$）+ "序列计数"（$\binom{n}{k}$ 条），两者相乘。注意它正好是本讲开篇的场景 (b)：$P(A) = p^k(1-p)^{n-k} \cdot \binom{n}{k}$——场景 (b) 中"已知的结果概率"在这里取值 $p^k(1-p)^{n-k}$（勿与硬币偏置 $p$ 混淆），$A$ = "恰 $k$ 次正面"这个事件。卡点诊断：$\binom{n}{k}$ 在这里不是"抽象符号"而是"正面出现位置的选法数"——从 $n$ 个位置里挑 $k$ 个给 H，其余给 T；上一节的组合公式由此直接落地。"序列等概率 + 只数个数"这个结构会在下一节条件概率问题里再次发力。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Coin tossing problem（掷硬币问题）</span>

- 事件 $B$：10 次投掷中恰有 3 次"正面"。
  - 已知 $B$ 发生了，前 2 次投掷都是正面的（条件）概率是多少？
- 集合 $B$ 中所有结果等可能：每个概率为 $p^3(1-p)^7$。
  - **条件概率律是均匀的**（uniform）。
- $B$ 中结果数：$\underline{\qquad}$
- $B$ 中以 HH 开头的结果有多少？$\underline{\qquad}$

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 验算并补全：
> - $|B| = \binom{10}{3} = 120$ ✓；以 HH 开头 = 前 2 次已定，剩 8 次里恰 1 次正面，$\binom{8}{1} = 8$ ✓。
> - 所求条件概率 $= \dfrac{\binom{8}{1}}{\binom{10}{3}} = \dfrac{8}{120} = \dfrac{1}{15} \approx 0.067$。
> 完整推导走条件概率定义：$P(\text{前两 H} \mid B) = \dfrac{P(\text{前两 H 且恰 3 H})}{P(B)} = \dfrac{\binom{8}{1}\,p^3(1-p)^7}{\binom{10}{3}\,p^3(1-p)^7}$——分子分母里的 $p^3(1-p)^7$ 被**完整约掉**，答案 $\tfrac{1}{15}$ 与 $p$ 无关。
> 卡点诊断：为什么能约掉？因为 $B$ 内每条序列的概率**全都是同一个值** $p^3(1-p)^7$——"恰 3 次正面"的信息把 120 条序列拉平成等可能，条件概率律退化为均匀律，硬币偏好被"吞"进公共因子。这正是均匀律 + 计数的复合威力：**条件化可以制造均匀性**。与 Lec 03 的"$\tfrac13$ 与 $p$ 无关"是同一个现象的另一化身（那里是"恰 1 次正面在哪次投掷"，这里是"3 次正面在哪些位置"）；更一般地，给定"恰 $k$ 次正面"时正面位置的分布是均匀的——这个事实在统计推断（如"次序统计量"）里会反复出现。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Partitions（划分）</span>

**例**：将一副 52 张的牌发给 4 名玩家（每人 13 张）。求 $P(\text{每人得到一张 ace（A 牌）})$。

- 结果 = 52 张牌的一个划分：结果总数为
```math
\frac{52!}{13!\,13!\,13!\,13!} .
```
- 数 4 张 ace 的分配方式：$4 \cdot 3 \cdot 2$（第 1 人 $4$ 选 $1$，第 2 人 $3$ 选 $1$，第 3 人 $2$ 选 $1$，第 4 人拿剩下的——故 $= 4!$）。
- 数其余 48 张牌的发牌方式：
```math
\frac{48!}{12!\,12!\,12!\,12!} .
```
- 答案：
```math
\frac{\;4 \cdot 3 \cdot 2 \;\cdot\; \dfrac{48!}{12!\,12!\,12!\,12!}\;}{\dfrac{52!}{13!\,13!\,13!\,13!}} = \frac{4! \cdot 13^4}{52 \cdot 51 \cdot 50 \cdot 49} \approx 0.1055 \;\; \text{（译者化简）} .
```

> <span style="color:#7f8c8d;">Bertsekas §1.6, p.49–51</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 验算：$\dfrac{4!\,(13!)^4\,48!}{(12!)^4\,52!}$，利用 $\dfrac{(13!)^4}{(12!)^4} = 13^4$、$\dfrac{48!}{52!} = \dfrac{1}{52\cdot 51\cdot 50\cdot 49}$，得 $\dfrac{24 \cdot 28561}{6497400} \approx 0.1055$（约 10.5%）✓。另一路验证：逐张发 ace，第一个 ace 落在哪一队都行（概率 1），第二个 ace 必须避开那一队（$39/51$），第三个避开两队（$26/50$），第四个别无选择（$13/49$），$1 \cdot \tfrac{39}{51} \cdot \tfrac{26}{50} \cdot \tfrac{13}{49} \approx 0.1055$，两路吻合 ✓。直觉核对：每人一张 ace 并非罕见——"4 张 ace 分进 4 只桶、每桶恰一张"远比"全聚在一桶"容易。
> 这类"把 $n$ 个对象分成 $r$ 组、各组 $n_i$ 个"的计数就是教材 Partitions 小节（p.49）的 **multinomial coefficient（多项式系数）** $\dfrac{n!}{n_1!\,n_2!\cdots n_r!}$——逐组选取用组合数连乘再约简即得。跨课程连接：你在 6.042J 见过多项式定理 $(x_1 + \cdots + x_r)^n = \sum \frac{n!}{n_1!\cdots n_r!} x_1^{n_1}\cdots x_r^{n_r}$，那组系数正是这里的计数。教材 Example 1.32（p.50）的 TATTOO 变位词（$6!/(3!\,1!\,2!) = 60$）是多项式系数的直接应用——把 6 个位置分成"3 个 T 位、1 个 A 位、2 个 O 位"；而 Example 1.33（p.50 题干、p.51 答案：4 名研究生 + 12 名本科生共 16 人分 4 组、每组 4 人，每组都含研究生的概率 $= \frac{12\cdot 8\cdot 4}{15\cdot 14\cdot 13}$）才与本讲 ace 例同构——"每组至少一个特殊元素"的概率，只是把"玩家"换成"小组"、"ace"换成"研究生"。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
