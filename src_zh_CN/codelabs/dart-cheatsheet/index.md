---
title: Dart Codelab 速查
description: 对 Dart 特有功能交互式学习及回顾。
---

<style>
  iframe {
    border: 1px solid #ccc;
    width: 100%;
    height: 400px;
  }

  iframe[short] {
    height: 220px;
  }
</style>


{% comment %}

The Dart language is designed to be easy to learn for
coders coming from other languages,
but it has a few unique features.
This codelab — which is based on a 
[Dart language cheatsheet](/guides/language/cheatsheet)
written by and for Google engineers —
walks you through the most important of these language features.

The embedded editors in this codelab have partially completed code snippets.
You can use these editors to test your knowledge by completing the code and
clicking the **Run** button.
If you need help, click the **Hint** button.
To run the code formatter ([dartfmt](/tools/dartfmt)), click **Format**.
The **Reset** button erases your work and
restores the editor to its original state.

<aside class="alert alert-warning">
The embedded editors use an experimental version of DartPad.
If you find a DartPad bug or have suggestions for DartPad, please
<a target="_BLANK" href="https://github.com/dart-lang/dart-pad/issues/new">create a DartPad issue.</a>
If you have suggestions for the text or examples in this codelab,
you can create a site issue by clicking the bug icon
at the top right of this page.
</aside>

{% endcomment %}

对于其他语言的开发者， Dart 语言的语法设计非常易学，但它也有一些其独特的功能。
该 Codelab 基于 为 google 工程师编写的 [Dart 语言速查](/guides/language/cheatsheet)，
Codelab 将引导你了解体验 Dart 语言功能中最重要的功能和特性。

此代码框中的嵌入式编辑器已部分完成代码片段。 您可以使用这些编辑器通过完成代码并单击“运行”按钮来测试您的知识。 如果需要帮助，请单击“提示”按钮。 要运行代码格式化程序（dartfmt），请单击“格式”。 “重置”按钮会删除您的工作并将编辑器恢复到其原始状态。

该 Codelab 中的内嵌编辑器已经包含了部分完成的代码片段。
通过补全下列编辑器中代码，并点击 **Run** 按钮，来测试你对语言知识的掌握情况。
如果需要帮助，可以点击 **Hint** 按钮。
格式化代码（[dartfmt](/tools/dartfmt)），请点击 **Format** 按钮。
清楚编辑内容，加载编辑器原始内容，点击 **Reset** 按钮。

<aside class="alert alert-warning">
嵌入的编辑器为实验版的 DartPad 。
如果在 DartPad 中发现 Bug 或对 DartPad 提出建议，请
<a target="_BLANK" href="https://github.com/dart-lang/dart-pad/issues/new">创建一个 DartPad 的 Issue</a> 。
如果是针对该 Codelab 内容或示例的建议，
可点击页面顶部右上角错误图标创建对于本站的 Issue 。
</aside>


{% comment %}

## String interpolation

To put the value of an expression inside a string, use `${expression}`.
If the expression is an identifier, you can omit the `{}`.

Here are some examples of using string interpolation:

| String                      | | Result |
|-----------------------------+-+ -------|
| `'${3 + 2}'`                | | `'5'` |
| `'${"word".toUpperCase()}'` | | `'WORD'` |
| `'$myObject'`               | | The value of `myObject.toString()` |

### Code example

The following function takes two integers as parameters.
Make it return a string containing both integers separated by a space.
For example, `stringify(2, 3)` should return `'2 3'`.

<iframe src="{{site.dartpadx}}?id=43f3db47b0632c557200270807696687"></iframe>

{% endcomment %}


## 字符串插值

通过 `${表达式}` 将表达式的值引入到字符串中。
如果表达式为标识符，可忽略 `{}` 。

下面是一些字符串插值的实例：

| 字符串                      | | 结果 |
|-----------------------------+-+ -------|
| `'${3 + 2}'`                | | `'5'` |
| `'${"word".toUpperCase()}'` | | `'WORD'` |
| `'$myObject'`               | | The value of `myObject.toString()` |

### 代码示例

以下函数将两个整数作为参数。
返回一个包含这两个整数的字符串，两个整数由空格分割。
例如，`stringify(2, 3)` 返回值为 `'2 3'` 。

<iframe src="{{site.dartpadx}}?id=43f3db47b0632c557200270807696687"></iframe>


{% comment %}

## Null-aware operators


Dart offers some handy operators for dealing with values that might be null. One is the
`??=` assignment operator, which assigns a value to a variable only if that
variable is currently null:

{% comment %}
TBD: Make this and all non-trivial snippets testable.
I found an error in one of the getter/setter snippets.
{% endcomment %}

{% prettify dart %}
int a; // The initial value of any object is null.
a ??= 3;
print(a); // <-- Prints 3.

a ??= 5;
print(a); // <-- Still prints 3.
{% endprettify %}

Another null-aware operator is `??`,
which returns the expression on its left unless that expression's value is null,
in which case it evaluates and returns the expression on its right:

{% prettify dart %}
    print(1 ?? 3); // <-- Prints 1.
    print(null ?? 12); // <-- Prints 12.
{% endprettify %}

### Code example

Try putting the `??=` and `??` operators to work below.

<iframe src="{{site.dartpadx}}?id=ee3d441f60acc95a07d73762a61b3b98"></iframe>

{% endcomment %}


## Null-Aware 操作符

Dart 提供一些用来处理值可能为 null 的操作符。
`??=` 为其中的一个操作符，使用该操作符赋值，仅当被赋值变量为空时赋值有效。

