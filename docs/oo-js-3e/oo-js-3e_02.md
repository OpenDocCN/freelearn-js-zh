# 第二章：原始数据类型、数组、循环和条件

在深入研究 JavaScript 的面向对象特性之前，让我们首先看一些基础知识。本章将介绍以下主题：

+   JavaScript 中的原始数据类型，如字符串和数字

+   数组

+   常见运算符，如`+`、`-`、`delete`和`typeof`

+   流程控制语句，如循环和`if...else`条件

# 变量

变量用于存储数据；它们是具体值的占位符。编写程序时，使用变量而不是实际数据更方便，因为写`pi`比写`3.141592653589793`要容易得多；特别是当它在程序中多次出现时。存储在变量中的数据可以在最初分配后进行更改，因此称为**变量**。您还可以使用变量存储在编写代码时对您未知的数据，例如稍后操作的结果。

使用变量需要以下两个步骤。您需要：

+   声明变量

+   初始化它，即给它一个值

要声明变量，您将使用`var`语句，如下面的代码片段：

```js
    var a; 
    var thisIsAVariable;  
    var _and_this_too;  
    var mix12three; 

```

对于变量的名称，可以使用字母、数字、下划线字符和美元符号的任何组合。但是，不能以数字开头，这意味着以下代码声明无效：

```js
    var 2three4five; 

```

初始化变量意味着为第一次（初始）赋予它一个值。以下是两种方法：

+   首先声明变量，然后初始化它

+   声明并用单个语句初始化它

后者的示例如下：

```js
    var a = 1; 

```

现在名为`a`的变量包含值`1`。

您可以使用单个`var`语句声明，并可选择初始化多个变量；只需用逗号分隔声明，如下行代码所示：

```js
    var v1, v2, v3 = 'hello', v4 = 4, v5; 

```

为了可读性，通常使用每行一个变量来编写，如下所示：

```js
    var v1,  
        v2,  
        v3 = 'hello',  
        v4 = 4,  
        v5; 

```

### 注意

变量名称中的$字符

您可能会看到变量名称中使用美元符号字符（`$`），如`$myvar`或不太常见的`my$var`。变量名称中允许此字符出现在任何位置，尽管以前的 ECMA 标准版本不鼓励在手写程序中使用它，并建议它只能在生成的代码（由其他程序编写的程序）中使用。JavaScript 社区并不太尊重这个建议，实际上$在实践中常用作函数名。

## 变量区分大小写

变量名称区分大小写。您可以轻松通过 JavaScript 控制台验证此语句。尝试按下每行后的*Enter*键输入以下代码：

```js
    var case_matters = 'lower'; 
    var CASE_MATTERS = 'upper';  
    case_matters; 
    CASE_MATTER; 

```

在输入第三行时，为了节省按键次数，您可以输入`case`并按*Tab*或右箭头键。**Console**会自动将变量名补全为`case_matters`。类似地，对于最后一行，输入`CASE`并按*Tab*键。最终结果如下图所示：

![变量区分大小写](img/image_02_001-e1482738938732.jpg)

在本书的其余部分，只提供示例的代码，而不是屏幕截图，如下所示：

```js
    > var case_matters = 'lower'; 
    > var CASE_MATTERS = 'upper'; 
    > case_matters; 
    "lower" 
    > CASE_MATTERS; 
    "upper" 

```

大于号（`>`）显示您键入的代码；其余部分是**Console**中打印的结果。再次提醒，当您看到这样的代码示例时，强烈建议您自己键入代码。然后，您可以通过稍微调整代码来进行实验，以更好地了解其工作原理。

### 注意

你可以在前面的截图中看到，有时你在**控制台**中输入的内容会导致**undefined**这个词。你可以简单地忽略它，但如果你好奇的话，当评估（执行）你输入的内容时，**控制台**会打印返回的值。一些表达式，比如`var a = 1;`，不会显式地返回任何东西，在这种情况下，它们会隐式地返回特殊值**undefined**（稍后会详细介绍）。当一个表达式返回某个值（例如，前面例子中的`case_matters`或类似`1 + 1`的东西）时，结果值会被打印出来。并非所有的控制台都会打印**undefined**值；例如，Firebug 控制台。

# 运算符

运算符接受一个或两个值（或变量），执行一个操作，并返回一个值。让我们看一个使用运算符的简单例子，以澄清术语：

```js
    > 1 + 2; 
    3 

```

在上面的代码中：

+   `+`符号是运算符

+   操作是加法

+   输入值是`1`和`2`（它们也被称为操作数）

+   结果值是`3`

+   整个东西被称为表达式

不要直接在表达式中使用值`1`和`2`，你可以使用变量。你也可以使用一个变量来存储操作的结果，如下面的例子所示：

```js
    > var a = 1; 
    > var b = 2; 
    > a + 1; 
    2 
    > b + 2; 
    4 
    > a + b; 
    3 
    > var c = a + b; 
    > c; 
    3 

```

以下表格列出了基本的算术运算符：

| **运算符符号** | **操作** | **示例** |
| --- | --- | --- |
| `+` | 加法 |

```js
> 1 + 2;   
3   

```

|

| `-` | 减法 |
| --- | --- |

```js
> 99.99 - 11;   
88.99   

```

|

| `*` | 乘法 |
| --- | --- |

```js
> 2 * 3;   
6   

```

|

| `/` | 除法 |
| --- | --- |

```js
> 6 / 4;   
1.5   

```

|

| `%` | 取模，除法的余数 |
| --- | --- |

```js
> 6 % 3;   
0   
> 5 % 3;   
2   

```

有时候测试一个数字是偶数还是奇数是很有用的。使用取模运算符，很容易做到这一点。所有奇数被 2 整除时返回`1`，而所有偶数返回`0`，例如：

```js
> 4 % 2;   
0   
> 5 % 2;   
1   

```

|

| `++` | 将值增加`1` | 后增加是指在返回之后增加输入值，例如：

```js
> var a = 123;    
> var b = a++;   
> b;   
123   
> a;   
124   

```

相反的是前增加。输入值首先增加`1`，然后返回，例如：

```js
> var a = 123;    
> var b = ++a;   
> b;   
124   
> a;   
124   

```

|

| `--` | 将值减 1 | 后减：

```js
> var a = 123;    
> var b = a--;   
> b;   
123   
> a;   
122   

```

前减：

```js
> var a = 123;    
> var b = --a;   
> b;   
122   
> a;   
122   

```

|

`var a = 1;`也是一个操作；它是简单的赋值操作，`=`是**简单赋值运算符**。

还有一类运算符，它们是赋值和算术运算符的组合。这些被称为**复合运算符**。它们可以使你的代码更加简洁。让我们看一些例子：

```js
    > var a = 5; 
    > a += 3; 
    8 

```

在这个例子中，`a += 3;`只是`a = a + 3;`的一种更简洁的方式。例如：

```js
    > a -= 3; 
    5 

```

在这里，`a -= 3;`和`a = a - 3;`是一样的：

```js
    > a *= 2; 
    10 
    > a /= 5; 
    2 
    > a %= 2; 
    0 

```

除了之前讨论的算术和赋值运算符之外，还有其他类型的运算符，你将在本章和下一章中看到。

### 注意

**最佳实践**

