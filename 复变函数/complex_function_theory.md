# 复变函数论
## 基础知识
### 复数
​定义： z =ax+iyz=x+iy 
​注意分清实部和虚部
​共轭复数： \bar{z}=x-iyzˉ=x−iy 
​ z \bar{z} =x^2+y^2zzˉ=x2+y2 
​ z+ \bar{z} =2x=2Re zz+zˉ=2x=2Rez 
​ z- \bar{z} =2iy=2iIm zz−zˉ=2iy=2iImz 
​复数的模与辐角
​模： |z| = \sqrt{x^{2}+y^{2} }∣z∣=x2+y2​ 
​辐角： θ \equiv Arg z = Arctan \frac{y}{x}θ≡Argz=Arctanxy​ 
​辐角主值：
 0<arg z \leq 2\pi0<argz≤2π
或
 -\pi<arg z \leq \pi−π<argz≤π  
 Arg z=arg z+2k\pi,k \in \mathbb{Z}Argz=argz+2kπ,k∈Z ​Arg z=arg z+2k\pi Arg z=arg z+2k\pi,k \in \mathbb{Z}Argz=argz+2kπ,k∈Z 
​复数的其他表示形式
​指数形式： z= ρ e^{iθ}z=ρeiθ 
​ e^{iθ}eiθ 又称为转角因子
​三角形式： z=cos θ +isin\thetaz=cosθ+isinθ 

### ​复数的运算
​加减运算
​ z_1+z_2=(x_1+x_2)+i(y_1+y_2)z1​+z2​=(x1​+x2​)+i(y1​+y2​) 
​满足平行四边形法则
或者三角形法则
​乘法运算
​一般形式
​运用定义运算：
 i^2=-1i2=−1 
​指数形式：
 e^{i \theta_1}e^{i \theta_2}=e^{i( \theta_1 + \theta_2)}eiθ1​eiθ2​=ei(θ1​+θ2​) 
​商运算
​一般形式：
 \frac{x_1+iy_1}{x_2+iy_2} = \frac{x_1x_2+y_1y_2}{x_2^2+y_2^2} +i \frac{x_2y_1-x_1y_2}{x_2^2+y_2^2}x2​+iy2​x1​+iy1​​=x22​+y22​x1​x2​+y1​y2​​+ix22​+y22​x2​y1​−x1​y2​​ 
​将分母实数化
​指数形式：
 \frac{e^{i \theta_1}}{e^{i \theta_2}} =e^{i(\theta_1-\theta_2)}eiθ2​eiθ1​​=ei(θ1​−θ2​) 
​复数的乘幂与开方
​乘幂： 
z^n= ρ ^ne^{in\theta}= ρ ^n(cosn \theta +isinn \theta )zn=ρneinθ=ρn(cosnθ+isinnθ) 
​棣莫弗公式：
(cos \theta +isin \theta)^n=cosn \theta +isinn \theta(cosθ+isinθ)n=cosnθ+isinnθ 
​开方：
 \sqrt[n]{z}=\sqrt[n]{ ρ } e^{i(\frac{\theta_0}{n}+\frac{2k\pi}{n})} ,k=0,1,…,n-1nz​=nρ​ei(nθ0​​+n2kπ​),k=0,1,…,n−1 

## ​复变函数的级数
​级数的基本性质
​级数收敛
​柯西判据：
 \forall ε >0, \exists N \in \mathbb{Z^+}∀ε>0,∃N∈Z+ ，当 n>Nn>N 时，
 \forall p>1,| f_{n+p}-f_n|< ε∀p>1,∣fn+p​−fn​∣<ε 
则 {\displaystyle \sum_{k=1}^{ \infty }{f_k} }k=1∑∞​fk​ 一定收敛
​ {\displaystyle \lim_{k \rightarrow \infty }{|f_k|} }=0k→∞lim​∣fk​∣=0 是级数收敛的必要条件
​比值（达朗贝尔）判别法：
 {\displaystyle \lim_{k \rightarrow \infty }{|\frac{f_{k+1}}{f_k}|} } =l \begin{cases} l<1 & 级数绝对收敛 \\ l>1 & 级数发散 \\ l=1 & 无法确定 \end{cases}k→∞lim​∣fk​fk+1​​∣=l⎩⎪⎨⎪⎧​l<1l>1l=1​级数绝对收敛级数发散无法确定​ 
