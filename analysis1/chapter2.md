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

# 第二章 一元函数微分学

## 2.1 导数与微分

$$
\frac{\mathrm{d}y}{\mathrm{d}x} = \lim\frac{\Delta y}{\Delta x}
$$

导数, 微分是一类特殊的极限.

+ **可导**的条件: 左右邻域内有定义.

*注*: 求导公式只能在**开区间**使用. 在端点处, 需要使用导数的定义求解.

+ **反函数**的导数
  - $(f^{-1})'(y)=\displaystyle\frac{1}{\frac{\mathrm{d}y}{\mathrm{d}x}} $ .
  - *注*: 这里的自变量变成了y, 求值时先将x转换为y再带入.
- **复合函数**的导数: **链式法则**.
- **对数求导法**: 两侧先取对数, 再求导.
   - 连乘, 连除函数
   - 幂指函数
- **参数方程**的导数

    $$
    \begin{cases}
    x=\varphi(t) \\
    y=f(t)
    \end{cases} \Rightarrow 
    \frac{\mathrm{d}y}{\mathrm{d}x}=\frac{f'(t)}{\varphi'(t)},\quad \frac{\mathrm{d}^2y}{\mathrm{d}x^2}=\frac{\frac{\mathrm{d}y}{\mathrm{d}x}}{\mathrm{d}t}\cdot\frac{\mathrm{d}t}{\mathrm{d}x}
    $$

- **隐函数**的导数: 将y看作关于x的复合函数, 两侧分别求导.

### 高阶导数的求法

+ 对于基本初等函数:
  - $y=a_0x^n+\ldots+a_{n-1}x+a_n $
    - $y^{(n)}=a_0n! $
    - $y^{(k)}=0\qquad(k>n) $
  - $y=a^x $
    - $y^{(n)}=a^x(\ln a)^n $
    - 特别地, 若 $a=e,\ y^{(n)}=e^x $ .
  - $y=\frac{1}{x} $
    - $y^{(n)}=\frac{(-1)^n\cdot n!}{x^{n+1}} $
    - 同样地, $(\ln x)^{(n)}=\frac{(-1)^{n-1}\cdot (n-1)!}{x^{n}} $ .
  - $y=\sin x $
    - $y^{(n)}=\sin (x+n\cdot\frac{\pi}{2}) $
- 对于初等函数的组合:
    - 化假分式为**真分式**, 转化为多项式+ $\frac{1}{f(x)}$ 的形式.
    - **因式分解**, 使形如 $\frac{1}{f(x)}$ 之式的分母都可化为一次式.
    - 对于**相乘**的情况, 使用**Leibniz公式**: $(uv)^{(n)}=\displaystyle\sum_{k=0}^n C_n^k u^{(n-k)} v^k $ . (与二项式定理形式类似)

*注*: Leibniz公式只适用于u为**低次多项式**的情况, 此时阶数高于其次数的导数为0, 结果可以控制为有限项.

特别地, 偶函数的奇次导与奇函数的偶次导必为**奇函数**. 利用奇函数 $f(0)=0 $ 的性质, 可以直接解决一部分问题.

## 2.2 微分学基本定理

*注*: 区分以下概念:

+ 零点: $f(x_0)=0$ , $x_0 $ 这个**横坐标**是零点.
+ 驻点: $f'(x_0)=0 $ , $x_0 $ 这个**横坐标**是驻点.
+ 极值点: $f(x)$ 在 $x_0 $ 处取极值, $x_0 $ 这个**横坐标**是极值点.
+ 拐点: $f(x)$ 在 $x_0 $ 处凸凹性改变, <font color = red> $(x,y)$ 这个点 </font> 是拐点.

---

*注*: 下面的定理都要求 $f(x)\in C[a,b],\ f(x)\in D(a,b) $ , 下面将其从略.

+ **Fermat引理**
  - $x_0$ 是 f(x) 的极值点 $\iff\ x_0$ 是 f(x) 的驻点.
  - 推论-**Darboux零点定理**: $f'_+(a)f'_-(b)<0 \Rightarrow \exists \xi\in(a,b),\ f'(\xi)=0 $ . 结合**极限的局部保号性**, 这常常用来证明驻点的存在.
