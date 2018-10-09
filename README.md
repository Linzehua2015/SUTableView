原文章地址：https://mp.weixin.qq.com/s/di3rg5GKGG2v4CYTtqHeog
首先感谢原作者分享！
早上看到这篇文章的推送，认真看了几遍，梳理了一下逻辑，根据自己的理解改了部分代码，减少属性，以及让逻辑更清晰（自我感觉）。
---
实现效果

![从原帖转过来的](http://upload-images.jianshu.io/upload_images/2083012-76300e03a456fbb5?imageMogr2/auto-orient/strip)

原文的逻辑如下：

![原逻辑](https://upload-images.jianshu.io/upload_images/2083012-b266e4c40b12799b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/640)

简单讲解一下，通过重写UITableView的SetDataSource将数据源交给Inteceptor处理，由Inteceptor负责管理消息转发，是要让谁来管理接收消息的对象。
SUTableView即用来重写方法，又要负责处理数据源，过于冗余。于是我结合MVP的思想，修改了一下逻辑。
如下：

![新逻辑](https://upload-images.jianshu.io/upload_images/2083012-e3b874f0af79db55.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/640)

不需要中间类来管理消息转发，直接将数据源方法交给Presenter来负责，如果Presenter没有实现部分数据源的方法，才将消息转发给外部负责数据源的对象。
原文的逻辑放大了消息转发，将逻辑复杂化了，其实转发只是用来单向传递数据源@require以外的方法，简单处理即可。 
我修改后的Demo：https://github.com/Linzehua2015/SUTableView

再次感谢原作者的分享！
