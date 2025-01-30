# Node.js 与 npm

## 1 安装 Node.js 和 npm

如果要用 nvm ，请先看下面的第二章。

### 1.1 安装 Node.js 和 npm

npm 是 Node.js 平台的包管理器

1. 官网下载对应的安装包。
2. 双击安装程序，可修改安装路径。
3. Custom Setup 一步，尚不知道何意，可选默认安装。
4. Tools for Native Modules 不选自动下载，直接 Next 。
5. 然后 Install 等待 Finish 即可
6. 测试安装是否成功 node -v 、 npm -v 显示版本
7. 在安装目录下新建两个文件夹： node_cach 、 node_global 。为方便后续操作，可以修改这两个文件夹的权限
8. npm config set prefix \<global 文件夹的路径 \>
9. npm config set cache \<cache 文件夹的路径 \>
10. 然后配置环境变量。在【系统变量】中新建 NODE_PATH 变量值 ...\\node_global\\node_modules ，这之后 node_global 里会多一个文件夹。如果没有，则自己建一个，然后复制路径到变量值里。
11. 编辑【用户变量】里的 Path ，将 AppData...npm 一项改成 node_global 的路径
12. 在【系统变量】中编辑 Path 添加 %NODE_PATH% ，一直确定出来即可
13. 测试 npm config get prefix 、 npm config get cache

### 1.2 npm 命令

1. 显示版本
  - 显示 node.js 版本 node -v
  - 显示 npm 版本 npm -v
2. 安装
  - npm install \<module\> 
  - npm install \<module\> -g 全局安装，会安装到 node_global 里面
3. 更改镜像源
  - 淘宝镜像 npm config set registry http://registry.npm.taobao.org
  - 华为镜像 npm config set registry https://mirrors.huaweicloud.com/repository/npm/
  - 查看是否成功 npm config get registry
  - 恢复默认镜像 npm config set registry https://registry.npmjs.org
  - 单次安装使用镜像，添加 `--registry` 参数 npm install express --registry=http://registry.npm.taobao.org
4. 安装 cnpm （可选）
  - cnpm 是个中国版的 npm ，是淘宝定制的。
  - npm install -g cnpm --registry=https://registry.npmmirror.com
  - 查看是否安装成功 cnpm -v
5. idea 配置 npm

## 2 使用 nvm 和 nrm

因为 Node.js 的版本更迭很快，所以用 nvm 管理 Node.js 的版本。
如果已经下载过 Node.js 可以完全删除，然后用 nvm 的方法；或者也可以不删，但我没有验证过。

### 2.1 下载 nvm

1. nvm 安装
  1. 下载最新版 nvm 然后安装即可，在 nvm 路径页面选择 nvm 的路径，在 Node.js 的页面选择 npm 安装路径
  2. `nvm --version` 验证是否下载成功
  3. *可选* 可以更改 npm 包的下载源地址：在 nvm 文件夹下的 setting.txt 文件中添加 `node_mirror: http://npm.taobao.org/mirrors/node/` 和 `npm_mirror: https://npm.taobao.org/mirrors/npm/`
  4. *分支* 如果没有更改，在慢慢地下载完 npm 后下载 nrm 以管理 npm 镜像源
  5. 配置环境变量。这次用户变量和环境变量中，应该都配好了 NVM_HOME 和 NVM_SYMLINK 。
  6. **版本** 测试一下。 `nvm -v` 查看当前版本。
  7. `nvm --config`
  8. `nvm list` 查看已安装的 node 版本列表。
  9. `nvm install 14.20.1` 下载对应的版本，如 14.20.1 。
  10. `nvm use 14.20.1` 切换 node 版本。
  11. `nvm on` 开启 nvm 。
  12. `nvm off` 关闭 nvm 。
2. 通过 nvm 安装 node
  1. 用上一节的命令安装一个 nodejs 版本，然后切换到此版本。
  2. 查看是否安装成功 `node -v` `npm -v` 。
  3. 查看当前配置 `npm config ls` 。上一章已提过全局配置方法。
  4. 根据路径添加 node_global 环境变量
  5. npm 配置源 `npm config get registry` `npm config set registry <url>` 。
3. 全局安装 yarn
  1. `npm install -g yarn`
  2. `yarn -v` 查看 yarn 版本。
  3. yarn 配置源 `yarn config get registry` `yarn config set registry <url>` 。


### 2.2 安装 nrm

nrm npm registry manager 是 npm 的镜像管理工具，使用它可以快速地在 npm 源间切换

1. 有了 npm 以后，命令行执行命令 `npm install -g nrm` 全局安装 nrm 。
2. 执行命令 `nrm ls` 查看可选的源，其中带 `*` 的是当前使用的源。
3. *注意* 如果 nrm 不是可执行的命令，退一下 cmd 再进应该就好了。
4. *举例* 如果要切换到 taobao 源，执行命令 `nrm use taobao` 。
5. 直接使用 `nrm current` 命令，也可以查看当前源。
6. **增加** 可以增加定制的源，特别适用于添加企业内部的私有源。 `nrm add <registry> <url>` 其中 registry 为源名， url 为源的路径。
7. **删除** `nrm del <registry>` 删除对应的源。
8. **测试速度** `nrm test <registry>` 测试响应源的响应时间。 `nrm test` 可以同时查看所有源的响应时间。
9. **默认源** nrm 没有直接的命令设置默认源，可在 `.nrmrc` 中修改，这样每次使用 nrm 时都会默认切换到该源。
10. *注意* 切换源之后，可能要重新 `npm install` 等命令来更新项目的依赖包。
11. *注意* 在切换源之前，建议备份当前正在使用的 npm 源，以便在需要的时候能够快速恢复。


## 参考

- [1] [2024最新版Node.js下载安装及环境配置教程（非常详细）](https://blog.csdn.net/m0_74825074/article/details/144771279)
- [2] [NVM的安装使用与配置（node, npm, yarn）](https://blog.csdn.net/ppz8823/article/details/130862191)
- [3] [Vue 安装|软件工程基础上机指南](https://buaa-goodbro2021.github.io/SE-Labs/docs/labs/lab03/vuebook/vue_install/)
- [4] [nrm的使用（安装、配置、查看、切换、增加、删除、测试）](https://blog.csdn.net/qq_38872934/article/details/105706101)
- [5] [nrm的安装及使用](https://blog.csdn.net/ithongchou/article/details/143777074)
