---
layout: page
title: talks
permalink: /talks/
description: A growing collection of your cool talks.
nav: false #true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

<!-- pages/talks.md -->
<div class="talks">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized talks -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_talks = site.talks | where: "category", category -%}
  {%- assign sorted_talks = categorized_talks | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_talks -%}
      {% include talks_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_talks -%}
      {% include talks.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display talks without categories -->
  {%- assign sorted_talks = site.talks | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for talk in sorted_talks -%}
      {% include talks_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_talks -%}
      {% include talks.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>