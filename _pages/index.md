---
layout: single
classes: wide
author_profile: true
title:
permalink: /
description: "Impactful Research blog"
---

**How do impactful papers come to be?**

**影响力之作是怎样炼成的？**

<h2 class="archive__subtitle">Recent posts / 最新文章</h2>

<div class="entries-list">
  {% for post in site.posts limit:5 %}
    {% include archive-single.html type="list" %}
  {% endfor %}
</div>

[View all posts →](/year-archive/)
