---
title: "关于"
description: "关于 Dart 编程语言中文版"
toc: false
---

## Dart 编程语言中文版

Dart 编程语言中文版（以下称为`中文版`）源于对 Dart 官方 [dart.dev](https://dart.dev) 英文官方版本（以下称为`英文版`）的翻译。目前 Dart 官方使用该翻译的版本做为 [dart.dev](https://dart.dev) 的中文版本。
- `中文版` github 地址：[site-www-cn](https://github.com/dartchina/site-www-cn)。
- `英文版` github 地址：[site-www](https://github.com/dart-lang/site-www) 。

`中文版` 的翻译出于个人学习及兴趣，同时也希望 `中文版` 的翻译能够帮助大家更加轻松的了解和学习 Dart 。

## 贡献

这里欢迎您一起来为 Dart 在国内推广贡献力量，如果您有兴趣翻译文档或期望成为 DartChina 中的一员，请加微信: `gunavy2009` （添加好友时，请填写验证备注）。
具体贡献方式及规则，详见：[贡献者指北](/about_zh_CN/contributor-guide)。

## 报错

如果您发现错误，您可以通过以下方式反馈：

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

1. 页面错误可点击当前页面的
<span class="btn-group" aria-label="Page GitHub links" role="group">
  <a href="{{path}}" class="btn no-automatic-external" title="View page source" target="_blank" rel="noopener">
    <i class="fas fa-file-alt fa-sm"></i>
  </a>
  <a href="{{repo}}/issues/new?{{issueTitle}}&{{issueBody}}" class="btn no-automatic-external" title="Report an issue with this page"
    target="_blank" rel="noopener">
    <i class="fas fa-bug fa-sm"></i>
  </a>
</span>
修改错误或提交 issue 。

1. 联系本人
	- 邮件：`243297288@qq.com`
	- 微信：`gunavy2009` （添加好友时，请填写验证备注）

## 使用

1. 使用该 `中文版` 请遵守官方 `TERMS` 。
2. 使用该 `中文版` 部署或发布的网站，请保留此页面及此页面相关入口。
3. 使用该 `中文版` 部分内容，请注明 `中文版` github 地址：[site-www-cn](https://github.com/dartchina/site-www-cn)。
