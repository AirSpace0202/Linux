## git 的基本概念

+ 工作区：仓库的目录，工作区独立于各个分支
+ 暂存区：数据暂时存放的区域，类似于工作区写入版本前的缓存区。缓存区独立于各个分支。
+ 版本库：存放所有已经提交到本地仓库的代码版本
+ 版本结构：树结构，树中的每个节点类似于一个代码版本



### git命令分类整理

#### 全局设置

``git config --global user.name xxx``：设置全局用户名，信息记录在~/.gitconfig文件中
``git config --global user.email xxx@xxx.com``：设置全局邮箱地址，信息记录在~/.gitconfig文件中
``git init``：将当前目录配置成git仓库，信息记录在隐藏的.git文件夹中

#### 常用命令

``git add XX`` ：将XX文件添加到暂存区
``git commit -m "给自己看的备注信息"``：将暂存区的内容提交到当前分支
``git status``：查看仓库状态
``git log``：查看当前分支的所有版本
``git push -u`` (第一次需要-u以后不需要) ：将当前分支推送到远程仓库

``git clone git@git.acwing.com:xxx/XXX.git``：将远程仓库XXX下载到当前目录下
``git branch``：查看所有分支和当前所处分支

#### 查看命令

``git diff XX``：查看XX文件相对于暂存区修改了哪些内容
``git status``：查看仓库状态
``git log``：查看当前分支的所有版本
``git log --pretty=oneline``：用一行来显示
``git reflog``：查看HEAD指针的移动历史（包括被回滚的版本）（HEAD指针始终指向当前版本）
``git branch``：查看所有分支和当前所处分支
``git pull`` ：将远程仓库的当前分支与本地仓库的当前分支合并

#### 删除命令

``git rm --cached XX``：将文件从仓库索引目录中删掉，不希望管理这个文件
``git restore --staged xx``：==将xx从暂存区里移除==
``git checkout — XX或git restore XX``：==将XX文件尚未加入暂存区的修改全部撤销==

#### 代码回滚

``git reset --hard HEAD^ 或git reset --hard HEAD~ ``：将代码库回滚到上一个版本
``git reset --hard HEAD^^``：往上回滚两次，以此类推
``git reset --hard`` 版本号：回滚到某一特定版本

#### 远程仓库

``git remote add origin git@git.acwing.com:xxx/XXX.git``：将本地仓库关联到远程仓库

终端输入ssh-keygen生成公钥，将公钥上传至github仓库中，进行连接，才能将本地仓库的文件上传到云端

``git push -u`` (第一次需要-u以后不需要) ：将当前分支推送到远程仓库
``git push origin branch_name``：将本地的某个分支推送到远程仓库
``git clone git@git.acwing.com:xxx/XXX.git``：将远程仓库XXX下载到当前目录下
``git push --set-upstream origin branch_name``：设置本地的branch_name分支对应远程仓库的branch_name分支
``git push -d origin branch_name``：删除远程仓库的branch_name分支
``git checkout -t origin/branch_name`` 将远程的branch_name分支拉取到本地
``git pull`` ：将远程仓库的当前分支与本地仓库的当前分支合并
``git pull origin branch_name``：将远程仓库的branch_name分支与本地仓库的当前分支合并
``git branch --set-upstream-to=origin/branch_name1 branch_name2``：将远程的``branch_name1``分支与本地的``branch_name2``分支对应



**git restore --staged** 用于将暂存区移至工作区

**git restore**

（1）（暂存区无文件）若工作区有文件，将工作区的文件删掉，当前文件变为上一个commit结点（版本库的head指针指向的文件），也称为版本回滚。

（2）（暂存区，工作区有文件）将工作区的文件删掉，也称为暂存回滚。



1、***git checkout branch_name*** 切换到branch_name分支

***git checkout -b branch_name*** 创建并切换到branch_name分支



1、***git branch*** 用于查看当前所在的分支和所有分支

2、***git branch -d branch_name*** 用于删除本地的branch_name分支，需要先切换到别的分支才能进行删除

***git push -d origin branch_name*** 用于删除云端的branch_name分支



1、***git push --set-upstream origin branch_name*** 将本地的branch_name和云端的branch_name分支进行绑定，绑定完后可以用git push将本地分支内容传输到云端分支内容

***git push*** 在进行完绑定之后可以用git push将本地的分支内容传输给云端的分支

2、***git branch --set-upstream-to=origin/branch_name1 branch_name2***

将云端的branch_name1分支和本地的branch_name2进行绑定，然后直接进行git pull就可以将云端的分支内容传输给本地

***git pull*** 在进行完绑定之后就可以用git pull将云端的分支内容传输给本地的分支







