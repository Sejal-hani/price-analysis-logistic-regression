
# Price Analysis Using Logistic Regression

## 1. Overview
The aim of this project is to create a full data analytics workflow that classifies clothing products into price categories.  
Instead of predicting price as a continuous numerical value, the task is reframed as a **binary classification problem**:

- **Standard-Priced**
- **High-Priced**

This framing enables more practical insights into pricing patterns and supports decision-making in retail contexts.

---

## 2. Data Source
The analysis uses the **Clothes Price Prediction** dataset, publicly available on Kaggle.

**Features include:**
- Product category  
- Brand  
- Season  
- User ratings  

These features provide a basis for investigating the drivers of clothing prices.

**Dataset Link:**  
Clothes Price Prediction on Kaggle

---

## 3. Methodology
A multi-stage analytics workflow was followed, progressing from data preparation to statistical validation and predictive modeling.

---

### a) Data Preparation & Feature Engineering
The dataset was cleaned and processed.  
The primary feature engineering step involved creating a **binary target variable**, `Price_Category`, by binning the `Price` column:

- **1 → High-Priced** (Price ≥ $108.00)  
- **0 → Standard-Priced** (Price ≤ $108.00)

This median-based binning ensured balanced class distribution, making the dataset suitable for classification modeling.

---

### b) Exploratory Data Analysis (EDA)
EDA was performed to identify visual patterns that might differentiate the two price categories.

Visualizations explored relationships between `Price_Category` and:
- Product category  
- Brand  
- Season  

These analyses helped form initial hypotheses regarding price drivers.

---

### c) Statistical Validation: One-Way ANOVA
To validate observations from EDA, a **One-Way ANOVA** test was conducted to examine whether mean prices differed significantly across product categories.

#### ANOVA Results

| Metric        | Value  |
|---------------|--------|
| F-statistic   | 1.3891 |
| p-value       | 0.2257 |

**Interpretation:**  
Since the p-value (0.2257) is greater than 0.05, the null hypothesis cannot be rejected.  
This indicates no statistically significant difference in mean prices across categories.

#### Confidence Interval Confirmation
The confidence intervals for all categories show substantial overlap. For example:
- **Dress:** $106.67 – $122.34  
- **Sweater:** $98.70 – $114.86  

This overlap further confirms the ANOVA conclusion that category-level price differences are not statistically meaningful.

---

### d) Predictive Modeling: Logistic Regression
A **:contentReference[oaicite:0]{index=0}** classifier was trained to predict `Price_Category`.

The model was selected as a **baseline** due to:
- Simplicity  
- Interpretability  
- Clear coefficient-based feature analysis  

---

### e) Model Evaluation
Model performance was evaluated using:
- Confusion Matrix  
- Accuracy Score  
- Precision and Recall  
- Classification Report  

#### Results
- **Precision:**  
  - Standard-Priced: 49%  
  - High-Priced: 47%
- **Recall:**  
  - Standard-Priced: 47%  
  - High-Priced: 49%
- **Accuracy:** ~0.48

The accuracy is no better than random guessing, indicating the model failed to learn meaningful predictive patterns.

---

## 4. Key Takeaways

### a) Product Category Does Not Strongly Influence Price
Both ANOVA results and EDA suggest that differences in mean prices across product categories are not statistically significant.

---

### b) Median-Based Binning Is Effective for Structuring the Problem
Transforming price into a binary target:
- Balances the dataset  
- Improves interpretability  
- Simplifies classification  

However, balance alone does not guarantee predictive power.

---

### c) Model Failure Confirms Feature Weakness
The Logistic Regression model’s ~48% accuracy directly reflects the weakness of the available features.

Statistical tests and correlation analysis confirm:
- Near-zero correlation between features and price  
- Lack of consistent, learnable patterns  

The model’s failure serves as validation of these findings.

---

### d) Demonstration of an End-to-End Analytics Workflow
Despite poor predictive performance, the project successfully demonstrates:
- Data preprocessing  
- Exploratory Data Analysis  
- Statistical validation (ANOVA, correlation analysis)  
- Model development  
- Performance evaluation  

---

## 5. Conclusion
This project applied Logistic Regression within a complete data analytics workflow to classify clothing products into price categories.

Although predictive performance was poor, the analysis produced **clear and valuable insights**:
- Product categories do not significantly influence price  
- Available features lack predictive signal  
- Model failure is statistically justified, not a modeling error  

Both ANOVA and correlation analysis show minimal feature relevance, explaining the model’s inability to perform better than random guessing.

### Future Work
Improvement should **not** focus on more complex models, as they would likely fail for the same reasons.  
Meaningful performance gains would require a **richer dataset**, incorporating:
- Style attributes  
- Material and quality metrics  
- Detailed seasonality effects  

These factors are more representative of real-world pricing decisions in the fashion industry.
ibutes, quality metrics, and seasonality-which are the true drivers of complex pricing decisions in the fashion industry.
