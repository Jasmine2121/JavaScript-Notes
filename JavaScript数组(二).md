# JavaScript数组

[TOC]

## 4 数组

### 4-1 数组的基本结构

数组是特殊的对象类型

```javascript
let ary = [];//空数组
let ary = [12,'哈哈',true,13];
console.log(ary);
//属性名从0开始，也叫索引
```

<img src="JavaScript%E6%95%B0%E7%BB%84.assets/image-20200315192931292.png" alt="image-20200315192931292" style="zoom:67%;" /> 属性名+属性值

数组是特殊的对象，因为：

- 我们中括号中设置的是属性值
- 属性名默认生成数字，从0开始递增
- 数字代表每一项的位置，叫做"索引"=>
- 什么是索引？从0开始，连续递增，代表每一项位置数字属性名
- 天生默认一个属性名length，**存储数组的长度**

```javascript
console.log(ary.length);
console.log(ary['length']);
//属性名要不是数字就是字符串

console.log(ary[1]);//输出哈哈
//第一项索引0，最后一项索引 ary.length-1
console.log(ary[0]);//12
console.log(ary[ary.length-1]);//最后一项

//向数组末尾增加内容
ary[ary.length] = 100;
console.log(ary);
```

### 4-2 数据类型的区别（堆栈底层机制）

#### 4-2-1 JS中常用数据类型

<img src="JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/20200303191514898.png" alt="img" style="zoom:80%;" />

<img src="JavaScript%E6%95%B0%E7%BB%84.assets/image-20200315194233601.png" alt="image-20200315194233601" style="zoom:67%;" /> 

```javascript
let a = 12;
let b = a;
b = 13;
console.log(a);//12

let n = {
    name:'孙完'
};
let m = n;
m.name = 'Wani';
console.log(n.name);

```

#### 4-2-2浏览器渲染机制

> 浏览器想要执行JS代码：
>
> 1. 从电脑内存中**分配出一块内存**，用来执行代码( 栈内存 => Stack )
> 2. 分配一个**主线程**，用来自上而下执行JS代码
>

![image-20200316080730289](JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/image-20200316080730289.png)

#### 4-2-3 堆栈内存课堂练习题

```javascript
let n = [10,20];
let m = n;
let x = m;
m[0] = 100;
x = [30,40];
x[0] = 200;
m = x;
m[1] = 300;
n[2] = 400;
console.log(n,m,x);

//10,20
//200,300
//200,40

//n=>[100,20,400]
//m=>[200,300]
//x=>[200,300]
```

![image-20200316082623520](JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/image-20200316082623520.png)

### 4-3 阿里的一道引发血案的面试题

#### 4-3-1阿里很难进的哦

```javascript
let a = {
    n: 1
};
let b = a;
a.x = a = {
    n: 2
};

console.log(a.x);
console.log(b);

//[1,2]
//[1]
```

![image-20200316083835123](JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/image-20200316083835123.png)

> 栈内存：执行代码，存储变量和基本类型值

```javascript
let a = {n:1};
let b = a;
a.x = b;

//堆的内存嵌套
//堆的无限溢出
```

<img src="JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/image-20200316084750400.png" alt="image-20200316084750400" style="zoom: 50%;" /> 

#### 4-3-2扩展题

