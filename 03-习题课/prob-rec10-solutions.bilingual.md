<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 10 解答（Recitation 10: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；内容即 6.041/6.431 Spring 2010 Quiz 1 解答（Quiz 1 Solutions））</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Question 1（第 1 题）**</span>

<span style="color:#00838f;">**1.1**　下列各陈述中，哪一个是正确的？</span>

- (a) $P(A\cap B)$ 可能大于 $P(A)$。
- (b) $X$ 的方差（variance）可能大于 $2X$ 的方差。
- (c) 若 $A^c\cap B^c=\emptyset$，则 $P(A\cup B)=1$。
- (d) 若 $A^c\cap B^c=\emptyset$，则 $P(A\cap B)=P(A)P(B)$。
- (e) 若 $P(A)>1/2$ 且 $P(B)>1/2$，则 $P(A\cup B)=1$。

> <span style="color:#2471a3;">[solution]</span> 答案：**(c)** 正确，因为 $A\cup B=(A^c\cap B^c)^c=\emptyset^c=\Omega$（样本空间）。

<span style="color:#00838f;">**1.2**　下列各陈述中，哪一个是正确的？</span>

- (a) 若 $E[X]=0$，则 $P(X>0)=P(X<0)$。
- (b) $P(A)=P(A\mid B)+P(A\mid B^c)$
- (c) $P(B\mid A)+P(B\mid A^c)=1$
- (d) $P(B\mid A)+P(B^c\mid A^c)=1$
- (e) $P(B\mid A)+P(B^c\mid A)=1$

> <span style="color:#2471a3;">[solution]</span> 答案：**(e)** 正确，因为 $B$ 与 $B^c$ 构成对 $\Omega$ 的一个分割（partition）。
>
> <span style="color:#1e8449;">[mathtip]</span> 这是因为 $A\cap B$ 与 $A\cap B^c$ 互斥（disjoint）且并集为 $A$，故 $P(A\cap B)+P(A\cap B^c)=P(A)$；两边除以 $P(A)$ 即得 $P(B\mid A)+P(B^c\mid A)=1$。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Question 2（第 2 题）**</span>

Heather（希瑟）与 Taylor（泰勒）用一枚不均匀硬币（unfair coin）的独立投掷来玩一个游戏：每次投掷出现正面（head）的概率为 $p$，其中 $0<p<1$。硬币被反复投掷，直到第二次出现正面——此时 Heather 获胜；或者第二次出现反面（tail）——此时 Taylor 获胜。注意：一局完整的游戏包含 2 或 3 次投掷。

<span style="color:#00838f;">**2.1**　考虑该游戏的一个概率模型，其样本结果（outcome）为一局完整游戏中正面与反面构成的序列。请列出全部结果及其发生的概率。</span>

> <span style="color:#2471a3;">[solution]</span> 由于各次投掷相互独立（independence），各结果及其概率如下：
>
> | 结果 | 概率 |
> |---|---|
> | $HH$ | $p^2$ |
> | $HTH$ | $p^2(1-p)$ |
> | $HTT$ | $p(1-p)^2$ |
> | $THH$ | $p^2(1-p)$ |
> | $THT$ | $p(1-p)^2$ |
> | $TT$ | $(1-p)^2$ |

<span style="color:#00838f;">**2.2**　Heather 获胜的概率是多少？</span>

> <span style="color:#2471a3;">[solution]</span> Heather 获胜的事件是 $\{HH,HTH,THH\}$。将该事件中各结果的概率相加，得
>
> ```math
> p^2+p^2(1-p)+p^2(1-p)=p^2(3-2p).
> ```

<!-- ===== PDF p2 ===== -->

**（续）**

<span style="color:#00838f;">**2.3**　已知第一次投掷出现正面，求 Heather 获胜的条件概率（conditional probability）。</span>

> <span style="color:#2471a3;">[solution]</span> 由条件概率的定义，
>
> ```math
> P(\{\text{Heather wins}\}\mid\{\text{first toss H}\})
> =\frac{P(\{\text{Heather wins}\}\cap\{\text{first toss H}\})}{P(\{\text{first toss H}\})}
> =\frac{P(\{HH,HTH\})}{P(\{\text{first toss H}\})}
> =\frac{p^2+p^2(1-p)}{p}=p(2-p).
> ```
>
> <span style="color:#1e8449;">[mathtip]</span> 事件 $\{\text{Heather wins}\}=\{HH,HTH,THH\}$，但在“第一次投掷为正面”的条件下，与其相交的只有 $HH$ 与 $HTH$ 两个结果。

<span style="color:#00838f;">**2.4**　已知 Heather 获胜，求第一次投掷出现正面的条件概率。</span>