{% comment %}
TBD: Make this and all non-trivial snippets testable.
I found an error in one of the getter/setter snippets.
{% endcomment %}

{% prettify dart %}
int a; // 对象的初始化值为 null 。
a ??= 3;
print(a); // <-- 打印结果为 3 。

a ??= 5;
print(a); // <-- 打印结果仍然是 3 。
{% endprettify %}

另一个 Null-Aware 操作符为 `??` ，
表达式左侧值为非 null 时，返回左侧表达式。
否则计算并返回右边的表达式：

{% prettify dart %}
    print(1 ?? 3); // <-- Prints 1.
    print(null ?? 12); // <-- Prints 12.
{% endprettify %}

### 示例代码

尝试将 `??=` 和 `??` 操作符加入到以下代码中。

<iframe src="{{site.dartpadx}}?id=ee3d441f60acc95a07d73762a61b3b98"></iframe>


{% comment %}

## Conditional property access

To guard access to a property or method of an object that might be null,
put a question mark (`?`) before the dot (`.`):

{% prettify dart %}
myObject?.someProperty
{% endprettify %}

The preceding code is equivalent to the following:

{% prettify dart %}
(myObject != null) ? myObject.someProperty : null
{% endprettify %}

You can chain multiple uses of `?.` together in a single expression:

{% prettify dart %}
myObject?.someProperty?.someMethod()
{% endprettify %}

The preceding code returns null (and never calls `someMethod`) if either
`myObject` or `myObject.someProperty` is
null.


### Code example

Try using conditional property access to finish the code snippet below.

<iframe src="{{site.dartpadx}}?id=58f14a3d943be6231ae611036fcfc80d"></iframe>

{% endcomment %}


## 属性的条件访问

防止对可能为 null 的对象进行属性或方法的访问，
可以在点（`.`）的前面加上一个问号（`？`）：

{% prettify dart %}
myObject?.someProperty
{% endprettify %}

上述代码等效于以下内容：

{% prettify dart %}
(myObject != null) ? myObject.someProperty : null
{% endprettify %}

可以在一个表达式中 `?.` 可以多次链式的使用：

{% prettify dart %}
myObject?.someProperty?.someMethod()
{% endprettify %}

上述代码中无论是 `myObject` 或 `myObject.someProperty` 为空，均返回 null （且永远不会调用 `someMethod` 函数）。

### 示例代码

使用属性条件访问完成下面的代码片段。

<iframe src="{{site.dartpadx}}?id=58f14a3d943be6231ae611036fcfc80d"></iframe>


{% comment %}

## Collection literals

Dart has built-in support for lists, maps, and sets.
You can create them using literals:

{% prettify dart %}
final aListOfStrings = ['one', 'two', 'three'];
final aSetOfStrings = {'one', 'two', 'three'};
final aMapOfStringsToInts = {
  'one': 1,
  'two': 2,
  'three': 3,
};
{% endprettify %}

Dart's type inference can assign types to these variables for you.
In this case, the inferred types are `List<String>`,
`Set<String>`, and `Map<String, int>`.

Or you can specify the type yourself:

{% prettify dart %}
final aListOfInts = <int>[];
final aSetOfInts = <int>{};
final aMapOfIntToDouble = <int, double>{};
{% endprettify %}

Specifying types is handy when you initialize a list with contents of a subtype,
but still want the list to be `List<BaseType>`:

{% prettify dart %}
final aListOfBaseType = <BaseType>[SubType(), SubType()];
{% endprettify %}

### Code example

Try setting the following variables to the indicated values.

<iframe src="{{site.dartpadx}}?id=8ba5e98559ff2a2e92e58ac5a28f1cff"></iframe>

{% endcomment %}


## 字面量集合

Dart 内建支持 List ， Map ， Set 类型。
这些类型可以通过字面量来创建：

{% prettify dart %}
final aListOfStrings = ['one', 'two', 'three'];
final aSetOfStrings = {'one', 'two', 'three'};
final aMapOfStringsToInts = {
  'one': 1,
  'two': 2,
  'three': 3,
};
{% endprettify %}

Dart的类型推断可以分配这些变量的类型。
基于推断，上述变量的推断类型分别为
`List<String>` ， `Set<String>` ，及 `Map<String, int>` 。
我们也可以显示的指定上述变量的类型。

{% prettify dart %}
final aListOfInts = <int>[];
final aSetOfInts = <int>{};
final aMapOfIntToDouble = <int, double>{};
{% endprettify %}

在使用子类型对象初始化 List ，可以非常方便的指定 List 类型。
但我们仍然可以人为的指定 List 类型，比如指定 List 类型为 `List<BaseType>` ：

{% prettify dart %}
final aListOfBaseType = <BaseType>[SubType(), SubType()];
{% endprettify %}


{% comment %}

## Arrow syntax

You might have seen the `=>` symbol in Dart code.
This arrow syntax is a way to define a function that executes the
expression to its right and returns its value.

For example, consider this call to the `List` class's
`any` method:

{% prettify dart %}
bool hasEmpty = aListOfStrings.any((s) {
  return s.isEmpty;
});
{% endprettify %}

Here’s a simpler way to write that code:

{% prettify dart %}
bool hasEmpty = aListOfStrings.any((s) => s.isEmpty);
{% endprettify %}

### Code example

Try finishing the following statements, which use arrow syntax.

<iframe src="{{site.dartpadx}}?id=7c287c55dcc7f414a5dfa5837e3450e3"></iframe>

{% comment %}
ISSUE: The analysis output kept getting in the way of my typing for the
last part of this code. Also, how are they supposed to know to use the
join() method?

