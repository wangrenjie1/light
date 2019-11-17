# BFC IFC FFC（Flex Format Context） GFC(Grid) KFC 概念

## 如何触发BFC ？

1. 根元素 说白了 <html></html> 
2. float不为none
3. position为absolute或者fixed
4. display为inline-block,table-cell,table-caption,flex,inline-flex
5. overflow不为visiable

## BFC的作用

1. 自适应两栏布局
2. 清除内部浮动，取消父元素高度塌陷的问题
3. 防止margin 会重叠

## IFC

1. 高度由内容的实际高度决定
2. 垂直方向的 padding和margin不起作用
3. inline-level box一般左右都贴紧整个IFC，但是会因为float元素而扰乱。float元素会位于IFC与与line box之间，使得line box宽度缩短？？？？不理解啥意思
4. IFC中不能有块级元素
5. text-align 水平居中，  
6. vertical-align:middle 经典用法 [见demo](./demo1.html)

## FFC

### 盒元素

1. flex-direction属性决定主轴的方向（即项目的排列方向）。
2. flex-wrap默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行
3. flex-flow == flex-direction + flex-wrap

### 盒内元素 属性都是 自相残杀 盒内的元素相互比较的

1. order
2. flex-grow 放大比例 就是把空余的地方也给占满
3. flex-shrink 缩小比例 地方不够了 就变小 
4. flex-basis 就是这个带这个元素的属性有个基本保障 放大缩小之前先满足他的条件
5. flex = flex-grow + flex-shrink + flex-basis

## KFC

肯德基（KentuckyFried Chicken，肯塔基州炸鸡），简称KFC，是美国跨国连锁餐厅之一，也是世界第二大速食及最大炸鸡连锁企业，1952年由创始人哈兰·山德士（Colonel Harland Sanders）创建，主要出售炸鸡、汉堡、薯条、盖饭、蛋挞、汽水等高热量快餐食品。
