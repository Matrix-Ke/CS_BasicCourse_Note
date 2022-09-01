# 数值分析笔记
记录数值分析学习笔记，此过程持续更新，逐步填坑中。。。

## 误差分析

#### 误差分析相关概念：
|概念|释义|性质|
|:--- | :---| :---|
|绝对误差| 设 $\mathrm{x}$ 为精确值， $\mathrm{x}^{*}$ 为 $\mathrm{x}$ 的一个近似值，则称 $\mathrm{e}^{*}=$ $\mathrm{x}^{*}-\mathrm{x}$ 为近似值的绝对误差，简称误差| 当绝对误差为正时，又叫做强近似值；当绝对误差为负时，又叫做弱近似值|
|绝对误差限 |若绝对误差 $\mathrm{e}^{*}$ 的绝对值不超过㭉正数 $\varepsilon^{*}$ ，则称 $\varepsilon^{*}$ 为 近似值的绝对误差限，简称洖差限|总是正数，且现实中相较绝对误差更加常用|
|相对误差 |设 $\mathrm{x}$ 为精确值，若 $\mathrm{e}^{*}=\mathrm{x}^{*}-\mathrm{x}$ 为近似值 $\mathrm{x}^{*}$ 的绝对误 差，则称 $e_{\mathrm{r}}^{*}=\frac{e^{*}}{x}$ 为近似值 $x^{*}$ 的相对误差 |在实际计算中，由于真值 $x$ 总是不知道的，因此 相对误差通常取 $\mathrm{e}_{\mathrm{r}}^{*}=\frac{\mathrm{e}^{*}}{\mathrm{x}^{*}}$|
|相对误差限|设 $\mathrm{x}$ 为精确值，若 $\varepsilon^{*}$ 为近似值 $\mathrm{x}^{*}$ 的绝对误差限，则 称 $\varepsilon_{r}^{*}=\frac{\varepsilon^{*}}{a b s\left(x^{*}\right)}$ 为近似值 $x^{*}$ 的相对误差限| 总是正数，且现实中相较相对误差更加常用|
|有效数字| 若近似值 $x^{*}$的误差限是某位的半个单位，则该位到 $\mathrm{x}^{*}$ 的第一位非零数字的位数 $\mathrm{n}$ ，称 $\mathrm{x}^{*}$ 有 $\mathrm{n}$ 位有效数字| n位有效数字的标准形式: $x^{*}=\left(a_{1}+a_{2} \times\right.$ $\left.10^{1}+\ldots+a_{\mathrm{n}} \times 10^{-(\mathrm{n}-1)}\right) \times \pm 10^{\mathrm{m}}$; 故其绝对误差限可表示为: $\varepsilon^{*}=\frac{1}{2} \times 10^{(m−n+1)}$ 故其相对误差限可表示为: $\varepsilon_{\mathrm{r}}^{*}=\frac{1}{2 a 1} \times$ $10^{(\mathrm{n}-1)}$|

>总结：
>* 近似值$x^{*}$的非零位个数不一定等于有效数字位数；
>* 对于四舍五入的近似值，它们的误差均不超过末位数字的半个单位，从$x^{*}$的第一位非零数字到末位都是有效数字；
>* 有效位数越多，绝对误差限越小，相对误差限亦越小；


#### 误差限四则运算
$$
\begin{aligned}
&\varepsilon\left(\mathrm{x}_{1}^{*} \pm \mathrm{x}_{2}^{*}\right)=\varepsilon\left(\mathrm{x}_{1}^{*}\right)+\varepsilon\left(\mathrm{x}_{2}^{*}\right) \\
&\varepsilon\left(\mathrm{x}_{1}^{*} \times \mathrm{x}_{2}^{*}\right) \approx\left|\mathrm{x}_{1}^{*}\right| \varepsilon\left(\mathrm{x}_{2}^{*}\right)+\left|\mathrm{x}_{2}^{*}\right| \varepsilon\left(\mathrm{x}_{1}^{*}\right) \\
&\varepsilon\left(\frac{\mathrm{x}_{1}^{*}}{\mathrm{x}_{2}^{*}}\right) \approx \frac{1}{\left.\mathrm{x}_{2}^{*}\right|^{2}}\left(\left|\mathrm{x}_{1}^{*}\right| \varepsilon\left(\mathrm{x}_{2}^{*}\right)+\left|\mathrm{x}_{2}^{*}\right| \varepsilon\left(\mathrm{x}_{1}^{*}\right)\right)
\end{aligned}
$$

