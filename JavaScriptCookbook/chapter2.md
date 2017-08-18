《javascript经典实例》
======

## 第2章  使用正则表达式

- 正则方法对比

    方法名             |   说明      |   返回
    --|--|--
    reg.test()          |   查找对应的字符串中是否存在       |   Boolean
    reg.exec()          |   RegExp对象的方法，查找并返回当前匹配的结果。返回数组有3个属性 : <br/>index : 当前匹配项的位置；<br/>lastIndex : 当前匹配项结束的位置,即index+当前匹配的长度；<br/>input : 需要匹配的对象(百度说必需在g的情况下才会有，但做例子的时候并没有这key的出现)  | 不存在返回null，<br/>存在则返回长度为1的数组
    reg.match()         |   String对象的方法，查找并返回所有匹配的结果    |   不存在返回null，<br/>存在返回长度为所有匹配项的数组

- 查找一个模式中的所有实例，以t开头以e结尾,中间可以有多个字符的单词或其他文本

        var str = 'this is a template, this is the time and that is the time';
        var pattern = /t\w*e/g;
        var matchStr = null;
        var endStr = '';

        while((matchStr = pattern.exec(str)) != null){

            endStr = 'at: ' + matchStr.index + '. we found : ' + matchStr[0];
            console.log(endStr);
        }


- 使用新字符串替换所有匹配的子字符串

    var searchStr = "now is the time, this is the time";
    var reg = /t\w{2}e/g;
    var resultStr = searchStr.replace(reg, 'place');
    console.log(resultStr);

- 使用捕获圆括号交换一个字符串中的单词

- eg 2.6-1

    var name = 'Wu Haijing';
    var pattern = /^(\w+)\s(\w+)$/;
    var newName = name.replace(pattern, '$2 $1');
    console.log(newName);

- eg 2.6-2

    var name = 'Wu Haijing';
    var pattern = /^(\w+)\s(\w+)$/;
    var resultName = pattern.exec(name);
    var newName = resultName[2] + ' ' + resultName[1];
    console.log(newName)


- replace()方法说明：

        string.replace(regexp/substr, replacement)
    
    参数 | 描述
    --|--
    regexp/substr | 必需。规定子字符串火药替换的模式的RegExp对象。<br/>如果该值是一个字符串，则将它作为检索的直接量文本模式，而不是首先被转换为RegExp对象
    replacement | 必需。一个字符串值。规定了替换文本或生成替换文本的函数

- 参数replacement章$字符具有特定的含义：

    字符 | 替换文本
    --|--
    $1、$2、... $99 | 插入使用RegExp的第n次捕获圆括号的值
    $' | 在匹配之后插入字符串的一部分
    $` | 在匹配之前插入字符串的一部分
    $& | 插入与RegExp相匹配的子字符串
    $$ | 允许替换中有一个直接量-美元符号$


### eg
- [2-1 使用exec和全局标志来查找并突出显示一个文本字符串中的所有匹配](template/2-1.html)
- [2-2 使用String.replace和特殊模式在字符串中查找文本并突出显示](template/2-2.html)
    + 对比2-1, 2-2未保留换行，2-1保留了
- [2-3 搜索特殊字符](template/2-3.html)