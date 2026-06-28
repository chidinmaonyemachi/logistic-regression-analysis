# ✈️ Airline Customer Satisfaction Prediction

## Project Overview

This project predicts whether an airline passenger is **satisfied or dissatisfied** using **Logistic Regression** on the Airline Passenger Satisfaction Dataset (129,880 passengers).

---

## Dataset

**Airline Passenger Satisfaction Dataset**
- 129,880 rows × 22 features
- Target variable: `satisfaction` (satisfied / dissatisfied)
- Class split: 71,087 satisfied | 58,793 dissatisfied

---

## Techniques Used

| Step | Technique |
|------|-----------|
| Data Cleaning | Forward-fill + drop for 393 null values in `Arrival Delay` |
| Encoding | `LabelEncoder` for `satisfaction`, `Customer Type`, `Type of Travel`, `Class` |
| Scaling | `StandardScaler` applied before model fitting |
| Modelling | Binary Logistic Regression (`max_iter=1000`) |
| Evaluation | Confusion Matrix, Precision, Recall, F1-Score, Classification Report |
| Interpretation | Model coefficients mapped to business insights |

---

## Results

| Metric | Score |
|--------|-------|
| **Accuracy** | **82.58%** |
| **Precision** | **84.24%** |
| **Recall** | **84.09%** |
| F1-Score (Satisfied) | 0.84 |
| F1-Score (Dissatisfied) | 0.81 |

### Confusion Matrix
|  | Predicted Dissatisfied | Predicted Satisfied |
|--|----------------------|-------------------|
| **Actual Dissatisfied** | 9,479 (TN) | 2,196 (FP) |
| **Actual Satisfied** | 2,274 (FN) | 12,027 (TP) |

---

## Feature Coefficients & Business Insights

| Feature | Coefficient | Insight |
|---------|------------|---------|
| Inflight Entertainment | **+0.984** | Strongest positive driver — upgrade screens & content |
| On-board Service | +0.406 | Cabin crew quality significantly boosts satisfaction |
| Seat Comfort | +0.391 | Comfortable seats are a key lever, especially in Economy |
| Check-in Service | +0.360 | A smooth check-in sets a positive tone for the journey |
| Ease of Online Booking | +0.310 | Reduce digital friction in the booking funnel |
| Online Boarding | +0.186 | Faster, clearer boarding improves experience |
| Customer Type | **−0.759** | Disloyal customers are much harder to satisfy → target with loyalty programmes |
| Arrival Delay | −0.269 | Each delay unit directly erodes satisfaction |
| Type of Travel | −0.419 | Personal travellers are less satisfied than business travellers |

> **Interpretation example:** For every 1-unit increase in standardised Inflight Entertainment rating, the log-odds of a passenger being satisfied increase by **0.984**, making it the single most impactful feature in the model.

---

## Tools & Libraries

| Tool | Purpose |
|------|---------|
| Python | Core language |
| Pandas | Data loading, cleaning, encoding |
| Scikit-learn | Preprocessing, modelling, evaluation |
| Matplotlib | Visualisations |
| Seaborn | Styled plots |

---

## Limitations & Future Work

- Logistic Regression assumes linear log-odds relationships; tree-based models (Random Forest, XGBoost) may capture non-linearities better.
- Survey ratings introduce subjectivity bias.
- Model was evaluated on a single train-test split; k-fold cross-validation would provide a more robust estimate.
- **Future:** SHAP values for explainability, ensemble methods, REST API deployment.