TBD: The comments in "Your code" are in the form of doc comments,
but they don't use `///`, and they end in `:`, not `.`.
{% endcomment %}

{% endcomment %}


## 箭头语法

我们在 Dart 代码中常常会见到 `=>` 字符。
该箭头语法用来定义一个函数，函数执行它右侧的表达式，并返回表达式结果。

例如，思考下面 `List` 的 `any` 的传统调用方式：
For example, consider this call to the `List` class's
`any` method:

{% prettify dart %}
bool hasEmpty = aListOfStrings.any((s) {
  return s.isEmpty;
});
{% endprettify %}

下面是对以上代码的一种简写：

{% prettify dart %}
bool hasEmpty = aListOfStrings.any((s) => s.isEmpty);
{% endprettify %}

### 代码示例

尝试使用箭头语法完成以下代码。

<iframe src="{{site.dartpadx}}?id=7c287c55dcc7f414a5dfa5837e3450e3"></iframe>

{% comment %}
ISSUE: The analysis output kept getting in the way of my typing for the
last part of this code. Also, how are they supposed to know to use the
join() method?

TBD: The comments in "Your code" are in the form of doc comments,
but they don't use `///`, and they end in `:`, not `.`.
{% endcomment %}


{% comment %}

## Cascades

To perform a sequence of operations on the same object, use cascades (`..`).
We've all seen an expression like this:

{% prettify dart %}
myObject.someMethod()
{% endprettify %}

It invokes `someMethod` on `myObject`, and the result of
the expression is the return value of `someMethod`.

Here's the same expression with a cascade:

{% prettify dart %}
myObject..someMethod()
{% endprettify %}

Although it still invokes `someMethod` on `myObject`, the result
of the expression **isn't** the return value — it's a reference to `myObject`!
Using cascades, you can chain together operations that
would otherwise require separate statements.
For example, consider this code:

{% prettify dart %}
var button = querySelector('#confirm');
button.text = 'Confirm';
button.classes.add('important');
button.onClick.listen((e) => window.alert('Confirmed!'));
{% endprettify %}

With cascades, the code becomes much shorter,
and you don’t need the `button` variable:

{% prettify dart %}
querySelector('#confirm')
..text = 'Confirm'
..classes.add('important')
..onClick.listen((e) => window.alert('Confirmed!'));
{% endprettify %}

### Code example

Use cascades to create a single statement that
sets the `anInt`, `aString`, and `aList` properties of a `BigObject`
to `1`, `'String!'`, and `[3.0]` (respectively)
and then calls `allDone()`.

<iframe src="{{site.dartpadx}}?id=72bde0b4d5c8c6046b4853a3b4053c3a"></iframe>

{% endcomment %}


## 级联

要对同一对象执行一系列操作，请使用级联（`..`）。 我们都见过下面的表达式：

{% prettify dart %}
myObject.someMethod()
{% endprettify %}

表达式调用 `myObject` 对象的 `someMethod` 方法，表达式返回
`someMethod` 函数结果。

下面是使用了级联的相似表达式：

{% prettify dart %}
myObject..someMethod()
{% endprettify %}

尽管表达式依旧调用了 `myObject` 对象的 `someMethod` 方法，但表达式结果
**并不是** 函数的执行结果，而是 `myObject` 的引用！
使用级联，可以将需要单独语句的操作链接在一起。请思考以下示例代码：

{% prettify dart %}
var button = querySelector('#confirm');
button.text = 'Confirm';
button.classes.add('important');
button.onClick.listen((e) => window.alert('Confirmed!'));
{% endprettify %}

使用级联，代码会变得非常简短，代码中不也不需要 `button` 这个中间变量。

{% prettify dart %}
querySelector('#confirm')
..text = 'Confirm'
..classes.add('important')
..onClick.listen((e) => window.alert('Confirmed!'));
{% endprettify %}

### 示例代码

使用级联来创建一个语句，将 `BigObject` 的 `anInt` ， `aString` 和 `aList` 属性分别设置为 `1` ，
`'String！'` 和 `[3.0]` 最后然后调用 `allDone()` 。

<iframe src="{{site.dartpadx}}?id=72bde0b4d5c8c6046b4853a3b4053c3a"></iframe>


{% comment %}

## Getters and setters

You can define getters and setters
whenever you need more control over a property
than a simple field allows.

For example, you can make sure a property's value is valid:

{% prettify dart %}
class MyClass {
  int _aProperty = 0;

  int get aProperty => _aProperty;

  set aProperty(int value) {
    if (value >= 0) {
      _aProperty = value;
    }
  }
}
{% endprettify %}

You can also use a getter to define a computed property:

{% prettify dart %}
class MyClass {
  List<int> _values = [];

  void addValue(int value) {
    _values.add(value);
  }

  // A computed property.
  int get count {
    return _values.length;
  }
}
{% endprettify %}

### Code example

Imagine you have a shopping cart class that keeps a private `List<double>`
of prices.
Add the following:

* A getter called `total` that returns the sum of the prices
* A setter that replaces the list with a new one,
  as long as the new list doesn't contain any negative prices
  (in which case the setter should throw an `InvalidPriceException`).

<iframe src="{{site.dartpadx}}?id=84561041d263cbd4c92f614eceec85e6"></iframe>

{% endcomment %}


## Getter 和 Setter

当需要对字段进行控制，可以通过定义 Getter 和 Setter 实现。

例如，判断属性值是否有效：

{% prettify dart %}
class MyClass {
  int _aProperty = 0;

  int get aProperty => _aProperty;

  set aProperty(int value) {
    if (value >= 0) {
      _aProperty = value;
    }
  }
}
{% endprettify %}

