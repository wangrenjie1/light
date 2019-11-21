## 如何理解 display 的属性值

##### 作者：hauk0101
##### 时间：2019-11-16

#### 问题来源

> 问题来源于某次在群里的讨论，关于 `text-align:center` 的使用场景，是否必须要与 `display:inline` 配合使用？于是展开了与 `display` 相关的更为深入的理解

* `display ` 属性的三个值  `block` `inline` `inline-block` 的理解 （[查看demo](https://github.com/wangrenjie1/toutiao_four_men/blob/master/hauk0101/demos/css/demo-css-display.html)）
* `text-align:center` 在 `block` `inline` `inline-block` 中的不同场景 （[查看demo](https://github.com/wangrenjie1/toutiao_four_men/blob/master/hauk0101/demos/css/demo-css-display.html)）
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

* `text-align:center` 在 `block` `inline` `inline-block` 中的不同场景
    * 目的是为了让子元素水平居中      
    * 父元素设置 `display:inline` `display:inline-block` 与 `text-align:center` 并不会使子元素水平居中
    * 父元素设置 `display:block` `text-align:center` ，子元素设置不同的 `display:inline` 、`display:inline-block` 、`display:block` 的属性值的影响
        * 子元素是block,则子元素的文字相对子元素居中，而子元素并不会相对父元素居中
        * 子元素是inline-block，则子元素的文字不仅相对子元素居中，而且子元素相对父元素也居中
        * 子元素是inline，则子元素的文字无法撑起子元素，子元素的宽高就是文字的宽高，而子元素是相对父元素居中的

* `display` 的属性值枚举及相关举例
    * 可以将 display 分为 7 大类，外部值、内部值、列表值、属性值、显示值、混合值、全局值
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
            * 说明：采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。
            * 容器相关属性：
                * `flex-direction: row | row-reverse | column | column-reverse` :决定主轴方向（即子元素的排列方向）
                * `flex-wrap: nowrap | wrap | wrap-reverse` :定义换行情况（默认情况下，项目都排列在一条轴线上，但有可能一条轴线排不下）
                * `flex-flow: <flex-direction> || <flex-wrap>`:`flex-direction`和`flex-wrap`的简写，默认`row nowrap`
                * `justify-content: start | end | flex-start | flex-end | center | left | right | space-between | space-around | space-evenly | stretch | safe | unsafe | baseline | first baseline | last baseline`: 定义项目在主轴上的对齐方式
                * `align-items: flex-start | flex-end | center | baseline | stretch`:定义在交叉轴上的对齐方式
                *  `align-content: flex-start | flex-end | center | space-between | space-around | stretch`:定义多根轴线的对齐方式（如果项目只有一根轴线，该属性不起作用。所以，容器必须设置`flex-wrap`）
            * 项目相关属性：
                * `order: <integer>`: 属性定义项目的排序顺序，数值越小，排列越靠前，默认为0
                * `flex-grow: <number>`: 属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大
                * `flex-shrink: <number>`: 属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
                * `flex-basis: <length> | auto`: 属性定义了在分配多余空间之前，项目占据的主轴空间。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小
                * `flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]`: 属性是 `flex-grow`,` flex-shrink` 和`flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选
                * `align-self: auto | flex-start | flex-end | center | baseline | stretch` : 属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`
            * `flex:1`:表示的是`flex-grow`,` flex-shrink` 和`flex-basis`的简写，其值表示 `flex-grow: 1;flex-shrink: 1;flex-basis: 0%`，即项目不占用主轴的空间。
        * display:grid
            * 说明：即网格布局
                * grid 引入了一个全新的单位 `fr`，它是 `fraction(分数)` 的缩写
                * 斜杠操作符，表示的是起始位置和结束为止，如`3/4`，不是四分之三的意思，表示的是一个元素从第3行开始，到第4行结束，但又不包括第4行
            * 相关属性：`grid, grid-column-start, grid-column-end, grid-row-start, grid-row-end, grid-template, grid-template-columns, grid-template-rows, grid-template-areas, grid-gap, grid-column-gap, grid-row-gap, grid-auto-columns, grid-auto-rows, grid-auto-flow, grid-column, grid-row`
        * display: flow
            * 说明：实验室阶段，Chorme 不支持，不推荐使用
            * 英文说明：If its outer display type is inline or run-in, and it is participating in a block or inline formatting context, then it generates an inline box. Otherwise it generates a block container box.
        * display: flow-root
            * 说明：它可以撑起被 `float` 掉的块级元素的高度
        * display: ruby
            * 说明：仅 Firefox 支持，类似于给汉字添加拼音
        * display: subgrid
            * 说明：具有争议的属性，即网格中嵌套互不影响的小网格
    * 列表值
        * display: list-item
            * 说明：实现类似`<ul><li>`效果的属性
    * 属性值
        * 说明：可参考 `display:table` 的相关属性
        * 还有包括 `display:ruby` 的相关属性
    * 显示值
        * `display: contents`: 它让子元素拥有和父元素一样的布局方式
        * `display: none` : 将元素设置为none的时候既不会占据空间，也无法显示，相当于该元素不存在。该属性可以用来改善重排与重绘，同时我也经常用它来做模态窗等效果
    * 混合值
        * `display: inline-block`: 详见上述内容
        * `display: inline-table`: 在行内显示一个表格
        * `display: inline-flex`: 在行内进行弹性布局
        * `display: inline-grid`: 在行内进行网格布局
    * 全局值
        * `display: inherit` : 继承父元素的 display 属性
        * `display: initial` : 不管父元素如何设定，恢复到浏览器最初始的 display 属性
        * `display: unset` : 混合了 `inherit``initial` ，如何父元素设值了就用父元素的，如果父元素没设置，就用浏览器的缺省设定。
#### 参考文章

* [display-MDN文档](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
* [CSS display 属性详解](https://zhanfang.github.io/2016/07/22/display%E5%B1%9E%E6%80%A7%E8%AF%A6%E8%A7%A3/)
* [display的32种写法](https://segmentfault.com/a/1190000012833458)
* [CSS之使用display:inline-block来布局](https://www.cnblogs.com/Ry-yuan/p/6848197.html)
* [基于CSS属性display:table的表格布局的使用](https://www.cnblogs.com/haoqipeng/p/html-display-table.html)
* [Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
* [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

## 浏览知识共享许可协议

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />本作品采用<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">知识共享署名-相同方式共享 4.0 国际许可协议</a>进行许可。