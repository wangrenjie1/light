## 如何理解 Object 

##### 作者：hauk0101
##### 时间：2019-11-16

#### 问题来源

> 问题来源于群里某次讨论，关于 Object.keys() 和 Object.values() 的妙用，区别，联系？

* Object.keys() 理解
* Object.values() 理解
* Object 的拓展

#### 问题总结

* Object.keys() 理解
    * 说明：该方法会返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和使用 `for...in` 循环遍历该对象时返回的顺序一致。

* Object.values() 理解
    * 说明：该方法返回一个给定对象自身的所有可枚举属性值的数组，值的顺序与使用 `for...in` 循环的顺序相同( 区别在于 `for-in` 循环枚举原型链中的属性 )

* Object 的拓展


#### 参考文章

* [Object-MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)


## 浏览知识共享许可协议

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />本作品采用<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">知识共享署名-相同方式共享 4.0 国际许可协议</a>进行许可。