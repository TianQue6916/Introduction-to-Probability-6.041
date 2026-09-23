<!-- ===== PDF p1 ===== -->

<span style="color:#c0392b;">**6.041 / 6.431　概率系统分析（Probabilistic Systems Analysis）**</span>

<span style="color:#c0392b;">**Recitation 24 解答（Recitation 24: Solutions）**</span> <span style="color:#7f8c8d;">（Fall 2010，2010 秋季学期；December 7, 2010，2010 年 12 月 7 日）</span>

<span style="color:#7f8c8d;">麻省理工学院（Massachusetts Institute of Technology）电气工程与计算机科学系（Department of Electrical Engineering & Computer Science）</span>

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 1**</span>

> <span style="color:#2471a3;">[solution]</span> **(a)** 分布的归一化（normalization）要求：
>
> ```math
> 1 = \sum_{k=0}^{\infty} p_K(k;\theta) = \sum_{k=0}^{\infty} \frac{e^{-k/\theta}}{Z(\theta)} = \frac{1}{Z(\theta)} \sum_{k=0}^{\infty} e^{-k/\theta} = \frac{1}{Z(\theta)\cdot\left(1 - e^{-1/\theta}\right)},
> ```
>
> 因此
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
> 即可看出：光子数（photon number）的概率分布是一个几何概率分布（geometric probability distribution），成功概率（probability of success）为 $p = 1 - e^{-1/\theta}$；由于它从 $k = 0$ 开始，相当于整体向左平移了 1。因此光子数的期望值为
>
> ```math
> \mu_K = \frac{1}{p} - 1 = \frac{1}{1 - e^{-1/\theta}} - 1 = \frac{1}{e^{1/\theta} - 1},
> ```
>
> 其方差为
>
> ```math
> \sigma_K^2 = \frac{1 - p}{p^2} = \frac{e^{-1/\theta}}{\left(1 - e^{-1/\theta}\right)^2} = \mu_K^2 + \mu_K.
> ```
>
> **(c)** 各 $k_i$ 的联合概率分布（joint probability distribution）为
>
> ```math
> p_K(k_1, \ldots, k_n; \theta) = \frac{1}{Z(\theta)^n} \prod_{i=1}^{n} e^{-k_i/\theta} = \frac{1}{Z(\theta)^n}\, e^{-\frac{1}{\theta} \sum_{i=1}^{n} k_i}.
> ```
>
> 对数似然（log likelihood）为 $-n \log Z(\theta) - \frac{1}{\theta} \sum_{i=1}^{n} k_i$。令其对参数 $\theta$ 的导数为零，以求出对数似然的极大值点：
>
> ```math
> \frac{d}{d\theta} \log p_K(k_1, \ldots, k_n; \theta) = -n \cdot \frac{e^{-1/\theta}}{\theta^2 \left(1 - e^{-1/\theta}\right)} + \frac{1}{\theta^2} \sum_{i=1}^{n} k_i = 0,
> ```
>
> 即
>
> ```math
> \frac{1}{e^{1/\theta} - 1} = \frac{1}{n} \sum_{i=1}^{n} k_i = s_n.
> ```
>
> 对灼热物体（hot body），$\theta \gg 1$ 且 $\frac{1}{e^{1/\theta} - 1} \approx \theta$，于是得到
>
> ```math
> \theta \approx \frac{1}{n} \sum_{i=1}^{n} k_i = s_n.
> ```
>
> 因此，在此极限下，温度的最大似然估计量（maximum likelihood estimator）$\hat{\Theta}_n$ 由光子数的样本均值（sample mean）给出：

<!-- ===== PDF p2 ===== -->

**（续）**

> ```math
> \hat{\Theta}_n = \frac{1}{n} \sum_{i=1}^{n} K_i.
> ```
>
> **(d)** 根据中心极限定理（central limit theorem），当 $n$ 足够大（取极限）时，样本均值趋近于一个高斯分布（Gaussian distribution），其标准差就是我们的均方根误差（root mean square error）
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
> 一般地，对高温情形（即平均光子数 $\mu_K \gg 1$），大约需要 10,000 个样本。
>
> **(e)** 对 (d) 中的情形，即 $\sigma_{\hat{\Theta}_n} = \frac{\sigma_K}{\sqrt{n}} = 0.01\,\mu_K$，温度估计的 95% 置信区间（confidence interval）为
>
> ```math
> \left[\hat{K} - 1.96\,\sigma_{\hat{K}},\; \hat{K} + 1.96\,\sigma_{\hat{K}}\right] = \left[\hat{K} - 0.0196\,\mu_K,\; \hat{K} + 0.0196\,\mu_K\right].
> ```

---

<span style="color:#2471a3;">[problem]</span> <span style="color:#c0392b;">**Problem 2**</span>

> <span style="color:#2471a3;">[solution]</span> **(a)** 利用 9.2 节的回归公式（regression formulas），有
>
> ```math
> \hat{\theta}_1 = \frac{\sum_{i=1}^{5} (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{5} (x_i - \bar{x})^2}, \qquad \hat{\theta}_0 = \bar{y} - \hat{\theta}_1 \bar{x},
> ```
>
> 其中
>
> ```math
> \bar{x} = \frac{1}{5} \sum_{i=1}^{5} x_i = 4.94, \qquad \bar{y} = \frac{1}{5} \sum_{i=1}^{5} y_i = 134.38.
> ```
>
> 由此得到的最大似然（ML）估计为
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
> 对给定数据，由此算得
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
