# 初始jquery
## 一、什么是jquery？
    jQuery是一个快速，小巧，功能丰富的JavaScript库。它通过易于使用的API在大量浏览器中运行，使得HTML文档遍历和操作，事件处理，动画和Ajax变得更加简单。通过多功能性和可扩展性的结合，jQuery改变了数百万人编写JavaScript的方式。
## 二 、jQuery的优点

1. 查找元素方便的方法多种多样，非常灵活
   
2. 拥有隐士迭代的特性，因此不需要手写 `for` 循环
3. 没有兼容性问题
4. 实现动画简单，功能强大，
5. 代码简单

## 三、jQuery版本问题
* 1.X版本:能够兼容IE6、7、8浏览器
  
* 2.X版本:不兼容IE6、7、8浏览器
* 3.x版本:不兼容IE、7、8浏览器
* 1.x版本让与2.x版本现在已经不再更新，目前只更新3.x
  
## 四、关于jQuery的压缩版本与未压缩版本

* jquery.min.js : 压缩版本，适用于生产环境，因为文件小
* jquery.js : 未压缩版本，适用于学习与开发坏境，代码清晰易懂
  
# jquery的基础

##  一、如何使用jquery

1. 引入jquery

> `<script src="jquery.js"></script>`

2. 写jquery入口函数(推荐写)

**第一种**
>`$(document).rendy(unction(){})`

**第二种**
>`$(function(){})`

3. 写jquery功能代码

## 二、 jquery对象与DOM对象

### 什么是jquery对象
    在jQuery库中，通过自身的发法获取到的DOM元素的对象叫DOM对象
### 什么是DOM对象
    使用传统方法(javascript)获取到的对象叫DOM对象
### DOM对象与jquery对象的区别
    jquery对象是通过jquery库里面的方法包装DOM对象后生成的一个js集合(伪数组),它是jqurty独有的，只有jquery对象才能调用jquery里面的方法。
### jquery对象与DOM对象之间的转换
**DOM对象转换成jquery对象**

```javascript
var dom = document.getElementBYId("idname");
$(dom)//将获取的dom元素用$()包住
```
**jquery对象转换成DOM对象**
```javascript
var $li = $("li");
$li[0].style.color="#f90";//在jquery对象后加下标
$li.get(0)//利用get方法
```
## 三、$符号的实质

    $其实就是一个函数，使用$时记得用$()
### $的三种用法
1. 参数为`function`
>`$(function(){})`
2. 参数为属性名
>`$(document).`
3. 参数为字符串
>`$("#idName") 、$("ClassName")`

# jquery的选择器

## 一、jquery的基本选择器

<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>id选择器</td>
        <td>$("#idName")</td>
        <td>通过元素id属性给定值查找</td>
    </tr>
    <tr bgcolor="#333">
        <td>class选择器</td>
        <td>$(".className")</td>
        <td>通过元素class属性给定值查找</td>
    </tr>
     <tr bgcolor="#333">
        <td>* 选择器</td>
        <td>$("*")</td>
        <td>找到页面种的所有元素（不推荐使用）</td>
    </tr>
     <tr bgcolor="#333">
        <td>element选择器</td>
        <td>$("element")</td>
        <td>通过标签名查找</td>
    </tr>
</table>

### 1. id选择器代码演示

**HTML代码**
```HTML
<div id="box"></div>
```
**jq代码**
```javascript
var $div = $("#box")
```
**结果**
```javascript
[<div id="box"></div>]
```
### 2. class选择器代码演示

**HTML代码**
```HTML
<div class="box"></div>
```
**jq代码**
```javascript
var $div = $(".box")
```
**结果**
```javascript
[<div class="box"></div>]
```
### 3. *选择器代码演示

**HTML代码**
```HTML
<div class="box">
    <p>
        <a href="#"></a>
    </p>
</div>
```
**jq代码**
```javascript
var $box = $("*")
```
**结果**
```javascript
[<div class="box"></div>,<p><a href="#"></a></p>,<a href="#"></a>]
```

### 4. element 选择器代码演示

**HTML代码**
```HTML
<div class="box">
    <p>
        <a href="#"></a>
    </p>
</div>
```
**jq代码**
```javascript
var $div = $("div"),
    $p = $("p"),
    $a = $("a");
```
**结果**
```javascript
[<div class="box"></div>]
[<p><a href="#"></a></p>]
[<a href="#"></a>]
```
## 二、jquery的层级选择器

<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>后代选择器</td>
        <td>$("ul li")</td>
        <td>查找给定元素的后代元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>子代选择器</td>
        <td>$("ul>a")</td>
        <td>查找给定元素的所有子元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>+ 选择器</td>
        <td>$("prev + next")</td>
        <td>查找给定元素的下一个元素</td>
    </tr>
     <tr bgcolor="#333">
        <td> ~ 选择器</td>
        <td>$("prev ~ sildings")</td>
        <td>查找给定元素之后的所有同名的兄弟元素</td>
    </tr>
