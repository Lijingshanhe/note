##### 视频标签:video

##### 音频标签:audio

##### 通过 JS 控制(video 与 audio 相同)

- 属性

  - currentTime 视频播放的当前进度、
  - duration:视频的总时间
  - paused:视频播放的状态

- 方法

  - ```
    load()
    ```

    重新加载音频/视频元素

    - 语法: `audio|video.load()`
    - 用于在更改来源或其他设置后对音频/视频元素进行更新

  - `play()` 播放

  - `pause()` 暂停

- 事件

  - `oncanplay:` 事件在用户可以开始播放视频/音频（audio/video）时触发。
  - `ontimeupdate:` 通过该事件来报告当前的播放进度.
  - `onended:` 播放完时触发

- 全屏：`video.webkitRequestFullScreen()`



#### 新增input type类型

- `email` 限制用户输入必须为Email类型
- `tel` 手机号码
- `url` 限制用户输入必须为URL类型
- `number` 只能输入数字
- `search` 具有搜索意义的表单属性
- `range` 范围 滑动条
- `color` 拾色器
- `time` 时间
- `date` 选取日、月、年
- `datetime` 选取时间、日、月、年（UTC 时间）(移动支持)
- `datetime-local` 选取时间、日、月、年（本地时间）
- `month` 选取月、年
- `week` 选取周和年
- 部分类型针对移动设备,具有一定的兼容性.

#### 新增form表单元素

* ` datalist` 数据列表 自动补全，常与`input`标签配合使用 实际开发中：需要自动补全的内容列表项可能很多，不可能挨个展示在页面中，一般是通过ajax局部页面刷新技术实现的。
* `meter` 用来表示规定范围内的数量值，如磁盘使用量比例饿、关键词匹配程度等。
* `progress` 进度条

### 新增表单属性

- `autofocus` 获取焦点
- `autocomplete` 自动完成，用于表单元素，也可用于表单自身(on/off)
- `form` 指定表单项属于哪个form，处理复杂表单时会需要 一般一个页面只有一个form
- `novalidate` 关闭验证，可用于form标签
- `required` 必填项
- `pattern` 正则表达式 验证表单
- `autocomplete` 是否保存用户输入值 默认为on，关闭提示选择off
- `formaction` 主要应用于表单内某元素提交地址与整个表单提交地址不同，进行单个地址覆盖 如：``

#### 新增表单事件

- `oninput` 用户输入内容时触发，可用于移动端输入字数统计
- `oninvalid` 验证不通过时触发
- `tabindex` (控制 input 标签按 tab 键获取到焦点的顺序)

```
姓名: <input type="text" tabIndex="1"> <br>
年龄: <input type="number" tabIndex="3"> <br>
电话: <input type="tel" tabIndex="2"> <br>
地址: <input type="text" tabIndex="4">
```



### DOM 扩展

###### 获取元素

`document.querySelector("selector")` html5新选择器，参数是css选择器参数,选择选中的第一个

`document.querySelectorAll("selector")` 选择多个

###### 类名操作

- `Node.classList.add('class')` 添加class
- `Node.classList.remove('class')` 移除class
- `Node.classList.toggle('class')` 切换class，有则移除，无则添加
- `Node.classList.contains('class')` 检测是否存在class 非常好用 但是出现的太晚了

###### 自定义属性

在HTML5中我们可以自定义属性，其格式如下 `data-*=""`，例如:

`data-info="我是自定义属性"`，通过`Node.dataset['info']` 我们便可以获取到自定义的属性值。

`Node.dataset`是以类对象形式存在的

当我们如下格式设置时，则需要以小驼峰格式才能正确获取

```
data-my-name="mm"`，获取`Node.dataset['myName']
```



### CSS3

可能使用的前缀有:

> Chrome: -webkit-
>
> Firefox: -moz-
>
> IE: -ms-
>
> IOS: -webkit-
>
> Opera: -o-
>
> safari: -webkit-



### 选择器

CSS3 新增了许多灵活查找元素的方法，极大的提高了查找元素的效率和精准度。CSS3 选择器与 jQuery 中所提供的绝大部分选择器兼容。

1. 属性选择器 通过属性来选择元素
   - `E[attr]` 选择包含 attr 属性的所有元素
   - `E[attr=mydemo]` 选择属性 attr 的值等于 mydemo 字符的所有元素
   - `E[attr*=mydemo]` 选择属性 attr 的值任意位置包含 mydemo 字符的所有元素
   - `E[attr^=mydemo]` 选择属性 attr 的值开始位置包含 mydemo 字符的所有元素
   - `E[attr$=demos]` 选择属性 attr 的值结束位置包含 mydemo 字符的所有元素

- 结构伪类 重点通过 E 来确定元素的父元素。
-  `E:first-child` 第一个子元素 
- E:last-child` 最后一个子元素  ` 
- `E:nth-child(n)` 第 n 个子元素
-  `E:nth-last-child(n)` 同 E:nth-child(n) 相似，只是倒着计算
- 目标伪类 E:target 结合锚点进行使用，处于当前锚点的元素会被选中
- `li:target{ font-size: 30px; color: blue; } <style> <body> <a href="#li3">点我</a> <li id="li3">li3</li> </body>`
- 伪元素  `E::before`、`E::after` 默认行内元素 `content` 属性必须写 
-  `E::first-letter`文本的第一个字母或字 
-  `E::first-line` 文本第一行 
-  `E::selection` 被选中的文本 
-  ":" 与 "::" 用于区分伪类和伪元素



