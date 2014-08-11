
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