</table>

### 1. 后代选择器的代码演示
**HTML代码**
```HTML
<ul>
    <li>1<li>
    <li>1<li>
</ul>
```
**jq代码**
```javascript
$("ul li")
```
**结果**
```javascript
[<li>1</li>,<li>1</li>]
```

### 2. 子代选择器的代码演示
**HTML代码**
```HTML
<ul>
    <li>
        <a href="#">链接1</a>
    <li>
    <li>
        <a href="#">链接2</a>
    <li>
</ul>
```
**jq代码**
```javascript
$("ul>a")
```
**结果**
```javascript
[ < a href="#">链接1</a>, <a href="#">链接2</a> ]
```
### 3. + 选择器的代码演示
**HTML代码**
```HTML
 <ul>
     <li>
         <a href="#">链接1</a>
         <p class="word">文本1</p>
         <span class="span">文本2</span>
     <li>
     <li>
         <a href="#">链接2</a>
         <span class="span"></span>
     <li>
</ul>
```
**jq代码**
```javascript
$(".word + .span")
```
**结果**
```javascript
[ <span class="span">文本2</span> ]
```
### 4. ~ 选择器的代码演示
**HTML代码**
```HTML
<form>
    <label>名字：</label>
    <input type="text">
    <Fieldset>
        <label>地址：</label>
        <input type="text">
        <input type="text">
        <input type="text">
        <label>邮箱：</label>
        <input type="text">
    </Fieldset>
</form>
```
**jq代码**
```javascript
$("label ~ input")
```
**结果**
```javascript
[ <input type="text">, <input type="text">, <input type="text">, <input type="text">, <input type="text"> ]
```
## 三、jquery的基本筛选器
<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>:first</td>
        <td>$("li:first")</td>
        <td>获取第一个元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:last</td>
        <td>$("li:last")</td>
        <td>获取最后一个元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:not(selector)</td>
        <td>$("li:not("list")")</td>
        <td>查找除给定元素一外的同名元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>:even</td>
        <td>$("li:even")</td>
        <td>查找索引值为偶数的元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>:odd</td>
        <td>$("li:odd")</td>
        <td>查找索引值为奇数的元素</td>
    </tr>
      <tr bgcolor="#333">
        <td>:eq(index)</td>
        <td>$("li:eq(0)")</td>
        <td>查找给定索引值的元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:gt(index)</td>
        <td>$("li:gt(1)")</td>
        <td>查找大于给定索引值的所有元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:lt(index)</td>
        <td>$("li:lt(1)")</td>
        <td>查找小于给定索引值的所有元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:focus</td>
        <td>$(":focus")</td>
        <td>查找当前获取焦点的元素</td>
    </tr>
</table>

### 1. :first的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li>2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
   $("li:first")
```
**结果**
```javascript
[  <li>1</li> ]
```
### 2. :last的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li>2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
   $("li:last")
```
**结果**
```javascript
[  <li>3</li> ]
```
### 3. :not(selector)的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li id="list">2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
    $("li:not(#list)")
```
**结果**
```javascript
[  <li>1</li>,<li>3</li> ]
```
### 4. :even的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li>2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
    $("li:even")
```
**结果**
```javascript
[  <li>1</li>,<li>3</li> ]
```
### 5. :odd的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li>2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
    $("li:odd")
```
**结果**
```javascript
[  <li>2</li> ]
```
### 6. :eq(index)的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li>2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
    $("li:eq(2)")
```
**结果**
```javascript
[  <li>3</li> ]
```
### 7. :gt(index)的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li>2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
    $("li:gt(0)").css("color","red")
```
**结果**
```javascript
[  <li>2</li>,<li>3<li> ]
```
### 8. :lt(index)的代码演示
**HTML代码**
```HTML
  <ul>
     <li>1</li>
     <li>2</li>
     <li>3</li>
  </ul>
```
**jq代码**
```javascript
    $("li:lt(2)").css("color","red")
```
**结果**
```javascript
[  <li>1</li>,<li>2<li> ]
```

### 9. :focus的代码演示
**HTML代码**
```HTML
  <div class="box">
     <input type="text">
     <input type="text">
     <input type="text">
     <p></p>
  </div>
```
**jq代码**
```javascript
     $(".box").delegate("input", "focus", function () {
       $(":focus").css("backgroundColor", "red")
     })
```
## 四、内容选择器

<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>:contains(text)</td>
        <td>$("li:contains(text)</td>
        <td>获取给定文本的元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:empty</td>
        <td>$("li:empty")</td>
        <td>获取不包含文本或子元素的空元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:has(selector)</td>
        <td>$("li:has("p")</td>
        <td>获取包含选择器所匹配的元素（p）的元素（li）</td>
    </tr>
</table>

### 1. ::empty的代码演示
**HTML代码**
```HTML
 <ul>
     <li>text</li>
     <li>2</li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li:contains(text)")
