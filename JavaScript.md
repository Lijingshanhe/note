#### String  Number  Boolean  undefined未定义  null空值  Object

##### 当变量为null时  typeof返回值为object

```
        // 情况一： 数字-- > 布尔。 除了0和NaN， 其余的都是true。

        // 情况二： 字符串-- - > 布尔。 除了空串， 其余的都是true。

        // 情况三： null和undefined都会转换为false。

        // 情况四： 对象也会转换为true。
        console.log(Boolean(' ')); // true
        console.log(Boolean(-1)); // true
        console.log(Boolean(0)); // false
        console.log(Boolean(NaN)); // false
        console.log(Boolean(undefined)); // false
        console.log(Boolean(null)); // false
        console.log(Boolean('')); // false
```

###### parseFloat()和 parseInt()的作用类似，不同的是，parseFloat()可以获得有效的小数部分。





### Date和Math对象

- `getDate()` **获取日 1-31**

- `getDay()` **获取星期 0-6**（0 代表周日，1 代表周一）

- `getMonth()` **获取月 0-11**（0 代表一月）

- `getFullYear()` 获取年份

- `getHours()` 获取小时 0-23

- `getMinutes()` 获取分钟 0-59

- `getSeconds()` 获取秒 0-59

- `getMilliseconds()` 获取毫秒 （1s = 1000ms）

- getTime() 获取时间戳 1970年1月1日，0时0分0秒

- Math.abs() 范围绝对值

- Math.floor() 向下取整

- Math.ceil() 向上取整

- Math.round() 四舍五入取整(负数五舍六入)

- Math.random() 生成0-1之间的随机数

- Math.max(x,y,z) 返回最大值

- Math.min(x,y,z)返回最小值

- Math.pow(x.y)返回x的y次幂

- Math.sqrt() 对一个数进行开方

  ### switch语句

  ```js
          var nowDate = new Date();
          var weekDay = nowDate.getDay();
          switch (weekDay) {
              case 1:
                  console.log('周一');
                  break;
              case 2:
                  console.log('周二');
                  break;
              case 3:
                  console.log('周三');
                  break;
              case 4:
                  console.log('周四');
                  break;
              case 5:
                  console.log('周五');
                  break;
              default:
                  console.log('周末');
                  break;
          }
  
  
          // 注意的 一个点   break 退出 switch 语句
  
          //  break  不能省略
  ```

  ### while语句

  ```js
          // 当符合条件时 就执行
          var num = 100;
          while (num > 0) {
              console.log(num);
              num--;
          }
  
          // do..while
          do {
              console.log(num);
              num--;
          } while (num > 0)
  
          // do  while  至少执行一次,第一次 不管条件符不符合  都要执行
          do {
              console.log(num);
              num++;
          } while (num < 100)
  
          while (num < 100) {
              console.log(num);
              num++;
          }
  ```

  

  ### break

  - break 可以用来退出 switch 语句或**整个**循环语句（循环语句包括 for、while）。

  - break 会立即终止离它**最近**的那个循环语句。

  ### continue

  - continue 可以用来跳过**当次**循环。
  - 同样，continue 默认只会离他**最近**的循环起作用。 





## 数组

* 字面量定义:直接创建 `var arr=[1,2,3];   var  arr=['小明','小红','小白'];`
* 对象定义(数组的构造函数) `var arr = new Array();`
* 如果**参数为空**，则表示创建一个空数组；参数位置是**一个数值**时，表示数组长度；参数位置是**多个数值**时，表示数组中的元素。

##### 数组的基本方法

* for循环 遍历数组

* `forEach`遍历数组

* ```js
          var arr = [1, 3, 5, 7];
          // 这个方法的参数 是一个函数(回调函数)
          arr.forEach(function (item, index, array) {
              // 回调函数当中 有三个参数
              // 第一个参数  遍历的这个元素值
              // 第二个参数  遍历元素的下标
              // 第三个参数  正在遍历的数组
              console.log(item);
          })
  ```

