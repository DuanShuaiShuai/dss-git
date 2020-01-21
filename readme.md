查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>或者git switch <name>

创建+切换分支：git checkout -b <name>或者git switch -c <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>

可以查看所有分支的所有操作记录: git reflog 
命令可以看到分支合并图：git log --graph
```javascript
git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除
另一种方式是用git stash pop，恢复的同时把stash内容也删了

你可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash，用命令：
git stash apply stash@{0}
```

cherry-pick:让我们能复制一个特定的提交到当前分支，避免重复劳动。

git branch -d <branch>: 删除一个已经合并的分支
git branch -D <branch>: 强制删除一个分支

查看远程库信息，使用git remote -v；

本地新建的分支如果不推送到远程，对其他人就是不可见的；

从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；

建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；

从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

git rebase :这就是rebase操作的特点：把分叉的提交历史“整理”成一条直线，看上去更直观。缺点是本地的分叉提交已经被修改过了。

命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id；

命令git tag -a <tagname> -m "blablabla..."可以指定标签信息；

命令git tag可以查看所有标签。
  
 
操作标签
阅读: 4282579
如果标签打错了，也可以删除：

$ git tag -d v0.1
Deleted tag 'v0.1' (was f15b0dd)
因为创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。

如果要推送某个标签到远程，使用命令git push origin <tagname>：

$ git push origin v1.0
Total 0 (delta 0), reused 0 (delta 0)
To github.com:michaelliao/learngit.git
 * [new tag]         v1.0 -> v1.0
或者，一次性推送全部尚未推送到远程的本地标签：

$ git push origin --tags
Total 0 (delta 0), reused 0 (delta 0)
To github.com:michaelliao/learngit.git
 * [new tag]         v0.9 -> v0.9
如果标签已经推送到远程，要删除远程标签就麻烦一点，先从本地删除：

$ git tag -d v0.9
Deleted tag 'v0.9' (was f52c633)
然后，从远程删除。删除命令也是push，但是格式如下：

$ git push origin :refs/tags/v0.9
To github.com:michaelliao/learngit.git
 - [deleted]         v0.9
要看看是否真的从远程库删除了标签，可以登陆GitHub查看。

命令git push origin <tagname>可以推送一个本地标签；

命令git push origin --tags可以推送全部未推送过的本地标签；

命令git tag -d <tagname>可以删除一个本地标签；

命令git push origin :refs/tags/<tagname>可以删除一个远程标签。


log
git log：如果你想了解本地仓库的历史记录，最简单的命令就是使用
git log --author=bob:你可以添加一些参数来修改他的输出，从而得到自己想要的结果。 只看某一个人的提交记录
git log --pretty=oneline:一个压缩后的每一条提交记录只占一行的输出
git log --graph --oneline --decorate --all:或者你想通过 ASCII 艺术的树形结构来展示所有的分支, 每个分支都标示了他的名字和标签
git log --name-status:看看哪些文件改变了
git log --help:这些只是你可以使用的参数中很小的一部分



revert

 git revert --no-commit f42955adb85
 git add  .
 git commit -m '***'
 git push 

 git revert --no-commit f7742cd..551c408
git commit -a -m 'This reverts commit 7e345c9 and 551c408'


cherry-pick

git cherry-pick ****
git add .  //如果有冲突就先解决冲突
git commit -m '...'
