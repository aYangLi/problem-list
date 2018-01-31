### 目录
[19. 兼容脚本题](#19)  
[18. 移动端 border 宽度问题](#18)  
[17. flex布局中的注意事项](#17)  
[16. jQuery选取元素](#16)  
[15. 布局垂直对齐的方式](#15)  
[14. cookie 和 session 的区别](#14)  
[13. 自动登录的实现](#13)  
[12. 移动端的几种适配](#12)  
[11. jQuery中判断一个元素是否显示或者隐藏](#11)  
[10. ios中的一些兼容问题](#10)  
[9. require.js 做单页面应用](#9)  
[8. 分享qq空间出现失败](#8)  
[7. img 标签边框问题](#7)  
[6. filezilla连接服务器连接不上](#6)  
[5. 自执行函数的使用](#5)  
[4. 按钮置灰不能点击的方法](#4)  
[3. 给元素添加事件满足的条件](#3)  
[2. jQuery 中 trigger 的使用](#2)  
[1. stick footer 黏性底部](#1)

<h3 id='19'>19. 兼容脚本题</h3>

#### 详情描述

1. rem.js		使IE8能够识别rem单位（但是不能控制伪元素）；
2. html5shiv.js	使IE8识别HTML5标签；
3. pie.htc		识别部分css3样式属性（border-radius等）；
4. response.js	使用js模仿媒体查询；

<h3 id='18'>18. 移动端 border 宽度问题</h3>

#### 详情描述

在移动端布局中，经常使用 rem 单位，但是 border 使用热门单位时会有兼容性， 比如魅族手机浏览器，ios 部分系统；border 不显示；可以使用 px 布局；

<h3 id='17'>17. flex布局中的注意事项</h3>

#### 详情描述

父级设置：display: flex;flex-wrap: wrap（超出部分换行，no-wrap  不换行wrap : 第一行在上面；wrap-reverse： 换行，第一行在下面）;子集纵轴排列会默认每个项目两侧的间隔相等，项目之间的间隔比项目之间的边框的间隔大一倍；如果需要清除默认样式的影响，则设置justify-content:  flex-start（flex-start :左对齐；flex-end: 右对齐；center：居中；space-between：两端对齐，项目之间的间隔都相等；space-around：每个项目两侧的间隔相等，项目之间的间隔比项目之间的边框的间隔大一倍）（实列见复诊建议项目框）;

<h3 id='16'>16. jQuery选取元素</h3>

#### 详情描述
jQuery([selector,[context]])  
selector:用来查找的字符串  
context:作为待查找的 DOM 元素集、文档或 jQuery 对象。  
$("p,div")		找到元素p和div  
$("p","div")	找到div里面的p

<h3 id='15'>15. 布局垂直对齐的方式</h3>

#### 详情描述
1. 左右容器分别设置display:table-cell；vertical-align:middle;
2. 左右容器分别设置display:inline-block；vertical-align:middle;（会出先兼容问题，比如努比亚z11line-height不起效果；可以利用padding居中，把空白撑开）

**注意：** display:table-cell属性指让标签元素以表格单元格的形式呈现，可以实现元素的垂直居中对齐(vertical-align:middle;)，关联伸缩等，与其他一些display属性类似，table-cell同样会被其他一些CSS属性破坏，例如float, position:absolute

<h3 id='14'>14. cookie 和 session 的区别</h3>

#### 详情描述

1. cookie 数据存放在客户的浏览器上，session 数据放在服务器上。
2. cookie 不是很安全，别人可以分析存放在本地的 COOKIE 并进行 COOKIE 欺骗考虑到安全应当使用 session 。
3. session 会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能考虑到减轻 		
服务器性能方面，应当使用 COOKIE 。
4. 单个 cookie 保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个 cookie 。
5. 所以个人建议：
    - 将登陆信息等重要信息存放为SESSION
   	- 其他信息如果需要保留，可以放在COOKIE中

<h3 id='13'>13. 自动登录的实现</h3>

#### 详情描述
1. 第一次登录之后，后台会在返回的cookie里保存的一些东西，然后每个页面都会掉一次getLapList接口，后台会判断cookie里是否有之前返回过的东西，根据返回的数据，成功则获取到用户的基本信息，失败则进入登录页面；
2. 用户点击退出登录之后，退出登录的接口成功后，后台会清除cookie，下次用户从新登录；
 

**注意：** 后台可以设置cookie是否可读可写，自动登录的机制（安全角度讲）下后台会禁止前端拿到后台设置的cookie进行读写；

<h3 id='12'>12. 移动端的几种适配</h3>

#### 详情描述

1. 淘宝：使用viewport缩放，通过给html添加 data-dpr=xx, 设置html字体大小，来适配移动端，唯医模仿淘宝；单位使用rem；
2. 天猫：禁止viewport缩放，定高不定宽，使用弹性盒子布局；单位使用px；
3. 京东：禁止viewport缩放，宽高都使用百分比，设置最大宽度和最小宽度；通过@media媒体查询，设置不同的宽高；单位使用px；
4. 小米：禁止viewport缩放，单位使用rem；当屏幕宽度改变时，html标签的行内样式font-size跟着改变(自己感觉可以根据window.resize()可以实现)；

<h3 id='11'>11. jQuery中判断一个元素是否显示或者隐藏</h3>

#### 详情描述
1. 第一种方式：

```

alert($('.div1').is(':hidden'));//false,没隐藏
alert($('.div2').is(':hidden'));//true,隐藏了
$('#dvData').is(":visible")
```
2. 第二种方式：

```
if ($('#dvData').css('display') == 'none') {
    // Item is hidden. Write your code.
}
if($('#dvData').is(":visible")){
     // Item is hidden. Write your code.
}
if ($('#dvData').css("visibility") == "hidden"){
   // Item is hidden. Write your code.
}
```

<h3 id='10'>10. ios中的一些兼容问题</h3>

#### 详情描述
1. ios8.4.1版本中对jQuery中closeset（）、find（）、存在兼容性，只能直接使用jQuery对象去使用这些方法。通过赋值的方法去调用不起作用；
2. ios上微信端a标签href必须填写（JavaScript：0；）；否则无法点击
3. ios上微信端不给元素设置 cursor:pointer 样式，可能会出现在手机上无法点击的情况；

<h3 id='9'>9. require.js 做单页面应用</h3>

#### 详情描述

require.js配合插件text.js实现最简单的单页应用程序；text和image插件，则是允许require.js加载文本和图片文件。详细代码见项目；require.js的好处：
1. 实现js文件的异步加载，避免网页失去响应；
2. 管理模块之间的依赖性，便于代码的编写和维护。

<h3 id='8'>8. 分享qq空间出现失败</h3>

#### 详情描述

做 qq 分享时，如果给 qq 的链接参数中有中文；会分享失败；

<h3 id='7'>7. img 标签边框问题</h3>

#### 详情描述

\<img\>标签默认有固定宽度，并且不设置src属性或者src属性=“”时，会有默认边框，想让边框消失的一个解决办法：  
利用属性选择器[src=""]让的 img 的 src 属性为空的透明度设为0；如下：

```
img[src=""],img:not([src]){
  opacity:0;
}
```


<h3 id='6'>6. filezilla连接服务器连接不上</h3>

#### 详情描述

ftp协议默认使用的是21端口，80端口默认是使用的http协议，也就是网站默认是使用的80端口您这边需要先配置FTP服务，然后才能使用ftp软件登录您的服务器。之前登录服务器是使用的sftp，也就是通过22端口来登录的。对于FTP的配置，linux 推荐 vsftpd 

<h3 id='5'>5. 自执行函数的使用</h3>

#### 详情描述

1. 在模板中循环添加数据并返回；
2. 减少全局变量，最后用window.xxx=xxx;把方法暴露出去就可以（是模块化开发演变中的一个历程）；
3. 自执行函数可以直接绑定在 onClick 上；比如：
```
<button onClick="(function(){alert('1')})()">执行</button>
```

<h3 id='4'>4. 按钮置灰不能点击的方法</h3>

#### 详情描述

1. 给button添加disabled的属性。注意，控制disabled为ture或者false才能起作用；
2. 给添加单独的类名显示不同的颜色，然后点击的时候判断return false；
3. 控制两个button，一个绑定事件，一个不绑定；通过控制验证字段是否通过来控制按钮的显示隐藏；

<h3 id='3'>3. 给元素添加事件满足的条件</h3>

#### 详情描述

1. 确保元素已经加载出来再添加；  
2. 利用事件委托的方式去添加事件（比较常用的一种方案）；利用事件流的冒泡机制，可以给父元素委托事件；这样动态添加的子元素也会有事件；

<h3 id='2'>2. jQuery 中 trigger 的使用</h3> 

#### 详情描述

1. trigger不可以直接触发input（file）、select的原生事件；可以触发给元素添加的事件；但是如果trigger外面包了一层on（“click”），则可以触发input（file）、select的原生事件
2. trigger触发某个元素的某个事件，首先得让那个元素把那个事件添加的函数提前执行；比如可以使用 trigger 做进入页面自动定位的功能，但是在触发 trigger 之前，必须确保触发元素的事件已经绑定上；
3. fastclick.js会影响trigger的使用，出现点击第一次没有出现响应，第二次才起效果（具体原因请看移动端 300ms 延时问题）

<h3 id='1'>1. stickfooter黏性底部</h3>  

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
