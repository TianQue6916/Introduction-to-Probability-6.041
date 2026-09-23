<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Problem Set 11 解答（Problem Set 11: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期）</span>

<span style="color:#7f8c8d;">Massachusetts Institute of Technology（麻省理工学院）· Department of Electrical Engineering & Computer Science（电气工程与计算机科学系）</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">**[solution]**</span> 本题解答见教材配套习题解答（Check book solutions，即查阅书中所附答案）。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 为求 MAP 估计（MAP estimate），需要找出使条件密度（conditional density）$f_{X|Y}(x\mid y)$ 最大的 $x$ 值：对其求导并令导数为零。
>
> ```math
> f_{X|Y}(x\mid y)=\frac{p_{Y|X}(y\mid x)\cdot f_X(x)}{p_Y(y)}
> =\frac{\mu e^{-\mu x}\cdot\dfrac{x^{y}}{y!}\cdot e^{-x}}{p_Y(y)}
> =\frac{\mu\, x^{y}\, e^{-(\mu+1)x}}{y!\,p_Y(y)},
> ```
>
> ```math
> \frac{d}{dx}f_{X|Y}(x\mid y)=\frac{\mu}{y!\,p_Y(y)}\cdot\frac{d}{dx}\left[x^{y}e^{-(\mu+1)x}\right]
> =\frac{\mu\, x^{y-1}e^{-(\mu+1)x}\left(y-x(\mu+1)\right)}{y!\,p_Y(y)}.
> ```
>
> 由于在依赖 $x$ 的各因子中，唯一能取零值的因子是 $(y-x(\mu+1))$，故最大值在
>
> ```math
> \hat{x}_{\mathrm{MAP}}(y)=\frac{y}{1+\mu}
> ```
>
> 处取得。容易验证该值确实是最大值（一阶导数在该点处由正变负）。
>
> **(b)**
>
> **i.** 为证明所给恒等式，需要使用贝叶斯法则（Bayes' rule）。我们先计算分母 $p_Y(y)$：
>
> ```math
> p_Y(y)=\int_0^{\infty}\mu e^{-\mu x}\,\frac{e^{-x}x^{y}}{y!}\,dx
> =\frac{\mu}{y!\,(1+\mu)^{y+1}}\int_0^{\infty}(1+\mu)^{y+1}x^{y}e^{-(1+\mu)x}\,dx
> =\frac{\mu}{(1+\mu)^{y+1}}.
> ```
>
> 然后把它代入 (a) 中已导出的表达式：
>
> ```math
> f_{X|Y}(x\mid y)=\frac{\mu\, x^{y}e^{-(\mu+1)x}}{y!\,p_Y(y)}
> =\frac{\mu\, x^{y}e^{-(\mu+1)x}}{y!}\cdot\frac{(1+\mu)^{y+1}}{\mu}
> =\frac{(1+\mu)^{y+1}x^{y}e^{-(\mu+1)x}}{y!}.
> ```
>
> 因此 $\lambda=1+\mu$。
>
> <span style="color:#1e8449;">**[mathtip]**</span> 所得后验密度 $f_{X|Y}(x\mid y)$ 恰为参数 $\lambda=1+\mu$ 的指数分布（Exponential）密度，故 $\lambda=1+\mu$。

<!-- ===== PDF p2 ===== -->

**（续）** Problem 2（解答续）

