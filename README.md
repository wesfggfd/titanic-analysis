# 🚢 Titanic Survival Prediction Model

[![Kaggle Competition](https://img.shields.io/badge/Kaggle-Compete-blue?logo=kaggle)](https://www.kaggle.com/competitions/titanic)
[![Best Score](https://img.shields.io/badge/Score-0.78947-brightgreen)](https://www.kaggle.com/yourusername)
[![Python Version](https://img.shields.io/badge/Python-3.1%2B-blue?logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

![Titanic Survival Prediction Flowchart](https://via.placeholder.com/800x400.png/009688/ffffff?text=Data+Processing+Pipeline)
*(Example flowchart placeholder - create actual diagram with https://draw.io/)*

## 📊 Key Results
```text
Leaderboard Progression:
Version 1: 0.77511 (Baseline)
Version 2: 0.78468 (+1.25% improvement) 
Version 3: 0.78947 (+1.84% total improvement)
```

# Improvement

```bash
1. Version 1

Selected four key features.

Applied simple label encoding.

Used a default-parameter Random Forest classifier.

Score: 0.77511

2. Version 2

Added basic categorical feature processing (mapped categories to median values).

Score: 0.78468

3. Version 3

Performed extensive data exploration.

Engineered new features (binning, missing-value handling, custom title categories, etc.).

Tuned hyperparameters via grid search.

Score: 0.78947
```

## Titanic Survival Prediction-Code Evolution Analysis

- **Kaggle Leaderboard Scores: https://www.kaggle.com/competitions/titanic/leaderboard?search=Sean**
-  **Current Best Score: 0.78947 (Top 10.1% at submission time)**

## Version 1:Baseline Model (Score: 0.77511)
```python
# Core Features
features = ["Pclass", "Sex", "SibSp", "Parch"]
model = RandomForestClassifier(n_estimators=100, max_depth=5, random_state=1)

# Key Characteristics
- Basic one-hot encoding
- No missing value handling
- Minimal feature engineering
- Default hyperparameters
```

## Version 2:Improved Data Handling (0.78468)
```python
# Key Additions
# Handle missing values
train_data['Age'].fillna(train_data['Age'].median(), inplace=True)
train_data['Fare'].fillna(train_data['Fare'].median(), inplace=True)

# Expanded Features
features_continuous = ["Age","Fare"]
X = pd.concat([X_categories, train_data[features_continuous]], axis=1)

# Improvements
- Added age/fare median imputation
- Incorporated continuous features
- Better data cleaning
```

## Version 3: Advanced Feature Engineering (Score: 0.78947)
```python
# Major Enhancements
1. Advanced feature creation:
   - Title extraction: all_data["Title"] = all_data["Name"].apply(...)
   - Deck information: all_data["Deck"] = all_data["Cabin"].str[0]
   - Family features: ["FamilySize", "IsAlone"]
   - Binned age: all_data["AgeBin"]

2. Sophisticated missing value handling:
   - Group-aware imputation for Age/Fare
   - Embarked imputation using group modes

3. Enhanced encoding:
   - Custom title categorization
   - One-hot encoding expansion

4. Model optimization:
   model = RandomForestClassifier(
       n_estimators=1500,
       max_depth=6,
       min_samples_split=5,
       oob_score=True,
       random_state=42
   )

5. Feature selection:
   - Correlation analysis
   - Chi-squared feature importance
   - Final 20+ engineered features
```


## README.md Template

# Titanic Survival Prediction

[![Kaggle Competition](https://img.shields.io/badge/Kaggle-Titanic_Competition-blue)](https://www.kaggle.com/competitions/titanic)
[![Best Score](https://img.shields.io/badge/Best_Score-0.78947-brightgreen)](https://www.kaggle.com/competitions/titanic/leaderboard)

## Solution Overview
Three progressive implementations with feature engineering improvements:

### 1. Baseline Model
```python
# Core implementation
features = ["Pclass", "Sex", "SibSp", "Parch"]
model = RandomForestClassifier(n_estimators=100, max_depth=5)
```

### 2.Enhanced Data Processing
```python
# Missing value handling
train_data['Age'].fillna(train_data['Age'].median(), inplace=True)
test_data['Fare'].fillna(test_data['Fare'].median(), inplace=True)
```

### 3.Advanced Pipeline
```python
# Feature engineering highlights
# Title extraction
all_data["Title"] = all_data["Name"].apply(lambda x:x.split(',')[1].split()[0])

# Family features
all_data["FamilySize"] = all_data["SibSp"] + all_data["Parch"] + 1
all_data["IsAlone"] = (all_data["FamilySize"] == 1).astype(int)

# Optimized model
model = RandomForestClassifier(
    n_estimators=1500,
    max_depth=6,
    min_samples_split=5,
    random_state=42
)
```

### How to Reproduce

- **1.Downlaod dataset above**
- **2.Run notebook sequentially:**
  ```bash
  jupyter notebook titanic_survival_prediction.ipynb
  ```
- **3.Submit ```submission.csv``` to Kaggle**


### Feature Importance
- **feature_importance_link:[feature_output]:(https://www.kaggle.com/datasets/seanchenxinyu/titanic-output)**
  # Critical Improvement Factors
1. **Feature Engineering**
   - Title extraction from names (Mr/Mrs/Miss)
   - Cabin deck information
   - Family size features
   - Age binning

2. **Data Imputation**
   - Group-based median imputation for Age
   - Fare imputation by Pclass
   - Smart Embarked value filling

3. **Model Optimization**
   - Increased n_estimators to 1500
   - Tuned max_depth and min_samples_split
   - OOB score validation
   - Feature importance analysis

4. **Encoding Expansion**
   - Custom one-hot encoding
   - Title categorization
   - Deck information utilization

This progression demonstrates how systematic feature engineering and careful data handling can improve model performance in Kaggle competitions.
