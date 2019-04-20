---
title: 用github + hexo 创建你的个人博客 初级篇
date: 2019-03-23 22:30:09
tags: 技术
reward: true
---
# 用github + hexo 创建你的个人博客(一) <br>初级篇
　　花了几天时间，搭建了一个基于hexo的个人博客，网上教程很多但不一定都全，我就基于我这次踩的一些坑写一篇教程，第一次写，如有缺陷请各位多多包涵。
## 1.申请github帐号　　
&nbsp;&nbsp;github地址 [github](https://github.com/)　<br/>
1.在github上建立一个新账号,并点击以下按钮<br/><br/>
[![AJ26f0.png](https://s2.ax1x.com/2019/03/23/AJ26f0.png)](https://imgchr.com/i/AJ26f0)<br/>
2.如图所示建立一个名为xxx.github.io的版本库<br><br>
[![AJ2hm4.md.png](https://s2.ax1x.com/2019/03/23/AJ2hm4.md.png)](https://imgchr.com/i/AJ2hm4)<br/>
## 2.安装HEXO
我使用的是arch,如果是ubuntu请用apt-get install<br/>
安装node.js<br/>
`sudo pacman -S nodejs`<br/>
安装npm<br/>
`yaourt -S npm`<br/>
安装git<br/>
`yaourt -S git`<br/>
安装 Hexo<br/>
`npm install -g hexo-cli`<br/>
然后建立你的博客目录<br/>
```
cd ~
mkdir ./blog
hexo init
```
以上命令将完成博客的初始化,接下来安装插件使hexo支持git<br/>
**(该命令需在博客目录下运行)**<br>
`npm install hexo-deployer-git --save`<br>
下面在本地生成你的第一个博客吧<br>
```
#生成博客
hexo g
#运行博客
hexo s
```
打开以下网址可以看到运行的的博客页面<br/>
`http://localhost:4000/`<br>
## 3.ssh公钥的配置
先进入~/.ssh文件夹,没有的话用以下命令创建<br>
`mkdir ~/.ssh`<br>
用以下命令生成ras秘钥<br>
`ssh-keygen -t rsa`
用以下命令打开并复制秘钥<br>
`vi ~/.ssh/scp id_ras.pub`<br>
打开你的github的设置,选择以下选项<br>
[![AJfkwQ.th.png](https://s2.ax1x.com/2019/03/24/AJfkwQ.th.png)](https://imgchr.com/i/AJfkwQ)<br>
在以下窗口的key选项里填入刚刚复制的秘钥,标题随便填<br>

[![AJfa6K.png](https://s2.ax1x.com/2019/03/24/AJfa6K.png)](https://imgchr.com/i/AJfa6K)<br>

输入ssh -T git@github.com，测试添加ssh是否成功。如果看到Hi后面是你的用户名，就说明成功了(**命令里的邮箱别改**)<br>

![AJf21P.png](https://s2.ax1x.com/2019/03/24/AJf21P.png)<br>
## 4.上传博客到github
修改博客目录下的_config.yml,修改以下字段<br>
**XXX为你github用户名**
```
deploy:
  type: git
  repository: git@github.com:XXX/XXX.github.io
  branch: master
```
**!! 以下命令均在博客目录下执行**
删除原有构建<br>
`hexo clean`<br>
重新构建<br>
`hexo g`<br>
发布博客<br>
`hexo d`<br>
***如果不出意外的话,恭喜你你的博客搭建成功啦!!!***<br>
打开(XXX为你的用户名)`http://XXX.github.io`就可以看到你的博客页面<br>


