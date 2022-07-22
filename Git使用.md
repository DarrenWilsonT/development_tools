# 配置用户名和邮件地址
``` bash
git config --local user.name <user.name>
git config --local user.email <user.email>
```
# **git**配置等级
使用多个git账户时，个人比较喜欢使用 `local`参数来进行**git**的的配置，每个仓库进行单独配置不会相互影响。
- `local`
  
  仓库级别，优先级最高，对应当前仓库下的`.git/config`。
  
- `global` 优先级次之。

- `system` 优先级最低。
# 初始化本地仓库
```bash
git init
```

执行此命令后会在本地创建 `.git` 文件。

# 添加管理文件

在此之前文件处于**unstaged**状态，执行`git add`后文件处于**staged**状态。

```bash
git add <filename>
```

# 提交改变

提交这次改变，并使用`-m`参数定义改变信息，要遵循**commit**规范填写相关信息。此后文件再次从**staged**状态回归**unstaged**状态。

``` bash
git commit -m <commit message>
```

# 流程图

[![2-1-1.png](https://i.postimg.cc/3NXn27b7/2-1-1.png)](https://postimg.cc/SYK6h0ht)

# 显示工作目录和暂存区状态

```bash
git status
```

# 查看日志

```bash
git log
git log --oneline #每个commit内容显示在一行
```

# 查看 unstaged

查看**unstaged**状态的文件与上个**commit**后的文件有什么不同

```bash
git diff
```

# 查看 staged

查看staged状态的文件与上个commit后的文件有什么不同

```bash
git diff --cached
```

# 查看全部修改

同时查看以上两个修改

```bash
git diff HEAD
```

# 修改已经commit的版本

将本次**add**内容合并到上次**commit**中不再创建一个新的**commit**记录，但会修改**commitId**

```bash
git commit --amend --no-edit  ## "--no-edit"：不编辑，直接合并到上一个commit
```

# reset 回到 add 之前

撤销本次 **add** 命令。

```bash
git reset <filename>
```

# reset 回到 commit 之前

每个 **commit** 都有自己的 **id**，**HEAD**是一个指针，指引当前的状态在哪一次**commit**。

```bash
git reset --hard HEAD  #强制回到最后一次commit
git reset --hard HEAD^^ #回到倒数第三个commit
git reset --hard HEAD~2 #结果同上一条命令
git reset --hard <commit id> #回到指定的commit
```

# 查看所有HEAD的改动

查看所有**HEAD**的改动，通过此方式可以使**HEAD**指针回到“未来”。

```bash
git reflog
```

# 回溯单个文件

不修改其他文件的前提下使单独的文件回到某次**commit**

```bash
git checkout <commit id> -- <filename>
```

# 查看分支结构

```bash
git log --oneline --graph
```

# 创建新的分支

```bash
git branch <branch name> #创建新的分支
git branch #查看当前所处分支
```

# 切换分支

```bash
git checkout <branch name>
```

# 创建并切换分支

```bash
git checkout -b <branch name>
```

# 合并分支

## merge

如果直接 `git merge dev`，**git** 会采用默认的 `Fast forward` 格式进行 `merge`，这样 `merge` 的这次操作不会有 `commit` 信息。 `log` 中也不会有分支的图案。 我们可以采取 `--no-ff` 这种方式保留 `merge` 的 `commit` 信息。

```bash
git merge <branch name> #将指定分支合并到当前分支
git merge --no-ff -m "merge info" <branch name> #将指定分支合并到当前分支，并保留merge信息。
```

## rebase

# 暂存修改

```bash
git stash   #暂存修改
git stash list #查看在stash中的缓存
git stash pip #h恢复暂存
```





[参考教程](https://link.juejin.cn/?target=https%3A%2F%2Fmofanpy.com%2Ftutorials%2Fothers%2Fgit%2F)
