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

## 第一章 矩阵

> 矩阵是数的拓展。

### 1.1 矩阵类型

下面给出若干**不同类型**的矩阵。

+ **方阵**：n*n矩阵
+ **向量**：
  - 行向量 - n*1矩阵
  - 列向量 - 1*n矩阵
+ **零矩阵**：所有元素均为0，记作 $O_{m\times n}$ 。
+ **对角矩阵**：除主对角线外元素均为0，记作 $diag(a_{11},a_{22},\ldots,a_{nn})$ 。
+ **数量矩阵**：对角线元素相同的对角矩阵，即 $diag(k,k,\ldots,k)$ 。
+ **单位矩阵**： $E_n=diag(1,1,\ldots,1)$ 。
+ **基本矩阵**：除 $a_{ij}=1$ 外其余元素均为0，记为 $E_{ij}$ 。对任意矩阵有 $A=\sum a_{ij}E{ij}$。
+ **对称矩阵**：矩阵的元素关于对角线对称，即 $a_{ij}=a_{ji}$ 。满足 $A^T=A$ 。（注：对角线元素不必相同）
+ **反对称矩阵**： $a_{ij}+a_{ji}=0$ 。因此，对角线元素必须全为0。
+ **初等矩阵**：将单位矩阵进行初等变换后的矩阵。
  - 对换变换： $E(i,j)$
  - 倍乘变换： $E(i,(k))$
  - 倍加变换： $E(i,j(k))$
+ **行阶梯形矩阵**：矩阵元素均位于上三角内。
+ **行最简形矩阵**：在行阶梯形的基础上，要求**非零首元**均为1，且非零首元列只有其自己一个元素。
+ **等价标准型**：对行最简形进行**列变换**后，得到的矩阵形如 $E_{m\times n}^{(r)}= 
\left(
\begin{matrix}
  E_r & O \\ 
  O & O \\
\end{matrix}
\right)$ 。

<u>*注*：行阶梯形、行最简形仅需要行变换，而行阶梯形则同时需要行变换与列变换。</u>

*几何意义*：矩阵对应于一种**线性变换**，以二维情况为例，矩阵A可以写作：

$$
A=\begin{pmatrix}
  a & b \\ 
  c & d
\end{pmatrix}=(\hat{i'},\hat{j'})
$$

这里， $\hat{i'},\hat{j'}$ 便表示了线性变换后基向量的位置。对于非方阵的情况，则说明该线性变换增加或减少了空间的维数。

### 1.2 矩阵运算

下面给出矩阵的若干**运算**。

+ **加法**：对应矩阵元素相加。（要求矩阵**同型**） $c_{ij}=a_{ij}+b_{ij}$
+ **数乘**：对每个元素同时乘以相同的系数。 $kA=(ka_{ij})_{m\times n}$

加法与数乘统称 **`线性变换`** 。

+ **乘法**：若C=AB，则 $c_{ij}=\displaystyle\sum_{k=1}^n a_{ik}b_{kj} $ 。

---

#### 矩阵乘法性质

+ **有结合律**： $A(BC)=(AB)C$
  - **eg1**：对列向量 $\alpha, \beta$ ，求 $(\alpha\beta^T)^n$ :
$$
(\alpha\beta^T)^n=\alpha(\beta^T\alpha)^{n-1}\beta^T
$$

  这时，复杂的矩阵幂次被化为了一个数的幂次。
<br>

  - **eg2**：求 $(P^{-1}AP)^n$ ：
$$
(P^{-1}AP)^n=P^{-1}(APP^{-1})^{n-1}AP=P^{-1}A^nP
$$
  由此也可得到：对于多项式函数f(x)， $f(P^{-1}AP)=P^{-1}f(A)P$ 。<br><br>
  - **eg3**：列向量 $\alpha, \beta$ ，求 $\alpha\beta^T$ 的特征值(之一)。
$$
(\alpha\beta^T)\alpha=\alpha(\beta^T\alpha)=(\beta^T\alpha)\alpha
$$
  因此， $\beta^T\alpha$ 是其特征值，而 $\alpha$ 是其特征向量。
<br>

