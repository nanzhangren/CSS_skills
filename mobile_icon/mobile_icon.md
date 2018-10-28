## 手机 app 图标右上方消息计数
突发奇想，实现了一下手机 app 图标右上方的消息计数功能。效果类似我们平时在手机上看到的消息计数，如下图：    
![app 消息计数](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/mobile_icon/mobile_icon_one_number.png)    
实现思路很简单：首先创建一个模拟 app 图标的 div 元素，设置宽度高度和圆边框；之后给该 div 元素设置 ::after 伪元素，用作消息计数；这里需要给伪类设置宽度高度、圆边框、背景颜色、字体颜色，关键在于基于 div 元素的宽度高度设置伪类的位置。

### HTML
``` html
<div class="icon-container">
	<div class="icon"></div>
</div>
```

### CSS
``` css
.icon {
	width: 45px;
	height: 45px;
	background-color: lightgray;
	border-radius: 20%;
}

/* only one number */
.icon::after {
	content: "6";
	display: block;
	box-sizing: border-box;
	width: 20px;
	height: 20px;
	border-radius: 10px;
	background-color: red;
	position: relative;
	top: -10px;
	left: 35px;
	text-align: center;
	color: white;
}
```
**解析**    
div 元素
- 宽度和高度相同
- border-radius 模拟圆边框效果    

伪元素 ::after    
- content 内容即为消息个数
- 设置 display 属性为 block，以便设置的宽度高度可以生效（行内元素设置宽度高度没有用）
- 宽度和高度相同
- border-radius 值为伪元素高度的一半，这样当字数变多时，圆边框不会失真
- 选择相对定位（相对定位是相对于元素本来位置的定位方式），top 值应为负的伪元素高度的一半，left 值应为 div 元素的宽度减去伪元素宽度的一半
- 红色背景和白色字体
