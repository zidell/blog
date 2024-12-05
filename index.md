---
layout: default
title: Home
---
<!-- https://jekyllrb-ko.github.io/docs/variables/ -->
<ul class="list-unstyled">
  {% for post in site.posts %}
    <li class="my-5">
        <a href="{{site.baseurl}}{{ post.url }}" class="d-block">
      <h2 class="fs-4 fw-bold text-decoration-underline">{{ post.title }}</h2>
      <div class="post-excerpt opacity-50">
        {{ post.excerpt | strip_html | truncatewords: 50 }}
        </div>
        <div class="post-meta opacity-50 fs-xs mt-1">{{ post.date | date: "%Y-%m-%d" }}</div>
        </a>
    </li>
  {% endfor %}
</ul>