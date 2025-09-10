# ROC-AUC-in-the-context-of-TCR-antigen-binding.
Beginner-friendly tutorial to learn ROC–AUC using dummy TCR antigen binding data (binary + multi-class).


# 🧬 ROC–AUC Tutorial with Dummy TCR Data

This repository is a **step-by-step tutorial** to understand and apply **ROC–AUC (Receiver Operating Characteristic – Area Under Curve)** in the context of **T-cell receptor (TCR) antigen binding**.  
It is written in **simple language** so even beginners can follow easily.

---

## 📘 What is ROC–AUC?

The **ROC curve** shows how well a model separates:
- **Positives** (e.g., TCR binds antigen, or a patient has disease)  
- **Negatives** (e.g., TCR does not bind, or a patient is healthy)  

- **Y-axis (TPR / Recall / Sensitivity):** How many positives the model finds correctly.  
- **X-axis (FPR):** How many negatives are incorrectly marked as positive.
- <img width="545" height="400" alt="image" src="https://github.com/user-attachments/assets/da19c81d-f6be-4bbd-9c3b-69bf41d05125" />


The **AUC** is a number between 0 and 1 that measures the area under the ROC curve:
- **1.0 → Perfect model**
- **0.9 → Excellent**
- **0.7–0.8 → Decent**
- **0.5 → Random guessing**
- **< 0.5 → Broken model**

👉 AUC tells us how good a model is overall at separating positives from negatives.

---

## 📂 What We Did

We used **dummy datasets** (simulated data) to learn ROC–AUC:

### 1️⃣ Binary Classification (TCR binds or not)
- Input: 500 samples, each TCR described by 10 features.  
- Label: `1 = binds antigen`, `0 = does not bind`.  
- Models: Logistic Regression, Random Forest.  

### 2️⃣ Multi-class Classification (Which antigen: Flu, Cancer, Other?)
- Input: 600 samples, 3 possible antigen classes.  
- Labels: `0 = Flu`, `1 = Cancer`, `2 = Other`.  
- Model: One-vs-Rest Logistic Regression.  

---

## 📊 Results

### Binary Case
- **Logistic Regression AUC = 0.88**  
- **Random Forest AUC = 0.97**  
👉 Random Forest clearly performed better.
<img width="613" height="547" alt="image" src="https://github.com/user-attachments/assets/1dc6f824-b077-41f3-a8a4-78969d86dd6e" />

  

### Multi-class Case
- **Class 0 (Flu) AUC = 0.82**  
- **Class 1 (Cancer) AUC = 0.80**  
- **Class 2 (Other) AUC = 0.83**  
👉 All classes show good separation (>0.8 AUC).
<img width="702" height="547" alt="image" src="https://github.com/user-attachments/assets/4a3a59d1-6916-444b-9cf0-c0bed5e4d4f9" />
  

---

## 🔧 Requirements

To run the code, you need:

- Python 3.x  
- numpy  
- pandas  
- matplotlib  
- scikit-learn  

Install them with:
```bash
pip install numpy pandas matplotlib scikit-learn
