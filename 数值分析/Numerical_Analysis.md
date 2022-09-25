# 数值分析
记录数值分析学习笔记，此过程持续更新，逐步填坑中。。。

### Prerequisite
##### 带着问题去学习：
求解方程组有很多方法，需要了解这些工具的“技术指标”来决定什么时候用什么方法。这些技术指标，比方说它们适用的矩阵有什么要求？它们需要的计算量各是多少？它们需要的存储量各是多少？它们对于大规模问题的表现怎么样？计算误差有多大？有没有什么特殊情况是它们特别适用或是特别不适用的？有没有进一步的手段改善它们的表现？ 总的来说一个方程组解的好不好，取决于选用的方法和问题本身！
**Cons VS Pros：**（todo...）
1. 高斯消去法：
2. Cholesky分解法:
3. QR分解法:
4. Jacobi迭代法:
5. Gauss-Seidel迭代法:
6. 共轭梯度法:

##### 方法论：
数值分析许多章节之间并没有特别紧密的联系，所以学习的时候可以铺开，发散思维。 对不同的章节, 各学各的，分别独立击破。

## 1.误差分析
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



## 2. 函数插值与逼近
核心思想： 用多项式来做拟合函数
### 插值方法：
(根据 某末知函数 $\mathrm{f}(\mathrm{x})$ 一系列的观测点 $\left(\mathrm{x}_{\mathrm{i}}, \mathrm{y}_{\mathrm{i}}\right)$ 求出既能反映 $\mathrm{f}(\mathrm{x})$ 的特性、又便于计算的简单的函数 $\mathrm{P}(\mathrm{x})$ (如代数多项式函数) 使得 $\mathrm{P}\left(\mathrm{x}_{\mathrm{i}}\right)=\mathrm{y}_{\mathrm{i}}$ ，以便近似求出/预判其他一些末观测的函数值)
#### Lagrange插值法
#### Aitken逐次线性插值法
#### Newton插值法
#### Hermite插值法
#### 三次样条插值法
### 逼近方法：

#### 函数逼近相关概念：
#### 常用正交多项式：
#### 函数族线性无关的CramerCramer判别法：
#### 法方程法求最佳平方逼近函数 / 多项式：
#### 广义Fourier级数求最佳平方逼近多项式：
#### Fourier级数求最佳平方逼近三角多项式：
#### 曲线拟合的最小二乘法：


## 3. 数值积分和数值微分
用有限去接近无限：数值微分就是差分和差商， 数值积分就是求和。

#### 有限差分法：
有限差分法基本概念
一、差商与微商
有限差分的数学基础是用差商代替微商。
有如下两种数学形式:
微商（导数）的定义
若 $T(x)$ 是连续函数, 则它的导数为:
$$
\frac{d T}{d x}=\lim _{\Delta x \rightarrow 0} \frac{T(x+\Delta x)-T(x)}{\Delta x}=\lim _{\Delta x \rightarrow 0} \frac{\Delta T}{\Delta x}
$$
右边 $\frac{\Delta T}{\Delta x}$ 是有限的差商。

