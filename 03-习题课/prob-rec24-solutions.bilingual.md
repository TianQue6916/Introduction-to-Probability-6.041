<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 24 解答（Recitation 24: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；December 7, 2010，2010 年 12 月 7 日）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）</span>

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span> **(a)** 分布的归一化（normalization）要求：所有可能的 $k$ 值对应的概率之和必须等于 1，即概率质量函数（probability mass function，缩写 PMF）在整个支撑集（support，即取到非零概率的所有 $k$ 的集合）上求和等于 1。于是有
>
> ```math
> 1 = \sum_{k=0}^{\infty} p_K(k;\theta) = \sum_{k=0}^{\infty} \frac{e^{-k/\theta}}{Z(\theta)} = \frac{1}{Z(\theta)} \sum_{k=0}^{\infty} e^{-k/\theta} = \frac{1}{Z(\theta)\cdot\left(1 - e^{-1/\theta}\right)},
> ```
>
> 最后一步用了无穷等比级数（geometric series）求和公式 $\sum_{k=0}^{\infty} r^k = \frac{1}{1-r}$，其中公比（common ratio）$r = e^{-1/\theta}$。由于 $\theta > 0$，有 $0 < e^{-1/\theta} < 1$，级数收敛。因此
>
> ```math
> Z(\theta) = \frac{1}{1 - e^{-1/\theta}}.
> ```
>
> **(b)** 把 $p_K(k;\theta)$ 改写为
>
> ```math
> p_K(k;\theta) = \left(e^{-1/\theta}\right)^k \left(1 - e^{-1/\theta}\right), \quad k = 0, 1, \ldots
> ```
>
> 即可看出：光子数（photon number）的概率分布是一个几何概率分布（geometric probability distribution），成功概率（probability of success）为 $p = 1 - e^{-1/\theta}$。这里要说明"从 0 开始"和"从 1 开始"的区别：若随机变量从 $k = 1$ 开始，几何分布记"直到首次成功共需的试验次数"，概率质量函数为 $(1-p)^{k-1}p$，其期望为 $1/p$；而本题的光子数从 $k = 0$ 开始，记"首次成功之前失败的次数"，概率质量函数为 $(1-p)^k p$，相当于把前一种变量的值整体减 1，故期望也减 1。因此光子数的期望值（mean）为
>
> ```math
> \mu_K = \frac{1}{p} - 1 = \frac{1}{1 - e^{-1/\theta}} - 1 = \frac{1}{e^{1/\theta} - 1},
> ```
>
> 其中最后一步用到 $\frac{1}{1-e^{-1/\theta}} - 1 = \frac{e^{-1/\theta}}{1-e^{-1/\theta}}$，再对分子分母同乘 $e^{1/\theta}$ 得 $\frac{1}{e^{1/\theta}-1}$。其方差（variance）为
>
> ```math
> \sigma_K^2 = \frac{1 - p}{p^2} = \frac{e^{-1/\theta}}{\left(1 - e^{-1/\theta}\right)^2} = \mu_K^2 + \mu_K.
> ```
>
> 其中 $\frac{1-p}{p^2}$ 是几何分布的标准方差公式（平移不改变方差，故"从 0 开始"与"从 1 开始"两种几何分布方差相同）；最后一步 $\frac{e^{-1/\theta}}{(1-e^{-1/\theta})^2} = \mu_K^2 + \mu_K$ 可由 $\mu_K = \frac{e^{-1/\theta}}{1-e^{-1/\theta}}$ 代入验证：$\mu_K^2 + \mu_K = \frac{e^{-2/\theta} + e^{-1/\theta}(1-e^{-1/\theta})}{(1-e^{-1/\theta})^2} = \frac{e^{-1/\theta}}{(1-e^{-1/\theta})^2}$。
>
> **(c)** 各 $k_i$ 的联合概率分布（joint probability distribution）为
>
> ```math
> p_K(k_1, \ldots, k_n; \theta) = \frac{1}{Z(\theta)^n} \prod_{i=1}^{n} e^{-k_i/\theta} = \frac{1}{Z(\theta)^n}\, e^{-\frac{1}{\theta} \sum_{i=1}^{n} k_i}.
> ```
>
> 这里假设各次观测 $k_1, \ldots, k_n$ 相互独立（independent），所以联合分布是各边缘分布（marginal distribution）的乘积，而公共因子 $\frac{1}{Z(\theta)}$ 连乘 $n$ 次得 $\frac{1}{Z(\theta)^n}$。对数似然（log likelihood）为 $-n \log Z(\theta) - \frac{1}{\theta} \sum_{i=1}^{n} k_i$。令其对参数 $\theta$ 的导数为零，以求出对数似然的极大值点。先算 $\log Z(\theta) = -\log\left(1 - e^{-1/\theta}\right)$ 对 $\theta$ 的导数，用链式法则（chain rule）并注意 $\frac{d}{d\theta}e^{-1/\theta} = e^{-1/\theta}\cdot\frac{1}{\theta^2}$：
>
> ```math
> \frac{d}{d\theta} \log Z(\theta) = -\frac{1}{1 - e^{-1/\theta}} \cdot e^{-1/\theta} \cdot \frac{1}{\theta^2} = -\frac{e^{-1/\theta}}{\theta^2\left(1 - e^{-1/\theta}\right)},
> ```
>
> 于是
>
> ```math
> \frac{d}{d\theta} \log p_K(k_1, \ldots, k_n; \theta) = -n \cdot \frac{e^{-1/\theta}}{\theta^2 \left(1 - e^{-1/\theta}\right)} + \frac{1}{\theta^2} \sum_{i=1}^{n} k_i = 0,
> ```
>
> 两边同乘 $\theta^2$、再同除以 $n$，并整理，即
>
> ```math
> \frac{1}{e^{1/\theta} - 1} = \frac{1}{n} \sum_{i=1}^{n} k_i = s_n.
> ```
>
> 这一步用到恒等式 $\frac{e^{-1/\theta}}{1-e^{-1/\theta}} = \frac{1}{e^{1/\theta}-1}$（分子分母同乘 $e^{1/\theta}$）。对灼热物体（hot body），$\theta \gg 1$ 且 $\frac{1}{e^{1/\theta} - 1} \approx \theta$，于是得到
>
> ```math
> \theta \approx \frac{1}{n} \sum_{i=1}^{n} k_i = s_n.
> ```
>
> 这里说明近似 $\frac{1}{e^{1/\theta}-1} \approx \theta$ 的来源：当 $\theta \gg 1$ 时 $1/\theta$ 很小，用一阶泰勒展开（Taylor expansion）$e^{1/\theta} \approx 1 + \frac{1}{\theta}$，代入分母得 $e^{1/\theta}-1 \approx \frac{1}{\theta}$，故 $\frac{1}{e^{1/\theta}-1} \approx \theta$。因此，在此极限下，温度的最大似然估计量（maximum likelihood estimator）$\hat{\Theta}_n$ 由光子数的样本均值（sample mean）给出：

