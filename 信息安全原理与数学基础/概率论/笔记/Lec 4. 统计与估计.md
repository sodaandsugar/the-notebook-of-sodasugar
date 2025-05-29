# Lec 4. 统计与估计
## 1 基本概念
* 样本均值（Sample Mean）
  * 针对独立同分布变量而言
  * $M_n(X)=\frac{X_1+\cdots + X_n}{n}$
  * 样本均值不等于期望，随着 $n$ 的增加，$M_n(X)$ 趋近于 $E[X]$
  * $E[M_n(X)] = E[X]$
  * $\text{Var}[M_n(X)]=\frac{\text{Var}[X]}{n}$
* 模型参数（Model Parameter）
  * 对于任意事件 $A$，$P[A]$ 是一个模型参数
* 模型参数的估计（Estimates of Model Parameters）
  * 考虑对随机变量X样本值的观测实验。观测值是$X_1, X_2, \ldots$的样本，与X同概率模型。
  * 设 $r$ 为概率模型参数，用 $X_1, X_2, \ldots$ 生成 $r$ 的估计值序列 $\hat{R}_1, \hat{R}_2, \ldots$ ，它们是随机变量。
  * $\hat{R}_1$是$X_1$函数，$\hat{R}_2$是$X_1$、$X_2$函数，$\hat{R}_n$是$X_1, \ldots, X_n$函数。  
* 对方差的估计（Estimating the Variance）
  * 当$E[X]$为已知量$\mu_X$时
    * $\text{Var}[X] = E[(X - \mu_X)^2]$ 
    * 此时可以用 $W = (X - \mu_X)^2$ 的样本均值来估计$\text{Var}[X]$ ，即：\(M_n(W)=\frac{1}{n}\sum_{i = 1}^{n}(X_i - \mu_X)^2\)，
    * 若 $\text{Var}[W]$ 存在，$M_n(W)$ 是 $\text{Var}[X]$ 的一致无偏估计量
  * 当期望值 $\mu_X$ 未知时
    * 用样本均值 $M_n(X)$ 来代替期望值 $\mu_X$ 
* 一致估计量（Consistent Estimator）
  * 对于任意 $\epsilon > 0$ ，有 $\lim\limits_{n \to \infty} P[|\hat{R}_n - r| \geq \epsilon] = 0$ 
  * 若 $X$ 具有有限方差，那么样本均值 $M_n(X)$ 是 $E[X]$ 的一致估计量序列
