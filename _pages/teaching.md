---
layout: page
title: Cours
permalink: /teachings/
description: Les ressources pour les cours
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

<!-- pages/teaching.md -->
<div class="teachings">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized teachings -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_teachings = site.teachings | where: "category", category %}
  {% assign sorted_teachings = categorized_teachings | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_teachings %}
      {% include teachings_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_teachings %}
      {% include teachings.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display teachings without categories -->

{% assign sorted_teachings = site.teachings | sort: "importance" %}

  <!-- Generate cards for each teaching -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_teachings %}
      {% include teachings_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_teachings %}
      {% include teachings.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
