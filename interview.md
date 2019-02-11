# 中高级前端大厂面试秘籍，寒冬中为您保驾护航，直达大厂

## 引言

当下，正面临着近几年来的最严重的互联网寒冬，听得最多的一句话便是：相见于江湖~🤣。缩减HC、裁员不绝于耳，大家都是人心惶惶，年前如此，年后想必肯定又是一场更为惨烈的江湖厮杀。但博主始终相信，**寒冬之中，人才更是尤为珍贵。只要有过硬的操作和装备，在逆风局下，同样也能来一波收割翻盘。**

博主也是年前经历了一番厮杀，最终拿到多家大厂的 offer。在闭关修炼的过程中，自己整理出了一套面试秘籍供自己反复研究，后来给了多位有需要的兄台，均表示相当靠谱，理应在这寒冬之中回报于社会。于是决定花点精力整理成文，让大家能比较系统的反复学习，快速提升自己。

面试固然有技巧，但绝不是伪造与吹流弊，通过一段短时间沉下心来闭关修炼，出山收割，步入大厂，薪资翻番，岂不爽哉？🤓

## 修炼原则

想必大家很厌烦笔试和考察知识点。因为其实在平时实战中，讲究的是开发效率，很少会去刻意记下一些细节和深挖知识点，脑海中都是一些分散的知识点，无法系统性地关联成网，一直处于时曾相识的状态。不知道多少人和博主一样，至今每次写阻止冒泡都需要谷歌一番如何拼写。🤪。

以如此的状态，定然是无法在面试的战场上纵横的。其实面试就犹如考试，大家回想下高考之前所做的事，无非就是 **理解** 和 **系统性记忆**。本秘籍的知识点较多，花点时间一个个理解并记忆后，自然也就融会贯通，无所畏惧。

由于本秘籍为了便于记忆，快速达到应试状态，类似于复习知识大纲。知识点会尽量的精简与总结大纲，知识脉络，并不去展开深入细节，面面俱到，有兴趣或者无法理解的童鞋可以自行谷歌下对应知识点的详细内容。😋

## CSS

### 1. 盒模型

页面渲染时，dom 元素所采用的 **布局模型**。可通过`box-sizing`进行设置。根据计算宽高的区域可分为：

- `content-box` (W3C 标准盒模型)
- `border-box` (IE 盒模型)
- `padding-box`
- `margin-box`

### 2. BFC

**格式化上下文**，是一个独立的渲染区域，让处于 BFC 内部的元素与外部的元素相互隔离，使内外元素的定位不会相互影响。

> IE下为 Layout，可通过 zoom:1 触发

- 触发条件:
	- 根元素
	- `positon: absolute/fixed`
	- `display: inline-block / table`
	- `float` 元素
	- `ovevflow` !== `visible`
		
- 规则:
	- 属于同一个 BFC 的两个相邻 Box 垂直排列
	- 属于同一个 BFC 的两个相邻 Box 的 margin 会发生重叠
	- BFC 中子元素不会超出他的包含块
	- BFC 的区域不会与 float 的元素区域重叠
	- 计算 BFC 的高度时，浮动子元素也参与计算
	- 文字层不会被浮动层覆盖，环绕于周围

- 应用:
	- 阻止`margin`重叠
	- 可以包含浮动元素 —— 清除内部浮动(清除浮动的原理是两个`div`都位于同一个 BFC 区域之中)
	- 自适应两栏布局
	- 可以阻止元素被浮动元素覆盖

### 3.层叠上下文

元素提升为一个比较特殊的图层，在三维空间中 **(z轴)** 高出普通元素一等。

- 触发条件
	- 根层叠上下文(`html`)
	- `position`
	- css3属性 
		- `flex`
		- `transform`
		- `opacticy`
		- `filter`
		- `will-change`
		- `-webkit-overflow-scrolling`

- 层叠等级：层叠上下文在z轴上的排序
	- 在同一层叠上下文中，层叠等级才有意义
	- `z-index`的优先级最高

<img width="600" src="./images/interview/4.png">

### 4. 居中布局

- 水平居中
	- 行内元素: `text-align: center`
	- 块级元素: `margin: 0 auto`
	- `absolute + transform`
	- `flex + justify-content: center`
	
- 垂直居中
	- `line-height: height` 
	- `absolute + transform`
	- `flex + align-items: center`
	- `table`
	
- 水平垂直居中
	- `absolute + transform`
	- `flex + justify-content + align-items`

### 5. 选择器优先级：

- `!important` > 行内样式 > `#id` > `.class` > `tag` > * > 继承 > 默认 
- 选择器 **从右往左** 解析

### 6.去除浮动影响，防止父级高度塌陷

- 通过增加尾元素清除浮动
	- `:after / <br> : clear: both`
- 创建父级 BFC
- 父级设置高度

### 7.link 与 @import 的区别
	
- `link`功能较多，可以定义 RSS，定义 Rel 等作用，而`@import`只能用于加载 css
- 当解析到`link`时，页面会同步加载所引的 css，而`@import`所引用的 css 会等到页面加载完才被加载
- `@import`需要 IE5 以上才能使用
- `link`可以使用 js 动态引入，`@import`不行

### 8. CSS预处理器(Sass/Less/Postcss)

常用功能: 

- 嵌套
- 变量
- 循环语句
- 条件语句
- 自动前缀
- 单位转换
- mixin复用

