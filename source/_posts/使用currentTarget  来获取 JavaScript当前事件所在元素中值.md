title:  使用currentTarget  来获取 JavaScript当前事件所在元素中值
date:  2018年1月2日 22点11分
tags: 
- JavaScript 
categories:
- JavaScript  
# 使用currentTarget  来获取 JavaScript当前事件所在元素中值
  在使用JavaScript时候，可能会遇到使用css来注册一个事件。当用css注册事件的时候，可能由于每个元素所传值不一样，需要分别去读。这时候，可以考虑把元素的值放入到元素id或者其他attribute中去。 例如如下代码段
```javascript
$(".dialog").button().on("click", function (event) {
        id = ""+event.currentTarget.id+"";
        console.log(event);
        dialog1.dialog("open");
    });
```
   我将所有的dialog的class按钮全部注册了一个click事件，但是我又想读出每个dialog按钮中的id值。这时候可以使用event.currentTarget.id 来获取当前元素的id。
   同理当我把这个event输入一下看结果可以看到。currentTarget可以把a标签中所有所包含的值全部滤出来。**currentTarget 事件属性返回其监听器触发事件的节点，即当前处理该事件的元素、文档或窗口。**

```json
currentTarget:
a#54240251119403008.ml10.btn.smallbtn.btn-y.dialogform-1.ui-button.ui-corner-all.ui-widget
accessKey:""
assignedSlot:null
attributes:NamedNodeMap {0: class, 1: title, 2: href, 3: id, 4: role, class: class, title: title, href: href, id: id, role: role, …}
baseURI:"http://127.0.0.1:8086/hou/order/list/company"
charset:""
childElementCount:0
childNodes:NodeList [text]
children:HTMLCollection []
classList:DOMTokenList(8) ["ml10", "btn", "smallbtn", "btn-y", "dialogform-1", "ui-button", "ui-corner-all", "ui-widget", value: "ml10 btn smallbtn btn-y dialogform-1 ui-button ui-corner-all ui-widget"]
className:"ml10 btn smallbtn btn-y dialogform-1 ui-button ui-corner-all ui-widget"
clientHeight:16
clientLeft:1
clientTop:1
clientWidth:52
contentEditable:"inherit"
coords:""
dataset:
DOMStringMap {}
dir:""
disabled:
false
download:""
draggable:true
firstChild:text
firstElementChild:null
hash:""
hidden:false
host:""
hostname:""
href:"javascript:void(0)"
hreflang:""
id:"54240251119403008"
innerHTML:"去联系"
innerText:"去联系"
isConnected:true
isContentEditable:false
jQuery11110905568812459252:85
lang:""
lastChild:text
lastElementChild:null
localName:"a"
name:""
```



