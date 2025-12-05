# Lab 20: Introduction to Machine Learning - Linear Regression

## Overview
Comprehensive introduction to supervised machine learning using linear regression. This lab demonstrates fundamental ML concepts including model training, prediction, evaluation, and visualization using real-world datasets.

## Course Information
**Course:** CSC 245 - Introduction to Data Science  
**Institution:** CUNY College of Staten Island  
**Semester:** Fall 2025  
**Due Date:** December 6, 2025

## Learning Objectives
- ✅ Understand linear regression fundamentals
- ✅ Implement supervised learning models
- ✅ Train models on real-world data
- ✅ Make predictions using trained models
- ✅ Evaluate model performance (MSE, R²)
- ✅ Visualize regression results and residuals
- ✅ Apply ML to financial time series data

## Technologies Used
- **Python 3.x**
- **NumPy** - Numerical computing
- **Pandas** - Data manipulation
- **Matplotlib** - Data visualization
- **scikit-learn** - Machine learning library

## Projects Implemented

### 1. Study Time vs. Exam Score Prediction
**Problem:** Predict exam scores based on hours studied

**Dataset:**
- 6 students
- Features: Hours studied
- Target: Exam score (out of 100)

**Model:** Simple Linear Regression  
**Equation:** `Score = 5 * Hours + 45`

**Results:**
- Perfect linear relationship
- Prediction for 4.5 hours: 67.5 points
- Demonstrates supervised learning basics

![Study Time vs Exam Score](Study_time_vs__Exam_score.png)

---

### 2. House Price Prediction
**Problem:** Predict house prices based on square footage

**Dataset:**
- 5 houses
- Features: Size (sq ft)
- Target: Price ($1000s)

**Model:** Linear Regression  
**Training:** 80% train, 20% test split

**Results:**
- Strong positive correlation
- Realistic predictions for new houses
- Demonstrates train/test split

![House Size vs Price](House_size_vs__price.png)

---

### 3. Apple Stock Price Prediction (AAPL)
**Problem:** Predict future stock prices using historical data

**Dataset:**
- Real Apple Inc. stock data (AAPL.csv)
- Time series analysis
- Features: Historical prices, moving averages
- Target: Next-day closing price

**Model:** Linear Regression with time features

**Performance Metrics:**
- **MSE (Mean Squared Error): 18.06**
- Low MSE indicates good predictions
- Model captures general trend

**Key Insights:**
- Blue line: Actual stock prices
- Orange line: Model predictions
- Model smooths out daily volatility
- Follows overall price trajectory

![Apple Stock Prediction](APPL_stock_price_pred.png)

---

### 4. Residual Analysis
**Purpose:** Evaluate model quality and identify patterns in errors

**What Are Residuals?**
- Residual = Actual Price - Predicted Price
- Shows prediction errors
- Ideal: randomly scattered around zero

**Analysis:**
- Points scattered around y=0 (good!)
- No clear pattern (indicates good fit)
- Some predictions over/under estimate
- Random distribution suggests model is appropriate

![Residual Plot](Residual_Plot.png)

---

## Key Concepts Explained

### Linear Regression
Mathematical model that finds the best-fit line through data points:
```
y = mx + b
```
Where:
- `y` = prediction (dependent variable)
- `x` = input feature (independent variable)
- `m` = slope (how much y changes per unit of x)
- `b` = intercept (y value when x = 0)

### Mean Squared Error (MSE)
Measures average squared difference between actual and predicted values:
```
MSE = (1/n) * Σ(actual - predicted)²
```
- Lower MSE = better predictions
- Penalizes large errors more than small ones
- Same units as target variable (squared)

### Train/Test Split
- **Training Set (80%):** Used to learn patterns
- **Test Set (20%):** Used to evaluate performance
- Prevents overfitting
- Simulates real-world predictions

### Residuals
Difference between actual and predicted values:
```
Residual = Actual - Predicted
```
- Positive residual: Underestimated
- Negative residual: Overestimated
- Pattern in residuals suggests model improvement needed

---

## File Structure
```
lab20-machine-learning/
├── ML_lab1.ipynb                    # Main Jupyter notebook
├── AAPL.csv                         # Apple stock data
├── Study_time_vs__Exam_score.png    # Plot 1: Study time regression
├── House_size_vs__price.png         # Plot 2: House price regression
├── APPL_stock_price_pred.png        # Plot 3: Stock price prediction
├── Residual_Plot.png                # Plot 4: Residual analysis
└── README.md                        # This file
```

---

## How to Run

### Prerequisites
```bash
pip install numpy pandas matplotlib scikit-learn jupyter
```

### Running the Notebook
```bash
jupyter notebook ML_lab1.ipynb
```

Or open in:
- Google Colab
- VS Code with Jupyter extension
- JupyterLab

---

## Code Highlights

### Simple Linear Regression
```python
from sklearn.linear_model import LinearRegression

# Create and train model
model = LinearRegression()
model.fit(X_train, y_train)

# Make predictions
predictions = model.predict(X_test)
```

### Model Evaluation
```python
from sklearn.metrics import mean_squared_error, r2_score

# Calculate error metrics
mse = mean_squared_error(y_actual, y_pred)
r2 = r2_score(y_actual, y_pred)
```

