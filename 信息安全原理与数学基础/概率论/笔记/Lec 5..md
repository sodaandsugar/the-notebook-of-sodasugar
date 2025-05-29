# Lec 5 过程
## 1 常见过程
### 1. 1 随机过程（Stochastic Process）
* 用 \(X(t)\) 表示
* 概率测度
  * 在样本空间 \(S\) 上定义的概率测度 \(P[\cdot]\) 的试验
* 时间函数映射（Sample Function）
  * 一个函数，它为试验样本空间中的每个结果\(s\)分配一个时间函数\(x(t, s)\)
* 样本空间（Ensemble）
  * 由一个试验可能产生的所有可能的时间函数构成的集合
* 随机序列（Random Sequence）
  * 随机序列 \(X_n\) 是随机变量 \(X_0, X_1, \cdots\) 组成的有序序列
* 随机变量
  * 用 \(X(t_1)\) 表示在特定时刻 \(t_1\) 观察某随机过程得到的随机变量
  * 和其他随机变量一样，它有概率密度函数 \(f_{X(t_1)}(x)\) 或概率质量函数 \(P_{X(t_1)}(x)\)

> **注**：符号 \(X(t)\) 既可以指随机过程，也可以指在时刻 \(t\) 对应随机过程取值的随机变量

### 1. 2 离散值与连续值过程
* 若在所有时刻 \(t\) ，\(X(t)\) 的所有可能取值构成的集合 \(S_X\) 是可数集 ，则 \(X(t)\) 是离散值过程
* 否则，\(X(t)\) 是连续值过程

