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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> counting principle（计数基本法则）要回答的不是"怎样把东西数完"，而是"什么样的数法可以合法地把各阶段的分支数直接相乘"。
>
> 先看两阶段。设第一阶段有 $m$ 种结果，第二阶段对每一种第一阶段结果都有 $n$ 种结果。把全部结果排成一张表：每一行对应第一阶段的一个结果，行内 $n$ 个格子对应第二阶段的选择。每个 ordered pair（有序对）恰好占一个格子，表格没有空位也没有重复，所以总数是 $m\times n$。这个"表格没有空位"才是乘法的真正理由——它同时用到两条性质：每行都一样长，且行与行不重叠。
>
> 推广到 $r$ 个阶段只是把同一论证重复使用。令 $N_i$ 表示前 $i$ 个阶段共有多少种结果。第 $i$ 阶段对每一个前缀结果都提供 $n_i$ 种选择，于是每个前缀长出 $n_i$ 个新叶子，$N_i=N_{i-1}\cdot n_i$。把递推式一路展开，得 $N_r=n_1n_2\cdots n_r$。教材 Fig. 1.17 画的就是这棵树：叶子数等于每层分支数的连乘。
>
> 这里有个条件绝不能省：第 $i$ 阶段的分支数必须对每一个前缀结果都相同。教材的措辞是"对任意前 $i-1$ 个阶段所形成的每一种结果，第 $i$ 阶段都有 $n_i$ 种可能结果"。如果某些前缀长出 3 个分支、另一些只长出 1 个，树就变成不规整的，叶子数只能靠加法：把各棵子树的叶子数相加。举例：第一阶段从 $\{A,B\}$ 里选；若选了 $A$，第二阶段有 3 种；若选了 $B$，第二阶段只有 1 种。总数是 $3+1=4$，不是 2 乘任何东西。所以乘法与加法不是两个并列公式，而是同一棵树在"规整"与"不规整"两种情形下的两种数法。
>
> 再追一层，会发现条件比"与前面的具体选择无关"更宽松：只要每种前缀的分支数相同，哪怕这个数依赖前面选了什么，仍然能乘。设三位密码：第一位取 1 到 9，共 9 种；第二位必须与第一位不同，无论第一位是什么都恰好剩 9 种；第三位必须与前两位都不同，无论前两位是什么都恰好剩 8 种。三个阶段的分支数都依赖历史，但每个前缀下的分支数一致，于是总数仍是 $9\times9\times8=648$。这处容易被误读成"每次选择必须完全独立"，其实只需"同一层的分支数处处相等"。
>
> 回到教材的两个例子。Example 1.26 的 7 位电话号码：第一位不能是 0 或 1，8 种；其余六位各 10 种；总数 $8\cdot10^6=8000000$。若取消第一位的限制，变成 $10^7=10000000$，两者差 200 万个号码——这个差额正是第一位少掉的 2 种被后面六位的 $10^6$ 放大出来的。Example 1.27 的子集数：$n$ 个元素逐个决定收或不收，每个元素 2 种，共 $2^n$。取 $n=20$ 得 $1048576$ 个子集，所以穷举子集的算法在 $n=20$ 时还能跑，$n=40$ 时已是 $10^{12}$ 量级。
>
> 跨课程看，这条法则在两处反复出现。6.042J 的教材《Mathematics for Computer Science》（作者 Lehman、Leighton、Meyer）的 Counting 一章把它命名为 product rule（乘法法则），并要求每一步的选择数不依赖之前的选择，与本节的措辞一致，区别是那边更强调用 bijection（双射）把陌生集合搬到熟悉集合再数。CSAPP 第 6 章讲 cache 容量时，容量等于组数乘每组的块数再乘块大小：设组索引 6 位、每块 16 字节、8 路组相联，容量是 $2^6\times8\times16=8192$ 字节，即 8 KiB。三个维度互相正交，换了组再选路、再选块内偏移互不影响，所以能连乘；一旦某个维度不再彼此独立，连乘立刻失效。
>
> 一句话收束：排列数、组合数、子集数都不是新公式，而是同一棵计数树在不同"每层分支数"设定下的叶子数；做题时先切出阶段，再检查每层分支数是否处处相等，乘法才允许落下。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这里的核心不是"随机"，而是"函数"：random variable（随机变量）就是从 sample space（样本空间）到实数的映射 $X:\Omega\to\mathbb R$，它的全部作用是把"结果的概率"翻译成"数轴上的概率"。
>
> 先问为什么非要这一步。概率公理只谈论事件，也就是样本空间的子集；可我们想说"平均温度""误差有多大""几次成功"，这些词都是对数字说的，不是对结果说的。要让"平均"有意义，前提是每个结果先被赋予一个数，否则连加法都无从谈起。随机变量就是这台贴牌机：它把抽象的 outcomes（结果）逐个贴上实数标签，此后所有算术都在这批标签上做。
>
> 有个极易含混的地方：$P(X=x)$ 里的 $X=x$ 不是"把一个数拿去问概率"，而是简写。完整写法是 $P(\{\omega\in\Omega: X(\omega)=x\})$，即取 $x$ 在映射 $X$ 下的原像，得到样本空间的一个子集，再对这个子集求概率。想清这一点，"随机变量"里的"随机"就不神秘了：随机性全部来自 $\Omega$ 上的概率律，$X$ 本身是确定性的函数，给定 $\omega$ 就给定 $X(\omega)$，没有任何随机成分。
>
> 同一个样本空间上可以挂任意多个随机变量，它们只是不同的观察角度。掷两颗四面骰子有 16 个等可能结果；$X$ 取两颗的和，$Y$ 取两颗的较大值，$Z$ 取"是否出现 4"。三个函数共用一套概率，却给出三条完全不同的 distribution（分布）。这说明随机变量不是样本空间自带的属性，而是研究者加装的一层刻度。
>
> 用教材图 2.2 的设定算一遍：$X$ 是两颗公平四面骰子的最大点数。$p_X(1)$ 只有 $(1,1)$ 一个结果，得 $1/16$；$p_X(2)$ 是 $(1,2),(2,1),(2,2)$ 三个，得 $3/16$；$p_X(3)$ 是 $(1,3),(2,3),(3,1),(3,2),(3,3)$ 五个，得 $5/16$；$p_X(4)$ 是其余七个，得 $7/16$。四个数相加 $16/16=1$，核对通过。奇数序列 $1,3,5,7$ 不是巧合：最大点数不超过 $k$ 的结果有 $k^2$ 个，于是 $P(X\le k)=k^2/16$，相邻两项相减即得 $p_X(k)=(2k-1)/16$。
>
> discrete（离散）的判据落在值域上：值域有限，或可数无限，也就是能与正整数一一对应地排成一列。在 $[-1,1]$ 上取一点 $a$，$a^2$ 能取到整个区间，不可数，所以不是离散的；$\text{sgn}(a)$ 只取 $-1,0,1$，永远离散。判据只问"能取多少种值"，不问"取值有多密集"：$\text{sgn}$ 的跳变很大，$a^2$ 连续铺满，差别不在密集程度，而在能否排成一列。
>
> 跨课程对照 Strang 的线性代数：线性映射 $T:\mathbb R^n\to\mathbb R$ 也是"把结构送成数"，但它要求 $T(u+v)=T(u)+T(v)$，随机变量完全没有这个要求，$\text{sgn}$ 就不是线性的。真正的区别在于随机变量额外背着一层"原像的概率权重"：线性映射只关心像，随机变量必须能回答"像落进这个集合的概率是多少"。这也解释了后面为什么可以直接在原分布上给 $g(x)$ 加权而不必先求 $g(X)$ 的分布——权重本来就在原像那一侧。
>
> 更高级的讲法要求每个 $\{X\le x\}$ 都是可测集，那是实分析的语言，本课用不到：你只需知道每个 $\{X=x\}$ 都能算出概率，这就够了。一句话收束：随机变量是函数，概率挂在它的原像上；后面的 probability mass function（概率质量函数）、expectation（期望）、variance（方差）、conditional distribution（条件分布），全都是在这层刻度上作业。
>
> 顺便回答"为什么值必须落在实数上"。因为后面要用的每个概念都是数的运算：比较大小（$P(X\le x)$）、求距离（$|X-E[X]|$）、variance（方差）的定义、expectation（期望）的求和。只要映射的终点是实数，这些操作才有定义；若映射到一般集合，就只能谈"等于哪一类"，谈不了"偏离多少"。实数这条终点线不是随便选的。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条注要拆的是一个常被当作定义抄下来的等式：$\sum_x p_X(x)=1$ 不是定义的一部分，而是从 probability axiom（概率公理）推出来的定理。
>
> 推导只要四步，每一步都有它的位置。第一，事件 $\{X=x\}$ 两两不交：若 $x\ne y$，一个 outcome 不可能同时让 $X(\omega)=x$ 与 $X(\omega)=y$，否则就违反"函数单值"这一条。第二，把这些事件的并取遍值域，得到整个 $\Omega$：每个 $\omega$ 都有 $X(\omega)$ 这个值，于是它一定落在自己那一格里。第三，countable additivity（可数可加性）允许把互斥事件的概率直接相加。第四，归一化公理给出 $P(\Omega)=1$。四步合起来，就是那条求和式。
>
> 反过来问：如果不归一化会怎样。设 $\sum_x p_X(x)=0.9$，则 $P(X\in S)+P(X\notin S)$ 等于 0.9 而不是 1，互补律失效，没发生的那部分凭空多出 0.1 的概率无处安放；若和是 1.2，某些事件就能拿到大于 1 的概率，而"概率不超过 1"是任何模型的地板。所以归一化不是审美选择，它是让互补律与有界性同时成立的唯一取值。
>
> 能逐点求和，靠的是离散这条假设：$x$ 只遍历值域，而离散随机变量的值域可数。可数才谈得上排成一列、谈得上可数可加；不可数时逐点求和没有定义，必须换一套工具，那是第 3 章连续随机变量的事。这里能看到离散假设的真正用途：它不是"取值少"，而是"能排成一列"，于是概率可以被逐点清点。
>
> 算两个能当场核对的例子。两次公平硬币，$X$ 为正面数：$p_X(0)=1/4$，$p_X(1)=1/2$，$p_X(2)=1/4$，和为 1；$P(X>0)=1/2+1/4=3/4$，而 $P(X=0)=1/4$，互补成 1。二项 $n=3,p=1/2$：四个概率是 $1/8,3/8,3/8,1/8$，和为 1；$P(X\ge2)=3/8+1/8=1/2$。做题时先做这道体检：任何一条 PMF 只要和不是 1，后面的期望与方差全都跟着错，而且错得隐蔽，往往到量级对不上时才回头找。
>
> 把 PMF 想成撒沙子最省事：总质量 1 千克的沙子撒在数轴上，$p_X(x)$ 是落在点 $x$ 上那一小堆的质量。求 $P(X\in S)$ 就是拿勺子把 $S$ 范围内的沙子全部舀起来称重，求和号就是"把所有小堆逐一称完再加起来"。这也解释了 probability mass（概率质量）这个名字：它不是密度，而是每一小堆自身的重量。等到学连续随机变量时，同样的沙子改成连续铺开，逐堆称重变成积分，$f_X(x)$ 变成每单位长度的质量，这正是 probability density（概率密度）这个名称的来历。
>
> 跨课程接一处：CSAPP 第 6 章 cache 的 hit rate（命中率）与 miss rate（缺失率）相加等于 1，结构与这里完全一样——互斥且穷尽的两类结果，比例之和为 1。区别在于一边是定理，从公理推出；一边是记账，一次访存要么命中要么不命中，二者必居其一。看见两个比例加起来必须为 1 时，先分辨它属于哪一类，能省掉不少无效推导。
>
> 一句话收束：给定一条 PMF，等于给出这个离散随机变量的全部性格，任何事件的概率、expectation（期望）、variance（方差）都由它唯一决定；而和等于 1 是这条性格的第一道体检，不是可有可无的装饰。
>
> 还有个顺序值得留意：先证明对任意取值集合 $S$ 有 $P(X\in S)=\sum_{x\in S}p_X(x)$，再取 $S$ 为满值域得到归一化，逻辑更顺。因为 $S$ 里的单点事件互不相交、并为 $\{X\in S\}$，可加性直接给出求和；归一化只是这个式子在 $S$ 取满值域时的特例。反过来先背归一化再套求和式，就说不清"为什么可以对任意集合求和"，遇到 $P(X>0)$ 这类区间求和时只能凭感觉。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条注的核心是一个拆字：binomial（二项）随机变量不是全新对象，而是 $n$ 个独立同分布的 Bernoulli（伯努利）随机变量之和，$X=\sum_{i=1}^{n}B_i$；一旦这样拆开，expectation（期望）与 variance（方差）就不再需要对 $k$ 逐项求和。
>
> 先说清这个等式为什么是恒等而不是近似。第 $i$ 次试验的结果 $B_i$ 记成功为 1、失败为 0。把它们加起来，$\sum_i B_i$ 数的正是有几个 1，也就是成功了几次，这正是 $X$ 的定义。这里没有信息损失：$X$ 的每个取值 $k$ 都对应恰好 $k$ 个 $B_i$ 等于 1 这件事，反之亦然。
>
> 期望一步到位：$E[X]=\sum_i E[B_i]=\sum_i p=np$。关键在于这一步不需要 independence（独立性）：线性性只用到一个事实，即求和号可以逐项拆开，而这件事对任何一组随机变量都成立，不管它们之间怎样纠缠。很多人误以为必须先有独立性才能拆期望，那是把期望的可加性与方差的可加性混为一谈。
>
> 方差才需要独立性。$\operatorname{var}(\sum_i B_i)=\sum_i\operatorname{var}(B_i)+\sum_{i\ne j}\operatorname{cov}(B_i,B_j)$，只有协方差项全为零时才化简成 $np(1-p)$，而独立强于不相关，保证协方差为零。反过来看代价：设各次试验完全同步，要么全成功要么全失败，$X$ 就只取 0 或 $n$，均值仍是 $np$，方差却是 $n^2p(1-p)$，比 $np(1-p)$ 大 $n$ 倍。取 $n=10,p=0.3$：独立时方差 $2.1$，标准差约 $1.449$；完全同步时方差 $21$，标准差约 $4.583$。均值一样，散布差出 $\sqrt{10}$ 倍，这就是独立性被打破能造成的具体伤害。
>
> 这个视角在 CLRS《Introduction to Algorithms》第 5 章被系统化，名字叫 indicator random variable（指示随机变量）：为第 $i$ 个事件定义 $I_i$，事件发生取 1、否则取 0，于是 $E[I_i]=P(A_i)$，把所有 $I_i$ 加起来求期望，就得到期望有多少个事件发生。它在 hiring problem（雇用问题）里最直观：第 $i$ 位候选人比前面都强就雇，期望雇用次数 $\sum_{i=1}^{n}1/i\approx\ln n$；若不用指示变量，就得先求恰好雇 $k$ 次的概率，工作量差一个量级。
>
> 回到本节做两处核对。$n=1$ 时二项退化为 Bernoulli：$p_X(0)=1-p$，$p_X(1)=p$，这正是教材那句"伯努利是二项在 $n=1$ 时的特殊情形"。再算一个数：$n=4,p=0.5$，$E[X]=2$，$\operatorname{var}=4\cdot0.5\cdot0.5=1$，标准差 $1$；手算核对，$p_X$ 是 $1/16,4/16,6/16,4/16,1/16$，$E[X]=(0+4+12+12+4)/16=32/16=2$，对得上。
>
> 与 CLRS 的用法有一处区别：那边用指示变量只为算期望，从不关心中间是否独立，所以推导里不出现协方差；本课要往下走到方差、Chebyshev 不等式与随机变量和的方差，就必须把独立性单独拎出来检查。一句话收束：见到计数型的随机变量，先问它是不是一串 0/1 之和；是的话，期望白拿，方差只需再补一条独立性。
>
> 顺带补上二项 PMF 长这样的理由，它与拆成伯努利之和是同一件事的两面。要恰好 $k$ 次成功，得先决定是哪 $k$ 次：在 $n$ 个位置里选 $k$ 个，有 $\binom{n}{k}$ 种选法，这是 counting principle（计数法则）的直接产物；再对每个选定位置乘一次 $p$，对剩下 $n-k$ 个位置各乘一次 $1-p$，独立性允许把这 $n$ 个概率连乘。所以 $\binom{n}{k}p^k(1-p)^{n-k}$ 的每个因子都有出处：组合数负责位置，幂次负责每次试验的概率，两件互相独立的工作相乘。
>
> 再给一个用得上的实例：把 $m$ 个 key 散列到 $n$ 个槽，第 $i$ 个 key 落进槽 $j$ 是 Bernoulli 事件，概率 $1/n$，于是槽 $j$ 里的 key 数是 $m$ 个指示变量之和，期望 $m/n$。取 $m=n$，负载因子为 1，每个槽平均 1 个 key，但平均为 1 并不等于"没有冲突"，下一节的泊松近似会给出"空槽约占 37%"这个反直觉的结论。

