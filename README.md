<div align="center">

# Python Data Science: Regression & Forecasting

### Course Repository · Maven Analytics
**Statistical modeling, regularization & time-series forecasting with Python**

![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat-square&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-8B0000?style=flat-square&logo=python&logoColor=white)
![Prophet](https://img.shields.io/badge/Prophet-1E3A8A?style=flat-square&logo=facebook&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter_Lab-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-In_Progress-lightgrey?style=flat-square)

</div>

---

## Course Info

| Field | Detail |
|---|---|
| **Course** | Python Data Science: Regression & Forecasting |
| **Instructor** | Chris Bruehl — Lead Python Instructor, Maven Analytics |
| **Platform** | Udemy |
| **Duration** | ≈8.5 hours |
| **Companion** | *Data Science in Python: Regression & Forecasting* ebook (230+ pages) |
| **Case Studies** | Pricing-strategy engagement for *Maven Consulting Group* (role: Associate Data Scientist) |
| **Part of** | [ml-engineering-bootcamp](https://github.com/MiltonValleL/ml-engineering-bootcamp) — Statistical Modeling Stack |
| **Prerequisites** | [Pandas_Bootcamp](https://github.com/MiltonValleL/Pandas_Bootcamp) · [MatplotSea_Bootcamp](https://github.com/MiltonValleL/MatplotSea_Bootcamp) · basic descriptive statistics |

<br><br>

---

## Learning Objectives

By the end of this course, you'll be able to:

- ✅ Understand the **regression modeling workflow** end to end and when to apply each regression type
- ✅ Build and interpret **simple and multiple linear regression** models with **Statsmodels** and **Scikit-Learn**
- ✅ Read model diagnostics correctly: **p-values, F-statistic, R², Adjusted R², residual analysis, multicollinearity**
- ✅ Improve model performance through **feature engineering** and **regularized regression** (Ridge, Lasso, Elastic Net)
- ✅ Model non-linear relationships with **polynomial features** and transformations
- ✅ Validate models honestly with **train/test split** and **cross-validation**, avoiding overfitting
- ✅ Explore **time series data** and build **forecasts** with linear regression and **Prophet**
- ✅ Translate model output into **business decisions** and communicate them clearly

<br><br>

---

## What This Covers

| Library | Topics |
|---|---|
| **Statsmodels** | OLS regression · Statistical inference · Coefficient interpretation · p-values & confidence intervals · Diagnostic plots · Multicollinearity (VIF) |
| **Scikit-Learn** | `LinearRegression` · `Ridge` / `Lasso` / `ElasticNet` · `PolynomialFeatures` · `Pipeline` · `train_test_split` · `cross_val_score` · Preprocessing & scaling |
| **Time Series & Forecasting** | Trend & seasonality · Autocorrelation · Linear-regression forecasting · Non-linear trends · **Prophet** · Forecast evaluation |
| **Modeling Foundations** | Regression workflow · Bias-variance tradeoff · Feature engineering · Regularization · Model selection & evaluation metrics |

<br><br>

---

## Regression Modeling Workflow

> The mental model this course is built around. Every case study follows these stages — worth internalizing as a reusable checklist.

1. **Frame the problem** — prediction vs. inference? What decision does the model support?
2. **Explore the data (EDA)** — distributions, relationships, outliers, missing values
3. **Prepare features** — encoding, scaling, transformations, feature engineering
4. **Fit a baseline** — simple linear regression as the reference point to beat
5. **Interpret & diagnose** — coefficients, p-values, residuals, assumptions (linearity, homoscedasticity, normality, independence)
6. **Improve** — add features, model non-linearity, apply regularization
7. **Validate** — train/test split and cross-validation; compare on held-out data, not training fit
8. **Communicate** — translate coefficients and error metrics into business language

<br><br>

---

## Course Outline & Progress

> Status reflects real progress. Checkboxes and notebook names are placeholders to update as you advance — adjust the grouping to match the course's actual section layout.

### Module 1 — Intro to Data Science with Python
- [x] The data science & machine learning landscape
- [x] The data science workflow (each phase)
- [x] Essential Python skills review for modeling
- [x] Setting up the modeling environment

### Module 2 — Regression 101
- [x] Goals & primary types of regression analysis
- [x] Prediction vs. inference
- [x] The regression modeling workflow (deep dive)
- [x] Key assumptions behind linear regression

### Module 3 — Pre-Modeling Data Prep & EDA
- [ ] EDA for regression: exploring the target and the features
- [ ] Linear relationships & correlation (and in Python)
- [ ] Feature–target and feature–feature relationships
- [ ] PRO TIP: pairplots & lmplots for visual EDA
- [ ] Preparing the data for modeling

### Module 4 — Simple (Univariate) Linear Regression
- [ ] Simple linear regression overview
- [ ] Least squared error
- [ ] Linear regression in Python and in Statsmodels
- [ ] Interpreting the model, making predictions
- [ ] R-Squared, Hipothesis Test, F-Test
- [ ] Coefficient estimates & P-Values, residual plots

### Module 5 — Multiple Linear Regression
- [ ] Multiple linear regression equation
- [ ] Fitting and interpreting multiple regression models
- [ ] Variable selection
- [ ] Mean Error metrics
- [ ] Adjusted R-Squared

### Module 6 — Model Assumptions
- [ ] The assumptions of linear regression
- [ ] Linearity & independence of errors
- [ ] Normality of errors + interpreting transformed targets
- [ ] No perfect multicollinearity
- [ ] Equal variance of errors (homoscedasticity)
- [ ] Outliers, leverage & influence

### Module 7 — Model Testing & Validation
- [ ] Model scoring steps & data splitting
- [ ] Overfitting, underfitting & the bias-variance tradeoff
- [ ] Validation data & model tuning
- [ ] Model scoring
- [ ] Cross-validation (simple vs. cross-validation)

### Module 8 — Feature Engineering
- [ ] Feature engineering techniques
- [ ] Polynomial terms, combining features & interaction terms
- [ ] Categorical features & dummy variables
- [ ] Binning categorical and numeric data

### 🏁 **PROJECT #1** — San Francisco Rent Prices
- [ ] Perform EDA on a modelling dataset
- [ ] Split your data and choose a validation framework
- [ ] Fit and tune a linear regression model by checking model assumptions and performing feature engineering
- [ ] Interpret a linear regression model

| Project Details | |
|---|---|
| **Dataset** | San Francisco rental listings |
| **Skills Applied** | EDA · linear regression · model assumptions · validation · feature engineering |
| **Notebook** | `project-1-sf-rent-prices.ipynb` |
| **Status** | ⏳ Pending |

---

### Module 9 — Regularized Regression
- [ ] Intro to regularized regression
- [ ] Ridge (L2) regression, standarization & fitting a Ridge regression model
- [ ] Lasso (L1) regression and feature selection
- [ ] Elastic Net regression
- [ ] Hyperparameter tuning (alpha) with cross-validation

### 🏁 **PROJECT #1** — San Francisco Rent Prices (Continued)
- [ ] Fit Lasso, Ridge, and Elastic Net Regression models
- [ ] Tune the models to the optimal regularization strength based on validation results
- [ ] Select the model which has the highest accuracy on out of sample data

| Project Details | |
|---|---|
| **Dataset** | San Francisco rental listings |
| **Skills Applied** | regularized regression · Ridge regression · Lasso regression · Elastic Net regression |
| **Notebook** | `project-1.2-sf-rent-prices.ipynb` |
| **Status** | ⏳ Pending |

---

### Module 10 — Time Series Analysis
- [ ] Time series, moving averages and exponential smoothing
- [ ] Decomposition, autocorrelation chart
- [ ] Forecasting, linear regression with trend & season
- [ ] Facebook Prophet

### 🏁 **PROJECT #2** — Electricity Consumption
- [ ] Explore and manipulate time series data
- [ ] Perform time series data splitting
- [ ] Build and compare the predictive accuracy of forecasting  models
- [ ] **Deliverable**: forecasting notebook

| Case Study Details | |
|---|---|
| **Scenario** | Forecasting electricity consumption |
| **Skills Applied** | Time series EDA · regression forecasting · Prophet · forecast metrics |
| **Notebook** | `project-2-forecasting.ipynb` |
| **Status** | ⏳ Pending |

<br><br>

---

## Model Evaluation Metrics Reference

> Which number tells you what. Keep this handy — choosing the right metric is half of modeling.

| Metric | What it measures | When to use | Notes |
|---|---|---|---|
| **R²** | Share of variance explained | Quick fit summary | Never decreases when adding features — misleading for model comparison |
| **Adjusted R²** | R² penalized by number of predictors | Comparing models with different feature counts | Prefer over R² for multiple regression |
| **MAE** | Mean absolute error: `mean(\|y − ŷ\|)` | When all errors matter equally | Same units as target; robust to outliers |
| **MSE** | Mean squared error: `mean((y − ŷ)²)` | Optimization / loss | Penalizes large errors heavily; squared units |
| **RMSE** | `sqrt(MSE)` | Reporting error in target units | Sensitive to outliers; most common regression score |
| **MAPE** | Mean absolute percentage error | Forecasting / cross-scale comparison | Breaks down when actuals are near zero |
| **AIC / BIC** | Likelihood penalized by complexity | Statsmodels model selection | Lower is better; BIC penalizes complexity harder |

<br><br>

---

## Key Concepts — Personal Notes

> *Updated as the course progresses. Working notes on the mental models behind regression & forecasting.*

| Concept | Description | Notes |
|---|---|---|
| **Prediction vs. Inference** | Two distinct goals of regression | Prediction optimizes accuracy; inference optimizes understanding *why*. The modeling choices differ |
| **Bias-Variance Tradeoff** | The core tension in model complexity | High bias → underfitting; high variance → overfitting. Regularization trades a little bias for less variance |
| **Regularization** | Shrinking coefficients to prevent overfitting | Ridge shrinks all; Lasso can zero out features (selection); Elastic Net blends both |
| **Multicollinearity** | Predictors correlated with each other | Inflates coefficient variance and breaks interpretation. Check with VIF |
| **Residual Analysis** | Inspecting what the model got wrong | Residuals should look like random noise. Patterns reveal violated assumptions |
| **Feature Engineering** | Creating better inputs from raw data | Often beats switching algorithms. Transformations, interactions, domain features |
| **Stationarity** | Statistical properties stable over time | Many forecasting methods assume it; trends/seasonality must be handled first |
| **Statsmodels vs Scikit-Learn** | Two philosophies, one task | See note below |

<br><br>

---

## Statsmodels vs Scikit-Learn — When to Use Which

This course is unusual (and valuable) because it uses **both**. They are not redundant:

- **Statsmodels** → built for **statistical inference**. Rich summary tables, p-values, confidence intervals, diagnostic tests. Reach for it when the question is *"which variables matter and how much?"*
- **Scikit-Learn** → built for **prediction and ML pipelines**. Consistent `fit`/`predict` API, regularization, cross-validation, preprocessing, pipelines. Reach for it when the question is *"how accurately can I predict new values?"*

A mature workflow often uses Statsmodels to *understand* the data and Scikit-Learn to *productionize* the prediction.

<br><br>

---

## Tips & Tricks Reference

| Task | Code Pattern |
|---|---|
| **Fit OLS with Statsmodels** | `import statsmodels.formula.api as smf` → `model = smf.ols('price ~ size + rooms', data=df).fit()` then `model.summary()` |
| **Fit linear regression (Scikit-Learn)** | `from sklearn.linear_model import LinearRegression` → `LinearRegression().fit(X, y)` |
| **Train/test split** | `from sklearn.model_selection import train_test_split` → `X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)` |
| **Cross-validation score** | `from sklearn.model_selection import cross_val_score` → `cross_val_score(model, X, y, cv=5, scoring='neg_root_mean_squared_error')` |
| **Ridge / Lasso** | `from sklearn.linear_model import Ridge, Lasso` → `Ridge(alpha=1.0).fit(X, y)` |
| **Polynomial features** | `from sklearn.preprocessing import PolynomialFeatures` → `PolynomialFeatures(degree=2).fit_transform(X)` |
| **Build a pipeline** | `from sklearn.pipeline import make_pipeline` → `make_pipeline(StandardScaler(), Ridge())` |
| **Check multicollinearity (VIF)** | `from statsmodels.stats.outliers_influence import variance_inflation_factor` |
| **Prophet forecast** | `from prophet import Prophet` → `m = Prophet(); m.fit(df); m.predict(m.make_future_dataframe(periods=90))` |
| **Regression metrics** | `from sklearn.metrics import mean_absolute_error, root_mean_squared_error, r2_score` |

<br><br>

---

## Prerequisites & Setup

### Required Knowledge
- ✅ **NumPy** arrays (indexing, slicing, broadcasting)
- ✅ **Pandas** DataFrames (filtering, groupby, aggregation, merging)
- ✅ **Matplotlib / Seaborn** for visualizing data and model results
- ✅ Basic descriptive statistics (mean, variance, correlation, distributions)
- ✅ Comfort with Jupyter Notebooks

### Recommended Prior Courses
- [Pandas_Bootcamp](https://github.com/MiltonValleL/Pandas_Bootcamp) — data manipulation
- [MatplotSea_Bootcamp](https://github.com/MiltonValleL/MatplotSea_Bootcamp) — visualization & reporting

### Environment Setup
```bash
# Create conda environment
conda create -n regression-forecasting -c conda-forge python=3.12 jupyter numpy pandas matplotlib seaborn scikit-learn statsmodels prophet

# Activate
conda activate regression-forecasting

```

<br><br>

---

## Integration with ML Bootcamp

This course is the **Statistical Modeling Stack** in the broader ML Engineering Bootcamp — the bridge from analysis to machine learning:

| Module | Course | Focus | Status |
|---|---|---|---|
| **1. Foundation** | Pandas_Bootcamp | Data manipulation, aggregation, reshaping | ✅ Complete |
| **2. Visualization** | MatplotSea_Bootcamp | Visualization, reporting, storytelling | 🔄 In Progress |
| **3. ML Foundations** | **Regression-and-Forecasting** | Regression, regularization, time-series forecasting | 🔄 This repo |
| **4. ML Foundations** | classification-modelling | Classification, pipelines, model selection | ⏳ Planned |
| **5. ML Foundations** | unsupervised-ml | Clustering, anomaly detection, dimensionality reduction, recommenders | ⏳ Planned |

> **Domain bridge**: Time-series forecasting is the same problem family as **electrical load forecasting** in power systems — a natural link between 13 years of electrical engineering and the [SIN project](https://github.com/MiltonValleL). *(Optional framing — remove if you'd rather keep this repo course-only.)*

<br><br>

---

## Resources & References

### Official Documentation
- [Scikit-Learn — Linear Models](https://scikit-learn.org/stable/modules/linear_model.html)
- [Statsmodels — Documentation](https://www.statsmodels.org/stable/index.html)
- [Prophet — Documentation](https://facebook.github.io/prophet/)

### Recommended Books & Resources
- **Regression**
  - *An Introduction to Statistical Learning* (ISLP) — James, Witten, Hastie & Tibshirani *(free online — the canonical reference)*
  - *Regression and Other Stories* — Gelman, Hill & Vehtari
  - **Chapters 12–13** of *Python for Data Analysis* — Wes McKinney

- **Forecasting & Time Series**
  - *Forecasting: Principles and Practice* (FPP3) — Hyndman & Athanasopoulos *(free online — the forecasting standard)*
  - *Practical Time Series Forecasting with R/Python* — Galit Shmueli

- **Communication**
  - *Storytelling with Data* — Cole Nussbaumer Knaflic

### Online Resources
- [Real Python — Linear Regression in Python](https://realpython.com/linear-regression-in-python/)
- [Scikit-Learn — Cross-validation guide](https://scikit-learn.org/stable/modules/cross_validation.html)

<br><br>

---

## Connect

> **Milton R. Valle Lora**
>
> Senior Electrical Engineer → ML Engineer in transition
>
> Cochabamba, Bolivia

<br>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/miltonvallelora)
[![GitHub](https://img.shields.io/badge/GitHub-%23181717.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/MiltonValleL)
[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=youtube&logoColor=white)](https://youtube.com/@DataScienceByDoing)

</div>



---

<div align="center">
<sub>Part of the ML Engineering Bootcamp · Statistical Modeling Stack · Updated as modules are completed</sub>
</div>
