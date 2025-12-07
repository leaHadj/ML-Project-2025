# Clash Royale Match Outcome Prediction

## Project Description

This project focuses on predicting the outcome of a 1v1 Clash Royale match using machine learning. The goal is to determine whether Player 1 wins or loses a match based only on the deck composition of both players.

The project is divided into two main phases:
- Phase 1: Prediction using only the deck composition.
- Phase 2: Prediction with additional statistical features related to the cards.

This work was done as part of a machine learning course project.

---

## Dataset

Two datasets from Kaggle are used in this project:

### 1. Match Dataset
- Contains 2311 matches.
- Each match includes:
  - 8 cards of Player 1
  - 8 cards of Player 2
  - Number of crowns for each player
- A new target column is created:
  - `win_p1 = 1` if Player 1 wins
  - `win_p1 = 0` otherwise
- The dataset is strongly imbalanced:
  - About 72% of matches are won by Player 1.

### 2. Card Statistics Dataset
- Contains global information for each card:
  - Elixir cost
  - Rarity
  - Win rate
  - Usage rate

---

## Data Preprocessing

- One-Hot Encoding is applied to the 16 card slots.
- The final feature space contains around 1300 binary features.
- The dataset is split into:
  - 80% training
  - 20% testing
- The split is stratified to keep the class distribution.
- In Phase 2, missing statistical values are filled using the mean of each column.

---

## Phase 1: Baseline Models

Three baseline models are trained:

- Logistic Regression  
- Decision Tree  
- K-Nearest Neighbors (KNN)  

Evaluation is done using:
- Accuracy  
- Precision  
- Recall (class 0)  
- F1-score  
- ROC-AUC  
- Confusion matrices  

Results show that all baseline models are strongly affected by class imbalance. Logistic Regression is the most balanced model, while KNN mainly predicts the majority class.

---

## Phase 2: Advanced Models

To improve performance, three advanced models are trained:

- Random Forest  
- XGBoost  
- CatBoost  

Additional deck features are introduced:
- Average elixir cost
- Average win rate
- Average usage rate
- Average rarity

CatBoost gives the best overall performance, but the improvement remains limited due to:
- Strong dataset imbalance
- Lack of real in-game information (player skill, timing, placements, etc.)

---

## Evaluation Metrics

All models are evaluated using:
- Accuracy
- Precision
- Recall (for losing class)
- F1-score
- ROC-AUC
- Confusion matrices

These metrics allow a detailed analysis of model behavior, especially for the minority class.

---

## Main Results

- Baseline accuracy is already high due to class imbalance (around 72%).
- Advanced models slightly improve performance.
- CatBoost achieves the best results in terms of overall discrimination.
- Recall for Player 1 losses remains low for all models.

This shows that deck composition alone is not sufficient to accurately predict match outcomes.

---

## Scientific References

- Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system.  
- Dorogush, A. V., Ershov, V., & Gulinostrov, A. (2018). CatBoost: Gradient boosting with categorical features support.  
- He, H., & Garcia, E. A. (2009). Learning from imbalanced data.

---

## Authors

- Faraa Awoyemi  
- Lilia Benabdallah  
- Ilyes Ben Younes  
- Lea Hadj-Said  

---

## How to Run the Project

1. Install dependencies:
```bash
pip install -r requirements.txt
