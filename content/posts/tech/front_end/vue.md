---
title: Vue基础概念
subtitle:
date: 2024-12-09T05:46:28+09:00
slug: fcab693
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["vue","前端"]
categories: ["vue","前端"]
collections: ["develop"]
hiddenFromHomePage: false
hiddenFromSearch: false
hiddenFromRss: false
hiddenFromRelated: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: false
lightgallery: false
password:
message:
repost:
  enable: false
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---
本文描述了vue的基本概念
<!--more-->

> [!tip] 本文内容可能已经过时，最新内容请看vue官网[Vue.js](https://cn.vuejs.org/guide/introduction)

## 一、Vue基础

### 1、概述

作者：尤雨溪

官网：https://cn.vuejs.org

Vue.js是一套构建用户界面的**渐进式**框架。**声明式渲染和组件系统是Vue的核心库所包含内容。**

- 渐进式：循序渐进，不需要掌握全部的点，学多少用多少
- 框架：半成品的应用（之前学习的jQuery也是一个框架）

![Vue特点](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/4f9e45db623e2c0f0dd1a45e985c36b83825ce6c.png?sign=cead88c04c73c6d314f093b1ef504d42&t=5f50707e)

![Vue与react在github上](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/229fe902962263af21443024e14a78b54ea5c3d1.png?sign=976600758fc879cea5db0a54774e1bda&t=5f5070ea)



- **声明**式渲染：（如同js基础一样，要使用变量则必须先声明变量，这种称之为声明式）

Vue.js的核心是一个允许采用简洁的模板语法来声明式的将数据渲染进DOM的系统。

- **组件化**应用构建

组件系统是Vue的另一个重要概念，因为它是一种抽象的允许我们使用**小型、独立**和通常**可复用**的“小积木”构建大型应用。几乎任意类型的应用界面都可以抽象为一个组件树。

![组件](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/279e26e948d53d33a2a05e10e7c29aa736fe80a1.png?sign=9f63925b42a763bb945ad25cda41928f&t=5f5073bf)

### 2、Vue的开发模式

MVC - model view controller

MVP - model view presenter

- M-V-VM
  - M：（model）普通的javascript数据对象（其实就是一个对象，对象里放了数据）
  - V：（view）前端展示页面（可以理解成html内容）
  - VM：（ViewModel）用于**双向绑定数据**与页面，对于我们的课程来说，就是vue的实例

MVVM 模式将 Presenter 改名为 ViewModel，它采用双向绑定（data-binding）：View的变动，自动反映在 ViewModel，反之亦然。**这种模式下，页面输入改变数据，数据改变影响页面数据展示与渲染**

> vue使用MVVM响应式编程模型，避免直接操作DOM , 降低DOM操作的复杂性。

![MVVM](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/daf286bb718f7afb09ddea7205c58a18d56797f5.png?sign=9597d9d44c7ac8ace46d8ab7c0500407&t=5f560d40)



## 二、Vue入门

### 1、初识Vue

> vuejs文件分为“.min.js”与“.js”文件，区别在于其中带“.min”这个是生产版本（压缩版），不带“.min”的是测试版本（测试时用的，不压缩的）：
>
> - 生产版本
>   - 代码压缩（代码不具备可读性）
>   - 不支持vue调试工具
> - 开发版本
>   - 代码不压缩（代码具备可读性）
>   - **支持vue的调试工具**

以输出“Hello World”为例，使用Vue.js实现输出“Hello World”案例：

> **步骤**（仅限在vue的非工程化的环境下）
>
> - 在视图部分定义渲染的容器，正常情况下内容相对固定，一般是：
>
>   - ~~~html
>     <div id="app"></div>
>     ~~~
>
> - 通过`script`标签引入下载好的`vue.js`文件
>
> - 产生vue实例（js部分，需要去new）
>
>   - 需要给实例传递配置选项（格式是一个对象）
>   - 如果可能，会用到一些数据，数据需要在对象中声明（声明式渲染）
>
> - 如果需要展示数据的话，则需要使用特定的表达式（插值表达式，形式`{{表达式}}`，在视图部分写，哪里需要值就在哪里写）

代码片段如下：

~~~html
<body>
    <!-- 1. 定义渲染的容器 -->
    <div id="app">
        {{msg}}
        <div>
            <!-- 只要不出id=app这个容器的界限，不管多少深度，都没问题 -->
            {{msg}}
        </div>
    </div>
    <!-- 2. 引入vue.js文件 -->
    <script src="./js/vue.js"></script>
    <script>
        // 3. 产生vue实例（V是大写的），传递配置选项
        new Vue({
            // el => element，指定vue负责渲染的容器的选择器
            el: "#app",
            // data指定vue实例需要的数据（数据的初始化）
            data: {
                msg: "hello world",
            },
        });
    </script>
</body>
~~~

Vue实例细节分析：

- Vue参数对象属性
  - el：元素挂载的位置，值可以是CSS选择器或DOM元素
  - data：模型数据，值是一个对象（仅限于当前）

- 插值表达式`{{msg}}`
  - 将数据填充到HTML标签中

上述提及的都是前端vue框架的模板语法，当然vue的模板不仅仅是上述这个2个，还有更多的，比如后面要学习的：

- 指令
- 事件
- 流程控制
- ....



### 2、vue devtools工具安装

通过chrome中的谷歌插件商店安装Vue Devtools工具，此工具帮助我们进行vue数据调试所用，一定要安装。Vue工具在谷歌商店的地址是：https://chrome.google.com/webstore?utm_source=chrome-ntp-icon

> 请注意：打开chrome应用商店，**需要科学上网**才能访问到，至于怎么科学上网请各位自行解决。

![Vue工具谷歌商店](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/dc840deb63c247fb5b7fac6f162f3fece10832ae.png?sign=180564fbbac92d11b6e89e4e9d8df208&t=5f561a39)

安装好后打开Chrome的`开发者工具（F12或Ctrl+Shift+I）`即可使用：

![谷歌浏览器使用Vue工具](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/7ea8955be2b91f4c8530fdf7696fa2f5508b3a35.png?sign=2773c0e615128ca86b96c79bca31eaf4&t=5f561a6a)

**补充：如果自己解决不了科学上网问题，但是又需要用Vue开发工具那该怎么办？**

> 如果实在解决不了科学上网难题，Vue官方也提供了插件源码允许我们自己编译/构建Google Chrom插件，步骤如下（构建插件流程稍微麻烦一些<**不要求掌握如何构建**>，此处已为同学们构建好，可以直接使用）。
>
> ![Vue调试工具](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/6f094719844e04c1aa853b36c18b1e18c1ee6c2d.png?sign=55a5622a22b937b7b1b419ca67dafd6b&t=5f38fa24)

- 克隆仓库
  - Git仓库地址：https://github.com/vuejs/vue-devtools
- 安装依赖包
- 构建
- 打开Chrome扩展页面
- 开启开发者模式
- 加载已解压扩展，选择shells-chrome目录
- 将产生的`.crx`文件拖入谷歌浏览器`扩展程序`界面
- 在Windows策略管理器中添加Google策略模板文件，将插件对应的ID添加到`配置扩展程序白名单`
  - `.crx`和`.adm`文件已打包上传至公有云，可以点击访问<a href='http://2url.cc/l3M5x1' target='_blank' alt='vue-devtools'>2url.cc/l3M5x1</a>进行下载
- 在谷歌浏览器`扩展程序`管理界面中给`Vue.js devtools`插件授权
  - 允许访问文件网址
  - 收集各项错误



### 3、Vue模板语法

#### 3.1、插值表达式

**插值表达式：**是vue框架提供的一种在HTML模板中绑定数据的方式，使用`{{变量名}}`方式绑定Vue实例中data中的数据变量，会将绑定的数据实时的在视图中显示出来。

插值表达式的写法支持使用：

- 变量名
- **部分**JavaScript表达式
  - 注：`{{  }}`括起来的区域，就是一个就是js语法区域，在里面可以写部份的js语法。不能写 var a = 10;分支语句;循环语句
- 三元运算符
- 方法调用（方法必须需要先声明）
- ...

~~~html
<body>
    <div id="app">
        <!-- 直接使用变量名 -->
        <h5>{{name}}</h5>
        <!-- 运算 -->
        <h5>{{name + '--好的'}}</h5>
        <h5>{{ 1 + 1 }}</h5>
        <!-- 使用函数 -->
        <h5>{{title.substr(0,6)}}</h5>
        <!-- 三目运算 -->
        <h5>{{ age > 18 ? '成年' : '未成年'}}</h5>
    </div>
</body>
<script src="./js/vue.js"></script>
<script>
    var vm = new Vue({
        el: "#app",
        data: {
            title: "我是一个标题，你们看到没有",
            name: "张三",
            age: 20,
        },
    });
</script>
~~~



#### 3.2、指令

**问1：什么是指令？**

- [x] 指令的本质就是标签中的vue**自定义属性**
- [x] 指令格式以“v-”开始，例如：v-cloak，v-text、v-html等

**指令的含义：在vue的html中，以`v-`开头的自定义属性就是指令。**

详见官网对指令的说明：https://cn.vuejs.org/v2/api/#%E6%8C%87%E4%BB%A4

**问2：指令有什么作用？**

语法糖：复杂操作的简化形式

当表达式的值改变时，将其产生的连带影响，响应式地作用于页面（DOM）。（简化操作）

**小试牛刀**：v-text指令与v-html指令【相当于innertHTML和innerText】

> **官网**
>
> v-text：https://cn.vuejs.org/v2/api/#v-text
>
> v-html：https://cn.vuejs.org/v2/api/#v-html

友情提醒：v-html尽量少用甚至不用，因为可能引发XSS（跨站脚本攻击，XSS）攻击。

~~~html
<body>
    <div id="app">
        <!-- 插值表达式形式 -->
        <div>{{str1}}</div>
        <!-- 插值表达式此时与v-text是等效的 -->
        <div v-text='str2'></div>
        <div v-html='str1'></div>
    </div>
</body>

<script src="./js/vue.js"></script>
<script>
    new Vue({
        el: '#app',
        data: {
            str1: '迫使 Vue 实例重新渲染。注意它仅仅影响实例本身和插入插槽内容的子组件，而不是所有子组件。',
            str2: '<a href="http://www.baidu.com">百度</a>'
        }
    })
</script>
~~~



## 三、常用指令

### 1、v-cloak（了解）

**作用：**解决浏览器在加载页面时因存在时间差而产生的`闪动`问题

**原理：**先隐藏元素挂载位置，处理好渲染后再显示最终的结果

**注意：**需要与CSS规则一起使用

**文档地址：**https://cn.vuejs.org/v2/api/#v-cloak

**示例：**

~~~html
<style>
    [v-cloak] {
        display: none;
    }
</style>

<div v-cloak>
  {{ message }}
</div
~~~

> 如果后期有多个元素需要解决闪动问题，可以将`v-cloak`写在根元素上。



### 2、数据绑定指令

- v-text	填充纯文本
  - 相比插值表达式更加简洁
  - 不存在插值表达式的闪动问题

~~~html
<div id='app'>
	<span v-text="msg"></span>
	<!-- 和下面的一样 -->
	<span>{{msg}}</span>
</div>

<script src="./js/vue.js"></script>
<script>
  new Vue({
    el: '#app',
    data: {
      msg:'<a href="http://www.baidu.com/">百度一下</a>'
    }
  })
</script>
~~~



- v-html 	填充HTML片段
  - 存在安全问题
  - 本网站内部数据可以使用，来自第三方的数据不可使用

~~~html
<div id='app'>
    <div v-html="html"></div>
</div>

<script src="./js/vue.js"></script>
<script>
  new Vue({
    el: '#app',
    data: {
      html:'<a href="http://www.baidu.com/">百度一下</a>'
    }
  })
</script>
~~~



- v-pre	填充原始信息（对应的是以前html中的标签“<pre>”）
  - 跳过表达式的编译过程，显示原始信息 

~~~html
<span v-pre>{{ this will not be compiled }}</span>
~~~

> **有些时候我们不想指令中的表达式进行运行，只需要给表达式加个引号**。例如：

~~~html
<div v-html='"msg"'></div>
<div v-html="'msg'"></div>
~~~

针对后续想让指令属性值不解析的操作都可以这么去做。



### 3、v-once（了解）

**作用：**只渲染**元素**和组件**一次**，之后元素和组件将失去**响应式（数据层面）**功能（对于数据的一锤子买卖）

> **Q & A：**如何理解响应式？
>
> - 布局响应式：布局会随着设备尺寸的大小变化而变化的布局方式
> - **数据响应式：双向数据绑定**

**示例：**

~~~html
<div id="app">
	<h3>{{message}}</h3>
	<!-- 动态修改message值，此绑定将不会发生改变 -->
	<div v-once>{{message}}</div>
</div>
<script src="./js/vue.js"></script>
<script type='javascript'>
  const vm = new Vue({
      el: '#app',
      data: {
          message: '你好世界'
      }
  })
</script>
~~~



### 4、v-bind（重点）

**作用：**动态地绑定一个或多个`attribute`【实现可以允许我们在html内置的属性值中使用变量】

场景：复用某个数据的时候会使用。例如：飞猪官网

~~~html
<!-- v-bind：给非指令的属性使用变量 -->
<a v-bind:href="url" v-bind:target="target">{{alt}}</a>

<!-- v-bind的简写形式，实际使用这样的写法 -->
<a :href="url" :target="target">{{alt}}</a>
~~~

**示例代码**

~~~html
<body>
    <div id="app">
        <a :href="url" :target="type" :alt="alt" :num="100" :flag="true">{{alt}}</a>
        <a :href="url">{{alt}}</a>
    </div>
</body>
<script src="./js/vue.js"></script>
<script>
    new Vue({
        el: '#app',
        data: {
            url: 'https://www.fliggy.com/',
            type: '_blank',
            alt: '飞猪官网'
        }
    })
</script>
~~~

> 如果属性的值是变量，boolean类型或者number类型，需要使用绑定属性

### 5、v-on（重点）

#### 5.1、基本使用

**作用：**绑定事件监听器（事件绑定）

**示例：**

~~~html
<!-- 直接执行操作 -->
<!-- 常规写法 -->
<button v-on:click="num++"></button>
<!-- 缩写 -->
<button @click="num++"></button>

<!-- 事件处理函数调用：直接写函数名 -->
<button @click="say"></button>
<!-- 事件处理函数调用：常规调用 -->
<button @click="say('sth'， $event)"></button>
~~~

如果事件处理函数为自定义函数，则需要先进行定义，定义的方式如下：

~~~javascript
...
data: {
    ...
},
methods: {
    functionName: function(arg1,arg2,arg3,...){
        // something to do
    },
    ....
}
~~~

> 注意：事件绑定`v-on`属性表达式中切记不能直接写业务逻辑，例如`@click="alert('123')"`。换言之，就咋行内上是不允许使用内置函数的，必须要调用自己定义的函数，然后你可以在自定义的函数内使用内置函数。



**事件处理函数传参**

~~~html
<!-- 事件处理函数调用：直接写函数名 -->
<button @click="say"></button>

<!-- 事件处理函数调用：常规调用 -->
<button @click="say('hi',$event)"></button>
~~~

在不传递自定义参数的时候，上述两种用法均可以使用；但是如果需要传递自定义参数的话，则需要使用第2种方式。

> 事件对象的传递与接收注意点
>
> - 如果事件直接使用函数名并且不写小括号，那么**默认**会将事件对象作为唯一参数进行传递，可以在定义函数的位置直接定义一个形参，并且在函数内可以使用该形参
> - 如果使用常规的自定义函数调用（只要写了小括号），那么如果需要使用**事件对象则必须作为最后一个参数进行传递**，且事件对象的名称必须是“$event”

**示例代码**

~~~html
<style>
    #big {
        width: 300px;
        height: 300px;
        background-color: red;
    }
    #mid {
        width: 200px;
        height: 200px;
        background-color: green;
    }
    #sma {
        width: 100px;
        height: 100px;
        background-color: pink;
    }
