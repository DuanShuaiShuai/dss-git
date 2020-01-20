查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>或者git switch <name>

创建+切换分支：git checkout -b <name>或者git switch -c <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>

可以查看所有分支的所有操作记录:git reflog 
命令可以看到分支合并图：git log --graph
git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除
另一种方式是用git stash pop，恢复的同时把stash内容也删了