### 9.CSS动画

- `transition`: 过渡动画
	- `transition-property`: 属性
	- `transition-duration`: 间隔
	- `transition-timing-function`: 曲线
	- `transition-delay`: 延迟
	- 常用钩子: `transitionend`

- `animation / keyframes`
	- `animation-name`: 动画名称，对应`@keyframes`
	- `animation-duration`: 间隔
	- `animation-timing-function`: 曲线
	- `animation-delay`: 延迟
	- `animation-iteration-count`: 次数
		- `infinite`: 循环动画
	- `animation-direction`: 方向
		- `alternate`: 反向播放 
	- `animation-fill-mode`: 静止模式
		- `forwards`: 停止时，保留最后一帧
		- `backwards`: 停止时，回到第一帧
		- `both`: 同时运用 `forwards / backwards`
	- 常用钩子: `animationend`
		
- 动画属性: 尽量使用动画属性进行动画，能拥有较好的性能表现
	- `translate`
	- `scale`
	- `rotate`
	- `skew`
	- `opacity`
	- `color`

## JavaScript

### 1. 原型 / 构造函数 / 实例

- 原型`(prototype)`: 一个简单的对象，用于实现对象的**属性继承**。可以简单的理解成对象的爹。在 Firefox 和 Chrome 中，每个`JavaScript`对象中都包含一个`__proto__` (非标准)的属性指向它爹(该对象的原型)，可`obj.__proto__`进行访问。

- 构造函数: 可以通过`new`来**新建一个对象**的函数。

- 实例: 通过构造函数和`new`创建出来的对象，便是实例。**实例通过`__proto__`指向原型，通过`constructor`指向构造函数**。

说了一大堆，大家可能有点懵逼，这里来举个栗子，以`Object`为例，我们常用的`Object`便是一个构造函数，因此我们可以通过它构建实例。

```js 
// 实例
const instance = new Object()
```
则此时， 实例为`instance`, 构造函数为`Object`，我们知道，构造函数拥有一个`prototype`的属性指向原型，因此原型为:

```js
// 原型
const prototype = Object.prototype
```

这里我们可以来看出三者的关系:

```js
实例.__proto__ === 原型

原型.constructor === 构造函数

构造函数.prototype === 原型

原型.constructorr === 构造函数
```

放大来看，我画了张图供大家彻底理解:

<img width="600" src="./images/interview/2.png">

### 2.原型链：

**原型链是由原型对象组成**，每个对象都有 `__proto__` 属性，指向了创建该对象的构造函数的原型，`__proto__` 将对象连接起来组成了原型链。是一个用来**实现继承和共享属性**的有限的对象链。

- **属性查找机制**: 当查找对象的属性时，如果实例对象自身不存在该属性，则沿着原型链往上一级查找，找到时则输出，不存在时，则继续沿着原型链往上一级查找，直至最顶级的原型对象`Object.prototype`，如还是没找到，则输出`undefined`；

- **属性修改机制**: 只会修改实例对象本身的属性，如果不存在，则进行添加该属性，如果需要修改原型的属性时，则可以用: `b.prototype.x = 2`；但是这样会造成所有继承于该对象的实例的属性发生改变。

### 3. 执行上下文(EC)

执行上下文可以简单理解为一个对象:

- 它包含三个部分: 
	- 变量对象(VO)
	- 作用域链(词法作用域)
	- `this`指向
	
- 它的类型: 
	- 全局执行上下文
	- 函数执行上下文  	  
	- `eval`执行上下文
	
- 代码执行: 
	- 创建 **全局上下文** (global EC)
	- 全局执行上下文 (caller) 逐行**自上而下**执行，遇到函数时，进入**函数执行上下文** (callee)， callee 被`push`到执行栈顶层
	- 函数执行上下文被激活，成为 active EC, 开始执行函数中的代码，caller被挂起
	- 函数执行完后，callee 被`pop`移除出执行栈，控制权交还全局上下文 (caller)，继续执行

### 2.变量对象

变量对象可以抽象为一种 **数据作用域**，其实也可以理解为就是一个简单的对象，它存储着该作用域中的所有 **变量和函数声明(不包含函数表达式)**。

> 活动对象 (AO): 当变量对象所处的上下文为 active EC 时，称为活动对象。

### 3. 作用域

作用域可理解为 **变量的作用范围**。
	
- 块级作用域
- 函数作用域
- **声明提前**: 一个声明在函数体内都是可见的, 函数优先于变量
- 非匿名自执行函数，函数变量为 **只读** 状态，无法修改
	
```js
const foo = 1
(function foo() {
    foo = 10  // 由于foo在函数中只为可读，因此赋值无效
    console.log(foo)
}()) 

// 结果打印：  ƒ foo() { foo = 10 ; console.log(foo) }
```

### 4.作用域链

作用域链: 对象列表，包含 **父级和自身的变量对象**，因此我们便能通过作用域链访问到父级，父父级里声明的变量或者函数。

- 包含: 	
	- `[[scope]]`: 指向父级变量对象和作用域链，也就是包含了父级的`[[scope]]`和`AO`
	- AO: 自身活动对象

### 5. 闭包

闭包属于一种特殊的作用域，称为 **静态作用域**。它在父函数被销毁的情况下，子函数的`[[scope]]`中仍然保留着父级的单变量对象和作用域链，因此可以继续访问到父级的变量对象，这样的函数称为闭包。
	
