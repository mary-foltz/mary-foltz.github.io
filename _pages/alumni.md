---
layout: page
title: alumni
permalink: /alumni/
description: A growing collection of cool alumni.
nav: false
nav_order: 5
display_categories: [PhD, Masters, Undergrad]
horizontal: false
---

<!-- pages/alumni.md -->
<div class="projects">
{%- if site.enable_alumni_categories and page.display_categories %}
  <!-- Display categorized alumni -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_alumni = site.alumni | where: "category", category -%}
  {%- assign sorted_alumni = categorized_alumni | sort: "importance" %}
  <!-- Generate cards for each alum -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for alum in sorted_alumni -%}
      {% include alumni_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for alum in sorted_alumni -%}
      {% include alumni.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display alumni without categories -->
  {%- assign sorted_alumni = site.alumni | sort: "importance" -%}
  <!-- Generate cards for each alum -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for alum in sorted_alumni -%}
      {% include alumni_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for alum in sorted_alumni -%}
      {% include alumni.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
