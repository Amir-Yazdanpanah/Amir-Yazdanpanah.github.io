---
layout: about
title: About
permalink: /
subtitle: Rostock, Germany

profile:
  align: right
  image: portrait-3x4.png
  image_circular: false # crops the image to make it circular
  more_info: >
    <ul aria-label="Profile and contact information" style="list-style: none; padding: 0 0 0 12px; margin: 16px 0; display: grid; gap: 10px; font-family: system-ui, sans-serif; font-size: 14px; line-height: 1.5; text-align: left;">
      <li style="display: grid; grid-template-columns: 14px minmax(0, 1fr); align-items: center; gap: 12px; margin: 0; padding: 0; text-align: left;">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true" style="display: block; width: 14px; height: 14px; margin: 0;">
          <path d="M12 1a8 8 0 0 0-8 8c0 6 8 14 8 14s8-8 8-14a8 8 0 0 0-8-8Zm0 11a3 3 0 1 1 0-6 3 3 0 0 1 0 6Z"/>
        </svg>
        <span>Rostock, Germany</span>
      </li>
      <li style="display: grid; grid-template-columns: 14px minmax(0, 1fr); align-items: center; gap: 12px; margin: 0; padding: 0; text-align: left;">
        <img src="/assets/img/social/email.svg" width="14" height="14" alt="" aria-hidden="true" style="display: block; width: 14px; height: 14px; margin: 0;">
        <a href="mailto:amiryazdanpanah26@gmail.com" style="color: inherit; text-decoration: none; text-align: left;">Email</a>
      </li>
      <li style="display: grid; grid-template-columns: 14px minmax(0, 1fr); align-items: center; gap: 12px; margin: 0; padding: 0; text-align: left;">
        <img src="/assets/img/social/github.svg" width="14" height="14" alt="" aria-hidden="true" style="display: block; width: 14px; height: 14px; margin: 0;">
        <a href="https://github.com/Amir-Yazdanpanah" style="color: inherit; text-decoration: none; text-align: left;">GitHub</a>
      </li>
      <li style="display: grid; grid-template-columns: 14px minmax(0, 1fr); align-items: center; gap: 12px; margin: 0; padding: 0; text-align: left;">
        <img src="/assets/img/social/linkedin.svg" width="14" height="14" alt="" aria-hidden="true" style="display: block; width: 14px; height: 14px; margin: 0;">
        <a href="https://www.linkedin.com/in/amirhosein-yp/" style="color: inherit; text-decoration: none; text-align: left;">LinkedIn</a>
      </li>
    </ul>

selected_papers: false # includes a list of papers marked as "selected={true}"
social: false # profile links are displayed below the photo

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder


# latest_posts:
#   enabled: true
#   scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
#   limit: 3 # leave blank to include all the blog posts
---

I am a Research Associate at the University of Rostock, Germany, and hold a master’s degree in Electrical Engineering, specializing in Digital System Design, from the University of Tehran. My interests lie in hardware–software co-design, with a focus on the energy efficiency, reliability, and security of computing systems.

My experience spans system-level modeling and software development through RTL design and FPGA prototyping. I have worked on RISC-V processors and SoCs, Linux kernel modules for controlling processor state, and storage-system projects involving Zoned Namespaces (ZNS), flash translation layers, and garbage collection. These projects have shaped my interest in how software behavior and hardware architecture jointly determine system performance and dependability.

In Germany, I work on measurement-based energy and execution-time characterization of embedded workloads. This builds on my master’s research into machine-learning-based, cycle-accurate power estimation at RTL. I also investigate the reliability and security of approximate arithmetic in neural networks, studying how bit flips and deliberate attacks affect their predictions and robustness.

<hr style="clear: none; overflow: hidden; border: 0; border-top: 1px solid var(--global-divider-color, #ddd); margin: 1rem 0;">

## Publication

{% for paper in site.data.homepage_publications %}
<h3 style="font-size: 1rem;">
  {{ paper.title | escape }}
  <a href="{{ '/publications/' | relative_url }}" style="font-size: 1rem; font-weight: normal;" aria-label="Read more about {{ paper.title | escape }}">Read more</a>
</h3>
{% endfor %}

<hr style="clear: both; border: 0; border-top: 1px solid var(--global-divider-color, #ddd); margin: 1.5rem 0;">

## Projects

{% assign selected_projects = site.projects | where: 'selected', true | sort: 'importance' %}
{% for project in selected_projects %}

<h3 style="font-size: 1.5rem;">{{ project.title | escape }}</h3>

<p style="margin-bottom: 4px;">{{ project.description | escape }} <a href="{{ project.url | relative_url }}" aria-label="Read more about {{ project.title | escape }}">Read more</a></p>

<p style="font-size: 0.85em; margin-top: 0;"><em>{{ project.technologies | escape }}</em></p>
{% endfor %}
