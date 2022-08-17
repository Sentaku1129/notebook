# Git分支管理

![Git_branch](D:/code/../../../images/Git/git-brance.png)

> 使用分支意味着我们进行开发时能够进行不同的版本管理，可以将一个项目从主线中分离出来，然后再不影响主线的同时进行多重开发

>
## 创建分支命令

    git branch (branch_name)

>> 不添加参数:列出分支

    $ git branch test
    $ git branch
    * master
      test

## 切换分支命令

    git checkout (branch_name)


## 合并分支命令

    git merge

## 删除分支

    git branch -d (branch_name)

例如我们要删除test分支

    $ git branch
    * master
      test
    $ git branch -d test
    Deleted branch testing (was )
    $ git branch
    * master