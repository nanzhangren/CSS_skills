## “冒尖”首字母
日常文本阅读中，经常可以看到段落首字母大写或加特效。想实现这种效果，我们借助于伪类first-letter的帮助即可。

### 难度系数
☆☆☆

### HTML
``` html
<p class="customized-first-letter">
    Prajna Paramita, soon as soon as, life be beautiful like summer flowers and death like autumn leaves. Also care
    about what has.
</p>
```  
解析： 
- 此处为示例文本，大家输入自己喜欢的一段内容即可。

### CSS
``` css
:root {
    --base-font-size: 16px;
    --base-line-height: 20px;
}

.customized-first-letter {
    font-size: var(--base-font-size);
    line-height: var(--base-line-height);
}

.customized-first-letter::first-letter {
    float: left;
    font-weight: bold;
    font-size: calc(var(--base-font-size) * 4);
    line-height: calc(var(--base-line-height) * 2);
}
```
解析： 
1. 建议设置首字母效果之前，先设置基础段落的样式，方便首字母样式与基础样式做对比。基础样式设置可利用CSS变量特性：
    - CSS原生变量定义语法：**--***   
    - 变量使用语法：**var(--*)**   
    - *表示要设置的变量名称。
2. 设置首字母效果，常见设置为文本加粗(font-weight)、字体放大(font-size)、跨文本行(line-height)。如示例代码，首字母字体放大为基础样式的4倍、跨2行文本布局。效果如下图：
![首字母无浮动](https://github.com/nanzhangren/CSS_skills/blob/master/first-letter/first-letter-without-float.png)   
如图可见，首字母并没有跨行，只是字体变大了。
3. 给首字母样式添加float，设置为浮动元素，即可实现首字母跨行效果。

### 效果图
![首字母浮动](https://github.com/nanzhangren/CSS_skills/blob/master/first-letter/first-letter-with-float.png)   

### 知识点
- ::first-letter
- var(--*)
- calc(*)
- float

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/first-letter/first-letter.html
