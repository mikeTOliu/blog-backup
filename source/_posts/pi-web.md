---
title: 树莓派利用微信控制gpio 点亮LED
date: 2019-04-20 23:10:47
tags: 技术 树莓派
reward: true
---
# 树莓派利用微信控制led灯 
最近在做一个自动解魔方的项目，颜色识别用的是树莓派+opencv，电机驱动用的arduino,（改天开个坑来写写2333）本来设计了几种功能通过按钮切换，我想既然有树莓派为啥要用物理按键，直接远程控制岂不是很炫酷（其实并没有什么卵用）。  一开始本来是想本地弄个局域网使用Bottle 弄个简单的web来实现，后来发现现在有很多现成的物联网平台而且api都是现成的，还可以公网访问，就随便选了一家，开搞。 

## 关于平台 
一开始是打算用yeelink，结果发现注册不上，就换了一家名为贝壳物联的平台（以下操作均以该平台为例） 
## 平台配置 
首先登陆
[贝壳物联](https://www.bigiot.net/)
的官网注册一个账号  

验证邮箱登陆之后点击自己的用户名进入下图所示的管理界面  

[![EPl88P.md.png](https://s2.ax1x.com/2019/04/20/EPl88P.md.png)](https://imgchr.com/i/EPl88P) 

然后点击智能设备中的设备列表，选择添加智能设备，进入下图所示界面，填写名称和简介完成后点击确定  

[![EPll4I.md.png](https://s2.ax1x.com/2019/04/20/EPll4I.md.png)](https://imgchr.com/i/EPll4I)
设备创建完成，如下图所示，你会获得一个设备ID和apikey  

[![EPl3Ct.md.png](https://s2.ax1x.com/2019/04/20/EPl3Ct.md.png)](https://imgchr.com/i/EPl3Ct)

## 服务端配置  

首先使用ssh连接你的树莓派，或者你也可以直接在树莓派上操作。 

**如果你的树莓未安装gpio库请先安装（一般都预装好了）** 

使用以下命令在当前目录建立一个(XXX.pyxxx随意)的文件  

`touch ./xxx.py` 

用nano打开它 

`nano ./xxx.py` 

输入并按注释修改以下代码 ： 

```python
#!/usr/bin/python3
import socket
import time
import json
import RPi.GPIO as gpio


#must be modified===
DEVICEID='***' #填入你的设备ID
APIKEY='***' #填入你的apikey
#modify end=========
#led = LED(17)
host="www.bigiot.net"
port=8181

#connect bigiot
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
s.settimeout(0)
while True:
	try:
		s.connect((host,port))
		break
	except:
		print('waiting for connect bigiot.net...')
		time.sleep(2)

#check in bigiot
checkinBytes=bytes('{\"M\":\"checkin\",\"ID\":\"'+DEVICEID+'\",\"K\":\"'+APIKEY+'\"}\n',encoding='utf8')
s.sendall(checkinBytes)

#keep online with bigiot function
data=b''
flag=1
t=time.time()
def keepOnline(t):
	if time.time()-t>40:
		s.sendall(b'{\"M\":\"status\"}\n')
		print('check status')
		return time.time()
	else:
		return t

#say something to other device function
def say(s,id,content):
	sayBytes=bytes('{\"M\":\"say\",\"ID\":\"'+id+'\",\"C\":\"'+content+'\"}\n',encoding='utf8')
	s.sendall(sayBytes)

#deal with message coming in
def process(msg,s,checkinBytes):
	msg=json.loads(msg)
	if msg['M'] == 'connected':
		s.sendall(checkinBytes)
	if msg['M'] == 'login':
		say(s,msg['ID'],'Welcome! Your public ID is '+msg['ID'])
	if msg['M'] == 'say':
		say(s,msg['ID'],'You have send to me:{'+msg['C']+'}')
		'''
		if msg['C'] == "play":
			led.on()
			say(s,msg['ID'],'LED turns on!')
		if msg['C'] == "stop":
			led.off()
			say(s,msg['ID'],'LED turns off!')
		'''
		if msg['C']=="rest": #C这个字符串内包含了你传入的信息，对其使用if做判断
			gpiocontrol(2)#对对应引脚进行能控制（BCM序列）
			print('rest')
			say(s,msg['ID'],'rest')#信息返回给服务器
		if msg['C']=="fast":
			gpiocontrol(3)
			print('fastmod')
			say(s,msg['ID'],'fastmod')
		if msg['C']=="study":
			gpiocontrol(4)
			print('study')
			say(s,msg['ID'],'step-forward')
	#for key in msg:
	#	print(key,msg[key])
	#print('msg',type(msg))


#初始化 gpio
gpio.setmode(gpio.BCM)#引脚编号采用BCM
gpio.setup(2,gpio.OUT)#定义GPIO为输出模式
gpio.setup(3,gpio.OUT)
gpio.setup(4,gpio.OUT)
#gpio控制函数
def gpiocontrol(pin):
	gpio.output(pin,gpio.HIGH)#对应gpio电平设为高
	time.sleep(1)#延迟1S
	gpio.output(pin,gpio.LOW)#对应gpio电平设为底
#main while
while True:
	try:
		d=s.recv(1)
		flag=True
	except:
		flag=False
		time.sleep(1)
		t = keepOnline(t)
	if flag:
		if d!=b'\n':
			data+=d
		else:
			msg=str(data,encoding='utf-8')
			process(msg,s,checkinBytes)
			print(msg)
			data=b''

```
确认无误后保存使用Python3在当前目录运行该程序，命令如下： 

`python3 ./xxx.py` 

## 控制端配置
### 微信公众号配置 
首先扫码关注贝壳物联的微信公众号  

![ ](https://www.bigiot.net/Public/images/weixin.png)

然后进入用户中心->个人信息 

点击微信下方，生成代码

将已生成的代码，用微信发送至此订阅号，即可完成微信绑定（注意：代码区分大小写，不可省略“+”号）。
### 微信小程序配置
首先扫码添加贝壳物联的小程序 

![ ](https://www.bigiot.net/Public/images/xcx_qrcode2.png) 

在小程序中登录你的账号

## 公众号与小程序使用说明 
### 公众号指令说明 
向公众号发送的指令会存储在以上程序中“C”这个字符串当中，在程序当中对“C”这个字符串进行判定即可执行相对应的函数(详情见注释) 

eg:在公众号发送rest，以上代码中`if msg['C']=="rest"`为真，执行其内部内容 
### 小程序自定义按钮说明 
输入按钮名字，指令填对公众号发送的指令即可 

## 结语 
虽然这只是一个很简单的程序，但只要你稍作修改就可以实现很多功能，控制家电，局域网唤醒电脑，或者执行你编写的Python程序或者shell脚本，而且这个平台还可以接入各大智能音箱，通过智能音箱对其进行控制。对于没有公网IP，又不愿意折腾内网穿透的朋友来说是一个挺好的解决方案。