---
title: 服务器 Dart
description: 与命令行和服务器端应用相关的所有内容。
toc: false
---


{% comment %}
This page points to tools and documentation
that can help you develop command-line and server-side apps.
{% endcomment %}


本章内容用来介绍一些有助于开发命令行和服务器应用的工具及文档。


{% comment %}
## Tools

[DartPad](/tools/dartpad)
: Handy for both beginners and experts,
  DartPad lets you try out language features and dart:* APIs.

  <aside class="alert alert-info" markdown="1">
    **Note:** DartPad does **not** support using dart:io APIs or
    importing libraries from packages.
  </aside>

[Dart SDK](/tools/sdk)
: [Install the Dart SDK](/tools/sdk#install) to get the core Dart
  libraries and [tools](/server/tools).

More tools
: The Dart [Tools](/tools) page links to generally useful tools,
  such as Dart plugins for your favorite IDE or editor.
{% endcomment %}

## 工具

[DartPad](/tools/dartpad)
: 无论是初学者还是专家，都可以便捷的通过 DartPad 尝试 Dart 语言的功能和 
  dart:* API 。

  <aside class="alert alert-info" markdown="1">
    **提示：** DartPad **不**支持 dart:io API 及其 package 的库导入。
  </aside>

[Dart SDK](/tools/sdk)
: [安装 Dart SDK](/tools/sdk#install) 来获取 Dart 核心库及
  [工具](/server/tools)。

更多工具
: Dart [工具](/tools) 页面中会提供常用工具的链接。比如一些 IDE 或 编辑器
  的 Dart 插件。


{% comment %}
## Tutorials

You might find the following tutorials helpful.

[Get Started](/tutorials/server/get-started)
: Shows how to write a basic Dart script.

[gRPC Quickstart](https://grpc.io/docs/quickstart/dart.html)
: Walks you through running and modifying a client-server example that uses the gRPC framework.

[Write Command-Line Apps](/tutorials/server/cmdline)
: Introduces dart:io and the args package.

[Write HTTP Clients & Servers](/tutorials/server/httpserver)
: Features dart:io and the http_server package.
{% endcomment %}


## 学习指南

你可能会感到下列学习指南对你很有帮助。

[入门](/tutorials/server/get-started)
: 演示如何编写基本 Dart 脚本。

[gRPC 快速入门](https://grpc.io/docs/quickstart/dart.html)
：通过运行和修改使用 gRPC 框架的客户端服务示例来介绍 gRPC 框架。

[编写命令行应用](/tutorials/server/cmdline)
: 介绍 dart:io 及包参数（args package）。

[编写 HTTP Client & Server](/tutorials/server/httpserver)
: 专题介绍 dart:io 和 http_server 包。


{% comment %}
## More resources

[Dart API]({{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}})
: API reference for dart:* libraries.

[A Tour of the dart:io Library](/server/io-library-tour)
: Shows how to use the major features of the dart:io library.
  You can use the dart:io library in command-line scripts, servers, and
  [Flutter mobile apps.]({{site.flutter}})

[Articles: Server-Side Dart](/articles/server)
: A collection of articles covering topics such as benchmarking,
  numeric computation, and SIMD.
{% endcomment %}


## 更多资源

[Dart API]({{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}})
: dart:* 的 API 参考。

[dart:io 库概览](/server/io-library-tour)
: 演示如何使用 dart:io 库的主要功能。 dart:io 库可以应用在命令行脚本，服务器应用以及 
  [Flutter 移动应用]({{site.flutter}}) 中。

[服务器 Dart 的文章](/articles/server)
: 包含例如 benchmarking ，数值计算，以及 SIMD 等话题的一些列文章。
