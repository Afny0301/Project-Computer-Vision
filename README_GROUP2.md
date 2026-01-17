# Stereo Vision Vehicle Detection and Distance Estimation

## 1. Project Description
This project focuses on implementing a **computer vision system for vehicle detection and distance estimation** using a **stereo vision setup** combined with **YOLOv8** object detection.

The system detects **cars and trucks** in real time using deep learning and estimates their **distance in meters** by computing depth from stereo image disparity. By integrating object detection with stereo vision, the project provides both **semantic understanding** (object type) and **spatial awareness** (distance), which are essential for autonomous driving and intelligent transportation systems.

---

## 2. Dataset
The dataset used in this project consists of:
- **Stereo image pairs** captured using two identical webcams
- **Labeled vehicle images** for YOLO training

### Dataset Details:
- **Training images:** 2531
- **Testing images:** 361
- **Classes:**
  - `0` → Car
  - `1` → Truck

Due to GitHub file size limitations, **large video files and raw datasets are not included** in this repository. Users are expected to prepare or download their own stereo image or video data and place them in the appropriate folders for testing.

---

## 3. Methodology
The system follows a structured computer vision pipeline:

### 3.1 Image Preprocessing
- Grayscale conversion to reduce computational complexity
- Histogram equalization to enhance contrast
- Gaussian blur to reduce noise

### 3.2 Feature Enhancement
- Sobel edge detection to highlight vehicle contours
- Edge normalization for consistency
- Histogram of Oriented Gradients (HOG) to capture vehicle shape and texture

### 3.3 Vehicle Detection
- YOLOv8n is used for detecting vehicles
- Lightweight architecture enables real-time performance
- Outputs bounding boxes and class labels (car or truck)

### 3.4 Stereo Vision and Depth Estimation
- Stereo camera calibration and rectification
- Disparity map computation from rectified images
- Depth calculation using the stereo vision equation:

Depth = (Focal Length × Baseline) / Disparity


---

## 4. Analysis and Results
The system successfully detects vehicles and estimates their distance with reliable accuracy.

### Calibration Results:
- Stereo RMS (baseline): **0.1035 m**
- Stereo RMS (pixel): **0.9896 px**
- Mean reprojection error: **0.0422 px**

### Observations:
- Rectified images show parallel epipolar lines, confirming correct calibration
- Disparity maps clearly represent depth differences
- Depth estimation results are consistent with real-world distances
- The combination of YOLOv8 and stereo vision provides robust spatial perception

Screenshots of detection results, rectified images, disparity maps, and depth visualization are included in the `results/` folder.

---

## 5. Code and Documentation
All source code and documentation for this project are available on GitHub:

🔗 **GitHub Repository:**  
https://github.com/Val87Anto/Stereo-Vision-Vehicle-Distance-Estimation-And-Detection

The repository includes:
- Vehicle detection modules
- Stereo calibration and rectification scripts
- Disparity and depth estimation code
- Result visualizations and documentation

---

## 6. Presentation Slides (PPT)
The presentation slides used to explain this project are available in the GitHub repository:

📊 **Project Presentation (PPT):**  
https://github.com/Val87Anto/Stereo-Vision-Vehicle-Distance-Estimation-And-Detection

(Please navigate to the presentation file inside the repository.)

---

## Team Members
- **Valerie Liang Alianto** (Leader)
- Jonathan Matthew Halim
- Sachika Valenlie
- Bryan Stevensen Kho
