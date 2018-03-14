---
layout: page
title: Tags
---
<ul class="tag-cloud">
{% assign sorted_tags = site.tags %}
{% for tag in sorted_tags %}
  <li class="tag-cloud-item">
    <a href="/tag_indices/{{ tag | first | slugize }}/">
      {{ tag | first }} ({{ tag | last | size }})
    </a>
  </li>
{% endfor %}
</ul>