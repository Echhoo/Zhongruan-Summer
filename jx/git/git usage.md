# git 用法
> 目前世界上最先进的分布式版本控制系统\
> 能记录每次文件的改动

> 参考[廖雪峰git教程](https://www.liaoxuefeng.com/wiki/896043488029600)

## 安装git

### linux
```
$ sudo apt-get install git
```
### MacOS
1. homebrew
2. XCode集成
### Windows
[git官网下载](https://git-scm.com/downloads)

## 创建版本库
1. 创建
    ```
    $ git init
    ```
2. 添加文件到版本库
    ```
    $ git add <filepath(relative)>
    ```
    e.g.
    ```
    git add file1.md
    git add ./other\ files/file2.md
    git add . //常用，添加所有文件的更改到git库
    ```
3. 确认更改
    ```
    $ git commit //without annotation
    //在mac上git commit，会打开vi编辑器
    $ git commit -m "some annotation"
    ```

## 时光机穿梭
1. 查看工作区状态
    ```
    $ git status
    ```
    e.g.
    ```
    $ git status
    On branch master
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

    no changes added to commit (use "git add" and/or "git commit -a")
    ```
2. 查看修改内容
    ```
    $ git diff
    ```
    e.g.
    ```
    $ git diff readme.txt 
    diff --git a/readme.txt b/readme.txt
    index 46d49bf..9247db6 100644
    --- a/readme.txt
    +++ b/readme.txt
    @@ -1,2 +1,2 @@
    -Git is a version control system.
    +Git is a distributed version control system.
    Git is free software.
    ```

### 版本回退
1. 查看历史记录
    ```
    $ git log
    ```
    特殊语法
    ```
    $ git log --pretty=oneline //显示为一行
    ```
    e.g.
    ```
    $ git log --pretty=oneline
    1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master) append GPL
    e475afc93c209a690c39c13a46716e8fa000c366 add distributed
    eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0 wrote a readme file
    //<版本号> <commit注释>
    ```
2. 时光机操作！！！
   - 时光机飞飞飞！
       ```
       git reset --hard <版本>
       ```
       e.g.
       ```
       git reset --hard HEAD^ //返回HEAD的上个版本
       ```
       HEAD: 当前版本 \
       HEAD的上两个版本: HEAD^^ \
       HEAD的前100个版本: HEAAD~100

       回退到下个版本
       ```
       git reset --hard 1094a //1094a是版本号
       //在使用版本号时不需要全部写出，只需描写特定部位即可
       ```
   - 版本操作视图化
       ```
       HEAD---- 1094a
             |- e475a
             `- eaadf
       ```
       版本回退之后
       ```
           /- 1094a
       HEAD--|- e475a
           `- eaadf
       ```
   - 查询时光机的操作
       ```
       $ git reflog
       ```
       e.g. 
       ```
       $ git reflog
       e475afc HEAD@{1}: reset: moving to HEAD^
       1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
       e475afc HEAD@{3}: commit: add distributed
       eaadf4e HEAD@{4}: commit (initial): wrote a readme file
       ```
       从上述控制台给出的数据可以看出reset之前的commit id: 1094adb

### 工作区与暂存区
1. 工作区
   > 当前的操作目录
2. 暂存区
   ```
   git add <file> //将文件添加到暂存区
   git commit     //一次性把暂存区的所有修改提交到分支
   ```
   ![图片理解](../static/git/0.jpeg)

### 管理修改
每次修改，如果不用git add到暂存区，那就不会加入到commit中

### 撤销修改
```
$ git checkout -- <file>
```
让这个文件回到最近一次git commit或git add时的状态。

已经git add过，想要回退到上次或其他版本的文件
```
$ git reset <版本> <file>
$ git checkout -- <file>
```

### 删除文件
```
$ git rm <file>
```
从git版本库中移除某些文件

误删重置
```
$ git checkout -- <file>
```

## 远程仓库
### 添加远程仓库
1. 在github上新建一个repo
2. 链接本地仓库和远程仓库
    ```
    $ git remote add origin git@github.com:<username>/<reponame>.git
    ```
    第一次:
    ```
    $ git push -u origin master
    ```
    但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来

    以后:
    ```
    $ git push origin <本地分支>:<远程分支>
    ```

### 克隆远程库
```
$ git clone <远程库>
```

## 分支管理
### 创建与合并分支
- 创建分支
    ```
    $ git checkout -b <分支名>
    ```
    等同于
    ```
    $ git branch <分支名>
    $ git checkout <分支名>
    ```
- 合并分支
    ```
    git merge <分支名>
    ```
    用于合并指定分支到当前分支
    ```
    git branch -d <分支名>
    ```
    删除分支
- 切换分支
    ```
    git switch <branch>
    git switch -c <branch> //新建并切换分支
    ```

### 解决冲突
Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，我们修改如下后保存
```
$ git log --graph
```
查看分支图

### 分支策略
master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。
![分支图](../static/git/分支图.png)

合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并

### Bug分支
```
$ git stash
```
储存工作现场

切换到用于解决bug的分支，新建在它的基础上新建一个分支。在新分支上解决bug。解决之后合并分支

```
$ git stash list
```
查看储存的工作现场

- 恢复现场
    ```
    //不会删除stash内容
    $ git stash apply
    $ git stash apply stash@{0}
    //会删除stash内容
    $ git stash pop
    ```
- 删除stash内容
    ```
    $ git stash drop
    ```

升级版本
```
$ git cherry-pick <版本号>
```
只merge<版本号>中的修改内容

### feature分支

开发一个新feature，最好新建一个分支

如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除

### 多人协作
```
$ git remote -v
```
查看远程仓库的详细信息

```
$ git push <local>:<remote>
$ git fetch origin <branch>
$ git pull origin <branch>
```
一些常用的语句

```
$ git branch --set-upstream-to <branch-name> origin/<branch-name>
```
如果本地库和远程库没有建立关联，可以使用以上代码

```
$ git checkout -b branch-name origin/branch-name
```
创建分支时建立关联

### rebase
```
$ git rebase
```
把分叉的提交历史“整理”成一条直线，看上去更直观。缺点是本地的分叉提交已经被修改过了

## 标签管理
### 创建标签
```
$ git tag <name>
$ git tag <name> <commit id>
```

```
$ git show <tagname>
```
查看标签信息

```
$ git tag -a <tagname> -m "blablabla..."
```
指定标签信息

### 操作标签
```
$ git push origin <tagname>
```
推送一个本地标签

```
$ git push origin --tags
```
推送全部未推送的本地标签

```
$ git tag -d <tagname>
```
删除一个本地标签

```
$ git push origin :refs/tags/<tagname>
```
删除一个远程标签，注意refs/tags不可省略

## 自定义git
### 忽略文件
忽略某些文件时，需要编写.gitignore

### 定义别名
```
$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

### 搭建git服务器
> 目前没有大用处，先不看了

## 使用source tree
使用SourceTree可以以图形界面操作Git，省去了敲命令的过程，对于常用的提交、分支、推送等操作来说非常方便。

SourceTree使用Git命令执行操作，出错时，仍然需要阅读Git命令返回的错误信息。