同样可以通过 Getter 来定义一个计算属性：

{% prettify dart %}
class MyClass {
  List<int> _values = [];

  void addValue(int value) {
    _values.add(value);
  }

  // 计算属性。
  int get count {
    return _values.length;
  }
}
{% endprettify %}

### 示例代码

假设一个购物车类中有一个私有的 `List<double>` 属性保存商品价格。
为该类增加以下内容：

* 名为 `total` 的 Getter 方法，，返回总价。 A getter called `total` that returns the sum of the prices
* 一个 Setter 方法，该方法用来设置一个新的 List 对象，但要求新的 List 对象中的价格不能包含负值。
  （如果 List 对象的价格中包含负值，那么应抛出一个 `InvalidPriceException` 异常）。

<iframe src="{{site.dartpadx}}?id=84561041d263cbd4c92f614eceec85e6"></iframe>


{% comment %}

## Optional positional parameters

Dart has two kinds of function parameters: positional and named. Positional parameters are the kind
you're likely familiar with:

{% prettify dart %}
int sumUp(int a, int b, int c) {
  return a + b + c;
}

int total = sumUp(1, 2, 3);
{% endprettify %}

With Dart, you can make these positional parameters optional by wrapping them in brackets:

{% prettify dart %}
int sumUpToFive(int a, [int b, int c, int d, int e]) {
  int sum = a;
  if (b != null) sum += b;
  if (c != null) sum += c;
  if (d != null) sum += d;
  if (e != null) sum += e;
  return sum;
}

int total = sumUptoFive(1, 2);
int otherTotal = sumUpToFive(1, 2, 3, 4, 5);
{% endprettify %}

Optional positional parameters are always last
in a function's parameter list.
Their default value is null unless you provide another default value:

{% prettify dart %}
int sumUpToFive(int a, [int b = 2, int c = 3, int d = 4, int e = 5]) {
  ...
}

int newTotal = sumUpToFive(1);
print(newTotal); // <-- prints 15
{% endprettify %}

### Code example

Implement a function called `joinWithCommas` that accepts one to
five integers, then returns a string of those numbers separated by commas.
Here are some examples of function calls and returned values:

| Function call                   | | Returned value |
|---------------------------------+-+----------------|
| `joinWithCommas(1)`             | | `'1'`          |
| `joinWithCommas(1, 2, 3)`       | | `'1,2,3'`      |
| `joinWithCommas(1, 1, 1, 1, 1)` | | `'1,1,1,1,1'`  |

<br>

<iframe src="{{site.dartpadx}}?id=9e7d5b6b56319b7e3b12b791c0ae27c1"></iframe>

{% endcomment %}


## 位置可选参数

Dart 拥有两种函数参数：位置参数和命名参数。
我们熟悉的位置参数类似于：

{% prettify dart %}
int sumUp(int a, int b, int c) {
  return a + b + c;
}

int total = sumUp(1, 2, 3);
{% endprettify %}

在 Dart 中，包裹在中括号中的位置参数为可选参数：

{% prettify dart %}
int sumUpToFive(int a, [int b, int c, int d, int e]) {
  int sum = a;
  if (b != null) sum += b;
  if (c != null) sum += c;
  if (d != null) sum += d;
  if (e != null) sum += e;
  return sum;
}

int total = sumUptoFive(1, 2);
int otherTotal = sumUpToFive(1, 2, 3, 4, 5);
{% endprettify %}

位置可选参数始终在参数列表的最后。
除非指定位置可选参数的默认值，否则它们的默认值为 null ：

{% prettify dart %}
int sumUpToFive(int a, [int b = 2, int c = 3, int d = 4, int e = 5]) {
  ...
}

int newTotal = sumUpToFive(1);
print(newTotal); // <-- prints 15
{% endprettify %}

### 示例代码

实现 `joinWithCommas` 函数，函数接收 1 到 5 个整型参数。
函数返回包含数字的字符串，数字间使用逗号分隔。
下面是函数调用及返回值的一些示例：

| 函数调用                   | | 返回值 |
|---------------------------------+-+----------------|
| `joinWithCommas(1)`             | | `'1'`          |
| `joinWithCommas(1, 2, 3)`       | | `'1,2,3'`      |
| `joinWithCommas(1, 1, 1, 1, 1)` | | `'1,1,1,1,1'`  |

<br>

<iframe src="{{site.dartpadx}}?id=9e7d5b6b56319b7e3b12b791c0ae27c1"></iframe>


{% comment %}

## Optional named parameters

Using a curly brace syntax,
you can define optional parameters that have names.

{% prettify dart %}
void printName(String firstName, String lastName, {String suffix}) {
  print('$firstName $lastName ${suffix ?? ''}');
}

printName('Avinash', 'Gupta');
printName('Poshmeister', 'Moneybuckets', suffix: 'IV');
{% endprettify %}

As you might expect, the value of these parameters is null by default,
but you can provide default values:

{% prettify dart %}
void printName(String firstName, String lastName, {String suffix = ''}) {
  print('$firstName $lastName ${suffix}');
}
{% endprettify %}

A function can't have both optional positional and optional named parameters.


### Code example

Add a `copyWith` instance method to the `MyDataObject`
class. It should take three named parameters:

* `int newInt`
* `String newString`
* `double newDouble`

When called, `copyWith` should return a new `MyDataObject`
based on the current instance,
with data from the preceding parameters (if any)
copied into the object's properties.
For example, if `newInt` is non-null,
then copy its value into `anInt`.

<iframe src="{{site.dartpadx}}?id=1dd9cc9654f9e6d080f99bfb9772dae4"></iframe>

