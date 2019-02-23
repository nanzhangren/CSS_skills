## CSS 实现向右导航 icon
对于看过CSS绘制三角形的童鞋来说，实现向右导航 icon 很好理解，可能大家稍加即可知晓实现方式。是的，只需要设置一个元素的相邻 border，之后旋转一下即可。

### HTML
``` html
<span id="right-arrow"></span>
```

### CSS
``` css
#right-arrow {
    display: inline-block;
    width: 17px;
    height: 17px;
    border-top: 2px solid red;
    border-right: 2px solid red;
    transform: rotate(45deg);
}
```
**解析**   
- 给 span 元素设置合适的宽高，到达要求的效果大小
- 设置元素的两个相邻 border，宽度合适即可
- 将元素旋转 45 度即为向右导航 icon 效果
- border 的颜色为 icon 的颜色

### 运行效果
![向右导航 icon 运行效果](https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/sign/right_arrow/right_arrow.png)

### GitHub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/sign/right_arrow