* 

* `push()`：向数组的**最后面**插入一个或多个元素，返回结果为**该数组新的长度**

* `pop()`：删除数组中的**最后一个**元素，返回结果为**被删除的元素**。

* `unshift()`：在数组**最前面**插入一个或多个元素，返回结果为**该数组新的长度**。

* `shift()`：删除数组中的**第一个**元素，返回结果为**被删除的元素**

* `concat()`：连接两个或多个数组，返回结果为**新的数组**。（不会改变原数组）

* `join()`：将数组转换为字符串，返回结果为**转换后的字符串**（不会改变原来的数组）。

* 补充：`join()`方法可以指定一个**字符串**作为参数，这个字符串将会成为数组中元素的**连接符**；如果不指定连接符，则默认使用 `,` 作为连接符，此时和 `toString()的效果是一致的`。

* `split()`：通过指定分隔符，如果省略，默认以逗号分隔，将字符串分割为字符串数组。

* search(): 搜索字符串中是否有符合条件的内容,搜索到会出现索引.

* match():将符合条件的内容提取出来.

* replace():索引到内容替换

#### 正则表达式

直接语法: /pattern/attribute    字符串  属性  i不区分大小是g全局匹配  m多行匹配

创建 RegExp 对象: new RegExp(pattern,attribute);   

[^ A-z]     /丨/       ^除了A-z的

量词 /a{n}/   代表n个a    /(ab){n}/      {m,n}出现m到n次    {m,}m以上次

/ab+c/    n+   至少一次 相当于{1,}

n*	    0个或多个  相当于{0,}  有没有都行

n?	      一个或没有  {0,1}

/^a/   匹配a开头的

/a$/   匹配a结尾的



\  转义字符 如上基本符号匹配都需要转义字符  如 \*  表示匹配*号

\w 表示英文字母和数字  \W  非字母和数字

\d  表示数字  \D  非数字

\s  空格



