# Introduction to Linear Regression

> *"All models are wrong, but some are useful."* — George Box

A theory-first introduction to **regression analysis** and, specifically, to **linear regression** — the foundational supervised learning technique for predicting numeric values. This lesson focuses on the *why* behind the ideas, building statistical and geometric intuition before any code.

---

## Table of Contents

1. [What Is Regression?](#1-what-is-regression)
2. [Core Terminology: Target and Features](#2-core-terminology-target-and-features)
3. [How a Regression Model Learns: Train, Then Predict](#3-how-a-regression-model-learns-train-then-predict)
4. [The Two Goals of Regression: Prediction vs. Inference](#4-the-two-goals-of-regression-prediction-vs-inference)
5. [Types of Regression (and Where Linear Regression Fits)](#5-types-of-regression-and-where-linear-regression-fits)
6. [A Closer Look at Linear Regression](#6-a-closer-look-at-linear-regression)
7. [The Regression Modeling Workflow](#7-the-regression-modeling-workflow)
8. [Key Takeaways](#8-key-takeaways)

---

## 1. What Is Regression?

**Regression analysis** is a **supervised learning** technique used to **predict a numeric variable** (the *target*) by **modeling its relationship** with a set of other variables (the *features*).

Two words in that definition carry most of the weight:

- **Supervised** — we learn from examples where we *already know the right answer*. The model sees past cases in which both the inputs and the correct numeric output are known.
- **Numeric** — the thing we predict is a continuous quantity (a price, a temperature, a weight), not a category. Predicting a category is **classification**, a different problem (more on this in [Section 5](#5-types-of-regression-and-where-linear-regression-fits)).

### The guiding example: diamonds

Throughout this lesson we use one running example:

> **Predicting the price of a diamond based on its carat weight.**

If we scatter many diamonds on a plot — `carat` on the horizontal axis, `price` on the vertical axis — we see that as carat weight goes up, price tends to go up as well. This is a **positive relationship**.

### The geometric intuition

In its simplest form, **a regression model is a line that represents this relationship.**

```
price
  ▲
  │                    ● ●
  │                ●  ╱●        ← the model: a line summarizing the trend
  │            ●  ╱ ●
  │         ● ╱●  ●
  │      ● ╱ ●
  │   ●╱ ●
  │ ╱●
  └──────────────────────────▶ carat
```

Once we have that line, prediction becomes a geometric act: to estimate the price of a diamond we have never seen, we locate its carat value on the horizontal axis, go up to the line, and read off the predicted price. For example, the line might tell us that *the predicted price for a 1.5-carat diamond is roughly $10,000.*

The line will not pass through every point — real data is noisy — but a good line captures the **underlying trend** well enough to be useful. That is exactly the spirit of George Box's quote above.

---

## 2. Core Terminology: Target and Features

Every regression problem is organized around two kinds of variables. Learning their many names is important, because different textbooks, fields, and libraries use different words for the *same idea*.

### Target ($y$)

The **target** is the variable **you are trying to predict**.

It goes by many names — all of these mean the same thing:

| Common name | Also called |
|---|---|
| **Target** | $y$, *model output*, *response*, *dependent variable* |

Regression helps us understand how the target is impacted by the features. In the diamonds example, **`price` is the target** — it is what we want to predict, and it is numerical, which is why regression (and not classification) is the right tool.

### Features ($X$)

The **features** are the variables that **help you predict the target**.

Again, one idea, many names:

| Common name | Also called |
|---|---|
| **Features** | $X$, *model inputs*, *predictors*, *independent variables* |

Regression helps us understand how the features **impact**, or **predict**, the target. In the diamonds example, `carat`, `cut`, `color`, `clarity`, and the remaining columns are all **features**.

### Seeing it in a table

Think of a dataset as a table where each **row** is one observation (one diamond) and each **column** is a variable:

| carat | cut | color | clarity | depth | table | x | y | z | **price** |
|---|---|---|---|---|---|---|---|---|---|
| 0.26 | Ideal | H | IF | 61.1 | 57.0 | 4.12 | 4.16 | 2.53 | **468** |
| 1.20 | Ideal | H | VS1 | 61.6 | 57.0 | 6.82 | 6.85 | 4.21 | **8275** |
| 0.62 | Good | E | SI2 | 59.4 | 65.0 | 5.54 | 5.48 | 3.27 | **1333** |
| 1.50 | Good | I | VVS2 | 63.3 | 58.0 | 7.24 | 7.27 | 4.59 | **9909** |
| 1.27 | Very Good | I | SI2 | 59.7 | 57.0 | 6.99 | 7.04 | 4.19 | **5371** |

- The **`price`** column (bold) is the **target** — numerical, so we use regression.
- **All other columns** are **features** — they can help us explain, or predict, the price of a diamond.

> **Note:** Here the lowercase column names `x`, `y`, `z` are physical diamond dimensions (length, width, depth in mm). Do not confuse them with the mathematical symbols $X$ (features) and $y$ (target) — an unfortunate but common naming clash.

---

## 3. How a Regression Model Learns: Train, Then Predict

Regression works in two stages, and the distinction between them is the heart of supervised learning.

### Stage 1 — Training (learning from observed values)

We take **records with observed values for both the features *and* the target** and use them to **"train"** the model. During training, the model has access to the right answers (`price`), so it can adjust itself to capture the relationship between the features and the target.

| carat | cut | ... | **price** (known) |
|---|---|---|---|
| 0.26 | Ideal | ... | **468** |
| 1.20 | Ideal | ... | **8275** |
| 0.62 | Good | ... | **1333** |
| ... | ... | ... | ... |

### Stage 2 — Prediction (applying to unobserved values)

Then we apply the trained model to **new, unobserved values** — records that contain the **features but no target**:

| carat | cut | ... | **price** |
|---|---|---|---|
| 0.90 | Ideal | ... | **??? ← this is what the model predicts** |

The model fills in the missing target. **This is what regression is *for*** — turning known inputs into an estimate of an unknown numeric output.

> **Why this split matters:** a model is only useful if it works on data it has *not* seen during training. Memorizing the training answers is not learning. This idea — generalizing to unseen data — will later motivate critical concepts such as *train/validation/test splits*, *overfitting*, and *underfitting*.

---

## 4. The Two Goals of Regression: Prediction vs. Inference

Regression models are used for **two primary goals**. Being explicit about *which one you want* matters, because the goal shapes the entire modeling approach — the algorithm you choose, how complex you let the model be, and more.

### Prediction

> **Goal:** predict the target as **accurately as possible.**
>
> *Typical question:* "What is the predicted price of a diamond given its characteristics?"

Here we mostly care about the *quality of the output*. If a more complex, harder-to-interpret model predicts better, prediction-focused work will often accept that trade-off.

### Inference

> **Goal:** **understand the relationships** between the features and the target.
>
> *Typical question:* "How much do a diamond's size and weight impact its price?"

Here we care about *explanation*: the direction and strength of each feature's effect. Inference favors models we can interpret and reason about.

### Striking a balance

In practice you often need to **strike a balance** between the two:

- A model that is **very inaccurate** won't be trustworthy for inference — if it predicts poorly, why believe its explanation of *why*?
- And understanding the impact that variables have on predictions can help make those predictions **more accurate**.

Prediction and inference are two ends of a spectrum, not a strict either/or. Knowing where your problem sits on that spectrum guides every decision that follows.

---

## 5. Types of Regression (and Where Linear Regression Fits)

"Regression" is a family of techniques, not a single algorithm. These are some of the major **types of regression** modeling techniques:

| Type | What it does |
|---|---|
| **Linear Regression** | Models the relationship between the features and target using a **linear equation** (a line / hyperplane). |
| **Regularized Regression** | An extension of linear regression that **penalizes model complexity** to reduce overfitting (e.g., Ridge, Lasso). |
| **Time-Series Forecasting** | Predicts future data using **historical trends and seasonality** (the ordering of observations in time matters). |
| **Tree-Based Regression** | **Splits the data** into groups by maximizing the difference between them (e.g., decision trees, random forests, gradient boosting). |

**Linear Regression** is where we focus next, and for good reason: it is the simplest, most interpretable member of the family, and the conceptual foundation on which the others build.

> ⚠️ **A classic gotcha:** even though **logistic regression** has *"regression"* in its name, it is actually a **classification** technique — it predicts a category, not a numeric value. The name is historical; the behavior is classification.

---

## 6. A Closer Look at Linear Regression

This section goes slightly beyond the overview to build the core theory of linear regression itself.

### 6.1 The model: a linear equation

With a **single feature** (simple linear regression), the model is the equation of a straight line:

$$\hat{y} = \beta_0 + \beta_1 x$$

- $\hat{y}$ (read "y-hat") is the **predicted** target.
- $x$ is the feature (e.g., `carat`).
- $\beta_0$ is the **intercept** — the predicted value of $y$ when $x = 0$ (where the line crosses the vertical axis).
- $\beta_1$ is the **slope** — how much $\hat{y}$ changes for a one-unit increase in $x$. A positive $\beta_1$ means a positive relationship (price rises with carat).

The symbols $\beta_0$ and $\beta_1$ are the model's **coefficients** (also called *parameters* or *weights*). **Training a linear regression means finding the values of these coefficients** that make the line fit the data best.

With **multiple features** (multiple linear regression), the idea generalizes — each feature gets its own coefficient:

$$\hat{y} = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n$$

Geometrically, a line in 2D becomes a flat **plane** in 3D and a **hyperplane** in higher dimensions, but the logic is unchanged: a weighted sum of the features, plus an intercept.

### 6.2 Residuals: measuring how wrong the line is

No line passes through every point. For each observation $i$, the gap between the **actual** value $y_i$ and the **predicted** value $\hat{y}_i$ is called the **residual** (or error):

$$e_i = y_i - \hat{y}_i$$

- A residual of **0** means the line hit that point exactly.
- A **positive** residual means the model *under-predicted*; a **negative** residual means it *over-predicted*.

The residuals are the vertical distances from each point to the line. Intuitively, a "good" line is one where these distances are **small overall**.

### 6.3 "Best fit" = least squares

How do we turn "small overall" into something precise? Linear regression's classic answer is the method of **Ordinary Least Squares (OLS)**: choose the coefficients that **minimize the Sum of Squared Residuals (SSR)**:

$$\text{SSR} = \sum_{i=1}^{m} (y_i - \hat{y}_i)^2 = \sum_{i=1}^{m} \big(y_i - (\beta_0 + \beta_1 x_i)\big)^2$$

Why **square** the residuals instead of just adding them?

- **Squaring removes the sign**, so positive and negative errors don't cancel out. (Simply summing raw residuals could give zero for a terrible line.)
- **Squaring penalizes large errors more than small ones** — being off by 10 costs far more than being off by 1 (100 vs. 1). The line is therefore pushed to avoid big misses.

This quantity we minimize is called a **cost function** (or *loss function*): a single number that measures how badly the model fits, which training tries to make as small as possible. Finding the line of best fit is an **optimization problem** — searching for the coefficients that sit at the bottom of this cost.

> **Where this goes next (optional deep dive):** there are two standard ways to *actually* find those optimal coefficients — solving the **normal equations** directly with linear algebra (a closed-form matrix solution), or iteratively with **gradient descent**. Both are beyond this introduction, but each follows naturally from the cost function above.

### 6.4 A brief word on assumptions

Linear regression is at its most trustworthy — especially for **inference** — when certain assumptions roughly hold: the relationship is approximately **linear**, the residuals are **independent**, have **constant variance**, and are **roughly normally distributed**. You do not need to master these yet; just keep in the back of your mind that the clean theory above comes with conditions, and that checking them is part of *Model Evaluation* in the workflow below.

---

## 7. The Regression Modeling Workflow

Modeling does not happen in isolation. It sits inside a broader data project with six stages:

```
1. Scoping  →  2. Gathering  ⇄  3. Cleaning  ⇄  4. Exploring  ⇄  5. Modeling  →  6. Sharing
   a project      data            data            data            data            insights
```

Stages 2–5 are iterative (the arrows go both ways) — you loop back as you learn more about the data. **Modeling** is stage 5, and it has its own internal flow:

| Sub-step | Purpose | Involves |
|---|---|---|
| **1. Preparing for Modeling** | Get the data ready to feed into an ML algorithm | Single clean table (non-null), *feature engineering*, data splitting |
| **2. Applying Algorithms** | Build regression models from the training data | Linear regression, regularized regression, time series |
| **3. Model Evaluation** | Evaluate model fit on training & validation data | R-squared & MAE, checking assumptions, validation performance |
| **4. Model Selection** | Pick the best model to deploy and extract insights | Test performance, interpretability |

Steps 1–3 form a **loop**: evaluation results send you back to prepare better features or try other algorithms, until the model is good enough to move on to selection.

---

## 8. Key Takeaways

- **Regression** is a *supervised learning* technique for predicting a *numeric* **target** ($y$) from one or more **features** ($X$).
- The same two ideas have many names: *target / response / dependent variable* and *features / predictors / independent variables*. Learn them — you will meet all of them.
- A model **trains** on observed data (features **and** target), then **predicts** the target for new, unobserved data (features only). Usefulness comes from **generalizing** to unseen data.
- Regression serves two goals — **prediction** (accurate outputs) and **inference** (understanding relationships) — and real projects **balance** the two.
- **Linear regression** is the simplest member of the regression family: it fits a straight line (or hyperplane) by choosing coefficients that **minimize the sum of squared residuals** (least squares).
- Beware the naming trap: **logistic regression is classification**, not regression.
- Modeling is one stage of a larger, **iterative** workflow: *scope → gather → clean → explore → model → share*.

---

*This README is a theoretical primer. The natural next steps are a hands-on notebook (fitting a real line to the diamonds data) and a deeper dive into how the optimal coefficients are computed — the **normal equations** and **gradient descent**.*
