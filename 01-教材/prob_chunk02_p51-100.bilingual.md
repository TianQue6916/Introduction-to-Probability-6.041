<!-- ===== batch02_A ===== -->
# <span style="color:#c0392b;">第 1 章 样本空间与概率（续）— 第 51–62 页</span>

覆盖第 1 章 §1.5 收尾（串联/并联子系统、独立性、独立试验与二项概率）、§1.6 计数（Counting）、§1.7 小结与讨论（Summary and Discussion）。

---

## <span style="color:#c0392b;">§1.5 独立性（Independence，续）</span>

这是一个典型的问题：评估一套由可独立失效的组件（components）所构成的系统的可靠性（reliability）。这样的系统常常可以划分成若干子系统（subsystems），其中每个子系统又由若干个以串联（in series）或并联（in parallel）方式连接的组件构成；参见 Fig. 1.15(b)。

设一个子系统由组件 `1, 2, …, m` 构成，并设 $P_i$ 为组件 $i$ 处于正常（"成功"）状态的概率。那么，一个**串联**子系统在它的全部组件都正常时成功，因此其成功概率等于各相应组件成功概率的乘积，即
```math
P(\text{series subsystem succeeds}) = P_1 P_2 \cdot \cdot \cdot p_m .
```

一个**并联**子系统在其任一组件成功时成功，因此其失效概率等于各相应组件失效概率的乘积，即
```math
P(\text{parallel subsystem succeeds}) = 1 - P(\text{parallel subsystem fails})
= 1 - ( 1 - P_1 )( 1 - P_2 ) \cdot \cdot \cdot ( 1 - P_m ) .
```

现在回到 Fig. 1.15(a) 的网络，我们可以利用上述公式、从（网络的）末端开始依次计算成功的概率（即存在一条从 A 到 B 的路径）。让我们用记号 `X → Y` 表示"存在一条（可能是间接的）从节点 X 到节点 Y 的连接"这一事件。于是
```math
P(C \to B) = 1 - ( 1 - P(C\text{-}E \text{ and } E \to B ) )( 1 - P(C\text{-}F \text{ and } F \to B ) )
= 1 - ( 1 - p_{CE} p_{EB} )( 1 - p_{CF} p_{FB} )
= 1 - ( 1 - 0.8 \cdot 0.9 )( 1 - 0.95 \cdot 0.85 )
= 0.946,
```
```math
P(A \to C\ \text{and}\ C \to B) = P(A \to C)P(C \to B) = 0.9 \cdot 0.946 = 0.851 .
```
```math
P(A \to D\ \text{and}\ D \to B) = P(A \to D)P(D \to B) = 0.75 \cdot 0.95 = 0.712,
```
最后得到所要求的概率
```math
P(A \to B) = 1 - ( 1 - P(A\text{-}C \text{ and } C \to B ) )( 1 - P(A\text{-}D \text{ and } D \to B ) )
= 1 - ( 1 - 0.851 )( 1 - 0.712 )
= 0.957 .
```

### <span style="color:#c0392b;">独立试验与二项概率（Independent Trials and the Binomial Probabilities）</span>

如果一个试验涉及一系列独立但相同的阶段（stages），我们就说我们得到了一系列**独立试验**（independent trials）。在每一阶段只有两种可能结果这一特殊情形下，我们称我们有一系列**独立伯努利试验**（independent Bernoulli trials）。这两种可能结果可以是任意的，例如"下雨"或"不下雨"，但我们常常用掷硬币来思考，并把这两种结果称为"正面"（heads，记作 H）和"反面"（tails，记作 T）。

考虑由 $n$ 次独立掷硬币组成的一次试验，其中每次掷币出现"正面"的概率为 $p$，$p$ 是介于 0 和 1 之间的某个数，并且各次掷币相互独立，这里的试验结果可以通过条件概率的方式（conditional probabilities）用一棵树来描述（如图 1.16 所示：三次独立掷硬币的树）。沿着这棵树的各分支，我们记录下相应的条件概率（conditional probabilities），并根据乘法规则（multiplication rule），通过将树上记录的各概率相乘，即可算出某一特定的 3 次掷币序列的概率。类似地，$n$ 次掷币序列有 $2^n$ 种可能的结果。

我们用 $A_i$ 表示事件 $\{ \text{第 } i \text{ 次掷币为正面} \}$。令 $k$ 为整数 $k = 0, 1, \ldots, n$，则在一个 $n$ 次掷币序列中恰好出现 $k$ 次正面的概率为 $p(k) = P(\text{在 } n \text{ 次掷币中恰好 } k \text{ 次正面})$，这个概率在后面的内容中扮演重要角色，因此我们给出其公式。数学上可证明：
```math
p(k) = \binom{n}{k} p^k (1 - p)^{n - k} ,
```
其中记号
```math
\binom{n}{k} = \text{含有 } k \text{ 个正面的不同 } n \text{ 次掷币序列的数目}。
```
这些数 $\binom{n}{k}$（读作 "$n$ 选 $k$"）称为**二项系数**（binomial coefficients），而这些概率则称为**二项概率**（binomial probabilities）。

利用一个将在第 1.6 节给出的计数论证（counting argument），可以证明
```math
\binom{n}{k} = \frac{n!}{k!(n - k)!}, \qquad k = 0, 1, \ldots, n,
```
其中对任何正整数 $i$ 都有
```math
i! = 1 \cdot 2 \cdot \ldots \cdot (i - 1) \cdot i ,
```
并且按约定 $0! = 1$。另一种验证方法略述于章末习题中。注意，二项概率的和必须为 1，从而表明**二项公式**（binomial formula）
```math
\sum_{k=0}^{n} \binom{n}{k} p^k (1 - p)^{n - k} = p(0) + p(1) + \cdots + p(n) = 1 .
```

## <span style="color:#2471a3;">[example] Example 1.25. 服务质量（Grade of Service）</span>
一家互联网服务提供商（ISP）安装了 $c$ 个调制解调器（modems），为 $n$ 个拨号上网客户（dialup customers）提供服务。据估计，在任一给定时刻，每个客户需要连接的概率均为 $p$，且各客户相互独立。那么，需要连接的客户数多于调制解调器数的概率是多少？

这里我们关心的是同时需要连接的客户数超过 $c$ 的概率。它等于
```math
\sum_{k = c + 1}^{n} p(k),
```
其中 $p(k)$ 是上述二项概率。例如，若 $n = 100$、$p = 0.1$、$c = 15$，则所求概率为 $0.0399$。

这个例子是典型的"设施规模设计"问题：为一个由相互独立的客户组成的同质群体（homogeneous population）提供服务。问题在于选择设施规模，以保证某个（有时称为服务质量 grade of service）概率，即没有用户被排除在服务之外。

---

## <span style="color:#c0392b;">§1.6 计数（Counting）</span>

概率的计算常常涉及事件中各种结果（outcomes）的数数问题（counting）。我们已经在两种情境中遇到过这类数数问题。

(a) 当样本空间 $\Omega$ 具有有限个等可能的结果，从而适用离散均匀概率律（discrete uniform probability law）时，任一事件 $A$ 的概率为
```math
P(A) = \frac{\text{number of elements of } A}{\text{number of elements of } \Omega},
```
这需要对 $A$ 和 $\Omega$ 的元素个数进行计数。

(b) 当我们想计算一个具有有限个等可能结果的事件 $A$ 的概率，而其中每个结果的概率 $p$ 已知时，$A$ 的概率为
```math
P(A) = p \cdot (\text{number of elements of } A),
```
这需要对 $A$ 的元素个数进行计数。这类问题的一个例子是计算 $n$ 次掷硬币中恰好出现 $k$ 次正面的概率（即二项概率 binomial probabilities）。我们在前一节中看到，含 $k$ 次正面（heads）的每个特定不同序列的概率都很容易得到，但要算出所有这类序列的数目（即将在下文给出）则需要动些脑筋。

虽然计数在原理上是直截了当的，但它常常具有挑战性；计数的艺术构成了组合学（combinatorics）这一领域的很大一部分。在本节中，我们介绍计数基本法则（the basic principle of counting），并把它应用到概率模型中经常遇到的各种情形。

### <span style="color:#c0392b;">计数法则（The Counting Principle）</span>

计数法则基于一种分而治之（divide-and-conquer）的策略，即通过使用一棵树把计数分解为若干阶段（stages）。例如，考虑一个由两个连续阶段组成的试验。第一阶段的可能结果是 $a_1, a_2, \ldots, a_m$；第二阶段的可能结果是 $b_1, b_2, \ldots, b_n$。于是，这个两阶段试验的可能结果就是所有可能的有序对（ordered pairs）$(a_i, b_j)$，其中 $i = 1, \ldots, m$，$j = 1, \ldots, n$。注意，这样的有序对数目等于 $mn$。这一观察结果可推广如下（也参见 Fig. 1.17）。

## <span style="color:#2471a3;">[figure] Fig. 1.17</span>
计数基本法则的图示（图中 $r = 4$）。计数按阶段进行。第一阶段有 $n_1$ 种结果。对前面 $i - 1$ 个阶段的每一种结果，第 $i$ 阶段都有 $n_i$ 种结果。树叶的总数为 $n_1 n_2 \cdots n_r$。这正是所求的计数结果。

设一个多阶段过程有 $r$ 个阶段，且：
(a) 第一阶段有 $n_1$ 种可能结果；

(b) 对第一阶段的每一种可能结果，第二阶段都有 $n_2$ 种可能结果；

(c) 对任意前 $i - 1$ 个阶段所形成的每一种结果，第 $i$ 阶段（$i > 1$）都有 $n_i$ 种可能结果。

那么，这个 $r$ 阶段过程的可能结果总数为
```math
n_1 n_2 \cdots n_r .
```
这就是**计数基本法则**（Counting Principle）。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 计数基本法则其实是你在离散数学里反复依赖的乘法原则——6.042J《Mathematics for CS》（Lehman–Leighton–Meyer）的 Combinatorics/Counting 一章专门以 product rule 命名它，并用一棵多叉树把所有可能结果铺开：每层把选项数相乘，树叶总数即总结果数。它和它的"另一面"——双射计数（bijection，一一对应）——共同构成组合学的两根支柱：要数清一堆东西，先把它们一一对应到一个已知可数的结构上。这里有个极易被忽略的细节：只有当第 $i$ 阶段的选项数目与前面阶段的具体选择无关时，连乘才成立，教材在第 1.26、1.27 两例中分别用"逐位十选""逐元素二选"再次印证这一点。建议把它当作组合、排列、划分所有公式的一阶脚手架：那些公式本质上都是同一棵计数树的某个分支计数，后面碰到的每一项都归结到"乘法"二字。

## <span style="color:#2471a3;">[example] Example 1.26. 电话号码的数目（The Number of Telephone Numbers）</span>
一个本地电话号码是一个 7 位数字的序列，但第一位数字不能为 0 或 1。问有多少个不同的电话号码？

我们可以把序列的选择可视化为一个逐个位置进行的过程，共 7 个阶段；对第一位的选择除外，在那里我们只有 8 种选择（choices）。因此答案是
```math
8 \cdot 10 \cdot 10 \cdots 10 = 8 \cdot 10^6 .
```
（上式中 10 连乘共 6 次。）

## <span style="color:#2471a3;">[example] Example 1.27. 一个 $n$ 元集合的子集数目（The Number of Subsets of an $n$-Element Set）</span>
考虑一个 $n$ 元集合 $\{ S_1, S_2, \ldots, S_n \}$。它有多少个子集（包括自身和空集）？

我们可以把选择一个子集可视化为一个顺序过程：每次检查一个元素，并决定是否把它纳入集合。总共有 $n$ 个阶段，每个阶段有两种选择（binary choice）。因此子集数目为
```math
2 \cdot 2 \cdots 2 = 2^n .
```
（上式中 2 连乘共 $n$ 次。）

应当注意，即使每个第一阶段的结果导致一组不同的可能第二阶段结果，等等，计数法则仍然成立。唯一的要求是：可能第二阶段的数目是恒定的，与第一阶段的结果无关。

在接下来的内容中，我们将主要关注两类涉及"从 $n$ 个对象中选取 $k$ 个对象"的计数论证。如果选取的顺序起作用，这样的选取称为**排列**（permutation）；否则称为**组合**（combination）。随后我们将讨论一种更一般的计数类型，涉及把 $n$ 个对象的集合划分为多个子集（即划分 partition）。

### <span style="color:#c0392b;">k-排列（$k$-permutations）</span>

我们从 $n$ 个互不相同的对象出发，设 $k$ 为某个正整数，满足 $k \le n$。我们希望计算从这 $n$ 个对象中选取 $k$ 个并把它们排列成一个序列的不同方式数目，即不同的 $k$ 对象序列的数目。

我们可以任选这 $n$ 个对象中的任何一个作为第一个。选定第一个之后，第二个只有 $n - 1$ 种可能选择；给定前两个的选择，第三阶段只剩 $n - 2$ 个可用对象，等等。当我们准备选取最后一个（第 $k$ 个）对象时，我们已经选定了 $k - 1$ 个对象，这给最后一个对象留下了 $n - (k - 1)$ 种选择。由计数法则，可能的序列数目，即**$k$-排列**（$k$-permutations），为
```math
n(n - 1) \cdots (n - k + 1) = \frac{n(n - 1) \cdots (n - k + 1) \cdot (n - k) \cdots 2 \cdot 1}{(n - k) \cdots 2 \cdot 1} = \frac{n!}{(n - k)!} .
```

在 $k = n$ 的特殊情形下，可能的序列数目（简称为**排列** permutations）为
```math
n(n - 1)(n - 2) \cdots 2 \cdot 1 = n! .
```
（在 $k$-排列数公式中令 $k = n$，并回忆约定 $0! = 1$。）

## <span style="color:#2471a3;">[example] Example 1.28</span>
让我们计算由四个互不相同的字母构成的不同单词（words）的数目。这是计算字母表中 26 个字母的 4-排列数的问题。所求数目为
```math
\frac{n!}{(n - k)!} = \frac{26!}{22!} = 26 \cdot 25 \cdot 24 \cdot 23 = 358{,}800 .
```

排列的计数可以与计数法则相结合，来解决更复杂的计数问题。

## <span style="color:#2471a3;">[example] Example 1.29</span>
你有 $n_1$ 张古典音乐 CD、$n_2$ 张摇滚音乐 CD 和 $n_3$ 张乡村音乐 CD。要想使相同类型的 CD 彼此相邻（contiguous）排列，共有多少种不同的排列方式？

我们把问题分解为两个阶段：先选取 CD 类型的顺序，再选取各类型内部 CD 的顺序。类型序列有 $3!$ 种有序排列（如 classical/rock/country、rock/country/classical 等），而古典（rock、country 分别）CD 的排列各有 $n_1!$（$n_2!$、$n_3!$）种。因此，对每一种 $3!$ 个 CD 类型序列，都有 $n_1! n_2! n_3!$ 种 CD 的排列方式，故所求总数为 $3! n_1! n_2! n_3!$。

现在假设你把每种类型 $i$ 的 $n_i$ 张 CD 中的 $k_i$ 张送给一位朋友，其中 $k_i < n_i$，$i = 1, 2, 3$。那么你所剩的 CD 的所有可能排列数目是多少？解法与前面类似，只是要把式中对类型 $i$ 的 CD 的"$n_i!$"替换为"$n_i$ 个对象中取 $(n_i - k_i)$ 个的排列（$(n_i - k_i)$-排列）数目"，即 $n_i!/(n_i - (n_i - k_i))! = n_i!/k_i!$；因此可能排列的数目为
```math
3! \cdot \frac{n_1!}{k_1!} \cdot \frac{n_2!}{k_2!} \cdot \frac{n_3!}{k_3!}.
```

### <span style="color:#c0392b;">组合（Combinations）</span>

有 $n$ 个人，我们想组成一个 $k$ 人委员会（committee）。有多少种不同的委员会？更抽象地说，这与"计给定 $n$ 元集合的 $k$ 元子集数目"是同一个问题。注意，组合与 $k$-排列是不同的，因为在组合中被选元素之间没有排序。

例如，字母 A、B、C、D 的 2-排列是
```math
AB, BA, AC, CA, AD, DA, BC, CB, BD, DB, CD, DC,
```
而这四个字母中取两个的组合是
```math
AB, AC, AD, BC, BD, CD.
```
在前面的例子中，组合是通过把排列中"重复项"归并而得到的；例如 AB 和 BA 不被视为不同，二者都对应组合 AB。这一推理可以推广：每个组合都关联着 $k!$ 个"重复"的 $k$-排列，所以 $k$-排列数 $n!/(n - k)!$ 等于组合数乘以 $k!$。因此，可能组合的数目为
```math
\binom{n}{k} = \frac{n!}{k! (n - k)!} .
```

现在我们把上面的表达式与二项系数（binomial coefficient）联系起来。二项系数记作 $\binom{n}{k}$，在前一节中定义为含 $k$ 个正面的 $n$ 次掷币序列的数目。我们注意到：指定一个含 $k$ 个正面的 $n$ 次掷币序列，等价于从 $n$ 个掷币结果（tosses）的集合中选取 $k$ 个元素（即那些对应正面（heads）的元素），这正是"从 $n$ 个对象中取 $k$ 个的组合"。因此，二项系数也由同一公式给出，即
```math
\binom{n}{k} = \frac{n!}{k! (n - k)!} .
```

