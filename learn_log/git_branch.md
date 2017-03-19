* [参考资料](https://git-scm.com/docs/git-branch)

* 本地新分支提交时指定远程创建新分支， 成功后这两个分支是否有关联？(木有！)

* 本地、远程两同名分支， 如果本地首次提交 git push 到该同名分支后， 这两分支是否就建立了关联？(没有关联！)

# git branch 指令
> if you wish to set tracking information for this branch you can do so with:

> git branch --set-upstream-to=origin/<branch> localBranchName

* 如果希望本地分支与远程分支建立关联可使用:
```
git branch --set-upstream-to=origin/remoteBranchName localBranchName`

```

## git branch 常用指令：
* git branch
	* 查看工程的分支列表（本地分支）

* git branch -va
	* 查看远程分支列表（查看前建议 使用 git pull -p 更新下远程分支信息）

* git checkout  remotes/origin/master
	* 切换到远程的 master 分支

* git checkout -b dev
	* 基于当前分支创建一个叫“dev”的分支,并切换到该分支，等于以下俩指令(-b 以当前分支为基础)
	* git branch dev   创建一叫“dev”的分支
	* git checkout dev  切换到“dev”分支

* git merge dev
	* 将当前分支（一般是master主分支）与叫“dev”（本地的dev分支）的分支代码合并

* git branch -d dev
	* 将叫“dev”的本地分支删除掉

* git branch -D dev
	* 将叫“dev”的本地分支删除掉（强制删除，即使该删除的分支有未提交代码）

* git branch -dr [origin/branch]
  * 相当于 `git branch -r -d origin/branch`删除的只是本地的缓存分支（`git branch -va`查看的那个），`git pull -p`可恢复；

* git push origin --delete [branch-name]
 	* 删除指定的远程分支（真正删除远程分支，需要当前账号的权限操作）

* git log —graph  
	* 查看分支合并情况（图方式显示）

* git push --set-upstream origin [localBranchName]
 	* 推送本地分支到远程分支并建立关联

如果忘了另起分支。而直接在主分支上修改代码，这可以使用下面的方法补救：

```
$ git branch new-feature-branch
$ git reset --hard
$ git checkout new-featrue-branch
```

但是这种方法不严谨，直接动了主分支的代码，可以通过下面的方法：

```
git  reset --hard是放弃本次修改，这个操作不可逆所以要慎重，如果如题主那样不小心修改主分支，也有办法：主分支上先commit，然后branch个新分支，主分支上用git reset  DEAD^切换要上一次commit,然后再checkout 切换到新建的分支。
```

## 相关指令：
* [git_checkout.md](https://github.com/huangtubiao/Git/blob/master/learn_log/git_checkout.md)  切换代码分支指令：使用git分支必定会用到的指令！
* [git_merge.md](https://github.com/huangtubiao/Git/blob/master/learn_log/git_merge.md) 合并分支指令：注意我合并的是**本地分支** 代码;
* [git_pull.md](https://github.com/huangtubiao/Git/blob/master/learn_log/git_pull.md) 更新、合并指令： 我能合并**远程分支**的代码哟！

## 相关ref
* [git 误删分支恢复方法](http://blog.csdn.net/fdipzone/article/details/50616386)
