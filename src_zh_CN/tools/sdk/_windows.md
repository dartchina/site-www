{% comment %}

Choose one of these options:

- [Install using Chocolatey](#install-using-chocolatey)
- [使用 Chocolatey 安装](#%E4%BD%BF%E7%94%A8-chocolatey-%E5%AE%89%E8%A3%85)
- [Install using a setup wizard](#install-using-a-setup-wizard)
- [使用设置向导安装](#%E4%BD%BF%E7%94%A8%E8%AE%BE%E7%BD%AE%E5%90%91%E5%AF%BC%E5%AE%89%E8%A3%85)

{% endcomment %}

选择以下一种方式安装：

{% comment %}

#### Install using Chocolatey

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
To use [Chocolatey][] to install a **dev** release of the Dart SDK, run this
command:

```terminal
C:\> choco install dart-sdk --pre
```

To install a **stable** release, run this command:

```terminal
C:\> choco install dart-sdk
```

To **upgrade** the dev release of the Dart SDK, run this command:
(remove the `--pre` to upgrade the stable release):

```terminal
C:\> choco upgrade dart-sdk --pre
```
{% else %}
To use [Chocolatey][] to install a **stable** release of the Dart SDK, run this
command:

```terminal
C:\> choco install dart-sdk
```

To install a **dev** release, run this command:

```terminal
C:\> choco install dart-sdk --pre
```

To **upgrade** the Dart SDK, run this command
(add `--pre` to upgrade the dev release):

```terminal
C:\> choco upgrade dart-sdk
```
{% endif %}

{% endcomment %}


#### 使用 Chocolatey 安装

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
使用 [Chocolatey][] 执行以下指令安装**开发版** Dart SDK：

```terminal
C:\> choco install dart-sdk --pre
```
执行以下指令安装**稳定版**：

```terminal
C:\> choco install dart-sdk
```

执行以下指令**升级**开发版 Dart SDK （升级稳定版移除 `--pre` 参数）：

```terminal
C:\> choco upgrade dart-sdk --pre
```
{% else %}
使用 [Chocolatey][] 执行以下指令安装**稳定版** Dart SDK：

```terminal
C:\> choco install dart-sdk
```

执行以下指令安装**开发板**：

```terminal
C:\> choco install dart-sdk --pre
```

执行以下指令**升级** Dart SDK （升级开发板添加 `--pre` 参数）：

```terminal
C:\> choco upgrade dart-sdk
```
{% endif %}


{% comment %}

#### Install using a setup wizard

Alternatively, use the community-supported
[Dart SDK installer for Windows.][Dart SDK installer for Windows]{: target="_blank"}
You can use the wizard to install **stable** or
**dev** versions of the Dart SDK.

![Windows Dart Setup Wizard][Windows installer img]{:.text-center width="250"}

{% endcomment %}


#### 使用设置向导安装

另外，你可以使用社区提供的
[ Windows 安装包][Dart SDK installer for Windows]{: target="_blank"}。
通过设置向导安装 **稳定版** 或者 **开发版** 的 Dart SDK 。

![Windows Dart Setup Wizard][Windows installer img]{:.text-center width="250"}


{% comment %}

[Chocolatey]: https://chocolatey.org
[Dart SDK installer for Windows]: http://www.gekorm.com/dart-windows
[Windows installer img]: {% asset shared/dart/installer-screenshot-no.png @path %}

{% endcomment %}


[Chocolatey]: https://chocolatey.org
[Dart SDK installer for Windows]: http://www.gekorm.com/dart-windows
[Windows installer img]: {% asset shared/dart/installer-screenshot-no.png @path %}
