
## 关于浏览器环境
### JavaScript代码嵌入网页的方法
JavaScript只有嵌入到网页才能在浏览器端运行，网页中嵌入javascript具有四种方法：

* <script>标签：代码嵌入网页
* <script>标签：加载外部脚本
* 事件属性：代码写入HTML元素的事件处理属性，比如onclick或者onmouseover
* URL协议：URL支持以javascript:协议的方式，执行JavaScript代码

后两种方法用得很少，常用的是前两种方法。由于内容（HTML代码）和行为代码（JavaScript）应该分离，所以第一种方法应当谨慎使用。

 转自：http://javascript.ruanyifeng.com/bom/engine.html
