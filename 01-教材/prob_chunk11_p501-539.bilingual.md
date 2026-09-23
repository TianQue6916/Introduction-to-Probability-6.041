<!-- ===== PDF p501 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">[原页此处 Example 号 OCR 损坏/承接单元 10，以「（续）」续接；按可见序列 Example 9.14 为本站内下一锚点]</span>

> <span style="color:#7f8c8d;">本页（书页 494）页首承接单元 10 末尾的同一例题——两个正态随机变量的似然比检验（likelihood ratio test, LRT）——继续计算其误接受概率 $\beta(R)$，并把 LRT 与另一形状的拒绝域 $R'=\{ (x_1,x_2)\mid \max\{x_1,x_2\}>\gamma\}$ 的性能加以对比。此段以「（续）」续接，未另起新例号；紧接其后本页便出现明确的 **Example 9.14**。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.12/9.13（续）——两正态变量的似然比检验：误接受概率对比**</span>

误接受概率（false acceptance probability）由下式给出

```math
\beta(R) = P(X_1 + X_2 \le 2.33;\; H_1)
= P\!\Big(\frac{X_1 + X_2 - 4}{\sqrt{2}} \le \frac{2.33 - 4}{\sqrt{2}};\; H_1\Big)
= P(Z \le -1.18),
```

其中 $Z$ 为标准正态。由于 $P(Z \le -1.18) = P(Z \ge 1.18) = 1 - P(Z \le 1.18)$，而 $P(Z \le 1.18) = 0.88$，于是

```math
\beta(R) = 1 - 0.88 = 0.12.
```

现在我们把 LRT 的性能，与一个不同形状的拒绝域 $R'$ 所导致的性能加以比较。例如，考虑一个如下形式的拒绝域（rejection region）

```math
R' = \{ (x_1, x_2) \mid \max\{x_1, x_2\} > \gamma\},
```

其中 $\gamma$ 的取值使得误拒概率（false rejection probability）再次等于 $0.05$。为确定 $\gamma$ 的值，我们写成

```math
0.05 = P(\max\{X_1, X_2\} > \gamma;\; H_0)
= 1 - P(\max\{X_1, X_2\} \le \gamma;\; H_0)
= 1 - P(X_1 \le \gamma;\; H_0)\, P(X_2 \le \gamma;\; H_0),
```

其中 $Z$ 为标准正态。上式给出 $P(Z \le \gamma;\; H_0) = \sqrt{1 - 0.05} \approx 0.975$。利用正态分布表（normal tables），我们得出结论 $\gamma = 1.96$。

> <span style="color:#7f8c8d;">[原页此处 OCR 轻度碎裂] 上式的中间一行在源 OCR 中被拆成碎片(如 `0.05 = P max{X1 , X2 } >`、`- p ( max{ X l , X2 } ::; (; Ho)`、`= 1 - P ( XI ::; (; Ho) P (X2 ::; (j Ho )` 等),现按「$P(Z \le (\gamma;\;H_0) = \sqrt{1-0.05}\approx 0.975$」的标准推导语义还原，数值未改动。</span>

现在让我们计算相应的误接受概率。令 $Z$ 再次表示标准正态变量，则有

```math
\beta(R') = P(\max\{X_1, X_2\} \le 1.96;\; H_1)
= \big(P(X_1 \le 1.96;\; H_1)\big)^2
= \big(P(X_1 - 2 \le -0.04;\; H_1)\big)^2
= \big(P(Z \le -0.04)\big)^2
= (0.49)^2 = 0.24.
```

我们看到，LRT 的误接受概率 $\beta(R) = 0.12$ 远优于另一检验——即替代拒绝域 $R'$——的误接受概率 $\beta(R') = 0.24$。

> <span style="color:#1e8449;">**[t_note]** 注：这个对比就是『最优性』的直观标本：在相同误拒概率 0.05 下，LRT 把误接受压到 0.12，而形状随意的 $R'$ 只得 0.24。先证其所以然——LRT 的拒绝域贴着似然比『最能区分 $H_0/H_1$ 的那一带』，内曼–皮尔逊引理（Neyman–Pearson lemma）保证：对简单假设，固定误拒概率下 LRT 在所有检验中使误接受概率最小，故此差距不是巧合而是定理。跨课程（离散数学 6.042J·反证结构）：『固定一类错误再最小化另一类』与反证里『先锚定前提再推导矛盾』同构——最优检验就是这两种错误率在约束下的极限解。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.14（一个离散的例子，A Discrete Example）**</span>

考虑对一枚硬币做 $n=25$ 次相互独立的抛掷。在原假设 $H_0$（分别地，备择假设 $H_1$）之下，每次抛掷出现正面的概率分别为 $\theta_0 = 1/2$（分别地，$\theta_1 = 2/3$）。令 $X$ 表示观察到的正面次数。若我们把误拒概率（false rejection probability）设定为 $0.1$，那么与 LRT 相关联的拒绝域（rejection region）是什么？

---

<!-- ===== PDF p502 ===== -->

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）**</span>

> <span style="color:#7f8c8d;">本页（书页 495）顶部承接上一页（书页 494）同一例子的尾部——广义似然比（LRT）下离散例的误拒概率 $\beta$ 与临界值 $\gamma$ 的求解（经精确二项尾与中心极限定理近似两法，得出 $\gamma=16$ 与 $X>15$），因此本段以「（续）」续接，编号为 **Example 9.14（续）**。随后本页正文正式开启 §9.4 显著性检验（Significance Testing）一节。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.14（续）——一个离散例（A Discrete Example）**</span>

我们观察到，当 $X = k$ 时，似然比（likelihood ratio）具有如下形式

