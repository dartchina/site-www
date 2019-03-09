    {% comment %}
    This file is generated from the other files in this directory.
    To re-generate it, please run the following command from root of
    the project:

      $ dart deploy/effective-dart-rules/bin/main.dart

    {% endcomment %}
    
<div class='effective_dart--summary_column' markdown='1'>

### Style


**标识符**

* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E4%BD%BF%E7%94%A8-uppercamelcase-%E9%A3%8E%E6%A0%BC%E5%91%BD%E5%90%8D%E7%B1%BB%E5%9E%8B'><strong>要</strong> 使用 <code>UpperCamelCase</code> 风格命名类型。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E5%9C%A8%E5%BA%93%E5%8C%85%E6%96%87%E4%BB%B6%E5%A4%B9%E6%BA%90%E6%96%87%E4%BB%B6%E4%B8%AD%E4%BD%BF%E7%94%A8-lowercase_with_underscores-%E6%96%B9%E5%BC%8F%E5%91%BD%E5%90%8D-do-name-libraries-and-source-files-using-lowercase_with_underscores'><strong>要</strong> 在<code>库</code>，<code>包</code>，<code>文件夹</code>，<code>源文件</code>中使用 <code>lowercase_with_underscores</code> 方式命名。 {#do-name-libraries-and-source-files-using-lowercase_with_underscores}</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E7%94%A8-lowercase_with_underscores-%E9%A3%8E%E6%A0%BC%E5%91%BD%E5%90%8D%E5%BA%93%E5%92%8C%E6%BA%90%E6%96%87%E4%BB%B6%E5%90%8D'><strong>要</strong> 用 <code>lowercase_with_underscores</code> 风格命名库和源文件名。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E4%BD%BF%E7%94%A8-lowercase_with_underscores-%E9%A3%8E%E6%A0%BC%E5%91%BD%E5%90%8D%E5%AF%BC%E5%85%A5%E7%9A%84%E5%89%8D%E7%BC%80'><strong>要</strong> 使用 <code>lowercase_with_underscores</code> 风格命名导入的前缀。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E4%BD%BF%E7%94%A8-lowercamelcase-%E9%A3%8E%E6%A0%BC%E6%9D%A5%E5%91%BD%E5%90%8D%E5%85%B6%E4%BB%96%E7%9A%84%E6%A0%87%E8%AF%86%E7%AC%A6'><strong>要</strong> 使用 <code>lowerCamelCase</code> 风格来命名其他的标识符。</a>
* <a href='/guides/language/effective-dart/style#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8-lowercamelcase-%E6%9D%A5%E5%91%BD%E5%90%8D%E5%B8%B8%E9%87%8F'><strong>推荐</strong> 使用 <code>lowerCamelCase</code> 来命名常量。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E6%8A%8A%E8%B6%85%E8%BF%87%E4%B8%A4%E4%B8%AA%E5%AD%97%E6%AF%8D%E7%9A%84%E9%A6%96%E5%AD%97%E6%AF%8D%E5%A4%A7%E5%86%99%E7%BC%A9%E7%95%A5%E8%AF%8D%E5%92%8C%E7%BC%A9%E5%86%99%E8%AF%8D%E5%BD%93%E5%81%9A%E4%B8%80%E8%88%AC%E5%8D%95%E8%AF%8D%E6%9D%A5%E5%AF%B9%E5%BE%85'><strong>要</strong> 把超过两个字母的首字母大写缩略词和缩写词当做一般单词来对待。</a>
* <a href='/guides/language/effective-dart/style#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8%E5%89%8D%E7%BC%80%E5%AD%97%E6%AF%8D'><strong>不要</strong> 使用前缀字母</a>

**顺序**

* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E6%8A%8A-dart-%E5%AF%BC%E5%85%A5%E8%AF%AD%E5%8F%A5%E6%94%BE%E5%88%B0%E5%85%B6%E4%BB%96%E5%AF%BC%E5%85%A5%E8%AF%AD%E5%8F%A5%E4%B9%8B%E5%89%8D'><strong>要</strong> 把 "dart:" 导入语句放到其他导入语句之前。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E6%8A%8A-package-%E5%AF%BC%E5%85%A5%E8%AF%AD%E5%8F%A5%E6%94%BE%E5%88%B0%E9%A1%B9%E7%9B%AE%E7%9B%B8%E5%85%B3%E5%AF%BC%E5%85%A5%E8%AF%AD%E5%8F%A5%E4%B9%8B%E5%89%8D'><strong>要</strong> 把 "package:" 导入语句放到项目相关导入语句之前。</a>
* <a href='/guides/language/effective-dart/style#%E6%8E%A8%E8%8D%90-%E6%8A%8A%E5%A4%96%E9%83%A8%E6%89%A9%E5%B1%95-package-%E5%AF%BC%E5%85%A5%E8%AF%AD%E5%8F%A5%E6%94%BE%E5%88%B0%E5%85%B6%E4%BB%96%E8%AF%AD%E5%8F%A5%E4%B9%8B%E5%89%8D'><strong>推荐</strong> 把外部扩展 "package:" 导入语句放到其他语句之前。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E6%8A%8A%E5%AF%BC%E5%87%BAexport%E8%AF%AD%E5%8F%A5%E4%BD%9C%E4%B8%BA%E4%B8%80%E4%B8%AA%E5%8D%95%E7%8B%AC%E7%9A%84%E9%83%A8%E5%88%86%E6%94%BE%E5%88%B0%E6%89%80%E6%9C%89%E5%AF%BC%E5%85%A5%E8%AF%AD%E5%8F%A5%E4%B9%8B%E5%90%8E'><strong>要</strong> 把导出（export）语句作为一个单独的部分放到所有导入语句之后。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E6%8C%89%E7%85%A7%E5%AD%97%E6%AF%8D%E9%A1%BA%E5%BA%8F%E6%9D%A5%E6%8E%92%E5%BA%8F%E6%AF%8F%E4%B8%AA%E9%83%A8%E5%88%86%E4%B8%AD%E7%9A%84%E8%AF%AD%E5%8F%A5'><strong>要</strong> 按照字母顺序来排序每个部分中的语句。</a>

**格式化**

* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E4%BD%BF%E7%94%A8-dartfmt-%E6%A0%BC%E5%BC%8F%E5%8C%96%E4%BD%A0%E7%9A%84%E4%BB%A3%E7%A0%81'><strong>要</strong> 使用 <code>dartfmt</code> 格式化你的代码。</a>
* <a href='/guides/language/effective-dart/style#%E8%80%83%E8%99%91-%E4%BF%AE%E6%94%B9%E4%BD%A0%E7%9A%84%E4%BB%A3%E7%A0%81%E8%AE%A9%E6%A0%BC%E5%BC%8F%E6%9B%B4%E5%8F%8B%E5%A5%BD'><strong>考虑</strong> 修改你的代码让格式更友好。</a>
* <a href='/guides/language/effective-dart/style#%E9%81%BF%E5%85%8D-%E5%8D%95%E8%A1%8C%E8%B6%85%E8%BF%87-80-%E4%B8%AA%E5%AD%97%E7%AC%A6'><strong>避免</strong> 单行超过 80 个字符。</a>
* <a href='/guides/language/effective-dart/style#%E8%A6%81-%E5%AF%B9%E6%89%80%E6%9C%89%E6%B5%81%E6%8E%A7%E5%88%B6%E7%BB%93%E6%9E%84%E4%BD%BF%E7%94%A8%E8%8A%B1%E6%8B%AC%E5%8F%B7'><strong>要</strong> 对所有流控制结构使用花括号。</a>

</div>
<div class='effective_dart--summary_column' markdown='1'>


### Documentation


**注释**

* <a href='/guides/language/effective-dart/documentation#%E8%A6%81-%E5%83%8F%E5%8F%A5%E5%AD%90%E4%B8%80%E6%A0%B7%E6%9D%A5%E6%A0%BC%E5%BC%8F%E5%8C%96%E6%B3%A8%E9%87%8A'><strong>要</strong> 像句子一样来格式化注释。</a>
* <a href='/guides/language/effective-dart/documentation#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8%E5%9D%97%E6%B3%A8%E9%87%8A%E4%BD%9C%E7%94%A8%E4%BD%9C%E8%A7%A3%E9%87%8A%E8%AF%B4%E6%98%8E'><strong>不要</strong> 使用块注释作用作解释说明。</a>

**文档注释**

* <a href='/guides/language/effective-dart/documentation#%E8%A6%81-%E4%BD%BF%E7%94%A8--%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A%E6%9D%A5%E6%B3%A8%E9%87%8A%E6%88%90%E5%91%98%E5%92%8C%E7%B1%BB%E5%9E%8B'><strong>要</strong> 使用 <code>///</code> 文档注释来注释成员和类型。</a>
* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E4%B8%BA%E5%85%AC%E5%BC%80%E5%8F%91%E5%B8%83%E7%9A%84-api-%E7%BC%96%E5%86%99%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A'><strong>推荐</strong> 为公开发布的 API 编写文档注释。</a>
* <a href='/guides/language/effective-dart/documentation#%E8%80%83%E8%99%91-%E7%BC%96%E5%86%99%E5%BA%93%E7%BA%A7%E5%88%ABlibrary-level%E7%9A%84%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A'><strong>考虑</strong> 编写库级别（library-level）的文档注释。</a>
* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E4%B8%BA%E7%A7%81%E6%9C%89api-%E7%BC%96%E5%86%99%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A'><strong>推荐</strong> 为私有API 编写文档注释。</a>
* <a href='/guides/language/effective-dart/documentation#%E8%A6%81-%E8%A6%81%E5%9C%A8%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A%E5%BC%80%E5%A4%B4%E6%9C%89%E4%B8%80%E4%B8%AA%E5%8D%95%E5%8F%A5%E6%80%BB%E7%BB%93'><strong>要</strong> 要在文档注释开头有一个单句总结。</a>
* <a href='/guides/language/effective-dart/documentation#%E8%A6%81-%E8%AE%A9%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A%E7%9A%84%E7%AC%AC%E4%B8%80%E5%8F%A5%E4%BB%8E%E6%AE%B5%E8%90%BD%E4%B8%AD%E5%88%86%E5%BC%80'><strong>要</strong> 让文档注释的第一句从段落中分开。</a>
* <a href='/guides/language/effective-dart/documentation#%E9%81%BF%E5%85%8D-%E4%B8%8E%E5%91%A8%E5%9B%B4%E4%B8%8A%E4%B8%8B%E6%96%87%E5%86%97%E4%BD%99'><strong>避免</strong> 与周围上下文冗余。</a>
* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E7%94%A8%E7%AC%AC%E4%B8%89%E4%BA%BA%E7%A7%B0%E6%9D%A5%E5%BC%80%E5%A7%8B%E5%87%BD%E6%95%B0%E6%88%96%E8%80%85%E6%96%B9%E6%B3%95%E7%9A%84%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A'><strong>推荐</strong> 用第三人称来开始函数或者方法的文档注释。</a>
* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E5%90%8D%E8%AF%8D%E7%9F%AD%E8%AF%AD%E6%9D%A5%E5%BC%80%E5%A7%8B%E5%8F%98%E9%87%8Fgettersetter-%E7%9A%84%E6%B3%A8%E9%87%8A'><strong>推荐</strong> 使用名词短语来开始变量、getter、setter 的注释。</a>
* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E5%90%8D%E8%AF%8D%E7%9F%AD%E8%AF%AD%E6%9D%A5%E5%BC%80%E5%A7%8B%E5%BA%93%E5%92%8C%E7%B1%BB%E5%9E%8B%E6%B3%A8%E9%87%8A'><strong>推荐</strong> 使用名词短语来开始库和类型注释。</a>
* <a href='/guides/language/effective-dart/documentation#%E8%80%83%E8%99%91-%E5%9C%A8%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A%E4%B8%AD%E6%B7%BB%E5%8A%A0%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81'><strong>考虑</strong> 在文档注释中添加示例代码。</a>
* <a href='/guides/language/effective-dart/documentation#%E8%A6%81-%E4%BD%BF%E7%94%A8%E6%96%B9%E6%8B%AC%E5%8F%B7%E5%9C%A8%E6%96%87%E6%A1%A3%E6%B3%A8%E9%87%8A%E4%B8%AD%E5%BC%95%E7%94%A8%E4%BD%9C%E7%94%A8%E5%9F%9F%E5%86%85%E7%9A%84%E6%A0%87%E8%AF%86%E7%AC%A6'><strong>要</strong> 使用方括号在文档注释中引用作用域内的标识符。</a>
* <a href='/guides/language/effective-dart/documentation#%E8%A6%81-%E4%BD%BF%E7%94%A8%E6%95%A3%E6%96%87%E7%9A%84%E6%96%B9%E5%BC%8F%E6%9D%A5%E6%8F%8F%E8%BF%B0%E5%8F%82%E6%95%B0%E8%BF%94%E5%9B%9E%E5%80%BC%E4%BB%A5%E5%8F%8A%E5%BC%82%E5%B8%B8%E4%BF%A1%E6%81%AF'><strong>要</strong> 使用散文的方式来描述参数、返回值以及异常信息。</a>
* <a href='/guides/language/effective-dart/documentation#%E8%A6%81-%E6%8A%8A%E6%B3%A8%E9%87%8A%E6%96%87%E6%A1%A3%E6%94%BE%E5%88%B0%E6%B3%A8%E8%A7%A3%E4%B9%8B%E5%89%8D'><strong>要</strong> 把注释文档放到注解之前。</a>

**Markdown**

* <a href='/guides/language/effective-dart/documentation#%E9%81%BF%E5%85%8D-%E8%BF%87%E5%BA%A6%E4%BD%BF%E7%94%A8-markdown'><strong>避免</strong> 过度使用 markdown。</a>
* <a href='/guides/language/effective-dart/documentation#%E9%81%BF%E5%85%8D-%E4%BD%BF%E7%94%A8-html-%E6%9D%A5%E6%A0%BC%E5%BC%8F%E5%8C%96%E6%96%87%E5%AD%97'><strong>避免</strong> 使用 HTML 来格式化文字。</a>
* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E5%8F%8D%E5%BC%95%E5%8F%B7%E6%A0%87%E6%B3%A8%E4%BB%A3%E7%A0%81'><strong>推荐</strong> 使用反引号标注代码。</a>

**如何写注释**

* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E7%AE%80%E6%B4%81'><strong>推荐</strong> 简洁.</a>
* <a href='/guides/language/effective-dart/documentation#%E9%81%BF%E5%85%8D-%E7%BC%A9%E5%86%99%E5%92%8C%E9%A6%96%E5%AD%97%E6%AF%8D%E7%BC%A9%E5%86%99%E8%AF%8D%E9%99%A4%E9%9D%9E%E5%BE%88%E5%B8%B8%E8%A7%81'><strong>避免</strong> 缩写和首字母缩写词，除非很常见。</a>
* <a href='/guides/language/effective-dart/documentation#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8-this-%E8%80%8C%E4%B8%8D%E6%98%AF-the-%E6%9D%A5%E5%BC%95%E7%94%A8%E5%AE%9E%E4%BE%8B%E6%88%90%E5%91%98'><strong>推荐</strong> 使用 "this" 而不是 "the" 来引用实例成员。</a>

</div>
<div style='clear:both'></div>
<div class='effective_dart--summary_column' markdown='1'>


### Usage


**库**

* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E5%9C%A8-part-of-%E4%B8%AD%E4%BD%BF%E7%94%A8%E5%AD%97%E7%AC%A6%E4%B8%B2'><strong>要</strong> 在 <code>part of</code> 中使用字符串。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E5%AF%BC%E5%85%A5-package-%E4%B8%AD-src-%E7%9B%AE%E5%BD%95%E4%B8%8B%E7%9A%84%E5%BA%93'><strong>不要</strong> 导入 package 中 <code>src</code> 目录下的库。</a>
* <a href='/guides/language/effective-dart/usage#%E5%BB%BA%E8%AE%AE-%E4%BD%BF%E7%94%A8%E7%9B%B8%E5%AF%B9%E8%B7%AF%E5%BE%84%E5%9C%A8%E5%AF%BC%E5%85%A5%E4%BD%A0%E8%87%AA%E5%B7%B1-package-%E4%B8%AD%E7%9A%84-lib-%E7%9B%AE%E5%BD%95'><strong>建议</strong> 使用相对路径在导入你自己 package 中的 <code>lib</code> 目录。</a>

**字符串**

* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E4%BD%BF%E7%94%A8%E4%B8%B4%E8%BF%91%E5%AD%97%E7%AC%A6%E5%AD%97%E7%9A%84%E6%96%B9%E5%BC%8F%E8%BF%9E%E6%8E%A5%E5%AD%97%E9%9D%A2%E9%87%8F%E5%AD%97%E7%AC%A6%E4%B8%B2'><strong>要</strong> 使用临近字符字的方式连接字面量字符串。</a>
* <a href='/guides/language/effective-dart/usage#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E6%8F%92%E5%80%BC%E7%9A%84%E5%BD%A2%E5%BC%8F%E6%9D%A5%E7%BB%84%E5%90%88%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%92%8C%E5%80%BC'><strong>推荐</strong> 使用插值的形式来组合字符串和值。</a>
* <a href='/guides/language/effective-dart/usage#%E9%81%BF%E5%85%8D-%E5%9C%A8%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%8F%92%E5%80%BC%E4%B8%AD%E4%BD%BF%E7%94%A8%E4%B8%8D%E5%BF%85%E8%A6%81%E7%9A%84%E5%A4%A7%E6%8B%AC%E5%8F%B7'><strong>避免</strong> 在字符串插值中使用不必要的大括号。</a>

**集合**

* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E5%B0%BD%E5%8F%AF%E8%83%BD%E7%9A%84%E4%BD%BF%E7%94%A8%E9%9B%86%E5%90%88%E5%AD%97%E9%9D%A2%E9%87%8F'><strong>要</strong> 尽可能的使用集合字面量。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8-length-%E6%9D%A5%E5%88%A4%E6%96%AD%E4%B8%80%E4%B8%AA%E9%9B%86%E5%90%88%E6%98%AF%E5%90%A6%E4%B8%BA%E7%A9%BA'><strong>不要</strong> 使用 <code>.length</code> 来判断一个集合是否为空。</a>
* <a href='/guides/language/effective-dart/usage#%E8%80%83%E8%99%91-%E4%BD%BF%E7%94%A8%E9%AB%98%E9%98%B6higher-order%E5%87%BD%E6%95%B0%E6%9D%A5%E8%BD%AC%E6%8D%A2%E9%9B%86%E5%90%88%E6%95%B0%E6%8D%AE'><strong>考虑</strong> 使用高阶（higher-order）函数来转换集合数据。</a>
* <a href='/guides/language/effective-dart/usage#%E9%81%BF%E5%85%8D-%E5%9C%A8-iterableforeach-%E4%B8%AD%E4%BD%BF%E7%94%A8%E5%AD%97%E9%9D%A2%E9%87%8F%E5%87%BD%E6%95%B0'><strong>避免</strong> 在 <code>Iterable.forEach()</code> 中使用字面量函数。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8-listfrom-%E9%99%A4%E9%9D%9E%E6%83%B3%E4%BF%AE%E6%94%B9%E7%BB%93%E6%9E%9C%E7%9A%84%E7%B1%BB%E5%9E%8B'><strong>不要</strong> 使用 <code>List.from()</code> 除非想修改结果的类型。</a>
* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E4%BD%BF%E7%94%A8-wheretype-%E6%8C%89%E7%B1%BB%E5%9E%8B%E8%BF%87%E6%BB%A4%E9%9B%86%E5%90%88'><strong>要</strong> 使用 <code>whereType()</code> 按类型过滤集合。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8-cast%E5%A6%82%E6%9E%9C%E6%9C%89%E6%9B%B4%E5%90%88%E9%80%82%E7%9A%84%E6%96%B9%E6%B3%95'><strong>不要</strong> 使用 <code>cast()</code>，如果有更合适的方法。</a>
* <a href='/guides/language/effective-dart/usage#%E9%81%BF%E5%85%8D-%E4%BD%BF%E7%94%A8-cast-'><strong>避免</strong> 使用 <code>cast()</code> 。</a>

**函数**

* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E4%BD%BF%E7%94%A8%E5%87%BD%E6%95%B0%E5%A3%B0%E6%98%8E%E7%9A%84%E6%96%B9%E5%BC%8F%E4%B8%BA%E5%87%BD%E6%95%B0%E7%BB%91%E5%AE%9A%E5%90%8D%E7%A7%B0'><strong>要</strong> 使用函数声明的方式为函数绑定名称。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8-lambda-%E8%A1%A8%E8%BE%BE%E5%BC%8F%E6%9D%A5%E6%9B%BF%E4%BB%A3-tear-off'><strong>不要</strong> 使用 lambda 表达式来替代 tear-off。</a>

**参数**

* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E4%BD%BF%E7%94%A8--%E6%9D%A5%E5%88%86%E9%9A%94%E5%8F%82%E6%95%B0%E5%90%8D%E5%92%8C%E5%8F%82%E6%95%B0%E9%BB%98%E8%AE%A4%E5%80%BC'><strong>要</strong> 使用 <code>=</code> 来分隔参数名和参数默认值。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E6%98%BE%E5%BC%8F%E7%9A%84%E4%B8%BA%E5%8F%82%E6%95%B0%E8%AE%BE%E7%BD%AE-null-%E5%80%BC'><strong>不要</strong> 显式的为参数设置 <code>null</code> 值。</a>

**变量**

* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E6%98%BE%E7%A4%BA%E7%9A%84%E4%B8%BA%E5%8F%82%E6%95%B0%E5%88%9D%E5%A7%8B%E5%8C%96-null-%E5%80%BC'><strong>不要</strong> 显示的为参数初始化 <code>null</code> 值。</a>
* <a href='/guides/language/effective-dart/usage#%E9%81%BF%E5%85%8D-%E4%BF%9D%E5%AD%98%E5%8F%AF%E8%AE%A1%E7%AE%97%E7%9A%84%E7%BB%93%E6%9E%9C'><strong>避免</strong> 保存可计算的结果。</a>

**成员**

* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%B8%BA%E5%AD%97%E6%AE%B5%E5%88%9B%E5%BB%BA%E4%B8%8D%E5%BF%85%E8%A6%81%E7%9A%84-getter-%E5%92%8C-setter-%E6%96%B9%E6%B3%95'><strong>不要</strong> 为字段创建不必要的 getter 和 setter 方法。</a>
* <a href='/guides/language/effective-dart/usage#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8-final-%E5%85%B3%E9%94%AE%E5%AD%97%E6%9D%A5%E5%88%9B%E5%BB%BA%E5%8F%AA%E8%AF%BB%E5%B1%9E%E6%80%A7'><strong>推荐</strong> 使用 <code>final</code> 关键字来创建只读属性。</a>
* <a href='/guides/language/effective-dart/usage#%E8%80%83%E8%99%91-%E5%AF%B9%E7%AE%80%E5%8D%95%E6%88%90%E5%91%98%E4%BD%BF%E7%94%A8--'><strong>考虑</strong> 对简单成员使用 <code>=&gt;</code> 。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8-this-%E5%9C%A8%E9%87%8D%E5%AE%9A%E5%90%91%E5%91%BD%E5%90%8D%E5%87%BD%E6%95%B0%E5%92%8C%E9%81%BF%E5%85%8D%E5%86%B2%E7%AA%81%E7%9A%84%E6%83%85%E5%86%B5%E4%B8%8B%E9%99%A4%E5%A4%96'><strong>不要</strong> 使用 <code>this.</code> ，在重定向命名函数和避免冲突的情况下除外。</a>
* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E5%B0%BD%E5%8F%AF%E8%83%BD%E7%9A%84%E5%9C%A8%E5%AE%9A%E4%B9%89%E5%8F%98%E9%87%8F%E7%9A%84%E6%97%B6%E5%80%99%E5%88%9D%E5%A7%8B%E5%8C%96%E5%8F%98%E9%87%8F%E5%80%BC'><strong>要</strong> 尽可能的在定义变量的时候初始化变量值。</a>

**构造函数**

* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E5%B0%BD%E5%8F%AF%E8%83%BD%E7%9A%84%E4%BD%BF%E7%94%A8%E5%88%9D%E5%A7%8B%E5%8C%96%E5%BD%A2%E5%BC%8F'><strong>要</strong> 尽可能的使用初始化形式。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E5%9C%A8%E5%88%9D%E5%A7%8B%E5%8C%96%E5%BD%A2%E5%BC%8F%E4%B8%AD%E5%81%9A%E7%B1%BB%E5%9E%8B%E6%B3%A8%E9%87%8A'><strong>不要</strong> 在初始化形式中做类型注释。</a>
* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E7%94%A8--%E6%9D%A5%E6%9B%BF%E4%BB%A3%E7%A9%BA%E7%9A%84%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E4%BD%93-'><strong>要</strong> 用 <code>;</code> 来替代空的构造函数体 <code>{}</code>。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8-new-'><strong>不要</strong> 使用 <code>new</code> 。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E5%86%97%E4%BD%99%E5%9C%B0%E4%BD%BF%E7%94%A8-const-'><strong>不要</strong> 冗余地使用 <code>const</code> 。</a>

**错误处理**

* <a href='/guides/language/effective-dart/usage#%E9%81%BF%E5%85%8D-%E4%BD%BF%E7%94%A8%E6%B2%A1%E6%9C%89-on-%E8%AF%AD%E5%8F%A5%E7%9A%84-catch'><strong>避免</strong> 使用没有 <code>on</code> 语句的 catch。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E4%B8%A2%E5%BC%83%E6%B2%A1%E6%9C%89%E4%BD%BF%E7%94%A8-on-%E8%AF%AD%E5%8F%A5%E6%8D%95%E8%8E%B7%E7%9A%84%E5%BC%82%E5%B8%B8'><strong>不要</strong> 丢弃没有使用 <code>on</code> 语句捕获的异常。</a>
* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E5%8F%AA%E5%9C%A8%E4%BB%A3%E8%A1%A8%E7%BC%96%E7%A8%8B%E9%94%99%E8%AF%AF%E7%9A%84%E6%83%85%E5%86%B5%E4%B8%8B%E6%89%8D%E6%8A%9B%E5%87%BA%E5%AE%9E%E7%8E%B0%E4%BA%86-error-%E7%9A%84%E5%BC%82%E5%B8%B8'><strong>要</strong> 只在代表编程错误的情况下才抛出实现了 <code>Error</code> 的异常。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E6%98%BE%E7%A4%BA%E7%9A%84%E6%8D%95%E8%8E%B7-error-%E6%88%96%E8%80%85%E5%85%B6%E5%AD%90%E7%B1%BB'><strong>不要</strong> 显示的捕获 <code>Error</code> 或者其子类。</a>
* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E4%BD%BF%E7%94%A8-rethrow-%E6%9D%A5%E9%87%8D%E6%96%B0%E6%8A%9B%E5%87%BA%E6%8D%95%E8%8E%B7%E7%9A%84%E5%BC%82%E5%B8%B8'><strong>要</strong> 使用 <code>rethrow</code> 来重新抛出捕获的异常。</a>

**异步**

* <a href='/guides/language/effective-dart/usage#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8-asyncawait-%E8%80%8C%E4%B8%8D%E6%98%AF%E7%9B%B4%E6%8E%A5%E4%BD%BF%E7%94%A8%E5%BA%95%E5%B1%82%E7%9A%84%E7%89%B9%E6%80%A7'><strong>推荐</strong> 使用 async/await 而不是直接使用底层的特性。</a>
* <a href='/guides/language/effective-dart/usage#%E4%B8%8D%E8%A6%81-%E5%9C%A8%E6%B2%A1%E6%9C%89%E6%9C%89%E7%94%A8%E6%95%88%E6%9E%9C%E7%9A%84%E6%83%85%E5%86%B5%E4%B8%8B%E4%BD%BF%E7%94%A8-async-'><strong>不要</strong> 在没有有用效果的情况下使用 <code>async</code> 。</a>
* <a href='/guides/language/effective-dart/usage#%E8%80%83%E8%99%91-%E4%BD%BF%E7%94%A8%E9%AB%98%E9%98%B6%E5%87%BD%E6%95%B0%E6%9D%A5%E8%BD%AC%E6%8D%A2%E4%BA%8B%E4%BB%B6%E6%B5%81stream'><strong>考虑</strong> 使用高阶函数来转换事件流（stream）</a>
* <a href='/guides/language/effective-dart/usage#%E9%81%BF%E5%85%8D-%E7%9B%B4%E6%8E%A5%E4%BD%BF%E7%94%A8-completer--'><strong>避免</strong> 直接使用 Completer  。</a>
* <a href='/guides/language/effective-dart/usage#%E8%A6%81-%E4%BD%BF%E7%94%A8-futuret-%E5%AF%B9-futureort-%E5%8F%82%E6%95%B0%E8%BF%9B%E8%A1%8C%E6%B5%8B%E8%AF%95%E4%BB%A5%E6%B6%88%E9%99%A4%E5%8F%82%E6%95%B0%E5%8F%AF%E8%83%BD%E6%98%AF-object-%E7%B1%BB%E5%9E%8B%E7%9A%84%E6%AD%A7%E4%B9%89'><strong>要</strong> 使用 <code>Future&lt;T&gt;</code> 对 <code>FutureOr&lt;T&gt;</code> 参数进行测试，以消除参数可能是 <code>Object</code> 类型的歧义。</a>

</div>
<div class='effective_dart--summary_column' markdown='1'>


### Design


**命名**

* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E4%BD%BF%E7%94%A8%E4%B8%80%E8%87%B4%E7%9A%84%E6%9C%AF%E8%AF%AD'><strong>要</strong> 使用一致的术语。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E7%BC%A9%E5%86%99'><strong>避免</strong> 缩写。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E6%8A%8A%E6%9C%80%E5%85%B7%E6%8F%8F%E8%BF%B0%E6%80%A7%E7%9A%84%E5%90%8D%E8%AF%8D%E6%94%BE%E5%88%B0%E6%9C%80%E5%90%8E'><strong>推荐</strong> 把最具描述性的名词放到最后。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E5%B0%BD%E9%87%8F%E8%AE%A9%E4%BB%A3%E7%A0%81%E7%9C%8B%E8%B5%B7%E6%9D%A5%E5%83%8F%E6%99%AE%E9%80%9A%E7%9A%84%E5%8F%A5%E5%AD%90'><strong>考虑</strong> 尽量让代码看起来像普通的句子。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E5%90%8D%E8%AF%8D%E7%9F%AD%E8%AF%AD%E6%9D%A5%E5%91%BD%E5%90%8D%E4%B8%8D%E6%98%AF%E5%B8%83%E5%B0%94%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%8F%98%E9%87%8F%E5%92%8C%E5%B1%9E%E6%80%A7'><strong>推荐</strong> 使用名词短语来命名不是布尔类型的变量和属性。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E9%9D%9E%E5%91%BD%E4%BB%A4%E5%BC%8F%E5%8A%A8%E8%AF%8D%E7%9F%AD%E8%AF%AD%E5%91%BD%E5%90%8D%E5%B8%83%E5%B0%94%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%8F%98%E9%87%8F%E5%92%8C%E5%B1%9E%E6%80%A7'><strong>推荐</strong> 使用非命令式动词短语命名布尔类型的变量和属性。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E7%9C%81%E7%95%A5%E5%91%BD%E5%90%8D%E5%B8%83%E5%B0%94%E5%8F%82%E6%95%B0%E7%9A%84%E5%8A%A8%E8%AF%8D'><strong>考虑</strong> 省略命名布尔<em>参数</em>的动词。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E4%B8%BA%E5%B8%83%E5%B0%94%E5%B1%9E%E6%80%A7%E6%88%96%E5%8F%98%E9%87%8F%E5%8F%96%E8%82%AF%E5%AE%9A%E5%90%AB%E4%B9%89%E7%9A%84%E5%90%8D%E5%AD%97'><strong>考虑</strong> 为布尔属性或变量取“肯定”含义的名字。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E5%91%BD%E4%BB%A4%E5%BC%8F%E5%8A%A8%E8%AF%8D%E7%9F%AD%E8%AF%AD%E6%9D%A5%E5%91%BD%E5%90%8D%E5%B8%A6%E6%9C%89%E5%89%AF%E4%BD%9C%E7%94%A8%E7%9A%84%E5%87%BD%E6%95%B0%E6%88%96%E8%80%85%E6%96%B9%E6%B3%95'><strong>推荐</strong> 使用命令式动词短语来命名带有副作用的函数或者方法。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E4%BD%BF%E7%94%A8%E5%90%8D%E8%AF%8D%E7%9F%AD%E8%AF%AD%E6%88%96%E8%80%85%E9%9D%9E%E5%91%BD%E4%BB%A4%E5%BC%8F%E5%8A%A8%E8%AF%8D%E7%9F%AD%E8%AF%AD%E5%91%BD%E5%90%8D%E8%BF%94%E5%9B%9E%E6%95%B0%E6%8D%AE%E4%B8%BA%E4%B8%BB%E8%A6%81%E5%8A%9F%E8%83%BD%E7%9A%84%E6%96%B9%E6%B3%95%E6%88%96%E8%80%85%E5%87%BD%E6%95%B0'><strong>考虑</strong> 使用名词短语或者非命令式动词短语命名返回数据为主要功能的方法或者函数。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E4%BD%BF%E7%94%A8%E5%91%BD%E4%BB%A4%E5%BC%8F%E5%8A%A8%E8%AF%8D%E7%9F%AD%E8%AF%AD%E5%91%BD%E5%90%8D%E4%B8%80%E4%B8%AA%E5%87%BD%E6%95%B0%E6%88%96%E6%96%B9%E6%B3%95%E8%8B%A5%E6%9E%9C%E4%BD%A0%E5%B8%8C%E6%9C%9B%E5%AE%83%E7%9A%84%E6%89%A7%E8%A1%8C%E8%83%BD%E8%A2%AB%E9%87%8D%E8%A7%86'><strong>考虑</strong> 使用命令式动词短语命名一个函数或方法，若果你希望它的执行能被重视。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%9C%A8%E6%96%B9%E6%B3%95%E5%91%BD%E5%90%8D%E4%B8%AD%E4%BD%BF%E7%94%A8-get-%E5%BC%80%E5%A4%B4'><strong>避免</strong> 在方法命名中使用 <code>get</code> 开头。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8-to___-%E6%9D%A5%E5%91%BD%E5%90%8D%E6%8A%8A%E5%AF%B9%E8%B1%A1%E7%9A%84%E7%8A%B6%E6%80%81%E8%BD%AC%E6%8D%A2%E5%88%B0%E4%B8%80%E4%B8%AA%E6%96%B0%E7%9A%84%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%87%BD%E6%95%B0'><strong>推荐</strong> 使用 <code>to___()</code> 来命名把对象的状态转换到一个新的对象的函数。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8-as___-%E6%9D%A5%E5%91%BD%E5%90%8D%E6%8A%8A%E5%8E%9F%E6%9D%A5%E5%AF%B9%E8%B1%A1%E8%BD%AC%E6%8D%A2%E4%B8%BA%E5%8F%A6%E5%A4%96%E4%B8%80%E7%A7%8D%E8%A1%A8%E7%8E%B0%E5%BD%A2%E5%BC%8F%E7%9A%84%E5%87%BD%E6%95%B0'><strong>推荐</strong> 使用 <code>as___()</code> 来命名把原来对象转换为另外一种表现形式的函数。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%9C%A8%E6%96%B9%E6%B3%95%E6%88%96%E8%80%85%E5%87%BD%E6%95%B0%E5%90%8D%E7%A7%B0%E4%B8%AD%E6%8F%8F%E8%BF%B0%E5%8F%82%E6%95%B0'><strong>避免</strong> 在方法或者函数名称中描述参数。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E5%9C%A8%E5%91%BD%E5%90%8D%E5%8F%82%E6%95%B0%E6%97%B6%E9%81%B5%E5%BE%AA%E7%8E%B0%E6%9C%89%E7%9A%84%E5%8A%A9%E8%AE%B0%E7%AC%A6%E7%BA%A6%E5%AE%9A'><strong>要</strong> 在命名参数时，遵循现有的助记符约定。</a>

**库**

* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8%E7%A7%81%E6%9C%89%E5%A3%B0%E6%98%8E'><strong>推荐</strong> 使用私有声明。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E5%A3%B0%E6%98%8E%E5%A4%9A%E4%B8%AA%E7%B1%BB%E5%9C%A8%E4%B8%80%E4%B8%AA%E5%BA%93%E4%B8%AD'><strong>考虑</strong> 声明多个类在一个库中。</a>

**类**

* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E9%81%BF%E5%85%8D%E4%B8%BA%E4%BA%86%E4%BD%BF%E7%94%A8%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84%E5%87%BD%E6%95%B0%E8%80%8C%E5%8E%BB%E5%AE%9A%E4%B9%89%E4%B8%80%E4%B8%AA%E5%8D%95%E4%B8%80%E6%88%90%E5%91%98%E7%9A%84%E6%8A%BD%E8%B1%A1%E7%B1%BB'><strong>避免</strong> 避免为了使用一个简单的函数而去定义一个单一成员的抽象类</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%AE%9A%E4%B9%89%E4%BB%85%E5%8C%85%E5%90%AB%E9%9D%99%E6%80%81%E6%88%90%E5%91%98%E7%9A%84%E7%B1%BB'><strong>避免</strong> 定义仅包含静态成员的类。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E9%9B%86%E6%88%90%E4%B8%80%E4%B8%AA%E4%B8%8D%E6%9C%9F%E6%9C%9B%E8%A2%AB%E9%9B%86%E6%88%90%E7%9A%84%E7%B1%BB'><strong>避免</strong> 集成一个不期望被集成的类。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E6%8A%8A%E8%83%BD%E5%A4%9F%E7%BB%A7%E6%89%BF%E7%9A%84%E8%AF%B4%E6%98%8E%E6%B7%BB%E5%8A%A0%E5%88%B0%E6%96%87%E6%A1%A3%E4%B8%AD%E5%A6%82%E6%9E%9C%E8%BF%99%E4%B8%AA%E7%B1%BB%E5%8F%AF%E4%BB%A5%E7%BB%A7%E6%89%BF'><strong>要</strong> 把能够继承的说明添加到文档中，如果这个类可以继承。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%8E%BB%E5%AE%9E%E7%8E%B0%E4%B8%80%E4%B8%AA%E4%B8%8D%E6%9C%9F%E6%9C%9B%E6%88%90%E4%B8%BA%E6%8E%A5%E5%8F%A3%E7%9A%84%E7%B1%BB%E8%AF%A5%E7%B1%BB%E4%B8%8D%E6%83%B3%E4%BD%9C%E4%B8%BA%E6%8E%A5%E5%8F%A3%E8%A2%AB%E5%AE%9E%E7%8E%B0'><strong>避免</strong> 去实现一个不期望成为接口的类（该类不想作为接口被实现）。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E5%AF%B9%E6%94%AF%E6%8C%81%E6%8E%A5%E5%8F%A3%E7%9A%84%E7%B1%BB%E5%9C%A8%E6%96%87%E6%A1%A3%E6%B3%A8%E6%98%8E'><strong>要</strong> 对支持接口的类在文档注明</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%8E%BB-mixin-%E4%B8%80%E4%B8%AA%E4%B8%8D%E6%9C%9F%E6%9C%9B%E8%A2%AB-mixin-%E7%9A%84%E7%B1%BB'><strong>避免</strong> 去 mixin 一个不期望被 mixin 的类</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E5%AF%B9%E6%94%AF%E6%8C%81-mixin-%E7%9A%84%E7%B1%BB%E5%9C%A8%E6%96%87%E6%A1%A3%E6%B3%A8%E6%98%8E'><strong>要</strong> 对支持 mixin 的类在文档注明</a>

**构造函数**

* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E5%9C%A8%E7%B1%BB%E6%94%AF%E6%8C%81%E7%9A%84%E6%83%85%E5%86%B5%E4%B8%8B%E6%8C%87%E5%AE%9A%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E4%B8%BA--const'><strong>考虑</strong> 在类支持的情况下，指定构造函数为  <code>const</code>。</a>

**成员**

* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E6%8C%87%E5%AE%9A%E5%AD%97%E6%AE%B5%E6%88%96%E9%A1%B6%E7%BA%A7%E5%8F%98%E9%87%8F%E4%B8%BA-final-'><strong>推荐</strong> 指定字段或顶级变量为 <code>final</code> 。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E5%AF%B9%E6%A6%82%E5%BF%B5%E4%B8%8A%E6%98%AF%E8%AE%BF%E9%97%AE%E7%9A%84%E5%B1%9E%E6%80%A7%E4%BD%BF%E7%94%A8-getter-%E6%96%B9%E6%B3%95'><strong>要</strong> 对概念上是访问的属性使用 getter 方法。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E5%AF%B9%E6%A6%82%E5%BF%B5%E4%B8%8A%E6%98%AF%E4%BF%AE%E6%94%B9%E7%9A%84%E5%B1%9E%E6%80%A7%E4%BD%BF%E7%94%A8-setter-%E6%96%B9%E6%B3%95'><strong>要</strong> 对概念上是修改的属性使用 setter 方法。</a>
* <a href='/guides/language/effective-dart/design#%E4%B8%8D%E8%A6%81-%E5%9C%A8%E6%B2%A1%E6%9C%89%E5%AF%B9%E5%BA%94%E7%9A%84-getter-%E7%9A%84%E6%83%85%E5%86%B5%E4%B8%8B%E5%AE%9A%E4%B9%89-setter'><strong>不要</strong> 在没有对应的 getter 的情况下定义 setter。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E4%BB%8E%E8%BF%94%E5%9B%9E%E7%B1%BB%E5%9E%8B%E4%B8%BA-bool--double--int-%E6%88%96-num-%E7%9A%84%E6%88%90%E5%91%98%E8%BF%94%E5%9B%9E-null-'><strong>避免</strong> 从返回类型为 <code>bool</code> ， <code>double</code> ， <code>int</code> 或 <code>num</code> 的成员返回 <code>null</code> 。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E4%B8%BA%E4%BA%86%E4%B9%A6%E5%86%99%E6%B5%81%E7%95%85%E8%80%8C%E4%BB%8E%E6%96%B9%E6%B3%95%E4%B8%AD%E8%BF%94%E5%9B%9E-this-'><strong>避免</strong> 为了书写流畅，而从方法中返回 <code>this</code> 。</a>

**类型**

* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%B8%BA%E7%B1%BB%E5%9E%8B%E4%B8%8D%E6%98%8E%E6%98%BE%E7%9A%84%E5%85%AC%E5%85%B1%E5%AD%97%E6%AE%B5%E5%92%8C%E5%85%AC%E5%85%B1%E9%A1%B6%E7%BA%A7%E5%8F%98%E9%87%8F%E6%8C%87%E5%AE%9A%E7%B1%BB%E5%9E%8B%E6%B3%A8%E8%A7%A3'><strong>推荐</strong> 为类型不明显的公共字段和公共顶级变量指定类型注解。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E4%B8%BA%E7%B1%BB%E5%9E%8B%E4%B8%8D%E6%98%8E%E6%98%BE%E7%9A%84%E7%A7%81%E6%9C%89%E5%AD%97%E6%AE%B5%E5%92%8C%E7%A7%81%E6%9C%89%E9%A1%B6%E7%BA%A7%E5%8F%98%E9%87%8F%E6%8C%87%E5%AE%9A%E7%B1%BB%E5%9E%8B%E6%B3%A8%E8%A7%A3'><strong>考虑</strong> 为类型不明显的私有字段和私有顶级变量指定类型注解。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E4%B8%BA%E5%88%9D%E5%A7%8B%E5%8C%96%E7%9A%84%E5%B1%80%E9%83%A8%E5%8F%98%E9%87%8F%E6%B7%BB%E5%8A%A0%E7%B1%BB%E5%9E%8B%E6%B3%A8%E8%A7%A3'><strong>避免</strong> 为初始化的局部变量添加类型注解。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%9C%A8%E5%87%BD%E6%95%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F%E4%B8%8A%E6%B3%A8%E8%A7%A3%E6%8E%A8%E6%96%AD%E7%9A%84%E5%8F%82%E6%95%B0%E7%B1%BB%E5%9E%8B'><strong>避免</strong> 在函数表达式上注解推断的参数类型。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%9C%A8%E6%B3%9B%E5%9E%8B%E8%B0%83%E7%94%A8%E4%B8%AD%E5%8F%82%E6%95%B0%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%86%97%E4%BD%99%E4%BD%BF%E7%94%A8'><strong>避免</strong> 在泛型调用中参数类型的冗余使用。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E5%9C%A8-dart-%E6%8E%A8%E6%96%AD%E7%B1%BB%E5%9E%8B%E9%94%99%E8%AF%AF%E7%9A%84%E6%97%B6%E5%80%99%E8%BF%9B%E8%A1%8C%E7%B1%BB%E5%9E%8B%E6%B3%A8%E8%A7%A3'><strong>要</strong> 在 Dart 推断类型错误的时候进行类型注解。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF%E7%94%A8-dynamic-%E6%B3%A8%E8%A7%A3%E6%9B%BF%E6%8D%A2%E6%8E%A8%E6%96%AD%E5%A4%B1%E8%B4%A5%E7%9A%84%E6%83%85%E5%86%B5'><strong>推荐</strong> 使用 <code>dynamic</code> 注解替换推断失败的情况。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BD%BF-function-%E7%B1%BB%E5%9E%8B%E6%B3%A8%E8%A7%A3%E7%9A%84%E7%89%B9%E5%BE%81%E6%9B%B4%E6%98%8E%E6%98%BE'><strong>推荐</strong> 使 function 类型注解的特征更明显</a>
* <a href='/guides/language/effective-dart/design#%E4%B8%8D%E8%A6%81-%E4%B8%BA-setter-%E6%96%B9%E6%B3%95%E6%8C%87%E5%AE%9A%E8%BF%94%E5%9B%9E%E7%B1%BB%E5%9E%8B'><strong>不要</strong> 为 setter 方法指定返回类型。</a>
* <a href='/guides/language/effective-dart/design#%E4%B8%8D%E8%A6%81-%E4%BD%BF%E7%94%A8%E5%BC%83%E7%94%A8%E7%9A%84-typedef-%E8%AF%AD%E6%B3%95'><strong>不要</strong> 使用弃用的 typedef 语法。</a>
* <a href='/guides/language/effective-dart/design#%E6%8E%A8%E8%8D%90-%E4%BC%98%E5%85%88%E4%BD%BF%E7%94%A8%E5%86%85%E8%81%94%E5%87%BD%E6%95%B0%E7%B1%BB%E5%9E%8B%E8%80%8C%E5%90%8E%E6%98%AF-typedef-'><strong>推荐</strong> 优先使用内联函数类型，而后是 typedef 。</a>
* <a href='/guides/language/effective-dart/design#%E8%80%83%E8%99%91-%E5%9C%A8%E5%8F%82%E6%95%B0%E4%B8%8A%E4%BD%BF%E7%94%A8%E5%87%BD%E6%95%B0%E7%B1%BB%E5%9E%8B%E8%AF%AD%E6%B3%95'><strong>考虑</strong> 在参数上使用函数类型语法。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E4%B8%BA%E7%B1%BB%E5%9E%8B%E6%98%AF%E4%BB%BB%E4%BD%95%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%8F%82%E6%95%B0%E4%BD%BF%E7%94%A8-object-%E6%B3%A8%E8%A7%A3%E8%80%8C%E4%B8%8D%E6%98%AF-dynamic-'><strong>要</strong> 为类型是任何对象的参数使用 <code>Object</code> 注解，而不是 <code>dynamic</code> 。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E4%BD%BF%E7%94%A8-futurevoid-%E4%BD%9C%E4%B8%BA%E6%97%A0%E6%B3%95%E5%9B%9E%E5%80%BC%E5%BC%82%E6%AD%A5%E6%88%90%E5%91%98%E7%9A%84%E8%BF%94%E5%9B%9E%E7%B1%BB%E5%9E%8B'><strong>要</strong> 使用 <code>Future&lt;void&gt;</code> 作为无法回值异步成员的返回类型。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E4%BD%BF%E7%94%A8-futureort-%E4%BD%9C%E4%B8%BA%E8%BF%94%E5%9B%9E%E7%B1%BB%E5%9E%8B'><strong>避免</strong> 使用 <code>FutureOr&lt;T&gt;</code> 作为返回类型。</a>

**参数**

* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%B8%83%E5%B0%94%E7%B1%BB%E5%9E%8B%E7%9A%84%E4%BD%8D%E7%BD%AE%E5%8F%82%E6%95%B0'><strong>避免</strong> 布尔类型的位置参数。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%9C%A8%E8%B0%83%E7%94%A8%E8%80%85%E9%9C%80%E8%A6%81%E7%9C%81%E7%95%A5%E5%89%8D%E9%9D%A2%E5%8F%82%E6%95%B0%E7%9A%84%E6%96%B9%E6%B3%95%E4%B8%AD%E4%BD%BF%E7%94%A8%E4%BD%8D%E7%BD%AE%E5%8F%AF%E9%80%89%E5%8F%82%E6%95%B0'><strong>避免</strong> 在调用者需要省略前面参数的方法中，使用位置可选参数。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E5%BC%BA%E5%88%B6%E5%8F%82%E6%95%B0%E5%8E%BB%E6%8E%A5%E5%8F%97%E4%B8%80%E4%B8%AA%E7%89%B9%E5%AE%9A%E8%A1%A8%E7%A4%BA%E7%A9%BA%E5%8F%82%E6%95%B0%E7%9A%84%E5%80%BC'><strong>避免</strong> 强制参数去接受一个特定表示"空参数"的值。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E4%BD%BF%E7%94%A8%E5%BC%80%E5%A7%8B%E4%B8%BA%E9%97%AD%E5%8C%BA%E9%97%B4%E7%BB%93%E6%9D%9F%E4%B8%BA%E5%BC%80%E5%8C%BA%E9%97%B4%E7%9A%84%E5%8D%8A%E5%BC%80%E5%8D%8A%E9%97%AD%E5%8C%BA%E9%97%B4%E4%BD%9C%E4%B8%BA%E6%8E%A5%E5%8F%97%E8%8C%83%E5%9B%B4'><strong>要</strong> 使用开始为闭区间，结束为开区间的半开半闭区间作为接受范围。</a>

**相等**

* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E5%AF%B9%E9%87%8D%E5%86%99--%E6%93%8D%E4%BD%9C%E7%AC%A6%E7%9A%84%E7%B1%BB%E9%87%8D%E5%86%99-hashcode-%E6%96%B9%E6%B3%95'><strong>要</strong> 对重写 <code>==</code> 操作符的类，重写 <code>hashCode</code> 方法。</a>
* <a href='/guides/language/effective-dart/design#%E8%A6%81-%E8%AE%A9--%E6%93%8D%E4%BD%9C%E7%AC%A6%E7%9A%84%E7%9B%B8%E7%AD%89%E9%81%B5%E5%AE%88%E6%95%B0%E5%AD%A6%E8%A7%84%E5%88%99'><strong>要</strong> 让 <code>==</code> 操作符的相等遵守数学规则。</a>
* <a href='/guides/language/effective-dart/design#%E9%81%BF%E5%85%8D-%E4%B8%BA%E5%8F%AF%E5%8F%98%E7%B1%BB%E8%87%AA%E5%AE%9A%E4%B9%89%E7%9B%B8%E7%AD%89'><strong>避免</strong> 为可变类自定义相等。</a>
* <a href='/guides/language/effective-dart/design#%E4%B8%8D%E8%A6%81-%E5%9C%A8%E8%87%AA%E5%AE%9A%E4%B9%89--%E6%93%8D%E4%BD%9C%E7%AC%A6%E4%B8%AD%E6%A3%80%E6%9F%A5-null-'><strong>不要</strong> 在自定义 <code>==</code> 操作符中检查 <code>null</code> 。</a>

</div>
<div style='clear:both'></div>
