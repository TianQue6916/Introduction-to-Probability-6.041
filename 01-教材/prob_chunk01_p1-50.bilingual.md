<span style="color:#7f8c8d;">`BT &Tsitsiklis, Introduction to Probability, 2nd ed. · 第 1 单元 · 对应 PDF 第 1–50 页`</span>

# Introduction to Probability（概率导论）— 单元 1（第 1–50 页）

> <span style="color:#7f8c8d;">**单元页范围**：PDF 第 1–50 页；内容 = 书名/版权/前言/目录 + 第 1 章 **Sample Space and Probability（样本空间与概率）** 的 1.1 Sets（集合）、1.2 Probabilistic Models（概率模型）、1.3 Conditional Probability（条件概率）、1.4 Total Probability Theorem & Bayes' Rule（全概率定理与贝叶斯法则）、1.5 Independence（独立性）的开篇。</span>
> <span style="color:#7f8c8d;">**教材缩写**：BT = Bertsekas & Tsitsiklis，2nd ed.</span>

---


---

batch_A.md
<span style="color:#7f8c8d;">*PDF 第 1–12 页：书名页、版权页、献词、前言、目录，及第 1 章开篇。*</span>

# <span style="color:#c0392b;">Introduction to Probability（概率导论）</span>

## Second Edition（第二版）

**Dimitri P. Bertsekas（迪米特里·P. 伯塞卡斯） 和 John N. Tsitsiklis（约翰·N. 齐齐克利斯）**

Massachusetts Institute of Technology（麻省理工学院）

<span style="color:#7f8c8d;">WWW 网站（书刊信息与订购）：http://www.athenasc.com</span>

**Athena Scientific（雅典娜科学出版社）, Belmont（贝尔蒙特）, Massachusetts（马萨诸塞州）**

---

**Athena Scientific（雅典娜科学出版社）**
邮政信箱 805（Post Office Box 805）
Nashua（纳舒厄）, NH 03061-0805, U.S.A.（美国）

<span style="color:#7f8c8d;">电子邮箱（Email）: info@athenasc.com　　WWW: http://www.athenasc.com</span>

<span style="color:#7f8c8d;">封面设计（Cover Design）：Ann Gallager（安·加拉格尔）</span>

**© 2002, 2008 Dimitri P. Bertsekas（迪米特里·P. 伯塞卡斯） 和 John N. Tsitsiklis（约翰·N. 齐齐克利斯）**

保留一切权利（All rights reserved）。未经出版者书面许可，本书的任何部分不得以任何电子或机械方式（包括影印、录制或信息存储与检索）加以复制。

> <span style="color:#7f8c8d;">**出版者目录数据（Publisher's Cataloging-in-Publication Data）**</span>
> - Bertsekas, Dimitri P., Tsitsiklis, John N.（伯塞卡斯，迪米特里·P.；齐齐克利斯，约翰·N.）
> - Introduction to Probability（概率导论）
> - 含参考文献与索引（bibliographical references and index）
> - 1. 概率（Probabilities）　2. 随机过程（Stochastic Processes）　I. 书名
> - QA273.B475 2008
> - 519.2 - 21
> - 美国国会图书馆控制号（Library of Congress Control Number）：2002092167
> - ISBN 978-1-886529-23-6

---

*纪念（To the memory of）－*
**Pantelis Bertsekas（潘特利斯·伯塞卡斯） 与 Nikos Tsitsiklis（尼科斯·齐齐克利斯）**

---

# <span style="color:#c0392b;">Preface（前言）</span>

> 概率是化为计算的常识（Probability is common sense reduced to calculation）
> —— Laplace（拉普拉斯）

本书源于我们在麻省理工学院（Massachusetts Institute of Technology）讲授一门概率入门课程（"Probabilistic Systems Analysis"（概率系统分析））的经历。

这门课有大量背景各异、兴趣广泛的学生参加。他们横跨整个谱系：从大一新生到刚开始读研的学生，从工学院到管理学院。因此，我们力图在阐述的简明性与分析推理的复杂度之间取得平衡。我们的核心目标在于培养一种能力：以直觉理解与数学严谨性相结合的方式来构造并分析概率模型（probabilistic models）。

本着这一精神，正文中对某些数学上更严格的分析仅作粗略勾勒或直觉性解释，以免复杂的证明妨碍原本简明的阐述。与此同时，其中部分分析又以更高深的微积分水平（advanced calculus）在"理论问题"（theoretical problems）中得到展开，这些题目收录在相应章节结尾。此外，一些更微妙的数学问题以脚注（footnotes）形式向更细心的读者作出提示。

本书涵盖概率论的基础内容（概率模型、离散与连续随机变量、多元随机变量以及极限定理），这些通常属于概率论首门课程的标准内容。本书在第 4–6 章还收录了若干更进阶的专题，教师可根据具体课程目标进行取舍。特别是，在第 4 章中我们研究了变换（transforms）、条件作用（conditioning）的更进阶视角、随机变量之和、最小二乘估计（least squares estimation）以及二元正态分布（bivariate normal distribution）。

此外，在第 5、6 章中，我们对伯努利过程（Bernoulli process）、泊松过程（Poisson process）和马尔可夫过程（Markov process）给出了较为详细的入门介绍。

我们在 M.I.T. 的课程在一个学期内覆盖全部七章，仅略去关于二元正态分布（第 4.7 节）以及连续时间马尔可夫链（continuous-time Markov chains，第 6.5 节）的内容。不过，在另一种课程方案中，随机过程部分也可以略去，从而使基础性内容获得更多关注，或供教师按自己的选择讲授其他专题。

我们在覆盖面方面最明显的省略是对统计学（statistics）的介绍。虽然我们以贝叶斯规则（Bayes' rule）的离散与连续模型以及最小二乘估计的形式，完整展开了贝叶斯统计学的基本要素，但我们并未深入参数估计（parameter estimation）或非贝叶斯假设检验（non-Bayesian hypothesis testing）等课题。

对正文作补充的题目分为三类：

**(a) 理论问题（Theoretical problems）：** 理论问题（以 `*` 标记）构成文本的一个重要组成部分，确保偏好数学的读者能找到一条平滑无重大缺环的发展路径。其解答在正文中给出，但有雄心的读者（尤其在较早章节）或许能在查看解答之前独立解出其中许多题。

**(b) 正文中的问题（Problems in the text）：** 除理论问题外，正文还包含若干难度各异的习题。它们体现了 M.I.T. 习题课与辅导课所覆盖题型的代表性，也是我们许多学生掌握材料的主要途径。我们希望其他学校的学生也能先尝试求解这些题目，再对照解答以校准并加深对材料的理解。解答发布在本书的 www 网站：http://www.athenasc.com/probbook.html

**(c) 补充问题（Supplementary problems）：** 还有一大批（且在不断扩充）的附加习题，它们并未收录进书，而是发布于本书的 www 网站。其中许多题目曾在 M.I.T. 用作作业或考试题，我们期望其他学校的教师也能用于类似目的。这些附加题的题干是公开可访问的，而其解答仅由作者提供给课程讲授教师。

我们要感谢多位以不同方式为本书作出贡献的人。我们的写作计划始于我们接手 M.I.T. 一门广受欢迎的概l率课，这门课此前由我们的同事 Al Drake（阿尔·德雷克）讲授了几十年。我们很幸运得以从一个经受住时间考验的学科组织、Al 经典教材中生动活泼的专题呈现，以及一套在习题课和作业中实际使用过的丰富材料出发。因此我们感谢 Al Drake 提供了一个非常有利的起点条件。

我们感谢数位在不同大学讲授过本书草稿或通读过它并给我们提供宝贵反馈的同事。特别地，我们感谢 Ibrahim Abou Faycal、Gustavo de Veciana、Eugene Feinberg、Bob Gray、Muriel Medard、Jason Papastavrou、Ilya Pollak、David Tse 和 Terry Wagner。

M.I.T. 这门课的助教们也非常有帮助。他们指出了多版草稿中的错误，开发了适合课程的题目与解答，并通过与学生群体的直接互动，为校准材料难度提供了一个稳健的机制。能够接触 M.I.T. 数千名才华横溢、正处于学习早期阶段的学生，对我们而言是极大的满足。我们感谢他们宝贵的反馈，也感谢他们在以一本"写作中的教科书"授课时的耐心。

最后但同样重要的是，我们感谢家人在这漫长项目全程中给予的支持。

<span style="color:#7f8c8d;">Dimitri P. Bertsekas（迪米特里·P. 伯塞卡斯）, dimitrib@mit.edu
John N. Tsitsiklis（约翰·N. 齐齐克利斯）, jnt@mit.edu
Cambridge（剑桥）, Mass.（马萨诸塞州）, 2002 年 5 月</span>

---

# <span style="color:#c0392b;">Preface to the Second Edition（第二版前言）</span>

这是对第 1 版的一次重大修订，涉及旧材料的重组和新材料的增加。本书篇幅增加了约 25%。主要改动如下：

**(a)** 新增了两章关于统计推断（statistical inference）的内容，一章关于贝叶斯方法（Bayesian），一章关于经典方法（classical）。我们的理念是聚焦主要概念，并通过若干关键示例帮助理解主要方法。

**(b)** 第 3、4 章经过了修订，部分是为了容纳推断章节的新材料，部分是为了使表述更精炼。第 1 版中的第 4.7 节（二元正态分布）在新版中被删去，但可在本书网站获取。

**(c)** 增加了一批新的例题和章末习题。

新版的主要目标是给教师在材料选择上提供灵活性，特别是让他们可以选择纳入统计推断的介绍。注意第 6–7 章与第 8–9 章是相互独立的，从而允许选用穿过本书的不同路径。此外，第 5–7 章并不需要第 4 章，而第 8、9 章只需要第 4 章中的第 4.2–4.3 节。因此，基于本书的若干可行课程方案如下：

**(a)** 概率论与统计推断入门：第 1–3 章、第 4.2–4.3 节、第 5 章、第 8–9 章。

**(b)** 概率论与随机过程入门：第 1–3 章和第 5–7 章，视情况可选第 4 章中的若干节。

我们要感谢多位对第 1 版材料或新章节材料组织提供了宝贵意见的同事。Ed Coffman、Munther Dahleh、Vivek Goyal、Anant Sahai、David Tse、George Verghese、Alan Willsky 和 John Wyatt 在这方面帮助很大。最后，我们感谢 Mengdi Wang（王梦迪）在为新章节绘制插图与编写题目方面的帮助。

<span style="color:#7f8c8d;">Dimitri P. Bertsekas（迪米特里·P. 伯塞卡斯）, dimitrib@mit.edu
John N. Tsitsiklis（约翰·N. 齐齐克利斯）, jnt@mit.edu
Cambridge（剑桥）, Mass.（马萨诸塞州）, 2008 年 6 月</span>

---

# <span style="color:#c0392b;">Contents（目录）</span>

**1. Sample Space and Probability（样本空间与概率）**
- 1.1 集合（Sets）　— p. 3
- 1.2 概率模型（Probabilistic Models）　— p. 6
- 1.3 条件概率（Conditional Probability）　— p. 18
- 1.4 全概率定理与贝叶斯规则（Total Probability Theorem and Bayes' Rule）　— p. 28
- 1.5 独立性（Independence）　— p. 34
- 1.6 计数（Counting）　— p. 44
- 1.7 小结与讨论（Summary and Discussion）　— p. 51
- 习题（Problems）　— p. 53

**2. Discrete Random Variables（离散随机变量）**
- 2.1 基本概念（Basic Concepts）　— p. 71
- 2.2 概率质量函数（Probability Mass Functions）　— p. 72
- 2.3 随机变量的函数（Functions of Random Variables）　— p. 74
- 2.4 期望、均值与方差（Expectation, Mean, and Variance）　— p. 80
- 2.5 多元随机变量的联合 PMF（Joint PMFs of Multiple Random Variables）　— p. 81
- 2.6 条件作用（Conditioning）　— p. 92
- 2.7 独立性（Independence）　— p. 97
- 2.8 小结与讨论（Summary and Discussion）　— p. 109
- 习题（Problems）　— p. 115

**3. General Random Variables（一般随机变量）**
- 3.1 连续随机变量与 PDF（Continuous Random Variables and PDFs）　— p. 119
- 3.2 累积分布函数（Cumulative Distribution Functions）　— p. 139
- 3.3 正态随机变量（Normal Random Variables）　— p. 140
- 3.4 多元随机变量的联合 PDF（Joint PDFs of Multiple Random Variables）　— p. 148
- 3.5 条件作用（Conditioning）　— p. 153
- 3.6 连续型贝叶斯规则（The Continuous Bayes' Rule）　— p. 158
- 3.7 小结与讨论（Summary and Discussion）　— p. 164
- 习题（Problems）　— p. 178

**4. Further Topics on Random Variables（随机变量的进阶专题）**
- 4.1 导出的分布（Derived Distributions）　— p. 201
- 4.2 协方差与相关（Covariance and Correlation）　— p. 202
- 4.3 再访条件期望与条件方差（Conditional Expectation and Variance Revisited）　— p. 217
- 4.4 变换（Transforms）　— p. 222
- 4.5 独立随机变量随机个数之和（Sum of a Random Number of Independent Random Variables）　— p. 229
- 4.6 小结与讨论（Summary and Discussion）　— p. 240
- 习题（Problems）　— p. 244

**5. Limit Theorems（极限定理）**
- 5.1 马尔可夫不等式与切比雪夫不等式（Markov and Chebyshev Inequalities）　— p. 263
- 5.2 大数弱定律（The Weak Law of Large Numbers）　— p. 265
- 5.3 依概率收敛（Convergence in Probability）　— p. 269
- 5.4 中心极限定理（The Central Limit Theorem）　— p. 271
- 5.5 大数强定律（The Strong Law of Large Numbers）　— p. 273
- 5.6 小结与讨论（Summary and Discussion）　— p. 280
- 习题（Problems）　— p. 282

**6. The Bernoulli and Poisson Processes（伯努利过程与泊松过程）**
- 6.1 伯努利过程（The Bernoulli Process）　— p. 295
- 6.2 泊松过程（The Poisson Process）　— p. 297
- 6.3 小结与讨论（Summary and Discussion）　— p. 309
- 习题（Problems）　— p. 324

**7. Markov Chains（马尔可夫链）**
- 7.1 离散时间马尔可夫链（Discrete-Time Markov Chains）　— p. 339
- 7.2 状态分类（Classification of States）　— p. 340
- 7.3 稳态行为（Steady-State Behavior）　— p. 346
- 7.4 吸收概率与到吸收的期望时间（Absorption Probabilities and Expected Time to Absorption）　— p. 352
- 7.5 连续时间马尔可夫链（Continuous-Time Markov Chains）　— p. 362
- 7.6 小结与讨论（Summary and Discussion）　— p. 369
- 习题（Problems）　— p. 378

**8. Bayesian Statistical Inference（贝叶斯统计推断）**
- 8.1 贝叶斯推断与后验分布（Bayesian Inference and the Posterior Distribution）　— p. 407
- 8.2 点估计、假设检验与 MAP 规则（Point Estimation, Hypothesis Testing, and the MAP Rule）　— p. 412
- 8.3 贝叶斯最小均方估计（Bayesian Least Mean Squares Estimation）　— p. 420
- 8.4 贝叶斯线性最小均方估计（Bayesian Linear Least Mean Squares Estimation）　— p. 430
- 8.5 小结与讨论（Summary and Discussion）　— p. 437
- 习题（Problems）　— p. 444

**9. Classical Statistical Inference（经典统计推断）**
- 9.1 经典参数估计（Classical Parameter Estimation）　— p. 459
- 9.2 线性回归（Linear Regression）　— p. 462
- 9.3 二元假设检验（Binary Hypothesis Testing）　— p. 477
- 9.4 显著性检验（Significance Testing）　— p. 486
- 9.5 小结与讨论（Summary and Discussion）　— p. 496
- 习题（Problems）　— p. 505

**Index（索引）** — p. 521

---

> <span style="color:#2471a3;">**[note]** 目录结构导读：</span> 本教材有一个值得注意的"依存说明"——第 4 章（随机变量进阶专题）的变换、协方差等内容是后续第 5–7 章（极限定理、伯努利/泊松过程、马尔可夫链）的基础，但它并非其唯一前提；真正让第 8、9 两章（贝叶斯与经典统计推断）能单独开课的是它们只需用到第 4 章的 4.2–4.3 节。对你（正在学 6.006 算法导论、CLRS）而言，这里可类比 CLRS 的分治与动态规划章节：表面的"章节顺序"并不代表唯一的阅读依赖，作者在第 6–9 章之间特别标注了"相互独立"，正是提醒读者存在多条阅读路径（可对照教科书第二版前言中的课程方案说明）。
<span style="color:#7f8c8d;">BT 目录 p. ix–xi</span>

