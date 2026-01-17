# Traffic Sign Detection Project (YOLOv8)

Repository (submission link):  
https://github.com/satriosaroyobinus-boop/Traffic_Sign_Detection_Project.git

## Overview
Project ini adalah sistem **deteksi rambu lalu lintas** berbasis **Computer Vision** menggunakan **YOLOv8 (YOLOv8n)**. Model dilatih menggunakan dataset dari **Roboflow** (format YOLOv8) dan dapat diuji secara real-time melalui **webcam/external camera**.  
Selain training baseline, project ini juga menambahkan tahap **image enhancement (CLAHE)** untuk mencoba meningkatkan kualitas citra pada kondisi pencahayaan yang kurang ideal.

## Objectives
- Membangun model object detection untuk mengenali rambu lalu lintas.
- Melatih dan mengevaluasi model YOLOv8n menggunakan dataset Roboflow.
- Menguji inferensi secara real-time memakai webcam.
- Menerapkan **image enhancement (CLAHE)** sebagai bagian dari eksperimen pre-processing.

## Project Pipeline (Simple)
1. **Dataset (Roboflow → YOLOv8 format)**
   - Struktur folder: `train/images`, `train/labels`, `valid/images`, `valid/labels`, `test/images`, `test/labels`
2. **Image Enhancement (Optional)**
   - CLAHE diterapkan ke gambar → output ke folder `train_enh/images`, `valid_enh/images`, `test_enh/images`
   - Label tetap sama (copy labels ke folder `_enh`)
3. **Training YOLOv8n**
   - Train baseline: `data.yaml`
   - Train enhanced: `data_enh.yaml`
4. **Evaluation**
   - Metrik umum: precision, recall, mAP50, mAP50-95 (dari output training Ultralytics)
5. **Real-time Inference**
   - Deteksi dari webcam dan tampilkan bounding box + label + confidence

## Dataset
- Source: Roboflow (Traffic Signs dataset)
- Format export: YOLOv8 (images + labels .txt + config `data.yaml`)
- `data.yaml` berisi path dataset train/val/test dan daftar kelas (names).

## Tech Stack
- Python 3.11+
- Ultralytics YOLOv8
- OpenCV (cv2)
- NVIDIA GPU (CUDA) (opsional, jika tersedia)

## Repository Structure (example)
> Struktur bisa menyesuaikan folder kamu, tapi intinya seperti ini.


## How to Run (Quick Guide)

### 1) Install dependencies
> Jalankan dari folder project:
```bash
pip install -r requirements.txt
```
### 2) Training (Baseline)
```bash
python code/train_traffic_sign.py
```
### 3) Image Enhancement (CLAHE) + Training Enhanced
> Generate enhanced images:
```bash
python code/enhance_clahe.py
```
> Train dengan dataset enhanced (gunakan data_enh.yaml):
```bash
python code/train_traffic_sign.py
```
### 4) Real-time detection (Webcam / External Camera)
```bash
python code/detect_sign.py
```
- source=0 untuk kamera default
- Jika webcam eksternal: coba source=1 atau source=2

Notes (Important)

- Folder runs/ akan terisi otomatis setiap training (berisi weights/best.pt, grafik, confusion matrix, dll).

- Label .txt tidak berubah saat enhancement (yang berubah hanya images).

- Jika hasil enhancement terlihat “lebih buram”, tuning parameter CLAHE (clipLimit / tileGridSize) diperlukan agar tidak over-enhance.

Team Members

1. Muhammad Randy
2. Satrio Wicaksono Saroyo
3. Fernando Adreas Lim
4. Alvin Oentoro Abadi 
