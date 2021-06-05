



# git note 20210665

[toc]

## 参考文档

- [How To Rebase and Update a Pull Request](https://www.digitalocean.com/community/tutorials/how-to-rebase-and-update-a-pull-request)



## setting up git 

```shell
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"
```

添加远程节点

```shell
git remove -v
git remote add upstream https://github.com/original-owner-username/original-repository.git
```

## git rebase

Git rebase 可以用于编辑先前提交的 commit 的 message, 或者合并数个 commit 以及删除、回滚等

### **如何使用 git rebase 处理多次提交**

```shell
git rebase -i HEAD~x #  x指代你要修改的最近哪几次提交
git rebase -i <commit-id>

```

如果你已经不记得你在这个分支的哪个节点开始提交的修改，可以通过下面的命令找到基本节点, 它会返回这个基础节点提交的 hash

```shell
git merge-base new-branch master
```

使用 `git reword` 可用于编辑历史 commit 的 message, 区别于 `git commit --amend` 只能对上一个提交的 message 做修改



### **如何使用 git rebase 进行合并分支**

```shell
cd repository
git fetch upstream
git rebase upstream/master
```
当与目标分支合并时发生冲突，此时需要解决冲突：
```
1. 修改发生冲突的文件
2. git add (无需git commit)
3. git rebase --continue
```



