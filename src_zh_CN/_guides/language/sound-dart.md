---
title: Dart 类型系统
description: 如何编写健全的 Dart 代码。
---
<?code-excerpt replace="/([A-Z]\w*)\d\b/$1/g; /\b(main)\d\b/$1/g"?>


{% comment %}

The Dart language is type safe: it uses a combination of static type checking and
[runtime checks](#runtime-checks) to
ensure that a variable's value always matches the variable's static type.
Although _types_ are mandatory, type _annotations_ are optional
because of [type inference](#type-inference).

This page concentrates on the type safety features added in Dart 2.
For a full introduction to the Dart language, including types, see the
[language tour](/guides/language/language-tour).

<aside class="alert alert-info" markdown="1">
  **Terminology note:**
  The terms **sound** Dart and **type safe** Dart
  are often used interchangeably.
  You might also see the term **strong mode**.
  Strong mode was an opt-in Dart 1.x feature
  that provided partial support for type safety.
</aside>

One benefit of static type checking is the ability to find bugs
at compile time using Dart's [static analyzer.][analysis]

You can fix most static analysis errors by adding type annotations to generic
classes. The most common generic classes are the collection types
`List<T>` and `Map<K,V>`.

For example, in the following code the `printInts()` function prints an integer list,
and `main()` creates a list and passes it to `printInts()`.

{:.fails-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (opening-example)" replace="/list(?=\))/[!$&!]/g"?>
{% prettify dart %}
void printInts(List<int> a) => print(a);

void main() {
  var list = [];
  list.add(1);
  list.add("2");
  printInts([!list!]);
}
{% endprettify %}

The preceding code results in a type error on `list` (highlighted
above) at the call of `printInts(list)`:

{:.console-output}
<?code-excerpt "strong/analyzer-2-results.txt" retain="/List.*strong_analysis.*argument_type_not_assignable/" replace="/ at (lib|test)\/\w+\.dart:\d+:\d+//g"?>
```nocode
error • The argument type 'List' can't be assigned to the parameter type 'List<int>' • argument_type_not_assignable
```

The error highlights an unsound implicit cast from `List<dynamic>` to `List<int>`.
The `list` variable has static type `List<dynamic>`. This is because the
initializing declaration `var list = []` doesn't provide the analyzer with
enough information for it to infer a type argument more specific than `dynamic`.
The `printInts()` function expects a parameter of type `List<int>`,
causing a mismatch of types.

When adding a type annotation (`<int>`) on creation of the list
(highlighted below) the analyzer complains that a string argument can't be assigned to
an `int` parameter. Removing the quotes in `list.add("2")` results
in code that passes static analysis and runs with no errors or warnings.

{:.passes-sa}
<?code-excerpt "strong/test/strong_test.dart (opening-example)" replace="/<int.(?=\[)|2/[!$&!]/g"?>
{% prettify dart %}
void printInts(List<int> a) => print(a);

void main() {
  var list = [!<int>!][];
  list.add(1);
  list.add([!2!]);
  printInts(list);
}
{% endprettify %}

{% comment %}
  Note: DartPad does not yet support no-implicit-casts, but it does
  report a runtime type error.
{% endcomment -%}

[Try it in DartPad]({{site.dartpad}}/f64e963cb5f894e2146c2b28d5efa4ed).

{% endcomment %}

Dart 类型安全的语言：Dart 使用静态类型检查和
[运行时检查](#runtime-checks)
的组合来确保变量的值始终与变量的静态类型匹配。尽管类型是必需的，但由于
[类型推断](#type-inference)
，类型的注释是可选的。

本章重点介绍 Dart 2 中添加的类型安全功能。有关 Dart 语言的完整介绍（包括类型），
请参阅[语言概览](/guides/language/language-tour)。

<aside class="alert alert-info" markdown="1">
  **术语说明：**
  术语 **sound** Dart 和 **type safe** Dart 通常可互换使用。
  你可能还会看到术语 **strong mode** 。 
  **strong mode** 是一种在Dart 1.x中可选的功能，
  可为类型安全提供部分支持。
</aside>

静态类型检查的一个好处是能够使用 Dart 的
[静态分析器][analysis]
在编译时找到错误。

可以向泛型类添加类型注释来修复大多数静态分析错误。最常见的泛型类是集合类型 `List<T>` 和 `Map<K,V>` 。

例如，在下面的代码中，`main()` 创建一个列表并将其传递给 `printInts()` ，由 `printInts()` 函数打印这个整数列表。

{:.fails-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (opening-example)" replace="/list(?=\))/[!$&!]/g"?>
{% prettify dart %}
void printInts(List<int> a) => print(a);

void main() {
  var list = [];
  list.add(1);
  list.add("2");
  printInts([!list!]);
}
{% endprettify %}

上面的代码在调用 `printInts(list)` 时会在 `list` （高亮提示）上产生类型错误：

{:.console-output}
<?code-excerpt "strong/analyzer-2-results.txt" retain="/List.*strong_analysis.*argument_type_not_assignable/" replace="/ at (lib|test)\/\w+\.dart:\d+:\d+//g"?>
```nocode
error • The argument type 'List' can't be assigned to the parameter type 'List<int>' • argument_type_not_assignable
```

高亮错误是因为产生了从 `List<dynamic>` 到 `List<int>` 的不正确的隐式转换。
`list` 变量是 `List<dynamic>` 静态类型。这是因为 `list` 变量的初始化声明 `var list = []`
没有为分析器提供足够的信息来推断比 `dynamic` 更具体的类型参数。
`printInts()` 函数需要 `List<int>` 类型的参数，因此导致类型不匹配。

在创建 `list` 时添加类型注释 `<int>`（代码中高亮显示部分）后，分析器会提示无法将字符串参数分配给 `int` 参数。
删除 `list.add("2")` 中的字符串引号使代码通过静态分析并能够正常执行。

{:.passes-sa}
<?code-excerpt "strong/test/strong_test.dart (opening-example)" replace="/<int.(?=\[)|2/[!$&!]/g"?>
{% prettify dart %}
void printInts(List<int> a) => print(a);

void main() {
  var list = [!<int>!][];
  list.add(1);
  list.add([!2!]);
  printInts(list);
}
{% endprettify %}

{% comment %}
  Note: DartPad does not yet support no-implicit-casts, but it does
  report a runtime type error.
{% endcomment -%}

[尝试在 DartPad 中练习]({{site.dartpad}}/f64e963cb5f894e2146c2b28d5efa4ed).


{% comment %}

## What is soundness?

*Soundness* is about ensuring your program can't get into certain
invalid states. A sound *type system* means you can never get into
a state where an expression evaluates to a value that doesn't match
the expression's static type. For example, if an expression's static
type is `String`, at runtime you are guaranteed to only get a string
when you evaluate it.

Dart's type system, like the type systems in Java and C#, is sound. It
enforces that soundness using a combination of static checking
(compile-time errors) and runtime checks. For example, assigning a `String`
to `int` is a compile-time error. Casting an `Object` to a string using
`as String` fails with a runtime error if the object isn't a
string.

{% endcomment %}


## 什么是类型安全

类型安全是为了确保程序不会进入某些无效状态。
安全类型系统意味着程序永远不会进入表达式求值为与表达式的静态类型不匹配的值的状态。
例如，如果表达式的静态类型是 `String` ，则在运行时保证在评估它的时候只会获取字符串。

Dart 的类型系统，同 Java 和 C＃ 中的类型系统类似，是安全的。
它使用静态检查（编译时错误）和运行时检查的组合来强制执行类型安全。
例如，将 `String` 分配给 `int` 是一个编译时错误。如果`对象`不是字符串，
使用 `as String` 将`对象`转换为字符串时，会由于运行时错误而导致转换失败。


{% comment %}

## The benefits of soundness

A sound type system has several benefits:

* Revealing type-related bugs at compile time.<br>
  A sound type system forces code to be unambiguous about its types,
  so type-related bugs that might be tricky to find at runtime are
  revealed at compile time.

* More readable code.<br>
  Code is easier to read because you can rely on a value actually having
  the specified type. In sound Dart, types can't lie.

* More maintainable code.<br>
  With a sound type system, when you change one piece of code, the
  type system can warn you about the other pieces
  of code that just broke.

* Better ahead of time (AOT) compilation.<br>
  While AOT compilation is possible without types, the generated
  code is much less efficient.

{% endcomment %}


## 类型安全的好处

安全类型系统有以下几个好处：

* 在编译时就可以检查并显示类型相关的错误。<br>
  安全类型系统强制要求代码明确类型，
  因此在编译时会显示与类型相关的错误，
  这些错误可能在运行时可能很难发现。

* 代码更容易阅读。<br>
  代码更容易阅读，因为我们信赖一个拥有指定类型的值。
  在类型安全的 Dart 中，类型是不会骗人的。 因为一个拥有指定类型的值是可以被信赖的。

* 代码可维护性更高。<br>
  在安全类型系统下，当更改一处代码后，
  类型系统会警告因此影响到的其他代码块。

* 更好的 AOT 编译。<br>
  虽然在没有类型的情况下可以进行 AOT 编译，
  但生成的代码效率要低很多。


{% comment %}

## Tips for passing static analysis

Most of the rules for static types are easy to understand.
Here are some of the less obvious rules:

* Use sound return types when overriding methods.
* Use sound parameter types when overriding methods.
* Don't use a dynamic list as a typed list.

Let's see these rules in detail, with examples that use the following
type hierarchy:

<img src="images/type-hierarchy.png" alt="a hierarchy of animals where the supertype is Animal and the subtypes are Alligator, Cat, and HoneyBadger. Cat has the subtypes of Lion and MaineCoon">

<a name="use-proper-return-types"></a>
### Use sound return types when overriding methods

The return type of a method in a subclass must be the same type or a
subtype of the return type of the method in the superclass. Consider
the getter method in the Animal class:

<?code-excerpt "strong/lib/animal.dart (Animal)" replace="/Animal get.*/[!$&!]/g"?>
{% prettify dart %}
class Animal {
  void chase(Animal a) { ... }
  [!Animal get parent => ...!]
}
{% endprettify %}

The `parent` getter method returns an Animal. In the HoneyBadger subclass,
you can replace the getter's return type with HoneyBadger (or any other subtype
of Animal), but an unrelated type is not allowed.

{:.passes-sa}
<?code-excerpt "strong/lib/animal.dart (HoneyBadger)" replace="/(\w+)(?= get)/[!$&!]/g"?>
{% prettify dart %}
class HoneyBadger extends Animal {
  void chase(Animal a) { ... }
  [!HoneyBadger!] get parent => ...
}
{% endprettify %}

{:.fails-sa}
<?code-excerpt "strong/lib/animal_bad.dart (HoneyBadger)" replace="/(\w+)(?= get)/[!$&!]/g"?>
{% prettify dart %}
class HoneyBadger extends Animal {
  void chase(Animal a) { ... }
  [!Root!] get parent => ...
}
{% endprettify %}

<a name="use-proper-param-types"></a>
### Use sound parameter types when overriding methods

The parameter of an overridden method must have either the same type
or a supertype of the corresponding parameter in the superclass.
Don't "tighten" the parameter type by replacing the type with a
subtype of the original parameter.

<aside class="alert alert-info" markdown="1">
  **Note:** If you have a valid reason to use a subtype, you can use the
  [`covariant` keyword](/guides/language/sound-problems#the-covariant-keyword).
</aside>

Consider the `chase(Animal)` method for the Animal class:

<?code-excerpt "strong/lib/animal.dart (Animal)" replace="/void chase.*/[!$&!]/g"?>
{% prettify dart %}
class Animal {
  [!void chase(Animal a) { ... }!]
  Animal get parent => ...
}
{% endprettify %}

The `chase()` method takes an Animal. A HoneyBadger chases anything.
It's OK to override the `chase()` method to take anything (Object).

{:.passes-sa}
<?code-excerpt "strong/lib/animal.dart (chase-Object)" replace="/Object/[!$&!]/g"?>
{% prettify dart %}
class HoneyBadger extends Animal {
  void chase([!Object!] a) { ... }
  Animal get parent => ...
}
{% endprettify %}

The following code tightens the parameter on the `chase()` method
from Animal to Mouse, a subclass of Animal.

{:.fails-sa}
<?code-excerpt "strong/lib/animal_bad.dart (chase-Mouse)" replace="/(\w+)(?= x)/[!$&!]/g"?>
{% prettify dart %}
class Mouse extends Animal {...}

class Cat extends Animal {
  void chase([!Mouse!] x) { ... }
}
{% endprettify %}

This code is not type safe because it would then be possible to define
a cat and send it after an alligator:

<?code-excerpt "strong/lib/animal_bad.dart (chase-Alligator)" replace="/Alligator/[!$&!]/g"?>
{% prettify dart %}
Animal a = Cat();
a.chase([!Alligator!]()); // Not type safe or feline safe
{% endprettify %}

{% endcomment %}


## 静态检查中的一些技巧

大多数静态类型的规则都很容易理解。
下面是一些不太明显的规则：

* 重写方法时，使用安全类型的返回值。
* 重写方法时，使用安全类型的参数。
* 不要将动态类型的 List 看做是有类型的 List 。

让我们通过下面示例的类型结构，来更深入的了解这些规则：

<img src="images/type-hierarchy.png" alt="a hierarchy of animals where the supertype is Animal and the subtypes are Alligator, Cat, and HoneyBadger. Cat has the subtypes of Lion and MaineCoon">

<a name="use-proper-return-types"></a>
### 重写方法时，使用安全类型的返回值

子类方法中返回值类型必须与父类方法中返回值类型的类型相同或其子类型。
考虑 Animal 类中的 Getter 方法：

<?code-excerpt "strong/lib/animal.dart (Animal)" replace="/Animal get.*/[!$&!]/g"?>
{% prettify dart %}
class Animal {
  void chase(Animal a) { ... }
  [!Animal get parent => ...!]
}
{% endprettify %}

`父类` Getter 方法返回一个 Animal 。在 HoneyBadger 子类中，
可以使用 HoneyBadger（或 Animal 的任何其他子类型）替换 Getter 的返回值类型，
但不允许使用其他的无关类型。

{:.passes-sa}
<?code-excerpt "strong/lib/animal.dart (HoneyBadger)" replace="/(\w+)(?= get)/[!$&!]/g"?>
{% prettify dart %}
class HoneyBadger extends Animal {
  void chase(Animal a) { ... }
  [!HoneyBadger!] get parent => ...
}
{% endprettify %}

{:.fails-sa}
<?code-excerpt "strong/lib/animal_bad.dart (HoneyBadger)" replace="/(\w+)(?= get)/[!$&!]/g"?>
{% prettify dart %}
class HoneyBadger extends Animal {
  void chase(Animal a) { ... }
  [!Root!] get parent => ...
}
{% endprettify %}

<a name="use-proper-param-types"></a>
### 重写方法时，使用安全类型的参数。

子类方法的参数必须与父类方法中参数的类型相同或是其参数的父类型。
不要使用原始参数的子类型，替换原有类型，这样会导致参数类型"收紧"。

<aside class="alert alert-info" markdown="1">
  **提示：** 如果有合理的理由使用子类型，可以使用 [`covariant` 关键字](/guides/language/sound-problems#the-covariant-keyword)。
</aside>

考虑 Animal 的 `chase(Animal)` 方法：

<?code-excerpt "strong/lib/animal.dart (Animal)" replace="/void chase.*/[!$&!]/g"?>
{% prettify dart %}
class Animal {
  [!void chase(Animal a) { ... }!]
  Animal get parent => ...
}
{% endprettify %}

`chase()` 方法的参数类型是 Animal 。一个 HoneyBadger 可以追逐任何东西。
因此可以在重写 `chase()` 方法时将参数类型指定为任意类型 （Object） 。

{:.passes-sa}
<?code-excerpt "strong/lib/animal.dart (chase-Object)" replace="/Object/[!$&!]/g"?>
{% prettify dart %}
class HoneyBadger extends Animal {
  void chase([!Object!] a) { ... }
  Animal get parent => ...
}
{% endprettify %}

Mouse 是 Animal 的子类，下面的代码将 `chase()` 方法中参数的范围从 Animal 缩小到 Mouse 。

{:.fails-sa}
<?code-excerpt "strong/lib/animal_bad.dart (chase-Mouse)" replace="/(\w+)(?= x)/[!$&!]/g"?>
{% prettify dart %}
class Mouse extends Animal {...}

class Cat extends Animal {
  void chase([!Mouse!] x) { ... }
}
{% endprettify %}

下面的代码不是类型安全的，因为 a 可以是一个 cat 对象，却可以给它传入一个 alligator 对象。

<?code-excerpt "strong/lib/animal_bad.dart (chase-Alligator)" replace="/Alligator/[!$&!]/g"?>
{% prettify dart %}
Animal a = Cat();
a.chase([!Alligator!]()); // Not type safe or feline safe
{% endprettify %}


### 不要将动态类型的 List 看做是有类型的 List 

当期望在一个 List 中可以包含不同类型的对象时，动态列表是很好的选择。
但是不能将动态类型的 List 看做是有类型的 List 。

这个规则也适用于泛型类型的实例。

下面代码创建一个 Dog 的动态 List ，并将其分配给 Cat 类型的 List ，
表达式在静态分析期间会产生错误。

{:.fails-sa}
<?code-excerpt "strong/lib/animal_bad.dart (dynamic-list)" replace="/.dynamic.(?!.*OK)/[!$&!]/g"?>
{% prettify dart %}
class Cat extends Animal { ... }

class Dog extends Animal { ... }

void main() {
  List<Cat> foo = [!<dynamic>!][Dog()]; // Error
  List<dynamic> bar = <dynamic>[Dog(), Cat()]; // OK
}
{% endprettify %}


{% comment %}

## Runtime checks

Runtime checks in tools like the [Dart VM][] and [dartdevc][]
deal with type safety issues that the analyzer can't catch.

For example, the following code throws an exception at runtime because it is an error
to assign a list of Dogs to a list of Cats:

{:.runtime-fail}
<?code-excerpt "strong/test/strong_test.dart (runtime-checks)" replace="/cats[^;]*/[!$&!]/g"?>
{% prettify dart %}
void main() {
  List<Animal> animals = [Dog()];
  List<Cat> [!cats = animals!];
}
{% endprettify %}

{% endcomment %}


## 运行时检查

运行时检查工具，比如 [Dart VM][] 和 [dartdevc][]，
处理分析器无法捕获的类型安全问题。

例如，以下代码在运行时会抛出异常，
因为将 Dog 类型的 List 赋值给 Cat 类型的 List 是错误的：

{:.runtime-fail}
<?code-excerpt "strong/test/strong_test.dart (runtime-checks)" replace="/cats[^;]*/[!$&!]/g"?>
{% prettify dart %}
void main() {
  List<Animal> animals = [Dog()];
  List<Cat> [!cats = animals!];
}
{% endprettify %}


{% comment %}

## Type inference

The analyzer can infer types for fields, methods, local variables,
and most generic type arguments.
When the analyzer doesn't have enough information to infer
a specific type, it uses the `dynamic` type.

Here's an example of how type inference works with generics.
In this example, a variable named `arguments` holds a map that
pairs string keys with values of various types.

If you explicitly type the variable, you might write this:

<?code-excerpt "strong/lib/strong_analysis.dart (type-inference-1-orig)" replace="/Map<String, dynamic\x3E/[!$&!]/g"?>
{% prettify dart %}
[!Map<String, dynamic>!] arguments = {'argA': 'hello', 'argB': 42};
{% endprettify %}

Alternatively, you can use `var` and let Dart infer the type:

<?code-excerpt "strong/lib/strong_analysis.dart (type-inference-1)" replace="/var/[!$&!]/g"?>
{% prettify dart %}
[!var!] arguments = {'argA': 'hello', 'argB': 42}; // Map<String, Object>
{% endprettify %}

The map literal infers its type from its entries,
and then the variable infers its type from the map literal's type.
In this map, the keys are both strings, but the values have different
types (String and int, which have the upper bound Object).
So the map literal has the type `Map<String, Object>`,
and so does the `arguments` variable.

{% endcomment %}


## 类型推断

分析器（analyzer）可以推断字段，方法，局部变量和大多数泛型类型参数的类型。
当分析器没有足够的信息来推断出一个特定类型时，会使用 `dynamic` 作为类型。

下面是在泛型中如何进行类型推断的示例。在此示例中，名为 `arguments` 的变量包含一个 Map ，
该 Map 将字符串键与各种类型的值配对。

如果显式键入变量，则可以这样写：

<?code-excerpt "strong/lib/strong_analysis.dart (type-inference-1-orig)" replace="/Map<String, dynamic\x3E/[!$&!]/g"?>
{% prettify dart %}
[!Map<String, dynamic>!] arguments = {'argA': 'hello', 'argB': 42};
{% endprettify %}

或者，使用 `var` 让 Dart 来推断类型：

<?code-excerpt "strong/lib/strong_analysis.dart (type-inference-1)" replace="/var/[!$&!]/g"?>
{% prettify dart %}
[!var!] arguments = {'argA': 'hello', 'argB': 42}; // Map<String, Object>
{% endprettify %}

Map 字面量从其条目中推断出它的类型，然后变量从 Map 字面量的类型中推断出它的类型。
在此 Map 中，键都是字符串，但值具有不同的类型（ String 和 int ，它们具有共同的上限类型 Object ）。
因此，Map 字面量的类型为 `Map<String, Object>` ，也就是 `arguments` 的类型。


{% comment %}

### Field and method inference

A field or method that has no specified type and that overrides
a field or method from the superclass, inherits the type of the
superclass method or field.

A field that does not have a declared or inherited type but that is declared
with an initial value, gets an inferred type based on the initial value.

{% endcomment %}


### 字段和方法推断


重写父类的且没有指定类型的字段或方法，继承父类中字段或方法的类型。

没有声明类型且不存在继承类型的字段，如果在声明时被初始化，
那么字段的类型为初始化值的类型。

{% comment %}

### Static field inference

Static fields and variables get their types inferred from their
initializer. Note that inference fails if it encounters a cycle
(that is, inferring a type for the variable depends on knowing the
type of that variable).

{% endcomment %}


### 静态字段推断

静态字段和变量的类型从其初始化程序中推断获得。 
需要注意的是，如果推断是个循环，推断会失败
（也就是说，推断变量的类型取决于知道该变量的类型）。


{% comment %}

### Local variable inference

Local variable types are inferred from their initializer, if any.
Subsequent assignments are not taken into account.
This may mean that too precise a type may be inferred.
If so, you can add a type annotation.

{:.fails-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (local-var-type-inference-error)"?>
{% prettify dart %}
var x = 3; // x is inferred as an int
x = 4.0;
{% endprettify %}

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (local-var-type-inference-ok)"?>
{% prettify dart %}
num y = 3; // a num can be double or int
y = 4.0;
{% endprettify %}

{% endcomment %}


### 局部变量推断

在不考虑连续赋值的情况下，局部变量如果有初始化值的情况下，其类型是从初始化值推断出来的。
这可能意味着推断出来的类型会非常严格。
如果是这样，可以为他们添加类型注释。（🤔 This may mean that too precise a type may be inferred.
If so, you can add a type annotation.）

{:.fails-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (local-var-type-inference-error)"?>
{% prettify dart %}
var x = 3; // x is inferred as an int
x = 4.0;
{% endprettify %}

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (local-var-type-inference-ok)"?>
{% prettify dart %}
num y = 3; // a num can be double or int
y = 4.0;
{% endprettify %}


{% comment %}

### Type argument inference

Type arguments to constructor calls and
[generic method](/guides/language/language-tour#using-generic-methods) invocations are
inferred based on a combination of downward information from the context
of occurrence, and upward information from the arguments to the constructor
or generic method. If inference is not doing what you want or expect,
you can always explicitly specify the type arguments.

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (type-arg-inference)"?>
{% prettify dart %}
// Inferred as if you wrote <int>[].
List<int> listOfInt = [];

// Inferred as if you wrote <double>[3.0].
var listOfDouble = [3.0];

// Inferred as Iterable<int>
var ints = listOfDouble.map((x) => x.toInt());
{% endprettify %}

In the last example, `x` is inferred as `double` using downward information.
The return type of the closure is inferred as `int` using upward information.
Dart uses this return type as upward information when inferring the `map()`
method's type argument: `<int>`.

{% endcomment %}


### 参数类型推断

构造函数调用的类型参数和
[泛型方法](/guides/language/language-tour#using-generic-methods)调用
是根据上下文的向下信息和构造函数或泛型方法的参数的向上信息组合推断的。
如果推断没有按照意愿或期望进行，那么你可以显式的指定他们的参数类型。

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (type-arg-inference)"?>
{% prettify dart %}
// Inferred as if you wrote <int>[].
List<int> listOfInt = [];

// Inferred as if you wrote <double>[3.0].
var listOfDouble = [3.0];

// Inferred as Iterable<int>
var ints = listOfDouble.map((x) => x.toInt());
{% endprettify %}

在最后一个示例中，根据向下信息 `x` 被推断为 `double` 。 闭包的返回类型根据向上信息推断为 `int` 。
在推断 `map()` 方法的类型参数：`<int>` 时，Dart 使用此返回值的类型作为向上信息。


{% comment %}

## Substituting types

When you override a method, you are replacing something of one type (in the
old method) with something that might have a new type (in the new method).
Similarly, when you pass an argument to a function,
you are replacing something that has one type (a parameter
with a declared type) with something that has another type
(the actual argument). When can you replace something that
has one type with something that has a subtype or a supertype?

When substituting types, it helps to think in terms of _consumers_
and _producers_. A consumer absorbs a type and a producer generates a type.

**You can replace a consumer's type with a supertype and a producer's
type with a subtype.**

Let's look at examples of simple type assignment and assignment with
generic types.

{% endcomment %}


## 替换类型

当重写方法时，可以使用一个新类型（在新方法中）替换旧类型（在旧方法中）。
类似地，当参数传递给函数时，可以使用另一种类型（实际参数）的对象替换现有类型（具有声明类型的参数）要求的对象。
什么时候可以用具有子类型或父类型的对象替换具有一种类型的对象那？

从_消费者_和_生产者_的角度有助于我们思考替换类型的情况。
消费者接受类型，生产者产生类型。

**可以使用父类型替换消费者类型，使用子类型替换生产者类型。**

下面让我们看一下普通类型赋值和泛型类型赋值的示例。


{% comment %}

### Simple type assignment

When assigning objects to objects, when can you replace a type with a
different type? The answer depends on whether the object is a consumer
or a producer.

Consider the following type hierarchy:

<img src="images/type-hierarchy.png" alt="a hierarchy of animals where the supertype is Animal and the subtypes are Alligator, Cat, and HoneyBadger. Cat has the subtypes of Lion and MaineCoon">

Consider the following simple assignment where `Cat c` is a _consumer_ and `Cat()`
is a _producer_:

<?code-excerpt "strong/lib/strong_analysis.dart (Cat-Cat-ok)"?>
{% prettify dart %}
Cat c = Cat();
{% endprettify %}

In a consuming position, it's safe to replace something that consumes a
specific type (`Cat`) with something that consumes anything (`Animal`),
so replacing `Cat c` with `Animal c` is allowed, because Animal is
a supertype of Cat.

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (Animal-Cat-ok)"?>
{% prettify dart %}
Animal c = Cat();
{% endprettify %}

But replacing `Cat c` with `MaineCoon c` breaks type safety, because the
superclass may provide a type of Cat with different behaviors, such
as Lion:

{:.fails-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (MaineCoon-Cat-err)"?>
{% prettify dart %}
MaineCoon c = Cat();
{% endprettify %}

In a producing position, it's safe to replace something that produces a
type (Cat) with a more specific type (MaineCoon). So, the following
is allowed:

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (Cat-MaineCoon-ok)"?>
{% prettify dart %}
Cat c = MaineCoon();
{% endprettify %}

{% endcomment %}


### 普通类型赋值

将对象赋值给对象时，什么时候可以用其他类型替换当前类型？
答案取决于对象是消费者还是生产者。

分析以下类型层次结构：

<img src="images/type-hierarchy.png" alt="a hierarchy of animals where the supertype is Animal and the subtypes are Alligator, Cat, and HoneyBadger. Cat has the subtypes of Lion and MaineCoon">

思考下面示例中的普通赋值，其中 `Cat c` 是_消费者_而 `Cat()` 是_生产者_：

<?code-excerpt "strong/lib/strong_analysis.dart (Cat-Cat-ok)"?>
{% prettify dart %}
Cat c = Cat();
{% endprettify %}

在消费者的位置，任意类型（`Animal`）的对象替换特定类型（`Cat`）的对象是安全的。
因此使用 `Animal c` 替换 `Cat c` 是允许的，因为 Animal 是 Cat 的父类。

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (Animal-Cat-ok)"?>
{% prettify dart %}
Animal c = Cat();
{% endprettify %}

但是使用 `MaineCoon c` 替换 `Cat c` 会打破类型的安全性，
因为父类可能会提供一种具有不同行为的 Cat ，例如 Lion ：

{:.fails-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (MaineCoon-Cat-err)"?>
{% prettify dart %}
MaineCoon c = Cat();
{% endprettify %}

在生产者的位置，可以安全地将生产类型 (Cat) 替换成一个更具体的类型 （MaineCoon）的对象。
因此，下面的操作是允许的：

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (Cat-MaineCoon-ok)"?>
{% prettify dart %}
Cat c = MaineCoon();
{% endprettify %}


{% comment %}

### Generic type assignment

Are the rules the same for generic types? Yes. Consider the hierarchy
of lists of animals&mdash;a List of Cat is a subtype of a List of
Animal, and a supertype of a List of MaineCoon:

<img src="images/type-hierarchy-generics.png" alt="List<Animal> -> List<Cat> -> List<MaineCoon>">

In the following example, you can assign a `MaineCoon` list to `myCats` because
`List<MaineCoon>` is a subtype of `List<Cat>`:

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (generic-type-assignment-MaineCoon)" replace="/MaineCoon/[!$&!]/g"?>
{% prettify dart %}
List<Cat> myCats = List<[!MaineCoon!]>();
{% endprettify %}

{% comment %}
Gist:  https://gist.github.com/4a2a9bc2242042ba5338533d091213c0
DartPad: {{site.dartpad}}/4a2a9bc2242042ba5338533d091213c0

[Try it in DartPad]({{site.dartpad}}/4a2a9bc2242042ba5338533d091213c0).
{% endcomment %}

What about going in the other direction? Can you assign an `Animal` list to a `List<Cat>`?

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (generic-type-assignment-Animal)" replace="/Animal/[!$&!]/g"?>
{% prettify dart %}
List<Cat> myCats = List<[!Animal!]>();
{% endprettify %}

This assignment passes static analysis,
but it creates an implicit cast. It is equivalent to:

<?code-excerpt "strong/lib/strong_analysis.dart (generic-type-assignment-implied-cast)" replace="/as.*(?=;)/[!$&!]/g"?>
{% prettify dart %}
List<Cat> myCats = List<Animal>() [!as List<Cat>!];
{% endprettify %}

The code may fail at runtime. You can disallow implicit casts
by specifying `implicit-casts: false` in the [analysis options file.][analysis_options.yaml]

{% endcomment %}


### 泛型赋值

上面的规则同样适用于泛型类型吗？是的。
考虑动物列表的层次结构&mdash; Cat 类型的 List 是 Animal 类型 List 的子类型，
是 MaineCoon 类型 List 的父类型。

<img src="images/type-hierarchy-generics.png" alt="List<Animal> -> List<Cat> -> List<MaineCoon>">

在下面的示例中，可以将 `MaineCoon` 类型的 List 赋值给 `myCats` ，
因为 `List<MaineCoon>` 是 `List<Cat>` 的子类型：

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (generic-type-assignment-MaineCoon)" replace="/MaineCoon/[!$&!]/g"?>
{% prettify dart %}
List<Cat> myCats = List<[!MaineCoon!]>();
{% endprettify %}

{% comment %}
Gist:  https://gist.github.com/4a2a9bc2242042ba5338533d091213c0
DartPad: {{site.dartpad}}/4a2a9bc2242042ba5338533d091213c0

[Try it in DartPad]({{site.dartpad}}/4a2a9bc2242042ba5338533d091213c0).
{% endcomment %}

从另一个角度看？可以将 `Animal` 类型的 List 赋值给 `List<Cat>` 吗？

{:.passes-sa}
<?code-excerpt "strong/lib/strong_analysis.dart (generic-type-assignment-Animal)" replace="/Animal/[!$&!]/g"?>
{% prettify dart %}
List<Cat> myCats = List<[!Animal!]>();
{% endprettify %}

上面的赋值通过了静态分析，但它进行了隐式的强制转换。上面的赋值相当于：

<?code-excerpt "strong/lib/strong_analysis.dart (generic-type-assignment-implied-cast)" replace="/as.*(?=;)/[!$&!]/g"?>
{% prettify dart %}
List<Cat> myCats = List<Animal>() [!as List<Cat>!];
{% endprettify %}

代码在运行时可能会执行失败。通过在 [静态分析配置文件][analysis_options.yaml] 
中指定 `implicit-casts: false` 来禁止隐式强制转换。


{% comment %}

### Methods

When overriding a method, the producer and consumer rules still apply.
For example:

<img src="images/consumer-producer-methods.png" alt="Animal class showing the chase method as the consumer and the parent getter as the producer">

For a consumer (such as the `chase(Animal)` method), you can replace
the parameter type with a supertype. For a producer (such as
the `parent` getter method), you can replace the return type with
a subtype.

For more information, see
[Use sound return types when overriding methods](#use-proper-return-types)
and [Use sound parameter types when overriding methods](#use-proper-param-types).

{% endcomment %}


### 方法

在重写方法中，生产者和消费者规则仍然适用。例如：

<img src="images/consumer-producer-methods.png" alt="Animal class showing the chase method as the consumer and the parent getter as the producer">

对于使用者（例如 `chase(Animal)` 方法），可以使用父类型替换参数类型。
对于生产者（例如 `父类` 的 Getter 方法），可以使用子类型替换返回值类型。

有关更多信息，请参阅
[重写方法时，使用安全类型的返回值](#use-proper-return-types)
以及
[重写方法时，使用安全类型的参数](#use-proper-param-types)。


{% comment %}

## Other resources

The following resources have further information on sound Dart:

* [Fixing common type problems](/guides/language/sound-problems) -
  Errors you may encounter when
  writing sound Dart code, and how to fix them.
* [Dart 2](/dart-2) - How to update Dart 1.x code to Dart 2.
* [Customizing static analysis][analysis] - How
  to set up and customize the analyzer and linter using an analysis
  options file.


[analysis_options.yaml]: /guides/language/analysis-options
[analysis]: /guides/language/analysis-options
[Dart VM]: /server/tools/dart-vm
[dartdevc]: /tools/dartdevc
[strong mode]: /guides/language/sound-dart#how-to-enable-strong-mode

{% endcomment %}


## 其他资源

以下是更多关于 Dart 类型安全的相关资源：

* [修复常见类型问题](/guides/language/sound-problems) -
  编写安全类型的 Dart 代码时可能遇到的错误，
  以及解决错误的方法。
* [Dart 2](/dart-2) - 如何从 Dart 1.x 代码迁移到 Dart 2 。
* [Customizing static analysis][analysis] - 如何使用
  分析配置文件设置及自定义分析器和 linter 。


[analysis_options.yaml]: /guides/language/analysis-options
[analysis]: /guides/language/analysis-options
[Dart VM]: /server/tools/dart-vm
[dartdevc]: /tools/dartdevc
[strong mode]: /guides/language/sound-dart#how-to-enable-strong-mode


