---
title: 工具
description: 支持 Dart 语言的开发工具。
show_breadcrumbs: false
toc: false
---


{% comment %}
When you're ready to create an app,
get the SDK and tools for your app type.
{% endcomment %}


在你准备好创建一个应用程序时，
请获对应于应用类型的SDK和工具。


{% comment %}
<div class="table-wrapper" markdown="1">
|------------+-----------------------------------+--------------------------|
| App type   | Get started instructions          | Tool information         |
|------------|-----------------------------------|--------------------------|
| Mobile | [Install Flutter]({{site.flutter}}/setup) | [Flutter tools]({{site.flutter}}/using-ide) |
| Web    | [Install the Dart SDK]({{site.webdev}}/tools/sdk) | [Dart tools for the web]({{site.webdev}}/tools) |
| Script or server | [Install the Dart SDK](/tools/sdk) | [Tools for server-side development](/server/tools) |
{:.table .table-striped}
</div>

The rest of this page covers general-purpose tools that
support the Dart language.
{% endcomment %}


<div class="table-wrapper" markdown="1">
|------------+-----------------------------------+--------------------------|
|  应用类型   |               使用说明              |          工具信息         |
|------------|-----------------------------------|--------------------------|
| 移动端      | [安装 Flutter]({{site.flutter}}/setup) | [Flutter 工具]({{site.flutter}}/using-ide) |
| Web        | [安装 Dart SDK]({{site.webdev}}/tools/sdk) | [Dart Web 端工具]({{site.webdev}}/tools) |
| 脚本或服务器 | [安装 Dart SDK](/tools/sdk) | [服务端开发工具](/server/tools) |
{:.table .table-striped}
</div>

本页的其余部分介绍了支持 Dart 语言的通用开发工具。


{% comment %}
## DartPad

<img src="{% asset dartpad-hello.png @path %}" alt="DartPad Hello World"
 width="200px" align="right" />
[DartPad](/tools/dartpad) is
a great, no-download-required way to learn Dart syntax
and to experiment with Dart language features.
It supports Dart's core libraries,
except for VM libraries such as dart:io.
{% endcomment %}


## DartPad

<img src="{% asset dartpad-hello.png @path %}" alt="DartPad Hello World"
 width="200px" align="right" />
[DartPad](/tools/dartpad) 无需下载，是学习 Dart 语法和体验 Dart 语言功能的
一个非常棒的途径。它支持 Dart 的核心库，但不包括 VM 库，例如 dart:io 。


{% comment %}
## IDEs and editors

Dart plugins exist for these commonly used IDEs.

<ul class="col2">
<li>
<img src="{% asset tools/android_studio.png @path %}"
     width="48" alt="IntelliJ logo">
<a class="no-automatic-external" href="https://developer.android.com/studio"><b>Android Studio</b></a>
</li>
<li>
<img src="{% asset tools/intellij-idea.svg @path %}"
     width="48" alt="IntelliJ logo">
<a class="no-automatic-external" href="/tools/jetbrains-plugin"><b>IntelliJ IDEA<br>
(and other JetBrains IDEs)</b></a>
</li>
<li>
<img src="{% asset tools/vscode.png @path %}" alt="Visual Studio Code logo">
<a class="no-automatic-external" href="https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code"><b>Visual Studio Code</b></a>
</li>
</ul>

The following Dart plugins are unsupported
and available as open source.

<ul class="col2">
<li>
<img src="{% asset tools/atom-logo.png @path %}" alt="Atom logo">
<a class="no-automatic-external" href="https://github.com/dart-atom/dartlang/"><b>Atom</b></a>
</li>
<li>
<img src="{% asset tools/emacs.png @path %}" alt="Emacs logo">
<a class="no-automatic-external" href="https://github.com/nex3/dart-mode"><b>Emacs</b></a>
</li>
<li>
<img src="{% asset tools/vim.png @path %}" alt="Vim logo">
<a class="no-automatic-external" href="https://github.com/dart-lang/dart-vim-plugin"><b>Vim</b></a>
</li>
</ul>
{% endcomment %}


## IDE 和 编辑器

这些常用的 IDE 中包含 Dart 插件。

<ul class="col2">
<li>
<img src="{% asset tools/android_studio.png @path %}"
     width="48" alt="IntelliJ logo">
<a class="no-automatic-external" href="https://developer.android.com/studio"><b>Android Studio</b></a>
</li>
<li>
<img src="{% asset tools/intellij-idea.svg @path %}"
     width="48" alt="IntelliJ logo">
