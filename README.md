# ECE528-Project
# ASL Simple Sentence Recognition

### Team Members
- **Isa Fontana** — isafon8@colostate.edu  
- **Braedon McGuire** — Braedon.McGuire@colostate.edu  

---

## 📖 Overview

This project aims to recognize short **ASL sentence commands** (e.g., “open door”, “turn on lights”, “call help”) in **real time** using a **Raspberry Pi 4** and camera feed.  
Our system detects hand and pose keypoints, interprets them with a lightweight **temporal model**, and classifies full multi-word gestures locally on the Pi — no cloud connection required.

This project demonstrates real-time **embedded machine learning** for accessibility on constrained hardware, balancing accuracy, speed, and energy efficiency.

---

## ⚙️ Features

- Real-time **hand landmark extraction** using **MediaPipe Hands**  
- Lightweight **Temporal Convolutional Network (TCN)** or **GRU** sequence model  
- Runs entirely **offline** on **Raspberry Pi 4/5**  
- **Quantization-aware training** for speed and efficiency  
- Recognizes 5–10 fixed ASL commands with consistent grammar  

---

## 🧩 System Design

**Pipeline Overview:**
1. **Camera Input:** Live Pi Camera or USB webcam captures hand movements  
2. **Preprocessing:** Extracts 3D keypoints using Google’s MediaPipe Hands  
3. **Sequence Modeling:** A GRU or TCN interprets gesture sequences  
4. **Classification:** Model predicts full sentence command  
5. **Output:** Displays recognized sentence in terminal or GUI  

---

## 🧠 Model Details

- **Input:** 3D hand keypoints (x, y, z) from each frame  
- **Sequence Length:** 60 frames per clip (~2 seconds)  
- **Network Options:**
  - GRU-based RNN with 64–128 hidden units  
  - Temporal Convolutional Network (TCN)  
  - Tiny CNN for baseline comparison  
- **Optimization:** Adam optimizer, early stopping, label smoothing  
- **Deployment:** TensorFlow Lite with post-training quantization  

---

## 🧪 Data

We are combining public datasets with our **custom dataset**:
- [GeeksforGeeks ASL Recognition](https://www.geeksforgeeks.org/machine-learning/sign-language-recognition-system-using-tensorflow-in-python)
- [CodingSamrat/Sign-Language-Recognition](https://github.com/CodingSamrat/Sign-Language-Recognition)
- [DataFlair Sign Language ML Project](https://data-flair.training/blogs/sign-language-recognition-python-ml-opencv)
- WLASL dataset for word-level ASL samples

**Custom Dataset Collection:**
- ~15 fixed ASL sentence classes  
- 5+ volunteers with varying hand sizes and skin tones  
- Each participant records 10–20 samples per sentence at 30 FPS  
- Annotated and trimmed clips with motion thresholding  

---

## 📊 Evaluation Metrics

**Quantitative Metrics**
- Accuracy, Precision, Recall, and F1-score per sentence class  
- Frame rate (FPS), end-to-end latency, and model size after quantization  

**Qualitative Outputs**
- Confusion matrices for model understanding  
- Real-time classification demo running on the Raspberry Pi  

---

## 🚀 Deployment

**Hardware:**
- Raspberry Pi 4 (or 5)
- Pi Camera / USB webcam

**Software:**
- Python 3.11+
- TensorFlow Lite
- OpenCV
- MediaPipe

**Run on Pi:**
```bash
python3 main.py
