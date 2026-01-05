# Unsupervised Deep Learning for Quantifying Atypical Motor Signatures in ASD

[cite_start]This repository contains the official PyTorch implementation of the paper: **"Unsupervised Deep Learning Framework for Quantifying Atypical Motor Signatures in ASD"**[cite: 1].

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](LINK_TO_YOUR_NOTEBOOK)

## 📄 Abstract
Motor impairments are pervasive in Autism Spectrum Disorder (ASD) but are often assessed using subjective or supervised methods. [cite_start]This project introduces a **Spatio-Temporal Graph Convolutional Network Autoencoder (STGCN-AE)** trained exclusively on neurotypical (NT) movement data to establish a normative model[cite: 13]. [cite_start]By using reconstruction error as an anomaly score, we objectively quantify atypical motor patterns[cite: 14].

Key findings:
- [cite_start]Autistic individuals show higher reconstruction errors compared to NT controls[cite: 16].
- [cite_start]Atypicality correlates with **postural sway** and **jerk**[cite: 17].
- [cite_start]SHAP analysis reveals that atypicality is driven by complex feature combinations rather than single features[cite: 19].

## 🏗️ Architecture
The model uses a STGCN-AE architecture to process 3D skeletal data extracted from video via MediaPipe.

![Model Architecture](figures/architecture_diagram.png) 
[cite_start]*(Note: Upload Figure 2 from your PDF here [cite: 148])*

## 🛠️ Usage
The code is hosted in Google Colab for ease of use. 
1. [cite_start]**Preprocessing:** Extracts 24-joint skeletal data using MediaPipe and segments into 2-second windows[cite: 95, 102].
2. [cite_start]**Training:** Trains the STGCN-AE on NT data to minimize MSE[cite: 126].
3. [cite_start]**Analysis:** Calculates reconstruction error and runs XGBoost/SHAP for interpretability[cite: 208, 209].

## ⚠️ Data Privacy
[cite_start]Due to the sensitive nature of the dataset (video recordings of minors and adults with ASD), the raw video data cannot be shared[cite: 84]. 
* **Provided:** Pre-trained model weights and a sample "dummy" skeletal dataset to demonstrate the pipeline.
* **Input Format:** The model expects `.npy` or `.csv` files containing 3D coordinates of 24 joints (MediaPipe format).

## 📚 Citation
[Insert Citation Here once published]
