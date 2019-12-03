
# Git

---

## 简介

 ![img](GIt.assets/clipboard.png)

Git是目前世界上最先进的**分布式版本控制系统**（没有之一)
Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开源的版本控制软件。
Git 与常用的版本控制工具 CVS, Subversion(SVN) 等不同，它采用了分布式版本库的方式，不必需服务器端软件支持。

### Git的作用

1、版本管理的服务器一旦崩溃，硬盘损坏，代码如何恢复？
2、系统正在上线运行，但是需要回复到前几天的某一个版本，如何处理？
3、如何管理一个分布在几个公司 或者世界各地、互不相识的大型开发团队？

 ![img](GIt.assets/wps5.jpeg)

### Git的优点

 - 容灾能力强

 - 本地版本管理

 - 异地协作开发
- 分支灵活

## Git 快速上手

### 安装 Git

1. Linux环境下安装 Git

   使用如下命令进行安装：

   ```shell
   # 安装依赖库
   yum install libcurl4-gnutls-dev libexpat1-dev gettext \ libz-dev libssl-dev
   # 安装Git的核心库
   yum install git-core
   # 查看Git版本
   git --version
   ```

2. Windows环境下安装 Git

   在官网下载 Git 安装包：[Git官网](http://msysgit.github.io/)
   然后直接按照步骤安装即可。其中需要注意如下几点：

   - 安装第五步时，**Adjusting your PATH environment** ，建议选择第一项：**Use Git from Git Bash only** ，只在 GIt Bash 中使用 Git 命令。第二项是在 Windows 的命令窗口 cmd 中使用 Git，而且会自动配置好 Git 命令的环境变量。第三项会自动配置好Git和Unix工具命令的环境变量。

   - 第六步，**Configuring the line ending conversions** ，配置行末结尾的转化。由于不同系统行末换行的处理方式不同(win是RELF，linux是LF)，所以，如果是跨平台项目在win中安装选择第一项，跨平台项目在Linux中安装选择第二项，非跨平台项目选择第三项。

   - 安装完成之后在任意文件路径下右键都可以打开Git的命令行窗口Bash。

     输入 `git --version` 即可查看已安装的git版本。

### git 初始化配置

​	由于git是一个分布式的版本控制系统，所以每个安装 git 的主机上都需要给 git 一个标识（用户名 + 邮箱）。一般全局配置用户信息。如下：

```shell
# 全局配置用户名&邮箱
git config --global user.name "xxx"
git config --global user.email "xxxxx@xxxxx.com"

# 单独配置用户名&邮箱
git --global user.name "xxx"
git --global user.email "xxxxx@xxxxx.com"
```

​	使用 --global表示全局属性，本机上所有 git 项目都会共用此属性。属性文件所在位置：`C:\Users\sk\.gitconfig`
​	如果在某项目中想要使用其他用户名或邮箱，只要在项目路径下使用git-bash 运行上面的命令，去掉 --global 即可完成单独配置。新的配置会保存在当前项目的 .gitconfig 文件中。

~~~shell
# 查看配置文件
git config --list
~~~

### 入门命令

~~~shell
# 初始化本地库
git init
# 添加对指定文件的操作到本地库/添加本项目所有操作
git add 文件名
git add .
# 提交操作
git commit -m "提交注释"

# 查看当前库状态/查看状态简易信息
git status
git stasus -s
# 查看工作区和暂存区之间的差异
git diff
# 查看日志/查看日志简易信息/查看日志详情（包含分支日志）
git log
git log --pretty=oneline
git log --oneline --graph
# 查看历史版本操作记录
git reflog --pretty=oneline

# 回退历史到上一版本/回退前n个版本
git reset --hard HEAD^
git reset --hard HEAD~n
# 穿越到某个版本（版本号定位）
git reset --hard f2996b8
# 文件检出
git checkout -- 文件名
~~~

备注：

	1. `git init` 初始化本地仓库， git有很多命令需要在仓库中运行，这是使用git的第一个命令。执行完此命令之后，当前目录下会生成一个.git目录。该目录包含了资源的所有元数据。其他项目目录保持不变。同类工具SVN则会在每个子目录都生成.svn目录。
 	2. 注意在进行 commit 提交操作时 直接带-m可以带注释提交。否则会进入编辑模式让你编辑注释。一次 commit 操作就会产生一个版本。
 	3. `git log` 和 `git reflog` 的区别在于前者只能查看 commit 提交记录版本。不包括已被删除的 commit 记录以及 reset 回退的版本。也就是说如果使用 reset 回退到某版本之后再使用 git log 就只能看到当前版本及以前的版本信息，无法看到当前版本之后的信息。而 `git reflog` 相当于是`git log`的增强版，从项目 clone 开始所有的版本信息全部都能看到。包括所有提交、回退的操作。一般用于要穿越到某个版本时查看版本号。
 	4. `git diff` 是比较工作目录和暂存区域之间的差异，也即修改之后还未暂存起来的内容。`git diff --cached filename` 比较暂存区和本地库最新版本之间的差异。`git diff HEAD filename` 比较工作区和本地库最新版本之间的差异。

### 进阶命令

```shell
# 
```



