---
title: "数学分析"
permalink: /math-analysis/
layout: single
toc: true
---

{% assign pdfs = site.static_files | where_exp: "f", "f.path contains '/pdfs/shuxue-fenxi/'" | where_exp: "f", "f.extname == '.pdf'" %}
{% assign groups = "" | split: "" %}

{% comment %}Group by module+type (e.g. 数分1 小测, 数分2 期末){% endcomment %}
{% assign seen = "" %}
{% for f in pdfs %}
  {% assign parts = f.basename | split: "_" %}
  {% assign module = parts[1] %}
  {% assign suffix = parts[2] %}
  {% if suffix contains "期末" %}
    {% assign key = module | append: " 期末" %}
  {% elsif suffix contains "小测" or suffix contains "测试" %}
    {% assign key = module | append: " 小测" %}
  {% else %}
    {% assign key = module | append: " " | append: suffix %}
  {% endif %}
  {% unless seen contains key %}
    {% assign seen = seen | append: "|" | append: key %}
    {% assign groups = groups | push: key %}
  {% endunless %}
{% endfor %}

{% for group in groups %}
## {{ group }}

  {% for f in pdfs %}
    {% assign parts = f.basename | split: "_" %}
    {% assign module = parts[1] %}
    {% assign suffix = parts[2] %}
    {% if suffix contains "期末" %}
      {% assign key = module | append: " 期末" %}
    {% elsif suffix contains "小测" or suffix contains "测试" %}
      {% assign key = module | append: " 小测" %}
    {% else %}
      {% assign key = module | append: " " | append: suffix %}
    {% endif %}
    {% if key == group %}
- [{{ f.basename | replace: "_", " " }}]({{ f.path }})
    {% endif %}
  {% endfor %}

{% endfor %}
