#### 事件三要素

```js
<body>
	<div id="box1"></div>

	<script type="text/javascript">
		// 1、获取事件源
		var div = document.getElementById("box1");
		// 2、绑定事件
		div.onclick = function() {
			// 3、书写事件驱动程序
			alert("我是弹出的内容");
		};
	</script>
</body>
```

#### 常见事件

* 鼠标双击:ondblclick

* 鼠标进入: onmouseenter

* 鼠标离开: onmouseleave

* 鼠标按下: onmousedown
* 鼠标松开:onmouseup

* 鼠标移动: onmousemove

* 鼠标松开: onmouseup

* 按下键盘: onkeydown

* 键盘弹起: onkeyup
* 输入框获得焦点:onfocus
* 输入框失去焦点:onblur
* 文本被选定:onselect
* 键盘按住:onkeypress

#### onload事件

###### window.onload = function () {} 页面加载完成时触发onload事件



#### 获取事件源

```js
var div1 = document.getElementById("box1"); //方式一：通过id获取单个标签

var arr1 = document.getElementsByTagName("div"); //方式二：通过 标签名 获得 标签数组，所以有s
var arr1 = document.getElementsByTagName("div")[0]; //获取数组第一个元素

var arr2 = document.getElementsByClassName("hehe"); //方式三：通过 类名 获得 标签数组，所以有s
```

#### 修改标签样式(事件驱动程序)

` div1.style.backgroundColor = "red";`

- 写属性值时，要用引号
- 写属性名时，是`backgroundColor`.
- this.style.display = 'none';  隐藏   this指向调用者

#### DOM：Document Object Model，文档对象模型。

##### 获取节点

* 父节点`.parentNode`

（1）nextSibling：

- 火狐、谷歌、IE9+版本：都指的是下一个节点（包括标签、空文档和换行节点）。
- IE678 版本：指下一个元素节点（标签）。

（2）nextElementSibling：

- 火狐、谷歌、IE9+版本：都指的是下一个元素节点（标签）。

`下一个兄弟节点 = 节点.nextElementSibling || 节点.nextSibling;`



* previousSibling上一个兄弟  nextSibling下一个兄弟
* firstChild   lastChild    children  childNodes
* **.nodeType == 1 表示的是元素节点**（标签） 。记住：元素就是标签。
* .nodeType == 2 表示是属性节点。
* .nodeType == 3 是文本节点。
* .nodeType == 8 注释节点

#### dom节点操作

##### 创建节点

```html
var a1 = document.createElement("li"); //创建一个li标签
```

##### 插入节点

* 父节点.appendChild() 作为子节点插入到 父节点的末尾

```javascript
box.appendChild(imgEl);
```

* 父节点.insertBefore(新的子节点, 作为参考的子节点)

```javascript
box.insertBefore(pEl, imgEl); 
```

* 删除节点 父节点.removeChild();

* 复制节点.cloneNode()); // 只复制标签本身

* 复制节点.cloneNode(true)); // 包含子节点(内容) 深复制

#### 修改属性

```javascript
myNode.src = "images/2.jpg"; //修改src的属性值
元素节点.setAttribute(属性名, 新的属性值);
myNode.setAttribute("src", "images/3.jpg");
删除
myNode.removeAttribute("class");
DOM 对象的属性和 HTML 的标签属性几乎是一致的。例如：src、title、className、href 等。
```

#### DOM 扩展 (H5)

1. 获取元素

   `document.querySelector(" ")` html5 新选择器，参数是 css 选择器参数,选择选中的第一个

   `document.querySelectorAll(" ")` 选择多个

2. 类名操作

- `Node.classList.add('class')` 添加 class
- `Node.classList.remove('class')` 移除 class
- `Node.classList.toggle('class')` 切换 class，有则移除，无则添加
- `Node.classList.contains('class')` 检测是否存在 class 非常好用 但是出现的太晚了 。。。

#### 定时器

- setTimeout(); 延迟执行
- setInterval(); 循环执行
- clearTimeout(); 清除延迟执行的定时器
- clearInterval(); 清除循环执行的定时器

#### 事件监听器

addEventListener    true 代表捕获，false 代表冒泡。

```javascript
d1.addEventListener('click',function(){
    alert('d1);
},true)
```


```javascript
移除绑定必须一一对应
d2.addEventListener("click", foo, false);
d2.removeEventListener("click", foo, false);
function foo() {
	alert("d2");
}
```

