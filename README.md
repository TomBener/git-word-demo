# git-word-demo

### 安装 Git 与 Pandoc

- 前往 [Git 官网](https://git-scm.com/downloads)，选择对应的操作系统版本，下载安装 Git。
- 前往 [Pandoc 官网](https://pandoc.org/installing.html)，下载安装对应系统版本的 Pandoc。

如果你的操作系统是 macOS，推荐使用 [Homebrew](https://brew.sh) 来安装 Git 和 Pandoc：

```bash
brew install git pandoc
```

### 配置 Git

在用户文件夹下找到文件 `.gitconfig`，使用文本编辑器打开它，加入下面的内容，然后保存。

```bash
[diff "pandoc"]
   textconv=pandoc --to=markdown
   prompt = false
 [alias]
   wdiff = diff --word-diff=color --unified=1
```

新建一个文件夹，这里命名为 `git-word-demo`。

初始化 Git 仓库

```bash
# 进入 git-word-demo 文件夹
cd git-word-demo

# 创建 Git 仓库
git initial
```

在 `git-word-demo` 目录下，新建一个文件 `.gitattributes`，写入下面的内容，然后保存。

```bash
*.docx diff=pandoc
```

### 编辑 Word 文件

在 `git-word-demo` 文件夹下，新建一个 Word 文件，这里命名为 `example.docx`，然后按照平常一样进行编辑，完成之后保存并提交，进入该目录，在终端中输入：

```bash
git wdiff example.docx
```

就可以像纯文本一样，看到增加或删除的内容。当然，使用 Git 的 GUI 客户端会更加直观，比如 [GitHub Desktop](https://desktop.github.com)，如下图所示，绿色表示增加的部分，红色表示减少的部分。

![](https://cdn.jsdelivr.net/gh/TomBener/image-hosting/images/git-diff-github-desktop.png)