```math
L(k) = \frac{\binom{n}{k}\,\theta_1^{\,k} (1-\theta_1)^{n-k}}{\;\binom{n}{k}\,\theta_0^{\,k} (1-\theta_0)^{n-k}\;}
     = \Bigl(\frac{\theta_1}{\theta_0}\Bigr)^{k}\,\Bigl(\frac{1-\theta_1}{1-\theta_0}\Bigr)^{n-k} .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 该似然比公式在源 OCR 中被切得十分零碎（如 `n    8(1-8 d n - k`、`80(1-80t k`、`2 k () 25` 等残句），其逐字结构已无法复原；上文按 §9.3 中 LRT 的标准形式 $\dfrac{\theta_1^k (1-\theta_1)^{n-k}}{\theta_0^k (1-\theta_0)^{n-k}}$ 作忠实重建。页内可辨且经下文核验的数值锚点 $\gamma = 16$ 与「$X > 15$」予以保留，未臆造任何原文未含的具体数值。</span>

> <span style="color:#1e8449;">**[t_note]** 注：本例的关键一步是『把 25 次抛掷的高维判定压成一维』：因为 $L(k)$ 随 $k$ 单调递增，拒绝条件 $L(k)>\zeta$ 与 $X>\gamma$（只数正面数）完全等价。先证：当 $\theta_1>\theta_0$ 时 $(\theta_1/\theta_0)^k$ 随 $k$ 增大、$((1-\theta_1)/(1-\theta_0))^{n-k}$ 随 $k$ 减小，但前者的相对增长率更大，净效应仍是 $L$ 单调。因而检验不需要知道抛掷顺序，只看正面总数即可——这正是『统计量压缩数据』的雏形，也是后文充分统计量（sufficient statistic）思想的第一处伏笔。</span>

注意到 $L(k)$ 是 $k$ 的单调递增函数（monotonically increasing function of $k$）。因此，拒绝条件 $L(k) > \zeta$（临界值）等价于 $k > \gamma$ 这一条件，只要适当地选定 $\gamma$ 即可。我们得出结论：LRT（likelihood ratio test，似然比检验）具有如下形式，
```math
\text{reject } H_0 \quad\text{if}\quad X > \gamma .
```
为满足对误拒概率（false rejection probability）的要求，我们需要找到使 $P(X > \gamma;\, H_0) \le 0.1$ 的 $\gamma$ 的最小可能值。

通过对上式右侧就不同的 $\gamma$ 取值作数值计算（numerically），我们找到所需的值为 $\gamma = 16$。

> <span style="color:#1e8449;">**[t_note]** 注：注意这里的约束是『$\le 0.1$』而非『$= 0.1$』。因为 $\gamma$ 是整数、$X$ 是离散的，$P(X>\gamma;\,H_0)$ 并非 $\gamma$ 的连续函数，无法精确命中 0.1，只能在满足 $P\le 0.1$ 的前提下取最小可能值——这对应『最难误拒』的那一档。先证：这是离散分布下的固有现象，也正是本页紧下面『用中心极限定理近似得 $\gamma=15.7$ 再上取整』的原因——近似值落在非整数处，就必须朝更安全（误拒更小）的整数方向收，才能守住 $\alpha$ 这条红线。</span>

选择 $\gamma$ 的另一方法基于中心极限定理（central limit theorem）的近似。在 $H_0$ 之下，
```math
Z = \frac{X - n\theta_0}{\sqrt{n\theta_0(1-\theta_0)}} = \frac{X - 12.5}{\sqrt{25/4}}
```
近似地是一标准正态随机变量（standard normal random variable）。因此，我们需要
```math
0.1 = P(X > \gamma;\, H_0)
   = P\Bigl(\frac{X-12.5}{\sqrt{25/4}} > \frac{\gamma - 12.5}{5/2}\,;\, H_0\Bigr)
   = P\Bigl(Z > \frac{2\gamma}{5} - 5\Bigr).
```

由正态分布表（normal tables），$\Phi(1.28) = 0.9$，因此我们应选取 $\gamma$ 使得 $(2\gamma/5) - 5 = 1.28$，即 $\gamma = 15.7$。由于 $X$ 是整数值（integer-valued）随机变量，我们发现 LRT 应在 $X > 15$ 时拒绝 $H_0$。

> <span style="color:#1e8449;">**[t_note]** 注：本例首次示范『精确解法 与 中心极限近似解法』并存：枚举得 $\gamma=16$、CLT 得 $\gamma=15.7$、上取整为 $X>15$。先证：CLT 把『找 $\gamma$』变成解方程 $(2\gamma/5)-5=1.28$（因为 $X$ 近似正态、$\Phi(1.28)=0.9$），但正态近似管不住尾部的离散细节，于是用 $X>15$（等价于整数直方右移到 15.7 之上）保证误拒概率不倒退。这三条等价的临界表达（16 / 15.7 / >15）是理解『连续近似取整回离散』的心法，也是本单元多处大样本近似的样板。</span>

---

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（正文开篇）**</span>

真实场景中遇到的假设检验问题并非总能归结为两个事先指定良好的备择假设，因此上一节所述方法并不能简单套用于此。本节的目的是为这类更一般的问题类引入一种方法。不过我们要提醒的是，并不存在唯一或普适的方法，这类问题的处理带有相当程度的判断与艺术成分在起作用。

> <span style="color:#1e8449;">**[t_note]** 注：这句『判断与艺术』不是客套，而是给显著性检验（significance testing）定基调：它只面对一个复合备择『找证据』，没有唯一最优答案。先证：当 $H_1$ 是复合假设（包含无穷多个 $\theta$）时，上一节内曼–皮尔逊引理的『唯一最优』失效，你必须在『选哪个统计量、取多宽的拒绝域』上做工程取舍。跨课程（凸优化·建模自由）：这其实就是建模者的自由度问题——把开放的生问题翻译成可解形式，与凸优化里『如何把问题写成可解凸形式』是同一种判断力。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p503）：本页只是 §9.4 的开篇过渡段，后续页将展开显著性检验方法学的各子节（The General Approach、Significance Testing Methodology 等）。</span>

---

<!-- ===== PDF p503 ===== -->
<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">本节承接上一页：本页首为 §9.4 开篇的动机型例子与「受限讨论范围」条件 (a)-(c) 的叙述（属上页 §9.4 小节标题之下的延续，故页首仍标「（续）」）；随后本页内另起新子节标题 **The General Approach（通用方法）**，并在页末引出新例 **Example 9.15（Is My Coin Fair?）**，其叙述延续到下一页。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 本页未知参数符号 $\theta$ 在源 OCR 中被多处拆碎：页首 "Xl : Xn" 为 $X_1, \ldots, X_n$ 的碎行、字母为 $\theta$、"(j =1= (jo" 为 $\theta\neq\theta_0$、下标的原假设 "Ho"/备择假设 "HI" 为 $H_0$/$H_1$。"(j"（作为参数符号）与 $\theta_0$ 依据行文语义与符号位置还原为规范 $\theta$、$\theta_0$，未作数值性臆造；其余叙述文本经由 OCR 基本完整可辨。</span>

为了获得一些动机（motivation），考虑如下这类问题：

- (i) 一枚硬币被反复且独立地抛掷。这枚硬币是公平（fair）的吗？
- (ii) 一枚骰子被反复且独立地抛掷。这枚骰子是公平的吗？
- (iii) 我们观测到一列独立同分布（i.i.d.）的正态随机变量 $X_1, \ldots, X_n$。它们是标准正态（standard normal）的吗？
- (iv) 两种不同的药物治疗（drug treatments）分别施用于两组患有同一疾病的病人。第一种治疗是否比第二种更有效？
- (v) 在历史数据（比如基于最近一年的数据）的基础上，道琼斯工业平均指数（Dow Jones Industrial Average）的每日变化是否服从正态分布？
- (vi) 在关于两个随机变量 $X$ 和 $Y$ 的若干样本对 $(X_i, Y_i)$ 的基础上，我们能否判定这两个随机变量是否相互独立？

> <span style="color:#1e8449;">**[t_note]** 注：这组例子是整章方法的地图：(i)(ii)(iii)对应简单原假设（直接可算误拒概率），(iv)(v)(vi)对应复合备择或非参数情形。先证：(iii)『是否标准正态』是拟合优度（goodness of fit）的对象，(vi)『是否独立』正是后面卡方型列联表检验能覆盖的场景——它们不再是『$\theta$ 等于某数吗』，而是『数据的分布形状/依赖结构符合预期吗』。跨课程（CSAPP·实验对照）：两变量独立性检验正是系统评测『分组是否真的随机』时背后那套统计验证机制，你的 A/B 直觉从这里生根。</span>

在以上所有情形中，我们处理的都是涉及不确定性的现象，这种不确定性想必由某个概率模型（probabilistic model）所支配。我们有一个默认假设，通常称作原假设（null hypothesis），记为 $H_0$；我们希望基于观测 $X = (X_1, \ldots, X_n)$ 判定原假设是否应当被拒绝。

为避免使关键思想变得晦涩（obscure），我们主要将讨论范围限制在具有如下特征的情形上。

- (a) 参数化模型（Parametric models）：我们假设观测 $X_1, \ldots, X_n$ 具有由联合 PMF（联合概率质量函数，离散情形）或联合 PDF（联合概率密度函数，连续情形）所支配的分布，该分布由属于给定可能参数集合 $M$ 的某个未知参数 $\theta$（标量或向量）完全确定。
- (b) 简单原假设（Simple null hypothesis）：原假设断言 $\theta$ 的真值等于 $M$ 中的给定元素 $\theta_0$。
- (c) 备择假设（Alternative hypothesis）：备择假设（记为 $H_1$）只是陈述 $H_0$ 不为真，即 $\theta \neq \theta_0$。

参照前面引入的动机型例子，注意例子 (i)-(ii) 满足上述条件 (a)-(c)。另一方面，在例子 (iv)-(vi) 中，原假设不是简单的（simple），违反了条件 (b)。

> <span style="color:#1e8449;">**[t_note]** 注：条件 (a)(b)(c) 划定了本节脚手架：参数化模型 + 简单原假设 + 『万能』复合备择 $H_1:\theta\ne\theta_0$。先证：条件 (b) 是灵魂——$H_0$ 简单，『在原假设下算误拒概率』才成为可精算的问题；而 $H_1$ 允许 $\theta$ 取任意非 $\theta_0$ 的值，正因它太开放，才需要引入统计量而非直接的似然比。例 (iv)-(vi) 因 $H_0$ 不简单而暂时出局，但方法本身可推广（卡方检验就用参数化技巧处理这类情形），这里先交代清楚讨论的地盘。</span>

---

<span style="color:#c0392b;">**通用方法（The General Approach）**</span>

我们通过一个具体例子引入这一通用方法（general approach）。随后我们总结并评论所涉及的各个步骤。最后，我们再考虑几个符合这一通用方法的例子。

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.15（Is My Coin Fair? 这枚硬币是公平的吗？）**</span>

一枚硬币被独立地抛掷 $n = 1000$ 次。设 $\theta$ 为每次抛掷出现正面的未知概率。所有可能参数的集合为……

> <span style="color:#7f8c8d;">衔接下一页：</span> <span style="color:#7f8c8d;">Example 9.15 于本页仅写出题设（$n=1000$ 次抛掷、$\theta$ 为正面概率、参数集 $M$），其该例的完整设定与后续取舍临界值 $\epsilon$ 的推导（源校核锚点：$\epsilon=31$、$s=472$）延续到下一页（PDF p504）。</span>

> <span style="color:#7f8c8d;">[原页页尾截断] 源 OCR 在 "The set of all"（即「所有可能参数的集合为……」）处页界截断，本页正文到此结束；例后的推导见下一页。</span>

---

<!-- ===== PDF p504 ===== -->
<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p504 − 7 = 书页 497，属 §9.4 内部子节「通用方法（The General Approach）」与「显著性检验方法学（Significance Testing Methodology）」的交界处。页首承接上一页（PDF p503）所引出、其题设已在上一页写出的 **Example 9.15（Is My Coin Fair?）** 之完整设定与后续推导，故例号以「（续）」处理；随后为该例的收束评注（「不拒绝」而非「接受」）、对通用方法的总结与推广，继而本页内另起子节标题 **Significance Testing Methodology（显著性检验方法学）** 并给出其步骤 (a)，步骤 (b)(c)(d) 延续到下一页（PDF p505）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页符号多处被 OCR 误读或拆碎：未知参数 $\theta$ 多次被读作「$()$」或Ｂ类占位，备择假设为 $\neq$；原假设 $H_0$ 读作 "Ho"、备择假设 $H_1$ 读作 "HI"；观测 $X_i$ 被拆成 "X."、"Xl"；临界值 $\epsilon$ 与显著性水平 $\alpha$ 在决策规则与误拒概率公式处被打成碎片（"Is  I > "、"P(reject Ho : Ho) = 0"、"° = 0.05"）。现象数值 $s=472$、$|472-500|=28\le 31$、$n=1000$、$p=1/2$、$\alpha = 0.05$ 均保持原样（与规范核对锚点 $\epsilon=31$、$s=472$ 一致）。下文按 §9.4 符号约定与可见上下文规范复原，非臆造数值。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.15（续）（Is My Coin Fair? 这枚硬币是公平的吗？）**</span>

可能参数的集合为 $M = [0,\,1]$。原假设（null hypothesis）$H_0$（“这枚硬币是公平的”）取 $\theta = 1/2$，而备择假设（alternative hypothesis）为 $\theta \neq 1/2$。

观测数据是一个序列 $X_1, \ldots, X_n$，其中 $X_i$ 的取值为 $1$ 或 $0$，取决于第 $i$ 次抛掷的结果是正面（heads）还是反面（tails）。我们这样来处理该问题：考察 $S = X_1 + \cdots + X_n$ 的值，也就是观测到的正面次数，并采用如下形式的决策规则：

```math
\text{reject } H_0 \quad\text{if}\quad \Big|\frac{S}{n} - \frac12\Big| > \epsilon,
```

其中 $\epsilon$ 是需要确定的合适临界值（critical value）。到目前为止，我们已经确定了拒绝域（rejection region）$R$ 的形状，即那些导致拒绝原假设的数据向量之集合。最后，我们选择临界值 $\epsilon$，使得误拒概率（false rejection probability）等于给定值 $\alpha$：

```math
P(\text{reject } H_0 \mid H_0) = \alpha.
```

通常，$\alpha$ 称为显著性水平（significance level），是一个较小的数；在本例中我们取 $\alpha = 0.05$。

到目前为止，上述讨论只涉及一系列直观的选择。现在需要进行一些概率计算来确定临界值 $\epsilon$。在原假设下，随机变量 $S$ 是以 $n = 1000$ 与 $p = 1/2$ 为参数的二项随机变量。借助二项分布的正态近似（normal approximation）与正态分布表，我们发现合适的选择是取临界值，使 $1000\epsilon = 31$，即要求 $|S - 500| \le 31$。例如，若 $S$ 的观测值碰巧为 $s = 472$，则

```math
\big|\,s - 500\,\big| = \big|\,472 - 500\,\big| = 28 \le 31,
```

从而在 $5\%$ 的显著性水平下，原假设 $H_0$ 不被拒绝（not rejected）。

> <span style="color:#1e8449;">**[t_note]** 注：临界值 $1000\epsilon=31$ 由正态近似反解：$H_0$ 下 $S\sim$ 二项$(1000,1/2)\approx$ 正态$(500,250)$，要求 $P(|S-500|>1000\epsilon)=\alpha$，对应标准化后 $|Z|>1.96$、即 $1000\epsilon\approx1.96\sqrt{250}\approx31$。先证：$s=472$ 处 $|472-500|=28\le31$，即离中心不足 1.96 个标准差，故 5% 下不拒绝。整段示范『假设分布近似 → 反解临界 → 作决策』的完整流水线，也与 Example 9.14 用 CLT 求 $\gamma$ 首尾相呼应——同一个方法在不同模型上的复现。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 上式中临界值对应的数值（$1000\epsilon = 31$、$|472-500| = 28$、比较值 $31$）在源 OCR 里被拆成碎片（"Is  I > "、"1472 - 5001 = 28 ::; 3 1"），此处按规范核对锚点（$\epsilon=31$、$s=472$）与上下文复原为规范表达式，数字未作改动。</span>

我们在前一例结尾使用「不拒绝（not rejected）」而非「接受（accepted）」这一措辞，是有意为之。我们没有任何坚实的依据去断言 $\theta$ 等于 $1/2$，而不是比如说 $0.51$。我们只能断言：$S$ 的观测值并未为反对原假设 $H_0$ 提供强有力的证据。

> <span style="color:#1e8449;">**[t_note]** 注：『不拒绝』≠『接受』，这是显著性检验最易绊脚的概念。先证：显著性水平 $\alpha$ 只能控制『误拒原假设』，它给不出『$H_0$ 恰好为真』的证据强度——$\theta=0.5$ 与 $\theta=0.51$ 在 1000 次抛掷下几乎压不住地面的区分。所以正确解读是『数据尚未构成反对 $H_0$ 的强证据』，而非『证明 $H_0$ 成立』。直觉（离散数学·反证/逻辑）：没有证据反驳 ≠ 命题为真，缺的是那一记能一脚踢翻 $H_0$ 的重证据——检验从不『证明』，只『证伪』。</span>

现在，我们能够对前一例的本质加以概括与推广，从而得到一种通用的方法论（generic methodology）。

---

<span style="color:#c0392b;">**显著性检验方法学（Significance Testing Methodology）**</span>

基于观测 $X_1, \ldots, X_n$，要对一个形如『$H_0 : \theta = \theta_0$』的假设进行统计检验（statistical test）。

- 在观测到数据之前，应依次执行以下步骤。
  - (a) 选择一个统计量（statistic）$S$，即一个用以概括待获取数据的标量随机变量。数学上，这涉及选取一个函数 $h : \mathbb{R}^n \to \mathbb{R}$，从而得到统计量 $S = h(X_1, \ldots, X_n)$。

> <span style="color:#1e8449;">**[t_note]** 注：方法学的第一步就点明显著性检验的性质：把数据向量 $X\in\mathbb{R}^n$ 压成一个标量统计量 $S=h(X)$——这是刻意的信息降维。先证：$S$ 选得好不好决定检验成败，理想 $S$ 应『在 $H_0$ 下分布已知、在偏离 $H_0$ 时明显偏移』（后面 Examples 9.15–9.17 正是照此挑选）；若 $S$ 是充分统计量（见 §9.1 习题 11–14），则压缩不丢任何关于 $\theta$ 的信息。跨课程（线性代数·数据降维/投影）：把高维数据映到一维坐标本质上是你学过的线性降维，$S$ 相当于挑一条『能最大限度分离 $H_0$ 与 $H_1$』的方向。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 步骤 (a) 中函数射向的符号 "$h : \mathbb{R}^n \to \mathbb{R}$" 的箭头在源 OCR 中被拆成独立碎行（"n"、"--->"、"."），已按数学语义规范为 $h : \mathbb{R}^n \to \mathbb{R}$。步骤 (b)(c)(d) 延续到下一页（PDF p505）。</span>

---

<!-- ===== PDF p505 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p505 − 7 = 书页 498，属 §9.4 显著性检验（Significance Testing）内部子节「显著性检验方法学（Significance Testing Methodology）」。本页无新节标题、无新 Example：页首承接上一页同一方法论步骤清单，方法步骤（a）已在上一页交代，本页续述步骤（b）（c）（d），紧接为其后的要点评注（i）–（iii）。故用「（续）」续接，不另起新编号。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页统计量符号 $S$ 多处被 OCR 误读为「5」（如 "the set of values of 5"、"if 5 belongs to"、"values of 5 under which"），原假设 $H_0$ 被误读为 "Ho"、参数 $\theta$ 被误读为 "B"、临界值符号 $\gamma$ 处打印为占位符「」、例号 "Example 9.15" 被拆碎为 "Example 9 . 1 5"。下文均已按 §9.4 的符号约定与可见上下文予以规范复原，非臆造。</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

<span style="color:#c0392b;">**显著性检验方法学（Significance Testing Methodology）（续）**</span>

（接上一页方法论步骤清单）步骤 $b$：**确定拒绝域（rejection region）的形状**——通过指定这样一个“对值集”：当统计量 $S$ 取到这些值时，$H_0$ 将被拒绝，作为某个尚未确定的临界值（critical value）$\gamma$ 的函数。

步骤 $c$：**选择显著性水平（significance level）**，即所需的一类误拒概率 $H_0$ 被误拒的概率 $\alpha$。

步骤 $d$：**选择临界值 $\gamma$**，使得误拒概率等于（或近似等于）$\alpha$。至此，拒绝域（rejection region）便完全确定下来。

> <span style="color:#1e8449;">**[t_note]** 注：步骤 (c)(d) 把检验完全钉死：先定 $\alpha$（你容忍的最大误拒概率），再反解临界值 $\gamma$ 使误拒概率恰为 $\alpha$。先证：$\alpha$ 与 $\gamma$ 不是互相独立的两个旋钮——一旦 $\alpha$ 定下、且 $S$ 在 $H_0$ 下的分布已知，$\gamma$ 就被唯一确定（从拒绝域尾端往内数入 $\alpha$ 的概率质量）。后面 Example 9.16 的 $|S|>1.96$ 就是 $\alpha=0.05$ 的标准解；$\alpha$ 若改小则 $\gamma$ 变大、拒绝域收窄。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 步骤（c）（d）与评注（iii）中出现多次的误拒概率符号，源 OCR 均读作「Q」（如 "the desired probability Q"、"equal ... to Q"、"false rejection probability Q ... between Q = .10 and Q = 0.01"）。按 §9.4 全章符号约定，误拒概率/显著性水平一律用 $\alpha$ 表示（§5：$\alpha$ 为显著性水平），故统一规范为 $\alpha$，仅此处作符号修正、未改动任何数值（$0.10$ 与 $0.01$ 两值照原样保留）。</span>

当观测到 $X_1, \ldots, X_n$ 的一组取值 $X_1, \ldots, X_n$ 之后：

（i） 计算统计量 $S$ 的取值 $s = h(X_1, \ldots, X_n)$。

（ii） 若 $s$ 属于拒绝域（rejection region），则拒绝原假设 $H_0$。

我们针对上述方法论的各个环节，补充一些评述与解释。

（i） 对于如何选择“恰当的”统计量 $S$，并没有放之四海而皆准的方法。在某些情形下，如 Example 9.15 中那样，这样的选择是自然而然的，并且也能从数学上加以论证。在其他情形下，一个有意义的 $S$ 之选取，往往牵涉到似然比（likelihood ratio）的某种推广，这一点将在本节稍后谈到。最后，在许多场合下，首要考虑的因素是 $S$ 是否足够简单，从而能完成我们上述方法论中步骤（d）所需的计算。

（ii） 在 $H_0$ 成立时使 $H_0$ 不被拒绝的那组 $S$ 取值，通常是环绕着 $H_0$ 下 $S$ 之分布峰值的一个区间（见 Figure 9.13）。当样本量 $n$ 很大时，中心极限定理（central limit theorem）往往适用于 $S$，而正态分布的对称性则提示我们采用一个关于 $S$ 的均值对称的区间。类似地，Example 9.15 中拒绝域的对称性之所以合理，其根据是：在 $H_0$ 成立的条件下，$S$ 的分布（参数为 $1/2$ 的二项分布）关于其均值是对称的。然而在其他情形下，非对称的拒绝域反而更为恰当。例如，若我们确信 Example 9.15 中的那枚硬币满足 $\theta \ge 1/2$，那么采用单侧拒绝域（one-sided rejection region）便是自然而然的：

```math
\text{reject } H_0 \quad \text{if} \quad \frac{S}{n} - \frac{1}{2} > \epsilon .
```

> <span style="color:#1e8449;">**[t_note]** 注：双侧 vs 单侧拒绝域的选择依据是『备择方向是否已知』。先证：题设『确信 $\theta\ge1/2$』时，$S/n<1/2$ 那一侧无论如何都不可能指向 $H_1$，把它纳入拒绝域只会白白消耗 $\alpha$；改为单侧后，同样水平的 $\alpha$ 全部投向 $S/n>1/2$ 一侧，对 $\theta>1/2$ 的检出力（power）更强。直觉：把火力对准唯一可能出错的半边。这是『先验方向信息如何折算成检验效能』的典型样例，和 Example 9.17 的单侧变体同源。</span>

> <span style="color:#7f8c8d;">图注（Figure 9.13，交叉引用）：$H_0$ 下统计量 $S$ 的分布峰值及其附近对应的接受区间（acceptance region）示意图——见上一小节“The General Approach（通用方法）”异常图编号所指向的显著性检验拒绝域示意图。</span>

（iii） 误拒概率 $\alpha$ 的典型取值大致介于 $\alpha = 0.10$ 与 $\alpha = 0.01$ 之间。当然，我们总是希望误拒情形尽量少出现；但鉴于此前在简单二元假设（simple binary hypotheses）语境下讨论过的此种权衡（tradeoff），若把 $\alpha$ 取得更小，反而会使我们更难拒绝一个错误的假设，也就是会增大误接受（false acceptance）发生的概率。

> <span style="color:#1e8449;">**[t_note]** 注：把 $\alpha$ 取小有双重效果：误拒更少（更『保守』），但拒绝域随之收窄，真实的偏差 $\theta\ne\theta_0$ 更不易被抓到——误接受随之上升。先证：这与二元假设检验里第一/二类错误（Type I/II error）的此消彼长是同一件事，只是显著性检验的 $H_1$ 不具体，只能定性地称『更难拒绝一个错误的假设』。跨课程（实分析·极限）：$\alpha\to0$ 时拒绝域趋空、检验几乎从不拒绝——那不是『更严谨』，而是彻底丧失区分力，正如把 $\epsilon$ 取得过小让几乎所有反例都『成立』。</span>

---

<!-- ===== PDF p506 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p506 − 7 = 书页 499，属 §9.4 显著性检验（Significance Testing）内部子节「显著性检验方法学（Significance Testing Methodology）」。本页无新节标题、无新 Example：页首承接上一页方法论要点评注（i）–（iii），续述评注（iv）——显著性水平与拒绝域、大样本正态近似，并以 p 值（p-value）的判据收尾（等价地，p 值小于显著性水平则拒绝 $H_0$）。故用「（续）」续接，不另起新编号。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页文本 OCR 严重碎裂：页首图名 "Rejection regions for significance testing" 与图注 "Figure 9.13：Two-sided and one-sided…" 被拆成碎片；正文多数叙述句只余单词（如 "based on a statistic S"、"1% the time"、"p-value… smaller than 0.05" 等）。下文按 §9.4 显著性检验方法学的语义与可见片段做忠实重建，仅保留原文明确出现的数值（$1\%$、$0.05$），未臆造其他数字。</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

<span style="color:#c0392b;">**显著性检验方法学（Significance Testing Methodology）（续）**</span>

（接上一页要点评注，续述评注 iv 与 p 值讨论）

（iv） 显著性水平（significance level）$\alpha$ 就是误拒（false rejection）的概率，即在原假设 $H_0$（null hypothesis）成立这一前提之下，统计量（statistic）$S$ 落入拒绝域（rejection region）内的概率。

> <span style="color:#1e8449;">**[t_note]** 注：这是 $\alpha$ 最精确的定义：显著性水平就是『条件在 $H_0$ 为真上』的误拒概率。先证：它衡量的不是数据本身多不可思议，而是『若世界真是 $H_0$，我的这套算法冒下误判的风险有多大』。这划出显著性检验的一条红线——拒绝域必须在 $H_0$ 下概率可控，而它在 $H_1$ 下表现如何只是副产品。这个措辞已经预告了下一段要引入的 p 值：两者都盯住『$H_0$ 下的极端观测』，只是 $\alpha$ 在观测前定死，p 值待数据到手才算。</span>

> <span style="color:#7f8c8d;">图注（Figure 9.13，交叉引用）：显著性检验的拒绝域（rejection regions）示意——双侧（two-sided）与单侧（one-sided）拒绝域。$H_0$ 下统计量 $S$ 的分布峰值附近对应接受区间（acceptance region），双侧拒绝域在两端各取一条尾，单侧拒绝域只取一侧的尾。</span>

在原假设 $H_0$ 成立时，使 $H_0$ 不被拒绝的那组 $S$ 取值，通常是环绕 $H_0$ 下 $S$ 之分布峰值的一个区间（见 Figure 9.13）。当样本量 $n$ 很大时，我们常常可以利用一些可靠的近似（approximations），例如基于中心极限定理（central limit theorem）的正态近似。此时统计量 $S$ 在其均值附近的分布大体对称，正态分布的对称性便提示我们采用一个关于 $S$ 之均值对称的拒绝域。然而在其他一些情形下，若难以判定 $S$ 的确切分布，也可以借助上述大样本正态近似来设定一个既实用又合理的拒绝域。

在实践中，当我们所计算的观测结果在原假设 $H_0$ 之下出现得如此罕见时——例如在 $H_0$ 成立时像这样极端的观测只会出现约 $1\%$ 的时长（only 1% the time）——这一极小概率就对 $H_0$ 构成了强有力（strong evidence）的反证，说明 $H_0$ 很可能是错误的。

> <span style="color:#1e8449;">**[t_note]** 注：这里给出 p 值（p-value）的频率式直感：p 值是『假设 $H_0$ 为真，观测到比手上数据更极端的情形』的概率。先证：『$1\%$ 的时长』是频率式解读——若反复在 $H_0$ 下重跑实验，只有约 1% 的样本会像现在这么极端。样本越极端，只有两种解释：或是撞了极小概率的大运，或是 $H_0$ 根本不真——当后者更合理时就构成反对 $H_0$ 的强证据。注意 p 值在『观测之后』才算，而 $\alpha$ 在观测之前就已定死，这两者绝不能互相替代。</span>

上述评注进一步引出了下述经常使用的判据（进入（c）步的检验阶段）：一旦他们算出了 p 值（p-value），就把它与所需的显著性水平（significance level）比较。等价地（Equivalently），当 p 值小于 $0.05$ 时，$H_0$ 应在 $\alpha$（显著性水平）下被拒绝：

```math
\text{reject } H_0 \quad \text{at the }\alpha\text{ significance level} \quad \text{if}\quad \text{p-value} \le \alpha.
```

> <span style="color:#1e8449;">**[t_note]** 注：p 值与显著性水平 $\alpha$ 的关系值得彻底厘清，这是本章最易混淆的一对。$\alpha$ 是观测前选定、用于构造拒绝域的固定阈值（第一类错误率的上限）；p 值是观测后由数据算出的『最小能拒绝 $H_0$ 的那一级显著性水平』，即『数据自身证据强度的连续度量』。判据『p 值 $\le\alpha$ 则拒绝』与『$S$ 落入 $\alpha$-拒绝域』完全等价，是同一行为的两种写法。先证：p 值越小、数据越极端，反证越强——所以 0.01 比 0.05 更值得惊讶，而 $\alpha$ 只是研究者预设的判决门槛。</span>

于是，p 值越小，反对原假设 $H_0$、支持备择假设（alternative hypothesis）的证据就越充分。若 p 值很小（例如不超过 $0.05$），我们便说这次检验在相应的显著性水平（例如 $0.05$）上是显著的（significant）。

> <span style="color:#1e8449;">**[t_note]** 注：『统计显著』（statistically significant）≠『实际重要』，这是做数据分析最常见的误读。先证：即使 $H_0$ 只是被轻微违反，只要样本量 $n$ 足够大，p 值就会被压到很小而判定显著——统计显著反映的是『证据强度』而非『效应大小』。跨课程（大数/Law of large numbers）：当 $n\to\infty$ 时检验几乎必然拒绝任何非精确成立的 $H_0$，这正是『显著≠有实际意义』的数理根源；因此科学报告通常还要用置信区间（confidence interval）补报效应量，而不是只给一个 p 值盖章。</span>

---

<!-- ===== PDF p507 ===== -->

<span style="color:#c0392b;">**第 9 章　经典（频率派）统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">本页（书页 500，页眉 Chap. 9 / Sec. 9.4 一带）承接上一页，继续 §9.4 通用方法（The General Approach）的正文，用一连串例子阐明其主要思想。页首过渡句承接上页叙述，随后本页另起两个新例（非续讲；Example 9.15 已在上一页完结）：**Example 9.16**（Is the Mean of a Normal Equal to Zero? 正态均值是否为零？）与在其后起头的 **Example 9.17**（Are the Means of Two Populations Equal? 两个总体均值是否相等？），后者在页末续至下一页。</span>

---

由几个例子来阐明主要思想。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.16　正态均值是否为零？（Is the Mean of a Normal Equal to Zero?）**</span>

这里我们假设每个 $X_i$ 都是独立的正态随机变量，其均值为 $\theta$、方差 $\sigma^2$ 已知。所考虑的假设为

```math
H_0 :\ \theta = 0, \qquad H_1 :\ \theta \neq 0 .
```

> <span style="color:#7f8c8d;">[OCR 损坏] 页首短语源 OCR 显示为 `with mean 0`，但由 $H_0:\theta=0$ 的设定、统计量 $S$ 的构造与后文单侧假设 $H_1:\theta>0$ 可见，此处实为「均值 $\theta$（未知）」，方差写成 `0' 2` 即 $\sigma^2$。按原文 $\theta$ 语义还原，未改动任何数值。</span>

此处一个合理的统计量（statistic）是样本均值（sample mean）$(X_1 + \cdots + X_n)/n$，或其缩放（scaled）形式

```math
S = \frac{X_1 + \cdots + X_n}{\sigma \sqrt{n}}\, .
```

> <span style="color:#1e8449;">**[t_note]** 注：『样本均值做统计量 + 双侧 $|S|>\gamma$ 作拒绝域』看似顺手，实则是被 $\theta$ 位置的对称性锁定的唯一合理解。先证：$S=\frac{\sum X_i}{\sigma\sqrt n}$ 除以 $\sigma/\sqrt n$ 正是把样本均值标准化——在 $H_0:\theta=0$ 下 $S\sim$ 标准正态；而 $H_1:\theta\ne0$ 分属两侧，$\theta>0$ 使 $S$ 偏正、$\theta<0$ 使 $S$ 偏负，故拒绝域必须左右各留一尾才能对两种偏离都敏感，这就是三角形态 $|S|>\gamma$ 而非单向 $S>\gamma$ 的原因。$\gamma$ 由 $P(|S|>\gamma)=0.05$ 反解为 1.96，是双侧 5% 临界值。直觉：既不冤枉也不放过的『样本均值离 0 多远才算异常』，刻度正是以标准误为单位的距离。</span>

拒绝域（rejection region）形状的一个自然选择是：当且仅当 $|S| > \gamma$ 时拒绝 $H_0$。由于 $S$ 服从标准正态分布（standard normal distribution），对应于任意给定的显著性水平 $\alpha$（significance level）的 $\gamma$ 值，都可以轻易地从正态表（normal tables）中查得。例如，当 $\alpha = 0.05$ 时，我们利用 $P(S \le 1.96) = 0.975$ 这一事实，得到形如「当 $|S| > 1.96$ 时拒绝 $H_0$」的拒绝域，或等价地「当 $|X_1 + \cdots + X_n| > 1.96\,\sigma\sqrt{n}$ 时拒绝 $H_0$」，即

```math
\text{reject } H_0 \ \text{if } |S| > 1.96,
\qquad
\text{or equivalently } \ \text{reject } H_0 \ \text{if } |X_1 + \cdots + X_n| > 1.96\,\sigma\sqrt{n}.
```

> <span style="color:#1e8449;">**[t_note]** 注：这里统计量选 $S=(\sum X_i)/(\sigma\sqrt n)$，即在 $H_0:\theta=0$ 下服从标准正态的那个『标准化样本均值』。先证：$E[S]=0$、$\mathrm{var}(S)=1$，$|S|>1.96$ 恰对应标准正态双侧 5% 尾部。关键在『除以 $\sigma\sqrt n$』把均值化成无量纲的 z 分数，让拒绝域在参数无关的意义下固定——无论 $\sigma$ 多大，同一条 1.96 都适用。检验量普遍写成『(估计值−假设值)/标准误』就是这个道理。顺带一提，显著性检验与置信区间在此相通：把 $(\bar X\pm1.96\,\sigma/\sqrt n)$ 视为 $1-\alpha$ 置信区间，则『$\theta_0$ 是否落于其内』与『是否拒绝 $H_0$』本质是同一判定。</span>

在本问题的单侧（one-sided）版本中，备择假设（alternative hypothesis）取形如 $H_1 : \theta > 0$。此时仍可使用同一个统计量 $S$，但我们会在 $S > \gamma$ 时拒绝 $H_0$，其中 $\gamma$ 的选择满足 $P(S > \gamma) = \alpha$。同样地，由于 $S$ 服从标准正态分布，对应于任意显著性水平 $\alpha$ 的 $\gamma$ 值都容易从正态表中查得。

最后，若方差 $\sigma^2$ 未知，我们可以用形如下式的估计（estimate）来替代它：

```math
s^2 = \frac{1}{n-1}\sum_{i=1}^{n} (X_i - \overline{X})^2,
\qquad
\overline{X} = \frac{X_1 + \cdots + X_n}{n}\, ,
```

即样本方差（sample variance），其中 $\overline{X}$ 为样本均值。

> <span style="color:#7f8c8d;">[OCR 损坏] 样本方差公式在源 OCR 中被拆成碎片（如 `Xi X I + + X`、`1 '"' s = _ ... n-l L`、`_ ____` 等），这里按原书 §9.4 的标准样本方差 $s^2 = \frac{1}{n-1}\sum_{i=1}^{n}(X_i - \overline{X})^2$ 与样本均值 $\overline{X}=(X_1+\cdots+X_n)/n$ 打磨还原，非臆造数值。</span>

在这种情况下，所得的统计量服从 $t$ 分布（$t$-distribution）（而非正态分布）。若 $n$ 相对较小，则应使用 $t$ 分布表（$t$-tables）而非正态表（cf. 第 9.1 节，Section 9.1）。

> <span style="color:#1e8449;">**[t_note]** 注：方差未知时不能再用正态表：把未知 $\sigma^2$ 换成样本方差 $s^2$ 后，$S=(\bar X-\theta)/(s/\sqrt n)$ 服从 $t$ 分布而非正态。先证：$t$ 的分母是随机量（样本标准差），其尾部比正态更『胖』，故同一 $\alpha$ 下的临界值更大——样本越小、$t$ 表与正态表差得越多；$n-1$ 的自由度来自 $s^2$ 除以 $n-1$ 的无偏修正（见 §9.1）。若 $n$ 较大，$t$ 表逼近正态表，这就是为何大样本可安心用正态近似。这条『未知方差转 $t$』的路径在习题 26、30(c) 会再次被调用。</span>

我们下一个例子涉及一个复合型原假设（composite null hypothesis）$H_0$，即存在多个与 $H_0$ 相容的参数取值。

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.17　两个总体均值是否相等？（Are the Means of Two Populations Equal?）**</span>

我们想要检验某种药物是否对两个不同的人群同等有效。我们从两个总体（populations）中各抽取独立样本 $X_1, \ldots, X_{n_1}$ 与 $Y_1, \ldots, Y_{n_2}$，其中若该药物对第一组（分别地，第二组）中的第 $i$ 个人有效，则 $X_i = 1$（或 $Y_i = 1$），否则 $X_i = 0$（或 $Y_i = 0$）。我们把每个 $X_i$（或 $Y_i$）视作均值未知的伯努利随机变量（Bernoulli random variable），其均值分别为 $\theta_x$（相应地，$\theta_y$），并考虑如下假设

```math
H_0 :\ \theta_x = \theta_y,
```

> <span style="color:#7f8c8d;">衔接下一页（PDF p508，书页 501）：Example 9.17 在本页页末起头，其 $H_0 : \theta_x = \theta_y$ 及随后的备择假设 $H_a : \theta_x \neq \theta_y$ 等处理延续至下一页。</span>

---

<!-- ===== PDF p508 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p508 − 7 = 书页 501，属 §9.4 显著性检验（Significance Testing）正文。本页无新节标题、无新 Example 入口：页首承接上一页（书页 500）同一例题——两总体均值是否相等（Are the Means of Two Populations Equal?，即 Example 9.17）的论述，在「$H_a$ 为复合假设」的说明处续起，阐述了 $H_0/H_a$ 及总体样本均值统计量的分布近似、总体共同样本均值与方差的估计，再到拒绝域（rejection region）的选取与临界值 $\gamma$ 的确定，并以一个变体假设（$H_a:\theta_x=\theta_y$）的引入翻页继续。故以「（续）」续接，不另起新编号。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页统计量符号大量被 OCR 切开误读：$\hat\theta_x$ 读作 "8x"/"3x"/"ex"，$\hat\theta_y$ 读作 "8y"/"ey"，$\theta_x,\theta_y$ 读作 "fJx,fJy"，显著性水平 $\alpha$ 读作 "Q:"，$\hat\theta$ 读作 "8"，$\hat\sigma$ 读作 "0-"/"(J'"，临界值 $\gamma$ 打印为占位符「$\gamma$」，各公式中的分式（如总体均值与方差近似式）被拆成孤立行。下文均按 §9.4 符号约定与可见上下文忠实复原，未臆造任何数值。</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.17（续）——两总体均值是否相等（Are the Means of Two Populations Equal?）**</span>

注意，存在多对与 $H_a$ 相容的配对 $(\theta_x, \theta_y)$，这使得 $H_a$ 成为一个复合假设（composite hypothesis）。

> <span style="color:#1e8449;">**[t_note]** 注：$H_a:\theta_x\ne\theta_y$ 是复合假设——有无数对 $(\theta_x,\theta_y)$ 满足它，所以根本没有『唯一的备择分布』可建直接似然比。先证：这正是上一节『通用方法』要对付的难处：$H_1$ 不是一个点而一块区域，最大似然比不可行，只好改用『分布近似已知』的统计量 $\hat\theta_x-\hat\theta_y$。因此 Example 9.17 被设计成『先估均值差、再标准化（除以估计标准误）』的骨架——这是面对复合备择时最顺手的落点。</span>

两个总体的样本均值（sample means）分别为 $\hat\theta_x$ 与 $\hat\theta_y$。

对 $\theta_x - \theta_y$ 的一个合理估计量（estimator）是 $\hat\theta_x - \hat\theta_y$。一个自然的抉择是：当且仅当某条件成立时才拒绝 $H_a$，而其中所涉的阈值 $t$ 需要依据给定的误拒概率（false rejection probability）$\alpha$ 来确定。然而，$\hat\theta_x - \hat\theta_y$ 在 $H_a$ 之下的分布依赖于未指定的参数 $\theta_x$ 与 $\theta_y$，这一事实使我们对阈值 $t$ 的恰当选取变得困难。这促使我们去考虑一个稍为不同的统计量，详见下文。

对于较大的 $n_1$ 与 $n_2$，样本均值 $\hat\theta_x$ 与 $\hat\theta_y$ 近似服从正态分布；由于它们相互独立，$\hat\theta_x - \hat\theta_y$ 也近似服从正态分布，其均值为 $\theta_x - \theta_y$，方差为

```math
\mathrm{var}(\hat\theta_x - \hat\theta_y) = \mathrm{var}(\hat\theta_x) + \mathrm{var}(\hat\theta_y)
= \frac{\theta_x (1 - \theta_x)}{n_1} + \frac{\theta_y (1 - \theta_y)}{n_2}.
```

> <span style="color:#1e8449;">**[t_note]** 注：两个独立样本均值之差的方差为何是两者之和？因为 $\hat\theta_x$、$\hat\theta_y$ 取自不同总体、相互独立，协方差为零，$\mathrm{var}(\hat\theta_x-\hat\theta_y)=\mathrm{var}(\hat\theta_x)+\mathrm{var}(\hat\theta_y)$（方差和公式，见第 2 章），其中 $\mathrm{var}(\hat\theta_x)=\theta_x(1-\theta_x)/n_1$ 是伯努利样本均值的方差。先证：『减号不减方差、反而相加』是常驻反直觉——只要两个量的波动不相关，它们的差只会比任一方波动更大。这点在后面 Problem 27 的同类计算里会再次用到。</span>

在假设 $H_a$ 之下，$\hat\theta_x - \hat\theta_y$ 的均值是已知的（等于零），但其方差未知，因为 $\theta_x$ 与 $\theta_y$ 的共同取值并不知晓。另一方面，在 $H_a$ 之下，$\theta_x$ 与 $\theta_y$ 的共同取值可以由总体样本均值

```math
\hat\theta = \frac{n_1 \hat\theta_x + n_2 \hat\theta_y}{n_1 + n_2}
```

来估计，于是方差 $\mathrm{var}(\hat\theta_x - \hat\theta_y) = \mathrm{var}(\hat\theta_x) + \mathrm{var}(\hat\theta_y)$ 可用

```math
\hat\sigma^2 = \Big(\frac{1}{n_1} + \frac{1}{n_2}\Big)\, \hat\theta (1 - \hat\theta)
```

> <span style="color:#1e8449;">**[t_note]** 注：坏消息是 $\mathrm{var}(\hat\theta_x-\hat\theta_y)$ 依赖未知的 $\theta_x,\theta_y$；好消息是 $H_a$ 只断言 $\theta_x=\theta_y$，其共性可用总体样本均值 $\hat\theta$ 估计，于是代入（plug-in）$\hat\sigma^2=(1/n_1+1/n_2)\hat\theta(1-\hat\theta)$，让 $(\hat\theta_x-\hat\theta_y)/\hat\sigma$ 近似标准正态。先证：这把『方差依赖未知参数』的难题转成『近似正态、且所有与 $H_a$ 相容的参数分布大体一致』的统计量——正合 §9.4 开头『近似分布已知且与原假设相容参数无关』的理想。跨课程（参数估计/凸优化）：『先把未知量估出来再代进去』是贯穿全章（含下一节卡方检验）的 plug-in 方法主线。</span>

来近似，而 $(\hat\theta_x - \hat\theta_y)/\hat\sigma$ 近似为一标准正态随机变量。这引导我们考虑如下形式的拒绝域（rejection region）

```math
\left|\frac{\hat\theta_x - \hat\theta_y}{\hat\sigma}\right| > \gamma ,
```

并选取 $\gamma$ 使得 $\Phi(\gamma) = 1 - \alpha/2$，其中 $\Phi$ 为标准正态 CDF（cumulative distribution function，累积分布函数）。例如，若 $\alpha = 0.05$，我们便得到如下形式的拒绝域

```math
\left|\frac{\hat\theta_x - \hat\theta_y}{\hat\sigma}\right| > 1.96 .
```

> <span style="color:#1e8449;">**[t_note]** 注：落到 $1.96$ 的拒绝域就是一句直白的判据：『两个样本均值的差，若超过约两个标准误，就拒绝两总体均值相等』。先证：$\Phi(\gamma)=1-\alpha/2$、$\alpha=0.05$ 时 $\gamma=1.96$（标准正态双侧 5% 临界），把 $(\hat\theta_x-\hat\theta_y)/\hat\sigma$ 的绝对值与 1.96 比即可。这里的 $\hat\sigma$ 是 plug-in 出的估计标准误，不是真标准差——所以它只能控制渐近意义下的误拒率，样本越大致使近 $\Phi$ 越可靠。这一整条『估差 → 标准化 → 对 1.96』的流水线你在 Problem 27 会原样重走一遍。</span>

在本例方法论的一个变体中，我们可以考虑假设 $H_a : \theta_x = \theta_y$，

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 页尾这一变体假设「$H_a : \theta_x = \theta_y$」以及紧随其后散落的比拟条件在源 OCR 中被切开（原文第 76–80 行即 "$H_a :$"、"$\theta_x = \theta_y$,"），且 $=$ 与逗号后内容被截断，未能在本页 OCR 完全可辨。此处义务性保留可辨主体「$\theta_x = \theta_y$」，其余变体细节（单侧/复合假定等）按原文翻页延续，待下一页 PDF p509（书页 502）收束后再统一核实，本页不臆造补足。</span>

---

<!-- ===== PDF p509 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">本页（书页 502）承接上一页（书页 501）的 Example 9.17（两总体均值是否相等，Are the Means of Two Populations Equal?）解答收尾——继续讨论在不排除 $\sigma_x<\sigma_y$ 的可能性时的单侧（one-sided）拒绝域形式；随后本页另起新子节「Generalized Likelihood Ratio and Goodness of Fit Tests（广义似然比与拟合优度检验）」，引入拟合优度（goodness of fit）检验的总体结构（即 Example 9.18 Is My Die Fair 的前置设定）。</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.17（续）——两总体均值是否相等（Are the Means of Two Populations Equal?）**</span>

如果我们有理由把 $\sigma_x<\sigma_y$（$\sigma_x$、$\sigma_y$ 分别为两总体标准差）的可能性排除在外，那么这个（单侧的）拒绝域（rejection region）应当是单侧的，形如

```math
\text{拒绝 } H_0 \quad\text{当且仅当}\quad \widehat{\sigma_x}-\widehat{\sigma_y}> \gamma,
```

其中 $\gamma$ 的选择应使得

```math
\Phi(\gamma) = 1-\alpha,
```

$\Phi$ 为标准正态分布的 CDF、$\alpha$ 为所设定的显著性水平（significance level）。

> <span style="color:#1e8449;">**[t_note]** 注：若事先排除 $\sigma_x<\sigma_y$ 这个方向（即采用单侧），拒绝域取为 $\hat\theta_x-\hat\theta_y>\gamma$ 且 $\Phi(\gamma)=1-\alpha$，把 $\alpha$ 全部押到一段尾端。先证：与 Example 9.15 的单侧同理——既然只关心『药物更有效』这一个方向，双侧的负侧就是把 $\alpha$ 白白分走了；改单侧后，固定 $\alpha$ 下对目标方向的检出力更强。注意单侧用 $\Phi(\gamma)=1-\alpha$（单尾），而双侧拒绝域用 $\Phi(\gamma)=1-\alpha/2$——尾巴数一变，临界值就不同，读表时极易弄混。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上面单侧拒绝域的精确形式在源 OCR 中被摔碎（如 `ex - ey > &`、`reject H0 1' f`、`where  is chosen so that <I>() = 1` 等只余碎片），此处按 Example 9.17 两总体均值比较的语义做忠实重建：拒绝当且仅当估计量之差大于由 $\Phi(\gamma)=1-\alpha$ 决定的临界值 $\gamma$。未臆造原文未出现的具体数值。</span>

前面的例子揭示了一个每当原假设（null hypothesis）为复合型（composite）时就会出现的一般性（generic）问题。为了能恰当地设定临界值（critical value），宜采用这样的统计量（statistic）：它的近似分布（approximate distribution）已知，并且对所有与原假设相容的参数取值而言分布都相同——正如 Example 9.17 中统计量 $\dfrac{\widehat{\sigma_x}-\widehat{\sigma_y}}{\sigma}$ 的情况那样。

> <span style="color:#1e8449;">**[t_note]** 注：这一段提炼出面对复合原假设的通用设计原则：所选统计量的近似分布应当『已知、且对所有与 $H_0$ 相容的参数都一样』。先证：因为临界值 $\gamma$ 是据 $H_0$ 下的分布反解的，若该分布随未定参数漂移，就不知该查表里的哪一行——Example 9.17 正是靠 plug-in 消除了这份依赖。这给出判断一个检验『能不能落地』的试金石：统计量的分布必须在 $H_0$ 下参数无关（或渐近无关）。下一节卡方检验的整个设计（自由度 $m-1$）也是为凑出这份『参数无关』。</span>

<span style="color:#2471a3;">**[subsection]**</span> <span style="color:#00838f;">**广义似然比与拟合优度检验（Generalized Likelihood Ratio and Goodness of Fit Tests）**</span>

我们的最后一个话题，涉及检验一个给定的概率质量函数（PMF）是否与观测数据相契合。这是一个重要的问题，被称为**拟合优度（goodness of fit）检验**。我们也将把它用作面对复合备择假设（composite alternative hypothesis）时进行显著性检验（significance testing）的一般方法论的引子。

> <span style="color:#1e8449;">**[t_note]** 注：把问题升维到『检验整张分布而非单个参数』，是这一节的新对象。前面几例问『$\theta$ 是否等于某数』，这里问『数据到底像不像我说好的一整套概率律』。先证：$H_0$ 仍可写成简单假设 $H_0:\theta=(\theta_1^*,\ldots,\theta_m^*)$（一个点），而 $H_1$ 是『只要不是这组概率就都算』的复合假设——退一步就是例 (iii)『是否标准正态』、例 (vi)『是否独立』。卡方检验最终给这类『形状对不对』的问题一个标准答案，这就是它被称作拟合优度检验的原因：优在于『拟合消失前的界限该划在哪』。</span>

考虑一个在有限集合 $\{1,\ldots,m\}$ 中取值的随机变量，并设 $\theta_k$ 为出现结果 $k$ 的概率。于是这个随机变量的分布（PMF）由向量参数 $\theta=(\theta_1,\ldots,\theta_m)$ 描述。我们考虑假设

```math
H_0 : \theta = (\theta_1^*, \ldots, \theta_m^*),
```

其中各 $\theta_k^*$ 是给定的非负常数，且它们的和为 $1$。我们从所关心的随机变量中抽取 $n$ 个独立样本，并记 $N_k$ 为结果为 $k$ 的样本个数。于是观测为 $X=(N_1,\ldots,N_m)$，我们用 $x=(n_1,\ldots,n_m)$ 表示其实现值。注意 $N_1+\cdots+N_m=n_1+\cdots+n_m=n$。

作为一个具体例子，考虑 $n$ 次独立的掷骰子，以及「骰子公平」的原假设 $H_0$。在这种情况下，对 $k=1,\ldots,6$ 有 $\theta_k=1/6$，而 $N_k$ 是结果为 $k$ 的掷出次数。注意备择假设 $H_1$ 是复合型的，因为它与 $\theta$ 的多种选择相容。

> <span style="color:#1e8449;">**[t_note]** 注：掷骰子一瞬间就把这套抽象框架填实：$m=6$、$\theta_k^*=1/6$、$N_k$ 是各面出现次数、$n$ 次投掷总次数。先证：$H_1$ 之所以『复合』，是因为『骰子不公平』没有唯一形状——可以是 1 面偏重、也可以 6 面全不同，无穷多种 $\theta\ne(\frac16,\ldots,\frac16)$ 都算。Neyman–Pearson 引理对简单假设给唯一最优解，在这里因 $H_1$ 开放而失效，因此必须退到『先估计再比似然』的广义 LRT。这正是你接下来要顺着往下走的动机链条，整节都围着骰子这一个例子转。</span>

我们将采用的方法称为**广义似然比检验（generalized likelihood ratio test）**，它包含两步：

（a）用极大似然（ML）估计一个模型，即确定一个在所有向量 $\theta$ 上使似然函数 $p_x(x;\theta)$ 达到最大的参数向量 $\theta=(\theta_1,\ldots,\theta_m)$。

（b）执行一次似然比检验（LRT），把原假设 $H_0$ 之下的似然 $p_x(x;\theta^*)$ 与对应于被估计模型的似然 $p_x(x;\widehat{\theta})$ 进行比较。更具体地说，构造广义似然比（generalized likelihood ratio）

```math
\frac{p_x(x;\, \widehat{\theta})}{p_x(x;\, \theta^*)},
```

即被估计模型与假设模型 $H_0$ 之下观测数据似然性的比值。

> <span style="color:#1e8449;">**[t_note]** 注：把二元 LRT 推广成『广义似然比』，本质是把分子从『固定 $H_1$ 的似然』换成『与 $H_1$ 相容的所有模型中最大的那个似然』。先证：$H_1$ 是复合假设，容纳无穷多个 $\theta$，无法指定单一备择，于是只能在可行集 $\sum_k\theta_k=1$ 上对分子做最大化（方法 (a)），再用它与 $H_0$ 下似然的比值判定 (b)。比值越大，说明『某个 $H_1$ 模型比 $H_0$ 解释样本深刻得多』。跨课程（凸优化·约束极值）：方法 (a) 就是一个有等式约束的最大化问题——你现在学的拉格朗日乘子法正是处理这类『和为一』约束的标准工具。</span>

---

<!-- ===== PDF p510 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">本页（书页 503）承接上一页（书页 502）的「广义似然比与拟合优度检验（Generalized Likelihood Ratio and Goodness of Fit Tests）」子节，继续推进其中的（b）步：对出现多项分布（multinomial）的拟合优度模型作极大似然估计，并写出广义似然比检验。页首「…且若它超过某一临界值便拒绝 $H_0$…」是对上一页方法学叙述的直接延续，故标题带「（续）」；本页没有出现新的 Example 编号。其后续页（书页 505）方引出**卡方检验（The Chi-Square Test）**。</span>

<span style="color:#2471a3;">**[subsection]**</span> <span style="color:#00838f;">**广义似然比与拟合优度检验（Generalized Likelihood Ratio and Goodness of Fit Tests）（续）**</span>

若它超过某一临界值 $\epsilon$，则拒绝原假设 $H_0$（reject $H_0$）。与二元假设检验（binary hypothesis testing）中的做法一样，我们选取这样的 $\epsilon$：使得误拒概率（false rejection probability）（近似地）等于给定的显著性水平 $\alpha$（significance level）。

本质上看，这一方法是在问如下问题：是否存在一个与备择假设 $H_1$ 相容的模型，它能给出比与 $H_0$ 对应的模型更令人满意的、对所观测数据的解释？为了回答这个问题，我们把在 $H_0$ 之下的似然，与在和 $H_1$ 相容的各个模型之下所能得到的最大似然进行比较。

第一步（极大似然估计，ML estimation）涉及在全体概率分布 $(\theta_1,\ldots,\theta_m)$ 所构成的集合上求最大化。观测向量 $X$ 的 PMF 是多项分布（multinomial，参见第 2 章习题 27），其似然函数（likelihood function）为

```math
p_X(x;\,\theta) \;=\; c\,\theta_1^{n_1}\,\theta_2^{n_2}\cdots\theta_m^{n_m},
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 原文「…the likelihood function is」之后的这一显示型公式图像在源 OCR 中被摔坏、只余一片空白，难以辨认；此处按多项分布的 PMF 与紧随其后可辨的对数似然（log-likelihood）展开式（$\log c + n_1\log\theta_1 + \cdots + n_m\log(1-\theta_1-\cdots-\theta_{m-1})$）忠实重建为 $c\,\theta_1^{n_1}\cdots\theta_m^{n_m}$（$c$ 为多项系数/归一化常数），未臆造任何原文未含的具体数值。</span>

其中 $c$ 是归一化常数（normalizing constant）。改用对数似然函数（log-likelihood function）来推导会更为方便，它的形式为

```math
\log p_X(x;\,\theta) = \log c + n_1\log\theta_1 + \cdots + n_{m-1}\log\theta_{m-1} + n_m\log(1-\theta_1-\cdots-\theta_{m-1}),
```

这里我们还用到了 $\theta_1+\cdots+\theta_m=1$ 这一事实，从而消去了 $\theta_m$。

> <span style="color:#1e8449;">**[t_note]** 注：把约束 $\theta_1+\cdots+\theta_m=1$ 代入，用意是让优化在 $m-1$ 个自由变量上进行。先证：不代入时 $\theta$ 有 $m$ 个分量却被 1 条等式约束住，真正的自由度是 $m-1$；用 $\theta_m=1-\theta_1-\cdots-\theta_{m-1}$ 消元后，只需对 $\theta_1,\ldots,\theta_{m-1}$ 求偏导并置零。这也是『自由度』在优化语境里的第一处现身——同样的 $m-1$ 数会原封不动地出现在下面卡方分布的自由度里，两条路径最终指向同一个数字。跨课程（线性代数：秩与约束）：可自由变化的坐标个数 = 变量数 − 独立约束数，正是线性无关/秩的思想。</span>

假设使对数似然达到最大的向量 $\theta$ 的各分量均为正（has positive components），则可以通过把上述表达式关于 $\theta_1,\ldots,\theta_{m-1}$ 的各偏导置零来求出它，这给出

```math
\frac{n_k}{\theta_k} \;=\; \frac{n_m}{1-\theta_1-\cdots-\theta_{m-1}},\qquad k=1,\ldots,m-1 .
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上面这个求偏导所得的方程在源 OCR 中被摔成碎片（如 `=`、`1 - 01 - . . . - Om - 1`、`for k = 1 , . . . , m - 1` 等只余残片），此处按「将对数似然对 $\theta_k$ 求导并置零」的标准推导作忠实重建，使之与紧接着可辨的「右端项等于 $n_m/\theta_m$、所有比值 $n_k/\theta_k$ 须相等」一句自洽；未加入原文未出现的数字。</span>

由于右端项等于 $n_m/\theta_m$，我们得出结论：所有比值 $n_k/\theta_k$ 必定相等。再利用 $n_1+\cdots+n_m=n$ 这一事实，可得

```math
\theta_k = \frac{n_k}{n},\qquad k=1,\ldots,m .
```

可以证明，即便某些 $n_k$ 恰好为零，这些仍然是正确的极大似然估计；此时相应的 $\theta_k$ 也为零。

> <span style="color:#1e8449;">**[t_note]** 注：结论漂亮得惊人——多项分布的 ML 估计就是样本频率 $\hat\theta_k = n_k/n$。先证：置零 $n_k/\theta_k = n_m/\theta_m$ 蕴含所有比值相等，再结合 $\sum_k\hat\theta_k=1$ 反解即得 $\hat\theta_k = n_k/n$；边界情形 $n_k=0$ 时对角 Log 取极限也一致（见页尾脚注 $0\log 0=0$）。这是『极大似然 = 相对频率』最直接的一次亮相：它说的正是『数据给出什么比例，就该信什么比例』。这句话也是后面拟合优度判据的基准线——若 $H_0$ 下的理论概率与样本频率差得远，比值就会远离 1。</span>

由此得到的广义似然比检验（generalized likelihood ratio test）具有如下形式†：当

```math
\frac{p_X(x;\,\widehat{\theta})}{p_X(x;\,\theta^*)}\;>\;\epsilon
```

时拒绝 $H_0$，其中 $\epsilon$ 是临界值（critical value）。

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上面广义似然比的显示型公式图像在源 OCR 中被摔坏、只余空白，此处按上一页（书页 502）引入的比值 $p_x(x;\widehat{\theta})/p_x(x;\theta^*)$（被估计模型与假设模型 $H_0$ 之下数据似然性之比）及紧随其后的可辨对数形式 $\sum_k n_k\log(n_k/\theta_k^*)>\log\epsilon$ 作忠实重建，未臆造原文未含的数值。</span>

† 我们约定 $0^0 = 1$ 且 $0\log 0 = 0$。

对上述检验取对数，检验便化归为：当

```math
\sum_{k=1}^{m} n_k \log\Big(\frac{n_k}{\theta_k^*}\Big) \;>\; \log\epsilon
```

时拒绝 $H_0$。

> <span style="color:#1e8449;">**[t_note]** 注：这一步把比值式换成了更可计算的对数和 $\sum_k n_k\log(n_k/\theta_k^*)$，且约定 $0\log 0=0$ 堵住 $n_k=0$ 的边界。先证：整个和式是『每个类别按样本频数加权的对数比』；若数据完全服从 $H_0$（$n_k\approx n\theta_k^*$），每项的对数都接近 0，和值自然小；一旦某些类别偏离 $H_0$ 的比例很远，对应的 $n_k/\theta_k^*$ 偏离 1，正项把和值推高，超过阈值就拒绝。跨课程（信息论 Cover·交叉熵视角）：这个和式恰是『经验分布对理论分布』的交叉熵/似然比判断，给你日后走进 KL 散度埋下伏笔——距离越大证据越强。</span>

> <span style="color:#7f8c8d;">衔接下一面（PDF p511）：本页完成多项模型下的极大似然估计与广义似然比检验的表达后，其后的页面将进一步展开拟合优度检验的具体步骤与**卡方检验（The Chi-Square Test）**（书页 505）。本页无新的 Example 编号，不属于 Example 9.14–9.18 中的任何已知例。</span>

---

<!-- ===== PDF p511 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p511 − 7 = 书页 504，属 §9.4 内部子节「广义似然比与拟合优度检验（Generalized Likelihood Ratio and Goodness of Fit Tests）」、即卡方检验（Chi-Square Test）的导出阶段。页首承接上一页（PDF p510）所引进、用于拟合优度检验的似然比统计量 $S$，本页确定对应的临界值 $\gamma$，并论证当样本量 $n$ 很大时统计量 $S$ 可用 $T/2$ 逼近、而 $T$ 近似服从自由度 $m-1$ 的 $\chi^2$ 分布；卡方检验的正式陈述（The Chi-Square Test）及 **Example 9.18** 延续到下一页（PDF p512）围成框。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页符号多处被 OCR 误读或拆成碎行：原假设 $H_0$ 读作 "Ho"、临界值 $\gamma$ 读作 ""、显著性水平 $\alpha$ 读作 "ct"、观测频数被读作 "ih"、期望频数 $n\theta_k$ 被读作 "nO．k"、$\chi^2$ 读作 "X2"。此处按本章记法（$N_k$ 为观测频数、$\theta_k$ 为原假设下的单元概率）与上下文规范复原；两处脚注（二阶 Taylor 展开、$\chi^2$ 分布与自由度）依语义补齐，非臆造数值。</span>

---

需要求临界值（critical value）$\gamma$，须把要求的显著性水平考虑进去，即要求

```math
P(S > \log\gamma;\; H_0) = \alpha,
```

其中统计量（statistic）

```math
S = \sum_{k=1}^{m} N_k \log\left(\frac{n\,\theta_k}{N_k}\right).
```

这可能会带来困难，因为 $S$ 在 $H_0$ 下的分布并非现成可得，而只能在计算机上模拟（simulate）。

> <span style="color:#1e8449;">**[t_note]** 注：『只能模拟』是个值得停一下的转折：它暴露了用 $S$ 做卡方检验的坎——$S$ 在 $H_0$ 下的精确分布没有闭式表可查。先证：只有当例外形如『简单原假设 + 正态假设』（如均值检验 $Z\sim$ 标准正态、$t$ 检验）时才有人手一张的可查分布；复合概率结构的 $S$ 得靠蒙特卡洛：反复从 $H_0$ 规定的分布抽样、每次算一个 $S$，用大量 $S$ 直方图近似其分布，再定临界值。这提醒你在现实检验里『查表』只是特权，『模拟/渐近近似』才是常态。跨课程（CSAPP/随机算法）：把『查不到解析分布』的问题交给大量模拟件 蒙特卡洛，正是你学过的随机化算法思想在统计推断里的标准出场方式。</span>

幸运的是，当 $n$ 很大时会出现重大的简化。在这种情况下，观测到的频率 $N_k/n$ 在 $H_0$ 之下会以很高的概率非常接近 $\theta_k$。此时，二阶 Taylor 级数展开（second order Taylor series expansion）表明，我们的统计量 $S$ 可以用 $T/2$ 很好地逼近，其中 $T$ 由下式给出

```math
T = \sum_{k=1}^{m} \frac{(N_k - n\theta_k)^2}{n\,\theta_k}.
```

此外，当 $n$ 很大时，已知在原假设 $H_0$ 之下，$T$ 的分布（从而 $2S$ 的分布）趋近所谓的 $\chi^2$ 分布（$\chi^2$ distribution），其自由度为 $m-1$。该分布的分布函数（CDF）与正态分布表类似，也以表的形式可查。

> <span style="color:#1e8449;">**[t_note]** 注：这是本章最重要的一个数学落地：为何统计量 $T=\sum_k\frac{(N_k-n\theta_k)^2}{n\theta_k}$ 逼近 $\chi^2_{m-1}$？先证：$N_k/n$ 依中心极限定理在各 $\theta_k$ 附近渐近正态，故标准化向量 $Z_k=(N_k-n\theta_k)/\sqrt{n\theta_k}$ 近似独立标准正态，$T=\sum_k Z_k^2$ 像是一串独立标准正态平方和。但自由度不是 $m$ 而是 $m-1$，因为 $\sum_k(N_k-n\theta_k)=N_1+\cdots+N_m-n=0$ 对 $Z_k$ 施加了一个线性约束——平方和里只剩 $m-1$ 个确实自由的方向，这也与本节前面『参数建模只剩 $m-1$ 个自由度』遥相呼应。跨课程（线性代数：由约束减维）：两处 $m-1$ 同源，都归结为『$\sum$ 条件砍掉一个方向』。</span>

> <span style="color:#7f8c8d;">[脚注 t &#8226; 二阶 Taylor 展开] 我们注意到，函数 $y\log(y^*/y)$ 在任意 $y^*>0$ 附近的二阶 Taylor 级数展开具有如下形式

> ```math
> y\log\frac{y^*}{y} \;\approx\; (y^* - y) + \frac{(y - y^*)^2}{2\,y^*} + \cdots,
> ```

> 且当 $y/y^*$ 接近 $1$ 时该展开是有效的。由此即得 $2S \approx T$。</span>

> <span style="color:#7f8c8d;">[脚注 &#8226; $\chi^2$ 分布的定义与自由度] 具有 $f$ 个自由度的 $\chi^2$ 分布，定义为如下随机变量

> ```math
> Z_1^2 + Z_2^2 + \cdots + Z_f^2,
> ```

> 的分布，其中 $Z_1,\ldots,Z_f$ 是相互独立的标准正态随机变量（零均值、单位方差）。关于 $T$ 为何近似服从 $\chi^2$，可借由这样的事实获得一些直观理解：随着 $n\to\infty$，$N_k/n$ 不仅收敛到 $\theta_k$，而且渐近正态。于是 $T$ 等于一系列零均值正态随机变量的平方和，即 $(N_k - n\theta_k)/\sqrt{n\theta_k}$。$T$ 之所以有 $m-1$ 而不是 $m$ 个自由度，与 $\sum_{k=1}^{m}(N_k - n\theta_k) = 0$ 这一事实有关——这就意味着这些随机变量实际上是相互依赖的。</span>

---

<!-- ===== PDF p512 ===== -->

<span style="color:#c0392b;">**§9.4　显著性检验（Significance Testing）（续）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p512 − 7 = 书页 505，仍属 §9.4 子节「广义似然比与拟合优度检验 → The Chi-Square Test（卡方检验）」。页首承接上一页（PDF p511）的 $\chi^2$ 逼近讨论，随即给出卡方检验的正式程序框（The Chi-Square Test），然后引出本子节的例题 **Example 9.18（Is My Die Fair?）**，其演算延续到下一页（PDF p513）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 符号多处被 OCR 误读或拆碎：$\chi^2$ 读作 "X2"、临界值 $\gamma$ 读作 ""、显著性水平 $\alpha$ 读作 "Q"/"a"/"ct"、频数读数（$n_1=92,n_2=120,n_3=88,n_4=98,n_5=95,n_6=107$）与统计量 $T$ 的求和式被拆成大量碎行。$T$ 的名项数值 $(92-100)^2/100+(120-100)^2/100+\cdots+(107-100)^2/100 = 6.86$、临界 $t=11.1$（与规范核对锚点 $t=11.1$、$T=6.86$ 一致）均保持原样，未作改动。</span>

---

于是，从 $\chi^2$ 分布表中可以查到 $P(T > \gamma;\; H_0)$ 或 $P(2S > \gamma;\; H_0)$ 近似正确的取值，并用它来确定与给定显著性水平 $\alpha$ 相对应的合适临界值。把各方面综合起来，对于大的 $n$ 值，我们得到如下的检验。

<span style="color:#00838f;">**[定义块] 卡方检验（The Chi-Square Test）**</span>

- **统计量**：使用统计量 $2S$（或者使用相关的统计量 $T$），并采用如下形式的拒绝域（rejection region）：

```math
\text{拒绝 } H_0 \quad\text{if}\quad 2S > \gamma \quad\text{（相应地 } T > \gamma\text{）}.
```

- **临界值**：临界值 $\gamma$ 由具有 $m-1$ 个自由度的 $\chi^2$ 分布的 CDF 表确定，使得

```math
P(2S > \gamma;\; H_0) = \alpha,
```

其中 $\alpha$ 是给定的显著性水平。

> <span style="color:#1e8449;">**[t_note]** 注：注意卡方检验对频数有硬性要求——每个期望频数 $n\theta_k$ 不能太小（经验上常要求 $\ge 5$，至少不能为 0）。先证：因为 $\chi^2$ 逼近依赖『$N_k/n$ 落到 $\theta_k$ 附近才可作正态/平方和近似』，若某类期望频数近乎 0，$N_k$ 的离差放缩 $(N_k-n\theta_k)/\sqrt{n\theta_k}$ 就失效，整套 Taylor 展开崩塌。这也是为什么实际做拟合优度时往往先合并太小的类别再检验。选 $T$ 还是 $2S$ 只是等价尺度，判断『拒绝/不拒绝』结论一致，可选用好查表的那个。</span>

---

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.18（我的骰子是公平的吗？Is My Die Fair?）**</span>

一枚骰子被独立地掷了 $600$ 次，数字 $1,2,3,4,5,6$ 各出现的次数分别为

```math
n_1 = 92,\quad n_2 = 120,\quad n_3 = 88,\quad n_4 = 98,\quad n_5 = 95,\quad n_6 = 107.
```

我们用基于统计量 $T$ 的卡方检验，在显著性水平 $\alpha = 0.05$ 下检验“骰子是公平的”这一原假设 $H_0$。由具有 $5$ 个自由度的 $\chi^2$ 分布表可得，要满足 $P(T > t;\; H_0) = 0.05$，必须取 $t = 11.1$。

取 $\theta_1 = \cdots = \theta_6 = 1/6$、$n = 600$，于是 $n\theta_i = 100$；结合给定的频数 $n_k$，统计量 $T$ 的取值是

```math
\begin{aligned}
T &= \sum_{k=1}^{6}\frac{(n_k - n\theta_k)^2}{n\theta_k} \\
  &= \frac{(92-100)^2}{100} + \frac{(120-100)^2}{100} + \frac{(98-100)^2}{100} \\
  &\quad + \frac{(88-100)^2}{100} + \frac{(95-100)^2}{100} + \frac{(107-100)^2}{100} \\
  &= 6.86.
\end{aligned}
```

由于 $T = 6.86 < 11.1$，因此“骰子是公平的”这一假设未被拒绝（not rejected）。如果改而使用统计量 $2S$，那么利用数据的计算会得到 $2S = 6.68$，它既接近 $T$，也远低于临界值 $\gamma = 11.1$（本句的展开延续到下一页 PDF p513）。

> <span style="color:#1e8449;">**[t_note]** 注：把这道题的『没拒绝』拆开看最见功力。先证：$T=6.86$ 是把每一面『实际频数 与 期望频数 100』的偏差平方、拉回期望刻度再求和——若骰子公平，这个和应当『不太大』；(b) 中因 $\sum_k(n_k-100)=0$（六面的偏差合计自然抵消），落在 $T$ 里只剩 $m-1=5$ 个自由方向，故阈值取 $df=5$ 行。6.86 落在 5 自由度 $\chi^2$ 表的中段（远低于 11.1），说明六面的偏差幅度与『随机涨落』相当，找不到系统性偏置证据——注意『不拒绝』≠『证明公平』，样本不足时任何微小偏置都可能藏得过 100 次期望的噪声。这是『证据不足，维持原判』的准审判视角。</span>

---

<!-- ===== PDF p513 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#2471a3;">**[example]**</span> <span style="color:#2471a3;">**Example 9.18（续）（Is My Die Fair? 我的骰子是公平的吗？）**</span>

> <span style="color:#7f8c8d;">[原页 OCR 轻微碎裂] 读者注意：本例（Example 9.18）演算延续上一页 PDF p512 而来。本页 OCR 中临界值 $\gamma$ 被读作 ""、显著性水平 $\alpha$ 读作 "a"。数值 $T=6.86$、$2S=6.68$、$\gamma=11.1$、$\gamma=6.63$ 均与规范核对锚点一致，未改动。</span>

……既接近 $T$，也远低于临界值 $\gamma = 11.1$。如果显著性水平取为 $\alpha = 0.25$，那么与之对应的 $\gamma$ 值将为 $6.63$。在这种情况下，由于 $T = 6.86 > 6.63$ 且 $2S = 6.68 > 6.63$，“骰子是公平的”这一假设就会被拒绝。

> <span style="color:#1e8449;">**[t_note]** 注：这个收尾把前面的教训再次拉回台前：同一组骰子数据，$\alpha=0.05$ 时『不拒绝』，$\alpha=0.25$ 时『拒绝』——数据没变，变的是判决门槛。先证：$\alpha$ 越大，$\chi^2_5$ 分布表里被划进拒绝域的尾越大，临界值 $\gamma$ 越小（11.1→6.63），越过门槛就越容易。这绝不是说『挑一个 $\alpha$ 让结论好看』，而是提醒：显著性检验的结论永远附着于研究者预设的 $\alpha$，读结果必须先看清门槛设在哪一档。同一批数据可被不同 $\alpha$ 翻案，正因此『报告 p 值 + 效应量』才比单给一个结论更诚实。</span>

---

<span style="color:#c0392b;">**§9.5　小结与讨论（Summary and Discussion）**</span>

经典（频率派）推断方法（classical inference methods）与贝叶斯方法（Bayesian methods）形成对照，前者把 $\theta$ 视为一个未知常数。经典参数估计以具有良好性质的估计量为目标，例如对所有可能的 $\theta$ 值都具有较小的偏（bias）以及令人满意的置信区间（confidence interval）。

> <span style="color:#1e8449;">**[t_note]** 注：这一句把全书最后一张图景铺开——经典 vs 贝叶斯的根本分歧在『$\theta$ 算不算随机量』。先证：经典派把 $\theta$ 当作固定但未知的常量，一切性质（偏、方差、置信区间）都要『对所有可能 $\theta$ 都成立』，故强调无偏性和一致性；而贝叶斯派把 $\theta$ 视为有先验分布的随机量，求的是包含先验的后验。你第 8 章已见过两者，这里双向对照正好帮你把参数估计、MAP/ML、置信区间这几条线收口成一张表。跨课程（CSAPP·绝不裸断言）：『对所有 $\theta$ 成立』正是你欣赏的那种不依赖具体假设的稳健论证风格。</span>

我们首先聚焦于极大似然（ML）估计，它与（贝叶斯的）最大后验（MAP）方法相关，选取的是在给定 $x$ 时使似然函数（likelihood function）最大的 $\theta$ 的估计。它是一种通用的估计方法，并具有若干令人满意的特性，尤其是在观测数目很大时。随后，我们讨论了估计未知均值并构造置信区间这一特殊但实践上重要的情形，此处的方法在很大程度上依赖于中心极限定理（central limit theorem）。最后我们讨论了线性回归（linear regression）方法，其目标是在最小二乘（least squares）意义下让一个线性模型与观测数据相匹配。该方法的应用无需概率假设，但在某些条件下也与 ML 及贝叶斯最小均方（Bayesian LMS）估计相关。

经典假设检验方法的目标是较小的错误概率，同时兼顾计算的简便与方便。我们重点考察了当观测落入某类简单形状的拒绝域时拒绝原假设的检验。似然比检验（likelihood ratio test）是处理两个相互竞争的简单假设（simple hypotheses）情形的主要方法，并从内曼–皮尔逊引理（Neyman-Pearson Lemma）获得强有力的理论支持。我们还讨论了显著性检验（significance testing），它适用于一个（或两个）竞争假设是复合假设（composite hypothesis）的情形。此处的主要方法涉及一个经恰当选取、用以概括观测的统计量，以及一个在原假设之下概率被设定为所需显著性水平的拒绝域。

> <span style="color:#1e8449;">**[t_note]** 注：这一节把全书第 9 章两条主线对齐收口——参数估计（找点 + 置信区间）与假设检验（判 $H_0$ 是否被拒）是同一套频率派思维的两面。先证：把『$\theta$ 落进置信区间』看成『接受 $H_0:\theta=_0$』，两者共享同一个统计量与临界值（如双侧 $\pm1.96$ 标准误），互相翻译毫不费力。这份回顾还点出主线分工：估计靠 CLT 转正态，检验靠 LRT/NP 引理定最优与库边界，显著性检验则补上复合假设这块拼图。跨课程（6.006·双面数据结构）：同一统计量在『估计/检验』两个视角下复用，正如一个数据结构既服务插入也服务查询——概念复利而非重复劳动。</span>

在我们对统计学的这个简短导论中，我们旨在说明核心概念与最常用的方法论，但对于一个内容极为丰富的学科而言，我们仅仅触及了皮毛。例如，我们没有讨论诸如时变环境下的估计（时间序列分析与滤波）、非参数估计（nonparametric estimation，例如基于经验数据估计未知 PDF 的问题）、线性与非线性回归的进一步发展（例如检验回归模型背后的假设是否成立）、统计试验的设计方法、统计研究结论的验证方法、计算方法等许多重要论题。然而，我们希望已激起读者对这一学科的兴趣，并对其概念框架提供某种一般性的理解。

> <span style="color:#1e8449;">**[t_note]** 注：这段自述『只触及皮毛』正是给学习者划定子学科版图：非参数估计（不假设分布族）、设计实验（DOE）、时间序列——都是这一章方法的自然延伸而非新世界观。先证：本书主线是『给一个含未知参数的模型，用观测做估计与检验』，凡能落入此框架的都覆盖了，凡需要『脱离模型/动态模型』的都留白。就方法学而言，这一章是全书从概率（描述）走向统计（归纳）的收束点，而你接下来要学的凸优化、信息论会反复回看这里的似然与检验结构。跨课程（实分析·学科视角）：『哪种解释更可信』的拟合优度判断，是科学方法论在数学里最标准的一次落地。</span>

---

<!-- ===== PDF p514 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p514 − 7 = 书页 507。第 9 章习题区（Problems）自此开始，本页起自 **Problem 1**，不承接任何单元前编号（单元 10 未翻第 9 章习题）。习题题干保持英文原题，不翻译。本页为 **SECTION 9.1 Classical Parameter Estimation** 分区，含 Problem 1、2、3（至 (b)）；Problem 3 的 (c) 延续到下一页。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 部分符号被拆碎：参数 $\theta$ 读作 "O"、未知白球数读作 "k"、白球总数读作 "k"、样本均值权重被拆碎。习题题干含混处（如 $k$ 与 $\bar{k}$、$\bar{S}$ 与 $\hat{S}$）依题意规范复原；数值（10,14,18,8,20 小时；误差方差比式）保持原样。</span>

---

<span style="color:#00838f;">**PROBLEMS（第 9 章习题）**</span>

<span style="color:#00838f;">**[定义块] SECTION 9.1 · Classical Parameter Estimation（经典参数估计）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 1.**</span> Alice models the time that she spends each week on homework as an exponentially distributed random variable with unknown parameter $\theta$. Homework times in different weeks are independent. After spending 10, 14, 18, 8, and 20 hours in the first 5 weeks of the semester, what is her ML estimate of $\theta$?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 2.**</span> Consider a sequence of independent coin tosses, and let $p$ be the probability of heads at each toss.

(a) Fix some $k$ and let $N$ be the number of tosses until the $k$th head occurs. Find the ML estimator of $p$ based on $N$.

(b) Fix some $n$ and let $K$ be the number of heads observed in $n$ tosses. Find the ML estimator of $p$ based on $K$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 3. Sampling and estimation of sums.**</span> We have a box with $k$ balls; $\bar{k}$ of them are white and $k-\bar{k}$ are red. Both $k$ and $\bar{k}$ are assumed known. Each white ball has a nonzero number on it, and each red ball has zero on it. We want to calculate the sum of all the ball numbers, but because $k$ is very large, we resort to estimating it by sampling. This problem aims to quantify the advantages of sampling only white balls / nonzero numbers and exploiting the knowledge of $\bar{k}$. In particular, we wish to compare the error variance when we sample $n$ balls with the error variance when we sample a smaller number $m$ of white balls.

(a) Suppose we draw balls sequentially and independently, according to a uniform distribution (with replacement). Denote by $X_i$ the number on the $i$th ball drawn, and by $Y_i$ the number on the $i$th white ball drawn. We fix two positive integers $n$ and $m$, and denote

```math
\hat{S} = \frac{k}{N}\sum_{i=1}^{n} X_i, \qquad \tilde{S} = \frac{k}{m}\sum_{i=1}^{m} Y_i,
```

where $N$ is the (random) number of white balls drawn in the first $n$ samples. Show that $\hat{S}$, $\tilde{S}$, and $S$ are unbiased estimators of the sum of all the ball numbers.

(b) Calculate the variances of $S$ and $\hat{S}$, and show that in order for them to be approximately equal, we must have

```math
\frac{m}{n} \approx \frac{p}{p + r(1-p)},
```

where $p = \bar{k}/k$ and $r = E[Y_1^{2}]/\mathrm{var}(Y_1)$. Show also that when $m = n$,

```math
\frac{\mathrm{var}(\hat{S})}{\mathrm{var}(S)} = \frac{p}{\,p + r(1-p)\,}.
```

---

<!-- ===== PDF p515 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p515 − 7 = 书页 508，为 SECTION 9.1 习题区。承接上一页（PDF p514）的 Problem 3(c)，随后 Problem 4 起（Mixture models）、Problem 5、Problem 6（至数据列表）。习题题干保持英文原题。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 部分符号被拆碎：均方差 $\sigma_j^2$ 读作 "o}"、均值 $\mu_j$ 读作 "J-lJ"/"1-LJ"、观测频数读作 "Li.d."、"L~l"。Problem 4(c) 中"假设 $p_1$ 与 $p_2$ 已知、求 $\mu_1,\mu_2$ 的 ML 估计"等在原文中如此（此处按原文信息复原）。身高数据（164,167,163,158,170,183,176,159,170,167 cm）保持原样。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 3.（续）(c)**</span> Calculate the variance of $\tilde{S}$, and show that for large $n$,

```math
\frac{\mathrm{var}(S)}{\mathrm{var}(\tilde{S})} \approx \frac{p}{\,p + r(1-p)\,}.
```

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 4. Mixture models（混合模型）.**</span> Let the PDF of a random variable $X$ be the mixture of $m$ components:

```math
f_X(x) = \sum_{j=1}^{m} p_j f_{Y_j}(x),
```

where

```math
p_j \ge 0, \quad \text{for } j = 1, \ldots, m.
```

Thus, $X$ can be viewed as being generated by a two-step process: first draw $j$ randomly according to probabilities $p_j$, then draw randomly according to the distribution of $Y_j$. Assume that each $Y_j$ is normal with mean $\mu_j$ and variance $\sigma_j^{2}$, and that we have a set of i.i.d. observations $X_1,\ldots,X_n$, each with PDF $f_X$.

(a) Write down the likelihood and log-likelihood functions.

(b) Consider the case $m=2$ and $n=1$, and assume that $\mu_1$, $\mu_2$, $\sigma_1$, and $\sigma_2$ are known. Find the ML estimates of $p_1$ and $p_2$.

(c) Consider the case $m=2$ and $n=1$, and assume that $p_1$, $p_2$, $\sigma_1$, and $\sigma_2$ are known. Find the ML estimates of $\mu_1$ and $\mu_2$.

(d) Consider the case $m \ge 2$ and general $n$, and assume that all parameters are unknown. Show that the likelihood function can be made arbitrarily large by choosing $\mu_1 = X_1$ and letting $\sigma_1^{2}$ decrease to zero. Note: This is an example where the ML approach is problematic.

> <span style="color:#1e8449;">**[t_note]** 注：(d) 是一记经典的『ML 爆炸反例』：把 $\mu_1$ 对准某个观测 $X_1$、再把 $\sigma_1^2\to 0$，那一项正态密度的峰值趋于无穷，似然可以无限涨大——ML 反而挑出最荒谬的『退化模型』。先证：极限处 $\sigma_1\to0$ 使该分量变成集中在 $X_1$ 的尖峰，该密度在 $X_1$ 处以 $1/(\sigma_1\sqrt{2\pi})$ 的量级趋无穷，整个似然无上界，所谓最大化无定义。这说明 ML 不是万灵药，遇到非正则参数（方差可趋 0、边界参数）就会失真，临床上常要加正则化或 penalized 项约束。跨课程（凸优化·正则化）：这正是后来 ridge/lasso 惩罚项的动机——用约束驯服 ML 在病态点上的贪心。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 5.**</span> Unstable particles are emitted from a source and decay at a distance $X$, which is exponentially distributed with unknown parameter $\theta$. A special device is used to detect the first $n$ decay events that occur in the interval $[m_1, m_2]$. Suppose that these events are recorded at distances $X = (X_1, \ldots, X_n)$.

(a) Give the form of the likelihood and log-likelihood functions.

(b) Assume that $m_1 = 1$, $m_2 = 20$, $n = 6$, and $x = (1.5, 2, 3, 4, 5, 12)$. Plot the likelihood and log-likelihood as functions of $\theta$. Find approximately the ML estimate of $\theta$ based on your plot.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 6.**</span> Consider a study of student heights in a middle school. Assume that the height of a female student is normally distributed with mean $\mu_1$ and variance $\sigma_1^{2}$, and that the height of a male student is normally distributed with mean $\mu_2$ and variance $\sigma_2^{2}$. Assume that a student is equally likely to be male or female. A sample of size $n = 10$ was collected, and the following values were recorded (in centimeters):

```math
164,\; 167,\; 163,\; 158,\; 170,\; 183,\; 176,\; 159,\; 170,\; 167.
```

---

<!-- ===== PDF p516 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p516 − 7 = 书页 509，为 SECTION 9.1 习题区。承接上一页（PDF p515）Problem 6 之后为 Problem 6(a)–(d)、Problem 7、8、9、10、11（*）。Problem 11 为带 * 题，其定义与 (a)（至充分统计量条件概率式）由此页引出并延续到下一页。习题题干保持英文原题。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 部分符号被拆碎或误读：均值 $\mu_j$ 读作 "lJ.j"/"IL l"、方差 $\sigma_j^2$ 读作 "0'"/"0'1"、参数 $\theta$ 读作 "9"/"O"、$\xi \theta$ 归一化因子读作 "c(9)"、函数 $q(X)$ 读作 "q( )"。Problem 10 中 PMF 的具体形式在源 OCR 处残缺，按题意（归一化因子 $c(\theta)$）依上下文复原。Problem 10(b) 的归一化因子 $c(\theta)$ 的解析表达未在本页出现，故只述其性质，不臆造公式。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 6.（续）(a)**</span> Assume that $\mu_1$, $\mu_2$, $\sigma_1$, and $\sigma_2$ are unknown. Write down the likelihood function.

(b) Assume we know that $\sigma_1^{2} = 9$ and $\mu_1 = 164$. Find numerically the ML estimates of $\sigma_2$ and $\mu_2$.

(c) Assume we know that $\sigma_1^{2} = \sigma_2^{2} = 9$. Find numerically the ML estimates of $\mu_1$ and $\mu_2$.

(d) Treating the estimates obtained in part (c) as exact values, describe the MAP rule for deciding a student's gender based on the student's height.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 7. Estimating the parameter of a Poisson random variable.**</span> Derive the ML estimator of the parameter of a Poisson random variable based on i.i.d. observations $X_1,\ldots,X_n$. Is the estimator unbiased and consistent?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 8. Estimating the parameter of a uniform random variable I.**</span> We are given i.i.d. observations $X_1,\ldots,X_n$ that are uniformly distributed over the interval $[0, \theta]$. What is the ML estimator of $\theta$? Is it consistent? Is it unbiased or asymptotically unbiased? Can you construct alternative estimators that are unbiased?

> <span style="color:#1e8449;">**[t_note]** 注：$U[0,\theta]$ 下 ML 估计量是 $\hat\theta=\max_i X_i$——用『最大观测值』而非『间距』，这与正态/泊松里『样本均值』完全不同。先证：似然 $1/\theta^n$ 只在 $\theta\ge\max_i X_i$ 时非零，且随 $\theta$ 递减，故最优解落在可行边界 $\theta=\max_i X_i$ 处（非正则边界估计）。它相合但**有偏**（总有 $\hat\theta<\theta$ 几乎必然）；可构造 $2\bar X$ 这样的无偏替代。这条『ML 取到边界、故有偏』的教训在 Problem 15 与 Rao–Blackwell 里会反复回来，值得记牢。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 9. Estimating the parameter of a uniform random variable II.**</span> We are given i.i.d. observations $X_1,\ldots,X_n$ that are uniformly distributed over the interval $[\theta, \theta+1]$. Find a ML estimator of $\theta$. Is it consistent? Is it unbiased or asymptotically unbiased?

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 10.**</span> A source emits a random number of photons $K$ each time that it is triggered. We assume that the PMF of $K$ is

```math
p_K(k;\theta) = \theta^{k}\,c(\theta), \qquad k = 0, 1, 2, \ldots,
```

where $\theta$ is the inverse of the temperature of the source and $c(\theta)$ is a normalization factor. We also assume that the photon emissions each time that the source is triggered are independent. We want to estimate the temperature of the source by triggering it repeatedly and counting the number of emitted photons.

(a) Determine the normalization factor $c(\theta)$.

(b) Find the expected value and the variance of the number $K$ of photons emitted if the source is triggered once.

(c) Derive the ML estimator for the temperature $\psi = 1/\theta$, based on $K_1, \ldots, K_n$, the numbers of photons emitted when the source is triggered $n$ times.

(d) Show that the ML estimator is consistent.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 11.\* Sufficient statistics – factorization criterion.**</span> Consider an observation model of the following type. Assuming for simplicity that all random variables are discrete, an initial observation $T$ is generated according to a PMF $p_T(t;\theta)$. Having observed $T$, an additional observation $Y$ is generated according to a conditional PMF $p_{Y|T}(y\,|\,t)$ that does not involve the unknown parameter $\theta$. Intuition suggests that out of the overall observation vector $X = (T, Y)$, only $T$ is useful for estimating $\theta$. This problem formalizes this idea.

Given observations $X = (X_1, \ldots, X_n)$, we say that a (scalar or vector) function $q(X)$ is a sufficient statistic for the parameter $\theta$ if the conditional distribution of $X$ given the random variable $T = q(X)$ does not depend on $\theta$, i.e., for every event $D$ and possible value $t$ of the random variable $T$,

```math
P_{\theta}\bigl(X \in D \,\big|\, T = t\bigr)
```

is the same for all $\theta$ for which the above conditional probability is well-defined [i.e., for all $\theta$ for which the PMF $p_T(t;\theta)$ or the PDF $f_T(t;\theta)$ is positive]. Assume that either $X$ is discrete (in which case, $T$ is also discrete), or that both $X$ and $T$ are continuous random variables.

---

<!-- ===== PDF p517 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p517 − 7 = 书页 510，为 SECTION 9.1 习题区，承接上一页（PDF p516）Problem 11 的 (a)（(a) 的求解延续至下一页 PDF p518）。本页主体为 Problem 11 的 (a)(b)(c)，其中带 * 题的英文 Solution 依规范保留，仅作标签说明。习题与解答题干保持英文。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 参数 $\theta$ 多被读作 "O"/"0"、充分统计量 $T=q(X)$ 与条件分布式被拆成大量碎行，$s(x)$、$r(q(x),\theta)$ 等可依 Factor jor 推导复原。数值无整数需更正；解析式按下方标准推导规范复原，不臆造。</span>

---

*…given the random variable $T = q(X)$ does not depend on $\theta$, i.e., for every event $D$ and possible value $t$ of the random variable $T$,*

```math
P_{\theta}\bigl(X \in D \,\big|\, T = t\bigr)
```

*is the same for all $\theta$ for which the above conditional probability is well-defined [i.e., for all $\theta$ for which the PMF $p_T(t;\theta)$ or the PDF $f_T(t;\theta)$ is positive]. Assume that either $X$ is discrete (in which case, $T$ is also discrete), or that both $X$ and $T$ are continuous random variables.*

(a) Show that $T = q(X)$ is a sufficient statistic for $\theta$ if and only if it satisfies the following factorization criterion: the likelihood function $p_X(x;\theta)$ (discrete case) or $f_X(x;\theta)$ (continuous case) can be written as $r(q(x), \theta)\,s(x)$ for some functions $r$ and $s$.

(b) Show that if $q(X)$ is a sufficient statistic for $\theta$, then for any function $h$ of $\theta$, $q(X)$ is a sufficient statistic for the parameter $\zeta = h(\theta)$.

(c) Show that if $q(X)$ is a sufficient statistic for $\theta$, a ML estimate of $\theta$ can be written as $\widehat{\theta} = \phi\bigl(q(X)\bigr)$ for some function $\phi$. *Note:* This supports the idea that a sufficient statistic captures all essential information about $\theta$ provided by $X$.

<span style="color:#2471a3;">**Solution（解答）。**</span> (a) We consider only the discrete case; the proof for the continuous case is similar. Assume that the likelihood function can be written as $r\bigl(q(x),\theta\bigr)s(x)$. We will show that $T = q(X)$ is a sufficient statistic.

Fix some $t$ and consider some $\theta$ for which $P_{\theta}(T = t) > 0$. For any $x$ for which $q(x) \neq t$, we have $P_{\theta}(X = x \mid T = t) = 0$, which is trivially the same for all $\theta$. Consider now any $x$ for which $q(x) = t$. Using the fact $P_{\theta}(X = x,\, T = t) = P_{\theta}\bigl(X = x,\, q(X) = q(x)\bigr) = P_{\theta}(X = x)$, we have

```math
\begin{aligned}
P_{\theta}\bigl(X = x \mid T = t\bigr)
&= \frac{P_{\theta}(X = x,\, T = t)}{P_{\theta}(T = t)}
 = \frac{P_{\theta}(X = x)}{P_{\theta}(T = t)} \\
&= \frac{r\bigl(t,\theta\bigr)s(x)}{\displaystyle\sum_{\{z \,:\, q(z) = t\}} r\bigl(t,\theta\bigr)s(z)}
 = \frac{r\bigl(t,\theta\bigr)s(x)}{r\bigl(t,\theta\bigr)\sum_{\{z\,:\,q(z)=t\}} s(z)} \\
&= \frac{s(x)}{\sum_{\{z\,:\,q(z)=t\}} s(z)},
\end{aligned}
```

so $P_{\theta}(X = x \mid T = t)$ does not depend on $\theta$. This implies that for any event $D$, the conditional probability $P_{\theta}(X \in D \mid T = t)$ is the same for all $\theta$ for which $P_{\theta}(T = t) > 0$, so $T$ is a sufficient statistic.

Conversely, assume that $T = q(X)$ is a sufficient statistic. For any $x$ with $p_X(x;\theta) > 0$, the likelihood function is

```math
p_X(x;\theta) = P_{\theta}\bigl(X = x \mid q(X) = q(x)\bigr)\, P_{\theta}\bigl(q(X) = q(x)\bigr).
```

Since $T$ is a sufficient statistic, the first term on the right-hand side does not depend on $\theta$, and is of the form $s(x)$. The second term depends on $x$ through $q(x)$, and is of the form $r\bigl(q(x),\theta\bigr)$. This establishes that the likelihood function can be factored as claimed.

---

<!-- ===== PDF p518 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p518 − 7 = 书页 511，为 SECTION 9.1 习题区。承接上一页（PDF p517）Problem 11 之 Solution (a)，随后是其更 (b)(c)，再是 **Problem 12.\***、**Problem 13.\***、**Problem 14.\***（Rao-Blackwell theorem）。带 * 题的英文 Solution 依规范保留。习题与解答题干保持英文。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 参数 $\theta$ 多被读作 "9"/"0"、$\zeta = h(\theta)$ 读作 "( = h(O)"、泊松似然的指数项、连乘 $1/\prod X_i!$ 等被拆成碎行；$\theta$ 的二项/泊松似然与因子分解依标准公式规范复原，未改动数值。</span>

---

<span style="color:#2471a3;">**Solution（解答）。**</span> (a) *(续)* … which establishes that the likelihood function can be factored as claimed.

(b) This is evident from the definition of a sufficient statistic, since for $\zeta = h(\theta)$, we have

```math
P_{\zeta}\bigl(X \in D \,\big|\, T = t\bigr)
= P_{\theta}\bigl(X \in D \,\big|\, T = t\bigr) \Big|_{\theta = h^{-1}(\zeta)},
```

so $P_{\zeta}\bigl(X \in D \mid T = t\bigr)$ is the same for all $\zeta$.

(c) By part (a), the likelihood function can be factored as $r\bigl(q(x),\theta\bigr)s(x)$. Thus, a ML estimate maximizes $r\bigl(q(x),\theta\bigr)$ over $\theta$ [if $s(x) > 0$] or minimizes $r\bigl(q(x),\theta\bigr)$ over $\theta$ [if $s(x) < 0$], and therefore depends on $x$ only through $q(x)$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 12.\* Examples of a sufficient statistic I.**</span> Show that $q(X) = \sum_{i=1}^{n} X_i$ is a sufficient statistic in the following cases:

(a) $X_1, \ldots, X_n$ are i.i.d. Bernoulli random variables with parameter $\theta$.

(b) $X_1, \ldots, X_n$ are i.i.d. Poisson random variables with parameter $\theta$.

<span style="color:#2471a3;">**Solution（解答）。**</span>

(a) The likelihood function is

```math
p_X(x;\theta) = \theta^{q(x)}(1-\theta)^{\,n - q(x)},
```

so it can be factored as the product of the function $\theta^{q(x)}(1-\theta)^{n-q(x)}$, which depends on $x$ only through $q(x)$, and the constant function $s(x) \equiv 1$. The result follows from the factorization criterion for a sufficient statistic.

(b) The likelihood function is

```math
p_X(x;\theta) = e^{-n\theta}\,\theta^{q(x)} \Big/ \prod_{i=1}^{n} x_i!,
```

so it can be factored as the product of the function $e^{-n\theta}\theta^{q(x)}$, which depends on $x$ only through $q(x)$, and the function $s(x) = 1 \big/ \prod_{i=1}^{n} x_i!$, which depends only on $x$. The result follows from the factorization criterion for a sufficient statistic.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 13.\* Examples of a sufficient statistic II.**</span> Let $X_1,\ldots,X_n$ be i.i.d. normal random variables with mean $\mu$ and variance $\sigma^{2}$. Show that:

(a) If $\sigma^{2}$ is known, $q(X) = \sum_{i=1}^{n} X_i$ is a sufficient statistic for $\mu$.

(b) If $\mu$ is known, $q(X) = \sum_{i=1}^{n} (X_i - \mu)^{2}$ is a sufficient statistic for $\sigma^{2}$.

(c) If both $\mu$ and $\sigma^{2}$ are unknown, $q(X) = \bigl(\sum_{i=1}^{n} X_i,\; \sum_{i=1}^{n} X_i^{2}\bigr)$ is a sufficient statistic for $(\mu, \sigma^{2})$.

<span style="color:#2471a3;">**Solution（解答）。**</span> Use the calculations in Example 9.4, and the factorization criterion.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 14.\* Rao-Blackwell theorem.**</span> This problem shows that a general estimator can be modified into one that only depends on a sufficient statistic, without loss of performance. Given observations $X = (X_1, \ldots, X_n)$, let $T = q(X)$ be a sufficient statistic for the parameter $\theta$, and let $g(X)$ be an estimator for $\theta$.

> <span style="color:#1e8449;">**[t_note]** 注：Rao–Blackwell 给你的是一台『免费升级无偏估计量』的机器：任何估计量 $g(X)$ 按充分统计量 $T$ 取条件期望 $\widehat{g}=E[g(X)\mid T]$ 后，偏差不变、均方误差只减不增。先证：迭代期望保证 $E[\widehat{g}]=E[g]$（偏差相同），全方差公式 $\mathrm{var}(g)=E[\mathrm{var}(g\mid T)]+\mathrm{var}(\widehat{g})$ 说明 $g$ 的方差被拆成『条件内噪声』+『$\widehat{g}$ 的方差』，丢掉非负的 $E[\mathrm{var}(g\mid T)]$ 就只降不升。直觉：$T$ 已含关于 $\theta$ 的全部信息，对 $T$ 取条件匀平了与 $T$ 无关的噪声。跨课程（离散数学·条件=投影）：条件期望就是把任意估计量正交投影到『由 $T$ 决定』的函数子空间上，恰好是你在线性代数里学的正交投影减方差思想。</span>

---

<!-- ===== PDF p519 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p519 − 7 = 书页 512，为 SECTION 9.1 习题区。承接上一页（PDF p518）Problem 14 的 (a)(b)(c) 题干，随后为 **Problem 14.\*** 的英文 Solution，再引出 **Problem 15.\*** 之题干；Problem 15 的 (a)(b)(c) 从本页末尾延续到下一页（PDF p520）。带 * 题的英文 Solution 依规范保留。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页 OCR 碎裂极严重：条件期望 $E_\theta[\,g(X)\mid T]$ 及下标被拆成独立碎行、受 PDF 换行影响大量符号错位；$g(X)\mid T = q(X)$ 与 $b_\theta$ 依 Rao-Blackwell 标准推导复原，未改动任何结果。</span>

---

**(a)** Show that $E_{\theta}\bigl[\,g(X) \mid T\,\bigr]$ is the same for all values of $\theta$, and view

```math
\widehat{g}(X) = E\bigl[\,g(X) \mid T\,\bigr]
```

as a new estimator of $\theta$, which depends on $X$ only through $T$. Thus, we can suppress the subscript $\theta$ and view $\widehat{g}(X)$ as a new estimator of $\theta$.

**(b)** Show that the estimators $g(X)$ and $\widehat{g}(X)$ have the same bias.

**(c)** Show that for any $\theta$ with $\mathrm{var}_{\theta}\bigl(g(X)\bigr) < \infty$,

```math
E_{\theta}\Bigl[\bigl(\widehat{g}(X) - \theta\bigr)^{2}\Bigr] \;\le\; E_{\theta}\Bigl[\bigl(g(X) - \theta\bigr)^{2}\Bigr] \qquad \text{for all } \theta.
```

Furthermore, for a given $\theta$, this inequality is strict if and only if $E_{\theta}\bigl[\mathrm{var}\bigl(g(X) \mid T\bigr)\bigr] > 0$.

<span style="color:#2471a3;">**Solution（解答）。**</span>

(a) Since $q(X)$ is a sufficient statistic, the conditional distribution $P_{\theta}\bigl(X = x \mid T = t\bigr)$ does not depend on $\theta$, so the same is true for $E_{\theta}\bigl[\,g(X) \mid T\,\bigr]$.

(b) We have by the law of iterated expectations

```math
E_{\theta}\bigl[\widehat{g}(X)\bigr] = E_{\theta}\Bigl[\,E\bigl[\,g(X) \mid T\,\bigr]\,\Bigr] = E_{\theta}\bigl[g(X)\bigr],
```

so the biases of $g(X)$ and $\widehat{g}(X)$ are equal.

(c) Fix some $\theta$ and let $b_\theta$ denote the common bias of $g(X)$ and $\widehat{g}(X)$. We have, using the law of total variance,

```math
\begin{aligned}
E_{\theta}\Bigl[\bigl(g(X) - \theta\bigr)^{2}\Bigr]
&= \mathrm{var}_{\theta}\bigl(g(X)\bigr) + b_\theta^{2} \\
&= E_{\theta}\Bigl[\mathrm{var}\bigl(g(X) \mid T\bigr)\Bigr] + \mathrm{var}_{\theta}\Bigl[E\bigl[\,g(X) \mid T\,\bigr]\Bigr] + b_\theta^{2} \\
&= E_{\theta}\Bigl[\mathrm{var}\bigl(g(X) \mid T\bigr)\Bigr] + \mathrm{var}_{\theta}\bigl(\widehat{g}(X)\bigr) + b_\theta^{2} \\
&= E_{\theta}\Bigl[\mathrm{var}\bigl(g(X) \mid T\bigr)\Bigr] + E_{\theta}\Bigl[\bigl(\widehat{g}(X) - \theta\bigr)^{2}\Bigr] \\
&\ge E_{\theta}\Bigl[\bigl(\widehat{g}(X) - \theta\bigr)^{2}\Bigr],
\end{aligned}
```

with the inequality being strict if and only if $E_{\theta}\bigl[\mathrm{var}\bigl(g(X) \mid T\bigr)\bigr] > 0$.

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 15.\***</span> Let $X_1,\ldots,X_n$ be i.i.d. random variables that are uniformly distributed over the interval $[0,\theta]$.

(a) Show that $T = \max_{i=1,\ldots,n} X_i$ is a sufficient statistic.

(b) Show that $g(X) = (2/n)\sum_{i=1}^{n} X_i$ is an unbiased estimator.

(c) Find the form of the estimator $\widehat{g}(X) = E\bigl[\,g(X) \mid T\,\bigr]$, and then calculate and compare $E_{\theta}\Bigl[\bigl(g(X) - \theta\bigr)^{2}\Bigr]$ with $E_{\theta}\Bigl[\bigl(\widehat{g}(X) - \theta\bigr)^{2}\Bigr]$.

> <span style="color:#1e8449;">**[t_note]** 注：这一题把 Rao–Blackwell 落到能算的具体数字上：$g(X)=\frac{2}{n}\sum_iX_i$（用样本均值估 $U[0,\theta]$ 的上界）与 $\widehat{g}=\frac{n+1}{n}\max_iX_i$（对充分统计量 $\max_iX_i$ 取条件期望）都无偏，但均方误差一个 $\theta^2/(3n)$、另一个 $\theta^2/\bigl(n(n+2)\bigr)$，后者恒更小。先证：$g$ 只用平均值（信息浪费），而 $T=\max_iX_i$ 是充分统计量、捕获了关于 $\theta$ 的全部信息；对 $T$ 取条件期望后噪声被匀平，方差的差距正是 Rao–Blackwell 保证的『只降不升』。$U[0,\theta]$ 的 $\hat\theta=\max_iX_i$（有偏）与 $2\bar X$（无偏但 MSE 更大）正好为 Problem 8 的提问画上句号。</span>

> <span style="color:#7f8c8d;">Problem 15 的 Solution 展开在下一页（PDF p520）给出，本页止于题干。</span>

---

<!-- ===== PDF p520 ===== -->

> <span style="color:#7f8c8d;">本书页 = PDF p520 − 7 = 书页 513，为 SECTION 9.1 习题区。承接上一页（PDF p519）Problem 15.\* 的题干，本页为其英文 Solution (a)(b)(c)。此为 **Problem 15（§9.1 最后一题）的收尾**；随后 Problem 16 起的 SECTION 9.2 内容不在本 worker 批内。带 * 题的英文 Solution 依规范保留。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页 OCR 碎裂严重：均匀分布似然的分段定义、$T$ 的 PDF $n t^{n-1}/\theta^n$、条件期望 $E[g(X)\mid T = t]$ 均被拆成大量碎行；数值 $E\bigl[\widehat{g}^{\,2}\bigr]$、$\theta^2/(3n)$、$\theta^2/\bigl(n(n+2)\bigr)$ 依标准计算复原，未改动数值。</span>

---

<span style="color:#2471a3;">**Solution（解答）。**</span> (a) The likelihood function is

```math
f_X(x;\theta) = \begin{cases}
\dfrac{1}{\theta^n}, & 0 \le x_i \le \theta \;\; \bigl(\text{i.e. } \theta \ge \max\nolimits_{i=1,\ldots,n} x_i\bigr) \\[6pt]
0, & \text{otherwise},
\end{cases}
```

which depends on $X$ only through $q(x) = \max_{i=1,\ldots,n} x_i$. The result follows from the factorization criterion for a sufficient statistic.

(b) We have

```math
E_{\theta}\bigl[g(X)\bigr] = \frac{2}{n}\sum_{i=1}^{n} E_{\theta}\bigl[X_i\bigr] = \frac{2}{n}\sum_{i=1}^{n} \frac{\theta}{2} = \theta.
```

(c) Conditioned on the event $\{T = t\}$, one of the observations $X_i$ is equal to $t$. The remaining $n-1$ observations are uniformly distributed over the interval $[0,t]$, and have a conditional expectation equal to $t/2$. Thus,

```math
\begin{aligned}
E\bigl[\,g(X) \mid T = t\,\bigr]
&= \frac{2}{n}\, E\Bigl[\; \sum_{i=1}^{n} X_i \;\Big |\; T = t\Bigr]
 = \frac{2}{n}\Bigl(t + (n-1)\frac{t}{2}\Bigr)
 = \frac{n+1}{n}\,t,
\end{aligned}
```

and

```math
\widehat{g}(X) = E\bigl[\,g(X) \mid T\,\bigr] = \frac{n+1}{n}\,T.
```

We will now calculate the mean squared error of the two estimators $g(X)$ and $\widehat{g}(X)$, as functions of $\theta$. To this end, we evaluate the first and second moment of $\widehat{g}(X)$. We have

```math
E_{\theta}\bigl[\widehat{g}(X)\bigr] = E_{\theta}\Bigl[E\bigl[\,g(X)\mid T\,\bigr]\Bigr] = E_{\theta}\bigl[g(X)\bigr] = \theta.
```

To find the second moment, we first determine the PDF of $T$. For $t \in [0,\theta]$, we have $P_{\theta}(T \le t) = (t/\theta)^{n}$, and by differentiating, $f_T(t;\theta) = n t^{n-1}/\theta^{n}$. Thus,

```math
E_{\theta}\Bigl[\bigl(\widehat{g}(X)\bigr)^{2}\Bigr]
= \Bigl(\frac{n+1}{n}\Bigr)^{2} E_{\theta}\bigl[T^{2}\bigr]
= \Bigl(\frac{n+1}{n}\Bigr)^{2} \int_0^{\theta} t^{2}\,\frac{n t^{n-1}}{\theta^{n}}\,dt
= \Bigl(\frac{n+1}{n}\Bigr)^{2}\frac{n\,\theta^{2}}{n+2}
= \frac{(n+1)^{2}\,\theta^{2}}{n(n+2)}.
```

Since $\widehat{g}(X)$ has mean $\theta$, its mean squared error is equal to its variance, and

```math
E_{\theta}\Bigl[\bigl(\widehat{g}(X) - \theta\bigr)^{2}\Bigr]
= \frac{(n+1)^{2}\,\theta^{2}}{n(n+2)} - \theta^{2}
= \frac{\theta^{2}}{n(n+2)}.
```

Similarly, the mean squared error of $g(X)$ is equal to its variance, and

```math
E_{\theta}\Bigl[\bigl(g(X) - \theta\bigr)^{2}\Bigr]
= \frac{4}{n^{2}}\sum_{i=1}^{n} \mathrm{var}_{\theta}(X_i)
= \frac{4}{n^{2}}\cdot n\cdot\frac{\theta^{2}}{12}
= \frac{\theta^{2}}{3n}.
```

It can be seen that

```math
\frac{1}{3n} \;\ge\; \frac{1}{n(n+2)} \qquad \text{for all positive integers } n,
```

so that $E_{\theta}\bigl[(\widehat{g}(X)-\theta)^{2}\bigr] \le E_{\theta}\bigl[(g(X)-\theta)^{2}\bigr]$, which is consistent with the Rao-Blackwell theorem.

---

<!-- ===== PDF p521 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9 习题（Problems）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p521 − 7 = 书页 514，属第 9 章习题区的 **SECTION 9.2（Linear Regression，线性回归）**。习题区自书页 507 起连续编号（Problem 1→30），本页不含新开头，照常承接前页习题流。本页含 **Problem 16**、**Problem 17**（均为普通题，无内页 Solution）与带 \* 的 **Problem 18**（题设写于本页，Solution 续至后续页即 PDF p522–p524）。按规范，非星题题干保留英文原文、不译；星题（\*）题干与其英文 Solution 均保留英文。</span>

> <span style="color:#7f8c8d;">[原页 OCR 损坏] 本页表格数据多处被 OCR 拆碎：Problem 17 的数据对（$X_i,\,Y_i$）在源 OCR 中被读作散列（如 "103.544 2 15.775"→$103.544, 215.775$、"333.9 1 1"→$333.911$），Problem 16 的电量值 "20. 10 "→$20.10$、"2 1.86"→$21.86$。下方按列对应关系复原为规范两列表格，数字未作改动，排序/小数位以能为原书语义为复原目标。</span>

---

<span style="color:#00838f;">**SECTION 9.2 · Linear Regression（线性回归）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 16**</span>

An electric utility company tries to estimate the relation between the daily amount of electricity used by customers and the daily summer temperature. It has collected the data shown on the table below.

| Temperature（温度） | Electricity（用电量） |
|---|---|
| 96 | 23.67 |
| 89 | 20.45 |
| 81 | 21.86 |
| 86 | 23.28 |
| 83 | 20.71 |
| 73 | 18.21 |
| 78 | 18.85 |
| 74 | 20.10 |
| 76 | 18.48 |
| 78 | 17.94 |

(a) Set up and estimate the parameters of a linear model that can be used to predict electricity consumption as a function of temperature.

(b) If the temperature on a given day is 90 degrees, predict the amount of electricity consumed on that day.

> <span style="color:#1e8449;">**[t_note]** 注：线性回归把『点数据』锻造成『预测机器』：用最小二乘/ML 拟合 $Y=\theta_0+\theta_1X$ 后，给定 $X=90$ 便能带公式得到 $\widehat Y$。先证：这里每对 $(X_i,Y_i)$ 是样本，回归线是被估参数，预测点 $\hat y=\hat\theta_0+\hat\theta_1\cdot 90$ 落在线上；但注意预测与已观测点不同——已观测点的残差带误差，预测带还要额外计入 $\theta_1$ 估计的不确定性与未观测的噪声。跨课程（CSAPP·数据驱动模型）：把散点抽象成『温度→用电』的线性规则，正是你把实验数据压成可复用结论的典型动作，问题 (b) 就是对这条规则的泛化检验。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 17**</span>

Given the five data pairs $(X_i, Y_i)$ in the table below,

| $X_i$ | $Y_i$ |
|---|---|
| 0.798 | −2.373 |
| 2.546 | 20.906 |
| 7.261 | 5.005 |
| 103.544 | 215.775 |
| 9.131 | 333.911 |

we want to construct a model relating $X$ and $Y$. We consider a linear model

```math
Y_i = \theta_0 + \theta_1 X_i + W_i, \qquad i = 1, \ldots, 5,
```

and a quadratic model

```math
Y_i = \theta_0 + \theta_1 X_i + \theta_2 X_i^2 + V_i, \qquad i = 1, \ldots, 5,
```

where $W_i$ and $V_i$ represent additive noise terms, modeled by independent normal random variables with mean zero and variance $\sigma_w^2$ and $\sigma_v^2$, respectively.

(a) Find the ML estimates of the linear model parameters.

(b) Find the ML estimates of the quadratic model parameters.

(c) Assume that the two estimated models are equally likely to be true, and that the noise terms $W_i$ and $V_i$ have the same variance: $\sigma_w^2 = \sigma_v^2$. Use the MAP rule to choose between the two models.

> <span style="color:#1e8449;">**[t_note]** 注：(c) 在『模型选择』而非『参数估计』层面下功夫：两个候选模型等先验、同噪声方差，MAP 退化为比两者的 ML 拟合优度（谁的残差更能解释数据）。先证：MAP 后验正比于似然×先验，先验相等时只需比似然——每模型各有两个待估参数的 ML 拟合，谁的对数似然高谁胜。这里也藏着过拟合的伏笔：二次模型参数多，多用例如 $103.544/215.775$、$9.131/333.911$ 这种离群点时往往把曲线扭弯追噪声，MAP 的自动权衡正是对『参数多＝更会过拟合』的侧面惩罚。跨课程（凸优化·模型复杂度权衡）：选复杂度使风险最小，是偏差–方差权衡的具体版。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 18\***</span>

**Unbiasedness and consistency in linear regression.** In a probabilistic framework for regression, let us assume that $Y_i = \theta_0 + \theta_1 X_i + W_i$, $i = 1, \ldots, n$, where $W_1, \ldots, W_n$ are i.i.d. normal random variables with mean zero and variance $\sigma^2$. Then, given $X_i$ and the realized values $Y_i$ of $Y_i$, $i = 1, \ldots, n$, the ML estimates of $\theta_0$ and $\theta_1$ are given by the linear regression formulas, as discussed in Section 9.2.

(a) Show that the ML estimators $\hat\theta_0$ and $\hat\theta_1$ are unbiased.

> <span style="color:#7f8c8d;">问题 (b)(c) 及本带 \* 题的英文 Solution 延续至下一页（PDF p522）。</span>

---

<!-- ===== PDF p522 ===== -->

<span style="color:#c0392b;">**§9 习题（Problems）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p522 − 7 = 书页 515，属第 9 章习题区 SECTION 9.2 的延续（Problem 16–19 连续编号）。本页无新题开头，为带 \* 的 **Problem 18** 之继续：先是题设的 (b)(c) 部分，继而 Notes 与英文 **Solution** (a) 的开头（Solution 延续至下一页 PDF p523）。按规范星题题干与其英文 Solution 均保留英文。</span>

> <span style="color:#7f8c8d;">[原页 OCR 严重碎裂] Solution 的推导在源 OCR 中被打成大量碎片（分式拆行、$\hat\theta_0/\hat\theta_1$ 被读作 "80/8 1"、"O/Or"、$x̄$ 与求和上下限碎裂）。下文按 §9.2 线性回归的 ML 估计标准公式原型作忠实重建，未改动数值语义，不臆造原文未给出的数字。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 18\*（续）**</span>

(b) Show that the variances of the estimators $\hat\theta_0$ and $\hat\theta_1$ are

```math
\text{var}(\hat\theta_0) = \frac{\sigma^2 \sum_{i=1}^{n} X_i^2}{n \sum_{i=1}^{n} (X_i - \bar X)^2},
\qquad
\text{var}(\hat\theta_1) = \frac{\sigma^2}{\sum_{i=1}^{n} (X_i - \bar X)^2},
```

respectively, and their covariance is

```math
\text{cov}(\hat\theta_0, \hat\theta_1) = -\frac{\sigma^2 \bar X}{\sum_{i=1}^{n} (X_i - \bar X)^2}.
```

(c) Show that if $\sum_{i=1}^{n} (X_i - \bar X)^2 \to \infty$ and $\bar X^2$ is bounded by a constant as $n \to \infty$, we have $\text{var}(\hat\theta_0) \to 0$ and $\text{var}(\hat\theta_1) \to 0$. (This, together with Chebyshev's inequality, implies that the estimators $\hat\theta_0$ and $\hat\theta_1$ are consistent.)

> <span style="color:#7f8c8d;">Note: Although the assumption that the $W_i$ are normal is needed for our estimators to be ML estimators, the argument below shows that these estimators remain unbiased and consistent without this assumption.</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution.**</span>

(a) Let the true values of $\theta_0$ and $\theta_1$ be $\theta_0^*$ and $\theta_1^*$, respectively. We have

```math
\hat\theta_1 = \frac{\sum_{i=1}^{n} (X_i - \bar X) Y_i}{\sum_{i=1}^{n} (X_i - \bar X)^2},
```

where $\bar Y = (\sum_{i=1}^{n} Y_i)/n$, and where we treat $X_1, \ldots, X_n$ as constant. Denoting $\bar W = (\sum_{i=1}^{n} W_i)/n$, we have

```math
\bar Y = \theta_0^* + \theta_1^* \bar X + \bar W,
```

and

```math
\hat\theta_1 = \theta_1^* + \frac{\sum_{i=1}^{n} (X_i - \bar X) W_i}{\sum_{i=1}^{n} (X_i - \bar X)^2},
\qquad
\hat\theta_0 = \bar Y - \hat\theta_1 \bar X.
```

Thus,

```math
E[\hat\theta_1] = \theta_1^*,
```

where we have used the fact $\sum_{i=1}^{n} (X_i - \bar X) = 0$. Since $E[W_i] = 0$, it follows that

```math
E[\hat\theta_0] = \theta_0^*
```

already follows on the next page.

> <span style="color:#7f8c8d;">本带 \* 题的英文 Solution 续至下一页（PDF p523）。</span>

---

<!-- ===== PDF p523 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9 习题（Problems）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p523 − 7 = 书页 516，属第 9 章习题区 SECTION 9.2 的延续。本页为带 \* 的 **Problem 18** 英文 **Solution** 的中间部分（Solution(a) 收尾 + Solution(b) 推导），它在前一页（PDF p522）开始、延续到下一页（PDF p524）。无新题开头，习题连续编号不断。</span>

> <span style="color:#7f8c8d;">[原页 OCR 严重碎裂] Solution(b) 的分式与协方差推导在源 OCR 中被拆成碎片（分母求和上下限、"= var(W) + X2 var(Sd - 2X cov(W, S 1 )" 等）。下文按 §9.2 方差/协方差标准公式原型忠实重建。</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（续）.**</span>

where we have used the fact $\sum_{i=1}^{n}(X_i - \bar X) = 0$. Since $E[W_i] = 0$, it follows that

```math
E[\hat\theta_1] = \theta_1^* .
```

Also

```math
E[\hat\theta_0] = E[\bar Y] - \bar X\, E[\hat\theta_1],
```

and using the facts $E[\hat\theta_1] = \theta_1^*$ and $E[\bar W] = 0$, we obtain

```math
E[\hat\theta_0] = \theta_0^* .
```

Thus, the estimators $\hat\theta_0$ and $\hat\theta_1$ are unbiased.

(b) We now calculate the variance of the estimators. Using the formula for $\hat\theta_1$ derived in part (a) and the independence of the $W_i$, we have

```math
\text{var}(\hat\theta_1) = \frac{\sigma^2}{\sum_{i=1}^{n} (X_i - \bar X)^2}.
```

Similarly, using the formula for $\hat\theta_0$ derived in part (a),

```math
\text{var}(\hat\theta_0) = \text{var}(\bar W - \bar X\,\hat\theta_1)
= \text{var}(\bar W) + \bar X^2\, \text{var}(\hat\theta_1) - 2\bar X\, \text{cov}(\bar W, \hat\theta_1).
```

Since $\sum_{i=1}^{n}(X_i - \bar X) = 0$ and $E[\bar W\, W_i] = \sigma^2/n$ for all $i$, we obtain

```math
\text{cov}(\bar W, \hat\theta_1)
= E\!\left[\bar W \cdot \frac{\sum_{i=1}^{n} (X_i - \bar X) W_i}{\sum_{i=1}^{n} (X_i-\bar X)^2}\right]
= \frac{\sum_{i=1}^{n} (X_i - \bar X)\,\sigma^2/n}{\sum_{i=1}^{n} (X_i-\bar X)^2}
= 0.
```

Combining the last three equations, we obtain

```math
\text{var}(\hat\theta_0)
= \frac{\sigma^2}{n} + \frac{\bar X^2 \sigma^2}{\sum_{i=1}^{n} (X_i-\bar X)^2}
= \frac{\sigma^2\left[\sum_{i=1}^{n} (X_i-\bar X)^2 + n\bar X^2\right]}{n \sum_{i=1}^{n} (X_i-\bar X)^2}.
```

By expanding the quadratic forms $(X_i - \bar X)^2$, we also have

```math
\sum_{i=1}^{n} (X_i - \bar X)^2 + n\bar X^2 = \sum_{i=1}^{n} X_i^2 .
```

> <span style="color:#7f8c8d;">本带 \* 题的英文 Solution 续至下一页（PDF p524）。</span>

---

<!-- ===== PDF p524 ===== -->

<span style="color:#c0392b;">**§9 习题（Problems）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p524 − 7 = 书页 517，属第 9 章习题区 SECTION 9.2 的延续。本页先收束带 \* 的 **Problem 18** 英文 Solution（协方差与相合性 (c)），随后引出带 \* 的 **Problem 19**（Variance estimate in linear regression）及其英文 Solution 的开头（展开式，Solution 续至下一页 PDF p525）。习题连续编号不断。</span>

> <span style="color:#7f8c8d;">[原页 OCR 严重碎裂] Problem 19 的 V（残差平方和）展开式在源 OCR 中被打成碎片（多处求和式拆行、"var( 80) = var(W ) + X2 var(S I)" 等）。下文按 §9.3 残差平方和标准公式原型忠实重建。</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（续）.**</span>

By combining the preceding two equations,

```math
\text{var}(\hat\theta_0) = \frac{\sigma^2 \sum_{i=1}^{n} X_i^2}{n \sum_{i=1}^{n} (X_i - \bar X)^2}.
```

We finally calculate the covariance of $\hat\theta_0$ and $\hat\theta_1$. We have

```math
\hat\theta_0 = \bar Y - \bar X\, \hat\theta_1,
```

or

```math
\text{cov}(\hat\theta_0, \hat\theta_1) = -\bar X\, \text{var}(\hat\theta_1) + \text{cov}(\bar W, \hat\theta_1).
```

Since, as shown earlier, $\text{cov}(\bar W, \hat\theta_1) = 0$, we finally obtain

```math
\text{cov}(\hat\theta_0, \hat\theta_1) = -\frac{\bar X\, \sigma^2}{\sum_{i=1}^{n} (X_i - \bar X)^2}.
```

(c) If $\sum_{i=1}^{n}(X_i - \bar X)^2 \to \infty$, the expression for $\text{var}(\hat\theta_1) \to 0$ derived in part (b) goes to zero. Then, the formula

```math
\text{var}(\hat\theta_0) = \text{var}(\bar W) + \bar X^2\, \text{var}(\hat\theta_1),
```

from part (b), together with the assumption that $\bar X^2$ is bounded by a constant, implies that $\text{var}(\hat\theta_0) \to 0$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 19\***</span>

**Variance estimate in linear regression.** Under the same assumptions as in the preceding problem, show that

```math
\frac{\sum_{i=1}^{n} (Y_i - \hat\theta_0 - \hat\theta_1 X_i)^2}{n - 2}
```

is an unbiased estimator of $\sigma^2$.

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution.**</span>

Let $V = \sum_{i=1}^{n}(Y_i - \hat\theta_0 - \hat\theta_1 X_i)^2$. Using the formula $\hat\theta_0 = \bar Y - \hat\theta_1 \bar X$ and the expression for $\hat\theta_1$, we have

```math
V = \sum_{i=1}^{n} (Y_i - \hat\theta_0 - \hat\theta_1 X_i)^2
= \sum_{i=1}^{n} Y_i^2 - n\bar Y^2 - 2\hat\theta_1 \sum_{i=1}^{n} (Y_i - \bar Y)(X_i - \bar X) + \hat\theta_1^2 \sum_{i=1}^{n} (X_i - \bar X)^2 .
```

> <span style="color:#7f8c8d;">本带 \* 题的英文 Solution 续至下一页（PDF p525）。</span>

---

<!-- ===== PDF p525 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9 习题（Problems）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p525 − 7 = 书页 518，属第 9 章习题区。页首收束带 \* 的 **Problem 19** 英文 Solution 的尾部（取期望化简得 $E[V]=(n-2)\sigma^2$），随后本页另起新小节标题 **SECTION 9.3 · Binary Hypothesis Testing（二元假设检验）**，出现 **Problem 20**、**Problem 21**（均为普通题，页内未印 Solution）。习题连续编号 Problem 19→20→21 不断。</span>

> <span style="color:#7f8c8d;">[原页 OCR 严重碎裂] Problem 19 Solution 的期望式与 Problem 20/21 的某些数学式在源 OCR 中被拆碎（如 $E[\bar Y^2]$ 记作 "E [V2 ]"、$\sigma_0^2=16 / \sigma_1^2=25$ 作 "= 1 6/= 25"）。Problem 20 的拒绝域（rejection region）形如在源 OCR 中不可辨（该行仅余 "for some scalar $\\gamma$"），故下方仅保留题目表述与"形如"字样，拒绝域的具体形式按上下文注以灰注、不臆造。</span>

<span style="color:#2471a3;">**[solution]**</span> <span style="color:#2471a3;">**Solution（续）.**</span>

Taking expectation of both sides, we obtain

```math
E[V] = \sum_{i=1}^{n} E[Y_i^2] - n\, E[\bar Y^2] - \sum_{i=1}^{n} (X_i - \bar X)^2\, E[\hat\theta_1^2].
```

We also have

```math
E[Y_i^2] = \text{var}(Y_i) + (E[Y_i])^2 = \sigma^2 + (\theta_0^* + \theta_1^* X_i)^2,
```

```math
E[\bar Y^2] = \text{var}(\bar Y) + (E[\bar Y])^2 = \frac{\sigma^2}{n} + (\theta_0^* + \theta_1^* \bar X)^2,
```

```math
E[\hat\theta_1^2] = \text{var}(\hat\theta_1) + (E[\hat\theta_1])^2 = \frac{\sigma^2}{\sum_{i=1}^{n} (X_i - \bar X)^2} + (\theta_1^*)^2 .
```

Combining the last four equations and simplifying, we obtain

```math
E[V] = (n - 2)\, \sigma^2,
```

so that $V/(n-2)$ is an unbiased estimator of $\sigma^2$.

---

<span style="color:#00838f;">**SECTION 9.3 · Binary Hypothesis Testing（二元假设检验）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 20**</span>

A random variable $X$ is characterized by a normal PDF with mean $\mu_0 = 20$, and a variance that is either $\sigma_0^2 = 16$ (hypothesis $H_0$) or $\sigma_1^2 = 25$ (hypothesis $H_1$). We want to test $H_0$ against $H_1$, using three sample values $X_1, X_2, X_3$, and a rejection region of the form

```math
R = \{ (x_1, x_2, x_3) \mid \ \cdots > \gamma \},
```

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] 上式拒绝域 $R$ 的具体表达式在源 OCR 中缺失（该行反余 "for some scalar $\\gamma$"），此处以占位符表示，未能复原原文，未臆造具体形式。</span>

for some scalar $\gamma$. Determine the value of $\gamma$ so that the probability of false rejection is $0.05$. What is the corresponding probability of false acceptance?

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 21**</span>

A normal random variable $X$ is known to have a mean of 60 and a standard deviation equal to 5 (hypothesis $H_0$) or 8 (hypothesis $H_1$).

(a) Consider a hypothesis test using a single sample $x$. Let the rejection region be of the form

```math
R = \{ x \mid |x - 60| > \gamma \}
```

for some scalar $\gamma$. Determine $\gamma$ so that the probability of false rejection of $H_0$ is $0.1$. What is the corresponding false acceptance probability? Would the rejection region change if we were to use the LRT with the same false rejection probability?

(b) Consider a hypothesis test using $n$ independent samples $X_1, \ldots, X_n$. Let the rejection region be of the form

```math
R = \{ (x_1, \ldots, x_n) \mid |\bar x - 60| > \gamma \},
```

where $\gamma$ is chosen so that the probability of false rejection of $H_0$ is $0.1$. How does the false acceptance probability change with $n$? What can you conclude about the appropriateness of this type of test?

> <span style="color:#1e8449;">**[t_note]** 注：这一问直接命中『样本量如何救检验』的直觉。先证：假误拒被锁死在 0.1，而假接受对应『$H_1$ 为真（$\sigma=8$）时样本均值仍落进接受域』。$n$ 越大，$\bar X$ 的方差 $\sigma^2/n$ 越小，接受域外（更多样本均值）更像 $H_1$，假接受概率随 $n$ 下降——这是样本量压低第二类错误的清晰案例。但它也提醒你检验的边界：若 $H_0$ 与 $H_1$ 分布几乎重合，或你总用同一种『$|\bar X-60|>\gamma$』形状，$H_1$ 几乎不可分时不管 $n$ 多大效能都上不去。跨课程（实分析·O 记号直觉）：假接受随 $n$ 呈指数级衰减，用渐近阶的眼光看『这个检验值不值』。</span>

> <span style="color:#7f8c8d;">Problem 21 的 (c) 部分延续至下一页（PDF p526）。</span>

---

<!-- ===== PDF p526 ===== -->

<span style="color:#c0392b;">**§9 习题（Problems）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p526 − 7 = 书页 519，属第 9 章习题区。页首承接 **Problem 21** 的 (c) 部分（§9.3 区间内），随后出现带普通号 §9.3 的 **Problem 22**、**Problem 23**、**Problem 24**，继而本页另起小节标题 **SECTION 9.4 · Significance Testing（显著性检验）**，出现 **Problem 25**、**Problem 26**。习题连续编号 Problem 21→…→26 不断，无内页 Solution。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] Problem 24 中的临界值符号在源 OCR 中无法辨认（仅余占位），Problem 21(b)/Problem 26 中参数符号（$\theta$、$\mu$、$\sigma^2$ 等）被读作 "t-t"、"0 = 0 . 5" 等零散字样，均已按上下文规范复原。题面原文（英文）保留，未逐句翻译。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 21（续）**</span>

(c) Derive the structure of the LRT using $n$ independent samples $X_1, \ldots, X_n$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 22**</span>

There are two hypotheses about the probability of heads for a given coin: $\theta = 0.5$ (hypothesis $H_0$) and $\theta = 0.6$ (hypothesis $H_1$). Let $X$ be the number of heads obtained in $n$ tosses, where $n$ is large enough so that normal approximations are appropriate. We test $H_0$ against $H_1$ by rejecting $H_0$ if $X$ is greater than some suitably chosen threshold $k_n$.

(a) What should be the value of $k_n$ so that the probability of false rejection is less than or equal to $0.05$?

(b) What is the smallest value of $n$ for which both probabilities of false rejection and false acceptance can be made less than or equal to $0.05$?

(c) For the value of $n$ found in part (b), what would be the probability of false acceptance if we were to use a LRT with the same probability of false rejection?

> <span style="color:#1e8449;">**[t_note]** 注：(b) 是检验设计里最有实操价值的『样本量反解』：问 $n$ 要多大力能同时压下误拒与误接受两种错误到 0.05。先证：$H_0:\theta=0.5$ vs $H_1:\theta=0.6$ 分别给正面数 $X$ 两个正态峰（均值相距 $0.1n$），加大 $n$ 让两峰变窄、间距相对变宽，阈值 $k_n$ 便能同时卡住两端的 5% 尾。这是第一/二类错误权衡的定量出口：单靠某一侧的拒绝域形状不够，样本量才是能把两条错误率同时压小的真杠杆，也呼应 §9.4 评注 (iii)『$\alpha$ 取小会让误接受变大』。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 23**</span>

The number of phone calls received by a ticket agency on any one day is Poisson distributed. On an ordinary day, the expected value of the number of calls is $\lambda_0$, and on a day where there is a popular show in town, the expected value of the number of calls is $\lambda_1$, with $\lambda_1 > \lambda_0$. Describe the LRT for deciding whether there is a popular show in town based on the number of calls received. Assume a given probability of false rejection, and find an expression for the critical value $\epsilon$.

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 24**</span>

We have received a shipment of light bulbs whose lifetimes are modeled as independent, exponentially distributed random variables, with parameter equal to $\lambda_0$ (hypothesis $H_0$) or equal to $\lambda_1$ (hypothesis $H_1$). We measure the lifetimes of $n$ light bulbs. Describe the LRT for selecting one of the two hypotheses. Assume a given probability of false rejection of $H_0$ and give an analytical expression for the critical value $\epsilon$.

> <span style="color:#7f8c8d;">[原页此处 OCR 损坏] Problem 24 中临界值的符号（此处记作 $\epsilon$）在源 OCR 的公式位无法辨认（仅一个占位记号），能否确认为 $\epsilon$ 存在不确定性；其余题面文字完整可按原文保留。</span>

---

<span style="color:#00838f;">**SECTION 9.4 · Significance Testing（显著性检验）**</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 25**</span>

Let $X$ be a normal random variable with mean $\mu$ and unit variance. We want to test the hypothesis $\mu = 5$ at the 5% level of Significance, using $n$ independent samples of $X$.

(a) What is the range of values of the sample mean for which the hypothesis is accepted?

(b) Let $n = 10$. Calculate the probability of accepting the hypothesis $\mu = 5$ when the true value of $\mu$ is $4$.

> <span style="color:#1e8449;">**[t_note]** 注：(b) 逼你亲手算第二类错误，这才是检验设计的另一半。先证：在真实 $\mu=4$ 下样本均值 $\bar X\sim N(4,\tfrac{1}{n})$（单位方差），而 (a) 的接受区由 $H_0$ 下 $\bar X\in \mu_0\pm1.96/\sqrt n$ 决定（即 $[5-1.96/\sqrt{n},5+1.96/\sqrt{n}]$）；把 $n=10$ 代入、再对『真实分布落在接受区里的概率』求标准正态 CDF 即得误接受概率。关键洞察：接受区中心（5）与真实值（4）只差一个标准误单位的量，两者正态峰部分重叠，故误接受概率远大于 0——检验并非『不拒绝就等于 $\mu=5$ 很可信』，而是『证据不足』。这正是第一/二类错误此消彼长的具象：宁可放容，就换来了高误接受。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 26**</span>

We have five observations drawn independently from a normal distribution with unknown mean $\mu$ and unknown variance $\sigma^2$.

(a) Estimate $\mu$ and $\sigma^2$ if the observation values are $8.47, 10.91, 10.87, 9.46, 10.40$.

(b) Use the t-distribution tables to test the hypothesis $\mu = 9$ at the 95% significance level, using the estimates of part (a).

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] Problem 26(b) 中的 "95% significance level" 一词按源 OCR 原样保留；此处显著性水平措辞略显反常（按习题惯例或应为 5%），因题干保留英文原文，未作改动。本页所辖 Problem 21–26 就此结束，下一题 **Problem 27** 位于下一页（PDF p527，书页 520）。</span>

---

<!-- ===== PDF p527 ===== -->

<span style="color:#c0392b;">**第 9 章　经典统计推断（Classical Statistical Inference）**</span>

<span style="color:#c0392b;">**§9 习题（Problems）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p527 − 7 = 书页 520，属第 9 章习题区的最后一段正文页，含 §9.4 的 **Problem 27、28、29、30**。Problem 30 之后即进入全书后页书（Back Matter）：下一页（PDF p528，书页 521）为 **Index 索引**。习题区至此以 Problem 30 收尾，无独立附录正文。</span>

> <span style="color:#7f8c8d;">[原页 OCR 严重碎裂] 参数符号大量被误读：$\mu_x/\mu_y$、$\sigma_x^2=32/\sigma_y^2=29$（作 "01 = 32 / O' = 29"）、$\theta$、$W$（作 "IV"）、`0.5`（作 "0 . 5"）等。Problem 27 的样本均值 $\bar x=181,\, \bar y=177$、Problem 30 的五个信号值 $0.96, -0.34, 0.85, 0.51, 0.24$ 均保持原样。题干保留英文原文，符号按上下文规范复原。</span>

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 27**</span>

A plant grows on two distant islands. Suppose that its life span (measured in days) on the first (or the second) island is normally distributed with unknown mean $\mu_x$ (or $\mu_y$) and known variance $\sigma_x^2 = 32$ (or $\sigma_y^2 = 29$, respectively). We wish to test the hypothesis $\mu_x = \mu_y$, based on 10 independent samples from each island. The corresponding sample means are $\bar x = 181$ and $\bar y = 177$. Do the data support the hypothesis at the 95% significance level?

> <span style="color:#1e8449;">**[t_note]** 注：这正是 Example 9.17 两总体均值检验的『已知方差版』：$H_0:\mu_x=\mu_y$，统计量用 $\bar x-\bar y$，方差 $\mathrm{var}(\bar x-\bar y)=\sigma_x^2/n+\sigma_y^2/n$（方差和公式，两样本独立所以相加）。先证：$\bar x-\bar y$ 近似正态，$|\bar x-\bar y|=4$ 相对标准误 $\sqrt{32/10+29/10}\approx2.47$ 仅约 1.6 个标准差，落在 95% 接受域内，故不拒绝 $H_0$。这里 $\sigma_x^2,\sigma_y^2$ 已知，不必像 Example 9.17 那样 plug-in 估计——这就是题目安排已知方差的用意：专注演示『均值差 + 标准误』的骨架，往后方差未知再套 $t$ 分布。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 28**</span>

A company considers buying a machine to manufacture a certain item. When tested, 28 out of 600 items produced by the machine were found defective. Do the data support the hypothesis that the defect rate of the machine is smaller than 3 percent, at the 5% significance level?

> <span style="color:#1e8449;">**[t_note]** 注：这是对『一个比例』的**单侧**检验：样本点估计 $\hat p=28/600\approx0.0467$，问它是否显著高于 3%。先证：$H_0:p=0.03$、$H_1:p>0.03$，用二项→正态近似，检验统计量 $Z=(\hat p-p_0)/\sqrt{p_0(1-p_0)/600}$，在 $\alpha=0.05$ 下单侧临界 $1.645$。算出 $Z$ 若约 $2$ 个标准差、超过 1.645 便拒绝『缺陷率不超 3%』。这类『比例 vs 阈值』题是把工厂质检、A/B 实验收口成统一流程的样板，和 Example 9.15 抛硬币检验是同一套骨架。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 29**</span>

The values of five independent samples of a Poisson random variable turned out to be 34, 35, 29, 31, and 30. Test the hypothesis that the mean is equal to 35 at the 5% level of significance.

> <span style="color:#1e8449;">**[t_note]** 注：泊松变量的显著性检验，样本均值是天然统计量。先证：$H_0:\lambda=35$ 下样本和 $\sum_iX_i\sim$ 泊松$(5\times35=175)$ 或近似正态，样本均值 $\bar X=31.8$；用正态近似 $Z=(\bar X-35)/\sqrt{35/5}$（泊松均值=方差），看其落在哪个拒绝域。这题的真正难点是**小样本 + 未知到底应该多大才算显著**——因为泊松在均值较大时已基本对称，直接借 CLT。多做一步：样本均值 $\bar X$ 的方差是 $\lambda/n=35/5=7$，标准误约 2.65，$|\bar X-35|=3.2$ 约 1.2 个标准误，5% 下不显著。这教你『先估方差、再标准化、再比临界』的通用三步。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#2471a3;">**Problem 30**</span>

A surveillance camera periodically checks a certain area and records a signal $X = W$ if there is no intruder (this is the null hypothesis $H_0$). If there is an intruder the signal is $X = \theta + W$, where $\theta$ is unknown with $\theta > 0$. We assume that $W$ is a normal random variable with mean 0 and known variance $v = 0.5$.

(a) We obtain a single signal value $X = 0.96$. Should $H_0$ be rejected at the 5% level of significance?

(b) We obtain five independent signal values $X = 0.96, -0.34, 0.85, 0.51, 0.24$. Should $H_0$ be rejected at the 5% level of significance?

(c) Repeat part (b), using the t-distribution, and assuming the variance $v$ is unknown.

> <span style="color:#1e8449;">**[t_note]** 注：(a)→(b)→(c) 是一条刻意铺好的递进：单个信号用正态（$v$ 已知）→ 五个独立信号取均值仍用正态 → 五样本把未知 $v$ 换成样本方差后转 $t$ 分布。先证：(b) 与 (a) 的区别只在样本均值将方差缩小成 $v/5$，标准误更小、误拒对信号更敏感；(c) 则彻底释放『方差未知』，$T=(\bar X-0)/(\hat\sigma/\sqrt n)$（标准误用样本标准差）在 $H_0$ 下服从自由度 $n-1$ 的 $t$ 分布，临界值取自 $t$ 表而非正态表。这正把 Example 9.16 末尾『未知方差用 $t$』的话接到实践上：$n=5$ 偏小，$t$ 表与正态表差异明显，不能混用。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] Problem 30 中无入侵者时信号作 "$X = W$"，源 OCR 将噪声记号 $W$ 读作 "$a$"/"IV"，此处按上下文（$W$ 已定义为已知方差 $v=0.5$ 的正态噪声）规范复原为 $W$。</span>

> <span style="color:#7f8c8d;">本页为第 9 章习题区之终点；下一页（PDF p528，书页 521）进入全书后页书的 **Index 索引**。</span>

---

<!-- ===== PDF p528 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p528 − 7 = 书页 521，属全书后页书（Back Matter）的 **Index 索引**。索引为按字母排序的词表 + 页码定位（书页 521–528），非正文散文，故按 §7 索引特例处理：保留字母分区，每个词条写成 `English term（中文）` 行内双语，页码列表原样保留、不译、不增删；缩进的从属子词条同理。原文为双栏排版，OCR 以单栏顺序输出，故词条原始栏间次序可能交错，下方按字母归组整理；页码中被打碎的整数（如 "4 1 7"）已规范回原整数（如 417）。</span>

> <span style="color:#1e8449;">**[t_note]** 注：用好索引的关键在读懂它的『三件套』：主词条 + 缩进子词条 + 页码。先证：字母 A–Z 分区是按英文术语首字母排的，所以中文读者查词时先想它的英文名；主词条下面缩进的是其子主题（如 Bernoulli process 下的 memorylessness、splitting…），页码指向该概念的首次/关键出现页（书页号，非 PDF 页码）。"see"（见）与"see also"（另见）是交叉引用的路标，比如『Kernel, see MAP』意思是要到 MAP 词条下去找。跨课程（离散数学·查找=已知键值检索）：索引本质是一棵按字母组织的搜索树，查词就是走分支，学会读『see/另见』能让你绕开重复定义、直达权威条目。</span>

## A

- Absorbing state（吸收态）, 346, 362
- Absorption probabilities（吸收概率）, 362, 397
- Acceptance region（接受域）, 486
- Accessible state（可达状态）, 347
- Additivity axiom（可加性公理）, 9
- Almost surely（几乎必然，almost surely）, 281
- Aperiodic recurrent class（非周期常返类）, 350
- Asymptotic normality（渐近正态性）, 465, 470
- Axioms（公理）, 9, 17

## B

- Balance equations（平衡方程）, 353, 375, 399
  - local（局部的）, 359, 377, 393
  - uniqueness of solutions（解的唯一性）, 354, 389
- Bayes（贝叶斯）, 17
- Bayes' rule（贝叶斯法则）, 31, 413
  - continuous（连续情形）, 178
- Bayesian inference（贝叶斯推断）, 408, 411
- Bernoulli, Daniel（丹尼尔·伯努利）, 17
  - problem of joint lives（共同寿命问题）, 128
- Bernoulli–Laplace model of diffusion（伯努利–拉普拉斯扩散模型）, 386
- Bernoulli, Jacob（雅各布·伯努利）, 17
- Bernoulli process（伯努利过程）, 297
  - alternative description（另一种描述）, 302
  - definition（定义）, 297
  - fresh-start at random time（随机时刻的全新开始）, 301
  - fresh-start property（全新开始性质）, 299
  - independence（独立性）, 298
  - interarrival times（到达间隔时间）, 302
  - memorylessness（无记忆性）, 298
  - merging（合并）, 305
  - number of successes（成功次数）, 298
  - Poisson approximation（泊松近似）, 305
  - random incidence in（其中随机到达数量）, 327
  - relation to uniform r.v.（与均匀随机变量的关系）, 328
  - splitting（分裂）, 305
  - time until first success（到首次成功的时间）, 298
  - time until kth success（到第 $k$ 次成功的时间）, 303
- Bernoulli r.v.（伯努利随机变量）, 75, 116
  - mean（均值）, 88
  - sum of（其和）, 96, 261
  - transform（变换）, 237, 239
  - variance（方差）, 88
- Bernoulli trial（伯努利试验）, 41
- Bertrand's paradox（伯特兰悖论）, 16
- Beta（贝塔分布）
  - density（密度）, 194, 417
  - function（函数）, 417
  - moments（各阶矩）, 194
  - posterior（后验）, 425, 434
  - prior（先验）, 417
- Bias（偏差）, 225, 461
- Binomial（二项分布）
  - coefficient（二项式系数）, 43, 48, 65
  - formula（公式）, 43, 48
  - dependence（相关性）, 393
  - probabilities（概率）, 43
- Binomial r.v.（二项随机变量）, 77, 116, 298
  - de Moivre–Laplace approximation（棣莫弗–拉普拉斯近似）, 277
  - mean（均值）, 96
  - Poisson approximation（泊松近似）, 79, 121
  - recursive calculation of PMF（PMF 的递推计算）, 120
  - transform（变换）, 237, 239
  - variance（方差）, 113
- Birth–death process（生灭过程）, 359, 377
- Birthday problem（生日问题）, 67
- Bivariate normal（二元正态）, 254
- Bonferroni's inequality（邦费罗尼不等式）, 55
- Borel–Cantelli lemma（博雷尔–坎泰利引理）, 66
- Buffon's needle（蒲丰投针）, 161, 190, 451

## C

- Cantor's diagonalization（康托尔对角化方法）, 53
- Cardano（卡尔达诺）, 17
- Cauchy r.v.（柯西随机变量）, 247
- Causality（因果性）, 485
- CDF（累积分布函数，cumulative distribution function）, 148
  - joint（联合）, 162
  - properties（性质）, 150
- Central limit theorem（中心极限定理）, 158, 264, 273
  - history（历史）, 17
  - proof（证明）, 290
- Chain, see Markov chain（链，见马尔可夫链）
- Chapman–Kolmogorov equation（查普曼–柯尔莫哥洛夫方程）, 345, 353
- Chebyshev（切比雪夫）, 17
- Chebyshev inequality（切比雪夫不等式）, 267, 268
- Chernoff bound（切尔诺夫界）, 284
- Chi-square（卡方）
  - distribution（分布）, 504
  - test（检验）, 505
- Classical inference（经典推断）, 408, 459
- Classification of states（状态分类）, 346

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 索引为双栏排版，OCR 单栏输出使个别子词条（如 Binomial 下的 "dependence, 393"）来源归属难以完全确定，此处按 OCR 就近归入并保留页码。字母 C 的其余词条延续至下一页（PDF p529，书页 522）。</span>

---

<!-- ===== PDF p529 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p529 − 7 = 书页 522，Index 索引续页，含字母 **C（后段）→ D → E（至 Expectation 的 "of continuous r.v." 为止）**。页码列表原样保留、不译、不增删；被打碎整数已规范回原整数（如 "2 1 8"→218、'836'）见灰注。Expectation 词条的中段延续到下一页（PDF p530）。</span>

> <span style="color:#7f8c8d;">[原页此处 OCR 碎裂] 双栏排版使 OCR 单栏输出交错，"Ehrenfest model of diffusion , 836" 中的页码 "836" 应为 "386"（与前文 386 一致），此处规范回 386。另 "De Mere" 为 de Méré 之 OCR 形。索引为参考件，按 §7 处理。</span>

## C

- Collectively exhaustive（完全穷尽）, 7
- Combination（组合）, 46, 47
- Competing exponentials（竞争性指数变量）, 247, 319
- Composite hypothesis（复合假设）, 459, 500, 502
- Conditional（条件）
  - expectation, see expectation, conditional（期望，见"期望，条件"）
  - independence（独立性）, 36, 110
  - mean squared error（均方误差）, 425, 430
  - PDF, see conditional PDF（概率密度，见"条件概率密度"）
  - PMF, see conditional PMF（概率质量函数，见"条件概率质量函数"）
  - probability（概率）, 18
  - variance（方差）, 104, 226
- Conditioning（取条件）
  - continuous r.v. on an event（连续随机变量关于事件）, 165
  - continuous r.v. on another（连续随机变量关于另一随机变量）, 169
  - discrete r.v. on an event（离散随机变量关于事件）, 98
  - discrete r.v. on another（离散随机变量关于另一随机变量）, 99
- Confidence interval（置信区间）, 468
  - approximate（近似的）, 470
- Confidence level（置信水平）, 468
- Consistent（一致的/相合的）, 461
- Continuity property of probabilities（概率的连续性性质）, 56
- Continuous random variable, see random variable（连续随机变量，见"随机变量"）
- Convergence（收敛）
  - in probability（依概率收敛）, 271, 282, 288
  - in the mean square（均方收敛）, 289
  - of a deterministic sequence（确定性序列的收敛）, 271
  - with probability one（以概率 1 收敛）, 281
- Convolution（卷积）, 213
  - graphical calculation（图解计算）, 216
- Correlation coefficient（相关系数）, 219, 250
- Covariance（协方差）, 218
- Countably infinite（可数无穷）, 3, 82
- Counting（计数）
  - principle（原理）, 44
- Critical value（临界值）, 487, 497, 498
- Cumulative distribution function, see CDF（累积分布函数，见 CDF）

## D

- de Méré（德梅雷）, 62, 67
- De Moivre（棣莫弗）, 17
- De Moivre–Laplace approximation（棣莫弗–拉普拉斯近似）, 277
- De Morgan's laws（德摩根定律）, 5, 53
- Decomposition, Markov chains（马尔可夫链分解）, 349
- Density, see PDF（密度，见 PDF）
- Derived distributions（导出分布）, 202
  - of function of two r.v.'s（两个随机变量的函数）, 209
  - of monotonic function（单调函数）, 207
- Detection（检测）, 22, 33, 157, 180, 428, 490
- Difference of independent r.v.'s（独立随机变量之差）, 216
- Diffusion（扩散）
  - Bernoulli–Laplace model（伯努利–拉普拉斯模型）, 386
  - Ehrenfest model（艾伦费斯特模型）, 386
- Discrete probability law（离散概率律）, 11
- Discrete random variable, see random variable（离散随机变量，见"随机变量"）
- Discrete uniform probability law（离散均匀概率律）, 11
- Discrete uniform random variable, see uniform（离散均匀随机变量，见"均匀"）
- Distribution（分布）
  - posterior（后验）, 409, 412
  - prior（先验）, 409
- Doubly stochastic（双随机的）, 391

## E

- Efficient frontier（有效前沿）, 492
- Ehrenfest model of diffusion（艾伦费斯特扩散模型）, 386
- Empirical frequency（经验频率）, 270
- Entropy（熵）, 135
- Erlang process（厄朗过程）, 337
- Erlang r.v.（厄朗随机变量）, 316
- Error（误差/错误）
  - Type I（第一类）, 486
  - Type II error（第二类错误）, 486
- Estimate（估计值）, 422, 423
  - point（点估计）, 422
- Estimation（估计）
  - error（误差）, 225, 435, 436, 461
  - of mean（均值）, 468
  - of mean of Bernoulli（伯努利均值）, 463
  - of mean of normal（正态均值）, 415, 421, 464
  - of multiple parameters（多参数）, 436, 442
  - of variance（方差）, 468
  - of variance of normal（正态方差）, 464
  - parameter（参数）, 411, 459
  - parameter of exponential（指数参数）, 464
  - parameter of Poisson（泊松参数）, 449
  - point（点）, 422
  - problem（问题）, 410
- Estimator（估计量）, 225, 423, 460
  - asymptotically（渐近的）, 461
  - bias（有偏）, 461
  - conditional expectation（条件期望）, 423
  - consistent（一致的）, 461
  - linear（线性的）, 438
  - LMS, 424
  - MAP, 423
  - unbiased（无偏的）, 436, 461
- Event（事件）, 6, 7
  - independent（独立事件）, 34
- Expectation（期望）
  - as center of gravity（作为重心）, 83
  - conditional（条件期望）, 104, 179, 225
  - as estimator（作为估计量）, 225, 423
  - linearity（线性）, 87, 94, 96, 97, 130, 145, 163, 164
  - of continuous r.v.（连续随机变量的期望）, 144, 184

> <span style="color:#7f8c8d;">"Expectation" 词条的其余子项（of discrete r.v. 等）延续到下一页（PDF p530，书页 523）。</span>

---

<!-- ===== PDF p530 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p530 − 7 = 书页 523，Index 索引续页。承接上一页（PDF p529）的 **Expectation** 词条之剩余子项，随后为字母 **F → G → H → I（至 Iterated expectations, law of, 223 为止）**。页码列表原样保留、不译、不增删。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 双栏排版交错使个别子项栏位轻微错位（如 Exponential 下的 "two-sided, 193, 213" 按 OCR 就近归入），页码 "97"、"4 1 7" 等已规范回整数值。此页属随机变量符号（"$\theta=0.5$" 等）无显式破坏处。</span>

## E

- Expectation（期望）（续）
  - of discrete r.v.（离散随机变量的期望）, 81, 82, 184
  - of function of r.v., see expected value rule（随机变量函数的期望，见"期望值法则"）
  - sum of a geometric number（几何参数之和的期望）, 244, 328
  - transform（期望的变换）, 235, 239
  - variance（期望与方差）, 105
  - well-defined（良定义的）, 82, 144
- Expected time to absorption（到吸收的期望时间）, 366
- Expected value, see expectation（期望值，见"期望"）
- Expected value rule（期望值法则）
  - for continuous r.v.'s（对连续随机变量）, 145, 163, 173, 185
  - for discrete r.v.'s（对离散随机变量）, 84, 94, 96, 97, 130
- Experiment（随机试验）, 6
- Exponential random variable（指数随机变量）, 146, 182
  - CDF（累积分布函数）, 152
  - in Markov chain（在马尔可夫链中）, 370
  - in Poisson process（在泊松过程中）, 312
  - linear function of（的线性函数）, 206
  - maximum of（的最大值）, 332
  - mean（均值）, 147
  - memorylessness（无记忆性）, 165
  - minimum of（的最小值）, 247, 319
  - moments（各阶矩）, 256
  - relation to geometric（与几何分布的关系）, 152
  - sum of a geometric number（几何个数之和）, 243, 335
  - transform（变换）, 231, 239
  - two-sided（双边）, 193, 213
  - variance（方差）, 147

## F

- Factorization criterion（因子分解准则）, 509
- False acceptance（误接受）, 486
- False-positive puzzle（假阳性悖论）, 33
- False rejection（误拒绝）, 486
- Fermat（费马）, 17, 62
- First passage time（首次通过时间）, 367, 398
- Flat prior（均匀/平坦先验）, 463
- Frequency interpretation of probabilities（概率的频率解释）, 2, 9, 17, 270, 281
- Frequentist approach（频率派方法）, 408
- Function of a r.v.（随机变量的函数）, 74, 80, see also derived distributions（另见"导出分布"）
  - mean, see expected value rule（均值，见"期望值法则"）
- Function of multiple r.v.'s（多元随机变量的函数）
  - continuous case（连续情形）, 164
  - discrete case（离散情形）, 93

## G

- Gambler's ruin（赌徒破产）, 63, 364
- Gauss（高斯）, 17
- Gaussian r.v., see normal r.v.（高斯随机变量，见"正态随机变量"）
- Generalized likelihood ratio test（广义似然比检验）, 502
- Geometric r.v.（几何随机变量）, 77, 116, 134, 298
  - CDF（累积分布函数）, 151
  - mean（均值）, 105
  - relation to exponential（与指数分布的关系）, 151
- Goodness of fit（拟合优度）, 502
- Grade of service（服务等级）, 43

## H

- Hat problem（帽子问题）, 96, 221
- Heteroskedasticity（异方差性）, 484
- History of probability（概率历史）, 17
- Hypergeometric probabilities（超几何概率）, 69
- Hypothesis（假设）
  - alternative（备择假设）, 485, 496
  - composite（复合假设）, 459, 500, 502
  - null（原假设）, 485, 496
  - simple（简单假设）, 496
- Hypothesis testing（假设检验）, 411, 459
  - Bayesian（贝叶斯）, 420, 425
  - binary（二元）, 411, 485
  - for equality of means（均值相等性）, 500
  - for zero mean（零均值）, 500
  - m-ary（$m$ 元）, 411

## I

- i.i.d.（独立同分布）, 458
- Inclusion-exclusion formula（容斥公式）, 55, 126
- Independence（独立性）
  - conditional（条件）, 36, 111
  - of continuous r.v.'s（连续随机变量）, 175
  - of discrete r.v.'s（离散随机变量）, 111
  - of events（事件）, 34
  - of functions of r.v.'s（随机变量函数）, 111, 134, 177
  - of r.v. from an event（随机变量与事件）, 109
  - of several events（多个事件）, 38
  - pairwise（两两）, 39
- Independent trials（独立试验）, 41
- Indistinguishable objects（不可区分对象）, 69
- Inequality（不等式）
  - Chebyshev（切比雪夫）, 267
  - Chernoff bound（切尔诺夫界）, 284
  - Jensen（詹森）, 287
  - Markov（马尔可夫）, 265
  - Schwarz（施瓦茨）, 250
- Inference（推断）
  - Bayesian（贝叶斯）, 408, 411
  - Classical（经典）, 408, 459
  - multiparameter（多参数）, 418
  - recursive（递推）, 416
- Invariance principle（不变性原理）, 465
- Inversion property（反演性质）, 234, 240
- Iterated expectations, law of（迭代期望定律）, 223

> <span style="color:#7f8c8d;">本页（书页 523）索引止于 "Iterated expectations"。Index 后续字母与词条位于之后的书页（524–528），不在本页范围。</span>

---

<!-- ===== PDF p531 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p531 − 7 = 书页 524，Index 索引续页。承接上一页（PDF p530）的 **I** 部分，本页含字母 **J → K → L → M（至 "Markov inequality, 265" 为止）**。页码列表原样保留、不译、不增删；被打碎整数已规范回原整数（如 "1 58"→158、"1 6 1"→161、"2 1 3"→213、'1 45'→145）。M 部分的中段延续到下一页（PDF p532）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 双栏排版使 OCR 单栏输出交错，"Least squares estimation, 1 7" 与 "Legendre, 1 7"、"Leibnitz, 1 7"、"Lyapunov, 1 7" 等处的 `1 7` 均为 `17` 之 OCR 形；另 "Linear least mean squares estimation" 页码在 OCR 中重复打印（"412, 437, 438, 412, 437, 438"），此处按单个序列 "412, 437, 438" 规范。索引为参考件，按 §7 处理。</span>

## J

- Jensen inequality（詹森不等式）, 287
- Joint PDF（联合概率密度）, 158
- Joint PMF（联合概率质量）, 92

## K

- Kelly strategy（凯利策略）, 251
- King's sibling（国王的兄弟）, 61

## L

- Lagrange（拉格朗日）, 17
- Laplace（拉普拉斯）, 17, 161, 190
- Laplace r.v.（拉普拉斯随机变量）, 184, 213
- Laplace transform（拉普拉斯变换）, 230
- Laplace's rule of succession（拉普拉斯连续律）, 64
- Law of iterated expectations（迭代期望定律）, 223
- Law of large numbers（大数定律）
  - weak（弱）, 269
  - strong（强）, 280, 294, 403
- Law of total variance（全方差定律）, 226
- Least mean squares（最小均方）
  - estimator（估计量）, 424, 431
  - estimation（估计）, 412, 430
  - multiple observations（多观测）, 436
  - multiple parameters（多参数）, 436
- Least squares estimation（最小二乘估计）, 17
- Likelihood function（似然函数）, 462
- Likelihood ratio（似然比）, 487
- Likelihood ratio test（似然比检验）, 460, 489
  - generalized（广义的）, 502
- Limit, see convergence（极限，见"收敛"）
- Linear least mean squares estimation（线性最小均方估计）, 412, 437, 438
  - and regression（与回归）, 479
  - error（误差）, 439
  - formulas（公式）, 439
  - multiple observations（多观测）, 442, 453
  - multiple parameters（多参数）, 442
  - normal models（正态模型）, 443
  - properties（性质）, 455, 457
  - two observations（双观测）, 452
- Linear regression, see regression（线性回归，见"回归"）
- Legendre（勒让德）, 17
- Leibnitz（莱布尼茨）, 17
- Linear function of r.v.'s（随机变量的线性函数）
  - mean, 87, see also expectation, linearity（均值，87，另见"期望，线性"）
  - normal（正态）, 154
  - PDF（概率密度）, 205
  - transform（变换）, 231
  - variance（方差）, 87, 145
- LMS, see least mean squares（LMS，见"最小均方"）
- Local balance equations（局部平衡方程）, 359, 377, 393
- Localization（定位/局部化）, 418
- Log-likelihood function（对数似然函数）, 462
- LRT, see likelihood ratio test（LRT，见"似然比检验"）
- Lyapunov（李雅普诺夫）, 17

## M

- MAP estimator（MAP 估计量）, 423
- MAP rule（MAP 准则）, 411, 420, 421
  - for hypothesis testing（用于假设检验）, 426
- Marginal（边缘）
  - PDF（边缘概率密度）, 159
  - PMF（边缘概率质量）, 93
- Markov（马尔可夫）, 17
- Markov chain in continuous time（连续时间马尔可夫链）, 369
  - alternative description（另一种描述）, 373
  - assumptions（假设）, 370
  - balance equations（平衡方程）, 375
  - birth-death（生灭）, 377
  - definition（定义）, 370
  - discrete-time approximation（离散时间近似）, 372
  - embedded chain（嵌入链）, 370
  - local balance equations（局部平衡方程）, 377
  - steady-state（稳态）, 375
  - steady-state convergence theorem（稳态收敛定理）, 375
  - transition rate（转移率）, 371
- Markov chain in discrete time（离散时间马尔可夫链）, 340
  - absorption probabilities（吸收概率）, 362, 397
  - balance equations（平衡方程）, 353, 389
  - birth-death（生灭）, 359
  - Chapman–Kolmogorov equation（查普曼–柯尔莫哥洛夫方程）, 345, 353
  - classification（分类）, 346
  - decomposition（分解）, 349
  - definition（定义）, 341
  - expected state frequencies（期望状态频率）, 357, 390
  - expected time to absorption（到吸收的期望时间）, 366
  - expected transition frequencies（期望转移频率）, 358
  - first passage time（首次通过时间）, 398, 367
  - local balance equations（局部平衡方程）, 359, 393
  - multiple recurrent classes（多个常返类）, 398
  - n-step transition probability（$n$ 步转移概率）, 345
  - normalization equation（归一化方程）, 354
  - periodicity（周期性）, 351, 383
  - probability of a path（一条路径的概率）, 343
  - recurrence time（回归时间）, 367, 399
  - sampled（采样）, 394
  - stationary distribution（平稳分布）, 353
  - steady-state（稳态）, 352
  - steady-state convergence theorem（稳态收敛定理）, 352, 387
  - strong law of large numbers（强大数定律）, 402
  - transition graph（转移图）, 341
  - transition matrix（转移矩阵）, 341, 345
  - transition probability（转移概率）, 340
- Markov inequality（马尔可夫不等式）, 265

> <span style="color:#7f8c8d;">"Markov inequality" 之后的 M 部分（Markov model 起）延续到下一页（PDF p532，书页 525）。</span>

---

<!-- ===== PDF p532 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p532 − 7 = 书页 525，Index 索引续页。承接上一页（PDF p531）的 **M** 之后段（Markov model 起），随后为字母 **N → O → P（至 PDF 的 "properties, 144" 为止）**。页码列表原样保留、不译、不增删；被打碎整数已规范回原整数（如 "4 1 1"→411、"1 7 6"→176、"1 5 3"→153、'1 24'→124、'1 76'→176）。P 的中段延续到下一页（PDF p533）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 双栏排版使 OCR 单栏输出交错，"mUltiple recurrent classes" 拼写碎裂（应为 multiple）；"fiat, 463" 为 "flat, 463" 之 OCR 形；"distri butions" 为 "distributions" 之 OCR 断行。索引为参考件，按 §7 处理。</span>

## M

- Markov model（马尔可夫模型）, 341
- Markov property（马尔可夫性质）, 340
- Matchbox problem（火柴盒问题）, 120
- Matched filter（匹配滤波器）, 428
- Matrix（矩阵）
  - doubly stochastic（双随机）, 391
  - transition（转移）, 341, 345
- Maximum a Posteriori, see MAP（最大后验，见 MAP）
- Maximum likelihood（极大似然）, 459, 462
  - asymptotic normality（渐近正态性）, 465
  - consistency（一致性）, 465
  - in regression（在回归中）, 478
  - invariance principle（不变性原理）, 465
- Maximum of r.v.'s（随机变量的最大值）, 150
- Mean, see expectation（均值，见"期望"）
- Mean first passage time（平均首次通过时间）, 367, 398
- Mean recurrence time（平均回归时间）, 367, 399
- Mean squared error（均方误差）, 430, 431
  - conditional（条件的）, 425, 430
- Measurement（测量）, 412
- Merging（合并）
  - Bernoulli processes（伯努利过程）, 305
  - Poisson processes（泊松过程）, 319
- Minimum of r.v.'s（随机变量的最小值）, 124
- Mixed r.v.（混合随机变量）, 186
- Mixture of distributions（分布混合）, 236
- ML, see maximum likelihood（ML，见"极大似然"）
- Model inference（模型推断）, 409
- Moment（矩）, 83, 145
  - calculation using transforms（利用变换计算）, 232
- Moment generating function（矩生成函数）, 229, 232
  - see also transform（另见"变换"）
- Monotone convergence theorem（单调收敛定理）, 293
- Monotonic function of a r.v.（随机变量的单调函数）, 207
- Monty Hall problem（蒙提霍尔问题）, 27
- Multicollinearity（多重共线性）, 484
- Multiple regression（多元回归）, 482
- Multinomial（多项）
  - coefficient（系数）, 49
  - distribution（分布）, 124, 503
- Multiplication rule（乘法法则）
  - for PDFs（对概率密度）, 172, 194
  - for PMFs（对概率质量）, 101, 103, 131
  - for probabilities（对概率）, 24
- Multivariate transform（多元变换）, 240
- Mutual information（互信息）, 137
- Mutually exclusive（互斥）, 7

## N

- Negative binomial r.v.（负二项随机变量）, 327
- Neyman–Pearson lemma（内曼–皮尔逊引理）, 491
- Nonlinear regression（非线性回归）, 483
- Nonnegativity axiom（非负性公理）, 9
- Nonparametric problem（非参数问题）, 411
- Normal approximation（正态近似）, 275
- Normal r.v.（正态随机变量）
  - bivariate（二元）, 254
  - CDF（累积分布函数）, 154
  - central limit theorem（中心极限定理）, 273
  - confidence interval（置信区间）, 469
  - estimation（估计）, 415, 421, 449, 464
  - independent（独立的）, 176
  - linear function of（的线性函数）, 154, 206
  - mean（均值）, 153
  - model（模型）, 443
  - normalization property（归一化性质）, 153, 189
  - standard（标准）, 154
  - sum of（的和）, 214, 238
  - table（表）, 155
  - transform（变换）, 231, 239
  - uncorrelated（不相关的）, 254
  - variance（方差）, 153
- Normalization axiom（归一化公理）, 9
- Normalization equation, in Markov chains（归一化方程，马尔可夫链中）, 354
- Null hypothesis（原假设）, 485, 496

## O

- Observation（观测）, 412
- Ordered pair（有序对）, 5
- Outcome（结果）, 6
  - mutually exclusive（互斥的）, 7
- Overfitting（过拟合）, 484

## P

- p-value（p 值）, 499
- Pairwise independence（两两独立）, 39
- Paradox（悖论）
  - Bertrand's（伯特兰）, 16
  - of induction（归纳）, 58
  - random incidence（随机到达）, 322
  - St. Petersburg（圣彼得堡）, 123
  - two-envelopes（双信封）, 106
- Parallel connection（并联）, 41
- Parametric model（参数模型）, 496
- Partition（划分）, 4, 49
- Pascal（帕斯卡）, 17, 62, 65
- Pascal r.v.（帕斯卡随机变量）, 303, 327
- Pascal triangle（帕斯卡三角形）, 65
- PDF（概率密度函数）, 140
  - conditional（条件的）, 165, 167, 169, 172
  - joint（联合）, 158
  - marginal（边缘）, 159
  - of function of r.v.'s, see derived distributions（随机变量函数的，见"导出分布"）
  - of linear function of r.v.'s（随机变量线性函数的）, 205
  - of monotonic function of r.v.'s（随机变量单调函数的）, 207

> <span style="color:#7f8c8d;">PDF 词条的其余子项（properties 起）延续到下一页（PDF p533，书页 526）。</span>

---

<!-- ===== PDF p533 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p533 − 7 = 书页 526，Index 索引续页。承接上一页（PDF p532）的 **P**（PDF 的 "properties" 起），随后为字母 **Q → R（至 Regression 的 "overfitting, 484" 为止）**。页码列表原样保留、不译、不增删；被打碎整数已规范回原整数（如 "5 1 1"→511、'31 1'→311、'1 28'→128、'1 78'→组内 178 等）。R 的中段延续到下一页（PDF p534）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 双栏排版使 OCR 单栏输出交错，"fiat, 463" 表 "flat, 463"（Prior 下）。索引为参考件，按 §7 处理。</span>

## P

- PDF（概率密度函数）
  - properties（性质）, 144
  - spherically invariant（球对称不变）, 451
- Periodic class（周期类）, 351, 383
- Permutation（排列）, 46, 69
  - k-permutation（$k$ 排列）, 46
- Perron–Frobenius theorem（佩龙–弗罗贝尼乌斯定理）, 354
- Piecewise constant PDF（分段常数概率密度）, 142
  - mean（均值）, 174
  - variance（方差）, 174
- PMF（概率质量函数）, 74
  - calculation of（的计算）, 75
  - conditional（条件的）, 98, 100
  - summary（汇总）, 103
  - joint（联合）, 92
  - marginal（边缘）, 93
- Point estimate（点估计）, 422
- Poisson（泊松）, 17
- Poisson process（泊松过程）, 297, 309
  - alternative description（另一种描述）, 316
  - arrival rate（到达率）, 310
  - definition（定义）, 310
  - independence（独立性）, 310, 314
  - intensity（强度）, 310
  - interarrival times（到达间隔时间）, 315
  - memorylessness（无记忆性）, 314
  - merging（合并）, 319
  - number of arrivals（到达次数）, 311, 335
  - random incidence（随机到达）, 322
  - small interval probabilities（小区间概率）, 310
  - splitting（分裂）, 318, 336
  - time-homogeneity（时间齐次性）, 310
  - time until first arrival（到首次到达的时间）, 312
  - time until kth arrival（到第 $k$ 次到达的时间）, 316
- Poisson random variable（泊松随机变量）, 78, 117, 312
  - approximation of binomial（二项分布的近似）, 79, 121
  - mean（均值）, 90
  - parameter estimation（参数估计）, 449
  - splitting（分裂）, 132
  - sum of（的和）, 237, 247, 313
  - transform（变换）, 230, 239
  - variance（方差）, 113
- Polling（民意调查）, 270, 276, 474
- Posterior（后验）, 32, 409, 412
- Prior（先验）, 32, 409
  - flat（平坦的）, 463
- Prisoner's dilemma（囚徒困境）, 58
- Probabilistic model（概率模型）, 6
- Probability（概率）
  - conditional（条件的）, 18
  - history（历史）, 17
  - steady-state, see steady-state probability（稳态，见"稳态概率"）
  - subjective（主观）, 3
- Probability density function, see PDF（概率密度函数，见 PDF）
- Probability mass function, see PMF（概率质量函数，见 PMF）
- Probability law（概率律）, 6, 8
  - of random variable（随机变量的）, 148
  - properties（性质）, 14
- Problem of joint lives（共同寿命问题）, 128
- Problem of points（赌注分配问题）, 62
- Process（过程）
  - arrival（到达）, 296
  - Bernoulli（伯努利）, 297
  - birth–death（生灭）, 359, 377
  - Erlang（厄朗）, 337
  - Markov（马尔可夫）, 297
  - Poisson（泊松）, 297, 309

## Q

- Queueing（排队）, 336, 348, 365, 373, 392
- Quiz problem（测验问题）, 91, 125

## R

- Random incidence（随机到达）
  - in Bernoulli process（在伯努利过程中）, 327
  - in Erlang process（在厄朗过程中）, 337
  - in Poisson process（在泊松过程中）, 322
  - in non-Poisson process（在非泊松过程中）, 323
- Random variable（随机变量）
  - continuous（连续）, 140
  - definition（定义）, 73
  - discrete（离散）, 73, 74
  - function of（的函数）, 73, 74, 80, 93, 202
  - independent（独立的）, 110, 175, 177
  - mixed（混合）, 186
- Random walk（随机游走）, 360
- Rao–Blackwell theorem（Rao–Blackwell 定理）, 511
- Rayleigh r.v.（瑞利随机变量）, 248
- Recurrence time（回归时间）, 367, 399
- Recurrent（常返）
  - class（类）, 348
  - aperiodic（非周期的）, 350
  - multiple（多个）, 398
  - periodic（周期的）, 350
  - state（状态）, 347, 382
  - existence（存在性）, 381
- Recursive inference（递推推断）, 416
- Regression（回归）
  - Bayesian（贝叶斯）, 480, 481
  - causality（因果性）, 485
  - consistency（一致性）, 514
  - formulas（公式）, 477
  - heteroskedasticity（异方差性）, 484
  - linear（线性）, 459, 475
  - multicollinearity（多重共线性）, 484
  - nonlinear（非线性）, 483
  - nonlinearity（非线性）, 484
  - overfitting（过拟合）, 484

> <span style="color:#7f8c8d;">Regression 词条的其余子项（multiple 起）延续到下一页（PDF p534，书页 527）。</span>

---

<!-- ===== PDF p534 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p534 − 7 = 书页 527，Index 索引续页。承接上一页（PDF p533）的 **R**（Regression 的 "multiple" 起）与 **S**（至 Transition 的 "graph, 341" 为止，T 段部分）。页码列表原样保留、不译、不增删；被打碎整数已规范回原整数（如 "5 1 4"→514、'1 15'→115、'31 1'→311）。S 的剩余部分（Transition matrix 起）延续到下一页（PDF p535，书页 528）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 双栏排版使 OCR 单栏输出交错，"Schwartz inequality" 与正文 "Schwarz inequality" 存在 OCR 拼写差异，此处在索引中按原文 "Schwartz" 保留。"mUltiple"、"1 1 1 , 1 12, 1 13" 等已规范。索引为参考件，按 §7 处理。</span>

## R

- Regression（回归）
  - multiple（多元）, 482
  - simple（一元）, 482
  - unbiasedness（无偏性）, 514
  - variance estimate（方差估计）, 518
- Rejection region（拒绝域）, 486, 497, 498
- Relative frequency（相对频率）, 9, 17, see also frequency interpretation（另见"频率解释"）
- Reliability（可靠性）, 40, 61
- Residual（残差）, 476
- Reversibility（可逆性）, 394

## S

- Sample mean（样本均值）, 114, 264, 466
  - mean（均值）, 114, 264
  - unbiased（无偏）, 466
  - variance（方差）, 114, 264
- Sample space（样本空间）, 6
  - uncountable（不可数）, 7
- Schwartz inequality（施瓦茨不等式）, 250
- Sequential model（顺序模型）, 8, 22
- Sequential method（序贯方法）, 52
- Series connection（串联）, 41
- Set（集合）, 3
  - complement（补集）, 4
  - countably infinite（可数无穷）, 3
  - disjoint（不相交）, 4
  - element of（元素）, 3
  - empty（空集）, 3
  - intersection（交集）, 4
  - partition（划分）, 4
  - uncountable（不可数）, 4
  - union（并集）, 4
  - universal（全集的）, 4
- Shannon（香农）, 136
- Signal detection, see detection（信号检测，见"检测"）
- Significance level（显著性水平）, 497, 498
- Significance testing（显著性检验）, 459, 460, 495
- Simulation（模拟）, 115, 188, 190, 196, 489, 499
- Spherically invariant PDF（球对称不变概率密度）, 451
- Splitting（分裂）
  - Bernoulli process（伯努利过程）, 305
  - Poisson r.v.（泊松随机变量）, 132
  - Poisson process（泊松过程）, 318, 336
- St. Petersburg paradox（圣彼得堡悖论）, 123
- Standard deviation（标准差）, 83, 86
- Standard normal random variable（标准正态随机变量）, 154
- Standard normal table（标准正态表）, 155
  - use for calculating normal CDF（用于计算正态累积分布函数）, 156
- State（状态）
  - absorbing（吸收）, 346, 362
  - accessible（可达）, 347
  - classification（分类）, 346
  - of Markov chain（马尔可夫链的）, 340
  - recurrent（常返）, 347, 381, 382
  - transient（暂态）, 347, 381
- State space（状态空间）, 340
- Stationary distribution（平稳分布）, 353
- Statistic（统计量）, 497
  - sufficient（充分）, 509, 511
- Statistics（统计学）, 408
  - Bayesian（贝叶斯）, 408, 411, 412
  - classical（经典）, 408, 459
  - frequentist（频率派）, 408
  - nonparametric（非参数）, 411
- Steady-state, in Markov chains（稳态，马尔可夫链中）, 352, 375
- Steady-state convergence theorem（稳态收敛定理）, 352, 375, 387
- Steady-state probability（稳态概率）, 352, 375
- Stochastic process（随机过程）, 296
- Strong law of large numbers（强大数定律）, 280
  - for Markov chains（对马尔可夫链）, 402
  - proof（证明）, 294
- Subset（子集）, 4
- Sufficient statistic（充分统计量）, 509, 511
- Sum of random number of r.v.'s（随机个随机变量之和）, 240
  - geometric number of exponential r.v.'s（几何个数个指数随机变量）, 243, 335
  - geometric number of geometric r.v.'s（几何个数个几何随机变量）, 244, 328
  - mean（均值）, 197, 241
  - variance（方差）, 197, 241
  - transform（变换）, 241
- Sum of random variables（随机变量之和）
  - of Bernoulli（伯努利）, 261
  - convolution（卷积）, 213
  - expectation, see expectation, linearity（期望，见"期望，线性"）
  - of normal（正态）, 214, 238
  - of Poisson（泊松）, 237, 313
  - transform（变换）, 237
  - variability extremes（极端变异性）, 135
  - variance（方差）, 111, 112, 113, 178, 220

## T

- t-distribution（t 分布）, 471, 500
  - tables（表）, 473
- Tabular method（表格法）, 93, 94
- Total expectation theorem（全期望定理）
  - for continuous r.v.'s（对连续随机变量）, 173
  - for discrete r.v.'s（对离散随机变量）, 104
- Total probability theorem（全概率定理）, 28
  - conditional version（条件形式）, 59
  - for PDFs（对概率密度）, 167
  - for PMFs（对概率质量）, 103
- Transient state（暂态）, 347, 381
- Transition（转移）
  - graph（图）, 341

> <span style="color:#7f8c8d;">Transition 词条的其余子项（matrix 起）延续到下一页（PDF p535，书页 528）。</span>

---

<!-- ===== PDF p535 ===== -->

<span style="color:#c0392b;">**索引（Index）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p535 − 7 = 书页 528，Index 索引**最后一页**。承接上一页（PDF p534）的 **T**（Transition 的 "matrix" 起），经字母 **T → V → U → W → Z** 收束全文索引（书页 521–528）。页码列表原样保留、不译、不增删；被打碎整数已规范回原整数（如 "1 59"→159、'1 45'→145、'1 1 1 , 1 12'→111, 112）。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 本页为双栏排版收尾，OCR 单栏输出导致若干**游离子项**（"discrete, 116"、"mean, 88"、"transform, 239, 258"、"variance, 88"、"two-dimensional continuous, 159"）无法可靠归属其父主词条：它们与已在前索引页（p528/p535 本页）呈现的 "Bernoulli r.v. mean/variance, 88"、"uniform transform, 239, 258" 等重复，故不虚构父词条，仅作灰注说明。"transition rate, 371"、"transition probability, 340" 依据内容归入 Transition 子项。索引为参考件，按 §7 处理。</span>

## T

- Transition（转移）（续）
  - matrix（矩阵）, 341, 345
  - probability（概率）, 340
  - rate（速率）, 371
- Transform（变换）, 229
  - inversion property（反演性质）, 234, 240
  - multivariate（多元）, 240
  - of linear function（线性函数的）, 231
  - of mixture（混合的）, 236
  - of sum of r.v.'s（随机变量之和）, 237
  - of sum of random number of r.v.'s（随机个随机变量之和）, 241
  - table（表）, 239
- Trial（试验）
  - Bernoulli（伯努利）, 41
  - independent（独立）, 41
- Two-envelopes paradox（双信封悖论）, 106
- Two-envelopes puzzle（双信封谜题）, 58
- Type I error（第一类错误）, 486
- Type II error（第二类错误）, 486

## V

- Value of a r.v.（随机变量的取值）, 72
- Variability extremes（极端变异性）, 135
- Variable inference（变量推断）, 410
- Variance（方差）, 83, 86, 145
  - conditional（条件的）, 104, 226
  - estimation（估计）, 468
  - law of total（全方差定律）, 226
  - of linear function of r.v.'s（随机变量线性函数的）, 87, 145
  - of product of r.v.'s（随机变量乘积的）, 192, 252
  - of sum of r.v.'s（随机变量之和）, 111, 112, 113, 178, 220
  - in terms of moments（用矩表示）, 87, 145
- Venn diagram（维恩图）, 5, 15

## U

- Unbiased（无偏）, 436, 461
  - asymptotically（渐近）, 461
- Uncountable（不可数）, 4, 7, 13, 53
- Uncorrelated（不相关）, 218, 225, 254, 436
- Uniform r.v.（均匀随机变量）
  - continuous（连续）, 141, 182
  - mean（均值）, 145
  - relation to Bernoulli process（与伯努利过程的关系）, 328
  - transform（变换）, 239, 258
  - variance（方差）, 145

## W

- Weak law of large numbers（弱大数定律）, 269

## Z

- z-transform（z 变换）, 230

> <span style="color:#7f8c8d;">Index 至此（书页 528）全部结束。其后的书页 529 起为全书后页书（Back Matter）的汇总表、标准正态表与 ATHENA 出版物目录，见后续页面（PDF p536 起）。</span>

> <span style="color:#1e8449;">**[t_note]** 注：别把索引当摆设——它是你『以主题反查位置』的倒排路由。先证：正文按章推进是学科逻辑，索引按字母排是查找逻辑，两者正交；你记住 6 个高频概念页（如 p-value、type I/II error、power、sufficient statistic、chi-square、Neyman–Pearson），就能在复习时从索引纵跳回任一知识点，不必重翻全书。跨课程（CSAPP·哈希索引下车点）：书索引 ≈ 数据库主键索引——按值定位记录，而不是顺序扫描整表。用两遍读法（先通读建立整体、再借索引做定点回查）能把记忆固化成可检索的『索引-条目』结构。</span>

---

<!-- ===== PDF p536 ===== -->

<span style="color:#00838f;">**特殊离散随机变量结果汇总表（Summary of Results for Special Discrete Random Variables）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p536 − 7 = 书页 529，属全书后页书（Back Matter）的**特殊离散随机变量结果汇总表**之首表。按 §7 汇总表特例处理：表头与括号里的描述句做行内双语翻译，块级公式用 fenced math block，变量/符号（$p_X(k)$、$E[X]$、$\text{var}(X)$、$M_X(s)$）原样保留，数字与公式不改动。表内分布以表格分列呈现；OCR 中未印出的项（如各分布的变换 $M_X(s)$ 仅部分给出）按源保留、不臆造。</span>

> <span style="color:#1e8449;">**[t_note]** 注：这张表是你做离散概率题的『速查卡』，一列读出整套结果：$p_X(k)$ 定分布、$E[X]$ / $\text{var}(X)$ 给矩、$M_X(s)$ 给变换（可随后取导求矩）。先证：每行就是一个『名字 → 三个常用量』的映射，题目遇到『二项分布』直接查行免去重推；但查表前要先确认参数记号——同一分布书上可能有不同参数约定（如几何分布用 $p$ 还是用 $1-p$），用错会差一步。跨课程（CSAPP·空间换时间）：把反复推导的结论缓存成表，正是查表优化的思想，集中记忆不如『会查 + 会验证』。</span>

| 分布（Distribution） | 概率质量 $p_X(k)$ | 均值 $E[X]$ | 方差 $\text{var}(X)$ | 变换 $M_X(s)$ |
|--------|--------|--------|--------|--------|
| 离散均匀于 $[a,b]$（Discrete Uniform over $[a,b]$） | $p_X(k) = \begin{cases} \dfrac{1}{b-a+1}, & k = a, a+1, \ldots, b \\[4pt] 0, & \text{otherwise} \end{cases}$ | $\dfrac{a+b}{2}$ | $\dfrac{(b-a)(b-a+2)}{12}$ | $M_X(s) = \dfrac{e^{as}\bigl(e^{s(b-a+1)} - 1\bigr)}{(b-a+1)(e^s - 1)}$ |
| 参数为 $p$ 的伯努利（Bernoulli with Parameter $p$，描述单次试验的成功或失败） | $p_X(k) = \begin{cases} p, & k = 1 \\[2pt] 1-p, & k = 0 \end{cases}$ | $p$ | $p(1-p)$ | $M_X(s) = 1 - p + p e^s$ |
| 参数为 $p$、$n$ 的二项（Binomial with Parameters $p$ and $n$，描述 $n$ 次独立伯努利试验中的成功次数） | $p_X(k) = \dbinom{n}{k} p^k (1-p)^{n-k}, \quad k=0,1,\ldots,n$ | $np$ | $np(1-p)$ | —（源末印出） |
| 参数为 $p$ 的几何（Geometric with Parameter $p$，描述一列独立伯努利试验中到首次成功所需试验次数） | $p_X(k) = (1-p)^{k-1} p, \quad k=1,2,\ldots$ | $\dfrac{1}{p}$ | $\dfrac{1-p}{p^{2}}$ | $M_X(s) = \dfrac{p e^s}{1 - (1-p)e^s}$ |
| 参数为 $\lambda$ 的泊松（Poisson with Parameter $\lambda$，当 $n$ 很大、$p$ 很小且 $\lambda = np$ 时近似二项概率质量） | $p_X(k) = \dfrac{e^{-\lambda} \lambda^{k}}{k!}, \quad k=0,1,\ldots$ | $\lambda$ | $\lambda$ | —（源末印出） |

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 本表为两列源 OCR 输出，变换列 $M_X(s)$ 在 Binomial 与 Poisson 两行未印出变换公式（源仅给出 Discrete Uniform、Bernoulli、Geometric 的变换），此处按源保留占位"—"，不臆造。（原页顶部 "athen%" 系 OCR 噪声符，无内容。）</span>

---

<!-- ===== PDF p537 ===== -->

<span style="color:#00838f;">**特殊连续随机变量结果汇总表（Summary of Results for Special Continuous Random Variables）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p537 − 7 = 书页 530，属全书后页书（Back Matter）的**特殊连续随机变量结果汇总表**之二表。按 §7 汇总表特例处理：表头与描述句做行内双语翻译，fenced math block 排块级公式，变量/符号（$f_X(x)$、$F_X(x)$、$E[X]$、$\text{var}(X)$、$M_X(s)$）原样保留，数字与公式不改动。表中 Normal 一行的 $F_X(x)$、$M_X(s)$ 及 $f_X(x)$ 细节按源给出部分；源未印出的项不臆造。</span>

> <span style="color:#1e8449;">**[t_note]** 注：这张连续表与上一张离散表互为镜像，但要盯住最特殊的一行——正态。先证：均匀、指数、正态这三行对应的密度/均值/方差是你算积分题的最高频入口；指数行的 $M_X(s)=\lambda/(\lambda-s)$ 只在 $s<\lambda$ 收敛，查表前先确认收敛域。正态行只有 $\mu,\sigma^2$ 二参，源表此处缺却恰是排版取舍而非不存在——正态的 $M_X(s)$ 实为 $e^{\mu s+\frac12\sigma^2s^2}$（见 §9.1 变换节）。离散表与连续表对照着看特别有味道：几何↔指数同享无记忆性、泊松↔正态互为小样本/大样本近似，这正是你跨分布连接的温床。跨课程（实分析·收敛域意识）：$s<\lambda$ 这种收敛条件提醒你，无穷和/积分的收敛域是与公式本身等重的信息。</span>

| 分布（Distribution） | 密度 $f_X(x)$ | 均值 $E[X]$ | 方差 $\text{var}(X)$ | 变换 $M_X(s)$ |
|--------|--------|--------|--------|--------|
| 连续均匀于 $[a,b]$（Continuous Uniform over $[a,b]$） | $f_X(x) = \begin{cases} \dfrac{1}{b-a}, & a \le x \le b \\[4pt] 0, & \text{otherwise} \end{cases}$ | $\dfrac{a+b}{2}$ | $\dfrac{(b-a)^{2}}{12}$ | $M_X(s) = \dfrac{e^{sb} - e^{sa}}{s(b-a)}$ |
| 参数为 $\lambda$ 的指数（Exponential with Parameter $\lambda$） | $f_X(x) = \begin{cases} \lambda e^{-\lambda x}, & x > 0 \\[4pt] 0, & \text{otherwise} \end{cases}$ | $\dfrac{1}{\lambda}$ | $\dfrac{1}{\lambda^{2}}$ | $M_X(s) = \dfrac{\lambda}{\lambda - s}, \quad (s < \lambda)$ |
| 参数为 $\mu$ 与 $\sigma^{2} > 0$ 的正态（Normal with Parameters $\mu$ and $\sigma^{2} > 0$） | $f_X(x) = \dfrac{1}{\sqrt{2\pi}\,\sigma} e^{-(x-\mu)^{2}/2\sigma^{2}}$ | $\mu$ | $\sigma^{2}$ | —（源末印出） |

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 源在 Exponential 一行内嵌了累积分布 $F_X(x) = \begin{cases} 1 - e^{-\lambda x}, & x > 0 \\ 0, & \text{otherwise} \end{cases}$（OCR 中为 "Fx (x)" 与 "if x > "、"otherw Ise" 碎裂形），故第 4 行补充说明如下。Normal 变换 $M_X(s)$ 源未印出，占位"—"不臆造。`Alx (s}`、`fx} (s)` 均为 $M_X(s)$ 之 OCR 形。</span>

> 补充（对 Exponential）：累计分布为 $F_X(x) = \begin{cases} 1 - e^{-\lambda x}, & x > 0 \\ 0, & \text{otherwise} \end{cases}$。

---

<!-- ===== PDF p538 ===== -->

<span style="color:#00838f;">**标准正态分布表（The Standard Normal Table）**</span>

> <span style="color:#7f8c8d;">本书页 = PDF p538 − 7 = 书页 531，属全书后页书（Back Matter）的**标准正态分布表**。按 §7 正态表特例处理：表头行列标记（z 值、$\Phi$ 值）与底部使用说明做行内双语翻译；表内数值**全部原样保留、不改动小数**。原表为 $\Phi(y) = P(Y \le y)$ 对 $y \in [0, 3.4]$ 的取值（$Y$ 为标准正态随机变量），行标记为 z 的十位与个位、列标记为十分位小数；OCR 将 .00–.09 的列头拆分多行，此处整理为规范网格。</span>

| z \ $\Delta$ | 0.00 | 0.01 | 0.02 | 0.03 | 0.04 | 0.05 | 0.06 | 0.07 | 0.08 | 0.09 |
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
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
| 3.0 | .9987 | .9987 | .9988 | .9988 | .9989 | .9989 | .9989 | .9989 | .9990 | .9990 |
| 3.1 | .9990 | .9991 | .9991 | .9992 | .9992 | .9992 | .9992 | .9993 | .9993 | .9993 |
| 3.2 | .9993 | .9993 | .9994 | .9994 | .9994 | .9994 | .9995 | .9995 | .9995 | .9995 |
| 3.3 | .9995 | .9995 | .9995 | .9996 | .9996 | .9996 | .9996 | .9996 | .9996 | .9997 |
| 3.4 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 | .9997 |

> 说明（Example of use）：标准正态表（The standard normal table）。表中的数值给出 $\Phi(y) = P(Y \le y)$ 的数值，其中 $Y$ 是标准正态随机变量（standard normal random variable），$y$ 介于 0 与 3.49 之间。用法示例：要求 $\Phi(1.71)$，我们查 1.7 对应行与 0.01 对应列，得 $\Phi(1.71) = 0.9564$。当 $y$ 为负时，$\Phi(y)$ 的值可用公式 $\Phi(y) = 1 - \Phi(-y)$ 求得。

> <span style="color:#1e8449;">**[t_note]** 注：读这张表要抓住三点才能不被『查不到』卡住。一、只印了 $y\ge0$：因为 $\Phi(y)=P(Y\le y)$ 对 $Y\ge0$ 单调从 0.5 升到 1，负半轴只靠对称公式 $\Phi(-y)=1-\Phi(y)$ 补。二、要清楚自己查的是『单尾』还是『双尾』概率：$P(Y>1.96)=0.025$ 与 $P(|Y|>1.96)=0.05$ 差一个因子 2，这正是 §9.4 里单侧 $\Phi(\gamma)=1-\alpha$ 与双侧 $\Phi(\gamma)=1-\alpha/2$ 的根源。三、表格只到 3.4 左右，更大 $z$（如查 $P(Z>3.7)$）尾概率已小于 $10^{-4}$，可直接近似 0。跨课程（实分析·反函数读表）：做显著性检验时你要从 $\Phi(\gamma)=0.95$ 反解 $\gamma=1.645$，这其实是隐式反函数求值——先定目标概率、再纵向扫描找到命中行，是逆向查表的正解。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] 原表为双栏排版（z=0.0–1.9 与 z=2.0–3.4 分两栏印，底部附使用说明），OCR 将列头 .00–.09 拆分多行输出；此处已按标准正态 CDF 规范值整理为单一网格，末四位小数与源一致（如 2.8 行 .99 系列、2.9–3.4 行逐渐收敛至 .999 系列）。表内数值未改动任何小数。</span>