1. 浏览器常用的输出方式，除了console.log还有哪些？

   **1.console.log**

   console.log(object[, object, ...])
   在控制台输出一条消息。如果有多个参数，输出时**会用空格隔开**这些参数。

   第一个参数可以是一个包含**格式化占位符输出**的字符串，例如：

   ```javascript
   console.log("The %s jumped over %d tall buildings", animal, count);
   ```

   上面的例子可以用下面的**无格式化占位符输出**的代码替换：

   ```javascript
   console.log("The", animal, "jumped over", count, "tall buildings");
   ```

   并且，这两种方式**是可以组合使用**的。如果使用了格式化占位符，而提供的参数的个数多于占位符的个数，那么，**多余的参数会以空格分隔的方式附加**在字符串后面，就像：

   ```javascript
   console.log("I am %s and I have:", myName, thing1, thing2, thing3);
   ```

   如果参数是一个**Javascript对象**，那么在控制台输出的就不是静态文字，而是一个可交互的超链接，点击超链接可以查看该对象的HTML, CSS, Script, DOM窗口，可用格式化字符串**%o代替Javascript对象**。

   ```javascript
   console.log("Body tag is %o", document.body); 
   ```

   格式化字符串列表：

   | 格式化字符串 | 类型                      |
   | ------------ | ------------------------- |
   | %s           | 字符串                    |
   | %d, %i       | 整型（暂不支持数字型）    |
   | %f           | 浮点型 （暂不支持数字型） |
   | %o           | 链接对象                  |

   **2.其他级别，debug、warn、error、assert等**

   ```javascript
   console.debug(object[, object, ...])
   ```

   在控制台输出一条消息，包含一个指向代码调用位置的超链接。假如是**直接在控制台输入该命令，就不会出现超链接**（和console.log()一样）。

   ```javascript
   console.info(object[, object, ...])
   ```


   在控制台输出一条带有**“信息”**图标的消息和一个指向代码调用位置的超链接。

   ```javascript
   console.warn(object[, object, ...])
   ```


   在控制台输出一条带有**“警告”**图标的消息和一个指向代码调用位置的超链接。

   ```
   console.error(object[, object, ...])
   ```


   在控制台输出一条带有**“错误”**图标的消息和一个指向代码调用位置的超链接。

   ```
   console.assert(expression[, object, ...])
   ```


   测试表达式expression是否为真。**如果不是真**，会在控制台写一条消息并抛出异常

   ```
   console.dir(object)
   ```


   以**列表形式**输出一个对象的所有属性，有点和你查看DOM窗口相类似。

   ```
   console.dirxml(node)
   ```


   输出一个HTML或者XML元素的**XML源代码**。和你在HTML窗口看到的相似。

   > ```javascript
   > console.trace()
   > ```
   >
   >
   > Prints an interactive stack trace of JavaScript execution at the point where itis called.
   >
   > **The stack trace** details the functions onthe stack, as well as the values that were passed as arguments to eachfunction. You can click each function to take you to its source in the Scripttab, and click each argument value to inspect it in the DOM or HTML tabs.

   ```
   console.group(object[, object, ...])
   ```

   输出一条消息，并打开一个嵌套块，块中的内容都会缩进。

   调用console.groupEnd()关闭块。该命令可以嵌套使用。

   ```
   console.groupEnd()
   ```


   关闭最近一个由console.group打开的块。

   ```
   console.time(name)
   ```


   创建一个名字为name的计时器，调用console.timeEnd(name)停止计时器并输出所耗时间（毫秒）。

   ```
   console.timeEnd(nam）
   ```

2. [<script>]标签放到页面头部和尾部的区别，以及解决办法？

   

### 4-4 数据类型检测

> !和html5按Enter键也可以

> //包含东西才叫正则

---

- typeof 运算符，不是一种方法
  - typeof [val] ：用来检测数据类型的运算符
- instanceof ：用来检测当前实例是否属于某个类
- constructor ： 基于构造函数检测数据类型（也是基于类的方式）
- Object.prototype.toString.call( ) ：检测数据类型的最好办法

---

```javascript
console.log(typeof 1);
/*
  基于typeof检测出来的结果:
	1.首先是一个字符串
	2.字符串中包含对应的类型
*/

console.log(typeof 1);
let a = NaN;
console.log(typeof a);//=>'number'
//蓝色数字，黑色字符串

console.log(typeof '12');//=>"String"

//undefined还是undefined,NaN是number
```

<img src="JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/image-20200316090942325.png" alt="image-20200316090942325" style="zoom:80%;" /> <img src="JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/image-20200316091428162.png" alt="image-20200316091428162" style="zoom:67%;" />  

**局限性**：

1. typeof null =》"object" **但null并不是对象**
2. 基于typeof**无法细分**出当前值是普通对象还是数组对象，因为只要是对象数据类型，返回的值都是"object"

```javascript
console.log(typeof typeof typeof[]);

//=>typeof [] => "object"
//typerof "object" => "string"
//因为typeof检测的结果都是字符串，因此只有两个及以上同时检测，最后必然是"string"
```

### 4-5 一小时掌握三种常用的判断

#### 4-5-1 JS中操作语句：判断、循环

> 条件成立做什么？不成立做什么？
>
> - if/else if/else
> - 三元运算符
> - switch case

1. if/else

```javascript
if(条件){
	条件成立执行
}else if(条件2){
	条件2成立执行
}
...
else{
	以上条件都不成立
}
```

```javascript
let a = 10;
if(a<=0){
    //如果上面条件为(a>=0),直接输出哈哈，后面不执行
    console.log('哈哈');
}else if(a>0 && a <10){
    //A && B:A和B都成立才为TRUE
    //A || B:A或者B一个成立就TRUE
    console.log('呵呵');
}else if(a == 10){
    //赋值=的操作恒成立，==才是等于
    console.log('嘿嘿');
}else{
    console.log('嘻嘻');
}
```

2. 三元运算符

```javascript
//条件可以多样性：大于小于等于的比较、一个值或取反
//最后都是要计算出TRUE还是FLASE

let a = 10;
if(a>=10){
    console.log('1');
}else{
    console.log('2');
}

//------------三元运算符：简单IF/ELSE的特殊处理方式--------------
let a = 10;
//条件?条件成立处理的事情:条件不成立处理的事情
a>=10 ? console.log('1') : console.log('2');


//1.如果处理的事情比较多，我们可以用括号包起来，每一件事情用逗号分隔
//2.如果不需要处理事情，可以用null、undefined占位
let a = 10;
if(a> 0 && a < 20){
    a++;//=>a+=1  a=a+1  =>自身累加1
    console.log(a);
}
//不成立啥都没干——null,多个事件逗号隔开
a> 0 && a < 20?( a++,console.log(a)) : null;

```

