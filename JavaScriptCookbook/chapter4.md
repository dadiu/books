《javascript经典实例》
======

## 第4章  使用Number和Math

- 使用Number对象的toString()方法，可将十进制转换为二进制、八进制（前面加0）、十六进制（前面加0x），括号内只有八进制、十六进制、十进制数字可以作为数字直接操作

- parseInt() 返回整数；parseFloat() 返回浮点数

- 生成0~256之间的随机数(Math.floor 向下取整)
        
         Math.floor(Math.random() * 256)

- 生成min~max之间的随机数

        Math.floor(Math.random() * (max - min + 1)) + min

- 生成随机RGB格式颜色(IE7不支持)

        function colorPack(num){

            return Math.floor(Math.random() * (num + 1))

        }

        function randomColor(){

            return "rgb(" + colorPack(255) + "," + colorPack(255) + "," + colorPack(255) + ")";
        }

        randomColor();

- 生成随机16进制格式颜色

        function colorPack(num){

            return Math.floor(Math.random() * (num + 1)).toString(16);

        }

        function randomColor(){

            var colorArr = [colorPack(255), colorPack(255), colorPack(255)];
            var i = 0;
            var endColr = '#';

            for(; i < 3; i++){

                if(colorArr[i].length < 2){
                    colorArr[i] = '0' + colorArr[i];
                }

                endColr += colorArr[i];
            };

            return endColr;
        }

        randomColor();


- [4-1 将表格值转为数字，并且求得加和结果](template/4-1.html)
- document.querySelectAll() : IE8以下不支持

- 角度转弧度

        var radians = degress * (Math.PI / 180);

- 弧度转角度

        var degress = radians * (180 / Math.PI);

- 找圆心，计算半径

        // 圆心
        var Point = [width / 2, height / 2]; 
        
        // 半径
        var R = Math.min(width, height)/2;


- [4-2 将一个SVG圆放入到一个div元素中](template/4-2.html)

 
+ getComputedStyle 是一个可以获取当前元素所有最终使用的CSS属性值。返回的是一个CSS样式声明对象([object CSSStyleDeclaration])，只读，只能获取样式，不能设置。兼容IE9及以上。

    + 语法(Gecko 2.0 (Firefox 4 / Thunderbird 3.3 / SeaMonkey 2.1) 之前，第二个参数“伪类”是必需的（如果不是伪类，设置为null），不过现在嘛，不是必需参数了。)
        
                var style = window.getComputedStyle("元素", "伪类");

    +  实例

                var dom = document.getElementById("testId");
                var style = window.getComputedStyle(dom, ":after");


    + getPropertyValue方法可以获取CSS样式申明对象上的属性值（直接属性名称），兼容IE9及以上。

                window.getComputedStyle(element, null).getPropertyValue("float");

+ currentStyle 是IE浏览器自娱自乐的一个属性，其与element.style可以说是近亲，至少在使用形式上类似，element.currentStyle，差别在于element.currentStyle返回的是元素当前应用的最终CSS属性值（包括外链CSS文件，页面中嵌入的&lt;style>属性等）。因此，从作用上将，getComputedStyle方法与currentStyle属性走的很近，形式上则style与currentStyle走的近。不过，currentStyle属性貌似不支持伪类样式获取，这是与getComputedStyle方法的差异，也是jQuery css()方法无法体现的一点。

    + 语法

            elem.currentStyle[style_name]

    + 实例
    
            alert((element.currentStyle? element.currentStyle : window.getComputedStyle(element, null)).height);

- [参考地址](http://www.zhangxinxu.com/wordpress/2012/05/getcomputedstyle-js-getpropertyvalue-currentstyle/)

