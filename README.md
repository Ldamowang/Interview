# async和defer区别

1.默认引用 script:<script type="text/javascript" src="x.min.js"></script>

当浏览器遇到 script 标签时，文档的解析将停止，并立即下载并执行脚本，脚本执行完毕后将继续解析文档。

2.async模式 <script type="text/javascript" src="x.min.js" async="async"></script>

当浏览器遇到 script 标签时，文档的解析不会停止，其他线程将下载脚本，脚本下载完成后开始执行脚本，脚本执行的过程中文档将停止解析，直到脚本执行完毕。

3.defer模式 <script type="text/javascript" src="x.min.js" defer="defer"></script>

当浏览器遇到 script 标签时，文档的解析不会停止，其他线程将下载脚本，待到文档解析完成，脚本才会执行。

所以async和defer的最主要的区别就是async是异步下载并立即执行，然后文档继续解析，defer是异步加载后解析文档，然后再执行脚本





# new操作符干了什么

1.隐式的创建了一个对象

2.将构造函数的this指向该对象

3.执行构造函数函数体，修改this，给对象添加属性和方法

4.返回新对象





# 原型的理解

1.js规定，每一个构造函数内部都有一个prototype属性，指向另外一个对象，我们把该对象称为原型对象

2.在js中，原型也是一个对象，通过原型可以实现对象的属性继承，js的对象中包含了一个prototype 内部属性，这个属性所对应的就是该对象的原型

3.prototype属性作为对象的内部属性，是不能直接访问的，所以为了方便查看一个对象的原型，firefox和chrome内核的js引擎提供了一个proto这个非标准的访问器

4.原型的主要作用就是为了实现继承和扩展对象



# 原型链

1.js原型：每个对象都会在其内部初始化一个属性，就是prototype（原型）

2.原型链：

​	当访问对象的某个属性时，会先在该对象的属性上找，如果找不到，就会去该对象的原型上查找。如果还没找到，就会去原型的原型上查找，一直找到null为止，如果都没有找到，就会返回undefined，这种链式的查找机制就被称为原型链



# 路由守卫

1.全局共享的

beforeEach,beforeResolve,afterEach

2.组件内部

beforeRouteEnter,beforeRouteUpdate,beforeRouteLeave



# 防抖和节流

防抖：一段时间内只执行最新触发的 ，如果在这段时间内重复执行，则会执行最新的取消上次的执行

节流：在一段时间内只会执行一次，执行结束之后才会执行新的事件





# 重绘和重排

重绘：当一个元素外观发生变化，但没有改变布局

重排：当DOM的变化影响了元素的几何信息



# 盒子模型

标准盒子模型：content+padding+border+margin

怪异盒子模型：content+margin



# js数据类型

基本数据类型：string，number，null，undefined，boolean，symbol

引用数据类型：object（array，function，object）



# cookie，sessionStorage，localStorage区别

cookie内存较小，4k左右

sessionStorage，localStorage较大5M左右

sessionStorage除非页面关闭才会被清理

localStorage长期存储在浏览器当中除非手动清理

**cookie**：

- 是网站为了标识用户身份而存储在本地终端上的数据（通常是经过加密的）；
- 如果不给`cookie`设置过期时间，则表示这个`cookie`的生命周期为浏览器会话期间，只要关闭浏览器窗口，`cookie`就消失了；

`cookie`数据始终在同源`http`请求中携带（也就是说`cookie`在浏览器和服务器之间来回传递），而`sessionStorage`和`localStorage`不会主动把数据发送给服务器；

**存储大小限制**：

- `cookie`：不能超过 `4KB`；
- `sessionStorage` 和 `localStorage`：虽然也有存储限制，但相比`cookie`要大得多，可达到 `5M` 甚至更大；

**数据的有效期不同**：

- `cookie`：只在设置的过期时间之前有效，即使关闭页面或浏览器也依然有效；
- `sessionStorage`：只在当前页面没有关闭之前有效；
- `localStorage`：始终有效，即使关闭窗口和浏览器也依然有效，除非手动清除；

**作用域不同**：

- `cookie`：在所有同源窗口中都是共享的；
- `sessionStorage`：只在当前窗口中共享；
- `localStorage`：在所有同源窗口中共享；

`cookie`并不一定都能通过js获取到，如果设置了`httponly`，是获取不到的；



# css选择器

!important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性



# MVVM

MVVM：model-view-viewModel

model：数据模型

view：视图组件（UI）

view-model：是model和view之间的桥梁，数据会自动的绑定在viewModel层并渲染在页面中，视图发生变化时会通知viewModel层更新数据，数据驱动视图改变



# vue底层原理

vue.js是采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter和getter，在数据变动时发布消息给订阅者，触发相应的监听回调



# keep-alive生命周期

keep-alive作用：缓存不活动的组件实例，能在组件切换过程中将状态保留在内存中，防止重复渲染DOM。

生命周期：

activated
deactivated