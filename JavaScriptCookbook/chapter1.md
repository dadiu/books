《javascript经典实例》
======

# 第1章  使用Javascript字符

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
                return this.replace(/(^\s*)|(\s*$)/g, '');
            }
        }

- 自定义左去除空格

        if(typeof String.trimLeft == 'undefined'){
            String.prototype.trimLeft = function(){
                return this,replace(/^\s+/, '');
            }
        }

- 自定义右去除空格

        if(typeof String.trimRight == 'undefined'){
            String.prototype.trimRight = function(){
                return this,replace(/\s+$/, '');
            }
        }

