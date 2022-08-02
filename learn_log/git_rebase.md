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
