### 目录
[53. H5 中调相机、多选等问题](#53)  
[52. 推荐医生白色区块问题](#52)  
[51. 推荐医生头像问题](#51)  
[50. IM中输入框的问题](#50)  
[49. iscroll 和 better-scroll](#49)  
[48. better-scroll的实现原理](#48)  
[47. scroll 事件的触发](#47)  
[46. ios 上 IM 页面路由跳转白屏](#46)  
[45. Safari 中双指放大缩小问题](#45)  
[44. vue 中的通信](#44)  
[43. es6 新增方法处理](#43)  
[42. 页面唤起拨打电话](#42)  
[41. vue 双向绑定数据限制长度](#41)  
[40. vue中 v-if 遇到的问题](#40)  
[39. vue中 keep-alive 的使用](#39)  
[38. 数组的过滤器 filter 的问题](#38)  
[37. 在不翻墙的情况下下载vue调试插件（vue-DevTools）](#37)  
[36. vue中 v-if 和 v-show](#36)  
[35. 视频中的坑](#35)  
[34. 滚动穿透问题](#34)  
[33. app引导页的判断](#33)  
[32. 页面跳转的方式以及区别](#32)  
[31. 什么是 URL Schema？](#31)  
[30. app 与 js 之间的交互](#30)  
[29. window.name 的使用](#29)  
[28. 代码计时器](#28)  
[27. canvas图画保存成本地图片的方法](#27)  
[26. json 的注意事项](#26)  
[25. input 输入框输入中文](#25)  
[24. 输入框的事件的几种触发事件对比](#24)  
[23. jQuery 中 data() 引发的错误](#23)  
[22. js打开新页面的几种方式](#22)  
[21. 跨域的方式](#21)  
[20. select 默认选中问题](#20)  
[19. 兼容脚本](#19)  
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

<h3 id='53'>53. H5 中调相机、多选等问题</h3>  

#### 详情描述

```
<input type="file" accept="image/*" capture="camera">
<input type="file" accept="video/*" capture="camcorder">
<input type="file" accept="audio/*" capture="microphone">

```

capture表示，可以捕获到系统默认的设备，比如：camera--照相机；camcorder--摄像机； microphone--录音。  
accept表示，直接打开系统文件目录。

其实html5的input:file标签还支持一个multiple属性，表示可以支持多选，如：  
<input type="file" accept="image/*" multiple>  
但是安卓不支持多图上传，（会诊项目）
加上这个multiple后，capture就没啥用了，因为multiple是专门用来支持多选的。

**注意：**  
input file 标签在安卓上想要掉起相机，需要添加capture="camera"，但是此属性会影响 ios 的掉起相机，在ios上需要取消掉；

<h3 id='52'>52. 推荐医生白色区块问题</h3>  

#### 问题描述  

> 在 ios 上，推荐医生数据超过十条时，渲染不出来，为白色
    
#### 解决方案 

替换ul、li标签为section标签；
具体原因不明

<h3 id='51'>51. 推荐医生头像问题</h3>  

#### 问题描述  

> 在ios9.3.2上滑动，图片会变成方形，其他手机没问题，。
    
#### 解决方案 
推荐医生医生头像，div 里面套了个 img 标签，只给 div 设置 border-radius: 50%;在 ios9.3.2 上滑动，图片会变成方形，其他手机没问题，给img也添加border-radius: 50%；

<h3 id='50'>50. IM中输入框的问题</h3>  

#### 详情描述

1. ios（特别是UC浏览器）对底部fiexd布局，兼容不好，再聚焦的时候fiexd会漂，所以不能用fiexd布局；
2. ios底部输入框用的是relative，absolute会再部分ios机子上全屏感觉有个遮罩层，使全屏不可点，点的时候有个黑色透明的遮罩层闪烁；
3. android 底部输入框用的是absolute，relative 布局在安卓上输入框会覆盖在虚拟键盘下面；
4. ios11.1.2 对面几种布局支持性都不好，当虚拟键盘出来后，输入框不会被挤到上面（因为body高度不变）；解决方式比较暴力，判断是ios11.1.2，数据框聚焦把body变为50%，失焦恢复；

<h3 id='49'>49. iscroll 和 better-scroll</h3>  

#### 详情描述

iscroll 和 better-scroll 的对比
iscroll的兼容性比较强，用requestAnimationFrame（表意为“请求动画帧”）实现，可以兼容到 ie6，requestAnimationFrame是根据浏览器的最小渲染值来触发；达到流畅效果；但是已经停止维护
better-scroll 是滴滴负责人黄轶写的，使用css3和requestAnimationFrame；默认优先使用css3，参数可以配置；

<h3 id='48'>48. better-scroll的实现原理</h3>  

#### 详情描述

父容器固定高度，并设置属性 overflow:hidden，使得子元素高度超出容器后能被隐藏。better-scroll作用在父容器上。通过touch事件给子容器设置transform：translate()translateZ();  
**注意：**   
Vue中数据更新是异步的，在数据还没有加载完之前，BScroll是无法获取目标内容容器的高度的，就会出现无法滚动的现象。

<h3 id='47'>47. scroll 事件的触发</h3>  

#### 详情描述

```
window.addEventListener('scroll',function () {

})
//ios上只会在滚动稳定后出发；安卓会有间隔的持续触发；
```


<h3 id='46'>46. ios 上 IM 页面路由跳转白屏</h3>  

#### 问题描述  

> vue 手机端项目在进入主页后在进入子页面，直接按返回出现空白情况，然后轻触一下，空白区域就消失了  
安卓手机上不会，ios 会出现这种情况。
    
#### 解决方案 
这是safari的ios render blank.

```
//拿到数据之后
this.$nextTick(() => {
	window.scrollTo(0, 1)
	window.scrollTo(0, 0)
})
```


<h3 id='45'>45. Safari 中双指放大缩小问题</h3>  

#### 问题描述  

> 为了提高Safari中网站的辅助功能，即使网站在视口中设置了user-scalable = no，用户也可以手动缩放。
    
#### 解决方案 
监听事件来阻止

```
window.onload=function () {  
 	document.addEventListener('touchstart',function (event) {  
        if(event.touches.length>1){  
            event.preventDefault();  
        }  
    })  
    var lastTouchEnd=0;  
    document.addEventListener('touchend',function (event) {  
        var now=(new Date()).getTime();  
        if(now-lastTouchEnd<=300){  
            event.preventDefault();  
        }  
        lastTouchEnd=now;  
    },false)  
}  
```
淘宝的解决方案也是如此 ；但是并不能很好的解决；

<h3 id='44'>44. vue 中的通信</h3>  

#### 详情描述

##### 父子组件通信：
1. 子组件触发父组件函数：

```
子组件：
<template>
    <button @click="submit">提交</button>
</template>
<script>
export default {
  props: {
    onsubmit: {
      type: Function,
      default: null
    }
  },
  methods: {
    submit: function () {
      if (this.onsubmit) {
        this.onsubmit(‘cc12345’)
      }
    }
  }
}
</script>
父组件：
<template>
    <editor id="editor" class="editor" :onsubmit="cc"></editor>
</template>
<script>
export default {
  methods: {
    cc: function (str) {
      alert(str)
    }
  }
}
</script>
```

2. 子组件修改父组件传过来的值:this.$emit('update:foo', newValue);父组件通过v-bind绑定并且写上.aync；
3. 由于javascript的特性，父组件像子组件传一个对象，子组件修改也会出发父组件变化；

##### 非父子组件通信

1. 	用一个新的 vue 实列管理
```
var bus = new Vue()
// 触发组件 A 中的事件
bus.$emit('id-selected', 1)
// 在组件 B 创建的钩子中监听事件
bus.$on('id-selected', function (id) {
 		 // ...
})
```
2. 用vuex状态管理
 

<h3 id='43'>43. es6 新增方法处理</h3>  

#### 详情描述
es6中Array.includes和Object.assign方法在部分浏览器中支持性不太好，需要用babel-polyfill处理。

<h3 id='42'>42. 页面唤起拨打电话</h3>  

#### 详情描述
1. window.location.href = "tel:010-59007006";支持性比较好，ios、安卓都支持
2. 用 a 标签：

```
<a href="tel:010-59007006" class="make-call" ref="makeCall"></a>；
//直接点击ios、安卓都支持、但是使用自动触发安卓支持、ios支持不太好；
```


<h3 id='41'>41. vue 双向绑定数据限制长度</h3>  

#### 问题描述  

> vue中输入框v-modle 双向绑定的数据；在需要的业务场景下需要对其进行字数长度限制；
    
#### 解决方案 
可以使用以下方法：  
1. 方法一：

```
//方法一：输入框添加keypress方法；然后函数为：
maxLength(attr,length){
	let keyCode = event.keyCode;
	console.log("keyCode");
    	let len=0;
	console.log(this[attr].length);
	for (let codePoint of this[attr]) {
 		if (this[attr].charCodeAt(codePoint) > 128) {
    			len += 2;
  		} else {
   	 		len++;
  		}
    	}
	if (len < length) {
  		event.returnValue = true;
	} else {
  		event.returnValue = false;
	}
},
//注意：事件必须为keypress；
//keydown 可以做限制，但是达到长度不可以删除；keyup不行；
```

2. 方法二：

```
//方法二：输入框添加input方法；然后函数为：
inputMaxLength(attr,length){
  		this[attr] = api.getStrByteLen(this[attr], length);
},
```

**方法对比：**  
方法一优点，循环少，性能高；缺点，中文输入法空格输入字符的时候不会触发；  
方法二优点，兼容性好，适合各种场景；缺点，循环多，性能比较差；

<h3 id='40'>40. vue中 v-if 遇到的问题</h3>  

#### 问题描述  

> 在添加患者中；botton 按钮用 v-if 隐藏掉之后，出现了不可见，但是可以点击的情况
    
#### 解决方案 
在 botton 外层添加了一层 session 标签；可能是 v-if 对行内块原理有兼容性；

<h3 id='39'>39. vue中 keep-alive 的使用</h3>  

#### 问题描述  

> 在业务开发中，会有路由跳转但是返回需要保留数据的场景；vue 中提供了 keep-alive 来处理
    
#### 解决方案 

返回dom不让其重新刷新，在vue-view外面包一层<keep-alive><keep-alive/>,
当引入keep-alive的时候，页面第一次进入，钩子的触发顺序created-> mounted-> activated，退出时触发deactivated。当再次进入（前进或者后退）时，只触发activated。  
事件挂载的方法等，只执行一次的放在 mounted 中；组件每次进去执行的方法放在 activated 中；
可以将 是否包裹 keep-alive 通过参数配置；

```
<keep-alive>
  	<router-view v-if="$route.meta.keepAlive" style="min-height:100%"></router-view>
</keep-alive>
<router-view v-if="!$route.meta.keepAlive" style="min-height:100%"></router-view>
//不需要刷新的路由配置里面配置 meta: {keepAlive: true}, 这个路由则显示在上面标签；
//需要刷新的路由配置里面配置 meta: {keepAlive: false}, 这个路由则显示在下面标签；
```

<h3 id='38'>38. 数组的过滤器 filter 的问题</h3>

#### 详情描述

对象或者数组的过滤器filter，不能使用第三方变量过滤；
比如：var num = value ; return num>0; 必须写成：return value>0;

<h3 id='37'>37. 在不翻墙的情况下下载vue调试插件（vue-DevTools）</h3>

#### 详情描述

1. Chrome地址栏输入"crx.2333.me"
2. 然后把你要下载的扩展ID填到输入框中，点击"Get"（vue的id：nhdogjmejiglipccpnnnanhbledajbpd）
3. 点击"成功Get，点我下载"
4. 或者在github 上搜vue-Devtools

<h3 id='36'>36. vue中 v-if 和 v-show</h3>

#### 详情描述

1. v-if是惰性的，每次false之后会删除元素，这样，每次显示的时候都会重新走选择城市的接口。
2. v-show，只是简单的显示隐藏

<h3 id='35'>35. 视频中的坑</h3>

#### 详情描述
[参考自此链接](http://mp.weixin.qq.com/s?__biz=MzI3NTM1MjExMg==&mid=2247484551&idx=1&sn=9d8995a704c3f674673eb41863781263&chksm=eb075bd8dc70d2ce057f257523d33beda366e1ae33db034c641c4070b8c220b85a0cdb58d2b9&mpshare=1&scene=1&srcid=0630AD0ajBVqblfyXGWwgvTU#rd) 以及乔的ppt；
1. 自动播放问题：
通过autoplay属性
视频的自动播放需要在video标签上添加autoplay属性, 如：\<video autoplay>\<video/>  
但是在很多浏览器里，如 iOS 下并不支持这个属性，在 iOS下必须给webview设置
self.wView.allowsInlineMediaPlayback = YES;self.wView.mediaPlaybackRequiresUserAction = NO; 
才能让这个属性生效从而让用户一进入页面就开始视频的自动播放
在微信下因为不允许视频直接播放，则必须通过用户的真实操作来触发调用video.play(),这就是各种微信的h5活动页面需要引导用户进行一下点击操作才开始的原因。
2. 页面内联播放问题：在iOS Safari 和一些安卓的一些浏览器下播放视频的时候，不能在h5页面中播放视频，系统会自动接管视频
如果需要在h5页面内播放视频，需要在视频标签上加上 webkit-playsinline，在iOS10以后，需要加上playsinline,建议同时加上这两个属性，同时需要app支持这种模式，手Q和微信都支持这种模式  
\<video id="player" webkit-playsinline playsinline > (在html)
    webview.allowsInlineMediaPlayback = YES(在app内设置webview属性);
3. 视频的高度问题：在安卓下，一些浏览器如 QQ 浏览器和 UC 浏览器，系统会把视频的层级调到最高，所以如果想在页面上显示 dom 元素，都会被视频盖住，单纯的设置该dom的z-index是无效的  
**解决方案：**
    1. 在弹出会显示在视频上方dom的时候暂停视频播放
    2. 将视频所在的dom的父元素的高度设为1
    3. 处理完弹出的事件后将视频所在的父元素高度还原
    4. 视频的默认播放图标
4. 在 iOS 下会有一个默认的播放图标，在 iOS 都会默认显示，不能通过 js 控制，但是可以通过css样式将其隐藏
```
	video::-webkit-media-controls-start-playback-button { display: none;}
```

    

<h3 id='34'>34. 滚动穿透问题</h3>

#### 详情描述
解决方法：
1. 在弹层出现时给body设置position：fixed，top：-滚动条高度；弹层消失的时候获取body的top，$(window).scrollTop(-body的高度)。解决大部分场景，在ios微信浏览器无法禁止微信浏览器原生的弹性黑层；
2. 用iscroll.js+禁止touch事件（唯医答题用的方法）解决

<h3 id='33'>33. app引导页的判断</h3>

#### 详情描述
1. 判断是否是第一次打开，本地存储一个标识符，第一次打开后设置为true，以后进入判断该标志符，为false则可以进入引导页；
2. 判断是否是同一版本号，进入时判断本地保存的版本号和打开的版本号是否是同一版本号，如果不是，则进入引导页，并且把版本号设置为当前版本号；

<h3 id='32'>32. 页面跳转的方式以及区别</h3>

#### 详情描述
跳转方式有：
- window.location.href,
- window.location.replace(),
- window.location.reload()  

三者的区别：
  1. window.location.href=“url”：改变url地址；
  2. window.location.replace(“url”)：将地址替换成新url，该方法通过指定URL替换当前缓存在历史里（客户端）的项目，因此当使用replace方法之后，你不能通过“前进”和“后 退”来访问已经被替换的URL，这个特点对于做一些过渡页面非常有用！
  3. window.location.reload()：强制刷新页面，从服务器重新请求！
解决的问题，在app中嵌套的网页中，收到传的参数时，用replace替换当前url。且不加入历史栈

<h3 id='31'>31. 什么是 URL Schema？</h3>

#### 详情描述

Android中的scheme是一种页面内跳转协议，是一种非常好的实现机制，通过定义自己的scheme协议，可以非常方便跳转app中的各个页面；通过scheme协议，服务器可以定制化告诉App跳转那个页面，可以通过通知栏消息定制化跳转页面，可以通过H5页面跳转页面等。  
[详细链接点此进入](http://blog.csdn.net/ruingman/article/details/70054670)



<h3 id='30'>30. app 与 js 之间的交互</h3>

#### 详情描述
采用的框架是 WebViewJavascriptBridge，采用这套框架可以方便的使 native 与 JS 交互  
[详细链接点此进入](http://www.cnblogs.com/TheYouth/p/5854467.html)

<h3 id='29'>29. window.name 的使用</h3>

#### 详情描述
window.name	给当前窗口起名字，iframe也可这样使用。  
name 在全局下是关键字；  
window.open('','MyName','width=200,height=100')；  
- 参数一：url，打开的链接；
- 参数二：打开窗口的名字；
- 参数三：打开窗口的大小px；
应用场景：
1. 用来判断此窗口是刷新，还是重新打开的窗口，来执行不同的操作；
2. 跨域（待补充）；

<h3 id='28'>28. 代码计时器</h3>

#### 详情描述

```
console.time("main");
console.timeEnd("main")。
```

<h3 id='27'>27. canvas图画保存成本地图片的方法</h3>

#### 详情描述

```
var oCanvas = document.getElementById("thecanvas");
Canvas2Image.saveAsPNG(oCanvas);  // 这将会提示用户保存PNG图片
Canvas2Image.saveAsJPEG(oCanvas); // 这将会提示用户保存JPG图片
Canvas2Image.saveAsBMP(oCanvas);  // 这将会提示用户保存BMP图片
// 返回一个包含PNG图片的<img>元素
var oImgPNG = Canvas2Image.saveAsPNG(oCanvas, true); 
// 返回一个包含JPG图片的<img>元素
var oImgJPEG = Canvas2Image.saveAsJPEG(oCanvas, true); 
// 返回一个包含BMP图片的<img>元素
var oImgBMP = Canvas2Image.saveAsBMP(oCanvas, true);
```

<h3 id='26'>26. json 的注意事项</h3>

#### 详情描述

自己写的json字符串中必须用双引号。使用单引号无法转换成json对象；

<h3 id='25'>25. input 输入框输入中文</h3>  

#### 问题描述  

> 在input输入框输入中文时，需要即时查询出匹配输入内容的结果，一般我们会使用input事件监听用户输入事件，但是在输入汉语拼音时，也会触发input事件，前端就会不断发送请求，用户体验非常差劲。
    
#### 解决方案 
针对这种情况，给大家介绍一个简单易懂的好方法。代码如下：
```
function in2 () {
	var cpLock = false;
    $('#in2').on('compositionstart', function () {
        cpLock = true;
        console.log("中文输入：开始");
		$("span").text("kaishi");
		$(this).off("input");
    });
    $('#in2').on('compositionend', function () {
        cpLock = false;
        console.log("中文输入：结束")
		$("span").text("jieshu");
		console.log($(this).val().length);
		$(this).on('input', function () {
            if (!cpLock) {
                console.log($(this).val().length);
            }
        });

	});
}
```
**原理：**  
当浏览器有非直接的文字输入时, compositionstart 事件会以同步模式触发.  
当浏览器是直接的文字输入时, compositionend 会以同步模式触发.  
当元素监听到 compositionstart 事件，给 input 中事件加锁，禁止 input中事件执行，  
当元素监听到 compositionend 事件，给input中事件解锁，正常执行。

<h3 id='24'>24. 输入框的事件的几种触发事件对比</h3>

#### 详情描述
1. change事件    触发事件必须满足两个条件：
    - 当前对象属性改变，并且是由键盘或鼠标事件激发的（脚本触发无效）
    - 当前对象失去焦点(onblur)
2. keypress  恩，还好。。。。。就是能监听键盘事件，鼠标复制黏贴操作他就无能为力
3. propertychange（ie）和input事件

input是标准的浏览器事件，一般应用于input元素，当input的value发生变化就会发生，无论是键盘输入还是鼠标黏贴的改变都能及时监听到变化  
propertychange，只要当前对象属性发生改变。

<h3 id='23'>23. jQuery 中 data() 引发的错误</h3>

#### 详情描述
jQuery 中 data()解释为可以获取、设置元素自定义的属性，但是尽量不用data()方法去获取元素的自定义属性；因为会引发一些隐形错误；
1. 只能获取到第一次赋值的属性，之后通过修改的值获取不到；
2. 如果值是string类型的数字，比如“123”，获取的时候会强转为number，123；
3. 所以建议还是使用 $("div").attr() 的方法去获取

<h3 id='22'>22. js打开新页面的几种方式</h3>

#### 详情描述
1. window.location.href=goUrl;
2. window.open(goUrl,"_self");
3. location.replace(goUrl);
4. location.assign(goUrl);

<h3 id='21'>21. 跨域的方式</h3>

#### 详情描述

具体详情见微信朋友圈
1. jsonp，动态创建script标签，scr设置为需要跨域的域名，加callback回掉函数参数。但是支持get请求，且必须后台支持jsonp跨域；
2. document.domain	设置相同的doncument.domain，动态创建一个隐藏的iframe来跨域；
3. window.name 这个全局属性主要是用来获取和这只窗口名称，但是通过结合ifame也可以跨域获取数据。
4. window.postMessage	 是HTML5新增在window对象上的方法，目的是为了解决在父子页面上通信的问题。该技术有个专有名词；跨文档消息（cross-document messaging）。利用postMessage的特性可以实现较为安全可信的跨域通信。
5. 使用代理服务器跨域；
6. CORS 跨域

<h3 id='20'>20. select 默认选中问题</h3>  

#### 问题描述  

> select 标签会默认选中第一个 option ；但是一般使用的时候不想要默认选中第一个，而是一个空白的选择框
    
#### 解决方案 

1. 给select元素pretend一个 \<option stype="display:none"></option>;
2. 给select元素pretend一个 \<option disabled = "disabled"></option>;

<h3 id='19'>19. 兼容脚本</h3>

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
