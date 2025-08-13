---
title: All Posts
layout: page
permalink: /blog/
---

<h1>{{ page.title }}</h1>

<p>A collection of articles and thoughts.</p>

<hr>

{%- if site.posts.size > 0 -%}
  <ul class="post-list">
    {%- for post in site.posts -%}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>
      {%- if post.description -%}
        <p class="post-blurb">{{ post.description }}</p>
      {%- endif -%}
    </li>
    {%- endfor -%}
  </ul>
{%- endif -%}