- 闭包问题: 多个子函数的`[[scope]]`都是同一份，是共享的。因此父级的变量对象被修改时，所有子函数都受到影响。
- 解决:
	- 变量可以通过 **参数的形式** 传入，避免使用默认的`[[scope]]`向上查找 
	- `setTimeout`第三个参数传入
	- 使用 **块级作用域**，避免共享

### 6. script 引入方式：

- html 静态`<script>`引入
- js 动态插入`<script>`
- `<script defer>`: 异步加载，元素解析完成后执行
- `<script async>`: 异步加载，与元素渲染并行执行

### 7. 对象的拷贝

- 浅拷贝: 以赋值的形式拷贝引用对象，仍指向同一个地址，**修改时原对象也会受到影响**
	- `Object.assign`
	- 展开运算符(...)
	
- 深拷贝: 完全拷贝一个新对象，**修改时原对象不再受到任何影响**
	- `JOSN.parse(JSON.stringify(obj))`: 性能最快
		- 循环引用的对象时，报错
		- 当值为函数或`undefined`时，无法拷贝  
	- 递归进行复制

### 8. new运算符的执行过程

- 新生成一个对象
- 链接到原型:  `obj.__protp__ = Con.prototype`
- 绑定this : `apply`
- 返回新对象

### 9. instanceof原理

能在实例的 **原型对象链** 中找到该构造函数的`prototype`属性所指向的 **原型对象**，就返回`true`。

### 10. 复用

- 继承 
- 复制`extend`
- 混入`mixin`
- 借用`apply/call`

### 11. 继承

- 最优化: **圣杯模式**
	
```js
var inherit = (function(c,p){
	var F = function(){};
	return function(c,p){
		F.prototype = p.prototype;
		c.prototype = new F();
		c.uber = p.prototype;
		c.prototype.constructor = c;
	}
})();
``` 
	
- 使用 ES6 的语法 `class / extends`

### 12. 类型转换

- -、*、/、% ：一律转换成数值后计算
- +： 
	- 数字 + 字符串 = 字符串， 运算顺序是从左到右
	- 数字 + 对象， 优先调用对象的`valueOf` -> `toString`
	- 数字 + `boolean/null` = 数字
	- 数字 + `undefined` == `NaN`
- `[1].toString == '1'`
- `{}.toString == '[object object]'`
- `NaN` !== `NaN` 、`+undefined == NaN`

### 13. 类型判断

- 基本类型(`null / string / number / boolean / undefined`) + `function`: 直接使用 `typeof`
- 其余引用类型: 调用`toString`后根据`[object XXX]`进行判断

很稳的判断封装:

```js
let class2type = {}
'Array Date RegExp Object Error'.split(' ').forEach(e => class2type[ '[object ' + e + ']' ] = e.toLowerCase()) 

function type(obj) {
    if (obj == null) return String(obj)
    return typeof obj === 'object' ? class2type[ Object.prototype.toString.call(obj) ] || 'object' : typeof obj
}
```
### 14. 模块化

- 分类: 
	- ES6： `import / exports`
	- commonjs: `require / module.exports / exports`
	- AMD: `require / defined`

- `require`与`import`的区别
	- `require`支持 **动态导入**，`import`不支持，正在提案 (babel 下可支持)
	- `require`是同步导入，`import`属于异步导入
	- `require`是值拷贝，导出值变化不会影响导入值；`import`指向内存地址，导入值会随导出值而变化

### 15. 反抖与节流

- **防抖 (debounce)**: 多次操作变为最后一次执行

```js
function debounce(fn, wait, immediate) {
    let timer = null

    return function() {
        let args = arguments
        let context = this

        if (immediate && !timer) {
            fn.apply(context, args)
        }

        if (timer) clearTimeout(timer)
        timer = setTimeout(() => {
            fn.apply(context, args)
        }, wait)
    }
}
```

- **节流(throttle)**: 每隔一段时间后执行一次

```js
function throttle(fn, wait, immediate) {
    let timer = null
    let callNow = true
    
    return function() {
        let context = this,
            args = arguments

        if (callNow) {
            fn.apply(context, args)
            callNow = false
        }

        if (!timer) {
            timer = setTimeout(() => {
                fn.apply(context, args)
                timer = null
            }, wait)
        }
    }
}
```

### 16. 函数执行改变this
	
- call: fn.call(this, 1, 2)
- apply: fn.apply(this, [1, 2])
- bind: fn.bind(this)(1,2)	 

### 17. ES6/ES7

- 声明
	- `let / const`: 块级作用域、不存在变量提升、暂时性死区、不允许重复声明
	- `const`: 声明常量，无法修改
- 解构赋值
- `class / extend`
- `Set / Map`
- `Promise`的使用与实现
- `generator`: 
	- `yield`: 暂停代码 
	- `next()`: 继续执行代码

```js
function* helloWorld() {
  yield 'hello';
  yield 'world';
  return 'ending';
}

const generator = helloWorld();

generator.next()  // { value: 'hello', done: false }

generator.next()  // { value: 'world', done: false }

generator.next()  // { value: 'ending', done: true }

generator.next()  // { value: undefined, done: true }

```

- `await / async`: 是`generator`的语法糖， babel中是基于`promise`实现。

```js
async function getUserByAsync(){
   let user = await fetchUser();
   return user;
}

const user = await getUserByAsync()
console.log(user)
``` 

