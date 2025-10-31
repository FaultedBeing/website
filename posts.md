---
title: All Posts
layout: page
permalink: /blog/
---

{% assign blog_posts = site.posts %}
{% assign promoted_updates = site.project_updates | where: "promote_to_blog", true %}
{% assign combined_posts = blog_posts | concat: promoted_updates %}
{% assign posts_by_topic = combined_posts | group_by_exp: "post", "post.topic | default: post.project_slug | default: 'Miscellaneous'" %}
{% assign posts_by_topic = posts_by_topic | sort: 'name' %}

{% capture topics_body %}
  {% if posts_by_topic.size > 0 %}
    <ul class="topics-list">
      {% for group in posts_by_topic %}
        {% assign topic_name = group.name %}
        {% assign topic_slug = topic_name | slugify: 'default' %}
        <li><a href="/topics/{{ topic_slug }}/">{{ topic_name }}</a></li>
      {% endfor %}
    </ul>
  {% else %}
    <p class="topics-empty">Topics will appear once the first post is published.</p>
  {% endif %}
{% endcapture %}

<div class="topics-collapsible">
  <details>
    <summary>Topics</summary>
    {{ topics_body | strip }}
  </details>
</div>

<div class="posts-page-container">
  <div class="posts-main-content">
    <h1>{{ page.title }}</h1>
    <p class="posts-intro">A collection of articles and thoughts.</p>
    <hr>

    {% if combined_posts.size > 0 %}
      <div class="post-card-grid">
        {% for post in combined_posts %}
          <article class="post-card">
            <a class="post-card-link" href="{{ post.url | relative_url }}">
              {% if post.image %}
                <div class="post-card-image" style="background-image: url('{{ post.image | relative_url }}');"></div>
              {% endif %}
              <div class="post-card-body">
                <div class="post-card-meta">
                  <span class="post-card-date">{{ post.date | date: "%B %d, %Y" }}</span>
                  <span class="post-topic-tag">{{ post.topic | default: post.project_slug | default: 'Miscellaneous' }}</span>
                </div>
                <h2 class="post-card-title">{{ post.title | escape }}</h2>
                <p class="post-card-excerpt">{{ post.excerpt | strip_html | truncate: 200 }}</p>
                <span class="post-card-readmore">Read more →</span>
              </div>
            </a>
          </article>
        {% endfor %}
      </div>
    {% else %}
      <p class="topics-empty">No posts yet, but soon!</p>
    {% endif %}
  </div>

  <aside class="topics-sidebar">
    <div class="topics-card">
      <h2 class="topics-heading">Topics</h2>
      {{ topics_body | strip }}
    </div>
  </aside>
</div>