<a class="no-automatic-external" href="/tools/jetbrains-plugin"><b>IntelliJ IDEA<br>
(以及其他 JetBrains IDE)</b></a>
</li>
<li>
<img src="{% asset tools/vscode.png @path %}" alt="Visual Studio Code logo">
<a class="no-automatic-external" href="https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code"><b>Visual Studio Code</b></a>
</li>
</ul>

下列 IDE 不支持 Dart 插件，但已有可用的开源支持。

<ul class="col2">
<li>
<img src="{% asset tools/atom-logo.png @path %}" alt="Atom logo">
<a class="no-automatic-external" href="https://github.com/dart-atom/dartlang/"><b>Atom</b></a>
</li>
<li>
<img src="{% asset tools/emacs.png @path %}" alt="Emacs logo">
<a class="no-automatic-external" href="https://github.com/nex3/dart-mode"><b>Emacs</b></a>
</li>
<li>
<img src="{% asset tools/vim.png @path %}" alt="Vim logo">
<a class="no-automatic-external" href="https://github.com/dart-lang/dart-vim-plugin"><b>Vim</b></a>
</li>
</ul>


{% comment %}
## Command-line tools

Some command-line tools are in Dart-related SDKs,
and some are in packages.

### Tools in SDKs

Most Dart-related SDKs include the following tools:

[Pub package manager (`pub`)](/tools/pub) 
: Manages Dart packages,
  making it easy for you to install, use, and share Dart libraries,
  command-line tools, and other assets.
  Some Dart technologies, such as Flutter, may not support
  all of the pub commands.
  IDEs that support Dart generally have special support for pub,
  but you can also use it from the command line.

[Static analyzer (`dartanalyzer`)](/tools/analyzer)
: Evaluates and reports any errors or warnings in your code.
  The Dart plugin for your IDE should make use of Dart's analysis engine,
  but you can also run the analyzer from the command line.

[Code formatter (`dartfmt`)](https://github.com/dart-lang/dart_style#readme)
: Formats your code, following the recommendations of the
  [Dart Style Guide](/guides/language/effective-dart/style).
  IDEs that support Dart generally allow you to format the code within
  the IDE. Or you can run the formatter from the command line.

### Tools in packages

The following tools are distributed in packages on the Dart package site.
To install them, use the `pub` command, as described in each tool's
installation instructions.

[build_runner][]
: A code generator.

[dartfix][]
: A tool for migrating Dart source code and fixing common issues.

Also see the [dart_style][] package, which can be useful
for getting a version of `dartfmt` that's different
from the one included in the SDK.

[build_runner]: /tools/build_runner
[dartfix]: {{site.pub-pkg}}/dartfix
[dart_style]: {{site.pub-pkg}}/dart_style
{% endcomment %}


## 命令行工具

一些命令行工具被包含在 Dart 相关的 SDK 中，及一些包（package）中。

### SDK 中的工具

大多数与 Dart 相关的 SDK 包括以下工具。

[Pub 包管理工具 (`pub`) ](/tools/pub)
: 通过管理 Dart 包，可以轻松的安装，使用和共享 Dart 库，命令行工具以及其他资源。
  某些 Dart 技术（如 Flutter ）可能不支持所有 Pub 命令。支持 Dart 的 IDE 
  通常会支持 Pub，当然你也可以通过命令行使用它。

[静态分析工具 (`dartanalyzer`) ](/tools/analyzer)
: 预估并提示代码中的错误或警告。IDE 的 Dart 插件会使用 Dart 的分析工具，
  当然你也可以从命令行执行分析工具。

[代码格式化工具 (`dartfmt`) ](https://github.com/dart-lang/dart_style#readme)
: 按照 Dart [风格指导](/guides/language/effective-dart/style)的建议格式化你的代码。
  支持 Dart 的 IDE 通常允许你在 IDE 中格式化代码。或者可以在命令行执行格式化程序。

### 包中的工具

下列工具分布在 Dart 包站点上的包中。
根据每个工具的安装说明描述，使用 `pub` 命令安装这些工具。

[build_runner][]
: 代码生成器。

[dartfix][]
: 用于 Dart 源代码迁移和常见问题修复的工具。

另请参见 [dart_style][] 包，该工具可以获取任意版本的 `dartfmt` ，
获取的 `dartfmt` 的版本可以与 SDK 中包含的版本不同。

[build_runner]: /tools/build_runner
[dartfix]: {{site.pub-pkg}}/dartfix
[dart_style]: {{site.pub-pkg}}/dart_style


