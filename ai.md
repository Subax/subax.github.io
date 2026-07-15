---
layout: page
title: AI
subtitle: Medical AI, Machine Learning, Deep Learning
---

{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{% assign subsections = "medical-ai|Medical AI,machine-learning|Machine Learning,deep-learning|Deep Learning" | split: "," %}

<div id="full-tags-list">
  {%- for s in subsections -%}
    {%- assign parts = s | split: "|" -%}
    {%- assign slug = parts[0] -%}
    {%- assign label = parts[1] -%}
    {%- assign cat_posts = site.categories[slug] -%}
    <a href="#{{ slug }}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{ label }}&nbsp;({{ cat_posts | size }})</a>
  {%- endfor -%}
</div>

<div id="full-tags-list">
  {%- for s in subsections -%}
    {%- assign parts = s | split: "|" -%}
    {%- assign slug = parts[0] -%}
    {%- assign label = parts[1] -%}
    {%- assign cat_posts = site.categories[slug] -%}
    <h2 id="{{ slug }}" class="linked-section">
      <i class="fas fa-tag" aria-hidden="true"></i>
      &nbsp;{{ label }}&nbsp;({{ cat_posts | size }})
    </h2>
    <div class="post-list">
      {%- if cat_posts.size > 0 -%}
        {%- for post in cat_posts -%}
          <div class="tag-entry">
            <a href="{{ post.url | relative_url }}">{{ post.title | strip_html }}</a>
            <div class="entry-date">
              <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: date_format }}</time>
            </div>
          </div>
        {%- endfor -%}
      {%- else -%}
        <p class="text-muted">아직 게시된 글이 없습니다.</p>
      {%- endif -%}
    </div>
  {%- endfor -%}
</div>
