## 文本编辑器安装与配置
---
### 1 VSCode安装与配置
### 2 Sublime Text安装与配置

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