---
layout: page
title: About
description: 终生学习，终生快乐
keywords: Orch Co, 菜哥
comments: true
menu: 关于
permalink: /about/
---

我是菜哥，人如其名，菜得一批。

仰慕「优雅编码的艺术」以及学习使我快乐。

坚信熟能生巧，努力改变人生。

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
