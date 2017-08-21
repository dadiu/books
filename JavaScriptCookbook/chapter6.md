《javascript经典实例》
======

## 第6章  使用JavaScript函数构建重要性

### 三种基本函数

- 声明式函数
    + 通过使用function关键字触发的一条语句，并且当JavaScript应用程序初次载入的时候解析。
    
    ```js
    // function functionName(arg0, arg1, ... argN) { statements }
    function test(n1,n2){

        return n1+n2;
        
    }
    ```

- 匿名函数 / 函数构造函数
    + 使用new运算符构造的，并且引用Function对象。它是匿名的，因为它没有给定一个名字，并且访问该函数是通过一个变量或另一个对象属性来进行的。每次访问它的时候解析它。

    ```js

    // 匿名函数 比如 jQuery
    (function($){

        // do something

    })(jQuery);

    // 构造函数  (函数首字母大写)
    // var function_name = new Function(arg1, arg2, ..., argN, function_body); 最后一个参数是函数主体（要执行的代码）
    function Person(name){
        this.name = name;
    };
    var p1 = new Person('Adobe');

    ```


- 函数直接量 / 函数表达式 
    + 和其他JavaScript对象一样，函数可以是对象，也可以是直接量。直接量函数是一个函数表达式，包括参数和函数体，它用于诸如另一个函数的参数中这样的地方。和声明式函数一样，它也只解析一次，即当JvavScript应用程序载入的时候。和创建为一个对象的函数一样，它也是匿名的。

    ```js   
    // var f = function(x){return x*x;};
    var test = function(n1, n2){

        return n1 + n2;
    }
    ```


### eq
- [6-1 标量参数和数组参数的功能性区别 P109](template/6-1.html)
- [6-2 使用匿名函数 P111](template/6-2.html)
- [6-3 实现递归算法 P113](template/6-3.html)
- 6-4 闭包
    + 优点
        1. 保护函数内的变量安全，加强了封装性，达到对变量的保护作用；（设计私有方法和变量）
        2. 逻辑连续，当闭包作为另一个函数调用的参数时，避免你脱离当前的逻辑而单独编写额外的逻辑；
        3. 在内存中维持一个变量
    + 缺点
        1. 常驻内存，会增大内存使用量，使用不当很容易造成内存泄露
    + 不适合场景
        1. 返回闭包的函数是个非常大的函数
    + 实例
    ```js

    function outer(x){

        return function(y){
            return x*y;
        }
    }

    var multiThree = outer(3);
    console.log(multiThree(2));
    console.log(multiThree(3));

    ```