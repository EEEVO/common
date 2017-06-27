# 平时累积常用代码,供自己方便

<!-- TOC -->

- [常用js代码](#常用js代码)
  - [BOM](#bom)
    - [判断浏览器](#判断浏览器)
    - [手机类型判断](#手机类型判断)
    - [获取当前js的版本](#获取当前js的版本)
    - [判断浏览器是否支持CSS3属性](#判断浏览器是否支持css3属性)
    - [阻止事件冒泡](#阻止事件冒泡)
    - [加入收藏](#加入收藏)
    - [实现设为首页](#实现设为首页)
    - [JS 弹出新窗口全屏](#js-弹出新窗口全屏)
  - [Array](#array)
    - [js删除数组指定item](#js删除数组指定item)
    - [js删除指定index的item](#js删除指定index的item)
    - [递归遍历数组成员并输出](#递归遍历数组成员并输出)
    - [JS插入排序](#js插入排序)
  - [Js身份证验证函数](#js身份证验证函数)
  - [String](#string)
    - [JS 替换非法字符主要用在密码验证上出现的特殊字符](#js-替换非法字符主要用在密码验证上出现的特殊字符)
    - [Js 去掉空格方法](#js-去掉空格方法)
    - [字符串截取方法](#字符串截取方法)
    - [求一个字符串长度](#求一个字符串长度)
    - [js实现解析URL参数， 返回一个对象](#js实现解析url参数-返回一个对象)
  - [Object](#object)
    - [js实现对象的深Clone](#js实现对象的深clone)
  - [Math](#math)
    - [JS 生成范围随机整数](#js-生成范围随机整数)
  - [DOM](#dom)
    - [移除事件](#移除事件)
    - [回车提交JQ](#回车提交jq)
    - [js实时计算rem,宽度大于1920px时1rem=100px](#js实时计算rem宽度大于1920px时1rem100px)
    - [绑定按钮回车触发单机事件](#绑定按钮回车触发单机事件)
    - [按Ctrl + Entert 直接提交表单](#按ctrl--entert-直接提交表单)
    - [全选 / 全不选](#全选--全不选)
    - [原生JS获取鼠标XY轴的值](#原生js获取鼠标xy轴的值)
    - [JS实现添加事件兼容函数](#js实现添加事件兼容函数)
    - [JS获取某元素以浏览器左上角为原点的坐标(有问题)](#js获取某元素以浏览器左上角为原点的坐标有问题)
    - [JS获取鼠标X.Y轴坐标](#js获取鼠标xy轴坐标)
  - [Date](#date)
    - [JS判断两个日期大小 适合 2012 - 09 - 09 与2012 - 9 - 9 两种格式的对比](#js判断两个日期大小-适合-2012---09---09-与2012---9---9-两种格式的对比)
    - [获取当前时间](#获取当前时间)
    - [JS 执行计时器](#js-执行计时器)
  - [JS写入Cookie](#js写入cookie)
  - [JS 读Cookie](#js-读cookie)
  - [Ajax 请求](#ajax-请求)
  - [JS StringBuilder](#js-stringbuilder)
  - [JS 加载到顶部LoadJS](#js-加载到顶部loadjs)
  - [清空 LoadJS 加载到顶部的js引用](#清空-loadjs-加载到顶部的js引用)
  - [js 动态移除 head 里的 js 引用](#js-动态移除-head-里的-js-引用)
  - [整个UL 点击事件 加在UL里的onclick里](#整个ul-点击事件-加在ul里的onclick里)

<!-- /TOC -->

## BOM

### 判断浏览器

```bash
function getOs() {
  if (navigator.userAgent.indexOf("MSIE 8.0") > 0) {
    return "MSIE8";
  } else if (navigator.userAgent.indexOf("MSIE 6.0") > 0) {
    return "MSIE6";
  } else if (navigator.userAgent.indexOf("MSIE 7.0") > 0) {
    return "MSIE7";
  } else if (isFirefox = navigator.userAgent.indexOf("Firefox") > 0) {
    return "Firefox";
  }
  if (navigator.userAgent.indexOf("Chrome") > 0) {
    return "Chrome";
  } else {
    return "Other";
  }
}
```

### 手机类型判断

```bash
var BrowserInfo = {
  userAgent: navigator.userAgent.toLowerCase(),
  isAndroid: Boolean(navigator.userAgent.match(/android/ig)),
  isIphone: Boolean(navigator.userAgent.match(/iphone|ipod/ig)),
  isIpad: Boolean(navigator.userAgent.match(/ipad/ig)),
  isWeixin: Boolean(navigator.userAgent.match(/MicroMessenger/ig)),
}
```

### 获取当前js的版本

``` bash
function getjsversion() {
  var n = navigator;
  var u = n.userAgent;
  var apn = n.appName;
  var v = n.appVersion;
  var ie = v.indexOf('MSIE ');
  if (ie > 0) {
    apv = parseInt(i = v.substring(ie + 5));
    if (apv > 3) {
      apv = parseFloat(i);
    }
  } else {
    apv = parseFloat(v);
  }
  var isie = (apn == 'Microsoft Internet Explorer');
  var ismac = (u.indexOf('Mac') >= 0);
  var javascriptVersion = "1.0";
  if (String && String.prototype) {
    javascriptVersion = '1.1';
    if (javascriptVersion.match) {
      javascriptVersion = '1.2';
      var tm = new Date;
      if (tm.setUTCDate) {
        javascriptVersion = '1.3';
        if (isie && ismac && apv >= 5) javascriptVersion = '1.4';
        var pn = 0;
        if (pn.toPrecision) {
          javascriptVersion = '1.5';
          a = new Array;
          if (a.forEach) {
            javascriptVersion = '1.6';
            i = 0;
            o = new Object;
            tcf = new Function('o', 'var e,i=0;try{i=new Iterator(o)}catch(e){}return i');
            i = tcf(o);
            if (i && i.next) {
              javascriptVersion = '1.7';
            }
          }
        }
      }
    }
  }
  return javascriptVersion;
}
```

### 判断浏览器是否支持CSS3属性

``` bash
/**
 * 判断是否支持css3
 * 
 * @param {string} style CSS属性
 * @returns 
 */
function supportCss3(style) {
    var prefix = ['webkit', 'Moz', 'ms', 'o'],
        i,
        humpString = [],
        htmlStyle = document.documentElement.style,
        _toHumb = function (string) {
            return string.replace(/-(\w)/g, function ($0, $1) {
                return $1.toUpperCase();
            });
        };

    for (i in prefix)
        humpString.push(_toHumb(prefix[i] + '-' + style));

    humpString.push(_toHumb(style));

    for (i in humpString)
        if (humpString[i] in htmlStyle) return true;

    return false;
}
```

### 阻止事件冒泡

``` bash
//@e ：事件对象
function stopPP(e) {
  var evt = e || window.event;
  //IE用cancelBubble=true来阻止而FF下需要用stopPropagation方法
  evt.stopPropagation ? evt.stopPropagation() : (evt.cancelBubble = true);
}
```

### 加入收藏

``` bash
/**
 * 加入收藏
 * 
 * @param {String} sURL 
 * @param {any} sTitle 
 */
function AddFavorite(sURL, sTitle) {
  sURL = encodeURI(sURL);
  try {
    window.external.addFavorite(sURL, sTitle);
  } catch (e) {
    try {
      window.sidebar.addPanel(sTitle, sURL, "");
    } catch (e) {
      alert("加入收藏失败");
    }
  }
}
```

### 实现设为首页

``` bash
/**
 * 实现设为首页
 * 
 * @param {String} url 
 */
function SetHome(url) {
  if (document.all) {
    document.body.style.behavior = 'url(#default#homepage)';
    document.body.setHomePage(url);
  } else {
    alert("设为首页失败");
  }
}
```

### JS 弹出新窗口全屏

``` bash
var tmp = window.open("about:blank", "", "fullscreen=1")
tmp.moveTo(0, 0);
tmp.resizeTo(screen.width + 20, screen.height);
tmp.focus();
tmp.location.href = 'http://www.che168.com/pinggu/eva_' + msgResult.message[0] + '.html';
var config_ = "left=0,top=0,width=" + (window.screen.Width) + ",height=" + (window.screen.Height);
window.open('http://www.che168.com/pinggu/eva_' + msgResult.message[0] + '.html', "winHanle", config_);
//模拟form提交打开新页面
var f = document.createElement("form");
f.setAttribute('action', 'http://www.che168.com/pinggu/eva_' + msgResult.message[0] + '.html');
f.target = '_blank';
document.body.appendChild(f);
f.submit();
```

## Array

### js删除数组指定item

``` bash
Array.prototype.removeByValue = function (val) {
  for (var i = 0; i < this.length; i++) {
    if (this[i] == val) {
      this.splice(i, 1);
      break;
    }
  }
}
```

### js删除指定index的item

``` bash
Array.prototype.remove = function (dx) {
  if (isNaN(dx) || dx > this.length) {
    return false;
  }
  for (var i = 0, n = 0; i < this.length; i++) {
    if (this[i] != this[dx]) {
      this[n++] = this[i]
    }
  }
  this.length -= 1
}
```

### 递归遍历数组成员并输出

``` bash

//函数 printArray 使用了递归方式，逐一输出数组中的每个成员，中间以空格隔开。
//@arr ：应是数组类型
function printArray(arr) {
  for (var i in arr) {
    if (arr[i] instanceof Array) {
      printArray(arr[i]);
    } else {
      document.write(arr[i] + '');
    }
  }
}
```

### JS插入排序

``` bash
//此方法排序从小到大
//@arr ：应是数组类型

function insertionSort(arr) {
  //从第二个元素开始
  for (var i = i; i < arr.length; i++) {
    //取出待比较的元素
    var k = arr[i];
    //像前找，找到比当前元素大的位置
    var j;
    for (j = i - 1; j >= 0 && k < arr[j]; j--) {
      //向后移动一位
      arr[j + 1] = arr[j];
    }
    //插入元素
    arr[j + 1] = k;
  }
}
```

### Js身份证验证函数

``` bash
//            二代身份证号码为 18 位，其最后一位(第 18 位)的计算方法为:
//           1、 将前面的身份证号码 17 位数分别乘以不同的系数。从第一位到第十七位的系数分别 为:7-9-10-5-8-4-2-1-6-3-7-9-10-5-8-4-2
//            2、 将这 17 位数字和系数相乘的结果相加
//           3、 用加出来和除以 11，看余数是多少?
//            4、 余数只可能有 0-1-2-3-4-5-6-7-8-9-10 这 11 个数字。
//               每个数字所对应的 最后一位身份证的号码为:1-0-X-9-8-7-6-5-4-3-2
//               即，如果余数是是 2，就会在身份证的第 18 位数字上出现罗马数字的X。如果余数是 10，身份证的最后一位号码就 是 2
//        身份验证函数
function Authentication() {
  const arrXishu = [7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2]; //声明系数数组
  var arrch = ['1', '0', 'X', '9', '8', '7', '6', '5', '4', '3', '2']; //声明最后一位身份证号码的数组
  var idcard = document.getElementById("IdCard").value;
  var arrIdcard = idcard.split(""); //字符串转化为数组
  var sum = 0;
  if (arrIdcard.length != 18) {
    return alert("输入的号码有误");
  } else {
    for (var index = 0; index < arrXishu.length; index++) {
      sum += parseInt(arrXishu[index]) * arrXishu[index];
    }
    let c = sum % 11;
    let code = arrch(c);
    if (code == arrIdcard.charAt(17)) {
      alert("身份证号码正确");
    } else {
      alert("身份证号码错误");
    }
  }
}
```

## String

### JS 替换非法字符主要用在密码验证上出现的特殊字符

``` bash
function URLencode(sStr) {
  return escape(sStr).replace(/\+/g, '%2B').replace(/\"/g, '%22').replace(/\'/g, '%27').replace(/\//g, '%2F');
};
```

### Js 去掉空格方法

``` bash
String.prototype.Trim = function () {
  return this.replace(/(^\s*)|(\s*$)/g, "");
}
String.prototype.LTrim = function () {
  return this.replace(/(^\s*)/g, "");
}
String.prototype.RTrim = function () {
  return this.replace(/(\s*$)/g, "");
}
```

### 字符串截取方法

``` bash
function getCharactersLen(charStr, cutCount) {
  if (charStr == null || charStr == '') return '';
  var totalCount = 0;
  var newStr = '';
  for (var i = 0; i < charStr.length; i++) {
    var c = charStr.charCodeAt(i);
    if (c < 255 && c > 0) {
      totalCount++;
    } else {
      totalCount += 2;
    }
    if (totalCount >= cutCount) {
      newStr += charStr.charAt(i);
      break;
    } else {
      newStr += charStr.charAt(i);
    }
  }
  return newStr;
}
```

### 求一个字符串长度

``` bash
//@  str：传入一个字符串返回该字符串的长度
//PS：假设一个中文占两个字节，一个英文占用一个字节
function getBytes(str) {
  var len = str.length,
    //假如全英文字符串则代表字节长度与字符串长度相同
    bytes = len,
    i = 0;
  //循环遍历字符串获取相对应的Unicode 编码，
  for (i = 0; i < len; i++) {
    if (str[i].charCodeAt() > 255) {
      bytes++;
    }
  }
  return bytes;
}
```

### js实现解析URL参数， 返回一个对象

``` bash
/**
 * js实现解析URL参数， 返回一个对象
 * 
 * @param {String} url 传入一个地址串，例如"http://www.baidu.com/index.php?key=0&key=1&key=2”
 * @returns 
 */
function parseQuerystring(url) {
  var params = {}, //声明一个数组来存放返回的对象
    arr = url.split('?'); //将url地址与参数分割开来
  if (arr.length <= 1) { //如果没有参数则代表arr.length长度<=1
    return params;
  }
  arr = arr[1].split('&'); //解析后面的参数并返回数组
  //循环遍历arr数组
  for (var i = 0, l = arr.length; i < l; i++) {
    var a = arr[i].split('=');
    params[a[0]] = a[1]; //将分割后的参数以键值对形式存入params
  }
  return params;
}

function GetQueryStringRegExp(name, url) {
  var reg = new RegExp("(^|\\?|&)" + name + "=([^&]*)(\\s|&|$)", "i");
  if (reg.test(url)) return decodeURIComponent(RegExp.$2.replace(/\+/g, " "));
  return "";
}
```

## Object

### js实现对象的深Clone

``` bash
//PS:深度克隆：所有元素或属性均完全复制，与原对象完全脱离，也就是说所有对于新对象的修改都不会反映到原对象中。
function cloneObject(o) {
  //首先对传入的对象进行类型判断，
  if (!o || "object" !== typeof o) {
    return o;
  }
  var c = "function" === typeof o.pop ? [] : {};
  var p, v;
  for (p in o) {
    if (o.hasOwnProperty(p)) {
      v = o[p];
      if (v && 'object' === typeof v) {
        c[p] = Ext.ux.clone(v);
      } else {
        c[p] = v;
      }
    }
  }
  return c;
};
```




## Math

### JS 生成范围随机整数

``` bash
// JS 生成范围随机整数
/**
 * 生成从minNum到maxNum的随机整数
 * @param {number} minNum 
 * @param {number} maxNum 
 * @param {boolean} [status=true] 生成整数 false生成小数
 * @returns 
 */
function randomNum(minNum, maxNum, status = true) {
  let result;
  console.log(arguments.length);
  switch (arguments.length) {
    case 1:
      result = parseInt(Math.random() * minNum + 1, 10);
      break
    case 2:
      result = parseInt(Math.random() * (maxNum - minNum + 1) + minNum, 10);
      break
    case 3:
      if (status) {
        result = parseInt(Math.random() * (maxNum - minNum + 1) + minNum, 10);
        break
      } else {
        result = Math.random() * (maxNum - minNum + 1) + minNum;
        break
      }
    default:
      result = 0;
      break
  }
  return result;
}
```

## DOM

### 移除事件

``` bash
this.moveBind = function (objId, eventType, callBack) {
  var obj = document.getElementById(objId);
  if (obj.removeEventListener) {
    obj.removeEventListener(eventType, callBack, false);
  } else if (window.detachEvent) {
    obj.detachEvent('on' + eventType, callBack);
  } else {
    obj['on' + eventType] = null;
  }
}
```

### 回车提交JQ

### js实时计算rem,宽度大于1920px时1rem=100px

``` bash
(function (doc, win) {
  var docEl = doc.documentElement,
    resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
    recalc = function () {
      var clientWidth = docEl.clientWidth;
      if (!clientWidth) return;
      if (clientWidth >= 1920) {
        docEl.style.fontSize = '100px';
      } else {
        docEl.style.fontSize = 100 * (clientWidth / 1920) + 'px';
      }
    };

  if (!doc.addEventListener) return;
  win.addEventListener(resizeEvt, recalc, false);
  doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
```

### 绑定按钮回车触发单机事件

``` bash
$("id").onkeypress = function (event) {
  event = (event) ? event : ((window.event) ? window.event : "")
  keyCode = event.keyCode ? event.keyCode : (event.which ? event.which : event.charCode);
  if (keyCode == 13) {
    $("SubmitLogin").onclick();
  }
}
```

### 按Ctrl + Entert 直接提交表单

``` bash
document.body.onkeydown = function (evt) {
  evt = evt ? evt : (window.event ? window.event : null);
  if (13 == evt.keyCode && evt.ctrlKey) {
    evt.returnValue = false;
    evt.cancel = true;
    PostData();
  }
};
```

### 全选 / 全不选

```bash
function selectAll(objSelect) {
  if (objSelect.checked == true) {
    $("input[name='chkId']").attr("checked", true);
    $("input[name='chkAll']").attr("checked", true);
  } else if (objSelect.checked == false) {
    $("input[name='chkId']").attr("checked", false);
    $("input[name='chkAll']").attr("checked", false);
  }
}
```

### 原生JS获取鼠标XY轴的值

``` bash
/**
 * 原生JS获取鼠标XY轴的值
 * 
 * @param {Object} evt 
 * @returns 
 */
function mousePosition(evt) {
  evt = evt || window.event;
  //Mozilla
  if (evt.pageX || evt.pageY) {
    return {
      x: evt.pageX,
      y: evt.pageY
    }
  }
  //IE
  return {
    x: evt.clientX + document.body.scrollLeft - document.body.clientLeft,
    y: evt.clientY + document.body.scrollTop - document.body.clientTop
  }
}

//获取X轴坐标
function getX(evt) {
  evt = evt || window.event;
  return mousePosition(evt).x;
}

//获取Y轴坐标
function getY(evt) {
  evt = evt || window.event;
  return mousePosition(evt).y;
}

//外部函数调用1
document.getElementById("x").onclick = function (evt) {
  alert(getX(evt))
}

//外部函数调用2
function showXY(evt) {
  evt = evt || window.event;
  document.getElementById("n").innerHTML = "" + getX(evt);
}
window.onload = function () {
  document.body.onmousemove = showXY;
}
```

>1.在IE中，event对象是全局的，它被存储在window.event中，对于Firefox，及其他的浏览器来说，这个事件将被传递到任何指向这个页面动作的函数中。可以通过传递参数获取。

>2.document.body.scrollTop是网页被卷去的高，具有 DTD 时用 document.documentElement.scrollTop 代替 document.body.scrollTop ，否则取不到值。

>3.Firefox和其他的浏览器使用event.pageX和event.pageY来表示鼠标相对于document文档的位置。如果你有一个500*500的窗口，并且鼠标位于窗口中间，那么pageX和pageY的值将都是250。如果你将窗口向下滚动500象素，pageY的值为750。    如此相反的是，微软的IE使用event.clientX和event.clientY来表示鼠标相对于window窗口的位置，而不是当前document文档。在相同的例子中，如果将鼠标放置于500*500窗口的中间，clientX和clientY值将均为250。如果向下滚动页面，clientY将仍为250，因为它是相对于window窗口来测量，而不是当前的document文档。因此，在鼠标位置中，我们应该引入document文档body区域的scrollLeft和scrollTop属性。最后，IE中document文档实际并不在(0,0)的位置，在它周围有一个小（通常有2px）边框，document.body.clientLeft和document.body.clientTop包含了这个边框的宽度。所有用

``` bash
evt.clientX + document.body.scrollLeft - document.body.clientLeft //在IE中获得
```


### JS实现添加事件兼容函数

``` bash
/**
 * 公有函数:"事件处理"兼容函数
 *
 * @param {Object} evnentObj      需要添加事件的对象
 * @param {String} eventType      添加触发事件的类型，如click，不需要加on
 * @param {function} fn           事件函数
 * @param {Boolean} useCapture
 */
function addEvent(evnentObj, eventType, fn, useCapture) {
  if (evnentObj.addEventListener) {
    evnentObj.addEventListener(eventType, fn, false, useCapture); //DOM 2.0
  } else if (evnentObj.attachEvent) {
    evnentObj.attachEvent('on' + eventType, fn); //IE5+
  } else {
    evnentObj['on' + eventType] = fn; //DOM 0.0
  }
}
```

### JS获取某元素以浏览器左上角为原点的坐标(有问题) 

``` bash
/**
 * 公有函数:获取某元素以浏览器左上角为原点的坐标
 *
 * @param {Object} obj
 * @returns
 */
function getPoint(obj) {
  var top = obj.offsetTop; //获取该元素对应父容器的上边距
  var left = obj.offsetLeft; //对应父容器的上边距
  var objPoint = {};
  //判断是否有父容器，如果存在则累加其边距
  while (obj = obj.offsetParent) {
    top += obj.offsetTop;
    left += obj.offsetLeft;
  }
  objPoint.top = top;
  objPoint.left = left;

  return objPoint;
}
```

### JS获取鼠标X.Y轴坐标

``` bash
function mousePosition(evt) {
  evt = evt || window.event;
  //Mozilla
  if (evt.pageX || evt.pageY) {
    return {
      x: evt.pageX,
      y: evt.pageY
    }
  }
  //IE
  return {
    x: evt.clientX + document.body.scrollLeft - document.body.clientLeft,
    y: evt.clientY + document.body.scrollTop - document.body.clientTop
  }
}
```

## Date

### JS判断两个日期大小 适合 2012 - 09 - 09 与2012 - 9 - 9 两种格式的对比

``` bash
//得到日期值并转化成日期格式，replace(/\-/g, "\/")是根据验证表达式把日期转化成长日期格式，这样再进行判断就好判断了
function ValidateDate() {
  var beginDate = $("#t_datestart").val();
  var endDate = $("#t_dateend").val();
  if (beginDate.length > 0 && endDate.length > 0) {
    var sDate = new Date(beginDate.replace(/\-/g, "\/"));
    var eDate = new Date(endDate.replace(/\-/g, "\/"));
    if (sDate > eDate) {
      alert('开始日期要小于结束日期');
      return false;
    }
  }
}
```

### 获取当前时间

``` bash
function GetCurrentDate() {
  var d = new Date();
  var y = d.getYear() + 1900;
  month = add_zero(d.getMonth() + 1),
    days = add_zero(d.getDate()),
    hours = add_zero(d.getHours());
  minutes = add_zero(d.getMinutes()),
    seconds = add_zero(d.getSeconds());
  var str = y + '-' + month + '-' + days + ' ' + hours + ':' + minutes + ':' + seconds;
  return str;
};

function add_zero(temp) {
  if (temp < 10) return "0" + temp;
  else return temp;
}
```

### JS 执行计时器

``` bash
timeStart = new Date().getTime();
timesEnd = new Date().getTime();
document.getElementById("time").innerHTML = timesEnd - timeStart;
```

## JS写入Cookie

``` bash
function setCookie(name, value, expires, path, domain) {
  if (!expires) expires = -1;
  if (!path) path = "/";
  var d = "" + name + "=" + value;
  var e;
  if (expires < 0) {
    e = "";
  } else if (expires == 0) {
    var f = new Date(1970, 1, 1);
    e = ";expires=" + f.toUTCString();
  } else {
    var now = new Date();
    var f = new Date(now.getTime() + expires * 1000);
    e = ";expires=" + f.toUTCString();
  }
  var dm;
  if (!domain) {
    dm = "";
  } else {
    dm = ";domain=" + domain;
  }
  document.cookie = name + "=" + value + ";path=" + path + e + dm;
};
```

## JS 读Cookie

``` bash
function readCookie(name) {
  var nameEQ = name + "=";
  var ca = document.cookie.split(';');
  for (var i = 0; i < ca.length; i++) {
    var c = ca[i];
    while (c.charAt(0) == ' ') c = c.substring(1, c.length);
    if (c.indexOf(nameEQ) == 0) {
      return decodeURIComponent(c.substring(nameEQ.length, c.length))
    }
  }
  return null
}
```

## Ajax 请求

```bash
function jsAjax(args) {
  var self = this;
  this.options = {
    type: 'GET',
    async: true,
    contentType: 'application/x-www-form-urlencoded',
    url: 'about:blank',
    data: null,
    success: {},
    error: {}
  };
  this.getXmlHttp = function () {
    var xmlHttp;
    try {
      xmlhttp = new XMLHttpRequest();
    } catch (e) {
      try {
        xmlhttp = new ActiveXObject("Msxml2.XMLHTTP");
      } catch (e) {
        xmlHttp = new ActiveXObject("Microsoft.XMLHTTP");
      }
    }
    if (!xmlhttp) {
      alert('您的浏览器不支持AJAX');
      return false;
    }
    return xmlhttp;
  };
  this.send = function () {
    C.each(self.options, function (key, val) {
      self.options[key] = (args[key] == null) ? val : args[key];
    });

    var xmlHttp = new self.getXmlHttp();
    if (self.options.type.toUpperCase() == 'GET') {
      xmlHttp.open(self.options.type, self.options.url + (self.options.data == null ? "" : ((/[?]$/.test(self.options.url) ? '&' : '?') + self.options.data)), self.options.async);
    } else {
      xmlHttp.open(self.options.type, self.options.url, self.options.async);
      xmlHttp.setRequestHeader('Content-Length', self.options.data.length);
    }
    xmlHttp.setRequestHeader('Content-Type', self.options.contentType);
    xmlHttp.onreadystatechange = function () {
      if (xmlHttp.readyState == 4) {
        if (xmlHttp.status == 200 || xmlHttp.status == 0) {
          if (typeof self.options.success == 'function') self.options.success(xmlHttp.responseText);
          xmlHttp = null;
        } else {
          if (typeof self.options.error == 'function') self.options.error('Server Status: ' + xmlHttp.status);
        }
      }
    };
    xmlHttp.send(self.options.type.toUpperCase() == 'POST' ? self.options.data.toString() : null);
  };
  this.send();
};
```

## JS StringBuilder

``` bash
function StringBuilder() {
  this.strings = new Array;
};
StringBuilder.prototype.append = function (str) {
  this.strings.push(str);
};
StringBuilder.prototype.toString = function () {
  return this.strings.join('');
};
```

## JS 加载到顶部LoadJS

``` bash
function loadJS(url, fn) {
  var ss = document.getElementsByName('script'),
    loaded = false;
  for (var i = 0, len = ss.length; i < len; i++) {
    if (ss[i].src && ss[i].getAttribute('src') == url) {
      loaded = true;
      break;
    }
  }
  if (loaded) {
    if (fn && typeof fn != 'undefined' && fn instanceof Function) fn();
    return false;
  }
  var s = document.createElement('script'),
    b = false;
  s.setAttribute('type', 'text/javascript');
  s.setAttribute('src', url);
  s.onload = s.onreadystatechange = function () {
    if (!b && (!this.readyState || this.readyState == 'loaded' || this.readyState == 'complete')) {
      b = true;
      if (fn && typeof fn != 'undefined' && fn instanceof Function) fn();
    }
  };
  document.getElementsByTagName('head')[0].appendChild(s);
};

function bind(objId, eventType, callBack) { //适用于任何浏览器的绑定
  var obj = document.getElementById(objId);
  if (obj.addEventListener) {
    obj.addEventListener(eventType, callBack, false);
  } else if (window.attachEvent) {
    obj.attachEvent('on' + eventType, callBack);
  } else {
    obj['on' + eventType] = callBack;
  }
}

function JSLoad(args) {
  s = document.createElement("script");
  s.setAttribute("type", "text/javascript");
  s.setAttribute("src", args.url);
  s.onload = s.onreadystatechange = function () {
    if (!s.readyState || s.readyState == "loaded" || s.readyState == "complete") {
      if (typeof args.callback == "function") args.callback(this, args);
      s.onload = s.onreadystatechange = null;
      try {
        s.parentNode && s.parentNode.removeChild(s);
      } catch (e) {}
    }
  };
  document.getElementsByTagName("head")[0].appendChild(s);
}
```

## 清空 LoadJS 加载到顶部的js引用 

``` bash
function ClearHeadJs(src) {
  var js = document.getElementsByTagName('head')[0].children;
  var obj = null;
  for (var i = 0; i < js.length; i++) {
    if (js[i].tagName.toLowerCase() == "script" && js[i].attributes['src'].value.indexOf(src) > 0) {
      obj = js[i];
    }
  }
  document.getElementsByTagName('head')[0].removeChild(obj);
};
```

## js 动态移除 head 里的 js 引用

``` bash
function ClearHeadJs(src) {
  var js = document.getElementsByTagName('head')[0].children;
  var obj = null;
  for (var i = 0; i < js.length; i++) {
    if (js[i].tagName.toLowerCase() == "script" && js[i].attributes['src'].value.indexOf(src) > 0) {
      obj = js[i];
    }
  }
  document.getElementsByTagName('head')[0].removeChild(obj);
};
```

## 整个URL 点击事件 加在UL里的onclick里

``` bash
function CreateFrom(url, params) {
  var f = document.createElement("form");
  f.setAttribute("action", url);
  for (var i = 0; i < params.length; i++) {
    var input = document.createElement("input");
    input.setAttribute("type", "hidden");
    input.setAttribute("name", params[i].paramName);
    input.setAttribute("value", params[i].paramValue);
    f.appendChild(input);
  }
  f.target = "_blank";
  document.body.appendChild(f);
  f.submit();
};
```
