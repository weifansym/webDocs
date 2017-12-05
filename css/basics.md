## CSS基础
### @规则
一个 at-rule 是一个CSS 语句，以at符号开头, '@' (U+0040 COMMERCIAL AT), 后跟一个标识符，并包括直到下一个分号的所有内容, ';' (U+003B SEMICOLON), 或下一个CSS块，以先到者为准。

下面是一些 @规则, 由它们的标示符指定, 每种规则都有不同的语法:

@charset, 定义样式表使用的字符集.
@import, 告诉 CSS 引擎引入一个外部样式表.
@namespace, 告诉 CSS 引擎必须考虑XML命名空间。
嵌套@规则, 是嵌套语句的子集,不仅可以作为样式表里的一个语句，也可以用在条件规则组里：
@media, 如果满足媒介查询的条件则条件规则组里的规则生效。
@page, 描述打印文档时布局的变化.
@font-face, 描述将下载的外部的字体。 
@keyframes, 描述 CSS 动画的中间步骤 . 
@supports, 如果满足给定条件则条件规则组里的规则生效。 
@document, 如果文档样式表满足给定条件则条件规则组里的规则生效。 (推延至 CSS Level 4 规范)

参考： https://developer.mozilla.org/zh-CN/docs/Web/CSS/At-rule
