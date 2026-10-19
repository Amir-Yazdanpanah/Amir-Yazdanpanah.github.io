---
layout: page
title: Projects
permalink: /projects/
description: Selected projects in computing systems, hardware design, and FPGA development.
nav: true
nav_order: 3
---

{% assign selected_projects = site.projects | where: 'selected', true | sort: 'importance' %}

<ul style="list-style: none; padding: 0; margin: 0;">
{% for project in selected_projects %}
  <li style="display: flex; align-items: flex-start; gap: 1rem; padding: 1rem 0; border-bottom: 1px solid var(--global-divider-color, #ddd);">
    <img src="{{ project.project_icon | relative_url }}" alt="" width="48" height="48" loading="lazy" style="flex: 0 0 48px; background: #f8fafc; border-radius: 8px;">
    <div style="min-width: 0;">
      <h3 style="font-size: 1.1rem; margin: 0 0 0.35rem;"><a href="{{ project.url | relative_url }}">{{ project.title | escape }}</a></h3>
      <p style="font-size: 0.85rem; margin: 0;"><em>{{ project.technologies | escape }}</em></p>
      {% if project.github %}
      <a href="{{ project.github }}" style="font-size: 0.85rem;" aria-label="View {{ project.title | escape }} on GitHub"><i class="fa-brands fa-github" aria-hidden="true"></i> View on GitHub</a>
      {% endif %}
    </div>
  </li>
{% endfor %}
</ul>
