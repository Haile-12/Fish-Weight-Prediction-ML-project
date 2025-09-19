# 🐟 Predicting Fish Weight Using Machine Learning

This project builds an **end-to-end ML pipeline** to accurately predict fish weight based on morphological features such as length, height, width, and species.  
It evaluates multiple **regression models** and identifies the best-performing one using comprehensive performance metrics.

---

## 📌 Table of Contents
- [Introduction](#-introduction)
- [Problem Statement](#-problem-statement)
- [Dataset Description](#-dataset-description)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [Preprocessing](#-preprocessing)
- [Model Training and Evaluation](#-model-training-and-evaluation)
- [Best Performing Model](#-best-performing-model)
- [Visualizations](#-visualizations)
- [Hyperparameter Tuning](#-hyperparameter-tuning)
- [Conclusion](#-conclusion)

---

## 🧾 Introduction
Accurately predicting the **weight of a fish** based on physical attributes is crucial in aquaculture, fisheries management, and food logistics.  
This project demonstrates an ML workflow to estimate fish weight and compares regression models for effectiveness.

---

## 🎯 Problem Statement
Given the physical measurements of a fish (**lengths, height, width, and species**), predict its **weight**.  
This is formulated as a **supervised regression problem**.

---

## 📂 Dataset Description
- Dataset: **Fish Market Dataset** (from Kaggle)  
- Features:
  - `Species` (categorical)
  - `Weight` (target)
  - `Length1`, `Length2`, `Length3`
  - `Height`
  - `Width`

📌 **Feature Engineering**  
A new feature was created:  
```python
Volume_Estimate = Length1 * Height * Width
```

## 🔍 Exploratory Data Analysis (EDA)
- Found strong correlations between **Weight** and both **Height** and **Volume_Estimate**.  
- Removed **outliers** (e.g., `Weight = 0` and mislabeled samples).  
- Scatterplots and heatmaps confirmed **linear trends** between features and target.  

---

## ⚙️ Preprocessing
Steps applied:  
- 🗑️ Dropped invalid/outlier entries  
- 📐 Engineered `Volume_Estimate`  
- 📊 Standard scaling for numerical features  
- 🔤 One-hot encoding for `Species`  
- ✂️ 80/20 **Train-Test split**  

---

## 🤖 Model Training and Evaluation
Trained models:  
- Linear Regression  
- Decision Tree Regressor  
- Random Forest Regressor  
- Gradient Boosting Regressor  

### 📊 Evaluation Metrics
- Train/Test **RMSE**  
- Test **MAE**  
- Test **R² Score**  
- Cross-validated **R² Mean & Std**  

| Model              | Train RMSE | Test RMSE | Test MAE | Test R²  | CV R² Mean | CV R² Std |
|--------------------|------------|-----------|----------|----------|------------|-----------|
| **Linear Regression** | 46.08      | 40.89     | 28.64    | **0.9850** | 0.9666     | 0.0119    |
| Gradient Boosting  | 6.66       | 48.65     | 34.19    | 0.9788   | 0.9668     | 0.0185    |
| Random Forest      | 19.59      | 52.37     | 32.98    | 0.9755   | 0.9658     | 0.0232    |
| Decision Tree      | 0.00       | 68.37     | 42.45    | 0.9582   | 0.9126     | 0.0434    |

---

## 🏆 Best Performing Model
✅ **Linear Regression**  
- Achieved the highest **R² = 0.9850** on the test set  
- Outperformed ensemble models despite simplicity  
- Generalized well → close **Train/Test RMSE** values  
- Strong **linear correlation** between features and target  

---

## 📊 Visualizations
Generated plots:  
- 📌 Actual vs. Predicted scatter plots  
- 📉 Residual plots  
- 📊 Error distribution histograms  
- 📈 Learning curves  
- 🪄 Feature importance bar plots  

🔎 **Linear Regression** had the most **stable residuals** and lowest variance.  

---

## 🔧 Hyperparameter Tuning
- Applied **GridSearchCV** for Random Forest and Gradient Boosting  
- Slight improvement in R² but **did not surpass Linear Regression**  

---

## ✅ Conclusion
- **Linear Regression** proved most effective due to strong **linear structure** in data  
- Feature engineering (`Volume_Estimate`) greatly enhanced accuracy  
- Complex models (RF, GBM) did not outperform simpler models  

---

## 🔮 Future Work
- 🐟 Collect more **diverse fish datasets**  
- 📈 Explore **non-linear models** if dataset grows in complexity  
- 🤖 Consider **neural networks or transformers** for large-scale datasets  
- 🌐 Apply in **real-time aquaculture systems** for operational use  
