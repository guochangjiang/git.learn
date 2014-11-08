## 浅显易懂的Git教程

### 目录
1. Git简介
2. 安装Git
3. 创建版本库
4. 时光机穿梭
5. 远程仓库
6. 分支管理
7. 标签管理
8. 使用GitHub
9. 自定义Git
10. 搭建Git服务器

### Git简介
Git是什么？Git是目前世界上最先进的分布式版本控制系统（没有之一）。

#### Git的诞生
2005年，Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了。Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。

#### 集中式vs分布式
Linus一直痛恨的CVS及SVN都是集中式的版本控制系统，而Git是分布式版本控制系统，集中式和分布式版本控制系统有什么区别呢？

先说集中式版本控制系统，版本库是集中存放在中央服务器的，而干活的时候，用的都是自己的电脑，所以要先从中央服务器取得最新的版本，然后开始干活，干完活了，再把自己的活推送给中央服务器。分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库，这样，你工作的时候，就不需要联网了，因为版本库就在你自己的电脑上。




### 安装Git完成后的初始设置

	$ git config --global usr.name
 	$ git config --global usr.email  
	
###1. 创建版本库  
####1.1 初始化目录为可管理的仓库
执行 **git init** 命令，在目录下生成一个.git 文件。

	$ git init 

####1.2 添加文本文件到版本库
第一步，通过 **git add**  命令把文件添加到仓库

	$ git add file.txt

第二步，通过 **git commit** 命令把文本文件提交到仓库

	$ git commit -m "wrote a text file"

*其中 -m后是本次提交的说明*  

为什么Git添加文件需要 add，commit两步呢？其中原因之一为 commit 可以一次提交很多文件，所以可以多次 add 不同的文件，比如

	$ git add file1.txt
	$ git add file2.txt
	$ git add file3.txt
	$ git commit -m "add 3 files."
###2. 时光机穿梭
####2.1 仓库状态查看
第一步，**git status** 命令可以时刻掌控仓库状态，监控文件修改情况

	$ git status
第二步，git diff 命令查看文件修改详情

	$ git diff modified.txt
第三步，git add 命令添加文件到仓库

	$ git add modified.txt
第四步，git status 命令查看待提交文件信息

	$ git status
第五步，git commit -m "" 命令提交文件
	
	$ git commit -m "modify file modified.txt"
第六步，git status 命令查看仓库的当前状态

	$ git status
Git会告诉我们当前没有需要提交的修改，工作目录是干净的。

####2.2 版本回退

第一步，**git log** 命令查看历史信息

	$ git log
	commit 3618dh8724779dfdj8e8797
	author: xxx <xxx#email.com>
	Date: xxxx
	note.information
git log 命令显示从最近到最远的的提交日志。如果觉得输出信息过多，可以添加 --pretty=oneline 参数简化信息

	$ git log --pretty=oneline
	618dh8724779dfdj8e8797  note.information
*其中长字符串“618dh8724779dfdj8e8797”是十六进制的 commit id.*

文件版本简介
> 在Git中，**用HEAD表示当前版本**，也就是最新提交的"618dh8.....dfdj8e8797"，**上一版本就是HEAD^**，上上一个版本是HEAD^^，………往上100个版本是HEAD~100

第二步，**git reset** 命令回退到指定版本

	$ git reset --hard HEAD^
	$ cat file.txt  #查看文件内容
	$ git log #回退版本以后的历史记录不见了
原来的最新版本已经消失了，好比从21世纪穿越到19世纪，就会回不来了。其实还是可以穿越回来的，就是找到相应版本的commit id，就可以指定回到未来的某个版本

	$ git reset --hard xxxxxxx   #commit id/版本号没有必要写全，前几位就可以了
如果无法找到commit id，可用 **git reflog** 命令查看命令历史记录

	$ git reflog
	xxxxx HEAD@(0): reset: move to HEAD^
	xxxxx HEAD@(1):commit: note.information ##这样就可以找到未来版本号了
	…………


###3. 远程仓库

####3.2 添加远程库
第一步，登陆GitHub，然后在右上角找到"Creat a new repo"按钮，创建新的仓库。在Repository name填入与本地仓库同名，最后按照默认设置完成创建。
第二步，根据GitHub提示在本地仓库下运行命令**git remote add origin <url\>** 即可将本地仓库与远程仓库相关联。

	$ git remote add origin git@github.com:username/repo.name.git
或者运行

	$ git remote add origin https://github.com/username/repo.name.git
如果出现以下出错信息

	fatal: remote origin already exists.

此时需要运行命令 **git remote rm origin** 后再重新运行上步关联命令。

	$ git remote rm origin
第三步，将本地库中的所有内容推送到远程库上，命令为 **git push -u origin master** 

	$ git push -u origin master
	
> 用git push命令实际上是把当前分支master推送到远程。第一次推送master分支时，

> 定义远程服务器别名origin：`$ git remote add origin git@github.com:xxx/github-test.git`.本地和远程实行合并，本地默认为master:`$ git push origin master`;

> 当通过Github以xxx对github-test作出修改时，由于本地快照与Github远程服务器上的不一致，会引起以下错误：
```
! [rejected]        master -> master (fetch first) 
error: failed to push some refs to 'git@github.com:xxx/puppet' 
hint: Updates were rejected because the remote contains work that you do 
hint: not have locally. This is usually caused by another repository pushing 
hint: to the same ref. You may want to first integrate the remote changes 
hint: (e.g., 'git pull ...') before pushing again. 
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
此时可①通过pull子命令更新Github项目中作出的更改：`$ git pull origin master`,之后再执行`$ git push origin master`;②可用`git push -f`进行强制上传覆盖。


删除文件用 git rm
改文件名用 git mv
使用 git 遇到问题时，git status 一下，通常都会有提示告诉你该怎么做