{% endcomment %}


## 命名可选参数

使用大括号语法，定义具有名称可选参数。

{% prettify dart %}
void printName(String firstName, String lastName, {String suffix}) {
  print('$firstName $lastName ${suffix ?? ''}');
}

printName('Avinash', 'Gupta');
printName('Poshmeister', 'Moneybuckets', suffix: 'IV');
{% endprettify %}

默认情况下这些参数的值为 null ，同样我们可以为这些参数提供默认值：

{% prettify dart %}
void printName(String firstName, String lastName, {String suffix = ''}) {
  print('$firstName $lastName ${suffix}');
}
{% endprettify %}

一个函数不能同时包含位置可选参数和命名可选参数。


### 示例代码

为 `MyDataObject` 类提供一个 `copyWith` 方法。
方法能够接收 3 个参数：

* `int newInt`
* `String newString`
* `double newDouble`

调用 `copyWith` 时应该根据当前实例返回一个新的 `MyDataObject` 示例，
并将前面参数（如果有）的数据复制到对象的属性中。
例如，如果 `newInt` 为非 null ，则将其值复制到 `anInt` 属性中。

<iframe src="{{site.dartpadx}}?id=1dd9cc9654f9e6d080f99bfb9772dae4"></iframe>


{% comment %}

## Exceptions

Dart code can throw and catch exceptions. In contrast to Java, all of Dart’s exceptions are unchecked
exceptions. Methods don't declare which exceptions they might throw, and you aren't required to catch
any exceptions.

Dart provides `Exception` and `Error` types, but you're
allowed to throw any non-null object:

{% prettify dart %}
throw Exception('Something bad happened.');
throw 'Waaaaaaah!';
{% endprettify %}

Use the `try`, `on`, and `catch` keywords when handling exceptions:

{% prettify dart %}
try {
  breedMoreLlamas();
} on OutOfLlamasException {
  // A specific exception
  buyMoreLlamas();
} on Exception catch (e) {
  // Anything else that is an exception
  print('Unknown exception: $e');
} catch (e) {
  // No specified type, handles all
  print('Something really unknown: $e');
}
{% endprettify %}

The `try` keyword works as it does in most other languages.
Use the `on` keyword to filter for specific exceptions by type,
and the `catch` keyword to get a reference to the exception object.

If you can't completely handle the exception, use the `rethrow` keyword
to propagate the exception:

{% prettify dart %}
try {
  breedMoreLlamas();
} catch (e) {
  print('I was just trying to breed llamas!.');
  rethrow;
}
{% endprettify %}

To execute code whether or not an exception is thrown,
use `finally`:

{% prettify dart %}
try {
  breedMoreLlamas();
} catch (e) {
  … handle exception ...
} finally {
  // Always clean up, even if an exception is thrown.
  cleanLlamaStalls();
}
{% endprettify %}

### Code example

Implement `tryFunction` below. It should execute an untrustworthy method and
then do the following:

* If `untrustworthy` throws an `ExceptionWithMessage`,
  call `logger.logException` with the exception type and message
  (try using `on` and `catch`).
* If `untrustworthy` throws an `Exception`,
  call `logger.logException` with the exception type
  (try using `on` for this one).
* If `untrustworthy` throws any other object, don't catch the exception.
* After everything's caught and handled, call `logger.doneLogging`
  (try using `finally`).

<iframe src="{{site.dartpadx}}?id=e221e3fd667825e62aac79079b8b5c59"></iframe>

{% comment %}
I was confused about the text saying "call... with the exception type" but
using only on for it (since how would you know the type without the exception
object?). I used on catch at first, and that worked. Then I looked at the
solution and changed to what it used, and it did NOT work! Here's what I saw:

Untrustworthy threw an Exception, but a different type was logged: Exception.

(Looking at the test code, I see the type it looks for is actually _Exception.)

Both the text & the test need to be changed.

ISSUE: Solution doesn't exactly match the comments in "Your code", so the
line count is off.

ISSUE: When I select all in the Solution and then switch to the Your code tab,
everything in THAT tab looks selected, too. The same is NOT true of the
Test code tab. After I reloaded, this behavior stopped.
{% endcomment %}

{% endcomment %}


## 异常

Dart 可以抛出和捕获异常。与 Java 相比， Dart 的所有异常都是未经检查的异常。
方法不会声明可能抛出的异常，任何异常也不要求你必须去捕获。

Dart提供了 `Exception` 和 `Error` 数据类型，但在异常中允许抛出任何非 null 对象：

{% prettify dart %}
throw Exception('Something bad happened.');
throw 'Waaaaaaah!';
{% endprettify %}

使用 `try` ， `on` ， 和 `catch` 关键字来处理异常：

{% prettify dart %}
try {
  breedMoreLlamas();
} on OutOfLlamasException {
  // A specific exception
  buyMoreLlamas();
} on Exception catch (e) {
  // Anything else that is an exception
  print('Unknown exception: $e');
} catch (e) {
  // No specified type, handles all
  print('Something really unknown: $e');
}
{% endprettify %}

`try` 关键字的作用与大多数其他语言一样。
`on` 关键字可以按类型过滤特定异常，
`catch` 关键字用来获取对异常对象的引用。

如果无法完全处理异常，应该使用 `rethrow` 关键字来传播异常：

{% prettify dart %}
try {
  breedMoreLlamas();
} catch (e) {
  print('I was just trying to breed llamas!.');
  rethrow;
}
{% endprettify %}

`finally` 中实现异常中始终要执行的代码：

To execute code whether or not an exception is thrown,
use `finally`:

