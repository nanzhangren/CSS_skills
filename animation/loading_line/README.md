## 加载动画之线条伸缩

### 难度系数
☆☆☆

### 效果图
![加载动画](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/animation/loading_line/loading_line.gif)

### 思路
通过 3 个线条高度的动态变化实现加载动画，为了突出效果，给线条增加了阴影。对动画而言，@keyframes 和 animation 是必不可少的技巧。同时本例中使用了 first-child 和 nth-child 选择器，用于给特定位置的元素添加其特有的动画属性。

### HTML
``` html
<div class="loading-container">
    <span class="loading-line"></span>
    <span class="loading-line"></span>
    <span class="loading-line"></span>
</div>
```
**解析**    
- loading-container 标识动画容器
- loading-line 标识各个动画线条

### CSS
``` css
.loading-container {
    padding: 60px;
    display: flex;
    align-items: center;
    height: 40px;
}

.loading-line {
    display: inline-block;
    width: 8px;
    height: 20px;
    background-color: dodgerblue;
    margin: 0 4px;
    box-shadow: 5px 5px 3px #a495e0db;
}

.loading-line:first-child {
    animation: higher 1.2s ease-out infinite alternate;
}
.loading-line:nth-child(2) {
    animation: higher 1.2s ease-out infinite .4s alternate;
}
.loading-line:nth-child(3) {
    animation: higher 1.2s ease-out infinite .8s alternate;
}

@keyframes higher {
    from {
        height: 20px;
    }
    to {
        height: 40px;
    }
}
```
**解析**   
- 动画容器需要设置高度，同时通过 flex 布局设置动画线条垂直居中
- 设置动画线条相同基础属性，宽高度、背景色、阴影等
- 添加自定义动画效果 higher
- 通过 CSS 选择器给 3 个线条添加动画效果，注意每个线条延时时间不一样

### 知识点
- @keyframes
- animation
- box-shadow
- first-child
- nth-child

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/animation/loading_line/loading_line.html
