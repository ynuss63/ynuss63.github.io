---
title: "常微分方程"
permalink: /ode/
layout: single
---

{% assign pdfs = site.static_files | where_exp: "f", "f.path contains '/pdfs/changweifen-fangcheng/'" | where_exp: "f", "f.extname == '.pdf'" %}
{% assign glist = "40,39,38,37,36,35,34,33,32,31,30,29,28,27,26,25,24,23,22,21,20" | split: "," %}
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

<p style="color:#777;font-size:0.92em;margin:0.2em 0 1.2em">共 {{ pdfs.size }} 份试卷，点标题展开</p>

{% if xiaoces.size > 0 %}
<div markdown="0">
<details style="margin:0 0 1em 0">
<summary style="cursor:pointer;font-weight:600;font-size:1.12em;padding:0.2em 0;border-bottom:1px solid #e6e6e6">小测 <span style="color:#999;font-size:0.85em;font-weight:400">（{{ xiaoces.size }}）</span></summary>
<ul>
{% for py in glist %}{% assign gs = py | append: "级" %}{% for ff in xiaoces %}{% assign pp = ff.basename | split: "_" %}{% if pp[0] == gs %}<li style="margin:0.3em 0"><a href="{{ ff.path }}">{{ ff.basename | replace: "_", " " }}</a></li>{% endif %}{% endfor %}{% endfor %}
</ul>
</details>
</div>
{% endif %}

{% if qimos.size > 0 %}
<div markdown="0">
<details style="margin:0 0 1em 0">
<summary style="cursor:pointer;font-weight:600;font-size:1.12em;padding:0.2em 0;border-bottom:1px solid #e6e6e6">期末 <span style="color:#999;font-size:0.85em;font-weight:400">（{{ qimos.size }}）</span></summary>
<ul>
{% for py in glist %}{% assign gs = py | append: "级" %}{% for ff in qimos %}{% assign pp = ff.basename | split: "_" %}{% if pp[0] == gs %}<li style="margin:0.3em 0"><a href="{{ ff.path }}">{{ ff.basename | replace: "_", " " }}</a></li>{% endif %}{% endfor %}{% endfor %}
</ul>
</details>
</div>
{% endif %}