### 18. AST

**抽象语法树 (Abstract Syntax Tree)**，将代码逐字母解析成树状对象的形式，便于代码转换、代码语法检查，代码风格检查，代码格式化，代码高亮，代码错误提示，代码自动补全等等。例如:

```js
function square(n){
	return n * n
}
```

通过解析转化成的`AST`如下图:

<img src="./images/interview/5.png" width="400">

### 19. babel编译原理

-  babylon 解析代码成 AST
-  babel-traverse 对 AST 进行遍历转译，得到新的 AST
-  新 AST 通过 babel-generator 转换成 ES5

### 20. 函数柯里化

在一个函数中，首先填充几个参数，然后再返回一个新的函数的技术，称为柯里化

```js
const add = function add(x) {
	return function (y) {
		return x + y
	}
}

add(1)(2)  // 3
```

### 21. 数组(array)

- `map`: 遍历数组，返回回调返回值组成的新数组

- `forEach`: 无法`break`，可以用`try/catch`中`throw new Error`来停止
- `filter`: 过滤
- `some`: 有一项返回`true`，则整体为`true`
- `every`: 有一项返回`false`，则整体为`false`
- `join`: 通过指定连接符生成字符串
- `push / pop`: 末尾推入和弹出，改变原数组， 返回推入/弹出项
- `unshift / shift`: 头部推入和弹出，改变原数组，返回操作项
- `sort(fn) / reverse`: 排序与反转，改变原数组
- `concat`: 连接数组，不影响原数组， 浅拷贝
- `slice(start, end)`: 返回截断后的新数组，不改变原数组
- `splice(start, number, value...)`: 返回删除元素组成的数组，value 为插入项，改变原数组
- `indexOf / lastIndexOf(value, fromIndex)`: 查找数组项，返回对应的下标
- `reduce / reduceRight(fn(prev, cur)， defaultPrev)`: 两两执行，prev 为上次化简函数的`return`值，cur 为当前值(从第二项开始) 

- 数组乱序： 
	
```js
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
arr.sort(function () {
    return Math.random() - 0.5;
});
```

- flat: [1,[2,3]] --> [1, 2, 3]

```js
arr.prototype.flat = function() {
    this.toString().split(',').map(item=> +item )
}
```

## 浏览器

### 1. 跨标签页通讯

- `localStorage`与监听`storage`
- `cookie`与`setInterval`

### 2. 浏览器结构
- 用户界面
- 主进程 
- 内核
	- 渲染引擎
	- JS 引擎
		- 执行栈 
	- 事件触发线程
		- 消息队列
			- 微任务
			- 宏任务  
	- 网络异步线程
	- 定时器线程

### 3. Event Loop

一次事件循环是执行一个宏任务，然后执行清空微任务列表，循环再执行宏任务，再清微任务列表 

- 微任务 `microtask(jobs)`: `promise / ajax / Object.observe`
- 宏任务 `macrotask(task)`: `setTimout / script / IO / UI Rendering`

### 4. 从输入 url 到展示的过程

- DNS 解析 
- TCP 三次握手
- 发送请求，分析 URL，设置请求报文(头，主体)
- 服务器返回请求的文件 (html)
- 浏览器渲染
	- HTML parser --> DOM Tree
		- 标记化算法，进行状态的标记
		- dom 树构建 
	- CSS parser --> Style Tree
	- attachment --> Render Tree
	- layout
	- GPU painting

### 5. 重绘与回流

- **重绘(repaint)**: 当元素样式的改变不影响布局时，浏览器将使用重绘对元素进行更新，此时**损耗较少**

- **回流(reflow)**: 当元素的尺寸、结构或触发某些属性时，浏览器会重新渲染页面，称为回流。会触发回流的操作: 
	- 页面初次渲染
	- 浏览器窗口大小改变
	- 元素尺寸、位置、内容发生改变
	- 元素字体大小变化
 	- 添加或者删除可见的 dom 元素
	- 激活 CSS 伪类（例如：:hover）
	- 查询某些属性或调用某些方法
		- clientWidth、clientHeight、clientTop、clientLeft
		- offsetWidth、offsetHeight、offsetTop、offsetLeft
		- scrollWidth、scrollHeight、scrollTop、scrollLeft
		- getComputedStyle()
		- getBoundingClientRect()
		- scrollTo()
  

**回流必定触发重绘，重绘不一定触发回流。重绘的开销较小，回流的代价较高。**

#### 最佳实践:

- css
	- 避免使用`table`布局
	- 将动画效果应用到`position`属性为`absolute`或`fixed`的元素上

- javascript 
	- 避免频繁操作样式，可汇总后统一 **一次修改**
	- 尽量使用`class`进行样式修改
	- 减少`dom`的增删次数，可使用 **字符串** 或者 `documentFragment` 一次性插入
	- 极限优化时，修改样式可将其`display: none`后修改
	- 避免多次触发上面提到的那些会触发回流的方法，可以的话尽量用 **变量存住**

### 6. 存储

- `cookie`: 通常用于存储用户身份，登录状态等
	- http 中自动携带， 体积上限为 4K， 可自行设置过期时间
- `localStorage / sessionStorage`: 长久储存/窗口关闭删除， 体积限制为 4~5M
- `indexDB`

### 7. Web Worker

