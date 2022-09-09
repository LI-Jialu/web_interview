# Axios
**Q**: axios为什么既能在浏览器环境运行又能在服务器(node)环境运行？
**难度:**  &#x2B50;&#x2B50;&#x2B50;
<details>
    <summary> <span style='font-weight:bold'> A:</span> </summary>

     
axios在浏览器端使用XMLHttpRequest对象发送ajax请求；在node环境使用http对象发送ajax请求。
  ```js
  var defaults.adapter = getDefaultAdapter();
function getDefaultAdapter () {
	var adapter;
    if (typeof XMLHttpRequest !== 'undefined') {
    	// 浏览器环境
        adapter = require('./adapter/xhr');
    } else if (typeof process !== 'undefined') {
    	// node环境
        adapter = require('./adapter/http');
    }
   return adapter;
}
  ```
上面几行代码，可以看出：XMLHttpRequest 是一个 API，它为客户端提供了在客户端和服务器之间传输数据的功能；process 对象是一个 global （全局变量），提供有关信息，控制当前 Node.js 进程。原来作者是通过判断XMLHttpRequest和process这两个全局变量来判断程序的运行环境的，从而在不同的环境提供不同的http请求模块，实现客户端和服务端程序的兼容。

参考：https://juejin.cn/post/6844904008872624142
</details>

# Axios
**Q**: axios相比原生ajax的优点
**难度:**  &#x2B50;&#x2B50;&#x2B50;
<details>
    <summary> <span style='font-weight:bold'> A:</span> </summary>

     
本身是针对MVC的编程,不符合现在前端MVVM的浪潮
基于原生的XHR开发，XHR本身的架构不清晰。
JQuery整个项目太大，单纯使用ajax却要引入整个JQuery非常的不合理（采取个性化打包的方案又不能享受CDN服务）不符合关注分离（Separation of Concerns）的原则配置和调用方式非常混乱，而且基于事件的异步模型不友好。

参考：https://juejin.cn/post/6844904008872624142
</details>