{% prettify dart %}
try {
  breedMoreLlamas();
} catch (e) {
  … handle exception ...
} finally {
  // Always clean up, even if an exception is thrown.
  cleanLlamaStalls();
}
{% endprettify %}

### 示例代码

在下面实现 `tryFunction` 方法。 它执行一个不被信任的方法，并执行以下操作：

* 如果 `untrustworthy` 抛出一个 `ExceptionWithMessage` 异常，
  则使用异常类型和消息调用 `logger.logException`（尝试使用 `on` 和 `catch` ）。
* 如果 `untrustworthy` 抛出一个 `Exception` 异常，
  则使用异常类型调用 `logger.logException`（尝试使用 `on` 和 `catch` ）。
* 如果 `untrustworthy` 抛出一个其他对象，
  不去捕获异常。
* 任意捕获和处理结束后, 调用 `logger.doneLogging`
  （尝试使用 `finally` ）。

<iframe src="{{site.dartpadx}}?id=e221e3fd667825e62aac79079b8b5c59"></iframe>

{% comment %}
I was confused about the text saying "call... with the exception type" but
using only on for it (since how would you know the type without the exception
object?). I used on catch at first, and that worked. Then I looked at the
solution and changed to what it used, and it did NOT work! Here's what I saw:

Untrustworthy threw an Exception, but a different type was logged: Exception.

(Looking at the test code, I see the type it looks for is actually _Exception.)

Both the text & the test need to be changed.

ISSUE: Solution doesn't exactly match the comments in "Your code", so the
line count is off.

ISSUE: When I select all in the Solution and then switch to the Your code tab,
everything in THAT tab looks selected, too. The same is NOT true of the
Test code tab. After I reloaded, this behavior stopped.
{% endcomment %}


{% comment %}

## Using `this` in a constructor

Dart provides a handy shortcut for assigning
values to properties in a constructor:
use `this.propertyName` when declaring the constructor:

{% prettify dart %}
class MyColor {
  int red;
  int green;
  int blue;

  MyColor(this.red, this.green, this.blue);
}

final color = MyColor(80, 80, 128);
{% endprettify %}

This technique works for named parameters, too.
Property names become the names of the parameters:

{% prettify dart %}
class MyColor {
  ...

  MyColor({this.red, this.green, this.blue});
}

final color = MyColor(red: 80, green: 80, blue: 80);
{% endprettify %}

For optional parameters, default values work as expected:

{% prettify dart %}
MyColor([this.red = 0, this.green = 0, this.blue = 0]);
// or
MyColor({this.red = 0, this.green = 0, this.blue = 0});
{% endprettify %}

### Code example

Add a one-line constructor to `MyClass` that uses
`this.` syntax to receive and assign values for
all three properties of the class.

<iframe src="{{site.dartpadx}}?id=2778e81ae2c5729d45c611829f3888c2"></iframe>

{% comment %}
This one seems super easy compared to previous ones.
We've already seen it in the Exceptions example,
and I'd already used it in a previous example.
Move it up higher? Or make it more challenging, somehow?
Maybe require both positional and optional named parameters (with defaults)?
{% endcomment %}

{% endcomment %}


## 在构造函数中使用 `this`

Dart 在构造函数中提供便利简短的属性访问：
在声明构造函数时使用 `this.propertyName` ：

{% prettify dart %}
class MyColor {
  int red;
  int green;
  int blue;

  MyColor(this.red, this.green, this.blue);
}

final color = MyColor(80, 80, 128);
{% endprettify %}

此技术也适用于命名参数。 将属性名称用作参数名称：

{% prettify dart %}
class MyColor {
  ...

  MyColor({this.red, this.green, this.blue});
}

final color = MyColor(red: 80, green: 80, blue: 80);
{% endprettify %}

对于可选参数，根据参数类型给定默认值：

{% prettify dart %}
MyColor([this.red = 0, this.green = 0, this.blue = 0]);
// or
MyColor({this.red = 0, this.green = 0, this.blue = 0});
{% endprettify %}

### 示例代码

为 `MyClass` 增加一个构造函数，构造函数使用 `this.` 语法来接收和赋值类的所有的属性的值。

<iframe src="{{site.dartpadx}}?id=2778e81ae2c5729d45c611829f3888c2"></iframe>

{% comment %}
This one seems super easy compared to previous ones.
We've already seen it in the Exceptions example,
and I'd already used it in a previous example.
Move it up higher? Or make it more challenging, somehow?
Maybe require both positional and optional named parameters (with defaults)?
{% endcomment %}


{% comment %}

## Initializer lists

Sometimes when you implement a constructor,
you need to do some setup before the constructor body executes.
For example, final fields must have values
before the constructor body executes.
Do this work in an initializer list,
which goes between the constructor's signature and its body:

{% prettify dart %}
Point.fromJson(Map<String, num> json)
    : x = json['x'],
      y = json['y'] {
  print('In Point.fromJson(): ($x, $y)');
}
{% endprettify %}

The initializer list is also a handy place to put asserts,
which run only during development:

{% prettify dart %}
NonNegativePoint(this.x, this.y)
    : assert(x >= 0),
      assert(y >= 0) {
  print('I just made a NonNegativePoint: ($x, $y)');
}
{% endprettify %}

### Code example

Complete the `FirstTwoLetters` constructor below.
Use an initializer list to assign the first two characters in `word` to
the `letterOne` and `LetterTwo` properties.
For extra credit, add an `assert` to catch words of less than two characters.

{% comment %}
ISSUE: The test was broken. I've fixed it in my gist.

