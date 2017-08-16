《编写可维护的javascript》
======


## 第一章

- 缩进
- 句尾封号
- 换行 (1、假如正常缩进为2像素，则换行的缩进为1像素； 2、不要在运算符之前换行)
- 对于函数和方法命名来说，第一个单词为动词
    
   动词     | 含义               
   -------- |-------------       
   can      | 函数返回一个布尔值  
   has      | 函数返回一个布尔值  
   is       | 函数返回一个布尔值 
   get      | 函数返回一个非布尔值 
   set      | 函数用来保存一个值  
   
- 常量用大写字母表示
- 构造函数用大驼峰命名法，使用时前面一定会有new
- number (1、不要省略“小数部分”或“整数部分”； 2、禁止使用八进制、十六进制、科学计数)
- null
    + **最好的方式是将它当做对象的占位符 ( placeholder )**
    + **下列场景应当使用Null**
    +   1、 用来初始化一个变量，这个变量可能赋值一个对象
    +   2、 用来和一个已经初始化的变量比较，这个变量可以是也可以不是一个对象
    +   3、 当函数的参数期望是一个对象时，用作参数传入
    +   4、 当函数的返回值期望是对象时，用作返回值传入
    + **下列场景不应当使用null**
    +   1、 不要用null来检测是否传入了某个参数
    +   2、 不要用null来检测一个未初始化的变量
- undefined
    + 禁止使用特殊值undefined，确保只有一种情况下 typeof 才会返回undefined：当变量未声明时
    + 如果你使用了一个可能（或可能不会）赋值为一个对象的变量时，则将其赋值为null

        | 返回值               
   -------- |-------------       
   typeof null      | object
   typeof undefined      | undefined  
   null == undefined      | true

- 对象直接量，在对象中直接写出所有属性，如下：

                var book = {
                    title : "title name",
                    author : "author name"
                };
                
- 数组直接量，用方括号代替Array构造函数，如下：

                var color = ['red', 'yellow', 'blue'];



---
## 第二章


注释规则，没啥好记录的。。



---
## 第三章

- 所有的块语句都应使用花括号，包括：
    + if; for; while; do...while...; try...catch..finally;
- 严格模式中，width语句是被明确禁止的
- for循环
    + break        不管循环迭代有没有执行完毕，立即退出循环
    + continue     立即退出本次循环，而进入下一次迭代循环
- for...in... 循环
    + 缺点：不近便利对象的实例属性，同时还遍历从原型继承来的属性，当遍历自定义的属性时，往往会因为意外的结果而终止
    + 解决方法：使用 hasOwnProperty() 方法来为for...in...循环过滤出实例属性，例如：

 				var prop;
 				for(prop in object){
 					if(object.hasOwnProperty(prop)){
 						console.log("Property name is " + prop);
 						console.log("Property value is " + object[prop]);
 					};
 				};

    + 注：for...in... 是用于遍历对象的循环，禁止用于遍历数组



---
## 第四章

- 变量声明提前 ： 即与javascript引擎解析这段代码的习惯相似；
- 函数声明提前 ：即与javascript引擎解析这段代码的习惯相似；
    + 注：函数声明不应当出现在语句块之内，如下：
                
                // 不好的写法
                if(condition){
                    function doSonmething(){ };
                } else {
                    functioan doOtherSomething(){ };
                }
     
- 函数调用时，函数名和左括号之间没有间隔（空格）；
- ES5，引入了严格模式，通过添加如下代码：
    + 注：不要在全局使用
  
                "user strict"
        
- 不要使用"==" 和"!="，而应当使用"===" 和 "!=="；
- eval() ： 只有涉及到回调中解析JSON的情形，才可以使用eval()，其他情况均禁止使用
- 禁止使用原始包装类型
  
  
--
## 第五章
- UI定义：
    + HTML  用来定义页面的数据和语义
    + CSS   用来给页面添加样式，创建视觉特征
    + Javascript    用来给页面添加行为，使其更具交互性
- 将JS从CSS中抽离
- 将CSS从JS中抽离（动态定位除外）
- 将JS从HTML中抽离
- 将HTML从JS种抽离（可配给其他模板）


**简单实例-模板**

body

                <ul id=""myList>
                    <script type="text/x-my-template" id="list-item">
                        <li>
                            <a href="%s">%s</a>
                        </li>
                    </script>
                </ul>

Script

                	<script type="text/javascript">
                		// 替换模板
                		function sprintf(txt) {
                			var  i=1, args=arguments;
                			 console.log(args);
                			return txt.replace(/%s/g, function() {
                				return (i < args.length ? args[i++]: '');
                			});
                		};
                
                		// 格式化并插入
                		function addItem(url, txt, b) {
                			// console.log(url);
                			var mylist = document.getElementById('mylist'),
                				script = document.getElementById('list-item'),
                				templateText = script.text,
                				result = sprintf(templateText, url, txt, b),
                				div = document.createElement('div');
                
                				div.innerHTML = result.replace(/^\s*/, '');
                				mylist.appendChild(div.firstChild);
                				//console.log(script.text);
                		};
                
                		// 待扩展遍历替换
                		addItem('/item/4', 'Forth item', 'strong');
                
                	</script>
                	
 "注：待扩展部分 - 遍历数组or对象替换模板"
 
 ---
 ### 第六章
 - 避免使用全局变量
 - 非破坏性的创建命名空间
                
  