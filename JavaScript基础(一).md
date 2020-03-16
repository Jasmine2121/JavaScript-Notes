# 40个小时彻底打实JavaScript基础

[TOC]

---

## 1 前端发展史

> [ WEB1.0时代：静态网页 ]
>
> -  1989年，在欧洲粒子物理实验室Tim Berners-Lee（伯纳斯·李）提出：个人计算机上访问大量的科研文献，并建议在文档中**链接其他文档 =>“WEB原型”**
> - 1994年，万维网（W3C）成立，网景推出了第一版Navigator浏览器，HTML也发布了第二代版本，TIM的好基友也设计了CSS...**所以我们把1994年称为“前端历史的起点”**
> - 1995年，网景工程师Brendan Eich花了**10天时间设计了JavaScript语言**，1996年微软发布了JScript（和JS有一些差异），同时拉开了Navigator和Internet Explorer浏览器大战的序幕（到2002年IE完胜，占据全世界96%的市场份额）。

> [ WEB2.0时代：动态网页的崛起 ]
>
> -  1995年之前，JS只用来做一些**简单的DOM修改**，WEB页面都是静态的（显示静态文本和图片）
> - 为了让WEB页面更具备活力（例如：动态展示数据），1995年PHP诞生，1996年JSP诞生，1996年ASP诞生，2002年ASP.NET诞生...这些**服务器端页面技术**实现了WEB页面的动态化，从此WEB2.0时代到来。
>
> 【弊端】
>
> 1. 同步**非异步刷新**    
> 2. 服务器**承受压力过大** 
> 3. **后台开发**的任务量过大（网页制作任务量少）
> 4. 代码过于臃肿，两种角色很难实现同时任务开发

> [ AJAX时代：前后端分离的雏形，异步渲染大显神通 ]
>
> - 在Web最初发展的阶段，前端页面要想获取后台信息需要刷新整个页面，这是很糟糕的用户体验。
> - Google分别在2004年和2005年先后发布了两款重量级的Web产品：Gmail和Google Map。这两款Web产品都大量使用了AJAX技术，不需要刷新页面就可以使得前端与服务器进行网络通信，所以AJAX是一项革命性的技术，颠覆了用户体验。
> - 到2013年/2014年，随着移动端H5的崛起，高性能的WEB体验是重中之重，国内大部分项目都已经改为**“前后端分离”**模式，这也奠定了前端开发二分天下的局面。导致到后期，跨域策略请求方案（JSONP、IFRAME、CORS、DOMAIN、POXY、SCOKET...）以及FETCH等新通信方案不断的崛起。

> [ 前端开发者之殇：浏览器兼容 ]
>
> -    IE在第一次浏览器大战中击败Netscape赢得胜利，垄断了浏览器市场。作为独裁者，IE并不遵循W3C的标准，IE成了事实标准。
> -   2004年11月Firefox发布，之后一路奋起直追，逐渐蚕食IE市场份额，这引发了第二次浏览器战争。2008年12月Chrome浏览器发布，也加入了浏览器大战，由于其优越的处理性能（webkit内核/V8引擎），到2016年，谷歌占据了浏览器市场的半壁江山。
> - 但是浏览器越多，**碎片化问题**也越来越严重，不同的浏览器执行不同的标准，对于开发人员来说这是一个恶梦。
> -    为了解决浏览器兼容性问题，Dojo、jQuery、YUI、ExtJS、等**前端类库**相继诞生。（jQuery独领风骚，几乎成了所有网站的标配，Dojo、YUI、ExtJS等提供了很多组件，让复杂的业务简单化...）

