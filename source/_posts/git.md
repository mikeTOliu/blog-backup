---
title: github 提交流程
date: 2019-08-04 07:06:11
tags: 技术
reward: true
---
# github 提交流程 
1.在github上建立你的git仓库

2.在对应位置打开你的命令行（win：shift+鼠标右键）

3.使用clong命令把仓库克隆到本地 

`git clone https://*****`  

3.修改或增加你的代码

4.设置更改 

`git add 文件名`  

如需提交所有已更改文件 

`git add .` 

5.将更改提交到缓存  

` git commit -m '提交信息'` 

6.提交更改 

`git push`

**PS:若不是第一次提交，每次提交前使用**`git pull`**更新一下本地仓库以防出现错误**