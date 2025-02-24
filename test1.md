
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

# Hello World!
## 更小的标题？
### 下一级标题
#### 再下一级
段落之间需间隔一行

Like This.
**同一段之间就可以随意。**
加粗是由快捷键CRTL+B做到的，当然也可以在需要加粗的文本两侧加上两个*，比如**这样**。

而一个*号则表示斜体，比如

*Quantum Physics*

引用可以用>符号做到，比如：

>“科学技术是第一生产力”

可以使用LATEX公式，行内添加$符号，公式块则使用两个该符号。

比如 $C:x^2 + y^2 = 1$ 是一个行内公式，而

$$
\begin{cases}
x=\rho\cos\theta \\
y=\rho\sin\theta \\
\end{cases}
$$

三条横线即可表示分割线，比如：

---

两个=号可以表示高亮，==Like this==.

行内代码使用`包起来：

`print('hello world')`

这也可以用来起到给文字增加强调的作用，`比如这样`。

在添加 $\LaTeX$ 公式时，利用\boxed{}命令也可以使公式加上框，比如：

$$
\boxed{\vec{F}=m\vec{a}}
$$

**注**:github不支持此语法,我们只能使用VScode查看。


插入超链接时，利用：`[超链接名称](链接地址)`

比如：[这里](https://www.baidu.com)。

$$
\textbf{公式块内部使用中文}
$$

````
**代码块内部使用中文**
````

