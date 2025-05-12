---
title: '使用githubPage+hexo搭建个人博客'
date: 2025-05-12 20:36:16
tags: 配置
author: whopxx
email: 2074447320@qq.com
---


### 常用命令
```bash
hexo init                      #初始化文件夹
hexo generate[g]               #生成静态页面至public目录
hexo server[s]                 #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy[d]                 #部署到GitHub
hexo new[n] "postName"         #新建文章
hexo new[n] page "pageName"    #新建页面
```

### 选择主题
1. 选一个主题并配置，具体操作根据READEME
[Themes](https://hexo.io/themes/)
2. 第一种方式：拉到hexo目录下的themes目录下
第二种方式：npm instll xxx（建议）
### 博客配置
1. 根据文档修改
2. 上传github
[在GitHub Pages上部署Hexo](https://hexo.io/zh-cn/docs/github-pages)
1. 配置
```bash
deploy:
  type: git
  repo: https://github.com/<username>/<project>
  # example, https://github.com/hexojs/hexojs.github.io
  branch: gh-pages
```
2. 执行 `hexo clean && hexo deploy`
3. 浏览 username.github.io，检查你的网站能否运作
### 编写文章
1. 创建文章
```bash
hexo new 使用githubPage+hexo搭建个人博客
```
2. 在source/_posts下找到创建的md文章进行修改
3. 编写完成后进行部署
```bash
hexo g
hexo d
```