<!-- ===== PDF p2 ===== -->

**（续）**

> ```math
> \hat{\Theta}_n = \frac{1}{n} \sum_{i=1}^{n} K_i.
> ```
>
> **(d)** 根据中心极限定理（central limit theorem），当 $n$ 足够大（取极限）时，样本均值趋近于一个高斯分布（Gaussian distribution）。这里先说明一个关键事实：样本均值 $\hat{\Theta}_n$ 的标准差等于单个观测的标准差除以 $\sqrt{n}$，即 $\sigma_{\hat{\Theta}_n} = \sigma_K/\sqrt{n}$——这是独立同分布变量之和的方差公式 $\mathrm{Var}(\bar{K}) = \mathrm{Var}\!\left(\frac{1}{n}\sum_i K_i\right) = \frac{1}{n^2}\cdot n\,\mathrm{Var}(K) = \frac{\mathrm{Var}(K)}{n}$ 的直接结果。而"估计量的标准差"正是这里所说的均方根误差（root mean square error，缩写 RMSE）：因为估计量 $\hat{\Theta}_n$ 无偏（unbiased），估计误差 $\hat{\Theta}_n - \theta$ 的均值为零，于是误差的均方根 $\sqrt{\mathrm{E}[(\hat{\Theta}_n - \theta)^2]}$ 就等于估计量的标准差。所以有
>
> ```math
> \sigma_{\hat{\Theta}_n} = \frac{\sigma_K}{\sqrt{n}}.
> ```
>
> 要使温度的相对均方根误差仅为 1%，需要 $\frac{\sigma_K}{\sqrt{n}} < 0.01\,\mu_K$。由 $\sigma_K^2 = \mu_K^2 + \mu_K$ 可推得
>
> ```math
> \sqrt{n} > \frac{\sigma_K}{0.01\,\mu_K} = 100\,\frac{\sqrt{\mu_K^2 + \mu_K}}{\mu_K} = 100\sqrt{1 + \frac{1}{\mu_K}}.
> ```
>
> 其中第二步到第三步是：$\frac{\sqrt{\mu_K^2+\mu_K}}{\mu_K} = \sqrt{\frac{\mu_K^2+\mu_K}{\mu_K^2}} = \sqrt{1 + \frac{1}{\mu_K}}$。一般地，对高温情形（即平均光子数 $\mu_K \gg 1$），$\sqrt{1+1/\mu_K} \approx 1$，故 $\sqrt{n} \gtrsim 100$，即大约需要 $100^2 = 10{,}000$ 个样本。
>
> **(e)** 对 (d) 中的情形，即 $\sigma_{\hat{\Theta}_n} = \frac{\sigma_K}{\sqrt{n}} = 0.01\,\mu_K$，温度估计的 95% 置信区间（confidence interval）为
>
> ```math
> \left[\hat{K} - 1.96\,\sigma_{\hat{K}},\; \hat{K} + 1.96\,\sigma_{\hat{K}}\right] = \left[\hat{K} - 0.0196\,\mu_K,\; \hat{K} + 0.0196\,\mu_K\right].
> ```
>
> 这里说明记号：区间里的 $\hat{K}$ 就是前面的样本均值估计量 $\hat{\Theta}_n = \frac{1}{n}\sum_{i=1}^{n} K_i$（原解答在此处改用 $\hat{K}$ 表示），$\sigma_{\hat{K}}$ 就是 $\sigma_{\hat{\Theta}_n} = \sigma_K/\sqrt{n}$。系数 $1.96$ 是标准正态分布（standard normal distribution）的 97.5% 分位点（quantile），对应 95% 的置信水平；故 $1.96 \times 0.01\,\mu_K = 0.0196\,\mu_K$。

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">[solution]</span> **(a)** 利用 9.2 节的回归公式（regression formulas），有
>
> ```math
> \hat{\theta}_1 = \frac{\sum_{i=1}^{5} (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{5} (x_i - \bar{x})^2}, \qquad \hat{\theta}_0 = \bar{y} - \hat{\theta}_1 \bar{x},
> ```
>
> 这里先补上"9.2 节回归公式"的来龙去脉，读者若没读到那一节也不会卡住：这是对线性模型 $y = \theta_0 + \theta_1 x$ 做最小二乘（least squares）估计的结果。最小二乘的目标是选 $\theta_0, \theta_1$ 使残差平方和（sum of squared residuals）$\sum_{i=1}^{n}\left(y_i - \theta_0 - \theta_1 x_i\right)^2$ 达到最小；对 $\theta_0$、$\theta_1$ 分别求偏导并令其为零，即可解得上面这两个公式——斜率（slope）$\hat{\theta}_1$ 是样本协方差除以样本方差（$\frac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})^2}$，即协方差 covariance 与方差 variance 之比），截距（intercept）$\hat{\theta}_0$ 由 $\bar{y} - \hat{\theta}_1 \bar{x}$ 给出（保证回归直线通过点 $(\bar{x}, \bar{y})$）。其中
>
> ```math
> \bar{x} = \frac{1}{5} \sum_{i=1}^{5} x_i = 4.94, \qquad \bar{y} = \frac{1}{5} \sum_{i=1}^{5} y_i = 134.38.
> ```
>
> 由此得到的最大似然（maximum likelihood，缩写 ML）估计为
>
> ```math
> \hat{\theta}_1 = 40.53, \qquad \hat{\theta}_0 = -65.86.
> ```
>
> **(b)** 采用与 (a) 相同的步骤，可得
>
> ```math
> \hat{\theta}_1 = \frac{\sum_{i=1}^{5} (x_i^2 - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{5} (x_i^2 - \bar{x})^2}, \qquad \hat{\theta}_0 = \bar{y} - \hat{\theta}_1 \bar{x},
> ```

