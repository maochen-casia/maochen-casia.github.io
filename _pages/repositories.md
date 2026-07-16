---
layout: page
permalink: /repositories/
title: repositories
description: research code repositories & open source projects
nav: true
nav_order: 4
---

{% if site.data.repositories.repositories %}

<style>
  .repo-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem 5rem;
    margin-top: 2.5rem;
  }

  .repo-card {
    border: 1px solid var(--global-divider-color);
    border-radius: 4px;
    padding: 1.2rem 1.5rem;
    min-height: 8.75rem;
    background: var(--global-bg-color);
  }

  .repo-card-title {
    display: inline-flex;
    align-items: center;
    gap: 0.55rem;
    color: var(--global-theme-color);
    font-size: 1.15rem;
    font-weight: 700;
    margin-bottom: 0.8rem;
  }

  .repo-card-title:hover {
    color: var(--global-theme-color);
  }

  .repo-icon {
    width: 1rem;
    text-align: center;
  }

  .repo-description {
    min-height: 2.75rem;
    margin-bottom: 1.5rem;
  }

  .repo-meta {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    color: var(--global-text-color);
    font-size: 0.9rem;
  }

  .repo-language-dot {
    display: inline-block;
    width: 0.72rem;
    height: 0.72rem;
    border-radius: 50%;
    background: #3572a5;
    margin-right: 0.35rem;
    vertical-align: -0.05rem;
  }

  .repo-meta i {
    color: var(--global-theme-color);
    margin-right: 0.25rem;
  }

  @media (max-width: 768px) {
    .repo-grid {
      grid-template-columns: 1fr;
      gap: 1rem;
      margin-top: 1.5rem;
    }
  }
</style>

<div class="repo-grid">
  {% for item in site.data.repositories.repositories %}
    <div class="repo-card">
      <a class="repo-card-title" href="https://github.com/{{ item.repo }}" target="_blank" rel="noopener noreferrer">
        <i class="fa-regular fa-file-code repo-icon" aria-hidden="true"></i>
        <span>{{ item.name }}</span>
      </a>
      <p class="repo-description">{{ item.description }}</p>
      <div class="repo-meta">
        <span><span class="repo-language-dot"></span>{{ item.language }}</span>
        <span><i class="fa-regular fa-star" aria-hidden="true"></i>{{ item.stars }}</span>
        <span><i class="fa-solid fa-code-fork" aria-hidden="true"></i>{{ item.forks }}</span>
      </div>
    </div>
  {% endfor %}
</div>

{% endif %}
