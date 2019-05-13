{% comment %}

[Install homebrew](http://brew.sh/), and then run:

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
```terminal
$ brew tap dart-lang/dart
$ brew install dart --devel
```

To install a **stable channel** release,
don't use `--devel`:

```terminal
$ brew install dart
```

{% else %}
```terminal
$ brew tap dart-lang/dart
$ brew install dart
```

To install a **dev channel** release, use `--devel`:

```terminal
$ brew install dart --devel
```
{% endif %}

{% endcomment %}

[安装 homebrew](http://brew.sh/)，然后执行以下命令：

{% if site.data.pkg-vers.SDK.channel == 'dev' %}
```terminal
$ brew tap dart-lang/dart
$ brew install dart --devel
```

移除 `--devel` 参数安装**稳定版**：

```terminal
$ brew install dart
```

{% else %}
```terminal
$ brew tap dart-lang/dart
$ brew install dart
```

添加 `--devel` 参数安装**稳定版**：

```terminal
$ brew install dart --devel
```
{% endif %}


{% comment %}

### Upgrade

To upgrade when a new release of Dart is available run:

```terminal
$ brew upgrade dart
```
To install a stable channel release when a dev release is currently active,
run:

```terminal
$ brew unlink dart
$ brew install dart
```

To upgrade to a dev channel release when a stable release is
currently active, run:

```terminal
$ brew upgrade dart --devel --force
```

{% endcomment %}


### 升级

升级 Dart 到一个新的可用版本：

```terminal
$ brew upgrade dart
```
如果当前有效版本为开发版，想要安装稳定版，执行：

```terminal
$ brew unlink dart
$ brew install dart
```

如果当前有效版本为稳定版，要升级到开发版，执行：

```terminal
$ brew upgrade dart --devel --force
```

{% comment %}

### Switch release

To switch between locally installed dart releases run
`brew switch dart <version>`. Examples:

```terminal
$ brew switch dart 1.24.3
$ brew switch dart 2.1.0
```

If you aren't sure which versions of dart you have installed, then run:

```terminal
$ brew info dart
```

The command output lists the latest stable and dev versions at the top,
followed by your locally installed versions.

{% endcomment %}


### 切换版本

切换本地已安装 Dart 版本，执行 `brew switch dart <version>` 。例如：

```terminal
$ brew switch dart 1.24.3
$ brew switch dart 2.1.0
```

如果无法确定本地已安装了哪些版本，可执行：

```terminal
$ brew info dart
```

该指令在顶部会打印最新的稳定版和开发版，随后会列出本地已安装的版本。