---

# <span style="color:#c0392b;">Chapter 1. Sample Space and Probability(第 1 章　样本空间与概率)</span>

**Contents（目录）**
- 1.1 集合（Sets）　— p. 3
- 1.2 概率模型（Probabilistic Models）　— p. 6
- 1.3 条件概率（Conditional Probability）　— p. 18
- 1.4 全概率定理与贝叶斯规则（Total Probability Theorem and Bayes' Rule）　— p. 28
- 1.5 独立性（Independence）　— p. 34
- 1.6 计数（Counting）　— p. 44
- 1.7 小结与讨论（Summary and Discussion）　— p. 51
- 习题（Problems）　— p. 53

<span style="color:#7f8c8d;">BT Ch. 1, p. 1</span>

"概率（Probability）"是一个非常有用的概念，但可以被多方式解读。作为说明，考虑下面的例证。

一位病人被送进医院，并接受了一种可能救命的药物。护士与一位忧心忡忡的亲属之间发生了如下对话。

> 亲属：护士，这药起作用的概率是多少？
> 护士：我希望它起作用，我们明天就知道了。
> 亲属：是的，但是它起作用的概率到底是多少？
> 护士：每个病例都不同，我们得等等看。
> 亲属：但是这样想，在一百个在相似条件下接受治疗的病人中，你会预期它起作用多少次？
> 护士（稍显恼火）：我跟你说过了，每个人都是不同的，对有些人它起作用，对有些人则不起。
> 亲属（坚持）：那告诉我，如果你不得不在"它起不起作用"上下注，你会押哪一边？
> 护士（一时振作起来）：我会押它起作用。
> 亲属（稍感宽慰）：好，现在，你愿不愿意在它不起作用时输掉两美元，而在它起作用时赢得一美元？
> 护士（恼怒）：多么病态的想法！你在浪费我的时间！
> 亲属：

在这段对话中，亲属试图用概率这一概念来讨论一种不确定的情形。护士最初的反应表明"概率"的含义并非公认或一致地为人所理解，而亲属则试图使它更具体。第一种做法是根据出现频率（frequency of occurrence）来定义概率，即把它看作在相当大量类似情形中成功的百分比。这样的解读往往是自然的。例如，当我们说一枚制造精良的硬币"以概率 50%"抛出正面时，我们通常的意思是"大约一半的时候"。但护士拒绝以这类说法讨论也可能未必全错。万一这是一种在这家医院或护士的阅历中首次使用的实验性药物呢？

尽管有许多涉及不确定性的情形中频率解读（frequency interpretation）是恰当的，但也有另一些情形它并不恰当。例如，考虑一位学者断言《伊利亚特》（Iliad）和《奥德赛》（Odyssey）出自同一人之手概率为 90%。这样的断言传达了某种信息，但不是以频率的方式，因为这个对象是单次事件（one-time event）。毋宁说，它是学者主观信念（subjective belief）的一种表达。有人或许会认为主观信念并不值得关注，至少从数学或科学的观点看是如此。另一方面，人们常常不得不在存在不确定性的情形下作出抉择，而一种系统化地运用自身信念的方式，正是作出成功或至少前后一致的决策（decision making）的前提条件。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这里用医院药物与荷马史诗两则例子，首次点出贯穿全书的一条主线——"概率"到底指什么，以及在什么前提下可以把它当作数学对象。第一类是频率解读（frequency interpretation）：认为概率等于"大量同类试验中成功的比例"。这与你在 6.042J 数学基础里接触到的"大量重复实验的长期比例"直觉一脉相承，也将在第 5 章大数定律（the weak/strong law of large numbers）中得到严格刻画：样本均值以概率收敛到期望值。第二类是主观信念（subjective belief）：把概率理解为对"单次事件"信任程度的量化，这在贝叶斯统计推断（第 8 章）中成为核心——你把自己对未知参数先验的相信程度写成先验分布，再用观测数据更新为后验分布。需要留意的是，教材在此并不急于站队，而是给出两种合法视角的并存：频率派强调"可重复试验"的长程客观比例，贝叶斯派强调"信息量化为分布"的主观更新。对正在学 100B 实分析的你而言，可把"频率→概率"的过渡看作一个弱极限过程：当试验次数 $n\to\infty$ 时经验频率趋于真实概率，而这一收敛的严格化正是第 5 章用 $\epsilon$–余集论证（$\epsilon$-arguments）处理的内容，与实分析中数列收敛的定义在精神上完全同构。
<span style="color:#7f8c8d;">BT §1.1, p. 1–2</span>

---

batch_B.md
# <span style="color:#c0392b;">Sample Space and Probability（样本空间与概率）</span>

> <span style="color:#7f8c8d;">BT §1.1–1.2</span>

实际上，一个理性人（`rational person`）的选择与行动，可以透露大量关于其内心所持的主观概率（`subjective probabilities`）的信息——即使这个人并没有有意识地使用概率推理。确实，前面那段对话的最后部分，就是试图以间接的方式推断护士的信念。既然护士愿意接受一赔一的赌注（即接受"药物有效则她赢"这一对赌），我们可以推断，在她看来成功的概率至少是 50%。如果护士接受了最后给出的那个赌注（二赔一），则会表明她认为成功概率至少是 2/3。

与其进一步纠缠于"概率推理是否恰当"这类哲学问题，我们不如干脆把这一点当作既定前提：概率论（`probability theory`）在极其广泛的语境中都非常有用，包括某些假定的概率仅仅反映主观信念的情形。在科学、工程、医学、管理等诸多领域，都有一大批成功的应用；基于这些经验证据，概率论是一个极为有用的工具。

本书的主要目标，是培养借助概率模型（`probabilistic models`）来描述不确定性的艺术，以及概率推理（`probabilistic reasoning`）的技能。第一步，也是本章的主题，是描述这类模型的一般结构及其基本性质。我们所要考虑的模型，会把概率分配给一组一组（即集合，`sets`）的可能结果（`outcomes`）。正因为如此，我们必须从对集合论（`set theory`）的简短回顾开始。

## <span style="color:#c0392b;">1.1 Sets（集合）</span>

概率论大量用到集合运算，因此我们先在开头引入相关的记号与术语。

一个**集合**（`set`）是若干对象的汇集，这些对象称为该集合的**元素**（`elements`）。若 $S$ 是一个集合，且 $x$ 是 $S$ 的一个元素，我们就记作 $x \in S$。若 $x$ 不是 $S$ 的元素，则记作 $x \notin S$。一个集合可以没有元素；在这种情况下，它被称为**空集**（`empty set`），记作 $\varnothing$。

集合有多种描述方式。若 $S$ 含有有限个元素，设其元素为 $x_1,\, x_2,\, \ldots,\, x_n$，我们就把这些元素用花括号列出来：

```math
S = \{x_1,\, x_2,\, \ldots,\, x_n\}.
```

例如，掷一颗骰子所有可能结果的集合是 $\{1,\,2,\,3,\,4,\,5,\,6\}$，而抛一枚硬币所有可能结果的集合是 $\{H,\,T\}$，其中 $H$ 代表"正面"（`heads`），$T$ 代表"反面"（`tails`）。

若 $S$ 含有无穷多个元素，且这些元素能够被列在一个表里（从而元素的数目与正整数的数目一样多），我们就记作

```math
S = \{x_1,\, x_2,\, \ldots\},
```

并称 $S$ 是**可数无穷**的（`countably infinite`）。例如，所有偶数的集合可以写成 $\{0,\,2,\,-2,\,4,\,-4,\,\ldots\}$，它就是可数无穷的。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 如果把"可数无穷"和后面马上要讲的"不可数"放在一起看会更清楚。（`countably infinite`，可数无穷）指一个集合能与正整数一一对应，也就是说能排成一列。**不可数**（`uncountable`）则指不存在这样的列举。在 6.042J 离散数学的集合论中我们学过：有理数集 $\mathbb{Q}$ 是可数的（用康托的对角列举法就能全部列出来），而区间 $[0,1]$（从而整个 $\mathbb{R}$）是不可数的，其证明正是著名的**康托对角线论证**（`Cantor's diagonal argument`）。这正是"全部实数 $[0,1]$ 无法列成一张表"的根本原因。这个"可数 vs 不可数"的区分对概率极其重要：当样本空间可数时，我们可以只用单元素概率来刻画整个概率律（靠求和）；而当样本空间不可数时，我们就必须改用面积/积分来描述概率。请记住：$[0,1]$ 里的实数没有"一列",也不存在所谓的"下一个实数"。

> <span style="color:#7f8c8d;">BT §1.1, p.4</span>

另一种方式，我们可以考虑所有满足某个性质 $P$ 的 $x$ 所构成的集合，并把它记为

```math
\{x \mid x \text{ 满足 } P\}.
```

（其中的竖线"$\mid$"应读作"使得/满足"（`such that`）。）例如，偶数的集合可以写成 $\{k \mid k/2 \text{ 是整数}\}$。类似地，区间 $[0,1]$ 内所有标量 $x$ 的集合可以写成 $\{x \mid 0 \le x \le 1\}$。注意，后一个集合中的元素 $x$ 取遍一段连续的值域（`continuous range`），无法被写成一张表（其证明略述于章末习题）；这样的集合被称为**不可数**的（`uncountable`）。

若集合 $S$ 的每一个元素同时也是集合 $T$ 的元素，我们就说 $S$ 是 $T$ 的**子集**（`subset`），并记作 $S \subset T$ 或 $T \supset S$。若 $S \subset T$ 且 $T \subset S$，则这两个集合**相等**（`equal`），记作 $S = T$。我们还有必要引入一个**全集**（`universal set`），记作 $\Omega$，它包含在特定语境下可能令人感兴趣的所有对象。一旦用全集 $\Omega$ 规定了语境，我们就只考虑那些是 $\Omega$ 子集的集合 $S$。

### Set Operations（集合运算）

一个集合 $S$ 关于全集 $\Omega$ 的**补集**（`complement`）是指 $\Omega$ 中所有不属于 $S$ 的元素所构成的集合 $\{x \in \Omega \mid x \notin S\}$，记作 $S^c$。注意 $\Omega^c = \varnothing$。

两个集合 $S$ 与 $T$ 的**并集**（`union`）是指属于 $S$ 或属于 $T$（或同时属于两者）的所有元素构成的集合，记作 $S \cup T$。两个集合 $S$ 与 $T$ 的**交集**（`intersection`）是指同时属于 $S$ 与 $T$ 的所有元素构成的集合，记作 $S \cap T$。于是

```math
S \cup T = \{x \mid x \in S \text{ 或 } x \in T\},
```

且

```math
S \cap T = \{x \mid x \in S \text{ 且 } x \in T\}.
```

在某些情形下，我们需要考虑多个、甚至无穷多个集合的并集或交集，其定义是显而易见的。例如，若对每个正整数 $n$ 给定一个集合 $S_n$，那么

```math
\bigcup_{n=1}^{\infty} S_n \;=\; S_1 \cup S_2 \cup \cdots \;=\; \{x \mid x \in S_n \text{ 对某个 } n\},
```

以及

```math
\bigcap_{n=1}^{\infty} S_n \;=\; S_1 \cap S_2 \cap \cdots \;=\; \{x \mid x \in S_n \text{ 对所有 } n\}.
```

若两个集合的交为空，则称它们**不相交**（`disjoint`）。更一般地，若干集合被称为不相交的，是指其中任意两个都不含公共元素。若一个集合的族中成员两两不相交，且它们的并集正好是 $S$，则称该集合族是 $S$ 的一个**划分**（`partition`）。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> "划分"这个词值得和其它学科对一下暗号。$S$ 的一个划分，就是一组两两不相交、并起来恰好等于 $S$ 的子集，通常称为一块一块（`blocks`）。这恰好是 6.042J 离散数学集合论里**等价关系**（`equivalence relation`）的"表兄弟"：一个集合上的等价关系会把该集合分割成一堆互不重叠的等价类，而反过来，任何一组划分也能诱导出一个等价关系（"属于同一块"）。两者是一一对应的。教材这里用划分来思考"n 个事件两两不相交且合起来覆盖整个样本空间"，正是后面概率律中加法公理处理的场景——把整个"单位质量"拆成互不重叠的几块来分配。记住这个"划分 ↔ 等价类"的对偶关系，会贯穿概率与组合计数始终。

> <span style="color:#7f8c8d;">BT §1.1, p.4</span>

**标量**（`scalars`），即实数（`real numbers`）的集合记为 $\mathbb{R}$。所有标量二元组 $x = (x_1, x_2)$ 的集合记为 $\mathbb{R}^2$（即二维平面），三元组 $x = (x_1, x_2, x_3)$ 的集合记为 $\mathbb{R}^3$（即三维空间）。这类无穷集合里面的集合运算，用文氏图（`Venn diagrams`）最容易直观理解，如图 1.1 所示。

**Figure 1.1（图 1.1）：** 集合运算的图解示例：(a) 阴影区域是 $S \cup T$。(b) 阴影区域是 $S \cap T$。(c) 阴影区域是…（图稿，略）。(d) 阴影区域是 $S$ 的补集 $S^c$。(e) 集合 $S$、$T$、$U$ 两两不相交。(f) 集合 $S$、$T$、$U$ 构成了 $\Omega$ 的一个划分。

下面这些集合代数（`set algebra`）恒等式是很有用的，它们都遵循同一构造逻辑，都可以通过数集元素（`element` 论证，element chasing）来证明：

```math
\begin{aligned}
S \cup (T \cup U) &= (S \cup T) \cup U, &\qquad S \cap (T \cap U) &= (S \cap T) \cap U,\\
S \cup (T \cap U) &= (S \cup T) \cap (S \cup U), &\qquad S \cap (T \cup U) &= (S \cap T) \cup (S \cap U),\\
(S \cup T)^c &= S^c \cap T^c, &\qquad (S \cap T)^c &= S^c \cup T^c,\\
S \cup \varnothing &= S, &\qquad S \cap \varnothing &= \varnothing,\\
S \cup \Omega &= \Omega, &\qquad S \cap \Omega &= S.
\end{aligned}
```

上面第二行即著名的**德摩根律**（`De Morgan's laws`）。德摩根律可以推广到任意多个集合：例如，对集合族 $\{S_n\}$，有

```math
\left(\bigcup_{n} S_n \right)^c \;=\; \bigcap_n S_n^{\,c}, \qquad \left(\bigcap_n S_n \right)^c \;=\; \bigcup_n S_n^{\,c}.
```

## <span style="color:#2471a3;">**[proof] 德摩根律（推广形式）的证明（`Proof`）**</span>

为证明第一个等式，我们取出任意一个元素 $x$，证明它属于 $\left(\bigcup_{n} S_n\right)^c$ 当且仅当它属于 $\bigcap_n S_n^{\,c}$。首先设 $x \in \left(\bigcup_{n} S_n\right)^c$。由补集定义，$x \notin \bigcup_n S_n$；即对每一个 $n$，都有 $x \notin S_n$。因此 $x$ 属于每个 $S_n$ 的补集，从而 $x \in \bigcap_n S_n^{\,c}$。这就证明了左边包含于右边。反之，若 $x \in \bigcap_n S_n^{\,c}$，则对每个 $n$ 都有 $x \notin S_n$，因而 $x$ 不属于并集 $\bigcup_n S_n$，故 $x \in \left(\bigcup_n S_n\right)^c$。两边互相包含，所以两集合相等。第二个等式的论证完全对称。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 上面那段证明的核心手法叫**元素追逐法（element chasing）**，可沉淀成一套固定步骤：证 $A=B$ → 任取任意元素 $x\in A$，沿补、交、并的逐元素定义一路推出 $x\in B$，得 $A\subset B$；再完全对称地证反向包含，两个方向都成立即可断言相等。这正是你在 6.042J 里反复练过的默认起手式，它不是特例而是集合论证明的通用模板。更有价值的是看清集合代数与数理逻辑的同构：并 $\cup\leftrightarrow\lor$、交 $\cap\leftrightarrow\land$、补 $^c\leftrightarrow\neg$，于是德摩根律 $(S\cup T)^c=S^c\cap T^c$ 不过是逻辑版 $\neg(P\lor Q)\Leftrightarrow\neg P\land\neg Q$ 换了件集合外衣。把这张「集合↔逻辑」的指纹焊进记忆后，处理概率里「至少一个发生」（$\cup$）与「一个都不发生」（$\cap^c$ 的全非）这类互补语义时，能一眼看出该调哪条规则。卡点提示：元素追逐法的命门在「任取」二字——必须对**任意**元素论证，举几个例子验证不算数。

> <span style="color:#7f8c8d;">BT §1.1, p.5–6</span>

## <span style="color:#c0392b;">1.2 Probabilistic Models（概率模型）</span>