### <span style="color:#c0392b;">几何随机变量（The Geometric Random Variable）</span>

<span style="color:#00838f;">**[definition] 几何随机变量（`geometric random variable`）**</span>

> 设想我们重复进行独立试验，直到出现首次成功为止，其中每次试验的成功概率为 $p$。若以概率 $1-p$ 继续出现失败、以概率 $p$ 出现成功，则首次成功会到来的尝试次数（trials）是随机变量 $X$，其取值为 $k$ 的概率等于前 $k-1$ 次失败后跟随第 $k$ 次成功的概率，故

```math
p_X(k) = (1-p)^{k-1} p, \qquad k = 1, 2, \ldots
```

该几何分布的 PMF 如图 2.4 所示。若 $X$ 服从几何分布，则 $E[X] = 1/p$。图中显示了归一化：$\sum_{k=1}^{\infty} p_X(k) = p \sum_{k=1}^{\infty} (1-p)^{k-1} = p \cdot \frac{1}{1-(1-p)} = 1$。该分布随 $k$ 以几何速率递减。

**图 2.4**　几何随机变量的 PMF。$p_X(k) = (1-p)^{k-1}p$ 随 $k$ 呈几何级数递减。其在每次试验成功概率 $p$ 恒定、试验重复进行时成立。几何随机变量的实际例子：通过给定科目测试所需的尝试次数等。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> geometric（几何）分布只做一件事：数第一次成功之前失败了多少次，$p_X(k)=(1-p)^{k-1}p$；它最值得记的不是这条公式，而是 memoryless（无记忆性）——剩余等待的分布与已经等了多久无关。
>
> 公式本身是两件独立工作的乘积：前 $k-1$ 次全失败，概率 $(1-p)^{k-1}$；第 $k$ 次成功，概率 $p$。独立性让这两件事同时发生的概率等于各自概率相乘。若试验之间不独立，比如连败之后"觉得该轮到我了"，这条乘积写法立刻失效。
>
> 归一化靠 geometric series（几何级数）：$\sum_{k\ge1}(1-p)^{k-1}p=p\cdot\frac{1}{1-(1-p)}=1$。这一步不只是形式演算，它在说"永远不成功"的概率是零：$P(X=\infty)=\lim_{m\to\infty}(1-p)^m=0$。只要 $p>0$，等待一定结束。
>
> 无记忆性写出来就是"条件概率等于无条件概率"。$P(X>m)=(1-p)^m$，即前 $m$ 次全失败。要求 $P(X>m+k\mid X>m)$，按定义为 $\frac{P(X>m+k,\ X>m)}{P(X>m)}$；而"等了 $m+k$ 次仍未成功"已经包含"等了 $m$ 次仍未成功"，所以分子就是 $(1-p)^{m+k}$。相除得 $(1-p)^k$，恰好等于 $P(X>k)$。整个推导只消两件事：独立让乘积可拆，包含关系让分子不必另算。
>
> 反例最能说明这个性质从哪来。二项 $n=10,p=0.5$：$P(X>3)$ 与 $P(X>5\mid X>2)$ 不相等，因为"总共 10 次"这个上界本身就是记忆的一部分——已经用掉 2 次，只剩 8 次机会，剩余分布自然变窄。几何分布没有总次数上限，时钟永远重新开始，所以剩余分布不变。一句话：无记忆性等于没有终点加每次独立。
>
> 均值 $1/p$ 有一条不必碰无穷级数的路，直接列方程：$E[X]=1+(1-p)E[X]$。第一次试验成功（概率 $p$）就到此为止；失败（概率 $1-p$）就浪费一次，然后面对一个全新的、与刚才完全相同的问题。解得 $pE[X]=1$，即 $E[X]=1/p$。这个方程是无记忆性最有用的副产品，它把无穷级数换成了一个一次方程。
>
> 代入数字，让无记忆性可触摸。设 $p=0.02$，平均 50 次见一次成功：$E[X]=50$，$P(X>50)=(0.98)^{50}\approx0.3642$，$P(X>100)=(0.98)^{100}\approx0.1326$。已知已经失败 50 次，再等超过 100 次的概率是 $P(X>150\mid X>50)=(0.98)^{100}\approx0.1326$，与从零开始等 100 次一模一样。白等的 50 次没有让未来变好分毫，这正是赌徒谬误在数学上的位置：它默认一个无记忆的系统会记住历史。
>
> 跨课程接 CSAPP 第 6 章。若把每次访存是否命中视为独立同分布的试验，命中概率 $h$，则连续 miss（缺失）的长度服从几何分布，期望 $1/(1-h)$；取 $h=0.95$，平均 20 次才见一次 miss。但真实 cache 有 temporal locality（时间局部性）：刚访问过的块更可能再次命中，于是下一次是否 miss 依赖历史，几何假设失效，真实的 miss 间隔比几何分布更不均匀——要么长时间不 miss，要么连着 miss 一片。
>
> 一句话收束：几何分布是"没有记忆的系统"的标准模型；凡系统带记忆，如 cache、TCP 拥塞窗口、球赛势头，它只能当零阶近似，而它失效的方式恰好能反过来说明记忆藏在哪里。
>
> 判断一个分布有没有无记忆性，有个不必计算的判据：看尾巴 $P(X>m)$ 的形状。几何分布的尾巴是纯指数 $(1-p)^m$，相除时 $m$ 必然约掉；只要尾巴里混进任何与 $m$ 有加性关系的项，比值就会把 $m$ 留下来。二项的尾巴带着"还剩几次"，泊松的尾巴带着阶乘，都约不掉。
>
> 离散与连续在这里有一处整齐的对应：几何分布数的是第几次成功，exponential（指数）分布量的是要等多少时间，两者都无记忆，$p$ 与 $\lambda$ 的角色一一对应。第 6 章讲泊松过程时，等待时间就是指数分布，这层对应能让不少公式直接搬过来。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> Poisson（泊松）分布之所以无处不在，全靠 law of rare events（稀有事件定律）：当 $n\to\infty$、$p\to0$、而 $np\to\lambda$ 保持适中时，二项 PMF 收敛到 $e^{-\lambda}\lambda^k/k!$，且 $\lambda$ 同时是均值与方差。
>
> 把推导拆开，$e$ 从哪冒出来就一清二楚。令 $p=\lambda/n$ 代入二项 PMF，得 $\binom{n}{k}(\lambda/n)^k(1-\lambda/n)^{n-k}$，三个因子分别取极限。第一，$\frac{n(n-1)\cdots(n-k+1)}{n^k}\to1$，因为 $k$ 固定，分子是 $k$ 个都近似为 $n$ 的因子。第二，$n^k(\lambda/n)^k=\lambda^k$，这一项根本不含极限。第三，$(1-\lambda/n)^n\to e^{-\lambda}$，而 $(1-\lambda/n)^{-k}\to1$ 可以并进去。三块拼起来就是 $e^{-\lambda}\lambda^k/k!$：$e^{-\lambda}$ 来自复利的那个极限，不是硬塞的常数。
>
> 三条限制各有各的活。$n\to\infty$ 让"最多 $n$ 次成功"这个天花板消失，否则 $k$ 靠近 $n$ 时阶乘比值不收敛；$p\to0$ 让"同一时刻发生两次"的概率趋于零，多出来的质量才有地方安放；$np\to\lambda$ 把平均发生率钉住，否则要么全挤在 0 上、要么全散开。缺任何一条，极限都不成立。
>
> 用教材的数核对：$n=100,p=0.01,\lambda=1,k=5$。二项给 $\binom{100}{5}(0.01)^5(0.99)^{95}=0.00290$；泊松给 $e^{-1}/120\approx0.003066$，相差 $0.00016$，相对误差约 5.6%。再看 $k=0$：二项 $(0.99)^{100}=0.36603$，泊松 $e^{-1}=0.36788$，相对误差只有 0.5%。规律是 $k$ 相对 $n$ 越小，被忽略的修正项越轻；$k$ 逼近 $n$ 时泊松明显失真，因为那边天花板开始起作用。
>
> $\lambda$ 既是均值也是方差，从 PMF 直接算：$E[X]=e^{-\lambda}\sum_k k\lambda^k/k!=\lambda e^{-\lambda}\sum_{j\ge0}\lambda^j/j!=\lambda$，把 $k/k!$ 写成 $1/(k-1)!$ 后求和又变回一个完整的泊松和。二阶矩 $E[X^2]=\lambda^2+\lambda$，于是 $\operatorname{var}=\lambda$。所以泊松只有一个参数，位置与散布被锁成同一个数：均值涨一倍，标准差只涨 $\sqrt{2}$ 倍。
>
> 跨课程最实用的一处是散列。把 $m$ 个 key 散到 $n$ 个槽，某槽的 key 数近似服从参数为 $m/n$ 的泊松分布。取 $m=n$，负载因子为 1，则某个指定槽为空的概率是 $e^{-1}\approx0.368$，即约 37% 的槽空着，另有约 26% 的槽装了 2 个以上。写 hash table 时这会反复用到：表"满"了并不代表槽用尽了，真正要处理的是冲突。区别在于真实散列的 key 总数固定，各槽计数间有弱负相关，泊松只是独立近似，$m,n$ 越大越准。
>
> 一个来源清楚的历史例子：Bortkiewicz 在 1898 年的《Das Gesetz der kleinen Zahlen》里，用普鲁士骑兵 10 个军团、20 年共 200 个军团-年的马踢致死人数拟合泊松，$n$ 大 $p$ 小正是这条定律的典型现场；分布本身则由 Poisson 在 1837 年作为二项的极限得到。
>
> 一句话收束：见到大量机会、极小概率、只数发生次数的结构，先试泊松；它的准头来自 $n$ 大 $p$ 小，而单一参数 $\lambda$ 既是均值也是方差这件事，同时决定了它何时能用、何时会失灵。
>
> 还有一面值得点明：泊松不只是二项的极限，它本身就是"把时间切成很多小格、每格至多发生一次"的自然产物。把长度为 $T$ 的区间切成 $n$ 小段，每段内发生一次的概率为 $\lambda T/n$，各段独立，由二项极限，整段内发生 $k$ 次的概率是 $e^{-\lambda T}(\lambda T)^k/k!$。这就是 Poisson process（泊松过程）的离散骨架：不是先有分布再有过程，而是同一件事的两种说法。
>
> 由这个骨架立刻得到一个常被直接引用的性质：若 $X$ 与 $Y$ 独立，分别为参数 $\lambda_1,\lambda_2$ 的泊松，则 $X+Y$ 是参数 $\lambda_1+\lambda_2$ 的泊松。代数的理由是把两个分布的卷积算一遍，等价于把两条概率生成函数相乘；直觉的理由是把两股独立的事件流合并成一股，平均发生率相加，而"稀有且独立"这个结构在合并后仍然成立。排队论里合并多个来源的到达、网络里把多条流的包计数相加，用的都是这一条。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条注要立的是一个分组再求和的机制：$p_Y(y)=\sum_{\{x:g(x)=y\}}p_X(x)$，$g(X)$ 的 distribution（分布）就是把同一 $y$ 的所有原像的 probability mass（概率质量）搬过去合并。
>
> 为什么必须求和而不能只取一个？事件 $\{Y=y\}$ 与 $\{X\in g^{-1}(y)\}$ 是同一个事件，只是换了一种描述：结果 $\omega$ 满足 $g(X(\omega))=y$，当且仅当 $X(\omega)$ 落在 $y$ 的原像里。原像可能含多个 $x$，对应的 $\{X=x\}$ 互不相交，于是可加性要求把它们的质量全部加起来。漏掉任何一个原像，等于凭空丢掉一部分概率。
>
> 漏项有代价，而且代价可测。仍用例 2.1：$X$ 在 $-4$ 到 $4$ 的整数上各占 $1/9$，$Y=|X|$。$p_Y(0)=1/9$；若把 $p_Y(1)$ 误算成 $p_X(1)=1/9$ 而漏掉 $x=-1$，总和就变成 $1/9+4\times1/9=5/9$，不等于 1。归一化这条体检会当场报警，这是它最实用的一处：不必知道正确答案，只要发现和不是 1 就知道错了。
>
> 这个求和其实是一次 partition（划分）。定义关系 $x\sim x'$ 当且仅当 $g(x)=g(x')$，它是 6.042J 里讲过的等价关系：自反、对称、传递都由"等于"直接继承。每个 $y$ 的原像就是一个 equivalence class（等价类），值域里不同的 $y$ 给出互不相交的类，全部类并起来正是整条数轴上的取值。$p_Y$ 做的就是"把每个类的质量加起来，挂到类标签上"。
>
> 由此可以给 $g$ 分类。若 $g$ 是 injective（单射），每个类只有一个元素，$p_Y$ 只是把 $p_X$ 整体搬了个位置，质量一点不损；线性变换 $Y=aX+b$ 在 $a\ne0$ 时正是这种情形。若 $g$ 多对一，信息就丢了，丢多少由每个类的大小决定。反过来，$p_Y$ 无法还原 $p_X$——从 $Y$ 的分布看不出原来每个 $x$ 各占多少，这正是后面 conditional distribution（条件分布）要补的东西：知道 $Y=y$ 之后，$X$ 在各原像上如何分摊。
>
> 接着算 $Z=X^2$。$z\in\{1,4,9,16\}$ 各有两个原像，即 $\pm1,\pm2,\pm3,\pm4$，各得 $2/9$；$z=0$ 只有一个原像，得 $1/9$；总和 $8/9+1/9=1$。顺手算 $E[Z]=0\cdot\frac19+(1+4+9+16)\cdot\frac29=\frac{60}{9}=\frac{20}{3}\approx6.667$。注意 $E[X]=0$ 而 $E[X^2]\approx6.667$，两者不等——到下一节讲期望值法则时，这一点会变成主线索：求 $E[g(X)]$ 不必先求 $g(X)$ 的分布。
>
> 跨课程接 CSAPP 第 6 章：64 位地址映射到 6 位组索引，就是一次多对一的 $g$。一个索引对应 $2^{58}$ 个字节地址，按 64 字节的块算就是 $2^{52}$ 个缓存块。硬件不把概率加起来，而是用 tag（标签）区分它们——因为硬件要问的是"这一块是不是我要的"，不是"这一类总概率多大"。同一个数学结构，两种用途：概率论要类内求和，硬件要类内区分。
>
> 一句话收束：写 $p_Y$ 之前先画 $g$ 的原像图，对着每个 $y$ 数清有几个 $x$ 落进来；单射时是搬运，多对一时是合并，合并处就是最容易漏项的地方。
>
> 用线性例子把"搬运"落实成数字。室温 $X$ 取 20 摄氏度或 30 摄氏度各一半概率，$Y=1.8X+32$。直接搬：$Y$ 取 68 或 86，各 $1/2$，于是均值为 77；先平均再变换：$E[X]=25$，$1.8\times25+32=77$。两条路一致，因为 $1.8$ 为正、每个类只有一个元素，质量既没丢也没重排。
>
> 非线性时这个便利立刻消失。同一个 $X$，令 $W=X^2$，则 $E[W]=(400+900)/2=650$，而 $(E[X])^2=625$，两者差 25，恰好是 $X$ 的方差。平方先把偏离均值的量放大再平均，这是方差定义里那个平方的来源，也是 $g(E[X])$ 与 $E[g(X)]$ 在非线性时几乎总不相等的具体表现。
>
> 顺序上也值得注意：先有 $p_Y$ 这个完整分布，才有力气谈 $E[g(X)]$；而一旦发现 $E[g(X)]$ 只需类内求和、不必知道类标签，就能跳过 $p_Y$ 直接算期望——这是下一节期望值法则省下的全部工作量。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条注要把 $E[X]=\sum_x x\,p_X(x)$ 拆成三件事：它是质心，即力矩平衡方程的解；它的 linearity（线性性）来自求和的分派律与归一化；它的 well-defined（良定义）要求 $\sum_x|x|\,p_X(x)<\infty$。
>
> 先证质心不是比喻。把 $p_X(x)$ 当作放在位置 $x$ 的质量，设 $c$ 是平衡点，则左右力矩相等：$\sum_{x<c}(c-x)p_X(x)=\sum_{x>c}(x-c)p_X(x)$。两边合写成 $\sum_x(x-c)p_X(x)=0$，展开是 $\sum_x xp_X(x)-c\sum_x p_X(x)=0$，再用归一化 $\sum_x p_X(x)=1$，立刻得 $c=\sum_x xp_X(x)$。所以"力矩平衡的解就是均值"是一条可算的恒等式，不是修辞。
>
> 良定义这条限制也不是形式主义。设 $X$ 取 $2^k$、概率 $2^{-k}$，$k=1,2,\ldots$。前 10 项之和是 $\sum_{k=1}^{10}2^k\cdot2^{-k}=10$，随项数线性增长，永远不收敛，于是 $E[X]=\infty$。更微妙的是对称版：正侧取 $+2^k$、负侧取 $-2^k$，两侧的概率质量都按 $2^{-k}$ 衰减，两个部分和各自无穷，$\sum_x xp_X(x)$ 成了 $\infty-\infty$，形式上像 0，值却取决于求和顺序，于是根本没有定义。
>
> 用具体数字看这条反例多反直觉：$k=1$ 到 $10$ 的概率之和是 $1-2^{-10}\approx0.999$，即 99.9% 的概率落在 1024 以内，均值仍被那 0.1% 的尾巴拉到无穷。这提醒一件事：期望不是最可能的值，也不是大多数时候的值，它对尾部极其敏感。这种敏感性后面会换个面貌反复出现：重尾分布，以及用样本均值估计期望时的慢收敛。
>
> 线性性的推导只有一行，每一步都在用前面的东西：$E[aX+b]=\sum_x(ax+b)p_X(x)=a\sum_x xp_X(x)+b\sum_x p_X(x)=aE[X]+b$。第二个等号是求和的分派律，第三个等号用归一化把常数项的系数消成 1。这里完全没用到 independence（独立性），也没对 $X$ 的分布做任何假设——它是恒等式，正因为如此才能在后面对方差、对随机变量和反复使用。
>
> 跨课程接一处很硬的等价：$E[X]$ 也是使 $\sum_x(x-c)^2p_X(x)$ 最小的 $c$。对 $c$ 求导置零，得 $-2\sum_x(x-c)p_X(x)=0$，即刚才那条力矩平衡方程；二阶导恒为 $2$，确实是最小值。这与线性代数里的 least squares（最小二乘）是同一件事：残差平方和极小，当且仅当残差与常数向量正交，而"与常数正交"翻译成概率语言就是"残差的加权和为 0"。区别只在每个样本点带着权重 $p_X$，且权重之和为 1，所以解是加权平均。
>
> 用例 2.2 做核对：$n=2,p=3/4$ 的二项，概率为 $1/16,6/16,9/16$，$E[X]=0\cdot\frac1{16}+1\cdot\frac6{16}+2\cdot\frac9{16}=\frac{24}{16}=1.5$，与 $np=1.5$ 一致。再看对称性：把 $X$ 换成 $2-X$，分布形状镜像，均值变成 $0.5$，这正是质心随形状移动的直接体现。
>
> 一句话收束：期望是一阶矩，是分布的位置坐标；方差是二阶中心矩，是围绕这个坐标的散布。整套矩方法从这一行求和起步，而质心解释、线性性、绝对可和这三条性质，各自对应后面一件反复要用的工具。
>
> 顺带把动机那段补严：为什么转很多次之后平均每次的钱会趋近 $\sum_i m_ip_i$？设转 $k$ 次，$m_i$ 出现 $k_i$ 次，平均值是 $\sum_i m_i k_i/k$。独立重复试验下频率 $k_i/k$ 依概率收敛到 $p_i$，这是 law of large numbers（大数定律）的结论；代入即得平均收敛到 $\sum_i m_ip_i$。所以期望不是凭空定义的数，而是长期平均的极限，这条定理保证定义与直觉对得上。
>
> 再看一个非对称例子，区分期望与典型值：$X$ 以 $0.9$ 取 0、以 $0.1$ 取 100，则 $E[X]=10$，质心被那 10% 的远端质量拉向右侧，而最可能的值是 0。若改成各一半，期望变成 50，正好落在中点。这说明期望只对质量的位置敏感，不对点数敏感：两个取值时它永远是加权中点，三个以上取值时才需要真画一遍。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条法则要解决的问题，是把“求分布”这一步从计算链上摘掉。random variable（随机变量）的分布是一个中间产物，而 expectation（期望）只需要一次按概率加权的求和；加权求和只用到 $g(X)$ 的分布，而 $g(X)$ 的分布又完全由 $X$ 的分布与 $g$ 的形状决定，于是这个中间产物是可绕过的。LOTUS（无意识统计学家法则）给的就是这条绕过路径。名字本身带自嘲：常用它的人容易把这条定理当成期望的定义，于是“无意识”地省掉了证明——它其实是定理，不是定义。
>
> 机制要拆成两层。第一层是分组：$g$ 未必是单射，多个 $x$ 可能落到同一个 $y$，求 $p_Y$ 时你被迫先分组，把同一组的 $p_X(x)$ 加在一起；教材那段验证之所以能从 $\sum_y\sum_{\{x:g(x)=y\}}$ 一路推到 $\sum_x$，靠的正是先把内层和式里那个组内统一的 $y$ 换成 $g(x)$，两层和式于是并成对全部 $x$ 的一次遍历。第二层是合法性：交换求和顺序在有限和时永远合法，有限个非负数的累加与次序无关；到可数无穷就要求绝对可和，否则重排会改变结果。这条“什么时候能换序”的边界，正是后面处理无限求和时反复要防的那个洞。
>
> 反过来问：不用这条法则会怎样？你得先算出 $p_Y$，再按 $p_Y$ 加权，等于把同一批 $p_X$ 先合并、再拆开，白做一次分组。分组本身不错，错的是它把一个线性运算挡在了一道非线性预处理后面，而那道预处理的代价随 $g$ 的像集大小增长。
>
> 手算一个非单射的例子。设一次 DNS 查询返回的答案条数 $X$，其分布为 $P(X=1)=0.7$、$P(X=2)=0.2$、$P(X=4)=0.1$；本地 cache（缓存）只留前两条，实际占用条目数 $g(x)=\min(x,2)$。走 LOTUS 一行就完：$E[g(X)]=0.7\cdot 1+0.2\cdot 2+0.1\cdot 2=1.3$。老老实实先求分布，则 $P(g=1)=0.7$、$P(g=2)=0.3$，期望 $0.7+0.6=1.3$，两条路必须同值——这就是法则的正确性在一组具体数字上的对账。再看量级：$E[X]=0.7+0.4+0.4=1.5$，截断把期望从 1.5 压到 1.3，压掉约 13%。
>
> 跨课程连接落在 CSAPP 第 6 章。direct-mapped cache（直接映射缓存）的 index 函数 $i(a)=\lfloor a/64\rfloor \bmod 1024$ 就是典型的非单射：相差 $64\times 1024$ 字节的两个地址共享同一个 set（组）。你在估平均 miss rate（缺失率）时算的是 $E[h(\text{addr})]$，其中 $h$ 是 hit 或 miss 的指示量；CSAPP 教你的做法是直接把地址流的统计特征代进去，那个手感就是 LOTUS——区别在于地址是确定的实测序列、没有概率权重，也不需要期望这个符号，而且你关心的是比值而不是期望值本身。
>
> 再补一个反面示范，把权重这件事钉死。一个常见错写是把 $E[g(X)]$ 写成 $\sum_x g(x)\,p_Y(g(x))$，也就是拿 $g(X)$ 取到该值的概率去加权原来的 $x$。用上面那组数一试就露：$x=4$ 该配的权重是 $p_X(4)=0.1$，而错写给的权重是 $P(g=2)=0.3$，一处就差三倍；把所有项按错权重加起来得 $1\cdot 0.7+2\cdot 0.3+2\cdot 0.3=1.9$，与正确的 $1.3$ 对不上。法则里那个 $p_X$ 是不可替换的，换了就等于把“每个原像各自携带的概率”误当成“整个像点携带的概率”。顺带验证最退化的情形：若 $g$ 是常函数取 $c$，法则给 $c\sum_x p_X(x)=c$，仍然对，说明它对常值也没有例外。
>
> 一句话收束：LOTUS 不是新定义，而是把分布从期望的计算路径上摘掉的许可证；下一节方差能用矩表达式一行算出，就是它第一次兑现。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这条注回答的是一个设计问题：度量散布的指标不止一种，为什么教材单挑平方。答案不是一条理由，而是一组必须同时满足的要求，平方恰好是唯一全中的那一档。
>
> 先把候选摊开比较。一阶中心矩 $E[X-E[X]]$ 不行，它恒等于零，加权平均把正负偏离精确抵消了。平均绝对偏差 $E[|X-E[X]|]$ 看着合格：非负、不抵消、与 $X$ 同单位。真正把它淘汰的是代数：绝对值在零点不可导，也没有形如平方展开的二项式，于是当你要处理两个随机变量之和时，展不出“各自贡献加交叉项”的结构，这类量因此失去可加性。三阶中心矩更糟，它带符号，在对称分布上直接得零，等于测不出散布。四阶矩能保号且更看重远端，代价是缩放规律变成四次，开四次方才回到同单位，别扭且有额外的存在性要求。
>
> 平方胜出，是因为它同时兑现三件事：非负；对缩放是二次齐次，即 $\operatorname{var}(aX)=a^2\operatorname{var}(X)$，开根号后变成一次齐次、与 $X$ 同单位；可以展开成二项式，交叉项取期望后在独立时为零，于是 $\operatorname{var}(X+Y)=\operatorname{var}(X)+\operatorname{var}(Y)$ 对独立变量成立。第一条排掉一阶，第二条排掉三阶，第三条排掉绝对值。教材那两条公式的来历也就干净了：矩表达式只是把 $E[X]$ 当常数把二次式展开再逐项取期望；平移公式只是靠期望线性让 $+b$ 在偏差里对消、让 $a$ 被平方提出。
>
> 手算一遍，并且和绝对值对照。取 $X$ 在 $\{-4,-3,\ldots,4\}$ 上均匀，每点概率 $1/9$。均值为零，$E[X^2]=(16+9+4+1+0+1+4+9+16)/9=60/9\approx 6.667$，于是 $\sigma_X\approx 2.582$。同一分布上算平均绝对偏差：$E[|X|]=(4+3+2+1+0+1+2+3+4)/9=20/9\approx 2.222$。两个数一比就看出来：$2.582$ 比 $2.222$ 大，多出来的部分正是远端四点的额外权重——平方给距离 4 的贡献是 16，给距离 1 的只有 1，比例是 16 倍而不是 4 倍。这就是“平方放大 outlier（离群值）”的量化说法，也解释了为什么一个远处的坏点能显著抬高标准差。
>
> 跨课程连接落在 Strang 的线性代数。把 $\langle X,Y\rangle=E[XY]$ 当成内积看，$\operatorname{var}(X)$ 就是 $\lVert X-E[X]\rVert^2$，也就是偏差向量长度的平方，covariance（协方差）就是内积本身；Cauchy-Schwarz（柯西–施瓦茨）不等式随即给出 $|\operatorname{cov}(X,Y)|\le\sigma_X\sigma_Y$，也就是相关系数被夹在 $-1$ 与 $1$ 之间。这条捷径只在二阶矩里存在：内积给长度，长度的平方就是方差，于是“必须平方”在这个视角下等价于“必须来自内积”。区别在于 Strang 的向量空间是 $\mathbb{R}^n$、内积是无权重点积，这里的权重是 $p_X$ 且总和为一，相当于带一个对角权重矩阵的内积。
>
> 还有一步常被跳过：为什么要先减均值。不减的话，散布就会随原点漂移。拿上面那组数整体加 10，$E[(X+10)^2]=E[X^2]+20E[X]+100=6.667+0+100=106.667$，涨到原来的十六倍；而 $\operatorname{var}$ 一动不动，还是 $6.667$。散布应当是形状的性质，不该随你把零刻度画在哪里而变，中心化就是把这个不变性焊进定义里。这也是同一份数据在不同单位制下换算出同一个散布值的前提。
>
> 一句话收束：方差不是平方更顺手，而是唯一同时保住非负、同单位、可加性三个语义的阶数；下一章 Chebyshev（切比雪夫）不等式能用几个标准差画射程，靠的正是这套单位与这套可加性。

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

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这道陷阱题真正的坑不在算术，而在一次隐形替换：把 $g$ 当成可以穿过加权平均的算子。加权平均是线性的，线性的东西能穿；$g$ 一般不是线性的，于是穿不过去。整条注就是在给“穿不过去”标定方向与幅度。
>
> 机制一次展开就够。设 $g$ 二阶可导、$\mu=E[X]$，在 $\mu$ 处做 Taylor（泰勒）展开：$g(x)=g(\mu)+g'(\mu)(x-\mu)+\tfrac12 g''(\xi)(x-\mu)^2$，其中 $\xi$ 夹在 $x$ 与 $\mu$ 之间。两边取期望，中间那项消失，因为 $E[X-\mu]=0$；剩下 $E[g(X)]=g(\mu)+\tfrac12 E[g''(\xi)(X-\mu)^2]$。这条式子一次交代三件事：$g$ 线性则二阶导为零、间隙严格为零，等号成立；$g''\ge 0$ 则间隙非负，方向是 $E[g(X)]\ge g(E[X])$，这就是 Jensen（詹森）不等式；间隙的大小与二阶导、与方差同阶，所以散布越大、弯曲越狠，错得越离谱。二阶导为负给另一侧；两侧不定时就只能说“不一定”，这也是唯一诚实的回答。
>
> 把教材的例子算到底。$V$ 以 $0.6$ 取 5 英里每小时、以 $0.4$ 取 30，则 $E[V]=0.6\cdot 5+0.4\cdot 30=15$。错误路径给出 $2/15\approx 0.1333$ 小时。正确路径先求 $T=2/V$ 的分布：$E[T]=0.6\cdot(2/5)+0.4\cdot(2/30)=0.24+0.02667=0.26667$ 小时，即 $4/15$。两者之比是 $2$，也就是说“用平均速度算平均时间”把时间低估了整整一半，这不是四舍五入级的偏差。再看 $V$ 的散布有多猛：$E[V^2]=0.6\cdot 25+0.4\cdot 900=375$，$\operatorname{var}(V)=375-225=150$，$\sigma_V\approx 12.25$，几乎与均值同一个量级，间隙被拉到两倍就不奇怪了。换成平均的语言看同一件事：加权调和平均是 $1/E[1/V]=1/0.13333\approx 7.5$，加权算术平均是 15，前者只有后者的半，$E[1/V]\neq 1/E[V]$ 就是这条不等式的日常名字。
>
> 换一个能精确对账的例子，验证前面的机制不是比喻。取 $X$ 以各半概率取 $0$ 与 $2$，$g(x)=x^2$。则 $E[X]=1$，$g(E[X])=1$，而 $E[g(X)]=(0+4)/2=2$，间隙恰为 $1$。用展开式预测：二次函数的二阶导恒为 $2$、Taylor 展开没有余项，于是间隙应等于 $\tfrac12\cdot 2\cdot\operatorname{var}(X)=\operatorname{var}(X)$；而 $\operatorname{var}(X)=E[X^2]-(E[X])^2=2-1=1$，与直接算出的间隙分毫不差。这条对账说明间隙不是模糊的“有误差”，而是可以解析预测的确定量。
>
> 方向的实际用处在于选边。做容量规划时，若单次耗时对负载是凸的，那么“按平均负载估平均耗时”必然低估，平均数落在真实均值的下方；此时保守的做法是按峰值或按间隙上浮，不能按平均数。反过来，若耗时对负载是凹的（比如批量越大单位成本越低），同一个陷阱会把结果高估，只是符号换了一边。判断符号不需要精确值，只需要二阶导的号，这正是 Jensen 给的那半个答案。
>
> 跨课程连接有两处。其一在 6.042J：那门课讲 expectation（期望）几乎只用 linearity（线性性）与 indicator variable（指示变量），全程处理线性量，所以从没撞上这个坑；本注补的正是线性之外的那一半，并且说明线性之外唯一能说的话——给一个方向，再加一个与方差同阶的误差项。其二在 CSAPP 第 11 章：TCP 的粗算吞吐是窗口除以往返时延，对窗口是线性的；一旦把丢包恢复算进去，真实 goodput（有效吞吐）变成窗口除以“往返时延加恢复时间”，对丢包率就是倒数型非线性。于是“平均丢包率代入公式算平均吞吐”与“平均速度算平均时间”是同一个错误，区别在于 CSAPP 只关心单条连接的一次行为，从不对它取期望。
>
> 一句话收束：以后见到 $E[g(X)]$，先问 $g$ 线性吗；不线性就去找二阶导的符号，报一个方向，而不是报一个数。

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