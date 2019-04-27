## 按钮大小变化效果
我们经常会看到有的网页上按钮由大变小、再由小变大，这样不停变化的情况。今天就来和大家介绍如何实现这种效果。   
首先将效果的实现过程分为两个阶段：    
    第一阶段，按钮由大变小；    
    第二阶段，按钮由小变大。    
说到这里，有没有联想到 CSS3 的自定义动画规则 @keyframes，是的，通过 @keyframes 就可以实现两个动画阶段的控制。而按钮大小变化的效果，可以通过 CSS3 的 transform 属性实现。

### HTML
``` html
<input type="button" id="btn" value="我会变" />
```
**解析**    
- html 中添加按钮标签

### CSS
``` css
#btn {
	width: 120px;
	height: 45px;
	background-color: greenyellow;
	border-radius: 45px;
	font-size: 16px;
	animation: switch 1s ease-out infinite;
}

@keyframes switch {
	0%, 100% {
		transform: scale(1);
	}
	50% {
		transform: scale(0.6);
	}
}
```
**解析**   
- 将按钮的边框设置为圆角边框
- 通过 @keyframes 添加自定义动画，按钮大小变化通过 transform 属性控制。动画起始点为按钮本来大小，中间变化点将按钮缩小为本身大小的 60%。按钮缩小比例可以根据实际需求做相应修改
- 自定义动画名称添加至 animation 属性，并设置动画时间为 1 秒，动画次数为无限次

### 运行效果
![按钮大小变化效果](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/animation/bigger_btn/bigger_btn.gif) 

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/animation/bigger_btn/bigger_btn.html