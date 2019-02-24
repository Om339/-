#### JavaScript的组成
1. 核心（ECMAScript）
2. 文档对象模型（DOM）
3. 浏览器对象模型（BOM）

#### 在HTML中使用JavaScript
##### <script>元素
1. 属性：
   1. asyns：立即下载脚本，不妨碍页面中其他操作。（只对外部脚本文件有效）
   2. charset：通过scr属性指定的代码的字符集。（少用）
   3. defer：脚本可延迟到文档完全被解析和显示之后再执行。（只对外部脚本文件有效）
   4. src：包含要执行代码的外部文件。
   5. type：（language）编写代码使用的脚本语言的内容类型。
   6. ecmascript（不是必需的）
2. 插入方式：
###### 直接放在元素内部
```
<script type="text/javascript">
</script>
```
==当遇到"</script>"时，就会认为那是结束的</script>标签。通过转义字符" / "解决这个问题。（即"<\/script>")==
###### 外部链接

```
<script type="text/javascript" src="example.js"></script>
```
*<script>也可以指向当前HTML页面所在域之外的某个域中完整的URL。
按先后顺序解析。*
3. 标签的位置
   1.<head>中，遇到<body>才开始呈现内容，导致出现延迟
   2.<body>中（主要内容后面），可避免上述问题
4. 延迟脚本

