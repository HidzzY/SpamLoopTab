# 🛠️ System Resilience & Synthetic Workload Generator

[![Build-Status](https://img.shields.io/badge/Build-Stable-green)](#)
[![License](https://img.shields.io/badge/License-MIT-blue)](#)
[![Platform](https://img.shields.io/badge/Environment-Browser--Based-orange)](#)

A high-performance system benchmarking tool designed to evaluate the operational limits of modern computing architectures. This suite executes synchronized stress-vectors across the CPU, RAM, and GPU to analyze thermal throttling, memory heap management, and rasterization throughput.

---

## 🔬 Technical Overview

This project implements a multi-vectored approach to hardware saturation using the V8 Engine's execution pipeline. 

### ⚡ Core Execution Engines

#### 1. Recursive CPU Saturation (`burnCPU`)
* **Mechanism:** Utilizing a high-frequency recursive loop executing $5 \times 10^6$ floating-point operations per cycle.
* **Architecture:** Deployed across 4 independent threads (asynchronous loops) to ensure maximum core-clock utilization.
* **Goal:** Testing instruction cycle stability and CPU thermal resistance.

#### 2. Dynamic Heap Allocation (`burnRAM`)
* **Mechanism:** Continuous injection of high-density array objects (500,000 elements/block) into the global state.
* **Interval:** 100ms polling rate to bypass standard Garbage Collection (GC) latency.
* **Goal:** Monitoring memory management thresholds and Out-Of-Memory (OOM) handling.

#### 3. GPU Rasterization Stress (`burnGPU`)
* **Mechanism:** Mass-parallel draw calls (1,000 instructions per frame) using the HTML5 Canvas API and `requestAnimationFrame`.
* **Visuals:** High-frequency RGB fill-rect randomization.
* **Goal:** Stress-testing the GPU’s fill rate and VRAM buffer efficiency.

---

## 🚀 Deployment & Usage

### Setup
Ensure you have a modern browser (Chromium-based recommended for V8 optimization).

1. Clone the repository:
   ```bash
   git clone [https://github.com/wahidofficial/system-resilience.git](https://github.com/wahidofficial/system-resilience.git)
