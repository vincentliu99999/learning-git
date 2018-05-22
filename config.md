# 環境設定

有訂好名字和 email 才能 commit

```sh
git config --global user.name "Vincent Liu"
git config --global user.email "vincentliu@abcde.com"
```

設定顏色

```sh
git config --global color.diff auto
git config --global color.status auto
git config --global color.branch auto
git config --global color.log auto
```

查看設定

```sh
git config --list
```

## 設定方式

1. 透過指令 `git config`
1. 直接修改 `~/.gitconfig`

```log
[user]
    name = Vincent Liu
    email = vincentliu@abcde.com
[core]
    editor = vim
    ignorecase = false
[push]
    default = simple
[color]
    diff = auto
    status = auto
    branch = auto
    log = auto
[alias]
    lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'
```

## 別名

當你熟練或懶惰時的好朋友

```sh
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.aa add --all
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cblueby %an %Cgreen(%cr)%Creset'"
```