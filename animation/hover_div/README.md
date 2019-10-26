## 鼠标经过放大元素
如题，这是一种访问网页时经常会出现的效果。当鼠标经过某一图片或某一容器时，对应元素会有一个放大的动画，有木有好奇这是怎么实现的？那就继续往下看吧！

### 难度系数
☆☆☆

### 效果图
![悬浮放大](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/animation/hover_div/hover_div.gif)

### 思路
本文用到的动画效果不是自定义 @keyframes 了，而是 CSS 的 transition 属性。
```
transition 属性用来设置元素变化的过渡效果。
```
例如：元素正常宽度是 100px，鼠标经过时宽度变为 200px，如果只设置宽度值，效果如下图：
![没有 transition](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/animation/hover_div/no_transition.gif)   
看起来是不是很生硬。   

我们再看一下加上 transition 的效果：
![有 transition](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/animation/hover_div/with_transition.gif)   

看了两个效果的差别，就明白 transition 属性的作用了吧。本例目标和宽度变化类似，只不过是换了一个最终效果。请继续往下看详细代码。

### HTML
``` html
<div id="container">
	<img src="./little_boy.jpg" />
	<span>大家好呀！我是谁你猜？</span>
</div>
```
**解析**    
- 如以上代码，容器中包含图片，以及在图片上绝对定位的标题文本
- 本例放大的是整个容器，所以容器中的元素都会被放大

### CSS
``` css
#container {
	margin: 200px;
	position: relative;
	width: 300px;
	height: 300px;
	background-color: greenyellow;
	transition: transform .5s ease-out;
}

#container img {
	width: 100%;
	height: 100%;
}

#container span {
	position: absolute;
	top: 0;
	left: 0;
	margin: 6px;
	width: 100%;
	height: 20px;
	line-height: 20px;
	font-size: 18px;
	color: white;
	text-align: center;
}

#container:hover {
	transform: scale(1.3);
}
```
**解析**   
（1）添加容器的 hover 伪类，通过 transform 属性设置容器放大效果
（2）设置容器的 transition 属性，属性值为 transform 以及其动画时长

### 留个问题
前面我们也用 @keyframes 实现了几个动画，那 @keyframes 和 transition 的差别是什么呢？什么时候该用 @keyframes？什么时候该用 transition？

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/animation/hover_div/hover_div.html