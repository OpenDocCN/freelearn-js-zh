# 第三章：特殊字符

在本章中，我们将看一些特殊字符和一些更高级的技术，这些将帮助我们创建更详细的**正则表达式**模式。我们还将慢慢过渡到使用标准 JavaScript 来构建更*完整*的真实世界示例，而不是使用我们的正则表达式测试环境。

在我们超前之前，我们还有一些事情可以使用我们当前的设置来学习，首先是一些约束。

在本章中，我们将涵盖以下主题：

+   为正则表达式定义边界

+   定义非贪婪量词

+   使用分组定义正则表达式

# 非可视约束

到目前为止，我们对模式施加的所有约束都与可以显示或不显示的字符有关，但是正则表达式提供了许多位置约束，允许您过滤掉一些误报。

## 匹配输入的开头和结尾

第一个这样的集合是*开始*和*结束*的字符串匹配器。使用(`^`) *插入符号*来匹配字符串的开头和(`$`)美元符号来匹配结尾，我们可以强制模式定位在这些位置，例如，您可以在单词的末尾添加美元符号，以确保它是提供的字符串中的最后一件事。在下一个例子中，我使用了`/^word|word$/g`模式来匹配`word`的出现，它可以是字符串的开头或结尾。下面的图片展示了给定**文本**输入时正则表达式的匹配：

![匹配输入的开头和结尾](img/2258OS_03_01.jpg)

同时使用开始和结束字符可以确保您的模式是字符串中唯一的内容。例如，如果您有一个`/world/`模式，它将匹配`world`字符串以及任何其他仅包含`world`的字符串，例如`hello world`。但是，如果您想确保字符串只包含`world`，您可以修改模式为`/^world$/`。这意味着正则表达式将尝试找到既开始字符串又结束字符串的模式。当然，这只会发生在它是字符串中的唯一内容时。

这是默认行为，但值得一提的是，情况并非总是如此。在前一章中，我们看到了`m`或多行标志，这个标志的作用是使插入符号不仅匹配字符串的开头，还匹配任何行的开头。美元符号也是如此：它将匹配每行的结尾，而不是整个字符串的结尾。因此，这实际上取决于您在特定情况下的需求。

## 匹配单词边界

**单词边界**与我们刚刚看到的**字符串边界**非常相似，只是它们在单词的上下文中起作用。例如，我们想匹配`can`，但这指的是单独的`can`，而不是`candy`中的`can`。我们在前面的例子中看到，如果您只输入一个模式，比如`/can/g`，即使它是另一个单词的一部分，也会匹配`can`，例如，在用户输入`candy`的情况下。使用反斜杠(`\b`)字符，我们可以表示一个单词边界（在开头或结尾），这样我们就可以使用类似`/\bcan\b/g`的模式来解决这个问题，如下所示：

![匹配单词边界](img/2258OS_03_02.jpg)

## 匹配非单词边界

与`\b`字符配对的是`\B`符号，它是其相反的。与我们在多个场合看到的类似，大写符号通常指相反的功能，并且也不例外。大写版本将对限制模式的约束放在单词边缘。现在，我们将运行相同的示例文本，只是用`/can\B/g`，这将交换匹配；这是因为`can`中的`n`处于其边界：

![匹配非单词边界](img/2258OS_03_03.jpg)

## 匹配空白字符

您可以使用反斜杠`s`字符匹配空白字符，并且它匹配诸如空格和制表符之类的内容。它类似于单词边界，但有一些区别。首先，单词边界匹配单词的结尾，即使它是模式中的最后一个单词，而空白字符则需要额外的空格。因此，`/foo\b/`将匹配`foo`。但是，`/foo\s/`不会，因为字符串末尾没有后续空格字符。另一个区别是边界匹配器将计算类似句号或破折号之类的内容作为实际边界，而空白字符只有在有空格时才匹配字符串： 

![匹配空白字符](img/2258OS_03_04.jpg)

### 注

值得一提的是，空白字符具有一个`\S`反向匹配器，它将匹配除空白字符之外的任何内容。

# 定义非贪婪量词

在上一节中，我们看了看乘法器，您可以指定一个模式应该重复一定次数。默认情况下，JavaScript 会尝试匹配尽可能多的字符，这意味着它将是一个贪婪匹配。假设我们有一个类似`/\d{1,4}/`的模式，它将匹配任何文本，并且有 1 到 4 个数字。默认情况下，如果我们使用`124582948`，它将返回`1245`，因为它将采用最大数量的选项（贪婪方法）。但是，如果我们想要，我们可以添加（`?`）问号运算符，告诉 JavaScript 不要使用贪婪匹配，而是尽可能返回最少数量的字符：

