---
title: Git命令
date: 2021-06-25
tags:
 - Git
categories:
 -  command
---

## 命令

```shell
vi ~/.gitconfig

git config --global credential.helper store

git config -l

git remote -v

git upstream -v

git branch -v

rm -r .git  #否则仓库中会有以前的提交信息等，windows执行erase .git

git init   

git add .

git commit -m "备注"

git remote add origin https://github.com/zhangmc/late.git
git remote set-url origin https://github.com/zhangmc/late.git

git remote add upstream https://github.com/zhangmc/late.git

git push -u origin master

#git bash命令中文乱码
git config --global core.quotepath false

npm config set registry https://registry.npm.taobao.org
配置后可通过下面方式来验证是否成功
npm config get registry

在 ~/.npmrc 加入下面内容，可以避免安装 node-sass 失败
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/

.npmrc 文件位于
win：C:\Users\[你的账户名称]\.npmrc
linux：直接使用 vi ~/.npmrc
```

```bash
git update-index --assume-unchanged "/root/tem/java/web/application-dev.yml" //git关闭跟踪文件修改提交
git update-index --no-assume-unchanged "/root/tem/java/web/application-dev.yml"//git打开跟踪文件修改提交

git update-index --assume-unchanged "/app/*.xml";//关闭跟踪app目录下后缀为.xml的文件
git update-index --assume-unchanged "/app/";//打开跟踪app目录下的所有文件

git update-index --skip-worktree "/app/tep/ap.txt"//关闭GIT跟踪本地文件修改
git update-index --no-skip-worktree "/app/tep/ap.txt"//打开GIT跟踪本地文件修改
```
