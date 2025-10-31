---
title: All Projects
layout: default
permalink: /projects/
---

<div class="post-content">
  <h1>{{ page.title }}</h1>
  <p>A complete archive of my projects, sorted by the most recent activity.</p>

  <hr>

  <div class="project-grid" style="margin-top: 2em;">
    {% comment %}
      Part 1: Display projects that HAVE updates, sorted by most recent update.
    {% endcomment %}
    {% assign slugs_with_updates = site.project_updates | map: 'project_slug' | uniq %}
    {% assign slugs_in_order = site.project_updates | sort: 'date' | reverse | map: 'project_slug' | uniq %}

    {% for slug in slugs_in_order %}
      {% assign project = site.projects | where: "slug", slug | first %}
      {% if project %}
        {% assign latest_update = site.project_updates | where: "project_slug", project.slug | sort: 'date' | last %}
        {% assign last_updated_date = latest_update.date | default: project.date %}
        <!-- We are reusing the 'project-box' style from your homepage -->
        <a href="{{ project.url | relative_url }}" class="project-box">
          <div class="project-image" style="background-image: url('{{ project.image | relative_url }}');"></div>
          <div class="project-title">
            <h3>{{ project.title }}</h3>
            <p class="project-last-updated">Last updated {{ last_updated_date | date: "%B %d, %Y" }}</p>
          </div>
        </a>
      {% endif %}
    {% endfor %}

    {% comment %}
      Part 2: Find and display projects that DO NOT have updates, sorted by their own date.
    {% endcomment %}
    {% assign projects_without_updates = "" | split: "" %}
    {% for project in site.projects %}
      {% unless slugs_with_updates contains project.slug %}
        {% assign projects_without_updates = projects_without_updates | push: project %}
      {% endunless %}
    {% endfor %}

    {% assign sorted_no_updates = projects_without_updates | sort: 'date' | reverse %}

    {% for project in sorted_no_updates %}
      {% assign latest_update = site.project_updates | where: "project_slug", project.slug | sort: 'date' | last %}
      {% assign last_updated_date = latest_update.date | default: project.date %}
      <a href="{{ project.url | relative_url }}" class="project-box">
        <div class="project-image" style="background-image: url('{{ project.image | relative_url }}');"></div>
        <div class="project-title">
          <h3>{{ project.title }}</h3>
          <p class="project-last-updated">Last updated {{ last_updated_date | date: "%B %d, %Y" }}</p>
        </div>
      </a>
    {% endfor %}
  </div>

</div>