## <span style="color:#2471a3;">[example] Example 1.30</span>
从四个字母 A、B、C、D 中取两个的组合数，可由令 $n = 4$、$k = 2$ 得到：
```math
\binom{4}{2} = \frac{4!}{2! \, 2!} = 6,
```
这与前面列出的结果一致。

值得注意，计数论证有时会得出在代数上相当难以推导的公式。一个例子是第 1.5 节讨论过的二项公式
```math
\sum_{k=0}^{n} \binom{n}{k} p^k (1 - p)^{n - k} = 1 .
```
在特殊情形 $p = 1/2$ 下，这个公式变为
```math
\sum_{k=0}^{n} \binom{n}{k} = 2^n,
```
并容许如下简单解释：由于 $\binom{n}{k}$ 是给定 $n$ 元集合的 $k$ 元子集数目，对 $k$ 求和就数出了所有可能基数的子集数目。因此它等于一个 $n$ 元集合的所有子集的数目，即
```math
2^n .
```

## <span style="color:#2471a3;">[example] Example 1.31</span>
我们有一组 $n$ 个人。考虑由组内一位特别的人（俱乐部主席 club leader）和若干（可能为零）其他俱乐部成员组成的俱乐部。让我们用两种不同方式计算这类可能俱乐部（clubs）的数目，从而得到一个代数恒等式。

俱乐部主席有 $n$ 种选择。主席确定后，剩下 $n - 1$ 个可用人选，我们可以任选这 $n - 1$ 人构成的 $2^{n - 1}$ 个子集中的任何一个。因此可能的俱乐部数目为 $n 2^{n - 1}$。

另一种方式：对固定的 $k$，我们可以先选出 $n$ 个可用人中的 $k$ 个来组成一个 $k$ 人俱乐部（有 $\binom{n}{k}$ 种选择），然后在这些成员中选出一位担任主席（有 $k$ 种选择）。对所有可能的俱乐部规模 $k$ 求和，得到可能的俱乐部数目为 $\sum_{k=1}^{n} k \binom{n}{k}$，从而表明恒等式
```math
\sum_{k=1}^{n} k \binom{n}{k} = n 2^{n - 1} .
```

### <span style="color:#c0392b;">划分（Partitions）</span>

回忆一下，组合是从一个 $n$ 元集合中不考虑顺序地选取元素。因此，组合可以被视为把集合一分为二的**划分**（partition）：一部分含有 $k$ 个元素，另一部分含有其余 $n - k$ 个元素。现在我们把它推广到把集合划分为多于两个子集的情形。

给定一个 $n$ 元集合，以及和为 $n$ 的非负整数 $n_1, n_2, \ldots, n_r$。我们考虑把集合划分为 $r$ 个两两不相交的子集，其中第 $i$ 个子集恰好含有 $n_i$ 个元素。让我们计算这种划分有多少种。

我们逐个构成子集。构成第一个子集有 $\binom{n}{n_1}$ 种方式。构成第一个子集后，剩下 $n - n_1$ 个元素，我们需要从中选出 $n_2$ 个来构成第二个子集，有 $\binom{n - n_1}{n_2}$ 种选择，如此等等。对这一 $r$ 阶段过程使用计数法则，选择总数为
```math
\binom{n}{n_1} \binom{n - n_1}{n_2} \cdots \binom{n - n_1 - \cdots - n_{r - 1}}{n_r},
```
它等于
```math
\frac{n!}{n_1! (n - n_1)!} \cdot \frac{(n - n_1)!}{n_2! (n - n_1 - n_2)!} \cdots \frac{(n - n_1 - \cdots - n_{r - 1})!}{n_r! \cdot 0!}.
```
我们注意到许多项相互抵消，最终留下
```math
\frac{n!}{n_1! n_2! \cdots n_r!}.
```
该式称为**多项式系数**（multinomial coefficient），通常记作
```math
\binom{n}{n_1, n_2, \ldots, n_r} .
```

## <span style="color:#2471a3;">[example] Example 1.32. 字谜（Anagrams）</span>
把单词 TATTOO 中的字母重新排列，可以得到多少个不同的单词（字母序列）？

共有六个位置需要由可用的字母来填充。每种重新排列都对应于把六个位置的集合划分为：一个大小为 3 的组（填字母 T 的位置）、一个大小为 1 的组（填字母 A 的位置）和一个大小为 2 的组（填字母 O 的位置）。因此所求数目为
```math
\frac{6!}{3! \, 1! \, 2!} = \frac{1 \cdot 2 \cdot 3 \cdot 4 \cdot 5 \cdot 6}{3! \cdot 1! \cdot 2!} = 60 .
```

用另一种论证推导这一答案是有启发性的。（这一论证也可用来重新导出多项式系数公式：参见章末习题。）让我把 TATTOO 写成 $T_1 A T_2 T_3 O_1 O_2$ 的形式，暂且假装我们处理的是 6 个可区分的对象。这 6 个对象可以有 $6!$ 种不同的排列。然而，$T_1$、$T_2$、$T_3$ 的任意 $3!$ 种排列，以及 $O_1$、$O_2$ 的任意 $2!$ 种排列，都会得到同一个单词。因此，当下标被去掉时，只有 $6!/(3!\, 2!)$ 个不同的单词。

## <span style="color:#2471a3;">[example] Example 1.33</span>
一个由 4 名研究生和 12 名本科生组成的班级被随机分成四个 4 人小组。那么每个小组都含有一名研究生的概率是多少？

这与第 1.3 节的 Example 1.11 相同，但现在我们要用计数论证来得到答案。

我们首先确定样本空间的性质。一个典型结果是"把 16 名学生划分为四个 4 人小组"的一种特定方式。我们把"随机"理解为每种可能的划分都是等可能的，从而把概率问题归结为计数问题。

根据我们前面的讨论，有
```math
\binom{16}{4, 4, 4, 4} = \frac{16!}{4! \, 4! \, 4! \, 4!}
```
种不同的划分，这就是样本空间的大小。

现在我们来关注"每个小组都含有一名研究生"这一事件。生成一个具有该性质的特定结果可以分两个阶段完成：

(a) 把四名研究生分配到四个小组；第一名研究生的组有 4 种选择，第二名有 3 种，第三名有 2 种。因此这一阶段总共有 $4!$ 种选择。

(b) 把其余 12 名本科生分配到四个小组（每组 3 人）。这可以用
```math
\frac{12!}{3! \, 3! \, 3! \, 3!}
```
种不同的方式完成。

由计数法则，感兴趣的事件可以以
```math
4! \cdot \frac{12!}{3! \, 3! \, 3! \, 3!}
```
种不同的方式发生。该事件的概率为
```math
\frac{4! \cdot \frac{12!}{3! \, 3! \, 3! \, 3!}}{\frac{16!}{4! \, 4! \, 4! \, 4!}} .
```
经过若干约分，我们发现它等于
```math
\frac{12 \cdot 8 \cdot 4}{15 \cdot 14 \cdot 13},
```
这与 Example 1.11 得到的答案一致。

下面是对我们已经建立的各项计数结果的总结。

### <span style="color:#c0392b;">计数结果小结（Summary of Counting Results）</span>

- $n$ 个对象的排列（Permutations of $n$ objects）：$n!$。
- $n$ 个对象的 $k$-排列（$k$-permutations of $n$ objects）：$n! / (n - k)!$。
- 从 $n$ 个对象中取 $k$ 个的组合（Combinations of $k$ out of $n$ objects）：
```math
\binom{n}{k} = \frac{n!}{k! (n - k)!} 。
```
- $n$ 个对象划分为 $r$ 组、第 $i$ 组含有 $n_i$ 个对象的划分（Partitions of $n$ objects into $r$ groups, with the ith group having $n_i$ objects）：
```math
\binom{n}{n_1, n_2, \ldots, n_r} = \frac{n!}{n_1! n_2! \cdots n_r!} 。
```

---

## <span style="color:#c0392b;">§1.7 小结与讨论（Summary and Discussion）</span>

一个概率问题通常可以分解为几个基本步骤：

(a) 描述**样本空间**（sample space），即给定试验的可能结果所构成的集合。

(b) 规定（可能是间接地规定）**概率律**（probability law），即每个事件的概率。

(c) 计算各个感兴趣事件的概率与条件概率。

事件的概率必须满足**非负性**（nonnegativity）、**可加性**（additivity）与**归一化**（normalization）公理。在可能结果集合为有限这一重要的特殊情形下，人们只需规定每个结果的概率，就可以通过对该事件所含元素的概率求和来得到任何事件的概率。

给定一个概率律，我们常常关心**条件概率**（conditional probabilities），它使我们能基于关于试验结果的**部分信息**（partial information）进行推理。我们可以把条件概率看作是一种特殊类型的概率律，在该律下，只有包含在条件事件（conditioning event）中的结果才可能具有正的条件概率。条件概率可以由（无条件）概率律利用定义 $P(A \mid B) = P(A \cap B)/P(B)$ 推导出来。然而，反向的过程常常更方便，即：先规定一些对我们想要建模的实际情形而言很自然的条件概率，然后利用它们推导出（无条件的）概率律。

我们通过例子说明了计算概率的三种方法：

(a) **计数方法**（counting method）。该方法适用于可能结果数目有限、且所有结果等可能的情形。为计算一个事件的概率，我们数出该事件的元素个数，再除以样本空间的元素个数。

(b) **序列方法**（sequential method）。该方法适用于试验具有序列特征的情形，并且沿相应树（tree）的各分支规定或计算出合适的条件概率（也许借用计数方法）。随后，利用乘法规则（multiplication rule），通过沿树相应路径将条件概率相乘，即可得到各个事件的概率。

(c) **分而治之方法**（divide-and-conquer method）。此处，各个事件 $B$ 的概率 $P(B)$ 由条件概率 $P(B \mid A_i)$ 得到，其中 $A_i$ 是形成样本空间的一个划分（partition）并具有已知概率 $P(A_i)$ 的合适事件。然后利用**全概率定理**（total probability theorem）得到概率 $P(B)$。

最后，我们还着重讨论了一些强化主题的次要专题。我们讨论了贝叶斯（Bayes）公式在推断（inference）中的应用，这是一个重要的应用场景。我们还讨论了计数与组合学（combinatorics）的一些基本法则，这些法则有助于运用计数方法。
<!-- ===== batch02_B ===== -->
# <span style="color:#c0392b;">Chapter 1 Sample Space and Probability — Problems（第 1 章习题）</span>

> <span style="color:#7f8c8d;">Bertsekas & Tsitsiklis, *Introduction to Probability*, 2nd ed. —— Problems（习题）区，页 63–80（第 1.1–1.6 节全部习题 1–62）；页 81–82 为第 2 章开头，见文末说明。</span>