柯西根植判别法：
​ {\displaystyle \lim_{k \rightarrow \infty }{ \sqrt[k]{|f_k|} } } =l \begin{cases} l<1 & 级数绝对收敛 \\ l>1 & 级数发散 \\ l=1 & 无法确定 \end{cases}k→∞
lim​
k∣fk​∣​=l⎩⎪⎨⎪⎧​l<1l>1l=1​级数绝对收敛级数发散无法确定​ 
​一致收敛
​ MM 判别法
​威尔斯特拉斯定理
​幂级数
​阿贝尔定理
​泰勒级数
​若 f(z)在区域 σ 内解析，则在 σ 内任意一点z=b的领域|z-b|<R内，f(z)均可展开为泰勒级数f(z)在区域σ内解析，
则在σ内任意一点z=b的领域∣z−b∣<R内，
f(z)均可展开为泰勒级数 
 f(z)= {\displaystyle \sum_{k=0}^{ \infty }{a_k(z-b)^k} }f(z)=k=0∑∞​ak​(z−b)k 
​ a_k=\frac{1}{k!}f^{(k)}(b)ak​=k!1​f(k)(b) 
​ \frac{1}{1+z}= {\displaystyle \sum_{k=0}^{ \infty }{(-1)^kz^k} } ,|z|<11+z1​=k=0∑∞​(−1)kzk,∣z∣<1 
​ \frac{1}{1-z}= {\displaystyle \sum_{k=0}^{ \infty }{z^k} } ,|z|<11−z1​=k=0∑∞​zk,∣z∣<1 
​ e^z= {\displaystyle \sum_{k=0}^{ \infty }{\frac{1}{k!}z^k} } ,|z|< \inftyez=k=0∑∞​k!1​zk,∣z∣<∞ 
​ sinz= {\displaystyle \sum_{k=0}^{ \infty }{\frac{(-1)^k}{(2k+1)!}z^{2k+1}} } ,|z|< \inftysinz=k=0∑∞​(2k+1)!(−1)k​z2k+1,∣z∣<∞ 
​ cosz= {\displaystyle \sum_{k=0}^{ \infty }{\frac{(-1)^k}{(2k)!}z^{2k}} } ,|z|< \inftycosz=k=0∑∞​(2k)!(−1)k​z2k,∣z∣<∞ 
​洛朗级数
​在环域 r<|z-b|<Rr<∣z−b∣<R 内解析，则
 f(z)= {\displaystyle \sum_{k=- \infty }^{ \infty }{C_k(z-b)^k} }f(z)=k=−∞∑∞​Ck​(z−b)k 
​ C_k=\frac{1}{2 \pi i} \oint_l {\frac{f(\zeta)}{(\zeta-b)^{k+1}}d\zeta}Ck​=2πi1​∮l​(ζ−b)k+1f(ζ)​dζ 
​ 注：此时C_k {=}\mathllap{/\,} \frac{f^{(k)}(b)}{k!}注：此时Ck​=/​k!f(k)(b)​ 
​负幂次项称为主部
​正幂次项称为正则部
​孤立奇点
​若 f(z)在b点不解析，但在0<|z-b|< δ 内处处解析，则b是f(z)的孤立奇点f(z)在b点不解析，
但在0<∣z−b∣<δ内处处解析，
则b是f(z)的孤立奇点 
​可去奇点
​级数展开只有正则部，即负幂次项系数均为零
​ m阶极点m阶极点 
​洛朗级数可展开到 -m−m 次项
​ b是 \frac{1}{f(z)} 的m重零点b是f(z)1​的m重零点 
​ f(b)=f^{(1)}(b)=…=f^{(m-1)}(b)=0,f^{(m)}{=}\mathllap{/\,}0,则b是f(z)的m重零点f(b)=f(1)(b)=…=f(m−1)(b)=0,
f(m)=/​0,
则b是f(z)的m重零点 
​本性奇点
​洛朗级数有无穷多项主部
​解析延拓
​ \Gamma函数Γ函数 
​ \Gamma(x)= \int_{0}^{ \infty } {t^{x-1}e^{-t}dt},x>0Γ(x)=∫0∞​tx−1e−tdt,x>0 
​ \Gamma(1)=1Γ(1)=1 
​ \Gamma(x+1)=x \Gamma(x)Γ(x+1)=xΓ(x) 
​ \Gamma(n+1)=n!,n \in \mathbb{N}Γ(n+1)=n!,n∈N 
​ \Gamma(x+1) \Gamma(1-x)=\frac{\pi}{\sin\pi x}Γ(x+1)Γ(1−x)=sinπxπ​ 
​ \Gamma(\frac{1}{2})=\sqrt{\pi}Γ(21​)=π​ 
​ \Gamma(\frac{2n+1}{2})=\frac{(2n)!}{4^nn!} \sqrt{\pi}Γ(22n+1​)=4nn!(2n)!​π​ 
​ \Gamma(n+\frac{1}{2})=\frac{(2n-1)!!}{2^n} \sqrt{\pi}Γ(n+21​)=2n(2n−1)!!​π​ 
## ​解析函数
​充分必要条件：满足C-R条件(柯西-黎曼条件)
和实部与虚部可微
​C-R条件：
 \begin{alignedat}{2} \frac{\partial u}{\partial x}&=&\frac{\partial v}{\partial y} \\ \frac{\partial v}{\partial x}&=&-\frac{\partial x}{\partial y} \end{alignedat}∂x∂u​∂x∂v​​==​∂y∂v​−∂y∂u​​ 
