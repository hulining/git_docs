---
title: git-add 添加文件到索引文件中
---

`git add` 命令将工作树中找到的内容来更新索引文件,用于下一次提交.

索引文件保存了工作树下文件的快照.在对工作树进行更改之后,在运行 `commit` 命令之前,必须使用 `add` 命令将所有新文件或已修改的文件快照添加到索引文件中.

`git status` 可用于获取哪些已修改的文件被添加到索引文件中,并在下一次提交时会被提交.

`git add` 默认不会添加被忽略的文件.如果指定了任何被忽略的文件,则 `git add` 将执行失败,并显示被忽略的文件的列表.可以将被忽略的文件添加到 `.gitignore` 文件中.`.gitignore` 文件支持 glob 匹配

```bash
git add [--verbose | -v] [--dry-run | -n] [--force | -f] [--interactive | -i] [--patch | -p]
      [--edit | -e] [--[no-]all | --[no-]ignore-removal | [--update | -u]]
      [--intent-to-add | -N] [--refresh] [--ignore-errors] [--ignore-missing] [--renormalize]
      [--chmod=(+|-)x] [--pathspec-from-file=<file> [--pathspec-file-nul]]
      [--] [<pathspec>…​]
```

`git add` 常用命令行选项如下:

- `-n, --dry-run`

实际不添加文件,仅显示它们是否存在或是否被忽略

- `-f, --force`

强制添加被忽略的文件

- `-i, --interactive`

交互式添加文件

- `--ignore-missing`

只能与 `--dry-run` 一起使用.用户可以检查是否会忽略任何给定的文件,无论它们是否已经存在于工作树中

- `--`

此选项可用于将命令行选项与文件列表分开,当文件名可能误认为命令行选项时很有用