</style>

<body>
    <div id="app">
        <div id="big" @click="say('大娃',$event)">
            <div id="mid" @click="say('二娃',$event)">
                <div id="sma" @click="say('三娃',$event)"></div>
            </div>
        </div>
    </div>
</body>

<script src="./js/vue.js"></script>
<script>
    new Vue({
        el: '#app',
        data: {

        },
        methods:{
            say: function(name,event){
                console.log('你点了' + name);
            }
        }
    })
</script>
~~~



#### 5.2、事件修饰符

含义：用来处理事件的特定行为（也是vue提供一些语法糖）

使用示例：

~~~html
<!-- 停止冒泡 -->
<button @click.stop="doThis"></button>
<!-- 阻止默认行为 -->
<button @click.prevent="doThis"></button>
<!--  串联修饰符 -->
<button @click.stop.prevent="doThis"></button>
~~~

更多事件修饰符请参考官方文档：https://cn.vuejs.org/v2/api/#v-on

**实例代码**

~~~vue
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .dawa {
            background: red;
            width: 400px;
            height: 400px;
        }
        .erwa {
            background: orange;
            height: 300px;
            width: 300px;
        }
        .sanwa {
            background: yellow;
            height: 200px;
            width: 200px;
        }
    </style>
</head>
<body>
    <div id="app">
        <!-- 套娃行为 -->
        <div class="dawa" @click="call_dawa">
            <div class="erwa" @click.stop="call_erwa">
                <div class="sanwa" @click.stop="call_sanwa">

                </div>
            </div>
        </div>
    </div>
    <script src="./js/vue.js"></script>
    <script>
        new Vue({
            el: "#app",
            data: {

            },
            methods:{
                call_dawa(){
                    console.log('大娃：收到');
                },
                call_erwa(){
                    console.log('二娃：收到');
                },
                call_sanwa(){
                    console.log('三娃：你说啥');
                }
            }
        })
    </script>
</body>
</html>
~~~



#### 5.3、按键修饰符

按键修饰符：按键事件

> 在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 `v-on` 在监听键盘事件时添加按键修饰符。

~~~html
<!-- 只有在 `key` 是 `Enter` 回车键的时候调用 -->
<input v-on:keyup.enter="submit">

<!-- 只有在 `key` 是 `Delete` 回车键的时候调用 -->
<input v-on:keyup.delete="handle">
~~~

