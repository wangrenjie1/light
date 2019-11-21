<!--
 * @Author: 13261909995@163.com
 * @Date: 2019-11-14 10:37:58
 * @LastEditTime: 2019-11-17 16:30:43
 * @LastEditors: Please set LastEditors
 -->
## display 
- display属性指定了元素的显示类型，包含两类基础特性，用于指定元素怎样生成盒模型
- 外部显示类型：定义了元素怎样参与流式布局的处理
- 内部显示类型：定义了元素内部子元素的布局方式

#### 属性
- block: 块状显示，元素后加换行符
- inline：内联显示，元素后边删除换行符，可以多个内联元素并列显示
- inline-block: 行内块级元素，元素的内容以块状显示，可以和其他元素显示在同一行（只有这一类元素类型支持vertical-align属性）
- none：此元素不会显示
- list-item：将元素转换成列表，li的默认类型

#### display：none 和 visibility：hidden
- 相同点
    - 都能让元素不可见
- 不同点
    - display：none 会让元素从渲染树消失，渲染的时候不会占据空间
    - visibility：hidden 不会让元素从渲染书消失，渲染元素继续占据空间，只是内容不可见
    - display: none 是非继承属性，子孙节点消失是由于父元素从渲染树消失造成的，所以通过修改子孙节点属性无法显示
    - visibility: hidden 是继承属性，子孙节点消失由于继承hidden，通过设置visibility：visible，可以让子孙节点显示
    - 修改常规流中元素的display通常会造成文档重排，修改visibility属性只会造成元素的重绘
    - 读屏器不会读取display：none元素内容，会读取visibility：hidden元素内容

#### inline-block 元素间隙
- 间隙是由于换行或者回车导致的，只要把标签写成一行或者标签之间没有空格，就不会出现间隙
- 去除间隙的方法
```
.test span {
    display: inline-block;
    border: 1px solid red;
    font-size: 20px;
}
<div class="test">
    <span>test one</span>
    <span>test two</span>
</div>
1. 去掉元素中间的空格
<div class="test">
    <span>test one</span><span>test two</span>
</div>

2. 利用html注释，道理其实和去空格一样
<div class="test">
    <span>test one</span><!--
    --><span>test two</span>
</div>

3. 取消标签闭合
<div class="test">
    <span>test one
    <span>test two
</div>

4. 在父容器上使用font-size：0，消除间隙
.test {
    font-size: 0;
}
<div class="test">
    <span>test one</span>
    <span>test two</span>
</div>
```

#### inline-block 可能出现的错位问题
- 当两个块的内容高度不相同时，两个块就会错位
- 因为所有的内联块都有一个默认的属性：vertical-align：baseline，baseline是块中内容的底线，而内容高度不同，就会错位
- 解决方式：设置vertical-align的属性为top、middle、bottom中的一个
```
.test span {
    display: inline-block;
    border: 1px solid red;
    font-size: 20px;
    /* vertical-align: top; */  设置vertical-align属性
}
.test .span1 {
    width: 200px;
    height: 100px;
}
.test .span2 {
    width: 200px;
    height: 80px;
}
<div class="test">
    <span class="span1">test onetest onetest one</span>
    <span class="span2">test two</span>
</div>
```

#### flex 弹性布局
- 任何一个容器都可以指定为Flex布局，行内元素也可以使用flex布局，设置flex布局以后，子元素的float、clear、vertical-align属性都失效
- 容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做mian end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。项目默认沿主轴排列，单个项目占据的主轴空间叫做mian size，占据的交叉轴空间叫做cross size。
- 容器上有六个属性
    - flex-direction：决定主轴的方向（即项目的排列方向）
        - row（默认值）：主轴为水平方向，起点在左端
        - row-reverse： 主轴为水平方向，起点在右端
        - column：主轴为垂直方向，起点在上边
        - column-reverse：主轴为垂直方向，起点在下边
    - flex-wrap：定义容器中项目一条轴线排不下的时候，如何排列
        - nowrap：（默认）不换行，都排在一行，等比例压缩
        - wrap：换行，不压缩，第一行在上方
        - wrap-reverse：换行，不压缩，第一行在下方
    - flex-flow：该属性是flex-direction属性和flex-wrap属性的简写形式，默认值是 row nowrap
    - justify-content：定义了项目在主轴上的对齐方式
        - flex-start: (默认值)左对齐
        - flex-end：右对齐
        - center：剧中
        - space-betwwen：两端对齐，项目之间的间隔都相等
        - space-around：每个项目两侧的间隔相等，所以项目之间的间隔比项目与边框的间隔大一倍
    - align-items：定义项目在交叉轴上如何对齐
        - flex-start：交叉轴的起点对齐
        - flex-end：交叉轴的终点对齐
        - center：交叉轴的中点对齐
        - baseline：项目的第一行文字的基线对齐
        - stretch（默认值）：如果项目未设置高度或者设为auto，将沾满整个容器的高度
    - align-content：定义了多根轴线的对齐方式，如果只有一个轴线，改属性不起作用
        - flex-start：与交叉轴的起点对齐。
        - flex-end：与交叉轴的终点对齐。
        - center：与交叉轴的中点对齐。
        - space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
        - space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
        - stretch（默认值）：轴线占满整个交叉轴。
- 项目上的属性
    - order：定义项目的排列顺序。数值越小，排列越靠前，默认为0
    - flex-grow：定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大
    - flex-shrink： shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。负值对该属性无效
    - flex-basis：定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
    - flex：flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
    - align-self：允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。