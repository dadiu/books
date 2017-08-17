《javascript经典实例》
======

# 第4章  使用Number和Math

- 使用Number对象的toString()方法，可将十进制转换为二进制、八进制（前面加0）、十六进制（前面加0x），括号内只有八进制、十六进制、十进制数字可以作为数字直接操作

- parseInt() 返回整数；parseFloat() 返回浮点数

## 生成0~256之间的随机数(Math.floor 向下取整)
        
         Math.floor(Math.random() * 256)

## 生成min~max之间的随机数

        Math.floor(Math.random() * (max - min + 1)) + min

## 生成随机RGB格式颜色(IE7不支持)

        function colorPack(num){

            return Math.floor(Math.random() * (num + 1))

        }

        function randomColor(){

            return "rgb(" + colorPack(255) + "," + colorPack(255) + "," + colorPack(255) + ")";
        }

        randomColor();

## 生成随机16进制格式颜色

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


## [4-1 将表格值转为数字，并且求得加和结果](template/4-1.html)
- document.querySelectAll() : IE8以下不支持