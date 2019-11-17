<!--
 * @Author: 13261909995@163.com
 * @Date: 2019-11-14 10:37:58
 * @LastEditTime: 2019-11-15 20:16:40
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
- 