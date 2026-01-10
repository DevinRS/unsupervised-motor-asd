# Unsupervised Deep Learning for Quantifying Atypical Motor Signatures in ASD

This repository contains the official PyTorch implementation of the paper: **"Unsupervised Deep Learning Framework for Quantifying Atypical Motor Signatures in ASD"**.

## 📄 Abstract
Motor impairments are pervasive in Autism Spectrum Disorder (ASD) but are often assessed using subjective or supervised methods. This project introduces a **Spatio-Temporal Graph Convolutional Network Autoencoder (STGCN-AE)** trained exclusively on neurotypical (NT) movement data to establish a normative model. By using reconstruction error as an anomaly score, we objectively quantify atypical motor patterns.

Key findings:
- Autistic individuals show higher reconstruction errors compared to NT controls.
- Atypicality correlates with **postural sway** and **jerk**.
- SHAP analysis reveals that atypicality is driven by complex feature combinations rather than single features.

## 🏗️ Architecture
The model uses a STGCN-AE architecture to process 3D skeletal data extracted from video via MediaPipe.

![Model Architecture](figures/Figure%202.png) 

## 🛠️ Usage

The project pipeline is divided into four sequential notebooks located in the `notebooks/` directory. You can run these directly in Google Colab.

Quick Start: For a full demo run, execute the notebooks in order (1 $\rightarrow$ 4). Notebook 1 will generate the necessary dummy data environment for the subsequent steps.

### 1. `1_DataProcessing.ipynb`
**From Raw Coordinates to Graph Tensors**
* **Function:** Converts raw MediaPipe CSV outputs into the specific Spatio-Temporal Graph tensors required by the model.
* **Key Operations:** Graph construction ($N=24$ fully connected nodes), sliding window segmentation (60 frames), and temporal trimming.
* **Demo Feature:** Includes a script to generate a **synthetic dummy dataset**, allowing you to test the pipeline without access to the private clinical data.

### 2. `2_ModelTraining.ipynb`
**Training the Normative Model**
* **Function:** Defines and trains the Spatio-Temporal Graph Convolutional Autoencoder (STGCN-AE).
* **Method:** Trains exclusively on Neurotypical (Control) data to learn a latent representation of "typical" movement.
* **Architecture:** Uses a custom symmetric ST-Conv encoder-decoder with temporal upsampling.

### 3. `3_ModelEvaluation.ipynb`
**Anomaly Detection & Statistical Testing**
* **Function:** Applies the trained model to the ASD cohort to quantify motor atypicality.
* **Key Operations:**
    * Calculates **Reconstruction Error (MSE)** as an anomaly score.
    * Establishes a "normative threshold" using the IQR method on control validation data.
    * Performs statistical testing (t-test) to validate group differences.
* **Replicability:** Validates findings against `anonymized_results.pkl` (pre-computed study results).

### 4. `4_ResultAnalysis.ipynb`
**Clinical Interpretability**
* **Function:** Bridges the gap between deep learning scores and clinical features.
* **Key Operations:**
    * **Correlation Analysis:** Maps reconstruction error to interpretable kinematic features (e.g., Jerk, Postural Sway).
    * **Explanatory Modeling:** Trains supervised classifiers (XGBoost, SVM) on features to predict diagnosis.
    * **SHAP Analysis:** Visualizes which motor features contribute most to the model's predictions.

## ⚠️ Data Privacy
Due to the sensitive nature of the dataset (video recordings of minors and adults with ASD), the raw video data cannot be shared. 
* **Provided:** Pre-trained model weights and an anonymized data for explanatory modeling to demonstrate the pipeline.
* **Input Format:** The model expects `.npy` or `.csv` files containing 3D coordinates of 24 joints (More detail in notebook).

## 📚 Citation
To be inserted