> <span style="color:#00838f;">**[definition] 样本空间与事件（`sample space` and `event`）**</span>
> **Every probabilistic model（每一个概率模型）都包含一个底层过程，称为试验（`experiment`，即进行一次试验），它必定会从若干个可能结果中恰好产生其中一个。** 所有可能结果的集合称为**样本空间**（`sample space`），记作 $\Omega$。样本空间的一个子集——也就是一组可能结果——称为一个**事件**（`event`）。**Figure 1.2（图 1.2）** 展示了概率模型的主要成分。每个概率模型还配有一个**概率律**（`probability law`），它对样本空间中的每个结果赋予一个概率。

> <span style="color:#7f8c8d;">BT §1.2, p.6</span>

对试验的构成没有限制。例如，它可以是抛一次硬币，也可以是抛三次硬币，还可以是一串无穷多次抛掷。但重要的是要注意：在我们对概率模型的表述中，**只有一个试验**。因此，抛三次硬币构成的是一个试验，而不是三个试验。

一个试验的样本空间可以由有限个或无穷多个可能结果组成。有限样本空间在概念上和数学上都更简单。不过，具有无穷多个元素的样本空间也非常常见。举个例，考虑向一个方形靶子掷飞镖，并把落点视为结果。

### Choosing an Appropriate Sample Space（选择恰当的样本空间）

不论结果数量多少，样本空间中的各个元素应当彼此**可区分**且**互斥**（`distinct and mutually exclusive`），这样当试验做完时，结果是唯一的。例如，与掷骰子相对应的样本空间不能既含有"$1$ 或 $3$"这一可能结果，又含有"$1$ 或 $4$"这另一个可能结果。若真如此，那么当掷出的结果是 $1$ 时，我们便无法指定唯一的结果了。

同一物理情境可以根据我们所关心的问题类型，用多种不同方式建立模型。一般来说，为一个概率模型选定的样本空间必须是**完全穷尽**的（`collectively exhaustive`），意思是：无论试验中发生什么，我们总能得到样本空间中已包含的一个结果。此外，样本空间应包含足够的细节，以区分建模者感兴趣的所有结果，同时避免无关的细节。

## <span style="color:#2471a3;">**[example] 例 1.1（两个备选的游戏）**</span>

考虑两个备选的游戏，两者都涉及连续十次抛硬币：

- **游戏 1（Game 1）：** 每出现一次正面，我们得到 \$1。
- **游戏 2（Game 2）：** 在第一次出现正面（含第一次）之前，每次抛硬币得到 \$1；之后,在第二次出现正面（含）之前，每次抛硬币得到 \$2。更一般地，每次出现正面，每次抛掷的美元数额就翻倍。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这个例子想让你抓住"建模者的意图决定样本空间"这件事。同一个物理过程（抛十次硬币），游戏 1 只关心"共出现几次正面"，游戏 2 却关心"每个正面的先后位置"，所以两者的样本空间要画得不一样。这正是上文中"样本空间要足够细致以区分感兴趣的结果，又别掺杂无关细节"的具体执行。选择样本空间不是机械的,它取决于你接下来要问什么问题、要算哪个量。这一点很关键，因为概率律（`probability law`）总是定义在某个选定的样本空间上的；样本空间选粗了，有些你关心的量就无从区分，选细了又会使计数和运算变肿。做概率题的第一步永远是"先把样本空间写清楚"。

> <span style="color:#7f8c8d;">BT §1.2, p.7</span>

> *脚注（footnote）：* 任何一组可能结果——包括整个样本空间 $\Omega$ 及其补集即空集 $\varnothing$——都可能够格作为一个事件。不过严格来说，有些集合必须被排除在外。特别是，当处理涉及不可数无穷样本空间的概率模型时，存在某些非同寻常的子集，无法为它们赋予有意义的概率。这是一个复杂的技巧性问题，牵涉到测度论（`measure theory`）的数学。幸运的是，这类病态子集既不会出现在本书所考虑的问题中，在实际中也不会出现，因此这个问题可以放心地忽略。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 此处脚注很值得停下来读。它承认：在数学上，"任意子集都应有概率"是行不通的，会碰到一些"病态"集合。这背后是**测度论**（`measure theory`）——你在 100B 实分析里会系统遇到的主题。那里的核心抽象正是"集合的长度/面积"到底怎么严谨地定义，以及为什么并非每个子集都"可测"。好消息是，对你在本课程和实际工程里遇到的所有"正常"集合（区间、三角形、平行四边形、可数并……），面积/概率都有定义，所以你可以安全地在直观层面使用面积思想，不必现在非要钻进测度论的细节。等 100B 学到勒贝格测度时，你会回头看这个脚注并会心一笑。

> <span style="color:#7f8c8d;">BT §1.2, p.7, fn</span>

对于一个由两次抛掷四面色子（4-sided die）构成的试验，其样本空间可以用二维表格（a 2-dimensional grid）来表示，如图 1.3 左侧所示。所有可能结果都是形如 $(i, j)$ 的有序对，其中 $i$ 是第一次的结果，$j$ 是第二次的结果。这些结果也可以由右侧的树（`tree`）来描述。**Figure 1.3（图 1.3）：** 进行了两次的四面色子实验的样本空间。该树的根对应实验开始整棵树，可以用这样一种方式刻画结果的进程：每个结果对应于树的一片叶子（`leaf`），并与从根到该叶子的路径相关联。左图中阴影区域对应事件 $\{(1,4),\,(2,4),\,(3,4),\,(4,4)\}$，即直到所有可能的路径部"第二次结果是 4"这一事件。这个同一事件也可以由右图中标亮的一组叶子来描述。另请注意，树的每一个节点都可以用一个事件来标识——即从该节点出发的所有下游叶子所构成的集合。例如，标记为"第一次结果为 1"的那个节点，可以对应事件 $\{(1,1),\,(1,2),\,(1,3),\,(1,4)\}$。

一旦我们把实验与样本空间 $\Omega$ 紧紧关联起来，概率模型就基本定形了；接下来需要引入概率律这个成分——它在先行小节中已被完整刻画。

### Probability Laws（概率律）

> <span style="color:#00838f;">**[definition] 概率律（`probability law`）**</span>
> 概率律（`probability law`）规定了任何结果或者任何一组可能结果（我们在前面曾称其为事件，`event`）的"可能性"。更精确地说，**概率律会给每个事件 $A$ 指派一个数 $P(A)$，称为事件 $A$ 的概率，并满足下面三条公理。**

#### <span style="color:#00838f;">**[definition] 概率公理（`Probability Axioms`）**</span>

1. **(非负性，`Nonnegativity`)** 对每个事件 $A$，有 $P(A) \ge 0$。
2. **(可加性，`Additivity`)** 若 $A$ 和 $B$ 是两个不相交的事件，则它们并集的概率满足
   ```math
P(A \cup B) = P(A) + P(B).
```
   更一般地，若样本空间有无穷多个元素，且 $A_1,\, A_2,\, \ldots$ 是一列不相交的事件，则它们并集的概率满足
   ```math
P\left(\bigcup_{n} A_n\right) = \sum_{n} P(A_n).
```
3. **(归一化，`Normalization`)** 整个样本空间 $\Omega$ 的概率等于 $1$，即 $P(\Omega) = 1$。

为了直观地理解概率律，想象有一单位质量的物体被"摊开"在样本空间上。那么 $P(A)$ 就简单地是分配给 $A$ 的所有元素的总体质量。借助这个类比,可加性公理变得非常直观：一列不相交事件的总质量，等于各自质量之和。

概率的另一种更具体的解释是**相对频率**（`relative frequencies`）：像 $P(A) = 2/3$ 这样的陈述，常常表达这样一种信念——在大量次重复试验中，事件 $A$ 出现的比例约为三分之二。这种解释虽然并不总是恰当，但有时能帮助我们的直觉理解。在第五章研究极限定理时，我们会再回到这个解释。

概率律还有许多自然的性质，之所以没有把它们写进上面的公理，仅仅是因为它们可由公理推出来。例如，注意归一化公理与可加性公理合起来蕴含

```math
1 = P(\Omega) = P(\Omega \cup \varnothing) = P(\Omega) + P(\varnothing) = 1 + P(\varnothing),
```

这就表明**空事件的概率为 0**：$P(\varnothing) = 0$。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 注意这副公理化结构的骨架：概率被定义成一个「集合到数」的函数，只受非负、不相交可加、总归一律三条公理约束，其余性质（$P(\varnothing)=0$、单调性、容斥公式）全部靠逻辑从公理推出，而不必逐条单列为公理。这正是你在 6.042J 接触过的公理化风格：给极小的公理集合，再系统性演绎出全部结论。尤其要盯住「可加性」条目的形态——它先对「至多有限个」不相交集之和成立，又对一列无穷多个不相交集也对，后者叫**可数可加性（countable additivity）**，并非所有测度都满足，而概率律恰恰需要它。当样本空间不可数、无法逐点求和定义概率时，可加性公理就把「把摊开的单位质量切成小份再求和」与积分自然接上了轨。卡点：「可数可加性」里的「可数」精确对应 6.042J 的可数集概念，不可数情形必须换积分语言，切勿以为可加性自动对任意不可数并集成立。

> <span style="color:#7f8c8d;">BT §1.2, p.9</span>

再举一个例子，考虑三个不相交的事件 $A_1$、$A_2$ 和 $A_3$。我们可以反复地对两个不相交事件使用可加性公理，得到

```math
P(A_1 \cup A_2 \cup A_3) = P\big(A_1 \cup (A_2 \cup A_3)\big) = P(A_1) + P(A_2 \cup A_3) = P(A_1) + P(A_2) + P(A_3).
```

类似地继续做下去，我们得到：**有限多个不相交事件并集的概率，总是等于这些事件概率之和。** 更多的此类性质我们稍后再讲。

### Discrete Models（离散模型）

下面举例说明如何从关于某一模型的常识性假设出发，构造一个概率律。

## <span style="color:#2471a3;">**[example] 例 1.2（抛掷单枚硬币）**</span>

考虑一个抛掷单枚硬币的试验。有两个可能结果：正面 $H$ 和反面 $T$。其样本空间是 $\Omega = \{H,\,T\}$，事件共有

```math
\{H,\,T\},\quad \{H\},\quad \{T\},\quad \varnothing.
```

若硬币是均匀的，即若我们相信正反面"等可能"，那么就应当给两个可能结果指派相等的概率，并规定 $P(\{H\}) = P(\{T\}) = 0.5$。可加性公理蕴含 $P(\{H,\,T\}) = P(\{H\}) + P(\{T\}) = 1$，这与归一化公理相容。于是概率律由下式给出：

```math
P(\{H,\,T\}) = 1,\qquad P(\{H\}) = 0.5,\qquad P(\{T\}) = 0.5,\qquad P(\varnothing) = 0,
```

并且它满足全部三条公理。

再看一个涉及抛掷三次硬币的试验。此时结果将是一个由正面或反面组成的三位串。样本空间是

```math
\Omega = \{HHH,\, HHT,\, HTH,\, HTT,\, THH,\, THT,\, TTH,\, TTT\}.
```

我们假定每个可能结果都有相同的概率 $1/8$。让我们构造一个满足三条公理的概率律。作为示例，考虑事件

```math
A = \{\text{恰好出现 2 次正面}\} = \{HHT,\, HTH,\, THH\}.
```

用可加性，$A$ 的概率等于其各元素概率之和：

```math
P(\{HHT,\,HTH,\,THH\}) = P(\{HHT\}) + P(\{HTH\}) + P(\{THH\}) = \frac{1}{8} + \frac{1}{8} + \frac{1}{8} = \frac{3}{8}.
```

类似地，任何事件的概率都等于 $1/8$ 乘以该事件所含的可能结果个数。这就定义了一个满足三条公理的概率律。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这个三次抛硬币例子是**离散均匀模型（discrete uniform model）**的第一次正式亮相：当所有结果等可能时，任何事件的概率 =（事件所含结果个数）÷（结果总数），本质就是「数数再除以总数」。它把概率计算退化成你在 6.042J 学的计数（counting）——乘法原理、排列组合——在概率里的直接落地场景，所以遇到「随机、等可能」的题目，十有八九会回到数数，把组合底子打牢非常划算。同时它悄悄演示了「单元素概率唯一确定概率律」：只要给定每个结果 $1/8$，任意事件的概率就由可加性公理自动拼出。这里还能预埋一条对比线索：有限等可能的样本空间靠计数，而后面不可数样本空间（如区间 $[0,1]$）必须改靠积分——同一套公理、两种不同的「量度」手段。卡点提示：用 $1/8$ 乘「事件元素个数」是均匀假设的直接推论，不要把它过度泛化成「所有概率题天生均分」。

> <span style="color:#7f8c8d;">BT §1.2, p.10</span>

通过使用可加性公理并概括上面例子中的推理，我们得到下面的结论。

> <span style="color:#00838f;">**[definition] 离散概率律（`Discrete Probability Law`）**</span>
> 若样本空间由有限多个可能结果组成，那么概率律就由那些"单元素事件"（即由单个结果构成的事件）的概率唯一确定。特别地，任何事件 $\{s_1,\, s_2,\, \ldots,\, s_n\}$ 的概率等于其各元素概率之和：

```math
P\big(\{s_1,\, s_2,\, \ldots,\, s_n\}\big) = P(s_1) + P(s_2) + \cdots + P(s_n).
```

注意，这里我们用较简略的记号 $P(s_i)$ 来表示单元素事件 $\{s_i\}$ 的概率，而不是更精确的 $P(\{s_i\})$。这一约定将在本书其余部分一直沿用。

在特殊情形下，若各概率 $P(s_1),\, \ldots,\, P(s_n)$ 全部相同（由归一化公理可知必然等于 $1/n$），我们就得到如下结论。

> <span style="color:#00838f;">**[definition] 离散均匀概率律（`Discrete Uniform Probability Law`）**</span>
> 若样本空间由 $n$ 个等可能的（即所有单元素事件概率都相同的）可能结果组成，则任何事件 $A$ 的概率为

```math
P(A) = \frac{\text{事件 } A \text{ 的元素个数}}{n}.
```

下面我们再给出几个样本空间与概率律的例子。

## <span style="color:#2471a3;">**[example] 例 1.3（同时掷一对四面色子）**</span>

考虑同时掷一对四面色子的试验（cf. 图 1.4）。我们假定色子是均匀的，并把这个假设解释为：十六个可能结果中的每一个——即有序对 $(i, j)$，其中 $i,\,j = 1,\,2,\,3,\,4$——都具有相同的概率 $1/16$。要计算一个事件的概率，我们必须数出该事件所含的元素个数，再除以 $16$（可能结果的总数）。

**Figure 1.4（图 1.4）：** 掷一对四面色子的样本空间中的各种事件，及其按离散均匀概率律（`discrete uniform law`）计算出的概率。例如，事件（sum 之和为偶数）含有 8 个有序对，因而概率为 $8/16 = 1/2$；事件（一对方恰好某个结果）……此类计数问题可利用图 1.4 的网格逐一数出（受扫描件图注残缺影响，细节以原书为准）。凡是"枚举十六个等可能结果再计数"的事件，其概率都用统一方式计算。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这里是"离散均匀 + 计数"的标准流水线:先认清样本空间里共有多少个等可能结果（这里有 $16$ 个，因为 $4\times4$），再把目标事件翻译成"满足某条件的有序对集合"，数出个数，最后用公式 $P = \text{个数} \div 16$。需要注意"有序对"（有序 vs 无序）的细节——$(1,2)$ 和 $(2,1)$ 是两个不同的结果，因为它们分别对应"第一次 $1$ 第二次 $2$"与"第一次 $2$ 第二次 $1$"。如果你在 6.042J 学过计数中的"重数/顺序"（`ordered vs unordered`），这里就是它的概率版应用。图中所列"和为偶数""一次性某个结果"这类事件，都可以用满足约束的有序对个数直接数出。把这种"建模→枚举→计数→相除"的套路练熟，是本例最该带走的东西。

> <span style="color:#7f8c8d;">BT §1.2, p.11–12</span>

### Continuous Models（连续模型）

接下来我们考虑样本空间不可数、从而无法用"逐结果计数"来定义概率律的情形。

## <span style="color:#2471a3;">**[example] 例 1.4（单位区间连续模型）**</span>

