# 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率）

## <span style="color:#c0392b">Lecture 3 — Independence（独立性）</span>

<span style="color:#7f8c8d;">讲师：John Tsitsiklis · Fall 2010 · MIT</span>

> <span style="color:#7f8c8d;">交叉引用教材缩写：Bertsekas = D. P. Bertsekas &amp; J. N. Tsitsiklis, *Introduction to Probability*, 2nd ed., Athena Scientific, 2008</span>

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Models based on conditional probabilities（基于条件概率的模型）</span>

**阅读**：教材 Section 1.5。

**本讲大纲（Lecture outline）**：
- 回顾（Review）。
- 两事件的独立性（Independence of two events）。
- 一族事件的独立性（Independence of a collection of events）。

**例（Example）**：一枚 biased coin（不均匀硬币）投掷 3 次：$P(H) = p$，$P(T) = 1 - p$。

> <span style="color:#7f8c8d;">图：三次投掷的概率树——根节点分出第一次投掷 $H$（概率 $p$）与 $T$（概率 $1-p$）；每个分支再按 $p$ / $1-p$ 分第二次、第三次投掷；共 8 片树叶：HHH、HHT、HTH、HTT、THH、THT、TTH、TTT，每片树叶的概率是沿路径各分支概率的乘积（如 $P(\text{THT}) = (1-p)\,p\,(1-p)$）。</span>

**课堂计算**（空栏填空）：
- $P(\text{THT}) = \underline{\qquad}$
- $P(\text{恰好 1 次正面}) = \underline{\qquad}$
- $P(\text{第一次投掷为 H} \mid \text{恰好 1 次正面}) = \underline{\qquad}$

**回顾**：
- 条件概率：$P(A \mid B) = \dfrac{P(A \cap B)}{P(B)}$，其中假设 $P(B) > 0$。

> <span style="color:#7f8c8d;">Bertsekas §1.3, p.18</span>

- <span style="color:#c0392b">乘法规则</span>：
```math
P(A \cap B) = P(B) \cdot P(A \mid B) = P(A) \cdot P(B \mid A) .
```

> <span style="color:#7f8c8d;">Bertsekas §1.3, p.24</span>

- <span style="color:#c0392b">全概率定理</span>：
```math
P(B) = P(A)\,P(B \mid A) + P(A^c)\,P(B \mid A^c) .
```
- <span style="color:#c0392b">贝叶斯法则</span>：
```math
P(A_i \mid B) = \frac{P(A_i)\,P(B \mid A_i)}{P(B)} .
```

> <span style="color:#7f8c8d;">Bertsekas §1.4, p.28（全概率定理）；p.31（贝叶斯法则）</span>

> <span style="color:#1e8449;">**[note] Note（译者注，证明策略模板）:**</span> 这棵不均匀硬币的树是"**用条件概率建模**"的标准范式：把复合实验（投 3 次）分解成一串阶段，每个阶段的概率以之前的阶段为条件。叶事件的概率等于沿路径连乘各分支的条件概率，这正是乘法规则 $P(A_1 \cap A_2 \cap A_3) = P(A_1)\,P(A_2 \mid A_1)\,P(A_3 \mid A_1 \cap A_2)$ 的图形化。同时，模型里藏着一个假设：**各次投掷 conditionally independent（条件独立）**——给定"硬币参数 $p$"，每次投掷结果不改变后续投掷的概率。这里要分清两层："独立"是给定 $p$ 之后在树模型内部的陈述，而本讲后面会看到，从数据反推参数时独立性可能被破坏。本讲的核心问题恰恰是"**独立与否依赖于你知道什么**"，这棵树就是后面两枚硬币反例的对照组。

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 费曼式洞察）:**</span> 验算三个空栏（每次投掷条件独立于历史，概率沿树连乘）：
> - $P(\text{THT}) = (1-p)\cdot p\cdot(1-p) = p(1-p)^2$ ✓。
> - $P(\text{恰好 1 次正面}) = P(\text{HTT}) + P(\text{THT}) + P(\text{TTH}) = 3\,p\,(1-p)^2$ ✓（三个叶事件互斥，用可加性求和）。
> - $P(\text{第一次为 H} \mid \text{恰好 1 次正面}) = \dfrac{p(1-p)^2}{3\,p(1-p)^2} = \dfrac{1}{3}$ ✓。
> 费曼式洞察：**那个 $\frac{1}{3}$ 与 $p$ 完全无关**——三个"恰有一次正面"的结果概率全是同一个 $p(1-p)^2$，正面出现在哪一次是均匀的。哪怕硬币偏得离谱（$p = 0.99$），只要你确实观测到"3 次里只有 1 次正面"，这次正面在三次投掷中的位置就是等可能的。这正是贝叶斯法则的"分母归一化"在抹去公共因子：分子分母里的 $p(1-p)^2$ 被约掉了。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Independence of two events（两事件的独立性）</span>