**约定**：习题题干按教材约定保留英文原题。每题下方附一行浅绿色学习提示（`[mathtip]`），用中文点明考点/方法，供学习参考。块级公式用 fenced ```math 块，行内公式用 `$...$`。

> <span style="color:#e67e22;">**重要说明**</span>：源 PDF 在页 70–71（对应习题 30–35 一带）扫描/OCR 严重损坏，部分题干无法精确复原，已尽量依据可辨认文字与教材标准内容补全，并以「〔据残片补全〕」标注；其余各题严格按照原文转录。

---

## Section 1.1 · Sets（集合）

### Problem 1 <span style="color:#2471a3;">**[problem/main]**</span>
Consider rolling a six-sided die. Let $A$ be the set of outcomes where the roll is an even number. Let $B$ be the set of outcomes where the roll is greater than $3$. Calculate and compare the sets on both sides of De Morgan's laws

```math
(A \cap B)^c = A^c \cup B^c,
\qquad
(A \cup B)^c = A^c \cap B^c .
```

> <span style="color:#1e8449;">**[mathtip]** </span> 把 $A=\{2,4,6\}$、$B=\{4,5,6\}$ 分别代入左右两端算出集合，逐项比对是否相等即可验证 De Morgan 律。

---

### Problem 2 <span style="color:#2471a3;">**[problem/main]**</span>
Let $A$ and $B$ be two sets.

(a) Show that

```math
A = (A \cap B) \cup (A \cap B^c).  \quad \text{〔据残片补全，原图此式缺失〕}
```

(b) Show that

```math
A \cup (A^c \cap B) = A \cup B.  \quad \text{〔据残片补全，原图此式缺失〕}
```

(c) Consider rolling a fair six-sided die. Let $A$ be the set of outcomes where the roll is an odd number. Let $B$ be the set of outcomes where the roll is less than $4$. Calculate the sets on both sides of the equality in part (b), and verify that the equality holds.

> <span style="color:#1e8449;">**[mathtip]** </span> 这类恒等式本质是"把 $B$ 拆成 $A\cap B$ 与 $A^c\cap B$ 两不相交部分"。取 $A=\{1,3,5\}$、$B=\{1,2,3\}$，(b) 左端 $A\cup(A^c\cap B)=\{1,2,3,5\}=A\cup B$。

---

### Problem 3 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
Prove the identity

```math
A \cup \left(\bigcap_{n=1}^{\infty} B_n\right) \;=\; \bigcap_{n=1}^{\infty} (A \cup B_n).  \quad \text{〔据残片与原解答补全〕}
```

Solution. If $x$ belongs to the set on the left, there are two possibilities. Either $x \in A$, in which case $x$ belongs to all of the sets $A \cup B_n$, and therefore belongs to the set on the right. Alternatively, $x$ belongs to all of the sets $B_n$, in which case it belongs to all of the sets $A \cup B_n$, and therefore again belongs to the set on the right. Conversely, if $x$ belongs to the set on the right, then it belongs to $A \cup B_n$ for all $n$. If $x$ belongs to $A$, then it belongs to the set on the left. Otherwise, $x$ must belong to every set $B_n$ and again belongs to the set on the left.

> <span style="color:#1e8449;">**[mathtip]** </span> 无限多集的"∩/∪"结合律（分配律）双向归谬：分 $x\in A$ 与 $x\notin A$ 两情形讨论，即可双向推出。

---

### Problem 4 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Cantor's diagonalization argument.** Show that the unit interval $[0,1]$ is uncountable, i.e., its elements cannot be arranged in a sequence.

Solution. Any number $x$ in $[0,1]$ can be represented in terms of its decimal expansion, e.g., $1/3 = 0.3333\cdots$. Note that most numbers have a unique decimal expansion, but there are a few exceptions. For example, $1/2$ can be represented as $0.5000\cdots$ or as $0.49999\cdots$. It can be shown that this is the only kind of exception, i.e., decimal expansions that end with an infinite string of zeroes or an infinite string of nines.

Suppose, to obtain a contradiction, that the elements of $[0,1]$ can be arranged in a sequence $x_1, x_2, x_3, \ldots$, so that every element of $[0,1]$ appears in the sequence. Consider the decimal expansion of $x_n$:

```math
x_n = 0.\, a_1^{(n)} a_2^{(n)} a_3^{(n)} \cdots,
```

where each digit $a_j^{(n)}$ belongs to $\{0,1,\ldots,9\}$. Consider now a number $y$ constructed as follows. The $n$th digit of $y$ can be $1$ or $2$, and is chosen so that it is different from the $n$th digit of $x_n$. Note that $y$ has a unique decimal expansion since it does not end with an infinite sequence of zeroes or nines. The number $y$ differs from each $x_n$, since it has a different $n$th digit. Therefore, the sequence $x_1, x_2, \ldots$ does not exhaust the elements of $[0,1]$, contrary to what was assumed. The contradiction establishes that the set $[0,1]$ is uncountable.

> <span style="color:#1e8449;">**[mathtip]** </span> 康托对角线论证：对第 $n$ 个数改其第 $n$ 位小数（取 $1$ 或 $2$ 避开 $9$ 的循环），构造出不在序列中的 $y$。这是"一个公理化基础上概率论为何需要连续区处理"的关键背景。

---

## Section 1.2 · Probabilistic Models（概率模型）

### Problem 5 <span style="color:#2471a3;">**[problem/main]**</span>
Out of the students in a class, $60\%$ are geniuses, $70\%$ love chocolate, and $40\%$ fall into both categories. Determine the probability that a randomly selected student is neither a genius nor a chocolate lover.

> <span style="color:#1e8449;">**[mathtip]** </span> 用容斥：$P(A\cup B)=0.6+0.7-0.4=0.9$，求补 $1-P(A\cup B)=0.1$。

---

### Problem 6 <span style="color:#2471a3;">**[problem/main]**</span>
A six-sided die is loaded in a way that each even face is twice as likely as each odd face. All even faces are equally likely, as are all odd faces. Construct a probabilistic model for a single roll of this die and find the probability that the outcome is less than $4$.

> <span style="color:#1e8449;">**[mathtip]** </span> 设单个奇数面概率为 $a$，则 $3a+3(2a)=1$，解得 $a=1/9$；再累加 $\{1,2,3\}$ 的概率即得答案。

---

### Problem 7 <span style="color:#2471a3;">**[problem/main]**</span>
A four-sided die is rolled repeatedly, until the first time (if ever) that an even number is obtained. What is the sample space for this experiment?

> <span style="color:#1e8449;">**[mathtip]** </span> 注意"if ever"：样本空间应为所有有限串 $\{o_1,\ldots,o_n\}$（前 $n-1$ 个为奇数、最后一个为偶数）再加上一个"永远不出偶数"的不可能/可讨论结果。

---

### Problem 8 <span style="color:#2471a3;">**[problem/main]**</span>
You enter a special kind of chess tournament, in which you play one game with each of three opponents, but you get to choose the order in which you play your opponents, knowing the probability of a win against each. You win the tournament if you win two games in a row, and you want to maximize the probability of winning. Show that it is optimal to play the weakest opponent second, and that the order of playing the other two opponents does not matter.

A **partition** of the sample space $\Omega$ is a collection of disjoint events $S_1,\ldots,S_n$ such that $\Omega = \cup_{i=1}^{n} S_i$.

> <span style="color:#1e8449;">**[mathtip]** </span> 设三位对手胜率 $p_1\lt p_2\lt p_3$。连赢两次需"第 2 场赢"，故先把最弱者放第 2 场；前后两场胜率乘同一常数，故顺序无关。列不同排列的总胜率随即验证。

---

### Problem 9 <span style="color:#2471a3;">**[problem/main]**</span>
**(a)** Show that for any event $A$, we have

```math
P(A) = \sum_{i=1}^{n} P(A \cap S_i).
```

**(b)** Use part (a) to show that for any events $A$, $B$, and $C$, we have

```math
P(A) = P(A \cap B) + P(A \cap C) + P(A \cap B^c \cap C^c) - P(A \cap B \cap C).
```

> <span style="color:#1e8449;">**[mathtip]** </span> (a) 由划分的可加性；(b) 取划分 $\{B,\; C\cap B^c,\; B^c\cap C^c\}$ 并在 $P(A\cap C)$ 中再对 $B$ 剖分 $P(A\cap C)=P(A\cap B\cap C)+P(A\cap B^c\cap C)$ 即可。

---

### Problem 10 <span style="color:#2471a3;">**[problem/main]**</span>
Show the formula

```math
P\big((A \cap B^c) \cup (A^c \cap B)\big) = P(A) + P(B) - 2P(A \cap B),
```

which gives the probability that exactly one of the events $A$ and $B$ will occur. [Compare with the formula $P(A \cup B) = P(A) + P(B) - P(A \cap B)$, which gives the probability that at least one of the events $A$ and $B$ will occur.]

> <span style="color:#1e8449;">**[mathtip]** </span> 两事件不相交，$P(A\cap B^c)=P(A)-P(A\cap B)$、$P(A^c\cap B)=P(B)-P(A\cap B)$，相加即得。

---

### Problem 11 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Bonferroni's inequality.**

**(a)** Prove that for any two events $A$ and $B$, we have

```math
P(A \cap B) \;\ge\; P(A) + P(B) - 1.
```

**(b)** Generalize to the case of $n$ events $A_1, A_2, \ldots, A_n$, by showing that

```math
P(A_1 \cap A_2 \cap \cdots \cap A_n) \;\ge\; P(A_1) + P(A_2) + \cdots + P(A_n) - (n-1).
```

Solution. We have $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ and $P(A \cup B) \le 1$, which implies part (a). For part (b), we use De Morgan's law to obtain

```math
\begin{aligned}
1 - P(A_1 \cap \cdots \cap A_n) &= P\big((A_1 \cap \cdots \cap A_n)^c\big) \\
&= P(A_1^c \cup \cdots \cup A_n^c) \\
&\le P(A_1^c) + \cdots + P(A_n^c) \\
&= \big(1 - P(A_1)\big) + \cdots + \big(1 - P(A_n)\big) \\
&= n - P(A_1) - \cdots - P(A_n).
\end{aligned}
```

> <span style="color:#1e8449;">**[mathtip]** </span> 由上界 $P(\cup)\le 1$ 直接得 (a)；(b) 用 De Morgan 把交集补转化为并集，再套可加性上界。

---

### Problem 12 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**The inclusion-exclusion formula.** Show the following generalizations of the formula

```math
P(A \cup B) = P(A) + P(B) - P(A \cap B).
```

**(a)** Let $A$, $B$, and $C$ be events. Then,

```math
P(A \cup B \cup C) = P(A)+P(B)+P(C) - P(A\cap B) - P(B\cap C) - P(A\cap C) + P(A\cap B\cap C).
```

**(b)** Let $A_1, A_2, \ldots, A_n$ be events. Let $S_1 = \{i_1 \mid 1 \le i_1 \le n\}$, $S_2 = \{(i_1,i_2) \mid 1 \le i_1 < i_2 \le n\}$, and more generally, let $S_m$ be the set of all $m$-tuples $(i_1,\ldots,i_m)$ of indices that satisfy $1 \le i_1 < i_2 < \cdots < i_m \le n$. Then,

```math
P\left(\bigcup_{k=1}^{n} A_k\right) \;=\; \sum_{(i_1)\in S_1} P(A_{i_1}) \;-\; \sum_{(i_1,i_2)\in S_2} P(A_{i_1} \cap A_{i_2}) \;+\; \cdots \;+\; (-1)^{n+1} P(A_1 \cap A_2 \cap \cdots \cap A_n).
```

Solution. **(a)** We use the formulas $P(X \cup Y) = P(X) + P(Y) - P(X \cap Y)$ and $(A \cup B) \cap C = (A \cap C) \cup (B \cap C)$. We have

```math
\begin{aligned}
P(A \cup B \cup C) &= P(A \cup B) + P(C) - P\big((A \cup B) \cap C\big) \\
&= P(A \cup B) + P(C) - P\big((A \cap C) \cup (B \cap C)\big) \\
&= P(A \cup B) + P(C) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C) \\
&= P(A) + P(B) - P(A \cap B) + P(C) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C) \\
&= P(A) + P(B) + P(C) - P(A \cap B) - P(B \cap C) - P(A \cap C) + P(A \cap B \cap C).
\end{aligned}
```

**(b)** Use induction and verify the main induction step by emulating the derivation of part (a). For a different approach, see the problems at the end of Chapter 2.

> <span style="color:#1e8449;">**[mathtip]** </span> 容斥原理：全体 $P(A_i)$ 减去两两交集、加上三重交集……，交叠项按奇偶交替补正；这正是"数盈亏"思想的推广。

---

### Problem 13 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Continuity property of probabilities.**

**(a)** Let $A_1, A_2, \ldots$ be an infinite sequence of events, which is "monotonically increasing," meaning that $A_n \subseteq A_{n+1}$ for every $n$. Let $A = \cup_{n=1}^{\infty} A_n$. Show that $P(A) = \lim_{n \to \infty} P(A_n)$. *Hint:* Express the event $A$ as a union of countably many disjoint sets.

**(b)** Suppose now that the events are "monotonically decreasing," i.e., $A_{n+1} \subseteq A_n$ for every $n$. Let $A = \cap_{n=1}^{\infty} A_n$. Show that $P(A) = \lim_{n \to \infty} P(A_n)$. *Hint:* Apply the result of part (a) to the complements of the events.

**(c)** Consider a probabilistic model whose sample space is the real line. Show that

```math
P\big([0,\infty)\big) = \lim_{n\to\infty} P\big([0,n]\big),
\qquad\text{and}\qquad
\lim_{n\to\infty} P\big([n,\infty)\big) = 0.
```

Solution. **(a)** Let $B_1 = A_1$ and, for $n \ge 2$, $B_n = A_n \cap A_{n-1}^c$. The events $B_n$ are disjoint, and we have $\cup_{k=1}^{n} B_k = A_n$, and $\cup_{k=1}^{\infty} B_k = A$. We apply the additivity axiom to obtain

```math
P(A) = \sum_{k=1}^{\infty} P(B_k) = \lim_{n\to\infty} \sum_{k=1}^{n} P(B_k) = \lim_{n\to\infty} P\left(\bigcup_{k=1}^{n} B_k\right) = \lim_{n\to\infty} P(A_n).
```

**(b)** Let $C_n = A_n^c$ and $C = A^c$. Since $A_{n+1} \subseteq A_n$, we obtain $C_n \subseteq C_{n+1}$, and the events $C_n$ are increasing. Furthermore, $C = A^c = (\cap_{n=1}^{\infty} A_n)^c = \cup_{n=1}^{\infty} A_n^c = \cup_{n=1}^{\infty} C_n$. Using the result from part (a) for the sequence $C_n$, we obtain

```math
1 - P(A) = P(A^c) = P(C) = \lim_{n\to\infty} P(C_n) = \lim_{n\to\infty} \big(1 - P(A_n)\big),
```

from which we conclude that $P(A) = \lim_{n\to\infty} P(A_n)$.

**(c)** For the first equality, use the result from part (a) with $A_n = [0,n]$ and $A = [0,\infty)$. For the second, use the result from part (b) with $A_n = [n,\infty)$ and $A = \cap_{n=1}^{\infty} A_n = \varnothing$.

> <span style="color:#1e8449;">**[mathtip]** </span> 概率的可加性蕴含了"极限可穿越"——单调事件序列的并/交概率等于概率的极限。把单调事件拆成不相交的"增补层" $B_n$ 是关键拆分。

---

## Section 1.3 · Conditional Probability（条件概率）

### Problem 14 <span style="color:#2471a3;">**[problem/main]**</span>
We roll two fair 6-sided dice. Each one of the $36$ possible outcomes is assumed to be equally likely.

**(a)** Find the probability that doubles are rolled.
**(b)** Given that the roll results in a sum of $4$ or less, find the conditional probability that doubles are rolled.
**(c)** Find the probability that at least one die roll is a $6$.
**(d)** Given that the two dice land on different numbers, find the conditional probability that at least one die roll is a $6$.

> <span style="color:#1e8449;">**[mathtip]** </span> 古典概型逐题计数：6/36；(b) 条件分母为"和为 ≤4"的样本；"至少一个 6" 用 $1-P(\text{都没有 6})$；(d) 在"点数不同"的 30 个等概率样本中计数。

---

### Problem 15 <span style="color:#2471a3;">**[problem/main]**</span>
A coin is tossed twice. Alice claims that the event of two heads is at least as likely if we know that the first toss is a head than if we know that at least one of the tosses is a head. Is she right? Does it make a difference if the coin is fair or unfair? How can we generalize Alice's reasoning?

> <span style="color:#1e8449;">**[mathtip]** </span> 分别求 $P(\text{HH}\mid\text{第一枚 H})$ 与 $P(\text{HH}\mid\text{至少一枚 H})$，比较大小；并检验结果与 $p$（正面概率）的关系。不公平情形下结论可能翻转。

---

### Problem 16 <span style="color:#2471a3;">**[problem/main]**</span>
We are given three coins: one has heads in both faces, the second has tails in both faces, and the third has a head in one face and a tail in the other. We choose a coin at random, toss it, and the result is heads. What is the probability that the opposite face is tails?

> <span style="color:#1e8449;">**[mathtip]** </span> 经典条件概率：$P(\text{背}\mid\text{正})$；由对称性，正面可见时对面是反面当且仅当抽中"两不同面"硬币。仔细用全概率或枚举 $6$ 个等可能面。

---

### Problem 17 <span style="color:#2471a3;">**[problem/main]**</span>
A batch of one hundred items is inspected by testing four randomly selected items. If one of the four is defective, the batch is rejected. What is the probability that the batch is accepted if it contains five defectives?

> <span style="color:#1e8449;">**[mathtip]** </span> 批量通过 ⇔ 抽到的 4 件都不是次品。不放回超几何计数：$\binom{95}{4}/\binom{100}{4}$。

---

### Problem 18 <span style="color:#2471a3;">**[problem/main]**</span>
Let $A$ and $B$ be events. Show that

```math
P(A \cap B \mid B) = P(A \mid B),
```

assuming that $P(B) > 0$.

> <span style="color:#1e8449;">**[mathtip]** </span> 把条件概率定义代入左端，分子 $P((A\cap B)\cap B)=P(A\cap B)$，再分母 $P(B)$ 约去即可。

---

## Section 1.4 · Total Probability Theorem and Bayes' Rule（全概率定理与贝叶斯公式）

### Problem 19 <span style="color:#2471a3;">**[problem/main]**</span>
Alice searches for her term paper in her filing cabinet, which has several drawers. She knows that she left her term paper in drawer $j$ with probability $p_j > 0$. The drawers are so messy that even if she correctly guesses that the term paper is in drawer $i$, the probability that she finds it is only $d_i$. Alice searches in a particular drawer, say drawer $i$, but the search is unsuccessful. Conditioned on this event, show that the probability that her paper is in drawer $j$ is given by

```math
\frac{p_j}{1 - p_i d_i}
\quad \text{for } j \ne i,
\qquad
\frac{p_i (1 - d_i)}{1 - p_i d_i}
\quad \text{for } j = i.
```

> <span style="color:#1e8449;">**[mathtip]** </span> 记事件 $F$＝"在抽屉 $i$ 中搜索失败"。用贝叶斯公式 $P(\text{inin }j\mid F)$，其中 $P(F\mid \text{in }j)$：$j=i$ 时为 $1-d_i$，$j\ne i$ 时为 $1$。

---

### Problem 20 <span style="color:#2471a3;">**[problem/main]**</span>
**How an inferior player with a superior strategy can gain an advantage.** Boris is about to play a two-game chess match with an opponent, and wants to find the strategy that maximizes his winning chances. Each game ends with either a win by one of the players, or a draw. If the score is tied at the end of the two games, the match goes into sudden-death mode, and the players continue to play until the first time one of them wins a game (and the match). Boris has two playing styles, timid and bold, and he can choose one of the two at will in each game, no matter what style he chose in previous games. With timid play, he draws with probability $p_d > 0$, and he loses with probability $1 - p_d$. With bold play, he wins with probability $p_w$, and he loses with probability $1 - p_w$. Boris will always play bold during sudden death, but may switch style between games 1 and 2.

**(a)** Find the probability that Boris wins the match for each of the following strategies:
- (i) Play bold in both games 1 and 2.
- (ii) Play timid in both games 1 and 2.
- (iii) Play timid whenever he is ahead in the score, and play bold otherwise.

**(b)** Assume that $p_w < 1/2$, so Boris is the worse player, regardless of the playing style he adopts. Show that with the strategy in (iii) above, and depending on the values of $p_w$ and $p_d$, Boris may have a better than a $50$-$50$ chance to win the match. How do you explain this advantage?

> <span style="color:#1e8449;">**[mathtip]** </span> 枚举两局的计分路径；"平分进突然死亡"时加一个几何级数项（连胜才赢）。数据：当 $p_w$ 略小于 $1/2$ 而 $p_d$ 接近 $1$ 时，"领先时保守"可把劣势球转成优势。

---

### Problem 21 <span style="color:#2471a3;">**[problem/main]**</span>
Two players take turns removing a ball from a jar that initially contains $m$ white and $n$ black balls. The first player to remove a white ball wins. Develop a recursive formula that allows the convenient computation of the probability that the starting player wins.

> <span style="color:#1e8449;">**[mathtip]** </span> 记 $P(m,n)$ 为先手胜率。第一步先手取白则胜，取黑则状态互换（先手变后手）：$P(m,n)=\tfrac{m}{m+n}+\tfrac{n}{m+n}\big(1-P(m,n-1)\big)$。

---

### Problem 22 <span style="color:#2471a3;">**[problem/main]**</span>
Each of $k$ jars contains $m$ white and $n$ black balls. A ball is randomly chosen from jar 1 and transferred to jar 2, then a ball is randomly chosen from jar 2 and transferred to jar 3, etc. Finally, a ball is randomly chosen from jar $k$. Show that the probability that the last ball is white is the same as the probability that the first ball is white, i.e., it is $m/(m+n)$.

> <span style="color:#1e8449;">**[mathtip]** </span> 归纳：只要下一罐中白球比例仍为 $m/(m+n)$（转移后比例"期望不变"），即可用全概率定理逐罐递推。

---

### Problem 23 <span style="color:#2471a3;">**[problem/main]**</span>
We have two jars, each initially containing an equal number of balls. We perform four successive ball exchanges. In each exchange, we pick simultaneously and at random a ball from each jar and move it to the other jar. What is the probability that at the end of the four exchanges all the balls will be in the jar where they started?

> <span style="color:#1e8449;">**[mathtip]** </span> 追"坏球"（前缀交换过一次即失位）：若每罐 $n$ 个球，把每次交换等价为概率 $\tfrac{1}{n}\cdot\tfrac{1}{n}$ 的选球。用互斥事件的并求"全部归位"。

---

### Problem 24 <span style="color:#2471a3;">**[problem/main]**</span>
**The prisoner's dilemma.** The release of two out of three prisoners has been announced, but their identity is kept secret. One of the prisoners considers asking a friendly guard to tell him who is the prisoner other than himself that will be released, but hesitates based on the following rationale: at the prisoner's present state of knowledge, the probability of being released is $2/3$, but after he knows the answer, the probability of being released will become $1/2$, since there will be two prisoners (including himself) whose fate is unknown and exactly one of the two will be released. What is wrong with this line of reasoning?

> <span style="color:#1e8449;">**[mathtip]** </span> 守卫的"信息不改变未知者集合里自己是否在列"：关键是守卫非随机地回答（总会点名一个"他人"被释放），故条件概率仍是 $2/3$，$(b)\ne$ 均匀骰式 $1/2$。

---

### Problem 25 <span style="color:#2471a3;">**[problem/main]**</span>
**A two-envelopes puzzle.** You are handed two envelopes, and you know that each contains a positive integer dollar amount and that the two amounts are different. The values of these two amounts are modeled as constants that are unknown. Without knowing what the amounts are, you select at random one of the two envelopes, and after looking at the amount inside, you may switch envelopes if you wish. A friend claims that the following strategy will increase above $1/2$ your probability of ending up with the envelope with the larger amount: toss a coin repeatedly, let $X$ be equal to $1/2$ plus the number of tosses required to obtain heads for the first time, and switch if the amount in the envelope you selected is less than the value of $X$. Is your friend correct?

> <span style="color:#1e8449;">**[mathtip]** </span> 是否换信封构成一随机阈值 $X\in\{1.5,2.5,3.5,\ldots\}$；分开 $X$ 落在两信封金额之间与否两种情形，可证明 $P(\text{拿到大者})>1/2$。朋友正确。

---

### Problem 26 <span style="color:#2471a3;">**[problem/main]**</span>
**The paradox of induction.** Consider a statement whose truth is unknown. If we see many examples that are compatible with it, we are tempted to view the statement as more probable. Such reasoning is often referred to as *inductive inference* (in a philosophical, rather than mathematical sense). Consider now the statement that "all cows are white." An equivalent statement is that "everything that is not white is not a cow." We then observe several black crows. Our observations are clearly compatible with the statement, but do they make the hypothesis "all cows are white" more likely?

To analyze such a situation, we consider a probabilistic model. Let us assume that there are two possible states of the world, which we model as complementary events:

```math
A:\ \text{all cows are white},
\qquad
A^c:\ 50\% \text{ of all cows are white}.
```

Let $p$ be the prior probability $P(A)$ that all cows are white. We make an observation of a cow or a crow, with probability $q$ and $1-q$, respectively, independent of whether event $A$ occurs or not. Assume that $0 < p < 1$, $0 < q < 1$, and that all crows are black.

**(a)** Given the event $B = \{\text{a black crow was observed}\}$, what is $P(A \mid B)$?
**(b)** Given the event $C = \{\text{a white cow was observed}\}$, what is $P(A \mid C)$?

> <span style="color:#1e8449;">**[mathtip]** </span> 关键：观测到的是一只乌鸦（概率 $1-q$）、还是一头白牛（概率 $q$）？由于 $P(B\mid A)=P(B\mid A^c)=1-q$ 与 $A$ 无关，(a) 中 $P(A\mid B)=p$；而 (b) 中 $P(A\mid C)$ 会升高。

---

### Problem 27 <span style="color:#2471a3;">**[problem/main]**</span>
Alice and Bob have $2n+1$ coins, each coin with probability of heads equal to $1/2$. Bob tosses $n+1$ coins, while Alice tosses the remaining $n$ coins. Assuming independent coin tosses, show that the probability that after all coins have been tossed, Bob will have gotten more heads than Alice is $1/2$.

> <span style="color:#1e8449;">**[mathtip]** </span> 对称性技巧：引入"第 $2n+2$ 枚硬币"作裁判硬币，配对 $n+1$ 对（每对一正一反）⇒ 谁正面更多由裁判硬币决定，概率恰为 $1/2$。

---

### Problem 28 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Conditional version of the total probability theorem.** Let $C_1, \ldots, C_n$ be disjoint events that form a partition of the state space. Let also $A$ and $B$ be events such that $P(B \cap C_i) > 0$ for all $i$. Show that

```math
P(A \mid B) \;=\; \sum_{i=1}^{n} P(C_i \mid B)\, P(A \mid B \cap C_i).
```

Solution. We have

```math
P(A \cap B) \;=\; \sum_{i=1}^{n} P\big((A \cap B) \cap C_i\big),
```

and by using the multiplication rule, $P\big((A \cap B) \cap C_i\big) = P(B \cap C_i)\, P(A \mid B \cap C_i)$ (under the appropriate conditioning). Combining these two equations, dividing by $P(B)$, and using the formula $P(A \mid B) = P(A \cap B)/P(B)$, we obtain the desired result.

> <span style="color:#1e8449;">**[mathtip]** </span> 把全概率定理在"已知 $B$"的条件空间里重述：$P(A\mid B)$ 是 $\{P(A\mid B\cap C_i)\}$ 按权重 $P(C_i\mid B)$ 的加权平均。

---

### Problem 29 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
Let $A$ and $B$ be events with $P(A) > 0$ and $P(B) > 0$. We say that an event $B$ **suggests** an event $A$ if $P(A \mid B) > P(A)$, and does **not suggest** event $A$ if $P(A \mid B) < P(A)$.

**(a)** Show that $B$ suggests $A$ if and only if $A$ suggests $B$.
**(b)** Assume that $P(B^c) > 0$. Show that $B$ suggests $A$ if and only if $B^c$ does not suggest $A$.
**(c)** We know that a treasure is located in one of two places, with probabilities $\beta$ and $1-\beta$, respectively, where $0 < \beta < 1$. We search the first place and if the treasure is there, we find it with probability $p > 0$. Show that the event of not finding the treasure in the first place suggests that the treasure is in the second place.

Solution. **(a)** We have $P(A \mid B) = P(A \cap B)/P(B)$, so $B$ suggests $A$ if and only if $P(A \cap B) > P(A)P(B)$, which is equivalent to $A$ suggesting $B$, by symmetry.

**(b)** Since $P(B) + P(B^c) = 1$, we have

```math
\begin{aligned}
P(A) &= P(B)\,P(A \mid B) + P(B^c)\,P(A \mid B^c), \\
P(B)\big(P(A \mid B) - P(A)\big) &= P(B^c)\big(P(A) - P(A \mid B^c)\big),
\end{aligned}
```

which implies that $P(A \mid B) > P(A)$ (i.e., $B$ suggests $A$) if and only if $P(A \mid B^c) < P(A)$ (i.e., $B^c$ does not suggest $A$).

**(c)** Let $A$ = event that the treasure is in the second place, so $A^c$ = event that the treasure is in the first place, and $B$ = event that we do not find the treasure in the first place. The probability $P(B)$ is given by

```math
P(B) \;=\; P(A^c)\,P(B \mid A^c) \;+\; P(A)\,P(B \mid A)
\;=\; \beta (1-p) \;+\; (1-\beta)\cdot 1
\;=\; 1 - \beta p,
```

so

```math
P(A \mid B) \;=\; \frac{P(A\cap B)}{P(B)} \;=\; \frac{(1-\beta)\cdot 1}{1-\beta p}
\;=\; \frac{1-\beta}{1-\beta p} \;>\; 1-\beta \;=\; P(A),
```

which shows that the event of not finding the treasure in the first place suggests that the treasure is in the second place. (In the above, $\beta(1-p)$ is the probability of not finding the treasure when it is actually in the first place and the search fails with probability $1-p$.)

> <span style="color:#1e8449;">**[mathtip]** </span> "suggests" ⇔ $P(A\mid B)>P(A)$ ⇔ $P(A\cap B)>P(A)P(B)$（正相关）。负事件与正事件在"是否 suggest"上必然相反（b）。

---

## Section 1.5 · Independence（事件的独立性）

### Problem 30 <span style="color:#2471a3;">**[problem/main]** 〔据残片补全〕</span>
A hunter has two hunting dogs. One day, on the trail of some animal, the tracking dog diverges into two paths. He knows from experience that each dog, independently of the other, chooses the correct path with probability $p$, and the wrong path with probability $1-p$. To decide on a path, he lets both dogs choose; if the two dogs agree, he follows them, and if they disagree, he picks a path at random. What is the probability that the hunter decides on the correct path?

> <span style="color:#1e8449;">**[mathtip]** </span> 精细概率 $p^2$（都猜对）+ $2p(1-p)\cdot\tfrac12$（一错一对、随机跟一条）对的那条概率 $\tfrac12$，求和即得正确率。

---

### Problem 31 <span style="color:#2471a3;">**[problem/main]** 〔据残片补全〕</span>
**Error probabilities in a communication channel.** A source transmits a message (a string of symbols) through a noisy communication channel. Each symbol is $0$ or $1$ with probability $1/2$, and each symbol is received incorrectly with probability $\varepsilon$, independently of all other symbols, i.e., a transmitted $0$ is received as $1$ (and vice versa) with probability $\varepsilon$.

**(a)** Find the probability that a certain symbol is received correctly.
**(b)** Find the probability that the received message differs from the transmitted message in at least one position.
**(c)** Find the probability that the received message is identical to the transmitted message.
**(d)** Given a received bit $r$, find the probability that the corresponding transmitted bit was the same. 〔(a)–(d) 细目按原图残片补全〕

> <span style="color:#1e8449;">**[mathtip]** </span> 二元对称信道，各比特独立。逐比特"接收正确"概率为 $1-\varepsilon$，整串全对为 $(1-\varepsilon)^{L}$，至少一处错为 $1-(1-\varepsilon)^{L}$。

---

### Problem 32–35 <span style="color:#2471a3;">**[problem/main]** 〔页 70–71 严重 OCR 损坏〕</span>
页 70–71 对应的第 32–35 题扫描/OCR 损坏极重，仅残留零散英文字段（如 "…or the movies…"、"…power utility can supply…"、"(d)…" 等），无法可靠复原完整题干。已尽量与教材标准内容比对，但为避免臆造，此处只作提示性占位：

> <span style="color:#1e8449;">**[mathtip]** </span> 本段习题集中在"独立事件的可加/可乘概率"与"由多个独立部件构成的系统可靠性"；常需用 $1-P(\text{全部失效})$ 反算"至少一个成功"，并会用到 $P(A\cup B)=P(A)+P(B)-P(A\cap B)$。

---

### Problem 36 <span style="color:#2471a3;">**[problem/main]**</span>
A power utility can supply electricity to a city from $n$ different power plants. Power plant $i$ fails with probability $p_i$, independently of the others.

**(a)** Suppose that any one plant can produce enough electricity to supply the entire city. What is the probability that the city will experience a black-out?
**(b)** Suppose that two power plants are necessary to keep the city from a black-out. Find the probability that the city will experience a black-out.

> <span style="color:#1e8449;">**[mathtip]** </span> (a) 停电 ⇔ 所有电厂都失效，$P=\prod_{i}(p_i)$。(b) 停电 ⇔ 同时失效的电厂 ≥ 2；用 $1-P(\text{失效}0\text{或}1\text{个})$ 反算，注意需枚举"恰好一个失效"的 $n$ 种情形（若各 $p_i$ 不同需逐项计算）。

---

### Problem 37 <span style="color:#2471a3;">**[problem/main]**</span>
A cellular phone system services a population of $n_1$ "voice users" (those who occasionally need a voice connection) and $n_2$ "data users" (those who occasionally need a data connection). We estimate that at a given time, each user will need to be connected to the system with probability $p_1$ (for voice users) or $p_2$ (for data users), independent of other users. The data rate for a voice user is $r_1$ bits/sec and for a data user is $r_2$ bits/sec. The cellular system has a total capacity of $c$ bits/sec. What is the probability that more users want to use the system than the system can accommodate?

> <span style="color:#1e8449;">**[mathtip]** </span> 设 $V\sim\mathrm{Binomial}(n_1,p_1)$、$D\sim\mathrm{Binomial}(n_2,p_2)$ 独立。所求为 $P(r_1V+r_2D>c)$，即枚举满足容量超限的 $(v,d)$ 求和。

---

### Problem 38 <span style="color:#2471a3;">**[problem/main]**</span>
**The problem of points.** Telis and Wendy play a round of golf (18 holes) for a $\$10$ stake, and their probabilities of winning on any one hole are $p$ and $1-p$, respectively, independent of their results in other holes. At the end of $10$ holes, with the score $4$ to $6$ in favor of Wendy, Telis receives an urgent call and has to report back to work. They decide to split the stake in proportion to their probabilities of winning had they completed the round, as follows. If $P_T$ and $P_W$ are the conditional probabilities that Telis and Wendy, respectively, are ahead in the score after 18 holes given the $4$-$6$ score after 10 holes, then Telis should get a fraction $P_T/(P_T + P_W)$ of the stake, and Wendy should get the remaining $P_W/(P_T + P_W)$. How much money should Telis get?

*Note:* This is an example of the so-called *problem of points*, which played an important historical role in the development of probability theory. The problem was posed by Chevalier de Méré in the 17th century to Pascal, who introduced the idea that the stake of an interrupted game should be divided in proportion to the players' conditional probabilities of winning given the state of the game at the time of interruption. Pascal worked out some special cases and through a correspondence with Fermat stimulated much thinking and several probability-related investigations.

> <span style="color:#1e8449;">**[mathtip]** </span> 已知 $4$-$6$ 落后 2 洞，剩 8 洞；Telis 要反超需胜的洞数多于对手。用二项概率 $P_T=\sum_{k} \binom{8}{k}p^k(1-p)^{8-k}$ 算出双方反超概率后按比例分 $10$ 美元。

---

### Problem 39 <span style="color:#2471a3;">**[problem/main]**</span>
A particular class has had a history of low attendance. The annoyed professor decides that she will not lecture unless at least $k$ of the $n$ students enrolled in the class are present. Each student will independently show up with probability $p_g$ if the weather is good, and with probability $p_b$ if the weather is bad. Given the probability of bad weather on a given day, obtain an expression for the probability that the professor will teach her class on that day.

> <span style="color:#1e8449;">**[mathtip]** </span> 用全概率（天气好坏两分支）：单日出席人数 $X\sim\mathrm{Binomial}(n,p_g)$ 或 $\mathrm{Binomial}(n,p_b)$，教授授课 ⇔ $X\ge k$。

---

### Problem 40 <span style="color:#2471a3;">**[problem/main]**</span>
Consider a coin that comes up heads with probability $p$ and tails with probability $1-p$. Let $q_n$ be the probability that after $n$ independent tosses, there have been an even number of heads. Derive a recursion that relates $q_n$ to $q_{n-1}$, and solve this recursion to establish the formula

```math
q_n \;=\; \frac{1 + (1 - 2p)^n}{2}.
```

> <span style="color:#1e8449;">**[mathtip]** </span> 递推：第 $n$ 次掷后偶数为 $q_n=(1-p)q_{n-1}+p(1-q_{n-1})$，即 $q_n=q_{n-1}+p(1-2q_{n-1})$；解：令 $d_n=q_n-\tfrac12$，由 $q_n=q_{n-1}+p(1-2q_{n-1})$ 得 $d_n=(1-2p)d_{n-1}$，故通式 $q_n=\tfrac12+(1-2p)^n\cdot\tfrac12=\tfrac{1+(1-2p)^n}{2}$。

---

### Problem 41 <span style="color:#2471a3;">**[problem/main]**</span>
Consider a game show with an infinite pool of contestants, where at each round $i$, contestant $i$ obtains a number by spinning a continuously calibrated wheel. The contestant with the smallest number thus far survives. Successive wheel spins are independent and we assume that there are no ties. Let $N$ be the round at which contestant 1 is eliminated. For any positive integer $n$, find $P(N = n)$.

> <span style="color:#1e8449;">**[mathtip]** </span> 独立同分布且连续（无平局）：到第 $n$ 轮存活 ⇔ 前 $n$ 个中最小的仍是 1 号（概率 $1/n$），而第 $n$ 轮出局还需第 $n$ 个更小（相对第 $n-1$ 个的最小值）。推得 $P(N=n)=\tfrac{1}{n(n-1)}$。

---

### Problem 42 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Gambler's ruin.** A gambler makes a sequence of independent bets. In each bet, he wins $\$1$ with probability $p$, and loses $\$1$ with probability $1-p$. Initially, the gambler has $\$k$, and plays until he either accumulates $\$n$ or has no money left. What is the probability that the gambler will end up with $\$n$?

Solution. Let us denote by $A$ the event that he ends up with $\$n$, and by $F$ the event that he wins the first bet. Denote also by $W_k$ the probability of event $A$, if he starts with $\$k$. We apply the total probability theorem to obtain

```math
W_k = P(A \mid F)P(F) + P(A \mid F^c)P(F^c) = p\,P(A \mid F) + q\,P(A \mid F^c),
\qquad 0 < k < n,
```

where $q = 1-p$. By the independence of past and future bets, having won the first bet is the same as if he were just starting now but with \$(k+1), so that $P(A \mid F) = W_{k+1}$ and similarly $P(A \mid F^c) = W_{k-1}$. Thus, we have $W_k = p W_{k+1} + q W_{k-1}$, which can be written as

```math
r\,W_{k+1} - W_k + W_{k-1} = 0, \qquad 0 < k < n,
```

where $r = q/p$. We will solve for $W_k$ in terms of $p$ and $q$ using iteration, and the boundary values $W_0 = 0$ and $W_n = 1$.

We have $W_{k+1} - W_k = r^k (W_1 - W_0)$, and since $W_0 = 0$,

```math
W_{k+1} = W_k + r^k W_1 = W_{k-1} + r^{k-1} W_1 + r^k W_1 = W_1 + r W_1 + \cdots + r^k W_1.
```

The sum in the right-hand side can be calculated separately for the two cases where $r = 1$ (or $p = q$) and $r \ne 1$ (or $p \ne q$). We have

```math
W_{k+1} = \begin{cases} \dfrac{1 - r^{k+1}}{1 - r}\, W_1, & \text{if } p \ne q, \\[4pt] (k+1)\, W_1, & \text{if } p = q. \end{cases}
```

Since $W_n = 1$, we can solve for $W_1$ and therefore for $W_k$:

```math
W_1 = \begin{cases} \dfrac{1-r}{1-r^{\,n}}, & \text{if } p \ne q, \\[6pt] \dfrac{1}{n}, & \text{if } p = q, \end{cases}
\qquad\text{so that}\qquad
W_k = \begin{cases} \dfrac{1-r^{\,k}}{1-r^{\,n}}, & \text{if } p \ne q, \\[6pt] \dfrac{k}{n}, & \text{if } p = q. \end{cases}
```

> <span style="color:#1e8449;">**[mathtip]** </span> 破产问题：用全概率列二阶线性递推 $W_k=pW_{k+1}+qW_{k-1}$，配合边界 $W_0=0,\;W_n=1$ 求解。设 $r=q/p$；$p=q$ 时 $W_k=k/n$，$p\ne q$ 时为 $\tfrac{1-r^k}{1-r^n}$。这是"吸收 Markov 链"的经典例。

---

### Problem 43 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
Let $A$ and $B$ be independent events. Use the definition of independence to prove the following:

**(a)** The events $A$ and $B^c$ are independent.
**(b)** The events $A^c$ and $B^c$ are independent.

Solution. **(a)** The event $A$ is the union of the disjoint events $A \cap B^c$ and $A \cap B$. Using the additivity axiom and the independence of $A$ and $B$, we obtain

```math
P(A) = P(A \cap B) + P(A \cap B^c) = P(A)P(B) + P(A \cap B^c).
```

It follows that

```math
P(A \cap B^c) = P(A)\big(1 - P(B)\big) = P(A)\,P(B^c),
```

so $A$ and $B^c$ are independent.
**(b)** Apply the result of part (a) twice: first on $A$ and $B$, then on $B^c$ and $A$.

> <span style="color:#1e8449;">**[mathtip]** </span> 由 $P(A)=P(A\cap B)+P(A\cap B^c)$ 及 $P(A\cap B)=P(A)P(B)$ 反解出 $P(A\cap B^c)=P(A)P(B^c)$ 即可。

---

### Problem 44 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
Let $A$, $B$, and $C$ be independent events, with $P(C) > 0$. Prove that $A$ and $B$ are conditionally independent given $C$.

Solution. We have

```math
\begin{aligned}
P(A \cap B \mid C) &= \frac{P(A \cap B \cap C)}{P(C)}
 = \frac{P(A)P(B)P(C)}{P(C)} \\
