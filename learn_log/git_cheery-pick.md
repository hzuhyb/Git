# git cheery-pick 指令

## 参考资料：
* [git cherry-pick官方API](https://git-scm.com/docs/git-cherry-pick)
* [git cherry-pick的使用](https://blog.csdn.net/fightfightfight/article/details/81039050)

## 实践总结：
* `git cherry-pick` 将其他分支的 commit 对应的改动添加到当前分支, 当然其他分支的代码不会受到影响；


## git cheery-pick 常用指令：
* git cherry-pick <commit-id>
	* 将指定 commitId（一般是其他分支的 commitId）的改动， 添加到当前分支；

* git cherry-pick --continue
    * 当迁移改动出现冲突时， 手动解决完冲突后，该指令告诉 git 冲突已解决；

* git cherry-pick --quit
    * 当迁移改动出现冲突时，忽略冲突继续下一步骤（生成新的 commitId）；

* git cherry-pick --abort
    * 当迁移改动出现冲突时，撤销 `git  cherry-pick` 指令；
