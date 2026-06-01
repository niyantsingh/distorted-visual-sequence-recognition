# Distorted Visual Sequence Pattern Recognition using Deep Learning

<div align="center">

### CAPTCHA Recognition using EfficientNet-B0 Multi-Head Classification

**Author:** Niyant Singh
**Enrollment No:** 24410023

![Python](https://img.shields.io/badge/Python-3.10-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-red)
![OCR](https://img.shields.io/badge/Task-OCR-green)
![Competition](https://img.shields.io/badge/Type-CAPTCHA%20Recognition-orange)

</div>

---

## Project Overview

This project solves the **Distorted Visual Sequence Pattern Recognition** challenge using Deep Learning.

The objective is to accurately recognize hidden character sequences from heavily distorted grayscale CAPTCHA-style images containing:

* Background Noise
* Overlapping Characters
* Shape Deformation
* Visual Artifacts
* Occlusion
* Irregular Character Placement

The final system reconstructs the correct 6-character sequence directly from the image.

---

## Problem Statement

Given a distorted grayscale image containing an unknown sequence of characters, predict the exact ordered sequence.

### Example

**Input**

Distorted CAPTCHA Image

**Output**

```text
AXU323
```

The challenge is evaluated using **Character Error Rate (CER)**, where lower values indicate better performance.

---

## Dataset Analysis

| Feature              | Value                |
| -------------------- | -------------------- |
| Training Images      | 20,000               |
| Test Images          | 5,000                |
| Image Size           | 200 × 100            |
| Image Type           | PNG                  |
| Sequence Length      | Fixed (6 Characters) |
| Character Vocabulary | 31 Classes           |
| Challenge Type       | CAPTCHA Recognition  |

### Character Set

```text
23456789ABCDEFGHJKMNPQRSTUVWXYZ
```

Excluded characters:

```text
0 1 I L O
```

to avoid visual ambiguity.

---

## Exploratory Data Analysis

Key observations:

* Fixed-length sequence problem
* Binary grayscale images
* Heavy salt-and-pepper noise
* Significant character overlap
* Variable noise density
* No perspective distortion
* CAPTCHA-specific generation process

These findings influenced the final architecture selection.

---

## Model Architecture

### EfficientNet-B0 Multi-Head Classifier

The final solution uses:

```text
Input Image
      │
      ▼
 EfficientNet-B0
      │
      ▼
 Shared Feature Vector
      │
 ┌────┼────┬────┬────┬────┬────┐
 ▼    ▼    ▼    ▼    ▼    ▼
C1   C2   C3   C4   C5   C6
 │    │    │    │    │    │
31   31   31   31   31   31
Classes Classes Classes Classes Classes Classes
```

Each head predicts one character position.

---

## Why Multi-Head Classification?

Traditional OCR models such as:

* CRNN
* Attention OCR
* Transformer OCR

are designed for variable-length sequences.

Since the dataset always contains exactly **6 characters**, a multi-head classifier provides:

* Faster training
* Simpler architecture
* Better convergence
* Higher accuracy

---

## Training Strategy

### Preprocessing

* RGB → Grayscale
* Normalization
* Dataset Cleaning
* Anomaly Removal

### Data Augmentation

* Median Blur
* Morphological Dilation
* Morphological Erosion
* Small Geometric Transformations

### Optimization

| Parameter       | Value                       |
| --------------- | --------------------------- |
| Optimizer       | AdamW                       |
| Learning Rate   | 1e-3                        |
| Batch Size      | 128                         |
| Epochs          | 80                          |
| Scheduler       | CosineAnnealingWarmRestarts |
| Label Smoothing | 0.1                         |
| Mixed Precision | Enabled                     |
| Early Stopping  | Enabled                     |

---

## Evaluation Metrics

### Character Error Rate (CER)

Measures the number of insertions, deletions, and substitutions required to transform the predicted sequence into the target sequence.

Lower CER indicates better performance.

### Word Accuracy

Measures complete sequence correctness.

Higher is better.

---

## Results

### Validation Performance

| Metric        | Score  |
| ------------- | ------ |
| Best CER      | 0.0002 |
| Best Epoch    | 20     |
| Word Accuracy | 99.90% |

### Training Outcome

* Rapid convergence
* Stable validation performance
* No significant overfitting
* Early stopping successfully triggered

---

## Project Structure

```text
distorted-visual-sequence-recognition/
│
├── README.md
│
├── notebook/
│   └── OCR_Captcha_Solution_24410023.ipynb
│
└── submission/
    └── submission_niyant_24410023.csv
```

---

## Files Included

### Notebook

Complete end-to-end implementation including:

* Dataset Analysis
* EDA
* Preprocessing
* Augmentation
* Model Development
* Training Pipeline
* Evaluation
* Inference
* Submission Generation

### Submission File

Contains predictions for all 5000 test images.

---

## Model Weights

The trained checkpoint is not included due to repository size limitations.

Final model statistics:

```text
Best Validation CER : 0.0002
Best Epoch          : 20
Word Accuracy       : 99.90%
```

---

## Technologies Used

* Python
* PyTorch
* EfficientNet-B0
* Albumentations
* NumPy
* Pandas
* Matplotlib
* Scikit-Learn
* Google Colab

---

## Author

**Niyant Singh**
Enrollment No: **24410023**

Indian Institute of Technology Roorkee

---

## License

This repository is intended for academic and competition purposes.
