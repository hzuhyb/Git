# git merge 指令
* [参考资料](https://git-scm.com/docs/git-merge)
* [参考资料2](http://blog.csdn.net/hudashi/article/details/7664382)
* [合并分支如何简洁](http://hungyuhei.github.io/2012/08/07/better-git-commit-graph-using-pull---rebase-and-merge---no-ff.html)
* 关于 git merge 与 git rebase的区别请看这个[教程](http://backlogtool.com/git-guide/cn/stepup/stepup1_4.html);

## git merge 常用指令：
* git merge branchName
	* 将当前分支 与 **本地** 叫“branchName”分支的代码合并（branchName代码合并到当前分支）；

* git merge --no-ff branchName
	* 将当前分支 与 **本地** 叫“branchName”分支的代码合并（branchName代码合并到当前分支）,并且显示合并细节，具体表现在 提交线路图会出现交叉线；

* git merge --squash branchName
  * 合并新分支代码时， 只将分支新改动放入暂存区，不产生commit;（合并分支减少commit）

## 相关文章：
- [洁癖者用 Git：pull --rebase 和 merge --no-ff](http://hungyuhei.github.io/2012/08/07/better-git-commit-graph-using-pull---rebase-and-merge---no-ff.html)