Is the assert even executed? I can't see any effect on the test,
which makes me think asserts are ignored.
Also, the test just checks for the presence of any exception, not for
an AssertionError.

Also, my print() wasn't visible in the Output until I fixed my code and/or
the test. That was unexpected.
It'd be cool if Output appeared only if you want it, like Solution does.
{% endcomment %}

<iframe src="{{site.dartpadx}}?id=df45dfc1af2e6af712930c331115eb78"></iframe>

{% endcomment %}


## 初始化列表

有时，在实现构造函数时，需要在构造函数体执行之前进行一些设置。
例如， final 字段必须在构造函数体执行之前具有值。
这些操作需要在初始化列表中执行，初始化列表位于构造函数名及构造函数体之间：

{% prettify dart %}
Point.fromJson(Map<String, num> json)
    : x = json['x'],
      y = json['y'] {
  print('In Point.fromJson(): ($x, $y)');
}
{% endprettify %}

初始化列表也是放置断言的便利位置，断言只在开发期间被执行：

{% prettify dart %}
NonNegativePoint(this.x, this.y)
    : assert(x >= 0),
      assert(y >= 0) {
  print('I just made a NonNegativePoint: ($x, $y)');
}
{% endprettify %}

### 示例代码

补全下面的 `FirstTwoLetters` 构造函数。
使用初始化列表将 `word` 中的前两个字符分配给 `letterOne` 和 `LetterTwo` 属性。
额外的，添加一个 `assert` 来捕获少于两个字符的单词。

{% comment %}
ISSUE: The test was broken. I've fixed it in my gist.

Is the assert even executed? I can't see any effect on the test,
which makes me think asserts are ignored.
Also, the test just checks for the presence of any exception, not for
an AssertionError.

Also, my print() wasn't visible in the Output until I fixed my code and/or
the test. That was unexpected.
It'd be cool if Output appeared only if you want it, like Solution does.
{% endcomment %}

<iframe src="{{site.dartpadx}}?id=df45dfc1af2e6af712930c331115eb78"></iframe>


{% comment %}

## Named constructors

{% comment %}
Much like JavaScript, Dart doesn't support method overloads
(two methods with the same name but different signatures).
[ISSUE: methods & constructors aren't the same thing,
so I deleted that. We can add it back if we can word it better.]
{% endcomment %}
To allow classes to have multiple constructors,
Dart supports named constructors:

{% prettify dart %}
class Point {
  num x, y;

  Point(this.x, this.y);

  Point.origin() {
    x = 0;
    y = 0;
  }
}
{% endprettify %}

To use a named constructor, invoke it using its full name:

{% prettify dart %}
final myPoint = Point.origin();
{% endprettify %}

### Code example

Give the Color class a constructor named `Color.black`
that sets all three properties to zero.

{% comment %}
ISSUE: comment says "a named constructor called "black"", which sounds
wrong to me. I fixed it in the text but not in the example.
{% endcomment %}

<iframe src="{{site.dartpadx}}?id=e1a82c77547e659eb24f4e698abf1eca"></iframe>

{% endcomment %}


## 命名构造函数

{% comment %}
Much like JavaScript, Dart doesn't support method overloads
(two methods with the same name but different signatures).
[ISSUE: methods & constructors aren't the same thing,
so I deleted that. We can add it back if we can word it better.]
{% endcomment %}
为了允许类具有多个构造函数，Dart 支持命名构造函数：

{% prettify dart %}
class Point {
  num x, y;

  Point(this.x, this.y);

  Point.origin() {
    x = 0;
    y = 0;
  }
}
{% endprettify %}

使用构造函数的完整名称来调用命名构造函数：

{% prettify dart %}
final myPoint = Point.origin();
{% endprettify %}

### 示例代码

为 Color 类提供一个 `Color.black` 的命名构造函数，
该构造函数设置将 3 个属性全部设置为 0 。

{% comment %}
ISSUE: comment says "a named constructor called "black"", which sounds
wrong to me. I fixed it in the text but not in the example.
{% endcomment %}

<iframe src="{{site.dartpadx}}?id=e1a82c77547e659eb24f4e698abf1eca"></iframe>


{% comment %}

## Factory constructors

Dart supports factory constructors,
which can return subtypes or even null.
To create a factory constructor, use the `factory` keyword:

{% prettify dart %}
class Square extends Shape {}

class Circle extends Shape {}

class Shape {
  Shape();

  factory Shape.fromTypeName(String typeName) {
    if (typeName == 'square') return Square();
    if (typeName == 'circle') return Circle();

    print('I don\'t recognize $typeName');
    return null;
  }
}
{% endprettify %}

### Code example

Fill in the factory constructor named `IntegerHolder.fromList`,
making it do the following:

* If the list has **one** value,
  create an `IntegerSingle` with that value.
* If the list has **two** values,
  create an `IntegerDouble` with the values in order.
* If the list has **three** values,
  create an `IntegerTriple` with the values in order.
* Otherwise, return null.
    
{% comment %}
TODO: Fix the comment to not say "named".
ISSUE: The hint acts like you don't already have the signature for the constructor.
{% endcomment %}
<iframe src="{{site.dartpadx}}?id=727981a8ece1244b52a3c6dc377a8085"></iframe>

{% endcomment %}


## 工厂构造函数

Dart 支持工厂构造函数，
工厂构造函数可以返回该类的子类实例甚至是 null 。
使用 `factory` 关键字来创建工厂构造函数：

{% prettify dart %}
class Square extends Shape {}

class Circle extends Shape {}

class Shape {
  Shape();