> [ H5崛起：Hybrid混合开发成为主导 ]
>
> - 相比于Native App，移动Web开发成本低、跨平台、发布周期短的优势愈发明显，但是Native App的性能和UI体验要远胜于移动Web（Hybrid技术是结合两者优势）
> - 根据实现原理，Hybrid技术可以分为两大类：
>
>            1. 将HTML5的代码**放到Native App的WebView控件中**运行，典型代表有PhoneGap(Cordova)以及AppCan、Ionic等（微信二次开发）。
>            2. 将HTML5代码针对不同平台**编译成不同的原生应用**，实现了Web开发，Native部署。这一类的典型代表有React Native  / Flutter / uni-app。

> [ NODE崛起：JS成为最热门全栈开发技术 ]
>
> -    2009年，Ryan利用Chrome的V8引擎打造了基于事件循环的异步I/O框架-Node.js诞生。
> - NODE特点：
>   - 基于事件循环的异步I/O框架，能够提高I/O吞吐量；
>   - 单线程运行，能够避免了多线程变量同步的问题；
>   - 使得JS可以编写后台代码，前后端编程语言统一。
> -  2010年1月，NPM作为**Node.js的包管理系统**首次发布。前NPM具有40万左右的模块，是世界上最大的包模块管理系统。

```
[ 第一阶段：HTML（5） + CSS（3）]

​       技术要点：HTML5、CSS3、响应式布局（rem/flex/@media等）、Hybrid混合APP开发、微信二次开发、小程序开发、React Native开发、Flutter、uni-app...
​       特殊说明：Hybrid、微信开发、小程序开发、React Native开发等，这些都需要有JS和框架编程的基础；H5不仅仅是标签，还需要掌握常用的API以及video和audio等，例如：localstorage、webscoket、getCurrentPosition等；     
```

    [ 第二阶段：JS包括ES6核心原理 ]
       JS堆栈内存、闭包作用域、浏览器词法解析（v8渲染机制原理）、面向对象和THIS处理（主要是独立封装组件和插件，研究常用类库的源码）； 
       ES6基础语法（包括class类的继承封装和多态）、ES6中的Promise（及Promise A+规范）、Generator生成器函数等深入用法；
       同步异步编程（包括运行机制和微任务、宏任务，以及实战应用）
       常用的编程思想和设计模式：函数的防抖和节流、柯理化函数、惰性函数、单例设计模式、发布订阅模式、Promise设计模式等
       DOM性能优化（重排和重绘的优化）、DOM事件
       前端编程常规算法：去重、冒泡排序、插入排序、快速排序、递归等     
    [ 第三阶段：AJAX和HTTP ]
       技术要点：ajax原理、ajax异步解决方案（promise）、axios（包括自己封装promise版ajax库）、fetch及封装处理、jquery中的ajax操作和库的封装等
          跨域解决方案及实现原理：jsonp、cors、webpack proxy（scoket.io）、document.domain、window.name+iframe、postMessage等
          HTTP报文（常用的响应请求头实战应用技巧）、HTTP（TCP）传输流程（包括三次握手四次挥手及TCP底层协议）、HTTP1和HTTP2的区别、HTTP和HTTPS的区别等
       特殊说明：HTTP是目前优秀公司重点考察的知识点，因为传统前端代码优化，性能上提高较小，HTTP相关优化手段是性能提高的重要方法（例如：304缓存、DNS缓存、减少HTTP传输次数和大小、HTTPS的加密等），这块是一个重点！    
    [ 第四阶段：框架开发 ]
       技术要点：目前市场上的项目大部分都是框架开发的，所以框架学习非常的重要，目前主流框架是 vue、react、angular，angular现在用的越来越少，一般都是老项目使用这个技术在维护（angular1.0版本居多）
       vue全家桶：vue（MVVM实现的原理以及一些语法实现的原理）、vue-router(HASH路由实现的原理)、vuex（掌握原理）、axios、vue-cli（需要能够修改脚手架的webpack配置项）、iview/vux/vue element等常用框架的使用等
       react全家桶：create-react-app（能够修改webpack的配置项）、react（掌握虚拟DOM渲染原理，掌握DOM-DIFF原理，掌握INDEX索引对比机制，掌握MVC实现的原理）、react-dom/react-native、react-router、react-redux/dva/mobx（掌握原理，自己可以基于原生JS写一套类似的插件、发现里面的一些不足点）、antd（最好可以自己封装一些基础的组件）等

    [ 第五阶段：辅助技能 ]
       技术要点
         Webpack：掌握常用的脚手架使用和修改，会一些基础的webpack搭建
         Git：熟练掌握团队协作开发中代码版本管控技巧，熟悉常用的操作命令
         Node：掌握基础的API、掌握express/koa/egg等框架、可以编写伪API，可以基于node做跨域处理等，有精力的同学可以研究一下数据库操作等
         Canvas：一些公司要求会可视化，需要掌握canvas/webGl/d3等，这个对于数学结构、算法等有一定的要求；这方面不好的，可以先掌握一些基础的操作，掌握echarts的用法等；   
