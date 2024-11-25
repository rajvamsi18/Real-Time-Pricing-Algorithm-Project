# **Regional Demand Prediction**

## **1. Introduction**
This phase lays the groundwork for a real-time pricing algorithm by predicting regional demand for products. The goal is to clean and prepare the dataset, build accurate predictive models, evaluate their performance, and derive insights into the factors influencing demand. These steps ensure that the subsequent phases of the project, including dynamic pricing, are built on a robust and validated foundation.

---

## **2. Objective of Phase 1**
The key objectives of Phase 1 are as follows:

1. **Prediction Accuracy**: Develop a reliable model to predict regional demand based on seller, product, and logistical attributes.
2. **Feature Insights**: Identify and interpret features that significantly influence demand fluctuations.
3. **Performance Benchmarking**: Compare and evaluate machine learning models to select the best one for demand prediction.
4. **Preparation for Phase 2**: Establish a foundation for the real-time pricing algorithm by ensuring the model generalizes well to unseen data.

---

## **3. Dataset Overview**
The dataset includes transactional, geographical, and product-specific data relevant to predicting demand across regions.

### **Key Features**
| **Feature Name**                | **Description**                             | **Example Values**                |
|---------------------------------|---------------------------------------------|------------------------------------|
| `seller_state`                  | State where the seller is located           | SP, RJ, MG                        |
| `seller_city`                   | Seller's city                               | São Paulo, Rio de Janeiro         |
| `freight_value`                 | Shipping costs                              | 12.50, 18.75                      |
| `product_category_name_english` | Product category                            | Health & Beauty, Telephony        |
| `regional_demand` (Target)      | Total demand in the region (target variable)| 4500, 7200                        |

---

## **4. Data Preprocessing**

### **4.1 Missing Values**
- **Numerical features** (e.g., `freight_value`) were imputed using the **mean**.
- **Categorical features** (e.g., `seller_city`) were imputed using the **mode**.

### **4.2 Outlier Analysis**
Outliers in `regional_demand` were visualized using boxplots and quantified statistically. The skewness value of **-0.94** confirmed no further transformation was necessary.

### **4.3 Feature Encoding**
- Categorical variables (e.g., `seller_state`) were converted to numerical format using **one-hot encoding**.

### **4.4 Feature Selection**
- **Mutual Information Scores** prioritized features like `seller_state`, `freight_value`, and `product_category_name_english`.

---

## **5. Model Selection**

### **5.1 Evaluated Models**
| **Model**         | **Strength**                                          | **Weakness**                        |
|-------------------|------------------------------------------------------|-------------------------------------|
| **Linear Regression** | Simple and interpretable                            | Poor handling of non-linear relationships |
| **Random Forest**     | Robust against outliers and non-linearity          | Can overfit without careful tuning |
| **LightGBM**          | Fast and efficient                                 | Requires parameter tuning for large datasets |
| **XGBoost**           | High accuracy potential                            | Computationally expensive and prone to overfitting |
| **CatBoost**          | Handles categorical data natively                  | Performed poorly on this dataset   |

### **5.2 Evaluation Metrics**
| **Metric**                      | **Description**                                                         |
|---------------------------------|-------------------------------------------------------------------------|
| **Mean Absolute Error (MAE)**   | Indicates how far, on average, predictions deviate from actual demand. Lower MAE ensures reliable pricing. |
| **Mean Squared Error (MSE)**    | Penalizes large prediction errors more heavily, reducing extreme mispredictions critical for pricing accuracy. |
| **R-Squared (R²)**              | Reflects how well the model captures demand patterns, crucial for aligning pricing with market dynamics. |

---

## **6. Model Evaluation**

### **6.1 Cross-Validation Results**
| **Model**         | **MAE (Mean)** | **Std Dev** | **Comments**                        |
|-------------------|----------------|-------------|-------------------------------------|
| Linear Regression | 0.0406         | ±0.0047     | Struggled with non-linear data.     |
| Random Forest     | 0.0194         | ±0.0044     | Best overall performance.           |
| LightGBM          | 0.7570         | ±0.0028     | Slower convergence.                 |
| XGBoost           | 1.4093         | ±0.0783     | Overfitting without tuning.         |
| CatBoost          | 8.5175         | ±1.0835     | Poor performance.                   |

---

### **6.2 Final Model Selection**
**Random Forest** was chosen based on superior performance:

| **Metric**  | **Validation Set** | **Test Set** |
|-------------|---------------------|--------------|
| **MAE**     | 0.1436              | 0.1436       |
| **MSE**     | 7.5681              | 7.5681       |
| **R²**      | 0.9999              | 0.9999       |

---

## **7. Explainability and Insights**

### **7.1 SHAP Analysis**
**SHAP** (SHapley Additive exPlanations) provided insights into feature importance:
- seller_state_sp (São Paulo) was the most influential feature, highlighting its economic significance.
- Freight value and product categories also significantly impacted demand predictions.

### **7.2 Feature Importance**
**Random Forest Feature Importance** confirmed:
1. Seller states (`seller_state_sp`, `seller_state_mg`).
2. Product categories (`health_beauty`).
3. Freight costs (`freight_value`).

### **7.3 Learning Curve Analysis**
Training and cross-validation errors were plotted against the training set size:
- Errors converged as the dataset size increased, confirming that the model was neither overfitting nor underfitting.

---

## **8. Residual Analysis**

Residuals were analyzed:
- Predictions were unbiased, with residuals centered around zero.
- A few outliers were identified, likely represented rare demand scenarios, highlighting areas for future analysis.

---

## **10. Conclusion**

Phase 1 successfully established:
1. **Model Selection**: Random Forest was finalized for its robustness and accuracy.
2. **Feature Insights**: Key demand drivers identified, aligning with the pricing objectives.
3. **Scalability**: Model generalizes well across unseen data.

---

