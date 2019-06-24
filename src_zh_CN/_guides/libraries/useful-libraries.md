---
title: 常用包
description: 在这里你可以了解更多非常流行的有用的包。
---


{% comment %}

This page lists some of the most popular and useful
[packages](/guides/packages) that Dart developers have published.
To find more packages —
and search [core libraries](/guides/libraries), as well —
use the [Pub site.]({{site.pub}})

Commonly used packages fall into three groups:

{% endcomment %}


本章列出了一些 Dart 开发者发布的非常流行的有用的[包](/guides/packages)。
到 [Pub 网站]({{site.pub}})发现更多包及[核心库](/guides/libraries)。

常用包分为以下三组：

- [通用包](#%E9%80%9A%E7%94%A8%E5%8C%85)
- [在 Dart 核心库上的扩展包 {#packages-that-correspond-to-sdk-libraries}](#%E5%9C%A8-dart-%E6%A0%B8%E5%BF%83%E5%BA%93%E4%B8%8A%E7%9A%84%E6%89%A9%E5%B1%95%E5%8C%85-packages-that-correspond-to-sdk-libraries)
- [专业包](#%E4%B8%93%E4%B8%9A%E5%8C%85)
  - [Flutter 包](#flutter-%E5%8C%85)
  - [Web 包](#web-%E5%8C%85)
  - [命令行和服务器包](#%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%92%8C%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%8C%85)


{% comment %}

## General-purpose packages

The following packages are useful for a wide range of projects.

| **Package** | **Description** | **Commonly used APIs** |
| [archive]({{site.pub-pkg}}/archive) | Encodes and decodes various archive and compression formats. | Archive, ArchiveFile, TarEncoder, TarDecoder, ZipEncoder, ZipDecoder |
| [http]({{site.pub-pkg}}/http) | A set of high-level functions and classes that make it easy to consume HTTP resources. | delete(), get(), post(), read() |
| [intl]({{site.pub-pkg}}/intl) | Internationalization and localization facilities, with support for plurals and genders, date and number formatting and parsing, and bidirectional text. | Bidi, DateFormat, MicroMoney, TextDirection |
| [json_serializable]({{site.pub-pkg}}/json_serializable) | An easy-to-use code generation package. For more information, see [JSON Support](/guides/json). | @JsonSerializable |
| [logging]({{site.pub-pkg}}/logging) | A configurable mechanism for adding message logging to your application. | LoggerHandler, Level, LogRecord |
| [mockito]({{site.pub-pkg}}/mockito) | A popular framework for mocking objects in tests. Especially useful if you are writing tests for dependency injection. Used with the [test]({{site.pub-pkg}}/test) package. | Answering, Expectation, Verification |
| [path]({{site.pub-pkg}}/path) | Common operations for manipulating different types of paths. For more information, see [Unboxing Packages: path.]({{site.news}}/2016/06/unboxing-packages-path.html) | absolute(), basename(), extension(), join(), normalize(), relative(), split() |
| [quiver]({{site.pub-pkg}}/quiver) | Utilities that make using core Dart libraries more convenient. Some of the libraries where Quiver provides additional support include async, cache, collection, core, iterables, patterns, and testing. | CountdownTimer (quiver.async); MapCache (quiver.cache); MultiMap, TreeSet (quiver.collection); EnumerateIterable (quiver.iterables); center(), compareIgnoreCase(), isWhiteSpace() (quiver.strings)  |
| [shelf]({{site.pub-pkg}}/shelf) | Web server middleware for Dart. Shelf makes it easy to create and compose web servers, and parts of web servers. | Cascade, Pipeline, Request, Response, Server |
| [stack_trace]({{site.pub-pkg}}/stack_trace) | Methods for parsing, inspecting, and manipulating stack traces produced by the underlying Dart implementation. Also provides functions to produce string representations of stack traces in a more readable format than the native StackTrace implementation. For more information, see [Unboxing Packages: stack_trace.]({{site.news}}/2016/01/unboxing-packages-stacktrace.html) | Trace.current(), Trace.format(), Trace.from() |
| [stagehand]({{site.pub-pkg}}/stagehand) | A Dart project generator. WebStorm and IntelliJ use Stagehand templates when you create a new application, but you can also use the templates from the command line. | Generally used through an IDE or the `stagehand` command. |
| [test]({{site.pub-pkg}}/test) | A standard way of writing and running tests in Dart. | expect(), group(), test() |
| [yaml]({{site.pub-pkg}}/yaml) | A parser for YAML. | loadYaml(), loadYamlStream() |
{:.table .table-striped .nowrap}

{% endcomment %}


## 通用包

以下包被广泛的应用于项目中。

| **包** | **描述** | **常用 API** |
| [archive]({{site.pub-pkg}}/archive) | 用于各种存档和压缩格式的编解码。 | Archive, ArchiveFile, TarEncoder, TarDecoder, ZipEncoder, ZipDecoder |
| [http]({{site.pub-pkg}}/http) | 一组可以轻松使用 HTTP 资源的高级函数和类。 | delete(), get(), post(), read() |
| [intl]({{site.pub-pkg}}/intl) | 用于国际化和本地化实施，支持复数表示，性别，日期，数字解析以及双向文本。 | Bidi, DateFormat, MicroMoney, TextDirection |
| [json_serializable]({{site.pub-pkg}}/json_serializable) | 简单易用的用于代码生成的包。更多内容，参见 [JSON 支持](/guides/json)。 | @JsonSerializable |
| [logging]({{site.pub-pkg}}/logging) | 为应用增加可配置日志。 | LoggerHandler, Level, LogRecord |
| [mockito]({{site.pub-pkg}}/mockito) | 在测试中 Mock 对象的流行框架。在依赖注入测试中非常有用。配合 [test]({{site.pub-pkg}}/test) 包使用。 | Answering, Expectation, Verification |
| [path]({{site.pub-pkg}}/path) | 为不同类型路径访问提供的通用操作。更多内容，参见 [Unboxing Packages: path]({{site.news}}/2016/06/unboxing-packages-path.html)。 | absolute(), basename(), extension(), join(), normalize(), relative(), split() |
| [quiver]({{site.pub-pkg}}/quiver) | Dart 核心库便捷工具。便捷工具为一些库提供额外扩展，这些库包括：Async， Cache， Collection， Core， Iterables， Patterns， 和 testing。 | CountdownTimer (quiver.async); MapCache (quiver.cache); MultiMap, TreeSet (quiver.collection); EnumerateIterable (quiver.iterables); center(), compareIgnoreCase(), isWhiteSpace() (quiver.strings)  |
| [shelf]({{site.pub-pkg}}/shelf) | Dart 的 Web 服务器中间件。 Shelf 可以轻松创建和组合 Web 服务器和 Web 服务器的部分服务。 | Cascade, Pipeline, Request, Response, Server |
| [stack_trace]({{site.pub-pkg}}/stack_trace) | 由 Dart 底层实现用于堆栈跟踪信息解析、查看、处理的方法。还提供了堆栈跟踪信息字符串格式化生成函数。字符串格式化后的表示比原生堆栈跟踪信息具有更高的可读性。有关更多内容，请参见 [Unboxing Packages: stack_trace]({{site.news}}/2016/01/unboxing-packages-stacktrace.html)。 | Trace.current(), Trace.format(), Trace.from() |
| [stagehand]({{site.pub-pkg}}/stagehand) | Dart 项目生成器。 WebStorm 和 IntelliJ 在创建新应用程序时使用 Stagehand 模板，这些模板也可以在命令行中使用。| Generally used through an IDE or the `stagehand` command. |
| [test]({{site.pub-pkg}}/test) | 在 Dart 中标准编写和运行测试的方式。 | expect(), group(), test() |
| [yaml]({{site.pub-pkg}}/yaml) | YAML 解析器。 | loadYaml(), loadYamlStream() |
{:.table .table-striped .nowrap}


{% comment %}

## Packages that expand on Dart core libraries {#packages-that-correspond-to-sdk-libraries}

Each of the following packages builds upon a [core library](/guides/libraries),
adding functionality and filling in missing features:

| **Package** | **Description** | **Commonly used APIs** |
| [async]({{site.pub-pkg}}/async) | Expands on dart:async, adding utility classes to work with asynchronous computations. For more information, see [Unboxing Packages: async part 1]({{site.news}}/2016/03/unboxing-packages-async-part-1.html), [part 2]({{site.news}}/2016/03/unboxing-packages-async-part-2.html), and [part 3.]({{site.news}}/2016/04/unboxing-packages-async-part-3.html) | AsyncMemoizer, CancelableOperation, FutureGroup, LazyStream, Result, StreamCompleter, StreamGroup, StreamSplitter |
| [collection]({{site.pub-pkg}}/collection) | Expands on dart:collection, adding utility functions and classes to make working with collections easier. For more information, see [Unboxing Packages: collection.]({{site.news}}/2016/01/unboxing-packages-collection.html) | Equality, CanonicalizedMap, MapKeySet, MapValueSet, PriorityQueue, QueueList |
|[convert]({{site.pub-pkg}}/convert) | Expands on dart:convert, adding encoders and decoders for converting between different data representations. One of the data representations is _percent encoding_, also known as _URL encoding_. | HexDecoder, PercentDecoder |
|[io]({{site.pub-pkg}}/io) | Contains two libraries, ansi and io, to simplify working with files, standard streams, and processes. Use the ansi library to customize terminal output. The io library has APIs for dealing with processes, stdin, and file duplication. |  copyPath(), isExecutable(), ExitCode, ProcessManager, sharedStdIn |
{:.table .table-striped .nowrap}

{% endcomment %}


## 在 Dart 核心库上的扩展包 {#packages-that-correspond-to-sdk-libraries}

以下包基于[核心库](/guides/libraries)构建，
添加功能，并补全缺少的功能：

| **包** | **描述** | **常用 API** |
| [async]({{site.pub-pkg}}/async) | 基于 dart:async 的扩展，增加 Utility 类用于异步计算。更多内容，参见 [Unboxing Packages: async part 1]({{site.news}}/2016/03/unboxing-packages-async-part-1.html)， [part 2]({{site.news}}/2016/03/unboxing-packages-async-part-2.html)， 以及 [part 3]({{site.news}}/2016/04/unboxing-packages-async-part-3.html)。 | AsyncMemoizer, CancelableOperation, FutureGroup, LazyStream, Result, StreamCompleter, StreamGroup, StreamSplitter |
| [collection]({{site.pub-pkg}}/collection) | 基于 dart:collection 的扩展，增加, 增加 Utility 类，简化集合操作。更多内容参见 [Unboxing Packages: collection]({{site.news}}/2016/01/unboxing-packages-collection.html)。 | Equality, CanonicalizedMap, MapKeySet, MapValueSet, PriorityQueue, QueueList |
|[convert]({{site.pub-pkg}}/convert) | 基于 dart:convert 的扩展，增加编解码器，用于在不同的数据表示之间进行转换。其中具有代表性的 _percent encoding_ ，也被称为 _URL encoding_ 。 | HexDecoder, PercentDecoder |
|[io]({{site.pub-pkg}}/io) | 包含两个库 ansi 和 io ，用来简化文件，标准流及进程处理。通过 ansi 可以实现自定义终端输出。 io 库用于处理进程，标准输入，以及文件拷贝等。 |  copyPath(), isExecutable(), ExitCode, ProcessManager, sharedStdIn |
{:.table .table-striped .nowrap}


{% comment %}

## Specialized packages

Here are some tips for finding packages that are more specialized,
such as packages for mobile (Flutter) and web development.

{% endcomment %}


## 专业包

以下是一些查找更专业软件包的技巧，例如用于移动开发（Flutter）和 Web 开发的包。


{% comment %}

### Flutter packages

See [Using packages]({{site.flutter}}/docs/development/packages-and-plugins/using-packages)
on the Flutter site.
Or use the Pub site to [search for Flutter packages.]({{site.pub}}/flutter)

{% endcomment %}


### Flutter 包

在 Flutter 网站，查看[包的使用]({{site.flutter}}/docs/development/packages-and-plugins/using-packages)。
或者使用 Pub 网站[查找 Flutter 包]({{site.pub}}/flutter)。


{% comment %}

### Web packages

See [Web libraries and packages](/web/libraries).
Or use the Pub site to [search for web packages.]({{site.pub}}/web)

{% endcomment %}


### Web 包

查看 [Web 库和包](/web/libraries)。
或者使用 Pub 网站[查找用于 Web 的包]({{site.pub}}/web)。


{% comment %}

### Command-line and server packages

See [Command-line and server libraries and packages](/server/libraries).
Or use the Pub site to [search for other packages.]({{site.pub}})

{% endcomment %}


### 命令行和服务器包

查看 [命令行和服务器的库和包](/server/libraries)。
或者使用 Pub 网站[查找用于其它应用的包]({{site.pub}})。

