《javascript经典实例》
======

## 第7章  处理事件

- [7-1 捕获鼠标电机王诶之并将元素移动到该位置 兼容所有](template/7-1.html)

- 创建一个通用的``停止监听``的函数

    ```js

    // 通用方法
    function stopListening(eventTarget, eventType, eventHandler){

        if(eventTarget.removeEventListener){    // w3c DOM Level 2 - IE8及以下不支持
            eventTarget.removeEventListener(eventType, evnetHandler, false);
        }
        else if(eventTarget.detachEvent){   // Microsoft 版本
            eventType = 'on' + eventType;
            eventTarget.detachEvent(eventType, eventHandler);
        }
        else {  // DOM Level 0
            eventTarget['on' + eventType] = null
        }
    }


    // 使用
    // stopListening(目标对象, 事件, 事件处理函数)
    stopListening(document.getElementById("test"), "click", func);

    ```

- 在一个事件传播到其他元素之前，需要``取消事件``，例如表单提交

    ```js

    // 通用方法
    function cancelEvent(event){

        if(event.preventDefault){   // DOM Levle2
            event.preventDefault();
        } else {    // DOM Level0
            event.returnValue = false;
        }
    }

    // 使用
    function validateForm(evt){
        
        evt = evt || window.event;
        cancelEvent(evt);

    }

    ```

- 一个元素嵌套在另外一个元素，``阻止事件从内部元素向上冒泡或传播到外围``

    ```js

    // 通用方法
    function cancelPropagation(event){

        if(event.stopPropagation){   // firefox chrome safari opera
            event.stopPropagation();
        } else {    // IE
            event.cancelBubble = true;
        }
    }

    // 使用
    cancelPropagation(event);

    ```

- 捕获textarea键盘获得转码

    ```js

    var inputTextarea = document.getElementById('source');

    // keypress 跟在 keydown之后， 表示输入的字符
    listenEvent(inputTextArea, "keypress", processKeyStroke);

    function processKeyStroke(evt){

        evt = evt || window.enent;
        
        // IE/opera 支持 keyCode; chrome/firefox/safari 支持 charCode;
        var key = evt.charCode || evt.keyCode;
        
        // 检查字符是否是ASCII 38 或者是一个&
        if(key == '38'){

            // do something

        }
    }

    ```


- [7-2 阻止一个时间在嵌套元素之间传播 P138](template/7-2.html)

- [7-3 根据键盘的ASCII值阻止一个键盘值 P142](template/7-3.html)

- [7-4 使用新的HTML5拖放 P143](template/7-4.html)