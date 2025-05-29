# Lec 2. 概率分布
## 1 基本概念
### 1. 1 重要函数
* 概率分布函数（PMF：Probability Mass Function）
  *  $P_X(x)=P[X=x]$
  *  $P_Y(y)= \sum\limits_{x:g(x)=y} P_X(x)$
* 累积分布函数 （CDF：Cumulative Distribution Function）
  * $F_X(x)=P[X\leq x]$
  * $P[x_1 \leq X \leq x_2]=F_X[x_2]-F_X[x_1]$
* 概率密度函数（PDF：Probability Density Function）
  * $f_X(x)=\frac{dF_X(x)}{dx}$
  * $f_X(x) \geq 0$
  * $F_X(x)=\int_{-\infty}^{x} f_X(u) \, du$
  * $\int_{-\infty}^{\infty}f_X(x)\,dx=1$
### 1. 2 重要定义
* 期望值（Expected Value）
  * 离散型
    * $E[X] = \mu_X = \sum\limits_{x \in S_X} x P_X(x)$
    * $E[g(x)]= \sum\limits_{x \in S_X} g(x)P_X(x)$
  * 连续型
    * $E[X]=\int_{-\infty}^{\infty}xf_X(x)dx$
    * $E[g(x)]=\int_{-\infty}^{\infty}g(x)f_X(x)dx$
  * $E[X-\mu_X]=0$
  * $E[aX+b]=aE[X]+b$
* 方差（Variance）
  * $Var[X]=E[(X-\mu_X)^2]=E[X^2]-(E[X])^2$
  * $Var[aX+b]=a^2Var[X]$
* 标准差（Standard Deviation）
  * $\sigma_X=\sqrt{Var[X]}$
* 矩（Moment）
  * $n$ 阶矩：$E[X^n]$
  * $n$ 阶中心矩：$E[(X-\mu_X)^n]$
## 2 离散型随机变量
### 2. 1 伯努利随机变量（Bernoulli (p) Random Variable 
* 单次进行试验时事件的发生次数 $X$
* $P_X(x) = \begin{cases} 1-p &  x =0\\p & x=1\\0 & \text{otherwise}\end{cases}$
* $E[X]=p$
* $Var[X]=p(1-p)$
### 2. 2 几何随机变量（Geometric (p) Random Variable 
* 试验进行 $X$ 次时事件恰好第一次发生
* $P_X(x)=\begin{cases}p(1-p)^{x-1} &x=1,2,...\\0 & \text{otherwise}\end{cases}$
* $E[X]=1/p$
* $Var[X]=(1-p)/p^2$
### 2. 3 二项随机变量（Binomial (k,p) Random Variable 
* $n$ 重伯努利试验中事件的发生次数 $K$
* $P _ { K } ( k ) = \binom { n } { k } p ^ { k } ( 1 - p ) ^ { n - k } $
* $E[X]=np$
* $Var[X]=np(1-p)$
* ‌棣莫弗-拉普拉斯公式（De Moivre-Laplace Formula）
  * \[
P[k_1 \leq K \leq k_2] \approx \Phi\left(\frac{k_2 + 0.5 - np}{\sqrt{np(1 - p)}}\right) - \Phi\left(\frac{k_1 - 0.5 - np}{\sqrt{np(1 - p)}}\right)
\] 
### 2. 4 帕斯卡随机变量（Pascal (k,p) Random Variable 
* 试验中事件恰好发生 $k$ 次所需的试验次数 $X$
* $P _ { X } ( x ) = \binom { x-1 } { k-1 } p ^ { k } ( 1 - p ) ^ { x - k } $
* $E[X]=k/p$
* $Var[X]=k(1-p)/p^2$
### 2. 5 离散均匀随机变量（Discrete Uniform (k,l) Random Variable）
* $P_X(x)=\begin{cases}1/(l-k+1) &x=k,k+1,k+2,...,l\\0 & \text{otherwise}\end{cases}$
* $E[X]=(k+l)/2$
* $Var[X]=(l-k)(l-k+2)/12$
### 2. 6 泊松随机变量（Poisson ($\alpha$) Random Variable 
* 描述单位时间或空间内某类事件发生次数的概率规律
* $P_X(x)=\begin{cases}\alpha ^xe^{-\alpha}/x! &x=0,1,2,...\\0 & \text{otherwise}\end{cases}$
* $\alpha$ 是单位时间或空间内事件的平均发生次数
* $Var[X]=\alpha$

## 3 连续型随机变量（Continuous Random Variable）
### 3. 1 均匀随机变量（Uniform Random Variable）
* $f_X(x)= \begin{cases} 1/(b-a) &  a \leq x \leq b \\ 0 & \text{otherwise}\end{cases}$
* $F_X(x)=\begin{cases}0 & x \leq a\\(x-a)/(b-a) & a<x \leq b\\1& x> b \end{cases}$
* $E[X]=(a+b)/2$
* $Var[X]=(b-a)^2/12$
### 3. 2 高斯随机变量（Gaussian Random Variable）
> **标准正态分布（Standard Normal Distribution）的CDF**
>  $$\Phi(z) = \int_{-\infty}^{z} \frac{1}{\sqrt{2\pi}} e^{-\frac{u^2}{2}} \, du$$
* $f_X(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x - \mu)^2}{2 \sigma^2}}$
* $F_X(x)=\phi (\frac{x-\mu}{\sigma})$
* $P[a \leq X \leq b]=\phi (\frac{b-\mu}{\sigma})-\phi (\frac{a-\mu}{\sigma})$
* $E[X]=\mu$
* $Var[X]=\sigma ^2$