​调和函数：拉普拉斯方程
​初等解析函数
​指数函数
​三角函数
​正弦函数
​ sinz= \frac{e^{iz}-e^{-iz}}{2i}sinz=2ieiz−e−iz​ 
​余弦函数
​ cosz= \frac{e^{iz}+e^{-iz}}{2}cosz=2eiz+e−iz​ 
​……
​与实函数无异
​平方和
​双曲函数
​双曲正弦函数
​ sinhz= \frac{e^{z}-e^{-z}}{2}sinhz=2ez−e−z​ 
​双曲余弦函数
​ sinhz= \frac{e^{z}+e^{-z}}{2}sinhz=2ez+e−z​ 
​……
​平方差
​双曲函数与三角函数的互化
​ sinhz=-isinizsinhz=−isiniz 
​ coshz=cosizcoshz=cosiz 
​ yanhz=-itanizyanhz=−itaniz 
​……
## ​留数
​ \oint_l {f(z)dz}=2 \pi i {\displaystyle \sum_{k=1}^{n}{res f(b_k)} }∮l​f(z)dz=2πik=1∑n​resf(bk​) 
​ res f(b_k)=C_{-1}(b_k)resf(bk​)=C−1​(bk​) ，是洛朗级数的 -1−1 次幂项系数
称为 f(z)在b_k点的留数f(z)在bk​点的留数 
​留数的计算
​本性奇点 bb 
​ f(z)= {\displaystyle \sum_{k=- \infty }^{\infty}{C_k(z-b)^k} }f(z)=k=−∞∑∞​Ck​(z−b)k 
 res f(b)=C_{-1}(b)resf(b)=C−1​(b) 
​一阶极点
​ res f(b)=\frac{1}{2 \pi i} \oint_{l}{ \frac{f(\zeta)}{\zeta-b}d\zeta}resf(b)=2πi1​∮l​ζ−bf(ζ)​dζ 
 res f(b)=(z-b)f(z)\text{\textbar}_{z=b}resf(b)=(z−b)f(z)|z=b​ 
