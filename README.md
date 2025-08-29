# female-body-type-prediction
# 👩‍🔬 Female Body Type Classification Model

## Project Overview

This project aims to develop a data-driven model to classify female body types based on a set of anthropometric (body) measurements. Understanding body types is valuable across various domains, including personalized fashion recommendations, tailored fitness and nutrition planning, and health-related research into body composition and disease risk.

The core of this project involves two main stages:
1.  **Rule-Based Classification:** Applying predefined logical conditions derived from anthropometric research to categorize individuals into standard body types.
2.  **Machine Learning Prediction:** Building and evaluating a classification model that can predict a person's body type from their measurements, extending beyond strict rule adherence.

---

## 🎯 Project Goal

The primary goal is to create a robust classification system that assigns a `Body_type` label (e.g., Hourglass, Rectangle, Triangle) to an individual based on their bust, waist, and hip measurements, along with derived ratios.

---

## 📊 Dataset

The dataset utilized for this project contains key anthropometric measurements of female individuals.

**Key Features (Inputs for Model):**
* `bust`: Bust circumference (in inches)
* `waist`: Waist circumference (in inches)
* `hips`: Hip circumference (in inches)
* `high_hip`: High hip circumference (in inches - if available in the dataset)

**Engineered Features:**
To better capture body proportions, the following ratios are calculated:
* `WHR` (Waist-to-Hip Ratio): `waist / hips`
* `BHR` (Bust-to-Hip Ratio): `bust / hips`
* `HHR_WHR` (High Hip-to-Waist Ratio): `high_hip / waist` (only if `high_hip` data is present)

**Target Variable (Output of Model):**
* `Body_type`: Categorical labels assigned based on predefined rules, including: 'Hourglass', 'Bottom hourglass', 'Top hourglass', 'Spoon', 'Triangle', 'Inverted triangle', 'Rectangle', and 'Undetermined'.

---

## 🛠️ Methodology

The project follows a structured data science methodology:

### 1. Data Preparation & Feature Engineering
* **Unit Consistency:** Ensures all raw measurements are uniformly in **inches**. If data is in centimeters, it is converted.
* **Ratio Calculation:** Computes `WHR`, `BHR`, and `HHR_WHR` to represent key body proportions. A small `epsilon` is used to prevent division by zero errors.
* **Missing Data Handling:** Specifically addresses the absence of the `high_hip` column. If missing, `HHR_WHR` is filled with `NaN`, affecting the classification of body types reliant on this measurement. Further general `NaN` imputation will be performed before ML training.

### 2. Rule-Based Body Type Classification
* A custom Python script (`np.select`) applies a series of detailed logical conditions, based on anthropometric differences and ratios, to assign an initial `Body_type` to each individual.
* **Order of Rules:** The sequence of conditions is critical, as a person is assigned the *first* body type whose criteria they meet.
* **'Undetermined' Category:** Individuals who do not fit any defined rules are initially labeled 'Undetermined' for later analysis or refined classification.

### 3. Machine Learning Model Development (Classification)
* **Problem Type:** This is a **multi-class classification** problem where the model learns to map input measurements/ratios to one of the `Body_type` categories.
* **Data Splitting:** The dataset is divided into training and testing sets (e.g., 80% train, 20% test) using `stratified sampling` to maintain the proportion of each body type across the sets.
* **Feature Scaling:** Numerical features are scaled (e.g., `StandardScaler`) for algorithms sensitive to feature ranges.
* **Model Selection:** Various classification algorithms (e.g., Random Forest, Logistic Regression, Gradient Boosting Machines) will be explored and evaluated.
* **Training & Evaluation:** Models are trained on the training set and evaluated on the unseen test set using metrics like accuracy, precision, recall, F1-score, and confusion matrices to assess performance across all body types.

---

## 🚀 Getting Started

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
