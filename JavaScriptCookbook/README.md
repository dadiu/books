《javascript经典实例》
======

# 第1章 使用Javascript字符

## 1.6 检查一个存在的、非空字的字符串

    if((typeof unknown != 'undefined') && 
        (unknow.valueOf() == 'string') &&
        (unknow.length > 0)){
            console.log("success")
        }

- typeof 运算符返返回一个变量的类型

    变量类型                            | 返回
    --|--
    数字                              |   'number'
    字符串                            |   'string'
    布尔                              |      'boolean'
    函数                              |       'function'
    null/数组/其他javascript对象       |       'object'
    未定义                             |       'undefined'


## 1.10 去除字符串周围的空白

方法             |       说明
--|--
trim()          |       去除周围所有空白
trimLeft()      |       去除左边空白
trimRight()     |       去除右边空白

- IE8及以下不支持trim，自定义trim方法

        if(typeof String.trim == 'undefined'){
            String.prototype.trim = function(){
                return this,replace(/(^\s*)|(\s*$)/g, '');
            }
        }



# 第2章 使用正则表达式

- 正则方法对比

方法名             |   说明      |   返回
--|--|--
reg.test()          |   查找对应的字符串中是否存在       |   Boolean
reg.exec()          |   RegExp对象的方法，查找并返回当前匹配的结果。返回数组有3个属性:index（当前匹配项的位置）；lastIndex(当前匹配项结束的位置,即index+当前匹配的长度)；input(需要匹配的对象)  | 不存在返回null，存在则返回长度为1的数组
reg.match()         |   String对象的方法，查找并返回所有匹配的结果    |   不存在返回null，存在返回长度为所有匹配项的数组

## 2.4 查找一个模式中的所有实例，以t开头以e结尾,中间可以有多个字符的单词或其他文本

        var str = 'this is a template, this is the time and that is the time';
        var pattern = /t\w*e/g;
        var matchStr = null;
        var endStr = '';

        while((matchStr = pattern.exec(str)) != null){

            endStr = 'at: ' + matchStr.index + '. we found : ' + matchStr[0];
            console.log(endStr);
        }


- [eq: 2-1 使用exec和全局标志来查找并突出显示一个文本字符串中的所有匹配](template/2-1.html)

## 2.5 使用新字符串替换所有匹配的子字符串

    var searchStr = "now is the time, this is the time";
    var reg = /t\w{2}e/g;
    var resultStr = searchStr.replace(reg, 'place');
    console.log(resultStr);

