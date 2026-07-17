---
title: "高等数学"
permalink: /advanced-math/
layout: single
toc: true
---

{% assign pdfs = site.static_files | where_exp: "f", "f.path contains '/pdfs/gaodeng-shuxue/'" | where_exp: "f", "f.extname == '.pdf'" %}
{% assign xiaoces = "" | split: "" %}
{% assign qimos = "" | split: "" %}
{% for f in pdfs %}
  {% assign parts = f.basename | split: "_" %}
  {% assign suffix = parts[2] %}
  {% if suffix contains "期末" %}{% assign qimos = qimos | push: f %}
  {% else %}{% assign xiaoces = xiaoces | push: f %}
  {% endif %}
{% endfor %}

{% if xiaoces.size > 0 %}
## 小测
{% for f in xiaoces %}
- [{{ f.basename | replace: "_", " " }}]({{ f.path }})
{% endfor %}
{% endif %}

{% if qimos.size > 0 %}
## 期末
{% for f in qimos %}
- [{{ f.basename | replace: "_", " " }}]({{ f.path }})
{% endfor %}
{% endif %}