```
**结果**
```javascript
[  <li>text</li> ]
```
### 2. :empty的代码演示
**HTML代码**
```HTML
 <ul>
     <li>text</li>
     <li></li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li:empty")
```
**结果**
```javascript
[  <li></li> ]
```
### 3. :has(selector)的代码演示
**HTML代码**
```HTML
 <ul>
     <li>text</li>
     <li>
         <p></p>
     </li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li:has(p)")
```
**结果**
```javascript
[  <li><p></p></li> ]
```
## 六、可见性选择器
<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>:hidden</td>
        <td>$("li:hidden")</td>
        <td>获取不可见的属性</td>
    </tr>
     <tr bgcolor="#333">
        <td>:visible</td>
        <td>$("li:visible")</td>
        <td>获取可见的属性</td>
    </tr>
</table>

### 3. :hidden的代码演示
**HTML代码**
```HTML
 <ul>
     <li style="display:none">text</li>
     <li></li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li:hidden")
```
**结果**
```javascript
[  <li>text</li> ]
```
### 3. :hidden的代码演示
**HTML代码**
```HTML
 <ul>
     <li style="display:none">text</li>
     <li>2</li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li::visible")
```
**结果**
```javascript
[  <li>2</li>,<li>3</li> ]
```
## 七、属性选择器
<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>[属性名]</td>
        <td>$("li[class]")</td>
        <td>获取特定属性名的元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>[属性名 = 值]</td>
        <td>$("li[id='list']")</td>
        <td>获取给定特定属性和属性值的元素;相反,[属性名 != 值]为获取为定义特定属性和值的元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>[属性名 ^= 值]</td>
        <td>$("li[class ^='list']")</td>
        <td>获取给定特定属性的属性值是某些值开始的元素;相反,[属性名 $= 值]获取给定特定属性的属性值是某些值结尾的元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>[属性名 ^= 值]</td>
        <td>$("li[class ^='list']")</td>
        <td>获取给定特定属性的属性值是某些值开始的元素;相反,[属性名 $= 值]获取给定特定属性的属性值是某些值结尾的元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>[属性名 *= 值]</td>
        <td>$("li[class *='list']")</td>
        <td>获取给定特定属性的属性值中包含某些值得元素</td>
    </tr>
</table>

### 1. [属性名]的代码演示
**HTML代码**
```HTML
 <ul>
     <li id="list">text</li>
     <li>2</li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li[id]")
```
**结果**
```javascript
[  <li id="list">text</li> ]
```
### 2. [属性名=值]的代码演示
**HTML代码**
```HTML
 <ul>
     <li id="list">text</li>
     <li id="newlist">2</li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li[id='list']")
```
**结果**
```javascript
[  <li id="list">text</li> ]
```
### 3. [属性名^=值]的代码演示
**HTML代码**
```HTML
 <ul>
     <li id="newlist">text</li>
     <li id="newlist">2</li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li[id ^='new']")
```
**结果**
```javascript
[  <li id="newlist">text</li>,<li id="newlist">2</li> ]
```
### 4. [属性名*=值]的代码演示
**HTML代码**
```HTML
 <ul>
     <li id="newlist">text</li>
     <li id="newlist">2</li>
     <li>3</li>
 </ul>
```
**jq代码**
```javascript
    $("li[id *='li']")
```
**结果**
```javascript
[  <li id="newlist">text</li>,<li id="newlist">2</li> ]
```
## 八、表单选择器
<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>:input</td>
        <td>$(":input")</td>
        <td>获取所有input表单元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:text</td>
        <td>$(":text")</td>
        <td>获取所有text表单元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>:password</td>
        <td>$(":password")</td>
        <td>获取所有密码表单元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>:radio</td>
        <td>$(":radio")</td>
        <td>获取所有单选框表单元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>:buuton</td>
        <td>$(":button")</td>
        <td>获取所有按钮表单元素</td>
    </tr>
</table>

### 1. :input代码演示
**HTML代码**
```HTML
   <form>
        <input type="text">
        <input type="button">
        <input type="radio">
         <textarea cols="30" rows="10">
        </textarea>
         <select >
            <option></option>
        </select>
    </form>
```
**jq代码**
```javascript
    $(":input")
```
**结果**
```javascript
[   <input type="text">,  <input type="button">2</li>, <input type="radio">,<textarea cols="30" rows="10">,<select><option></option></select> ]
```

### 2. :text代码演示
**HTML代码**
```HTML
   <form>
        <input type="text">
        <input type="button">
        <input type="radio">
         <textarea cols="30" rows="10">
        </textarea>
         <select >
            <option></option>
        </select>
    </form>
