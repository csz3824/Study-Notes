# git的一些常用操作
>最近两天有同事提交代码冲突让我解决，由于我一直用source tree这样的GUI工具提交代码，对git一些基本命令之前只是有一点了解，一不小心把代码上传到master上面了，后来又去revert什么的，走了不少弯路。。。今天再把git一些基本操作整理一下，今后尽量用git bash的命令行，少用GUI工具吧。

## 一、本地仓库的基本操作：
###      1. 通过命令 git init 把这个目录变成git可以管理的仓库【目录下会多了一个.git的目录，这个目录是Git来跟踪管理版本】
###  2. 把文件添加到版本库中：
#### 1) git add readme.txt添加到暂存区里面去。【提交文件和提交修改都需要先git add】
#### 2) 用命令 git commit告诉Git，把文件提交到仓库【git commit -m "这是提交的备注" 】
#### 3) 命令git status来查看是否还有文件未提交。
#### 4) 查看已经添加到暂存区但是没有提交的文件的修改 ：git diff readme.txt      
###     ３. git log查看git所有的提交记录



## 二、远端仓库的基本操作：

### 1.克隆远端分支:git clone git@github.com:csz3824/Study-Notes.git【可以用ssh方式或者https的方式】
### 2.将文件放到版本库
#### 1)使用上述git add、git commit将代码上传到本地仓库 
#### 2) 用git push命令将代码push到远端分支。git push <远程主机名> <本地分支名>:<远程分支名>【e.g.   git push origin k1:master】
### 3.将远端代码pull到本地。git pull <远程主机名> <远程分支名>:<本地分支名>【e.g.  git pull origin master:k1】
### 4.本地分支跟踪远程分支，多分支的时候Git push和git pull都需要指定远程分支和本地分支的名字，如果绑定了远程分支和本地分支的话，可以直接Git push/git pull：git branch --set-upstream <本地分支名>   <远程主机名>/<远程分支名>:  【e.g.  git branch --set-upstream k1 origin/k1】  


# git的一些常用操作
>最近两天有同事提交代码冲突让我解决，由于我一直用source tree这样的GUI工具提交代码，对git一些基本命令之前只是有一点了解，一不小心把代码上传到master上面了，后来又去revert什么的，走了不少弯路。。。今天再把git一些基本操作整理一下，今后尽量用git bash的命令行，少用GUI工具吧。

## 一、本地仓库的基本操作：
###      1. 通过命令 git init 把这个目录变成git可以管理的仓库【目录下会多了一个.git的目录，这个目录是Git来跟踪管理版本】
###  2. 把文件添加到版本库中：
#### 1) git add readme.txt添加到暂存区里面去。【提交文件和提交修改都需要先git add】
#### 2) 用命令 git commit告诉Git，把文件提交到仓库【git commit -m "这是提交的备注" 】
#### 3) 命令git status来查看是否还有文件未提交。
#### 4) 查看已经添加到暂存区但是没有提交的文件的修改 ：git diff readme.txt      
###     ３. git log查看git所有的提交记录



## 二、远端仓库的基本操作：

### 1.克隆远端分支:git clone git@github.com:csz3824/Study-Notes.git【可以用ssh方式或者https的方式】
### 2.将文件放到版本库
#### 1)使用上述git add、git commit将代码上传到本地仓库 
#### 2) 用git push命令将代码push到远端分支。git push <远程主机名> <本地分支名>:<远程分支名>【e.g.   git push origin k1:master】
### 3.将远端代码pull到本地。git pull <远程主机名> <远程分支名>:<本地分支名>【e.g.  git pull origin master:k1】
### 4.本地分支跟踪远程分支，多分支的时候Git push和git pull都需要指定远程分支和本地分支的名字，如果绑定了远程分支和本地分支的话，可以直接Git push/git pull：git branch --set-upstream <本地分支名>   <远程主机名>/<远程分支名>:  【e.g.  git branch --set-upstream k1 origin/k1】  




![git data transpot commands](https://github.com/csz3824/Study-Notes/blob/master/Git/git_data_transpot_commands.jpg)