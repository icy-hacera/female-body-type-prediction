# Predicting Female Body Types with Machine Learning

## Project Overview
This project explores the intersection of **fashion, data, and machine learning** by building a model to predict **female body types** (Apple, Pear, Hourglass, Rectangle, Inverted Triangle) from anthropometric measurements.  

The idea came from a real-life curiosity: many people don’t know their body type, yet it plays a huge role in how we style ourselves. Using data science, I set out to create a model that can **classify body types from just a few key measurements**.


## Dataset
- Source: Custom-merged dataset of bust, waist, hip, and shoulder measurements.  
- Preprocessing:
  - Removed duplicates & checked missing values.
  - Engineered new features:  
    - **whr (Waist-to-Hip Ratio)**  
    - **bhr (Bust-to-Hip Ratio)**  
  - Balanced the dataset using **SMOTE** to overcome class imbalance.


## Methodology
1. **EDA**  
   - Explored distributions of measurements.  
   - Visualized body type counts → noticed severe class imbalance.  

2. **Feature Engineering**  
   - Added **WHR & BHR** (anthropometric standards used in fashion/fitness).  
   - Normalized features with `StandardScaler`.

3. **Modeling**  
   - Used **K-Nearest Neighbors (KNN)** as baseline classifier.  
   - Tuned `n_neighbors` for best performance.  
   - Handled class imbalance with **SMOTE oversampling**.

4. **Evaluation**  
   - Metrics: Confusion Matrix, Precision, Recall, F1-Score.  
   - Focused on **per-class performance**, not just overall accuracy.


##  Results
- Without SMOTE: Model ignored minority classes (e.g., “Apple”).  
- With SMOTE + WHR/BHR:  
  - Overall Accuracy: **90%**  
  - Better balance across classes (no “ghost classes”).  
  - Per-class recall improved significantly.  


## Getting Started

To run this project, follow these steps:

### Prerequisites

* Python 3.x
* `pandas`
* `numpy`
* `scikit-learn` (for ML models and tools)
* Jupyter Notebook or Google Colab (recommended for interactive development)

You can install the necessary libraries using pip:
```bash
pip install pandas numpy scikit-learn jupyter
