---
title: "数学分析"
permalink: /math-analysis/
layout: single
---

{% assign pdfs = site.static_files | where_exp: "f", "f.path contains '/pdfs/shuxue-fenxi/'" | where_exp: "f", "f.extname == '.pdf'" %}
{% assign glist = "40,39,38,37,36,35,34,33,32,31,30,29,28,27,26,25,24,23,22,21,20" | split: "," %}
{% assign groups = "" | split: "" %}
{% assign seen = "" %}
{% for f in pdfs %}
  {% assign parts = f.basename | split: "_" %}
  {% assign module = parts[1] %}
  {% assign suffix = "" %}
  {% for p in parts %}{% if p contains "小测" or p contains "期中" or p contains "期末" or p contains "随堂" %}{% assign suffix = p %}{% endif %}{% endfor %}
  {% if suffix contains "期末" %}{% assign key = module | append: " 期末" %}{% else %}{% assign key = module | append: " 小测" %}{% endif %}
  {% unless seen contains key %}{% assign seen = seen | append: "|" | append: key %}{% assign groups = groups | push: key %}{% endunless %}
{% endfor %}
{% assign groups = groups | sort %}

<p style="color:#777;font-size:0.92em;margin:0.2em 0 1.2em">共 {{ pdfs.size }} 份试卷，点标题展开</p>

{% for group in groups %}
  {% assign cnt = 0 %}
  {% for f in pdfs %}{% assign parts = f.basename | split: "_" %}{% assign module = parts[1] %}{% assign suffix = "" %}{% for p in parts %}{% if p contains "小测" or p contains "期中" or p contains "期末" or p contains "随堂" %}{% assign suffix = p %}{% endif %}{% endfor %}{% if suffix contains "期末" %}{% assign key = module | append: " 期末" %}{% else %}{% assign key = module | append: " 小测" %}{% endif %}{% if key == group %}{% assign cnt = cnt | plus: 1 %}{% endif %}{% endfor %}
<div markdown="0">
<details style="margin:0 0 1em 0">
<summary style="cursor:pointer;font-weight:600;font-size:1.12em;padding:0.2em 0;border-bottom:1px solid #e6e6e6">{{ group }} <span style="color:#999;font-size:0.85em;font-weight:400">（{{ cnt }}）</span></summary>
<ul>
{% for py in glist %}{% assign gs = py | append: "级" %}{% for ff in pdfs %}{% assign pp = ff.basename | split: "_" %}{% assign mid = pp[1] %}{% assign sf = "" %}{% for q in pp %}{% if q contains "小测" or q contains "期中" or q contains "期末" or q contains "随堂" %}{% assign sf = q %}{% endif %}{% endfor %}{% if sf contains "期末" %}{% assign kk = mid | append: " 期末" %}{% else %}{% assign kk = mid | append: " 小测" %}{% endif %}{% if kk == group and pp[0] == gs and sf contains "期中" %}<li style="margin:0.3em 0"><a href="{{ ff.path }}">{{ ff.basename | replace: "_", " " }}</a></li>{% endif %}{% endfor %}{% for ff in pdfs %}{% assign pp = ff.basename | split: "_" %}{% assign mid = pp[1] %}{% assign sf = "" %}{% for q in pp %}{% if q contains "小测" or q contains "期中" or q contains "期末" or q contains "随堂" %}{% assign sf = q %}{% endif %}{% endfor %}{% if sf contains "期末" %}{% assign kk = mid | append: " 期末" %}{% else %}{% assign kk = mid | append: " 小测" %}{% endif %}{% if kk == group and pp[0] == gs %}{% unless sf contains "期中" %}<li style="margin:0.3em 0"><a href="{{ ff.path }}">{{ ff.basename | replace: "_", " " }}</a></li>{% endunless %}{% endif %}{% endfor %}{% endfor %}
</ul>
</details>
</div>
{% endfor %}
