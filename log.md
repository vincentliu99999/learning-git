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
- %s': subject

- %Cred': 把字換成紅色
- %Cgreen': 把字換成綠色
- %Cblue': 把字換成藍色
- %Creset': 重設顏色

git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
git log --graph --pretty=format:'%Cred%H%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%D%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
git log --graph --pretty=format:'%Cred%h%Creset'
git log --graph --pretty=format:'-%C(yellow)'
git log --graph --pretty=format:'%d%Creset'
git log --graph --pretty=format:'%s '
git log --graph --pretty=format:'%Cblueby %an'
git log --graph --pretty=format:'%Cgreen(%cr)'