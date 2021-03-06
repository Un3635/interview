## 五大布局
1. 单列布局(上中下一栏式)，有以下两种情况
    - header,content 和 footer 等宽的单列布局

    - header 与 footer 等宽,content 略窄的单列布局
    
    *代码见 css布局/单列布局.html*
1. 左右两栏式
   - 第一种方式 **浮动+普通流**
    步骤： 
      1. 设置父级的宽度，居中
      1. 设置左边的宽度，定位使用float
      1. 右边只设置高度就可以，不需要设置宽度
      
      *代码见 css布局/左右两栏式布局1.html*
   - 第二种方式 **纯浮动式， 需要注意的地方，父级的高度会为0**
      *代码见 css布局/左右两栏式布局2.html*
   - 第三种方式 **绝对定位的方式** 
      *代码见 css布局/左右两栏式布局3.html*

1. 两列自适应布局(两列自适应布局是指一列由内容撑开，另一列撑满剩余宽度的布局方式)
    - float + overflow:hidden 

      ``.left {float: left;} .right {overflow:hidden}``
    - flexBox 
    
        设置父级 ``display:flex`` 和 ``.right {flex:1}``
    - Grid布局

1. 三栏布局 **特征：中间列自适应宽度，旁边两侧固定宽度**
    - 第一种方式 *左右两侧是float布局 + 普通流*

      *代码见  css布局/三栏式布局-float.html*
    - 第二种方式-双飞翼布局 *三列军师float布局*

      比圣杯布局更优化一点

      *代码见  css布局/三栏式布局-双飞翼布局*
    - 第三种方式 - 圣杯布局 

      优点：dom结构优先加载
      缺点：
        
        1. 主体main的宽度不能小于left宽度，否则两侧的div会掉到下一行
        1. 其中一列的内容高度拉长，其他两列的背景并不会自动填充

1. 等高列布局

    是指在子元素在父元素种高度相等的布局，等高布局的包括伪等高和真等高，伪等高是指看上去等高而已，真登高是指实实在在的等高
    
    - 第一种方式，利用背景图片进行布局

        优点：兼容性强，简单，不需要太多的css样式
        缺点：此方法不适合流体布局
    - 利用padding + 负margin
       
       在所有的列中加入如下样式
       ```css
        #left,
        #right,
        #main {
            padding-bottom: 10000px;
            margin-bottom: -10000px;
        }
        <!-- 并且父级需要加入溢出隐藏 -->
        .wrap {
            overflow:hidden;
        }
       ```

1. 粘连布局，也就是sticker footer 布局
    步骤:

    1. 设置html, body的高度是 100%``html, body{height: 100%}``, 其中一定要设置html的高度，如果只设置body的高度而不设置html的高度，则不回成功；
    1. 设置wrap的最小高度``.wrap {min-height: 100%}``,其中若需要兼容ie6，则需添加
    ```css
    .wrap {
        min-height: 100%;
        height: auto !important; /* 如果你不需要考虑IE6，则可以把这行与下一行代码删除 */
        height: 100%;
    }
    ```
    1. 设置wrap子元素的css样式,添加padding-bottom的样式 ``.main{padding-bottom: footer的高度}``
    1. 设置footer的样式 ``.footer {height: footer的高度; margin-top: 负的footer的高度}``
    

