### 事件委托
  原理： 利用事件的冒泡机制，只指定一个事件处理程序，就可以管理某一类型的所有事件
  因为绑定事件，是需要不断的与dom操作，访问dom的次数也就越多，就会导致页面的重绘与重排，延长整个页面的交互时间。而且每个事件都是一个函数，就会占用内存，函数一多，内存占用也就是越多
  优点
  
  * 使用冒泡的机制减少对dom的操作
  * 给未来的子元素绑定事件

  缺点
  
