# Working with repository Meow

```sh
git reset HEAD <file-name> # unstaged 檔案
git reset --soft ba9be6e # 回到某個版本，之後的異動都保留
git reset --hard ba9be6e # 回到某個版本，之後的異動都清除
git clean -f # 清除 untracked 檔案
git clean -df # 清除 untracked 目錄
git checkout <file-name> # 復原不小心刪除的檔案
git checkout . # 不小心刪除太多檔案
```