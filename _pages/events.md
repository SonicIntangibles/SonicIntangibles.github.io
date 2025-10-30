---
layout: page
title: events
permalink: /events/
description: Events run by the team.
nav: true
nav_order: 3
#pagination:
#  enabled: true
#  collection: events
#  permalink: /page/:num/
#  per_page: 8
#  sort_field: date
#  sort_reverse: true
#  trail:
#    before: 1 # The number of links before the current page
#    after: 3 # The number of links after the current page
horizontal: false
---

<!-- pages/events.md -->
<div class="events">
{% if site.enable_event_categories and page.display_categories %}
  <!-- Display categorized events -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_events = site.events | where: "category", category %}
  {% assign sorted_events = categorized_events | sort: "importance" %}
  <!-- Generate cards for each event -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for event in sorted_events %}
      {% include events_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for event in sorted_events %}
      {% include events.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display events without categories -->

{% assign sorted_events = site.events | sort: "importance" %}

  <!-- Generate cards for each event -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for event in sorted_events %}
      {% include events_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for event in sorted_events %}
      {% include events.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