提取信息中的网络链接：(h|H)(r|R)(e|E)(f|F) *= *('|")?(\w|\\|\/|\.)+('|"| *|>)?

提取信息中的邮件地址：\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*

提取信息中的图片链接：(s|S)(r|R)(c|C) *= *('|")?(\w|\\|\/|\.)+('|"| *|>)?

提取信息中的IP地址：(\d+)\.(\d+)\.(\d+)\.(\d+)

提取信息中的中国手机号码：(86)*0*13\d{9}

提取信息中的中国固定电话号码：(\d3,4|\d{3,4}-|\s)?\d{8}

提取信息中的中国电话号码（包括移动和固定电话）：(\d3,4|\d{3,4}-|\s)?\d{7,14}

提取信息中的中国邮政编码：[1-9]{1}(\d+){5}

提取信息中的浮点数（即小数）：(-?\d*)\.?\d+

提取信息中的任何数字 ：(-?\d*)(\.\d+)? 

IP：(\d+)\.(\d+)\.(\d+)\.(\d+)

电话区号：/^0\d{2,3}$/

腾讯QQ号：^[1-9]*[1-9][0-9]*$

帐号(字母开头，允许5-16字节，允许字母数字下划线)：^[a-zA-Z][a-zA-Z0-9_]{4,15}$

中文、英文、数字及下划线：^[\u4e00-\u9fa5_a-zA-Z0-9]+$



## 函数

* function：是一个关键字。中文是“函数”、“功能”。
* 具名函数:  `function 函数名(){}`
* 匿名函数: `var  foo = function(){};`
* 立即执行函数:`; (function  arr(){console.log(i)}) ();`
* return 后的值将会作为函数的执行结果返回，可以定义一个变量，来接收该结果。
* 返回值可以是任意的数据类型，可以是对象，也可以是函数。

#### fn()和fn的区别[重要]

- `fn()`：调用函数。相当于获取了函数的返回值。
- `fn`：函数对象。相当于直接获取了函数对象。



### 对象

##### 创建对象

* 使用对象字面量创建一个对象 ` var obj={name:'张三',age:'22',sex:'男'};`

* 使用 new 关键字调用的函数，是构造函数 constructor。**构造函数是专门用来创建对象的函数**。

* `var obj = new Object();`

* 给对象添加,修改,追加属性:  `对象.属性名=属性值`

* 删除: `delete obj.name`

* 通过构造函数Object, new 出来一个实例对象,构造函数首字母大写,专门用来造对象

* ```js
     function Student(name, sex) {
          this.level = '1911';
          this.room = '1803';
          this.name = name;
          this.sex = sex;
          this.say = function () {
              alert(this.name)
          }
      }
        	var s1 = new Student('张三', '男');
      var s2 = new Student('小红', '女');
      console.log(s1);
      console.log(s2);
      s1.say();
      // new  到底做了什么 
      // 1 . 创建了一个空对象{} ,将this指向这个空对象
      // 2.  执行构造函数中的代码  {level:'1911',room:'1803',name:'张	三',sex:'男',say:function(){alert(this.name)}
      // 3.  把这个 return  出去
      // 4. s3 接收了这个对象
        
      // 总结this 指向问题
      // 1. 指向(最后)调用者
      // 2. 构造函数当中的this指向 new出来的 实例对象
      // 3. 可以通过一些方法强行修改this 的指向,比如 (apply/bind/call)
  ```

#### 遍历对象for  in

```js
for (var key in user) {
	//xx.xx 这种形式 只能取原来具有的属性
	//非常重要! xx.abc  abc是变量,就必须通过  xx[abc] 形式取值
	console.log("属性" + key + "==>" + user[key]);
}
```



#### JOSN

* JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。 JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串

* ```js
      var movie={}
      var movieJson = JSON.stringify(movie); // 把普通对象 转换成 json 字符串
      console.log(movieJson);
      // 后台拿到数据 json 字符串,需要变回对象 在进行使用
      var newMovie = JSON.parse(movieJson);
      console.log(newMovie);
  
      var str = '{"a": "Hello","b": "World"}';
      // 只有json格式字符串才能变回对象
      console.log(JSON.parse(str));
  ```

#### 数组和字符串常用方法

##### 数组

* `reverse()`：反转数组，返回结果为**反转后的数组**（会改变原来的数组）
* `slice()`：从数组中提取指定的一个或者多个元素，返回结果为**新的数组**（不会改变原来的数组）。
* `splice()`：从数组中**删除**指定的一个或多个元素，返回结果为**新的数组**（会改变原来的数组，会将指定元素从原数组中删除）。
* `indexOf(value)：从前往后索引，获取 value 在数组中的第一个下标。`
* `lastIndexOf(value) ：从后往前索引如果没找到则返回`
* `sort()`：对数组的元素进行从小到大来排序（会改变原来的数组）。
* 如果在使用 sort() 方法时不带参，则默认按照**Unicode 编码**，从小到大进行排序。
* 浏览器根据回调函数的返回值来决定元素的排序：（重要）
  - 如果返回一个大于 0 的值，则元素会交换位置
  - 如果返回一个小于 0 的值，则元素位置不变
  - 如果返回一个 0，则认为两个元素相等，则不交换位置

```js
var arr3 = [5, 2, 11, 3, 4, 1];

// 自定义排序规则
var result = arr3.sort(function(a, b) {
	return a - b; // 升序排列
	// return b - a; // 降序排列
});

console.log("arr3 =" + arr3); // [1,2,3,4,5,11]
console.log("result =" + result); // [1,2,3,4,5,11]
```



##### 字符串

```
// toUpperCase() 转成大写
// toLowerCase() 转成小写
// charAt() 获取相应位置的字符
// charCodeAt() 指定位置字符 的 Unicode 编码
// indexOf() 返回字符在字符串中的位置
// lastIndexOf()  从后找
// concat() 连接字符串
// slice() 提取字符串的某个部分
// substr() 截取字符串 第一个参数 起始位置,第二个参数 表示截取的个数
```











