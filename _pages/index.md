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

<div class="notice--primary" markdown="1">
**📢 Call For Proposals / 公开征集采访提案**

We're inviting you to propose — and conduct — an interview with an impactful researcher. [Read the full call →]({% post_url 2026-05-04-call-for-proposals %})

我们邀请您提交一份采访提案，由您来完成对一位有影响力学者的深度对话。[查看完整征稿启事 →]({% post_url 2026-05-04-call-for-proposals %})
</div>

<h2 class="archive__subtitle">Recent posts / 最新文章</h2>

<div class="entries-list">
  {% for post in site.posts limit:5 %}
    {% include archive-single.html type="list" %}
  {% endfor %}
</div>

[View all posts →](/year-archive/)