#### 函数误差限
一元函数 $\mathrm{f}(\mathrm{x})$ 误差限： $\varepsilon\left(\mathrm{f}\left(\mathrm{x}^{*}\right)\right)=\left|\mathrm{f}^{\prime}(\mathrm{x} *)\right| \varepsilon\left(\mathrm{x}^{*}\right)$
多元函数误差限: $\varepsilon\left(\mathrm{f}\left(\mathrm{x}_{1}^{*}, \mathrm{x}_{2}^{*}, \ldots, \mathrm{x}_{\mathrm{n}}^{*}\right)\right)=\sum\left|\frac{\delta \mathrm{f}}{\delta \mathrm{x}_{\mathrm{i}}^{*}}\right| \varepsilon\left(\mathrm{x}_{\mathrm{i}}^{*}\right)$

#### 误差分析原则：
* 避免除数绝对值远远小于被除数绝对值的除法
* 避免两个相近数的减法
* 先计算小数，再计算大数，防止大数运算中截断小数



## 函数插值

(根据 某末知函数 $\mathrm{f}(\mathrm{x})$ 一系列的观测点 $\left(\mathrm{x}_{\mathrm{i}}, \mathrm{y}_{\mathrm{i}}\right)$ 求出既能反映 $\mathrm{f}(\mathrm{x})$ 的特性、又便于计算的简单的函数 $\mathrm{P}(\mathrm{x})$ (如代数多项式函数) 使得 $\mathrm{P}\left(\mathrm{x}_{\mathrm{i}}\right)=\mathrm{y}_{\mathrm{i}}$ ，以便近似求出/预判其他一些末观测的函数值)

### Lagrange插值法

### Aitken逐次线性插值法

### Newton插值法

### Hermite插值法

### 三次样条插值法


## 函数逼近：

#### 函数逼近相关概念：
#### 常用正交多项式：
#### 函数族线性无关的CramerCramer判别法：
#### 法方程法求最佳平方逼近函数 / 多项式：
#### 广义FourierFourier级数求最佳平方逼近多项式：
#### FourierFourier级数求最佳平方逼近三角多项式：
#### 曲线拟合的最小二乘法：


## 数值积分和数值微分
#### 数值积分相关概念：
#### Newton-CotesNewton−Cotes公式：
#### 复化求积法：
#### RombergRomberg公式RichardsonRichardson外推加速法：
#### Gauss-LegendreGauss−Legendre公式：
#### 数值微分常用方法:

## 函数方程数值解法：
#### 二分法：
#### 迭代法：
#### Aitken迭代法：
#### Newton切线法：
#### 弦截法：
#### 抛物线法：


## 常微分方程数值解法
#### Lipschitz条件：
对于一阶微分方程的初值问题: $\mathrm{y}^{\prime}=\mathrm{f}(\mathrm{x}, \mathrm{y}), \mathrm{y}\left(\mathrm{x}_0\right)=\mathrm{y}_0$ ，若函数 $\mathrm{f}(\mathrm{x}, \mathrm{y})$ 满足: $\left|\mathrm{f}\left(\mathrm{x}, \mathrm{y}_1\right)-\mathrm{f}\left(\mathrm{x}, \mathrm{y}_2\right)\right| \leq \mathrm{L}\left|\mathrm{y}_1-\mathrm{y}_2\right|$ 的Lipschitz条件， 则该问题存在唯一解 $\mathrm{y}=\mathrm{y}(\mathrm{x})$

#### Euler解法：
#### Taylor解法：
#### Runge−Kutta解法：
#### Adams解法：
#### Milne解法Simpson解法：
####  Hamming解法：
#### 边值问题的差分解法：







## 线性方程组数值解法
许多数值问题都可以转化为求解线性问题：
$$\mathbf{Ax = b}\\$$

计算 $\mathbf{A^-1}$的成本很高，尤其是在$\mathbf{A}$大且稀疏的情况下。 所以我们不能简单地做:$\mathbf{x = A^{-1}}$

