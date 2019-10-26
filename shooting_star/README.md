## 漫天纷飞“流星雨”
本文通过 CSS 的简单应用实现了流星雨的效果。

### 难度系数
☆☆☆☆☆

### 效果图
![漫天纷飞流星雨](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/shooting_star/shooting_star.gif)

### 思路
流星雨的实现分为三部分：   
（1）用 border 属性实现直角三角形。三角形的实现可以参考“CSS绘制三角形”   
（2）给直角三角形添加圆形效果，弱化直角形状的棱角
（3）添加动画效果，让直角三角形动起来

### HTML
``` html
<span class="shooting-star animation"></span>
```
**解析**   
- html 添加一个动画容器即可

### CSS
``` css
.shooting-star {
    margin: 30px;
    display: block;
    width: 0;
    border-radius: 2px;
    border-top-width: 1px;
    border-top-style: solid;
    border-top-color: transparent;
    border-left-width: 230px;
    border-left-style: solid;
    border-left-color: white;
    border-right-width: 230px;
    border-right-style: solid;
    border-right-color: transparent;
    border-bottom-width: 1px;
    border-bottom-style: solid;
    border-bottom-color: white;
}
.animation {
    animation: fly 3s infinite;
}
@keyframes fly {
    from {
        margin-left: 900px;
        border-left-width: 130px;
        border-right-width: 130px;
    }
    to {
        margin-left: -900px;
        border-left-width: 360px;
        border-right-width: 360px;
    }
}
```
**解析**   
- 直角三角形
    - 直角三角形的实现，首先确定直角的方位，本例直角方位为左下角，因此设置左边框和下边框为有颜色的，右边框和上边框为透明色
    - 流星类似一条线的形状，所以直角三角形高度很小，宽度很大。因此此处设置左右边框宽度值很大，上下边框宽度值很小
    - 类似 span 这样 display 默认属性值不为 block 的元素，需要设置 display 属性为 block
- 圆形效果
    - 通过 border-radius 设置圆形 border 即可，border-radius 的值与直角三角形高度相同即可（注意高度值应为 border-top-width 和 border-bottom-width 数值之和）
- 动画效果
    - 通过 margin-left 设置动画初始和结束位置
    - 通过改变 border-*-width 的值达到流星长度变化的效果
    - 动画时长决定流星通过界面的时间
    - 动画次数设置为无限次

### 知识点
- CSS 实现三角形
- 圆角 border
- animation 添加动画效果
- @keyframes 自定义动画

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/shooting_star/shooting_star.html