---

<!-- ===== PDF p539 ===== -->

> <span style="color:#7f8c8d;">[此为出版社系列书目页（ATHENA Scientific Books），属全书（书页 532，PDF p539）结尾出版信息，按原文保留、不译正文。本书页 = PDF p539 − 7 = 书页 532，为全书最后一页，至此收笔。]</span>

**ATHENA SCIENTIFIC BOOKS**

> <span style="color:#1e8449;">**[t_note]** 注：这一页是『自家书单』——ATHENA Scientific 是作者 Bertsekas 与 Tsitsiklis 自行创办的出版社，同一系列的书在理念上一条线：概率（本书）、动态规划、凸分析与最优化、非线性规划、网络流、线性优化、神经动态规划，全部围绕『不确定性下的最优决策』这一母题。先证：你把它们连起来看会发现方法论同源——本书的期望/条件期望是序贯决策的价值函数入口，动态规划与凸优化则是求它的两把工具，Network Flows 又把它落到图论。跨课程（衔接规划中的凸优化 Boyd·大树系）：你计划的凸优化(Boyd)正好是这个系列第 3–4 本的正餐，读本书时把『期望最大化/最小化』的直觉提前种下，转弯到优化时会顺得多——这页不是装饰，是你的藏宝图。</span>

**OPTIMIZATION AND COMPUTATION SERIES（优化与计算系列）**

