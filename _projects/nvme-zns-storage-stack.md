---
layout: page
title: User-Space NVMe/ZNS Storage Stack
permalink: /projects/nvme-zns-storage-stack/
description: Built a storage stack with flash translation, garbage collection, and RocksDB integration, validated on QEMU-emulated ZNS devices.
importance: 4
category: work
selected: true
project_icon: /assets/img/project-icons/storage.svg
github: https://github.com/Amir-Yazdanpanah/storage-system-m1
technologies: C/C++ · Linux · QEMU · NVMe/ZNS · libnvme · RocksDB
---

<p style="font-size: 0.9rem;">
  <a href="{{ page.github }}"><i class="fa-brands fa-github" aria-hidden="true"></i> View on GitHub</a>
</p>

<img src="{{ '/assets/img/projects/nvme-zns-storage-stack/stosys-fig1.png' | relative_url }}" alt="StoSys course overview, from NAND flash and NVMe interfaces to filesystems, key-value stores, and distributed systems." width="1899" height="1066" style="max-width: 100%; height: auto;">

Developed a user-space storage stack following the practical assignments of the [Storage Systems (StoSys) course](https://animeshtrivedi.github.io/course-stosys/). The project connects low-level NVMe device operations with filesystem design and database integration, using QEMU-emulated Zoned Namespace (ZNS) devices.

The central challenge was to support arbitrary logical-block updates over storage organized around sequentially written zones. I implemented a hybrid log-structured flash translation layer (FTL), combining page-level mapping for the log region with zone-level mapping for the data region.

<img src="{{ '/assets/img/projects/nvme-zns-storage-stack/stosys-fig2.png' | relative_url }}" alt="Hybrid FTL design: user writes enter an LBA-mapped log zone, then garbage collection and compaction move data into zone-mapped data zones." width="1716" height="615" loading="lazy" style="max-width: 100%; height: auto;">

My implementation included:

- **Device access:** NVMe reads, writes, zone append/reset operations, and I/O splitting based on the maximum transfer size.
- **Storage management:** address translation and synchronized background garbage collection.
- **Filesystem integration:** a custom filesystem connected to RocksDB through its FileSystem API.
- **Persistence and validation:** metadata recovery across orderly shutdowns, tested using sequential, random, and database restart workloads.

<img src="{{ '/assets/img/projects/nvme-zns-storage-stack/stosys-fig3.png' | relative_url }}" alt="User-space storage stack connecting RocksDB through its filesystem API to libstosys, log and data regions, background garbage collection, and the NVMe device." width="1535" height="957" loading="lazy" style="max-width: 100%; height: auto;">

The course consists of five assignments as follows:

## Assignment 1: NVMe/ZNS Device Access

Configured a Linux development environment with QEMU-emulated Zoned Namespace (ZNS) devices. Implemented device operations using libnvme, including reads, writes, zone append, and zone reset, with I/O splitting to respect the device’s maximum transfer size. This established the foundation for working with zone capacity, write pointers, and sequential-write constraints.

## Assignment 2: Hybrid Flash Translation Layer

Implemented a host-side, hybrid log-structured flash translation layer (FTL) that exposes a logical-block interface over the ZNS device. Combined page-level mapping in the log region with zone-level mapping in the data region, translating logical addresses into physical storage locations while respecting zone-writing rules.

## Assignment 3: Background Garbage Collection

Extended the FTL with garbage collection to reclaim space and support repeated updates to logical addresses. Implemented cleaning in a separate background thread, coordinating data movement, mapping updates, and zone reclamation with foreground reads and writes. Validated data integrity under sequential, random, and repeated-overwrite workloads.

## Assignment 4: Filesystem and RocksDB Integration

Built a custom filesystem above the FTL and integrated it with RocksDB through its FileSystem API. Connected database file operations to the underlying storage stack, managing file metadata and storage allocation while coordinating concurrent access. Validated key-value operations against a reference database using the host filesystem.

## Assignment 5: Persistence and Restart

Implemented persistence for FTL and filesystem metadata, allowing the stack to restore its state after an orderly shutdown. Verified that previously stored RocksDB records remained accessible and consistent across database restarts.

This project strengthened my experience in systems programming, storage abstractions, concurrency, and the interaction between device constraints and application behavior.

**Technologies:** C/C++ · Linux · QEMU · NVMe/ZNS · libnvme · RocksDB

Project structure and educational materials: [Storage Systems (StoSys)](https://animeshtrivedi.github.io/course-stosys/), [Animesh Trivedi](https://animeshtrivedi.github.io/) and collaborators.

[Back to Projects]({{ '/projects/' | relative_url }})
