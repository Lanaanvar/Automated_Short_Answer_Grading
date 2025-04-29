# 🧠 Automated Short Answer Grading (ASAG) using Semantic Similarity

## 📌 Project Overview

This project presents two distinct approaches for automating the grading of short textual answers based on their semantic similarity to reference answers. The objective is to build systems that can perform consistent, scalable, and fair assessment of student responses with minimal human intervention.

---

## 🎯 Core Problem Statement

**Automating the grading of short textual answers by evaluating semantic similarity to reduce manual effort, minimize bias, and enable scalable assessment.**

---

## 🗃 Dataset

- Dataset: ASAG (Automated Short Answer Grading)
- Target column: `grades_round`
- Text columns used: `ref_answer`, `student_answer`
- Unused columns: Embeddings, preprocessed versions, alignment scores — to allow custom feature extraction and greater control.

---

## 🔀 Approaches

---

### ✅ **Approach 1: Feature-Based Machine Learning (By Lana)**

#### Overview

This approach involves manual feature engineering to capture surface-level and shallow semantic similarity, followed by training classical and ensemble regression models.

#### 🔧 Pipeline

1. **Text Preprocessing**:
   - Lowercasing
   - Stopword removal
   - Lemmatization
   - Punctuation and digit removal

2. **Feature Extraction**:
   - TF-IDF Cosine Similarity
   - BLEU Score
   - ROUGE-L F1 Score
   - Jaccard Similarity
   - Token Overlap Ratio
   - Word Count Ratio
   - Character Length Difference

3. **Modeling**:
   - Linear, Ridge, Lasso, ElasticNet
   - Support Vector Regression (SVR)
   - Random Forest Regressor
   - Gradient Boosting Regressor
   - **XGBoost**
   - **Voting Regressor (Ensemble)**

4. **Evaluation Metrics**:
   - Mean Squared Error (MSE)
   - Mean Absolute Error (MAE)
   - R² Score

#### 📈 Sample Results

| Model              | MSE   | MAE   | R²    |
|-------------------|-------|-------|-------|
| SVR               | 0.266 | 0.393 | 0.412 |
| Random Forest     | 0.281 | 0.404 | 0.398 |
| Gradient Boosting | 0.274 | 0.396 | 0.405 |

#### 💡 Strengths
- Lightweight and easy to deploy
- Highly interpretable
- Works well on small to medium datasets
- Avoids black-box behavior

---

### ⚡ **Approach 2: Deep Learning with Transformer-Based Embeddings (By Neha)**

#### Overview

This approach leverages pre-trained transformer models (e.g., BERT or Sentence-BERT) to generate contextual embeddings for both student and reference answers. The embeddings are then passed into a deep neural regressor for grade prediction.

#### 🔧 Pipeline

1. **Text Preprocessing**:
   - Tokenization as per transformer model requirements

2. **Feature Generation**:
   - Sentence embeddings using BERT/Sentence-BERT
   - Cosine similarity between embeddings

3. **Modeling**:
   - Fully Connected Feedforward Neural Network (or)
   - Regression layer on top of Sentence-BERT
   - Trained using Mean Squared Error Loss

4. **Evaluation Metrics**:
   - Mean Squared Error (MSE)
   - Mean Absolute Error (MAE)
   - R² Score

#### 📈 Sample Results (to be updated)

| Model       | MSE   | MAE   | R²    |
|-------------|-------|-------|-------|
| BERT-Based  | 0.189   | 0.300   | 0.581   |

#### 💡 Strengths
- Deeper semantic understanding
- Handles paraphrasing better than manual features
- Can scale well with larger datasets

---
