---
title: "复变函数论"
permalink: /complex-analysis/
layout: single
toc: true
---

{% assign pdfs = site.static_files | where_exp: "f", "f.path contains '/pdfs/fubian-hanshulun/'" | where_exp: "f", "f.extname == '.pdf'" %}
{% assign xiaoces = "" | split: "" %}
{% assign qimos = "" | split: "" %}
{% for f in pdfs %}
  {% assign parts = f.basename | split: "_" %}
  {% assign suffix = "" %}
  {% for p in parts %}{% if p contains "小测" or p contains "期中" or p contains "期末" or p contains "随堂" %}{% assign suffix = p %}{% endif %}{% endfor %}
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

