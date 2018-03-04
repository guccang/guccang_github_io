title: git command
date: 2015-07-22 01:29:03
tags:
- git
- tools
- all
---

***
***

##[git 命令]

git 版本管理是基于快照(也就是copy备份)每个单独文件来完成的，而以前使用的svn则是记录了文件的不同部分。
<!-- mroe -->
git 有一个特点就是，每个版本只保留,上个版本变动的文件，因此非常优雅。

***


1.  git status
    文件状态,git status
    untracked-未加入github维护 
    unmodified-未改变的
    modified-改变的/修改，新增，删除，冲突
    staged-处于暂缓处区域的执行git add命令后进入staged状态,等待commit 到本地仓库。
 
2.  git clone url name
    clone创建工程

        git init
        vim .gitignore
        git remote add origin url
        git push origin master

    本地创建工程
    github创建项目 url
    本地创建工程文件夹，进入文件夹
    git init 初始化，用github管理文件夹
    vim .gitignore 创建一个忽略文件，这很重要。
    git remote add origin url 关联远程仓库，然后push，pull就用origin别名来做了。而不需要完整的url了。
    git push origin master  / git push  / 默认在master分支，所以直接git push就将本地文件同步到远端仓库。
    至此，仓库创建完成。

3.  修改,添加,删除.
        git status
        git add .
        git commit -a -m "comment"
        git push
    git staus 查看文件状态，修改，新增，删除，冲突。
    git add . 添加所有状态改变文件。
    git commit -a -m "comment" 提交到本地仓库，保存。生成commit日志。而后就确保了，你怎么乱来都不会丢失掉提交。
    git push 讲修改同步到远端仓库。那么，呵呵~~永远都丢不了了。
    git rm file 删除文件
    git rm -rf dir 删除文件夹

4.  分支相关
        git branch -a 
        git checkout -b newBranch master
        git branch -d barnchName
        git branch -r -d branchName

    分支创建
    git branch -a 查看所有分支
    git checkout -b newBranch master 从master分支上创建一个名为newBranch的分支。
    编辑，修改后。
        git add .
        git commit -a -m "comment"
    git push 会提示错误如下
        fatal: The current branch bare02 has no upstream branch.
        To push the current branch and set the remote as upstream, use
        git push --set-upstream origin bare02
    表示远端其实没有这个分支存在，需要使用如下简单命令即可。
    git push -u origin newBranch 表示远端没有，那么就创建一个newBranch，然后提交ok，远端就有新分支名字叫做newBranch了
    这样就ok了。
    
    删除分支
        git branch -d origin/branchName
        git branch -r -d origin/branchName 远程仓库分支

5.  抓取远端仓库数据
        git pull origin
        git pull origin bare02
    其他人checkout分支
    git pull origin 
    这个命令会将origin关联的所有分支都抓取下来。
    git checkout newBranch 切换到newBranch分支。

    在分支上，合并其他分支修改。
    比如，处于bare01分支，远端库bare02分支存在有用的内容，你需要合入。
    这种情况通常发生在clone项目，或者开发项目想发布项目合并时发生。分支间的合并。
    git pull origin bare02  然后你所处的分支bare01就会讲bare02的分支内容合并到bare01。
    然后相当于执行了三部修改bare01，add执行，commit执行。剩下的就是push 操作，将合并同步到远端仓库了。

6.  检出
        git checkout
    git checkout 实际上是修改HEAD文件的内容，让其指向不同的branch
    HEAD文件指向的branch就是当前branch.
    一般来讲，HEAD的内容是指向staging（暂存区）的master文件的
        detached HEAD
    如果让HEAD文件指向一个commit id，那就变成了detached HEAD。git checkout 可以达到这个效果

7.  远端仓库操作
        git pull / git fetch
    git fetch origin master:bare01 从远端仓库master分支抓取最新内容到本地bare01分支，这是files处于modified状态。
    git diff bare01  比较一下，bare01分支和本地分支。
    git merge bare01 合并bare01分支到本地分支
    git pull 相当于 git fetch + git merge
    git pull origin master 从远端仓库master分支抓取最新内容到HEAD指向分支，然后合并。

8.  标签
        git tag
    git tag 显示所有标签
    git tag -a v0.2 -m "create v0.2 tag" 创建一个名叫v0.2的标签
    git tag -d v0.2 删除标签
    git push origin --tag 将所有标签同步到远端服务器。
    git push origin:refs/tags/v0.2 删除远端标签