更多按键修饰符请参考官方文档：[https://cn.vuejs.org/v2/guide/events.html#%E6%8C%89%E9%94%AE%E4%BF%AE%E9%A5%B0%E7%AC%A6](https://cn.vuejs.org/v2/guide/events.html#按键修饰符)



### 6、循环分支指令（重点）

#### 6.1、循环指令

**作用：**根据一组**数组**或对象的选项列表进行渲染。

**指令：**v-for 

> item in list
>
> Item of list
>
> (Item, index) of list
>
> Key

- 数组遍历使用示例：

~~~html
<!-- 模板部分 -->
<ul>
    <!-- 直接取值 -->
    <li v-for='item in fruits'>{{item}}</li>
    <!-- 带索引 -->
    <li v-for='(item,index) in fruits'>{{item}}{{index}}</li>
</ul>

<!-- JavaScript部分 -->
......
data: {
	fruits: ['apple','pear','banana','orange']
}
......
~~~

> 细节：key的作用，提高性能，不影响显示效果（`如果没有id，可以考虑使用索引替代`），切记`key`的值不能重复，只要遵循不重复的原则即可，值是什么无所谓。
>
> 十把锁十把钥匙
>
> 

~~~html
<ul>
    <li :key='item.id' v-for='(item,index) in fruits'>{{item}}</li>
</ul>
~~~

- 对象遍历使用示例：

~~~html
<!-- 模板部分 -->
<ul>
    <li v-for='(value,name,index) in obj'>{{value + '-' + name + '-' + index}}</li>
</ul>

<!-- JavaScript部分 -->
......
data: {
	obj: {
		username: 'zhangsan',
		age: 28,
		gender: 'male'
	}
}
......
~~~

**示例代码：**

~~~html
<body>
    <div id="app">
        <div>
            <ul>
                <li :key="index" v-for="(item,index) in cars">{{item}}</li>
            </ul>
        </div>
        <div>
            <ul>
                <li :key="index" v-for="(item,key,index) in user">{{key}}：{{item}}</li>
            </ul>
        </div>
    </div>
</body>
<script src="./js/vue.js"></script>
<script>
    new Vue({
        el: '#app',
        data: {
            cars: ['bmw','aodi','benci','haima'],
            user: {
                username: 'zhangsan',
                gender: 'mele',//性别，sex
                age: 22
            }
        }
    })
</script>
~~~



#### 6.2、分支指令

注意点：

- 基础语法
- 为什么v-show会出现在这里，与v-if系列有什么联系

**作用：**根据表达式的布尔值(true/false)进行判断是否**渲染**/显示该元素

- v-if
- v-else
- v-else-if

> 上述三个指令是分支中最常见的。根据需求，v-if可以单独使用，也可以配合v-else一起使用，也可以配合v-else-if和v-else一起使用。

- v-show

> v-show是根据表达式之真假值，切换元素的 `display` CSS属性（是根据表达式的布尔值来判断是否**显示**该元素）。

使用示例：

~~~html
<!-- 模板部分 -->
<div v-if="score >= 90">
  优秀
</div>
<div v-else-if="score >= 80 && score < 90">
  良好
</div>
<div v-else-if="score >= 70 && score < 80">
  一般
</div>
<div v-else>
  不及格
</div>
<!-- v-show -->
<div v-show='flag'>测试v-show</div>

<!-- JavaScript部分 -->
......
data: {
	score: 88,
	flag:false
}
......
~~~

> 思考：v-if系列与v-show的区别是什么？
>
> v-if：控制元素是否渲染
>
> v-show：控制元素是否显示（**已经渲染**，display:none;）

> v-if系列指令、v-show指令可以与v-for指令结合起来使用（循环+分支）。例如：

~~~html
<ul>
    <li v-for='(v,k,i) in obj' v-show='v==25'>{{v}}</li>
</ul>
~~~



### 7、综合案例：简易购物车

**案例效果**

![简易购物车案例效果](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/306aab7bc3f508529eacd7e352283a5670a36873.gif?sign=c1f7cd1b184d05b5a750c70759eb9a0a&t=5f5748db)

> 细节：
>
> - 展示基本的商品信息
> - 计算每个商品的小计
> - 商品数量的加、减操作
>   - +：增加商品数量，同时更新小计
>   - -：减少商品熟练，同时更新小计，如果本身为“1”，再点-号则需要移除商品

> 如果需要在Vue实例中访问自身data属性中的数据，可以使用以下方式：
>
> - **this.xxxxx**
> - this.$data.xxxxx
> - this._data.xxxxx

**参考数据源**

~~~javascript
var cartData = [
    {
        id: 1,
        name: '小米',
        price: 100,
        num: 1
    },
    {
        id: 2,
        name: '华为',
        price: 200,
        num: 1
    },
    {
        id: 3,
        name: '联想',
        price: 300,
        num: 1
    }
]
~~~

**参考核心代码**

~~~html
<body>
    <div id="app">
        <ul>
            <li v-for="(item,index) in cartData" style="list-style: none;">
                商品ID：{{item.id}}&emsp;&emsp;
                商品名称：{{item.name}}&emsp;&emsp;
                商品价格：{{item.price}}&emsp;&emsp;
                商品数量：<button @click="dec(item,index)">-</button>{{item.num}}<button @click="inc(item)">+</button>&emsp;&emsp;
                商品小计：{{item.price * item.num}}
            </li>
        </ul>
    </div>
</body>

<script src="./js/vue.js"></script>
<script>
    var cartData = [
        {id:1,name:'苹果',num:1,price:100},
        {id:2,name:'小米',num:1,price:200},
        {id:3,name:'华为',num:1,price:300},
    ]

    new Vue({
        el: '#app',
        data: {
            cartData
        },
        methods: {
            dec: function (item,index) {
                // 判断是否是1件
                if(item.num == 1){
                    confirm('机不可失，确定不要买一件吗？') && this.cartData.splice(index,1)
                }else{
                    item.num--
                }
            },
            inc: function (item) {
                item.num++
            }
        }
    })
</script>
~~~

> `&emsp;`表示`tab`，一个顶四个`&nbsp;`



### 8、样式绑定

#### 8.1、class样式绑定

- 对象语法（`用于控制开关切换`）【常用】

~~~html
<style>
/* CSS片段 */
.active {
	color: red;
}
</style>

<!-- HTML片段 -->
<div v-bind:class="{active: isActive}">class样式</div>

<script type='text/javascript'>
// JavaScript片段
data: {
	isActive: true
}
</script>
~~~



- 数组写法（了解）

~~~html
<style>
/* CSS片段 */
.active {
	color: red;
}
</style>

<!-- HTML片段 -->
<div v-bind:class="[activeClass]">数组写法</div>

<script type='text/javascript'>
// JavaScript片段
data: {
	activeClass: 'active'
}
</script>
~~~



#### 8.2、style样式处理（了解）

- 对象语法

~~~html
<!-- HTML片段 -->
<div:style="{color: redColor, fontSize: '20px'}">对象写法</div>

<script type='text/javascript'>
// JavaScript片段
data: {
	redColor: 'red'
}
</script>
~~~

- 数组语法

~~~html
<!-- HTML片段 -->
<div v-bind:style="[color, fontSize]">数组写法</div>

<script type='text/javascript'>
// JavaScript片段
data: {
	color: {
		color: 'red'
	},
	fontSize: {
		'font-size': '20px'
	}
}
</script>
~~~



### 9、v-model

**作用:**==表单==元素的绑定，实现了**双向数据绑定**，通过表单项可以更改数据。

- 实现类似以以前html中使用value属性给input设置默认值的效果（可以为表单项设置默认设置）
- 实现表单数据方便接收处理的环节（以前：获取dom，再获取value；现在直接更新到data，获取data数据即可）

![单向与双向数据绑定](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/9c5b0121053708abca7fb4fb7aad1ebbbccda672.png?sign=c753d4526e96e7bbb0e226e6b3036883&t=5f2d216b)

v-model会忽略所有表单元素的value、checked、selected特性的初始值,而总是将Vue实例的数据作为数据来源，应该在data选项中声明初始值。

- 普通文本框上的使用（直接将value属性替换成v-model即可）

~~~html
<div id='app'>
    <p>{{message}}</p>
    <input type='text' v-model='message'>

    <!--
    v-model其实是`语法糖`,它是下面这种写法的简写
    语法糖：这种语法对语言的功能并没有影响，但是更方便程序员使用
    -->
    <input type='text' :value='msg' @input='msg=$event.target.value'/>
</div>

<script type='text/javascript'>
new Vue({
    el: '#app',
    data: {
		msg: 'message默认值'
    }
})
</script>
~~~



- 多行文本框上的使用（使用v-model来替代标签之间写内容的方式）

~~~html
<div id='app'>
    <textarea v-model="message"></textarea>
</div>

<script type='text/javascript'>
new Vue({
	el: '#app',
	data: {
		message: '我是多行文本内容'
	}
})
</script>
~~~

**注意：在多行文本框中使用插值表达式无效（此时，其只能接受数据，不能改变数据）**



- 单个复选框上的使用

~~~html
<div id='app'>
    <input type="checkbox" v-model="checked">
</div>

<script type='text/javascript'>
new Vue({
	el: '#app',
	data:{
		checked:true
	}
})
</script>
~~~



- 多个复选框上的使用（需要使用v-model结合value）

~~~html
<div id='app'>
    <input type="checkbox" value="html" v-model="checkedNames">
    <input type="checkbox" value="css" v-model="checkedNames">
    <input type="checkbox" value="js" v-model="checkedNames">
</div>

<script type='text/javascript'>
new Vue({
	el: '#app',
	data:{
    	// 如果数组中有对应的value值，则此checkbox会被选中
		checkedNames:[]
	}
})
</script>
~~~

**注意：此种用法需要`input`标签提供`value`属性，并且需要注意属性的大小写要与数组元素的大小写一致**



- 单选按钮上的使用

~~~html
<div id='app'>
    男<input type="radio" name="sex" value="男" v-model="sex">
	女<input type="radio" name="sex" value="女" v-model="sex">
</div>

<script type='text/javascript'>
new Vue({
	el: '#app',
	data: {
		sex: '女'
	}
})
</script>
~~~



- 下拉框上的使用

~~~html
<div id='app'>
    <select v-model="selected">
        <option disabled>请选择</option>
        <option>HTML</option>
        <option>CSS</option>
        <option>JS</option>
    </select>
</div>

<script type='text/javascript'>
new Vue({
	el: '#app',
	data: {
		selected: 'JS'
	}
})
</script>
~~~

> 如果 `v-model` 表达式的初始值未能匹配任何选项，`<select>` 元素将被渲染为“未选中”状态。在 iOS 中，这会使用户无法选择第一个选项。因为这样的情况下，iOS 不会触发 change 事件。因此，更推荐像上面这样提供一个值为空的禁用选项。


- 修饰符

> .lazy：默认情况下Vue的数据同步采用`input`事件，使用`.lazy`将其修改为失去焦点时触发
>
> .number：自动将用户的输入值转为数值类型（如果能转的话）
>
> .trim：自动过滤用户输入的首尾空白字符



> `v-model` 在内部为不同的输入元素使用不同的 property 并抛出不同的事件：
>
> - text 和 textarea 元素使用 `value` property 和 `input` 事件；
> - checkbox 和 radio 使用 `checked` property 和 `change` 事件；
> - select 字段将 `value` 作为 prop 并将 `change` 作为事件。



### 10、综合案例：全选/全不选

知识点：v-model中的复选框（单个+多个）

代码见code中的文件。



## 四、Vue常用属性

### 1、自定义指令 - directive

[directive]:https://cn.vuejs.org/v2/guide/custom-directive.html

除了核心功能默认内置的指令，Vue也允许开发者注册自定义指令。有的情况下，对普通DOM元素进行底层操作，这时候就会用到自定义指令绑定到元素上执行相关操作。

**自定义指令分为：全局指令和局部指令**，当全局指令和局部指令同名时**以局部指令为准**（局部指令的优先级高于全局的）。

**问题：全局与局部有什么区别？**

- **在当前（非工程化，每一个文件都是一个html文件）的时候是没区别的**
- vue工程化的时候是有区别的
  - 全局的适用于整个项目的（常用）
  - 局部的适用于当前组件的

自定义指令**常用**钩子函数（名字固定的函数）有：

- bind：在**指令**第一次绑定到元素时调用（在**该环节中是获取不到父节点的**，父节点是null），序号：1
- inserted：被绑定**元素**插入父节点时调用（在**该环节中是可以获取到父节点的**），序号：2
- update：数据更新时调用，序号：3（该环节会重复触发）
- componentUpdated：指定元素及子节点更新完成后会触发
- unbind：取消绑定后触发

> 请注意：不管在定义全局还是局部自定义指令时，**所提及的指令名均是不带`v-`前缀的名称**。

**全局指令语法**

~~~js
// 无参
Vue.directive('指令名',{
	钩子函数名: function(el){
        // 业务逻辑
    	// el参数是挂载到的元素的DOM对象
    	// <div v-abc>123</div>
    }
}

// 传参
Vue.directive('指令名',{
	钩子函数名: function(el,binding){
    	let param = binding.value
        // 业务逻辑
    },
    ....
}
~~~

> **请务必注意，作为全局配置，不能将其写在指定的Vue实例里，后续其它全局配置亦是如此**

**局部自定义指令定义**

可以在`new Vue`的时候添加`directives`以注册局部自定义指令，局部自定义指令只能在当前组件实例中使用：

~~~javascript
directives: {
  指令名: {
    // 指令的定义
    钩子函数名: function (el,binding) {
      // 业务逻辑
    }
  }
}
~~~

**函数简写（了解，使用机会很少）**

> 部分时候，我们可能想在 `bind` **和 **`update` 时触发**相同**行为（如果只是其一，则还是单独分开声明），而不关心其它的钩子。那么这样写：

~~~javascript
// 全局
Vue.directive('指令名', function (el,binding) {
  // 业务逻辑
})

// 局部
directives: {
  指令名: function (el,binding) {
      // 业务逻辑
  }
}
~~~

> 在自定义指令的方法中，不能像以前的`methods`中的方法一样使用关键词`this`，此时`this`关键词指向的是`Window`对象。

案例：使用自定义指令实现以下效果

- 使用全局指令定义自定义的`v-red（不传参）`和`v-color（传参）`，在元素被插入时设置内容颜色
- 使用局部自定义指令实现`v-mobile（不传参）`验证用户输入的是否是合法的手机号，不合法手机号为红色，合法为黑色



### 2、计算属性 - computed

模板中放入太多的逻辑（方法）会让模板过重且难以维护，使用计算属性可以让模板变得简洁易于维护。计算属性是基于它们的响应式依赖进行**缓存**的，计算属性比较适合对多个变量或者对象进行处理后返回一个结果值，也就是数多个变量中的某一个值发生了变化则我们监控的这个值也就会发生变化。

计算属性定义在Vue对象中，通过关键词`computed`属性对象中定义一个个函数，并返回一个值，使用计算属性时和`data`中的数据使用方式一致。

核心点：

- 计算属性其在代码的表现也是方法，但是与methods不同
  - 计算属性必须有return
- 在某些场景下，计算属性的效率要比methods效率高
  - 计算属性支持数据的缓存操作（在依赖数据不变的情况下），而methods不行

**示例**

~~~html
<div id="app">
    <!-- 当多次调用 cfn计算属性时只要里面的 num值不改变,它会把第一次计算的结果直接返回直到data中的num值改变 计算属性才会重新发生计算 -->
    <div>{{ cfn }}</div>
    <div>{{ cfn }}</div>
    <!-- 调用methods中的方法的时候  他每次会重新调用 -->
    <div>{{ fn() }}</div>
    <div>{{ fn() }}</div>
</div>
<script src="./js/vue.js"></script>
<script type="text/javascript">
    const vm = new Vue({
        el: "#app",
        data: {
            num: 10,
        },
        // 方法
        methods: {
            fn() {
                console.log("methods");
                return this.num;
            },
        },
        // 计算属性
        computed: {
            cfn() {
                console.log("computed");
                return this.num;
            },
        },
    });
</script>
~~~

**注意：**只要依赖的数据源不发生改变，计算属性里的对应方法就只被调用1次，其它时候被调用时则使用缓存。提高效率。



### 3、监听器 - watch

使用watch来侦听**data**中数据的变化，**watch中的属性（watch是对象格式）一定是data 中已经存在的数据**。（特殊情况除外）

**使用场景：**数据变化时执行**异步或开销比较大的操作**。

**典型应用：**http://www.pinyinzi.cn/

![监听器](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/6ae51459d0c21c076baf58e26829a6265e3ee938.png?sign=87b53c566e524496faa45fc17ee38816&t=5f3648ac)

**案例：**给定三个输入框，第一个为姓输入框，第二个为名输入框，第三个为姓名组合结果框；要求当用户更新姓或名后，第三个输入框自动生成完整的姓名结果。

**语法**

~~~vue
new Vue({
	.....
	watch: {
		data中数据的名称: fn方法,
		....
	}
})
~~~

**参考代码：**

~~~html
<div id="app">
    <p><input type="text" v-model='firstName' placeholder="姓" /></p>
    <p><input type="text" v-model='lastName' placeholder="名" /></p>
    <p><input type="text" v-model='fullName' placeholder="全名" /></p>
</div>

<script src="./js/vue.js"></script>
<script type="text/javascript">
    const vm = new Vue({
        el: '#app',
        data: {
            firstName: '',
            lastName: '',
            fullName: ''
        },
        watch: {
            firstName: function(val) {
                this.fullName = val + ' ' + this.lastName
            },
            lastName: function(val) {
                this.fullName = this.firstName + ' ' + val
            }
        }
    })
</script>
~~~

> 注意点：
>
> - 声明监听器，使用的关键词是`watch`
> - 每个监听器的方法，可以接受2个参数，第一个参数是新的值，第二个参数是之前的值

**注意：**当需要监听一个对象的改变时，普通的watch方法无法监听到对象内部属性的改变，此时就需要deep属性对对象进行**深度监听**。

**使用对象的数据形式改写上述案例参考代码：**

~~~html
<div id="app">
    <p><input type="text" v-model='userinfo.firstName' placeholder="姓" /></p>
    <p><input type="text" v-model='userinfo.lastName' placeholder="名" /></p>
    <p><input type="text" v-model='userinfo.fullName' placeholder="全名" /></p>
</div>

<script src="./js/vue.js"></script>
<script type="text/javascript">
    const vm = new Vue({
        el: '#app',
        data: {
            userinfo: {
                firstName: '',
                lastName: '',
                fullName: ''
            }
        },
        watch: {
            userinfo: {
                // handler是固定的写法
                handler(val) {
                    this.userinfo.fullName = val.firstName + ' ' + val.lastName
                    // 对象支持引用传值
                    val.fullName = val.firstName + ' ' + val.lastName
                },
                deep: true
            }
        }
    })
</script>
~~~



### 4、综合案例：完善购物车

**进一步需求：**

- 增加自动计算总价功能，只计算被选中的商品【计算属性】
- 增加反选功能【事件绑定】
- 当手动选中全部商品，`全选`复选框自动选中，但凡有一个商品的复选框没有被选中，则`全选`复选框不选中【监听器】

实现代码参考代码文件。



### 5、过滤器 - filter

**作用：**格式化数据，比如将字符串格式化为首字母大写、将日期格式化为指定的格式等。

- 过滤器可以定义成全局过滤器和局部过滤器。
- **过滤器的本质就是一个方法**，使用过滤器实际上就相当于方法调用，仅是书写形式上的差异（使用的时候需要用“|”（shift + \），其也可以被称之为`管道`或`变量/数据修饰符`）
  - 语法：
    - {{待修饰的数据|过滤器方法名}}
    - {{待修饰的数据|过滤器方法名(参数1,参数2....)}}
- 这玩意在vue3中已经废弃了
  - vue3中解决办法是通过methods来替代

![过滤器](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/82ec23d614d0bf55ff0e2ecc1ac9414db2607490.png?sign=019afa9de124d3e56fb0fb0584616f73&t=5f364f40)

**声明语法：**

~~~javascript
// 全局过滤器
Vue.filter('过滤器名称',function(value[,arg1,arg2...]){
	//过滤器业务逻辑
	return ....
})

// 局部过滤器
el: '#app',
data: {},
filters: {
    过滤器名称: function(value[,arg1,arg2...]){
        return something
    },
    // ....
}
~~~

> 过滤器的处理函数中的第一个参数**固定**是`绑定的待处理数据`，后续可以根据需要添加自定义参数



**使用语法：**

~~~html
<!-- 过滤器使用 -->
<div>{{msg | upper}}</div>

<!-- 过滤器允许连续使用，“前 → 后”按顺序执行 -->
<div>{{msg | upper | lower}}</div>

<!-- 过滤器支持在v-bind中使用 -->
<div v-bind:id='id | formatId'></div>

<!-- 过滤器支持传参 -->
<div>{{msg | mysub(1,2)}}</div>
~~~



**案例：声明转字母为大写的全局过滤器和转字母为小写的局部过滤器并使用**

~~~html
<body>
    <div id="app">
        <h4>{{msg | toUpper}}</h4>
        <h4>{{msg | toLower}}</h4>
    </div>
</body>

<script src="./js/vue.js"></script>
<script type="text/javascript">
    // 全局过滤器：转字母为大写
    Vue.filter('toUpper',(val) => {
        return val.toUpperCase()
    })

    const vm = new Vue({
        el: '#app',
        data: {
            msg: 'HeLLo WoRld'
        },
        // 局部过滤器：转字母为小写
        filters: {
            toLower: (val) => {
                return val.toLowerCase()
            }
        }
    })
</script>
~~~



### 6、混入 - mixins

混入（mixins）是一种分发Vue组件中**可复用**功能的非常灵活的方式。**混入对象可以包含任意组件选项**。当组件使用混入对象时，==所有混入对象（加的水）的选项将被混入该组件本身的选项（锅底）。==

通俗来讲，就是把一部分可复用的代码片段，加入到另一个代码中。

混入分为全局混入和局部混入。

![混入](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/e090362ac96d806e9cec71c693b62f2640ea9967.jpeg?sign=553e389ab69879e18d97d6c7520f7daa&t=5f58b1a8)

**示例：**

- 局部混入（按需混入）【推荐】

~~~html
<script src="./js/vue.js"></script>
<script type="text/javascript">
    // 定义一个混入对象（局部混入）
    var myMixin = {
        created: function () {
            this.hello();
        },
        methods: {
            hello: function () {
                console.log("hello from mixin!");
            },
        },
        computed:{
            ....
        }
    };
    // Vue实例
    const vm = new Vue({
        mixins: [myMixin],
    });
</script>
~~~

- 全局混入（强制混入）

~~~html
<script src="./js/vue.js"></script>
<script type="text/javascript">
    // 全局混入
    Vue.mixin({
        created: function () {
            var myOption = this.myOption;
            if (myOption) {
                console.log(myOption);
            }
        },
    });

    new Vue({
        data: {
            myOption: "hello!",
        }
    });
</script>
~~~

> **注意事项**

- 当组件和混入对象含有同名选项时，这些选项将以恰当的方式进行“合并”，合并策略：
  - `data`数据对象发生冲突时以组件（被混入对象）数据优先
  - 同名钩子函数（生命周期函数）将合并为一个数组，都将被调用，并且混入对象的钩子将在组件自身钩子**之前**调用
  - 值为对象的选项，例如 `methods`、`components` 和 `directives`，将被合并为同一个对象。两个对象键名冲突时，取组件对象（自身）的键值对
- 全局注册使用时需要格外小心！一旦使用全局混入，它将影响**每一个**之后创建的 Vue 实例





### 7、生命周期

生命周期：从vue实例产生开始到vue实例被销毁这段时间所经历的过程。

vue更像工具人，在整个过程中只会按照作者预设的程序去做事，不能由开发者去控制或者diy。如果这样开发时限制是比较多的，因此作者开放了生命周期，允许我们定义vue在特定的时候去做我们让其做的事情（钩子函数）。

每个 Vue 实例在被创建之前都要经过一系列的初始化过程。例如需要设置数据监听、编译模板、挂载实例到 DOM，在数据变化时更新 DOM 等。同时在这个过程中也会运行一些叫做**生命周期钩子**的函数，目的是给予用户在一些特定的场景下添加他们自己代码的机会。

vue2中一共有11个生命周期。

Vue生命周期的**主要阶段**：

- 挂载（初始化相关属性）
  - beforeCreate
    - **注意点**：在此时不能获取data中的数据，也就是说`this.msg`得到的是`undefined`
  - created
  - beforeMount
  - mounted【页面加载完毕的时候就是此时】
    - **注意点**：默认情况下，在组件的生命周期中只会触发一次
- 更新（元素或组件的变更操作）
  - beforeUpdate
  - updated
    - **注意点**：可以重复触发的
- 销毁（销毁相关属性）
  - beforeDestroy
    - **注意点**：
  - destroyed

> 销毁（手动）使用`this.$destroy()`

![生命周期](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/5d6a79ad2a3b74d4ad9d70f868de0545f9939b8f.png?sign=b2936e9953891efac26abe8060495936&t=5f365858)

关于8个生命周期涉及到的方法，可以参考Vue官网API：[https://cn.vuejs.org/v2/api/#%E9%80%89%E9%A1%B9-%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E9%92%A9%E5%AD%90](https://cn.vuejs.org/v2/api/#选项-生命周期钩子)



补充：如果涉及到父子（一个组件包了另外一个组件）组件的话，则生命周期会怎么执行？

![](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/12/b79b0b2a8fecf81dbd0c701435abc3347a75d601.jpeg?sign=62fd7bf931784d222500e4e1d7ee5c5d&t=5fe5c26e)





### 8、虚拟DOM与diff算法

**什么是虚拟DOM？**

![虚拟DOM](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/7782f6424492630815195ed5722bdae78448601c.png?sign=e33c1bcebed7f86de415715793bb5444&t=5f60a247)

定义：指将真实的dom按照特定的语法转化（抽象）成一个js对象，这个**js对象称之为虚拟dom**。



**什么是diff（different）算法？**

差异比较算法的一种，把树形结构按照层级分解，只**比较同级**元素。不同层级的节点只有创建和删除操作

![diff算法](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/925fb1057a940bea0ea1863cb6df88c72496d65f.png?sign=a480a62fcd8497af8a60acd193b4facd&t=5f60a529)

**`虚拟DOM+diff算法`的方式与`传统DOM操作`相比，有什么好处？**

**传统DOM操作**：在一次操作中，往往会伴随多次个DOM节点更新，浏览器收到第一个DOM请求后并不知道还有若干次更新操作，因此会马上执行流程，最终执行若干次次。在后续找DOM坐标的时候，可能因为前期更新DOM导致了后续需要寻找的DOM坐标发生了变化。而操作DOM频繁还会出现页面卡顿，影响用户体验。

**虚拟DOM+diff算法**：若一次操作中有若干次更新DOM的动作，虚拟DOM不会立即操作DOM，而是将这若干次更新的diff内容保存到本地一个JS对象中，最终将这个JS对象**一次性**放到DOM树上，再进行后续操作，避免大量无谓的计算量。

建议：面试之前一定要去找下比较正规的理论性的东西。



### 9、双向数据绑定原理

面试可能会被大概率问到，需要领悟其中的关键词“代理”、“Object.defineProperty（vue2）”、“Proxy（vue3）”

核心：数据订阅、数据劫持（代理）

**当把一个普通的JavaScript对象传给Vue实例的data选项，Vue将遍历此对象所有的属性，使用Object.defineProperty把这些属性全部转为getter（获取）/setter（设置）。**

```javascript
Object.defineProperty(obj, prop, descriptor)
// 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象。
// 应当直接在Object构造器对象上调用此方法，而不是在任意一个Object类型的实例上调用。
```

> ***obj***
>
> 要定义属性的对象。
>
> ***prop***
>
> 要定义或修改的属性的名称 。
>
> ***descriptor***
>
> 要定义选项，“{    }”。在这里面设置getter和setter。

**示例代码：**

~~~html
<body>
    <div id="app">
        <div>
            <!-- 输入框 -->
            <input type="text" id="inpt" oninput="changeVal(this.value)" />
        </div>
        <div id="content"></div>
    </div>

    <script>
        // 1. 定义数据源
        var data = {
            msg: "hello world.",
        };
        // 等同于之前的data属性

        // 2. 通过dom操作将数据写在页面上（一锤子买卖）
        document.getElementById("inpt").value = data.msg;
        document.getElementById("content").innerText = data.msg;

        // 3. 通过Object.defineProperty()去实现数据的劫持(代理)
        var obj = {};
        Object.defineProperty(obj, "proxy", {
            // 设置getter和setter
            // 代理获取数据
            get() {
                return data.msg;
            },
            // 代理设置数据
            set(val) {
                data.msg = val;
                document.getElementById("content").innerText = val;
            },
        });

        // 4. input事件的处理程序
        function changeVal(val){
            // console.log(val);
            // 更新数据源
            obj.proxy = val;
        }
    </script>
</body>
~~~

vue2与vue3双向数据绑定的实现比较参考：

https://www.jianshu.com/p/255d4dec710a



## 五、网络请求

### 1、XHR

浏览器对XMLHttpRequest对象的支持度不足, 创建 XMLHttpRequest 对象时需要对IE浏览器做的兼容解决。（自己去回顾）

- 兼容性
- 代码量

回顾：XHR

- readyState：我们可以把xhr对象的工作内容划分成若干部分，每一个部分在执行的时候都对应着一个序号，序号就用readyState表示。
  - 0-4：
    - 0表示未初始化
    - 1请求已经装载
    - 2已经得到响应
    - 3正在解析返回数据
    - **4表示请求已完成**（完成=成功？）
- status（HTTP响应状态码）
  - **200：OK，成功**（以2开头）
  - 3XX【重定向系列的状态码】
    - 301：永久重定向
    - 302：临时重定向
    - 307：内部浏览器（缓存）重定向
  - 4XX【错误系列】（错误对半开，可能自己错误，也可能后端错误）
    - 400：bad request，错误请求
    - **401：鉴权失败**
    - **403：禁止访问**
    - **404：找不到对应的资源**
    - 405：方法不被允许
  - 5XX【服务器错误，环境问题】，只要是5开头的直接找你们后端
    - 500：服务器内部错误（代码、环境问题）
    - 502：bad Getway，错误网关

**案例：使用XHR请求全国高校数据接口**

- 接口地址
  - https://api.i-lynn.cn/college
  - 只循环展示`list`信息即可
  - 接口可以直接被跨域请求（后端做好了cors）
- 这个支持get/post请求类型

- 案例效果

![高校数据](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/6f67f15f5d33030c4b2f7bae59dca41dc234f102.png?sign=2bf279b1cbe1a290a957a1cf0957b108&t=5f58c66c)

**参考代码：**

~~~html
<!-- 
涉及知识点：网络请求xhr，v-for，注意this指向问题
-->
<body>
    <div id="app">
        <ul>
            <li v-for="item in list" :key="item.area">
                {{item.area}}：{{item.counts}}所
            </li>
        </ul>
    </div>
    <script src="./js/vue.js"></script>
    <script>
        new Vue({
            el: "#app",
            data: {
                list: []
            },
            // 发起网络请求
            created(){
                // xhr步骤
                // 1. 产生xhr实例
                var xhr = new XMLHttpRequest();
                // var _ = this;
                // 2. 设置处理程序
                xhr.onreadystatechange = () => {
                    // 判断是否成功
                    if(xhr.readyState == 4 && xhr.status == 200){
                        // console.log(this);
                        // _.list = JSON.parse(xhr.responseText).list
                        this.list = JSON.parse(xhr.responseText).list
                    }
                }
                // GET
                // 3. 打开请求
                // xhr.open("get","https://api.i-lynn.cn/college");
                // 4. 发送请求
                // xhr.send();

                // POST
                // 3. 打开请求
                xhr.open("post","https://api.i-lynn.cn/college");
                // 是否要传参，如果要还要加以下代码
                xhr.setRequestHeader("content-type","application/x-www-form-urlencoded")
                // 4. 发送请求
                xhr.send("type=2");
            }
        });
    </script>
</body>
~~~



### 2、jQuery

jQuery类的引入解决自己写兼容的烦恼，但现在只是使用了jQuery库中的网络请求功能，而jQuery中大量的dom的方法都是无效引入了，有点大材小用的意思。

**基本语法**

~~~javascript
$.ajax({
	url,
	type:get/post,
	data,
	dataType:json/text/xml/html/jsonp
	success:function(res){},
	error:function(){},
    complete: function(){}
});
// $.ajax(url,{type....})

$.get(url,data,callback,dataType)

$.post(url,data,callback,dataType)

// $.ajax是$.get与$.post的底层实现
~~~

**使用jQuery方式改写`XHR`部分案例**

~~~html
<body>
    <div id="app">
        <ul>
            <li v-for="item in list" :key="item.area">
                {{item.area}}：{{item.counts}}所
            </li>
        </ul>
    </div>
    <script src="./js/vue.js"></script>
    <!-- 引入jq -->
    <script src="./js/jquery-3.5.1.min.js"></script>
    <script>
        new Vue({
            el: "#app",
            data: {
                list: [],
            },
            created() {
                // 使用jq实现
                $.ajax({
                    url: "https://api.i-lynn.cn/college",
                    data: {},
                    type: "get",
                    dataType: "json", // text、xml
                    // 注意this指向问题
                    success: (data) => {
                        this.list = data.list;
                    },
                });
            },
        });
    </script>
</body>
~~~

> async：关键词，用于函数声明关键词`function`之前，标记当前的函数为异步函数
>
> await：关键词，让当前关键词的行代码执行之后等到到结果之后再去执行后续代码
>
> 两个关键词一般同时使用，并且是**一个async对应至少一个await**。



### 3、fetch

- **由HTML5提供的内置API**

- 更加简单的数据获取方式，功能更强大、灵活，可以看作是xhr的升级版
- 基于Promise实现（**强烈给个建议：宏任务、微任务、promise**）
- fetch支持很多请求方式，但默认为`GET`请求，如果需要使用其他方式可以通过第二个自选参数的`method`选项去指定

**语法结构**

~~~javascript
fetch(url[,some settings]).then(fn2)	// 首个then：处理数据的格式
		  .then(fn3)		// 第二个then是处理业务逻辑的
		  ...
          .catch(fn)
// catch，（try catch）
~~~

**用法示例**

~~~javascript
// 通过url表达式来传递数据（GET）
fetch("http://xxx/?id=123")
    .then(res => res.json())	// 将收到的数据进行转化，转化成json格式
    .then(data => console.log(data));	// 最终可以获得数据并写业务逻辑

// post标准提交(表单数据)
fetch("http://xxxx/post", {
    method: "post",		// 请求类型限制
    body: "uname=lisi&pwd=123",	// 提交的数据
    headers: {
        "Content-Type": "application/x-www-form-urlencoded",
    },
	})
    .then(res => res.json())
    .then(data => console.log(data));

// post提交json数据（接口开发）
fetch("http://localhost:3000/books", {
    method: "post",
    body: JSON.stringify({
        uname: "lisi",
        pwd: "123",
    }),
    headers: {
        "Content-Type": "application/json",
    },
	})
    .then(res => res.json())
    .then(data => console.log(data));
~~~

> 注意：fetch 不会发送 cookies。除非你使用了credentials 的初始化选项`credentials: "include"`

在上述代码示例中我们会看到有个`json()`方法，它是fetch的响应结果处理方法，fetch的常用响应结果处理方法有：

- text()：将返回体处理成字符串类型
- json()：返回结果和JSON.parse(responseText)一样

**使用fetch方式改写`XHR`部分案例**

~~~html
<body>
    <div id="app">
        <ul>
            <li v-for="item in list" :key="item.area">
                {{item.area}}：{{item.counts}}所
            </li>
        </ul>
    </div>
    <script src="./js/vue.js"></script>
    <script>
        new Vue({
            el: "#app",
            data: {
                list: [],
            },
            created() {
                // 不需要引入fetch
                fetch("https://api.i-lynn.cn/college")
                    .then((res) => res.json())
                    .then((data) => (this.list = data.list));
            },
        });
    </script>
</body>
~~~

![预检请求](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/d0ab6d2cee41c413339131ab1d907417b0a69cf1.png?sign=7b7a9b880a6b506fc6205c57e410f047&t=5f631b81)

> 当异步请求为非传统的`GET`与`POST`的时候，浏览器会先发送一个请求给接口地址，去询问当前服务器是否是否支持该请求类型（请求动词），如果支持，才会继续发送异步请求，否则不发送。
>
> 那么这个预先发送的请求，称之为`预检请求`，其请求动词是`OPTIONS`。
>
> 后期学习的`PUT`、`DELETE`等特殊的请求动词都会触发预检请求。

![预检请求动词](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/e19708ff08dddab7e37eb91b631c1f89e949dc3f.png?sign=7d8ee2eb8e20ea339d492f6fb39c5ae1&t=5f631c2c)



### 4、axios

文档：https://www.kancloud.cn/yunye/axios/234845

axios 是一个基于 promise 的 **HTTP ==库==**，可以用在浏览器和node.js中。**axios是vue作者推荐使用的网络请求库**，它具有以下特性：

- 支持浏览器和node.js（降低学习成本） 
- 支持promise
- 能够拦截`请求和响应`（拦截器）
- 自动转换json数据

**在使用axios之前需要在对应的模板文件中引入axios的js库文件**，随后按照以下用法使用axios：

~~~javascript
// GET请求方式
axios.get('/get_data?id=10010').then(ret => console.log(ret.data))
axios.get('/get_data',{
    params: {
        id: 10010,
        name: 'zhangsan',
        age: 26
    }
}).then(ret => console.log(ret.data))

//POST请求方式
// 参数是对象形式的，axios发送的请求头是application/json
axios.post('/set_data', {
  	firstName: 'zhang',
  	lastName: 'san'
}).then(ret => { })
// 参数是字符串形式的，axios发送的请求头是application/x-www-form-urlencoded
axios.post('/set_data',"firstName=zhang&lastName=san").then(ret => { })

// 先不指定请求类型，在配置中去指定请求类型（类似$.ajax）
axios({
  	method: 'post',
  	url: 'set_data',
    // 超时时间：如果请求花的时候超过了预设时间，则请求取消
  	timeout: 1000,
  	headers: {'头信息名': '头信息值'},
  	data: "username=zhangsan&type=2"
}).then(ret => { })
~~~

当然axios**除了**支持传统的`GET`和`POST`方式**以外**，常见的请求方式还支持：

- put：修改数据
- delete：删除数据

> 需要注意，**针对POST/PUT请求**，此处的参数提交格式以参数形式为准，如果是字符串（a=b&c=d形式），则发送表单格式（"Content-Type": "application/x-www-form-urlencoded"）；如果是对象，则发送json格式（"Content-Type": "application/json"）。

以上方的axios请求示例为例，axios响应结果（`ret`）的主要属性有：

- **data：实际响应回来的数据（最常用）**
- headers：响应头信息
- status：响应状态码
- statusText：响应状态信息
- config
- request

另外需要注意的是，在使用axios发送请求之前它允许我们通过**全局配置**做一些设置，这样可以方便后续的请求操作，例如：

- axios.defaults.timeout = 3000【设置超时时间】
- axios.defaults.baseURL = 'http://localhost/app'【设置默认地址】
- axios.defaults.headers['_token'] = '123123123'【设置请求头信息，通用头信息】
  - axios.defaults.headers.get['_token'] = '123123'
  - axios.defaults.headers.post['_token'] = '123123'
  - axios.defaults.headers.common['_token'] = '123123'【通用头信息，common可以不写】
- ...

**使用axios方式改写`XHR`部分案例**

~~~html
<body>
    <div id="app">
        <ul>
            <li v-for="item in list" :key="item.area">{{item.area}}：{{item.counts}}所</li>
        </ul>
    </div>
    <script src="./js/vue.js"></script>
    <!-- 引入axios -->
    <script src="./js/axios.min.js"></script>
    <script>
        new Vue({
            el: "#app",
            data: {
                list: [],
            },
            created() {
                // axios.get("https://api.i-lynn.cn/college").then((ret) => {
                //     if (ret.status == 200) {
                //         this.list = ret.data.list;
                //         // this.list = ret.data.data;
                //     }
                // });

                // 发送json格式的post请求
                // axios.post("https://api.i-lynn.cn/college", { type: 2 }).then((ret) => (this.list = ret.data.list));

                // 发送字符串形式的表单请求
                axios.post("https://api.i-lynn.cn/college", "type=2").then((ret) => (this.list = ret.data.list));
            },
        });
    </script>
</body>
~~~



## 六、Vue组件

核心：

- 声明式渲染
- 组件化

### 1、什么是组件

组件 （Component）是 Vue.js 最强大的功能之一，**组件是一个自定义HTML元素（标签）**或称为一个模块，包括所需的模板（HTML）、逻辑（JavaScript）和样式（CSS）。

**组件化开发的特点：**

- 标准
- 分治（解耦）
- 重用
- 组合

组件也是有`全局（component）`与`局部（components）`之分。



### 2、组件的注册及使用

在使用组件时需要注意以下几点：

- 构造 Vue 实例时传入的各种选项**大多数**都可以基于原格式在组件里使用，只有一个例外：**data必须是函数，同时这个函数要求必须返回一个对象**

~~~javascript
data: function(){
    return {
        msg: '你好世界'
    }
}
~~~

- 组件模板`template`

  - 必须是单个根元素 --- 来源于 react 中 jsx（javascriptxml）思想

  - ~~~html
    <!-- 单个根元素 -->
    <div>
        <ul>
            <li></li>
        </ul>
        <ul>
            <li></li>
        </ul>
    </div>
    
    <!-- 不符合单个根元素的情况 -->
    <p></p>
    <p></p>
    ~~~

  - 支持模板字符串形式

- 组件名称命名方式

  - 短横线方式（推荐）
    - my-component
  - 大驼峰方式（只能在其他组件模板字符串中使用，不能在HTML模板中**直接**使用）
    - MyComponent

> 大驼峰式组件名不能在HTML模板中直接使用，如果需要在HTML模板中使用，需要将其进行特定规则转化：
>
> - 首字母从大写转为小写
> - 后续每遇到大写字母都要转化成小写并且在转化后的小写字母前加`-`
>
> 例如，`WoDeZuJian`这个大驼峰组件名在HTML中使用的时候需要写成`wo-de-zu-jian`

组件使用分为全局注册组件以及局部注册组件

>全局： --- new Vue之前定义
>
>​	全局自定义指令，全局过滤器，全局混入
>
>局部：--- vue的实例内部添加选项
>
>​	局部自定义指令，局部过滤器， 局部混入

#### 2.1、全局组件

全局组件注册形式如下：

~~~javascript
// 声明全局组件
Vue.component(componentName,{
    // 存放该组件需要使用的数据
    data: function(){
        return {
            
        }
    },
    // 用于定义组件的视图内容
    template: '组件模版内容'
})
~~~

上述示例中，`component()`的第一个参数是`组件名`（**实则可以看作是HTML标签名称**），第二个参数是一个对象形式的选项，里面存放组件的声明信息。全局组件注册后，任何Vue实例都可以使用。

例如，有以下代码：

~~~javascript
// 声明一个全局的HelloWorld组件
Vue.component('HelloWorld', {
  	data: function(){
    	return {
      		msg: 'HelloWorld'
    	}
  	},
  	template: '<div>{{msg}}</div>'
});
~~~

课堂案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <my-com></my-com>
    <!-- 不管定义组件是使用的 短横线方式还是大驼峰式，在html模版中，只能使用 短横线方式 -->
    <!-- <MyCom></MyCom> -->
  </div>
</body>
<script>

  // 全局注册组件
  // Vue.component('组件名称', 组件选项)
  // 组件是特殊的vue实例
  // 特殊 data 是一个函数，必须返回一个对象
  // Vue.component('my-com', {
  //   template: `<h1>hello world - {{ msg }}</h1>`,
  //   data () {
  //     return {
  //       msg: '您好'
  //     }
  //   }
  // })
  Vue.component('MyCom', {
    template: `<h1>hello world - {{ msg }}</h1>`,
    data () {
      return {
        msg: '您好'
      }
    }
  })
  new Vue({
    el: '#app',
    data: {}
  })
</script>
</html>
```

> 为什么组件的data必须是一个函数？https://cn.vuejs.org/v2/api/#data
>
> 函数拥有自己的作用域
>
> 当一个**组件**被定义，`data` 必须声明为返回一个初始数据对象的函数，因为组件可能被用来创建多个实例。如果 `data` 仍然是一个纯粹的对象，则所有的实例将**共享引用**同一个数据对象！通过提供 `data` 函数，每次创建一个新实例后，我们能够调用 `data` 函数，从而返回初始数据的一个全新副本数据对象。

#### 2.2、局部组件

局部组件定义后只能在当前注册它的Vue实例中使用，其是通过某个 Vue 实例/组件的实例选项 components 注册。

例如，有以下代码：

~~~javascript
var Child = {
  	template: '<div>A custom component!</div>'
}
new Vue({
  	components: {
    	// <my-component/> 将只在父组件模板中可用
    	'my-component': Child,
        // <child/>
        Child
  	}
})
~~~

课堂案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <my-com></my-com>
    <!-- <MyCom></MyCom> -->
  </div>
</body>
<script>
  // 局部注册组件
  // 在vue的实例选项中添加 components 选项
  
  new Vue({
    el: '#app',
    data: {},
    components: {
      // 'my-com': {
      //   // 必须保证组件的模版中 只有一个顶级的标签
      //   template: '<div><h2>您好世界{{ msg }}</h2>{{msg}}</div>',
      //   data () {
      //     return {
      //       msg: 'hello'
      //     }
      //   }
      // }
      MyCom: {
        // 必须保证组件的模版中 只有一个顶级的标签
        template: '<div><h2>您好世界{{ msg }}</h2>{{msg}}</div>',
        data () {
          return {
            msg: 'hello'
          }
        },
        mounted () {
          console.log('mounted')
        }
      }
    }
  })
</script>
</html>
```

> 如果组件的逻辑特别多，使用起来肯定不方便



#### 2.3 先定义组件后注册

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <my-com></my-com>
  </div>
</body>
<script>
  // 先定义定义组件，再注册组件
  const MyCom = {
    // 必须保证组件的模版中 只有一个顶级的标签
    template: '<div><h2>您好世界{{ msg }}</h2>{{msg}}</div>',
    data () {
      return {
        msg: 'hello'
      }
    },
    mounted () {
      console.log('mounted')
    }
  }
  // Vue.component('MyCom', MyCom)
  new Vue({
    el: '#app',
    data: {},
    components: {
      // 局部注册组件
      MyCom: MyCom
    }
  })
</script>
</html>
```

> 如果组件的模版内容特别多

#### 2.4 抽离组件的模版

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <my-com></my-com>
  </div>
</body>
<!-- 抽离了组件的模版 -->
<template id="mycom">
  <div>
    <h2>您好世界{{ msg }}</h2>
    {{msg}}
  </div>
</template>
<script>
  // 先定义定义组件，再注册组件
  const MyCom = {
    // 以id来绑定使用哪一个模版
    template: '#mycom',
    data () {
      return {
        msg: 'hello'
      }
    },
    mounted () {
      console.log('mounted')
    }
  }
  // Vue.component('MyCom', MyCom)
  new Vue({
    el: '#app',
    data: {},
    components: {
      // 局部注册组件
      MyCom: MyCom
    }
  })
</script>
</html>
```

### 3、组件间传值

问题：你知道vue传值的方式有哪些？

如前面介绍组件时所说，组件有`分治`的特点，每个组件之间具有一定的独立性，但是在实际工作中使用组件的时候有互相之间传递数据的需求，此时就得考虑如何进行`组件间传值`的问题了。

课堂案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <child-com></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件</h3>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    template: '#child'
  }
  const ParentCom = {
    template: '#parent',
    components: {
      childCom // 对象内部 key 和value相同且value值是一个变量，可以采用简写形式 
    }
  }
  new Vue({
    el: '#app',
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
```



#### 3.1、父→子传值（常用）

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <!-- 
      父组件在调用子组件的地方，添加自定义属性
      属性的值就是父组件要传递给子组件的值
      如果属性的值是一个变量，boolean类型或者是number类型，需要使用绑定属性
     -->
    <child-com test="测试" :count="count" :num="100" :flag="true"></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件</h3>
    <p>{{test}}</p>
    <p>{{count}}</p>
    <p>{{num}}</p>
    <p>{{flag}}</p>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    // 在子组件定义的地方，添加一个props选项，用来接收父组件传递的数据
    // 数据接收的第一种方式就是数组方式，数组的元素就是自定义的属性名
    // 就可以在子组件中使用通过自定义的属性名显示数据
    props: ['test', 'count', 'num', 'flag'],
    template: '#child'
  }
  const ParentCom = {
    template: '#parent',
    data () {
      return {
        count: 100000
      }
    },
    components: {
      childCom // 对象内部 key 和value相同且value值是一个变量，可以采用简写形式 
    }
  }
  new Vue({
    el: '#app',
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <!-- 
      父组件在调用子组件的地方，添加自定义属性
      属性的值就是父组件要传递给子组件的值
      如果属性的值是一个变量，boolean类型或者是number类型，需要使用绑定属性
     -->
    <child-com test="测试" :count="count" :num="100" :flag="true"></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件</h3>
    <p>{{test}}</p>
    <p>{{count}}</p>
    <p>{{num}}</p>
    <p>{{flag}}</p>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    // 在子组件定义的地方，添加一个props选项，用来接收父组件传递的数据
    // 1.数据接收的第一种方式就是数组方式，数组的元素就是自定义的属性名
    // 就可以在子组件中使用通过自定义的属性名显示数据
    // 2.数据接收的第二种方式就是对象方式，
    // key值为自定义的属性名，value值为数据类型，用于校验用户传值是否合适
    // props: ['test', 'count', 'num', 'flag'],
    props: {
      test: String,
      count: Number,
      num: String, // 本身是Number，注意观察控制台的红色警告信息
      flag: Boolean
    },
    template: '#child'
  }
  const ParentCom = {
    template: '#parent',
    data () {
      return {
        count: 100000
      }
    },
    components: {
      childCom // 对象内部 key 和value相同且value值是一个变量，可以采用简写形式 
    }
  }
  new Vue({
    el: '#app',
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <!-- 
      父组件在调用子组件的地方，添加自定义属性
      属性的值就是父组件要传递给子组件的值
      如果属性的值是一个变量，boolean类型或者是number类型，需要使用绑定属性
     -->
     <child-com test="测试" :count="count" :num="100" :flag="true"></child-com>
     <hr />
     <!-- 使用组件的默认值 -->
     <child-com ></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件</h3>
    <p>{{test}}</p>
    <p>{{count}}</p>
    <p>{{num}}</p>
    <p>{{flag}}</p>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    // 在子组件定义的地方，添加一个props选项，用来接收父组件传递的数据
    // 1.数据接收的第一种方式就是数组方式，数组的元素就是自定义的属性名
    // 就可以在子组件中使用通过自定义的属性名显示数据
    // 2.数据接收的第二种方式就是对象方式，
    // key值为自定义的属性名，value值为数据类型，用于校验用户传值是否合适
    // 3.数据接收的第三种方式就是对象方式
    // 对象的key值为自定义的属性名，value值为对象
    // 对象中的type的key值表示数据类型，default代表默认值，如果默认值是对象或者数组，需要使用函数返回
    // 如果遇到某一个属性是必须传递的，添加required属性
    // props: ['test', 'count', 'num', 'flag'],
    // props: {
    //   test: String,
    //   count: Number,
    //   num: String, // 本身是Number，注意观察控制台的红色警告信息
    //   flag: Boolean
    // },
    props: {
      test: {
        type: String,
        default: '测试中....'
      },
      count: {
        type: Number,
        default: 1010110
      },
      num: {
        type: Number,
        default: 1,
        required: true // 必须传递 -- 注意观察控制台
      },
      flag: {
        type: Boolean,
        default: false
      },
      obj: {
        type: Object,
        // default: { a: 1 }// X
        default () { // 如果默认值是对象或者数组，需要使用函数返回
          return { a: 1 }
        }
      }
    },
    template: '#child'
  }
  const ParentCom = {
    template: '#parent',
    data () {
      return {
        count: 100000
      }
    },
    components: {
      childCom // 对象内部 key 和value相同且value值是一个变量，可以采用简写形式 
    }
  }
  new Vue({
    el: '#app',
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
```



#### 3.2、子→父传值

- 子组件模版内容中用`$emit()`定义`自定义事件`，`$emit()`方法**至少**有2个参数
  - 第一个参数为自定义的事件名称（不要和内置的事件重名，例如click、change等）abc
  - 第二个参数为需要传递的数据（可选，如果传可以是任何格式的数据）
- ...

- 父组件模板内容中的子组件占位标签上用v-on（或@）绑定子组件定义的自定义事件名，监听子组件的事件，实现通信 

**示例代码：每点击子组件按钮给父组件字体加9（由子决定，当然也可以写成其它的值）像素**

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <!-- 
      在调用子组件的地方，绑定一个自定义的事件
      自定义事件的默认参数就是子组件传递过来的值
     -->
    <child-com @myevent="getData"></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件</h3>
    <button @click="sendData">发送数据</button>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    template: '#child',
    data () {
      return {
        msg: '我是子组件'
      }
    },
    methods: {
      sendData () {
        // 在子组件的某一个事件内部，通过 this.$emit('自定义事件名', 参数)即可完成传值
        this.$emit('myevent', this.msg)
      },
      fn () {
        console.log(this.msg)
      }
    }
  }
  const ParentCom = {
    template: '#parent',
    methods: {
      getData (data) {
        console.log(data)
      }
    },
    components: {
      childCom // 对象内部 key 和value相同且value值是一个变量，可以采用简写形式 
    }
  }
  new Vue({
    el: '#app',
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
~~~



#### 3.3、EventBus

> EventBus又被称之为**中央事件总线**

在Vue中通过单独的`事件中心`来管理非`父子关系`组件（兄弟）间的通信：

![事件中心](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/297ffa8474e3e1ba1b392c422284a9889d9181f8.png?sign=b6a91e2548fd10fabc71f4adf538d61d&t=5f3a3491)

**核心步骤**

- 建立事件中心

  - ~~~javascript
    const eventBus = new Vue()
    ~~~

- 传递数据

  - ~~~javascript
    eventBus.$emit('自定义事件名',传递的数据)
    ~~~

- 接收数据

  - ~~~javascript
    eventBus.$on('自定义事件名'[,callback])
    ~~~

- 销毁事件中心

  - ~~~javascript
    eventBus.$off('自定义事件名')
    ~~~



~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <my-content></my-content>
    <my-footer></my-footer>
  </div>
</body>
<script src="lib/vue.js"></script>
<template id="content">
  <div>
    {{ text }}
  </div>
</template>
<template id="footer">
  <ul>
    <li @click="changePage('首页')">首页</li>
    <li @click="changePage('分类')">分类</li>
    <li @click="changePage('购物车')">购物车</li>
    <li @click="changePage('我的')">我的</li>
  </ul>
</template>
<script>
  // 中央事件总线
  // 实例化新的vue作为中央事件总线 bus
  // 在需要获取数据的地方，通过 bus.$on(自定义事件名, 回调函数) 接收数据，
  // 回调函数的默认参数就是传递的值
  // 在发送数据的地方，通过 bus.$emit(自定义事件名，传递的参数) 发送数据即可
  const eventBus = new Vue()
  const Content = {
    template: '#content',
    data () {
      return {
        text: '首页'
      }
    },
    mounted () {
      // 接收数据 ---- 监听
      eventBus.$on('footer-content', (data) => {
        this.text = data
      })
    }
  }
  const Footer = {
    template: '#footer',
    methods: {
      changePage (text) {
        // 发送数据
        eventBus.$emit('footer-content', text)
      }
    }
  }
  new Vue({
    el: '#app',
    components: {
      'my-content': Content,
      'my-footer': Footer
    }
  })
</script>
</html>
~~~



#### 3.4、ref（常用）

父去取子的数据信息。（方向：子-父，但是区别于之前的子传父，之前是主动，现在是被动）

`ref`属性被用来给元素或子组件注册引用信息，引用信息将会注册在父组件的 `$refs` 对象上。如果在普通的 DOM 元素上使用`ref`属性，则引用指向的就是 DOM 元素；如果`ref`属性用在子组件上，引用就指向子组件**实例**。

- `ref`放在标签上，拿到的是原生节点。`ref`放在组件上 拿到的是组件实例
- 原理：在父组件中通过`ref`属性（会被注册到父组件的`$refs`对象上）拿到组件/DOM对象，从而得到组件/DOM中的**所有的信息**，也包括值

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <!-- 
      父组件调用子组件的地方，添加ref属性，属性的值随便定义
     -->
    <child-com ref = "child"></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件</h3>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    template: '#child',
    data () {
      return {
        a: 100
      }
    },
    methods: {
      fn () {
        console.log('aaaa')
      }
    }
  }
  const ParentCom = {
    template: '#parent',
    components: {
      childCom // 对象内部 key 和value相同且value值是一个变量，可以采用简写形式 
    },
    mounted() {
      // 在父组件的任意的地方，可以通过 this.$refs.自定义的ref属性的值 获取到子组件实例
      console.log(this.$refs.child)
      console.log(this.$refs.child.a)
      this.$refs.child.fn()
    },
  }
  new Vue({
    el: '#app',
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
~~~

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <div id="box">box</div>
    <!-- ref放到标签上表示可以使用DOM操作 -->
    <div ref="content">content</div>
  </div>
</body>

<script>
  new Vue({
    el: '#app',
    mounted() {
      document.getElementById('box').style.color = "red"
      this.$refs.content.style.color = "green"
    },
  })
</script>
</html>
```



> 注意：
>
> 
>
> `ref`属性这种获取子元素/组件的方式虽然写法简单，容易上手，但是其由于权限过于开放，不推荐使用，有安全问题。（不仅可以获取值，还可以获取其他所有的元素/组件的数据，甚至可以修改这些数据。）

#### 3.5 Parent

子组件可以直接通过 this.$parent 获取到父组件实例的属性和方法

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <child-com ></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件</h3>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    template: '#child',
    mounted() {
      console.log(this.$parent.a)
      this.$parent.fn()
    },
  }
  const ParentCom = {
    template: '#parent',
    components: {
      childCom 
    },
    data () {
      return {
        a: 100
      }
    },
    methods: {
      fn () {
        console.log('aaaa')
      }
    }
  }
  new Vue({
    el: '#app',
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
```

#### 3.6 Provide / inject

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="lib/vue.js"></script>
</head>
<body>
  <div id="app">
    <parent-com></parent-com>
  </div>
</body>
<template id="parent">
  <div>
    <h1>父组件</h1>
    <child-com></child-com>
  </div>
</template>
<template id="child">
  <div>
    <h3>子组件 - {{ msg }}</h3>
  </div>
</template>
<script>
  // 谁用谁注册
  const childCom = {
    template: '#child',
    inject: ['msg']
  }
  const ParentCom = {
    template: '#parent',
    components: {
      childCom // 对象内部 key 和value相同且value值是一个变量，可以采用简写形式 
    }
  }
  new Vue({
    el: '#app',
    provide: {
      msg: 'abcd'
    },
    components: {
      ParentCom: ParentCom
    }
  })
</script>
</html>
```



### 4、动态组件

通过使用保留的 `<component> `元素，动态地绑定到它的` is` 特性，==我们让多个组件可以使用同一个挂载点（位置），并动态切换。==

**示例代码**

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <!-- <component is="user-com"></component> -->
    <component :is="type"></component>
    <ul>
      <li @click="type='home-com'">首页</li>
      <li @click="type='kind-com'">分类</li>
      <li @click="type='cart-com'">购物车</li>
      <li @click="type='user-com'">我的</li>
    </ul>
  </div>
</body>
<template id="home">
  <div>首页</div>
</template>
<template id="kind">
  <div>分类</div>
</template>
<template id="cart">
  <div>购物车</div>
</template>
<template id="user">
  <div>我的</div>
</template>
<script src="lib/vue.js"></script>
<script>
  
  new Vue({
    el: '#app',
    data: {
      type: 'home-com'
    },
    components: {
      'home-com': {
        template: '#home'
      },
      'kind-com': {
        template: '#kind'
      },
      'cart-com': {
        template: '#cart'
      },
      'user-com': {
        template: '#user'
      }
    }
  })
</script>
</html>
~~~

默认情况下，动态组件切换时，实际上是触发了组件的销毁和重建钩子

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <!-- <component is="user-com"></component> -->
    <component :is="type"></component>
    <ul>
      <li @click="type='home-com'">首页</li>
      <li @click="type='kind-com'">分类</li>
      <li @click="type='cart-com'">购物车</li>
      <li @click="type='user-com'">我的</li>
    </ul>
  </div>
</body>
<template id="home">
  <div>首页
    <input type="text" placeholder="home"/>
  </div>
</template>
<template id="kind">
  <div>分类
    <input type="text" placeholder="kind"/>
  </div>
</template>
<template id="cart">
  <div>购物车
    <input type="text" placeholder="cart"/>
  </div>
</template>
<template id="user">
  <div>我的
    <input type="text" placeholder="user"/>
  </div>
</template>
<script src="lib/vue.js"></script>
<script>
  
  new Vue({
    el: '#app',
    data: {
      type: 'home-com'
    },
    components: {
      'home-com': {
        template: '#home'
      },
      'kind-com': {
        template: '#kind'
      },
      'cart-com': {
        template: '#cart'
      },
      'user-com': {
        template: '#user'
      }
    }
  })
</script>
</html>
```



> **keep-alive**的作用：
>
> `keep-alive`可以将已经切换出去的非活跃组件保留在内存中。如果把切换出去的组件保留在内存中，可以保留它的状态，避免重新渲染。生成两个声明周期钩子 activated deactivated（显示，隐藏）

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <!-- <component is="user-com"></component> -->
    <keep-alive>
      <component :is="type"></component>
    </keep-alive>
    <ul>
      <li @click="type='home-com'">首页</li>
      <li @click="type='kind-com'">分类</li>
      <li @click="type='cart-com'">购物车</li>
      <li @click="type='user-com'">我的</li>
    </ul>
  </div>
</body>
<template id="home">
  <div>首页
    <input type="text" placeholder="home"/>
  </div>
</template>
<template id="kind">
  <div>分类
    <input type="text" placeholder="kind"/>
  </div>
</template>
<template id="cart">
  <div>购物车
    <input type="text" placeholder="cart"/>
  </div>
</template>
<template id="user">
  <div>我的
    <input type="text" placeholder="user"/>
  </div>
</template>
<script src="lib/vue.js"></script>
<script>
  
  new Vue({
    el: '#app',
    data: {
      type: 'home-com'
    },
    components: {
      'home-com': {
        template: '#home',
        activated() {
          console.log('home activated')
        },
        deactivated() {
          console.log('home deactivated')
        },
      },
      'kind-com': {
        template: '#kind',
        activated() {
          console.log('kind activated')
        },
        deactivated() {
          console.log('kind deactivated')
        },
      },
      'cart-com': {
        template: '#cart',
        activated() {
          console.log('cart activated')
        },
        deactivated() {
          console.log('cart deactivated')
        },
      },
      'user-com': {
        template: '#user',
        activated() {
          console.log('user activated')
        },
        deactivated() {
          console.log('user deactivated')
        },
      }
    }
  })
</script>
</html>
```

> 万一不是所有的组件都需要保留状态呢,定义组件时添加name属性，给keep-alive 添加include属性

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <!-- <component is="user-com"></component> -->
    <!-- 如果写的是组件的name属性，字符串中间不要空格 -->
    <!-- <keep-alive include="home,kind,cart"> -->
      <!-- 数组形式 -->
    <keep-alive :include="['home', 'kind', 'cart']">
      <component :is="type"></component>
    </keep-alive>
    <ul>
      <li @click="type='home-com'">首页</li>
      <li @click="type='kind-com'">分类</li>
      <li @click="type='cart-com'">购物车</li>
      <li @click="type='user-com'">我的</li>
    </ul>
  </div>
</body>
<template id="home">
  <div>首页
    <input type="text" placeholder="home"/>
  </div>
</template>
<template id="kind">
  <div>分类
    <input type="text" placeholder="kind"/>
  </div>
</template>
<template id="cart">
  <div>购物车
    <input type="text" placeholder="cart"/>
  </div>
</template>
<template id="user">
  <div>我的
    <input type="text" placeholder="user"/>
  </div>
</template>
<script src="lib/vue.js"></script>
<script>
  
  new Vue({
    el: '#app',
    data: {
      type: 'home-com'
    },
    components: {
      'home-com': {
        name: 'home',
        template: '#home',
        activated() {
          console.log('home activated')
        },
        deactivated() {
          console.log('home deactivated')
        },
      },
      'kind-com': {
        name: 'kind',
        template: '#kind',
        activated() {
          console.log('kind activated')
        },
        deactivated() {
          console.log('kind deactivated')
        },
      },
      'cart-com': {
        name: 'cart',
        template: '#cart',
        activated() {
          console.log('cart activated')
        },
        deactivated() {
          console.log('cart deactivated')
        },
      },
      'user-com': {
        name: 'user',
        template: '#user',
        activated() {
          console.log('user activated')
        },
        deactivated() {
          console.log('user deactivated')
        },
      }
    }
  })
</script>
</html>
~~~

> 在动态组件中存在2个生命周期函数（需要配合keep-alive标签）：
>
> ​              activated：激活缓存组件的时候被触发
>
> ​              deactivated：离开缓存组件的时候被触发
>
> ​            当使用了keepalive组件后，组件在切换的时候就不会被销毁，而是被缓存起来了。【此处需要注意生命周期相关的执行情况】
>
> 



### 5、组件插槽

组件内部的代码显示还是不显示，在哪里显示，如何显示，这就是内容分发所干的活

插槽也是组件传值的一种方式。

组件的最大特性就是`重用`，而用好插槽能大大提高组件的可重用能力。

![小霸王](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/ccc81e4e187bb6ac614d3d69724cb4c5342fed73.jpeg?sign=b0c53aaaa69c1bdfe25e76e303c54362&t=5f5b5665)

**插槽的作用：**父组件向子组件传递内容。

![父组件向子组件传递内容](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/c5ddf742613c5886ff140e5d381f9ff76a803d8b.jpeg?sign=59bc2dccbbaf747f12c649b7c17d9415&t=5f3a3981)

通俗的来讲，**插槽无非就是在`子组件`中挖个坑，坑里面放什么东西由`父组件`决定。**（父-子）

插槽类型有：

- 单个（匿名）插槽
- 具名插槽
- 作用域插槽

#### 5.1、匿名插槽（常用）

> 匿名插槽一般就是使用单个插槽

**示例代码**

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <my-com>
      您好呀
    </my-com>
  </div>
</body>
<script src="lib/vue.js"></script>
<template id="com">
  <div>
    <slot></slot>
    <h1>插槽</h1>
    <slot></slot>
  </div>
</template>
<script>
  const Com = {
    template: '#com'
  }
  new Vue({
    el: '#app',
    components: {
      'my-com': Com
    }
  })
</script>
</html>
~~~

> 注意：子组件的`slot`标签中允许书写内容，当父组件不往子组件传递内容时，`slot`中的内容才会被展示出来。



#### 5.2、具名插槽

`slot` 元素可以用一个特殊的特性 `name` 来进一步配置如何分发内容。多个插槽可以有不同的名字，具名插槽将匹配内容片段中有对应 `slot` 特性的元素。

**`上中下`形式网页布局示例代码**

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <my-com>
      <header slot="header">头部</header>
      <footer slot="footer">底部</footer>
    </my-com>
  </div>
</body>
<script src="lib/vue.js"></script>
<template id="com">
  <div>
    <slot name="header"></slot>
    <h1>插槽</h1>
    <slot name="footer"></slot>
  </div>
</template>
<script>
  const Com = {
    template: '#com'
  }
  new Vue({
    el: '#app',
    components: {
      'my-com': Com
    }
  })
</script>
</html>
~~~

> 具名插槽存在的意义就是为了解决在单个页面中同时使用多个插槽。



#### 5.3、作用域插槽

**应用场景：**父组件对子组件的内容进行加工处理

作用域插槽是一种**特殊类型**的插槽，**作用域插槽会绑定了一套数据，父组件可以拿这些数据来用**，于是，情况就变成了这样：样式父组件说了算，但父组件中内容可以显示子组件插槽绑定的数据。



**示例代码**

~~~html
<body>
    <div id="app">
        <child>
            <div slot-scope="props">
                <div>父组件</div>
                <h3>{{ props.text }}</h3>
            </div>
        </child>
    </div>
</body>

<script src="./js/vue.js"></script>
<script type="text/javascript">
    Vue.component('child', {
        template: `
            <div>
            	<slot text="我是子组件中的内容"></slot>
            </div>
			`
    })
    const vm = new Vue({
        el: '#app'
    })
</script>
~~~

#### 5.4 v-slot

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <my-com>
      <!-- 使用 v-slot 时，只能使用template标签 -->
      <!-- 可以在一个 <template> 元素上使用 v-slot 指令，并以 v-slot 的参数的形式提供其名称： -->
      <template v-slot:header>头部</template>
      <template v-slot:footer>底部</template>
    </my-com>
  </div>
</body>
<script src="lib/vue.js"></script>
<template id="com">
  <div>
    <slot name="header"></slot>
    <h1>插槽</h1>
    <slot name="footer"></slot>
  </div>
</template>
<script>
  const Com = {
    template: '#com'
  }
  new Vue({
    el: '#app',
    components: {
      'my-com': Com
    }
  })
</script>
</html>
```



## 七、Vue-cli（工程化）

vue command line tool，简单的来讲，就是一个基于命令行的vue开发工具。

**Vue-CLI ≠ Vue**，Vue-CLI就是一个Vue工具。

vue脚手架工具

### 1、单文件组件

在很多 Vue 项目中，我们使用 Vue.component 来定义全局组件，紧接着用 new Vue({ el: '#container '}) 在每个页面内指定一个容器元素。这种方式在很多中小规模的项目中运作的很好，在这些项目里 JS 只被用来加强特定的视图。但当在更复杂的项目中，或者你的前端完全由JS驱动的时候，下面这些缺点将变得非常明显：

- 所有的组件都放同一个html文件中
- 没有构建步骤(build操作)，不能使用npm来管理项目
- 缺乏语法高亮和提示
- 没有针对单个组件的css样式支持

针对于上述的问题，vue框架发布了`vue-cli`项目`生成`工具，Vue-cli是一个基于 Vue.js 进行快速开发的完整系统， 致力于将 Vue 生态中的工具基础标准化。它确保了各种构建工具能够基于智能的默认配置即可平稳衔接，这样你可以专注在撰写应用上，而不必花好几天去纠结配置的问题。

![单文件组件](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/d661ee6ee425b328096a2f472257dcade94cf1e7.png?sign=e157b5d6bdfaa11a2acfe6ffd06cf724&t=5f5e0742)

单文件组件的要求：

- 后缀必须是“.vue”
- 需要使用三个标签将整个文件分成3部分
  - template标签：包裹的是html部分（视图部分）【必须要有的】
  - script标签：包裹的是JavaScript部分（逻辑部分）【必须要有的】
    - css-in-js：在JavaScript中写样式
  - style标签：包裹的css/scss/less等样式部分（样式部分）【可以没有】
    - 样式存在范围的问题的
      - 有“scoped”属性则表示该组件的样式代码只在当前组件生效
      - 如果没有“scoped”属性则表示该组件的样式会影响自己及后代，一般在工程化开发的模式中，只有根组件“App.vue”不写“scoped”属性（全局样式）
- 其他的语法与之前的一致



### 2、工具安装

网址：http://npmjs.com

~~~shell
## 安装
# -g：全局安装
npm i -g @vue/cli #不推荐

#如果想要使用国内的淘宝镜像http://npm.taobao.org/，可以运行命令：
npm install -g cnpm --registry=https://registry.npm.taobao.org

cnpm i -g @vue/cli

# 安装yarn
cnpm i yarn -g
yarn global add @vue/cli

## 安装成功后，检查
vue --version
vue -V
#  Vue和VueCLI是两回事

## 卸载（了解）
npm uninstall -g @vue/cli
~~~

![版本检查](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/0a637b8f10a340665538af6f079480dabf686f21.png?sign=d4b0bcdfcda0c91a18b1212f24892c5d&t=5f63af2f)

> 如果需要安装其他版本，可以使用`npm install -g @vue/cli@版本号`的方式进行指定版本。

如果最新版安装不成功，可以尝试以下几种方式去解决：

- 断网，使用热点共享流量去执行安装命令
- 安装其他版本
- 切换一下npm镜像源，切换成taobao
- 卸载nodejs重安装
- 重装系统/换电脑



### 3、创建项目

~~~shell
# 首先需要进入到对应的目录中(英文目录不要有空格及中文),执行如下命令
# 如果当前你的终端工作路径带有中文或者空格，你可以使用`cd 路径`形式进行路径切换，切换到符合要求的路径中
vue create 项目名称(创建时会自己以对应的项目名称生成目录)
## 例
vue create vue-test
# 上述命令中，可以允许变的就是`myproject`部分
~~~

**以下步骤以`Vue CLI v4.5.6`为例，仅供参考，在实际使用时，请以自身需求为准进行配置**

- 预设选择

![预设选择](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/3306e33dc3e5d81070a8dc78b02d897565e97ad7.png?sign=c5f7873bfe1db941667c2c8f4c1660bf&t=5f6725b8)

- 选择预设功能（**根据自身项目需要选择**）

  >
  >
  >? Please pick a preset: Manually select features
  >? Check the features needed for your project: 
  > ◉ Choose Vue version
  > ◉ Babel
  > ◯ TypeScript
  > ◉ Progressive Web App (PWA) Support
  > ◉ Router
  > ◉ Vuex
  >❯◉ CSS Pre-processors
  > ◉ Linter / Formatter
  > ◯ Unit Testing
  > ◯ E2E Testing

![预设功能选择](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/983429d74ae8a2b0bcbe6989c9ba9222a7ef6c2a.png?sign=cc4159e20f273686b40ac1c0caac9d05&t=5f672644)

- 选择Vue版本

![vue版本选择](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/675e2b02b44d13452ad50edff22290e7940cd982.png?sign=59a0c6ddfea13fde357d1f384296978e&t=5f67266e)

- 选择路由模式

  > Use history mode for router?  y

- 选择css预处理器

- >
  >
  >? Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by default): 
  >  Sass/SCSS (with dart-sass) 
  >  Sass/SCSS (with node-sass) 
  >  Less 
  >❯ Stylus 

- 选择`ESlint`配置（如果启用）

![eslint](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/82a888c3ce2ab58c6f0af95423d671b7def7c823.png?sign=1f6540c77f791528813ac36e2de731c3&t=5f6726bb)

- 选择额外的`eslint`功能

![额外lint选配](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/43ca4b950cee6c4b437521ce5eda7d7435c2488a.png?sign=fe94111f1dd389c051af27ede9dd231f&t=5f67278e)

- 是否独立配置

![是否独立配置](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/c73968823c3540002ba7365381f9a2d075c15ac4.png?sign=2baba46888f7a176c6d27f3441522b1a&t=5f6727b1)

- 是否保存本次操作预设

![保存预设](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/4f8734a2d5581a1616b4ebfe1117b6b2fa322618.png?sign=beda5914c014f84d5a02b61f89c49ca8&t=5f6727eb)

- 项目创建成功

![创建成功](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/74b3f1f5a30596606c16b93fc24ab018e6e98487.png?sign=531f60f30c89e95c6718fad45ee248d0&t=5f6728ae)



### 4、目录结构介绍

- public：不需要去改动现有的文件，里面存放的是浏览器访问的入口文件（index.html）

- src（**后期很多操作都在这个目录中完成**）
  - main.js：项目/程序入口文件 （该文件中JavaScript代码都会被执行）
  - App.vue：根组件（万物之根）
  - components：存放自定义的`功能`组件（涉及到业务逻辑）
  - assets：静态资源目录（图片、视频、音频等就是静态资源），这里面的静态资源浏览器是无法直接访问的，而是给组件通过模块化的方式导入进组件使用的。
    - 项目中的静态资源有2个地方可以放
      - public：供在public/index.html中直接引入（link标签、script标签）的
      - src/assets：供单文件组件导入时需要的静态资源文件（import ...）
  - **views：（当前是没有的，但是后期要用）存放`视图`组件的**（只是涉及到页面的布局排版）
  - Router: 路由
  - Store: 状态管理器

如何很好的划分功能组件与视图组件呢？

小技巧：可以被复用的就算它功能组件，不能被复用的就算它是视图组件。





### 5、项目的运行及注意事项

#### 5.1、项目的启停

![创建成功](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/74b3f1f5a30596606c16b93fc24ab018e6e98487.png?sign=531f60f30c89e95c6718fad45ee248d0&t=5f6728ae)

如上图所示，在创建项目完成后有提示我们后续的操作：

- 在命令行中进入项目目录
- 运行`npm run serve`命令来启动项目

按照上述命令执行后，我们会见到如下的效果，即表示项目运行成功：

![项目启动成功](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/1335f9133e19d0a1d6b2f629bc8b7bde9a0868d8.png?sign=5b56d2e029b8969783fd1c82dc299261&t=5f683757)

>  注意：默认端口号会从8080开始，如果再次启动其他项目后续会以8081、8082……进行监听。

如果需要停止正在运行的项目，可以选择以下两种方式任一：

- 关闭终端
- 在终端中按下组合键`Ctrl + C`（Cancel），随后选择`Y`并键入`回车`（如下图）
- 也可以按下两次`Ctrl + C`

![关闭项目运行](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/987aba14adc55be552add382c8c565d82dbf5b90.png?sign=ffaad83e946c9b1205a489388dc64adc&t=5f68396c)

> 部分同学的机器在启动vue项目的时候可能会出现卡在“40%”的进度并且长时间不动，如果这样，则直接`Ctrl + C`停止本次启动，重新再去尝试启动。

==关于项目运行时，如果修改了项目代码是否需要重启的说明：==

是否需要重启取决于我们修改了什么内容，如果只是修改了代码部分（js、css、vue文件等）是不需要开发者手动重启项目的，系统会自动重新编译（有点nodemon感觉）；但是如果修改的是配置文件，则必须需要自己先去停止项目，然后再去启动项目（手动实现重启）。



#### 5.2、关于ESlint

ESlint用于规范项目的编码，大型项目一般多人开发，为了避免一些个人编程恶习`坑自己坑别人`，项目中使用了ESlint会起到`紧箍咒`的作用，强制开发人员注意代码规范。例如，在不使用ESlint的情况下，JS允许我们声明一个不变量但不使用。如果使用了ESlint，在上述情况下会报错如下：

![eslint报错演示](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/b83ccf704842a3a495c99aba44baa772ede48a7b.png?sign=787cecc32474ee8d85b6b6a6ffd1116c&t=5f6838c1)



关于ESlint的报错，有一份错误参照，可以访问以下地址查看：https://cn.eslint.org/docs/rules/

必须使用eslint锻炼自己的代码规范



## 八、路由（重点）

### 1、路由的概念（了解）

路由的本质就是一种`对应关系`（此处的路由含义同之前nodejs的路由），根据不同的URL请求，返回对应不同的资源。那么url地址和真实的资源之间就有一种对应的关系，就是路由。

路由分为：`后端路由`和`前端路由`

- 后端路由：由服务器端进行实现并实现资源映射分发（nodejs、jsp、php等）
  - 概念：根据不同的用户URL请求，返回不同的内容（**地址与资源**产生对应关系）
  - 本质：URL请求地址与服务器资源之间的对应关系（映射）

![后端路由](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/a832ee01e808edae5e035257d6d9b65411ca0142.jpeg?sign=2a588882a568365ae19f525571bce452&t=5f3e3ebf)

- 前端路由：根据不同的**事件**来显示不同的页面内容，是事件与事件处理函数之间的对应关系
  - 概念：根据不同的用户事件，显示不同的页面内容（**地址与事件**产生对应关系）
  - 本质：用户事件与事件处理函数之间的对应关系

![前端路由](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/2bddc42178c6449942b3dfe53187a890a20f4c9f.png?sign=c895f41a55db1f871fee8c98db306c8e&t=5f3e41f2)





### 2、前端路由实现

核心思想：通过监听地址栏的变化事件来实现资源的动态显示

前端路由有2种模式：

- hash模式

>  hash路由模式是这样的：http://xxx.abc.com/#/xx。 有带#号，后面就是hash值的变化。改变后面的hash值，它不会向服务器发出请求，因此也就不会刷新页面。并且每次hash值发生改变的时候，会触发hashchange事件。因此我们可以通过监听该事件，来知道hash值发生了哪些变化。

~~~javascript
window.addEventListener('hashchange', ()=>{
  // 通过 location.hash 获取到最新的 hash 值
  console.log(location.hash);
});
~~~

- history模式

> 形如：http://xxx.abc.com/xx/yy/zz。HTML5的History API为浏览器的全局history对象增加了该扩展方法。它是一个浏览器（bom）的一个接口，在window对象中提供了onpopstate事件来监听历史栈的改变，只要历史栈有信息发生改变的话，就会触发该事件。

~~~javascript
history.pushState({},title,url); // 向历史记录中追加一条记录
history.replaceState({},title,url); // 替换当前页在历史记录中的信息。
window.addEventListener('popstate', function(event) {
	console.log(event)
})
~~~

>注：浏览器地址没有#， 比如(http://localhost:3001/a); 它也一样不会刷新页面的。但是url地址会改变。**但它在服务器没有配置的情况下，不能手动刷新，否则返回404页面**

**hash**路由体验

~~~html
<body>
    <a href="#/a">去a页面</a><hr>
    <a href="#/b">去b页面</a><hr>
    <a href="#/c">去c页面</a><hr>
    <a href="#/d">去d页面</a><hr>

    <div id="route-view"></div>
</body>

<script type="text/javascript">
    // 获取元内容素
    var ctn = document.getElementById('route-view')

    // 默认渲染
    render('/a')

    // 监听hashchange事件
    window.addEventListener('hashchange',function(){
        render(location.hash.slice(1))
    })

    // 分支
    function render(router){
        switch (router) {
            case '/a':
                ctn.innerHTML = '这是a页面'
                break;
            case '/b':
                ctn.innerHTML = '这是b页面'
                break;
            case '/c':
                ctn.innerHTML = '这是c页面'
                break;
            case '/d':
                ctn.innerHTML = '这是d页面'
                break;
            default:
                ctn.innerHTML = '404页面'
                break;
        }
    }
</script>
~~~



### 3、Vue Router（重点）

网址：https://router.vuejs.org/zh/，vuerouter是vue全家桶之一。

#### 3.1、介绍

**Vue Router 是 Vue.js 官方的路由管理器**。它和 Vue.js 的核心深度集成，让构建单页面应用变得易如反掌。包含的功能有：

- 嵌套的路由

- **模块化**的、基于组件的路由配置

- 路由参数、查询、通配符

- 带有自动激活（默认选中效果）的 CSS class 的链接

- HTML5 历史模式或 hash 模式




#### 3.2、安装

如果在vue-cli创建项目时没有勾选上`vue-router`选项，此时就需要手动的来安装它（**切记，要进入项目中再去运行这个指令**）：

~~~shell
npm i -S vue-router
~~~

查看是否安装成功，查看此文件`/package.json`

![vue-router安装成功检查](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/da67726d850713a81b814a877c862431a1740a5c.png?sign=f20b3897f66ca81281c00986e18faee3&t=5f67297b)



#### 3.3、Vue Router基本使用

Vue Router的基本使用步骤：

- 在src/创建路由文件的归档目录“router”

- 引入相关库文件
- VueRouter引入到Vue类中
- **定义路由组件规则**
- 创建路由实例
- 把路由挂载到Vue根实例中
- **添加路由组件渲染容器（router-view，组件）到对应组件中（占坑）**

~~~javascript
// 引入相关库文件
import Vue from 'vue'
import VueRouter from 'vue-router'

// VueRouter引入到Vue类中
Vue.use(VueRouter)

// 组件的引入
import Foo from './views/Foo'
import Bar from './views/Bar'

// 定义路由规则
const routes = [
  { path: '/foo', component: Foo },
  { path: '/bar', component: Bar }
]

// 创建路由实例
const router = new VueRouter({
  routes
  // routes: anyname
  // 传递规则的时候，传递的规则的属性名必须是`routes`
})

// 暴露router让外界使用（默认导出，一个模块只能默认导出1次）
export default router
// =====================================
// 挂载根实例（main.js）
// 记得要通过 router 配置参数注入路由，
// 从而让整个应用都有路由功能
const app = new Vue({
  router
}).$mount('#app')

<!-- html，添加路由组件渲染容器 -->
<div id="app">
	<router-view></router-view>
</div>
~~~

> - 后期在项目中以`index`命名的文件在引入时，可以省去文件名不写。
> - 在`import`的时候如果涉及到了路径，建议写`@`符号开头的路径（`@表示src目录`，这个操作是打包工具已经帮我们定义好了，vue-cli的功劳，后续webpack再去说明）
> - 名称的规范：
>   - 在`创建路由实例`的时候要去其属性名必须是`routes`
>   - 在`挂载路由实例到根实例`的时候要求属性名必须是`router`
>   - 请注意大小写

**示例代码：**

![](img/1.png)

```js
// router/index.js
import Vue from 'vue'
import VueRouter from 'vue-router'
// import Home from '../views/Home.vue'
// 什么时候使用路由的懒加载
import Home from '@/views/home/index.vue'
import Kind from '@/views/kind/index.vue'
// use
Vue.use(VueRouter)

const routes = [
  {
    path: '/home', // 路径
    name: 'home', // 命名路由
    component: Home
  },
  {
    path: '/kind',
    name: 'kind',
    component: Kind
  },
  {
    path: '/cart',
    name: 'cart',
    component: () => import('@/views/cart/index.vue')
  },
  {
    path: '/user',
    name: 'user',
    component: () => import('@/views/user/index.vue')
  }
]
console.log(process.env.BASE_URL)
const router = new VueRouter({
  mode: 'hash', // hash
  base: process.env.BASE_URL,
  routes
})

export default router

```

```vue
<!-- App.vue
告诉路由对应显示视图的位置 <router-view/>
导航的跳转 改变路由 路由映射视图
-->
<template>
  <div id="app">
    <router-view/>
    <footer>
      <ul>
        <router-link to="/home" tag="li">首页</router-link>
        <router-link to="/kind" tag="li">分类</router-link>
        <router-link to="/cart" tag="li">购物车</router-link>
        <router-link to="/user" tag="li">我的</router-link>
      </ul>
    </footer>
    <!--
      声明式跳转 标签 a href
      编程式跳转 js  window.location.href = ""

      vue
        声明式 router-link tag(router-link默认为a标签，tag可以声明要渲染为什么标签)
        编程式 this.$router.push() / replace() /back() / go(-1)

      选中的元素会自带选中的class样式 router-link-active
     -->
  </div>
</template>

<style lang="stylus">
.router-link-active
  color #f66
#app
  font-family Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>

```



#### 3.4、路由模式切换

vue-router中默认使用的是hash模式的路由，也就是前面介绍的地址栏中URL带有“#”的形式，如果需要切换成history模式，则可以在创建路由实例时进行指定，指定的配置项为`mode`，可选值：

- hash：**默认**，设置路由模式为hash路由
- history：设置路由模式为history路由

例如，如果我们想设置路由模式从`hash`改变为`history`则可以配置路由入口文件为：

```
const router = new VueRouter({
  mode: 'history', // hash
  base: process.env.BASE_URL,
  routes
})
```





#### 3.5、导航方式

含义：从一个组件/地址去往另一个组件/地址的方式。

在页面中，导航实现有2种方式：

- 声明式导航：通过点击链接实现的导航方式，例如HTML中的“<a>”标签，Vue中的“<router-link>”所实现的。
- 编程式导航：通过调用JavaScript形式API实现的导航方式，例如location.href实现的跳转效果

##### 3.5.1、声明式导航

它就是先在页面中定义好跳转的路由规则，vueRouter中通过 router-link组件来完成

```html
 <ul>
<router-link to="/home" tag="li">首页</router-link>
<router-link to="/kind" tag="li">分类</router-link>
<router-link to="/cart" tag="li">购物车</router-link>
<router-link to="/user" tag="li">我的</router-link>
</ul> 
    
```



~~~html
 <ul>
   <router-link to="/home" tag="li">首页</router-link>
   <!-- <router-link to="/kind" tag="li">分类</router-link> -->
   <router-link :to="{ path: '/kind' }" tag="li">分类</router-link>
   <router-link :to="{ path: '/cart', query: { id: 100 } }" tag="li">购物车</router-link>
   <router-link to="/user?id=1000" tag="li">我的</router-link>
</ul>
<!-- 
	to 要跳转到的路由规则  string|object
	to="users"
	:to="{path:'path'}"

	tag="tagName"		去指定声明式导航产生的链接所使用的标签，默认是a标签
-->
~~~



##### 3.5.2、编程式导航

简单来说，编程式导航就是通过`JavaScript`来实现路由跳转

```
  <!-- 编程式 -->
      <ul>
        <li @click="$router.push('/home')">首页</li>
        <li @click="$router.push('/kind')">分类</li>
        <li @click="$router.push('/cart')">购物车</li>
        <li @click="$router.push('/user')">我的</li>
      </ul>
```



~~~javascript
this.$router.push("/login");
this.$router.push({ path:"/login" });
this.$router.push({ path:"/login",query:{username:"jack"} });
// 不要将path属性与params属性一起使用，这样会导致params路由参数获取不到
// name属性可以与params属性传参一起使用
this.$router.push({ name:'user' , params: {id:123} });
this.$router.go( n );//n为数字  负数为回退
this.$router.back(); // 返回上一页
~~~

**注意点：**编程式导航在跳转到与当前地址一致的URL时会报错，但这个报错不影响功能：

![重复导航错误](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/09/ffae8bf7ff5e46907768198ed81ce996be3ee11f.png?sign=fdd95d31c85eedc806e8e5b0817fc555&t=5f68a439)

如果患有强迫症，可以在路由入口文件`index.js`中添加如下代码解决该问题：

~~~javascript
// 该段代码不需要记，理解即可
const originalPush = VueRouter.prototype.push
VueRouter.prototype.push = function push (location) {
  return originalPush.call(this, location).catch((err) => err)
}
Vue.use(VueRouter)
~~~

**面试题问题：`this.$router`与`this.$route`有什么区别？***

答：`$router`是用于做编程式导航的（改变路由的）；`$route`是用户获取路由信息的。



#### 3.6、路由重定向

- 概念：用户在访问地址 A 的时候，强制用户跳转到地址 C ，从而展示特定的组件页面
- 实现： 通过路由规则的` redirect `属性，指定一个新的路由地址，可以很方便地设置路由的重定向

**代码示例**

~~~js
const routes = [
  { // 路由的匹配是从上到下，匹配到就停止
    path: '/',
    redirect: '/home'
  },
  {
    path: '/home', // 路径
    name: 'home', // 命名路由
    component: Home
  },
  {
    path: '/kind',
    name: 'kind',
    component: Kind
  },
  {
    path: '/cart',
    name: 'cart',
    component: () => import('@/views/cart/index.vue')
  },
  {
    path: '/user',
    name: 'user',
    component: () => import('@/views/user/index.vue')
  }
]
~~~

> component属性是可选属性，因此在写的时候需要注意，写错了也不会报错的。



#### 3.7、嵌套路由（重点）

路由前缀： **/admin/user**/add    **/admin/user**/del   **/admin/user**/mod

相同部分可以**提取**出来，减少重复劳动。

————————————以上为nodejs中的概念————————————————

上述概念在vue中被称之为叫做嵌套路由。

套娃，可以按照之前的nodejs处的路由前缀去理解。（当有些路由有公共部分的前缀时，在vue中就可以使用嵌套路由）

嵌套路由最关键在于理解子级路由的概念：

比如我们有一个`/users`的路由，那么`/users`下面还可以添加子级路由，如:`/users/index`、`/users/add`等等，这样的路由情形称之为嵌套路由。

>  核心思想：在**父路由组件**的模板内容中添加子路由链接和子路由**填充位（占坑）**，同时在路由规则处为父路由配置**children属性**指定子路由规则：

```html
<!--views/user/logined.vue-->
<template>
  <div>欢迎您*****</div>
</template>

<!--views/user/nologin.vue-->
<template>
  <div>登录之后查看</div>
</template>

```

~~~javascript
const routes = [
  { // 路由的匹配是从上到下，匹配到就停止
    path: '/',
    redirect: '/home'
  },
  {
    path: '/home', // 路径
    name: 'home', // 命名路由
    component: Home
  },
  {
    path: '/kind',
    name: 'kind',
    component: Kind
  },
  {
    path: '/cart',
    name: 'cart',
    component: () => import('@/views/cart/index.vue')
  },
  {
    path: '/user',
    name: 'user',
    // 如果有嵌套路由，那么一定在这个页面有 <router-view></router-view>
    component: () => import('@/views/user/index.vue'),
    children: [ // 浏览器输入 /user/nologin   以及/user/logined 查看效果
      {
        path: 'nologin', // 嵌套路由不要加 /
        name: 'nologin',
        component: () => import('@/views/user/nologin.vue')
      },
      {
        path: 'logined',
        name: 'logined',
        component: () => import('@/views/user/logined.vue')
      }
    ]
  }
]
~~~

~~~html
<!--views/user/index.vue -->
<template>
  <div>
    <router-view></router-view>
    <ul>
      <li>地址管理</li>
      <li>订单管理</li>
      <li>浏览历史</li>
    </ul>
  </div>
</template>

~~~



#### 3.8、404路由

作用：用于处理当路由匹配不上的时候页面的展示（不做404路由，则页面限时白板页面）

由于Vue路由是从上到下执行的，**只要在路由配置规则中最后面放个*号（通配符）路由就可以了**，例如：

```html
<!--views/error/404.vue-->
<template>
  <div> 抱歉，您查找页面不存在 - 404 </div>
</template>
```



配置404路由一定是在最后

~~~javascript
const routes = [
    ...,
    // 404路由
    { path: "*", component: NotFound },
];
~~~

问题：正常情况下404找不到会有状态码，是404，请问，为什么我们现在看到的状态码是200？

答：目前是在做前端开发，不是后端开发，无法指定返回的状态码，等到vue项目上线后可以与后端服务器结合实现状态码的指定。



#### 3.9、动态路由匹配（重点）

> 扩展：restful
>
> restful一个接口设计的开发规范（是规范不是标准），规范了请求的**地址格式**、请求方式、参数形式、响应的格式等等。
>
> 以往给一个请求地址传参一般是`xxx.com/index.php?id=123&age=23`，以上形式在restful规范中应该写成：`xxx.com/index.php/123/23`
>
> 本节知识点就是为了restful服务的，看如果在vue中使用restful形式进行**参数传递**。

所谓动态路由就是路由规则中有部分规则是动态变化的，不是固定的值，需要去匹配取出数据（即`路由参数`）。

- 如何传递
  - 在声明路由的时候，将可变部分通过“`:变量名`”的形式进行替代
- 如何获取
  - 获取this.$route来获取

~~~javascript
{ // 动态路由，name是一个参数的名称
    path: '/detail/:name',
    name: 'detail',
    component: () => import('@/views/detail/index.vue')
  },

~~~

```vue
<!--views/home/index.vue-->
<template>
  <div>
    <ul>
      <!-- <li v-for="item of list" :key="item.id">
        {{ item.name }}
      </li> -->
      <!-- 字符串拼接 -->
      <!-- <router-link :to="'/detail/' + item.name" tag="li" v-for="item of list" :key="item.id">
        {{ item.name }}
      </router-link> -->
      <!-- 对象path属性拼接 -->
      <!-- <router-link :to="{ path: '/detail/' + item.name }" tag="li" v-for="item of list" :key="item.id">
        {{ item.name }}
      </router-link> -->
      <!-- 命名路由传递参数 -->
      <router-link :to="{ name: 'detail', params: { name: item.name } }" tag="li" v-for="item of list" :key="item.id">
        {{ item.name }}
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      list: [
        {
          id: 1,
          name: '张三'
        },
        {
          id: 2,
          name: '李四'
        },
        {
          id: 3,
          name: '王五'
        },
        {
          id: 4,
          name: '亢成🐯'
        }
      ]
    }
  },
  mounted () {
    console.log(this.$router)
    console.log(this.$route)
  }
}
</script>

```



~~~vue
<!--views/detail/index.vue-->
<template>
  <div>
    详情 -- {{ name }}
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: ''
    }
  },
  mounted () {
    console.log(this.$route.params.name)
    this.name = this.$route.params.name
  }
}
</script>

~~~

路由规则中的“:”只是在声明的时候写，在使用的时候不需要写“:”，例如如下代码：





问题：如上代码，如果路由规则里声明需要传递参数，但是实际使用的时候没传递参数会怎么样？

答：如果声明需要传递参数，但是实际不传的话则会影响落地页的显示，显示成白板（但是不报错）。但是如果有404路由在规则的最后，则匹配404路由。



**注意：在实际开发的时候会有可能需要传参也可能不需要传参的情况，这个时候需要用到`可选路由参数`点。**

定义可选路由参数的方式很简单，只需要在原有的路由参数声明位置后面加上个`?`即可。例如：

~~~javascript
{ path: "showdetail/:id?", component: ShowDetail },
~~~

```js
 { // 动态路由，name是一个参数的名称
    // ? 代表的就是可选参数name
    path: '/detail/:name?',
    name: 'detail',
    component: () => import('@/views/detail/index.vue')
  },
```



目前地址栏传递参数已经支持2种形式：

- 查询字符串，也就是“?”传参形式
- 动态路由参数，也就是“/user/:id”形式

后续开发的时候如何选择？

- **要不要遵循restful规则**
  - 遵循
    - 请求需要使用动态路由参数形式
      - GET：/user/100，获取用户信息，id为100
      - POST：/user，添加一个用户
      - PUT：/user/100，修改用户信息，id为100
      - DELETE：/user/100，删除用户，id是100
  - 不遵循
    - 看你领导心情
      - 看你心情
- 看后端



#### 3.10、命名路由

命名路由：路由别名，顾名思义就是给路由起名字（外号）。

高尔基（阿列克赛·马克西莫维奇·高尔基）

通过一个名称来标识一个路由显得更方便一些，特别是在链接一个路由，或者是执行一些跳转的时候。

~~~javascript
// 路由
const router = new VueRouter({
  routes: [
    {
      path: '/user/:id',
      name: 'user',
      component: User
    }
  ]
})
~~~

~~~html
<!-- 声明路由 -->
<router-link :to="{ name: 'user', params: { id: 123 }}">User</router-link>
~~~

问：一般什么使用用命名路由？

答：当路由本身的path写法比较长的时候，建议写命名的方式。而且需要注意，如果使用的是path写法，则当path发生变化后，其对应的导航地址也需要跟着变化。但是如果使用了别名则不用理会path内容的变化。

#### 3.11 别名

**`/a` 的别名是 `/b`，意味着，当用户访问 `/b` 时，URL 会保持为 `/b`，但是路由匹配则为 `/a`，就像用户访问 `/a` 一样。**

上面对应的路由配置为：

```js
{
    path: '/home', // 路径
    name: 'home', // 命名路由
    alias: '/h',
    component: Home
  },
```

#### 3.12 命名视图

有时候想同时 (同级) 展示多个视图，而不是嵌套展示，例如创建一个布局，有 `sidebar` (侧导航) 和 `main` (主内容) 两个视图，这个时候命名视图就派上用场了。你可以在界面中拥有多个单独命名的视图，而不是只有一个单独的出口。如果 `router-view` 没有设置名字，那么默认为 `default`。

```vue
<!--App.vue-->
<template>
  <div id="app">
    <router-view/>
    <router-view name="footer"></router-view>
  </div>
</template>

<style lang="stylus">
.router-link-active
  color #f66
#app
  font-family Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>

```

```vue
<!--components/Footer.vue-->
<template>
  <footer>
    <ul>
      <router-link to="/home" tag="li">首页</router-link>
      <router-link to="/kind" tag="li">分类</router-link>
      <router-link :to="{ path: '/cart', query: { id: 100 } }" tag="li">购物车</router-link>
      <router-link to="/user?id=1000" tag="li">我的</router-link>
    </ul>
  </footer>
</template>

```

```js
// router/index.js
import Vue from 'vue'
import VueRouter from 'vue-router'
// import Home from '../views/Home.vue'
// 什么时候使用路由的懒加载
import Home from '@/views/home/index.vue'
import Kind from '@/views/kind/index.vue'
import Footer from '@/components/Footer.vue'

// 编程式导航时连续点击同一个选项，触发警告
const originalPush = VueRouter.prototype.push
VueRouter.prototype.push = function push (location) {
  return originalPush.call(this, location).catch((err) => err)
}
// use
Vue.use(VueRouter)

const routes = [
  { // 路由的匹配是从上到下，匹配到就停止
    path: '/',
    redirect: '/home'
  },
  {
    path: '/home', // 路径
    name: 'home', // 命名路由
    alias: '/h',
    // component: Home
    components: {
      default: Home,
      footer: Footer
    }
  },
  {
    path: '/kind',
    name: 'kind',
    // component: Kind
    components: {
      default: Kind,
      footer: Footer
    }
  },
  {
    path: '/cart',
    name: 'cart',
    // component: () => import('@/views/cart/index.vue')
    components: {
      default: () => import('@/views/cart/index.vue'),
      footer: Footer
    }
  },
  { // 动态路由，name是一个参数的名称
    // ? 代表的就是可选参数name
    path: '/detail/:name?',
    name: 'detail',
    component: () => import('@/views/detail/index.vue')
    // components: {
    //   default: () => import('@/views/detail/index.vue')
    // }
  },
  {
    path: '/user',
    name: 'user',
    // 如果有嵌套路由，那么一定在这个页面有 <router-view></router-view>
    // component: () => import('@/views/user/index.vue'),
    components: {
      default: () => import('@/views/user/index.vue'),
      footer: Footer
    },
    children: [ // 浏览器输入 /user/nologin   以及/user/logined 查看效果
      {
        path: 'nologin', // 嵌套路由不要加 /
        name: 'nologin',
        component: () => import('@/views/user/nologin.vue')
      },
      {
        path: 'logined',
        name: 'logined',
        component: () => import('@/views/user/logined.vue')
      }
    ]
  },
  {
    path: '*',
    component: () => import('@/views/error/404.vue')
  }
]
console.log(process.env.BASE_URL)
const router = new VueRouter({
  mode: 'history', // hash
  base: process.env.BASE_URL,
  routes
})

export default router

```

