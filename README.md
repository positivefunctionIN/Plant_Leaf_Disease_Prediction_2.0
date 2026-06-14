# Plant Disease Detection using CNN with Grad-CAM

## 📌 Project Overview

This project builds a deep learning model to detect plant diseases from leaf images. It supports **38 disease classes** across crops like potato, tomato, apple, and corn. The model not only predicts the disease but also uses **Grad-CAM** to show which part of the leaf influenced its decision.

---

## 🎯 What I Learned & Built

| Category | Details |
|----------|---------|
| **Model** | CNN from scratch using TensorFlow/Keras |
| **Dataset** | PlantVillage (54,000 images, 38 classes) |
| **Image Size** | 128×128 pixels |
| **Accuracy** | 75% training, 68% validation |
| **Explainability** | Grad-CAM heatmaps |
| **Best Test** | Potato Late Blight - 99.92% confidence |

---

## 🏗️ Model Architecture
Conv2D(32, 3x3) + MaxPooling(2x2)
Conv2D(64, 3x3) + MaxPooling(2x2)
Conv2D(128, 3x3) + MaxPooling(2x2)
Flatten
Dense(256) + Dropout(0.5)
Dense(38) + Softmax



**Total Parameters:** 6,525,798

---

## 🔥 Grad-CAM (Explainable AI)

Grad-CAM answers: *"Which part of the leaf made my model predict this disease?"*

### How It Works

| Step | What Happens |
|------|--------------|
| 1 | Image passes through model until last conv layer |
| 2 | Gradients of predicted class are calculated |
| 3 | Gradients are averaged to get importance per feature map |
| 4 | Weighted sum of feature maps creates a heatmap |
| 5 | Heatmap overlays on original image (red = important) |

### Why It Works
- **Last conv layer** preserves spatial info (where things are)
- **Gradients** tell us which neurons matter most
- **ReLU** removes negative influences (only show what activates the class)

---

## 📊 Results & Testing

### Test Image 1: Potato Leaf with Spots

| Original | Grad-CAM | Overlay |
|----------|----------|---------|
| Potato leaf with brown lesions | Heatmap shows red on lesions | Red overlay on diseased spots |

**Prediction:** Potato___Late_blight  
**Confidence:** 99.92%  
**Top 3:** 1. Late Blight (99.92%), 2. Tomato Late Blight (0.07%), 3. Tomato Septoria (0.00%)

### Test Image 2: Healthy Tomato Leaf

**Prediction:** Tomato___Healthy  
**Confidence:** 87%  
**Heatmap Focus:** Diffuse, no specific hotspots

### Test Image 3: Apple Scab

**Prediction:** Apple___Scab  
**Confidence:** 91%  
**Heatmap Focus:** Dark circular spots highlighted

---
