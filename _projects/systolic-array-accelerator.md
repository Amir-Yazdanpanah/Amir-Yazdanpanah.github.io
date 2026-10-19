---
layout: page
title: Systolic Array Accelerator for Neural Networks
permalink: /projects/systolic-array-accelerator/
description: Designed a parameterizable systolic array accelerator for MLPs and CNNs, supporting energy-efficient operation, configurable dataflows, and sparsity-aware computation.
importance: 3
category: work
selected: true
project_icon: /assets/img/project-icons/systolic-array.svg
technologies: RTL Design · Systolic Arrays · FPGA · Neural Network Acceleration
---

I designed and implemented a parameterizable systolic array architecture for accelerating multilayer perceptrons (MLPs) and convolutional neural networks (CNNs), with energy efficiency and sparsity-aware computation as the main goals.

## Tile Architecture

The architecture follows a hierarchical design. At the tile level, a 4 × 4 systolic array contains 16 interconnected processing elements, supported by local input and weight buffers. FIFOs align operands as they enter the array, while a local controller manages buffer accesses, data movement, and computation. Request–grant interfaces coordinate the transfer of inputs and weights to each tile.

<figure>
  <img src="{{ '/assets/img/projects/systolic-array-accelerator/Slide3.JPG' | relative_url }}" alt="Tile architecture with a 4 by 4 processing-element array, input and weight buffers, operand-alignment FIFOs, and a local controller." width="1280" height="720" loading="lazy" style="max-width: 100%; height: auto;">
  <figcaption>Tile-level architecture: local buffers, controller, FIFOs, and 16 processing elements.</figcaption>
</figure>

## Tile Hierarchy and System Organization

Multiple tiles form a larger logical three-dimensional organization, allowing larger tensor computations to be mapped across the accelerator.

<figure>
  <img src="{{ '/assets/img/projects/systolic-array-accelerator/Slide2.JPG' | relative_url }}" alt="Multiple systolic array tiles arranged in a logical three-dimensional hierarchy for larger tensor computations." width="1280" height="720" loading="lazy" style="max-width: 100%; height: auto;">
  <figcaption>Logical three-dimensional organization of systolic array tiles.</figcaption>
</figure>

At the system level, separate global buffers hold inputs, weights, and outputs, while dedicated data-transfer modules connect these buffers to the tile hierarchy. Parameterizable array dimensions and customizable dataflow strategies allow the architecture to accommodate different neural network layers and workload sizes.

<figure>
  <img src="{{ '/assets/img/projects/systolic-array-accelerator/Slide1.JPG' | relative_url }}" alt="System architecture connecting global input, weight, and output buffers through dedicated data-transfer modules to the systolic tile hierarchy." width="1280" height="720" loading="lazy" style="max-width: 100%; height: auto;">
  <figcaption>System-level architecture with global buffers and dedicated data-transfer modules.</figcaption>
</figure>

## Implementation and Performance

The design supports an energy-efficient operating mode and sparsity-aware computation to improve efficiency when processing sparse neural network data. I developed FPGA implementations for MLP and CNN acceleration, while the ASIC implementation achieved a peak performance of **113.9 GOPS**. The project focused on balancing resource utilization, throughput, energy efficiency, and adaptability.

<p style="font-size: 0.85em; margin-top: 0;"><em>RTL Design · Systolic Arrays · FPGA · Neural Network Acceleration</em></p>

[Back to Projects]({{ '/projects/' | relative_url }})
