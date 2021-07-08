# Crystal 的面试题整理

> 更新说明： 本专题不定期长期更新

## JavaScript部分

1. [什么是函数式编程？ JavaScript的哪些特性使其成为函数式语言的候选语言？](/javascript/什么是函数式编程？%20JavaScript的哪些特性使其成为函数式语言的候选语言？.md)

2. [什么是高阶函数？](/javascript/%E4%BB%80%E4%B9%88%E6%98%AF%E9%AB%98%E9%98%B6%E5%87%BD%E6%95%B0.md)

3. [为什么函数被称为一等公民？](/javascript/为什么函数被称为一等公民.md)

4. [如何检查值是否虚值？](/javascript/如何检查值是否虚值.md)

5. ['use strict' 有什么用？](/javascript/'use%20strict'%20有什么用.md)

6. [描述一下作用域链与原型链](/javascript/描述一下作用域链与原型链.md)

7. [谈谈你是如何理解JS异步编程的](/javascript/%E8%B0%88%E8%B0%88%E4%BD%A0%E6%98%AF%E5%A6%82%E4%BD%95%E7%90%86%E8%A7%A3JS%E5%BC%82%E6%AD%A5%E7%BC%96%E7%A8%8B%E7%9A%84.md)

8. [阅读下面代码，只考虑浏览器环境下的输出结果，写出他们结果打印的先后顺序，并分析出原因](/javascript/08_阅读代码给出结果.md)

   ```js
   const myPromise = () => Promise.resolve('I have resolved')
   function FirstFun() {
   	myPromise().then(res => console.log(res))
   	console.log('first')
   }
   
   async function SecondFun() {
   	console.log('second 1');
   	console.log('second', await myPromise())
   	console.log('second 2');
   }
   
   FirstFun() 
   SecondFun()
   ```

9. [阅读下面代码，我们只考虑浏览器环境下的输出结果，写出它们结果打印的先后顺序，并分析出原因](/javascript/09_阅读代码给出结果.js)

   ```js
   new Promise((resolve, reject) => {
     console.log("A");
     setTimeout(() => {
       console.log("B");
     }, 0);
     console.log("C");
     resolve();
     console.log("D");
   })
     .then(() => {
       console.log("E");
       new Promise((resolve, reject) => {
         console.log("F");
         resolve();
         console.log("G");
       })
         .then(() => {
           setTimeout(() => {
             console.log("H");
           }, 0);
           console.log("I");
         })
         .then(() => {
           console.log("J");
         });
     })
     .then(() => {
       console.log("K");
     });
   
   setTimeout(() => {
     console.log("L");
   }, 0);
   
   new Promise((resolve, reject) => {
     console.log("M");
     resolve();
   }).then(() => {
     setTimeout(() => {
       new Promise((resolve, reject) => {
         console.log("N");
         resolve();
       })
         .then(() => {
           setTimeout(() => {
             console.log("O");
           }, 0);
         })
         .then(() => {
           console.log("P");
         });
     }, 0);
   });
   
   console.log("Q");
   ```

10. [有赞|B站][实现 debounce](/javascript/实现%20debounce.js)

    ```js
    const a = {
      name: 'test-debounce',
      log: debounce(function (a) {
          console.log('test')
          console.log(this.name)
          console.log(a)
      }, 100)
    }
    
    // a.log()
    // a.log(123) /'test' 'test-debounce' 123
    ```

11. [有赞]将一个json数据的所有key从下划线改为驼峰

    ```js
    function mapKeysToCamelCase(data) {
    
    }
    
    const testData = {
      a_bbb_c: 123,
      a_g: [[1], 2, 3, 4],
      a_d: {
          s: 2,
          s_d: 3
      },
      a_f: [1, 2, 3, {
          a_g: 5
      }],
      a_d_s: 1
    }
    // {"aBbbC":123,"aG":[1,2,3,4],"aD":{"s":2,"sD":3},"aF":[1,2,3,{"aG":5}],"aDS":1}
    // console.log(JSON.stringify(mapKeysToCamelCase(testData)))
    ```

12. [有赞]将一天24小时按每半时小划分成48段，我们用一个位图表示选中的时间区间，

    例如110000000000000000000000000000000000000000000000

    表示第一个半小时和第二个半小时被选中了，其余时间段都没有被选中，也就是对应00:00~01:00这个时间区间。

    一个位图中可能有个不连续的时间区间被选中，例如110010000000000000000000000000000000000000000000，

    表示00:00~01:00和02:00~02:30这两个时间区间被选中了。

    写一个timeBitmapToRanges,将上述规则描述的时间位图转挨成一个选中时间区间的数组。

    ```js
    function timeBitmapToRanges(str) {
    
    }
    
    // ['00:00~01:30', '02:00~02:30', '17:30~18:30', '23:30~24:00']
    console.log(timeBitmapToRanges('111010000000000000000000000000000001100000000001'))
    ```

13. 请说一下Promise的内部实现方式

14. [完美世界]请介绍一下消息队列和event loop

15. 如何继承

16. 有哪几种异步解决方案

17. loader中如何写入异步代码

18. 修饰器是什么，是如何工作的

19. [滴滴]说一下js的数据类型，如何判断数据类型

20. [滴滴]如何判断一个对象是否属于某个类

21. [滴滴]说一下防抖函数的应用场景，并简单说下实现方式

22. [滴滴]new Promise构造函数的入参是什么？你在什么场景下会使用promise 

23. [小米]手写翻转二叉树 

24. [小米]说下归并排序的思路和应用场景

25. [小米]说说重绘、重排、回流

26. [小米]说一下V8的垃圾回收机制

