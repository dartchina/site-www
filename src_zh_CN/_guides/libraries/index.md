---
title: 核心库
description: 学习了解 Dart 的核心库及 API 。
toc: false
---

{% comment %}

Dart has a rich set of core libraries that provide essentials for many everyday
programming tasks such as working on collections of objects
(`dart:collection`), making calculations (`dart:math`), and encoding/decoding
data (`dart:convert`). Additional APIs are available in
[community contributed packages](/guides/libraries/useful-libraries).

The following table lists all of the Dart core libraries.
Each library works on at least one [platform](/platforms).

{% endcomment %}

Dart 拥有丰富的核心库，他们为许多日常编程任务提供支持，例如处理对象集合的 (`dart:collection`) ，
进行计算的 (`dart:math`) 以及编/解码数据的 (`dart:convert`) 。
[社区贡献的包](/guides/libraries/useful-libraries)中提供了额外的 API 。

下表列出了所有 Dart 核心库。每个库至少可以工作在其中一个[平台](/platforms)上。

{% comment %}

<div class="table-wrapper" markdown="1">
|-----------------------------------------------+-------------------------------|
| Library                                       | Supported platforms   |
|-----------------------------------------------|-------------------------------|
| [`dart:async`][dart-async]              <br> Support for asynchronous programming, with classes such as Future and Stream. | All |
| [`dart:collection`][dart-collection]    <br> Classes and utilities that supplement the collection support in `dart:core`. | All |
| [`dart:convert`][dart-convert]          <br> Encoders and decoders for converting between different data representations, including JSON and UTF-8. | All |
| [`dart:core`][dart-core]                <br> Built-in types, collections, and other core functionality for every Dart program. | All |
| [`dart:developer`][dart-developer]      <br> Interaction with developer tools such as the debugger and inspector. | JIT<br>Web (experimental, dartdevc&nbsp;only) |
| [`dart:html`][dart-html]                <br> HTML elements and other resources for web-based applications. | Web |
| [`dart:indexed_db`][dart-indexed_db]    <br> Client-side key-value store with support for indexes. | Web |
| [`dart:io`][dart-io]                    <br> File, socket, HTTP, and other I/O support for non-web applications. | JIT<br>AOT |
| [`dart:isolate`][dart-isolate]          <br> Concurrent programming using isolates: independent workers similar to threads. | JIT<br>AOT |
| [`dart:js`][dart-js]                    <br> Interoperability with JavaScript. [PENDING: obsolete? use package:js instead?] | Web |
| [`dart:js_util`][dart-js_util]          <br> Utility methods to efficiently manipulate typed JSInterop objects. | Web |
| [`dart:math`][dart-math]                <br> Mathematical constants and functions, plus a random number generator. | All
| [`dart:mirrors`][dart-mirrors]          <br> Basic reflection with support for introspection and dynamic invocation. | JIT (experimental, _not_&nbsp;Flutter) |
| [`dart:typed_data`][dart-typed_data]    <br> Lists that efficiently handle fixed sized data (for example, unsigned 8-byte integers) and SIMD numeric types. | All |
| [`dart:web_audio`][dart-web_audio]      <br> High-fidelity audio programming in the browser. | Web |
| [`dart:web_gl`][dart-web_gl]            <br> 3D programming in the browser. | Web 
| [`dart:web_sql`][dart-web_sql]          <br> API for storing data in the browser that can be queried with SQL. | Web (obsolete) |
{:.table .table-striped}
</div>

{% endcomment %}


<div class="table-wrapper" markdown="1">
|-----------------------------------------------+-------------------------------|
| 库                                       | 支持平台   |
|-----------------------------------------------|-------------------------------|
| [`dart:async`][dart-async]              <br> 异步编程支持，比如 Future 和 Stream 类。 | 全部 |
| [`dart:collection`][dart-collection]    <br> `dart:core` 中提供了集合扩展的类和工具。 | 全部 |
| [`dart:convert`][dart-convert]          <br> 包括 JSON 和 UTF-8 在内的，不同数据表示见的编解码。 | 全部 |
| [`dart:core`][dart-core]                <br> 所有 Dart 程序所需要的内建类型，集合以及其他核心功能。 | 全部 |
| [`dart:developer`][dart-developer]      <br> 与开发人员相关工具，比如调试器和检查器。 | JIT<br>Web (实验性的，仅用于 dartdevc) |
| [`dart:html`][dart-html]                <br> 为基于 Web 的应用支持 HTML 元素及其他资源。 | Web |
| [`dart:indexed_db`][dart-indexed_db]    <br> 支持索引的客户端键值存储。 | Web |
| [`dart:io`][dart-io]                    <br> 对非 Web 应用程序的文件，Socket，HTTP 和其他 I/O 的支持。 | JIT<br>AOT |
| [`dart:isolate`][dart-isolate]          <br> 基于隔离的并发编程：类似于线程的独立任务。 | JIT<br>AOT |
| [`dart:js`][dart-js]                    <br> 提供与 JavaScript 的交互操作。 [PENDING: obsolete? use package:js instead?] | Web |
| [`dart:js_util`][dart-js_util]          <br> 用于高效操作 JSInterop 类型对象的工具方法。 | Web |
| [`dart:math`][dart-math]                <br> 数学常数和函数，以及随机数生成器。 | 全部 |
| [`dart:mirrors`][dart-mirrors]          <br> 基础反射用于支持内省和动态调用。 | JIT (实验性的， _不支持_&nbsp;Flutter) |
| [`dart:typed_data`][dart-typed_data]    <br> 用于高效处理固定大小数据（比如，无符号 8 为整数）以及 SIMD 数字类型数据。 | 全部 |
| [`dart:web_audio`][dart-web_audio]      <br> 基于浏览器的高保真音频编程。 | Web |
| [`dart:web_gl`][dart-web_gl]            <br> 基于浏览器的 3D 编程。 | Web 
| [`dart:web_sql`][dart-web_sql]          <br> 提供在浏览器中使用 SQL 查询存储数据的 API 。 | Web (废弃的) |
{:.table .table-striped}
</div>


[dart-async]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-async/dart-async-library.html
[dart-collection]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-collection/dart-collection-library.html
[dart-convert]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-convert/dart-convert-library.html
[dart-core]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-core/dart-core-library.html
[dart-developer]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-developer/dart-developer-library.html
[dart-math]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-math/dart-math-library.html
[dart-collection]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-collection/dart-collection-library.html
[dart-typed_data]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-typed_data/dart-typed_data-library.html
[dart-cli]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-cli/dart-cli-library.html
[dart-io]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/dart-io-library.html
[dart-isolate]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-isolate/dart-isolate-library.html
[dart-mirrors]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-mirrors/dart-mirrors-library.html
[dart-html]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/dart-html-library.html
[dart-indexed_db]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-indexed_db/dart-indexed_db-library.html
[dart-js]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-js/dart-js-library.html
[dart-js_util]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-js_util/dart-js_util-library.html
[dart-svg]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-svg/dart-svg-library.html
[dart-web_audio]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-web_audio/dart-web_audio-library.html
[dart-web_gl]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-web_gl/dart-web_gl-library.html
[dart-web_sql]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-web_sql/dart-web_sql-library.html