&= P(A)P(B) = P(A \mid C)\,P(B \mid C),
\end{aligned}
```

so $A$ and $B$ are conditionally independent given $C$. In the preceding calculation, the first equality uses the definition of conditional probabilities; the second uses the assumed independence; the fourth uses the independence of $A$ from $C$, and of $B$ from $C$.

> <span style="color:#1e8449;">**[mathtip]** </span> 三事件全独立 ⇒ 任取一事件作条件后仍独立（条件独立）。直接代入定义并利用全独立分解 $P(A\cap B\cap C)=P(A)P(B)P(C)$。

---

### Problem 45 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
Assume that the events $A_1, A_2, A_3, A_4$ are independent and that $P(A_3 \cap A_4) > 0$. Show that

```math
P(A_1 \cup A_2 \mid A_3 \cap A_4) \;=\; P(A_1 \cup A_2).
```

Solution. We have

```math
P(A_1 \mid A_3 \cap A_4) = \frac{P(A_1 \cap A_3 \cap A_4)}{P(A_3 \cap A_4)} = \frac{P(A_1)P(A_3)P(A_4)}{P(A_3)P(A_4)} = P(A_1).
```

We similarly obtain $P(A_2 \mid A_3 \cap A_4) = P(A_2)$ and $P(A_1 \cap A_2 \mid A_3 \cap A_4) = P(A_1 \cap A_2)$, and finally,

```math
\begin{aligned}
P(A_1 \cup A_2 \mid A_3 \cap A_4) &= P(A_1 \mid A_3 \cap A_4) + P(A_2 \mid A_3 \cap A_4) - P(A_1 \cap A_2 \mid A_3 \cap A_4) \\
&= P(A_1) + P(A_2) - P(A_1 \cap A_2) = P(A_1 \cup A_2).
\end{aligned}
```

> <span style="color:#1e8449;">**[mathtip]** </span> 独立 ⇒ 与其他事件（及其交）条件无关。逐项把 $P(\cdot\mid A_3\cap A_4)$ 化为无条件概率，再用并的概率公式合并即可。

---

### Problem 46 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Laplace's rule of succession.** Consider $m+1$ boxes with the $k$th box containing $k$ red balls and $m-k$ white balls, where $k$ ranges from $0$ to $m$. We choose a box at random (all boxes are equally likely) and then choose a ball at random from that box, successive times (the ball drawn is replaced each time, and a new ball is selected independently). Suppose a red ball was drawn each of the $n$ times. What is the probability that if we draw a ball one more time it will be red? Estimate this probability for large $m$.

Solution. We want to find the conditional probability $P(E \mid R_n)$, where $E$ is the event of a red ball drawn at time $n+1$, and $R_n$ is the event of a red ball drawn each of the $n$ preceding times. Intuitively, the consistent draw of a red ball indicates that a box with a high percentage of red balls was chosen, so we expect that $P(E \mid R_n)$ is closer to $1$ than to $0$. In fact, Laplace used this example to calculate the probability that the sun will rise tomorrow given that it has risen for the preceding 5,000 years. (It is not clear how serious Laplace was about this calculation, but the story is part of the folklore of probability theory.)

We have

```math
P(E \mid R_n) = \frac{P(E \cap R_n)}{P(R_n)},
```

and by using the total probability theorem, we obtain

```math
P(R_n) = \sum_{k=0}^{m} P(k\text{-th box chosen})\left(\frac{k}{m}\right)^n = \frac{1}{m+1}\sum_{k=0}^{m} \left(\frac{k}{m}\right)^n,
```

```math
P(E \cap R_n) = P(R_{n+1}) = \frac{1}{m+1}\sum_{k=0}^{m} \left(\frac{k}{m}\right)^{n+1}.
```

For large $m$, we can view $P(R_n)$ as a piecewise constant approximation to an integral:

```math
P(R_n) = \frac{1}{m+1}\sum_{k=0}^{m}\left(\frac{k}{m}\right)^n \;\approx\; \frac{1}{m+1}\cdot m \int_0^1 x^n\, dx
\;=\; \frac{m}{m+1}\cdot\frac{1}{n+1} \;\approx\; \frac{1}{n+1}.
```

Similarly,

```math
P(E \cap R_n) = P(R_{n+1}) \;\approx\; \frac{1}{n+2},
```

so that

```math
P(E \mid R_n) \;\approx\; \frac{n+1}{n+2}.
```

Thus, for large $m$, drawing a red ball one more time is almost certain when $n$ is large.

> <span style="color:#1e8449;">**[mathtip]** </span> 继位规则 $\frac{n+1}{n+2}$：把"未知盒子"当作参数，红球连续出现会更新其后验分布；用积分近似离散加权矩。这就是"太阳明日升起"的拉普拉斯荒谬用法出处。

---

### Problem 47 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Binomial coefficient formula and the Pascal triangle.**

**(a)** Use the definition of $\binom{n}{k}$ as the number of distinct $n$-toss sequences with $k$ heads, to derive the recursion suggested by the so called Pascal triangle, given in Fig. 1.20.

**(b)** Use the recursion derived in part (a) and induction, to establish the formula

```math
\binom{n}{k} = \frac{n!}{k!\,(n-k)!}.
```

Solution. **(a)** Note that $n$-toss sequences that contain $k$ heads (for $0 < k < n$) can be obtained in two ways:

1. By starting with an $(n-1)$-toss sequence that contains $k$ heads and adding a tail at the end. There are $\binom{n-1}{k}$ different sequences of this type.
2. By starting with an $(n-1)$-toss sequence that contains $k-1$ heads and adding a head at the end. There are $\binom{n-1}{k-1}$ different sequences of this type.

Each term $\binom{n}{k}$ in the array (Pascal's triangle) is the sum of its two neighbors in the row above it (except for the boundary terms with $k=0$ or $k=n$, which are equal to $1$):

```math
\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k},
\qquad \text{if } 1 \le k \le n-1.
```

This is the formula corresponding to the Pascal triangle calculation, given in Fig. 1.20.

**(b)** We now use induction on $n$. We have $\binom{n}{0} = \binom{n}{n} = 1$, so $n = 1$ holds. The above formula is seen to hold as long as we use the convention $0! = 1$. If the formula holds for each index up to $n-1$, we have for $k = 1, 2, \ldots, n-1$:

```math
\begin{aligned}
\binom{n}{k} &= \binom{n-1}{k-1} + \binom{n-1}{k} \\
&= \frac{(n-1)!}{(k-1)!\,(n-k)!} + \frac{(n-1)!}{k!\,(n-1-k)!} \\
&= \frac{k\,(n-1)!}{k!\,(n-k)!} + \frac{(n-k)\,(n-1)!}{k!\,(n-k)!} \\
&= \frac{n!}{k!\,(n-k)!},
\end{aligned}
```

and the induction is complete.

> <span style="color:#1e8449;">**[mathtip]** </span> 杨辉三角递推 $\binom{n}{k}=\binom{n-1}{k-1}+\binom{n-1}{k}$：按"末位是头或尾"分类；再用阶乘公式代入递推右端完成归纳。

---

### Problem 48 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**The probability of success at the $i$th trial is some positive number $p_i$.** Consider an infinite sequence of trials. Let $N$ be the event that there is no success, and let $I$ be the event that there is an infinite number of successes.

**(a)** Assume that the trials are independent and that $\sum_{i=1}^{\infty} p_i = \infty$. Show that $P(N) = 0$ and $P(I) = 1$.
**(b)** Assume that $\sum_{i=1}^{\infty} p_i < \infty$. Show that $P(I) = 0$.

Solution. **(a)** The event $N$ is a subset of the event that there were no successes in the first $n$ trials, so that

```math
P(N) \;\le\; \prod_{i=1}^{n} (1 - p_i).
```

Taking logarithms,

```math
\log P(N) \le \sum_{i=1}^{n} \log(1-p_i) \le - \sum_{i=1}^{n} p_i .
```

Taking the limit as $n$ tends to infinity, we obtain $\log P(N) = -\infty$, or $P(N) = 0$. Let now $L_n$ be the event that there is a finite number of successes and that the last success occurs at the $n$th trial. We use the already established result $P(N) = 0$, and apply it to the sequence of trials after trial $n$, to obtain $P(L_n) = 0$. The event (finite number of successes) is the union of the disjoint events $L_n$, $n \ge 1$, and $N$, so that

```math
P(I^c) = P(N) + \sum_{n=1}^{\infty} P(L_n) = 0,
```

and $P(I) = 1$.

**(b)** Let $S_i$ be the event that the $i$th trial is a success. Fix some number $n$ and for every $i > n$, let $F_i$ be the event that the first success after time $n$ occurs at time $i$. Note that $F_i \subseteq S_i$. Finally, let $A_n$ be the event that there is at least one success after time $n$. Note that $I \subseteq A_n$, because an infinite number of successes implies that there are successes subsequent to time $n$. Furthermore, the event $A_n$ is the union of the disjoint events $F_i$, $i > n$. Therefore,

```math
P(I) \le P(A_n) = P\left(\bigcup_{i>n} F_i\right) = \sum_{i>n} P(F_i) \le \sum_{i>n} P(S_i) = \sum_{i>n} p_i .
```

We take the limit of both sides as $n \to \infty$. Because of the assumption $\sum_{i=1}^{\infty} p_i < \infty$, the right-hand side converges to zero. This implies that $P(I) = 0$.

> <span style="color:#1e8449;">**[mathtip]** </span> **Borel–Cantelli 引理**雏形：$\sum p_i=\infty$ 且独立 ⇒ 无限多次成功（对数法估计 $\prod(1-p_i)$）；$\sum p_i<\infty$ ⇒ 成功次数有限（用尾和 $\sum_{i>n}p_i\to0$ 夹出 $P(I)=0$）。

---

## Section 1.6 · Counting（计数）

### Problem 49 <span style="color:#2471a3;">**[problem/main]**</span>
**De Méré's puzzle.** A six-sided die is rolled three times independently. Which is more likely: a sum of $11$ or a sum of $12$? (This question was posed by the French nobleman de Méré to his friend Pascal in the 17th century.)

> <span style="color:#1e8449;">**[mathtip]** </span> 计数有序三元组：和为 11 的 $(a,b,c)$ 组合数比和为 12 的多（11 更多"重复较少"的有序排列）。逐一枚举或用"隔板法/容斥"去重计算。

---

### Problem 50 <span style="color:#2471a3;">**[problem/main]**</span>
**The birthday problem.** Consider $n$ people who are attending a party. We assume that every person has an equal probability of being born on any day during the year, independent of everyone else, and ignore the additional complication presented by leap years (i.e., assume that nobody is born on February 29). What is the probability that each person has a distinct birthday?

> <span style="color:#1e8449;">**[mathtip]** </span> 全部生日不同：$365\cdot 364\cdots(365-n+1)/365^{n}$（需 $n\le 365$）。这就是著名的生日悖论：$n\ge 23$ 时有两个人生日相同概率已过半数。

---

### Problem 51 <span style="color:#2471a3;">**[problem/main]**</span>
An urn contains $m$ red and $n$ white balls.

**(a)** We draw two balls randomly and simultaneously. Describe the sample space and calculate the probability that the selected balls are of different color, by using two approaches: a counting approach based on the discrete uniform law, and a sequential approach based on the multiplication rule.

**(b)** We roll a fair 3-sided die whose faces are labeled $1, 2, 3$, and if $k$ comes up, we remove $k$ balls from the urn at random and put them aside. Describe the sample space and calculate the probability that all of the balls drawn are red, using a divide-and-conquer approach and the total probability theorem.

> <span style="color:#1e8449;">**[mathtip]** </span> (a) 不同色 $=\tfrac{2mn}{(m+n)(m+n-1)}$（先"一红一白/一白一红"两条路径）。(b) 用全概率对 $k=1,2,3$ 求和，各支为不放回"全红"的超几何概率。

---

### Problem 52 <span style="color:#2471a3;">**[problem/main]**</span>
We deal from a well-shuffled 52-card deck. Calculate the probability that the 13th card is the first king to be dealt.

> <span style="color:#1e8449;">**[mathtip]** </span> 前 12 张无 K、第 13 张是 K：$\tfrac{48\cdot47\cdots37\cdot 4}{52\cdot51\cdots40}$；等价于把 4 张 K 看作"下界"，关注它们相对非 K 卡的插入位置。

---

### Problem 53 <span style="color:#2471a3;">**[problem/main]**</span>
Ninety students, including Joe and Jane, are to be split into three classes of equal size, and this is to be done at random. What is the probability that Joe and Jane end up in the same class?

> <span style="color:#1e8449;">**[mathtip]** </span> 固定 Joe 后再看；或直接用无序分组计数。全排九十分三组 $\tfrac{90!}{(30!)^3\cdot 3!}$，同组情形为"同入一组的组合数"之比（可用"先放 Joe 再选 Jane"更简）。

---

### Problem 54 <span style="color:#2471a3;">**[problem/main]**</span>
Twenty distinct cars park in the same parking lot every day. Ten of these cars are US-made, while the other ten are foreign-made. The parking lot has exactly twenty spaces, all in a row, so the cars park side by side. However, the drivers have varying schedules, so the position any car might take on a certain day is random.

**(a)** In how many different ways can the cars line up?
**(b)** What is the probability that on a given day, the cars will park in such a way that they alternate (no two US-made are adjacent and no two foreign-made are adjacent)?

> <span style="color:#1e8449;">**[mathtip]** </span> (a) $20!$。(b) 交替停列恰 $2\cdot 10!\cdot 10!$（US/foreign 谁打头 2 种，内部各 $10!$），概率为其比上 $20!$。

---

### Problem 55 <span style="color:#2471a3;">**[problem/main]**</span>
Eight rooks are placed in distinct squares of an $8 \times 8$ chessboard, with all possible placements being equally likely. Find the probability that all the rooks are safe from one another, i.e., that there is no row or column with more than one rook.

> <span style="color:#1e8449;">**[mathtip]** </span> 不相攻 ⇔ 恰每行每列一个车：每个车占不同行、不同列，安全布法数为 $8!$（行固定、列排列）；总布法为 $\binom{64}{8}$。概率 $=8!/\binom{64}{8}$。

---

### Problem 56 <span style="color:#2471a3;">**[problem/main]**</span>
An academic department offers $8$ lower level courses: $\{L_1, L_2, \ldots, L_8\}$ and $10$ higher level courses: $\{H_1, H_2, \ldots, H_{10}\}$. A valid curriculum consists of $4$ lower level courses, and $3$ higher level courses.

**(a)** How many different curricula are possible?

**(b)** Suppose that $\{H_1, \ldots, H_5\}$ have $L_1$ as a prerequisite, and $\{H_6, \ldots, H_{10}\}$ have $L_2$ and $L_3$ as prerequisites, i.e., any curricula which involve, say, one of $\{H_1, \ldots, H_5\}$ must also include $L_1$. How many different curricula are there?

> <span style="color:#1e8449;">**[mathtip]** </span> (a) $\binom{8}{4}\binom{10}{3}$。(b) 按所选 3 门高级课是否含 $\{H_1,\ldots,H_5\}$/$\{H_6,\ldots,H_{10}\}$ 分类，对应的 4 门低级课必须先含 $L_1$ 或 $\{L_2,L_3\}$，分情形相乘求和。

---

### Problem 57 <span style="color:#2471a3;">**[problem/main]**</span>
How many 6-word sentences can be made using each of the 26 letters of the alphabet exactly once? A word is defined as a nonempty (possibly gibberish) sequence of letters.

> <span style="color:#1e8449;">**[mathtip]** </span> 把 26 个字母排成一列，再在 25 个间隔中选 5 处放空格分成 6 段：$26! \cdot \binom{25}{5}$。

---

### Problem 58 <span style="color:#2471a3;">**[problem/main]**</span>
We draw the top 7 cards from a well-shuffled standard 52-card deck. Find the probability that:

**(a)** The 7 cards include exactly 3 aces.
**(b)** The 7 cards include exactly 2 kings.
**(c)** The probability that the 7 cards include exactly 3 aces, or exactly 2 kings, or both.

> <span style="color:#1e8449;">**[mathtip]** </span> (a) $\tfrac{\binom{4}{3}\binom{48}{4}}{\binom{52}{7}}$；(b) $\tfrac{\binom{4}{2}\binom{48}{5}}{\binom{52}{7}}$；(c) 用 $P(A)+P(B)-P(A\cap B)$，交点"恰好 3 A 且 2 K"为 $\tfrac{\binom{4}{3}\binom{4}{2}\binom{44}{2}}{\binom{52}{7}}$。

---

### Problem 59 <span style="color:#2471a3;">**[problem/main]**</span>
A parking lot contains 100 cars, $k$ of which happen to be lemons. We select $m$ of these cars at random and take them for a test drive. Find the probability that $n$ of the cars tested turn out to be lemons.

> <span style="color:#1e8449;">**[mathtip]** </span> 超几何分布：$P=\tfrac{\binom{k}{n}\binom{100-k}{m-n}}{\binom{100}{m}}$（$n$ 须满足 $0\le n\le k$、$0\le m-n\le 100-k$）。

---

### Problem 60 <span style="color:#2471a3;">**[problem/main]**</span>
A well-shuffled 52-card deck is dealt to 4 players. Find the probability that each of the players gets an ace.

> <span style="color:#1e8449;">**[mathtip]** </span> 把 4 张 A 摊给四人（$4!$ 种）+ 其余 48 张自由分（$48!/(12!)^4$），除以全分法 $52!/(13!)^4$；概率 $=\tfrac{4!(13)^4}{52\cdot51\cdot50\cdot49}\approx0.1055$ 实际化简为每把得一张 A。

---

### Problem 61 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Hypergeometric probabilities.** An urn contains $n$ balls, out of which $m$ are red. We select $k$ of the balls at random, without replacement (i.e., selected balls are not put back into the urn before the next selection). What is the probability that $i$ of the selected balls are red?

Solution. The sample space consists of the $\binom{n}{k}$ different ways that we can select $k$ out of the available balls. For the event of interest to occur, we have to select $i$ out of the $m$ red balls, which can be done in $\binom{m}{i}$ ways, and also select $k-i$ out of the $n-m$ balls that are not red, which can be done in $\binom{n-m}{k-i}$ ways. Therefore, the desired probability is

```math
P(\text{selected balls include } i \text{ red}) = \frac{\binom{m}{i}\,\binom{n-m}{k-i}}{\binom{n}{k}},
```

for $i$ satisfying $0 \le i$, $i \le m$, $i \le k$, and $k-i \le n-m$. For all other $i$, the probability is zero.

> <span style="color:#1e8449;">**[mathtip]** </span> 超几何分布：分子"取 $i$ 红 + $k-i$ 非红"的组合数，分母 $\binom{n}{k}$。不放回（无替换）抽样即此分布。

---

### Problem 62 <span style="color:#2471a3;">**[problem/main]** *（附解答）</span>
**Correcting the number of permutations for indistinguishable objects.** When permuting $n$ objects, some of which are indistinguishable, different permutations may lead to indistinguishable object sequences, so the number of distinguishable object sequences is less than $n!$. For example, there are six permutations of the letters A, B, and C:

```math
ABC,\quad ACB,\quad BAC,\quad BCA,\quad CAB,\quad CBA,
```

but only three distinguishable sequences that can be formed using the letters A, D, and D:

```math
ADD,\quad DAD,\quad DDA.
```

**(a)** Suppose that $k$ out of the objects are indistinguishable. Show that the number of distinguishable object sequences is $n!/k!$.

**(b)** Suppose that we have $r$ types of indistinguishable objects, and for each $i$, $k_i$ objects of type $i$. Show that the number of distinguishable object sequences is

```math
\frac{n!}{k_1!\,k_2!\,\cdots\,k_r!}.
```

Solution. **(a)** Each one of the $n!$ permutations corresponds to $k!$ duplicates which are obtained by permuting the $k$ indistinguishable objects. Thus, the $n!$ permutations can be grouped into $n!/k!$ groups of $k!$ indistinguishable permutations that result in the same object sequence. Therefore, the number of distinguishable object sequences is $n!/k!$. For example, the three letters A, D, and D give the $3! = 6$ permutations

```math
ADD,\quad ADD,\quad DAD,\quad DDA,\quad DAD,\quad DDA,
```

obtained by replacing B and C by D in the permutations of A, B, and C given earlier. However, these 6 permutations can be divided into the $n!/k! = 3!/2! = 3$ groups $\{ADD, ADD\}$, $\{DAD, DAD\}$, $\{DDA, DDA\}$, each having $k! = 2! = 2$ indistinguishable permutations.

**(b)** One solution is to extend the argument in (a) above: for each object type $i$, there are $k_i!$ indistinguishable permutations of the $k_i$ objects. Hence, each permutation belongs to a group of $k_1!\,k_2!\cdots k_r!$ indistinguishable permutations, all of which yield the same object sequence.

An alternative argument goes as follows. Choosing a distinguishable object sequence is the same as starting with $n$ slots and for each $i$, choosing the $k_i$ slots to be occupied by objects of type $i$. This is the same as partitioning the set $\{1,\ldots,n\}$ into groups of size $k_1, \ldots, k_r$, and the number of such partitions is given by the multinomial coefficient:

```math
\frac{n!}{k_1!\,k_2!\cdots k_r!}.
```

> <span style="color:#1e8449;">**[mathtip]** </span> 多重排列 / 多项式系数：对每种"同类"对象除以内部排列数 $k_i!$，即"排列去重"。等价于把 $n$ 个位置按 $k_1,\ldots,k_r$ 分组。

---

## 页 81–82（批尾说明）

> <span style="color:#7f8c8d;">页 81</span> 是第 2 章 **Discrete Random Variables（离散随机变量）** 的 "Contents"（目录）页；页 82 是该章 §2.1 正文开头（描述随机变量概念的叙述文本）。二者均不属于第 1 章习题区。页 82 上半部分扫描/OCR 损坏严重，仅为章节正文的叙述性文字（非习题），本批不再展开，后续应在第 2 章对应批次处理。

**本批核对**：页 63–80 覆盖第 1 章全部习题（Problems 1–62），共 **62 题**，全部保留英文题干并按节整理；页 81–82 为第 2 章开头，不在本章习题范围。页 70–71（习题 30–35 一带）OCR 严重损坏，其中 30、31 已尽力补全，32–35 仅作占位标注。无未截断题目；公式均以 math 块/行内式保留。
<!-- ===== batch02_C ===== -->
# <span style="color:#c0392b;">第 2 章　离散随机变量（Discrete Random Variables）</span>

## <span style="color:#c0392b;">2.1　基本概念（Basic Concepts）</span>

（承接上文）正反面（heads and tails）的组合不被视为一个随机变量，因为它没有明确的数值。

（b）在掷两次骰子的实验中，下列都是随机变量的例子：
（i）两次掷骰结果之和。
（ii）两次掷骰中出现点数 6 的次数。
（iii）第二次掷骰结果的五次方。

（c）在传输一条消息的实验中，传输该消息所需的时间、错误接收到的符号个数，以及消息被接收到的延迟，都是随机变量。

与随机变量相关的基本概念有许多，现概述如下。这些概念将在本章中详细讨论。

### <span style="color:#c0392b;">与随机变量相关的主要概念（Main Concepts Related to Random Variables）</span>

从实验的概率模型出发：

<span style="color:#00838f;">**[definition] 随机变量（`random variable`）**</span>

> 随机变量（random variable）是实验结果的实值函数（real-valued function）。

- 随机变量的函数定义出另一个随机变量。
- 我们可以把某些感兴趣的"平均值"与每个随机变量关联起来，例如均值（mean）和方差（variance）。
- 随机变量可以相对于一个事件或另一个随机变量进行条件化（conditioned）。
- 随机变量与某个事件、或与另一个随机变量之间，存在独立（independence）的概念。

<span style="color:#00838f;">**[definition] 离散随机变量（`discrete`）**</span>

> 如果一个随机变量的取值范围（即它可以取到的所有值的集合）是有限的或可数无限的（countably infinite），则称之为离散的（discrete）。例如，上面（a）和（b）中提到的随机变量至多可取有限个数值，因此它们是离散的。

可以取不可数无限（uncountably infinite）多个值的随机变量不是离散的。例如，考虑从区间 $[-1, 1]$ 中选取一点 $a$ 的实验。将数值 $a^2$ 与结果 $a$ 相关联的随机变量不是离散的。另一方面，将与 $a$ 相关联的数值

```math
\text{sgn}(a) = \begin{cases} 1, & \text{若 } a > 0, \\ 0, & \text{若 } a = 0, \\ -1, & \text{若 } a < 0 \end{cases}
```

的随机变量是离散的。

在本章中，我们只专注于离散随机变量，尽管我们通常省略"离散"这一限定词。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 随机变量是把"结果"翻译成"数字"的翻译官：它就是在样本空间上定义的一个实值函数 $X:\Omega\to\mathbb R$。你之前学函数时（比如线性代数中的线性映射），关心的是从一种结构到另一种结构的对应；随机变量的独特之处在于，它把概率的"权重"整个搬运到数轴上——每个数字 $x$ 得到的分量恰是 $P(X=x)$。这正是从"事件概率"迈向"分布"的关键一步：后面所有内容（期望、方差、条件分布）几乎都是在这个"数轴上的概率分配"上操作的。离散与连续的界限也由此划定：值域有限或可数无限就离散，否则连续——正如教材例子所示，$a\mapsto a^2$ 在 $[-1,1]$ 上取不可数个值所以不是离散的，而 $\text{sgn}(a)$ 只取 $-1,0,1$ 三个值所以是离散的。把随机变量想成"测度空间上映射到实数的可测函数"，在将来的实分析（100B 测度与积分一章）里会无缝衔接。

### <span style="color:#c0392b;">与离散随机变量相关的概念（Concepts Related to Discrete Random Variables）</span>

从实验的概率模型出发：

- 离散随机变量是实验结果的实值函数，它可以取有限或可数无限多个值。
- 离散随机变量有一个关联的概率质量函数（probability mass function，PMF），它给出该随机变量可以取到的每一个数值的概率。
- 离散随机变量的函数定义出另一个离散随机变量，其 PMF 可以由原随机变量的 PMF 得到。

我们将在后续各节中逐一讨论上述概念及相关方法。此外，我们还将给出一些重要且常见的随机变量的例子。在第 3 章中，我们将讨论一般的（不一定是离散的）随机变量。

尽管本章可能看似涉及大量新内容，但事实并非如此。总体的发展思路仅仅是把第 1 章中的概念（概率、条件化、独立性等）应用于随机变量而非事件，同时引入一些方便的新记号。唯一真正全新的概念与均值和方差有关。

## <span style="color:#c0392b;">2.2　概率质量函数（Probability Mass Functions）</span>

<span style="color:#00838f;">**[definition] 概率质量函数 PMF（`probability mass function`）**</span>

> 刻画随机变量最重要的方式是通过它所取各值的概率。对于一个离散随机变量 $X$，这些概率由 $X$ 的概率质量函数（简称 PMF）来刻画，记作 $p_X$。特别地，如果 $x$ 是 $X$ 的一个可能取值，则 $x$ 的概率质量（probability mass），记作 $p_X(x)$，是事件 $\{X = x\}$ 的概率，该事件由所有使 $X$ 取值为 $x$ 的结果组成：

```math
p_X(x) = P\big(\{X = x\}\big).
```

例如，设实验由两次独立的公平硬币掷投组成，并设 $X$ 为得到正面的次数。那么 $X$ 的 PMF 为

```math
p_X(x) = \begin{cases} 1/4, & \text{若 } x = 0 \text{ 或 } x = 2, \\ 1/2, & \text{若 } x = 1, \\ 0, & \text{其他情况。} \end{cases}
```

在后续内容中，当不会产生歧义时，我们常常省略事件/集合记号中的大括号。特别是，我们通常用 $P(X = x)$ 代替更规范的记号 $P(\{X = x\})$，并用 $P(X \in S)$ 表示 $X$ 取 $S$ 这个集合内某个值的概率。我们还将在全书中遵循以下约定：用大写字母表示随机变量，用小写字母表示实数，例如随机变量的数值。

注意

```math
\sum_x p_X(x) = 1,
```

其中上面的求和式中，$x$ 遍历 $X$ 的所有可能数值。这由可加性与归一化公理（additivity and normalization axioms）得出：当 $x$ 遍历 $X$ 的所有可能取值时，事件 $\{X = x\}$ 互不相交且构成样本空间的一个划分。类似地，对 $X$ 的任意取值集合 $S$，我们有

```math
P(X \in S) = \sum_{x \in S} p_X(x).
```

例如，如上面那样，若 $X$ 是两次独立公平硬币掷投中得到正面的次数，则至少出现一次正面的概率为

```math
P(X > 0) = \sum_{x=1}^{2} p_X(x) = \frac{1}{2} + \frac{1}{4} = \frac{3}{4}.
```

计算 $X$ 的 PMF 在概念上是直截了当的，如图 2.2 所示。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> PMF 的归一化 $\sum_x p_X(x)=1$ 不是偶然，而是概率公理中可加性加归一化的直接翻译：事件 $\{X=x\}$ 互不相交，并对 $x$ 取遍可能值时并起来正好是整个样本空间。把概率理解为"定义在事件上的测度"，你在实分析（100B 的测度与积分章）里会见到完全相同的语言：PMF 就是定义在可数值集上的"数数密度"，离散情形的"积分"退化为求和 $\sum_x$，而总和为 1 正是"总测度为 1"的高傲复述。这也解释了为何后面期望会要求 $\sum_x |x|p_X(x)<\infty$——可与测度论的 $\ell^1$ 可积条件同构，确保无限求和不因重排而改变。简言之，给定一条 PMF，等于给出该离散随机变量的全部"性格"：任何事件的概率、均值、方差都由它唯一决定，之后的章节几乎都是在给这条"质量分配曲线"做各种统计加工。

### <span style="color:#c0392b;">随机变量 $X$ 的 PMF 的计算（Calculation of the PMF of a Random Variable X）</span>

对 $X$ 的每一个可能取值 $x$：

1. 收集所有给出事件 $\{X = x\}$ 的可能结果。
2. 将这些结果的概率相加，得到 $p_X(x)$。

### <span style="color:#c0392b;">伯努利随机变量（The Bernoulli Random Variable）</span>

<span style="color:#00838f;">**[definition] 伯努利随机变量（`Bernoulli random variable`）**</span>

> 考虑掷一次硬币，它以概率 $p$ 出现正面，以概率 $1-p$ 出现反面。伯努利随机变量取两个值 1（正面）与 0（反面）。其 PMF 为

```math
p_X(0) = 1 - p, \qquad p_X(1) = p.
```

<!-- 本批在页 85–86 之间经过了图 2.2 的插图说明。 -->

**图 2.2**　计算一个随机变量 $X$ 的 PMF 方法的说明。$X$ 是掷两次公平四面体骰子的最大点数值。有四种可能取值 $X = 1, 2, 3, 4$。要计算 $p_X(x)$，我们把那些给出 $X = x$ 的结果的概率相加。例如，存在三个结果给出 $X = 2$（即 $(1,2)$、$(2,1)$、$(2,2)$），每个结果概率为 $1/16$，因此得出 $p_X(2)$ 的值，如图所示。

### <span style="color:#c0392b;">二项随机变量（The Binomial Random Variable）</span>

若某人有两种可能身份且都属于某类结果，则该事件可被看作一次伯努利式试验（Bernoulli trial）。这类试验的例子有：一个人可以生病或健康（患病），在某事件上支持或反对等。

<span style="color:#00838f;">**[definition] 二项随机变量（`binomial random variable`）**</span>

> 在实际中，我们常遇到满足以下条件的二项随机变量（binomial random variable）场景：一次试验要么成功（success）要么失败（failure），互斥且穷尽；试验重复 $n$ 次，每次成功概率 $p$ 相同且相互独立；随机变量 $X$ 等于成功的总次数。例如：一枚硬币被掷 $n$ 次，$X$ 为得到正面的次数。若硬币以概率 $p$ 出现正面、以概率 $1-p$ 出现反面，则 $X$ 的概率质量函数为

```math
p_X(k) = \binom{n}{k} p^k (1-p)^{n-k}, \qquad k = 0, 1, \ldots, n.
```

（注意我们使用符号 $k$ 来表示整数值随机变量的取值，以简化记号。）归一化性质 $\sum_{k=0}^{n} \binom{n}{k} p^k (1-p)^{n-k} = 1$ 成立，其图为图 2.3。

**图 2.3**　一个二项随机变量的 PMF。（a）若 $p = 1/2$，则 PMF 关于 $n/2$ 对称；（b）若 $p < 1/2$，PMF 偏向 0 一侧；若 $p > 1/2$，则偏向 $n$ 一侧。

注意，伯努利随机变量是二项随机变量在 $n=1$ 时的特殊情形。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 请把伯努利随机变量看作整个离散分布的"积木"：它只取 0/1 两个值，却是二项分布的原子。二项随机变量不过就是 $n$ 个独立同分布的伯努利之和 $X=\sum_{i=1}^{n}B_i$，这个视角在算法设计课《CLRS》（Introduction to Algorithms）第 5 章 Probabilistic Analysis and Randomized Algorithms 里被称为"指示随机变量（indicator random variable）"，专用于瞬间算出大量期望。一旦你掌握第四章的期望线性性 $E[X]=\sum_i E[B_i]$，本节的 $E[X]=np$、$\operatorname{var}(X)=np(1-p)$ 就不必逐项对 $k$ 求和，几乎动笔即得。养成"把复杂随机变量拆成一串独立伯努利之和、再逐个取期望"的直觉，是把随机算法、散列分析这类问题迅速算平的核心技能，也是后面"随机变量和的期望、方差"两块正规理论的直观源头。

### <span style="color:#c0392b;">几何随机变量（The Geometric Random Variable）</span>

<span style="color:#00838f;">**[definition] 几何随机变量（`geometric random variable`）**</span>

> 设想我们重复进行独立试验，直到出现首次成功为止，其中每次试验的成功概率为 $p$。若以概率 $1-p$ 继续出现失败、以概率 $p$ 出现成功，则首次成功会到来的尝试次数（trials）是随机变量 $X$，其取值为 $k$ 的概率等于前 $k-1$ 次失败后跟随第 $k$ 次成功的概率，故

```math
p_X(k) = (1-p)^{k-1} p, \qquad k = 1, 2, \ldots
```

该几何分布的 PMF 如图 2.4 所示。若 $X$ 服从几何分布，则 $E[X] = 1/p$。图中显示了归一化：$\sum_{k=1}^{\infty} p_X(k) = p \sum_{k=1}^{\infty} (1-p)^{k-1} = p \cdot \frac{1}{1-(1-p)} = 1$。该分布随 $k$ 以几何速率递减。

**图 2.4**　几何随机变量的 PMF。$p_X(k) = (1-p)^{k-1}p$ 随 $k$ 呈几何级数递减。其在每次试验成功概率 $p$ 恒定、试验重复进行时成立。几何随机变量的实际例子：通过给定科目测试所需的尝试次数等。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 几何分布刻画"等待"：等待首次成功的次数，其 PMF $p_X(k)=(1-p)^{k-1}p$ 以几何速率衰减，正是"每天成功概率恒为 $p$"的直接后果。它最深刻的性质是无记忆性（memoryless）：已知已经等了 $m$ 次仍未成功，从此刻起还要再等多久的分布，与从零起步完全相同——因为过去的失败并不会改变"下ー次"成功概率 $p$。这一性质使"几何"与"无记忆"在随机过程理论里几乎成了同义词（泊松过程里的等待时间就是指数分布的连续版、几何分布的连续对应），而它的均值 $E[X]=1/p$（本节正文已给出）会在后续章节用几何级数或记忆性给出正式推导。直观上，一个"记不住失败经历"的系统，其剩余寿命与已等待时间无关，这正是"每次试验独立"这一假设被压进一个极简分布的极端体现：多次跌倒，概率不因跌倒而倾斜。

### <span style="color:#c0392b;">泊松随机变量（The Poisson Random Variable）</span>

<span style="color:#00838f;">**[definition] 泊松随机变量（`Poisson random variable`）**</span>

> 一个泊松随机变量（Poisson random variable）具有如下形式的 PMF

```math
p_X(k) = \frac{e^{-\lambda} \lambda^k}{k!}, \qquad k = 0, 1, 2, \ldots
```

归一化条件 $\sum_{k=0}^{\infty} e^{-\lambda}\lambda^k/k! = 1$ 成立。它常用于计数"稀有"事件的发生次数，例如：某城市一天内收到多封错误投递信件、某段时间内电话交换台接收到的呼叫数，或者寻找某样遗失物品时所需的尝试次数等。

**图 2.5**　泊松随机变量在不同 $\lambda$ 取值下的 PMF $e^{-\lambda}\lambda^k/k!$。注意，若 $\lambda < 1$，则 PMF 随 $k$ 递减；而若 $\lambda > 1$，PMF 先增后减（这在章末习题中说明）。

泊松分布常用作二项分布（binomial distribution）的近似：当二项试验次数 $n$ 很大、而成功概率 $p$ 很小、且 $np$ 取适中值时，泊松 PMF 可以很好地逼近二项 PMF。更精确地说，令 $\lambda = np$，则对 $k = 0, 1, \ldots, n$，当 $n$ 很大且 $p$ 很小时，有

```math
\binom{n}{k} p^k (1-p)^{n-k} \approx \frac{e^{-\lambda}\lambda^k}{k!}
```

这种近似可能得出更简单的计算。例如，设 $n = 100$ 次试验、$p = 0.01$。则 $np = \lambda = 1$，$k = 5$ 次成功的概率（用二项 PMF 表示）为

```math
\binom{100}{5} (0.01)^5 (1 - 0.01)^{95} = 0.00290.
```

而用 $\lambda = np = 1$ 的泊松 PMF 近似，该概率为

```math
\frac{e^{-1}}{5!} = 0.00306.
```

两者非常接近。我们将在章末习题中给出这种近似的正式证明，并在第 6 章中进一步使用它。泊松回顾用例：历史上曾用泊松 PMF 拟合波兰骑兵在数年时间内被马踢致死事故（horse kick accidents）的数目。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 泊松之所以无处不在，全靠"稀有事件定律"（law of rare events）：当试验次数 $n\to\infty$、成功概率 $p\to0$、而乘积 $np\to\lambda$ 保持适中时，二项 PMF 必收敛到泊松 PMF（正式的极限论证放在章末习题）。直观上，泊松刻画"某种几乎必然不发生的事件，在单位尺度里平均发生 $\lambda$ 次"的情形，$\lambda$ 既是均值也是方差，是全部分布唯一的参数。它的最佳应用载体是泊松过程与排队论（电话呼叫流、放射性衰变），在算法课上则出现在散列（hashing）的碰撞分析——生日问题与哈希表冲突，都可近似为泊松计数。注意泊松在此有"三重身份"：既是二项在极端情形下的极限近似，又是与二项独立并存的原生分布，还是"到下一次事件所需等待时间"（即指数分布）所依托的计数过程。借助 $e^{-\lambda}\lambda^k/k!$ 把 $\binom{n}{k}p^k(1-p)^{n-k}$ 换掉，常能把难以据算的阶乘和变成手可心算的四则运算，正如 $n=100,p=0.01$ 那例所示。

## <span style="color:#c0392b;">2.3　随机变量的函数（Functions of Random Variables）</span>

给定随机变量 $X$，可以通过对 $X$ 施加各种变换来生成其他随机变量。作为例子，设随机变量 $X$ 是今天以摄氏度（degrees Celsius）计的室温，考虑变换 $Y = 1.8X + 32$，它给出以华氏度（degrees Fahrenheit）计的温度。在这个例子中，$Y$ 是 $X$ 的线性函数，形如

```math
Y = g(X) = aX + b,
```

其中 $a$ 和 $b$ 是标量。我们也可以考虑 $X$ 的一般形式的非线性函数

```math
Y = g(X).
```

例如，如果我们希望在对数刻度上显示温度，我们会使用函数 $g(X) = \log X$。

<span style="color:#00838f;">**[definition] 随机变量的函数（`function of a random variable`）**</span>

> 若 $Y = g(X)$ 是随机变量 $X$ 的函数，则由于它为每个可能结果提供一个数值，$Y$ 也是一个随机变量。这是因为样本空间中的每个结果都为 $X$ 定义了一个数值，从而也就为 $Y$ 定义了数值 $y = g(x)$。若 $X$ 是离散的且 PMF 为 $p_X$，则 $Y$ 也是离散的，并且它的 PMF 可以用 $X$ 的 PMF 来计算。特别是，为求 $p_Y(y)$，对任意 $y$，我们把所有满足 $g(x) = y$ 的 $x$ 值的概率相加：

```math
p_Y(y) = \sum_{\{x \mid g(x) = y\}} p_X(x).
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 随机变量函数 $Y=g(X)$ 的本质，是把"数轴上的概率分配"沿 $g$ 重新打包：$p_Y(y)$ 把能落到 $y$ 的所有 $x$（即 $g$ 的原像集 $g^{-1}(y)$）的 $p_X$ 值加总。这正是测度论里"前向推移测度 / 分布推移（pushforward measure / pushforward of a distribution）"在离散情形的化身——你将来在实分析里会以不同符号见到同一件事。它的最大实用价值在于：处理 $g(X)$ 的任一性质，不必像例题那样先完整求出 $g(X)$ 的分布，只要能"在原分布上对着 $g$ 值加权"即可（下一节期望值法则就是同一思路的果实）。务必留意"多对一"的情形：$Y=|X|$ 与 $Z=X^2$ 中多个 $x$ 会撞向同一个 $y$，这些合并点正是求和最容易漏项、错项的所在，例 2.1 的所有计算都在示范如何把它们数对。

