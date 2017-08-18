《javascript经典实例》
======

## 第5章  使用数组和循环

- sort() 正序排列，可传入方法

- reverse() 反转数组

- silce() 可创建数组的一个子集，这是从一个数组复制一个子集的一种快速方法，如果值是对象，确保两个数组都是同步的，IE8不支持

- splice(index,howmany,item1,.....,itemX) 可删除从 index 处开始的零个或多个元素，并且用参数列表中声明的一个或多个值来替换那些被删除的元素。

- indexOf() / lastIndexOf() 可在数组中搜索元素，返回索引，IE8不支持
    + 自定义 indexOf

            if(!Array.prototype.indexOf){
                Array.prototype.indexOf = function(elt /* , from*/){

                    var len = this.length >>> 0;

                    var from = Number(arguments[1]) || 0;
                     
                    from = (from < 0) ? Math.ceil(from) : Math.floor(from);

                    if(from < 0) {
                        from += len;
                    };

                    for(; from < len; from ++){

                        if(from in this && this[from] === elt){
                            return form;
                        }
                    };

                    return -1;
                }
            }


- forEach(数组元素, 元素索引, 数组) 改变原来的数组，无返回，IE8不支持
    + 自定义 forEach

            if(!Array.prototype.forEach){

                Array.prototype.forEach = function(fun /* , thisp */){

                    var len = this.length >>> 0;

                    if(typeof fun !== 'function'){
                        
                        throw new TypeError();

                    }

                    var thisp = arguments[1];

                    for(var i; i < len; i++){

                        if(i in thisp){
                            fun.call(thisp, this[i], i, this);
                        }
                    }
                }
            }


- map(数组元素, 元素索引, 数组) 不改变原来的数组，返回新数组，IE8不支持
    + 自定义 map

            if(!Array.prototype.map){

                Array.prototype.map = function(fun /* , thisp */){

                    var len = this.length >>> 0;

                    if(typeof fun != 'function'){
                        
                        throw new TypeError();

                    }

                    var res = new Array(len);
                    var thisp = arguments[1];

                    for(var i = 0; i < len; i++){

                        if( i in this){

                            res[i] = fun.call(thisp, this[i], i, this);
                        }
                    }

                    return res;
                }
            }


- filter(数组元素, 元素索引, 数组)  过滤数组中的元素值，并且把结果赋给一个新的数组，IE8不支持

    + 实例

            function removeChars (element, index,array){

                return (element !== "**")

            };

            var charSet = new Array("**", "bb", "cc", "dd", "**", "ee", "**");

            var newArray = charSet.filter(removeChars);
            console.log(newArray);

    + 自定义

            if(!Array.prototype.filter){

                Array.prototy.filter = function(fun, /* , thisp */){

                    var len = this.length >>> 0;

                    if(typeof fun !== 'function'){

                        throw new TypeError();
                    }

                    var res = new Array();
                    var thisp = arguments[1];
                    for(var i; i < len; i++){

                        if( i in this ){
                            
                            var val = this[i];
                            fun.call(thisp, val, i, this){

                                res.push(val)
                            }
                        }
                    }

                    return res;

                }
            }

- every() 检查符合给定条件的每个元素，只要该函数返回一个false值，处理就会结束，并且该方法返回一个false; IE8不支持 p98

- some() 检查至少某些元素符合该条件 p99