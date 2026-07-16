---
layout: page
permalink: /cv/
title: CV
nav: true
nav_order: 5
description: Curriculum vitae of Mao Chen.
toc:
  sidebar: left
---

<div class="mb-4">
  <a class="btn btn-sm z-depth-0" href="{{ '/assets/pdf/Mao_Chen_CV.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer">Download PDF</a>
</div>

{% for section in site.data.cv %}
## {{ section.title }}

{% if section.type == "map" %}
<table class="table table-sm table-borderless">
  <tbody>
    {% for item in section.contents %}
      <tr>
        <td><strong>{{ item.name }}</strong></td>
        <td>{{ item.value }}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>

{% elsif section.type == "time_table" %}
{% for item in section.contents %}
<div class="row mb-3">
  <div class="col-sm-3 text-muted">{{ item.year }}</div>
  <div class="col-sm-9">
    {% if item.title %}<strong>{{ item.title }}</strong>{% endif %}
    {% if item.institution %}<div><em>{{ item.institution }}</em></div>{% endif %}
    {% if item.items %}
      <ul>
        {% for subitem in item.items %}
          <li>{{ subitem }}</li>
        {% endfor %}
      </ul>
    {% endif %}
    {% if item.description %}
      <ul>
        {% for desc in item.description %}
          {% if desc.title %}
            <li>{{ desc.title }}</li>
          {% else %}
            <li>{{ desc }}</li>
          {% endif %}
        {% endfor %}
      </ul>
    {% endif %}
  </div>
</div>
{% endfor %}

{% elsif section.type == "nested_list" %}
{% for item in section.contents %}
<p><strong>{{ item.title }}</strong></p>
{% if item.items %}
<ul>
  {% for subitem in item.items %}
    <li>{{ subitem }}</li>
  {% endfor %}
</ul>
{% endif %}
{% endfor %}

{% elsif section.type == "list" %}
<ul>
  {% for item in section.contents %}
    <li>{{ item }}</li>
  {% endfor %}
</ul>
{% endif %}

{% endfor %}
