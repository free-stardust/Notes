## NodeJS配置
---
### 1 下载网站
[https://nodejs.org/](https://nodejs.org/)
### 2 两种安装包(*.msi、*.zip)的区别
- 类型*.msi形式的安装包，是傻瓜式安装包，一路next就能安装好；
- 类型*.zip形式的安装包是绿色版，解压即可，只不过需要自己进行一些配置，比如环境变量等；
### 3 类型*.zip安装包的安装与配置
#### 3.1 安装
- 解压安装包；
- 在解压文件夹新建以下两个目录：
  - node_global： npm全局安装位置；
  - node_cache： npm缓存路径；
- 执行命令配置环境以上两个目录的路径：
    ```shell
    npm config set prefix "C:\NodeJS\NodeFile\node_global"
    npm config set cache "C:\NodeJS\NodeFile\node_cache"
    ```
- 修改npm资源镜像链接
    ```shell
    # 注：不修改npm安装以及进行以下测试可能会报这个错：rollbackFailedOptional verb npm-session；
    npm config set registry http://registry.npm.taobao.org
    ```
- 执行npm命令进行测试；
    ```shell
    npm install webpack -g

    # 执行后会在node_global文件夹下多一个webpack文件夹及相关文件；
    ```
#### 3.2 配置
- NODE_HOME环境变量
    ```shell
    # NODE_HOME
    C:\NodeJS\NodeFile;
    ```
- NODE_PATH环境变量
    ```shell
    # NODE_PATH
    C:\NodeJS\NodeFile\node_global;
    ```
- NODE_GLOBAL_PAT环境变量（可选）
    ```shell
    # NODE_GLOBAL_PATH
    C:\NodeJS\NodeFile\node_global\node_moules;
    ```