* 无偏估计量（Unbiased Estimator）
  * $E[\hat{R}] = r$
  * 样本均值$M_n(X)$ 是$E[X]$ 的无偏估计量
  * \(V'_n(X)=\frac{1}{n - 1}\sum_{i = 1}^{n}(X_i - M_n(X))^2\) 是总体方差$\text{Var}[X]$ 的无偏估计量
  * 当 $\hat{R}_n$ 是无偏估计量且满足$\lim\limits_{n \to \infty} \text{Var}[\hat{R}_n] = 0$ 时，$\hat{R}_n$是一致估计量
* 有偏估计量（Biased Estimator）
  * $E[\hat{R}] \neq  r$
* 渐近无偏估计量（Asymptotically Unbiased Estimator）
  * $\lim\limits_{n \to \infty} E[\hat{R}_n] = r$
* 均方误差（Mean Square Error）
  * $e = E[(\hat{R} - r)^2]$ 
  * 样本均值估计量 $M_n(X)$ 的均方误差 \(e_n = E[(M_n(X) - E[X])^2] = \text{Var}[M_n(X)] = \frac{\text{Var}[X]}{n}\)
* 标准差（Standard Error）
  - $\sqrt{e_n}$
  - 当 $X$ 是高斯随机变量且 $M_n(X)$ 也是高斯随机变量时：
  \[P[E[X] - \sqrt{e_n} \leq M_n(X) \leq E[X] + \sqrt{e_n}] = 2\Phi(1) - 1 \approx 0.68 \] 
  - 当 $n$ 很大且根据中心极限定理 $M_n(X)$ 近似为高斯分布时，上述结论也近似成立
* 样本方差（Sample Variance）
  * $V_n(X)=\frac{1}{n}\sum\limits_{i = 1}^{n}(X_i - M_n(X))^2$
  * $E[V_n(X)] = \frac{n - 1}{n}\text{Var}[X]$
>**证明过程**
\[
\begin{align*}
V_n(X)&=\frac{1}{n}\sum_{i = 1}^{n}(X_i - M_n(X))^2\\&=\frac{1}{n}\sum_{i = 1}^{n}X_i^2 - \frac{1}{n^2}\sum_{i = 1}^{n}\sum_{j = 1}^{n}X_iX_j
\end{align*}
\]\[
\begin{align*}
E[V_n]&=E[X^2] - \frac{1}{n^2}\sum_{i = 1}^{n}\sum_{j = 1}^{n}(\text{Cov}[X_i,X_j] + \mu_X^2)\\
&=\text{Var}[X] - \frac{1}{n^2}\sum_{i = 1}^{n}\sum_{j = 1}^{n}\text{Cov}[X_i,X_j]\\
&=\text{Var}[X] - \frac{1}{n^2}(n\text{Var}[X])\\
&=\frac{n - 1}{n}\text{Var}[X]
\end{align*}
\]
## 2 重要不等式
### 2. 1 马尔可夫不等式（Markov Inequality）
* 对于随机变量$X$，满足$P[X < 0]=0$ ，以及常数$c$ ，有：
\[P[X\geq c^2]\leq\frac{E[X]}{c^2}\]
* 给出了非负随机变量大于等于某个正数的概率的上界，在概率论中用于对随机变量的尾概率进行估计
> **证明**：
$E[X]=\int_{-\infty}^{\infty}xf_X(x)dx=\int_{0}^{c^2}xf_X(x)dx+\int_{c^2}^{\infty}xf_X(x)dx\geq\int_{c^2}^{\infty}xf_X(x)dx$
$\because x \geq c^2 $ 
$\therefore \int_{c^2}^{\infty}xf_X(x)dx\geq\int_{c^2}^{\infty}c^2f_X(x)dx$
又 $\because \int_{c^2}^{\infty}f_X(x)dx =P[X\geq c^2]$
$\therefore E[X]\geq c^2P[X\geq c^2]$
$\text {Q.E.D} $
### 2. 2 切比雪夫不等式（Chebyshev Inequality）
* 对于任意随机变量$Y$ 和常数$c > 0$ ，有：
\[P[|Y - \mu_Y|\geq c]\leq\frac{\text{Var}[Y]}{c^2}\] 
> **证明：**
在马尔可夫不等式中，令$X = (Y - \mu_Y)^2$，则有：
\[P[X\geq c^2]=P[(Y - \mu_Y)^2\geq c^2]\leq\frac{E[(Y - \mu_Y)^2]}{c^2}=\frac{\text{Var}[Y]}{c^2}\quad\]
$\text{Q.E.D}$


## 3 弱大数定律（Weak Law of Large Numbers）
* 针对有限样本
* 对于任意常数$c > 0$ ：
  * \(P[|M_n(X)-\mu_X|\geq c]\leq\frac{\text{Var}[X]}{nc^2}\)
    * 描述了样本均值与期望值之间的距离。
  * \(P[|M_n(X)-\mu_X|< c]\geq1 - \frac{\text{Var}[X]}{nc^2}\) 。
* 随着样本数量 \(n\) 的增大，样本均值 \(M_n(X)\) 与总体期望 \(\mu_X\) 之间的差距超过给定正数\(c\) 的概率会越来越小
> **证明**
> 令切比雪夫不等式中的 \(Y = M_n(X)\)即可，具体过程略

## 4 置信区间（Confidence Intervals）
* \(P[|M_n(X) - \mu_X| < c] \geq 1 - \frac{\text{Var}[X]}{nc^2} = 1 - \alpha\)
* 定义此事件的区间长度为 $2c$ 单位，这个区间被称为置信区间
* 将$1 - \alpha$ 称为置信系数
*  设\(X\)是服从高斯分布\((\mu, \sigma)\)的随机变量，对于\(\mu\)的一种置信区间估计形式为：
\[M_n(X) - c \leq \mu \leq M_n(X) + c\]该置信区间的置信系数为\(1 - \alpha\) ，其中：
\[\alpha/2 = Q(c\sqrt{n}/\sigma) = 1 - \Phi(c\sqrt{n}/\sigma)\]其中，\(Q\) 函数是标准正态分布的右尾概率函数，\(\Phi\) 函数是标准正态分布的累积分布函数。
> **证明**
> $\mathrm{P}[M_n(X)-c\leq\mu_X\leq M_n(X)+c]=\mathrm{P}[\mu_X - c\leq M_n(X)\leq\mu_X + c]=\mathrm{P}[-c\leq M_n(X)-\mu_X\leq c].$
> \(\because M_n(X)-\mu\) 是 \((0,\sigma/\sqrt{n})\) 高斯随机变量
> $\therefore \mathrm{P}[M_n(X)-c\leq\mu\leq M_n(X)+c]=\mathrm{P}\left[\frac{-c}{\sigma/\sqrt{n}}\leq\frac{M_n(X)-\mu}{\sigma/\sqrt{n}}\leq\frac{c}{\sigma/\sqrt{n}}\right]=1 - 2Q\left(\frac{c\sqrt{n}}{\sigma}\right)$
> \(\therefore 1-\alpha=1 - 2Q(c\sqrt{n}/\sigma)\)