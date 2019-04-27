## 多图滚动切换

### 写在前面的话
之前写多图切换时有童鞋建议多写写动画效果，也想和大家多多分享的，怎奈想象力不足，一直没找到合适的效果。最近在网上无意看到了一个多图滚动切换的效果，感觉看起来不错，遂写下来和大家分享一下。

### 思路
- 动画效果技术上严格依赖于以下几点，请大家熟练掌握，然后看下文就比较好理解了
	- transform 属性
	- animation 属性
	- @keyframes 自定义动画规则
- 本文为3张图片滚动切换，每滚动一圈（360 度）有 3 个动画切换效果，0 度 -> 120 度 -> 240 度 -> 0 度；每一圈动画结束会替换首图，3 张图片都做首图总共需要 3 圈，之后整个动画完成。所以自定义动画规则中总共需要 3 * 3 = 9 个动画切换效果
```
首图指的是下文中 rotateY(0deg) 的动画停留效果
```

### HTML
``` html
<div id="container">
	<img class="scroll-img" />
</div>
```
**解析**    
- html 中添加图片容器元素，容器中添加图片元素

### CSS
``` css
#container {
	width: 210px;
	height: 630px;
	overflow: hidden;
}

#container > img {
	width: 100%;
	height: 100%;
	background-repeat: no-repeat;
	background-size: contain;
}

.scroll-img {
	animation: scroll 9s ease-out infinite;
}

@keyframes scroll {
	0%, 7% {
		background-image: url("111.png");
		transform: rotateY(0deg);
	}
	12%, 17% {
		background-image: url("222.png");
		transform: rotateY(120deg);
	}
	22%, 27% {
		background-image: url("333.png");
		transform: rotateY(240deg);
	}
	32%, 41% {
		background-image: url("222.png");
		transform: rotateY(0deg);
	}
	46%, 51% {
		background-image: url("333.png");
		transform: rotateY(120deg);
	}
	56%, 61% {
		background-image: url("111.png");
		transform: rotateY(240deg);
	}
	66%, 74% {
		background-image: url("333.png");
		transform: rotateY(0deg);
	}
	79%, 84% {
		background-image: url("111.png");
		transform: rotateY(120deg);
	}
	89%, 94% {
		background-image: url("222.png");
		transform: rotateY(240deg);
	}
	99%, 100% {
		background-image: url("111.png");
		transform: rotateY(0deg);
	}
}
```
**解析**   
- 本例通过 background-image 属性实现图片资源的切换。使用 background-image 时注意同时要设置 background-repeat 和 background-size 属性，防止图片资源过大或过小时影响界面显示
- 由于本例中动画切换效果较多，设置 animation 属性值时动画时长要相应加大一些
- 垂直方向旋转在 transform 属性值中使用 rotateY 函数，水平方向旋转使用 rotateX 函数
- @keyframes 自定义动画中包含两种效果：**动画停留和动画切换**。规则中可见区间对应的是动画停留效果，比如 0%~7%、12%~17%；除规则中标识之外的区间则对应动画切换效果，比如 7%~12%、17%~22%
- 可以看出 scroll 规则中有 9 个动画切换，10 个动画停留。为什么是这样呢？要注意最后一个动画停留到第一个动画停留之间也是需要有动画切换效果的，所以**最后一个动画停留要和第一个动画停留效果要保持一致**，这样动画重复播放时才会平稳过渡，而不是一个强切的效果

### 动画各阶段比例的计算
怎么计算动画停留需要多少比例，动画切换需要多少比例，肯定有不少童鞋要问这个问题了？这里专门拉个标题说明一下。    
1. 根据需求明确动画切换数量。比如本例是 3 圈旋转，每圈旋转有 3 个动画切换，所以总共是 9 个动画切换
2. 动画停留 = 动画切换 + 1。动画切换是 9 个，所以动画停留应该是 9 + 1 = 10 个
3. 动画停留第一个和最后一个是相同效果，所以比例是按照 n - 1 进行计算的。如本例就是 9 个
4. 将 100 个比例用动画停留和动画效果的总和进行等分。不能够等分时看动画停留是不是有需要偏重的，像本例首图就可以多分些比例。
```
本例计算方法：
（1）100 ÷ (9 + 9) = 5 余 10，所以每个动画停留和动画切换都有一个基数 5
（2）将余数 10 分到 3 个首图中，不能等分就 3 + 3 + 4
（3）为了动画平稳过渡，需要将第一个动画停留比例分一小部分至最后一个动画停留。分一小部分即可，不然会影响刚开始时的动画效果
（4）所以动画各阶段比例划分如下：
	第一个动画停留（第一个首图）：7
	第二个首图动画停留：5 + 4 = 9
	第三个首图动画停留：5 + 3 = 8
	最后一个动画停留（第一个首图）：1
	其他所有动画停留：5
	所有动画切换：5
``` 

### 运行效果
![多图滚动切换](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/animation/scroll_image/scroll_image.gif)

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/animation/scroll_image/scroll_image.html