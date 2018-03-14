---
layout: page
title: Tags
---
<ul class="tag-cloud">
{% assign sorted_tags = site.tags %}
{% for tag in sorted_tags %}
  <li style="font-size: {{ tag | last | size | times: 100 | divided_by: site.tags.size | plus: 35  }}%">
    <a href="/tag_indices/{{ tag | first | slugize }}/">
      {{ tag | first }} ({{ tag | last | size }})
    </a>
  </li>
{% endfor %}
</ul>