## <span style="color:#2471a3;">[example] 例（Example）2.1</span>
设 $Y = |X|$，并设

```math
p_X(x) = \begin{cases} 1/9, & \text{若 } x \text{ 是区间 } [-4, 4] \text{ 中的整数}, \\ 0, & \text{其他情况,} \end{cases}
```

参见图 2.6 的说明。$Y$ 的可能取值为 $y = 0, 1, 2, 3, 4$。要对这个范围内给定的某个 $y$ 计算 $p_Y(y)$，我们对所有满足 $|x| = y$ 的 $x$ 值将 $p_X(x)$ 相加。特别地，与 $y = 0$ 对应的 $X$ 值只有一个，即 $x = 0$。于是

```math
p_Y(0) = p_X(0) = \frac{1}{9}.
```

另外，与 $y = 1, 2, 3, 4$ 中每一个都对应的 $X$ 值各有两个，所以例如

```math
p_Y(1) = p_X(-1) + p_X(1) = \frac{2}{9}.
```

因此，$Y$ 的 PMF 为

```math
p_Y(y) = \begin{cases} 2/9, & \text{若 } y = 1, 2, 3, 4, \\ 1/9, & \text{若 } y = 0, \\ 0, & \text{其他情况。} \end{cases}
```

（本批末尾截断，续于下批。）
<!-- ===== batch02_D ===== -->
> <span style="color:#7f8c8d;">BT（`Bertsekas & Tsitsiklis`）§2.4 期望、均值与方差（`Expectation, Mean, and Variance`），p.91–100</span>

