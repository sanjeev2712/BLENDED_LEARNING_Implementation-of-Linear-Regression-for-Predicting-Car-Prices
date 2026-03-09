# BLENDED_LEARNING
# Implementation-of-Linear-Regression-for-Predicting-Car-Prices
## AIM:
To write a program to predict car prices using a linear regression model and test the assumptions for linear regression.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import Libraries: Bring in essential libraries such as pandas, numpy, matplotlib, and sklearn.
2. Load Dataset: Import the dataset containing car prices along with relevant features.
3. Data Preprocessing: Manage missing data and select key features for the model, if required.
4. Split Data: Divide the dataset into training and testing subsets.
5. Train Model: Build a linear regression model and train it using the training data.
6. Make Predictions: Apply the model to predict outcomes for the test set.
7. Evaluate Model: Measure the model's performance using metrics like R² score, Mean Absolute Error (MAE), etc.
8. Check Assumptions: Plot residuals to verify assumptions like homoscedasticity, normality, and linearity.
9. Output Results: Present the predictions and evaluation metrics.

## Program:
```
/*
 Program to implement linear regression model for predicting car prices and test assumptions.
Developed by: Sanjeev Kumar K
RegisterNumber:25012334  

df.head
df = pd.read_csv('CarPrice_Assignment.csv')
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score,mean_absolute_error
from sklearn.preprocessing import StandardScaler
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm
x=df[['enginesize','horsepower','citympg','highwaympg']]
y=df['price']
x_train,x_test,y_train,y_test = train_test_split(x, y, test_size=0.2,random_state=42)
scaler = StandardScaler()
x_train_scaled = scaler.fit_transform(x_train)
x_test_scaled = scaler.transform(x_test)
model = LinearRegression()
model.fit(x_train_scaled, y_train)
y_pred = model.predict(x_test_scaled)
print('Name:Sanjeev')
print('Reg. No:25012334')
print("MODEL COEFFICIENTS:")
for feature,coef in zip(x.columns, model.coef_):
    print(f"{feature:}: {coef:}")
print(f"{'Intercept':}: {model.intercept_:}")
print("\nMODEL PERFORMANCE:")
print(f"{'MSE':}: {mean_squared_error(y_test, y_pred):}")
print(f"{'RMSE':}: {np.sqrt(mean_squared_error(y_test, y_pred)):}")
print(f"{'R-squared':}: {r2_score(y_test, y_pred):}")
print(f"{'MAE':}:{mean_absolute_error(y_test, y_pred):}")
plt.figure(figsize=(10, 5))
plt.scatter(y_test, y_pred, alpha=0.6)
plt.plot([y.min(), y.max()],[y.min(),y.max()], 'r--')
plt.title("Linearity Check: Actual vs Predicted Prices")
residuals = y_test - y_pred
dw_test = sm.stats.durbin_watson(residuals)
print(f"\nDurbin_Watson Statistic: {dw_test:.2f}", "\n(Values close to indicate no autocorrection)")


plt.figure(figsize=(10,5))
sns.residplot(x=y_pred, y = residuals, lowess=True, line_kws={'color':'red'})
plt.title("Homoscedasticity check: Residuals vs Predicted")
plt.xlabel("Predicted Price ($)")
plt.ylabel("Residuals ($)")
plt.grid(True)
plt.show()

*/
```

## Output:
![alt text](<Screenshot 2026-03-09 094944.png>) 
![alt text](<Screenshot 2026-03-09 094950.png>) 
![alt text](<Screenshot 2026-03-09 095008.png>) 
![alt text](<Screenshot 2026-03-09 095031.png>) 
![alt text](<Screenshot 2026-03-09 095048.png>)

## Result:
Thus, the program to implement a linear regression model for predicting car prices is written and verified using Python programming, along with the testing of key assumptions for linear regression.
