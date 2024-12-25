# Real-Time Pricing Algorithm

This project demonstrates the development of a Real-Time Pricing Algorithm to dynamically adjust product prices based on market demand, regional trends, and competitor data. The primary goal is to optimize revenue by leveraging data-driven insights and predictive analytics.

---

## Project Structure

### A. **real-time-pricing.ipynb**

**Objective:**  
Perform initial data preprocessing, feature engineering, and exploratory analysis to prepare the dataset for predictive modeling.

**Key Steps:**  

1. **Integrated and cleaned e-commerce data:**  
    * Imported and merged datasets such as Orders, Products, Customers, and Seller data.  
    * Addressed missing values by imputing or removing incomplete data as appropriate.  
    * Ensured data consistency through type conversions (e.g., datetime formats) and column renaming for clarity.

2. **Engineered key features:**  
    * `regional_demand`: Aggregated order quantities by seller regions to compute demand patterns.  
    * **Demand and Supply Metrics:** Derived features to understand demand fluctuations across regions and time.

3. **Exploratory Data Analysis:**  
    * Visualized demand distribution across different regions and product categories.  
    * Examined regional and product-level trends to uncover variations in demand and supply.

**Insights:**  

1. **Demand trends across regions:**  
    * Identified top-performing regions with consistently higher order volumes.  
    * Highlighted regions with significant seasonal demand variability.

2. **Product category insights:**  
    * Determined product categories with consistently high demand across all regions.  
    * Noted variations in demand behavior for certain categories during specific time periods.

3. **Preliminary analysis for prediction:**  
    * Established baselines for regional demand prediction using existing trends.  
    * Identified potential gaps in data for further feature engineering.

---

### B. **regional_demand_prediction.ipynb**

**Objective:**  
Perform predictive modeling to estimate regional demand based on engineered features.

**Key Steps:**  

* Loaded and preprocessed the refined dataset to prepare features (`X`) and target (`regional_demand`).  
* Implemented feature selection to identify the most impactful predictors for regional demand.  
* Used various regression models including:
    * Linear Regression  
    * Random Forest Regressor  
    * XGBoost  
    * LightGBM  
    * CatBoost  
* Conducted hyperparameter tuning for optimal performance using GridSearchCV.  
* Evaluated model performance using metrics such as MAE, MSE, and R² on both validation and test sets.  
* Performed residual analysis and SHAP explainability to interpret model results and ensure transparency.

**Insights:**  

* **Random Forest** emerged as the most suitable model for regional demand prediction with the lowest MAE and competitive R² scores.  
* Identified key features driving regional demand through SHAP values and feature importance analysis.  
* Observed patterns of overfitting and mitigated them through augmented training data and regularization techniques.

This notebook sets the foundation for applying the predicted regional demand in the dynamic pricing algorithm for improved e-commerce performance.

---

### C. **dynamic_pricing_algorithm.ipynb**

**Objective:**  
Implement the real-time pricing algorithm using demand predictions and competitor data.

**Key Steps:**  

* Integrated processed demand and competitive data to construct a comprehensive dataset.  
* Applied machine learning techniques (e.g., Gradient Boosting, Random Forest) for demand prediction and pricing optimization.  
* Utilized evaluation metrics like Mean Absolute Error (MAE) to validate demand predictions, ensuring alignment with business objectives.  
* Designed a dynamic pricing algorithm based on predicted demand, competitor prices, and customer satisfaction metrics.  
* Simulated pricing scenarios and their revenue impact.  
* Developed insightful visualizations showcasing revenue contributions, price uplift, and other pricing metrics.

**Insights:**  

* Identified optimal price points for key product categories and regions to maximize revenue.  
* Visualized top contributing products and revenue uplift.

---

## Key Visualizations  

The project includes insightful visualizations to convey the results:

1. **Top Product Categories by Price Uplift:**  
    * Highlighted the top 10 product categories with the highest and lowest price uplift.  
    * Visualized the contribution of optimal pricing strategies to revenue improvement.

2. **Revenue Contribution Analysis:**  
    * Showed the percentage contribution of top product categories to the optimized revenue.  
    * Helped identify the most impactful product categories and regions for targeted pricing strategies.

3. **Revenue Uplift Comparison Across Categories:**  
    * Compared original and optimized revenues across product categories.  
    * Illustrated the revenue uplift achieved through dynamic pricing strategies.

4. **Summarizing Prices by Product Category:**  
    * Visualized the distribution of prices across product categories to understand pricing trends.  
    * Highlighted variations in pricing within categories to identify opportunities for optimization.

5. **Competitor Price Comparison:**  
    * Provided a comparison of pricing strategies with competitors.  
    * Highlighted areas where pricing adjustments can improve competitiveness and profitability.

---

## Tools & Techniques  

* **Languages:** Python (NumPy, Pandas, Scikit-Learn, Matplotlib, Seaborn).  
* **Machine Learning Models:** Random Forest, Gradient Boosting.  
* **Visualization:** Matplotlib, Seaborn.  
* **Data Processing:** Feature engineering, data cleaning, and statistical analysis.

---

## How to Use  

1. Clone this repository.  
2. Run the notebooks in the following order:
    * `real-time-pricing.ipynb`  
    * `regional_demand_prediction.ipynb`  
    * `dynamic_pricing_algorithm.ipynb`  

---

## Future Scope  

* Enhance the model by incorporating seasonal trends and marketing campaign effects.  
* Develop a user-friendly dashboard for real-time monitoring and decision-making.  
