## CSS 实现对号效果
实现对号效果，一种思路是利用现成的符号，直接在网上搜索到 √，插入页面。另一种思路是本文要介绍的用 CSS 实现。思路是：
- 给块级元素设置宽度和高度
- 设置元素相邻的两个 border
- 旋转元素

### HTML
``` html
<div class="check-style-unequal-width"></div>
```
**解析**    
- 此处需要使用块级元素
- 不需要设置元素内容

### CSS
``` css
.check-style-unequal-width {
    width: 8px;
    height: 16px;
    border-color: #009933;
    border-style: solid;
    border-width: 0 3px 5px 0;
    transform: rotate(45deg);
}
```
**解析**   
- 设置宽度和高度，得出一个矩形效果，并且矩形中没有内容
- 设置相邻 border 的样式，得到对号的大体轮廓
- 使用旋转属性，成功得到对号

### 运行效果
!(check 运行效果)[https://raw.githubusercontent.com/nanzhangren/CSS_skills/master/sign/check/check.PNG]

### 提醒
- 行级元素直接设置宽度和高度没有用，需要设置其 display 使其变为块级元素。例如：span 需要设置 display 为 inline-block 才能适用于本例效果
- 不需要设置元素内容
- 可以根据实际需求调整元素宽度和高度
- 可以根据实际需求设置不同的 border，以及相邻 border 的宽度
- 可以对此效果做简单的修改，作用于伪元素 ::before 和 ::after。可参考 [::before & :：after](https://github.com/nanzhangren/CSS_skills/blob/master/pseudo_element/before_after/before_after_real_case.html)