现代浏览器为`JavaScript`创造的 **多线程环境**。可以新建，并将部分任务分配到`worker`线程并行运行，两个线程可 **独立运行，互不干扰**，可通过自带的 **消息机制** 相互通信。

### 8. V8垃圾回收机制

- 首先执行**新生代算法**: 用于存活较短的对象
	- Scavenge GC: 对象从 from space 转移到 to space (两个不同的空间)
- **老生代算法**: 用于存活时间较长的对象
	- 从新生代算法转移到老生代算法的条件
		- 经历过 Scavenge GC 的对象
		- 当 to space 体积超过25%
	- **标记清除算法**: 
		- 增量标记: 小模块标记，在代码执行间隙执行
		- 并发标记(2018): 不阻塞 js 执行
	- **压缩算法**: 清除后导致的内存碎片化

### 9. 内存泄露

- **全局变量** 无法被回收
- **定时器** 与外部变量相互关系，导致外部变量无法被释放
- **事件监听** 没有正确销毁 (低版本浏览器可能出现)
- **闭包** 会导致父级中的变量无法被释放

## 框架：Vue

### 1. nextTick

在下次`dom`更新循环结束之后执行延迟回调，可用于获取更新后的`dom`状态

- 默认使用`mincrotasks`, `v-on`使用`macrotasks`
- `macrotasks`
	- `setImmediate / MessageChannel / setTimeout`

### 2. 生命周期

- `_init_`  
	- `initLifecycle/Event`，往`vm`上挂载各种属性
	- `callHook: beforeCreated`: 实例刚创建
	- `initInjection/initState`: 初始化注入和 data 响应性
	- `created`: 创建完成，属性已经绑定， 但还未生成真实`dom`
	- 进行元素的挂载： `$el / vm.$mount()`
	- 是否有`template`: 解析成`render function`
		- `*.vue`文件: `vue-loader`会将`<template>`编译成`render function`
	- `beforeMount`: 模板编译/挂载之前
	- 执行`render function`，生成真实的`dom`，并替换到`dom tree`中
	- `mounted`: 组件已挂载

- `update`:
	- `re-vdom diff`
	- `flushScheduleQueue`
		- `watcher.before`: `beforeUpdate`组件更新			- `watcher.run()`: `watcher`触发更新
	- `updated`: 组件已更新
	
- `actived / deactivated(keep-alive)`: 不销毁，缓存，组件激活与失活
	
- `destroy`:
	- `beforeDestroy`: 销毁开始
	- 销毁自身且递归销毁子组件以及事件监听
		- `remove()`: 删除节点
		- `watcher.teardown()`: 删除依赖
		- `vm.$off()`: 删除监听
	- `destroyed`: 完成后触发

上面是`vue`的声明周期的简单梳理，接下来我们直接以代码的形式来完成`vue`的初始化

```js

new Vue({})

// 初始化Vue实例
function _init() {
	 // 挂载属性
    initLifeCycle(vm) 
    // 初始化事件系统，钩子函数等
    initEvent(vm) 
    // 编译slot、vnode
    initRender(vm) 
    // 触发钩子
    callHook(vm, 'beforeCreate')
    // 添加inject功能
    initInjection(vm)
    // 完成数据响应性 props/data/watch/computed/methods
    initState(vm)
    // 添加 provide 功能
    initProvide(vm)
    // 触发钩子
    callHook(vm, 'created')
		
	 // 挂载节点
    if (vm.$options.el) {
        vm.$mount(vm.$options.el)
    }
}

// 挂载节点实现
function mountComponent(vm) {
	 // 获取 render function
    if (!this.options.render) {
        // template to render
        // Vue.compile = compileToFunctions
        let { render } = compileToFunctions() 
        this.options.render = render
    }
    // 触发钩子
    callHook('beforeMounte')
    // 初始化观察者
    // render 渲染 vdom， 
    vdom = vm.render()
    // update: 根据 diff 出的 patchs 挂载成真实的 dom 
    vm._update(vdom)
    // 触发钩子  
    callHook(vm, 'mounted')
}

// 更新节点实现
funtion queueWatcher(watcher) {
	nextTick(flushScheduleQueue)
}

// 清空队列
function flushScheduleQueue() {
	 // 遍历队列中所有修改
    for(){
	    // beforeUpdate
        watcher.before()
         
        // 依赖局部更新节点
        watcher.update() 
        callHook('updated')
    }
}

// 销毁实例实现
Vue.prototype.$destory = function() {
	 // 触发钩子
    callHook(vm, 'beforeDestory')
    // 自身及子节点
    remove() 
    // 删除依赖
    watcher.teardown() 
    // 删除监听
    vm.$off() 
    // 触发钩子
    callHook(vm, 'destoryed')
}
```
	
### 3. 数据响应

