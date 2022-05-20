---
layout: page
title: About
permalink: /about/
weight: 3
---

# **About Me**

Hi I am **{{ site.author.name }}** :wave:,<br>
백엔드 개발자를 희망하고 있습니다. 

<div class="row">
{% include about/skills.html title="Programming Skills" source=site.data.programming-skills %}
{% include about/skills.html title="Tools" source=site.data.other-skills %}
</div>

<div class="row">
{% include about/timeline.html %}
</div>