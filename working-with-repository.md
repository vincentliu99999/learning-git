# Working with repository

```sh
echo "hello, git" >  git-tutorial.txt # 新增檔案
git add git-tutorial.txt # 新增 git-tutorial.html  到 staging area
git add . # 新增所有異動到 staging area
git rm --cached git-tutorial.txt # 由 staging area 還原檔案
git commit -m "add git-tutorial.txt" # 提交至repository
```

## 修改記錄

```sh
git commit --amend # 修改最後一次的 commit message

# 合併修改記錄到最近一次的 commit
echo "console.log('hello, git');" > hello.js
vim hello.js
git add hello.js
git commit --amend -m "add git-tutorial.txt and hello.js"
git commit --amend --no-edit # message 同上一次
```

## 新增空目錄

因為 git 紀錄的是檔案內容差異，所以預設空目錄是無法 commit

```sh
mkdir upload_image
cd upload_image
touch .gitkeep
git add .
git commit -m "add upload image folder"
```

## 刪除檔案

```sh
git rm <file-name>
git rm <file-name> --cached
```

## 重新命名

```sh
git mv <file-name-old> <file-name-new>
```