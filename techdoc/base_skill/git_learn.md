



# git note 20210665 关于提交

[toc]

## 参考文档

- [How To Rebase and Update a Pull Request](https://www.digitalocean.com/community/tutorials/how-to-rebase-and-update-a-pull-request)
- [Git 工具 - 重写历史](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E9%87%8D%E5%86%99%E5%8E%86%E5%8F%B2#_git_amend)



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



## 修改最后一次提交

```shell
git commit --amend
```

如果你并不想编辑 message, 那么可以使用如下命令

```shell
git commit --amend --no-edit
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

### 如何使用 git rebase 拆分提交

拆分一个提交会撤销这个提交，然后多次地部分暂存与提交直到完成所需次数的提交。
常见的 case 发生在我们把两个不同属性的更改操作放在一个 commit 中， 而我们更希望将其拆成两个 commit, 如此还能创建分支提两个 PR

假设在某次提交中将两个文件放在同一个提交里，那么可以将要拆分的提交的指令修改为 `edit`

```
pick f7f3f6d changed my name a bit
edit 310154e add file1 and file2
pick a5f4a0d added cat-file
```

使用如下命令进行操作：

```shell
$ git reset HEAD^
$ git add file1
$ git commit -m 'add file1'
$ git add file2
$ git commit -m 'add file2'
$ git rebase --continue
```

该操作会撤销 id 310154e 的提交，将修改的文件取消暂存

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

## todo-read

- [核武器级选项：filter-branch](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E9%87%8D%E5%86%99%E5%8E%86%E5%8F%B2#_git_amend)
- 如何查看某次提交的改动