+ **无交换律**： $AB\neq BA$ 。特殊情况下 $AB= BA$ ，称为**可交换**，有如下情况：
  - 同阶对角矩阵
  - 与自己的逆矩阵相乘
  - **结论**：A与任意n阶方阵可交换 $\iff$ A为n阶数量矩阵
<br>

+ **特别的消去律**：
$$
\begin{cases} AB=AC \\ |A|\neq 0
\end{cases}\quad \Rightarrow B=C
$$
但仅仅是 $A\neq 0$ 则无法推出结论。
<br>

+ **矩阵多项式**： $f(A)=a_kA^k+\ldots +a_1A+a_0\color{red}E$ <br> *注*：结果仍为矩阵，常数项需要添加单位矩阵。
+ **初等矩阵乘法**：左乘初等矩阵相当于行变换，右乘初等矩阵相当于列变换，简记为 $\textcolor{red}{左行右列}$ 。
+ **特别情况1**：对于对角矩阵A,B，则 $C=AB=diag(a_{11}b_{11},\ldots,a_{nn}b_{nn})$ 。（只需对角元素相乘）
+ **特别情况2**：对于对角线元素均为0的k阶**Jordan块**，有 $J^k=O$ 。以3维情况为例：

$$
J=\begin{pmatrix}
  0 & 1 & 0 \\ 
  0 & 0 & 1\\
  0 & 0 & 0
\end{pmatrix},
\ J^2= \begin{pmatrix}
  0 & 0 & 1 \\ 
  0 & 0 & 0\\
  0 & 0 & 0
\end{pmatrix},
\ J^3=O
$$

乘法的*几何意义*：相当于对空间依次进行几个线性变换，顺序由右至左执行。

---

+ **转置**：若 $B=A^T$ ，则 $a_{ij}=b_{ji}$ 。
  
  简单性质： 
  - $(A^T)^T=A$
  - $(kA)^T=kA^T$
  - $(A+B)^T=A^T+B^T$
  - $(AB)^T=B^TA^T$
  
  其中，后两个性质尤为重要。
<br>

+ **求逆**：若AB=E，则 $B=A^{-1}$ 。

---

#### 逆矩阵的性质

+ 要求：A为**方阵**且 $|A|\neq 0$ 。
+ 基本运算性质：
  - $(A^{-1})^{-1}=A$  （逆矩阵的唯一性）
  - $(A^T)^{-1}=(A^{-1})^T$
  - $(AB)^{-1}=B^{-1}A^{-1}$
- **初等矩阵**的逆矩阵：
  - $(E(i,j))^{-1}=E(i,j)$ **【逆矩阵仍为自身】**
  - $[E(i(k))]^{-1}=E(i(\frac{1}{k}))$
  - $[E(i,j(k))]^{-1}=E(i,j(-k))$
  得到性质：**初等矩阵均可逆**。

+ **计算逆矩阵方法**：对于矩阵A，写出其与E的**增广矩阵**： $[A\quad E]$ ，则 $A^{-1}[A\quad E]=[E\quad A^{-1}]$ 。因此，对 $[A\quad E]$ ，做**初等行变换**得到 $[E\quad A^{-1}]$。

---

### 1.3 矩阵的行列式

可逆n阶**方阵**A的行列式可**沿任意行或列展开**（下面的例子是沿第i行展开的）：

$$
D_n=\sum_{k=1}^{n}a_{ik}A_{ik} \tag{\text{Laplace展开式}}
$$

其中，$A_{ik}$ 为**代数余子式**，定义为 $\color{red}(-1)^{i+k}\color{black}\times\text{去掉第i行与第j列后的n-1阶行列式}$ 。（*一定注意乘以前面控制正负的系数*）

#### 性质

+ $|A^T|=|A|$ （行与列是对称的）
+ $|AB|=|A||B|$
+ **线性性质**：
  - $\det(\alpha_1,\ldots,k\alpha_j,\ldots,\alpha_n)=k\det(\alpha_1,\ldots,\alpha_j,\ldots,\alpha_n)$ ，即 $|kA|=k^n|A|$ 。（*易错！*）
  - $\det(\alpha_1,\ldots,\alpha_{j1},\ldots,\alpha_n)+\det(\alpha_1,\ldots,\alpha_{j2},\ldots,\alpha_n)=\det(\alpha_1,\ldots,\alpha_{j1}+\alpha_{j2},\ldots,\alpha_n)$ 。由此， $|A+B|\neq |A|+|B|$ 。
