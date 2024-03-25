# 超长文本“省略”
页面内容处理中，经常遇到的问题之一就是内容过长不能全部显示，要截取主要内容显示在界面。一般的做法大家会通过JS截取字符串到一定长度，将截取后的字符串显示在页面中，这样处理实现目标效果是没有问题的，不过有几个缺陷：各语言字母宽度不一致，页面很难控制内容宽度，容易产生多余空白；通过JS实现必然会增加逻辑复杂度，产生多余的处理逻辑；单行文本省略JS处理起来复杂度尚可，多行文本省略时复杂度会比较高。
由此，给大家介绍直接使用CSS控制即可实现的文本省略效果。之前有文章[《使溢出文字显示为...》](https://mp.weixin.qq.com/s?__biz=MzUyMzEwNjc5NQ==&mid=2247483670&idx=1&sn=d0c0011c22ed39a8ac38b4ed6c485745&chksm=f9c0e192ceb76884ea38e12f9aeb49567d746363af1b1c49ca5af92eb2c906ab1b0639f83850&token=419180341&lang=zh_CN#rd)已经简单介绍过，这里给大家详细介绍下单行、多行文本省略的实现方法及实现原理。

## 难度系数
☆☆☆☆

## 单行文本省略
### HTML
``` html
<p class="text-container one-line-ellipsis" title="寻寻觅觅，冷冷清清，凄凄惨惨戚戚。乍暖还寒时候，最难将息。三杯两盏淡酒，怎敌他、晚来风急？雁过也，正伤心，却是旧时相识。满地黄花堆积。憔悴损，如今有谁堪摘？守着窗儿，独自怎生得黑？梧桐更兼细雨，到黄昏、点点滴滴。这次第，怎一个愁字了得！">
    寻寻觅觅，冷冷清清，凄凄惨惨戚戚。乍暖还寒时候，最难将息。三杯两盏淡酒，怎敌他、晚来风急？雁过也，正伤心，却是旧时相识。满地黄花堆积。憔悴损，如今有谁堪摘？守着窗儿，独自怎生得黑？梧桐更兼细雨，到黄昏、点点滴滴。这次第，怎一个愁字了得！
</p>
```  
解析： 
- 此处为示例文本，大家输入自己喜欢的一段内容即可。
- 可给DOM元素设置title属性，用于文本隐藏时的内容提示。

### CSS
``` css
.one-line-ellipsis {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
```
解析： 
1. 通过white-space属性控制文本不换行，一直在一行显示。
2. 在文本宽度固定的前提下，通过overflow属性控制文本超出固定宽度后，超出宽度的文本被隐藏。
3. 设置**text-overflow**属性值为**ellipsis**，显示省略号来替代被隐藏的文本。

### 效果图
![单行超长文本省略](https://github.com/nanzhangren/CSS_skills/blob/master/text-ellipsis/one-line-ellipsis.png)   


## 多行文本省略
### HTML
``` html
<p class="text-container multi-line-ellipsis" title="寻寻觅觅，冷冷清清，凄凄惨惨戚戚。乍暖还寒时候，最难将息。三杯两盏淡酒，怎敌他、晚来风急？雁过也，正伤心，却是旧时相识。满地黄花堆积。憔悴损，如今有谁堪摘？守着窗儿，独自怎生得黑？梧桐更兼细雨，到黄昏、点点滴滴。这次第，怎一个愁字了得！">
    寻寻觅觅，冷冷清清，凄凄惨惨戚戚。乍暖还寒时候，最难将息。三杯两盏淡酒，怎敌他、晚来风急？雁过也，正伤心，却是旧时相识。满地黄花堆积。憔悴损，如今有谁堪摘？守着窗儿，独自怎生得黑？梧桐更兼细雨，到黄昏、点点滴滴。这次第，怎一个愁字了得！
</p>
```  
解析： 
- 此处为示例文本，大家输入自己喜欢的一段内容即可。
- 可给DOM元素设置title属性，用于文本隐藏时的内容提示。

### CSS
``` css
.multi-line-ellipsis {
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3;
    overflow: hidden;
}
```
解析： 
1. 多行文本隐藏需要借助于**-webkit-line-clamp**属性，-webkit-line-clamp生效有两点依赖：
a. **display**属性设置成**-webkit-box**或**-webkit-inline-box**；
b. **box-orient**属性设置成**vertical**。
详见：https://developer.mozilla.org/zh-CN/docs/Web/CSS/-webkit-line-clamp。设置后效果如下图：
![多行超长文本省略无overflow](https://github.com/nanzhangren/CSS_skills/blob/master/text-ellipsis/multi-line-ellipsis-no-overflow.png)   
2. 设置webkit相关属性后，文本被限制在设定行数，还需要设置overflow属性为hidden隐藏多余文本行，以达到预期的文本省略效果。

### 效果图
![多行超长文本省略](https://github.com/nanzhangren/CSS_skills/blob/master/text-ellipsis/multi-line-ellipsis.png)   

## 知识点
- text-overflow
- -webkit-line-clamp
- white-space
- overflow


## Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/text-ellipsis/text-ellipsis.html