![定义非贪婪量词](img/2258OS_03_05.jpg)

贪婪匹配是使在代码中查找错误变得困难的东西。考虑以下示例文本：

```js
<div class="container" id="main">
   Site content  
<div>
```

如果我们想要提取类，您可能会考虑以这种方式编写模式：

```js
/class=".*"/
```

这里的问题是`*`字符将尝试匹配尽可能多的字符，所以我们不会得到像我们想要的`container`，而是会得到`"container" id="main"`。由于点字符将匹配任何内容，正则表达式将从`class`单词之前的第一个引号匹配到`id`单词之前的右引号。为了解决这个问题，我们可以使用非贪婪问号并将模式更改为`/class=".*?"/`。这将导致它在达到第一个引号时停止，这是最小要求的匹配：

![定义非贪婪量词](img/2258OS_03_06.jpg)

# 在正则表达式中匹配组

我到目前为止留下的最后一个主题是**组**。但是，为了使用组，我们必须回到 JavaScript 控制台，因为这将提供我们需要查看的实际结果对象。

组显示了我们如何从提供的输入中提取数据。没有组，您可以检查是否有匹配，或者给定的输入文本是否遵循特定模式。但是，您无法利用模糊的定义来提取相关内容。语法非常简单：您将要提取的模式包装在括号内，然后表达式的这部分将被提取到自己的属性中。

## 将字符分组以创建从句

让我们从一些基本的东西开始——标准 JavaScript 中的人名。如果您有一个包含某人姓名的字符串，您可能会按空格字符拆分它，并检查其中是否有两个或三个组件。如果有两个，第一个将包括名字，第二个将包括姓氏；但是，如果有三个组件，那么第二个组件将包括中间名，第三个将包括姓氏。

与强加条件不同，我们可以创建一个简单的模式，如下所示：

```js
/(\S+) (\S*) ?\b(\S+)/
```

第一组包含一个必需的非空单词。加号将再次无限制地增加模式。接下来，我们想要一个带有第二个单词的空格；这次，我使用了星号来表示它的长度可以为零，并且在此之后，我们有另一个空格，尽管这次是可选的。

### 注意

如果没有中间名，就不会有第二个空格，后面跟着一个单词边界。这是因为空格是可选的，但我们仍然希望确保存在一个新单词，然后是最后一个单词。

现在，打开 JavaScript 控制台（在 Chrome 中）并为此模式创建一个变量：

```js
var pattern = /(\S+) (\S*) ?\b(\S+)/
```

然后，尝试对此模式使用不同的名称运行`exec`命令，有中间名和没有中间名，并查看结果输出：

![将字符分组在一起以创建从句](img/2258OS_03_07.jpg)

无论字符串是否有中间名，它都将具有我们可以分配给变量的三个模式，因此，我们可以使用其他东西来代替这个：

```js
var res = name.split(" ");
first_name = res[0];

if (res.length == 2) {
   middle_name = "";
   last_name = res[1];
} else {
   middle_name = res[1];
   last_name = res[2];
}
```

我们可以从前面的代码中删除条件语句（`if`-`else`），并编写类似于此的代码：

```js
var res = /(\S+) (\S*) ?\b(\S+)/.exec(name);

first_name = res[1];
middle_name = res[2];
last_name = res[3];
```

如果省略中间名，我们的表达式仍将具有该组，只是一个空字符串。

另一个值得一提的事情是，组的索引从`1`开始，因此第一组在结果`1`索引中，结果`0`索引保存整个匹配。

### 捕获和非捕获组

在第一章中，我们看到了一个示例，我们想要解析某种**XML**标记，并且我们说我们需要一个额外的约束条件，即关闭标记必须与开放标记匹配才能有效。因此，例如，这应该被解析：

```js
<duration>5 Minutes</duration>
```

在这里，这不应该被解析：

```js
<duration>5 Minutes</title>
```

由于闭合标签与开放标签不匹配，引用模式中先前组的方法是使用反斜杠字符，后跟组的索引号。例如，让我们编写一个小脚本，该脚本将接受一系列以**XML**标签分隔的行，然后将其转换为 JavaScript 对象。

首先，让我们创建一个输入字符串：

```js
var xml = [
   "<title>File.js</title>",
   "<size>36 KB</size>",
   "<language>JavaScript</language>",
   "<modified>5 Minutes</name>"
].join("\n");
```

在这里，我们有四个属性，但是最后一个属性没有有效的闭合标签，所以不应该被捕获。接下来，我们将循环遍历这个模式，并设置一个`data`对象的属性：

