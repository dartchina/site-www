---
title: Dart 语言速查
description: 总结一些 Dart 最有用、有趣的功能。
---

{% comment %}

This cheatsheet is based on an internal document
created by Googler [Mehmet Fidanboylu](https://medium.com/@mehmetf_71205)
to help Google engineers remember the syntax for
some of Dart's commonly used features.
For an interactive guide to these features and more, see the
[Dart cheatsheet codelab](/codelabs/dart-cheatsheet).

{% endcomment %}

本速查基于 Google 工程师 [Mehmet Fidanboylu](https://medium.com/@mehmetf_71205)
撰写的一份内部文档。该文档用来帮助 Google 工程师记忆一些 Dart 通用的语法功能。

有关这些功能的交互式指南，参见 [Dart Codelab 速查](/codelabs/dart-cheatsheet)。

{% comment %}

## Using literals

### `‘Substitution ${val}’`

Puts the value of `val` into a string literal.
Equivalent: `‘Substitution’ + val`

### `<type>[ ]`

Creates an object of type `List<type>`.
Equivalent: `new List<type>();`

### `const [1, 2, 3]`

Creates a compile-time constant list.

### `= { }`

Initializes a map.
Equivalent: `new Map<>();`

{% endcomment %}


## 字面量的使用

### `‘插值 ${val}’`

在字面量字符串中引入 `val` 的值。
等价于： `‘Substitution’ + val`

### `<type>[ ]`

创建一个 `List<type>` 类型的对象。
等价于：`new List<type>();`

### `const [1, 2, 3]`

创建一个编译时 List 常量。

### `= { }`

初始化一个 Map 。
等价于：`new Map<>();`

{% comment %}

## Declaring fields

| `var` | Generic `var` (dynamic) |
| `final` | Same as `var` but final |
| `const` | Constant |
{:.table}

{% endcomment %}


## 字段声明

| `var` | 一般 `var` (动态的) |
| `final` | 同 `var` 但仅能单次赋值 |
| `const` | 常量 |
{:.table}


{% comment %}

## Checking types

| `as` | Typecast |
| `is` | instanceof |
| `is!` | !instanceof |
{:.table}

{% endcomment %}


## 类型检查

| `as` | 类型转换 |
| `is` | 示例类型判断 |
| `is!` | 示例类型判断结果取反 |
{:.table}


{% comment %}

## Chaining method calls

### `a..b = true..c = 5;`

Cascade used for chaining access to methods and other members.
Equivalent: `a.b = true; a.c = 5;`

{% endcomment %}

## 链式方法调用

### `a..b = true..c = 5;`

使用级联来链接方法和访问其他成员。
等价于：`a.b = true; a.c = 5;`


{% comment %}

## Dealing with null

### `b ??= val;`

If `b` is null, assign the value of `val` to `b`;
otherwise, `b` stays the same.

### `a = value ?? 0;`

If value is null, set `a` to 0.
Otherwise, set `a` to value.

### `a?.b`

Conditional access.
Equivalent: `a == null ? null : a.b`

{% endcomment %}


## null 处理

### `b ??= val;`

如果 `b` 为 null ，设置 `b` 的值为 `val` ，
否则，保持 `b` 的原值。

### `a = value ?? 0;`

如果 value 的值为 null ，设置 `a` 为 0 。
否则，设置 `a` 为 value 。

### `a?.b`

条件访问。
等价于：`a == null ? null : a.b`


{% comment %}

## Implementing functions

### `fn({bool bold: false, bool hidden: false})`

Named params with default values.

### `int incr(int a) => a + 1;`

Single return statement can be abbreviated.

{% endcomment %}


## 函数实现

### `fn({bool bold: false, bool hidden: false})`

为命名参数设置默认值。

### `int incr(int a) => a + 1;`

可以简化单个返回语句。


{% comment %}

## Handling exceptions

```dart
try {...}
on MyException {...}
catch (e) {...}
finally {...}
```

Use `on` to catch a type.
Use `catch` to catch an instance.

{% endcomment %}


## 异常处理

```dart
try {...}
on MyException {...}
catch (e) {...}
finally {...}
```

通过 `on` 来捕获一种类型的异常。
通过 `catch` 来捕获异常的实例。


{% comment %}

## Implementing constructors

### Normal constructor

```dart
Point(this.x, this.y);
```

### Factory constructor

```dart
factory Point(int x, int y) => ...;
```

Use `factory` when implementing a constructor that
doesn’t always create a new instance.


### Named constructor

```dart
Point.fromJson(Map json) {
    x = json['x'];
    y = json['y'];
  }
```

### Delegating constructor

```dart
Point.alongXAxis(num x) : this(x, 0);
```

### Const constructor

```dart
const ImmutablePoint(this.x, this.y);
```

Produces an object that will never change. All vars have to be final.

### Initializer list

```dart
Point.fromJson(Map jsonMap)
      : x = jsonMap['x'], y = jsonMap['y'];
```

Initializer lists are handy when setting up final fields.

{% endcomment %}


## 构造函数实现

### 标准构造函数（Normal constructor）

```dart
Point(this.x, this.y);
```

### 工厂构造函数（Factory constructor）

```dart
factory Point(int x, int y) => ...;
```

构造函数不总是创建一个新的对象时，使用 `factory` 方式实现构造函数。


### 命名构造函数（Named constructor）

```dart
Point.fromJson(Map json) {
    x = json['x'];
    y = json['y'];
  }
```

### 代理构造函数（Delegating constructor）

```dart
Point.alongXAxis(num x) : this(x, 0);
```

### 常量构造函数（Const constructor）

```dart
const ImmutablePoint(this.x, this.y);
```

生成一个永远不会改变的对象。 这里所有的变量必须都是 final 。

### 初始化列表

```dart
Point.fromJson(Map jsonMap)
      : x = jsonMap['x'], y = jsonMap['y'];
```

设置的字段为 final 时，使用初始化程序列表会很便捷。
