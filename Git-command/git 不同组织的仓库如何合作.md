## 修改别人的库的代码

+ fork 一份到自己的github 仓库

+ 从自己的库中`git clone` 一份代码到自己的local

```
git clone xx.git
```

+ 建分支修改代码

+ push 代码到自己的仓库

\+ 向别人的库发 pull request

## 同步代码

当别人的库代码更新后，如何同步更新自己的库？

+ `git remote -v` 来查看本地有哪些代码源

+ 添加别人库的源,`consumer` 是自己随便起的别名

```
git remote add cusumer xx.git
```

+ 用`git pull --reb cusumer master` 从别人的库中pull下master分支的最新代码

+ 现在自己的local 是最新的代码，需要`git push origin master`,将最近的代码更新到自己的远程仓库

