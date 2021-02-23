## 文本编辑器安装与配置
---
>注意：以下内容中涉及到的所有相关文件路径以读者自己实际的安装路径为准，此处仅为示例。
### 1 VSCode安装与配置
#### 1.1 说明
- VSCode是微软提供的一个免费开源现代化轻量级跨平台编辑；
- 由于依托微软，所以具有强大优势；
- 虽然他很强大，但是随着一次又一次更新，插件的增多，也有了启动慢等特点；
- 虽然目前它还有不少缺点，但是就笔者当前的使用来看，用的是最舒服的；
#### 1.2 安装与配置
- 下载安装；
  - 下载地址[https://code.visualstudio.com/](https://code.visualstudio.com/);
  - VSCode在Windows上只有安装版，不过毕竟是微软自家的产品，倒也能理解；
- 配置；
  - 插件安装：`Ctrl+Shift+X`然后输入想要的插件名称检索进行安装；
  - 汉化；VSCode目前直接安装后是英文界面，需要安装汉化插件Chinese (Simplified) Language Pack for Visual Studio Code；
  - 界面字体显示设置：`Ctrl+,`进入可视化设置界面，即可进行相关的显示设置；

### 2 Sublime Text安装与配置
#### 2.1 安装与配置
- 安装版与绿色版；
  - 直接安装便可配置鼠标右键菜单，且会写入注册表数据；
  - 解压即用，需要自己配置右键快捷菜单；
- 内部配置；
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

    # 输入激活许可（注：此处许可适用Sublime Text3 Build3211）
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
    # 这个地址时快时慢的，网好的时候可以使用该地址下载最新的channel_v3.json
    https://packagecontrol.io/channel_v3.json

    # 笔者github中channel_v3.json下载地址
    # 该json下载时间为2021年2月23日
    https://github.com/free-stardust/Notes/blob/main/CSNotes/EnvironmentDeploy/assets/channel_v3.json

    # 下载后将该文件放到Sublime Text3根目录的Packages文件夹中，毕竟是包清单，放在这里比较合理
    # 修改Package Control用户设置，Preference->package setting->package control->setting
    # 在Package Control.subime-setting--User文件中添加以下内容
    "channels":
	  [
		  "C:/Apps/TextEditors/SublimeText3/Packages/channel_v3.json"
	  ],

    # 进行完上述操作，Package Control即可正常使用
    ```
  - 汉化以及其他配置
    ```shell
    # 汉化
    # Ctrl+Shift+P打开命令窗口，输入Install Package
    # 候选中会看到Package Control: Install Package选项，点击后则会跳出包安装窗口
    # 在包安装窗口输入localizeMenu，安装该插件
    # 安装localizedMenu后，在Preference->show language->中文，即可显示中文界面

    # 侧边栏颜色同步
    # 安装SyncedSidebarBg，使侧边栏与编辑区主题配色一致
    # 注意，安装侧边栏背景同步插件后，当前侧边栏的配色不会同步默认的Monokai配色
    # 若要同步配色可以切换下主题，或者Ctrl+Shift+P安装Monokai Gray和Monokai Dark主题
    # 当然其他主题也可，笔者比较喜欢这个系列的主题

    # 禁用和启用插件
    # 禁用插件Ctrl+Shift+P，输入Disable Package，选择Package Control: Disable Package，弹出窗口选择要禁用的即可
    # 启用插件Ctrl+Shift+P，输入Enable Package，选择Package Control: Enable Package，弹出窗口选择要启用的即可

    # 移除插件
    # Ctrl+Shift+P，输入Remove Package，选择Package Control: Remove Packsge，弹出窗口选择要移除的即可

    # 安装SideBarEnhancements插件
    # 该插件增强了侧边栏功能
    # Ctrl+Shift+P，输入install package，选择Package Control: Install Package，弹出窗口输入插件名称点击即可安装
    # 安装后配置，该配置适合做web开发，做各种浏览器调试，从而增加了不同浏览器打开的快捷键
    # 配置文件Preference->Package Setting->Side Bar->Key Binding-User
    # 打开后在Default(Windows).sublime-keymap文件中添加以下内容
    [
      { "keys": ["ctrl+shift+c"], "command": "copy_path" },

      // edge
      { "keys": ["f1"], "command": "side_bar_files_open_with",
          "args": {
              "paths": [],
              "application": "C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe",
              "extensions":".*", // 匹配任何文件类型
          }
      },

      // chrome
      { "keys": ["f2"], "command": "side_bar_files_open_with",
          "args": {
              "paths": [],
              "application": "C:/Program Files (x86)/Google/Chrome/Application/chrome.exe",
              "extensions":".*"
          }
      },

      // firefox
      { "keys": ["f3"], "command": "side_bar_files_open_with",
          "args": {
              "paths": [],
              "application": "C:/Program Files/Mozilla Firefox/firefox.exe",
              "extensions":".*"
          }
       },

      // ie
      { "keys": ["f4"], "command": "side_bar_files_open_with",
          "args": {
              "paths": [],
              "application": "C:/Program Files/Internet Explorer/iexplore.exe",
              "extensions":".*"
          }
      },
    ]

    # 同以上步骤安装ConvertToUTF8插件，解决中文乱码的问题
    # 同以上步骤安装Bracket Highlighter，使括号、引号、html标签等高亮显示
    ```
  - 使用注意事项；
    ```shell
    # 对于Mac，笔者看到网上有人说，由于文件索引会经常卡死，并提供了解决方法，笔者也将其解决方案记录了过来
    # Preference->Setting-User
    # 在打开的文件中添加以下内容
    "index_file": false,

    # 在写代码的过程中，有时候由于分栏，或者现实问题，一行内容如果显示不下会自动换行，如果不希望自动换行，可以进行如下设置
    # 同样是在Preference->Setting-User
    "word_wrap": false,

    # 对于初次启动的Sublime，字体显示和大小可能不好看而且小，所以可以进行如下设置
    # 同样是在Preference->Setting-User
    "font_face": "JetBrains Mono NL",
	  "font_size": 12,

    # 默认情况下Sublime的vim模式是启用状态，如果一不小心按了esc就会是文件进入Command Mode，无法进行正常编辑
    # 这种情况下有两种处理方式
    # 第一种处理方式：点击A键或者I键或者O键即可推出Command Mode模式
    # 第二种处理方式：关闭vim模式，禁用Vintage插件
    # 同样是在Preference->Setting-User
    "ignored_packages":
    [
        "Vintage"
    ]
    ```
- 右键菜单配置；
  - `Win+R`输入regedit打开注册表；
  - 定位到`HKEY_CLASSES_ROOT->*->shell`路径下；
  - 新建`SublimeText3`项，并修改`(默认)`字符串值为`Sublime Text 打开`；
  - 在`SublimeText3`项下新建字符串值，重命名为`Icon`，并修改其中的值为`C:/Apps/TextEditors/SublimeText3/sublime_text.exe`；
  - 在`SublimeText3`项下新建`command`项，并修改`(默认)`字符串值为`"C:/Apps/TextEditors/SublimeText3/sublime_text.exe" "%1"`；
  - 自此，右键快捷菜单便会出现相关的快捷方式；
- 右键菜单配置示例图如下；
![SublimeText3_01|SublimeText3项下的配置](./image/TextEditors_SublimeText3_01.png)
![SublimeText3_01|command项下的配置](./image/TextEditors_SublimeText3_02.png)
### 3 Notepad++安装与配置
#### 3.1 安装与配置
- 安装版和绿色版；
  - 如果嫌配置麻烦，可以使用安装版本傻瓜式安装，一键配置；
  - 如果喜欢绿色版，选择改版，这个版本的安装包，解压即用，但是不会往注册表写入内容，所以右键也没有快捷方式；
- 针对绿色版的右键打开方式配置；
  - `Win+R`输入regedit打开注册表；
  - 定位到`HKEY_CLASSES_ROOT->*->shell`路径下；
  - 新建`Notepad++`项，并修改`(默认)`字符串值为`Nodepad++ 打开`；
  - 在`Notepad++`项下新建字符串值，重命名为`Icon`，并修改其中的值为`C:/Apps/TextEditors/Notepad++/notepad++.exe`；
  - 在`Nodepad++`项下新建`command`项，并修改`(默认)`字符串值为`"C:/Apps/TextEditors/Notepad++/notepad++.exe" "%1"`；
  - 自此，右键快捷菜单便会出现相关的快捷方式；
- 针对绿色版Nodepad++配置右键快捷菜单示例图如下；
![NPP_01|Notepad++项下的配置](./image/TextEditors_NPP_01.png)
![NPP_02|command项下的配置](./image/TextEditors_NPP_02.png)
#### 3.2 题外话
- Nodepad++为免费版文本编辑器，但是界面古老，且作者是个反华分子；
- 虽然该软件的作者有点难以让人接受，但是该软件还是有不少可去之处，比如批量删除空行还是挺方便的；
- 虽然功能强大，但是大部分时候用着还是不如VSCode和Sublime Text舒服，所以当作备用吧；