```
**jq代码**
```javascript
    $(":text")
```
**结果**
```javascript
[   <input type="text"> ]
```

### 3. :password代码演示
**HTML代码**
```HTML
   <form>
        <input type="text">
        <input type="button">
           <input type="password">
        <input type="radio">
         <textarea cols="30" rows="10">
        </textarea>
         <select >
            <option></option>
        </select>
    </form>
```
**jq代码**
```javascript
    $(":password")
```
**结果**
```javascript
[   <input type="password"> ]
```
### 4. :radio代码演示
**HTML代码**
```HTML
   <form>
        <input type="text">
        <input type="button">
           <input type="password">
        <input type="radio">
         <textarea cols="30" rows="10">
        </textarea>
         <select >
            <option></option>
        </select>
    </form>
```
**jq代码**
```javascript
    $(":radio")
```
**结果**
```javascript
[   <input type="radio"> ]
```
## 九、表单对象属性选择器
<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>:enabled</td>
        <td>$("input:enabled")</td>
        <td>获取所有可用元素；disabled为不可用</td>
    </tr>
    <tr bgcolor="#333">
        <td>:checked</td>
        <td>$("input:checked")</td>
        <td>获取所有被选中得表单元素（单选、复选、select中得option）</td>
    </tr>
    <tr bgcolor="#333">
        <td>:selected</td>
        <td>$("select option:selected")</td>
        <td>获取所有选中得option元素</td>
    </tr>
</table>

### 1. :enabled代码演示
**HTML代码**
```HTML
   <form>
      
    </form>
```
**jq代码**
```javascript
    $(":enabled")
```
**结果**
```javascript
[    <input type="button"> ]
```
### 2. :ckecked代码演示
**HTML代码**
```HTML
<form>
    <input type="checkbox" checked="checked" value="技能">
    <input type="checkbox" value="爱好">
    <input type="checkbox" checked="checked" value="习惯">
</form>
```
**jq代码**
```javascript
    $(":checked")
```
**结果**
```javascript
[     <input type="checkbox" checked="checked" value="技能">, <input type="checkbox" checked="checked" value="习惯"> ]
```
### 3. :selected代码演示
**HTML代码**
```HTML
<form>
  <select >
    <option value="北京" selected="selected"></option>
    <option value="天津" ></option>
  </select>
</form>
```
**jq代码**
```javascript
    $(":selected")
```
**结果**
```javascript
[     <option value="北京" selected="selected"></option>  ]
```
## 十、 子元素选择器
<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>:first-child</td>
        <td>$("div p:first-child")</td>
        <td>获取给定元素的第一个子元素，同理，last-child就是获取最后一个子元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>:first-of-type</td>
        <td>$("p:first-of-type")</td>
        <td>获取所有父级元素下的所有第一个子元素（与给定元素的类型相同的第一个元素），同理，:last-of-type为最后一个</td>
    </tr>
    <tr bgcolor="#333">
        <td>:nth-child(index)</td>
        <td>$("div > p:nth-child(1)")</td>
        <td>获取父级元素下的第几个子元素（索引值从1开始）</td>
    </tr>
    <tr bgcolor="#333">
        <td>:nth-last-of-type(index)</td>
        <td>$("ul li:nth-last-of-type(2)")</td>
        <td>获取所有父级元素下的子元素从最后开始计数的倒数第几个元素（与给定元素相同的所有子元素）</td>
    </tr>
    <tr bgcolor="#333">
        <td>:only-child</td>
        <td>$("ul li:only-child")</td>
        <td>获取父级元素下的唯一一个子元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>:only-of-type</td>
        <td>$("ul li:only-of-type")</td>
        <td>获取所有父级元素下没有兄弟元素且与给定元素相同类型的元素</td>
    </tr>
</table>

### 1. :first-child代码演示

**HTML代码**
```HTML
  <div>
     <p>文字1</p>
     <p>文字2</p>
 <div>
 <div>
     <p>文字3</p>
     <p>文字4</p>
 <div>
```
**jq代码**
```javascript
 $("div p:first-child")
```
**结果**
```javascript
[ <p>文本1</p>, <p>文字3</p> ]
```
### 2. :first-of-type代码演示

**HTML代码**
```HTML
 <div>
     <p>文字1</p>
     <p>文字2</p>
 <div>
 <ul>
     <li>
        <p>文字3</p>
        <p>文字4</p>
     </li>
     <li>
         <div>
             <p>文字5</p>
             <p>文字6</p>
         </div>
          <div>
            <span>span1</span>
        </div>
     </li>
 </ul>
```
**jq代码**
```javascript
 $("p:first-of-type")
