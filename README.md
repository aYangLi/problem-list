### 目录
[9.require.js 做单页面应用](#9)  
[8.分享qq空间出现失败](#8)  
[7.img 标签边框问题](#7)  
[6.filezilla连接服务器连接不上](#6)  
[5.自执行函数的使用](#5)  
[4.按钮置灰不能点击的方法](#4)  
[3.给元素添加事件满足的条件](#3)  
[2.jQuery 中 trigger 的使用](#2)  
[1.stick footer 黏性底部](#1)

<h3 id='9'>9.require.js 做单页面应用</h3>

#### 详情描述

require.js配合插件text.js实现最简单的单页应用程序；text和image插件，则是允许require.js加载文本和图片文件。详细代码见项目；require.js的好处：
1. 实现js文件的异步加载，避免网页失去响应；
2. 管理模块之间的依赖性，便于代码的编写和维护。

<h3 id='8'>8.分享qq空间出现失败</h3>

#### 详情描述

做 qq 分享时，如果给 qq 的链接参数中有中文；会分享失败；

<h3 id='7'>7.img 标签边框问题</h3>

#### 详情描述

\<img\>标签默认有固定宽度，并且不设置src属性或者src属性=“”时，会有默认边框，想让边框消失的一个解决办法：  
利用属性选择器[src=""]让的 img 的 src 属性为空的透明度设为0；如下：

```
img[src=""],img:not([src]){
  opacity:0;
}
```


<h3 id='6'>6.filezilla连接服务器连接不上</h3>

#### 详情描述

ftp协议默认使用的是21端口，80端口默认是使用的http协议，也就是网站默认是使用的80端口您这边需要先配置FTP服务，然后才能使用ftp软件登录您的服务器。之前登录服务器是使用的sftp，也就是通过22端口来登录的。对于FTP的配置，linux 推荐 vsftpd 

<h3 id='5'>5.自执行函数的使用</h3>

#### 详情描述

1. 在模板中循环添加数据并返回；
2. 减少全局变量，最后用window.xxx=xxx;把方法暴露出去就可以（是模块化开发演变中的一个历程）；
3. 自执行函数可以直接绑定在 onClick 上；比如：
```
<button onClick="(function(){alert('1')})()">执行</button>
```

<h3 id='4'>4.按钮置灰不能点击的方法</h3>

#### 详情描述

1. 给button添加disabled的属性。注意，控制disabled为ture或者false才能起作用；
2. 给添加单独的类名显示不同的颜色，然后点击的时候判断return false；
3. 控制两个button，一个绑定事件，一个不绑定；通过控制验证字段是否通过来控制按钮的显示隐藏；

<h3 id='3'>3.给元素添加事件满足的条件</h3>

#### 详情描述

1. 确保元素已经加载出来再添加；  
2. 利用事件委托的方式去添加事件（比较常用的一种方案）；利用事件流的冒泡机制，可以给父元素委托事件；这样动态添加的子元素也会有事件；

<h3 id='2'>2.jQuery 中 trigger 的使用</h3> 

#### 详情描述

1. trigger不可以直接触发input（file）、select的原生事件；可以触发给元素添加的事件；但是如果trigger外面包了一层on（“click”），则可以触发input（file）、select的原生事件
2. trigger触发某个元素的某个事件，首先得让那个元素把那个事件添加的函数提前执行；比如可以使用 trigger 做进入页面自动定位的功能，但是在触发 trigger 之前，必须确保触发元素的事件已经绑定上；
3. fastclick.js会影响trigger的使用，出现点击第一次没有出现响应，第二次才起效果（具体原因请看移动端 300ms 延时问题）

<h3 id='1'>1.stickfooter黏性底部</h3>  

#### 问题描述  

> 问诊咨询流程页，布局需要将下一步（提交）按钮在内容较少时，固定在底部；内容超出页面高度时，跟随内容高度下面
    
#### 解决方案 

这种布局就是 stick footer 黏性底部 布局；这里提供两种方案实现以及实现的思路；  
思路为有一个 min-height:100% 的元素，围绕这个元素做文章；注意 html 需要设置 height:100%;

方案一：footer绝对定位-并加一层父元素
 
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            margin:0;
            padding:0;
            box-sizing: border-box;
        }
        html,body{
            height: 100%;
            /*min-height: 100%;*/
            min-width: 1200px;
        }
        body{
            font: 14px/1.5 "Microsoft YaHei", sans-serif;
            color: #666666;
            background: #e8e8e8;
        }
        .body{
            position: relative;
            min-height: 100%;
            height:auto !important;
            height:100%;//IE6不识别min-height
        }
        .header{
            width: 100%;
            background-color: #f1a899;
            height: 64px;
            box-shadow: 0 0 0 transparent, 0 0 0 transparent, 0 4px 8px #DFDFDF, 0 0 0 transparent;
        }
        .section{
            width: 1200px;
            margin: 0 auto;
            padding: 30px 0 145px;
        }
        .container{
            background: #ffffff;
            height:500px;
        }
        .footer{
            position: absolute;
            bottom: 0;
            height: 95px;
            width: 100%;
            background: #858B9A;
        }
    </style>
</head>
<body>
<div class="body">
    <div class="header">
        header页面头部
    </div>
    <div class="section">
        <div class="container">
            页面主体内容
        </div>
    </div>
    <div class="footer">
        footer页面底部
    </div>
</div>
</body>
</html>
```

方案二：footer加负值上边距
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            height: 100%;
            min-height: 100%;
            min-width: 1200px;
        }

        body {
            font: 14px/1.5 "Microsoft YaHei", sans-serif;
            color: #666666;
            background: #e8e8e8;
        }

        .header {
            width: 100%;
            background-color: #f1a899;
            height: 64px;
            box-shadow: 0 0 0 transparent, 0 0 0 transparent, 0 4px 8px #DFDFDF, 0 0 0 transparent;
        }

        .section {
            min-height: 100%;
            padding: 0 0 95px;
        }

        .container {
            width: 1200px;
            height: 500px;
            margin: 30px auto;
            background: #ffffff;
        }

        .footer {
            height: 95px;
            margin-top: -95px;
            width: 100%;
            background: #858B9A;
        }
    </style>
</head>
<body>

<div class="section">
    <div class="header">
        header页面头部
    </div>
    <div class="container">
        页面主体内容
    </div>
</div>

<div class="footer">
    footer页面底部
</div>
</body>
</html>
```
