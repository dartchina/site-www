{% comment %}

If you're using Debian/Ubuntu on AMD64 (64-bit Intel), you can choose one of the
following options, both of which can update the SDK automatically when new
versions are released.

{% endcomment %}

如果是在 Debian/Ubuntu 系统的 AMD64 (64-bit Intel) 机器上，可选择以下一种方式安装，
两个方式都可以在发布新版本时自动更新 SDK 。

{% comment %}

- [Install using apt-get](#install-using-apt-get)
- [使用 apt-get 安装](#%E4%BD%BF%E7%94%A8-apt-get-%E5%AE%89%E8%A3%85)
- [Install a Debian package](#install-a-debian-package)
- [安装 Debian 包](#%E5%AE%89%E8%A3%85-debian-%E5%8C%85)
- [Modify PATH for access to all Dart binaries](#modify-path-for-access-to-all-dart-binaries)
- [修改访问 Dart 库的环境变量（PATH）](#%E4%BF%AE%E6%94%B9%E8%AE%BF%E9%97%AE-dart-%E5%BA%93%E7%9A%84%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8Fpath)

{% endcomment %}

{% comment %}

#### Install using apt-get

Perform the following **one-time setup**:

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
```terminal
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_unstable.list > /etc/apt/sources.list.d/dart_unstable.list'
```
{% else %}
```terminal
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
```
{% endif %}

Then install the
**{{site.data.pkg-vers.SDK.channel}}**
release of the Dart SDK:

```terminal
$ sudo apt-get update
$ sudo apt-get install dart
```

Or, to install the
{% if site.data.pkg-vers.SDK.channel == 'dev' -%}
**stable**
{% else -%}
**dev**
{% endif -%}
release of the Dart SDK,
run the one-time setup commands followed by:

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
```terminal
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
$ sudo apt-get update
$ sudo apt-get install dart
```
{% else %}
```terminal
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_unstable.list > /etc/apt/sources.list.d/dart_unstable.list'
$ sudo apt-get update
$ sudo apt-get install dart
```
{% endif %}

{% endcomment %}

#### 使用 apt-get 安装

执行以下**一次性**设置：

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
```terminal
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_unstable.list > /etc/apt/sources.list.d/dart_unstable.list'
```
{% else %}
```terminal
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
```
{% endif %}

然后安装
{% if site.data.pkg-vers.SDK.channel == 'dev' -%}
**开发版**
{% else -%}
**稳定版**
{% endif -%}
Dart SDK ：

```terminal
$ sudo apt-get update
$ sudo apt-get install dart
```

或者，安装
{% if site.data.pkg-vers.SDK.channel == 'dev' -%}
**稳定版**
{% else -%}
**开发板**
{% endif -%}
Dart SDK ，
执行一次性设置命令：

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
```terminal
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
$ sudo apt-get update
$ sudo apt-get install dart
```
{% else %}
```terminal
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_unstable.list > /etc/apt/sources.list.d/dart_unstable.list'
$ sudo apt-get update
$ sudo apt-get install dart
```
{% endif %}


{% comment %}

#### Install a Debian package

Alternatively, download Dart SDK as Debian package in the `.deb` package format.

{:.downloads}
- [Stable channel](#){:.download-link #debian-link-stable
  data-bits="64" data-os="debian" data-tool="sdk"}
- [Dev channel](#){:.download-link #debian-link-dev
  data-bits="64" data-os="debian" data-tool="sdk"}

{% endcomment %}


#### 安装 Debian 包

以.deb包格式

另外，可以下载 Debian `.deb` 格式的 Dart SDK 安装包。

{:.downloads}
- [Stable channel](#){:.download-link #debian-link-stable
  data-bits="64" data-os="debian" data-tool="sdk"}
- [Dev channel](#){:.download-link #debian-link-dev
  data-bits="64" data-os="debian" data-tool="sdk"}


{% comment %}

#### Modify PATH for access to all Dart binaries

After installing the SDK, **add its bin directory to your PATH**. For example,
use the following command to change PATH in your active terminal session:

```terminal
$ export PATH="$PATH:/usr/lib/dart/bin"
```

To change the PATH for future terminal sessions, use a command like this:

```terminal
$ echo 'export PATH="$PATH:/usr/lib/dart/bin"' >> ~/.profile
```

{% endcomment %}


#### 修改访问 Dart 库的环境变量（PATH）

SDK 安装完成后，添加 SDK 的 bin 目录到环境变量中。例如：
使用以下命令更改当前终端会话中的环境变量：

```terminal
$ export PATH="$PATH:/usr/lib/dart/bin"
```

要更改新建终端会话的环境变量，使用命令：

```terminal
$ echo 'export PATH="$PATH:/usr/lib/dart/bin"' >> ~/.profile
```