```
**结果**
```javascript
[ <p>文本1</p>, <p>文字3</p>, <p>文字5</p> ]
```
### 3. :nth-child(index)代码演示

**HTML代码**
```HTML
 <div>
     <p>文字1</p>
     <p>文字2</p>
 <div>
 <ul>
     <li>
        <p>文字3</p>
        <p>文字4</p>
     </li>
     <li>
         <div>
             <p>文字5</p>
             <p>文字6</p>
         </div>
          <div>
            <span>span1</span>
        </div>
     </li>
 </ul>
```
**jq代码**
```javascript
  $("div > p:nth-child(2)")
```
**结果**
```javascript
[  <p>文字2</p>,  <p>文字6</p> ]
```
### 4. :nth-last-of-type(index)代码演示

**HTML代码**
```HTML
<ul>
  <li>文字1</li>
  <li>文字2</li>
  <li>文字3</li>
  <li>文字4</li>
</ul>
 <ul>
  <li>
      <ul>
          <li>文字5</li>
          <li>文字6</li>
          <li>文字7</li>
      </ul>
  </li>
  <li>文字8</li>
  <li>文字9</li>
  <li>文字10</li>
 </ul>
```
**jq代码**
```javascript
   $("ul li:nth-last-of-type(2)")
```
**结果**
```javascript
[   <li>文字3</li>,  <p>文字6</p>, <li>文字9</li> ]
```
### 5. :only-child代码演示

**HTML代码**
```HTML
<ul>
    <li>文字1</li>
</ul>
 <ul>
     <li>
      <ul>
          <li>文字2</li>
      </ul>
     </li>
     <li>文字3</li>
     <li>文字4</li>
     <li>文字5</li>
 </ul>
```
**jq代码**
```javascript
   $("ul li::only-child")
```
**结果**
```javascript
[   <li>文字1</li>,  <p>文字2</p> ]
```
### 6. :only-of-type代码演示

**HTML代码**
```HTML
 <div>
    <span>span1</span>
</div>
 <p>
    <span>span2</span>
 </p>
 <ul>
    <li>
        <span>span3</span>
        <span>span4</span>
        <span>span5</span>
    </li>
 </ul>
```
**jq代码**
```javascript
   $("span:only-of-type")
```
**结果**
```javascript
[    <span>span1</span>,<span>span2</span> ]
```

## 十一、 筛选选择器（方法）
<table width=100% border=1>
    <tr bgcolor="#f1f1f1">
        <th>选择器</th>
        <th>语法</th>
        <th>描述</th>
    </tr>
    <tr bgcolor="#333">
        <td>.childen()</td>
        <td>$("div").childen("p")</td>
        <td>相当于子代选择器，获取规定祖先的子代元素</td>
    </tr>
     <tr bgcolor="#333">
        <td>.find()</td>
        <td>$("div").find()</td>
        <td>相当于后代选择器，获取规定祖先的后代元素</td>
    </tr>
    <tr bgcolor="#333">
        <td>.siblings()</td>
        <td>$("div").siblings()</td>
        <td>获取规定元素的兄弟元素，不包含本身</td>
    </tr>
    <tr bgcolor="#333">
        <td>.next()</td>
        <td>$("div").prev()</td>
        <td>获取规定元素的下一个兄弟节点</td>
    </tr>
      <tr bgcolor="#333">
        <td>.eq(index)</td>
        <td>$("div").eq(1)</td>
        <td>获取规对应下标的元素</td>
    </tr>
</table>

### 1. .childen()代码演示
**HTML代码**
```HTML
 <div>
     <p>文本1</p>
     <a href="#">链接</a>
</div>
```
**jq代码**
```javascript
     $("div").children("p")
```
**结果**
```javascript
[ <p>文本1</p> ]
```

### 2. .find()代码演示
**HTML代码**
```HTML
<div>
  <p>
      <span>1</span>
  </p>
  <a href="#">链接</a>
</div>
```
**jq代码**
```javascript
    $("div").find("span")
```
**结果**
```javascript
[ <span>1</span> ]
```
### 3. .siblings()代码演示
**HTML代码**
```HTML
<div>
  <p>文本1</p>
  <span>span1</span>
  <span>span2</span>
  <p>文本2</p>
</div>
```
**jq代码**
```javascript
    $("div > p").siblings("span")
```
**结果**
```javascript
[  <span>span1</span>,<span>span2</span> ]
```
### 4. .next()代码演示
**HTML代码**
```HTML
<div>
  <p>文本1</p>
  <span>span1</span>
  <span>span2</span>
</div>
```
**jq代码**
```javascript
    $("div > p").next()
```
**结果**
```javascript
[ <span>span1</span> ]
```
### 5. .eq(index)代码演示
**HTML代码**
```HTML
<div>
  <p>文本1</p>
  <p>文本2</p>
  <p>文本3</p>
</div>
```
**jq代码**
```javascript
    $("div > p").eq(1)