#### LU分解法：
$\bf{LU}$分解定理：若 $\mathbf{A}$ 的各阶顺序主子式 $\mathbf{D}_{\mathbf{k}} \equiv 0$ ，则 $\mathbf{A}$ 可唯一分解为一个单位下三角矩阵 $\mathbf{L}$ 和一个上 三角矩阵$\mathbf{U}$的乘积的形式，即： $\bf{A=L U}$ 
(1) 直接线性求解器：
* 直接求解器通常基于 LU 分解或其变体：Cholesky、LDLT， ETC…
$$
\mathbf{A}=\mathbf{L U}=\left[\begin{array}{ccc}
l_{00} & & \\
l_{10} & l_{11} & \\
\vdots & \cdots & \ddots
\end{array}\right]\left[\begin{array}{ccc}
\ddots & \ldots & \vdots \\
& u_{n-1, n-1} & u_{n-1, n} \\
& & u_{n, n}
\end{array}\right]
$$
图解如下：
![](./image/LU_Decompose.png)
* 先求解: 𝐋𝐲 = 𝐛:
$$
\left[\begin{array}{ccc}
l_{00} & & \\
l_{10} & l_{11} & \\
\vdots & \cdots & \ddots
\end{array}\right]\left[\begin{array}{c}
y_{0} \\
y_{1} \\
\vdots
\end{array}\right]=\left[\begin{array}{c}
b_{0} \\
b_{1} \\
\vdots
\end{array}\right]\\
\begin{aligned}
&y_{0}=b_{0} / l_{00} \\
&y_{1}=\left(b_{1}-l_{10} y_{0}\right) / l_{11}\\
&\cdots \\
\end{aligned}\\
$$
* 然后将上一步求解的$\bf y$带入$\mathbf{Ux=y}$即求解$\bf x$：
$$
\left[\begin{array}{ccc}
\ddots & \ldots & \vdots \\
& u_{n-1, n-1} & u_{n-1, n} \\
& & u_{n, n}
\end{array}\right]\left[\begin{array}{c}
\vdots \\
x_{n-1} \\
x_{n}
\end{array}\right]=\left[\begin{array}{c}
\vdots \\
y_{n-1} \\
y_{n}
\end{array}\right]\\
\begin{aligned}
&x_{n}=y_{n} / u_{n, n} \\
&x_{n-1}=\left(y_{n-1}-u_{n-1, n} x_{n}\right) / u_{n-1, n-1}\\
&\cdots\\
\end{aligned}
$$

(2) 迭代线性求解器
* 迭代求解器具有形式:
![](./image/Iterative_solver.png)

* 原理证明：
$$
\begin{aligned}
\mathbf{b}-\mathbf{A} \mathbf{x}^{[k+1]} &=\mathbf{b}-\mathbf{A} \mathbf{x}^{[k]}-\alpha \mathbf{A} \mathbf{M}^{-1}\left(\mathbf{b}-\mathbf{A} \mathbf{x}^{[k]}\right) \\
&=\left(\mathbf{I}-\alpha \mathbf{A} \mathbf{M}^{-1}\right)\left(\mathbf{b}-\mathbf{A \mathbf { x } ^ { [ k ] }}\right)=\left(\mathbf{I}-\alpha \mathbf{A} \mathbf{M}^{-1}\right)^{k+1}\left(\mathbf{b}-\mathbf{A \mathbf { x } ^ { [ 0 ] }}\right)
\end{aligned}
$$
因为$\left(\mathbf{b}-\mathbf{A} \mathbf{x}^{[0]}\right)$是最初迭代形似，满足一下条件时，迭代结果越来越好。
$$
\mathbf{b}-\mathbf{A x} \mathbf{x}^{[k+1]} \rightarrow 0，即\rho(\left(\mathbf{I}-\alpha \mathbf{A} \mathbf{M}^{-1}\right)^{k+1}) \lt 1\\
$$

>Note:  $\rho\left(\mathbf{I}-\alpha \mathbf{A} \mathbf{M}^{-1}\right)^{k+1}$就是谱半径（特征值的最大绝对值）

* M矩阵需要时容易计算的形似，还有其他形式：
  * **Jacobi Method** ： $\bf M = diag(A)$ （对角矩阵）
  * **Gauss-Seidel Method** : $\mathbf{M = lower(A)}$ （下三角矩阵） 
  * 可以加速收敛：Chebyshev、Conjugate Gradient、……

* Pros and Cons ：
  * 实现简单， 不精确的情况快速，可并行
  * 需要满足条件（谱半径< 1,判断谱半径可以简单先判断：Gauss-Seidel A矩阵需要正定，Jacobi A矩阵需要对角占优）, 精确解很慢

#### 常用向量范数：
#### 常用矩阵范数：
#### 矩阵条件数：
#### Gauss消去法：
#### 矩阵谱半径/迭代法收敛定理：

#### Jacobi迭代法：

#### Gauss−Seidel迭代法：

#### 超松弛迭代法：



**参考资料：**

1. [快速掌握A=LU分解及应用](https://www.bilibili.com/video/BV1r84y1F7qC?spm_id_from=333.337.search-card.all.click&vd_source=1a163e481fb12c5b6ca8a57f994c1d73)
2. [常微分方程数值解法](https://blog.csdn.net/qq_44820158/article/details/108259616)