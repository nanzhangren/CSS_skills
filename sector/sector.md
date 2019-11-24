## CSS 画扇形
扇形的绘制只需要在三角形的基础上做出小的修改即可。三角形的绘制可参考《CSS绘制三角形》。

### 难度系数
☆☆

### HTML
``` html
<span class="sector-style"></span>
```  

### 三角形 CSS
``` css
.triangle-style {
    display: inline-block;
    position: absolute;
    top: 80px;
    left: 70px;
    width: 0;
    height: 0;
    border-left: 76px solid transparent;
    border-right: 76px solid transparent;
    border-bottom: 130px solid red;
}
```
**解析**   
- display 值不能为 inline
- 宽度和高度为 0
- 颜色
    - 三角形颜色为其底边对应 border 的颜色
    - 三角形两个侧边对应 border 颜色设置为**透明色**
- 宽度
    - 三角形高度为其底边对应 border 设置的宽度
    - 三角形宽度为两个侧边对应 border 宽度之和

**效果图**   
![***](****)

### 扇形 CSS
``` css
.sector-style {
    display: inline-block;
    position: absolute;
    top: 80px;
    left: 70px;
    width: 0;
    height: 0;
    border-left: 76px solid transparent;
    border-right: 76px solid transparent;
    border-bottom: 130px solid blue;
    border-bottom-right-radius: 130px;
    border-bottom-left-radius: 130px;
}
```
**解析**   
- 在三角形实现基础上，添加 border-radius 效果即可实现扇形。如以上代码，添加三角形底边对应 border 和两个侧边对应 border 的圆角效果即可
- 注意圆角边框值等于底边对应 border 宽度值

**效果图**   
![***](****)

### 知识点
- 三角形实现
- border-radius

### Gitbub 源码
https://github.com/nanzhangren/CSS_skills/blob/master/sector/sector.html