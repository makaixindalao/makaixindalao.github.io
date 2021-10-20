---
layout: page
title: About
description: 打码改变世界
keywords: KaiXin
comments: true
menu: 关于
permalink: /about/
---

我是开心。

衣带渐宽终不悔，BUG修得人憔悴。

## 联系

邮箱：makaixindalao@163.com

GitHub：makaixindalao



## Skill Keywords

{% for skill in site.data.skills %}
### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