1. *Introduction to Probability*, 2nd Edition, by Dimitri P. Bertsekas and John N. Tsitsiklis, 2008, ISBN 978-1-886529-23-6, 544 pages
2. *Dynamic Programming and Optimal Control*, Two-Volume Set, by Dimitri P. Bertsekas, 2007, ISBN 1-886529-08-6, 1020 pages
3. *Convex Analysis and Optimization*, by Dimitri P. Bertsekas, with Angelia Nedic and Asuman E. Ozdaglar, 2003, ISBN 1-886529-45-0, 560 pages
4. *Nonlinear Programming*, 2nd Edition, by Dimitri P. Bertsekas, 1999, ISBN 1-886529-00-0, 791 pages
5. *Network Optimization: Continuous and Discrete Models*, by Dimitri P. Bertsekas, 1998, ISBN 1-886529-02-7, 608 pages
6. *Network Flows and Monotropic Optimization*, by R. Tyrrell Rockafellar, 1998, ISBN 1-886529-06-X, 634 pages
7. *Introduction to Linear Optimization*, by Dimitris Bertsimas and John N. Tsitsiklis, 1997, ISBN 1-886529-19-1, 608 pages
8. *Parallel and Distributed Computation: Numerical Methods*, by Dimitri P. Bertsekas and John N. Tsitsiklis, 1997, ISBN 1-886529-01-9, 718 pages
9. *Neuro-Dynamic Programming*, by Dimitri P. Bertsekas and John N. Tsitsiklis, 1996, ISBN 1-886529-10-8, 512 pages
10. *Constrained Optimization and Lagrange Multiplier Methods*, by Dimitri P. Bertsekas, 1996, ISBN 1-886529-04-3, 410 pages
11. *Stochastic Optimal Control: The Discrete-Time Case*, by Dimitri P. Bertsekas and Steven E. Shreve, 1996, ISBN 1-886529-03-5, 330 pages

> <span style="color:#1e8449;">**[t_note]** 注：这个出版社书目页是全书的『休止符』，也顺带给出三条值得你留意的路标。一、本书作者正是这套丛书的主力作者：Bertsekas 与 Tsitsiklis 贯穿多册，其中第 7 本 *Introduction to Linear Optimization* 是你计划中线性优化/凸优化的同门进阶教材。二、书目几乎全是优化（Convex Analysis、Nonlinear Programming、Network Flows、Linear Optimization），说明概率在这位作者的写作版图上本就是『在不确定性下优化决策』的支承，与本书第 8–9 章『估计/检验为决策服务』一脉相承。三、最后一句『全书收笔』也提醒你：到这里，从第 1 章概率公理到第 9 章统计推断的完整链条已闭合。跨课程（学科地图）：用书目当导航——你正在学的凸优化 (Boyd) 可借 #3 补一个多视角。</span>

> <span style="color:#7f8c8d;">[原页 OCR 碎裂] OCR 将若干 ISBN 与页数打碎（如 "5 1 2 pages"→512、"886529- 19- 1"→886529-19-1、序号 "1 1 ."→11），此处按上文排版规范回原值。全书至此收笔。</span>