- `Observe(观察者)`观察 props 与 state
- 遍历 props 与 state，对每个属性进行响应性定义
- 使用 `defineProperty` 重写每个属性的 get/set，(`defineReactive`）
	- `get`: 收集依赖
		- `Dep.depend()`
		- `watcher.addDep()`
	- `set`: 派发更新
		- `Dep.notify()`
		- `watcher.update()`
		- `queenWatcher()`
		- `nextTick`
		- `flushScheduleQueue`
		- `watcher.run()`
		- `updateComponent()`

大家可以先看下面的数据相应的代码实现后，理解后就比较容易看懂上面的简单脉络了。

```js
let data = {a: 1}
// 数据响应性
observe(data)

// 初始化观察者
new Watcher(data, 'name', updateComponent)
data.a = 2

// 简单表示用于数据更新后的操作
function updateComponent() {
    vm._update() // patchs
}

// 监视对象
function observe(obj) {
	 // 遍历对象，使用 get/set 重新定义对象的每个属性值
    Object.keys(obj).map(key => {
        defineReactive(obj, key, obj[key])
    })
}

function defineReactive(obj, k, v) {
    // 递归子属性
    if (type(v) == 'object') observe(v)
    
    // 新建依赖收集器
    let dep = new Dep()
    // 定义get/set
    Object.defineProperty(obj, k, {
        enumerable: true,
        configurable: true,
        get: function reactiveGetter() {
        	  // 当有获取该属性时，证明依赖于该对象，因此被添加进收集器中
            if (Dep.target) {
                dep.addSub(Dep.target)
            }
            return v
        },
        // 重新设置值时，触发收集器的通知机制
        set: function reactiveSetter(nV) {
            v = nV
            dep.nofify()
        },
    })
}

// 依赖收集器
class Dep {
    constructor() {
        this.subs = []
    }
    addSub(sub) {
        this.subs.push(sub)
    }
    notify() {
        this.subs.map(sub => {
            sub.update()
        })
    }
}

Dep.target = null

// 观察者
class Watcher {
    constructor(obj, key, cb) {
        Dep.target = this
        this.cb = cb
        this.obj = obj
        this.key = key
        this.value = obj[key]
        Dep.target = null
    }
    addDep(Dep) {
        Dep.addSub(this)
    }
    update() {
        this.value = this.obj[this.key]
        this.cb(this.value)
    }
    before() {
        callHook('beforeUpdate')
    }
}
```
	
### 4. virtual dom 原理实现

- 创建 dom 树 
	
- 树的`diff`，同层对比，输出`patchs(listDiff/diffChildren/diffProps)`
	- 没有新的节点，返回
	- 新的节点`tagName`与`key`不变， 对比`props`，继续递归遍历子树
		- 对比属性(对比新旧属性列表):
			- 旧属性是否存在与新属性列表中
			- 都存在的是否有变化
			- 是否出现旧列表中没有的新属性
	- `tagName`和`key`值变化了，则直接替换成新节点
	
- 渲染差异
	- 遍历`patchs`， 把需要更改的节点取出来
	- 局部更新`dom` 

```js
// diff算法的实现
function diff(oldTree, newTree) {
	 // 差异收集
    let pathchs = {}
    dfs(oldTree, newTree, 0, pathchs)
    return pathchs
}

function dfs(oldNode, newNode, index, pathchs) {
    let curPathchs = []
    if (newNode) {
        // 当新旧节点的 tagName 和 key 值完全一致时
        if (oldNode.tagName === newNode.tagName && oldNode.key === newNode.key) {
        	  // 继续比对属性差异
            let props = diffProps(oldNode.props, newNode.props)
            curPathchs.push({ type: 'changeProps', props })
            // 递归进入下一层级的比较
            diffChildrens(oldNode.children, newNode.children, index, pathchs)
        } else {
        	  // 当 tagName 或者 key 修改了后，表示已经是全新节点，无需再比
            curPathchs.push({ type: 'replaceNode', node: newNode })
        }
    }

	 // 构建出整颗差异树
    if (curPathchs.length) {
    		if(pathchs[index]){
    			pathchs[index] = pathchs[index].concat(curPathchs)
    		} else {
    			pathchs[index] = curPathchs
    		}
    }
}

// 属性对比实现
function diffProps(oldProps, newProps) {
    let propsPathchs = []
    // 遍历新旧属性列表
    // 查找删除项
    // 查找修改项
    // 查找新增项
    forin(olaProps, (k, v) => {
        if (!newProps.hasOwnProperty(k)) {
            propsPathchs.push({ type: 'remove', prop: k })
        } else {
            if (v !== newProps[k]) {
                propsPathchs.push({ type: 'change', prop: k , value: newProps[k] })
            }
        }
    })
    forin(newProps, (k, v) => {
        if (!oldProps.hasOwnProperty(k)) {
            propsPathchs.push({ type: 'add', prop: k, value: v })
        }
    })
    return propsPathchs
}

// 对比子级差异
function diffChildrens(oldChild, newChild, index, pathchs) {
		// 标记子级的删除/新增/移动
    let { change, list } = diffList(oldChild, newChild, index, pathchs)
    if (change.length) {
        if (pathchs[index]) {
            pathchs[index] = pathchs[index].concat(change)
        } else {
            pathchs[index] = change
        }
    }

	 // 根据 key 获取原本匹配的节点，进一步递归从头开始对比
    oldChild.map((item, i) => {
        let keyIndex = list.indexOf(item.key)
        if (keyIndex) {
            let node = newChild[keyIndex]
            // 进一步递归对比
            dfs(item, node, index, pathchs)
        }
    })
}

// 列表对比，主要也是根据 key 值查找匹配项
// 对比出新旧列表的新增/删除/移动
function diffList(oldList, newList, index, pathchs) {
    let change = []
    let list = []
    const newKeys = getKey(newList)
    oldList.map(v => {
        if (newKeys.indexOf(v.key) > -1) {
            list.push(v.key)
        } else {
            list.push(null)
        }
    })

    // 标记删除
    for (let i = list.length - 1; i>= 0; i--) {
        if (!list[i]) {
            list.splice(i, 1)
            change.push({ type: 'remove', index: i })
        }
    }

    // 标记新增和移动
    newList.map((item, i) => {
        const key = item.key
        const index = list.indexOf(key)
        if (index === -1 || key == null) {
            // 新增
            change.push({ type: 'add', node: item, index: i })
            list.splice(i, 0, key)
        } else {
            // 移动
            if (index !== i) {
                change.push({
                    type: 'move',
                    form: index,
                    to: i,
                })
                move(list, index, i)
            }
        }
    })

    return { change, list }
}
```

### 5. Proxy 相比于 defineProperty 的优势

- 数组变化也能监听到
- 不需要深度遍历监听

```js
let data = { a: 1 }
let reactiveData = new Proxy(data, {
	get: function(target, name){
		// ...
	},
	// ...
})
```
	
### 6. vue-router

- `mode` 
	- `hash`
	- `history`
- 跳转
	- `this.$router.push()`
	- `<router-link to=""></router-link>`
- 占位
	- `<router-view></router-view>`

### 7. vuex

- `state`: 状态中心	 
- `mutations`: 更改状态
- `actions`: 异步更改状态
- `getters`: 获取状态
- `modules`: 将`state`分成多个`modules`，便于管理

## 服务端与网络

### 1. http/https协议

- 1.0 协议缺陷: 
	- 无法复用链接，完成即断开，**重新慢启动和 TCP 3次握手**
	- head of line blocking: 线头阻塞，导致请求之间互相影响
	
- 1.1 改进: 
	- **长连接**(默认 keep-alive)，复用
	- host 字段指定对应的虚拟站点
	- 新增功能:
		- 断点续传
		- 身份认证
		- 状态管理
		- cache 缓存
			- Cache-Control
			- Expires
			- Last-Modified
			- Etag
		
- 2.0:
	- 多路复用
	- 二进制分帧层: 应用层和传输层之间
	- 首部压缩
	- 服务端推送
	
- https: 
	- 证书(公钥)
	- SSL 加密
	- 端口 443

- TCP:
	- 三次握手
	- 四次挥手
	- 滑动窗口: 流量控制
	- 拥塞处理
		- 慢开始
		- 拥塞避免
		- 快速重传
		- 快速恢复 

- 缓存策略
	- Cache-Control/Expires: 浏览器判断缓存是否过期，未过期时，直接使用强缓存，**Cache-Control的 max-age 优先级高于 Expires**
	- 当缓存已经过期时，使用协商缓存
		- 唯一标识方案: Etag(response 携带) & If-None-Match(request携带，上一次返回的 Etag): 服务器判断资源是否被修改，如果一致，则直接返回 304 通知浏览器使用缓存，如不一致，则服务端返回新的资源
		- 最后一次修改时间: Last-Modified(response) & If-Modified-Since (request，上一次返回的Last-Modified)，逻辑如上
		
		- Last-Modified 缺点：
			- 周期性修改，但内容未变时，会导致缓存失效
			- 最小粒度只到 s， s 以内的改动无法检测到 
		- Etag 的优先级高于 Last-Modified

### 2. 常见状态码

- 1xx： 接受，继续处理 
- 200： 成功，并返回数据
- 201： 已创建
- 202： 已接受
- 203： 成为，但未授权
- 204： 成功，无内容
- 205： 成功，重置内容
- 206： 成功，部分内容
- 301： 永久移动，重定向
- 302： 临时移动，可使用原有URI
- 304： 资源未修改，可使用缓存
- 305： 需代理访问
- 400： 请求语法错误
- 401： 要求身份认证
- 403： 拒绝请求
- 404： 资源不存在
- 500： 服务器错误

### 3. get / post

- get: 缓存、请求长度受限、会被历史保存记录
	- 无副作用(不修改资源)，幂等(请求次数与资源无关)的场景 
- post: 安全、大数据、更多编码类型

<img width="600" src="./images/interview/3.png">

### Websocket

Websocket 是一个 **持久化的协议**， 基于 http ， 服务端可以 **主动 push**

- 兼容：
	- FLASH Socket
	- 长轮询： 定时发送 ajax
	- long poll： 发送 --> 有消息时再 response

- `new WebSocket(url)`
- `ws.onerror = fn`
- `ws.onclose = fn`
- `ws.onopen = fn`
- `ws.onmessage = fn`
- `ws.send()`

### TCP三次握手

- 客户端发送 syn(同步序列编号) 请求，进入 syn_send 状态，等待确认
- 服务端接收并确认 syn 包后发送 syn+ack 包，进入 syn_recv 状态
- 客户端接收 syn+ack 包后，发送 ack 包，双方进入 established 状态

### TCP四次挥手

- 客户端 -- FIN --> 服务端， FIN—WAIT
- 服务端 -- ACK --> 客户端， CLOSE-WAIT
- 服务端 -- ACK,FIN --> 客户端， LAST-ACK
- 客户端 -- ACK --> 服务端，CLOSED

### Node 的 Event Loop: 6个阶段

- timer: 执行`setTimeout / setInterval`
- I/O: 执行上轮循环残流的`callback`
- idle, prepare
- poll：等待回调
	- 1. 执行回调
	- 2. 执行定时器
		- 如有`setTimeout / setInterval`， 则返回 timer 阶段
		- 如有`setImmediate`，则前往 check 阶段
- check
	- 执行`setImmediate`
- close callbacks

### 跨域

- JSONP
- 设置 CORS: Access-Control-Allow-Origin：*
- postMessage
- document.domain

### 安全

- XSS攻击: 注入恶意代码
	- cookie 设置 httpOnly
	- 转义页面上的输入内容和输出内容 
- CSPF: 跨站请求伪造
	- get 不修改数据
	- 不被第三方网站访问到用户的 cookie
	- 设置白名单，不被第三方网站请求
	- 请求校验 

## 算法

### 1. 五大算法

- **贪心算法**: 局部最优解法
- **分治算法**: 分成多个小模块，与原问题性质相同
- **动态规划**: 每个状态都是过去历史的一个总结
- **回溯法**: 发现原先选择不优时，退回重新选择
- **分支限界法**

### 2. 基础排序算法

- 冒泡排序: 两两比较

```js
	function bubleSort(arr) {
	    var len = arr.length;
	    for (let outer = len ; outer >= 2; outer--) {
	        for(let inner = 0; inner <=outer - 1; inner++) {
	            if(arr[inner] > arr[inner + 1]) {
	                [arr[inner],arr[inner+1]] = [arr[inner+1],arr[inner]]
	            }
	        }
	    }
	    return arr;
	}
```

- 选择排序: 遍历自身以后的元素，最小的元素跟自己调换位置

```js
function selectSort(arr) {
    var len = arr.length;
    for(let i = 0 ;i < len - 1; i++) {
        for(let j = i ; j<len; j++) {
            if(arr[j] < arr[i]) {
                [arr[i],arr[j]] = [arr[j],arr[i]];
            }
        }
    }
    return arr
}
```
	
- 插入排序: 即将元素插入到已排序好的数组中

```js
function insertSort(arr) {
    for(let i = 1; i < arr.length; i++) {  //外循环从1开始，默认arr[0]是有序段
        for(let j = i; j > 0; j--) {  //j = i,将arr[j]依次插入有序段中
            if(arr[j] < arr[j-1]) {
                [arr[j],arr[j-1]] = [arr[j-1],arr[j]];
            } else {
                break;
            }
        }
    }
    return arr;
}
```
	
### 3. 高级排序算法

- 快速排序
	- 选择基准值(base)，原数组长度减一(基准值)，使用 splice
	- 循环原数组，小的放左边(left数组)，大的放右边(right数组);
	- concat(left, base, right)
	- 递归继续排序 left 与 right

```js
function quickSort(arr) {
    if(arr.length <= 1) {
        return arr;  //递归出口
    }
    var left = [],
        right = [],
        current = arr.splice(0,1); 
    for(let i = 0; i < arr.length; i++) {
        if(arr[i] < current) {
            left.push(arr[i])  //放在左边
        } else {
            right.push(arr[i]) //放在右边
        }
    }
    return quickSort(left).concat(current,quickSort(right));
}
```
- 希尔排序：不定步数的插入排序，插入排序

- 口诀: 插冒归基稳定，快选堆希不稳定

<img width="600" src="./images/interview/1.png">

稳定性： 同大小情况下是否可能会被交换位置, 虚拟dom的diff，不稳定性会导致重新渲染；

### 4. 递归运用(斐波那契数列)： 爬楼梯问题

初始在第一级，到第一级有1种方法(s(1) = 1)，到第二级也只有一种方法(s(2) = 1)， 第三级(s(3) = s(1) + s(2))

```js
function cStairs(n) {
    if(n === 1 || n === 2) {
        return 1;
    } else {
        return cStairs(n-1) + cStairs(n-2)
    }
}
```
### 5. 数据树
	- 二叉树 ： 最多只有两个子节点
		- 二叉查找树 ：小值在左，大值在右

### 6. 天平找次品

## Webpack (待补充)

### 原理
### Loader

- loader-utils: 编写 loader 时官方提供的工具函数包
- 同步与异步: return / async
- 处理二进制： module.exports.raw = true;
- ResolveLoader: modules: ['node_modules','./loaders/']

### Plugin

- 启动时初始化插件实例，进行事件的监听，传入 Compiler
- Compiler: 包含了 Webpack 环境所有的的配置信息，代表了整个 Webpack 从启动到关闭的生命周期
- Compilation: 包含了当前的模块资源、编译生成资源、变化的文件等，只是代表了一次新的编译

## Hybrid 与 Webview (待补充)

- webview 加载过程
- hybrid app 
- bridge 原理

## 项目优化 (待补充)

- 首屏渲染优化
- 用户体验优化
- webpack性能优化

## 结语

😂。不知道看到此的各位看官作何感想~反正我当时是觉得: 'shit! 复习真痛苦，什么都不会，要看的知识点无穷无尽'。不过为了工作，还是得沉下心来慢慢啃。

其实在面试中，很多领域并没有真正的答案，能回答到什么样的深度，还是得靠自己真正的去使用和研究。知识面的广度与深度应该并行，尽量的拓张自己的领域，至少都有些基础性的了解，可以同面试官唠嗑两句，然后在自己喜欢的领域，又有着足够深入的研究，让面试官觉得你是这方面的专家。

知识大纲还需要不断的完善和修正，也希望大家能一起参与进来。~~在编写的时候，其实也是对自己的归纳和总结。~~😉