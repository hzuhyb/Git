# git push 指令
* [参考资料](http://www.yiibai.com/git/git_push.html)
* git push <远程主机名> <本地分支名>:<远程分支名>
* 如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略。
* `git push origin`
* 上面命令表示，将当前分支推送到origin主机的对应分支。

## git stash 常用指令：
* git push
	* 推送代码至与当前分支关联的远程分支

* git push origin remoteBranchName
	* 推送代码至指定的远程分支

* git push origin newBranch:newBranch
	* 推送分支到远程并在远程创建一同名分支， ’newBranch’为本地分支，线上没有的那种

* git push origin --delete [branch-name]
  * 删除远程分支

* git push origin HEAD --force
  * 推送到本地到远程仓库：让远程仓库代码和你本地一样，到当前你本地的版本。


## 相关指令：
* [git_status.md](https://github.com/huangtubiao/Git/blob/master/learn_log/git_status.md)  查看当前代码状态指令： 使用我这个指令，只是为了确认提交远程是否成功而已。。。