  factory Shape.fromTypeName(String typeName) {
    if (typeName == 'square') return Square();
    if (typeName == 'circle') return Circle();

    print('I don\'t recognize $typeName');
    return null;
  }
}
{% endprettify %}

### 示例代码

完成名为 `IntegerHolder.fromList` 的工厂构造函数，使其执行以下操作：

* 如果 List 中包含 **一个** 值，
  使用该值创建 `IntegerSingle` 。
* 如果 List 中包含 **两个** 值，
  使用这些值创建 `IntegerDouble` 。
* 如果 List 中包含 **三个** 值，
  使用这些值创建 `IntegerTriple` 。
* 其他情况，返回 null 。
    
{% comment %}
TODO: Fix the comment to not say "named".
ISSUE: The hint acts like you don't already have the signature for the constructor.
{% endcomment %}
<iframe src="{{site.dartpadx}}?id=727981a8ece1244b52a3c6dc377a8085"></iframe>


{% comment %}

## Redirecting constructors

Sometimes a constructor’s only purpose is to redirect to
another constructor in the same class.
A redirecting constructor’s body is empty,
with the constructor call appearing after a colon (`:`).

{% prettify dart %}
class Automobile {
  String make;
  String model;
  int mpg;

  // The main constructor for this class.
  Automobile(this.make, this.model, this.mpg);

  // Delegates to the main constructor.
  Automobile.hybrid(String make, String model) : this(make, model, 60);

  // Delegates to a named constructor
  Automobile.fancyHybrid() : this.hybrid('Futurecar', 'Mark 2');
}
{% endprettify %}

### Code example

Remember the `Color` class from above? Create a named constructor called
`black`, but rather than manually assigning the properties, redirect it to the
default constructor with zeros as the arguments.

<iframe src="{{site.dartpadx}}?id=94eb1d8be5b64163753c7350f1f09edf"></iframe>

{% endcomment %}


## 重定向构造函数

有时构造函数的唯一目的是重定向到同一个类中的另一个构造函数。
重定向构造函数的主体是空的，实际构造函数出现在冒号（`:`）之后。

{% prettify dart %}
class Automobile {
  String make;
  String model;
  int mpg;

  // The main constructor for this class.
  Automobile(this.make, this.model, this.mpg);

  // Delegates to the main constructor.
  Automobile.hybrid(String make, String model) : this(make, model, 60);

  // Delegates to a named constructor
  Automobile.fancyHybrid() : this.hybrid('Futurecar', 'Mark 2');
}
{% endprettify %}

### 示例代码

还记得上面的 `Color` 类吗？
创建一个名为 `black` 的命名构造函数，但不手动分配属性，
而是将其重定向到默认构造函数，设置默认构造函数的参数为 0 。

<iframe src="{{site.dartpadx}}?id=94eb1d8be5b64163753c7350f1f09edf"></iframe>


{% comment %}

## Const constructors

If your class produces objects that never change, you can make these objects compile-time constants. To
do this, define a `const` constructor and make sure that all instance variables
are final.

{% prettify dart %}
class ImmutablePoint {
  const ImmutablePoint(this.x, this.y);

  final int x;
  final int y;

  static const ImmutablePoint origin =
      ImmutablePoint(0, 0);
}
{% endprettify %}

### Code example

Modify the `Recipe` class so its instances can be constants,
and create a constant constructor that does the following:

* Has three parameters: `ingredients`, `calories`,
  and `milligramsOfSodium` (in that order).
* Uses `this.` syntax to automatically assign the parameter values to the
  object properties of the same name.
* Is constant, with the `const` keyword just before
  `Recipe` in the constructor declaration.

<iframe src="{{site.dartpadx}}?id=c400cb84fab309ddbbb436c1ced90dad"></iframe>

{% comment %}
TODO: Copy edit the hint.
{% endcomment %}

{% endcomment %}


## 常量构造函数

如果类创建的对象永远不会改变，那么可以定义这些对象为编译时常量。
此时，可以定义一个常量构造函数，并保证所有成员变量为 final 变量。

{% prettify dart %}
class ImmutablePoint {
  const ImmutablePoint(this.x, this.y);

  final int x;
  final int y;

  static const ImmutablePoint origin =
      ImmutablePoint(0, 0);
}
{% endprettify %}

### 实例代码

修改 `Recipe` 类，使其实例为常量，并创建一个执行以下操作的常量构造函数：

* 有三个参数：`ingredients`，`calories` 和 `milligramsOfSodium`（参数按此顺序排列）。
* 使用 `this` 语法自动将参数值分配给同名的对象属性。
* 是常量，在构造函数声明中的 `Recipe` 之前使用 `const` 关键字。

<iframe src="{{site.dartpadx}}?id=c400cb84fab309ddbbb436c1ced90dad"></iframe>

{% comment %}
TODO: Copy edit the hint.
{% endcomment %}

{% comment %}

## What next?

We hope you enjoyed using this codelab to learn or test your knowledge of
some of the most interesting features of the Dart language.
Here are some suggestions for what to do now:

* Try [other Dart codelabs](/codelabs).
* Read the [Dart language tour](/guides/language/language-tour).
* Play with [DartPad.]({{site.dartpad}})
* [Get the Dart SDK](/get-dart).

{% endcomment %}


## 下一步？

希望你能够喜欢使用此 Codelab 来学习和检测对 Dart 语言中一些最有趣的特性。
以下是接下来可以实践的一些建议：

* 尝试 [其他 Dart Codelab](/codelabs)。
* 阅读 [Dart 语言概览](/guides/language/language-tour)。
* 尝试 [DartPad]({{site.dartpad}})。
* [获取 Dart SDK](/get-dart)。