考虑连续样本空间为整个单位区间 $[0,1]$ 的概率模型：对 $[0,1]$ 中的任意子集 $S$（在通常的微积分意义下的"正常"集合，`nice` sets），我们把其概率定义为 $S$ 的**长度**（即积分 $\int_S dx$）。例如，若 $S$ 是长度为 $1/4$ 的区间 $[1/4,\, 1/2]$，则 $P(S) = 1/4$。归一化公理要求 $P(\Omega) = P([0,1]) = \int_0^1 dx = 1$；空集的长度为零，于是 $P(\varnothing)=0$，这与归一化公理相容。这样定义的（连续）概率律满足三条公理。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这里把"概率 = 长度/面积的积分"正式摆上台面：对不可数样本空间，不再逐点计数，而是用积分 $\int_S dx$ 量度集合大小，这就是**例 1.4** 的核心。注意归一化公理如何逼出"整个空间总长为 1"，而空集长度为零又自动满足非负加可加——这提醒我们，连续概率律的本质是在不可数候选上分配一个"可加、非负、总质量为 1"的度量。这正是你 100B 实分析里"集合长度 / 测度"概念的直观雏形，届时你会用 $\sigma$-代数、可测集、勒贝格积分等更严格的语言重写这段话，现阶段先把"面积兑换成概率"的几何直觉立起来。一个实操武器是"总面积 − 补区域面积"：像下一例罗密欧与朱丽叶那个阴影带（总面积 1 减去两个直角边为 $3/4$ 的三角形），直接算带形面积往往比拆两段积分省心得多。卡点：课本只认"正常（`nice`）"集合可测，病态子集要等实分析才能处理，现阶段按几何直觉放心用即可。

> <span style="color:#7f8c8d;">BT §1.2, p.13</span>
## <span style="color:#2471a3;">**[example] 例 1.5（罗密欧与朱丽叶）**</span>

罗密欧与朱丽叶（`Romeo and Juliet`）约定在某处相会，但两人到达的时间都是随机的——我们把一小时的约会期等比例压到单位区间 $[0,1]$ 上。设 $x$ 为罗密欧到达的时刻，$y$ 为朱丽叶到达的时刻，则样本空间 $\Omega = [0,1]\times[0,1]$，即平面上的整个单位正方形，其中每个点 $(x,y)$ 都是等可能的（连续均匀，面积即概率）。"等可能"在这里被解释为：$\Omega$ 的任一子集的概率等于其面积，于是任一"正常"事件的概率介于 0 与 1 之间，满足三条概率公理。**图 1.5** 刻画的是"罗密欧与朱丽叶将在 15 分钟内到达对方的时刻"这一事件。该事件即图中阴影区域，其概率计算为 $7/16$。

**Figure 1.5（图 1.5）：** 罗密欧与朱丽叶在 15 分钟内（相互间隔）到达的事件 $M$。$M = \{(x,y) \mid |x-y| \le \tfrac14\}$，在图中以阴影标出。$M$ 的面积等于 1 减去两个非阴影（直角三角形）区域之和：两个阴影外的三角形各自的"长度"均为 $\tfrac34$，所以