```js
var data = {};

xml.split("\n").forEach(function(line){
   match = /<(\w+)>([^<]*)<\/\1>/.exec(line);
   if (match) {
      var tag = match[1];
      data[tag] = match[2];
   }
});
```

如果我们在控制台中输出数据，您将看到我们实际上获得了三个有效属性：

![捕获和非捕获组](img/2258OS_03_08.jpg)

但是，让我们花一点时间来检查这个模式；我们寻找一些带有名称的开放标签，然后捡起除了使用否定范围的开放三角括号之外的所有字符。之后，我们使用（`\1`）反向引用来查找闭合标签以确保其匹配。您可能还意识到我们需要转义斜杠，以便它不会认为我们正在关闭 Regexp 模式。

### 注意

当将反向引用添加到正则表达式模式的末尾时，允许您在模式内部引用子模式，以便记住子模式的值并将其用作匹配的一部分。例如，`/(no)\1/`在`nono`中匹配`nono`。`\1`将被替换为模式内的第一个子模式的值，或者(`no`)，从而形成最终模式。

到目前为止，我们看到的所有组都是**捕获组**，它们告诉 Regexp 将模式的这一部分提取到自己的变量中。但是，还有其他组或括号的用途可以实现更多的功能，其中之一是非捕获组。

#### 匹配非捕获组

**非捕获组**将模式的一部分分组，但实际上不会将这些数据提取到结果数组中，也不会在反向引用中使用它。其中一个好处是它允许您在模式中的完整部分上使用字符修饰符。例如，如果我们想要获得一个无限重复`world`的模式，我们可以将其写成这样：

```js
/(?:world)*/
```

这将匹配`world`以及`worldworldworld`等等。非捕获组的语法类似于标准组，只是你要用问号和（`?:`）冒号开始。对它进行分组使我们能够将整个内容视为单个对象，并使用修饰符，这些修饰符通常只适用于单个字符。

非捕获组的另一个最常见用途（也可以在捕获组中完成）是与管道字符一起使用。管道字符允许您在模式中依次插入多个选项，例如，在我们想要匹配`yes`或`no`的情况下，我们可以创建这个模式：

```js
/yes|no/
```

然而，大多数情况下，这组选项只会是模式的一小部分。例如，如果我们正在解析日志消息，我们可能想要提取日志级别和消息。日志级别只能是几个选项之一（例如`debug`、`info`、`error`等），但消息总是存在的。现在，您可以编写一个模式而不是这个：

```js
/[info] - .*|[debug] - .*|[error] - .*/
```

我们可以将共同部分提取到自己的非捕获组中：

```js
/[(?:info|debug|error)] - .*/
```

通过这样做，我们消除了大量重复的代码。

## 匹配前瞻组

您的代码中可以有的最后一组组是**前瞻**组。这些组允许我们对模式设置约束，但实际上并不包括这个约束在实际匹配中。使用非捕获组时，JavaScript 不会为某个部分创建特殊索引，尽管它会将其包含在完整结果中（结果的第一个元素）。使用前瞻组，我们希望能够确保在我们的匹配后面有或没有一些文本，但我们不希望这些文本出现在结果中。

例如，假设我们有一些输入文本，我们想要解析出所有.com 域名。我们可能并不一定希望在匹配中包含`.com`，只是实际的域名。在这种情况下，我们可以创建这个模式：

```js
/\w+(?=\.com)/g
```

具有`?=`字符的组意味着我们希望它在我们的模式末尾有这个文本，但实际上我们不想包括它；我们还必须转义句号，因为它是一个特殊字符。现在，我们可以使用这个模式来提取域：

```js
text.match(/\w+(?=\.com)/g)
```

我们可以假设我们有一个类似的变量文本：

![匹配前瞻组](img/2258OS_03_09.jpg)

### 使用负向前瞻

最后，如果我们想要使用**负向前瞻**，就像一个前瞻组确保包含的文本不遵循某种模式，我们可以简单地使用感叹号代替等号：

```js
var text = "Mr. Smith & Mrs. Doe";

text.match(/\w+(?!\.)\b/g);
```

这将匹配所有不以句号结尾的单词，也就是说，它将从这段文本中提取出名称：

![使用负向前瞻](img/2258OS_03_10.jpg)

# 摘要

在本章中，我们学习了如何处理贪婪和非贪婪匹配。我们还学习了如何使用组来创建更复杂的正则表达式。在学习如何对 Regex 进行分组时，我们还学习了捕获组、非捕获组和前瞻组。

在下一章中，我们将实现我们在本书中学到的一切，并创建一个真实世界的示例来匹配和验证用户输入的信息。