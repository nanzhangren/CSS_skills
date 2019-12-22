## CSS 画圆环
画圆环思想很简单：首先画两个圆，设置不同的背景色；然后让两个圆的圆心重合即可。

### 难度系数
☆☆

### HTML
``` html
<div class="container">
    <span class="ring-style"></span>
</div>
```  
解析： 
- 此处有父容器

### CSS
``` css
.container {
    position: relative;
    top: 0;
    left: 0;
    width: 300px;
    height: 300px;
    background-color: lightgrey;
}
.ring-style {
    display: inline-block;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: blue;
    width: 260px;
    height: 260px;
    border-radius: 260px;
}
.ring-style::before {
    content: ' ';
    display: inline-block;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    width: 200px;
    height: 200px;
    border-radius: 200px;
}
```
解析： 
- 设置元素的宽高、圆角效果，即可画出一个圆
- 通过 ::before 伪元素和本体元素，创建两个圆
- 通过基于父容器的绝对定位，设置 top、left、translate 属性，让元素基于父容器水平、竖直居中，即可让两个圆的圆心重合

### 效果图
![圆环](https://github.com/nanzhangren/CSS_skills/blob/master/sector/ring/ring.png)

### 知识点
- border-radius
- ::before && ::after
- 元素水平、竖直居中

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/sector/ring/ring.html