- **直觉定义**：$P(B \mid A) = P(B)$。
  - "$A$ 的发生不提供任何关于 $B$ 是否发生的信息"。
- 回顾：$P(A \cap B) = P(A) \cdot P(B \mid A)$。
- **数学定义**（Defn）：
```math
P(A \cap B) = P(A) \cdot P(B) .
```
- 该定义对 $A$ 与 $B$ 是 **symmetric（对称的）**：
  - 即使 $P(A) = 0$ 或 $P(B) = 0$ 也适用——此时相应的条件概率无定义（$P(B) = 0$ 时 $P(A \mid B)$ 无定义，$P(A) = 0$ 时 $P(B \mid A)$ 无定义），但乘积式永远成立且有意义。
  - 由对称定义可推出 $P(A \mid B) = P(A)$（当 $P(B) > 0$ 时）。

> <span style="color:#7f8c8d;">Bertsekas §1.5, p.34</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 为什么正式定义用乘积式 $P(A \cap B) = P(A)P(B)$ 而不用更直观的 $P(B \mid A) = P(B)$？因为**条件式在 $P(A) = 0$ 或 $P(B) = 0$ 时根本没定义**（除以零），而乘积式永远有意义——讲义特别强调"即使 $P(A) = 0$ 也适用"就是这个意思。很多人第一反应是"两个事件不相交所以互不影响"，其实恰好相反。若 $A$、$B$ 互斥且 $P(A), P(B) > 0$，则 $P(A \cap B) = 0 \neq P(A)P(B) > 0$，**它们永远不独立**——因为"$A$ 发生"这条信息直接宣判了"$B$ 不可能发生"，信息量大得很。直觉上，独立对应"由互不干扰的物理过程支配"（教材原话），而不是"图上不重叠"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditioning may affect independence（条件化可能破坏独立性）</span>

- **条件独立**：给定事件 $C$，若在概率律 $P(\,\cdot \mid C)$ 之下 $A$ 与 $B$ 独立，即
```math
P(A \cap B \mid C) = P(A \mid C)\,P(B \mid C),
```
  则称 $A$ 与 $B$ 在给定 $C$ 下 **conditionally independent（条件独立）**。
- **设 $A$ 与 $B$（无条件）独立**。

> <span style="color:#7f8c8d;">图：维恩图——样本空间中有独立事件 $A$ 与 $B$，另一事件 $C$ 与 $A$、$B$ 都相交，把样本空间切成多块。</span>

- **问题**：如果我们被告知 $C$ 发生了，$A$ 与 $B$ 还独立吗？

> <span style="color:#7f8c8d;">Bertsekas §1.5, p.36–37</span>

> <span style="color:#1e8449;">**[note] Note（译者注，卡点诊断）:**</span> 答案是**不一定**——这正是本节的标题含义：**条件化可能创造独立，也可能摧毁独立**。卡点诊断：很容易以为"$A$、$B$ 本来独立，加个条件不会怎样"。但"在 $P(\cdot\mid C)$ 这个新概率律下重新归一化"之后，$A$、$B$ 在新世界里的行为完全可能改变。反方向也成立（教材 Example 1.20，p.37）：两次独立公平掷硬币，$H_1$ = 第一次正面、$H_2$ = 第二次正面，给定 $D$ = "两次结果不同"，则 $P(H_1 \cap H_2 \mid D) = 0 \neq \tfrac{1}{2}\cdot\tfrac{1}{2}$——**无条件独立的事件在条件 $D$ 下被迫互斥**。记住这句总结（教材 p.38 小结框）：独立性不蕴含条件独立性，反之亦然。两者的分界线是"**你把哪些信息当成了背景假设**"。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Conditioning may affect independence（续）：两枚不均匀硬币</span>

**例**：两枚不均匀硬币 $A$ 与 $B$：$P(H \mid \text{coin } A) = 0.9$，$P(H \mid \text{coin } B) = 0.1$；以等概率随机选用其中一枚。

> <span style="color:#7f8c8d;">图：两级概率树——第一层：选中 Coin $A$ 与 Coin $B$，各概率 $0.5$；第二层：Coin $A$ 分支下两次投掷均按 $0.9$（正面）/ $0.1$（反面）分支，Coin $B$ 分支下按 $0.1$ / $0.9$ 分支。每枚硬币分支下各 4 片树叶：HH、HT、TH、TT（概率为沿路径乘积），全树共 8 条路径。</span>

