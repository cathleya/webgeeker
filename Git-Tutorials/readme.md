# Git配置 (别名 [alias)

https://www.kancloud.cn/kancloud/progit/70180


```sh
$ git cm "???"

$ git commit "???"
``` 



```
所有Git配置都保存在你的 .gitconfig 文件中。

Git命令自定义别名

别名用来帮助你定义自己的git命令。比如你可以定义 git a 来运行 git add --all 。

要添加一个别名， 一种方法是打开 ~/.gitconfig 文件并添加如下内容：

[alias]
  co = checkout
  cm = commit
  p = push
  # Show verbose output about tags, branches or remotes
  tags = tag -l
  branches = branch -a
  remotes = remote -v
...或者在命令行里键入：

$ git config --global alias.new_alias git_function
例如：

$ git config --global alias.cm commit
指向多个命令的别名可以用引号来定义：

$ git config --global alias.ac 'add -A . && commit'
下面列出了一些有用的别名：

别名 Alias	命令 Command	如何设置 What to Type
git cm	git commit	git config --global alias.cm commit
git co	git checkout	git config --global alias.co checkout
git ac	git add . -A git commit	git config --global alias.ac '!git add -A && git commit'
git st	git status -sb	git config --global alias.st 'status -sb'
git tags	git tag -l	git config --global alias.tags 'tag -l'
git branches	git branch -a	git config --global alias.branches 'branch -a'
git remotes	git remote -v	git config --global alias.remotes 'remote -v'
git lg	git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)%Creset' --abbrev-commit --	git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)%Creset' --abbrev-commit --"
自动更正

如果键入 git comit 你会看到如下输出：

$ git comit -m "Message"
# git: 'comit' is not a git command. See 'git --help'.

# Did you mean this?
#   commit
为了在键入 comit 调用 commit 命令，只需启用自动纠错功能：

$ git config --global help.autocorrect 1
现在你就会看到：

$ git comit -m "Message"
# WARNING: You called a Git command named 'comit', which does not exist.
# Continuing under the assumption that you meant 'commit'
# in 0.1 seconds automatically...
带颜色输出

要在你的Git命令输出里加上颜色的话，可以用如下命令：

$ git config --global color.ui 1
``` 





