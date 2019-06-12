---
title: "贡献者指北"
description: "Dart 编程语言中文版贡献者指北"
---

## 贡献者指北

本章意期望或已加入本站翻译的成员了解一下本站整体流程，有助于更快的参与到翻译贡献当中。
以下`中文译文`简称`译文`，`英文原文`简称`原文`。

## 中文排版指北

见：[中文排版指北](/about_zh_CN/chinese-copywriting-guidelines)。

## 译文仓库

译文仓库 [site-www-cn](https://github.com/dartchina/site-www-cn/tree/src_zh_CN)
Fork 于官方原文仓库 [site-www](https://github.com/dart-lang/site-www) 。

### 分支结构

|-----------------------------+-------------------------------------------|
| 分支名称                     | 分支描述                                    |
|-----------------------------+-------------------------------------------|
| `master`                    | 主分支
| `src_zh_CN`                 | 译文分支
| `1.x`                       | 原文 1.0 版本分支
| `2.2_src`                   | 原文 2.2 版本分支
| `2.2_src_zh_CN`             | 译文 2.2 版本分支
| `其他分支`                   | 错误修改，翻译任务及其他任务分支
{:.table}

#### master 分支

译文仓库的 master 分支不加入任何修改，仅用来合并官方原文仓库 master 分支，保持与官方同步。

#### src_zh_CN 分支

译文仓库 src_zh_CN 分支包括译文文件，经修改或增加的配置构建文件。

### 目录结构

#### src 目录

src 为原文文件夹。翻译不在该文件夹做任何操作或修改，文件夹内容保持与官网原文同步。
保持原始文件内容的目的是为了方便与已翻译译文内容进行对比，保持译文与原文版本同步。

#### src_zh_CN 目录

src_zh_CN 为译文文件夹。翻译译文在该文件夹中进行。src_zh_CN 文件夹由译文仓库创建，
初始 src_zh_CN 文件夹拷贝自 src 文件夹，文件数量及文件名称与 src 相同。进行翻译时
直接打开 src_zh_CN 文件夹下的原文文件，增加译文即可。


## 贡献及翻译

贡献及翻译的人员分两种角色：非成员和成员（在 github 上加入了 DartChina 组织的账户）。

### 非成员

#### 完整章节

非成员需要 Fork 本仓库，基于仓库 src_zh_CN 分支创建新分支，翻译完成后通过 PR 进行提交，
后由 DartChina 成员处理及合并。

#### 错误和 Issue

{% assign repo = page.repo | default: site.repo.this -%}
{% capture path -%} {{repo}}/tree/{{site.branch}}/{{site.source}}/{{page.path}} {%- endcapture -%}
{% assign title = page.title | default: page.url -%}
{% assign url = site.url | append: page.url -%}

{% capture issueTitle -%} title='{{title}}' page issue {%- endcapture -%}

{% assign nl = '%0D%0A' -%}
{% capture issueBody -%}body=
Page URL: {{url}}{{nl}}
Page source: {{path}}{{nl}}
{{nl}}
Found a typo? You can fix it yourself by going to the page source and clicking the pencil icon. Or finish creating this issue.{{nl}}
{{nl}}
Description of issue:
{%- endcapture -%}

如果页面存在错误或异议可点击当前页面的
<span class="btn-group" aria-label="Page GitHub links" role="group">
  <a href="{{path}}" class="btn no-automatic-external" title="View page source" target="_blank" rel="noopener">
    <i class="fas fa-file-alt fa-sm"></i>
  </a>
  <a href="{{repo}}/issues/new?{{issueTitle}}&{{issueBody}}" class="btn no-automatic-external" title="Report an issue with this page"
    target="_blank" rel="noopener">
    <i class="fas fa-bug fa-sm"></i>
  </a>
</span>
提交 Bug 或 Issue 。

### 成员

除可以通过非成员方式进行贡献外，还可以在原仓库 src_zh_CN 上创建新分支进行翻译贡献或错误更正。
在原仓库中创建分支应遵循分支命名规则。

#### 分支命名规则

分支名称应始终使用`小写`加`中划线`原则进行命名，如：`hj-tra-effective-dart-design` 。其中前两节意义固定：

- 第一节：成员简称，限两个字母
- 第二节：分支意图，限三个字母，以下列出可选意图简写
  - `tra` 文章翻译
  - `fix` 错误、歧义等问题的修改
  - `dev` 译文站点功能、配置开发等
  - `syn` 译文原文同步
- 第三节及更多：分支涉及的主题、内容或文件等，小节数量不限。

#### 示例解释：

`hj-tra-effective-dart-design` 示例解释：

|-----------------------------+-------------------------------------------|
| 小节内容                     | 说明                                       |
|-----------------------------+-------------------------------------------|
| `hj`                        | 成员简称
| `tra`                       | 分支意图 -- 文章翻译
| `effective-dart-design`     | 翻译内容为 effective-dart-design
{:.table}

### 增加译文

{% assign openTag = '{%' %}

贡献者需要使用 `{{ openTag }} comment %}` `{{ openTag }} endcomment %}` 注释的方式保留原文内容，
然后在被注释的原文后增加译文内容，其中 `{{ openTag }} comment %}` 注释语句的前面应空两行，后面空一行。
`{{ openTag }} endcomment %}` 注释语句的前面应空一行，后面空两行。
如：

```
{% assign openTag = '{%' %}
// 空两行
// 
{{ openTag }} comment %}    
// 空一行
English：Everything you can imagine is real.
// 空一行
{{ openTag }} endcomment %}
// 空两行
// 
中文：你能想象到的都是真实的。
```

<aside class="alert alert-info" markdown="1">
**提示：**
之所以采用注释保留原文，增加译文的方式进行文章翻译，目的是为了保持译文与官方原文的同步。
官方会频繁的对原文进行增加，删除和修改，注释并保留译文文件中的原文，有利于使用对比工具进行对比溯源，
从而减少译文同步所带来的负担，增加译文的可维护性。
这里常用的对比工具如：`BeyondCompare` ， `vscode + 对比插件` 等。
</aside>