> <span style="color:#2471a3;">[solution]</span> 同理，
>
> ```math
> P(\{\text{first toss H}\}\mid\{\text{Heather wins}\})
> =\frac{P(\{\text{first toss H}\}\cap\{\text{Heather wins}\})}{P(\{\text{Heather wins}\})}
> =\frac{P(\{HH,HTH\})}{P(\{\text{Heather wins}\})}
> =\frac{p^2+p^2(1-p)}{p^2(3-2p)}=\frac{2-p}{3-2p}.
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Question 3（第 3 题）**</span>

某赌场提供一种使用均匀四面骰（fair 4-sided die，各面分别标有 1、2、3、4）的游戏，其中一局基础游戏（basic game）包含 1 或 2 次掷骰：

- 若第一次掷出 1、2 或 3，玩家赢得与骰子点数等额的美元，游戏结束。
- 若第一次掷出 4，玩家赢得 \$2 以及第二次（“奖励”，bonus）掷骰点数等额的美元。

设 $X$ 为一局基础游戏的收益（payoff，单位为美元）。

<span style="color:#00838f;">**3.1**　求 $X$ 的概率质量函数（PMF）$p_X(x)$。</span>

> <span style="color:#2471a3;">[solution]</span> 定义一个概率模型：其样本结果为一局完整游戏中掷骰结果的序列。各结果、其概率以及对应的 $X$ 值如下：
>
> | $\omega$ | $P(\{\omega\})$ | $X(\omega)$ |
> |---|---|---|
> | $(1)$ | $1/4$ | $1$ |
> | $(2)$ | $1/4$ | $2$ |
> | $(3)$ | $1/4$ | $3$ |
> | $(4,1)$ | $1/16$ | $3$ |
> | $(4,2)$ | $1/16$ | $4$ |
> | $(4,3)$ | $1/16$ | $5$ |
> | $(4,4)$ | $1/16$ | $6$ |

<!-- ===== PDF p3 ===== -->

**（续）**

> <span style="color:#2471a3;">[solution]</span>（续）将 $X$ 各可能取值对应的概率归并，得
>
> ```math
> p_X(x)=\begin{cases}
> 1/4, & x=1,2;\\
> 5/16, & x=3;\\
> 1/16, & x=4,5,6;\\
> 0, & \text{otherwise.}
> \end{cases}
> ```

<span style="color:#00838f;">**3.2**　求 $E[X]$。</span>

> <span style="color:#2471a3;">[solution]</span> 用上一小问求得的 PMF 来计算 $E[X]$，其实并不需要太多算术；一个更优雅的解法是使用全期望定理（total expectation theorem）。设 $A$ 为事件“第一次掷出 4”。则
>
> ```math
> E[X]=P(A)\,E[X\mid A]+P(A^c)\,E[X\mid A^c]
> =\underbrace{1/4}_{P(A)}\cdot\underbrace{4.5}_{E[X\mid A]}+\underbrace{3/4}_{P(A^c)}\cdot\underbrace{2}_{E[X\mid A^c]}=\frac{21}{8}.
> ```
>
> 其中 $E[X\mid A]=4.5$，因为此时的条件分布是 $\{3,4,5,6\}$ 上的均匀分布（uniform distribution）；而 $E[X\mid A^c]=2$，因为此时的条件分布是 $\{1,2,3\}$ 上的均匀分布。

<span style="color:#00838f;">**3.3**　在 $X=3$ 的条件下，求第一次掷骰结果的条件 PMF（conditional PMF）。（请使用你明确定义的合理记号。）</span>

> <span style="color:#2471a3;">[solution]</span> 设 $Z$ 为第一次掷骰的结果，并令 $B=\{X=3\}$。由条件化（conditioning）的定义，
>
> ```math
> p_{Z\mid B}(z)=\frac{P(\{Z=z\}\cap B)}{P(B)}.
> ```
>
> 利用上表中的数值，
>
> ```math
> p_{Z\mid B}(z)=\begin{cases}
> 4/5, & z=3;\\
> 1/5, & z=4;\\
> 0, & \text{otherwise.}
> \end{cases}
> ```
>
> <span style="color:#1e8449;">[mathtip]</span> 由表格可得 $P(B)=P(\{X=3\})=1/4+1/16=5/16$；$P(\{Z=3\}\cap B)=1/4$（结果 $(3)$），$P(\{Z=4\}\cap B)=1/16$（结果 $(4,1)$），代入即得上述条件 PMF。

<span style="color:#00838f;">**3.4**　现在考虑一个可以有任意多次奖励掷骰的扩展游戏（extended game）。具体而言：</span>

- 任何一次掷出 1、2 或 3，玩家赢得与骰子点数等额的美元，游戏终止。
- 任何一次掷出 4，玩家赢得 \$2，游戏继续。

设 $Y$ 为扩展游戏的收益（payoff，单位为美元）。求 $E[Y]$。

> <span style="color:#2471a3;">[solution]</span> 显式求出 $Y$ 的 PMF 固然可行，但没有必要地繁琐。不妨令 $L$ 为最后一次掷骰的收益，$W$ 为此前所有掷骰的收益。则按构造有 $Y=W+L$，从而 $E[Y]=E[W]+E[L]$。
>
> 最后一次掷骰在 $\{1,2,3\}$ 上均匀分布，故 $E[L]=2$。此前各次掷骰的收益合计为 $2(N-1)$，其中 $N$ 为一局游戏中的掷骰次数。由于游戏的终止可视为一次“成功概率为 $3/4$ 的伯努利试验（Bernoulli trial）”中的“成功”，所以 $N$ 服从参数为 $3/4$ 的几何分布（geometric distribution）。于是
>
> ```math
> E[W]=E[2(N-1)]=2E[N]-2=2\cdot\frac{4}{3}-2=\frac{2}{3}.
> ```
>
> <span style="color:#1e8449;">[mathtip]</span> 参数为 $p$ 的几何分布其期望为 $1/p$，故 $E[N]=1/(3/4)=4/3$。
>
> 综合以上计算，
>
> ```math
> E[Y]=E[W]+E[L]=\frac{2}{3}+2=\frac{8}{3}.
> ```
>
> （还有许多其他解法。）

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare（MIT 开放课件）　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 Probabilistic Systems Analysis and Applied Probability（概率系统分析与应用概率），Fall 2010（2010 秋季学期）。有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>