​ 若f(z)=\frac{ φ (z)}{ ψ (z)} ,且 ψ (b)=0, φ (b){=}\mathllap{/\,}0若f(z)=ψ(z)φ(z)​,且ψ(b)=0,φ(b)=/​0 
则 resf(b)=\frac{ φ (b)}{ ψ '(b)}resf(b)=ψ′(b)φ(b)​ 
​ n阶极点 mm阶极点 
​ resf(b)=\frac{1}{(m-1)!} \frac{d^{m-1}}{dz^{m-1}}[f(z)(z-b)^m]|_{z=b}resf(b)=(m−1)!1​dzm−1dm−1​[f(z)(z−b)m]∣z=b​ 
应用
​计算实积分
​ R（\cos \theta,\sin \theta)类型令z=e^{i \theta}R（cosθ,sinθ)类型令z=eiθ 
​ \int_{- \infty }^{\infty} {f(x)dx}∫−∞∞​f(x)dx 
​ 若z \rightarrow \infty ,zf(z)\xrightarrow{一致}0,则 \int_{- \infty }^{\infty} {f(x)dx}=2 \pi i {\displaystyle \sum_{k=1}^{n}{resf(b_k)}|_{Im b_k>0} }若z→∞,zf(z)一致​0,
则∫−∞∞​f(x)dx=2πik=1∑n​resf(bk​)∣Imbk​>0​ 
​ \oint_{-\infty}^{\infty}{f(x) \begin{Bmatrix} \cos px \\ \sin px \end{Bmatrix}dx},(p>0)∮−∞∞​f(x){cospxsinpx​}dx,(p>0) 
​ \oint_{-\infty}^{\infty}{f(x)e^{ipx}dx}=2 \pi i {\displaystyle \sum_{k=1}^{n}{res(f(z)e^{ipb_k})|_{Imb_k>0}} }∮−∞∞​f(x)eipxdx=2πik=1∑n​res(f(z)eipbk​)∣Imbk​>0​ 
​小圆弧引理
​ {\displaystyle \lim_{r \rightarrow 0}{ \int_{C_r}{f(z)dz} } }=i(\theta_2-\theta_1)resf(a)r→0lim​∫Cr​​f(z)dz=i(θ2​−θ1​)resf(a) 
​大圆弧引理
## ​复变函数的积分
​定义以及
解析函数在单连通区域内积分与路径无关
​柯西定理
​在单连通区域内解析函数
沿任意闭合曲线的积分为零
​ \oint_{l} f(z)dz=0∮l​f(z)dz=0 
​在复连通区域内解析函数
按逆时针方向沿外边界线的积分
等于按逆时针方向沿所有内边界线的积分之和
​ \oint_{l} f(z)dz= {\displaystyle \sum_{k=1}^{n}{ \oint_{l_k} f(z)dz} }∮l​f(z)dz=k=1∑n​∮lk​​f(z)dz 
​ \oint_{l} \frac{1}{(z-a)^n}dz = \begin{cases} 0 & n \leq 0 \\ 2 \pi i & n=1 \\ 0 & n \geq 2 \end{cases}∮l​(z−a)n1​dz=⎩⎪⎨⎪⎧​02πi0​n≤0n=1n≥2​ 
​ aa 在积分围道内
​若 aa 在积分围道外时，
则被积函数在积分围道内解析，
积分为零
​柯西积分公式
​ f(a)= \frac{1}{2 \pi i} \oint_{l} \frac{f(z)}{z-a}dzf(a)=2πi1​∮l​z−af(z)​dz 
​ f(z)= \frac{1}{2 \pi i} \oint_{l} \frac{f(\zeta)}{\zeta-z}d\zetaf(z)=2πi1​∮l​ζ−zf(ζ)​dζ 
​当 zz 不在积分围道内时，
 \oint_{l} {\frac{f(\zeta)}{\zeta-z}dz}=0 \oint_{l} {\frac{f(\zeta)}{\zeta-z}d\zeta}=0∮l​ζ−zf(ζ)​dζ=0  
​ f^{(n)}(z)=\frac{n!}{2\pi i}\oint_{l} {\frac{f(\zeta)}{(\zeta-z)^{(n+1)}}d\zeta}f(n)(z)=2πin!​∮l​(ζ−z)(n+1)f(ζ)​dζ 
 l:|\zeta-z|=Rl:∣ζ−z∣=R ​
若 f(\zeta)f(ζ) 在围道内解析，在围道上连续，
且有上界，即 f(\zeta) \leq Mf(ζ)≤M ，
则 |f^{(n)}(z)| \leq \frac{n!M}{R^n}∣f(n)(z)∣≤Rnn!M​ 
​刘维尔定理：
若 f(z)f(z) 在复平面上解析，
且当 z \rightarrow \inftyz→∞ 时有界，
则 f(z)f(z) 必为一常数
​模数定理：
若 f(z)f(z) 在闭区域中解析，
则它的模必在区域边界上达到极大值
​平均值定理（中值定理）：
 f(a)= \frac{1}{2 \pi } \int_{0}^{2 \pi} {f(a+Re^{i φ })d φ }f(a)=2π1​∫02π​f(a+Reiφ)dφ 



 **参考资料**
 [](https://zhimap.com/mmap/13e476df788b4cacbbbeceb7765918b9)