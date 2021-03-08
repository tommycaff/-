# CSS知识总结

最近学习了CSS动画的制作。

今天的博客主要包括两个部分：

1. 浏览器渲染原理

2. CSS 动画的两种做法（transition 和 animation)

## 浏览器渲染原理

1. 浏览器将获取的HTML文档解析成DOM树。

2. 处理CSS标记，构成层叠样式表模型CSSOM(CSS Object Model)。

3. 将DOM和CSSOM合并为渲染树(rendering tree)将会被创建，代表一系列将被渲染的对象。

4. 渲染树的每个元素包含的内容都是计算过的，它被称之为布局layout。浏览器使用一种流式处理的方法，只需要一次绘制操作就可以布局所有的元素。

5. 将渲染树的各个节点绘制到屏幕上，这一步被称为绘制painting。

作者：oWSQo

链接：https://www.jianshu.com/p/e6252dc9be32

6. 最后还有一个步骤：Compose,根据层叠关系展示画面。

![](/images/渲染树.png)

渲染的流程与一些环节的改动有关，例如删除了某个div造成排版的重新改变，这个时候以上流程的每一步都需要进行，有时候只是改变了背景颜色，其他布局不变，那么久直接跳过了layout，如果只是改变了某些样式，例如transform，就可以跳过layout和paint，直接合成。

渲染的更新需要在全屏查看效果，在iframe里面看有问题。

## CSS动画制作

CSS的transform命令可以对元素进行旋转，缩放，倾斜或平移操作。

1. 位移translate，通常X/Y/Z代表坐标系里各方向上的平移。也可以用三个数字分别进行表示，不表示的可以不写。

2. 缩放scale，一位数表示整体缩放，两位数分别表示X/Y上各自的缩放倍数。

3. 旋转rotate，以度数表示。

4. 倾斜skew，这个涉及立体上的角度，给定定位点可以更加具体的展示元素的倾斜情况。

### transition制作动画

transition主要是为给定的两个点补充中间帧。

语法：transition：属性名 时长 过度方式 延时时长

通常后面延时比较少用。也不是所有属性都能过度，需要透明度（opacity）、背景等等额改变最好作明确的编码表达。

## animation制作动画

语法1：@keyframe 元素id{n% {相应命令}}

语法2：@keyframe form{相应命令} to{相应命令}

附带两个自制动画链接：

transition: http://js.jirengu.com/javil/1/watch?html,css,output

animation: http://js.jirengu.com/feyev/1/watch?html,css,output