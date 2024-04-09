# Pre-Processing

---

### 🕵🏻‍♂️ Import & Exploration

- [ ] Data-Types? (Continuous, Discrete, Categorical)
- [ ] Data-Structures? (Relationships, Time-Series, Distribution)
- [ ] Obvious Correlations?
- [ ] Missing Data?
- [ ] Statistical Summaries (Mean, Median, Standard Deviation)
- [ ] Visualizations (Histograms, Boxplots, Scatterplots)
- [ ] Checking for Outliers

---

### 👨🏽‍🍳 Feature Selection

- [ ] Independent variables (X), Dependent variables (Y)
- [ ] Feature Selection 🧮
  - [ ] Feature Importance Evaluation (e.g., with Random Forest)
- [ ] Dimensionality Reduction (PCA, t-SNE)
- [ ] Feature Engineering: Combining features to create new ones

---

### 🔍 Missing Values

1. [ ] Drop Columns 🗑
2. [ ] Imputation 💧 (Replace by mean/median/most frequent of the column)
3. [ ] Extended Imputation 💦 (Keep track of imputed values)

- [ ] KNN-Imputation, and other advanced methods
- [ ] Target Encoding for categorical variables with many categories
- [ ] Handling of rare categories

---

### 🎲 Categorical data

1. [ ] Drop Data ✂️
2. [ ] Ordinal Encoding 🥇 (Each value gets an Integer)
3. [ ] One Hot Encoding 🔥 (Transform categories into binary Vectors)

- [ ] Target Encoding for categorical variables with many categories
- [ ] Handling of rare categories

---

### ✂️ Splitting (Train, Test, Val)

- [ ] Cross-Validation as an alternative to simple splitting
  - [ ] 20% for testing data is a common rate
- [ ] Stratified Split, to maintain the distribution of the target variable

---

### 📐 Feature Scaling

Discussion on when scaling is necessary (dependent on the ML model)

##### Standardisation
- [ ] Standardisation --> (X - mean) / standard deviation --> Between -3 and +3
  - [ ] -> Good for all kinds of data (preferred)

##### Normalisation
- [ ] Normalisation --> (X - min) / (max - min) --> Between 0 and 1
  - [ ] -> Good for normal distribution
- [ ] RobustScaler as an option that is less susceptible to outliers

---

### 🏎️ Optimization

- [ ] Data-Leakage: "Using info that would not be available"
- [ ] Hyperparameters (Grid-Search, Random Search, Optuna)
- [ ] Dealing with imbalanced data (Oversampling, Undersampling, SMOTE)
- [ ] Data security and privacy considerations, especially with sensitive data
- [ ] Automation of pre-processing pipelines (e.g., with scikit-learn's Pipeline)

---
