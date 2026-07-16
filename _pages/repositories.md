---
layout: page
permalink: /repositories/
title: repositories
description: Selected GitHub repositories and open-source research projects.
nav: false
nav_order: 4
---

{% assign github_user = site.data.repositories.github_user %}

{% if github_user %}

[GitHub profile](https://github.com/{{ github_user }})

{% endif %}

---

{% if site.data.repositories.repositories %}

## Selected Repositories

<div class="repositories">
  {% for item in site.data.repositories.repositories %}
    <div class="repository my-4">
      <h3>
        <a href="https://github.com/{{ item.repo }}" target="_blank" rel="noopener noreferrer">{{ item.name }}</a>
      </h3>
      <p>{{ item.description }}</p>
      <p><code>{{ item.repo }}</code></p>
    </div>
  {% endfor %}
</div>

{% endif %}