```
<script type="text/javascript" defer="defer" src="example.js"></script>
```
浏览器立即下载，但延迟执行(遇到</htm>执行）。按先后顺序执行。
5. 异步脚本

```
<script type="text/javascript" async src="example.js"></script>
```
不一定按先后顺序执行。会在load事件前执行。
6. 在XHTML中的用法("<"解析错误)
   1. "&lt;"代替"<"
   2.
   
```
<script type="text/javascript"><![CDATA[
]]></script>
```
7. 外部文件优点：可维护性；可缓存；适应未来。
8. <noscript>元素：脚本无效下向用户显示一条消息。
#### 基本概念
1. 语法
   1. 区分大小写
   2. 标识符：变量、函数、属性的名字。
   *第一个字符是字母或下划线或$*
   3. 注释
      1. 单行注释 //
      2. 块级注释 
      
      ```
      /*
       *
       *
       */
       ```
    4. 严格模式
    
    ```
    顶部或函数内添加
    *use strict*;
    ```
    5. 语句:
    **不要省略 ";"和"{}"**
       
2.关键字和保留字
3.变量
  1. 推荐使用var输入变量。
  2. 函数中的变量是局部变量，推出函数就会被销毁。（函数中省略var，创建的是全局变量，不推荐）
  3. 一个语句可以定义多个变量。
  
   ```
   var message = 1，
       age = 2；
   ```
4. 数据类型
   1. 简单：
      1. Undefined：未定义(var message;变量默认获得undefin值)
      2. Null：空对象指针（typeof检测到null会返回object)
      3. Boolean：布尔值
         ```
         graph LR
         Boolean-->String/Number/Object/Undefined
         ture-->任何非空字符/任何非零数值/任何对象/n/a
         false--> **/0和NaN/null/undefined
         ```
      4. Number：数字  
      intnum 十进制整数  
      octalNum 八进制  
      hexnum 十六进制  
      floatNum 浮点数值 0.1（最高精度是17位小数）  
      超过最大值会转化位正无穷infinity值  
      NaN(not a number)本来要返回数值但未返回数值，与任何值都不同。isNaN函数：不能被转换为数值的都显示true
      5. String：字符串(")/(')
   2. 复杂: Object：对象或null
   3. typeof:测定变量类型
    
    ```
    var message = "some string";
    alert(typeof message);     //"string"
    alert(typeof 95);          //"number"
    ```
   4. 数值转换
       1. Number()
       
       ```
        graph LR
        ture/false-->1/0
        null-->0
        undefined-->NaN
       ```
       "123"-->123;"011"-->11;空的-->0;其它字符-->NaN;十六进制-->十进制.
       2. parseInt():处理整数常用（忽略1234blue中的blue部分，小数点后内容）
       3. parseFloat()：和parseInt()相似，但可解析第一个小数点，只解析十进制,忽略前面的0。
   5. 字符串转换  toString
5. 操作符
   1. 一元操作符：++age （age加一）； --age（age减一）P38-39。
   2. 位操作符
   3. 布尔操作符
   4. 乘性操作符：乘法*，除法/
   5. 加性操作符：+，-
   6. 关系操作符：<,>,<=,>=
   7. 相等操作符：相等（==），不相等（！=）,全等（===），不全等（！===）。  
   *一个数是NaN,相等返回false，不相等返回ture*
   
     ```
     var result = ("55" == 55);   //ture
     var result = ("55" === 55); //false
     ```
     8. 条件操作符
     ```
     var max = (num1 > num2) ? num1 : num2;
     //max 中会保存一个较大的值
     ```
     9.赋值操作符：=，+=，*=，左移/赋值(<<=),有符号右移/赋值(>>=),无符号右移/赋值(>>>=)。
     10.逗号操作符
6. 语句

```
if(i > 25){
    alert("ture");
}else{
    alert("false");
}                                   //if语句

```

```
var i = 0;
do {
    i += 2;
}while(i < 10);
alert(i)                            //do-while语句

```

```
var i = 0;
while (i < 10){
    i += 2;
}                                  //while语句
```

```
var count = 10;
for(var i = 0;i < count; i++){
    alert(i);
}                                  //for语句
for(;;){                           //无限循环
    dosomething();
}
```

```
for (var proName in window){
    document.write(proName);
}                                  //for-in语句
```

```
start: for (var i=0;i < count;i++){
    alert(i);
}                                  //label语句
```

```
var num = 0;
for(var i=1;i < 10;i++){
    if(i & 5 == 0){
        break;
    }
    num++;
}
alert(num);                         //4 break语句(推出循环，执行循环后面的语句)
var num = 0;
for(var i=1;i < 10;i++){
    if(i & 5 == 0){
        continue;
    }
    num++;
}
alert(num);                         //8 continue语句(退出循环，从循环顶部继续执行)
//break，continue语句可与label语句连用，如：break outermost
```

```
with（location）{
    var qs = search。substring(1);
    var url = href;
}                                   //with语句
<!--var qs = location.search.substring(1);-->
<!--var url = href;-->
```

```
switch(i){
    case 25:
        alert("25");
        break;
    case 35:
        alert("35");
        break;
    default:
        alert("45");
}                                   //switch语句
//删除break，合并两种情形
<!--if(i == 25){-->
<!--    alert("25");-->
<!--}else if (i == 35){-->
<!--    alert("35");-->
<!--}else{-->
<!--    alert("45");-->
<!--}-->
```

7. 函数：function  
==return后面的代码都不会执行==  
同样的函数被定义了两次，后面的会覆盖前面的。
#### 变量、作用域和内存问题
1. 基本类型和引用类型的值
   1. 动态的属性：只能给引用类型值动态地增加属性’
   2. 复制变量值：
       ```
       var obj1 = new Object();
       var obj2 = obj1;
       obj1.name = "Amy";
       alert(obj2.name);         //"Amy"
       ```
   3. 传递参数
        ```
        function setName(obj){
            obj.name = "Amy";
        }
        var person = new Object();
        setName(person);
        alert(person.name);       //"Amy"
        ```
   4. 检测类型  
     alert(typeof a);  
     alert(person instanceof Object);
2. 执行环境及工作域
    1. 延长工作域链：try-catch语句的catch块；with语句。
    2. 没有块级工作域
3. 垃圾收集：标记清除，引用计数（对象 = null），性能问题，管理内存
#### 引用类型
1. Object类型
```
var person = new Object();    //{}等于new Object()
person.name = "Amy";
person.age = 29;
```

```
var person = {
    name : "Amy",
    age : 29
};
```
"[]"优点：通过变量访问属性；有导致语法错误的字符。
2. Array类型

```
var colors = new Array();   //长度为20的数组
```

```
var colors = ["red","blue","green"]
alert(color[0]);                //显示第一项
color[2] = "black";             //修改第三项
```

```
//检测数组
if (Array.isArray(value){
    //对数组执行某些操作
}
```
==转换方法：join();toLocaleString();toString();valueOf()==  
toLocaleString()可调用每一项的值  
##### 栈方法
==push()==：接受任意数量的参数，把它们逐个添加到数组末尾，并返回修改数组的长度。 
==pop()==：从数组末尾移除最后一项，减少数组的length值，然后返回移除的项。  
##### 队列方法
==shift()==：移除数组中的第一项并返回该项，同时将数组长度减一。 var item = colors.shift();
##### 重排序方法
==reverse()==:反转数组项的顺序。values.reverse();
==sort()==:按升序排列数组项，比较字符串。valuse.sort();
##### 操作方法
==concat()==:基于当前数组中的所有项创建一个新的数组，如果传递的值不是数组，这些值就会被简单地添加到结果数组的末尾。

```
var colors = ["red","green"];
var colors2 = colors.concat("yellow",["black","brown"]);
alert(colors2);     //red,green,yellow,black,blown
```
==slice()==:基于当前数组中的一个或多个项创建一个数组。不会影响到原始数组。在只有一个参数的情况下，slice()方法返回从该参数指定位置开始到当前数组末尾的所有项，如果有两个参数，该方法返回起始和结束位置之间的项，但不包括结束位置的项。
==splice()==:删除（指定两个参数，要删除的第一项和要删除的项数）；插入（提供三个参数，起始位置、0、要插入的项）；替换（指定三个参数，起始位置、要删除的项数、要插入的任意数量的项）
##### 位置方法
==indexOf()、lastIndexOf()==:两个参数，要查找的项和查找起点位置的索引（indexOf从数组开头，lastIndexOf从数组末尾开始查找）
##### 迭代方法
==every()==:对数组中的每一项运行给定函数，如果该函数对每一项都返回true,则返回flase。  
==filter()==:对数组中的每一项运行给定函数，返回该函数会返回true的项组成的数组。  
==forEach()==:对数组中的每一项运行给定函数。这个方法没有返回值。  
==map()==:对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。  
==some()==: 对数组中的每一项运行给定函数，如果该西数对任一项返回true,则返回true。 
以上方法都不会修改数组中的包含的值
##### 归并方法
==reduce() 、reduceRight()==：迭代数组的所有项，然后构建一个最终返回的值。reduce()方法从数组的第一项开始，逐个遍历到最后。reduceRight ()从数组的最后一项开始， 向前遍历到第一项。
3. Date类型（P99-102)
4. RegExp类型（正则）  
var expression = /pattern/ flags；  
==g==：全局模式，所有字符串。  
==i==：不区分大小写模式。  
==m==：多行模式，查找下一行是否存在匹配的项。  
*RegExp函数，$（）见P108-109*
5. Function类型
   1. 没有重载
   2. argument：保存函数参数
        ```
        function factorial(num){
            if(num < 1){
                return 1;
            }else{
                return num*factorial(num-1);
            }
        }
        //用arguments.callee代替factorial，消除紧密耦合的现象
        ```
    3. this：引用的是函数执行的环境对象。（当网页的全局作用域中调用函数时，this的引用对象就是window，this.color = window.color)
    4. 函数属性：length（函数希望接受的命名参数的个数）；prototype。  
    apply()方法接受两个参数：其中运行函数的作用域，参数数组（可以是Array实例也可以是arguments对象。  
    call()和apply()相似，但是第二个参数必须逐个列举出来。  
    bind():创建一个函数实例，this的值会传到bind函数的值。
