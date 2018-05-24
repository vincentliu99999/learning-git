# Message Log

```sh
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