始终用分号结束你的表达式。JavaScript 有一个分号插入机制，如果你忘记在行尾加上分号，它会自动添加分号。然而，这也可能是一个错误的来源，所以最好确保你总是明确地声明你想要结束表达式的地方。换句话说，`> 1 + 1`和`> 1 + 1;`都可以工作；但在整本书中，你总是会看到第二种类型，以分号结束，只是为了强调这个习惯。

# 基本数据类型

你使用的任何值都是某种类型的。在 JavaScript 中，以下是一些基本的数据类型：

1.  **数字**：这包括浮点数和整数。例如，这些值都是数字-`1`，`100`，`3`.`14`。

1.  **字符串**：这些由任意数量的字符组成，例如，`a`，`one`和`one 2 three`。

1.  **布尔**：这可以是`true`或`false`。

1.  **未定义**：当你尝试访问一个不存在的变量时，你会得到特殊值未定义。当你声明一个变量但尚未给它赋值时，也会发生同样的情况。JavaScript 在幕后用值`undefined`初始化变量。未定义数据类型只能有一个值-特殊值`undefined`。

1.  **Null**：这是另一种特殊的数据类型，只能有一个值-`null`值。它表示没有值，空值或无。与未定义的区别在于，如果变量具有空值，则仍然已定义；只是它的值恰好是空的。您很快就会看到一些例子。

不属于这里列出的五种原始类型之一的任何值都是对象。甚至 null 也被认为是对象，这有点尴尬，有一个（东西）实际上是什么都没有的对象。我们将在第四章*对象*中了解更多关于对象的知识，但目前，只需记住在 JavaScript 中，数据类型如下：

+   原始（先前列出的五种类型）

+   非原始（对象）

## 查找值类型-typeof 运算符

如果您想知道变量或值的类型，可以使用特殊的`typeof`运算符。此运算符返回表示数据类型的字符串。使用`typeof`的返回值是以下之一：

+   数字

+   字符串

+   布尔值

+   未定义

+   对象

+   函数

在接下来的几节中，您将看到`typeof`在使用每种五种原始数据类型的示例中的作用。

## 数字

最简单的数字是整数。如果将`1`分配给变量，然后使用`typeof`运算符，它将返回字符串`number`，如下所示：

```js
    > var n = 1; 
    > typeof n; 
    "number" 
    > n = 1234; 
    > typeof n; 
    "number" 

```

在前面的示例中，您可以看到第二次设置变量值时，不需要`var`语句。

数字也可以是浮点数（小数），例如：

```js
    > var n2 = 1.23; 
    > typeof n; 
    "number" 

```

您可以直接在值上调用`typeof`，而无需首先将其分配给变量，例如：

```js
    > typeof 123; 
    "number" 

```

### 八进制和十六进制数

当数字以`0`开头时，它被视为八进制数。例如，八进制`0377`是十进制`255`：

```js
    > var n3 = 0377; 
    > typeof n3; 
    "number" 
    > n3; 
    255 

```

前面示例中的最后一行打印了八进制值的十进制表示。

ES6 提供了一个前缀`0o`（或`0O`，但在大多数等宽字体中看起来非常令人困惑）来表示八进制。例如，考虑以下代码行：

```js
    console.log(0o776); //510 

```

虽然您可能不太熟悉八进制数，但您可能已经在 CSS 样式表中使用十六进制值来定义颜色。

在 CSS 中，您有几种选项来定义颜色，其中两种如下：

+   使用十进制值来指定 R（红色）、G（绿色）和 B（蓝色）的数量，范围从`0`到`255`。例如，*rgb(0, 0, 0)*是黑色，*rgb(255, 0, 0)*是红色（红色的最大量，没有绿色或蓝色）。

+   使用十六进制并为每个 R、G 和 B 值指定两个字符。例如，*#000000*是黑色，*#ff0000*是红色。这是因为*ff*是`255`的十六进制值。

在 JavaScript 中，您可以在十六进制值之前加上`0x`，也称为十六进制，例如：

```js
    > var n4 = 0x00; 
    > typeof n4; 
    "number" 
    > n4; 
    0 
    > var n5 = 0xff; 
    > typeof n5; 
    "number" 
    > n5; 
    255 

```

### 二进制文字

直到 ES6，如果您需要整数的二进制表示，您必须将它们作为字符串传递给`parseInt()`函数，基数为`2`，如下所示：

```js
    console.log(parseInt('111',2)); //7 

```

在 ES6 中，您可以使用`0b`（或`0B`）前缀表示二进制整数。例如：

```js
    console.log(0b111); //7 

```

### 指数文字

`1e1`（也写作`1e+1`或`1E1`或`1E+1`）表示数字 1 后面跟着一个 0，换句话说，是`10`。同样，`2e+3`表示数字 2 后面跟着三个 0，或者`2000`，例如：

```js
    > 1e1; 
    10 
    > 1e+1; 
    10 
    > 2e+3; 
    2000 
    > typeof 2e+3; 
    "number" 

```

`2e+3`表示将数字**2**的小数点向右移动三位。还有`2e-3`，意思是将数字**2**的小数点向左移动三位。看一下下面的图：

![指数文字](img/image_02_002.jpg)

以下是代码：

```js
    > 2e-3; 
    0.002 
    > 123.456E-3; 
    0.123456 
    > typeof 2e-3; 
    "number" 

```

### 无穷大

JavaScript 中有一个称为 Infinity 的特殊值。它表示 JavaScript 无法处理的数字太大。Infinity 确实是一个数字，因为在控制台中键入`typeof Infinity`将确认。您还可以快速检查具有`308`个零的数字是否正常，但`309`个零太多。准确地说，JavaScript 可以处理的最大数字是`1.7976931348623157e+308`，而最小数字是`5e-324`，请看下面的示例：

```js
    > Infinity; 
    Infinity 
    > typeof Infinity; 
    "number" 
    > 1e309; 
    Infinity 
    > 1e308; 
    1e+308 

```

除以零会得到无穷大，例如：

```js
    > var a = 6 / 0; 
    > a; 
    Infinity 

```

`Infinity`是最大的数（或者比最大的数稍微大一点），但最小的数呢？它是带有负号的无穷大；`-Infinity`，例如：

```js
    > var i = -Infinity; 
    > i; 
    -Infinity 
    > typeof i; 
    "number" 

```

这是否意味着你可以有一个正好是无穷大两倍的东西，从 0 到无穷大，然后从 0 到负无穷大？嗯，并不是真的。当你把`Infinity`和`-Infinity`相加时，你得到的不是`0`，而是一个被称为**Not a Number**（**NaN**）的东西，例如：

```js
    > Infinity - Infinity; 
    NaN 
    > -Infinity + Infinity; 
    NaN 

```

任何其他算术运算中的`Infinity`作为操作数之一都会得到`Infinity`，例如：

```js
    > Infinity - 20; 
    Infinity 
    > -Infinity * 3; 
    -Infinity 
    > Infinity / 2; 
    Infinity 
    > Infinity - 99999999999999999; 
    Infinity 

```

有一个不太为人知的全局方法`isFinite()`，它告诉你值是否是无穷大。ES6 添加了一个`Number.isFinite()`方法来做到这一点。你可能会问为什么还需要另一个方法。全局的`isFinite()`方法试图通过 Number(value)来转换值，而`Number.isFinite()`不会，因此它更准确。

### NaN