## <span style="color:#c0392b;">2.4　期望、均值与方差（`Expectation, Mean, and Variance`）</span>

（本批开头接续上批，处于例 2.1 的讨论中——关于 $Y=|X|$。图 2.6（`Fig. 2.6`）给出 $X$ 与 $Y=|X|$ 的概率质量函数（`PMF`）。）

> <span style="color:#7f8c8d;">**（开头接续上批）** [figure] 图 2.6：例 2.1 中 $X$ 与 $Y=|X|$ 的概率质量函数。

**例 2.1 续。** 再看一个相关的例子。令 $Z$ 等于 $X$ 的平方（`square`），即 $Z=X^2$。为求出 $Z$ 的 PMF，我们整理使 $X^2=z$ 的所有 $x$，利用公式

```math
p_Z(z)=P(Z=z)=P(X^2=z)=\sum_{\{x\mid x^2=z\}}p_X(x)=\sum_{\{x\mid x^2=z\}}p_Y(y),
```

即得到

```math
p_Z(z)=\begin{cases} 2/9, & \text{若 } z=1,\,4,\,9,\,16,\\
1/9, & \text{若 } z=0,\\
0, & \text{其他情形}.\end{cases}
```

随机变量（`random variable`）的函数这一含混而宽泛的概念（`vague notion`），为我们提供了几个有用的工具。最重要的问题是寻找所有可能取值（`possible values`，按概率成比例）的**加权平均**（`average`）。设 $m_1,m_2,\ldots,m_n$ 是 $X$ 的若干可能取值，分别对应概率 $p_1,p_2,\ldots,p_n$。所谓"平均值"到底指什么，以及它为什么有用？