```math
P(M) \;=\; 1 - 2 \cdot \tfrac12 \bigl(\tfrac34\bigr)\bigl(\tfrac34\bigr) \;=\; 1 - \tfrac{9}{16} \;=\; \tfrac{7}{16}.
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这个例子是全书第一次出现"不可数、靠面积算概率"的样本空间，它是本小节"连续模型"的核心演练。关键转折在于：当结果无穷多、而且连续（不可数）时，"逐一求和"彻底失效——你不能把 $[0,1]\times[0,1]$ 里的点一个个列出来再把概率加总，于是概率律改由"区域的面积/长度"来定义。归一化公理 $P(\Omega)=1$ 此时读作"整个单位正方形的面积为 1"，而"某个事件发生"则译成"落点落在对应区域内"，概率 = 区域面积。这正是微积分积分（以及你在 100B 实分析中要系统学习的"集合的长度 $\leftrightarrow$ 积分"）在概率里的直接化身。看懂阴影也是一个好训练：它由一条"带子"构成——带子上方与下方各缺一个直角边为 $\tfrac34$ 的直角三角形，每个三角形面积为 $\tfrac12\cdot\tfrac34\cdot\tfrac34=\tfrac9{32}$，两个合计 $\tfrac9{16}$，故 $M$ 的面积 $=1-\tfrac9{16}=\tfrac7{16}$。多练这种"整块总面积减掉补区域"的技巧，是处理连续概率的拿手武器。

> <span style="color:#7f8c8d;">BT §1.2, p.13</span>


---

### Properties of Probability Laws（概率律的性质）

概率律具有若干可以由公理推出的性质，其中一些归纳如下。

> <span style="color:#00838f;">**[definition] 概率律的一些性质（`Some Properties of Probability Laws`）**</span>
> 设一个概率律，并令 $A$、$B$、$C$ 为事件。

- (a) 若 $A \subset B$，则 $P(A) \le P(B)$。
- (b) $P(A\cup B) = P(A) + P(B) - P(A\cap B)$。
- (c) $P(A\cup B) \le P(A) + P(B)$。
- (d) $P(A\cup B \cup C) = P(A) + P(A^c \cap B) + P(A^c \cap B^c \cap C)$。

这些性质及其它类似性质，都可以用文氏图（`Venn diagrams`）直观地加以展示和验证，如图 1.6 所示。注意性质 (c) 可推广为

```math
P(A_1 \cup A_2 \cup \cdots \cup A_n) \;\le\; \sum_{i=1}^{n} P(A_i).
```

要看出这一点，我们把性质 (c) 分别应用到集合组 $A_1$ 与 $A_2 \cup \cdots \cup A_n$、$A_2$ 与 $A_3 \cup \cdots \cup A_n$ 上，……，如此继续，最后把所有不等式相加。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 课堂上你常把这个"并集的概率不超过各概率之和"的推广叫**并事件界 / 布尔不等式**（`union bound` / subadditivity）。它非常朴素却极有用：哪怕一堆事件的概率都只略大于零，并集的概率也绝不会超过它们的和（而当它们彼此不相交时等号成立，即回到可加性公理）。原因在于相交的部分不会让并集变大，只会让"相加"重复计数，故求和总是并集概率的上界。你在 100B 分析里遇见的"次可加性"（`subadditivity`）思想，与此同源，而它在后续估计"至少一个坏事件发生"的概率时几乎是每个概率题架的默认首招。把这条性质记成"和之内，且只在不相交时取等号"，用它时就不会心慌。

> <span style="color:#7f8c8d;">BT §1.2, p.14</span>

---

### Models and Reality（模型与现实）

概率论的框架可用于分析各种物理情境中的不确定性。典型地，这涉及两个不同阶段：

- (a) **第一阶段**，我们在一个恰当定义的样本空间上指定一个概率律，从而构造出一个概率模型。在这一步除了要求概率律符合前面三条公理之外，没有刻板的规则来指导。理性的人可能会就"哪个模型最能刻画现实"产生分歧。在许多情况下，人们甚至可能愿意使用某种意义上"不正确"的模型，如果它比"正确"的模型更简单，或者能带来更易处理的运算。这也与科学中普遍的做法相吻合……

- (b) **第二阶段**，由该模型推导出概率论断。一个模型的选择往往是在准确度（`accuracy`）、简洁性（`simplicity`）与可处理性（`tractability`）之间的折中；某些情况下，模型是依据统计（`statistical`）考虑来选定的，而这会牵涉到具体的检验方法，这套方法将在 §9.3 中给出。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 这段话表面在讲建模方法论，实则在提醒你概率是一门"给定模型即确定结果"的演绎学科：只要模型（样本空间 + 概率律）定下来，往后算出的每个概率都是硬邦邦的数学结论，与模型本身的"对错/好坏"无关。模型选择往往是一个工程判断（`judgment` 技巧——示例不必尽善尽美，够用、可算、可解就行）。这个立场和我们后面讲"如何选取样本空间、怎么把现实命题翻译成事件"一脉相承。而可靠的模型判断依赖的正是前面那些基本功——正确地构造样本空间、正确地把"至少一个 / 恰好一个 / 都在"这类语义转成 $\cup$、$\cap$、$^c$、然后正确地应用公理与恒等式。把"模型即约定"与"给定模型后严格演算"这两层分开，是读懂后续大量例子的关键。

> <span style="color:#7f8c8d;">BT §1.2, p.14（模型与现实，后续内容随下一批次）</span>

---

batch_C.md
> <span style="color:#7f8c8d;">**batch_C**（PDF 第 25–36 页）：§1.2 Probabilistic Models（概率模型）末尾 + §1.3 Conditional Probability（条件概率）</span>

# <span style="color:#c0392b;">1.2 概率模型 Probabilistic Models（续）</span>

……一个模型的选择，往往是在准确度（accuracy）、简洁性（simplicity）与可处理性（tractability）之间的折中。某些情况下，模型是依据统计（statistical）考虑来选定的，而这会牵涉到具体的检验方法，这套方法我们将在 §9.3 中给出。

## <span style="color:#c0392b;">概率律性质的直观验证 Properties of Probability Laws（用 Venn 图验证）</span>

我们可以用 **Venn 图（Venn diagram）** 来直观地展示并验证概率律的若干基本性质。考虑如下三种情形（示意图）：

(a) 若 $A\subset B$，则 $B$ 正是两个互不相交（disjoint）事件 $A$ 与 $A^c\cap B$ 之并，于是由可加性公理（additivity axiom）

```math
P(B) = P(A) + P(A^c\cap B),
```

其中由非负性公理（nonnegativity axiom）知 $P(A^c\cap B)\ge 0$，故

```math
P(B)\ge P(A),
```

这就验证了（单调性）性质（a）。

(b) 从图 (b) 出发，我们可以把 $A\cup B$ 与 $B$ 分别写成互不相交事件的并：

```math
A\cup B = A\cup (A^c\cap B),\qquad B = (A\cap B)\cup(A^c\cap B).
```

两次利用可加性公理，即得

```math
P(A\cup B) = P(A) + P(A^c\cap B),\qquad
P(B) = P(A\cap B) + P(A^c\cap B).
```

由第一式与第二式相减（消去相同的 $P(A^c\cap B)$ 项），得到

```math
P(A\cup B) = P(A) + P(B) - P(A\cap B),
```

即概率律性质（b）。再借助 $P(A\cap B)\ge 0$ 这一事实，可得

```math
P(A\cup B)\le P(A) + P(B),
```

即概率律性质（c），也就是 **可数次可加性（subadditivity）**，亦称"并的不等式 / 联合界"。

(c) 观察图 (c) 可以看到，事件 $A\cup B\cup C$ 可以写成三个互不相交事件之并：

```math
A\cup B\cup C = A\ \cup\ (A^c\cap B)\ \cup\ (A^c\cap B^c\cap C),
```

这正是可加性公理（对三个互斥事件推广）的自然应用。

> <span style="color:#1e8449;">**[note] Note（译者注）：**</span> 注意这里 $P(A\cup B)\le P(A)+P(B)$（并事件上界，Union Bound / Boole 不等式）是从「有限可加性 + 非负性」两条公理**推出来**的定理，而非新公理——这正是公理化结构给你的红利：给极少公理，再用纯逻辑把有用性质炼出来。它与「真正的可数可加性」（对一列无穷多互斥事件，并的概率等于各概率之和）是两回事，后者才是单独一条公理，且依赖 6.042J 的可数集概念。Union Bound 的直觉核心是：相交重合的部分让「直接相加」重复计数，所以求和总是并集概率的**上界**，只有互斥时才取等号（回到可加性公理）。它是算法分析里最常用的工具：你不知道某个坏事件的精确概率，但能逐条界住每个「小坏事件」，再累加得到一个安全的总界，这正是你 6.006/CLRS 里典型的分治式估计。卡点：CSAPP 里哈希表「某个桶元素过多」的概率估计，走的正是用 Union Bound 对多个小坏事件取并的传统套路，别把它和容斥公式混淆——这里是上界、容斥是精确值。

> <span style="color:#7f8c8d;">BT §1.2, p.14–15</span>

## <span style="color:#c0392b;">模型必须被完整指定：Bertrand 悖论</span>

在实际建模中，我们始终在一个**完全指定（fully specified）**的概率模型内部进行推理：样本空间 $\Omega$、事件类与概率律 $P$ 一经给出，任意事件的概率就由可加性公理**唯一地**确定下来，可以据此推导出各种概率与性质。尽管公理本身没有规定如何为具体问题选择概率律，模型一旦定下来，内部就不再有含糊（ambiguous）的空间；全部剩下的工作，只是**利用这套规则做计算（calculation）**而已。

不过，选择概率律这一步本身，却可能暗藏陷阱。一个非常著名的例子由 **L. F. Bertrand 于 1889 年**提出，它有力地说明：选择概率模型的方式不同，可能导致彼此矛盾的结果。

**Bertrand 悖论（Bertrand's paradox）。** 考虑一个圆，以及圆内接的一个正三角形。问：随机选取的一条弦，其长度**大于**三角形边长的概率是多少？这里的答案取决于"随机选取（randomly chosen）"究竟是什么意思。图 (a)、(b) 所示的两种"随机取弦"方法，会得到**相互矛盾**的结果。

- **(a)** 取圆的一条半径，在其上随机选一点 $C$（$C$ 在该半径上的各位置**等可能**）。过 $C$ 作与该半径垂直的弦。由初等几何可知，半径与边 $AB$ 的交点恰为 $AB$ 的**中点**，即当且仅当 $C$ 落在半径的中点与圆心之间时，弦长才大于边。故所求概率为 $1/2$。
- **(b)** 在圆上取一点，例如顶点 $V$，过 $V$ 作圆的切线，再过 $V$ 作一条与该切线成随机角 $\phi$ 的直线（$\phi$ 的各取值等可能）。考虑此直线与圆相交所得到的弦。由初等几何可知，弦长大于边长的情形恰对应 $\phi$ 介于 $\pi/3$ 与 $2\pi/3$ 之间；又因 $\phi$ 取值于 $[0,\pi]$，故所求概率为 $(\frac{2\pi}{3}-\frac{\pi}{3})/\pi = 1/3$。

同一个问题、两种都看似"合理"的随机模型，却给出 $1/2$ 与 $1/3$ 两个不同答案。这告诉我们：**"随机"必须在一个明确指定的概率模型内部才有意义**；不把"随机选取"落实为具体的概率律，概率计算就无从谈起。

> <span style="color:#1e8449;">**[note] Note（译者注）：**</span> Bertrand 悖论（1889，L. F. Bertrand 提出）的教训在方法论层面而非数学层面：概率不是「凭空属于一条弦」的固有属性，而是**某个明确指定的模型**赋予它的量。同一物理对象放进两个都看似自然的随机模型，分别得到 $1/2$ 与 $1/3$——二者并不矛盾，因为它们在说两个不同模型里的事。根源在于「随机选取」这四个字没被翻译成具体的概率律：方法 (a) 在半径上均匀取点，方法 (b) 在角度上均匀取角，均匀的标准不同，弦长的分布自然不同；这在连续情形尤其尖锐，因为「均匀」没有先在的标准，不似有限等可能那般自然唯一。这与你学 6.042J 时强调的「集合/关系必须显式定义才有意义」一脉相承，也为后面连续随机变量「密度选得不当、结论会变」埋下伏笔。卡点：动手算任何连续概率前，先自问「我所谓随机，落在哪个样本空间、用什么度量」，否则答案无从谈起。

> <span style="color:#7f8c8d;">BT §1.2, p.16</span>

## <span style="color:#c0392b;">概率简史 A Brief History of Probability（历史注记）</span>

- **[约 1000 年以前]** 赌博游戏在古希腊和罗马就十分流行，但没有产生任何科学化的进展——一个可能的原因是当时希腊人的记数系统不利于做代数运算。基于可靠科学分析的概率论，要等到印度人与阿拉伯人在公元后第一个千年的后半叶发展出现代算术系统，再加上文艺复兴所激发的科学思潮洪流，才得以起步。
- **[16 世纪]** 意大利数学家 **吉罗拉莫·卡尔达诺（Girolamo Cardano）**——一位性情鲜明且颇受争议的人物——出版了第一本阐述掷骰子、玩纸牌等赌博游戏中正确概率计算方法的书。
- **[17 世纪]** **费马（Fermat）**与**帕斯卡（Pascal）**之间的书信往来，触及若干有趣的概率问题，推动了这个领域的进一步发展。
- **[18 世纪]** **雅各布·伯努利（Jacob Bernoulli）**研究反复抛硬币的问题，提出了第一条**大数定律（law of large numbers）**，为概率论的理论概念与经验事实之间架起桥梁。**丹尼尔·伯努利（Daniel Bernoulli）**、**莱布尼茨（Leibniz）**、**贝叶斯（Bayes）**与**拉格朗日（Lagrange）**等数学家都为概率论及其在现实现象分析中的应用作出了重要贡献。**棣莫弗（De Moivre）**引入了**正态分布（normal distribution）**，并证明了**中心极限定理（central limit theorem）**的第一种形式。
- **[19 世纪]** **拉普拉斯（Laplace）**出版了一部影响深远的著作，确立了概率论作为一门定量学科的重要性，书中包含许多原创贡献，其中包括中心极限定理的更具一般性的版本。**勒让德（Legendre）**与**高斯（Gauss）**借助最小二乘法（method of least squares）把概率论应用于天文预测，由此开辟了极其广阔的应用空间。**泊松（Poisson）**发表了一部影响广泛的著作，其中包含若干原创贡献，包括**泊松分布（Poisson distribution）**。【**切比雪夫（Chebyshev）**】及其学生**马尔可夫（Markov）**与**李雅普诺夫（Lyapunov）**研究极限定理，并提高了该领域的数学严密性标准。整个这一时期，概率论大体上被视为一门自然科学，其主要目标是解释物理现象；与此目标一致，概率主要被解释为"可重复实验中相对频率（relative frequency）的极限"。
- **[20 世纪]** 相对频率这一概念作为概率论的概念基础被弃置，取而代之的是由**柯尔莫哥洛夫（Kolmogorov）**引入、如今被普遍采用的**公理体系（axiomatic system）**。与其他数学分支一样，概率理论从公理出发的发展只依赖于逻辑正确性，而与它是否切合某个物理现象无关。尽管如此，概率论仍然在科学与工程中无所不在，因为它有能力描述与阐释现实世界中大多数类型的不确定现象。

> <span style="color:#7f8c8d;">BT §1.2, p.17（历史注记框）</span>

---

# <span style="color:#c0392b;">1.3 条件概率 Conditional Probability</span>

**条件概率（conditional probability）**为我们提供了一种基于**部分信息（partial information）**来推理试验结果的方法。我们心设的典型场景如下：

(a) 在一个连续两次掷骰子的试验中，被告知两次点数之和为 $9$。问第一次掷出的是 $6$ 的可能性有多大？

(b) 在一个猜词游戏中，单词的第一个字母是 t。第二个字母是 h 的可能性有多大？

(c) 假设某项医学检测结果为阴性，问某人患有某种疾病的可能性有多大？

(d) 雷达屏幕上出现一个光点。它对应一架飞机的可能性有多大？

更精确地说：给定一个试验及其相应的样本空间和概率律，假定我们知道试验结果落在某个给定事件 $B$ 之内。我们希望**量化**试验结果同时也属于另一个给定事件 $A$ 的可能性。于是，我们要构造一个新的概率律，使之纳入上述已知信息：对任意事件 $A$，这个概率律给出"在已知事件 $B$ 发生的前提下，$A$ 的条件概率"——

```math
P(A\mid B).
```

我们期望，对不同的事件 $A$，这些条件概率 $P(A\mid B)$ 能构成一个**合法的概率律（legitimate probability law）**，也就是满足三条概率公理。同时，条件概率还应与我们在重要特殊情形下的直觉相符，例如当试验的所有可能结果等可能时。举例来说，假设一枚公平骰子的六个可能结果都等可能。若我们被告知结果是偶数，那么就只剩下三个可能结果，即 $2,4,6$。这三个结果原本等可能，那么在上"结果是偶数"这一额外信息后它们仍应等可能。因此，合理地取

```math
P(\text{结果是 }6\mid \text{结果是偶数}) = \frac{1}{3}.
```

这个论证提示我们：当所有结果等可能时，条件概率的一个合适定义是

```math
P(A\mid B) = \frac{\text{集合 }A\cap B\text{ 的元素个数}}{\text{集合 }B\text{ 的元素个数}}.
```

把上面的论证推广，我们就引入如下的条件概率定义：

> <span style="color:#00838f;">**[definition] 条件概率的定义（Definition of Conditional Probability）:**</span> 对于任意两个事件 $A$ 与 $B$，

```math
P(A\mid B) = \frac{P(A\cap B)}{P(B)},
```

其中我们假设 $P(B)>0$；若被条件化的事件 $B$ 的概率为零，则条件概率无定义。用语言说：在 $B$ 的各元素的总概率之中，$P(A\mid B)$ 是分派给"同时也属于 $A$ 的那些可能结果"所占的**份额（fraction）**。

> <span style="color:#1e8449;">**[note] Note（译者注）：**</span> 条件概率的定义可以这样直观理解：已知 $B$ 发生，就把**整个样本空间"收缩"到 $B$** 上，然后问 $A\cap B$（即 $B$ 中同时又属于 $A$ 的部分）在整个 $B$ 里占多大比例。"份额 = $B$ 内命中 $A$ 的概率 ÷ $B$ 的总概率"，分母 $P(B)$ 起的就是**归一化（normalize）**作用——它把 $B$ 的总质量重新"拉到 $1$"。当所有结果等可能时，概率之比退化成**基数（count）之比**，即上面那个"元素个数之比"的公式。这个"收缩到已知事件 $B$、再重新归一化"的视角非常重要：后续你会看到，固定 $B$ 之后，$P(\cdot\mid B)$ 本身就是一个定义在 $B$ 这个"新宇宙"上的合法概率律（下面马上验证）。在 CSAPP 里做随机化算法分析时，你常常"已知某个阶段已经发生"（比如哈希表中某链表已非空），再用这种重新归一化的份额去估计下一步的概率，正是这条定义在工作。

> <span style="color:#7f8c8d;">BT §1.3, p.18</span>

## <span style="color:#c0392b;">条件概率给出一个概率律 Conditional Probabilities Specify a Probability Law</span>

对一个固定的事件 $B$，可以验证：条件概率 $P(A\mid B)$（作为 $A$ 的函数）构成一个满足三条公理的合法概率律。确实如此：

- **非负性（nonnegativity）**是显然的，因为概率律非负，且 $P(B)>0$。
- **归一化公理（normalization axiom）**：由于 $\Omega\cap B = B$，

```math
P(\Omega\mid B) = \frac{P(\Omega\cap B)}{P(B)} = \frac{P(B)}{P(B)} = 1.
```

- **可加性公理（additivity axiom）**：对任意两个互不相交的事件 $A_1$ 与 $A_2$，

```math
\begin{aligned}
P(A_1\cup A_2\mid B)
&= \frac{P\big((A_1\cup A_2)\cap B\big)}{P(B)}\\
&= \frac{P\big((A_1\cap B)\cup(A_2\cap B)\big)}{P(B)}\\
&= \frac{P(A_1\cap B) + P(A_2\cap B)}{P(B)}\\
&= \frac{P(A_1\cap B)}{P(B)} + \frac{P(A_2\cap B)}{P(B)}\\
&= P(A_1\mid B) + P(A_2\mid B),
\end{aligned}
```

其中第三个等号用到了"$A_1\cap B$ 与 $A_2\cap B$ 是互不相交的集合"这一事实以及（无条件）概率律的可加性公理。对**可数无穷多个**互不相交集合的论证，与此完全类似。

既然条件概率构成一个合法的概率律，那么概率律的一切**一般性质**对条件概率依然成立。例如，事实 $P(A\cup C)\le P(A)+P(C)$ 可以照搬到：

```math
P(A\cup C\mid B) \le P(A\mid B) + P(C\mid B).
```

再留意一点：由于 $P(B\mid B) = P(B)/P(B)=1$，全部条件概率质量都**集中在 $B$ 上**。因此我们不妨把 $B$ 之外的所有可能结果全部丢弃，把条件概率看作定义在**新宇宙 $B$** 上的一个概率律。

> <span style="color:#1e8449;">**[note] Note（译者注）：**</span> 上面这段是公理化验证的完整示范：先**猜测**「条件概率应满足三条公理」，再逐条验证并且真通过了——这正是你在 6.042J 公理化训练里反复见的节奏：给出一个合理定义，回头从公理框架内证明它合法，而非默认合法。验证可加性时用到了分配律 $(A_1\cup A_2)\cap B=(A_1\cap B)\cup(A_2\cap B)$，而 $A_1\cap B$ 与 $A_2\cap B$ 的不相交性继承自 $A_1,A_2$ 的不相交性——「集合代数 + 公理」在此配合得严丝合缝。对可数无穷多个互斥集的推广则依赖上批强调过的可数可加性公理。落到直觉：$P(\cdot\mid B)$ 就是一个定义在「新宇宙 $B$」上的合法概率律，因为全部质量压缩到 $B$ 上、$B$ 之外一概丢弃，故 $B$ 内部的可加性、容斥、Union Bound 全部照单全收。卡点：把 $\frac{P(A_1\cap B)+P(A_2\cap B)}{P(B)}$ 拆成两项 $P(A_1\mid B)+P(A_2\mid B)$ 时，分母 $P(B)$ 是公共的比例因子，每一步都要自问「这一步是哪个公理许可的」，正是这套自问训练让你后面不吃亏。

> <span style="color:#7f8c8d;">BT §1.3, p.19</span>

现在总结我们到目前为止的结论。

> <span style="color:#c0392b;">**[property] 条件概率的性质（Properties of Conditional Probability）:**</span>
>
> - 给定事件 $B$（$P(B)>0$）之下，事件 $A$ 的条件概率定义为

```math
P(A\mid B) = \frac{P(A\cap B)}{P(B)},
```

> 它规定了同一个样本空间 $\Omega$ 上的一个新的（条件）概率律。特别地，概率律的一切性质对条件概率律依然有效。
>
> - 条件概率也可看作定义在新宇宙 $B$ 上的概率律，因为全部条件概率质量都集中在 $B$ 上。
>
> - 若可能的结果**有限**且**等可能**，则

```math
P(A\mid B) = \frac{\text{集合 } A\cap B\text{ 的元素个数}}{\text{集合 } B\text{ 的元素个数}}.
```

下面给出三个例子。

---

## <span style="color:#2471a3;">**[example] 例 1.6（抛三次硬币）**</span>

我们连续三次抛掷一枚公平硬币，希望求条件概率 $P(A\mid B)$，其中

```math
A = \{\text{正面朝上的次数多于反面}\},\qquad
B = \{\text{第一次抛掷结果是正面}\}.
```

样本空间由八个序列构成：

```math
\Omega = \{HHH,\ HHT,\ HTH,\ HTT,\ THH,\ THT,\ TTH,\ TTT\},
```

我们假设它们等可能。事件 $B$ 由四个元素 $HHH, HHT, HTH, HTT$ 组成，所以

```math
P(B) = \frac{4}{8}.
```

事件 $A\cap B$ 由三个元素 $HHH, HHT, HTH$ 组成，所以

```math
P(A\cap B) = \frac{3}{8}.
```

于是条件概率为

```math
P(A\mid B) = \frac{P(A\cap B)}{P(B)} = \frac{3/8}{4/8} = \frac{3}{4}.
```

由于这里所有可能结果等可能，我们也可以用捷径计算 $P(A\mid B)$：直接跳过 $P(B)$ 与 $P(A\cap B)$ 的计算，用 $A$ 与 $B$ 的公共元素个数 $3$ 除以 $B$ 的元素个数 $4$，就得到同样的结果 $3/4$。

## <span style="color:#2471a3;">**[example] 例 1.7（掷两次正四面体骰子）**</span>

掷两次公平的正四面体骰子（4 面骰），假设全部 $16$ 个可能结果等可能。设 $X$、$Y$ 分别是第一次和第二次的点数。我们希望求 $P(A\mid B)$，其中

```math
A = \{\max(X,Y)=m\},\qquad B = \{\min(X,Y)=2\},
```

而 $m$ 分别取 $1,2,3,4$。

(参考 图 1.8：这是一个"掷两次正四面体骰子"试验的样本空间。)

集合 $A = \{\max(X,Y)=m\}$ 与 $B$ 的交集：当 $m=3$ 或 $m=4$ 时含有两个元素，当 $m=2$ 时含一个元素，当 $m=1$ 时不含任何元素。于是

```math
P\big(\{\max(X,Y)=m\}\mid B\big) =
\begin{cases}
2/5, & \text{若 } m=3\text{ 或 }m=4,\\
1/5, & \text{若 } m=2,\\
0,    & \text{若 } m=1.
\end{cases}
```

(注：因为 $B=\{\min(X,Y)=2\}$ 由 $(2,2),(2,3),(2,4),(3,2),(4,2)$ 五个等可能结果组成，$P(B)=5/16$。我们也可以直接数 $A\cap B$ 与 $B$ 的元素个数相除，得到同样的结果。)

## <span style="color:#2471a3;">**[example] 例 1.8（两个团队的产品设计）**</span>

有两个团队——记为 $C$ 与 $N$——被要求在**一个月内各自独立**地设计一款新产品。根据过去的经验，我们知道：

(a) 团队 $C$ 成功的概率是 $2/3$。

(b) 团队 $N$ 成功的概率是 $1/2$。

(c) 至少一个团队成功的概率是 $3/4$。

假设最终**恰好**有一份成功的设计方案被生产出来，问这份方案是由团队 $N$ 设计的概率是多少？

这里一共有四个可能结果，对应两个团队成败的四种组合：

```math
SS:\ \text{两者都成功},\qquad SF:\ C\text{ 成功、}N\text{ 失败},\qquad
FS:\ C\text{ 失败、}N\text{ 成功},\qquad FF:\ \text{两者都失败}.
```

题目告诉我们这些结果的概率满足

```math
P(SS)+P(SF)=\frac{2}{3},\qquad
P(SS)+P(FS)=\frac{1}{2},\qquad
P(SS)+P(SF)+P(FS)=\frac{3}{4}.
```

由这些关系，再加上归一化方程

```math
P(SS)+P(SF)+P(FS)+P(FF)=1,
```

可以解出各单个结果的概率：

```math
P(SS)=\frac{5}{12},\qquad
P(SF)=\frac{1}{4},\qquad
P(FS)=\frac{1}{12},\qquad
P(FF)=\frac{1}{4}.
```

所求条件概率为

```math
P\big(FS\mid \{SF,FS\}\big) = \frac{P(FS)}{P(SF)+P(FS)}
= \frac{1/12}{1/4+1/12} = \frac{1}{4}.
```

> <span style="color:#1e8449;">**[note] Note（译者注）：**</span> 例 1.8 亮出一个高频套路：题目给的往往是「若干子集概率之和」这类宏观约束，必须先反解出单个结果的概率、再做条件化。这里三个方程解三个未知量 $P(SS),P(SF),P(FS)$，再配归一化方程补足第四个——这本质就是在解一个小线性方程组，正是你在 Strang 线性代数里那套高斯消元/系数矩阵思想在概率里的化身。条件化时分母 $P(\{SF,FS\})=P(SF)+P(FS)$ 之所以能相加，凭的是 $SF$ 与 $FS$ 互不相交这条**可加性公理**，不是想当然。反过来，若题目额外给出两队独立，才可用乘法 $P(SS)=P(C\text{成功})P(N\text{成功})=\tfrac23\cdot\tfrac12$——但这里故意不给独立性条件，正是提醒你：工程题往往只给边缘（汇总）信息，独立性必须单独验证或假定，不能默认成立。卡点：先分辨「命题给我的究竟是边概率还是联合约束」，再决定该逆向求解还是直接相乘。

> <span style="color:#7f8c8d;">BT §1.3, p.21</span>

## <span style="color:#c0392b;">用条件概率进行建模 Using Conditional Probability for Modeling</span>

在构造**具有序贯（sequential）特征**的试验概率模型时，一个自然且方便的做法往往是：**先**规定各个条件概率，**再**用它们去求无条件概率。在此过程中，规则

```math
P(A\cap B) = P(B)\,P(A\mid B),
```

（它是条件概率定义的重述）常常很有帮助。

## <span style="color:#2471a3;">**[example] 例 1.9（雷达检测 Radar Detection）**</span>

若某个区域内有飞机，则雷达能以概率 $0.99$ 探测到它并发出警报信号；若该区域没有飞机，则雷达以概率 $0.10$ 发出（虚）警报。我们假设区域内出现飞机的概率为 $0.05$。问："没有飞机且发出虚警"的概率是多少？"有飞机但未被探测到"的概率是多少？

这里的试验很适合用**序贯表示（sequential representation）**，如图 1.9 所示。设 $A$、$B$ 为事件：

```math
A = \{\text{区域内存在飞机}\},\qquad
B = \{\text{雷达发出警报}\},
```

并考虑它们的补事件：

```math
A^c = \{\text{区域内不存在飞机}\},\qquad
B^c = \{\text{雷达不发出警报}\}.
```

给定的概率被记录在描述样本空间的**树（tree）**的相应分支旁（见图 1.9）。每个可能结果对应树的一片叶子；叶子的概率等于从根到该叶子的路径上各分支概率之积。于是所求概率为

```math
P(\text{无飞机，虚警}) = P(A^c\cap B) = P(A^c)\,P(B\mid A^c) = 0.95\times 0.10 = 0.095,
```

```math
P(\text{有飞机，未探测到}) = P(A\cap B^c) = P(A)\,P(B^c\mid A) = 0.05\times 0.01 = 0.0005.
```

把上面的例子推广，可以得到一个用于"结合树图序贯描述计算概率"的通用规则。

> <span style="color:#c0392b;">**[property] 树图序贯描述下的概率计算规则（General Rule）:**</span>
>
> (a) 我们布置这棵树，使所关心的事件与某一特定的**叶子**相关联。我们把该事件的发生看作一系列步骤，即从根到叶的路径上对各分支的依次穿越。
>
> (b) 我们把与树各分支相关联的**条件概率**记录下来。
>
> (c) 我们通过把沿树中相应路径记录下来的概率**相乘**，得到该叶子的概率。

用数学的话说：我们处理的是一类事件 $A$，它发生当且仅当若干个事件 $A_1,\ldots,A_n$ 全部发生，即 $A = A_1\cap A_2\cap\cdots\cap A_n$。$A$ 的发生被看作是：先发生 $A_1$，接着发生 $A_2$，再发生 $A_3$，等等；并可想象为一条含 $n$ 条分支的路径，分别对应事件 $A_1,\ldots,A_n$。$A$ 的概率由下列规则给出（也见图 1.10）。

> <span style="color:#c0392b;">**[property] 乘法规则（The Multiplication Rule）:**</span> 假设所有出现的条件化事件概率均为正，则

```math
P\left(\bigcap_{i=1}^{n}A_i\right)
= P(A_1)\,P(A_2\mid A_1)\,P(A_3\mid A_1\cap A_2)\cdots
P\!\left(A_n\mid \bigcap_{i=1}^{n-1}A_i\right).
```

乘法规则可以通过反复使用条件概率定义来验证：把右端写成一串"分子分母逐项相消"的形式——

```math
P\left(\bigcap_{i=1}^{n}A_i\right)
= P(A_1)\cdot
\frac{P(A_1\cap A_2)}{P(A_1)}\cdot
\frac{P(A_1\cap A_2\cap A_3)}{P(A_1\cap A_2)}\cdots
\frac{P\left(\bigcap_{i=1}^{n}A_i\right)}
{P\left(\bigcap_{i=1}^{n-1}A_i\right)}.
```

(图 1.10：乘法规则的可视化。交集事件 $A = A_1\cap A_2\cap\cdots\cap A_n$ 与树上的某条特定路径相关联；把这条路径的各分支对应到事件 $A_1,\ldots,A_n$，并在分支旁记录相应的条件概率。路径的末端节点对应交集事件 $A$，其概率就是把路径各分支上记录的条件概率相乘而得。注意：路径上**任何中间节点**也都对应某个交集事件，其概率等于把到该节点为止的各条件概率相乘。例如，事件 $A_1\cap A_2\cap A_3$ 对应图中所示节点，其概率即各相应条件概率之积。)

对只有两个事件 $A_1,A_2$ 的情形，乘法规则正是条件概率的定义本身。

> <span style="color:#1e8449;">**[note] Note（译者注）：**</span> 乘法规则在直觉上非常好用，就一句话：**"一整串同时发生"的概率 = 一步一步地"在已发生的前提下接着发生的条件概率"连乘**。每一步乘进去的分母，恰好会与下一步分子的重叠部分相消，所以最终得到的那一大串其实是"链式法则（chain rule）"。树图把这个过程变成了**可读的流程图**：根到叶的每条路径，都是一条"先……在……条件下再……"的故事线，概率就在图上逐段连乘。这条规则与 CSAPP 里**随机化算法的期望分析**密切相关：当你沿某个分支一步步走下去（例如哈希表的插入路径、随机化快排的递归路径）时，每一步都给出一个条件概率，整条路径的概率正是它们的乘积，而"期望路径长度/命中概率"就是这样累积出来的。注意规则里要求"每个条件化事件概率均为正"——这是因为分母不能为零，与条件概率本身"$P(B)>0$才有定义"的约定一致。

> <span style="color:#7f8c8d;">BT §1.3, p.23–24</span>

## <span style="color:#2471a3;">**[example] 例 1.10（三张扑克牌）**</span>

从一副普通的 $52$ 张扑克牌中**不放回**地抽取 $3$ 张（抽出的牌不放回）。我们希望求"三张都不是红心"的概率。我们假设在每一步，剩余的每张牌等可能被抽到。由对称性，这意味着每**三张一组**的牌等可能被抽出。一种繁琐的方法（我们不采用）是数出不含红心的三张牌组的个数，再除以所有可能三张牌组的总数。我们改用试验的**序贯描述**并结合**乘法规则**（参见图 1.11）。

定义事件

```math
A_i = \{\text{第 }i\text{ 张牌不是红心}\},\qquad i=1,2,3.
```

用乘法规则计算 $A_1\cap A_2\cap A_3$（即三张都不是红心）的概率：

```math
P(A_1\cap A_2\cap A_3) = P(A_1)\,P(A_2\mid A_1)\,P(A_3\mid A_1\cap A_2).
```

确定性：$52$ 张牌中有 $39$ 张不是红心，所以

```math
P(A_1)=\frac{39}{52}.
```

已知第一张不是红心后，剩下 $51$ 张牌，其中 $38$ 张不是红心，于是

```math
P(A_2\mid A_1)=\frac{38}{51}.
```

同理，已知前两张都不是红心后，剩下 $50$ 张牌中有 $37$ 张不是红心，故

```math
P(A_3\mid A_1\cap A_2)=\frac{37}{50}.
```

这些概率被记录在描述样本空间的树图的相应分支旁（见图 1.11）。现在，把树中相应路径上记录的各概率相乘，即得所求概率：

```math
P(A_1\cap A_2\cap A_3) = \frac{39}{52}\cdot\frac{38}{51}\cdot\frac{37}{50}.
```

(图 1.11：例 1.10"三张牌抽取问题"中试验的序贯描述。)

注意：一旦这些概率被记录到树图上，**其他**事件的概率也就可以依次相乘计算出来。例如：

```math
P(\text{第 1 张不是红心，且第 2 张是红心}) = \frac{39}{52}\cdot\frac{13}{51},
```

```math
P(\text{第 1、2 张都不是红心，且第 3 张是红心}) = \frac{39}{52}\cdot\frac{38}{51}\cdot\frac{13}{50}.
```

## <span style="color:#2471a3;">**[example] 例 1.11（把学生随机分组）**</span>

一个班级由 $4$ 名研究生和 $12$ 名本科生组成，被**随机**分成 $4$ 个小组，每组 $4$ 人。问：每个小组都包含一名研究生的概率是多少？

我们把"随机"理解为：在把某些学生分配到某些位置之后，剩下的任意一名学生等可能地被分配到剩余各位置。于是用乘法规则求解，步骤如下。

把 $4$ 名研究生记为 $1,2,3,4$，考虑事件

```math
A_1 = \{\text{学生 }1\text{ 与 }2\text{ 分在不同组}\},\qquad
A_2 = \{\text{学生 }1,2,3\text{ 分在不同组}\},\qquad
A_3 = \{\text{学生 }1,2,3,4\text{ 分在不同组}\}.
```

我们用乘法规则计算 $P(A_3)$：

```math
P(A_3) = P(A_1\cap A_2\cap A_3) = P(A_1)\,P(A_2\mid A_1)\,P(A_3\mid A_1\cap A_2).
```

由于除学生 $1$ 所在的组之外还有 $12$ 个学生位，而扣除学生 $1$ 后总共有 $15$ 个位，故 $P(A_1)=\frac{12}{15}$；……

（本批日志在例 1.11 展开到 $P(A_1)=\frac{12}{15}$ 与条件概率 $P(A_2\mid A_1)=\frac{8}{14}$ 处截止——因为扣除学生 $1,2$ 所在的组之外还有 $8$ 个位，而扣除 $1,2$ 后共有 $14$ 个位。完整解答将由后续批次续完。）

> <span style="color:#7f8c8d;">BT §1.3, p.25（例 1.11 起始）</span>

---

batch_D.md
# <span style="color:#c0392b;">1.4 全概率定理与贝叶斯法则 (`Total Probability Theorem and Bayes' Rule`)</span>

