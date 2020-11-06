# Vue讲解

## 1.Vue.js特性简介

### 什么是Vue.js

 Vue是一套用于构建用户界面的渐进式JavaScript框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，方便与第三方库或既有项目整合。 

Vue.js是一个**渐进式框架**，什么是渐进式？

- 渐进式意味着你可以将Vue作为你应用的一部分嵌入其中，带来更丰富的交互体验。
- 如果你希望将更多的业务逻辑适用Vue实现，那么Vue有成熟，稳定的核心库和生态系统。
- Core+Vue-router+Vuex可以满足你各种各样的需求。

 Vue的目标：通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件 。

Vue的特点：

1.  在有HTML+CSS +JavaScript的基础上，快速上手。 
2.  简单小巧的核心，渐进式技术栈，足以应付任何规模的应用。 
3.  20kb min+gzip 运行大小、超快虚拟 DOM，最省心的优化。 
4.  双向数据绑定，让开发者不用在去操作dom对象，把更多的精力放在业务逻辑上。

**Vue官网**：https://cn.vuejs.org/

Vue的安装和使用：

- 方式一：CDN的引入  例如：==<script type="text/javascript" src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>==

- 方式二：下载和引入

  			下载好js文件后，在使用的时候直接引入本地的js文件。

  - 开发环境   https://vuejs.org/js/vue.js
  - 生产环境   https://vuejs.org/js/vue.min.js

- NPM下载

  - 使用node.js安装

### Vue的mvvm实现

vue中的MVVM模式即Model-View-ViewModel。 即模型-视图-视图模型。 

View层：视图层，在前端开发中通常就是DOM层，主要作用是给用户展示各种信息。

Model层： 数据可能使我们固定的死数据，更多的是来自我们服务器，从网络上请求下来的数据。 

ViewModel：

- 视图模型层 视图模型层是View和Model沟通的桥梁。 
- 一方面它实现了Data Binding，也就是数据绑定，将Model的改变实时的反应到View中; 
- 另一方面它实现了DOM Listener，也就是DOM监听，当DOM发生一些事件(点击、滚动、touch等)时，可以监听到，并在需要的情况下改变对应的Data。 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029121759905.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


 Vue是以数据为驱动的，Vue自身将DOM和数据进行绑定，一旦创建绑定，DOM和数据将保持同步，每当数据发生变化，DOM会跟着变化。 

优点：

- 低耦合
- 可重用性
- 独立开发
- 可测试

计数器示例

```html
<body>
    <div id="app">
      <p>当前计数{{counter}}</p>
      <button @click="add">+</button>
      <button @click="sub">-</button>
    </div>
<script type="text/javascript" src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
<script>
    new Vue({
        el:"#app",
        data:{
            counter:0
        },
        methods: {
            add(){
                this.counter++;
            },  
            sub(){
                if(this.counter>0){
                    this.counter--;
                }
            }
        },
    })
</script>
</body>
```



### Vue需要的前置ES6知识

**ES6:**	 

