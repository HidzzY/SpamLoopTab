# 🛠️ System Resilience & Synthetic Workload Generator

[![Build-Status](https://img.shields.io/badge/Build-Stable-green)](#)
[![License](https://img.shields.io/badge/License-MIT-blue)](#)
[![Platform](https://img.shields.io/badge/Environment-Vercel--Edge-black)](#)
[![Deployment](https://img.shields.io/badge/Maintained%20By-HidzzY%20Tamvan-191919)](#)

A high-performance system benchmarking tool designed to evaluate the operational limits of modern computing architectures. This suite executes synchronized stress-vectors across the CPU, RAM, and GPU to analyze thermal throttling, memory heap management, and rasterization throughput.

---

## 🔬 Technical Analysis

Proyek ini menerapkan pendekatan **multi-vectored** untuk saturasi hardware melalui optimasi V8 Engine execution pipeline.

| Resource | Method | Complexity | Target Objective |
| :--- | :--- | :--- | :--- |
| **CPU** | Recursive FP Ops | $O(n \times 4)$ | Thermal Throttling Analysis |
| **RAM** | Heap Injection | Exponential | Garbage Collection Latency |
| **GPU** | Mass Rasterization | High-Frequency | VRAM Buffer Saturation |

### ⚡ Core Execution Engines

#### 1. Recursive CPU Saturation (`burnCPU`)
* **Mechanism:** Memanfaatkan loop rekursif frekuensi tinggi yang mengeksekusi $5 \times 10^6$ operasi *floating-point* per siklus.
* **Architecture:** Terdistribusi pada 4 thread independen (asynchronous loops) untuk memastikan utilisasi core-clock maksimal.

#### 2. Dynamic Heap Allocation (`burnRAM`)
* **Mechanism:** Injeksi kontinyu objek array dengan densitas tinggi (500,000 elemen per blok) ke dalam global state.
* **Interval:** Polling rate 100ms untuk melampaui ambang batas latensi *Garbage Collection* (GC).

#### 3. GPU Rasterization Stress (`burnGPU`)
* **Mechanism:** Instruksi *draw-calls* paralel (1,000 instruksi per frame) via HTML5 Canvas API.
* **Logic:** Sinkronisasi visual melalui `requestAnimationFrame` untuk saturasi frame buffer secara instan.

---

## 🚀 Live Environment

Proyek ini telah dideploy melalui infrastruktur **Vercel Edge Network** untuk memastikan distribusi beban yang stabil dan akses latensi rendah di seluruh region.

**Official Access:** [https://portofolio-digital.vercel.app](https://portofolio-digital.vercel.app)

---

## 🛑 Safety & Termination Protocols

Script ini menyertakan *low-level event listener* untuk mencegah sistem terkunci secara permanen pada lingkungan pengujian:

* **`Key_ESC`**: Memicu terminasi instan seluruh loop eksekusi dan melakukan pembersihan (*flushing*) pada primary memory heap.
* **Logs**: Pantau alokasi resource secara real-time melalui *Developer Console*.

---

## ⚖️ Disclaimer
Software ini dirancang untuk **tujuan riset dan pengujian sistem**. Penggunaan pada perangkat tanpa sistem pendingin yang memadai dapat menyebabkan degradasi hardware atau kehilangan data akibat sistem yang tidak responsif. 

---
**Architected by [HidzzY]** • *Full-Stack Engineer & Infrastructure Enthusiast.*

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FHidzzY%2FSpamLoopTab)
