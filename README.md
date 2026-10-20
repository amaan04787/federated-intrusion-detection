# Robust Federated Learning for Intrusion Detection under Label-Flipping Attacks

A lightweight 5-client federated intrusion detection framework evaluating robust aggregation rules (Coordinate-wise Median and Krum) against targeted label-flipping poisoning attacks on the CICIDS2017 benchmark dataset.

---

## 📌 Overview

Federated Learning (FL) enables collaborative threat detection without exposing raw network traffic. However, dishonest clients can poison the global model. This study analyzes the vulnerability of standard Federated Averaging (`FedAvg`) to local label-flipping attacks (20% adversarial client ratio) and measures performance recovery using Byzantine-robust aggregation methods.

### Key Highlights
- **Dataset:** CICIDS2017 (2,520,798 cleaned flow records, 70 input features, binary classification: Benign vs. Attack).
- **Architecture:** Compact Multi-Layer Perceptron (70–64–32–1 with ReLU activations and Dropout).
- **Federated Setup:** 5 clients, 10 communication rounds, 2 local epochs per round (evaluated under IID and Dirichlet α = 0.5 non-IID partitions).
- **Adversarial Scenario:** 1 of 5 clients (20%) executes a complete label-flipping attack y' = 1 − y.
- **Defense Mechanisms:** Comparative evaluation of standard **FedAvg**, **Coordinate-wise Median**, and **Krum** aggregation.

---

## 📊 Experimental Results (Held-Out Test Set: 504,160 Samples)

| Method | Accuracy (%) | Precision (%) | Recall (%) | F1-Score (%) | ROC-AUC (%) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **FedAvg (Clean IID)** | 98.67 | 98.42 | 93.60 | 95.95 | 99.93 |
| **FedAvg (Clean Non-IID)** | 98.48 | 96.65 | 94.28 | 95.45 | 99.88 |
| **FedAvg (Poisoned)** | 98.10 | 98.31 | 90.31 | 94.14 | 99.86 |
| **Median (Poisoned)** | 98.60 | 98.52 | **93.13** | **95.75** | 99.90 |
| **Krum (Poisoned)** | 98.55 | **98.86** | 92.49 | 95.57 | **99.93** |

### Key Takeaway
While overall accuracy dropped by only 0.57% under label flipping, attack recall plummeted by **3.29%** (resulting in 2,806 additional missed intrusions). **Coordinate-wise Median** recovered ~86% of the lost recall (+2.82%), whereas **Krum** achieved the highest precision (98.86%) and lowest false-alarm rate.

---

## 🛠️ Tech Stack & Requirements

- **Environment:** Python 3, Kaggle Notebooks (NVIDIA Tesla T4 GPU)
- **Deep Learning:** TensorFlow / Keras
- **Data & Evaluation:** Scikit-Learn, NumPy, Pandas, Matplotlib, Seaborn

---
