# MC3DTrackNet: End-to-End Multi-Camera 3D Object Detection and Tracking

MC3DTrackNet is a lightweight, end-to-end framework for **3D multi-object detection and tracking** using **only multi-camera RGB images**, designed for autonomous driving scenarios.  
The model avoids LiDAR, BEV transformers, object queries, and attention mechanisms, achieving strong tracking performance with low computational cost.

---

## 📌 Motivation
Most existing 3D tracking systems rely on LiDAR or heavy transformer-based architectures, which are expensive and difficult to deploy in real-time systems.  
MC3DTrackNet addresses this by using **camera-only inputs** and a **simple yet effective grid-based BEV representation**, making it suitable for real-world autonomous driving applications.

---

## 🧠 Key Contributions
- End-to-end **camera-only** 3D detection and tracking framework
- Lightweight architecture without:
  - LiDAR
  - Object queries
  - Temporal attention
  - Re-ID modules
- Simple multi-camera fusion using **average pooling**
- Grid-based BEV supervision for structured 3D reasoning
- Efficient identity association using **3D center-distance matching**

---

## 🏗️ Architecture Overview

### 1. Multi-Camera Feature Extraction
- Six synchronized camera images
- Shared **ResNet-50** backbone
- Feature dimensionality reduced using 1×1 convolutions

### 2. Multi-View Fusion
- Camera-wise features fused via **mean pooling**
- Produces a unified BEV-aligned feature map

### 3. Grid-Based 3D Detection
- Scene discretized into a **7×13 BEV grid**
- Each grid cell predicts:
  - Object class
  - 3D bounding box parameters `[x, y, z, w, l, h, yaw]`
- One object per grid cell (YOLO-style formulation)

### 4. Tracking & Association
- Motion prediction using linear velocity model
- Identity association using **3D center-distance Hungarian matching**
- No appearance-based Re-ID features required

---

## 📂 Dataset
- **nuScenes** autonomous driving dataset
- 6 synchronized RGB cameras per frame
- Standard nuScenes train/val/test splits

---

## ⚙️ Training Details
- Framework: **PyTorch**
- Loss Functions:
  - Focal Loss (classification)
  - Smooth L1 Loss (3D box regression)
- Optimizer: Adam
- End-to-end RGB-only supervision

---

## 📊 Results
- Achieves **state-of-the-art AMOTA and AMOTP** among vision-only methods
- Significantly fewer identity switches compared to transformer-based baselines
- Strong performance even with limited training data
- Suitable for **real-time deployment** due to low memory and compute cost

---

## 📈 Evaluation Metrics
- AMOTA / AMOTP
- MOTA / MOTP
- Recall
- Identity Switches (IDS)
- Track Fragmentation (FRAG)

---

## 🧩 Skills & Concepts Demonstrated
- Multi-Camera Multi-Object Tracking (MC-MOT)
- 3D Object Detection
- BEV-based spatial reasoning
- End-to-end deep learning pipelines
- PyTorch
- Autonomous driving perception
- nuScenes benchmark evaluation

---

## ✨ Acknowledgements
- Internship at NIT Tiruchirappalli, Dept. of CSE
- Mentorship by Dr. Brindha M, Associate Professor