<span style="color:#7f8c8d;">**[tag: §1.4, continuation from §1.2 & §1.3]**</span>

> <span style="color:#7f8c8d;">BT §1.4, p.27–33</span>

## <span style="color:#c0392b;">（接续 1.2 顺序建模 `Sequential Modeling`）</span>

在顺序建模（`sequential modeling`）里，复杂实验的概率是把树形图（`tree diagram`）中沿某条路径（`path`）的各条边的概率相乘得到的，这就是乘法法则（`multiplication rule`）。以例 1.11 中的学生问题为例，所求概率就是通过把图 1.12 中树形图对应路径（`path`）上的概率相乘得到的。

下面这个著名的智力题恰好说明，能否求出概率，取决于我们如何使用信息。

## <span style="color:#2471a3;">**[example] 例 1.12　Monty Hall 问题（`Monty Hall Problem`）**</span>

这是一个广为人知的谜题，取材于一档古老的美国电视节目。你被告知：奖品（`prize`）等可能地（`equally likely`）藏在三扇门中的任意一扇后面，你希望选中藏着奖品的那扇门。你先把手指向门 1（`door 1`）；随后的主持人（`host`）——他知道奖品在哪——会在另外两扇门中打开其中一扇，并且确保打开的这扇门后面没有奖品。到这个时候，你可以坚持你的最初选择（`stick to your initial choice`），也可以切换到另一扇尚未打开的门（`switch to the other unopened door`）。只要你最终选择的门后面藏着奖品，你就获胜。请比较以下三种策略：

(a) 坚持最初的（`initial`）选择。

(b) 切换到另一扇尚未打开的门。

(c) 你先把手指向门 1。如果门 2 被打开，你就不切换；如果门 3 被打开，你就切换。

哪种策略最好？为了回答这个问题，让我们计算每一种策略下你赢或输的概率，记为奖品等可能地藏在三扇门中的任意一扇后面。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 题目里那句"保证打开的这扇门后面没有奖品"是关键。这里用的思路，正是"条件概率=把样本空间缩小到已经发生的事件"这一直觉：一旦主持人开门，样本空间就不再是原来的"三扇门"，而是缩小成"你选的门 + 主持人留下的那扇门"。你原来的选择命中奖品的概率是 1/3，而"另一扇没打开的门"这一事件实际上吸收了"奖品在我没选且主持人没开的那扇门后"这 2/3 的概率。关键是主持人永远不会开出奖品，所以他的信息(self-selecting choice)不是随机的——他是在"排除一个确定没有奖品的选项"，而不是"随机开一扇也可能开中奖品的门"。这也是为什么策略 (b) 通常得到 2/3 而不是 1/2：因为主持人的行为把"剩余 2/3"全部集中到了他要你切换的那扇门上。你之前在 6.042J 里用条件概率算过此类博弈，这里的本质没有变，只是要分清"信息是如何产生的"——是公平随机还是被策略性地选择，这直接决定了你能否把它当作"无信息"来处理。

**策略 (a) 与 (b)。** 如果你不切换（策略 a），你赢当且仅当你最初已指向奖品所在的门，故获胜概率为 1/3。另一方面，如果你切换到另一扇尚未打开的门（策略 b），那么只要奖品最初不在你指的那扇门后——这个事件的概率为 2/3——主持人就会为你打开另一扇没有奖品的门，于是你一旦切换就必然到达藏有奖品的那扇门。因此，获胜概率现在是 2/3，故策略 (b) 优于策略 (a)。

现在考虑策略 (c)。在这个策略下，信息不足以确定获胜概率；答案取决于你的朋友选择打开哪扇门的方式。让我们考虑两种可能。

假设如果奖品在门 1 后面，你的朋友总是选择打开门 2。（如果奖品在门 2 或门 3 后面，你的朋友别无选择。）此时：若奖品在门 1 后面，你的朋友打开门 2，你不切换，你获胜；若奖品在门 2 后面，你的朋友打开门 3，你切换，你获胜；若奖品在门 3 后面，你的朋友打开门 2，你不切换，你失败。因此获胜概率为 2/3，所以此时策略 (c) 与策略 (b) 一样好。

再假设如果奖品在门 1 后面，你的朋友以相同的概率打开门 2 或门 3 中的任意一扇。若奖品在门 1 后面（概率 1/3），且你的朋友打开门 2（概率 1/2），则你不切换并获胜（概率 1/6）；但若你的朋友打开门 3，你切换并失败。若奖品在门 2 后面，你的朋友打开门 3，你切换并获胜（概率 1/3）；若奖品在门 3 后面，你的朋友打开门 2，你不切换并失败。因此获胜概率为 $1/6+1/3=1/2$，所以此时策略 (c) 劣于策略 (b)。

---

本节我们探讨条件概率（`conditional probability`）的一些应用。从下面的定理开始，它在计算各种事件的概率时常常很有用，采用一种"分而治之"（`divide-and-conquer`）的思路。

## <span style="color:#2471a3;">**[theorem] 全概率定理（`Total Probability Theorem`）**</span>

设 $A_1,\ldots,A_n$ 是两两不交（`disjoint`）的事件，它们构成样本空间的一个分割（`partition`）（每个可能结果都恰包含在 $A_1,\ldots,A_n$ 中的某一个里），并假设对所有 $i$ 有 $P(A_i)>0$。于是对任意事件 $B$，有

