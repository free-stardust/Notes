## 吴恩达机器学习
---
### 1 绪论：初识机器学习
#### 1.1 应用领域
- **数据挖掘**
    - 网页点击数据；
    - 医疗记录；
    - 生物工程等数据集；
- **无法编写的程序**
    - 自动驾驶；
    - 手写体识别；
    - 自然语言处理；
    - 计算机视觉；
- **私人定制程序**
    - 智能推荐；
- **理解人类的学习过程和大脑**
#### 1.2 什么是机器学习
- **Arthur Samuel在1959年的定义**：在没有明确设置的情况下，是计算机具有学习能力的领域；
- **Tom Mitchell在1998年的定义**：计算机程序从经验E中学习，解决某一项任务T，进行某一性能度量P，通过P测定在T上的表现因经验而提高；
- #### 1.3 监督学习和无监督学习
- **监督学习 (Supervised Learning)**
    - 根据给定的算法和数据集，且该数据集包含了正确的答案，便可以对应给出任意给定一个数据的对应答案，即解决的是**回归问题**或者**分类问题**；
- **无监督学习 (Unsupervised Learning)**
    - 给算法大量的数据，要求其找出数据结构，即解决的是**聚类问题**；

### 2 单变量线性回归
#### 2.1 代价函数
- **假设函数**
    $$h_\theta(x)=\theta_0+\theta_1x$$
- **参数**
    $$\theta_0,\theta_1$$
- **代价函数**
    $$J(\theta_0,\theta_1)=\frac{1}{2m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^{2}$$
- **目标**
    $$\underset{\theta_0,\theta_1}\text{minimize}\ J(\theta_0,\theta_1)$$
    ><font size=2>**说明**：此处之所以是$\frac{1}{2m}$，原因是在按梯度下降法求最小值点时刚好可以把平方的2约掉，从而变为$\frac{1}{m}$，且不论是$\frac{1}{m}$，还是$\frac{1}{2m}$，最后计算得出的$\theta_0$、$\theta_1$都是一样的。</font>
#### 2.2 梯度下降法
- **算法描述**
    $$\begin{array}{lc} 
        \text{repeat until convergence}\ \{\\
        \qquad \theta_j:=\theta_j-\alpha\frac{\partial}{\partial \theta_j}J(\theta_0, \theta_1)\qquad (\text{for}\ j=0\ \text{and}\ j = 1 \\
        \}
    \end{array}$$
    > <font size=2>**说明**：此处的“:=”表示赋值运算。</font>
- **同步更新**
    $$\begin{array}{l} 
        temp0:=\theta_0-\alpha\frac{\partial}{\partial \theta_0}J(\theta_0, \theta_1) \\ 
        temp1:=\theta_1-\alpha\frac{\partial}{\partial \theta_1}J(\theta_0, \theta_1) \\ 
        \theta_0:=temp0 \\ 
        \theta_1:=temp1
    \end{array}$$
- **$J(\theta_0, \theta_1)$的偏导数**
    $$\frac{\partial}{\partial \theta_0}J(\theta_0,\theta_1)=\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})$$

    $$\frac{\partial}{\partial \theta_1}J(\theta_0,\theta_1)=\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})\cdot x^{(i)}$$
