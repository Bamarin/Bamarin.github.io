---
title: Blog
permalink: /developer/
list_title: Projects
---

## Platforms

github|gitlab|bitbucket
---|---|---
[Bamarin][github]|[Bamarin][gitlab]|[bamarin_it][bitbucket]

<div>
{%- if site.posts.size > 0 -%}
<h2 class="post-list-heading">{{ page.list_title | default: "Posts" }}</h2>
<ul class="post-list">
  {%- assign posts = site.posts -%}
  {% include related.html postlist=posts %}
</ul>
{%- endif -%}
</div>


[github]: https://github.com/Bamarin
[gitlab]: https://gitlab.com/Bamarin
[bitbucket]: https://bitbucket.org/bamarin_it
