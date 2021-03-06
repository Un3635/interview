### 页面渲染的流程
  1. 解析html生成dom树
  1. 解析css生成cssom规则树
  1. 将dom树和css规则树合并在一起生成渲染树
  1. 遍历渲染树开始布局，就算每个节点的位置大小
  1. 将渲染树的每个节点绘制在屏幕上
  *重点：上述的过程是逐步完成，但是渲染引擎会尽早的将内容呈现在屏幕上，并不会等所有html都解析完成，再去构建和布局,是解析完一部分渲染一部分*
  * 减少DNS的查询，css 和 js的顺序

  * 几个概念
    * reflow: 浏览器花时间去渲染，当发现某个部分发生了变化，就需要倒回去重新渲染
      * 原因
      1. 页面初始化的时候
      1. 操作DOM的时候
      1. 某些元素的尺寸变了
      1. 如果css的属性发现变化
    * repaint: 如果只是改变了某个元素的背景，文字颜色，不影响周围颜色的布局，和内部布局的属性，将引起浏览器的重绘
    *回流比重绘更费时间，所以在实际开发中要尽量减少回流*
    * 减少reflow/repaint
      1. 不要一条一条地修改 DOM 的样式。与其这样，还不如预先定义好 css 的 class，然后修改 DOM 的 className。 
      1. 不要把 DOM 结点的属性值放在一个循环里当成循环里的变量。 
      1. 为动画的 HTML 元件使用 fixed 或 absoult 的 position，那么修改他们的 CSS 是不会 reflow 的。 
      1. 千万不要使用 table 布局。因为可能很小的一个小改动会造成整个 table 的重新布局。

###　编写css时注意事项
1. dom深度尽量浅。
1. 减少inline javascript、css的数量。
1. 使用现代合法的css属性。
1. 不要为id选择器指定类名或是标签，因为id可以唯一确定一个元素。
1. 避免后代选择符，尽量使用子选择符。原因：子元素匹配符的概率要大于后代元素匹配符。后代选择符;#tp p{} 子选择符：#tp>p{}
1. 避免使用通配符，举一个例子，.mod .hd *{font-size:14px;} 根据匹配顺序,将首先匹配通配符,也就是说先匹配出通配符,然后匹配.hd（就是要对dom树上的所有节点进行遍历他的父级元素）,然后匹配.mod,这样的性能耗费可想而知.

### 编写javascript的加载和执行的特点
1. 载入后马上执行； 
1. 执行时会阻塞页面后续的内容（包括页面的渲染、其它资源的下载）。原因：因为浏览器需要一个稳定的DOM树结构，而JS中很有可能有 代码直接改变了DOM树结构，比如使用 document.write 或 appendChild,甚至是直接使用的location.href进行跳转，浏览器为了防止出现JS修 改DOM树，需要重新构建DOM树的情况，所以 就会阻塞其他的下载和呈现。

### 减低页面加载时间的
  1. 图片
    * 图像格式的选择（GIF:提供的色彩较少）
    * 标明图片的高度，和宽度（如果图片没有标明高度，需要边下载边计算的图片的高度，然后不断的进行调整页面）
    1. 优化css
    1. 网址后面加/ 
    1. 减少http的请求
      - 图片换成精灵图
      - 合并脚本和样式表
      - 图片使用base64编码减少页面请求数
    1. 将外部脚本置底
### 性能优化， 体验优化
    1. 减少dom的操作
    1. 将css放在head中
    1. 减少dom操作的原因
       因为绑定事件，是需要不断的与dom操作，访问dom的次数也就越多，就会导致页面的重绘与重排，延长整个页面的交互时间。
### 各种主流框架之间的区别
### 浏览器的缓存
### http的keep-alive


    