6. 基本包装类型
###### Boolean类型

```
var booleanObject = new Boolean(ture);
```
###### Number类型

```
var num = 10;
alert(num.toString());              //"10"（10进制）
alert(num.toString(8));             //"12"（8进制）
alert(num.toFixed(2));              //"12.00"（指定小数位）
alert(num.toExponential(1));        //"1.0e+1"（e表示法，小数位数）
```

```
var num = 99;
alert(num.toPrecision(2));           //"99"
alert(num.toPrecision(1));           //"1e+2"
alert(num.toPrecision(2));           //"99.0"
//toPrecision决定调用toExponential还是toFixed
```
###### String类型
==charAT==：接受一个参数，基于0的字符位置，以单字符字符串的形式返回给定位置的那个字符。
==charCodeAt()==：接受一个参数，基于0的字符位置，返回字符编码。
==concat==:将一或多个字符串拼接起来，返回拼接得到的新字符串，

```
var a = "hello";
var result = a.concat("world","!");
alert(result);                  //"hello world!"
```
==slice(),substr(),substring()==:接受一或两个参数。第一个参数指定子字符串开始的位置，第二个参数本事到哪里结束。silce(),substring()的第二个参数指定的是子字符串最后一个字符后面的位置。substr()的第二个参数是返回的字符的个数。  
==indexOf()，lastIndexOf()==  
==trim()==:创建一个字符串的副本，删除前置及后缀的所有的空格，然后返回结果。
```
var stringValue ="   hello world  ";
var trimmedstringValue = stringValue.trim();
alert(stringValue);            //"     hello world   "
alert(trimmedStringValue);     //"hello world"
```
==toLowerCase()、toLocaleLowerCase()、toUpperCase()和toLocaleUpperCase()==。

