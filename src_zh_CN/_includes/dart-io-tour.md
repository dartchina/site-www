{% comment %}

<?code-excerpt plaster="none"?>

The [dart:io][] library provides APIs to deal with
files, directories, processes, sockets, WebSockets, and HTTP
clients and servers.

<div class="alert alert-warning" markdown="1">
  **Important:**
  Only [Flutter mobile apps,]({{site.flutter}}) command-line scripts, and servers
  can import and use `dart:io`, not web apps.
</div>

In general, the dart:io library implements and promotes an asynchronous
API. Synchronous methods can easily block an application, making it
difficult to scale. Therefore, most operations return results via Future
or Stream objects, a pattern common with modern server platforms such as
Node.js.

The few synchronous methods in the dart:io library are clearly marked
with a Sync suffix on the method name. Synchronous methods aren't covered here.

To use the dart:io library you must import it:
<?code-excerpt "misc/test/library_tour/io_test.dart (import)"?>
{% prettify dart %}
import 'dart:io';
{% endprettify %}

{% endcomment %}


<?code-excerpt plaster="none"?>

[dart:io][] 库提供处理文件，目录，进程，套接字， WebSocket ，以及 HTTP 客户端和服务端
的 API 。


<div class="alert alert-warning" markdown="1">
  **重要：**
  `dart:io` 只能被 [Flutter 移动应用]({{site.flutter}})，命令行脚本，以及服务端应用引入和使用，
  Web 应用无法使用。
</div>

通常，dart:io 库提供的 API 为异步调用方法。同步方法常常会导致应用阻塞，且难以扩展。
因此，大多数操作的返回值为 Future 或 Stream 对象，
此模式与 Node.js 等现代服务器平台的模式相同。

dart:io 库中包含少量的同步方法，这些方法名后会明确标有 Sync 后缀。本节内容不涉及同步方法。

使用 dart:io 库前必须导入：
<?code-excerpt "misc/test/library_tour/io_test.dart (import)"?>
{% prettify dart %}
import 'dart:io';
{% endprettify %}


{% comment %}

### Files and directories

