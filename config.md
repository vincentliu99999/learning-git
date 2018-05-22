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