<img src="JavaScript%E5%9F%BA%E7%A1%80(%E4%B8%80).assets/image-20200315200833262.png" alt="image-20200315200833262" style="zoom:80%;" />

<img src="JavaScript%E5%9F%BA%E7%A1%80(%E4%B8%80).assets/image-20200315200932338.png" alt="image-20200315200932338" style="zoom:80%;" />

<img src="JavaScript%E5%9F%BA%E7%A1%80(%E4%B8%80).assets/image-20200315201008562.png" alt="image-20200315201008562" style="zoom:80%;" />

<img src="JavaScript%E5%9F%BA%E7%A1%80(%E4%B8%80).assets/image-20200315201149729.png" alt="image-20200315201149729" style="zoom:80%;" />

前端未来发展预估    
       A：小程序是企业产品的重要组成部分
       B：IOS和安卓开发逐步被淘汰
       C：VR/AI最终转为B端（JS，尤其是webGL、canvas、three.js等是3D虚拟交互的主要实现技术）    
       D：H5游戏/小游戏的热度会提高（白鹭JS引擎）
       E：NODE.JS还会迎来下一个高潮

侵占移动端APP市场

![image-20200315201630324](JavaScript%E5%9F%BA%E7%A1%80(%E4%B8%80).assets/image-20200315201630324.png)

### 1-1服务器渲染时代

![image-20200315201418750](JavaScript%E5%9F%BA%E7%A1%80(%E4%B8%80).assets/image-20200315201418750.png)

### 1-2客户端渲染时代

![image-20200315201520682](JavaScript%E5%9F%BA%E7%A1%80(%E4%B8%80).assets/image-20200315201520682.png)

### 1-3需要掌握的技术栈



---

## 2 浏览器内核和控制台

<img src="https://i.loli.net/2020/03/14/gVO61mGedCDM58Q.png" alt="image-20200314125732767.png" style="zoom:33%;" /> 				 <img src="https://i.loli.net/2020/03/14/Mc5JeG6bLnXFZRS.png" alt="image-20200314130923128.png" style="zoom:33%;" />

### 2-1谷歌浏览器控制台（F12/Fn+F12）

- Elements: 查看结构样式，可以修改这些内容
- Console: 查看输出结果和报错信息，是JS调试的利器
- Sources: 查看项目源码
- Network: 查看当前网站所有资源的请求信息（包括和服务器传输的HTTP报文信息）、加载时间等（根据加载时间进行项目优化）
- Application: 查看当前网站数据存储和资源文件
  - Manifest：离线缓存
  - Service Workers:
  - Clear Storage:
- Storage: 本地存储（进行存储优化）<img src="https://i.loli.net/2020/03/14/2EZNauLGcHxRWqo.png" alt="image-20200314133044331.png" style="zoom:33%;" />
- Cookies: <img src="https://i.loli.net/2020/03/14/jPSwkRpcVd4Nfm6.png" alt="image-20200314143338701.png" style="zoom:33%;" />
- Frames: 重点，网页图片都在这 <img src="https://i.loli.net/2020/03/14/SMhtyBr6xOA1JQq.png" alt="image-20200314143554305.png" style="zoom:33%;" />



