---
layout: page
title: Linux Kernel Module for Controlled RISC-V Energy and Runtime Measurement
permalink: /projects/risc-v-kernel-module/
description: Developed a Linux kernel module and execution framework for repeatable energy and runtime measurements on the Banana Pi BPI-F3, combining processor-state preparation, dynamic chunking, and GPIO synchronization.
importance: 1
category: work
selected: true
project_icon: /assets/img/project-icons/kernel.svg
github: https://github.com/Amir-Yazdanpanah/cache-flush-0
technologies: C · Linux Kernel · RISC-V · Banana Pi BPI-F3 · GPIO
---

<p style="font-size: 0.9rem;">
  <a href="{{ page.github }}"><i class="fa-brands fa-github" aria-hidden="true"></i> View on GitHub</a>
</p>

I developed a Linux kernel module and execution framework to support repeatable energy and runtime measurements on the Banana Pi BPI-F3, based on the SpacemiT X60 RISC-V processor. The project addresses a practical challenge in repeated experiments: processor state left by previous executions can influence subsequent measurements.

The module exposes a `/dev/cache_flush` interface and performs cache maintenance using the RISC-V `cbo.flush` instruction over selected memory regions. Additional preparation routines include instruction-cache synchronization, branch-predictor and branch-target-buffer conditioning, and pipeline draining. CPU affinity and preemption control help reduce scheduling-related variability, while GPIO signals mark the measurement interval for external power-measurement equipment.

A central feature is **time-based dynamic chunking**. The framework first calibrates execution time using 100 repetitions of the state-preparation and workload sequence. It then groups repetitions into chunks, checking elapsed time between chunks rather than after every iteration. As the target duration approaches, it adapts the chunk size to the remaining time, progressively reducing the number of repetitions per chunk. This approach amortizes timing-check overhead while limiting overshoot of the requested measurement duration.

<figure>
  <img src="{{ '/assets/img/projects/risc-v-kernel-module/kernel.jpg' | relative_url }}" alt="Measurement workflow showing experiment configuration, processor-state preparation, 100-iteration calibration, adaptive dynamic chunking, and GPIO-controlled measurement boundaries." width="1280" height="720" loading="lazy" style="max-width: 100%; height: auto;">
  <figcaption>Execution framework with processor-state preparation, time-based dynamic chunking, and external measurement synchronization.</figcaption>
</figure>

The framework brings privileged processor-state preparation, adaptive execution control, and external measurement synchronization into one experimental workflow. It was designed to improve measurement consistency and support automated energy and latency characterization without relying on hardware performance counters.

<p style="font-size: 0.85em; margin-top: 0;"><em>C · Linux Kernel · RISC-V · Banana Pi BPI-F3 · GPIO</em></p>

[Back to Projects]({{ '/projects/' | relative_url }})
