# 实用工具类
---
>说明：本文档内容既有原创，也有借鉴，对于来自各位博主的内容，均在文中放置传送。
## 1 控制台命令的使用
### 1.1 打开控制台、查看命令帮助及路径切换
#### 1.1.1 打开控制台
  - `win+r`输入`cmd`确认即可打开；
- 命令帮助查看；
  - 查看控制台支持的命令：控制台输入`help`；
  - 查看特定命令的用法：`help [命令名称]`或者`[命令名称] /?`；  
  - **<font color=red>注意</font>**：此处的方括号[]在实际使用时不需要打出，此处只是作为一个标记符号使用，下同；
#### 1.1.2 路径切换
  - 初次打开命令提示符窗口会显示为以下样式；
    ```shell
    Microsoft Windows [版本 xx.x.xxxxx.xxx]
    (c) 2020 Microsoft Corporation. 保留所有权利。

    C:\Users\xxx>
    ```
  - `dir /b`查看当前目录下的文件；
    - `dir`命令作用是列出当前路径下的文件；
    - `/b`属性是只列出各个文件的名称，而不包含各个文件的详细信息；
  - `cd [文件夹路径]`可以定位到指定文件夹；
    - `cd`命令作用显示当前目录名或者改变当前目录；
    - `[文件夹路径]`是要改变并定位到的目标目录；
    - `cd ..`是返回当前目录的上层目录；
    - **<font color=red>注意</font>**：在首次启动的命令提示符窗口改变目录定位，执行后目录并未切换，还需要再次定位一次到目标目录所在的磁盘，具体使用如下；
      - 初次启动改变目录定位会发生的情况；
        ```shell
        Microsoft Windows [版本 xx.x.xxxxx.xxx]
        (c) 2020 Microsoft Corporation. 保留所有权利。

        C:\Users\xxx>cd d:\test

        C:\Users\xxx>
        ```
      - 初次启动改变目录定位的一般做法；
        ```shell
        Microsoft Windows [版本 xx.x.xxxxx.xxx]
        (c) 2020 Microsoft Corporation. 保留所有权利。

        C:\Users\xxx>d:

        D:\>cd d:\test

        D:\test>cd ..

        D:\>
        ```
### 1.2 ren/rename实现批量修改文件名
#### 1.2.1 命令介绍
- 在cmd命令提示符窗口操作命令时，`ren`和`rename`功能相同，都是修改文件名的命令，命令用法如下；
  - ren/rename命令帮助内容；
    ```shell
    ren [驱动器:][路径][原始文件名] [目标文件名]
    rename [驱动器:][路径][原始文件名] [目标文件名]
    ```
  - ren/rename使用示例；
    ```shell
    ren d:\test\a.jpg 01.jpg
    rename d:\test\a.jpg 01.jpg
    ```
  - **<font color=red>注意</font>**：由于我们使用该命令一般是定位到目标文件目录才进行使用，所以我们可以按以下格式记忆该命令的用法；
    ```shell
    ren [原始文件名] [目标文件名]
    rename [原始文件名] [目标文件名]
    ```
  - 实际使用示例；
    ```shell
    Microsoft Windows [版本 xx.x.xxxxx.xxx]
    (c) 2020 Microsoft Corporation. 保留所有权利

    C:\Users\xxx>d:

    D:\>cd d:\test

    D:\test>ren a.jpg 01.jpg

    D:\test>
    ```
#### 1.2.2 实现文件批量重命名
- **<font color=green>说明</font>**：实现文件批处理我们主要采用bat文件进行实现；且针对文件重命名的批处理操作，实现方式一般有两种，一种是采用命令脚本，一种是使用excel合成多条重命名命令放到bat文件中进行处理或者直接复制到定位后的控制台命令窗口执行；
- bat文件的新建；
  - `win+r`输入notepad打开记事本软件，然后选择文件另存，编码方式选择ANSI编码，后缀改为`.bat`存到要进行批量重命名的目标目录下；
  - 修改ANSI编码的目的：有时候我们批量重命名需要包含中文字符，或者显示一些提示信息，如果是UTF-8或者其他编码，则脚本执行过程中的回显和重命名可能出现乱码，但是如果改成ANSI编码则会正常显示；
  - bat文件的编辑：右键该文件，打开方式选择记事本打开，即可编辑其内容；
