---
layout: archive
title: "Articles"
date: 2015-12-30T11:39:03-04:00
modified:
excerpt: "These are some of my favorite things"
tags: []
image:
  feature:
  teaser:
---

<div class="tiles">
{% for post in site.categories.articles %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->