---

## 3 JS基础知识（一）

### 3-1 JS的组成和变量

> <img src="https://i.loli.net/2020/03/14/bsxt1U7Z9HKuY6p.png" alt="image-20200314144118469.png" style="zoom: 67%;" />

页面刷新

<img src="https://i.loli.net/2020/03/14/eDjPl9AwFGZaJHp.png" alt="image-20200314150403401.png" style="zoom:80%;" />  


### 3-2 创建变量的几种方式
```javascript
	//ES3
	var a = 12;
	console.log(a);//=>输出的是a代表的值12
	
	//ES6
	let b = 100;//var 和 let 的区别以后再说
	b = 200；
	
	const c = 1000;
	c= 2000; //->报错：CONST创建的变量，存储的值不能被修改（可以理解为常量）

	//创建函数也相当于在创建变量
	function fn(){}
	//创建类也相当于创建变量
	class A{}
	//ES6的模块导入也可以创建变量
	import B from './B.js';
	//Symbol创建唯一值
	let n =Symbol(100);
	let m =Symbol(100);
	n==m
	false//因为创建的是唯一值
	
```

### 3-3 JS命名规范

> <img src="https://i.loli.net/2020/03/14/CEfgOryc27m9NoK.png" alt="image-20200314161837773.png" style="zoom: 50%;" />

- 严格区分大小写
```javascript
let Test = 100;
console.log(test)//无法输出，因为第一个字母小写了
```

- 使用数字、字母、下划线、$，数字不能作为开头

```javascript
let $box;//一般用JQ获取的以$开头
let _box;//一般公共变量都是_开头
let 1box;//不可以，但是可以box1
```

- 使用驼峰命名法：首字母小写，其余每个有意义的单词首字母大写

```javascript
let studentInformation;
let studentInfo
//常用缩写：add/insert/create/new(新增)/update(修改)/delete(删除)/del/remove/rm/sel/select/query/get(查询)/info(信息)

//不正确
let xueshengInfo;
let xueshengxinxi;
let xsxx;
```

- 不能使用关键字和保留字

```javascript
//当下有特殊含义的是关键字，未来可能成为关键字的叫保留字
var let const function ...

var var = 10 //不行
var var10 = 10 //不行
var _var = 10 //不行
```


### 3-4 JS中的数据类型分类

> <img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314172335856.png" alt="image-20200314172335856" style="zoom:80%;" />

- 基本数据类型
  - 数字number：常规数字和NaN
  - 字符串string：所有用单引号、双引号、反引号包起来的都叫字符串
  - 布尔boolean：TRUE/FALSE
  - 空对象指针null
  - 未定义undefined
- 引用数据类型
  - 对象数据类型object
    - { }普通对象
    - [ ]数组对象
    - /^[+-]?(\d|[1-9]\d+))(\.\d+)?$/ 正则对象
    - Math数学函数对象
    - 日期对象
    - ...
  - 函数数据类型function

### 3-5 NUMBER数字数据类型详解

> 包含：常规数字、NaN(Not a number)
>
> 一个叹号Enter

```javascript
//console.log([val]):在控制台输出内容
console.log('hello world~')
//==:进行比较
console.log('AA' == NaN);//False
console.log(10 == NaN);//False
//NaN 和任何值都不相等，和他自己也不相等
```

- isNaN——检测一个值是否为非有效数字，如果不是有效数字返回True，反之是有效数字，则为FALSE

```javascript
//isNaN([val])参数描述占位符（就是占一个值就没了）
console.log(isNaN(10));//False，是有效数字
console.log(isNaN('AA'));//True,不是有效数字

//isNaN有一个机制：首先会验证检测的值是否为数字，如果不是，先基于Number()这个方法，把值转化为数字类型，然后再检测
console.log(isNaN('10'));//False，是有效数字
/*
	Number('10')//10
	isNaN(10)//False
*/
```