在前面的例子中，这个`NaN`是什么？原来，尽管它的名字是 Not a Number，`NaN`是一个特殊的值，也是一个数字：

```js
    > typeof NaN; 
    "number" 
    > var a = NaN; 
    > a; 
    NaN 

```

当你尝试执行假定数字的操作，但操作失败时，你会得到`NaN`。例如，如果你尝试将`10`乘以字符`"f"`，结果是`NaN`，因为`"f"`显然不是乘法的有效操作数：

```js
    > var a = 10 * "f"; 
    > a;   
    NaN 

```

`NaN`是具有传染性的，所以如果你的算术运算中有一个`NaN`，整个结果都会泡汤，例如：

```js
    > 1 + 2 + NaN; 
    NaN 

```

#### Number.isNaN

ES5 有一个全局方法-`isNaN()`。它确定一个值是否是`NaN`。ES6 提供了一个非常相似的方法-`Number.isNaN()`（请注意，这个方法不是全局的）。

全局`isNaN()`和`Number.isNaN()`之间的区别在于，全局`isNaN()`在评估之前会转换非数字值为`NaN`。让我们看下面的例子。我们使用 ES6 的`Number.isNaN()`方法来测试某个值是否是`NaN`：

```js
    console.log(Number.isNaN('test')); //false : Strings are not NaN 
    console.log(Number.isNaN(123)); //false : integers are not NaN 
    console.log(Number.isNaN(NaN)); //true : NaNs are NaNs 
    console.log(Number.isNaN(123/'abc')); //true : 123/'abc' results in an NaN 

```

我们看到 ES5 的全局`isNaN()`方法首先转换非数字值，然后进行比较；其结果与 ES6 的对应方法不同：

```js
    console.log(isNaN('test')); //true 

```

总的来说，与其全局变量相比，`Number.isNaN()`更正确。然而，它们都不能用来判断某个值是否不是一个数字-它们只是回答这个值是否是`NaN`。实际上，你更感兴趣的是知道一个值是否被识别为一个数字。Mozilla 建议使用以下 polyfill 方法来做到这一点：

```js
    function isNumber(value) { 
      return typeof value==='number' && !Number.isNaN(value); 
    } 

```

#### Number.isInteger

这是 ES6 中的一个新方法。如果数字是有限的并且不包含任何小数点（是一个整数），它返回`true`：

```js
    console.log(Number.isInteger('test')); //false 
    console.log(Number.isInteger(Infinity)); //false 
    console.log(Number.isInteger(NaN)); //false 
    console.log(Number.isInteger(123)); //true 
    console.log(Number.isInteger(1.23)); //false 

```

## 字符串

字符串是用来表示文本的字符序列。在 JavaScript 中，放在单引号或双引号之间的任何值都被视为字符串。这意味着`1`是一个数字，但`"1"`是一个字符串。当与字符串一起使用时，`typeof`返回字符串`"string"`，例如：

```js
    > var s = "some characters"; 
    > typeof s; 
    "string" 
    > var s = 'some characters and numbers 123 5.87'; 
    > typeof s; 
    "string" 

```

这是一个在字符串上下文中使用的数字的例子：

```js
    > var s = '1'; 
    > typeof s; 
    "string" 

```

如果你在引号中什么都不放，它仍然是一个字符串（一个空字符串），例如：

```js
    > var s = ""; typeof s; 
    "string" 

```

正如你已经知道的，当你用加号和两个数字一起使用时，这是算术加法运算。然而，如果你用加号和字符串一起使用，这是一个字符串连接操作，并且返回两个字符串粘在一起：

```js
    > var s1 = "web";  
    > var s2 = "site";  
    > var s = s1 + s2;  
    > s; 
    "website" 
    > typeof s; 
    "string" 

```

`+`运算符的双重用途是错误的根源。因此，如果你打算连接字符串，最好确保所有的操作数都是字符串。加法也是一样；如果你打算加上数字，那么确保操作数是数字。你将在本章和本书的后面学到各种方法来做到这一点。

### 字符串转换

当你使用类似数字的字符串，例如，`"1"`，作为算术运算中的操作数时，字符串在幕后被转换为数字。这对所有算术运算都有效，除了加法，因为它存在歧义。考虑以下例子：

```js
    > var s = '1';  
    > s = 3 * s;  
    > typeof s; 
    "number" 
    > s; 
    3 
    > var s = '1'; 
    > s++; 
    > typeof s; 
    "number" 
    > s; 
    2 

```

将任何类似数字的字符串转换为数字的一种懒惰方法是将其乘以`1`（另一种方法是使用一个名为`parseInt()`的函数，您将在下一章中看到）：

```js
    > var s = "100"; typeof s; 
    "string" 
    > s = s * 1; 
    100 
    > typeof s; 
    "number" 

```

如果转换失败，您将得到`NaN`：

```js
    > var movie = '101 dalmatians'; 
    > movie * 1; 
    NaN 

```

您可以通过将其乘以`1`将字符串转换为数字。相反-将任何东西转换为字符串-可以通过与空字符串连接来完成，如下所示：

```js
    > var n = 1; 
    > typeof n; 
    "number" 
    > n = "" + n; 
    "1" 
    > typeof n; 
    "string" 

```

### 特殊字符串

还有一些具有特殊含义的字符串，如下表所示：

| **String** | **Meaning** | **Example** |
| --- | --- | --- |

| `\\``'``"` | `\`是转义字符。当您想在字符串中使用引号时，您可以转义它们，以便 JavaScript 不认为它们意味着字符串的结束。如果您想在字符串中有一个实际的反斜杠，请用另一个反斜杠转义它。| `> var s = 'I don't know';`: 这是一个错误，因为 JavaScript 认为字符串是`I don`，其余是无效的代码。以下代码是有效的：

```js
> var s = 'I don't know';   
> var s = "I don't know";   
> var s = "I don't know";   
> var s = '"Hello",   he said.';   
> var s = ""Hello",   he said.";   
Escaping the escape:   
> var s = "1\\2"; s;   
"1\2"   

```

|

| `\n` | 行尾。 |
| --- | --- |

```js
> var s = '\n1\n2\n3\n';   
> s;   
"   
1   
2   
3   
"   

```

|

| `\r` | 回车。|考虑以下陈述：

```js
> var s = '1\r2';   
> var s = '1\n\r2';   
> var s = '1\r\n2';   

```

所有这些的结果如下：

```js
> s;   
"1   
2"   

```

|

| `\t` | 制表符。 |
| --- | --- |

```js
> var s = "1\t2";   
> s;   
"1 2"   

```

|

| `\u` | `\u`后跟字符代码，允许您使用 Unicode。|以下是我的保加利亚名字，用西里尔字母写成：

```js
> "\u0421\u0442\u043E\u044F\u043D";   
"Стoян"   

```

|

还有一些很少使用的其他字符：`\b`（退格）、`\v`（垂直制表符）和`\f`（换页符）。

### 字符串模板文字

ES6 引入了模板文字。如果您熟悉其他编程语言，Perl 和 Python 现在已经支持模板文字一段时间了。模板文字允许在常规字符串中嵌入表达式。ES6 有两种文字：模板文字和标记文字。

模板文字是带有嵌入表达式的单行或多行字符串。例如，您一定做过类似的事情：