- **方式一**：bat命令脚本实现文件批量重命名；
  - **脚本A**：如果当前文件夹含有txt文本文件、图片文件、PPT等文件格式，且只想对图片文件重命名，则可以采用以下脚本，将以下脚本复制到bat文件保存，双击运行即可；
    ```shell
    @echo off
    setlocal EnableDelayedExpansion

    rem Rename picture
    set a=1
    for %%i in (*.bmp,*.gif,*.jpeg,*.jpg,*.png) do (
    	set /a b=10000000+a
    	set file=!b:~-5!
    	echo !file!
    	ren "%%i" "!file!.*"
    	set /a a+=1
    )

    pause
    ```
    - 本脚本的目的是将当前目录下的的各类格式图片按照bmp、gif、jpeg、jpg、png的检索顺序重命名为诸如00001.bmp、00002.gif、00003.jpeg、00004.jpg、00005.png格式的文件，因此按本脚本重命名的文件，未必按原始文件排列顺序排列，若要保证排列顺序请将图片都存入一个独立文件夹并使用`脚本B`重命名文件，其他格文档操作类似；
    - 脚本内容说明；
      - @echo off主要是为了关闭回显，如果不关闭，在命令运行过程中会显示诸如以下格式的输出内容；
        ```shell
        D:\test>xxx
        D:\test>xxx
        ```
      - setlocal EnableDelayedExpansion主要目的是设置本地为延迟扩展，这个不太好解释，建议移步脚本之家[了解详情](https://www.jb51.net/article/29323.htm)；
      - rem是脚本的注释，其使用方式如下；
        ```shell
        rem [注释内容]
        ```
      - `set`命令可以用来设置变量，`/a`命令行开关指定等号右边的字符串为被评估的数字表达式，更多有关set命令的用法可以使用`set /?`查看；
      - echo用于显示脚本执行中的过程信息；
      - 由于直接重命名为00001这样的名称如果是数字不好操作，所以采用了字符串截取的方式实现，即将10000000加上索引值，之后按字符串方式截取后5位，即脚本中的`set /a b=10000000+a`语句和`set file=!b:~-5!`语句；
      - `for`命令的用法比较多，建议移步这篇博文学习[批处理命令For循环命令详解](https://www.cnblogs.com/yang-hao/p/6003923.html)；
      - `pause`命令是为了让批处理窗口执行完毕后不关闭，以便查看过程信息；
  - **脚本B**：重命名当前目录下除bat批处理文件以外的其他文件，该脚本可以保持重命名前后文件的原始排列顺序；
    ```shell
    @echo off
    setlocal EnableDelayedExpansion

    rem Rename all file
    set a=1
    for %%i in (*.*) do (
      set fileName=%%i
      set fileSuffix=!fileName:~-3!
      if !fileSuffix! neq bat (
      	set /a b=10000000+a
      	set file=!b:~-5!
      	echo !file!
      	ren "%%i" "!file!.*"
      	set /a a+=1
      )
    )

    pause
    ```
- **方式二**：
    - 首先定位到目标文件夹，然后使用`dir`命令获取当前文件夹下的文件名称；
      - 以D盘test文件夹下的各项内容为例；
        - test文件夹内容；
          ```shell
          a.bmp
          b.gif
          c.jpeg
          d.jpg
          e.png
          filea.txt
          fileb.txt
          filec.txt
          ```
        - 获取当前文件夹下所有文件名称；
          ```shell
          Microsoft Windows [版本 xx.x.xxxxx.xxx]
          (c) 2020 Microsoft Corporation. 保留所有权利

          C:\Users\xxx>d:

          D:\>cd d:\test

          D:\test>dir /b *.* > filename.txt

          D:\test>
          ```
        - filename.txt中文件内容；
          ```shell
          a.bmp
          b.gif
          c.jpeg
          d.jpg
          e.png
          filea.txt
          fileb.txt
          filec.txt
          filename.txt
          test.bat
          ```
          >**<font color=red size=2>注意</font>**<font size=2>:由于命令是提取当前目录下所有文件的名称，所以批处理文件和文件名txt也被读取到文件中，所以在后续处理时要删掉这两个多余的文件名。</font>
        - 将文件名txt中的文件复制到excel中，按`.`分列，分列工具位置：数据->数据工具->分列；
        - 对于分列后的文件名进行批处理合成，之后使用字符串合并函数`CONCATENATE`将ren和文件名以及后缀合并成多条单列命令；
          ```c
          // 原始列
          a.bmp
          b.gif
          c.jpeg
          d.jpg
          e.png
          filea.txt
          fileb.txt
          filec.txt

          // 分列后
          a     | bmp
          b     | gif
          c     | jpeg
          d     | jpg
          e     | png
          filea | txt
          fileb | txt
          filec | txt

          // 处理后的表格内容
          ren |a     |bmp
          ren |b     |gif
          ren |c     |jpeg
          ren |d     |jpg
          ren |e     |png
          ren |filea |txt
          ren |fileb |txt
          ren |filec |txt

          // 字符串拼接后，注意别忘了命令剑的空格
          ren |a     |a_01    |bmp  |ren a.bmp a_01.bmp 
          ren |b     |b_02    |gif  |ren b.gif b_02.gif
          ren |c     |c_03    |jpeg |ren c.jpeg c_03.jpeg
          ren |d     |d_04    |jpg  |ren d.jpg d_04.jpg
          ren |e     |e_05    |png  |ren e.png e_05.jpg
          ren |filea |filea_1 |txt  |ren filea.txt filea_1.txt
          ren |fileb |fileb_2 |txt  |ren fileb.txt fileb_2.txt
          ren |filec |filec_3 |txt  |ren filec.txt filec_3.txt

          // 则拼接后得第五列内容即为待执行命令，将这一列复制到脚本或者当前目录
          // 的命令提示符窗口即可实现文件批量重命名。
          ```
- 和重命名有关的通配符和占位符说明；
  - 通配符是`*`，占位符是`？`；
  - `*`是指各类名称的全匹配，而`？`则是占位符，具体使用如下；
    ```c
    // 命令A：将当前目录下的txt文件批量重命名，重命名规则是保留原文件名的前5位字符，若文件名称不够5位，则不重命名
    ren *.txt ?????.txt // 命令A

    // 假设执行命令A前如下
    file.txt
    filea_xyz.txt
    fileb_ddd.txt
    filec_rst.txt

    // 执行命令A后如下
    file.txt
    filea.txt
    fileb.txt
    filec.txt

    // ren命令也可这样使用
    ren file_*.txt ??????.txt // 命令B

    // 假设执行命令B前如下
    file_a1.txt
    file_b2.txt
    file_c3.txt

    // 执行命令B后如下
    file_a.TXT
    file_b.txt
    file_c.txt
    ```
## 2 百度网盘
### 2.1 百度网盘视频在线倍速播放
><font size=2>**注**：本内容来自CSDN博主，[点击](https://blog.csdn.net/weijifen000/article/details/79889247)阅读原文。</font>
- 浏览器F12进入开发者模式选择`Console`输入以下代码即可实现加速；
  - 百度网盘视频在线1.5倍速播放核心代码;
    ```JS
    videojs.getPlayers("video-player").html5player.tech_.setPlaybackRate(1.5)
    ```
  - 百度网盘视频在线任意倍率播放设置；
    ```JS
    videojs.getPlayers("video-player").html5player.tech_.setPlaybackRate(任意倍率)
    ```
## 3 Python小工具
### 3.1 批量重命名文件
```Python
import os

# 指示要批量重命名的地址
filePath = "E:\\test"
# 定义计数器并设定初值1
count = 1
# os.listdir(filePath)获取目标录下文件集合
for file in os.listdir(filePath):
    fileName = os.path.splitext(file)[0]  # 获取文件名称
    fileType = os.path.splitext(file)[1]  # 获取文件后缀名称
    if fileType != ".ini":  # 有时候图片文件夹下会有一个ini文件，得把这个排除掉
        # 合成形如00001.bmp这样的名称
        changeFile = "{0:0>5}".format(count) + fileType
        # 重命名文件
        os.rename(os.path.join(filePath, file), os.path.join(filePath, changeFile))
        # 边重命名边计数输出指示
        print("{0:>5}  ".format(count), end="")
        print(changeFile)
        # 计数器加一
        count += 1

```