### [#](https://metro2703.github.io/bufan-doc/learn/jquery/#jquery-的其他选择器)jQuery 的其他选择器

- 层级选择器(css 也有)

| 符号 | 说明       | 用法                             |
| ---- | :--------- | :------------------------------- |
| 空格 | 后代选择器 | $('div span').css('color','red') |
| >    | 子代选择器 | $('div>span').css('color','red') |
| +    | 紧邻选择器 | $('div+p').css('color','red')    |
| ~    | 兄弟选择器 | $('div~p').css('color','red')    |

- 属性选择器

| 符号                       | 说明                                                        | 用法                                          |
| -------------------------- | :---------------------------------------------------------- | :-------------------------------------------- |
| $('a[href]')               | 具有 href 属性的 a 标签                                     | $('a[href]').css('color','red')               |
| $('a[href='baidu']')       | href 属性为'baidu'的 a 标签                                 | $('a[href='baidu']').css('color','red')       |
| $('a[href!='baidu']')      | href 属性不为'baidu'的 a 标签,包括不具有 href 属性的 a 标签 | $('a[href!='baidu']').css('color','red')      |
| $('a[href^='www']')        | href 属性以'www'开头的 a 标签                               | $('a[href^='www']').css('color','red')        |
| $('a[href$='cn']')         | href 属性以'cn'结尾的 a 标签                                | $('a[href$='cn']').css('color','red')         |
| $('a[href*='i']')          | href 属性包含'i'的 a 标签                                   | $('a[href*='i']').css('color','red')          |
| $('a[href][title='内容']') | 具有 href 属性且 title 属性为'内容'的 a 标签                | $('a[href][title='内容']').css('color','red') |

- 基本筛选选择器

| 符号       | 说明(index 从 0 开始)        | 用法                             |
| ---------- | :--------------------------- | :------------------------------- |
| :eq(index) | 匹配一个给定索引值的元素     | $('li:eq(1)').css('color','red') |
| :gt(index) | 匹配所有大于给定索引值的元素 | $('li:gt(1)').css('color','red') |
| :lt(index) | 匹配所有小于给定索引值的元素 | $('li:lt(2)').css('color','red') |
| :odd       | 匹配所有索引值为奇数的元素   | $('li:odd').css('color','red')   |
| :even      | 匹配所有索引值为偶数的元素   | $('li:odd').css('color','red')   |
| :first     | 获取匹配的第一个元素         | $('li:first').css('color','red') |
| :last      | 获取匹配的最后一个元素       | $('li:last').css('color','red')  |

- 其他选择器

| 符号            | 说明(index 从 0 开始)                | 用法                     |
| --------------- | :----------------------------------- | :----------------------- |
| :empty          | 匹配所有不包含子元素或者文本的空元素 | $('li:empty')            |
| :contains(text) | 匹配包含给定文本的元素               | $('li:contains('john')') |

##  DOM 操作

### 样式操作 .css()

### 属性操作 .attr()

- 获取属性   $('img').attr('src')  获取 img 的 src 属性值
- 设置属性   $('img').attr({src:'text.jpg',alt:'sorry'})
- removeAttr()   $('img').removeAttr('src')   删除 src 属性

### html 代码/文本/值

- 可以取值,设值
- html()   $('p').html()   $("p").html('html 代码')
- text()   $('p').text()   $('p').text('内容')
- value()   $('input').value()   $('input').value('姓名')
- prop()   $('input').prop('checked')   $('input').prop('checked',false

### 类名操作

- addClass(); 向被选元素添加一个或多个类
- removeClass(); 从被选元素删除一个或多个类
- toggleClass(); 对被选元素进行添加/删除类的切换操作
- hasClass(); 判断被选元素是否存在类

### dom 筛选过滤/查找

- eq(index);
- find(); 符合条件的后代节点
- siblings(); 除了自己以外的所有兄弟节点
- children(); 所有孩子节点
- next(); 下一个兄弟节点
- nextAll(); 后面的所有兄弟节点
- nextUntil();后面的兄弟节点,直到...
- prev();上一个兄弟节点
- prevAll();
- prevUntil();
- parent(); 父节点
- parents(); 所有父节点
- parentsUntil();

### 自定义动画

$(selector).animate(styles,speed,ease,callback)

- 第一个参数表示：要执行动画的 CSS 属性（必选）
- 第二个参数表示：执行动画时长（可选）
- 第三个参数表示: 运动函数 'swing'和'linear'
- 第四个参数表示：动画执行完后立即执行的回调函数（可选)



* 隐藏和显示:hide      show
* 淡入和淡出:fadeIn    fadeOut    fadeTo (时间,透明度)
* 滑入和滑出:slideDown    slideUp
* 停止动画stop(stopAll,goToEnd)

* stopAll:是否全部停止动画(停止队列中所有动画),默认 false goToEnd: 是否将停止的动画,停在当前动画的最后一个状态

##### 插入节点

* after()  被选元素之前插入

* before() 之后插入

* append()  在被选元素内部从后面插入  被字句   appendTo() 效果一样  把字句

* prepend()  在被选元素内部从前面插入

* clone() 复制

* $(selector).empty();  清空内部

   $(selector).html(''); 空

   $(selector).remove(); 会把自己也删除

##### bom相关

* offset()   获取元素坐标值 
* position()   自己在具有定位的父元素中的位置。 不能设置
* scrollTop()     元素卷进去的高度



##### on方式

```js
// 事件委托
        // 把li的点击事件 委托给了 ul
        $('ul').on('click', 'li', function () {
            // this 指向 ul ,不加过滤元素('li')
            // 加上'li' ,之后 this  指向 点击的 那个 li
            console.log(this);
            console.log($(this).text());
        })
.off()方法移除用.on绑定的事件处理程序
.off(); 不写参数   解除所有绑定的事件
```

#### 事件对象 Event

- event.data 传递给事件处理程序的额外数据
- event.currentTarget 事件绑定的对象(事件源),和 this 相同
- event.pageX 鼠标相对于文档左部边缘的位置
- event.target 实际触发事件的对象，不一定===this
- event.stopPropagation()； 阻止事件冒泡
- event.preventDefault(); 阻止默认行为
- event.type 事件类型：click，mouseover…
- event.which 鼠标的按键类型：左 1 中 2 右 3
- event.keyCode 键盘按键代码

##### each

* each  类似于 数组的 forEach 方法
* .each(index,item)

