# Music Genre Classification

This repository contains the project report for a **Music Genre Classification** study comparing classical machine learning baselines with deep learning approaches on music datasets.

The project explores how different audio representations and model architectures affect classification performance across multiple datasets.

📄 **Project Report:**  
[Music_Genre_Classification___Progress_Report.pdf](Music_Genre_Classification___Progress_Report.pdf)

> Note: This repository contains the **project report only**. Training and inference code are not included.

---

# Project Overview

Music genre classification is a common problem in music information retrieval (MIR).  
However, it becomes challenging in practice due to:

- Label noise in real-world datasets
- Overlapping genre characteristics
- Class imbalance between genres

This project investigates different approaches to classify music tracks using both **classical machine learning** and **deep learning models**.

---

# Datasets

The experiments use the following widely used music datasets:

**GTZAN**
- 1000 audio clips
- 10 genres
- 30 seconds per track
- Sample rate: 22,050 Hz

**FMA-small**
- 8,000 tracks
- 8 balanced genres

**FMA-medium**
- 25,000 tracks
- 16 genres
- Highly imbalanced class distribution

---

# Methods

## Audio Representation

Audio tracks are converted into **log-mel spectrograms**, which are commonly used for deep learning on audio signals.

Configuration:
- 128 mel frequency bands
- Hop length: 512
- FFT size: 1024 / 2048
- Amplitude converted to decibel scale

For sequence modeling, tracks are also split into **short segments** which are later aggregated by a transformer model.

---

## Models

The project compares both classical and deep learning approaches.

### Classical Machine Learning
- Logistic Regression
- PCA + RBF-SVM

These models use **handcrafted audio features** from the FMA dataset.

### Deep Learning
- Convolutional Neural Network (CNN) operating on spectrograms
- CNN–Transformer architecture combining convolutional feature extraction with transformer-based sequence aggregation

---

# Training Strategy

Deep learning models are trained using:

- **AdamW optimizer**
- Learning rate: 2e-4
- Weight decay: 1e-3
- Gradient clipping
- Mixed precision training (FP16)
- Early stopping
- Learning rate scheduling (ReduceLROnPlateau)

---

# Key Results

### GTZAN
- PCA + RBF-SVM: **91.9% accuracy**
- CNN: **75.0% accuracy**

### FMA-small
- Logistic Regression: **53.7% accuracy**
- PCA + RBF-SVM: **~58.0% accuracy**
- CNN: **59.1% accuracy**

### FMA-medium
- CNN–Transformer: **69.2% accuracy**
- Macro F1: **0.394**
- Weighted F1: **0.697**

The experiments show that handcrafted features perform strongly on clean datasets, while deep learning models scale better to larger and noisier datasets.

---

# Authors

- Yunus Emre Ulusoy  
- Semih Dogan  
- Alp Eren Gül  
- Burak Ala  
- Umut Köprülü
