# Vuex


**Q:** vuex的流程 
**难度:**  &#x2B50;
<details>
    <summary> <span style='font-weight:bold'>A:</span> </summary>


页面通过mapAction异步提交事件到action。action通过commit把对应参数同步提交到mutation，mutation会修改state中对应的值。最后通过getter把对应值跑出去，在页面的计算属性中，通过，mapGetter来动态获取state中的值
参考： https://zhuanlan.zhihu.com/p/163283018
</details>

--- 

**Q:** 每个 vue 应用可以有几个 store 对象？
**难度:**  &#x2B50;
<details>
    <summary> <span style='font-weight:bold'>A:</span> </summary>

一个
参考： https://www.cnblogs.com/qduanxq/p/15099684.html
</details>

--- 

**Q:** 怎么改变store中的状态？ 
**难度:**  &#x2B50;
<details>
    <summary> <span style='font-weight:bold'>A:</span> </summary>


不能直接改变store中的状态。改变store中的状态的唯一途径是提交(commit)mutations。这样使
得我们可以方便地跟踪每一个状态的变化。
参考： https://www.cnblogs.com/qduanxq/p/15099684.html
</details>

--- 


**Q:** 解释store的五种属性： State , Getter , Mutation , Action , Module (就是mapAction)
**难度:**  &#x2B50;&#x2B50;
<details>
    <summary> <span style='font-weight:bold'>A:</span> </summary>


* modules：模块化store，使得结构非常清晰，方便管理
* state：vuex的基本数据，用来存储变量
* getter：从基本数据(state)派生的数据，相当于state的计算属性
* mutation：更改状态的逻辑，同步操作
* action：提交mutation，异步操作

```JS
const store = new Vuex.Store({
  state: {
    // 存放状态
  },
  getters: {
    // state的计算属性
  },
  mutations: {
    // 更改state中状态的逻辑，同步操作
  },
  actions: {
    // 提交mutation，异步操作
  },
  // 如果将store分成一个个的模块的话，则需要用到modules。
   //然后在每一个module中写state, getters, mutations, actions等。
  modules: {
    a: moduleA,
    b: moduleB,
    // ...
  }
```
参考： https://www.cnblogs.com/qduanxq/p/15099684.html
</details>

--- 
**Q:** Vue.js中ajax请求代码应该写在组件的methods中还是vuex的actions中？

**难度:**  &#x2B50;&#x2B50;
<details>
    <summary> <span style='font-weight:bold'>A:</span> </summary>


一、如果请求来的数据是不是要被其他组件公用，仅仅在请求的组件内使用，就不需要放入vuex 的state里。

二、如果被其他地方复用，这个很大几率上是需要的，如果需要，请将请求放入action里，方便复用，并包装成promise返回，在调用处用async await处理返回的数据。如果不要复用这个请求，那么直接写在vue文件里很方便

参考： https://zhuanlan.zhihu.com/p/163283018
</details>

---

**Q:** dispatch和commit来调用mutations的相同与不同? 

**难度:**  &#x2B50;&#x2B50;&#x2B50;
<details>
    <summary> <span style='font-weight:bold'>A:</span> </summary>

相同： 
commit 和 dispatch 两个方法都是传值给vuex的mutation改变state

不同： 
state和getters在组件中的computed中使用, mutations 和 actions 在组件的methods中使用, dispatch在actions中.

commit: 用来提交当前模块的mutations， mutations修改state,
dispatch: 用来提交当前模块的actions(actions可以提交mutations,可以进行异步操作). 如果修改完还想做其他事情就用actions比较方便(then后执行想要做的事情)`this.$store.dispatch().then()`


commit: 同步操作
存储 `this.$store.commit('changeValue',name)`
取值 `this.$store.state.changeValue`

dispatch: 异步操作
存储 `this.$store.dispatch('getlists',name)`
取值 `this.$store.getters.getlists`

参考： [稀土掘金](https://juejin.cn/post/6972704942695907358)

</details>



前端持久化存储 localStorage、sessionStorage、Cookie 解释与区别？ 
