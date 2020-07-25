### 介绍

2011年，我成为了一名 Ruby on Rails 开发者。Rails 是一个伟大的框架。它也是一个庞大而应用广泛的框架。它尽量允许我们开箱即用尽可能多的功能（而无论我们是否用得到），这些功能甚至不用配置或者只需要极少的配置。

在使用 Rails 一段时间后，我决定转向更小型的框架，以获得更简约的使用方式。在尝试众多 Gem 之后，我选定了`Roda`。它由 Jeremy Evans 创建，我十分喜爱它，我想通过分享有关它的有关知识和使用方法，来表达我对它的喜爱。

### 关于 Roda

Roda 是一个树状路由 Web 工具。Roda 的设计哲学包括简约，可读性扩展性以及注重性能，它的默认配置只会开启一些最常用的基本特性。Roda 通过扩展的方式实现了大量特性。这些特性均可以通过插件进行开启。

可以把 Roda 的每个特性（插件），想象成一个工具，不同类型的 Web 应用依赖不同的工具。Roda 让我们自己选择我们打算用来构建 Web 应用的工具。Roda 常常被拿来与其他 Web 框架比较，事实上，比起 Web 框架，Roda 更像一个提供不同工具的库。

Roda 的路由实现，被开发者成为`树状路由`。如我们在上面提到的，树状路由为 Roda 提供了可扩展性和可用性。树状路由将路由配置与请求的响应集成在了一起，所以当路由被捕获的时候，我们也处理了它，这是树状路由的主要特点。利用这一特性，我们可以消除许多 Web 框架中，将路由与请求分开的固有代码。

Roda 是一个轻量级的库。默认开启的基础特性实现还不到 800 行代码。同时，Roda 提供了将近 100 个插件来实现大部分 Web 应用程序的需求。

Roda 设计之初就考虑了性能，被广泛认为是最快的 Ruby Web 框架。Roda 的某些性能优化代码难以理解，但 Roda 大多数代码是容易理解的。使用 Roda 构建的应用程序也容易理解，因为它可以清晰的追踪处理逻辑，并准确查看请求路由的处理方式。

Roda 特别注意应用程序范围内的污染，尽量避免在应用内部使用实例变量，常量或方法。这有助于避免因为名称冲突而产生的异常错误。Roda 内部的实例变量，均以下划线为前缀，常量使用 Roda 为前缀。而在应用范围内定义的方法很少。

在本书中，我们将介绍 Roda 基础概念和所提供的工具。这些理念和好的实践将帮助我们入门这个让人惊喜的库。

### 如何阅读这本书？

本书是由案例驱动的。每当一个概念介绍完毕后，都会抛出一个需要解决的问题或情况，来进行描述。

本书对略读是友好的。每个例子您都可以在家自己练习，我也建议您这样做。通过执行示例代码，可以很快弄明白书中的概念。

我还建议您进一步尝试这些代码。如果有些内容让你感到困惑，在联系我们之前，可以尝试修改代码来弄清到底缺的使哪些。如果您发现有些内容需要修改，请(提交一个 Merge Request)[https://gitlab.com/fiachetti/mastering-roda/merge_requests]。


### 快速介绍 lucid_http

在内容开始涉及 Roda 之前，我想先介绍 `lucid_http`，这是我为了展示 HTTP 的交互而创建的一个 gem。在本书其余的部分，将会使用该 gem 来完成发送请求和接收请求响应的示例代码。这里不详细展开。有关更详细的介绍，请参阅附录 `lucid_http gem`。

`lucid_http` 是在 `http.rb` 之上做了一层薄薄的封装。`http.rb` 提供了非常简单和一致的 API，用来执行 HTTP 请求。`lucid_http`在此之上，提供了更高层次的抽象表示。


