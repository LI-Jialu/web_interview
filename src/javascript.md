

**Q:** JavaScript 中 `null` 和 `undefined` 的区别? 
**难度:**  &#x2B50;
<details>
    <summary> <span style='font-weight:bold'> A:</span> </summary>

null用来表示空值，undefined用来表示不存在

参考：https://www.jianshu.com/p/6ac1397e944c

</details>

---

**Q:** JavaScript 中 `typeof` 和 `instanceof` 的区别? 
**难度:**  &#x2B50;
<details>
    <summary> <span style='font-weight:bold'> A:</span> </summary>

* `typeof` 会把数组、对象、null都会被判断为object，其他判断都正确。 
```JS
console.log(typeof 2);               // number
console.log(typeof true);            // boolean
console.log(typeof 'str');           // string
console.log(typeof []);              // object    
console.log(typeof function(){});    // function
console.log(typeof {});              // object
console.log(typeof undefined);       // undefined
console.log(typeof null);            // object
```
* `instanceof` 只能正确判断引用数据类型，而不能判断基本数据类型。其内部运行机制是判断在其原型链中能否找到该类型的原型。
```JS
console.log(2 instanceof Number);                    // false
console.log(true instanceof Boolean);                // false 
console.log('str' instanceof String);                // false 
 
console.log([] instanceof Array);                    // true
console.log(function(){} instanceof Function);       // true
console.log({} instanceof Object);                   // true
```

参考：https://juejin.cn/post/6940945178899251230#heading-3

</details>

---

**Q:** JavaScript 中 `==` 和 `===` 的区别? 
**难度:**  &#x2B50;
<details>
    <summary> <span style='font-weight:bold'> A:</span> </summary>


* ==操作符会先将两边的值进行强制类型转换再比较是否相等，而===操作符不会进行类型转换。
* ==操作符只要求比较两个值是否相等，而===操作符不仅要求值相等，而且要求类型相同。
* 由于==和!=带来的隐式类型转换规则非常繁琐，以及为了避免混淆数据类型导致的 bug，推荐使用===操作符和!==操作符。
```JS
// true
55 == '55'
// false
55 === '55'
```

```JS
// true
null == undefined
// false
null === undefined
```


参考：https://www.jianshu.com/p/6ac1397e944c

</details>

---

**Q:** JavaScript 中为什么 `0.1+0.2 ! == 0.3`, 如何让其相等 ? 
**难度:**  &#x2B50;
<details>
    <summary> <span style='font-weight:bold'> A:</span> </summary>

过分简单的回答： 
```JS
(n1 + n2).toFixed(2) // 注意，toFixed为四舍五入
```
在 JavaScript 中只有一种数字类型：Number，它的实现遵循IEEE 754标准，使用64位固定长度来表示，也就是标准的double双精度浮点数。在二进制科学表示法中，双精度浮点数的小数部分最多只能保留52位，再加上前面的1，其实就是保留53位有效数字，剩余的需要舍去，遵从“0舍1入”的原则。
根据这个原则，0.1和0.2的二进制数相加，再转化为十进制数就是：0.30000000000000004

正确回答： 
```JS
function numberepsilon(arg1,arg2){                   
  return Math.abs(arg1 - arg2) < Number.EPSILON;        
}        

console.log(numberepsilon(0.1 + 0.2, 0.3)); // true
```

参考：https://juejin.cn/post/6940945178899251230

</details>

---


**Q:** 简单介绍和写一个JavaScript 中闭包? 
**难度:**  &#x2B50;&#x2B50;
<details>
    <summary> <span style='font-weight:bold'> A:</span> </summary>


Javascript语言特有的"链式作用域"结构（chain scope），子对象会一级一级地向上寻找所有父对象的变量。所以，父对象的所有变量，对子对象都是可见的，反之则不成立。

```JS
　function f1(){

　　　　var n=999;

　　　　function f2(){
　　　　　　alert(n);
　　　　}

　　　　return f2();

　　}

　　var result=f1();

　　result(); // 999
```
代码中的f2函数，就是闭包，简单理解为能够读取其他函数内部变量的函数。
因为f2可以读取f1中的局部变量，把f2作为返回值，就可以在f1外部读取它的内部变量。 

参考：https://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html

</details>

---
