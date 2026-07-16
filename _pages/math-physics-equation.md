---
title: "数学物理方程"
permalink: /math-physics-equation/
layout: single
toc: true
---

{% assign pdfs = site.static_files | where_exp: "f", "f.path contains '/pdfs/shuxue-wuli-fangcheng/'" | where_exp: "f", "f.extname == '.pdf'" %}

{% for group_name in "小测,期末" | split: "," %}
  {% assign has = false %}
  {% for f in pdfs %}{% assign parts = f.basename | split: "_" %}{% assign suffix = parts[2] %}{% if suffix contains "期末" and group_name == "期末" %}{% assign has = true %}{% elsif suffix contains "小测" or suffix contains "测试" and group_name == "小测" %}{% assign has = true %}{% endif %}{% endfor %}
  {% if has %}
## {{ group_name }}
    {% for f in pdfs %}{% assign parts = f.basename | split: "_" %}{% assign suffix = parts[2] %}{% if suffix contains "期末" and group_name == "期末" %}- [{{ f.basename | replace: "_", " " }}]({{ f.path }})
{% elsif suffix contains "小测" or suffix contains "测试" and group_name == "小测" %}- [{{ f.basename | replace: "_", " " }}]({{ f.path }})
{% endif %}{% endfor %}
  {% endif %}
{% endfor %}

{% assign has_other = false %}
{% for f in pdfs %}{% assign parts = f.basename | split: "_" %}{% assign suffix = parts[2] %}{% unless suffix contains "期末" or suffix contains "小测" or suffix contains "测试" %}{% assign has_other = true %}{% endunless %}{% endfor %}
{% if has_other %}
## 其他
{% for f in pdfs %}{% assign parts = f.basename | split: "_" %}{% assign suffix = parts[2] %}{% unless suffix contains "期末" or suffix contains "小测" or suffix contains "测试" %}- [{{ f.basename | replace: "_", " " }}]({{ f.path }})
{% endunless %}{% endfor %}
{% endif %}
