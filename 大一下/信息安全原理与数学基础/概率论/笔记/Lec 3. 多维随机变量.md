# Lec 3. 多维随机变量
## 1 基本概念
### 1. 1 重要函数
* 联合概率分布函数（Joint PMF）
  * $P_{X,Y}(x,y)=P[X=x,Y=y]$
* 边际概率分布函数（Marginal PMF）
  * $P_X(x)=\sum\limits_{y \in S_Y}P_{X,Y}(x,y)$
  * $P_Y(y)=\sum\limits_{x \in S_X}P_{X,Y}(x,y)$
* 联合概率密度函数（Joint PDF）
  * $F_{X,Y}(x)=\int^x_{-\infty}\int^y_{-\infty}f_{X,Y}(u,v)\,dvdu $
  * $f_{X,Y}(x,y)=\frac{\partial^2F_{X,Y}(x,y)}{\partial x \partial y}$
* 条件概率分布函数（Conditional PMF）
  * $P_{X|Y}(x|y)=P[X=x|Y=y]=\frac{P_{X,Y}(x,y)}{P_Y(y)}$
  * $P_{Y|X}(y|x)=\frac{P_{X,Y}(x,y)}{P_X(x)}$
  * $P_{X,Y}(x,y)=P_{Y|X}(y|x)\cdot P_X(x)=P_{X|Y}(x|y) \cdot P_Y(y)$
* 条件概率密度函数（Conditional PDF）
  * $f_{X|Y}(x|y)=\frac{f_{X,Y}(x,y)}{f_Y(y)}$
  * $f_{X,Y}(x,y)=f_{Y|X}(y|x)\cdot f_X(x)=f_{X|Y}(x|y) \cdot f_Y(y)$
* $P[A]=\iint\limits_A f_{X,Y}(x,y)\,dxdy$
### 1. 2 重要定义
* 协方差（Covariance）
  * $Cov[X,Y]=E[(X-\mu_X)(Y-\mu_Y)]=E[XY]-E[X]E[Y]$
  * $Cov[aX+b,cY+d]=ac\,Cov[X,Y]$
  * 若协方差为正，则两个变量呈正相关
  * 若协方差为负，则两个变量呈负相关
  * 若协方差为零，则两个变量之间不存在线性相关性
* 相关系数（Correlation coefficient）
  * $\rho _{X,Y}=\frac{Cov[X,Y]}{\sqrt{Var[X]Var[Y]}}=\frac{Cov[X,Y]}{\sigma_X\sigma_Y}$
  * $\rho_{aX+b,cY+d}=\rho_{X,Y}$
  * 若相关系数为正，则两个变量呈正相关
  * 若相关系数为负，则两个变量呈负相关
  * 若相关系数为零，则两个变量之间不存在线性相关性
* 皮尔逊积矩相关系数（Pearson Product-moment Correlation Coefficient）
  * $\rho _{X,Y}=\frac{E[X,Y]-\mu_X\mu_Y}{\sigma_X\sigma_Y}$
* 相关性（Correlation）
  * $r_{X,Y}=E[XY]=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}xyf_{X,Y}(x,y)\,dxdy$
  * $Cov[X,Y]=r_{X,Y}-\mu_X\mu_Y$
  * $Var[X+Y]=Var[X]+Var[Y]+2Cov[X,Y]$
  * 若 $X=Y$，则 $Cov[X,Y]=Var[X]=Var[Y]$ 且 $r_{X,Y}=E[X^2]=E[Y^2]$
* 二元高斯随机变量
  * $$f_{X,Y}(x,y) = \frac{\exp\left[-\frac{\left(\frac{x - \mu_X}{\sigma_X}\right)^2 - \frac{2\rho_{X,Y}(x - \mu_X)(y - \mu_Y)}{\sigma_X\sigma_Y}+\left(\frac{y - \mu_Y}{\sigma_Y}\right)^2}{2(1 - \rho_{X,Y}^2)}\right]}{2\pi\sigma_X\sigma_Y\sqrt{1 - \rho_{X,Y}^2}}$$
  * $$f_X(x) = \frac{1}{\sigma_X\sqrt{2\pi}}e^{-(x - \mu_X)^2/2\sigma_X^2}\quad ,\quad f_Y(y) = \frac{1}{\sigma_Y\sqrt{2\pi}}e^{-(y - \mu_Y)^2/2\sigma_Y^2}$$
  * $$\rho_{X,Y} = \frac{E[XY] - \mu_X\mu_Y}{\sigma_X\sigma_Y}$$
  * 若 \(X\) 和 \(Y\) 是二元高斯变量，\(W_1 = a_1X + b_1Y, \quad W_2 = a_2X + b_2Y\)，则:
    * \(E[W_i] = a_i\mu_X + b_i\mu_Y, i = 1,2,... \)
    * \(Var[W_i] = a_i^2\sigma_X^2 + b_i^2\sigma_Y^2 + 2a_ib_i\rho_{X,Y}\sigma_X\sigma_Y,  i = 1,2,...\)
    * \(Cov[W_1,W_2] = a_1a_2\sigma_X^2 + b_1b_2\sigma_Y^2 + (a_1b_2 + a_2b_1)\rho_{X,Y}\sigma_X\sigma_Y\)

## 2 随机变量的和
* 对任意随机变量 $X_1,X_2,\cdots ,X_n$，若 $W_n=X_1+X_2+\cdots+X_n$，则：
  * $E[W_n]=E[X_1]+E[X_2]+ \cdots + E[X_n]$
  * $Var[W_n]=\sum\limits_{i=1}^nVar[X_i]+2\sum\limits_{i=1}^{n-1}\sum\limits_{j=i+1}^nCov[X_i,X_j]$
  * $Var[W_n]=E[(\sum\limits_{i=1}^n(X_i-\mu_i))^2]=\sum\limits_{i=1}^n\sum\limits_{j=1}^nCov[X_i,X_j]$
  * 若 $X_1,X_2,\cdots ,X_n$ 线性无关，则 $Var[W_n]=\sum\limits_{i=1}^nVar[X_i]$
* 当独立随机变量相加时，即使原始变量本身并非呈正态分布，经过适当标准化后的和也趋向于正态（高斯）分布
* 若随机变量 $X_1, X_2, \ldots$ 独立同分布（iid：independent and identically distributed），则$Z_n = \frac{\sum_{i = 1}^{n}X_i - n\mu_X}{\sqrt{n\sigma_X^2}}$ 的累积分布函数（CDF）满足：
  $$\lim_{n \to \infty} F_{Z_n}(z)=\Phi(z)= \frac{1}{\sqrt{2\pi}}\int_{-\infty}^{z}  e^{-\frac{u^2}{2}} \, du$$
* 设$W_n = X_1 + \cdots + X_n$ 为 $n$ 个独立同分布随机变量之和，则 $W_n$ 的累积分布函数的近似为：
  $$F_{W_n}(w) \approx \Phi\left(\frac{w - n\mu_X}{\sqrt{n\sigma_X^2}}\right)$$