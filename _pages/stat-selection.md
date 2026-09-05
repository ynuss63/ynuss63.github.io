---
title: "统计拔尖班选拔"
permalink: /stat-selection/
layout: single
toc: true
---

{% assign pdfs = site.static_files | where_exp: "f", "f.path contains '/pdfs/tongji-xuanba/'" | where_exp: "f", "f.extname == '.pdf'" %}

{% for f in pdfs %}
- [{{ f.basename | replace: "_", " " }}]({{ f.path }})
{% endfor %}
