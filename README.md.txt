# Distorted Visual Sequence Pattern Recognition

## Overview

Deep learning solution for recognizing distorted CAPTCHA-like text sequences from grayscale images.

## Dataset

- Training Images: 20,000
- Test Images: 5,000
- Image Size: 200x100
- Fixed Sequence Length: 6

## Model

- EfficientNet-B0 Backbone
- Multi-Head Classification Architecture
- 6 Independent Character Heads
- Label Smoothing
- Mixed Precision Training
- Early Stopping

## Results

- Best Validation CER: 0.0002
- Word Accuracy: 99.9%
- Best Epoch: 20

## Files

- notebook/OCR_Captcha_Solution_24410023.ipynb
- submission/submission_niyant_24410023.csv
- model/best_model.pth

## Author

Niyant
Enrollment No: 24410023