```js
    var log_level="debug"; 
    var log_message="meltdown"; 
    console.log("Log level: "+ log_level + 
      " - message : " + log_message); 
    //Log level: debug - message : meltdown 

```

您也可以使用模板文字来实现相同的效果，如下所示：

```js
    console.log(`Log level: ${log_level} - message: ${log_message}`) 

```

模板文字用反引号（`` ` ``）（重音符）字符，而不是通常的双引号或单引号。模板文字占位符由美元符号和花括号（`${expression}`）表示。默认情况下，它们被连接在一起形成一个字符串。以下示例显示了一个带有稍微复杂的表达式的模板文本:

```js
    var a = 10; 
    var b = 10; 
    console.log(`Sum is ${a + b} and Multiplication would be ${a * b}.`);   
    //Sum is 20 and Multiplication would be 100\. 

```

嵌入一个函数调用怎么样？

```js
    var a = 10; 
    var b = 10; 
    function sum(x,y){ 
      return x+y 
    } 
    function multi(x,y){ 
      return x*y 
    } 
    console.log(`Sum is ${sum(a,b)} and Multiplication 
      would be ${multi(a,b)}.`); 

```

模板文字也简化了多行字符串的语法。不需要写下面这行代码：

```js
    console.log("This is line one \n" + "and this is line two"); 

```

你可以使用模板文字得到更清晰的语法，如下所示：

```js
    console.log(`This is line one and this is line two`); 

```

ES6 还有另一种有趣的文字类型，叫做**标记模板文字**。标记模板允许你使用函数修改模板文字的输出。如果你在模板文字前面加上一个表达式，那么这个前缀被认为是一个要调用的函数。在使用标记模板文字之前，这个函数需要先定义好。例如，以下表达式：

```js
    transform`Name is ${lastname}, ${firstname} ${lastname}` 

