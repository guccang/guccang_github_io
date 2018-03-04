title: git log
date: 2015-07-31 00:12:25
tags:
- git
- all
-------

***

```bash
git reflog
```
*  作用:显示所有HEAD改变历史
*  HEAD改变条件有  
*  git commit命令  
*  分支切换
*  git merge命令
*  ...待补充

***

```bash
git log
```
1.  作用: 查看提交历史

2.  参数：

	* -p 按补丁格式显示每个更新之间的差异。
	* --stat 显示每次更新的文件修改统计信息。
	* --shortstat 只显示 --stat 中最后的行数修改添加移除统计。
	* --name-only 仅在提交信息后显示已修改的文件清单。
	* --name-status 显示新增、修改、删除的文件清单。
	* --abbrev-commit 仅显示 SHA-1 的前几个字符，而非所有的 40 个字符。
	* --relative-date 使用较短的相对时间显示（比如，“2 weeks ago”）。
	* --graph 显示 ASCII 图形表示的分支合并历史。
	* --pretty 使用其他格式显示历史提交信息。可用的选项包括 oneline，short，full，fuller 和 format（后跟指定格式）。
    
3.  常用参数: 
	* git log -p  	// -p表示显示，提交历史的差异部分。
	* git log -n 		// n为数字,表示显示n条git 提交数据。没有-p 不会显示提交历史。比较整洁。
	* git log --stat  // --stat 仅仅显示，增改行数的统计。
	* git log --graph // 图形化显示分支提交数据
    
4.  格式化参数:
	* git log --pretty=oneline // 表示log数据在一行显示，和整洁。
	* git log --pretty=format:"%h - %an, %ar : %s" // format参数，后面接占位符。
    
    
		选项	 	说明
		%H			提交对象（commit）的完整哈希字串
		%h			提交对象的简短哈希字串
		%T			树对象（tree）的完整哈希字串
		%t			树对象的简短哈希字串
		%P			父对象（parent）的完整哈希字串
		%p			父对象的简短哈希字串
		%an			作者（author）的名字
		%ae			作者的电子邮件地址
		%ad			作者修订日期（可以用 -date= 选项定制格式）
		%ar			作者修订日期，按多久以前的方式显示
		%cn			提交者(committer)的名字
		%ce			提交者的电子邮件地址
		%cd			提交日期
		%cr			提交日期，按多久以前的方式显示
		%s			提交说明
