<p align="center">
  <h1 align="center">🚦 Traffic Sign Classification</h1>
  <p align="center">
    A deep learning project that classifies <strong>43 categories</strong> of traffic signs using a LeNet-inspired CNN trained on the <a href="https://benchmark.ini.rub.de/">German Traffic Sign Recognition Benchmark (GTSRB)</a> dataset.
  </p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Keras-Sequential_CNN-D00000?logo=keras&logoColor=white" alt="Keras" />
  <img src="https://img.shields.io/badge/Accuracy-86.57%25-brightgreen" alt="Accuracy" />
  <img src="https://img.shields.io/badge/License-MIT-blue" alt="License" />
</p>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Preprocessing Pipeline](#preprocessing-pipeline)
- [Model Architecture](#model-architecture)
- [Training](#training)
- [Results](#results)
- [Installation & Usage](#installation--usage)
- [Dependencies](#dependencies)
- [Project Structure](#project-structure)
- [Future Improvements](#future-improvements)
- [License](#license)

---

## Overview

This project builds an end-to-end image classification pipeline that can recognize **43 different types** of German traffic signs (speed limits, warnings, prohibitions, etc.). The model is based on a modified **LeNet-5** architecture implemented with **Keras / TensorFlow** and achieves **86.57% test accuracy**.

The full workflow — from data loading and visualization, through preprocessing and model training, to evaluation and prediction visualization — is contained in a single Jupyter Notebook.

---

## Dataset

The project uses the **German Traffic Sign Recognition Benchmark (GTSRB)** dataset, stored as pickled files:

| Split        | Samples  | Image Size      |
|--------------|----------|-----------------|
| **Training**   | 34,799   | 32 × 32 × 3 (RGB) |
| **Validation** | 4,410    | 32 × 32 × 3 (RGB) |
| **Test**       | 12,630   | 32 × 32 × 3 (RGB) |

> **Note:** The dataset files (`train.p`, `valid.p`, `test.p`) are not included in this repository due to their size. You can download them from the [GTSRB benchmark website](https://benchmark.ini.rub.de/) or [Kaggle](https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign).

---

## Preprocessing Pipeline

Each image goes through the following preprocessing steps before being fed to the model:

1. **Shuffling** — Training data is shuffled to prevent order bias (`sklearn.utils.shuffle`)
2. **Grayscale Conversion** — RGB images are converted to single-channel grayscale by averaging across color channels
3. **Normalization** — Pixel values are normalized to the range **[-1, 1]** using the formula: `(pixel - 128) / 128`

Final input shape: **32 × 32 × 1**

---

## Model Architecture

The CNN follows a **LeNet-5**-inspired architecture:

```
┌─────────────────────────────────────────────────────┐
│ Input                              (32 × 32 × 1)    │
├─────────────────────────────────────────────────────┤
│ Conv2D       6 filters, 5×5, ReLU                   │
│ AveragePooling2D                   2×2              │
├─────────────────────────────────────────────────────┤
│ Conv2D       16 filters, 5×5, ReLU                  │
│ AveragePooling2D                   2×2              │
├─────────────────────────────────────────────────────┤
│ Flatten                                             │
│ Dense        120 units, ReLU                        │
│ Dense         84 units, ReLU                        │
│ Dense         43 units, Softmax    (output)         │
└─────────────────────────────────────────────────────┘
```

**Loss Function:** Sparse Categorical Crossentropy  
**Optimizer:** Adam (learning rate = 0.001)

---

## Training

| Parameter     | Value  |
|---------------|--------|
| Epochs        | 50     |
| Batch Size    | 500    |
| Optimizer     | Adam   |
| Learning Rate | 0.001  |

---

## Results

### Test Accuracy: **86.57%**

### Predictions on Test Set
<img width="1171" height="797" alt="Predictions on test images showing true vs predicted labels" src="https://github.com/user-attachments/assets/d8e929ea-a039-44d5-af40-5e75fd18556c" />

### Training & Validation Metrics
<img width="827" height="555" alt="Training and validation accuracy/loss curves over 50 epochs" src="https://github.com/user-attachments/assets/cb792d0e-1335-4be7-8f53-503b950c048c" />

The metric plots show training/validation accuracy and loss over 50 epochs. The model demonstrates steady convergence with the training set while maintaining reasonable generalization on the validation set.

---

## Installation & Usage

### 1. Clone the Repository

```bash
git clone https://github.com/TkWarrior/Road-Signal-Detector.git
cd Road-Signal-Detector
```

### 2. Install Dependencies

```bash
pip install numpy pandas matplotlib seaborn scikit-learn keras tensorflow
```

### 3. Download the Dataset

Place the following pickle files in the project root directory:
- `train.p`
- `valid.p`
- `test.p`

### 4. Run the Notebook

```bash
jupyter notebook "Traffic Sign Classification-checkpoint.ipynb"
```

Execute all cells sequentially to reproduce the full training and evaluation pipeline.

---

## Dependencies

| Package        | Purpose                                |
|----------------|----------------------------------------|
| Python 3.11+   | Runtime                                |
| NumPy          | Array operations & preprocessing       |
| Pandas         | Data manipulation                      |
| Matplotlib     | Visualization & plotting               |
| Seaborn        | Enhanced statistical visualizations    |
| scikit-learn   | Shuffling, confusion matrix            |
| Keras          | Model definition & training            |
| TensorFlow     | Backend for Keras                      |

---

## Project Structure

```
Road-Signal-Detector/
├── Traffic Sign Classification-checkpoint.ipynb   # Main notebook (full pipeline)
├── README.md                                       # Project documentation
├── train.p                                         # Training data (not tracked)
├── valid.p                                         # Validation data (not tracked)
└── test.p                                          # Test data (not tracked)
```

---

## Future Improvements

- 🔄 **Data Augmentation** — Apply rotation, zoom, and shift to increase training diversity
- 🏗️ **Deeper Architecture** — Experiment with VGG, ResNet, or other modern architectures
- 🎯 **Dropout & Regularization** — Add dropout layers to reduce overfitting
- 📈 **Learning Rate Scheduling** — Use callbacks to decay the learning rate during training
- 🌐 **Web App Deployment** — Build a Streamlit or Flask app for real-time sign classification
- 📊 **Per-Class Analysis** — Investigate performance on underrepresented classes

---

## License

This project is open source and available under the [MIT License](LICENSE).

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/TkWarrior">TkWarrior</a>
</p>
