## 文本编辑器安装与配置
---
### 1 VSCode安装与配置
### 2 Sublime Text安装与配置
#### 2.1 安装与配置
- 安装版与绿色版；
  - 直接安装配鼠标右键菜单，且会写入注册表数据；
  - 解压即用，需要自己配置右键快捷菜单；
- 配置；
  - 破解与激活；
    ```shell
    # 修改hosts文件，添加以下内容屏蔽激活验证
    127.0.0.1 sublimetext.com
    127.0.0.1 sublimehq.com
    127.0.0.1 license.sublimehq.com
    127.0.0.1 45.55.255.55
    127.0.0.1 45.55.41.223
    0.0.0.0 license.sublimehq.com
    0.0.0.0 45.55.255.55
    0.0.0.0 45.55.41.223

    # 输入激活许可（注：此处许可适用Sublime Text3）
    ----- BEGIN LICENSE -----
    Member J2TeaM
    Single User License
    EA7E-1011316
    D7DA350E 1B8B0760 972F8B60 F3E64036
    B9B4E234 F356F38F 0AD1E3B7 0E9C5FAD
    FA0A2ABE 25F65BD8 D51458E5 3923CE80
    87428428 79079A01 AA69F319 A1AF29A4
    A684C2DC 0B1583D4 19CBD290 217618CD
    5653E0A0 BACE3948 BB2EE45E 422D2C87
    DD9AF44B 99C49590 D2DBDEE1 75860FD2
    8C8BB2AD B2ECE5A4 EFC08AF2 25A9B864
    ------ END LICENSE ------​

    # 做完以上工作，如果防止其自动更新，可以关闭自动检查
    # preferences->Setting-User
    # 添加以下内容
    "update_check": false,
    ```
  - 安装Package Control;
    ```shell
    # 国内未知原因在线安装Packacge Control会失败，所以采取离线安装方式
    # Package Contro离线包下载地址
    https://github.com/wbond/package_control

    # 进入github的package_control项目后，直接下载整个项目的zip
    # 下载的项目解压直接重命名放在Sublime Text3的根目录中Data/Packages目录下即可

    # 上述操作过后Package Control依旧无法使用
    # 原因是获取包安装清单文件channel_v3.json失败

    # channel_v3.json文件源地址
    # 这个地址时快时慢的，网好的时候可以下载最新的
    https://packagecontrol.io/channel_v3.json

    # github
    ```
### 3 Notepad++安装与配置
#### 3.1 安装与配置
- 安装版和绿色版；
  - 如果嫌配置麻烦，可以使用安装版本傻瓜式安装，一键配置；
  - 如果喜欢绿色版，选择改版，这个版本的安装包，解压即用，但是不会往注册表写入内容，所以右键也没有快捷方式；
- 针对绿色版的右键打开方式配置；
  - `Win+R`输入regedit打开注册表；
  - 定位到`HKEY_CLASSES_ROOT->*->shell`路径下；
  - 新建`Notepad++`项，并修改`(默认)`字符串值为`Nodepad++ 打开`；
  - 在`Notepad++`项下新建字符串值，重命名为`Icon`，并修改其中的值为`C:\TextEditors\Notepad++\notepad++.exe`；
  - 在`Nodepad++`项下新建`command`项，并修改`(默认)`字符串值为`"C:\TextEditors\Notepad++\notepad++.exe" "%1"`；
  - 自次，右键快捷菜单便会出现相关的快捷方式；
- 针对绿色版Nodepad++配置右键快捷菜单示例图如下；
![NPP_01|Notepad++项下的配置](./image/TextEditors_NPP_01.png)
![NPP_02|command项下的配置](./image/TextEditors_NPP_02.png)
#### 3.2 题外话
- Nodepad++为免费版文本编辑器，但是界面古老，且作者是个反华分子；
- 虽然该软件的作者有点难以让人接受，但是该软件还是有不少可去之处，比如批量删除空行还是挺方便的；
- 虽然功能强大，但是大部分时候用着还是不如VSCode和Sublime Text舒服，所以当作备用吧；