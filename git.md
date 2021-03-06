---
title: Git 分布式版本控制工具
---

## Git 简介

Git 是一个快速,可扩展的分布式修订版本控制系统.

与其它版本控制软件相比,Git 有如下优势:

- 直接记录快照，而非差异比较

Git 与其它版本控制系统的主要差别在于 Git 只关心文件数据的整体是否发生变化.Git 更像是把变化的文件作快照后,记录在一个微型的文件系统中.每次提交更新时,它会浏览一遍所有文件的指纹信息并对文件作一快照,然后保存一个指向这次快照的索引.为提高性能,若文件没有变化,Git 不会再次保存,而只对上次保存的快照作一链接.

![Git 保存每次更新时的文件快照](https://gitee.com/progit/figures/18333fig0105-tn.png)

- 近乎所有操作都是本地执行

在 Git 中的绝大多数操作都只需要访问本地文件和资源,不用联网.Git 在本地磁盘上就保存着所有当前项目的历史更新,处理起来速度飞快.

- 时刻保持数据完整性

保存到 Git 之前,所有数据都要进行内容的校验和(checksum)计算,并将此结果作为数据的唯一标识和索引.

## 文件的三种状态

在 Git 内部,对于任何一个文件只有三种状态:

- 已提交(committed): 表示文件已被安全的保存在本地数据库中了.
- 已修改(modified): 表示修改了某个文件,但还没有提交保存.
- 已缓存(staged): 表示把已修改的文件放在下次要提交时保存的清单中.

![工作目录,暂存区域以及本地仓库](https://gitee.com/progit/figures/18333fig0106-tn.png)

每个项目都有一个 Git 目录(`git clone` 是 `.git` 目录,`git clone --bare` 是当前目录),它是 Git 用来保存元数据和对象数据库的地方.

从项目中取出某个版本的所有文件和目录,用以开始后续工作的叫做工作目录.

所谓的暂存区域只不过是个简单的文件,一般都放在 Git 目录中.这个文件也叫索引文件(index)

基本的 Git 工作流程如下:

1. 在工作目录中修改某些文件
2. 对修改后的文件进行快照,然后保存到暂存区域
3. 提交更新,将保存在暂存区域的文件快照永久转储到 Git 目录中

## git 命令

git 包含众多子命令和命令行选项.

```bash
git [--version] [--help] [-C <path>] [-c <name>=<value>]
    [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
    [-p|--paginate|-P|--no-pager] [--no-replace-objects] [--bare]
    [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
    [--super-prefix=<path>]
    <command> [<args>]
```

下面介绍一些常用的命令行选项

- `-C <path>`

在 `<path>` 中执行 git 命令,而不是在当前目录.

- `-c <name>=<value>`

向命令传入配置参数

- `-p, --paginate`

用管道的方式将命令的输出内容输出到 `less` (可使用 `$PAGER` 变量设置)

- `--git-dir=<path>`

将 `<path>` 设置为 git 的存储库(`.git` 目录).也可以通过 `GIT_DIR` 环境变量来设置.

- `--work-tree=<path>`

设置 `<path>` 目录为工作目录.也可以通过 `GIT_WORK_TREE` 环境变量来设置.

- `--bare`

将本地目录作为初始化的存储库.会在当前目录下生成 `.git` 目录下的文件.