- **Rolle中值定理**
  - $f(a)=f(b) \Rightarrow \exists\xi\in(a,b),\ f(\xi)=0 $ .
- **Lagrange中值定理**
  - $\exists \xi\in(a,b),\ f'(\xi)=\frac{f(b)-f(a)}{b-a} $ .
- **Cauchy中值定理**
  - $\exists\xi\in(a,b),\ \frac{f'(\xi)}{g'(\xi)}=\frac{f(b)-f(a)}{g(b)-g(a)} $ . 

### 用中值定理证明等式

#### 单变量情况

+ 只含一阶导数.
  - 经过移项, 将等式改写为 $f'(\xi)+f(\xi)g(\xi)=0 $ .
  - **构造辅助函数** $F(x)=f(x)e^{\int g(x)\mathrm{d}x} $ , 即证 $F'(\xi)=0 $ .
  - 找到两个点 $F(a)=F(b)=0 $ .
  - 由Rolle定理, 得证.
- 含多阶导数. 这种情况没有通法, 要具体情况具体分析.
  - *方法1*: 补**邻阶**. 例如: 若证 $f(\xi)=f'''(\xi) $ , 则设 $g(x)=f(x)+f'(x)+f''(x) $ , 只需证 $g(\xi)=g'(\xi) $ .
  - *方法2*: 添加"没用的常数". 例如: 若证 $f''(\xi)+f'(\xi)=1 $ , 设 $F(x)=(f'(x)\textcolor{red}{-1})'+(f'(x)-1) $ , 只需证 $F(x)=0 $ .
  - *方法3*: 逐次使用Rolle定理. 例如: 若证 $f''(\xi)=0 $ , 需证存在2个相等的 $f'(x) $ , 这需证存在3个相等的 $f(x)$ . 根据分析逐层证明即可.

#### 双中值问题

- 不要求 $\xi\neq\eta$ 时:
    - 利用**Cauchy中值定理**, 配凑出 $\frac{f'(\eta)}{g'(\eta)}=\frac{f(b)-f(a)}{b-a} h(a,b) $ .
    - 由**Lagrange中值定理**, $\frac{f'(\eta)}{g'(\eta)}=f'(\xi) h(a,b) $ .
- 要求 $\xi\neq\eta$ 时: <font color = red>设置中间点 $x_0$  </font> .
    - $\exists\xi\in(a,x_0),\ f'(\xi)=\frac{f(x_0)-f(a)}{x_0-a};\ \exists\eta\in(x_0,b),\ f'(\eta)=\frac{f(b)-f(x_0)}{b-x_0} $ . 
    - 中间点的要求: 将 $f'(\xi),f'(\eta) $ 带入原等式, 等式得证.
    - **寻找中间点的方法**:
      - 设中间点为c, 带入找到关于c的等式. (计算量一般较大, 采取"先猜, 后验证" 的方法.)
      - 对于形如 $\frac{\lambda_1}{f'(\xi)}+\frac{\lambda_2}{f'(\eta)}=b-a $ 型, 函数值位于分母上, 要求**中间点的函数值成比例**, 即: $\frac{f(x_0)-f(a)}{f(b)-f(x_0)}=\frac{\lambda_1}{\lambda_2} $ .
      - 对于形如 $\lambda_1f'(\xi)+\lambda_2f'(\eta)=f(b)-f(a) $ 型, 自变量位于分母上, 要求**中间点到两侧距离成比例**, 即 $\frac{x_0-a}{b-x_0}=\frac{\lambda_1}{\lambda_2} $ .

### Taylor公式

$$
f(x)=\sum_{k=0}^n \frac{f^{(k)}(x_0)}{n!} (x-x_0)^k + o((x-x_0)^n)
$$

+ **Peano余项**: $o((x-x_0)^n)$ .
+ **Lagrange余项**: $\frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}\quad (\xi\in(x_0,x)) $ .
+ 特别地, $x_0=0$ 时, 称为**Maclaurin公式**.

#### 求函数Taylor公式的方法

+ 初等函数的Maclaurin公式:
  - $e^x=1+x+\frac{1}{2!}x^2+\ldots+\frac{1}{k!}x^k+\ldots+o(x^n) $
  - $\sin x=x-\frac{1}{3!}x^3+\frac{1}{5!}x^5+\ldots+\frac{(-1)^{2k-1}}{(2k-1)!}x^{2k-1}+\ldots+o(x^{2n}) $
  - $\ln(x+1)=x-\frac{1}{2}x^2+\frac{1}{3}x^3+\ldots+\frac{(-1)^{(k-1)}}{k}x^k+\ldots+o(x^n) $
  - $\frac{1}{1-x}=1+x+x^2+\ldots+x^k+\ldots+o(x^n) $
- **间接法**: 利用上述已知的Maclaurin公式, 进行**变形**.
  - 将所求函数化为 $f(x-x_0) $ 的形式, 其中 f(x) 是已知初等函数.
  - 对于有理分式, 只需将分母裂项并展开, 最后将分子与其相乘. *注*: 这要求分子为多项式函数, 因为Taylor公式需要保证其**结果为多项式**.
- 对于难以变形的函数, 可以采用**求导**或**积分**
  - 若该函数是某个简单函数的导数, 先对原函数展开, 再**求导**. 例如: $\frac{1}{x^2}=\frac{\mathrm{d}}{\mathrm{d}x}(-\frac{1}{x}) $ .
  - 若该函数的导数是某个简单函数, 先对其导数展开, 再**积分**. 例如 $\arctan x=\int \frac{1}{1+x^2} $ .

#### Taylor公式的应用

+ 求无穷小阶数或极限.
  - 对分子或分母进行展开, 这里常常需要用到**高阶无穷小的运算性质**:
    -  $o(x^m)\pm o(x^n) = o(x^k),\ k=\min\{m,n\} $
    -  $o(x^m)\cdot o(x^n)=x^m\cdot o(x^n)=o(x^{m+n}) $
- 证明等式或不等式.
    - 对于**可导阶数**高的函数, 展开到(n-1)阶, 利用Lagrange余项进行比较.
- **求高阶导数**: 利用直接法=间接法.
  - 由直接法, $x^n $ 前系数为 $\frac{f^{(n)}(x_0)}{n!} $ .
  - 由间接法, 可求得 $x^n $ 前系数为 $g(n) $ .
  - 令两者相等, 得到 $f^{(n)}(x_0)=n!g(n) $ .

## 2.3 函数的性态

+ 单调性: 求导得到, 常用于证明函数不等式. (对于常数不等式, 常常将某一常数转为x而得到函数不等式.)
+ 极值与最值: **驻点**与<font color = red> 不可导的点 </font> 均为可能的极值点.
+ **渐近线**.
  - 垂直渐近线: 在所有的**无穷间断点**处.
  - 水平渐近线: $\displaystyle\lim_{x\to\infty}f(x)=b $ .
  - **斜渐近线**( $y=ax+b$ ): 

$$
\begin{cases}
\displaystyle\lim_{x\to\infty}\frac{f(x)}{x}=a \\
\displaystyle\lim_{x\to\infty}[f(x)-ax]=b
\end{cases}
$$

- *注1*: $+\infty,\ -\infty$ 的结果可能不一样.
- *注2*: a与b中任意一个不存在, 则斜渐近线不存在.

### 函数的凸凹性

**下凸函数**的等价定义(上凸同理):

1. $p_1+p_2=1,\ f(p_1x_1)+f(p_2x_2)\leq p_1f(x_1)+p_2f(x_2) $ .
2. $f''(x)\geq 0 $ .
3. $f(x_0)+f'(x_0)(x-x_0)\leq f(x) $

对于1式, 若将p换为由积分表示的权重函数, 便可得**Jensen不等式**: (其中, $\varphi(x)$ 是下凸函数)

$$
\varphi\left(\frac{\int_a^b xf(x)\mathrm{d}x}{\int_a^b f(x)\mathrm{d}x}\right) \leq\frac{\int_a^b \varphi(x) f(x)\mathrm{d}x}{\int_a^b f(x)\mathrm{d}x}
$$

在大多数题目的证明中, 一般选取合适的 $x_0$ 点, 写出3式, 再将两侧积分. 事实上, 这便是Jensen不等式的另一种写法.