- 与**初等变换**关系：
  - **对换变换**后，行列式变号。
  - **倍加变换**不改变行列式的值。
- 对**上/下三角矩阵** $A_n$ ， $|A|=\displaystyle\prod_{i=1}^{n}a_{ii}$ 。
- 若 $i\neq j$ ，则 $\displaystyle\sum_{s=1}^{n}a_{is}A_{js}=0$

#### 计算方法

+ 初等行变换，化为上三角形。
+ 按某行（列）展开。（一般选择0较多的行/列，但不绝对）
+ 求出递归式。

注：**Vandermonde行列式**

$$
D_n=\begin{vmatrix}
1 & \ldots & 1 \\
a_1 & \ & a_n \\
\vdots & & \vdots \\
a_1^{n-1} & \ldots & a_n^{n-1}
\end{vmatrix}=\prod_{1\leq i<j\leq n}(a_i-a_j)
$$

#### 应用

$A=(a_{ij})_n$ ，则A的**伴随矩阵** $A^*=(A_{\color{red}ji})_n$ （*留意各元素与其余子式的位置发生了行列互换*）。

两者之间存在关系： $AA^*=|A|E$ 。若 $|A|\neq 0$ （**非奇异**），则 $A^{-1}=\frac{1}{|A|}A^*$ 。

+ **Cramer法则**用处不大，略。

行列式的*几何意义*：描述方阵对应线性变换伸缩空间的比例。

### 1.4 矩阵的等价关系与秩

#### 等价关系的性质

+ 反身性： $A\cong A$
+ 对称性： $A\cong B \Rightarrow B\cong A$
+ 传递性： $A\cong B,\ B\cong C \Rightarrow A\cong C$

$A\cong B \iff$ 
+ A可由初等变换得到B
  - 初等行变换：**行等价**（行向量组等价）
  - 初等列变换：**列等价**（列向量组等价）
  *注*：列等价 $\neq$ 列等价

+ $A=PE_{m\times n}^{(r)}Q$ ，P、Q为可逆矩阵。
+ $r(A)=r(B)$

#### 秩（rank）

+ 定义：最大的非零子式阶数

*几何意义*：矩阵的列向量张成空间的维度。

+ 运算性质：
  - $r(A)=r(A^T)$
  - $r(A)=n \iff |A|\neq 0$ （**满秩**）

+ **秩的不等式** （*重要！*）
  - $\max\{r(A),r(B)\}\leq r[A\quad B]\leq r(A)+r(B)$
  - $r(A+B) \leq r(A)+r(B)$
  - $r(AB)\leq \min\{r(A),r(B) \} $
  - $r(A)+r(B)\leq r(AB)+n $
  - $r\begin{bmatrix}
  A & O \\ 
  C & B
\end{bmatrix}\leq
 r\begin{bmatrix}
  A & O \\ 
  O & B
\end{bmatrix} $

+ **重要结论**
  - $r(E_n-BA)=r(E_n-AB) $
  - $r(A^*)=\begin{cases}
 n \qquad r(A)=n \\
 1 \qquad r(A)=n-1 \\
 0 \qquad r(A)\leq n-2
\end{cases} $

### 1.5 分块矩阵运算性质

+ 加法、乘法：与正常矩阵相同
+ 转置：**整体转置**+每个子块**分别转置**
+ 求逆：
  - **分块对角矩阵**：对每个子块分别求逆
  - 其他情况，常用设逆矩阵来解决。如 $\begin{pmatrix}
  A & C \\ 
  O & B
\end{pmatrix}^{-1}=
\begin{pmatrix}
  A^{-1} & -CB^{-1}A^{-1} \\ 
  O & B^{-1}
\end{pmatrix}$

+ 行列式： $\begin{vmatrix}
  A & O \\ 
  C & B
\end{vmatrix}=|A||B|$
*注*：对$\begin{vmatrix}
  A & D \\ 
  C & B
\end{vmatrix},\ 
\begin{vmatrix}
  O & A \\ 
  C & B
\end{vmatrix}$ 均不可使用对角线法则，而常常使用**对换变换**（要注意乘以-1的次数）
