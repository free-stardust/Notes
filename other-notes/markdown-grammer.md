# Markdown 基本语法 + LaTex 公式
---
[TOC]
## 序
### 说明
- Markdown 是一种轻量级标记语言；
- Markdown 以纯文本形式编写文档，并最终以 HTML 格式发布，因此兼容一些 HTML 语法；
- Markdown 由 Aaron Swartz 和 John Gruber 共同设计，但遗憾的是，Aaron Swartz 于 2013 年 1 月自杀；
### 优点
- 语法简单，一般 0-15 分钟即可学会，学的最慢也不过 30 分钟；
- 其文件是易读、易写、易改的纯文本文件，文件以“.md”为后缀；
- 兼容 HTML，可以转换为 HTML 文件，同时借用 Typora 工具可以导出较为美观的 HTML 和 PDF；
- 适合做学习记录；
- 可以用来编写公众号文案；
### 缺点
- 缺点就是相比 word，需要记忆一些语法（但是其实也没啥大不了的）；
- 文档格式没有 word 那样多变，但是配合 Typora 主题即可弥补；
## 1 基本语法
### 1.1 标题
- 在想要设为标题的文字前面加 `#` 来表示；
```text
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
- 显示效果可自行测试；
### 1.2 字体
#### 1.2.1 加粗、斜体、斜体加粗、删除线
- 语法示例
  ```text
  **加粗文字**
  *斜体文字*
  ***斜体加粗文字***
  ~~删除线~~
  ++下划线++
  ==背景高亮==
  ```
- 显示效果如下
  **加粗文字**
  *斜体文字*
  ***斜体加粗文字***
  ~~删除线~~
  ++下划线++
  ==背景高亮==
#### 1.2.2 字体、字号、颜色
- 语法示例
  ```text
  <font face="黑体">我是黑体字</font>
  <font face="微软雅黑">我是微软雅黑</font>
  <font face="STCAIYUN">我是华文彩云</font>
  <font color=#0099ff size=12 face="黑体">黑体</font>
  <font color=gray size=5>gray</font>
  <font color=#00ffff size=3>null</font>
  ```
- 显示效果
  <font face="黑体">黑体</font>
  <font face="微软雅黑">微软雅黑</font>
  <font face="STCAIYUN">华文彩云</font>
  <font color=#0099ff size=5 face="黑体">黑体 size=5</font>
  <font color=gray size=5>灰色</font>
  <font color=#00ffff size=3>颜色 #00ffff</font>
### 1.3 引用
- 语法示例
    ```text
    >一级引用
    >>二级引用
    >>>三级引用
    ```
- 显示效果如下
    >一级引用
    >>二级引用
    >>>三级引用
### 1.4 链接
#### 1.4.1 一般格式超链接
- 语法格式
    ```text
    [链接说明](链接地址 "链接标题") 

    注：其中的连接标题可加可不加，其内容在鼠标悬停时显示
    ```
- 语法示例
    ```text
    点击进入[GitHub](https://github.com/ "GitHub")
    ```
- 效果如下
  点击进入[GitHub](https://github.com/ "GitHub")
#### 1.4.2 参开形式的链接
- 语法格式
    ```text
    [链接说明][1]   

    [1]:链接地址
    ```
- 语法示例
    ```text
    点击进入[GitHub][1] 

    [1]:https://github.com/
    ```
- 效果如下
    点击进入[GitHub][1]
    [1]:https://github.com/
#### 1.4.3 注脚
- 语法示例
    ```text
    学习 Markdwon[^1]

    [^1]:Markdown 是一种纯文本标记语言
    ```
- 效果如下
    学习 Markdwon[^1]
    [^1]:Markdown 是一种纯文本标记语言
### 1.5 列表
>**说明**：列表嵌套只需要进行 Tab 缩进即可。
#### 1.5.1 无序列表
- 语法示例
    ```text
    注：*、-、+表示无序列表

    * 无序列表 1
    - 无序列表 2
    + 无序列表 3
    ```
- 显示效果
    * 无序列表 1
    - 无序列表 2
    + 无序列表 3
#### 1.5.2 有序列表
- 语法示例
    ```text
    注：数字 + 英文句点 + 空格 + 内容

    1. 有序列表 A
    2. 有序列表 B
    3. 有序列表 C
    ```
- 显示效果
    1. 有序列表 A
    2. 有序列表 B
    3. 有序列表 C
### 1.6 插入图像
- 语法格式
```text
![图片说明](图片地址 "图片标题")
```
- 语法示例
```text
注：如果是 Typro 预览，图片链接前最好空一行，这样显示的图片就会居中
![插入图片](./assets/markdown-grammer-01.gif "吞噬")
```
- 显示效果

![插入图片](./assets/markdown-grammer-01.gif "吞噬")
### 1.6 表格
- 语法格式
```text
表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

说明：
    1. 第二行分割表头和内容（有一个就行，为了对齐，多加了几个）；
    2. 文字默认居左；
    3. 两边加“:”表示文字居中；
    4. 右边加”:“表示文字居右；
```
- 语法示例
表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容
### 1.7 代码
#### 1.7.1 行代码
- 语法格式
```text
说明：使用反引号（键盘 Tab 上面那个按键英文状态下按出的符号）；

`行代码`
```
- 语法示例
`行代码`
#### 1.7.2 块代码
- 语法格式
```语言名称标记
说明：由于此处使用代码块的形式展示语法，所以无法正常显示出```，故采用···替换表示，实际使用，请读者自行替换为```；

···语言名称
第一行代码；
第二行代码；
第三行代码；
···
```
- 语法示例
```text
注意：替换···为```即为实际语法

···c
#include <stdlib.h>

int main()
{
    printf("Hello World!");
}
···
```
- 示例效果
```c
#include <stdlib.h>

int main()
{
    printf("Hello World!");
}
```
- 代码块支持的语言名称及其关键字标记
名称|关键字
:-:|:-:
AppleScript|applescript
ActionScript 3.0|actionscript3, as3
Shell|bash, shell
ColdFusion|coldfusion, cf
C|cpp, c
C#|c#, c-sharp, csharp
CSS|css
Delphi|delphi, pascal, pas
diff&patch|diff patch
Erlang|erl, erlang
Groovy|groovy
Java|java
JavaFX|jfx, javafx
JavaScript|js, jscript, javascript
Perl|perl, pl, Perl
PHP|php
text|text, plain
Python|py, python
Ruby|ruby, rails, ror, rb
SASS&SCSS|sass, scss
Scala|scala
SQL|sql
Visual Basic|vb, vbnet
XML|xml, xhtml, xslt, html
Objective C|objc, obj-c
F#|f#, f-sharp, fsharp
R|r, s, splus
matlab|matlab
swift|swift
GO|go, golang
### 1.8 分隔线
- 独立一行使用“---”或者“***”即为分隔线
- 显示效果如下
---
## 1.9 上标、下标
- 语法示例
```text
上标<sup>上标</sup>
下标<sub>下标</sub>
```
- 语法示例
上标<sup>上标</sup>
下标<sub>下标</sub>
## 1.10 特殊字符
特殊字符|字符含义|字符实体（去掉+）
:-:|:-:|:-:
 |空格|&+nbsp;
<|小于|&+lt;
>|大于|&+gt;
&|与|&+amp;
￥|人民币|&+yen;
©|版权|&+copy;
®|注册商标|&+reg;
°|度|&+deg;
±|正负号|&+plusmn;
×|乘号|&+times;
÷|除号|&+divide;
²|平方|&+sup2;
³|立方|&+sup3;
## 1.11 插图目录
- 在文档开头插入独立一行插入`[TOC]`即可；
## 2 LaTex 公式
>**说明**：LaTex 公式符号复杂多样，但没必要刻意记忆，可以在使用的过程中慢慢熟练，自然能记住，详细可参考 [LaTex Mathematical Symbols](https://www.caam.rice.edu/~heinken/latex/symbols.pdf)。
### 2.1 行内公式
- 语法示例
```text
$E=mc^2$
```
- 显示效果
$E=mc^2$
### 2.2 行间公式
- 示例代码1
```text
$$
\frac{\partial}{\partial \theta_0}J(\theta_0,\theta_1)=\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})
$$
```
- 显示效果1
$$
\frac{\partial}{\partial \theta_0}J(\theta_0,\theta_1)=\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})
$$
- 示例代码2
```text
$$
\begin{array}{l}
    \text{Repeat}\ \{\\
    \qquad \theta_j:=\theta_j-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{j}^{(i)}\ \ \ (\text{for}\ j=0,1,2,\ldots,n)\\
    \}\\
    \ \\
    \theta_0:=\theta_0-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{0}^{(i)}\\
    \theta_1:=\theta_1-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{1}^{(i)}\\
    \theta_2:=\theta_2-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{2}^{(i)}\\
    \ldots
\end{array}
$$
```
- 显示效果2
$$
\begin{array}{l}
    \text{Repeat}\ \{\\
    \qquad \theta_j:=\theta_j-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{j}^{(i)}\ \ \ (\text{for}\ j=0,1,2,\ldots,n)\\
    \}\\
    \ \\
    \theta_0:=\theta_0-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{0}^{(i)}\\
    \theta_1:=\theta_1-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{1}^{(i)}\\
    \theta_2:=\theta_2-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{2}^{(i)}\\
    \ldots
