---
title: 服务器 Dart
description: 与命令行和服务器端应用相关的所有内容。
toc: false
---

{% comment %}

This page points to tools and documentation
that can help you develop command-line and server apps.

<p class="text-center">
  <a href="/tutorials/server/get-started" class="btn btn-primary btn-lg">Get started</a>
</p>

{% endcomment %}


本章内容用来介绍一些有助于开发命令行和服务器应用的工具及文档。

<p class="text-center">
  <a href="/tutorials/server/get-started" class="btn btn-primary btn-lg">Get started</a>
</p>


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
  libraries and [tools](/tools).

More tools
: The [Tools](/tools) page links to generally useful tools,
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
  [工具](/tools)。

更多工具
: [工具](/tools) 页面中会提供常用工具的链接。比如一些 IDE 或 编辑器
  的 Dart 插件。


{% comment %}

## Tutorials

You might find the following tutorials helpful.

[Get started](/tutorials/server/get-started)
: Learn how to use the Dart SDK to develop command-line and server apps.

[gRPC Quickstart](https://grpc.io/docs/quickstart/dart.html)
: Walks you through running and modifying a client-server example that uses the gRPC framework.

[Write command-line apps](/tutorials/server/cmdline)
: Introduces dart:io and the args package.

[Write HTTP clients & servers](/tutorials/server/httpserver)
: Features dart:io and the http_server package.

{% endcomment %}


## 学习指南

你可能会感到下列学习指南对你很有帮助。

[入门](/tutorials/server/get-started)
: 学习如何使用 Dart SDK 来开发命令行和服务端应用。

[gRPC 快速入门](https://grpc.io/docs/quickstart/dart.html)
：通过运行和修改使用 gRPC 框架的客户端服务示例来介绍 gRPC 框架。

[编写命令行应用](/tutorials/server/cmdline)
: 介绍 dart:io 及包参数（args package）。

[编写 HTTP 客户端 & 服务端](/tutorials/server/httpserver)
: 专题介绍 dart:io 和 http_server 包。


{% comment %}

## More resources

[Dart API]({{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}})
: API reference for dart:* libraries.

[dart:io section of the library tour](/guides/libraries/library-tour/#dartio)
: Shows how to use the major features of the dart:io library.
  You can use the dart:io library in command-line scripts, servers, and
  [Flutter mobile apps.]({{site.flutter}})

{% endcomment %}


## 更多资源

[Dart API]({{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}})
: dart:* 的 API 参考。

[库概览中的 dart:io 章节](/guides/libraries/library-tour/#dartio)
: 演示如何使用 dart:io 库的主要功能。 dart:io 库可以应用在命令行脚本，服务器应用以及 
  [Flutter 移动应用]({{site.flutter}}) 中。
