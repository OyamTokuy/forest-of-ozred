# Node.js 与 npm

参考资料：

1. [2024最新版Node.js下载安装及环境配置教程（非常详细）](https://blog.csdn.net/m0_74825074/article/details/144771279)

## 介绍

npm 是 Node.js 平台的包管理器

## 安装 Node.js

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
## npm 命令

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