> **ii.** 先对 $x\,f_{X|Y}(x\mid y)$ 进行变形：
>
> ```math
> x\,f_{X|Y}(x\mid y)=\frac{(1+\mu)^{y+1}}{y!}\,x^{y+1}e^{-(\mu+1)x}
> =\frac{y+1}{1+\mu}\cdot\frac{(1+\mu)^{y+2}}{(y+1)!}\,x^{y+1}e^{-(\mu+1)x}
> =\frac{y+1}{1+\mu}\,f_{X|Y}(x\mid y+1).
> ```
>
> 于是可求条件期望估计器（conditional expectation estimator）：
>
> ```math
> \hat{x}_{\mathrm{CE}}(y)=E[X\mid Y=y]=\int_0^{\infty}x\,f_{X|Y}(x\mid y)\,dx
> =\frac{y+1}{1+\mu}\int_0^{\infty}f_{X|Y}(x\mid y+1)\,dx=\frac{y+1}{1+\mu}.
> ```
>
> **(c)** 条件期望估计器总是比 MAP 估计器大 $\dfrac{1}{1+\mu}$。

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 3**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 似然函数（likelihood function）为
>
> ```math
> \prod_{i=1}^{k}P_{T_i}(T_i=t_i\mid Q=q)=q^{k}(1-q)^{\sum_{i=1}^{k}t_i-k}.
> ```
>
> 为使上述概率最大化，对其关于 $q$ 求导并令其为零：
>
> ```math
> kq^{k-1}(1-q)^{\sum_i t_i-k}-\Big(\sum_i t_i-k\Big)q^{k}(1-q)^{\sum_i t_i-k-1}=0,
> ```
>
> 等价地，
>
> ```math
> k(1-q)-\Big(\sum_i t_i-k\Big)q=0,
> ```
>
> 由此解得 $\hat{Q}_b=\dfrac{k}{\sum_{i=1}^{k}t_i}$。这与之前求得的 MAP 估计并无不同。由于 MAP 估计是在均匀先验（uniform prior）下计算的，似然函数是后验概率的一个“缩放（scaled）”版本，二者会在相同的 $q$ 值处取得最大。
>
> **(b)** 由于 $\dfrac{1}{\hat{Q}_b}=\dfrac{1}{k}\sum_{i=1}^{k}T_i$，且各 $T_i$ 独立同分布，可知 $\dfrac{1}{\hat{Q}_b}$ 实际上就是一个样本均值估计器（sample mean estimator）。弱大数定律（weak law of large numbers）指出：当样本数增至无穷时，样本均值估计器收敛到真实均值，在本题中即 $1/q^{*}$。于是可将该概率的极限写为
>
> ```math
> \lim_{k\to\infty}P\left(\left|\frac{1}{\hat{Q}_b}-\frac{1}{q^{*}}\right|>\epsilon\right)
> =\lim_{k\to\infty}P\left(\left|\frac{1}{k}\sum_{i=1}^{k}T_i-E[T_1]\right|>\epsilon\right)=0.
> ```

<!-- ===== PDF p3 ===== -->

**（续）** Problem 3（解答续）

> **(c)** 切比雪夫不等式（Chebyshev inequality）给出
>
> ```math
> P\left(\left|\frac{1}{k}\sum_{i=1}^{k}T_i-E[T_1]\right|\geq\epsilon\right)\leq\frac{\mathrm{var}(T_1)}{k\epsilon^{2}}.
> ```
>
> 于是
>
> ```math
> P\left(\left|\frac{1}{\hat{Q}_b}-\frac{1}{q^{*}}\right|\leq 0.1\right)
> =P\left(\left|\frac{1}{k}\sum_{i=1}^{k}T_i-E[T_1]\right|\leq 0.1\right)
> =1-P\left(\left|\frac{1}{k}\sum_{i=1}^{k}T_i-E[T_1]\right|\geq 0.1\right)
> \geq 1-\frac{\mathrm{var}(T_1)}{k\cdot 0.1^{2}}.
> ```
>
> 要使上述概率大于 $0.95$，需要
>
> ```math
> 1-\frac{\mathrm{var}(T_1)}{k\cdot 0.1^{2}}
> =1-\frac{(1-q)/q^{2}}{k\cdot 0.1^{2}}\geq 0.95,
> ```
>
> 即
>
> ```math
> k\geq 2000\,\mathrm{var}(T_1)=2000\,\frac{1-q}{q^{2}}.
> ```
>
> 所需观测数 $k$ 取决于 $T_1$ 的方差。当 $q$ 接近 $1$ 时，方差接近 $0$，所需观测数非常小（接近 $0$）。当 $q=1/2$ 时，方差最大（$\mathrm{var}(T_1)=2$），此时需要 $k=4000$。因此，为保证对一切 $q$ 都达到所需的精度与置信度，需要
>
> ```math
> k\geq 4000.
> ```
>
> <span style="color:#7f8c8d;">**[note]** 译者注：几何分布方差 $(1-q)/q^{2}$ 关于 $q$ 单调递减，“$q=1/2$ 时方差最大”应在题目允许的参数范围（$q\ge 1/2$）内理解。</span>

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 4**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 分布的归一化（normalization）要求：
>
> ```math
> 1=\sum_{k=0}^{\infty}p_K(k;\theta)=\sum_{k=0}^{\infty}\frac{1}{Z(\theta)}\,e^{-k/\theta}
> =\frac{1}{Z(\theta)}\cdot\frac{1}{1-e^{-1/\theta}},
> ```
>
> 所以 $Z(\theta)=\dfrac{1}{1-e^{-1/\theta}}$。
>
> **(b)** 把 $p_K(k;\theta)$ 改写为
>
> ```math
> p_K(k;\theta)=\left(1-e^{-1/\theta}\right)\cdot\left(e^{-1/\theta}\right)^{k},\qquad k=0,1,\ldots
> ```
>
> 可见光子数（photon number）的概率分布是一个几何分布（geometric distribution），成功概率（probability of success）为 $p=1-e^{-1/\theta}$；且由于它从 $k=0$ 开始，相当于向左平移了 $1$。因此光子数的期望值为
>
> ```math
> \mu_K=\frac{1}{p}-1=\frac{1}{1-e^{-1/\theta}}-1=\frac{1}{e^{1/\theta}-1},
> ```
>
> 方差为
>
> ```math
> \sigma_K^{2}=\frac{1-p}{p^{2}}=\frac{e^{-1/\theta}}{\left(1-e^{-1/\theta}\right)^{2}}=\mu_K^{2}+\mu_K.
> ```