可以参考文章[微分方程数值求解——有限差分法](https://zhuanlan.zhihu.com/p/411798670)

**二阶差分公式推导：**
对连续函数 $f(x)$ 以间隔 $\Delta x$ 进行空间离散, 则 $f(x)$ 的前后两 个采样值 $f(x \pm \Delta x)$ 在 $x$ 点处的泰勒级数展开式为
$$
f(x \pm \Delta x)=f(x) \pm \Delta x f^{\prime}(x)+\frac{(\Delta x)^2}{2} f^{\prime \prime}(x) \pm \frac{(\Delta x)^3}{6} f^{\prime \prime \prime}(x)+O\left((\Delta x)^3\right)
$$
将上式中带正负号的两个泰勒级数展开式相加,并经过整理可获取二阶导数的差分格式：
$$
\begin{aligned}
f^{\prime \prime}(x) &=\frac{f(x+\Delta x)-2 f(x)+f(x-\Delta x)}{(\Delta x)^2}-O\left((\Delta x)^2\right) \\
& \approx \frac{f(x+\Delta x)-2 f(x)+f(x-\Delta x)}{(\Delta x)^2}
\end{aligned}
$$

### 数值积分相关概念：
#### 提出问题
如何计算 $\int_a^b f(x) d x=\lim _{\lambda \rightarrow 0} \sum_{j=0}^n f\left(x_j\right) \Delta x_j$ 定积分？
微积分基本定理 ：
$$
\int_a^b f(x) d x=F(b)-F(a)
$$
如果⽆法找到原函数或者原函数过于复杂不适合数值计算，怎么办？
* 定积分本质是⼀个具体的数
* ⽬标是找到这个数的近似值，精度越⾼越好，代价越⼩越好！

#### 数值积分的方法
- 积分中值定理:
$$
\int_a^b f(x) d x=f(\xi)(b-a)
$$
- 近似被积函数
$$
\int_a^b f(x) d x \approx \int_a^b p(x) d x
$$
- 积分的区域可加性: 复化求积分公式
$$
\int_a^b f(x) d x=\int_a^c f(x) d x+\int_c^b f(x) d x=\ldots
$$
- 进⼀步提⾼效率：⾃适应求积分

##### 积分中值定理
**矩形公式：**  左矩形，右矩形公式，中点公式，梯形公式
$$
\begin{array}{rlr}
\int_a^b f(x) d x & =f(\xi)(b-a) & \\
& \approx f(a)(b-a) & \text { 左矩形 } \\
& \approx f(b)(b-a) & \text { 右矩形 } \\
& \approx f\left(\frac{a+b}{2}\right)(b-a) & \text { 中矩形 } \\
& \approx \frac{f(a)+f(b)}{2}(b-a) &  \text { 梯形公式 } \\
\end{array}
$$

**梯形公式的截断误差：**
利用Taylor展开推导：
$$
E_T=\int_a^b f(x) d x-\frac{f(a)+f(b)}{2}(b-a)=\int_a^b\left[f(x)-\frac{f(a)+f(b)}{2}\right] d x
$$
Hint:
$$
\begin{aligned}
f(x) &=f(a)+f^{\prime}(a)(x-a)+f^{\prime \prime}\left(\xi_1\right)(x-a)^2 \\
f(x) &=f(b)+f^{\prime}(b)(x-b)+f^{\prime \prime}\left(\xi_2\right)(x-b)^2 \\
E_T &=\int_a^b \frac{1}{2}\left[f^{\prime}(a)(x-a)+f^{\prime}(b)(x-b)+f^{\prime \prime}\left(\xi_1\right)(x-a)^2+f^{\prime \prime}\left(\xi_2\right)(x-b)^2\right] d s \\
&=\frac{1}{2}\left[\left(f^{\prime}(a)-f^{\prime}(b)\right) \frac{(b-a)^2}{2}+\mathrm{(f^{\prime\prime}(\xi_1) - f^{\prime\prime}(\xi_2))} * \frac{(b-a)^3}{3}\right] \\
&=\mathrm{( (f^{\prime\prime}(\xi_1) - f^{\prime\prime}(\xi_2)) -  f^{\prime\prime}(\xi_3) )} * \frac{(b-a)^3}{-12}\\
&= -\frac{f^{\prime \prime}(\eta)}{12}(b-a)^3 \\
\end{aligned}\\
$$
> Note: 
> * $\mathrm{C}_2$ 与二阶导数相关。

#### Newton−Cotes公式：


#### 复化求积法：
#### Richardson外推加速法：
#### Gauss−Legendre公式：
#### 数值微分常用方法:

## 4. (非线性) 方程求根：
求解函数方程 $\mathrm{f}(\mathrm{x})=0, \mathrm{x} \in[\mathrm{a}, \mathrm{b}]$ 的根 $\mathrm{x}^*$ 的近似值 $\mathrm{x}$ ，使得误差 $\left|\mathrm{x}^*-\mathrm{x}\right|<\varepsilon$ ，其中 $\varepsilon$ 为预定的精度

**核心思想：**

迭代法的最简单应用， 以牛顿法为核心去理解所有问题。 
* 一阶可导：牛顿法（切线法）
* 一阶不可导：拟牛顿法（割线法、弦截法）

#### 二分法：
#### 迭代法：
#### Aitken迭代法：
#### Newton切线法：
#### 弦截法：
#### 抛物线法：



## 5. 线性方程组数值解法
许多数值问题都可以转化为求解线性问题：
$$\mathbf{Ax = b}\\$$

计算 $\mathbf{A^-1}$的成本很高，尤其是在$\mathbf{A}$大且稀疏的情况下。 所以不能简单地做:$\mathbf{x = A^{-1}}$

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


## 6. 常微分方程数值解法
#### Lipschitz条件：
对于一阶微分方程的初值问题: $\mathrm{y}^{\prime}=\mathrm{f}(\mathrm{x}, \mathrm{y}), \mathrm{y}\left(\mathrm{x}_0\right)=\mathrm{y}_0$ ，若函数 $\mathrm{f}(\mathrm{x}, \mathrm{y})$ 满足: $\left|\mathrm{f}\left(\mathrm{x}, \mathrm{y}_1\right)-\mathrm{f}\left(\mathrm{x}, \mathrm{y}_2\right)\right| \leq \mathrm{L}\left|\mathrm{y}_1-\mathrm{y}_2\right|$ 的Lipschitz条件， 则该问题存在唯一解 $\mathrm{y}=\mathrm{y}(\mathrm{x})$

#### Euler解法：
#### Taylor解法：
#### Runge−Kutta解法：
#### Adams解法：
#### Milne解法Simpson解法：
####  Hamming解法：
#### 边值问题的差分解法：



**参考资料：**

1. [快速掌握A=LU分解及应用](https://www.bilibili.com/video/BV1r84y1F7qC?spm_id_from=333.337.search-card.all.click&vd_source=1a163e481fb12c5b6ca8a57f994c1d73)
2. [常微分方程数值解法](https://blog.csdn.net/qq_44820158/article/details/108259616)
3. [微分方程数值求解——有限差分法](https://zhuanlan.zhihu.com/p/411798670)
4. [二阶中心差分格式](http://www.tup.tsinghua.edu.cn/upload/books/yz/085948-01.pdf)
5. [李庆扬，《数值分析》，清华大学出版社]()