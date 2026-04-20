# 📊 Learning Probability Density Function using GAN

## 📌 Project Overview

This project implements a **Generative Adversarial Network (GAN)** to learn the **probability density function (PDF)** of a transformed random variable using only data samples.

Unlike traditional methods, **no parametric distribution (Gaussian, etc.) is assumed**. The model learns the distribution directly from data.

---

## 📂 Dataset

* **Source:** India Air Quality Dataset
* **Link:** https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data
* **Feature Used:** NO₂ concentration (`no2`)

---

## 🔄 Data Transformation

Each input value ( x ) is transformed into ( z ) using:

[
z = x + a_r \cdot \sin(b_r \cdot x)
]

### 🔢 Parameters

Roll Number: **102303048**

* ( a_r = 0.5 \times (r \bmod 7) = 0.5 \times 1 = 0.5 )
* ( b_r = 0.3 \times ((r \bmod 5) + 1) = 0.3 \times 4 = 1.2 )

---
---

## 🧠 GAN Architecture

### 🔹 Generator

* Input: Noise sampled from ( N(0,1) )
* Architecture:

  * Linear → ReLU → Linear → ReLU → Linear
* Output: Generated samples ( z_f )

### 🔹 Discriminator

* Input: Real or fake samples
* Architecture:

  * Linear → ReLU → Linear → ReLU → Linear → Sigmoid
* Output: Probability of being real

---

## 🔁 Training Process

* Loss Function: Binary Cross Entropy (BCE)
* Optimizer: Adam
* Steps:

  1. Train discriminator to distinguish real vs fake samples
  2. Train generator to fool discriminator

---

## 📈 PDF Estimation

After training:

* Generate samples from the generator
* Apply **Kernel Density Estimation (KDE)** to approximate the PDF

---

## 📊 Results

The output compares:

* Real distribution (histogram)
* GAN-learned distribution (KDE curve)

![PDF Plot](outputs/pdf_plot.png)

---

## 🔍 Observations

### ✔ Mode Coverage

* The GAN captures the **main peak** of the distribution effectively

### ✔ Training Stability

* Training is reasonably stable with minor oscillations

### ✔ Quality of Generated Distribution

* Generated samples closely match the real distribution
* Slight smoothing observed due to KDE approximation

---

## 🚀 How to Run

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Run the Project

```bash
python main.py
```

---

## 📌 Key Highlights

* No prior assumption of distribution
* Fully data-driven PDF learning
* Modular and reproducible implementation
* Clean GAN-based approach

---

## 📜 License

This project is developed for academic purposes only.

---

