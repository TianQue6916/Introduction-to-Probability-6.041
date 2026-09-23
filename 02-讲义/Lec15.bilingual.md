# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 15 — Poisson Process — II（泊松过程 II）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Lecture outline &amp; review（本讲大纲与复习）</span>

**阅读**：读完教材 Section 6.2（Finish Section 6.2）。

**本讲大纲（Lecture outline）**：
- 泊松过程复习（Review of Poisson process）。
- 合并与分裂（Merging and splitting）。
- 例子（Examples）。
- Random incidence（随机察看）。

**复习（Review）——定义特征（defining characteristics）**：
- Time homogeneity（时间齐次性）：$P(k, \tau)$；Independence（独立性）；Small interval probabilities（小区间概率，小 $\delta$）：
```math
P(k, \delta) \approx \begin{cases} 1 - \lambda\delta, & \text{if } k = 0, \\ \lambda\delta, & \text{if } k = 1, \\ 0, & \text{if } k > 1. \end{cases}
```
- $N_\tau$ 是参数为 $\lambda\tau$ 的 Poisson r.v.（泊松随机变量）：
```math
P(k, \tau) = \frac{(\lambda\tau)^k\, e^{-\lambda\tau}}{k!}, \qquad k = 0, 1, \ldots
```
- $\mathrm{E}[N_\tau] = \mathrm{var}(N_\tau) = \lambda\tau$。
- 到达间隔（$k = 1$）：exponential（指数分布）：$f_{T_1}(t) = \lambda e^{-\lambda t}$，$t \ge 0$，$\mathrm{E}[T_1] = 1/\lambda$。
- 到第 $k$ 次到达的时间 $Y_k$：Erlang($k$)（$k$ 阶尔朗分布）：
```math
f_{Y_k}(y) = \frac{\lambda^k\, y^{k-1}\, e^{-\lambda y}}{(k-1)!}, \qquad y \ge 0 .
```

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.309–312, p.316</span>

> <span style="color:#1e8449;">**[note] Note（译者注，战略定位）:**</span> 本讲是 §6.2 的下半场，复习页把上一讲攒下的"过程字典"一次性摆上台面：定义特征三条（时间齐次、区间独立、小区间概率）、区间计数 $N_\tau \sim \mathrm{Poisson}(\lambda\tau)$、间隔 exponential(λ)、$k$ 次到达时间 Erlang($k$)——它们分别钉在教材 p.310（定义）、p.311–312（分布列与均值方差）、p.312–314（指数与无记忆性）、p.316（尔朗）。今天新增的三块各有分工：merging and splitting（合并与分裂）把工具箱补全，说明泊松过程在"多条流并成一条、一条流抽成子流"下封闭（p.318–319）；examples 用钓鱼与灯泡两道题演示无记忆性怎么变成解题杠杆（对应教材章末 Problem 10, p.329–330 与 Example 6.16, p.320）；random incidence（随机察看）则是全章的思想高潮——"在任意时刻看一眼"会系统性偏向长间隔，得到 Erlang(2) 而非 exponential（p.322–324）。读法建议：把复习页当卡片盒，后面每道题都回到这五张卡取工具。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Poisson fishing（泊松钓鱼）</span>

- 假设：Poisson，$\lambda = 0.6$/hour（条/小时）。
  - 钓两个小时。
  - 若一无所获，则继续钓，直到第一条鱼上钩为止。
