# Message Log

```sh
# log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset %ai %ci'
git log
git log --graph --oneline
git log --oneline --grep="git" # 過濾 message
git log -S "repo" # 過濾 commit 的檔案
git log --oneline --author="vincent" # vincent commit 過哪些東西
git log --oneline --since="9am" --until="18pm" # 上班時間的 commit
git log --oneline --since="9am" --until="23pm" --after="2018-05-23" # 2018-05-23開始，上班時間的 commit
git log -p <file-name> # 看單一檔案的log
git blame <file-name> # 檢視每一行程式碼的紀錄
git show <object> # 檢視更動的內容
```

## pretty-format

- '%H': commit hash
- '%h': abbreviated commit hash
- '%d': ref names, like the --decorate option of git-log[1]
- '%D': ref names without the " (", ")" wrapping.
- %s': subject，基本上就是 commit message
- '%B': raw body (unwrapped subject and body)

- %Cred': 把字換成紅色
- %Cgreen': 把字換成綠色
- %Cblue': 把字換成藍色
- %Creset': 重設顏色

```sh
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
git log --graph --pretty=format:'%Cred%H%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%D%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
git log --graph --pretty=format:'%Cred%h%Creset'
git log --graph --pretty=format:'-%C(yellow)'
git log --graph --pretty=format:'%d%Creset'
git log --graph --pretty=format:'%s '
git log --graph --pretty=format:'%Cblueby %an'
git log --graph --pretty=format:'%Cgreen(%cr)'

git log --pretty=format:'%h %<(20)%an %s' -10

git log --graph --pretty=format:'%Cred%h%Creset %Cblue%<(20)%an %Cgreen(%cr)%Creset -%C(yellow)%d%Creset %s '
git log --graph --pretty=format:'%Cred%h%Creset %Cblue%<(15)%an %Cgreen%<(15)%cr%Creset %s %C(yellow)%d%Creset'
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset'
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(dim white)<%an>%Creset'

# 試顏色
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(magenta)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci' # like
git log --graph --pretty=format:'%C(dim magenta)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(ul magenta)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(blink magenta)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(reverse magenta)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(reverse ul cyan)%h%Creset -%C(yellow)%d%Creset %C(ul)%s%Creset %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci' # like
git log --graph --pretty=format:'%C(strike magenta)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(cyan)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(white)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'
git log --graph --pretty=format:'%C(yellow)%h%Creset -%C(yellow)%d%Creset %s %C(dim white)<%an>%Creset %Cgreen(%cr)%Creset %ci'

# 查作者
git log --pretty=format:"%ad " --date=short --author=vincent | sort -u | awk '{print $1,a++}'

# https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs

git log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
git log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all

git log --graph --pretty=tformat:"%C(yellow)%h%Creset}%Cgreen(%ar)%Creset}%C(bold blue)<%an>%Creset}%C(bold red)%d%Creset %s" -100|  column -s '}'

git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative
git shortlog --format='%H|%cn|%s' | grep 'git'
git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short
```

```sh
#查看当前目录每个文件的最后提交者。
git ls-tree -r --name-only HEAD | while read filename; do
  echo "$(git log -1 --format="%an %ae" -- $filename) $filename"
done
```