```javascript
a>0 ? a++: a+=2
//先看最外层
a > 0 ? (a < 10 ? a++ : a--) : (a > -10 ? a+=2 : null);
//所以简单的才用三元运算符
//void:0就是undefined
```

<img src="JavaScript%E6%95%B0%E7%BB%84(%E4%BA%8C).assets/image-20200316111953045.png" alt="image-20200316111953045" style="zoom:67%;" /> 

3. switch case

```javascript
let a = 10;
if(a==1){
    console.log('1');
}else if(a==5){
    console.log('2');
}else if(a==10){
    console.log('3');
}else{
    console.log('4');
}
//一个变量在不同值情况下的不同操作
//1.每一种情况结束最好都加上break
//2.default等价于else，以上都不成立干的事情
//3.每一种case情况的比较都用的是==="绝对相等"
switch(a){
    case 1:
        console.log('1');
        break;
    case 5:
        console.log('2');
        break;
    case 10:
        console.log('3');
        break;
    default:
        console.log('4');
}
//不加break，后面不管成立不成立都会执行，直到遇到break
//不加break也可以，实现变量在某些值的情况下做相同的事情

//'5' => 5 字符串先转换为数字
// case 5 ,此处'5' case 5 => FALSE
```

4. == VS ===

== ：相等(如果左右两边数据值类型不同，默认先转化为相同的类型，然后比较)

'5'==5 =>TRUE

=== ：绝对相等(如果类型不同，肯定不相同，不会默认转换数据类型)

'5'===5 =>FALSE

项目中为了保证业务的严谨，推荐使用===

### 4-6珠峰扩展题答案

**1. 浏览器常用的输出方式，除了console.log还有哪些？**

| 方式                 | 含义                                                         |
| -------------------- | ------------------------------------------------------------ |
| alert                | 普通弹框(默认调用 toString 方法将参数序列化)                 |
| console.log          | 打印参数日志                                                 |
| console.dir          | 打印参数详细信息                                             |
| console.table        | 以表格的形式打印                                             |
| console.warn         | 打印参数的警告信息                                           |
| console.info         | 打印参数信息                                                 |
| console.error        | 打印参数的错误信息                                           |
| confirm              | 带有确定和取消的弹框,返回值:确定返回 true,取消返回false      |
| prompt               | 在confirm基础上给用户选填原因;返回值:未填返回 null, 填写返回填写信息 |
| console.time/timeEnd | 中间的程序代码执行所消耗的时间                               |
| .vaule               | js 动态表单插值                                              |
| innerText            | dom 元素内插入文本值                                         |
| innerHTML            | dom 元素内插入文本值或者 dom 节点                            |
| appendChild          | 在父元素下最后一个子节点后面追加一个 dom “碎片”              |
| insertBefore         | 在父元素下给定子节点之前追加一个 dom “碎片”                  |

2. **< script > 标签放到页面头部和尾部的区别，以及解决办法 ？**

- <script> 标签放在头部和尾部的异同 :

  - **同 : 不论 <script> 标签在 头部 或者 尾部 都会阻塞页面的渲染。**

  - 异 : 

    - 放在头部不仅阻塞**页面解析**而且还会阻塞页面的渲染,

    - 而放在 尾部 **不会阻塞页面的解析**仅仅会阻塞页面的渲染。

      所以这就导致一个问题 : 如果在头部执行脚本的时候去获取某个 dom 节点, 但是 js 已经阻塞了页面的解析, dom 结构还未解析就去获取结果会抛出异常, 脚本放在尾部就不会有这个问题, 因为在尾部执行脚本不会阻塞页面的解析仅会阻塞渲染, 所以使不耽误获取 dom 节点的。

- 解决方案 :
  (1)在 尾部 执行脚本

> <body>
>
> <script src="Xxx.js"></script>
>
> </body>

​		(2)在 头部 执行脚本的时候, 脚本代码用 `window.onload = function(){}` 包裹。

> <head>
>     <script>
> 	window.onload = function() {
> 		// code ...
> 	};
> 	</script>
> </head>

​		(3)在 头部 执行脚本的时候使用 script 标签的 defer 属性来更改脚本的执行时机。

> <head>
>     <script src="Xxx.js" defer></script>
> </head>

这样脚本就会在页面结构解析完毕后再执行脚本。

### 4-7 基于CSS实现鼠标滑过显示详情

```html
!
```









### 4-8 基于JS实现点击切换效果

### 4-9 彻底掌握FOR循环

### 4-10 判断逻辑的案例练习（判断数字正负）

### 4-11 元素对象的深一层理解（堆栈）

### 4-12 实现奇偶行变色

### 4-13 鼠标滑过变颜色（未完成，留作思考）


