---
layout: default
title: "Dart 测试"
description: "如何测试 Flutter, Web, 以及 VM 应用。"
---


{% comment %}
Software testing, an important part of app development, helps verify that
your app is working correctly before you release it.
This Dart testing guide outlines several types of testing, and points
you to where you can learn how to test your
[mobile]({{site.flutter}}), [web]({{site.webdev}}),
and [server-side apps and scripts](/server).

<aside class="alert alert-info" markdown="1">
**Terminology: widget vs. component**<br>
Flutter, an SDK for building apps for iOS and Android, defines its
GUI elements as _widgets_. AngularDart, a web app framework,
defines its GUI elements as _components_.
This doc uses **component** (except when explicitly discussing Flutter),
but both terms refer to the same concept.
</aside>
{% endcomment %}


软件测试是应用程序开发的重要组成部分，可帮助你在应用程序发布之前验证应用程序的正确性。
此 Dart 测试指南概述了几种类型的测试，并指出了可以学习
[移动]({{site.flutter}}), [Web]({{site.webdev}})，
以及 [服务器应用和脚本](/server) 地方。

<aside class="alert alert-info" markdown="1">
**术语 widget vs. component**<br>
用于构建 iOS 和 Android 应用的 SDK —— Flutter 定义的 GUI 元素称之为 _widgets_ 。
用于构建 Web 应用的 framework —— AngularDart 定义的 GUI 元素称之为 _components_ 。
本文中使用 **component** （除了在明确讨论 Flutter ），两个术语指的是同一种概念。
</aside>


{% comment %}
## Kinds of testing

