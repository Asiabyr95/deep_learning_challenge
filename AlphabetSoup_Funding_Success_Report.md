# Predicting Funding Success with Machine Learning

## 📊 Overview of the Analysis

The objective of this analysis is to **predict the success of funding applications** submitted to Alphabet Soup, a nonprofit foundation. Using machine learning and deep learning techniques, we aim to build a binary classifier that determines whether an applicant is likely to use the allocated funding effectively (success) or not.

This solution helps the foundation **allocate resources more efficiently**, focusing support on applicants with a higher chance of success and maximizing the impact of their funding.

---

## 📋 Results

### 🔧 Data Preprocessing

- **🎯 Target Variable:**
  - `IS_SUCCESSFUL` — This binary variable indicates whether the organization used the funding effectively (`1`) or not (`0`).

- **🔑 Features Used:**
  - `APPLICATION_TYPE`
  - `AFFILIATION`
  - `CLASSIFICATION`
  - `USE_CASE`
  - `ORGANIZATION`
  - `STATUS`
  - `INCOME_AMT`
  - `SPECIAL_CONSIDERATIONS`
  - `ASK_AMT`
  - *(Optional in some optimizations: `NAME`)*

- **❌ Features Removed:**
  - `EIN` — Just an identification number, not useful for prediction.
  - *(In some versions: `NAME` — removed to reduce dimensionality and overfitting)*

---

### 🧠 Compiling, Training, and Evaluating the Model

#### Optimization 1
- Hidden Layers: 3
- Neurons: 15 → 25 → 35
- Activation (Hidden): ReLU
- Activation (Output): Sigmoid
- Epochs: 100
- Accuracy: **~72.69%**

#### Optimization 2
- Hidden Layers: 3
- Neurons: 15 → 25 → 35
- Activation (Hidden): ReLU
- Epochs: **200**
- Accuracy: **~73.00%**

#### Optimization 3
- Features: Same as above **+ `NAME`**
- Accuracy: **~78.8%**

---

- **🎯 Were You Able to Achieve Target Model Performance?**
  - ✅ Yes. When the `NAME` feature was included, model accuracy improved significantly, exceeding 78%.

---

### 🔁 Steps Taken to Increase Model Performance

- 🔢 Increased the number of hidden layers and neurons
- ⏳ Increased the number of training epochs (100 → 200)
- ➕ Included high-cardinality feature `NAME` for additional signal
- ✅ Scaled data using `StandardScaler`
- ➕ One-hot encoded all categorical features

---

## ✅ Summary

- The final neural network model achieved an **accuracy of ~78.8%** after multiple optimizations.
- Including the `NAME` feature contributed significantly to performance improvement, despite the risk of high dimensionality.

---

## 💡 Recommendation for Alternative Approach

To further improve accuracy and interpretability, we recommend trying **Gradient Boosting models**, especially:

- **🔹 XGBoost** or **LightGBM**
  - Handle categorical variables well
  - Automatically perform feature selection
  - Less sensitive to overfitting
  - Offer better interpretability through feature importance plots

These models could provide better generalization and transparency — ideal for supporting funding decisions in a real-world, stakeholder-driven environment.
