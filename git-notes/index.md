# Git learning notes

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
[Git](https://git-scm.com/)
<!--more-->
# Install
- Identity
```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
- check status
`git status`
# Repositories
![](https://user-gold-cdn.xitu.io/2019/6/28/16b9d385970c7b6c?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
- Initializing a Repository in an Existing Directory
`$ git init`
- Add files to stage
`git add .`means add all files to stage
`git add ./xxx/` add files one by one
- Add files from stage to repositories
`git commit -m "xxx"` add all files to repositories
- Connect local repositories and internet repositories
`git remote add origin https://github.com/name/name_cangku.git`
- push form local repositories to internet repositories
`git push -u origin master`
![lifecycle of status](https://git-scm.com/figures/18333fig0201-tn.png)
# Go back and go future
```
git log

git log --pretty=oneline
```

view commit history

`git reset --hard + 版本号` go any version
# 撤销
- 场景1：在工作区时，你修改了一个东西，你想撤销修改， `git checkout -- file`。廖雪峰老师指出撤销修改就回到和版本库一模一样的状态，即用版本库里的版本替换工作区的版本。
- 场景2：你修改了一个内容，并且已经git add到暂存区了。想撤销怎么办？回溯版本，`git reset --hard + 版本号`,再`git checkout -- file`,替换工作区的版本。
- 场景3：你修改了一个内容，并且已经git commit到了master。跟场景2一样，版本回溯，再进行撤销。

# Branch
## Create new branch and merge
![](https://user-gold-cdn.xitu.io/2019/6/28/16b9e012079c4724?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
when there is only master branch, you `git push -u origin master` every time, there will add a new time line, and master will move to new version
![](https://user-gold-cdn.xitu.io/2019/6/28/16b9e11b1115072b?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
- Creat a other branch, and move to new branch
```
git branch other
git checkout other
```
- Check current Branch
`git branch`
- commit with other
`git add ./xxx/`
`git commit -m "xxx"`

- move to master
`git checkout master`
- merge branch 
`git merge other`
- delete other branch
`git branch -d other`
## Deal with merge program
![](https://user-gold-cdn.xitu.io/2019/6/29/16ba102bd434afc6?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

假如有这样一种情况，分支other已经commit了，但是此时指针指回master时，并且master没有合并，而是git add / commit 提交了。这样，就产生了冲突，主分支master文件内容与other分支的内容不一样。合并不起来！
- 修改文件的内容，让其保持一致。
- git add git commit 提交。
- 分支合并

- `git log --graph` 查看分支合并图
- `git branch -d other` 删除分支，任务结束。

# Reference
[你喜欢吃辣椒吗](https://juejin.im/post/5d157bf3f265da1bcc1954e6)
[Git](https://git-scm.com/book/en)