* 设 \(X_n\) 表示独立同分布的随机序列
  * 对于离散值过程，样本向量 \(\mathbf{X} = [X_{n_1}\cdots X_{n_k}]'\) 的联合概率质量函数（PMF）为：
\[P_{\mathbf{X}}(\mathbf{x}) = P_X(x_1)P_X(x_2)\cdots P_X(x_k)=\prod_{i = 1}^{k}P_X(x_i).\]
  * 对于连续值过程，样本向量 \(\mathbf{X} = [X_{n_1},\cdots,X_{n_k}]'\) 的联合概率密度函数（PDF）为：
\[f_{\mathbf{X}}(\mathbf{x}) = f_X(x_1)f_X(x_2)\cdots f_X(x_k)=\prod_{i = 1}^{k}f_X(x_i).\] 

### 1. 3 离散时间与连续时间过程
* 若随机过程 \(X(t)\) 仅在一组时刻 \(t_n = nT\) （其中 \(T\) 为常数，\(n\) 为整数 ）上有定义，则 \(X(t)\) 是离散时间过程
* 否则，\(X(t)\) 是连续时间过程

### 1. 4 伯努利过程
  * 伯努利\((p)\) 过程 \(X_n\) 是一个独立同分布的随机序列，其中每个 \(X_n\) 都是伯努利\((p)\) 随机变量

## 2 泊松过程
### 2. 1 定义
* 计数过程（Counting Process）
  * 若随机过程 $N(t)$ 对于每个样本函数满足：在 $t < 0$ 时有 $n(t, s)=0$ ，且 $n(t, s)$ 取值为随时间非递减的整数，则称 $N(t)$ 是计数过程
* 泊松过程（Possion Process）
  * 计数过程 $N(t)$ 是速率为 $\lambda$ 的泊松过程，需满足：
    * 在任意区间 $(t_0, t_1]$ 内的到达数 $N(t_1) - N(t_0)$ 是一个泊松随机变量，其期望值为$\lambda(t_1 - t_0)$
    * 对于任意一对不重叠的区间 $(t_0, t_1]$ 和 $(t_0', t_1']$ ，两个区间内的到达数，分别为$N(t_1) - N(t_0)$ 和$N(t_1') - N(t_0')$ ，是相互独立的随机变量
### 2. 2 定理
* 对于速率为 $\lambda$ 的泊松过程 $N(t)$ ，在有序时刻 $t_1 < \cdots < t_k$ 下，$\mathbf{N} = [N(t_1), \cdots, N(t_k)]'$ 的 PMF 为：
\[
P_{\mathbf{N}}(\mathbf{n}) = 
\begin{cases}
\frac{\alpha_1^{n_1}e^{-\alpha_1}}{n_1!} \cdot \frac{\alpha_2^{n_2 - n_1}e^{-\alpha_2}}{(n_2 - n_1)!} \cdots \frac{\alpha_k^{n_k - n_{k - 1}}e^{-\alpha_k}}{(n_k - n_{k - 1})!} & 0 \leq n_1 \leq \cdots \leq n_k \\
0 & \text{otherwise}
\end{cases}
\]其中$\alpha_1 = \lambda t_1$ ，对于$i = 2, \cdots, k$ ，$\alpha_i = \lambda (t_i - t_{i - 1})$
> **证明**
> 令 $M_1 = N(t_1)$ ，对于 $i > 1$ ，令 $M_i = N(t_i) - N(t_{i - 1})$
> 则 $M_1, \cdots, M_k$ 是一组相互独立的泊松随机变量，且 $\mathrm{E}[M_i] = \alpha_i$
> $\therefore P_{\mathbf{N}}(\mathbf{n}) = P_{M_1, M_2, \cdots, M_k}(n_1, n_2 - n_1, \cdots, n_k - n_{k - 1}) = P_{M_1}(n_1)P_{M_2}(n_2 - n_1) \cdots P_{M_k}(n_k - n_{k - 1})$
> 将 $P_{M_i}(n_i - n_{i - 1})$ 代入展开即可得证

* 对于速率为 $\lambda$ 的泊松过程，到达间隔时间 $X_1, X_2, \cdots$ 是独立同分布的随机序列，且具有指数概率密度函数（PDF）：
\[
f_X(x)=
\begin{cases}
\lambda e^{-\lambda x} & x \geq 0\\
0 & \text{otherwise}
\end{cases}
\]
> **证明**
> 令 $X_1 = x_1, X_2 = x_2, \cdots, X_{n - 1} = x_{n - 1}$ ，则第 $n - 1$ 次到达发生在时刻 $t_{n - 1}=x_1 + \cdots + x_{n - 1}$
> 对于 $x > 0$ ，当且仅当区间 $(t_{n - 1}, t_{n - 1} + x]$ 内没有到达事件时，$X_n > x$
> $\because X_n$ 与 $X_1, \cdots, X_{n - 1}$ 相互独立
> $\therefore \mathrm{P}[X_n > x|X_1 = x_1, \cdots, X_{n - 1} = x_{n - 1}]=\mathrm{P}[N(t_{n - 1} + x) - N(t_{n - 1}) = 0]=e^{-\lambda x}$
> $\therefore F_{X_n}(x)=1 - \mathrm{P}[X_n > x]=\begin{cases}1 - e^{-\lambda x} & x > 0\\0 & \text{otherwise}\end{cases}$
对 $F_{X_n}(x)$求导即可得证 

* 若一个计数过程的到达间隔时间 $X_1, X_2, \cdots$ 相互独立且服从参数为 $\lambda$ 的指数分布 ，则它是速率为$\lambda$ 的泊松过程
* 设 $N_1(t)$ 和 $N_2(t)$ 是两个速率分别为 $\lambda_1$ 和 $\lambda_2$ 的独立泊松过程，则计数过程 $N(t)=N_1(t)+N_2(t)$ 是一个速率为$\lambda_1 + \lambda_2$ 的泊松过程
* 由泊松过程 $N(t)$ 的伯努利分解得到的计数过程 $N_1(t)$ 和 $N_2(t)$ 是相互独立的泊松过程，速率分别为$\lambda p$ 和$\lambda(1 - p)$
* 设 $N(t)=N_1(t)+N_2(t)$ 为两个速率分别为 $\lambda_1$ 和 $\lambda_2$ 的独立泊松过程之和，若 $N(t)$ 过程有一个到达事件，那么该到达事件来自 $N_1(t)$ 的条件概率为 $\lambda_1/(\lambda_1 + \lambda_2)$

## 3 布朗运动过程（Brownian Process）
* 用 $W(t)$ 表示
* $W(0) = 0$
* 对于 $\tau > 0$ ，$W(t + \tau) - W(t)$ 是一个服从高斯分布 $(0, \sqrt{\alpha\tau})$ 的随机变量 ，并且它与所有满足 $t' \leq t$ 的$W(t')$ 相互独立
* 对于布朗运动过程 $W(t)$ ，$\mathbf{W} = [W(t_1), \cdots, W(t_k)]'$ 的概率密度函数（PDF）为：
\[
f_{\mathbf{W}}(\mathbf{w}) = \prod_{n = 1}^{k} \frac{1}{\sqrt{2\pi\alpha (t_n - t_{n - 1})}} e^{-(w_n - w_{n - 1})^2/[2\alpha (t_n - t_{n - 1})]}
\] 

## 4 期望值与相关性
* 过程的期望值（Expected Value）
  * $\mu_X(t) = \mathrm{E}[X(t)]$
* 相关性（Correlation）
  |比较项|随机过程 $X(t)$|随机序列$X_n$|
  |----|---|----|
  |自协方差（Autocovariance）|$C_X(t, \tau)=\mathrm{Cov}[X(t), X(t + \tau)]$|$C_X[m, k]=\mathrm{Cov}[X_m, X_{m + k}]$|
  |自相关函数（Autocorrelation Function）|$R_X(t, \tau)=\mathrm{E}[X(t)X(t + \tau)]$|$R_X[m, k]=\mathrm{E}[X_mX_{m + k}]$|
  |二者关系|$C_X(t, \tau)=R_X(t, \tau)-\mu_X(t)\mu_X(t + \tau)$|$C_X[n, k]=R_X[n, k]-\mu_X(n)\mu_X(n + k)$|