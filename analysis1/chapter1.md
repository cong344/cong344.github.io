<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# 第一章 极限与连续

## 1.1 数列极限

### 有界与无界

+ 有上界: $\forall x\in A, x \leq L $ . 有下界同理.
+ **有界**: $\forall x\in A, |x| \leq L $ .

当数列有界时, 其有**无数个**上界或下界.

+ **确界**: 具体的定义略. 确界是**唯一**的.
  - 上确界 $\sup A$ (最小的上界).
  - 下确界 $\inf A$ (最大的下界).

### 数列极限的定义

$$
\forall \varepsilon>0,\   \exist N \in \mathbb{N^+}.\quad \text{若}\ n>N,\ |x_n-a|<\varepsilon.
$$ 

此时, 称 $\displaystyle\lim_{n\to\infty}x_n=a $ .

+ 利用定义证明: 
  - 写出 $|x_n-a|<\varepsilon $ .
  - 化简, 在合适时进行**放缩**, 得到关于n与 $\varepsilon$ 的不等式.
    - *注1*: 在这一步时, 只有得到形如 $n>f(\varepsilon) $ 才是成功的放缩.
    - *注2*: 由于这里的 $\varepsilon$ 通常是个**小量**, 因此其一般位于分母. 例如 $f(\varepsilon)=\frac{2}{\varepsilon^2} $ .
  - <font color = red> 令 $N=[f(\varepsilon)] $ </font> , 则 $n>N$ 时, 有 $|x_n-a|<\varepsilon $ .

数列极限的逆命题即**数列发散**, 常常用于证明数列极限不存在: 

$$
\exist \varepsilon_0 > 0,\ \forall N \in \mathbb{N^+}.\quad \text{若}\ n>N,\ |x_n-a|>\varepsilon_0.
$$

在证明时, 只需要根据题目情况取合适的 $\varepsilon_0$ 即可.

### 数列极限性质

+ 唯一性
+ 有界性: 若 $\{x_n\} $ 收敛, 则 $|x_n|<L $ .
+ **保序性**: $\displaystyle\lim_{n\to\infty}x_n=a,\ \displaystyle\lim_{n\to\infty}y_n=b,\ a<b\ \Rightarrow \exist N \in \mathbb{N^+}\  \text{若}\ n>N,\ x_n<y_n$ .
+ 保号性: 保序性的特别情况, 即 b = 0 时.
+ 运算法则: 加减乘除. 
    - **前提: 极限存在**.
    - 作除法时, 要求分母不为0.
+ **夹逼定理**

### 数列极限的敛判法

#### 单调有界原理

$$
\text{单增有上界, 单减有下界的数列必有极限.}
$$

对于给出**递归式**形如 $x_n=f(x_{n-1}) $ 的题目, 一般使用单调有界原理. 步骤如下: 

+ 证明**单调性**.
  - 1. 直接由递归式可以看出.
    - **作差法**: 比较 $x_{n+1}-x_n $ 与 0.
    - **作比法**: 比较 $\frac{x_{n+1}}{x_n} $ 与 1. 
  - 2. 写出 $x_{n+1}-x_n $ , 分别带入递归式, 得到含有 $x_n-x_{n-1} $ 的式子. 若两者**同号**, 则说明单调. 带入 $n=1 $ 来判断增减性.
  - 3. 设函数 $y=f(x) $ , 则 $x_n=f(x_{n-1}),\ x_{n+1}=f(x_n) $ . 由**Lagrange中值定理**, $f'(\xi)=\frac{f(x_n)-f(x_{n-1})}{x_n-x_{n-1}}=\frac{x_{n+1}-x_n}{x_n-x_{n-1}} $ . 故 $\boxed{f'(x)>0} $ 时, 数列单调.
  - 4. 若发现 $x_{n+1}-x_n $ 与 $x_n-x_{n-1} $ 不同号, 则**分奇偶讨论**, 将数列分成奇偶两个子列, 只需证明  $x_{n+2}-x_n $ 与 $x_n-x_{n-2} $ 同号.