```math
P(B)=P(A_1\cap B)+\cdots+P(A_n\cap B)
=P(A_1)P(B\mid A_1)+\cdots+P(A_n)P(B\mid A_n).
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 这个定理的可视化与证明在图 1.13 中给出。直观上，我们把样本空间分割成若干个"情景"（场景，`scenario`）$A_i$；于是事件 $B$ 发生的概率，是它每种情景下的**条件概率**的加权平均，其中每个情景按它自己的（无条件）概率来加权。定理的用途之一，是计算那些"条件概率 $P(B\mid A_i)$ 已知或容易算"的事件 $B$ 的概率。关键在于**恰当地选择**把样本空间分割成哪些 $A_1,\ldots,A_n$——要贴合问题的结构。这里的"条件概率其实是把样本空间换成了某个 $A_i$"这个想法，正是上一小节"条件作为新样本空间"的延续：$P(B\mid A_i)$ 是在把样本空间缩小到 $A_i$ 之后的概率，而把各情景按其实出现的可能性加权相加，就还原了整个样本空间上的 $P(B)$。它跟你学过的 6.042J 里"先按情景区分再求和"的思路一脉相承，只不过这里每个分支被系统地乘上了它自身的先验权重。

图 1.13（`Fig. 1.13`）可视化了定理的证明思路。由于 $A_1,\ldots,A_n$ 构成样本空间的一个分割，事件 $B$ 可以分解成它与各 $A_i$ 之交的**不交并**（`disjoint union`）

```math
B=(A_1\cap B)\cup\cdots\cup(A_n\cap B).
```

利用可加性公理（`additivity axiom`）可知

```math
P(B)=P(A_1\cap B)+\cdots+P(A_n\cap B).
```

再由条件概率的定义 $P(A_i\cap B)=P(A_i)P(B\mid A_i)$，即得

```math
P(B)=P(A_1)P(B\mid A_1)+\cdots+P(A_n)P(B\mid A_n).
```

另一种视角：考虑一个等价的**顺序模型**（`sequential model`），如图右侧所示。叶子 $A_i\cap B$ 的概率，就是通向该叶子的路径上各概率的乘积 $P(A_i)\,P(B\mid A_i)$；事件 $B$ 由这三片叶子组成，把它们的概率相加即可得到 $P(B)$。

## <span style="color:#2471a3;">**[example] 例 1.13（象棋比赛）**</span>

你要参加一个象棋（`chess`）锦标赛。你战胜对手的概率取决于对手所属的类型（`type`）：你能战胜一半的选手（称其为类型 1，`type 1`），战胜四分之一的选手（称其为类型 2，`type 2`），而对剩下四分之一中的选手（称其为类型 3，`type 3`）也能取胜（原文此处因扫描缺损，按上下文与例 1.17 的数据还原为：赢类型 1 的概率为 0.3、赢类型 2 为 0.4、赢类型 3 为 0.5）。你被随机安排与一名随机选择的对手博弈（`play a game against a randomly chosen opponent`）。请问你赢的概率是多少？

设 $A_i$ 为`你遇到类型 i 的对手`这一事件。由"一半 / 四分之一 / 四分之一"的结构（并结合 §1.4 末尾例 1.17 的同一组先验），有 $P(A_1)=0.5$，$P(A_2)=0.25$，$P(A_3)=0.25$。再设 $B$ 为`你获胜`这一事件，并给定

```math
P(B\mid A_1)=0.3,\qquad P(B\mid A_2)=0.4,\qquad P(B\mid A_3)=0.5.
```

于是由全概率定理，获胜概率为

```math
P(B)=P(A_1)P(B\mid A_1)+P(A_2)P(B\mid A_2)+P(A_3)P(B\mid A_3)
=0.5\cdot0.3+0.25\cdot0.4+0.25\cdot0.5=0.375.
```

## <span style="color:#2471a3;">**[example] 例 1.14（四面骰子）**</span>

你掷一个均匀的四面骰子（`fair four-sided die`）。如果结果是 1 或 2，你再多掷一次；否则你停下。请问你所有掷出的点的**总和**（`sum total`）至少为 4 的概率是多少？

设 $A_i$ 为`第一次掷出的结果是 i`这一事件，并注意对每个 $i$ 有 $P(A_i)=1/4$。设 $B$ 为`总和至少为 4`这一事件。给定事件 $A_1$，只有当第二次掷出 3 或 4（概率 1/2）时总和才至少为 4；类似地，给定事件 $A_2$，只有当第二次掷出 2、3 或 4（概率 3/4）时总和才至少为 4；再给定事件 $A_3$，你停下，总和仍小于 4；而给定事件 $A_4$，你停下，总和即为 4（概率 1）。因此

```math
P(B\mid A_1)=\frac12,\quad P(B\mid A_2)=\frac34,\quad P(B\mid A_3)=0,\quad P(B\mid A_4)=1.
```

由全概率定理，

```math
P(B)=\frac14\cdot\frac12+\frac14\cdot\frac34+\frac14\cdot0+\frac14\cdot1=\frac18+\frac3{16}+0+\frac14=\frac9{16}.
```

全概率定理可以反复应用，来计算具有**顺序特征**（`sequential character`）的实验中的概率，如下例所示。

## <span style="color:#2471a3;">**[example] 例 1.15（爱丽丝是否跟上进度）**</span>

爱丽丝（`Alice`）在上一个概率班，每周末她要么跟上了进度（`up-to-date`），要么落下了进度（`behind`）。如果她在某周跟上了，则下一周她跟上的概率为 0.8、落下的概率为 0.2；如果她在某周落后了，则下一周她跟上的概率为 0.4、落下的概率为 0.6。爱丽丝（默认）在开课之初是跟上的。请问三周之后她跟上进度的概率是多少？

设 $U_i$ 和 $B_i$ 分别为`爱丽丝在第 i 周末跟上`和`第 i 周末落后`的事件。根据全概率定理，所求概率 $P(U_3)$ 由下式给出

```math
P(U_3)=P(U_2)P(U_3\mid U_2)+P(B_2)P(U_3\mid B_2)=P(U_2)\cdot0.8+P(B_2)\cdot0.4.
```

$P(U_2)$ 与 $P(B_2)$ 也可用全概率定理计算：

```math
P(U_2)=P(U_1)P(U_2\mid U_1)+P(B_1)P(U_2\mid B_1)=P(U_1)\cdot0.8+P(B_1)\cdot0.4,
```

```math
P(B_2)=P(U_1)P(B_2\mid U_1)+P(B_1)P(B_2\mid B_1)=P(U_1)\cdot0.2+P(B_1)\cdot0.6.
```

最后，由于爱丽丝开课时是跟上的，我们有

```math
P(U_1)=0.8,\qquad P(B_1)=0.2.
```

把上述三组方程结合起来，得

```math
P(U_2)=0.8\cdot0.8+0.2\cdot0.4=0.72,
```

```math
P(B_2)=0.8\cdot0.2+0.2\cdot0.6=0.28,
```

再用这些概率代入 $P(U_3)$ 的公式：

```math
P(U_3)=0.72\cdot0.8+0.28\cdot0.4=0.688.
```

注意，我们本可以通过构造实验的树形图、再用乘法法则（`multiplication rule`）计算 $U_3$ 中每个元素的概率并求和，来求出所求概率 $P(U_3)$。但在某些情形下，基于全概率定理的计算更方便。例如，假设我们对"20 周之后爱丽丝跟上"的概率 $P(U_{20})$ 感兴趣。用乘法法则计算会非常繁琐，因为表示该实验的树深达 20 层、有 $2^{20}$ 片叶子。另一方面，用计算机做基于全概率公式的**顺序计算**（`sequential calculation`）

```math
P(U_{i+1})=P(U_i)\cdot0.8+P(B_i)\cdot0.4,
```

```math
P(B_{i+1})=P(U_i)\cdot0.2+P(B_i)\cdot0.6,
```

并配合初值条件 $P(U_1)=0.8,\;P(B_1)=0.2$，则非常简单。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 例 1.15 里「递推前进一步」的写法，其实就是一个初等的**动态规划（dynamic programming）**/ 状态转移（`state transition`）模型：$U_i,B_i$ 是两个状态，0.8、0.4 等数值把本周的状态分布推到下周。你在 6.006（CLRS）和 18.065 会反复看到这种「一步更新当前向量」的思想，只是这里更新的是**概率分布**而非单一数值。它的骨骼就是 $2\times2$ 转移矩阵 $\begin{pmatrix}0.8&0.4\\0.2&0.6\end{pmatrix}$ 左乘状态向量 $\begin{pmatrix}P(U_i)\\P(B_i)\end{pmatrix}$，与你刚在 Strang / 18.065 学的矩阵幂、特征值、稳态正好配套：$P(U_{20})$ 就是不断左乘该矩阵逼近稳态分布的极限，这正是第 7 章马尔可夫链（`Markov chain`）的雏形。所以看特征值与稳态分布可预判长期行为，而迭代算下值只需 $O(i)$ 次矩阵乘，远比枚举 $2^{20}$ 片叶子的穷举树可行。卡点：留意转移矩阵的**列和恒为 1**——每列条件转移概率相加必须等于 1，否则状态分布的总质量会漂移，这是这类模型自洽的检验线。

## <span style="color:#c0392b;">推断与贝叶斯法则（`Inference and Bayes' Rule`）</span>

全概率定理常与下面这个著名的定理联用。该定理把形如 $P(A\mid B)$ 的条件概率与形如 $P(B\mid A)$ 的条件概率联系起来——后者中**条件化的顺序**（`order of the conditioning`）被颠倒了过来。

## <span style="color:#2471a3;">**[theorem] 贝叶斯法则（`Bayes' Rule`）**</span>

设 $A_1,A_2,\ldots,A_n$ 是两两不交且构成样本空间分割的事件，并假设对所有 $i$ 有 $P(A_i)>0$。于是对任意满足 $P(B)>0$ 的事件 $B$，有