<!-- ===== PDF p4 ===== -->

**（续）** Problem 4（解答续）

> **(c)** 各 $k_i$ 的联合概率分布（joint probability distribution）为
>
> ```math
> p_K(k_1,\ldots,k_n;\theta)=\prod_{i=1}^{n}\frac{1}{Z(\theta)}\,e^{-k_i/\theta}
> =\frac{1}{Z(\theta)^{n}}\cdot e^{-\frac{1}{\theta}\sum_{i=1}^{n}k_i}.
> ```
>
> 对数似然（log likelihood）为
>
> ```math
> \log p_K(k_1,\ldots,k_n;\theta)=-\frac{1}{\theta}\sum_{i=1}^{n}k_i-n\log Z(\theta).
> ```
>
> 通过对参数 $\theta$ 求导并令其为零来求对数似然的最大值点：
>
> ```math
> \frac{d}{d\theta}\log p_K(k_1,\ldots,k_n;\theta)
> =\frac{1}{\theta^{2}}\sum_{i=1}^{n}k_i-n\cdot\frac{e^{-1/\theta}}{\theta^{2}\left(1-e^{-1/\theta}\right)}=0,
> ```
>
> 或者等价地，记 $\sum_{i=1}^{n}k_i=s_n$，则 $\dfrac{s_n}{n}=\dfrac{1}{e^{1/\theta}-1}$。当 $e^{1/\theta}-1\approx 1/\theta$ 时即得 $\dfrac{s_n}{n}\approx\theta$。对热体（hot body）而言，$\theta\gg 1$ 且 $e^{1/\theta}\approx 1+1/\theta$。因此，温度的极大似然估计器（maximum likelihood estimator）$\hat{\Theta}_n$ 在此极限下由光子数的样本均值给出：
>
> ```math
> \hat{\Theta}_n=\frac{1}{n}\sum_{i=1}^{n}K_i.
> ```
>
> <span style="color:#7f8c8d;">**[note]** 原页此段多行分式与求和式存在提取噪声（分数被竖排拆行、求和上下限错位），已按对数似然极大化的推导还原，数学内容与原文一致。</span>
>
> **(d)** 根据中心极限定理（central limit theorem），样本均值在 $n$ 较大时近似服从高斯分布（Gaussian distribution），其标准差（即我们的均方根误差，root mean square error）为
>
> ```math
> \sigma_{\hat{\Theta}_n}=\frac{\sigma_K}{\sqrt{n}}.
> ```
>
> 要使温度的相对均方根误差只有 $1\%$，需要 $\dfrac{\sigma_K}{\sqrt{n}}<0.01\mu_K$。结合 $\sigma_K^{2}=\mu_K^{2}+\mu_K$ 可得
>
> ```math
> \sqrt{n}>\frac{\sigma_K}{0.01\mu_K}=100\cdot\frac{\sqrt{\mu_K^{2}+\mu_K}}{\mu_K}=100\sqrt{1+\frac{1}{\mu_K}}.
> ```
>
> 一般地，对于高温（即平均光子数 $\mu_K\gg 1$）的情形，大约需要 10,000 个样本。
>
> **(e)** (d) 中情形（即 $\sigma_{\hat{\Theta}_n}=\sigma_K/\sqrt{n}=0.01\mu_K$）下，温度估计的 95% 置信区间（confidence interval）为
>
> ```math
> \left[\hat{K}-1.96\sigma_{\hat{K}},\ \hat{K}+1.96\sigma_{\hat{K}}\right]
> =\left[\hat{K}-0.0196\mu_K,\ \hat{K}+0.0196\mu_K\right].
> ```

