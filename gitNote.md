git学习笔记



开源的 分布式 版本控制系统 特点（吹点）高大上



版本控制系统（与手动管理版本对比）： 

简要理解

为项目创建 更新历史记录，记录下每一个时期的项目状态，方便 回顾和对比

特性概括

自动记录每个文件改动，允许他人协作，随时可查看任意一次改动



插入案例介绍-Linux-diff-手动

集中式的版本控制系统 ，免费的CVS，SVN，收费的ClearCase

分布式 BitKeeper（收费的），Bazaar，Git（追加单最流行）

Git--GitHub 开源项目-免费Git存储网站



集中式vs分布式

集中式：

​	版本库在重要服务器，与操作端分离，工作室要不断获取和上传旧版本和新版本

​	必须联网，网速慢时传输文件成为煎熬（局域网体验姣好）

分布式：

​	没有中央服务器，每个操作端都有完整版本库，可以脱机使用

​	p2p点对点，互相推送修改，互相查看彼此修改

​	较之集中式，版本库安全性更高

​	伪中央服务器（一台操作端电脑，方便各自修改的交换）

​	Git强大的分支管理等



Git安装（Windows上）

msysgit Windows版的git

 https://gitforwindows.org/

$ git config --global user.name "UrName"

$ git config --global user.email "181...89@qq.com"

$ git config --global color.ui true/false 启用/禁用配色方案

创建版本库

​	找个地方弄个空文件夹（空目录），其路径上不能有任何中文字符

​	$ mkdir DirectorName 	创建目录

​	$ cd DirectorName	 进入目录

​	$ type nul>FileName.Exp 创建文件

​	$ pwd	 显示当前目录

​	ls -ah 显示隐藏文件/目录

（第一个字母是L的小写，为便于记忆，因为这里指令都是小写，所以不会是大写的 i ）

​	用git init命令转化该目录，使之成为可被Git管理的仓库

​		$ git init



注意：

​	版本控制系统只能跟踪文本文件（txt，html等）的改动，能知悉改动了哪里以及改动细节，而针对二进制文件（图片，视频，word文档等），只能知悉其改动前后文件大小，无法知悉改动细节

​	仅限存文本编写的文件作为完美发挥版本控制系统的对象

​	win系统的记事本对UTF-8编码的文件保存方式不合理，在每个文件开头填入一串十六进制字符，使用记事本编辑和修改文本文件会给你带来大量问题（教程推荐Notepad++，设置默认编码为UTF-8 without BOM）

​	必须放在创建的git库中



子目录？？？

$ git add FileName1 FileName2

从工作区向缓存区添加若干文件，成功时无提示

$ git add .   将工作区所有文件添入

$ git add *.html 将某一类文件添入

$ git commit -m "Update Instruction"

从缓存区向本地库添加一条记录，成功时会提示 file changed

$ git commit 直接回车 

会进入预选的编辑器（安装时候某个选项）

在编辑器里完成编辑后保存并关闭对应编辑文件（或输入esc:wq 回车），git会统一处理



$ git status 

查看库当前状态，文件是否被修改等

$ git diff FileNameAdded

查看已录入文件的修改（新旧版不同）



修改后的文件需要再次写入库（上文add命令）



$ git log 

输出近期版本和版本指针 作者 时间

$ git reflog

输出有关版本和版本指针


$ git reset --hard commitIDTip

将指针（head）指向对应提交片段匹配的版本

git reset .

git reset File


git checkout . 将所有add添入（缓存区）全部回到工作区 （丢失找回）

git checkout File



分支 如果做了某些操作后的版本簇，

操作处于哪个分支，就影响哪个分支

只有分支创建后的操作才会影响之

master 主分支

git branch branchName 创建分支

git branch -a 查看分支

git checkout BranchName 切换分支

git push origin branchName 向GitHub库添入分支

合并分支

位于主分支

git merge branchName 将对应分支合并到主分支

git branch -D branchName 删除对应分支

冲突解决

git diff --name-only --diff-filter=U

查看冲突

冲突部分会被

 <<<<<  内容A  =====  内容B  >>>>>

这样标注，需要手动解决





git rm FileName.Exp

从本地库中移除对应文件



clear清空命令行



可在命令行（cmd或powershell）使用（无需键入$)

git remote add origin https://github.com/hellarose/gitBankForLab.git

git push -u origin master
上传GitHub

此处用vscode的powershell会令人发疯，建议老实点使用正经命令行

新建一个空文件夹
git clone github地址
克隆一个库



用GitHub作为作品展示/个人博客主页

建立GitHubpage库

GitHubUserName.github.io

以GitHub账号用户名为一部分的特定写法名称

本地克隆一份git clone URL

将作品（index.html等）放入，然后git add commit push一套上传

在浏览器地址栏键入https://GitHubUserName.github.io

剩下的就是多试几遍看缘分了