27. [跟谁学]commonjs esmodule的区别

28. [跟谁学]闭包实现加法器 

29. [完美世界]object.defineproperty 和 proxy 的区别 

## CSS 部分

1. [小米]说一下css的三个特性并展开说一下应用场景
2. [小米]说一下CSS七层层叠顺序
3. [阿里]z-index的层级关系及css中的层叠上下文
4. [阿里]尽量多的水平垂直居中，分是否已知道父子dom宽高的情况
5. [阿里]如何触发BFC，以及用法和IFC区别
6. [阿里]简单介绍下box-sizing属性 
7. [[阿里]css优先级如何计算](/css/css优先级如何计算.md)
8. [阿里]top、left是相对于padding还是border
9. [阿里]flex布局的使用及在平时中哪些时候会用到 
10. [阿里]display:none和visibility:hidden的区别 
11. [阿里]清除浮动的方法
12. [阿里] ::before和:after中双冒号和单冒号有什么区别 
13. [阿里]1像素边框在移动端的实现
14. [阿里]rem和em区别及使用方法 
15. [阿里]CSS中哪些属性可以继承？ 
16. [阿里]CSS3动画的实现步骤 

## HTTP

1. 说下你知道的HTTP状态码并说出它们的出现场景
2. [腾讯视频]http2.0的优势

## Webpack 部分

1. [请说明webpack打包的原理](./engineering/请说明webpack%20打包的原理.md)
2. webpack的打包流程，ast是什么
3. webpack如何提升打包后的页面性能
4. webpack如何打包多端项目
5. [跟谁学]webpack常用配置项
6. [跟谁学]webpack css-loader 的作用 commonChunk/splitChunk作用点 区别
7. [跟谁学]webpack dll优化效果

## Vue部分

1. Vue是如何实现响应式的
2. [滴滴]vue的设计核心思想是什么
3. [滴滴]说下vue的双向数据绑定的实现原理
4. [小米]vue的源码是否看过，说一下比较有收获的几个点
5. [小米]说一下VUE3.0比VUE2.0做了哪些改动
6. [腾讯视频]vue响应式实现$nexttick实现
7. [完美世界]vuex 中的 mutations 和 actions 的区别 
8. [完美世界]vue 中跨组件通信的实现方案
9. [完美世界]vue 中事件总线的实现（发布订阅模式）

## React部分

1. [跟谁学]为什么选择react/vue 及二者差别
2. [跟谁学]react-router实现原理 hash/history 如何跳转不刷新 ngnix如何配置跨域
3. [跟谁学]purecomponent优势
4. [腾讯视频]react setState 实现
5. [B站]react fiber算法原理及实现
6. [B站]react 子组件与父组件如何通信
7. [B站]react 怎么根据 state 和 props 的变化去更新 dom 树的

## 小程序

1. 小程序有几个线程，分别是做什么的
2. 有没有考虑过为什么一个小程序页面需要4个文件
3. H5如何拿取小程序登录态
4. [滴滴]微信小程序和传统h5页面相比哪个性能更好一些，为什么

## NodeJS

1. nodejs如何使用中间件，在不同的网关添加不同的请求内容。
2. [跟谁学]express/koa区别 

## 性能优化

1. [小米]如何进行前端性能优化
2. [完美世界]首屏白屏的优化方案
3. [完美世界]瀑布屏如何实现，以及如何优化
4. [完美世界]当页面数据非常多，比如一直上拉加载，加载了很多的数据，页面性能会变差，如何优化

## 未分类

1. Jsbridge是如何工作的
2. [滴滴]APP内嵌H5页面如何和APP本身进行通信
3. [滴滴]H5的开发和PC端的开发有什么本质的不同 
4. [滴滴]如何针对H5页面进行远程调试？
5. [滴滴]如何进行手机的页面或者应用的抓包
6. [滴滴]已知公司附近有两个加油站，和一条主干道，要求在24小时内尽可能准确的统计全市有多少台车， 说出你的思路 
7. [小米]说一下从浏览器输入网址到页面渲染中间发生了什么
8. [小米]如何实现一个简单的单点登录
9. [小米]说一下关系数据库和非关系数据库的区别，并说下使用场景
10. [小米]说一下关系数据库外键的使用
11. [小米]说下你知道的设计模式及应用场景
12. [小米]如何用缓存进行前端优化；说下浏览器缓存、DNS缓存、nginx缓存、服务端缓存的区别；强缓存和协商缓存的应用
13. [小米]如何开启GPU加速，GPU加速的作用是什么
14. [小米]是否了解浏览器内核相关技术
15. [小米]说一下jsbridge是如何实现的  
16. [完美世界]题目：两个玻璃小球，从一到一百层中间的某一层落下会碎，不考虑小球的磨损情况，比如说一层落下不会碎，小球不会受到任何伤害，如何最快找出小球破碎的最低层
17. [完美世界]扩展，有很多的小球，题目类似，然后把一到一百层放到一个数组中，数组是乱序，如果最快找出破碎的最低层 
18. [完美世界]题目：一个函数，没有入参，如何实现每次调用返回1到200中的任意一个数，且每次返回的数不重复，如果1到200都被返回过了，就不在返回任何数字
19. [完美世界]百度网盘的下载功能如何实现，浏览器环境，不使用浏览器自带的下载功能，可以暂停，可以继续
20. [完美世界]给定一个整数 N，写一个程序判断是否存在 2 个整数 a、b（a < b），使得 a^2 + b^2 = N，如果存在返回所有的结果



# 资料

- https://www.kancloud.cn/pillys/qianduan/2049476