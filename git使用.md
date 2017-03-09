## git 命令

* 创建本地仓库

```
git init
```

* 创建远程仓库

```
// 添加一个新的 remote 远程仓库
git remote add [remote-name] [url]
例：git remote add origin https://github.com/you/yourpro.git
origin：相当于该远程仓库的别名
```

* 从本地仓库中删除

```
git rm file.txt         // 从版本库中移除，删除文件
git rm file.txt -cached // 从版本库中移除，不删除原始文件
git rm -r xxx           // 从版本库中删除指定文件夹
```

* 从本地仓库中添加新的文件

```
git add .               // 添加所有文件
git add file.txt        // 添加指定文件
```

* 提交，把缓存内容提交到 HEAD 里

```
git commit -m "注释"
```

* 把本地提交 push 到远程服务器

```
git push [remote-name] [loca-branch]:[remote-branch]
例：git push origin master:master
```

* 查看状态

```
git status
```

* 从远程库中下载新的改动

```
pull = fetch + merge

git pull [remote-name] [branch]
例：git pull origin master
```