```javascript
//-----------String----to----number-----------
//只要字符串转化为数字，只要字符串中包含任意一个非有效数字，第一个点除外，结果都是NaN
console.log(Number('12.5'));//12.5
console.log(Number('12.5px'));//NaN
console.log(Number('12.5.5'));//NaN
console.log(Number(''));//0,注意不是空格，是空字符串

//----------Boolean----to----number------------
console.log(Number('true'));//1
console.log(Number('false'));//0
console.log(Number(true));//1，低层机制

//-----isNaN总是要先转化成有效数字再判断-----
console.log(isNaN(false));//False
console.log(isNaN(true));//False

//--------Number()函数------null-----undefined--------
console.log(Number(null));//0，空指针转化成0
console.log(Number(undefined));//NaN，没有赋值就NaN

//把引用数据类型转化为数字时先把他基于toString方法转化为字符串，然后再转化为数字
console.log(Number({}));//普通对象,NaN
console.log(Number({name:'10'}));//NaN,转化不成数字
console.log(Number({name:'xxx'}));//NaN

console.log(Number([]));//数组对象,0
console.log(Number([12]));//12
console.log(Number([12,13]));//NaN

//正则也是NaN
```

<img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314190657920.png" alt="image-20200314190657920" style="zoom:50%;" /> 之后会讲 	<img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314190906440.png" alt="image-20200314190906440" style="zoom:67%;" /> 

```javascript
let str = '12.5px';
console.log(Number(str));//NaN
console.log(parseInt(str));//12
console.log(parseFloat(str));//12.5
console.log(parseFloat('width:12.5px'));//NaN
```

- parseInt/parseFloat([val],[进制])：也是转化为数字的方法，从左到右依次查找有效数字字符，直到遇到非有效数字字符，停止查找(不管后面是否还有数字，都不找了)，就把找到的当做数字返回，没有就NaN

- ==进行比较的时候，也会转化为数字

### 3-6 关于Number和Parsefloat的一点补充

<img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314192727106.png" alt="image-20200314192727106" style="zoom: 50%;" /> Number低层机制，parseFloat不一样**先转化为字符串'true'再一个个找**

### 3-7 STRING字符串数据类型详解

> 所有用单引号、双引号、反引号（撇 ES6模板字符串）包起来的都是字符串

#### 3-7-1把其他类型值转化为字符串

- [val].toString( )
- 字符串拼接

 ```html
//html导入.js文件
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>XXXXXX</title>       
    </head>
    <body>
        <script src="js/XXX.js"> </script>
    </body>
</html>

 ```

```js
console.log(12.toString())//会报错

let a = 12;
console.log(a.toString())//'12'
console.log((NaN).toString())//NaN
console.log((true).toString())//"true"
//null,undefined 都禁止直接toString的,结果还是有的，但是浏览器把它禁止了，保护起来不能用
```

<img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314194603177.png" alt="image-20200314194603177" style="zoom:67%;" />          —— <img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314194649320.png" alt="image-20200314194649320" style="zoom:67%;" /> 

<img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314194810138.png" alt="image-20200314194810138" style="zoom:80%;" /> 

注意：除了普通对象&大括号,其他遇到字符串拼接直接拼接，而不是变成上图[object,object]

#### 3-7-2字符串拼接

```javascript
//四则运算，只有加法可能存在字符串拼接，一旦遇到字符串，就不是数学运算，而是字符串拼接
console.log('10' + 10);//'1010'
console.log('10' - 10);//0
console.log('10px' - 10);//NaN-10,也变得不正常了，所以NaN
```

###### 面试题

```javascript
let a = 10 + null + true + [] + undefined + '美丽' + null + [] + 10 +false;
console.log(a);//空数组先要变为字符串

```

