title: github 常用命令
date: 2015-01-03 10:20:27
tags: 
    - git-command
---

1、查看当前git的版本

    $ git version   #查看当前git版本

2、Debian或Ubuntu linux系统上的命令安装git

    $ sudo apt-get install git-core #系统版本老一点
    $ sudo apt-get install git      #系统版本新一点

3、Mac OS X系统上是通过homebrew来安装git

    $ brew install git  #前提是已经安装homebrew

4、Window 系统可以去Git官网[下载安装程序](https://git-scm.com/downloads)

    $安装完成后，打开Git Bash

5、安装完成后，还需要最后一步设置，在命令行输入：

    $ git config --global user.name "Your Name"
    $ git config --global user.email "email@example.com"
    每个机器都必须自报家门：你的名字和Email地址。用了--global参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

6、生成密钥，关联远端仓库时候需要提供公钥，本地保存私钥.

    $ ssh-keygen -t rsa -C "youremail@example.com"
    在本地/User/.ssh/ 目录下有会生成两个文件id_rsa、id_rsa.pub，id_rsa文件保存的是私钥，保存于本地，id_rsa.pub文件保存的是公钥，需要将里面内容上传到远端仓库

7、查看用户名和邮箱地址.

    $ git config user.name
    $ git config user.email

<!--more-->

8、一些常用命令:

    $ git init  #把当前目录变成Git可以管理的本地仓库
    $ git add 文件   #告诉Git，把文件添加到本地仓库
    $ git add .     #把当前所有文件添加到本地仓库
    $ git commit -m "说明"   #告诉Git，把文件提交到本地仓库，并说明一下本次提交
    $ git status    #查看当前仓库状态
    $ git diff      #查看当前仓库修改了的文件和修改的内容
    $ git log       #查看最近到最远的提交日志,追加一个参数看看 --pretty=oneline
    $ git remote add origin git@github.com:xxx/yyy.git  #将本地仓库和远程仓库关联
    $ git push -u origin master    #第一次推送到远程master分支，并且把本地master分支和远程master分支关联起来,以后的推送或者拉取时就可以简化命令
    $ git clone 远程仓库地址  #将远端代码克隆到当前目录,若要指定目录则在后面追加YourDir
    $ git branch            #查看本地仓库所有分支
    $ git branch -r         #查看远程仓库所有分支
    $ git branch -a         #查看本地和远程仓库所有分支
    $ git branch 分支名      #新建分支
    $ git branch -d 分支名   #删除分支
    $ git checkout 分支名 #切换分支
    $ git remote -v     #查看远程仓库地址

全局配置
    
    $ git config --global user.name "yourname"  #git的用户名
    $ git config --global user.email "email@example.com"  #git的登录账号
    $ git config --global core.editor vim    #设置默认编辑器
    $ git config --global merge.tool vimdiff #设置默认的对比文件差异工具
    $ git config --global color.status auto  #显示颜色信息
    $ git config --global color.branch auto  #显示颜色信息
    $ git config --global color.interactive auto #显示颜色信息
    $ git config --global color.diff auto     #显示颜色信息
    $ git config --global push.default simple #简化提交
    $ git config core.ignorecase false #设置大小写敏感
    $ git config --list #查看配置的信息
    $ git help config   #获取帮助信息
    