- **问题 1**：一旦我们知道用的是硬币 $A$，各次投掷还独立吗？
- **问题 2**：如果我们**不知道**用的是哪枚硬币，各次投掷还独立吗？
  - 比较：$P(\text{第 11 次投掷为 H})$ 与 $P(\text{第 11 次投掷为 H} \mid \text{前 10 次全是正面})$。

> <span style="color:#7f8c8d;">Bertsekas §1.5, p.37–38</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 跨课程连接）:**</span> 两个问题的答案分别是"独立"与"不独立"，验算第二问（数值）：
> - 无条件：由对称性 $P(\text{第 } k \text{ 次为 H}) = 0.5 \times 0.9 + 0.5 \times 0.1 = 0.5$，对每个 $k$ 都一样。
> - 条件：前 10 次全正面是强烈的"选了 $A$"的证据，用贝叶斯法则更新：
> $P(A \mid 10\text{H}) = \dfrac{0.5 \times 0.9^{10}}{0.5 \times 0.9^{10} + 0.5 \times 0.1^{10}} = \dfrac{0.9^{10}}{0.9^{10} + 0.1^{10}} \approx \dfrac{0.3487}{0.3487 + 10^{-10}} \approx 1$（偏差仅约 $3\times 10^{-10}$）。
> - 于是 $P(\text{第 11 次为 H} \mid 10\text{H}) \approx 0.9 \times 1 + 0.1 \times 0 \approx 0.9 \neq 0.5$——**观测到的历史改变了你对下一次的预测**，故（无条件）各次投掷不独立 ✓。
> - 而问题 1 中，给定硬币身份后 $P(\text{第 11 次为 H} \mid \text{coin } A, 10\text{H}) = 0.9 = P(\text{第 11 次为 H} \mid \text{coin } A)$——条件独立 ✓。
> 跨课程连接：这就是"**独立性是模型陈述，不是数据的属性**"——同一串投掷，在"知不知道硬币参数"两个模型里独立性结论相反。教材 Example 1.21（0.99/0.01）算出 $P(H_1 \cap H_2) = \tfrac{1}{2}\cdot 0.99^2 + \tfrac{1}{2}\cdot 0.01^2 = 0.4901 \neq P(H_1)P(H_2) = \tfrac{1}{4}$，故 $H_1$、$H_2$（无条件）相互依赖——同一结论。"观测更新信念"的机制与你 Lec 02 的贝叶斯规则一脉相承：前 10 次投掷是证据，硬币身份是待更新的假设。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Independence of a collection of events（一族事件的独立性）</span>

- **直觉定义**：关于其中一些事件的信息，不会告诉我们任何与**其余**事件相关的概率。
  - 例如：
```math
P\big(A_1 \cap (A_2^c \cup A_3) \,\big|\, A_5 \cap A_6^c\big) = P\big(A_1 \cap (A_2^c \cup A_3)\big) .
```
- **数学定义**：事件 $A_1, A_2, \ldots, A_n$ 称为 independent（独立），若对从 $\{1, \ldots, n\}$ 中任取的**不同**下标 $i, j, \ldots, q$ 都有
```math
P(A_i \cap A_j \cap \cdots \cap A_q) = P(A_i)\,P(A_j) \cdots P(A_q) .
```

> <span style="color:#7f8c8d;">Bertsekas §1.5, p.38</span>

> <span style="color:#1e8449;">**[note] Note（译者注，第一性原理）:**</span> 这个定义比看起来强得多：它要求**所有大小 $\ge 2$ 的子集**都满足乘积等式，对 $n$ 个事件共 $2^n - n - 1$ 个条件（$n = 3$ 时是 4 个：三个两两等式加一个三元等式）。为什么要这么苛刻？直觉定义已经给出答案：真正"互不干扰"的一族事件里，你拿走**任意**子集的信息都不该影响剩下的部分。只要漏掉一种组合（比如只查了两两、漏了三元），就存在"集体效应"钻空子的可能，下一节的反例正是这么构造的。顺带读懂讲义那个花哨的例子：左边条件化在 $A_5 \cap A_6^c$ 上，右边原封不动——因为 $A_5, A_6$ 的信息对"由 $A_1, A_2, A_3$ 拼出的事件"理应毫无影响，这正是"信息不外泄"的数学化。跨课程预告：这套"整体独立强于两两独立"的结构，与线性代数里"两两线性无关不蕴含整体线性无关"（如 $(1,0), (0,1), (1,1)$ 两两无关但第三个 = 前两个之和）完全同构——先记下这个类比，下一节它还会出现。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">Independence vs. pairwise independence（独立与两两独立）</span>

**例**：两次独立公平掷硬币：
- $A$：第一次投掷为 $H$；
- $B$：第二次投掷为 $H$；
- $P(A) = P(B) = \tfrac{1}{2}$。

