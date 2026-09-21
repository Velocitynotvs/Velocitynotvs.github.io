---
layout: home
title: Home
layout: base
---
<div class="home">
  {%- if page.title -%}
    <h1 class="page-heading">{{ page.title }}</h1>
  {%- endif -%}

  {{ content }}

  {% if site.posts.size > 0 %}
    <h2 class="post-list-heading">{{ page.list_title | default: "Posts" }}</h2>
    <ul class="post-list">
      {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
      {%- for post in site.posts -%}
      <li style="display: flex; align-items: center; margin-bottom: 20px;">
        
        <!-- 1. The Picture Link -->
        {% if post.thumbnail %}
          <a href="{{ post.url | relative_url }}" style="margin-right: 15px; flex-shrink: 0;">
            <img src="{{ post.thumbnail | relative_url }}" alt="{{ post.title }}" style="width: 100px; height: 100px; object-fit: cover; border-radius: 4px;">
          </a>
        {% endif %}

        <!-- 2. The Title and Date Link -->
        <div>
          <span class="post-meta">{{ post.date | date: date_format }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">
              {{ post.title | escape }}
            </a>
          </h3>
          {%- if site.show_excerpts -%}
            {{ post.excerpt }}
          {%- endif -%}
        </div>

      </li>
      {%- endfor -%}
    </ul>

    <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
  {% endif %}
</div>
