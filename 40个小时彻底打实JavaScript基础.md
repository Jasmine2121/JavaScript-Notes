---
typora-copy-images-to: ..\JavaScript基础\图片笔记
---

# 40个小时彻底打实JavaScript基础



---

## 1 前端发展史

### 1-1服务器渲染时代



### 1-2客户端渲染时代



### 1-3需要掌握的技术栈



---

## 2 浏览器内核和控制台

<img src="T:\JavaScript基础\图片笔记\gVO61mGedCDM58Q.png" alt="image-20200314125732767.png" style="zoom:33%;" /> 				 <img src="T:\JavaScript基础\图片笔记\Mc5JeG6bLnXFZRS.png" alt="image-20200314130923128.png" style="zoom: 33%;" /> 

### 2-1谷歌浏览器控制台（F12/Fn+F12）

- Elements: 查看结构样式，可以修改这些内容
- Console: 查看输出结果和报错信息，是JS调试的利器
- Sources: 查看项目源码
- Network: 查看当前网站所有资源的请求信息（包括和服务器传输的HTTP报文信息）、加载时间等（根据加载时间进行项目优化）
- Application: 查看当前网站数据存储和资源文件
  - Manifest：离线缓存
  - Service Workers:
  - Clear Storage:
- Storage: 本地存储（进行存储优化）<img src="T:\JavaScript基础\图片笔记\2EZNauLGcHxRWqo.png" alt="image-20200314133044331.png" style="zoom:33%;" />
- Cookies: <img src="T:\JavaScript基础\图片笔记\jPSwkRpcVd4Nfm6.png" alt="image-20200314143338701.png" style="zoom:33%;" />
- Frames: 重点，网页图片都在这 <img src="T:\JavaScript基础\图片笔记\SMhtyBr6xOA1JQq.png" alt="image-20200314143554305.png" style="zoom:33%;" />



---

## 3 JS基础知识（一）

### 3-1 JS的组成和变量

<img src="T:\JavaScript基础\图片笔记\bsxt1U7Z9HKuY6p.png" alt="image-20200314144118469.png" style="zoom:67%;" />

页面刷新

<img src="T:\JavaScript基础\图片笔记\eDjPl9AwFGZaJHp.png" alt="image-20200314150403401.png" style="zoom:80%;" />  


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

<img src="T:\JavaScript基础\图片笔记\CEfgOryc27m9NoK.png" alt="image-20200314161837773.png" style="zoom:80%;" />

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
```




### 3-4 JS中的数据类型分类



### 3-5 NUMBER数字数据类型详解



### 3-6 关于Number和Parsefloat的一点补充

P1515-STRING字符串数据类型详解
P1616-BOOLEAN布尔数据类型详解
P1717-null和undefined的区别
P1818-对象数据类型的基本结构及操作



## 4 数组

### 4-1 数组的基本结构（特殊对象类型）

P5656-数组常用方法1（增删改操作）
P5757-数组常用方法2（slice）
P5858-数组常用方法3（join、concat、indexOf等）
P5959-数组常用方法4（reverse、sort）
P6060-数组常用方案5（forEach）
P6161-数组去重比较LOW的两个方法（数组塌陷问题）
P6262-数组去重比较优秀的方式（基于对象处理）
P6363-其它实现数组去重的方式



## 5 函数

### 5-1 函数的基础概念（用洗衣机模型理解函数）



P3333-函数基础语法和形参的细节知识
P3434-函数中的返回值
P3535-匿名函数
P3636-选项卡案例的样式
P3737-选项卡JS部分（但是实现不了）
P3838-分析不行的原因和设置解决方案



## 6 综合复习

### 6-1一周综合复习1（基础知识）





P4040-一周综合复习2（浏览器常用的输出方式）
P4141-一周综合复习3（SCRIPT位置问题）
P4242-一周综合复习4（部分练习题讲解）
P4343-一周综合复习5（部分练习题讲解）
P4444-一周综合复习6（判断循环等知识）
P4545-一周综合复习7（i++和++i的细节知识）
P4646-一周综合复习8（切换颜色的两种办法）
P4747-一周综合复习9（变态的基础知识练习）
P4848-一周综合复习10（逻辑思维判断题）







## 7 JS基础知识（二）

### 7-1 变量和属性名区别以及FOR IN循环（网络出现故障）



P5050-隔行变色和自定义属性的再一次理解
P5151-函数的底层运行机制
P5252-基于一个案例进一步理解自定义属性方式
P5353-函数中的ARGUMENTS（任意数求和）
P5454-初窥ES6中的箭头函数
P5555-Math数学函数中常用的方法



P2020-数据类型的区别（堆栈底层机制）
P2121-堆栈内存课堂练习题
P2222-阿里的一道引发血案的面试题
P2323-数据类型检测
P2424-一小时掌握三种常用的判断
P2525-基于CSS实现鼠标滑过显示详情
P2626-基于JS实现点击切换效果
P2727-彻底掌握FOR循环
P2828-判断逻辑的案例练习（判断数字正负）
P2929-元素对象的深一层理解（堆栈）
P3030-实现奇偶行变色
P3131-鼠标滑过变颜色（未完成，留作思考）





P6464-字符串中常用的方法
P6565-时间字符串的格式化处理
P6666-queryURLParams
P6767-实现四位随机验证码
P6868-日期函数及时钟案例
P6969-格式化时间字符串处理
P7070-获取DOM元素的九种方式
P7171-获取元素方法的简单描述
P7272-节点和节点之间的关系属性
P7373-节点的简单应用（封装JQ中的children和prev等）
P7474-对元素的增加、删除、克隆等操作
P7575-设置自定义属性的其它方式