<!-- ===== PDF p5 ===== -->

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 5**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 样本均值估计器 $\hat{\Theta}_n=\dfrac{W_1+\cdots+W_n}{n}$ 在本情形下为
>
> ```math
> \hat{\Theta}_{1000}=\frac{2340}{1000}=2.34.
> ```
>
> 由标准正态表（standard normal table）知 $\Phi(1.96)=0.975$，于是
>
> ```math
> P\left(\frac{\left|\hat{\Theta}_{1000}-\mu\right|}{\sqrt{\mathrm{var}(W_i)/1000}}\leq 1.96\right)\approx 0.95.
> ```
>
> 由于方差小于 4，有
>
> ```math
> P\left(\left|\hat{\Theta}_{1000}-\mu\right|\leq 1.96\sqrt{\mathrm{var}(W_i)/1000}\right)
> \leq P\left(\left|\hat{\Theta}_{1000}-\mu\right|\leq 1.96\sqrt{4/1000}\right),
> ```
>
> 令上式右端 $\approx 0.95$ 即得 95% 置信，亦即区间
>
> ```math
> \left[\hat{\Theta}_{1000}-1.96\sqrt{4/1000},\ \hat{\Theta}_{1000}+1.96\sqrt{4/1000}\right]
> =\left[\hat{\Theta}_{1000}-0.124,\ \hat{\Theta}_{1000}+0.124\right]
> =\left[2.216,\ 2.464\right].
> ```
>
> <span style="color:#7f8c8d;">**[note]** 原文此处写作 “the variance is less that 4”，系 “less than 4（小于 4）” 之笔误。</span>
>
> **(b)** 似然函数为
>
> ```math
> f_W(w;\theta)=\prod_{i=1}^{n}f_{W_i}(w_i;\theta)=\prod_{i=1}^{n}\theta e^{-\theta w_i},
> ```
>
> 对数似然函数为
>
> ```math
> \log f_W(w;\theta)=n\log\theta-\theta\sum_{i=1}^{n}w_i,
> ```
>
> 它关于 $\theta$ 的导数为 $\dfrac{n}{\theta}-\sum_{i=1}^{n}w_i$。令其为零，可知 $\log f_W(w;\theta)$ 在 $\theta\ge 0$ 上的最大值在 $\hat{\theta}_n=\dfrac{n}{\sum_{i=1}^{n}w_i}$ 处取得。所得估计器为
>
> ```math
> \hat{\Theta}_n^{\mathrm{mle}}=\frac{n}{\sum_{i=1}^{n}W_i}.
> ```
>
> 在本情形下，
>
> ```math
> \hat{\Theta}^{\mathrm{mle}}=\frac{1000}{2340}=0.4274.
> ```

---

<span style="color:#2471a3;">**[problem]**</span> <span style="color:#c0392b;">**Problem 6**</span>

> <span style="color:#2471a3;">**[solution]**</span>
>
> **(a)** 利用 9.2 节的回归（regression）公式，有
>
> ```math
> \hat{\theta}_1=\frac{\sum_{i=1}^{5}(x_i-\bar{x})(y_i-\bar{y})}{\sum_{i=1}^{5}(x_i-\bar{x})^{2}},
> \qquad
> \hat{\theta}_0=\bar{y}-\hat{\theta}_1\bar{x},
> ```
>
> 其中
>
> ```math
> \bar{x}=\frac{1}{5}\sum_{i=1}^{5}x_i=4.94,
> \qquad
> \bar{y}=\frac{1}{5}\sum_{i=1}^{5}y_i=134.38.
> ```
>
> 由此得到的 ML 估计为
>
> ```math
> \hat{\theta}_1=40.53,
> \qquad
> \hat{\theta}_0=-65.86.
> ```

<!-- ===== PDF p6 ===== -->

**（续）** Problem 6（解答续）

> **(b)** 采用与 (a) 相同的步骤，得
>
> ```math
> \hat{\theta}_1=\frac{\sum_{i=1}^{5}(x_i^{2}-\overline{x^{2}})(y_i-\bar{y})}{\sum_{i=1}^{5}(x_i^{2}-\overline{x^{2}})^{2}},
> \qquad
> \hat{\theta}_0=\bar{y}-\hat{\theta}_1\,\overline{x^{2}},
> ```
>
> 其中
>
> ```math
> \overline{x^{2}}=\frac{1}{5}\sum_{i=1}^{5}x_i^{2}=33.60,
> \qquad
> \bar{y}=\frac{1}{5}\sum_{i=1}^{5}y_i=134.38.
> ```
>
> 对所给数据即得
>
> ```math
> \hat{\theta}_1=4.09,
> \qquad
> \hat{\theta}_0=-3.07.
> ```
>
> 图 1 展示了数据点 $(x_i,\,y_i),\ i=1,\ldots,5$、估计出的线性模型
>
> ```math
> y=40.53x-65.86,
> ```
>
> 以及估计出的二次模型
>
> ```math
> y=4.09x^{2}-3.07.
> ```

<span style="color:#7f8c8d;">【图】原页此处为回归散点图（Figure 1: Regression Plot），展示 5 个数据点 $(x_i,y_i)$、拟合线性模型 $y=40.53x-65.86$ 与二次模型 $y=4.09x^{2}-3.07$。原图由后处理统一插入。</span>

<!-- ===== PDF p7 ===== -->

<span style="color:#7f8c8d;">MIT OpenCourseWare　http://ocw.mit.edu</span>

<span style="color:#7f8c8d;">6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）</span>

<span style="color:#7f8c8d;">有关引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms</span>
