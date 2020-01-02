## BOM browser

#### 三大家族其一 `Offset` 家族  scroll  client

> 家族成员： `offsetWidth` `offsetHeight` `offsetLeft` `offsetTop` `offsetParent`

##### `offsetWidth`  `offsetHeight`  （检测盒子自身宽高）

> 这两个属性，他们绑定在了所有的节点元素上。获取之后，只要调用这两个属性，我们就能够获取元素节点的宽和高。

>` offset宽/高  =  盒子自身的宽/高(width/height) + padding +border`

##### `offsetLeft`  和  `offsetTop`  （检测距离有定位的父盒子的左/上面的距离）

> 如果父级都没有定位则以 `body` 为准, `offsetLeft` 从父亲的 `padding` 开始算,父亲的 `border` 不算。
> 在父盒子有定位的情况下，`ele.offsetLeft == ele.style.left`(去掉 px)

##### `offsetTop/Left` 和 `style.top/left` 的区别：

1. `ele.style.xxx`只能获取行内样式设置的值，并不一定是实际值。

   ```html
   <!-- eg -->
   <div id="box" style="top: 200px"></div>
   
   <script>
   	console.log(box.style.top); // "200px"
   	console.log(box.offsetTop); // 0
   </script>
   ```

2. `offsetTop/Left` 只读，而 `style.top/left` 可读写。（只读是获取值，可写是赋值）

3. `offsetTop/Left` 返回的是整数，而 `style.top/left` 返回的是字符串，除了数字外还带有单位：`px`

```js
<div class="d1" style="position:relative;width: 300px;height: 200px;background-color: green;"></div>
<script>
	var d1= document.getElementsByClassName('d1')[0];
	d1.onclick = function(){
		d1.style.width = '400.499999999999999px';
		console.log(d1.offsetWidth);	// 401
		console.log(d1.style.width);	// "400.5px"
		d1.style.top = "50.49999999999999px";
		console.log(d1.style.top)	// "50.5px"
		console.log(d1.offsetTop)	// 51
	}
</script>
```

##### `offsetParent`   （检测父系盒子中带有定位的父盒子节点）

返回该对象带有定位的父类

> 1、如果当前元素的父级元素没有进行 CSS 定位(absolute,relative,fixed) `offsetParent` 为 `body`
> 	
>2、如果当前元素的父级元素中有 CSS 定位 `offsetParent` 取最近的那个父级元素。

#### 动画和封装

1. 动画的种类
	+ 闪现动画（被淘汰）
	+ 匀速动画
	+ 缓动动画

2. 动画原理
	+ 物体运动： 起点，终点，速度（距离/时间）
	+ 盒子的位置 = 盒子本身所在的位置 + 步长

> 缓动动画计算方式：
> leader = leader + (target - leader) / 10;
> 
> 起点 = 起点 + (终点 - 起点) / 10;

```js
// 匀速动画的封装
function averageMove(ele,target,step){
    // 如果起点等于终点,直接返回,不执行函数
    if(ele.offsetLeft === target) return;
    
	// 先清除上一个元素上绑定的定时器   防止定时器冲突
	if(ele.timer) clearInterval(ele.timer);
    
	// 先写定时器
	ele.timer = setInterval(function (){
		// 起点 style.left 只能获取行内样式 , 获取到的值是 "56px"
		var start = ele.offsetLeft;
		// 步长  需要判断方向，注意这里不能写var step
		step = target > start ? Math.abs(step) : -Math.abs(step);
		// 运动 运动距离 = 起点 + 步长
		ele.style.left = start + step + "px";
		// 需要停止定时器的条件  终点与起点的距离 <= 步长
		if(Math.abs(target - start) <= Math.abs(step)){
			clearInterval(ele.timer);
			// 直接到终点
			ele.style.left = target + "px";
		}
	},17)
}
```

```js
// 缓动动画封装
function move(ele,target){
    // 如果起点等于终点,直接返回,不执行函数
    if(ele.offsetLeft === target) return;
    
    // 先清除上一个元素上绑定的定时器   防止定时器冲突
    if(ele.timer) clearInterval(ele.timer);
    
    // 给元素绑定定时器
    ele.timer = setInterval(function(){
        // 设置起点
        var start = ele.offsetLeft;
        // 设置步长
        var step = (target - start)/10;
        // 判断步长区间 (-1,1)
        if(Math.abs(step) < 1){
            // 0<step<1 取1
            // 0>step>-1 取-1
            step = step > 0 ? 1 : -1;
        }
        // 运动
        ele.style.left = start + step + "px";
        // 判断停止条件
        if(start + step === target){
            // 清除定时器
            clearInterval(ele.timer);
        }
    },1000/60)
}
```