[ECMAScript](https://baike.baidu.com/item/ECMAScript/1889420) 6（简称ES6）是于2015年6月正式发布的[JavaScript](https://baike.baidu.com/item/JavaScript/321142)语言的标准，正式名为ECMAScript 2015（ES2015）。它的目标是使得JavaScript语言可以用来编写复杂的大型应用程序。

 另外，一些情况下ES6也泛指ES2015及之后的新增特性，虽然之后的版本应当称为ES7、ES8等。  

#### **ES6的新语法**

**let和const**

	在ES6之前，一般使用var来使用定义。但是这是一个JavaScript的错误设计var会导致变量声明提升和没有块级作用域等问题。在ES6中，使用let和const来进行声明，let声明变量，const声明常量。 
	
	 使用了let和const后，只能在其所在作用域中访问相关属性（let和const外部找到的第一对{}括起来的区域为其作用域） 
	
	使用var时，重复声明一个值，除第一次外的声明会被忽略，而对于let和const来说，在其作用域内不可以重复声明同一个值，会报错。
	
	const：必须有值且不能为null, 不能再更改(仅可读)，如果更改const的值会报错。（但是，如果const声明的是一个对象，那么这个对象所包含的属性值是可以更改的，但是对象本身所指向的地址不能改变）

**对象赋值简写**

	在ES5中对象定义的方式为：

```javascript
 function people(name, age) {
        return {
            name: name,
            age: age
        };
    }
```

 对象以K-V的形式进行赋值，在给对象赋值时，可能会出现key和value相等的情况，在ES6中，当key和value重名时，可以直接简写为一个： 

```javascript
function people(name, age) {
     return {
          name,
          age
      };
}
```

在给对象赋方法的时候

	在ES5中：

```javascript
    const people = {
        name: 'lux',
        getName: function() {
            console.log(this.name)
        }
    }
```

 ES6中可以省略: function而直接写成属性名(){} 

```javascript
    const people = {
        name: 'lux',
        getName () {
            console.log(this.name)
        }
    }
```

**模板字符串**

语法：\`${}\`

 第一个用途，基本的字符串格式化。将表达式嵌入字符串中进行拼接。用${}来界定： 

```javascript
    //ES5 
    var name = 'lux' //此处使用的单引号
    console.log('hello' + name)
    //ES6
    const name = 'lux'
    console.log(`hello ${name}`) //hello lux 此处使用的是反引号
```

 第二个用途，使用反引号拼接多行字符串： 

```javascript
    // ES5
    var msg = "Hi \      //使用双引号需要使用转移字符
    man!
    "
    // ES6
    const template = `<div>
        <span>hello world</span>
    </div>`               //使用单引号可以直接换行
```

**箭头函数**

特点：1.不需要function关键词  2.有些情况下可以省略return关键字  3.自身没有this，继承上下文的this关键字

语法：

```javascript
let demoFun = oArgument => oDessert
// demoFun 为函数名
// oArgument 为函数形参
// oDessert 为返回的值

let func = (x, y) => {return x + y; }; 
//常规编写 明确的返回值
```

箭头函数可以看做是对匿名函数的优化，参数用括号包裹，函数语句用花括号包裹，使用return返回，支持使用ES6 rest参数（展开运算符）和默认参数语法：

```javascript
let demoFun = (param1, param2, ...rest) => { statements }
// 支持 剩余参数和默认参数:
```

当函数有且仅有一个参数的时候，是可以省略掉括号的。当你函数返回有且仅有一个表达式的时候可以省略{} 和 return；例如:

```javascript
var people = name => 'hello' + name
  //参数name就没有括号
let demoFun = params => ({foo: bar})
//但是返回一个对象时，函数体外要加圆括号，不然会被解析为代码段
```

箭头函数会捕获其所在上下文的 this 值，作为自己的 this 值，因此下面的代码将如期运行（如果箭头函数外为全局环境，this指向window）：

```javascript
function Person() { 
  this.age = 0; 
  setInterval(() => {
    // 回调里面的 `this` 变量就指向了期望的那个对象了
    this.age++;
  }, 3000);
}
var p = new Person();
```

箭头函数没有原型属性：

```javascript
var Foo = () => {};

console.log(Foo.prototype); // undefined
```

箭头函数不能用作构造器，和 new 一起用就会抛出错误：

```javascript
var Foo = () => {};

var foo = new Foo(); // TypeError: Foo is not a constructor
```

箭头函数没有自己的 arguments对象：

```javascript
var arr = () => arguments;

arr(); // Uncaught ReferenceError: arguments is not defined(…)
```

但有时候我们仍然需要获取函数中的多余参数，此时可以使用rest参数（rest参数搭配的变量是一个数组，该变量将多余的参数放入数组中，多余指的是形参列表中没有罗列出来的参数），且rest 参数之后不能再有其他参数（即只能是最后一个参数），否则会报错：

**promise**

Promise是一个构造函数，自己身上有all、reject、resolve这几个眼熟的方法，原型上有then、catch等同样很眼熟的方法。

```js
var p = new Promise(function(resolve, reject){
    //做一些异步操作
    setTimeout(function(){
        console.log('执行完成');
        resolve('随便什么数据');//异步操作成功返回的数据
        //reject() 异部操作失败的返回数据
    }, 2000);
});
```

 Promise的构造函数接收一个参数，是函数，并且传入两个参数：resolve，reject，分别表示异步操作执行成功后的回调函数和异步操作执行失败后的回调函数 。

 Promise的时候一般是包在一个函数中，在需要的时候去运行这个函数 。

```js
function runAsync(){
    var p = new Promise(function(resolve, reject){
        //做一些异步操作
        setTimeout(function(){
            console.log('执行完成');
            resolve('随便什么数据');
        }, 2000);
    });
    return p;       //返回Promise对象     
    }
    runAsync()	//执行runAsunc函数
```

 包装好的函数最后，会return出Promise对象，也就是说，执行这个函数我们得到了一个Promise对象。还记得Promise对象上有then、catch方法。

```js
 runAsync().then(function(data){   //调用函数返回值（Promise对象）的then方法，执行操作完成后的动作。
        console.log(data)
    })
```

 在runAsync()的返回上直接调用then方法，then接收一个参数，是函数，并且会拿到我们在runAsync中调用resolve时传的的参数。运行这段代码，会在2秒后输出“执行完成”，紧接着输出“随便什么数据”。 

Promise在功能上和回调函数类似，而Promise的优势在于，可以在then方法中继续写Promise对象并返回，然后继续调用then来进行回调操作。 

reject方法

 reject的作用就是把Promise的状态置为rejected，这样我们在then中就能捕捉到，然后执行“失败”情况的回调。 

```js
    function getNumber(){
    var p = new Promise(function(resolve, reject){
        //做一些异步操作
        setTimeout(function(){
            var num = Math.ceil(Math.random()*10); //生成1-10的随机数
            if(num<=5){
                resolve(num);
            }
            else{
                reject('数字太大了');
            }
        }, 2000);
    });
    return p;            
}

getNumber()
.then(
    function(data){
        console.log('resolved');
        console.log(data);
    }, 
    function(reason, data){//reason是Promise的reject传递的数据
        console.log('rejected');
        console.log(reason);
    }
);
```

 then方法可以接受两个参数，第一个对应resolve的回调，第二个对应reject的回调。调用reject并传递一个参数，作为失败的原因。 

链式操作：

 从表面上看，Promise只是能够简化层层回调的写法，而实质上，Promise的精髓是“状态”，用维护状态、传递状态的方式来使得回调函数能够及时调用，它比传递callback函数要简单、灵活的多。 

```js
function runAsync1(){
    var p = new Promise(function(resolve, reject){
        //做一些异步操作
        setTimeout(function(){
            console.log('异步任务1执行完成');
            resolve('随便什么数据1');
        }, 1000);
    });
    return p;            
}
function runAsync2(){
    var p = new Promise(function(resolve, reject){
        //做一些异步操作
        setTimeout(function(){
            console.log('异步任务2执行完成');
            resolve('随便什么数据2');
        }, 2000);
    });
    return p;            
}
function runAsync3(){
    var p = new Promise(function(resolve, reject){
        //做一些异步操作
        setTimeout(function(){
            console.log('异步任务3执行完成');
            resolve('随便什么数据3');
        }, 2000);
    });
    return p;            
}
//链式操作
runAsync1()
.then(function(data){
    console.log(data);
    return runAsync2();
})
.then(function(data){
    console.log(data);
    return runAsync3();
})
.then(function(data){
    console.log(data);
});
```



#### js规范

##### 变量名：

 变量名推荐使用驼峰法来命名(**camelCase**):  

```javascript
firstName = "John";
lastName = "Doe";

price = 19.90;
tax = 0.20;

fullPrice = price + (price * tax);
```

##### 空格与运算符

 通常运算符 ( = + - * / ) 前后需要添加空格: 

```javascript
var x = y + z;
var values = ["Volvo", "Saab", "Fiat"];
```

##### 代码缩进

 通常使用 4 个空格符号来缩进代码块： 

==不推荐使用 TAB 键来缩进，因为不同编辑器 TAB 键的解析不一样.==

##### 语句规则

 简单语句的通用规则: 

- 一条语句通常以分号作为结尾。

 复杂语句的通用规则: 

- 将左花括号放在第一行的结尾。
- 左花括号前添加一空格。
- 将右花括号独立放在一行。
- 不要以分号结束一个复杂的声明。

##### 对象规则

对象定义的规则:

- 将左花括号与类名放在同一行。
- 冒号与属性值间有个空格。
- 字符串使用双引号，数字不需要。
- 最后一个属性-值对后面不要添加逗号。
- 将右花括号独立放在一行，并以分号作为结束符号。

```js
var person = {
    firstName: "John",
    lastName: "Doe",
    age: 50,
    eyeColor: "blue"
};
```

 短的对象代码可以直接写成一行: 

```js
 var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```



#####  每行代码字符小于 80

为了便于阅读每行字符建议小于数 80 个。

如果一个 JavaScript 语句超过了 80 个字符，建议在 运算符或者逗号后换行。

### Vue虚拟DOM和组件化

#### DOM:

文档对象模型( Document Object Model ), 是[W3C](https://baike.baidu.com/item/W3C)组织推荐的处理[可扩展置标语言](https://baike.baidu.com/item/可扩展置标语言/4605507)的标准[编程接口](https://baike.baidu.com/item/编程接口/3339711)。它是一种与平台和语言无关的[应用程序接口](https://baike.baidu.com/item/应用程序接口)(API),它可以动态地访问程序和脚本,更新其内容、结构和[www](https://baike.baidu.com/item/www/109924)文档的风格(目前,HTML和XML文档是通过说明部分定义的) 。[DOM](https://baike.baidu.com/item/DOM/50288)是一种基于树的[API](https://baike.baidu.com/item/API/10154)文档，它要求在处理过程中整个文档都表示在[存储器](https://baike.baidu.com/item/存储器/1583185)中。 

简单来说，DOM就是一个树型结构的文档。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020102912192714.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


#### 虚拟Dom：

虚拟DOM是真实DOM的抽象,再通过一系列操作映射到真实环境上.

虚拟DOM的原理流程：

- 用JavaScript模拟得到DOM，并渲染这个DOM树。

- 比较新老DOM，得到比较的差异对象

- 把差异应用到渲染的DOM树。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020102912194428.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


  为什么使用虚拟DOM:

  传统的浏览器资源开销最大的是DOM节点,当DOM节点很多时,使用Javascript处理DOM效率往往很低,此时浏览器往往是重绘DOM的树结构,重绘次数越多,应用程序月卡顿.虚拟DOM是放在JS和HTML中间的一个层,通过新旧DOM的比较,获取差异对象,有针对的渲染差异部分,最终达到性能优化的目的.

  ##### Vue中虚拟DOM的渲染流程:
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029122033316.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)



- **渲染函数**：渲染函数是用来生成Virtual DOM的 

- **VNode 虚拟节点**：它可以代表一个真实的 dom 节点。 

- **patch(也叫做patching算法)**：虚拟DOM最核心的部分，它可以将vnode渲染成真实的DOM，这个过程是对比新旧虚拟节点之间有哪些不同，然后根据对比结果找出需要更新的的节点进行更新。 

#### 组件化

什么是组件：

​	当人遇到一个非常复杂的问题是，不太可能一次性搞定一大堆东西。但是可以将复杂的问题拆分成一个个独立的小问题，再放入整体中，复杂的大问题就会迎刃而解。

 	组件的出现，就是为了拆分Vue实例的代码量的，能够让我们以不同的组件，来划分不同的功能模块，	将来我们需要什么样的功能，就可以去调用对应的组件即可。

组件化和模块化的不同： 

​	 模块化： 是从代码逻辑的角度进行划分的；方便代码分层开发，保证每个功能模块的职能单一； 				  			组件化： 是从UI界面的角度进行划分的；前端的组件化，方便UI组件的重用。

##### 	组件化优点：

- 实现简单
- 便于管理和维护
- 功能独立

#####    使用步骤

- 创建组件构造器
- 注册组件
- 使用组件

### Vue的响应式和双向数据绑定

##### 响应式编程：

 响应式编程（reactive programming）是一种基于数据流（data stream）和变化传递（propagation of change）的声明式（declarative）的编程范式。 

Vue的响应式的官网解释：Vue 最独特的特性之一，是其非侵入性的响应式系统。数据模型仅仅是普通的 JavaScript 对象。而当你修改它们时，视图会进行更新。

简而言之就是数据变页面变。

##### 实现原理：

Vue在组件和实例初始化的时候，会将data里的数据进行[数据劫持](https://www.cnblogs.com/zhangym118/p/8717999.html)(object.definepropty对数据做处理)。被劫持过后的数据会有两个属性：一个叫`getter`，一个叫`setter`。

`getter`是使用数据的时候触发，`setter`是在修改数据的时候触发，修改数据的时候触发`setter`，同时也触发了底层的`watcher`监听，通知dom修改刷新。

![	](https://img-blog.csdnimg.cn/2020102912205449.gif#pic_center)
##### 双向数据绑定 

双向数据绑定就是基于Vue响应式实现的。

```html
<body>
    <div id="app">
      <input type="text" v-model='mes'>
      <p>{{mes}}</p>
    </div>
<script type="text/javascript" src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
<script>
    new Vue({
        el:"#app",
        data:{
            mes:"v-model的使用"
        },
    })
</script>
</body>
```

双向绑定有什么用：

​	可以省掉一些dom操作因为view对model 的改变是view改变后自动进行的，所以不需要人工dom对		model进行改变

​	适用场景：

​		 表单交互较多的场景下，会简化大量业务无关的代码 。

## 2.指令

> 指令讲解：https://www.bilibili.com/video/BV11s411A7h6?p=7

Vue的指令都带有前缀v，表示他是Vue特有的attribute。它们会在渲染的 DOM 上应用特殊的响应式行为。

### 插值指令

- `v-cloak`

使用v-cloak能够解决插值闪烁的问题

- `v-text`

默认v-text是没有闪烁问题的

v-test会替代元素中原本的内容，但是v-cloak不会，只会把{{}}中的内容替换

- `v-html`

使用v-html能解析html中的内容

- `v-bind`

用来绑定元素的属性，缩写是 `:`

在head中加上display属性，可以使得v-cloak中的{{msg}}在加载完前不会显示(也就是不会闪烁)

```html
<style>
    [v-cloak] {
        display: none;
    }
</style>
```

```html
<body>
    <!--vue控制的元素区，就是v-->
    <div id="app">
        <!--使用v-cloak能够解决插值表达式闪烁的问题-->
        <p v-cloak>{{ msg }}</p>
        <h4 v-text="msg"></h4>  <!--默认v-test是没有闪烁问题的-->  
        <!--v-test会替代元素中原本的内容，但是v-cloak不会，只会把{{}}中的内容替换-->
        <div v-html="msg2"></div>   
        <!--使用v-html可以直接解析html标签，v-html也会覆盖元素中原本的内容-->
        <input type="button" value="按钮" v-bind:title="mytitle">  
        <!--v-bind用于绑定属性，mytitle就相当于一个变量。v-bind:也可以简写为:-->
    </div>
    <!--这个vm对象就是MVVM中的VM调度者-->
    <script>
        //创建Vue实例
        var vm = new Vue({
            el:'#app',    //表示我们要控制的区域
            //这里的data就是MVVM中的M，专门用来保存每一个页面的数据
            data:{
                msg:'欢迎学习Vue',
                msg2:'<h1>我是一个h1标签</h1>',
                mytitle:'我是一个title'
            }
        })
    </script>
</body>
```

####　v-bind设置样式

**通过v-bind绑定class属性来设置内部样式：**

一些样式如下：

```html
<style>
    .red{
        color:red
    }
    .thin{
        font-weight: 200;
    }
    .italic{
        font-style: italic;
    }
    .active{
        letter-spacing: 0.5em;
    }
</style>
```

如何用Vue设置元素的样式：

1. 使用数组的形式

```html
<body>
    <div id="app">
        <!--修改样式，第一种：直接传递一个数组。使用v-bind绑定。注意数组中是元素是样式的字符形式(不使用字符形式，则会将其看作变量)-->
        <h1 v-bind:class="['thin','italic','red']">这是一个H1</h1>
    </div>

    <script>
        var vm = new Vue({
            el:'#app',
            data:{

            },
            methods:{

            }
        })
    </script>
</body>
```

2. 使用三元表达式，实现样式的选择

```html
<body>
    <div id="app">
        <!--使用三元运算，当flag为true时为red，否则就不为red-->
        <h1 v-bind:class="['thin','italic',flag?'red':'']">这是一个H1</h1>
    </div>
    <script>
        var vm = new Vue({
            el:'#app',
            data:{
                flag : false
            },
            methods:{
            }
        })
    </script>
</body>
```

3. 数组中嵌套对象，实现样式的选择

```html
<body>
    <div id="app">
        <!--在数组中 使用对象来代替三元表达书，red为类名，flag为值-->
        <h1 v-bind:class="['thin','italic',{'red':flag}]">这是一个H1</h1>
    </div>

    <script>
        var vm = new Vue({
            el:'#app',
            data:{
                flag : true
            },
            methods:{

            }
        })
    </script>
</body>
```

4. 直接使用对象

```html
<h1 v-bind:class="{red:true,italic:true,thin:true,active:false}">这是一个H1</h1>
```

**通过v-bind绑定style属性来设置行内样式：**

1. 在style里面写上对象

```html
<body>
    <div id="app">
        <!--直接在里面加上对象，对象就是无序的键值对集合-->
        <h1 :style="{'color':'red','font-weight':200}">这是一个H1</h1>
    </div>
    <script>
        var vm = new Vue({
            el:'#app',
            data:{
            },
            methods:{

            }
        })
    </script>
</body>
```

2. 将样式定义到data中，并引入到style中

通过数组可以引入多个

```html
<body>
    <div id="app">
        <!--直接在里面加上对象，对象就是无序的键值对集合-->
        <h1 :style="[styleObj1,styleObj2]">这是一个H1</h1>
    </div>
    <script>
        var vm = new Vue({
            el:'#app',
            data:{
                styleObj1:{'color':'red','font-weight':200},
                styleObj2:{'fontStyle':'italic'}
            },
            methods:{

            }
        })
    </script>
</body>
```

### 事件指令

`v-on`

使用v-on实现事件，缩写是@，他会在method中寻找方法。

```html
<input type="button" value="按钮2" v-on:click="show"> <!--点击事件-->
<input type="button" value="按钮2" v-on:mouseover="show">  <!--鼠标触及事件-->
<script>
    //创建Vue实例
    var vm = new Vue({
        el:'#app',    //表示我们要控制的区域
        methods:{ //在method中定义方法
            show: function () {
                alert('Hello')
            }
        }

    })
</script>
```

#### 事件修饰符

- `.stop`：阻止冒泡(事件的继续传播)
- `.prevent`：阻止默认事件
- `.capture`：添加事件侦听器时使用事件捕获模式
- `.self`：只有当事件在该元素本身(不包含子元素等)触发时触发回调,但是阻止别的冒泡
- `.once`：事件只触发一次
- `.passive`：默认会执行的事件，使用这个可以让事件快速产生，通常应用于滑动事件

**注：不要把 `.passive` 和 `.prevent` 一起使用，因为 `.prevent` 将会被忽略，同时浏览器可能会向你展示一个警告。请记住，`.passive` 会告诉浏览器你*不*想阻止事件的默认行为。**

```html
<body>
    <div id="app">
        <div class="inner" @click="divHandler">
            <!--默认会先实现button的点击事件，然后触发div的点击事件-->
            <!--如果在button后加上stop的事件修饰符，就会阻止事件的冒泡(也就是只会触发button的点击事件)-->
            <input type="button" value="戳他" @click.stop="btnHandler">
            <!--prevent阻止了默认行为的发生(这里就不会跳转到百度这个界面)。这个就可以用于权限上(没有权限就不能点击啥的)-->
            <!--once是让事件只发生一次，也就是这里的prevent只阻止了一次-->
            <a href="http://www.baidu.com" @click.prevent.once="linkClick">有问题，问百度</a>
        </div>

        <!--使用capture实现捕获触发事件的机制(在这里就是先触发外部的点击事件，再触发里面的)-->
        <div class="inner" @click.capture="divHandler">
            <input type="button" value="戳他" @click.stop="btnHandler">
        </div>
        <!--使用self，只有触发自己的事件才可以，冒泡或者孩子都不行-->
        <div class="inner" @click.self="divHandler">
            <input type="button" value="戳他" @click.stop="btnHandler">
        </div>
    </div>
    <script>
        //创建一个Vue实例，得到ViewModel
        var vm = new Vue({
            el:'#app',
            data:{

            },
            methods:{
                divHandler(){
                    console.log("触发了div的点击事件")
                },
                btnHandler(){
                    console.log("触发了btn的点击事件")
                },
                linkClick(){
                    console.log("跳转至百度")
                }
            }
        })
    </script>
</body>
```

#### 按键修饰符

在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 `v-on` 在监听键盘事件时添加按键修饰符：

```html
<!-- 只有在 `key` 是 `Enter` 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">

```

为了在必要的情况下支持旧浏览器，Vue 提供了绝大多数常用的按键码的别名：

- `.enter`
- `.tab`
- `.delete` (捕获“删除”和“退格”键)
- `.esc`
- `.space`
- `.up`
- `.down`
- `.left`
- `.right`

### v-for循环

v-for可以循环一个普通数组、对象数组、对象，也可以迭代数字(从1开始)

```html
<body>
    <div id="app">
        <!--循环普通数组，第一个位置的item就是list中遍历的值，第二个位置的i为索引值-->
        <p v-for="(item,i) in list">索引值：{{i}} --- {{item}}</p>
        <!--循环对象数组-->
        <p v-for="user in list1">{{user.id}} --- {{user.name}}</p>
        <!--循环对象中的属性,除了val和key，在第三个位置上是索引-->
        <p v-for="(val,key) in user">值是：{{val}} --- 键是：{{key}}</p>
        <!--迭代数字，这里的count是从1开始的-->
        <p v-for="count in 10">这是第{{count}}次循环</p>
    </div>

    <script>s
        var vm = new Vue({
            el:'#app',
            data:{
                list:[1,2,3,4,5],
                list1:[
                    {id:1,name:'a'},
                    {id:2,name:'b'},
                    {id:3,name:'c'},
                    {id:4,name:'d'},
                    {id:5,name:'e'},
                ],
                user:{
                    id:1,
                    name:'Tom',
                    gender:'男'
                }
            },
            methods:{

            }
        })
    </script>
</body>
```

**循环组件：**

```html
<body>
    <div id="app">
        <div>
            <label>Id:
                <input type="text" v-model="id">
            </label>
            <label>Name:
                <input type="text" v-model="name">
            </label>
            <input type="button" value="添加" @click="add">
        </div>
    
        <!--循环组件-->
        <!--指定了key值就可以指定循环的位置，如果没有的话，就默认以索引作为位置(而当动态变化数组的时候索引为变化，对应的位置就会变化)-->
        <!--注意v-for的时候，key属性只能使用number获取string-->
        <!--注意：key在使用的时候，必须使用v-bind属性绑定的形式，指定key的值-->
        <p v-for="item in list2" v-bind:key="item.id">
            <input type="checkbox">
            {{item.id}}--{{item.name}}
        </p>
    </div>


    <script>
        var vm = new Vue({
            el:'#app', 
            data:{
                name:'',
                id:'',
                list2:[
                    {id:1,name:'软件工程'},
                    {id:2,name:'需求'},
                    {id:3,name:'数据库'},
                    {id:4,name:'vue'},
                    {id:5,name:'springboot'},
                ]
            },
            methods:{
                add(){
                    //this.list2.push({id:this.id,name:this.name})   //直接使用push向里面添加(在数组后面添加)
                    this.list2.unshift({id:this.id,name:this.name})   //使用unshift添加(在数组前面添加)
                }
            }
        })
    </script>
</body>
```

### v-if和v-show

```html
<body>
    <div id="app">
        <input type="button" value="按钮" @click="toggle">
        <!--v-if是只要没有了，就是将其删除-->
        <!--v-show不会删除组件，不会进行DOM的删除和创建，只是切换了display:none样式-->
        <!--v-if有较高的切换性能消耗-->
        <!--v-show又较高的初始渲染消耗-->
        <!--如果元素涉及到频繁的切换，最好不要使用v-if。如果元素可能永远不会显示出来(稳定的时候)，则选择v-if好些-->
        <h3 v-if="flag">这是用v-if控制的元素</h3>
        <h3 v-show="flag">这是用v-show控制的元素</h3>
    </div>

    <script>
        var vm = new Vue({
            el:'#app',
            data:{
                flag:true
            },
            methods:{
                toggle(){
                    this.flag = !this.flag
                }
            }
        })
    </script>
</body>
```

## 生命周期

每个 Vue 实例在被创建时都要经过一系列的初始化过程——例如，需要设置数据监听、编译模板、将实例挂载到 DOM 并在数据变化时更新 DOM 等。同时在这个过程中也会运行一些叫做**生命周期钩子**的函数，这给了用户在不同阶段添加自己的代码的机会。

**生命周期图示：** 

> 过程讲解：https://www.bilibili.com/video/BV11s411A7h6?p=36
>
> 图片地址：
>
>  <img src="https://img-blog.csdnimg.cn/20201029145620150.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dheW5lYWRkdg==,size_16,color_FFFFFF,t_70#pic_center" alt="img" style="zoom: 25%;" /> 



![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153927151.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)

**注意：**

生命周期函数不能使用箭头函数，因为箭头函数里面是没有this的，而在生命周期中我们需要频繁的使用this。

**钩子函数：**

- `beforeCreate`

在实例初始化之后，数据观测(data observer)和event/watcher事件配置之前被调用。(整个页面创建之前调用的生命周期)

- `created`

实例创建完之后被立即调用。

此时，实例已经完成了数据观测(data observer),属性和方法的运算，watcher/event事件回调。

但是挂载阶段还没有开始，$el属性目前不可见。

- `beforeMount`

在挂载开始之前被调用，相关的渲染函数首次被调用。

- `mounted`

挂载成功之后调用的函数，el被新创建的vm.$el替换

- `beforeUpdate`

数据更新是调用，发生在虚拟DOM打补丁之前。这里适合在更新之前访问现有DOM。

- `updated`

数据更改导致虚拟DOM重新渲染和补丁，在这之后会调用此钩子

数据、组件更新完毕时调用

- `beforeDestory`

实例销毁之前调用。在这一步，实例仍然完全可用。

- `destoryed`

实例销毁后调用。该钩子被调用后，对应 Vue 实例的所有指令都被解绑，所有的事件监听器被移除，所有的子实例也都被销毁。

### 浅谈Vue3生命周期

> Vue3新特性：http://www.liulongbin.top:8085/#/ 

setup()函数会在buforeCreate()之后，created之前执行

钩子函数的变化：

- ~~`beforeCreate`~~ -> use `setup()`
- ~~`created`~~ -> use `setup()`
- `beforeMount` -> `onBeforeMount`
- `mounted` -> `onMounted`
- `beforeUpdate` -> `onBeforeUpdate`
- `updated` -> `onUpdated`
- `beforeDestroy` -> `onBeforeUnmount`
- `destroyed` -> `onUnmounted`

所有的函数都需要先导入，然后再setup中书写

其中`vue-compisition-api`是Vue团队开发的RFC，供开发者提前体验 vue 3.0 的新特性。

使用前需要先安装`composition-api`

```js
import { onMounted, onUpdated, onUnmounted } from '@vue/composition-api'

const MyComponent = {
    setup() {
        onMounted(() => {
            console.log('mounted!')
        })
        onUpdated(() => {
            console.log('updated!')
        })
        onUnmounted(() => {
            console.log('unmounted!')
        })
    }
}
```

## 3.watch、computed、method

## watch

​		一个对象，键是需要观察的表达式，值是对应回调函数。值也可以是方法名，或者包含选项的对象。Vue 实例将会在实例化时调用 $watch()，遍历 watch 对象的每一个属性。



```js
var vm = new Vue({
			    el:"#box",
			    data: {
					a: "",
					b: "",
					c: {
						name:"bob",
                        age:18
					},
					d: "立即响应!",
				},
			 watch: {
			    a(val, oldVal) {
				 console.log('new: %s, old: %s', val, oldVal)
			   },
			   //方法名
			   b: 'bMethod',
			},
			  methods:{
				  bMethod(){
					  console.log("监听触发")
				  },
				  dMethod(){
					  console.log(this.d);
				  }
				  
			  },
			})
```

### immediate属性

`immediate:true`代表如果在 wacth 里声明了 d 之后，就会立即先去执行里面的handler方法。

```js
 watch:{
   //该回调将会在侦听开始之后被立即调用
     d: {
         handler: 'dMethod',
         immediate:true
     },  
     
 }

```

### deep属性

默认值是 `false`，代表是否深度监听

如果`deep:true`,监听器会一层层的往下遍历，给对象的所有属性都加上这个监听器，但是这样性能开销就会非常大了，任何修改`c`里面任何一个属性都会触发这个监听器里的 handler。

```js
watch:{
        //该回调会在任何被侦听的对象的 property 改变时被调用，不论其被嵌套多深
    c: {
        handler(val, oldVal) {
            console.log('newvalue:',val.name);
        },
            deep:true
    },
}
```

因此，可以使用字符串形式监听

```js
watch:{
  //对对象的某一属性添加监听
        'c.name'(val, oldVal) {  
            console.log('new: %s, old: %s', val, oldVal) 
        }
}
```

## method

methods 将被混入到 Vue 实例中。可以直接通过 VM 实例访问这些方法，或者在指令表达式中使用。方法中的 `this` 自动绑定为 Vue 实例。

```js
var vm = new Vue({
    el:"#box",
    data: { a: 1 },
    methods: {
        //无参数方法
        plus() {
            this.a++
        },
        //有参数方法
        plus2(str){
            console.log("a=",str);
        },
        //调用其他方法
        plus3(){
            this.plus2(this.a);
            this.plus();
            this.plus2(this.a);
        }
    }
})
```

注意，**不应该使用箭头函数来定义 method 函数** (例如 `plus: () => this.a++`)。理由是箭头函数绑定了父级作用域的上下文，所以 `this` 将不会按照期望指向 Vue 实例，`this.a` 将是 undefined。

## computed

计算属性将被混入到 Vue 实例中。所有 getter 和 setter 的 this 上下文自动地绑定为 Vue 实例。

计算属性的结果会被缓存，除非依赖的响应式 property 变化才会重新计算

```js
var vm = new Vue({
    el:"#box",
    data:{
        a:1,
    },
    computed:{
        // 仅读取
        aDouble(){
            return this.a*2
        },
        // 读取和设置
        aPlus: {
            get() {
                return this.a + 10
            },
            set(v) {
                this.a = v - 5
            }
        }
    }
})
console.log(vm.aDouble);//=>2
console.log(vm.aPlus);//=>11
vm.aPlus=20;
console.log(vm.a);//=>15
console.log(vm.aPlus);//=>25
console.log(vm.aDouble);//=>30
```



## 区别

### methods和computed的区别

1.computed是属性调用，而methods是方法调用 

2.methods的运算是没有缓存的，computed运算是有缓存的（只要运算所依赖的数据没有发生变化就会从缓存中取出结果）

```js
<div id="box">
    <button @click="getcomputed()">获取computed数据</button>
    <h3>{{date1}}</h3>
    <button @click="getmethods()">获取methods数据</button>
    <h3>{{date2}}</h3>
</div>


new Vue({
    el:'#box',
    data:{
        date1:"",
        date2:""
    },
    computed:{
        computedDate() {
            return new Date()
        }
    },
    methods:{
        getcomputed(){
            this.date1 = this.computedDate
        },
        getmethods(){
            this.date2 = new Date();
        },
        methodsDate(){
            return new Date();
        }
    }
})
```



### watch 和 computed 的对比

共同点：都是希望在依赖数据发生改变的时候，被依赖的数据根据预先定义好的函数，发生变化。

不同点：watch擅长处理的场景：一个数据影响多个数据

​			   computed擅长处理的场景：一个数据受多个数据影响

```js
var vm = new Vue({
    el:"#box",
    data:{
        message:"",
        number:1
    },
    computed: {
        ComMessage () {
            return this.message.split('').reverse().join('')+this.number
        }
    },
    watch: {
        message(val, oldVal) {
            this.number++
			console.log("number: %s,val: %s",this.number,val);
        }
    }
})
```



## 组件

## 什么是组件

组件是对数据和方法的简单封装，也就是可复用的Vue实例

它跟普通的Vue有一样的属性：

1. **data** （数据存放）
2. **computed**（计算属性）
3. **watch**（监听属性）
4. **methods**（方法存放）

但是组件并没有`el`属性，即组件没有根节点相关的属性。

## 组件注册

### 全局组件 

#### Vue.component 

```js
// 定义全局组件
			Vue.component("navbar",{
				template:
					`<div style="background:lightgreen">
					<button @click="handleClick()">click</button>
					Component--{{navbarname}}
				</div>`,
				methods:{
					handleClick(){
						console.log("back");
					}
				},
				data(){
					return{
						navbarname:"navbar组件"
					}
				}
			})
```

#### \<template>\</template>

```js
<template id="tem">
    <div>
    	{{navbarname}}
    </div>
</template>

<script type="text/javascript">

    Vue.component('navbar',{
    template:'#tem',
    data(){
        return{
            navbarname:"navbar组件"
        }
    }
})

new Vue({
    el:"#box"
})
</script>
```



### 局部组件

```js
//局部组件navbarchild 只有它的父组件navbar可以访问
				components:{
					//子组件名字
					navbarchild:{
						template:
						`<div>
						局部组件-navbarchild
						</div>`,
                    	}
				}
```

*自定义组件需要有一个root element

```js
Vue.component("test",{
				template:
				`<div>
					<navbar></navbar>
					<navbarchild></navbarchild>
				</div>	`
			})
			 
```

*父子组件的data是无法共享 

*组件可以有data,methods,computed....,但是data 必须是一个函数 



## 父组件向子组件传值

props用于父组件把数据传给子组件。

props可以是数组或对象，用于接收来自父组件的数据。props 可以是简单的数组，或者使用对象作为替代，对象允许配置高级选项，如类型检测、自定义验证和设置默认值。

```js
props:["myshow","myname"]


props:{
    myshow:Boolean,
    myname:{
        type:String,
        default:'init', //若该 prop 没有被传入，则换做用这个值。
        required:true, //若该 prop 没有被传入，则一个控制台警告将会被抛出。
        //自定义验证函数
        validator(value){
        	return value.length>=5
        }
    }
}
```



## 子组件向父组件传值

$emit()用于触发父组件的自定义事件

在子组件中，首先需要使用$emit方法，该方法接收2个参数，第一个参数是事件的名称，自己随意定义。第二个参数是需要传递的数据，可以是对象，也可以是字符串类型。$emit是VUE实例中的一个方法，所以前面要加上this。

```js
Vue.component("navbar",{
				template:
					`<div>
					{{mydata}}
					<navbarchild @myEvent="change($event)"></navbarchild>
				</div>`,
				methods:{
					change(ev){
						this.mydata=ev
					}
				},
				data(){
					return{
						mydata:"这是父组件的数据"
					}
				},
				components:{
					navbarchild:{
						template:
						`<div>
						<button @click="toParent()">child--button</button>
						</div>`,
						methods:{
							toParent(){
								this.$emit("myEvent",this.childData)
							}
						},
						data(){
							return {
								childData:"子组件的数据"
							}
						},
					}
				}
			})

```



## 4.模块化开发

- 什么是模块化开发？

  将代码隔离封装成一个具有特定功能的模块，在开发时，需要什么功能就加载什么模块。每个模块都是单独的作用域，但一个模块的实现可以依赖其他模块

  开发时，所有模块组装成一个整体，完成整个系统所要求的功能

- 模块化开发的好处？

  1. 提高代码复用率
  2. 避免变量名污染、冲突
  3. 便于维护
  4. 更好的分离，按需加载

## Vue-cli3

- 什么是vue-cli3？

  vue脚手架，帮助用户快速创建vue项目。创建一套文件结构，包含了基本的依赖库，用户只需要`npm install`就可以安装。官方提供的vue-cli脚手架很友好，不用想vue+webpack的工作流怎么搭建。

### 创建vue-cli3

1. 全局安装 `npm install -g @vue/cli` 或 `yarn global add @vue/cli`

2. 创建一个项目 `vue create hello`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152140338.png#pic_center)


3. 会进入一个配置的选择页面，有默认和手动选择，我们选择手动选择，一起来看看

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152157466.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152209592.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


   - Babel：把 JavaScript 中 es2015/2016/2017/2046 的新语法转化为 es5，让低端运行环境(如浏览器和 node )能够认识并执行

   - TypeScript：支持TypeScript书写源码

   - Processive Web App (PWA) Support:渐进式网络应用程序

   - Router：支持vue-router 。
   - Vuex：支持 vuex 
   - CSS Pre-processors：支持 CSS 预处理器。
   - Linter / Formatter 支持代码风格检查和格式化。
   - Unit Testing 支持单元测试。
   - E2E Testing 支持 E2E 测试。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152240824.png#pic_center)


   `Use  history mode for router?`：

   	最直观的区别就是**在url中 hash 带了一个很丑的 #   而history是没有#的**。比如 ：`http://www.fineven.com/#/hello` 

   具体的见我们组其他同学分享的路由部分

5. 选择css预处理器

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020102915230491.png#pic_center)


6. 选择代码规则

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152314381.png#pic_center)

   	

7. 选择语法检查方式，保存检测或者是fix和commit检测

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152327741.png#pic_center)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152414105.png#pic_center)


   文件保存方式：

   - 独立文件
   - package.json

9. 是否记录本次的配置，以便下次使用

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152429147.png#pic_center)


10. 等待下载

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152438217.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


11. 安装好后就可以启动啦

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152507170.png#pic_center)




### 文件目录结构

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152520195.png#pic_center)


```
├── node_modules                    # 存放项目依赖包
├── public                          #     / Vue 项目：公用文件夹，打包时会原封不动复制到dist文件夹 /
│   ├── favicon.ico                 # [*] 在浏览器标签卡上显示的图标
│   └── index.html                  # [*] 做基础承载的 HTML
├── src                             #     / Vue 项目：源代码文件夹 /
│   ├── App.vue                     # [*] Vue 模板节点树的 根组件
│   ├── assets                      #     / Vue 项目：资源文件夹 /
│   │   └── logo.png                    
│   ├── components                  #     / Vue 项目：组件源码文件夹 /
│   │   └── Login.vue               # [*] 实现登录的组件
│   ├── main.js                     # [*] JavaScript 入口文件
│   ├── router                      # [x] / Vue-Router 文件夹 /
│   │   └── index.js
│   ├── store                       # [x] / Vuex 文件夹 /
│   │   └── index.js
│   └── views                       # [*] / Vue 项目：页面视图文件夹 /
│       ├── About.vue               # [*] 「关于我们」页面视图组件
│       └── Home.vue                # [*] 「主页」   页面视图组件
├── .gitignore                      # [x] git忽略文件
├── babel.config.js                 # [x] Babel 配置文件
├── package.json                    # [*] 当前项目 NPM 配置
├── package-lock.json               # [*] 锁定依赖包的版本
└── README.md                       # [*] 说明文档

```



### 项目运行

`npm run serve`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152532751.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


运行结果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152713161.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152806465.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


### 项目打包

`npm run build/yarn build`,将整个项目进行压缩构建到dist这个目录下(俗称打包)

打包后会生成一个新文件夹`dist`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152835567.png#pic_center)

vue-cli是使用了webpack来实现打包功能的，而在本地打开index.html文件并不能正常显示项目内容还会有一堆找不到资源的错误

，如图

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152908271.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


`vue-cli`脚手架里是帮你做了很多关于webpack的配置的, 运用了处理css文件的`style-loader`、`css-loader`, 处理文件的`file-loader`等功能，`publicPath`属性默认为`/`，就会从整个项目的根目录去找dist里的css、js等文件夹，但我们可以看到根目录下并没有这些文件夹，所以会有资源加载失败错误。而打包到服务器是上传整个dist文件夹，根目录下放的就是以下文件了

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152932506.png#pic_center)

## Webpack

### 安装

`npm install -g webpack`

`npm install --save-dev webpack`



![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029152959776.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


### 使用前的配置

1.创建package.json  `npm init`，终端会问你一系列问题，如果不准备发表模块，这些问题都不重要，可以直接回车

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153026451.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


2. 安装依赖包  `npm install --save-dev webpack`

3. 创建两个文件夹`app`、`public`.其中`app`存放原始数据和我们写的js模块，`public`存放供浏览器读取的文件（包括使用webpack打包生成的js文件以及一个index.html文件）

4. 创建三个文件：

   - index.html  --放在public下
   - Greeter.js  --放在app文件夹下
   - main.js  --放在app文件夹下

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153046567.png#pic_center)


5. 在index.html写入最基础html代码，引入打包后的js文件（先暂时命名为bundle.js）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153105688.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


6. 在Greeter.js里定义一个返回问候信息的html元素的函数，并依据CommonJS规范导出这个函数为一个模块
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020102915312327.png#pic_center)


7. 在main.js里把Greeter返回的节点插入页面

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153135602.png#pic_center)


### 正式使用

基本使用方法：

`webpack {entry file} {destination for bundled file}`	

- `entry file`填写入口文件的路径，也就是上述的main.js路径。
- `{destination for bundled file}`填写打包文件的存放路径。

需要注意的是如果你的webpack不是全局安装的，需要输入命令`node_modules/.bin/webpack app/main.js public/bundle.js`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153150558.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153205334.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


**推荐方法**：(采用文件配置的方式)

在根目录新建`webpack.config.js`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153225337.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


在package.json里设置以下启动命令：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153250716.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)


就可以使用`npm run webpack`执行打包任务啦！

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153311300.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029153322801.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1bW9yaW91cw==,size_16,color_FFFFFF,t_70#pic_center)

## 5.1 Vue Router

    用 Vue.js + Vue Router 创建单页应用，是非常简单的。使用 Vue.js ，我们已经可以通过组合组件来组成应用程
    序，当你要把 Vue Router 添加进来，我们需要做的是，将组件 (components) 映射到路由 (routes)，然后告诉V
    ue Router在哪里渲染它们。

### 动态路由匹配

 ##### 1.响应路由参数的变化

 - 我们经常需要把某种模式匹配到的所有路由，全都映射到同个组件。例	如，我们有一个 User 组件，对于所有 ID 各不相同的用户，都要使用这个组件来渲染。那么，我们可以在 vue-router 的路由路径中使  用“动态路径参数”(dynamic segment) 来达到这个效果。

 ```javascript
 const User = {
  template: '<div>User</div>'
}

const router = new VueRouter({
  routes: [
    // 动态路径参数 以冒号开头
    { path: '/user/:id', component: User },
    // 会匹配所有路径
    {  path: '*' },
    // 会匹配以 `/user-` 开头的任意路径
	{  path: '/user-*'}
  ]
})
 ```

注意：

- 当使用通配符路由时，请确保路由的顺序是正确的，也就是说含有通配符的路由应该放在最后。路由 { path: '*' } 通常用于客户端 404 错误。如果你使用了History 模式，请确保正确配置你的服务器。
- 当使用一个通配符时，$route.params 内会自动添加一个名为 pathMatch 参数。它包含了 URL 通过通配符被匹配的部分。

 ##### 2.高级匹配模式

 + vue-router 使用 path-to-regexp 作为路径匹配引擎，所以支持很多高级的匹配模式，例如：可选的动态路径参数、匹配零个或多个、一个或多个，甚至是自定义正则匹配。[github地址](https://github.com/pillarjs/path-to-regexp/tree/v1.7.0#parameters)

 ##### 3.匹配优先级

 + 有时候，同一个路径可以匹配多个路由，此时，匹配的优先级就按照路由的定义顺序：谁先定义的，谁的优先级就最高。

### 嵌套路由

实际生活中的应用界面，通常由多层嵌套的组件组合而成。同样地，URL 中各段动态路径也按某种结构对应嵌套的各层组件，例如：

````
/user/foo/profile                     /user/foo/posts
+------------------+                  +-----------------+
| User             |                  | User            |
| +--------------+ |                  | +-------------+ |
| | Profile      | |  +------------>  | | Posts       | |
| |              | |                  | |             | |
| +--------------+ |                  | +-------------+ |
+------------------+                  +-----------------+
````

借助 vue-router，使用嵌套路由配置，就可以很简单地表达这种关系。
接着上节创建的 app：

```javascript
<div id="app">
  <router-view></router-view>
</div>

const User = {
  template: '<div>User {{ $route.params.id }}</div>'
}

const router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User }
  ]
})

```

这里的 <router-view> 是最顶层的出口，渲染最高级路由匹配到的组件。同样地，一个被渲染组件同样可以包含自己的嵌套 <router-view>。例如，在 User 组件的模板添加一个 <router-view>：

```javascript
const User = {
  template: `
    <div class="user">
      <h2>User {{ $route.params.id }}</h2>
      <router-view></router-view>
    </div>
  `
}
```

要在嵌套的出口中渲染组件，需要在 VueRouter 的参数中使用 children 配置：

```javascript
onst router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User,
      children: [
        {
          // 当 /user/:id/profile 匹配成功，
          // UserProfile 会被渲染在 User 的 <router-view> 中
          path: 'profile',
          component: UserProfile
        },
        {
          // 当 /user/:id/posts 匹配成功
          // UserPosts 会被渲染在 User 的 <router-view> 中
          path: 'posts',
          component: UserPosts
        }
      ]
    }
  ]
})
```

你会发现，children 配置就是像 routes 配置一样的路由配置数组，所以呢，你可以嵌套多层路由。

此时，基于上面的配置，当你访问 /user/foo 时，User 的出口是不会渲染任何东西，这是因为没有匹配到合适的子路由。如果你想要渲染点什么，可以提供一个 空的子路由：

```javascript
const router = new VueRouter({
  routes: [
    {
      path: '/user/:id', component: User,
      children: [
        // 当 /user/:id 匹配成功，
        // UserHome 会被渲染在 User 的 <router-view> 中
        { path: '', component: UserHome },
		
        // ...其他子路由
      ]
    }
  ]
})
```

### 编程式的导航

除了使用 <router-link> 创建 a 标签来定义导航链接，我们还可以借助 router 的实例方法，通过编写代码来实现。

```javascript
router.push(location, onComplete?, onAbort?)
```

想要导航到不同的 URL，则使用 router.push 方法。这个方法会向 history 栈添加一个新的记录，所以，当用户点击浏览器后退按钮时，则回到之前的 URL。

当你点击 <router-link> 时，这个方法会在内部调用，所以说，点击 <router-link :to="..."> 等同于调用 router.push(...)。

| 声明式                   | 编程式           |
| ------------------------ | ---------------- |
| \<router-link :to="..."> | router.push(...) |

该方法的参数可以是一个字符串路径，或者一个描述地址的对象。例如：

```javascript
// 字符串
router.push('home')

// 对象
router.push({ path: 'home' })

// 命名的路由
router.push({ name: 'user', params: { userId: '123' }})

// 带查询参数，变成 /register?plan=private
router.push({ path: 'register', query: { plan: 'private' }})
```

```javascript
router.go(n)
```

这个方法的参数是一个整数，意思是在 history 记录中向前或者后退多少步，类似 window.history.go(n)

```javascript
// 在浏览器记录中前进一步，等同于 history.forward()
router.go(1)

// 后退一步记录，等同于 history.back()
router.go(-1)

// 前进 3 步记录
router.go(3)

// 如果 history 记录不够用，那就默默地失败呗
router.go(-100)
router.go(100)
```

更多操作 History 查看history api

### 命名路由

有时候，通过一个名称来标识一个路由显得更方便一些，特别是在链接一个路由，或者是执行一些跳转的时候。你可以在创建 Router 实例的时候，在 routes 配置中给某个路由设置名称。

```javascript
const router = new VueRouter({
  routes: [
    {
      path: '/user/:userId',
      name: 'user',
      component: User
    }
  ]
})
```

要链接到一个命名路由，可以给 router-link 的 to 属性传一个对象：

```	html
<router-link :to="{ name: 'user', params: { userId: 123 }}">User</router-link>
```

这跟代码调用 router.push() 是一回事：

```
router.push({ name: 'user', params: { userId: 123 }})
```

两个的作用都是去访问 /user/123 这个path

### 路由组件传参（props）

在组件中使用 $route 会使之与其对应路由形成高度耦合，从而使组件只能在某些特定的 URL 上使用，限制了其灵活性。
使用 props 将组件和路由解耦，取代与 $route 的耦合。

如果是下面的这段代码来定义路由的话就只能在路由传参中使用

```	javascript
const User = {
  template: '<div>User {{ $route.params.id }}</div>'
}
const router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User }
  ]
})
```

通过一下props解耦后可以在父子逐渐传参中使用

```javascript
const User = {
  props: ['id'],
  template: '<div>User {{ id }}</div>'
}
const router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User, props: true },
  ]
})
```

这样你便可以在任何地方使用该组件，而不仅仅是在route功能中使用该组件，使得该组件更易于重用和测试。

### HTML5 History

​	vue的router是在浏览器上运行的，使用对应的router-link并没有去请求服务器，所以要通过浏览器的url来直接访问组件，可以使用html5history，需要在前端和后端都进行一定的history配置。

​	

- 前端配置例子
- 后端配置例子
  [History模式后端配置例子](https://router.vuejs.org/zh/guide/essentials/history-mode.html#%E5%90%8E%E7%AB%AF%E9%85%8D%E7%BD%AE%E4%BE%8B%E5%AD%90)

### 导航守卫

#### 1.全局守卫

##### 全局前置守卫

你可以使用 router.beforeEach 注册一个全局前置守卫：

```javascript
const router = new VueRouter({ ... })

router.beforeEach((to, from, next) => {
  // ...
})
```

当一个导航触发时，全局前置守卫按照创建顺序调用。守卫是异步解析执行，此时导航在所有守卫 resolve 完之前一直处于 等待中。

每个守卫方法接收三个参数：

	to: Route: 即将要进入的目标 路由对象
	
	from: Route: 当前导航正要离开的路由
	
	next: Function: 一定要调用该方法来 resolve 这个钩子。执行效果依赖 next 方法的调用参数。
	
	next(): 进行管道中的下一个钩子。如果全部钩子执行完了，则导航的状态就是 confirmed (确认的)。
	
	next(false): 中断当前的导航。如果浏览器的 URL 改变了 (可能是用户手动或者浏览器后退按钮)，那么 URL 地址会重置到 from 路由对应的地址。
	
	next('/') 或者 next({ path: '/' }): 跳转到一个不同的地址。当前的导航被中断，然后进行一个新的导航。你可以向 next 传递任意位置对象，且允许设置	诸如 replace: true、name: 'home' 之类的选项以及任何用在 router-link 的 to prop 或 router.push 中的选项。
	
	next(error): (2.4.0+) 如果传入 next 的参数是一个 Error 实例，则导航会被终止且该错误会被传递给 router.onError() 注册过的回调。

**确保 next 函数在任何给定的导航守卫中都被严格调用一次。它可以出现多于一次，但是只能在所有的逻辑路径都不重叠的情况下，否则钩子永远都不会被解析或报错。**这里有一个在用户未能验证身份时重定向到 /login 的示例：

```javascript
router.beforeEach((to, from, next) => {
  if (to.name !== 'Login' && !isAuthenticated) next({ name: 'Login' })
  // 如果用户未能验证身份，则 `next` 会被调用两次
  next()
})
```

```javascript
router.beforeEach((to, from, next) => {
  if (to.name !== 'Login' && !isAuthenticated) next({ name: 'Login' })
  else next()
})
```

##### 全局解析守卫

在 2.5.0+ 你可以用 router.beforeResolve 注册一个全局守卫。这和 router.beforeEach 类似，区别是在导航被确认之前，同时在所有组件内守卫和异步路由组件被解析之后，解析守卫就被调用。

##### 全局后置钩子

你也可以注册全局后置钩子，然而和守卫不同的是，这些钩子不会接受 next 函数也不会改变导航本身：

```javascript
router.afterEach((to, from) => {
  // ...
})
```

#### 2.路由独享的守卫

你可以在路由配置上直接定义 beforeEnter 守卫：

```javascript
const router = new VueRouter({
  routes: [
    {
      path: '/foo',
      component: Foo,
      beforeEnter: (to, from, next) => {
        // ...
      }
    }
  ]
})
```

#### 3.组件内的守卫

最后，你可以在路由组件内直接定义以下路由导航守卫：
beforeRouteEnter
beforeRouteUpdate (2.2 新增)
beforeRouteLeave

```javascript
const Foo = {
  template: `...`,
  beforeRouteEnter (to, from, next) {
    // 在渲染该组件的对应路由被 confirm 前调用
    // 不！能！获取组件实例 `this`
    // 因为当守卫执行前，组件实例还没被创建
  },
  beforeRouteUpdate (to, from, next) {
    // 在当前路由改变，但是该组件被复用时调用
    // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
    // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
  },
  beforeRouteLeave (to, from, next) {
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
  }
}
```

#### 完整的导航解析流程

1.导航被触发。
2.在失活的组件里调用 beforeRouteLeave 守卫。
3.调用全局的 beforeEach 守卫。
4.在重用的组件里调用 beforeRouteUpdate 守卫 (2.2+)。
5.在路由配置里调用 beforeEnter。
6.解析异步路由组件。
7.在被激活的组件里调用 beforeRouteEnter。
8.调用全局的 beforeResolve 守卫 (2.5+)。
9.导航被确认。
10.调用全局的 afterEach 钩子。
11.触发 DOM 更新。
12.调用 beforeRouteEnter 守卫中传给 next 的回调函数，创建好的组件实例会作为回调函数的参数传入。

### 路由懒加载

当打包构建应用时，JavaScript 包会变得非常大，影响页面加载。如果我们能把不同路由对应的组件分割成不同的代码块，然后当路由被访问的时候才加载对应组件，这样就更加高效了。
结合 Vue 的异步组件和 Webpack 的代码分割功能，轻松实现路由组件的懒加载。

```javascript
const Foo = () => import('./Foo.vue')
```

在路由配置中什么都不需要改变，只需要像往常一样使用 Foo：

```javascript
const router = new VueRouter({
  routes: [
    { path: '/foo', component: Foo }
  ]
})
```



## 5.2 Vuex

### 什么情况下该使用Vuex？

如果您不打算开发大型单页应用，使用 Vuex 可能是繁琐冗余的。确实是如此——如果您的应用够简单，您最好不要使用 Vuex。一个简单的 store 模式就足够您所需了。但是，如果您需要构建一个中大型单页应用，您很可能会考虑如何更好地在组件外部管理状态，Vuex 将会成为自然而然的选择。



### 传统的数据管理方式(单向数据流)

+ state，驱动应用的数据源；

+ view，以声明方式将 state 映射到视图；

+ actions，响应在 view 上的用户输入导致的状态变化。

      单向数据流

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201028163124339.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0JhYmF6dWk2,size_16,color_FFFFFF,t_70#pic_center)
  但是，当我们的应用遇到多个组件共享状态时，单向数据流的简洁性很容易被破坏：
  原因：

+ 多个视图依赖于同一状态。

+ 来自不同视图的行为需要变更同一状态。

后果：

+ 对于问题一，传参的方法对于多层嵌套的组件将会非常繁琐，并且对于兄弟组件间的状态传递无能为力。
+ 对于问题二，我们经常会采用父子组件直接引用或者通过事件来变更和同步状态的多份拷贝。以上的这些模式非常脆弱，通常会导致无法维护的代码。

因此，我们为什么不把组件的共享状态抽取出来，以一个全局单例模式来管理数据呢？在这种模式下，我们的组件树构成了一个巨大的“视图”，不管在树的哪个位置，任何组件都能获取状态或者触发行为！

通过定义和隔离状态管理中的各种概念并通过强制规则维持视图和状态间的独立性，我们的代码将会变得更结构化且易维护。

这就是vuex背后的核心思想。

                                vuex 新的数据流方式

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201028163414109.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0JhYmF6dWk2,size_16,color_FFFFFF,t_70#pic_center)


### State

#### 简单的获取状态

使用计算方法，每当 store.state.count 变化的时候, 都会重新求取计算属性，并且触发更新相关联的 DOM。

```javascript
const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return this.$store.state.count
    }
  }
}
```

#### mapState辅助函数

当一个组件需要获取多个状态的时候，将这些状态都声明为计算属性会有些重复和冗余。为了解决这个问题，我们可以使用 mapState 辅助函数帮助我们生成计算属性，让你少按几次键：

```javascript
import { mapState } from 'vuex'

export default {
  // ...
  computed: mapState({
    // 箭头函数可使代码更简练
    count: state => state.count,

    // 传字符串参数 'count' 等同于 `state => state.count`
    countAlias: 'count',
      
      
      

    // 为了能够使用 `this` 获取局部状态，必须使用常规函数
    countPlusLocalState (state) {
      return state.count + this.localCount
    }
  })
}
```

#### getter访问

有时候我们需要从 store 中的 state 中派生出一些状态，例如对列表进行过滤并计数,如果有多个组件需要用到此属性，我们要么复制这个函数，或者抽取到一个共享函数然后在多处导入它——无论哪种方式都不是很理想。

Vuex 允许我们在 store 中定义“getter”（可以认为是 store 的计算属性）。就像计算属性一样，getter 的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算。

Getter 接受 state 作为其第一个参数：

```javascript
const store = new Vuex.Store({
  state: {
    todos: [
      { id: 1, text: '...', done: true },
      { id: 2, text: '...', done: false }
    ]
  },
  getters: {
    doneTodos: state => {
      return state.todos.filter(todo => todo.done)
    }
  }
})
```

Getter 也可以接受其他 getter 作为第二个参数：

```javascript
getters: {
  // ...
  doneTodosCount: (state, getters) => {
    return getters.doneTodos.length
  }
}
```

我们可以很容易地在任何组件中使用它：

```javascript
computed: {
  doneTodosCount () {
    return this.$store.getters.doneTodosCount
  }
}
```

### Mutations

更改 Vuex 的 store 中的状态的唯一方法是提交 mutation。Vuex 中的 mutation 非常类似于事件：每个 mutation 都有一个字符串的 事件类型 (type) 和 一个 回调函数 (handler)。这个回调函数就是我们实际进行状态更改的地方，并且它会接受 state 作为第一个参数：

```javascript
const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment (state) {
      // 变更状态
      state.count++
    }
  }
})
```

你可以向 store.commit 传入额外的参数，即 mutation 的 载荷（payload）：

```javascript
mutations: {
  increment (state, n) {
    state.count += n
  }
}
store.commit('increment', 10)
```

### Actions

Action 类似于 mutation，不同在于：

+ Action 提交的是 mutation，而不是直接变更状态。
+ Action 可以包含任意异步操作。

让我们来注册一个简单的 action：

```javascript
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  },
  actions: {
    increment (context) {
      context.commit('increment')
    }
  }
})
```

####  方法触发

Action 通过 store.dispatch 方法触发：

```javascript
store.dispatch('increment')
```

异步例子

```javascript
actions: {
  incrementAsync ({ commit }) {
    setTimeout(() => {
      commit('increment')
    }, 1000)
  }
}
```

### Modules

由于使用单一状态树，应用的所有状态会集中到一个比较大的对象。当应用变得非常复杂时，store 对象就有可能变得相当臃肿。

为了解决以上问题，Vuex 允许我们将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割：

```javascript
const moduleA = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... }
}

//将module传入到全局的store的属性中去管理
const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

//访问不同的module
store.state.a // -> 访问moduleA 的状态
store.state.b // -> 访问moduleB 的状态
```

# 6.项目实战——基于Echarts的疫情实时数据可视化平台

## 单页应用

  **SPA(single page web application)** 表示单页Web应用，即只加载单个HTML应用并在用户与应用程序交互时动态更新页面，是MVVM开发模式的典型应用， VueCLI所构建的既是SPA，配合vue-router来实现前端对路由的管理。
*单页应用相对多页应用的优点和缺点：*

   + 优点：
     1. 良好的前后端分离，解耦前后端关注点，前端负责数据交互和界面显示，后端负责数据存储和计算，各司其职，不会把前后端的逻辑混杂在一起。
     2. 使后端API通用化，一套代码即可运用于web端、移动端、小程序等，提高网站可移植性
     3. 页面切换不需要进行对html的请求，速度快，同时由于服务端不再负责模板渲染、输出页面等工作，减小了对服务器的压力。
  + 缺点：
    1. 不利于SEO（搜索引擎优化），不方便网页得到优先的关键词自然排名，不方便爬虫进行数据爬取。
    2. 初次加载由于需请求大量文件，耗时过多。
    3. 前进、后退、地址栏、书签等路由变化操作需要程序管理，页面复杂度提高。

## 项目演示

 [新冠疫情实时数据](http://47.100.36.240:8080/)

## Vue.js应用与工程化

### 架构设计与工程化规范

  #### 架构设计

  当我们在实际开发中进行技术选型时，如果我们选择了Vue作为客户端的实现方案，那我们需要在Vue的结构下进行前端架构设计，可以分为以下几个内容：

      1. **项目模板**：使用VueCLI进行快速架构，利用配置好的模板迅速搭建起一个项目工程，省去自己配置webpack配置文件的基本内容；同时，根据项目的需求来修改脚手架目录结构
         <img src="https://img-blog.csdnimg.cn/20201102004229167.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center" alt="在这里插入图片描述" style="zoom:70%;" />
         	

```javascript
		|-- node_modules                     // 项目所需依赖包
		|   |-- ..........                   // 依赖文件
		|-- public                           // 静态资源，打包不进行处理
		|   |-- favicon.ico                  // 网页图标
		|   |-- index.html                   // 入口页面
		|-- src                              // 源码目录
		|   |-- assets                       // 放置图片、文字等静态文件
		|   |-- components                   // vue公共组件
		|   |   |-- Aside.vue                // 侧边栏
		|   |   |-- Footer.vue               // 页脚
		|   |   |-- Header.vue               // 导航栏
		|   |-- less                         // 公共less预处理文件
		|   |-- router                       // vue的路由管理
		|   |-- service                      // 网络请求管理
		|   |   |-- api.js                   // 封装axios请求
		|   |   |-- dataService              
		|   |   |   |-- dataService.js       // 疫情数据API管理
		|   |-- views                        // vue路由组件
		|   |   |-- components               // 路由组件公用组件
		|   |   |   |-- AreaBox.vue          // 地区数据栏
		|   |   |   |-- TotalBox.vue         // 总体数据栏
		|   |   |-- DomesticData.vue         // 国内总体数据页面
		|   |   |-- DomesticDetails.vue      // 国内详情数据页面
		|   |   |-- ForeignData.vue          // 国外总体数据页面
		|   |   |-- ForeignDetails.vue       // 国外详情数据页面
		|   |   |-- GlobalData.vue           // 全球数据页面
		|   |-- App.vue                      // 页面入口文件
		|   |-- main.js                      // 程序入口文件
		|-- .browserslistrc                  // 配置兼容设置
		|-- .gitignore                       // git上传需要忽略的文件格式
		|-- README.md                        // 项目说明
		|-- package.json                     // 项目基本信息,包依赖信息等
		|-- babel.config.js                  // babel配置文件
		|-- vue.config.js                    // 自定义vue配置文件
		|-- yarn.lock                        // 包依赖管理
```


由于 vue-cli 3 采取了**零配置**的思路，项目初始化后，没有了 build 目录，不能直接进入修改配置文件，当开发者需要修改配置文件时，可以在根目录下创建vue.config.js。vue.config.js 是一个可选的配置文件，如果项目的根目录中存在这个文件，那么它会被 @vue/cli-service 自动加载。




   2. **UI界面**：选用一套适配Vue的UI组件库

      >本项目使用饿了么前端团队制作的ElementUI作为UI框架

   ```javascript
      //npm安装
        npm i element-ui -S
        //yarn安装
        yarn add element-ui
        
        //全局引用 main.js
        import ElementUI from 'element-ui';
        import 'element-ui/lib/theme-chalk/index.css';
        Vue.use(ElementUI);

        //按需引用
        //安装 babel-plugin-component：
        npm install babel-plugin-component -D

        //修改配置项 babel.config.js
        plugins: [
          [
            "component",
            {
              libraryName: "element-ui",
              styleLibraryName: "theme-chalk"
            }
          ]
        ]

        //main.js
        import { Button, Select } from 'element-ui';
        Vue.use(Button)
        Vue.use(Select)
   ```

3. **路由管理**：在单页应用中，前端需要自己管理路由，借助vue-router来管理前端路由

   <img src="https://img-blog.csdnimg.cn/20201029184403260.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center =" alt="在这里插入图片描述" style="zoom: 50%;" />

   4. **网络请求**：选用合适的网络请求框架进行与服务端的交互，同时解决好跨域问题。比如使用反向代理等方法，在vue开发环境下可配置proxyTable，在生产环境下可使用NGINX或Tomcat等
      - 开发环境
        ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029173922372.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center)

- 生产环境

  进行项目打包：

  ```javascript
  npm run build
  //or
  yarn build
  ```

  打包生成dist文件夹，文件被处理为如下结构：

  

​		<img src="https://img-blog.csdnimg.cn/20201029190006103.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center =230x600 =" alt="在这里插入图片描述" style="zoom:67%;" />

​	将dist文件夹放入服务器中，服务器安装nginx，进入nginx文件夹
​	![在这里插入图片描述](https://img-blog.csdnimg.cn/20201101232650149.png#pic_center)
​	nginx/conf/nginx.conf中添加如下配置：(指定项目位置，确定服务端口，进行反向代理
​	![在这里插入图片描述](https://img-blog.csdnimg.cn/20201101232356107.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center)

5. **状态管理**：在中大型项目中，使用Vuex来管理共享状态和数据

  #### 工程化规范

  在工程项目中，随着业务体量的逐渐增大，对于项目的管理会越发困难，同时项目的性能也会受到影响，我们可以从以下几个方面来解决这个问题：

      1. 路由去中心化
         我们通常在router/index.js中定义或加载所有的路由配置，那这个文件就是这个项目当中唯一的引用路由的节点（中心），但这样的中心节点在多人协同时会出现问题：
         **文件冲突**：在使用svn这种集中式版本控制服务时，没有分支的概念，全部依赖一个远程中心仓库。
         **发布故障**：在使用git等分布式版本控制服务时，试想多人同时修改同一个文件，在发布流程不是非常完善，且相互沟通不顺畅的情况下，容易出现某个正在开发的需求被另一个同样发布中的需求带上线了，但另一个需求的相关依赖并没有上线。导致生产环境编译错误从而引发线上故障。
         ==解决方式：==
         使用require.context()通过正则动态匹配并引入我们的依赖文件，实现路由文件的动态加载：(此处约束每个开发者都通过在router下根据功能创建不同的路由文件夹，并在其中书写该类js文件)

```javascript
		// 加载router目录下所有js文件作为路由配置
		let routes
		let matches = require.context('./', true, /^\.\/[^/]+\/.+\.js$/)
		matches.keys().forEach(key => {
		    routes = routes.concat(matches(key).default)
		})
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201030234351184.png#pic_center)

   2. Vuex模块化

      由于使用单一状态树，应用的所有状态会集中到一个比较大的对象。当应用变得非常复杂时，store 对象就有可能变得相当臃肿。
      为了解决以上问题，Vuex 允许我们将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割：
      <img src="https://img-blog.csdnimg.cn/20201029193513714.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center" alt="在这里插入图片描述" style="zoom:50%;" />

      3. 组件去中心化

<img src="https://img-blog.csdnimg.cn/20201029194135972.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center =" alt="在这里插入图片描述" style="zoom:50%;" />





<img src="https://img-blog.csdnimg.cn/20201029194156715.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center" alt="在这里插入图片描述" style="zoom:50%;" />

  4. 请求与视图分离
     如果将Network Request代码放在视图中，这样随着业务代码的增量，接口维护也变得越来越艰难。而将API请求分离出来做统一管理是一种优雅的方式，你只需要在视图页面中直接获取数据然后将其赋值到页面需要的变量上去：
        	![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029195040102.png#pic_center =300x100)
     *api.js中封装网络请求：*

```javascript
import axios from 'axios'

axios.defaults.baseURL = '/api/';

export const myRequest = options => {
  return new Promise((reslove,reject)=>{
    let {url,method,data,headers} = options;
    let trReq = [
      function (data) {
         let ret = '';
         for (let it in data) {
            ret += encodeURIComponent(it) + '=' + encodeURIComponent(data[it]) + '&';
         }
         ret = ret.substring(0, ret.lastIndexOf('&'));
         return ret;
      }
    ]
    let type;
    if(method=='get'){
      type='params';
    }else{
      type='data';
    }
    let axiosObj = {
      method: method || 'get',
      // url: BASE_URL + url,
      url: url,
      [type]: data || {},
      headers: headers || {'Content-Type': 'application/json','Accept': 'application/json'}
    }
    if(headers){//form-data
      axiosObj = {...axiosObj,transformRequest:trReq};
    }
    axios(axiosObj)
    .then( res => {
      reslove(res);
    })
    .catch( err =>{
      reject(err);
    })
  })
}

```

*dataService.js中书写接口并导出：*

```javascript
import {myRequest} from '../api'

class dataService {
  /**
   * 获取当前时间
   * @resolve {Object[]} nowTime
   */
  async nowTime(){
    const res = await myRequest({
      url:'/getNowTime',
      method:'get'
    })
    return res.data;
  }

  /**
   * 获取疫情总览信息
   * @resolve {Object[]} totalInfo
   */
  async totalEpidemicInfo(){
    const res = await myRequest({
      url:'/getTotalEpidemicInfo',
      method:'get'
    })
    return res.data;
  }

  /**
   * 获取国内疫情信息
   * @resolve {Object[]} domesticInfo
   */
  async domesticEpidemicInfo(){
    const res = await myRequest({
      url:'/getDomesticEpidemicInfo',
      method:'get'
    })
    return res.data;
  }

  /**
   * 获取国际疫情信息
   * @resolve {Object[]} foreignInfo
   */
  async foreignEpidemicInfo(){
    const res = await myRequest({
      url:'/getForeignEpidemicInfo',
      method:'get'
    })
    return res.data;
  }

}

export default new dataService();
```

*main.js中导入并全局使用：*
		

```javascript
import dataService from '@/service/dataService/dataService'
Vue.prototype.$dataService = dataService;
```

*组件中使用：*

```javascript
this.$dataService.totalEpidemicInfo()
.then(res=>{
  this.totalInfo = res.msg.totalInfo;
  this.loading = false;
})
.catch(err=>{
  this.$message({
    message: '获取数据失败',
    type: 'error'
  });
})
```

### 工程中Vue风格指南

      1. 自定义组件名为多个单词，这样可以避免跟现有的以及未来的 HTML 元素相冲突

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029180719131.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center =200x250)
    

    2. Prop定义应更加详细，且在声明 prop 的时候，其命名应该始终使用 驼峰表示法（camelCase），而在HTML中应该始终使用横线连接 kebab-case

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029181855960.png#pic_center =200x100)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029182714221.png#pic_center)

    3. 为组件样式设置作用域

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029182017690.png#pic_center =300x30)

    4. 将每个组件单独分成文件

    5. 由于 HTML 大小写不敏感，模板中组件名采用横线连接 (kebab-case)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029182720350.png#pic_center)

    6. 指令缩写 (用 : 表示 v-bind:、用 @ 表示 v-on: 和用 # 表示 v-slot:) 应该要么都用要么都不用
    7. 组件模板应该只包含简单的表达式，复杂的表达式则应该重构为计算属性或方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029182946771.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201029183000693.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0ODI2MDQz,size_16,color_FFFFFF,t_70#pic_center)

