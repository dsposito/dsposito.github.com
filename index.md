---
layout: page
title : Welcome
group: navigation
---

{% include JB/setup %}

Hello World.


### Recent Posts
---
<ul>
{% for post in site.posts limit:5 %}
  <li><span>{{ post.date | date: "%B %d, %Y" }}</span>  : <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
