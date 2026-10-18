---
layout: about
title: about
permalink: /
subtitle: Rostock, Germany

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  more_info: >
    <div style="display: flex; justify-content: center; align-items: center; gap: 14px; margin: 12px 0;">
      <a href="/assets/pdf/example_pdf.pdf" aria-label="Download CV" title="CV" style="display: inline-flex;">
        <img src="/assets/img/social/cv.svg" width="24" height="24" alt="CV">
      </a>
      <a href="mailto:amiryazdanpanah26@gmail.com" aria-label="Email Amirhosein" title="Email" style="display: inline-flex;">
        <img src="/assets/img/social/email.svg" width="24" height="24" alt="Email">
      </a>
      <a href="https://www.linkedin.com/in/amirhosein-yp/" aria-label="LinkedIn profile" title="LinkedIn" style="display: inline-flex;">
        <img src="/assets/img/social/linkedin.svg" width="24" height="24" alt="LinkedIn">
      </a>
      <a href="https://github.com/Amir-Yazdanpanah" aria-label="GitHub profile" title="GitHub" style="display: inline-flex;">
        <img src="/assets/img/social/github.svg" width="24" height="24" alt="GitHub">
      </a>
    </div>
    <p>Rostock, Germany</p>

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

## [Publication]({{ '/publications/' | relative_url }})

## Selected Projects

{% assign selected_projects = site.projects | where: 'selected', true | sort: 'importance' %}
{% for project in selected_projects %}

### {{ project.title }}

{{ project.description }}

_{{ project.technologies }}_

<a class="btn btn-sm btn-outline-primary" href="{{ project.url | relative_url }}" aria-label="Read more about {{ project.title | escape }}">Read more</a>
{% endfor %}
