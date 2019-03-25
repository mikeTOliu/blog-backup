---
title: 用github + hexo 创建你的个人博客(二) 进阶篇
date: 2019-03-26 00:05:35
tags: 技术
reward: true
---
# 用github + hexo 创建你的个人博客(二) 进阶篇
## 1.使用主题  
博客已经搭建完成，不过样子是不是不太满意？别急，让我们给hexo添加主题。  
**以下以yilia主题为例[yilia主题github地址](https://github.com/litten/hexo-theme-yilia)
若使用其他主题请参照其帮助文档**  
### 1.下载yilia主题  
切换到博客目录，在目录下执行以下命令  
`git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia`  
### 2.修改博客配置文件 _config.yml  
在该文件中找到以下代码
```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```
改为  
```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: yilia
```  
**以下命令均在博客目录执行**  
清除原有生成  
`hexo clean`  
重新生成  
`jexo g`  
发布博客  
`hexo g`  
进入你的博客，是不是感觉焕然一新？
## 2.主题配置（yilia）  
主题设置好了是不是感觉少了些什么？别急接下来让我们对主题进行配置  
在theme 文件夹找到 _config.yml文件 按照里面的注释来对你的信息进行补全，若不需要该项则在
该项前加以#来注释。    

该主题的侧边栏需要安装插件来实现，请按作者在侧边栏中的描述来安装。  
如有疑问可以参照我的[博客备份](https://github.com/mikeTOliu/blog-backup)
## 3.发布文章  
  主题配置完成，是时候来写你的第一篇博客了  
  在博客目录当中使用以下命令生成博文  
  `hexo new "XXX"`(XXX为你的博文名字)  
  进入博客目录下的source/_posts文件夹可以看见一个名为XXX.md的文件（XXX为你的博文名）  
  用vscode或者其他支持Markdown的编辑器来对博文进行编辑，有关markdown的语法改天再聊一聊  

## 4.使用私有域名  
使用github默认的域名不够高大上？下面让我们来配置属于你自己的专属域名。  
首先你需要去申请一个域名并对域名进行解析，腾讯云，阿里云都行，国内域名需要备案所以我使用的是一个国外的网站叫做[GoDaddy](https://sg.godaddy.com)  
  

在搜索框中输入你想要购买的域名   

[![ANpS5d.md.png](https://s2.ax1x.com/2019/03/25/ANpS5d.md.png)](https://imgchr.com/i/ANpS5d) 

选择一个你想要注册的域名，不同域名价格不一样  

[![ANSo59.md.png](https://s2.ax1x.com/2019/03/25/ANSo59.md.png)](https://imgchr.com/i/ANSo59)  

在购物车中取消安全服务（土豪随意）  

[![ANpixP.md.png](https://s2.ax1x.com/2019/03/25/ANpixP.md.png)](https://imgchr.com/i/ANpixP)  

买单（支持支付宝）   

[![ANpAr8.md.png](https://s2.ax1x.com/2019/03/25/ANpAr8.md.png)](https://imgchr.com/i/ANpAr8)  

有了域名我们还要对域名进行解析  
我使用的是一个名为[clooudflare](https://www.cloudflare.com/)的域名解析服务   

注册账号，登录后点击以下按钮添加你的域名  
![ANpdR1.png](https://s2.ax1x.com/2019/03/25/ANpdR1.png)  
  

填入你的域名  
[![ANprqO.png](https://s2.ax1x.com/2019/03/25/ANprqO.png)](https://imgchr.com/i/ANprqO)  

选择DNS设置  
  
  [![ANp2id.png](https://s2.ax1x.com/2019/03/25/ANp2id.png)](https://imgchr.com/i/ANp2id)  

在按以下图片中的内容配置你需要解析的IP地址  
  
  [![ANp4QP.md.png](https://s2.ax1x.com/2019/03/25/ANp4QP.md.png)](https://imgchr.com/i/ANp4QP)  
**A项之中填入你刚刚ping出来的ip**   
**www项之中填入你博客的原地址**  
cloudflare 选项中按下图填入  
[![ANpqij.md.png](https://s2.ax1x.com/2019/03/25/ANpqij.md.png)](https://imgchr.com/i/ANpqij)  
访问你刚刚购买的域名，诶怎么还是打不开，别急我们还需要对博客进行配置  
在博客目录下的source文件夹中建立一个名为CNAME的文件并在当中输入你
刚刚购买的域名（不需要http://）保存 然后用`hexo g`生成`hexo d`提交  
再在浏览器中打开刚刚购买的域名，是不是可以访问了，把它推荐给你的朋友吧。


