# Music Genre Classification (Deep Learning + Classical Baselines)

This repository contains the project report for **Music Genre Classification: A Deep Learning Approach**, comparing classical handcrafted-feature pipelines with spectrogram-based deep models across **GTZAN** and **Free Music Archive (FMA)** subsets. :contentReference[oaicite:0]{index=0}

📄 **Report (PDF):**
- `report/Music_Genre_Classification___Progress_Report.pdf` (add the PDF here)

> **Code note:** This repository currently shares the **report only** (no training/inference code). The report documents datasets, preprocessing, model architectures, and experimental results. :contentReference[oaicite:1]{index=1}

---

## Project Summary

Music genre classification is challenging in real-world settings due to **label noise**, **overlapping genre boundaries**, and **class imbalance**. This project evaluates:
- **Handcrafted feature baselines** (FMA official feature set) with Logistic Regression and PCA + RBF-SVM
- **Log-mel spectrogram deep models**: a lightweight CNN and a **CNN–Transformer** that aggregates multiple segments per track :contentReference[oaicite:2]{index=2}

---

## Datasets

- **GTZAN**: 1,000 clips, 10 genres, 30s each @ 22,050 Hz :contentReference[oaicite:3]{index=3}  
- **FMA-small**: 8,000 tracks, 8 balanced genres :contentReference[oaicite:4]{index=4}  
- **FMA-medium**: 25,000 tracks, 16 genres, strongly imbalanced :contentReference[oaicite:5]{index=5}

---

## Methods (High-Level)

### Audio Representation
- **Log-mel spectrograms** (128 mel bands), hop length 512, FFT size 1024/2048, amplitude→dB :contentReference[oaicite:6]{index=6}  
- Segment-based setup for CNN–Transformer (e.g., 3s or 5s segments; multiple segments per track) :contentReference[oaicite:7]{index=7}

### Normalization
- Per-sample (local) z-score
- Global z-score (dataset-wide statistics)
- No normalization :contentReference[oaicite:8]{index=8}

### Models
- **Handcrafted baselines**: Logistic Regression; PCA + RBF-SVM :contentReference[oaicite:9]{index=9}  
- **CNN**: lightweight spectrogram CNN (~1.2M params) :contentReference[oaicite:10]{index=10}  
- **CNN–Transformer**: CNN encoder per segment + Transformer aggregator with a [CLS] token :contentReference[oaicite:11]{index=11}

### Training (Deep Models)
- AdamW, LR 2e-4, weight decay 1e-3
- ReduceLROnPlateau, gradient clipping, mixed precision (FP16), early stopping :contentReference[oaicite:12]{index=12}

---

## Key Results (from the report)

### GTZAN (clean/small)
- **PCA + RBF-SVM (handcrafted)**: **0.919 accuracy**
- **CNN (log-mel)**: **0.750 accuracy** :contentReference[oaicite:13]{index=13}

### FMA-small (noisier/balanced)
- Logistic Regression: **0.537**
- PCA + RBF-SVM: **~0.580**
- CNN (log-mel): **0.591** :contentReference[oaicite:14]{index=14}

### FMA-medium (noisy/long-tailed)
- Best CNN–Transformer config reported: **0.692 accuracy**, **Macro F1 = 0.394**, **Weighted F1 = 0.697** :contentReference[oaicite:15]{index=15}  
- Silent-segment filtering had a large impact (disabling it reduced accuracy substantially). :contentReference[oaicite:16]{index=16}

---

## Repository Structure (suggested)

---

## Authors / Contributions

- Yunus Emre Ulusoy 
- Semih Dogan 
- Alp Eren Gül  
- Burak Ala
- Umut Köprülü 

---

## References

See the report bibliography for full citations (GTZAN, FMA, and related deep learning baselines). :contentReference[oaicite:18]{index=18}
