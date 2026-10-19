---
layout: page
title: Cryptographic Hardware Design
permalink: /projects/cryptographic-hardware-design/
description: Developed FPGA implementations of multiple AES architectures, the Keccak-f[1600] permutation, and an arbiter PUF for hardware security applications.
importance: 7
category: work
selected: true
github: https://github.com/Amir-Yazdanpanah/Amir-Yazdanpanah-26
technologies: RTL Design · Cryptography · FPGA · Xilinx Vivado
---

<p style="font-size: 0.9rem;">
  <a href="{{ page.github }}"><i class="fa-brands fa-github" aria-hidden="true"></i> View on GitHub</a>
</p>

Developed RTL implementations of cryptographic primitives and hardware security mechanisms for FPGA platforms, including the Xilinx Cmod A7. These projects connected cryptographic algorithms with practical architectural choices involving resource usage, parallelism, and memory organization.

## AES-128 Architectures

Implemented multiple AES architectures, including LUT-based, BRAM-based, byte-serial, and column-based designs, alongside AES decryption. Working across these architectures developed my understanding of how resource sharing and parallelism influence throughput, area, and the internal activity of a cryptographic circuit.

## Keccak-f[1600]

Designed the permutation at the core of SHA-3, translating its state transformations and round operations into RTL. This provided experience with a cryptographic structure different from AES and with organizing wide datapaths and iterative computation.

## Arbiter Physical Unclonable Function (PUF)

Implemented an arbiter PUF, exploring how physical path-delay differences can support device identification. The project introduced the importance of implementation asymmetry, response stability, and resistance to predictive modeling.

## Security and Attack Insights

These projects strengthened my understanding that cryptographic security depends on the hardware implementation as well as the algorithm. Architectural choices affect switching activity, timing, and intermediate-state exposure, properties relevant to side-channel leakage and fault attacks. PUF design also highlighted the distinction between generating device-dependent responses and demonstrating resistance to modeling attacks.

<p style="font-size: 0.85em; margin-top: 0;"><em>RTL Design · Cryptography · FPGA · Xilinx Vivado</em></p>

[Back to Projects]({{ '/projects/' | relative_url }})