```
**结果**
```javascript
[ <p>文本2</p> ]
```
# jquery操作样式

## 一、css操作

> ### 设置单个样式
>
>  `.css(name,value)`
>
>1. name : 样式名
>2. vaue : 样式值

**参考代码**
```javascript
$("div").css("backgroundColor","#f30");
```
> ### 设置多个样式
>
>  `.css(obj)`
>
>* obj : 对象

**参考代码**
```javascript
$("div").css({
    "width":"200px",
    "backgroundColor":"#f30",
})
```
> ### 获取样式
>
>  `.css(name)`
>
>* name : 样式名

**参考代码**
```javascript
 $("div").css("width")
```
## 二、class操作

> ### 添加类名
>
>  `addClass("name")`
>
>* name : 指定添加的类名

**参考代码**
```javascript
$("div").addClass("content")
$("div").addClass("content con1")
```
> ### 移除类名
>
>  `removeClass("name")`
>
>* name : 指定要移除的类名

**参考代码**
```javascript
$("div").removeClass("content")
$("div").removeClass("content con1")
```
> ### 判断类名
>
>  `hasClass("name")`
>
>* name : 指定要判断的类名
>
>**注意：这里返回的为`Boolean`类型（true，flase）**

**参考代码**
```javascript
if($("div").hasClass("box")){
    alert("有类名")
}else{
    alert("无类名")
}
```
> ### 切换类名
>
>  `toggleClass("name")`
>
>* name : 指定要切换的类名
>
>**原理：当元素没有指定类名时添加指定类名，有时移除**

**参考代码**
```javascript
$("#btn").click(function(){
    $("p").toggleClass("name")
})
```
# jquery操作属性
    这里的属性是指不是在 style="" 里面的属性

## 一、 attr() 方法

> ### 设置单个属性
>
>  `.attr(name,value)`
>
>1. name : 属性名
>2. vaue : 属性值

**参考代码**
```javascript
 $("input").attr("name","Input")
```
> ### 设置多个样式
>
>  `.attr(obj)`
>
>* obj : 对象

**参考代码**
```javascript
$("input").attr({
   "name":"Input",
   "title":"这是input"
 })
```
> ### 获取属性
>
>  `.attr(name)`
>
>* name : 属性名

**参考代码**
```javascript
 $("input").css("type")
```
## 二、 prop() 方法
>### 注意:
>   **对于布尔类型的属性不要用attr方法，应该使用prop方法，使用方法与attr方法一样**

**参考代码**
```javascript
  $("input").prop("checked",true)
```
# jquery 动画

## 一、显示与隐藏
###  1. 显示动画
> `.show([speed],[easing],[callback])`
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript
$("div").show();
$("div").show("slow");
$("div").show(1000);
$("div").show(1000,"linear");
$("div").show(1000,"linear",function(){
    alert("动画执行完")
});
```
###  2. 隐藏动画
> `.hide([speed],[easing],[callback])`
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript
$("div").hide();
$("div").hide("slow");
$("div").hide(1000);
$("div").hide(1000,"linear");
$("div").hide(1000,"linear",function(){
    alert("动画执行完")
});
```
###  3. 切换动画
> `.toggle([speed],[easing],[callback])`
> 
> **原理:如果元素隐藏时执行显示，若显示则显示**
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript

$("div").toggle(1000,"linear",function(){
    alert("动画执行完")
});
```
## 二、 滑入与滑出
### 1. 滑入动画
> `.slideDown([speed],[easing],[callback])`
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript

$("div").slideDown();
$("div").slideDown(1000);
$("div").slideDown("normal");
$("div").slideDown(1000,"swing",function(){});
```
### 2. 滑出动画
> `.slideUp([speed],[easing],[callback])`
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript

$("div").slideUp();
$("div").slideUp(1000);
$("div").slideUp("normal");
$("div").slideUp(1000,"swing",function(){});
```
###  3. 切换滑入滑出动画
> `.slideToggle([speed],[easing],[callback])`
> 
> **原理:如果元素处于滑入状态时执行滑出，若处于滑出状态则执行滑入**
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript

$("div").slideToggle(1000,"linear",function(){
    alert("动画执行完")
});
```
## 三、 淡入与淡出
### 1. 淡入动画
> `fadeIn([speed],[easing],[callback])`
> 
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript

$("div").fadeIn(1000,"linear",function(){
    alert("动画执行完")
});
```
### 2. 淡出动画
> `fadeOut([speed],[easing],[callback])`
> 
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript

$("div").fadeOut(1000,"linear",function(){
    alert("动画执行完")
});
```
###  4. 切换淡入淡出动画
> `.slideToggle([speed],[easing],[callback])`
> 
> **原理:如果元素处于淡入状态时执行淡出，若处于淡出状态则淡入**
#### 参数
>
>1. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>2. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>3. callback : 回调函数，动画执行完后执行函数

**参考代码**
```javascript

