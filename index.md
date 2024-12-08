---
layout: default
title: Home
---
<!-- https://jekyllrb-ko.github.io/docs/variables/ -->
<ul class="list-unstyled">
  {% for post in site.posts %}
    <li class="my-5">
        <div class="post-meta opacity-50 fs-sm mb-1">{{ post.date | date: "%B %d, %Y" }}</div>
        <a href="{{site.baseurl}}{{ post.url }}" class="d-block">
      <h2 class="fs-4 fw-bold text-decoration-underline">{{ post.title }}</h2>
      <div class="post-excerpt opacity-50">
        {{ post.excerpt | strip_html | truncatewords: 50 }}
        </div>
        </a>
    </li>
  {% endfor %}

  <!-- Pagination links -->
<div class="pagination">
    {% if paginator.previous_page %}
      <a href="{{ paginator.previous_page_path }}" class="previous">
        Previous
      </a>
    {% else %}
      <span class="previous">Previous</span>
    {% endif %}
    <span class="page_number ">
      Page: {{ paginator.page }} of {{ paginator.total_pages }}
    </span>
    {% if paginator.next_page %}
      <a href="{{ paginator.next_page_path }}" class="next">Next</a>
    {% else %}
      <span class="next ">Next</span>
    {% endif %}
  </div>
</ul>