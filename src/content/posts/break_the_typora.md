---
title: 如何下载并破解Typora
published: 2026-02-20
pinned: false
description: "Typora是一个非常好用的md编辑器，不过要收费，本文提供了一种破解的方法"
tags: [ "教程", "Markdown","破解"]
category: 教程
---




# 如何下载Typora并破解

## 下载一个Typora 

### 注意：

#### 	 下载时注意版本不要超过1.10.8

​		**超过该版本无法正常破解**

#### 	下载完后一定记得打开一下,不然会闪退

​		

然后就可以关闭退出，准备开始破解了。

---



## 激活Typora

### 右键桌面快捷方式，打开文件所在位置



### 依次找到这个文件

**resources\page-dist\static\js\  LicenseIndex.********.**************.chunk.js**



### 用笔记本打开它

**查 找（ctrl+f）【e.hasActivated="true"==e.hasActivated,】**

**替换为【e.hasActivated="true"=="true",】**

#### 保存关闭

  **此时已激活成功**



## 关闭每次启动时的已激活弹窗

### 在Typora安装目录依次找到这个文件

**resources\page-dist\static\js\0.99879679.chunk.js**

### 用记事本打开它

**找到下面内容：**

**/*! For license information please see 0.99879679.chunk.js.LICENSE.txt */**

**回车一行，加入以下代码：**

~~~js
var div = document.createElement('div');

div.id = 'myOverlay';

div.style.position = 'fixed';
div.style.top = '0';
div.style.left = '0';
div.style.width = '100vw'; 
div.style.height = '100vh';
div.style.backgroundColor = 'rgb(54,59,64)'; 
div.style.zIndex = '9999'; 

document.body.appendChild(div);

setTimeout(function () {
    var overlay = document.getElementById('myOverlay');
    if (overlay) {
        overlay.remove(); 
    }

```js
document.querySelector('.default-btn.secondary-btn').click(); 
```

}, 360); 
~~~



##### 保存关闭



## 四.去除软件左下角“未激活”提示

### 在Typora安装目录依次找到这个文件

**resources\window.html**

### 用记事本打开它

**查 找【`<head>`】（第一个`<head>`）**

**加入以下代码**
~~~js
 <style>
         body>div[role="button"] {
             visibility: hidden;
         }
 </style>
 ~~~
### 保存关闭





