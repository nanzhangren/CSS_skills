## 加载动画之菊花旋转

### 写在前面的话
“读书破万卷”，不仅仅在于“万”，更重要的是要“破”。给大家推荐一本书《远见》，对于即将步入职场或者正在职场拼搏的你来说，值得一看！    

看到目前很多网站的加载效果用的是 gif 图片，于是很好奇了，仅仅用 CSS 怎么实现呢？干货来袭，请接招。

### 难度系数
\****

### 效果图
![加载动画](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/animation/load_effect/load_effect.gif)

### 思路
CSS 用于修饰 HTML，所以即便是再简单的效果，都是要依赖于 HTML 的，而本例效果的实现 HTML 布局更是重中之重。   

先来分析动画效果组成：
- 线条
	- 加载静止的话，就是几个线条组成了一个圈
	- 这些线条长度一致，只是方向有所差别   
	- 每个线条不是贯穿整个直径，而是以半径为单位
- 圆
	- 整体效果是一个圆环，内圆的背景色和整个背景一致   
- 动画
	- 从某一个线条开始，每个半径线条颜色（透明度）逐个发生变化

综上，我们用以下步骤一步步解开加载效果的神秘面纱：   
- 用 HTML 实现沿某个点分布的相同线条，由它们组成一个圆形
- 画一个小圆，添加背景色，并覆盖至线条圆心处
- 添加渐变动画，使线条透明度发生变化
- 通过给不同线条设置不同动画延迟，让线条动起来

### HTML
``` html
<div id="container">
	<div class="load-line rotate-0">
		<span class="left"></span>
		<span class="right"></span>
	</div>
	<div class="load-line rotate-30">
		<span class="left"></span>
		<span class="right"></span>
	</div>
	<div class="load-line rotate-60">
		<span class="left"></span>
		<span class="right"></span>
	</div>
	<div class="load-line rotate-90">
		<span class="left"></span>
		<span class="right"></span>
	</div>
	<div class="load-line rotate-120">
		<span class="left"></span>
		<span class="right"></span>
	</div>
	<div class="load-line rotate-150">
		<span class="left"></span>
		<span class="right"></span>
	</div>
	<div id="circle-center"></div>
</div>
```
**解析**    
- load-line 表示在同一直径的半径线条，由于旋转方向一致，将其放在同一 div 中
- 由于每个半径线条的动画延迟不一样，添加 left 和 right 两种线条
- circle-center 表示内圆

### CSS
``` css
#container, #circle-center {
	background: grey;
}
#container {
	position: relative;
	width: 600px;
	height: 300px;
}
#circle-center {
	position: absolute;
	top: 100px;
	left: 250px;
	width: 100px;
	height: 100px;
	border-radius: 100px;
}
.load-line {
	position: absolute;
	top: 150px;
	left: 200px;
	width: 200px;
	height: 13px;
}
.load-line > span {
	display: inline-block;
	width: 50%;
	height: 100%;
	border-radius: 20px;
	background: white;
}
.left {
	float: left;
}
.right {
	float: right;
}
.rotate-0 {
	transform: rotate(0);
}
.rotate-0 > .left {
	animation: load-effect 1.2s linear 0s infinite;
}
.rotate-0 > .right {
	animation: load-effect 1.2s linear 0.6s infinite;
}
.rotate-30 {
	transform: rotate(30deg);
}
.rotate-30 > .left {
	animation: load-effect 1.2s linear 0.1s infinite;
}
.rotate-30 > .right {
	animation: load-effect 1.2s linear 0.7s infinite;
}
.rotate-60 {
	transform: rotate(60deg);
}
.rotate-60 > .left {
	animation: load-effect 1.2s linear 0.2s infinite;
}
.rotate-60 > .right {
	animation: load-effect 1.2s linear 0.8s infinite;
}
.rotate-90 {
	transform: rotate(90deg);
}
.rotate-90 > .left {
	animation: load-effect 1.2s linear 0.3s infinite;
}
.rotate-90 > .right {
	animation: load-effect 1.2s linear 0.9s infinite;
}
.rotate-120 {
	transform: rotate(120deg);
}
.rotate-120 > .left {
	animation: load-effect 1.2s linear 0.4s infinite;
}
.rotate-120 > .right {
	animation: load-effect 1.2s linear 1.0s infinite;
}
.rotate-150 {
	transform: rotate(150deg);
}
.rotate-150 > .left {
	animation: load-effect 1.2s linear 0.5s infinite;
}
.rotate-150 > .right {
	animation: load-effect 1.2s linear 1.1s infinite;
}
@keyframes load-effect {
	0% {
		opacity: 0;
	}
	100% {
		opacity: 1;
	}
}
```
**解析**   
- 整个效果的父容器需要设置非 static 的定位，方便子元素布局。本例为 relative
- 所有线条大小一致，并且有圆角
- 沿同一直径方向的线条旋转角度一致
- 所有线条动画效果一致（透明度在变化），动画时长一致，动画延迟从某一个线条开始，逐个递加

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/animation/load_effect/load_effect.html

### 参考链接
https://www.cnblogs.com/zourong/p/3980006.html