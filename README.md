# SentinelGrid — Occlusion-Resistant 3D Crowd Counting

> An end-to-end multi-camera crowd counting and surveillance pipeline using YOLO, camera calibration, ground-plane projection, and cross-view spatial fusion.

SentinelGrid is an AI-powered multi-camera crowd counting system designed to estimate a unified number of people across overlapping camera views.

Instead of independently counting people in every camera and adding the results together—which can cause the same person to be counted multiple times—SentinelGrid projects detected people onto a shared ground plane and performs spatial fusion across camera views.

The project uses the **WILDTRACK multi-camera pedestrian dataset** for model training and evaluation.

---

## ✨ Features

- 🎥 Multi-camera person detection
- 🤖 YOLO-based deep person detection
- 📐 Camera calibration and geometric projection
- 🌍 Image-to-ground-plane homography transformation
- 🔄 Cross-camera spatial fusion
- 👥 Unified crowd counting
- 🗺️ Bird's-eye occupancy visualization
- 🚨 Configurable crowd-capacity alerts
- 📊 Event statistics and CSV logging
- 🔬 WILDTRACK-based training and evaluation
- 🌐 Web dashboard for visualizing results
- 📡 FastAPI backend for analysis and geometry APIs

---

## 🧠 How It Works

The SentinelGrid pipeline follows these steps:

```text
                 ┌─────────────────────┐
                 │  Multiple Cameras   │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │   YOLO Detection    │
                 │   Person Detection  │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │  Foot-point        │
                 │  Extraction         │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Ground-plane        │
                 │ Homography          │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Cross-view Spatial  │
                 │ Fusion              │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Unified Crowd Count │
                 └──────────┬──────────┘
                            │
                 ┌──────────┴──────────┐
                 ▼                     ▼
        ┌─────────────────┐   ┌─────────────────┐
        │ Bird's-eye Map  │   │ Capacity Alerts │
        └─────────────────┘   └─────────────────┘