```math
P(A_i\mid B)=\frac{P(A_i)P(B\mid A_i)}{P(B)}=\frac{P(A_i)P(B\mid A_i)}{P(A_1)P(B\mid A_1)+\cdots+P(A_n)P(B\mid A_n)}.
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 贝叶斯法则的推理脉络藏在图 1.14 的"推断"语境里：我们观察到一个**效应**（`effect`），想反推它背后若干互斥且穷尽的原因各自的可能性。设 $A_1,A_2,A_3$ 为三种可能的原因（例如恶性肿瘤、良性病变、其他原因），$B$ 为观察到的效应；假设已知各先验概率（`prior`）$P(A_i)$ 和"若原因为 $A_i$ 则效应 $B$ 出现"的概率 $P(B\mid A_i)$（即似然，`likelihood`），则贝叶斯法则给出后验（`posterior`）$P(A_i\mid B)$。形象地看，$P(A_1\mid B)$（恶性肿瘤的后验）就是第一片高亮叶子的概率 $P(A_1\cap B)$ 除以全部叶子（效应 $B$）的总概率 $P(B)$。这里"$P(A_i\mid B)$ 是给定信息（观察到效应 B 之后）下事件 $A_i$ 的概率，要与无条件概率 $P(A_i)$ 相区分"这一点，正是"条件作为新样本空间"的又一次体现：观察到 $B$ 把你的样本空间从全部结果缩小到那些效应发生的结果，再在其中衡量各原因的相对权重。你下学期要学的信息论（`information theory`）里，$P(A\mid B)$ 更新前后熵（`entropy`）的变化正是互信息（`mutual information`）——贝叶斯法则就是在量化"观察到效应增加了多少关于原因的信息"，只是信息论用对数熵来衡量、概率论用直接的概率更新来衡量，两者是同一个直觉的两副面孔。

## <span style="color:#2471a3;">**[example] 例 1.16（雷达检测）**</span>

让我们回到例 1.9 与图 1.9 的雷达检测问题。设

```math
A=\{\text{存在一架飞机(an aircraft is present)}\},\qquad
B=\{\text{雷达发出警报(the radar generates an alarm)}\}.
```

已知

```math
P(A)=0.05,\qquad P(B\mid A)=0.99,\qquad P(B\mid A^c)=0.1.
```

取 $A_1=A$、$A_2=A^c$，应用贝叶斯法则，得

```math
P(\text{飞机存在}\mid\text{有警报})=P(A\mid B)=\frac{P(A)P(B\mid A)}{P(B)}
```

```math
=\frac{P(A)P(B\mid A)}{P(A)P(B\mid A)+P(A^c)P(B\mid A^c)}
```

```math
=\frac{0.05\cdot0.99}{0.05\cdot0.99+0.95\cdot0.1}\approx0.3426.
```

## <span style="color:#2471a3;">**[example] 例 1.17（回到象棋问题）**</span>

让我们回到例 1.13 的象棋问题。此处 $A_i$ 是`遇到类型 i 的对手`这一事件，且

```math
P(A_1)=0.5,\qquad P(A_2)=0.25,\qquad P(A_3)=0.25.
```

另外 $B$ 是`获胜`这一事件，且

```math
P(B\mid A_1)=0.3,\qquad P(B\mid A_2)=0.4,\qquad P(B\mid A_3)=0.5.
```

假设你赢了。请问$P(A_1\mid B)$——你遇到的是类型 1 对手的概率——是多少？

用贝叶斯法则，有

```math
P(A_1\mid B)=\frac{P(A_1)P(B\mid A_1)}{P(A_1)P(B\mid A_1)+P(A_2)P(B\mid A_2)+P(A_3)P(B\mid A_3)}
```

```math
=\frac{0.5\cdot0.3}{0.5\cdot0.3+0.25\cdot0.4+0.25\cdot0.5}=0.4.
```

## <span style="color:#2471a3;">**[example] 例 1.18　假阳性谜题（`The False-Positive Puzzle`）**</span>

针对某种罕见疾病（`rare disease`）的检验被假定有 95% 的正确率：如果一个人患有该病，检验结果以概率 0.95 为阳性（`positive`）；如果一个人没有患病，检验结果以概率 0.95 为阴性（`negative`）。从某一人群中随机抽取一人，其患病的概率为 0.001。已知此人刚测出阳性，那么他患病的概率是多少？

若 $A$ 是`此人患病`这一事件，$B$ 是`检验结果为阳性`这一事件，则所求概率 $P(A\mid B)$ 为

```math
P(A\mid B)=\frac{P(A)P(B\mid A)}{P(A)P(B\mid A)+P(A^c)P(B\mid A^c)}
```

```math
=\frac{0.001\cdot0.95}{0.001\cdot0.95+0.999\cdot0.05}=0.0187.
```

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 请注意：尽管检验被假定相当准确，但一个测出阳性的人***仍然不大可能***（不足 2%）真的患病。据《经济学人》1999 年 2 月 20 日报道，在一家美国大医院接受提问的人中有 80% 大幅错估了这类题的答案，其中大多数人以为此人患病的概率是 0.95！这个反直觉结果的根源在于**基础比率（`base rate`）**：先验 $P(A)=0.001$ 极低，而假阳性率虽小（5%）却乘以了一个庞大的"未患病"群体 $P(A^c)=0.999$。贝叶斯法则把"假阳性绝对数量很大"这一点显式地放进了分母，所以即使似然 $P(B\mid A)=0.95$ 很高，后验仍被先验牢牢拉住。这正是"条件作为新样本空间"与"后验更新"在现实中的教训：条件概率很好用，但只有把先验放进称量，结论才不会被"貌似可靠的检验"误导。它和例 1.16 的雷达问题、上一题的虚假警报是同一道算术——识别"罕见事件 + 不高但存在的误报率"这个组合，AUC/ROC 曲线那套思想（你会在信息论或统计课上遇到）也是为驯服这类权衡而生的。

---

# <span style="color:#c0392b;">1.5 独立性（`INDEPENDENCE`）</span>

我们引入条件概率 $P(A\mid B)$，是为了捕捉事件 $B$ 提供的关于事件 $A$ 的**部分信息**（`partial information`）。一个有趣且重要的特殊情形是：$B$ 的发生不提供这方面的任何信息，也不改变 $A$ 已经发生的概率，即

```math
P(A\mid B)=P(A).
```

> <span style="color:#00838f;">**[definition] 独立性（`independence`）**</span>
> 当上式成立时，我们说 $A$ 与 $B$ **独立**（`independent`）。注意：由定义 $P(A\mid B)=P(A\cap B)/P(B)$，上式等价于

```math
P(A\cap B)=P(A)P(B).
```

> 我们采用后一个关系作为**独立性的定义**（`definition of independence`），因为即使当 $P(B)=0$（此时 $P(A\mid B)$ 无定义）它也能使用。这个关系的对称性也蕴含了独立性是对称的性质：即若 $A$ 与 $B$ 独立，则 $B$ 与 $A$ 独立，于是我们可以无歧义地说 $A$ 和 $B$ 是独立事件。

独立性在直觉上往往很好理解。例如，若两个事件的发生分别由截然不同、互不作用的物理过程决定，那么这两个事件通常就是独立的。另一方面，独立性很难用样本空间来可视化。一个常见的初步想法是：两个事件若**不交**（`disjoint`）就是独立的，但事实上恰恰相反：两个不交事件 $A$ 与 $B$，若 $P(A)>0$ 且 $P(B)>0$，则它们**从不**独立，因为它们的交集 $A\cap B$ 为空、概率为 0（从而 $P(A)P(B)>0$），而 $P(A\cap B)=0$。例如，事件 $A$ 与其补 $A^c$ 不独立，除非 $P(A)=0$ 或 $P(A)=1$，因为"$A$ 已发生"这一知识精确地告诉我们 $A^c$ 是否发生。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span> 独立性选乘法 $P(A\cap B)=P(A)P(B)$ 而非条件式 $P(A\mid B)=P(A)$ 来定义，技术原因在于后者在 $P(B)=0$ 时根本无定义、前者处处有意义——多花这一行是为了定义域的干净。这与你正在学的实分析测度视角严丝合缝：事件是 $\Omega$ 的子集，$P(\cdot)$ 是 $\sigma$-代数上的有限测度，「独立」就是两个事件族上的测度乘积可分解 $P(A\cap B)=P(A)P(B)$，正对应测度论里乘积测度（`product measure`）构造那条路（也可类比 Strang 里「两个不相干因子的外积/张量」直觉）。务必分清：独立**完全不是**集合论里的「互不相交」，恰恰相反，两个不交且概率为正的事件满足 $P(A\cap B)=0\lt P(A)P(B)$，因此从不独立——不交意味着「含一个就绝不含另一个」（信息高度耦合），独立却意味着「知不知道无所谓」，是两个极端。你在 6.042J 已用条件概率处理过独立事件，这里是无量纲化（不除以 $P(B)$）的改写，也为后文推广到一族事件独立与随机变量独立铺路。卡点预告：协方差为 0（不相关）与独立并不等价，独立蕴含不相关但反之不然（联合正态除外），等学到第 4 章协方差再回看这条会更清楚。

## <span style="color:#2471a3;">**[example] 例 1.19**</span>

考虑这样一个实验：连续掷两次均匀的四面骰子（`4-sided die`），所有 16 种可能结果等可能、每种概率为 1/16。

**(a)** 事件

```math
A_i=\{第 1 次掷出 i (1st roll results in i)\},\qquad
B_j=\{第 2 次掷出 j (2nd roll results in j)\}
```

是否独立？我们有

```math
P(A_i\cap B_j)=P(\text{两次掷出的结果是 }(i,j))=\frac1{16},
```

```math
P(A_i)=\frac{\text{ }A_i\text{ 中元素的个数}}{\text{可能结果总数}}=\frac4{16},\qquad
P(B_j)=\frac{\text{ }B_j\text{ 中元素的个数}}{\text{可能结果总数}}=\frac4{16}.
```

我们观察到 $P(A_i\cap B_j)=1/16=P(A_i)P(B_j)$，于是 $A_i$ 与 $B_j$ 的独立性得以验证。因此，我们对离散均匀概率律（`discrete uniform probability law`）的选择隐含了两次掷骰工作的独立性。

**(b)** 事件

```math
A=\{第 1 次掷出 1 (1st roll is a 1)\},\qquad B=\{\text{两次点数和为 5 (sum of the two rolls is a 5)}\}
```

是否独立？这里的答案没那么显然。我们有

```math
P(A\cap B)=P(\text{两次掷出的结果是 }(1,4))=\frac1{16},
```

且

```math
P(A)=\frac{\text{}A\text{ 中元素的个数}}{\text{可能结果总数}}=\frac4{16}.
```

事件 $B$ 由结果 (1,4)、(2,3)、(3,2)、(4,1) 组成，且

```math
P(B)=\frac{\text{ }B\text{ 中元素的个数}}{\text{可能结果总数}}=\frac4{16}.
```

于是我们看到 $P(A\cap B)=1/16=P(A)P(B)$，事件 $A$ 与 $B$ 独立。

**(c)** 事件

```math
A=\{\text{两次掷出的最大值是 2 (maximum of the two rolls is 2)}\},\qquad
B=\{\text{两次掷出的最小值是 2 (minimum of the two rolls is 2)}\}
```

是否独立？直觉上答案是"否"，因为两次掷出的最小值泄漏了一些关于最大值的消息。例如，若最小值为 2，则最大值不可能为 1。更严格地说，为验证 $A$ 与 $B$ 不独立，我们计算

```math
P(A\cap B)=P(\text{两次掷出的结果是 }(2,2))=\frac1{16},
```

且

```math
P(A)=\frac{\text{ }A\text{ 中元素的个数}}{\text{可能结果总数}}=\frac3{16},\qquad
P(B)=\frac{\text{ }B\text{ 中元素的个数}}{\text{可能结果总数}}=\frac5{16}.
```

我们有 $P(A)P(B)=\frac{15}{256}\ne\frac{16}{256}=\frac{1}{16}=P(A\cap B)$，所以 $P(A\cap B)\ne P(A)P(B)$，因而 $A$ 与 $B$ 不独立。

最后我们注意到，如前所述，若 $A$ 与 $B$ 独立，则 $B$ 的发生不会为"$A$ 发生的概率"提供任何新信息。自然地，$B$ 的**不发生**也应当不提供关于 $A$ 概率的任何信息。事实上可以验证：若 $A$ 与 $B$ 独立，则 $A$ 与 $B^c$ 也独立（见章末习题）。

## <span style="color:#c0392b;">条件独立（`Conditional Independence`）</span>

我们前面提到，以某一特定事件为条件的事件条件概率，构成一个合法的概率律（`legitimate probability law`）。因此我们可以谈论各事件关于**这个条件概率律**（`conditional law`）的独立性。特别地，给定事件 $G$，事件 $A$ 与 $B$ 被称为**条件独立**（`conditionally independent`），若

```math
P(A\cap B\mid G)=P(A\mid G)P(B\mid G).
```

为导出条件独立的另一种刻画，我们利用条件概率的定义与乘法法则，写出

```math
P(A\cap B\mid G)=\frac{P(A\cap B\cap G)}{P(G)}=\frac{P(G)P(B\mid G)P(A\mid B\cap G)}{P(G)}=P(B\mid G)P(A\mid B\cap G).
```

现在比较上述两个式子，在消去公共因子 $P(B\mid G)$（假设其非零）之后，我们看到条件独立等价于条件

```math
P(A\mid B\cap G)=P(A\mid G).
```

用语言表述，这个关系说的是：若已知 $G$ 已发生，那么"$B$ 也发生了"这一额外知识不会改变 $A$ 的概率。

有意思的是，两个事件 $A$ 与 $B$ 关于（无条件）概率律的独立性，**并不蕴含**条件独立性，反之亦然，如下面两个例子所示。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 条件独立与(无条件)独立互不蕴含，这个"方向性"很容易和直觉打架，需要建立良性的心智模型。核心区别在于：**(无条件)独立**是在"你没有任何额外信息的整个样本空间"上，$B$ 发生与否不改变 $A$ 的概率；**条件独立**则是在"你已经知道 $G$ 发生的缩小的样本空间"上，再知道 $B$ 也不改变 $A$ 的概率——但 $G$ 本身可能已经把"使得 $A$ 与 $B$ 相关的机制"暴露或隐藏了。所谓"缺失变量（`confounder`）"套路：若 $C$ 是一个常见原因，同时驱动 $A$ 和 $B$（比如"选择了蓝硬币"这个 $C$ 同时驱动两次抛硬币的头），那么给定 $C$ 之后 $A,B$ 反而条件独立——因为它们的相关性"全部由 $C$ 解释"，条件化抽掉了相关性来源。相反，例 1.20 从"无条件独立"出发，一旦给定 $D$（两次结果不同）这个**结果**变量，$H_1,H_2$ 反而变得条件相关。这很像你在 6.042J 学过的"两个独立事件在一筛选条件下相互牵连"：独立性命题只在它被声明的那个"样本空间大小"下成立，缩小条件空间会永久改变其真值。这正是信息论里"条件概率改变等号是否成立"的活标本，也是概率论中"非条件成立不代表条件成立"最常见的反直觉来源。

## <span style="color:#2471a3;">**[example] 例 1.20**</span>

考虑两次独立的公平掷硬币（`independent fair coin tosses`），所有四种可能结果等可能。设

```math
H_1=\{第 1 次掷出正面 (1st toss is a head)\},\qquad
H_2=\{第 2 次掷出正面 (2nd toss is a head)\},
```

```math
D=\{\text{两次掷出的结果不同 (the two tosses have different results)}\}.
```

事件 $H_1$ 与 $H_2$（无条件地）独立。但是

```math
P(H_1\mid D)=\frac12,\qquad P(H_1\cap H_2\mid D)=0,
```

从而 $P(H_1\cap H_2\mid D)=0\ne P(H_1\mid D)P(H_2\mid D)$，故 $H_1,H_2$ 并不条件独立。

这个例子可以推广。对任意概率模型，设 $A$ 与 $B$ 独立，并设 $C$ 是满足 $P(C)>0$、$P(A\mid C)>0$、$P(B\mid C)>0$ 的事件，同时 $A\cap B\cap C$ 为空。于是 $A$ 与 $B$ 不可能（在给定 $C$ 之下）条件独立，因为 $P(A\cap B\mid C)=0$ 而 $P(A\mid C)P(B\mid C)>0$。

## <span style="color:#2471a3;">**[example] 例 1.21**</span>

有两枚硬币，一枚蓝色、一枚红色。我们以等概率随机选中其中一枚（每枚被选中的概率为 1/2），然后做两次独立抛掷。这两枚硬币是有偏的（`biased`）：掷蓝色硬币时，任一次抛出正面的概率是 0.99；而掷红色硬币时该概率是 0.01。

设 $B$ 为`选中蓝色硬币`这一事件，并设 $H_i$ 为`第 i 次抛出正面`这一事件。给定硬币的选择，事件 $H_1$ 与 $H_2$ 独立，因为这是我们假设了抛掷独立。于是

```math
P(H_1\cap H_2\mid B)=P(H_1\mid B)P(H_2\mid B)=0.99\cdot0.99.
```

另一方面，事件 $H_1$ 与 $H_2$ 并不独立。直觉上，如果告诉我们第一次抛出了正面，这会使我们怀疑选中的是蓝色硬币，而在此情形下我们会预期第二次也抛正面。数学上，我们用全概率定理得到

```math
P(H_1)=P(B)P(H_1\mid B)+P(B^c)P(H_1\mid B^c)=\frac12\cdot0.99+\frac12\cdot0.01=\frac12,
```

对称性考虑也当如此。类似地，我们有 $P(H_2)=1/2$。现在注意

```math
P(H_1\cap H_2)=P(B)P(H_1\cap H_2\mid B)+P(B^c)P(H_1\cap H_2\mid B^c)
=\frac12\cdot0.99\cdot0.99+\frac12\cdot0.01\cdot0.01\approx\frac12.
```

因此 $P(H_1\cap H_2)\approx1/2\ne P(H_1)P(H_2)=1/4$，事件 $H_1$ 与 $H_2$ 是**相依**（`dependent`）的——尽管它们给定 $B$ 之后是条件独立的。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 例 1.21 是"M形结构"的最干净模型：公共原因 $B$（选中了哪枚硬币）同时驱动 $H_1$ 和 $H_2$。给定 $B$，两个抛掷之间无任何联系，故条件独立；但**不**给定 $B$ 时，两次抛掷通过同一个未知的公共原因锁定在一起，于是表现出正相关——看到第一次是正面，就提示"很可能是蓝硬币"，进而提示第二次也偏正面。这正是"相关性可以完全由第三变量 $B$ 解释"的算术化：相关 ≠ 因果，去掉/加入条件能凭空制造出依赖或独立性。你将来做统计推断或学因果推断（`causal inference`）时，这个"unobserved confounder（未观测的共同原因）"模式是 B 面；而信息论里，$P(H_1,H_2)$ 与 $\sum_B P(B)P(H_1\mid B)P(H_2\mid B)$ 的差别，恰好刻画了"未知的公共原因"贡献了多少互信息。它跟你 18.065 的隐藏因子、Eigen 分解的思想互相呼应，可先用"硬币示例"把"隐藏在共同原因里"这条直觉磨锋利。

我们做如下总结。

<span style="color:#c0392b;">**[boxed-property] 独立性总结（`Independence`）**</span>

- 若 $P(A\cap B)=P(A)P(B)$，则称两个事件 $A$ 与 $B$ **独立**。

- 此外，若 $P(B)>0$，则独立性等价于条件 $P(A\mid B)=P(A)$。

- 若 $A$ 与 $B$ 独立，则 $A$ 与 $B^c$ 也独立。

- 给定另一事件 $G$（且 $P(G)>0$），若 $P(A\cap B\mid G)=P(A\mid G)P(B\mid G)$，则称两个事件 $A$ 与 $B$ **条件独立**。

- 此外，若 $P(B\cap G)>0$，则条件独立等价于条件 $P(A\mid B\cap G)=P(A\mid G)$。

- （无条件）独立性**并不蕴含**条件独立性，反之亦然。

## <span style="color:#c0392b;">一族事件的独立性（`Independence of a Collection of Events`）</span>

独立性的定义可以推广到多个事件。

<span style="color:#00838f;">**[definition] 多个事件的独立性定义（`Definition of Independence of Several Events`)**</span>

若对 $\{1,2,\ldots,n\}$ 的**每个子集**（`every subset`）$S$ 都有

```math
P\left(\bigcap\nolimits_{i\in S} A_i\right)=\prod_{i\in S} P(A_i),
```

则称事件 $A_1,A_2,\ldots,A_n$ **独立**（`independent`）。

对于三个事件 $A_1,A_2,A_3$ 的情形，独立性相当于同时满足以下四个条件：

```math
P(A_1\cap A_2)=P(A_1)P(A_2),
```

```math
P(A_1\cap A_3)=P(A_1)P(A_3),
```

```math
P(A_2\cap A_3)=P(A_2)P(A_3),
```

```math
P(A_1\cap A_2\cap A_3)=P(A_1)P(A_2)P(A_3).
```

> <span style="color:#00838f;">**[definition] 两两独立（`pairwise independence`）**</span>

前三个条件只是断言任意两个事件都独立，这个性质称为**两两独立**（`pairwise independence`）。但第四个条件也很重要，且不能从前三个条件推出。反过来，第四个条件也不蕴含前三个条件；请看下面两个例子。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 事件一族独立的要求，比"任意两个都独立"这一两两独立（`pairwise independence`）强得多：定义要求对**每一个**子集 $S$（包括三元、四元……整族）的概率都能拆成乘积。直观原因是，独立意味着"知道其中任何一部分的信息，对另外任何部分都不构成影响"——这种"整体无信息"只有在所有子集的联合分布都因子分解时才成立。你可以在实分析里看到它的测度论化身：一族随机变量的独立性要求整个乘积 σ-代数上的联合分布等于各边际分布的乘积（`product`），而不仅是两两可乘。例 1.22（两次抛硬币 + $D$）给出的，是"两两独立但三元联合却不因子分解"的最小实例；例 1.23（掷骰子）则展示它另一个方向的失败：三元乘积对，但两两不独立。这两个反例正好说明，独立性是一个"必须逐层核对每个子集"的联合性质，不能指望靠少数几个等式蒙混过关。这也是为什么后面定义**i.i.d.（独立同分布）**随机变量序列时，要对任意有限子列逐一验证。

## <span style="color:#2471a3;">**[example] 例 1.22　两两独立不蕴含独立（`Pairwise Independence does not Imply Independence`）**</span>

考虑两次独立的公平抛硬币，以及如下事件：

```math
H_1=\{第 1 次掷出正面\},\qquad H_2=\{第 2 次掷出正面\},
```

```math
D=\{\text{两次掷出的结果不同}\}.
```

由定义，$H_1$ 与 $H_2$ 独立。为验证 $H_1$ 与 $D$ 独立，我们注意到

```math
P(D\mid H_1)=\frac{P(H_1\cap D)}{P(H_1)}=\frac{1/4}{1/2}=\frac12=P(D).
```

类似地，$H_2$ 与 $D$ 独立。另一方面，我们有

```math
P(H_1\cap H_2\cap D)=0\ne\frac12\cdot\frac12\cdot\frac12=P(H_1)P(H_2)P(D),
```

所以这三个事件并不独立。

## <span style="color:#2471a3;">**[example] 例 1.23　等式 $P(A_1\cap A_2\cap A_3)=P(A_1)P(A_2)P(A_3)$ 不足以保证独立（`The Equality P(A_1nA_2nA_3)=P(A_1)P(A_2)P(A_3) is not Enough for Independence`）**</span>

考虑对均匀六面骰子（`fair six-sided die`）做两次独立掷，以及如下事件：

```math
A=\{\text{第 1 次掷出 1、2 或 3 (1st roll is 1, 2, or 3)}\},
```

```math
B=\{\text{第 1 次掷出 3、4 或 5 (1st roll is 3, 4, or 5)}\},
```

```math
C=\{\text{两次掷出的总和为 9 (the sum of the two rolls is 9)}\}.
```

我们有

```math
P(A\cap B)=\frac16\ne\frac12\cdot\frac12=P(A)P(B),
```

```math
P(A\cap C)=\frac1{36}\ne\frac12\cdot\frac19=P(A)P(C),
```

```math
P(B\cap C)=\frac1{12}\ne\frac12\cdot\frac19=P(B)P(C),
```

而另一方面

```math
P(A\cap B\cap C)=\frac1{36}=\frac12\cdot\frac12\cdot\frac19=P(A)P(B)P(C).
```

也就是说，三事件的交集概率恰好能因子分解，但它们**并不独立**（两两条件已失败）。由此可见"只核对整族乘积"的不足：即使三元乘积成立，两两独立也可能失败，所以独立性的定义必须对每个子集逐一验证。

## <span style="color:#2471a3;">**[example] 例 1.24（串联与并联的可靠性，`Series and Parallel Reliability`）**</span>

考虑一个由若干部件组成的系统，这些部件以**串联**（`series`）与**并联**（`parallel`）方式连接，图中每条链（`link`）旁的数字标示该链正常工作的概率（此处为填补损坏页，按原文结构还原为：部件是否正常相互独立）。若某条**串联**（`series`）连接要求其上的所有部件都正常工作，系统才能工作，则整段串联正常工作的概率等于各部件概率的乘积；若某条**并联**（`parallel`）连接只要其中至少一个部件正常，系统就能工作，则整段并联正常工作的概率等于 1 减去所有部件都失效的概率之积。通过把串联段当作一个整体、并联段当作另一个整体，再嵌套相乘，就可以逐层算出整个系统的可靠性（`reliability`）。

> <span style="color:#1e8449;">**[note] Note（译者注）:**</span>
> 串联/并联可靠性的两条公式，本质是独立性定义的直接应用。串联要求"全部工作"，故 $P(\text{全好})=\prod_{\text{部件}} P(A_i)$，这是独立性定义对整族事件的乘积分解；并联要求"至少一个好"，更好算的是它的对偶事件"全部失效"，于是 $P(\text{至少一个好})=1-\prod_{\text{部件}}(1-P(A_i))$，这正是把"失效"事件族按补事件化、再用独立性拿乘法。注意这两个公式都**默认部件之间独立**，这是它们成立的前提；若部件会一起失效（共因失效，`common-mode failure`），真实可靠性会远低于公式给出的值。这也是为什么工程上强调"冗余"——并联的意义在于即便单个部件不可靠，只要失效彼此独立，系统整体仍能高可靠。这个"独立性假设必须显式声明"的习惯，和你前面学的一切条件概率公式是一致的要求：独立性不是一个可以默认为真的空假设，而是一个需要举证、并随样本空间大小变化而变化的性质。

> <span style="color:#7f8c8d;">BT §1.5, p.33–39</span>

---
*本批次覆盖教材 1.4 节（全概率定理与贝叶斯法则）与 1.5 节（独立性）的主体内容（PDF 页 37–50）。文中补全了源文件损坏（OCR 乱码）之处的数学式，保持了原文的定理、定义、性质与示例编号。*