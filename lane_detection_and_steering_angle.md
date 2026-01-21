# 📌 Lane Detection and Steering Angle Estimation

**Lane Detection and Steering Angle Estimation** is a vision-based perception and control system that detects lane regions and estimates the steering angle using deep learning and filtering techniques. The project integrates semantic segmentation, geometric curve fitting, and Kalman filtering into a complete pipeline designed for autonomous driving applications. :contentReference[oaicite:1]{index=1}

Repository: https://github.com/alvitowongsonegoro-bit/Lane-Detection-and-Steering-Angle-Estimation.git
---

## 🧠 Project Summary

Lane detection and steering estimation are fundamental tasks in autonomous driving and driver-assistance systems. Traditional methods based on classical computer vision struggle with lighting changes, shadows, and road texture variations. This project combines a **U-Net deep learning model** with signal smoothing using a **Kalman Filter** to produce robust lane segmentation and smooth steering angle estimation. :contentReference[oaicite:2]{index=2}

---

## 🎯 Objectives

This project aims to:

- Perform **semantic segmentation for lane detection** using a U-Net CNN model. :contentReference[oaicite:3]{index=3}
- Extract lane boundaries from predicted segmentation masks. :contentReference[oaicite:4]{index=4}
- Estimate steering angles from lane geometry (curve fitting). :contentReference[oaicite:5]{index=5}
- Apply a **Kalman Filter** to smooth steering estimates. :contentReference[oaicite:6]{index=6}
- Demonstrate an end-to-end perception → estimation pipeline for autonomous navigation. :contentReference[oaicite:7]{index=7}

---

## 🛠️ System Pipeline

```text
Stereo Camera Input
        ↓
Image Preprocessing
        ↓
U-Net Lane Segmentation
        ↓
Lane Mask Generation
        ↓
Lane Boundary Extraction
        ↓
Polynomial Curve Fitting
        ↓
Steering Angle Estimation
        ↓
Kalman Filter for Smoothing
        ↓
Smoothed Steering Output
```
📊 Dataset Description

- The dataset contains image–mask pairs where:

  - Image: Front-facing RGB road image frame.

  - Mask: Binary segmentation mask labelling the lane region (white for lane area, black for background).

- Preprocessing includes:

  - Resizing to standard input size.

  - Normalizing pixel values.

  - Converting masks to binary.

🧠 U-Net Model Details

- Architecture: Modified U-Net for binary segmentation.

- Activation: Sigmoid.

- Loss: Binary Cross Entropy.

- Optimizer: Adam.

- Trained from scratch on custom lane dataset.

📈 Steering Angle Estimation

- After segmentation, lane boundaries are extracted and approximated with a 2nd-order polynomial curve. The tangent of this curve is used to compute a steering angle. Noise and frame-to-frame variation are minimized using a Kalman Filter, resulting in a smoother steering output.

⚠️ Limitations

- Binary segmentation does not distinguish between left/right lanes.

- Reflection, shadows, and wet surfaces can still reduce performance.

- Real-time optimization and hardware integration are future goals.

🔧 Installation Instructions

- To install required dependencies:

```text
git clone https://github.com/alvitowongsonegoro-bit/Lane-Detection-and-Steering-Angle-Estimation.git
cd Lane-Detection-and-Steering-Angle-Estimation
pip install -r requirements.txt
```

🚀 Usage

- Prepare your dataset in folders under datasets/.

- Run notebook 01_data_preprocessing.ipynb to preprocess data.

- Train U-Net with 02_unet_training.ipynb.

- Run inference with 03_lane_inference.ipynb.

- Estimate steering angle and smooth with Kalman filter using 04_steering_angle_kalman.ipynb.

🧑‍💻 Authors

1. Alvito Danendra Putra

2. Ben Arthur

3. Nathan Shaun

4. William Henry
