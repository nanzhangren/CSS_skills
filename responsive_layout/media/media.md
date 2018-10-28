## 媒体查询实现响应式布局
本文主要介绍 @media 查询的使用。通过媒体查询，在不同的屏幕尺寸下，可以设置不同的样式。以此，可以完美解决不同屏幕适配的问题。话不多说，先来看看效果：   
![media 适配屏幕](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/responsive_layout/media/media.gif)

### CSS
``` css
@media screen and (max-width: 400px) {
	.btn {
		background-color: lightblue;
	}
}

@media screen and (min-width: 400px) and (max-width: 800px) {
	.btn {
		background-color: yellowgreen;
	}
}

@media screen and (min-width: 800px) {
	.btn {
		background-color: orangered;
	}
}

.btn {
	width: 100%;
	height: 60px;
	border: none;
	outline: none;
}
```
**解析**    
将大大小小的屏幕尺寸划分为连续的几个宽度区间，在各个宽度区间内，设置各自的元素属性。这样在不同宽度的屏幕上，媒体查询会根据具体的屏幕尺寸适配到对应的区间，来应用此区间内的元素属性，达到适配不同屏幕的效果。
```
- 高度同样可以适配
- 这时想想使用 bootstrap 时用到的 xs、sm、md、lg，用没有恍然大悟的感觉 ^_^