$("div").fadeToggle(1000,"linear",function(){
    alert("动画执行完")
});
```
## 四、自定义动画
### 1. animate()函数
> `animate([obj],[speed],[easing],[callback])`

#### 参数
>
>1. obj: 一组包含需要执行动画的属性和属性值的集合
>
>2. speed : 动画执行所需的时间（速度），可以是毫秒值（如10000），也可是字符串["slow","normal","flast"]
>3. easing : 指定动画执行的效果，默认是"swing",也可用参数"linear"
>4. callback : 回调函数，动画执行完后执行函数
**参考代码**
```javascript
$("div").animate({
    width:"200px",
    height:"300px"
},1000,"linear",function(){})
```
### 2. stop()
    停止正在执行的动画
> `stop([clearQueue],[jumpToEnd])`
#### 参数
>
>1. clearQueue: 是否清楚动画队列 （true为清除、false为清除）
>
>2. jumpToEnd : 是否跳转到当前动画的最终效果（true为跳转、false为不跳转

**参考代码** 
```javascript
$("div").stop().animate({
    width:"200px",
    height:"300px"
},1000,"linear",function(){})
```
### 3. 动画队列
    动画队列就是将动画存储到一个对列里面，按照队列将其执行
**参考代码**
```javascript
$("div").animate({
    left:"200px"
    },)
    .animate({
    top:"100px"
    })
    .animate({
    width:"300px"
    })
```
# jquery操作节点

## 1. 创建节点
>`$("<p></p>")`

## 2. 添加节点
>`.append()`

**描述**
>向所匹配的元素内部追加内容(html标签)

**参考代码**
```javascript
$("div").append("<p id='word'></p>")
```
>`.prepend()`

**描述**
>向所匹配的元素内部前置内容(html标签)

**参考代码**
```javascript
$("div").prepend("<p id='word'></p>")
```
>`.appendTo()`

**描述**
>将所匹配的元素追加到另一个元素内容(html标签)

**参考代码**
```javascript
$("<p id='word'></p>").appendTo("div")
```
>`.prependTo()`

**描述**
>将所匹配的元素前置到另一个元素内容(html标签)

**参考代码**
```javascript
$("<p id='word'></p>").prependTo("div")
```
>`.appendTo()`

**描述**
>将所匹配的元素追加到另一个元素内容(html标签)

**参考代码**
```javascript
$("<p id='word'></p>").appendTo("div")
```
>`.after()`

**描述**
>在所匹配的元素的后面添加内容(html标签)

**参考代码**
```javascript
$("p").after("<span></span>")
```
>`.before()`

**描述**
>在所匹配的元素之前添加内容(html标签)

**参考代码**
```javascript
$("p").before("<span></span>")
```
## 3. 清空节点 与 删除节点
>`.html()`

**描述**
>清除元素的内容（不推荐使用，会造成内存泄漏）

**参考代码**
```javascript
$("div").html("")
```
>`.empty()`

**描述**
>删除元素中的所有子节点

**参考代码**
```javascript
$("div").empty("")
```
>`.detach()`

**描述**
>在DOM中删除所有匹配的元素
**HTML代码**
```HTML
<p>文字1</p>
文字2
<p>文字3</p>
```
**参考代码**
```javascript
$("p").detach()
```
**结果**
```javascript
文字2   
```
## 4. 克隆
>`.clone(boolean)`

**描述**
>克隆所匹配的元素并且选中元素中的副本
#### 参数
>
>1. Boolean: (true/false)决定事件是否被克隆,默认为false
>
**HTML代码**
```HTML
<span>文字1</span>
<p>文字3</p>
```
**参考代码**
```javascript
$("p").clone(true).appendTo("span")
```
**结果**
```HTML
<span>
    文字1
    <p>文字3</p>    