### 阴影

1. 文本阴影

```
text-shadow: h-shadow(x) v-shadow(y) blur(模糊半径) color(颜色)
```

1、水平偏移量 正值向右 负值向左

2、垂直偏移量 正值向下 负值向上

3、模糊半径是不能为负值

4、可以有多个影子，用逗号隔开 案例:浮雕文字

1. 盒子阴影

```
box-shadow: h-shadow(x) v-shadow(y) blur(模糊半径) spread(扩展范围) color(颜色) inset(是否内嵌,可省略)
```

------

### 盒模型

CSS3 中可以通过`box-sizing`来指定盒模型，即可指定为`content-box`、`border-box`，这样我们计算盒子大小的方式就发生了改变

- `content-box`: 对象的实际宽度等于设置的 width 值和 border、padding 之和 (默认方式)
- `border-box`： 对象的实际宽度就等于设置的 width 值，即使定义有 border 和 padding 也不会改变对象的实际宽度，即 ( Element width = width )

我们把这种方式叫做 css3 盒模型

### 渐变

1. 线性渐变 沿着某条直线朝一个方向产生渐变效果

语法: `background: linear-gradient(direction, color-stop1, color-stop2, ...);`

```css
direction: 方向 可以是 角度(10deg)顺时针  也可以是 to top/left/right/bottom
	eg: background: linear-gradient(right ,red 60%,orange 80%);
颜色后面可以跟百分比,表示从百分几开始渐变
渐变的兼容写法 方向是相反的  而且不带to
	eg: background: -webkit-linear-gradient(right ,red 60%,orange 80%);

重复渐变: background: repeating-linear-gradient(to right,red 0, red 10%, purple 10%, purple 20%)
可简写为: background: repeating-linear-gradient(to right,red 0 10%, purple 10% 20%)
一般是通过ui设计稿 直接提取的渐变 角度 颜色比重
```

1. 径向渐变 从一个中心点开始沿着四周产生渐变效果

语法: `background: radial-gradient((shape? size? (at position?))?, start-color, ..., last-color)` **? 表示可省略**

```css
shape 渐变形状 : circle | ellipse(椭圆)
size 渐变大小:
	closest-side（指定径向渐变的半径长度为从圆心到离圆心最近的边）
	closest-corner （指定径向渐变的半径长度为从圆心到离圆心最近的角）
	farthest-side（指定径向渐变的半径长度为从圆心到离圆心最远的边）
	farthest-corner（指定径向渐变的半径长度为从圆心到离圆心最远的角）
	也可指定大小: 需要注意的是 若渐变形状为圆形，则该渐变大小只能设置一个数且不能为百分数，而椭圆既可以为具体数值也可以为百分数

	注意: 只传一个值默认形状为圆形,传入的是半径大小,不能为百分比;
				传两个值则代表形状为椭圆形,第一个是x轴半径,第二个是y轴半径
				圆心位置参数一定要置于radial-gradient()第一个参数的末尾，顺序千万不能放反了

	重复渐变 : background: repeating-radial-gradient(circle at center,#f00 0,#f00 10%,#ff0 10%,#ff0 20%);
	可简写为: background: repeating-radial-gradient(circle at center,#f00 0 10%,#ff0 10% 20%);
```

### 过渡

`transition` 过渡 实现元素不同状态间的平滑过渡，经常用来制作动画效果

```css
transition: transition-property transition-duration transition-timing-function transition-delay
		transition-property   规定应用过渡的 CSS 属性的名称 (一般都写 all);
		transition-duration   定义过渡效果花费的时间。默认是 0
		transition-timing-function: 规定过渡效果的时间曲线。默认是 "ease"。
					linear|ease|ease-in|ease-out|ease-in-out|cubic-bezier(n,n,n,n);
		transition-delay 			规定过渡效果何时开始。默认是 0
```

`transform` 用于设置转换动画 如旋转、位移、倾斜等

```css
transform: scale? translate? rotate? skew?;
缩放 scale(x, y) 可以对元素进行水平和垂直方向的缩放，x、y的取值可为小数，不可为负值，设置一个值时表示 x、y同时进行缩放
移动 translate(x, y) 可以改变元素的位置，x、y可为负值
旋转 rotate(deg) 可以对元素进行旋转，正值为顺时针，负值为逆时针
倾斜 skew(x-angle,y-angle)	定义沿着 X 和 Y 轴的 2D 倾斜转换
		skewX(x-angle) 	定义沿着 X 轴的 2D 倾斜转换
		skewY(y-angle)	定义沿着 Y 轴的 2D 倾斜转换

rotateX/Y/Z 		沿X/Y/Z轴旋转
translateX/Y/Z 	沿X/Y/Z轴移动
```

------

### 透视

`perspective`有两种写法

a) 作为一个属性，设置给父元素，作用于所有 3D 转换的子元素 

b) 作为 transform 属性的一个值，作用于元素自身,子元素的 3D 效果可呈现 *透视会产生近大远小的效果* `backface-visibility：visible/ hidden` 设置元素背面是否可见

#### 动画

- `Animation-name` 动画名称(必填)
- `Animation-duration` 动画持续时间(必填)
- `animation-timing-function`规定动画的速度曲线
- `animation-delay` 动画延迟（只是第一次）
- `animation-iteration-count` 重复次数 infinite 无限次
- `animation-direction` 动画是否重置后再开始播放
- `animation-fill-mode` 动画执行完毕后状态
- 简写`animation: name duration timing-function delay iteration-count direction fill-mode;`