### 3 线性代数回顾
#### 3.1 需要用到的线性代数基础知识
><font size=2>**说明**：本部分回顾的线代都很基础，没有涉及深入的线性代数知识，且学习本课程理解基本原理需要这些知识足以，但对于个别公式推导需要的线性代数知识则超过本部分复习的基础知识，需要课下自行学习，比如矩阵的求导的知识。</font>
- 矩阵和向量的概念；
- 矩阵的加法和乘法运算；
- 矩阵乘法的性质;
- 逆矩阵和转置；
### 4 环境配置
#### 4.1 Octave安装及环境配置
- **下载地址**
    ><font size=2>**注意**：达叔说不要安装Octave4.0版本。</font>
  - [Microsoft Windows下载地址](http://wiki.octave.org/Octave_for_Microsoft_Windows)
  - [macOS下载地址](http://wiki.octave.org/Octave_for_macOS)
  - [其他环境适配版本下载地址](http://wiki.octave.org/Category:Installation)
- **注意事项**
    - **重要**：第一次使用前先运行post-install.bat文件；
    - 启动方式是octave.vbs，可以新建快捷键到其他地方，在快捷方式文件属性的目标文件后添加“--no-gui”打开后便是命令窗口视图；
#### 4.2 Matlab安装及环境配置
- **下载地址**
  - [Matlab2020b百度网盘下载地址](https://pan.baidu.com/share/init?surl=XegUi8JgN1fgG_cPqWSTPA)
  - 提取码：j826
  - 安装教程见[脚本之家](https://www.jb51.net/softs/745941.html) 
### 5 多变量线性回归
#### 5.1 多元梯度下降法
- **假设函数**
    $$h_\theta(x)=\theta^{T}x=\theta_0x_0+\theta_1x_1+\theta_2x_2+\cdot\cdot\cdot+\theta_nx_n$$
- **参数**
    $$\theta_0,\theta_1,\ldots,\theta_n$$
- **代价函数**
    $$J(\theta_0,\theta_1,\ldots,\theta_n)=\frac{1}{2m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})^{2}$$
    ><font size=2>**注意**：上式中的$x^{(i)}$和$y^{(i)}$表示的是第$i$个向量，其中每个$x^{(i)}$向量含有$n$+1个维度。</font>
- **梯度下降算法(n≥1)**
    $$\begin{array}{l}
        \text{Repeat}\ \{\\
        \qquad \theta_j:=\theta_j-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{j}^{(i)}\ \ \ (\text{for}\ j=0,1,2,\ldots,n)\\
        \}\\
        \ \\
        \theta_0:=\theta_0-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{0}^{(i)}\\
        \theta_1:=\theta_1-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{1}^{(i)}\\
        \theta_2:=\theta_2-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{2}^{(i)}\\
        \ldots
    \end{array}$$
    ><font size=2>**注意A**：$x_{j}^{(i)}$表示的是第$i$个向量中的第$j$维的值；</br> **注意B**：$\frac{\partial}{\partial \theta_j}J(\theta_0,\theta_1,\ldots,\theta_n)=\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{j}^{(i)}$。</font>
#### 5.2 梯度下降法实用技巧A——特征缩放
- **目的**
  - 使不同特征得取值处在相近的范围，使梯度下降法更快的收敛；
- **做法**
    ><font size=2>**注意A**：一般将特征值的取值约束到-1到+1的范围内;</br>**注意B**：实际上是约束到和该范围同数量级的其他范围也是可以的，比如0到3或者-2到+0.5都是可以的。</font>
    - 用特征值除以最大值；
    - 归一化处理，比如一般分布的正态归一化；
#### 5.3 梯度下降法B——学习率的选择
- **什么是学习率？**
  - 学习率为梯度下降算法中的$\alpha$；
  - 在梯度下降算法中，如果**学习率选择的太大**，则**代价函数$J(\theta)$可能不会每次都下降**；如果**学习率选择的太小**，则**代价函数$J(\theta)$可能收敛缓慢**，效率低下；
- **收敛的判断**
  - 通过观察代价函数对应不同的迭代次数的函数图像进行判断；
  - 通过自动检测函数，设定合适的阈值$\varepsilon$，代价函数的变化值小于该阈值则收敛，但该方法很难确定合适的阈值$\varepsilon$;
- **学习率的选择**
  - 一般按以下值从小到大一次尝试，尝试过程中按10倍上个学习率进行迭代；
  $$\ldots,0.001,0.01,0.1,1,\ldots$$
  - **达叔的选择**是按3倍上个迭代的学习率进行迭代；
  $$\ldots,0.001,0.003,0.01,0.03,0.1,0.3,1,\ldots$$
#### 5.4 正规方程法(区别于迭代方法的直接解法)
- **前置条件**
  - **$m$个样本**
  $$(x^{(1)},y^{(1)}),(x^{(2)},y^{(2)}),(x^{(3)},y^{(3)}),\ldots,(x^{(m)},y^{(m)})$$
  - **$n$个特征**
  ><font size=2>**说明**：每个$x^{(i)}$向量均含有$n$+1个维度，其中$x_{0}^{(i)}$为常数$1$，其余$n$个维度则表示$n$个特征的样本值。</font>

  $$x^{(i)}=
  \left[ \begin{array}{c}
      x_{0}^{(i)}\\
      x_{1}^{(i)}\\
      x_{2}^{(i)}\\
      \vdots\\
      x_{n}^{(i)}
  \end{array} \right]
  \in \mathbb{R}^{n+1}$$
- **构建矩阵$X$和向量$y$**
    ><font size=2>**注意**：矩阵$X$为$m\times(n+1)$的矩阵，$y$为$m$维向量。</font>

  $$X=
  \left[ \begin{array}{c}
      (x^{(1)})^{T}\\
      (x^{(2)})^{T}\\
      (x^{(3)})^{T}\\
      \vdots\\
      (x^{(m)})^{T}
  \end{array} \right]
  \quad \text{and} \quad  
  y=
  \left[ \begin{array}{c}
      y^{(1)}\\
      y^{(2)}\\
      y^{(3)}\\
      \vdots\\
      y^{(m)}
  \end{array} \right]$$
- **利用正规方程法计算$\theta$向量**
  - **参数$\theta$向量**
  $$\theta=
  \left[ \begin{array}{c}
      \theta_0\\
      \theta_1\\
      \theta_2\\
      \vdots\\
      \theta_n
  \end{array} \right]$$
  - **正规方程计算参数$\theta$向量**
  $$\theta=(X^{T}X)^{-1}X^{T}y$$
  - **Octave实现正规方程的计算语句**
    ```matlab
    pinv (X'*X)*X'*y
    ```
  - **正规方程直接计算参数$\theta$向量**
    - 待定……
- **梯度下降法和正规方程法的优缺点**
  - **梯度下降法**
    - **优点**
      - 在特征变量很多的情况下，也能运行的很好；
    - **缺点**
      - 需要选择并尝试不同的学习率$\alpha$，找到运行的最好的哪个;
      - 需要更多次迭代，且取决于具体细节，计算可能会更慢；
  - **正规方程法**
    - **优点**
      - 不需要选择学习效率$\alpha$;
      - 不需要迭代；
    - **缺点**
      - 求解参数$\theta$向量需要计算$(X^{T}X)^{-1}$，且对大多数计算应用来说，实现逆矩阵计算的代价，以矩阵维度的三次方增长，即时间复杂度为$O(n^{3})$，故如果特征变量很多时，计算会慢很多；
  - **计算方法的选择**
    - 以$10000$为分界线，当特征变量的维数$n$为$10000$左右的时候，正规方程计算参数$\theta$的优势不在明显；
    - 当特征变量的维数为$100$和$1000$这样低于$10000$的数量时，正规方程计算参数$\theta$更具优势；
    - 当特征变量的维数远大于$10000$，比如为$10^{6}$方时，梯度下降法更具优势；
#### 5.5 正规方程在矩阵不可逆情况下的解决方法
- **伪逆矩阵**
  - 逆矩阵的广义形式；
  - 由于奇异矩阵(不可逆的方阵矩阵)和非方阵的矩阵不存在逆矩阵，但是在Matlab或者Octave中可以使用pinv(A)求这两种矩阵的伪逆矩阵(且inv(A)伪求逆矩阵的函数)；
- **$X^{T}X$不可逆的可能原因及处理方法**
  - **原因A**
    - 由于某些原因，学习问题包含了多余的特征，比如某些特征线性相关；
      - **示例**：在预测房价的示例中，如果特征变量$x_1$使用平方英尺为单位，而特征变量$x_2$使用平方米为单位，这种情况下得出的$X^{T}X$通常是不可逆的；
    - **处理方法**：删除多组(如果有很多组的话)具有线性关系的两个特征中的一个，直到没有多余的特征为止；
  - **原因B**
    - 运行的学习算法有很多特征，具体来说例如样本数小于等于特征变量数，即$m\leq n$；
      - **示例**：比如让$m=10$，$n=100$时，要找到合适的参数向量$\theta$(该向量为$n+1$维)，即使用10个样本找到101个参数值，有时可能会成功，但不具有普遍性；
    - **处理方法**：删除一些特征；或者使用正则化的方法(这个方法后面会学到)；
### 6 Octave/Matlab 教程
#### 6.1 基本操作
>**说明**：Octave的语法和Matlab基本相同，此处以使用Octave操作为例。
- **基本常量赋值**
  ```matlab
  octave:1>   % 默认的Octave命令窗口显示内容
  octave:2> PS1 >>    % PS1指令切换Octave窗口提示符的显示内容为“>>”
  >>a = 1
  a = 1
  >>a = 3;    % 语句末尾加了分号“;”，命令窗口就不会答应输出结果
  >>a = pi
  a = 3.1416    % 默认输出格式
  >>disp(a)
  3.1416
  >>disp(sprintf('2 decimals: %0.2f', a))  % 传统C语言的格式化输出 
  2 decimals: 3.14
  >>format long   % 改变小数显示默认的位数
  >>a
  a = 3.14159265358979
  >>format short
  a = 3.1416
  ```
- **简单矩阵构建**
  ```matlab
  >>A = [1 2; 3 4; 5 6]   % 构建一个3×2矩阵
  A =

     1   2
     3   4
     5   6

  >>A = [1 2;   
  >3 4;
  >5 6]   % 构建一个矩阵的另一种写法
  A =

     1   2
     3   4
     5   6

  >>V = [1 2 3]   % 构建一个1×3的行向量
  V =

     1   2   3

  >>V = [1; 2; 3]   % 构建一个3×1的列向量
  V =

     1
     2
     3

  >>V = 1:0.2:2   % 按照0.2的步长构建一个范围为1到2的1×6的行向量
  V =

      1.0000    1.2000    1.4000    1.6000    1.8000    2.0000

  >>V = 1:6   % 构建一个1到6逐步递增的行向量
  V =

      1   2    3   4   5   6
  ```
- **特殊矩阵构建**
  ```matlab
  >>ones(2,3)   % 构建一个各项都为1的2×3矩阵
  ans =

      1   1   1
      1   1   1

  >>C = 2 * ones(2,3)   % 构建一个各项都为2的2×3矩阵
  C =

      2   2   2
      2   2   2

  >>W = rand(3,3)   % 构建一个各项值介于0到1之间的3×3随机数矩阵
  W =

     0.112010   0.388236   0.744595
     0.046368   0.174028   0.427191
     0.321745   0.147818   0.804832 

  >>W = randn(1,3)    % 构建一个各项值符合高斯随机分布(正态分布)1×3矩阵
  W =

    -0.9340  -0.8005  -0.1647
  ```
- **直方图绘制**
  ```matlab
  >>W = -6 + sqrt(10)*(randn(1,10000));   % 一个复杂的示例
  >>hist(W)   % 绘制直方图
  >>hist(W, 50)   % 绘制具有50竖条的直方图
  >>eye(4)    % 构建一个4阶单位矩阵
  ans =

  Diagonal Matrix

     1   0   0   0
     0   1   0   0
     0   0   1   0
     0   0   0   1
  ```
  ![hist(W)绘制的直方图(左) hist(W,50)绘制的直方图(右)](image/hist_w.png)
- **查看矩阵属性**
  ```matlab
  >>A = [1 2; 3 4; 5 6]
  A =

     1   2
     3   4
     5   6

  >>size(A)   % 返回矩阵A的行列数
  ans =

     3   2
  >>size(A,1)   % 返回矩阵的行数
  ans = 3
  >>size(A,2)   % 返回矩阵的列数
  ans = 2
  >>length(A)   % 返回矩阵的最大维数
  ans = 3
  >>B = [1 2 3 4 5]
  B =

     1   2   3   4   5

  >>length(B)
  ans = 5
  >> C = [1;2;3;4;5]
  C =

     1
     2
     3
     4
     5

  >>length(C)
  ans = 5
  >>help eye    % 查看eye的帮助信息
  >>help help   % 查看帮助的使用方法
  >>help rand   % 产看rand的帮助信息
  ```
#### 6.2 移动数据
- **工作目录切换及目录内容查看**
  ```matlab
  >>pwd    % 显示目前所处目录
  ans = C:\Compilers\Octave
  >> cd E:\Exc\MechineLearning\course_materials\Chapter06\ex1 % 切换当前工作目录
  >>pwd
  ans = E:\Exc\MechineLearning\course_materials\Chapter06\ex1
  >>ls
   驱动器 E 中的卷没有标签。
   卷的序列号是 CC0C-73EE

   E:\Exc\MechineLearning\course_materials\Chapter06\ex1 的目录

  [.]                      ex1data2.txt             normalEqn.m
  [..]                     ex1_multi.m              plotData.m
  computeCost.m            featureNormalize.m       submit.m
  computeCostMulti.m       gradientDescent.m        warmUpExercise.m
  ex1.m                    gradientDescentMulti.m
  ex1data1.txt             [lib]
                13 个文件         18,682 字节
                 3 个目录 195,141,681,152 可用字节
  ```
  - **加载数据**
  ```matlab
  >>load ex1data1.txt
  >>load('ex1data2.txt')
  ```
- **环境变量及其属性查看**
  ```matlab
  >>who    % 查看当前环境中有哪些变量 
  Variables visible from the current scope:

  A         B         C         ans       ex1data1  ex1data2
  >>whos  % 查看当前环境中的变量及其属性
  Variables visible from the current scope:

  variables in scope: top scope

     Attr Name          Size                     Bytes  Class
     ==== ====          ====                     =====  =====
          A             3x2                         48  double
          B             1x5                         40  double
          C             5x1                         40  double
          ans           1x53                        53  char
          ex1data1     97x2                       1552  double
          ex1data2     47x3                       1128  double

  Total is 404 elements using 2861 bytes

  >>size(ex1data1)
  ans =

     97    2

  >>size(ex1data2)
  ans =

     47    3

  >>clear ex1data2
  >>whos
  Variables visible from the current scope:

  variables in scope: top scope

     Attr Name          Size                     Bytes  Class
     ==== ====          ====                     =====  =====
          A             3x2                         48  double
          B             1x5                         40  double
          C             5x1                         40  double
          ans           1x2                         16  double
          ex1data1     97x2                       1552  double

  Total is 212 elements using 1696 bytes
  ```
- **批量赋值及数据存储**
  ```matlab
  >>v = ex1data1(1:10,1)   % 获取ex1data1第一列的前10个值并赋给v  
  v =

     6.1101
     5.5277
     8.5186
     7.0032
     5.8598
     8.3829
     7.4764
     8.5781
     6.4862
     5.0546

  >>save test.mat v;   % 将v中的值存入以二进制存储的test.mat文件                                  
  >>clear
  >>whos
  >>load test.mat
  >>v
  v =

     6.1101
     5.5277
     8.5186
     7.0032
     5.8598
     8.3829
     7.4764
     8.5781
     6.4862
     5.0546

  >>save test.txt v -ascii   % 保存为ASCII编码的TXT文档
  >>A = [1 2; 3 4; 5 6]
  A =

     1   2
     3   4
     5   6
  ```
- **数据访问**
  ```matlab
  >>A(3,2)   % 获取A中第3行第2列的元素
  ans = 6
  >>A(2,:)   % 获取A中第2行的所有元素
  ans =

     3   4

  >>A(:,2)   % 获取A中第2列的所有元素
  ans =

     2
     4
     6

  >>A([1 3],:)   % 获取A中第1行和第3行的元素
  ans =

     1   2
     5   6

  >>A(:,2) = [10;11;12]
  A =

      1   10
      3   11
      5   12

  >>A = [A, [100;101;102]];    % 在A的右边追加一列
  >>A
  A =

       1    10   100
       3    11   101
       5    12   102

  >>A(:)   % 一列显示A中所有元素
  ans =

       1
       3
       5
      10
      11
      12
     100
     101
     102

  >>A = [1 2; 3 4; 5 6];
  >>B = [11 12; 13 14; 15 16];
  >>C = [A B]
  C =

      1    2   11   12
      3    4   13   14
      5    6   15   16

  >>C = [A; B]
  C =

      1    2
      3    4
      5    6
     11   12
     13   14
     15   16

  >>[A,B]
  ans =

      1    2   11   12
      3    4   13   14
      5    6   15   16

  ```
#### 6.3 计算数据
- **矩阵运算**
  ```matlab
  >>A = [1 2; 3 4; 5 6];
  >>B = [11 12; 13 14; 15 16];
  >>A
  A =

     1   2
     3   4
     5   6

  >>B
  B =

     11   12
     13   14
     15   16

  >>A .* B    % A中的元素乘以B中的每一个元素
  ans =

     11   24
     39   56
     75   96

  >>A .^ 2    % 对A中的每个元素进行平方
  ans =

      1    4
      9   16
     25   36

  >>v = [1;2;3]
  v =

     1
     2
     3

  >> 1 ./ v   % 对v中的每个元素取倒数
  ans =

     1.0000
     0.5000
     0.3333

  >>1 ./ A
  ans =

     1.0000   0.5000
     0.3333   0.2500
     0.2000   0.1667
  ```
- **矩阵特殊运算**
  ```
  >>log(v)    % 对v中的每个元素取自然对数
  ans =

          0
     0.6931
     1.0986

  >>exp(v)    % 以e为底以v中的每个元素为指数的幂运算
  ans =

      2.7183
      7.3891
     20.0855

  >>abs([-1;2;-3])    % 对矩阵中的每个元素取绝对值
  ans =

     1
     2
     3

  >>-v    % 对矩阵中的每个元素取其相反数
  ans =

    -1
    -2
    -3

  >>v + ones(length(v),1)   % v与同型各元素都为1的矩阵相加
  ans =

     2
     3
     4

  >>v + 1   % v中的每个元素加1
  ans =

     2
     3
     4
  ```
- **矩阵的转置**
  ```matlab
  >>A'    % A矩阵的转置
  ans =

     1   3   5
     2   4   6

  >>(A')'   % A矩阵转置的转置
  ans =

     1   2
     3   4
     5   6
  ```
- **max()、sum()、find()、prod()函数的使用**
  ```matlab
  >>a = [1 15 2 0.5]
  a =

      1.0000   15.0000    2.0000    0.5000

  >>max(a)    % 获取矩阵a中的最大值
  ans = 15
  >>[val ind] = max(a)    % 求取矩阵a中的最大值及其索引
  val = 15
  ind = 2
  >>max(A)    % 获取矩阵A中每一列的最大值
  ans =

     5   6

  >>a < 3   % 判断a中的元素是否小于3，小于则赋值1，否则赋值0
  ans =

    1  0  1  1

  >>find(a < 3)   % 找出a中小于3的元素索引
  ans =

     1   3   4

  >>sum(a)    % 求和
  ans = 18.500
  >>prod(a)   % 求积
  ans = 15
  ```
- **magic()、floor()、ceil()函数的使用**
  ```matlab
  >> A = magic(3)   % 构造一个每行每列各个及对角线元素之和为同一个数的矩阵
  A =

     8   1   6
     3   5   7
     4   9   2

  >>[r, c] = find(A >= 7)   % 找出矩阵A中大于等7元素的行列索引
  r =

     1
     3
     2

  c =

     1
     2
     3

  >>floor(a)    % 向下取整
  ans =

      1   15    2    0

  >>ceil(a)   % 向上取整
  ans =

      1   15    2    1
  ```
- **max()函数与rand()函数的混合使用**
  ```matlab
  >>rand(3)   % 生成3×3随机数矩阵
  ans =

     0.050874   0.363564   0.948816
     0.547956   0.716681   0.695986
     0.629558   0.993116   0.905270

  >>max(rand(3),rand(3))    % 取两个3×3随机数矩阵中对应位置的最大元素组成新 的随机数矩阵
  ans =

     0.7610   0.4552   0.4932
     0.8411   0.5731   0.8508
     0.7669   0.8573   0.2908
  ```
- **max()函数用法拓展**
  ```matlab
  >>A
  A =

     8   1   6
     3   5   7
     4   9   2

  >>max(A,[],1)   % 获取矩阵A各列元素的最大值
  ans =

     8   9   7

  >>max(A,[],2)   % 获取矩阵A各行元素的最大值
  ans =

     8
     7
     9

  >>max(A)    % 默认求矩阵A各列元素的最大值
  ans =

     8   9   7
  ```
- **矩阵垂直反转函数flipud()函数及求逆矩阵**
  ```matlab
  >>A = magic(9)    % 生成9阶幻方
  A =

     47   58   69   80    1   12   23   34   45
     57   68   79    9   11   22   33   44   46
     67   78    8   10   21   32   43   54   56
     77    7   18   20   31   42   53   55   66
      6   17   19   30   41   52   63   65   76
     16   27   29   40   51   62   64   75    5
     26   28   39   50   61   72   74    4   15
     36   38   49   60   71   73    3   14   25
     37   48   59   70   81    2   13   24   35

  >>eye(9)     % 生成9阶单位矩阵
  ans =

  Diagonal Matrix

     1   0   0   0   0   0   0   0   0
     0   1   0   0   0   0   0   0   0
     0   0   1   0   0   0   0   0   0
     0   0   0   1   0   0   0   0   0
     0   0   0   0   1   0   0   0   0
     0   0   0   0   0   1   0   0   0
     0   0   0   0   0   0   1   0   0
     0   0   0   0   0   0   0   1   0
     0   0   0   0   0   0   0   0   1

  >>flipud(eye(9))    % 将9阶单位矩阵垂直旋转
  ans =

  Permutation Matrix

     0   0   0   0   0   0   0   0   1
     0   0   0   0   0   0   0   1   0
     0   0   0   0   0   0   1   0   0
     0   0   0   0   0   1   0   0   0
     0   0   0   0   1   0   0   0   0
     0   0   0   1   0   0   0   0   0
     0   0   1   0   0   0   0   0   0
     0   1   0   0   0   0   0   0   0
     1   0   0   0   0   0   0   0   0

  >>sum(sum(A .* eye(9)))   * 求矩阵A对角线元素的和
  ans = 369
  >>sum(sum(A .* flipud(eye(9)))) * 求矩阵A斜对角线元素的和
  ans = 369
  >>A = magic(3)
  A =

     8   1   6
     3   5   7
     4   9   2

  >>temp = pinv(A)    % 求矩阵A的逆矩阵
  temp =

     0.147222  -0.144444   0.063889
    -0.061111   0.022222   0.105556
    -0.019444   0.188889  -0.102778

  >>A * temp
  ans =

     1.0000e+00  -1.2212e-14   6.3283e-15
     5.5511e-17   1.0000e+00  -2.2204e-16
    -5.9952e-15   1.2268e-14   1.0000e+00
  ```
#### 6.4 数据绘制
- **单一窗口覆盖绘制图像**
  ```matlab
  >>t = [0:0.01:0.98];    % 构造一个从0到0.98，步长为0.01的数列
  >>y1 = sin(2*pi*4*t);   % 设置y1为正弦函数
  >>plot(t,y1)    % 绘制y1的函数图像
  >>y2 = cos(2*pi*4*t);   % 设置y2为余弦函数
  >>plot(t,y2)    % 绘制y2的函数图像
  ```
- **同一个图像窗口绘制图像**
  ```matlab
  >>plot(t,y1);
  >>hold on;    % 让新图像在旧图像上绘制
  >>plot(t,y2,'r');   % 绘制余弦函数且指定绘制颜色为红色
  ```
- **设置图像坐标轴标签和标题**
  ```matblb
  >>xlabel('time')    % 设置x坐标轴名称
  >>ylabel('value')   % 设置y坐标轴名称
  >>legend('sin','cos')   % 添加图像图例
  >>title('my plot')    % 添加图像标题
  ```
  ![同一个窗口绘制图像](image\myPlot.png)
- **图像保存及多窗口绘制图像**
  ```matlab
  >>cd E:\Exc\MechineLearning\course_materials\Chapter06\ex1;
  >>print -dpng 'myPlot.png'    % 保存图像为png图片
  >>close   % 关闭图像窗口
  >>figure(1);plot(t,y1);   % 新建一个窗口绘制正弦函数
  >>figure(2);plot(t,y2);   % 新建一个窗口绘制余弦函数
  ```
- **单一窗口分区绘制图像**
  ```matlab
  >>subplot(1,2,1);   % 将图像区域分成1×2的图像区域，并使用区域1绘制
  >>plot(t,y1);
  >>subplot(1,2,2);   % 将图像区域分成1×2的图像区域，并使用区域2绘制
  >>plot(t,y2);
  >>axis([0.5 1 -1 1])    % 设置区域2中图像x轴和y轴的范围
  >>print -dpng 'myPlot2.png'
  >>clf;    % 清除图像绘制区域
  ```
  ![同一个窗口绘制图像](image\myPlot2.png)
- **可视化矩阵及颜色渲染**
  ```matlab
  >>A = magic(5)
  A =

     17   24    1    8   15
     23    5    7   14   16
      4    6   13   20   22
     10   12   19   21    3
     11   18   25    2    9

  >>imagesc(A)    % 可视化矩阵A
  >>imagesc(A), colorbar, colormap gray;    % 改变可视化颜色并添加颜色条带
  >>imagesc(magic(15)), colorbar, colormap gray;
  >>print -dpng 'myMagic.png'
  >>a = 1, b = 2, c =3    % 使用逗号来实现连续调用函数
  a = 1
  b = 2
  c = 3
  ```
  ![矩阵可视化](image\myMagic15.png)
#### 6.5 控制语句：for、while、if语句
- **for循环语句**
  ```matlab
  >>v = zeros(10,1)
  v =

     0
     0
     0
     0
     0
     0
     0
     0
     0
     0

  >>for i = 1:10,
  >   v(i)=2^i;
  > end;
  >>v
  v =

        2
        4
        8
       16
       32
       64
      128
      256
      512
     1024

  >>for i = 1:10,
  >   disp(i);
  > end;
  1
  2
  3
  4
  5
  6
  7
  8
  9
  10
  ```
- **while循环语句**
  ```matlab
  >>v
  v =
  
      100
      100
      100
      100
      100
       64
      128
      256
      512
     1024
  
  >>i = 1;
  >>while true,
  >   v(i) = 999;
  >   i = i +1;
  >   if i == 6,
  >       break;
  >    end;
  > end;
  >>v
  v =
  
      999
      999
      999
      999
      999
       64
      128
      256
      512
     1024
  ```
- **if条件语句**
  ```matlab
  >>v(1)
  ans = 999
  >>v(1)=2;
  >>if v(1)==1,
  >    disp('The value is one.');
  > elseif v(1)==2,
  >    disp('The value is two.');
  > else
  >    disp('The value is not one or two.');
  > end;
  The value is two.
  ```
- **函数**
  - 函数A
    - 函数定义：squareThisNumber.m
      ```matlab
      function y = squareThisNumber(x)

      y = x^2;
      ```
    - 函数调用
      ```matlab
      >>cd E:\Exc\MechineLearning\course_materials\Chapter06\ex1
      >>pwd
      ans = E:\Exc\MechineLearning\course_materials\Chapter06\ex1
      >>squareThisNumber(5)
      ans = 25
      >>addpath('E:\Exc\MechineLearning\course_materials\Chapter06\ex1')
      >>cd C:\
      >>pwd
      ans = C:\
      >>squareThisNumber(5)
      ans = 25
      ```
  - 函数B
    - 函数定义：squareAndCubeThisNumber.m
      ```matlab
      function [y1,y2] = squareAndCubeThisNumber(x)

      y1 = x^2;
      y2 = x^3;
      ```
    - 函数调用
      ```matlab
      >>[a, b] = squareAndCubeNumber(5)
      error: 'squareAndCubeNumber' undefined near line 1, column 1
      >>[a, b] = squareAndCubeThisNumber(5);
      >>a
      a = 25
      >>b
      b = 125
  - 函数C
    - 函数定义：costFunctionJ.m
      ```matlab
      function J = costFunctionJ(X, y, theta)

      % X is the "design matrix" containing out training examples.
      % y is the class labels.

      m = size(X,1);              % number of training examples
      predictions = X * theta;    % predictions of hypothesis on all m examples
      sqrErrors = (predictions-y) .^ 2;   % squared errors

      J = 1 / (2 * m) * sum(sqrErrors);
      ```
    - 函数调用
      ```matlab
      >>X = [1 1; 1 2; 1 3]
      X =
    
         1   1
         1   2
         1   3
    
      >>y = [1; 2; 3]
      y =
    
         1
         2
         3
    
      >>theta=[0;1];
      >>j = costFunctionJ(X,y,theta)
      j = 0
      >>theta = [0;0];
      >>j = costFunctionJ(X,y,theta)
      j = 2.3333
      ```
#### 6.6 矢量
- **梯度下降的同步更新实现**
$$\begin{array}{c}
  \theta_0:=\theta_0-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{0}^{(i)}\\
  \theta_1:=\theta_1-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{1}^{(i)}\\
  \theta_2:=\theta_2-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{2}^{(i)}\\
  \ldots\\
  \theta_n:=\theta_n-\alpha\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{n}^{(i)}
\end{array}$$
- **矢量化参数说明**
$$\theta=
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
\delta_j=\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})x_{j}^{(i)},\ (j=0,1,\ldots,n)$$
- **矢量化的实现**
$$\theta:=\theta-\alpha\delta\ \Rightarrow\ 
\left[ \begin{array}{c}
  \theta_0\\
  \theta_1\\
  \theta_2\\
  \vdots\\
  \theta_n
\end{array} \right]:=
\left[ \begin{array}{c}
  \theta_0\\
  \theta_1\\
  \theta_2\\
  \vdots\\
  \theta_n
\end{array} \right]-\alpha
\left[ \begin{array}{c}
  \delta_0\\
  \delta_1\\
  \delta_2\\
  \vdots\\
  \delta_n
\end{array} \right]$$
### 7 Logistic 回归
#### 7.1 分类
- Logistic 回归处理的是预测的变量是离散的情况下的分类；
- Logistic 回归的预测值介于0到1之间；
#### 7.2 假设陈述
- **Logistic 回规模型**
$$\left. \begin{array}{r}
  h_{\theta}(x)=\theta^{T}x\\
  g(z)=\frac{1}{1+e^{-z}}
\end{array}  
\right\} \xRightarrow{z=\theta^{T}x}
h_{\theta}(x)=\frac{1}{1+e^{-\theta^{T}x}}$$
- **对预测值即假设输出的说明**
  - 首先假设样本值中$y$只有0和1两个取值；
  - $h_{\theta}(x)$表示对于输入的$x$，$y=1$的概率；
  - 示例：
    - 示例内容
    $$If\ x=\left[
    \begin{array}{c}
      x_0 \\ x_1 
    \end{array} \right]=\left[
    \begin{array}{c}
      1 \\ \text{tumorSize}
    \end{array} \right],\ h_{\theta}(x)=0.7$$
    - 示例说明：示例中的$h_{\theta}(x)$等于0.7表示该患者的肿瘤是一个恶性肿瘤的概率为70%；
    - 针对此类示例，有一下拓展：
    $$\begin{array}{l}
        h_{\theta}(x)=P(y=1|x;\theta) \\
        y=0\ or\ y=0 \Rightarrow \left\{
        \begin{array}{l}
          P(y=0|x;\theta)+P(y=1|x;\theta)=1\\
          P(y=0|x;\theta)=1-P(y=1|x;\theta)
        \end{array} \right.
    \end{array}
    $$
#### 7.3 决策界限
- 决策边界是根据训练集拟合$\theta$进而得出假设函数所确定的训练集分类边界；
- 决策边界是假设函数的一个属性，不是数据集的属性；
- 一旦假设函数有确定参数，就可完全确定决策边界，不一定需要通过绘制训练集来确定决策边界；
#### 7.4 代价函数
- **训练集**
$$\{(x^{(1)},y^{(1)}),(x^{(2)},y^{(2)}),\ldots,(x^{(m)},y^{(m)})\}$$
- **$m$个样本**
$$x \in \left[
  \begin{array}{c}
    x_0 \\ x_1 \\ x_2 \\ \vdots \\ x_n
  \end{array} \right]
  \in \mathbb{R}^{n+1};\ 
  x_0=1,\ y \in \{ 0,1 \}$$
- **假设函数**
$$h_\theta(x)=\frac{1}{1+e^{-\theta^{T}x}}$$
- **Logistic 回归代价函数**
  >**<font size=2>说明</font>**：<font size=2>在Octave中，计算自然对数为log()函数。</font>

$$\begin{array}{l}
  J(\theta)=\frac{1}{m}\sum\limits_{i=1}^{m}Cost(h_\theta(x^{(i)}),y^{(i)})\\
  Cost(h_\theta(x),y)=\left\{ 
    \begin{array}{r}
      -\ln(h_\theta(x)) & if\ y=1\\
      -\ln(1-h_\theta(x)) & if\ y=0
    \end{array}\right.\\
    \text{Note:\ y=0\ or\ 1\ always.} 
\end{array}$$
- **简化代价函数和梯度下降**
  - 简化代价函数：该代价函数的采用极大似然估计得到；
  $$Cost(h_\theta(x),y)=-y\ln(h_\theta(x))-(1-y)\ln(1-h_\theta(x))$$
  - 梯度下降
  $$\begin{array}{l}
    \textsf{Gradient Descent:}\\
    \qquad J(\theta)=-\frac{1}{m}\sum\limits_{i=1}^{m}[y^{(i)}\ln(h_\theta(x^{(i)}))+(1-y^{(i)})\ln(1-h_\theta(x^{(i)}))]\\ \\
    \textsf{Want}\ \text{min}_\theta\ J(\theta):\\
    \quad\text{Repeat}\ \{ \\
    \qquad \quad \theta_j:=\theta_j-\alpha\frac{\partial}{\partial{\theta_j}}J(\theta)\quad (\text{simultaneously update all}\  \theta_j) \\ 
    \quad \}\\ \\
    \textsf{Besides:}\\
    \qquad \frac{\partial}{\partial{\theta_j}}J(\theta)=\frac{1}{m}\sum\limits_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_{j}^{(i)}
  \end{array}$$
#### 7.5 高级优化
- **给定$\theta$，需要编程计算以下两项**
  - $J(\theta)$
  - $\frac{\partial}{\partial{\theta_j}}J(\theta)\quad (\text{for}\ j=0,1,\ldots,n)$
- **优化算法**
  - Gradient descent (梯度下降)
  - Conjugate gradient (共轭梯度)
  - BFGS
  - L-BFGS
- **Conjugate gradient、BFGS、L-BFGS算法的优缺点**
  - 优点
    - 不需要计算学习率$\alpha$;
    - 通常比梯度下降快；
  - 缺点
    - 相比梯度下降更复杂；
- **示例代码**
  - 示例
    $$\begin{array}{l}
      \theta=\left[ \begin{array}{c}
        \theta_1 \\ \theta_2
      \end{array} \right] \\
      J(\theta)=(\theta_1-5)^{2}+(\theta_2)^{2} \\
      \frac{\partial}{\partial{\theta_1}}J(\theta)=2(\theta_1-5)\\
      \frac{\partial}{\partial{\theta_2}}J(\theta)=2(\theta_2-5)
    \end{array}$$
  - 代码表示
    ```matlab
    % costFunction.m
    function [jVal, gradient] = costFunction(theta)

    jVal = (theta(1)-5)^2 + (theta(2)-5)^2;

    gradient = zeros(2,1);
    gradient(1) = 2 * (theta(1)-5);
    gradient(2) = 2 * (theta(2)-5);
    ```
    ```matlab
    % Octave窗口操作
    % 设定操作参数和迭代次数
    >>options = optimest('GradObj', 'on', 'MaxIter', '100');
    >>initialTheta = zeros(2,1);
    >>% 此处@表示指向函数costFunction
    >>[optTheta, functionVal, exitFlag] = fminunc(@costFunction, initialTheta, options);  % 此句命令运行后会产生如下格式内容

    <ag] = fminunc(@costFunction, initialTheta, options)
    optTheta = 

       5.0000
       5.0000

    functionVal = 1.5777e-030   % 很小，可以认为是0
    exitFlag = 1  % 表示收敛
    ```
#### 7.6 多元分类：一对多
- **具体做法**
  - 可以将多元分类转换为多个独立的二元分类进行；
  - 最后类别归属为多个独立二元分类中预测值最大的一个；
![多元分类的一对多情况](image\logistic_one-vs-all.png)
- **实现步骤**
  - 为每个类别$i$训练一个Logistic回归分类器$h_{\theta}^{(i)}(x)$，以预测$y=i$时的概率；
  - 对于每一个新输入的$x$做预测，选定最大预测值$\underset{i}{\text{max}}\ h_\theta^{(i)}(x)$所属的类别$i$为$x$的归属;