- 证明**有界性**.
  - 1. 由递归式可以直接放缩得到.
  - 2. 极限值即上(下)界. 设极限值为L, 利用**数学归纳法**: 
    - $x_1<L $
    - 设 $x_n<L $
    - $x_{n+1}=f(x_n)<L $
- **求出极限值**.
  - 利用**不动点**, 即 $L=f(L) $ .
  - 求得多个极限值时, 可以采用**带回极限值**或**判断上下界**等方法进行舍解.

#### Cauchy收敛准则

$$
\forall \varepsilon>0,\ \exist N\in\mathbb{N^+}.\quad \text{若}\ n>N,\ \forall p \in \mathbb{N^+},\ |x_{n+p}-x_n|<\varepsilon.
$$

此时, 称 $x_n $ 为**Cauchy列**. Cauchy列必收敛.

对于**和式**的极限, 一般使用Cauchy收敛准则. 步骤如下:

+ 求出 $|x_{n+p}-x_n|$.
+ 进行放缩. 在放缩中需要**消去p**, 得到n位于分母的式子.
  - 裂项, 放缩掉尾项.
  - 利用等比数列求和, 有时可消去p.
+ 得到 $|x_{n+p}-x_n|<f(n)<\varepsilon $ .
  - 令 $N=f^{-1}(\varepsilon) $ (同极限的定义).
  - 在极限易求的情况, 直接使用 $\displaystyle\lim_{n\to\infty}f(n)=0 $ .

用Cauchy准则证明**发散**: 选取合适的 $\varepsilon_0,\ p $ .

$$
\exist\varepsilon_0>0,\ \forall N\in\mathbb{N^+}.\quad \text{若}\ n>N,\ \exist p \in \mathbb{N^+},\ |x_{n+p}-x_n|>\varepsilon_0.
$$

## 1.2 函数极限

### 极限的定义

利用 $\epsilon - \delta $ 语言进行描述.

+ $\displaystyle\lim_{x\to x_0}f(x)=A $
+ $\displaystyle\lim_{x\to \infty}f(x)=A $

区分**左右极限**: 
+ $x\to x_0^+,\ x\to x_0^- $
+ $x\to +\infty,\ x\to -\infty $

**极限存在**的条件: $\displaystyle\lim_{x\to x_0^+}f(x)=\displaystyle\lim_{x\to x_0^-}f(x)=A $ .

### Heine定理

联系了数列极限与函数极限. 具体内容略, 这里只写出其应用.

+ 将数列极限转化为函数极限. 例如:
  - <font color = red> 由Heine定理, </font> $\displaystyle\lim_{n\to \infty}n\sin\frac{1}{n} = \displaystyle\lim_{x\to 0}\frac{\sin x}{x} $ .