<!-- ===== PDF p3 ===== -->

**（续）**

> 其中
>
> ```math
> \bar{x} = \frac{1}{5} \sum_{i=1}^{5} x_i^2 = 33.60, \qquad \bar{y} = \frac{1}{5} \sum_{i=1}^{5} y_i = 134.38,
> ```
>
> 这里说明一下记号：在 (b) 中我们把二次模型 $y = \theta_0 + \theta_1 x^2$ 里的"自变量"取成 $x^2$ 本身，于是上面的 $\bar{x}$ 其实表示的是 $\overline{x^2} = \frac{1}{5}\sum_{i=1}^{5} x_i^2$（即 $x_i^2$ 的样本均值，值 $33.60$），而不再是 (a) 中 $x_i$ 的均值 $4.94$——把 $x^2$ 当作一个新的自变量 $u$ 后，套用与 (a) 完全相同的线性回归公式即可。对给定数据，由此算得
>
> ```math
> \hat{\theta}_1 = 4.09, \qquad \hat{\theta}_0 = -3.07.
> ```
>
> 图 1（Figure 1）给出了数据点 $(x_i, y_i)$，$i = 1, \ldots, 5$、估计出的线性模型（linear model）
>
> ```math
> y = 40.53\,x - 65.86,
> ```
>
> 以及估计出的二次模型（quadratic model）
>
> ```math
> y = 4.09\,x^2 - 3.07.
> ```
>
> <span style="color:#7f8c8d;">【图】原页此处为图 1：回归图（Figure 1: Regression Plot）——数据点（Sample data points）、估计的一阶模型（Estimated first-order model）与估计的二阶模型（Estimated second-order model）三条曲线，纵轴 Y 范围约 −100 至 500，横轴 X 范围约 0 至 12。原图由后处理统一插入。</span>
>
> <span style="color:#1e8449;">[note] 原解答 PDF 中"二次模型"之后的公式紧邻图形、未被文本层提取；上式 $y = 4.09\,x^2 - 3.07$ 依据本课配套题目版（Recitation 24 题目 PDF）及 (b) 的估计值 $\hat{\theta}_1 = 4.09$、$\hat{\theta}_0 = -3.07$ 补出。</span>

<span style="color:#7f8c8d;">†6.431 必做；6.041 选做（Required for 6.431; optional for 6.041）。第 3 页，共 3 页（Page 3 of 3）　Image by MIT OpenCourseWare.（图片由 MIT OpenCourseWare 提供）</span>

<!-- ===== PDF p4 ===== -->

<span style="color:#7f8c8d;">**MIT OpenCourseWare**（MIT 开放课件）　http://ocw.mit.edu　6.041 / 6.431 概率系统分析与应用概率（Probabilistic Systems Analysis and Applied Probability），Fall 2010（2010 秋季学期）。关于引用这些材料或使用条款（Terms of Use）的信息，请访问：http://ocw.mit.edu/terms。</span>
