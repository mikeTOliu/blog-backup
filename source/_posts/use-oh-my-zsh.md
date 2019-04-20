---
title:  zsh+oh-my-zsh 提高shell效率的神器
date: 2019-04-14 09:32:04
tags: 技术 
reward: true
---
# zsh+oh-my-zsh 提高shell效率的神器
当你每次使用shell命令行的时候，有没有感觉自动补全不是那么智能？有没有感觉每次切换路径时自己手敲目录名称很麻烦？有没有感觉自带shell的主题太丑影响心情？如果你被以上问题所困扰又或者你比较懒，那么不妨试试zsh这款提高shell效率的神器 
## 安装zsh 
使用你系统自带的包管理器安装zsh(本文档一ubuntu为例)  

`sudo apt-get install zsh` 

## 把zsh设置为默认shell 
执行以下语句（别用sudo） 

`chsh -s /bin/zsh`  
>注销，然后重新打开终端，你会发现shell已经变成了zsh,但是怎么感觉和原来差不多？别急接下来我们安装oh-my-zsh使我们的zsh支持插件和主题。

## 安装 oh-my-zsh 
oh-my-zsh 是github上的一个开源项目
[项目地址](https://github.com/robbyrussell/oh-my-zsh/)，开源大发好，既然是github上的我们首先得安装git 

`sudo apt-get install git`  
 
 然后我们就可以安装oh-my-zsh了 
  
  `sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"` 
## 主题配置
安装完毕，下面我们对oh-my-zsh进行配置  
首先用文本编辑器打开oh-my-zsh的配置文件 

`nano ~/.zshrc`  


[![AOQeJA.th.png](https://s2.ax1x.com/2019/04/14/AOQeJA.th.png)](https://imgchr.com/i/AOQeJA)  
 
 找到以下黑体字语句(引号内的内容不相同)，填入你的主题名字，各种主题可以在
 [这里](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)查看  

 我用的是一个名为agnoster的主题，效果如下： 
  
  [![AOQtWn.md.png](https://s2.ax1x.com/2019/04/14/AOQtWn.md.png)](https://imgchr.com/i/AOQtWn) 
   
如需使用该主题则直接在引号内填入angoster 如需使用其他主题则填入对应名称。 
 
 如果使用angoster主题则需用以下命令安装powerline font 否则在某些地方字体会乱码。 

 `sudo apt-get install fonts-powerline` 
  
  重新打开你的终端，嗯是不是漂亮多了？ 
  ## 插件配置 
  漂亮还不够我们还需要生产力，那么，下面就轮到插件出场了。 下面我推荐几个我常用的插件，记住，别装太多插件插件越多越卡。

  ### autodump
   每次输路径很麻烦？autodump这款插件可以大大提高你输入路径的效率  

   安装  
   `sudo apt-get install autojump`  
   重启终端cd一下摁两下tab就能进入以下界面  

   [![AOlvg1.md.png](https://s2.ax1x.com/2019/04/14/AOlvg1.md.png)](https://imgchr.com/i/AOlvg1)  

   接下来你就可以用上下左右选择你需要的目录或文件，回车之后会自动补全在命令后  
    
###  zsh-autosuggestions 
觉得自带的自动补全不够智能？别怕 zsh-autosuggestions这款插件可以让你的自动补全更高效。
 
安装  zsh-autosuggestions  

`git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
`

编辑配置文件  

打开配置文件

`nano ~/.zshrc` 

找到黑体字部分  

[![AO3ITU.md.png](https://s2.ax1x.com/2019/04/14/AO3ITU.md.png)](https://imgchr.com/i/AO3ITU) 
 
 如图在括号里添加  zsh-autosuggestions 
  
重启终端，试试新的自动补全吧。




