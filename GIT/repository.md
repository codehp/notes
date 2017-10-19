版本库（Repository）
===========================

版本库又名仓库，英文名Repository

获取 Git 仓库
-------------------

有两种取得 Git 项目仓库的方法。 第一种是在现有项目或目录下导入所有文件到 Git 中； 第二种是从一个服务器克隆一个现有的 Git 仓库。

###在现有目录中初始化仓库
如果你打算使用 Git 来对现有的项目进行管理，你只需要进入该项目目录并输入：
```
$ mkdir notes
$ cd notes
$ git init
````
该命令将创建一个名为 .git 的子目录，这个子目录含有你初始化的 Git 仓库中所有的必须文件，这些文件是 Git 仓库的骨干。 但是，在这个时候，我们仅仅是做了一个初始化的操作，你的项目里的文件还没有被跟踪。 (参见 [Git 内部原理](https://git-scm.com/book/zh/v2/Git-%E5%86%85%E9%83%A8%E5%8E%9F%E7%90%86-%E5%BA%95%E5%B1%82%E5%91%BD%E4%BB%A4%E5%92%8C%E9%AB%98%E5%B1%82%E5%91%BD%E4%BB%A4#_git_internals) 来了解更多关于到底 .git 文件夹中包含了哪些文件的信息。)

###把文件添加到版本库
首先在刚刚创建的notes目录下编写一个readme.txt文件并且添加提交到GIT仓库
```
$ touch readme.txt
$ git add readme.txt
$ git commit -m 'add readme.txt'
```
现在，你已经得到了一个实际维护（或者说是跟踪）着若干个文件的 Git 仓库。

克隆现有的仓库
-------------------
如果你想获得一份已经存在了的 Git 仓库的拷贝，比如说，你想为某个开源项目贡献自己的一份力，这时就要用到 git clone 命令。 如果你对其它的 VCS 系统（比如说Subversion）很熟悉，请留心一下你所使用的命令是"clone"而不是"checkout"。 这是 Git 区别于其它版本控制系统的一个重要特性，Git 克隆的是该 Git 仓库服务器上的几乎所有数据，而不是仅仅复制完成你的工作所需要文件。 当你执行 git clone 命令的时候，默认配置下远程 Git 仓库中的每一个文件的每一个版本都将被拉取下来。 事实上，如果你的服务器的磁盘坏掉了，你通常可以使用任何一个克隆下来的用户端来重建服务器上的仓库（虽然可能会丢失某些服务器端的挂钩设置，但是所有版本的数据仍在，详见 [在服务器上搭建 Git](https://git-scm.com/book/zh/v2/%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E5%9C%A8%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E6%90%AD%E5%BB%BA-Git#_git_on_the_server) ）。


###远程库
注册一个GitHub账号，本地Git仓库和GitHub仓库之间的传输是通过SSH加密的，所以需要获得SSH KEY
1. 创建SSH KEY，先在GIT BASH下输入
`$ ls -rtl $HOME/.ssh/id_rsa*`，如果有id_rsa、id_rsa.pub文件可以跳过该步骤，否则在GIT BASH下创建SSH KEY
```
ssh-keygen -t rsa -C "email@mail.com"
```
2. 在GITHUB中找到Account Setting->SSH Keys页面，点击Add SSH Key。填个标题后在Key里粘贴id_rsa.pub的文本

###添加远程库
当你本地已经存在了一个本地GIT仓库，需要把本地仓库添加到远程库时候，首先登陆GitHub，右上角找到“Create a new repo”按钮，创建新的仓库notes，根据GitHub的提示，在本地的notes仓库下运行命令：
```
$ git remote add origin git@github.com:GITHUB账号/notes.git
```
接下来就可以把本地的内容推送到GITHUB上了
```
$ git push -u origin master
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 420 bytes | 420.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:codehp/notes.git
   c598bf4..96acc31  master -> master
```

第一次推送时候使用`push -u`参数是会把本地分支和远程分支关联，后面就可以不在加`-u`参数

###克隆远程库
当你已经拥有一个远程库，想把远程库的内容克隆到本地库时
```
$git clone git@github.com:GITHUB账号/notes.git
或者使用以下https等协议克隆
$git clone https://github.com/GITHUB账号/notes.git
```

###参考书籍
[Pro Git](https://git-scm.com/book/zh/v2)
