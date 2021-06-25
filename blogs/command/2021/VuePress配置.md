---
title: VuePress配置
date: 2021-06-25
tags:
 - vuepress
categories:
 -  command
---

## 部署

```bash
yarn global add vuepress
yarn add vuepress-theme-reco
# 初始化
yarn global add @vuepress-reco/theme-cli
theme-cli init
# package.json  "dev"值修改为"vuepress dev ."
yarn dev
```

## 推送github page

> config.js       "dest"值修改为"dist"
>
> 如果配置域名后缀形式，添加“base”:”/appName/”

```bash
git add . 
git commit -m 'init'
git push
```

```deploy.sh
# 确保脚本抛出遇到的错误
set -e

# 生成静态文件
yarn build

# 进入生成的文件夹
cd .vuepress/dist

# 如果是发布到自定义域名
# echo 'www.example.com' > CNAME

git init
git add -A
git commit -m 'deploy'

# 如果发布到 https://<USERNAME>.github.io
# git push -f git@github.com:<USERNAME>/<USERNAME>.github.io.git master

# 如果发布到 https://<USERNAME>.github.io/<REPO>
# git push -f git@github.com:<USERNAME>/<REPO>.git master:gh-pages

git push -f https://github.com/zhangmc/zhangmc.github.io.git master

cd -

```

```.gitignore
node_modules/
yarn.lock
yarn.error
yarn-error.log
.vuepress/dist/*
package-lock.json
```

## Github Action

```bash
name: Deploy GitHub Pages

# 触发条件：在 push 到 master 分支后
on:
  push:
    branches:
      - main

# 任务
jobs:
  build-and-deploy:
    # 服务器环境：最新版 Ubuntu
    runs-on: ubuntu-latest
    steps:
      # 拉取代码
      - name: Checkout
        uses: actions/checkout@v2.3.1

      # 生成静态文件
      - name: Build
        run: |
          yarn add vuepress
          yarn build
      # 部署到 GitHub Pages
      - name: Deploy
        uses: JamesIves/github-pages-deploy-action@4.1.4
        with:
          ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
          BRANCH: gh-pages
          FOLDER: .vuepress/dist
```