### Visualization
```python
import matplotlib.pyplot as plt

# Plot actual vs predicted
plt.plot(X, y_actual, label='Actual')
plt.plot(X, y_pred, label='Predicted')
plt.legend()
plt.savefig('prediction.png')
```

---

## Real-World Applications

### Finance
- Stock price prediction (demonstrated)
- Portfolio optimization
- Risk assessment
- Algorithmic trading

### Real Estate
- Property valuation (demonstrated)
- Market trend analysis
- Investment ROI prediction

### Business
- Sales forecasting
- Demand prediction
- Revenue modeling
- Customer lifetime value

### Education
- Grade prediction (demonstrated)
- Student performance modeling
- Resource allocation
- Intervention targeting

---

## Model Performance

### Study Time Model
- **Type:** Perfect linear fit
- **Use Case:** Educational demonstration
- **Insight:** Every hour studied = +5 points

### House Price Model
- **Type:** Simple regression
- **Strength:** Strong positive correlation
- **Insight:** Bigger houses = higher prices (expected!)

### Stock Price Model
- **MSE:** 18.06 (relatively low)
- **Challenge:** Stock prices are volatile
- **Achievement:** Model captures general trends
- **Limitation:** Can't predict sharp movements

---

## What I Learned

### Machine Learning Fundamentals
1. **Supervised Learning:** Using labeled data to train models
2. **Feature Engineering:** Selecting relevant input variables
3. **Model Training:** Finding patterns in historical data
4. **Prediction:** Using learned patterns on new data
5. **Evaluation:** Measuring model accuracy with metrics

### Data Science Workflow
1. Load and explore data
2. Clean and prepare features
3. Split into train/test sets
4. Train regression model
5. Make predictions
6. Evaluate performance
7. Visualize results

### Python Libraries
- NumPy for numerical operations
- Pandas for data manipulation
- scikit-learn for ML algorithms
- Matplotlib for professional visualizations

---

## Extensions and Improvements

### Possible Enhancements
1. **Multiple Features:** Use house location, bedrooms, age, etc.
2. **Polynomial Regression:** Capture non-linear relationships
3. **Feature Scaling:** Normalize features for better performance
4. **Cross-Validation:** More robust evaluation
5. **Regularization:** Prevent overfitting (Ridge, Lasso)
6. **Time Series Features:** For stock prediction (lag, moving avg)

### Advanced Techniques
- Random Forest Regression
- Gradient Boosting (XGBoost)
- Neural Networks
- LSTM for time series
- Ensemble methods

---

## Model Limitations

### Linear Regression Assumptions
- ❌ Relationship must be linear
- ❌ Residuals should be normally distributed
- ❌ No multicollinearity among features
- ❌ Homoscedasticity (constant variance)

### When to Use Alternative Models
- **Non-linear data:** Polynomial regression, tree-based models
- **Complex patterns:** Neural networks, deep learning
- **Time series:** ARIMA, LSTM, Prophet
- **Classification:** Logistic regression, SVM, trees

---

## Performance Metrics Explained

### Mean Squared Error (MSE)
- **What:** Average squared error
- **Good:** Low values (close to 0)
- **Bad:** High values (large errors)
- **AAPL MSE = 18.06:** Predictions are ~$4.25 off on average

### R² Score (Not shown but important)
- **Range:** 0 to 1 (1 = perfect fit)
- **Interpretation:** Percentage of variance explained
- **Example:** R² = 0.85 means model explains 85% of variance

### Residual Analysis
- **Random scatter:** Good model
- **Pattern visible:** Model missing something
- **Funnel shape:** Heteroscedasticity (varying error)

---

## Comparison to Other Algorithms

| Algorithm | Pros | Cons | Best For |
|-----------|------|------|----------|
| Linear Regression | Fast, interpretable, simple | Only linear relationships | Baseline model |
| Polynomial Regression | Captures curves | Can overfit | Non-linear data |
| Decision Trees | Non-linear, no scaling needed | Can overfit | Complex patterns |
| Random Forest | Robust, accurate | Black box, slower | Production systems |
| Neural Networks | Very flexible | Needs lots of data | Complex problems |

---

## Conclusion

This lab successfully demonstrated:
- ✅ Building ML models from scratch
- ✅ Training on real-world data
- ✅ Making accurate predictions
- ✅ Evaluating model performance
- ✅ Creating professional visualizations
- ✅ Understanding ML fundamentals

**Key Takeaway:** Linear regression is a powerful baseline ML technique that provides interpretable results and works well for many real-world problems.

---

## Author
**Mamadou Ba**  
Computer Science @ CUNY College of Staten Island  
Fall 2025

---

## Submission
- ✅ 4 PNG plots generated and saved
- ✅ Jupyter notebook with complete code
- ✅ AAPL.csv dataset included
- ✅ All outputs displayed
- 📅 Due: December 6, 2025 11:59 PM

---

**Note:** This lab provides foundational knowledge for advanced machine learning topics including deep learning, ensemble methods, and neural networks. The concepts learned here apply to all supervised learning algorithms.
