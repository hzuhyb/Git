## 概念说明
首先要理解这个base，base也就是基础的意思，当我们从代码分支上获取代码的时候，我们就有了一个基础，也就是base，此后的修改我们都是在这个基础之上进行的，但是当我们需要提交修改的时候，遇到了别人的代码，变基这个操作就是在这个时候，我们不去合并别人的代码，而是直接把我们原先的基础变掉，变成以别人修改过后的新代码为基础，把我们的修改在这个新的基础之上重新进行。基础变掉了，所以叫作变基。

那么，变基有什么好处呢？好处之一是可以使我们的时间线变得非常干净，以前采用合并的时候，时间线里完整记录了我们的代码是从哪个基础上拉取出来的，做了哪些修改，然后又在哪个时间点合并回分支去，而采用变基之后，时间线上不再反映拉取的时间点，因为每次提交都是以最新代码为基础的，所以时间线就变成了一根直线。

## 实践总结：
* git merge 跟 git rebase 经常一起讨论，但它们不是相互替换的关系；；

* git rebase 是git merge的辅助，用了git rebase还得用git merge完成分支合并；

* 使用git rebase后，用法上比git merge复杂， 例如将experiment分支代码合并到master:
<img width="468" alt="git_rebase_s1" src="https://user-images.githubusercontent.com/10185166/182366400-c5d43740-6f02-4e18-b48b-a8cc1a4c9c62.png">

* git merge 是切换到master分支然后合并：git checkout master + git merge experiment:
<img width="461" alt="git_rebase_s2" src="https://user-images.githubusercontent.com/10185166/182366432-ab1ecd2f-9ab8-48ca-b051-da7cb4cab065.png">

* git rebase 是切换到experiment然后变基到master分支,完成后,切换回master再将两分支合并： git checkout experiment + git rebase master + git checkout master + git merge experiment:
<img width="462" alt="git_rebase_s3" src="https://user-images.githubusercontent.com/10185166/182366452-a979d065-ef75-437c-8805-d2969264fecd.png">
<img width="454" alt="git_rebase_s4" src="https://user-images.githubusercontent.com/10185166/182366466-c4c21d06-9aec-4323-b8ce-9c287cbdceaa.png">

* git rebase xxx，冲突不多，使用git rebase --continue， 冲突太多git rebase --abort 取消变基。

## git merge 常用指令：
* git rebase master
  * 将当前分支 与 本地 叫master分支的代码合并, 当前分支与master处在同一线上，当前分支的改动将在master分支的下一节点上；

* git rebase --abort
  * 如果当前分支 跟 待合并的分支有冲突， 可以使用该指令取消git rebase branchName指令；（不想取消且你有足够耐心：可使用git rebase --continue和git rebase --skip手动一步一步完成代码合并，当然没git merge branchName来的有效率）

* git rebase master newBranch
  * 将newBranch分支代码变基到master分支；相当于git checkout newBranch + git rebase master;

* git rebase -i
  * 编辑本地未push的commit（本人多用于合并commit）, 注意： 该指令需要 当前分支有 关联的 远程分支；
  将要合并的commit前面“pick”改成（vim模式输入“i”进入编辑状态）“s”就能将它合并到前一个commit去, 然后保存退出(esc退出编辑状态，然后”:"输入“wq”保存退出)。
  退出后进入下一个编辑窗口， 主要修改合并后新的注释， 同理 输入“i”进入编辑状态， 修改完esc退出编辑状态，然后”:"输入“wq”保存退出；

## 自动变基
* git config --global pull.rebase true
  * 首先，我们要搞清楚一点：什么时机是变基的时机？一般理解是推送的时候，其实不是，而是从拉取的时候就要开始变基了，因为你拉取的时候，服务器上可能已经有新代码了，所以要变基也是在这个时候，一旦发现有新基础了，则立马变掉。所以，通常情况下，我们拉取新代码无非就是一个命令：git pull，但现在我们要变基拉取，就需要用 git pull --rebase。但是每次这样执行命令就会很麻烦，而且你在vscode里也没有办法自动加这个参数，所以为了方便起见，我们就设置一下第一条命令，这样每次拉取它都会自动变基。

* git config --global rebase.autoStash true
  * 每次 rebase 的时候都自动把我们工作区里的内容自动 stash 进去，rebase 完成之后再自动恢复出来。

## 相关文章：
- [两条命令让你的git轻松自动变基，学到了！](https://maimai.cn/article/detail?fid=1681418899&efid=_toaAvswR0rIuyYD0iFDBg)
- [团队协作中的 Github flow 工作流程](https://zhuanlan.zhihu.com/p/39148914)