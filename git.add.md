## git add命令详解
------------------------

### 一、前言

`git add`命令主要用于把我们要提交的文件的信息添加到索引库中。当我们使用`git commit`时，git将依据索引库中的内容来进行文件的提交。

### 二、基本

`git add <path>` 表示 `add to index only files created or modified and not those deleted `

Git通常是通过`git add` 的形式把<path>添加到索引库中，<path>可以是文件也可以是目录。git不仅能判断出<path>中，修改（不包括已删除）的文件，还能判断出新添的文件，并把它们的信息添加到索引库中。

### 三、git add -u

`git add -u` 表示 `add to index only files modified or deleted and not those created` 

`git add -u [<path>]`: 把<path>中所有tracked文件中被修改过或已删除文件的信息添加到索引库。它不会处理untracted的文件。省略<path>表示.,即当前目录。

### 四、git add -A

`git add -A: [<path>]`表示把<path>中所有tracked文件中被修改过或已删除文件和所有untracted的文件信息添加到索引库。省略<path>表示.,即当前目录。

### 五、git add -i

我们可以通过`git add -i [<path>]`命令查看中被所有修改过或已删除文件但没有提交的文件，并通过其`revert`子命令可以查看中所有untracted的文件，同时进入一个子命令系统。

#### 5.1、revert子命令

可以通过`git add -i`的`revert`子命令（`3: [r]evert`）把已经添加到索引库中的文件从索引库中剔除。

（`3: [r]evert`）表示通过3或r或revert加回车执行该命令。执行该命令后，git会例出索引库中的文件列表; 然后通过数字来选择。输入"1"表示git会例出索引库中的文件列表中的第1个文件。"1-15"表示git会例出索引库中的文件列表中的第1个文件到第15个文件.回车将执行。

如果我们不输入任何东西，直接回车，将结束revert子命令，返回`git add -i`的主命令行。

#### 5.2、update子命令

可以通过update子命令（`2: [u]pdate`）把已经tracked的文件添加到索引库中。其操作和revert子命令类似。

#### 5.3、add untracked子命令

通过`add untracked`子命令（`4: [a]dd untracked`）可以把还没被git管理的文件添加到索引库中。其操作和revert子命令类似。

#### 5.4、diff子命令

可以通过`diff`子命令（`6: [d]iff`）可以比较索引库中文件和原版本的差异。其操作和revert子命令类似。

#### 5.5、status子命令
`status`子命令(`1: [s]tatus`)功能上和`git add -i`相似

#### 5.6、quit子命令

`quit`子命令（`7: [q]uit`）用于退出`git add -i`命令系统

六、帮助
我们可以通过`git add -h`命令来看`git ad`d命令的帮助文档。

```
git add -h
usage: git add [options] [--] ...
    -n, --dry-run         dry run
    -v, --verbose         be verbose

    -i, --interactive     interactive picking
    -p, --patch           select hunks interactively
    -e, --edit            edit current diff and apply
    -f, --force           allow adding otherwise ignored files
    -u, --update          update tracked files
    -N, --intent-to-add   record only the fact that the path will be added later
    -A, --all             add changes from all tracked and untracked files
    --refresh             don't add, only refresh the index
    --ignore-errors       just skip files which cannot be added because of errors
    --ignore-missing      check if - even missing - files are ignored in dry run
```