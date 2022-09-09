# Vue2



**Q:** vue组件间如何进行通讯？ 
**难度:**  &#x2B50;&#x2B50;
<details>
    <summary> <span style='font-weight:bold'>A:</span> </summary>


方法一：props/$emit
父组件A 向 子组件B 传递数据 通过props的方法
子组件B 向 父组件A 发送数据 通过emit


方法二：$parent/$children与ref
子实例可以用this.$parent访问父实例
子实例被推入父实例的$children
ref：如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例

$emit/$on
这个方法可用于父子、隔代、兄弟组件通信
这种方式是通过一个类似App.vue的实例作为一个模块的事件中心，用它来触发事件和监听事件，从而实现任何组件间的通信，包括父子、隔代、兄弟组件

参考： https://segmentfault.com/a/1190000022083517
</details>

---

