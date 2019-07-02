---
title: 创建 Package
description: 学习在 Dart 中如何创建 Library Package 。
---

{% comment %}

The Dart ecosystem uses [packages][]
to share software such as libraries and tools.
This page tells you how to create a package,
with a focus on the most common kind of package,
[_library_ packages](/tools/pub/glossary#library-package).

{% comment %}
TODO: Add coverage of packages that contain tools.
{% endcomment %}

{% endcomment %}


在 Dart 生态系统中使用 [Package][] 实现共享软件，
比如一些 Library 和工具。
本章将通过最常见的 [Library Package](/tools/pub/glossary#library-package)
来介绍如何创建一个 Package 。

{% comment %}
TODO: Add coverage of packages that contain tools.
{% endcomment %}

[Package]: /guides/packages


{% comment %}

## What makes a library package

The following diagram shows the layout of the simplest
library package:

{% asset libraries/simple-lib2.png alt="root directory contains pubspec.yaml and lib/file.dart" %}

The minimal requirements for a library are:

<dl markdown="1">

<dt markdown="1">
pubspec file
</dt>
<dd markdown="1">
The `pubspec.yaml` file for a library is the same
as for an application package&mdash;there is no special
designation to indicate that the package is a library.
</dd>

<dt markdown="1">
lib directory
</dt>
<dd markdown="1">
As you might expect, the library code lives under the _lib_
directory and is public to other packages.
You can create any hierarchy under lib, as needed.
By convention, implementation code is placed under _lib/src_.
Code under lib/src is considered private;
other packages should never need to import `src/...`.
To make APIs under lib/src public, you can export lib/src files
from a file that's directly under lib.
</dd>

<aside class="alert alert-info" markdown="1">
**Note:**
When the `library` directive isn't specified, a unique
tag is generated for each library based on its path and filename.
Therefore, we suggest that you omit the `library` directive from
your code unless you plan to
[generate library-level documentation](#documenting-a-library).
</aside>

</dl>

{% endcomment %}


## Library Package 的组成

下图展示了最简单的 Library Package 布局：

{% asset libraries/simple-lib2.png alt="root directory contains pubspec.yaml and lib/file.dart" %}

Library 的最基本要求包括：

<dl markdown="1">

<dt markdown="1">
pubspec 文件
</dt>
<dd markdown="1">
Library 的 `pubspec.yaml` 文件与应用程序的 `pubspec.yaml` 文件相同&mdash; `pubspec.yaml` 文件中并没有特别的指出这个 Package 是一个 Library 。
</dd>

<dt markdown="1">
lib 目录
</dt>
<dd markdown="1">
如你所料， Library 的代码位于 _lib_ 目录下，且对于其他 Package 是公开的。
你可以根据需要在 _lib_ 下任意创建组织文件结构。
按照惯例，实现代码会放在 _lib/src_ 目录下。
lib/src 目录下的代码被认为是私有的。
其他 Package 应该永远不需要导入 `src/...` 目录下代码。
通过导出 lib/src 目录的文件到一个 lib 目录的文件，实现
对 lib/src 目录中 API 的公开。
</dd>

<aside class="alert alert-info" markdown="1">
**提示：**
在未指定 `library` 命令下，每个 Library 会根据它的路径及文件
生成一个唯一标记。
因此，这里我们建议在你的代码中忽略 `library` 命令，除非想要
[生成 Library-Level 文档](#documenting-a-library)。
</aside>

</dl>


{% comment %}

## Organizing a library package

Library packages are easiest to maintain, extend, and test
when you create small, individual libraries, referred to as
_mini libraries_.
In most cases, each class should be in its own mini library, unless
you have a situation where two classes are tightly coupled.

<aside class="alert alert-info" markdown="1">
**Note:** You may have heard of the `part` directive, which allows
you to split a library into multiple Dart files. We recommend
that you avoid using `part` and create mini libraries instead.
</aside>

Create a "main" library file directly under lib,
lib/_&lt;package-name&gt;_.dart, that
exports all of the public APIs.
This allows the user to get all of a library's functionality
by importing a single file.

The lib directory might also include other importable, non-src, libraries.
For example, perhaps your main library works across platforms, but
you create separate libraries that rely on dart:io or dart:html.
Some packages have separate libraries that are meant to be imported
with a prefix, when the main library is not.

Let's look at the organization of a real-world library package: shelf. The
[shelf](https://github.com/dart-lang/shelf)
package provides an easy way to create web servers using Dart,
and is laid out in a structure that is commonly used for Dart
library packages:

{% asset libraries/shelf.png alt="shelf root directory contains example, lib, test, and tool subdirectories" %}

Directly under lib, the main library file,
`shelf.dart`, exports several files from lib/src:

{% prettify dart %}
export 'src/cascade.dart';
export 'src/handler.dart';
export 'src/handlers/logger.dart';
export 'src/hijack_exception.dart';
export 'src/middleware.dart';
export 'src/pipeline.dart';
export 'src/request.dart';
export 'src/response.dart';
export 'src/server.dart';
export 'src/server_handler.dart';
{% endprettify %}

The shelf package also contains a mini library: shelf_io.
This adapter handles HttpRequest objects from dart:io.

<aside class="alert alert-info" markdown="1">
**Tip for web apps:**
For the best performance when developing with
[dartdevc,](/tools/dartdevc)
put [implementation
files](/tools/pub/package-layout#implementation-files) under `/lib/src`,
instead of elsewhere under `/lib`.
Also, avoid imports of <code>package:<em>package_name</em>/src/...</code>.
</aside>

{% endcomment %}


## 组织 Library Package

在创建一个小的，独立的 Library（称之为 _Mini Library_）。
Library Package 非常容易维护，扩展和测试。
大多数情况下，除非存在两个类紧密耦合的情况，否则每个类都应该将自己视为一个 Mini Library 。

<aside class="alert alert-info" markdown="1">
**提示：** 
在文件的头部使用 `part` 命令，能够将一个 Library 分割成多个 Dart 文件。
这里，我们建议应该创建 Mini Library ，而避免使用 `part` 命令。
</aside>

直接在 lib 目录下创建“主” Library 文件，lib/_&lt;package-name&gt;_.dart，
该文件导出所有的公开的 API 。
这样就可以允许使用者导入单个文件就能够获得 Library 的所有功能。

lib 目录还可能包含其他可导入的非src Library。
例如，主 Library 可能是跨平台的，但创建的独立 Library 依赖于 dart:io 或 dart:html 。
Some packages have separate libraries that are meant to be imported
with a prefix, when the main library is not.（无法确切理解含义，暂未翻译）

这里让我们来看下一个真实 Library Package 的组织结构： shelf 。
[shelf](https://github.com/dart-lang/shelf) Package 提供了一种使用 Dart 创建 Web 服务器的简便方法，
它的布局在 Dart Library Package 中是一种常用布局：

{% asset libraries/shelf.png alt="shelf root directory contains example, lib, test, and tool subdirectories" %}

主 Library 文件 `shelf.dart` 在 lib 目录下，通过 `shelf.dart` 文件导出 lib/src 目录下的若干文件：

{% prettify dart %}
export 'src/cascade.dart';
export 'src/handler.dart';
export 'src/handlers/logger.dart';
export 'src/hijack_exception.dart';
export 'src/middleware.dart';
export 'src/pipeline.dart';
export 'src/request.dart';
export 'src/response.dart';
export 'src/server.dart';
export 'src/server_handler.dart';
{% endprettify %}

在 shelf Package 中同样包含了 Mini Library：shelf_io 。
适配器用来处理来自 dart:io 的 HttpRequest 对象。

<aside class="alert alert-info" markdown="1">
**针对 Web 应用的提示：**
为了在开发时使 [dartdevc](/tools/dartdevc) 工具能够达到最佳新能，
应该将[实现文件](/tools/pub/package-layout#implementation-files)放到目录 `/lib/src` 下，
而不是 `/lib` 目录的其他地方。
另外，避免通过 <code>package:<em>package_name</em>/src/...</code> 导入文件。
</aside>


{% comment %}

## Importing library files

When importing a library file, you can use the
the `package:` directive to specify the URI of that file.

{% prettify dart %}
import 'package:utilities/utilities.dart';
{% endprettify %}

You can import a library using a relative path when
both files are inside of lib,
or when both files are outside of lib.
However, you must use `package:` when importing a file that reaches
inside, or outside, of lib.
When in doubt, use the `package:` directive; it works in all cases.

The following graphic shows how
to import `lib/foo/a.dart` from both lib and web.

{% asset libraries/import-lib-rules.png alt="lib/bar/b.dart uses a relative import; web/main.dart uses a package import" %}

<aside class="alert alert-info" markdown="1">
**Note:**
Although the lib graphic shows `lib/bar/b.dart` using a relative import
(`import '../foo/a.dart'`),
it could instead use the `package:` directive
(`import 'package:my_package/foo/a.dart'`).
</aside>

{% endcomment %}


## 导入 Library 文件

在导入 Library 文件时，使用 `package:` 命令来指定文件的 URI 。

{% prettify dart %}
import 'package:utilities/utilities.dart';
{% endprettify %}

在两个文件都在 lib 目录中，或两个文件都在 lib 目录外，
我们都可以使用相对路径的方式导入 Library 。
但是，如果两个文件不都在 lib 目录中，需要对 lib 内或者 lib 外进行查找，
那么此时必须要使用 `package:` 导入。
如果对当前使用存在疑惑，那么直接 `package:` ； `package:` 满足所有情况。

下面图片展示分别从 lib 和 web 目录中导入 `lib/foo/a.dart` 。

{% asset libraries/import-lib-rules.png alt="lib/bar/b.dart uses a relative import; web/main.dart uses a package import" %}

<aside class="alert alert-info" markdown="1">
**提示：**
虽然 lib 图片上使用相对路径 (`import '../foo/a.dart'`) 导入 `lib/bar/b.dart` ，
但是它同样能使用 `package:` 直接 (`import 'package:my_package/foo/a.dart'`) 导入 。
</aside>


{% comment %}

## Providing additional files

A well designed library package is easy to test.
We recommend that you write tests using the
[test](https://github.com/dart-lang/test) package,
placing the test code in the `test` directory at the
top of the package.

If you create any command-line tools intended for public consumption,
place those in the `bin` directory, which is public.
Enable running a tool from the command line, using
[`pub global activate`](/tools/pub/cmd/pub-global#activating-a-package).
Listing the tool in the
[`executables` section](/tools/pub/pubspec#executables)
of the pubspec allows a user to run it directly without calling
[`pub global run`](/tools/pub/cmd/pub-global#running-a-script-using-pub-global-run).

It's helpful if you include an example of how to use your library.
This goes into the `example` directory at the top of the package.

Any tools or executables that you create during development that aren't for
public use go into the `tool` directory.

Other files that are required if you publish your library to the
Pub site, such as a README and a CHANGELOG, are
described in [Publishing a package](/tools/pub/publishing).
For more information on how to organize a package directory,
see the [pub package layout conventions](/tools/pub/package-layout).

{% endcomment %}


## 提供额外文件

一个精心设计的 Library Package 很容易被测试。
我们建议使用 [test](https://github.com/dart-lang/test) Package
编写测试用例，并将测试代码放到 Package 根目录的 `test` 目录中。

如果要创建一个公用的命令行工具，应该将这些工具放到公共目录 `bin` 中。
使用 [`pub global activate`](/tools/pub/cmd/pub-global#activating-a-package) 命令行
来运行工具。
在 pubspec 的 [`executables` 部分](/tools/pub/pubspec#executables)
列出的工具允许用户直接运行它而无需调用
[`pub global run`](/tools/pub/cmd/pub-global#running-a-script-using-pub-global-run) 。

在 Library 中包含一个 example 程序演示如何使用 Library 是非常有用的。
example 程序在 Package 根目录的 `example` 目录中。

在开发过程中任何非公开的工具或可执行程序，应该放到 `tool` 文件夹。

如果要将 Library 发布到 Pub 网站还要求一些其他的文件来描述[发布的 Package](/tools/pub/publishing) ，
例如：README 和 CHANGELOG 文件。
更多关于如何组织 Package 目录的内容，参见 [Pub Package 布局约定](/tools/pub/package-layout)。


{% comment %}

## Documenting a library

You can generate API docs for your library using
the [dartdoc][] tool.
Dartdoc parses the source looking for
[documentation comments](/guides/language/effective-dart/documentation#doc-comments),
which use the `///` syntax:

{% prettify dart %}
/// The event handler responsible for updating the badge in the UI.
void updateBadge() {
  ...
}
{% endprettify %}

For an example of generated docs, see the
[shelf documentation.]({{site.pub-api}}/shelf/latest)

<aside class="alert alert-info" markdown="1">
**Note:**
To include any library-level documentation in the generated docs,
you must specify the `library` directive.
See [issue 1082.](https://github.com/dart-lang/dartdoc/issues/1082)
</aside>

{% endcomment %}


## 为 Library 制作文档

使用 [dartdoc][] 可以为 Library 生成 API 文档。
dartdoc 解析源文件去查找使用 `///` 语法标注的
[文档注释](/guides/language/effective-dart/documentation#doc-comments)：

{% prettify dart %}
/// The event handler responsible for updating the badge in the UI.
void updateBadge() {
  ...
}
{% endprettify %}

文档生成示例，参见 [shelf 文档]({{site.pub-api}}/shelf/latest)。

<aside class="alert alert-info" markdown="1">
**提示：**
在生成的文档中要包含任何 Library-Level 的文档，必须要指定 `library` 命令。
参见 [issue 1082](https://github.com/dart-lang/dartdoc/issues/1082) 。
</aside>


{% comment %}

## Distributing an open source library {#distributing-a-library}

If your library is open source,
we recommend sharing it on the [Pub site.]({{site.pub}})
To publish or update the library,
use [pub publish](/tools/pub/cmd/pub-lish),
which uploads your package and creates or updates its page.
For example, see the page for the [shelf package.]({{site.pub}}/packages/shelf)
See [Publishing a package](/tools/pub/publishing)
for details on how to prepare your package for publishing.

The pub site not only hosts your package,
but also generates and hosts your package's API reference docs.
A link to the latest generated docs is in the package's **About** box;
for example, see the shelf package's
[API docs.]({{site.pub-api}}/shelf)
Links to previous versions' docs are in the
**Versions** tab of the package's page.

To ensure that your package's API docs look good on the pub site,
follow these steps:

* Before publishing your package, run the [dartdoc][] tool
  to make sure that your docs generate successfully and look as expected.
* After publishing your package, check the **Versions** tab
  to make sure that the docs generated successfully.
* If the docs didn't generate at all,
  click **failed** in the **Versions** tab to see the dartdoc output.

{% endcomment %}


## 分发开源 Library {#distributing-a-library}

如果 Library 是开源的，
我们建议将他共享到 [Pub 网站]({{site.pub}})。
使用 [pub publish](/tools/pub/cmd/pub-lish) 来发布或者更新 Library，
该命令将会上传 Package 并创建或更新其页面。
示例参见 [shelf Package]({{site.pub}}/packages/shelf) 页面。
有关如何准备发布 Package 的详细内容，参见[发布 Package](/tools/pub/publishing)。

Pub 网站不仅仅是 Package 的主机。
Pub 网站不仅用于托管 Package ，还能够生成托管 Package 的 API 参考文档。
最新生成的文档的链接位于 Package 的 **About** 选项卡中;
示例参见 shelf Package 的 [API 文档]。
链接到以前版本的文档，位于 Package 页面的 **Versions** 选项卡中。

为了确保 Package 的 API 文档在 Pub 网站上看起来更美观，
请遵循以下步骤：

* 在发布 Package 前，请通过执行 [dartdoc][] 工具确保文档能够生成成功且符合预期。
* 在发布 Package 后，请检查 **Versions** 选项卡，确保文档生成成功。
* 如果文档没有生成，点击 **Versions** 选项卡中的 **failed** 查看 dartdoc 的输出。


{% comment %}

## Resources

Use the following resources to learn more about library packages:

* [Libraries and visibility](/guides/language/language-tour#libraries-and-visibility)
  in the [language tour](/guides/language/language-tour) covers
  using library files.
* The [package](/guides/packages) documentation is useful, particularly the
  [package layout conventions](/tools/pub/package-layout).
* [What not to commit](private-files)
  covers what should not be checked into a source code repository.
* The newer library packages under the
  [dart-lang](https://github.com/dart-lang) organization tend
  to show best practices. Consider studying these examples:
  [dart_style,](https://github.com/dart-lang/dart_style)
  [path,](https://github.com/dart-lang/path)
  [shelf,](https://github.com/dart-lang/shelf)
  [source_gen,](https://github.com/dart-lang/source_gen) and
  [test.](https://github.com/dart-lang/test)

[dartdoc]: https://github.com/dart-lang/dartdoc#dartdoc

{% endcomment %}


## 资源

通过运用以下资源来了解学习更多关于 Library Package 的内容：


* [Libraries 和可见性](/guides/language/language-tour#libraries-and-visibility)
  在 [语言概览](/guides/language/language-tour) 中涵盖了 Library 文件使用的内容。
* [Package](/guides/packages) 文档非常有用，尤其是 particularly the
  [Package 布局约定](/tools/pub/package-layout).
* [什么不应该被提交](private-files)包含了关于什么文件不应该被提交到源码仓库的介绍。
* [dart-lang](https://github.com/dart-lang) 组织下的最新 Library Package
  常常是最佳实践的提现。可以参考学些以下这些实例：
  [dart_style](https://github.com/dart-lang/dart_style)，
  [path](https://github.com/dart-lang/path)，
  [shelf](https://github.com/dart-lang/shelf)，
  [source_gen](https://github.com/dart-lang/source_gen) 以及
  [test](https://github.com/dart-lang/test) 。

[dartdoc]: https://github.com/dart-lang/dartdoc#dartdoc
