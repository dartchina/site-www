{% comment %}

Use the [dart:html][] library to
program the browser, manipulate objects and elements in the DOM, and
access HTML5 APIs. DOM stands for *Document Object Model*, which
describes the hierarchy of an HTML page.

Other common uses of dart:html are manipulating styles (*CSS*), getting
data using HTTP requests, and exchanging data using
[WebSockets](#sending-and-receiving-real-time-data-with-websockets).
HTML5 (and dart:html) has many
additional APIs that this section doesn’t cover. Only web apps can use
dart:html, not command-line apps.

<div class="alert alert-info" markdown="1">
**Note:**
For a higher level approach to web app UIs, use a web framework such as
[AngularDart.]({{site.angulardart}})
</div>

To use the HTML library in your web app, import dart:html:

{% comment %}
TODO: Figure out why we get ERRORs when using code-excerpt with triple ticks.
Workaround: use prettify dart (with liquid syntax,
surrounded with braces and percent marks).

TODO: Consider helping users run these examples in DartPad.
{% endcomment %}

{% comment %} code-excerpt "lib/html.dart (import)" {% endcomment %}
```dart
import 'dart:html';
```

{% endcomment %}

在浏览器上使用 [dart:html][] 库编程，操作 DOM 中的对象和元素，以及访问 HTML5 API 。
DOM 全称为 **Document Object Model** ，用来描述 HTML 页面的层次结构。

[dart:html][] 的其他常见用途是操作样式（*CSS*），获取 HTTP 请求数据，以及使用
[WebSockets](#sending-and-receiving-real-time-data-with-websockets) 交换数据。
HTML5（和 dart:html）有许多其他 API 本章节无法全部涵盖，本节未涵盖这些API。 dart:html 只能
被用于 Web 应用，命令行应用无法使用。

<div class="alert alert-info" markdown="1">
**提示：**
对于 Web 应用 UI 的高级处理方式，可以使用 Web 框架，例如：
[AngularDart.]({{site.angulardart}})
</div>

在 Web 应用中使用 HTML 库，导入 dart:html ：

{% comment %}
TODO: Figure out why we get ERRORs when using code-excerpt with triple ticks.
Workaround: use prettify dart (with liquid syntax,
surrounded with braces and percent marks).

TODO: Consider helping users run these examples in DartPad.
{% endcomment %}

{% comment %} code-excerpt "lib/html.dart (import)" {% endcomment %}
```dart
import 'dart:html';
```

{% comment %}

### Manipulating the DOM

To use the DOM, you need to know about *windows*, *documents*,
*elements*, and *nodes*.

A [Window][] object represents
the actual window of the web browser. Each Window has a Document object,
which points to the document that's currently loaded. The Window object
also has accessors to various APIs such as IndexedDB (for storing data),
requestAnimationFrame (for animations), and more. In tabbed browsers,
each tab has its own Window object.

With the [Document][] object, you can create and manipulate [Element][] objects
within the document. Note that the document itself is an element and can be
manipulated.

The DOM models a tree of
[Nodes.][Nodes] These nodes are often
elements, but they can also be attributes, text, comments, and other DOM
types. Except for the root node, which has no parent, each node in the
DOM has one parent and might have many children.

{% endcomment %}


### DOM 操作

在操作 DOM 前，需要对 *windows*， *documents*,
*elements*， 以及 *nodes* 有所了解。

[Window][] 对象表示 Web 浏览器的实际窗口。
每个 Window 都有一个 Document 对象，该对象指向当前加载的文档。
Window 对象还包括各种 API 的访问器，例如 IndexedDB（用于存储数据），
requestAnimationFrame（用于动画）等。
在选项卡式浏览器中，每个选项卡都有自己的 Window 对象。

使用 [Document][] 对象，可以在文档中创建和操作 [Element][] 对象。
需要注意的是，文档本身也是一个元素，可以被操作。

DOM 模拟一棵树的[结点][Nodes]。这些节点通常是元素，
但也可以是属性，文本，注释和其他 DOM 类型。
除了根节点（该节点没有父节点）之外，
DOM 中的每个节点都有一个父节点，且可能有许多子节点。


{% comment %}

#### Finding elements

To manipulate an element, you first need an object that represents it.
You can get this object using a query.

Find one or more elements using the top-level functions
`querySelector()` and `querySelectorAll()`. You can query by ID, class, tag, name, or
any combination of these. The [CSS Selector Specification
guide](http://www.w3.org/TR/css3-selectors/) defines the formats of the
selectors such as using a \# prefix to specify IDs and a period (.) for
classes.

The `querySelector()` function returns the first element that matches
the selector, while `querySelectorAll()`returns a collection of elements
that match the selector.

{% comment %}code-excerpt "lib/html.dart (querySelector)"{% endcomment %}
```dart
  // Find an element by id (an-id).
  Element elem1 = querySelector('#an-id');

  // Find an element by class (a-class).
  Element elem2 = querySelector('.a-class');

  // Find all elements by tag (<div>).
  List<Element> elems1 = querySelectorAll('div');

  // Find all text inputs.
  List<Element> elems2 = querySelectorAll(
    'input[type="text"]',
  );

  // Find all elements with the CSS class 'class'
  // inside of a <p> that is inside an element with
  // the ID 'id'.
  List<Element> elems3 = querySelectorAll('#id p.class');
```

{% endcomment %}


#### 查找元素

在操作元素钱，首先需要一个能够表示它的对象。
我们可以通过查找获取这个对象。

查找一个或多个元素可以使用顶级函数 `querySelector()` 和 `querySelectorAll()` 。
我们可以按ID，类，标签，名称或这些的任意组合进行查询。
[CSS 选择器规范指南](http://www.w3.org/TR/css3-selectors/)
定义了选择器的格式，例如使用 \# 前缀指定 ID 和点 (.) 前缀指定类。

`querySelector()` 函数返回与选择器匹配的第一个元素，
而 `querySelectorAll()` 返回与选择器匹配的元素集合。


{% comment %}code-excerpt "lib/html.dart (querySelector)"{% endcomment %}
```dart
  // Find an element by id (an-id).
  Element elem1 = querySelector('#an-id');

  // Find an element by class (a-class).
  Element elem2 = querySelector('.a-class');

  // Find all elements by tag (<div>).
  List<Element> elems1 = querySelectorAll('div');

  // Find all text inputs.
  List<Element> elems2 = querySelectorAll(
    'input[type="text"]',
  );

  // Find all elements with the CSS class 'class'
  // inside of a <p> that is inside an element with
  // the ID 'id'.
  List<Element> elems3 = querySelectorAll('#id p.class');
```


{% comment %}

#### Manipulating elements

You can use properties to change the state of an element. Node and its
subtype Element define the properties that all elements have. For
example, all elements have `classes`, `hidden`, `id`, `style`, and
`title` properties that you can use to set state. Subclasses of Element
define additional properties, such as the `href` property of
[AnchorElement.][AnchorElement]

Consider this example of specifying an anchor element in HTML:

{% comment %}code-excerpt "test/html_test.dart (anchor-html)" replace="/.*'(.*?)'.*/$1/g"{% endcomment %}
```html
<a id="example" href="http://example.com">link text</a>
```

This \<a\> tag specifies an element with an `href` attribute and a text
node (accessible via a `text` property) that contains the string
“linktext”. To change the URL that the link goes to, you can use
AnchorElement’s `href` property:

{% comment %}code-excerpt "test/html_test.dart (href)"{% endcomment %}
```dart
var anchor = querySelector('#example') as AnchorElement;
anchor.href = 'http://dartlang.org';
```

Often you need to set properties on multiple elements. For example, the
following code sets the `hidden` property of all elements that have a
class of “mac”, “win”, or “linux”. Setting the `hidden` property to true
has the same effect as adding `display:none` to the CSS.

{% comment %}code-excerpt "test/html_test.dart (os-html)" replace="/.*? = '''|''';$//g"{% endcomment %}
```dart
  <!-- In HTML: -->
  <p>
    <span class="linux">Words for Linux</span>
    <span class="macos">Words for Mac</span>
    <span class="windows">Words for Windows</span>
  </p>
```

{% comment %}code-excerpt "test/html_test.dart (os)"{% endcomment %}
```dart
  // In Dart:
  final osList = ['macos', 'windows', 'linux'];
  final userOs = determineUserOs();

  // For each possible OS...
  for (var os in osList) {
    // Matches user OS?
    bool shouldShow = (os == userOs);

    // Find all elements with class=os. For example, if
    // os == 'windows', call querySelectorAll('.windows')
    // to find all elements with the class "windows".
    // Note that '.$os' uses string interpolation.
    for (var elem in querySelectorAll('.$os')) {
      elem.hidden = !shouldShow; // Show or hide.
    }
  }
```

When the right property isn’t available or convenient, you can use
Element’s `attributes` property. This property is a
`Map<String, String>`, where the keys are attribute names. For a list of
attribute names and their meanings, see the [MDN Attributes
page.](https://developer.mozilla.org/en/HTML/Attributes) Here’s an
example of setting an attribute’s value:

{% comment %}code-excerpt "lib/html.dart (attributes)"{% endcomment %}
```dart
  elem.attributes['someAttribute'] = 'someValue';
```

{% endcomment %}


#### 操作元素

元素的状态可以通过属性来修改。节点和它的子元素定义所有元素具有的属性。
例如，所有元素都具有可用于设置的 `classes` ， `hidden` ， `id` ， `style` 以及
`title` 属性。子元素定义一些附加的属性，例如 [AnchorElement.][AnchorElement] 的 `href` 属性。

思考下面示例 - 在 HTML 中指定锚元素：

{% comment %}code-excerpt "test/html_test.dart (anchor-html)" replace="/.*'(.*?)'.*/$1/g"{% endcomment %}
```html
<a id="example" href="http://example.com">link text</a>
```

这个 \<a\> 标签指定具有 `href` 属性的元素并包含字符串 “linktext” 的文本节点（可通过 `text` 属性访问）。
这里可以使用 AnchorElement 的 `href` 属性来修改链接转到的 URL ：

{% comment %}code-excerpt "test/html_test.dart (href)"{% endcomment %}
```dart
var anchor = querySelector('#example') as AnchorElement;
anchor.href = 'http://dartlang.org';
```

我们常常需要设置多个元素的属性。
例如，以下代码中 “mac”, “win”, 或 “linux” 这些类的元素集合中都包含 `hidden` 属性。
将 `hidden` 属性设置为 true 和将 `display:none` 添加到 CSS 具有相同的效果。


{% comment %}code-excerpt "test/html_test.dart (os-html)" replace="/.*? = '''|''';$//g"{% endcomment %}
```dart
  <!-- In HTML: -->
  <p>
    <span class="linux">Words for Linux</span>
    <span class="macos">Words for Mac</span>
    <span class="windows">Words for Windows</span>
  </p>
```

{% comment %}code-excerpt "test/html_test.dart (os)"{% endcomment %}
```dart
  // In Dart:
  final osList = ['macos', 'windows', 'linux'];
  final userOs = determineUserOs();

  // For each possible OS...
  for (var os in osList) {
    // Matches user OS?
    bool shouldShow = (os == userOs);

    // Find all elements with class=os. For example, if
    // os == 'windows', call querySelectorAll('.windows')
    // to find all elements with the class "windows".
    // Note that '.$os' uses string interpolation.
    for (var elem in querySelectorAll('.$os')) {
      elem.hidden = !shouldShow; // Show or hide.
    }
  }
```

当右侧属性不可用或不方便时，可以使用元素的 `attributes` 属性。
此属性是 `Map<String, String>` ，其中键是属性名称。
有关属性名称及其描述列表，请参阅
[MDN 属性页面](https://developer.mozilla.org/en/HTML/Attributes) 。
以下是设置 `attributes` 值的示例：

{% comment %}code-excerpt "lib/html.dart (attributes)"{% endcomment %}
```dart
  elem.attributes['someAttribute'] = 'someValue';
```


{% comment %}

#### Creating elements

You can add to existing HTML pages by creating new elements and
attaching them to the DOM. Here’s an example of creating a paragraph
(\<p\>) element:

{% comment %}code-excerpt "lib/html.dart (creating-elements)"{% endcomment %}
```dart
  var elem = ParagraphElement();
  elem.text = 'Creating is easy!';
```

You can also create an element by parsing HTML text. Any child elements
are also parsed and created.

{% comment %}code-excerpt "lib/html.dart (creating-from-html)"{% endcomment %}
```dart
  var elem2 = Element.html(
    '<p>Creating <em>is</em> easy!</p>',
  );
```

Note that `elem2` is a `ParagraphElement` in the preceding example.

Attach the newly created element to the document by assigning a parent
to the element. You can add an element to any existing element’s
children. In the following example, `body` is an element, and its child
elements are accessible (as a List\<Element\>) from the `children`
property.

{% comment %}code-excerpt "lib/html.dart (body-children-add)"{% endcomment %}
```dart
  document.body.children.add(elem2);
```

{% endcomment %}


#### 创建元素

在已有的 HTML 上，你可以创建元素并将它们添加到 DOM 中。
下面是一个创建段落元素 (\<p\>) 的实例：

{% comment %}code-excerpt "lib/html.dart (creating-elements)"{% endcomment %}
```dart
  var elem = ParagraphElement();
  elem.text = 'Creating is easy!';
```
同样你可以通过解析 HTML 文本来创建元素。
元素的其他的子元素也将被解析和创建。

{% comment %}code-excerpt "lib/html.dart (creating-from-html)"{% endcomment %}
```dart
  var elem2 = Element.html(
    '<p>Creating <em>is</em> easy!</p>',
  );
```

请注意， `elem2` 是前面示例中的 `ParagraphElement` 。、

你可以向任何现有元素的子元素添加元素。
在以下示例中，`body` 是一个元素，其子元素可以从 `children` 属性访问（类型为 List\<Element\>）。

{% comment %}code-excerpt "lib/html.dart (body-children-add)"{% endcomment %}
```dart
  document.body.children.add(elem2);
```

{% comment %}

#### Adding, replacing, and removing nodes

Recall that elements are just a kind of node. You can find all the
children of a node using the `nodes` property of Node, which returns a
List\<Node\> (as opposed to `children`, which omits non-Element nodes).
Once you have this list, you can use the usual List methods and
operators to manipulate the children of the node.

To add a node as the last child of its parent, use the List `add()`
method:

{% comment %}code-excerpt "lib/html.dart (nodes-add)"{% endcomment %}
```dart
  querySelector('#inputs').nodes.add(elem);
```

To replace a node, use the Node `replaceWith()` method:

{% comment %}code-excerpt "lib/html.dart (replaceWith)"{% endcomment %}
```dart
  querySelector('#status').replaceWith(elem);
```

To remove a node, use the Node `remove()` method:

{% comment %}code-excerpt "lib/html.dart (remove)"{% endcomment %}
```dart
  // Find a node by ID, and remove it from the DOM.
  querySelector('#expendable').remove();
```

{% endcomment %}


#### 增加，替换，以及移除节点

回忆一下，元素只是节点的一种。你可以使用节点的 `nodes` 属性找到该节点的所有子节点，
该属性返回 List\<Node\>（与 `children` 不同， `children` 省略了非元素节点（non-Element nodes））。
获得此列表后，可以使用常用的 List 方法和运算符来操作这些子节点。

使用 List 的 `add()` 方法，在父节点的最后一个子节点：

{% comment %}code-excerpt "lib/html.dart (nodes-add)"{% endcomment %}
```dart
  querySelector('#inputs').nodes.add(elem);
```

使用 `replaceWith()` 方法，替换一个节点：

{% comment %}code-excerpt "lib/html.dart (replaceWith)"{% endcomment %}
```dart
  querySelector('#status').replaceWith(elem);
```

使用 `remove()` 方法，移除一个节点：

{% comment %}code-excerpt "lib/html.dart (remove)"{% endcomment %}
```dart
  // Find a node by ID, and remove it from the DOM.
  querySelector('#expendable').remove();
```


{% comment %}

#### Manipulating CSS styles

CSS, or *cascading style sheets*, defines the presentation styles of DOM
elements. You can change the appearance of an element by attaching ID
and class attributes to it.

Each element has a `classes` field, which is a list. Add and remove CSS
classes simply by adding and removing strings from this collection. For
example, the following sample adds the `warning` class to an element:

{% comment %}code-excerpt "lib/html.dart (classes-add)"{% endcomment %}
```dart
  var elem = querySelector('#message');
  elem.classes.add('warning');
```

It’s often very efficient to find an element by ID. You can dynamically
set an element ID with the `id` property:

{% comment %}code-excerpt "lib/html.dart (set-id)"{% endcomment %}
```dart
  var message = DivElement();
  message.id = 'message2';
  message.text = 'Please subscribe to the Dart mailing list.';
```

You can reduce the redundant text in this example by using method
cascades:

{% comment %}code-excerpt "lib/html.dart (elem-set-cascade)"{% endcomment %}
```dart
  var message = DivElement()
    ..id = 'message2'
    ..text = 'Please subscribe to the Dart mailing list.';
```

While using IDs and classes to associate an element with a set of styles
is best practice, sometimes you want to attach a specific style directly
to the element:

{% comment %}code-excerpt "lib/html.dart (set-style)"{% endcomment %}
```dart
  message.style
    ..fontWeight = 'bold'
    ..fontSize = '3em';
```

{% endcomment %}


#### 操作 CSS 样式

CSS ，也称为*级联样式表*，用来定义 DOM 元素的显示风格。
你可以通过将 ID 和类属性附加到元素上来更改元素的外观。

每个元素都有一个 List 类型的 `classes` 字段。
只要在这个 List 中添加或删除字符串即可实现 CSS 类的添加和删除。 
例如，以下示例将 `warning` 类添加到元素中：

{% comment %}code-excerpt "lib/html.dart (classes-add)"{% endcomment %}
```dart
  var elem = querySelector('#message');
  elem.classes.add('warning');
```

通常使用 ID 查找元素是非常高效的。
使用 `id` 属性可以动态设置元素的 ID ：

{% comment %}code-excerpt "lib/html.dart (set-id)"{% endcomment %}
```dart
  var message = DivElement();
  message.id = 'message2';
  message.text = 'Please subscribe to the Dart mailing list.';
```

You can reduce the redundant text in this example by using method
cascades:

使用方法级联可以简化上述代码：

{% comment %}code-excerpt "lib/html.dart (elem-set-cascade)"{% endcomment %}
```dart
  var message = DivElement()
    ..id = 'message2'
    ..text = 'Please subscribe to the Dart mailing list.';
```

While using IDs and classes to associate an element with a set of styles
is best practice, sometimes you want to attach a specific style directly
to the element:

虽然使用 ID 和 classes 将元素与一组样式相关联是非常有效的方法，
但有时你也可以为元素直接指定特定的样式：

{% comment %}code-excerpt "lib/html.dart (set-style)"{% endcomment %}
```dart
  message.style
    ..fontWeight = 'bold'
    ..fontSize = '3em';
```


{% comment %}

#### Handling events

To respond to external events such as clicks, changes of focus, and
selections, add an event listener. You can add an event listener to any
element on the page. Event dispatch and propagation is a complicated
subject; [research the
details](http://www.w3.org/TR/DOM-Level-3-Events/#dom-event-architecture)
if you’re new to web programming.

Add an event handler using
<code><em>element</em>.on<em>Event</em>.listen(<em>function</em>)</code>,
where <code><em>Event</em></code> is the event
name and <code><em>function</em></code> is the event handler.

For example, here’s how you can handle clicks on a button:

{% comment %}code-excerpt "lib/html.dart (onClick)"{% endcomment %}
```dart
  // Find a button by ID and add an event handler.
  querySelector('#submitInfo').onClick.listen((e) {
    // When the button is clicked, it runs this code.
    submitData();
  });
```

Events can propagate up and down through the DOM tree. To discover which
element originally fired the event, use `e.target`:

{% comment %}code-excerpt "lib/html.dart (target)"{% endcomment %}
```dart
  document.body.onClick.listen((e) {
    final clickedElem = e.target;
    // ...
  });
```

To see all the events for which you can register an event listener, look
for "onEventType" properties in the API docs for [Element][] and its
subclasses. Some common events include:

-   change
-   blur
-   keyDown
-   keyUp
-   mouseDown
-   mouseUp

{% endcomment %}


#### 处理事件

通过添加事件监听来实现对外部事件的响应，例如：点击，焦点更改，选择等。
事件监听可以添加到页面的任意元素上。事件的传播和分发的原理比较复杂，
如果你的 Web 新手，[可以在这里了解更多细节](http://www.w3.org/TR/DOM-Level-3-Events/#dom-event-architecture)。

使用 <code><em>element</em>.on<em>Event</em>.listen(<em>function</em>)</code> 添加事件处理程序，
其中 <code><em>Event</em></code> 是事件名称，
<code><em>function</em></code> 是事件处理程序。

例如，下面是处理按钮点击的示例：

{% comment %}code-excerpt "lib/html.dart (onClick)"{% endcomment %}
```dart
  // Find a button by ID and add an event handler.
  querySelector('#submitInfo').onClick.listen((e) {
    // When the button is clicked, it runs this code.
    submitData();
  });
```

事件可以通过 DOM 树向上或向下传播。可以使用 `e.target` 要找到最初触发事件的元素：

{% comment %}code-excerpt "lib/html.dart (target)"{% endcomment %}
```dart
  document.body.onClick.listen((e) {
    final clickedElem = e.target;
    // ...
  });
```

要查看所有可以注册的监听器事件，可以在 [Element][] 及其子类的 API 文档中查找 "onEventType" 属性来获取事件类型。
下面是一些常见的事件：

-   change
-   blur
-   keyDown
-   keyUp
-   mouseDown
-   mouseUp


{% comment %}

### Using HTTP resources with HttpRequest

Formerly known as XMLHttpRequest, the [HttpRequest][] class
gives you access to HTTP resources from within your browser-based app.
Traditionally, AJAX-style apps make heavy use of HttpRequest. Use
HttpRequest to dynamically load JSON data or any other resource from a
web server. You can also dynamically send data to a web server.

{% endcomment %}


### 通过 HttpRequest 访问 HTTP 资源

[HttpRequest][] 之前被称为 XMLHttpRequest ，在浏览器应用中可以通过
[HttpRequest][] 来访问 HTTP 资源。
在传统的 AJAX 风格应用程序中会大量使用 HttpRequest 。
使用 HttpRequest 可以从 Web 服务器动态加载 JSON 数据以及其他资源。
也还可以将数据动态发送到 Web 服务器。


{% comment %}

#### Getting data from the server

The HttpRequest static method `getString()` is an easy way to get data
from a web server. Use `await` with the `getString()` call
to ensure that you have the data before continuing execution.

{% comment %}code-excerpt "test/html_test.dart (getString)" plaster="none" replace="/await.*;/[!$&!]/g"{% endcomment %}
```dart
  Future main() async {
    String pageHtml = [!await HttpRequest.getString(url);!]
    // Do something with pageHtml...
  }
```

Use try-catch to specify an error handler:

{% comment %}code-excerpt "lib/html.dart (try-getString)"{% endcomment %}
```dart
  try {
    var data = await HttpRequest.getString(jsonUri);
    // Process data...
  } catch (e) {
    // Handle exception...
  }
```

If you need access to the HttpRequest, not just the text data it
retrieves, you can use the `request()` static method instead of
`getString()`. Here’s an example of reading XML data:

{% comment %}code-excerpt "test/html_test.dart (request)" replace="/await.*;/[!$&!]/g"{% endcomment %}
```dart
  Future main() async {
    HttpRequest req = await HttpRequest.request(
      url,
      method: 'HEAD',
    );
    if (req.status == 200) {
      // Successful URL access...
    }
    // ···
  }
```

You can also use the full API to handle more interesting cases. For
example, you can set arbitrary headers.

The general flow for using the full API of HttpRequest is as follows:

1.  Create the HttpRequest object.
2.  Open the URL with either `GET` or `POST`.
3.  Attach event handlers.
4.  Send the request.

For example:

{% comment %}
TODO: use original source from dart-tutorials-samples/web/portmanteaux/portmanteaux.dart
{% endcomment %}

{% comment %}code-excerpt "lib/html.dart (new-HttpRequest)"{% endcomment %}
```dart
  var request = HttpRequest();
  request
    ..open('POST', url)
    ..onLoadEnd.listen((e) => requestComplete(request))
    ..send(encodedData);
```

{% endcomment %}


#### 从服务器获取数据

HttpRequest 静态方法 `getString()` 是从 Web 服务器获取数据的一种简便方法。
配合 `await` 使用，可以确保获得请求数据之后，再继续执行后续操作。

{% comment %}code-excerpt "test/html_test.dart (getString)" plaster="none" replace="/await.*;/[!$&!]/g"{% endcomment %}
```dart
  Future main() async {
    String pageHtml = [!await HttpRequest.getString(url);!]
    // Do something with pageHtml...
  }
```

使用 Try-Catch 来捕获处理错误：

{% comment %}code-excerpt "lib/html.dart (try-getString)"{% endcomment %}
```dart
  try {
    var data = await HttpRequest.getString(jsonUri);
    // Process data...
  } catch (e) {
    // Handle exception...
  }
```

HttpRequest 请求不仅仅可以通过 `getString()` 检索文本数据，
这里可以使用 `request()` 访问更丰富的 HTTP 资源。
下面是读取 XML 数据的示例：

{% comment %}code-excerpt "test/html_test.dart (request)" replace="/await.*;/[!$&!]/g"{% endcomment %}
```dart
  Future main() async {
    HttpRequest req = await HttpRequest.request(
      url,
      method: 'HEAD',
    );
    if (req.status == 200) {
      // Successful URL access...
    }
    // ···
  }
```

使用完整的 API 可以处理更复杂的情况。比如，我们可以设置任意请求头（Header） 。

一般使用 HttpRequest 完整 API 的流程如下：

1.  创建 HttpRequest 对象。
2.  使用 `GET` 或 `POST` 方式打开 URL。
3.  添加附加的事件处理程序。
4.  发送请求。

例如：

{% comment %}
TODO: use original source from dart-tutorials-samples/web/portmanteaux/portmanteaux.dart
{% endcomment %}

{% comment %}code-excerpt "lib/html.dart (new-HttpRequest)"{% endcomment %}
```dart
  var request = HttpRequest();
  request
    ..open('POST', url)
    ..onLoadEnd.listen((e) => requestComplete(request))
    ..send(encodedData);
```

{% comment %}

#### Sending data to the server

HttpRequest can send data to the server using the HTTP method POST. For
example, you might want to dynamically submit data to a form handler.
Sending JSON data to a RESTful web service is another common example.

Submitting data to a form handler requires you to provide name-value
pairs as URI-encoded strings. (Information about the URI class is in
the [URIs section][URIs] of the [Dart Library Tour.][Dart Library Tour])
You must also set the `Content-type` header to
`application/x-www-form-urlencode` if you wish to send data to a form
handler.

{% comment %}code-excerpt "test/html_test.dart (POST)"{% endcomment %}
```dart
  String encodeMap(Map data) => data.keys
      .map((k) => '${Uri.encodeComponent(k)}=${Uri.encodeComponent(data[k])}')
      .join('&');

  Future main() async {
    var data = {'dart': 'fun', 'angular': 'productive'};

    var request = HttpRequest();
    request
      ..open('POST', url)
      ..setRequestHeader(
        'Content-type',
        'application/x-www-form-urlencoded',
      )
      ..send(encodeMap(data));

    await request.onLoadEnd.first;

    if (request.status == 200) {
      // Successful URL access...
    }
    // ···
  }
```

{% endcomment %}


#### 向服务器发送数据

HttpRequest 可以通过 HTTP POST 方式将数据发送到服务器。
例如，动态的提交表单数据。另一个常见情况是将 JSON 数据发送到 RESTful Web 服务。

提交表单数据要求提供键-值对的 URI 编码字符串。
（有关 URI 类的信息位于 [Dart 概览][Dart Library Tour]的 [URIs 章节][URIs]。）
如果要将数据发送给表单处理程序，还必须将 `Content-type` Header 设置为 `application/x-www-form-urlencode` 。

{% comment %}code-excerpt "test/html_test.dart (POST)"{% endcomment %}
```dart
  String encodeMap(Map data) => data.keys
      .map((k) => '${Uri.encodeComponent(k)}=${Uri.encodeComponent(data[k])}')
      .join('&');

  Future main() async {
    var data = {'dart': 'fun', 'angular': 'productive'};

    var request = HttpRequest();
    request
      ..open('POST', url)
      ..setRequestHeader(
        'Content-type',
        'application/x-www-form-urlencoded',
      )
      ..send(encodeMap(data));

    await request.onLoadEnd.first;

    if (request.status == 200) {
      // Successful URL access...
    }
    // ···
  }
```

{% comment %}

### Sending and receiving real-time data with WebSockets

A WebSocket allows your web app to exchange data with a server
interactively—no polling necessary. A server creates the WebSocket and
listens for requests on a URL that starts with **ws://**—for example,
ws://127.0.0.1:1337/ws. The data transmitted over a WebSocket can be a
string or a blob.  Often, the data is a JSON-formatted string.

To use a WebSocket in your web app, first create a [WebSocket][] object, passing
the WebSocket URL as an argument:

{% comment %}
Code inspired by:
https://github.com/dart-lang/dart-samples/blob/master/html5/web/websockets/basics/websocket_sample.dart

Once tests are written for the samples, consider getting code excerpts from
the websocket sample app.
{% endcomment %}

{% comment %}code-excerpt "test/html_test.dart (WebSocket)"{% endcomment %}
```dart
  var ws = WebSocket('ws://echo.websocket.org');
```

{% endcomment %}


### 通过 WebSocket 发送和接收实时数据

WebSocket 允许 Web 应用程序以交互方式与服务器交换数据，且无需轮询。
服务器创建 WebSocket 并侦听以 **ws://** 开头的 URL 请求 - 例如，ws://127.0.0.1:1337/ws 。
通过 WebSocket 传输的数据可以是字符串或 blob 。通常，数据为 JSON 格式的字符串。

要在 Web 应用程序中使用 WebSocket ，
使用 WebSocket URL 作为一个参数创建一个 [WebSocket][] 对象：

{% comment %}
Code inspired by:
https://github.com/dart-lang/dart-samples/blob/master/html5/web/websockets/basics/websocket_sample.dart

Once tests are written for the samples, consider getting code excerpts from
the websocket sample app.
{% endcomment %}

{% comment %}code-excerpt "test/html_test.dart (WebSocket)"{% endcomment %}
```dart
  var ws = WebSocket('ws://echo.websocket.org');
```

{% comment %}

#### Sending data

To send string data on the WebSocket, use the `send()` method:

{% comment %}code-excerpt "test/html_test.dart (send)"{% endcomment %}
```dart
  ws.send('Hello from Dart!');
```

{% endcomment %}


#### 发送数据

使用 `send()` 方法在 WebSocket 发送字符串数据：

{% comment %}code-excerpt "test/html_test.dart (send)"{% endcomment %}
```dart
  ws.send('Hello from Dart!');
```


{% comment %}

#### Receiving data

To receive data on the WebSocket, register a listener for message
events:

{% comment %}code-excerpt "test/html_test.dart (onMessage)" plaster="none"{% endcomment %}
```dart
  ws.onMessage.listen((MessageEvent e) {
    print('Received message: ${e.data}');
  });
```

The message event handler receives a [MessageEvent][] object.
This object’s `data` field has the data from the server.

{% endcomment %}

注册监听事件，来接收 WebSocket 数据：

{% comment %}code-excerpt "test/html_test.dart (onMessage)" plaster="none"{% endcomment %}
```dart
  ws.onMessage.listen((MessageEvent e) {
    print('Received message: ${e.data}');
  });
```

消息处理时间会接收到一个 [MessageEvent][] 对象。
该对象的 `data` 字段包含来自服务器的数据。


{% comment %}

#### Handling WebSocket events

Your app can handle the following WebSocket events: open, close, error,
and (as shown earlier) message. Here’s an example of a method that
creates a WebSocket object and registers handlers for open, close,
error, and message events:

{% comment %}code-excerpt "test/html_test.dart (initWebSocket)" plaster="none"{% endcomment %}
```dart
  void initWebSocket([int retrySeconds = 1]) {
    var reconnectScheduled = false;

    print("Connecting to websocket");

    void scheduleReconnect() {
      if (!reconnectScheduled) {
        Timer(Duration(seconds: retrySeconds),
            () => initWebSocket(retrySeconds * 2));
      }
      reconnectScheduled = true;
    }

    ws.onOpen.listen((e) {
      print('Connected');
      ws.send('Hello from Dart!');
    });

    ws.onClose.listen((e) {
      print('Websocket closed, retrying in ' + '$retrySeconds seconds');
      scheduleReconnect();
    });

    ws.onError.listen((e) {
      print("Error connecting to ws");
      scheduleReconnect();
    });

    ws.onMessage.listen((MessageEvent e) {
      print('Received message: ${e.data}');
    });
  }
```

{% endcomment %}


#### 处理 WebSocket 事件

应用能够处理以下 WebSocket 事件：打开，关闭，错误和（如前所示的）消息。
下面是一个创建 WebSocket 对象并为打开，关闭，错误和消息事件注册处理程序的示例：

{% comment %}code-excerpt "test/html_test.dart (initWebSocket)" plaster="none"{% endcomment %}
```dart
  void initWebSocket([int retrySeconds = 1]) {
    var reconnectScheduled = false;

    print("Connecting to websocket");

    void scheduleReconnect() {
      if (!reconnectScheduled) {
        Timer(Duration(seconds: retrySeconds),
            () => initWebSocket(retrySeconds * 2));
      }
      reconnectScheduled = true;
    }

    ws.onOpen.listen((e) {
      print('Connected');
      ws.send('Hello from Dart!');
    });

    ws.onClose.listen((e) {
      print('Websocket closed, retrying in ' + '$retrySeconds seconds');
      scheduleReconnect();
    });

    ws.onError.listen((e) {
      print("Error connecting to ws");
      scheduleReconnect();
    });

    ws.onMessage.listen((MessageEvent e) {
      print('Received message: ${e.data}');
    });
  }
```

{% comment %}

### More information

This section barely scratched the surface of using the dart:html
library. For more information, see the documentation for
[dart:html.][dart:html]
Dart has additional libraries for more specialized web APIs, such as
[web audio,][web audio] [IndexedDB,][IndexedDB] and [WebGL.][WebGL]

For more information about Dart web libraries, see the
[web library overview.][web library overview]

[AnchorElement]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/AnchorElement-class.html
[dart:html]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/dart-html-library.html
[Dart Library Tour]: {{site.dartlang}}/guides/libraries/library-tour
[Document]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Document-class.html
[Element]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Element-class.html
[HttpRequest]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/HttpRequest-class.html
[IndexedDB]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-indexed_db/dart-indexed_db-library.html
[MessageEvent]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/MessageEvent-class.html
[Nodes]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Node-class.html
[URIs]: /guides/libraries/library-tour#uris
[web audio]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-web_audio/dart-web_audio-library.html
[WebGL]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-web_gl/dart-web_gl-library.html
[WebSocket]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/WebSocket-class.html
[web library overview]: /web/libraries
[Window]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Window-class.html

{% endcomment %}


### 更多内容

本章只是介绍了 dart:html 库使用的一些皮毛。更多内容，参见 [dart:html][dart:html] 文档。
Dart 一些额外的库提供了更专业的 Web API ，
例如 [Web Audio][web audio] , [IndexedDB][IndexedDB], 以及 [WebGL][WebGL] 。

更多关于 Dart Web 库的内容，参见 [Web 库综述][web library overview] 。

[AnchorElement]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/AnchorElement-class.html
[dart:html]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/dart-html-library.html
[Dart Library Tour]: {{site.dartlang}}/guides/libraries/library-tour
[Document]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Document-class.html
[Element]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Element-class.html
[HttpRequest]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/HttpRequest-class.html
[IndexedDB]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-indexed_db/dart-indexed_db-library.html
[MessageEvent]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/MessageEvent-class.html
[Nodes]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Node-class.html
[URIs]: /guides/libraries/library-tour#uris
[web audio]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-web_audio/dart-web_audio-library.html
[WebGL]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-web_gl/dart-web_gl-library.html
[WebSocket]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/WebSocket-class.html
[web library overview]: /web/libraries
[Window]: {{site.dart_api}}/{{site.data.pkg-vers.SDK.channel}}/dart-html/Window-class.html