| 第一次 \ 第二次 | 第二次 = H | 第二次 = T |
|:---:|:---:|:---:|
| **第一次 = H** | HH（$\tfrac14$） | HT（$\tfrac14$） |
| **第一次 = T** | TH（$\tfrac14$） | TT（$\tfrac14$） |

- $C$：第一次与第二次投掷结果相同。
- 课堂计算（空栏填空）：
  - $P(C) = \underline{\qquad}$
  - $P(C \cap A) = \underline{\qquad}$
  - $P(A \cap B \cap C) = \underline{\qquad}$
  - $P(C \mid A \cap B) = \underline{\qquad}$
- **结论：两两独立不蕴含整体独立**。

> <span style="color:#7f8c8d;">Bertsekas §1.5, p.39</span>

> <span style="color:#1e8449;">**[note] Note（译者注，验证 + 证明策略模板）:**</span> 验算四个空栏：
> - $P(C) = P(\text{HH}) + P(\text{TT}) = \tfrac14 + \tfrac14 = \tfrac12$ ✓；
> - $C \cap A$ = "结果相同且第一次是 H" = {HH}，故 $P(C \cap A) = \tfrac14$ ✓；
> - $A \cap B \cap C$ = {HH}，故 $P(A \cap B \cap C) = \tfrac14$ ✓；
> - $P(C \mid A \cap B) = \dfrac{1/4}{1/4} = 1 \neq P(C) = \tfrac12$ ✓。
> 核对两两独立：$P(A \cap B) = P(A \cap C) = P(B \cap C) = \tfrac14 = \tfrac12 \cdot \tfrac12$，三个两两等式全部成立；但 $P(A)P(B)P(C) = \tfrac18 \neq \tfrac14 = P(A \cap B \cap C)$，三元等式崩塌。诊断直觉：一旦 $A$、$B$ 都发生了（两次都是正面），$C$ 就**必然**成立——$A \cap B$ 这条"联合信息"对 $C$ 的预测力远超各自单独提供的。构造反例的模板由此可复用：**造一个"由若干事件联合决定"的第三个事件**（如"相同""不同""和为 9"），它天然与每个成员两两无关，却被联合信息完全锁定。教材 Example 1.22（p.39）以 $D$ = "两次结果不同"构造同一反例（讲义的 $C$ = "相同"是 $D$ 的补事件）；教材 Example 1.23（p.39，掷两次骰子、和为 9）演示了反方向——三元乘积等式成立也不足以推出全部两两条件，两头都不能省。

---

### <span style="color:#2471a3;">**[section]**</span> <span style="color:#c0392b">The king's sibling（国王的兄弟姐妹）</span>

**问题**：国王来自一个有两个孩子的家庭。他的 sibling（兄弟姐妹）是女性的概率是多少？

> <span style="color:#1e8449;">**[note] Note（译者注，完整解 + 卡点诊断）:**</span> 这是本讲留给课堂的收尾谜题，答案出人意料：**$\tfrac{2}{3}$**。建模：每个孩子性别的模型与掷公平硬币相同，四个等可能家庭 $\{$BB, BG, GB, GG$\}$ 各 $\tfrac14$。"国王来自这个家庭"意味着**家中至少有一个男孩**（国王本人是男性），把样本空间条件化到 $\{$BB, BG, GB$\}$；"兄弟姐妹是女性"的事件是 $\{$BG, GB$\}$，故所求概率 $= \dfrac{2/4}{3/4} = \dfrac{2}{3}$。卡点诊断：直觉答案 $\tfrac12$ 来自"另一个孩子的性别与国王无关"——这个直觉在**另一种模型**里是对的：若"国王"就是**指定的那个孩子**（例如"最年长的孩子"继承王位、与性别无关），那么"指定孩子是男孩"与他/她之外那个孩子的性别确实独立，答案就是 $\tfrac12$。要小心一个反面陷阱：若继承制是"传长男"，"家中出了国王"仍然只传递"至少有一个男孩"的存在性信息，答案仍是 $\tfrac23$——因为"长子"的指称依赖两个孩子的性别组合（$\{$GB$\}$ 家的最年长孩子是女孩，国王是弟弟），它并不是"指定孩子"模型。这正是你在 6.042J 条件概率里见过的"男孩女孩悖论"家族（如"至少一个男孩时两个都是男孩"为 $\tfrac13$）——**同样一句话，不同实验模型给出不同概率**；判断"信息条件化在谁身上"永远先于套公式。

---

<span style="color:#7f8c8d;">MIT OpenCourseWare · http://ocw.mit.edu · 6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability, Fall 2010 · 引用本材料或使用条款，见 http://ocw.mit.edu/terms。</span>