```
var stringValue = "hello world";
alert(stringValue.toLocaleUpperCase());     //"HELLO WORLD"
alert(stringValue.toUpperCase());           //"HELLO WorLD"
alert(stringValue.toLocaleLowerCase());     //"he1lo world"
alert(stringValue.tolowerCase());           //"hello world"
```
==match==:只接受一个参数，要么正则表达式，要么是RepExp对象。  
==search==：参数同上，返回第一个匹配项的索引，没有就返回-1。  
==replace==:两个参数，第一个同上，第二个可以是一个字符串或一个函数。
```
var result = text.replace(/at/g,"ond");
var pos = text.search(/at/);
```
==split()==:第一个参数是分隔符（可以是字符串，也可以是RegExp对象），可接受第二个参数，指定数组的大小。
==localeOCompare==：字符串在字母表中应该排在字符串参数之前，则返回一个负数，等于返回0。
```
var a = "yellow";
alert(a.localeOCompare("brick"));       //1
```
==fromCharCode==：接收一或多个字符编码，然后将它们转换成一个字符串。alert(String.fromCharCode(104,101,108,111)); //"hello"
7. 单体内置对象
    1. Global对象
    2. eval()方法：eval("function sayHi() {alert('hi');});
    3. Math.ceil(向上舍入),Math.floor(向下舍入),Math.round(标准舍入),min(),max()，random().
#### 面对对象的程序设计
1. 理解对象  
[[Cofigurable]]: 表示能否通过delete删除属性从而重新定义属性，能否修改属性的特性，或者能否把属性修改为访问器属性。默认值为true。  
[[Enumerable]]:表示能否通过for-in循环返回属性。默认值为true。  
[[Writable]]:表示能否修改属性的值。默认值为true。  
[[Value]]:包含这个属性的数据值。读取属性值的时候,从这个位置读;写入属性值的时候,把新值保存在这个位置。默认值为undefined  。  
[[get]]:在读取属性时调用的函数。默认值为undefined。   
[[Set]]:在写入属性时调用的函数。默认值为undefined。
2. 创建对象  
###### 工厂模式
定义一种函数，用函数来封装以特定的接口创建对象的细节。

```
function createPerson(name,age,job){
    var o = new Object();
    o.name = name;
    o.age = age;
    o.sayName = function(){
        alert(this.name);
    };
    return o;
}
var person1 = createPerson("Amy",29,"teacher");
```

###### 构造函数模式

```
function Person(name,age,job){
    this.name = name;
    this.age = age;
    this.sayName = function(){
        alert(this.name);
    };   //this.sayName = new Function("alert(this.name)");等价
}
var person1 = Person("Amy",29,"teacher");
```
###### 原型模式

```
function Person(){
}
Person.prototype.name = "Amy";
Person.prototype.age = 29;
Person.prototupe.sayName = function(){
    alert(this.name);
};
var person1 = new Person();
person1.sayName();                         //"Amy"
person1.name = "Greg";
alert(person1.name);                       //"Grey"
delete(person1.name);
alert(person1.name);                       //"Amy"
alert（person1.hasOwnProperty("name"));    //false来自原型;hasOwnProperty()方法检测一个属性是存在域实例中还是存在于原型中。
alert("name" in person1);                  //ture来自原型
```

```
function Person(){
}
Person.prototype = {
    constructor :Person,
    name : "Amy",
    friends :["Shelly","Bell"]
};
var person1 = new Person();
var person2 = new Person();
person1.friends.push("Van");
alert(person1.friends);                //"Shelly,Bell,Van"
alert(person2.friends);                //"Shelly,Bell,Van"

```

###### 组合使用构造函数模式和原型模式
组合构造函数模式和原型模式(P159)
###### 动态原型模式

```
function Person(name,age){
    this.name = name;
    this.age = age;
    if(typeof this.sayName !="function"){
        Person.prtotypr.sayName = function(){
            alert(this.name);
        };
    }
}
var friend = new Person("Amy",29);
friend.sayName();
```

###### 寄生构造函数模式

```
function Person(name,age){
    var o =new Object();
    o.name = name;
    o.age = age;
    o.sayName =function(){
        alert(this.name);
    };
    return o;
}
var friend = new Person("Amy",29);
friend.sayName();                         //"Amy"
```

###### 稳妥构造函数模式

```
function Person(name,age){
    var o =new Object();
    o.sayName =function(){
        alert(this.name);
    };
    return o;
}
var friend = new Person("Amy",29);
friend.sayName();                         //"Amy"
```

3. 继承
###### 原生链：利用原型让一个引用类型继承另一个引用类型的属性和方法。

```
function SuperType(){
    this.property = true;
}
SuperType.prototype.getSuperValue = function(){
    return this.property;
};
function SubType(){
    this.subproperty = false;
}               //继承了SuperType
SubType.prototype = new SuperType();
Subtype.prototype.grtSubValue = function(){
    return this.subproperty;
};
var instance = new SubType();
alert(instance.getSuperValue());             //true
```
###### 构造函数  P167
###### 组合继承  P168
###### 原型式继承  P169
###### 寄生式继承   P171
###### 寄生组合式继承  P172
#### 函数表达式
##### 递归 一个函数通过调用自身名字的情况下构成的

```
var factorial =( function f(num){
    if (num < 1){
        return 1;
    }else{
        return num*f(num-1);
    }
});
```
##### 闭包 有权访问另一个函数作用域中的变量的函数
创建匿名函数

```
function createFunction(){
    var result = new Array();
    for(var i=0;i < 10;i++){
        result[i] = function(num){
            return function(){
                return num;
            };
        }(i);
    }
    return result;
}
```
##### 模仿块级作用域
```
(function(){
    //这里是块级作用域
})();
```
##### 私有变量
1. 静态私有变量：与特权函数的区别，由实例共享的。
2. 模块模式：单例（只有一个实例的对象）创建私有变量和特权的方法。

```
var singleton = function(){
    var privateVarible = 10;
    function prtvateFunction(){
        return false;
    }
    return {
        publicProperty:true;
        publicMethod:function(){
            privateVariable++;
            return privateFunction();
        }
    };
}();
```











