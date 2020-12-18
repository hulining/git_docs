---
title: git-branch 列出,创建或删除 Git 分支
---

Git 中的分支,其实本质上仅仅是个指向 commit 对象的可变指针.Git 会使用 master 作为分支的默认名字.在若干次提交后,你其实已经有了一个指向最后一次提交对象的 master 分支,它在每次提交的时候都会自动向前移动.

![分支就是从某个提交对象往回看的历史](https://ask.qcloudimg.com/http-save/yehe-4501745/fny729468c.png)

本地或远程仓库可以存在多个分支.Git 保存着一个名为 `HEAD` 的特别指针,指向当前所在的分支.可以使用 `git checkout` 命令切换到其它分支.

```bash
git branch [--color[=<when>] | --no-color] [--show-current]
    [-v [--abbrev=<length> | --no-abbrev]]
    [--column[=<options>] | --no-column] [--sort=<key>]
    [--merged [<commit>]] [--no-merged [<commit>]]
    [--contains [<commit>]] [--no-contains [<commit>]]
    [--points-at <object>] [--format=<format>]
    [(-r | --remotes) | (-a | --all)]
    [--list] [<pattern>…​]
git branch [--track | --no-track] [-f] <branchname> [<start-point>]
git branch (--set-upstream-to=<upstream> | -u <upstream>) [<branchname>]
git branch --unset-upstream [<branchname>]
git branch (-m | -M) [<oldbranch>] <newbranch>
git branch (-c | -C) [<oldbranch>] <newbranch>
git branch (-d | -D) [-r] <branchname>…​
git branch --edit-description [<branchname>]
```

`git branch` 默认列出本地分支,且 `HEAD` 指针指向的分支为绿色,相当于 `git branch --list --color` 命令.`git branch` 还包含众多命令行选项,已完成对本地或远程分支的管理.如下:

- `-d, --delete, -D <branchname>`

删除指定分支.如果删除当前 `HEAD` 指向的分支,会报错.`-D` 表示强制删除,相当于 `--delete --force`

- `-f, --force`

强制操作

- `-m, --move, -M [<oldbranch>] <newbranch>`

重命名分支.如果 `<oldbranch>` 被省略,则表示重命名当前分支.`-M` 表示强制删除,相当于 `--move --force`

- `-c, --copy, -C [<oldbranch>] <newbranch>`

复制分支.如果 `<oldbranch>` 被省略,则表示复制当前分支.`-C` 表示强制删除,相当于 `--copy --force`

- `--color[=<when>]`

特殊颜色显示 `HEAD` 指针指向的当前本地,远程跟踪的分支.可选值为 `always`(默认), `never`, `auto`.

- `--no-color`

不使用特殊颜色显示,相当于 `--color=never`

- `-i, --ignore-case`

排序和过滤分支时不区分大小写

- `-r, --remotes`

对远程跟踪分支进行操作,如列出或删除

- `-a, --all`

列出所有分支,本地和远程跟踪分支

- `--list [<pattern>…​]`

列出符合 `<pattern>` 模式匹配的本地分支.若 `<pattern>` 为空,则列出所有本地分支

- `-t, --track <branchname> [<start-point>]`

创建新分支 `<branchname>`,新创建的分支跟踪 `<start-point>`.`<start-point>` 可以为本地分支,也可以为远程分支.若 `<start-point>` 为空,则默认为当前分支

- `-u <upstream>, --set-upstream-to=<upstream> [<branchname>]`

设置 `<branchname>` 的上游分支为 `<upstream>`,即 `<branchname>` 跟踪 `<upstream>`

- `--unset-upstream [<branchname>]`

删除 `<branchname>` 的上游分支

- `--sort=<key>`

以指定 `<key>` 对分支进行排序.`<key>` 以 `-` 开头表示反向排序.排序字段详见 `git-for-each-ref`

- `--format=<format>`

按照指定格式输出