- 给出一种证明函数**极限不存在**的方法: 取 $\{x_n'\},\ \{x_n''\},\ \displaystyle\lim_{n\to \infty}x_n'=\displaystyle\lim_{n\to \infty}x_n''=x_0 $ , 但 $\displaystyle\lim_{n\to \infty}f(x_n')\neq\displaystyle\lim_{n\to \infty}f(x_n'') $ .
  - 例如, 对 $f(x)=\sin\frac{1}{x} $ , 可以取 $x_n'=\frac{1}{2n\pi},\ x_n''=\frac{1}{2n\pi+\frac{\pi}{2}} $ .
  - 注: 区分与证明**非一致连续**的关系: 一致连续要求的是函数值相减, 而非极限的唯一性.

函数极限的运算性质, 敛判法则与数列极限基本一致, 不再赘述.

*注*: 一点处的极限是**局部性质**. 因此有界性, 保序性只在局部适用.


## 1.3 极限的计算

+ 简单极限: 直接利用连续性带值, 或依据极限的运算即可求得.
+ 利用**等价无穷小**的代换求极限.
  - *注*: 等价无穷小只可以<font color = red> 代换因式 </font> .
+ 数列**平均值**的极限:
  - 算术平均: $\displaystyle\lim_{n\to \infty}\frac{\displaystyle\sum_{i=1}^nx_i}{n}=\displaystyle\lim_{n\to \infty}x_n $ .
  - 几何平均: $\displaystyle\lim_{n\to \infty}\sqrt[n]{\displaystyle\prod_{i=1}^nx_i}=\displaystyle\lim_{n\to \infty}x_n  $ .
    - 推论: 若 $\displaystyle\lim_{n\to \infty}\frac{b_{n+1}}{b_n}=a,\ \displaystyle\lim_{n\to \infty}b_n=a^n $ .
  - **Stolz定理**: 若 $y_n $ 单增且趋于无穷大, 则 $\displaystyle\lim_{n\to \infty}\frac{x_n}{y_n}=\displaystyle\lim_{n\to \infty}\frac{x_{n+1}-x_n}{y_{n+1}-y_n} $ .
  - $\displaystyle\lim_{n\to \infty}\sqrt[n]{a^n+b^n+c^n}=max\{a,b,c\} $ . (可用夹逼定理证明)
- **分式**的极限(形如 $\displaystyle\lim \frac{f(x)}{g(x)} $ )
  + 若两者均为**多项式**: 
    + f(x) 次数低时, 极限为0.
    + f(x) 次数高时, 极限不存在.
    + 两针次数相同时, 极限为最高次系数之比.
  + 对于**未定式**(分子分母中含无穷大, 或分母为0): 
     - 使用**L'Hospita法则**: $\displaystyle\lim \frac{f(x)}{g(x)}=\displaystyle\lim \frac{f'(x)}{g'(x)} $ . *使用条件*: $f'(x) $ 在 $x_0 $ 的**邻域内**存在.
     - 对分子或分母进行**Taylor展开**, 一般展开至分子分母次数可相消的阶数.
   - 对于**导数定义**类极限: 进行配凑. 例如:

  $$
  \begin{aligned}
  &\lim_{x\to x_0} \frac{f(x_0+at(x))-f(x_0-bt(x))}{g(x)} \\
  &=\lim_{x\to x_0} a\frac{f(x_0+at(x))-f(x_0)}{at(x)}\cdot \frac{t(x)}{g(x)} + b\frac{f(x_0-bt(x))-f(x_0)}{-bt(x)}\cdot \frac{t(x)}{g(x)} \\
  &=[af'(x_0)+bf'(x_0)]\cdot \lim_{x\to x_0}\frac{t(x)}{g(x)}
  \end{aligned}
  $$

  *注*: 反之, 若已知形如 $\displaystyle\lim_{x\to0} \frac{f(x)}{x}=0 $ 的式子, 可以推得: $f(0)=0,\ f'(0)=0 $ .

  - 对于形如 $\frac{f(u_2)-f(u_1)}{v} $ 的极限, 可以使用**Lagrange中值定理**.

  $$
  \begin{aligned}
  &\exist \xi\in(u_1,u_2),\ f'(\xi)=\frac{f(u_2)-f(u_1)}{u_2-u_1} .\\
  &\therefore \lim \frac{f(u_2)-f(u_1)}{v}=\lim f'(\xi)\cdot\lim \frac{u_2-u_1}{v}
  \end{aligned}
  $$

  此时, 一般有 $\lim \xi = \lim u_2 = \lim u_1 $ , 相当于使用了夹逼定理.

+ 对于**非分式**的极限, 可以使用一些方法将其**化为分式**.
  - 对于**根式**的减法, 进行**分子有理化**.
  - 对于**分式之差**, 对其进行**通分**.
  - 对于变量在**幂次**上的, 将其化为乘法: $\lim u(x)^{v(x)}=\lim e^{v(x)\ln u(x)} $ .
    - 特别地, 形如 $1^\infty $ 形式的, 直接使用 **幂等函数公式**, 化为: $\exp(\lim v(x)[u(x)-1]) $ .
    - 注: 幂等函数公式*只能对函数整体使用*, 即使是因式也不可单独使用.
- **求和**的极限:
  - 利用**夹逼定理**, 将**分母**放缩为相同的形式, 便于求和.
  - 利用**定积分的定义**, 提取出 $\frac{1}{n},\ \frac{k}{n} $ ,有:

  $$
  \lim_{n\to\infty} \sum_{k=1}^n \frac{1}{n} f(\frac{k}{n}) =\int_0^1 f(x)\mathrm{d}x
  $$
- 用极限表示的**函数**: 有两种基本型, 可以组合形成许多不同的函数.
  - $f(x)=\displaystyle\lim_{n\to\infty}x^n $
  $$
  \begin{cases}
  0\qquad |x|<1 \\
  \infty\qquad |x|>1\\
  1 \qquad x=1 \\
  \text{视情况而定} \quad x=-1
  \end{cases}
  $$
  - $f(x)=\displaystyle\lim_{t\to\infty}e^{tx} $
   $$
  \begin{cases}
  0\qquad x<0 \\
  1 \qquad x=0 \\
  +\infty\quad x>0\\
  \end{cases}
  $$

## 1.4 函数的连续性

$$
\lim_{x\to x_0}f(x)=f(x_0)
$$

若在(a,b)的每个点都满足此条件, 则 f(x) 在区间 (a,b) 连续, 记作 $f(x)\in C(a,b) $ .

### 间断点的分类
- 第一类间断点: 左右极限均存在. 
  - **可去间断点**:  $\displaystyle\lim_{x\to x_0^-}f(x)=\displaystyle\lim_{x\to x_0^+}f(x) $ . 可能情况:
    - 分段函数.
    - f(x) 在 $x_0$ 处无定义.
  - **跳跃间断点**:  $\displaystyle\lim_{x\to x_0^-}f(x)\neq\displaystyle\lim_{x\to x_0^+}f(x) $ .
- 第二类间断点: 左右极限**至少有一个**不存在.
  - 无穷间断点
  - 振荡间断点

### 闭区间上连续函数性质

+ **有界性**定理: 闭区间上连续函数必有界.
+ **最大-最小值**定理: 闭区间上连续函数必存在最大值与最小值.
+ **零点定理**: $f(x)\in C[a,b],\ f(a)f(b)<0 $ , 则区间内至少有一个零点.
+ **介值定理**:  $f(x)\in C[a,b],\ f_{\min}(x)\leq\mu\leq f_{\max}(x) $ , 则区间内必有至少一个 $f(c)=\mu $ .
+ **Contor定理**: 闭区间上连续函数必**一致连续**.

### 一致连续

$$
\forall \varepsilon>0,\ \exist \delta>0.\quad \text{若}|x-x_0|<\delta,\ |f(x)-f(x_0)|<\varepsilon .
$$

**证明**一致连续:

+ 利用定义.
+ 证明函数符合**Lipschitz条件**: $\exist L>0,\ \forall x_1,x_2\in (a,b). \quad |f(x_1)-f(x_2)|\leq L|x_1-x_2| $ .
+ 由**Lagrange中值定理**, $\exist |f'(\xi)|=\frac{|f(x_1)-f(x_2)|}{|x_1-x_2|}\leq L \Rightarrow f'(x) $ 在区间内有界.

证明非一致连续:

+ 利用定义的逆命题.
+ **反证法**: 假设数列 $\{x_n'\},\ \{x_n''\},\ \displaystyle\lim_{n\to \infty}|x_n'-x_n''|=0 $ , 但总有 $\displaystyle\lim_{n\to \infty}|f(x_n')-f(x_n'')|\geq \varepsilon_0 >0 $ .