**动机（`motivation`）。** 假设你转动一个转盘，它可能停在某些数字 $m_1,m_2,\ldots,m_n$ 上；并假设结果 $m_j$ 以概率 $p_j$ 出现。若转动的次数 $k$ 很大，则出现每个 $m_i$ 的次数 $k_i$ 占总数 $k$ 的比例大致等于 $p_i$：$k_i/k\approx p_i$（$i=1,\ldots,n$）。这样，你每转一次"期望"（`expect`）获得的金额大致为 $m_1p_1+\cdots+m_np_n$。受这个例子启发，我们引入下面的定义。

<span style="color:#00838f;">**[definition] 期望 / 均值（`expectation` / `expected value` / `mean`）**</span>

> 我们定义随机变量 $X$ 的期望值（`expected value`），也称期望（`expectation`）或均值（`mean`），其 PMF 为 $p_X$，即

```math
E[X]=\sum_x x\,p_X(x).
```

> <span style="color:#7f8c8d;">**[note]** 当处理的随机变量取可数无穷多个值时，必须处理无限求和 $\sum_x x\,p_X(x)$ 或许无定义的可能性。具体地说，当 $\sum_x |x|\,p_X(x)<\infty$ 时，我们说期望是有良定义的（`well-defined`）。此时已知无限求和 $\sum_x x\,p_X(x)$ 收敛到某个有限值，且该值与各项求和的先后顺序无关。关于期望无定义的例子，考虑取值为 $2^k$、概率为 $2^{-k}$（$k=1,2,\ldots$）的随机变量 $X$。一个更微妙的例子：考虑取值为 $2^k$ 与 $-2^k$、概率为 $2^{-k}$（$k=1,2,\ldots$）的随机变量 $X$。此时即便 PMF 关于零对称，人们可能会忍不住说 $E[X]=0$，但期望仍然是未定义的。全书在不作相反说明的情况下，默认所关心的随机变量的期望是有良定义的。

## <span style="color:#2471a3;">[example] 例 2.2</span>
考虑两次独立的抛硬币试验，每次正面（`head`）出现的概率为 $3/4$，令 $X$ 为得到的正面次数。这是参数 $n=2,\ p=3/4$ 的二项随机变量（`binomial random variable`）。其 PMF 为

```math
p_X(k)=\begin{cases} (1/4)^2, & \text{若 } k=0,\\
2\cdot(1/4)\cdot(3/4), & \text{若 } k=1,\\
(3/4)^2, & \text{若 } k=2,\end{cases}
```

故均值为

```math
E[X]=0\cdot\left(\frac14\right)^2+1\cdot\left(2\cdot\frac14\cdot\frac34\right)+2\cdot\left(\frac34\right)^2=\frac{24}{16}=\frac32.
```

把 $X$ 的均值视为 $X$ 的某个"代表值"（`representative value`）是很有用的，其意义可用图 2.7（`Fig. 2.7`）解释。直观上，把均值视为 PMF 的"质心"（`center of gravity`）：在每点 $x$ 放置权重 $p_X>0$，则质心就是使左侧所有力矩之和等于右侧所有力矩之和的点，即 $\sum_x(x-c)p_X(x)=0$ 的解；这个质点系的重心就等于均值 $E[X]$。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 期望 $E[X]=\sum_x x\,p_X(x)$ 值得逐项拆解：它按概率 $p_X(x)$ 为权重、对全部可能取值 $x$ 加权平均，$\sum$ 里每一项都是"数值乘权重"，所以它就是概率版的质心。把每个取值 $x$ 想成数轴上质量为 $p_X(x)$ 的一枚砝码，$E[X]$ 就是整排砝码的平衡点——正负力矩互相抵消，$\sum_x(x-c)p_X(x)=0$ 正是"力矩平衡"的代数写法。由此你也明白为何期望对加法与数乘"线性"：求和这种运算天然把常数因子和常数项分派进每一项，后文把 $E[X]$ 在方差里搬进又搬出全靠这条性质。至于良定义，前面灰色脚注已经强调需要 $\sum_x|x|p_X(x)<\infty$——这正是实分析里"$\ell^1$ 函数"的可积条件，保证无限级数不因重排而变（对应黎曼级数重排定理的反例）。一句话，期望是"一阶矩"，整个矩方法（moment method）的第一级台阶，二阶中心矩方差马上就位。

