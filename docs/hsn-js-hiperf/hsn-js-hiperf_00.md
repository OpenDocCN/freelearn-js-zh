# 前言

今天的网络环境发生了巨大变化-不仅在创建 Web 应用程序方面，而且在创建服务器端应用程序方面也是如此。以 jQuery 和 Bootstrap 等 CSS 框架为主导的前端生态系统已经被具有响应性的完整应用程序所取代，这些应用程序可能被误认为是在桌面上运行的应用程序。

我们编写这些应用程序的语言也发生了戏剧性的变化。曾经是一团混乱的`var`和作用域问题已经变成了一种快速且易于编程的语言。JavaScript 不仅改变了我们编写前端的方式，还改变了后端编程的体验。

我们现在能够用我们前端使用的语言来编写服务器端应用程序。JavaScript 也现代化了，甚至可能通过 Node.js 推广了事件驱动系统。我们现在可以用 JavaScript 编写前端和后端的代码，甚至可能在两者之间共享我们生成的 JavaScript 文件。

然而，尽管应用程序的格局已经发生了变化，许多人已经转向了现代框架，比如 React 和 Vue.js 用于前端，Express 和 Sails 用于后端，但许多这些开发人员并不了解内部运作。虽然这展示了进入生态系统是多么简单，但也展示了我们如何不理解如何优化我们的代码库是多么容易。

本书专注于教授高性能 JavaScript。这不仅意味着快速执行速度，还意味着更低的内存占用。这意味着任何前端系统都能更快地到达用户手中，我们也能更快地启动我们的应用程序。除此之外，我们还有许多新技术推动了网络的发展，比如 Web Workers。

# 本书对象

本书适合那些对现代网络的最新功能感兴趣的人。除此之外，它也适合那些对减少内存成本并提高速度感兴趣的人。对计算机工作原理甚至 JavaScript 编译器工作原理感兴趣的人也会对本书内容感兴趣。最后，对于那些对 WebAssembly 感兴趣但不知道从何开始的人来说，这是学习基本知识的好起点。

# 本书内容

第一章，“网络高性能工具”，将介绍我们的应用程序可以运行的各种浏览器。我们还将介绍各种工具，帮助我们调试、分析，甚至运行临时代码来测试我们的 JavaScript 功能。

第二章，“不可变性与可变性-安全与速度之间的平衡”，将探讨可变/不可变状态的概念。我们将介绍何时何地使用每种状态。除此之外，我们还将介绍如何在拥有可变数据结构的同时创建不可变性的幻觉。

第三章，“原生之地-看看现代网络”，将介绍 JavaScript 的发展历程以及截至 ECMAScript 2020 的所有新功能。除此之外，我们还将探讨各种高级功能，比如柯里化和以函数式方式编写。

第四章，“实际例子-看看 Svelte 和原生”，将介绍一个相当新的框架叫做 Svelte。它将介绍这个编译成原生 JavaScript 的框架，并探讨它如何通过直观的框架实现闪电般快速的结果。

第五章，“切换上下文-无 DOM，不同的原生”，将介绍低级别的 Node.js 工作。这意味着我们将看看各种可用的模块。我们还将看看如何在没有额外库的情况下实现惊人的结果。

第六章，*消息传递-了解不同类型*，将介绍不同进程之间交流的不同方式。我们将涵盖未命名管道，命名管道，套接字，以及通过 TCP/UDP 进行传输。我们还将简要介绍 HTTP/2 和 HTTP/3。

第七章，*流-理解流和非阻塞 I/O*，将介绍流 API 以及如何利用它。我们将介绍每种类型的流以及每种流的用例。除此之外，我们还将实现一些实用的流，经过一些修改后，可以在其他项目中使用。

第八章，*数据格式-查看除 JSON 之外的不同数据类型*，将研究模式和无模式数据类型。我们将研究实施数据格式，然后看看流行的数据格式是如何运作的。

第九章，*实际示例-构建静态服务器*，将使用前面四章的概念构建一个静态站点生成器。虽然它可能没有 GatsbyJS 那么强大，但它将具有我们从静态站点生成器中期望的大多数功能。

第十章，*Workers-了解专用和共享工作者*，将回到前端，看看两种 Web Worker 类型。我们将利用这些来处理来自主线程的数据。除此之外，我们还将看看如何在工作者和主进程之间交流。