\end{array}
$$
- 示例代码3
```text
$$
\theta=
\left[ \begin{array}{c}
  \theta_0\\
  \theta_1\\
  \theta_2\\
  \vdots\\
  \theta_n
\end{array} \right];\ 
\delta=
\left[ \begin{array}{c}
  \delta_0\\
  \delta_1\\
  \delta_2\\
  \vdots\\
  \delta_n
\end{array} \right]; \ 
\delta_j=\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})x_{j}^{(i)},\ (j=0,1,\ldots,n)
$$
```
- 显示效果3
$$
\theta=
\left[ \begin{array}{c}
  \theta_0\\
  \theta_1\\
  \theta_2\\
  \vdots\\
  \theta_n
\end{array} \right];\ 
\delta=
\left[ \begin{array}{c}
  \delta_0\\
  \delta_1\\
  \delta_2\\
  \vdots\\
  \delta_n
\end{array} \right]; \ 
\delta_j=\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})x_{j}^{(i)},\ (j=0,1,\ldots,n)
$$
- 示例代码4
```text
$$
\left. \begin{array}{r}
  h_{\theta}(x)=\theta^{T}x\\
  g(z)=\frac{1}{1+e^{-z}}
\end{array}  
\right\} \Rightarrow
h_{\theta}(x)=\frac{1}{1+e^{-\theta^{T}x}}
$$
```
- 显示效果4
$$
\left. \begin{array}{r}
  h_{\theta}(x)=\theta^{T}x\\
  g(z)=\frac{1}{1+e^{-z}}
\end{array}  
\right\} \Rightarrow
h_{\theta}(x)=\frac{1}{1+e^{-\theta^{T}x}}
$$