除均值外，还有几个与其 PMF 相关联的重要量。其中，$E[X^n]$（$n$ 阶矩，`nth moment`）常常很有用；按惯例，一阶矩（`first moment`）即均值。与之相关的最重要量是方差（`variance`），记为 $\operatorname{var}(X)$，定义为随机变量 $(X-E[X])^2$ 的期望值。因为 $(X-E[X])^2$ 只能取非负值，所以方差永远是非负的，并刻画 $X$ 围绕其均值的散布程度。方差的正平方根称为 $X$ 的标准差（`standard deviation`），记为 $\sigma_X$：

```math
\sigma_X\;\hat{=}\;\sqrt{\operatorname{var}(X)}.
```

标准差往往更容易解读，因为它与 $X$ 具有相同的单位。例如，若 $X$ 以米为单位度量长度，则方差的单位是平方米，而标准差的单位是米。

计算 $\operatorname{var}(X)$ 的一种方法，是先求出随机变量 $(X-E[X])^2$ 的 PMF，再用期望的定义来计算；后者是 $X$ 的函数，其 PMF 可按上一小节讨论的方式求得。

## <span style="color:#2471a3;">[example] 例 2.3</span>
考虑例 2.1 的随机变量 $X$，其 PMF 为

```math
p_X(x)=\begin{cases} 1/9, & \text{若 } x \text{ 是区间 } [-4,4] \text{ 中的整数},\\
0, & \text{其他情形}.\end{cases}
```

由 $X$ 的 PMF 关于 0 的对称性可知，均值 $E[X]$ 等于 0，也可由定义验证：

```math
E[X]=\sum_x x\,p_X(x)=\frac19\sum_{x=-4}^{4}x=0.
```

令 $Z=(X-E[X])^2=X^2$。如同例 2.1，我们有

```math
p_Z(z)=\begin{cases} 2/9, & \text{若 } z=1,\,4,\,9,\,16,\\
1/9, & \text{若 } z=0,\\
0, & \text{其他情形}.\end{cases}
```

于是 $X$ 的方差为

```math
\operatorname{var}(X)=E[Z]=\sum_z z\,p_Z(z)=0\cdot\frac19+1\cdot\frac29+4\cdot\frac29+9\cdot\frac29+16\cdot\frac29=\frac{60}{9}.
```

事实证明，计算 $\operatorname{var}(X)$ 还有一个更简便的方法，它只用 $X$ 的 PMF，而无需求出 $(X-E[X])^2$ 的 PMF。这个方法基于下面的法则。

<span style="color:#00838f;">**[definition] 随机变量函数的期望值法则（`Expected Value Rule for Functions of Random Variables`）**</span>

> 设 $X$ 是 PMF 为 $p_X$ 的随机变量，设 $g(X)$ 是 $X$ 的一个函数。则随机变量 $g(X)$ 的期望值为

```math
E[g(X)]=\sum_x g(x)\,p_X(x).
```

**验证该法则。** 令 $Y=g(X)$，利用上一小节导出的公式 $p_Y(y)=\sum_{\{x\mid g(x)=y\}}p_X(x)$，我们有

```math
E[g(X)]=E[Y]=\sum_y y\,p_Y(y)
=\sum_y y\sum_{\{x\mid g(x)=y\}}p_X(x)
=\sum_y\sum_{\{x\mid g(x)=y\}}y\,p_X(x)
=\sum_y\sum_{\{x\mid g(x)=y\}}g(x)\,p_X(x)
=\sum_x g(x)\,p_X(x).
```

利用期望值法则，可以把方差写成

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 期望值法则 $E[g(X)]=\sum_x g(x)\,p_X(x)$ 在概率论里俗称"无意识统计学家法则"（LOTUS，Law of the Unconscious Statistician）。它的威力在于：要算 $g(X)$ 的期望，完全不必先求出 $g(X)$ 自身的分布，只需在 $X$ 原分布上一一把 $x$ 换成 $g(x)$ 再按 $p_X(x)$ 加权。直觉上完全自洽——$g(X)$ 取到某个值的概率本已由"多少 $x$ 的像落到那里"决定，于是把每个 $x$ 的 $p_X(x)$ 分配给 $g(x)$ 即可；教材的验证本质上就是在两级求和之间对换求和顺序 $(\sum_y\sum_{\{x:g(x)=y\}}=\sum_x)$。这同时解释了为什么期望像普通求和一样对常数项、数乘都"线性"，因为它就是对样本空间的概率加权求和。顺着这条思路，下一章"随机变量和的期望"就是把线性性与本法则结合，成批处理一堆随机变量之和的期望。

```math
\operatorname{var}(X)=E[(X-E[X])^2]=\sum_x (x-E[X])^2\,p_X(x),
```

无需计算 $(X-E[X])^2$ 的 PMF。类似地，第 $n$ 阶矩为 $E[X^n]=\sum_x x^n p_X(x)$。

## <span style="color:#2471a3;">[example] 例 2.3（续）</span>
对于 PMF 为 $p_X(x)=1/9$（$x\in\{-4,\ldots,4\}$）、其余为 0 的随机变量 $X$，我们有

```math
\operatorname{var}(X)=E[(X-E[X])^2]=\sum_x (x-E[X])^2\,p_X(x)
=\frac19\bigl(16+9+4+1+0+1+4+9+16\bigr)=\frac{60}{9},
```

（因为 $E[X]=0$），这与先前得到的结果一致。

如前所述，方差总是非负的，但它可能等于零吗？由于方差公式里的每一项 $(x-E[X])^2p_X(x)$ 都非负，求和为零当且仅当每一项都是零，即对每个满足 $p_X(x)>0$ 的 $x$，均有 $x=E[X]$。这一条件意味着随机变量其实并不"随机"（`not really random`）：它以概率 1 等于其均值。

<span style="color:#00838f;">**[definition] 方差（`Variance`）**</span>

> 随机变量 $X$ 的方差 $\operatorname{var}(X)$ 定义为

```math
\operatorname{var}(X)=E[(X-E[X])^2],
```

并可计算为 $\sum_x (x-E[X])^2\,p_X(x)$。它总是非负的。其平方根记为 $\sigma_X$，称为标准差。

## <span style="color:#c0392b;">均值与方差的性质（`Properties of Mean and Variance`）</span>

现在我们用期望值法则来推导均值和方差的一些重要性质。从一个随机变量 $X$ 出发，定义形如 $Y=aX+b$ 的新随机变量 $Y$，其中 $a$、$b$ 是给定的标量（`scalar`）。下面推导线性函数 $Y$ 的均值与方差。我们有

```math
E[Y]=\sum_x(ax+b)p_X(x)=a\sum_x x\,p_X(x)+b\sum_x p_X(x)=aE[X]+b.
```

此外，

```math
\operatorname{var}(Y)=\sum_x\bigl(ax+b-E[aX+b]\bigr)^2p_X(x)
=\sum_x\bigl(ax+b-aE[X]-b\bigr)^2p_X(x)
=a^2\sum_x(x-E[X])^2p_X(x)
=a^2\operatorname{var}(X).
```

## <span style="color:#2471a3;">[property] 随机变量线性函数的均值与方差（`Mean and Variance of a Linear Function of a Random Variable`）</span>
设 $X$ 是一个随机变量，令 $Y=aX+b$，其中 $a$、$b$ 是给定标量。则

```math
E[Y]=aE[X]+b,\qquad \operatorname{var}(Y)=a^2\operatorname{var}(X).
```

下面再给出方差的一个方便的等价公式。

## <span style="color:#2471a3;">[property] 用矩表达式表示的方差（`Variance in Terms of Moments Expression`）</span>
```math
\operatorname{var}(X)=E[X^2]-(E[X])^2.
```

该表达式验证如下：

```math
\begin{aligned}
\operatorname{var}(X)&=\sum_x(x-E[X])^2p_X(x)\\
&=\sum_x\bigl(x^2-2xE[X]+(E[X])^2\bigr)p_X(x)\\
&=E[X^2]-2(E[X])^2+(E[X])^2\\
&=E[X^2]-(E[X])^2.
\end{aligned}
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 方差为什么偏偏用平方，而不是用 $|X-E[X]|$？原因有三：平方让正负偏离各自变为非负、从而不会相互抵消；平方激励放飞（outlier）——离均值越远的取值贡献越大，正好度量"散布"多"激进"；而且 $\operatorname{var}$ 开根号给出与 $X$ 同单位的标准差，量纲、直觉都顺。两条关键公式$\operatorname{var}(X)=E[X^2]-(E[X])^2$ 与 $\operatorname{var}(aX+b)=a^2\operatorname{var}(X)$ 的来历很干净：前者只是把 $E[X]$ 当普通常数展开二次型 $(x-E[X])^2$ 再逐项取期望，后者则靠期望线性——平移 $+b$ 在平方里对消，缩放 $a$ 被平方提出为 $a^2$。若把期望看作样本空间上的线性运算，那么方差就是对随机变量"二次型/二阶中心矩"，这与你在线性代数（Strang《Introduction to Linear Algebra》的线性变换章）里见过的"线性映射平移不变、缩放改尺度"完全同构。这条平方结构还是后面 Chebyshev 不等式与"偏离均值超过 $k$ 个标准差"射程论题的命脉，务必在第二章就把它吃透。

最后，我们用例子说明一个常见的陷阱：除非 $g(X)$ 是线性函数，否则一般不成立 $E[g(X)]=g(E[X])$。

## <span style="color:#2471a3;">[example] 例 2.4　平均速度与平均时间（`Average Speed Versus Average Time`）</span>
如果天气良好（其发生概率为 0.6），爱丽丝（`Alice`）以每小时 $V=5$ 英里的速度步行 2 英里到教室；否则她以每小时 $V=30$ 英里的速度骑摩托车。到达教室所需时间 $T$ 的均值是多少？

正确的做法是先求出 $T$ 的 PMF：

```math
p_T(t)=\begin{cases} 0.6, & \text{若 } t=2/5 \text{ 小时},\\
0.4, & \text{若 } t=2/30 \text{ 小时}.\end{cases}
```

再计算其均值：

```math
E[T]=0.6\cdot\frac25+0.4\cdot\frac{2}{30}=\frac{4}{15}\ \text{小时}.
```

然而，先算速度 $V$ 的均值 $E[V]=0.6\cdot5+0.4\cdot30=15$（英里每小时），再断言时间 $T$ 的均值为 $2/E[V]=2/15$ 小时，是错误的。总之，本例中 $T=2/V$，所以

```math
E[T]\neq \frac{2}{E[V]}.
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 陷阱题的核心是：$E[g(X)]=g(E[X])$ 只在 $g$ 为线性时才成立，因为线性运算可以穿过加权平均而保持结构，非线性则不行。本例 $T=2/V$ 是倒数变换，$E[1/V]\ne1/E[V]$ 正是算术平均与调和平均不相等的体现。其背后的精确不等式是 Jensen：当 $g$ 为凸函数（二阶导 $\ge0$，如 $1/v$ 在 $v>0$）时 $g(E[X])\le E[g(X)]$，凹函数则反向——所以教材断言 $E[2/V]\ge 2/E[V]$，方向与凸性吻合。判断"能否把函数投机取巧搬进期望"，只需看 $g$ 是否线性；若否，则按凸凹性给出一边界的单向估计。这条"函数与期望不可随便互换"的直觉，往后会在 Chebyshev 不等式、$E[X^2]$ 与 $(E[X])^2$ 的比较、以及各种期望不等式的证明里反复现身。

## <span style="color:#c0392b;">一些常见随机变量的均值与方差（`Mean and Variance of Some Common Random Variables`）</span>

下面推导几个重要随机变量均值与方差的公式。全书会在多种情境下反复使用这些公式。

## <span style="color:#2471a3;">[example] 例 2.5　伯努利随机变量的均值与方差</span>
考虑抛硬币试验：正面（`head`）概率为 $p$，反面（`tail`）概率为 $1-p$。令伯努利随机变量（`Bernoulli random variable`）$X$ 的 PMF 为

```math
p_X(k)=\begin{cases} p, & \text{若 } k=1,\\
1-p, & \text{若 } k=0.\end{cases}
```

$X$ 的均值、二阶矩与方差由下列计算给出：

```math
E[X]=1\cdot p+0\cdot(1-p)=p,
```
```math
E[X^2]=1^2\cdot p+0\cdot(1-p)=p,
```
```math
\operatorname{var}(X)=E[X^2]-(E[X])^2=p-p^2=p(1-p).
```

## <span style="color:#2471a3;">[example] 例 2.6　离散均匀随机变量（`Discrete Uniform Random Variable`）</span>
掷一个均匀六面骰子一次，与之相关的均值与方差是多少？若把掷骰的结果视为随机变量 $X$，其 PMF 为

```math
p_X(k)=\begin{cases} 1/6, & \text{若 } k=1,\,2,\,3,\,4,\,5,\,6,\\
0, & \text{其他情形}.\end{cases}
```

由于 PMF 关于 3.5 对称，我们推断 $E[X]=3.5$。至于方差，我们有

```math
\operatorname{var}(X)=E[X^2]-(E[X])^2=\frac16(1^2+2^2+3^2+4^2+5^2+6^2)-(3.5)^2,
```

其结果为 $\operatorname{var}(X)=35/12$。

更一般地，设想一个均匀地（`uniformly`）取值于某段连续整数 $\{a,a+1,\ldots,b\}$ 之一的随机变量，其中 $a\lt b$ 是两个整数；其 PMF（见图 2.8（`Fig. 2.8`），即均匀分布于 $a$ 与 $b$ 之间整数的离散随机变量的 PMF）为

```math
p_X(k)=\begin{cases}\displaystyle\frac{1}{b-a+1}, & \text{若 } k=a,\,a+1,\ldots,b,\\
0, & \text{其他情形}.\end{cases}
```

均值是

```math
E[X]=\frac{a+b}{2},
```

由对称性一望即知。为计算 $X$ 的方差，先考虑较简单的 $a=1,\ b=n$ 的情况。可以证明

```math
\sum_{k=1}^{n}k=\frac{n(n+1)}{2},
```
并由此推得 $\displaystyle E[X]=\frac{n+1}{2}$。利用平方和公式计算二阶矩，可得方差。可将该结果迁移到一般的 $a,b$：均匀分布于 $[a,b]$ 的随机变量，与均匀分布于 $[1,b-a+1]$ 的随机变量具有相同的方差，因为后者的 PMF 正是前者的平移。因此，令 $n=b-a+1$，所求方差为

```math
\operatorname{var}(X)=\frac{(b-a+1)^2-1}{12}=\frac{(b-a)(b-a+2)}{12}.
```

> <span style="color:#7f8c8d;">**[note]** 原文此处（p.99）PDF-OCR 中 $E[X^2]$ 的平方和公式细节残缺，已按标准结果 $E[X^2]=\frac{1}{6}(n+1)(2n+1)$ 与 $\operatorname{var}(X)=(n^2-1)/12$ 予以还原；得到的 $a=1,b=6$ 时即 $35/12$，与例 2.6 一致——待读者核对原书公式。本译文不承担更正职责，仅保证数值自洽。

## <span style="color:#2471a3;">[example] 例 2.7　泊松分布的均值（`The Mean of the Poisson`）</span>
泊松概率质量函数的均值：

```math
p_X(k)=e^{-\lambda}\frac{\lambda^k}{k!},\qquad k=0,1,2,\ldots,
```

可以如下计算：

```math
\begin{aligned}
E[X]&=\sum_{k=0}^{\infty}k\,e^{-\lambda}\frac{\lambda^k}{k!}
=\sum_{k=1}^{\infty}k\,e^{-\lambda}\frac{\lambda^k}{k!}
=\lambda\sum_{k=1}^{\infty}e^{-\lambda}\frac{\lambda^{k-1}}{(k-1)!}
=\lambda\sum_{m=0}^{\infty}e^{-\lambda}\frac{\lambda^m}{m!}
=\lambda.
\end{aligned}
```

（其中 $k=0$ 项为零；并令 $m=k-1$。）最后一个等号成立，是因为 $\sum_m e^{-\lambda}\lambda^m/m!=1$ 正好是泊松 PMF 的归一化性质（`normalization property`）。类似的推演表明，泊松随机变量的方差也等于 $\lambda$（参见 2.7 节例 2.20）。后面几章我们还会用多种不同的方法推导这一事实。

---

## <span style="color:#c0392b;">用期望值做决策（`Decision Making Using Expected Values`）</span>

期望值常常为在若干可能导致随机奖励（`random reward`）的候选决策方案之间做最优化选择，提供了方便的工具。若把某个决策的期望奖励视为其"大量试验下的平均回报"，那么选择期望奖励最大的决策就是合理的。下面是这样一个例子。

（本批末尾截断，续于下批）