- a) $P(\text{钓超过两小时}) = \underline{\qquad}$
- b) $P(\text{钓超过两小时且少于五小时}) = \underline{\qquad}$
- c) $P(\text{至少钓到两条鱼}) = \underline{\qquad}$
- d) $\mathrm{E}[\text{鱼的条数}] = \underline{\qquad}$
- e) $\mathrm{E}[\text{未来的钓鱼时间} \mid \text{已钓了四小时}] = \underline{\qquad}$
- f) $\mathrm{E}[\text{总钓鱼时间}] = \underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.314–315（无记忆性）；章末 Problem 10, p.329–330</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证）:**</span> 记 $N_2$ 为前两小时的到达（上钩）数，参数 $\lambda\tau = 0.6 \times 2 = 1.2$。a) 钓超过两小时 $\iff$ 前两小时零到达：$P(N_2 = 0) = e^{-1.2} \approx 0.301$ ✓。b) 总时长落在 $(2, 5)$ 小时 $\iff$ 前两小时零到达 **且** 之后三小时内首达：$e^{-1.2}\big(1 - e^{-1.8}\big) \approx 0.301 \times 0.835 = 0.251$ ✓。c) 规则是"钓到第一条就走"（若两小时内已钓到），故总数为 1 当且仅当 $N_2 = 1$（两小时止）或 $N_2 = 0$（续钓恰得一条）：$P(\text{恰一条}) = 1.2\,e^{-1.2} + e^{-1.2} = 2.2\,e^{-1.2} \approx 0.663$，于是 $P(\ge 2) = 1 - 2.2\,e^{-1.2} \approx 0.337$ ✓。d) $\mathrm{E}[\text{鱼}] = \mathrm{E}[N_2] + P(N_2 = 0) \cdot 1 = 1.2 + 0.301 = 1.501$ 条 ✓——$N_2 \ge 1$ 时不再添鱼，$N_2 = 0$ 时恰好再添一条。四个小题全程只动用了两件武器：区间计数 $\sim \mathrm{Poisson}(\lambda\tau)$ 与不相交区间独立性（复习页的两张卡）。方法上建议按"先切时间段、再逐段写事件"推进：b) 的两个因子各涉一段区间，独立性才允许直接相乘；c)、d) 先按 $N_2 = 0, 1, \ge 2$ 分局面，再依规则定后续——分情况配全概率展开，是带停时规则的到达问题的通用打开方式。

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 第一性原理）:**</span> e) 是全题的点睛之笔：条件"已钓了四小时"意味着前四小时零到达，而由无记忆性（教材 p.314），从时刻 4 起过程 fresh start（重新开始），未来的等待时间仍服从均值 $1/\lambda = 5/3 \approx 1.67$ 小时的指数分布 ✓——已经花掉的四小时是"沉没成本"，完全不进入答案。卡点诊断：有人会把 e) 答成"已钓四小时加上 $5/3$"——题目问的是 future fishing time（未来时间）；教材 Problem 10(e)（p.330）问的才是总时长，应答 $4 + 5/3 = 17/3 \approx 5.67$ 小时，读题时先分清"未来"与"累计"。f) 用指示变量收尾：总时长 $T = 2 + \mathbf{1}\{N_2 = 0\} \cdot T'$，其中 $T'$ 是两小时后到首达的时间（无记忆性保证 $\mathrm{E}[T'] = 1/\lambda$），于是 $\mathrm{E}[T] = 2 + P(N_2 = 0)/\lambda = 2 + e^{-1.2}/0.6 \approx 2.50$ 小时 ✓。这里的 $\mathrm{E}[\mathbf{1}\{A\} X] = P(A)\,\mathrm{E}[X]$ 依赖"$A$ 与未来独立"，正是无记忆性在期望层面显形；指示变量分解这一手与 Lec 07 帽子问题、二项均值两例同源。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Merging Poisson Processes (again)（再谈泊松过程的合并）</span>

- independent Poisson random variables（独立泊松随机变量）之和是 Poisson。
- independent Poisson processes（独立泊松过程）的 merging（合并）是 Poisson。

> <span style="color:#7f8c8d;">图：红灯泡闪烁（Poisson，速率 $\lambda_1$）与绿灯泡闪烁（Poisson，速率 $\lambda_2$），合并后的"所有闪光"（All flashes）仍是 Poisson。</span>

- **课堂提问**：下一次到达来自第一个过程的概率是多少？$\underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.318–319（Example 6.14, p.319）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断）:**</span> 空栏答案：$\lambda_1 / (\lambda_1 + \lambda_2)$。验算：在宽 $\delta$ 的区间内，第一过程到达 $\approx \lambda_1\delta$、第二过程到达 $\approx \lambda_2\delta$，两者互斥且独立；给定"恰有一次到达"，它来自第一过程的条件概率为 $\dfrac{\lambda_1\delta}{\lambda_1\delta + \lambda_2\delta} = \dfrac{\lambda_1}{\lambda_1 + \lambda_2}$ ✓——分式上下同除 $\delta$，答案与窗口宽度无关，这正是"速率占比决定竞争胜负"的含义（教材 p.319 的邮局例：寄信者流与寄包裹者流合并）。卡点诊断：常见误答有二——答 $\lambda_1/\lambda_2$（混淆"占比"与"比值"）、答 $1/2$（默认对称；只有 $\lambda_1 = \lambda_2$ 时才成立）。另须留意 p.319 的新信息：各次到达的**来源**相互独立，于是"来源标签序列"恰似独立重复掷一枚偏硬币——这个事实让"合并的逆操作"（下一页的 splitting，分裂）成为干净的构造：给每个到达独立贴 0/1 标签再分流。合并保泊松、分裂保泊松、且分裂出的两条流还相互独立（p.319 称之为 somewhat surprising），泊松过程在"流的组合运算"下封闭，这是它作为建模语言的看家本领。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Light bulb example（灯泡例题）</span>

- 每只灯泡的寿命是 independent（独立）的 exponential($\lambda$)（参数 $\lambda$ 的指数分布）。
- 装上三只灯泡。求最后一只灯泡烧断时刻的期望。

- **解**：把每只灯泡的烧断视为一条泊松过程的首达。开局三条独立流并联，合并流速率 $3\lambda$，故首只烧断时刻 $T_1$ 服从 exponential($3\lambda$)，$\mathrm{E}[T_1] = 1/(3\lambda)$。此后由指数分布的无记忆性，幸存两只的剩余寿命仍是参数 $\lambda$ 的独立指数变量，$T_2 \sim \text{exponential}(2\lambda)$，$\mathrm{E}[T_2] = 1/(2\lambda)$。再烧断一只后同理，$T_3 \sim \text{exponential}(\lambda)$，$\mathrm{E}[T_3] = 1/\lambda$。于是
```math
\mathrm{E}[\text{最后一只烧断时刻}] = \mathrm{E}[T_1 + T_2 + T_3] = \frac{1}{3\lambda} + \frac{1}{2\lambda} + \frac{1}{\lambda} = \frac{11}{6\lambda} .
```

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.320（Example 6.16）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 第一性原理）:**</span> 逐层验算：$1/(3\lambda) + 1/(2\lambda) + 1/\lambda = \tfrac{2 + 3 + 6}{6\lambda} = \tfrac{11}{6\lambda}$ ✓，与教材 Example 6.16（p.320）一致；教材还顺手算了方差——三个阶段独立（无记忆性保证），$\mathrm{var} = \tfrac{1}{9\lambda^2} + \tfrac{1}{4\lambda^2} + \tfrac{1}{\lambda^2} = \tfrac{49}{36\lambda^2}$ ✓，方差和规则（Lec 07）在此直接落地。第一性原理上，本题的引擎是两件事的接力：其一，**competing exponentials（竞争指数）**——$\min(T_a, T_b)$ 服从参数 $\lambda_a + \lambda_b$ 的指数分布（教材 Example 6.15, p.319–320 用 CDF 与"合并流首达"两种路径各证一遍）；其二，**memorylessness（无记忆性）**——每烧断一只，幸存者"忘记年龄"，剩余寿命分布重置为 exponential($\lambda$)，于是三阶段相互独立、可以逐段定价。卡点预警：不要把答案写成 $3/\lambda$（三只"串联"的错觉）——灯泡是并联工作的，"最快的那只"决定第一阶段时长；均值 $\tfrac{11}{6\lambda} \approx 1.83/\lambda$ 小于单只寿命的三倍，因为每阶段都有多只灯泡同时兜底。这个"并联流 + 阶段重置"的图像还会以排队、机器维修的面目重现。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Splitting of Poisson processes（泊松过程的分裂）</span>

- 假设通过某 server（服务器）的 email traffic（邮件流量）是一个 Poisson process（泊松过程）。
- 不同邮件的目的地（destinations）相互 independent（独立）。

> <span style="color:#7f8c8d;">图：离开 MIT 的邮件流（速率 $\lambda$）进入 MIT 服务器，按目的地分流——以概率 $p$ 去往 USA（输出速率 $p\lambda$），以概率 $1-p$ 去往 Foreign（输出速率 $(1-p)\lambda$）。</span>

- 每条输出流都是 Poisson。

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.318–319（Example 6.13, p.318）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断 + 跨课程连接）:**</span> 卡点：分裂为什么"保泊松"？教材 Example 6.13（p.318）把定义三条逐一重验：时间齐次性显然（$\lambda$、$p$ 都不随时间变）；不相交区间独立显然（每个到达的标签独立于其他时刻）；关键在第三条——小 $\delta$ 内出现一封"本地包"的概率 $\approx \lambda\delta \cdot p = (\lambda p)\delta$，而两次及以上本地到达是 $\delta$ 的高阶量、可忽略，于是输出流满足泊松定义，速率 $\lambda p$ ✓。注意分裂切的是**到达**而不是时间轴：每个到达独立地以概率 $p$ 被保留（thinning，稀疏化），输出速率按 $p$ 等比例缩水。另一件易被忽略的事实：分裂出的两条输出流**相互独立**（p.319，教材明言 surprising 并留作章末习题）——直觉是"标签与时刻都独立，把一维流拆成两维也没有制造关联"。跨课程连接：给每个事件独立乘一个 0/1 指示变量再对子样本分析，正是 CLRS 第 5 章 indicator random variable（指示随机变量）的手法——对每个事件贴一枚独立的伯努利标签，套路同源；而"$\lambda\delta$ 再乘 $p$"的两步分解，就是 6.042J 乘法公式在小区间上的直接套用。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Random incidence for Poisson（泊松过程的随机察看）</span>

- 一个已经运行了 forever（永远）的 Poisson process（泊松过程）。
- 在某个 "random time"（随机时刻）现身——实则意指 arbitrary time（任意时刻）。

> <span style="color:#7f8c8d;">图：时间轴上一串到达（×）；选定的时刻 $t^*$ 落在某一段到达间隔之内——该间隔从上一次到达延伸到下一次到达，$t^*$ 把它切成"已流逝部分"与"剩余部分"。</span>

- **课堂提问**：被选中的那段到达间隔，其长度服从什么分布？$\underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.322–324（The Random Incidence Paradox；Fig. 6.7）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理 + 验证）:**</span> 空栏答案：Erlang of order 2（2 阶尔朗分布），PDF $f_L(l) = \lambda^2 l\, e^{-\lambda l}$，均值 $2/\lambda$。推导（教材 p.322）：把选中间隔的长度拆成 $L = (t^* - \underline{V}) + (\bar{V} - t^*)$——"已流逝时间"由 $t^*$ 之前的过去决定，"剩余时间"由 $t^*$ 之后的未来决定；由泊松过程的独立性假设，两者 independent ✓。剩余一侧用无记忆性：从 $t^*$ 起 fresh start，$\bar{V} - t^* \sim \text{exponential}(\lambda)$；已流逝一侧有对称论证（教材 p.322：把时间轴倒放，泊松过程回放仍是泊松过程），形式化即 $P(t^* - \underline{V} > x) = P(0, x) = e^{-\lambda x}$ ✓。两个独立 exponential($\lambda$) 之和即 Erlang(2)，$\mathrm{E}[L] = 2/\lambda$ ✓——不是 $1/\lambda$！这就是 random incidence paradox（随机察看悖论）：$t^*$ 并非随机变量（教材原话：the term is misleading，这个叫法有误导性），而是**更容易落进长间隔**——就像随机挑一天量超市排队长度，多半赶上高峰。100B 视角：$f_L(l) = \int_0^l \lambda e^{-\lambda x}\, \lambda e^{-\lambda (l - x)}\, dx = \lambda^2 l\, e^{-\lambda l}$ 是一次卷积积分，erlang 的封闭形式正好可验 ✓。与"第 $k$ 段间隔"（$k$ 固定，分布 exponential）相比，"包含 $t^*$ 的间隔"（编号随机）是两个不同的实验——教材 p.324 专门强调这一区分，也是下一页 renewal 版本的思想铺垫。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Random incidence in "renewal processes"（"更新过程"中的随机察看）</span>

- 相继到达（successive arrivals）构成的序列——"renewal processes"（更新过程）：
  - 到达间隔 i.i.d.（独立同分布），但不必是 exponential（指数分布）。
- **例**：公交车（bus）的到达间隔等可能地（equally likely）为 5 或 10 分钟。
- 若你在 "random time"（随机时刻）到达车站：
  - 你选中的是一段 5 分钟间隔的概率是多少？$\underline{\qquad}$
  - 到下一班车的期望等待时间是多少？$\underline{\qquad}$

> <span style="color:#7f8c8d;">Bertsekas §6.2, p.322–324（随机察看悖论与公交例）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 卡点诊断 + 跨课程连接）:**</span> 空栏验算：在很长的时段里，"5 分钟间隔"条数与"10 分钟间隔"条数各占一半，但贡献的**时间占比**是 $5 \cdot \tfrac12 : 10 \cdot \tfrac12 = 2.5 : 7.5$——随机时刻落进某类间隔的概率应按时间占比计，故 $P(\text{选中 5 分钟间隔}) = 2.5/7.5 = 1/3$ ✓。等待时间：落入 5 分钟间隔（概率 $1/3$）时，位置在其中大致均匀，平均剩余 $2.5$ 分钟；落入 10 分钟间隔（概率 $2/3$）时平均剩余 $5$ 分钟；故 $\mathrm{E}[\text{等待}] = \tfrac13 \cdot 2.5 + \tfrac23 \cdot 5 = \tfrac{25}{6} \approx 4.17$ 分钟 ✓。顺带补齐讲义上一页的同类量：被选中间隔的长度期望 $\mathrm{E}[L] = \tfrac13 \cdot 5 + \tfrac23 \cdot 10 = \tfrac{25}{3} \approx 8.33$ 分钟 ✓，与教材公交例（p.322–324）的 $8.33$ 吻合。卡点诊断：两个空栏的直觉答案 $1/2$ 与 $5$ 分钟全错——错在把"按条数抽签"与"按时间抽签"混为一谈；教材 p.324 总结道：固定编号 $k$ 看第 $k$ 段间隔，与固定时刻 $t$ 看包含 $t$ 的那段间隔，是两个**选择机制不同**的实验。跨课程连接：这种"长个体被超额抽中"的 length-biased sampling（长度偏倚抽样）本质是加权平均换了权重——6.042J 里数方案时"每个对象一票"，这里换成"每分钟一票"；分清计数的度量单位（个数还是时长），是组合与概率衔接处最容易失分也最值钱的一条缝。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
