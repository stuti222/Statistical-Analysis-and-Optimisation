# Statistical-Analysis-and-Optimisation

# Predictive Optimisation of Reaction Yield

## Project Overview
This project focuses on identifying the combination of experimental settings—**temperature**, **pH**, and **pressure**—that maximise the yield of a chemical reaction. Using **statistical data science techniques**, we developed a multivariate polynomial regression model to guide experimental decisions.

**Objective:** Recommend optimal settings for reaction conditions to maximise predicted yield.

---

## Dataset
The dataset contains the following variables:

| Variable | Description |
|----------|-------------|
| X1       | Reaction Temperature (°C) |
| X2       | pH of the reaction |
| X3       | Pressure (kPa) |
| Y        | Yield of reaction (%) |

> Note: Data preprocessing and variable scaling were applied for stability in the regression model.

---

## Methodology

### 1. Data Exploration & Assumptions
- Checked variable distributions and potential transformations (Box-Cox analysis)
- Analysed multicollinearity and interactions (Variance Inflation Factor)
- Identified outliers and influential points (Cook’s Distance)
- Verified modelling assumptions:
  - Normality of residuals (QQ plot)
  - Homoscedasticity (constant variance)
  - Independence of errors

### 2. Model Development
- Developed a **second-order polynomial regression model** including interaction terms
- Ensured functional marginality: interaction terms only included if main effects are significant
- Represented model in matrix form:  
  \[
  \hat{Y} = X \hat{\beta}, \quad Y \sim N_n(X\beta, \sigma^2 I)
  \]

### 3. Model Selection
- Used **Global and Partial F-tests**, **ANOVA**, **Adjusted R²**, **AIC**, **Mallow’s Cp**
- Explored stepwise and all-subset regression to balance complexity vs. predictive performance
- Selected the best-fitting quadratic model with key interaction terms

### 4. Model Evaluation
- Evaluated model using residual diagnostics:
  - QQ plot for normality
  - Scatter of residuals for homoscedasticity
- Performance metrics:
  - High R² and Adjusted R²
  - Low MSE and AIC

### 5. Optimisation
- Calculated stationary point analytically for second-order model:
  \[
  \hat{x_s} = -\frac{1}{2} \hat{\beta}^{-1} \hat{b}
  \]
- Eigenvalues checked to confirm maximum
- Optimal conditions predicted within experimental ranges

---

## Results (example)

| Parameter   | Optimal Value | Notes |
|------------|---------------|------|
| Temperature | 225 °C        | Within experimental range |
| pH          | 5.8           | Significant impact on yield |
| Pressure    | 180 kPa       | Moderate sensitivity |
| Predicted Yield | 96.3%     | Maximum expected yield |

> Sensitivity analysis indicates temperature and pH as the key drivers of reaction yield.
  
---

## Future Work
- Explore **non-linear or machine learning models** (e.g., Random Forest, Gradient Boosting)  
- Extend to **multi-stage or multi-output optimisation**  
- Automate **model selection and diagnostics validation**  
- Integrate **visualisations for interactive portfolio display**