</span>
<p>文字3</p>  
```
# jquery特殊属性操作
## 一、val()方法
>用来获取和设置表单元素的值
### 1. 获取
> `$("input).val()`

### 2. 设置
> `$("input").val("提交")`

## 二、 width()和height()
> 用来获取和设置元素得宽高

### 1. 获取
> `$("div").with()`//获取宽度

> `$("div").height()`//获取高度

### 2. 设置
> `$("div").width(200)`//设置高度

> `$("div").height(200)`//设置高度

### 3. innerwidth()
> 获取所匹配元素的内部区域宽度（padding+width）

> `$("div").innerwidth()`

### 4. innerheight()
> 获取所匹配元素的内部区域高度（padding+height）

> `$("div").innerheight()`

### 5. outerwidth([option])
> 获取所匹配元素的外部区域高度（padding+width+border）

**参数**

1. true : 可获取边距(padding+width+border+margin)
2. false : 默认不获取边距
> `$("div").outerwidth(true)`

### 6. outerheight([option])
> 获取所匹配元素的外部区域高度（padding+height+border）

**参数**

1. true : 可获取边距(padding+height+border+margin)
2. false : 默认不获取边距
> `$("div").outerwidth(true)`

## 三、 scrollTop() 与 scrollLeft()
> 获取和设置元素相对与滚动条垂直和水平方向偏移位置

### 1. scrollTop()
###  获取
> `$("p").scrollTop()`

###  设置
> `$("p").srollTop(10)`

### 2. scrollLeft()
###  获取
> `$("p").scrollLeft()`

###  设置
> `$("p").srollLeft(10)`

## 四、offset() 与 position()
> 获取元素的位置，返回的是一个对象

### 1. offset()
> 获取元素相对于document的位置

> `$("div").offset()`
### 2. position()
> 获取元素相对于有定位父级u的位置

> `$("p").position()`

# jquery 事件机制
## 一、 jquery 事件发展历程
简单事件绑定————>bind事件绑定————>delegate事件绑定————>on事件绑定
### 1. 简单事件绑定（一次只能注册一个事件）
```javascript
$("div").click()
$("div").mousenenter()
```
### 2. bind()事件绑定
```javascript
$("div").bind("click mouseenter",function(){
    console.log("bind")
})
```
### 3. delegate()委托事件
> 给元素注册委托事件，最终不是所匹配元素执行，而是由子元素执行，优点是能为动态创建的元素注册事件，缺点是只能注册委托事件

> `$("div").delegate(element,"type",callback)`

**参数**

1. element : 最终执行事件的元素
2. type : 执行事件类型
3. callback : 事件所执行的功能
   
**代码演示**
```javascript
$("div").delegate("p","click",function(){
    console.log("p元素执行事件")
})
```
### 4. on()事件
> 统一所有事件的处理方法

1. 给元素自身注册事件
   
```javascript
$("div").on("click",function(){
    console.log("div执行事件")
})
```
2. 给元素添加委托事件
   
```javascript
$("div").on("p","click",function(){
    console.log("p元素执行事件")
})
```
## 二、 事件的执行顺序
> 先执行自己的委托事件，然后再执行自身的事件

## 三、 事件解绑
> `off()`

**参数**
1. 不带参数： 解除所有的匹配元素的事件
2. 带参数 : 接触匹配元素所规定的事件`.off("click")`
   
## 四、 触发事件
> `trigger([type],[data])`

**参数**
1. type : 一个事件对象要触发的事件类型
2. data ：传递给事件处理函数的附加参数
   
**代码演示**
```javascript
$("div").trigger("click","hello")    
```
# jquery 事件对象
    jquery 事件对象其实就是js事件对象的一个封装，处理了兼容性
1. e.screenX与screenY : 对应屏幕最左上角的值
2. e.clientX与e.clientY : 距离页面左上角的位置（忽视滚动条）
3. e.PageX 与 e.PageX : 距离页面最顶部左上角的位置（会计滚动条距离）
4. e.preventDefault() : 阻止浏览器默认事件
5. e.stoppropagation() : 阻止冒泡事件
6. return false : 阻止浏览器默认事件()
7. return flase : 既能阻止浏览器默认事件也能阻止冒泡事件
   
# 链式编程
* 设置型操作可链式编程
* 获取性操作不可链式编程，因为获取性操作返回值为数值，字符串不是jquery对象

# end()方法
当获取性操作不能返回jquery对象是，在后面加.end()方法，会让其恢复到上一个jquery对象的状态

# each()方法
> jquery中的遍历


> `.each(index,element)`

**参数**
1. index: 选择器下标
2. element : 当前元素

**代码演示**
```javascript
$("li").each(index,element){
    $(element).css("opacity",(index+1)/10)
}
```
# jquery 中的插件
    jquery不可能有所有功能，我们可以通过插件扩展jquery的功能
## 一、 jquery.color.js(颜色最好使用16进制)
**使用**

1. 先引入jquery的js文件
> `<script src="jquery.js"></script>`

2. 再引入jquery.color.js文件
> `<script src="jquery.color.js"></script>`

**代码演示**
```javascript
$("div").animate("backgroundColor","red");
```
## 一、 jquery.Lazyload.js(颜色最好使用16进制)
**使用**

1. 先引入jquery的js文件
> `<script src="jquery.js"></script>`

2. 再引入jquery.color.js文件
> `<script src="jquery.Lazyload.js"></script>`

**HTML代码**

```html
<img class="Lazy" data-original="01.jpg"/>
```
**jq代码**
```javascript
$("img.Lazy").lazyload()
```
## 三、 制作jquery插件
    制作jquery插件其就是在jquery的原型上添加方法
**封装**
```javascript
$(function(){
    $.fn.bgc = function(color){
        this.css("backgroundColor",color);
        return this;
    }
})
```
**使用**
```javascript
$(function(){
  $("div").bgc("#f30")
})
```