The I/O library enables command-line apps to read and write files and
browse directories. You have two choices for reading the contents of a
file: all at once, or streaming. Reading a file all at once requires
enough memory to store all the contents of the file. If the file is very
large or you want to process it while reading it, you should use a
Stream, as described in
[Streaming file contents](#streaming-file-contents).

{% endcomment %}


### 文件和目录

命令行应用程序通过 I/O 库读取和写入文件以及浏览目录。
这里有两种读取文件内容的方式：一次性读取或使用 Stream 方式操作。
一次文件读取需要足够的内存来存储要读取文件的全部内容。
如果文件非常大或者在读取文件时想对其进行一些其他处理，
此时应该使用 Stream 方式，使用方式介绍见[流式文件操作](#streaming-file-contents)。


#### 以文本方式读取文件

读取 UTF-8 编码的文本文件时，可以使用 `readAsString()` 读取整个文件内容，
使用 `readAsLines()` 按行读取。
以上两种读取方式都会返回一个 Future 对象， 文件内容通过Future 对象以一个或多个字符串的方式提供。

<?code-excerpt "misc/test/library_tour/io_test.dart (readAsString)" replace="/\btest_data\///g"?>
{% prettify dart %}
Future main() async {
  var config = File('config.txt');
  var contents;

  // 将整个文件内容读取到一个字符串中。
  contents = await config.readAsString();
  print('The file is ${contents.length} characters long.');

  // 将整个文件内容按行读取。
  contents = await config.readAsLines();
  print('The file is ${contents.length} lines long.');
}
{% endprettify %}


{% comment %}

#### Reading a file as binary

The following code reads an entire file as bytes into a list of ints.
The call to `readAsBytes()` returns a Future, which provides the result
when it’s available.

<?code-excerpt "misc/test/library_tour/io_test.dart (readAsBytes)" replace="/\btest_data\///g"?>
{% prettify dart %}
Future main() async {
  var config = File('config.txt');

  var contents = await config.readAsBytes();
  print('The file is ${contents.length} bytes long.');
}
{% endprettify %}

{% endcomment %}


#### 以库的方式读取文件

以下代码将整个文件按字节读取到整数 List 中。
`readAsBytes()` 函数返回一个 Future 对象，
当 Future 对象有效时，
由 Future 对象提供读取内容。

<?code-excerpt "misc/test/library_tour/io_test.dart (readAsBytes)" replace="/\btest_data\///g"?>
{% prettify dart %}
Future main() async {
  var config = File('config.txt');

  var contents = await config.readAsBytes();
  print('The file is ${contents.length} bytes long.');
}
{% endprettify %}


{% comment %}

#### Handling errors

To capture errors so they don't result in uncaught exceptions, you can
register a `catchError` handler on the Future,
or (in an async function) use try-catch:

<?code-excerpt "misc/test/library_tour/io_test.dart (try-catch)" replace="/does-not-exist/config/g"?>
{% prettify dart %}
Future main() async {
  var config = File('config.txt');
  try {
    var contents = await config.readAsString();
    print(contents);
  } catch (e) {
    print(e);
  }
}
{% endprettify %}

{% endcomment %}


#### 错误处理

为了防止产生未捕获异常，应该对错误进行捕获。
错误捕获可以通过对 Future 注册 `catchError` 处理函数，
或者（在异步方法中）使用 Try-Catch 进行处理。

<?code-excerpt "misc/test/library_tour/io_test.dart (try-catch)" replace="/does-not-exist/config/g"?>
{% prettify dart %}
Future main() async {
  var config = File('config.txt');
  try {
    var contents = await config.readAsString();
    print(contents);
  } catch (e) {
    print(e);
  }
}
{% endprettify %}

{% comment %}

#### Streaming file contents

Use a Stream to read a file, a little at a time.
You can use either the [Stream API](/guides/libraries/library-tour#stream)
or `await for`, part of Dart's
[asynchrony support.](/guides/language/language-tour#asynchrony-support)

<?code-excerpt "misc/test/library_tour/io_test.dart (read-from-stream)" replace="/_?test_\w*\/?//g"?>
{% prettify dart %}
import 'dart:io';
import 'dart:convert';

Future main() async {
  var config = File('config.txt');
  Stream<List<int>> inputStream = config.openRead();

  var lines = inputStream
      .transform(utf8.decoder)
      .transform(LineSplitter());
  try {
    await for (var line in lines) {
      print('Got ${line.length} characters from stream');
    }
    print('file is now closed');
  } catch (e) {
    print(e);
  }
}
{% endprettify %}

{% endcomment %}


#### 流式文件操作

使用 Stream 一次读取一个文件，可以每次只读取文件的一小部分。
操作可以使用 [Stream API](/guides/libraries/library-tour#stream) 
或 `await for` ，这些异步操作包含在 Dart [异步支持中](/guides/language/language-tour#asynchrony-support)。

<?code-excerpt "misc/test/library_tour/io_test.dart (read-from-stream)" replace="/_?test_\w*\/?//g"?>
{% prettify dart %}
import 'dart:io';
import 'dart:convert';

Future main() async {
  var config = File('config.txt');
  Stream<List<int>> inputStream = config.openRead();

  var lines = inputStream
      .transform(utf8.decoder)
      .transform(LineSplitter());
  try {
    await for (var line in lines) {
      print('Got ${line.length} characters from stream');
    }
    print('file is now closed');
  } catch (e) {
    print(e);
  }
}
{% endprettify %}


{% comment %}

#### Writing file contents

You can use an [IOSink][] to
write data to a file. Use the File `openWrite()` method to get an IOSink
that you can write to. The default mode, `FileMode.write`, completely
overwrites existing data in the file.

<?code-excerpt "misc/test/library_tour/io_test.dart (write-file)" replace="/\btest_data\///g"?>
{% prettify dart %}
var logFile = File('log.txt');
var sink = logFile.openWrite();
sink.write('FILE ACCESSED ${DateTime.now()}\n');
await sink.flush();
await sink.close();
{% endprettify %}

To add to the end of the file, use the optional `mode` parameter to
specify `FileMode.append`:

<?code-excerpt "misc/test/library_tour/io_test.dart (append)" replace="/_?test_\w*\/?//g"?>
{% prettify dart %}
var sink = logFile.openWrite(mode: FileMode.append);
{% endprettify %}

To write binary data, use `add(List<int> data)`.

{% endcomment %}


#### 写入文件内容

文件数据的写入使用 [IOSink][] 对象。 [IOSink][] 对象可以通过 File 对象的 `openWrite()` 获取，
获取 IOSink][] 后即可通过它想文件写入数据。
文件写入的默认模式为 `FileMode.write` ，写入数据将完全覆盖文件现有内容。

<?code-excerpt "misc/test/library_tour/io_test.dart (write-file)" replace="/\btest_data\///g"?>
{% prettify dart %}
var logFile = File('log.txt');
var sink = logFile.openWrite();
sink.write('FILE ACCESSED ${DateTime.now()}\n');
await sink.flush();
await sink.close();
{% endprettify %}

要在文件末尾追加内容，需要指定 `openWrite()` 的可选参数 `mode` 为 `FileMode.append` 模式：

<?code-excerpt "misc/test/library_tour/io_test.dart (append)" replace="/_?test_\w*\/?//g"?>
{% prettify dart %}
var sink = logFile.openWrite(mode: FileMode.append);
{% endprettify %}

使用 `add(List<int> data)` 方法为文件写入二进制数据。


{% comment %}

#### Listing files in a directory

Finding all files and subdirectories for a directory is an asynchronous
operation. The `list()` method returns a Stream that emits an object
when a file or directory is encountered.

<?code-excerpt "misc/test/library_tour/io_test.dart (list-dir)" replace="/\btest_data\b/tmp/g"?>
{% prettify dart %}
Future main() async {
  var dir = Directory('tmp');

  try {
    var dirList = dir.list();
    await for (FileSystemEntity f in dirList) {
      if (f is File) {
        print('Found file ${f.path}');
      } else if (f is Directory) {
        print('Found dir ${f.path}');
      }
    }
  } catch (e) {
    print(e.toString());
  }
}
{% endprettify %}

{% endcomment %}


#### 获取目录中的文件列表

查找目录的所有文件和子目录是一个异步操作。`list()` 返回一个 Stream 对象。
当异步检索到一个文件或目录时，会得到一个文件或目录的实体对象（FileSystemEntity）。

<?code-excerpt "misc/test/library_tour/io_test.dart (list-dir)" replace="/\btest_data\b/tmp/g"?>
{% prettify dart %}
Future main() async {
  var dir = Directory('tmp');

  try {
    var dirList = dir.list();
    await for (FileSystemEntity f in dirList) {
      if (f is File) {
        print('Found file ${f.path}');
      } else if (f is Directory) {
        print('Found dir ${f.path}');
      }
    }
  } catch (e) {
    print(e.toString());
  }
}
{% endprettify %}


{% comment %}

#### Other common functionality

The File and Directory classes contain other functionality, including
but not limited to:

-   Creating a file or directory: `create()` in File and Directory
-   Deleting a file or directory: `delete()` in File and Directory
-   Getting the length of a file: `length()` in File
-   Getting random access to a file: `open()` in File

Refer to the API docs for [File][] and [Directory][] for a full
list of methods.

{% endcomment %}


#### 其他公共方法

File 和 Directory 类中包含的其他方法，方法包括但不限于以下内容：

-   在 File 和 Directory 中使用 `create()` 方法创建一个文件或目录
-   在 File 和 Directory 中使用 `delete()` 方法删除一个文件或目录
-   在 File 中使用 `length()` 方法获取一个文件的长度。
-   在 File 中使用 `open()` 方法随机访问一个文件。

全部方法列表参考 [File][] 和 [Directory][] API 文档。


{% comment %}

### HTTP clients and servers

The dart:io library provides classes that command-line apps can use for
accessing HTTP resources, as well as running HTTP servers.

{% endcomment %}


### HTTP 客户端和服务端

dart:io 库提供 HTTP 相关的类，基于这些类命令行应用可以访问 HTTP 资源及运行 HTTP 服务。


{% comment %}

#### HTTP server

The [HttpServer][] class
provides the low-level functionality for building web servers. You can
match request handlers, set headers, stream data, and more.

The following sample web server returns simple text information.
This server listens on port 8888 and address 127.0.0.1 (localhost),
responding to requests for the path `/dart`. For any other path,
the response is status code 404 (page not found).

<?code-excerpt "misc/lib/library_tour/io/http_server.dart" replace="/\b_//g"?>
{% prettify dart %}
Future main() async {
  final requests = await HttpServer.bind('localhost', 8888);
  await for (var request in requests) {
    processRequest(request);
  }
}

void processRequest(HttpRequest request) {
  print('Got request for ${request.uri.path}');
  final response = request.response;
  if (request.uri.path == '/dart') {
    response
      ..headers.contentType = ContentType(
        'text',
        'plain',
      )
      ..write('Hello from the server');
  } else {
    response.statusCode = HttpStatus.notFound;
  }
  response.close();
}
{% endprettify %}

{% endcomment %}


#### HTTP 服务

[HttpServer][] 类提供用于构建 Web 服务的底层方法。 
该类用于匹配请求处理程序，设置 Header ，Stream 数据等。

下面 Web 服务示例返回简单文本信息。
服务侦听端口 8888 和地址 127.0.0.1（localhost），响应 `/dart` 路径的请求。
对于任何其他路径，响应状态码 404（找不到页面）。

<?code-excerpt "misc/lib/library_tour/io/http_server.dart" replace="/\b_//g"?>
{% prettify dart %}
Future main() async {
  final requests = await HttpServer.bind('localhost', 8888);
  await for (var request in requests) {
    processRequest(request);
  }
}

void processRequest(HttpRequest request) {
  print('Got request for ${request.uri.path}');
  final response = request.response;
  if (request.uri.path == '/dart') {
    response
      ..headers.contentType = ContentType(
        'text',
        'plain',
      )
      ..write('Hello from the server');
  } else {
    response.statusCode = HttpStatus.notFound;
  }
  response.close();
}
{% endprettify %}


{% comment %}

#### HTTP client

The [HttpClient][] class
helps you connect to HTTP resources from your Dart command-line or
server-side application. You can set headers, use HTTP methods, and read
and write data. The HttpClient class does not work in browser-based
apps. When programming in the browser, use the
[dart:html HttpRequest class.][HttpRequest]
Here’s an example of using HttpClient:

<?code-excerpt "misc/test/library_tour/io_test.dart (client)"?>
{% prettify dart %}
Future main() async {
  var url = Uri.parse('http://localhost:8888/dart');
  var httpClient = HttpClient();
  var request = await httpClient.getUrl(url);
  var response = await request.close();
  var data = await response.transform(utf8.decoder).toList();
  print('Response ${response.statusCode}: $data');
  httpClient.close();
}
{% endprettify %}

{% endcomment %}


#### HTTP 客户端

通过 HttpClient 类从 Dart 命令行或服务端应用程序访问 HTTP 资源。
该类可以设置 Header ，HTTP 访问方式（GET，POST）以及读取和写入数据。
HttpClient 类无法在浏览器的应用中使用。
为浏览器编写应用时，应该使用[dart:html HttpRequest 类][HttpRequest]。
下面是 HttpClient 的使用示例：

<?code-excerpt "misc/test/library_tour/io_test.dart (client)"?>
{% prettify dart %}
Future main() async {
  var url = Uri.parse('http://localhost:8888/dart');
  var httpClient = HttpClient();
  var request = await httpClient.getUrl(url);
  var response = await request.close();
  var data = await response.transform(utf8.decoder).toList();
  print('Response ${response.statusCode}: $data');
  httpClient.close();
}
{% endprettify %}


{% comment %}

### More information

This page showed how to use the major features of the [dart:io][] library.
Besides the APIs discussed in this section, the dart:io library also
provides APIs for [processes,][Process] [sockets,][Socket] and
[web sockets.][WebSocket]
For more information about server-side and command-line app development, see the
[server-side Dart overview.](/server)

For information on other dart:* libraries, see the
[library tour.][library tour]


[library tour]: /guides/libraries/library-tour
[dart:io]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/dart-io-library.html
[Directory]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/Directory-class.html
[File]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/File-class.html
[HttpClient]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/HttpClient-class.html
[HttpRequest]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/HttpRequest-class.html
[HttpServer]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/HttpServer-class.html
[IOSink]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/IOSink-class.html
[Process]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/Process-class.html
[Socket]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/Socket-class.html
[WebSocket]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/WebSocket-class.html

{% endcomment %}


### 更多内容

本章只是介绍了 [dart:io][] 库主要功能的使用。除了本章中提到的 API 以外，dart:io 库还提供了
[进程][Process]， [套接字][Socket]，以及 [WebSocket][WebSocket] 的 API 。
有关服务端和命令行应用程序开发的更多内容，请参阅[服务端 Dart 综述](/server)。

有关其他 dart:* 库的内容，请参阅[库概览][library tour]。

[library tour]: /guides/libraries/library-tour
[dart:io]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/dart-io-library.html
[Directory]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/Directory-class.html
[File]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/File-class.html
[HttpClient]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/HttpClient-class.html
[HttpRequest]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/HttpRequest-class.html
[HttpServer]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/HttpServer-class.html
[IOSink]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/IOSink-class.html
[Process]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/Process-class.html
[Socket]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/Socket-class.html
[WebSocket]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-io/WebSocket-class.html
