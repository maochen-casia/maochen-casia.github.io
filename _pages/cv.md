---
layout: page
permalink: /cv/
title: Mao Chen's CV
nav: true
nav_order: 5
description: 
toc:
  sidebar: left
---

<style>
  .cv-pdf-link {
    float: right;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 2.75rem;
    height: 2.75rem;
    margin-top: -4.2rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 4px;
    color: var(--global-theme-color);
    font-size: 1.65rem;
    text-decoration: none;
  }

  .cv-pdf-link:hover {
    color: var(--global-theme-color);
    text-decoration: none;
  }

  .cv-card {
    border: 1px solid var(--global-divider-color);
    border-radius: 4px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.12);
    margin: 1.25rem 0;
    padding: 1.25rem 1.5rem;
    background: var(--global-bg-color);
  }

  .cv-card h2 {
    margin-top: 0;
    margin-bottom: 1.25rem;
  }

  .cv-card table {
    margin-bottom: 0;
  }

  .cv-entry {
    border-bottom: 1px solid var(--global-divider-color);
    padding: 0.85rem 0;
  }

  .cv-entry:first-child {
    padding-top: 0;
  }

  .cv-entry:last-child {
    border-bottom: 0;
    padding-bottom: 0;
  }

  .cv-year {
    color: var(--global-theme-color);
    font-weight: 700;
  }

  .cv-entry-title {
    color: var(--global-theme-color);
    font-weight: 700;
  }

  @media (max-width: 576px) {
    .cv-pdf-link {
      margin-top: -3.7rem;
    }
  }
</style>

<a class="cv-pdf-link" href="{{ '/assets/pdf/Mao_Chen_CV.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Download PDF" title="Download PDF">
  <i class="fa-regular fa-file-pdf" aria-hidden="true"></i>
</a>

{% for section in site.data.cv %}
<section class="cv-card">
<h2>{{ section.title }}</h2>

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
<div class="row cv-entry">
  <div class="col-sm-3 cv-year">{{ item.year }}</div>
  <div class="col-sm-9">
    {% if item.title %}<div class="cv-entry-title">{{ item.title }}</div>{% endif %}
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
<div class="cv-entry">
<p class="cv-entry-title">{{ item.title }}</p>
{% if item.items %}
<ul>
  {% for subitem in item.items %}
    <li>{{ subitem }}</li>
  {% endfor %}
</ul>
{% endif %}
</div>
{% endfor %}

{% elsif section.type == "list" %}
<ul>
  {% for item in section.contents %}
    <li>{{ item }}</li>
  {% endfor %}
</ul>
{% endif %}

</section>
{% endfor %}
