# jQuery-v3.2.1-read
jQuery v3.2.1源码分析

在网上看到很多人都说jQuery已经out了，但流行的库只是因为它好用，而且符合业务上的需求才会选择它，你没可能在一个单单的页面上引用vue全家桶吧？

每个库都有它的优势，而jQuery只是一个时代的产物，jQuery当时流行的程度和用的人绝对比现在流行的MVVM库多。所以jQuery在前端的地位上是不可否决的。

我学前端的时候发现利用jQuery之后非常容易上手，用着用着就发现jQuery里面有这么多的方法，其他方法我都用不上。

我就想着假如我只要我想要的方法就好了，这样可以减小jQuery的体积而且不会代码冗余。(代码洁癖)

有了这想法就想着我可以去了解jQuery源码，了解它的结构，这样我就可以删除我不想要的代码啦。然后就有了这个源码解析。

在这个jQuery文件中的中文注释是我的解析，伴随着我对jQuery的理解，我所做的中文注释中肯定会有一些错误的，望指正。



## 源码目录结构

        (14 , 37)  做个判断兼容Node.JS

        (40 , 112)  定义了一些变量和函数 jquery = function(){};

        (114 , 193) 给jQuery添加一些原型方法

        (195 , 262) extend : JQ的继承方法

        (264 , 510) jQuery.extend()  :  扩展一些工具方法

        (538 , 2901) Sizzle  :  实现复杂选择器

        (2903 ， 2945)  一些jQuery对象实例方法（find fliter not is）

        (2952 ， 3060)  定义rootjQuery 和 init构造函数，实现一些简单的选择器

        (3076 ， 3155)  定义一些jQuery实例方法（has closest index add addBack）

        (3162 ， 3238)  用jQuery.each()循环执行工具方法
        (parent parents parentsUntil next prev nextAll prevAll nextUntil prevUntil siblings children contents)

        (3274 , 3507) Callbacks : 回调对象 ： 对函数的一个统一管理

        (3509 , 3848) Deferred : 延迟兑现 ： 对异步的统一管理

        (3894 ， 3950)  jQuery.ready附带方法，判断DOM是否加载完成

        (3957 ， 4024)  jQuery内部access方法

        (4035 , 4351)  jQuery里的data数据缓存

        (4354 ，4486)  jQuery的队列管理(queue dequeue)

        (4494 ，4692)  jQuery实例方法：操作DOM(show hide toggle)

        (4693 ，4964) 内部方法(getAll setGlobalEval buildFragment 内部函数 on )

        (4970 ，5468)  封装event对象(add remove dispatch handlers addProp fix) jQuery工具方法(removeEvent Event)

        (5471 ，5565)  所有常见事件的封装

        (5614 ，5817)  定义一些内部方法（on one off）

        (5614 ，5818)定义一些正则 内部方法为下面的工具方法做铺垫
        (manipulationTarget disableScript restoreScript cloneCopyEvent fixInput domManip remove)

        (5820 ，5900)  jQuery工具方法(htmlPrefilter clone cleanData)

        (5902 ，6067)  jQuery实例方法(detach remove text append prepend before after empty clone html replaceWit)

        (6088 ，6163)  自执行函数(做兼容)

        (6166 ，6380) 定义一些内部方法为下面的工具方法做铺垫
        (curCSS addGetHookIf vendorPropName finalPropName setPositiveNumber augmentWidthOrHeight getWidthOrHeight)

        (6382 ，6624)  jQuery工具方法 定义一些内部对象(cssHooks cssNumber cssProps) 工具方法(style css) jQuery.cssHooks

        (6626 ，6649)  jQuery的CSS方法。上面代码都是做铺垫。

        (6652 ，7456)  animate jQuery的动画

        (7459 ，7746) jQuery的attr方法

        (7753 ，7920) jQuery实例方法(addClass removeClass toggleClass hasClass)

        (7927 ，8303)

        (10246)       window.jQuery = window.$ = jQuery;

## 代码持续更新