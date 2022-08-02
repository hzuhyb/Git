# git log 指令
* [参考资料](https://git-scm.com/docs/git-log)

## git log 常用指令：
* git log
	* 查看commit提交历史, 查看commit id方便回退；

* git log --pretty=oneline
	* 简短形式显示 commit 提交历史；(只显示每一次commit的id以及注释)

* git log branch_name1..branch_name2
	* 检查 branch_name1 分支是否部分落后于上 branch_name2 分支
	
* git reflog
	* 查看本地仓库所有改变列表（git reset的每次操作都会记录在该列表）

* git shortlog -sn
	* 列出代码仓库的提交者统计

## 相关指令：
* [git reset](https://github.com/huangtubiao/Git/blob/master/learn_log/git_reset.md) 代码撤销（回退）指令： `git log`好基友！
