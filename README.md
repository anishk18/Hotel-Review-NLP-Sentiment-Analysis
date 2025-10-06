# 🏨 Hotel Review Sentiment Analysis  
*Predicting Customer Satisfaction from Hotel Reviews*


🗂️Project Structure
---
hotel-review-sentiment-analysis/
├── notebooks/
│   ├── [Hotel_Review_NLP](notebooks/Hotel_Review_NLP.ipynb)
├── .gitignore
├── requirements.txt
├── README.md
└── LICENSE




---

## 🧭 Project Overview

This project aims to help **Hotel Management Inc.** understand what aspects of a hotel stay drive **customer satisfaction and higher ratings**.  

Using a dataset of customer reviews (both positive and negative) and hotel stay details, we:
- Explore the data through **EDA and visualization**
- Process and vectorize text data using **NLP techniques**
- Train and compare **Logistic Regression** and **Decision Tree (with PCA)** models
- Identify the **top positive and negative keywords** linked to satisfaction
- Provide **business insights** based on model outcomes

---

## 🧩 Dataset

The dataset includes:
- **Positive_Review**: Text field of positive customer comments  
- **Negative_Review**: Text field of negative customer comments  
- **Reviewer_Score**: Encoded as `1` for positive sentiment and `0` for negative  
- **Additional features**: Hotel location, nights stayed, trip type, etc.

*Note: Dataset not included in this repo. Please download it from the provided source or request access.*

---

## 🧮 Methodology

1. **Exploratory Data Analysis (EDA):**
   - Statistical summaries, distributions, and correlations  
   - Text analysis and visualizations (word clouds, review lengths, etc.)  

2. **Preprocessing:**
   - Text cleaning (lowercasing, punctuation removal, stopword filtering, lemmatization)
   - Vectorization using `CountVectorizer` with:
     - `max_features = 500`
     - `min_df = 10`
   - Separate vectorization for positive and negative reviews  
   - Merge with numeric features for model training  

3. **Modeling:**
   - **Logistic Regression**: baseline linear model  
   - **PCA + Decision Tree Classifier**: non-linear model with dimensionality reduction  
   - Hyperparameter tuning via **GridSearchCV (5-fold CV)**

4. **Evaluation:**
   - Accuracy, precision, recall, F1-score  
   - Confusion matrix and feature importance visualization  

---

## 🔍 Exploratory Data Analysis

Some key EDA steps and findings:
- **Missing values** handled through imputation or removal  
- **Review length** strongly correlates with sentiment — longer reviews tend to be negative  
- **Top positive terms:** “clean”, “friendly”, “comfortable”, “breakfast”, “location”  
- **Top negative terms:** “dirty”, “noisy”, “rude”, “small”, “expensive”  
- Seasonal trends indicate lower satisfaction during high occupancy months

---

## ⚙️ Preprocessing

- Applied `nltk` for tokenization, lemmatization, and stopword removal  
- Vectorized `Positive_Review` and `Negative_Review` separately using `CountVectorizer`
- Prefixed feature names as:
  - `pos_` → words from positive reviews  
  - `neg_` → words from negative reviews  
- Combined with structured (numeric) features to form the final feature matrix  

---

## 🤖 Modeling

### **1️⃣ Logistic Regression**
- Fitted on combined text + numeric data  
- Extracted **top 20 most predictive words** for both positive and negative sentiments  

📈 **Example Results:**
- Train Accuracy: 0.84  
- Test Accuracy: 0.81  

**Top Predictors:**
- Positive words: clean, friendly, comfortable, breakfast, location  
- Negative words: dirty, noisy, rude, small, expensive  

🧩 *Actionable Insight:* Cleanliness, staff attitude, and comfort are key satisfaction drivers, while noise and room size are major pain points.

---

### **2️⃣ PCA + Decision Tree Classifier**
- Built a pipeline combining **PCA (20 components)** + **Decision Tree**
- Tuned via 5-fold cross-validation for:
  - `max_depth`
  - `min_samples_leaf`
  - `min_samples_split`

📈 **Example Results:**
- Train Accuracy: 0.87  
- Test Accuracy: 0.79  

🧠  *Observation:* Logistic Regression generalizes better; Decision Tree tends to overfit slightly.

---

## 📈 Evaluation

| Model | Train Accuracy | Test Accuracy | Precision | Recall | F1-Score |
|--------|----------------|---------------|------------|--------|----------|
| Logistic Regression | 0.84 | 0.81 | 0.83 | 0.80 | 0.81 |
| Decision Tree (PCA) | 0.87 | 0.79 | 0.82 | 0.76 | 0.79 |

---

## 💡 Results & Insights

1. **Cleanliness and Staff Friendliness** have the strongest impact on satisfaction.  
2. **Noise, room size, and Wi-Fi issues** are the main drivers of dissatisfaction.  
3. **Logistic Regression** provides strong interpretability and generalization.  
4. Focus improvement on service quality and facility comfort to increase ratings.

---

 