```

前述表达式被转换为一个函数调用：

```js
    transform([["Name is ", ", ", " "],firstname, lastname) 

```

标记函数'transform'接收两个参数-类似`Name is`的模板字符串和`${}`定义的替换项。替换项只有在运行时才知道。让我们扩展`transform`函数：

```js
    function transform(strings, ...substitutes){ 
      console.log(strings[0]); //"Name is" 
      console.log(substitutes[0]); //Bond 
    }   
    var firstname = "James"; 
    var lastname = "Bond" 
    transform`Name is ${lastname}, ${firstname} ${lastname}` 

```

当模板字符串（`Name is`）传递给标记函数时，每个模板字符串有两种形式，如下所示：

+   反斜杠不被解释的原始形式

+   有特殊含义的反斜杠的转义形式

你可以通过使用原始属性来访问原始字符串形式，如下例所示：

```js
    function rawTag(strings,...substitutes){ 
      console.log(strings.raw[0]) 
    } 
    rawTag`This is a raw text and \n are not treated differently` 
    //This is a raw text and \n are not treated differently 

```

## 布尔值

只有两个值属于布尔数据类型-不带引号的`true`和`false`值：

```js
    > var b = true;  
    > typeof b; 
    "boolean" 
    > var b = false;  
    > typeof b; 
    "boolean" 

```

如果你引用`true`或`false`，它们会变成字符串，如下例所示：

```js
    > var b = "true";  
    > typeof b; 
    "string" 

```

### 逻辑运算符

有三个称为逻辑操作符的运算符，可以与布尔值一起使用。它们分别是：

```js
    ! - logical NOT (negation) 
    && - logical AND 
    || - logical OR 

```

你知道当某事不是真的时，它必须是假的。下面是用 JavaScript 和逻辑`!`运算符表达这一点的方式：

```js
    > var b = !true; 
    > b; 
    false 

```

如果你连续使用逻辑`NOT`两次，你会得到原始值，如下所示：

```js
    > var b = !!true; 
    > b; 
    true 

```

如果你在非布尔值上使用逻辑运算符，该值会在后台被转换为布尔值，如下所示：

```js
    > var b = "one"; 
    > !b; 
    false 

```

在前面的情况下，字符串值`"one"`被转换为布尔值`true`，然后取反。取反`true`的结果是`false`。在下面的示例中，有一个双重取反，所以结果是`true`：

```js
    > var b = "one"; 
    > !!b; 
    true 

```

你可以使用双重取反将任何值转换为它的布尔等价值。理解任何值如何转换为布尔值是很重要的。大多数值转换为`true`，除了以下这些，它们转换为`false`：

+   空字符串`""`

+   null

+   undefined

+   数字`0`

+   数字`NaN`

+   布尔`false`

这六个值被称为假值，而所有其他值都被称为真值（包括，例如，字符串`"0"`，`" "`和`"false"`）。

让我们看一些关于另外两个运算符-逻辑`AND`（`&&`）和逻辑`OR`（`||`）的例子。当你使用`&&`时，只有当所有操作数都为`true`时结果才为`true`。当你使用`||`时，只要至少有一个操作数为`true`结果就为`true`：

```js
    > var b1 = true, b2 = false; 
    > b1 || b2; 
    true 
    > b1 && b2; 
    false 

```

以下是可能的操作及其结果的列表：

| **操作** | **结果** |
| --- | --- |
| `true && true` | `true` |
| `true && false` | `false` |
| `false && true` | `false` |
| `false && false` | `false` |
| `true &#124;&#124; true` | `true` |
| `true &#124;&#124; false` | `true` |
| `false &#124;&#124; true` | `true` |
| `false &#124;&#124; false` | `false` |

你可以像下面一样连续使用几个逻辑操作：

```js
    > true && true && false && true; 
    false 
    > false || true || false; 
    true 

```

你还可以在同一表达式中混合使用 `&&` 和 `||`。在这种情况下，你应该使用括号来阐明操作的意图。考虑以下示例：

```js
    > false && false || true && true; 
    true 
    > false && (false || true) && true; 
    false 

```

### 运算符优先级

你可能会想知道为什么之前的表达式（`false && false || true && true`）返回了`true`。答案在于运算符的优先级，就像你从数学中知道的那样：

```js
    > 1 + 2 * 3; 
    7 

```

这是因为乘法具有比加法更高的优先级，所以 `2 * 3` 首先被计算，就好像你打了：

```js
    > 1 + (2 * 3); 
    7 

```

同样，在逻辑操作中，`!` 具有最高的优先级，并首先执行，假设没有需要其他操作的括号。然后，按照优先级的顺序，接下来是 `&&`，最后是 `||` 。换句话说，以下两段代码片段是相同的。第一个如下所示：

```js
    > false && false || true && true; 
    true 

```

第二个如下所示：

```js
    > (false && false) || (true && true); 
    true 

```

### 注意

**最佳实践**

使用括号而不依赖于运算符优先级。这样可以使你的代码更容易阅读和理解。

ECMAScript 标准定义了运算符的优先级。虽然这可能是一种很好的记忆练习，但本书并没有提供。首先，你会忘掉它，而且即使你设法记住了它也不应依赖于它。阅读和维护你的代码的人可能会感到困惑。

### 惰性评估

如果你连续进行几个逻辑操作，但在最后一刻结果已经很明显，那么最后的操作就不会被执行，因为它们不影响最终结果。考虑以下行代码作为例子：

```js
    > true || false || true || false || true; 
    true 

```

由于这些都是`OR`操作并且具有相同的优先级，如果至少有一个操作数为`true`，则结果将为`true`。在第一个操作数计算后，就很明显结果将为`true`，不管后面跟着什么值。因此，JavaScript 引擎决定偷懒（好吧，高效），并通过评估不影响最终结果的代码来避免不必要的工作。你可以通过在控制台中进行实验来验证这种短路行为，如下面的代码块所示：

```js
    > var b = 5; 
    > true || (b = 6); 
    true 
    > b; 
    5 
    > true && (b = 6); 
    6 
    > b; 
    6 

```

这个例子还展示了另一个有趣的行为-如果 JavaScript 在逻辑操作中遇到非布尔表达式作为操作数，那么将返回非布尔值作为结果：

```js
    > true || "something"; 
    true 
    > true && "something"; 
    "something" 
    > true && "something" && true; 
    true 

```

这种行为不是你应该依赖的，因为这会使代码更难理解。通常在不确定之前是否已定义变量时，会使用这种行为来定义变量。在下一个例子中，如果`mynumber`变量已被定义，则保留其值；否则，将其初始化为值`10`：

```js
    > var mynumber = mynumber || 10; 
    > mynumber; 
    10 

```

这看起来很简单并且优雅，但要注意它并不是完全可靠的。如果`mynumber`被定义并初始化为`0`，或者任何六个假值之一，这段代码可能会表现得与预期不同，如下面的代码示例所示：

```js
    > var mynumber = 0; 
    > var mynumber = mynumber || 10; 
    > mynumber; 
    10 

```

### 比较

另一组运算符也都会返回布尔值作为操作的结果。这些是比较运算符。以下表格列出了它们以及示例用法：

| **运算符符号** | **描述** | **示例** |
| --- | --- | --- |
| `==` | **相等比较**：当两个操作数相等时返回`true`。在比较之前，操作数将被转换为相同的类型。它们也被称为宽松比较。 |

```js
> 1 == 1;   
true   
> 1 == 2;   
false   
> 1 =='1';   
true   

```

|

| `===` | **相等和类型比较**：如果两个操作数相等并且类型相同，则返回`true`。这种比较方式更好、更安全，因为不会进行后台类型转换。它也被称为严格比较。 |
| --- | --- |

```js
> 1 === '1';   
false   
> 1 === 1;   
true   

```

|

| `!=` | **不相等比较**：如果进行类型转换后，操作数不相等，则返回`true`。 |
| --- | --- |

```js
> 1 != 1;   
false   
> 1 != '1';   
false   
> 1 != '2';   
true   

```

|

| `!==` | **非相等比较，不进行类型转换**：如果操作数不相等或者它们的类型不同，则返回`true`。 |
| --- | --- |

```js
> 1 !== 1;   
false   
> 1 !== '1';   
true   

```

|

| `>` | 如果左操作数大于右操作数，则返回`true`。 |
| --- | --- |

```js
> 1 > 1;   
false   
> 33 > 22;   
true   

```

|

| `>=` | 如果左操作数大于或等于右操作数，则返回`true`。 |
| --- | --- |

```js
> 1 >= 1;   
true   

```

|

| `<` | 如果左操作数小于右操作数，则返回`true`。 |
| --- | --- |

```js
> 1 < 1;   
false   
> 1 < 2;   
true   

```

|

| `<=` | 如果左操作数小于或等于右操作数，则返回`true`。 |
| --- | --- |

```js
> 1 <= 1;   
true   
> 1 <= 2;   
true   

```

|

注意，`NaN`不等于任何东西，甚至不等于它自己。看一下下面这行代码：

```js
    > NaN == NaN; 
    false 

```

## 未定义和 null

如果你试图使用一个不存在的变量，你会得到以下错误：

```js
    > foo; 
    ReferenceError: foo is not defined 

```

对于不存在的变量使用`typeof`运算符不会报错。你将得到`"undefined"`字符串作为返回，如下所示：

```js
    > typeof foo; 
    "undefined" 

```

如果声明一个不给出值的变量，当然不会报错。但是，`typeof`依然返回`"undefined"`：

```js
    > var somevar; 
    > somevar; 
    > typeof somevar; 
    "undefined" 

```

这是因为，当你声明一个变量但不初始化它时，JavaScript 会自动将其初始化为`undefined`值，如下面的代码所示：

```js
    > var somevar; 
    > somevar === undefined; 
    true 

```

另一方面，`null`值并不是由 JavaScript 在后台分配的；它是由你的代码分配的，如下所示：

```js
    > var somevar = null; 
    null 
    > somevar; 
    null 
    > typeof somevar; 
    "object" 

```

尽管`null`和`undefined`之间的差异很小，但有时也可能非常关键。例如，如果尝试进行算术运算，将会得到不同的结果：

```js
    > var i = 1 + undefined; 
    > i; 
    NaN 
    > var i = 1 + null; 
    > i; 
    1 

```

这是因为`null`和`undefined`转换为其他原始类型的方式不同。以下示例显示了可能的转换：

+   转换为数字：

```js
            > 1 * undefined; 

    ```

+   转换为 NaN：

```js
            > 1 * null; 
            0 

    ```

+   转换为布尔值：

```js
            > !!undefined; 
            false 
            > !!null; 
            false 

    ```

+   转换为字符串：

```js
            > "value: " + null; 
            "value: null" 
            > "value: " + undefined; 
            "value: undefined" 

    ```

## 符号

ES6 引入了一个新的原始类型-符号。几种语言都有类似的概念。符号看起来非常类似于普通字符串，但它们非常不同。让我们看看如何创建这些符号：

```js
    var atom = Symbol() 

```

注意，在创建符号时，我们不使用`new`运算符。当你这样做时会出错：

```js
    var atom = new Symbol() //Symbol is not a constructor 

```

你也可以描述`Symbol`：

```js
    var atom = Symbol('atomic symbol') 

```

描述符号在调试大型程序时非常方便，因为其中有许多散布的符号。

`Symbol`的最重要特性（也即其存在的原因）是它们是唯一的和不可变的：

```js
    console.log(Symbol() === Symbol()) //false 
    console.log(Symbol('atom') === Symbol('atom')) // false 

```

目前，我们不得不暂停探讨关于符号的讨论。符号用作属性键和需要唯一标识符的地方。我们将在本书的后面讨论符号。

# 原始数据类型回顾

让我们快速总结一下到目前为止讨论的一些主要要点：

+   JavaScript 中有五种原始数据类型：

    +   数字

    +   字符串

    +   布尔

    +   未定义

    +   空

+   不是原始数据类型的所有东西都是对象。

    原始数字数据类型可以存储正整数和负整数或浮点数、十六进制数、八进制数、指数以及特殊的数-`NaN`、`Infinity`和`-Infinity`。

+   字符串数据类型包含带引号的字符。模板文字允许在字符串中嵌入表达式。

+   布尔数据类型的唯一值是`true`和`false`。

+   null 数据类型的唯一值是`null`值。

+   未定义数据类型的唯一值是`undefined`值。

+   当转换为布尔值时，所有的值都变为`true`，除了以下六个虚假值：

    +   `""`

    +   `null`

    +   `undefined`

    +   `0`

    +   `NaN`

    +   `false`

# 数组

现在你已经了解了 JavaScript 中的基本原始数据类型，是时候转向更强大的数据结构-数组了。

那么，什么是数组？它只是一个值的列表（一个序列）。你可以用一个数组变量而不是一个变量来存储任意数量的值作为数组的元素。

要声明一个包含空数组的变量，你可以使用两个方括号之间没有任何内容的方式，就像下面的代码行所示：

```js
    > var a = []; 

```

要定义一个有三个元素的数组，你可以写下面的代码行：

```js
    > var a = [1, 2, 3]; 

```

当你简单地在控制台中键入数组的名称时，你可以得到数组的内容：

```js
    > a; 
    [1, 2, 3] 

```

现在的问题是如何访问这些数组元素中存储的值。数组中包含的元素是用连续的数字进行索引的，从零开始。第一个元素的索引（或位置）为 0，第二个元素的索引为 1，依此类推。以下是上一个示例中的三个元素数组：

| **索引** | **值** |
| --- | --- |
| 0 | 1 |
| 1 | 2 |
| 2 | 3 |

要访问数组元素，你可以在方括号内指定该元素的索引。所以，`a[0]`给出了数组`a`的第一个元素，`a[1]`给出了第二个元素，如下面的例子所示：

```js
    > a[0]; 
    1 
    > a[1]; 
    2 

```

## 添加/更新数组元素

使用索引，你也可以更新数组元素的值。下面的示例更新了第三个元素（索引为 2），并打印了新数组的内容，如下所示：

```js
    > a[2] = 'three'; 
    "three" 
    > a; 
    [1, 2, "three"] 

```

你可以通过访问之前不存在的索引来添加更多的元素，就像下面的代码行中所示：

```js
    > a[3] = 'four'; 
    "four" 
    > a; 
    [1, 2, "three", "four"] 

```

如果你添加新元素但在数组中留下一个空隙，那么这些之间的元素就不存在，并且在访问时返回`undefined`值。查看以下示例：

```js
    > var a = [1, 2, 3]; 
    > a[6] = 'n`xew'; 
    "new" 
    > a; 
    [1, 2, 3, undefined x 3, "new"] 

```

## 删除元素

要删除一个元素，你可以使用`delete`运算符。但是，在删除后，数组的长度不会改变。在某种意义上，你可能会在数组中得到一个空缺：

```js
    > var a = [1, 2, 3]; 
    > delete a[1]; 
    true 
    > a; 
    [1, undefined, 3] 
    > typeof a[1]; 
    "undefined" 

```

## 数组的数组

数组可以包含各种类型的值，包括其他数组：

```js
    > var a = [1, "two", false, null, undefined]; 
    > a; 
    [1, "two", false, null, undefined] 
    > a[5] = [1, 2, 3]; 
    [1, 2, 3] 
    > a; 
    [1, "two", false, null, undefined, Array[3]] 

```

控制台中的结果中的`Array[3]`是可点击的，它会展开数组值。让我们看一个例子，你有一个包含两个元素的数组，它们都是其他数组：

```js
    > var a = [[1, 2, 3], [4, 5, 6]]; 
    > a; 
    [Array[3], Array[3]] 

```

数组的第一个元素是`[0]`，也是一个数组：

```js
    > a[0]; 
    [1, 2, 3] 

```

要访问嵌套数组中的元素，你可以参考另一组方括号中的元素索引，如下所示：

```js
    > a[0][0]; 
    1 
    > a[1][2]; 
    6 

```

请注意，你可以使用数组表示法来访问字符串内的单个字符，就像下面的代码块中所示：

```js
    > var s = 'one'; 
    > s[0]; 
    "o" 
    > s[1]; 
    "n" 
    > s[2]; 
    "e" 

```

### 注意

许多浏览器已经支持对字符串的数组访问（不包括较旧的 IE），但它直到 ECMAScript 5 才被官方承认。

有更多与数组有趣的玩法（我们将在第四章*对象*中介绍），但现在让我们先停在这里，记住以下几点：

+   数组是一个数据存储

+   一个数组包含索引元素

+   索引从零开始，并且对于数组中的每个元素递增一次

+   要访问数组的一个元素，你可以使用它在方括号中的索引

+   一个数组可以包含任何类型的数据，包括其他数组

# 条件和循环

条件提供了一个简单但强大的方式来控制代码执行流程。循环允许你以较少的代码执行重复操作。让我们来看一下：

+   `if`条件

+   `switch`语句

+   `while`，`do...while`，`for`，和`for...in`循环

### 注意

以下各节中的示例需要你切换到多行的 Firebug 控制台。或者，如果你使用 WebKit 控制台，按下*Shift* + *Enter*而不是*Enter*来添加新行。

## 代码块

在前面的示例中，你看到了代码块的使用。让我们花一点时间澄清什么是代码块，因为在构建条件和循环时，你会广泛使用代码块。

一块代码由花括号括起来的零个或多个表达式组成，就像下面的代码行所示：

```js
    { 
      var a = 1; 
      var b = 3; 
    } 

```

你可以无限嵌套块，就像下面的例子：

```js
    { 
      var a = 1; 
      var b = 3; 
      var c, d; 
      { 
        c = a + b; 
        { 
          d = a - b; 
        } 
      } 
    } 

```

### 注意

**最佳实践提示**

使用一行结束的分号，正如前面章节中讨论的那样。虽然当每行只有一个表达式时分号是可选的，但最好养成使用它们的习惯。为了最佳可读性，块中的单个表达式应该每行放置一个，并用分号分隔。

缩进任何放置在花括号内的代码。一些程序员喜欢一个制表符缩进，一些使用四个空格，一些使用两个空格。实际上这并不重要，只要你保持一致就行。在前面的示例中，外部块缩进两个空格，第一个嵌套块中的代码缩进四个空格，最里面的块缩进六个空格。

使用花括号。当一个块只由一个表达式组成时，花括号是可选的，但出于可读性和可维护性的考虑，你应该养成始终使用它们的习惯，即使它们是可选的。

### if 条件

下面是一个`if`条件的简单示例：

```js
    var result = '', a = 3; 
    if (a > 2) { 
      result = 'a is greater than 2'; 
    } 

```

`if`条件的部分如下：

+   `if`语句

+   括号中的条件-`is a greater than 2`？

+   一个被`{}`包裹的一段代码，如果条件满足则执行

条件（括号中的部分）始终返回一个布尔值，并且还可能包含以下内容：

+   逻辑操作-`!`，`&&`或`||`

+   比较，如`===`，`!=`，`>`等

+   任何可以转换为布尔值的值或变量

+   上述的组合

### else 子句

if 条件还可以有一个可选的 else 部分。`else`语句后面跟着一段代码，该代码在条件评估为`false`时运行：

```js
    if (a > 2) { 
      result = 'a is greater than 2'; 
    } else { 
      result = 'a is NOT greater than 2'; 
    } 

```

在`if`和`else`语句之间，还可以有无限数量的`else...if`条件。下面是一个例子：

```js
    if (a > 2 || a < -2) { 
      result = 'a is not between -2 and 2'; 
    } else if (a === 0 && b === 0) { 
      result = 'both a and b are zeros'; 
    } else if (a === b) { 
      result = 'a and b are equal'; 
    } else { 
      result = 'I give up'; 
    } 

```

你还可以通过在任何块中嵌套条件来嵌套条件，如下面的代码片段所示：

```js
    if (a === 1) { 
      if (b === 2) { 
        result = 'a is 1 and b is 2'; 
      } else { 
        result = 'a is 1 but b is definitely not 2'; 
     } 
    } else { 
      result = 'a is not 1, no idea about b'; 
    } 

```

### 检查变量是否存在

让我们将新的有关条件的知识应用到一些实际问题上。通常需要检查变量是否存在。这样做的最懒的方法是简单地将变量放在`if`语句的条件部分中，例如`if (somevar) {...}`。但是，这未必是最好的方法。让我们看一个测试变量`somevar`是否存在的例子，如果存在，则将`result`变量设置为`yes`：

```js
    > var result = ''; 
    > if (somevar) {  
        result = 'yes';  
      } 
    ReferenceError: somevar is not defined 
    > result;   
    "" 

```

这段代码显然有效，因为最终结果不是`yes`。但首先，代码生成了一个错误-`somevar`未定义，你不希望你的代码表现出这样的行为。其次，仅仅因为`if (somevar)`返回`false`，并不意味着`somevar`未定义。可能是`somevar`已经定义和初始化，但包含一个类似`false`或`0`的假值。

检查变量是否定义的更好方法是使用`typeof`：

```js
    > var result = ""; 
    > if (typeof somevar !== "undefined") {  
        result = "yes";  
      } 
    > result; 
    "" 

```

`typeof`运算符始终返回一个字符串，可以将该字符串与字符串`"undefined"`进行比较。注意，`somevar`变量可能已经声明但尚未赋值，你仍然会得到相同的结果。因此，通过像这样使用`typeof`进行测试时，你实际上在测试变量是否具有除`undefined`值以外的任何值：

```js
    > var somevar; 
    > if (typeof somevar !== "undefined") {  
        result = "yes";  
      } 
    > result; 
    "" 
    > somevar = undefined; 
    > if (typeof somevar !== "undefined") {  
        result = "yes";  
      } 
    > result; 
    "" 

```

如果一个变量被定义并初始化为除了`undefined`之外的任何值，那么通过`typeof`返回的类型就不再是`"undefined"`，如下面的代码片段所示：

```js
    > somevar = 123; 
    > if (typeof somevar !== "undefined") {  
        result = 'yes';  
      } 
    > result; 
    "yes" 

```

### 备用的 if 语法

当你有一个简单条件时，可以考虑使用另一种`if`语法。看看这个：

```js
    var a = 1; 
    var result = ''; 
    if (a === 1) { 
      result = "a is one"; 
    } else { 
      result = "a is not one"; 
    } 

```

你也可以这样写：

```js
    > var a = 1; 
    > var result = (a === 1) ? "a is one" : "a is not one"; 

```

你应该只在简单条件下使用这种语法。要小心不要滥用它，因为它很容易使你的代码难以阅读。以下是一个示例。

假设你想确保一个数字在一个特定范围内，比如在`50`和`100`之间：

```js
    > var a = 123; 
    > a = a > 100 ? 100 : a < 50 ? 50: a; 
    > a; 
    100 

```

可能不太清楚这个代码是如何工作的，因为有多个?。添加括号可以让它稍微清晰一些，如下面的代码块所示：

```js
    > var a = 123; 
    > a = (a > 100 ? 100 : a < 50) ? 50 : a; 
    > a; 
    50 
    > var a = 123; 
    > a = a > 100 ? 100 : (a < 50 ? 50 : a); 
    > a; 
    100 

```

`?:`被称为三元运算符，因为它需要三个操作数。

### Switch

如果你发现自己在使用`if`条件并且有太多`else...if`部分，可以考虑将`if`改为`switch`，如下所示：

```js
    var a = '1', 
        result = ''; 
    switch (a) { 
    case 1: 
      result = 'Number 1'; 
      break; 
    case '1': 
      result = 'String 1'; 
      break; 
    default: 
      result = 'I don't know'; 
      break; 
    } 

```

执行完之后的结果是`"String 1"`。让我们来看看`switch`的各部分是什么：

+   `switch`语句。

+   括号中的表达式。最常见的表达式包含一个变量，但可以是任何返回值的东西。

+   一系列用花括号括起来的`case`块。

+   每个`case`语句后面跟着一个表达式。这个表达式的结果会与`switch`语句后面的表达式进行比较。如果比较的结果为`true`，则执行`case`后面冒号之后的代码。

+   存在一个可选的`break`语句，用于表示`case`块的结束。如果到达这个`break`语句，`switch`语句就执行完成了。否则，如果缺少`break`，程序执行就进入下一个`case`块。

+   有一个可选的默认情况，用`default`语句标记，并跟着一块代码。如果之前的任何情况都没被评估为`true`，则执行`default`情况。

换句话说，执行`switch`语句的逐步过程如下：

1.  评估括号中的`switch`表达式；记住它。

1.  移动到第一个`case`并将其值与步骤 1 中的值进行比较。

1.  如果步骤 2 中的比较返回`true`，则执行`case`块中的代码。

1.  在执行`case`块之后，如果在其末尾有一个`break`语句，则退出`switch`。

1.  如果没有`break`或者步骤 2 返回`false`，则继续下一个`case`块。

1.  重复步骤 2 到 5。

1.  如果你还在这里（第 4 步没有退出），执行`default`语句后面的代码。

### 小贴士

缩进跟在`case`行之后的代码。你也可以缩进`switch`的`case`，但这对可读性没有太大帮助。

#### 别忘了加上`break`

有时，你可能有意地省略 `break`，但这很少见。这被称为穿透，一定要记录下来，因为它可能看起来像是一个意外的遗漏。另一方面，有时你可能希望省略跟在一个 `case` 后面的整个代码块，并且让两个 `case` 共享相同的代码。这是可以的，但这并不改变以下规则：如果有跟在一个 `case` 语句后面的代码，这段代码应该以 `break` 结尾。至于缩进，将 `break` 与 `case` 或 `case` 内部的代码对齐是个人偏好；再次强调，保持一致才是最重要的。

使用默认情况。这可以确保在 `switch` 语句之后始终有一个有意义的结果，即使没有任何一个 `case` 与被切换的值匹配。

## 循环

`if...else` 和 `switch` 语句允许你的代码走不同的路径，就好像你站在十字路口一样，在依据条件决定往哪个方向走。另一方面，循环允许你的代码在回到主干路之前绕几个圈。重复多少次？这取决于在每次迭代之前（或之后）评估条件的结果。

假设你（你的程序执行）从 **A** 到 **B**。在某一时刻，你将到达一个需要评估条件 **C** 的地方。评估 **C** 的结果告诉你是否应该进入一个循环 **L**。你进行一次迭代，再次到达 **C**。然后，再次评估条件，看是否需要另一个迭代。最终，你继续前往 **B**：

![循环](img/image_02_003.jpg)

无限循环是当条件总是 `true` 时发生的，你的代码会永远停留在循环中。这显然是一个逻辑错误，你应该注意这种情况。

在 JavaScript 中，循环有以下四种类型：

+   `while` 循环

+   `do-while` 循环

+   `for` 循环

+   `for-in` 循环

### while 循环

`while` 循环是最简单的迭代类型，它看起来像下面这样：

```js
    var i = 0; 
    while (i < 10) { 
      i++; 
    } 

```

`while` 语句后面跟着一个括号中的条件，然后是一个花括号中的代码块。只要条件评估为 `true`，代码块就会一遍又一遍地执行。

### `do-while` 循环

`do...while` 循环是 `while` 循环的轻微变种，示例如下所示：

```js
    var i = 0; 
    do { 
      i++; 
    } while (i < 10); 

```

在这里，`do` 语句后面是一个代码块，在代码块后面是一个条件。这意味着在评估条件之前，代码块总是被执行至少一次。

如果在最后两个示例中将 `i` 初始化为 `11` 而不是 `0`，则第一个示例中的代码块（`while` 循环）将不会被执行，最后 `i` 仍然是 `11`，而在第二个示例中（`do...while` 循环），代码块将被执行一次，`i` 将变为 `12`。

### For 循环

`for` 循环是最常用的循环类型，你应该确保自己熟悉这一点。它在语法方面需要稍微多一点：

![For 循环](img/image_02_004.jpg)

除了**C**条件和**L**代码块，你还有以下内容：

+   **初始化**：这是在进入循环之前执行的代码（在图表中标为**0**）

+   **增量**：这是在每次迭代后执行的代码（在图表中标为**++**）

以下是最广泛使用的`for`循环模式：

+   在初始化部分，你可以定义一个变量（或设置现有变量的初始值），通常称为`i`

+   在条件部分，你可以比较`i`和边界值，比如`i < 100`

+   在增量部分，你可以增加`i`，比如`i++`

例子如下：

```js
    var punishment = ''; 
    for (var i = 0; i < 100; i++) { 
      punishment += 'I will never do this again, '; 
    } 

```

所有三个部分（初始化、条件和增量）都可以包含多个用逗号分隔的表达式。假设你想重写示例并在循环的初始化部分定义变量`punishment`：

```js
    for (var i = 0, punishment = ''; i < 100; i++) { 
      punishment += 'I will never do this again, '; 
    } 

```

你能把循环体移到增量部分吗？可以，特别是当它是一行代码的时候。这会给你一个看起来有点奇怪的循环，因为它没有循环体。请注意，这只是一种智力练习；不建议你写出看起来奇怪的代码：

```js
    for ( 
      var i = 0, punishment = ''; 
      i < 100; 
      i++, punishment += 'I will never do this again, ') { 

      // nothing here 

    } 

```

这三个部分都是可选的。以下是重写相同示例的另一种方式：

```js
    var i = 0, punishment = ''; 
    for (;;) { 
      punishment += 'I will never do this again, '; 
      if (++i == 100) { 
        break; 
      } 
    } 

```

尽管最后的重写与原始代码的作用方式完全相同，但它更长，更难阅读。也有可能使用`while`循环来实现相同的结果。但是，`for`循环使得代码更加紧凑和稳健，因为`for`循环的语法本身让你思考三个部分（初始化、条件和增量），从而帮助你重新确认逻辑，避免陷入无限循环的情况。

`for`循环可以嵌套在彼此之中。以下是一个循环嵌套在另一个循环中，并组装一个包含十行十列星号的字符串的示例。把`i`想象为一幅图像的行，`j`想象为列：

```js
    var res = '\n'; 
    for (var i = 0; i < 10; i++) { 
      for (var j = 0; j < 10; j++) { 
        res += '* '; 
      } 
      res += '\n'; 
    } 

```

结果是一个字符串，如下所示：

```js
    " 
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    * * * * * * * * * *  
    " 

```

这是另一个例子，它使用嵌套循环和取模操作来绘制类似雪花的结果：

```js
    var res = '\n', i, j; 
    for (i = 1; i <= 7; i++) { 
      for (j = 1; j <= 15; j++) { 
        res += (i * j) % 8 ? ' ' : '*'; 
      } 
      res += '\n'; 
    } 

```

结果如下：

```js
    " 
           *        
       *   *   *    
           *        
     * * * * * * *  
           *        
       *   *   *    
           *        
    " 

```

### 对于...在循环中

`for...in`循环用于遍历数组或对象的元素，稍后你会看到。这是它的唯一用途；它不能用作替换`for`或`while`的通用重复机制。让我们看一个使用`for-in`循环来遍历数组元素的例子。但是请记住，这仅用于信息目的，因为`for...in`主要适用于对象，而常规的`for`循环应该用于数组。

在这个例子中，你可以遍历数组的所有元素，并打印出每个元素的索引（键）和值，例如：

```js
    // example for information only 
    // for-in loops are used for objects 
    // regular for is better suited for arrays 

    var a = ['a', 'b', 'c', 'x', 'y', 'z']; 

    var result = '\n'; 

    for (var i in a) { 
      result += 'index: ' + i + ', value: ' + a[i] + '\n'; 
    } 
    The result is: 
    " 
    index: 0, value: a 
    index: 1, value: b  
    index: 2, value: c  
    index: 3, value: x 
    index: 4, value: y  
    index: 5, value: z 
    " 

```

# 注释

这一章的最后一件事-注释。在您的 JavaScript 程序中，您可以放置注释。这些被 JavaScript 引擎忽略，并不会对程序的运行方式产生任何影响。但是，当您在几个月后重新访问代码，或将代码转交给其他人进行维护时，它们可能会非常宝贵。

允许以下两种类型的注释：

+   单行注释以 `//` 开头，并在行尾结束。

+   多行注释以 `/*` 开头，并以同一行或任何后续行的 `*/` 结束。请注意，注释开始和注释结束之间的任何代码都将被忽略。

一些示例如下：

```js
    // beginning of line 

    var a = 1; // anywhere on the line 

    /* multi-line comment on a single line */ 

    /* 
      comment that spans several lines 
    */ 

```

甚至有一些工具，比如 JSDoc 和 YUIDoc，可以解析你的代码，并根据你的注释提取有意义的文档。

# 练习

1.  在控制台执行这些行的结果是什么？为什么？

```js
            > var a; typeof a; 
            > var s = '1s'; s++; 
            > !!"false"; 
            > !!undefined; 
            > typeof -Infinity; 
            > 10 % "0"; 
            > undefined == null; 
            > false === ""; 
            > typeof "2E+2"; 
            > a = 3e+3; a++; 

    ```

1.  在以下操作后的 v 的值是多少？

```js
            > var v = v || 10; 

    ```

首先尝试将`v`设置为`100`，`0`或`null`进行实验。

1.  编写一个打印乘法表的小程序。提示：在另一个循环内嵌套使用循环。

# 总结

在本章中，你学到了关于 JavaScript 程序的基本构建块。现在你知道以下原始数据类型：

+   数字

+   字符串

+   布尔值

+   未定义

+   空

你也知道了相当多的运算符，它们如下：

+   **算术运算符**：`+`，`-`，`*`，`/`和`%`

+   **递增运算符**：`++`和`-`

+   **赋值运算符**：`=`，`+=`，`-=`，`*=`，`/=`和`%=` 

+   **特殊运算符**：`typeof`和`delete`

+   **逻辑运算符**：`&&`，`||`和`!`

+   **比较运算符**：`==`，`===`，`!=`，`!==`，`<`，`>`，`>=`和`<=`

+   **三元运算符**：`?`

然后你学会了如何使用数组来存储和访问数据，最后你看到了使用条件（`if...else`或`switch`）和循环（`while`，`do...while`，`for`和`for...in`）来控制程序流程的不同方法。

这是相当多的信息；在深入下一章之前，给自己一个当之无愧的鼓励。更有趣的内容即将到来！
