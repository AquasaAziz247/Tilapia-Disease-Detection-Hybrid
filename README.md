# 🐟 Tilapia Fish Disease Detection using Hybrid Deep Learning

## 📌 Project Overview

This project implements a **hybrid deep learning system** to detect whether a **Tilapia fish is Healthy or Diseased** from images.

The system combines:
- **YOLOv8 (Object Detection)** for visible disease regions
- **CNN (EfficientNet-based Classifier)** for overall fish health judgment

The hybrid approach is designed to **minimize false negatives**, which is critical in disease detection systems.

---

## 🎯 Problem Statement

In aquaculture, early disease detection is essential to:
- Prevent large-scale fish loss
- Maintain fish quality
- Enable timely medical intervention

Single-model systems often fail when:
- Disease patterns are subtle
- Lighting/background conditions vary
- Disease does not appear as a clear object

---

## 🧠 Hybrid Solution Strategy

### 🔹 YOLOv8 (Detection Model)
- Detects visible disease regions on fish skin
- Highly precise when disease patterns are obvious

### 🔹 CNN (Classification Model)
- EfficientNet-based architecture
- Learns global texture, color, redness, and scale damage
- Works even when disease regions are not clearly localized

### 🔹 Final Decision Logic
1. YOLO runs first
2. If YOLO detects disease with sufficient confidence → **Diseased**
3. Otherwise, CNN prediction is used

This strategy significantly reduces **false negatives**.

---

## 🧱 System Architecture

Input Image
│
├── YOLOv8 Detector
│ └── Disease detected → Diseased
│
└── CNN Classifier
└── Healthy / Diseased


---

## 📂 Dataset Structure

### YOLO Dataset (Detection)
tilapia_yolo_cleaned/
├── train/images
├── train/labels
├── valid/images
├── valid/labels
└── data.yaml


### CNN Dataset (Classification)
classifier_dataset/
├── train/
│ ├── healthy/
│ └── diseased/
├── val/
│ ├── healthy/
│ └── diseased/
└── test/
├── healthy/
└── diseased/


---

## ⚙️ Final Inference Configuration (Locked)

These values were finalized after error analysis:

- YOLO confidence threshold: **0.25**
- YOLO minimum bounding box area: **0.03**
- CNN architecture: **EfficientNet**
- Priority metric: **Disease Recall**

📌 False positives are acceptable; false negatives are not.

---

## 📊 Final Performance (Test Set)

| Metric | Value |
|------|------|
| Accuracy | ~95% |
| Precision | ~95% |
| Recall (Diseased) | **100%** |
| F1-score | ~95% |

The hybrid model outperforms standalone YOLO or CNN models.

---

## 🖼️ Qualitative Results

- Correct healthy predictions
- Correct diseased predictions
- Reduced false positives after threshold tuning
- Confusion matrix included

See the `results/` folder for visual outputs.

---


## 🧪 Error Analysis & Design Decisions
Why Hybrid Model?
YOLO alone may miss subtle disease patterns

CNN alone may miss localized visible lesions

The hybrid approach combines both strengths and reduces failure cases

Why Allow False Positives?
In disease detection systems:

Missing a diseased fish is more harmful than flagging a healthy one.

Therefore, the model prioritizes recall over precision.

## 🛠️ Technologies Used
- Python
- PyTorch
- Ultralytics YOLOv8
- Torchvision
- EfficientNet
- Scikit-learn
- Matplotlib
- Google Colab
- Gradio

## 📌 Future Enhancements
- Multi-class disease classification
- Video-based disease analysis
- Mobile or web deployment
- Expansion to other fish species

## 👩‍💻 Author
- Your Name: Aquasa Aziz
- B.Tech: Computer Science and Business System
- Specialization: AI / Machine Learning

## 📜 License
This project is intended for academic and research purposes only.
