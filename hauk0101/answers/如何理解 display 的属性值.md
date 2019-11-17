## 如何理解 display 的属性值

##### 作者：hauk0101
##### 时间：2019-11-16

#### 问题来源

> 问题来源于某次在群里的讨论，关于 `text-align:center` 的使用场景，是否必须要与 `display:inline` 配合使用？于是展开了与 `display` 相关的更为深入的理解

* `display ` 属性的三个值  `block` `inline` `inline-block` 的理解
* `text-align:center` 在 `block` `inline` `inline-block` 中的不同场景
* `display` 的属性值枚举及相关举例


#### 问题总结

* `display ` 属性的三个值  `block` `inline` `inline-block` 的理解
    * `display:block` 的特点
        * 可以使元素变成块级元素，独占一行，在不设置自己的宽度的情况下，块级元素会默认填满父级元素的宽度
        * 能够改变元素的 height , width 值
        * 可以设置 padding , margin 的各个属性值， top , left , bottom , right 都能够产生边距效果
        * 元素后的内容自动换行
    *  `display:inline` 的特点
        * 使元素变成行内元素，拥有行内元素的特性，即可以与其他行内元素共享一行，不会独占一行
        * 不能更改元素的 height , width 的值，大小由内容撑开
        * 可以使用 padding 上下左右都有效，margin 只有 left 和 right 产生边距效果，但是 top 和 bottom 就不行
    * `display:inline-block` 的特点
        * 结合了 inline 和 block 的一些特点，结合了上述 inline 的第1个特点和 block 的第2、3个特点
        * 用通俗的话讲，就是不独占一行的块级元素
        * 存在间隙问题，间隙是 4 px ，这个问题的原因是换行引起的，因为在写标签时通常会在标签结束符后输入回车而产生回车符，相当于是空白符
            * 去除的办法是将父元素设置 font-size:0
            * 删除回车符，但是会导致 html 中的代码很长，不易阅读

* `text-align:center` 在 `block` `inline` `inline-block` 中的不同场景，详细 demo 请见项目的 `demos/css/demo-css-display.html`
    * 目的是为了让子元素水平居中      
    * 父元素设置 `display:inline` `display:inline-block` 与 `text-align:center` 并不会使子元素水平居中
    * 父元素设置 `display:block` `text-align:center` ，子元素设置不同的 `display:inline` 、`display:inline-block` 、`display:block` 的属性值的影响
        * 子元素是block,则子元素的文字相对子元素居中，而子元素并不会相对父元素居中
        * 子元素是inline-block，则子元素的文字不仅相对子元素居中，而且子元素相对父元素也居中
        * 子元素是inline，则子元素的文字无法撑起子元素，子元素的宽高就是文字的宽高，而子元素是相对父元素居中的

* `display` 的属性值枚举及相关举例
    * 可以将 display 分为 6 大类，外部值、内部值、列表值、属性值、显示值、混合值、全局值
    * 外部值（所谓外部值，就是说这些值只会直接影响一个元素的外部表现，而不影响元素里面的儿子级孙子级元素的表现）
        * display:block 
            * 说明：块级元素，独占一行，可设置宽高，可设置 margin 、padding 、top 、right 、bottom 、top
            * 举例：`<div>` `<h1>` - `<h6>` `<p>` `<form>` `<header>` `<footer>` `<section>` `<article>`
        * display:inline
            * 说明：行内元素，详情见上述
            * 举例：`<span>` `<a>` `<img>` `<b>` `<i>`
        * display:run-in
            * 说明：仅有 IE | Opera 支持，可以在父元素中用 `<span>` 元素设置 `font-size` 进行模拟实现
    * 内部值 （所谓内部值，主要是用来管束自己下属的儿子级元素的布局的，规定它们或者排成 S 形，或者排成 B 形）
        * display:table
            * 说明：将元素显示成 table 的样式，此元素会作为块级表格来显示（类似 `<table>`），表格前后带有换行符
            * 举例：`<table>`
            * 相关属性：
                * `display:table-row-group`:此元素会作为一个或多个行的分组来显示（类似 `<tbody>`）
                * `display:table-header-group`:此元素会作为一个或多个行的分组来显示（类似 `<thead>`）
                * `display:table-footer-group`:  此元素会作为一个或多个行的分组来显示（类似 `<tfoot>`）
                * `display:table-row`: 此元素会作为一个表格行显示（类似`<tr>`）
                * `display:table-column-group`:此元素会作为一个或多个列的分组来显示（类似 `<colgroup>`）
                * `display:table-column`: 此元素会作为一个单元格列显示（类似 `<col>`）
                * `display:table-cell`:此元素会作为一个表格单元格显示（类似 `<td>` 和` <th>`）
                * `display:table-caption`:此元素会作为一个表格标题显示（类似 `<caption>`）
        * display:flex
        * display:grid
        * display: flow
        * display: flow-root
        * display: ruby
        * display: subgrid
    * 列表值
        * display: list-item

#### 参考文章

* [display-MDN文档](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
* [CSS display 属性详解](https://zhanfang.github.io/2016/07/22/display%E5%B1%9E%E6%80%A7%E8%AF%A6%E8%A7%A3/)
* [display的32种写法](https://segmentfault.com/a/1190000012833458)
* [CSS之使用display:inline-block来布局](https://www.cnblogs.com/Ry-yuan/p/6848197.html)
* [基于CSS属性display:table的表格布局的使用](https://www.cnblogs.com/haoqipeng/p/html-display-table.html)


## 浏览知识共享许可协议

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />本作品采用<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">知识共享署名-相同方式共享 4.0 国际许可协议</a>进行许可。