<img src="40%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%BD%BB%E5%BA%95%E6%89%93%E5%AE%9EJavaScript%E5%9F%BA%E7%A1%80.assets/image-20200314200800107.png" alt="image-20200314200800107" style="zoom:67%;" /> 

### 3-8 BOOLEAN布尔数据类型详解

#### 3-8-1数据类型定义

- 只有两个值： true/false

#### 3-8-2转换

- 只有0、NaN、' '、null、undefined 五个值转化为FALSE，其他都转化为TRUE（而且**没有任何特殊情况**）

#### 3-8-3最常用三种表现方式

- Boolean([val])
- !/!!
- 条件判断

```javascript
//Boolean([val])
console.log(Boolean(0));//False
console.log(Boolean(''));//False
console.log(Boolean(' '));//True
console.log(Boolean(null));//False
console.log(Boolean(undefined));//False
console.log(Boolean([]));//True
console.log(Boolean([12]));//True
console.log(Boolean(-1));//True
```

```javascript
//!/!!
// ! : 取反(先转为布尔，然后取反)
console.log(!1);//False
//!!:取反再取反，但是变成了布尔,等价于Boolean
console.log(!!1);//True
```

```javascript
//条件判断
//如果条件是一个值，不是==、===、!=、>=等这些比较，是要先把这个值转换成布尔，然后验证真假
if(1){
    console.log('哈哈');//条件成立，输出哈哈
}
if('3px' + 3){
    //=>'3px3'
    console.log('哈哈');//会输出
}
if('3px' - 3){
    //NaN-3=>NaN
    console.log('哈哈');//不会输出
}
```

### 3-9 null和undefined的区别

> 难理解
>
> 都代表没有

- null ：意料之中(一般都是开始不知道值，我们手动先设置null，后期再给值操作)

```javascript
let num = null;//let num = 0(零有空间，null没有空间),一般最好用null作为初始的空值，因为0不是空值，在栈内存中有自己的存储空间(占了位置)
...
num = 12;
```

- undefined：意料之外(不是我能决定的)

```javascript
let num;//创建一个变量没有赋值，默认值是undefined
...
num = 12;
```

### 3-10 对象数据类型的基本结构及操作

<img src="JavaScript%E5%9F%BA%E7%A1%80.assets/image-20200315190036029.png" alt="image-20200315190036029" style="zoom:80%;" /> 

#### 3-10-1object对象数据类型——普通对象

数组是特殊的对象

> {[key]:[value],...}任何一个对象都是**由零到多组键值对(**属性名：属性值)组成的。(并且属性名不能重复)

```javascript
let person={
	name:'孙胜完',
	age:25,
	height:'168CM',
	weight:'48KG',
    1:100
};

//设置属性名属性值
person.GF='远远';
person.name='孙完';//=>孙完
//属性名不能重复，如果属性名已经存在，不属于新增，而属于修改属性值
console.log(person['GF']);
console.log(person['name']);

//获取属性名对应的属性值
//对象.属性名
//对象[属性名]——属性名是数字或字符串格式的
console.log(person.name);//孙胜完
console.log(person['age']);//25

//如果当前属性名不存在，默认属性值是undefined
console.log(person.sex);//undefined

//如果属性名是数字，则不能使用点的方式获取属性
console.log(person[1]);//100
console.log(person.1);//SyntaxError:语法错误

//删除属性
//=>真删除：把属性彻底干掉
delete person[1];//数字只能用中括号
delete person(person.name);//格式错了

------------------------------------------------------------
delete person.name;
console.log(person.name);// undefined
最有效的方式，应该是将不需要的属性设置为 undefined
person.name = undefined; // 删除 name 属性
也可以考虑使用 Spread Operator for objects
const omit = (prop, { [prop]: _, ...rest }) => rest;
const newObj = omit('name', person); // 删除 name 属性
------------------------------------------------------------
 
//=>假删除：属性还在，值为空
person.weight = null;//person.weight = undefined;也可以
console,log(person);
```





