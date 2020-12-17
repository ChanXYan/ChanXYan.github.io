---
layout: page
title: About
description: 世界观察者
keywords: Xyan
comments: true
menu: 关于
permalink: /about/
---

我是Xyan

身处泥底 , 心比天高

一如名字所表现的 :  末流的出身 , 顶流的心思

## 联系

<ul>
{% for website in site.data.social %}
<li>{{website.sitename }}：<a href="{{ website.url.none }}" target="_blank">@{{ website.name.none }}</a></li>
{% endfor %}
{% if site.url contains 'username.org' %}
<li>
微信公众号：<br />
<img style="height:192px;width:192px;border:1px solid lightgrey;" src="{{ assets_base_url }}/assets/images/qrcode.jpg" alt="无二维码" />
</li>
{% endif %}
</ul>


## Skill Keywords

{% for skill in site.data.skills %}
### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