第十一章，*Service Workers-缓存和加速*，将介绍服务工作者和服务工作者的生命周期。除此之外，我们还将看看如何在渐进式 Web 应用程序中利用服务工作者的实际示例。

第十二章，*构建和部署完整的 Web 应用程序*，将使用 CircleCI 工具进行**持续集成**/**持续部署**（**CI**/**CD**）。我们将看到如何使用它来部署我们在第九章构建的 Web 应用程序，*实际示例-构建静态服务器*，到服务器上。我们甚至将在部署之前检查应用程序的一些安全性。

第十三章，*WebAssembly-简要了解 Web 上的本机代码*，将介绍这项相对较新的技术。我们将看到如何编写低级 WebAssembly 以及它在 Web 上的运行方式。然后，我们将把注意力转向为浏览器编写 C++。最后，我们将看看一个移植的应用程序以及背后的 WebAssembly。

# 为了充分利用本书

总的来说，运行大多数代码的要求是最低的。需要一台能够运行 Chrome、Node.js 和 C 编译器的计算机。我们将在本书的最后使用的 C 编译器将是 CMake。这些系统应该在所有现代操作系统上都能运行。

对于 Chrome 来说，拥有最新版本将是有帮助的，因为我们将利用一些提案阶段或 ECMAScript 2020 中的功能。我们正在使用最新的 LTS 版本的 Node.js（v12.16.1），并且避免使用 Node.js 13，因为它不会被提升为 LTS。除此之外，Windows 的命令行工具并不是很好，因此建议下载 Cmder，从[`cmder.net/`](https://cmder.net/)，以在 Windows 上拥有类似 Bash 的 shell。

最后，需要一个现代的集成开发环境或编辑器。我们将在整本书中使用 Visual Studio Code，但也可以使用许多其他替代方案，比如 Visual Studio、IntelliJ、Sublime Text 3 等。

| **书中涉及的软件/硬件** | **操作系统要求** |
| --- | --- |
| Svelte.js v3 | Windows 10/OSX/Linux |
| ECMAScript 2020 | Windows 10/OSX/Linux |
| Node.js v12.16.1 LTS | Windows 10/OSX/Linux |
| WebAssembly | Windows 10/OSX/Linux |

# 下载示例代码文件

您可以从[www.packt.com](http://www.packt.com)的帐户中下载本书的示例代码文件。如果您在其他地方购买了本书，可以访问[www.packtpub.com/support](https://www.packtpub.com/support)注册，文件将直接发送到您的邮箱。

您可以按照以下步骤下载代码文件：

1.  在[www.packt.com](http://www.packt.com)登录或注册。

1.  选择支持选项卡。

1.  点击代码下载。

1.  在搜索框中输入书名，然后按照屏幕上的说明操作。

下载文件后，请确保使用最新版本的软件解压或提取文件夹：

+   Windows 系统使用 WinRAR/7-Zip

+   Mac 系统使用 Zipeg/iZip/UnRarX

+   Linux 系统使用 7-Zip/PeaZip

本书的代码包也托管在 GitHub 上，网址为[`github.com/PacktPublishing/Hands-On-High-Performance-Web-Development-with-JavaScript`](https://github.com/PacktPublishing/Hands-On-High-Performance-Web-Development-with-JavaScript)。如果代码有更新，将在现有的 GitHub 存储库中更新。

我们还有其他代码包，来自我们丰富的图书和视频目录，可在**[`github.com/PacktPublishing/`](https://github.com/PacktPublishing/)** 上找到。去看看吧！

# 使用的约定

本书中使用了许多文本约定。

`CodeInText`：表示文本中的代码词、数据库表名、文件夹名、文件名、文件扩展名、路径名、虚拟 URL、用户输入和 Twitter 用户名。例如："这与`console.time`和`timeEnd`非常相似，但它应该展示生成器可用的内容。"

代码块设置如下：

```js
for(let i = 0; i < 100000; i++) {
    const j = Library.outerFun(true);
}
```

任何命令行输入或输出都是这样写的：

```js
> npm install what-the-pack
```

**粗体**：表示新术语、重要单词或屏幕上看到的单词。例如，菜单或对话框中的单词会以这种方式出现在文本中。例如："如果我们在 Windows 中按下*F12*打开 DevTools，我们可能会看到**Shader Editor**选项卡已经打开。"

警告或重要提示会显示为这样。提示和技巧会显示为这样。