The Dart testing docs focus on three kinds of testing, out of the
[many kinds of testing](https://en.wikipedia.org/wiki/Software_testing)
that you may be familiar with: unit, component, and end-to-end
(a form of integration testing). Testing terminology varies,
but these are the terms and concepts that you are likely to
encounter when using Dart technologies:

* _Unit_ tests focus on verifying the smallest piece of testable
  software, such as a function, method, or class. Your test suites
  should have more unit tests than other kinds of tests.

* _Component_ tests verify that a component (which
  usually consists of multiple classes) behaves as expected.
  A component test often requires the use of mock objects
  that can mimic user actions, events, perform layout,
  and instantiate child components.

* _Integration_ and _end-to-end_ tests verify the behavior of
  an entire app, or a large chunk of an app. An integration test
  generally runs on a real device or OS simulator (for mobile)
  or on a browser (for the web) and consists of two pieces:
  the app itself, and the test app that puts
  the app through its paces. An integration test often measures performance,
  so the test app generally runs on a different device or OS
  than the app being tested.
{% endcomment %}


## 测试方式

此 Dart 测试文档侧重于[多种熟知测试](https://en.wikipedia.org/wiki/Software_testing)
中的三种测试方式：单元（unit），组件（component）和端到端（end-to-end）（一种集成测试方式）。
测试术语可能各不相同，下面是你在使用 Dart 技术时会遇到的术语和概念：

* **_单元_** 测试侧重于验证最小的可测试软件，例如函数，方法或类。单元测试
  相对于其他类型的测试具有更多的测试用例。 

* **_组件_** 测试用于验证一个组件（通常来说这个组件会包含多个类）的行为是否符合预期。
  组件测试通常需要使用 mock 对象，mock 对象可以模仿用户操作，事件，执行布局以及
  实例化子组件。

* **_集成_ 和 _端到端_** 测试用于验证整个应用，或大部分应用的行为。一个集成测试
  通常会运行在真实的设备或系统模拟器（用于移动设备），或浏览器（用于Web），一个
  集成测试包含两部分：应用程序本身，以及让应用执行它的流程来进行应用测试。集成测试
  通常会用来测量应用性能，因此在应用程序被测试时，测试的应用程序通常会运行在不同
  的设备或操作系统上。


{% comment %}
## Generally useful libraries

Although your tests partly depend on the platform your code is intended
for&mdash;Flutter, the web, or server-side, for example&mdash;the
following packages are useful across Dart platforms:

* [package:test]({{site.pub}}/packages/test)<br>
  Provides a standard way of writing tests in Dart. You can use the test
  package to:
    * Write single tests, or groups of tests.
    * Use the `@TestOn` annotation to restrict tests to run on
      specific environments.
    * Write asynchronous tests just as you would write synchronous
      tests.
    * Tag tests using the `@Tag` annotation. For example, define a tag to
      create a custom configuration for some tests, or to identify some tests
      as needing more time to complete.
    * Create a `dart_test.yaml` file to configure tagged tests across
      multiple files or an entire package.


* [package:mockito]({{site.pub}}/packages/mockito)<br>
  Provides a way to create
  [mock objects,](https://en.wikipedia.org/wiki/Mock_object)
  easily configured for use in fixed scenarios, and to verify
  that the system under test interacts with the mock object in
  expected ways.
  For an example that uses both package:test and package:mockito,
  see the [International Space Station API library and its unit
  tests](https://github.com/dart-lang/mockito/tree/master/test/example/iss)
  in the [mockito package](https://github.com/dart-lang/mockito).
{% endcomment %}


## 通用库


虽然测试部分取决于代码所针对的平台&mdash;例如， Flutter ，Web 或服务器端&mdash;
但是以下的 package 适用于所有的 Dart 平台：

* [package:test]({{site.pub}}/packages/test)<br>
  提供在 Dart 中编写标准的测试用例。你可以使用 package 来：
    * 编写单个或一组测试。
    * 使用 `@TestOn` 注解限制测试在特定的环境中运行。
    * 像编写同步测试一样编写异步测试。
    * 使用 `@Tag` 注解进行 Tag 测试。例如，定义 Tag 为某些测试创建自定义配置，
      或表示一些测试完成需要更多的时间。
    * 创建一个`dart_test.yaml` 文件，以跨多个文件或整个包配置 Tag 测试。

* [package:mockito]({{site.pub}}/packages/mockito)<br>
  提供一种创建
  [mock 对象](https://en.wikipedia.org/wiki/Mock_object) 的方法，
  进行简单的配置即可应用在固定测试情景中，验证被测系统是否以预期方式与模拟对象进行交互。
  有关使用 package:test 和 package:mockito 的示例，请参见
  [mockito package](https://github.com/dart-lang/mockito) 中的
  [International Space Station API 库及其单元测试](https://github.com/dart-lang/mockito/tree/master/test/example/iss)。


{% comment %}
## Flutter testing

Use the following resources to learn more about testing Flutter apps:

* [Testing Flutter Apps]({{site.flutter}}/docs/testing)<br>
  How to perform unit, widget, or integration tests on a Flutter app.
* [flutter_test]({{site.flutter_api}}/flutter/flutter_test/flutter_test-library.html)<br>
  A testing library for Flutter built on top of package:test.
* [flutter_driver]({{site.flutter_api}}/flutter/flutter_driver/flutter_driver-library.html)<br>
  A testing library for testing Flutter applications on real devices and
  emulators (in a separate process).
* [flutter/examples/flutter_gallery](https://github.com/flutter/flutter/tree/master/examples/flutter_gallery)<br>
  Tests for the Flutter gallery example.
* [flutter/dev/manual_tests](https://github.com/flutter/flutter/tree/master/dev/manual_tests)<br>
  Many examples of tests in the Flutter SDK.
{% endcomment %}


## Flutter 测试

通过下面的资源了解更多关于 Flutter 应用测试的内容：

* [测试 Flutter 应用]({{site.flutter}}/docs/testing)<br>
  如何在一个 Flutter 应用程序中进行 unit ， widget ，以及集成测试。
* [flutter_test]({{site.flutter_api}}/flutter/flutter_test/flutter_test-library.html)<br>
  基于 package:test 之上的 Flutter 测试库。
* [flutter_driver]({{site.flutter_api}}/flutter/flutter_driver/flutter_driver-library.html)<br>
  在真机或模拟器上对 Flutter 应用程序测试的测试库（在一个独立的进程中）。
* [flutter/examples/flutter_gallery](https://github.com/flutter/flutter/tree/master/examples/flutter_gallery)<br>
  测试 Flutter gallery 的示例。
* [flutter/dev/manual_tests](https://github.com/flutter/flutter/tree/master/dev/manual_tests)<br>
  Flutter SDK 中的许多测试示例。


{% comment %}
## Web testing

Use the following resources to learn more about testing Dart web
applications:

* [Testing]({{site.webdev}}/angular/guide/testing)(a page
  in the AngularDart guide)<br>
  How to use the [angular_test]({{site.pub}}/packages/angular_test)
  package to test AngularDart components and subsystems.
  <!-- More pages are coming! -->
* [package:webdriver]({{site.pub}}/packages/webdriver)<br>
  A Dart package for interfacing with
  [WebDriver](https://www.w3.org/TR/webdriver/) servers.
{% endcomment %}


## Web 测试

通过下面的资源了解更多关于 Dart web 应用测试的内容：

* [Testing]({{site.webdev}}/angular/guide/testing)（ AngularDart 指南中的一个页面）<br>
  如何使用 [angular_test]({{site.pub}}/packages/angular_test)
  package 来测试 AngularDart component 以及其系统。
  <!-- More pages are coming! -->
* [package:webdriver]({{site.pub}}/packages/webdriver)<br>
  一个用于连接 [WebDriver](https://www.w3.org/TR/webdriver/) 服务的 Dart package 。


{% comment %}
## Other tools and resources

You may also find the following resources useful for developing and
debugging Dart applications.
{% endcomment %}


## 其它工具及资源

你还可以找到以下用于开发和调试 Dart 应用程序的资源。


{% comment %}
### IDE

When it comes to debugging, your first line of defense is your IDE.
Dart plugins exist for many commonly used IDEs.

If you don't have a preferred IDE, try
[WebStorm]({{site.webdev}}/tools/webstorm) for web apps, or
[IntelliJ](/tools/jetbrains-plugin) for Flutter.
The JetBrains products have a full-featured Dart debugger, and WebStorm and
IntelliJ Ultimate include additional built-in support for running test suites.
{% endcomment %}


### IDE

在调试方面，第一个要解决的问题就是 IDE 。许多常用的IDE都有 Dart 插件。

如果没有一个首选的 IDE ，请尝试
[WebStorm]({{site.webdev}}/tools/webstorm) 用来开发 Web 应用，或
[IntelliJ](/tools/jetbrains-plugin)
用来开发 Flutter 。
JetBrains 具有全功能的 Dart 调试器， WebStorm 和 IntelliJ Ultimate 内置了支持
运行测试的套件。


{% comment %}
### Observatory

Observatory is a browser-based tool for profiling and debugging your
Dart applications. You can learn more using the following resources:

* [Observatory: A Profiler for Dart
  Apps](https://dart-lang.github.io/observatory/)
* [Dart
  Observatory]({{site.flutter}}/testing/debugging#dart-observatory-statement-level-single-stepping-debugger-and-profiler),
  a section in [Debugging Flutter Apps]({{site.flutter}}/testing//debugging)
* [Dart VM
  Observatory]({{site.group}}/forum/#!forum/observatory-discuss)
  discussion group
{% endcomment %}


### Observatory

Observatory 是一个基于浏览器的 Dart 应用程序分析和调试工具。通过下面资源了解更多内容：

* [Observatory: Dart 应用程序分析工具](https://dart-lang.github.io/observatory/)
* [Dart
  Observatory]({{site.flutter}}/testing/debugging#dart-observatory-statement-level-single-stepping-debugger-and-profiler)，
  [Flutter 应用程序调试]({{site.flutter}}/debugging/) 中的一节内容
* [Dart VM
  Observatory]({{site.group}}/forum/#!forum/observatory-discuss)
  讨论组


{% comment %}
### Continuous integration

Consider using continuous integration (CI) to build your project
and run its tests after every commit. Two CI services for GitHub are
[Travis CI](https://travis-ci.org/) (for OS X and Unix) and
[AppVeyor](https://www.appveyor.com/) (for Windows).

Travis has built-in support for Dart projects.
Learn more at the following links:

* [Building a Dart Project](https://docs.travis-ci.com/user/languages/dart)
  covers how to configure Travis for Dart projects
* The [shelf](https://github.com/dart-lang/shelf/blob/master/.travis.yml)
  example uses the `dart_task` tag (in `.travis.yml`) to configure
  the build.
{% endcomment %}


### 持续集成

考虑使用持续集成（CI）来构建项目并在每次提交后执行测试。
针对 GitHub 的有两个 CI 服务：
[Travis CI](https://travis-ci.org/) (用于 OS X 和 Unix) 以及
[AppVeyor](https://www.appveyor.com/) (用于 Windows)。

Travis 内建支持 Dart 项目。
通过下面链接了解更多内容：

* [构建一个 Dart 项目](https://docs.travis-ci.com/user/languages/dart)
  涵盖了如何为 Dart 项目配置 Travis 。
* [shelf](https://github.com/dart-lang/shelf/blob/master/.travis.yml)
  使用 `dart_task` Tag（在 `.travis.yml` 文件中）配置构建的示例。
