---
title: 常用Markdown语法
date: 2019-04-13 12:34:21
tags: 技术 
reward: true
---
#  常用Markdown语法

Markdown是一种简单易用的富文本标记语言，语法简单，上手快，排版优秀，而且对代码和数学公式和代码的兼容性很好，很适合写个人博客或者一些技术文档，让我们一起来学习一下吧。 
 
  
> **在学习之前请大家务必记住在使用符号标记语句时务必在符号后加上空格,且符号均为英文符号！！！**
## 换行 
Markdown中直接敲回车是无法换行的如需换行请在句子结尾加上一个空格再回车。
## 标题  
Markdown的标题共有六种级别： 
```
# 一级标题 
## 二级标题 
### 三级标题 
#### 四级标题 
##### 五级标题 
###### 六级标题 
```
效果如下:  

# 一级标题 

## 二级标题 

### 三级标题 

#### 四级标题 

##### 五级标题 

###### 六级标题 

## 高亮  
使用>使语句高亮  
语法如下：

`> 高亮的内容`  
效果如下： 
> 高亮的内容 

## 插入连接或图片 
### 连接 
语法如下  
`[连接名](地址)`  
效果如下  
[百度](www.baidu.com)

### 图片
`![图片名称](图片地址)`
> 图片地址可以是本地路径，也可以是URL，推荐使用各大图床生成URL以节约服务器空间 
## 列表 
### 无序列表 
语法如下：  
```
* 元素X
* 元素Y
* 元素Z
或
+ 元素X
+ 元素Y
+ 元素Z
或
- 元素X
- 元素Y
- 元素Z
```
效果如下 
* 元素X
* 元素Y
* 元素Z  
### 有序列表  
语法如下：  
```
1. 元素X
2. 元素Y
3. 元素Z
```
效果如下 
1. 元素X
2. 元素Y
3. 元素Z  
>  如果在单一列表项中包含了多个段落，*与段落首字母之间必须保留四个空格   

例如： 
```
*    段落一

     小段一
*    段落二

     小段二
```
效果如下：
*    段落一

     小段一
*    段落二

     小段二  
## 分割线 
语法如下： 
```
*** 
或
---
```
效果如下： 
*** 
## 加粗与斜体
### 加粗 
语法如下：  
```
**加粗**
或
__加粗__
```
效果如下：  
**加粗** 
## 斜体 
```
*斜体* 
或 
_斜体_
```
## 插入代码 
如需插入一行代码只需将代码放在两个`(反引号esc键下面那个键)之间如需插入一个代码块则需使用三个反引号将其包裹住。 

效果如下： 
```
print('welecome')
```
  
    


---  
  
    
    

>**Markdown语法看起来有点麻烦，其实只要你上手用一用就能很快的掌握它。一旦你习惯了它之后，你会真真切切的感受到它给你带来的方便，你也会爱上它这种简约美观的排版风格，如果你经常和文字打交道，又或者你有在文章中插入代码的需求，那么不妨试试Markdown或许它将是你的不二之选。** 